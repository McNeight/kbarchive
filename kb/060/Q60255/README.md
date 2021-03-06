---
layout: page
title: "Q60255: &#95;&#95;STDC&#95;&#95; Is Undefined If Microsoft Extensions Are Allowed"
permalink: /kb/060/Q60255/
---

## Q60255: &#95;&#95;STDC&#95;&#95; Is Undefined If Microsoft Extensions Are Allowed

{% raw %}

	Article: Q60255
	Product(s): See article
	Version(s): 2.50 2.51
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | s_quickasm s_c | mspl13_c
	Last Modified: 15-APR-1990
	
	The __STDC__ macro is defined if a C compiler is ANSI C-standard
	conforming, and is undefined in QuickC Versions 2.50 and 2.51 if
	Microsoft extensions are allowed (default). To allow the macro to be
	defined, go to Options.Make.Compiler Flags.C Language and check ANSI
	compatibility. If you are compiling from the command line, add the /Za
	switch.
	
	This macro may be used as in the following code fragment:
	
	Code Example
	------------
	
	#ifdef __STDC__
	  void foo_bar (void);
	#endif

{% endraw %}
