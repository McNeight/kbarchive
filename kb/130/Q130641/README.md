---
layout: page
title: "Q130641: MS-DOS-Based Application Hangs on Beep Under Windows NT"
permalink: /kb/130/Q130641/
---

## Q130641: MS-DOS-Based Application Hangs on Beep Under Windows NT

{% raw %}

	Article: Q130641
	Product(s): Microsoft Windows NT
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51 
	- Microsoft Windows NT Server versions 3.5, 3.51 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you run an MS-DOS-based application in full screen mode under Windows NT on
	an Intel-based computer, the application may stop responding (hang) when it
	tries to print ASCII \007 (CHR$ 7, ^G). The application runs fine in a window.
	
	This problem occurred on several computer models from Siemens-Nixdorf (SNI) and
	on an Intel L486 Professional Workstation. All machines were using Phoenix BIOS
	1.x and an ET4000W32p-based graphics adapters.
	
	CAUSE
	=====
	
	In full screen mode, Windows NT allows the video BIOS to handle screen output
	for enhanced MS-DOS compatibility. Some video BIOS hand off this request to the
	system BIOS. The Phoenix BIOS version 1.x tries to generate the beep using
	hardware that has not been virtualized by Windows NT.
	
	WORKAROUND
	==========
	
	To work around this problem:
	
	- Run the application in a window.
	
	  -or-
	
	- Replace the graphics adapter with one which handles CHR$7.
	
	
	If you are using a Siemens-Nixdorf computer, you can contact your dealer or the
	manufacturer for an updated system BIOS.
	
	Additional query words: 3.10 3.50 3.51 prodnt windowed
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNT350search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search
	
	=============================================================================
	

{% endraw %}
