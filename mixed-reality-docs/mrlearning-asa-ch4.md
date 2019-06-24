---
title: MR Learning ASA モジュール HoloLens 2 Azure 空間アンカー
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: b29f27284c352d27fb1d4d4de701a1ebc2a7cd1c
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328092"
---
# <a name="photon-correct-me-if-im-wrong"></a>Photon (適切な me 私は正しくない場合)

このレッスンで 

目標:

* について説明します _ _ _ する方法

* について説明します _ _ _ する方法

  

## <a name="instructions"></a>手順

### <a name="setting-up-photon"></a>Photon の設定

1. セットアップ、 [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)アカウント。 これは、電子メールを置き換えると、いくつかの検証手順をで構成されます。
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. 、サインアップ後は、Sdk をクリックします。 そのページが、"server"をクリックし、書かれている、「自己ホスト型です」ことを確認します。 下へスクロールし、"server"次の 2 つ目の図に示すようにをクリックします。

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. 原因となるテキスト ボックスのラベルの付いた表示「お読みください」 読み取るしてみてください。 完了すると、ダウンロードするには、"downloadSDK"の横にあるリンクをクリックします。


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. ダウンロードが完了したら、フォルダーをダブルクリックします。  エクスプ ローラーを開くと、SDK のフォルダーを公開、したら、SDK フォルダーをコピーします。
   
   - Windows の c: ドライブに移動し、「サーバーです」と呼ばれる新しいフォルダーを作成する次の手順になります
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - 今すぐ、フォルダーを開き、先ほどコピーした SDK のフォルダーを貼り付けます。
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. SDK フォルダーを開きますが完了すると、「展開、」"bin_Win64"しに移動し、「photon コントロール」をダブルクリックします


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> 注:IP アドレスについてご質問またはその他同様の質問がある場合は、ツールバーで、情報の大部分を検索し、(次の図に示すように) とにします。
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. サーバーを設定すると、開始されたが、Photon web サイトに戻って「アプリケーションです」を選択してと (次の図でボックス化された) プロファイル アイコンをクリックします
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. アプリケーション ID を作成するには、「新しいアプリの作成」ボタンをクリックします。

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - 「Photon の種類」の下のドロップダウン メニューから [Photon 実行] を選択します 名前を付けます、(ものするには注意してください)。 この例では、という名前に"HoloLensPhotonProject" 完了すると、クリックして「を作成します」

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. 完了すると、アプリケーション ページに戻るし、次の図のような画面を表示する必要があります。 アプリケーション ID をクリックし、それをコピーします。 貼り付けがどこかに簡単にアクセスすることができます。  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. 新しい unity プロジェクトを作成します。 Unity のハブを開き、"new"をクリックしてください "HLSharingProject"という名前を付けます クリックを作成します。 

   > 注:読み込むには、最大 2 分間、コンピューターの速度に基づいてこれかかることができます。

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> 注:"location"オプションを変更することで、コンピューターで、プロジェクトを保存する場所を選択します。 記憶され、簡単にアクセスする場所に保存します。

10. プロジェクトが読み込まれたらを「アセット ストア」をクリックします。 次に、検索ボックスに次の図に示すように、「から」を入力し、「Photon だじゃれ 2 無料」の資産を選択します。 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. ダウンロードしてインポートします。
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a>**Unity プロジェクトの設定** 

11. クリックすると、Unity で Photon を設定するために必要な新しい資産をダウンロード[ここです。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)

12. Unity では、資産 メニューと"資産、import"を選択し、カスタム アセット"をクリックしてください

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. 手順 1. で指定されたリンクからダウンロードした Unity パッケージを選択します。 Unity にインポート ボタンが表示されたら、それをクリックします。

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> 注: 検索の場所にパッケージをダウンロードした場所になります。 上の図は、パッケージをどこを提示していません。

14. 新しいシーンを作成する (これは、コントロールを使用して元に戻す/コマンド + N または"file"をクリックすると、「新しいシーンです。」を選択して)。 シーンを付けて保存"HLSharedProjectMain"

> 注: 次の図のようなポップアップが表示される可能性があります。 ここでは、クリックして"no"です。
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. "Mixed Reality Toolkit"クリック「シーンに追加して構成します」

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. 完了すると、新しい構成ファイルが表示され選択してプロファイルをカスタマイズすること。 「コピーし、カスタマイズ」をクリックします。

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. 下へスクロールし、「診断システムを有効にします。」オフにします。 これは、ため、このプロジェクトをセットアップしやすく、されます。

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. ビルドの設定 (コントロール + shift + B) を開きます。 プログラムが「PC、Mac、Linux のスタンドアロン」プラットフォームで現在設定されていることを確認します。 このプロジェクトで「ユニバーサル windows プラットフォーム」を使用するプラットフォームを設定します。 選択して、「プラットフォームの切り替え」をクリックします。

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. 完了すると、「開いているシーンを追加します。」と書かれたボックスをクリックします。 Inspector パネルに移動し、(下図参照) として「サポートされている仮想現実」の右側にあるチェック ボックスを確認するようになりましたがチェックされます。 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> 注:また、"シーン/HLSharedProjectMain"の横にあるチェック ボックスをチェックすることを確認します。

20. [インスペクター] パネルの「発行の設定」が「機能」までスクロールし、次のチェック ボックスのみがマークされていることを確認します。

- インターネット クライアント
- インターネット クライアント サーバー
- プライベート ネットワーク クライアント サーバー
- カメラ/web カメラ
- マイク

21. 12 の手順と同じように次の手順は [こちら] ダウンロードできます「レッスン 2」と呼ばれる別のカスタム パッケージをインポートすること[lesson2.unitypackage リンクをここに挿入]そのパッケージをインポートします。

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. ここで、プロジェクト パネルで、フォルダーに移動「プレハブ」、いくつかのプレハブをシーンに次の手順で実装されるためです。 「プレハブ」フォルダーにをクリックし、"DebugWindow"階層に、プレハブをドラッグします。 完了すると、プロジェクトを保存します ([] をクリック ファイルを保存して、またはコントロール + S)。

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> 注:TMP Essentials について質問する、プレハブをクリックすると表示されるポップアップ ウィンドウがあります。 これらが必要になります"インポート TMP Essentials をクリックします。
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a>**複数のユーザーを接続します。**

23. プロジェクト パネルで、「プレハブ」フォルダー内の 22 の手順と同様に、次の手順にドラッグ アンド ドロップ"NetworkLobby"プレハブ階層には。 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. "NetworkLobby、"である親プレハブを開くときに子 prefab、"NetworkRoom"が表示されます。 選択されていると、インスペクター パネルに移動し、「コンポーネントを追加します」をクリックしてください "PhotonView"を検索し、コンポーネントを追加します。

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. 階層 (階層し、"empty"内を右クリック) で、新しい空のゲーム オブジェクトを作成します。 位置 x に設定されていることを確認 = 0、y = 0、z = 0 およびオブジェクトの名前を"PhotonUser"。

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a>結論



