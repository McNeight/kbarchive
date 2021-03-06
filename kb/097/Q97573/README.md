---
layout: page
title: "Q97573: Using DoubleSpace with LANtastic"
permalink: /kb/097/Q97573/
---

## Q97573: Using DoubleSpace with LANtastic

{% raw %}

	Article: Q97573
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:6.0,6.2,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 03-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 6.0, 6.2, 6.22 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This information applies to both Microsoft DoubleSpace and Microsoft DriveSpace.
	For MS-DOS 6.22, use DRVSPACE in place of DBLSPACE for commands and filenames.
	
	This article describes the use of LANtastic software with DoubleSpace and
	contains information not found in the NETWORKS.TXT file. For background
	information, section 6 of the NETWORKS.TXT file is included here:
	
	  You cannot use DoubleSpace to compress a drive on a LANtastic server because
	  all local drives are viewed as network drives. To compress a drive, disable
	  the server service by typing REM and space in front of the server command in
	  your AUTOEXEC.BAT file, and restarting the computer. Then run DoubleSpace to
	  compress the drive. After you run DoubleSpace, remove the REM command from
	  your AUTOEXEC.BAT file.
	
	  After you compress a drive on a server, some DoubleSpace features-- such as
	  the LIST, CHKDSK, MOUNT, and UNMOUNT features--will not work correctly unless
	  you stop the server service.
	
	MORE INFORMATION
	================
	
	The problem described above occurs only when the machine is running the
	LANtastic server software. You can use DoubleSpace on a drive if the server
	software is not loaded.
	
	When a network drive is assigned to a DoubleSpace drive and you try to run a
	DoubleSpace command, the following message is displayed
	
	  A network drive has been connected using letter <X>. To use drive
	  <X>, you must first remove the network drive or assign it a different
	  drive letter.
	
	where <X> is the DoubleSpace drive.
	
	If you try to mount a DoubleSpace drive while the LANtastic server software is
	running, you receive the error message:
	
	  Dblspace cannot mount drive <X> because of an unrecognized error(#105).
	
	Because LANtastic servers make all local drives appear as network drives, most
	DoubleSpace operations will not work correctly. This is consistent with most
	MS-DOS-based peer-to-peer networks.
	
	If are loading LANtastic NODERUN.EXE, AILANBIO.EXE, or REDIR.EXE, DoubleSpace has
	the following problems with floppy disks:
	
	- DoubleSpace thinks the floppy disk drive is a network drive; therefore, its
	  functions do not access it.
	
	- When compressing a floppy disk, DoubleSpace reboots the system twice (as it
	  would if you were compressing a hard disk).
	
	- When explicitly mounting or compressing a floppy disk, DoubleSpace puts an
	  ActivateDrive line in the DBLSPACE.INI file (as if it were a hard disk).
	  Every time the system boots, the floppy disk drive is recalibrated multiple
	  times during the boot process (usually making a lot of noise).
	
	In addition, ScanDisk refuses to check the floppy disk.
	
	To work around this problem, always reboot the system without the LANtastic
	terminate-and-stay-resident (TSR) programs before compressing floppy disks and
	don't explicitly mount a floppy disk while the terminate-and-stay-resident (TSR)
	programs are running.
	
	
	The product included here is manufactured by LANtastic, a vendor independent of
	Microsoft; we make no warranty, implied or otherwise, regarding this product's
	performance or reliability.
	
	Additional query words: 6.00 6.20 mode dblspace double space net floppies diskette
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS622 kbMSDOS620 kbMSDOS600
	Version           : MS-DOS:6.0,6.2,6.22
	
	=============================================================================
	

{% endraw %}
