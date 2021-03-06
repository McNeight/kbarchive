---
layout: page
title: "Q168824: FIX: Setting ComboBox Control Text in Click Event Wipes Out Text"
permalink: /kb/168/Q168824/
---

## Q168824: FIX: Setting ComboBox Control Text in Click Event Wipes Out Text

{% raw %}

	Article: Q168824
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:5.0,6.0
	Operating System(s): 
	Keyword(s): kbCtrl kbVBp kbVBp500bug kbVBp600bug kbGrpDSVBDB kbDSupport kbVS600sp4fix kbVS600sp5fix
	Last Modified: 24-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When setting the ComboBox control Text property in the Click event of ComboBox
	control, the text always returns blank. This is different behavior than Visual
	Basic 3.0 and Visual Basic 4.0.
	
	RESOLUTION
	==========
	
	Instead of setting the Text property of the ComboBox control in the Click event,
	change it at the LostFocus event by shifting the focus to another control, such
	as TextBox, although it leaves the focus set to the TextBox. To work around
	that, hide a TextBox behind the ComboBox with TabStop property set to False. In
	the GotFocus event of the TextBox, set the focus back to the ComboBox. To place
	a TextBox behind the ComboBox in design time, choose the Send To Back menu
	command from the Format/Order menu. In run time, set the z-order of TextBox to
	1.
	
	The following code example shows how to keep the text of ComboBox control after
	being set at the Click event:
	
	1. Start a new Standard EXE project. Form1 is created by default.
	
	2. Add a TextBox control, Text1, to Form1.
	
	3. Add a ComboBox control, Combo1, to Form1.
	
	4. Place the following code into the General Declarations section of Form1:
	
	        Dim ClickFlag As Integer
	
	        Private Sub Combo1_Click()
	           ClickFlag = True
	           Text1.SetFocus
	        End Sub
	
	        Private Sub Combo1_LostFocus()
	           If ClickFlag = True Then
	              Combo1.Text = Mid(Combo1.Text, 4)
	              ClickFlag = False
	           End If
	        End Sub
	
	        Private Sub Form_Load()
	           ClickFlag = False
	           With Combo1
	               .AddItem "1. Adam"
	               .AddItem "2. Bob"
	               .AddItem "3. Charles"
	           End With
	           Combo1.Text = Mid(Combo1.List(0), 4)
	
	           'Hide Text1 under Combo1
	           Text1.Move Combo1.Left, Combo1.Top, Combo1.Width, Combo1.Height
	           Text1.ZOrder (1)
	           Text1.TabStop = False
	        End Sub
	
	        Private Sub Text1_GotFocus()
	           Combo1.SetFocus
	        End Sub
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug was corrected in the latest service pack for
	Visual Studio 6.0.
	
	For additional information about Visual Studio service packs, click the article
	numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	  Q194295 HOWTO: Tell That a Visual Studio Service Pack Is Installed
	
	You can download the latest Visual Studio service pack from the following
	Microsoft Web site:
	
	  Visual Studio Product Updates
	  (http://msdn.microsoft.com/vstudio/downloads/updates.asp)
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Start a new Standard EXE project. Form1 is created by default.
	
	2. Add a ComboBox control, Combo1, to Form1.
	
	3. Paste the following code into the General Declarations section of Form1:
	
	        Private Sub Combo1_Click()
	           Combo1.Text = Mid(Combo1.Text, 1, 3)
	        End Sub
	
	        Private Sub Form_Load()
	          With Combo1
	            .AddItem "1. Adam"
	            .AddItem "2. Bob"
	            .AddItem "3. Charles"
	          End With
	          Combo1.Text = Mid(Combo1.List(0), 4)
	        End Sub
	
	4. Start the program or press the F5 key.
	
	5. Click one item of the ComboBox control drop-down list and note that the text
	  portion of the ComboBox control is wiped out and becomes blank.
	
	(c) Microsoft Corporation 2000, All Rights Reserved. Contributions by Adrian
	Chiang, Microsoft Corporation
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbCtrl kbVBp kbVBp500bug kbVBp600bug kbGrpDSVBDB kbDSupport kbVS600sp4fix kbVS600sp5fix 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVB500 kbVB600
	Version           : WINDOWS:5.0,6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
