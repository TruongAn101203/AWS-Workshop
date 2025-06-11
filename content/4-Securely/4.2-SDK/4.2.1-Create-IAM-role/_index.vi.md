---
title : "Tạo IAM ROLE"
date: "2025-05-29"
weight : 1
chapter : false
pre : " <b> 4.2.1 </b> "
---


Trên trang AWS Console, nhấp vào liên kết *IAM* trong phần *Security*, *Identity* & *Compliance* (hoặc tìm kiếm *IAM*).

Trên trang IAM, chọn mục *Roles* ở bên trái.

Trên trang roles, nhấn nút *Create role*.

Ở màn hình tiếp theo, chọn *Lambda* làm dịch vụ sẽ sử dụng vai trò này, sau đó nhấn nút *Next*.

![ConnectPrivate](/images/4-Securely/4.8.png)

Trên trang phân quyền, tìm kiếm vai trò *AmazonSSMReadOnlyAccess* và chọn nó. Bạn đang cấp quyền chỉ đọc cho AWS Systems Manager để lấy tham số từ Parameter Store. Nhấn nút *Next*.

![ConnectPrivate](/images/4-Securely/4.9.png)

Trên trang xem lại, nhập tên vai trò phù hợp, ví dụ *DojoLambdaSSMRole*.

![ConnectPrivate](/images/4-Securely/4.10.png)
![ConnectPrivate](/images/4-Securely/4.11.png)

Cuối cùng, nhấn nút *Create Role*.

Vai trò đã được tạo. Hãy nhớ tên vai trò này vì bạn sẽ cần khi triển khai hàm Lambda sau.