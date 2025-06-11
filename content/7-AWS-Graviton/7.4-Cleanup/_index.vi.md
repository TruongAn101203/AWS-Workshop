---
title : "Dọn dẹp"
date: "2025-05-29"
weight : 4
chapter : false
pre : " <b> 7.4 </b> "
---


{{% notice note %}}
Bạn nên lưu ý rằng hành động này không thể hoàn tác. Vì vậy, nếu trong hàm đó có chứa đoạn mã hoặc cấu hình quan trọng, hãy đảm bảo rằng bạn đã sao lưu trước khi thực hiện
{{% /notice %}}

- Chọn EC2 instance bạn muốn xóa: Vào trang EC2 > Instances. Tại bảng danh sách instance, tích chọn instance có tên **DotNet8Graviton3** (ID: i-06bb5d87b4248c384).
- Truy cập chi tiết instance: Nhấp vào Instance ID để mở trang chi tiết của instance.

![ConnectPrivate](/images/7-Graviton/7.10.clean.png)

- Xóa (Terminate) instance: Trong trang chi tiết, nhấn vào nút Instance state (Góc trên bên phải). Chọn Terminate (delete) instance từ menu xổ xuống. Xác nhận lại khi AWS hỏi để tiến hành xóa.
  
![ConnectPrivate](/images/7-Graviton/7.11.clean.png)