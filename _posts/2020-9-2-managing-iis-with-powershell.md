---
layout: post
title: Managing IIS with PowerShell
tags: programming
---

With Windows 10 and Windows Server 2016, a new and simplified IISAdministration module was released side by side with the existing WebAdministration Cmdlets. The new module contains simple cmdlets and provides direct access to the server manager. It also offers better support for pipeline and scaling. 

Though you can manage IIS with the IIS Manager GUI, using PowerShell gives you much more control, is much more convenient and can be easily automated. Here's a brief overview of the basic IIS management with PowerShell.  

Create a directory for your site. I will name my site 'CityOverflow'

```powershell
New-Item -ItemType Directory -Name 'CityOverflow' -Path 'C:\Sites'
```

Create the index.html that will be served when you go to your site

```powershell
New-Item -ItemType File -Name 'index.html' -Path 'C:\Sites\CityOverflow'
```

Add some HTML content to your landing page. 

```powershell
Add-Content -Path 'C:\Sites\CityOverflow\index.html' -Value "<h1>Hello World</h1>"
```

So far, we haven't used any IIS-specific features. We have just created a directory for our site that contains HTML. You can do that by using your favourite editor. I just wanted to show the basic PowerShell commands that do the same. 

Now, let's create a new IIS site that will serve our CityOverflow website. 

```powershell
New-IISSite -Name 'CityOverflow' -PhysicalPath 'C:\Sites\CityOverflow\' -BindingInformation '*:8000:'
```

Once the IIS site is created, run Get-IISSite to get information about that site. 

```powershell
Get-IISSite

Name             ID   State      Physical Path                  Bindings
----             --   -----      -------------                  --------
CityOverflow     2    Started    C:\Sites\CityOverflow\         http *:8000:
```

That's it. If you navigate to localhost:8000 in your browser, you will see the web page you just created. 

To stop a running site, use the Stop-IISSite cmdlet, providing the name of the site. 

```powershell
Stop-IISSite -Name "CityOverflow"

Confirm
Are you sure you want to perform this action?
Performing the operation "Stop-IISSite" on target "CityOverflow".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
```

To start the site again, run the Start-IISSite cmdlet.

```powershell
Start-IISSite -Name "CityOverflow"
```

If you have more than one site, you can start/stop all of them by piping the output of Get-IISSite to either StartIISSite or Stop-IISSite. 

```powershell
Get-IISSite | Start-IISSite
```

To remove a site, run Remove-IISSite. 

```powershell
Remove-IISSite -Name 'CityOverflow'
```