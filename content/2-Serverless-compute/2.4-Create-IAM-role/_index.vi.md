---
title : "Tạo IAM role"
date: "2025-05-29"
weight : 4
chapter : false
pre : " <b> 2.4 </b> "
---


Trên trang AWS Console, nhấp vào liên kết *IAM* trong phần *Security, Identity & Compliance*(hoặc tìm kiếm *IAM*).

Trên trang IAM, nhấp vào mục *Roles* ở bên trái.

Trên trang Roles, nhấp vào nút *Create role*.

Ở màn hình tiếp theo, chọn *Lambda* làm dịch vụ sẽ sử dụng vai trò này, sau đó nhấn nút Next.

![ConnectPrivate](/images/2-Severless-compute/2.9.png)

Trên ô tìm kiếm bộ lọc policies, nhập *LambdaBasic* và chọn policy *AWSLambdaBasicExecutionRole*.


![ConnectPrivate](/images/2-Severless-compute/2.10.png)

Ngoài ra, nhập *S3Full* hoặc đơn giản là *s3* vào ô tìm kiếm và chọn policy *AmazonS3FullAccess*. Nhấn nút *Next*.


![ConnectPrivate](/images/2-Severless-compute/2.11.png)

Trên trang Review, đặt tên vai trò của bạn là *ImageResizeLambdaExecutionRole*, đảm bảo bạn thấy hai chính sách đã được thêm ở bước trên.

![ConnectPrivate](/images/2-Severless-compute/2.12.1.png)
![ConnectPrivate](/images/2-Severless-compute/2.12.2.png)

Cuối cùng, nhấp vào nút *Create Role*.

