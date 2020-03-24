---
title: マルチユーザー機能のチュートリアル - 1。 Photon Unity Networking の設定
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 94068ff706e0e56ca8ec0f23beaed3a34159b777
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031331"
---
# <a name="1-setting-up-photon-unity-networking"></a>1.Photon Unity Networking の設定

## <a name="overview"></a>概要

このチュートリアルでは、Photon Unity Networking (PUN) を Unity プロジェクトにインポートして共有エクスペリエンスの作成準備をする方法を学習します。 Photon は、Mixed Reality の開発者が共有エクスペリエンスを作成するために使用できるいくつかのネットワーク オプションの 1 つです。 Photon アカウントを作成し、Photon をインポートし、オプションのローカル サーバーを作成する方法について学習します

## <a name="objectives"></a>目標

* Photon アカウントを作成する方法を学習する
* Photon Unity Networking を検出してインポートする方法を学習する
* ローカル Photon サーバーを設定する

## <a name="prerequisites"></a>前提条件

>[!TIP]
>[入門チュートリアル](mrlearning-base.md)と [Azure Spatial Anchors の入門チュートリアル](mrlearning-asa-ch1.md)のチュートリアル シリーズをまだ完了していない場合は、まずこれらのチュートリアルを完了することをお勧めします。

* 正しい[ツールがインストールされている](install-the-tools.md)構成済みの Windows 10 PC
* Windows 10 SDK 10.0.18362.0 以降
* 基本的な C# プログラミング能力
* [開発用に構成された](using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス

>[!IMPORTANT]
> このチュートリアル シリーズで推奨されている Unity バージョンは Unity 2019.2.X です。 これは、上のリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。

## <a name="setting-up-photon"></a>Photon の設定

1. [Photon](https://dashboard.photonengine.com//Account/SignUp) アカウントを設定します。 [こちらのリンク](https://dashboard.photonengine.com//Account/SignUp)をクリックして、Photon のサインアップ ページに移動します。 サインアップ ページの指示に従って、アカウントを作成します。

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. [Create a New App]\(新しいアプリの作成\) ボタンをクリックして、アプリケーション ID を作成します。

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. [Photon Type]\(Photon の種類\) の下のドロップダウン メニューから [Photon PUN] を選択します。 次に、それに名前を付けます。 この例では、HoloLensPhotonProject という名前を付けました。 完了したら、[Create]\(作成\) ボタンをクリックします。

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. アプリケーションのページに戻ります。次の画像のように表示されます。 アプリケーション ID をクリックしてコピーします。 すぐにアクセスできる任意の場所に貼り付けます。  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. 新しい Unity プロジェクトを作成し、HLSharingProject という名前を付けます。 新しい Unity プロジェクトを作成する方法については、[ベース モジュールの "Unity プロジェクトの作成" に関するセクション](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)を参照してください。 

6. プロジェクトを読み込んだら、次の図に示すように、[Assets Store]\(アセット ストア\) タブをクリックします。 次に、以下の図で強調表示されている検索ボックスに「PUN」と入力し、検索結果から [Photon PUN 2 - FREE] アセットを選択します。

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. [Download]\(ダウンロード\) と [Import]\(インポート\) ボタンを押して、このアセットをダウンロードしてインポートします。

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Photon がインポート プロセスを完了すると、PUN ウィザードが表示されます。 手順 4 のアプリケーション ID (クリップボードにある) を [AppID] ボックスに貼り付けて、[Setup Project]\(プロジェクトの設定\) ボタンを押します。

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. AppID を正常に追加したら、アセット内で [Photon] -> [PhotonUnityNetworking] -> [Resources]\(リソース\) -> [PhotonServerSettings] の順に移動します。 [Use Name Server]\(ネーム サーバーを使用する\) オプションを選択し、固定リージョンを [US]\(米国\)、またはお使いの Photon サービス リージョンに設定します。

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>結論

Photon アカウントを正常に作成し、ローカル Photon サーバーを設定し、PUN を Unity にインポートしました。 次の手順では、プロジェクトを設定し、他のユーザーとの接続を許可して複数のユーザーが作業を表示できるようにします。

[次のチュートリアル: 2.Unity の開発に向けた準備](mrlearning-sharing(photon)-ch2.md)
