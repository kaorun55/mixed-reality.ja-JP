---
title: Unity のパフォーマンスに関する推奨事項
description: Mixed reality アプリのパフォーマンスを向上させるための Unity 固有のヒント。
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: グラフィックス、cpu、gpu、レンダリング、ガベージコレクション、hololens
ms.openlocfilehash: 724ec24408e70360fda07c59a4ca2ffc30b49c1f
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438131"
---
# <a name="performance-recommendations-for-unity"></a>Unity のパフォーマンスに関する推奨事項

この記事は、「 [mixed reality のパフォーマンスに関する推奨事項](understanding-performance-for-mixed-reality.md)」で説明されている説明に基づいていますが、Unity エンジン環境に固有の学習に重点を置いています。

また、開発者が[Unity の推奨される環境設定](Recommended-settings-for-unity.md)を確認することを強くお勧めします。 この記事には、パフォーマンスに優れた Mixed Reality アプリの構築に関して、最も重要なシーン構成の一部が含まれています。 これらの推奨設定の一部も下に強調表示されています。

## <a name="how-to-profile-with-unity"></a>Unity でプロファイルする方法

Unity には、特定のアプリの貴重なパフォーマンスの洞察を収集するための優れたリソースである **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** が組み込まれています。 エディターでプロファイラーを実行できますが、これらのメトリックは実際のランタイム環境を表すものではないため、このような結果は慎重に使用する必要があります。 デバイスでの実行中に、正確で実用的な洞察を得るために、アプリケーションをリモートでプロファイリングすることをお勧めします。 さらに、Unity の[フレームデバッガー](https://docs.unity3d.com/Manual/FrameDebugger.html)は、利用するための非常に強力な洞察ツールでもあります。

Unity は、次のことに関する優れたドキュメントを提供します。
1) [Unity profiler をリモートで UWP アプリケーションに](https://docs.unity3d.com/Manual/windowsstore-profiler.html)接続する方法
2) [Unity Profiler でパフォーマンスの問題](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)を効果的に診断する方法

