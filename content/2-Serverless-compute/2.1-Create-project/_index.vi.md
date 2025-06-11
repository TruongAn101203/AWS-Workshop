---
title : "Tạo dự án"
date: "2025-05-29"
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---


Sau khi đăng nhập vào EC2 qua kết nối RDP, chờ vài phút để các ứng dụng tải và thanh taskbar hiển thị đầy đủ.

Khởi chạy **Visual Studio 2022** từ thanh taskbar.

Nhấp vào **Create new project**.

Trong ô tìm kiếm mẫu (template searchbox), nhập **lambda** và sau đó chọn mẫu *AWS Lambda Project (.NET Core - C#)*. Nhiều mẫu AWS khác nhau đã được cài đặt như một phần của AWS Toolkit for Visual Studio.

![ConnectPrivate](../../../images/2-Severless-compute/2.1.png)

Nhấp **Next**

Đặt tên cho project là **ImageResize**.
Nhấp Next.

![ConnectPrivate](../../../images/2-Severless-compute/2.2.png)

Chọn *Simple S3 Function* blueprint. Nhấp Finish.


![ConnectPrivate](../../../images/2-Severless-compute/2.3.png)

Hãy xem qua project mẫu được tạo ra:

- Tệp *aws-lambda-tools-defaults.json* chứa thông tin về AWS Lambda runtime và tham chiếu đến AWS Lambda function handler.
  
![ConnectPrivate](../../../images/2-Severless-compute/2.4.png)

- Tệp *Function.cs* Chứa AWS Lambda function handler.

![ConnectPrivate](../../../images/2-Severless-compute/2.5.png)
