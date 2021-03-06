---
layout: page
title: "Q176189: WD97: Shading of Solid Black or Gray Wont Print Duplex on NT"
permalink: /kb/176/Q176189/
---

## Q176189: WD97: Shading of Solid Black or Gray Wont Print Duplex on NT

{% raw %}

	Article: Q176189
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97; winnt:4.0
	Operating System(s): 
	Keyword(s): word97
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows, used with:
	   - the operating system: Microsoft Windows NT 4.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you print in duplex mode to an HP LaserJet 5si running under Windows NT
	4.0, your document does not print on both sides of the page. Instead it prints
	only on one side of the page.
	
	CAUSE
	=====
	
	This problem will occur if your document contains a table with solid black
	shading.
	
	This problem is more likely to occur with shading of higher percentages of gray
	(70% and higher). However, there is no certain percentage of shading at which
	this problem occurs. Sometimes the document will be printed on both sides of the
	page if it is formatted at 70-80% gray shading; however, other times it will not
	be printed at all.
	
	NOTE: If the shading is of lower percentages of gray shading (5% to approximately
	65%), duplex printing should function correctly.
	
	This problem occurs with the HP LaserJet 5si driver that shipped with Windows NT
	4.0. Changing any of the settings in the driver does not provide a workaround to
	this issue.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the Hewlett-Packard (HP) LaserJet 5si driver for
	Windows NT 4.0 from the HP Web site. If you have trouble installing the new
	driver, contact Hewlett-Packard (HP) technical support.
	
	
	There are four printer driver versions provided with the HP driver:
	
	  HP LaserJet 5si (Standard)
	  HP LaserJet 5si Mopier
	  HP LaserJet 5si Mopier PS
	  HP LaserJet 5si/5si MX PS
	
	NOTE: The standard HP LaserJet 5si driver does not have the duplexing feature.
	
	For information about how to contact HP, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q65416 Hardware and Software Third-Party Vendor Contact List, A-K
	
	
	MORE INFORMATION
	================
	
	The driver mentioned in this article is manufactured by Hewlett-Packard (HP), a
	vendor independent of Microsoft; we make no warranty, implied or otherwise,
	regarding this product's performance or reliability.
	
	Additional query words: one side two sided shade shades format borders and shading table cell duplex duplexed duplexing broken will not print both sides simplex one-sided two-sided multiple multiplex
	
	======================================================================
	Keywords          : word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97; winnt:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
