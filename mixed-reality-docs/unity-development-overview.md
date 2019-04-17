---
title: Unity 開発の概要
description: 構築の作業開始の複合現実アプリ Unity でします。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity では、実際には、開発、作業の開始、新しいプロジェクト、移植、機能、カメラ、シミュレーション、エミュレーション、ドキュメントの混在
ms.openlocfilehash: fc40ef4eae31cf22f640be2666c5af3afb717ff3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604548"
---
# <a name="unity-development-overview"></a>Unity 開発の概要

最も高速パスのビルド方法、 [mixed reality アプリ](app-views.md)は[Unity](http://aka.ms/HoloLensUnity)。 探索する時間を取ることをお勧めします。、 [Unity チュートリアル](https://unity3d.com/learn/tutorials)します。 Unity が包括的で資産が必要な場合[Asset Store](https://www.assetstore.unity3d.com/)します。 アクセスすることができます、Unity の基本的な知識を蓄積した後、 [Mixed Reality Academy](academy.md)を Unity での複合現実開発の詳細を参照してください。 参照してください、 [Unity Mixed Reality フォーラム](http://forum.unity3d.com/forums/hololens.102/)が発生する問題の解決策を見つけて、コミュニティの構築、Unity での複合現実アプリの残りの部分とかかわります。

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Windows Mixed Reality への既存の Unity アプリの移植

Windows Mixed Reality を移植する既存の Unity プロジェクトを使用する場合はと共にに従って、 [Unity 移植のガイド](porting-guides.md)を開始します。

## <a name="configuring-a-new-unity-project-for-windows-mixed-reality"></a>Windows Mixed Reality を新しい Unity プロジェクトを構成します。

まず、Unity を使用した複合現実アプリの構築を開始する[ツールをインストールする](install-the-tools.md)します。 HoloLens ではなく Windows Mixed Reality イマーシブ ヘッドセットする対象とするが場合、は、ここでは、Unity の特別なバージョンを必要があります。

新しい Unity プロジェクトをいま作成した場合は、少数の Unity の設定の 2 つのカテゴリに分類、Windows Mixed Reality を変更する必要があります。 プロジェクトごとおよびシーンごと。

### <a name="per-project-settings"></a>プロジェクトの設定

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

アプリは、基本的な holographic レンダリングと空間の入力を今すぐ実行できます。 さらに移動し、特定の機能を活用するには、アプリは、自らのマニフェストで適切な機能を宣言しなければなりません。 すべての後続のプロジェクトのエクスポートに含まれるように、Unity でマニフェストの宣言を作成できます。 設定がある**プレーヤー設定 > ユニバーサル Windows プラットフォームの設定 > 発行の設定 > 機能**します。 For Mixed Reality Unity Api の一般的な使用を有効にするための適用可能な機能は次のとおりです。

|  機能  |  Api の機能を必要とします。 | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (へのアクセスを[空間マッピング](spatial-mapping.md)HoloLens でメッシュ)&mdash;*ヘッドセットの一般的な空間の追跡に必要な機能もありません* | 
|  WebCam  |  PhotoCapture と VideoCapture | 
|  PicturesLibrary/VideosLibrary  |  PhotoCapture または VideoCapture、それぞれ (格納するときにキャプチャしたコンテンツ) | 
|  マイク  |  VideoCapture (オーディオをキャプチャ) するときに、DictationRecognizer、GrammarRecognizer、および KeywordRecognizer | 
|  internetClient  |  DictationRecognizer (および Unity Profiler を使用する) | 

**Unity の品質の設定**

![Unity の品質の設定](images/unityqualitysettings-350px.png)<br>
*Unity の品質の設定*

HoloLens では、mobile クラス GPU があります。 場合は、アプリは、HoloLens をターゲットとするが、完全なフレーム レートを維持するということを確認する最速のパフォーマンス チューニング、品質設定します。
1. 選択**編集 > プロジェクトの設定 > 品質**
2. 選択、**ドロップダウン**下、 **Windows ストア**ロゴと選択**Fastest**します。 設定すると正しく適用はご存知でしょう Windows ストアの列のボックスと**Fastest**行は緑色です。

### <a name="per-scene-settings"></a>シーンごとの設定

**Unity のカメラ設定**

![Unity のカメラ設定](images/unitycamerasettings.png)<br>
*Unity のカメラ設定*

「仮想現実サポート」チェック ボックスを有効にすると、 [Unity カメラ](camera-in-unity.md)コンポーネント ハンドル[追跡とステレオスコ ピック レンダリング ヘッド](rendering.md)します。 これを行うカスタム カメラに置き換える必要はありません。

アプリでは、具体的には HoloLens をターゲットが場合、は、現実の世界をアプリに表示されますので、デバイスの透過的な表示、最適化するために変更する必要があるいくつかの設定があります。
1. **階層**を選択、 **Main Camera**
2. **インスペクター**パネルで、設定、変換**位置**に**0, 0, 0**ユーザー ヘッドの位置が、Unity の世界配信元で起動するようです。
3. 変更**フラグをクリア**に**単色**します。
4. 変更、**バック グラウンド**する色**RGBA 0,0,0,0**します。 黒は、HoloLens で透明としてレンダリングします。
5. 変更**Clipping - つまり近く**を[推奨 HoloLens](camera-in-unity.md#clip-planes) 0.85 (メートル)。

削除し、新しいカメラを作成した場合、カメラが確認**タグ**として**MainCamera**します。

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>複合現実の機能および入力の追加

前述のように、プロジェクトを構成したら、(カメラ) などの標準の Unity ゲーム オブジェクトが点灯直後の**取り付けられているスケール エクスペリエンス**、ユーザーとして自動的に更新するカメラの位置に移動します。自分の頭世界をします。

Windows Mixed Reality 機能のサポートを追加するなど、[空間ステージ](coordinate-systems.md#spatial-coordinate-systems)、[ジェスチャ、モーションのコント ローラー](gestures-and-motion-controllers-in-unity.md)または[音声入力](voice-input-in-unity.md)に直接組み込まれている Api を使用して実現されますUnity です。

最初の手順は、確認する必要があります、[スケールが発生する](coordinate-systems.md)アプリを対象とします。
* ビルドに必要な場合、**向き専用**または**取り付けられているスケール エクスペリエンス**、設定する必要があります Unity に領域の種類の追跡の[静止](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。
* ビルドに必要な場合、**継続スケール**または**ルーム スケール エクスペリエンス**、Unity のことを確認する必要がありますに正常に設定されて領域の種類を追跡[RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)します。
* ビルドに必要な場合、**世界規模**、HoloLens でエクスペリエンスをユーザーが 5 m を超えるローミングできるようにすることを使用する必要があります、 [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience)コンポーネント。

すべての複合現実アプリ用のコア ビルディング ブロックは、その他の Unity Api を使用した一貫性のある方法で公開されます。
* [カメラ](camera-in-unity.md)
* [座標系](coordinate-systems-in-unity.md)
* [視線入力](gaze-in-unity.md)
* [ジェスチャとアニメーション コント ローラー](gestures-and-motion-controllers-in-unity.md)
* [音声入力](voice-input-in-unity.md)
* [永続化](persistence-in-unity.md)
* [空間のサウンド](spatial-sound-in-unity.md)
* [空間マッピング](spatial-mapping-in-unity.md)

多くの複合現実アプリは、使用する Unity アプリにも公開するその他の主な機能があります。
* [共有エクスペリエンス](shared-experiences-in-unity.md)
* [場所を特定できるカメラ](locatable-camera-in-unity.md)
* [フォーカス ポイント](focus-point-in-unity.md)
* [損失の追跡](tracking-loss-in-unity.md)
* [[キーボード]](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>実際、またはシミュレートされたデバイスで Unity プロジェクトを実行しています。

次の手順は、ようになったら、holographic の Unity プロジェクトをテストする準備ができて、[をエクスポートし、Unity Visual Studio ソリューションをビルド](exporting-and-building-a-unity-visual-studio-solution.md)します。

手の形でその VS ソリューションとできますし、アプリを実行する 3 つの方法のいずれかでいずれかを使用して実際またはシミュレーション上のデバイス。
* [実際 HoloLens や Windows Mixed Reality イマーシブ ヘッドセットを展開します。](using-visual-studio.md)
* [HoloLens のエミュレーターへのデプロイします。](using-the-hololens-emulator.md)
* [Windows Mixed Reality イマーシブ ヘッドセット シミュレーターへのデプロイします。](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Unity のドキュメント

このドキュメントの他使用可能な Windows デベロッパー センターでは、Unity は Unity エディターと共に Windows Mixed Reality 機能のドキュメントをインストールします。 Unity のドキュメントには、2 つのセクションが含まれています。 提供されています。
1. **Unity スクリプトのリファレンス**
    * ドキュメントのこのセクションには、Unity が提供するスクリプト API の詳細が含まれています。
    * Unity エディターからを通じてアクセス可能な**ヘルプ > スクリプトのリファレンス**
2. **Unity マニュアル**
    * このマニュアルは、高度な基本的な手法から Unity を使用する方法を学習するために設計されています。
    * Unity エディターからを通じてアクセス可能な**ヘルプ > 手動**

## <a name="see-also"></a>関連項目
* [MR 基礎 100:Unity の概要](holograms-100.md)
* [Unity の推奨設定](recommended-settings-for-unity.md)
* [Unity のパフォーマンスに関する推奨事項](performance-recommendations-for-unity.md)
* [エクスポートして、Unity Visual Studio ソリューションを構築します。](exporting-and-building-a-unity-visual-studio-solution.md)
* [HoloLens の Unity アプリを使用して Windows 名前空間の使用](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Unity と Visual Studio を使用するためのベスト プラクティス](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity の再生モード](unity-play-mode.md)
* [移植のガイド](porting-guides.md)
