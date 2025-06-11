---
title : "Xuất bản dự án"
date: "2025-05-29"
weight : 5
chapter : false
pre : " <b> 2.5 </b> "
---


Sau khi xây dựng giải pháp của bạn, nhấp chuột phải vào dự án trong Solution Explorer và chọn *Publish to AWS Lambda* để khởi chạy trình hướng dẫn xuất bản.

![ConnectPrivate](../../../images/2-Severless-compute/2.13.png)

Đảm bảo rằng ô chọn *Account profile to use* và *Region* được thiết lập đúng với hồ sơ và vùng bạn đang sử dụng cho bài lab hôm nay. Đặt tên cho Lambda Function là *ImageResize*, rồi nhấn Next.

![ConnectPrivate](../../../images/2-Severless-compute/2.14.png) 

Chọn tên Role mà bạn đã tạo ở phần trước của bài lab này và nhấp vào *Upload*.

![ConnectPrivate](../../../images/2-Severless-compute/2.15.png)

Khi hàm AWS Lambda được xuất bản, bạn có thể thấy nó trong AWS Explorer:

![ConnectPrivate](../../../images/2-Severless-compute/2.16.png)