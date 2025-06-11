---
title : "Dọn dẹp"
date: "2025-05-29"
weight : 3
chapter : false
pre : " <b> 6.3 </b> "
---


{{% notice note %}}
Bạn nên lưu ý rằng hành động này không thể hoàn tác. Vì vậy, nếu trong hàm đó có chứa đoạn mã hoặc cấu hình quan trọng, hãy đảm bảo rằng bạn đã sao lưu trước khi thực hiện
{{% /notice %}}

Lab này không tạo ra tài nguyên lâu dài trong AWS (như S3, Lambda, DynamoDB,...), nên không cần vào AWS Console để cleanup.

Tuy nhiên, cần lưu ý:

- Nếu bạn sử dụng Access Key thủ công để cấu hình SDK, hãy xóa hoặc vô hiệu hóa key IAM sau khi lab xong để tránh rò rỉ hoặc sử dụng ngoài ý muốn.

- Xóa thư mục project trong máy nếu bạn không còn sử dụng, giúp tránh chạy lại nhầm và giữ máy gọn gàng hơn.