---
layout: page
title: "Q155690: Regaut.exe Registers an Automation Object as Active"
permalink: /kb/155/Q155690/
---

## Q155690: Regaut.exe Registers an Automation Object as Active

{% raw %}

	Article: Q155690
	Product(s): Microsoft C Compiler
	Version(s): 2.0,2.1,2.2,4.0,4.1,4.2,5.0,6.0
	Operating System(s): 
	Keyword(s): kbfile kbole kbSample kbActiveX kbAutomation kbCOMt kbMFC kbRegistry kbVC200 kbVC400 kb
	Last Modified: 02-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, versions 2.0, 2.1, 2.2, 4.0, 4.1 
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 4.2, 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, versions 4.2, 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Regaut.exe is a sample Microsoft Foundation Classes (MFC) Appwizard- generated
	application that shows how to register a running object as active in the running
	object table (ROT) so that multiple clients can connect to it. The CDocument
	derived class CRegautDoc of this sample acts as the automation object, which is
	registered in the running object table every time a new document is created or
	an existing document is opened. By registering its document as active, this
	sample application demonstrates how multiple clients can attach to a single
	automation object in a local server and share its data.
	
	MORE INFORMATION
	================
	
	The following files are available for download from the Microsoft Download
	Center:
	
	Visual C++ 6.0:
	
	  DownloadDownload Regaut.exe now
	  (http://download.microsoft.com/download/vc60std/Sample1/1/WIN98/EN-US/Regaut.exe)
	
	For additional information about how to download Microsoft Support files, click
	the following article number to view the article in the Microsoft Knowledge
	Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft scanned this file for viruses. Microsoft used the most current
	virus-detection software that was available on the date that the file was
	posted. The file is stored on secure servers that prevent any unauthorized
	changes to the file.
	
	Visual C++ 6.0:
	
	  DownloadDownload Regautvcnet.exe now
	  (http://download.microsoft.com/download/VisualStudioNET/sample/1.22/WIN98MeXP/EN-US/Regautvcnet.exe)
	
	Release Date: June 26, 2002
	
	For additional information about how to download Microsoft Support files, click
	the following article number to view the article in the Microsoft Knowledge
	Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft scanned this file for viruses. Microsoft used the most current
	virus-detection software that was available on the date that the file was
	posted. The file is stored on secure servers that prevent any unauthorized
	changes to the file.
	
	
	NOTE: Use the -d option when running Regaut.exe to decompress the file and
	re-create the proper directory structure.
	
	The Regaut sample includes a Visual Basic client application called Vbclient.exe.
	Vbclient.exe tries to attach to the Regaut server's document by calling the
	Visual Basic GetObject API, which looks for the object in the ROT; if that
	fails, it creates the object using the Visual Basic CreateObject API. Once the
	first Vbclient.exe has been started, more instances of Vbclient.exe can be
	started, which attach to the already running Regaut document. All instances of
	Vbclient.exe share the same automation object. A C++ version of Vbclient.exe,
	Vcclient.exe, is also included.
	
	Another way to use this sample is to start the Regaut.exe application. After
	Regaut is running, start as many instances of Vbclient.exe as you want. All of
	these instances attach to the already running Regaut document. Each instance of
	Vbclient.exe can retrieve and change the Regaut document's data. When the
	Vbclient.exe applications are done accessing the Regaut document's data, they
	can shut down, leaving Regaut running with its document containing the data from
	the last Vbclient.exe that changed Regaut's data.
	
	Regaut.exe also demonstrates the correct way to leave an automation server
	running if the automation client makes the automation server's application
	window visible. If during the course of automating a server, a client makes the
	server[ASCII 146]s application window visible, the server should shut down only
	in response to an explicit user or automation client command (such as the Exit
	command from the File menu or the equivalent).
	
	The CRegautDoc::RegisterAsActive() function registers the Regaut document as
	active when a new document is created or when an existing document is opened. It
	does this by registering The CRegautDoc's IUnknown pointer in the running object
	table using the OLE API RegisterActiveObject. RegisterActiveObject has the
	following prototype:
	
	     HRESULT RegisterActiveObject (IUnknown FAR* punk,
	                                   REFCLSID rclsid,
	                                   DWORD dwFlags,
	                                   unsigned long FAR* pdwRegister);
	
	NOTE: punk is the IUnknown * for the object we want to register. You get this
	pointer in Regaut by calling CCmdTarget::GetControllingUnknown().
	
	The rclsid parameter is the clsid of the local server, which OLE uses to identify
	this object in the ROT. Automation clients use this clsid to search for this
	object in the ROT and to create this object. This clsid is generated by
	Appwizard when you choose the Automation support option while generating your
	application. It is created as a member variable of the CWinApp derived class, so
	Regaut just uses a helper function in CRegautApp to access this value from other
	classes.
	
	The dwFlags parameter specifies how you would like to register the active object
	in the running object table. You can either register with a strong lock
	ACTIVEOBJECT_STRONG or a weak lock ACTIVEOBJECT_WEAK. For automation objects,
	ACTIVEOBJECT_WEAK is almost always used. Online documentation for
	RegisterActiveObject in Visual C++ Books online has a detailed discussion of the
	differences between registering your automation object weak versus strong. You
	should be familiar with this documentation before you use RegisterActiveObject.
	Regaut.exe uses ACTIVEOBJECT_WEAK.
	
	The pdwRegister parameter is a value returned by OLE to RegisterActiveObject that
	is used in calls to RevokeActiveObject to explicitly remove an object's entry
	from the ROT.
	
	When a client application has connected to Regaut and wants to make it visible,
	the client calls the ShowWindow() method. Once the Regaut window is visible, the
	Regaut document makes sure the Regaut application stays running after the last
	client disconnects by calling AfxSetUserControl(TRUE). This ensures that
	Regaut.exe will not shut down after the last client detaches but does not ensure
	that the current document will close after the last client detaches.
	
	To ensure that the current document does not close, CRegautDoc calls
	CoLockObjectExternal(GetControllingUnknown(),TRUE,TRUE) to put an external lock
	on the document. When the user does decide to shut down the CRegaut application
	or otherwise close the document,
	CoLockObjectExternal(GetControllingUnknown(),FALSE,TRUE) is called to remove the
	external lock on the document object. The calls to AfxSetUserControl and
	CoLockObjectExternal ensure that the automation server behaves correctly if the
	application window becomes visible. Having the server's application window
	become visible is also known as putting the user in control.
	
	This article demonstrates registering an object on the Running Object Table (ROT)
	with the RegisterActiveObject API. RegisterActiveObject registers an object
	using that objects GUID. To uniquely identify objects of the same type on the
	ROT it is necessary to register the object with a moniker. Q152087 demonstrates
	how to register a moniker on the ROT with IRunningObject::Register however,
	please keep in mind the this is not what this sample was written to illustrate.
	
	REFERENCES
	==========
	
	Visual C++ Books Online
	
	Additional query words:
	
	======================================================================
	Keywords          : kbfile kbole kbSample kbActiveX kbAutomation kbCOMt kbMFC kbRegistry kbVC200 kbVC400 kbVC500 kbVC600 kbGrpDSMFCATL 
	Technology        : kbVCsearch kbVC400 kbAudDeveloper kbVC220 kbVC410 kbVC420 kbVC500 kbVC600 kbVC200 kbVC210 kbVC32bitSearch kbVC500Search
	Version           : :2.0,2.1,2.2,4.0,4.1,4.2,5.0,6.0
	
	=============================================================================
	

{% endraw %}
