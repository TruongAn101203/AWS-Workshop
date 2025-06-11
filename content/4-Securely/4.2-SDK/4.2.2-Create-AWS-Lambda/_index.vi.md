---
title : "Tạo dự án AWS Lambda"
date: "2025-05-29"
weight : 2
chapter : false
pre : " <b> 4.2.2 </b> "
---


Tạo dự án mới sử dụng mẫu *AWS Lambda Project* (.NET Core - C#).

![ConnectPrivate](/images/4-Securely/4.12.png)

![ConnectPrivate](/images/4-Securely/4.13.png)

Trong cửa sổ Select Blueprint, chọn blueprint *Empty Top-level Function* và nhấn nút *Finish*.

![ConnectPrivate](/images/4-Securely/4.14.png)

Sau khi dự án được tạo, thêm gói NuGet *AWSSDK.SimpleSystemsManagement* vào dự án.

![ConnectPrivate](/images/4-Securely/4.15.png)

Mở file *Function.cs* và thêm các câu lệnh using sau:

```csharp
using Amazon.SimpleSystemsManagement;
using Amazon.SimpleSystemsManagement.Model;
```

Trong file *Function.cs*, thay thế handler hiện có bằng đoạn mã sau:

```csharp
var handler = async (string input, ILambdaContext context) =>
{
    var client = new AmazonSimpleSystemsManagementClient();

    var request = new GetParameterRequest
    {
        Name = "/SampleApp/ConnectionStrings/MyConnection",
        WithDecryption = true
    };

    GetParameterResponse response = await client.GetParameterAsync(request);

    return string.Format("Decrypted Value: {0}", response.Parameter.Value);
};
```

Mã đã sẵn sàng. Hãy xây dựng (Build) dự án Lambda.