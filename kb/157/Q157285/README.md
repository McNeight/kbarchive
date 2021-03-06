---
layout: page
title: "Q157285: STL Sample for the Predicate Persion of upper_bound Function"
permalink: /kb/157/Q157285/
---

## Q157285: STL Sample for the Predicate Persion of upper_bound Function

{% raw %}

	Article: Q157285
	Product(s): Microsoft C Compiler
	Version(s): winnt:
	Operating System(s): 
	Keyword(s): _IK
	Last Modified: 05-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Standard C++ Library, included with:
	   - *EDITOR Please do not choose this product*Microsoft Visual C++ 32-bit Edition* use 241, 265, 225, version 4.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The sample code below illustrates how to use the predicate version of
	upper_bound STL function in Visual C++.
	
	MORE INFORMATION
	================
	
	Required Header
	---------------
	
	     <algorithm>
	
	Prototype
	---------
	
	     template<class ForwardIterator, class T, class Compare> inline
	         ForwardIterator upper_bound(ForwardIterator first,
	                                     ForwardIterator last,
	                                     const T& value,
	                                     Compare compare)
	
	NOTE: The class/parameter names in the prototype do not match the original
	version in the header file. They have been modified to improve readability.
	
	Description
	-----------
	
	The upper_bound algorithm returns the last location in the sequence that value
	can be inserted such that the order of the sequence [first..last) is
	maintained.
	
	upper_bound returns an iterator positioned at the location that value can be
	inserted in the range [first..last), or returns last if no such position
	exists.
	
	This version assumes the range [first..last) is sorted sequentially using the
	compare function.
	
	Sample Code
	-----------
	
	  ////////////////////////////////////////////////////////////////////// 
	  // 
	  // Compile options needed: /GX
	  // 
	  // upper_bound.cpp : Illustrates how to use the predicate version
	  //                   of the upper_bound function.
	  // 
	  // Functions:
	  // 
	  //    upper_bound : Return the upper bound within a range.
	  // 
	  // Written by Kalindi Sanghrajka
	  // of Microsoft Product Support Services,
	  // Software Core Developer Support.
	  // Copyright (c) 1996 Microsoft Corporation. All rights reserved.
	  ////////////////////////////////////////////////////////////////////// 
	
	  // disable warning C4786: symbol greater than 255 character,
	  // okay to ignore
	  #pragma warning(disable: 4786)
	
	  #include <iostream>
	  #include <algorithm>
	  #include <functional>
	  #include <vector>
	  using namespace std;
	
	  void main()
	  {
	      const int VECTOR_SIZE = 8 ;
	
	      // Define a template class vector of int
	      typedef vector<int, allocator<int> > IntVector ;
	
	      //Define an iterator for template class vector of strings
	      typedef IntVector::iterator IntVectorIt ;
	
	      IntVector Numbers(VECTOR_SIZE) ;
	
	      IntVectorIt start, end, it, location ;
	
	      // Initialize vector Numbers
	      Numbers[0] = 4 ;
	      Numbers[1] = 10;
	      Numbers[2] = 70 ;
	      Numbers[3] = 10 ;
	      Numbers[4] = 30 ;
	      Numbers[5] = 69 ;
	      Numbers[6] = 96 ;
	      Numbers[7] = 100;
	
	      start = Numbers.begin() ;   // location of first
	                                  // element of Numbers
	
	      end = Numbers.end() ;       // one past the location
	                                  // last element of Numbers
	
	      //sort Numbers using the function object less<int>()
	      //upper_bound assumes that Numbers is sorted
	      //using the "compare" (less<int>() in this case)
	      //function
	      sort(start, end, less<int>()) ;
	
	      // print content of Numbers
	      cout << "Numbers { " ;
	      for(it = start; it != end; it++)
	          cout << *it << " " ;
	      cout << " }\n" << endl ;
	
	      //return the highest location at which 10 can be inserted
	      // in Numbers
	      location = upper_bound(start, end, 10, less<int>()) ;
	
	      cout << "Last location  for element 10 in Numbers is: "
	          << location - start << endl ;
	  }
	
	Program Output is:
	
	Numbers { 4 10 10 30 69 70 96 100  }
	
	Last location for element 10 in Numbers is: 3
	
	REFERENCES
	==========
	
	Visual C++ Books On Line: Visual C++ Books:C/C++:Standard C++ Library Reference.
	
	Additional query words: STL upper_bound
	
	======================================================================
	Keywords          : _IK 
	Technology        : kbVCsearch kbAudDeveloper kbVCLibrary
	Version           : winnt:
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
