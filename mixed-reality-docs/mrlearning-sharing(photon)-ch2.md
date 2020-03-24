---
title: マルチユーザー機能のチュートリアル - 2. Unity の開発に向けた準備
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法を学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: f7ae77d6978b5da860d890bcfe5b6f7c3d4640c8
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031240"
---
# <a name="2-getting-unity-ready-for-development"></a>2.Unity の開発に向けた準備

このチュートリアルでは、Mixed Reality Toolkit のインポート、ビルド設定の構成、シーンの準備など、アプリケーション開発に向けて Unity を準備して構成する方法を学習します。

## <a name="objectives"></a>目標

* アプリケーション開発のために Unity を構成する
* Mixed Reality ツールキットをインポートする
* プロジェクト シーンを準備する

## <a name="instructions"></a>手順

1. [こちら](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)をクリックして、Mixed Reality Toolkit Foundation Unity パッケージをダウンロードして保存します。

2. Unity で、[Assets]\(アセット\) メニューをクリックして [Import Package]\(パッケージのインポート\) を選択し、[Custom Package]\(カスタム パッケージ\) をクリックします。

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. 手順 1 に示されているリンクからダウンロードした Unity パッケージを選択します。 [Import]\(インポート\) ポップアップ ウィンドウが Unity に表示されたら、[Import]\(インポート\) ボタンをクリックして MRTK のインポートを開始します。 この処理には数分かかることがあります。

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    >ダウンロードしたパッケージは、ファイルを保存したローカル フォルダーにあります。 上の図では、パッケージのある場所は示されていません。

    パッケージがインポートされると、[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウが表示されます。 表示されない場合は、Unity メニューの [Mixed Reality Toolkit] > [Utilities]\(ユーティリティ\) > [Configure Unity Project]\(Unity プロジェクトの構成\) を選択して開きます。

    [MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウで、[Modify Configurations]\(構成の変更\) セクションを展開し、[Enable MSBuild for Unity]\(MSBuild for Unity を有効にする\) チェックボックスをオフにし、他のすべてのオプションがオンになっていることを確認し、[Apply]\(適用\) ボタンをクリックして設定を適用します。

    ![Module3Chapter2note1im](images/module3chapter2note1im-missing01.png)

    > [!CAUTION]
    > MSBuild for Unity は使用するすべての SDK をサポートしていない場合があり、有効にした後は無効にするのが困難な場合があります。 そのため、MSBuild for Unity を有効にしないことを強くお勧めします。
    
4. 新しいシーンを作成します。 これを行うには、[File]\(ファイル\) をクリックし、[New Scene]\(新しいシーン\) を選択します。 HLSharedProjectMain として保存します。

5. Mixed Reality Toolkit の下で、[Add to Scene and Configure]\(シーンに追加して構成\) をクリックします。

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. これが完了したら、階層から [Mixed-Reality Toolkit (MRTK)] を選択します。 [Inspector]\(インスペクター\) パネルで、MRTK の構成プロファイルを [DefaultHoloLens2ConfigurationProfile] に変更します。

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima-missing01.png)

7. 階層から [Mixed-Reality Toolkit (MRTK)] を選択します。 [Inspector]\(インスペクター\) パネルで Mixed Reality Toolkit (Script) を探し、次の図に示すように [Copy & Customize]\(コピーしてカスタマイズ\) ボタンを押します。  この後、ポップアップが表示されます。ポップアップ メニューで [Clone]\(複製\) オプションを選択します。

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. 診断ウィンドウを非表示にする場合は、下にスクロールし、[Enable Diagnostics system]\(診断システムを有効にする\) チェックボックスをオフにします。 アプリケーションの開発中は、パフォーマンスを監視するために診断ウィンドウを有効なままにし、運用またはアプリケーションのデモンストレーション中は無効にすることをお勧めします。 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. Ctrl + Shift + B を押すか、[File]\(ファイル\) > [Build Settings]\(ビルド設定\) に移動して、ビルド設定を開きます。 プログラムが現在、[PC, Mac and Linux Standalone]\(PC、Mac、および Linux のスタンドアロン\) プラットフォームに設定されていることに注意してください。 HoloLens 2 の開発の場合は、プラットフォームを [Universal Windows Platform]\(ユニバーサル Windows プラットフォーム\) に設定します。 それを選択し、[Switch Platform]\(プラットフォームの切り替え\) をクリックします。

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. 完了したら、[Add Open Scenes]\(オープン シーンの追加\) というボックスをクリックします。 次に、[Inspector]\(インスペクター\) パネルに移動し、[Virtual Reality Supported]\(仮想現実がサポートされている\) の右側にあるチェック ボックスがオンになっている (下の図を参照) ことを確認します。 また、次の図に示すように、[scenes/HLSharedProjectMain]\(シーン/HLSharedProjectMain\) の横のチェック ボックスもオンになっていることを確認します。

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. [Inspector]\(インスペクター\) パネルの [Publishing Settings]\(発行の設定\) セクションで、下にスクロールして [Capabilities]\(機能\) に移動し、次のチェック ボックスがオンになっていることを確認します。

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. 一覧表示されているカスタム パッケージをインポートします。

    * [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (バージョン 2.1.1)
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    >Azure Spatial Anchors 用に Unity プロジェクトを構成する方法については、[Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) のチュートリアル シリーズの一部である「[Azure Spatial Anchors をお使いになる前に](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1)」チュートリアルを参照してください。


13. [Project]\(プロジェクト\) パネルで、[Prefabs] フォルダーに移動します。 次の手順では、いくつかのプレハブをシーンに実装します。 [Prefabs] フォルダーで、[Debug Window] というプレハブをクリックして階層にドラッグします。 完了したら、[File]\(ファイル\)、[Save]\(保存\) の順にクリックするか、Ctrl + S を押して、プロジェクトを保存します。

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    プレハブをクリックするとポップアップが表示され、TMP Essentials について尋ねられることがあります。 それらは必要なので、[Import TMP Essentials]\(TMP Essentials のインポート\) をクリックします。 このポップアップが表示された場合は、テキストに関連したエラーが発生しないように、階層からプレハブを削除し、再び階層にドラッグする必要がある場合があります。

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a>結論

Unity プロジェクトを Photon で使用する準備ができました。 この後のチュートリアルでは、このシーンに基づき、完全な共有エクスペリエンスに向けて Unity プロジェクトを構築します。

[次のチュートリアル: 3.複数ユーザーの接続](mrlearning-sharing(photon)-ch3.md)
