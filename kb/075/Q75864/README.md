---
layout: page
title: "Q75864: Async VMM Services May Be Called by Interrupt Handlers"
permalink: /kb/075/Q75864/
---

## Q75864: Async VMM Services May Be Called by Interrupt Handlers

{% raw %}

	Article: Q75864
	Product(s): Microsoft Windows Device Driver Kit
	Version(s): 3.0,3.1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 30-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Device Development Kit (DDK) for Windows, versions 3.0, 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Enhanced Mode Windows Virtual Machine Manager (VMM) is a single- threaded,
	non-reentrant operating environment. Because VMM is non- reentrant, when a
	virtual device (VxD) is entered due to an asynchronous interrupt, the VxD can
	call only a limited set of VMM and VxD services.
	
	A service that can be called from a VxD interrupt handler must be declared using
	the "Async_Service" option for the BeginProc macro. An async service may only
	call other services which are also async services. If a service that is not
	declared as an async service is called when VMM has been reentered, the debug
	version of WIN386.ExE will output the following error message:
	
	  ERROR: Synchronous service called from a nested interrupt.
	
	MORE INFORMATION
	================
	
	The table below lists all async services which may be called by interrupt
	handlers in Enhanced Mode Windows 3.0 and 3.1. It also lists the page in the 3.1
	Device Driver Kit Virtual Device Adaptation Guide on which the service is
	documented.
	
	VDAG
	Page  3.0 3.1  Service Name           VMM Async Services
	====================================================================
	257   [+] [+]  Begin_Reentrant_Execution
	261   [+] [+]  Call_Global_Event
	262   [1] [+]  Call_Priority_VM_Event
	265   [+] [+]  Call_VM_Event
	272   [+] [+]  Cancel_Global_Event
	274   [+] [+]  Cancel_VM_Event
	276   [2] [+]  Close_VM
	282   [+] [+]  Crash_Cur_VM
	294   [+] [+]  End_Reentrant_Execution
	297   [+] [+]  Fatal_Error_Handler
	297   [+] [+]  Fatal_Memory_Error
	301   [+] [3]  Get_Crit_Section_Status
	302   [2] [+]  Get_Crit_Status_No_Block
	304   [+] [+]  Get_Cur_VM_Handle
	309   [+] [+]  Get_Execution_Focus
	313   [+] [+]  Get_Last_Updated_System_Time
	314   [+] [+]  Get_Last_Updated_VM_Exec_Time
	320   [+] [+]  Get_Next_VM_Handle
	330   [2] [+]  GetSetDetailedVMError
	335   [+] [+]  Get_System_Time
	335   [+] [+]  Get_Sys_VM_Handle
	336   [+] [+]  Get_Time_Slice_Info
	340   [+] [+]  Get_VM_Exec_Time
	340   [+] [+]  Get_VMM_Reenter_Count
	341   [+] [+]  Get_VMM_Version
	368   [+] [+]  List_Allocate
	369   [+] [+]  List_Attach
	370   [+] [+]  List_Attach_Tail
	372   [+] [+]  List_Deallocate
	373   [+] [+]  List_Get_First
	374   [+] [+]  List_Get_Next
	374   [+] [+]  List_Insert
	375   [+] [+]  List_Remove
	376   [+] [+]  List_Remove_First
	417   [+] [+]  Schedule_Global_Event
	418   [+] [+]  Schedule_VM_Event
	438   [+] [+]  Signal_Semaphore
	448   [+] [+]  Test_Cur_VM_Handle
	449   [+] [+]  Test_Debug_Installed
	452   [+] [+]  Test_Sys_VM_Handle
	454   [+] [+]  Update_System_Clock
	455   [+] [+]  Validate_VM_Handle
	
	VDAG
	Page  3.0 3.1  Service Name        VMM Debug Async Services
	====================================================================
	276   [2] [+]  Clear_Mono_Screen
	284   [+] [+]  Debug_Convert_Hex_Binary
	284   [+] [+]  Debug_Convert_Hex_Decimal
	285   [+] [+]  Debug_Test_Cur_VM
	285   [+] [+]  Debug_Test_Valid_Handle
	288   [2] [+]  Disable_Touch_1st_Meg
	290   [2] [+]  Enable_Touch_1st_Meg
	316   [2] [+]  Get_Mono_Chr
	317   [2] [+]  Get_Mono_Cur_Pos
	358   [+] [+]  In_Debug_Chr
	364   [2] [+]  Is_Debug_Chr
	377   [+] [+]  Log_Proc_Call
	391   [+] [+]  Out_Debug_Chr
	391   [+] [+]  Out_Debug_String
	393   [2] [+]  Out_Mono_Chr
	394   [2] [+]  Out_Mono_String
	411   [+] [+]  Queue_Debug_String
	427   [2] [+]  Set_Mono_Cur_Pos
	451   [+] [+]  Test_Reenter
	454   [+] [+]  Validate_Client_Ptr
	
	VDAG
	Page  3.0 3.1  Service Name           VxD Async Services
	====================================================================
	40   [2] [+]  BlockDev_Command_Complete
	43   [2] [+]  BlockDev_Send_Command
	138   [+] [+]  DOSMGR_Get_DOS_Crit_Status
	147   [2] [+]  PageFile_Read_Or_Write
	154   [+] [+]  VPICD_Call_When_Hw_Int
	155   [+] [+]  VPICD_Clear_Int_Request
	155   [+] [+]  VPICD_Convert_Handle_To_IRQ
	156   [+] [+]  VPICD_Convert_Int_To_IRQ
	157   [+] [+]  VPICD_Convert_IRQ_To_Int
	157   [+] [+]  VPICD_Force_Default_Behavior
	158   [+] [+]  VPICD_Force_Default_Owner
	159   [+] [+]  VPICD_Get_Complete_Status
	160   [+] [+]  VPICD_Get_IRQ_Complete_Status
	161   [+] [+]  VPICD_Get_Status
	162   [+] [+]  VPICD_Phys_EOI
	163   [+] [+]  VPICD_Physically_Mask
	163   [+] [+]  VPICD_Physically_Unmask
	164   [+] [+]  VPICD_Set_Auto_Masking
	164   [+] [+]  VPICD_Set_Int_Request
	165   [+] [+]  VPICD_Test_Phys_Request
	192   [+] [+]  VTD_Update_System_Clock
	
	1. Call_Priority_VM_Event causes an erroneous error message and breakpoint on
	  the 3.0 debug version of WIN386.EXE when called asynchronously. This message
	  can be ignored and will not occur in the retail version of WIN386.EXE.
	
	2. These services are new in Windows 3.1 and not present in Windows 3.0.
	
	3. Get_Crit_Section_Status is an async service in Windows 3.0 but not in Windows
	  3.1. Get_Crit_Status_No_Block should be used instead in Windows 3.1.
	
	Additional query words: 3.00 3.10
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbWin3xSearch kbWinDDKSearch kbWinDDK300 kbWinDDK310
	Version           : :3.0,3.1
	
	=============================================================================
	

{% endraw %}
