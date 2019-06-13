---
title: 場所を特定できるカメラ
description: HoloLens の前面カメラ、しくみ、およびプロファイルの全般的な情報と解決策を開発者に提供します。
author: wguyman
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: カメラ、hololens、色のカメラ、前面に接続する、hololens 2、cv、基準コンピューター ビジョン、マーカー、qr コード、qr、写真、ビデオ
ms.openlocfilehash: cadcd0762b8adf1001896c614451d2e1c9776c65
ms.sourcegitcommit: 79398a6b5b7037babcb05d86a5bcc336fd089ea0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2019
ms.locfileid: "67028614"
---
# <a name="locatable-camera"></a>場所を特定できるカメラ

HoloLens には、アプリをユーザーに表示される内容を参照してください。 有効にするデバイスの前面に取り付け世界に接続されたカメラが含まれています。 開発者へのアクセスと、カメラのコントロールのスマート フォン、ノートブック、またはデスクトップの色のカメラと同様にあります。 同じユニバーサル windows[メディアのキャプチャ](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx)HoloLens では、windows メディア ファンデーション モバイルとデスクトップで機能する Api の動作。 Unity[がこれらの windows Api をラップしても](locatable-camera-in-unity.md)HoloLens にカメラを正規の写真やビデオ (ホログラムの有無にかかわらず) を取得し、上でのカメラの位置とパースペクティブを検索するなどのタスクの簡単な使用を抽象化するため、シーンです。

## <a name="device-camera-information"></a>デバイスのカメラの情報

### <a name="hololens-first-generation"></a>HoloLens (第 1 世代)

