---
layout: page
title: "Q103934: How to Add More Than Two IDE or ESDI Drives in Windows NT"
permalink: /kb/103/Q103934/
---

## Q103934: How to Add More Than Two IDE or ESDI Drives in Windows NT

{% raw %}

	Article: Q103934
	Product(s): Microsoft Windows NT
	Version(s): winnt:3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): kbhw kbHardware
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 3.1 
	- Microsoft Windows NT Workstation version 3.1 
	- Microsoft Windows NT Advanced Server, version 3.1 
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it
	if a problem occurs. For information about how to do this, view the
	"Restoring the Registry" Help topic in Regedit.exe or the "Restoring a
	Registry  Key" Help topic in Regedt32.exe.
	
	SUMMARY
	=======
	
	If a computer has more than two IDE or ESDI hard disk controllers and needs an
	MS-DOS-based device driver to use the extra drives, Windows NT may not be able
	to use the extra drives by default.
	
	
	To configure more than two IDE or ESDI hard disk controllers with Windows NT, the
	Windows NT Registry must be modified to add the information about the additional
	drives. You need technical information about your drives, which should be
	included in the manufacturer's documentation included with them.
	
	NOTE: To make the necessary changes in the Registry, you must be logged on as an
	Administrator.
	
	MORE INFORMATION
	================
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall your operating system. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editor can be solved. Use
	Registry Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" Help topic in Registry Editor (Regedit.exe) or the "Add and Delete
	Information in the Registry" and "Edit Registry Data" Help topics in
	Regedt32.exe. Note that you should back up the registry before you edit it.
	
	Most new computers come with two built in IDE controllers. Each controller (or
	channel) can handle two IDE Hard drives. This procedure should only be necessary
	if you are trying to add a third or higher IDE or ESDI controller or if your
	secondary IDE or ESDI controller is at a non- standard memory address. If the
	drive is at a non-standard address, use the following procedure to add the
	correct address to the Windows NT registry. The registry key name in this case
	would be either 1 or 2.
	
	NOTE: The information in this article applies only to Intel x86 architecture
	computers.
	
	To add support for three or more IDE or ESDI controllers in Windows NT, follow
	these steps:
	
	1. Start Registry Editor (Regedt32.exe), and then locate the following registry
	  key:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Atdisk
	
	2. On the Edit menu, click Add Key, and then create the following key:
	
	  Key Name: PARAMETERS
	  Class: <blank>
	
	3. Open the PARAMETERS key that you created in Step 2.
	
	4. On the Edit menu, click Add Key, and then create the following key:
	
	  Key Name: <number>
	  Class: <blank>
	
	  where <number> is the number of the additional drive, such as 2 for the
	  third drive. For each additional drive, increment the Key Name by 1. In
	  general, you must specify the starting parameter as 2 or higher. This
	  prevents a conflict with the primary or secondary controller that most BIOSs
	  support.
	
	5. Open the key that you created in step 4.
	
	6. On the Edit menu, click Add value, and then add the following values:
	
	  BaseAddress
	  -----------
	  This is the physical address of the Data register for the controller.
	
	  DriveControl
	  ------------
	  This is the physical address of the drive control register of the controller.
	  Often this is 0x206 off of the BaseAddress register.
	
	  Interrupt
	  ---------
	  This is the interrupt that the controller will use.
	
	  NOTE: Set the Data Type of all three entries to REG_DWORD.
	
	7. Quit Registry Editor.
	
	Here is what a sample registry entry looks like for adding a Quantum EZ hard disk
	onto a COMPAQ 486/33L. This computer has a simple ESDI drive as its primary
	controller.
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Atdisk \Parameters\2
	
	  BaseAddress = REG_DWORD 0x320
	  DriveControl = REG_DWORD 0x32e
	  Interrupt = REG_DWORD 0xa
	
	NOTE: On an R4000 ARC computer, you should not have to add anything if you
	configure the IDE adapter for the 0x1f0 or 0x170 memory address.
	
	Additional query words: 3.10 gateway multiple eide second tertiary
	
	======================================================================
	Keywords          : kbhw kbHardware 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTW310 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS310 kbWinNTAdvSerSearch kbWinNTAdvServ310 kbWinNTS351search kbWinNTS350search kbWinNTS310search kbWinNT310Search kbWinNTW310Search
	Version           : winnt:3.5,3.51,4.0
	
	=============================================================================
	

{% endraw %}
