---
title: 導入事例 - マイ最初の年、HoloLens の設計チーム
description: 2016 年 1 月で HoloLens デザイン チームに参加するときに開始、3 D ワールドに 2D flatland からへ。
author: designnomad
ms.author: haejinl
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、設計、編集、パーソナル
ms.openlocfilehash: 050645e6096559a4f37b033e5ddfdc5444039c08
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873952"
---
# <a name="case-study---my-first-year-on-the-hololens-design-team"></a>導入事例 - マイ最初の年、HoloLens の設計チーム

2016 年 1 月で HoloLens デザイン チームに参加するときに開始、3 D ワールドに 2D flatland からへ。 チームに参加する前に 3D の設計でごくわずかなの経験がありました。 千マイルの今回はその最初の手順が閏日点を除いて、1 つの手順を以降の旅の中国語ことわざのようなことでした。

![2D から 3D にクラウドがかかっています](images/2D_to_3D-800px.gif)<br>
*2D から 3D にクラウドがかかっています*

> *"感じましたなものとして、車を導く方法を知ることがなく主導権をジャンプする必要があります。負荷がかかることが怖いまだ非常にフォーカスがあるとします"。*<br>
> — Hae Jin Lee

過去の年にしまいましたスキルと知識を同じですが、まだ学ぶ速度。 ここでは、4 つの観測を 2D から 3D の相互作用のデザイナーへの移行は、文書化ビデオ チュートリアルを作成しました。 私の経験を他のデザイナーを 3D に移行を実行するきっかけと思います。

## <a name="good-bye-frame-hello-spatial--diegetic-ui"></a>終わりのフレーム。 空間こんにちは/diegetic UI

ポスター、雑誌、web サイト、またはアプリの画面をデザインするときに、定義済みのフレーム (通常は四角形) は、すべての問題のための定数をしました。 HoloLens、またはその他の VR デバイスでは、この投稿を読んでいる場合を除いて、 *、外部からこれを見て*2D 画面のフレーム内で保護された安全に使用します。 コンテンツは、外部にします。 ただし、Mixed Reality ヘッドセット*フレームを排除*し徹底解剖からコンテンツを追いコンテンツの領域内であるため、します。

