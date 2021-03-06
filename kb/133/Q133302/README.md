---
layout: page
title: "Q133302: FIX: Application Fails But Gives No Error Message"
permalink: /kb/133/Q133302/
---

## Q133302: FIX: Application Fails But Gives No Error Message

{% raw %}

	Article: Q133302
	Product(s): Microsoft C Compiler
	Version(s): winnt:2.0,2.1,2.2
	Operating System(s): 
	Keyword(s): kbcode kbMFC kbVC200bug kbVC210bug kbVC220bug kbVC400fix kbGrpDSMFCATL kbNoUpdate
	Last Modified: 07-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, versions 2.0, 2.1, 2.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A Windows-based application using the DLL version of the CRT (C run-time) causes
	a run-time error and exits without displaying any error message or notification.
	
	CAUSE
	=====
	
	There are two ways to notify a user of a run-time error -- one for Windows-
	based applications and one for console-based applications. A Windows-based
	application linked with the static CRT pops up a dialog box with the run-time
	error number. A console-based application outputs the error message to stderr.
	However a Windows-based application using the CRT DLL calls the console version,
	which outputs to stderr. Because stderr does nothing in a Windows-based
	application, the application terminates without giving a warning or
	notification.
	
	RESOLUTION
	==========
	
	Here are two workarounds for a Windows-based application using the CRT DLL:
	
	- Use the static CRT library version.
	
	  -or-
	
	- Use the sample code listed in the "More Information" section of this article.
	
	The initialization section of the sample code allocates a console window for the
	Windows-based application and redirects stderr. CreateProcess() must then be
	used so that the window will not terminate with a run-time error. If the
	application encounters a run-time error, the console window stays on the screen
	to display the run-time error message.
	
	The initialization part of the sample code should execute before any other global
	data initialization. Within a source file, the order of execution will be in the
	order the initializations appear in the file. In order to ensure that the
	initialization code is executed first, place the code within that compilation
	unit at the top of the file, after include files.
	
	The order of initialization of data in different compilation units cannot be
	guaranteed. If your application is still exiting without a message you can use
	the first workaround, or you can place all your global data in the same
	compilation unit, with the sample initialization code at the top of the file.
	
	The termination section of the sample code is used for the normal termination of
	the application. It ensures that the console window is destroyed when the
	application terminates. For MFC applications, place the termination code in the
	application object's ExitInstance() member function. In a non-MFC Windows-based
	application, place this code in the WM_DESTROY message hanlder.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This problem was corrected in Visual C++ 4.0
	
	REFERENCES
	==========
	
	Sample Code - Initialization Section
	------------------------------------
	
	  /* The following lines of code need to be placed in file scope, in
	     one source file, in your project. */ 
	
	  #include   <stdio.h>
	  #include   <wincon.h>
	
	  PROCESS_INFORMATION    pi;
	
	  int    InitConsoleWindow()
	  {
	     STARTUPINFO si = {0};            // Initialize all members to zero
	     si.cb = sizeof(STARTUPINFO);     // Set byte count
	
	     AllocConsole();                  // Allocate console window
	     freopen("CONOUT$", "a", stderr); // Redirect stderr to console
	
	     // Display user message in console window.
	     fprintf(stderr, "Application stderr output window\n");
	     fprintf(stderr, "DO NOT CLOSE THIS WINDOW, ");
	     fprintf(stderr, "it will terminate your application!\n");
	
	     return CreateProcess(NULL,// address of module name
	            "cmd.exe",         // address of command line
	            NULL,              // address of process security attributes
	            NULL,              // address of thread security attributes
	            TRUE,              // new process inherits handles
	            CREATE_SUSPENDED,  // creation flags
	            NULL,              // address of new environment block
	            NULL,              // address of current directory name
	            &si,               // address of STARTUPINFO
	            &pi);              // address of PROCESS_INFORMATION
	  }
	
	  int  nInit = InitConsoleWindow();
	
	Sample Code - Termination Section
	---------------------------------
	
	  /* The following two lines need to be placed in the normal termination
	     procedure for your application. */ 
	
	  TerminateProcess(pi.hProcess, 0);
	  CloseHandle(pi.hProcess);
	
	Additional query words: 2.00 2.10 2.20 3.00 3.50 3.51 4.00
	
	======================================================================
	Keywords          : kbcode kbMFC kbVC200bug kbVC210bug kbVC220bug kbVC400fix kbGrpDSMFCATL kbNoUpdate 
	Technology        : kbVCsearch kbAudDeveloper kbVC220 kbVC200 kbVC210
	Version           : winnt:2.0,2.1,2.2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
