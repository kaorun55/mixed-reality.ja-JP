---
title: ラーニング モジュールを共有 HoloLens 2 を MR
description: このコースでは、HoloLens 2 アプリケーション内でのマルチ ユーザー共有機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 9f4a0c0cc37ab097a60c44891d56fa65f6032418
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327767"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a>Azure の空間アンカーおよび共有エクスペリエンス

このレッスンでは、Azure 空間アンカー (ASA) を共有のエクスペリエンスに統合する方法について学習します。 ASA では、共通理解があるすべての参加要素が同じ物理的な場所にオブジェクトを表示するように仮想を固定するには、物理環境が発生した場合に併置されている複数のデバイスを許可します。

このレッスンを続行する前に、ASA の基礎、Azure アカウントとリソースの作成と、共有のエクスペリエンスに統合できます ASA 前に必要な他の基本的なビルディング ブロックについては説明、ASA ラーニング モジュールを完了する必要があります。

目標:

- ASA をマルチ デバイスの配置の共有エクスペリエンスに統合します。
- ローカルの共有エクスペリエンスの観点で ASA のしくみの基礎を学習します。

### <a name="instructions"></a>手順

1. (コントロール + S) は、前のレッスンからプロジェクトを保存して、もう一度必要なときを見つけやすいように"HLSharedProjectMainPart5.unity"という名前を付けます。

2. "MixedRealityPlayspace"の親オブジェクトの下にある TableAnchor プレハブを選択し、それを削除します。

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3. 前のレッスン、一部のようにインポートすれば、新しいカスタム パッケージを[ここです。](placeholderlink)

![Module3Chapter5step3im](images/module3chapter5step3im.PNG)

4. インポートされたら、[プロジェクト] パネルで「プレハブ」フォルダーから (インポート前の手順で unity パッケージ) から新しく更新されたテーブルのアンカーを取得し、親オブジェクトの"MixedRealityPlayspace"にドロップ

![Module3hapter5step4im](images/module3chapter5step4im.PNG)

5. 展開し、"MixedRealityPlayspace"の親オブジェクトでは、"TableAnchor"オブジェクトを展開しも「ボタン」のオブジェクトを展開します。 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

6. 今すぐ階層では、"ShareAzureAnchorButton"を選択し、inspector パネルに、注意を移動します。 、次の図に示すように、ドロップダウン メニューまでスクロールし、"AnchorModuleScript"を選択し、"ShareAnchorNetework()。"をクリックしてください

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

7. 手順 6 と同様に"GetAzureAnchorButton"を選択し、[inspector] パネルに、注意します。 、次の図に示すように、ドロップダウン メニューまでスクロールし、"AnchorModuleScript"を選択し、"GetSharedAnchorNetwork()。"をクリックしてください 保存します。

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a>結論

このレッスンでは、Azure の強力な新しい空間アンカー共有エクスペリエンスに併置されているデバイスに合わせてを統合する方法を学習しました。 このレッスンでは、共有モジュールも終了です。 アバターと共有オブジェクトを構成して、最後に ASA を使用して複数の参加要素のアラインメントは、新しい Photon アカウントを設定する、Photon とだじゃれを新しい Unity アプリケーションに統合する方法を学びました。 

