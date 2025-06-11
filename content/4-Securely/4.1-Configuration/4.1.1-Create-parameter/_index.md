---
title : "Create parameter"
date: "2025-05-29"
weight : 1
chapter : false
pre : " <b> 4.1.1 </b> "
---


On the AWS Console page, search for *Systems Manager*.

On the Systems Manager page, click on the *Parameter Store* menu item in the left.

On the parameter store page, click on the *Create parameter* button.

On the parameter details page, enter parameter name as */SampleApp/ConnectionStrings/MyConnection*, select type as *SecureString*, select KMS key source as *My current account* and KMS Key id as *alias/aws/ssm* (default). Finally enter a value for your parameter and then click on the *Create parameter* button.

![ConnectPrivate](../../../images/4-Securely/4.1.png)
![ConnectPrivate](../../../images/4-Securely/4.2.png)

The parameter is created and it has stored the parameter value in the encrypted format using the AWS KMS key.

![ConnectPrivate](../../../images/4-Securely/4.3.png)