>[!NOTE]
> Unity プロファイラーが接続され、GPU プロファイラーを追加した後 (「Profiler を右上隅に*追加*する」を参照してください)、プロファイラーの途中で CPU & GPU でどのくらいの時間がかかっているかを確認できます。 これにより、開発者は、アプリケーションが CPU または GPU で制限されている場合に、簡単に近似できます。
>
> ![Unity CPU と GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>CPU パフォーマンスに関する推奨事項

以下のコンテンツでは、特に Unity & C#開発を対象とした、より詳細なパフォーマンスプラクティスについて説明します。

#### <a name="cache-references"></a>キャッシュ参照

初期化時に、関連するすべてのコンポーネントとオブジェクトへの参照をキャッシュすることをお勧めします。 これは、 *[Getcomponent\<t > ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* などの繰り返し関数呼び出しの方が、ポインターを格納するためのメモリコストと比べてかなりコストがかかるためです。 これは、非常に頻繁に使用される[カメラ](https://docs.unity3d.com/ScriptReference/Camera-main.html)にも適用されます。 *Camera. main は、* 実際には *[findexpensively](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* を使用します。このタグは、 *"maincamera"* タグを持つカメラオブジェクトのシーングラフを検索します。

```CS
using UnityEngine;
using System.Collections;

public class ExampleClass : MonoBehaviour
{
    private Camera cam;
    private CustomComponent comp;

    void Start() 
    {
        cam = Camera.main;
        comp = GetComponent<CustomComponent>();
    }

    void Update()
    {
        // Good
        this.transform.position = cam.transform.position + cam.transform.forward * 10.0f;

        // Bad
        this.transform.position = Camera.main.transform.position + Camera.main.transform.forward * 10.0f;

        // Good
        comp.DoSomethingAwesome();

        // Bad
        GetComponent<CustomComponent>().DoSomethingAwesome();
    }
}
```

>[!NOTE] 
> GetComponent (string) を避けます。 <br/>
> *[Getcomponent ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* を使用する場合、いくつかの異なるオーバーロードがあります。 常に型ベースの実装を使用し、文字列ベースの検索オーバーロードは使用しないことが重要です。 シーンでの文字列による検索は、型での検索よりもかなりコストがかかります。 <br/>
> 正常コンポーネント GetComponent (型の型) <br/>
> 正常T GetComponent\<T > () <br/>
> 不良コンポーネント GetComponent (文字列) > <br/>

#### <a name="avoid-expensive-operations"></a>コストのかかる操作を避ける

1) **[LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)の使用を避ける**

    LINQ は非常にクリーンで、読み取りと書き込みが簡単ですが、通常はアルゴリズムを手動で記述するよりもはるかに多くの計算と、特にメモリの割り当てが必要になります。

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) **共通 Unity Api**

    特定の Unity Api は便利ですが、実行するのは非常にコストがかかります。 ほとんどの場合、シーングラフ全体を検索して、一致するオブジェクトの一覧を検索します。 これらの操作は、通常、参照をキャッシュするか、問題のあるオブジェクトのマネージャーコンポーネントを実装して実行時に参照を追跡することで回避できます。

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> *[SendMessage ()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* と *[BroadcastMessage ()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* は、すべてのコストで排除する必要があります。 これらの関数は、直接の関数呼び出しよりも1,000 倍の速度で実行できます。

3) **ボックス化に注意してください**

    [ボックス](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing)化は、 C#言語とランタイムの中核となる概念です。 これは、char、int、bool などの値で型指定された変数を参照型の変数にラップするプロセスです。 値型の変数が "ボックス化" されている場合は、マネージヒープに格納されている System.object の内部にラップされます。 したがって、ガベージコレクターによって破棄される必要がある場合は、メモリが割り当てられ、最終的にはメモリが割り当てられます。 これらの割り当てと割り当て解除には、パフォーマンスコストが発生します。また、多くのシナリオでは不要であるか、低コストの代替手段で簡単に置き換えることができます。

    開発でのボックス化の最も一般的な形式の1つは、 [null 許容値型](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/)の使用です。 特に、値を取得しようとするときに操作が失敗する可能性がある場合は、関数の値型に対して null を返すことができます。 この方法で発生する可能性のある問題は、ヒープで割り当てが行われ、その結果、後でガベージコレクションを行う必要があることです。

    **のボックス化の例C#**

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

    **Null 許容値型を使用した問題のあるボックス化の例**

    このコードは、Unity プロジェクトで作成できるダミーのパーティクルクラスを示しています。 `TryGetSpeed()` を呼び出すと、ヒープ上でオブジェクトが割り当てられ、後でガベージコレクションが必要になります。 この例は、シーンに1000以上のパーティクルがあり、それぞれが現在の速度を求めているため、特に問題になります。 したがって、1000のオブジェクトが割り当てられ、その結果、パフォーマンスが大幅に低下するすべてのフレームが割り当て解除されます。 エラーが発生したことを示す-1 などの負の値を返すように関数を再記述すると、この問題は回避され、メモリがスタックに保持されます。

    ```csharp
        public class MyParticle
        {
            // Example of function returning nullable value type
            public int? TryGetSpeed()
            {
                // Returns current speed int value or null if fails
            }
        }
    ```

#### <a name="repeating-code-paths"></a>繰り返しコードパス

すべての繰り返し Unity コールバック関数 ( 更新) 1 秒間に何度も実行されるか、またはフレームが非常に慎重に書き込まれる必要があります。 ここで高価な操作を行うと、パフォーマンスに大きな影響を与えます。

1) **空のコールバック関数**

    以下のコードは、アプリケーション内に残すことができないように見えることがありますが、特にすべての Unity スクリプトがこのコードブロックで自動的に初期化するため、これらの空のコールバックは実際には非常にコストが高くなる可能性があります。 Unity はアンマネージコードとマネージコードの境界を越えて、UnityEngine コードとアプリケーションコードの間で動作します。 このブリッジに対するコンテキストの切り替えは、実行するものがない場合でもかなりコストがかかります。 これは、アプリに空の Unity コールバックを持つコンポーネントを含む100のユーザーオブジェクトがある場合に特に問題になります。

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> Update () は、このパフォーマンスの問題の最も一般的な取り組みですが、次のようなその他の繰り返し Unity コールバックは、FixedUpdate ()、Behaviour ()、OnPostRender "、OnPreRender ()、OnRenderImage () などの問題がある場合にも同様に問題が発生する可能性があります。 

2) **フレームごとに1回実行を優先する操作**

    次の Unity Api は、多くの Holographic アプリで一般的な操作です。 これらの関数の結果は、常に可能であるとは限りませんが、通常は1回計算し、その結果を特定のフレームのアプリケーション全体で再利用することができます。

    a) 一般に、1つのシーンに対して Raycast を処理する専用のシングルトンクラスまたはサービスを用意し、その後、それぞれの Raycast 操作を繰り返すのではなく、他のすべてのシーンコンポーネントで再利用することをお勧めします。成分. もちろん、アプリケーションによっては、異なるオリジンまたは異なる[レイヤーマスク](https://docs.unity3d.com/ScriptReference/LayerMask.html)の raycasts が必要になる場合があります。

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    b) Start () または起動 () で[参照をキャッシュ](#cache-references)することで、Update () のような Unity コールバックを繰り返し実行する場合は、getcomponent () 操作を避けてください。

        UnityEngine.Object.GetComponent()

    c) 初期化時にすべてのオブジェクトをインスタンス化し、[オブジェクトプーリング](#object-pooling)を使用して、アプリケーションの実行時にユーザーオブジェクトをリサイクルして再利用することをお勧めします。

        UnityEngine.Object.Instantiate()

3) **インターフェイスと仮想コンストラクトを避ける**

    インターフェイスと直接のオブジェクトまたは呼び出し元の仮想関数を使用した関数呼び出しの呼び出しは、直接コンストラクトや直接関数呼び出しを利用するよりもはるかにコストがかかることがあります。 仮想関数またはインターフェイスが不要な場合は、削除する必要があります。 ただし、これらのアプローチを利用すると、開発コラボレーション、コードの読みやすさ、およびコードの保守性が簡単になるため、一般に、これらの方法のパフォーマンスが低下します。

    一般に、このメンバーを上書きする必要があることを明確に見込んでいない限り、フィールドと関数を仮想としてマークしないことをお勧めします。 多くの場合、フレームごとに何回呼び出されるか、またはフレームごとに1回 (`UpdateUI()` メソッドなど) に呼び出される、高頻度のコードパスを特に注意する必要があります。

