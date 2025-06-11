---
title : "Triển khai Amazon API Gateway"
date: "2025-05-29"
weight : 6
chapter : false
pre : " <b> 5.6 </b> "
---


Bước tiếp theo là thêm Amazon API Gateway phía trước hàm Lambda của bạn. Amazon API Gateway sẽ cung cấp một điểm cuối HTTP công khai mà bất kỳ ai trên Internet đều có thể truy cập bằng trình duyệt web.

Bạn sẽ sử dụng tích hợp proxy của AWS Lambda được gắn vào gốc của API. Điều này có nghĩa là bất kỳ yêu cầu nào đến bất kỳ đường dẫn URL nào đều sẽ được chuyển tiếp trực tiếp đến hàm AWS Lambda của bạn và phản hồi từ hàm đó sẽ được trả về cho người dùng.

[Cập nhật dự án]()

Thêm dòng lệnh using sau:

```csharp
    using Amazon.CDK.AWS.APIGateway;
```

Tiếp theo, thêm một đối tượng *LambdaRestApi* vào stack của bạn để định nghĩa một điểm cuối API và liên kết nó với hàm AWS Lambda của bạn.

```csharp
    namespace CdkLab
    {
        public class CdkLabStack : Stack
        {
            internal CdkLabStack(Construct scope, string id, IStackProps props = null) : base(scope, id, props)
            {
                ..........

                // defines an API Gateway REST API resource backed by our "hello" function.
                new LambdaRestApi(this, "Endpoint", new LambdaRestApiProps
                {
                    Handler = hello
                });
            }
        }
    }
```
Chỉ như vậy là đủ. Đây là tất cả những gì bạn cần làm để định nghĩa một Amazon API Gateway chuyển tiếp tất cả yêu cầu đến một hàm AWS Lambda.

[Triển khai]()

Trước tiên, hãy chạy *cdk diff* để xem các thay đổi sẽ được triển khai:

```csharp
    cdk diff
```
Nếu bạn cuộn xuống phần đầu ra, bạn sẽ thấy rằng 10 tài nguyên mới sẽ được tạo và một điểm cuối sẽ được xuất ra:

![ConnectPrivate](/images/5-Infrastructure/5.19.png)

Bây giờ đã đến lúc triển khai Amazon API Gateway.

```csharp
    cdk deploy
```

Khi việc triển khai hoàn tất, bạn sẽ thấy dòng sau (cuộn đến cuối phần đầu ra):

![ConnectPrivate](/images/5-Infrastructure/5.20.png)
![ConnectPrivate](/images/5-Infrastructure/5.20.1.png)

Đây là một đầu ra của stack được tự động thêm bởi đối tượng Amazon API Gateway và bao gồm URL của điểm cuối API Gateway.

Giờ bạn có thể thử mở URL này trong trình duyệt của mình:

![ConnectPrivate](/images/5-Infrastructure/5.21.png)
