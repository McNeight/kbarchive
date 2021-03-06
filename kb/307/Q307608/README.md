---
layout: page
title: "Q307608: INFO: Availability of URLScan Version 2.5 Security Tool"
permalink: /kb/307/Q307608/
---

## Q307608: INFO: Availability of URLScan Version 2.5 Security Tool

{% raw %}

	Article: Q307608
	Product(s): Internet Information Server
	Version(s): 4.0,5.0
	Operating System(s): 
	Keyword(s): kbSecurity KbSECTools
	Last Modified: 04-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.1 
	- Microsoft Internet Information Services version 5.0 
	- Microsoft Internet Information Server version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	URLScan is a security tool that works in conjunction with the IIS Lockdown Tool
	to give Internet Information Services (IIS) Web site administrators the ability
	to turn off unnecessary features and to restrict the type of HTTP requests that
	the server will process. By blocking specific HTTP requests, the URLScan
	security tool prevents potentially harmful requests from reaching the server and
	from causing damage.
	
	Microsoft has released an updated version of the URLScan security tool, version
	2.5, which provides greater security and functionality than earlier versions of
	the tool. URLScan 2.5 is an update to URLScan 1.0 and URLScan 2.0, and you can
	download the update in this article. When you install this new version, your
	earlier version of the URLScan executable file is updated with the URLScan 2.5
	executable file, which also updates the URLScan.ini file accordingly, without
	making any modifications to your previously configured settings.
	
	You have to install URLScan 2.5 over either URLScan 1.0 or URLScan 2.0. If you do
	not currently have URLScan 1.0 or 2.0 on your computer, you should install
	URLScan 2.0 as part of the IIS Lockdown Wizard. If you want to install only the
	URLScan security tool, you can manually extract it from the IIS Lockdown Tool.
	
	For additional information about how to manually extract the URLScan tool from
	the IIS Lockdown Tool, click the article number below to view the article in the
	Microsoft Knowledge Base:
	
	  Q315522 HOW TO: Extract the URLScan Tool and Lockdown Template Files
	
	To determine which version of URLScan is installed on your computer, use
	Add/Remove Programs. URLScan will be present in the list of installed
	components.
	
	NOTE: Both downloads include version 2.5 of URLScan.dll. URLScan-SRP has more
	restrictive settings than Baseline URLScan, which is described in the "More
	Information" section in this article.
	
	The following files are available for download from the Microsoft Download
	Center:
	
	  DownloadDownload Baseline URLScan 2.5 URLScan.exe now
	  (http://www.microsoft.com/downloads/release.asp?ReleaseID=37757)
	
	  Picture of Download IconDownload URLScan-SRP 2.5 URLScan.exe now
	  (http://www.microsoft.com/Downloads/Release.asp?ReleaseID=37756)
	
	Release Date: April 9, 2001
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. After it is posted, the file is housed on
	secure servers that prevent any unauthorized changes to the file.
	
	MORE INFORMATION
	================
	
	The URLScan security tool is comprised of two files: URLScan.dll and
	URLScan.ini, which are packaged together in URLScan.exe. With this latest update
	of URLScan:
	
	- Administrators have an even greater control over the URLScan configuration.
	
	  -and-
	
	- Administrators can secure and lock down the server to a greater degree.
	
	Baseline URLScan
	----------------
	
	This download is the baseline version of URLScan 2.5.
	
	This update introduces the following new features:
	
	- The ability to change the log file directory.
	
	- The ability to log long URLs.
	
	- The ability to restrict the size of requests.
	
	The Ability to Change the Log File Directory:
	
	You can use the LoggingDirectory option to specify the folder in which the log
	file is stored. You have to use the absolute path (such as c:\directory_path)
	for this value. If you do not specify a folder, URLScan creates the log in the
	same folder in which URLScan.dll is located.
	
	The Ability to Log Long URLs:
	
	The addition of the LogLongUrls option allows for an increase in the length of
	URLS that get logged. In earlier versions, URLScan truncated the log lines to
	1024 bytes. The new option provides enhanced logging by increasing the limit to
	128 KB. The allowed values are 0 or 1. The default value is 0. If you set the
	value to 1, URLScan logs up to 128 KB per request. If you set the value is to 0,
	log entries contain only the first 1024 bytes.
	
	The Ability to Restrict the Size of Requests:
	
	With the addition of the RequestLimits section, URLScan can enforce limits on the
	size (in bytes) of separate parts of requests that reach the server. The
	RequestLimits section includes the following three entries:
	
	- MaxAllowedContentLength: This enforces a maximum value to content-length. It
	  does not actually prevent the server from necessarily reading in more data
	  than what this value is set to. For example, if a client makes a chunk
	  transfer encoded POST, this URLScan option is not effective in tracking the
	  size of the entity in the request. The default value is approximately 2 GB
	  (2,000,000,000 bytes).
	
	- MaxUrl: This restricts the length of the request URL (in bytes) but it does
	  not restrict the length of the query string. When you upgrade URLScan by
	  using the installer, the default value is 16 KB.
	
	  NOTE: If you manually extract URLScan.dll from URLScan.exe and do not update
	  URLScan.ini, the default setting will be 260 bytes, and you will have to add
	  MaxUrl = 16384 to URLScan.ini to overwrite the default setting.
	
	- MaxQueryString: This restricts the length of the query string, in bytes. The
	  default value is 4 KB.
	
	In addition, you can impose a byte limit on the size of a specific request header
	by prepending Max- to the name of any header. For example, the following entry
	imposes a limit of 100 bytes on the 'Content-Type' header:
	
	  Max-Content-Type=100
	
	To list a header and not specify a maximum value, use 0. For example:
	
	  Max-User-Agent=0
	
	Also, any headers that are not listed in this section are not checked for length
	limits.
	
	URLScan-SRP
	-----------
	
	This download of URLScan can protect against all the vulnerabilities listed in
	the Microsoft Security Bulletin MS02-018.
	
	IMPORTANT: The main difference between the URLScan-SRP configuration and that of
	the Baseline URLScan lies in its handling of Chunked Encoding data transfers. By
	default, chunked encoding transfers are blocked in URLScan-SRP; they are not
	blocked by default in the baseline URLScan; therefore, clients that rely on
	chunked encoding are blocked by the URLScan-SRP configuration settings. In
	addition, uploads to the server are restricted to 30 MB in the URLScan-SRP
	configuration. All other features are the same as in the Baseline URLScan
	configuration, which is described in the "URLScan Baseline" section.
	
	URLScan 2.0 Features
	--------------------
	
	URLScan 2.0 incorporates customer feedback from URLScan 1.0 and extends the
	functionality available to administrators. URLScan 2.0 introduced the following
	new features:
	
	- The ability to parse the first recognizable extension in a request string.
	
	- An improvement in logging capabilities.
	
	- The ability to include periods as possible extensions.
	
	- The ability to customize a return message for failed requests.
	
	The Ability to Parse the First Recognizable Extension in a Request String:
	
	URLScan 1.0 implements AllowDotInPath=0 to reject requests in the form of
	"/abc.dll/def.ghi.htm." It does all of the parsing to find the last recognizable
	extension. URLScan 2.0 searches for the first recognizable extension in the
	request string. If the extension is .dll, .com, or .exe, that extension is
	stored (where) instead, and then (what passes) passes the AllowDotInPath test.
	
	For example, in URLScan 1.0, the string "/_vti_bin/shtml.dll/def.ghi.htm" results
	in an extension of .htm and fails the AllowDotInPath test. In URLScan 2.0, the
	string "/_vti_bin/shtml.dll/def.ghi.htm" results in an extension of .dll and
	passes the AllowDotInPath test.
	
	An Improvement in URLScan Logging Capabilities:
	
	URLScan 2.0 changes the log output for URLs so that they are automatically
	preceded with the instance ID of the site for the request (such as,
	"1:/def.htr", instead of "/def.htr"). Administrators can also create daily log
	files, where the file name is in the form of "URLScan.092801.log" using
	PerDayLogging. The date format in the URLScan.log has been changed from [Fri,
	Sept 28 2001 - 01:01:01] to [09-28-2001 - 01:01:01], which makes it easier to
	parse the logs programmatically.
	
	The Ability to Include Periods as Possible Extensions:
	
	URLScan 2.0 supports entering period (.) as an extension to the [AllowExtensions]
	and [DenyExtensions] sections of the URLScan.ini file. By adding a period to
	[AllowExtensions] or [DenyExtensions], administrators can prohibit URLs without
	extensions. The ability to customize return message for failed requests URLScan
	2.0 adds a new option, RejectResponseUrl, that the administrator can use to
	specify a URL to return to the client in the case of a rejected request. Not
	only can the administrator select what the client sees, but it defaults to
	Rejected-By-URLScan, which returns a complete custom error 404 by default.
	
	You can also configure URLScan to send a standard 404 response to the client. By
	setting RejectFastPath to 1, URLScan ignores the RejectResponseUrl option and
	returns a standard 404 response back to the client in the case of a rejected
	request. By enabling RejectFastPath, IIS cannot return a custom 404 response or
	log some parts of the request into the IIS log file; however, the URLScan log
	file will still contain complete information about rejected requests.
	
	For more information about the features in URLScan 2.0, please read the
	documentation that is packaged in URLScan.exe.
	
	URLScan 1.0 Features
	--------------------
	
	With URLScan 1.0, the administrator can reject requests based on the following
	criteria:
	
	- Request method (verb).
	
	- File extension of the resource that is requested.
	
	- Suspicious URL encoding.
	
	- Presence of non-ASCII characters in the URL.
	
	- Presence of specified character sequences in the URL.
	
	- Presence of specified headers in the request.
	
	URLScan 1.0 shipped with limited functionality and has been greatly improved in
	later versions. For more information about the features in URLScan 1.0, please
	read the documentation that is packaged in URLScan.exe.
	
	How to Manually Install URLScan 2.5
	-----------------------------------
	
	To automatically install URLScan 2.5, download and run the appropriate
	URLScan.exe file by using the links in the "Summary" section of this article. To
	manually install URLScan 2.5, perform the following steps:
	
	1. Ensure that you have URLScan 1.0 or URLScan 2.0 on your computer. You have to
	  install URLScan 2.5 over either URLScan 1.0 or URLScan 2.0.
	
	  If you do not currently have URLScan 1.0 or 2.0 on your computer, install
	  URLScan 2.0 as part of the IIS Lockdown Wizard.
	
	  If you want to install only the URLScan security tool, you can manually
	  extract it from the IIS Lockdown Tool.
	
	  For additional information about manually extracting the URLScan tool from the
	  IIS Lockdown Tool, click the article number below to view the article in the
	  Microsoft Knowledge Base:
	
	  Q315522 HOW TO: Extract the URLScan Tool and Lockdown Template Files
	
	  To determine which version of URLScan is installed on your computer, use
	  Add/Remove Programs. URLScan will be present in the list of installed
	  components.
	
	2. Download URLScan.exe to a directory location of your choice.
	
	3. From the command line, navigate to the directory where you saved URLScan.exe.
	
	4. Type "URLScan.exe /x" (without the quotation marks)
	
	5. Stop the World Wide Web Publishing Service.
	
	6. Replace the existing version of URLScan.dll with URLScan.dll, version 2.5.
	
	7. Manually add the following entries to your existing URLScan.ini file:
	
	  1. Add the following section to the URLScan.ini file:
	
	[RequestLimits] 
	MaxAllowedContentLength=30,000,000 (Urlscan-SRP) MaxAllowedContentLength=2,000,000,000 (Baseline Urlscan) 
	MaxUrl=16384 
	MaxQueryString=4096
	
	  2. Add the following entries to the options section:
	
	LoggingDirectory= 
	LogLongUrls=0
	
	  3. Add the transfer-encoding header from the DenyHeaders section
	     (Urlscan-SRP).
	
	  4. Start the World Wide Web Publishing Service.
	
	Rolling Back Changes Made to the URLScan.ini File by URLScan 2.5
	----------------------------------------------------------------
	
	If you discover that you need to roll back to your old URLScan.ini configuration
	after installing URLScan 2.5, complete the following procedure:
	
	To rollback from the "URLScan-SRP" download of the URLScan 2.5:
	
	1. Open URLScan.ini.
	
	2. Set: MaxUrl= -1
	
	3. Set: MaxQueryString= -1
	
	4. Set: MaxAllowedContentLength= -1
	
	5. Set: LogLongUrls = 0
	
	6. Remove the transfer-encoding header from the DenyHeaders section.
	
	To rollback from the "Baseline URLScan" download of the URLScan 2.5:
	
	1. Open URLScan.ini.
	
	2. Set: MaxUrl= -1
	
	3. Set: MaxQueryString= -1
	
	4. Set: MaxAllowedContentLength= -1
	
	5. Set: LogLongUrls = 0
	
	Frequently Asked Questions
	--------------------------
	
	Question: What is URLScan?
	Answer: URLScan screens all incoming requests to the server and filters them
	based on rules set by the administrator. This secures the server by ensuring
	that only valid requests are processed. URLScan is effective in protecting Web
	servers because most malicious attacks share a common characteristic--they
	involve the use of a request that is unusual in some way. For example, the
	request might be:
	
	- Extremely long.
	- Requesting an unusual action.
	- Encoded by using an alternate character set, or include character sequences
	  that are rarely seen in legitimate requests.
	
	By filtering out all unusual requests, URLScan prevents them from reaching the
	server and potentially causing damage.
	
	Question: I am already using URLScan 2.0. Why should I download this update?
	Answer: URLScan 2.5 includes new features have been added to URLScan to provide
	better security. These are as follows:
	
	- The ability to change the log file directory.
	
	- The ability to log long URLs.
	
	- The ability to restrict the size of requests.
	
	Question: Why is Microsoft shipping two versions of URLScan?
	Answer: Microsoft is shipping two versions of URLScan because different servers
	have different requirements and shipping a single version might break some
	applications. The main difference between the URLScan-SRP configuration and that
	of the Baseline URLScan lies in its handling of Chunked Encoding data transfers.
	By default, chunked encoding transfers are blocked in URLScan-SRP; they are not
	blocked by default in the baseline URLScan. In addition, uploads to the server
	are restricted to 30 MB in the URLScan-SRP configuration.
	
	Question: I have already configured URLScan for my site. Will URLScan 2.5
	overwrite my current configuration settings?
	Answer: No. URLScan 2.5 only adds new entries to your existing configuration
	file.
	
	Question: I am trying to install URLScan 2.5 and it will not install. What is
	wrong?
	Answer: URLScan 2.5 only installs over URLScan 1.0 or URLScan 2.0, so you
	probably do not have a version of URLScan already installed on your computer. If
	you do not currently have URLScan 1.0 or 2.0 on your computer, install URLScan
	2.0 as part of the IIS Lockdown Wizard.
	
	If you have URLScan installed on your computer and the installation of URLScan
	2.5 still fails, the existing version of URLScan is probably installed as a site
	filter and not as a global filter. For the URLScan 2.5 installation to be
	successful, you must have any previous version of URLScan installed as a global
	filter.
	
	Question: My applications do not work after installing URLScan 2.5. I would like
	to revert back to my preexisting URLScan.ini configuration until I determine the
	problem. How do I undo the additions to URLScan.ini?
	Answer: URLScan 2.0 introduced the /~* special value to RejectResponseUrl that
	puts URLScan in a logging-only mode so that administrators can better figure out
	why URLScan is rejecting a request. If you still want to rollback all changes,
	please follow the procedure in the "Rolling Back Changes Made to the URLScan.ini
	File by URLScan 2.5" section.
	
	Question: If URLScan-SRP protects me against all vulnerabilities in the Microsoft
	Security Bulletin MS02-018, is it necessary to apply the patches specified in
	the Microsoft Security Bulletin MS02-018?
	Answer: Yes, it is absolutely necessary. Patches provide the ultimate fix to this
	vulnerability. Microsoft strongly recommends that you apply the Security Rollup
	patch as soon as possible to protect from any existing vulnerability.
	
	Question: I am not sure if I am using chunk encoding in any of my custom
	applications. What is it?
	Answer: Chunked transfer encoding transmits the message body to the client as
	chunks that are stamped with their size. This allows the client to ensure that
	it has received all of the data that was sent from the server. Chunked transfer
	encoding is similar to MIME encoding in relation to Internet mail. For more
	information, refer to RFC 2616.
	
	Question: Will there be more updates to the URLScan security tool?
	Answer: Yes, Microsoft continually makes changes to their tools and products in
	response to customers' needs and the changing landscape of security.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbSecurity KbSECTools 
	Technology        : kbiisSearch kbiis500 kbiis400 kbiis510
	Version           : :4.0,5.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
