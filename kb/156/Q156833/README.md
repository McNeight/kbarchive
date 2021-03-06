---
layout: page
title: "Q156833: STOP 0X7B Inaccessible Boot Device When Starting Windows NT"
permalink: /kb/156/Q156833/
---

## Q156833: STOP 0X7B Inaccessible Boot Device When Starting Windows NT

{% raw %}

	Article: Q156833
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbsetup
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You have a NEC Versa 4000 computer with the following configuration:
	
	- IDE controller-1: IDE hard drive (master) and IDE hard drive (slave)
	
	- IDE controller-2: IDE CD-ROM drive (master/standalone)
	
	When you add the third IDE hard drive as master on the second channel and
	reconfigure the CD-ROM drive to be a slave, the following error message will be
	displayed:
	
	  STOP 0x0000007B Inaccessible Boot device
	
	The same problem will be noticed with similarly configured systems using
	combination IDE disk and IDE CD-ROM drive peripheral devices.
	
	
	CAUSE
	=====
	
	This problem is caused by the Atapi.sys driver not functioning properly in this
	configuration.
	
	WORKAROUND
	==========
	
	To work around this problem, replace the Atapi.sys driver found in the
	%SystemRoot%\System32\Drivers directory with the Atapi.sys driver from Windows
	NT 4.0 Service Pack 3 or later.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 4.0. This
	problem was first corrected in Windows NT 4.0 Service Pack 3.
	
	Additional query words: ghost
	
	======================================================================
	Keywords          : kbsetup 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	
	=============================================================================
	

{% endraw %}
