---
layout: page
title: "Q216848: BUG: MDAC: SQL Server Driver May Return Error &quot;Login Failed&quot;"
permalink: /kb/216/Q216848/
---

## Q216848: BUG: MDAC: SQL Server Driver May Return Error &quot;Login Failed&quot;

{% raw %}

	Article: Q216848
	Product(s): Open Database Connectivity (ODBC)
	Version(s): WINDOWS:3.7; winnt:6.5,7.0
	Operating System(s): 
	Keyword(s): kbSQLServ650bug kbSQLServ700bug
	Last Modified: 27-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft ODBC Driver for SQL Server, version 3.7 
	- Microsoft SQL Server versions 6.5, 7.0 
	-------------------------------------------------------------------------------
	
	BUG #: 54023 (SQLBUG_70)
	
	BUG #: 18608 (SQLBUG_65)
	
	SYMPTOMS
	========
	
	An ODBC application may fail to connect to SQL Server 6.x with the following
	error message returned:
	
	  [28000][Microsoft][ODBC SQL Server Driver][SQL Server] Login failed (4002)
	
	This problem occurs when applications use the Microsoft Data Access Components
	(MDAC) 2.1 version of the SQL Server driver (3.70.623) to make trusted
	connections to SQL Server 6.x and an older version (version 6.x or earlier) of
	the SQL Server client-side Net-Library DLL is the first on the path.
	
	If all client-side Net-Library DLLs are updated to the SQL Server 7.0 version,
	this problem does not occur. Applications will not experience this problem when
	connecting to SQL Server 7.0. Finally, if the ODBC application is started from a
	directory that contains the updated client-side Net-Library DLL, the problem
	does not occur either.
	
	CAUSE
	=====
	
	The MDAC 2.1 SQL Server driver is designed to automatically load the correct
	version of Net-Library from the <Winntroot>\System32 directory if an older
	version of Net-Library is initially loaded. However, when loading the
	Net-Library DLL from the System32 directory for the second time, the driver
	incorrectly assumes it is making a trusted connection to SQL Server 7.0,
	resulting an invalid login packet sent. This causes the connection to fail and
	the error to be returned.
	
	WORKAROUND
	==========
	
	This problem can easily be avoided by updating all Net-Library DLLs on the path,
	including those in the current directory where the application is started. MDAC
	2.1 installs the following Net-Library DLLs to the System32 directory, all with
	the date of 11/13/98:
	
	  DBNMPNTW.DLL
	  DBMSRPCN.DLL
	  DBMSSOCN.DLL
	  DBMSSPXN.DLL
	  DBMSVINN.DLL
	  DBMSADSN.DLL
	  DBMSSHRN.DLL
	
	These are the correct versions of Net-Library DLLs and should be used with the
	MDAC 2.1 SQL Server driver. To ensure that there are no older versions of these
	DLLs somewhere on the path, it is suggested that you search the hard disk(s) for
	those DLLs and replace them with the new ones. For example, if the Named Pipes
	Net-Library is used for the ODBC application, you should search the hard disks
	for DBNMPNTW.DLL (especially the directory where the application executable file
	is located), and either rename the old DLLs or replace them with the new ones
	found in the System32 directory.
	
	To verify whether MDAC 2.1 is installed on the system, start the ODBC Data Source
	Administrator from Control Panel, click the Drivers tab, and check the SQL
	Server driver version. If it is 3.70.623, then the MDAC 2.1 SQL Server driver is
	installed.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SQL Server 6.5 and 7.0.
	
	MORE INFORMATION
	================
	
	MDAC 2.1 is included with both SQL Server 6.5 Service Pack 5 and SQL Server 7.0.
	The problem is less likely to occur on a server running SQL Server 7.0 because
	the installation of SQL Server 7.0 will update the client-side Net-Library DLLs
	that it can find. On a SQL Server 6.5 computer, the Service Pack 5 upgrade does
	not update the client-side Net-Library DLLs to the SQL Server 7.0 version. Even
	if the MDAC 2.1 installation program copies the SQL Server 7.0 version of the
	Net-Library DLLs to the System32 directory, it does not update those DLLs in
	other directories (such as the Mssql\Binn directory). As a result, any ODBC
	applications that are started from those directories may encounter this problem
	when making trusted connections to SQL Server 6.x-based servers. For example,
	when SQL Server 6.5 is updated to Service Pack 5 and MDAC 2.1 is installed,
	replication distribution tasks may fail to connect to the distribution server
	with the same error in the history log.
	
	
	Additional query words: integrated security named pipes socket tcp/ip sqlsrv32 sp sp5 sp5a netlib
	
	======================================================================
	Keywords          : kbSQLServ650bug kbSQLServ700bug 
	Technology        : kbSQLServSearch kbAudDeveloper kbSQLServ700 kbSQLServ650 kbODBCSearch kbODBCSQLServ370
	Version           : WINDOWS:3.7; winnt:6.5,7.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
