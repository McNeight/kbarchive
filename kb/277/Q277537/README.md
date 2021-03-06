---
layout: page
title: "Q277537: Error Message When You Open a Notepad File on IBM AS400"
permalink: /kb/277/Q277537/
---

## Q277537: Error Message When You Open a Notepad File on IBM AS400

{% raw %}

	Article: Q277537
	Product(s): Microsoft Windows NT
	Version(s): 4.0,4.0 SP6
	Operating System(s): 
	Keyword(s): kberrmsg kbfile kbHardware
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 4.0, 4.0 SP6, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you open Notepad to view a file on an IBM AS400 server, you may receive the
	following error message:
	
	  "The specified server cannot perform the requested operation".
	
	CAUSE
	=====
	
	This problem can occur when the network redirector (Rdr.sys) incorporates
	additional checks to validate data that is returned from a remote server for the
	QueryInformationFile function. If less than the full structure size of data that
	you expect (but a minimum structure size that is still valid) is returned from a
	remote server, the client redirector returns the following error message to
	Notepad:
	
	  STATUS_INVALID_NETWORK_RESPONSE NTSTATUS 0xC00000C3
	  "The network responded incorrectly".
	
	Notepad maps this error to the following error:
	
	  ERROR_BAD_NET_RESP WINERROR 0x57
	  "The specified server cannot perform the requested operation".
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Windows NT 4.0 SP7 that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English-language version of this fix should have the following file
	attributes or later:
	
	  Date      Time    Size     File name  Platform
	  ----------------------------------------------
	  10/23/00  7:23pm  265,904  Rdr.sys    Intel
	  10/23/00  7:08pm  519,216  Rdr.sys    Alpha
	
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg kbfile kbHardware 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbNTTermServ400 kbNTTermServ400sp6 kbNTTermServSearch
	Version           : :4.0,4.0 SP6
	Hardware          : ALPHA x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
