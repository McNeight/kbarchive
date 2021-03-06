---
layout: page
title: "Q216391: BUG: VSS History Not Updated for Modified Word Documents"
permalink: /kb/216/Q216391/
---

## Q216391: BUG: VSS History Not Updated for Modified Word Documents

{% raw %}

	Article: Q216391
	Product(s): Microsoft SourceSafe
	Version(s): WINDOWS:2000,6.0,97
	Operating System(s): 
	Keyword(s): kbinterop wordnt word97 ntword kbSSafe600bug
	Last Modified: 03-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe for Windows, version 6.0, used with:
	   - Microsoft Word 97 for Windows 
	   - Microsoft Word 2000 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The file history is not updated when a Word document is checked out, modified,
	and checked into Visual SourceSafe.
	
	RESOLUTION
	==========
	
	To work around the problem, you can do either of the following:
	
	- From the Word Tools menu, select Options, and click the Save tab. Clear the
	  Allow Fast Saves option. Click OK.
	
	  -or-
	
	- From the Visual SourceSafe Tools menu, select Options, and click the General
	  tab. Make sure "Check-In unchanged files" is set to Check In.
	
	  -or-
	
	- From the Visual SourceSafe, Tools menu, select Options, and click the Local
	  Files tab. Make sure "Compare files by:" is set to anything other than
	  Checksum.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. From the Visual SourceSafe Tools menu, select Options. On the General tab,
	  set "Check-In unchanged files" to Undo Check Out. On the Local Files tab, set
	  Compare files by: to Checksum.
	
	2. Add a Word document to a project in Visual SourceSafe.
	
	3. Check out the Word document and specify a working folder if necessary.
	
	4. Open the document in Word.
	
	5. From the Word Tools menu, select Options, and click the Save tab when the
	  Options dialog box appears.
	
	6. Select the Allow Fast Saves option if it is cleared, and click OK.
	
	7. Make changes to the document.
	
	8. Save the document by going to the File menu and clicking Save.
	
	9. Close the document in Word.
	
	10. Go the Visual SourceSafe Explorer and check in the Word document.
	
	11. Right-click the Word document and select the Show History option. The
	  history will display one version. This is the version created when the file
	  was added to Visual SourceSafe.
	
	REFERENCES
	==========
	
	For more information, see the following articles in the Microsoft Knowledge
	Base:
	
	  Q192480 WD97: Frequently Asked Questions About "Allow Fast Saves
	
	  Q71999 WD97: How to Disable the FastSave Option in Word for Windows
	
	Additional query words: version fast save checksum
	
	======================================================================
	Keywords          : kbinterop wordnt word97 ntword kbSSafe600bug 
	Technology        : kbSSafeSearch kbAudDeveloper
	Version           : WINDOWS:2000,6.0,97
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
