---
layout: page
title: "Q100039: Mac Wkst: Reading Resources from Server"
permalink: /kb/100/Q100039/
---

## Q100039: Mac Wkst: Reading Resources from Server

{% raw %}

	Article: Q100039
	Product(s): Microsoft Mail For Appletalk Networks
	Version(s): WINDOWS:3.1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for AppleTalk Networks, version 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	With version 3.1 of Microsoft Mail for AppleTalk networks, the workstation
	software may display the following status dialog box during login:
	
	  Reading Resources from Server
	
	While this message is displayed, the workstation downloads into the MS Mail Cache
	file all resources necessary to work offline. These resources include:
	
	- The All list
	
	- All message forms
	
	- All one-off addressing screens
	
	- Contents of the Personal Address Book
	
	- Personal Group definitions
	
	The offline preference is enabled by default. If you do not need offline
	operation, you can prevent the information from being downloaded by disabling
	the offline preference. You can do this while you are logged into the user
	account.
	
	To ensure the offline information is kept up to date, the workstation downloads
	the information from the server. The frequency of the download depends on the
	preference setting for the workstation. The default is seven days.
	
	MORE INFORMATION
	================
	
	You may encounter the Reading Resources message more frequently than the
	specified download time in the Preferences section. The workstation keeps a
	version number of the Personal Address Book (PAB). This version number matches
	the information stored on the local workstation with the information stored on
	the server to ensure synchronization.
	
	Updates of the PAB are not controlled by the Preferences setting. If the user
	allows all message recipients to be added to the PAB, this may cause frequent
	updates to the PAB. The next time the user logs into the server, the PAB version
	numbers will be compared and if they are different, the address book is
	downloaded. To minimize the download of resources, you should not automatically
	add users to the address book.
	
	A corrupt MS Mail Cache may also repeatedly download the resources from the
	server. You can create a new cache by removing the cache file and restarting the
	computer. The next time the user signs in to the mail server, the resources will
	be fully read one time. After they are fully read, download will only occur
	based on the download preference or when the PAB has been updated.
	
	Additional query words: 3.10
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailATN310
	Version           : WINDOWS:3.1
	
	=============================================================================
	

{% endraw %}
