---
layout: page
title: "Q136019: FAQ: Visual SourceSafe Integration with Visual C++ 4.0"
permalink: /kb/136/Q136019/
---

## Q136019: FAQ: Visual SourceSafe Integration with Visual C++ 4.0

{% raw %}

	Article: Q136019
	Product(s): Microsoft SourceSafe
	Version(s): 4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbSSafe400 kbSSafe500 kbSSafe600 kbVC400kbfaq
	Last Modified: 18-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe for Windows, versions 4.0, 5.0, 6.0 
	- Microsoft Visual C++, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article covers some of the most frequently asked questions (FAQ) about
	Visual SourceSafe integration with Visual C++ version 4.0.
	
	MORE INFORMATION
	================
	
	1. Q. How should I set up Visual SourceSafe for a multiple-developer project
	  with Visual C++ version 4.0?
	
	  A. Please see the following article in the Microsoft Knowledge Base:
	
	  Q139358 INFO: Readme.wri: Section 1, Software Installation Information
	
	  This article includes a detailed discussion comparing Setup.exe, which
	  provides Server, Client, and Custom setups, with Netsetup.exe, which provides
	  a Network Client setup from an existing Server installation.
	
	2. Q. I have installed Visual C++ and Visual SourceSafe, but Visual SourceSafe
	  is still not available under the Source Control menu in the Tools menu. Why?
	
	  A. Verify registration settings found in the following article in the
	  Microsoft Knowledge Base:
	
	  Q139358 INFO: Readme.wri: Section 1, Software Installation Information
	
	
	3. Q. How do I add a Project Workspace to Source Code Control?
	
	  A. If you have installed a Source Code Control Provider, such as Visual
	  SourceSafe 4.0, the Tools Menu of the Developer Studio will offer a Source
	  Control menu choice. This choice will offer a number of other options,
	  including "Add to Source Control." You can use this option to place your
	  newly created or existing project workspace under source code control.
	
	4. Q. How do I open a Project Workspace that is under Source Code Control?
	
	  A. Once you have installed a Source Code Control Provider, a new button will
	  appear in the dialog box brought up by clicking Open Workspace on the File
	  menu. This lets you choose a project currently under source code control, and
	  open it just as you would open any project workspace stored on the disk.
	
	5. Q. How does Visual C++ 4.0 show whether a given file or project is under
	  source code control?
	
	  A. Please see the following article in the Microsoft Knowledge Base:
	
	  Q136020 INFO: Glyphs in Visual C++ with Source Code Control Enabled
	
	6. Q. I'm performing an operation to manage my project workspace, and the dialog
	  box that comes up has an Advanced button that is unavailable (dimmed). Why is
	  it always disabled?
	
	  A. The support within Microsoft Developer Studio is designed to support any
	  Source Code Control Provider that meets the required specification. The
	  specification is generic enough so that if the provider wants to provide
	  advanced features, it can through a standard interface. The Advanced button
	  is part of that standard interface. Visual SourceSafe will take advantage of
	  it where appropriate, and leave it disabled when it is not useful. Other
	  providers may or may not take advantage of this as well.
	
	7. Q. I have a project under Visual SourceSafe control. Why can't I make any
	  modifications to my files in this project now?
	
	  A. When anything is under Visual SourceSafe control, the files must be checked
	  out of Visual SourceSafe before they can be modified in Visual C++. You can
	  check files out either from within Visual C++, which is usually the preferred
	  route for Visual C++ projects, or you can check out files within the Visual
	  SourceSafe explorer.
	
	8. Q. I have renamed a file in the Visual SourceSafe Explorer. Why is the file
	  not renamed in Visual C++?
	
	  A. Visual SourceSafe does not have a way to tell Visual C++ to rename a file
	  in a given project. On the other hand, Visual C++, through the integration
	  component, can tell SourceSafe that a file has been renamed. Therefore, the
	  best way to rename a file is to do it within Visual C++. This will update the
	  Visual SourceSafe Explorer.
	
	9. Q. Where can I find additional information about Visual SourceSafe?
	
	  A. Please see the following article in the Microsoft Knowledge Base:
	
	  Q134369 Microsoft SourceSafe Frequently Asked Questions (FAQ)
	
	  This includes information on how to obtain further technical support as well
	  as technical information.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbSSafe400 kbSSafe500 kbSSafe600 kbVC400 kbfaq
	Technology        : kbVCsearch kbVC400 kbSSafeSearch kbAudDeveloper kbSSafe600 kbSSafe400 kbSSafe500
	Version           : :4.0,5.0,6.0
	
	=============================================================================
	

{% endraw %}
