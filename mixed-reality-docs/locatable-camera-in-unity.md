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
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="29f17-104">Unity での場所を特定できるカメラ</span><span class="sxs-lookup"><span data-stu-id="29f17-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="29f17-105">フォト ビデオ_カメラの機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="29f17-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="29f17-106">使用するアプリの「web カメラ」機能を宣言する必要があります、[カメラ](locatable-camera.md)します。</span><span class="sxs-lookup"><span data-stu-id="29f17-106">The "WebCam" capability must be declared for an app to use the [camera](locatable-camera.md).</span></span>
1. <span data-ttu-id="29f17-107">Unity エディターは、「> プロジェクトの設定 > プレーヤーの編集」のページに移動して、player の設定に移動します。</span><span class="sxs-lookup"><span data-stu-id="29f17-107">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="29f17-108">"Windows Store" タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="29f17-108">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="29f17-109">「発行の設定 > 機能」セクションでは、確認、 **web カメラ**と**マイク**機能</span><span class="sxs-lookup"><span data-stu-id="29f17-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="29f17-110">1 つの操作は、一度にカメラで発生します。</span><span class="sxs-lookup"><span data-stu-id="29f17-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="29f17-111">どちらのモード (写真、ビデオ、または none) にカメラがある現在を判断するには、UnityEngine.XR.WSA.WebCam.Mode を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="29f17-111">To determine which mode (photo, video, or none) the camera is currently in, you can check UnityEngine.XR.WSA.WebCam.Mode.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="29f17-112">写真をキャプチャ</span><span class="sxs-lookup"><span data-stu-id="29f17-112">Photo Capture</span></span>

<span data-ttu-id="29f17-113">\**名前空間:\*\*\*UnityEngine.XR.WSA.WebCam*</span><span class="sxs-lookup"><span data-stu-id="29f17-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="29f17-114">\**種類:\*\*\*PhotoCapture*</span><span class="sxs-lookup"><span data-stu-id="29f17-114">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="29f17-115">*PhotoCapture*もフォト ビデオ カメラで写真を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="29f17-115">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="29f17-116">使用するための一般的なパターン*PhotoCapture*写真を撮るには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="29f17-116">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="29f17-117">作成、 *PhotoCapture*オブジェクト</span><span class="sxs-lookup"><span data-stu-id="29f17-117">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="29f17-118">作成、 *CameraParameters*設定を持つオブジェクト</span><span class="sxs-lookup"><span data-stu-id="29f17-118">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="29f17-119">使用して写真モードを開始*StartPhotoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="29f17-119">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="29f17-120">目的の写真を撮る</span><span class="sxs-lookup"><span data-stu-id="29f17-120">Take the desired photo</span></span>
    * <span data-ttu-id="29f17-121">(省略可能)その図との対話します。</span><span class="sxs-lookup"><span data-stu-id="29f17-121">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="29f17-122">写真のモードを停止し、リソースをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="29f17-122">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="29f17-123">PhotoCapture の一般的なセットアップ</span><span class="sxs-lookup"><span data-stu-id="29f17-123">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="29f17-124">同じ上記の最初の 3 つの手順をまずの 3 つのすべての使用</span><span class="sxs-lookup"><span data-stu-id="29f17-124">For all three uses, we start with the same first 3 steps above</span></span>

<span data-ttu-id="29f17-125">まずを作成、 *PhotoCapture*オブジェクト</span><span class="sxs-lookup"><span data-stu-id="29f17-125">We start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="29f17-126">オブジェクトを格納、パラメーターを設定してフォト モードを開始しました次</span><span class="sxs-lookup"><span data-stu-id="29f17-126">Next we store our object, set our parameters, and start Photo Mode</span></span>

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

<span data-ttu-id="29f17-127">最終的には、使用、ここで示すコードをクリーンアップする同じ</span><span class="sxs-lookup"><span data-stu-id="29f17-127">In the end, we will also use the same clean up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="29f17-128">これらの手順の後に、キャプチャする写真の種類を選択できます。</span><span class="sxs-lookup"><span data-stu-id="29f17-128">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="29f17-129">ファイルに写真をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="29f17-129">Capture a Photo to a File</span></span>

<span data-ttu-id="29f17-130">ファイルに直接写真をキャプチャする、最も簡単な操作です。</span><span class="sxs-lookup"><span data-stu-id="29f17-130">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="29f17-131">写真は、JPG または PNG として保存できます。</span><span class="sxs-lookup"><span data-stu-id="29f17-131">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="29f17-132">写真のモードが正常に開始した場合ようになりましたが写真を撮影してディスクに保存</span><span class="sxs-lookup"><span data-stu-id="29f17-132">If we successfully started photo mode, we now will take a photo and store it on disk</span></span>

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

<span data-ttu-id="29f17-133">ディスクに写真をキャプチャした後に、フォト モードを終了し、オブジェクトをクリーンアップし、私たちは</span><span class="sxs-lookup"><span data-stu-id="29f17-133">After capturing the photo to disk, we will exit photo mode and then clean up our objects</span></span>

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

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="29f17-134">Texture2D に写真をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="29f17-134">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="29f17-135">Texture2D へのデータをキャプチャするときに、プロセスは、ディスクへのキャプチャに非常に似ています。</span><span class="sxs-lookup"><span data-stu-id="29f17-135">When capturing data to a Texture2D, the process is extremely similar to capturing to disk.</span></span>

<span data-ttu-id="29f17-136">上記のプロセスの設定に従います。</span><span class="sxs-lookup"><span data-stu-id="29f17-136">We will follow the set up process above.</span></span>

