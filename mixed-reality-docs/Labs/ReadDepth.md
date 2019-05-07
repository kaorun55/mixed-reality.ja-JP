# <a name="reading-depth-data"></a>深さのデータの読み取り

デバイスからの深さのデータを読み取る必要がありますか。 簡単です！

**目次**  
[デバイスを構成します。](#Configuring-the-Device)  
[データへのアクセス](#Acessing-Depth-Data)  
[クリーンアップします。](#Cleaning-Up)  
[完全なソース](#Full-Source)  

**使用して関数を次に示します。**  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_depth_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-depth-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release)  

## <a name="configuring-the-device"></a>デバイスを構成します。

後[インターフェイスを開く]()Azure Kinect DK デバイスには、データをキャプチャするためのカメラを構成する必要があります。 1 つだけの項目の深さを構成する際に知って本当に必要があることと、 `depth_mode`!

```C
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.depth_mode = K4A_DEPTH_MODE_NFOV_UNBINNED;

k4a_device_start_cameras(device, &config);
```

ここで、`depth_mode`いくつかを選択できます。 アプリケーションのコンテキストに応じて、さまざまな形式でデータを要求できます。

深さのデータにアルゴリズムの時間の制約付き実行しているでしょうか。 必要なデータを操作するため、2X2BINNED モードを選択かもしれません。 関心があるよりははるかに直接アウトは閉じるのではなく、視界に先行しますか? フィールドの表示の幅が狭いを使用して、NFOV モード。
| [`depth_mode`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-depth-mode-t) | description |
|------------|-------------|
|`K4A_DEPTH_MODE_WFOV_UNBINNED`|さまざまな角度ビュー (120 x 120) 浅い深度 (0.25-2.21 m) データの高解像度 (1024 x 1024)。 15 文字の最大フレーム レートがあります。|
|`K4A_DEPTH_MODE_WFOV_2X2BINNED`|さまざまな角度ビュー (120 x 120) 深さ (0.25-2.88 m) が浅い解像度の低いデータ (512 x 512)。|
|`K4A_DEPTH_MODE_NFOV_UNBINNED`|狭い角度ビュー (75 x 65)、相手側の深さ (0.5-3.86 m) データの高解像度 (640 x 576)。|
|`K4A_DEPTH_MODE_NFOV_2X2BINNED`|狭い角度ビュー (75 x 65)、相手側の深さ (0.5-5.46 m) 解像度の低いデータ (320 x 288)。|
|`K4A_DEPTH_MODE_PASSIVE_IR`|Raw IR カメラ (1024 × 1024) からのフィード|
||オブジェクトの反射率によって指定された範囲外の深さが提供されます。|

## <a name="acessing-depth-data"></a>データへのアクセス

![](img/Depth.png)

デバイスからのフレームをキャプチャときに使用できます`k4a_capture_get_depth_image`と`k4a_image_get_buffer`深さの生データを取得します。

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

深度の情報は、カメラからミリメートルを表す、符号なし 16 ビット整数の配列として提供されます。 特定のピクセルの深度値がない場合、配列は 0 を保持します。

この例では、だけ、グレースケールの画像に深度データを変換し、ファイルに保存しましたします!

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

## <a name="cleaning-up"></a>クリーンアップします。

シャット ダウンして割り当てられたまたは取得したすべてのリリースに注意してください。 別のフレームをキャプチャする前に完了したら、フレームのキャプチャを解放する必要が注意してください。

```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(depth_image);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a>完全なソース

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

## <a name="next-lab---reading-rgb-datareadcolormd"></a>次の実習 - [RGB データの読み取り](ReadColor.md)