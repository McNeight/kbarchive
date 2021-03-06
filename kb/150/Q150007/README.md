---
layout: page
title: "Q150007: Failed FPNW Logon Attempt Maps to F:&#92;"
permalink: /kb/150/Q150007/
---

## Q150007: Failed FPNW Logon Attempt Maps to F:&#92;

{% raw %}

	Article: Q150007
	Product(s): Microsoft Windows NT
	Version(s): winnt:3.51,4.0
	Operating System(s): 
	Keyword(s): kbinterop
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.51, 4.0 
	- Microsoft File and Print Services for NetWare versions 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use the Login.exe file from Microsoft File and Print Services for
	NetWare (FPNW) version 3.51 and 4.0, and you fail in an attempt to log on to a
	Novell server, the failed attempt will root map the Novell server's login area
	to F:\. This becomes a problem if a Novell login script expects to be in and at
	a certain drive and directory prompt, such as F:\LOGIN.
	
	Normally, Novell NETX shell behavior is not to root map the login area, even in
	the case of logon failure. With a Novell NETX shell running on a DOS 6.x
	computer, Novell's Login.exe would normally, in the event of a logon failure,
	leave the user at the login area prompt, usually F:\LOGIN. You would then be
	able to change out of this directory to another directory, such as F:\PUBLIC.
	However, this is not how FPNW'S Login.exe file operates.
	
	CAUSE
	=====
	
	The cause of this problem is currently under investigation.
	
	RESOLUTION
	==========
	
	Ensure that all logon attempts using FPNW'S Login.exe program supply a valid
	user name and password to avoid a possible failure in the execution of the
	user's Novell logon script.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 4.0.
	
	
	A supported fix is now available, but has not been fully regression-tested and
	should be applied only to systems experiencing this specific problem. Unless you
	are severely impacted by this specific problem, Microsoft recommends that you
	wait for the next Service Pack that contains this fix. Contact Microsoft
	Technical Support for more information.
	
	
	
	Additional query words: netware redirector validation
	
	======================================================================
	Keywords          : kbinterop 
	Technology        : kbWinNTsearch kbWinNT351search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS351search kbServicesNetwareSearch kbFPNW351 kbFPNW400
	Version           : winnt:3.51,4.0
	
	=============================================================================
	

{% endraw %}
