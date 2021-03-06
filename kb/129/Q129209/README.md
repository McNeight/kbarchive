---
layout: page
title: "Q129209: HOWTO: Convert 10-Byte Long Doubles to 8-Byte Doubles"
permalink: /kb/129/Q129209/
---

## Q129209: HOWTO: Convert 10-Byte Long Doubles to 8-Byte Doubles

{% raw %}

	Article: Q129209
	Product(s): Microsoft C Compiler
	Version(s): 1.0,2.0,2.1,4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbCompiler kbVC100 kbVC200 kbVC210 kbVC400 kbVC500 kbVC600
	Last Modified: 29-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft C/C++ Compiler (CL.EXE), included with:
	   - Microsoft Visual C++, 32-bit Editions, versions 1.0, 2.0, 2.1, 4.0, 5.0, 6.0, used with:
	      - the hardware: Intel x86 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	With the 16-bit Microsoft C/C++ compilers, long doubles are stored as 80- bit
	(10-byte) data types. Under Windows NT, in order to be compatible with other
	non-Intel floating point implementations, the 80-bit long double format is
	aliased to the 64-bit (8-byte) double format.
	
	This means that 32-bit programs may not be able read back data files written by
	16-bit programs because the long double formats are incompatible.
	
	On Intel platforms, the only workaround is to let the floating point processor
	handle the conversion from 80-bit to 64-bit doubles. Afterwards, the data can be
	stored back into a 64-bit double for use under Win32.
	
	The sample code below illustrates how you could use floating point instructions
	in inline assembly to convert from a 10-byte double in a data file to an 8-byte
	double.
	
	Sample Code
	-----------
	
	  /* Compile options needed: none
	  */ 
	
	  #include <stdio.h>
	
	  void main(void)
	  {
	     FILE *inFile;
	     char buffer[10];
	     long double Newdbl;
	
	     inFile = fopen("data","rb");
	     fread(buffer, 10, 1, inFile);      // reads in 10-byte long double
	     fclose(inFile);
	
	     // This moves the contents of the buffer into the floating point
	     // register, which then then takes care of the automatic convertion
	     // back to a 8-byte long double
	
	     _asm {
	        fld TBYTE PTR buffer;
	        fstp Newdbl;
	     }
	  }
	
	Additional query words: 8.00 9.00 9.10
	
	======================================================================
	Keywords          : kbCompiler kbVC100 kbVC200 kbVC210 kbVC400 kbVC500 kbVC600 
	Technology        : kbVCsearch kbAudDeveloper kbCVCComp
	Version           : :1.0,2.0,2.1,4.0,5.0,6.0
	Hardware          : x86
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
