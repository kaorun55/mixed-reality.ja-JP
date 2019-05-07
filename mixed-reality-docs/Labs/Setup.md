# <a name="setting-up"></a><span data-ttu-id="68532-101">設定します。</span><span class="sxs-lookup"><span data-stu-id="68532-101">Setting Up</span></span>

<span data-ttu-id="68532-102">Azure の Kinect DK API の概要ですか。</span><span class="sxs-lookup"><span data-stu-id="68532-102">Getting started with the Azure Kinect DK API?</span></span> <span data-ttu-id="68532-103">探す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="68532-103">Look no further!</span></span> <span data-ttu-id="68532-104">このドキュメントが揃って稼働しているアクセス権を持つデバイスに!</span><span class="sxs-lookup"><span data-stu-id="68532-104">This document will get you up and running with access to the device!</span></span>

<span data-ttu-id="68532-105">まず、ダウンロードしてインストール、 [Azure Kinect DK API](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK) Github から。</span><span class="sxs-lookup"><span data-stu-id="68532-105">First, download and install the [Azure Kinect DK API](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK) from Github.</span></span>

<span data-ttu-id="68532-106">**目次**</span><span class="sxs-lookup"><span data-stu-id="68532-106">**Contents**</span></span>  
[<span data-ttu-id="68532-107">ヘッダー</span><span class="sxs-lookup"><span data-stu-id="68532-107">Headers</span></span>](#Headers)  
[<span data-ttu-id="68532-108">Kinect デバイスの検索</span><span class="sxs-lookup"><span data-stu-id="68532-108">Finding a Kinect Device</span></span>](#Finding-a-Kinect-Device)  
[<span data-ttu-id="68532-109">カメラの開始</span><span class="sxs-lookup"><span data-stu-id="68532-109">Starting the Cameras</span></span>](#Starting-the-Cameras)  
[<span data-ttu-id="68532-110">エラー処理</span><span class="sxs-lookup"><span data-stu-id="68532-110">Error Handling</span></span>](#Error-Handling)  
[<span data-ttu-id="68532-111">完全なソース</span><span class="sxs-lookup"><span data-stu-id="68532-111">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="68532-112">**使用して関数を次に示します。**</span><span class="sxs-lookup"><span data-stu-id="68532-112">**Here are the functions we'll use:**</span></span>  
[`k4a_device_get_installed_count()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count)  
[`k4a_device_open()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)  
[`k4a_device_get_serialnum()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-serialnum)  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_device_stop_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-stop-cameras)  
[`k4a_device_close()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)

## <a name="headers"></a><span data-ttu-id="68532-113">ヘッダー</span><span class="sxs-lookup"><span data-stu-id="68532-113">Headers</span></span>
<span data-ttu-id="68532-114">必要となる 1 つだけのヘッダーがあるし、k4a.h です!</span><span class="sxs-lookup"><span data-stu-id="68532-114">There's only one header that you'll need, and that's k4a.h!</span></span> <span data-ttu-id="68532-115">SDK のライブラリで任意のコンパイラを設定するかどうかを確認し、フォルダーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="68532-115">Make sure your compiler of choice is set up with the SDK's lib and include folders.</span></span> <span data-ttu-id="68532-116">リンク k4a.lib と k4a.dll ファイルも必要になります。</span><span class="sxs-lookup"><span data-stu-id="68532-116">You'll also need the k4a.lib and k4a.dll files linked up.</span></span>
```C
#include <k4a/k4a.h>
```

## <a name="finding-a-kinect-device"></a><span data-ttu-id="68532-117">Kinect デバイスの検索</span><span class="sxs-lookup"><span data-stu-id="68532-117">Finding a Kinect Device</span></span>

![](img/Serial.png)

<span data-ttu-id="68532-118">複数の Azure Kinect DK デバイスは、コンピューターに接続できます。</span><span class="sxs-lookup"><span data-stu-id="68532-118">Multiple Azure Kinect DK devices can be connected to your computer!</span></span> <span data-ttu-id="68532-119">最初に、数を検索してを起動しますか、まったくを使用していずれかに接続している場合、 [ `k4a_device_get_installed_count` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count)関数。</span><span class="sxs-lookup"><span data-stu-id="68532-119">We'll first start by finding out how many, or if any are connected at all using the [`k4a_device_get_installed_count`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count) function.</span></span> <span data-ttu-id="68532-120">この関数は、追加設定なしすぐ、機能する必要があります!</span><span class="sxs-lookup"><span data-stu-id="68532-120">This function should work right away, without any additional setup!</span></span>

```C
uint32_t count = k4a_device_get_installed_count();
```

<span data-ttu-id="68532-121">使用して開くことができますわかったらがありますが実際には、デバイスに接続されているコンピューター、 [ `k4a_device_open`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)します。</span><span class="sxs-lookup"><span data-stu-id="68532-121">Once you've determined there is actually a device connected to the computer, you can open it using [`k4a_device_open`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open).</span></span> <span data-ttu-id="68532-122">インデックスを指定することができますを開くには、必要なデバイスのまたはを使用できます[ `K4A_DEVICE_DEFAULT` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT) 1 つ目です。</span><span class="sxs-lookup"><span data-stu-id="68532-122">You can provide the index of the device you want to open, or you can just use [`K4A_DEVICE_DEFAULT`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT) for the first one.</span></span>

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
k4a_device_open(K4A_DEVICE_DEFAULT, &device);
```
<span data-ttu-id="68532-123">として k4a API で多くのものと、何かを開くときにする必要がありますも閉じる操作を終了したら!</span><span class="sxs-lookup"><span data-stu-id="68532-123">As with most things in the k4a API, when you open something, you should also close it when you're finished with it!</span></span> <span data-ttu-id="68532-124">呼び出しをシャット ダウンしている場合に注意して[ `k4a_device_close`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)します。</span><span class="sxs-lookup"><span data-stu-id="68532-124">When you're shutting down, remember to make a call to [`k4a_device_close`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close).</span></span>

```C
k4a_device_close(device);
```

<span data-ttu-id="68532-125">デバイスが開いたら、すばらしいことを確認する本当に簡単なテストを実行できます。</span><span class="sxs-lookup"><span data-stu-id="68532-125">Once the device is open, we can make a really simple test to ensure it's all good.</span></span> <span data-ttu-id="68532-126">デバイスのシリアル番号を読み取てしましょう!</span><span class="sxs-lookup"><span data-stu-id="68532-126">So let's read the device's serial number!</span></span>

```C
// Get the size of the serial number
size_t serial_size = 0;
k4a_device_get_serialnum(device, NULL, &serial_size);

// Allocate memory for the serial, then acquire it
char *serial = static_cast<char*>(malloc(serial_size));
k4a_device_get_serialnum(device, serial, &serial_size);
printf("Opened device: %s\n", serial);
free(serial);
```

## <a name="starting-the-cameras"></a><span data-ttu-id="68532-127">カメラの開始</span><span class="sxs-lookup"><span data-stu-id="68532-127">Starting the Cameras</span></span>

<span data-ttu-id="68532-128">デバイスを開くことでカメラを構成する必要があります、 [ `k4a_device_configuration_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="68532-128">Once you've opened the device, you'll need to configure the camera with a [`k4a_device_configuration_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t) object!</span></span> <span data-ttu-id="68532-129">カメラの構成では、各種のオプションの数と、独自のシナリオに最適な設定を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68532-129">Camera configuration has a number of different options, and you'll need to choose the settings that best fit your own scenario.</span></span>

```C
// Configure a stream of 4096x3072 BRGA color data at 15 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_15;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_3072P;

// Start the camera with the given configuration
k4a_device_start_cameras(device, &config)

// ...Camera capture and application specific code would go here...

// Shut down the camera when finished with application logic
k4a_device_stop_cameras(device);
```

<span data-ttu-id="68532-130">構成の詳細について、__色__カメラ、[このドキュメントをチェック アウト]()!</span><span class="sxs-lookup"><span data-stu-id="68532-130">For configuration details about the __color__ camera, [check out this document]()!</span></span>  
<span data-ttu-id="68532-131">構成の詳細について、__深さ__カメラ、[このドキュメントをチェック アウト]()!</span><span class="sxs-lookup"><span data-stu-id="68532-131">For configuration details about the __depth__ camera, [check out this document]()!</span></span>

## <a name="error-handling"></a><span data-ttu-id="68532-132">エラー処理</span><span class="sxs-lookup"><span data-stu-id="68532-132">Error Handling</span></span>

<span data-ttu-id="68532-133">説明を簡潔にするため、わかりやすくするためには、インライン例をいくつかのエラー処理を紹介はありません。</span><span class="sxs-lookup"><span data-stu-id="68532-133">For the sake of brevity and clarity, we don't show error handling in some inline examples.</span></span> <span data-ttu-id="68532-134">ただし、エラー処理では、常に重要です。</span><span class="sxs-lookup"><span data-stu-id="68532-134">However, error handling is always important!</span></span> <span data-ttu-id="68532-135">多くの関数が成功/失敗の一般的な型を返す[ `k4a_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t)、具体的なバリアントの詳細情報または[ `k4a_wait_result_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t)します。</span><span class="sxs-lookup"><span data-stu-id="68532-135">Many functions will return a general success/failure type [`k4a_result_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t), or a more specific variant with detailed information such as [`k4a_wait_result_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t).</span></span> <span data-ttu-id="68532-136">ドキュメントを確認してください、またはどのようなエラー メッセージを表示する特定の関数の intellisense に期待する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="68532-136">Be sure to check the docs or intellisense of a specific function to see what error messages you might expect to see from it!</span></span>

<span data-ttu-id="68532-137">エラーの種類とも、 [ `K4A_SUCCEEDED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED)と[ `K4A_FAILED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED)それらで使用できるマクロ。</span><span class="sxs-lookup"><span data-stu-id="68532-137">Along with the error types, there's also the [`K4A_SUCCEEDED`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED) and [`K4A_FAILED`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED) macros that you can use with them.</span></span> <span data-ttu-id="68532-138">したがって k4a デバイスを開くだけで、代わりに、このような保護可能性があります。</span><span class="sxs-lookup"><span data-stu-id="68532-138">So instead of just opening a k4a device, we might guard it like this:</span></span>

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
if ( K4A_FAILED( k4a_device_open(K4A_DEVICE_DEFAULT, &device) ) )
{
    printf("Failed to open k4a device!\n");
    return;
}
```

# <a name="full-source"></a><span data-ttu-id="68532-139">完全なソース</span><span class="sxs-lookup"><span data-stu-id="68532-139">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

int main()
{
    uint32_t count = k4a_device_get_installed_count();
    if (count == 0)
    {
        printf("No k4a devices attached!\n");
        return 0;
    }

    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    if (K4A_FAILED(k4a_device_open(K4A_DEVICE_DEFAULT, &device)))
    {
        printf("Failed to open k4a device!\n");
        return 0;
    }

    // Get the size of the serial number
    size_t serial_size = 0;
    k4a_device_get_serialnum(device, NULL, &serial_size);

    // Allocate memory for the serial, then acquire it
    char* serial = static_cast<char*>(malloc(serial_size));
    k4a_device_get_serialnum(device, serial, &serial_size);
    printf("Opened device: %s\n", serial);
    free(serial);

    // Configure a stream of 4096x3072 BRGA color data at 15 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps = K4A_FRAMES_PER_SECOND_15;
    config.color_format = K4A_IMAGE_FORMAT_COLOR_BGRA32;
    config.color_resolution = K4A_COLOR_RESOLUTION_3072P;

    // Start the camera with the given configuration
    if (K4A_FAILED(k4a_device_start_cameras(device, &config)))
    {
        printf("Failed to start cameras!\n");
        k4a_device_close(device);
        return 0;
    }

    // ...Camera capture and application specific code would go here...

    // Shut down the camera when finished with application logic
    k4a_device_stop_cameras(device);
    k4a_device_close(device);

    return 0;
}
```

## <a name="next-lab---reading-depth-datareaddepthmd"></a><span data-ttu-id="68532-140">次の実習 -[深さデータの読み取り](ReadDepth.md)</span><span class="sxs-lookup"><span data-stu-id="68532-140">Next Lab - [Reading Depth Data](ReadDepth.md)</span></span>
