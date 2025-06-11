---
title : "Create sample .NET 8 web application"
date: "2025-05-29"
weight : 3
chapter : false
pre : " <b> 7.3 </b> "
---


Now that you have installed .NET 8 SDK, you can create sample .NET web application:

Create new folder:

```csharp
    mkdir ~/awesomeapp
    cd ~/awesomeapp
```

Run *dotnet new webapp* command to create new project based on *webapp* template (ASP.NET Core Web App):

```csharp
    dotnet new webapp
```

Now you can build and run the generated sample .NET web application and expose it on port 5000:

```csharp
    dotnet run --urls=http://0.0.0.0:5000
```

Once you see the output like this, you can use your web browser to access it:

![ConnectPrivate](/images/7-Graviton/7.8.png) 

On the AWS Console page, click on the *EC2* link under the *Compute* section (or search for *EC2*) and locate your *EC2* instance. Copy public IPv4 address of the instance.

![ConnectPrivate](/images/7-Graviton/7.8.1.png)

Open Web browser and navigate to public IPv4 address of the instance, port 5000:

![ConnectPrivate](/images/7-Graviton/7.9.png)

Congratulations! You have .NET 8 web application is up and running on AWS Graviton instance!