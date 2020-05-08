---
title: マルチユーザー機能のチュートリアル - 5. Azure Spatial Anchors の共有エクスペリエンスへの統合
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法を学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: c27ed7327cfe0a61f2b63e309348bdea1a535ea1
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604973"
---
# <a name="4-integrating-azure-spatial-anchors-into-a-shared-experience"></a>4.Azure Spatial Anchors の共有エクスペリエンスへの統合

このチュートリアルでは、Azure Spatial Anchors (ASA) を共有エクスペリエンスに統合する方法を学習します。 ASA により複数のデバイスが現実の世界への共通の参照を持てるようになり、ユーザーは互いの姿をその現実の物理的な位置に見たり、共有エクスペリエンスを同じ場所で見たりすることができるようになります。

## <a name="objectives"></a>目標

* ASA を共有エクスペリエンスに統合し、複数デバイスで位置合わせする
* ASA がローカル共有エクスペリエンスのコンテキストでどのように機能するかについての基本を学ぶ

## <a name="preparing-the-scene"></a>シーンの準備

[Hierarchy]\(ヒエラルキー\) ウィンドウで **SharedPlayground** オブジェクトを展開し、**TableAnchor** オブジェクトを展開してその子オブジェクトを公開します。

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-1.png)

[Project]\(プロジェクト\) ウィンドウで **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.MultiUserCapabilities]**  >  **[Prefabs]\(プレハブ\)** フォルダーに移動して、**Buttons** プレハブを [Hierarchy]\(ヒエラルキー\) ウィンドウの **TableAnchor** 子オブジェクト上にドラッグし、TableAnchor オブジェクトの子としてシーンに追加します。

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a>シーンを操作するためのボタンの構成

このセクションでは一連のボタン イベントを構成して、Azure Spatial Anchors を使用して共有エクスペリエンスでの空間的な位置合わせを実現する方法の基本を示します。

[Hierarchy]\(ヒエラルキー\) ウィンドウで **Button** オブジェクトを展開し、**StartAzureSession** という名前の最初の子ボタン オブジェクトを選択します。

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-1.png)

[Inspector]\(インスペクター\) ウィンドウで **Interactable (Script)** コンポーネントを探し、**OnClick ()** イベントを次のように構成します。

* **"None (Object)"(なし (オブジェクト))** フィールドに、**TableAnchor** オブジェクトを割り当てる
* **[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  > **StartAzureSession ()** 関数を選択する

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-2.png)

[Hierarchy]\(ヒエラルキー\) ウィンドウで **CreateAzureAnchor** という名前の 2 番目の子ボタン オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで **Interactable (Script)** コンポーネントを探して **OnClick ()** イベントを次のように構成します。

* **"None (Object)"(なし (オブジェクト))** フィールドに、**TableAnchor** オブジェクトを割り当てる
* **[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  > **CreateAzureAnchor()** 関数を選択する
* 表示される新しい **"None (Game Object)"(なし (ゲーム オブジェクト))** フィールドに、**TableAnchor** オブジェクトを割り当てる

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-3.png)

[Hierarchy]\(ヒエラルキー\) ウィンドウで **ShareAzureAnchor** という名前の 3 番目の子ボタン オブジェクトを選択して、[Inspector]\(インスペクター\) ウィンドウで **Interactable (Script)** コンポーネントを探して **OnClick ()** イベントを次のように構成します。

* **"None (Object)"(なし (オブジェクト))** フィールドに、**TableAnchor** オブジェクトを割り当てる
* **[No Function]** (関数なし) ドロップダウンから、 **[SharingModuleScript]**  > **ShareAzureAnchor()** 関数を選択する

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-4.png)

[Hierarchy]\(ヒエラルキー\) ウィンドウで **GetAzureAnchor** という名前の 4 番目の子ボタン オブジェクトを選択して、[Inspector]\(インスペクター\) ウィンドウで **Interactable (Script)** コンポーネントを探して **OnClick ()** イベントを次のように構成します:

* **"None (Object)"(なし (オブジェクト))** フィールドに、**TableAnchor** オブジェクトを割り当てる
* **[No Function]** (関数なし) ドロップダウンから、 **[SharingModuleScript]**  > **GetAzureAnchor()** 関数を選択する

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>シーンを Azure リソースに接続する

