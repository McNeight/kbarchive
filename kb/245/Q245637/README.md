---
layout: page
title: "Q245637: Some LARGE LUN Numbers Are Not Available to the Computer"
permalink: /kb/245/Q245637/
---

## Q245637: Some LARGE LUN Numbers Are Not Available to the Computer

{% raw %}

	Article: Q245637
	Product(s): Microsoft Windows NT
	Version(s): 4.0 SP5,4.0 SP6
	Operating System(s): 
	Keyword(s): kbWinNT400PreSP7Fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 4.0 SP5, 4.0 SP6 
	- Microsoft Windows NT Workstation versions 4.0 SP5, 4.0 SP6 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you configure a computer to use LARGE LUN Support, such as on a Fibre
	Channel controller, some of the LUNs assigned to disks or other devices are not
	visible to other system drivers or the computer.
	
	Only 231 of the 256 possible LUNs are visible. The LUNs that are not visible are
	in the following ranges:
	
	  64 to 71
	  128 to 135
	  192 to 199
	  255
	
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
	
	  Date        Time     Size     File name     Platform
	  ----------------------------------------------------
	  10/25/1999  01:57p   35,504   Scsiport.sys  i386
	  10/25/1999  01:56p   56,400   Scsiport.sys  alpha
	
	For additional information on LargeLun support in Windows, click the article
	number below to view the article in the Microsoft Knowledge Base:
	
	  Q310072 Adding Support for More Than Eight LUNs in Windows Server
	
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT 4.0.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbWinNT400PreSP7Fix 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400search kbWinNT400search kbWinNTW400sp5 kbWinNTSsearch kbWinNTS400sp6 kbWinNTS400sp5 kbWinNTS400search kbWinNTW400sp6
	Version           : :4.0 SP5,4.0 SP6
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
