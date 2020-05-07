---
title: マルチユーザー機能のチュートリアル - 3. 複数のユーザーの接続
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法を学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: a597aadbddb49fefc824d8c5b5193585fa9476a5
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610932"
---
# <a name="2-connecting-multiple-users"></a>2.複数のユーザーの接続

このチュートリアルでは、ライブ共有エクスペリエンスの一部として複数のユーザーを接続する方法を学習します。 チュートリアルを終えるときには、複数のデバイスでアプリケーションを実行して、各ユーザーが他のユーザーのアバターの動きをリアルタイムで確認できるようになります。

## <a name="objectives"></a>目標

* 共有エクスペリエンスで複数のユーザーを接続する方法を学習する

## <a name="preparing-the-scene"></a>シーンの準備

このセクションでは、チュートリアルのプレハブをいくつか追加してシーンを準備します。

[Project]\(プロジェクト\) ウィンドウで **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.MultiUserCapabilities]**  >  **[Prefabs]\(プレハブ\)** フォルダーに移動します。 Ctrl ボタンを押しながら **[DebugWindow]** 、 **[NetworkLobby]** 、 **[SharedPlayground]** をクリックして、3 つのプレハブを選択します。

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section1-step1-1.png)

3 つのプレハブを選択したまま、[Hierarchy]\(ヒエラルキー\) ウィンドウにドラッグしてこれらをシーンに追加します。

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a>ユーザー プレハブを作成する

このセクションでは、共有エクスペリエンスでユーザーを表すために使用されるプレハブを作成します。

### <a name="1-create-and-configure-the-user"></a>1.ユーザーの作成と構成

[Hierarchy]\(ヒエラルキー\) ウィンドウで空の領域を右クリックし、 **[Create Empty]\(空のユーザーを作成\)** を選択してシーンに空のオブジェクトを追加し、オブジェクトに「**PhotonUser**」という名前を付けて、次のように構成します。

* [Transform]\(変換\) の **[Position]\(位置\)** が、X = 0、Y = 0、Z = 0 に設定されていることを確認する

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-1.png)

**PhotonUser** オブジェクトを引き続き選択した状態で、[Inspector]\(インスペクター\) ウィンドウの **[Add Component]\(コンポーネントの追加\)** ボタンを使用して **Photon User (Script)** コンポーネントを PhotonUser オブジェクトに追加します。

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-2.png)

[Inspector]\(インスペクター\) ウィンドウで、 **[Add Component]\(コンポーネントの追加\)** ボタンを使用して PhotonUser オブジェクトに **Generic Net Sync (Script)** コンポーネントを追加し、次のように構成します。

* **[Is User]\(ユーザーである\)** チェックボックスをオンにする

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-3.png)

[Inspector]\(インスペクター\) ウィンドウで、 **[Add Component]\(コンポーネントの追加\)** ボタンを使用して PhotonUser オブジェクトに **Photon View (Script)** コンポーネントを追加し、次のように構成します。

* **"Observed Components"(観察されるコンポーネント)** フィールドに、Generic Net Sync (Script) コンポーネントを割り当てる

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-4.png)

### <a name="2-create-the-avatar"></a>2.アバターを作成する

[Hierarchy]\(ヒエラルキー\) ウィンドウで、**PhotonUser** オブジェクトを右クリックして **[3D Object]\(3D オブジェクト\)**  >  **[Sphere]\(球体\)** を選択し、PhotonUser オブジェクトの子として球体オブジェクトを作成して次のように構成します。

* [Transform]\(変換\) の **[Position]\(位置\)** が、X = 0、Y = 0、Z = 0 に設定されていることを確認する
* [Transform]\(変換\) の **[Scale]\(スケール\)** を適切なサイズに変更する。例: X = 0.15、Y = 0.15、Z = 0.15

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step2-1.png)

### <a name="3-create-the-prefab"></a>3.プレハブを作成する

[Project]\(プロジェクト\) ウィンドウで **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.MultiUserCapabilities]**  >  **[Resources]\(リソース\)** フォルダーに移動します。

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-1.png)

[Resources]\(リソース\) フォルダーを選択したまま、[Hierarchy]\(ヒエラルキー\) ウィンドウから **PhotonUser** オブジェクトを **[Resources]\(リソース\)** フォルダーに**クリックしてドラッグ**し、PhotonUser オブジェクトをプレハブにします。

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-2.png)

[Hierarchy]\(ヒエラルキー\) ウィンドウで **PhotonUser** オブジェクトを右クリックし、 **[Delete]\(削除\)** を選択してシーンから削除します。

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a>PUN を構成してユーザー プレハブのインスタンスを作成する

このセクションでは、前のセクションで作成した PhotonUser プレハブを使用するようにプロジェクトを構成します。

[Project]\(プロジェクト\) ウィンドウで **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.MultiUserCapabilities]**  >  **[Resources]\(リソース\)** フォルダーに移動します。

[Hierarchy]\(ヒエラルキー\) ウィンドウで **NetworkLobby** オブジェクトを展開して **NetworkRoom** 子オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで **Photon Room (Script)** コンポーネントを探し、次のように構成します。

* **"Photon User Prefab"(Photon ユーザー プレハブ)** フィールドに、[Resources]\(リソース\) フォルダーから **PhotonUser** プレハブを割り当てる

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a>複数のユーザーのエクスペリエンスを試す

Unity プロジェクトをビルドして HoloLens に配置してから Unity に戻り、HoloLens でアプリケーションが実行されている間に [Play]\(再生\) ボタンを押してゲーム モードに入ると、頭 (HoloLens) を動かした時に HoloLens のユーザー アバターが動くのを確認できます。

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section4-step1-1.gif)

> [!TIP]
> HoloLens 2 に Unity プロジェクトをビルドしてデプロイする方法については、「[デバイスへのアプリケーションのビルド](mrlearning-base-ch1.md#build-your-application-to-your-device)」の手順を参照してください。

> [!CAUTION]
> アプリケーションは Photon に接続する必要があるため、お使いのコンピューター/デバイスがインターネットに接続されていることを確認してください。

## <a name="congratulations"></a>結論

複数のユーザーが同じエクスペリエンスに接続して、互いの動きを確認できるようにプロジェクトを構成できました。 次のチュートリアルでは、オブジェクトの動きが複数のデバイスで共有されるようにする機能を実装します。

[次のチュートリアル: 2.オブジェクトの動きの複数のユーザーとの共有](mrlearning-sharing(photon)-ch3.md)
