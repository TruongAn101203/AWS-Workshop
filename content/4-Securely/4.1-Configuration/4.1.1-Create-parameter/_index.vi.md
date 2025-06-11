---
title : "Tạo tham số (parameter)"
date: "2025-05-29"
weight : 1
chapter : false
pre : " <b> 4.1.1 </b> "
---


Trên trang AWS Console, tìm kiếm *Systems Manager*.

Trên trang Systems Manager, nhấp vào mục *Parameter Store* ở bên trái.

Trên trang Parameter Store, nhấn nút *Create parameter*.

Ở trang chi tiết tham số, nhập tên tham số là */SampleApp/ConnectionStrings/MyConnection*, chọn loại là *SecureString*, chọn nguồn khóa KMS là *My current account* và ID khóa KMS là *alias/aws/ssm* (mặc định). Cuối cùng nhập giá trị cho tham số rồi nhấn nút *Create parameter*.

![ConnectPrivate](/images/4-Securely/4.1.png)
![ConnectPrivate](/images/4-Securely/4.2.png)

Tham số đã được tạo và giá trị tham số được lưu dưới dạng mã hóa sử dụng khóa AWS KMS.

![ConnectPrivate](/images/4-Securely/4.3.png)

