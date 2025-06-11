---
title : "Create project"
date: "2025-05-29"
weight : 1
chapter : false
pre : " <b> 3.1 </b> "
---


Create new project using *AWS Serverless* Application (*.NET Core - C#*) template.

![ConnectPrivate](../../images/3-Amazon-API-Gateway/3.1.png)

![ConnectPrivate](../../images/3-Amazon-API-Gateway/3.2.png)

Select *ASP.NET Core Minimal API* blueprint.

![ConnectPrivate](../../images/3-Amazon-API-Gateway/3.3.png)

Take a look at the generated sample project:

- *aws-lambda-tools-defaults.json* file contains reference to the AWS Serverless Application Model (SAM) template that should be used to deploy serverless application
- *serverless-template* file contains AWS Serverless Application Model (SAM) template
  
![ConnectPrivate](../../images/3-Amazon-API-Gateway/3.4.png)

- Program.cs adds AWS Lambda support.

    ```csharp
    // When application is run in Lambda Kestrel is swapped out as the web server with Amazon.Lambda.AspNetCoreServer. 
    // This package will act as the webserver translating request and responses between the Lambda event source and ASP.NET Core.
    builder.Services.AddAWSLambdaHosting(LambdaEventSource.RestApi);
    ```

![ConnectPrivate](../../images/3-Amazon-API-Gateway/3.5.png)