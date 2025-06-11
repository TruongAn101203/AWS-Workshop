---
title : "Test throttling"
date: "2025-05-29"
weight : 5
chapter : false
pre : " <b> 3.5 </b> "
---


In this module you will test throttling configuration of Amazon API Gateway using simple load test script.

You can access the *Default Method Throttling* configuration by navigating to:

1. Stages
2. Click on the stage (eg Prod)
3. Click Edit

![ConnectPrivate](../../images/3-Amazon-API-Gateway/3.15.png)

Enable throttling, change the throttling values to *1* request/second, with a burst rate of *1* requests. We’re choosing this low value to make it easier to test without load-testing software. Save your changes.

![ConnectPrivate](../../images/3-Amazon-API-Gateway/3.16.png)

Confirm the changes:

![ConnectPrivate](../../images/3-Amazon-API-Gateway/3.17.png)

Create the new PowerShell script file with the following content (use your API Gateway URL):

```csharp
    Write-Output "Sending GET request to your REST endpoint 10 times"

    for ($i = 0; $i -lt 10; $i++) {
        Invoke-WebRequest -Uri https://<Your API Endpoint URL>/Prod/values -UseBasicParsing -Method 'Get'
    }
```

Open PowerShell, and navigate to the folder where you saved the file. Run your PowerShell script by typing *.\<file-name>.ps1* where *<file-name>* is the name you gave the file.

Depending on your network connection, and the speed at which your computer is able to execute the requests, you will see some of the requests succeed with status code 200, while others will fail with the *{“message”:“Too Many Requests”}* error message indicating that requests were throttled.

![ConnectPrivate](../../images/3-Amazon-API-Gateway/3.18.png)
![ConnectPrivate](../../images/3-Amazon-API-Gateway/3.18.1.png)