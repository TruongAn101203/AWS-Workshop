---
title : "Publish project"
date: "2025-05-29"
weight : 5
chapter : false
pre : " <b> 2.5 </b> "
---


After building your solution, right-click your project in Solution Explorer, and select *Publish to AWS Lambda* to launch the publishing wizard.

![ConnectPrivate](/images/2-Severless-compute/2.13.png)

Ensure the *Account profile to use* drop-down and *Region* drop-down are set to the profile and region you are using for today's labs. Name your Lambda Function as *ImageResize*, and click Next.

![ConnectPrivate](/images/2-Severless-compute/2.14.png)

Select the Role Name that you have created at previous part of this lab and click on *Upload*.

![ConnectPrivate](/images/2-Severless-compute/2.15.png)

Once AWS Lambda function is published, you can see it in AWS Explorer:

![ConnectPrivate](/images/2-Severless-compute/2.16.png)