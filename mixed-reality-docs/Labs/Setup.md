# <a name="setting-up"></a>設定します。

Azure の Kinect DK API の概要ですか。 探す必要はありません。 このドキュメントが揃って稼働しているアクセス権を持つデバイスに!

まず、ダウンロードしてインストール、 [Azure Kinect DK API](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK) Github から。

**目次**  
[ヘッダー](#Headers)  
[Kinect デバイスの検索](#Finding-a-Kinect-Device)  
[カメラの開始](#Starting-the-Cameras)  
[エラー処理](#Error-Handling)  
[完全なソース](#Full-Source)  

**使用して関数を次に示します。**  
[`k4a_device_get_installed_count()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count)  
[`k4a_device_open()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)  
[`k4a_device_get_serialnum()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-serialnum)  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_device_stop_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-stop-cameras)  
[`k4a_device_close()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)

## <a name="headers"></a>ヘッダー
必要となる 1 つだけのヘッダーがあるし、k4a.h です! SDK のライブラリで任意のコンパイラを設定するかどうかを確認し、フォルダーが含まれます。 リンク k4a.lib と k4a.dll ファイルも必要になります。
```C
#include <k4a/k4a.h>
```

## <a name="finding-a-kinect-device"></a>Kinect デバイスの検索

![](img/Serial.png)

複数の Azure Kinect DK デバイスは、コンピューターに接続できます。 最初に、数を検索してを起動しますか、まったくを使用していずれかに接続している場合、 [ `k4a_device_get_installed_count` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count)関数。 この関数は、追加設定なしすぐ、機能する必要があります!

```C
uint32_t count = k4a_device_get_installed_count();
```

使用して開くことができますわかったらがありますが実際には、デバイスに接続されているコンピューター、 [ `k4a_device_open`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)します。 インデックスを指定することができますを開くには、必要なデバイスのまたはを使用できます[ `K4A_DEVICE_DEFAULT` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT) 1 つ目です。

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
k4a_device_open(K4A_DEVICE_DEFAULT, &device);
```
として k4a API で多くのものと、何かを開くときにする必要がありますも閉じる操作を終了したら! 呼び出しをシャット ダウンしている場合に注意して[ `k4a_device_close`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)します。

```C
k4a_device_close(device);
```

デバイスが開いたら、すばらしいことを確認する本当に簡単なテストを実行できます。 デバイスのシリアル番号を読み取てしましょう!

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

## <a name="starting-the-cameras"></a>カメラの開始

デバイスを開くことでカメラを構成する必要があります、 [ `k4a_device_configuration_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t)オブジェクト。 カメラの構成では、各種のオプションの数と、独自のシナリオに最適な設定を選択する必要があります。

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

構成の詳細について、__色__カメラ、[このドキュメントをチェック アウト]()!  
構成の詳細について、__深さ__カメラ、[このドキュメントをチェック アウト]()!

## <a name="error-handling"></a>エラー処理

説明を簡潔にするため、わかりやすくするためには、インライン例をいくつかのエラー処理を紹介はありません。 ただし、エラー処理では、常に重要です。 多くの関数が成功/失敗の一般的な型を返す[ `k4a_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t)、具体的なバリアントの詳細情報または[ `k4a_wait_result_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t)します。 ドキュメントを確認してください、またはどのようなエラー メッセージを表示する特定の関数の intellisense に期待する可能性があります。

エラーの種類とも、 [ `K4A_SUCCEEDED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED)と[ `K4A_FAILED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED)それらで使用できるマクロ。 したがって k4a デバイスを開くだけで、代わりに、このような保護可能性があります。

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
if ( K4A_FAILED( k4a_device_open(K4A_DEVICE_DEFAULT, &device) ) )
{
    printf("Failed to open k4a device!\n");
    return;
}
```

# <a name="full-source"></a>完全なソース

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

## <a name="next-lab---reading-depth-datareaddepthmd"></a>次の実習 -[深さデータの読み取り](ReadDepth.md)
