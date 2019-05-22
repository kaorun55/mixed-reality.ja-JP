---
title: MR 入力 213
description: アニメーション コント ローラーの詳細については、Unity、Visual Studio およびイマーシブ ヘッドセットを使用してこのコーディング チュートリアルに従ってください。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity のイマーシブなアニメーション コント ローラー、academy, チュートリアル
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604701"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。  そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。  これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。  サポートされているデバイスで作業を続行するが保持されます。 一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。  この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。

<br>

# <a name="mr-input-213-motion-controllers"></a>MR 入力 213:アニメーション コント ローラー

複合現実の世界でのモーション コント ローラーは、別のレベルの対話機能を追加します。 [コント ローラーのモーション](motion-controllers.md)、私たちできます直接オブジェクトで実際には、物理操作のようなより自然な方法で immersion を増やすと対話、アプリのエクスペリエンスに喜びを感じています。

MR 入力 213 では、アニメーション コント ローラーの入力イベントをについて説明を単純な空間ペイント エクスペリエンスを作成します。 このアプリでは、ユーザーは、さまざまな種類のブラシと色の 3 次元空間で描画できます。

## <a name="topics-covered-in-this-tutorial"></a>このチュートリアルで説明したトピック

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 トピック 2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**コント ローラーの視覚化**|**コント ローラーの入力イベント**|**カスタム コント ローラーと UI**|
|Unity のゲーム モードとランタイムの motion コント ローラー モデルをレンダリングする方法について説明します。|さまざまな種類のボタン イベントとそのアプリケーションについて説明します。|コント ローラー上に UI 要素を重ね合わせる、または完全にカスタマイズする方法について説明します。|

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td>MR 入力 213:アニメーション コント ローラー</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始前の作業

### <a name="prerequisites"></a>前提条件

イマーシブ ヘッドセットのインストールのチェックリストを参照してください[このページ](install-the-tools.md)します。

* このチュートリアルが必要です[Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)

### <a name="project-files"></a>プロジェクト ファイル

