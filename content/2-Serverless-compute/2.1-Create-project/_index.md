---
title : "Create project "
date: "2025-05-29"
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---


Once logged into the EC2 via RDP connection, wait a few mins for applications to load and taskbar to populate.

Launch **Visual Studio 2022** from the taskbar.

Click **Create new project**

In the template searchbox type **lambda** and then select *AWS Lambda Project (.NET Core - C#)* template. Various AWS templates were installed as part of AWS Toolkit for Visual Studio.

![ConnectPrivate](../../images/2-Severless-compute/2.1.png)

Click **Next**

Provide a name for the project **ImageResize**. Click Next.

![ConnectPrivate](../../images/2-Severless-compute/2.2.png) 

Select Simple S3 Function blueprint. Click Finish.

![ConnectPrivate](../../images/2-Severless-compute/2.3.png)

Take a look at the generated sample project:

- *aws-lambda-tools-defaults.json* file contains information about AWS Lambda runtime and reference to the AWS Lambda function handler
  
![ConnectPrivate](../../images/2-Severless-compute/2.4.png)

- *Function.cs* contains AWS Lambda function handler

![ConnectPrivate](../../images/2-Severless-compute/2.5.png)