---
title : "Create AWS Lambda project"
date: "2025-05-29"
weight : 2
chapter : false
pre : " <b> 4.2.2 </b> "
---


Create new project using *AWS Lambda Project*(.NET Core - C#) template.

![ConnectPrivate](/images/4-Securely/4.12.png)

![ConnectPrivate](/images/4-Securely/4.13.png)

On the Select Blueprint window, select *Empty Top-level Function* blueprint and click on the *Finish* button.

![ConnectPrivate](/images/4-Securely/4.14.png)

Once project is created, add the following NuGet Package to the project: *AWSSDK.SimpleSystemsManagement*.

![ConnectPrivate](/images/4-Securely/4.15.png)

Open the Function.cs file and add the following using statements.

```csharp
    using Amazon.SimpleSystemsManagement;
    using Amazon.SimpleSystemsManagement.Model;
```

In *Function.cs file*, replace the existing handler with the following code:

```csharp
    var handler = async (string input, ILambdaContext context) =>
    {
        var client = new AmazonSimpleSystemsManagementClient();

        var request = new GetParameterRequest
        {
            Name = "/SampleApp/ConnectionStrings/MyConnection",
            WithDecryption = true
        };

        GetParameterResponse response = await client.GetParameterAsync(request);

        return string.Format("Decrypted Value: {0}", response.Parameter.Value);
    };
```

The code is ready. Build the Lambda project.