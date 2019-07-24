---
title: Unity でのお持ちのカメラ
description: Unity での HoloLens によるカメラの使用。
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 写真、ビデオ、hololens、カメラ、unity、お持ちの場合
ms.openlocfilehash: f0183400f55b1c6663a9a20ab4992befe5ad0718
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515438"
---
# <a name="locatable-camera-in-unity"></a>Unity でのお持ちのカメラ

## <a name="enabling-the-capability-for-photo-video-camera"></a>フォトビデオカメラの機能を有効にする

アプリで[カメラ](locatable-camera.md)を使用するには、"WebCam" 機能を宣言する必要があります。
1. Unity エディターで、[Edit > Project Settings > Player] ページに移動して、windows media player の設定に移動します。
2. [Windows ストア] タブをクリックします。
3. [発行設定 > 機能] セクションで、 **Web カメラ**と**マイク**の機能を確認します。

カメラで一度に実行できる操作は1つだけです。 カメラを現在使用しているモード (写真、ビデオ、またはなし) を確認するには、UnityEngine. XR を確認します。

## <a name="photo-capture"></a>写真のキャプチャ

**名前空間:** *UnityEngine. XR*<br>
**種類:** *PhotoCapture*

*Photocapture*の種類を使用すると、写真ビデオカメラで引き続き写真を撮ることができます。 *Photocapture*を使用して写真を撮影する一般的なパターンを次に示します。
1. *Photocapture*オブジェクトを作成する
2. 必要な設定で*CameraParameters*オブジェクトを作成する
3. *Startphotomodeasync*を使用して写真モードを開始する
4. 目的の写真を撮影する
    * optionalその画像と対話する
5. フォトモードを停止してリソースをクリーンアップする

### <a name="common-set-up-for-photocapture"></a>PhotoCapture 用の一般的な設定

3つのすべての使用について、上記と同じ最初の3つの手順から開始します。

まず、 *Photocapture*オブジェクトを作成します。

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

次に、オブジェクトを保存し、パラメーターを設定して、写真モードを開始します。

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

最後に、ここで紹介したものと同じクリーンアップコードを使用します。

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

これらの手順の後に、キャプチャする写真の種類を選択できます。

### <a name="capture-a-photo-to-a-file"></a>写真をファイルにキャプチャする

最も簡単な操作は、写真を直接ファイルにキャプチャすることです。 写真は、JPG または PNG として保存できます。

写真モードを正常に開始した場合は、写真を撮影してディスクに保存します。

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

写真をディスクにキャプチャした後、写真モードを終了し、オブジェクトをクリーンアップします。

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

### <a name="capture-a-photo-to-a-texture2d"></a>写真を Texture2D に取り込む

Texture2D にデータをキャプチャする場合、プロセスはディスクへのキャプチャと非常によく似ています。

上記のセットアッププロセスに従います。

*Onphotomodestarted 開始*したときに、フレームをメモリにキャプチャします。

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

次に、結果をテクスチャに適用し、上記の一般的なクリーンアップコードを使用します。

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>写真をキャプチャし、生のバイトを操作する

インメモリフレームの生バイトを操作するには、Texture2D に写真をキャプチャする場合と同じように、上記と*Onphotomodestarted 開始*したときと同じセットアップ手順に従います。 違いは、生のバイトを取得して操作できる*OnCapturedPhotoToMemory*です。

この例では、 *setpixels ()* を使用してさらに処理またはテクスチャに適用できる*リスト<Color>* を作成します。

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

## <a name="video-capture"></a>ビデオキャプチャ

**名前空間:** *UnityEngine. XR*<br>
**種類:** *VideoCapture*

*VideoCapture*は*photocapture*と非常に似ています。 2つの違いは、1秒あたりのフレーム数 (FPS) の値を指定する必要があり、mp4 ファイルとして直接ディスクに保存できることだけです。 *VideoCapture*を使用する手順は次のとおりです。
1. *VideoCapture*オブジェクトを作成する
2. 必要な設定で*CameraParameters*オブジェクトを作成する
3. *Startvideomodeasync*を使用してビデオモードを開始する
4. ビデオの録画を開始する
5. ビデオ記録の停止
6. ビデオモードを停止してリソースをクリーンアップする

まず、 *VideoCapture*オブジェクト*VideoCapture m_VideoCapture = null*を作成します。

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

次に、記録と開始のために必要なパラメーターを設定します。

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

開始したら、記録を開始します。

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

記録が開始されたら、UI または動作を更新して停止を有効にすることができます。 ここでログを記録します。

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

後で、記録を停止します。 これは、たとえば、タイマーやユーザー入力によって発生する可能性があります。

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

記録が停止したら、ビデオモードを停止し、リソースをクリーンアップします。

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
* 解決策はありません
    * **Web カメラ**機能がプロジェクトで指定されていることを確認します。

## <a name="see-also"></a>関連項目
* [場所を特定できるカメラ](locatable-camera.md)
