---
title : "Địa phương hóa nội dung bằng Amazon Translate"
date: "2025-05-29"
weight : 2
chapter : false
pre : " <b> 6.2 </b> "
---


Amazon Translate là một dịch vụ dịch máy bằng mạng nơ-ron cung cấp bản dịch ngôn ngữ nhanh, chất lượng cao và chi phí thấp. Dịch máy bằng mạng nơ-ron là một hình thức tự động dịch ngôn ngữ sử dụng các mô hình học sâu để mang lại bản dịch chính xác hơn và tự nhiên hơn so với các thuật toán dịch dựa trên thống kê và quy tắc truyền thống.
Amazon Translate cho phép bạn địa phương hóa nội dung – như trang web và ứng dụng – cho người dùng quốc tế, và dễ dàng dịch khối lượng lớn văn bản một cách hiệu quả.

Trong bài lab này, chúng ta sẽ sử dụng Amazon Translate để dịch văn bản từ tiếng Anh sang tiếng Pháp.

[Tạo dự án]()

1. Thêm gói Nuget *AWSSDK.Translate* vào dự án của bạn:

![ConnectPrivate](/images/6-Adding-innovation/6.7.png)

2. Thêm các lệnh using sau vào file *Program.cs*:

```csharp
    using Amazon.Translate;
    using Amazon.Translate.Model;
```

3. Thêm đoạn mã sau để khởi tạo *AmazonTranslateClient*:

```csharp
    var translateClient = new AmazonTranslateClient(Amazon.RegionEndpoint.EUWest1);
```

{{% notice note %}}
Lưu ý rằng khi bạn khởi tạo *AmazonTranslateClient* của AWS SDK, bạn cần truyền vào *RegionEndpoint* của khu vực mà bạn đang thực hiện lab. Đoạn mã bên dưới khởi tạo client tại khu vực *EUWest1*.
{{% /notice %}}

5. Thêm đoạn mã sau để dịch văn bản:

```csharp
    var translatRequest = new TranslateTextRequest
    {
        Text = text,
        SourceLanguageCode = "en",
        TargetLanguageCode = "fr"
    };

    var translatResponse = await translateClient.TranslateTextAsync(translatRequest);

    Console.WriteLine("Translation to French:");
    Console.WriteLine("==========================");
    Console.WriteLine(translatResponse?.TranslatedText);
```

Chạy chương trình và xác nhận rằng văn bản đã được dịch chính xác:

![ConnectPrivate](/images/6-Adding-innovation/6.8.png)