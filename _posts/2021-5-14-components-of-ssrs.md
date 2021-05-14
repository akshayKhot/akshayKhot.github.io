---
layout: post
title: Components of SSRS
tags: ssrs
---

SSRS has an architecture similar to a web application, consisting of a web server that serves responses to the clients who connect to it. Here are all the components that make up SQL Server Reporting System.  

**Reporting Service** is responsible for the two main interfaces with the report server. It contains the web portal application and provides a web services interface. It also provides the engine responsible for report rendering.

**Reporting Services Configuration Manager** can examine and modify the configuration settings. It can run on the computer hosting the reporting service and also allows remote administration if the service is running on another computer. 

**SQL Server Instance** is required to host the database. **SQL Server Agent** is also needed to execute scheduled jobs at a certain time. For example, e-mailing a report to its subscribers.

**The Report Server Database** stores the report catalog along with other information such as web portal folder structure and security settings. A **Temp DB Database** is also created as temporary storage for the SSRS operations. It holds the information such as current users on the portal as well as a cache for the recent reports.

You can create SSRS reports using **SQL Server Data Tools, Visual Studio,** or the **Report Builder**. There's no difference between the reports created by these tools.  

These components can be installed in the following three combinations:

1. **The full installation:** All the above components are installed. Typically used for development. 
2. **The server installation:** User when we are setting up SSRS on a production server. Reports are created somewhere else and deployed to the production server. Hence install only what you need. 
3. **The report author installation:** For users who are creating the SSRS reports. It includes SS Data Tools, Visual Studio, Report Builder, etc. 