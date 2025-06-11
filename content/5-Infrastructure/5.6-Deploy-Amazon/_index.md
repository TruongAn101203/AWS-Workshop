---
title : "Deploy Amazon API Gateway"
date: "2025-05-29"
weight : 6
chapter : false
pre : " <b> 5.6 </b> "
---


Next step is to add an Amazon API Gateway in front of your function. Amazon API Gateway will expose a public HTTP endpoint that anyone on the internet can hit with web browser.

You will use AWS Lambda proxy integration mounted to the root of the API. This means that any request to any URL path will be proxied directly to your AWS Lambda function, and the response from the function will be returned back to the user.

[Update project]()

Add the following using statement:

```csharp
    using Amazon.CDK.AWS.APIGateway;
```

Next add a *LambdaRestApi* construct to your stack that defines an API endpoint and associate it with our AWS Lambda function.

```csharp
    namespace CdkLab
    {
        public class CdkLabStack : Stack
        {
            internal CdkLabStack(Construct scope, string id, IStackProps props = null) : base(scope, id, props)
            {
                ..........

                // defines an API Gateway REST API resource backed by our "hello" function.
                new LambdaRestApi(this, "Endpoint", new LambdaRestApiProps
                {
                    Handler = hello
                });
            }
        }
    }
```

That’s it. This is all you need to do in order to define an Amazon API Gateway which proxies all requests to an AWS Lambda function.

[Deploy]()

First run cdk diff to take a look at the changes that are going to be deployed.

```csharp
    cdk diff
```

If you scroll down the output, you will see that 10 new resources will be created and one endpoint will be output:

![ConnectPrivate](/images/5-Infrastructure/5.19.png)

Now it's time to deploy Amazon API Gateway.

```csharp
    cdk deploy
```

When deployment is complete, you’ll notice this line (scroll to the end of output):

![ConnectPrivate](/images/5-Infrastructure/5.20.1.png)

This is a stack output that’s automatically added by the Amazon API Gateway construct and includes the URL of the Amazon API Gateway endpoint.

Now you can try to open this URL in your browser:

![ConnectPrivate](/images/5-Infrastructure/5.21.png)