概念的には、これを理解しましたが、単に 2D の考え方を 3D 空間に転送の過ちを犯しては最初に。 明らかにしていないため、うまく動作 3D 空間がある (ユーザーのヘッドの移動に基づく) ビューの変更など、独自の一意のプロパティと[快適性の要件が異なる](https://www.youtube.com/watch?v=-606oZKLa_s/)(を使用して、人間とデバイスのプロパティに基づくその)。 たとえばを 2D の UI デザイン領域に画面の隅にある UI 要素にロックは非常に一般的なパターンがこの HUD (ヘッドをディスプレイ) スタイルの UI が MR/VR エクスペリエンスで自然に感じはありません。スペースにユーザーの immersion の妨げになってし、ユーザーの不安をによりします。 処分するたい場合は、眼鏡の面倒な場合、ほこりパーティクルをできるようになります。 時間の経過と共に、3 D 空間でコンテンツを配置して、コンテンツに従って相対の固定距離にあるユーザーは、本文ロックの動作を追加するより自然な感じることがわかりました。

![本文ロック](images/bodylockedtagalong.gif)<br>
*本文ロック*

<br>

![世界ロック](images/worldlocked.gif)<br>
*世界ロック*

### <a name="fragments-an-example-of-great-diegetic-ui"></a>フラグメント:優れた Diegetic UI の例

[フラグメント](https://www.microsoft.com/p/fragments/9nblggh5ggm8)、によって開発された最初のユーザーの犯罪 thriller [Asobo Studio](http://www.asobostudio.com/)の HoloLens は優れた Diegetic UI を示します。 このゲームでは、ユーザーはメインの謎を解決しようとした探偵文字になります。 この謎を解決するために極めて重要なヒント、ユーザーの物理的なルームでのさまざまな箇所を取得、多くの場合、独自の既存のではなく、架空のオブジェクトの内部に埋め込まれたです。 UI Asobo チームが巧みに仮想の文字の視線方向、サウンド、光、およびガイド (ヒントの場所を指す矢印など) を含む多くのキューを使用するために、UI の本文がロックされているよりも見つけにくいする傾向にありますこの diegetic ユーザーの注意を取得します。

![フラグメントの Diegetic UI の例](images/fragments-game-example-1.jpg)<br>
*フラグメントの Diegetic UI の例*

### <a name="observations-about-diegetic-ui"></a>観測 diegetic UI について

空間の (両方本文ロックおよび世界ロック) の UI と diegetic UI は、独自の長所と短所があります。 デザイナーをできるだけ多く MR/VR アプリを試すおよびメソッドを配置するさまざまな UI の独自の理解と感情を開発することをお勧めします。

## <a name="the-return-of-skeuomorphism-and-magical-interaction"></a>恣意と魔法のような操作の戻り値

恣意、現実世界のオブジェクトの形状を模倣したデジタル インターフェイスがありません「クール」デザイン業界での過去の 5 ~ 7 年間です。 最後に、Apple は、iOS 7 でフラット デザインする方法を指定、ときに恣意がインターフェイスのデザイン方法論として最後に停止しているように思われました。 次に、新しいメディア、MR/VR ヘッドセットが市場に到着し、恣意が再度返されるように見えます。 : )

### <a name="job-simulator-an-example-of-skeuomorphic-vr-design"></a>ジョブ シミュレーターの場合:Skeuomorphic VR 設計の例

[ジョブのシミュレーター](http://jobsimulatorgame.com/)、という風変わりなゲームを開発した[Owlchemy Labs](https://owlchemylabs.com/) skeuomorphic VR デザインの最も一般的な例の 1 つです。 このゲームでプレーヤーは将来、ロボットは人間を置き換えるし、人間には、1 つの異なる 4 つのジョブでの日常のタスクを実行するは、ように感じること博物館を参照してください転送します。自動整備士、グルメ Chef、ストアのクラークまたはオフィス ワーカーです。

恣意の利点は明らかです。 使い慣れた環境とこのゲーム内のオブジェクトより快適さと仮想空白文字であると思われる新しい VR のユーザーに役立ちます。 また、オブジェクトおよび対応する物理反応と使い慣れた知識と動作を関連付けることによってコントロールがされているように感じになります。 たとえば、コーヒーを飲み、人だけ必要がありますコーヒー マシンをボタンを押して、cup ハンドルをドラッグして現実の世界でしまうと、口に傾けます。

![ジョブのシミュレーター](images/job-simulator.gif)<br>
*ジョブのシミュレーター*

MR/VR がまだ開発中であるためは恣意度を使用して MR/VR テクノロジを説明して、世界各地のより多くのユーザーに紹介するために必要なは。 さらに、恣意または現実的な表現を使用してが手術またはフライト シミュレーションなどのアプリケーションの特定の種類な役に立ちます可能性があります。 これらのアプリの目的は、開発および現実の世界で直接適用できる特定のスキルを絞り込むであるために近ければ近いほどシミュレーションが実際には、譲渡できません。 またより知識は。

その恣意がのみ 1 つの方法に注意してください。 MR/VR 世界中の可能性がはるかに超えて、およびデザイナーが魔法のようなハイパー自然の相互作用を作成するよう努力する必要があります: MR VR/世界で一意に可能な新しいアフォーします。 開始、として基本的な自分たちの希望を満たすためにユーザーを有効にする通常のオブジェクトへの魔法のような電源の追加を検討してください: teleportation 周到など。

![Doraemon の魔法のようなドア (左) と Ruby slippers(right)](images/doraemons-magical-door-and-ruby-slippers.jpg)<br>
*Doraemon の魔法のようなドア (左) と ruby slippers(right)*

### <a name="observations-about-skeuomorphism-in-vr"></a>VR で恣意の所見

「Anywhere ドア」Doraemon、オズのハリー ポッターで「Maurader のマップ」の「Ruby スリッパ」では、人気のある架空の魔法のような能力の通常のオブジェクトの例が数多く存在します。 これらの魔法のようなオブジェクトでは、実世界と新機能となる可能性の間、すばらしい機能間の接続を視覚化するのに役立ちます。 魔法のようなまたは surreal を設計するときに、機能、エンターテインメントのバランスを取るように 1 つのオブジェクトが必要に留意してください。 新奇のための純粋な魔法のようなものを作成するという誘惑に注意してください。

## <a name="understanding-different-input-methods"></a>さまざまな入力方法を理解します。

中程度の 2D のデザイン時はタッチ、マウス、および入力のキーボードの相互作用に注目する必要があります。 MR/VR デザイン領域で、当社の本文になり、インターフェイス、ユーザーは入力方式の広範な選択を使用することが: 音声、視線、ジェスチャ、 [6 自由度のコント ローラー](https://en.wikipedia.org/wiki/Six_degrees_of_freedom)、しより直感的な直接接続に余裕がある gloves仮想オブジェクトです。

![HoloLens で使用できる入力](images/inputs.jpg)<br>
*HoloLens で使用できる入力*

> *「すべてが、何かに最適と他の情報を最も不適切です。」*<br>
> — [Bill Buxton](https://www.billbuxton.com/)

たとえば、ッドマウント デバイスでのベア手の形とカメラのセンサーを使用して入力ジェスチャをコント ローラーを保持または sweaty gloves、ソックスを着けずにからユーザーの手の解放が頻繁に使用される物理疲労 (別名、gorilla arm) が発生することができます。 ユーザーは、視野; 内で維持する必要があります。カメラは、手を参照してくださいことはできません、手が使用できません。

音声入力は切り抜けるには 1 つのコマンドを使用して入れ子になったメニューにユーザーを許容するために、複雑なタスクを走査 (たとえば、"Show me による Laika studio 映画") でも非常に経済的なその他のモダリティと組み合わせると (など、使用するコマンドの"直面 me"、。ホログラム ユーザーが見るユーザーの方に)。 ただし、音声入力ノイズの多い環境で正常に機能しない、または非常に非表示の領域で適切でない可能性があります。

ジェスチャと音声認識、だけでなく携帯用追跡コント ローラー (、Oculus タッチなど、Vive など) に使いやすく、正確で活用してユーザーのために非常に一般的な方法で入力は[proprioception](https://en.wikipedia.org/wiki/Proprioception)、パッシブ ハプティクス的な手掛かりを提供します。ただし、これらのメリットは、ベア手にして、完全な本の指の追跡を使用することができなくての犠牲が伴います。

![Senso (左) と Manus VR(Right)](images/senso-and-manus-vr.jpg)<br>
*Senso (左) と Manus VR (右)*

中されません一般的なコント ローラーとして、gloves は、もう一度、MR/VR wave に協力してくれた勢いが。 ヘッドセットを EEG または採用されているのでのセンサーを統合することで仮想環境のインターフェイスとして乗れずに脳/注意入力を開始した最も最近、(たとえば、 [MindMaze VR](http://www.mindmaze.com/))。

### <a name="observations-about-input-methods"></a>入力方法の所見

これらは、単なる MR/VR の市場で使用可能な入力デバイスのサンプルです。 引き続き、業界の成熟して同意したら、ベスト プラクティスまでの急増にします。 それまでは、デザイナーは常に新しい入力デバイスの認識と、特定のプロジェクトの特定の入力方法に精通する必要があります。 デザイナーは、クリエイティブなソリューションものデバイスの長所を再生中に、制限内で検索する必要があります。

## <a name="sketch-the-scene-and-test-in-the-headset"></a>シーンをスケッチし、ヘッドセットのテスト

私は、2 D で作業した、ときに、コンテンツだけはスケッチほとんどの場合。 ただし、複合現実の領域で十分でした。 ユーザーと仮想オブジェクト間のリレーションシップを想像するシーン全体をスケッチする必要があります。 シーンをスケッチする開始は自分の空間的な考え方をする[シネマ 4 D](https://www.maxon.net/en/products/cinema-4d/overview/)場合がありますでプロトタイプを作成する単純な資産を作成[Maya](http://www.autodesk.com/products/maya/overview/)します。 HoloLens チームに参加する前にいずれかのプログラムを使用したことはありませんし、私もは、初心者がこれら 3D プログラムを使用する確実に役立ったなどの新しい用語、慣れてできます[シェーダー](https://en.wikipedia.org/wiki/Shader)と[IK (逆関数キネマティクス)](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-07C3BA47-32BB-477B-B6C5-1090E5C9B81C-htm.html/)します。

**"3d シーンをスケッチしたはどの程度近いかに関係なくヘッドセットで実際の経験がほとんどないスケッチの場合と同じです。その理由はターゲット ヘッドセットにシーンをテストすることが重要"— Hae Jin Lee**

HoloLens のプロトタイプ作成にあるすべてのチュートリアルを試しました[Mixed Reality チュートリアル](tutorials.md)を開始します。 再生を開始した、 [HoloToolkit.Unity](https://github.com/Microsoft/HoloToolkit-Unity/) holographic アプリケーションの開発を加速する開発者にマイクロソフトが提供しています。 何かでスタックしたに自分の質問を投稿[HoloLens の質問と回答フォーラム](https://forums.hololens.com/categories/questions-and-answers/)します。

HoloLens のプロトタイプ作成の基本的な理解を取得するには、後に他の非占めるを自分でプロトタイプを支援する考えました。 したがって、HoloLens を使用して単純な光線を開発する方法を示すビデオ チュートリアルがしました。 簡単に説明の基本概念をでも HoloLens の開発に 0 個の経験があれば、作業を進めるにできる必要があります。

<br>

>[!VIDEO https://www.youtube.com/embed/58612RT2CT8]
*自分のような非プログラマのためこの簡単なチュートリアルを行いました。*

コースを VR プロトタイプを作成しました[VR Dev 学校](http://learn.vrdev.school/)、所要時間も[仮想現実の 3D コンテンツの作成](https://www.lynda.com/Unreal-Engine-tutorials/3D-Content-Creation-Virtual-Reality/482055-2.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3aVirtual+Reality+%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2/)Lynda.com にします。 VR Dev school には、コーディングの詳細な知識と詳細 Lynda コース提供 me VR の資産を作成する便利な概要が提供されています。

## <a name="take-the-leap"></a>移行を実行します。

1 年前、落としたような少し反響は大変大きかったのです。 今すぐお伝えできます労力を費やす価値の 100% が。 MR/VR は子供の頃の中でも、非常に多くの興味深い可能性を実現するを待機しています。 インスピレーションと残念な気分を将来の設計に 1 つのごく一部の再生できるようにします。 3D 空間に旅に合流を願っています!

## <a name="about-the-author"></a>執筆者紹介

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Hae Jin Lee" width="60" height="60" src="images/haejinlee.jpg"></td>
<td style="border-style: none"><b>Hae Jin Lee</b><br>UX デザイナー @Microsoft</td>
</tr>
</table>

 