* 白い自動分散、自動露出、完全なイメージ処理パイプラインと写真/ビデオ (PV) カメラを固定フォーカスします。
* カメラがアクティブなときに世界が直面しているホワイト プライバシー LED が点灯します。
* カメラには、30、24、20、15、および 5 fps で次のモード (すべてのモードはアスペクト比 16:9) がサポートされています。

  |  Video  |  [プレビュー]  |  それでもなお  |  水平視野 (FOV H) |  推奨される使用状況 | 
  |----------|----------|----------|----------|----------|
  |  1280 x 720 |  1280 x 720 |  1280 x 720 |  45deg  |  (既定のモードでビデオ安定化) | 
  |  なし |  なし |  2048 x 1152 |  67deg |  最高の解像度の静止画 | 
  |  1408 x 792 |  1408 x 792 |  1408 x 792 |  48deg |  ビデオ安定化する前にオーバー (埋め込み) の解決 | 
  |  1344 x 756 |  1344 x 756 |  1344 x 756 |  67deg |  オーバーでの大規模な FOV ビデオ モード | 
  |  896 x 504 |  896 x 504 |  896 x 504 |  48deg |  低電力]、[イメージの低解像度モード処理タスク | 

### <a name="hololens-2"></a>HoloLens 2

* 写真/ビデオ (PV) カメラを自動フォーカス オート ホワイト バランス、自動公開、および完全なイメージ処理パイプラインを使用します。
* カメラがアクティブなときに、世界中に接続するホワイト プライバシー LED が点灯します。
* HoloLens 2 では、さまざまなカメラのプロファイルをサポートします。 学習方法[を検出およびカメラ機能を選択](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/camera-profiles)します。
* カメラには、次のプロファイルと解決策の (すべてのビデオ モードはアスペクト比 16:9) がサポートされています。
  
  | Profile                                         | Video     | [プレビュー]   | それでもなお     | フレーム レート | 水平視野 (FOV H) | 推奨される使用状況                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | 従来、0 の BalancedVideoAndPhoto 100             | 2272 x 1278 | 2272 x 1278 |           | 15,30       | 64.69                            | 高品質のビデオ記録                |
  | 従来、0 の BalancedVideoAndPhoto 100             |           |           | 3904 x 2196 |             | 64.69                            | 高品質な写真をキャプチャ                  |
  | BalancedVideoAndPhoto、120                       | 1952 x 1100 | 1952 x 1100 | 1952 x 1100 | 15,30       | 64.69                            | 長期間シナリオ                     |
  | BalancedVideoAndPhoto、120                       | 1504 x 846  | 1504 x 846  |           | 15,30       | 64.69                            | 長期間シナリオ                     |
  | ビデオ会議、100                           | 1952 x 1100 | 1952 x 1100 | 1952 x 1100 | 15,30,60    | 64.69                            | ビデオ会議、長期間シナリオ |
  | ビデオ会議、100                           | 1504 x 846  | 1504 x 846  |           | 5,15,30,60  | 64.69                            | ビデオ会議、長期間シナリオ |
  | ビデオ会議、100 の BalancedVideoAndPhoto 120 | 1920 x 1080 | 1920 x 1080 | 1920 x 1080 | 15,30       | 64.69                            | ビデオ会議、長期間シナリオ |
  | ビデオ会議、100 の BalancedVideoAndPhoto 120 | 1280 x 720  | 1280 x 720  | 1280 x 720  | 15,30       | 64.69                            | ビデオ会議、長期間シナリオ |
  | ビデオ会議、100 の BalancedVideoAndPhoto 120 | 1128 x 635  |           |           | 15,30       | 64.69                            | ビデオ会議、長期間シナリオ |
  | ビデオ会議、100 の BalancedVideoAndPhoto 120 | 960 x 540   |           |           | 15,30       | 64.69                            | ビデオ会議、長期間シナリオ |
  | ビデオ会議、100 の BalancedVideoAndPhoto 120 | 760 x 428   |           |           | 15,30       | 64.69                            | ビデオ会議、長期間シナリオ |
  | ビデオ会議、100 の BalancedVideoAndPhoto 120 | 640x360   |           |           | 15,30       | 64.69                            | ビデオ会議、長期間シナリオ |
  | ビデオ会議、100 の BalancedVideoAndPhoto 120 | 500x282   |           |           | 15,30       | 64.69                            | ビデオ会議、長期間シナリオ |
  | ビデオ会議、100 の BalancedVideoAndPhoto 120 | 424 x 240   |           |           | 15,30       | 64.69                            | ビデオ会議、長期間シナリオ |

>[!NOTE]
>利用[実際のキャプチャを混合](mixed-reality-capture.md)ビデオまたはホログラムとビデオ安定化を含む、アプリの写真をします。
>
>開発者は、顧客がコンテンツをキャプチャしたときにできるだけきれいで検索する場合は、アプリを作成するときに考慮する考慮事項があります。 有効にする (およびカスタマイズできる)、アプリ内で直接から複合現実キャプチャします。 詳細[開発者向けの実際のキャプチャの混合](mixed-reality-capture-for-developers.md)します。

## <a name="locating-the-device-camera-in-the-world"></a>世界中で、デバイスのカメラを検索します。

HoloLens では、写真やビデオを受け取り、ときにキャプチャされたフレームには、透視投影カメラのほか、世界中で、カメラの位置が含まれます。 これにより、イメージング シナリオを拡張現実の世界でカメラの位置に関する理由アプリケーションことができます。 開発者は、お気に入りの画像処理またはカスタム コンピューター ビジョンのライブラリを使用して、独自のシナリオをロール独創的なことができます。

HoloLens のドキュメントの他の場所では「カメラ」は、「仮想ゲームのカメラ」(アプリの視錐台をレンダリングする) を参照できます。 それ以外の場合に示されるように、しない限り、このページでは「カメラ」は現実世界の RGB 色のカメラを指します。

詳細については、このページのカバー [Media Foundation 属性](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx)、組み込み関数を使用してカメラをプルするための Api がありますも[WinRT Api](https://msdn.microsoft.com/library/windows/apps/windows.media.devices.core.cameraintrinsics)します。  

### <a name="images-with-coordinate-systems"></a>座標系を使用したイメージ

各イメージのフレーム (かどうかの写真またはビデオ)、座標系と 2 つの重要な変換が含まれています。 "View"は、カメラに指定された座標システムからのマップおよびイメージのピクセルにカメラからの「射影」マップを変換します。 同時に、これらの変換の定義の各ピクセル光線ピクセルを生成した光子で使用されるパスを表す 3 次元空間で。 フレームの座標系からいくつかその他の座標系に変換を取得することにより、アプリで他のコンテンツへこれら光線を関連付けることができます (などから、[フレームの静止した基準](coordinate-systems.md#stationary-frame-of-reference))。 要約すると、各フレームの画像は次のよう
* ピクセル形式のデータ (を RGB、NV12、JPEG/など)
* メタデータの 3 つの要素 (として格納されている[IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)) 各フレームを"場所を特定できる"ようにします。

|  属性名  |  種類  |  GUID  |  説明 | 
|----------|----------|----------|----------|
|  MFSampleExtension_Spatial_CameraCoordinateSystem  |  IUnknown ([SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx))  |  {9D13C82F-2199-4E67-91CD-D1A4181F2534}  |  ストア、[座標系](coordinate-systems-in-directx.md)キャプチャされたフレームの | 
|  MFSampleExtension_Spatial_CameraViewTransform  |  Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))  |  {4E251FA4-830F-4770-859A-4B8D99AA809B}  |  座標システムでのカメラの外部の変換を格納します。 | 
|  MFSampleExtension_Spatial_CameraProjectionTransform  |  Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))  |  {47F9FCB5-2A02-4F26-A477-792FDF95886A}  |  カメラの projection 変換を格納します。 | 

