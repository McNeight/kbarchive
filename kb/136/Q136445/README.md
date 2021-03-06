---
layout: page
title: "Q136445: Error Using SyQuest 5110 88MB-C Removable Drive In Windows NT"
permalink: /kb/136/Q136445/
---

## Q136445: Error Using SyQuest 5110 88MB-C Removable Drive In Windows NT

{% raw %}

	Article: Q136445
	Product(s): Microsoft Windows NT
	Version(s): 3.5,3.51
	Operating System(s): 
	Keyword(s): 
	Last Modified: 13-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51 
	- Microsoft Windows NT Server versions 3.5, 3.51 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you start Windows NT with a 44 megabyte (MB) cartridge in the SyQuest 5110
	88MB-C drive, the following error message appears:
	
	  The drive is not ready for use; It's door may be open. Please check drive
	  \device\harddiskx\partition0 and make sure that a disk is inserted and that
	  the drive door is closed.
	
	where x is the SCSI hard disk number. The following system event appears in Event
	Viewer:
	
	  Event ID: 5
	  Source: Scsidisk
	  Type: Error
	  Description: The device, \device\hardiskx\partition0 is not ready for access
	  yet.
	
	where x is the SCSI hard disk number. In addition, File Manager displays a
	ghosted drive letter that does not exist.
	
	NOTE: The SyQuest 5110 88MB-C drive can perform both read and write requests to
	the 44 MB media. This drive model is not listed in the Windows NT Hardware
	Compatibility List (HCL).
	
	WORKAROUND
	==========
	
	To work around this problem, insert the cartridge after you log on to Windows
	NT. For more information, contact Syquest Technical Support at (510) 226-4000.
	
	
	The 5110 88MB-C is manufactured by SyQuest, a vendor independent of Microsoft; we
	make no warranty, implied or otherwise, regarding this product's performance or
	reliability.
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNT350search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search
	Version           : :3.5,3.51
	
	=============================================================================
	

{% endraw %}
