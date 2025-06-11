---
title : "Xuất bản dự án"
date: "2025-05-29"
weight : 3
chapter : false
pre : " <b> 3.3 </b> "
---


Sau khi xây dựng giải pháp của bạn, nhấp chuột phải vào dự án trong Solution Explorer và chọn *Publish to AWS Lambda*... để khởi chạy trình hướng dẫn xuất bản.

![ConnectPrivate](/images/3-Amazon-API-Gateway/3.6.png)

Đảm bảo ô chọn Account profile to use và Region được thiết lập đúng với hồ sơ và vùng bạn đang dùng cho bài lab hôm nay.

Trong phần Stack Name, nhập tên stack như *aws-serverless-api-test*.

Sau đó, nhấp vào *New*... dưới mục Amazon S3 Bucket và tạo một bucket mới với tên duy nhất như *aws-serverless-api-test-SOMENUMBER*.

![ConnectPrivate](/images/3-Amazon-API-Gateway/3.7.png)

Bây giờ chờ ứng dụng Serverless được triển khai, khi hoàn tất trạng thái sẽ là *CREATE\_COMPLETE*.

![ConnectPrivate](/images/3-Amazon-API-Gateway/3.8.png)

Truy cập *AWS Serverless URL* (thêm */values* vào cuối URL) để gọi phương thức API bạn đã tạo. Trình duyệt sẽ hiển thị JSON cho *value1* và *value2*.

```csharp
    https://nxlwjdj8ol.execute-api.eu-west-1.amazonaws.com/Prod/values
```

![ConnectPrivate](/images/3-Amazon-API-Gateway/3.9.png)

Chúc mừng! Bạn đã có ASP.NET Web API chạy phía sau Amazon API Gateway!