---
title : "Cleanup"
date: "2025-05-29"
weight : 3
chapter : false
pre : " <b> 4.3 </b> "
---


{{% notice note %}}
You should note that this action cannot be undone. Therefore, if the function contains important code or configurations, make sure to back them up before proceeding.
{{% /notice %}}

- Log in to the AWS Console. In the **Services** menu, search for and select **Systems Manager**, then navigate to **Parameter Store** to manage configuration parameters.

- Select the parameter to delete by ticking the checkbox, e.g.:*/SampleApp/ConnectionStrings/MyConnection
*
- Click the "Delete" button at the top right.

- Confirm the deletion when prompted.

![ConnectPrivate](/images/4-Securely/4.20.clean.png)