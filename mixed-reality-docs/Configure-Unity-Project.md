---
title: Windows Mixed Reality を新しい Unity プロジェクトを構成します。
description: MRTK なしの Unity プロジェクトを構成します。
author: yoyoz
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity では、実際には、開発、はじめに、新しいプロジェクトの混在
ms.openlocfilehash: aad38474781fd78425d48034877122d36d9e3e93
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2019
ms.locfileid: "65940753"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>Windows Mixed Reality を新しい Unity プロジェクトを構成します。 

(MRTK v2 は、Unity プロジェクトに既にインポートした場合は省略)

Mixed Reality ツールキットをインポートせず、新しい Unity プロジェクトを作成したい場合は、少数の Unity の設定が 2 つのカテゴリに分類、Windows Mixed Reality を手動で変更する必要があります。 プロジェクトごとおよびシーンごと。

## <a name="per-project-settings"></a>プロジェクトの設定

Windows Mixed Reality を対象とは、まず、ユニバーサル Windows プラットフォーム アプリとしてエクスポートする Unity プロジェクトを設定する必要があります。
1. 選択**ファイル > の設定を作成しています.**
2. 選択**ユニバーサル Windows プラットフォーム**、プラットフォームに一覧表示し、クリックして**スイッチ プラットフォーム**
3. 設定**SDK**に**ユニバーサル 10**
4. 設定**ターゲット デバイス**に**任意のデバイス**イマーシブ ヘッドセットをサポートするかに切り替えてに**HoloLens**
5. 設定**ビルドの種類**に**D3D**
6. 設定**UWP SDK**に**インストールされている最新**

Unity エクスポートしようとしましたが、アプリが作成することを把握できるようにする必要があります、[没入型ビュー](app-views.md) 2D ビューではなく。 そのために、「仮想現実サポート」を有効にします。
1. **ビルド設定しています.** ウィンドウを開いて、**プレーヤー設定しています.**
2. 選択、**ユニバーサル Windows プラットフォームの設定** タブ
3. 展開、 **XR 設定**グループ
4. **XR 設定** セクションで、チェック、**仮想現実サポート**を追加するチェック ボックスをオン、**仮想現実デバイス**一覧。
5. **XR 設定**グループで、ことを確認します **"Windows Mixed Reality"** サポートされているデバイスとして表示されます。 (この場合がありますに表示されます"Windows Holographic"として以前のバージョンの Unity)

![Unity の品質の設定](images/getting-started-unity-quality-settings.jpg)<br>
*Unity xr の設定*

アプリは、基本的な holographic レンダリングと空間の入力を今すぐ実行できます。 さらに移動し、特定の機能を活用するには、アプリは、自らのマニフェストで適切な機能を宣言しなければなりません。 すべての後続のプロジェクトのエクスポートに含まれるように、Unity でマニフェストの宣言を作成できます。 設定がある**プレーヤー設定 > ユニバーサル Windows プラットフォームの設定 > 発行の設定 > 機能**します。 For Mixed Reality Unity Api の一般的な使用を有効にするための適用可能な機能は次のとおりです。

|  機能  |  Api の機能を必要とします。 | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (へのアクセスを[空間マッピング](spatial-mapping.md)HoloLens でメッシュ)&mdash;*ヘッドセットの一般的な空間の追跡に必要な機能もありません* | 
|  WebCam  |  PhotoCapture と VideoCapture | 
|  PicturesLibrary/VideosLibrary  |  PhotoCapture または VideoCapture、それぞれ (格納するときにキャプチャしたコンテンツ) | 
|  マイク  |  VideoCapture (オーディオをキャプチャ) するときに、DictationRecognizer、GrammarRecognizer、および KeywordRecognizer | 
|  internetClient  |  DictationRecognizer (および Unity Profiler を使用する) | 

**Unity の品質の設定**

![Unity の品質の設定](images/getting-started-unity-quality-settings.jpg)<br>
*Unity の品質の設定*

HoloLens では、mobile クラス GPU があります。 場合は、アプリは、HoloLens をターゲットとするが、完全なフレーム レートを維持するということを確認する最速のパフォーマンス チューニング、品質設定します。
1. 選択**編集 > プロジェクトの設定 > 品質**
2. 選択、**ドロップダウン**下、 **Windows ストア**ロゴと選択**Very Low**します。 設定すると正しく適用はご存知でしょう Windows ストアの列にあるボックスと**Very Low**行は緑色です。

## <a name="per-scene-settings"></a>シーンごとの設定

**Unity のカメラ設定**

![Unity のカメラ設定](images/Unitycamerasettings.png)<br>
*Unity のカメラ設定*

「仮想現実サポート」チェック ボックスを有効にすると、 [Unity カメラ](camera-in-unity.md)コンポーネント ハンドル[追跡とステレオスコ ピック レンダリング ヘッド](rendering.md)します。 これを行うカスタム カメラに置き換える必要はありません。

アプリでは、具体的には HoloLens をターゲットが場合、は、現実の世界をアプリに表示されますので、デバイスの透過的な表示、最適化するために変更する必要があるいくつかの設定があります。
1. **階層**を選択、 **Main Camera**
2. **インスペクター**パネルで、設定、変換**位置**に**0, 0, 0**ユーザー ヘッドの位置が、Unity の世界配信元で起動するようです。
3. 変更**フラグをクリア**に**単色**します。
4. 変更、**バック グラウンド**する色**RGBA 0,0,0,0**します。 黒は、HoloLens で透明としてレンダリングします。
5. 変更**Clipping - つまり近く**を[推奨 HoloLens](camera-in-unity.md#clip-planes) 0.85 (メートル)。

削除し、新しいカメラを作成した場合、カメラが確認**タグ**として**MainCamera**します。


## <a name="see-also"></a>関連項目
* [複合現実 Toolkit v2](mrtk-getting-started.md)
* [Unity 開発の概要](unity-development-overview.md)
