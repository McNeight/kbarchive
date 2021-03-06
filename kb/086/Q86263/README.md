---
layout: page
title: "Q86263: Redirecting Debugging Information Under Windows 3.0, 3.1"
permalink: /kb/086/Q86263/
---

## Q86263: Redirecting Debugging Information Under Windows 3.0, 3.1

{% raw %}

	Article: Q86263
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.0,3.1
	Operating System(s): 
	Keyword(s): kbfile kbsample kb16bitonly kbOSWin310 kbOSWin300
	Last Modified: 04-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) versions 3.0, 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Each new application for the Microsoft Windows environment should be tested
	under the Windows debugging kernel. When an application performs an illegal or
	potentially harmful operation, the debugging kernel traps the error and provides
	a descriptive message about the source of the problem. By default, the debugging
	kernel sends its messages to the AUX device (which maps to the COM1 port). This
	article describes how to redirect output from the debugging kernel under Windows
	versions 3.0 and 3.1.
	
	MORE INFORMATION
	================
	
	As noted above, in the Windows 3.0 and 3.1 environments, the debugging kernel
	sends its data to the AUX device, which (in general) maps to the COM1 port. One
	method to display this debugging information is to connect a serial
	communications terminal or another computer running a terminal emulation program
	to the COM1 port. Before running Windows, set the port's parameters
	appropriately through the MS-DOS MODE command. Placing the MODE command in the
	AUTOEXEC.BAT file automatically sets the port's parameters.
	
	When the debugging kernel starts, if no device is connected to COM1, the kernel
	displays a "Cannot write to device AUX" message box. If the COM1 port is
	dedicated to another use and cannot be connected to a serial terminal, you can
	configure the debug kernel to send its messages elsewhere. The remainder of this
	article explains the procedures required.
	
	Moreover, if you do not have a serial terminal connected to the COM1 port, then
	before starting the debug version of Windows, ensure that the following lines
	are added to the [Windows] section of the WIN.INI file:
	
	  DebugOptions=0x0000
	  DebugFilter=0x0000
	  DebugTaskFilter=       ;leave it blank
	
	and the following new section to your SYSTEM.INI file:
	
	  [Debug]
	  OutputTo=NUL
	
	The setting for the OutputTo entry in the SYSTEM.INI disables the default debug
	Kernel output to the AUX device (which maps to COM1 port). It is a good idea to
	do this, since DBWIN Windows sample application can be used to redirect output
	to either COM1 or COM2 port.
	
	The setting for the DebugOptions entry corresponds to the values for the
	dwOptions member of the WINDEBUGINFO structure in the Windows SDK. The setting
	for the DebugFilter entry corresponds to the values for the dwFilter member of
	WINDEBUGINFO. To determine the proper hexadecimal value for a setting, add the
	values of the options to be set. For example, to specify DBO_CHECKHEAP and
	DBO_FREEFILL, the setting for the DebugOptions entry would be 0x0021 (0x0001 +
	0x0020). For information about the possible values for these options and a full
	description of the WINDEBUGINFO structure, see the Microsoft Windows Programmers
	Reference, Volume 3.
	
	Windows 3.1
	-----------
	
	In the Windows 3.1 environment, the debugging terminal is not required. The
	Windows 3.1 debugging kernel provides two methods to redirect debugging
	information:
	
	1. Redirect the debugging information from COM1 into a file by specifying the
	  following in the [Debug] section of the SYSTEM.INI file:
	
	     OutputTo = <filename>
	
	  To disable sending debug messages to AUX, specify the following in the
	  SYSTEM.INI file:
	
	     OutputTo = NUL
	
	2. Version 3.1 of the Microsoft Windows Software Development Kit (SDK) includes
	  the DBWIN sample program in the advanced samples directory (by default,
	  C:\WINDEV\SAMPLES). DBWIN provides a good interface and some useful features
	  to debug an application in the Windows environment. DBWIN can disable sending
	  debugging messages to AUX or redirect the debugging messages to any of the
	  following:
	
	   - The COM1 port
	
	   - The COM2 port
	
	   - A window on the primary display
	
	   - A secondary monochrome monitor
	
	  These redirection options are listed on the Options menu. When using DBWIN,
	  choose Settings from the Options menu and verify that the Break On Traces
	  option is not selected. For more information on DBWIN, see the DBAPI.TXT and
	  DBWIN.TXT files in the DBWIN directory, Appendix C of the "Microsoft Windows
	  Software Development Kit: Programming Tools" version 3.1 manual, and the
	  online help files.
	
	Windows 3.0
	-----------
	
	Windows 3.0 does not provide a built-in method to redirect debugging output;
	external measures are required.
	
	This article outlines two methods to redirect output under Windows 3.0. The first
	is through the WINAUX.SYS device driver that redirects debugging output into a
	window on the main display, similar to the DBWIN application discussed above.
	The second is through the OX.SYS device driver that redirects debugging output
	to a secondary monochrome adapter connected to the system.
	
	The WINAUX.SYS device driver is the method of choice.
	
	The following file is available for download from the Microsoft Download Center:
	
	  WinAux.exe
	  (http://download.microsoft.com/download/platformsdk/file89/3.1/W31/EN-US/WINAUX.EXE)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	To install WINAUX.SYS, place the following line in the CONFIG.SYS file:
	
	  DEVICE=WINAUX.SYS
	
	Another method to redirect debugging output under Windows 3.0 is to use the
	OX.SYS device driver that redirects output for the AUX device to a monochrome
	video adapter. Many development systems have a secondary monochrome display to
	use with CodeView for Windows (CVW). OX.SYS sends the debug messages to the
	monochrome display.
	
	The OX.SYS file and its source code is available in the Software Library. If
	necessary, you can modify the OX source code to direct debugging output to
	another device such as LPT1, COM2, and so on.
	
	The following file is available for download from the Microsoft Download Center:
	
	  Ox.exe
	  (http://download.microsoft.com/download/pandora/app95/3.1/W31/EN-US/OX.EXE)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	To install OX.SYS, add the following line to the CONFIG.SYS file:
	
	  DEVICE=OX.SYS
	
	Under Windows 3.0, OX.SYS is limited because it provides an input-only or
	output-only device. Therefore, when the Windows debugging kernel provides output
	for a FatalExit message followed by the "Abort, Break, Ignore?" prompt, OX.SYS
	cannot obtain the user's response. Third-party developers have developed
	bi-directional device drivers to address this limitation and have placed the
	drivers into the public domain. Two examples are WINRIP.SYS and MONO-DRV.SYS.
	
	Additional query words: softlib OX.EXE WINAUX.EXE kbfile
	
	======================================================================
	Keywords          : kbfile kbsample kb16bitonly kbOSWin310 kbOSWin300 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK300 kbWinSDK310
	Version           : WINDOWS:3.0,3.1
	
	=============================================================================
	

{% endraw %}
