---
title : "Sử dụng cấu hình .NET Core"
date: "2025-05-29"
weight : 1
chapter : false
pre : " <b> 4.1 </b> "
---


Cấu hình trong .NET Core khá khác so với những gì bạn từng dùng trong .NET Framework. Với .NET Framework, bạn chỉ có một nguồn cấu hình duy nhất là file app.config/web.config, và nếu muốn sử dụng các nguồn cấu hình khác, bạn phải tự tạo giải pháp cấu hình riêng.

Hệ thống cấu hình của .NET Core được thiết kế để có thể mở rộng dễ dàng. Ví dụ, khi bạn tạo ứng dụng ASP.NET Core, mặc định nó sẽ lấy thông tin cấu hình từ file **appsettings.json**, các tham số dòng lệnh (command line arguments) và biến môi trường (environment variables). Bạn cũng có thể thêm vào các nguồn cấu hình khác (configuration source providers) rồi cho phép ứng dụng truy cập cấu hình đó qua cùng một giao diện (interface).

AWS cung cấp một gói NuGet có tên là **Amazon.Extensions.Configuration.SystemsManager**, giúp đơn giản hóa cách ứng dụng của bạn tải các thiết lập cấu hình trong AWS Systems Manager Parameter Store vào hệ thống cấu hình của .NET Core.
