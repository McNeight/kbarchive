---
layout: page
title: "Q157799: WD97: Letter Wizard Defaults Stored In Normal Template"
permalink: /kb/157/Q157799/
---

## Q157799: WD97: Letter Wizard Defaults Stored In Normal Template

{% raw %}

	Article: Q157799
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbualink97
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Letter Wizard default information is reset to blank if the Normal template
	(Normal.dot) is renamed or deleted.
	
	
	MORE INFORMATION
	================
	
	In Microsoft Word 97 for Windows, all default information for the Letter Wizard
	is now stored as AutoText entries in the Normal.dot template. This is different
	from the other wizards in Word 97 where the default information is stored in the
	Windows Registry. In previous versions of Word (6.0/7.0), this information was
	stored in the Wordwiz.ini file in the Windows directory.
	
	The following lists the items from the Letter Wizard that are stored as AutoText
	entries in the Normal.dot file:
	
	Item                     Letter Wizard Dialog Tab   AutoText Name
	----------------------   ------------------------   -------------------
	
	Sender's Name            Sender Info                Signature
	Job Title                Sender Info                Signature Job Title
	Company                  Sender Info                Signature Company
	Writer/Typist Initials   Sender Info                Reference Initials
	Recipient Name           Recipient Info             Inside Address Name
	
	NOTE: If you rename or delete the Normal.dot template, the above information is
	lost. You may want to back up or copy the Normal.dot template.
	
	To Run the Letter Wizard:
	-------------------------
	
	Method 1:
	
	a. On the File menu, Click New.
	
	b. Click the Letters and Faxes tab. Click the Letter Wizard icon, then click OK.
	
	Method 2:
	
	On the Tools menu, click Letter Wizard.
	
	Additional query words: 8.0 word8 word97 letter.wiz
	
	======================================================================
	Keywords          : kbualink97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	
	=============================================================================
	

{% endraw %}
