---
title : "Cấu hình sự kiện"
date: "2025-05-29"
weight : 6
chapter : false
pre : " <b> 2.6 </b> "
---


Bây giờ bạn sẽ liên kết một sự kiện Amazon S3 với hàm AWS Lambda của bạn.

Trên trang AWS Console, nhấp vào liên kết *Lambda* trong phần *Compute* (hoặc tìm kiếm *Lambda*).

Nhấp vào tên hàm AWS Lambda mà bạn đã xuất bản.

![ConnectPrivate](../../../images/2-Severless-compute/2.17.png)

Thêm một trigger Amazon S3 vào hàm AWS Lambda bằng cách nhấp vào *Add trigger* ở bên trái.

![ConnectPrivate](../../../images/2-Severless-compute/2.18.png)

Cấu hình trigger: chọn bucket bạn đã tạo trong danh sách thả xuống bucket và nhập *images/* làm tiền tố mà AWS Lambda sẽ theo dõi, sau đó nhấn *Add*.

![ConnectPrivate](../../../images/2-Severless-compute/2.19.png)
![ConnectPrivate](../../../images/2-Severless-compute/2.19.1.png)

{{% notice warning %}}
**Đừng quên định nghĩa tiền tố (prefix)**  
Hàm AWS Lambda sẽ lưu ảnh thu nhỏ vào một thư mục mới có tên thumbnails trong cùng bucket. Nếu bạn không định nghĩa tiền tố, hàm AWS Lambda sẽ rơi vào vòng lặp đệ quy vì mỗi lần lưu ảnh vào bucket, hàm AWS Lambda sẽ được kích hoạt lại.
{{% /notice %}}

Khi trigger được tạo, bạn sẽ thấy nó trong phần *Triggers* của hàm AWS Lambda:

![ConnectPrivate](../../../images/2-Severless-compute/2.20.png)

