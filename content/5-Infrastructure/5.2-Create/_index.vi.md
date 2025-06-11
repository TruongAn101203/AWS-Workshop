---
title : "Create test project"
date: "2025-05-29"
weight : 2
chapter : false
pre : " <b> .2 </b> "
---


Tạo thư mục trống mới:

```csharp
    mkdir cdk-lab
    cd cdk-lab
```

Bạn tạo một dự án AWS CDK mới bằng cách chạy *cdk init* trong thư mục trống. *cdk init* sử dụng tên thư mục dự án để đặt tên cho các phần tử khác nhau trong dự án, bao gồm lớp, thư mục con và tập tin. Dự án được tạo bao gồm tham chiếu tới *Amazon.CDK.Lib* NuGet package. Package này và các phụ thuộc sẽ được NuGet tự động cài đặt.

Chạy *cdk init* trong thư mục đó với các tham số sau:

- *sample-app* là mẫu ứng dụng CDK ví dụ có một số construct
- *--language csharp* chỉ định bạn muốn dùng ngôn ngữ C#

```csharp
    cdk init sample-app --language csharp
```

Bạn sẽ thấy đầu ra như sau (lưu ý tên dự án *CdkLab* dựa trên tên thư mục bạn tạo):

![ConnectPrivate](/images/5-Infrastructure/5.1.png)

Mở tập tin *CdkLab.sln* mới được tạo trong Visual Studio.

![ConnectPrivate](/images/5-Infrastructure/5.2.png)

Mở *Program.cs*. Tập tin này khởi tạo lớp *CdkLabStack* từ file *CdkLabStack.cs*.

```csharp
    using Amazon.CDK;

    namespace CdkLab
    {
        sealed class Program
        {
            public static void Main(string[] args)
            {
                var app = new App();
                new CdkLabStack(app, "CdkLabStack");

                app.Synth();
            }
        }
    }
```

Mở *CdkLabStack.cs*.

```csharp
    using Amazon.CDK;
    using Amazon.CDK.AWS.SNS;
    using Amazon.CDK.AWS.SNS.Subscriptions;
    using Amazon.CDK.AWS.SQS;
    using Constructs;

    namespace CdkLab
    {
        public class CdkLabStack : Stack
        {
            internal CdkLabStack(Construct scope, string id, IStackProps props = null) : base(scope, id, props)
            {
                // The CDK includes built-in constructs for most resource types, such as Queues and Topics.
                var queue = new Queue(this, "CdkLabQueue", new QueueProps
                {
                    VisibilityTimeout = Duration.Seconds(300)
                });

                var topic = new Topic(this, "CdkLabTopic");

                topic.AddSubscription(new SqsSubscription(queue));
            }
        }
    }
```

Mẫu ứng dụng *sample-app* đã tạo cho bạn một stack với nội dung sau:

Stack bao gồm:

- Amazon SQS Queue (một *Queue* mới)
- Amazon SNS Topic (một *Topic* mới)
- Đăng ký hàng đợi để nhận các tin nhắn được phát tới topic (*topic.AddSubscription*)
