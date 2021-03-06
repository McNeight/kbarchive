---
layout: page
title: "Q140489: PRB: One-to-Many Report Prints First Child If Scope Is One"
permalink: /kb/140/Q140489/
---

## Q140489: PRB: One-to-Many Report Prints First Child If Scope Is One

{% raw %}

	Article: Q140489
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:2.5x,2.6x,3.0,3.0b
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b 
	- Microsoft FoxPro for Windows, versions 2.5x, 2.6x 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A one-to-many report with a scope of one record in the parent table does not
	display all the related records in the child table. Only the first related child
	record prints where the tables have a parent and child one-to-many relationship.
	
	CAUSE
	=====
	
	In one-to-many relationships, when you skip through the parent table, the record
	pointer remains on the same parent record until the record pointer moves through
	all related records in the child table.
	
	RESOLUTION
	==========
	
	To have all the related records in the child table print for a specific parent
	record:
	
	- Use the FOR <expL> clause of the REPORT FORM command to identify the
	  record in the parent table.
	
	-or-
	
	- Use the NEXT <expN> clause of the REPORT FORM command where
	  <expN> = the number of child records related to the parent record.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	For more information about how to specify a scope for a report in Visual FoxPro,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q135342 BUG: Scope on Report Command Doesn't Work as It Did in 2.x
	
	Visual FoxPro Steps to Reproduce Behavior
	-----------------------------------------
	
	1. Open the Testdata database located in the \Samples\Data directory under the
	  Main Visual FoxPro directory.
	
	2. Create a new report using the One-to-Many Report Wizard.
	
	  1. Fields from the parent table
	
	     Select Customer for the parent table, and choose any fields.
	
	  2. Fields from the child table
	
	     Select Orders for the child table, and choose any fields.
	
	  3. Relationships
	
	     Customer.cust_id -- Orders.cust_id (should be the default)
	
	  4. Sort order
	
	     Ignore. Go on to Step 5.
	
	  5. Style
	
	     Use the defaults. Go on to Step 6.
	
	  6. Finish
	
	     Choose "Save report for later use" and click Finish.
	
	3. Save the report as Test.frx in the default directory.
	
	4. In the Command window, type:
	
	  " REPORT FORM test RECORD 3 " (without the quotation marks)
	
	  -or-
	
	  " REPORT FORM test NEXT 1" (without the quotation marks)
	
	5. Examine the report. Only the first of thirteen child records prints.
	
	Example Resolution
	------------------
	
	To resolve this behavior, use the FOR clause of the REPORT FORM command, as in
	these examples:
	
	     REPORT FORM Test FOR Cust_Id = "ANTON"
	
	-or-
	
	     REPORT FORM Test FOR RECNO() = 3
	
	-or-
	
	     REPORT FORM Test NEXT x
	
	where x is the number of child records related to the parent record.
	
	Additional query words: 2.50 2.50a 2.50b 2.60 2.60a FoxWin VFoxWin
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbFoxproSearch kbVFP300 kbVFP300b
	Version           : WINDOWS:2.5x,2.6x,3.0,3.0b
	
	=============================================================================
	

{% endraw %}
