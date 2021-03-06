---
layout: page
title: "Q97016: Windows Err Msg with MS-DOS 6: EMM386: Unable to Start"
permalink: /kb/097/Q97016/
---

## Q97016: Windows Err Msg with MS-DOS 6: EMM386: Unable to Start

{% raw %}

	Article: Q97016
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:6.0,6.2,6.21,6.22; WINDOWS:3.0,3.0a,3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 16-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 6.0, 6.2, 6.21, 6.22 
	- Microsoft Windows versions 3.0, 3.0a, 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If you start Microsoft Windows in 386 enhanced mode after you upgrade to MS-
	DOS, you may receive the following error message:
	
	  EMM386: Unable to start enhanced mode Windows due to invalid path
	  specification for EMM386
	
	CAUSE
	=====
	
	This error can be caused by the following:
	
	- A possible incompatibility between Windows, EMM386.EXE version 4.45, and
	  VSafe.
	
	  For more information, type "help vsafe" (without the quotation marks) at the
	  MS-DOS command prompt, press ENTER, and then choose Note.
	
	- The presence of MS-DOS CHKLIST.MS (or older Central Point CHKLIST.CPS) check
	  list files in your Windows or MS-DOS directory.
	
	- With MS-DOS 6.2 Upgrade, running Microsoft Anti-Virus (MSAV) before running
	  MS-DOS 6.2 Step-Up installation, and loading the MS-DOS VSafe program.
	
	WORKAROUND
	==========
	
	If you are running the MS-DOS version of VSafe (not Central Point VSafe or PC
	Tools Vdefend), you should first add the /Y parameter (along with the path to
	EMM386.EXE) to the DEVICE command for EMM386.EXE in your CONFIG.SYS file. For
	example, add the following:
	
	     device=c:\dos\emm386.exe noems /y=c:\dos\emm386.exe
	
	If you are running MS-DOS 6.0, work around this problem as follows:
	
	- Unload VSafe by typing "vsafe /u" (without the quotation marks) at the MS-DOS
	  command prompt, or change the command for VSafe in your AUTOEXEC.BAT file so
	  that it has the path to the DOS directory (for example, C:\DOS\VSAFE.COM) and
	  then restart your computer.
	
	-or-
	
	- Delete the CHKLIST.MS files (and any CHKLIST.CPS files) from the Windows or
	  \DOS directories.
	
	-or-
	
	- Use the Windows version of EMM386.EXE.
	
	If the problem occurred when you upgraded to MS-DOS 6.2, try the following:
	
	- Run MSAV again after upgrading.
	
	-or-
	
	- Delete the CHKLIST.MS file from your Windows or MS-DOS directory.
	
	-or-
	
	- Unload Vsafe before running Windows.
	
	Additional query words: 6.22 6.00 6 nav norton nortons norton's anti virus anti-virus nav& sys nav&.sys stepup
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin300 kbWin300a kbWin310 kbWin311 kbMSDOSSearch kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600
	Version           : MS-DOS:6.0,6.2,6.21,6.22; WINDOWS:3.0,3.0a,3.1,3.11
	
	=============================================================================
	

{% endraw %}
