---
layout: page
title: "Q164017: Explanation of a DNS Zone Transfer"
permalink: /kb/164/Q164017/
---

## Q164017: Explanation of a DNS Zone Transfer

{% raw %}

	Article: Q164017
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article discusses the circumstances that can trigger a Domain Name System
	(DNS) Zone Transfer, the purpose of zone transfers, and how the process works.
	
	MORE INFORMATION
	================
	
	Definition of a Zone Transfer: A Zone Transfer is the term used to refer to the
	process by which the contents of a DNS Zone file are copied from a primary DNS
	server to a secondary DNS server.
	
	A Zone transfer will occur during any of the following scenarios:
	
	- When starting the DNS Service on the secondary DNS server.
	
	- When the refresh time expires.
	
	- When changes are saved to the Primary Zone file and there is a Notify List.
	
	Zone Transfers are always initiated by the secondary DNS server. The primary DNS
	server simply answers the request for a Zone Transfer.
	
	The following Network Monitor Capture sequence shows the process when either the
	DNS Service is started on the secondary DNS server or the refresh time expires:
	
	Frame 1: The secondary DNS server - JH40PS - requests the SOA record from the
	primary DNS server - SERVER - for Zone DOMAIN.COM. Note DNS Question Type.
	
	JH40PS SERVER DNS 0x4000:Std Qry for domain.com. of type SOA on class INET addr.
	
	DNS: 0x4000:Std Qry for domain.com. of type SOA on class INET addr.
	
	   DNS: Query Identifier = 16384 (0x4000)
	   DNS: DNS Flags = Query, OpCode - Std Qry, RCode - No error
	       DNS: 0............... = Query
	       DNS: .0000........... = Standard Query
	       DNS: .....0.......... = Server not authority for domain
	       DNS: ......0......... = Message complete
	       DNS: .......0........ = Iterative query desired
	       DNS: ........0....... = No recursive queries
	       DNS: .........000.... = Reserved
	       DNS: ............0000 = No error
	   DNS: Question Entry Count = 1 (0x1)
	   DNS: Answer Entry Count = 0 (0x0)
	   DNS: Name Server Count = 0 (0x0)
	   DNS: Additional Records Count = 0 (0x0)
	   DNS: Question Section: domain.com. of type SOA on class INET addr.
	       DNS: Question Name: domain.com.
	       DNS: Question Type = Start of zone of authority
	       DNS: Question Class = Internet address class
	
	Frame 2: The primary DNS server responds with the contents of the SOA record in
	the Answer Section.
	
	SERVER JH40PS DNS 0x4000:Std Qry Resp. for domain.com. of type SOA on class INET
	addr.
	
	DNS: 0x4000:Std Qry Resp. for domain.com. of type SOA on class INET addr.
	
	   DNS: Query Identifier = 16384 (0x4000)
	   DNS: DNS Flags = Response, OpCode - Std Qry, AA RA Bits Set, RCode - No
	        error
	       DNS: 1............... = Response
	       DNS: .0000........... = Standard Query
	       DNS: .....1.......... = Server authority for domain
	       DNS: ......0......... = Message complete
	       DNS: .......0........ = Iterative query desired
	       DNS: ........1....... = Recursive queries supported by server
	       DNS: .........000.... = Reserved
	       DNS: ............0000 = No error
	   DNS: Question Entry Count = 1 (0x1)
	   DNS: Answer Entry Count = 1 (0x1)
	   DNS: Name Server Count = 0 (0x0)
	   DNS: Additional Records Count = 0 (0x0)
	   DNS: Question Section: domain.com. of type SOA on class INET addr.
	       DNS: Question Name: domain.com.
	       DNS: Question Type = Start of zone of authority
	       DNS: Question Class = Internet address class
	   DNS: Answer section: domain.com. of type SOA on class INET addr.
	       DNS: Resource Name: domain.com.
	       DNS: Resource Type = Start of zone of authority
	       DNS: Resource Class = Internet address class
	       DNS: Time To Live = 86400 (0x15180)
	       DNS: Resource Data Length = 41 (0x29)
	       DNS: Primary Name Server: server.domain.com.
	       DNS: Responsible Authorative Mailbox: administrator.domain.com.
	       DNS: Version number = 26 (0x1A)
	       DNS: Refresh Interval = 300 (0x12C)
	       DNS: Retry interval = 120 (0x78)
	       DNS: Expiration Limit = 600 (0x258)
	       DNS: Minimum TTL = 86400 (0x15180)
	
	Frame 3: Having compared the version number (serial number) and found it to be
	different than its current version number, the secondary DNS server now requests
	a Zone Transfer. Note the Question Type in the DNS Question Section.
	
	JH40PS SERVER DNS 0x0:Std Qry for domain.com. of type Req. for zn Xfer on class
	INET addr.
	
	DNS: 0x0:Std Qry for domain.com. of type Req. for zn Xfer on class INET addr.
	
	   DNS: TCP Length = 31 (0x1F)
	   DNS: Query Identifier = 0 (0x0)
	   DNS: DNS Flags = Query, OpCode - Std Qry, RCode - No error
	       DNS: 0............... = Query
	       DNS: .0000........... = Standard Query
	       DNS: .....0.......... = Server not authority for domain
	       DNS: ......0......... = Message complete
	       DNS: .......0........ = Iterative query desired
	       DNS: ........0....... = No recursive queries
	       DNS: .........000.... = Reserved
	       DNS: ............0000 = No error
	   DNS: Question Entry Count = 1 (0x1)
	   DNS: Answer Entry Count = 0 (0x0)
	   DNS: Name Server Count = 0 (0x0)
	   DNS: Additional Records Count = 0 (0x0)
	   DNS: Question Section: domain.com. of type Req. for zn Xfer on class
	        INET addr.
	       DNS: Question Name: domain.com.
	       DNS: Question Type = Request for zone transfer
	       DNS: Question Class = Internet address class
	   DNS: Frame Padding
	
	Frame 4: The primary DNS server complies with the request for a Zone Transfer.
	The entire contents of the Zone file are transferred in the DNS Answer section.
	
	SERVER JH40PS DNS 0x0:Std Qry Resp. for domain.com. of type SOA on class INET
	addr.
	
	DNS: 0x0:Std Qry Resp. for domain.com. of type SOA on class INET addr.
	
	   DNS: TCP Length = 445 (0x1BD)
	   DNS: Query Identifier = 0 (0x0)
	   DNS: DNS Flags = Response, OpCode - Std Qry, RA Bits Set, RCode - No
	        error
	       DNS: 1............... = Response
	       DNS: .0000........... = Standard Query
	       DNS: .....0.......... = Server not authority for domain
	       DNS: ......0......... = Message complete
	       DNS: .......0........ = Iterative query desired
	       DNS: ........1....... = Recursive queries supported by server
	       DNS: .........000.... = Reserved
	       DNS: ............0000 = No error
	   DNS: Question Entry Count = 1 (0x1)
	   DNS: Answer Entry Count = 16 (0x10)
	   DNS: Name Server Count = 0 (0x0)
	   DNS: Additional Records Count = 0 (0x0)
	   DNS: Question Section: domain.com. of type Req. for zn Xfer on class
	        INET addr.
	       DNS: Question Name: domain.com.
	       DNS: Question Type = Request for zone transfer
	       DNS: Question Class = Internet address class
	   DNS: Answer section: . of type SOA on class INET addr.(16 records
	        present)
	       DNS: Resource Record: domain.com. of type SOA on class INET addr.
	           DNS: Resource Name: domain.com.
	           DNS: Resource Type = Start of zone of authority
	           DNS: Resource Class = Internet address class
	           DNS: Time To Live = 86400 (0x15180)
	           DNS: Resource Data Length = 41 (0x29)
	           DNS: Primary Name Server: server.domain.com.
	           DNS: Responsible Authorative Mailbox: administrator.domain.com.
	           DNS: Version number = 26 (0x1A)
	           DNS: Refresh Interval = 300 (0x12C)
	           DNS: Retry interval = 120 (0x78)
	           DNS: Expiration Limit = 600 (0x258)
	           DNS: Minimum TTL = 86400 (0x15180)
	       DNS: Resource Record: domain.com. of type Host Addr on class INET
	            addr.
	           DNS: Resource Name: domain.com.
	           DNS: Resource Type = Host Address
	           DNS: Resource Class = Internet address class
	           DNS: Time To Live = 86400 (0x15180)
	           DNS: Resource Data Length = 4 (0x4)
	           DNS: IP address = 130.0.10.150
	       DNS: Resource Record: domain.com. of type Auth. NS on class INET
	            addr.
	           DNS: Resource Name: domain.com.
	           DNS: Resource Type = Authoritative Name Server
	           DNS: Resource Class = Internet address class
	           DNS: Time To Live = 86400 (0x15180)
	           DNS: Resource Data Length = 10 (0xA)
	           DNS: Authoritative Name Server: server.domain.com.
	       DNS: Resource Record: Dell.domain.com. of type Host Addr on class
	            INET addr.
	           DNS: Resource Name: Dell.domain.com.
	           DNS: Resource Type = Host Address
	           DNS: Resource Class = Internet address class
	           DNS: Time To Live = 86400 (0x15180)
	           DNS: Resource Data Length = 4 (0x4)
	           DNS: IP address = 130.0.10.30
	       DNS: Resource Record: JH40PS.domain.com. of type Host Addr on
	                class INET addr.
	           DNS: Resource Name: JH40PS.domain.com.
	           DNS: Resource Type = Host Address
	           DNS: Resource Class = Internet address class
	           DNS: Time To Live = 86400 (0x15180)
	           DNS: Resource Data Length = 4 (0x4)
	           DNS: IP address = 130.0.10.155
	
	If changes are made to the Zone file and there are entries in the Notify List,
	the following sequence will occur before the regular Zone Transfer sequence as
	outlined above.
	
	Frame A: In this frame, a change has been made to the Zone file. Because JH40PS
	is on the Notify List, the primary DNS server sends this frame to notify the
	secondary DNS server that a change has occurred and that the secondary DNS
	server should query the SOA resource record.
	
	SERVER JH40PS DNS 0x0:Std Qry for domain.com. of type SOA on class INET addr.
	
	DNS: 0x0:Std Qry for domain.com. of type SOA on class INET addr.
	
	   DNS: Query Identifier = 0 (0x0)
	   DNS: DNS Flags = Query, OpCode - Rsrvd, AA Bits Set, RCode - No error
	       DNS: 0............... = Query
	       DNS: .0100........... = Reserved
	       DNS: .....1.......... = Server authority for domain
	       DNS: ......0......... = Message complete
	       DNS: .......0........ = Iterative query desired
	       DNS: ........0....... = No recursive queries
	       DNS: .........000.... = Reserved
	       DNS: ............0000 = No error
	   DNS: Question Entry Count = 1 (0x1)
	   DNS: Answer Entry Count = 0 (0x0)
	   DNS: Name Server Count = 0 (0x0)
	   DNS: Additional Records Count = 0 (0x0)
	   DNS: Question Section: domain.com. of type SOA on class INET addr.
	       DNS: Question Name: domain.com.
	       DNS: Question Type = Start of zone of authority
	       DNS: Question Class = Internet address class
	
	Frame B: The secondary DNS server acknowledges the receipt of Frame 1.
	
	JH40PS SERVER DNS 0x0:Std Qry Resp.
	
	DNS: 0x0:Std Qry Resp.
	
	   DNS: Query Identifier = 0 (0x0)
	   DNS: DNS Flags = Response, OpCode - Rsrvd, AA Bits Set, RCode - No
	        error
	       DNS: 1............... = Response
	       DNS: .0100........... = Reserved
	       DNS: .....1.......... = Server authority for domain
	       DNS: ......0......... = Message complete
	       DNS: .......0........ = Iterative query desired
	       DNS: ........0....... = No recursive queries
	       DNS: .........000.... = Reserved
	       DNS: ............0000 = No error
	   DNS: Question Entry Count = 1 (0x1)
	   DNS: Answer Entry Count = 0 (0x0)
	   DNS: Name Server Count = 0 (0x0)
	   DNS: Additional Records Count = 0 (0x0)
	   DNS: Question Section: domain.com. of type SOA on class INET addr.
	       DNS: Question Name: domain.com.
	       DNS: Question Type = Start of zone of authority
	       DNS: Question Class = Internet address class
	
	Immediately following this response, the Zone Transfer process begins as in Frame
	1 in the first capture sequence above.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
