---
layout: page
title: "Q33112: Removing BACKUP.??? and CONTROL.??? from a Backup Disk"
permalink: /kb/033/Q33112/
---

## Q33112: Removing BACKUP.??? and CONTROL.??? from a Backup Disk

{% raw %}

	Article: Q33112
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:3.x,4.x,5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 3.1, 3.2, 3.21, 3.3, 3.3a, 4.0, 4.01, 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When the BACKUP command from MS-DOS versions 3.x and later are used, it creates
	two files on the disk in which to store information. These files are BACKUP.???
	and CONTROL.???, where the ??? are replaced with disk-sequence number in the
	backup (e.g. 001, 002, 003, etc.).
	
	When backing up to a hard drive, these files both have the extension .001 and are
	always placed in a subdirectory called \BACKUP. These files are protected from
	accidental erasure by setting them with a read-only flag. If you want to delete
	these files from a disk without reformatting, you must use the ATTRIB command to
	clear the read-only flag. The following is an example of how to use the ATTRIB
	command:
	
	  ATTRIB -R CONTROL.???
	  ATTRIB -R BACKUP.???
	
	After using the ATTRIB command to clear the read-only flags on the files, use the
	DEL command to delete the files.
	
	Additional query words: 3.30 3.30a 4.00 5.00 noupd
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS321 kbMSDOS400 kbMSDOS320 kbMSDOS330a kbMSDOS310 kbMSDOS500 kbMSDOS330 kbMSDOS401
	Version           : MS-DOS:3.x,4.x,5.0
	
	=============================================================================
	

{% endraw %}
