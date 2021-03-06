---
layout: page
title: "Q140598: FIX: AppendOnly Snapshot Recordset Update() Causes Error"
permalink: /kb/140/Q140598/
---

## Q140598: FIX: AppendOnly Snapshot Recordset Update() Causes Error

{% raw %}

	Article: Q140598
	Product(s): Microsoft C Compiler
	Version(s): 2.00 2.10 2.20
	Operating System(s): 
	Keyword(s): kbDatabase kbMFC kbODBC kbVCkbbuglist kbfixlist
	Last Modified: 03-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), included with:
	   - Microsoft Visual C++, 32-bit Editions, versions 2.0, 2.1, 2.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Opening a recordset as an append-only snapshot with no cursor library support
	leads to an internal application error (ICE) when Update() is called to commit
	an AddNew(). A CDBException is thrown and the following error is displayed in
	the output window of the debugger (DB tracing enabled):
	
	In Visual C++ 2.x using the Microsoft Access 7.0 driver:
	
	  
	
	  Error: failure updating record.
	  Invalid argument value
	  State:S1009,Native:57,Origin:[Microsoft][ODBC Microsoft Access
	  7.0 Driver]
	
	This happens when the cursor library is inhibited from loading by passing FALSE
	as the last parameter to CDatabase Open() prior to opening the recordset or if
	the cursor library fails to load for any reason.
	
	CAUSE
	=====
	
	A snapshot recordset relies on the cursor library for additions or updates to
	the database. If the cursor library is not loaded, the recordset becomes
	read-only and does not allow additions or updates. In this case, the recordset
	member variable m_bUpdatable is correctly set to FALSE, but due to a bug in MFC,
	if the recordset is opened appendOnly, m_bAppendable is still set to TRUE.
	AddNew() checks m_bAppendable and continues to process the addition. Eventually,
	Update() is called. Because the cursor library is not present, Update() calls
	CRecordset::ExecuteSetPosUpdate() to use SQLSetPos for performing the update.
	SQLSetPos fails and generates the error message.
	
	If the appendOnly option is not specified for the snapshot, then both
	m_bUpdatable and m_bAppendable are set properly and the expected behavior
	occurs:
	
	- This error message is displayed in the output window when AddNew() is called:
	  "Recordset is read-only."
	
	- A CDBException is thrown.
	
	RESOLUTION
	==========
	
	Snapshots become read-only if the cursor library is not loaded. To get an
	updatable and appendable snapshot, make sure the cursor library is properly
	loaded by the application.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This problem was corrected in Visual C++ version 4.0.
	
	Additional query words: 2.00 3.00 2.10 3.10 2.20 3.20
	
	======================================================================
	Keywords          : kbDatabase kbMFC kbODBC kbVC kbbuglist kbfixlist
	Technology        : kbAudDeveloper kbMFC
	Version           : 2.00 2.10 2.20
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