Projection 変換は、X と Y の両方の軸の +1-1 からまでをイメージ平面上のマップ レンズの組み込みプロパティ (焦点距離、投影の中心の傾斜) を表します。

```
Matrix4x4 format          Terms
   m11 m12 m13 m14      fx    0   0   0
   m21 m22 m23 m24     skew  fy   0   0
   m31 m32 m33 m34      cx   cy   A  -1
   m41 m42 m43 m44       0    0   B   0
```

さまざまなアプリケーションは、さまざまな座標系必要があります。 1 つのアプリケーションのカメラのピクセルを検索するフローの概要を次に示します。

![カメラの座標系に適用された変換](images/pvcameratransform5-500px.png)

### <a name="camera-to-application-specified-coordinate-system"></a>アプリケーションで指定された座標系にカメラ

アプリケーション/ワールド座標系を 'カメラビュー' と 'CameraCoordinateSystem' からは、次が必要です。

[Unity での場所を特定できるカメラ](locatable-camera-in-unity.md):CameraToWorldMatrix は、(ため CameraCoordinateSystem 変換について心配する必要はありません) に自動的に PhotoCaptureFrame クラスによって提供されます。

[DirectX の場所を特定できるカメラ](locatable-camera-in-directx.md):カメラの座標系と独自アプリケーション coordinate system(s) 間で変換を照会する非常に簡単な方法を示しています。

### <a name="application-specified-coordinate-system-to-pixel-coordinates"></a>ピクセル座標を座標システムのアプリケーションで指定されました。

検索またはでカメラ イメージ 3d の特定の場所に描画したいとします。

ビューおよび射影変換の両方の 4 × 4 行列の中には、若干異なる方法で使用する必要があります。 Namely の射影を実行するには後、1 つは"正規化 w で'、投影でこの余分な手順をシミュレート (つまり特定光線に沿ったものに表示されます、同じピクセル)、画面上の同じ 2d 場所として複数の異なる 3d 場所が最終的にできます。 (シェーダー コード) で、キーのポイント:

