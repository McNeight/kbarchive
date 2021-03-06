---
layout: page
title: "Q251066: HOWTO: Determine If a Computer Is a Microsoft Terminal Server"
permalink: /kb/251/Q251066/
---

## Q251066: HOWTO: Determine If a Computer Is a Microsoft Terminal Server

{% raw %}

	Article: Q251066
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0,3.0b,5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbAPI kbvfp kbvfp300 kbvfp300b kbvfp500 kbvfp500a kbvfp600 kbGrpDSFox kbDSupport kbCode
	Last Modified: 06-APR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article shows how to determine if a computer is a Microsoft Windows NT or
	Windows 2000 Terminal Server.
	
	MORE INFORMATION
	================
	
	1. In Visual FoxPro, create a program file using the following code:
	
	  *Start of Code
	  LOCAL lTerminalServer
	
	  lTerminalServer = IsTerminalServer()
	
	  IF (lTerminalServer) THEN
	     =MESSAGEBOX ("This Computer is a Terminal Server")
	  ELSE
	     =MESSAGEBOX("This Computer is not a Terminal Server")
	  ENDIF
	
	  FUNCTION IsTerminalServer
	     * This function will determine if the machine is a Terminal Server.
	     * It will return .T. if it is and .F. if not.
	
	     * Constants that are needed for Registry functions
	     #DEFINE HKEY_LOCAL_MACHINE -2147483646  && BITSET(0,31)+2
	     #DEFINE REG_DWORD 4	                   && A 32-bit number.
	
	     * WIN 32 API functions that are used
	     DECLARE Integer RegOpenKey IN Win32API ;
	        Integer nHKey, String @cSubKey, Integer @nResult
	     DECLARE Integer RegQueryValueEx IN Win32API ;
	        Integer nHKey, String lpszValueName, Integer dwReserved,;
	        Integer @lpdwType, String @lpbData, Integer @lpcbData
	     DECLARE Integer RegCloseKey IN Win32API ;
	        Integer nHKey
	     DECLARE GetVersionEx IN win32api STRING @OSVERSIONINFO
	
	     * Local variables used
	     LOCAL nErrCode	   && Error Code returned from Registry functions
	     LOCAL nKeyHandle	   && Handle to Key that is opened in the Registry
	     LOCAL lpdwValueType	   && Type of Value that we are looking for
	     LOCAL lpbValue	   && The data stored in the value
	     LOCAL lpcbValueSize	   && Size of the variable
	     LOCAL lpdwReserved	   && Reserved Must be 0
	     LOCAL cKey		   && Key we need to open
	     LOCAL cValueToGet	   && Value to get
	     LOCAL lTerminalServer   && True if it is a Terminal Server
	     LOCAL nTSEnabled	   && Numeric value of TSEnabled
	     LOCAL OSVersion	   && OS Version
	     LOCAL cMajorVersion	   && Just the Version number i.e. 4 or 5
	  	
	     * Initialize the variables
	     cKey = "System\CurrentControlSet\Control\Terminal Server"
	     cValueToGet = "TSEnabled"
	     nKeyHandle = 0				
	     lpdwReserved = 0	       && Must be 0
	     lpdwValueType = REG_DWORD
	     lpcbValueSize = 4	      && DWORD is 4 bytes
	     lTerminalServer = .F.      && Assume it isn't a Terminal Server
	     lpbValue = SPACE(4)
	
	     nErrCode = RegOpenKey(HKEY_LOCAL_MACHINE, cKey, @nKeyHandle)
	     * If the error code isn't 0, then the key doesn't exist or can't be opened.
	     IF (nErrCode # 0) THEN
	        RETURN .F.
	     ENDIF
	
	     * We need to check and see what version we are running NT 4 and Windows 2000 are different
	     OSVersion = LongToStr(148) + REPLICATE(CHR(0), 144)
	     =GetVersionEx(@OSVersion)
	     nMajorVersion = StrToLong(SUBSTR(OSVersion, 5, 4))
	     cMajorVersion = ALLTRIM(STR(nMajorVersion))
	
	     * If it is NT 4 and we made it this far the machine is a Terminal Server
	     IF (cMajorVersion = "4") THEN
	        * Close the key when done.
	        =RegCloseKey(nKeyHandle)
	        RETURN .T.
	     ENDIF
	
	     * Get the value of TSEnabled. 1 is a Terminal  Server 0 isn't 
	     nErrCode=RegQueryValueEx(nKeyHandle, cValueToGet, lpdwReserved, @lpdwValueType, @lpbValue, @lpcbValueSize)
	
	     * Close the key when done.
	     =RegCloseKey(nKeyHandle)
	
	     IF (nErrCode # 0) THEN
	        RETURN .F.
	     ELSE
	        nTSEnabled = StrToLong(lpbValue)
	     ENDIF
	  	
	     * Check to see if it is a Terminal Server	
	     IF (nTSEnabled = 1) THEN
	         RETURN .T.
	     ELSE
	        RETURN .F.		
	     ENDIF
	  ENDFUNC	
	
	  FUNCTION StrToLong
	  * This function converts a String to a Long
	     PARAMETERS cLongStr
	
	     LOCAL nLoopVar, nRetval
	
	     nRetval = 0
	     FOR nLoopVar = 0 TO 24 STEP 8
	        nRetval = nRetval + (ASC(cLongStr) * (2^nLoopVar))
	        cLongStr = RIGHT(cLongStr, LEN(cLongStr) - 1)
	     NEXT
	  RETURN nRetval
	
	  FUNCTION LongToStr
	  * This function converts a long to a string
	     PARAMETERS nLongVal
	
	     LOCAL nLoopVar, strReturn
	
	     strReturn = ""
	     FOR nLoopVar = 24 TO 0 STEP -8
	        strReturn = CHR(INT(nLongVal/(2^nLoopVar))) + strReturn
	        nLongVal = MOD(nLongVal, (2^nLoopVar))
	     NEXT
	  RETURN strReturn
	  *End of Code
	
	2. Run the program created in step 1. The result appears in a message box as:
	
	  This computer is a Terminal Server.
	
	  -or-
	
	  This computer is not a Terminal Server.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbAPI kbvfp kbvfp300 kbvfp300b kbvfp500 kbvfp500a kbvfp600 kbGrpDSFox kbDSupport kbCodeSnippet 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP300b kbVFP500 kbVFP600 kbVFP500a
	Version           : WINDOWS:3.0,3.0b,5.0,5.0a,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
