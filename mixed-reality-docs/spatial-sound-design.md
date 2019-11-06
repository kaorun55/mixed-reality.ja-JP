---
title: Mixed Reality アプリケーションでのサウンドの使用
description: 空間サウンドは、mixed reality アプリケーションでの immersion、アクセシビリティ、UX の設計を行うための強力なツールです。
author: kegodin
ms.author: kegodin
ms.date: 11/02/2019
ms.topic: article
keywords: Windows Mixed Reality、空間サウンド、デザイン、スタイル
ms.openlocfilehash: c069095808eaa9d31b1ffa41dbaa29c9f635837b
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641063"
---
# <a name="using-sound-in-mixed-reality-applications"></a>Mixed Reality アプリケーションでのサウンドの使用

サウンドを使用して、ユーザーのアプリケーション状態のメンタルモデルを通知し、補強します。 必要に応じて spatialization を使用して、サウンドを混合世界に配置します。 この方法で聴覚とビジュアルを接続することで、多くの相互作用を直感的に deepens し、ユーザーの信頼度を高めることができます。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="when-should-i-add-sounds"></a>サウンドを追加するタイミング
混合現実アプリケーションでは、物理インターフェイスがないため、多くの場合、2D 画面のアプリケーションよりも音が大きくなります。 ユーザーに通知する場合や、対話を補強する場合は、サウンドを追加する必要があります。

### <a name="inform-and-reinforce"></a>通知と補強
* 通知など、ユーザーによって開始されていないイベントについては、変更が発生したことをユーザーに通知するためにサウンドを追加することを検討してください。
* 相互作用には複数の段階があります。 ステージの遷移を補強するには、サウンドを使用することを検討してください。

相互作用、イベント、および推奨されるサウンド特性の例については、以下を参照してください。

### <a name="exercise-restraint"></a>演習ガイド
ユーザーは、オーディオ情報に対して無制限の容量を使用できません。
* 各サウンドは、特定の重要な情報を伝達します。
* ユーザーに通知することを意図したサウンドを再生する場合は、一時的に他のサウンドの音量を下げる
* ボタンをポイントしたときのサウンド (下記参照) では、音が過剰にトリガーされないように遅延時間を追加します。

### <a name="dont-rely-solely-on-sounds"></a>サウンドだけに依存しない
サウンドは、ユーザーが音声を聞くことはできますが、サウンドがオフの場合でもアプリケーションが使用可能であることを確認しておくと便利です。
* ユーザーの聴覚が不自由である可能性がある
* アプリケーションは、大きな環境で使用できます。
* ユーザーは、デバイスオーディオを無効にするためのプライバシーまたはその他の理由を持っている可能性があります。

## <a name="how-should-i-sonify-interactions"></a>相互作用を sonify するにはどうすればよいですか。
混合現実の対話型には、ジェスチャ、直接操作、音声などがあります。 次の推奨される特性を使用して、これらのインタラクションのサウンドを選択または設計します。

