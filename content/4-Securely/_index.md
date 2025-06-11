---
title : "Securely store your secrets"
date: "2025-05-29"
weight : 4
chapter : false
pre : " <b> 4. </b> "
---


The purpose of the lab is to store secret keys like connection strings and passwords in AWS Systems Manager Parameter Store in the encrypted format and then use two different ways to fetch values:

- Using extensions to .NET Core configuration.
- Using AWS Lambda function and AWS SDK.
  
AWS Systems Manager Parameter Store provides secure hierarchical storage for configuration data management and secrets management. Using AWS Systems Manager Parameter Store, you can safely store application configurations separately from your application’s code.

<!-- ### Content:

4.1. [Use .NET Core Configuration](4.1-Configuration/)\
4.2. [Use AWS SDK and Lambda](4.2-SDK/) -->