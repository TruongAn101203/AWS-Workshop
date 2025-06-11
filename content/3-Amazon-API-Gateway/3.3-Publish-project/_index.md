---
title : "Publish project"
date: "2025-05-29"
weight : 3
chapter : false
pre : " <b> 3.3 </b> "
---


After building your solution, right-click your project in Solution Explorer, and select *Publish to AWS Lambda*... to launch the publishing wizard.

![ConnectPrivate](../../images/3-Amazon-API-Gateway/3.6.png)

Ensure the Account profile to use drop-down and Region drop-down are set to the profile and region you are using for today’s labs.

Under the Stack Name enter a stack name such as *aws-serverless-api-test*.

Then, click the *New*... under Amazon S3 Bucket and create a new bucket with a unique name like *aws-serverless-api-test-SOMENUMBER*.

![ConnectPrivate](../../images/3-Amazon-API-Gateway/3.7.png)

Now wait for the Serverless Application to be deployed, once it has finished the status should be *CREATE_COMPLETE*.

![ConnectPrivate](../../images/3-Amazon-API-Gateway/3.8.png)

Browse the *AWS Serverless URL* (append */values* to the end of the URL) to call the API method you created. Your browser should display the JSON for *value1* and *value2*.

```csharp
    https://nxlwjdj8ol.execute-api.eu-west-1.amazonaws.com/Prod/values
```

![ConnectPrivate](../../images/3-Amazon-API-Gateway/3.9.png)

Congratulations! You have your ASP.NET Web API up and running behind Amazon API Gateway!