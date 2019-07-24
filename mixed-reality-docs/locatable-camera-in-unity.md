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
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="9fe30-104">Unity でのお持ちのカメラ</span><span class="sxs-lookup"><span data-stu-id="9fe30-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="9fe30-105">フォトビデオカメラの機能を有効にする</span><span class="sxs-lookup"><span data-stu-id="9fe30-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="9fe30-106">アプリで[カメラ](locatable-camera.md)を使用するには、"WebCam" 機能を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9fe30-106">The "WebCam" capability must be declared for an app to use the [camera](locatable-camera.md).</span></span>
1. <span data-ttu-id="9fe30-107">Unity エディターで、[Edit > Project Settings > Player] ページに移動して、windows media player の設定に移動します。</span><span class="sxs-lookup"><span data-stu-id="9fe30-107">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="9fe30-108">[Windows ストア] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9fe30-108">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="9fe30-109">[発行設定 > 機能] セクションで、 **Web カメラ**と**マイク**の機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="9fe30-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="9fe30-110">カメラで一度に実行できる操作は1つだけです。</span><span class="sxs-lookup"><span data-stu-id="9fe30-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="9fe30-111">カメラを現在使用しているモード (写真、ビデオ、またはなし) を確認するには、UnityEngine. XR を確認します。</span><span class="sxs-lookup"><span data-stu-id="9fe30-111">To determine which mode (photo, video, or none) the camera is currently in, you can check UnityEngine.XR.WSA.WebCam.Mode.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="9fe30-112">写真のキャプチャ</span><span class="sxs-lookup"><span data-stu-id="9fe30-112">Photo Capture</span></span>

<span data-ttu-id="9fe30-113">**名前空間:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="9fe30-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="9fe30-114">**種類:** *PhotoCapture*</span><span class="sxs-lookup"><span data-stu-id="9fe30-114">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="9fe30-115">*Photocapture*の種類を使用すると、写真ビデオカメラで引き続き写真を撮ることができます。</span><span class="sxs-lookup"><span data-stu-id="9fe30-115">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="9fe30-116">*Photocapture*を使用して写真を撮影する一般的なパターンを次に示します。</span><span class="sxs-lookup"><span data-stu-id="9fe30-116">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="9fe30-117">*Photocapture*オブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="9fe30-117">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="9fe30-118">必要な設定で*CameraParameters*オブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="9fe30-118">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="9fe30-119">*Startphotomodeasync*を使用して写真モードを開始する</span><span class="sxs-lookup"><span data-stu-id="9fe30-119">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="9fe30-120">目的の写真を撮影する</span><span class="sxs-lookup"><span data-stu-id="9fe30-120">Take the desired photo</span></span>
    * <span data-ttu-id="9fe30-121">optionalその画像と対話する</span><span class="sxs-lookup"><span data-stu-id="9fe30-121">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="9fe30-122">フォトモードを停止してリソースをクリーンアップする</span><span class="sxs-lookup"><span data-stu-id="9fe30-122">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="9fe30-123">PhotoCapture 用の一般的な設定</span><span class="sxs-lookup"><span data-stu-id="9fe30-123">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="9fe30-124">3つのすべての使用について、上記と同じ最初の3つの手順から開始します。</span><span class="sxs-lookup"><span data-stu-id="9fe30-124">For all three uses, we start with the same first 3 steps above</span></span>

<span data-ttu-id="9fe30-125">まず、 *Photocapture*オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9fe30-125">We start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="9fe30-126">次に、オブジェクトを保存し、パラメーターを設定して、写真モードを開始します。</span><span class="sxs-lookup"><span data-stu-id="9fe30-126">Next we store our object, set our parameters, and start Photo Mode</span></span>

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

<span data-ttu-id="9fe30-127">最後に、ここで紹介したものと同じクリーンアップコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="9fe30-127">In the end, we will also use the same clean up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="9fe30-128">これらの手順の後に、キャプチャする写真の種類を選択できます。</span><span class="sxs-lookup"><span data-stu-id="9fe30-128">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="9fe30-129">写真をファイルにキャプチャする</span><span class="sxs-lookup"><span data-stu-id="9fe30-129">Capture a Photo to a File</span></span>

<span data-ttu-id="9fe30-130">最も簡単な操作は、写真を直接ファイルにキャプチャすることです。</span><span class="sxs-lookup"><span data-stu-id="9fe30-130">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="9fe30-131">写真は、JPG または PNG として保存できます。</span><span class="sxs-lookup"><span data-stu-id="9fe30-131">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="9fe30-132">写真モードを正常に開始した場合は、写真を撮影してディスクに保存します。</span><span class="sxs-lookup"><span data-stu-id="9fe30-132">If we successfully started photo mode, we now will take a photo and store it on disk</span></span>

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

<span data-ttu-id="9fe30-133">写真をディスクにキャプチャした後、写真モードを終了し、オブジェクトをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="9fe30-133">After capturing the photo to disk, we will exit photo mode and then clean up our objects</span></span>

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

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="9fe30-134">写真を Texture2D に取り込む</span><span class="sxs-lookup"><span data-stu-id="9fe30-134">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="9fe30-135">Texture2D にデータをキャプチャする場合、プロセスはディスクへのキャプチャと非常によく似ています。</span><span class="sxs-lookup"><span data-stu-id="9fe30-135">When capturing data to a Texture2D, the process is extremely similar to capturing to disk.</span></span>

