---
layout: page
title: "Q167364: Automating AUTOADMINLOGON Locally When Joining a Domain"
permalink: /kb/167/Q167364/
---

## Q167364: Automating AUTOADMINLOGON Locally When Joining a Domain

{% raw %}

	Article: Q167364
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): kbsetup
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	By default, when automating the installation of Windows NT Server or Workstation
	4.0 and the system is joining a domain, the Default Domain Name set in the
	registry is the domain that owns the machine account.
	
	HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT
	\Current Version\Winlogon
	
	  DefaultDomainName: REG_SZ <Domain Name>
	
	In many cases, Automatic Administrator Logon is enabled during setup so
	additional applications and settings can be configured. In most cases, a domain
	account and password are used for the domain that owns the machine account. By
	default, there is no way to log on to the local computer if the computer is
	joining a domain.
	
	MORE INFORMATION
	================
	
	By using Cmdlines.txt and a few other supplied applications with Windows NT 4.0,
	it is possible to build an Autolog.reg script that can be imported into the
	registry for Automatic Administrator Logon to the local machine account rather
	than the domain.
	
	The following required files ship with Windows NT and are part of the normal
	Windows NT installation:
	
	  Findstr.exe
	  Qbasic.exe
	  Regedit.exe
	
	How the Process Works
	---------------------
	
	During an unattended or automated installation of Windows NT 4.0, the
	Unattend.txt answer file will contain the computer name used during the
	installation. The answer file is parsed at the beginning of setup and additional
	setup information is appended to a new file and saved as $WinNT$.inf in the
	%systemroot%\system32 directory.
	
	Through the use of Findstr.exe, the line containing the computer name can be
	exported to a single line text file. Through the use of a simple Microsoft
	QuickBasic program, the text file is read and manipulated to get the actual
	computer name and writes a REGEDIT4 compatible registry file.
	
	After the registry file is written, it can be imported into the Windows NT
	registry using Regedit.exe.
	
	To take advantage of the local logon option during the Windows NT automated
	installation process, the following information must be configured.
	
	1. You will need an Unattend.txt file that is configured to install Windows NT
	  4.0.
	
	2. The option OEMPreInstall = Yes must be added to the [unattended] section in
	  the answer file.
	
	3. Create an I386 directory on a server and copy the files from the I386
	  directory of the Windows NT 4.0 compact disc to the I386 directory on the
	  server.
	
	4. Under the I386 directory on the server, create a directory called $OEM$.
	
	5. Paste the following lines of code into a text editor and save as Autolog.bas
	  to the $OEM$ directory.
	
	  Note: Some Lines are wrapped for formatting purposes of the article.
	
	        OPEN "AUTOLOG.TXT" FOR INPUT AS #1
	        INPUT #1, a$
	        b$ = MID$(a$, 17)
	        c$ = MID$(b$, 1, (LEN(b$) - 1))
	        CLOSE #1
	        OPEN "AUTOLOG.REG" FOR OUTPUT AS #1
	        PRINT #1, "REGEDIT4"
	        PRINT #1, ""
	        PRINT #1, "[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
	        NT\CurrentVersion\Winlogon]"
	        PRINT #1, CHR$(34) + "DefaultUserName" + CHR$(34) + "=" + CHR$(34) +
	        "Administrator" + CHR$(34)
	        PRINT #1, CHR$(34) + "AutoAdminLogon" + CHR$(34) + "=" + CHR$(34) +
	        "1" + CHR$(34)
	        PRINT #1, CHR$(34) + "DefaultPassword" + CHR$(34) + "=" + CHR$(34) +
	        CHR$(34)
	        PRINT #1, CHR$(34) + "DefaultDomainName" + CHR$(34) + "=" + CHR$(34)
	        + c$ + CHR$(34)
	        CLOSE #1
	        END
	
	6. Using a text editor create or modify the Cmdlines.txt file to add:
	  ".\AUTOLOG.CMD" line under [commands] and save it to the $OEM$ directory.
	
	  To save time you can copy the following two lines of information to create the
	  required Cmdlines.txt.
	
	     [commands]
	     ".\AUTOLOG.CMD"
	
	  If you have an existing Cmdlines.txt do not copy the [Commands] line since an
	  existing Cmdlines.txt file already has this line.
	
	7. A batch job called Autolog.cmd needs to be created and placed in the $OEM$
	  directory.
	
	  The following commands make up the Autolog.cmd batch job.
	
	  @echo off
	  CLS
	  findstr.exe /C:ComputerName %systemroot%\system32\$winnt$.inf >
	  autolog.txt
	  START QBASIC.EXE /RUN .\AUTOLOG.BAS
	  :TOP
	  IF NOT EXIST AUTOLOG.REG GOTO TOP
	  START /WAIT REGEDIT.EXE /S .\AUTOLOG.REG
	
	  NOTE: The third and fourth lines in the Autolog.cmd listed above should be
	  entered as one line. They are wrapped here for readability.
	
	  Findstr.exe is case sensitive; therefore, the entry in the Unattend.txt file
	  for CompterName must match what FINDSTR is looking for.
	
	  It is important not to modify any of the command lines by adding or deleting
	  the START or START /WAIT options. The sequences used are to ensure events
	  happen in a specific order and time.
	
	  The Findstr.exe command parses out the line ComputerName to a text file into
	  the $OEM$ directory during setup. This is done to keep the Microsoft
	  QuickBasic program as simple as possible.
	
	  The Autolog.bas program opens Autolog.txt and parses out the actual computer
	  name for the computer and writes a registry-compatible script to enable the
	  Automatic Administrator Logon.
	
	  The IF NOT EXIST line basically tests for the Autolog.reg file presence before
	  importing. After the file is written and the Autolog.bas finishes,
	  Regedit.exe will run and import the registry script.
	
	8. During GUI mode setup, an MS-DOS command window will appear that is normally
	  not on the screen during setup. This is by design and will terminate normally
	  at the end of setup.
	
	9. Verify that the Shlwapi.dll file is located in the I386\$oem$ directory.
	
	The example given is provided as a working example and does not require any
	additional software outside of the components supplied with Windows NT
	Workstation 4.0 or Server 4.0. The process could be enhanced through the use of
	C++ or Visual Basic to build a standalone utility, if desired.
	
	For additional information on the Windows NT 4.0 Power Toys, consult the
	Microsoft Windows NT Server Resource Kit Version 4.0, Supplement One online
	documentation.
	
	You can also download the Windows NT 4.0 Deployment Guide from:
	
	  http://www.microsoft.com/ntworkstation.
	
	Note that the deployment guide is valid for both Windows NT Workstation and
	Windows NT Server.
	
	Additional query words: prodnt
	======================================================================
	Keywords          : kbsetup 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : WinNT:4.0
	Hardware          : x86
	
	=============================================================================
	

{% endraw %}
