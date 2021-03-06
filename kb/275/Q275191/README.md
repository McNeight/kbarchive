---
layout: page
title: "Q275191: SMS: Corrupted Raw File Is Created After Hardware Inventory"
permalink: /kb/275/Q275191/
---

## Q275191: SMS: Corrupted Raw File Is Created After Hardware Inventory

{% raw %}

	Article: Q275191
	Product(s): Microsoft Systems Management Server
	Version(s): 1.2
	Operating System(s): 
	Keyword(s): kbinterop kbConfig kbsms120 kbsms120bug kbInventory
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you run a hardware inventory, a corrupted RAW file may be created. If the
	hardware inventory is performed on a client that is not already in the database,
	a .mif file cannot be produced by the Systems Management Server (SMS) Inventory
	Processor, and the client is not added to the database.
	
	When the server attempts to process a RAW file from a client, the Invproc.log
	file that is created by the SMS Inventory Processor may report the following
	error messages:
	
	  Reading the RAW file $$<SMS_INVENTORY_PROCESSOR>
	  It's for machine HF1004R1 $$<SMS_INVENTORY_PROCESSOR>
	  Processing Machine ISV MIF Files... $<SMS_INVENTORY_PROCESSOR>
	  Converting RAW data to MIF $$<SMS_INVENTORY_PROCESSOR>
	  >>>Inside of IndexValid(), pNetwork->dwNumNetCard = 2
	  $$<SMS_INVENTORY_PROCESSOR>
	  >>>Inside of IndexValid(), pNetwork->dwNumNetCard = 2
	  $$<SMS_INVENTORY_PROCESSOR>
	  >>>Inside of IndexValid(), pNetwork->dwNumNetCard = 2
	  $$<SMS_INVENTORY_PROCESSOR>
	  >>>Inside of IndexValid(), pNetwork->dwNumNetCard = 2
	  $$<SMS_INVENTORY_PROCESSOR>
	  Appending no ID group PC BIOS $$<SMS_INVENTORY_PROCESSOR>
	  Writing $$<SMS_INVENTORY_PROCESSOR>
	  Compilation failed~Time has incorrect format or illegal values. on line 109
	  $$<SMS_INVENTORY_PROCESSOR>
	  No inventory changes for this machine, delta-mif not created
	  $$<SMS_INVENTORY_PROCESSOR>
	  Waiting for MIF ........ $$<SMS_INVENTORY_PROCESSOR>
	
	CAUSE
	=====
	
	This issue can occur on some Dell PowerEdge servers that are running Phoenix ROM
	BIOS PLUS version 1.10 A04 or A05. On these servers, the date string that is
	collected by the SMS Inventory Process is reported by the manufacturer in
	European format (YY/MM/DD) instead of American format (MM/DD/YY).
	
	WORKAROUND
	==========
	
	To work around this issue, open an incident with Microsoft Product Support
	Services and obtain the hotfix that is described in the following Knowledge Base
	article:
	
	  Q239534 SMS: Data Loader Cannot Process MIF Date Above Year 2030
	
	This hotfix provides a resolution for this issue. You are not charged for the
	hotfix.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 1.2.
	
	MORE INFORMATION
	================
	
	The Windows NT Inventory Agent extracts the video date from the following
	registry key:
	
	  HKEY_LOCAL_MACHINE\HARDWARE\DESCRIPTION\System\VideoBiosDate
	
	This part of the registry is built when Windows NT is started (it is a volatile
	part of the registry). If you modify the key, the changes are only valid until
	you restart the computer.
	
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbinterop kbConfig kbsms120 kbsms120bug kbInventory 
	Technology        : kbSMSSearch kbSMS120
	Version           : :1.2
	Hardware          : x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
