---
layout: page
title: "Q158862: Microsoft Mail PostOffice Icon Is Missing in Control Panel"
permalink: /kb/158/Q158862/
---

## Q158862: Microsoft Mail PostOffice Icon Is Missing in Control Panel

{% raw %}

	Article: Q158862
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): kbsetup
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Microsoft Mail PostOffice icon in Control Panel is missing. The icon may not
	appear even after removing and adding Windows Messaging through Windows NT
	Setup.
	
	CAUSE
	=====
	
	This behavior occurs because the Microsoft Mail component has not been
	installed. This behavior can also occur after having Microsoft Outlook profiles
	installed on the system that did not use the Microsoft Mail postoffice.
	
	RESOLUTION
	==========
	
	To resolve this problem, install the Microsoft Mail component.
	
	When you install the Microsoft Mail component, Setup also installs the Microsoft
	Mail PostOffice Control Panel extension file, Wgpocpl.cpl, into the
	<systemroot>\System32 directory.
	
	1. Click the Start button, point to Settings, and then click Control Panel.
	
	2. Double-click Add/Remove Programs.
	
	3. Click the Windows NT Setup tab.
	
	4. Select Windows Messaging from the Components list, and then click Details.
	
	5. Select the Microsoft Mail check box, and then click OK.
	
	6. Click OK on the Windows NT Setup properties page, and follow the on-screen
	  directions for installing the Microsoft Mail component.
	
	NOTE: If you do not close and reopen Control Panel after you have installed the
	Microsoft Mail component, you may need to click Refresh on the View menu of
	Control Panel to see the addition of the Microsoft Mail postoffice icon.
	
	To add the Postoffice icon when Outlook profiles are installed that do not use
	the Microsoft Mail postoffice:
	
	1. Back up any mail folders currently in use.
	
	2. Remove any components of Windows Messaging in Windows NT Setup.
	
	3. Start Registry Editor (Regedt32.exe).
	
	4. Go to the following location in the registry:
	
	  HKEY_CURRENT_USER\Software\Microsoft\WindowsNT\CurrentVersion\Windows
	  Messaging Subsystem
	  NOTE: The registry key above is all one path; it has been wrapped for
	  readability.
	
	5. On the Registry menu, click Save Key.
	
	6. Delete any profiles found under the following registry key:
	
	  HKEY_CURRENT_USER\Software\Microsoft\WindowsNT\CurrentVersion\Windows
	  Messaging Subsystem\Profiles\MS Exchange Settings NOTE: The registry key
	  above is all one path; it has been wrapped for readability.
	
	7. Restart your computer, and then add the Windows Messaging components through
	  Windows NT Setup again.
	
	8. Close, and then open Control Panel to refresh the icons.
	
	Additional query words: exchange WGPO Admin Workgroup prodnt
	
	======================================================================
	Keywords          : kbsetup 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : WinNT:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
