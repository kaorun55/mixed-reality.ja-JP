---
title: MR Learning ASA モジュール Azure 空間アンカー (HoloLens 2)
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: c6e902710eebe205b9e944b1bf95a9ddd3bd9044
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293802"
---
# <a name="displaying-azure-spatial-anchor-feedback"></a>Azure 空間アンカーフィードバックの表示

このレッスンでは、Azure 空間アンカーを使用するときに、アンカー検出、イベント、および状態に関するフィードバックをユーザーに提供する方法について説明します。

事項

* 現在の ASA セッションに関する重要な情報を表示する UI パネルを設定する方法について説明します。

* ASA SDK によってユーザーに提供されるフィードバック要素について理解し、調査する

## <a name="instructions"></a>手順

### <a name="set-up-asa-feedback-ui-panel"></a>ASA フィードバック UI パネルを設定する

1. このレッスンでは、"SaveAnchorToDisk" と "" ボタンを使用していないので、これらのボタンを非表示にするには、両方のボタンを選択し、[インスペクター] パネルのチェックボックスをオフにします (次の図を参照)。
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. 次に、命令パネルを作成します。 まず、[命令] ボタンを右クリックし、[3D オブジェクト] の上にマウスポインターを移動して、[textmeshpro-text] を選択します。

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. シーンの指示と一致するように、スケールとテキストの配置を調整します。 また、すべてのテキストの配置が中央揃えになっていることを確認します。 次の図に示すように、テキストエディターからサンプルテキストを削除します。

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. TextMeshPro オブジェクトの名前を「フィードバックパネル」に変更します。
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. [プロジェクト] パネルで、[資産] を選択して右クリックし、[エクスプローラーで表示] を選択します。
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

ここで、[ここ](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E)をクリックして、次のいくつかの手順で必要なファイルをダウンロードします。

6. エクスプローラーが開いたら、assets フォルダー、"ASAmodulesAssets" フォルダーの順に選択し、アンカーフィードバックスクリプトとアンカーモジュールスクリプトファイルをフォルダーにコピーします。 

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> 注: 古いものを上書きするか、古いものを保持するかを確認するポップアップが表示された場合は、[上書き] を選択してください。

7. 次に、Assets フォルダーに戻ります。 次に、"AzureSpatialAnchorsPlugin" フォルダーにアクセスし、[例] フォルダーをクリックし、最後に scripts フォルダーを選択して、Azure 空間アンカーデモラッパーをそのフォルダーにコピーします。 

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. ファイルがアップロードされたので、ASA_feedback 階層で "フィードバックパネル" というテキストが選択されていることを確認し、[コンポーネントの追加] をクリックしてアンカーフィードバックスクリプトを検索し、表示されたらそれを選択して追加します。 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. 次の図に示すように、ASA_Feedback 階層の "フィードバックパネル" テキストオブジェクトを、スクリプトの下の空のスロットにドラッグします。 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a>結論

このレッスンでは、ユーザーにリアルタイムのフィードバックを提供するための Azure 空間アンカーエクスペリエンスの現在の状態を表示する UI パネルを作成する方法について学習しました。