```
// Usual 3d math:
 float4x4 WorldToCamera = inverse( CameraToWorld );
 float4 CameraSpacePos = mul( WorldToCamera, float4( WorldSpacePos.xyz, 1 ) ); // use 1 as the W component
 // Projection math:
 float4 ImagePosUnnormalized = mul( CameraProjection, float4( CameraSpacePos.xyz, 1 ) ); // use 1 as the W component
 float2 ImagePosProjected = ImagePosUnnormalized.xy / ImagePosUnnormalized.w; // normalize by W, gives -1 to 1 space
 float2 ImagePosZeroToOne = ( ImagePosProjected * 0.5 ) + float2( 0.5, 0.5 ); // good for GPU textures
 int2 PixelPos = int2( ImagePosZeroToOne.x * ImageWidth, ( 1 - ImagePosZeroToOne.y ) * ImageHeight ); // good for CPU textures
```

### <a name="pixel-to-application-specified-coordinate-system"></a>アプリケーションで指定された座標系にピクセル

ワールド座標をピクセルからの移動には、やや難しくなります。

```
float2 ImagePosZeroToOne = float2( PixelPos.x / ImageWidth, 1.0 - (PixelPos.y / ImageHeight ) );
 float2 ImagePosProjected = ( ( ImagePosZeroToOne * 2.0 ) - float2(1,1) ); // -1 to 1 space
 float3 CameraSpacePos = UnProjectVector( Projection, float3( ImagePosProjected, 1) );
 float3 WorldSpaceRayPoint1 = mul( CameraToWorld, float4(0,0,0,1) ); // camera location in world space
 float3 WorldSpaceRayPoint2 = mul( CameraToWorld, CameraSpacePos ); // ray point in world space
```

場所として UnProject を定義します。

```
public static Vector3 UnProjectVector(Matrix4x4 proj, Vector3 to)
 {
   Vector3 from = new Vector3(0, 0, 0);
   var axsX = proj.GetRow(0);
   var axsY = proj.GetRow(1);
   var axsZ = proj.GetRow(2);
   from.z = to.z / axsZ.z;
   from.y = (to.y - (from.z * axsY.z)) / axsY.y;
   from.x = (to.x - (from.z * axsX.z)) / axsX.x;
   return from;
 }
```

ポイントの実際の世界の場所を検索する必要がありますか。 2 つの世界光線とそれぞれの積集合、またはポイントの既知のサイズを検索します。

### <a name="distortion-error"></a>歪みのエラー

HoloLens、ビデオおよび静止画像ストリームされない、システムのイメージ処理パイプラインでは変形 (プレビュー ストリームは、元の歪んだフレームを含む)、アプリケーションで使用できるように、フレーム前にします。 射影行列のみが利用できるので、アプリケーションでも、イメージ フレームを表しますを完璧な一カメラを想定する必要があります、イメージ プロセッサ関数、歪みを除去ただししまう可能性がありますも最大 10 個のピクセルのエラーで投影行列を使用する場合フレームのメタデータ。 多くのユース ケース、場合など、現実世界のポスター/マーカーにホログラムを配置してわかりますが、このエラーが問題ない、< 10px オフセット (位置 2 メートル離れたホログラムの約 11 mm) このゆがみエラーが原因になります。

## <a name="locatable-camera-usage-scenarios"></a>場所を特定できるカメラの使用シナリオ

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>キャプチャされた世界で写真やビデオを表示します。

デバイスのカメラのフレームには"カメラ World"の変換になり、イメージが作成されたときに、デバイスの正確なが表示に使用できます。 小さい holographic アイコン (CameraToWorld.MultiplyPoint(Vector3.zero)) およびも描画カメラには (CameraToWorld.MultiplyVector(Vector3.forward)) が直面していました方向に小さな矢印は、この場所に配置する例。

### <a name="painting-the-world-using-a-camera-shader"></a>カメラのシェーダーを使用して、世界中の描画

このセクションで作成します素材 'シェーダー' 世界が、デバイスのカメラのビューに含めました場所に基づいてその色。 効果的に行うことは各頂点は、カメラを基準には、その場所を把握、ごとのピクセルが図に投影行列を利用し、イメージに関連付けられているテクセルを出力します。 最後に、および必要に応じてよりも多くの夢のようなメモリを表示するイメージのコーナー フェードアウトします。