<span data-ttu-id="9fe30-136">上記のセットアッププロセスに従います。</span><span class="sxs-lookup"><span data-stu-id="9fe30-136">We will follow the set up process above.</span></span>

<span data-ttu-id="9fe30-137">*Onphotomodestarted 開始*したときに、フレームをメモリにキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="9fe30-137">In *OnPhotoModeStarted*, we will capture a frame to memory.</span></span>

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

<span data-ttu-id="9fe30-138">次に、結果をテクスチャに適用し、上記の一般的なクリーンアップコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="9fe30-138">We will then apply our result to a texture and use the common clean up code above.</span></span>

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="9fe30-139">写真をキャプチャし、生のバイトを操作する</span><span class="sxs-lookup"><span data-stu-id="9fe30-139">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="9fe30-140">インメモリフレームの生バイトを操作するには、Texture2D に写真をキャプチャする場合と同じように、上記と*Onphotomodestarted 開始*したときと同じセットアップ手順に従います。</span><span class="sxs-lookup"><span data-stu-id="9fe30-140">To interact with the raw bytes of an in memory frame, we will follow the same set up steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="9fe30-141">違いは、生のバイトを取得して操作できる*OnCapturedPhotoToMemory*です。</span><span class="sxs-lookup"><span data-stu-id="9fe30-141">The difference is in *OnCapturedPhotoToMemory* where we can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="9fe30-142">この例では、 *setpixels ()* を使用してさらに処理またはテクスチャに適用できる*リスト<Color>* を作成します。</span><span class="sxs-lookup"><span data-stu-id="9fe30-142">In this example, we will create a *List<Color>* which could be further processed or applied to a texture via *SetPixels()*</span></span>

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

## <a name="video-capture"></a><span data-ttu-id="9fe30-143">ビデオキャプチャ</span><span class="sxs-lookup"><span data-stu-id="9fe30-143">Video Capture</span></span>

<span data-ttu-id="9fe30-144">**名前空間:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="9fe30-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="9fe30-145">**種類:** *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="9fe30-145">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="9fe30-146">*VideoCapture*は*photocapture*と非常に似ています。</span><span class="sxs-lookup"><span data-stu-id="9fe30-146">*VideoCapture* functions very similarly to *PhotoCapture*.</span></span> <span data-ttu-id="9fe30-147">2つの違いは、1秒あたりのフレーム数 (FPS) の値を指定する必要があり、mp4 ファイルとして直接ディスクに保存できることだけです。</span><span class="sxs-lookup"><span data-stu-id="9fe30-147">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as an .mp4 file.</span></span> <span data-ttu-id="9fe30-148">*VideoCapture*を使用する手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9fe30-148">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="9fe30-149">*VideoCapture*オブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="9fe30-149">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="9fe30-150">必要な設定で*CameraParameters*オブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="9fe30-150">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="9fe30-151">*Startvideomodeasync*を使用してビデオモードを開始する</span><span class="sxs-lookup"><span data-stu-id="9fe30-151">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="9fe30-152">ビデオの録画を開始する</span><span class="sxs-lookup"><span data-stu-id="9fe30-152">Start recording video</span></span>
5. <span data-ttu-id="9fe30-153">ビデオ記録の停止</span><span class="sxs-lookup"><span data-stu-id="9fe30-153">Stop recording video</span></span>
6. <span data-ttu-id="9fe30-154">ビデオモードを停止してリソースをクリーンアップする</span><span class="sxs-lookup"><span data-stu-id="9fe30-154">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="9fe30-155">まず、 *VideoCapture*オブジェクト*VideoCapture m_VideoCapture = null*を作成します。</span><span class="sxs-lookup"><span data-stu-id="9fe30-155">We start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="9fe30-156">次に、記録と開始のために必要なパラメーターを設定します。</span><span class="sxs-lookup"><span data-stu-id="9fe30-156">We then will set up the parameters we will want for the recording and start.</span></span>

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

<span data-ttu-id="9fe30-157">開始したら、記録を開始します。</span><span class="sxs-lookup"><span data-stu-id="9fe30-157">Once started, we will begin the recording</span></span>

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

<span data-ttu-id="9fe30-158">記録が開始されたら、UI または動作を更新して停止を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="9fe30-158">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="9fe30-159">ここでログを記録します。</span><span class="sxs-lookup"><span data-stu-id="9fe30-159">Here we just log</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="9fe30-160">後で、記録を停止します。</span><span class="sxs-lookup"><span data-stu-id="9fe30-160">At a later point, we will want to stop the recording.</span></span> <span data-ttu-id="9fe30-161">これは、たとえば、タイマーやユーザー入力によって発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9fe30-161">This could happen from a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="9fe30-162">記録が停止したら、ビデオモードを停止し、リソースをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="9fe30-162">Once the recording has stopped, we will stop video mode and clean up our resources.</span></span>

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

## <a name="troubleshooting"></a><span data-ttu-id="9fe30-163">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="9fe30-163">Troubleshooting</span></span>
* <span data-ttu-id="9fe30-164">解決策はありません</span><span class="sxs-lookup"><span data-stu-id="9fe30-164">No resolutions are available</span></span>
    * <span data-ttu-id="9fe30-165">**Web カメラ**機能がプロジェクトで指定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9fe30-165">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="9fe30-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="9fe30-166">See Also</span></span>
* [<span data-ttu-id="9fe30-167">場所を特定できるカメラ</span><span class="sxs-lookup"><span data-stu-id="9fe30-167">Locatable camera</span></span>](locatable-camera.md)
