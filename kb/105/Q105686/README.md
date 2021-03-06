---
layout: page
title: "Q105686: Deleting Windows 3.1 After Installing Windows NT"
permalink: /kb/105/Q105686/
---

## Q105686: Deleting Windows 3.1 After Installing Windows NT

{% raw %}

	Article: Q105686
	Product(s): Microsoft Windows NT
	Version(s): 3.1
	Operating System(s): 
	Keyword(s): kbsetup
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 3.1 
	- Microsoft Windows NT Workstation version 3.1 
	- Microsoft Windows NT Advanced Server, version 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	If you install Windows NT 3.1 or Windows NT 3.1 Advanced Server over Windows 3.1
	or Windows for Workgroups 3.1, the Windows NT files are installed to a
	subdirectory under the existing WINDOWS directory called SYSTEM32.
	
	NOTE: The original Microsoft Windows directory may be called WIN31 or any number
	of other names because it is user-configurable, but for the purposes of this
	article, WINDOWS is the assumed name of the directory.
	
	Some files from the original Windows 3.1 installation are used by the Windows NT
	operating system, however, and should not be deleted. This article describes how
	to remove the original Windows installation without affecting Windows NT, to
	help maximize your available disk space.
	
	MORE INFORMATION
	================
	
	WARNING: This information applies only to Window NT 3.1. If you remove the files
	indicated in this article from your computer running a later version of Windows
	NT, for example, Windows NT 3.5 or 3.51, Windows NT stops functioning properly.
	
	Windows NT 3.1 and Windows NT 3.1 Advanced Server use the existing fonts
	installed in the SYSTEM subdirectory, so you should not remove any of the .FOT,
	.TTF, or .FON files from the existing SYSTEM subdirectory.
	
	In addition, many Microsoft and third-party manufacturer' applications store
	various .DLL files in the WINDOWS directory and the SYSTEM subdirectory. Windows
	NT does not require these files, but the individual application that initially
	installed them may require them to operate properly.
	
	If you have stored any data files (such as with Notepad or Paintbrush) in the
	WINDOWS directory, these files should be backed up or copied to a different
	location. It is also a good idea to have backup copies of all .INI and .GRP
	files in the WINDOWS directory, because new users will not be able to migrate
	Windows 3.1 settings without these files. Once all these files have been backed
	up or copied, the remainder of the files in the WINDOWS directory can be safely
	removed without affecting the base Windows NT installation.
	
	Important: If you delete files required by a Windows application, you might have
	to reinstall that application in order for it to work properly. The safest way
	to do this is to keep backup copies of the files.
	
	Additional query words: wfw wfwg prodnt TrueType disappear uninstall
	
	======================================================================
	Keywords          : kbsetup 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW310 kbWinNTSsearch kbWinNTS310 kbWinNTAdvSerSearch kbWinNTAdvServ310 kbWinNTS310search kbWinNT310Search kbWinNTW310Search
	Version           : 3.1
	
	=============================================================================
	

{% endraw %}
