---
title: Azure Spatial Anchors チュートリアル - 2. Azure Spatial Anchors の保存、取得、および共有
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 36f25229469e848a3f0612a5971cc8e9381262f5
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362009"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2.Azure Spatial Anchors の保存、取得、および共有

このチュートリアルでは、HoloLens 2 のストレージにアンカー ID を保存することにより、複数のアプリ セッションにわたって Azure Spatial Anchors を保存する方法について学習します。 また、このアンカー ID を他のデバイスと共有して、複数デバイスのアンカーの位置合わせ行う方法についても学習します。

## <a name="objectives"></a>目標

* アプリ セッション間で永続化するために、Azure Spatial Anchor ID を HoloLens 2 ローカル ディスクに保存したり、そこから取得したりする方法について学習します。
* マルチデバイス シナリオで、Azure Spatial Anchor ID をユーザー間で共有する方法について学習します

## <a name="preparing-the-scene"></a>シーンの準備

[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.AzureSpatialAnchors]**  >  **[Prefabs]\(プレハブ\)** フォルダーに移動します。 Ctrl ボタンを押したまま、 **[ButtonParent_SaveAnchorId]** および **[ButtonParent_ShareAnchorId]** をクリックして 2 つのプレハブを選択し、これらを [Hierarchy]\(階層\) ウィンドウにドラッグしてシーンに追加します。

![mrlearning-asa](images/mrlearning-asa/tutorial2-section1-step1-1.png)

## <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>アプリ セッション間で Azure Anchors を永続化する - アンカー ID をディスクに保存する
<!-- TODO: Consider renaming to 'Persist Azure Anchors between app sessions' -->

このセクションでは、Azure Anchor ID を HoloLens 2 ローカル ディスクに保存したり、そこから取得したりするについて学習します。 これにより、Azure に対して、異なるアプリ セッション間で同じアンカー ID をクエリできるため、固定されたホログラムを前のアプリ セッションと同じ場所に配置できます。

[Hierarchy]\(階層\) ウィンドウで、Azure Anchor ID を HoloLens 2 ストレージに保存するためのボタンと、保存された ID をディスクから取得するためのボタンの 2 つのボタンを含む **[ButtonParent_SaveAnchorId]** オブジェクトを展開します。

![mrlearning-asa](images/mrlearning-asa/tutorial2-section2-step1-1.png)

前のチュートリアルの[シーンを操作するためのボタンの構成](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)と同じ手順に従い、**Pressable Button Holo Lens 2 (Script)** コンポーネントと **Interactable (Script)** コンポーネントを次の 2 つのボタンそれぞれに対して構成します。

* **[SaveAzureAnchorIdToDisk]** オブジェクトの場合、[AnchorModuleScript] > **[SaveAzureAnchorIdToDisk ()]** 関数を割り当てます。
* **[GetAzureAnchorIdFromDisk]** オブジェクトの場合、[AnchorModuleScript] > **[GetAzureAnchorIdFromDisk ()]** 関数を割り当てます。

更新されたアプリケーションを HoloLens にビルドすると、Azure Anchor ID を保存することで、アプリ セッション間で Azure Spatial Anchors を永続化できるようになります。 これをテストするには、次の手順を実行します。

1. ロケット発射台エクスペリエンスを目的の場所に移動します。
2. Azure セッションを開始します。
3. Azure Anchor を作成します (ロケット発射台エクスペリエンスの場所にアンカーを作成します)。
4. Azure Anchor ID をディスクに保存します。
5. アプリケーションを再起動します。
6. ディスクから Azure Anchor を取得します (保存したアンカー ID を読み込みます)。
7. Azure セッションを開始します。
8. Azure Anchor を見つけます (手順 3 の場所にロケット発射台エクスペリエンスを配置します)。

> [!NOTE]
> アプリケーションを完全に再起動するには、イマーシブ アプリ ビューを終了した後、[スタート] メニューからアプリケーションを再起動する前に、Mixed Reality ホームのアプリ ウィンドウを閉じる必要があります。 詳細については、「[HoloLens でアプリを使用する](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens)」のドキュメントを参照してください。

## <a name="share-azure-anchors-between-multiple-devices"></a>複数のデバイス間で Azure Anchor を共有する

