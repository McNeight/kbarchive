---
layout: page
title: "Q295058: SMS: Memory Leak During SMS_Advertisement Instance Enumeration"
permalink: /kb/295/Q295058/
---

## Q295058: SMS: Memory Leak During SMS_Advertisement Instance Enumeration

{% raw %}

	Article: Q295058
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0,2.0 SP1,2.0 SP2,2.0 SP3
	Operating System(s): 
	Keyword(s): kbsms200 kbsms200bug kbsms200preSP4fix
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1, 2.0 SP2, 2.0 SP3 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When it is enumerating instances of the SMS_Advertisement Windows Management
	Instrumentation (WMI) class, the SMS provider can cause a leak in private bytes
	of the Winmgmt service.
	
	CAUSE
	=====
	
	This leak can occur when mandatory assignments are used in the advertisement's
	schedule. If advertisements contain one or more mandatory assignments, a leak in
	Winmgmt private bytes occurs when the Advertisements node is refreshed in the
	SMS Administration console.
	
	Additionally, custom programs that use the Microsoft Systems Management Server
	(SMS) Software Development Kit (SDK) to enumerate or poll the SMS_Advertisement
	WMI class can cause this leak to occur.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Systems Management
	Server version 2.0. For additional information, click the following article
	number to view the article in the Microsoft Knowledge Base:
	
	  Q288239 SMS: How to Obtain the Latest Systems Management Server 2.0 Service
	  Pack
	
	
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article. This problem was first corrected in
	Systems Management Server 2.0 Service Pack 4.
	
	MORE INFORMATION
	================
	
	Although the leak is small (about 36 bytes per advertisement that contains a
	single mandatory assignment schedule), the leak can be increased by the heavy
	use of mandatory assignments and many advertisements.
	
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsms200 kbsms200bug kbsms200preSP4fix 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1 kbSMS200SP2 kbSMS200SP3
	Version           : :2.0,2.0 SP1,2.0 SP2,2.0 SP3
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
