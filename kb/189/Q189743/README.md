---
layout: page
title: "Q189743: INFO: Description of Setup.lst Sections"
permalink: /kb/189/Q189743/
---

## Q189743: INFO: Description of Setup.lst Sections

{% raw %}

	Article: Q189743
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): kbwizard kbAppSetup kbRegistry kbVBp kbVBp600 kbGrpDSVB kbDSupport
	Last Modified: 01-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Package and Deployment Wizard (PDW) uses the information located in the
	Setup.lst file to install applications. This file contains all relevant
	information for the application to be installed. This article describes the
	usage of each section in the Setup.lst file.
	
	MORE INFORMATION
	================
	
	The Setup.lst file is created when the PDW is used to package an application. It
	is typically located in the same directory as Setup.exe (the application used to
	start the installation).
	
	NOTE: The Setup.lst file is a text file that can be viewed and edited using any
	text editor. The information below is based on a simple Standard EXE that has
	been packaged using the Package and Deployment Wizard (PDW).
	
	The application installation process has two parts:
	
	- Setup.EXE - A bootstrap process that loads the files required to perform the
	  actual installation.
	
	- Setup1.EXE - This process does the actual installation of the application:
	  program files are copied to their destination, required registry entries are
	  made, shortcuts for the desktop are made, etc.
	
	Bootstrap
	---------
	
	The Bootstrap section contains initial information used by Setup.exe to install
	the application. Included with this is:
	
	- SetupTitle - The name that appears on the blue screen gradient when the PDW
	  launches the second part of setup, Setup1.exe.
	
	- SetupText - Text displayed to users by Setup.exe while it copies files
	  necessary for Setup1.exe to start, located in the [Bootstrap Files] section.
	
	- CabFile - The name of the file containing all files to be installed.
	
	- Spawn - The name of the second setup application to be run by Setup.exe,
	  usually Setup1.exe.
	
	- Uninstal - The name of the uninstall application.
	
	- TmpDir - Specifies the temporary directory used by Setup to install files.
	
	- Cabs - The total number of cab files in the application.
	
	Example of [Bootstrap] section:
	
	  [Bootstrap]
	  SetupTitle=Install
	  SetupText=Copying Files, please stand by.
	  CabFile=Hello.CAB
	  Spawn=setup1.exe
	  Uninstal=st6unst.exe
	  TmpDir=msftqws.pdw
	  Cabs=1
	
	Bootstrap Files
	---------------
	
	The Bootstrap Files section contains all the necessary files to run the second
	part of the installation, Setup1.exe. These files must be in place for any
	Microsoft Visual Basic application to work correctly. The files listed here, one
	line per file, have the following arguments:
	
	File#=Filename, Install Macro, Register, Shared, Date, Size, Version where each
	argument corresponds to:
	
	- File# - The number of the file being installed. These files are in numeric
	  order starting at 1.
	
	- Filename - The name of the file to install. This name corresponds to the file
	  located in the .CAB file.
	
	- Install Macro - The installation macro used by the Setup process. For
	  additional information, please refer the following article in the Microsoft
	  Knowledge Base:
	
	- Register - How the file is to be registered, if necessary. The following are
	  typical registration processes:
	
	   - None - The file does not need to be registered or cannot be registered by
	     the PDW.
	
	   - $(DLLSelfRegister) - Self-registering file containing DLLRegisterServer
	     and DLLUnregisterServer functions.
	
	   - $(EXESelfRegister) - Registers any ActiveX EXE that supports the
	     /RegServer and /UnRegServer functions.
	
	   - $(TLBRegister) - Registration for Type Libraries.
	
	   - filename.reg - Allows a custom .REG file to register the component.
	
	- Shared - Indicates if the file is a shared system file and will be registered
	  as such in the system registry.
	
	- Date - Last modified date.
	
	- Size - Last modified file size.
	
	- Version - Internal version number of the file.
	
	Example of [Bootstrap Files] section:
	
	  [Bootstrap Files]
	  File1=@VB6STKIT.DLL,$(WinSysPathSysFile),,,6/13/98 12:00:00
	  AM,103424,6.0.81.64
	  File2=@COMCAT.DLL,$(WinSysPathSysFile),$(DLLSelfRegister),,5/31/98
	  12:00:00 AM,22288,4.71.1460.1
	  File3=@STDOLE2.TLB,$(WinSysPathSysFile),$(TLBRegister),,6/11/98
	  4:07:22 PM,17920,2.30.4261.1
	  File4=@ASYCFILT.DLL,$(WinSysPathSysFile),,,6/11/98 4:07:22
	  PM,147728,2.30.4261.1
	  File5=@OLEPRO32.DLL,$(WinSysPathSysFile),$(DLLSelfRegister),,6/11/98
	  4:07:23 PM,164112,5.0.4261.1
	  File6=@OLEAUT32.DLL,$(WinSysPathSysFile),$(DLLSelfRegister),,6/11/98
	  4:07:24 PM,598288,2.30.4261.1
	  File7=@MSVBVM60.DLL,$(WinSysPathSysFile),$(DLLSelfRegister),,6/13/98
	  12:00:00 AM,1409024,6.0.81.64
	
	IconGroups
	----------
	
	In this example, there are two groups of icons to be created "Hello" and "Another
	Group." The IconGroups section dictates the name, location on the Start Menu,
	and whether the group is a common group or private group on NT machines. The
	IconGroups section also contains pointers to the "Hello" and "Another Group"
	sections. These sections instruct Setup1.exe what shortcuts to create including
	the application to run, title, and the Start In directory for the link. There
	will be a section name for each group of icons created.
	
	- Group0=Hello - Section name of Program Group to be created, entitled "Hello."
	
	- PrivateGroup0=True - Dictates whether the group is private or common group on
	  Microsoft Windows NT 4.0 and higher.
	
	- Parent0=$(Programs) - The position on the Start Menu where the group is to be
	  created. Groups can only be created on either the $(Start Menu) or
	  $(Programs) macro installation point.
	
	- Group1=Another Group - Section name of Program Group to be created, entitled
	  "Another Group."
	
	- PrivateGroup1=True - Dictates whether the group is private or common group on
	  Microsoft Windows NT 4.0 and higher.
	
	- Parent1=$(Start Menu) - The position on the Start Menu where the group is to
	  be created. Groups can only be created on either the $(Start Menu) or
	  $(Programs) macro installation point.
	
	Example of [IconGroups] and individual icon creation sections:
	
	  [IconGroups]
	  Group0=Hello
	  PrivateGroup0=True
	  Parent0=$(Programs)
	  Group1=Another Group
	  PrivateGroup1=True
	  Parent1=$(Start Menu)
	
	  [Hello]
	  Icon1="Hello.exe"
	  Title1=Hello
	  StartIn1=$(AppPath)
	
	  [Another Group]
	  Icon1="Another.exe"
	  Title1=Another Icon
	  StartIn1=$(AppPath)
	
	Setup
	-----
	
	The Setup section contains information on the application being installed:
	
	- Title=Hello - This allows for customization of the title shown on the blue
	  backdrop during the installation.
	
	- DefaultDir=$(ProgramFiles)\Hello - Where the default installation path is
	  set.
	
	- AppExe=Hello.exe - Main application being installed.
	
	- AppToUninstall=Hello.exe - Main application to be uninstalled.
	
	  NOTE: Another valid entry in this section is ForceUseDefDir=1, which would
	  instruct the setup program to not prompt the user to select or modify the
	  installation path. The path in the DefaultDir entry would be used to install
	  the application.
	
	Example of [Setup] section:
	
	  [Setup]
	  Title=Hello
	  DefaultDir=$(ProgramFiles)\Hello
	  AppExe=Hello.exe
	  AppToUninstall=Hello.exe
	
	Setup1 Files
	------------
	
	This section is identical to the [BootStrap Files] section in usage. The
	difference is that the files listed here are installed by the second portion of
	the installation, Setup1.vbp, and consist of the specific files necessary to run
	the application.
	
	Example of [Setup1 Files] section:
	
	  [Setup1 Files]
	  File1=@Hello.exe,$(AppPath),,,6/17/98 11:58:25 AM,16384,1.0.0.0
	  ; The following lines may be deleted in order to obtain extra
	  ; space for customizing this file on a full installation diskette.
	  ;
	  ; XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
	
	In the example above, most of the excess lines of X's have been removed to save
	space. In a true Setup.lst, the "X" lines pad the length of the Setup.lst file
	by about 5K. The extra length is used when the Package and Deployment Wizard
	determines which files will fit onto a diskette. After the installation package
	is prepared, the Setup.lst file can be customized by overwriting or deleting the
	X-padded lines. This assures that customizations will not make the setup files
	too large to fit onto the diskette.
	
	REFERENCES
	==========
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q189739 : Package And Deployment Wizard Installation Macros
	
	Additional query words:
	
	======================================================================
	Keywords          : kbwizard kbAppSetup kbRegistry kbVBp kbVBp600 kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVB600
	Version           : :6.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
