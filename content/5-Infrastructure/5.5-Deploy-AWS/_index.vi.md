---

title: "Triển khai AWS Lambda với CDK"
date: "2025-05-29"
weight: 5
chapter: false
pre: " <b> 5.5 </b> "
---------------------

Trong mô-đun này, bạn sẽ triển khai một hàm AWS Lambda mẫu bằng cách sử dụng AWS CDK.

[Mã xử lý Lambda](#)

Trước tiên, chúng ta bắt đầu với mã xử lý của AWS Lambda.

Tạo một thư mục tên là *lambda* trong thư mục gốc của dự án (cùng cấp với thư mục *src*).

![ConnectPrivate](/images/5-Infrastructure/5.12.png)

Thêm một tệp có tên *lambda/hello.js* với nội dung như sau:

```csharp
    exports.handler = async function(event) {
        console.log("request:", JSON.stringify(event, undefined, 2));
        return {
            statusCode: 200,
            headers: { "Content-Type": "text/plain" },
            body: `Hello, CDK! You've hit ${event.path}\n`
        };
    };
```

Đây là một hàm AWS Lambda đơn giản trả về văn bản “Hello, CDK! You’ve hit [đường dẫn URL]”. Phần kết quả trả về cũng bao gồm mã trạng thái HTTP và tiêu đề HTTP, được sử dụng bởi API Gateway để tạo phản hồi HTTP cho người dùng.

[Cập nhật dự án]()

AWS CDK đi kèm với một thư viện các construct phong phú gọi là AWS Construct Library.

Cập nhật *CdkLabStack.cs* với các thay đổi sau:

- Thêm using statement

```csharp
    using Amazon.CDK.AWS.Lambda;
```

- Thêm tài nguyên Lambda Function

```csharp
    using Amazon.CDK;
    using Constructs;
    using Amazon.CDK.AWS.Lambda;

    namespace CdkLab
    {
        public class CdkLabStack : Stack
        {
            internal CdkLabStack(Construct scope, string id, IStackProps props = null) : base(scope, id, props)
            {
                // Định nghĩa một tài nguyên Lambda mới
                var hello = new Function(this, "HelloHandler", new FunctionProps
                {
                    Runtime = Runtime.NODEJS_20_X, // môi trường thực thi
                    Code = Code.FromAsset("lambda"), // mã nguồn nằm trong thư mục "lambda"
                    Handler = "hello.handler" // tệp là "hello", hàm là "handler"
                });
            }
        }
    }
```

Một vài lưu ý:

- Hàm sử dụng runtime NodeJS 20.X
- Mã xử lý được lấy từ thư mục *lambda*
- Tên hàm là *hello.handler* (tức là file *hello.js*, function *handler*)

[Triển khai]()

Trước tiên, chạy lệnh *cdk diff* để xem trước các thay đổi sẽ được triển khai:

```csharp
    cdk diff
```

Kết quả sẽ giống như sau:

![ConnectPrivate](/images/5-Infrastructure/5.13.png)

Như bạn có thể thấy, đoạn mã này tạo ra các tài nguyên *AWS::Lambda::Function* và *AWS::IAM::Role*. Nó cũng tạo ra một vài tham số CloudFormation được sử dụng bởi toolkit để truyền thông tin vị trí của mã xử lý (handler code).

Lúc này bạn có thể triển khai hàm bằng lệnh:

```csharp
    cdk deploy
```

Bạn sẽ thấy cảnh báo như sau:

![ConnectPrivate](/images/5-Infrastructure/5.14.png)

Nhập *y* để xác nhận triển khai stack và tạo tài nguyên.

Sau khi stack được triển khai, bạn sẽ thấy đầu ra như sau:

![ConnectPrivate](/images/5-Infrastructure/5.15.png)

[Kiểm tra hàm Lambda]()

Trên giao diện AWS Console, nhấp vào liên kết *Lambda* dưới mục *Compute* (hoặc tìm kiếm "Lambda").

![ConnectPrivate](/images/5-Infrastructure/5.16.png)

Tìm hàm Lambda của bạn (tên bắt đầu bằng *CdkLabStack-HelloHandler*) và mở nó.

Chuyển sang tab *Test* và cấu hình một test event.

Chọn mẫu *Amazon API Gateway AWS Proxy* (lưu ý giá trị của trường *path* trong payload mẫu).

![ConnectPrivate](/images/5-Infrastructure/5.17.png)

Nhấp nút *Test* để chạy hàm.

Mở rộng phần *Details* trong pane *Executing function: succeeded*, bạn sẽ thấy kết quả như mong đợi (trong đó giá trị của path chính là dữ liệu bạn gửi vào).

![ConnectPrivate](/images/5-Infrastructure/5.18.png)
