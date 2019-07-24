---
title: お持ちのカメラ
description: HoloLens のフロント接続カメラに関する一般的な情報、そのしくみ、および開発者が使用できるプロファイルと解決方法について説明します。
author: cdedmonds
ms.author: wguyman, cdedmonds
ms.date: 06/12/2019
ms.topic: article
keywords: カメラ、hololens、カラーカメラ、フロント接続、hololens 2、cv、コンピュータービジョン、基準、マーカー、qr コード、qr、写真、ビデオ
ms.openlocfilehash: b80e201723f8f499a6d35008b9d308f93b925b1c
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694535"
---
# <a name="locatable-camera"></a>お持ちのカメラ

HoloLens には、デバイスの前面に取り付けられている世界中のカメラが搭載されています。これにより、アプリはユーザーに表示される内容を確認できます。 スマートフォン、ノートブック、またはデスクトップのカラーカメラの場合と同じように、開発者はカメラのアクセスと制御を行うことができます。 モバイルおよびデスクトップで動作する同じユニバーサル windows [media capture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx)および windows Media foundation Api が HoloLens で動作します。 Unity では、[これらの Windows api をラップ](locatable-camera-in-unity.md)して、HoloLens でのカメラの単純な使用を抽象化し、(ホログラムの有無にかかわらず) 通常の写真やビデオを撮影したり、カメラの位置をシーン上で検索したりするなどのタスクを実行しました。

## <a name="device-camera-information"></a>デバイスカメラ情報

### <a name="hololens-first-generation"></a>HoloLens (最初世代)

* 自動白バランス、自動露出、およびフルイメージ処理パイプラインを使用して、フォーカスされたフォト/ビデオ (PV) カメラを修正します。
* 世界中のホワイトプライバシー LED は、カメラがアクティブになるたびに点灯します
* カメラは、30、24、20、15、および 5 fps で、次のモード (すべてのモードが16:9 の縦横比) をサポートしています。

  |  Video  |  [プレビュー]  |  それでもなお  |  ビューの水平方向のフィールド (H 視界) |  推奨される使用方法 | 
  |----------|----------|----------|----------|----------|
  |  1280 x 720 |  1280 x 720 |  1280 x 720 |  45度  |  (ビデオ安定化を使用した既定のモード) | 
  |  なし |  なし |  2048x1152 |  67deg |  高解像度の静止画像 | 
  |  1408x792 |  1408x792 |  1408x792 |  48度 |  ビデオ安定化前のオーバースキャン (埋め込み) 解像度 | 
  |  1344x756 |  1344x756 |  1344x756 |  67deg |  オーバースキャンによる大規模な視界のビデオモード | 
  |  896x504 |  896x504 |  896x504 |  48度 |  イメージ処理タスクの低電力/低解像度モード | 

### <a name="hololens-2"></a>HoloLens 2

* 自動ホワイトバランス、自動露出、およびフルイメージ処理パイプラインを使用して、写真/ビデオ (PV) カメラを自動フォーカスします。
* 世界中のホワイトプライバシー LED は、カメラがアクティブになるたびに点灯します。
* HoloLens 2 では、さまざまなカメラプロファイルがサポートされています。 [カメラの機能を検出して選択](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/camera-profiles)する方法について説明します。
* カメラでは、次のプロファイルと解像度がサポートされています (すべてのビデオモードは16:9 縦横比です)。
  
  | Profile                                         | Video     | [プレビュー]   | それでもなお     | フレームレート | ビューの水平方向のフィールド (H 視界) | 推奨される使用方法                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | Legacy、0 BalancedVideoAndPhoto、100             | 2272x1278 | 2272x1278 |           | 15、30       | 64.69                            | 高品質なビデオ記録                |
  | Legacy、0 BalancedVideoAndPhoto、100             | 896x504   | 896x504   |           | 15、30       | 64.69                            | 高品質の写真キャプチャ用のプレビューストリーム |
  | Legacy、0 BalancedVideoAndPhoto、100             |           |           | 3904x2196 |             | 64.69                            | 高品質な写真キャプチャ                  |
  | BalancedVideoAndPhoto、120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15、30       | 64.69                            | 長期間のシナリオ                     |
  | BalancedVideoAndPhoto、120                       | 1504x84 6  | 1504x84 6  |           | 15、30       | 64.69                            | 長期間のシナリオ                     |
  | ビデオ会議、100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15、30、60    | 64.69                            | ビデオ会議、長期間のシナリオ |
  | ビデオ会議、100                           | 1504x84 6  | 1504x84 6  |           | 5、15、30、60  | 64.69                            | ビデオ会議、長期間のシナリオ |
  | ビデオ会議、100 BalancedVideoAndPhoto、120 | 1920 x 1080 | 1920 x 1080 | 1920 x 1080 | 15、30       | 64.69                            | ビデオ会議、長期間のシナリオ |
  | ビデオ会議、100 BalancedVideoAndPhoto、120 | 1280 x 720  | 1280 x 720  | 1280 x 720  | 15、30       | 64.69                            | ビデオ会議、長期間のシナリオ |
  | ビデオ会議、100 BalancedVideoAndPhoto、120 | 1128x636  |           |           | 15、30       | 64.69                            | ビデオ会議、長期間のシナリオ |
  | ビデオ会議、100 BalancedVideoAndPhoto、120 | 960 x 540   |           |           | 15、30       | 64.69                            | ビデオ会議、長期間のシナリオ |
  | ビデオ会議、100 BalancedVideoAndPhoto、120 | 760x428   |           |           | 15、30       | 64.69                            | ビデオ会議、長期間のシナリオ |
  | ビデオ会議、100 BalancedVideoAndPhoto、120 | 640 x 360   |           |           | 15、30       | 64.69                            | ビデオ会議、長期間のシナリオ |
  | ビデオ会議、100 BalancedVideoAndPhoto、120 | 500x282   |           |           | 15、30       | 64.69                            | ビデオ会議、長期間のシナリオ |
  | ビデオ会議、100 BalancedVideoAndPhoto、120 | 424x240   |           |           | 15、30       | 64.69                            | ビデオ会議、長期間のシナリオ |

