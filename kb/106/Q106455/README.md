---
layout: page
title: "Q106455: HOWTO: Acquire a List of All CDocument Objects"
permalink: /kb/106/Q106455/
---

## Q106455: HOWTO: Acquire a List of All CDocument Objects

{% raw %}

	Article: Q106455
	Product(s): Microsoft C Compiler
	Version(s): 1.0,1.5,1.51,1.52,2.0,2.1,2.2,4.0
	Operating System(s): 
	Keyword(s): kbDocView kbMFC kbVC kbGrpDSMFCATL
	Last Modified: 27-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++ for Windows, 16-bit edition, versions 1.0, 1.5, 1.51, 1.52 
	   - Microsoft Visual C++, 32-bit Editions, versions 1.0, 2.0, 2.1, 2.2, 4.0 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	The code samples below demonstrate how to retrieve a list of pointers to all
	open CDocument (and CDocument-derived objects) created by a CWinApp-derived
	object. For MFC versions 3.x and below, Sample Code 1 shows the use of
	CWinApp::m_templateList, CDocTemplate::GetFirstDocPosition(), and
	CDocTemplate::GetNextDoc(). For MFC version 4.0, Sample Code 2 provides a
	similar implementation, but uses CWinApp::GetFirstDocTemplatePosition() and
	CWinApp::GetNextDocTemplate() to obtain the valid CDocTemplate pointers.
	
	For both code samples, CMyApp is derived from CWinApp. Moreover, once a valid
	CDocTemplate pointer is obtained, CDocTemplate::GetFirstDocPosition() and
	CDocTemplate::GetNextDoc() are used in both samples to iterate through the list
	of open documents for each document template. For MFC versions 3.x and earlier,
	an application object's list of document template pointers is contained in
	CWinApp::m_templateList, a CPtrList object. Sample Code 1 makes use of this
	fact. For MFC version 4.0, CWinApp uses a CDocManager to maintain its list of
	document templates and provides the GetFirstDocTemplatePosition() and
	GetNextDocTemplate() member functions to traverse the list. Sample Code 2
	exhibits this.
	
	Sample Code 1 - MFC 3.x and prior
	---------------------------------
	
	  /* Compile options needed: none
	  */ 
	
	  void CMyApp::GetDocumentList(CObList * pDocList)
	  {
	     ASSERT(pDocList->IsEmpty());
	
	     POSITION pos = m_templateList.GetHeadPosition();
	
	     while (pos)
	     {
	        CDocTemplate* pTemplate = (CDocTemplate*)m_templateList.GetNext(pos);
	        POSITION pos2 = pTemplate->GetFirstDocPosition();
	        while (pos2)
	        {
	           CDocument * pDocument;
	           if ((pDocument=pTemplate->GetNextDoc(pos2)) != NULL)
	              pDocList->AddHead(pDocument);
	        }
	     }
	  }
	
	Sample Code 2 - MFC 4.0
	-----------------------
	
	  /* Compile options needed: none
	  */ 
	
	  void CMyApp::GetDocumentList(CObList * pDocList)
	  {
	     ASSERT(pDocList->IsEmpty());
	
	     POSITION pos = GetFirstDocTemplatePosition();
	
	     while (pos)
	     {
	        CDocTemplate* pTemplate = (CDocTemplate*)GetNextDocTemplate(pos);
	        POSITION pos2 = pTemplate->GetFirstDocPosition();
	        while (pos2)
	        {
	           CDocument * pDocument;
	           if ((pDocument=pTemplate->GetNextDoc(pos2)) != NULL)
	              pDocList->AddHead(pDocument);
	        }
	     }
	  }
	
	MORE INFORMATION
	================
	
	The Visual C++ version 4.0 Books Online document all of the following
	functions:
	
	- CWinApp::GetFirstDocTemplatePosition
	
	- CWinApp::GetNextDocTemplate
	
	- CDocTemplate::GetFirstDocPosition
	
	- CDocTemplate::GetNextDoc
	
	However, the GetFirstDocPosition and GetNextDoc member functions of CDocTemplate
	are not documented in previous versions of Visual C++. These public member
	functions are defined in the CDocTemplate class and provide simple functionality
	for traversing the list of open documents as shown above. These functions
	operate as follows:
	
	CDocTemplate::GetFirstDocPosition Function:
	
	Declaration: virtual POSITION GetFirstDocPosition() const;
	
	Remarks:
	Call this function to get the position of the first document in the list of open
	documents associated with the template.
	
	Return Value:
	A POSITION value that can be used for iteration with the GetNextDoc member
	function.
	
	CDocTemplate::GetNextDoc Funcation:
	
	Declaration: virtual CDocument* GetNextDoc(POSITION& rPosition) const;
	
	rPosition:
	A reference to a POSITION value returned by a previous call to the GetNextDoc or
	GetFirstDocPosition member function. This value must not be NULL.
	
	Remarks:
	Call this function to iterate through all of the document template's open
	documents. The function returns the document identified by rPosition and then
	sets rPosition to the POSITION value of the next document in the list. If the
	retrieved document is the last in the list, then rPosition is set to NULL.
	
	Return Value:
	A pointer to the view identified by rPosition.
	
	Additional query words: kbinf 1.00 1.50 2.00 2.10 2.20 2.50 2.51 2.52 3.00 4.00
	
	======================================================================
	Keywords          : kbDocView kbMFC kbVC kbGrpDSMFCATL 
	Technology        : kbAudDeveloper kbMFC
	Version           : :1.0,1.5,1.51,1.52,2.0,2.1,2.2,4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
