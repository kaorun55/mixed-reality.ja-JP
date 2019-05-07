# <a name="reading-rgb-data"></a>RGB データの読み取り

**目次**  
[デバイスを構成します。](#Configuring-the-Device)  
[色のフレームを取得します。](#Getting-a-Color-Frame)  
[クリーンアップします。](#Cleaning-Up)  
[完全なソース](#Full-Source)  

**使用して関数を次に示します。**  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_color_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-color-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release) 

## <a name="configuring-the-device"></a>デバイスを構成します。

後[k4a デバイスを開く]()色のデータを取得するためにカメラを設定する必要があります。 ここでオプションの多くも、ために説明。 外観を本当に基本的な色のカメラを開始する簡単な例を次に示します。

```C
// Configure a stream of 1280x720 BGRA color data at 5 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_720P;

k4a_device_start_cameras(device, &config);
```

`color_format`イメージ バッファーに格納されている色については、適用する方法により、! `K4A_IMAGE_FORMAT_COLOR_BGRA32` 青、緑、赤、およびアルファの 8 ビットずつとして格納されているピクセルあたり 32 ビットとなります。 その利便性のための例は、この形式を使用しますが、その他の形式では優れた選択肢があります concious のメモリ使用量を指定する場合は、!

|`color_format`||
|--------------|-----------|
|`K4A_IMAGE_FORMAT_COLOR_MJPG`|色のデータに[モーション JPEG 形式](https://en.wikipedia.org/wiki/Motion_JPEG)|
|`K4A_IMAGE_FORMAT_COLOR_NV12`|[YUV](https://en.wikipedia.org/wiki/YUV)色の領域の 4:2:0 形式の NV12、720p の解像度でのみ使用できます。|
|`K4A_IMAGE_FORMAT_COLOR_YUY2`|[YUV](https://en.wikipedia.org/wiki/YUV)色の領域の 4:2:2 形式、YUY2、720p の解像度でのみ使用できます。|
|`K4A_IMAGE_FORMAT_COLOR_BGRA32`|色の生データをピクセルあたり 32 ビットが青、緑、赤、アルファとして順序付け|

書き込み中に YUV 変換の可能性があります、高速で堅牢なライブラリは非常に簡単に YUV 変換がある[libyuv](https://chromium.googlesource.com/libyuv/libyuv/)します。

`color_resolution`いくつかのオプションがあります。

|`color_resolution`|解決方法|側面|ビューのフィールド| |
|------------------|----------|------|-------------|-|
|`K4A_COLOR_RESOLUTION_720P`  | 1280 x 720  | 16:9 | 90 x 59
|`K4A_COLOR_RESOLUTION_1080P` | 1920 x 1080 | 16:9 | 90 x 59
|`K4A_COLOR_RESOLUTION_1440P` | 2560 x 1440 | 16:9 | 90 x 59
|`K4A_COLOR_RESOLUTION_2160P` | 3840 x 2,160 | 16:9 | 90 x 59
|`K4A_COLOR_RESOLUTION_1536P` | 2048 x 1536 | 4:3  | 90x74.3 
|`K4A_COLOR_RESOLUTION_3072P` | 4096 x 3072 | 4:3  | 90x74.3 | 15 フレーム レートを最大になります。

もちろん、および、`camera_fps`もします。

|camera_fps||
|--|--|
|`K4A_FRAMES_PER_SECOND_5`
|`K4A_FRAMES_PER_SECOND_15`
|`K4A_FRAMES_PER_SECOND_30`

## <a name="getting-a-color-frame"></a>色のフレームを取得します。

非常に同様のプロセスは、色のフレームと深さフレームのデータの取得! 最初のキャプチャをデバイスから取得し、色の画像から抽出し、そのイメージから生データをプルします。

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

今すぐに格納されているデータ`colorDataBRGA`構成では示される形式に依存します。 要求しましたので`K4A_IMAGE_FORMAT_COLOR_BGRA32`配列に格納されている BGRA 32 ビット カラー値の完全ながある order!

この場合は、.tga ファイル ストア色 BGR の順序で既に! 保存する関数は、これらの引数でアルファ チャネルを省略できるため渡すだけでイメージのデータを!

## <a name="cleaning-up"></a>クリーンアップします。

それらに完了すると、リソースを解放する注意してください。
```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(colors);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

## <a name="full-source"></a>完全なソース

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

## <a name="next-lab---mixing-color-and-depth-datamixdepthandrgbmd"></a>次の実習 -[色と深度データの混在](MixDepthAndRGB.md)