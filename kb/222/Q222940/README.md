---
layout: page
title: "Q222940: SNA 5250 Print Service (PPV5250) May Log Event 4097 In Error"
permalink: /kb/222/Q222940/
---

## Q222940: SNA 5250 Print Service (PPV5250) May Log Event 4097 In Error

{% raw %}

	Article: Q222940
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:4.0,4.0SP1,4.0SP2
	Operating System(s): 
	Keyword(s): kbsna400sp3fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 4.0, 4.0SP1, 4.0SP2 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When using the SNA Print Server to support print emulation to an AS/400 or S/36,
	Event 4097 may be logged even when no error has actually occurred. For example:
	
	  Event ID: 4097
	  Source: PPV5250
	  Type: Error
	  Description:
	  Receive and Wait verb has completed with primary return code Dealloc Normal.
	
	This event was logged when testing the SNA Print Server against an IBM S/36, when
	the S/36 print writer for the print device was not started.
	
	CAUSE
	=====
	
	The SNA Print Service logs this error whenever one of its APPC function calls
	completes when AP_OK is not the primary return code. However, in some cases, an
	APPC primary return code of AP_DEALLOC_NORMAL (0x0009) may not indicate an
	actual error condition.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for SNA Server version
	4.0. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q215838 How to Obtain the Latest SNA Server Version 4.0 Service Pack
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server 4.0, 4.0 SP1 and 4.0
	SP2. This problem was first corrected in SNA Server version 4.0 Service Pack 3.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsna400sp3fix 
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ400
	Version           : WINDOWS:4.0,4.0SP1,4.0SP2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
