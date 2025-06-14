---
title : "Amazon API Gateway"
date: "2025-05-29"
weight : 3
chapter : false
pre : " <b> 3. </b> "
---

Trong bài thực hành này, bạn sẽ tạo một ứng dụng ASP.NET Web API đơn giản, triển khai nó bằng AWS Serverless Application Model (SAM) trên AWS Lambda, và sau đó cấu hình Amazon API Gateway làm lớp proxy phía trước các endpoint của Web API.

Amazon API Gateway là một dịch vụ được quản lý hoàn toàn, giúp các nhà phát triển dễ dàng tạo, xuất bản, duy trì, giám sát và bảo mật các API ở mọi quy mô. Bằng cách sử dụng Amazon API Gateway trước các endpoint của API trong ứng dụng của bạn, bạn có thể áp dụng giới hạn truy cập (throttling), bảo mật, giám sát và ghi log, cải thiện hiệu năng bằng tính năng cache của dịch vụ, cũng như quản lý phiên bản và tài liệu dành cho nhà phát triển (bao gồm hỗ trợ Swagger).

![ConnectPrivate](../images/3-Amazon-API-Gateway/3.diagram.png)

Bạn sẽ hoàn thành các bài tập sau trong bài thực hành này:
- Tạo một ASP.NET Web API bằng mẫu AWS Serverless Application
- Thêm ghi log vào Web API
- Triển khai ASP.NET Web API lên Amazon API Gateway được hỗ trợ bởi AWS Lambda
- Kiểm tra cấu hình giới hạn truy cập (Throttling) của Amazon API Gateway

<!-- ### Content
3.1. [Create Project](3.1-Create-project/)\
3.2. [Add logging](3.2-Add-logging/)\
3.3. [Publish project](3.3-Publish-project/) \
3.4. [Verify API Gateway](3.4-Verify-API/)\
3.5. [Test throttling](3.5-Test-throttling/) -->