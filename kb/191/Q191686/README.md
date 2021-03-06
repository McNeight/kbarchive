---
layout: page
title: "Q191686: BUG: Focus Changes Even Though Grid Text Box Valid Returns .F."
permalink: /kb/191/Q191686/
---

## Q191686: BUG: Focus Changes Even Though Grid Text Box Valid Returns .F.

{% raw %}

	Article: Q191686
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0,3.0b,5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In a grid, focus leaves the text box control to go to the control you are
	clicking even though the Valid method of the text box returns .F. or 0. However,
	the focus remains unchanged in the text box control when you are tabbing out to
	move to a different control.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a new form, named mytest.
	
	2. Add a one column grid to the form and two Command buttons.
	
	3. In the Load event of the form, insert the following code:
	
	        SET SAFETY OFF
	        CREATE TABLE xyz (name C(10))
	        INSERT INTO xyz VALUES ("test")
	
	4. In the Valid method of the text box in the grid, place the following code:
	
	        RETURN .F.
	
	5. Save and run the form.
	
	After you open the form, click Command button 1. The "Invalid input" message
	appears and then the focus shifts from the text box in the grid to the Command
	button. At the same time, the grid's text box also has a black border indicating
	that it also has focus. At this point, if you press the Tab key, the focus moves
	to the other command button. Apparently, the focus is no longer with the text
	box even though the Valid method in the text box is returning false.
	
	Additional query words: kbVFp600bug kbVFp500abug kbVFp300bbug kbCtrl kbContainer
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP300b kbVFP500 kbVFP600 kbVFP500a
	Version           : WINDOWS:3.0,3.0b,5.0,5.0a,6.0
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
