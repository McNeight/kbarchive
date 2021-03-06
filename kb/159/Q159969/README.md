---
layout: page
title: "Q159969: AutoLogon Fails If DontDisplayLastUserName Is Also Enabled"
permalink: /kb/159/Q159969/
---

## Q159969: AutoLogon Fails If DontDisplayLastUserName Is Also Enabled

{% raw %}

	Article: Q159969
	Product(s): Microsoft Windows NT
	Version(s): winnt:3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): kbenv
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Although you have the AutoLogon feature of Windows NT enabled, when you start
	your Windows NT system you may receive the following error message instead of
	being automatically logged onto the computer:
	
	  Logon Message
	  The system could not log you on. Make sure your User name and domain are
	  correct, then type your password again. Letters in passwords must be typed
	  using the correct case. Make sure that Caps Lock is not accidentally on.
	
	When you click OK, you are prompted for a user name and password that is valid
	for the system.
	
	CAUSE
	=====
	
	Your Windows NT system also has the registry entry DontDisplayLastUserName
	enabled.
	
	RESOLUTION
	==========
	
	To resolve this issue and use the AutoLogon feature, you will need to disable
	DontDisplayLastUserName using the following steps:
	
	WARNING: Using Registry Editor incorrectly may cause serious, system-wide
	problems that may require you to reinstall Windows NT to correct them. Microsoft
	cannot guarantee that any problems resulting from the use of Registry Editor can
	be solved. Use this tool at your own risk.
	
	1. Start Registry Editor (Regedt32.exe) and select the following subkey:
	
	  HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion
	  \Winlogon
	
	2. Select the DontDisplayLastUserName value, and then click String from the Edit
	  menu.
	
	3. Type 0 in the String Editor dialog box, and then click OK.
	
	4. Exit Registry Editor and restart your Windows NT computer.
	
	MORE INFORMATION
	================
	
	The reason for this conflict is that the registry values are mutually exclusive.
	If you enable the DontDisplayLastUserName, you are effectively blanking out the
	user name during authentication. Auditing Logon and Logoff Success and Failure
	Events demonstrates that the user name is not available to the system:
	
	11/11/96 2:41:02 PM  Security Failure Audit  Logon/Logoff   529   NT
	AUTHORITY\SYSTEM  <Servername> Logon Failure:
	     Reason: Unknown user name or bad password
	     User Name:
	     Domain: <Domain>
	     Logon Type: 2
	     Logon Process: User32
	     Authentication Package: MICROSOFT_AUTHENTICATION_PACKAGE_V1_0
	     Workstation Name: <Servername>
	
	NOTE: The User Name field is blank. When the user name is not suppressed in the
	registry, any other circumstance to cause a failed logon attempt always displays
	the user name attempting to logon. This includes gibberish for either a
	DefaultUserName or DefaultPassword. In these cases the user name field is
	occupied.
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  ARTICLE-ID: Q97597
	  TITLE : How to Enable Automatic Logon in Windows NT
	
	Additional query words: prodnt Auto autoadminlogon
	
	======================================================================
	Keywords          : kbenv 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search
	Version           : winnt:3.5,3.51,4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