```
// In the vertex shader:
 float4 worldSpace = mul( ObjectToWorld, float4( vertexPos.xyz, 1));
 float4 cameraSpace = mul( CameraWorldToLocal, float4(worldSpace.xyz, 1));

 // In the pixel shader:
 float4 unprojectedTex = mul( CameraProjection, float4( cameraSpace .xyz, 1));
 float2 projectedTex = (unprojectedTex.xy / unprojectedTex.w);
 float2 unitTexcoord = ((projectedTex * 0.5) + float4(0.5, 0.5, 0, 0));
 float4 cameraTextureColor = tex2D(_CameraTex, unitTexcoord);
 // Fade out edges for better look:
 float pctInView = saturate((1.0 - length(projectedTex.xy)) * 3.0);
 float4 finalColor = float4( cameraTextureColor.rgb, pctInView );
```

### <a name="tag--pattern--poster--object-tracking"></a>タグ/パターン/ポスター/追跡オブジェクト

複合現実の多くのアプリケーションでは、認識可能なイメージや視覚的なパターンを使用して、領域に適したポイントを作成します。 これはオブジェクトを基準としたか、既知の場所を作成、表示するために使用されます。 HoloLens の使用は、調べて (例: QR コードをテレビ モニター) でタグ付けされた現実の世界のオブジェクトを検索、ホログラムを調べて、経由で配置する視覚的に経由での HoloLens との通信にセットアップされているタブレットなどの非 HoloLens デバイスとペアリングWi-fi。

を視覚的なパターンを認識して、アプリケーションのワールド空間におけるそのオブジェクトを配置するには、いくつかの点を必要があります。
1. イメージのパターン認識ツールキット円トラッカー、OCR など、QR コード、AR タグ、顔 finder など。
2. 実行時に、イメージ フレームを収集して認識レイヤーに渡す
3. 世界中の位置や可能性の高い世界光線に戻す、画像の場所を unproject します。 参照先
4. 世界中のこれらの場所の上、仮想モデルを配置します。

