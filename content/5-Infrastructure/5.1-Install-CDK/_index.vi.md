---
title : "Cài đặt CDK"
date: "2025-05-29"
weight : 1
chapter : false
pre : " <b> 5.1 </b> "
---


Chạy lệnh sau để cập nhật Node.js lên phiên bản LTS mới nhất (v20):

```csharp
    choco upgrade nodejs.install --version=20.11.0
```

Kiểm tra xem bạn đã cài đặt phiên bản Node.js mới nhất chưa bằng lệnh:

```csharp
    node --version
```

Bạn sẽ thấy kết quả tương tự:

```csharp
    v20.17.0
```

Chạy lệnh sau để cập nhật AWS CDK lên phiên bản mới nhất:

```csharp
    npm install -g aws-cdk
```

Kiểm tra AWS CDK phiên bản 2 đã được cài đúng chưa bằng lệnh:

```csharp
    cdk --version
```

Bạn sẽ thấy số phiên bản, ví dụ:

```csharp
    2.1018.0 (build e629e30)
```

{{% notice info %}}
Hãy chắc chắn rằng bạn đang sử dụng CDK v2.
{{% /notice %}}

