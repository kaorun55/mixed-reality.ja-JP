---
title: Unreal での QR コード
description: Unreal で QR コードを使用するためのガイド
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, QR コード
ms.openlocfilehash: 67a3a8092ab908cba6768e92ed6a0e7bd2737275
ms.sourcegitcommit: 5b802078090700e06630c8fc665fedeaa0a16eb7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83342660"
---
# <a name="qr-codes-in-unreal"></a>Unreal での QR コード

HoloLens では、空間上の QR コードを見つけて、現実世界の既知の位置にホログラムをレンダリングできます。  これは、エクスペリエンスを共有するために、同じ場所にある複数のデバイスでホログラムをレンダリングするためにも使用できます。 

HoloLens で QR の検出を有効にするには、[プロジェクト設定] > [プラットフォーム] > [HoloLens] > [機能] の下にある Unreal エディターで、"Web カメラ" 機能を確実にオンにします。  

StartARSession 関数を使用して ARSession を開始することにより、Unreal で QR コード追跡を使用することをオプトインします。 

QR コードは、追跡対象のイメージとして、Unreal の AR で追跡されたジオメトリ システムによって表示されます。  これを使用するには、ブループリント アクターに AR Trackable Notify コンポーネントを追加します。 

![QR の AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

次に、コンポーネントの詳細にアクセスし、監視するイベントの緑色の [+] ボタンをクリックします。  

![QR のイベント](images/unreal-spatialmapping-events.PNG)

ここでは、OnUpdateTrackedImage をサブスクライブして、QR コードの中心にポイントをレンダリングし、QR コードのエンコードされたデータを出力しています。 

![QR のレンダリングの例](images/unreal-qr-render.PNG)

最初に、追跡したイメージを ARTrackedQRCode にキャストして、現在の更新されたイメージが QR コードであることを確認します。  これで、QRCode 変数を使用して、エンコードされたデータを取得できます。  QR コードの左上は、GetLocalToWorldTransform の場所から取得できます。  次元は GetEstimateSize で取得できます。 

すべての QR コードに独自の GUID があります。 

![QR の GUID](images/unreal-qr-guid.PNG)

## <a name="see-also"></a>関連項目
* [QR コードの追跡](qr-code-tracking.md)
