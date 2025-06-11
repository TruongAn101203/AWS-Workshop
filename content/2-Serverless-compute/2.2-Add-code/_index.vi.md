---
title : "Thêm mã để tạo ảnh thu nhỏ (thumbnails)"
date: "2025-05-29"
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---


Thêm gói *NuGet SixLabors.ImageSharp* vào dự án:

![ConnectPrivate](../../../images/2-Severless-compute/2.6.png)

Thêm các lệnh using sau vào file *Function.cs*:

```csharp
using Amazon.Lambda.Core;
using Amazon.Lambda.S3Events;
using Amazon.S3;
using Amazon.S3.Model;
using System.IO;
using SixLabors.ImageSharp;
using SixLabors.ImageSharp.Processing;
using SixLabors.ImageSharp.PixelFormats;
using SixLabors.ImageSharp.Formats.Jpeg;
```

Thay thế phương thức *FunctionHandler* trong file *Function.cs* bằng đoạn mã dưới đây:

```csharp
public async Task FunctionHandler(S3Event evnt, ILambdaContext context)
{
    string[] fileExtentions = new string[] { ".jpg", ".jpeg" };
    var s3Event = evnt.Records?[0].S3;
    if (s3Event == null)
    {
        return;
    }

    try
    {
        foreach (var record in evnt.Records)
        {
            context.Logger.Log("----> File: " + record.S3.Object.Key);
            if (!fileExtentions.Contains(Path.GetExtension(record.S3.Object.Key).ToLower()))
            {
                context.Logger.Log("File Extention is not supported - " + s3Event.Object.Key);
                continue;
            }

            Stream imageStream = new MemoryStream();
            var objectResponse = await S3Client.GetObjectAsync(record.S3.Bucket.Name, record.S3.Object.Key);
                
            using (Stream responseStream = objectResponse.ResponseStream)
            {
                using (var image = Image.Load(responseStream))
                {
                    // Create B&W thumbnail
                    image.Mutate(ctx => ctx.Grayscale().Resize(200, 200));
                    image.Save(imageStream, new JpegEncoder());
                    imageStream.Seek(0, SeekOrigin.Begin);
                }
            }                

            // Creating a new S3 ObjectKey for the thumbnails
            string thumbnailObjectKey = "";
            string objectKey = record.S3.Object.Key.ToLower();
            int endSlash = objectKey.LastIndexOf("/");
            if (endSlash > 0)
            {
                string S3ObjectName = objectKey.Substring(endSlash + 1);
                int beginSlash = objectKey.Substring(0, endSlash - 1).LastIndexOf("/");
                if (beginSlash > 0)
                {
                    thumbnailObjectKey = objectKey.Substring(0, beginSlash) + "thumbnails/" + S3ObjectName;
                }
                else
                {
                    thumbnailObjectKey = "thumbnails/" + S3ObjectName;
                }                   
            }
            else
            {
                thumbnailObjectKey = "thumbnails/" + objectKey;
            }

            context.Logger.Log("----> Thumbnail file Key: " + thumbnailObjectKey);

            await S3Client.PutObjectAsync(new PutObjectRequest
            {
                BucketName = record.S3.Bucket.Name,
                Key = thumbnailObjectKey,
                InputStream = imageStream
            });
        }

        context.Logger.Log("Processed " + evnt.Records.Count.ToString());
    }
    catch (Exception e)
    {
        context.Logger.LogLine($"Error getting object {s3Event.Object.Key} from bucket {s3Event.Bucket.Name}");
        context.Logger.LogLine($"Make sure they exist and your bucket is in the same region as this function");
        context.Logger.LogLine(e.Message);
        context.Logger.LogLine(e.StackTrace);
        throw;
    }
}
```

Đoạn mã trên thực hiện các tác vụ sau:
- Liệt kê tất cả các tệp được nhận như một phần của S3Event:
  ```csharp
    foreach (var record in evnt.Records)
    ```
- Tải tệp xuống từ S3 bucket
    ```csharp
    var objectResponse = await S3Client.GetObjectAsync(record.S3.Bucket.Name, record.S3.Object.Key)
    ```
- Thay đổi kích thước và chuyển nó sang đen trắng:

  ```csharp
    image.Mutate(ctx => ctx.Grayscale().Resize(200, 200));
    image.Save(imageStream, new JpegEncoder());
    ```
- Saves generated thumbnail back to S3 bucket:
    ```csharp
    await S3Client.PutObjectAsync(new PutObjectRequest
    {
        BucketName = record.S3.Bucket.Name,
        Key = thumbnailObjectKey,
        InputStream = imageStream
    });
    ``` 
