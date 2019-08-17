---
title: 新しいスペースでの HoloLens の使用
description: HoloLens は、時間の経過と共にどのようなスペースが見えるかを学習します。 ユーザーは、特定の方法で HoloLens をスペースを介して移動することで、このプロセスを容易にすることができます。
author: dorreneb
ms.author: dobrown
ms.date: 08/16/2019
ms.topic: article
keywords: Windows Mixed Reality、設計、空間マッピング、HoloLens、surface 再構築、メッシュ、ヘッド追跡、マッピング
ms.openlocfilehash: a6a83dfc2c883723e4cd79c0dc46a9cd78f1f604
ms.sourcegitcommit: 60f73ca23023c17c1da833c83d2a02f4dcc4d17b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566021"
---
# <a name="use-hololens-in-new-spaces"></a>新しいスペースでの HoloLens の使用

HoloLensは、ユーザーがスペースを移動するときに、その環境に関する情報を学習します。 時間の経過と共に、HoloLens は、監視されている環境のすべての部分の*空間マップ*を構築します。 HoloLens は、環境内の変更が検出されたときにマップを更新します。 このスキャンは、アプリの起動間に自動的に保持されます。

HoloLens は、デバイスがオンになっていて、ユーザーがログインしている限り、マップを作成および更新します。 カメラがスペースで指されているデバイスを押さえたり、磨耗したりすると、デバイスはその領域をマップしようとします。 HoloLens は、時間の経過と共に自然に領域を取得しますが、スペースをより迅速かつ効率的にマップするためのヒントとテクニックが用意されています。 

HoloLens がスペースをマップできない場合、または調整されていない場合は、制限モードになることがあります。 制限モードでは、ホログラムを周囲に配置することはできません。

## <a name="tips-and-tricks-for-mapping-spaces"></a>スペースのマッピングに関するヒントとテクニック

### <a name="make-sure-the-space-is-set-up-for-mixed-reality"></a>混合現実のために領域が設定されていることを確認します。

環境内の機能によって、HoloLens がスペースを解釈するのが困難になる場合があります。 ライトレベル、空間内の素材、オブジェクトのレイアウトなどはすべて、HoloLens が領域をマップする方法に影響を与えます。

HoloLens とその他の mixed reality デバイス用の領域を設定するためのヒントについては、「 [hololens の環境に関する考慮事項](environment-considerations-for-hololens.md)」を参照してください。

### <a name="understand-the-scenarios-for-the-area"></a>領域のシナリオを理解する

HoloLens を使用する最も時間をかけて、マップが関連性と完全なものになるようにすることが重要です。 

たとえば、HoloLens のユーザーシナリオで、ポイント A からポイント B への移行が必要な場合、そのパスを 2 ~ 3 回進めます。移動すると、すべての方向が表示されます。 

### <a name="walk-slowly-around-the-space"></a>領域をゆっくりと処理する

この領域を簡単に説明すると、HoloLens がマッピング領域を見逃してしまう可能性があります。 領域をゆっくりとしていき、5-8 フィートごとに停止して、周囲の部分を見てみましょう。

Smooth 移動は、HoloLens map より多くの effeciently にも役立ちます。

### <a name="look-in-all-directions"></a>すべての方向を検索

空間をマップする際には、1つの HoloLens が互いに相対的な場所に移動します。 

たとえば、検索しない場合、たとえば、1つの部屋の天井がどこにあるかを HoloLens が認識できない可能性があります。 

スペースをマップする際には、必ずフロアを見てください。

### <a name="cover-key-areas-multiple-times"></a>主要領域を複数回カバーする

1つの区分を複数回移動すると、最初のチュートリアルでは見つからなかった機能を選択できます。 理想的なマップを作成するために、2 ~ 3 回の領域を走査します。

可能であれば、これらの移動を繰り返しながら、1つの方向の領域をたどる時間をかけて、前に戻ってみてください。

### <a name="take-your-time-mapping-the-area"></a>時間を取って領域をマッピングする

HoloLens が完全にマップされ、その周囲に調整されるまでに 15 ~ 20 分かかることがあります。 HoloLens を頻繁に使用する予定がある場合は、この時間を使用して領域をマップすると、後で問題が発生しなくなる可能性があります。 

## <a name="possible-errors-in-the-spatial-map"></a>空間マップで発生する可能性のあるエラー

空間マッピングデータのエラーは、次の3つのカテゴリのいずれかに分類されます。

* *穴*:空間マッピングデータに実際のサーフェイスがありません。
* *Hallucinations*:サーフェイスは、実際の環境に存在しない空間マッピングデータに存在します。
* *Wormholes*:HoloLens ' は、マップの別の部分にあるとしても、実際の値とは異なる部分にあると考えて、空間マップの一部を失います。
* *バイアス*:空間マッピングデータ内のサーフェイスは、実際のサーフェイスに固定されていて、プッシュまたはプルされます。

これらのエラーの多くは、[ホログラムを削除](environment-considerations-for-hololens.md)してスペースを再マップすることによって軽減できます。