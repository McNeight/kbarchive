---
layout: page
title: "Q171874: Link Service Title Cannot be Modified for DFT Link Services"
permalink: /kb/171/Q171874/
---

## Q171874: Link Service Title Cannot be Modified for DFT Link Services

{% raw %}

	Article: Q171874
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0,3.0 SP1
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0, 3.0 SP1, on platform(s):
	   - the operating system: Microsoft Windows NT 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The Link Service title cannot be modified for IBM and DCA DFT Link Services in
	Microsoft SNA Server versions 3.0 and 3.0 Service Pack 1 (SP1).
	
	CAUSE
	=====
	
	The Link Service Title from the dialog is not placed in the Link Service
	Information Structure. It is, therefore, unavailable for modification.
	
	RESOLUTION
	==========
	
	An update to SNA Server 3.0 (post SP1) is available to support this feature.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server 3.0 and 3.0 Service
	Pack 1 (SP1). This problem was corrected in the latest SNA Server version 3.0
	U.S. Service Pack. For information on obtaining this Service Pack, query on the
	following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	Additional query words:
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbAudDeveloper kbSNAServSearch
	Version           : WINDOWS:3.0,3.0 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
