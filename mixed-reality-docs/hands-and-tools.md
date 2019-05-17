---
title: 手およびモーションのコント ローラー
description: 手およびモーション コント ローラーの相互作用の概要
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: 複合現実、手、アニメーション コント ローラーとの対話の設計します。
ms.openlocfilehash: b13efadd111ca970abe625221fb8045644822c37
ms.sourcegitcommit: b5bad4eeb5cdd0c2a7b639442656c306e8b5853b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2019
ms.locfileid: "65813978"
---
# <a name="hands-and-motion-controllers"></a>手およびモーションのコント ローラー
## <a name="scenarios"></a>シナリオ
読み取り時にこの対話モデルを採用する場合、[デザイン ガイドライン](interaction-fundamentals.md)、holographic の世界とのやり取りに 2 つの手を使用するユーザーを必要とするアプリケーションを開発していることを意味します。 アプリケーションが仮想および物理の間の境界の削除の目標を達成しようとしています。

特定のシナリオは次のようになります。
* 情報ワーカーの 2D 仮想画面と Ui を表示および内容の制御を提供します。
* 最初の行のワーカーのチュートリアルと factory の組み立てラインのガイドを提供します。
* 支援と医療専門家の指導の本格的なツールの開発  
* 仮想の 3D オブジェクトを使用して現実の世界を修飾する、または 2 つ目の世界を作成するには 
* サービスと現実の世界を背景としてを使用してゲームに基づく場所を作成します。

## <a name="hands-and-motion-controllers-modalities"></a>手およびモーション コント ローラーのモダリティ
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[手で直接操作](direct-manipulation.md)
これは、ユーザーが手を加えることと、ホログラムを直接操作できる、手の機能を活用モダリティです。 Leaveraging 日常業務のエクスペリエンスし、適切な visual アフォーを提供するには、ユーザーは現実世界のオブジェクトを操作するのと同じ方法を使用して仮想のものを操作できます。   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[手を使ったポイントとコミット](point-and-commit.md)
このモードでは、距離でホログラムと対話するユーザーを支援します。 環境を最大限に利用できます。 ユーザーは、ホログラムを任意の場所に配置でき、それらの距離からアクセスできます。 メンタル モデルおよびジェスチャを制御すると、2 D および 3D ホログラムの操作が高と同期の直接操作します。

### <a name="motion-controllersmotion-controllersmd"></a>[モーション コントローラー](motion-controllers.md)
アニメーション コント ローラーは、手の 1 つまたは両方を使用しているときに、大規模な距離の範囲にわたって正確な相互作用を提供することで、ユーザーの物理的な機能を拡張するツールです。 これらのハードウェア製品では、さまざまな操作の多く一般的に使用されるの相互作用し、surefooted、触るフィードバックへのショートカットを提供します。 現時点では、モーションのコント ローラーでは、のみ WMR シナリオの使用できます。 

![](images/Hands-and-controllers-720px.jpg)<br>

## <a name="see-also"></a>関連項目
* [頭の視線入力とコミット](gaze-and-commit.md)
* [(近くに手の形の相互作用) を直接操作](direct-manipulation.md)
* [ポイントとコミット (Far 手の形の相互作用)](point-and-commit.md)
* [ハンズフリー](hands-free.md)
* [視線入力とドウェル](gaze-targeting.md)
