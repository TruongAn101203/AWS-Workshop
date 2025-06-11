---
title : "Cleanup"
date: "2025-05-29"
weight : 4
chapter : false
pre : " <b> 7.4 </b> "
---


{{% notice note %}}
You should note that this action cannot be undone. Therefore, if the function contains important code or configurations, make sure to back them up before proceeding.
{{% /notice %}}

- Select the EC2 instance you want to delete: Go to EC2 > Instances. In the instance list, check the instance named **DotNet8Graviton3** (ID: i-06bb5d87b4248c384).
- Open instance details: Click on the Instance ID to navigate to the detailed view. Confirm the termination when prompted.
![ConnectPrivate](../../images/7-Graviton/7.10.clean.png)
- Terminate the instance: In the detail view, click the Instance state button (top right). From the dropdown, select Terminate (delete) instance.

![ConnectPrivate](../../images/7-Graviton/7.11.clean.png)

