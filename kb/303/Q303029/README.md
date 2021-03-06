---
layout: page
title: "Q303029: Combat Flight Simulator 2: Cannot Control Rudder or Throttle"
permalink: /kb/303/Q303029/
---

## Q303029: Combat Flight Simulator 2: Cannot Control Rudder or Throttle

{% raw %}

	Article: Q303029
	Product(s): Microsoft Home Games
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): kbimu
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Combat Flight Simulator 2: WWII Pacific Theater, version 1.0 
	-------------------------------------------------------------------------------
	
	WARNING:This information is preliminary and has not been confirmed or tested by Microsoft. Use only with discretion.IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	When you play Microsoft Combat Flight Simulator 2, you may not be able to
	control the throttle, the rudder, or both.
	
	CAUSE
	=====
	
	This issue can occur in the following situation:
	
	- You are using a Microsoft SideWinder game controller.
	
	  -and-
	
	- The game controller is connected to the Universal Serial Bus (USB) port.
	
	RESOLUTION
	==========
	
	To resolve this issue, remove and then reinstall the game controller software
	and the Combat Flight Simulator 2 program. To do this, follow these steps.
	
	NOTE: Because there are several versions of Microsoft Windows, the following
	steps may be different on your computer. If they are, see your product
	documentation to complete these steps.
	
	Step 1: Remove Microsoft Combat Flight Simulator 2
	--------------------------------------------------
	
	1. Quit all running programs.
	
	2. Unplug the USB game controller.
	
	3. On the taskbar, click Start, point to Programs, point to Microsoft Games,
	  point to "Combat Flight Simulator 2", and then click "Uninstall Combat Flight
	  Simulator 2".
	
	4. On the Combat Flight Simulator 2 screen that appears, click Uninstall, and
	  then click OK.
	
	5. You receive the following message:
	
	  Combat Flight Simulator 2 was uninstalled successfully
	
	  Click OK.
	
	Step 2: Remove Microsoft SideWinder Game Controller Software
	------------------------------------------------------------
	
	1. On the taskbar, click Start, point to Programs, point to Microsoft Hardware,
	  point to "SideWinder Game Controller Software 4.0", point to "SideWinder
	  <controllername>", and then click "Uninstall SideWinder Game Controller
	  Software 4.0".
	
	  You receive the following message:
	
	  Are you sure you want to completely remove "SideWinder
	  <controllername>" and all of its
	  components?
	
	2. Click Yes. On the Uninstallation dialog box that appears, click OK to delete
	  all files. If a Remove Shared File dialog box appears, click Yes To All, and
	  then click Yes to confirm the removal of shared components that the system
	  indicates are no longer being used.
	
	3. Click OK.
	
	Step 3: Restart the Computer in Safe Mode
	-----------------------------------------
	
	1. On the taskbar, click Start, and then click Run.
	
	2. In the Open box, type "Msconfig" (without the quotation marks), and then
	  click OK.
	
	3. In System Configuration Utility, on the General tab, click Advanced.
	
	4. In the Advanced Troubleshooting Settings dialog box, click to select the
	  Enable Startup Menu check box.
	
	5. Click OK twice, and then click Yes to restart the computer.
	
	6. On the Microsoft Windows <version> Startup menu that appears, select
	  "Safe mode", and then press ENTER.
	
	7. Click OK to close the Safe Mode dialog box or close the "Help and Support"
	  window.
	
	Step 4: Remove USB Devices
	--------------------------
	
	1. On the taskbar, click Start, point to Settings, and then click Control Panel.
	
	2. In Control Panel, double-click System.
	
	3. In the System Properties dialog box, click the Device Manager tab.
	
	4. Click the plus sign next to "Sound, video and game controllers" to expand the
	  branch.
	
	5. Under "Sound, video and game controllers", remove the following devices:
	
	  Microsoft SideWinder devices
	  HID-compliant game controllers
	  Microsoft Virtual Keyboards or Pointing devices
	
	  To do this, click a device, and then click Remove. On the Confirm Device
	  Removal message that appears, click OK.
	
	  NOTE: You must expand the "Sound, video and game controllers" branch again
	  after each device removal.
	
	6. Click the plus sign next to "Universal Serial Bus controllers" to expand the
	  branch.
	
	7. Under "Universal Serial Bus controllers", remove all devices. To do this,
	  click a device, and then click Remove. On the Confirm Device Removal message
	  that appears, click OK.
	
	8. Click Close.
	
	Step 5: Remove USB Device Enumeration Registry Keys
	---------------------------------------------------
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	1. On the taskbar, click Start, and then click Run.
	
	2. In the Open box, type "Regedit" (without the quotation marks), and then click
	  OK.
	
	3. In Registry Editor, expand the following registry subkey.
	
	  HKEY_LOCAL_MACHINE\Enum\HID
	
	4. Click the HID folder, and then click Delete on the Edit menu.
	
	  You receive the following message:
	
	  Are you sure you want to delete this key?
	
	5. Click Yes.
	
	6. Expand the following registry subkey:
	
	  HKEY_LOCAL_MACHINE\Enum\USB
	
	7. Click the USB folder, and then click Delete on the Edit menu.
	
	  You receive the following message:
	
	  Are you sure you want to delete this key?
	
	8. Click Yes.
	
	9. Expand the following registry subkey.
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\MediaResources\joystick
	
	10. Click the "joystick" folder, and then on the Edit menu, click Delete.
	
	  You receive the following message:
	
	  Are you sure you want to delete this key?
	
	11. Click Yes.
	
	12. On the Registry menu, click Exit.
	
	Step 6: Delete the Contents of the Temp Folder
	----------------------------------------------
	
	1. Start Windows Explorer, and then navigate to the following folder
	
	  <C>:\<Windows>\Temp
	
	  where <C> is the drive on which Windows is installed and where
	  <Windows> is the folder in which Windows is installed.
	
	2. On the Edit menu, click Select All.
	
	3. On the File menu, click Delete. If you receive a message that states "Confirm
	  Multiple File Delete," click Yes. If you receive a message that states
	  "Confirm File Delete," click "Yes to All".
	
	4. Quit Windows Explorer.
	
	Step 7: Empty the Recycle Bin
	-----------------------------
	
	1. On the desktop, double-click Recycle Bin.
	
	2. On the File menu, click Empty Recycle Bin. If you receive a message that
	  states "Confirm Multiple File Delete," click Yes.
	
	3. Quit Recycle Bin.
	
	Step 8: Restart Windows Normally
	--------------------------------
	
	1. Click Start, and then click Run.
	
	2. In the Open box, type "Msconfig" (without the quotation marks), and then
	  click OK.
	
	3. In System Configuration Utility, click Advanced on the General tab.
	
	4. In the Advanced Troubleshooting Settings dialog box, click to clear the
	  Enable Startup Menu check box.
	
	5. Click OK twice, and then click Yes to restart the computer.
	
	6. Follow the steps of the Add New Hardware Wizard to install drivers for the
	  devices in the computer.
	
	  NOTE: You may need to insert the Windows CD into the CD-ROM or DVD-ROM drive.
	
	  NOTE: If you have an original equipment manufacturer (OEM) installation of
	  Windows, the Windows files may also be located in one of the following
	  folders:
	
	  C:\WINDOWS\OPTIONS\CABS
	  C:\WINDOWS\OPTIONS\INSTALL
	
	Step 9: Reinstall Game Controller and Combat Flight Simulator 2
	---------------------------------------------------------------
	
	1. Reinstall the Microsoft SideWinder game controller and game controller
	  software. Restart the computer if prompted.
	
	2. Reinstall Combat Flight Simulator 2.
	
	  NOTE: During Setup, select "Customize installation options" on the Default
	  Installation Options screen. Do NOT install Combat Flight Simulator 2 the
	  following default folder:
	
	  C:\Program Files\Microsoft Games\Combat Flight Simulator 2
	
	  Install Combat Flight Simulator 2 in a different folder.
	
	3. Restart the computer.
	
	MORE INFORMATION
	================
	
	For additional information about USB game controller issues, click the article
	numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q191721 Disk Activity May Interfere with USB Devices
	
	  Q216096 SideWinder USB: Status Reported as Not Connected
	
	Additional query words: msgame
	
	======================================================================
	Keywords          : kbimu 
	Technology        : _IKkbbogus kbGamesSearch kbCombatFlightSim2 kbCombatFlightSimSearch kbSimSearch
	Version           : :1.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
