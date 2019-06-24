---
title: MR Learning ASA モジュール HoloLens 2 での Azure 空間アンカー
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 7843e4de014fe14d7c40b5e6d68f72ea45b4df9e
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326892"
---
# <a name="getting-started-with-azure-spatial-anchors-on-hololens-2"></a>HoloLens 2 で空間アンカーを Azure の概要

2 番目のモジュールの HoloLens 2 のチュートリアルへようこそ。 始める前に、必ずすべての[の前提条件](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens)が完了します。 まず、完了していない場合[ベース モジュール](mrlearning-base.md)まだ、強くお勧めその最初が完了することです。 新しい unity プロジェクトから開始する場合は 新しいプロジェクトの作成手順に従ってください、[ベース モジュール](mrlearning-base.md)します。 

## <a name="objectives"></a>目標

* HoloLens 2 Azure 空間アンカーを使用した開発の基礎を学習します。

* 作成、アップロード、および空間アンカーのダウンロード

  

## <a name="instructions"></a>手順

### <a name="downloading-and-importing-assets"></a>ダウンロードとアセットのインポート
始める前は、ダウンロードして、次のアセットをインポートする必要があります。

[Azure Spatial Anchors](https://github.com/azure/azure-spatial-anchors-samples/releases)

[資産パックの MR ベース モジュール](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)

[ASA モジュール資産パック](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_B2)

[Mixed Reality ツールキット](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

> 注: Azure 空間アンカー、MR ベース モジュール資産パックの具体的な手順について、手順 6、および Mixed Reality Toolkit の具体的な手順について、手順 3 ~ 4 をインポートする方法の具体的な手順については、手順 5 を参照してください。

1. プロジェクトに新しいシーンを作成します。 シーンのフォルダーを右クリックして、「作成、」シーンをクリックします。 名前を新しいシーン"ASALearningmodule"

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. "ASALearningmodule"をダブルクリック、新しいシーンと共に表示されるいくつか事前定義済みの項目を確認します。 
3. 複合現実の開発のシーンを構成します。 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> 注:示すポップアップが表示されます、「ファイルは Mixed Reality ツールキットを選択する必要があります」します。 [Ok] の順にクリックでは、手順 4 に表示されます。

4. Mixed Reality Toolkit のファイルを選択するときに選択して、"DefaultMixedRealityToolkitConfigurationProfile"

   > 注:独自の構成プロファイルを自由に代わりに使用する場合は。

![module2chapter1step4im](images/module2chapter1step4im.PNG)

シーンを複合現実用に構成されました。 シーンを保存してください (どちらのコントロールで行う/コマンド + S、またはファイルをクリックします をクリックして保存) します。 

5. インポート、 [Azure 空間アンカー](https://github.com/azure/azure-spatial-anchors-samples/releases)します。 空間アンカーを使用するには、このアセットをインポートする必要があります。 そのため、上記のリンクをクリックし、"AzureSpatialAnchors.unitypackage"を右クリックしてください "ターゲット"の保存と保存をコンピューターをクリックします。 

   ![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

   次に保存した後、unity に戻り、[アセット、"パッケージのインポート"、"まで移動では、「カスタム パッケージ...」] をクリックしてコンピューターのファイルが開きます。 1 回の操作を行いますが、Azure 空間アンカー パッケージを保存した検索および選択します。 クリックして「を開きます」

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   今すぐ与える一連のツールと設定をインポートするように求めるポップアップがあります。 選択***すべて***"使用可能なオプションのインポート をクリックします。

   ![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

   > 注: インポートする場合に、これには数分かかります待ちください。 

   6. インポート[MR ベース モジュール資産パック](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)[次へ]。 手順 5 と同じように上記のリンクをクリックして、"BasemoduleAssetsV1 1.unitypackage"を右クリックして、コンピューターに"ターゲット"の保存と保存をクリックします。

   ![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

   > ヒント:簡単に見つけにアクセスできるように、同じフォルダーにこれらすべての資産を保存します。 便利で、構成されたすべてのものが維持されます。

   手順に戻り、unity に移動して、5 と同じようには、「資産」、「パッケージのインポート」にマウスをクリックし、「カスタム パッケージ.」をクリックします。もう一度、コンピューターのファイルが表示されますので資産パックのベース モジュールを格納した場所に移動され、選択。 クリックして「を開きます」

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   > 注: がこのモジュールで後で必要な複数のアセットがあります。 この時点で説明されているすべてのアセットをインポートする次の手順に従います。 

7. ASA モジュールの以前のパッケージのインポートと同じアプローチを使用してパックをインポートします。

### <a name="configuring-your-scene"></a>シーンの構成

このセクションで追加される予定プレハブとスクリプトの一連のアプリケーションでのローカルのアンカーと空間アンカーを Azure の両方の動作方法の基礎を説明するボタンを作成するシーンに。

7. 「プロジェクト」 タブで、アセット フォルダーの下に、"ASAmoduleAssets。"をクリックします。 選択したら、"ButtonParent"と"ParentAnchor"の 2 つのプレハブが表示されます。

![module2chapter1step7im](images/module2chapter1step7im.PNG)

8. シーンのプレハブの両方にドラッグします。 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

9. 親のアンカーをダブルクリックします。 シーン全体を参照してください、そのため、必要に応じて、シーンを調整する表示を調整する必要があります。

    ParentAnchor プレハブを理解します。 現時点では、"ParentAnchor"という名前のゲーム オブジェクトには、デモンストレーション用の色付きのキューブです。 最終的には、キューブを非表示にはされ、ParentAnchor の子として、コンテンツを配置します。 このプレハブには、(ASA SDK に含まれる) AzureSpatialAnchorsDemoWrapper.cs スクリプトと ParentAnchor オブジェクトに ASAmoduleScript.cs スクリプト (このモジュールの一部として含まれています) が含まれます。 

10. ボタンを構成します。 ParentAnchor プレハブ、いくつかのラベルの付いたボタンが表示されます。 これらのボタンは、MRTK の PressableButton のプレハブから作成されます。 Pressable ボタンを作成する方法について説明します、[ベース モジュール](mrlearning-base-ch2.md)します。 各ボタンを押すか、以下の一覧に従ってボタンを選択したときにトリガーされるイベントを追加します。 

- "StartAzureSession"をという名前のボタン、イベント トリガーの「ボタンが押されている」と「クリックして」イベント トリガーの下に新しいイベントを作成します。 空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから StartAzureSession() メソッドを割り当てます。

  ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

  ![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

  ![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- "StopAzureSession"をという名前のボタン、イベント トリガーの「ボタンが押されている」と「クリックして」イベント トリガーの下に新しいイベントを作成します。 空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから StopAzureSession() メソッドを割り当てます。

- "CreateAnchor"をという名前のボタン、イベント トリガーの「ボタンが押されている」と「クリックして」イベント トリガーの下に新しいイベントを作成します。 空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから CreateAzureAnchor() メソッドを割り当てます。

- 「開始お探しのアンカー」をという名前のボタン、イベント トリガーの「ボタンが押されている」と「クリックして」イベント トリガーの下に新しいイベントを作成します。 空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから FindAzureAnchor() メソッドを割り当てます。

- "DeleteAzureAnchor"をという名前のボタン、イベント トリガーの「ボタンが押されている」と「クリックして」イベント トリガーの下に新しいイベントを作成します。 空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから DeleteAzureAnchor() メソッドを割り当てます。

- 「ローカル アンカーの削除」をという名前のボタン、イベント トリガーの「ボタンが押されている」と「クリックして」イベント トリガーの下に新しいイベントを作成します。 空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから RemoveLocalAnchor() メソッドを割り当てます。

### <a name="build-and-demonstrate-base-application"></a>ビルドし、ベース アプリケーションのデモンストレーション

これで、シーンは Azure 空間アンカーの基本について説明する構成は作成し、Azure 空間アンカーの基本的な動作を示します。 

1. 前のセクションで [ビルド設定] ウィンドウを閉じた場合は、[ファイル] > [ビルド設定] の順に移動して [ビルド設定] ウィンドウを再度開きます。
    ![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)

2. [開いているシーンの追加] ボタンをクリックして、試したいシーンが [ビルド内のシーン] リストに含まれていることを確認します。

3. [ビルド] ボタンを押して、ビルド プロセスを開始します。
    ![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)

4. アプリケーション用の新しいフォルダーを作成して、名前を付けます。 下の図では、アプリケーションを含めるために [App] という名前のフォルダーが作成されています。 [フォルダーの選択] をクリックして、新しく作成したフォルダーへのビルドを開始します。 ビルドが完了したら、Unity の [ビルド設定] ウィンドウを閉じてもかまいません。 
    ![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)

  > 注: ビルドが失敗した場合は、もう一度構成してみるか、Unity を再起動してから再度ビルドしてください。 エラー:CS0246 = tyoe または名前空間の名前が"XX"が見つかりませんでした (が存在することを使用して、ディレクティブまたはアセンブリ参照か)"、をインストールする必要がありますし、 [Windows 10 SDK (10.0.18362.0)。](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) 
  >

5. ビルドが完了したら、新しくビルドされたアプリケーション ファイルが含まれている、新しく作成されたフォルダーを開きます。 [MixedRealityBase.sln] ソリューション (または、プロジェクトの代替名を使用した場合は対応する名前) をダブルクリックして、Visual Studio でソリューション ファイルを開きます。

  > 注:必ず、新しく作成したフォルダー (つまり、前の手順で名前付け規則に従っている場合は、[App] フォルダー) を開いてください。そのフォルダーの外部に同じような名前の .sln ファイルがあり、ビルド フォルダー内の .sln ファイルと混同してはならないためです。 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

  > 注:Visual studio の新しいコンポーネントをインストールする場合、ご協力くださいにすべての前提条件となるコンポーネントがインストールされていることを確認します具体的に["ツールをインストールする ページ。](install-the-tools.md) 

6. USB ケーブルを使って HoloLens 2 を PC に接続します。 レッスンの手順では、HoloLens 2 デバイスでのテスト、デプロイする前提としています、中にすることもできますを展開する、 [HoloLens 2 エミュレーター](using-the-hololens-emulator.md)を作成することも、[サイドローディング用アプリ パッケージ](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. デバイスにビルドする前に、デバイスが開発者モードであることを確認してください。 HoloLens 2 に初めてデプロイする場合は、Visual Studio により、PIN を使用して HoloLens 2 をペアリングするよう求められる場合があります。 開発者モードを有効にするか、Visual Studio とペアリングする必要がある場合は、[こちらの手順](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)に従ってください。

8. [リリース] 構成と [ARM] アーキテクチャを選択して、HoloLens 2 へのビルド用に Visual Studio を構成します。
    ![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)
    
9. 最後に、デバッグを選択して、デバイスにビルド > デバッグなしで開始します。 [デバッグなしで開始] を選択すると、ビルドが成功した時点でアプリケーションがデバイスですぐに起動しますが、Visual Studio にデバッグ情報は表示されません。 これは、アプリケーションが停止することなく HoloLens 2 上で実行されている間は、USB ケーブルを取り外すことができることも意味します。 また、[ビルド] > [ソリューションの配置] を選択することで、アプリケーションを自動的に起動せずにデバイスに配置することもできます。
    ![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)
    
10. アプリケーションは、デバイスで実行中は、次の画面に表示される手順。 次の手順に対応するシーン ボタンを押してください。
    
    ![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. Azure の空間アンカー セッションを開始します。
    
    2. キューブは、別の場所に移動します。
    
    3. キューブの位置にある Azure 空間アンカーを保存します。
    
    4. Azure の空間アンカー セッションを停止します。
    
    5. ユーザーがキューブに移動を許可するキューブ上でローカルのアンカーを削除します。
    6. キューブの別の場所に移動します。
    
    7. Azure の空間アンカー セッションを開始します。
    
    8. Azure の空間アンカーを検索します。
    (キューブが元の場所に戻るにはこれで配置することが、アンカーを作成したときに)。
    9. Azure の空間アンカーを削除します。
    
    10. Azure のセッションを停止します。

### <a name="anchoring-an-experience"></a>アンカーのエクスペリエンス

前のセクションでは、空間のアンカーを Azure の基礎について説明しました。 表し、添付のアンカーを持つ親ゲーム オブジェクトを視覚化するキューブを使用しています。 このセクションでは、wiill するは、ParentAnchor オブジェクトの子として配置することによって、エクスペリエンス全体を固定する方法を説明します。 この例では、中に作成された旧暦モジュール アセンブリのデモ アプリを使用しますが[レッスン 6 のベース モジュール](mrlearning-base-ch6.md)します。

1. 旧暦モジュール アセンブリの完全なプレハブを検索し、ドラッグ、階層に AnchorParent の gameobject の子として次の図に示すようにします。

   ![module2chapter1step11](images/module2chapter1step11im.PNG)

2. 次の図に示すように、このような方法をキューブがまだ公開されることでモジュール アセンブリのエクスペリエンスを配置します。 アプリケーションでは、ユーザーは、全体のエクスペリエンスをキューブに移動することによって再配置することができます。 

   ![module2chapter1step12im](images/module2chapter1step12im.PNG)

   > 注:さまざまなユーザー エクスペリエンスのフローを経験を囲む境界ボックスを切り替え、位置と回転ギズモの使用を (この手順で使用)、キューブなどの再配置オブジェクトを使用するボタンの使用など、エクスペリエンスを再配置します。、など。

## <a name="congratulations"></a>結論
このレッスンでは、空間のアンカーを Azure の基礎について説明しました。 このレッスンは、いくつかのボタンを起動し、Azure のセッションを停止するために必要なさまざまな手順の詳細し作成、アップロード、および 1 つのデバイスでの azure のアンカーをダウンロードすることができますを提供します。 次のレッスンでは、アプリケーションの再起動後も、HoloLens の 2 を取得するために Azure のアンカー Id を保存する方法説明します。 シリーズの中には、空間の配置を実現するために複数のデバイス間にアンカー Id を転送する方法についても説明し、最終的に複数のユーザーが共有セッション (近日公開予定のモジュールを共有の一部として。) について説明します

[次のレッスン:ASA Lesson 2](mrlearning-asa-ch2.md)

