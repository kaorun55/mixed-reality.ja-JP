# <a name="reading-rgb-data"></a><span data-ttu-id="4c744-101">RGB データの読み取り</span><span class="sxs-lookup"><span data-stu-id="4c744-101">Reading RGB Data</span></span>

<span data-ttu-id="4c744-102">**目次**</span><span class="sxs-lookup"><span data-stu-id="4c744-102">**Contents**</span></span>  
[<span data-ttu-id="4c744-103">デバイスを構成します。</span><span class="sxs-lookup"><span data-stu-id="4c744-103">Configuring the Device</span></span>](#Configuring-the-Device)  
[<span data-ttu-id="4c744-104">色のフレームを取得します。</span><span class="sxs-lookup"><span data-stu-id="4c744-104">Getting a Color Frame</span></span>](#Getting-a-Color-Frame)  
[<span data-ttu-id="4c744-105">クリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="4c744-105">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="4c744-106">完全なソース</span><span class="sxs-lookup"><span data-stu-id="4c744-106">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="4c744-107">**使用して関数を次に示します。**</span><span class="sxs-lookup"><span data-stu-id="4c744-107">**Here are the functions we'll use:**</span></span>  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_color_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-color-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release) 

## <a name="configuring-the-device"></a><span data-ttu-id="4c744-108">デバイスを構成します。</span><span class="sxs-lookup"><span data-stu-id="4c744-108">Configuring the Device</span></span>

<span data-ttu-id="4c744-109">後[k4a デバイスを開く]()色のデータを取得するためにカメラを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c744-109">After [opening a k4a device](), we'll need to set up the cameras to grab color data!</span></span> <span data-ttu-id="4c744-110">ここでオプションの多くも、ために説明。</span><span class="sxs-lookup"><span data-stu-id="4c744-110">There's a lot of options here as well, so we'll go through them.</span></span> <span data-ttu-id="4c744-111">外観を本当に基本的な色のカメラを開始する簡単な例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c744-111">Here's a quick example of what it looks like to start up a really basic color camera.</span></span>

```C
// Configure a stream of 1280x720 BGRA color data at 5 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_720P;

k4a_device_start_cameras(device, &config);
```

<span data-ttu-id="4c744-112">`color_format`イメージ バッファーに格納されている色については、適用する方法により、!</span><span class="sxs-lookup"><span data-stu-id="4c744-112">The `color_format` allows us to say how we want our color information stored in the image buffer!</span></span> <span data-ttu-id="4c744-113">`K4A_IMAGE_FORMAT_COLOR_BGRA32` 青、緑、赤、およびアルファの 8 ビットずつとして格納されているピクセルあたり 32 ビットとなります。</span><span class="sxs-lookup"><span data-stu-id="4c744-113">`K4A_IMAGE_FORMAT_COLOR_BGRA32` would be 32 bits per pixel, stored as 8 bits each for Blue, Green, Red, and Alpha.</span></span> <span data-ttu-id="4c744-114">その利便性のための例は、この形式を使用しますが、その他の形式では優れた選択肢があります concious のメモリ使用量を指定する場合は、!</span><span class="sxs-lookup"><span data-stu-id="4c744-114">We use this format in the examples due to its convenience, but if you want to be concious of memory usage, other formats may be superior choices!</span></span>

|`color_format`||
|--------------|-----------|
|`K4A_IMAGE_FORMAT_COLOR_MJPG`|<span data-ttu-id="4c744-115">色のデータに[モーション JPEG 形式](https://en.wikipedia.org/wiki/Motion_JPEG)</span><span class="sxs-lookup"><span data-stu-id="4c744-115">Color data will be in [Motion JPEG format](https://en.wikipedia.org/wiki/Motion_JPEG)</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_NV12`|<span data-ttu-id="4c744-116">[YUV](https://en.wikipedia.org/wiki/YUV)色の領域の 4:2:0 形式の NV12、720p の解像度でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="4c744-116">[YUV](https://en.wikipedia.org/wiki/YUV) color space 4:2:0 format, NV12, only available at 720p resolution.</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_YUY2`|<span data-ttu-id="4c744-117">[YUV](https://en.wikipedia.org/wiki/YUV)色の領域の 4:2:2 形式、YUY2、720p の解像度でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="4c744-117">[YUV](https://en.wikipedia.org/wiki/YUV) color space 4:2:2 format, YUY2, only available at 720p resolution.</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_BGRA32`|<span data-ttu-id="4c744-118">色の生データをピクセルあたり 32 ビットが青、緑、赤、アルファとして順序付け</span><span class="sxs-lookup"><span data-stu-id="4c744-118">Raw color data, 32 bits per pixel, ordered as Blue, Green, Red, Alpha</span></span>|

<span data-ttu-id="4c744-119">書き込み中に YUV 変換の可能性があります、高速で堅牢なライブラリは非常に簡単に YUV 変換がある[libyuv](https://chromium.googlesource.com/libyuv/libyuv/)します。</span><span class="sxs-lookup"><span data-stu-id="4c744-119">While writing your own YUV conversion may be easy enough, a fast, robust library for YUV conversion can be found at [libyuv](https://chromium.googlesource.com/libyuv/libyuv/).</span></span>

<span data-ttu-id="4c744-120">`color_resolution`いくつかのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="4c744-120">The `color_resolution` also has a couple of options!</span></span>

|`color_resolution`|<span data-ttu-id="4c744-121">解決方法</span><span class="sxs-lookup"><span data-stu-id="4c744-121">resolution</span></span>|<span data-ttu-id="4c744-122">側面</span><span class="sxs-lookup"><span data-stu-id="4c744-122">aspect</span></span>|<span data-ttu-id="4c744-123">ビューのフィールド</span><span class="sxs-lookup"><span data-stu-id="4c744-123">field of view</span></span>| |
|------------------|----------|------|-------------|-|
|`K4A_COLOR_RESOLUTION_720P`  | <span data-ttu-id="4c744-124">1280 x 720</span><span class="sxs-lookup"><span data-stu-id="4c744-124">1280 x 720</span></span>  | <span data-ttu-id="4c744-125">16:9</span><span class="sxs-lookup"><span data-stu-id="4c744-125">16:9</span></span> | <span data-ttu-id="4c744-126">90 x 59</span><span class="sxs-lookup"><span data-stu-id="4c744-126">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1080P` | <span data-ttu-id="4c744-127">1920 x 1080</span><span class="sxs-lookup"><span data-stu-id="4c744-127">1920 x 1080</span></span> | <span data-ttu-id="4c744-128">16:9</span><span class="sxs-lookup"><span data-stu-id="4c744-128">16:9</span></span> | <span data-ttu-id="4c744-129">90 x 59</span><span class="sxs-lookup"><span data-stu-id="4c744-129">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1440P` | <span data-ttu-id="4c744-130">2560 x 1440</span><span class="sxs-lookup"><span data-stu-id="4c744-130">2560 x 1440</span></span> | <span data-ttu-id="4c744-131">16:9</span><span class="sxs-lookup"><span data-stu-id="4c744-131">16:9</span></span> | <span data-ttu-id="4c744-132">90 x 59</span><span class="sxs-lookup"><span data-stu-id="4c744-132">90x59</span></span>
|`K4A_COLOR_RESOLUTION_2160P` | <span data-ttu-id="4c744-133">3840 x 2,160</span><span class="sxs-lookup"><span data-stu-id="4c744-133">3840 x 2160</span></span> | <span data-ttu-id="4c744-134">16:9</span><span class="sxs-lookup"><span data-stu-id="4c744-134">16:9</span></span> | <span data-ttu-id="4c744-135">90 x 59</span><span class="sxs-lookup"><span data-stu-id="4c744-135">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1536P` | <span data-ttu-id="4c744-136">2048 x 1536</span><span class="sxs-lookup"><span data-stu-id="4c744-136">2048 x 1536</span></span> | <span data-ttu-id="4c744-137">4:3</span><span class="sxs-lookup"><span data-stu-id="4c744-137">4:3</span></span>  | <span data-ttu-id="4c744-138">90x74.3</span><span class="sxs-lookup"><span data-stu-id="4c744-138">90x74.3</span></span> 
|`K4A_COLOR_RESOLUTION_3072P` | <span data-ttu-id="4c744-139">4096 x 3072</span><span class="sxs-lookup"><span data-stu-id="4c744-139">4096 x 3072</span></span> | <span data-ttu-id="4c744-140">4:3</span><span class="sxs-lookup"><span data-stu-id="4c744-140">4:3</span></span>  | <span data-ttu-id="4c744-141">90x74.3</span><span class="sxs-lookup"><span data-stu-id="4c744-141">90x74.3</span></span> | <span data-ttu-id="4c744-142">15 フレーム レートを最大になります。</span><span class="sxs-lookup"><span data-stu-id="4c744-142">Max framerate 15.</span></span>

<span data-ttu-id="4c744-143">もちろん、および、`camera_fps`もします。</span><span class="sxs-lookup"><span data-stu-id="4c744-143">And of course, the `camera_fps` as well.</span></span>

|<span data-ttu-id="4c744-144">camera_fps</span><span class="sxs-lookup"><span data-stu-id="4c744-144">camera_fps</span></span>||
|--|--|
|`K4A_FRAMES_PER_SECOND_5`
|`K4A_FRAMES_PER_SECOND_15`
|`K4A_FRAMES_PER_SECOND_30`

## <a name="getting-a-color-frame"></a><span data-ttu-id="4c744-145">色のフレームを取得します。</span><span class="sxs-lookup"><span data-stu-id="4c744-145">Getting a Color Frame</span></span>

<span data-ttu-id="4c744-146">非常に同様のプロセスは、色のフレームと深さフレームのデータの取得!</span><span class="sxs-lookup"><span data-stu-id="4c744-146">Getting data for a color frame and a depth frame is a very similar process!</span></span> <span data-ttu-id="4c744-147">最初のキャプチャをデバイスから取得し、色の画像から抽出し、そのイメージから生データをプルします。</span><span class="sxs-lookup"><span data-stu-id="4c744-147">First we get a capture from the device, then we extract the color image from it, and then we pull the raw data out of that image.</span></span>

```C
// Wait until the first capture is available to us
k4a_capture_t capture;
k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

// Get the color data and information from the current capture
k4a_image_t colors      = k4a_capture_get_color_image(capture);
uint8_t    *colors_bgra = k4a_image_get_buffer(colors);
int width  = k4a_image_get_width_pixels (colors);
int height = k4a_image_get_height_pixels(colors);

// Write this capture to file
tga_write("out.tga", width, height, colorDataBGRA, 4, 3);
```

<span data-ttu-id="4c744-148">今すぐに格納されているデータ`colorDataBRGA`構成では示される形式に依存します。</span><span class="sxs-lookup"><span data-stu-id="4c744-148">The data now stored in `colorDataBRGA` is dependant on the format we indicated in configuration.</span></span> <span data-ttu-id="4c744-149">要求しましたので`K4A_IMAGE_FORMAT_COLOR_BGRA32`配列に格納されている BGRA 32 ビット カラー値の完全ながある order!</span><span class="sxs-lookup"><span data-stu-id="4c744-149">Since we asked for `K4A_IMAGE_FORMAT_COLOR_BGRA32`, we have an array full of 32 bit color values stored in BGRA order!</span></span>

<span data-ttu-id="4c744-150">この場合は、.tga ファイル ストア色 BGR の順序で既に!</span><span class="sxs-lookup"><span data-stu-id="4c744-150">In this case, .tga files store colors in BGR order already!</span></span> <span data-ttu-id="4c744-151">保存する関数は、これらの引数でアルファ チャネルを省略できるため渡すだけでイメージのデータを!</span><span class="sxs-lookup"><span data-stu-id="4c744-151">And since our saving function can skip the alpha channel with these arguments, we can just pass the image data as is!</span></span>

## <a name="cleaning-up"></a><span data-ttu-id="4c744-152">クリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="4c744-152">Cleaning Up</span></span>

<span data-ttu-id="4c744-153">それらに完了すると、リソースを解放する注意してください。</span><span class="sxs-lookup"><span data-stu-id="4c744-153">And as always, remember to release your resources when you're done with them!</span></span>
```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(colors);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

## <a name="full-source"></a><span data-ttu-id="4c744-154">完全なソース</span><span class="sxs-lookup"><span data-stu-id="4c744-154">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels);

int main() {
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Configure a stream of 1280x720 BRGA data at 5 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
    config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
    config.color_resolution = K4A_COLOR_RESOLUTION_720P;

    k4a_device_start_cameras(device, &config);

    // Wait until the first capture is available to us
    k4a_capture_t capture;
    k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

    // Get the color data and information from the current capture
    k4a_image_t colors      = k4a_capture_get_color_image(capture);
    uint8_t    *colors_bgra = k4a_image_get_buffer(colors);
    int width  = k4a_image_get_width_pixels (colors);
    int height = k4a_image_get_height_pixels(colors);
    printf("Captured RGB image, %dx%d\n", width, height);

    // Write this capture to file
    tga_write("out.tga", width, height, colors_bgra, 4, 3);

    // Release all allocated resources, and shut down the Kinect
    k4a_image_release(colors);
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

## <a name="next-lab---mixing-color-and-depth-datamixdepthandrgbmd"></a><span data-ttu-id="4c744-155">次の実習 -[色と深度データの混在](MixDepthAndRGB.md)</span><span class="sxs-lookup"><span data-stu-id="4c744-155">Next Lab - [Mixing Color and Depth Data](MixDepthAndRGB.md)</span></span>