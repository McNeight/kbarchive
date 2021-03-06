---
layout: page
title: "Q295084: SMS: Program Does Not Run if User Is Not Logged On"
permalink: /kb/295/Q295084/
---

## Q295084: SMS: Program Does Not Run if User Is Not Logged On

{% raw %}

	Article: Q295084
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0 SP3
	Operating System(s): 
	Keyword(s): kbenv kbtool kbClient kbConfig kbsms200 kbsms200bug kbAdvertisement kbPackage kbSoftwar
	Last Modified: 09-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 SP3 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to send a program that should run whether a user is logged on or
	not and the program properties specify "SMS Restarts computer", the program may
	not run until a user logs on. The following error message may be logged in the
	Smsapm32 log file on the client computer:
	
	  SCHEDULER : Found a job in the scheduled job list with program index 0.
	  SCHEDULER : ODP, dependent program, or program removal data is available for
	  this job.
	  SCHEDULER : The program is available for this job.
	  SCHEDULER : This job needs to be run when a user is logged on.
	  SCHED DATA : This job can execute whether the user is logged on or not.
	  SCHED DATA : Checking if a countdown dialog should be required at this time.
	  SCHEDULER : Checking if a user is actually logged on.
	  SCHEDULER : A user is not logged on to the system.
	  SCHED DATA : This job does not require a countdown dialog.
	  SCHEDULER : The monitor has not yet connected and registered the logged on
	  user.
	  SCHEDULER : This job requires the monitor to present a dialog box.
	  SCHEDULER : Moving this job from the schedule to trigger job list.
	  SCHEDULER : Inserting the job into the Triggered Events list.
	  SCHEDULER : Removing the job from the Scheduled Events list.
	  SCHEDULER : When the user logs on at some time in the future the monitor will
	  be available and this job will be moved back into the schedule job list.
	
	CAUSE
	=====
	
	This problem was introduced in a post Systems Management Server (SMS) version
	2.0 Service Pack 2 (SP2) hotfix. This problem is also noted in Service Pack 3.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Systems Management
	Server version 2.0. For additional information, please see the following article
	in the Microsoft Knowledge Base:
	
	  Q288239 SMS: How to Obtain the Latest Systems Management Server 2.0 Service
	  Pack
	
	
	
	WORKAROUND
	==========
	
	To work around this problem, do not specify "SMS restarts computer" within the
	program properties.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article. This problem was first corrected in
	Systems Management Server 2.0 Service Pack 4.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbenv kbtool kbClient kbConfig kbsms200 kbsms200bug kbAdvertisement kbPackage kbSoftwareDist kbsms200preSP4fix 
	Technology        : kbSMSSearch kbSMS200SP3
	Version           : :2.0 SP3
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
