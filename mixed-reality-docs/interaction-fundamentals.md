---
title: 相互作用の基礎
description: HoloLens の間で構築したエクスペリエンス (第 1 世代) HoloLens 2、イマーシブ ヘッドセットを共有すると便利ですが見つかりましたいくつを書き留めるが開始されました。
author: rwinj
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 複合現実との対話を設計します。
ms.openlocfilehash: d594126529b6314a4706f8b6b6af856058c3280a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597551"
---
# <a name="interaction-fundamentals"></a>相互作用の基礎

HoloLens とイマーシブ ヘッドセットの間でエクスペリエンスを構築したら、下の点を共有すると便利ですが見つかりましたを書き始めたしました。 複合現実対話デザインの基本的な構成要素の役割も果たします。

## <a name="device-support"></a>デバイスのサポート

適用される使用可能な相互作用デザイン記事と、どのデバイスの種類または種類の概要を次に示します。
<br>

<table>

<th>
<tr>

<td style="width:150px;"><strong>入力</strong></td>
<td style="width:150px; text-align: center;"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></td>
<td style="width:150px; text-align: center;"><strong>HoloLens 2</strong></td>
<td style="width:150px; text-align: center;"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
</tr>
</th>
 
<tr>
<td> <a href="gestures.md">関節手</a></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td><td></td>

</tr><tr>
<td> <a href="gaze-targeting.md">監視対象とします。</a></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td><td style="text-align: center;"></td>
</tr><tr>
<td> <a href="gaze-targeting.md">視線の先を対象とします。</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gestures.md">ジェスチャ</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-design.md">音声のデザイン</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> ゲームパッド</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr>
<tr>
<td> <a href="motion-controllers.md">アニメーション コント ローラー</a></td><td></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>

</tr>
<th>
<tr>
<td style="width:150px;"><strong>概念と空間機能</strong></td>
<td style="width:150px; text-align: center;"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></td>
<td style="width:150px; text-align: center;"><strong>HoloLens 2</strong></td>
<td style="width:150px; text-align: center;"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
</tr>
</th>
<tr>

<td> <a href="spatial-sound-design.md">サウンドの空間の設計</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping-design.md">空間マッピングの設計</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="hologram.md">ホログラム</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>

</table>

## <a name="the-user-is-the-camera"></a>ユーザーは、カメラです。

![ユーザーは、カメラです。](images/useriscamera-640px.jpg)

に関する彼らの実数部と仮想世界に移動する場合に、ユーザーの観点の設計について常に考えます。

**一般的な質問**
* ユーザーに座って、リクライニングであること、または徒歩、エクスペリエンスを使用しているときにしますか。
* コンテンツは、別の位置にどのように調整しますか。
* ユーザー調整できますか。
* ユーザーが快適にアプリを使用できますか。

**ベスト プラクティス**
* ユーザーは、カメラであり、動作を制御します。 ドライブにできるようにします。
* 事実上、ユーザーを転送する必要がある場合は、不安を合わせた前庭に関する問題を機密性が高いものです。
* 短いアニメーションを使用して、
* ダウン/左/右からアニメーション化する、または Z の代わりにフェードイン
* 低下するタイミング
* バック グラウンドで世界を表示します。

**避けるべきこと**
* シェイク、カメラまたは 3DOF を意図的にロックしないでください (方向、翻訳のみ)、ユーザーが感じたことができます。
* 突然動きがありません。 ユーザーとの間にコンテンツを表示する必要がある場合、緩やかに変化かつ円滑目標の移動最大快適性します。 ユーザーは、それらに送信される大規模なメニューに対応します。
* 高速化、またはユーザーのカメラを有効にしないでください。 ユーザーは、機密性の高い (angular と直線) の高速化します。

## <a name="leverage-the-users-perspective"></a>ユーザーの視点を活用します。

ユーザーは、没入型および holographic デバイス ディスプレイでの複合現実の世界を参照してください。 この表示が呼び出された、HoloLens、 [holographic フレーム](holographic-frame.md)します。

