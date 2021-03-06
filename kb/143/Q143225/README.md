---
layout: page
title: "Q143225: FP: HTTP Code 501 Error Opening, Creating Web"
permalink: /kb/143/Q143225/
---

## Q143225: FP: HTTP Code 501 Error Opening, Creating Web

{% raw %}

	Article: Q143225
	Product(s): Word Front Page
	Version(s): 1.0,1.1
	Operating System(s): 
	Keyword(s): kberrmsg kbusage kbdta
	Last Modified: 13-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FrontPage 97 for Windows with Bonus Pack 
	- Microsoft FrontPage for Windows, versions 1.0, 1.1 
	-------------------------------------------------------------------------------
	
	For a Microsoft FrontPage 2000 version of this article, see Q205700.
	
	For a Microsoft FrontPage 98 version of this article, see Q194061.
	
	SYMPTOMS
	========
	
	When you try to open or create a Web you get an "HTTP error 501" error message.
	
	CAUSE
	=====
	
	FrontPage cannot properly communicate with the server extensions.
	
	RESOLUTION
	==========
	
	To resolve this error, follow these steps:
	
	1. Verify that you can browse to the server using your Web browser.
	
	2. Run the Server Administrator to verify that the server extensions are
	  installed. If they are not installed, install the server extensions.
	
	3. Check the Error.log file for out-of-memory errors and verify the amount of
	  physical and virtual memory available. Make sure that you are using at least
	  a 20 (mebabyte) MB permanent swap file. You should have at least 16 MB of
	  random access memory (RAM).
	
	For additional information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q169529 FP97: How to Install FrontPage Server Extensions for IIS 3.0
	
	  Q167931 How to Install FrontPage Server Extensions for MSPWS
	
	  Q161845 FP97: How to Upgrade the FrontPage Server Extensions
	
	  Q156842 How to Install FrontPage Server Extensions for IIS
	
	Additional query words: front page server vermeer 501 browsing browses error code
	
	======================================================================
	Keywords          : kberrmsg kbusage kbdta 
	Technology        : kbFrontPageSearch kbFrontPage1xSearch kbFrontPage97Search kbZNotKeyword3 kbFrontPage100 kbFrontPage110
	Version           : :1.0,1.1
	Hardware          : x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
