---
title: MR Learning ASA モジュール HoloLens 2 での Azure 空間アンカー
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: c120d22f955d366042bbcb9ac73eaa4f13dc20e9
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415271"
---
# <a name="getting-started-with-azure-spatial-anchors-on-hololens-2"></a>HoloLens 2 空間アンカーを Azure の概要

2 番目のモジュールの HoloLens 2 のチュートリアルへようこそ。 始める前に、必ずすべての[の前提条件](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens)が完了します。 まず、完了していない場合[ベース モジュール](mrlearning-base.md)モジュールを最初に完了することを勧めします。 新しい Unity プロジェクトから開始する場合は 新しいプロジェクトの作成手順に従ってください、[ベース モジュール](mrlearning-base.md)します。 

## <a name="objectives"></a>目標

* HoloLens 2 Azure 空間アンカーを使用した開発の基礎を学習します。

* 作成、アップロード、および空間アンカーのダウンロード

  

## <a name="instructions"></a>手順

### <a name="downloading-and-importing-assets"></a>ダウンロードとアセットのインポート
始める前に、ダウンロードし、次のアセットをインポートします。

[Azure Spatial Anchors](https://github.com/azure/azure-spatial-anchors-samples/releases)

[資産パックの MR ベース モジュール](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)

[ASA モジュール資産パック](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_B2)

[Mixed Reality ツールキット](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

> 注:Azure 空間アンカー、MR ベース モジュール資産パックの詳細については、手順 6、および Mixed Reality ツールキット (MRKT) で、手順 3 ~ 4 具体的な手順についてをインポートする方法の具体的な手順については、手順 5 を参照してください。

1. プロジェクトに新しいシーンを作成します。 シーンのフォルダーを右クリックして、シーン"作成、 をクリックします。 新しいシーン ASALearningmodule の名前を付けます。

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. 新しいシーンと共に表示されるいくつか事前定義された項目を表示する ASALearningmodule をダブルクリックします。 
3. 複合現実の開発のシーンを構成します。 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> 注:示すポップアップが表示されます、「ファイルは Mixed Reality ツールキットを選択する必要があります」します。 [Ok] をクリックすると、手順 4 に表示されます。

4. ときに、MRTK のファイルを選択すると、選択、DefaultMixedRealityToolkitConfigurationProfile。

   > 注:独自の構成プロファイルを用意する場合は、代わりに使用するかまいません。

![module2chapter1step4im](images/module2chapter1step4im.PNG)

シーンを複合現実用に構成されました。 シーンを保存するかどうかを確認 (どちらのコントロールでそれを行うコマンド + S またはファイルをクリックし、クリックして/保存時に)。 

5. インポート、 [Azure 空間アンカー](https://github.com/azure/azure-spatial-anchors-samples/releases)します。 空間アンカーを使用するには、このアセットをインポートする必要があります。 上記のリンクをクリックし、AzureSpatialAnchors.unitypackage を右クリックします。 [ターゲットの名前を付けて保存] をクリックし、コンピューターに保存します。 

   ![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

   保存すると後、は、Unity に戻り、資産をクリックします。、パッケージのインポートに移動します。 カスタム パッケージをクリックしてください.コンピューターのファイルが開きます。 場合の操作を行いますが、Azure 空間アンカー パッケージを保存した検索しを選択します。 [開く] をクリックします。

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   Providingg 一連のツールおよび設定、およびインポートするように求めるポップアップが表示されます。 選択***すべて***使用可能なオプションのインポート をクリックします。

   ![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

   > 注:患者をすると、インポートするまで数分がかかります。 

   6. インポート[MR ベース モジュール資産パック](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)[次へ]。 はるか手順 5 のような場合は、上記のリンクをクリックします。 BasemoduleAssetsV1 1.unitypackag を右クリックし、ターゲットとして保存 をクリックし、コンピューターに保存します。

   ![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

   > ヒント:簡単に見つけにアクセスできるように、同じフォルダーにこれらすべての資産を保存します。 便利で、構成されたすべてのものを保持します。

   手順 5 と同じようを Unity に、資産、 をクリックしてパッケージのインポートを合わせます。 カスタム パッケージをクリックします。コンピューターのファイルが再び表示されます。 資産パックのベース モジュールを格納した場所に移動します。 選択します。 [開く] をクリックします。

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   > 注:このモジュールで後で必要な複数のアセットである可能性があります。 この時点で説明されているすべてのアセットをインポートする次の手順に従います。 
                                                                                                                                                                                                                    
7. 前のパッケージのインポートと同じアプローチを使用して ASA モジュールの ack をインポートします。

### <a name="configuring-your-scene"></a>シーンの構成

このセクションで、シーンの一連のアプリケーションでのローカルのアンカーと空間アンカーを Azure の両方の動作方法の基礎を説明するボタンを作成するにプレハブとスクリプトは追加します。

7. [プロジェクト] タブの Assets フォルダーの下にある ASAmoduleAssets をクリックします。 選択すると、2 つのプレハブが表示されます。ButtonParent ParentAnchor.

![module2chapter1step7im](images/module2chapter1step7im.PNG)

8. 両方のプレハブをシーンにドラッグします。 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

9. 親のアンカーをダブルクリックします。 シーン全体を表示する表示を調整する必要があります。 必要に応じて、シーンを調整します。

    ParentAnchor プレハブを理解します。 現在、ParentAnchor、という名前のゲーム オブジェクトは、デモンストレーション用の立方体です。 ここでは最終的には、'、ll、キューブを非表示にして、ParentAnchor の子として、コンテンツを配置します。 このプレハブには、(ASA SDK に含まれる) AzureSpatialAnchorsDemoWrapper.cs スクリプト、および ParentAnchor オブジェクトには、このモジュールの一部として含まれる、ASAmoduleScript.cs スクリプトが含まれます。 

10. ボタンを構成します。 ParentAnchor プレハブを下には、いくつかのラベルの付いたボタンに注目してください。 これらのボタンは、MRTK の PressableButton のプレハブから作成されます。 Pressable ボタンを作成する方法について説明します、[ベース モジュール](mrlearning-base-ch2.md)します。 各ボタンを押すか、以下の一覧に従ってボタンを選択したときにトリガーされるイベントを追加します。 

- 名前付き、StartAzureSession、ボタンのクリックしてイベント トリガーと同様に、押された状態のイベント トリガーの下に新しいイベントを作成します。 空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから StartAzureSession() メソッドを割り当てます。

  ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

  ![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

  ![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- ボタン名、StopAzureSession、クリックしてイベント トリガーと同様に、押された状態のイベント トリガーの下に新しいイベントを作成します。 空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから StopAzureSession() メソッドを割り当てます。

- 名前付き、CreateAnchor、ボタンのクリックしてイベント トリガーと同様に、押された状態のイベント トリガーの下に新しいイベントを作成します。 空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから CreateAzureAnchor() メソッドを割り当てます。

- イベント トリガーの起動お探しのアンカーをという名前のボタンのボタン Presse の下に新しいイベントの作成"だけでなく、イベント トリガーのをクリックします。 空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから FindAzureAnchor() メソッドを割り当てます。

- 名前付き、DeleteAzureAnchor、ボタンのクリックしてイベント トリガーと同様に、押された状態のイベント トリガーの下に新しいイベントを作成します。 空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから DeleteAzureAnchor() メソッドを割り当てます。

- 名前付き、ローカルのアンカーの削除 ボタンのクリックしてイベント トリガーと同様に、押された状態のイベント トリガーの下に新しいイベントを作成します。 空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから RemoveLocalAnchor() メソッドを割り当てます。

### <a name="build-and-demonstrate-base-application"></a>ビルドし、ベースのアプリケーションのデモンストレーション

これで、シーンは Azure 空間アンカーの基本について説明する構成は作成し、Azure 空間アンカーの基本的な動作を示します。 

1. 前のセクションで [ビルド設定] ウィンドウを閉じた場合は、[ファイル] > [ビルド設定] の順に移動して [ビルド設定] ウィンドウを再度開きます。
    ![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)

2. 試したいシーンが開いているシーンの追加 ボタンをクリックしてビルド リスト内のシーンでは確認してください。

3. [ビルド] ボタンを押して、ビルド プロセスを開始します。
    ![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)

4. アプリケーション用の新しいフォルダーを作成して、名前を付けます。 以下の図では、アプリの名前のフォルダーをアプリケーションを含めることが作成されました。 新しく作成したフォルダーにビルドを開始するには、[フォルダーの選択] をクリックします。 Unity でビルドが完了すると、ビルド設定を閉じることがあります"ウィンドウです。 
    ![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)

  > 注: ビルドが失敗した場合は、もう一度構成してみるか、Unity を再起動してから再度ビルドしてください。 エラー:CS0246 = tyoe または名前空間の名前が"XX"が見つかりませんでした (が存在することを使用して、ディレクティブまたはアセンブリ参照か?)。 インストールする必要があります[Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) 
  >

5. ビルドが完了したら、新しくビルドされたアプリケーション ファイルが含まれている、新しく作成されたフォルダーを開きます。 The"MixedRealityBase.sln ソリューションまたは対応する名前をダブルクリックします。 場合は、プロジェクトの代替名を使用した Visual Studio でソリューション ファイルを開きます。

  > 注:開いて、新しく作成されたフォルダー (つまり、アプリ フォルダー、ビルド フォルダー内の .sln ファイルと混同しないように、そのフォルダーの外部で同様に名前付きの .sln ファイルがあるため、前の手順から名前付け規則に従う場合。 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

  > 注:Visual Studio の新しいコンポーネントをインストールする場合、ご協力くださいにすべての前提条件となるコンポーネントがインストールされていることを確認します具体的に["ツールをインストールする ページ。](install-the-tools.md) 

6. USB ケーブルを使って HoloLens 2 を PC に接続します。 レッスンの手順では、HoloLens 2 デバイスでのテスト、デプロイする前提としています、中にすることもできますを展開する、 [HoloLens 2 エミュレーター](using-the-hololens-emulator.md)を作成することも、[サイドローディング用アプリ パッケージ](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. デバイスにビルドする前に、デバイスが開発者モードであることを確認してください。 HoloLens 2 に初めてデプロイする場合は、Visual Studio により、PIN を使用して HoloLens 2 をペアリングするよう求められる場合があります。 次の[手順](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)開発者モードを有効にするか、Visual Studio とペアリングする必要がある場合。

8. リリース構成と、"RM"のアーキテクチャを選択して、HoloLens 2 を構築するための Visual Studio を構成します。
    ![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)
   
9. 最後に、デバッグを選択して、デバイスにビルド > デバッグなしで開始します。 デバッグなしの開始 を選択するとすぐに Visual Studio に表示されているビルドが成功した ithout デバッグ情報を基に、デバイスで開始するアプリケーション。 これは、アプリケーションが停止することなく HoloLens 2 上で実行されている間は、USB ケーブルを取り外すことができることも意味します。 ビルドを選択することも可能性があります。 > を自動的に起動するアプリケーションをしなくても、デバイスに展開するには、ソリューションの配置。
    ![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)
    
10. では、指示に従います。 次のアプリケーションがデバイスで実行しているときに、画面に表示される手順。 次の手順に対応するシーン ボタンを押します。
    
    ![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. 空間アンカー セッションを開始します。
    
    2. キューブは、別の場所に移動します。
    
    3. キューブの位置にある Azure 空間アンカーを保存します。
    
    4. Azure の空間アンカー セッションを停止します。
    
    5. ユーザーがキューブに移動を許可するキューブ上でローカルのアンカーを削除します。
    6. キューブの別の場所に移動します。
    
    7. Azure の空間アンカー セッションを開始します。
    
    8. Azure 空間 aachors を検索します。 
    
    e を」に戻ってください元の場所を配置、アンカーを作成したときに) します。
    9. Azure の空間アンカーを削除します。
    
    10. Azure のセッションを停止します。

### <a name="anchoring-an-experience"></a>アンカーのエクスペリエンス

前のセクションでは、空間のアンカーを Azure の基礎について説明しました。 表し、添付のアンカーを持つ親ゲーム オブジェクトを視覚化するキューブを使用しています。 このセクションでは、ParentAnchor オブジェクトの子として配置することによって、エクスペリエンス全体を固定する方法について説明します。 この例では、使用旧暦モジュールの中に作成されたアセンブリのデモ アプリケーション[レッスン 6 のベース モジュール](mrlearning-base-ch6.md)します。

1. 旧暦モジュール アセンブリの完全なのプレハブを検索し、ドラッグ、階層に AnchorParent gameobject の子として次の図に示すようにします。

   ![module2chapter1step11](images/module2chapter1step11im.PNG)

2. 次の図に示すように、キューブがまだ公開されているように、モジュール アセンブリの位置が発生します。 アプリケーションでは、ユーザーは、全体のエクスペリエンスをキューブに移動することによって再配置することができます。 

   ![module2chapter1step12im](images/module2chapter1step12im.PNG)

   > 注:さまざまなユーザー エクスペリエンスのフローを経験を囲む境界ボックスを切り替え、位置と回転ギズモの使用を (この手順で使用)、キューブなどの再配置オブジェクトを使用するボタンの使用など、エクスペリエンスを再配置します。、など。

## <a name="congratulations"></a>結論
このレッスンでは、空間のアンカーを Azure の基礎について説明しました。 このレッスンでは、開始し Azure のセッションを停止し、作成、アップロード、および 1 つのデバイスでの azure のアンカーをダウンロードするためのさまざまな手順を調査できるいくつかのボタンが用意されています。 次のレッスンでは、アプリケーションの再起動後も、HoloLens の 2 を取得するために Azure のアンカー Id を保存する方法説明します。 シリーズの中には、空間の配置を実現し、複数のユーザーが共有セッション (近日公開予定のモジュールを共有の一部として。) について説明します、複数のデバイス間でアンカー Id を転送する方法も学習は

[次のレッスン:ASA Lesson 2](mrlearning-asa-ch2.md)

