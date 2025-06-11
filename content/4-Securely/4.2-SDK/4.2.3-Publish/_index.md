---
title : "Publish project"
date: "2025-05-29"
weight : 3
chapter : false
pre : " <b> 4.2.3 </b> "
---


In order to deploy the function, right click on the Lambda project and click on the *Publish to AWS Lambda*... menu option.

![ConnectPrivate](/images/4-Securely/4.16.png)

Type in the function name as *SSMDemo*. Leave everything else as the default and click on the *Next* button.

![ConnectPrivate](/images/4-Securely/4.17.png)

On the Advanced Function Details screen, select the same role which you created in the first exercise (that role has access to the AWS Systems Manager Parameter Store). Click the *Upload* button.

![ConnectPrivate](/images/4-Securely/4.18.png)


The upload will start the function deployment. The deployment screen will close and test screen will open as soon as the AWS Lambda function is uploaded successfully.

Type in any string as input (as input has no meaning here) and then click on the *Invoke* button. It will execute the function and return the parameter value as the result.

![ConnectPrivate](/images/4-Securely/4.19.png)