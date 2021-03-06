---
layout: page
title: "Q168831: PRB: Older MFC OCX Controls Incompatible with Visual Basic 4.0"
permalink: /kb/168/Q168831/
---

## Q168831: PRB: Older MFC OCX Controls Incompatible with Visual Basic 4.0

{% raw %}

	Article: Q168831
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbGrpDSVBDB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Upon placing an OCX control on a Visual Basic form, the control will ASSERT or
	cause a General Protection Fault. The most common asserts are as follows:
	
	- Assertion Failure in CTLPROP.CPP Line 768
	
	- Assertion Failure in CTLMODUL.CPP Line 128
	
	The control will continue to run in most cases, but will not function properly.
	
	CAUSE
	=====
	
	OLE Custom Controls (OCX Controls) created using the Microsoft Foundation
	Classes (MFC) that ship with Microsoft Visual C++ version 2.0 or earlier for
	32-bit development and Microsoft Visual C++ 1.51 or earlier for 16-bit
	development will not work properly in Visual Basic 4.0.
	
	The OCX standards and implementations have changed such that some minor
	incompatibilities have been created. The following MFC code raises the assertion
	when Visual Basic passes NULL as parameters:
	
	     STDMETHODIMPCOleControl::XPerPropertyBrowsing::GetPredefinedStrings(
	         DISPID dispid,
	     CALPOLESTR FAR* lpcaStringsOut, CADWORD FAR*
	      lpcaCookiesOut)
	     {
	         ...
	         METHOD_MANAGE_STATE(COleControl,PerPropertyBrowsing)
	         ...
	         ASSERT_POINTER(lpcaStringsOut,CALPOLESTR);
	         ASSERT_POINTER(lpcaCookiesOut, CADWORD);
	         ...
	     }
	
	RESOLUTION
	==========
	
	Upgrade to Visual C++ 2.1 or higher for 32-bit development and Visual C++ 1.52
	or higher for 16-bit development.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem with Visual C++ version 2.0 and
	earlier for 32-bit development and Visual C++ 1.51 and earlier for 16-bit
	development.
	
	(c) Microsoft Corporation 1997, All Rights Reserved. Contributions by Troy
	Cambra, Microsoft Corporation
	
	
	Additional query words: kbMFC kbVBp400 kbdse kbDSupport kbVBp kbVC
	
	======================================================================
	Keywords          : kbGrpDSVBDB 
	Technology        : kbVBSearch kbAudDeveloper kbVB400Search kbVB400 kbVB16bitSearch
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
