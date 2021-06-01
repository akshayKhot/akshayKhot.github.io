---
layout: post
title: Introduction to SQL Server Reporting Services (SSRS)
server: ssrs/report_server.png
portal: ssrs/web_portal.png
tags: ssrs
---

Brian Larson's [Microsoft SQL Server 2016 Reporting Services](https://learning.oreilly.com/library/view/microsoft-sql-server/9781259641510/) provides a thorough overview of the SSRS technology. I have tried to summarize the essentials from the book into easy-to-digest blog posts. Here is the post on the first chapter. 

Reporting Services provides an environment for creating different types of reports from several different data sources. The reports are deployed to a **report server**, making the reports available via the Internet in a structured, secure environment. The report management and distribution portion of Reporting Services is free of charge when installed on a server already running SQL Server.

When Reporting Services renders a report, it gathers the most recent data from the database, formats the data in the manner the report’s author specifies, and outputs the report into the selected format (that is, HTML, PDF, TIFF, and so on). You can configure a report to query the database every time it is accessed. This ensures the report is always up to date.

SSRS reports are created using either the **Report Builder** or the **Report Designer**.

- **The Report Builder** supports the construction of full-featured Reporting Services reports. It features a user interface similar to that of Microsoft Word 2013 or Microsoft Excel 2013.
- **The Report Designer,** found in SQL Server Data Tools and Visual Studio, also supports all of the features of Reporting Services. In addition, it provides tools for project organization and source-code management for those reporting projects that have a lifecycle similar to that of a software development project (version control, check-in/check-out, etc.).

Each SSRS report contains two distinct sets of instructions that determine what the report will contain. 

- **Data Definition**
  - Controls where the data for the report will come from (**data source**) and what information will be selected from that data (**dataset**). 
  - When the report executes, it uses the data source instructions in the report to gain access to the database. It then extracts information from the database into a new format that the report can use. This new format is called a dataset*.*
  - The content of the dataset is defined using **query designer.** It helps you to build a T-SQL query that fetches data from the database. The dataset only contains the query and other metadata but not the actual data, which will be fetched from the database when the report is run.
- **Report Layout**
  - Controls how the information will be presented on the screen or paper. It specifies which fields go in which locations on the screen or paper. You can also add titles, headings, and page numbers. 
  - A report layout also has a data region that displays all the rows in the dataset by repeating a section of the report layout for each row.

Both of these sets of instructions are stored in the Report Definition Language.

**Report Definition Language** ([RDL](https://docs.microsoft.com/en-us/sql/reporting-services/reports/report-definition-language-ssrs?view=sql-server-ver15)): An XML representation of an SSRS report definition. A report definition contains **data retrieval and layout information** for a report. When you create a report in the Report Designer, it is saved in a file with a .rdl extension. 

### Report Server

When you finish building the reports, you deploy or publish the report on a report server. 

<a target="_blank" href="{{ site.images }}/{{ page.server }}">
  <img src="{{ site.images }}/{{ page.server }}" alt="Report Server">
</a>  

1. Report Catalog
   - A set of databases used to store the definitions for all of the reports and other objects available on a particular report server. 
   - When a report is deployed to a report server, its definition is put in that server's report catalog. 
   - It also stores the configuration, security, and caching information. 
2. Report Processor
   - Acts as a controller to coordinate all the steps to build and execute the report. 
   - Retrieves an SSRS report from the Report Catalog and executes it.
3. Data Providers
   - The **report processor** uses the data source information to select a **data provider** that knows how to retrieve information from this type of data source. 
   - The data provider then connects to the database and then fetches the data to populate the dataset.
4. Renderers
   - After the data has been collected, the **report processor** processes the report layout. 
   - According to the format mentioned (HTML, PDF, etc.) the report processor selects the **renderer** that knows how to produce that format. 
   - The renderer combines the report layout with the dataset and outputs the requested output format. 
5. Request Handler
   - Receives the requests for reports and passes those requests to the report processor. 
   - Once the **report processor** has created the requested report using the data provider and renderer, the **request handler** delivers the report. 



### Report Delivery

Once a report is created, it can be delivered in different ways, depending on the type of request. It can be viewed on a web portal, sent as a response to a web service request, or e-mailed to a user who has subscribed to the report.

**A Web Portal**

When you install SSRS, a website is created for you. It looks as follows. Users can search reports and browse through the folders to find the ones they need. The website also provides role-based security to folders and reports. 

The web portal always displays the reports in HTML format. The users can export the reports into other formats. You can also create the key performance indicators (KPIs) to embed onto the dashboard.

<a target="_blank" href="{{ site.images }}/{{ page.portal }}">
  <img src="{{ site.images }}/{{ page.portal }}" alt="Web Portal">
</a>  



**E-mail Subscriptions**

If the users don't want to visit the web portal, they can subscribe to their reports (using the web portal). The request handler then e-mails the reports to the subscribers. The report can either be embedded in the e-mail body or included as an attachment, depending on the requested format.

Rather than each user having to subscribe to the reports, the report administrator can also create a reporting newsletter, where reports are mailed to a set of users. 

**Web Services**

Web services allow two programs to communicate with each other over the internet. The request handler can send the report as a response to web service requests, both from a human or a program.

Using web services, a program sends a request to the report server, requesting a particular report. The request handler forwards this request to the report processor just as it would for a request from the web portal. The completed report is returned as a response to the web service request.  