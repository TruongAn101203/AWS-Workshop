---
title : "Verify API Gateway"
date: "2025-05-29"
weight : 4
chapter : false
pre : " <b> 3.4 </b> "
---


In the AWS Console, type *api gateway* into the search box to navigate to the API Gateway console.

The Serverless Application that you created deployed a new Amazon API Gateway.

![ConnectPrivate](../../images/3-Amazon-API-Gateway/3.10.png)

In the left menu, under the name of the newly created API, click the Resources link to view the resources for your API.

Select the *ANY* value under *{proxy+}*.

The content pane will show a graphical-like view of the full round-trip path of requests, starting with the client in a box on the left, and the backend resource in a box on the right.

Open *Test* tab. In the method type, select *GET* as the method, */values* as the path proxy, then click the Test button.

![ConnectPrivate](../../images/3-Amazon-API-Gateway/3.11.png)

The response body should show the same json response as you saw in the browser earlier.

![ConnectPrivate](../../images/3-Amazon-API-Gateway/3.12.png)

Go to AWS Console and open CloudWatch.

Search for the *serverless-api* (the name of the application that you have deployed) log group.

![ConnectPrivate](../../images/3-Amazon-API-Gateway/3.13.png)

Open the log group. You will be able to see the logs sent from your application and log entry from *Get values* API call.

![ConnectPrivate](../../images/3-Amazon-API-Gateway/3.14.png)