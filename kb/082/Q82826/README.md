---
layout: page
title: "Q82826: OLE and Networking Issues"
permalink: /kb/082/Q82826/
---

## Q82826: OLE and Networking Issues

{% raw %}

	Article: Q82826
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 04-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When using Microsoft Windows operating system version 3.1 with OLE version 1.0,
	it is possible to share an object (create a link to a piece of data) that is
	located on a network file server. To do this, both the client application and
	the server application must be installed on the same local machine.
	
	MORE INFORMATION
	================
	
	To establish an OLE communication, both the server and the client application
	must be installed on the same machine. The interprocess communication that OLE
	uses (dynamic data exchange -- DDE) is not supported across the network, only
	locally. The information, either the container document or the source of the
	linked object, can be on the network server.
	
	In the case of a linked object, the network address for the file that contains
	the object is stored with the object. When the object is activated, OLE tries to
	bind to the object. If the network file server is not connected, OLE will
	attempt to make the connection. If the file server has a password, then OLE will
	ask for the password. If the connection cannot be established, or if the file is
	not found, an error message is displayed:
	
	  Linked document is unavailable.
	
	There is no known limit to the number of connections or links to a network file
	server, except available drive letters.
	
	Additional query words: 3.10 3.1
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin310 kbWin311
	Version           : WINDOWS:3.1,3.11
	
	=============================================================================
	

{% endraw %}
