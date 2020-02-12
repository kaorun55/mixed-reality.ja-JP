---
title: 入門チュートリアル-4. 動的なコンテンツの配置とソルバーの使用
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 8275d5a97d7827d34ed3926cabe4032cc7f4cfac
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129333"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. 動的なコンテンツを配置し、ソルバーを使用する
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

ホログラムは、ユーザーに直感的に従うことができ、シームレスで洗練された方法で物理的な環境に配置されると、HoloLens 2 で有効になります。 このチュートリアルでは、複雑な空間配置シナリオを解決するために、ソルバーと呼ばれる MRTK の利用可能な配置ツールを使用して、ホログラムを動的に配置する方法について説明します。 MRTK では、ソルバーはスクリプトと動作のシステムであり、UI 要素がシーン内のユーザー、ユーザー、またはその他のゲームオブジェクトに従うことを許可するために使用されます。 また、特定の場所にすばやくスナップして、アプリケーションをさらに直感的にするために使用することもできます。

## <a name="objectives"></a>目標

* MRTK のソルバーを導入する
* ソルバーを使用して、ユーザーに続くボタンのコレクションを作成します
* ソルバーを使用して、ユーザーの追跡対象に従うゲームオブジェクトを作成します。

## <a name="location-of-solvers-in-the-mrtk"></a>MRTK でのソルバーの場所

 MRTK のソルバーは、MRTK SDK フォルダーにあります。 プロジェクトで使用可能なソルバーを表示するには、プロジェクト ウィンドウで、**資産** >   > **機能**  >  > **ユーティリティ** **ソルバー** の順に**移動します**。

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

このチュートリアルでは、回転ソルバーと放射状ビューのソルバーの実装について説明します。 MRTK で利用可能なすべてのソルバーの詳細については、 [Mrtk ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の「[ソルバー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)ガイド」を参照してください。

## <a name="use-a-solver-to-follow-the-user"></a>ソルバーを使用してユーザーをフォローする
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

このセクションでは、前のチュートリアルで作成したボタンコレクションを拡張して、ユーザーの見つめ方向に従うようにします。 さらに、ボタンコレクションが常にであるように、ソルバーも構成します。

* 自然な左から右への読み取りのために、ユーザーの読み取り方向に並列に回転
* このチュートリアルの後半では、ユーザーの横方向の水平方向の向きを少しずらして配置します。そのため、このチュートリアルの後半で追加するオブジェクトは obstructing ません。
* ユーザーに対して約半分の arm の長さが配置されているため、ボタンを簡単に押すことができます。

このためには、**回転ソルバー**を使用します。これにより、オブジェクトが、参照先のオブジェクトから指定した位置とオフセットにロックされます。

### <a name="1-add-the-orbital-solver"></a>1. 回転ソルバーを追加する

階層 ウィンドウで、 **buttoncollection**オブジェクトを選択し、インスペクター ウィンドウで **コンポーネントの追加** ボタンを使用して、**回転 (スクリプト)** コンポーネントを buttoncollection オブジェクトに追加します。

> [!NOTE]
> ソルバー (この場合は回転 (スクリプト) コンポーネント) を追加すると、ソルバーで必要になるため、ソルバーハンドラー (スクリプト) コンポーネントが自動的に追加されます。

### <a name="2-configure-the-orbital-solver"></a>2. 回転ソルバーを構成する

**ソルバーハンドラー (スクリプト)** コンポーネントを構成します。

* **追跡対象のターゲットの種類**が**Head**に設定されていることを確認する

**回転 (スクリプト)** コンポーネントを構成します。

* **追跡対象オブジェクトに従っ**て**向きの種類**を変更する
* **ローカルオフセット**を X = 0、Y = 0、Z = 0 にリセットします。
* **ワールドオフセット**を X = 0、Y =-0.4、Z = 0.3 に変更します。

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a>3. エディター内シミュレーションを使用して回転ソルバーをテストする

再生ボタンを押してゲームモードに入り、マウスの右ボタンを押したままにして、次の点に注意してください。

* ButtonCollection の変換位置が、ソルバーの設定によって決定されるようになりました。
* この場合、ソルバーの影響を受けないキューブは同じ位置に残ります。

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> シーンウィンドウにカメラの射線が表示されない場合は、ギズモメニューが有効になっていることを確認してください。 [ギズモ] メニューと、それを使用してシーンビューを最適化する方法の詳細については、Unity の<a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">ギズモメニュー</a>のドキュメントを参照してください。
>
> 上の図に示されているようにシーンとゲームウィンドウを並べて表示するには、[シーン] ウィンドウの右側にゲームウィンドウをドラッグするだけです。 ワークスペースのカスタマイズの詳細については、「<a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">ワークスペース</a>のドキュメントをカスタマイズする」を参照してください。

## <a name="enabling-objects-to-follow-tracked-hands"></a>追跡したハンドに従ってオブジェクトを有効にする

このセクションでは、前のチュートリアルで作成したキューブオブジェクトを構成して、ユーザーの追跡対象 (特に右側の手首) に従っていることを確認します。 また、次のように、キューブにソルバーを構成します。

* ユーザーの手の回転で向きを変更します。
* ユーザーの手首に位置指定

この場合は、参照先のオブジェクトによってキャストされたビューコーン内のオブジェクトを保持する**放射状ビューのソルバー**を使用します。

### <a name="1-add-the-radial-view-solver"></a>1. 放射状ビューのソルバーを追加する

階層 ウィンドウで、**キューブ**オブジェクトを選択し、インスペクター ウィンドウで **コンポーネントの追加** ボタンを使用して、**放射状ビュー (スクリプト)** コンポーネントキューブオブジェクトを追加します。

### <a name="2-configure-the-radial-view-solver"></a>2. 放射状ビューのソルバーを構成する

**ソルバーハンドラー (スクリプト)** コンポーネントを構成します。

* **追跡対象のターゲットの種類**を**手動**に変更する
* **追跡**した内容を**右**に変更する
* 追跡した**ハンドジョイント**を**手首**に変更する

**放射状ビュー (スクリプト)** コンポーネントを構成します。

* **参照の方向**を**オブジェクト指向**に変更し、 **[参照方向への向き]** チェックボックスをオンにします。
* **最小距離**と**最大距離**を0に変更します

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a>3. エディター内シミュレーションを使用して放射状ビューのソルバーをテストする

再生ボタンを押してゲームモードに入り、space キーを押したままにします。 マウスカーソルを移動して手を動かし、マウスの左ボタンを押したままにします。

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a>結論

このチュートリアルでは、MRTK のソルバーを使用して、UI を直感的にユーザーに従う方法を学習しました。 また、オブジェクト (つまりキューブ) にソルバーをアタッチして、ユーザーの追跡対象に従う方法についても学習しました。 MRTK に含まれるこれらの他のソルバーの詳細については、 [Mrtk ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の「[ソルバー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)ガイド」を参照してください。

[次のチュートリアル: 5. 3D オブジェクトとの対話](mrlearning-base-ch4.md)
