---
title: ラーニング モジュールを共有 HoloLens 2 を MR
description: このコースでは、HoloLens 2 アプリケーション内でのマルチ ユーザー共有機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 8940de029ef5c67c38f427a238f88fcab527d79d
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327183"
---
# <a name="setting-up-photon"></a>Photon の設定

このレッスンでは、Photon Unity Networking (だじゃれ) を Unity プロジェクトにインポートすると、共有のエクスペリエンスを作成するための準備の方法について説明します。 Photon はいくつかのネットワーク オプション Mixed Reality 開発者が利用できる共有のエクスペリエンスを作成するのです。 私たちは Photon アカウントを作成、インポート Photon、および省略可能なローカル サーバーを作成する方法を説明します

目標:

* Photon アカウントを作成する方法について説明します

* 検索して Photon Unity ネットワークをインポートする方法について説明します

* ローカル Photon サーバーを設定します。

  

### <a name="setting-up-photon"></a>Photon の設定

1. セットアップ、 [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)アカウント。 クリックして、Photon のサインアップ ページに移動します[このリンク](https://dashboard.photonengine.com/en-US/Account/SignUp)します。 サインアップ ページ、アカウントを作成するには、指示に従います。 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

2. 、サインアップ後は、Sdk をクリックします。 そのページが、"server"をクリックし、書かれている、「自己ホスト型です」ことを確認します。 下へスクロールし、"server"次の 2 つ目の図に示すようにをクリックします。

   

   ![Module3Chapter1step2aim](images/module3chapter1step2aim.PNG)

   ![Module3Chapter1step2bim](images/module3chapter1step2bim.PNG)
   
   3. 原因となるテキスト ボックスのラベルの付いた表示「お読みください」 読み取るしてみてください。 完了すると、ダウンロードするには、"downloadSDK"の横にあるリンクをクリックします。


![Module3Chapter1step3im](images/module3chapter1step3im.PNG)

4. ダウンロードが完了したら、フォルダーをダブルクリックします。  エクスプ ローラーを開くと、SDK のフォルダーを公開、したら、SDK フォルダーをコピーします。
   
   - Windows の c: ドライブに移動し、「サーバーです」と呼ばれる新しいフォルダーを作成する次の手順になります
   
   ![Module3Chapter1step4aim](images/module3chapter1step4aim.PNG)
   
   - 今すぐ、フォルダーを開き、先ほどコピーした SDK のフォルダーを貼り付けます。
   
   ![Module3Chapter1step4bim](images/module3chapter1step4bim.PNG)
   
5. SDK フォルダーを開きますが完了すると、「展開、」"bin_Win64"しに移動し、「photon コントロール」をダブルクリックします


![Module3Chapter1step5im](images/module3chapter1step5im.PNG)

> 注:IP アドレスについてご質問またはその他同様の質問がある場合は、ツールバーで、情報の大部分を検索し、(次の図に示すように) とにします。
>
> ![Module3Chapter1noteim](images/module3chapter1noteim.PNG)

6. サーバーを設定すると、開始されたが、Photon web サイトに戻ると署名されても確認します (またはない場合にもう一度サインイン)。(次の図の右上隅でボックス化された) プロファイル アイコンをクリックし、「アプリケーションです。」を選択します。
   

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

7. アプリケーション ID を作成するには、「新しいアプリの作成」ボタンをクリックします。

   ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

   - 「Photon の種類」の下のドロップダウン メニューから「Photon だじゃれ」を選択します。 名前、この例では、"HoloLensPhotonProject"という 完了すると、[作成] ボタンをクリックします。

   ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

8. 完了すると、アプリケーション ページに戻るし、次の図のような画面を表示する必要があります。 アプリケーション ID をクリックし、それをコピーします。 貼り付けがどこかに簡単にアクセスすることができます。  
   

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

9. 新しい unity プロジェクトを作成し、"HLSharingProject"という名前を付けます 新しい Unity プロジェクトを作成する方法についてを参照してください[「Unity プロジェクトの作成」セクションのベース モジュールの](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)します。 


10. プロジェクトが読み込まれたらは、次の図に示すように、「資産ストア」タブをクリックします。 次に、次の図で強調表示されている検索ボックスに「から」を入力し、検索結果から「Photon だじゃれ 2 無料」の資産を選択します。 

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)
    
    11. ダウンロードし、[ダウンロード] と [インポート] ボタンを押してこのアセットをインポートします。
    
    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

## <a name="congratulations"></a>結論

Photon アカウントを作成して、ローカル Photon サーバーをセットアップ、およびだじゃれを Unity にインポートが正常が。 次の手順では、プロジェクトを設定して、複数のユーザーは、作業内容を確認できるように他のユーザーとの接続を許可します。 

[次のレッスン:Sharing(Photon) レッスン 2](mrlearning-sharing(photon)-ch2.md)

