---
layout: page
title: "Q237424: Error Message on a Blue Screen When Using Bookman Old Style Font"
permalink: /kb/237/Q237424/
---

## Q237424: Error Message on a Blue Screen When Using Bookman Old Style Font

{% raw %}

	Article: Q237424
	Product(s): Microsoft Windows NT
	Version(s): 2000,4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4,4.0 SP5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3, 4.0 SP4, 4.0 SP5 
	- Microsoft Windows NT Server, Enterprise Edition versions 4.0, 4.0 SP4, 4.0 SP5 
	- Microsoft Windows NT Workstation versions 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3, 4.0 SP4, 4.0 SP5 
	- Microsoft Windows 2000 Server 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you are using the Bookman Old Style font, you may receive a stop error
	message on a blue screen that is similar to one of the following:
	
	   - STOP 0x0000001E (0xc0000005, 0xfccc6add, 0x00000001, 0x013b8020)
	
	NOTE: The second and fourth parameters may vary depending on the system
	configuration, but the second parameter is always within Vga.dll.
	
	   - STOP 0x00000050 (0xca8971d0, 0x00000001, 0x0000000, 0x00000000)
	
	NOTE: The parameters may vary depending on the system configuration.
	
	CAUSE
	=====
	
	This problem can occur when the video driver attempts to process a glyph with a
	negative "x" position written to a particular screen position.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem.
	
	To resolve this problem, contact Microsoft Product Support Services to obtain the
	fix. For a complete list of Microsoft Product Support Services phone numbers and
	information on support costs, please go to the following address on the World
	Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English-language version of this fix should have the following file
	attributes or later:
	
	  Date       Time             Size     File name     Platform
	  ------------------------------------------------------------
	  8/18/99    4:53p            161,020  Bookosi.ttf   x86
	  8/18/99    4:53p            161,020  Bookosi.ttf   Alpha
	
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	Both the "stop 0x1E" error message and the "stop 0x50" error message have been
	received when processing a glyph of the letter M in the Bookman Old Style italic
	font. The "stop 0x1E" error message is commonly received on a Windows NT
	Server-based or a Windows NT Workstation-based computer.
	
	
	The "stop 0x50" error message is commonly received on a Windows NT Terminal
	Server-based computer. It occurs in the Win32k.sys file rather than the Vga.dll
	file because remote sessions do not use the server's video driver.
	
	
	
	Additional query words: 0xa
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400search kbwin2000Serv kbWinNTW400sp5 kbWinNTW400sp3 kbWinNTW400sp1 kbWinNTSsearch kbWinNTSEnt400sp4 kbWinNTS400sp4 kbWinNTS400sp2 kbWinNTS400search kbwin2000ServSearch kbWinNTW400 kbWinNT400search kbWinNTW400sp4 kbWinNTW400sp2 kbWinNTSEntSearch kbWinNTSEnt400sp5 kbWinNTSEnt400 kbWinNTS400sp5 kbWinNTS400sp3 kbWinNTS400sp1 kbWinNTS400 kbwin2000Search
	Version           : :2000,4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4,4.0 SP5
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
