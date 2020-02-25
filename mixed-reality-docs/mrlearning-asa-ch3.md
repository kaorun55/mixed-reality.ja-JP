---
title: Azure 空間アンカーチュートリアル-3. Azure 空間アンカーフィードバックの表示
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 3d762950ea8e211fd5a8e4cf8af717674d3fe7e1
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553944"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3. Azure 空間アンカーのフィードバックを表示する

このチュートリアルでは、Azure 空間アンカー (ASA) を使用する場合のアンカー検出、イベント、および状態に関するフィードバックをユーザーに提供する方法について説明します。

## <a name="objectives"></a>目標

* 現在の ASA セッションに関する重要な情報を表示する UI パネルを設定する方法について説明します。
* ASA SDK によってユーザーに提供されるフィードバック要素について理解し、調査する

## <a name="set-up-asa-feedback-ui-panel"></a>ASA フィードバック UI パネルを設定する

[階層] ウィンドウで、 **Textcontent**オブジェクト > の**指示**を右クリックし、[ **3D オブジェクト** > **テキスト-TextMeshPro** ] を選択して、指示 > Textcontent オブジェクトの子として TextMeshPro Text オブジェクトを作成し、適切な名前 (たとえば、**フィードバック**) を指定します。

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> シーンを簡単に操作できるようにするには、オブジェクトの左側にある目のアイコンをクリックして、ParentAnchor オブジェクトの<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">シーンの表示</a>をオフに設定します。 これにより、シーンウィンドウ内のオブジェクトが非表示になります。ゲーム中の可視性は変更されません。

**フィードバック**オブジェクトを選択した状態で、[インスペクター] ウィンドウの位置とサイズを変更して、指示テキストの下に表示されるようにします。次に例を示します。

* Rect 変換**Pos Y**を-0.24 に変更します。
* 四角形の変換**幅**を0.555 に変更します
* 四角形の変換の**高さ**を0.1 に変更します。

次に、テキスト領域内でテキストが適切に適合するように、[フォントのプロパティ] を選択します。次に例を示します。

* Text メッシュ Pro (スクリプト) の**フォントスタイル**を太字に変更する
* Text メッシュ Pro (スクリプト) の**フォントサイズ**を0.17 に変更します。
* Text メッシュ Pro (スクリプト) の**配置**を中央および中央に変更する

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

**フィードバック**オブジェクトを選択したまま、インスペクター ウィンドウで **コンポーネントの追加** ボタンを使用して、フィードバックオブジェクトに**アンカーフィードバックスクリプト (スクリプト)** コンポーネントを追加します。

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

**フィードバック**オブジェクト自体を**アンカーフィードバックスクリプト (スクリプト)** コンポーネントの**フィードバックテキスト**フィールドに割り当てます。

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a>結論

このチュートリアルでは、ユーザーにリアルタイムのフィードバックを提供するための Azure 空間アンカーエクスペリエンスの現在の状態を表示する UI パネルを作成する方法を学習しました。
