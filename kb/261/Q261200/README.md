---
layout: page
title: "Q261200: HTTP 500 Error Displays Instead of ASP Error from 500-100.asp"
permalink: /kb/261/Q261200/
---

## Q261200: HTTP 500 Error Displays Instead of ASP Error from 500-100.asp

{% raw %}

	Article: Q261200
	Product(s): Internet Information Server
	Version(s): winnt:5.0
	Operating System(s): 
	Keyword(s): kbOSWin2000
	Last Modified: 05-AUG-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When a .asp file encounters an error, the following standard HTTP 500 error
	message is displayed instead of an error returned by the 500-100.asp file:
	
	  The page cannot be displayed
	  There is a problem with the page you are trying to reach and it cannot be
	  displayed.
	  ...
	  HTTP 500 - Internal server error
	  Internet Explorer
	
	CAUSE
	=====
	
	The .asp file is located on a non-default Web site that, by default, does not
	use the 500-100.asp file for error handling.
	
	NOTE: This behavior is described in the Internet Information Services (IIS)
	product documentation at http://localhost/iishelp/iis/htm/core/iiprstop.htm.
	
	RESOLUTION
	==========
	
	To use the 500-100.asp file for error handling on the non-default Web site,
	Perform the following steps:
	
	1. Start the Internet Service Manager (ISM), which loads the Internet
	  Information Services snap-in for the Microsoft Management Console (MMC).
	
	2. Right-click the appropriate Web site, click New, and then click Virtual
	  Directory.
	
	3. In the Virtual Directory Creation Wizard, click Next. In the Alias text box,
	  type "IISHelp" (without the quotation marks), and then click Next.
	
	4. When you are prompted for the path to the content directory, click Browse,
	  select the WINNT\Help\IisHelp folder, and then click Next.
	
	5. On the Access Permissions page, accept all the defaults, click Next, and then
	  click Finish.
	
	6. Right-click the Web site again, and then click Properties.
	
	7. On the Custom Errors tab, select the "500;100" error line, and then click
	  Edit Properties.
	
	8. In the Message Type list box, select URL, and then type
	  "/iisHelp/common/500-100.asp" (without the quotation marks) in the URL text
	  box.
	
	9. Click OK twice to return to the ISM.
	
	MORE INFORMATION
	================
	
	NOTE: The exact error message displayed by Internet Explorer may vary, depending
	on whether the "Show friendly HTTP error messages" setting in Internet Explorer
	is selected or not.
	
	(c) Microsoft Corporation 2000, All Rights Reserved. Contributions by Kevin
	Zollman, Microsoft Corporation.
	
	
	Additional query words: iis 5 500.100 500100 akz
	
	======================================================================
	Keywords          : kbOSWin2000 
	Technology        : kbiisSearch kbiis500
	Version           : winnt:5.0
	Issue type        : kbprb
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
