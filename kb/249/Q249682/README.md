---
layout: page
title: "Q249682: HOWTO: Change a Field's Datatype using DAO"
permalink: /kb/249/Q249682/
---

## Q249682: HOWTO: Change a Field's Datatype using DAO

{% raw %}

	Article: Q249682
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:5.0,6.0
	Operating System(s): 
	Keyword(s): kbDAOsearch kbJET kbGrpDSVBDB kbDSupport
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Microsoft Access allows you to modify an existing field's data type. To do so
	programmatically, Microsoft Jet 4.0 introduces the ALTER TABLE ALTER COLUMN DDL
	statement. However, there is no equivalent for Microsoft Jet 3.5.
	
	This article demonstrates a method to alter a field's data type using DAO
	objects.
	
	MORE INFORMATION
	================
	
	Modifying a field's data type requires the following steps:
	
	1. Rename the old field.
	
	2. Add a new field.
	
	3. Copying the data from the old field to the new field.
	
	4. Delete the old field.
	
	If the table has any indexes or relations, the relationships and indexes must be
	dropped prior to performing the steps above, then re-established after
	completion of the steps above.
	
	Microsoft Access handles indexes but not relationships when changing data types.
	The Jet 4.0 ALTER TABLE ALTER COLUMN DDL statement has similar limitations.
	
	The sample code provided handles both indexes and relationships. It also contains
	error handling to roll back the changes and report on any problems.
	
	The main procedure is ChangeFieldType. It takes the following arguments:
	
	- db - an open Database object where the table resides.
	
	- TableName - the name of the table where the field resides.
	
	- FieldName - the name of the field to be changed.
	
	- NewType - the new data type for the field.
	
	- NewAllowZeroLength - new value for the AllowZeroLength property.
	
	- NewAllowNulls - used to set the Required property of the new field.
	
	- NewAttributes - used to set the Attributes property of the new field.
	
	Note: This procedure is for illustration purposes only. For example, the
	procedure copies only basic field properties. In addition to these basic field
	properties, other field properties might also have to be copied. These
	additional field properties include ValidationRule, ValidationText,
	DecimalPlaces, and others, depending on the field type. In addition, the
	procedure does not copy user-defined properties.
	
	The other procedures, RecordRelationInfo, RecordIndexInfo, IsField, and
	MakeArray, are helper procedures used by the main function.
	
	Sample Code
	-----------
	
	This sample changes the CustomerID field in the Customers table from a five
	character field to an eight character field.
	
	The sample uses the Nwind database that comes with Visual Basic.
	
	1. In Visual Basic, create a new Standard EXE project.
	  Form1 is created by default.
	
	2. Add a command button to Form1. Command1 is created by default.
	
	3. On the Project menu, select References.
	  In the References dialog, select the Microsoft DAO Object Library.
	
	4. On the Project menu, select Add Module to add a Code Module.
	  Module1 is created by default.
	
	5. Paste the following code into the General Declarations section of Module1's
	  Code Window:
	
	  Option Compare Text
	  Option Explicit
	
	  Const CFT_Failed As Long = 55555
	
	  Private Const R_NAME = 0, R_ATTRIBUTES = 1, R_TABLE = 2, R_FOREIGNTABLE = 3, R_FIELD = 4, R_FOREIGNFIELD = 5
	
	  Private Const I_NAME = 0, I_PRIMARY = 1, I_UNIQUE = 2, I_REQUIRED = 3, I_IGNORENULLS = 4, I_CLUSTERED = 5, I_FIELD = 6, I_FIELDATTRIBUTES = 7
	
	  Public Sub ChangeFieldType(db As Database, _
	                            ByVal TableName As String, _
	                            ByVal FieldName As String, _
	                            ByVal NewType As Integer, _
	                            Optional NewSize As Long, _
	                            Optional NewAllowZeroLength As Boolean = False, _
	                            Optional NewAllowNulls As Boolean = True, _
	                            Optional NewAttributes As Long)
	
	  ' User-defined properties are not maintained
	
	    Dim td As TableDef, I As Index, R As Relation, F As Field
	
	  ' loop iterators for Indexes, Fields, and Relations collections:
	    Dim I1 As Long, F1 As Long, R1 As Long
	
	    Dim colR As Collection, colI As Collection
	    Dim E_Desc As String, Process As String, SubProcess As String, E As Error
	    Dim TempFieldName As String, Suffix As Long, OldName As String
	    Dim Temp As Variant
	    Dim OrdinalPosition As Long
	
	    Set colI = New Collection
	    Set colR = New Collection
	    On Error GoTo CFT_Err
	    DBEngine(0).BeginTrans
	
	  ' Enumerate relations and save/remove them
	
	    DBEngine(0).BeginTrans
	    Process = "Removing relations on [" & TableName & "]![" & FieldName & "]"
	    SubProcess = ""
	    For R1 = db.Relations.Count - 1 To 0 Step -1
	      Set R = db.Relations(R1)
	      If R.Table = TableName Then
	        For F1 = 0 To R.Fields.Count - 1
	          Set F = R.Fields(F1)
	          If F.Name = FieldName Then
	            RecordRelationInfo R, colR
	            SubProcess = "Removing relation " & R.Name
	            db.Relations.Delete R.Name
	            Exit For
	          End If
	        Next F1
	      ElseIf R.ForeignTable = TableName Then
	        For F1 = 0 To R.Fields.Count - 1
	          Set F = R.Fields(F1)
	          If F.ForeignName = FieldName Then
	            RecordRelationInfo R, colR
	            SubProcess = "Removing relation " & R.Name
	            db.Relations.Delete R.Name
	            Exit For
	          End If
	        Next F1
	      End If
	    Next R1
	    Set F = Nothing
	    Set R = Nothing
	    DBEngine(0).CommitTrans
	
	  ' Enumerate indices and save/remove them
	
	    DBEngine(0).BeginTrans
	    Process = "Removing indexes on [" & TableName & "]![" & FieldName & "]"
	    SubProcess = ""
	    db.TableDefs.Refresh
	    Set td = db(TableName)
	    td.Indexes.Refresh
	    For I1 = td.Indexes.Count - 1 To 0 Step -1
	      Set I = td.Indexes(I1)
	      If I.Foreign <> True Then
	        For F1 = 0 To I.Fields.Count - 1
	          Set F = I.Fields(F1)
	          If F.Name = FieldName Then
	            RecordIndexInfo I, colI
	            SubProcess = "Removing index " & I.Name
	            td.Indexes.Delete I.Name
	            Exit For
	          End If
	        Next F1
	      End If
	    Next I1
	    Set F = Nothing
	    Set I = Nothing
	    DBEngine(0).CommitTrans
	
	  ' Rename Field
	
	    DBEngine(0).BeginTrans
	    Process = "Renaming field"
	    SubProcess = ""
	    td.Fields.Refresh
	    Set F = td(FieldName)
	    OrdinalPosition = F.OrdinalPosition   ' save this value
	
	    ' determine a field name not in use
	    Suffix = 0
	    Do
	      Suffix = Suffix + 1
	      TempFieldName = "XXX" & Suffix
	    Loop While IsField(td, TempFieldName)
	
	    ' rename the field
	    SubProcess = "to " & TempFieldName
	    F.Name = TempFieldName
	
	    Set F = Nothing
	    DBEngine(0).CommitTrans
	
	  ' Add new Field
	
	    DBEngine(0).BeginTrans
	    Process = "Adding new field"
	    SubProcess = ""
	    td.Fields.Refresh
	    Set F = td.CreateField(FieldName, NewType)
	    If NewSize Then F.Size = NewSize
	    F.AllowZeroLength = NewAllowZeroLength
	    F.Required = Not NewAllowNulls
	    F.Attributes = NewAttributes
	    F.OrdinalPosition = OrdinalPosition
	    td.Fields.Append F
	    Set F = Nothing
	    Set td = Nothing
	    DBEngine(0).CommitTrans
	
	  ' Copy data
	
	    DBEngine(0).BeginTrans
	    Process = "Copying data from " & TempFieldName & " to " & FieldName
	    SubProcess = ""
	    db.Execute "UPDATE [" & TableName & "] SET [" & FieldName & "]=[" & _
	                TempFieldName & "]", dbFailOnError
	    DBEngine(0).CommitTrans
	
	  ' Delete temporary field
	
	    DBEngine(0).BeginTrans
	    Process = "Deleting temporary field " & TempFieldName
	    SubProcess = ""
	    Set td = db(TableName)
	    td.Fields.Delete TempFieldName
	    DBEngine(0).CommitTrans
	
	  ' Add back Indices
	
	    DBEngine(0).BeginTrans
	    Process = "Adding indexes back into table"
	    SubProcess = ""
	    Set td = db(TableName)
	    td.Fields.Refresh
	    td.Indexes.Refresh
	    OldName = ""
	    Set I = Nothing
	    For Each Temp In colI
	      If Temp(I_NAME) <> OldName Then
	        If Not (I Is Nothing) Then   ' handle first time through case
	          SubProcess = "Adding index " & I.Name
	          td.Indexes.Append I
	        End If
	        Set I = td.CreateIndex(Temp(I_NAME))
	        I.Primary = Temp(I_PRIMARY)
	        I.Unique = Temp(I_UNIQUE)
	        I.Required = Temp(I_REQUIRED)
	        I.IgnoreNulls = Temp(I_IGNORENULLS)
	        I.Clustered = Temp(I_CLUSTERED)
	      End If
	      Set F = I.CreateField(Temp(I_FIELD))
	      F.Attributes = Temp(I_FIELDATTRIBUTES)  ' to handle descending index
	      I.Fields.Append F
	    Next Temp
	    If Not (I Is Nothing) Then   ' handle case of no indexes
	      SubProcess = "Adding index " & I.Name
	      td.Indexes.Append I
	    End If
	    Set F = Nothing
	    Set I = Nothing
	    Set td = Nothing
	    DBEngine(0).CommitTrans
	
	  ' Add back relations
	
	    DBEngine(0).BeginTrans
	    Process = "Adding relations back into database"
	    SubProcess = ""
	    OldName = ""
	    db.Relations.Refresh
	    Set R = Nothing
	    For Each Temp In colR
	      If Temp(I_NAME) <> OldName Then
	        If Not (R Is Nothing) Then   ' handle first time through case
	          SubProcess = "Adding relation " & R.Name
	          db.Relations.Append R
	        End If
	        Set R = db.CreateRelation(Temp(R_NAME), Temp(R_TABLE), _
	                                  Temp(R_FOREIGNTABLE), Temp(R_ATTRIBUTES))
	      End If
	      Set F = R.CreateField(Temp(R_FIELD))
	      F.ForeignName = Temp(R_FOREIGNFIELD)
	      R.Fields.Append F
	    Next Temp
	    If Not (R Is Nothing) Then   ' if there are no indexes...
	      SubProcess = "Adding relation " & R.Name
	      db.Relations.Append R
	    End If
	    Set F = Nothing
	    Set R = Nothing
	    DBEngine(0).CommitTrans
	
	  ' Commit all pending chhanges
	
	    DBEngine(0).CommitTrans
	    Exit Sub
	    
	  CFT_Abort:
	    On Error Resume Next
	    Set F = Nothing
	    Set td = Nothing
	    DBEngine(0).Rollback
	    DBEngine(0).Rollback
	    Err.Clear
	    On Error GoTo 0
	    Err.Raise CFT_Failed, "ChangeFieldType", E_Desc
	    Exit Sub
	    
	  CFT_Err:
	    E_Desc = "Error " & Process
	    If SubProcess <> "" Then E_Desc = E_Desc & vbCrLf & SubProcess
	    If DBEngine.Errors.Count = 0 Then
	      E_Desc = E_Desc & vbCrLf & "Error " & Err.Number & " " & _
	               Err.Description
	    Else
	      For Each E In DBEngine.Errors
	        E_Desc = E_Desc & vbCrLf & "Error " & E.Number & " (" & _
	                 E.Source & ") " & E.Description
	      Next E
	    End If
	    Debug.Print E_Desc
	    Resume CFT_Abort
	  End Sub
	
	  Private Sub RecordRelationInfo(ByVal R As Relation, colR As Collection)
	
	  ' Records information regarding the relationship and its fields
	  ' in the colR collection.
	
	    Dim F1 As Long, F As Field
	    For F1 = 0 To R.Fields.Count - 1
	      Set F = R.Fields(F1)
	      colR.Add MakeArray(R.Name, R.Attributes, R.Table, R.ForeignTable, _
	                          F.Name, F.ForeignName)
	    Next F1
	  End Sub
	
	  Private Sub RecordIndexInfo(ByVal I As Index, colI As Collection)
	
	  ' Records information about fields in the index and about the index itself
	  ' into the colI collection.
	
	    Dim F1 As Long, F As Field
	    For F1 = 0 To I.Fields.Count - 1
	      Set F = I.Fields(F1)
	      colI.Add MakeArray(I.Name, I.Primary, I.Unique, I.Required, _
	                         I.IgnoreNulls, I.Clustered, F.Name, F.Attributes)
	    Next F1
	  End Sub
	
	  Private Function IsField(td As TableDef, ByVal FieldName As String) _
	          As Boolean
	
	  ' Returns TRUE if a field exists in the table with the same name as
	  '    specified in FieldName.
	  ' Returns FALSE otherwise.
	
	     Dim F As Field
	     Err.Clear
	     On Error Resume Next
	     Set F = td(FieldName)
	     IsField = Err.Number = 0
	     Err.Clear
	  End Function
	   
	  Private Function MakeArray(ParamArray X() As Variant) As Variant
	    
	    ' Does the same thing as the Array() function in VB6
	    
	      MakeArray = X
	    
	  End Function
	
	6. If necessary, change the CFT_Failed constant to use an error number that
	  conforms to your company's standards.
	
	7. Paste the following code into the General Declarations section of Form1's
	  Code Window:
	
	    Private Sub Command1_Click()
	
	       Dim strDB As String
	       strDB = "c:\Program Files\Microsoft Visual Studio\VB98\Nwind.mdb"
	
	       Dim db As DAO.Database
	       Set db = DBEngine(0).OpenDatabase(strDB)
	       ChangeFieldType db, "Customers", "CustomerID", dbText, 8
	       db.Close
	   
	   End Sub
	
	8. If necessary, modify strDB to use your Nwind database.
	
	9. Run the sample project.
	  Click the command button.
	  End the project.
	
	10. Examine the table in Microsoft Access or the Visual Basic Visual Database
	  Manager add-in.
	  Note that the field has been resized.
	
	(c) Microsoft Corporation 1999, All Rights Reserved.
	Contributions by Malcolm Stewart, Microsoft Corporation
	
	
	REFERENCES
	==========
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q217011 HOWTO:Copy a DAO Tabledef Including User-Defined Properties
	
	Additional query words: kbdsupport kbgrpvbdb
	
	======================================================================
	Keywords          : kbDAOsearch kbJET kbGrpDSVBDB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600
	Version           : WINDOWS:5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
