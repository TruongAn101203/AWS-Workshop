---
title : "Tìm hiểu thông tin từ văn bản bằng Amazon Comprehend"
date: "2025-05-29"
weight : 1
chapter : false
pre : " <b> 6.1 </b> "
---


Amazon Comprehend là một dịch vụ xử lý ngôn ngữ tự nhiên (NLP) sử dụng machine learning để tìm kiếm thông tin và mối quan hệ trong văn bản. Không yêu cầu có kinh nghiệm với machine learning.

Trong bài lab này, bạn sẽ sử dụng Amazon Comprehend để phát hiện ngôn ngữ của văn bản và hiểu được cảm xúc của một đoạn đánh giá sách mẫu.

[Tạo dự án]()

1. Tạo một dự án .NET Console App mới.

![ConnectPrivate](/images/6-Adding-innovation/6.1.png)

![ConnectPrivate](/images/6-Adding-innovation/6.2.png)

Chọn .NET 8.0 framework:

![ConnectPrivate](/images/6-Adding-innovation/6.3.png)

2. Thêm gói NuGet *AWSSDK.Comprehend* vào dự án:
   
![ConnectPrivate](/images/6-Adding-innovation/6.4.png)

3. Thêm các lệnh import sau vào *Program.cs*:

```csharp
    using Amazon.Comprehend;
    using Amazon.Comprehend.Model;
```

4. Thêm đoạn mã sau để khởi tạo *AmazonComprehendClient*:

```csharp
    var comprehendClient = new AmazonComprehendClient(Amazon.RegionEndpoint.EUWest1);
```

{{% notice note %}}
Khi bạn khởi tạo *AmazonComprehendClient* của AWS SDK, bạn cần truyền vào *RegionEndpoint* tương ứng với khu vực bạn đang thực hiện lab. Đoạn mã trên khởi tạo client ở khu vực *EUWest1*.
{{% /notice %}}

5. Thêm văn bản mẫu để làm việc (hoặc bạn có thể thay bằng đoạn văn bản khác để thử nghiệm):

```csharp
    var text = "This was such a beautiful book. I wasn't even planning any travel when I came across this and just started flipping through the pages. I really like the cover and all the large glossy photographs in this book. John Smith did a wonderful job with the photography. I've found a perfect home for this on my coffee table. I'm planning a trip to Paris and Barcelona soon and I know this will come in handy. In the meantime, it's perfect for assisting this armchair traveler!";
```

6. Thêm đoạn mã sau để phát hiện ngôn ngữ của đoạn văn bản. Đoạn mã này tạo một đối tượng *DetectDominantLanguageRequest* và gọi phương thức *DetectDominantLanguageAsync*:

```csharp
    var detectDominantLanguageRequest = new DetectDominantLanguageRequest()
    {
        Text = text
    };

    var detectDominantLanguageResponse = await comprehendClient.DetectDominantLanguageAsync(detectDominantLanguageRequest);

    Console.WriteLine("Detect Dominant Language:");
    Console.WriteLine("==========================");

    foreach (var dominantLanguage in detectDominantLanguageResponse.Languages)
    {
        Console.WriteLine($"Language Code: {dominantLanguage.LanguageCode}, Score: {dominantLanguage.Score}");
    }
```

Chạy chương trình và kiểm tra xem ngôn ngữ đã được phát hiện chính xác với độ tin cậy cao hay chưa:

![ConnectPrivate](/images/6-Adding-innovation/6.5.png)

7. Thêm đoạn mã sau để phát hiện cảm xúc của văn bản. Đoạn mã này tạo một đối tượng *DetectSentimentRequest* và gọi phương thức *DetectSentimentAsync*:

```csharp
    // 2 - Detect sentiment of the text
    var detectSentimentRequest = new DetectSentimentRequest()
    {
        Text = text,
        LanguageCode = "en"
    };

    var detectSentimentResponse = await comprehendClient.DetectSentimentAsync(detectSentimentRequest);

    Console.WriteLine("Detect Sentiment:");
    Console.WriteLine("==========================");

    Console.WriteLine(detectSentimentResponse.Sentiment);
```

Chạy chương trình và kiểm tra xem cảm xúc của văn bản đã được phát hiện đúng hay chưa:

![ConnectPrivate](/images/6-Adding-innovation/6.6.png)
