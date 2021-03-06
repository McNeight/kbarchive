---
layout: page
title: "Q105154: How AppleTalk Routers Function in Internet Communications"
permalink: /kb/105/Q105154/
---

## Q105154: How AppleTalk Routers Function in Internet Communications

{% raw %}

	Article: Q105154
	Product(s): Microsoft LAN Manager
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 27-FEB-2002
	
	SUMMARY
	=======
	
	LocalTalk networks are different from PC networks and require you to consider
	special concepts and issues when setting them up. Most LocalTalk networks are
	internets--separate physical networks connected by routers that enable network
	communications by maintaining a map of the physical network on the internet and
	forwarding data to the correct network destinations.
	
	Seed routers provide other specialized internet functions. For more information
	on them see Q105155.
	
	ROUTING TABLE MAINTENANCE PROTOCOL (RTMP)
	-----------------------------------------
	
	AppleTalk uses routing table maintenance protocol (RTMP) to maintain information
	about internetworking addresses and connections. Routers provide interfaces for
	RTMP and numerous other protocols and processes.
	
	The routing table contains all possible destination network numbers (or the
	network range) and five entries necessary for forwarding datagrams:
	
	- the number of the data link port that connects to the local network's DDP
	
	- the destination network number
	
	- the next router's node ID
	
	- the number of hops needed to reach the destination network
	
	- a cross-reference into the zone information table
	
	The routers use RTMP to exchange this routing information, keeping their tables
	current and minimizing internetwork delays.
	
	ZONE INFORMATION PROTOCOL (ZIP)
	-------------------------------
	
	The zone information protocol (ZIP) maintains a zone information table that the
	name binding protocol (NBP) uses to match networks with their zones. ZIP also
	helps routers maintain their tables.
	
	EXAMPLE
	-------
	
	If you send a job across a router to a printer. A sniff of the request will show
	you the process stages:
	
	- When the printing process begins, you will see RTMP and ZIP packets. These
	  update the routers.
	
	- Then, an NBP request to find the printer, something resembling:
	
	         NBP Request ID=XX (=:LaserWriter@zonename)
	
	- After the logical connection is initiated, the printer access protocol (PAP)
	  starts a connection.
	
	- When this connection is confirmed, data transmission starts.
	
	The process for a file request is very similar, although it uses the file access
	protocol (FAP) instead of the printer access protocol (PAP). If you are looking
	for network or broadcast problems, use the ZIP and RTMP packets to verify that
	the information (number of hops and network ranges) is correct.
	
	Additional query words: 1.0a macfile localtalk osi
	
	======================================================================
	Keywords          :  
	
	=============================================================================
	

{% endraw %}
