---
layout: page
title: "Q177071: OFF97: IPF Quitting with File Containing Long Property Strings"
permalink: /kb/177/Q177071/
---

## Q177071: OFF97: IPF Quitting with File Containing Long Property Strings

{% raw %}

	Article: Q177071
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kberrmsg word97
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	- Microsoft Outlook 97 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you close a document and then quit Microsoft Word, you may receive the
	following error message:
	
	  This program has performed an illegal operation and will be shut down. If the
	  problem persists, contact the program vendor.
	
	  If you click Details, you receive the following message:
	
	  WINWORD caused an invalid page fault in module WINWORD.EXE.
	
	If you close a Microsoft PowerPoint presentation and then quit Microsoft
	PowerPoint, you may receive the following error message:
	
	  PowerPoint encountered an error that it could not correct.
	
	CAUSE
	=====
	
	The problem occurs if both of the following are true:
	
	- The file properties keywords contain more than 255 characters.
	
	  -and-
	
	- Journaling of Microsoft Word or Microsoft PowerPoint is enabled in Microsoft
	  Outlook 97.
	
	
	WORKAROUND
	==========
	
	Use one of the following methods to work around the problem.
	
	Method 1: Reduce the Length of the Keywords
	-------------------------------------------
	
	The problem occurs only if the file keywords contain more than 255 characters. If
	you delete or shorten the document keywords so that they contain fewer than 255
	characters, the problem will not occur.
	
	Method 2: Disable Outlook Journaling of Word or PowerPoint
	----------------------------------------------------------
	
	Outlook journaling is a feature in Microsoft Outlook that tracks and records when
	files are opened, closed, or modified. If you disable this feature for Microsoft
	Word and Microsoft PowerPoint, the problem will no longer occur on that
	particular computer. To disable Outlook journaling for Microsoft Word or
	Microsoft PowerPoint, follow these steps:
	
	1. Start Microsoft Outlook 97.
	
	2. On the Tools menu, click Options.
	
	3. Click the Journal tab.
	
	4. Click to clear the "Always record files from Microsoft Word" or the "Always
	  record files from Microsoft PowerPoint" check boxes, and then click OK.
	
	5. Quit and then restart Microsoft Outlook 97.
	
	NOTE: When working with a file that is opened by multiple users, Outlook
	journaling needs to be disabled on each workstation that is opening the file.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article. This problem has been corrected in Microsoft
	Outlook 98.
	
	MORE INFORMATION
	================
	
	This problem does not occur with other file properties because they will only
	accept a maximum of 255 characters.
	
	This problem does not occur in Microsoft Excel because Microsoft Excel does not
	support journaling for the keyword strings.
	
	REFERENCES
	==========
	
	For more information about Outlook journaling, please see the following article
	in the Microsoft Knowledge Base:
	
	  Q161032 OL97: Blank Item in Deleted Items Folder While Journaling
	
	For more information about Outlook journaling, click the Office Assistant in
	Microsoft Outlook, type "journaling," click Search, and then click one of the
	topics.
	
	For more information about finding documents using keywords, click the Office
	Assistant in Microsoft Word, type "keyword search," click Search, and then click
	"Find Files".
	
	NOTE: If the Assistant is hidden, click the Office Assistant button on the
	Standard toolbar. If Word Help is not installed on your computer, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q120802 Office: How to Add/Remove a Single Office Program or Component
	
	Additional query words: findfile ipf ppt97
	
	======================================================================
	Keywords          : kberrmsg word97 
	Technology        : kbWordSearch kbOutlookSearch kbWord97 kbWord97Search kbZNotKeyword2 kbOutlook97Search kbZNotKeyword3
	Version           : WINDOWS:97
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
