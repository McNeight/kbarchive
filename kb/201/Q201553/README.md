---
layout: page
title: "Q201553: HOWTO: Disable the Window Close Button in an MDI Application"
permalink: /kb/201/Q201553/
---

## Q201553: HOWTO: Disable the Window Close Button in an MDI Application

{% raw %}

	Article: Q201553
	Product(s): Microsoft C Compiler
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): kbMDI kbMenu kbMFC KbUIDesign kbVC600 kbGrpDSMFCATL
	Last Modified: 12-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), included with:
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	   - Microsoft Visual C++.NET (2002) 
	-------------------------------------------------------------------------------
	
	NOTE: Microsoft Visual C++ NET (2002) supported both the managed code model that is provided by the .NET Framework and the unmanaged native Windows code model. The information in this article applies to unmanaged Visual C++ code only.
	
	SUMMARY
	=======
	
	This article describes how to disable the close button in the title bar of the
	main frame and child frame windows of an MFC Multiple Document Interface (MDI)
	application.
	
	MORE INFORMATION
	================
	
	In some circumstances you may want to prevent the user from clicking the close
	button in the window's title bar to close a frame window in an MFC application.
	The close button can be removed by removing the WS_SYSMENU style from the frame
	window. However, the minimize, maximize, and restore buttons are also removed
	and cannot be added. This is in accordance to the design of Windows.
	
	To workaround this limitation, you can simulate the functionality of a window
	without a close button by disabling the close button. In the WM_CREATE message
	handler for the MDI child frame window (CMDIChildWnd-derived class) disable the
	close button with the following code:
	
	  CMenu *pSysMenu = GetSystemMenu(FALSE);
	  ASSERT(pSysMenu != NULL);
	  VERIFY(pSysMenu->RemoveMenu(SC_CLOSE, MF_BYCOMMAND));
	
	When the child frame window is not maximized, the above code prevents the user
	from closing the child frame window by clicking the close button. When the child
	frame window is maximized, the above code makes the close button appear
	disabled. However, a user can still close the child frame window by clicking
	this window's close button. You can prevent this by trapping the SC_CLOSE
	command when it is sent to the child frame window and preventing further
	processing of this command. To do so, use the WM_SYSCOMMAND message handler for
	the child frame's class, as in the following example:
	
	  // CChildFrame is a CMDIChildWnd-derived class.
	  void CChildFrame::OnSysCommand(UINT nID, LPARAM lParam)
	  {
	      if(nID == SC_CLOSE)
	          return;
	      CMDIChildWnd::OnSysCommand(nID, lParam);
	  }
	
	(c) Microsoft Corporation 1999, All Rights Reserved. Contributions by Isaac L.
	Varon, Microsoft Corporation.
	
	
	Additional query words: ChildFrame MainFrame
	
	======================================================================
	Keywords          : kbMDI kbMenu kbMFC KbUIDesign kbVC600 kbGrpDSMFCATL 
	Technology        : kbAudDeveloper kbMFC
	Version           : :6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
