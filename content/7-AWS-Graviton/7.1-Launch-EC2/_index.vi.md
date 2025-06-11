---
title : "Khởi chạy phiên bản EC2"
date: "2025-05-29"
weight : 1
chapter : false
pre : " <b> 7.1 </b> "
---


Đầu tiên, bạn cần khởi chạy một phiên bản EC2 *Ubuntu* mới sử dụng bộ xử lý AWS Graviton.

Tại trang AWS Console, nhấp vào liên kết EC2 trong phần *Compute* (hoặc tìm kiếm EC2). Nhấp vào nút Launch *Instance*.

{{% notice note %}}
Bạn đang chọn *Ubuntu Server* vì đây là một trong những bản phân phối Linux được .NET 8 hỗ trợ và có thể chạy trên kiến trúc Arm64. Bạn có thể xem danh sách các bản phân phối Linux được hỗ trợ cho .NET tại đây: [Install .NET on Linux](https://learn.microsoft.com/en-us/dotnet/core/install/linux) 
{{% /notice %}}

- Đặt tên cho phiên bản mới là *DotNet8Graviton3* và chọn *Ubuntu* AMI từ menu Quick Start;
- Chọn *Ubuntu Server 24.04* LTS từ danh sách AMI;
- Chọn kiến trúc *64-bit (Arm)*.

![ConnectPrivate](../../../images/7-Graviton/7.1.png)

Tiếp theo, chọn loại phiên bản tối ưu hóa tính toán *c7g.medium*, cung cấp 1 vCPU và 2GB bộ nhớ.

![ConnectPrivate](../../../images/7-Graviton/7.2.png)

Tiếp theo, bạn cần tạo mới hoặc cung cấp một cặp khóa hiện có. Tạo và tải về cặp khóa.

![ConnectPrivate](../../../images/7-Graviton/7.2.1.png)

Sau đó, trong phần thiết lập mạng, cấu hình một security group mới:

- Mở cổng 5000 để có thể truy cập ứng dụng web khi nó chạy.

![ConnectPrivate](../../../images/7-Graviton/7.3.png)

Nhấp vào *Launch Instance*.

Bây giờ phiên bản của bạn đang được khởi chạy và bạn có thể nhấp vào nút *View Instances* để xem trạng thái của các phiên bản trong tài khoản AWS của bạn.

![ConnectPrivate](../../../images/7-Graviton/7.4.png)

Chúng ta đã sẵn sàng để kết nối với phiên bản c7g. Cách dễ nhất là sử dụng Session Manager ngay từ AWS Console.

![ConnectPrivate](../../../images/7-Graviton/7.5.png)

Sau khi kết nối thành công, bạn sẽ ở tại dòng lệnh Ubuntu.

Chạy lệnh sau:

```csharp
    uname -i
```

Lệnh này sẽ hiển thị rằng chúng ta đang chạy trên kiến trúc ‘aarch64’ – tên kiến trúc của Linux cho nền tảng Arm 64-bit:

```csharp
    aarch64
```

Chúc mừng! Bạn đã khởi chạy và kết nối thành công với phiên bản Ubuntu sử dụng AWS Graviton!