# Welcome to the ReEntry412 wiki!

## Introduction

This repository belongs to the Pittsburgh-based nonprofit, ReEntry412. The NewERA412 platform was built by student consultants in 67-373, Information Systems Consulting Project, @ Carnegie Mellon University.

The project is now maintained by <a href="mailto:jlucas@workhardpgh.com">Josh Lucas</a> and the fine tech staff at <a href="https://workhardpgh.com">WorkHardPgh</a>

***

## Quick Summary 

The system serves ReEntry412 in two capacities. 
1. As an accessible platform for searchable NewERA resources
2. As a CRM internal to the organization 

### Main Features
* Publically displaying, searching, and filtering system Resources (+`CRUD`)
* User management (`CRUD`) for two types of users:
  1. __Street Outreach Workers:__ only able to view resources, create referrals, and manage their caseload
  2. __Admins:__ are given complete CRUD privileges as well as access to backend KPI's
* CaseLoadUser management, where system SOWs/Admins can add constituents to their caseloads (`CRUD`)
* Referral Creation: 
  1. __In System:__ An Admin/SOW can refer a CaseLoadUser some system resources (via phone or email)
  2. __Out of System:__ Ditto but no CaseLoadUser object is needed (only a phone or email)
  * __NOTE:__ Referral notification links are used to confirm whether a user accessed a sent referral. This is done by hardcoding a query param into the URL's link, then matching it with a referral in the backend. See documentation on the Resource#index action for more info.
* EMAIL/SMS Notifications: When a referral is made, the end-user is notified 
  1. __via Email:__ using `django.core.mail`
  2. __via SMS:__ using an API key for the `Twilio messaging service`
* KPI Exports: system KPI's are aggregated and exported to Excel
* Unique Visit Tracking: Unique visits to site resources are tracked in the backend. The server checks the visitor's cookie, and increments the view count depending on whether their browser has see a particular resource or not. 
* Password Resets: via the basic `django.contrib.auth` library

***

## Internal Documentation (code-level)

## External Documentation (general onboarding docs) 
* Onboarding documents:
1. <a href="https://docs.google.com/document/d/14lV7LetxAvPJ9m-_OqEKzMIXFnvkgHvxLV6P2vAvPdE/edit?usp=sharing">NewERA412 SOW Training Document (view only)</a>