* [ファイルをダウンロード](https://github.com/Microsoft/MixedReality213/archive/master.zip)プロジェクトに必要し、デスクトップにファイルを抽出します。

>[!NOTE]
>をダウンロードする前に、ソース コードを検索する場合がある[GitHub で入手できます](https://github.com/Microsoft/MixedReality213)します。

## <a name="unity-setup"></a>Unity のセットアップ

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>目標

* Windows for Mixed Reality の Unity 開発を最適化します。
* 複合現実のカメラをセットアップします。
* 環境のセットアップ

### <a name="instructions"></a>手順

* Unity を起動します。
* **[開く]** を選択します。
* デスクトップおよび検索に移動し、 **MixedReality213 マスター**フォルダーの以前にアーカイブ解除します。
* **[フォルダーの選択]** をクリックします。
* Unity では、プロジェクト ファイルの読み込みが完了すると、Unity エディターを表示できなきます。
* Unity では、次のように選択します。**ファイル > Build Settings**します。

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* 選択**ユニバーサル Windows プラットフォーム**で、**プラットフォーム**を一覧表示し、をクリックして、**スイッチ プラットフォーム**ボタンをクリックします。
* ターゲット デバイスを設定**任意のデバイス**
* ビルドの種類を設定**D3D**
* SDK を設定**インストールされている最新**
* 確認**UnityC#プロジェクト**
    * これにより、Unity プロジェクトをリビルドすることがなく、Visual Studio プロジェクト内のスクリプト ファイルを変更できます。
* クリックして**プレーヤー設定**します。
* **インスペクター**パネルで、一番下までスクロール
* XR の設定で確認**仮想現実のサポート**
* 仮想現実 Sdk では、次のように選択します**Windows Mixed Reality。**

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* 閉じる**Build Settings**ウィンドウ。

### <a name="project-structure"></a>プロジェクトの構造

このチュートリアルでは **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** します。 リリースを確認できます[このページ](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)します。

![構造](images/mr213-projectstructure-650px.png)

**参照用の完成したシーン**
* 下の 2 つの完成した Unity シーンが見つかります**シーン**フォルダー。
    * **MixedReality213**:1 つのブラシで完了したシーン
    * **MixedReality213Advanced**:複数のブラシで高度なデザインにシーンが完了しました

**このチュートリアル用に新しいシーン設定**
* Unity では、次のようにクリックします**ファイル > 新しいシーン。**
* 削除**メイン カメラ**と**指向性光**
* **プロジェクト パネル**し、検索に次のプレハブをドラッグ、**階層**パネル。
    * 資産/HoloToolkit/入力/プレハブ/**MixedRealityCamera**
    * 資産/AppPrefabs/**環境**

![カメラと環境](images/mr213-cameraenvironment-300px.jpg)
* Mixed Reality toolkit カメラ プレハブを 2 つあります。
    * **MixedRealityCamera.prefab**:カメラのみ
    * **MixedRealityCameraParent.prefab**:カメラ + Teleportation 境界
    * このチュートリアルでは使用**MixedRealityCamera** teleportation 機能なし。 このため、単純な追加**環境**プレハブを根拠と感じるユーザーを作成する基本的な床面が含まれています。
    * 詳細と teleportation については**MixedRealityCameraParent**を参照してください[設計 - Teleportation と locomotion の詳細](#advanced-design---teleportation-and-locomotion)

**スカイ ボックスのセットアップ**
* クリックして**ウィンドウ > 照明 > の設定**
* 右側にある円をクリックして、**スカイ ボックス素材フィールド**
* '灰色' で入力し、選択**SkyboxGray**

(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)

![スカイ ボックスの設定](images/mr123-skyboxsetting-400px.jpg)
* 確認**スカイ ボックス**オプションを表示するのには、グレーのグラデーション スカイ ボックスを割り当てられています。

![トグル スカイ ボックスのオプション](images/mr213-skyboxcheck-400px.jpg)
* MixedRealityCamera、環境、および灰色のスカイ ボックスのシーンは、次のようになります。

![MixedReality213 環境](images/mr213-environment-600px.jpg)
* クリックして**ファイル > としてシーンを保存**
* **保存**任意の名前とシーンのフォルダーの下、シーン

## <a name="chapter-1---controller-visualization"></a>第 1 章 - コント ローラーの視覚化

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>目標

* コント ローラー モデルおよび実行時の Unity のゲーム モードのアニメーションをレンダリングする方法について説明します。

Windows Mixed Reality は、コント ローラーの視覚エフェクトのアニメーション コント ローラー モデルを提供します。 これには、アプリにコント ローラーの視覚エフェクトに対して実行できるいくつかの方法があります。
* 既定値は変更しなくても既定のコント ローラーを使用します。
* 既定のコント ローラーを使用して、その要素の一部をカスタマイズする UI コンポーネントを重ねて表示したり、ハイブリッド
* 置換 - 独自を使用して、コント ローラーの 3D モデルをカスタマイズ

この章でこれらのコント ローラーのカスタマイズの例について説明します。

### <a name="instructions"></a>手順

* **プロジェクト**入力パネルで、 **MotionControllers**検索ボックスにします。 資産/HoloToolkit/入力/プレハブの下で検索することもできます/。
* ドラッグ、 **MotionControllers**にプレハブ、**階層**パネル。
* をクリックして、 **MotionControllers**のプレハブ、**階層**パネル。

**MotionControllers プレハブ**

**MotionControllers**プレハブは、 **MotionControllerVisualizer**スロットを代わりのコント ローラー モデルを提供するスクリプト。 手の形や剣などお客様独自のカスタムの 3D モデルを割り当て、常に使用して代替左/右のモデル ' を確認して場合、は、既定のモデルではなく表示されます。 ブラシを使用して、コント ローラー モデルを置換するのに第 4 章では、このスロットを使用します。

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**手順**
* **インスペクター**パネルをダブルクリックして**MotionControllerVisualizer** Visual Studio でコードを表示するスクリプト

**MotionControllerVisualizer スクリプト**

**MotionControllerVisualizer**と**MotionControllerInfo**クラスへのアクセスし、既定のコント ローラー モデルを変更するための手段を提供します。 **MotionControllerVisualizer**をサブスクライブする Unity の**InteractionSourceDetected**イベントが見つかったときに、コント ローラー モデルを自動的にインスタンス化します。

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

コント ローラー モデルに従って配信[glTF 仕様](https://github.com/KhronosGroup/glTF)します。 送信および 3D アセットをアンパックの背後にあるプロセスを向上させながら、一般的な形式を提供するは、この形式が用意されています。 この場合を取得し、ユーザーのエクスペリエンスを可能な限りシームレスにようにするため、アニメーション コント ローラーのバージョン、ユーザーは使用する場合がありますとは限りません時に、コント ローラー モデルを読み込む必要があります。 このコースでは、混合の現実 Toolkit を使用して、Khronos グループのバージョンを使用する[UnityGLTF プロジェクト](https://github.com/KhronosGroup/UnityGLTF)します。

スクリプトで使用できるコント ローラーが配信されると**MotionControllerInfo**自体位置は正しくできるように特定のコント ローラーの要素の変換が見つかりません。

後の章では、これらのスクリプトを使用して、コント ローラーに UI 要素をアタッチする方法を学びます。

*いくつかのスクリプトでは、コードのブロックを紹介します **#if!UNITY_EDITOR**または**UNITY_WSA**します。これらのコード ブロックは、Windows を展開するときに、UWP ランタイムのみで実行します。これは、Unity エディターと、UWP アプリのランタイムで使用される Api のセットが異なるためです。*
* **保存**シーンとクリック、**再生**ボタンをクリックします。

ヘッドセット内のモーション コント ローラーとシーンを表示できます。 ボタンのクリック、スティックの移動、およびタッチパッド タッチの強調表示の詳細なアニメーションを表示できます。

![MR213_Controller 視覚エフェクトの既定値](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>第 2 章 – コント ローラーへの UI 要素

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>目標

* アニメーション コント ローラーの要素について説明します
* オブジェクトのコント ローラーの特定の部分にアタッチする方法について説明します

この章では、ユーザーは簡単にアクセスし、いつでも操作コント ローラーにユーザー インターフェイス要素を追加する方法を学びます。 単純なカラー ピッカー入力タッチパッドを使用して UI を追加する方法も学習します。

### <a name="instructions"></a>手順

* **プロジェクト**パネルで、検索**MotionControllerInfo**スクリプト。
* 検索結果からダブル クリックして**MotionControllerInfo**スクリプトを Visual Studio でコードを参照してください。

**MotionControllerInfo script**

最初の手順では、コント ローラーの要素にアタッチする UI をするかを選択します。 これらの要素が定義されている**ControllerElementEnum**で**MotionControllerInfo.cs**します。

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)
* **ホーム**
* **メニュー**
* **理解**
* **スティック**
* **Select**
* **タッチパッド**
* **ポインティングの姿勢**: この要素は、順方向を指すコント ローラーの先端を表します。

**手順**
* **プロジェクト**パネルで、検索**AttachToController**スクリプト。
* 検索結果からダブル クリックして**AttachToController**スクリプトを Visual Studio でコードを参照してください。

**AttachToController スクリプト**

**AttachToController**スクリプトが指定されたコント ローラーの処理および要素をすべてのオブジェクトをアタッチする簡単な方法を提供します。

In **AttachElementToController()**,
* 処理を使用して確認**MotionControllerInfo.Handedness**
* コント ローラーを使用して、特定の要素を取得**MotionControllerInfo.TryGetElement()**
* 要素を取得した後、コント ローラー モデル、その下にあるオブジェクトの親から変換し、オブジェクトのローカルの位置と回転は 0 に設定します。

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type " + element + " under controller " + newController.ControllerParent.name + "; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

使用する最も簡単な方法は、 **AttachToController**の場合と、そこから継承するようにスクリプトは**ColorPickerWheel します。** オーバーライドするだけで、 **OnAttachToController**と**OnDetatchFromController**セットアップを実行する関数//コント ローラーが検出されました。 切断されたときにブレーク ダウンします。

**手順**
* **プロジェクト**パネルで、検索ボックスに入力**ColorPickerWheel**します。 資産/AppPrefabs で検索することもできます/。
* ドラッグ**ColorPickerWheel**にプレハブ、**階層**パネル。
* をクリックして、 **ColorPickerWheel**のプレハブ、**階層**パネル。
* **インスペクター**パネルをダブルクリックして**ColorPickerWheel**スクリプトを Visual Studio でコードを参照してください。

![ColorPickerWheel プレハブ](images/mr213-colorpickerwheel-1000px.jpg)

**ColorPickerWheel スクリプト**

**ColorPickerWheel**継承**AttachToController**、表示**処理**と**要素**で、 **Inspector**パネル。 アタッチ、UI、左側のコント ローラーのタッチパッド要素にします。

![ColorPickerWheel スクリプト](images/mr213-attachtocontroller-300px.jpg)

**ColorPickerWheel**オーバーライド、 **OnAttachToController**と**OnDetatchFromController**と色の選択の次の章で使用される入力イベントをサブスクライブするにはタッチパッドを入力します。

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```
* **保存**シーンとクリック、**再生**ボタンをクリックします。

**コント ローラーにオブジェクトのアタッチの代替方法**

スクリプトがから継承することをお勧めします。 **AttachToController**オーバーライドと**OnAttachToController**します。 ただし、これができるとは限りません。 代わりにでは、スタンドアロン コンポーネントとして使用します。 これは、スクリプトをリファクタリングすることがなく、コント ローラーを既存のプレハブをアタッチする場合に役立ちます。 単に IsAttached に設定するまで待機する、クラスがある任意のセットアップを実行する前に true。 これを行う最も簡単な方法は、'Start ' のコルーチンを使用して、します。

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>第 3 章 - タッチパッドの入力

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>目標

* タッチパッド入力データのイベントを取得する方法について説明します
* アプリのエクスペリエンスにタッチパッド軸の位置に関する情報を使用する方法について説明します

### <a name="instructions"></a>手順

* **階層**パネルで、をクリックして**ColorPickerWheel**
* **インスペクター**パネルの**Animatior**、ダブルクリック**ColorPickerWheelController**
* 表示することができます**Animator**タブが開かれます

**Unity のアニメーション コント ローラーと UI を表示/非表示**

表示/非表示に、 **ColorPickerWheel**使用してアニメーションを使用して UI、 [Unity のアニメーション システム](https://docs.unity3d.com/Manual/AnimationOverview.html)します。 設定、 **ColorPickerWheel**の**Visible**プロパティを true または false のトリガー**表示**と**を非表示に**アニメーション トリガーします。 **表示**と**を非表示に**でパラメーターが定義されている、 **ColorPickerWheelController**アニメーション コント ローラー。

![Unity のアニメーション コント ローラー](images/mr123-animationcontroller-550px.jpg)

**手順**
* **階層**パネルで、 **ColorPickerWheel**プレハブ
* **インスペクター**パネルをダブルクリックして**ColorPickerWheel** Visual Studio でコードを表示するスクリプト

**ColorPickerWheel スクリプト**

**ColorPickerWheel**をサブスクライブする Unity の**InteractionSourceUpdated**タッチパッド イベントをリッスンするイベントです。

**InteractionSourceUpdated()**、ことを確認して、スクリプトが最初に確認します。
* タッチパッド イベントでは実際には、(obj.state **。touchpadTouched**)
* 左側のコント ローラーの発生元 (obj.state.source **。処理**)

タッチパッドの両方に該当する場合は位置 (obj.state **。touchpadPosition**) に割り当てられている**selectorPosition**します。

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

**Update()** に基づいて、**表示**プロパティ、カラー ピッカーの animator コンポーネントでの表示と非表示のアニメーション トリガーでトリガーされます

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

**Update()**、 **selectorPosition** UV 位置を返しますカラー ホイールの mesh collider コライダーに伸びる射線をキャストするために使用します。 この位置は、ピクセル座標を見つけて、色のカラー ホイールのテクスチャの値を使用できます。 この値が他のスクリプトを使用してアクセスできる、 **SelectedColor**プロパティ。

![カラー ピッカーのホイール レイキャスト](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a>第 4 章 - コント ローラー モデルをオーバーライドします。

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>目標

* カスタムの 3D モデルとコント ローラー モデルを上書きする方法について説明します。

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>手順

* クリックして**MotionControllers**で、**階層**パネル。
* 右側にある円をクリックして、**代替の右側のコント ローラー**フィールド。
* 入力 **'BrushController**' し、結果から、プレハブを選択します。 資産/AppPrefabs 下で見つかります/**BrushController**します。
* 確認**常に別の適切なモデルを使用して、**

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

**BrushController**プレハブは対象にする必要はありません、**階層**パネル。 ただし、その子コンポーネントを確認します。
* **プロジェクト**に入力パネルで、 **BrushController**ドラッグ**BrushController**にプレハブ、**階層**パネル。

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

検索は、**ヒント**コンポーネント**BrushController**します。 開始/停止の線を描画するのに、変換を使用します。
* 削除、 **BrushController**から、**階層**パネル。
* **保存**シーンとクリック、**再生**ボタンをクリックします。 ブラシ モデルが右側のモーション コント ローラーを交換できるようにします。

## <a name="chapter-5---painting-with-select-input"></a>第 5 章「選択の入力による塗りつぶし

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>目標

* [選択] ボタンのイベントを使用して開始および線の描画を停止する方法について説明します

### <a name="instructions"></a>手順

* 検索**BrushController**のプレハブ、**プロジェクト**パネル。
* **インスペクター**パネルをダブルクリックして**BrushController**スクリプトを Visual Studio でコードを参照してください。

**BrushController スクリプト**

**BrushController** InteractionManager のサブスクライブ**InteractionSourcePressed**と**InteractionSourceReleased**イベント。 ときに**InteractionSourcePressed**イベントがトリガーされると、ブラシの**描画**プロパティがときに true **InteractionSourceReleased**イベントがトリガーされると、ブラシの**描画**プロパティが false に設定します。

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

中に**描画**に設定されている場合は true、ブラシが生成されますポイントをインスタンス化された Unity で**LineRenderer**します。 ブラシにこのプレハブへの参照が保持される**ストローク Prefab**フィールド。

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

カラー ピッカー ホイール UI から現在選択されている色を使用する**BrushController**への参照が必要、 **ColorPickerWheel**オブジェクト。 **BrushController**プレハブは、交換したコント ローラーとして実行時にインスタンス化、シーン内のオブジェクトへの参照が実行時に設定する必要があります。 ここで使用**GameObject.FindObjectOfType**を検索する、 **ColorPickerWheel**:

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```
* **保存**シーンとクリック、**再生**ボタンをクリックします。 線の描画し、ペイントの右側のコント ローラーの選択ボタンを使用することができます。

## <a name="chapter-6---object-spawning-with-select-input"></a>第 6 章 - は入力オブジェクトの生成での選択

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>目標

* 選択を使用する方法について説明し、ボタンの入力イベントを把握
* オブジェクトをインスタンス化する方法について説明します

### <a name="instructions"></a>手順

* **プロジェクト**入力パネルで、 **ObjectSpawner**検索ボックスにします。 資産/AppPrefabs で検索することもできます/
* ドラッグ、 **ObjectSpawner**にプレハブ、**階層**パネル。
* クリックして**ObjectSpawner**で、**階層**パネル。
* **ObjectSpawner**という名前のフィールドを持つ**色ソース**します。
* **階層**パネルで、ドラッグ、 **ColorPickerWheel**このフィールドへの参照。

![オブジェクトの Spawner インスペクター](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* をクリックして、 **ObjectSpawner**のプレハブ、**階層**パネル。
* **インスペクター**パネルをダブルクリックして**ObjectSpawner**スクリプトを Visual Studio でコードを参照してください。

**ObjectSpawner スクリプト**

**ObjectSpawner** (キューブ、球、円柱) プリミティブのメッシュのコピーを領域にインスタンス化します。 ときに、 **InteractionSourcePressed**処理を確認し、かどうかは、検出された、 **InteractionSourcePressType.Grasp**または**InteractionSourcePressType.Select**イベントです。

**持ち**イベント、現在のメッシュ型 (球体、キューブ、円柱) のインデックスの値が増加

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

**選択**イベントで、 **SpawnObject()**、新しいオブジェクトをインスタンス化された、親が設定されていない、世界中にリリースされました。

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detatch the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

**ObjectSpawner**を使用して、 **ColorPickerWheel**表示オブジェクトの素材の色を設定します。 生成されたオブジェクトの色が保持されますが、この資料のインスタンスが提供されます。
* **保存**シーンとクリック、**再生**ボタンをクリックします。

理解 ボタンを持つオブジェクトを変更し、選択 ボタンを持つオブジェクトを生成することができます。

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>ビルドしてアプリをデプロイする Mixed Reality ポータル
* Unity では、次のように選択します。**ファイル > Build Settings**します。
* クリックして**開くシーンを追加**を現在のシーンを追加する、 **Scenes In Build**します。
* **[Build]** をクリックします。
* 作成、**新しいフォルダー** "App"という名前です。
* 1 回のクリック、**アプリ**フォルダー。
* **[フォルダーの選択]** をクリックします。
* Unity を完了すると、ファイル エクスプ ローラー ウィンドウが表示されます。
* 開く、**アプリ**フォルダー。
* ダブルクリック**YourSceneName.sln** Visual Studio ソリューション ファイル。
* デバッグからターゲットを変更する Visual Studio で、上部のツールバーを使用して**リリース**を ARM から**X64**します。
* デバイスのボタンの横にあるドロップダウン矢印をクリックし、**ローカル マシン**します。
* クリックして**デバッグ]、[デバッグなしで開始**メニューまたはキーを押して**ctrl キーを押しながら f5 キーを押して**します。

これでアプリがビルドし、Mixed Reality ポータルにインストールされています。 Mixed Reality ポータルで [スタート] メニューをもう一度起動できます。

## <a name="advanced-design---brush-tools-with-radial-layout"></a>高度なデザインのレイアウトとブラシ ツール

![MixedReality213 Main](images/mr213-main-600px.jpg)

この章では、カスタム ブラシ ツール コレクションで、既定のモーション コント ローラー モデルを置換する方法を学びます。 参照用には、完了したシーンを見つけることができます**MixedReality213Advanced** **シーン**フォルダー。

### <a name="instructions"></a>手順

* **プロジェクト**入力パネルで、 **BrushSelector**検索ボックスにします。 資産/AppPrefabs で検索することもできます/
* ドラッグ、 **BrushSelector**にプレハブ、**階層**パネル。
* 組織の作成と呼ばれる空の GameObject**ブラシ**
* 次のプレハブからドラッグして、**プロジェクト**にパネル**ブラシ**
    * 資産/AppPrefabs/**BrushFat**
    * 資産/AppPrefabs/**BrushThin**
    * 資産/AppPrefabs/**消しゴム**
    * 資産/AppPrefabs/**MarkerFat**
    * 資産/AppPrefabs/**MarkerThin**
    * 資産/AppPrefabs/**鉛筆**

![ブラシ](images/mixedreality213-brushes-250px.png)
* クリックして**MotionControllers**のプレハブ、**階層**パネル。
* **インスペクター**パネルをオフにします**常に代替権限モデルを使用する**上、**アニメーション コント ローラーのビジュアライザー**
* **階層**パネルで、をクリックして**BrushSelector**
* **BrushSelector**という名前のフィールドを持つ**ColorPicker**
* **階層**パネルで、ドラッグ、 **ColorPickerWheel**に**ColorPicker**フィールドに、**インスペクター**パネル。

![ブラシのセレクターを ColorPickerWheel を割り当てる](images/mr213-brushselector-500px.jpg)
* **階層**パネルの**BrushSelector**プレハブを選択、**メニュー**オブジェクト。
* **インスペクター**パネルの**LineObjectCollection**コンポーネント、オープン、**オブジェクト**ドロップダウンの配列。 6 は空きスロットが表示されます。
* **階層**パネルで、各親の下のプレハブのドラッグ、**ブラシ**任意の順序でこれらのスロットに GameObject です。 (シーン、プロジェクト フォルダーのプレハブから、プレハブをドラッグしていることを確認してください。)

![ブラシのセレクター](images/mr213-brushselectorbrushes-700px.jpg)

**BrushSelector プレハブ**

以降、 **BrushSelector**継承**AttachToController**、表示**処理**と**要素**オプション、 **Inspector**パネル。 選択した**右**と**発生ポイント**順方向で右側にあるコント ローラーにブラシ ツールをアタッチします。

**BrushSelector**の 2 つのユーティリティを使用します。
* **楕円**: 楕円に沿った空間のポイントを生成するために使用します。
* **LineObjectCollection**: 任意の行クラス (例: 楕円) によって生成されたポイントを使用してオブジェクトを配布します。 これは、どのような使用する、ブラシに沿って楕円のシェイプを配置します。

組み合わせて使用すると、放射状メニューを作成するこれらのユーティリティを使用できます。

**LineObjectCollection スクリプト**

**LineObjectCollection**サイズ、位置の行に分散されていますオブジェクトの回転のコントロールがあります。 これは、ブラシのセレクターのような放射状のメニューを作成するために役立ちます。 外観を作成するブラシをスケールから近づいた場合は、選択したセンターの位置に何も、 **ObjectScale**オフ、エッジの中央と tapers のピークを曲線します。

**BrushSelector スクリプト**

場合、 **BrushSelector**、手続き型のアニメーションを使用することにしました。 最初に、ブラシのモデルは、によって楕円で配布、 **LineObjectCollection**スクリプト。 各ブラシがその位置に基づいて、ユーザーの手の形での保守を担当し、その**DisplayMode**値で、選択内容に基づいて変更します。 手続き型の方法を選択したユーザーは、ブラシを選択すると、中断されているブラシの位置の遷移の可能性が高くため。 Mecanim アニメーションでは、中断を正常に処理できますが、単純な Lerp 操作よりも複雑にします。

**BrushSelector**両方の組み合わせを使用します。 タッチパッドの入力が検出されると、ブラシ オプションは表示されているようになり、放射状のメニューに沿ったスケール アップします。 (これは、ユーザーが選択を行うことを示します) タイムアウト期間後に、ブラシのオプションをスケール ダウン、もう一度選択したブラシのみを離れること。

**タッチパッドの入力を視覚化します。**

コント ローラー モデルが完全に置き換えられましたいる場合でも元のモデルの入力に入力を表示することもできます。 これにより、実際には、ユーザーのアクションを地上にします。 **BrushSelector**入力を受け取ったとき、タッチパッドを簡単に表示することにしました。 カスタム素材には、その素材を置き換えて、コント ローラーからタッチパッド要素を取得することによってこれは、入力を受信した最後の時間タッチパッドに基づいてその素材の色をグラデーションを適用します。

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }
            
    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

**タッチパッドの入力とブラシ ツールの選択**

タッチパッドの押された入力が検出されると、ブラシのセレクターを左または右がかどうかことを確認する入力の位置を確認します。

**ストロークの太さを selectPressedAmount**

代わりに、 **InteractionSourcePressType.Select**内のイベント、 **InteractionSourcePressed()**、押された状態の量をアナログ値を取得する**selectPressedAmount**. この値を取得できる**InteractionSourceUpdated()** します。

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

**消しゴム スクリプト**

**消しゴム**は特殊な種類の基本をオーバーライドするブラシ**ブラシ**の**DrawOverTime()** 関数。 描画が true の場合、消しゴムがそのヒントが、既存のブラシのストロークと交差するかどうかを確認します。 その場合を圧縮するキューに追加され削除します。

## <a name="advanced-design---teleportation-and-locomotion"></a>高度な設計 - Teleportation と locomotion

Teleportation スティックを使用して、シーン内を移動するには、使用できるようにする場合**MixedRealityCameraParent**の代わりに**MixedRealityCamera**します。 追加する必要があります**InputManager**と**DefaultCusor**します。 **MixedRealityCameraParent**が既に含まれて**MotionControllers**と**境界**、子コンポーネントとして既存を削除する必要があります**MotionControllers**と**環境**prefab します。

### <a name="instructions"></a>手順

* **階層**パネルで、削除**MixedRealityCamera**、**環境**と**MotionControllers**
* **プロジェクト パネル**し、検索に次のプレハブをドラッグ、**階層**パネル。
    * 資産/AppPrefabs/入力/プレハブ/**MixedRealityCameraParent**
    * 資産/AppPrefabs/入力/プレハブ/**InputManager**
    * 資産/AppPrefabs/入力/プレハブ/カーソル/**DefaultCursor**

![複合現実のカメラの親](images/mr213-cameraparent-300px.png)
* **階層**パネルで、をクリックして**入力マネージャー**
* **インスペクター**パネルで、下へスクロールして、**単純な 1 つのポインターのセレクター**セクション
* **階層**パネルで、ドラッグ**DefaultCursor**に**カーソル**フィールド

![既定値のカーソルの割り当てください。](images/mr213-defaultcursor-500px.png)
* **保存**シーンとクリック、**再生**ボタンをクリックします。 左/右またはテレポートを回転するスティックを使用することができます。

## <a name="the-end"></a>最後です

このチュートリアルは終わりです。 学習内容。
* Unity のゲーム モードとランタイムの motion コント ローラー モデルを操作する方法。
* さまざまな種類のボタン イベントとそのアプリケーションを使用する方法。
* コント ローラー上に UI 要素を重ね合わせる、または完全にカスタマイズする方法。

アニメーション コント ローラーで、独自の没入型エクスペリエンスの作成を開始する準備が整いました。

## <a name="completed-scenes"></a>完了したシーン

* Unity の**プロジェクト**パネル クリック、**シーン**フォルダー。
* 2 つの Unity sceens 見つかります**MixedReality213**と**MixedReality213Advanced**します。
    * **MixedReality213**:1 つのブラシで完了したシーン
    * **MixedReality213Advanced**:[選択] ボタンを押して量例での複数のブラシで完了したシーン

## <a name="see-also"></a>関連項目

* [MR 入力 213 プロジェクト ファイル](https://github.com/Microsoft/MixedReality213)
* [混合現実 Toolkit - モーション コント ローラーのテスト シーン](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [Mixed Reality Toolkit - グラブのしくみ](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [アニメーション コント ローラーの開発のガイドライン](motion-controllers.md)