>[!NOTE]
>[混合 reality キャプチャ](mixed-reality-capture.md)を利用して、アプリのビデオや写真を撮ることができます。これには、ホログラムやビデオの安定化が含まれます。
>
>開発者にとっては、顧客がコンテンツをキャプチャしたときに可能な限り、アプリを作成する際に考慮する必要がある考慮事項があります。 また、アプリ内で直接、mixed reality キャプチャを有効 (およびカスタマイズ) することもできます。 詳細につい[ては、「開発者向けの混合現実のキャプチャ」を](mixed-reality-capture-for-developers.md)参照してください。

## <a name="locating-the-device-camera-in-the-world"></a>デバイスカメラを世界中に配置する

HoloLens が写真やビデオを撮影する場合、キャプチャされたフレームには、世界中のカメラの位置と、カメラのレンズモデルが含まれます。 これにより、アプリケーションは、イメージのシナリオを強化するために、実際の環境におけるカメラの位置を理解することができます。 開発者は、お気に入りのイメージ処理またはカスタムコンピュータービジョンライブラリを使用して、独自のシナリオを独創ロールできます。

HoloLens ドキュメントの他の場所にある "カメラ" は、"仮想ゲームカメラ" (アプリがレンダリングするための、視錐) を指している場合があります。 特に明記しない限り、このページの "カメラ" は実際の RGB カラーカメラを表します。

このページでは、 [MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference)クラスの使用方法について詳しく説明しますが、[メディアファンデーション属性](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx)を使用してカメラの組み込みと場所をプルする api もあります。 詳細については、 [Holographic face tracking サンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)を参照してください。

### <a name="images-with-coordinate-systems"></a>座標系の画像

