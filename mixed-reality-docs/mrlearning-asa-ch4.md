---
title: MR Learning ASA モジュール Azure 空間アンカー (HoloLens 2)
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 141aa90f2bf5d90527a0fe1e6a812c1ce56bd0eb
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437793"
---
# <a name="photon-correct-me-if-im-wrong"></a>Photon (間違っている場合は修正)

このレッスンでは、 

事項

* 詳細については、こちらを参照してください。 __ __ を参照してください。

* 詳細については、こちらを参照してください。 __ を参照してください。 __ __。

  

## <a name="instructions"></a>手順

### <a name="setting-up-photon"></a>Photon の設定

1. [Photon](https://dashboard.photonengine.com//Account/SignUp)アカウントを設定します。 これを行うには、電子メールを送信し、いくつかの検証手順を実行します。
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. サインアップしたら、[Sdk] をクリックします。 このページが表示されたら、[サーバー] をクリックし、"自己ホスト型" と表示されていることを確認します。 下にスクロールし、次の2番目の図に示すように、[サーバー] をクリックします。

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. これにより、テキストボックスに "read me" というラベルが付けられます。 こちらからお読みください。 完了したら、"downloadSDK" の横にあるリンクをクリックしてダウンロードします。


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. ダウンロードが完了したら、フォルダーをダブルクリックします。  ファイルエクスプローラーで SDK フォルダーが表示されたら、SDK フォルダーをコピーします。
   
   - 次の手順では、windows C: ドライブにアクセスし、"server" という名前の新しいフォルダーを作成します。
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - ここで、フォルダーを開き、先ほどコピーした SDK フォルダーを貼り付けます。
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. この操作が完了したら、SDK フォルダーを開き、[deploy]、[bin_Win64] の順に選択し、[photon control] をダブルクリックします。


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> 注: IP アドレスについて質問がある場合、またはその他の同様の質問がある場合は、ツールバーでほとんどの情報を確認できます (次の図を参照)。
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. サーバーがセットアップされ、開始されたので、Photon の web サイトに戻り、プロファイルアイコン (下の図のボックス) をクリックして、[your applications] \ (アプリケーション \) を選択します。
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. [新しいアプリの作成] ボタンをクリックして、アプリケーション ID を作成します。

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - [Photon type] の下にあるドロップダウンメニューから [Photon RUN] を選択します。 次に、名前 (覚えているもの) を指定します。 この例では、"HoloLensPhotonProject" という名前が付けられています。 完了したら、[作成] をクリックします。

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. この操作が完了すると、アプリケーションのページに戻り、次の図のような結果が表示されます。 アプリ ID をクリックしてコピーします。 貼り付けは、簡単にアクセスできる任意の場所にあります。  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. 新しい unity プロジェクトを作成します。 Unity Hub を開き、[new] \ (新規 \) をクリックします。 "HLSharingProject" という名前を指定します。 [作成] をクリックします。 

   > 注: コンピューターの速度によっては、読み込みに最大2分かかることがあります。

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> 注: [場所] オプションを変更して、コンピューターにプロジェクトを保存する場所を選択します。 覚えやすい場所に保存して、簡単にアクセスできます。

10. プロジェクトが読み込まれたら、[assets ストア] をクリックします。 次に、下の画像に示されている検索ボックスに「さしあたっ」と入力し、"Photon さしあたっ-2 FREE" 資産を選択します。 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. ダウンロードしてインポートします。
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a>**Unity プロジェクトの設定** 

11. Unity で Photon を設定するために必要な新しい資産をダウンロードするには、ここをクリック[してください。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)

12. Unity で、[アセット] メニューをクリックし、[アセットのインポート] を選択して、[カスタムアセット] をクリックします。

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. 手順 1. で指定したリンクからダウンロードした Unity パッケージを選択します。 Unity に [インポート] ボタンが表示されたら、それをクリックします。

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> メモ: パッケージをダウンロードした場所はどこにありますか。 上の図では、パッケージを検索する場所はされるません。

14. 新しいシーンを作成します (これを行うには、control/command + N を使用するか、[ファイル] をクリックして [新しいシーン] を選択します)。 シーンを "HLSharedProjectMain" として保存します。

> 注: 次の図のようなポップアップが表示される場合があります。 ここでは、[いいえ] をクリックします。
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. "Mixed Reality Toolkit" で、[シーンに追加して構成する] をクリックします。

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. この処理が完了すると、新しい構成ファイルが表示され、プロファイルをカスタマイズするためのオプションが表示されます。 [コピーとカスタマイズ] をクリックします。

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. 下にスクロールし、[診断システムを有効にする] チェックボックスをオフにします。 これにより、このプロジェクトのセットアップが簡単になります。

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. ビルド設定を開きます (ctrl + shift + B)。 このプログラムは、現在、"PC, Mac および Linux スタンドアロン" プラットフォームで設定されていることに注意してください。 このプロジェクトの場合は、プラットフォームを "ユニバーサル windows プラットフォーム" に設定します。 それを選択し、[switch platform] をクリックします。

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. 完了したら、[open シーンの追加] というボックスをクリックします。 次に、[インスペクター] パネルにアクセスし、[virtual reality がサポートされています] の右側にあるチェックボックスがオンになっていることを確認します (下図を参照)。 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> 注: [シーン/HLSharedProjectMain] の横にあるチェックボックスもオンになっていることを確認します。

20. [インスペクター] パネルの [発行の設定] で、[機能] まで下にスクロールし、次のチェックボックスのみがマークされていることを確認します。

- インターネットクライアント
- インターネットクライアントサーバー
- プライベートネットワーククライアントサーバー
- カメラ/webcam
- マイク

21. 手順12と同じように、次の手順では、"レッスン 2" という名前の別のカスタムパッケージをインポートします。このパッケージはダウンロードできます (こちらを参照)。[レッスン 2. unitypackage link here]そのパッケージをインポートします。

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. 次に、[プロジェクト] パネルで、"prefabs" フォルダーにアクセスします。これは、次のいくつかの手順で、いくつかの prefabs をシーンに実装するためです。 "Prefabs" フォルダーで、prefab "DebugWindow" をクリックして階層にドラッグします。 完了したら、プロジェクトを保存します ([ファイル]、[保存]、または [コントロール + S] をクリックします)。

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> 注: prefab をクリックするとポップアップが表示され、TMP Essentials について質問されることがあります。 必要に応じて [Import TMP Essentials] をクリックします。
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a>**複数のユーザーの接続**

23. 手順 22. と同じように、[プロジェクト] パネルの "prefabs" フォルダーで、次の手順では、"NetworkLobby" の事前 fab を階層にドラッグアンドドロップします。 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. 親 prefab "NetworkLobby" を開くと、子 prefab "Networklobby" が表示されます。 選択した状態で、[インスペクター] パネルにアクセスし、[コンポーネントの追加] をクリックします。 "PhotonView" を検索し、コンポーネントを追加します。

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. 階層内に新しい空のゲームオブジェクトを作成します (階層内を右クリックし、[空] を選択します)。 位置が x = 0、y = 0、z = 0 に設定されていることを確認し、オブジェクトに "PhotonUser" という名前を指定します。

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a>結論



