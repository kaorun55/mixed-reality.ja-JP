---
title: ラーニング モジュールを共有 HoloLens 2 を MR
description: このコースでは、HoloLens 2 アプリケーション内でのマルチ ユーザー共有機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: a67eaef45582054b62198a563f0ee01724fd60db
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328110"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a>同期共有のオブジェクトの移動

このレッスンでは、共有セッションのすべての参加者が共同して、互いの相互作用を表示できるように、オブジェクトの動きを共有する方法を学びます。 このレッスンの一部として構築された、太陰暦ランチャーに磨き、[ベース モジュール チュートリアル](mrlearning-base.md)します。

目標:

- 3D モデルを共有すると、完了した太陰暦ランチャーをインポートします。
- 3D モデルの動作を共有するプロジェクトを構成します。
- 基本的なマルチ ユーザー コラボレーション アプリケーションを構築する方法について説明します

### <a name="instructions"></a>手順

1. (コントロール + S) は、前のレッスンからシーンを保存します。 名前を付ける"HLSharedProjectMainPart4.unity"必要なときに見つけやすくなるようにします。

2. (を選択し、del キーを押します)、"NetworkLobby"オブジェクトを削除します。 また、レッスン 2 から「プレハブ」フォルダーに移動し、そこからも"NetworkLobby"プレハブを削除します。

![Module3Chapter4tep2im](images/module3chapter4step2im.PNG)

3. (手順 2、レッスン 2 から) のような場合は、新しいカスタム パッケージをインポートし、インポート、 [LunarModule.unitypackage](linkforModule1 lesson with the lunar module)と[NetworkLobbyReplacement.unitypackage します。](linkforNetworklobbyreplacement package here)

![Module3Chapter4step3im](images/module3chapter4step3im.PNG)

4. ここで、「プレハブ」フォルダーには、階層に新しい"NetworkLobby"プレハブをドラッグします。 

![Module3hapter4step4im](images/module3chapter4step4im.PNG)

> 注: 前の手順でインポートした 2 つのパッケージは、"NetworkLobby"プレハブを更新します。 多くの入力が省けます。

5. ここで、"MixedRealityPlayspace"の左側にある矢印をクリックし、子ゲーム オブジェクトの"MainCamera"を"SharedPlayground"プレハブを下へ移動します。 (削除、プレハブを選択し、キーボードの「削除」をタップします) を prefab"MixedRealityPlayspace"を削除してください。

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

6. 子オブジェクトとして設定 (新しいオブジェクトを作成、親オブジェクトを右クリックし、「空の作成」を選択) する"SharedPlayground"の親オブジェクトに新しいゲーム オブジェクトを作成します。
7. 新しいオブジェクトを階層内の選択、インスペクターのパネルでオブジェクトの名前を"TableAnchor"に変更します。 また、"コンポーネントの追加 をクリックし、"TableAnchor"コンポーネントを検索します。 これを選択し、オブジェクトに追加します。

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> 注: x 位置を設定 = 1、y =-0.55、および z = 2 です。 また、y に回転を設定 = 90 です。 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

8. 今すぐプロジェクト パネルで、「プレハブ」フォルダーにドラッグ"table"プレハブ"TableAnchor"子オブジェクトを作成しました。

   ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

9. "NetworkRoom"、"NetworkLobby"の下で、階層内の子オブジェクトを選択して、"PhotonView"を検索してインスペクターのパネルで「コンポーネントの追加」をクリックし、スクリプトを追加、"*NetworkRoom*"オブジェクト。

![Module3Chapter4step9im](images/module3chapter4step9im.PNG)

11. 最後に、"DebugWindow"オブジェクトでは、80 と高さを 10 に幅を変更します。

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a>結論

これが完了すると、Unity プロジェクトに参加するすべてのユーザーを太陰暦ランチャーを移動できます。 各ユーザーが互いの相互作用を表示できるように、すべての動きが同期されます。 これらの概念は、全機能装備のコラボレーション エクスペリエンス用の基本的な構成要素として機能します。 

アプリケーションがアバターとオブジェクトをローカル ユーザーと、同じ物理内でオブジェクトを参照してくださいように正確に配置することはできないが、すべてのユーザーは、共有のエクスペリエンスの一部として接続しているし、オブジェクトの相対的な動きを確認できます、世界です。 ローカルの共有エクスペリエンスを固定するためには、すべてのデバイスには、物理環境の共通理解が必要です。 このモジュールでこれを実現しますを使用して[Azure 空間アンカー](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) は、次のレッスンでは実装されています。

次のレッスンに進む前に、取り上げる ASA の基礎, Azure アカウントとリソースの作成、およびその他の基本的なビルディング ブロックが必要な共有のエクスペリエンスに組み込むことができます前に、ASA ラーニング モジュールを完了する必要があります。

[次のレッスン:Sharing(Photon) レッスン 5](mrlearning-sharing(photon)-ch5.md)

