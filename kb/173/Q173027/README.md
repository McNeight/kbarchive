---
layout: page
title: "Q173027: FIX: CRichEditView as Second Splitter Pane Causes Crash"
permalink: /kb/173/Q173027/
---

## Q173027: FIX: CRichEditView as Second Splitter Pane Causes Crash

{% raw %}

	Article: Q173027
	Product(s): Microsoft C Compiler
	Version(s): winnt:4.0,4.0a,4.1
	Operating System(s): 
	Keyword(s): kbDocView kbMFC kbVC400bug kbVC410bug kbVC420fix kbGrpDSMFCATL
	Last Modified: 17-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++, 32-bit Editions, versions 4.0, 4.0a, 4.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If an MFC program uses a CRichEditDoc and a CRichEditView is not the first pane
	of a splitter window, an access violation occurs when you start the program.
	
	CAUSE
	=====
	
	MFC's CRichEditDoc::GetView always assumes the first view of the active frame
	window is a CRichEditView. The pointer is returned and used as a CRichEditView
	object even though it may not be. The crash occurs when you use a data member or
	function specific to CRichEditView.
	
	RESOLUTION
	==========
	
	Since GetView is not virtual, it cannot be overriden. When using Visual C++ 4.0
	or 4.1, make sure that the first pane is a CRichEditView.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug has been corrected in the Microsoft
	Foundation Classes version 4.2 and shipped with Visual C++ version 4.2.
	
	MORE INFORMATION
	================
	
	When a CRichEditView is specified during the creation of an MFC program using
	AppWizard, a CRichEditDoc derived class is created for the program. When the
	rich edit view is initially displayed, the framework calls
	CRichEditDoc::SetTitle to update the frame window's title. However, SetTitle
	calls GetView, which returns the first view in the view list.
	
	(c) Microsoft Corporation 1997, All Rights Reserved. Contributions by Adam Kim,
	Microsoft Corporation
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDocView kbMFC kbVC400bug kbVC410bug kbVC420fix kbGrpDSMFCATL 
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:4.0,4.0a,4.1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
