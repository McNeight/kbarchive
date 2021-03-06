---
layout: page
title: "Q135896: Windows 95 CD-ROM Hardware.txt File"
permalink: /kb/135/Q135896/
---

## Q135896: Windows 95 CD-ROM Hardware.txt File

{% raw %}

	Article: Q135896
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 95
	Operating System(s): 
	Keyword(s): win95
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains a copy of the information in the Hardware.txt file from
	the Windows 95 CD-ROM. Setup copies this file to the Windows folder.
	
	MORE INFORMATION
	================
	
	----------------------------------------------------------------------
	                Microsoft Windows 95 README for Hardware
	                                August 1995
	----------------------------------------------------------------------
	
	                (c) Copyright Microsoft Corporation, 1995
	
	This document provides complementary or late-breaking information to
	supplement the Microsoft Windows 95 documentation.
	
	------------------------
	How to Use This Document
	------------------------
	
	To view Hardware.txt on screen in Notepad, maximize the Notepad
	window.
	
	To print Hardware.txt, open it in Notepad or another word processor,
	then use the Print command on the File menu.
	
	--------
	CONTENTS
	
	PLUG AND PLAY
	SCANNERS
	MODEMS
	TAPE DRIVES
	
	--------
	
	PLUG AND PLAY
	=============
	
	PCI Systems
	-----------
	If the video is configured by the BIOS to consume an IRQ and you need
	to use the secondary PCI IDE controller in your PC, your video will
	work only in VGA mode. To load the accelerated Windows 95 driver for
	your video, disable the secondary PCI IDE controller in the BIOS and
	the Device Manager (located in the System control panel). Another
	alternative (if supported by the BIOS) is to disable the IRQ of the
	video device.
	
	IBM Thinkpad Models 750 (all 750 series except 750ce)
	-----------------------------------------------------
	A new BIOS that solves several problems with power management is
	available from IBM's bulletin board. Download the latest System
	Program Service Diskette for the Thinkpad 750 from the BBS. See your
	hardware documentation for information on how to access the IBM
	bulletin board.
	
	IBM Thinkpad Models 755cd, cx, ce, cse, cdv (but not 755c)
	----------------------------------------------------------
	We are in the process of resolving with IBM several known problems:
	1. Mwave is lost if you have more than 8 MB of memory.
	  - IBM is working on updated drivers. The 1.1 revision does not
	    solve this problem.
	2. If you install Windows 95 into the same directory that contains
	  your current version of Windows, Mwave will continue to function.
	  - If you install Windows 95 to a different directory, Mwave will
	    not work unless you reinstall the Mwave drivers by using IBM's
	    Mwave setup program disks. This is by design. The Windows 3.1
	    drivers are required to run the Mwave chip.
	3. The infrared port shows up with problems in Device Manager.
	  - IBM is working on an updated Infrared VxD that resolves this
	    problem.
	4. Docking is not supported.
	  - IBM is expected to release fixes to their Plug and Play BIOS
	    shortly, which will enable full Windows 95 Plug and Play and
	    docking support. For updates to the System Program Service
	    Diskette for your model of Thinkpad, check IBM's bulletin
	    board. See your hardware documentation for information about
	    accessing the bulletin board.
	5. There are power management problems with the suspend and resume
	  commands.
	  - If you have a 1994 BIOS, you can usually resolve these problems
	    by upgrading to the latest Flash BIOS revision from 1995. You can
	    find it on CompuServe, THINKPAD forum, or on IBM's bulletin
	    board.
	    See your IBM hardware documentation for information about
	    accessing the bulletin board.
	6. Mwave versions earlier than 1.2 contain numerous bugs.
	  - These bugs in earlier versions of Mwave cause serious problems
	    when Mwave is run on Windows 95. For more information, call the
	    IBM PC HelpCenter.
	
	IBM Thinkpad Dock II
	--------------------
	If you use IBM Thinkpad Dock II, you must disable the BIOS for the
	Adaptec 1530P SCSI controller in the docking station before starting
	your computer while it is docked. If you do not, your computer will
	hang repeatedly. This controller works fine in protected mode even
	without the BIOS enabled, so you should not lose access to any SCSI
	devices as a result.
	
	To disable the BIOS:
	1. Restart your computer while it is docked.
	2. Press CTRL+A to start the Adaptec SCSISelect utility.
	3. Choose Configure/View Host Adapter Settings.
	4. Choose Advanced Configuration Options.
	5. Change the setting for Host Adapter BIOS to Disabled.
	
	Press ESC until you are prompted to exit the utility, at which point
	the computer will restart.
	
	An even better solution is to disable the BIOS completely, which will
	enable the adapter to run completely in Plug and Play mode. This will
	allow its resources to be allocated dynamically at Windows 95 startup.
	However, this requires changing a DIP switch inside the dock unit.
	For details about disabling the SCSI adapter BIOS, refer to your Dock
	II manual.
	
	Micron M5-PI Series
	-------------------
	Before installing Windows, users of Micron M5-PI series (P-60, P-66)
	need to be sure the BIOS read/write jumper(W22) is set to the read-
	only position. If you try to install Windows 95 with this jumper in
	the read\write position, it may cause BIOS corruption. For more
	information, contact Micron Technologies.
	
	Micron P90/100
	---------------
	Before installing Windows, users of Micron P90 and P100 systems must
	make sure their BIOS version is N15 or later. For more information,
	contact Micron Technologies.
	
	NEC Versa M and AT&T Globalyst
	------------------------------
	If you use AT&T Globalyst and NEC Versa M, you must set the BIOS
	setting for PCMCIA Power to Enabled before running the PC Card
	(PCMCIA) wizard to enable the Windows 95 PCMCIA support. The default
	setting is Disabled.
	
	To change the PCMCIA Power setting to Enabled:
	1. Restart your computer.
	2. When the cursor changes to a rectangle, press F1.
	3. When the BIOS configuration program is ready, select Power, and
	  then change the PCMCIA Power setting to Enabled.
	4. Save these settings.
	
	Winbook XP
	----------
	There is a problem on the Winbook XP which could cause the keyboard
	not to function properly. The workaround is to disable Windows 95
	power status polling.
	
	To disable Windows 95 power status polling:
	1. In Control Panel, double-click the System icon, and then click the
	  Device Manager tab.
	2. Click the plus (+) sign next to the system class you want to
	  change.
	3. Double click Advanced Power Management Support, and then click the
	  Settings tab.
	4. Make sure that the Disable Power Status Polling box is checked.
	5. Click OK to save your changes and exit Control Panel.
	
	HP OmniBook 600C
	----------------
	The Omnibook's PCMCIA controller is supported via special drivers
	in the Drivers directory on the CD version of Windows 95.
	Refer to the Readme file in the Drivers directory for installation
	instructions.
	
	The OmniBook also requires a special mouse driver for Windows.
	Windows 95 Setup will preserve and use this driver when upgrading over
	Windows 3.1. If you installed Windows 95 into a new directory
	on an OmniBook, then you must copy the HP Obmouse.drv file into the
	Windows\System directory, and then change the following lines in your
	System.ini file:
	
	  [boot]
	  mouse.drv=obmouse.drv
	
	  [386Enh]
	  mouse=*vmd
	
	DEC Hi Note Ultra
	------------------
	There are known problems with PCMCIA under older BIOS versions on
	this machine. If you encounter difficulties getting your PCMCIA cards
	recognized correctly, update your BIOS to a version later than
	3/31/95 (v.1.3).
	
	Acer Acernotes
	--------------
	You may hear a negative (low) tone when you insert the PCMCIA card
	after activating the 32-bit PCMCIA drivers. If this happens, remove
	the EMMExclude line from the System.ini file and the exclude range
	data from the EMM386 line in the Config.sys file. If you still get a
	low tone, try carrying out the following procedure:
	
	1. Double-click the PCMCIA icon in Control Panel.
	2. Click Global Settings, and make sure Automatic Selection is not
	  checked.
	3. Set the valid range to start at 000D0000 and end at 000DFFFF.
	
	Compaq Aero
	------------
	The Compaq Aero floppy disk drive is only partially supported by the
	Windows 95 PCMCIA drivers. To gain access to the floppy drive,
	you need to make sure the card is already inserted when you boot.
	After the card has been configured by Windows 95, you can remove and
	insert the card normally.
	
	If access to the floppy card still fails:
	1. In Control Panel, double-click the System icon, and then click the
	  Device Manager tab.
	2. Click the plus (+) sign next to "Floppy disk controllers."
	3. Double-click the floppy disk controller you are having trouble
	  with.
	4. Look at the Device Status area.
	5. If it reports a resource conflict, click the Resources tab,
	  click the "Set Configuration Manually" button, then click OK.
	
	DEC Venturis and Media Vision Audio Cards
	-----------------------------------------
	There's a known problem with certain combinations of the DEC Venturis
	and Media Vision Audio cards.
	
	If you experience problems with this combination:
	1. In Control Panel, double-click the System icon.
	2. Click the Device Manager tab.
	3. Under Sound, Video and Game Controllers, double-click
	  Media Vision Pro Audio Spectrum 16/Studio With SCSI.
	4. Click the Settings tab.
	5. Make sure the Enable Warm Boot box is not checked.
	
	Zenith NoteFLEX 486DX and PC cards
	-----------------------------------
	If your PC cards are not being detected or working properly with the
	Windows 95 PCMCIA drivers, follow the below procedure to reserve IRQ
	10 and the memory range C000-CBFF.
	
	To reserve resources:
	1. In Control Panel, double-click the System icon.
	2. Click the Device Manager tab.
	3. Click Computer, and then click Properties.
	4. Click the Reserve Resources tab.
	5. Click Interrupt Request (IRQ), and then click Add.
	6. Reserve IRQ 10, and then click OK.
	7. Click Memory, and then click Add.
	8. Reserve the memory range C000-CBFF, and then click OK.
	9. Click OK again, and then restart your computer.
	
	Zenith NoteFLEX 486DX and Flexshow docking station
	--------------------------------------------------
	If you are using the NoteFLEX with the Flexshow docking station, you
	must reserve IRQ 10 so that the built-in CD-ROM drive will work. To
	do this, follow the above procedure and only reserve IRQ 10.
	
	In your Config.sys file, make sure the line loading Mztinit.sys
	appears before the line loading PCenable.exe or your computer will
	stop responding during startup.
	
	Also, to avoid numerous "Bad Command or File Name" errors during
	startup and to ensure the computer is configured properly, copy
	Rplstr.com from your \Dos directory to your \Windows directory.
	
	Zenith NoteFLEX 486DX and PCMCIA hard drives
	--------------------------------------------
	If you are using a PCMCIA hard drive with this computer, you must
	enable 32-bit PCMCIA support in order to access the drive.
	
	To enable 32-bit PCMCIA support:
	1. In Control Panel, double-click the PC Card (PCMCIA) icon.
	2. Follow the instructions on your screen.
	
	If you see properties for your PCMCIA socket instead of the wizard,
	Windows 32-bit support for PC cards is already turned on. If you do
	not see the PC Card (PCMCIA) icon in Control Panel, double-click the
	Add New Hardware icon in Control Panel to install your PCMCIA socket.
	
	Megahertz Em1144T and 16-bit Modem
	----------------------------------
	If you experience problems setting up the modem side of this card
	in a real-mode PCMCIA environment, try explicitly setting the COMIRQ
	and COMBASE parameters in the Megahertz section of your Protocol.ini
	file. There is a known problem where this card enabler ignores the
	default values set for these parameters.
	
	Digital Venturis (any model)
	----------------------------
	If PNPISA and/or PCI cards are not automatically recognized, or if
	Windows generates Blue Screen errors when reconfiguring your COM
	ports, contact Digital for a new BIOS.
	
	Printing from Device Manager
	----------------------------
	If you choose to print "all devices and system summary" from Device
	Manager, the device detection code MAY cause problems for MS-DOS-
	based programs. The symptom of this problem is that after you print,
	your computer reports that it is out of memory when you try to run
	an MS-DOS-based program. When this problem occurs, you may need to
	restart Windows to correct the problem.
	
	Mozart Sound Card/Canon Innova 550 CD Driver Problem
	----------------------------------------------------
	You may experience problems when you start up Windows 95. To receive
	a new driver that works with Windows 95, contact the Canon Help Desk.
	
	Users of TrueFFS Flash File System for PCMCIA Cards
	---------------------------------------------------
	The MS-DOS or Windows 3.1 versions of the TrueFFS driver will not work
	with the Windows 95 PCMCIA driver. To work with FTL formatted Linear
	Flash PCMCIA cards when the Windows 95 PCMCIA driver is enabled, you
	must install a new Windows 95 device driver provided by M-Systems. To
	do this, carry out the following procedure:
	
	1. In Control Panel, double-click the Add New Hardware icon.
	2. Click Next, and then click the option not to have Windows search
	  for your new hardware.
	3. Click Hard Disk Controllers, and then click Next.
	4. From the list, click M-Systems.
	5. Click the specific Flash Card, and then click Next. Then follow
	  the instructions on your screen.
	
	NOTE: If M-Systems is not shown in the list, click Have Disk, and then
	insert the M-Systems Windows 95 installation disk and follow the
	instructions on your screen.
	
	Micronics Motherboards with a Flash BIOS
	-----------------------------------------
	Before installing Windows, users of Micronics motherboards with a
	Flash BIOS need to be sure the BIOS read/write jumper is set to the
	read-only position. If you try to install Windows 95 with this jumper
	in the read\write position, it may cause BIOS corruption. For more
	information, contact your computer manufacturer.
	
	Toshiba Computers: T610 T400 series, T2100 series, T2400 series,
	T4700 series, T4800 series, and the T4900CT and T3600
	----------------------------------------------------------------
	If you use any of these Toshiba computers, Toshiba strongly recommends
	upgrading your computer's BIOS to version 5.0. The upgraded BIOS
	provides additional functionality for the Windows 95 operating system.
	For more information, in the United States contact Toshiba at
	(800) 999-4273. Outside the U.S., contact your local Toshiba dealer.
	
	Toshiba T2150 models
	---------------------
	If your system stops responding during suspend or resume operations,
	comment out the line that loads the Toscdrom.sys driver from your
	Config.sys file. For example:
	
	  rem device=c:\cddrv\toscdrom.sys
	
	Sanyo 3-D ATAPI (IDE) CD-ROM drive
	----------------------------------
	The Sanyo 3-D ATAPI (IDE) CD-ROM drive uses a proprietary scheme to
	support the three-disk changer. Although all three drives will appear
	when you are running in protected mode, only one of them will be
	accessible.
	
	To regain access to all three drives, remove the REM command from the
	beginning of the MSCDEX line in your Autoexec.bat file. You also need
	to disable the Windows 95 protected-mode disk driver. To do this,
	carry out the following procedure:
	
	1. Click the Start button, and then point to Settings.
	2. Click Control Panel, and then double-click the System icon.
	3. Click the Device Manager tab.
	4. Click View Devices By Connection.
	5. Click plus signs next to devices until you find the Sanyo drive.
	6. After you find the Sanyo drive, look at the levels above it
	  until you find the parent controller.
	7. Click the controller, and then click Properties.
	8. In the Device Usage area, clear the check box next to the current
	  configuration.
	
	This will enable access to all three drives from Windows 95 protected-
	mode; however, your disk, CD, and any other devices under the
	controller will be accessed only through real-mode drivers.
	
	For information about updating your driver to a Windows 95 driver,
	contact your hardware vendor.
	
	Micron PowerServer M5-PE (66 MHz Pentium PCI/EISA bus)
	-------------------------------------------------------
	The BusLogic BT-946C PCI SCSI adapter may not be compatible with
	Windows 95. If you encounter difficulties with your SCSI peripherals,
	contact Micron to determine whether you need an updated adapter.
	
	SCANNERS
	========
	
	Windows 95 will detect most scanner hardware, but does not supply
	protected-mode drivers for any scanner model.
	
	All SCSI scanners use a feature called ASPI to talk to the controller
	in question. Windows 95 supports ASPI in protected mode. Hence, a
	scanner, although listed as an "unknown device" in Device Manager, is
	supported through protected-mode drivers in Windows 95, if there is a
	protected-mode driver for the SCSI controller in question.
	
	Note that theoretically you would not need the ASPI manager real-mode
	driver (such as Aspi2dos.sys) in your Config.sys file. However, some
	programs, such as HP ScanJet II and its associated real-mode drivers,
	Sj!!.sys and Sjiix.sys, require the real-mode ASPI manager to be in
	the Config.sys file or they will fail to load. In these cases, you
	would need to keep the real-mode drivers in the Config.sys file, but
	Windows 95 will still support the scanner through the protected-mode
	SCSI miniport driver (if one exists for the SCSI controller in
	question).
	
	Logitech Scanman
	----------------
	If you use a handheld Logitech Scanman on a computer that has more
	than 16 MB of memory, you may see the following message: "Insufficient
	system resources." To resolve this problem, you can obtain an updated
	driver, Scanupt.exe, from the Logitech bulletin board or from
	CompuServe.
	
	MODEMS
	======
	
	Modems Control Panel
	--------------------
	In order to use your modem with the built-in communications features
	of Windows 95, including HyperTerminal, and Dial-Up Networking, your
	modem must be configured in Modems properties in Control Panel.
	
	Settings made in Modems properties do not affect modem operation in
	programs designed for MS-DOS or Windows 3.1.
	
	Modem Detection
	---------------
	If Windows 95 detects your modem as a "Standard Modem," or incorrectly
	detects its make and model, you can use the Change button in the
	Install New Modem wizard to make a different selection. However, if
	you manually select an incorrect type, your modem may not to work with
	Windows 95 communications features. If this happens, double-click the
	Modems icon in Control Panel, remove the modem, and then add it back
	as one of the Standard modem types.
	
	When configured for "Standard Modem," Windows 95 will use your modem
	with its factory default settings. The modem will make optimal high-
	speed connections with Windows 95 communications features. However,
	you will not be able to adjust some of the modem's settings, such as
	speaker volume and cellular protocols.
	
	Racal Modems
	------------
	If you have a Racal modem, do not use detection in the Install New
	Modem wizard. Instead, click Don't Detect My Modem, and then pick one
	of the standard modem types. If you have already run detection and
	your modem is not responding, turn the modem off and then back on
	again.
	
	Minitel (France)
	----------------
	Some modems may not be able to connect to French Minitel in
	HyperTerminal by using the Windows 95 default settings. To correct
	this, carry out the following procedure:
	
	1. Check your modem manual for a command that will enable your modem
	  to connect in V.23 modulation to Minitel.
	2. In Control Panel, double-click the Modems icon, click the name of
	  your modem, and then click Properties.
	3. Click the Connection tab, and then click Advanced.
	4. In the Extra Settings box, type the command.
	
	TAPE DRIVES
	===========
	
	Tape Drive Detection
	--------------------
	Plug and Play software does not detect tape drives. As a result, the
	only tape drives that appear in Device Manager are SCSI tape drives,
	which appear as either an unknown device or a tape drive.
	
	However, most backup programs do detect tape drives, so don't be
	concerned if your tape drive does not appear in Device Manager. If
	your backup software does not detect your tape drive, contact the
	company that wrote the software.
	
	Tape Drive Compatibility
	------------------------
	Microsoft Backup works only with the 1992 or later versions of the
	tape drives listed below. If your tape drive does not appear in the
	list below, contact your tape drive manufacturer for information about
	backup software that you can use with Windows 95.
	
	The following tape drives are compatible with Backup:
	- QIC 40, 80, and 3010 tape drives made by the following companies,
	 and connected to the primary floppy disk controller:
	    Colorado Memory Systems
	    Conner
	    IOmega
	    Wangtek (only in hardware phantom mode)
	- Colorado Memory Systems QIC 40, 80, and 3010 tape drives connected
	 through a parallel port.
	
	The following are not compatible with Backup:
	- Drives connected to a secondary floppy disk controller or to an
	 accelerator card
	- Archive drives
	- Irwin AccuTrak tapes
	- Irwin drives
	- Mountain drives
	- QIC Wide tapes
	- QIC 3020 drives
	- SCSI tape drives
	- Travan drives
	- Summit drives
	
	Additional query words: arrow
	
	======================================================================
	Keywords          : win95 
	Technology        : kbWin95search kbZNotKeyword3
	Version           : 95
	
	=============================================================================
	

{% endraw %}
