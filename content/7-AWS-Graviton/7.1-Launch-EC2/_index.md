---
title : "Launch EC2 instance"
date: "2025-05-29"
weight : 1
chapter : false
pre : " <b> 7.1 </b> "
---


First you need to launch new *Ubuntu* EC2 instance powered by AWS Graviton processor.

On the AWS Console page, click on the *EC2* link under the *Compute* section (or search for *EC2*). Click the Launch *Instance* button.

{{% notice note %}}
You are selecting *Ubuntu Server* as this is one of the Linux distributions supported by .NET 8 and that can be run on Arm64 architecture. You can check the list of currently supported Linux distributions for .NET here: [Install .NET on Linux](https://learn.microsoft.com/en-us/dotnet/core/install/linux) 
{{% /notice %}}

- Set name of the new instance as *DotNet8Graviton3* and select *Ubuntu* AMI fro Quick Start menu;
- Select *Ubuntu Server 24.04* LTS from AMI dropdown;
- Select *64-bit (Arm)* as architecture.

![ConnectPrivate](../../images/7-Graviton/7.1.png)

Next select an *c7g.medium* compute-optimized instance type that offers 1 vCPU and 2GB of memory.

![ConnectPrivate](../../images/7-Graviton/7.2.png)

Next you need to either create new or supply an existing key-pair. Create and download key-pair.

![ConnectPrivate](../../images/7-Graviton/7.2.1.png)

Next under network settings configure new security group:

- Open port 5000 to be able to access web application once it's up and running

![ConnectPrivate](../../images/7-Graviton/7.3.png)

Click *Launch Instance*.

Now your instance is launching and you can click on the *View Instances* button to see the status of instances within your AWS account.

![ConnectPrivate](../../images/7-Graviton/7.4.png)

We are ready to connect to your c7g instance. The easiest way is to connect using Session Manager right from AWS Console.

![ConnectPrivate](../../images/7-Graviton/7.5.png)

After successfully connecting, you will be at the Ubuntu command prompt.

Run the following command:

```csharp
    uname -i
```

That will show that we are running on an ‘aarch64’ architecture which is the Linux architecture name for 64-bit Arm:

```csharp
    aarch64
```

Congratulations! You have successfully launched and connected to the Ubuntu instance powered by AWS Graviton!