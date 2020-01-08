---
title: MRTK 101-基本的な対話に Mixed Reality Toolkit Unity を使用する方法 (HoloLens 2、HoloLens、Windows Mixed Reality、Open VR)
description: 基本的な対話に Mixed Reality Toolkit Unity を使用する方法 (HoloLens 2、HoloLens、Windows Mixed Reality、Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens、MRTK、Mixed Reality Toolkit、Windows Mixed Reality、design、sample app、controls
ms.openlocfilehash: ad9d2755522c2610ae051fa61f96605e49404d2d
ms.sourcegitcommit: 5054f5c23965ce56599cb29ac9d9c6e48812dabd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/03/2020
ms.locfileid: "75623505"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a>MRTK 101: 基本的な対話に Mixed Reality Toolkit Unity を使用する方法 (HoloLens 2、HoloLens、Windows Mixed Reality、Open VR)

![MRTK](images/MRTK101/MRTK101Cover.png)

MRTK を使用して、mixed reality で最も広く使用されている一般的な相互作用パターンを実現する方法について説明します。

- Unity エディターで入力の相互作用をシミュレートする方法
- オブジェクトを取得および移動する方法
- オブジェクトのサイズを変更する方法
- 有効桁数を使用してオブジェクトを移動または回転する方法
- オブジェクトを入力イベントに応答させる方法
- 視覚的フィードバックを追加する方法
- オーディオフィードバックを追加する方法
- HoloLens 2 スタイルボタン prefabs の使用方法
- オブジェクトをフォローする方法
- オブジェクトをどのように表示するか

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a>Unity エディターで入力の相互作用をシミュレートする方法
MRTK は、エディター内入力のシミュレーションをサポートしています。 Unity の [再生] ボタンをクリックしてシーンを実行するだけです。 入力をシミュレートするには、これらのキーを使用します。
W、A、S、D キーを押して、カメラを移動します。
マウスの右ボタンを押したまま、マウスを動かして移動します。
シミュレートされたハンドを表示するには、スペースバー (右側) または左 Shift キー (左側) を押して、シミュレートされたハンドを保持します。 T キーまたは Y キーを押して、シミュレートされたハンドを回転します。

- [MRTK のドキュメントで入力シミュレーションの詳細を確認する](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a>オブジェクトを取得および移動する方法
オブジェクトを grabbable にするには、次の2つのスクリプトを割り当てます。 ManipulationHandler.cs と NearInteractionGrabbable (トレーラー型の追跡入力を使用した直接グラブ) では、near と far の相互作用の両方がサポートされています。 オブジェクトを取得および移動するには、HoloLens 2 の手による追跡入力 (near)、ハンドレイ (遠く)、モーションコントローラーのビーム (遠く)、HoloLens を見つめたカーソル & エアタップ (遠く) を使用します。

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a>オブジェクトのサイズを変更する方法
ManipulationHandler.cs は、2つのを持つスケール/回転をサポートしています。 これは、HoloLens 2 の手入力、HoloLens 1 の宝石となるジェスチャ入力、Windows Mixed Reality のイマーシブヘッドセットのモーションコントローラー入力など、さまざまな入力の種類で機能します。

- [操作ハンドラーの詳細については、MRTK のドキュメントを参照してください。](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a>有効桁数を使用してオブジェクトを移動または回転する方法
BoundingBox.cs をオブジェクトに割り当てて、オブジェクトを拡大縮小および回転するためのインターフェイスである境界ボックスを使用します。 既定では、HoloLens 1 スタイルの青いハンドルとワイヤが表示されます。 HoloLens 2 のスタイル近接に基づくアニメーションハンドルを使用するには、prefabs と素材を割り当てる必要があります。 構成の詳細については、[境界ボックスのドキュメント](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)と BoundingBoxExamples シーンを参照してください。

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [詳細については、MRTK のドキュメントの境界ボックスに関するページを参照してください。](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a>オブジェクトを入力イベントに応答させる方法
PointerHandler.cs をオブジェクトに割り当てます。 インスペクターでは、イベント Onポインタ Down ()、Onポインタ Up ()、Onポインターをクリックした ()、Onポインターをドラッグして ()、スクリプトでこれらのイベントを使用することができます。

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [入力システムの詳細については、MRTK のドキュメントを参照してください。](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a>視覚的フィードバックを追加する方法
Interactable.cs をオブジェクトに割り当てます。 インスペクターで、新しいテーマを作成します。 対話型のテーマプロファイルを使用すると、利用可能なすべての入力対話状態に視覚的フィードバックを簡単に追加できます。

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


対話型には、シェーダーのテーマを含むさまざまな種類のテーマが用意されています。これにより、相互作用状態ごとにシェーダーのプロパティを制御できます。

- [対話型の詳細については、MRTK のドキュメントを参照してください。](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

視覚的なフィードバックのためのもう1つの重要な構成要素は、MRTK Standard Shader です。 MRTK Standard Shader を使用すると、ホバー光や近接光などの視覚的なフィードバック効果を簡単に追加できます。 MRTK Standard shader では Unity Standard shader よりも計算が大幅に減少するため、パフォーマンスに優れたエクスペリエンスを実現できます。

新しい素材を作成し、シェーダー ' Mixed Reality Toolkit > Standard ' を選択します。 または、MRTK Standard Shader を使用する既存のマテリアルの1つを選択することもできます。

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [Mrtk のドキュメントの MRTK Standard Shader の詳細については、こちらを参照してください。](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a>オーディオフィードバックを追加する方法
AudioSource をオブジェクトに追加します。 次に、入力イベントを公開するスクリプト (例: Interactable.cs または PointerHandler.cs) で、オブジェクトをイベントに割り当て、AudioSource. PlayOneShot () を選択します。 オーディオクリップを使用するか、MRTK のオーディオアセットから1つを選択することができます。

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a>HoloLens 2 スタイルボタン prefabs の使用方法
MRTK には、さまざまな種類の HoloLens 2 のシェル (OS) スタイルボタンが用意されています。 これにより、近接光、フィードバックの圧縮、ボタン画面に対する ripple 効果などの洗練されたビジュアルが提供されます。

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

HoloLens 2 style pressable button prefab の1つをシーンにドラッグアンドドロップするだけです。 Prefab は、上記で導入された Interactable.cs を使用します。 対話型の OnClick () などの公開されたイベントを使用して、アクションをトリガーできます。

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [詳細については、MRTK のドキュメントのボタン prefabs に関するページを参照してください。](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a>オブジェクトをフォローする方法
RadialView.cs スクリプトをオブジェクトに割り当てます。 これは、3D 空間でさまざまな種類のオブジェクトの配置を実現するための、ソルバースクリプトシリーズの一部です。 SolverHandler.cs が自動的に追加されます。
次に示すのは、HoloLens シェルの [スタート] メニューと同じように、"遅延した後の" タグの動作を実現するための、放射 Alview 構成の例です。 最小/最大距離および最小/最大ビューの角度を指定できます。 次の例では、オブジェクトを 0.4 m と 0.8 m の範囲の15°以内に配置しています。 Lerp 時刻値を調整して、位置指定更新を高速または低速にします。

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [詳細については、MRTK のドキュメントを参照してください。](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a>オブジェクトをどのように表示するか
Billboard.cs スクリプトをオブジェクトに割り当てます。 位置に関係なく、常に表示されます。 [ピボット軸] オプションを指定できます。

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


Mixed reality のすばらしいエクスペリエンスを作成する準備はできましたか? MRTK と mixed reality の詳細については、以下のページを参照してください。

## <a name="about-the-author"></a>執筆者紹介

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>駐車中</b><br>UX デザイナーの @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>「

* [Mixed Reality Toolkit-Unity (MRTK) GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [MRTK ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [MRTK でのはじめに](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [HoloToolkit to MRTK 移植ガイドライン](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
