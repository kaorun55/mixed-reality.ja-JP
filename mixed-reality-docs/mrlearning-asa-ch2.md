---
title: Azure 空間アンカーチュートリアル-2. Azure 空間アンカーの保存、取得、共有
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 7b19233a9634e2568200476c9483464bbf9dd3c8
ms.sourcegitcommit: a580166a19294f835b8e09c780f663f228dd5de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77250745"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2. Azure 空間アンカーを保存、取得、共有する

このチュートリアルでは、HoloLens 2 のストレージにアンカー ID を保存することにより、複数のアプリセッションにわたって Azure 空間アンカーを保存する方法について説明します。 また、このアンカー ID を他のデバイスと共有して、複数デバイスのアンカーの配置を行う方法についても説明します。

## <a name="objectives"></a>目標

* アプリセッション間の永続化のために、HoloLens 2 ローカルディスクとの間で Azure 空間アンカー Id を保存および取得する方法について説明します。
* マルチデバイスシナリオでユーザー間で Azure 空間アンカー Id を共有する方法について説明します。

## <a name="preparing-the-scene"></a>シーンの準備

[プロジェクト] ウィンドウで、[**アセット** > **mrtk] に移動します。AzureSpatialAnchors** > **Prefabs**フォルダー。 CTRL ボタンを押したまま、 **ButtonParent_SaveAnchorId**をクリックして**ButtonParent_ShareAnchorId** 2 つの prefabs を選択し、階層 ウィンドウにドラッグしてシーンに追加します。

![mrlearning-asa](images/mrlearning-asa/tutorial2-section1-step1-1.png)

## <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>アプリセッション間で Azure のアンカーを保持する-アンカー ID をディスクに保存する
<!-- TODO: Consider renaming to 'Persist Azure Anchors between app sessions' -->

このセクションでは、HoloLens 2 ローカルディスクとの間で Azure Anchor ID を保存および取得する方法について説明します。 これにより、異なるアプリセッション間で同じアンカー ID の Azure に対してクエリを実行できるため、固定されたホログラムを前のアプリセッションと同じ場所に配置できます。

[階層] ウィンドウで、2つのボタンが含まれている**ButtonParent_SaveAnchorId**オブジェクトを展開します。1つは、AZURE Anchor ID を HoloLens 2 ストレージに保存するためのボタンで、もう1つは、保存された id をディスクから取得するためのボタンです。

![mrlearning-asa](images/mrlearning-asa/tutorial2-section2-step1-1.png)

前のチュートリアルの「[シーンの指示を操作するためのボタンの構成](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)」の手順に従って、 **Pressable Button Holo レンズ 2 (スクリプト)** コンポーネントと**対話型 (スクリプト)** コンポーネントを次の2つのボタンにそれぞれ構成します。

* **SaveAzureAnchorIdToDisk**オブジェクトの場合は、AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** 関数を割り当てます。
* **GetAzureAnchorIdFromDisk**オブジェクトの場合は、AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** 関数を割り当てます。

更新されたアプリケーションを HoloLens にビルドすると、Azure アンカー ID を保存することで、アプリセッション間で Azure 空間アンカーを永続化できるようになりました。 テストするには、次の手順を実行します。

1. ロケットランチャーエクスペリエンスを目的の場所に移動します。
2. Azure セッションを開始します。
3. Azure Anchor を作成します (ロケットランチャーエクスペリエンスの場所にアンカーを作成します)。
4. Azure Anchor ID をディスクに保存します。
5. アプリケーションを再起動します。
6. ディスクから Azure アンカーを取得します (保存したアンカー ID が読み込まれます)。
7. Azure セッションを開始します。
8. Azure Anchor を探します (手順 3. の場所にロケットランチャーエクスペリエンスを配置します)。

## <a name="share-azure-anchors-between-multiple-devices"></a>複数のデバイス間で Azure アンカーを共有する

このセクションでは、複数のデバイス間で Azure Anchor ID を共有する方法について説明します。 これにより、複数のデバイスが同じアンカー ID に対して Azure に対してクエリを実行できるようになり、固定されたホログラムを空間的に配置できるようになります。 空間の配置。つまり、複数のデバイス間で同じ物理的な場所に同じホログラムがある場合は、HoloLens 2 のローカル共有エクスペリエンスが重要になります。

[複数ユーザー機能のチュートリアル](mrlearning-sharing(photon)-ch1.md)シリーズに記載されている方法を含め、デバイス間で Azure Anchor id を転送する方法は多数あります。 この例では、単純な web サービスを使用して、デバイス間でアンカー Id をアップロードしてダウンロードします。

[階層] ウィンドウで、2つのボタンを含む**ButtonParent_ShareAnchorId**オブジェクトを展開します。Azure Anchor ID を web サーバーにアップロードするためのボタンと、web サーバーから ID をダウンロードするためのボタンの1つです。

![mrlearning-asa](images/mrlearning-asa/tutorial2-section3-step1-1.png)

前のチュートリアルの「[シーンの指示を操作するためのボタンの構成](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)」の手順に従って、 **Pressable Button Holo レンズ 2 (スクリプト)** コンポーネントと**対話型 (スクリプト)** コンポーネントを次の2つのボタンにそれぞれ構成します。

* **ShareAzureAnchorIdToNetwork**オブジェクトの場合は、AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** 関数を割り当てます。
* **GetAzureAnchorIdFromNetwork**オブジェクトの場合は、AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** 関数を割り当てます。

更新されたアプリケーションを2つの HoloLens デバイスにビルドすると、Azure アンカー ID を共有することによって、それらの間で空間の配置を実現できるようになりました。 テストするには、次の手順を実行します。

1. HoloLens デバイス 1: ロケットランチャーエクスペリエンスを目的の場所に移動します。
2. HoloLens デバイス 1: Azure セッションを開始します。
3. HoloLens デバイス 1: Azure アンカーを作成します (ロケットランチャーエクスペリエンスの場所にアンカーを作成します)。
4. HoloLens デバイス 1: Azure Anchor ID をネットワークに共有します。
5. HoloLens デバイス 2: アプリケーションを再起動します。
6. HoloLens デバイス 2: ネットワークから共有アンカー ID を取得します (HoloLens デバイス1から共有されたアンカー ID をフェッチします)。
7. HoloLens デバイス 2: Azure セッションを開始します。
8. HoloLens デバイス 2: Azure アンカーを検索します (手順 3. の場所でロケットランチャーエクスペリエンスを配置します)。

> [!TIP]
> HoloLens が1つしかない場合でも、2つ目の HoloLens デバイスを使用する代わりにアプリケーションを再起動することで、機能をテストできます。

## <a name="congratulations"></a>結論

このチュートリアルでは、azure 空間アンカー ID を HoloLens のローカルディスクに保存することで、アプリケーションセッションとアプリケーションの再起動の間で Azure 空間アンカーを永続化する方法について学習しました。 また、複数のデバイス間で Azure 空間アンカーを共有し、基本的なマルチユーザーの静的なホログラム共有エクスペリエンスを実現する方法についても学習しました。

次のチュートリアルでは、リアルタイムのフィードバックをユーザーに提供する方法について説明します。 このフィードバックには、アンカーの作成、環境の理解の質、Azure セッションの状態に関する情報が含まれています。 フィードバックがないと、アンカーが Azure に正常にアップロードされたかどうか、環境の品質がアンカーの作成に十分であるか、現在の状態であるかをユーザーが知ることができません。

[次のレッスン: 3. Azure 空間アンカーフィードバックの表示](mrlearning-asa-ch3.md)
