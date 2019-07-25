---
title: HoloLens 2 用 MR Learning 共有モジュール
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 529a888dfa00180ca908fbc7f4c62f9a9086c661
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460327"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4。オブジェクトの移動を複数のユーザーと共有する

このチュートリアルでは、共有セッションのすべての参加者が連携して相互作用を表示できるように、オブジェクトの移動を共有する方法について説明します。 このレッスンは、[基本モジュールチュートリアル](mrlearning-base.md)の一部として作成された太陰暦ランチャーに基づいています。

事項

- 共有する3D モデルとして旧暦ランチャーを使用する
- 3D モデルの移動を共有するようにプロジェクトを構成します。
- 基本的なマルチユーザーコラボレーションアプリケーションを構築する方法について説明します

### <a name="instructions"></a>手順


1. 前のレッスン (コントロール + S) からシーンを保存します。 必要なときに簡単に見つけられるように、HLSharedProjectMainPart4 という名前を指定できます。

2. [プロジェクト] ウィンドウの [Assets-> Scripts] フォルダーで [GenericNetSync] をダブルクリックして、Visual Studio または使用しているコードエディターで開きます。  

![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. 34および38行の場合は、このレッスンで使用するテーブルのコードをアクティブ化するために//を削除します。 次に、ファイルを保存します。 

![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. プロジェクトウィンドウで、PhotonRoom.cs Scripts フォルダー > 内のファイルをダブルクリックして、Visual Studio で開きます。 

![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. 手順 3. と同じように、//を削除して106コードをアクティブ化する必要があります。

![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png) 

![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. [階層] ビューで、NetworkRoom オブジェクトを選択します。

![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. プロジェクト ビューで、資産-> Resources-> Prefabs に移動します。 まず、テーブル prefab を PhotonRoom クラスの Tableprefab スロットにドラッグアンドドロップします。 次に、RocketLauncherCompleteVariantprefab を PhotonRoom クラスのモジュール Prefab スロットにドラッグアンドドロップします。

![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

   注:Prefab オブジェクトとリリースのいずれかをクリックすると、インスペクターがそのオブジェクトに切り替わります。 各オブジェクトをクリックし、ドラッグしてドロップし、各オブジェクトを適切なスロットに解放します。

8. MixedRealityPlayspace の左側にある矢印をクリックし、子ゲームオブジェクトの MainCamera を SharedPlayground グラウンドに移動します。 次に、prefab、MixedRealityPlayspace を削除して削除し、事前 fab を選択して、キーボードの [削除] をタップします。
![Module3hapter4step5im](images/module3chapter4step5im.PNG)

>注:メインカメラと SharedPlayground グラウンドの両方の位置が0、0、0に設定されていることを確認します。
>

9. 新しいオブジェクトを作成するために、SharedPlayground グラウンド親オブジェクトの子オブジェクトとして新しいゲームオブジェクトセットを作成します。 親オブジェクトを右クリックし、[空の作成] を選択します。 

10. 階層で新しいオブジェクトを選択し、[インスペクター] パネルでオブジェクトの名前を TableAnchor に変更します。 また、[コンポーネントの追加] をクリックし、TableAnchor コンポーネントを検索します。 それを選択してオブジェクトに追加します。 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

11. 次に、[プロジェクト] パネルの [Prefabs] フォルダーで、先ほど作成した "TableAnchor" 子オブジェクトにテーブル prefab をドラッグします。

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

12. 最後に、DebugWindow オブジェクトで、幅を50に、高さを20に変更します。

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)

## <a name="congratulations"></a>結論


この処理が完了すると、Unity プロジェクトに参加しているすべてのユーザーが、旧暦ランチャーを移動できるようになります。 すべての移動が同期されるため、各ユーザーが互いの相互作用を参照できます。 これらの概念は、すべての機能を備えた共有コラボレーションエクスペリエンスの基本的な構成要素として機能します。 

すべてのユーザーは共有エクスペリエンスの一部として接続されており、オブジェクトの相対的な移動を確認できますが、ローカルユーザーが物理的に同じ場所にある他のオブジェクトとオブジェクトを参照できるように、アバターとオブジェクトを正確に配置することはできません。現実的. ローカルの共有エクスペリエンスを固定するために、すべてのデバイスは物理環境についてよく理解している必要があります。 このモジュールでは、次のレッスンで実装する[Azure 空間アンカー](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) を使用してこれを実現します。

次のレッスンに進む前に、asa の基本、Azure アカウントとリソースの作成、およびその他の基本的なビルディングブロックについて説明している ASA Learning モジュールを完成させる必要があります。これは、共有エクスペリエンスに統合する前に必要です。

[次のレッスン:共有 (Photon) レッスン5](mrlearning-sharing(photon)-ch5.md)

