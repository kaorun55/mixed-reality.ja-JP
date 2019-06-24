---
title: MR Learning ASA モジュール HoloLens 2 での Azure 空間アンカー
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 4aabb4a35efebdd893cbb248365e534abd60f684
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327369"
---
# <a name="displaying-azure-spatial-anchor-feedback"></a>Azure の空間アンカーからのフィードバックを表示します。

このレッスンでは、Azure 空間アンカーを使用する場合、アンカーの検出、イベント、およびステータスに関するフィードバックをユーザーに提供する方法について学習します。

目標:

* ASA の現在のセッションに関する重要な情報を表示する UI パネルを設定する方法について説明します

* 理解し、調査をユーザーに、ASA SDK が利用できるようにするフィードバック要素

  

## <a name="instructions"></a>手順

### <a name="set-up-asa-feedback-ui-panel"></a>ASA フィードバック UI パネルを設定します。

1. このレッスンでは、"SaveAnchorToDisk"を使用していないことと"ShareAnchor"ボタンは、そのため両方のボタンを選択し、(下図参照) とインスペクター パネル内のチェック ボックスをオフにこれらのボタンを非表示にします。
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. 次に、命令のパネルを作成します。 "Instruction"ボタンを右クリックして開始し、"3 D Object"と「textmeshpro-テキストを選択します」合わせ、

   

   ![module2chapter3step2im](images/module2chapter3step2im.PNG)

   3. スケールと手順については、シーン内で一致するよう、テキストの配置を調整します。 また、すべてのテキストの配置の中心を確認します。 下の画像に示すように、テキスト エディターからサンプル テキストを削除します。


![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. TextMeshPro オブジェクトの名前を"FeedbackPanel。"に変更します。
   
   ![module2chapter3step4im](images/module2chapter3step4im.PNG)
   
5. プロジェクト パネルで、アセット を選択し、右クリックし、「エクスプ ローラーで表示します。」を選択します。
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

をクリックして[ここ](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E)ファイルをダウンロードするために必要な次のいくつかの手順。

6. エクスプ ローラーが開いたら、assets フォルダー、"ASAmodulesAssets"フォルダーを選択し、アンカーのフィードバック スクリプトとアンカー モジュール スクリプト ファイルをフォルダーにコピーします。 
   

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> 注: 古いを上書きするか、古いを保持する場合を確認する上書きを選択するかをたずねるポップアップが表示されます。

7. Assets フォルダーに戻るようになりました。 次に、"AzureSpatialAnchorsPlugin"フォルダー、し、フォルダー、および最後に、scripts フォルダーに移動し、Azure 空間アンカー デモのラッパーをそのフォルダーにコピーします。 
   

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. ファイルをアップロードすると、これでは、ASA_feedback 階層で、"feedbackpanel"テキストを選択することを確認し、"コンポーネントの追加 をクリックします。 検索し、選択することが表示されたら、アンカーのフィードバック スクリプトを追加します。 
   
   

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. 次の図に示すように、スクリプトの下に空のスロットに ASA_Feedback 階層から"feedbackPanel"テキスト オブジェクトをドラッグします。 
   

![module2chapter3step9im](images/module2chapter3step9im.PNG)

   

## <a name="congratulations"></a>結論

このレッスンでは、ユーザーをリアルタイムのフィードバックを提供するための Azure 空間アンカー エクスペリエンスの現在の状態を表示する UI パネルを作成する方法について説明しました。


