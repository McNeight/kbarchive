---
layout: page
title: "Q255184: NT 4.0 Option Pack Installation Errors on MSCS Running MSDTC"
permalink: /kb/255/Q255184/
---

## Q255184: NT 4.0 Option Pack Installation Errors on MSCS Running MSDTC

{% raw %}

	Article: Q255184
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	- Microsoft Cluster Server 
	- Microsoft Internet Information Server version 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	When you install the Microsoft Windows NT 4.0 Option Pack on a Microsoft Cluster
	Server-based computer running Microsoft Distributed Transaction Coordinator
	(MSDTC), MSDTC may cause errors during installation or may not start after the
	option pack installation.
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To resolve this behavior, follow these steps:
	
	1. Remove the MSDTC resource group from the cluster.
	
	2. On the computer that is running MSDTC, delete the following registry keys:
	
	HKEY_LOCAL_MACHINE\Software\Microsoft\MSDTC
	
	HKEY_LOCAL_MACHINE\CurrentControlSet\Services\MSDTC
	
	3. Remove the shared MSDTCLog folder on the shared drive.
	
	4. Perform a stand-alone installation of MSDTC.
	
	  NOTE: If Windows NT Service Pack 5 is installed on the Cluster Server-based
	  computer, contact Microsoft Technical Support to obtain the Dtcsetup.exe
	  setup program and to request the hotfix appropriate for your environment. The
	  hotfix creates an MSDTCLog folder on the shared drive and adds the MSDTC
	  resource group in Cluster Administrator.
	
	5. Stop and restart the cluster services on both nodes.
	
	MORE INFORMATION
	================
	
	When you install multiple Microsoft server applications in a cluster
	environment, you must install them in a prescribed order. Failure to follow the
	prescribed order may cause the applications not to be installed correctly.
	
	For additional information installing applications in a cluster environment,
	click the article numbers below to view the articles in the Microsoft Knowledge
	Base:
	
	  Q241573 How to Install IIS 4.0 onto a Single Node of MSCS 1.0
	
	  Q192708 Installation Order: Cluster Server Support for SQL or MSMQ
	
	  Q219264 Order of Installation for SQL Server 7.0 Clustering Setup
	
	  Q191138 How to Install the Windows NT Option Pack on Microsoft Cluster Server
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbiisSearch kbAudDeveloper kbClustServSearch kbiis400
	Version           : winnt:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
