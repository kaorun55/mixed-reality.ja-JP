---
title: Azure Spatial Anchors チュートリアル - 3. Azure Spatial Anchors のフィードバックの表示
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 62ce1151837a345dea1bea4a8bea275cc851b9bd
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/26/2020
ms.locfileid: "83866902"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3.Azure Spatial Anchors のフィードバックの表示

このチュートリアルでは、Azure Spatial Anchors (ASA) を使用する場合のアンカーの検出、イベント、および状態に関するフィードバックをユーザーに提供する方法について説明します。

## <a name="objectives"></a>目標

* 現在の ASA セッションに関する重要な情報を表示する UI パネルを設定する方法を理解する
* ASA SDK によってユーザーに提供されるフィードバック要素を理解および確認する

## <a name="set-up-asa-feedback-ui-panel"></a>ASA フィードバック UI パネルの設定

[Hierarchy]\(階層\) ウィンドウで、 **[Instructions]\(指示\)**  >  **[TextContent]** オブジェクトを右クリックし、 **[3D Object]\(3D オブジェクト\)**  >  **[Text - TextMeshPro]\(テキスト - TextMeshPro\)** を選択して、[Instructions]\(指示\) > [TextContent] オブジェクトの子として TextMeshPro テキスト オブジェクトを作成し、適切な名前 (**Feedback** など) を付けます。

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> シーンを簡単に操作できるようにするには、ParentAnchor オブジェクトの左側にある目のアイコンをクリックして、そのオブジェクトの<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">シーンの可視性</a>をオフに設定します。 これにより、ゲーム中の可視性を変更することなく、[Scene]\(シーン\) ウィンドウ内のオブジェクトが非表示になります。

**Feedback** オブジェクトを引き続き選択した状態で、[Inspector]\(インスペクター\) ウィンドウでその位置とサイズを変更して、指示テキストの下に配置されるようにします。次に例を示します。

* [Rect Transform]\(四角形の変換\) の **[Pos Y]\(位置 Y\)** を -0.24 に変更する
* [Rect Transform]\(四角形の変換\) の **[幅]** を 0.555 に変更する
* [Rect Transform]\(四角形の変換\) の **[高さ]** を 0.1 に変更する

次に、テキスト領域内にテキストがうまく適合するように、フォントのプロパティを選択します。次に例を示します。

* Text Mesh Pro (Script) の **[Font Style]\(フォント スタイル\)** を太字に変更する
* Text Mesh Pro (Script) の **[Font Size]\(フォント サイズ\)** を 0.17 に変更する
* Text Mesh Pro (Script) の **[Alignment]\(配置\)** を中央揃え中央に変更する

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

**Feedback** オブジェクトを引き続き選択した状態で、[Inspector]\(インスペクター\) ウィンドウの **[Add Component]\(コンポーネントの追加\)** ボタンを使用して **Anchor Feedback Script (Script)** コンポーネントを Feedback オブジェクトに追加します。

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

**Feedback** オブジェクト自体を **Anchor Feedback Script (Script)** コンポーネントの **[Feedback Text]\(フィードバック テキスト\)** フィールドに割り当てます。

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a>結論

このチュートリアルでは、ユーザーにリアルタイムのフィードバックを提供するために、Azure Spatial Anchors エクスペリエンスの現在の状態を表示する UI パネルを作成する方法を学習しました。

[次のレッスン:4.Android と iOS 用の Azure Spatial Anchors](mrlearning-asa-ch4.md)
