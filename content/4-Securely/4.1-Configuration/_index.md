---
title : "Use .NET Core Configuration"
date: "2025-05-29"
weight : 1
chapter : false
pre : " <b> 4.1 </b> "
---

Configuration in .NET Core is quite different from what you were used to in the .NET Framework. With the .NET Framework, you had only app.config/web.config as our configuration source and, for any other sources, you had to create your custom configuration solution.

The .NET Core configuration system was built to be extensible. For example, when you create an ASP.NET Core application, by default it pulls configuration information from your **appsettings.json file**, command line arguments, and environment variables. You can also plug in other configuration source providers and then let your application access the configuration with the same interface.

AWS provides NuGet package, **Amazon.Extensions.Configuration.SystemsManager** that simplifies how your application loads the application configuration settings in the AWS Systems Manager Parameter Store into the .NET Core configuration system.