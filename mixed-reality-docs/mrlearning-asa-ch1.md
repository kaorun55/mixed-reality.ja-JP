---
title: Azure 空間アンカーチュートリアル-1. Azure 空間アンカーの概要
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: fb7074849c5a07a95b370b5bfa75228fac36ba5b
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105959"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Azure 空間アンカーの概要

HoloLens 2 チュートリアルの2番目のモジュールへようこそ。 作業を開始する前に、すべての[前提条件](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens)が満たされていることを確認してください。 最初の[ベースモジュール](mrlearning-base.md)をまだ完了していない場合は、最初にそのモジュールを完了することをお勧めします。 新しい Unity プロジェクトから開始する場合は、[ベースモジュール](mrlearning-base.md)の新しいプロジェクト作成手順に従います。 

## <a name="objectives"></a>目標

* HoloLens 2 を使用した Azure 空間アンカーを使用した開発の基礎について説明します。

* 空間アンカーを作成、アップロード、ダウンロードする

## <a name="instructions"></a>手順

### <a name="downloading-and-importing-assets"></a>アセットのダウンロードとインポート
開始する前に、次のアセットをダウンロードしてインポートします。

[Azure 空間アンカー v 1.1.0](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage)

[HoloLens2. 2.1.0.0. unitypackage を実行します。](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage)

[HoloLens2. AzureSpatialAnchor. 2.1.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchor-v2.1.0.0/Unity.HoloLens2.AzureSpatialAnchor.Tutorials.Asset.2.1.0.0.unitypackage)

[Mixed Reality Toolkit Foundation パッケージ2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.1.0)

1. プロジェクトに新しいシーンを作成します。 シーンフォルダーを右クリックし、[作成]、[シーン] の順にクリックします。 新しいシーンに "ASALearningModule" という名前を付けます。

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. [ASALearningmodule] シーンをダブルクリックすると、新しいシーンと共に表示される定義済みの項目が表示されます。 
3. 混合現実開発のシーンを構成します。 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> 注: [Mixed Reality Toolkit のプロファイル](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html)を選択するためのポップアップダイアログボックスが表示される場合があります。 *DefaultHoloLens2ConfigurationProfile*という名前のプロファイルをダブルクリックして選択します。

4. MRTK のファイルを選択する場合は、[DefaultMixedRealityToolkitConfigurationProfile] を選択します。

> 注: 独自の構成プロファイルがある場合は、代わりに自由に使用できます。
>

![module2chapter1step4im](images/module2chapter1step4im.PNG)

これで、シーンが混合現実用に構成されました。 シーンを保存していることを確認します (これを行うには、control/command + S を使用するか、[ファイル] をクリックして、[保存] をクリックします)。 

5. 手順 1. でダウンロードした[Azure 空間アンカー v 1.1.0](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage) unity パッケージをインポートします。 その場合は、[資産] をクリックし、[パッケージのインポート] に移動します。 [カスタムパッケージ] をクリックします。コンピューターのファイルが開きます。 その場合は、Azure 空間アンカーパッケージを保存した場所を見つけて、それを選択します。 [開く] をクリックします。

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

ポップアップが表示され、ツールと設定の一覧が表示され、インポートする内容を確認するメッセージが表示されます。 使用可能な***すべて***のオプションを選択し、[インポート] をクリックします。

