---
title: MR Learning ASA モジュール Azure 空間アンカー (HoloLens 2)
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 9f830bc4ead35fd308108051617c61c65d98d451
ms.sourcegitcommit: c0d5c19b756b8e6ff95ea26a4d8d2b3a53878c2e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671965"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Azure 空間アンカーの概要

HoloLens 2 チュートリアルの2番目のモジュールへようこそ。 作業を開始する前に、すべての[前提条件](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens)が満たされていることを確認してください。 最初の[ベースモジュール](mrlearning-base.md)をまだ完了していない場合は、最初にそのモジュールを完了することをお勧めします。 新しい Unity プロジェクトから開始する場合は、[ベースモジュール](mrlearning-base.md)の新しいプロジェクト作成手順に従います。 

## <a name="objectives"></a>目的

* HoloLens 2 を使用した Azure 空間アンカーを使用した開発の基礎について説明します。

* 空間アンカーを作成、アップロード、ダウンロードする

## <a name="instructions"></a>手順

### <a name="downloading-and-importing-assets"></a>アセットのダウンロードとインポート
開始する前に、次のアセットをダウンロードしてインポートします。

[Azure 空間アンカー v 1.1.0](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage)

[MR Base モジュール Asset Pack v1.0](https://github.com/microsoft/MixedRealityLearning/releases/download/1.2/BaseModuleAssets-1.2.unitypackage)

[ASA モジュール Asset Pack v1.0](https://github.com/microsoft/MixedRealityLearning/releases/download/v1/ASAModuleAssets_1.unitypackage)

[Mixed Reality Toolkit 2.0.0 RC1](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1-Refresh.unitypackage)

> 注:Azure 空間アンカーをインポートする具体的な手順については、手順5を参照してください。 MR Base モジュール Asset Pack に関する具体的な手順については、手順6を参照してください。また、Mixed Reality Toolkit (MRKT) の具体的な手順については、手順 3 ~ 4 を参照してください。

1. プロジェクトに新しいシーンを作成します。 シーンフォルダーを右クリックし、[作成]、[シーン] の順にクリックします。 新しいシーンに ASALearningmodule という名前を指定します。

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. [ASALearningmodule] をダブルクリックすると、定義済みの項目の一部が新しいシーンと共に表示されます。 
3. 混合現実開発のシーンを構成します。 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> 注:[Mixed Reality Toolkit] のファイルを選択する必要があるというポップアップが表示されます。 [Ok] をクリックすると、手順 4. が表示されます。

4. MRTK のファイルを選択する場合は、[DefaultMixedRealityToolkitConfigurationProfile] を選択します。

> 注:独自の構成プロファイルがある場合は、それを自由に使用できます。

![module2chapter1step4im](images/module2chapter1step4im.PNG)

これで、シーンが混合現実用に構成されました。 シーンを保存していることを確認します (これを行うには、control/command + S を使用するか、[ファイル] をクリックして、[保存] をクリックします)。 

5. [Azure 空間アンカー](https://github.com/azure/azure-spatial-anchors-samples/releases)をインポートします。 空間アンカーを使用するには、この資産をインポートする必要があります。 上のリンクをクリックし、AzureSpatialAnchors. unitypackage を右クリックします。 [ターゲットに名前を付けて保存] をクリックし、コンピューターに保存します。 

![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

保存した後、Unity に戻り、[アセット] をクリックして、[パッケージのインポート] に移動します。 [カスタムパッケージ] をクリックします。コンピューターのファイルが開きます。 その場合は、Azure 空間アンカーパッケージを保存した場所を見つけて、それを選択します。 [開く] をクリックします。

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

ポップアップが表示され、ツールと設定の一覧が表示され、インポートする内容が尋ねられます。 使用可能な***すべて***のオプションを選択し、[インポート] をクリックします。

![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

> 注:しばらくお待ちください。インポートには数分かかります。 

6. [MR Base module Asset Pack]https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2) をインポートします。 手順 5. と同じように、上のリンクをクリックします。 次に、[BasemoduleAssetsV1 1. unitypackag] を右クリックし、[ターゲットを名前を付けて保存] をクリックして、コンピューターに保存します。

![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

> ヒント:これらのすべての資産を同じフォルダーに保存して、見つけやすく、アクセスしやすいようにします。 すべての問題を把握し、整理することができます。

手順5と同じように、Unity に戻り、[アセット] をクリックして、[インポートパッケージ] にカーソルを合わせます。 [カスタムパッケージ] をクリックします。コンピューターのファイルが再び表示されます。 Base module Asset Pack を格納した場所に移動します。 を選択します。 [開く] をクリックします。

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

> 注:このモジュールの後に必要な資産が増える場合があります。 ここで説明したアセットをインポートするには、次の手順に従います。 

7. 以前のパッケージをインポートする場合と同じ方法を使用して[ASA モジュールパック](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_1.1)をインポートします。

### <a name="configuring-your-scene"></a>シーンの構成

このセクションでは、prefabs とスクリプトをシーンに追加して、アプリケーションでローカルアンカーと Azure 空間アンカーの両方が動作する方法の基礎を示す一連のボタンを作成します。

8. [プロジェクト] タブの [アセット] フォルダーの下で、[ASAmoduleAssets] をクリックします。 選択すると、2つの prefabs が表示されます。ButtonParent および ParentAnchor。

![module2chapter1step7im](images/module2chapter1step7im.PNG)

9. 両方の prefabs をシーンにドラッグします。 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

10. 親アンカーをダブルクリックして選択します。 場合によっては、シーン全体を表示するようにビューを調整する必要があります。 必要に応じてシーンを調整します。

ParentAnchor prefab について理解を深めます。 現在、ParentAnchor という名前のゲームオブジェクトは、デモを目的として色分けされたキューブです。 最終的には、キューブを非表示にして、コンテンツを ParentAnchor の子として配置します。 この事前 fab には、ASA SDK に含まれる AzureSpatialAnchorsDemoWrapper.cs スクリプトと ASAmoduleScript.cs スクリプトが含まれています。このスクリプトは、このモジュールの一部として ParentAnchor オブジェクトに含まれています。 

11. ボタンを構成します。 ButtonParent prefab の下に、ラベル付きのボタンがいくつかあることを確認します。 これらのボタンは、MRTK の PressableButton prefabs から作成されます。 Pressable ボタンを作成する方法の詳細については、「[基本モジュール](mrlearning-base-ch2.md)」を参照してください。 各ボタンに対して、ユーザーが次の一覧に従ってボタンをクリックまたは選択したときにトリガーされるイベントを追加します。 

- StartAzureSession という名前のボタンについては、Click イベントトリガーおよび On Click イベントトリガーの下に新しいイベントを作成します。 ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから StartAzureSession () メソッドを割り当てます。

![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- ボタン名として [StopAzureSession] をクリックし、Click イベントトリガーおよび On Click イベントトリガーの下に新しいイベントを作成します。 ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから StopAzureSession () メソッドを割り当てます。

- [CreateAnchor] という名前のボタンに対して、ボタン押されたイベントトリガーおよび On Click イベントトリガーの下に新しいイベントを作成します。 ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから CreateAzureAnchor () メソッドを割り当てます。

- という名前のボタンについては、アンカーの検索を開始し、ボタン Presse "イベントトリガーと On Click イベントトリガーの下に新しいイベントを作成します。 ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから FindAzureAnchor () メソッドを割り当てます。

- [DeleteAzureAnchor] という名前のボタンに対して、Click イベントトリガーおよび On Click イベントトリガーの下に新しいイベントを作成します。 ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから DeleteAzureAnchor () メソッドを割り当てます。

- [ローカルアンカーの削除] という名前のボタンに対して、Click イベントトリガーおよび On Click イベントトリガーの下に新しいイベントを作成します。 ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから RemoveLocalAnchor () メソッドを割り当てます。

### <a name="build-and-demonstrate-base-application"></a>基本アプリケーションのビルドとデモンストレーション

ここでは、Azure 空間アンカーの基本を示すためにシーンが構成されたので、Azure 空間アンカーの基本的な動作について説明します。 

1. 前のセクションで [ビルド設定] ウィンドウを閉じた場合は、[ファイル] > [ビルド設定] の順に移動して [ビルド設定] ウィンドウを再度開きます。
![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)

2. [開いているシーンを追加] ボタンをクリックして、目的のシーンがビルドリストのシーンにあることを確認します。

3. [ビルド] ボタンを押して、ビルド プロセスを開始します。
![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)

4. アプリケーション用の新しいフォルダーを作成して、名前を付けます。 次の図では、アプリケーションを格納するために、App という名前のフォルダーが作成されています。 [フォルダーの選択] をクリックして、新しく作成したフォルダーへのビルドを開始します。 ビルドが完了したら、Unity の [ビルドの設定] ウィンドウを閉じることができます。 
![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)

  > 注: ビルドが失敗した場合は、もう一度構成してみるか、Unity を再起動してから再度ビルドしてください。 エラー:CS0246 = tyoe または名前空間の名前 "XX" が見つかりませんでした。 using ディレクティブまたはアセンブリ参照が指定されていないことを確認してください。 [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)のインストールが必要になる場合があります。 
  >

5. ビルドが完了したら、新しくビルドされたアプリケーション ファイルが含まれている、新しく作成されたフォルダーを開きます。 "MixedRealityBase ソリューションまたは対応する名前をダブルクリックします。 プロジェクトに代替名を使用して、Visual Studio でソリューションファイルを開く場合。

  > 注:新しく作成したフォルダー (つまり、前の手順の名前付け規則に従っている場合は、アプリフォルダー) を必ず開いてください。これは、ビルドフォルダー内の .sln ファイルと混同しないように、同じ名前の .sln ファイルがそのフォルダー外に存在するためです。 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

> 注:Visual Studio で新しいコンポーネントのインストールを求められた場合は、 [[ツールのインストール] ページ](install-the-tools.md)で、前提条件となるすべてのコンポーネントが特定のコンポーネントとしてインストールされていることを確認してください。 

6. USB ケーブルを使って HoloLens 2 を PC に接続します。 これらのレッスンの手順では、HoloLens 2 デバイスでテストをデプロイすることを想定していますが、 [hololens 2 エミュレーター](using-the-hololens-emulator.md)にデプロイするか、[サイドローディング用のアプリパッケージの](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)作成を選択することもできます。

7. デバイスにビルドする前に、デバイスが開発者モードであることを確認してください。 HoloLens 2 に初めてデプロイする場合は、Visual Studio により、PIN を使用して HoloLens 2 をペアリングするよう求められる場合があります。 開発者モードを有効にする必要がある場合、または Visual Studio と組み合わせて使用する場合は、[次の手順](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)に従います。

8. リリース構成と RM アーキテクチャを選択して、HoloLens 2 にビルドするように Visual Studio を構成します。
![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)
   
9. 最後の手順は、デバッグ > デバッグなしで開始 を選択してデバイスにビルドすることです。 [デバッグなしで開始] を選択すると、Visual Studio に表示されるビルド ithout デバッグ情報が正常に完了した時点で、アプリケーションがすぐにデバイスで開始されます。 これは、アプリケーションが停止することなく HoloLens 2 上で実行されている間は、USB ケーブルを取り外すことができることも意味します。 また、[ビルド > デプロイ] を選択して、アプリケーションを自動的に起動せずにデバイスにデプロイすることもできます。
![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)
   
10. 画面の指示に従います。 デバイスでアプリケーションが実行されている場合は、画面の指示に従います。 次の手順に対応するシーンボタンを押します。

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

1. 次の図に示すように、旧暦モジュールアセンブリの完全な prefab を検索し、AnchorParent のユーザーオブジェクトの子として階層にドラッグします。

![module2chapter1step11](images/module2chapter1step11im.PNG)

2. 次の図に示すように、モジュールのアセンブリエクスペリエンスを配置して、キューブが引き続き公開されるようにします。 アプリケーションでは、ユーザーはキューブを移動することで、エクスペリエンス全体を再配置できます。 

![module2chapter1step12im](images/module2chapter1step12im.PNG)

> 注:エクスペリエンスを再配置するためのさまざまなユーザーエクスペリエンスフローがあります。たとえば、ボタンを使用して、操作を囲む境界ボックスの切り替え、オブジェクトの再配置 (この手順で使用するキューブなど)、位置と回転の使用などがあります。、その他。

## <a name="congratulations"></a>結論
このチュートリアルでは、Azure 空間アンカーの基礎について学習しました。 ここでは、Azure セッションを開始および停止するために必要なさまざまな手順を説明し、1つのデバイスで azure のアンカーを作成、アップロード、ダウンロードするためのボタンをいくつか紹介しました。 次のレッスンでは、アプリケーションを再起動した後でも、Azure anchor Id を HoloLens 2 に保存して取得する方法について説明します。 このシリーズでは、空間アラインメントを実現するために複数のデバイス間でアンカー Id を転送する方法や、マルチユーザー共有セッションについて学習する方法についても説明します。

[次のレッスン:2. Azure Spatial Anchors の保存、取得、および共有](mrlearning-asa-ch2.md)

