---
title : "Tạo dự án"
date: "2025-05-29"
weight : 1
chapter : false
pre : " <b> 3.1 </b> "
---


Tạo dự án mới sử dụng mẫu *AWS Serverless* Application (*.NET Core - C#*).

![ConnectPrivate](../../../images/3-Amazon-API-Gateway/3.1.png)

![ConnectPrivate](../../../images/3-Amazon-API-Gateway/3.2.png)

Chọn mẫu *ASP.NET Core Minimal API* blueprint.

![ConnectPrivate](../../../images/3-Amazon-API-Gateway/3.3.png)

Xem qua dự án mẫu được tạo:

- File *aws-lambda-tools-defaults.json* chứa tham chiếu đến mẫu AWS Serverless Application Model (SAM) được sử dụng để triển khai ứng dụng serverless

- File *serverless-template* chứa mẫu AWS Serverless Application Model (SAM)

![ConnectPrivate](../../../images/3-Amazon-API-Gateway/3.4.png)

- File Program.cs thêm hỗ trợ AWS Lambda.

```csharp
  // Khi ứng dụng chạy trong Lambda, Kestrel được thay thế bằng Amazon.Lambda.AspNetCoreServer làm web server. 
  // Gói này sẽ hoạt động như webserver, chuyển đổi yêu cầu và phản hồi giữa nguồn sự kiện Lambda và ASP.NET Core.
  builder.Services.AddAWSLambdaHosting(LambdaEventSource.RestApi);
```

![ConnectPrivate](../../../images/3-Amazon-API-Gateway/3.5.png)

