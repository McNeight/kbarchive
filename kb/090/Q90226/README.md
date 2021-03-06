---
layout: page
title: "Q90226: Troubleshooting Lost Network Connections"
permalink: /kb/090/Q90226/
---

## Q90226: Troubleshooting Lost Network Connections

{% raw %}

	Article: Q90226
	Product(s): Microsoft Windows 3.x Retail Product
	Version(s): WINDOWS:
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-SEP-1999
	
	3.10 3.11
	
	WINDOWS
	
	kbnetwork kbtshoot
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows for Workgroups 
	-------------------------------------------------------------------------------
	
	This article provides troubleshooting steps and suggestions that may
	assist you in solving network connectivity problems. Microsoft cannot
	guarantee the success of any specific steps provided in this article.
	
	SUMMARY
	=======
	
	Windows for Workgroups may sometimes lose (drop) network connections. This
	problem is most likely to occur if one of the following conditions exists:
	
	- You are running a network installation (SETUP /N) of Windows for Workgroups.
	
	  NOTE: Microsoft does not recommend running Windows for Workgroups from a
	  network installation (SETUP /N) because doing so is a common stress condition
	  that can cause a loss of network connections. If your system is run this way,
	  store data and applications on a client or server that does NOT contain the
	  shared Windows directory (created with SETUP /A); this appears to reduce the
	  frequency of the problem.
	
	- Several people in a workgroup are running the same application from a
	  server.
	
	  NOTE: Network connections also can be lost when many users run the same
	  application from a server (for example, 10 clients use the same installation
	  of Microsoft FoxPro for MS-DOS). MS-DOS-based applications seem most
	  susceptible to this problem, but Windows-based applications can be affected
	  as well. Windows-based applications generally report segment load failures
	  when the network connection is lost. MS-DOS-based applications that leave a
	  lot of files open, such as database programs, are more susceptible to this
	  problem.
	
	If network connections are lost or dropped, the system or application may stop
	responding(hang), the network installation of Windows for Workgroups may become
	corrupted, and MS-DOS-based applications may produce unexpected results.
	
	WARNING: If you lose your Windows for Workgroups connections, immediately save
	all open data files to backup files on your local drive or a remote drive where
	you still have a valid connection.
	
	MORE INFORMATION
	================
	
	Loss of network connections can occur when you use any version of the
	redirector, but the basic redirector, invoked by using the "NET START BASIC"
	command, is most likely to have this problem. The problem seems to be caused by
	a timing issue in the NetBEUI protocol. It may also be related to the network
	buffer size because it occurs when data is being sent over the wire. In testing,
	this problem didn't occur unless the system was running under the conditions
	listed above; however, the problem may occur when a system is not under any
	stress, but this is very rare.
	
	Other factors that can cause connection problems include the following:
	
	- Network cards: Some network cards are more prone to these problems than
	  others.
	
	- Machine speed: The slower the machine, the more likely that its network
	  connections may be lost.
	
	This problem usually originates with the server but affects clients only.
	
	Attempting to Recover
	---------------------
	
	To determine if you have lost network connections, go to the server and use Net
	Watcher to see if the machine that is not responding still has a valid session
	open. This method does not always work because some applications can reopen the
	network connections. Some applications may not be affected by a lost network
	connection if they are not dependent on file pointers being maintained on the
	server.
	
	Sometimes you can issue the NET USE command at the command prompt to determine
	whether or not a session has been disconnected. This technique works best when
	the machine is not using a network installation (SETUP /N) of Windows. Issuing
	the DIR command may restore the network connection and allow the application to
	continue or at least exit without causing the system to stop responding (hang).
	
	You can also try to close all open files and attempt to quit Windows. If the
	problem results from a network installation of Windows having lost its network
	connections, you will get a message telling you that you do not have enough
	memory to complete the operation.
	
	Avoiding the Problem
	--------------------
	
	The following steps may help prevent this problem:
	
	- Increase FILES= to 128 or higher in the CONFIG.SYS file.
	
	- Increase FCBS= to 25 or higher in the CONFIG.SYS file.
	
	- Increase Sessions= to 20 or higher in the PROTOCOL.INI file.
	
	- Set NCBS= to 40 in the PROTOCOL.INI file.
	
	- Set NetHeapSize= to 52 in the [386Enh] section of the SYSTEM.INI file.
	
	- Set TimerCriticalSection= to 5000 or higher in the [386Enh] section of the
	  SYSTEM.INI file.
	
	- If you are using a network installation of Windows (Setup /N) set
	  maintainserverlist= to NO in the [network] section of the SYSTEM.INI file.
	
	Additional query words: 3.10 3.11 sessions install tshoot
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbWFWSearch
	Version           : WINDOWS:
	
	=============================================================================
	

{% endraw %}
