---
title: Windows Mixed Reality 用の新しい Unity プロジェクトを構成する
description: MRTK を使用せずに Unity プロジェクトを構成する
author: thetuvix
ms.author: alexturn
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, mixed reality, 開発, 作業の開始, 新しいプロジェクト
ms.openlocfilehash: 99c72f2d9d900c8a05fb7d8b9b8de10d657fdd13
ms.sourcegitcommit: 7e8b9de561cbc8483e84511f3e9cbd779f3a999f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/27/2019
ms.locfileid: "75502653"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>Windows Mixed Reality 用の新しい Unity プロジェクトを構成する 

(Unity プロジェクトに MRTK v2 が既にインポートされている場合はスキップします)

混合 Reality ツールキットをインポートせずに新しい Unity プロジェクトを作成する場合は、Windows Mixed Reality に対して手動で変更する必要がある Unity 設定の小さなセットがあります。これは、プロジェクトごととシーン単位の2つのカテゴリに分類されます。

## <a name="per-project-settings"></a>プロジェクトごとの設定

Windows Mixed Reality をターゲットにするには、最初に Unity プロジェクトをユニバーサル Windows プラットフォームアプリとしてエクスポートするように設定する必要があります。 
1. **ファイル > ビルド設定**を選択してください...
2. プラットフォーム ボックスの一覧の **ユニバーサル Windows プラットフォーム**を選択し、**プラットフォームの切り替え** をクリックします。
3. **SDK**を**Universal 10**に設定する
4. イマーシブヘッドセットまたは**HoloLens**への切り替えをサポートするために、**ターゲットデバイス**を**任意のデバイス**に設定する
5. **ビルドの種類**を**D3D**に設定
6. **UWP SDK**を**最新のインストール**に設定する

次に、エクスポートしようとしているアプリが2D ビューではなく[イマーシブビュー](app-views.md)を作成する必要があることを Unity に知らせる必要があります。 これを行うには、"Virtual Reality がサポートされている" を有効にします。
1. **[ビルドの設定...]** ウィンドウで、プレーヤーの **[設定]** を開きます。
2. [ユニバーサル Windows プラットフォーム] タブ**の設定**を選択します。
3. **[XR Settings]** グループを展開します。
4. **[XR の設定]** セクションで、 **[仮想現実のサポート]** チェックボックスをオンにして、 **[仮想現実のデバイス]** の一覧を追加します。
5. **[XR 設定]** グループで、 **"Windows Mixed Reality"** がサポートされているデバイスとして表示されていることを確認します。 (以前のバージョンの Unity では、"Windows Holographic" として表示される場合があります)

![Unity 品質設定](images/getting-started-unity-quality-settings.jpg)<br>
*Unity xr の設定*

これで、アプリで基本的な holographic のレンダリングと空間入力を行うことができるようになりました。 特定の機能を利用するには、アプリでマニフェスト内の適切な機能を宣言する必要があります。 マニフェスト宣言は Unity で作成できるため、後続のすべてのプロジェクトエクスポートに含まれます。 設定は、**ユニバーサル Windows プラットフォーム > の発行設定 > 機能の [プレーヤーの設定 > 設定**] にあります。 一般的に使用される Unity Api を混合現実に対して有効にするための適用可能な機能は次のとおりです。

|  機能  |  機能を必要とする Api | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (HoloLens の[空間マッピング](spatial-mapping.md)メッシュへのアクセス)&mdash;*ヘッドセットの一般的な空間追跡に必要な機能はありません* | 
|  WebCam  |  PhotoCapture と VideoCapture | 
|  PicturesLibrary / VideosLibrary  |  PhotoCapture または VideoCapture (キャプチャされたコンテンツを格納する場合) | 
|  マイク  |  VideoCapture (オーディオをキャプチャする場合)、DictationRecognizer、GrammarRecognizer、および KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (および Unity Profiler の使用) | 

**Unity の品質設定**

![Unity 品質設定](images/getting-started-unity-quality-settings.jpg)<br>
*Unity の品質設定*

HoloLens には、モバイルクラスの GPU があります。 アプリが HoloLens を対象としている場合は、完全なフレームレートを維持するために、品質設定のパフォーマンスを最速に調整することをお勧めします。
1. **[プロジェクト設定の編集 > の > 品質]** を選択します。
2. **Windows ストア**のロゴの下にある**ドロップダウン**を選択し、 **[非常に低い]** を選択します。 Windows ストアの列のボックスと**非常に少ない**行が緑色になっている場合は、設定が正しく適用されていることがわかります。

## <a name="per-scene-settings"></a>シーンごとの設定

**Unity カメラの設定**

![Unity カメラの設定](images/Unitycamerasettings.png)<br>
*Unity カメラの設定*

"Virtual Reality がサポートされています" チェックボックスをオンにすると、 [Unity カメラ](camera-in-unity.md)コンポーネントは[ヘッドトラッキングとステレオスコピックレンダリング](rendering.md)を処理します。 これを行うには、カスタムカメラで置き換える必要はありません。

アプリが HoloLens を対象としている場合は、デバイスの透明なディスプレイを最適化するために変更する必要がある設定がいくつかあります。そのため、アプリは物理的な世界に表示されます。
1. **階層**で、**メインカメラ**を選択します。
2. **[インスペクター]** パネルで、変換 **[位置]** を**0、0、0**に設定します。これにより、ユーザーのヘッドの位置が Unity の元の場所から開始されます。
3. **クリアフラグ**を**純色**に変更します。
4. **背景**色を**RGBA 0、0、0、0**に変更します。 ブラックは HoloLens では透明としてレンダリングされます。
5. **クリッププレーン**を[HoloLens の推奨](camera-in-unity.md#clip-planes)0.85 (メーター) に近い場所に変更します。

新しいカメラを削除して作成する場合は、カメラが**maincamera**として**タグ付け**されていることを確認してください。


## <a name="see-also"></a>「
* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [Unity 開発の概要](unity-development-overview.md)
