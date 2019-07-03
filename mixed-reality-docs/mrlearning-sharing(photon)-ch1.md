---
title: ラーニング モジュールを共有 HoloLens 2 を MR
description: このコースでは、HoloLens 2 アプリケーション内でのマルチ ユーザー共有機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 80cefb36ec1944ec6f537aafcbf4b63f7f812d26
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523291"
---
#  <a name="setting-up-photon-unity-networking"></a>Photon Unity ネットワークを設定

このチュートリアルでは、Photon Unity Networking (だじゃれ) を Unity プロジェクトにインポートすると、共有のエクスペリエンスを作成するために準備する方法について説明します。 Photon はいくつかのネットワーク オプション Mixed Reality 開発者が利用できる共有のエクスペリエンスを作成するのです。 私たちは Photon アカウントを作成、インポート Photon、および省略可能なローカル サーバーを作成する方法を説明します

目標:

* Photon アカウントを作成する方法について説明します

* 検索して Photon Unity ネットワークをインポートする方法について説明します

* ローカル Photon サーバーを設定します。

  

### <a name="setting-up-photon"></a>Photon の設定

1. セットアップ、 [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)アカウント。 クリックして、Photon のサインアップ ページに移動します[このリンク](https://dashboard.photonengine.com/en-US/Account/SignUp)します。 サインアップ ページ、アカウントを作成するには、指示に従います。 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. 新しいアプリのボタンの作成 をクリックして、アプリケーション ID を作成します。

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. Photon だじゃれを Photon の種類の下のドロップダウン メニューから選択します。 名前を付けます。 この例では、という HoloLensPhotonProject します。 完了すると、[作成] ボタンをクリックします。

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. 完了すると、アプリケーション ページに戻るし、次の図のような画面を表示する必要があります。 アプリケーション ID をクリックし、それをコピーします。 貼り付けがどこかに簡単にアクセスすることができます。  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. 新しい unity プロジェクトを作成し、HLSharingProject という名前を付けます。 新しい Unity プロジェクトを作成する方法についてを参照してください[「Unity プロジェクトの作成」セクションのベース モジュールの](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)します。 

6. プロジェクトを読み込んだらは、次の図に示すようにアセット ストア タブをクリックします。 検索結果から資産を次に、次の図で強調表示されている検索ボックスには、だじゃれを入力し、FRE Photon だじゃれ 2 - を選択します"。 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. ダウンロードし、ダウンロードとインポートのボタンを押してこのアセットをインポートします。

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Photon には、インポート プロセスが完了したら、だじゃれウィザードが表示されます。 アプリケーション id (これはクリップボード上にある必要があります) を手順 4. から、AppID ボックスに貼り付けます、セットアップ プロジェクト をクリックします。 
![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. AppID が正常に追加した後には、Photon に移動します。 PhotonUnityNetworking]-> []-> [リソースの資産で PhotonServerSettings]-> [です。 名前のサーバーを使用するオプションを選択し、ご意見の固定のリージョンまたは yourPphoton サービス地域を設定します。

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>結論

Photon アカウントを作成して、ローカル Photon サーバーをセットアップ、およびだじゃれを Unity にインポートが正常が。 次の手順では、プロジェクトを設定して、複数のユーザーは、作業内容を確認できるように他のユーザーとの接続を許可します。 

[次のチュートリアル:Unity の開発の準備](mrlearning-sharing(photon)-ch2.md)

