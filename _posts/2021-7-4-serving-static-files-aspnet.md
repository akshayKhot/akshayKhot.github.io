---
layout: post
title: Service Static Files in ASP.NET
tags: dotnet aspnet
---

One of the changes from ASP.NET MVC to  ASP.NET Core is that the latter doesn't have built-in support for static files, i.e. HTML, CSS, JavaScript, and images that are served directly to the users without any dynamic computation. To serve static files from an ASP.NET Core app, you must configure [static files middleware](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/static-files).

In ASP.NET Core, the web root directory holds the static files. By default, it is the `{content root}/wwwroot directory`, but you can change it using the `UseWebRoot()` method. 

In the Program class, the `CreateDefaultBuilder()` method initializes the content root. 

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }
 
    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseStartup<Startup>();
            });
}
```

You can have different directories for each type of file that your application serves. For example, a directory named **css** holds the stylesheets, another one named **js** serves the JavaScript that your application uses, etc. 

The directories within the **wwwroot** directory are directly accessed via a path relative to the host. For example, if you store your images in **wwwroot/pictures** directory, the users can access the images by the following URL: **https://<host_name>/images/<image_name>**

`UseStaticFiles()` method in the `Startup.Configure()` method enables static file serving for the current request path. 

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }
    else
    {
        app.UseExceptionHandler("/Home/Error");
        app.UseHsts();
    }
    app.UseHttpsRedirection();
    
    app.UseStaticFiles();

    app.UseRouting();

    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapControllerRoute(
            name: "default",
            pattern: "{controller=Home}/{action=Index}/{id?}");
    });
}
```

When you call the Static File Middleware before the authorization middleware, the framework doesn’t perform any authorization checks on the static files getting served. Hence the files under **wwwroot** directory are publicly accessible. 

If you want to authorize the requests before serving the static files, you need to store them outside the **wwwroot** directory and call the Static File Middleware after the call to `UseAuthorization()`.

