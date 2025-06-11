---
title : "Thêm logging"
date: "2025-05-29"
weight : 2
chapter : false
pre : " <b> 3.2 </b> "
---


Cập nhật file *Program.cs* với API khác và thêm logging bằng cách thêm đoạn mã sau ngay sau app.MapGet hiện tại:

```csharp
    app.MapGet("/values", (HttpRequest request) =>
    {
        app.Logger.LogInformation($">>>>>>>>>> GET values request from {request.HttpContext.Connection.RemoteIpAddress}");

        return new string[] { "value1", "value2" };
    });
```