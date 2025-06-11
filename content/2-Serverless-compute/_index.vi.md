---
title : "Điện toán không máy chủ với AWS Lambda"
date: "2025-05-29"
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

Trong bài thực hành này, bạn sẽ tạo một dự án AWS Lambda đơn giản bằng Visual Studio 2022. Bạn sẽ xây dựng một hàm AWS Lambda có chức năng tạo hình ảnh thu nhỏ đen trắng (B&W thumbnail) mỗi khi một hình ảnh được lưu vào Amazon S3 bucket.

Các bài tập sau cần được thực hiện theo thứ tự để hoàn thành bài thực hành này:
- Tạo một dự án AWS Lambda (sử dụng C# và .NET 8)
- Tạo một Amazon S3 bucket
- Tạo một vai trò AWS IAM
- Triển khai hàm AWS Lambda từ Visual Studio 2022
- Tạo và liên kết sự kiện S3 với hàm AWS Lambda của bạn
- Tải lên các tệp và kiểm tra xem hàm AWS Lambda có được thực thi và hình ảnh thu nhỏ có được tạo hay không

<!-- ### Content
2.1. [Create Project](2.1-Create-project/)\
2.2. [Add code to generate thumbnails](2.2-Add-code/)\
2.3. [Create S3 bucket](2.3-Create-S3-bucket/)\
2.4. [Create IAM role](2.4-Create-IAM-role/)\
2.5. [Publish project](2.5-Public-project/)\
2.6. [Configure event](2.6-Configure-event/)\
2.7. [Test AWS Lambda function](2.7-Test-AWS-Lambda/) -->