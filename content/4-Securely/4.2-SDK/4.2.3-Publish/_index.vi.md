---
title : "Xuất bản dự án"
date: "2025-05-29"
weight : 3
chapter : false
pre : " <b> 4.2.3 </b> "
---


Để triển khai hàm, nhấp chuột phải vào dự án Lambda và chọn tùy chọn *Publish to AWS Lambda*...

![ConnectPrivate](/images/4-Securely/4.16.png)

Nhập tên hàm là *SSMDemo*. Giữ nguyên các thiết lập mặc định khác và nhấn nút *Next*.

![ConnectPrivate](/images/4-Securely/4.17.png)

Trên màn hình Advanced Function Details, chọn lại vai trò mà bạn đã tạo trong bài tập đầu tiên (vai trò này có quyền truy cập AWS Systems Manager Parameter Store). Nhấn nút *Upload*.

![ConnectPrivate](/images/4-Securely/4.18.png)

Quá trình tải lên sẽ bắt đầu triển khai hàm. Khi hàm AWS Lambda được tải lên thành công, màn hình triển khai sẽ đóng và màn hình kiểm thử sẽ mở ra.

Nhập một chuỗi bất kỳ làm input (vì input ở đây không có ý nghĩa), sau đó nhấn nút *Invoke*. Hàm sẽ được thực thi và trả về giá trị tham số làm kết quả.

![ConnectPrivate](/images/4-Securely/4.19.png)

