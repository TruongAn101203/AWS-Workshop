---

title : "Triển khai dự án thử nghiệm"
date: "2025-05-29"
weight : 3
chapter : false
pre : " <b> 5.3 </b> "
----------------------

AWS CDK apps thực chất chỉ là một định nghĩa về hạ tầng của bạn bằng cách sử dụng code. Khi các CDK apps được chạy, chúng tạo ra (hoặc “synthesize”, theo thuật ngữ CDK) một AWS CloudFormation template cho mỗi stack được định nghĩa trong ứng dụng của bạn.

Để tổng hợp (synthesize) một CloudFormation template từ một CDK app, sử dụng lệnh *cdk synth*

{{% notice info %}}
CDK CLI yêu cầu bạn phải ở cùng thư mục với file cdk.json của bạn.
{{% /notice %}}

Hãy xem template được tổng hợp từ ứng dụng mẫu:

```csharp
    cdk synth
```

Nó sẽ xuất ra template CloudFormation như sau:

![ConnectPrivate](../../../images/5-Infrastructure/5.3.png)
![ConnectPrivate](../../../images/5-Infrastructure/5.3.1.png)

Như bạn thấy, template này bao gồm bốn resources:

- AWS::SQS::Queue - hàng đợi của chúng ta
- AWS::SQS::QueuePolicy - chính sách IAM cho phép topic này gửi tin nhắn tới hàng đợi
- AWS::SNS::Subscription - sự đăng ký giữa hàng đợi và topic
- AWS::SNS::Topic - topic của chúng ta

#### Bootstrapping an enviroment

Lần đầu tiên bạn triển khai một AWS CDK app vào một môi trường (account/region), bạn sẽ cần cài đặt một “bootstrap stack”. Stack này bao gồm các resources cần thiết cho hoạt động của toolkit. Ví dụ, stack này có một S3 bucket dùng để lưu template và assets trong quá trình triển khai.

Bạn có thể dùng lệnh *cdk bootstrap* để cài đặt bootstrap stack vào một môi trường:

{{% notice info %}}
CDK CLI yêu cầu bạn phải ở cùng thư mục với file cdk.json của bạn.
{{% /notice %}}

```csharp
    cdk bootstrap
```

Bạn sẽ thấy kết quả như sau:

![ConnectPrivate](../../../images/5-Infrastructure/5.4.png)

#### Deploy stack

Để triển khai các resources được định nghĩa trong AWS CDK app lên AWS, sử dụng lệnh *cdk deploy*.

```csharp
    cdk deploy
```

Bạn sẽ thấy cảnh báo như sau:

![ConnectPrivate](../../../images/5-Infrastructure/5.5.png)

Đây là cảnh báo rằng việc triển khai app có thể gây ra một số rủi ro. Vì chúng ta cần cho phép topic gửi tin nhắn đến hàng đợi, nhập *y* để triển khai stack và tạo các resources.

Kết quả xuất ra sẽ như sau:

![ConnectPrivate](../../../images/5-Infrastructure/5.6.png)

#### The CloudFormation Console

CDK apps được triển khai thông qua AWS CloudFormation. Mỗi CDK stack tương ứng 1:1 với CloudFormation stack.

Điều này có nghĩa là bạn có thể sử dụng console AWS CloudFormation để quản lý các stack của mình.

Hãy cùng xem console AWS CloudFormation. Vào AWS Console và tìm kiếm *CloudFormation*.

![ConnectPrivate](../../../images/5-Infrastructure/5.7.png)

Lọc danh sách các stack theo từ khóa cdk và bạn sẽ thấy hai CDK stack đã được triển khai:

- *CDKToolkit* - CDK Toolkit Stack. Nó được tạo bởi *cdk bootstrap* và quản lý các resources cần thiết để quản lý các Cloud Applications với AWS CDK.
- *CdkLabStack* - CDK stack mẫu mà bạn vừa triển khai bằng lệnh *cdk deploy*.

![ConnectPrivate](../../../images/5-Infrastructure/5.8.png)

Chọn *CdkLabStack* và mở tab *Resources*:

![ConnectPrivate](../../../images/5-Infrastructure/5.9.png)