このセクションでは、複数のデバイス間で Azure Anchor ID を共有する方法について学習します。 これにより、複数のデバイスが同じアンカー ID を Azure に対してクエリできるようになり、固定されたホログラムを空間的に位置合わせできるようになります。 空間的な位置合わせ、つまり複数のデバイス間で同じ物理的な場所に同じホログラムを表示できることは、HoloLens 2 のローカル共有エクスペリエンスにとって重要です。

Azure Anchor ID をデバイス間で転送するには、[マルチユーザー機能のチュートリアル](mrlearning-sharing(photon)-ch1.md) シリーズで説明されている方法など、さまざまな方法があります。 この例では、デバイス間でアンカー ID をアップロードおよびダウンロードする単純な Web サービスを使用します。

[Hierarchy]\(階層\) ウィンドウで、 Azure Anchor ID を Web サーバーにアップロードするためのボタンと、ID を Web サーバーからダウンロードするためのボタンの 2 つのボタンを含む **[ButtonParent_ShareAnchorId]** オブジェクトを展開します。

![mrlearning-asa](images/mrlearning-asa/tutorial2-section3-step1-1.png)

前のチュートリアルの[シーンを操作するためのボタンの構成](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)と同じ手順に従い、**Pressable Button Holo Lens 2 (Script)** コンポーネントと **Interactable (Script)** コンポーネントを次の 2 つのボタンそれぞれに対して構成します。

* **[ShareAzureAnchorIdToNetwork]** オブジェクトの場合は、[AnchorModuleScript] > **[ShareAzureAnchorIdToNetwork ()]** 関数を割り当てます。
* **[GetAzureAnchorIdFromNetwork]** オブジェクトの場合は、[AnchorModuleScript] > **[GetAzureAnchorIdFromNetwork ()]** 関数を割り当てます。

更新されたアプリケーションを 2 つの HoloLens デバイスにビルドすると、Azure Anchor ID を共有することで、デバイス間で空間的な位置合わせを実現できるようになります。 これをテストするには、次の手順を実行します。

1. HoloLens デバイス 1 で次のようにします。ロケット発射台エクスペリエンスを目的の場所に移動します。
2. HoloLens デバイス 1 で次のようにします。Azure セッションを開始します。
3. HoloLens デバイス 1 で次のようにします。Azure Anchor を作成します (ロケット発射台エクスペリエンスの場所にアンカーを作成します)。
4. HoloLens デバイス 1 で次のようにします。Azure Anchor ID をネットワークに共有します。
5. HoloLens デバイス 2 で次のようにします。アプリケーションを開始します。
6. HoloLens デバイス 2 で次のようにします。ネットワークから共有アンカー ID を取得します (HoloLens デバイス 1 から共有されたアンカー ID を取得します)。
7. HoloLens デバイス 2 で次のようにします。Azure セッションを開始します。
8. HoloLens デバイス 2 で次のようにします。Azure Anchor を見つけます (手順 3 の場所にロケット発射台エクスペリエンスを配置します)。

> [!TIP]
> HoloLens が 1 つしかない場合でも、2 つ目の HoloLens デバイスを使用する代わりにアプリケーションを再起動することで、機能をテストできます。

## <a name="congratulations"></a>結論

このチュートリアルでは、Azure Spatial Anchor ID を HoloLens のローカル ディスクに保存することで、アプリケーションのセッションとアプリケーションの再起動を通して Azure Spatial Anchors を永続化する方法について学習しました。 また、Azure Spatial Anchors を複数のデバイス間で共有し、基本的なマルチユーザーの静的ホログラム共有エクスペリエンスを実現する方法についても学習しました。

次のチュートリアルでは、リアルタイムのフィードバックをユーザーに提供する方法について学習します。 このフィードバックには、アンカーの作成、環境の品質についての理解、および Azure セッションの状態に関する情報が含まれています。 フィードバックがなければ、アンカーが Azure に正常にアップロードされたかどうか、環境の品質がアンカーの作成に十分であるかどうか、または現在の状態をユーザーが知ることができません。

[次のレッスン:3.Azure Spatial Anchors フィードバックの表示](mrlearning-asa-ch3.md)
