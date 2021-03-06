---
layout: page
title: "Q156795: HOWTO: Using Sysdiff.exe with Unattended Setup and Windows NT 4."
permalink: /kb/156/Q156795/
---

## Q156795: HOWTO: Using Sysdiff.exe with Unattended Setup and Windows NT 4.

{% raw %}

	Article: Q156795
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbOPK kbSBKkbfaq
	Last Modified: 15-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	Sysdiff.exe is a Windows NT 4.0-only utility used to profile and install
	applications for Windows NT 4.0 systems. The utility has several modes that must
	be run to achieve a proper profile of the system for installation purposes.
	
	Sysdiff consists of a three step process:
	
	1. Step one is SNAP mode, which takes an initial snapshot of a fresh install of
	  Windows NT.
	
	2. Step two is DIFF mode, which is run after applications have been installed
	  and uses the image created with SNAP mode for comparison.
	
	3. Step three is INF mode, which is used to incorporate the installation of the
	  applications with unattended setup.
	
	Sysdiff.exe does not provide support for any registry values that are contained
	in any of the HKEY_USER hives. This includes items like the desktop, screen
	savers, and wallpaper. Also, Sysdiff.exe does not support any installable
	services or device drivers.
	
	MORE INFORMATION
	================
	
	The following instructions provide a working model that can be used in preparing
	your distribution server:
	
	1. Make a directory on the distribution server called I386.
	
	2. Copy the entire contents of the I386 directory from the Windows NT 4.0
	  compact disc to the I386 directory. Share the I386 directory as I386 on the
	  distribution server.
	
	3. Do a fresh installation of Windows NT 4.0 on another system. This system is
	  called the Master System.
	
	4. Create a directory (MKDIR C:\Images) on the Master System to hold the files
	  created by Sysdiff. It is not necessary to send the images to a network
	  drive. A local drive will increase the performance of Sysdiff.
	
	5. Once Windows NT is installed, Sysdiff can be run to get an initial snapshot
	  used for comparison. From an MS-DOS window run the following command:
	
	  sysdiff /snap c:\images\snap.img
	
	6. Next, install the applications that will be used.
	
	7. Once all applications are installed, the system is ready to run the next step
	  of Sysdiff, which is DIFF mode. DIFF mode will use Snap.img to determine what
	  the applications directory structure is and the registry entries to add, if
	  any. Use the following command:
	
	  sysdiff /diff c:\images\snap.img c:\images\diff.img
	
	  The most common issues with DIFF mode occur when Sysdiff is profiling the
	  registry and is unable to extract the information. Review the Registry window
	  to see where Sysdiff stopped. In most cases, the application cannot be
	  profiled and will have to be installed manually. Another area to watch is the
	  INI files section. In some cases, the files for some applications are not
	  placed in the image. Application INI files may have to be copied manually
	  once the installation of Windows NT is completed.
	
	
	8. Now that the difference file (Diff.img) has been created, the next step is to
	  incorporate the applications into the I386 directory on the distribution
	  server. The way to incorporate the applications is with INF mode. The
	  Diff.img file will be extracted and a special directory structure built for
	  unattended setup to use. Also, a special INF file is created to rebuild the
	  registry.
	
	  Map a drive letter to the distribution server's share of the I386 directory
	  that was created earlier:
	
	  net use z:\\server_name\i386
	
	  Now run the following command:
	
	  sysdiff /inf /m c:\images\diff.img z:\
	
	  /M is used to ensure the shortcuts are added to the Start menu.
	
	  NOTE: Sysdiff will create a directory called $OEM$ and it is very important
	  that this directory be under the I386 directory on the server. In this case,
	  the I386 directory is shared as a root so Z:\ is all that is needed. To
	  verify that $OEM$ is in the correct location, from the server, check that
	  $OEM$ is under the I386 directory. If, for some reason, the $OEM$ directory
	  is not written to I386, it can moved using File Manager.
	
	  The distribution server is now ready to install Windows NT 4.0 and the
	  applications. One additional item is to verify the directory length under
	  $OEM$. The first phase of the installation of Windows NT is MS-DOS based, and
	  MS-DOS cannot copy directories with path names longer than 64 characters.
	
	9. To turn on the installation of applications placed in the $OEM$ directory,
	  OEMPreInstall = Yes must be added to the [Unattended] section of the answer
	  file. Using OEMPreInstall = Yes may require additional entries in the answer
	  file.
	
	  For additional information, please see the following article in the Microsoft
	  Knowledge Base:
	
	  ARTICLE-ID: Q155197
	  TITLE : Unattended Setup Parameters for Unattend.txt File
	
	Definitions of directories created by Sysdiff using INF mode
	
	$OEM$\$$
	----------------------------------------------------------------------
	
	This directory contains the system files (either new files or replacements for
	retail files) that are copied to the various subdirectories when Windows NT is
	installed. The structure of this directory must match the structure of a
	standard Windows NT installation, where $OEM$\$$ matches %Windir%,
	$OEM$\$$\System32 matches %Windir%\System32, and so on.
	
	Each subdirectory should contain the files that need to be copied to the
	corresponding system directory on the target computer. This directory should
	also contain $$Rename.txt, which lists all files that need to be renamed, such
	as files in 8.3 format that must change to long file names.
	
	$OEM$\drive_letter
	------------------
	
	Each $OEM$\drive_letter directory contains a subdirectory structure that is
	copied during text mode setup to the root of a corresponding drive in the target
	computer. Files that need to be renamed should be listed in $$Rename.txt.
	
	Additional information on Windows NT 4.0 Deployment is available for free
	download from the following Microsoft Web site:
	
	  http://www.microsoft.com/ntworkstation/info/deployguide.htm
	
	The Sysdiff.exe utility can be found on the Windows NT 4.0 CD-ROM at <cd-rom
	drive>:\Support\Deptools\I386\Sysdiff.exe for the Intel platform.
	
	For additional information on troubleshooting Sysdiff.exe, see the following
	article in the Microsoft Knowledge Base:
	
	  ARTICLE-ID: Q157576
	  TITLE : How to Troubleshoot the Sysdiff Tool in Windows NT
	
	
	Additional query words: SBK OPK Unattended Setup
	
	======================================================================
	Keywords          : kbOPK kbSBK kbfaq
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : :4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
