---
layout: page
title: "Q118665: How to Install ISDN on WFWG 3.11 RAS"
permalink: /kb/118/Q118665/
---

## Q118665: How to Install ISDN on WFWG 3.11 RAS

{% raw %}

	Article: Q118665
	Product(s): Windows for Workgroups and Windows NT Networking Issues
	Version(s): 3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows for Workgroups version 3.11 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	This article provides instructions to install ISDN on your Windows for
	Workgroups version 3.11 computer. These instructions are divided into the
	following sections and should be performed in the order given:
	
	- Before You Install ISDN
	
	- To Install ISDN
	
	- To Add an Entry in Remote Access Service (RAS) to Call an ISDN Server
	
	- To Receive Incoming Calls on the ISDN Line
	
	MORE INFORMATION
	================
	
	Before You Install ISDN
	-----------------------
	
	1. Because ISDN service is not available in all areas, check with your local
	  telephone company to see if ISDN service is available in your area before you
	  order an ISDN board.
	
	
	2. If ISDN service is available in your area, you can order an ISDN card from
	  Digi International at (612) 943-9020.
	
	3. When you order ISDN lines from your local ISDN service provider, make note of
	  the following information they give you because you will need to enter it in
	  Windows for Workgroups when you set up ISDN:
	
	  1. Service Profile ID (SPID)
	
	  2. Switch type
	
	  3. Line type
	
	4. Obtain the ISDN Windows for Workgroups version 3.11 software from Microsoft.
	
	
	To Install ISDN
	---------------
	
	1. In the Program Manager window, double-click the Network Setup icon, or use
	  the arrow keys to select the Network Setup icon, and then press ENTER.
	
	2. Choose the Drivers button.
	
	3. Choose the Add Adapter button.
	
	4. In the Network Adapters box, select DigiBoard PCIMAC - ISA ISDN Adapter, and
	  then choose the OK button.
	
	5. Follow the on-screen instructions, and then when you are prompted with the
	  DigiBoard PCIMAC - ISA ISDN Adapter Card Setup dialog box:
	
	  a. For IRQ Level, choose Disabled.
	
	  b. For I/O Base Address, choose an address that is not used by any other
	     device yet; if in doubt, leave at the default of 0x320.
	
	  c. For Memory Base Address, choose an address that is not used by any other
	     device yet; if in doubt, leave at the default of 0xD0000.
	
	  d. For Switch Type, select the switch type you got from your ISDN service
	     provider.
	
	6. Choose the LineOptions button. The Line Configuration Options dialog box
	  appears.
	
	7. In the Line Configuration Options dialog box:
	
	  a. For Line Number, leave at the default of Line 1.
	
	  b. Do not select the Enable Terminal Management check box. (This option
	     applies only to the AT&T switch type. For more information, see the
	     RAS Help file.)
	
	  c. For Number Of Logical Terminals, leave at the default of 1. (This
	     information is provided by the ISDN service provider. For more
	     information, see the RAS Help file.)
	
	  d. Enter your Service Profile ID (SPID) number in the format provided by your
	     ISDN service provider.
	
	  e. Enter your ISDN phone number, which is probably identical to your
	     seven-digit SPID.
	
	8. Choose the OK buttons and Close buttons as prompted until you are prompted to
	  choose Restart Computer or Continue; at this point, choose the Restart
	  Computer button if you don't have any unsaved open files in other
	  applications. If you need to save files in other applications, switch to
	  those applications to save the files and close the applications, and then
	  choose the Restart Computer button.
	
	
	To Add an Entry in Remote Access Service (RAS) to Call an ISDN Server
	---------------------------------------------------------------------
	
	1. Start RAS and choose the Add button.
	
	2. Enter an appropriate Entry Name, and then the server's ISDN Phone Number and
	  Description.
	
	3. In the Port box, select ISDN1.
	
	4. At the bottom of the Add Phone Book Entry dialog box, choose the ISDN button.
	
	5. In the ISDN Settings dialog box, select the appropriate line type that was
	  provided by your ISDN service provider (leave at 64K Digital if you are
	  unsure of the line type).
	
	6. Leave the Negotiate Line Type and Enable Hardware Compression check boxes
	  selected.
	
	7. In the Channels To Use box, leave the "1" if you want to use only one 64k
	  line during your communication with the ISDN server; enter "2" if you want to
	  use both ISDN B channels for a total of 128K Digital line speed.
	
	8. Choose the OK buttons in this and the previous dialog box.
	
	You are now ready to dial the ISDN RAS server.
	
	To Receive Incoming Calls on the ISDN Line
	------------------------------------------
	
	1. Make sure the RAS Point-to-Point (PTP) server is installed.
	
	2. Select the Allow Incoming Calls To This Computer check box.
	
	3. In the Server Port box, select ISDN1.
	
	4. Enter the password if you want a password that callers must know before they
	  can access your RAS PTP server.
	
	5. Choose the OK button.
	
	6. When you are prompted to quit RAS right now or to continue, choose the Yes
	  button.
	
	7. Restart RAS.
	
	When you choose the Answer button, your server will be ready to receive incoming
	ISDN calls.
	
	The third-party products discussed here are manufactured by vendors independent
	of Microsoft; we make no warranty, implied or otherwise, regarding these
	products' performance or reliability.
	
	Additional query words: wfw wfwg 3.11
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbWFWSearch kbWFW311
	Version           : :3.11
	
	=============================================================================
	

{% endraw %}
