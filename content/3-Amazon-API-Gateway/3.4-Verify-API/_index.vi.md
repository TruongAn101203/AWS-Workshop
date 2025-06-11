---
title : "Xác minh API Gateway"
date: "2025-05-29"
weight : 4
chapter : false
pre : " <b> 3.4 </b> "
---


Trong AWS Console, nhập *api gateway* vào ô tìm kiếm để truy cập vào bảng điều khiển API Gateway.

Ứng dụng Serverless mà bạn đã tạo sẽ triển khai một Amazon API Gateway mới.

![ConnectPrivate](/images/3-Amazon-API-Gateway/3.10.png)

Trong menu bên trái, dưới tên API mới tạo, nhấp vào liên kết Resources để xem các tài nguyên của API.

Chọn giá trị *ANY* dưới *{proxy+}*.

Phần nội dung sẽ hiển thị một sơ đồ trực quan về toàn bộ chu trình yêu cầu, bắt đầu với client ở ô bên trái và tài nguyên backend ở ô bên phải.

Mở tab *Test*. Ở phần loại phương thức, chọn *GET* làm method, nhập */values* làm đường dẫn proxy, rồi nhấn nút Test.

![ConnectPrivate](/images/3-Amazon-API-Gateway/3.11.png)

Phần nội dung phản hồi sẽ hiển thị cùng JSON như bạn đã thấy trong trình duyệt trước đó.

![ConnectPrivate](/images/3-Amazon-API-Gateway/3.12.png)

Truy cập AWS Console và mở CloudWatch.

Tìm kiếm nhóm log có tên *serverless-api* (tên ứng dụng bạn đã triển khai).

![ConnectPrivate](/images/3-Amazon-API-Gateway/3.13.png)

Mở nhóm log. Bạn sẽ thấy các log được gửi từ ứng dụng của bạn cùng các mục log từ lệnh gọi API *Get values*.

![ConnectPrivate](/images/3-Amazon-API-Gateway/3.14.png)