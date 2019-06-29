---
title: ラーニング モジュールを共有 HoloLens 2 を MR
description: このコースでは、HoloLens 2 アプリケーション内でのマルチ ユーザー共有機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 2a16d318c6d749bcbf6ed9db0d6cd2228a6ea06e
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465203"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a>Azure の空間アンカーおよび共有エクスペリエンス

このレッスンでは、共有の経験に Azure 空間アンカー (ASA) を統合する方法について説明します。 ASA では、一般的な参照がある、物理環境があるすべての参加要素は、同じ物理的な場所にオブジェクトを参照してくださいにアンカー仮想体験する場合に併置されている複数のデバイスを許可します。

このレッスンを続行する前に、ASA 基本、Azure アカウントとリソースの作成と、共有のエクスペリエンスに統合できます ASA 前に必要な他の基本的なビルディング ブロックはカバー ASA ラーニング モジュールを完了する必要があります。

目標:

- ASA をマルチ デバイスの配置の共有エクスペリエンスに統合します。
- ローカルの共有エクスペリエンスの観点で ASA のしくみの基礎を学習します。

### <a name="instructions"></a>手順

1. (コントロール + S) は、前のレッスンからプロジェクトを保存して、もう一度必要なときを見つけやすいように"HLSharedProjectMainPart5.unity"という名前を付けます。

2. MixedRealityPlayspace 親オブジェクトの下にある TableAnchor プレハブを選択し、それを削除します。

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)



3.  資産に移動して、プロジェクト ビューではリソース]-> [プレハブを -> し、子 SharedPlayground オブジェクト上に TableAnchor プレハブをドラッグします。
4.  MixedRealityPlayspace の親オブジェクト、TableAnchor のオブジェクトを展開しもボタン オブジェクトを展開します。 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. 今すぐ階層では、ShareAzureAnchorButton を選択し、Inaspector パネルに、注意を移動します。 、次の図に示すように、ドロップ ダウン メニューまで下へスクロールし、AnchorModuleScript ShareAnchorNetework() をクリックします。

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. GetAzureAnchorButton を選択します (手順 4 を参照)、し、[Inspector] パネルに、注意を移動します。 、次の図に示すように、ドロップ ダウン メニューまで下へスクロール選択 AnchorModuleScript、GetSharedAnchorNetwork()、 をクリックし、保存します。

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a>結論

このレッスンでは、Azure の強力な新しい空間アンカー共有エクスペリエンスに併置されているデバイスに合わせてを統合する方法を学習しました。 このレッスンでは、共有モジュールも終了です。 アバターと共有オブジェクトを構成して、最後に ASA を使用して複数の参加要素のアラインメントは、新しい Photon アカウントを設定する、Photon とだじゃれを新しい Unity アプリケーションに統合する方法を学びました。 

