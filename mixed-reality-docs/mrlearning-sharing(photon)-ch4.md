---
title: マルチユーザー機能のチュートリアル - 4. 複数のユーザーとオブジェクトの移動を共有する
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: b0ddf0799fd94c29ce8f1221c55073cd77b63703
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031243"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4.複数のユーザーとオブジェクトの移動を共有する

このチュートリアルでは、共有セッションのすべての参加者が共同作業したり、相互の操作を表示したりできるように、オブジェクトの移動を共有する方法について説明します。 このレッスンは、[ベース モジュール チュートリアル](mrlearning-base.md)の一部として作成された月着陸船ランチャーに基づいて進められます。

## <a name="objectives"></a>目標

- 共有する 3D モデルとして月着陸船ランチャーを取り込む
- 3D モデルの移動を共有するようにプロジェクトを構成する
- 基本的なマルチユーザー コラボレーション アプリケーションを構築する方法を学習する

## <a name="instructions"></a>手順

1. 前のレッスンのシーンを保存します (Ctrl + S)。 必要なときに簡単に見つけられるように、HLSharedProjectMainPart4.unity という名前を付けることができます。

2. [Project]\(プロジェクト\) ウィンドウの [Assets]\(資産\) -> [Scripts]\(スクリプト\) フォルダーで、[GenericNetSync] をダブルクリックして、Visual Studio または使用している任意のコード エディターで開きます。  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. 行 34 および 38 の "//" を削除して、このレッスンで使用するテーブルのコードをアクティブにします。 次に、ファイルを保存します。

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. [Project]\(プロジェクト\) ウィンドウで、[Assets]\(資産\) -> [Scripts]\(スクリプト\) フォルダー内の PhotonRoom.cs ファイルをダブルクリックして、Visual Studio で開きます。

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. 手順 3 と同じように、"//" を削除して、行 25、26、106 のコードをアクティブにする必要があります。

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. [Hierarchy]\(階層\) ビューで、[NetworkRoom] オブジェクトを選択します。

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. [Project]\(プロジェクト\) ビューで、[Assets]\(資産\) -> [Resources]\(リソース\) -> [Prefabs]\(プレハブ\) に移動します。 まず、Table プレハブを PhotonRoom クラスの Tableprefab スロットにドラッグ アンド ドロップします。 次に、RocketLauncherCompleteVariantprefab を PhotonRoom クラスの Module Prefab スロットにドラッグ アンド ドロップします。

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    >プレハブ オブジェクトのいずれかをクリックして解放した場合、インスペクターがそのオブジェクトに切り替えます。 各オブジェクトをクリックし、適切なスロットにドラッグしてドロップし、解放します。

8. MixedRealityPlayspace の左側にある矢印をクリックし、子ゲーム オブジェクト MainCamera を SharedPlayground プレハブに移動します。 次に、プレハブ MixedRealityPlayspace を選択してキーボードの [Delete] キーを押して、そのプレハブを削除します。

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    >Main Camera と SharedPlayground の両方の位置が 0、0、0 に設定されていることを確認してください。

9. "SharedPlayground" オブジェクトを選択し、マウスを右クリックして [Create Empty]\(空の作成\) オプションを選択し、空のゲーム オブジェクトを "SharedPlayground" ゲーム オブジェクトの子として作成します。

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. 階層で新しいオブジェクトが選択された状態で、[Inspector]\(インスペクター\) パネルでオブジェクトの名前を TableAnchor に変更します。 また、[Add Component]\(コンポーネントの追加\) をクリックし、TableAnchor コンポーネントを検索します。 それを選択してオブジェクトに追加します。

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. [Prefabs]\(プレハブ\) フォルダーの [Project]\(プロジェクト\) パネルで、Table プレハブを、先ほど作成した "TableAnchor" 子オブジェクトにドラッグします。

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

## <a name="congratulations"></a>結論

これが完了したら、月着陸船を見つけます。 その後、Unity プロジェクトに参加するすべてのユーザーが月着陸船ランチャーをあちこちに移動できます。  すべての移動が同期されるため、各ユーザーがお互いの操作を確認できます。 これらの概念は、すべての機能を備えた共有コラボレーション エクスペリエンスの基本的な構成要素となります。

すべてのユーザーは共有エクスペリエンスの一部として接続され、オブジェクトの相対的な移動を参照できますが、アプリケーションでは依然としてアバターとオブジェクトを正確に配置できないため、ローカル ユーザーは現実世界の中の同じ場所にあるお互いとオブジェクトを参照できませんでした。 ローカル共有エクスペリエンスを固定するために、すべてのデバイスで物理環境についての共通理解が必要です。 このモジュールでは、次のレッスンで実装する [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) を使用してこれを実現します。

次のレッスンに進む前に、ASA 学習モジュールを完了する必要があります。これには、ASA の基本、Azure アカウントとリソースの作成、および共有エクスペリエンスにこれを統合する前に必要なその他の基本的な構成要素が対象として含まれます。

[次のレッスン:5.Azure Spatial Anchors の共有エクスペリエンスへの統合](mrlearning-sharing(photon)-ch5.md)