4) **構造体を値で渡さないようにする**

    クラスとは異なり、構造体は値型であり、関数に直接渡されると、その内容が新しく作成されたインスタンスにコピーされます。 このコピーにより、CPU コストとスタックの追加メモリが追加されます。 小さい構造体の場合、通常、影響は最小限に抑えられるため、許容されます。 ただし、すべてのフレームと、大きな構造体を取得する関数を繰り返し呼び出す関数の場合は、可能であれば、参照渡しで渡すように関数定義を変更します。 [詳細情報](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a>その他

1) **物理**

    a) 一般に、物理機能を改善する最も簡単な方法は、物理または1秒あたりの反復回数にかかる時間を制限することです。 もちろん、これによりシミュレーションの精度が低下します。 Unity の[TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html)を参照してください。

    b) Unity の colliders の種類には、さまざまなパフォーマンス特性があります。 次の順序では、最もパフォーマンスの高い colliders を左から右へと最もパフォーマンスの低い colliders に一覧表示します。 メッシュの Colliders を回避することは、プリミティブな Colliders よりはるかに高価であることを避けることが最も重要です。

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    詳細については、「 [Unity の物理ベストプラクティス](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)」を参照してください。

2) **動画**

    アニメーターコンポーネントを無効にして、アイドル状態のアニメーションを無効にします (game オブジェクトを無効にしても効果はありません)。 ループ内にアニメーターがあるときに値を同じものに設定する設計パターンは避けてください。 この手法にはかなりのオーバーヘッドがあり、アプリケーションに影響はありません。 [詳細については、こちらをご覧ください。](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **複雑なアルゴリズム**

    アプリケーションで、逆のキネマティック、パス検索などの複雑なアルゴリズムを使用している場合は、より単純なアプローチを見つけたり、パフォーマンスに関連する設定を調整したりします。

## <a name="cpu-to-gpu-performance-recommendations"></a>CPU と GPU のパフォーマンスに関する推奨事項

一般に、CPU と GPU のパフォーマンスは、グラフィックスカードに送信される**描画呼び出し**に対して行われます。 パフォーマンスを向上させるには、描画呼び出しが戦略的に再構築 **)** 、最適な結果を得るために**b)** 必要があります。 描画呼び出し自体はリソースを集中的に使用するため、必要な作業全体を減らすことができます。 さらに、描画呼び出し間の状態変更には、グラフィックスドライバーでのコストの高い検証と変換の手順が必要です。したがって、状態の変化を制限するためにアプリケーションの描画呼び出しを再構築する必要があります (つまり、 さまざまな素材など) によってパフォーマンスが向上します。

