---
title: ケース スタディ - 3 HoloStudio UI と相互作用教訓を設計します。
description: HoloStudio UI との対話デザインの学習内容
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: 複合現実、HoloLens、HoloStudio、Windows
ms.openlocfilehash: e01e2ea888398e9982b56fd95f90ef0731ec6bc2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974826"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a>ケース スタディ - 3 HoloStudio UI と相互作用教訓を設計します。

[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) HoloLens の最初の Microsoft アプリのいずれかでした。 このためは、3 d UI の新しいベスト プラクティスと対話デザインを作成する必要があります。 多くのユーザーのテスト、プロトタイプ作成、および試行錯誤のようにしました。

この種類の調査を行うには自由に使用できるリソースのあるすべてのユーザー、HoloLens のアプリの UI との対話の設計に関する HoloStudio の開発中に学んだこと、シニア Holographic デザイナー、Marcus Ghaly、次の 3 つの共有がありましたのでことがわかっています。

## <a name="watch-the-video"></a>ビデオを見る

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a>問題 #1:ユーザーが作成、移動たくありませんでした。

もともと設計しました HoloStudio で workbench 四角形としてはるか現実の世界で見られるようにします。 問題は、ユーザーが机に向っているまたは、workbench の周囲に移動していないため、コンピューターの前に作業およびすべての辺から 3D の作成を調査している時にまだを維持するかを示すエクスペリエンスの有効期間があることです。

![HoloStudio で workbench の四角形のデザインはないユーザーが移動し、すべての辺から、作成を確認します。](images/rectangular-workbench-500px.jpg)

Workbench またはスタンバイを予定していた場所をオフに切り上げるには、「前面」ができるようにする情報を得ることがありました。 これをテストしましたが突然人起動内を移動し、自分で自分の作成を探索します。

![循環 workbench デザインでは、ユーザーの作成までわざわざ行かずを推奨します。](images/circular-workbench-500px.jpg)

**学習内容**

ユーザーの新機能について考えるを常になります。 HoloLens とその他のデバイスで実行できないことの優れた機能は、その物理容量を活用します。

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a>問題 2:モーダル ダイアログ ボックスが holographic フレーム外にあります。

場合によっては、ユーザーがアプリで、注意が必要なものから別の方向で表示されます。 PC では、ダイアログをポップアップだけができます。 が 3D 環境で他のユーザーの面でこれを実行する場合、ダイアログ ボックスがその方法で取得するように感じ、ことができます。 メッセージを読みする必要があるが、直感がこれから取得しようとするが。 この対応は、ゲームをプレイしているが、作業用に設計されたツールは遅くなります。

いくつかの異なる点を試用するには、後に最後に「バブルを考える」システムを使用して、ダイアログ ボックスの上に設置されたし、tendrils アプリケーションでは、注意が必要な場所を後に使用できるユーザーを追加します。 暗黙の方向性を把握できるように、ユーザーが移動するかを知っている tendrils パルスを行いました。

![「と考えるバブル」システムには、アプリで、注意が必要な場所にユーザーを先頭方向性を提供するパルスを発する tendrils が含まれています。](images/thought-bubble-500px.jpg)

**学習内容**

注意を払う必要があることをユーザーに警告を 3D ではるかに困難になります。 などのアテンション ディレクターを使用して[空間サウンド](spatial-sound.md)光線、ライトや、思考をバブルする可能性がユーザーに必要な場所。

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a>問題 3:その他のホログラムで UI をブロックすることがあります。

ユーザーがホログラムとその関連の UI コントロールを操作する場合も、別ホログラムがそれらの前にあるため、ビューからブロックされますがあります。 HoloStudio、開発中に試行錯誤を使用して、このソリューションに付属しました。

![HoloLens ソックスを着けずにユーザーとの間のもう 1 つのホログラムがある場合は、ホログラムに関連付けられた UI コントロールをブロックになることができます。](images/ui-blocked-500px.jpg)

私たちは、ブロックされるが見つかったでした。 離れたいたホログラム同時にしている間に近くするがコントロールを検索するユーザーの満足を取得できませんでしたをユーザーに近い UI コントロールを移動しようとしました。 ただし、最も近いホログラムの前にコントロールを移動、ユーザーに場合、その影響を与えている必要がありますホログラムからデタッチされたように感じました。

私たちは最後に、最終的に、UI コントロールをゴーストし、配置同じ距離にあるユーザーからは、関連付けられたホログラムとしてどちらも、接続されているため。 これにより、ユーザーが隠される場合でも、コントロールと対話します。

![ソリューション: コントロールとの対話を許可されているし、に影響を与えることがホログラムに接続されていると感じることの両方を UI コントロールは非実体化しました。](images/ghosting-ui-500px.jpg)

**学習内容**

ユーザーは、簡単に UI コントロールのアクセスがブロックされている場合でも、ユーザーがどこでも、ホログラム現実の世界でタスクを完了できるようにするメソッドを調べるためにできる必要があります。

## <a name="about-the-author"></a>執筆者紹介

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><b>Marcus Ghaly</b><br>シニア Holographic デザイナー @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>関連項目
* [本能的な操作](interaction-fundamentals.md)

 
