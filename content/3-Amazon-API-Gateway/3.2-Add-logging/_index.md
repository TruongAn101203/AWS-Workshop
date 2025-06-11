---
title : "Add logging"
date: "2025-05-29"
weight : 2
chapter : false
pre : " <b> 3.2 </b> "
---


Update *Program.cs* file with another API and add logging by adding the following code after existing app.MapGet:

```csharp
    app.MapGet("/values", (HttpRequest request) =>
    {
        app.Logger.LogInformation($">>>>>>>>>> GET values request from {request.HttpContext.Connection.RemoteIpAddress}");

        return new string[] { "value1", "value2" };
    });
```
