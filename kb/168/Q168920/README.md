---
layout: page
title: "Q168920: Disabling Documents Folder on the Start Menu"
permalink: /kb/168/Q168920/
---

## Q168920: Disabling Documents Folder on the Start Menu

{% raw %}

	Article: Q168920
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the
	registry.
	Before you edit the registry, make sure you understand how to restore it if
	a problem occurs. For information on how to do this, view the "Restoring
	the Registry" online Help topic in Regedit.exe or the "Restoring a Registry
	Key" online Help topic in Regedt32.exe.
	
	SUMMARY
	=======
	
	When you lock down a Windows NT 4.0 client, users still have the Documents
	folder on the Start menu. This article discusses methods to disable the
	Documents folder so that it always reads (Empty).
	
	MORE INFORMATION
	================
	
	To disable the Documents folder on the Start menu, select the procedure
	according to the following three configurations:
	
	- NTFS partition on a computer running Windows NT Workstation 4.0 or Windows NT
	  Server 4.0
	
	- FAT partition on a networked computer running Windows NT Workstation 4.0 or
	  Windows NT Server 4.0
	
	- FAT partition on stand-alone computer running Windows NT Workstation 4.0 or
	  Windows NT Server 4.0
	
	Ideally, the first fix is the easiest to implement and restore. The other
	techniques require editing the registry and are more complex. The last method
	requires disabling the Recycle Bin and this should be used only in the direst of
	situations.
	
	NTFS Partition on a Computer Running Windows NT Workstation 4.0 or Windows NT
	Server 4.0:
	
	1. Log on as the user who needs folder disabled.
	
	2. Go to <winnt systemroot>\Profiles\<username>\Recent
	
	  NOTE: You may have to go into Options (on the View menu) in Windows Explorer
	  and select Show All Files to see Recent, which is a hidden file.
	
	3. Set permissions on Recent so that everyone has read-only access.
	
	  NOTE: On Windows NT Server and in other instances, there may be other users in
	  the Recent permissions. Everyone is the only group that can be there, with
	  only read access.
	
	FAT Partition on a Networked Computer Running Windows NT Workstation 4.0 or
	Windows NT Server 4.0:
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall your operating system. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editor can be solved. Use
	Registry Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" online Help topic in Registry Editor (Regedit.exe) or the "Add and
	Delete Information in the Registry" and "Edit Registry Data" online Help topics
	in Regedt32.exe. Note that you should back up the registry before you edit it.
	
	1. On a server in a network that the workstation can access:
	
	  a. Create a share.
	
	  b. Give users read-only access to the share.
	
	2. On the workstation, log on as the user who needs the folder disabled.
	
	3. Run Regedt32.exe
	
	4. Go to the following registry key:
	
	     HKEY_CURRENT_USER\Software\Microsoft\Windows\Current Version
	     \Explorer
	
	  NOTE: The above registry key is one path; it has been wrapped for readability.
	
	  a. In Shell Folders, set "Recent:REG_SZ:<\\server\read onlyshare>".
	
	  b. In User Shell Folders, set "Recent:REG_EXPAND_SZ:<\\server\ read
	     onlyshare>".
	
	FAT Partition on Stand-Alone Computer Running Windows NT Workstation 4.0 or
	Windows NT Server 4.0:
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall your operating system. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editor can be solved. Use
	Registry Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" online Help topic in Registry Editor (Regedit.exe) or the "Add and
	Delete Information in the Registry" and "Edit Registry Data" online Help topics
	in Regedt32.exe. Note that you should back up the registry before you edit it.
	
	1. Log on as the user who needs the folder disabled.
	
	2. Go to PROPERTIES of the Recycle Bin and select "Do not move files to the
	  Recycle Bin. Remove files immediately on delete."
	
	  NOTE: All files will be deleted for this user and cannot be recovered.
	
	3. Run regedt32.exe
	
	4. Go to the following registry key:
	
	     HKEY_CURRENT_USER\Software\Microsoft\Windows\Current Version
	     \Explorer
	
	  NOTE: The above registry key is one path; it has been wrapped for readability.
	
	  a. In Shell Folders, set "Recent:REG_SZ:C:\Recycled".
	
	  b. In User Shell Folders, set "Recent:REG_EXPAND_SZ:C:\Recycled".
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : WinNT:4.0
	Hardware          : x86
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
