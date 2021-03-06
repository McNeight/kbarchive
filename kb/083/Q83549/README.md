---
layout: page
title: "Q83549: Unable to Print to LPT1/LPT2 on Novell NetWare 3.11"
permalink: /kb/083/Q83549/
---

## Q83549: Unable to Print to LPT1/LPT2 on Novell NetWare 3.11

{% raw %}

	Article: Q83549
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.0,3.0a,3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 04-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.0, 3.0a, 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	Microsoft Windows operating system versions 3.0 and 3.1 may not be able to print
	to either LPT1 and LPT1.OS2 or LPT2 and LPT2.OS2 on a Novell network.
	
	CAUSE
	=====
	
	Novell has confirmed that when using Novell NetWare 3.11 in conjunction with
	NETx.COM on Intel 80286 microprocessor-based computers, LPT1 parallel port
	address 0378h may be overwritten with 03BCh. LPT2 and LPT3 default addresses may
	also be overwritten on INTEL 80386 and 80486 microprocessor-based computers with
	the same address (03BCh).
	
	NETx.COM changes the address in the BIOS that defines where to send data for LPT1
	from the default (0378h) to 03BCh. When programs are printed to the parallel
	port through MS-DOS, the BIOS sends the data to 03BCh and the boards never see
	the data through their default addresses.
	
	WORKAROUND
	==========
	
	Sending Data to LPT1
	--------------------
	
	For LPT1 to work properly, its default address must be restored. Two methods for
	restoring the LPT1 address are listed as follows:
	
	1. Program the following in C (using any standard C Compiler):
	
	        int far *pt;
	        pt=MK_FP (0,0x408);
	        *pt=0x378h;
	
	  Save the file as C:\FIXLPT1.COM and add the program to the AUTOEXEC.BAT file
	  after NETx.COM, but before the LOGIN program, as follows:
	
	        NETx.COM
	        FIXLPT1.COM
	        NET LOGIN
	
	  -or-
	
	2. Use Windows Notepad to create the following Debug script for LPT1:
	
	        E40:8
	        78 03
	        q 
	
	  (Press the ENTER key)
	
	  NOTE: Do NOT include the parenthetical statement in script.
	
	3. Save the file as C:\FIXLPT1.DEB and add the Debug script to the AUTOEXEC.BAT
	  file after NETx.COM, but before the LOGIN program as follows:
	
	        NETx.COM
	        DEBUG < FIXLPT1.DEB
	        NET LOGIN
	
	4. Save the AUTOEXEC.BAT file and restart the machine.
	
	These programs insert the value 0378h into the BIOS data area address
	0000:0408h.
	
	Sending Data to LPT2
	--------------------
	
	If data output should be sent to LPT2, use the value 040Ah in the C program (see
	step 1, above) by replacing
	
	       (0,0x408);
	
	  with:
	
	       (0,0x40A);
	
	In the Debug script (see step 2, above), change E40:8 to E40:A. The address
	default 0278h may also be used for either LPT1 or LPT2.
	
	REFERENCES
	==========
	
	For further information concerning problems printing to parallel ports over a
	Novell network, contact Novell Technical Support.
	
	The products included here are manufactured by vendors independent of Microsoft;
	we make no warranty, implied or otherwise, regarding these products' performance
	or reliability.
	
	Additional query words: 3.00 3.00a 3.10 5.00
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin300 kbWin300a kbWin310 kbWin311
	Version           : WINDOWS:3.0,3.0a,3.1,3.11
	
	=============================================================================
	

{% endraw %}
