---
layout: page
title: "Q221737: FIX: C0000005 Fatal Error With SET('RELATION') Function"
permalink: /kb/221/Q221737/
---

## Q221737: FIX: C0000005 Fatal Error With SET('RELATION') Function

{% raw %}

	Article: Q221737
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbservicepack kbDatabase kbvfp600 kbvfp600bug kbXBase KbDBFDBC kbVS600sp2 kbVS600SP1 kb
	Last Modified: 20-MAY-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When repeatedly calling the SET() function and passing the "RELATION" argument,
	you might see an error similar to the the following:
	
	  Fatal error: Exception code=C0000005
	  Called from - <procedure name and line number> {<path and
	  filename>}
	
	The error may also appear as follows under Windows NT:
	
	  An application error has occurred and an application error log is being
	  generated.
	  VFP6.exe
	  Exception: access violation (0xc0000005),Address 0x77f6489f
	
	It is possible that use of the SET() function with certain other arguments could
	also cause this behavior. These are SET('FIELDS'), SET('ORDER'), SET('INDEX'),
	SET('NOCPTRANS'), and SET('SKIP').
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	This bug was corrected in Visual Studio 6.0 Service Pack 3. For more information
	about Visual Studio service packs, please see the following articles in the
	Microsoft Knowledge Base:
	
	Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	Q194295 HOWTO: Tell That Visual Studio 6.0 Service Packs Are Installed
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Run the following code from a program (.PRG) file:
	
	  FOR i = 1 TO 100
	     @ 1,1 SAY i PICTURE '999'
	     DO Proc1
	  ENDFOR
	
	  RETURN
	
	  PROCEDURE Proc1
	
	     DELETE FILE a01.DBF
	     DELETE FILE a01.CDX
	     DELETE FILE a02.DBF
	     DELETE FILE a02.CDX
	
	     CREATE TABLE a01 (f1 c(10),f2 c(10),f3 c(10),f4 c(10))
	     INDEX ON f1+f2+f3+f4 TAG f1234
	
	     CREATE TABLE a02 (f1 c(10),f2 c(10),f3 c(10),f4 c(10))
	     INDEX ON f1+f2+f3+f4 TAG f1234
	
	     SELECT a02
	     SET RELATION TO ;
	        SUBS(f1,1,1)+SUBS(f2,2,2)+SUBS(f3,3,3)+SUBS(f4,4,4)+;
	        SUBS(f1,5,5)+SUBS(f2,6,6)+SUBS(f3,7,7)+SUBS(f4,8,8) ;
	        INTO a01
	
	     * With the following line uncommented no error occurs
	     * m.setrel = SPACE(1024)
	
	     m.setrel = SET('RELATION')
	
	     CLOSE DATA
	
	     RETURN
	  ENDPROC
	
	2. The error occurs.
	
	Allocating a buffer for the variable to which the value is stored will prevent
	the exception from occurring. You can remove the asterisk from the beginning of
	the line m.setrel = SPACE(1024) to demonstrate this.
	
	(c) Microsoft Corporation 1999, All Rights Reserved.
	Contributions by Jim Saunders, Microsoft Corporation
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbservicepack kbDatabase kbvfp600 kbvfp600bug kbXBase KbDBFDBC kbVS600sp2 kbVS600SP1 kbVS600sp3fix kbGrpDSFox 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
