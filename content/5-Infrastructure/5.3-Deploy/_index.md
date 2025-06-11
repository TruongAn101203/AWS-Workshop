---
title : "Deploy test project"
date: "2025-05-29"
weight : 3
chapter : false
pre : " <b> 5.3 </b> "
---


AWS CDK apps are effectively only a definition of your infrastructure using code. When CDK apps are executed, they produce (or “synthesize”, in CDK parlance) an AWS CloudFormation template for each stack defined in your application.

To synthesize a CloudFormation template from a CDK app, use the *cdk synth* command

{{% notice info %}}
The CDK CLI requires you to be in the same directory as your cdk.json file.
{{% /notice %}}

Let’s check out the template synthesized from the sample app:

```csharp
    cdk synth
```

It will output the following CloudFormation template:

![ConnectPrivate](../../images/5-Infrastructure/5.3.png)
![ConnectPrivate](../../images/5-Infrastructure/5.3.1.png)

As you can see, this template includes four resources:

- AWS::SQS::Queue - our queue
- AWS::SQS::QueuePolicy - the IAM policy which allows this topic to send messages to the queue
- AWS::SNS::Subscription - the subscription between the queue and the topic
- AWS::SNS::Topic - our topic

[Bootstrapping an enviroment](#)

The first time you deploy an AWS CDK app into an environment (account/region), you’ll need to install a “bootstrap stack”. This stack includes resources that are needed for the toolkit operation. For example, the stack includes an S3 bucket that is used to store templates and assets during the deployment process.

You can use the *cdk bootstrap* command to install the bootstrap stack into an environment:

{{% notice info %}}
The CDK CLI requires you to be in the same directory as your cdk.json file.
{{% /notice %}}

```csharp
    cdk bootstrap
```
You will see output like this:

![ConnectPrivate](../../images/5-Infrastructure/5.4.png)

[Deploy stack](#)

In order to deploy the resources defined in your AWS CDK app to AWS, use *cdk deploy* command.

```csharp
    cdk deploy
```
You should see a warning like the following:

![ConnectPrivate](../../images/5-Infrastructure/5.5.png)

This is warning you that deploying the app entails some risk. Since we need to allow the topic to send messages to the queue, enter *y* to deploy the stack and create the resources.

Output should look like the following:

![ConnectPrivate](../../images/5-Infrastructure/5.6.png)

[The CloudFormation Console](#)

CDK apps are deployed through AWS CloudFormation. Each CDK stack maps 1:1 with CloudFormation stack.

This means that you can use the AWS CloudFormation console in order to manage your stacks.

Let’s take a look at the AWS CloudFormation console. Go to AWS Console and search for *CloudFormation*.

![ConnectPrivate](../../images/5-Infrastructure/5.7.png)

Filter the list of stacks by cdk and you will see two CDK stacks deployed:

- *CDKToolkit* - the CDK Toolkit Stack. It was created by *cdk bootstrap* and manages resources necessary for managing your Cloud Applications with AWS CDK.
- *CdkLabStack* - sample CDK stack that you have just deployed by running *cdk deploy* command.

![ConnectPrivate](../../images/5-Infrastructure/5.8.png)

Select *CdkLabStack* and open the *Resources* tab:

![ConnectPrivate](../../images/5-Infrastructure/5.9.png)
