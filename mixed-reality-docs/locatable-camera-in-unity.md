---
title: Unity での場所を特定できるカメラ
description: Unity での HoloLens 場所を特定できるカメラの使用量。
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 写真、ビデオ、hololens、カメラ、unity、場所を特定できます。
ms.openlocfilehash: f0183400f55b1c6663a9a20ab4992befe5ad0718
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601771"
---
# <a name="locatable-camera-in-unity"></a>Unity での場所を特定できるカメラ

## <a name="enabling-the-capability-for-photo-video-camera"></a>フォト ビデオ_カメラの機能を有効にします。

使用するアプリの「web カメラ」機能を宣言する必要があります、[カメラ](locatable-camera.md)します。
1. Unity エディターは、「> プロジェクトの設定 > プレーヤーの編集」のページに移動して、player の設定に移動します。
2. "Windows Store" タブをクリックします。
3. 「発行の設定 > 機能」セクションでは、確認、 **web カメラ**と**マイク**機能

1 つの操作は、一度にカメラで発生します。 どちらのモード (写真、ビデオ、または none) にカメラがある現在を判断するには、UnityEngine.XR.WSA.WebCam.Mode を確認することができます。

## <a name="photo-capture"></a>写真をキャプチャ

**名前空間:***UnityEngine.XR.WSA.WebCam*<br>
**種類:***PhotoCapture*

*PhotoCapture*もフォト ビデオ カメラで写真を実行することができます。 使用するための一般的なパターン*PhotoCapture*写真を撮るには、次のようにします。
1. 作成、 *PhotoCapture*オブジェクト
2. 作成、 *CameraParameters*設定を持つオブジェクト
3. 使用して写真モードを開始*StartPhotoModeAsync*
4. 目的の写真を撮る
    * (省略可能)その図との対話します。
5. 写真のモードを停止し、リソースをクリーンアップします。

### <a name="common-set-up-for-photocapture"></a>PhotoCapture の一般的なセットアップ

同じ上記の最初の 3 つの手順をまずの 3 つのすべての使用

まずを作成、 *PhotoCapture*オブジェクト

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

オブジェクトを格納、パラメーターを設定してフォト モードを開始しました次

```cs
void OnPhotoCaptureCreated(PhotoCapture captureObject)
   {
       photoCaptureObject = captureObject;

       Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

       CameraParameters c = new CameraParameters();
       c.hologramOpacity = 0.0f;
       c.cameraResolutionWidth = cameraResolution.width;
       c.cameraResolutionHeight = cameraResolution.height;
       c.pixelFormat = CapturePixelFormat.BGRA32;

       captureObject.StartPhotoModeAsync(c, false, OnPhotoModeStarted);
   }
```

最終的には、使用、ここで示すコードをクリーンアップする同じ

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

これらの手順の後に、キャプチャする写真の種類を選択できます。

### <a name="capture-a-photo-to-a-file"></a>ファイルに写真をキャプチャします。

ファイルに直接写真をキャプチャする、最も簡単な操作です。 写真は、JPG または PNG として保存できます。

写真のモードが正常に開始した場合ようになりましたが写真を撮影してディスクに保存

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format(@"CapturedImage{0}_n.jpg", Time.time);
           string filePath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

ディスクに写真をキャプチャした後に、フォト モードを終了し、オブジェクトをクリーンアップし、私たちは

```cs
void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           Debug.Log("Saved Photo to disk!");
           photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
       }
       else
       {
           Debug.Log("Failed to save Photo to disk");
       }
   }
```

### <a name="capture-a-photo-to-a-texture2d"></a>Texture2D に写真をキャプチャします。

Texture2D へのデータをキャプチャするときに、プロセスは、ディスクへのキャプチャに非常に似ています。

上記のプロセスの設定に従います。

*OnPhotoModeStarted*メモリへのフレームのキャプチャされます。

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           photoCaptureObject.TakePhotoAsync(OnCapturedPhotoToMemory);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

テクスチャに結果を適用が、上記のコードをクリーンアップする一般的な使用されいます。

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           // Create our Texture2D for use and set the correct resolution
           Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
           // Copy the raw image data into our target texture
           photoCaptureFrame.UploadImageDataToTexture(targetTexture);
           // Do as we wish with the texture such as apply it to a material, etc.
       }
       // Clean up
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>生のバイトを写真との対話をキャプチャします。

