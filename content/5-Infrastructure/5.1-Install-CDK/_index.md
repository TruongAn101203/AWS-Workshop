---
title : "Install CDK"
date: "2025-05-29"
weight : 1
chapter : false
pre : " <b> 5.1 </b> "
---


Run the following command to update Node.js to the latest LTS version (v20):

```csharp
    choco upgrade nodejs.install --version=20.17.0
```

Verify that you have latest version of Node.js installed by running the following command:

```csharp
    node --version
```

You should see output like this:

```csharp
    v20.17.0
```

Run the following command to update AWS CDK to the latest version:

```csharp
    npm install -g aws-cdk
```

Verify that AWS CDK v2 is correctly installed by running the following command:

```csharp
    cdk --version
```

As output you should see version number, something like this:

```csharp
    2.1018.0 (build e629e30)
```

{{% notice info %}}
Please ensure that you use CDK v2.
{{% /notice %}}
