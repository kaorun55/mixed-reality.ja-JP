---
title: Unreal での HoloLens 写真/ビデオ カメラ
description: HoloLens 写真/ビデオを Unreal で使用するためのガイド
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, カメラ, PV カメラ, MRC
ms.openlocfilehash: 06ceb26d58fe60848e5e90360aa2e05984a901c5
ms.sourcegitcommit: f24ac845e184c2f90e8b15adab9addb913f5cb83
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2020
ms.locfileid: "84451337"
---
# <a name="hololens-photovideo-camera-in-unreal"></a>Unreal での HoloLens 写真/ビデオ カメラ

HoloLens には、Mixed Reality Capture (MRC) に使用される写真/ビデオ (PV) カメラがあり、アプリで実際のビジュアルにアクセスするために使用できます。

## <a name="render-from-the-pv-camera-for-mrc"></a>MRC 用の PV カメラからのレンダリング

> [!NOTE]
> これには **Unreal Engine 4.25** 以降のバージョンが必要です。

システムとカスタム MRC レコーダーは、PV カメラとイマーシブ アプリによってレンダリングされたホログラムを組み合わせることにより、Mixed Reality キャプチャを作成します。

既定では、Mixed Reality キャプチャでは、右目のホログラフィック出力が使用されます。 イマーシブ アプリが [PV カメラ](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)からのレンダリングを選択した場合は、それが代わりに使用されます。 これにより、現実世界と MRC ビデオのホログラムとの間のマッピングが向上します。

PV カメラからの表示をオプトインするには、次のようにします。

1. **SetEnabledMixedRealityCamera** および **ResizeMixedRealityCamera** の呼び出し
    * **サイズ X** および**サイズ Y** の値を使用して、ビデオのディメンションを設定します。

![第 3 のカメラ](images/unreal-camera-3rd.PNG)

その後、Unreal は MRC からのリクエストを処理して、PV カメラの視点からレンダリングします。

> [!NOTE]
> [Mixed Reality キャプチャ](mixed-reality-capture.md)がトリガーされた場合にのみ、アプリは写真/ビデオ カメラの視点からレンダリングするよう求められます。

## <a name="using-the-pv-camera"></a>PV カメラの使用

Web カメラ テクスチャは実行時にゲームで入手できますが、エディターの **[編集] > [プロジェクトの設定]** で有効にする必要があります。
1. **[プラットフォーム] > [HoloLens] > [機能]** に移動し、**Web カメラ**を確認します。
    * 実行時に Web カメラを使用するには、**StartCameraCapture** 関数を使用し、記録を停止するには、**StopCameraCapture** 関数を使用します。

![カメラの開始と停止](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a>イメージのレンダリング
カメラ イメージをレンダリングするには次のようにします。
1. 以下のスクリーンショットでは **PVCamMat** という名前のプロジェクトのマテリアルに基づいて、ダイナミック マテリアル インスタンスを作成します。  
2. ダイナミック マテリアル インスタンスを **Material Instance Dynamic Object Reference** 変数に設定します。  
3. カメラ フィードをレンダリングするシーン内のオブジェクトのマテリアルを、この新しいダイナミック マテリアル インスタンスに設定します。
    * カメラ イメージをマテリアルにバインドするために使用されるタイマーを開始します。 

![カメラのレンダリング](images/unreal-camera-render.PNG)

4. このタイマーに新しい関数 (この場合は **MaterialTimer**) を作成し、**GetARCameraImage** を呼び出して、Web カメラからテクスチャを取得します。  
5. このテクスチャが有効な場合は、シェーダーのテクスチャ パラメーターをこのイメージに設定します。  そうでない場合は、もう一度素材のタイマーを開始します。 

![カメラのテクスチャ](images/unreal-camera-texture.PNG)

5. マテリアルに、カラー エントリにバインドされている **SetTextureParameterValue** の名前と一致するパラメータがあることを確認します。 これを行わないと、カメラ イメージを正しく表示できません。

![カメラのテクスチャ](images/unreal-camera-material.PNG)

## <a name="see-also"></a>関連項目
* [場所を特定できるカメラ](locatable-camera.md)
* [開発者向け複合現実キャプチャ](mixed-reality-capture-for-developers.md)
