---
layout: page
title: "Q224979: Using Browser Capabilities with Internet Explorer 5.0"
permalink: /kb/224/Q224979/
---

## Q224979: Using Browser Capabilities with Internet Explorer 5.0

{% raw %}

	Article: Q224979
	Product(s): Internet Information Server
	Version(s): WINDOWS:5; winnt:5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 20-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.0 
	- Microsoft Internet Explorer version 5 for Windows NT 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Microsoft Internet Information Services (IIS) version 5.0 with Active Server
	Pages (ASP) and Internet Explorer provides enhanced client and server
	capabilities components that can be combined to allow Web developers greater
	control over the presentation of Web data to clients.
	
	This article explains how to combine these new features in a working example
	scenario.
	
	MORE INFORMATION
	================
	
	WARNING: ANY USE BY YOU OF THE CODE PROVIDED IN THIS ARTICLE IS AT YOUR OWN
	RISK. Microsoft provides this code "as is" without warranty of any kind, either
	express or implied, including but not limited to the implied warranties of
	merchantability and/or fitness for a particular purpose.
	
	Client Capabilities in Internet Explorer 
	----------------------------------------
	
	Microsoft Internet Explorer 4.0 introduced several client-side attributes to the
	DHTML Object Model (DOM) that can be used in customizing a page layout after it
	has been rendered for the client. Internet Explorer 5.0 takes this a step
	further by exposing this information as one of the browser's Default Behaviors.
	
	The following table is a partial list of useful client capabilities. (For a more
	complete list see the MSDN clientCaps Behavior page.)
	
	  
	  +----------------------------------------------------------------------------------------------------------------------------------------------------------+
	  | Client Capability | Description                                                                                        | DHTML Implementation            | 
	  +----------------------------------------------------------------------------------------------------------------------------------------------------------+
	  | AvailHeight       | Specifies the height of the working area of the system's screen,
	  in pixels, excluding the taskbar. | Window.screen.availHeight       | 
	  +----------------------------------------------------------------------------------------------------------------------------------------------------------+
	  | AvailWidth        | Specifies the width of the working area of the system's screen, in
	  pixels, excluding the taskbar.  | Window.screen.availWidth        | 
	  +----------------------------------------------------------------------------------------------------------------------------------------------------------+
	  | BufferDepth       | Specifies the number of bits per pixel used for colors on the off-
	  screen bitmap buffer.           | Window.screen.bufferDepth       | 
	  +----------------------------------------------------------------------------------------------------------------------------------------------------------+
	  | ColorDepth        | Specifies the number of bits per pixel used for colors on the
	  destination device or buffer.        | Window.screen.colorDepth        | 
	  +----------------------------------------------------------------------------------------------------------------------------------------------------------+
	  | CookieEnabled     | Specifies whether client-side cookies are enabled in the
	  browser.                                  | Window.navigator.cookieEnabled  | 
	  +----------------------------------------------------------------------------------------------------------------------------------------------------------+
	  | CpuClass          | Specifies the type of CPU of the client computer.                                                  | Window.navigator.cpuClass       | 
	  +----------------------------------------------------------------------------------------------------------------------------------------------------------+
	  | Height            | Specifies the vertical resolution of the screen, in pixels.                                        | Window.screen.height            | 
	  +----------------------------------------------------------------------------------------------------------------------------------------------------------+
	  | JavaEnabled       | Specifies whether the Microsoft virtual computer is enabled in the
	  browser.                        | Window.navigator.javaEnabled()  | 
	  +----------------------------------------------------------------------------------------------------------------------------------------------------------+
	  | Platform          | Specifies the platform on which the browser is running.                                            | Window.navigator.platform       | 
	  +----------------------------------------------------------------------------------------------------------------------------------------------------------+
	  | SystemLanguage    | Specifies the default language that the system is running.                                         | Window.navigator.systemLanguage | 
	  +----------------------------------------------------------------------------------------------------------------------------------------------------------+
	  | UserLanguage      | Indicates the current user language.                                                               | Window.navigator.userLanguage   | 
	  +----------------------------------------------------------------------------------------------------------------------------------------------------------+
	  | Width             | Specifies the horizontal resolution of the screen, in pixels.                                      | Window.screen.width             | 
	  +----------------------------------------------------------------------------------------------------------------------------------------------------------+
	
	Browser Capabilities in IIS
	---------------------------
	
	IIS 5.0 adds server-side functionality by exchanging the client capabilities
	information through cookies and returning this information to an ASP page as
	part of the Browser Capabilities component. This allows Web developers that
	ability to write ASP code that is custom tailored for a client's display.
	
	Implementation
	--------------
	
	Combining the Internet Explorer 5.0 and IIS 5.0 functionality into a single
	implementation can be thought of as a two-step process:
	
	1. A DHTML page needs to be created to obtain the client capabilities and store
	  them in cookies.
	
	  a. The DHTML page needs to declare the clientcaps behavior.
	
	  <HTML XMLNS:IE>
	  <HEAD>
	  <STYLE>
	    IE\:clientCaps {behavior:url(#default#clientcaps)}
	  </STYLE>
	
	  <!-- client capabilities code goes here -->
	
	  </HEAD>
	  <BODY>
	    <IE:clientcaps ID="objClientCaps" />
	  </BODY>
	
	  b. All desired capabilities need to collected as name=value pairs.
	
	  c. All name=value pairs need to be concatenated together into a single string
	     separated by ampersands (&).
	
	  d. The resulting string needs to be stored in a cookie named BrowsCap.
	
	  e. The following example page illustrates all of the above steps. Copy this
	     code and save it is "clientcap.htm" on your IIS computer in a Web folder
	     with Script and Read access enabled.
	
	  <HTML XMLNS:IE>
	  <HEAD>
	
	  <STYLE>
	    IE\:clientCaps {behavior:url(#default#clientcaps)}
	  </STYLE>
	
	  <SCRIPT language="JavaScript">
	
	  function stopAllErrors() {
	    return true;
	  }
	
	  window.onerror = stopAllErrors;
	
	  function window.onload () {
	    var strBrowsCap;
	
	    strBrowsCap  = "availHeight="     + objClientCaps.availHeight;
	    strBrowsCap += "&availWidth="     + objClientCaps.availWidth;
	    strBrowsCap += "&bufferDepth="    + objClientCaps.bufferDepth;
	    strBrowsCap += "&colorDepth="     + objClientCaps.colorDepth;
	    strBrowsCap += "&cookieEnabled="  + objClientCaps.cookieEnabled;
	    strBrowsCap += "&cpuClass="       + objClientCaps.cpuClass;
	    strBrowsCap += "&height="         + objClientCaps.height;
	    strBrowsCap += "&javaEnabled="    + objClientCaps.javaEnabled;
	    strBrowsCap += "&platform="       + objClientCaps.platform;
	    strBrowsCap += "&systemLanguage=" + objClientCaps.systemLanguage;
	    strBrowsCap += "&userLanguage="   + objClientCaps.userLanguage;
	    strBrowsCap += "&width="          + objClientCaps.width;
	
	    document.cookie = "BrowsCap=" + strBrowsCap;
	  }
	  </SCRIPT>
	  </HEAD>
	
	  <BODY>
	    <IE:clientcaps ID="objClientCaps" />
	  </BODY>
	  <HTML>
	
	2. An ASP page needs to be created to read and use this information.
	
	  a. The ASP page needs to reference the DHTML client capabilities through the
	     use of a special METADATA tag:
	
	  <!--METADATA TYPE="Cookie" NAME="BrowsCap" SRC="clientcap.htm"-->
	
	     Note:The SRC attribute of the tag needs to be set to the name of your DHTML
	     page.
	
	  b. Next, a BrowserType component needs to be created in the ASP page:
	
	  <% Set objBrowserType = Server.CreateObject("MSWC.BrowserType") %>
	
	  c. Individual client attributes can now be obtained by referencing them by
	     name:
	
	  <P>availHeight = <%=objBrowserType.availHeight%></P>
	  <P>availWidth = <%=objBrowserType.availWidth%></P>
	
	  d. The following example page illustrates all of the above steps. Copy this
	     code and save it is "Clientcap.asp" on your IIS computer in the same Web
	     folder as "Clientcap.htm."
	
	  <%@LANGUAGE="VBSCRIPT"%>
	  <HTML>
	  <HEAD>
	  <TITLE>Client Capabilities Test</TITLE>
	  </HEAD>
	  <BODY>
	  <!--METADATA TYPE="Cookie" NAME="BrowsCap" SRC="clientcap.htm"-->
	  <H2 ALIGN="CENTER">Client Capabilities Test</H2>
	  <CENTER>
	  <% Set objBrowserType = Server.CreateObject("MSWC.BrowserType") %>
	  <TABLE BORDER="1">
	    <TR><TH>Attribute     </TH><TH>Value
	  </TH></TR>
	    <TR><TD>availHeight   </TD><TD><%=objBrowserType.availHeight
	  %></TD></TR>
	    <TR><TD>availWidth    </TD><TD><%=objBrowserType.availWidth
	  %></TD></TR>
	    <TR><TD>bufferDepth   </TD><TD><%=objBrowserType.bufferDepth
	  %></TD></TR>
	    <TR><TD>colorDepth    </TD><TD><%=objBrowserType.colorDepth
	  %></TD></TR>
	    <TR><TD>cookieEnabled </TD><TD><%=objBrowserType.cookieEnabled
	  %></TD></TR>
	    <TR><TD>cpuClass      </TD><TD><%=objBrowserType.cpuClass
	  %></TD></TR>
	    <TR><TD>height        </TD><TD><%=objBrowserType.height
	  %></TD></TR>
	    <TR><TD>javaEnabled   </TD><TD><%=objBrowserType.javaEnabled
	  %></TD></TR>
	    <TR><TD>platform      </TD><TD><%=objBrowserType.platform
	  %></TD></TR>
	
	  <TR><TD>systemLanguage</TD><TD><%=objBrowserType.systemLanguage%></TD></TR
	  >
	    <TR><TD>userLanguage  </TD><TD><%=objBrowserType.userLanguage
	  %></TD></TR>
	    <TR><TD>width         </TD><TD><%=objBrowserType.width
	  %></TD></TR>
	  </TABLE>
	  </CENTER>
	  </BODY>
	  </HTML>
	
	Example Scenario
	----------------
	
	The following ASP example uses the DHTML client capabilities "Clientcap.htm" page
	from earlier and shows some of the above properties in action. This example
	illustrates a splash screen style home page for a Web site by:
	
	1. Creating a table at 90% width and 50% height of the available screen.
	
	2. Creating the page title based on the user's CPU type and operating platform.
	
	3. Creating a URL to another Web folder from the user's language setting.
	
	  <%@LANGUAGE="VBSCRIPT"%>
	  <HTML>
	  <HEAD>
	  <TITLE>Welcome to our Web Site!</TITLE>
	  </HEAD>
	  <BODY BGCOLOR="#000000">
	  <!--METADATA TYPE="Cookie" NAME="BrowsCap" SRC="clientcap.htm"-->
	  <H2 ALIGN="CENTER">Client Capabilities Test</H2>
	  <CENTER>
	  <% Set objBrowserType = Server.CreateObject("MSWC.BrowserType") %>
	  <TABLE WIDTH="<%=objBrowserType.availWidth * .9%>"
	  HEIGHT="<%=objBrowserType.availHeight * .5%>">
	    <TR>
	      <TD ALIGN="CENTER" BGCOLOR="#FFFFFF">
	        <H2>Welcome to the <%=UCase(objBrowserType.cpuClass)%> site!</H2>
	        <P>This site is dedicated to <%=UCase(objBrowserType.platform)%>
	  issues.</P>
	        <P><A HREF="/<%=objBrowserType.userLanguage%>/">Click Here to
	  Continue</A></P>
	    </TR>
	  </TABLE>
	  </CENTER>
	  </BODY>
	  </HTML>
	
	For more information, please see the Microsoft Scripting Technologies Web site.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbIEsearch kbiis500 kbZNotKeyword2 kbIENT400Search kbIE500Search kbZNotKeyword3 kbIE500WinNT400
	Version           : WINDOWS:5; winnt:5.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
