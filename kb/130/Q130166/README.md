---
layout: page
title: "Q130166: Data Type Mapping in the Upsizing Wizard"
permalink: /kb/130/Q130166/
---

## Q130166: Data Type Mapping in the Upsizing Wizard

{% raw %}

	Article: Q130166
	Product(s): Microsoft FoxPro
	Version(s): 3.00
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Field names and data types are automatically translated into SQL Server fields
	when a Visual FoxPro table is exported by the Upsizing Wizard. This article
	lists the data type mapping that occurs between Visual FoxPro and SQL when the
	data is exported from the Upsizing Wizard.
	
	The information in this article is also available under many separate topics in
	the Visual FoxPro Help file. Search using "Upsizing Wizard."
	
	MORE INFORMATION
	================
	
	Field names and data types are automatically translated into SQL Server fields
	when a Visual FoxPro table is exported by the Upsizing Wizard. Visual FoxPro
	data types map to SQL Server data types as follows:
	
	                 Visual FoxPro   SQL Server
	  Abbreviation   Data Type       Data Type
	  -----------------------------------------
	  C              Character       char
	  Y              Currency        money
	  D              Date            datetime
	  T              DateTime        datetime
	  B              Double          float
	  F              Float           float
	  G              General         image
	  I              Integer         int
	  L              Logical         bit
	  M              Memo            text
	  N              Numeric         float
	  P              Picture         image
	
	Expressions that Map Directly from Visual FoxPro to SQL Server
	--------------------------------------------------------------
	
	The following expressions are the same on Visual FoxPro and on SQL Server:
	
	  CEILING()    MAX()     PADR()
	  LEN()        MIN()     PROPER()
	  LOG()        PADL()    STR()
	
	Index Type Mapping
	------------------
	
	SQL Server and Visual FoxPro indexes are very similar. The following table shows
	how Visual FoxPro index types are converted to SQL Server index types:
	
	  Visual FoxPro Index Type   SQL Server 4.x Index Type
	  ----------------------------------------------------
	  Primary                    Clustered Unique
	  Candidate                  Unique
	  Unique, Regular            Non-unique
	
	The Upsizing Wizard uses Visual FoxPro tag names as names for indexes on SQL
	Server. If the tag name is a reserved word on the server, the wizard alters the
	tag name by appending the underscore (_) character.
	
	NOTE: SQL Server doesn't support ascending or descending indexes, nor does it
	permit expressions within server indexes. The Upsizing Wizard removes Visual
	FoxPro expressions from index expressions as the index is upsized; only field
	names are sent to the server.
	
	SQL Server Data Types that Force Timestamp Columns
	--------------------------------------------------
	
	If you choose Add Timestamp Field, by default the Upsizing Wizard adds a new
	column with the Timestamp data type if the SQL Server table to be created will
	have any of the following data types:
	
	  binary   varbinary   float
	  real     image       text
	
	Object Mapping
	--------------
	
	The following table summarizes how objects are mapped from Visual FoxPro to SQL
	Server:
	
	  Visual FoxPro objects         SQL Server objects
	  --------------------------------------------------------------------
	  Database                      Database
	  Table                         Table
	  Indexes                       Indexes
	  Field                         Field
	  Default                       Default
	
	  Table validation rule         SQL Server stored procedures,
	                                called from UPDATE and INSERT triggers
	
	  Field validation rule         SQL Server stored procedures,
	                                called from UPDATE and INSERT triggers
	
	  Persistent relationships      Update, Insert, and Delete triggers
	  (where used for referential
	  integrity constraints)
	
	Referential Integrity and Rule Mapping
	--------------------------------------
	
	The following table describes the triggers created by the Upsizing Wizard. Any
	specific trigger might contain code to emulate some or all of the Visual FoxPro
	functionalities listed.
	
	  Trigger           Visual FoxPro Functionality Emulated
	  -----------------------------------------------------------
	  UPDATE            Validation rules (field- and record-level
	                    validation) Referential integrity
	
	  INSERT            Validation rules (field- and record-level
	                    validation) Referential integrity (child
	                    table triggers only)
	
	  DELETE (Parent    Referential integrity
	  table only)
	
	Additional query words: VFoxWin
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	Version           : 3.00
	
	=============================================================================
	

{% endraw %}
