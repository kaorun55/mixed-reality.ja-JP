---
title: Unreal での HoloLens カメラ
description: HoloLens カメラを Unreal で使用するためのガイド
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, カメラ, 第 3 のカメラ, MRC
ms.openlocfilehash: 9ef9ce27d161130c6b9f3aa6bb1dbc47d7608ad9
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840121"
---
# <a name="hololens-camera-in-unreal"></a>Unreal での HoloLens カメラ

## <a name="third-camera-mixed-reality-capture"></a>第 3 のカメラの Mixed Reality キャプチャ

第 3 のカメラの Mixed Reality キャプチャ (MRC) を使用すると、目のテクスチャの視点ではなく、HoloLens バイザー上のカメラの視点から Mixed Reality キャプチャをレンダリングできます。  これにより、現実世界と MRC ビデオのホログラムとの間のマッピングが向上します。 

第 3 のカメラの MRC の使用をオプトインするには、SetEnabledMixedRealityCamera と ResizeMixedRealityCamera を必要なビデオの次元で呼び出します。 

![第 3 のカメラ](images/unreal-camera-3rd.PNG)

次に、HoloLens デバイス ポータルで MRC ビデオを記録します。 

## <a name="pv-camera"></a>PV カメラ

Web カメラのテクスチャを、実行時にゲームで取得することもできます。  HoloLens で Web カメラのテクスチャを実現するには、[プロジェクト設定] > [プラットフォーム] > [HoloLens] > [機能] の下にある Unreal エディターで、最初に "Web カメラ" 機能を確実にオンにします。 

StartCameraCapture 関数を使用して、実行時に Web カメラの使用をオプトインします。  キャプチャを停止するには、StopCameraCapture 関数を使用します。 

![カメラの開始と停止](images/unreal-camera-startstop.PNG)

カメラのイメージをレンダリングするには、まず、プロジェクトの素材に基づいて動的な素材のインスタンスを作成します。  この例では、PVCamMat という名前の素材に基づいています。  これを、[Material Instance Dynamic Object Reference]\(素材インスタンスの動的オブジェクト参照\) 型の変数に設定します。  次に、カメラ フィードをこの新しい動的素材インスタンスにレンダリングするオブジェクトの素材をシーンに設定し、カメラのイメージを素材にバインドするために使用するタイマーを開始します。 

![カメラのレンダリング](images/unreal-camera-render.PNG)

このタイマーに新しい関数 (この場合は MaterialTimer) を作成し、GetARCameraImage を呼び出して、Web カメラからテクスチャを取得します。  このテクスチャが有効な場合は、シェーダーのテクスチャ パラメーターをこのイメージに設定します。  そうでない場合は、もう一度素材のタイマーを開始します。 

![カメラのテクスチャ](images/unreal-camera-texture.PNG)

この素材には、カメラのイメージを適切に表示するためにカラー エントリにバインドされている、SetTextureParameterValue 内の名前と一致するパラメーターが必要です。 

![カメラのテクスチャ](images/unreal-camera-material.PNG)

## <a name="see-also"></a>関連項目
* [場所を特定できるカメラ](locatable-camera.md)
* [開発者向け複合現実キャプチャ](mixed-reality-capture-for-developers.md)
