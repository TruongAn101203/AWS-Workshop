---
title : "Clean up test project"
date: "2025-05-29"
weight : 4
chapter : false
pre : " <b> 5.4 </b> "
---


The project created using sample-app template includes an Amazon SQS queue, and an Amazon SNS topic. You’re not going to use them in your project, so remove them from your the CdkLabStack constructor.

Open *CdkLabStack.cs* and clean it up. It should look like this:

```csharp
    using Amazon.CDK;

    namespace CdkLab
    {
        public class CdkLabStack : Stack
        {
            internal CdkLabStack(Construct scope, string id, IStackProps props = null) : base(scope, id, props)
            {
                // empty
            }
        }
    }`
```

Now that you have modified your stack’s contents, you can ask the toolkit to show you the difference between your CDK app and what’s currently deployed. This is a safe way to check what will happen once you deploy and is always good practice:

```csharp
    cdk diff
```

Output should look like the following. As expected, all resources are going to be destroyed.

![ConnectPrivate](/images/5-Infrastructure/5.10.png)

Run *cdk deploy* and see the resources being deleted:

```csharp
    cdk deploy
```

![ConnectPrivate](/images/5-Infrastructure/5.11.png)
