---
layout: page
title: "Q190212: BUG: Add-Ins Only Visible to the User Who Installs VB"
permalink: /kb/190/Q190212/
---

## Q190212: BUG: Add-Ins Only Visible to the User Who Installs VB

{% raw %}

	Article: Q190212
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): kbGrpDSVB
	Last Modified: 16-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you install Visual Basic and log on to the machine as a different user
	(with or without administrator privileges), you cannot see any Add-Ins in the
	Add-In dialog in Visual Basic.
	
	CAUSE
	=====
	
	Visual Basic retrieves available Add-Ins based on the CurrentUser Settings in
	the Registry. When a user logs on to a machine and launches Visual Basic, Visual
	Basic determines which Add-ins to load by checking on the CurrentUser keys.
	Because users who log on to the system have their individual settings, Visual
	Basic will load Add-Ins differently for different users.
	
	RESOLUTION
	==========
	
	To resolve the issue the Add-Ins need to be registered for each user. There are
	two possible ways to update the registry with the necessary information:
	
	- Manually register each Add-In for each user using the Regsvr32.exe utility.
	  For example, the following command line shows how to register the Package and
	  Deployment Wizard Add-In:
	
	  <Path to regsvr32.exe>\regsvr32.exe <Path to Add-In>\pdaddin.dll
	
	  NOTE: The above line should be modified to reflect the correct path
	  information.
	
	  This workaround would have to be done by each user and for each Add-In the
	  user requires. For a list of available Add-Ins and where they are located
	  please see the "More Information" section in this article.
	
	- Export the necessary registry entries and import them into the registry while
	  logged in as the appropriate user. The steps below describe how to do this:
	
	Step-By-Step
	------------
	
	IMPORTANT: This article contains information about editing the registry. Before
	you edit the registry, make sure you understand how to restore it if a problem
	occurs. For information about how to do this, view the "Restoring the Registry"
	Help topic in Regedit.exe or the "Restoring a Registry Key" Help topic in
	Regedt32.exe.
	
	1. Log in to the machine using the installing users account.
	
	2. Run the Registry Editor, RegEdit.Exe.
	
	3. Locate the following registry key:
	
	  HKEY_CURRENT_USER\Software\Microsoft\Visual Basic\6.0\Addins
	
	4. Choose Export Registry File from the Registry menu to create a .Reg file.
	
	5. Follow steps 3 and 4 again for the following key:
	
	  HKEY_CURRENT_USER\Software\Microsoft\Visual Basic\6.0\AddInToolbar
	
	6. Logoff the NT machine.
	
	7. Log on as a different user.
	
	8. Locate and double click the two .Reg files created above to update the
	  registry with the proper information.
	
	Once all the Add-Ins are available to you, you may run into the following error
	when you attempt to create a data form in the Application Wizard:
	
	  You do not have the proper license to load the Data Form Wizard. You must
	  have the Professional or Enterprise edition of Visual Basic Installed!
	
	To resolve this error, follow these steps:
	
	1. Log into your computer as a user who is a member of the Administrators group.
	
	2. Click the Start button, and then click Run. In the Open box, type "regedt32"
	  (without the quotation marks), and then click OK.
	
	3. In the HKEY_LOCAL_MACHINE window, double-click Software, then double-click
	  Classes, and then double-click Licenses.
	
	4. While Licenses is open, click Permissions on the Security menu.
	
	5. In the Registry Key Permissions dialog box, click to select the "Replace
	  Permission on Existing Subkeys" check box. In the Name list, click Everyone
	  once so it is selected, and then click Full Control in the Type Of Access
	  list. Click OK.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	The following table shows where the Add-In files are located.
	
	NOTE: The locations below should be preceded with the following path:
	
	  c:\program files\microsoft visual studio
	
	The above path assumes Visual Basic was installed to its default location.
	
	Add-In Name                          Location
	-----------------------------------------------------------------------
	Package And Deployment Wizard        \VB98\Wizards\PDWizard\PDADDIN.DLL
	VB 6 ActiveX Ctrl Interface Wizard   \VB98\Wizards\CTRLWIZ.DLL
	VB 6 ActiveX Doc Migration Wizard    \VB98\Wizards\AXDOCWIZ.DLL
	VB 6 Add-In Toolbar                  \VB98\Wizards\AITOOL.DLL
	VB 6 Application Wizard              \VB98\Wizards\APPWIZ.OCX
	VB 6 Class Builder Utility           \VB98\Wizards\CLSSBLD.DLL
	VB 6 Data Form Wizard                \VB98\Wizards\DATAFORM.OCX
	VB 6 Data Object Wizard              \VB98\Wizards\MSDATOBJ.DLL
	VB 6 Property Page Wizard            \VB98\Wizards\PROPPGWZ.DLL
	VB 6 Resource Editor                 \VB98\Wizards\RESEDIT.DLL
	VB 6 Template Manager                \VB98\Wizards\TEMPMGR.DLL
	VB 6 Wizard Manager                  \VB98\Wizards\WIZMAN.DLL
	VB T-SQL Debugger                    \VB98\Tsql\VBSDIADD.DLL
	Visual Component Manager 6.0         \Common\Tools\VCM\VCMMGR.DLL
	Visual Modeler Add-In                \Common\Tools\VS-Ent98\vmodeler\ 
	                                       RVBADDIN.DLL
	Visual Modeler Menus Add-In          \Common\Tools\VS-Ent98\vmodeler\ 
	                                       RVBADDINMENUS.DLL
	                                    \Common\Tools\VS-Ent98\vmodeler\ 
	                                       RVBRESO.DLL
	
	Additional query words: kbDSupport kbAddIn kbdss kbVBp600bug kbVBp
	
	======================================================================
	Keywords          : kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : :6.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