[Hierarchy]\(ヒエラルキー\) ウィンドウで **SharedPlayground** オブジェクトを展開し、**TableAnchor** オブジェクトを選択します。 [Inspector]\(インスペクター\) ウィンドウで **Spatial Anchor Manager (Script)** コンポーネントを探し、このチュートリアル シリーズの「[前提条件](mrlearning-sharing(photon)-ch1.md#prerequisites)」の部分で作成した Azure Spatial Anchors アカウントからの資格情報を使用して、 **[Credentials]\(資格情報\)** セクションを構成します。

* **"Spatial Anchors Account ID"(Spatial Anchors アカウント ID)** フィールドに、Azure Spatial Anchors アカウントからの**アカウント ID** を貼り付ける
* **"Spatial Anchors Account Key"(Spatial Anchors アカウント キー)** フィールドに、Azure Spatial Anchors アカウントからのプライマリまたはセカンダリ **アクセス キー** を貼り付ける

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-1.png)

**TableAnchor** オブジェクトを選択したまま、[Inspector]\(インスペクター\) ウィンドウですべてのスクリプト コンポーネントが有効になっていることを確認します。

* **Spatial Anchor Manager (Script)** コンポーネントの隣にあるチェックボックスをオンにして有効にする
* **Anchor Module Script (Script)** コンポーネントの隣にあるチェックボックスをオンにして有効にする
* **Sharing Module Script (Script)** コンポーネントの隣にあるチェックボックスをオンにして有効にする

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-2.png)

## <a name="trying-the-experience-with-spatial-alignment"></a>空間的な位置合わせのエクスペリエンスを試す

> [!NOTE]
> Azure Spatial Anchors を Unity で実行することはできません。 そのため、Azure Spatial Anchors の機能をテストするには、最低 2 台の HoloLens デバイスにプロジェクトを配置する必要があります。

Unity プロジェクトをビルドして 2 台の HoloLens デバイスに配置すると、Azure Anchor ID を共有してデバイス間で空間的な位置合わせを実現できます。 これをテストするには、次の手順を実行します。

1. HoloLens デバイス 1 で次のようにします。**アプリケーションを開始する** (Rocket Launcher のインスタンスが作成され、テーブルに配置されます)
2. HoloLens デバイス 2 で次のようにします。**アプリケーションを開始する** (両方のユーザーが Rocket Launcher のあるテーブルを見ることができますが、テーブルは同じ場所には表示されず、ユーザー アバターはユーザーが実際にいるところに表示されません)
3. HoloLens デバイス 1 で次のようにします。 **[Start Azure Session]\(Azure セッションの開始\)** ボタンを押す
4. HoloLens デバイス 1 で次のようにします。 **[Create Azure Anchor]\(Azure Anchor の作成\)** ボタンを押す (TableAnchor オブジェクトの場所にアンカーが作成され、アンカーの情報が Azure リソースに保存されます)。
5. HoloLens デバイス 1 で次のようにします。 **[Share Azure Anchor]\(Azure Anchor の共有\)** ボタンを押す (他のユーザーとアンカー ID がリアルタイムで共有されます)
6. HoloLens デバイス 2 で次のようにします。 **[Start Azure Session]\(Azure セッションの開始\)** ボタンを押す
7. HoloLens デバイス 2 で次のようにします。 **[Get Azure Anchor]\(Azure Anchor の取得\)** を押す (Azure リソースに接続して共有アンカー ID のアンカー情報が取得され、TableAnchor オブジェクトは HoloLens デバイス 1 でアンカーを作成した場所に移動します)

## <a name="congratulations"></a>結論

このチュートリアルでは、Azure の強力な Spatial Anchors を統合して、複数のデバイスを共有エクスペリエンスの中に配置する方法を学習しました。 これでこのチュートリアル シリーズは終了となります。Photon アカウントとアプリケーションを設定し、Photon と PUN を Unity アプリケーションに統合し、ユーザー アバターと共有オブジェクトを構成し、最後に ASA を使用して複数の参加者を配置する方法を学習しました。
