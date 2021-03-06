---
layout: page
title: "Q138124: DHCPADMN.EXE Reports Incorrect Server Configuration"
permalink: /kb/138/Q138124/
---

## Q138124: DHCPADMN.EXE Reports Incorrect Server Configuration

{% raw %}

	Article: Q138124
	Product(s): Microsoft Windows NT
	Version(s): 3.5,3.51
	Operating System(s): 
	Keyword(s): 
	Last Modified: 21-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51 
	- Microsoft Windows NT Server versions 3.5, 3.51 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you install the DHCP Administrator Program (DHCPADMN.EXE) from the Windows NT
	Server 3.51 compact disc, using the SETUP.BAT file in \CLIENTS\SRVTOOLS\WINNT
	directory, you experience erratic results while administering remote DHCP
	servers. Results from selecting a valid DHCP Scope may be one or more of the
	following:
	
	- All configuration options are displayed.
	
	- No configuration options are displayed.
	
	- The correct configuration options are displayed.
	
	The display problems do not happen when your computer is connected to all remote
	DHCP servers, however, if the problem occurs with a particular remote server it
	is persistent and always occurs with that same server.
	
	Using DHCPADMN.EXE locally on the DHCP server displays the correct configuration.
	
	CAUSE
	=====
	
	The DHCPSAPI.DLL file located in the following subdirectories of the Windows NT
	Server 3.51 compact disc is corrupt:
	
	  \CLIENTS\SRVTOOLS\WINNT\I386 \CLIENTS\SRVTOOLS\WINNT\MIPS
	  \CLIENTS\SRVTOOLS\WINNT\ALPHA
	
	RESOLUTION
	==========
	
	To resolve this problem, install the fix mentioned below.
	
	To work around this problem, do one of the following:
	
	- From a computer of the same processor type that is running Windows NT 3.51
	  DHCP without this problem, copy the %SystemRoot%\SYSTEM32\DHCPSAPI.DLL file
	  to your SystemRoot%\SYSTEM32 directory. Make sure that this DHCPSAPI.DLL was
	  not installed using the SETUP.BAT file mentioned above.
	
	  -or-
	
	- Replace your corrupt DHCPSAPI.DLL with the uncorrupted file version on the
	  Windows NT Server 3.51 compact disc in the \I386, \MIPS, and \ALPHA
	  subdirectories:
	
	- Insert the Windows NT Server 3.51 compact disc into your CD-ROM drive.
	
	- In Windows NT File Manager, display the contents of one of the following
	  subdirectories that corresponds to the processor on your computer:
	
	  \I386
	  \MIPS
	  \ALPHA
	
	- Copy the DHCPSAPI.DL_ file to a temporary subdirectory on your hard drive.
	
	- Type the following command and press the Enter key:
	
	  expand dhcpsapi.dl_ dhcpsapi.dll
	
	- Replace the %SystemRoot%\SYSTEM32\DHCPSAPI.DLL file on the local workstation
	  with the DHCPSAPI.DLL you just expanded.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 3.51. This
	problem was corrected in Windows NT version 4.0.
	
	Additional query words: prodnt DHCPADMN DHCPADMIN ADMIN TOOLS parameter incorrect
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNT350search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search
	Version           : :3.5,3.51
	
	=============================================================================
	

{% endraw %}
