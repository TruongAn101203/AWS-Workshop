---
title : "Tạo ứng dụng web mẫu .NET 8"
date: "2025-05-29"
weight : 3
chapter : false
pre : " <b> 7.3 </b> "
---


Bây giờ bạn đã cài đặt .NET 8 SDK, bạn có thể tạo ứng dụng web mẫu .NET:

Tạo thư mục mới:

```csharp
    mkdir ~/awesomeapp
    cd ~/awesomeapp
```

Chạy lệnh *dotnet new webapp* để tạo dự án mới dựa trên mẫu *webapp* (ASP.NET Core Web App):

```csharp
    dotnet new webapp
```

Bây giờ bạn có thể build và chạy ứng dụng web mẫu .NET được tạo, và mở cổng 5000 để truy cập:

```csharp
    dotnet run --urls=http://0.0.0.0:5000
```

Khi bạn thấy kết quả đầu ra như dưới đây, bạn có thể sử dụng trình duyệt web để truy cập ứng dụng:

![ConnectPrivate](../../../images/7-Graviton/7.8.png)

Trên trang AWS Console, nhấp vào liên kết EC2 trong phần *Compute* (hoặc tìm kiếm *EC2*) và tìm đến instance *EC2* của bạn. Sao chép địa chỉ IPv4 công khai của instance.

![ConnectPrivate](../../../images/7-Graviton/7.8.1.png)

Mở trình duyệt web và truy cập địa chỉ IPv4 công khai của instance, cổng 5000:

![ConnectPrivate](../../../images/7-Graviton/7.9.png)

Chúc mừng! Bạn đã có ứng dụng web .NET 8 chạy thành công trên instance AWS Graviton!
