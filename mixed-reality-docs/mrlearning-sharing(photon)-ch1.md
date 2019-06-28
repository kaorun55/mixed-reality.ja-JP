---
title: ラーニング モジュールを共有 HoloLens 2 を MR
description: このコースでは、HoloLens 2 アプリケーション内でのマルチ ユーザー共有機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: f612fa89db1a3f5ed34f6e0bb7062b53780f09b8
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416123"
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



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. アプリケーション ID を作成するには、「新しいアプリの作成」ボタンをクリックします。

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. 「Photon の種類」の下のドロップダウン メニューから「Photon だじゃれ」を選択します。 名前、この例では、"HoloLensPhotonProject"という 完了すると、[作成] ボタンをクリックします。

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. 完了すると、アプリケーション ページに戻るし、次の図のような画面を表示する必要があります。 アプリケーション ID をクリックし、それをコピーします。 貼り付けがどこかに簡単にアクセスすることができます。  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. 新しい unity プロジェクトを作成し、"HLSharingProject"という名前を付けます 新しい Unity プロジェクトを作成する方法についてを参照してください[「Unity プロジェクトの作成」セクションのベース モジュールの](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)します。 

6. プロジェクトが読み込まれたらは、次の図に示すように、「資産ストア」タブをクリックします。 次に、検索ボックスに次の図で強調表示されている、「から」を入力し、検索結果から「Photon だじゃれ 2 - 無料」の資産を選択します。 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. ダウンロードし、[ダウンロード] と [インポート] ボタンを押してこのアセットをインポートします。

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Photon には、インポート プロセスが完了したら、だじゃれウィザードが表示されます。 手順 4 から、アプリケーション id (これはクリップボード上にある必要があります) と、[AppID] ボックスに貼り付けます「セットアップ プロジェクト」ボタンを押します。 
![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. AppID を正常に追加した後は、"Photon"->"PhotonUnityNetworking"に移動]-> [->"PhotonServerSettings"資産を"Resources"。 「名前のサーバーを使用する」オプションを選択し、固定の領域を photon サービス リージョンまたは「弊社」に設定します。

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>結論

Photon アカウントを作成して、ローカル Photon サーバーをセットアップ、およびだじゃれを Unity にインポートが正常が。 次の手順では、プロジェクトを設定して、複数のユーザーは、作業内容を確認できるように他のユーザーとの接続を許可します。 

[次のレッスン:Sharing(Photon) レッスン 2](mrlearning-sharing(photon)-ch2.md)

