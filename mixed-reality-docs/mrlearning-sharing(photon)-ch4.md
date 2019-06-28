---
title: ラーニング モジュールを共有 HoloLens 2 を MR
description: このコースでは、HoloLens 2 アプリケーション内でのマルチ ユーザー共有機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: d5bed61f5ffc1d3b4efed96f47c3568fbf3a2948
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416013"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a>同期共有のオブジェクトの移動

このレッスンでは、共有セッションのすべての参加者が共同して、互いの相互作用を表示できるように、オブジェクトの動きを共有する方法を学びます。 このレッスンの一部として構築された、太陰暦ランチャーに磨き、[ベース モジュール チュートリアル](mrlearning-base.md)します。

目標:

- 共有する 3D モデルとして太陰暦ランチャーに表示します。
- 3D モデルの動作を共有するプロジェクトを構成します。
- 基本的なマルチ ユーザー コラボレーション アプリケーションを構築する方法について説明します

### <a name="instructions"></a>手順

1. (コントロール + S) は、前のレッスンからシーンを保存します。 名前を付ける"HLSharedProjectMainPart4.unity"必要なときに見つけやすくなるようにします。

2. プロジェクト ウィンドウの 資産 > Scripts フォルダーでは、Visual Studio またはコード エディターを使用することで開く GenericNetSync ダブルクリックします。  ![](images/module3chapter4updatestep2.png)

3. 34 と 38 の行では、削除、"//"このレッスンで使用するテーブルのコードをアクティブにします。  ファイルを保存します。 ![](images/module3chapter4updatestep3.png)

4. [プロジェクト] ウィンドウで、資産の PhotonRoom.cs ファイルをダブルクリックします。 > Scripts フォルダーをもう一度 Visual Studio で開きます。 ![](images/module3chapter4updatestep4.png)

5. 同じように手順 3 で削除する必要があります、"//"25、26、および 106 行でコードをアクティブにします。![](images/module3chapter4updatestep5a.png) ![](images/module3chapter4updatestep5b.png)

6. 階層ビューでは、NetworkRoom オブジェクトを選択します。![](images/module3chapter4updatestep6.png)

7. プロジェクト ビューでは、資産に移動します > リソース > プレハブします。 最初に、ドラッグし、テーブル プレハブを PhotonRoom クラスの"Tableprefab"スロットにドロップします。 次にドラッグし、PhotonRoom クラスのプレハブ"モジュール"スロットに LunarModule プレハブをドロップします。 ![](images/module3chapter4updatestep7.png)

   注:Prefab オブジェクトとリリースのいずれかをクリックすると、インスペクターはそのオブジェクトに切り替わります。 をクリックして、ドラッグ、ドロップおよび適切なスロットには、各オブジェクトを解放します。



8. ここで、"MixedRealityPlayspace"の左側にある矢印をクリックし、子ゲーム オブジェクトの"MainCamera"を"SharedPlayground"プレハブを下へ移動します。 (削除、プレハブを選択し、キーボードの「削除」をタップします) を prefab"MixedRealityPlayspace"を削除してください。

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

注:0,0,0 に Main Camera と SharedPlayground の両方の位置が設定されていることを確認します。

9. 子オブジェクトとして設定 (新しいオブジェクトを作成、親オブジェクトを右クリックし、「空の作成」を選択) する"SharedPlayground"の親オブジェクトに新しいゲーム オブジェクトを作成します。 

10. 新しいオブジェクトを階層内の選択、インスペクターのパネルでオブジェクトの名前を"TableAnchor"に変更します。 また、"コンポーネントの追加 をクリックし、"TableAnchor"コンポーネントを検索します。 これを選択し、オブジェクトに追加します。 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> 注: x 位置を設定 = 1、y =-0.55、および z = 2 です。 また、y に回転を設定 = 90 です。 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. 今すぐプロジェクト パネルで、「プレハブ」フォルダーにドラッグ"table"プレハブ"TableAnchor"子オブジェクトを作成しました。

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. 最後に、"DebugWindow"オブジェクトでは、80 と高さを 10 に幅を変更します。

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a>結論

これが完了すると、Unity プロジェクトに参加するすべてのユーザーを太陰暦ランチャーを移動できます。 各ユーザーが互いの相互作用を表示できるように、すべての動きが同期されます。 これらの概念は、全機能装備のコラボレーション エクスペリエンス用の基本的な構成要素として機能します。 

アプリケーションがアバターとオブジェクトをローカル ユーザーと、同じ物理内でオブジェクトを参照してくださいように正確に配置することはできないが、すべてのユーザーは、共有のエクスペリエンスの一部として接続しているし、オブジェクトの相対的な動きを確認できます、世界です。 ローカルの共有エクスペリエンスを固定するためには、すべてのデバイスには、物理環境の共通理解が必要です。 このモジュールでこれを実現しますを使用して[Azure 空間アンカー](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) は、次のレッスンでは実装されています。

次のレッスンに進む前に、取り上げる ASA の基礎, Azure アカウントとリソースの作成、およびその他の基本的なビルディング ブロックが必要な共有のエクスペリエンスに組み込むことができます前に、ASA ラーニング モジュールを完了する必要があります。

[次のレッスン:Sharing(Photon) レッスン 5](mrlearning-sharing(photon)-ch5.md)

