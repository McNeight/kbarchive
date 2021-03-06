---
layout: page
title: "Q200027: HOWTO: Determine If IE Is Offline from an ActiveX Document"
permalink: /kb/200/Q200027/
---

## Q200027: HOWTO: Determine If IE Is Offline from an ActiveX Document

{% raw %}

	Article: Q200027
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0,4.01,4.01 SP1,4.01 SP2,5,5.0,5.5,6.0
	Operating System(s): 
	Keyword(s): kbActiveDocs kbInternet kbVBp kbVC500 kbVC600 kbie401sp1 kbie401sp2 kbGrpDSInet kbie500
	Last Modified: 20-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Internet Explorer (Programming) versions 4.0, 4.01, 4.01 SP1, 4.01 SP2, 5, 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When developing Internet applications, developers need to account for end users
	with a wide variety of system environments with different ways of connecting to
	the Internet. This ActiveX Document sample code demonstrates how to determine if
	Internet Explorer is offline.
	
	MORE INFORMATION
	================
	
	Use the following sample code to determine if Internet Explorer is offline:
	
	1. Start a new ActiveX Document project. UserDocument1 is added by default.
	
	2. Add the following code to the general declarations section of UserDocument1:
	
	  Dim bOffline As Boolean
	
	  Private Function get_Offline() As Boolean ' (VARIANT_BOOL * bOffline)
	   Dim hr As Long
	   Dim ci As INTERNET_CONNECTED_INFO
	   Dim ci_len As Long
	   ci_len = 8
	   Dim ret As Long
	
	   ret = InternetQueryOption(0&, INTERNET_OPTION_CONNECTED_STATE, _
	          ci, ci_len)
	  get_Offline = Not ((ci.dwConnectedState And INTERNET_STATE_CONNECTED) = 
	  INTERNET_STATE_CONNECTED)
	  End Function
	
	  Private Sub put_Offline(bOffline As Boolean)
	    Dim hr As Long
	    Dim ci As INTERNET_CONNECTED_INFO
	    Dim ret As Long
	    If bOffline Then
	       ci.dwConnectedState = INTERNET_STATE_DISCONNECTED_BY_USER
	       ci.dwFlags = ISO_FORCE_DISCONNECTED
	    Else
	       ci.dwConnectedState = INTERNET_STATE_CONNECTED
	    End If
	
	    ret = InternetSetOption(0&, INTERNET_OPTION_CONNECTED_STATE, _
	                 ci, LenB(ci))
	  End Sub
	
	3. Add a Command button to UserDocument1 and insert this code:
	
	  Private Sub Command1_Click()
	     MsgBox "Offline = " & get_Offline()
	  End Sub
	
	4. Add a Command button to form1 and insert this code:
	
	  Private Sub Command2_Click()
	     put_Offline True
	  End Sub
	
	5. Add a standard module to the project and insert this code:
	
	     Option Explicit
	     Public Type INTERNET_CONNECTED_INFO
	        dwConnectedState As Long
	        dwFlags As Long
	     End Type
	
	     Public Declare Function InternetSetOption Lib "wininet.dll" Alias _
	       "InternetSetOptionA" (ByVal hInternet As Long, _
	         ByVal lOption As Long, ByRef sBuffer As Any, _
	           ByVal lBufferLength As Long) As Integer
	
	  ' Queries an Internet option on the specified handle
	     Public Declare Function InternetQueryOption Lib "wininet.dll" Alias _
	      "InternetQueryOptionA" (ByVal hInternet As Long, _
	         ByVal lOption As Long, ByRef sBuffer As Any, _
	         ByRef lBufferLength As Long) As Integer
	
	     Public Const INTERNET_OPTION_CONNECTED_STATE = 50
	     Public Const INTERNET_STATE_CONNECTED = 1
	
	  ' // disconnected from network
	      Public Const INTERNET_STATE_DISCONNECTED = 2
	  ' 0x00000010    //  disconnected by user request
	      Public Const INTERNET_STATE_DISCONNECTED_BY_USER = &H10
	  '// no network requests being made (by Wininet)
	      Public Const INTERNET_STATE_IDLE = &H100
	  '// network requests being made (by  Wininet)
	      Public Const INTERNET_STATE_BUSY = &H200
	  '// 
	  '// ISO_FORCE_DISCONNECTED -
	  '// if set when putting Wininet into disconnected mode,
	  '// all outstanding requests will be aborted with a cancelled error
	  '// 
	
	  Public Const ISO_FORCE_DISCONNECTED = 1
	
	6. Save Project and press F5 to test.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbActiveDocs kbInternet kbVBp kbVC500 kbVC600 kbie401sp1 kbie401sp2 kbGrpDSInet kbie500 kbie550 
	Technology        : kbVBSearch kbIEsearch kbAudDeveloper kbZNotKeyword6 kbSDKIESearch kbZNotKeyword2 kbVB500Search kbVB600Search kbVB500 kbVB600 kbIE500Search kbSDKIE400 kbSDKIE401 kbSDKIE401SP1 kbSDKIE401SP2 kbSDKIE500 kbSDKIE550 kbIE550Search
	Version           : WINDOWS:4.0,4.01,4.01 SP1,4.01 SP2,5,5.0,5.5,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