メモリ内の生バイトと対話するフレーム、に従って同じ設定には、上記の手順と*OnPhotoModeStarted* Texture2D に写真をキャプチャするようにします。 違いは*OnCapturedPhotoToMemory*生のバイトを取得し、対話機能を使用します。

この例では作成、*一覧<Color>* 処理またはを使用して、テクスチャに適用されるさらに可能性がある*SetPixels()*

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           List<byte> imageBufferList = new List<byte>();
           // Copy the raw IMFMediaBuffer data into our empty byte list.
           photoCaptureFrame.CopyRawImageDataIntoBuffer(imageBufferList);

           // In this example, we captured the image using the BGRA32 format.
           // So our stride will be 4 since we have a byte for each rgba channel.
           // The raw image data will also be flipped so we access our pixel data
           // in the reverse order.
           int stride = 4;
           float denominator = 1.0f / 255.0f;
           List<Color> colorArray = new List<Color>();
           for (int i = imageBufferList.Count - 1; i >= 0; i -= stride)
           {
               float a = (int)(imageBufferList[i - 0]) * denominator;
               float r = (int)(imageBufferList[i - 1]) * denominator;
               float g = (int)(imageBufferList[i - 2]) * denominator;
               float b = (int)(imageBufferList[i - 3]) * denominator;

               colorArray.Add(new Color(r, g, b, a));
           }
           // Now we could do something with the array such as texture.SetPixels() or run image processing on the list
       }
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

## <a name="video-capture"></a>ビデオのキャプチャ

**名前空間:***UnityEngine.XR.WSA.WebCam*<br>
**種類:***VideoCapture*

*VideoCapture*関数に非常によく似た*PhotoCapture*します。 2 つの違いはフレーム/秒 (FPS) の値を指定する必要がありますのみ .mp4 ファイルとしてディスクに直接保存することができます。 使用して手順*VideoCapture*次に示します。
1. 作成、 *VideoCapture*オブジェクト
2. 作成、 *CameraParameters*設定を持つオブジェクト
3. 使用してビデオ モードの開始*StartVideoModeAsync*
4. ビデオの録画を開始します。
5. ビデオの録音を停止します。
6. ビデオ モードを停止し、リソースをクリーンアップします。

まずを作成、 *VideoCapture*オブジェクト*VideoCapture m_VideoCapture = null;*

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

録音を開始しますパラメーターを設定します。

```cs
void OnVideoCaptureCreated (VideoCapture videoCapture)
   {
       if (videoCapture != null)
       {
           m_VideoCapture = videoCapture;

           Resolution cameraResolution = VideoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           float cameraFramerate = VideoCapture.GetSupportedFrameRatesForResolution(cameraResolution).OrderByDescending((fps) => fps).First();

           CameraParameters cameraParameters = new CameraParameters();
           cameraParameters.hologramOpacity = 0.0f;
           cameraParameters.frameRate = cameraFramerate;
           cameraParameters.cameraResolutionWidth = cameraResolution.width;
           cameraParameters.cameraResolutionHeight = cameraResolution.height;
           cameraParameters.pixelFormat = CapturePixelFormat.BGRA32;

           m_VideoCapture.StartVideoModeAsync(cameraParameters,
                                               VideoCapture.AudioState.None,
                                               OnStartedVideoCaptureMode);
       }
       else
       {
           Debug.LogError("Failed to create VideoCapture Instance!");
       }
   }
```

録音を開始しましたが開始されると、

```cs
void OnStartedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format("MyVideo_{0}.mp4", Time.time);
           string filepath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           m_VideoCapture.StartRecordingAsync(filepath, OnStartedRecordingVideo);
       }
   }
```

記録の開始後は、"stopping"を有効にするには、UI または動作を更新することが。 ここでだけ記録しています

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

後で、録画を停止します。 これは、タイマーまたはユーザーの入力、たとえばから発生する可能性があります。

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

記録が停止するをビデオ モードを停止して、リソースをクリーンアップします。

```cs
void OnStoppedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Stopped Recording Video!");
       m_VideoCapture.StopVideoModeAsync(OnStoppedVideoCaptureMode);
   }

   void OnStoppedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       m_VideoCapture.Dispose();
       m_VideoCapture = null;
   }
```

## <a name="troubleshooting"></a>トラブルシューティング
* 使用可能な解決策はありません。
    * 確認、 **web カメラ**機能は、プロジェクトで指定します。

## <a name="see-also"></a>関連項目
* [場所を特定できるカメラ](locatable-camera.md)
