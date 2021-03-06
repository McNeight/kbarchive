---
layout: page
title: "Q216109: HOWTO: Troubleshoot MSDN Library Run-Time/Install/Uninstall"
permalink: /kb/216/Q216109/
---

## Q216109: HOWTO: Troubleshoot MSDN Library Run-Time/Install/Uninstall

{% raw %}

	Article: Q216109
	Product(s): Microsoft Developer Network
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): kbHTMLHelp kbMSDN kbVC600 kbGrpDSTools
	Last Modified: 11-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Developer Network (MSDN) 
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, version 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes steps to troubleshoot MSDN library run-time,
	installation, and uninstall problems.
	
	MORE INFORMATION
	================
	
	The following are some troubleshooting steps that may fix a number of MSDN
	library problems:
	
	1. Before installing the MSDN Library: Make sure there are no programs running
	  in the background such as antiviral software. It is also very important for
	  all MSDN Libraries to be closed during the installation of a new MSDN
	  Library. If not, changes made to HHCOLREG.DAT can be lost and the new MSDN
	  Library may not function. It is a good idea to also temporarily remove any
	  programs from the Windows Start menu, and then reboot.
	
	2. Rename the Hh.dat file: Exit the MSDN library and then rename the Hh.dat file
	  that resides in your Windows\Help directory. Launch the MSDN library. The
	  Hh.dat file is re-created every time you rename it and launch MSDN library.
	
	3. Examine the registry: Launch either Regedit.exe or Regedt32.exe and look for
	  the following key:
	
	  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\HTML Help Collections\Developer
	  Collections\0x0409\0x035efac10
	
	  The 0x035efac10 key is not unique; you will have a different value after
	  installation. Make sure that the Filename key has the path set to the proper
	  collections file. The collections file takes different file names depending
	  on the version of MSDN library; for example, Msdnvs98.col for MSDN 6.0,
	  Msdn830.col for MSDN October 1998, and Msdn900.col for MSDN January 1999.
	
	  If the path is not set properly, make the changes and launch MSDN library
	  again. Please make sure to exit from MSDN library before making changes to
	  the registry.
	
	  If you don't want to modify the keys, then rename the HTML Help Collections
	  key, reinstall the MSDN library, and follow the steps in item number 1. If
	  the installation is successful, new registry keys will be created.
	
	4. Test the MSDN library installation: The MSDN library is based on HTML Help,
	  which depends primarily on two files, Hh.exe and Hhctrl.ocx.
	
	  Open any MSDN file with the .chm extension in Internet Explorer; if the MSDN
	  file opens successfully, then Hhctrl.ocx is working properly.
	
	  Hh.exe can be tested by opening a command prompt and going to the
	  drive:\Program Files\Microsoft Visual Studio\MSDN98\98OCT\1033 directory.
	
	  For MSDN Oct 98, type the following:
	
	  "hh.exe msdn830.col" (without the quotation marks)
	
	  For MSDN 6.0, type:
	
	  "hh.exe msdnvs98.col" (without the quotation marks)
	
	  This should launch the MSDN library. The above path name to the 1033 directory
	  may vary depending on the MSDN library installation directory.
	
	  When you get errors involving HTML Help, manually uninstalling and updating
	  the HTML Help components should fix the problem.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q201420 HOWTO: Manually Uninstall and Update HTML Help
	
	5. Manually uninstall and then reinstall the MSDN Library.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q240350 HOWTO: Manually Uninstall the MSDN Library
	
	6. Reinstall the product within which MSDN is being used, such as Visual C++
	  6.0:
	
	  MSDN problems may also be caused by an unsuccessful installation of the
	  product being used in conjunction with the MSDN library. In such cases, it
	  may be possible to launch the MSDN library from the shortcut menu on the
	  desktop or from the Start menu on your task bar, but not from the product.
	
	  For example, if you are using Visual C++ 6.0, from the Tools menu, click
	  Options and click the Help System tab. Your Preferred Language and Preferred
	  Collections fields should not be empty. For example, the Preferred Language
	  could be English and Preferred Collections could be MSDN Library - January
	  1999 (12/2/98). If these fields are empty, the most likely cause is an
	  unsuccessful Visual C++ installation, and therefore you might try
	  reinstalling Visual C++ 6.0 and then the MSDN library.
	
	7. MSDN uses the HTML Help technology, which is dependent on Internet Explorer
	  technology. There could be situations where MSDN exhibits unexpected
	  behavior, due to problems with your Internet Explorer installation. There may
	  be situations where you need to uninstall and reinstall Internet Explorer.
	  Please see the REFERENCES section below for information on uninstalling and
	  reinstalling Internet Explorer.
	
	8. MSDN library Setup may freeze on Windows NT and Windows 95/98.
	
	  If MSDN library Setup.exe freezes, then perform a flat install. In a flat
	  install, copy the CD-ROM bits to the hard drive and then run Setup; for a
	  typical install, copying CD 1 bits will be sufficient. By specifying
	  "setup.exe /G filename" you can create a log file of the setup process.
	
	  If Setup continues to freeze, then restart the computer in VGA mode for
	  Windows NT and Safe Mode for Windows 95/98 and rerun Setup. This behavior
	  maybe due to the display device drivers or a damaged CD-ROM.
	
	9. If the keywords in the Index tab disappear, then you may want to copy just
	  the files with the .chi extension from the MSDN CD-ROM 1 to the hard drive
	  location where the MSDN library has been installed (or in other words,
	  overwrite the .chi files).
	
	10. Please note that "Favorites" will be lost if another version of MSDN library
	  is installed on a computer that already has the library installed. There is
	  no way to move the Favorites to newer installations.
	
	
	
	REFERENCES
	==========
	
	For additional information about uninstall errors, please see the following
	article in the Microsoft Knowledge Base:
	
	  Q198928 PRB: MSDN Library Error During Uninstall
	
	
	For additional information about Internet Explorer problems, please see the
	following articles in the Microsoft Knowledge Base:
	
	  Q156933 Windows 95 Files Replaced by Internet Explorer Setup
	
	  Q166322 Uninstalling Internet Explorer 4.0 Platform Preview 1.0
	
	  Q176667 "Installation Is Incomplete" Installing Internet Explorer 4.0
	
	  Q175610 How to Manually Uninstall Internet Explorer 4.0
	
	  Q174867 Errors Installing Internet Explorer
	
	Additional query words: MSDN INSTALL UNINSTALL ERRORS
	
	======================================================================
	Keywords          : kbHTMLHelp kbMSDN kbVC600 kbGrpDSTools 
	Technology        : kbVCsearch kbAudDeveloper kbMSDNSearch kbZNotKeyword2 kbVC600 kbVC32bitSearch
	Version           : :6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
