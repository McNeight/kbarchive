---
layout: page
title: "Q180619: SNA Server Stops After Logging Event 684 and 685."
permalink: /kb/180/Q180619/
---

## Q180619: SNA Server Stops After Logging Event 684 and 685.

{% raw %}

	Article: Q180619
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0,3.0 SP1,3.0 SP2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 02-APR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0, 3.0 SP1, 3.0 SP2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The SNA Server service may stop unexpectedly and log the following Event ID in
	the Windows NT Event Viewer Application log:
	
	  Event ID: 685
	  Source: SNA Server
	  Description: An attempt was made to extend a buffer pool, but
	  the related pool had reached its maximum size. The affected component is
	  terminating, and an audit of the buffer pools just before termination is
	  attached
	
	  <the data will indicate a large number of trusted headers owned by the
	  SNASERVR process >
	
	This event will be preceded by numerous Event 684 messages, which indicate that
	the SNA Server's trusted header use is growing by about 150 per minute until the
	maximum trusted header pool is reached (of 100,000). When this occurs, SNA
	Server stops.
	
	This problem coincides with the use of an APPC application that uses the DISPLAY
	API function to retrieve all LU6.2 configuration and state information.
	
	CAUSE
	=====
	
	When receiving an APPC DISPLAY request from an APPC application to retrieve
	LU6.2 information, SNA Server occasionally allocates an extra trusted header it
	doesn't actually use and then fails to free it.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server versions 3.0, 3.0 SP1
	and 3.0 SP2. This problem is fixed in SNA 4.0.
	
	This problem was corrected in the latest SNA Server version 3.0 U.S. Service
	Pack. For information on obtaining this Service Pack, query on the following
	word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ300SP1 kbSNAServ300SP2
	Version           : WINDOWS:3.0,3.0 SP1,3.0 SP2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