Unity には、概要を説明し、そのプラットフォームの描画呼び出しをバッチ処理するためのダイブがあります。
- [Unity 描画呼び出しのバッチ処理](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a>シングルパスインスタンスレンダリング

Unity での単一パスのインスタンスレンダリングでは、各視点の描画呼び出しを1つのインスタンス化描画呼び出しに減らすことができます。 2つの描画呼び出しの間のキャッシュの一貫性により、GPU にもパフォーマンスが向上しています。

Unity プロジェクトでこの機能を有効にするには
1)  **プレーヤーの XR の設定**を開きます ( **[編集]**  > **プロジェクトの設定** > **player** > **XR 設定**)
2) **[ステレオレンダリングメソッド]** ドロップダウンメニューから **[シングルパスインスタンス]** を選択します ( **[Virtual Reality がサポートさ]** れる チェックボックスをオンにする必要があります)

この表示方法の詳細については、Unity から次の記事をお読みください。
- [高度なステレオレンダリングを使用して AR と VR のパフォーマンスを最大化する方法](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [シングルパスのインスタンス化](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> 単一パスのインスタンス化に関する一般的な問題の1つは、開発者が既にインスタンス化用に作成されていない既存のカスタムシェーダーを持っている場合です。 この機能を有効にした後、開発者は、一部のオブジェクトが1つの目にしか表示されないことに気付く場合があります。 これは、関連付けられたカスタムシェーダーに、インスタンス化するための適切なプロパティがないためです。
>
> この問題への対処方法については、Unity[の HoloLens のシングルパスステレオレンダリング](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)に関する説明を参照してください。

#### <a name="static-batching"></a>静的バッチ処理

Unity では、多くの静的オブジェクトをバッチ処理して、GPU への描画呼び出しを減らすことができます。 静的バッチ処理は、Unity では **、1) 同じ素材を共有**し、 **2) すべてが*静的*としてマークされ**ている (unity のオブジェクトを選択し、インスペクターの右上のチェックボックスをクリックする) ため、ほとんどの[レンダラー](https://docs.unity3d.com/ScriptReference/Renderer.html)オブジェクトで動作します)。 *Static*とマークされたユーザーオブジェクトは、アプリケーションのランタイム全体で移動できません。 そのため、事実上、すべてのオブジェクトの配置、移動、スケーリングなどを必要とする HoloLens では、静的バッチ処理を利用することが困難になります。イマーシブヘッドセットの場合、静的なバッチ処理によって描画呼び出しが大幅に減少し、パフォーマンスが向上します。

詳細については、「 [Unity での描画呼び出しのバッチ](https://docs.unity3d.com/Manual/DrawCallBatching.html)処理」の「*静的バッチ*」を参照してください。

#### <a name="dynamic-batching"></a>動的バッチ処理

HoloLens 開発ではオブジェクトを*静的*としてマークするのは問題なので、動的バッチ処理は、このような機能がないことを補うために優れたツールとなります。 もちろん、イマーシブヘッドセットにも役立つことがあります。 Unity で動的バッチ処理を有効にすることは困難ですが、このよう**なオブジェクトは、を**使用する必要があります) 同じ素材を共有し、 **b) 他の条件の長いリストを満たす**ことができます。

