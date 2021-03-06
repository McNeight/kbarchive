---
layout: page
title: "Q303250: XADM: Command Line Directory Export Does Not Succeed"
permalink: /kb/303/Q303250/
---

## Q303250: XADM: Command Line Directory Export Does Not Succeed

{% raw %}

	Article: Q303250
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 24-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to perform a directory export with the Command Line Directory
	Export Utility by using a directory export options file, the export might not
	succeed. The result is a .csv file that contains only header information. The
	.csv file contains an entry similar to the following:
	
	Container,,,,,Recipients,,,,,,,
	
	CAUSE
	=====
	
	The objects to be exported are located in a subcontainer. In the directory
	export options file, the attribute BasepointOnly= was added. The BasepointOnly=
	attribute was either set to "Yes" or left blank.
	
	RESOLUTION
	==========
	
	Set the value for the attribute BasepointOnly to "No" to make sure that the
	objects in the subcontainer will be exported. You can also delete the whole
	attribute in the export options file.
	
	MORE INFORMATION
	================
	
	Because the objects to be exported are located in a subcontainer, you must
	specify a value in the export options file for the attribute "Basepoint" in the
	following form:
	BasePoint=/o=<Your Org Name>/ou=<Your Site Name>/cn=Recipients
	You must also specify a value for the attribute "Container" in the following
	form:
	Container=<Your subcontainer Name>
	
	Additionally, you must specify the value for the attribute "BasepointOnly."
	
	If this value is set to "Yes," the content of the subcontainer is not accessed
	during the export process. Instead, the basepoint itself is exported, which in
	this case is the recipient container. As a result, you get a .csv file as
	described in the "Symptoms" section of this article.
	
	NOTE: The Help file states that the default value for BasepointOnly is "No." This
	is not true. The default value is "Yes." Therefore, even if you leave the value
	blank, the problem described in the "Symptoms" section of this article will
	occur.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : :5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
