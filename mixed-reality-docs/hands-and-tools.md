---
title: ハンドコントローラーとモーションコントローラー
description: ハンドアンドモーションコントローラーの相互作用の概要
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: Mixed Reality、ハンズオン、motion コントローラー、対話、設計
ms.openlocfilehash: b6efb0a9651cad8eee9b80bb130aa1a85b9a9941
ms.sourcegitcommit: 76a7aa6e64e114b63ace058dd6d6d662b3c9f09e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/26/2019
ms.locfileid: "68507868"
---
# <a name="hands-and-motion-controllers"></a>ハンドコントローラーとモーションコントローラー
## <a name="scenarios"></a>シナリオ
[デザインガイドライン](interaction-fundamentals.md)を読み込んだ後にこの対話モデルを採用する場合は、ユーザーが holographic 世界と対話するために2人のユーザーを使用する必要があるアプリケーションを開発していることを意味します。 アプリケーションは、仮想と物理の間で boundry を削除するという目標を達成します。

次のようなシナリオが考えられます。
* インフォメーションワーカーの2D バーチャル画面と Ui を提供してコンテンツを表示および制御する
* 工場出荷時の組み立てラインでのファーストラインワーカーのチュートリアルとガイドの提供
* 医療プロフェッショナルを支援および教育するためのプロフェッショナルなツールの開発  
* 3D 仮想オブジェクトを使用して実際の世界を装飾する、または第2の世界を作成する 
* リアルワールドを背景として使用した場所ベースのサービスとゲームの作成

## <a name="hands-and-motion-controllers-modalities"></a>ハンドアンドモーションコントローラー感覚様相
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[手で直接操作](direct-manipulation.md)
これは、ユーザーがホログラムを直接操作したり操作したりできるようにするための、手の力を活用したモダリティです。 1日の有効期間を最小にして、適切な視覚的 affordances を提供することで、ユーザーは、実際のオブジェクトを操作するのと同じ方法を使用して仮想マシンとやり取りすることができます。   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[手を使ったポイントとコミット](point-and-commit.md)
このモダリティによって、ユーザーは距離内でホログラムを操作できるようになります。 これにより、ユーザーは周囲を最大限に活用できるようになります。 ユーザーは、ホログラムをどこにでも配置でき、任意の距離からそれらにアクセスできます。 2D および3D ホログラムの制御と操作を行うためのメンタルモデルとジェスチャは、直接操作のものと非常に同期されています。

### <a name="motion-controllersmotion-controllersmd"></a>[モーション コントローラー](motion-controllers.md)
モーションコントローラーは、ユーザーの物理的な機能を拡張するツールであり、1つまたは両方のハンズを使用しながら、広範囲の距離にわたる正確な対話を実現します。 これらのハードウェアアクセサリは、一般的に使用される多くの対話にショートカットを提供し、さまざまなアクションに対して tactile のフィードバックを提供します。 現在、モーションコントローラーは、Windows Mixed Reality (WMR) シナリオでのみ使用できます。 

![ハンドコントローラーとモーションコントローラーの比較感覚様相](images/Hands-and-controllers-720px.jpg)<br>

*ハンドコントローラーとモーションコントローラーの比較感覚様相*

## <a name="see-also"></a>関連項目
* [頭の視線入力とコミット](gaze-and-commit.md)
* [ヘッド視線入力とドウェル](gaze-and-dwell.md)
* [手で直接操作](direct-manipulation.md)
* [手を使ったポイントとコミット](point-and-commit.md)
* [ハンズフリー](hands-free.md)
