---
title : "Tạo dự án ASP.NET Core"
date: "2025-05-29"
weight : 2
chapter : false
pre : " <b> 4.1.2 </b> "
---


Tạo dự án mới *ASP.NET Core Web API*.

![ConnectPrivate](../../../../images/4-Securely/4.4.png)

Đặt tên dự án là *ParameterStoreDemo*

Chọn *.NET 8.0* và bỏ chọn hỗ trợ HTTPS:

![ConnectPrivate](../../../../images/4-Securely/4.5.png)

Sau khi dự án được tạo, thêm gói NuGet *Amazon.Extensions.Configuration.SystemsManager* vào dự án.

![ConnectPrivate](../../../../images/4-Securely/4.6.png)

Tiếp theo, bạn cần kích hoạt provider cấu hình mới trong code.

Đối với ứng dụng ASP.NET Core, bạn có thể thực hiện trong file *Program.cs* bằng cách thêm dòng sau trước đoạn var *app = builder.Build();*:

```csharp
builder.Configuration.AddSystemsManager("/SampleApp");
```

Thêm API mới để đọc chuỗi kết nối từ cấu hình bằng cách thêm đoạn code sau vào file *Program.cs* trước *app.Run();*:

```csharp
    app.MapGet("/connection", (IConfiguration configuration) =>
{
    var connectionString = configuration.GetConnectionString("MyConnection");

    return connectionString;
});
```

Xây dựng và chạy dự án, kiểm tra chuỗi kết nối được hiển thị dưới dạng đã giải mã.

![ConnectPrivate](../../../../images/4-Securely/4.7.png)

Chúc mừng! Bạn đã cấu hình thành công nguồn cấu hình AWS Systems Manager và truy xuất tham số từ Parameter Store bằng giao diện chuẩn IConfiguration.
 
