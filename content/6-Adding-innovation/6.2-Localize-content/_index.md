---
title : "Localize content using Amazon Translate"
date: "2025-05-29"
weight : 2
chapter : false
pre : " <b> 6.2 </b> "
---


Amazon Translate is a neural machine translation service that delivers fast, high-quality, and affordable language translation. Neural machine translation is a form of language translation automation that uses deep learning models to deliver more accurate and more natural sounding translation than traditional statistical and rule-based translation algorithms. Amazon Translate allows you to localize content - such as websites and applications - for international users, and to easily translate large volumes of text efficiently.

In this lab, we will use Amazon Translate to translate text from English to French.

#### Create project

1. Add *AWSSDK.Translate* Nuget package to your project:

![ConnectPrivate](../../images/6-Adding-innovation/6.7.png)

2. Add the following import statements to *Program.cs*:

```csharp
    using Amazon.Translate;
    using Amazon.Translate.Model;
```

3. Add the following code to initalize *AmazonTranslateClient*:

```csharp
    var translateClient = new AmazonTranslateClient(Amazon.RegionEndpoint.EUWest1);
```

{{% notice note %}}
Please note that when you initialize AWS SDK’s *AmazonTranslateClient*, you need to pass the RegionEndpoint of the region you are making labs in. The code below initializes *AmazonTranslateClient* in the *EUWest1* region.
{{% /notice %}}

5. Add the following code to translate the text:

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

Run the program and verify that text was correctly translated:

![ConnectPrivate](../../images/6-Adding-innovation/6.8.png)