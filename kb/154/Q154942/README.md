---
layout: page
title: "Q154942: IIS Virtual Root Cannot Be Browsed on a SAMBA or WIN95 Share"
permalink: /kb/154/Q154942/
---

## Q154942: IIS Virtual Root Cannot Be Browsed on a SAMBA or WIN95 Share

{% raw %}

	Article: Q154942
	Product(s): Microsoft Windows NT
	Version(s): 1.0,3.5,3.51
	Operating System(s): 
	Keyword(s): 
	Last Modified: 13-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51 
	- Microsoft Windows NT Server versions 3.5, 3.51 
	- Microsoft Internet Information Server version 1.0 
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	A virtual root cannot be set up using a SAMBA or a Windows 95 server share.
	
	
	CAUSE
	=====
	
	This is caused by not defaulting back to file allocation table (FAT) on the
	GetVolumeType call when in a failure condition.
	
	RESOLUTION
	==========
	
	Set the default condition in GetVolumeType to FAT, or obtain the fix referenced
	below.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 3.51. This
	problem was corrected in the latest Windows NT 3.51 U.S. Service Pack. For
	information on obtaining the Service Pack, query on the following word in the
	Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	MORE INFORMATION
	================
	
	The third-party products discussed here are manufactured by vendors independent
	of Microsoft; we make no warranty, implied or otherwise, regarding these
	products' performance or reliability.
	
	Additional query words: prodnt 3.50 3.51
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNT350search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search kbiisSearch kbWin95search kbiis100 kbZNotKeyword3
	Version           : :1.0,3.5,3.51
	
	=============================================================================
	

{% endraw %}
