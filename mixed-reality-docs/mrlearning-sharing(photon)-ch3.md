---
title: マルチユーザー機能のチュートリアル - 4. 複数のユーザーとオブジェクトの移動を共有する
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 41b62eb2d9f400d0af341c9fcce887c72af7a3aa
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610648"
---
# <a name="3-sharing-object-movements-with-multiple-users"></a>3.複数のユーザーとオブジェクトの移動を共有する

このチュートリアルでは、共有エクスペリエンスのすべての参加者が共同作業したり、相互の操作を表示したりできるように、オブジェクトの移動を共有する方法について説明します。

## <a name="objectives"></a>目標

* オブジェクトの移動を共有するようにプロジェクトを構成する
* 基本的なマルチユーザー コラボレーション アプリケーションを構築する方法を学習する

## <a name="preparing-the-scene"></a>シーンの準備

このセクションでは、チュートリアルのプレハブを追加してシーンを準備します。

[Project]\(プロジェクト\) ウィンドウで **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.MultiUserCapabilities]**  >  **[Prefabs]\(プレハブ\)** フォルダーに移動して、**TableAnchor** プレハブを [Hierarchy]\(ヒエラルキー\) ウィンドウの **SharedPlayground** オブジェクト上にドラッグし、SharedPlayground オブジェクトの子としてシーンに追加します。

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a>PUN を構成してオブジェクトのインスタンスを作成する

このセクションでは、前のセクションで作成した RocketLauncher_Complete_Variant プレハブを使うようにプロジェクトを構成して、そのインスタンスを作成する場所を定義します。

[Project]\(プロジェクト\) ウィンドウで **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.MultiUserCapabilities]**  >  **[Resources]\(リソース\)** フォルダーに移動します。

[Hierarchy]\(ヒエラルキー\) ウィンドウで **NetworkLobby** オブジェクトを展開して **NetworkRoom** 子オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで **Photon Room (Script)** コンポーネントを探し、次のように構成します。

* **"Photon User Prefab"(Photon ユーザー プレハブ)** フィールドに、[Resources]\(リソース\) フォルダーから **PhotonUser** プレハブを割り当てる

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-1.png)

**NetworkRoom** 子オブジェクトを選択したまま [Hierarchy]\(ヒエラルキー\) ウィンドウで **TableAnchor** オブジェクトを展開し、[Inspector]\(インスペクター\) ウィンドウで **Photon Room (Script)** コンポーネントを探して次のように構成します。

* **"Rocket Launcher Location"(Rocket Launcher の場所)** フィールドに、[Hierarchy]\(ヒエラルキー\) ウィンドウから **Table** 子オブジェクトを割り当てる

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a>共有オブジェクト移動のエクスペリエンスを試す

Unity プロジェクトをビルドして HoloLens に配置してから Unity に戻り、HoloLens でアプリケーションが実行されている間に [Play]\(再生\) ボタンを押してゲーム モードに入ると、HoloLens でオブジェクトを動かした時に Unity でオブジェクトが移動するのを確認できます。

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section3-step1-1.gif)

## <a name="congratulations"></a>結論

オブジェクトの移動が同期するようにプロジェクトを構成できました。ユーザーがオブジェクトを移動すると、そのオブジェクトの移動が他のユーザーにも表示されます。 次のチュートリアルでは、共有エクスペリエンスを現実世界に収め、ユーザーたちが互いの姿をその現実の物理的な位置に見られるようにしたり、オブジェクトがどのユーザーからも同じ物理的な位置と角度で表示されるようにしたりする機能を実装します。

[次のチュートリアル: 4.Azure Spatial Anchors の共有エクスペリエンスへの統合](mrlearning-sharing(photon)-ch4.md)