各イメージフレーム (写真またはビデオ) には、キャプチャ時にカメラをルートとする[SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem)が含まれています。これには、 [MediaFrameReference](https://docs.microsoft.com/en-us/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference)の[CoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem)プロパティを使用してアクセスできます。 さらに、各フレームには、 [CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics)プロパティで確認できるカメラレンズモデルの説明が含まれています。 これらの変換は、ピクセルを生成した photons によって取得されたパスを表す3D 空間の光をピクセルごとに定義します。 これらの光線は、フレームの座標系から他の座標系 (例:[静止フレーム](coordinate-systems.md#stationary-frame-of-reference)から) への変換を取得することによって、アプリ内の他のコンテンツに関連付けることができます。 要約すると、各イメージフレームには次のものが表示されます。
* ピクセルデータ (RGB/NV12/JPEG/など)
* キャプチャの場所からの[SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem)
* カメラのレンズモードを含む[CameraIntrinsics](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics)クラス

### <a name="camera-to-application-specified-coordinate-system"></a>アプリケーションによって指定された座標系へのカメラ

' CameraIntrinsics ' と ' CameraCoordinateSystem ' からアプリケーション/ワールド座標系に移行するには、次のものが必要です。

[Unity でのお持ちのカメラ](locatable-camera-in-unity.md):CameraToWorldMatrix は PhotoCaptureFrame クラスによって自動的に提供されます (そのため、CameraCoordinateSystem の変換について心配する必要はありません)。

[DirectX でのお持ちのカメラ](locatable-camera-in-directx.md):カメラの座標系と独自のアプリケーション座標系との間の変換をクエリするための非常に簡単な方法を示します。

### <a name="distortion-error"></a>ディストーションエラー

HoloLens では、アプリケーションでフレームを利用できるようになる前に、ビデオストリームと静止画像ストリームがシステムのイメージ処理パイプラインで undistorted されます (プレビューストリームには、元のゆがんだフレームが含まれます)。 CameraIntrinsics のみが使用可能になるため、アプリケーションはイメージフレームが完全な pinhole カメラを表すものと想定する必要がありますが、イメージプロセッサのディストーション関数では、HoloLens で最大10ピクセルのエラーが引き続き発生する場合があります (最初の生成)。フレームメタデータで CameraIntrinsics を使用する場合。 多くのユースケースでは、このエラーは問題にはなりませんが、たとえば、ホログラムを実際のポスター/マーカーに整列させている場合、< 10px オフセット (2 メートルの位置にあるホログラムの場合は約 11 mm) がある場合は、このゆがみエラーが原因である可能性があります。 

## <a name="locatable-camera-usage-scenarios"></a>お持ちのカメラの使用シナリオ

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>キャプチャされた場所で写真またはビデオを表示する

デバイスカメラのフレームには、イメージがどこで撮影されたかを正確に示すために使用できる "カメラからワールドへの変換" 変換が付属しています。 たとえば、小さな holographic アイコンをこの場所 (CameraToWorld (Vector3)) に配置して、カメラが直面している方向に小さな矢印を描画する (CameraToWorld) ことができます (Yvector (Vector3))。

### <a name="tag--pattern--poster--object-tracking"></a>タグ/パターン/ポスター/オブジェクトの追跡

多くの mixed reality アプリケーションでは、認識可能なイメージまたはビジュアルパターンを使用して、空間内の追跡可能なポイントを作成します。 その後、そのポイントを基準としてオブジェクトをレンダリングしたり、既知の場所を作成したりするために使用されます。 HoloLens の使用例としては、fiducials でタグ付けされた現実世界のオブジェクト (QR コードを使用したテレビモニターなど) の検索、fiducials に対するホログラムの配置、およびを介して HoloLens と通信するように設定されているタブレットなどの非 HoloLens デバイスとの視覚的なペアリングがあります。Wi-fi。

ビジュアルパターンを認識し、そのオブジェクトをアプリケーションのワールド空間に配置するには、次のものが必要です。
1. 画像パターン認識ツールキット (QR コード、AR タグ、顔ファインダー、サークルトラッカー、OCR など)。
2. 実行時にイメージフレームを収集して認識レイヤーに渡す
3. 画像の位置を、世界中や世界中の写真に戻すことができます。 参照先
4. これらの世界の場所に仮想モデルを配置する

いくつかの重要な画像処理リンク:
* [OpenCV](http://opencv.org/)
* [QR タグ](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](http://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

対話型アプリケーションのフレームレートを維持することは、特に長時間実行されるイメージ認識アルゴリズムを扱う場合に重要です。 このため、一般的には次のパターンを使用します。
1. メインスレッド: カメラオブジェクトを管理します
2. メインスレッド: 新しいフレームの要求 (非同期)
3. メインスレッド: 新しいフレームを追跡スレッドに渡します
4. 追跡スレッド: キーポイントを収集するためのイメージの処理
5. メインスレッド: 検出されるキーポイントに一致するように仮想モデルを移動します
6. メインスレッド: 手順2の繰り返し

一部のイメージマーカーシステムは、1ピクセルの位置のみを提供します (他のユーザーが完全変換を提供するため、このセクションは必要ありません)。これは、可能な場所の射線に相当します。 1つの3d 位置に移動するには、複数の光線を活用し、最終的な結果をおおよその交点で見つけることができます。 これを行うには、次の手順を実行する必要があります。
1. 複数のカメライメージの収集を開始するループを取得する
2. 関連する特徴ポイントとそのワールド光線を検索する
3. 特徴のディクショナリ (それぞれが複数のワールド線を持つ) がある場合は、次のコードを使用して、これらの光線の交差部分を解決できます。

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

複数の追跡タグの場所を指定すると、ユーザーの現在のシナリオに合わせてモデル化シーンを配置できます。 重力を想定できない場合は、3つのタグ位置が必要になります。 多くの場合、ホワイト球体がリアルタイムで追跡されるタグ位置を表し、blue 球体がモデル化タグの場所を表す単純な配色を使用します。これにより、ユーザーは、配置の品質を視覚的に測定できます。 ここでは、すべてのアプリケーションで次のセットアップを想定しています。
* 2つ以上のモデル化タグの場所
* シーン内の1つの ' 調整スペース ' は、タグの親です。
* カメラの機能識別子
* 調整領域を移動して、モデル化タグをリアルタイムタグに整列させる動作 (他の接続はその相対的な位置であるため、モデル化マーカー自体ではなく、親スペースを移動することは注意してください)。

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>Led または他のレコグナイザーライブラリを使用して、タグ付き静止を追跡または特定したり、実際のオブジェクト/顔を移動したりします。

例 :
* Led のある工業ロボット (または低速な移動オブジェクトの QR コード)
* ルーム内のオブジェクトを識別して認識する
* 部屋のメンバーを識別して認識します (たとえば、顔を holographic 連絡先カードを配置します)。

## <a name="see-also"></a>関連項目
* [DirectX での場所を特定できるカメラ](locatable-camera-in-directx.md)
* [Unity での場所を特定できるカメラ](locatable-camera-in-unity.md)
* [複合現実キャプチャ](mixed-reality-capture.md)
* [開発者向け複合現実キャプチャ](mixed-reality-capture-for-developers.md)
* [メディアキャプチャの概要](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
* [Holographic face tracking サンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
