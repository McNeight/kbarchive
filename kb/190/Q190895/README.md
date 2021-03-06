---
layout: page
title: "Q190895: DirectX: Different File Versions Listed in Diagnostic Tools"
permalink: /kb/190/Q190895/
---

## Q190895: DirectX: Different File Versions Listed in Diagnostic Tools

{% raw %}

	Article: Q190895
	Product(s): Microsoft Home Games
	Version(s): WINDOWS:95
	Operating System(s): 
	Keyword(s): kbenv kbtool kbimu msgame
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- the operating system: Microsoft Windows 95 
	- the operating system: Microsoft Windows 98 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When you run the DirectX diagnostic tools (DirectX Diagnostic Tool and DirectX
	Information) included in DirectX, a different file version number (a version
	other than 4.06.00.0318) appears to be listed for some DirectX components.
	
	NOTE: If you run the DirectX Driver Tool (a component of DirectX 5.0 and 5.2)
	after you install DirectX 6.0 on your computer, the versions of both DirectInput
	and DirectSound are listed as DirectX 5 under DirectX Version Information as
	these components are not updated to DirectX 6.0.
	
	MORE INFORMATION
	================
	
	Not all DirectX files were updated in this release of DirectX, and some files
	were updated to a different version number. The DirectX files that were not
	updated in this release retain their prior version number.
	
	The version number of these files should be 4.05.00.0155 or 4.05.00.0165 for
	Windows 95 and 4.05.01.1998 for Windows 98.
	
	The following DirectX files were not updated in this release of DirectX:
	
	- Dinput.dll
	- Dinput.vxd
	- Djoyd.vxd
	- Dsound.dll
	- Dsound.vxd
	- Gcdef.dll
	- Gchand.dll
	- Joy.cpl
	- Msanalog.vxd
	
	The following DirectX files were updated to version 4.86.00.0318 in this release
	of DirectX:
	
	- Ddrawex.dll
	- Dxapi.sys
	
	For more information about how to solve problems related to DirectX, use the
	DirectX Home User Troubleshooter located at the following Microsoft Web site:
	
	  http://support.microsoft.com/support/directx/directx_7.0/tshooter/default.asp
	
	Additional query words: direct-x dxdiag dxinfo dxtool win95 win98
	
	======================================================================
	Keywords          : kbenv kbtool kbimu msgame 
	Technology        : kbOSWin98 kbOSWin95 kbOSWinSearch
	Version           : WINDOWS:95
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
