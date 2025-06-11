---
title : "Install .NET 8 SDK"
date: "2025-05-29"
weight : 2
chapter : false
pre : " <b> 7.2 </b> "
---

Now we are going to download and install .NET 8 SDK.

Navigate to the official .NET 8 web site: [.NET 8](https://dotnet.microsoft.com/en-us/download/dotnet/8.0) to get the direct link to the latest .NET 8 SDK binaries:

![ConnectPrivate](/images/7-Graviton/7.6.png)

Click on the *Arm6*4 and copy the direct download link:

![ConnectPrivate](/images/7-Graviton/7.6.1.png)

The download link for .NET 8 SDK 8.0.303 is the following:

```csharp
    sudo wget https://download.visualstudio.microsoft.com/download/pr/4bfdbe1a-e1f9-4535-8da6-6e1e7ea0994c/b110641d008b36dded561ff2bdb0f793/dotnet-sdk-8.0.303-linux-arm64.tar.gz
```

Create new folder and unzip SDK there (please change the version number to correspond to the SDK version that you downloaded):

```csharp
    mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-8.0.303-linux-arm64.tar.gz -C $HOME/dotnet
    export DOTNET_ROOT=$HOME/dotnet
    export PATH=$PATH:$HOME/dotnet
```

Now you can check that installation was successful:

```csharp
    dotnet --info
```

As output you should see SDK version information, something like this:

![ConnectPrivate](/images/7-Graviton/7.7.png)

Congratulations! You have successfully installed .NET 8 SDK!