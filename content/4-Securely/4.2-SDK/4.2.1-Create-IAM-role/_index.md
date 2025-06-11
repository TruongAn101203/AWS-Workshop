---
title : "Create IAM ROLE"
date: "2025-05-29"
weight : 1
chapter : false
pre : " <b> 4.2.1 </b> "
---


On the AWS Console page, click on the *IAM* link under the *Security*, *Identity* & *Compliance* section (or search for *IAM*).

On the IAM Page, click on the *Roles* menu item in the left.

On the roles page, click on the *Create role* button.

On the next screen, select *Lambda* as the service which will use this role and then click on the *Next* button.

![ConnectPrivate](/images/4-Securely/4.8.png)

On the permission page, search for the *AmazonSSMReadOnlyAccess* role and select it. You are providing this role, read only access to AWS System Manager in order to fetch the parameters from the parameter stores. Click on the *Next* button.

![ConnectPrivate](/images/4-Securely/4.9.png)

On the review page, enter a suitable role name, for example *DojoLambdaSSMRole*.

![ConnectPrivate](/images/4-Securely/4.10.png)
![ConnectPrivate](/images/4-Securely/4.11.png)

Finally, click on the *Create Role* button.

The role is created. Please remember this role name because you will need this information later when you deploy Lambda function.