### <a name="gesture-interactions"></a>ジェスチャの相互作用
Mixed reality では、ユーザーはカーソルを使用してボタンを操作できます。 ボタンの操作は、通常、ユーザーがボタンを押したときではなくボタンを離したときに実行され、ユーザーが操作をキャンセルできるようにします。 サウンドを使用して、これらのステージを補強します。 また、離れた場所にあるボタンをユーザーがターゲットにできるようにするには、カーソルをポイントする音を使用することを検討してください。
* ボタンを押す音には、短い tactile のクリックが必要です。 例: [MRTK_ButtonPress](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* ボタンの押されていない音には、同様の tactile 感が必要です。 ピッチと押されたピッチを持つと、完了の意味がわかります。 例: [MRTK_ButtonUnpress](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)
* ホバーサウンドの場合は、低周波数の thud やバンプなど、微妙で脅威のないサウンドを使用することを検討してください。


### <a name="direct-manipulation"></a>直接操作
HoloLens 2 では、独自の追跡はユーザーインターフェイス要素の直接操作をサポートしています。 サウンドは、物理的なフィードバックがない場合の重要な交換です。

ユーザーがキー移動の一番下に到達したことを物理的に示すことがないため、直接操作では**ボタンの押下**音が重要です。 キー移動の視覚的なインジケーターは、小規模、軽度、occluded になることがあります。 ジェスチャによる対話と同様に、ボタンを押すには、tactile のような短い音が必要です。また、押されていない場合は、[ピッチ] をクリックした場合と同様のクリックが発生します。
* 例: [MRTK_ButtonPress](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* 例: [MRTK_ButtonUnpress](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonUnpress)

直接操作で**グラブ**または**リリース**を確認することは、視覚的に通信するのは困難です。 多くの場合、ユーザーの手は視覚効果の高い方法であり、ハードハンドオブジェクトには "グラブ" という実際の視覚的な類似性がありません。 これに対し、サウンドは、成功したグラブとリリースの相互作用を効果的に伝えることができます。
* グラブアクションには、オブジェクトの周りを閉じる指の概念を evokes する、少し muffled tactile サウンドが必要です。 場合によっては、音が出たときの動きを通知する音が "whoosh" サウンドによって示されることもあります。 例: [MRTK_Move_Start](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_Move_Start.wav)
* リリースアクションには同様の短いサウンドと tactile サウンドが必要です。通常は、グラブのサウンドと逆の順序で、影響を与え、"whoosh" によってオブジェクトが所定の位置に向かっていることを通知します。 例: [MRTK_Move_End](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_Move_End.wav)

**描画**の相互作用には、ユーザーの手の動きによってボリュームが制御される、ループした永続的なサウンドが必要です。また、ユーザーの手が出てきたときには、完全に無音になっています。



### <a name="voice-interactions"></a>音声操作
音声のやり取りには、微妙な視覚要素があることがよくあります。 サウンドを使用して相互作用ステージを補強します。 ジェスチャや直接操作サウンドと区別するために、より多くの色調音を選択することを検討してください。

* 音声コマンドの確認には、正の音を**使用します**。 この時点では、増加している色調と主な音楽の間隔が効果的です。
* 音声コマンドの**エラー**に対して、より短い、負でない音の調子を使用します。 負の音は避けてください。代わりに、percussive のニュートラルサウンドを使用して、アプリケーションが相互作用から移動していることを伝えます。
* アプリケーションでウェイクワードを使用している場合は、デバイスが**リッスンを開始**したときに短時間で、すぐに聞こえ、アプリケーションがリッスンしている間は微妙なループサウンドを使用します。 

### <a name="notifications"></a>通知
通知は、アプリケーションの状態の変化や、ユーザーによって開始されていないその他のイベント (プロセスの完了、メッセージ、呼び出しなど) を伝えます。

Mixed reality では、移動するオブジェクトをユーザーのビューのフィールドから移動できます。 アニメーション化された**オブジェクト**には、オブジェクトとモーションの速度に依存する spatialized サウンドが付属しています。
* また、アニメーションの最後に spatialized サウンドを再生して、新しい位置をユーザーに通知することもできます。
* 段階的な移動では、移動中に "whoosh" サウンドを使用すると、ユーザーがオブジェクトを追跡できます。

多くの場合、**メッセージ通知**は数回通知されます。また、場合によっては、連続して発生することもあります。 非常に注意してください。または、過酷なことはありません。 ここでは、中間範囲の正の色調音が効果的です。

* 呼び出しは、携帯電話の着信音と同様の品質を持つ必要があります。 これらは通常、ユーザーが通話に応答するまで再生されるミュージックフレーズをループします。
* 音声通信の接続と切断には、短時間の色調音が必要です。 接続サウンドには、接続が成功したことを示す正の音が必要です。また、切断音は、呼び出しの完了を示すニュートラルサウンドである必要があります。

## <a name="spatialization"></a>Spatialization
Spatialization は、ステレオヘッドホンまたはスピーカーを使用して、混合世界にサウンドを配置します。

### <a name="which-sounds-should-i-spatialize"></a>どのようなサウンドを spatialize ばよいでしょうか。
空間位置を持つイベントに関連付けられている場合は、サウンドを spatialized する必要があります。 これには、UI、埋めを行う AI 音声、および視覚的インジケーターが含まれます。

Spatializing**ユーザーインターフェイス**要素は、ヘッドにロックされているステレオサウンドの数を制限することで、ユーザーの sonic "space" をまとめするのに役立ちます。 特に直接操作の対話では、音声フィードバックが spatialized されると、タッチ、グラブ、および解放がより自然になります。 ただし、これらの要素の距離の減衰については、以下を参照してください。

Spatializing の**視覚的なインジケーター**と埋めを行う AI の音声は、ユーザーがビューのフィールドの外部にあるときに、直感的にユーザーに通知します。
    
これに対して、  **_faceless_ AI の音声**と、適切に定義された空間の場所を持たないその他の要素の spatialization は避けてください。 関連するビジュアル要素のない Spatialization は、ユーザーが見つけられない視覚的な要素があると考えることができないようにします。

Spatialization を追加すると、CPU コストが発生します。 多くのアプリケーションは同時に2つのサウンドを再生します。 この場合、spatialization のコストはごくわずかです。 MRTK のフレームレートモニターを使用して、spatialization を追加した場合の影響を判断できます。 

### <a name="when-and-how-should-i-apply-distance-based-attenuation"></a>距離ベースの減衰を適用するタイミングと方法
物理的な世界では、遠く離れている音はより静かです。 オーディオエンジンは、ソースの距離に基づいてこの減衰をモデル化できます。 関連情報を通信するときは、距離ベースの減衰を使用します。

**視覚的なインジケーター**、アニメーション化された**ホログラム**、およびその他の情報音への距離は、通常、ユーザーに関連します。 距離ベースの減衰を使用して、このキューを直感的に提供します。
* 各ソースの減衰曲線を、混合ワールドスペースのサイズに合わせて調整します。 オーディオエンジンの既定の曲線は、多くの場合、非常に大きい (最大ハーフ kilometer) スペース用です。

ボタンやその他の対話の段階的な**段階**を補強する音は、減衰が適用されないようにする必要があります。 これらのサウンドの強化された効果は、通常、ボタンへの距離を伝えるよりも重要です。 バリエーションは、特にキーボードを使用すると、多くのボタンのクリックが連続して聞こえます。

### <a name="which-spatialization-technology-should-i-use"></a>どの spatialization テクノロジを使用すればよいでしょうか。
ヘッドホンまたは HoloLens スピーカーを使用する場合は、HRTF (head 関連の転送関数) ベースの spatialization テクノロジを使用します。 これらは、物理的な世界でのヘッドの周りにおけるサウンド伝達をモデル化します。 サウンドソースが一番上にある場合でも、サウンドは減衰と遅延によって遠くの耳に伝達されます。 これに対して、スピーカーパンは減衰にのみ依存し、サウンドが右側にあるときは左の耳に合計の減衰を適用します (逆の場合もあります)。 これは、通常の聴覚のリスナーでは不快になる可能性があり、1つの耳で聴覚障害があるリスナーにはアクセスできません。

## <a name="next-steps"></a>次のステップ
* [Unity で空間サウンドを使用する](spatial-sound-in-unity.md)
* [Roboraid のケーススタディ](case-study-using-spatial-sound-in-roboraid.md)
* [HoloTour のケーススタディ](case-study-spatial-sound-design-for-holotour.md)