完全な一覧については、「 [Unity での描画呼び出しのバッチ](https://docs.unity3d.com/Manual/DrawCallBatching.html)処理」の*動的バッチ*処理を参照してください。 一般に、関連するメッシュデータは300の頂点を超えることができないため、多くの場合、このようなオブジェクトは、動的にバッチ処理されるように無効になります。

#### <a name="other-techniques"></a>その他の方法

バッチ処理は、複数のオブジェクトが同じ素材を共有できる場合にのみ発生します。 通常、これはブロックされます。これは、作成オブジェクトがそれぞれのマテリアルに対して一意のテクスチャを持つ必要があるためです。 テクスチャを1つの大きなテクスチャ ([テクスチャの atlasing](https://en.wikipedia.org/wiki/Texture_atlas)呼ばれるメソッド) にまとめるのが一般的です。

さらに、一般に、可能であれば、メッシュを1つのオブジェクトに結合することをお勧めします。 Unity の各レンダラーには、関連付けられた描画呼び出しと、1つのレンダラーの下で結合メッシュが送信されます。

>[!NOTE]
> 実行時にレンダラーのプロパティを変更すると、マテリアルのコピーが作成されるため、バッチ処理が中断される可能性があります。 オブジェクト間で共有マテリアルのプロパティを変更するには、Renderer を使用します。

## <a name="gpu-performance-recommendations"></a>GPU のパフォーマンスに関する推奨事項

[Unity でのグラフィックスレンダリングの最適化](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)についての詳細情報

### <a name="optimize-depth-buffer-sharing"></a>深度バッファーの共有を最適化する

通常は、**プレーヤーの XR 設定**で**深度バッファーの共有**を有効にして、[ホログラムの安定性](Hologram-stability.md)を最適化することをお勧めします。 ただし、この設定で深さベースの遅延段階の再プロジェクションを有効にする場合は、 **24 ビットの深度形式**ではなく、 **16 ビットの深さ形式**を選択することをお勧めします。 16ビットの深度バッファーによって、深度バッファートラフィックに関連付けられた帯域幅 (および電力) が大幅に減少します。 これは、電力の削減とパフォーマンスの向上の両方に大きなメリットがあります。 ただし、 *16 ビット深度形式*を使用すると、2つの結果が得られる可能性があります。

**Z 戦い**

深度範囲の忠実性を低くすると、 [z の戦い](https://en.wikipedia.org/wiki/Z-fighting)が、16ビットの24ビットで発生する可能性が高くなります。 これらの成果物を回避するには、 [Unity カメラ](https://docs.unity3d.com/Manual/class-Camera.html)の近距離/遠クリッププレーンを変更して、精度を低くします。 HoloLens ベースのアプリケーションでは、Unity の既定の1000m ではなく、50m の遠くのクリッププレーンによって、一般に z 戦いを排除できます。

**無効なステンシルバッファー**

Unity が[16 ビット深度でレンダリングテクスチャ](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html)を作成する場合、ステンシルバッファーは作成されません。 各 Unity ドキュメントに対して24ビットの深さ形式を選択すると、24ビットの z バッファーと[8 ビットのステンシルバッファー](https://docs.unity3d.com/Manual/SL-Stencil.html)が作成されます (デバイスに32ビットが適用されている場合は、通常は HoloLens など)。

### <a name="avoid-full-screen-effects"></a>全画面表示の効果を避ける

全画面で動作する手法は、すべてのフレームに対して数百万の操作が行われるため、非常にコストが高くなる可能性があります。 したがって、アンチエイリアシング、ブルームなどの[処理後の効果](https://docs.unity3d.com/Manual/PostProcessingOverview.html)を避けることをお勧めします。

### <a name="optimal-lighting-settings"></a>最適な光源設定

Unity で[リアルタイムのグローバルな照明](https://docs.unity3d.com/Manual/GIIntro.html)を使用すると、視覚的な結果を得ることができますが、非常にコストのかかる照明計算が含まれます。 **ウィンドウ** > 使用してすべての Unity シーンファイルのリアルタイムグローバル照明を無効にすることをお勧めします。これに**より、リアルタイムのグローバルな照明**> オフにして > 光源の**設定**が**表示**されます。

さらに、すべてのシャドウキャストを無効にすることをお勧めします。これにより、Unity シーンに負荷の高い GPU パスも追加されます。 影はライトごとに無効にすることができますが、品質設定を使用して総合的を制御することもできます。

 > **プロジェクトの設定**を**編集**し、 **[品質]** カテゴリを選択 > UWP プラットフォームの **[低品質]** を選択します。 また、 **shadows**プロパティを設定して、**影を無効**にすることもできます。

### <a name="reduce-poly-count"></a>Poly 数を減らす

通常、Polygon カウントは
1) シーンからのオブジェクトの削除
2) 指定されたメッシュの多角形の数を減らす資産の決定
3) アプリケーションに[詳細レベル (LOD) システム](https://docs.unity3d.com/Manual/LevelOfDetail.html)を実装して、同じ geometry の低いポリゴンバージョンで遠く離れたオブジェクトをレンダリングする

### <a name="understanding-shaders-in-unity"></a>Unity のシェーダーについて

シェーダーをパフォーマンスで比較するための簡単な方法は、実行時に各操作が実行される平均操作数を特定することです。 これは、Unity で簡単に実行できます。

1) シェーダー資産を選択するか、素材を選択します。次に、[インスペクター] ウィンドウの右上隅にある歯車アイコンを選択し、[**シェーダーの選択]** をクリックします。

    ![Unity でシェーダーを選択する](images/Select-shader-unity.png)
2) シェーダー資産を選択した状態で、インスペクター ウィンドウの下にある **コードのコンパイルと表示** ボタンをクリックします。

    ![Unity でシェーダーコードをコンパイルする](images/compile-shader-code-unity.PNG)

3) コンパイル後、頂点シェーダーとピクセルシェーダーの両方の異なる操作の数を使用して、結果の統計セクションを探します (注: ピクセルシェーダーはフラグメントシェーダーとも呼ばれます)。

    ![Unity の標準シェーダー操作](images/unity-standard-shader-compilation.png)

#### <a name="optmize-pixel-shaders"></a>ピクセルシェーダーの最適化

上記のメソッドを使用してコンパイルされた統計結果を確認すると、通常、[フラグメントシェーダー](https://en.wikipedia.org/wiki/Shader#Pixel_shaders)は[頂点シェーダー](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)よりも多くの操作を平均で実行します。 フラグメントシェーダーは、ピクセルシェーダーとも呼ばれ、画面出力のピクセルごとに実行されます。一方、頂点シェーダーは、画面に描画されるすべてのメッシュの頂点ごとに実行されます。 

したがって、すべての光源の計算のために、頂点シェーダーよりも多くの命令を持つフラグメントシェーダーだけでなく、ほとんどの場合、フラグメントシェーダーは大規模なデータセットで実行されます。 たとえば、画面出力が 2k x 2k のイメージの場合、フラグメントシェーダーは 2000 * 2000 = 400万回実行されます。 2つの画面が表示される場合、2つの画面があるため、この数は2倍になります。 混合の現実アプリケーションに複数のパス、全画面の処理後の影響、または複数のメッシュを同じピクセルにレンダリングする場合は、この数が大幅に増加します。 

そのため、フラグメントシェーダー内の操作の数を減らすと、通常、頂点シェーダーの最適化よりもはるかに高いパフォーマンスが得られます。

#### <a name="unity-standard-shader-alternatives"></a>Unity 標準シェーダーの代替手段

物理的ベースのレンダリング (.PBR) やその他の高品質シェーダーを使用する代わりに、より高性能で安価なシェーダーを利用することを検討してください。 [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)には、mixed reality プロジェクト用に最適化された[mrtk standard shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)が用意されています。

Unity では、Unity 標準シェーダーと比較して、unlit、頂点の lit、拡散、およびその他の単純化されたシェーダーオプションも提供されます。 詳細については[、「組み込みシェーダーの使用状況とパフォーマンス](https://docs.unity3d.com/Manual/shader-Performance.html)」を参照してください。

#### <a name="shader-preloading"></a>シェーダーのプリロード

シェーダーの[読み込み時間](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html)を最適化するには、*シェーダーのプリ*ロードやその他のテクニックを使用します。 特に、シェーダーのプリロードは、ランタイムシェーダーのコンパイルによって hitches が表示されないことを意味します。

### <a name="limit-overdraw"></a>オーバードローを制限する

Unity では、**シーンビュー**の左上隅にある [[**描画モード] メニュー**](https://docs.unity3d.com/Manual/ViewModes.html)を切り替えて、 **[オーバードロー]** を選択すると、シーンのオーバードローを表示できます。

一般に、GPU に送信される前にオブジェクトを事前にカリングすることで、オーバードローを軽減できます。 Unity は、エンジンに対して[遮蔽カリング](https://docs.unity3d.com/Manual/OcclusionCulling.html)を実装する方法について詳しく説明します。

## <a name="memory-recommendations"></a>メモリに関する推奨事項

過剰なメモリ割り当て & 解放操作によって holographic アプリケーションに悪影響を及ぼす可能性があるため、パフォーマンスが低下したり、フレームが固定されたり、その他の有害な動作が発生したりする可能性があります。 メモリ管理はガベージコレクターによって制御されるため、Unity で開発するときは、メモリに関する考慮事項を理解することが特に重要です。

#### <a name="garbage-collection"></a>ガベージコレクション

Holographic アプリは、GC がアクティブ化され、実行中にスコープ外になったオブジェクトを分析し、そのメモリを解放して再利用できるようにする必要がある場合、ガベージコレクター (GC) への処理時間が緩やかになります。 通常、一定の割り当てと割り当て解除では、ガベージコレクターの実行頻度を高くする必要があります。その結果、低下のパフォーマンスとユーザーエクスペリエンスが向上します。

Unity では、ガベージコレクターのしくみを詳しく説明する優れたページと、メモリ管理に関してより効率的なコードを記述するためのヒントが提供されています。
- [Unity ゲームでのガベージコレクションの最適化](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

ガベージコレクションが過剰になる最も一般的な方法の1つは、Unity 開発のコンポーネントおよびクラスへの参照をキャッシュしないことです。 すべての参照は、Start () または起動中 () にキャプチャし、Update () や Behaviour () などの後の関数で再利用する必要があります。

その他のクイックヒント:
- [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C#クラスを使用して、実行時に複雑な文字列を動的に構築する
- アプリケーションのすべてのビルドバージョンでまだ実行されているため、必要がなくなったときに、デバッグログ () への呼び出しを削除します。
- Holographic アプリで一般的に多くのメモリが必要な場合は、読み込み中または移行画面を表示するときなど、読み込みフェーズ中に、 [ _**System. GC ()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2)を呼び出すことを検討してください。

#### <a name="object-pooling"></a>オブジェクトプール

オブジェクトプールは、オブジェクトの割り当て解除 & の継続的な割り当てのコストを削減するための一般的な手法です。 これを行うには、同一のオブジェクトの大規模なプールを割り当て、時間の経過と共にオブジェクトを絶えず破棄するのではなく、このプールから使用可能な非アクティブなインスタンスを再利用します。 オブジェクトプールは、アプリの有効期間が可変の再使用可能なコンポーネントに最適です。

- [Unity でのオブジェクトプールのチュートリアル](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>起動時のパフォーマンス

より小さなシーンでアプリを起動し、 *[SceneManager](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* を使用してシーンの残りの部分を読み込むことを検討してください。 これにより、アプリは可能な限り高速に対話型状態になることができます。 新しいシーンをアクティブ化し、レンダリングされたコンテンツが途切れたり順調したりする可能性がある場合は、CPU のスパイクが大きくなる可能性があることに注意してください。 この問題を回避する方法の1つとして、読み込まれるシーンで allowSceneActivation プロパティを false に設定し、シーンが読み込まれるまで待機します。次に、画面を黒にオフにし、AsyncOperation を true に設定してシーンのアクティブ化を完了します。

スタートアップシーンが読み込まれている間、holographic スプラッシュ画面がユーザーに表示されることに注意してください。

## <a name="see-also"></a>関連項目
- [Unity ゲームでのグラフィックスレンダリングの最適化](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [Unity ゲームでのガベージコレクションの最適化](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- [物理的なベストプラクティス [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)
- [スクリプトの最適化 [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)
