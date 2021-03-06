---
layout: page
title: "Q185616: XADM: Directory Replication Fails, Event 1124 Error Displayed"
permalink: /kb/185/Q185616/
---

## Q185616: XADM: Directory Replication Fails, Event 1124 Error Displayed

{% raw %}

	Article: Q185616
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it if
	a problem occurs. For information about how to do this, view the "Restoring
	the Registry" Help topic in Regedit.exe or the "Restoring a Registry Key"
	Help topic in Regedt32.exe.
	
	SYMPTOMS
	========
	
	You may experience either of the following symptoms:
	
	- When you attempt to perform directory replication between two Microsoft
	  Exchange Server computers, directory replication may fail.
	
	- If you attempt to check the knowledge consistency of an Exchange Server
	  computer by clicking Check Now in the properties for the directory service,
	  the following message is displayed:
	
	  An internal error has occurred during directory replication. Stop
	  and then restart the directory service. Then try directory
	  replication again. ID no: c1030b0d
	
	  In addition, the following event may appear in the event log:
	
	     Event: 1124
	     Source: MSExchangeDS
	     Severity: Error
	     Category: Knowledge Consistency Checker
	     Description: The consistency checker encountered an internal error
	     and can't continue checking the consistency of this directory. Stop
	     and restart this Microsoft Exchange computer.
	   
	
	
	CAUSE
	=====
	
	This problem can occur if the Site value under the following registry key
	contains an incorrect site name:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\MSExchangeSA
	  \Parameters
	
	NOTE: The above registry key is one path; it has been wrapped for readability.
	
	WORKAROUND
	==========
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall your operating system. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editor can be solved. Use
	Registry Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" Help topic in Registry Editor (Regedit.exe) or the "Add and Delete
	Information in the Registry" and "Edit Registry Data" Help topics in
	Regedt32.exe. Note that you should back up the registry before you edit it.
	
	To work around this problem, follow these steps:
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate the Site value under the following key in the registry:
	
	     HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\MSExchangeSA
	     \Parameters
	 
	
	  NOTE: The above registry key is one path; it has been wrapped for readability.
	
	3. Click String on the Edit menu, type the correct site name in the String box,
	  and then click OK.
	
	4. Quit Registry Editor.
	
	5. Stop and restart the Microsoft Exchange System Attendant service. To do so,
	  follow these steps:
	
	  a. In Control Panel, double-click Services.
	
	  b. Click the Microsoft Exchange System Attendant service, and then click
	     Stop. If a dialog box appears stating that additional services will be
	     stopped, note the services that will be stopped, and then click OK. All
	     other Exchange Server services are stopped when you stop the system
	     attendant.
	
	  c. Click the Microsoft Exchange System Attendant service, and then click
	     Start.
	
	  d. Start any additional services that were stopped in step B.
	
	MORE INFORMATION
	================
	
	For information about the steps that are performed when you check the knowledge
	consistency of an Exchange Server computer, please see the following article in
	the Microsoft Knowledge Base:
	
	  Q174758 XADM: Steps Performed During Knowledge Consistency Check
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange500 kbZNotKeyword2
	Version           : WINDOWS:5.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
