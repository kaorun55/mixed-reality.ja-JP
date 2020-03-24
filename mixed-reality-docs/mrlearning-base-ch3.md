---
title: 入門チュートリアル - 4. 動的なコンテンツの配置とソルバーの使用
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 2825f99f49eca6fd7277d02828bfe1bc3c23291a
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031221"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4.動的なコンテンツの配置とソルバーの使用
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

ホログラムは HoloLens 2 で現実のものとなります。ホログラムは直感的にユーザーを追跡し、滑らかで洗練された操作ができるように物理環境に配置されます。 このチュートリアルでは、複雑な空間配置シナリオを解決するために、「ソルバー」として知られる MRTK で使用できる配置ツールを使用して、ホログラムを動的に配置する方法について学習します。 MRTK では、ソルバーとは、UI 要素がシーン内で、あなた、ユーザー、他のゲーム オブジェクトを追跡できるようにするために使用される、スクリプトと動作のシステムです。 また、特定の場所にすばやくスナップして、アプリケーションをさらに直感的にするために使用することもできます。

## <a name="objectives"></a>目標

* MRTK ソルバーの紹介
* ソルバーを使用して、ボタン コレクションにユーザーを追跡させる
* ソルバーを使用して、ユーザーの追跡対象の手をゲーム オブジェクトに追跡させる

## <a name="location-of-solvers-in-the-mrtk"></a>MRTK でのソルバーの場所

 MRTK のソルバーは、MRTK SDK フォルダーにあります。 プロジェクトで使用可能なソルバーを表示するには、[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MixedRealityToolkit.SDK]**  >  **[Features]\(機能\)**  >  **[Utilities]\(ユーティリティ\)**  >  **[Solvers]\(ソルバー\)** に移動します。

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

このチュートリアルでは、Orbital ソルバーと Radial View ソルバーの実装について説明します。 MRTK で利用可能なすべてのソルバーの詳細については、[MRTK ドキュメント ポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の[ソルバー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)に関するガイドを参照してください。

## <a name="use-a-solver-to-follow-the-user"></a>ソルバーを使用してユーザーを追跡する
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

このセクションでは、前のチュートリアルで作成したボタン コレクションを拡張して、ユーザーの視線の方向に従うようにします。 さらに、ボタン コレクションが常に次のようになるようにソルバーを構成します。

* 左から右への自然な読み取りのために、ユーザーの読み取り方向に対して平行に回転する
* ユーザーの水平の視線の向きより少し下に配置することで、このチュートリアルの後の方で追加する他のオブジェクトを妨げないようにする
* ボタンを押しやすくするために、ユーザーからおよそ腕半分の距離に配置する

このためには、参照オブジェクトから、指定された位置とオフセットにオブジェクトをロックする **Orbital ソルバー**を使用します。

### <a name="1-add-the-orbital-solver"></a>1.Orbital ソルバーを追加する

[Hierarchy]\(階層\) ウィンドウで、 **[ButtonCollection]** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで、 **[Add Component]\(コンポーネントの追加\)** ボタンを使用して、**Orbital (Script)** コンポーネントを ButtonCollection オブジェクトに追加します。

> [!NOTE]
> ソルバー (この場合は Orbital (Script) コンポーネント) を追加すると、ソルバーで必要になる Solver Handler (Script) コンポーネントが自動的に追加されます。

### <a name="2-configure-the-orbital-solver"></a>2.Orbital ソルバーを構成する

**Solver Handler (Script)** コンポーネントを構成する

* **[Tracked Target Type]\(追跡対象の種類\)** が **[Head]\(頭\)** に設定されていることを確認します

**Orbital (Script)** コンポーネントを構成します。

* **[Orientation Type]\(向きの種類\)** が **[Follow Tracked Object]\(追跡対象オブジェクトに従う\)** に設定されていることを確認します
* **[Local Offset]\(ローカル オフセット\)** を X = 0、Y = 0、Z = 0 にリセットします
* **[World Offset]\(ワールド オフセット\)** を X = 0、Y = -0.4、Z = 0.3 に変更します

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a>3.エディター内シミュレーションを使用して Orbital ソルバーをテストする

[Play]\(再生\) ボタンを押してゲーム モードに入り、マウスの右ボタンを押したままにして視線方向を回転させます。次の点に注意してください。

* ButtonCollection の変換位置が、ソルバーの設定によって決定されるようになりました
* ソルバーの影響を受けない Cube は同じ位置のままになります

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> シーン ウィンドウにカメラの光線が表示されない場合は、ギズモ メニューが有効になっていることを確認してください。 ギズモ メニューと、それを使用してシーン ビューを最適化する方法の詳細については、Unity の <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">ギズモ メニュー</a>に関するドキュメントを参照してください。
>
> 上の図に示されているようにシーンとゲーム ウィンドウを並べて表示するには、ゲーム ウィンドウをシーン ウィンドウの右側にドラッグします。 ワークスペースのカスタマイズの詳細については、Unity の<a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">ワークスペースのカスタマイズ</a>に関するドキュメントを参照してください。

## <a name="enabling-objects-to-follow-tracked-hands"></a>オブジェクトに追跡対象の手を追跡させる

このセクションでは、前のチュートリアルで作成した Cube オブジェクトを、ユーザーの追跡対象の手 (特に右手の手首) を追跡するように構成します。 さらに、キューブが常に次のようになるようにソルバーを構成します。

* ユーザーの手の回転に合わせて向きを変える
* ユーザーの手首の位置に移動する

このためには、参照オブジェクトによって投影されるビュー円錐内にオブジェクトを維持する **Radial View ソルバー**を使用します。

### <a name="1-add-the-radial-view-solver"></a>1.Radial View ソルバーを追加する

[Hierarchy]\(階層\) ウィンドウで、 **[Cube]** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで、 **[Add Component]\(コンポーネントの追加\)** ボタンを使用して、**Radial View (Script)** コンポーネントを Cube オブジェクトに追加します。

### <a name="2-configure-the-radial-view-solver"></a>2.Radial View ソルバーを構成する

**Solver Handler (Script)** コンポーネントを構成する

* **[Tracked Target Type]\(追跡対象の種類\)** を **[Hand Joint]\(手の関節\)** に変更します
* **[Tracked Handness]\(追跡対象の手\)** を **[Right]\(右\)** に変更します
* **[Tracked Hand Joint]\(追跡対象の手の関節\)** を **[Wrist]\(手首\)** に変更します

**Radial View (Script)** コンポーネントを構成します。

* **[Reference Direction]\(参照方向\)** を **[Object Oriented]\(オブジェクトの向き\)** に変更してから、 **[Orient To Reference Direction]\(参照方向に向ける\)** チェックボックスをオンにします
* **[Min Distance]\(最小距離\)** および **[Max Distance]\(最大距離\)** を 0 に変更します

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a>3.エディター内シミュレーションを使用して Radial View ソルバーをテストする

[Play]\(再生\) ボタンを押してゲーム モードに入り、スペースキーを押して保持することで手を表示します。 マウス カーソルを移動して手を動かし、マウスの左ボタンを押したままにして手を回転させます。

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a>結論

このチュートリアルでは、MRTK ソルバーを使用して UI に直感的にユーザーを追跡させる方法を学びました。 また、ソルバーをオブジェクト (cube) に追加して、ユーザーの追跡対象の手を追跡させる方法についても学びました。 MRTK に含まれるこれらのソルバーや他のソルバーについて学ぶには、[MRTK ドキュメント ポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の[ソルバー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) に関するガイドを参照してください。

[次のチュートリアル:5.3D オブジェクトの操作](mrlearning-base-ch4.md)
