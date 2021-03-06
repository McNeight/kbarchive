---
layout: page
title: "Q308117: Games: Error Message: Ddraw.dll Cannot Start"
permalink: /kb/308/Q308117/
---

## Q308117: Games: Error Message: Ddraw.dll Cannot Start

{% raw %}

	Article: Q308117
	Product(s): Microsoft Home Games
	Version(s): 2.0
	Operating System(s): 
	Keyword(s): kbimu
	Last Modified: 07-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Midtown Madness 2, version 2.0 
	- Microsoft Flight Simulator 98 
	- Microsoft Golf 2001 Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to start any of the above programs, you may receive an error
	message similar to one of the following:
	
	  Ddraw.dll cannot start.
	
	-or-
	
	  Failed to open ddraw.dll.
	
	CAUSE
	=====
	
	This issue can occur if DirectX is corrupt, your video adapter does not meet the
	minimum requirements, or your monitor is set as unknown or default.
	
	RESOLUTION
	==========
	
	To resolve this issue, use one or more of the following methods.
	
	Method 1: Check the Amount of Video Memory
	------------------------------------------
	
	1. Click Start, and then click Run.
	
	2. In the Open box, type "C:\Program Files\DirectX\Setup\Dxdiag.exe" (without
	  the quotation marks), and then click OK.
	
	3. Click the Display (or Display 1, if present) tab.
	
	  If fewer than 4 megabytes (MB) of video memory are installed on your video
	  adapter, you need to install additional video memory or install a video
	  adapter with more memory.
	
	Method 2: Configure Midtown Madness to Use Software Rendering
	-------------------------------------------------------------
	
	To resolve this issue in Midtown Madness, follow these steps:
	
	1. Start Midtown Madness 2.
	
	2. In the Startup dialog box, click Options, and then click Graphics.
	
	3. In the Renderer dialog box, click "Software only (no 3D video card)", click
	  Done, and then click Back.
	
	Method 3: Check Your Monitor Setting
	------------------------------------
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click System, and then click the Device Manager tab.
	
	3. Click the plus sign next to Monitors.
	
	4. If there is more than one monitor listed, make sure that the selected monitor
	  is the same as the monitor that you are using.
	
	Method 4: Restart Your Computer by Using a Clean Boot and Reinstall DirectX
	---------------------------------------------------------------------------
	
	1. Click Start, and then click Run.
	
	2. In the Open box, type "msconfig" (without the quotation marks), and then
	  click OK.
	
	3. On the General tab, click "Selective startup", and then click to clear each
	  check box.
	
	  When you receive the confirmation message, click Yes.
	
	4. Restart your computer.
	
	5. See the following Microsoft Web site:
	
	  http://www.microsoft.com/directx/homeuser/downloads/default.asp
	
	6. On the Home User Downloads Web page, click the appropriate Web link to
	  download DirectX.
	
	7. In the File Download dialog box, click "Save this program to disk", click OK,
	  and then click Save.
	
	8. When the download process is finished, click Open, and then click Yes.
	
	9. Click Yes to accept the license agreement.
	
	NOTE: If you do not accept the license agreement, you will not be able to install
	DirectX. 10. When prompted, restart your computer.
	
	MORE INFORMATION
	================
	
	To download the latest version of DirectX, see the following Microsoft Web
	site:
	
	  http://www.microsoft.com/directx/homeuser/downloads/default.asp
	
	REFERENCES
	==========
	
	For additional information, click the article number below to view the article
	in the Microsoft Knowledge Base:
	
	  Q179113 How to Download and Install DirectX
	
	Additional query words: msgame
	
	======================================================================
	Keywords          : kbimu 
	Technology        : kbHomeProdSearch kbGamesSearch kbFlightSimSearch kbGolf2001 kbGolfSearch kbMidtownMadSearch kbFlightSim98 kbMidtownMadness2
	Version           : :2.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
