---
title : "Configure event"
date: "2025-05-29"
weight : 6
chapter : false
pre : " <b> 2.6 </b> "
---


Now you are going to associate a Amazon S3 event with your AWS Lambda function.

On the AWS Console page, click on the *Lambda* link under the *Compute* section (or search for *Lambda*).

Click on the AWS Lambda function name you have published.

![ConnectPrivate](/images/2-Severless-compute/2.17.png)

Add a Amazon S3 trigger to the AWS Lambda function by clicking on the *Add trigger* on the left.

![ConnectPrivate](/images/2-Severless-compute/2.18.png)

Configure the trigger: select the bucket you have created on the bucket drop-down and enter *images/* as the prefix the AWS Lambda will be watching, and press *Add*.

![ConnectPrivate](/images/2-Severless-compute/2.19.png)
![ConnectPrivate](/images/2-Severless-compute/2.19.1.png) 


{{% notice warning %}}
**Do not forget to define prefix**  
The AWS Lambda function will save the thumbnail image in a new folder called thumbnails within the same bucket. If you don’t define a prefix you AWS Lambda function will enter in a recursive loop as every time you save an image in the bucket the AWS Lambda function will be triggered.
{{% /notice %}}

Once trigger is created, you will see it under *Triggers*section of your AWS Lambda function:

![ConnectPrivate](/images/2-Severless-compute/2.20.png)