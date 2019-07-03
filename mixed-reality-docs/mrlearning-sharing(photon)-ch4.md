---
title: ラーニング モジュールを共有 HoloLens 2 を MR
description: このコースでは、HoloLens 2 アプリケーション内でのマルチ ユーザー共有機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 2a4ea599fd4887f30589c2d839be305d3dc8d1bd
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523192"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4。オブジェクトの動きを複数のユーザーと共有

このチュートリアルでは、共有セッションのすべての参加者が共同して、互いの相互作用を表示できるように、オブジェクトの動きを共有する方法について説明します。 このレッスンの一部として構築された、太陰暦ランチャーに磨き、[ベース モジュール チュートリアル](mrlearning-base.md)します。

目標:

- 共有する 3D モデルとして太陰暦ランチャーに表示します。
- 3D モデルの動作を共有するプロジェクトを構成します。
- 基本的なマルチ ユーザー コラボレーション アプリケーションを構築する方法について説明します

### <a name="instructions"></a>手順


1. 前のレッスンでは、(コントロール + S) から、シーンを保存します。 という名前を HLSharedProjectMainPart4.unity、必要なときに見つけやすくなるようにします。

2. プロジェクト ウィンドウで、Scripts フォルダー]-> [資産、Visual Studio またはコード エディターを使用することで開く GenericNetSync をダブルクリックします。  ![](images/module3chapter4updatestep2.png)

3. 行 34 および 38 で、削除、//このレッスンで使用するテーブルのコードをアクティブにします。 次に、ファイルを保存します。 ![](images/module3chapter4updatestep3.png)

4. プロジェクト ウィンドウで、資産で PhotonRoom.cs ファイルをダブルクリックしますに Scripts フォルダーは、Visual Studio で開く-> です。 ![](images/module3chapter4updatestep4.png)

5. ステップ 3 で、削除すると同様、//25、26、および 106 行でコードをアクティブにします。![](images/module3chapter4updatestep5a.png) ![](images/module3chapter4updatestep5b.png)

6. 階層ビューでは、NetworkRoom オブジェクトを選択します。![](images/module3chapter4updatestep6.png)

7. プロジェクト ビューに移動します。 資産のリソース]-> [プレハブ]-> [です。 最初に、ドラッグし、Tableprefab スロット PhotonRoom クラスにテーブルのプレハブをドロップします。 次にドラッグし、モジュール Prefab スロット PhotonRoom クラスに LunarModule プレハブをドロップします。 ![](images/module3chapter4updatestep7.png)

   注:Prefab オブジェクトとリリースのいずれかをクリックすると、インスペクターはそのオブジェクトに切り替わります。 をクリックして、ドラッグ、ドロップ、および適切なスロットには、各オブジェクトを解放します。



8. MixedRealityPlayspace の左側にある矢印をクリックし、SharedPlayground プレハブに下 MainCamera 子ゲーム オブジェクトに移動します。 次に、削除、プレハブ、MixedRealityPlayspace、削除、プレハブを選択し、キーボードの「削除」をタップします)。
![Module3hapter4step5im](images/module3chapter4step5im.PNG)

注:0,0,0 に Main Camera と SharedPlayground の両方の位置が設定されていることを確認します。

9. 新しいオブジェクトを作成する SharedPlayground の親オブジェクトに子オブジェクトとして設定の新しいゲーム オブジェクトを作成します。 親オブジェクトを右クリックし、空アイテムの作成を選択します。 

10. 新しいオブジェクトを階層内の選択、インスペクターのパネルでオブジェクトの名前を TableAnchor に変更します。 また、コンポーネントの追加 をクリックし、TableAnchor コンポーネントを検索します。 これを選択し、オブジェクトに追加します。 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> 注:X 位置を設定 = 1、y =-0.55、および z = 2 です。 また、y に回転を設定 = 90 です。 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. 今すぐ Prefabs フォルダーに [プロジェクト] パネルから作成した"TableAnchor"の子オブジェクトにテーブルのプレハブをドラッグします。

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. 最後に、DebugWindow オブジェクトでは、80 と高さを 10 に幅を変更します。

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a>結論


これが完了すると、Unity プロジェクトに参加するすべてのユーザーを太陰暦ランチャーを移動できます。 各ユーザーが互いの相互作用を表示できるように、すべての動きが同期されます。 これらの概念は、フル機能の共有のコラボレーション エクスペリエンス用の基本的な構成要素として機能します。 

アプリケーションがアバターとオブジェクトをローカル ユーザーと、同じ物理内でオブジェクトを参照してくださいように正確に配置することはできないが、すべてのユーザーは、共有のエクスペリエンスの一部として接続しているし、オブジェクトの相対的な動きを確認できます、世界です。 ローカルの共有エクスペリエンスを固定するためには、すべてのデバイスには、物理環境の共通理解が必要です。 このモジュールで私たちを得ることがこれを使用して[Azure 空間アンカー](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) は、次のレッスンで実装します。

次のレッスンに進む前にカバーする ASA の基礎, Azure アカウントとリソースの作成、およびその他の基本的なビルディング ブロックが必要な共有のエクスペリエンスに組み込むことができます前に、ASA ラーニング モジュールを完了する必要があります。

[次のレッスン:Sharing(Photon) レッスン 5](mrlearning-sharing(photon)-ch5.md)