2D の開発では、頻繁にアクセスされるコンテンツと設定を簡単にアクセスできるようにするための画面の隅に配置することもできます。 ただし、holographic のアプリでコンテンツをユーザーのビューの隅にない可能性がありますアクセスします。 ここでは、holographic のフレームの中央には、コンテンツの主な場所です。

ユーザーは、重要なイベントまたは即時表示外にあるオブジェクトを見つけやすいように説明する必要があります。 矢印、ライトの証跡、文字ヘッドの移動、吹き出し、ポインター、空間のサウンド、および音声プロンプトを使用して、アプリで重要なコンテンツをユーザーに役立つことができます。

ユーザーの快適性のために画面ロック コンテンツではなくすることをお勧めします。 ビュー内のコンテンツを保管する必要がある場合、世界中に配置および"tag-along"[スタート] メニューのようなコンテンツを作成します。 ユーザーの観点とプルのコンテンツは、環境で自然に感じられます。

![フレームの端に達すると、ユーザーのビューに依存して、[スタート] メニュー](images/tagalong-1000px.jpg)<br>
*フレームの端に達すると、ユーザーのビューに依存して、[スタート] メニュー*

これらがカットしないため、holographic フレーム内に収まる場合に、HoloLens ホログラムを実際と思われます。 ユーザーは、フレーム内のホログラムの境界を確認するために移動します。 HoloLens には、ユーザーのビュー内に収まるし、メイン アクションで、フォーカスを保持するように UI を簡略化する重要です。 イマーシブ ヘッドセットがデバイスのビューのフィールド内の永続的な仮想世界の錯覚を維持するために重要です。

## <a name="user-comfort"></a>快適性

最大値を確実に[快適性](comfort.md)ヘッド マウントのディスプレイでは作成し、人間が 3D 図形と自然にオブジェクトの相対位置を解釈する方法を模倣した方法でコンテンツを表示するには、設計者や開発者にとって重要です世界です。 物理の観点からも重要です首部分の腕疲れるモーションが不要なコンテンツをデザインします。

HoloLens のイマーシブ ヘッドセットを開発するかどうかが両方の目のビジュアルを表示するために重要です。 1 つ目のヘッドアップ ディスプレイをレンダリングのみによりにくくインターフェイスについては、ユーザーの目、脳に uneasiness の原因とします。

## <a name="share-your-experience"></a>体験を共有します。

使用して[実際のキャプチャを混合](mixed-reality-capture.md)ユーザーが写真や、いつでもエクスペリエンスのビデオをキャプチャできます。 スナップショットまたはビデオをお勧めする必要のあるアプリでのエクスペリエンスを検討してください。

## <a name="leverage-basic-ui-elements-of-the-windows-mixed-reality-home"></a>Windows Mixed Reality ホームの基本的な UI 要素を活用します。

Windows PC エクスペリエンスがデスクトップで始まるよう Windows Mixed Reality ホームから始まります。 [Windows Mixed Reality ホーム](navigating-the-windows-mixed-reality-home.md)を理解し、3 D の場所を移動します。 本質的な能力を活用します。 HoloLens、自宅は、実際の場所です。 イマーシブ ヘッドセット、自宅は仮想の場所です。

自宅は、[スタート] メニューを開き、アプリやコンテンツを配置に使用する場所もです。 複合現実のコンテンツを自宅に入力し、同時に複数のアプリを使用して、マルチタスクを実行できます。 自宅に配置することは、デバイスを再起動する場合でも、ままです。

## <a name="see-also"></a>関連項目
* [視線の先を対象とします。](gaze-targeting.md)
* [ジェスチャ](gestures.md)
* [音声のデザイン](voice-design.md)
* [アニメーション コント ローラー](motion-controllers.md)
* [サウンドの空間の設計](spatial-sound-design.md)
* [空間マッピングの設計](spatial-mapping-design.md)
* [快適性](comfort.md)
* [Windows Mixed Reality ホームに移動します。](navigating-the-windows-mixed-reality-home.md)
