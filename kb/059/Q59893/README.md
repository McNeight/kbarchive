---
layout: page
title: "Q59893: Multithreaded Run-Time Libraries Require 40 File Handles"
permalink: /kb/059/Q59893/
---

## Q59893: Multithreaded Run-Time Libraries Require 40 File Handles

{% raw %}

	Article: Q59893
	Product(s): See article
	Version(s): 5.10 6.00
	Operating System(s): OS/2
	Keyword(s): ENDUSER | | mspl13_c
	Last Modified: 17-JUL-1990
	
	If you are creating an application that uses the multithreaded version
	of the run-time library (LLIBCMT.LIB or CRTLIB.DLL), it is not
	possible to set the file-handle count lower than 40. This is by design
	and may change in a future release of the run-time library.
	
	The DosSetMaxFH() function allows an application to dynamically set
	the number of file handles a program requires. It takes one parameter
	(the number of handles) and returns success, or one of the following
	two errors:
	
	   ERROR_INVALID_PARAMETER
	   ERROR_NOT_ENOUGH_MEMORY
	
	However, there is a limitation in the function. It will not allow the
	program to reduce the number of file handles, only increase them.
	
	In the case of an application that is linked with CRTLIB.DLL or
	LLIBCMT.LIB, the library has already set the file-handle count to 40.
	In this case, a call to DosSetMaxFH() with a number less than 40
	returns an ERROR_INVALID_PARAMETER value.

{% endraw %}
