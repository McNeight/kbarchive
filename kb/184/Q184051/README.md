---
layout: page
title: "Q184051: XFOR: Queued Message Waiting for ETRN Never Expires"
permalink: /kb/184/Q184051/
---

## Q184051: XFOR: Queued Message Waiting for ETRN Never Expires

{% raw %}

	Article: Q184051
	Product(s): Microsoft Exchange
	Version(s): 5.0,5.5
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 04-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	Normally, when a message sent from a client is undelivered after the scheduled
	time (message time-out value), the Microsoft Exchange Internet Mail Service
	expires the message on the Internet Mail Service outbound queue and returns a
	non-delivery report (NDR) to the sender. However, when this problem occurs, the
	queued message, which is waiting for the ETRN command, remains in the outgoing
	queue and never expires after the scheduled time. The sender never receives an
	NDR.
	
	CAUSE
	=====
	
	Microsoft Exchange Server supports the use of an SMTP extension called ETRN. An
	Exchange Server computer can be used as a host SMTP server and will respond to
	ETRN commands from the remote host. After the remote host submits the ETRN
	command to the Exchange Server computer, a new connection is established from
	the Exchange Server computer to the remote host. The Exchange Server computer
	keeps a message until it receives the ETRN command from the remote host. If the
	queued message is waiting for the ETRN command, the message never expires even
	after the scheduled time. Then the sender never receives an NDR. The scheduled
	time is 48 hours for Normal Message by default.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.0.
	
	
	A supported fix is now available, but has not been fully regression-tested and
	should be applied only to systems experiencing this specific problem. Unless you
	are severely impacted by this specific problem, Microsoft recommends that you
	wait for the next Service Pack that contains this fix. Contact Microsoft
	Technical Support for more information. This fix has been posted to the
	following Internet location:
	
	  ftp://ftp.microsoft.com/bussys/exchange/exchange-public/fixes/Eng/Exchg5.0/Post-SP2-IMS/
	
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server version
	5.5. This problem has been corrected in the latest U.S. Service Pack for
	Microsoft Exchange Server version 5.5. For information about obtaining the
	Service Pack, query on the following word in the Microsoft Knowledge Base
	(without the spaces):
	
	  S E R V P A C K
	
	
	
	Additional query words: ISP RFC1985 SBS dialup DNS
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbZNotKeyword2
	Version           : :5.0,5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
