---
layout: page
title: "Q139348: HOWTO: Set a Filter Using an Item Selected from a Combo Box"
permalink: /kb/139/Q139348/
---

## Q139348: HOWTO: Set a Filter Using an Item Selected from a Combo Box

{% raw %}

	Article: Q139348
	Product(s): Microsoft FoxPro
	Version(s): 
	Operating System(s): 
	Keyword(s): kbnokeyword kbvfp300 kbvfp500 kbvfp600
	Last Modified: 03-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article shows by example how to use the item selected in a combo box to
	filter what is displayed in a second combo box.
	
	MORE INFORMATION
	================
	
	The Scenario
	------------
	
	Say you have two combo boxes on a form. The first reflects a field in the parent
	table, and the second reflects the child records related to the parent value
	picked from the possible parent values presented in the first combo box.
	
	Step-by-Step Procedure
	----------------------
	
	1. Create a new form.
	
	2. Right-click the form, and click Data Environment. Then right-click the Data
	  Environment window, and add the Customer table from \Vfp\Samples\Data. In
	  Visual FoxPro 6.0 the Customer table can be found in home(2)+"data".
	
	3. Right-click the Data Environment window again, and add the Orders table from
	  \Vfp\Samples\Data. In Visual FoxPro 6.0 the Orders table can be found in
	  home(2)+"data".
	
	4. Place a combo box on the form. Change its RowSource property to
	  Customer.cust_id and its RowSourceType property to 6 - Fields.
	
	5. Add the following code to the InteractiveChange event for the combo box:
	
	  
	
	     thisform.dataenvironment.cursor2.filter= ;
	        "alltrim(cust_id)='"+alltrim(this.value)+"'"
	
	6. Place a second combo box on the form. Change its RowSource property to
	  Orders.to_name and its RowSourceType property to 6 - Fields.
	
	7. Save and run the form.
	
	8. Select a customer ID from the first combo box. Click the down arrow on the
	  second combo box, and note the records displayed in the second combo box
	  relates to the customer ID you selected from the first combo box.
	
	NOTE: If you place the line of code in Step 5 in the Valid event for the combo
	box, the event fires twice - once when you select an item from the combo box and
	again when the combo box loses the focus. Placing the code in the
	InteractiveChange event avoids this behavior.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbnokeyword kbvfp300 kbvfp500 kbvfp600 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP500 kbVFP600
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
