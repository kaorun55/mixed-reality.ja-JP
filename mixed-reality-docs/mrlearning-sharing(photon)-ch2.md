---
title: 複数ユーザー機能のチュートリアル-2. Unity を開発用に準備する
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, チュートリアル, hololens
ms.openlocfilehash: 6abf4fa8fc87afc7007d6f7c76becfbd88ed7a12
ms.sourcegitcommit: 2bfe9b1af4ee2cc0d668caeccb8ebc3137cbc20b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901515"
---
# <a name="2-getting-unity-ready-for-development"></a>2. Unity を開発用に準備する

このチュートリアルでは、Mixed Reality Toolkit のインポート、ビルド設定の構成、シーンの準備など、アプリケーション開発のために Unity を準備して構成する方法について説明します。

## <a name="objectives"></a>目標

* アプリケーション開発のための Unity の構成
* Mixed Reality ツールキットをインポートする
* プロジェクトシーンを準備する

## <a name="instructions"></a>手順

1. ここをクリックして、Mixed Reality Toolkit Foundation unity パッケージをダウンロードして保存し[ます。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)

2. Unity で、[アセット] メニューをクリックし、[パッケージのインポート] をクリックして、[カスタムパッケージ] をクリックします。

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. 手順 1. で指定したリンクからダウンロードした Unity パッケージを選択します。 [インポート] ポップアップウィンドウが Unity に表示されたら、[インポート] ボタンをクリックして MRTK のインポートを開始します。 これには数分かかる場合があります。

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    >ダウンロードしたパッケージは、ファイルを保存したローカルフォルダーにあります。 上の図では、パッケージを検索する場所はされるません。

4. 新しいシーンを作成します。 これを行うには、[ファイル] をクリックし、[新しいシーン] を選択します。 HLSharedProjectMain として保存します。

    次の図のようなポップアップが表示されることがあります。 ここでは、[いいえ] をクリックします。
    ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. Mixed Reality Toolkit の [シーンに追加] をクリックし、[構成] をクリックします。

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. この処理が完了すると、新しい構成ファイルが表示され、プロファイルをカスタマイズすることができます。

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima.PNG)

7. 階層から [Mixed-Reality Toolkit (MRTK)] を選択します。 [インスペクター] パネルで、Mixed Reality Toolkit スクリプトを探して、次の図に示すように [Copy & Customize] ボタンを押します。  この後、ポップアップメニューの [複製] オプションを選択すると、pop が表示されます。

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. [診断] ウィンドウを非表示にする場合は、下にスクロールし、[診断システムを有効にする] チェックボックスをオフにします。 アプリケーションの開発中は、パフォーマンスを監視し、運用またはアプリケーションのデモンストレーション中に無効にすることをお勧めします。 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. Ctrl + shift + B キーを押すか、[ファイル > ビルド設定] に移動して、ビルド設定を開きます。 プログラムは、現在 PC、Mac、および Linux スタンドアロンプラットフォームで設定されていることに注意してください。 HoloLens 2 開発の場合は、プラットフォームをユニバーサル Windows プラットフォームに設定します。 それを選択し、[プラットフォームの切り替え] をクリックします。

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. 完了したら、[Open シーンの追加] というボックスをクリックします。 次に、[インスペクター] パネルにアクセスし、[サポートされている仮想現実 (下の図を参照)] の右側にあるチェックボックスがオンになっていることを確認します。 また、次の図に示すように、[シーン/HLSharedProjectMain] の横のチェックボックスもオンになっていることを確認します。

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. [インスペクター] パネルの [発行の設定] セクションで、[機能] まで下にスクロールし、次のチェックボックスがオンになっていることを確認します。

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. 一覧表示されたカスタムパッケージをインポートします。

    」を参照します。 [AzureSpatialAnchors unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (バージョン 2.0.0)

    b. [MRTK。HoloLens2. 2.1.0.1. unitypackage を実行します。](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)

    c. [MRTK。HoloLens2. AzureSpatialAnchors. 2.1.0.1. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

    d. [MRTK。HoloLens2. 2.1.0.1. unitypackage のようになります。](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    >Azure 空間アンカー用に Unity プロジェクトを構成する方法については、 [azure 空間アンカーチュートリアルシリーズ](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1)の一部である[azure 空間](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1)アンカーの概要に関するチュートリアルを参照してください。

    ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

13. [プロジェクト] パネルで、Prefabs フォルダーにアクセスします。 次の手順では、いくつかの prefabs をシーンに実装します。 Prefabs フォルダーで、[prefab]、[デバッグ] ウィンドウをクリックし、階層にドラッグします。 完了したら、[ファイル] をクリックし、[保存] をクリックしてプロジェクトを保存するか、ctrl + S キーを押します。

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    Prefab をクリックするとポップアップが表示され、TMP Essentials について質問されることがあります。 必要に応じて、[TMP Essentials のインポート] をクリックします。 このポップアップが表示された場合は、テキスト関連のエラーが発生しないように、階層から prefab を削除し、階層に再ドラッグする必要がある場合があります。

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a>結論

Unity プロジェクトは Photon の準備ができました。 今後のチュートリアルでは、このシーンと Unity プロジェクトを完全な共有エクスペリエンスに向けて構築します。

[次のチュートリアル: 3. 複数のユーザーを接続する](mrlearning-sharing(photon)-ch3.md)
