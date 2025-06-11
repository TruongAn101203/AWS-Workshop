---
title : "Find insights in text using Amazon Comprehend"
date: "2025-05-29"
weight : 1
chapter : false
pre : " <b> 6.1 </b> "
---


Amazon Comprehend is a natural language processing (NLP) service that uses machine learning to find insights and relationships in text. No machine learning experience required.

In this lab, you will use Amazon Comprehend to detect the language of the text and understand the sentiment of sample book review.

#### Create project

1. Create a new .NET Console App project.

![ConnectPrivate](../../images/6-Adding-innovation/6.1.png)

![ConnectPrivate](../../images/6-Adding-innovation/6.2.png)

Choose .NET 8.0 framework:

![ConnectPrivate](../../images/6-Adding-innovation/6.3.png)

2. Add *AWSSDK.Comprehend* Nuget package to the project:
   
![ConnectPrivate](../../images/6-Adding-innovation/6.4.png)

3. Add the following import statements to *Program.cs*:

```csharp
    using Amazon.Comprehend;
    using Amazon.Comprehend.Model;
```

4. Add the following code to initalize *AmazonComprehendClient*:

```csharp
    var comprehendClient = new AmazonComprehendClient(Amazon.RegionEndpoint.EUWest1);
```

{{% notice note %}}
Please note that when you initialize AWS SDK’s *AmazonComprehendClient*, you need to pass the RegionEndpoint of the region you are making labs in. The code below initializes *AmazonComprehendClient* in the *EUWest1* region.
{{% /notice %}}

5. Add sample text to work with (or add your own text for testing purposes):

```csharp
    var text = "This was such a beautiful book. I wasn't even planning any travel when I came across this and just started flipping through the pages. I really like the cover and all the large glossy photographs in this book. John Smith did a wonderful job with the photography. I've found a perfect home for this on my coffee table. I'm planning a trip to Paris and Barcelona soon and I know this will come in handy. In the meantime, it's perfect for assisting this armchair traveler!";
```

6. Add the following code to detect language of the text. It creates an instance of *DetectDominantLanguageRequest* and calls method *DetectDominantLanguageAsync*:

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

Run the program and verify that language was detected correctly with high confidence:

![ConnectPrivate](../../images/6-Adding-innovation/6.5.png)

7. Add the following code to detect the sentiment of the text. It creates an instance of *DetectSentimentRequest* and calls the method *DetectSentimentAsync*:

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

Run the program and verify that text sentiment was detected correctly:

![ConnectPrivate](../../images/6-Adding-innovation/6.6.png)