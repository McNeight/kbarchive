---
layout: page
title: "Q116163: Baseball: Contents of TBLSHOOT.TXT File"
permalink: /kb/116/Q116163/
---

## Q116163: Baseball: Contents of TBLSHOOT.TXT File

{% raw %}

	Article: Q116163
	Product(s): Microsoft Home Multimedia Titles
	Version(s): 1994 edition
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Complete Baseball for Windows, version 1994 edition 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains the text of the Complete Baseball TBLSHOOT.TXT file. The
	TBLSHOOT.TXT file is located in the DAILY directory on the Complete Baseball CD,
	and contains troubleshooting information for using the Baseball Daily feature.
	
	=====================================================================
	                          TBLSHOOT.TXT
	=====================================================================
	
	==============================================
	MICROSOFT COMPLETE BASEBALL'S BASEBALL DAILY
	==============================================
	
	This file contains troubleshooting information about Baseball Daily
	not included in the User's Guide.
	
	To read this file on-screen, use the Page Down and Page Up keys.
	You can also print the file by opening this file in any Windows
	word processing program and choosing the Print command from
	the File menu.
	
	This file contains important information on the following topics:
	
	1) MODEM INITIALIZATION STRINGS
	
	2) SPECIFIC MODEM INFORMATION
	
	3) COPYING FROM BASEBALL DAILY
	
	4) CHANGING YOUR PHONE PREFIX
	
	5) DISPLAY PROBLEMS
	
	6) GENERAL PROBLEMS
	
	7) BILLING AND PRODUCT SUPPORT INFORMATION
	
	8) LATEST STATISTICS ROTATION SCHEDULE
	
	=================================================================
	1. MODEM INITIALIZATION STRINGS
	=================================================================
	
	Baseball Daily registration uses an initialization string when
	setting up your modem for Baseball Daily service. Most modems can
	accept the standard, Hayes-compatible, string that Baseball Daily
	provides for you automatically. However, some modems require a
	specific string that you must enter manually.
	
	When registering for Baseball Daily, first try using the Hayes-
	compatible string provided by Complete Baseball. If you experience
	connectivity problems, try the following:
	
	1. Return to the Complete Baseball Contents screen and click the
	  Daily button to begin the registration process again. Fill out
	  all the information as before until you reach the Modem Settings
	  dialog.
	
	2. In the Modem Settings dialog, click Other. In the edit field
	  under the Other radio button, enter the following:
	
	     AT&FQOV1EOX4SO=O
	
	3. When you're done, click OK and complete the remaining
	  registration information.
	
	If you continue to experience connectivity problems, call
	(800) 638-8730 for Baseball Daily on-line service product support.
	
	=================================================================
	2. SPECIFIC MODEM INFORMATION
	=================================================================
	
	For information regarding your particular modem, you can
	call the product support phone number listed in your modem's
	documentation.
	
	=================================================================
	3. COPYING FROM BASEBALL DAILY
	=================================================================
	
	To copy information from a Baseball Daily screen, press
	CTRL+C. The information on the active screen is copied to
	the Windows clipboard. You can now copy this information into
	any word processing or spreadsheet application by switching to
	that application and choosing the application's Copy command.
	
	=================================================================
	4. CHANGING YOUR PHONE PREFIX
	=================================================================
	
	If your phone uses a different prefix from the one Baseball Daily
	registration offers, you can set your own phone prefix in the
	[online] section of your MSSPORTS.INI file. To set your own
	phone prefix:
	
	1. Exit Complete Baseball and Baseball Daily if you are currently
	  viewing them.
	
	2. In your Windows directory, open your MSSPORTS.INI file.
	
	3. Under the [on-line] section, add the following:
	
	       PhonePrefix=<your phone prefix>
	
	4. Choose Save from the File menu.
	
	5. Run Complete Baseball and try downloading an issue of Baseball
	  Daily again.
	
	=================================================================
	5. DISPLAY PROBLEMS
	=================================================================
	
	---------------------------------------------
	8514/a AND SUPER VGA LARGE FONT VIDEO DRIVERS
	---------------------------------------------
	
	If you are using either the 8514/a or Super VGA, 256 color, Large
	Font driver and a 1024 x 768 resolution, some statistics in Baseball
	Daily may appear clipped or will overlap each other. Switching to
	the Small Font version of either driver will fix this problem.
	
	=================================================================
	6. GENERAL PROBLEMS
	=================================================================
	
	---------------------------
	CORRUPT BASEBALL DAILY FILE
	---------------------------
	
	If you receive the following error message while attempting to
	view a Baseball Daily file you've already downloaded, your
	Baseball Daily file may be corrupt:
	
	  "Multimedia Viewer:
	  This file is not a Viewer file and cannot be opened in this
	  application."
	
	To download another issue of the current day's Daily, first, in File
	Manager, switch to the \DAILY subdirectory of your \BASEBALL directory
	and delete the Baseball Daily file bearing the current day's date.
	For example, if today's date is 7\8\94, you would delete the file
	named 19940708.MVB. You can now download the current day's file again
	by choosing the Daily button on the Complete Baseball Contents screen.
	
	-----------------------
	VIEWING PREVIOUS ISSUES
	-----------------------
	
	To view a previous issue of Baseball Daily:
	
	1. Choose the Daily button on the Complete Baseball Contents screen.
	
	2. In the Microsoft Baseball Daily dialog box, choose the View Old
	  Issue button.
	
	3. In the File Name list box, select the name of the file that
	  corresponds with the date of the issue you want to view. For
	  example, if you want to view an issue from June 15, 1994, choose
	  the file named 19940615.MVB.
	
	=================================================================
	7. BILLING AND PRODUCT SUPPORT INFORMATION
	=================================================================
	
	For assistance with Baseball Daily billing questions, call
	(800) 806-6587. For problems with connectivity using Baseball
	Daily, call (800) 638-8730.
	
	=================================================================
	8. LATEST STATISTICS ROTATION SCHEDULE
	=================================================================
	
	Statistical information contained in the Latest Statistics
	section of Baseball Daily is rotated daily according to the
	following schedule:
	
	  Monday: AL and NL Team Pitching Statistics
	  Tuesday: AL Individual Batting Statistics
	  Wednesday: NL Individual Batting Statistics
	  Thursday: AL Individual Pitching Statistics
	  Friday: NL Individual Pitching Statistics
	  Saturday: AL Team Batting Statistics
	  Sunday: NL Team Batting Statistics
	
	Additional query words: kbhowto 1994 multi media multimedia multi-media modem online electronic on line on-line tshoot trouble shoot troubleshoot
	
	======================================================================
	Keywords          :  
	Technology        : kbHomeProdSearch kbGamesSearch kbBaseballSearch kbCompleteBaseballSearch kbCompleteBaseball1994
	Version           : :1994 edition
	
	=============================================================================
	

{% endraw %}