![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

> メモ: しばらくお待ちください。インポートには数分かかります。 

6. [HoloLens2. 2.1.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage) next. をインポートします。 手順 5. と同じように、Unity に戻り、[アセット] をクリックして、[インポートパッケージ] にカーソルを合わせます。 [カスタムパッケージ] をクリックします。コンピューターのファイルが再び表示されます。 Base module Asset Pack を格納した場所に移動します。 を選択します。 [開く] をクリックします。

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

> 注: このモジュールでは、後で必要となる資産が増える場合があります。 ここで説明したアセットをインポートするには、次の手順に従います。 

7. 他のパッケージをインポートする場合と同じ手順を使用して、 [ASA module pack 1.3.1](https://github.com/Developer-OI/MixedRealityLearning/releases/download/ASA_1.3/ASAModuleAssets_1.3.1.unitypackage)をインポートします。

### <a name="configuring-your-scene"></a>シーンの構成

このセクションでは、prefabs とスクリプトをシーンに追加して、アプリケーションでローカルアンカーと Azure 空間アンカーの両方が動作する方法の基礎を示す一連のボタンを作成します。

8. [プロジェクト] タブの [アセット] フォルダーの下で、[ASAmoduleAssets] をクリックします。 選択すると、2つの prefabs: ButtonParent と ParentAnchor が表示されます。

![module2chapter1step7im](images/module2chapter1step7im.PNG)

9. 両方の prefabs をシーンにドラッグします。 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

注: ButtonParent をシーンに追加すると、TMP アセットをインポートするように求めるポップアップが表示されます。 "TMP Essentials" をインポートします。 その後、シーンに大きなフォントテキストが表示された場合は、ButtonParent オブジェクトを削除し、ASAmoduleAssets フォルダーからもう一度追加します。

注: HoloLens のデバッグログを確認する場合は、 DebugWindow prefab を ASAModuleAssets フォルダーからシーンにドラッグアンドドロップできます。 DebugWindow inspector パネルで DebugWindowMessaging スクリプトをアタッチし、[デバッグウィンドウを有効にする] オプションを有効にします。 その後、DebugWindow prefab を Debugwindow 空のフィールドにドラッグアンドドロップします。 また、必要に応じて、DebugWindow の位置を調整することもできます。

10. シーンを拡大するには、階層内の親アンカーをダブルクリックし、必要に応じてシーン全体を表示するようにビューを調整します。 現在、ParentAnchor は、デモンストレーションのみを目的として使用される色付きのキューブです。 最終的には、キューブを非表示にして、コンテンツを ParentAnchor の子として配置します。 

11. 次に、シーンを操作するためのボタンを構成します。 そのためには、ButtonParent prefab を展開し、ラベルの付いたボタンをいくつか確認します。 これらのボタンは、MRTK の PressableButton prefabs から作成されます。 [基本モジュール](mrlearning-base-ch2.md)から PressableButton を作成する方法について説明します。 これらのボタンを操作するには、ユーザーが個々のボタンを押したとき、または選択したときにトリガーされるイベントを追加する必要があります。 

- StartAzureSession という名前のボタンについては、Click イベントトリガーおよび On Click イベントトリガーの下に新しいイベントを作成します。 ParentAnchor オブジェクトを空のフィールドにドラッグし、次のスクリーンショットに示すように、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから StartAzureSession () メソッドを割り当てます。
- ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- ボタン名として [StopAzureSession] をクリックし、Click イベントトリガーおよび On Click イベントトリガーの下に新しいイベントを作成します。 ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから StopAzureSession () メソッドを割り当てます。

- [CreateAnchor] という名前のボタンに対して、ボタン押されたイベントトリガーおよび On Click イベントトリガーの下に新しいイベントを作成します。 ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから CreateAzureAnchor () メソッドを割り当てます。  **その後、ParentAnchor を次の空の [Game Object] \ (ゲームオブジェクト \) フィールドにもう一度ドラッグします。**

- という名前のボタンについては、アンカーの検索を開始し、Click Click イベントトリガーと On Click イベントトリガーの下に新しいイベントを作成します。 ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから FindAzureAnchor () メソッドを割り当てます。

- [DeleteAzureAnchor] という名前のボタンに対して、Click イベントトリガーおよび On Click イベントトリガーの下に新しいイベントを作成します。 ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから DeleteAzureAnchor () メソッドを割り当てます。  

- [ローカルアンカーの削除] という名前のボタンに対して、Click イベントトリガーおよび On Click イベントトリガーの下に新しいイベントを作成します。 ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから RemoveLocalAnchor () メソッドを割り当てます。 **その後、ParentAnchor オブジェクトを、次の空の [Game Object] \ (ゲームオブジェクト \) フィールドにもう一度ドラッグします。**

12. Azure 空間アンカーを設定するには、assets フォルダー内の AzureSpatialAnchorsPlugin フォルダーに移動し、[例-> Resources-> AzureSpatialAnchorsDemoConfig file] に移動します。 [インスペクター] パネルで、先ほど作成した Azure アカウント ID とアカウントキーを追加します。 まだ作成していない場合、または所有していない場合は、[前提条件](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens)に従ってください。 

  ![module2chapter1step13im](images/module2chapter1step13im.PNG)

### <a name="build-and-demonstrate-base-application"></a>基本アプリケーションのビルドとデモンストレーション

ここでは、Azure 空間アンカーの基本を示すためにシーンが構成されたので、Azure 空間アンカーの基本的な動作について説明します。 

1. [ファイル > ビルドの設定] に移動して、[ビルドの設定] ウィンドウを再び開きます。
    ![mrlearning-ch1--ステップごとの](images/mrlearning-asa-ch1-3-step1.jpg)
2. [開いているシーンを追加] ボタンをクリックして、目的のシーンがビルドリストのシーンにあることを確認します。
3. プラットフォームがユニバーサル Windows プラットフォームに設定されていることを確認します。 そうでない場合は、同じに設定してください。
4. [プレーヤーの設定] ボタンをクリックし、[発行の設定] にアクセスします。 [機能] で、[インターネット]、[インターネットクライアントサーバー]、[プライベートネットワーククライアントサーバー]、[リムーバブル記憶域]、[Webcam]、[マイクと空間認識] を有効にします。
5. 同じプレーヤー設定で、XR settings にアクセスして、でサポートされている仮想現実を選択します。
6. [ビルド] ボタンを押して、ビルド プロセスを開始します。
   ![mrlearning-ch1-手順 6](images/mrlearning-asa-ch1-3-step6.jpg)
7. アプリケーション用の新しいフォルダーを作成して、名前を付けます。 次の図では、アプリケーションを格納するために、App という名前のフォルダーが作成されています。 [フォルダーの選択] をクリックして、新しく作成したフォルダーへのビルドを開始します。 ビルドが完了したら、Unity の [ビルドの設定] ウィンドウを閉じることができます。

    ![mrlearning-ch1-step7](images/mrlearning-asa-ch1-3-step7.jpg)

    > 注: ビルドに失敗した場合は、もう一度ビルドするか、Unity を再起動して、もう一度ビルドしてみてください。 "エラー: CS0246 = 型または名前空間の名前" XX "が見つからないというエラーが表示された場合は、using ディレクティブまたはアセンブリ参照が不足しています。 [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)のインストールが必要になる場合があります。 


8. ビルドが正常に完了した後でも、次のようにエラーが発生する可能性がありますが、ビルドが成功した場合は無視して次の手順に進むことができます。

    ![mrlearning-ch1-step7B](images/mrlearning-asa-ch1-3-step7B.png)

    

9. ビルドが完了したら、新しくビルドされたアプリケーション ファイルが含まれている、新しく作成されたフォルダーを開きます。 "MixedRealityBase" ソリューションまたは対応する名前をダブルクリックします。 プロジェクトに代替名を使用して、Visual Studio でソリューションファイルを開く場合。

    > メモ: 新しく作成されたフォルダー (つまり、前の手順の名前付け規則に従っている場合は、アプリフォルダー) を必ず開いてください。これは、ビルドフォルダー内の .sln ファイルと混同しないように、同じ名前の .sln ファイルがそのフォルダーの外部に存在するためです。

    ![mrlearning-ch1-step8](images/mrlearning-asa-ch1-3-step8.jpg)

    > 注: Visual Studio で新しいコンポーネントのインストールを求められた場合は、 [[ツールのインストール] ページ](install-the-tools.md)で、前提条件となるすべてのコンポーネントが特定のコンポーネントとしてインストールされていることを確認してください。


9. USB ケーブルを使って HoloLens 2 を PC に接続します。 これらのレッスンの手順では、HoloLens 2 デバイスでテストをデプロイすることを想定していますが、 [hololens 2 エミュレーター](using-the-hololens-emulator.md)にデプロイするか、[サイドローディング用のアプリパッケージの](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)作成を選択することもできます。

10. デバイスにビルドする前に、デバイスが開発者モードであることを確認してください。 HoloLens 2 に初めてデプロイする場合は、Visual Studio により、PIN を使用して HoloLens 2 をペアリングするよう求められる場合があります。 開発者モードを有効にする必要がある場合、または Visual Studio と組み合わせて使用する場合は、[次の手順](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio)に従います。

11. リリース構成と ARM アーキテクチャを選択して、HoloLens 2 にビルドするように Visual Studio を構成します。

    ![mrlearning-ch1-step11](images/mrlearning-asa-ch1-3-step11.jpg)


12. 最後の手順は、デバッグ > デバッグなしで開始 を選択してデバイスにビルドすることです。 [デバッグなしで開始] を選択すると、Visual Studio にデバッグ情報が表示されずにビルドが成功したときに、アプリケーションがすぐにデバイスで起動します。 これは、アプリケーションが停止することなく HoloLens 2 上で実行されている間は、USB ケーブルを取り外すことができることも意味します。 また、[ビルド > デプロイ] を選択して、アプリケーションを自動的に起動せずにデバイスにデプロイすることもできます。

    ![mrlearning-ch1-step12](images/mrlearning-asa-ch1-3-step12.jpg)

>注: Azure 空間アンカーは、インターネットを使用してアンカーデータを保存して読み込みます。そのため、ASA アプリをテストする前に、デバイスがインターネットに接続されていることを確認してください。

13. 画面の指示に従います。 
    デバイスでアプリケーションが実行されている場合は、画面の指示に従います。 次の手順に対応するシーンボタンを押します。 前の手順で説明したようにデバッグウィンドウを追加した場合は、個々のボタンの押下に関するフィードバックと、Azure 空間アンカーに関連する個々の操作の進行状況を確認できます。

![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. 空間アンカーセッションを開始します。
    
    2. キューブを別の場所に移動します。
    
    3. キューブの場所に Azure 空間アンカーを保存します。
    
    4. Azure 空間アンカーセッションを停止します。
    
    5. キューブのローカルアンカーを削除して、ユーザーがキューブを移動できるようにします。
    
    6. キューブを別の場所に移動します。
    
    7. Azure 空間アンカーセッションを開始します。
    
    8. Azure 空間アンカーを検索します。 
    アンカーを作成したときに、元の場所に戻ります。
    
    9. Azure 空間アンカーを削除します。
    
    10. Azure セッションを停止します。

### <a name="anchoring-an-experience"></a>エクスペリエンスを固定する

前のセクションでは、Azure 空間アンカーの基礎について学習しました。 キューブを使用して、アタッチされたアンカーで親ゲームオブジェクトを表現し、視覚化しました。 このセクションでは、ParentAnchor オブジェクトの子として配置することで、エクスペリエンス全体を固定する方法について説明します。 この例では、「[基本モジュールレッスン 6](mrlearning-base-ch6.md)」で作成した旧暦モジュールアセンブリデモンストレーションアプリケーションを使用します。

1. "ロケットランチャー Complete" prefab を検索し、次の図に示すように、オブジェクトの子として階層にドラッグします。

![module2chapter1step11](images/module2chapter1step11im.PNG)

2. 次の図に示すように、モジュールのアセンブリエクスペリエンスを配置して、キューブが引き続き公開されるようにします。 アプリケーションでは、ユーザーはキューブを移動することで、エクスペリエンス全体を再配置できます。 

![module2chapter1step12im](images/module2chapter1step12im.PNG)

> 注: エクスペリエンスを再配置するためのさまざまなユーザーエクスペリエンスフローがあります。たとえば、ボタンを使用して、操作を囲む境界ボックスの切り替え、オブジェクトの再配置 (この手順で使用されるキューブなど)、位置と回転の使用などがあります。ギズモなど。

## <a name="congratulations"></a>結論
このチュートリアルでは、Azure 空間アンカーの基礎について学習しました。 このレッスンでは、Azure セッションを開始および停止するために必要なさまざまな手順を説明し、1つのデバイスで azure のアンカーを作成、アップロード、ダウンロードするためのボタンをいくつか紹介しました。 次のレッスンでは、アプリケーションを再起動した後でも、Azure anchor Id を HoloLens 2 に保存して取得する方法について説明します。 このシリーズでは、空間アラインメントを実現するために複数のデバイス間でアンカー Id を転送する方法や、マルチユーザー共有セッションについて学習する方法についても説明します。

[次のレッスン: 2. Azure 空間アンカーの保存、取得、共有](mrlearning-asa-ch2.md)

