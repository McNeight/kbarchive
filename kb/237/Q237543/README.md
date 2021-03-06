---
layout: page
title: "Q237543: SMS: Service Pack Upgrade Considerations for Clients"
permalink: /kb/237/Q237543/
---

## Q237543: SMS: Service Pack Upgrade Considerations for Clients

{% raw %}

	Article: Q237543
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0
	Operating System(s): 
	Keyword(s): kbsms200
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When a Systems Management Server (SMS) 2.0 site is upgraded to a service pack,
	all clients reporting to the site are automatically upgraded. In a site with a
	significant number of clients, you may need to consider your network bandwidth
	when you are creating your upgrade strategy.
	
	MORE INFORMATION
	================
	
	A service pack upgrade of the site server also automatically upgrades all the
	Client Access Point (CAP) servers and Logon Point servers. Depending on the
	combination of optional components installed, the client upgrade copies anywhere
	from 8 MB to 24 MB at the time of upgrade. Client upgrades are automatic, but
	the upgrade method depends on several factors:
	
	- A Windows NT client on the network that is not usually logged out runs a
	  Client Configuration Installation Manager (CCIM32) maintenance cycle every 23
	  hours. During this maintenance cycle, CCIM32 contacts the CAP server, finds
	  the upgraded files, and performs an automatic upgrade of the client.
	
	- A Microsoft Windows 95 or Microsoft Windows 98 client that remains logged on
	  the network overnight with a user logged on, runs the same CCIM32 23-hour
	  maintenance cycle and automatically upgrades.
	
	- All other clients run upgrades when they log on and run the SMS logon script
	  (SMSLS) from the SMS Logon Points.
	
	To avoid having all clients logging on and running upgrades at the same time,
	consider the following points when you are creating your upgrade plan.
	Individual plans depend on the site, network bandwidth availability, and other
	factors specific to the environment. Before upgrading, consider the following
	options:
	
	- Disable logon scripts and let CCIM32 run its course on the clients every 23
	  hours. This should spread some of the load because different clients might
	  upgrade at different times.
	
	  This works for client computers that are up and running on the network all the
	  time. A quick way to disable the execution of SMS logon script during network
	  logon is to add a line such as "GOTO END" (without the quotation marks) at
	  the top of the SMSLS logon script.
	
	- Turn on logon scripts for a few users at a time. This ensures controlled
	  client upgrades to the SMS service pack.
	
	- Apply the service pack to the site on a Friday or over the weekend and
	  instruct users to leave their computers on over the weekend. With less
	  network traffic on weekends, there should be more network bandwidth available
	  for the upgrade of the clients.
	
	
	Notes
	-----
	
	- If you have client computers connecting to the network using RAS, you should
	  probably turn off SMS logon scripts for them. If you do not, they will
	  attempt to upgrade over the RAS link. You should schedule upgrades for these
	  computers when they are brought into the office and are on the network.
	
	- Windows 95/98 does not have the ability to replace in-use files and requires
	  one or more reboots to upgrade. For best results, do not reboot the client
	  until 15 minutes or more after the initial upgrade.
	
	- Active Advertised programs should be expired before the service pack is
	  applied and reactivated after the clients are upgraded. This ensures the best
	  results with software distribution.
	
	REFERENCES
	==========
	
	For additional information about SMS 2.0 service packs, please click the article
	numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q236325 How to Obtain the Latest Systems Management Server Service Pack
	
	
	  Q236596 SMS: Client Components Fail to Install with SMS 2.0 SP1
	
	
	Additional query words: prodsms sp1 upgrade servpack sms20 kbhowto smsfaqtop
	
	======================================================================
	Keywords          : kbsms200 
	Technology        : kbSMSSearch kbSMS200
	Version           : winnt:2.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
