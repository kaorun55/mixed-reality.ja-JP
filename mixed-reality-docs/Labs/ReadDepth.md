# <a name="reading-depth-data"></a><span data-ttu-id="c63ec-101">深さのデータの読み取り</span><span class="sxs-lookup"><span data-stu-id="c63ec-101">Reading Depth Data</span></span>

<span data-ttu-id="c63ec-102">デバイスからの深さのデータを読み取る必要がありますか。</span><span class="sxs-lookup"><span data-stu-id="c63ec-102">Need to read depth data from the device?</span></span> <span data-ttu-id="c63ec-103">簡単です！</span><span class="sxs-lookup"><span data-stu-id="c63ec-103">It's easy!</span></span>

<span data-ttu-id="c63ec-104">**目次**</span><span class="sxs-lookup"><span data-stu-id="c63ec-104">**Contents**</span></span>  
[<span data-ttu-id="c63ec-105">デバイスを構成します。</span><span class="sxs-lookup"><span data-stu-id="c63ec-105">Configuring the Device</span></span>](#Configuring-the-Device)  
[<span data-ttu-id="c63ec-106">データへのアクセス</span><span class="sxs-lookup"><span data-stu-id="c63ec-106">Acessing Depth Data</span></span>](#Acessing-Depth-Data)  
[<span data-ttu-id="c63ec-107">クリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="c63ec-107">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="c63ec-108">完全なソース</span><span class="sxs-lookup"><span data-stu-id="c63ec-108">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="c63ec-109">**使用して関数を次に示します。**</span><span class="sxs-lookup"><span data-stu-id="c63ec-109">**Here are the functions we'll use:**</span></span>  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_depth_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-depth-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release)  

## <a name="configuring-the-device"></a><span data-ttu-id="c63ec-110">デバイスを構成します。</span><span class="sxs-lookup"><span data-stu-id="c63ec-110">Configuring the Device</span></span>

<span data-ttu-id="c63ec-111">後[インターフェイスを開く]()Azure Kinect DK デバイスには、データをキャプチャするためのカメラを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c63ec-111">After [opening an interface]() to the Azure Kinect DK device, you'll need to configure the camera for capturing depth data.</span></span> <span data-ttu-id="c63ec-112">1 つだけの項目の深さを構成する際に知って本当に必要があることと、 `depth_mode`!</span><span class="sxs-lookup"><span data-stu-id="c63ec-112">There's only one item you really need to know about when configuring depth, and that's the `depth_mode`!</span></span>

```C
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.depth_mode = K4A_DEPTH_MODE_NFOV_UNBINNED;

k4a_device_start_cameras(device, &config);
```

<span data-ttu-id="c63ec-113">ここで、`depth_mode`いくつかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="c63ec-113">Here the `depth_mode` has a couple choices!</span></span> <span data-ttu-id="c63ec-114">アプリケーションのコンテキストに応じて、さまざまな形式でデータを要求できます。</span><span class="sxs-lookup"><span data-stu-id="c63ec-114">Depending on the context of our application, we can request our depth data in different formats.</span></span>

<span data-ttu-id="c63ec-115">深さのデータにアルゴリズムの時間の制約付き実行しているでしょうか。</span><span class="sxs-lookup"><span data-stu-id="c63ec-115">Are you running time constrained algorithms on the depth data?</span></span> <span data-ttu-id="c63ec-116">必要なデータを操作するため、2X2BINNED モードを選択かもしれません。</span><span class="sxs-lookup"><span data-stu-id="c63ec-116">Maybe pick a 2X2BINNED mode so there's less data to operate on!</span></span> <span data-ttu-id="c63ec-117">関心があるよりははるかに直接アウトは閉じるのではなく、視界に先行しますか?</span><span class="sxs-lookup"><span data-stu-id="c63ec-117">Do you care more about what's far out directly ahead, rather than what's close and in the periphery?</span></span> <span data-ttu-id="c63ec-118">フィールドの表示の幅が狭いを使用して、NFOV モード。</span><span class="sxs-lookup"><span data-stu-id="c63ec-118">Use a narrow field of view with the NFOV modes!</span></span>
| [`depth_mode`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-depth-mode-t) | <span data-ttu-id="c63ec-119">description</span><span class="sxs-lookup"><span data-stu-id="c63ec-119">description</span></span> |
|------------|-------------|
|`K4A_DEPTH_MODE_WFOV_UNBINNED`|<span data-ttu-id="c63ec-120">さまざまな角度ビュー (120 x 120) 浅い深度 (0.25-2.21 m) データの高解像度 (1024 x 1024)。</span><span class="sxs-lookup"><span data-stu-id="c63ec-120">Wide angle view (120x120), shallow depth (0.25-2.21m), high data resolution (1024x1024).</span></span> <span data-ttu-id="c63ec-121">15 文字の最大フレーム レートがあります。</span><span class="sxs-lookup"><span data-stu-id="c63ec-121">Has a maximum framerate of 15.</span></span>|
|`K4A_DEPTH_MODE_WFOV_2X2BINNED`|<span data-ttu-id="c63ec-122">さまざまな角度ビュー (120 x 120) 深さ (0.25-2.88 m) が浅い解像度の低いデータ (512 x 512)。</span><span class="sxs-lookup"><span data-stu-id="c63ec-122">Wide angle view (120x120), shallow depth (0.25-2.88m), low data resolution (512x512).</span></span>|
|`K4A_DEPTH_MODE_NFOV_UNBINNED`|<span data-ttu-id="c63ec-123">狭い角度ビュー (75 x 65)、相手側の深さ (0.5-3.86 m) データの高解像度 (640 x 576)。</span><span class="sxs-lookup"><span data-stu-id="c63ec-123">Narrow angle view (75x65), far depth (0.5-3.86m), high data resolution (640x576).</span></span>|
|`K4A_DEPTH_MODE_NFOV_2X2BINNED`|<span data-ttu-id="c63ec-124">狭い角度ビュー (75 x 65)、相手側の深さ (0.5-5.46 m) 解像度の低いデータ (320 x 288)。</span><span class="sxs-lookup"><span data-stu-id="c63ec-124">Narrow angle view (75x65), far depth (0.5-5.46m), low data resolution (320x288).</span></span>|
|`K4A_DEPTH_MODE_PASSIVE_IR`|<span data-ttu-id="c63ec-125">Raw IR カメラ (1024 × 1024) からのフィード</span><span class="sxs-lookup"><span data-stu-id="c63ec-125">Raw feed from the IR camera (1024x1024)</span></span>|
||<span data-ttu-id="c63ec-126">オブジェクトの反射率によって指定された範囲外の深さが提供されます。</span><span class="sxs-lookup"><span data-stu-id="c63ec-126">Depth will be provided outside of indicated range depending on object reflectivity.</span></span>|

## <a name="acessing-depth-data"></a><span data-ttu-id="c63ec-127">データへのアクセス</span><span class="sxs-lookup"><span data-stu-id="c63ec-127">Acessing Depth Data</span></span>

![](img/Depth.png)

<span data-ttu-id="c63ec-128">デバイスからのフレームをキャプチャときに使用できます`k4a_capture_get_depth_image`と`k4a_image_get_buffer`深さの生データを取得します。</span><span class="sxs-lookup"><span data-stu-id="c63ec-128">When we capture a frame from the device, we can use `k4a_capture_get_depth_image` and `k4a_image_get_buffer` to get the raw depth data!</span></span>

```C
// Capture a frame
k4a_capture_t capture;
k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

// Get the depth data and information from the current capture
k4a_image_t depth_image  = k4a_capture_get_depth_image(capture);
uint16_t   *depth_buffer = reinterpret_cast<uint16_t*>(k4a_image_get_buffer(depth_image));
int32_t width  = k4a_image_get_width_pixels (depth_image);
int32_t height = k4a_image_get_height_pixels(depth_image);
```

<span data-ttu-id="c63ec-129">深度の情報は、カメラからミリメートルを表す、符号なし 16 ビット整数の配列として提供されます。</span><span class="sxs-lookup"><span data-stu-id="c63ec-129">Depth information is provided as an array of unsigned 16 bit integers, representing millimeters from the camera.</span></span> <span data-ttu-id="c63ec-130">特定のピクセルの深度値がない場合、配列は 0 を保持します。</span><span class="sxs-lookup"><span data-stu-id="c63ec-130">The array will hold a zero if the depth value isn't present for a particular pixel.</span></span>

<span data-ttu-id="c63ec-131">この例では、だけ、グレースケールの画像に深度データを変換し、ファイルに保存しましたします!</span><span class="sxs-lookup"><span data-stu-id="c63ec-131">In this example, we'll just convert the depth data into a grayscale image, and save it to file!</span></span>

```C
// Write this depth capture to an image file

// Allocate memory for an 8-bit grayscale image
uint8_t *file_color = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * width*height));

// Convert each depth value to a shade of gray!
for (int32_t i = 0; i < width*height; i++)
{
    // Make a gray from the depth, white up close, black at 3 meters in the distance
    float depth_gray = 1-(depth_buffer[i] / 3000.0f);
    // Cap at 1.0, any higher and our uint8_t will overflow and wrap around
    depth_gray = depth_gray > 1.0f ? 1.0f : depth_gray;

    file_color[i] = static_cast<uint8_t>(depth_gray * 255);
}
tga_write("outDepth.tga", width, height, file_color, 1, 3);
free(file_color);
```

## <a name="cleaning-up"></a><span data-ttu-id="c63ec-132">クリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="c63ec-132">Cleaning Up</span></span>

<span data-ttu-id="c63ec-133">シャット ダウンして割り当てられたまたは取得したすべてのリリースに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c63ec-133">Remember to shut down and release everything you've allocated or grabbed!</span></span> <span data-ttu-id="c63ec-134">別のフレームをキャプチャする前に完了したら、フレームのキャプチャを解放する必要が注意してください。</span><span class="sxs-lookup"><span data-stu-id="c63ec-134">Remember that frame captures should be freed after you're finished with them and before grabbing another frame.</span></span>

```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(depth_image);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a><span data-ttu-id="c63ec-135">完全なソース</span><span class="sxs-lookup"><span data-stu-id="c63ec-135">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels);

int main()
{
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Configure the Kinect to open a stream of 1024x1024 wide FOV at 5 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps = K4A_FRAMES_PER_SECOND_5;
    config.depth_mode = K4A_DEPTH_MODE_WFOV_UNBINNED;

    k4a_device_start_cameras(device, &config);

    // Wait until the first capture is available to us
    k4a_capture_t capture;
    k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

    // Get the depth data and information from the current capture
    k4a_image_t depth_image  = k4a_capture_get_depth_image(capture);
    uint16_t   *depth_buffer = reinterpret_cast<uint16_t*>(k4a_image_get_buffer(depth_image));
    int32_t width  = k4a_image_get_width_pixels (depth_image);
    int32_t height = k4a_image_get_height_pixels(depth_image);
    printf("Captured depth image, %dx%d\n", width, height);

    // Write this depth capture to an image file

    // Allocate memory for an 8-bit grayscale image
    uint8_t *file_color = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * width*height));

    // Convert each depth value to a shade of gray!
    for (int32_t i = 0; i < width*height; i++)
    {
        // Make a gray from the depth, white up close, black at 3 meters in the distance
        float depth_gray = 1-(depth_buffer[i] / 3000.0f);
        // Cap at 1.0, any higher and our uint8_t will overflow and wrap around
        depth_gray = depth_gray > 1.0f ? 1.0f : depth_gray;

        file_color[i] = static_cast<uint8_t>(depth_gray * 255);
    }
    tga_write("outDepth.tga", width, height, file_color, 1, 3);
    free(file_color);

    // Release all allocated resources, and shut down the Kinect
    k4a_image_release(depth_image);
    k4a_capture_release(capture);

    k4a_device_stop_cameras(device);
    k4a_device_close(device);

    return 0;
}

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels)
{
    FILE *fp = NULL;
    fopen_s(&fp, filename, "wb");
    if (fp == NULL) return;

    uint8_t header[18] = { 0,0,2,0,0,0,0,0,0,0,0,0, width % 256, (uint8_t)(width / 256), height % 256, (uint8_t)(height / 256), file_channels * 8u, 0x20 };
    fwrite(&header, 18, 1, fp);
    for (uint32_t i = 0; i < width*height; i++)
        for (uint32_t b = 0; b < file_channels; b++)
            fputc(data_bgra[(i*data_channels) + (b%data_channels)], fp);
    fclose(fp);
}
```

## <a name="next-lab---reading-rgb-datareadcolormd"></a><span data-ttu-id="c63ec-136">次の実習 - [RGB データの読み取り](ReadColor.md)</span><span class="sxs-lookup"><span data-stu-id="c63ec-136">Next Lab - [Reading RGB Data](ReadColor.md)</span></span>