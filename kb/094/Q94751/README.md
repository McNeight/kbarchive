---
layout: page
title: "Q94751: FIX: ORG Behavior Different with Span-Dependent Value"
permalink: /kb/094/Q94751/
---

## Q94751: FIX: ORG Behavior Different with Span-Dependent Value

{% raw %}

	Article: Q94751
	Product(s): Microsoft Macro Assembler
	Version(s): MS-DOS:6.0,6.0a,6.0b
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Macro Assembler (MASM), versions 6.0, 6.0a, 6.0b 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In Microsoft Macro Assembler (MASM) versions 6.0, 6.0a, and 6.0b, if the offset
	for an ORG directive depends on the difference between two labels (a
	span-dependent value), the assembled code differs from that produces by previous
	versions of MASM.
	
	CAUSE
	=====
	
	The offset for the ORG directive depends on label values that are not yet
	determined in the first assembly pass.
	
	RESOLUTION
	==========
	
	Modify the code to remove span-dependent values in an ORG directive in code
	assembled with MASM versions 6.0, 6.0a, or 6.0b.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in MASM version 6.0, 6.0a, and 6.0b
	for MS-DOS and OS/2. This problem was corrected in MASM version 6.1 for MS-DOS.
	
	MORE INFORMATION
	================
	
	This problem usually occurs when a forward reference occurs between the two
	labels. The assembler adds padding bytes for the forward reference and
	eliminates these bytes during a subsequent assembly pass. When this occurs, the
	second label has a larger value during the first assembly pass than it does in
	subsequent passes.
	
	The sample code below demonstrates this behavior.
	
	Sample Code
	-----------
	
	  ; Assemble options needed: none
	
	  tst1 SEGMENT para public
	  ASSUME cs:tst1
	  start:
	       jmp SHORT forward
	  forward:
	       mov ax, 4C00h
	       int 21h
	  tst1 ENDS
	
	  count = offset forward - offset start
	
	  tst2 SEGMENT para public
	       DB 1
	       ORG count  ; This assembles as ORG 10 in MASM versions 6.0, 6.0a, and
	                  ; 6.0b. It assembles as ORG 2 in MASM versions 5.1 and 6.1.
	  xxx  DB 1
	  tst2 ENDS
	
	  END start
	
	Additional query words: 6.00 6.00a 6.00b buglist6.00 buglist6.00a buglist6.00b fixlist6.10
	
	======================================================================
	Keywords          :  
	Technology        : kbMASMsearch kbAudDeveloper kbMASM600 kbMASM600a kbMASM600b
	Version           : MS-DOS:6.0,6.0a,6.0b
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
