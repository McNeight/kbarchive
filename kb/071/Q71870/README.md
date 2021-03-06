---
layout: page
title: "Q71870: Task Swapper in MS-DOS Shell"
permalink: /kb/071/Q71870/
---

## Q71870: Task Swapper in MS-DOS Shell

{% raw %}

	Article: Q71870
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:5.x,6.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Task Swapper is a new feature added to MS-DOS version 5.0. The Active Task List
	appears in MS-DOS Shell when you choose Task Swapper from the Options menu. Any
	programs you start after enabling Task Swapper will then appear in the Active
	Task List.
	
	MORE INFORMATION
	================
	
	Task Swapper (DOSSWAP.EXE) swaps files to a temporary directory when they are
	put on the Active Task List. When a particular task is selected, it is swapped
	from the temporary directory into memory. For this reason, you should not delete
	any files from the temporary directory until Task Swapper is disabled and you
	have exited Shell.
	
	When Task Swapper is activated, it automatically occupies approximately 35.4K of
	conventional memory, even if no tasks are added to the Active Task List.
	
	Up to 13 tasks can be added to the Active Task List at one time. If tasks are
	simply added to the list, Task Swapper will still use only approximately 35.4K
	of conventional memory. If the tasks are enabled first, there may be an
	additional small amount of memory (1 or 2K) added to that 35.4K.
	
	To add a task to the Active Task List without executing the task, do the
	following:
	
	1. Highlight the item to be added to the task list.
	
	2. Press SHIFT+ENTER, or hold down the SHIFT key and double-click the mouse.
	
	To enable a task then add it to the Active Task List, do the following:
	
	1. Highlight the item you want to add to the task list.
	
	2. Press ENTER, or double-click the mouse.
	
	3. After the task or program is loaded, press CTRL+ESC to return to Shell. An
	  icon will be displayed in the Active Task List.
	
	Tasks that can be enabled are program files ending with the extensions .EXE,
	.BAT, .SYS, and .COM.
	
	Additional query words: 5.00 5.00a 6.00 noupd
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS600 kbMSDOS500 kbMSDOS500a
	Version           : MS-DOS:5.x,6.0
	
	=============================================================================
	

{% endraw %}
