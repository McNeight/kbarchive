---
layout: page
title: "Q146920: XADM: Restoring Individual Mailboxes, Messages, or Folders"
permalink: /kb/146/Q146920/
---

## Q146920: XADM: Restoring Individual Mailboxes, Messages, or Folders

{% raw %}

	Article: Q146920
	Product(s): Microsoft Exchange
	Version(s): 4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): kbusage exc4 exc5 exc55
	Last Modified: 01-MAR-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The backup program in Microsoft Exchange Server version 4.0 does not have the
	capability to back up and restore individual mailboxes. This article describes
	how you can work around this limitation and recover deleted items from backup.
	
	Microsoft Exchange Administrators need to be able to recover an individual item
	from backup. For example, there may be a need to restore a deleted users mail,
	or to recover a deleted mail message or a deleted folder. In each of these
	cases, the only option is to recover the deleted item from a backup.
	
	MORE INFORMATION
	================
	
	To recover an individual item (mailbox, folder, or message) from a backed up
	Microsoft Exchange Information Store, follow these steps:
	
	IMPORTANT: Read all of the steps before you start.
	
	1. Install Microsoft Exchange Server on another computer, and select "Create a
	  New Site".
	
	The same computer name is not required, but must have the same organization and
	site name as the tape being restored.
	
	2. Using Windows NT Backup, restore the information store and type the alternate
	  server name for the destination server in the Restore Information dialog box.
	
	3. In the Administrator program, in the Advanced Properties of the Server
	  Object, click the Consistency Adjuster button. Under "the Private Information
	  Store" section of the Operations group box, click "Synchronize with the
	  directory, and create new directory entries for mailboxes that do not have a
	  corresponding directory entry". Under the Filter group box, click All
	  Inconsistencies, and then click OK.
	
	  NOTE: You must click OK again to acknowledge the warning dialog box and
	  proceed.
	
	4. Give yourself permission for the mailbox you want to restore from or for any
	  mailbox if you are restoring a public folder.
	
	5. Log on to the server with a Microsoft Exchange Client.
	
	6. To add the Personal Folders service, click Tools, click Services, click Add,
	  click Personal Folder, and then drag and drop the Public older data to the
	  .pst file.
	
	7. Log on to an online server with a profile that also points to the .pst file
	  used in the previous step.
	
	8. Move the messages from the .pst file onto the online server.
	
	Although this method works with Microsoft Outlook, after you use the method,
	journal entries are no longer linked to the contact items with which they were
	created.
	
	To retain the links between journal and contact entries, restore the entire
	information store intact. For additional information, click the article number
	below to view the article in the Microsoft Knowledge Base:
	
	  Q169824 OL97: Contact's Journal Entries Lost When Importing or Exporting
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbusage exc4 exc5 exc55 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : :4.0,5.0,5.5
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
