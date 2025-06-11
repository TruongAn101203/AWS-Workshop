---
title : "Create test project"
date: "2025-05-29"
weight : 2
chapter : false
pre : " <b> 5.2 </b> "
---


Create new empty folder:

```csharp
    mkdir cdk-lab
    cd cdk-lab
```

You create a new AWS CDK project by invoking *cdk init* in an empty directory. cdk init uses the name of the project folder to name various elements of the project, including classes, subfolders, and files. The resulting project includes a reference to the *Amazon.CDK.Lib* NuGet package. It and its dependencies are installed automatically by NuGet.

Run *cdk init* from within that folder with following parameters:
- sample-app is example CDK Application template with some constructs
- --language csharp specifies that you want to use C# language

```csharp
    cdk init sample-app --language csharp
```

You will see the output like this (please note that project name *CdkLab* is based on the name of folder you created):

![ConnectPrivate](/images/5-Infrastructure/5.1.png)

Open newly generated *CdkLab.sln* in Visual Studio.

![ConnectPrivate](/images/5-Infrastructure/5.2.png)

Open *Program.cs*. It instantiates the *CdkLabStack* class from the *CdkLabStack.cs* file.

```csharp
    using Amazon.CDK;

    namespace CdkLab
    {
        sealed class Program
        {
            public static void Main(string[] args)
            {
                var app = new App();
                new CdkLabStack(app, "CdkLabStack");

                app.Synth();
            }
        }
    }
```

Open *CdkLabStack.cs*.

```csharp
    using Amazon.CDK;
    using Amazon.CDK.AWS.SNS;
    using Amazon.CDK.AWS.SNS.Subscriptions;
    using Amazon.CDK.AWS.SQS;
    using Constructs;

    namespace CdkLab
    {
        public class CdkLabStack : Stack
        {
            internal CdkLabStack(Construct scope, string id, IStackProps props = null) : base(scope, id, props)
            {
                // The CDK includes built-in constructs for most resource types, such as Queues and Topics.
                var queue = new Queue(this, "CdkLabQueue", new QueueProps
                {
                    VisibilityTimeout = Duration.Seconds(300)
                });

                var topic = new Topic(this, "CdkLabTopic");

                topic.AddSubscription(new SqsSubscription(queue));
            }
        }
    }
```

The *sample-app* template has created the following stack for you.

The stack includes:

- Amazon SQS Queue (new Queue)
- Amazon SNS Topic (new Topic)
- Subscribing the queue to receive any messages published to the topic (topic.AddSubscription)