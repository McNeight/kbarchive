---
layout: page
title: "Q51833: QuickC Environment Does Not Control Output Scrolling"
permalink: /kb/051/Q51833/
---

## Q51833: QuickC Environment Does Not Control Output Scrolling

{% raw %}

	Article: Q51833
	Product(s): See article
	Version(s): 1.00 1.01 2.00 2.01
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | S_QUICKASM | mspl13_c
	Last Modified: 17-JAN-1990
	
	QuickC Versions 1.00, 1.01, 2.00, and 2.01 does not scroll the output
	window when running a program in the environment. QuickC displays a
	frame-like fixed window on top of the DOS screen. If the DOS screen
	scrolls, the display will scroll through the output window. Likewise,
	if the DOS screen does not scroll, the display will not scroll through
	the output window.
	
	To illustrate QuickC's behavior with the output window, follow the
	steps below:
	
	1. Write a program to print numbers 1-100 on the screen and then
	   compile the sample program to generate a SAMPLE.EXE file. For
	   example:
	
	      use: printf("%d\n", num);  /* don't forget the "\n" */)
	
	2. From the DOS prompt clear the screen with "cls".
	
	3. Run your program and DOS will start to scroll the screen when the
	   screen runs out of lines to display the output.
	
	4. Clear the screen once again as in Step 2.
	
	5. Invoke QuickC and open the output window (View.Window.Output with
	   full menus). Single step through the print loop and watch the
	   output window. It will behave exactly the same as the actual output
	   screen.

{% endraw %}
