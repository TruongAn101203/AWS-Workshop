---
title : "Cleanup"
date: "2025-05-29"
weight : 3
chapter : false
pre : " <b> 6.3 </b> "
---


{{% notice note %}}
You should note that this action cannot be undone. Therefore, if the function contains important code or configurations, make sure to back them up before proceeding.
{{% /notice %}}

This lab does not create any long-term resources in AWS (such as S3, Lambda, DynamoDB, etc.), so there's no need to access the AWS Console for cleanup.

However, please keep the following in mind:

- If you manually configured the SDK using an Access Key, make sure to delete or disable the IAM key after completing the lab to avoid potential leakage or unintended usage.

- Delete the project folder on your machine if you no longer need it to prevent accidental reruns and keep your workspace clean.