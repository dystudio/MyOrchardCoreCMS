# MyOrchardCoreCMS

An Example of Creating a Orchard Core Content Management System Application using NuGet packages

## PDF Version of the Documentation
[Getting-Started-with-Orchard-Core.pdf](https://github.com/OrchardSkills/MyOrchardCoreCMS/files/3996013/Getting-Started-with-Orchard-Core.pdf)

# Getting Started with Orchard Core CMS using Visual Studio

![OrchardCMSBackground](https://user-images.githubusercontent.com/59172485/71376645-5e37a200-257f-11ea-9bb8-890825fec338.png)

## Introduction

In this article, you're going to see how easy it is to get Orchard Core running in your very own ASP.NET Core Web Application using Visual Studio. You’ll be using the power of the Orchard Core NuGet packages to simplify the process.

## Create a new ASP.NET Core Web Application

First, launch Visual Studio, and create a new ASP.NET Core Web Application:

![Getting-Started-with-Orchard-Core-001](https://user-images.githubusercontent.com/59172485/71376623-5b3cb180-257f-11ea-9955-5224e558e521.png)

Select the box button at the lower left of the screen, “Create a new project”.

![Getting-Started-with-Orchard-Core-002](https://user-images.githubusercontent.com/59172485/71376624-5bd54800-257f-11ea-811e-4e66f3440bc3.png)

Select the ASP.NET Core Web Application that is highlighted in blue and press the “Next” button.

![Getting-Started-with-Orchard-Core-003](https://user-images.githubusercontent.com/59172485/71376625-5bd54800-257f-11ea-9e34-0b026fc7ea5f.png)

Enter a project name, location, and a solution name. It’s customary to add a “.Web” to specify the project is a web application. The Solution can be whatever you decide. Anther customary practice is to put all the source code in a root “src” folder. Again, it’s up to you to decide how you want to structure your code.

![Getting-Started-with-Orchard-Core-004](https://user-images.githubusercontent.com/59172485/71376626-5bd54800-257f-11ea-95f6-44154c735e0d.png)

At the time of writing this article, Orchard Core is based on ASP.NET Core version 3.0. Make sure you select “ASP.NET Core 3.0” in the top right combo. Select the “Empty” template and then press the “Create” button.

## Create“NuGet.config”

In order to utilized the latest code, use the  dev packages, by adding the Orchard Core Preview Feed. Create the fie “NuGet.config” in the root folder and add the following configuration.

![Getting-Started-with-Orchard-Core-005](https://user-images.githubusercontent.com/59172485/71376627-5bd54800-257f-11ea-9905-ac0472782b27.png)

Nuget.config:

```
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <packageSources>
        <add key="Orchard Core Preview Feed" value="https://www.myget.org/F/orchardcore-preview/api/v3/index.json" />
    </packageSources>
</configuration>
```

## Modify Startup Code and Add the Orchard Core Preview Feed to your NuGet Package Manager Package Sources

![Getting-Started-with-Orchard-Core-006](https://user-images.githubusercontent.com/59172485/71376628-5bd54800-257f-11ea-8639-69af1d65e7f8.png)

Update code block to add Orchard Core CMS.

```
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Hosting;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;

namespace MyOrchardCoreCMS.Web
{
    public class Startup
    {
        // This method gets called by the runtime. Use this method to add services to the container.
        // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
        public void ConfigureServices(IServiceCollection services)
        {
            services.AddOrchardCms();
        }

        // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
        public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
        {
            if (env.IsDevelopment())
            {
                app.UseDeveloperExceptionPage();
            }

            app.UseOrchardCore();
        }
    }
}

```

Select the Include prerelease check box. Select the gear icon on the left side Package Source

![Getting-Started-with-Orchard-Core-007](https://user-images.githubusercontent.com/59172485/71376629-5c6dde80-257f-11ea-9fde-5751d854f2dc.png)

Verify the Orchard Core Preview Feed package source is the first entry and that the URL is correct.
Name: Orchard Core Preview Feed
Source: https://www.myget.org/F/orchardcore-preview/api/v3/index.json

## Install OrchardCore.Application.CMS.Targets

![Getting-Started-with-Orchard-Core-008](https://user-images.githubusercontent.com/59172485/71376630-5c6dde80-257f-11ea-91e9-9b9c693dc5ae.png)

Select the “Browse” tab in the NuGet Package Manager Window. Enter “OrchardCore.Application.CMS.Targets” in the Search edit box. Make sure the check box “Include prereleases is checked.

![Getting-Started-with-Orchard-Core-009](https://user-images.githubusercontent.com/59172485/71376632-5d067500-257f-11ea-9c05-415340aea316.png)

Select the package “OrchardCore.Application.CMS.Targets” and press the “install” button.

![Getting-Started-with-Orchard-Core-010](https://user-images.githubusercontent.com/59172485/71376633-5d067500-257f-11ea-845c-b5659a41b150.png)

Wait until all the packages are installed.

![Getting-Started-with-Orchard-Core-011](https://user-images.githubusercontent.com/59172485/71376634-5d067500-257f-11ea-924c-2e6c3a4b1fe5.png)

Allow Visual Studio to make changes by selecting the “OK” button.

![Getting-Started-with-Orchard-Core-012](https://user-images.githubusercontent.com/59172485/71376635-5d067500-257f-11ea-9019-5d32e8eefe52.png)

Select the “I Accept” button to accept the license agreement.

## Run the Application

![Getting-Started-with-Orchard-Core-013](https://user-images.githubusercontent.com/59172485/71376636-5d067500-257f-11ea-9376-8cde0769643a.png)

Select “MyOrchardCoreCMS.Web” and click on the green play button to run the application.

![Getting-Started-with-Orchard-Core-014](https://user-images.githubusercontent.com/59172485/71376637-5d9f0b80-257f-11ea-8748-af53e22b69f9.png)

Select “Yes” button to trust the self-signed certificate.

![Getting-Started-with-Orchard-Core-015](https://user-images.githubusercontent.com/59172485/71376638-5d9f0b80-257f-11ea-9b26-1f32f5d672db.png)

Select “Yes” button to trust the self-signed certificate.

![Getting-Started-with-Orchard-Core-016](https://user-images.githubusercontent.com/59172485/71376639-5d9f0b80-257f-11ea-9592-34dc809a1101.png)

A logging window will appear displaying debug information.

![Getting-Started-with-Orchard-Core-017](https://user-images.githubusercontent.com/59172485/71376640-5d9f0b80-257f-11ea-9196-dca6cb69e159.png)

Your Orchard Core application will then display a Setup page. Enter the “name of your site”, “Blog” for Recipe, your “default time zone”, “Sqlite” for the database, a “user name” and password. Press the “Finish Setup” button to complete the process.


![Getting-Started-with-Orchard-Core-018](https://user-images.githubusercontent.com/59172485/71376641-5d9f0b80-257f-11ea-9d24-3533943d6b26.png)

Navigate to the admin dashboard page by specifying “/admin” at the end of the URL. i.e. https://localhost:5001/admin. Login with your credentials.

![Getting-Started-with-Orchard-Core-019](https://user-images.githubusercontent.com/59172485/71376642-5d9f0b80-257f-11ea-8273-0948979177ab.png)

Congratulations! Your Orchard Core Web Application will now be running in the default web browser.

![Getting-Started-with-Orchard-Core-020](https://user-images.githubusercontent.com/59172485/71376643-5e37a200-257f-11ea-92d8-be8f58b84b4c.png)

Navigate to the admin dashboard page by specifying “/admin” at the end of the URL. i.e. https://localhost:5001/admin. Login with your credentials.

![Getting-Started-with-Orchard-Core-021](https://user-images.githubusercontent.com/59172485/71376644-5e37a200-257f-11ea-9663-d263321b903f.png)

You are now ready to configure and create content for your Orchard Core Web Application.

## Conclusion

With just a new few lines of code and some configuration, it is easy to create a Content Management System with ASP.NET Core and Orchard Core CMS.