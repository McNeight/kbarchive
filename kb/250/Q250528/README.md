---
layout: page
title: "Q250528: Using Account Joiner Utility in Microsoft Metadirectory Services"
permalink: /kb/250/Q250528/
---

## Q250528: Using Account Joiner Utility in Microsoft Metadirectory Services

{% raw %}

	Article: Q250528
	Product(s): Microsoft Windows NT
	Version(s): 2.1
	Operating System(s): 
	Keyword(s): kbinterop kbtool
	Last Modified: 27-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Metadirectory Services, version 2.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article provides information about using the Account Joiner utility.
	
	MORE INFORMATION
	================
	
	Account Joiner is a Lightweight Directory Access Protocol (LDAP) client you can
	use to help manage and control the join process. Account Joiner is used to
	process those connector space entries that could not be joined through the
	standard join rules of the Management Agent (MA). Account Joiner enables you
	to:
	
	- View all the MAs on your server and any disconnected entries in each MA.
	
	- Build ad-hoc queries to propose joins to the metaverse.
	
	- Manually join problem entries that will not join using the inclusion rules
	  specified.
	
	- Disconnect accounts that have been joined in error.
	
	NOTE: Account Joiner is installed automatically when you install Microsoft VIA
	Compass. Also, you are prompted to log on with the Zoomit Metadirectory Login
	prompt before loading Account Joiner.
	
	Normally you would use Account Joiner after an automated join operation by the
	Management Agent was complete, and there are some entries that remain
	disconnected.
	
	The Account Joiner utility permits you to select entries under a particular MA
	and join them to the metaverse object. However, if there are several entries
	listed in the metadirectory results, and you find there is a 1 to 1 mapping
	between the connector space and metadirectory results using the full name query,
	you should modify your join criteria to reduce the number of results requiring
	specific attention.
	
	The following examples are based on the default values associated with a
	predefined MA. Each MA will be unique and can be customized through the Account
	Joiner utility. For additional information about using Account Joiner, click the
	article number below to view the article in the Microsoft Knowledge Base:
	
	  Q251297 How to customize the Account Joiner Utility for a Particular MA
	
	Using Account Joiner to Join Disconnected Objects on a Windows NT 4.0 Domain MA
	-------------------------------------------------------------------------------
	
	1. Log on to the Microsoft Metadirectory Services (MMS) server using Compass.
	
	2. Click Start, point to Programs, and then click Zoomit Directory Service V2.
	
	3. Click Account Joiner, and then click the appropriate MA tab.
	
	4. Click the appropriate entry, and then click Full Name.
	
	5. Under Metadirectory Results, click Join.
	
	NOTE: When you join a connector space object to the metaverse, the object icon
	changes from green to red. A red icon indicates the connector space object is
	assigned to the metaverse, and there is no need to join this object. A green
	icon indicates you need to do something with this metaverse object.
	
	Disconnect an Account that Has Been Joined in Error
	---------------------------------------------------
	
	1. Log on to Compass
	
	2. Click Start, point to Programs, and then click Zoomit Directory Service V2.
	
	3. Click Account Joiner, and then click the appropriate MA tab.
	
	4. In the Search Content box, click First And Last, and then type the name of
	  the user that you would like to disconnect.
	
	5. Click Search.
	
	6. Right-click the user name, click Connectors, click the appropriate entry in
	  the Connected Objects box, and then click Disconnect.
	
	7. Click Close.
	
	For additional information about joining accounts, click the article numbers
	below to view the articles in the Microsoft Knowledge Base:
	
	  Q250584 Understanding a Join in Microsoft Metadirectory Services
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbinterop kbtool 
	Technology        : kbMMSSearch kbMMS210
	Version           : :2.1
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