いくつかの重要なイメージ処理リンク:
* [OpenCV](http://opencv.org/)
* [QR タグ](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](http://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

対話型アプリケーションのフレーム レートを維持することは、します実行時間の長いイメージ認識アルゴリズムを扱う場合に特に重要な。 このため、次のパターンよく使用します。
1. メイン スレッド: カメラ オブジェクトを管理します。
2. メイン スレッド: 要求の新しいフレーム (非同期)
3. メイン スレッド: スレッドを追跡する新しいフレームを渡す
4. 重要なポイントを収集するスレッドの追跡: プロセスのイメージ
5. メイン スレッド: 一致するように仮想モデルの移動が検出された重要なポイント
6. 手順 2 からメイン スレッド: 繰り返し

イメージのマーカー システムによってのみ 1 つのピクセルの場所を提供する (完全な変換を提供する場合、このセクションでは必要ありません)、可能な場所の光線に相当します。 1 つの 3d の場所を取得するには複数光線を活用し、おおよその重なる部分によって、最終的な結果を検索します。 これを行うには、する必要があります。
1. 複数のカメラのイメージの収集とループします。
2. 検索、[関連付けられている機能のポイント](#pixel-to-application-specified-coordinate-system)、およびその世界光線
3. 機能は、それぞれに複数の世界光線のディクショナリがある場合は、その光線が交差する位置を解決するために、次のコードを使用できます。

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

2 つ以上の追跡対象タグの場所を指定するには、ユーザーの現在のシナリオに合わせて modelled シーンを配置できます。 重力を想定することはできませんがある場合は、次の 3 つのタグの場所を必要があります。 使用して多くの場合白の球体がリアルタイムを表す単純な配色、タグの場所を追跡して青の球体がモデル化のタグの場所を表す、これにより、ユーザーを視覚的に配置の品質を測定します。 すべてのアプリケーションで、次の設定と仮定します。
* 2 つまたは複数のモデル化のタグの場所
* 1 つは「調整スペース」が、シーン内のタグの親であります。
* カメラの機能の識別子
* (は親領域自体、modelled マーカーいないを移動するように注意してください。 他の接続がそれらの相対位置であるため)、リアルタイムのタグを使用して、modelled タグに合わせて調整領域を移動する動作。

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

### <a name="render-holograms-from-the-cameras-position"></a>カメラの位置からホログラムをレンダリングします。

注:独自に作成しようとしている場合[実際のキャプチャ (MRC) を混在](mixed-reality-capture.md)、カメラのストリームを持つホログラムをブレンドする、使用することができます、 [MRC 効果](mixed-reality-capture-for-developers.md)showHolograms プロパティを有効にまたは[Unity での場所を特定できるカメラ](locatable-camera-in-unity.md)します。

RGB カメラ ストリーム上で直接特殊なレンダリングを実行したい場合、カスタム ホログラム記録/ライブ プレビューを提供するためにカメラの位置からの領域でホログラム ビデオ フィードとの同期をレンダリングすることは。

Skype、HoloLens のユーザーが認識されて、リモート クライアントを表示して、同じホログラムと対話することを行います。 Skype サービスを通じて各ビデオのフレーム経由で送信する前に、各フレームの対応するカメラのデータを取得します。 ビデオのフレームを使用してカメラの外部と組み込みのメタデータをパッケージ化し、Skype サービス経由で送信します。

受信側では、Unity を使用してした既に同期されてすべて同じ座標系を使用して、HoloLens のユーザーの領域でホログラムの。 これにより、カメラの外部メタデータを使用して、HoloLens のユーザーがそのビデオのフレームをキャプチャしたときに立っていました (、ホログラムの残りの部分) を基準と世界中で正確な場所に Unity のカメラを配置するカメラの組み込みの情報を使用して、できます。ビューは、同じことを確認します。

カメラが適切に設定したら、Skype、HoloLens ユーザーには Graphics.Blit を使用しての複合現実ビューの作成から受け取りましたフレーム上にカメラが表示されるどのようなホログラムを組み合わせています。

```cs
private void OnFrameReceived(Texture frameTexture, Vector3 cameraPosition, Quaternion cameraRotation, Matrix4x4 cameraProjectionMatrix)
{
    //set material that will be blitted onto the RenderTexture
    this.compositeMaterial.SetTexture(CompositeRenderer.CameraTextureMaterialProperty, frameTexture);
    //set the camera to be that of the HoloLens's device camera
    this.Camera.transform.position = cameraPosition;
    this.Camera.transform.rotation = cameraRotation;
    this.Camera.projectionMatrix = cameraProjectionMatrix;
    //trigger the Graphics's Blit now that the frame and camera are set up
    this.TextureReady = false;
}
private void OnRenderImage(RenderTexture source, RenderTexture destination)
{
    if (!this.TextureReady)
    {
        Graphics.Blit(source, destination, this.compositeMaterial);
        this.TextureReady = true;
    }
}
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>追跡またはタグ付けされた固定の識別または移動現実世界のオブジェクト/顔 Led または認識エンジンの他のライブラリを使用して

例:
* Led の産業ロボット (または低速に移動するため QR コードのオブジェクト)
* 識別し、ルーム内のオブジェクトを認識
* 識別し、(例: 場所 holographic 連絡先カード顔) ルーム内のユーザーの認識

## <a name="see-also"></a>関連項目
* [DirectX での場所を特定できるカメラ](locatable-camera-in-directx.md)
* [Unity での場所を特定できるカメラ](locatable-camera-in-unity.md)
* [複合現実キャプチャ](mixed-reality-capture.md)
* [開発者向け複合現実キャプチャ](mixed-reality-capture-for-developers.md)
* [メディアのキャプチャの概要](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
