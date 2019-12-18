---
title: 空間オーディオのチュートリアル-1. プロジェクトへの空間オーディオの追加
description: Microsoft Spatializer プラグインを Unity プロジェクトに追加して、HoloLens 2 HRTF ハードウェアオフロードにアクセスします。
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality、unity、チュートリアル、hololens2、空間オーディオ
ms.openlocfilehash: 8978017b3ce6c49a81b3eee2fe21e9234f4e71f0
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182799"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a>Unity プロジェクトへの空間オーディオの追加

HoloLens2 の空間オーディオ tutioral for Unity へようこそ。 このチュートリアルでは、次の手順について説明します。
* Unity の HoloLens 2 で HRTF offload を使用する方法
* HRTF オフロードを使用するときにリバーブを有効にする方法

[Microsoft Spatializer GitHub リポジトリ](https://github.com/microsoft/spatialaudio-unity)には、このチュートリアルシーケンスの完成した Unity プロジェクトが用意されています。 

サウンドの spatialize に役立つ場合の推奨事項については、「[空間サウンドの設計](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)」を参照してください。

## <a name="objectives"></a>目標
この最初の章では、次のことについて説明します。
* Unity プロジェクトを作成して MRTK をインポートする
* Microsoft spatializer プラグインをインポートする
* Microsoft spatializer プラグインを有効にする
* 開発者ワークステーションで空間オーディオを有効にする

## <a name="create-a-project-and-add-nuget-for-unity"></a>プロジェクトを作成し、Unity の NuGet を追加する
空の Unity プロジェクトから開始し、Unity 用に NuGet を追加して構成します。
1. 最新の NuGetForUnity をダウンロードし[ます。 unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)
2. Unity のメニューバーで、 **[資産-> インポートパッケージ-> カスタムパッケージ]** をクリックし、NuGetForUnity パッケージをインストールします。

![カスタムパッケージのインポート](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a>Windows Mixed Reality パッケージを追加する
Unity 2019 以降での Windows Mixed Reality のサポートは、オプションのパッケージに含まれています。 プロジェクトに追加するには、Unity のメニューバーから [ **Window-> Package Manager]** を開きます。

![パッケージマネージャーメニュー](images/spatial-audio/package-manager-menu.png)

次に、 **Windows Mixed Reality**パッケージを検索してインストールします。

![パッケージマネージャーウィンドウ](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a>MRTK と Microsoft Spatializer をインストールする
Unity 用の NuGet を使用して、MRTK と Microsoft Spatializer プラグインをインストールします。
1. Unity のメニューバーで、[ **nuget->] [Nuget パッケージの管理**] の順にクリックします。

![NuGet パッケージの管理](images/spatial-audio/manage-nuget-packages.png)

2. **検索**ボックスに「MixedReality」と入力し、MRTK コアパッケージ ( **MixedReality** ) をインストールしてください。

![MRTK NuGet パッケージ](images/spatial-audio/mrtk-nuget-package.png)

[Mrtk NuGet パッケージ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html)には、追加のコンテキストと詳細があります。

4. **検索**ボックスに「SpatialAudio」と入力し、microsoft Spatializer パッケージ: **SpatialAudio**をインストールします。

![Spatializer プラグイン NuGet](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a>プロジェクトでの MRTK の設定

1. ビルドの設定 ウィンドウを開き、**ファイル > ビルドの設定** に移動します。

2. _ユニバーサル Windows プラットフォーム_を選択し、 **[プラットフォームの切り替え]** をクリックします。

3. [**ビルド] ウィンドウ**の **[プレーヤーの設定]** をクリックして、 **[インスペクター]** ウィンドウの **[プレーヤーの設定]** プロパティを開きます。
    * **[XR の設定]** で、 **[Virtual Reality がサポート]** する チェックボックスをオンにします。
    * **[XR の設定]** で、**ステレオレンダリングモード**を**シングルパスインスタンス**化に変更します。
    * **[発行の設定]** で、 **[機能]** セクションの **[空間の認識]** チェックボックスをオンにします。

4. メニューバーで  **Mixed Reality Toolkit-> シーンに追加 を**クリックし、構成 をクリックします。 を使用して、シーンに MRTK を追加します。

アプリをビルドして HoloLens 2 にデプロイする方法など、その他のガイダンスについては、 [MR ラーニングベースモジュールの第1章](mrlearning-base-ch1.md)を参照してください。

## <a name="enable-the-microsoft-spatializer-plugin"></a>Microsoft Spatializer プラグインを有効にする
**Microsoft Spatializer**プラグインを有効にします。 **[編集-> プロジェクトの設定-> オーディオ]** を開き、 **Spatializer プラグイン**を "Microsoft Spatializer" に変更します。 **プロジェクト設定**の**Audio**セクションは次のようになります。

![Spatializer プラグインを表示するプロジェクト設定](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a>ワークステーションで空間オーディオを有効にする
Windows のデスクトップバージョンでは、空間オーディオは既定で無効になっています。 これを有効にするには、タスクバーのボリュームアイコンを右クリックします。 HoloLens 2 で耳になる内容を最大限に活用するには、 **[空間サウンド > Windows Sonic For ヘッドホン]** を選択します。

![デスクトップ空間オーディオの設定](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> この設定は、Unity エディターでプロジェクトをテストする場合にのみ必要です。

## <a name="next-steps"></a>次のステップ
[Unity の空間オーディオ chapter 2](unity-spatial-audio-ch2.md) to spatialize button 対話サウンドに進みます。

