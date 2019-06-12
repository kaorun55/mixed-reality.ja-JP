---
title: カスタムのホーム環境を追加します。
description: 提供 Windows Mixed Reality ホーム環境、だけでなく、作成と使用、独自に実験できます。
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、仮想現実、VR、MR、ホーム、カスタム環境、場所、cliff 家、skyloft、ユーザーの作成
ms.openlocfilehash: 8f5a3a1bdf5728260b0b7717c74a50f3356ca04a
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829640"
---
# <a name="add-custom-home-environments"></a>カスタムのホーム環境を追加します。

>[!NOTE]
>これは、試験的な機能です。 試してみてくださいと、楽しみが想定どおりすべて非常にうまくいかない場合も驚かないでください。 この機能とこれを使用して、関心の有効性を評価してについてお聞かせくださいエクスペリエンス (および見つかったバグ) で、[デベロッパー フォーラム](https://forums.hololens.com/categories/custom-home-environments)します。

以降では、 [Windows 10 April 2018 update](#release-notes-april-2018.md)、として使用するカスタム環境を ([スタート] メニューの) 場所の選択に追加することができます、試験的な機能を有効にしたこと、 [Windows Mixed Reality ホーム](#navigating-the-windows-mixed-reality-home.md). Windows Mixed Reality は、2 つの既定の環境、Cliff 家と Skyloft、自宅として選択することができます。 カスタム環境を作成すると、独自の作成とその一覧を展開できます。 弊社が使用できるようにこの初期状態の作成者と開発者が関心を評価し、世界の種類を作成、およびさまざまなオーサリング ツールを操作する方法を理解するを参照してください。

その teleporting わかりますカスタム環境を使用する場合、アプリと対話して、ホログラムを配置することは、Cliff 家と Skyloft で同様は機能します。 ファンタジー ランドス ケープで web を参照するかと同じ市を塗りつぶすホログラム -、可能性は無限大です!

## <a name="device-support"></a>デバイスのサポート

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>機能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
    </tr>
     <tr>
        <td>カスタムのホーム環境</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a>サンプル環境をしようとしてください。

カスタム ホーム環境の創造的な可能性のいくつかを示すサンプル環境を作成しました。 試してみるにこれらの手順に従います。
1. [このサンプルのファンタジー島環境をダウンロード](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe)(自己解凍実行可能ファイルにリンクがポイント)。

    ![Fantasy 島サンプル環境](images/FantasyLand.jpg)<br>
    *Fantasy 島サンプル環境*<br>

2. 実行、 **Fantasy_Island.exe**ダウンロードしたファイル。

    > [!NOTE]
    > (次のような) web からダウンロードされると .exe ファイルを実行しようとすると、「Windows は、お使いの PC を保護」のポップアップが発生する可能性があります。 このポップアップから Fantasy_Island.exe を実行する選択**詳細については**し**実行**します。 これを信頼したくないファイルのダウンロードを防ぐためにこのセキュリティ設定は、ファイルのソースを信頼するときに、のみこのオプションを選択してください。

3. 開いている**ファイル エクスプ ローラー** 、アドレス バーで、次を貼り付けることによって、環境フォルダーに移動します:`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`します。
4. このフォルダーにダウンロードしたサンプル環境をコピーします。
5. 再起動**現実ポータルを混合**します。 これにより、場所の選択で環境の一覧が更新されます。
6. ヘッドセットに配置します。 自宅であなたを開く、 **[スタート] メニュー**コント ローラーの Windows を使用してボタンをクリックします。
7. 選択、**場所**ホーム環境を選択してピン留めされたアプリの一覧の上のアイコン。
8. 場所の一覧でダウンロードしたファンタジー島環境が表示されます。 選択**ファンタジー島**新しいカスタム ホーム環境を入力します。

## <a name="creating-your-own-custom-environment"></a>独自のカスタム環境を作成します。

に加えて、サンプル環境を使用して、ソフトウェアの編集、お気に入りの 3D を使用して、独自のカスタム環境をエクスポートできます。 

### <a name="modeling-guidelines"></a>モデリングのガイドライン

お客様の環境をモデル化する場合は、次の推奨事項に注意してください。 ユーザーを産み落とす believably 規模の世界で正しい向きにすることができます。

1. ユーザーは、原点の周囲の生成に必要な場所に 0,0,0 は center で生成されます。
2. 世界規模で資産を作成できるように、メーター作業単位を設定してください。
3. アップ軸は、"Y"に設定する必要があります。
4. 資産は、正の Z 軸方向に"forward"に直面する必要があります。
5. すべてのメッシュは、結合する必要はありませんが、リソースが限られたデバイスを対象としている場合をお勧めします。

### <a name="exporting-your-environment"></a>お客様の環境をエクスポートします。

Windows Mixed Reality は、環境の資産の配信形式としてバイナリ glTF (.glb) に依存します。 glTF は、使用料無料のオープン標準の 3D アセットの配信 Khronos グループによって管理されます。 Windows アプリおよびエクスペリエンスの間での形式については、マイクロソフトのサポートはため glTF の進化に伴って相互運用可能な 3D コンテンツの業界標準として、します。

カスタムのホーム環境として使用するアセットをエクスポートする最初の手順は、glTF 2.0 モデルを生成しています。 GlTF ワーキング グループの管理、[サポートされているエクスポーターとコンバーターの一覧](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters)glTF 2.0 モデルを作成します。 最初に、このページに記載されているプログラムのいずれかを使用して作成し、glTF 2.0 モデルをエクスポートまたはサポートされているコンバーターのいずれかを使用して既存のモデルに変換します。

さらに、チェック アウト[この便利な記事](https://www.khronos.org/blog/art-pipeline-for-gltf)Blender や 3 ds から glTF モデルをエクスポートするため、アート ワークフローの概要を説明する直接 Max です。 

### <a name="environment-limits"></a>環境の制限

すべての環境は、< 256 mb である必要があります。 256 mb を超える環境は、ユーザーを囲む既定スカイ ボックスだけで、空の世界にフォールバックを読み込みは失敗します。 ください、モデルを作成するときに、このファイルのサイズ制限に注意してください。 さらに、以下に示すように、WindowsMRAssetConverter を使用して環境を最適化する場合は、できなければ、オプティマイザー、大きなファイルサイズが読み込みも高速のテクスチャが作成されると、テクスチャのサイズが増加します。 

### <a name="optimizing-your-environment"></a>お客様の環境を最適化します。

Windows Mixed Reality は、いくつかの環境の読み込み時間が大幅に低下する省略可能な最適化をサポートします。 これは、読み込み中にタイムアウトになる場合がありますが、多くのテクスチャでは、使用環境にとって特に重要です。 一般に、すべての資産に対してこの手順をお勧め、ただし、いくつか、または低解像度のテクスチャで小規模な環境常に必要としないことです。 

このプロセスを簡単に作成しました、 [Windows Mixed Reality 資産コンバーター (GitHub で入手できます)](https://github.com/Microsoft/glTF-Toolkit/releases)最適化を実行します。 このツールは、追加のテクスチャのパッキング、圧縮および解像度のスケールを実行することによって、標準の 2.0 glTF や .glb を最適化するために、Microsoft glTF toolkit で使用可能なユーティリティのセットを使用します。 

コンバーターには、さまざまな最適化の正確な動作を調整するためのフラグがサポートされています。 最良の結果を次のフラグ付きの実行をお勧めします。

Flag|推奨値|説明
---|---|---
-max-texture-size|1024 または 2048| このテクスチャの品質を向上させるために調整、既定値は 512 x 512 します。 大きい値は、環境のファイル サイズに影響が大幅にことに注意してください。 保管しておいて、256 mb の制限に注意してください。
最小バージョン|1803|カスタム環境は windows のバージョンでのみサポートされます > 1803 を = です。 このフラグは以前のバージョンのテクスチャを削除して、最終的な資産のファイル サイズを縮小

例:

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a>環境をテストします。

最終的な .glb 環境を作成したら、ヘッドセットでテストを実行する準備ができました。 手順 2. で始まり、 [「サンプル環境をしようとした」](#trying-a-sample-environment)ホーム複合現実として、カスタム環境を使用するセクション。 

## <a name="feedback"></a>Feedback

この実験的な機能を評価して、私たちは、バグが発生する可能性のカスタム環境を使用している方法に興味を持つと、機能方法を指定してください。 作成すると、カスタム ホーム環境を使用して、あらゆるフィードバックを共有してください、[デベロッパー フォーラム](https://forums.hololens.com/categories/custom-home-environments)します。

## <a name="troubleshooting-and-tips"></a>トラブルシューティングとヒント

### <a name="how-do-i-change-the-name-of-the-environment"></a>環境の名前を変更する方法はありますか

[環境] フォルダー内のファイル名は、場所の選択に適用されます。 環境の名前を変更するには、は、単に名前変更、環境は、ファイル名をし、し、Mixed Reality ポータルを再起動します。

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a>マイ プレース ピッカーからのカスタム環境を削除する方法

カスタム環境を削除するには、お使いの PC 上のフォルダーに環境を開きます (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) し、環境を削除します。 Mixed Reality ポータルを再起動するとこの環境は不要になった場所ピッカーに表示されます。 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a>私のお気に入りのカスタム環境を既定する方法は?

現在、既定の環境を変更することはできません。 混合の現実ポータルを再起動するたびに Cliff 家環境に返されるされます。 

### <a name="i-spawn-into-a-blank-space"></a>空白の領域に生成します。

Windows Mixed Reality [256 mb を超える環境をサポートしていない](#environment-limits)します。 環境では、この制限を超えているときに、モデルのない空のスカイ ボックスに表示されます。

### <a name="it-takes-a-long-time-to-load-my-environment"></a>自分の環境を読み込みに長い時間がかかる

省略可能な最適化は、読み込みも高速にする環境に追加できます。 参照してください[「環境の最適化」](#optimizing-your-environment)詳細についてはします。

### <a name="the-scale-of-my-environment-is-incorrect"></a>自分の環境内の小数点以下桁数が正しくありません。

Windows Mixed Reality 環境の読み込み時に 1 メートルに glTF 単位の平行移動します。 環境内で、予期しないスケールを再確認することを確認する、エクスポーターが読み込まれる場合は、1 m 規模でモデル化をでしょう。 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a>私の環境での生成場所が正しくありません。

既定の生成場所は、環境で 0,0,0 にあります。 その現在できない配信元の生成に必要なポイントに配置されると、環境をエクスポートすることによって、起動ポイントを変更する必要がありますので、この場所をカスタマイズします。

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a>環境内の適切なオーディオとは言えません

カスタム環境を作成するときに作成した物理領域に一致しない音響学のレンダリング シミュレーション使用します。 サウンドが間違った方向から取得したものし、思われるかもしれませんがこもった感じです。 

## <a name="see-also"></a>関連項目
* [実際にはホームを混合するウィンドウを移動します。](#navigating-the-windows-mixed-reality-home.md)
* [Windows (GitHub 上) 資産コンバーターを現実の混在](https://github.com/Microsoft/glTF-Toolkit/releases)

