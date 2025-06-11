---
title : "Cài đặt .NET 8 SDK"
date: "2025-05-29"
weight : 2
chapter : false
pre : " <b> 7.2 </b> "
---


Bây giờ chúng ta sẽ tải xuống và cài đặt .NET 8 SDK.

Truy cập trang web chính thức của .NET 8: [.NET 8](https://dotnet.microsoft.com/en-us/download/dotnet/8.0) để lấy liên kết tải xuống trực tiếp các tệp nhị phân mới nhất của .NET 8 SDK:

![ConnectPrivate](../../../images/7-Graviton/7.6.png)

Nhấp vào *Arm64* và sao chép liên kết tải xuống trực tiếp:

![ConnectPrivate](../../../images/7-Graviton/7.6.1.png)

Liên kết tải về cho .NET 8 SDK 8.0.303 là:

```csharp
    sudo wget https://download.visualstudio.microsoft.com/download/pr/4bfdbe1a-e1f9-4535-8da6-6e1e7ea0994c/b110641d008b36dded561ff2bdb0f793/dotnet-sdk-8.0.303-linux-arm64.tar.gz
```

Tạo thư mục mới và giải nén SDK vào đó (vui lòng thay đổi số phiên bản tương ứng với phiên bản SDK bạn đã tải xuống):

```csharp
    mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-8.0.303-linux-arm64.tar.gz -C $HOME/dotnet
    export DOTNET_ROOT=$HOME/dotnet
    export PATH=$PATH:$HOME/dotnet
```

Bây giờ bạn có thể kiểm tra xem quá trình cài đặt có thành công không bằng cách chạy:

```csharp
    dotnet --info
```

Kết quả đầu ra bạn sẽ thấy thông tin về phiên bản SDK, tương tự như sau:

![ConnectPrivate](../../../images/7-Graviton/7.7.png)

Chúc mừng! Bạn đã cài đặt thành công .NET 8 SDK!