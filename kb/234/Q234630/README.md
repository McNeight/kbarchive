---
layout: page
title: "Q234630: XADM: Event Scripts Fail after Installing Exchange 5.5 SP2"
permalink: /kb/234/Q234630/
---

## Q234630: XADM: Event Scripts Fail after Installing Exchange 5.5 SP2

{% raw %}

	Article: Q234630
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5 SP2
	Operating System(s): 
	Keyword(s): exc55sp2 EXC55SP3Fix
	Last Modified: 01-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 SP2 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	After you install Exchange Server 5.5 Service Pack 2 (SP2), applications that
	use Cdo.dll may start receiving an error of 0x800401F0 (CO_E_NOTINITIALIZED)
	indicating that CoInitialize() has not been called. The most common environment
	where this may be seen is with event scripts that run using the Microsoft Event
	Service. This problem will typically be seen with event scripts that log on to a
	new MAPI session from within the script.
	
	The application event log may show events that look similar to the following:
	
	  Event ID: 6
	  Source: MSExchangeES
	  Description: An unexpected MAPI error occurred while processing binding
	  "Script Name". Error returned was [0x800401f0].
	
	  Event ID: 16
	  Source: MSExchangeES
	  Description: Unexpected error 0x800401f0 occurred during processing of
	  timer-based events.
	
	CAUSE
	=====
	
	Changes were made in Exchange Server 5.5 SP2 to allow Cdo.dll to properly
	support the Component Object Model (COM) Multi-Threaded Apartment (MTA) model.
	The Microsoft Event Service exposed a problem with these changes.
	
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Exchange Server
	version 5.5. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: MAPI
	
	+-------------------------+
	| File name  | Version    | 
	+-------------------------+
	| Mapi32.dll | 5.5.2622.0 | 
	+-------------------------+
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5 Service Pack 2. This problem was first corrected in Exchange Server
	5.5 Service Pack 3.
	
	Additional query words: script failure event cdo mapi unitialized
	
	======================================================================
	Keywords          : exc55sp2 EXC55SP3Fix 
	Technology        : kbExchangeSearch kbZNotKeyword2 kbExchange550SP2
	Version           : winnt:5.5 SP2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
