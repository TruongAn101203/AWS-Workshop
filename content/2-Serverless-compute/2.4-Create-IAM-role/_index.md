---
title : "Create IAM role"
date: "2025-05-29"
weight : 4
chapter : false
pre : " <b> 2.4 </b> "
---


On the AWS Console page, click on the *IAM* link under the *Security, Identity & Compliance* section (or search for *IAM*).

On the IAM Page, click on the *Roles* menu item in the left.

On the roles page, click on the *Create role* button.

On the next screen, select *Lambda* as the service which will use this role and then click on the Next button.

![ConnectPrivate](/images/2-Severless-compute/2.9.png)

On the filter policies search, type *LambdaBasic* and select the *AWSLambdaBasicExecutionRole* policy.

![ConnectPrivate](/images/2-Severless-compute/2.10.png)

Also, type *S3Full* or simply *s3* at the search field and select the *AmazonS3FullAccess* policy. Click on *Next* button.

![ConnectPrivate](/images/2-Severless-compute/2.11.png)

On the Review page name your role as *ImageResizeLambdaExecutionRole*, make sure you seeing the two policies added on the step above.

![ConnectPrivate](/images/2-Severless-compute/2.12.1.png)
![ConnectPrivate](/images/2-Severless-compute/2.12.2.png)

Finally, click on the *Create Role* button.