---
layout: page
title: "Q11274: Italics (and Other Fonts) on a Monochrome Monitor"
permalink: /kb/011/Q11274/
---

## Q11274: Italics (and Other Fonts) on a Monochrome Monitor

{% raw %}

	Article: Q11274
	Product(s): See article
	Version(s): 3.00 4.00 5.00 5.10 6.00 6.00a
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | s_quickc | mspl13_c
	Last Modified: 15-JAN-1991
	
	Question:
	
	On some Microsoft products (such as Microsoft Word), I have seen text
	represented in italics on a monochrome monitor without a graphics
	adapter. How can I get italics on the monitor using Microsoft C or
	Macro Assembler?
	
	Response:
	
	These products create the italics font internally, in graphics mode
	(regardless of whether or not you have a monochrome monitor or color
	monitor attached), then it is mapped into the BIOS graphics ASCII
	table and presented on the screen.
	
	To get italics on the screen, you must first create this graphics font
	(or purchase a library of fonts from a software vendor), then map the
	graphics font to the BIOS graphics font table.
	
	It is possible to incorporate many desired fonts into your application
	by writing your application to interface with Microsoft Windows.

{% endraw %}
