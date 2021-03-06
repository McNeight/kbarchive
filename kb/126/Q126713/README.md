---
layout: page
title: "Q126713: Resetting Default Access Controls on Selected Registry Keys"
permalink: /kb/126/Q126713/
---

## Q126713: Resetting Default Access Controls on Selected Registry Keys

{% raw %}

	Article: Q126713
	Product(s): Microsoft Windows NT
	Version(s): WinNT:3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): kbenv
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it if
	a problem occurs. For information about how to do this, view the "Restoring
	the Registry" Help topic in Regedit.exe or the "Restoring a Registry Key"
	Help topic in Regedt32.exe.
	
	SYMPTOMS
	========
	
	A user with a valid user name and domain name, who also has the right to log on
	locally to a Windows NT computer, can have the system run a program on the local
	computer in a heightened security context.
	
	NOTE: The Guest account does not have access to modify the registry. By default,
	Windows NT domain controllers only permit administrators to log on and therefore
	are not vulnerable.
	
	CAUSE
	=====
	
	When a properly authenticated user logs on locally to a Windows NT computer,
	that user becomes a member of the "Everyone" group. The default permission on
	the keys cited below allow members of the "Everyone" group special access, which
	includes the right to Set Values or Create Subkeys. This allows members of the
	"Everyone" group to create an entry under the Run and RunOnce keys that contains
	the name of a program to run when the computer starts. The Uninstall key defines
	the programs to run when you remove an application.
	
	  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run
	  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce
	  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
	
	Because there is a potential for the abuse of this level of rights, some
	organizations may want to reset the permissions, as described below in the
	Resolution section. A user must be logged on locally in order to change these
	keys. They can be changed remotely by properly authenticated and privileged
	administrators.
	
	RESOLUTION
	==========
	
	Resetting the permissions for these three registry subkeys to READ resolves this
	issue.
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall your operating system. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editor can be solved. Use
	Registry Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" Help topic in Registry Editor (Regedit.exe) or the "Add and Delete
	Information in the Registry" and "Edit Registry Data" Help topics in
	Regedt32.exe. Note that you should back up the registry before you edit it.
	
	Perform the following steps to reset the permissions:
	
	1. Run Registry Editor (Regedt32.exe).
	
	2. Perform the following steps on each of the registry keys identified above:
	
	  a. On the Security menu, click Permissions.
	
	  b. Click "Replace Permissions on Existing Subkeys" so that it is selected.
	
	  c. Click Everyone, change the Type Of Access to Read, and then click OK.
	
	3. Exit Registry Editor.
	
	Additional query words: 4.0
	======================================================================
	Keywords          : kbenv 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search
	Version           : WinNT:3.5,3.51,4.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
