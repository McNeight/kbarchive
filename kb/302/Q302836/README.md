---
layout: page
title: "Q302836: SMS: Cannot Increase APM Polling Interval to More Than 1,440"
permalink: /kb/302/Q302836/
---

## Q302836: SMS: Cannot Increase APM Polling Interval to More Than 1,440

{% raw %}

	Article: Q302836
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbtool kbsms200 kbsms200bug kbsms200preSP4fix
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you configure the Advertised Programs Client Agent polling interval for new
	programs in the Systems Management Server (SMS) Administrator Console, you
	cannot set a value above 1,440 minutes (1 day). If you try to do so, you receive
	the following error message:
	
	  Please enter an integer between 5 and 1440.
	
	This limitation also applies to the Advertised Programs Monitor on SMS clients.
	You receive the following error message if you enter a value that is outside of
	the range:
	
	  The refresh interval must be between 5 and 1440 minutes.
	
	You can configure the polling interval both on a per-client basis and on a
	site-wide basis. On the client, you can use the Options command on the System
	menu in the Advertised Programs Monitor tool in Control Panel to adjust this
	setting.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Systems Management
	Server version 2.0. For additional information, click the following article
	number to view the article in the Microsoft Knowledge Base:
	
	  Q236325 How to Obtain the Latest Systems Management Server 2.0 Service Pack
	
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article. This problem was first corrected in
	Systems Management Server 2.0 Service Pack 4.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbenv kberrmsg kbtool kbsms200 kbsms200bug kbsms200preSP4fix 
	Technology        : kbSMSSearch kbSMS200
	Version           : :2.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
