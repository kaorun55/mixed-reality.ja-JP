---
title: HoloLens 2 用 MR Learning 共有モジュール
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 46c32abaf45623b7ccba90f257959e4ef4f8e1b5
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485643"
---
#  <a name="1-setting-up-photon-unity-networking"></a>1. Photon Unity ネットワークのセットアップ

このチュートリアルでは、Photon Unity ネットワーク (さしあたっ) を Unity プロジェクトにインポートして、共有エクスペリエンスを作成する準備をする方法について説明します。 Photon は、混合環境の開発者が共有エクスペリエンスを作成するために使用できるいくつかのネットワークオプションの1つです。 ここでは、Photon アカウントを作成し、Photon をインポートして、オプションのローカルサーバーを作成する方法について説明します。

## <a name="objectives"></a>目的

* Photon アカウントを作成する方法について説明します。

* Photon Unity ネットワークを検索してインポートする方法について説明します。

* ローカル Photon サーバーをセットアップする

  

## <a name="setting-up-photon"></a>Photon の設定

1. [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)アカウントを設定します。 [このリンク](https://dashboard.photonengine.com/en-US/Account/SignUp)をクリックして、Photon サインアップページに移動します。 サインアップページの指示に従って、アカウントを作成します。 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. [新しいアプリの作成] ボタンをクリックして、アプリケーション ID を作成します。

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. [Photon Type] の下にあるドロップダウンメニューから [Photon さしあたっ] を選択します。 次に、名前を指定します。 この例では、HoloLensPhotonProject という名前を付けています。 完了したら、[作成] ボタンをクリックします。

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. この操作が完了すると、アプリケーションのページに戻り、次の図のような結果が表示されます。 アプリケーション ID をクリックしてコピーします。 簡単にアクセスできる場所に貼り付けます。  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. 新しい unity プロジェクトを作成し、HLSharingProject という名前を指定します。 新しい Unity プロジェクトを作成する方法については、[ベースモジュール「Unity プロジェクトの作成」セクション](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)を参照してください。 

6. プロジェクトが読み込まれたら、次の図に示すように、[アセットストア] タブをクリックします。 次に、下の画像で強調表示されている検索ボックスで、「さしあたっ」と入力し、検索結果から Photon さしあたっ 2 FREE "資産を選択します。 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. [ダウンロード] と [インポート] ボタンを押して、この資産をダウンロードしてインポートします。

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Photon がインポートプロセスを完了すると、さしあたっウィザードが表示されます。 手順 4. のアプリケーション ID (クリップボード内にある必要があります) を取得し、[AppID] ボックスに貼り付けて、[Setup Project] ボタンを押します。 
![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. AppID が正常に追加されたら、Photon-> PhotonUnityNetworking-> Resources-> PhotonServerSettings in Assets に移動します。 [ネームサーバーを使用する] オプションを選択し、[固定] リージョンを [US] または [photon service region] に設定します。

![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>結論

Photon アカウントの作成、ローカル Photon サーバーの設定、Unity へのさしあたっのインポートが正常に完了しました。 次の手順では、プロジェクトを設定し、他のユーザーとの接続を許可して、複数のユーザーが自分の作業を確認できるようにします。 

[次のチュートリアル:2. Unity の開発に向けた準備](mrlearning-sharing(photon)-ch2.md)

