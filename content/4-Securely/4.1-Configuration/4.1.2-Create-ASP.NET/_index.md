---
title : "Create ASP.NET Core project"
date: "2025-05-29"
weight : 2
chapter : false
pre : " <b> 4.1.2 </b> "
---


Create new *ASP.NET Core Web API*.

![ConnectPrivate](/images/4-Securely/4.4.png)

Name your project *ParameterStoreDemo*

Choose *.NET 8.0* and remove HTTPS support:

![ConnectPrivate](/images/4-Securely/4.5.png) 

Once project is created, add *Amazon.Extensions.Configuration.SystemsManager* Nuget package to the project.

![ConnectPrivate](/images/4-Securely/4.6.png)

Next you need to enable new configuration provider in the code.

For an ASP.NET Core application, you can do this in the *Program.cs* file by adding the following line before the var *app = builder.Build();*:

```csharp
    builder.Configuration.AddSystemsManager("/SampleApp");
```

Add another API to read connection string from the configuration by adding the following code to to *Program.cs* file before *app.Run();*:

```csharp
        app.MapGet("/connection", (IConfiguration configuration) =>
    {
        var connectionString = configuration.GetConnectionString("MyConnection");

        return connectionString;
    });
```

Build & Run the project and verify that connection string is displayed in decrypted form.

![ConnectPrivate](/images/4-Securely/4.7.png)

Congratulations! You have successfully configured AWS Systems Manager configuration source provider and retrieved parameter from the parameter store using standard IConfiguration interface.