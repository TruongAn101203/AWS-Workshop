---

title : "Dọn dẹp dự án thử nghiệm"
date: "2025-05-29"
weight : 4
chapter : false
pre : " <b> 5.4 </b> "
----------------------

Dự án được tạo bằng mẫu *sample-app* bao gồm một hàng đợi Amazon SQS và một chủ đề Amazon SNS. Bạn sẽ không sử dụng chúng trong dự án của mình, vì vậy hãy xóa chúng khỏi hàm tạo *CdkLabStack*.

Mở *CdkLabStack.cs* và dọn dẹp như sau:

```csharp
    using Amazon.CDK;

    namespace CdkLab
    {
        public class CdkLabStack : Stack
        {
            internal CdkLabStack(Construct scope, string id, IStackProps props = null) : base(scope, id, props)
            {
                // empty
            }
        }
    }`
```

Bây giờ bạn đã chỉnh sửa nội dung của stack, bạn có thể yêu cầu toolkit hiển thị sự khác biệt giữa ứng dụng CDK của bạn và những gì hiện đang được triển khai. Đây là cách an toàn để kiểm tra điều gì sẽ xảy ra khi bạn triển khai và luôn là một thực hành tốt:

```csharp
    cdk diff
```

Kết quả đầu ra sẽ như sau. Như mong đợi, tất cả tài nguyên sẽ bị xóa.

![ConnectPrivate](/images/5-Infrastructure/5.10.png)

Chạy *cdk deploy* và xem các tài nguyên bị xóa:

```csharp
    cdk deploy
```

![ConnectPrivate](/images/5-Infrastructure/5.11.png)