<span data-ttu-id="29f17-137">*OnPhotoModeStarted*メモリへのフレームのキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="29f17-137">In *OnPhotoModeStarted*, we will capture a frame to memory.</span></span>

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

<span data-ttu-id="29f17-138">テクスチャに結果を適用が、上記のコードをクリーンアップする一般的な使用されいます。</span><span class="sxs-lookup"><span data-stu-id="29f17-138">We will then apply our result to a texture and use the common clean up code above.</span></span>

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="29f17-139">生のバイトを写真との対話をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="29f17-139">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="29f17-140">メモリ内の生バイトと対話するフレーム、に従って同じ設定には、上記の手順と*OnPhotoModeStarted* Texture2D に写真をキャプチャするようにします。</span><span class="sxs-lookup"><span data-stu-id="29f17-140">To interact with the raw bytes of an in memory frame, we will follow the same set up steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="29f17-141">違いは*OnCapturedPhotoToMemory*生のバイトを取得し、対話機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="29f17-141">The difference is in *OnCapturedPhotoToMemory* where we can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="29f17-142">この例では作成、*一覧<Color>* 処理またはを使用して、テクスチャに適用されるさらに可能性がある*SetPixels()*</span><span class="sxs-lookup"><span data-stu-id="29f17-142">In this example, we will create a *List<Color>* which could be further processed or applied to a texture via *SetPixels()*</span></span>

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

## <a name="video-capture"></a><span data-ttu-id="29f17-143">ビデオのキャプチャ</span><span class="sxs-lookup"><span data-stu-id="29f17-143">Video Capture</span></span>

<span data-ttu-id="29f17-144">\**名前空間:\*\*\*UnityEngine.XR.WSA.WebCam*</span><span class="sxs-lookup"><span data-stu-id="29f17-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="29f17-145">\**種類:\*\*\*VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="29f17-145">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="29f17-146">*VideoCapture*関数に非常によく似た*PhotoCapture*します。</span><span class="sxs-lookup"><span data-stu-id="29f17-146">*VideoCapture* functions very similarly to *PhotoCapture*.</span></span> <span data-ttu-id="29f17-147">2 つの違いはフレーム/秒 (FPS) の値を指定する必要がありますのみ .mp4 ファイルとしてディスクに直接保存することができます。</span><span class="sxs-lookup"><span data-stu-id="29f17-147">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as an .mp4 file.</span></span> <span data-ttu-id="29f17-148">使用して手順*VideoCapture*次に示します。</span><span class="sxs-lookup"><span data-stu-id="29f17-148">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="29f17-149">作成、 *VideoCapture*オブジェクト</span><span class="sxs-lookup"><span data-stu-id="29f17-149">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="29f17-150">作成、 *CameraParameters*設定を持つオブジェクト</span><span class="sxs-lookup"><span data-stu-id="29f17-150">Create a *CameraParameters* object with the settings we want</span></span>
3. <span data-ttu-id="29f17-151">使用してビデオ モードの開始*StartVideoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="29f17-151">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="29f17-152">ビデオの録画を開始します。</span><span class="sxs-lookup"><span data-stu-id="29f17-152">Start recording video</span></span>
5. <span data-ttu-id="29f17-153">ビデオの録音を停止します。</span><span class="sxs-lookup"><span data-stu-id="29f17-153">Stop recording video</span></span>
6. <span data-ttu-id="29f17-154">ビデオ モードを停止し、リソースをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="29f17-154">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="29f17-155">まずを作成、 *VideoCapture*オブジェクト*VideoCapture m_VideoCapture = null;*</span><span class="sxs-lookup"><span data-stu-id="29f17-155">We start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="29f17-156">録音を開始しますパラメーターを設定します。</span><span class="sxs-lookup"><span data-stu-id="29f17-156">We then will set up the parameters we will want for the recording and start.</span></span>

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

<span data-ttu-id="29f17-157">録音を開始しましたが開始されると、</span><span class="sxs-lookup"><span data-stu-id="29f17-157">Once started, we will begin the recording</span></span>

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

<span data-ttu-id="29f17-158">記録の開始後は、"stopping"を有効にするには、UI または動作を更新することが。</span><span class="sxs-lookup"><span data-stu-id="29f17-158">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="29f17-159">ここでだけ記録しています</span><span class="sxs-lookup"><span data-stu-id="29f17-159">Here we just log</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="29f17-160">後で、録画を停止します。</span><span class="sxs-lookup"><span data-stu-id="29f17-160">At a later point, we will want to stop the recording.</span></span> <span data-ttu-id="29f17-161">これは、タイマーまたはユーザーの入力、たとえばから発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="29f17-161">This could happen from a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="29f17-162">記録が停止するをビデオ モードを停止して、リソースをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="29f17-162">Once the recording has stopped, we will stop video mode and clean up our resources.</span></span>

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

## <a name="troubleshooting"></a><span data-ttu-id="29f17-163">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="29f17-163">Troubleshooting</span></span>
* <span data-ttu-id="29f17-164">使用可能な解決策はありません。</span><span class="sxs-lookup"><span data-stu-id="29f17-164">No resolutions are available</span></span>
    * <span data-ttu-id="29f17-165">確認、 **web カメラ**機能は、プロジェクトで指定します。</span><span class="sxs-lookup"><span data-stu-id="29f17-165">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="29f17-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="29f17-166">See Also</span></span>
* [<span data-ttu-id="29f17-167">場所を特定できるカメラ</span><span class="sxs-lookup"><span data-stu-id="29f17-167">Locatable camera</span></span>](locatable-camera.md)
