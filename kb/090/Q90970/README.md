---
layout: page
title: "Q90970: Setup, Network Card Settings, and Preliminary Troubleshooting"
permalink: /kb/090/Q90970/
---

## Q90970: Setup, Network Card Settings, and Preliminary Troubleshooting

{% raw %}

	Article: Q90970
	Product(s): Microsoft Windows 3.x Retail Product
	Version(s): WINDOWS:
	Operating System(s): 
	Keyword(s): 
	Last Modified: 20-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows for Workgroups 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	This article contains questions and answers about Windows for Workgroups Setup,
	network card settings, and important preliminary troubleshooting steps.
	
	MORE INFORMATION
	================
	
	The following information applies to Microsoft Windows(TM) for Workgroups
	version 3.1.
	
	1. Q. What are the memory and disk space system requirements for Microsoft
	  Windows for Workgroups?
	
	  A. Windows for Workgroups must be run in 386 enhanced mode in order to share
	  resources. 386 enhanced mode requires a minimum of 3 megabytes (MB) of
	  memory; however, 4 MB is recommended. Standard mode operation requires a
	  minimum of 2 MB of memory. These memory requirements refer to total
	  conventional and extended memory only. Windows for Workgroups requires a
	  minimum of 9.5 MB and a maximum of 14.5 MB of free disk space. Upgrading over
	  Microsoft Windows operating system version 3.1 reduces these free disk space
	  requirements to a minimum of 3.5 MB and a maximum of 8.5 MB. Workgroup
	  Connections require 320 kilobytes (K) of free conventional memory and 1 MB of
	  free disk space.
	
	  Windows for Workgroups must be installed on a workstation that has a hard disk
	  drive. Windows for Workgroups and Workgroup Connections are supported on
	  MS-DOS-based systems.
	
	2. Q. I'm having difficulty installing Microsoft Windows for Workgroups. What
	  should I do?
	
	  A. Complete information on installing Windows for Workgroups is contained in
	  the "Getting Started" manual. The following are five general setup tips:
	
	  1. Before you run the Setup program, start your machine with a minimal
	     configuration. For more information, please refer to the section titled
	     "Streamline the CONFIG.SYS and AUTOEXEC.BAT Files" in Chapter 6 of the
	     "Getting Started" manual. The examples provided in this manual refer to a
	     minimum configuration after Windows for Workgroups is loaded. The last
	     three lines in the CONFIG.SYS file and the first line in the AUTOEXEC.BAT
	     file that relate to the network are not loaded before installation.
	
	  2. Windows for Workgroups installations are most successful when installed to
	     a newly created and empty subdirectory. This applies to all packages of
	     Windows for Workgroups, including upgrade packages. Upgrading over a
	     Windows 3.x environment configured for a network other than Microsoft LAN
	     Manager or Novell(R) NetWare(R) may cause incompatibility issues. If
	     Windows 3.x is currently installed on your computer for a network, choose
	     the Windows Setup icon, choose Change Systems Settings from the Options
	     menu, and select the No Network Installed option before you run the
	     Windows for Workgroups upgrade.
	
	  3. If your Windows 3.x environment is not installed for a network and you are
	     using any third-party drivers, font software, desktop shells, or
	     utilities, consider installing Windows for Workgroups to a different
	     directory. If you choose to upgrade over the Windows 3.x directories, at
	     least disable any third-party products from the Windows 3.x environment
	     before you run Setup.
	
	  4. Workgroup Connections should be installed to a different subdirectory; do
	     not upgrade over Windows. If you do so, a new SYSTEM.INI file is created.
	
	  5. During Setup, if your machine locks up, reboots itself, or displays
	     corrupt images on the screen, Setup may have incorrectly recognized your
	     hardware. For solutions to these problems, please refer to the section
	     titled "Setting Up Windows for Workgroups" in Chapter 6 of the "Getting
	     Started" manual.
	
	3. Q. Where can I find more information about setup entries and the setup of
	  supported network adapter cards?
	
	  A. To properly configure your network card, please refer to the complete
	  instructions in the section titled "Setting Up a Network Card" in Chapter 6
	  of the "Getting Started" manual. The following are four general tips:
	
	  1. Entries referring to Workgroup and ComputerName should be limited to 15
	     characters. All other share names should conform to the MS-DOS file-naming
	     convention, which consists of an eight-character maximum filename and an
	     optional extension limited to three characters.
	
	
	  2. The Windows for Workgroups Setup may not always detect your network card
	     and its configuration accurately. For this reason, you may want to choose
	     Custom Setup so that you can modify the network card configuration. This
	     configuration can also be changed in the Windows for Workgroups Control
	     Panel after Setup is complete.
	
	  3. Some cards, such as the Intel(R) EtherExpress(TM), may be software
	     configurable; therefore, there may not be any jumpers and/or switches on
	     the card to configure the IRQ, I/O port, and RAM addresses. The Windows
	     for Workgroups network card installation software configures these cards.
	
	  4. Windows for Workgroups supports only the NetBEUI protocol. The MSIPX
	     protocol is available only after you install the optional network
	     functionality for Novell NetWare. The protocols conform to the Network
	     Driver Interface Specification (NDIS). If you want to use another
	     protocol, obtain the NDIS-compliant protocol driver and an OEMSETUP.INF
	     file from the software company that provides the protocol.
	
	4. Q. Where can I find information on installing unlisted network protocols and
	  adapters?
	
	  A. Information on installing third-party networks and protocols can be found
	  on pages 152 and 204 of the "User's Guide." The following are six general
	  tips:
	
	  1. For information about using the Microsoft LAN Manager TCP/IP protocol with
	     Microsoft Windows for Workgroups, please refer to the Windows for
	     Workgroups Resource Kit. For information on purchasing Microsoft Data Link
	     Control (DLC) and Microsoft TCP/IP for Windows for Workgroups, Call
	     Microsoft Consumer Sales at (800) 426-9400. Both TCP/IP and MSDLC are
	     supported by Microsoft LAN Manager support.
	
	  2. The MSIPX protocol is available only after you add Novell NetWare
	     connectivity to Windows for Workgroups.
	
	  3. If you have an Ethernet adapter that can emulate either an NE1000 or an
	     NE2000 network card, choose the NE1000- compatible adapter for an 8-bit
	     card or the NE2000- compatible adapter for a 16-bit card in the Network
	     Adapter dialog box.
	
	  4. If you have an ArcNet(R) adapter that conforms to the Network Driver
	     Interface Specification (NDIS), select ArcNet Compatible in the Network
	     Adapter dialog box.
	
	  5. If your network card is not listed in the Network Adapter Compatibility
	     List, you must obtain the NDIS driver specific to your network card and
	     the OEMSETUP.INF file from the vendor of your network card.
	
	5. Q. I'm receiving the error message, "The Protocol Manager has reported an
	  incomplete binding." What is causing this error?
	
	  A. The error "The Protocol Manager has reported an incomplete binding" is most
	  often caused by a conflict in the upper memory area or an incorrect setting
	  in the PROTOCOL.INI file. To correct the error, use the following two steps:
	
	  1. If the memory manager EMM386.EXE is loaded in the CONFIG.SYS file, modify
	     the line to read as follows:
	
	  device=<path>emm386.exex=a000-efff
	
	  2. Save this file and restart the computer. If the
	
	  incomplete binding
	
	     error message continues after you modify the CONFIG.SYS file, the answers
	     to the next two questions may help you correct this problem.
	
	6. Q. I'm still receiving the "incomplete binding" error message after I exclude
	  the upper memory area with EMM386 in the CONFIG.SYS file. What should I try
	  next?
	
	  A. If you still receive the "incomplete binding" error message after you have
	  excluded the upper memory area, use the following four steps to check for
	  possible PROTOCOL.INI setting errors:
	
	  1. In the Control Panel window, choose the Network icon.
	
	  2. Choose the Adapters button and note the brand name and model of the
	     network card listed under Network Adapter In Use. If the network adapter
	     is incorrect, choose the Remove button, then choose the Add button to
	     select the correct driver.
	
	  3. Note the IRQ, I/O Port, and Base Memory address configurations. If any of
	     these settings is incorrect, change the entry to its correct setting. This
	     configuration information can also be found by choosing the Setup button
	     in the Network Adapter dialog box.
	
	  4. The last item to check is the protocol. You must have at least one
	     protocol selected in the dialog box titled Protocols In Use. Windows for
	     Workgroups supports the NetBEUI protocol. MSIPX is only available after
	     Novell NetWare connectivity is added to Windows for Workgroups.
	
	7. Q. I'm still receiving the "incomplete binding" error message even after I
	  have confirmed and corrected all the settings in the PROTOCOL.INI file. What
	  should I do now?
	
	  A. If you continue to receive the "incomplete binding" error message after you
	  verify that all the settings in the PROTOCOL.INI file are correct, and if you
	  are using the Intel EtherExpress adapter card, use the following three steps:
	
	  1. Turn off the computer and disconnect any cables from the card.
	
	  2. Attach a T connector to the card with two terminators on the T.
	
	  3. Restart the computer. If the message
	
	  The Protocol Manager has reported an incomplete binding
	
	     no longer displays, there is a problem with the cable.
	
	8. Q. I'm running Microsoft Windows for Workgroups on a Novell Token Ring
	  network and am receiving the error message
	
	  File server cannot be found.
	
	  What is causing this error?
	
	  A. If you are running on a Novell Token Ring network, the error
	
	  File server cannot be found
	
	  may be caused by loading ROUTE.COM in the AUTOEXEC.BAT file. Edit the
	  AUTOEXEC.BAT file and remove the line that loads ROUTE.COM. After you save
	  the file, restart your machine.
	
	9. Q. I'm running on a Novell Ethernet network and am receiving the error
	  message
	
	  File server cannot be found.
	
	  What is causing this error?
	
	  A. If you are running on a Novell Ethernet network, the error message
	
	  File server cannot be found
	
	  may be caused by exceeding the user limit of the Novell software or by an
	  entry in the PROTOCOL.INI file referring to the incorrect Ethernet frame
	  type. If you have not exceeded your user limit on the Novell network, try
	  correcting this problem by using the following four steps:
	
	  1. In the Control Panel window, choose the Network icon, then choose the
	     Adapters button.
	
	  2. Select the adapter that is bound to MSIPX, choose the Setup button, then
	     choose the Advanced button.
	
	  3. Select Novell IPX from the Protocols In Use box, then choose the Settings
	     button.
	
	  4. In the Adapter Media Type Value box, you will see either Novell/Ethernet
	     or Ethernet_II(DIX). Note which parameter is indicated, and then select
	     the other Media Type parameter.
	
	10. Q. I'm receiving the error message
	
	  NetBIOS session limit exceeded.
	
	  What is causing this error?
	
	  A. "NetBIOS session limit exceeded" refers to the number of connections that
	  can be made to your server at any one time. This limit is affected by the
	  number of sessions set in the [MS$NetBEUI] section of the PROTOCOL.INI file.
	  Other protocols refer to variables other than SESSIONS. Please refer to your
	  network protocol documentation for more information. Use the following four
	  steps to increase the number of sessions:
	
	  1. Open the PROTOCOL.INI file from the WINDOWS directory in an ASCII text
	     editor, such as Microsoft Windows Notepad.
	
	  2. Locate the section titled [MS$NetBEUI].
	
	  3. Double the value following SESSIONS=. When you increase the value
	     following SESSIONS=, you must also increase the value following NCBS=. The
	     NCBS value should be double the value of SESSIONS.
	
	  4. Save the file and restart Windows.
	
	Additional query words: 3.10 ivrfax wfwg wc AWG31
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbWFWSearch
	Version           : WINDOWS:
	
	=============================================================================
	

{% endraw %}
