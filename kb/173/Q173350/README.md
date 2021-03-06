---
layout: page
title: "Q173350: WD97: When and Why Link Fixing May Not Work"
permalink: /kb/173/Q173350/
---

## Q173350: WD97: When and Why Link Fixing May Not Work

{% raw %}

	Article: Q173350
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): winword word97 kbwdinternet
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	If you create a Web page using the Word 97 Web Authoring Tools Update, and
	insert links to objects such as files, images, or sounds, the Check Links
	feature may prompt you with options for correcting broken links when you save
	the page.
	
	This article discusses when you may or may not be prompted to fix links, and when
	the link fixing feature may fail to repair the links in your document.
	
	MORE INFORMATION
	================
	
	Conditions Necessary for the Link Fixing Options Dialog Box
	-----------------------------------------------------------
	
	Word displays the Link Fixing Options dialog box when all of the following
	conditions are true:
	
	- You use Save As to save a file for the first time, or to specify a new
	  location for an existing file.
	
	  -and-
	
	- There are relative links (either hyperlinks or image source paths) in the
	  file.
	
	Conditions Preventing the Link Fixing Options Dialog Box
	--------------------------------------------------------
	
	Word does not display the Link Fixing Options dialog box when any of the
	following conditions are true:
	
	- You set the hyperlink base property (base path) of your document. For more
	  information, see the "What is a Hyperlink Base?" section later in this
	  article.
	
	  -or-
	
	- You change the hyperlink base property of your document. Word cannot
	  automatically repair links in this case.
	
	  -or-
	
	- The only images in your document are OLE objects, such as WordArt and
	  Clipart, created in the current editing session.
	
	  -or-
	
	- The only hyperlinks are absolute hyperlinks. Absolute hyperlinks cannot be
	  broken.
	
	Conditions for Failure of Link Fixing
	-------------------------------------
	
	Link fixing may fail to repair the links in your document when any of the
	following conditions are true:
	
	- When your page contains images and you save the page to a network drive, if
	  you choose Update Links instead of Copy Images, the links will point to
	  locations on your computer. For example, you may be able to access the
	  following link
	
	  file:///C:\My Documents\MyPicture.gif
	
	  but other users on the network cannot access it.
	
	  -or-
	
	- When you set the hyperlink base property of your document, and you insert a
	  video or background sound, the video or sound file is never copied to the
	  base path.
	
	  -or-
	
	- When you save the default (index) file of a Web site to a local disk, Word
	  may not be able to locate the images. For example, a default (index) file of
	  a Web site is
	
	  http://www.microsoft.com/
	
	  To avoid this problem, include the HTML file name when opening from a Web
	  site. For example:
	
	  http://www.microsoft.com/default.htm
	
	  Tip:
	
	  If you have a set of documents in a directory on your hard disk and these
	  documents contain links to each other, select "Don't Fix for Hyperlinks" when
	  you save the files to the network drive. This preserves the relative links
	  between files.
	
	What is a Hyperlink Base?
	-------------------------
	
	When you create a hyperlink in a document, the hyperlink can be a fixed file
	location (absolute link), or a relative link. An absolute link contains a full
	address, such as c:\My Documents\Sales.doc. A relative link contains an address
	relative to a base address: the hyperlink base of the containing document.
	
	Use a relative link if you want to move or copy the file that contains the
	hyperlink, or the linked file to a new location. By default, the hyperlink base
	of a document is the location where it is saved, although you may specify any
	location.
	
	For example, assume you have an HTML document called Doc1.htm located in C:\My
	Documents. By default, the hyperlink base is C:\My Documents. Therefore, when
	you insert a relative hyperlink to C:\Windows\Image1.bmp, the following
	hyperlink is inserted into Doc1.htm:
	
	  ..\Windows\Image1.bmp
	
	However, if you specify a different hyperlink base, such as C:\ (and you do not
	move the documents or images), when you insert a relative hyperlink to
	C:\Windows\Image1.bmp, the following hyperlink is inserted into Doc1.htm:
	
	  \Windows\Image1.bmp
	
	Note that the hyperlink is relative to the hyperlink base for Doc1.htm, and not
	the current location of Doc1.htm.
	
	How to Set a Hyperlink Base
	---------------------------
	
	To set a hyperlink base, follow these steps:
	
	1. Open the document you want to set a hyperlink base for.
	
	2. On the File menu, click Properties, and then click the Summary tab.
	
	3. In the Hyperlink Base box, type the base path you want to use for all the
	  relative hyperlinks in this document.
	
	REFERENCES
	==========
	
	For more information about the Web Authoring Tools, please see the following
	articles in the Microsoft Knowledge Base:
	
	  Q163299 WD97: Web Page Authoring Tools AutoUpdate
	
	  Q172745 WD97: Editing Web Browser Path Creates Duplicate Entry
	
	  Q172747 WD97: What's New in the Web Page Authoring Tools Update
	
	  Q173146 WD97: Run from Network Installation for Web Authoring AutoUpdate
	
	  Q172502 WD97: Troubleshooting Setup for the Web AutoUpdate Feature
	
	For more information about setting a base path, click the Office Assistant, type
	"base path" (without the quotation marks), click Search, and then click "Set a
	hyperlink base for a document."
	
	NOTE: If the Assistant is hidden, click the Office Assistant button on the
	Standard toolbar. If Word Help is not installed on your computer, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q120802 Office: How to Add/Remove a Single Office Program or Component
	
	Additional query words: 8.0 8.00
	
	======================================================================
	Keywords          : winword word97 kbwdinternet 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
