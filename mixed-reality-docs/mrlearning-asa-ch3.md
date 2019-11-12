---
title: Azure 空間アンカーチュートリアル-3. Azure 空間アンカーフィードバックの表示
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 9f57cb9874aade2d6b19d0c061fd83eb04b9ef11
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2019
ms.locfileid: "73914379"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3. Azure 空間アンカーのフィードバックを表示する

このレッスンでは、Azure 空間アンカーを使用する場合のアンカー検出、イベント、および状態に関するフィードバックをユーザーに提供する方法について説明します。

## <a name="objectives"></a>目標

* 現在の ASA セッションに関する重要な情報を表示する UI パネルを設定する方法について説明します。

* ASA SDK によってユーザーに提供されるフィードバック要素について理解し、調査する

## <a name="instructions"></a>手順

### <a name="set-up-asa-feedback-ui-panel"></a>ASA フィードバック UI パネルを設定する

1. このレッスンでは、"SaveAnchorToDisk" と "" ボタンを使用していないので、両方のボタンを選択し、次に示すようにインスペクターパネルのチェックボックスをオフにして、これらのボタンを非表示にします。
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. 命令パネルを作成します。 まず、[命令] ボタンを右クリックし、[3D オブジェクト] の上にマウスポインターを移動して、[textmeshpro-text] を選択します。

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. シーン内の指示と一致するように、テキストのスケールと配置を調整します。 また、すべてのテキストの配置が中央揃えになっていることを確認します。 次の図に示すように、テキストエディターからサンプルテキストを削除します。

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. TextMeshPro オブジェクトの名前を「フィードバックパネル」に変更します。
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. ASA_feedback 階層で "フィードバックパネル" のテキストが選択されていることを確認し、[コンポーネントの追加] をクリックして、アンカーフィードバックスクリプトを検索し、表示されたらそれを選択して追加します。 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

6. 次の図に示すように、ASA_Feedback 階層の "フィードバックパネル" テキストオブジェクトを、スクリプトの下の空のスロットにドラッグします。 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a>結論

このレッスンでは、リアルタイムのフィードバックをユーザーに提供するために、Azure 空間アンカーエクスペリエンスの現在の状態を表示する UI パネルを作成する方法を学習しました。


