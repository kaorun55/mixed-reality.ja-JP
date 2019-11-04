---
title: ハンドコントローラーとモーションコントローラー
description: ハンドアンドモーションコントローラーの相互作用の概要
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: 混合現実、ハンド、モーションコントローラー、相互作用、設計
ms.openlocfilehash: 395862fe987244e2af70bb6794caa91e243cd076
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435153"
---
# <a name="hands-and-motion-controllers"></a>ハンドコントローラーとモーションコントローラー
## <a name="scenarios"></a>シナリオ
[相互作用の概要](interaction-fundamentals.md)を読み取った後にこの相互作用モデルを採用することを選択した場合は、ユーザーが holographic 世界と対話するために2人のユーザーを使用する必要があるアプリケーションを開発していることを意味します。 アプリケーションは、仮想と物理の間の境界を削除するという目標を達成します。

次のようなシナリオが考えられます。
* UI affordances を使用してインフォメーションワーカーの2D 仮想スクリーンを提供し、コンテンツの表示と制御を行う
* ファクトリアセンブリラインのためのファーストラインワーカーのチュートリアルとガイドの提供
* 医療プロフェッショナルを支援および教育するためのプロフェッショナルなツールの開発  
* 3D 仮想オブジェクトを使用して実際の世界を装飾する、または第2の世界を作成する 
* 現実世界を背景とした場所ベースのサービスとゲームの作成

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a>ハンドアンドモーションコントローラー感覚様相

:::row:::
    :::column:::
       [ハンドを使用した ![直接操作](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)<br>
       ### <a name="direct-manipulation-with-handsdirect-manipulationmdbr"></a>[手で直接操作](direct-manipulation.md)<br>
       これは、ユーザーがホログラムを直接操作したり操作したりできるようにするための、手の力を活用したモダリティです。 日常的な経験を活用し、適切な視覚的 affordances を提供することにより、ユーザーは、実際のオブジェクトを操作するのと同じ方法を使用して仮想マシンとやり取りすることができます。
    :::column-end:::
    :::column:::
       [![ポイントし、ハンドでコミットする](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)<br>
        ### <a name="point-and-commit-with-handspoint-and-commitmdbr"></a>[手を使ったポイントとコミット](point-and-commit.md)<br>
        このモダリティによって、ユーザーは距離内でホログラムを操作できるようになります。 これにより、ユーザーは周囲を最大限に活用できるようになります。 ユーザーは、ホログラムをどこにでも配置でき、任意の距離からそれらにアクセスできます。 2D および3D ホログラムの制御と操作を行うためのメンタルモデルとジェスチャは、直接操作のものと非常に同期されています。
    :::column-end:::
    :::column:::
       [![モーションコントローラー](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)<br>
       ### <a name="motion-controllersmotion-controllersmdbr"></a>[モーション コントローラー](motion-controllers.md)<br>
       モーションコントローラーは、ユーザーの物理的な機能を拡張するツールであり、1つまたは両方のハンズを使用しながら、広範囲の距離にわたる正確な対話を実現します。 これらのハードウェアアクセサリは、一般的に使用される多くの対話にショートカットを提供し、さまざまなアクションに対して tactile のフィードバックを提供します。 現在、モーションコントローラーは、Windows Mixed Reality (WMR) シナリオでのみ使用できます。 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>関連項目
* [頭の視線入力とコミット](gaze-and-commit.md)
* [ヘッド視線入力とドウェル](gaze-and-dwell.md)
* [手で直接操作](direct-manipulation.md)
* [手を使ったポイントとコミット](point-and-commit.md)
* [ハンズフリー](hands-free.md)
