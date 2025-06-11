---
title : "Test throttling"
date: "2025-05-29"
weight : 5
chapter : false
pre : " <b> 3.5 </b> "
---


Trong module này, bạn sẽ kiểm tra cấu hình throttling của Amazon API Gateway bằng cách sử dụng một script tải đơn giản.

Bạn có thể truy cập cấu hình *Default Method Throttling* bằng cách:

1. Vào mục Stages
2. Nhấp vào stage (ví dụ: Prod)
3. Nhấn Edit

![ConnectPrivate](/images/3-Amazon-API-Gateway/3.15.png)

Bật throttling, thay đổi giá trị throttling thành *1* request/giây, với tốc độ burst là *1* request. Chúng ta chọn giá trị thấp này để dễ dàng kiểm tra mà không cần phần mềm load-testing. Lưu các thay đổi.

![ConnectPrivate](/images/3-Amazon-API-Gateway/3.16.png)

Xác nhận các thay đổi:

![ConnectPrivate](/images/3-Amazon-API-Gateway/3.17.png)

Tạo file script PowerShell mới với nội dung sau (thay bằng URL API Gateway của bạn):

```csharp
    Write-Output "Sending GET request to your REST endpoint 10 times"

    for ($i = 0; $i -lt 10; $i++) {
        Invoke-WebRequest -Uri https://<Your API Endpoint URL>/Prod/values -UseBasicParsing -Method 'Get'
    }
```

Mở PowerShell, chuyển đến thư mục chứa file script. Chạy script bằng cách gõ *.\<tên-file>.ps1* trong đó *\<tên-file>* là tên bạn đặt cho file.

Tùy thuộc vào kết nối mạng và tốc độ máy tính, bạn sẽ thấy một số yêu cầu thành công với mã trạng thái 200, trong khi các yêu cầu khác sẽ thất bại với thông báo lỗi *{“message”:“Too Many Requests”}* báo hiệu các yêu cầu bị throttled.

![ConnectPrivate](/images/3-Amazon-API-Gateway/3.18.png)
![ConnectPrivate](/images/3-Amazon-API-Gateway/3.18.1.png)