---
title: Unity のパフォーマンスに関する推奨事項
description: 複合現実アプリを使用してパフォーマンスを向上させるために unity に固有のヒント。
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: 表示、ガベージ コレクション、hololens、グラフィック、cpu、gpu
ms.openlocfilehash: 37eac566a0315009330ac7fee96edd82348d6ba3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604911"
---
# <a name="performance-recommendations-for-unity"></a>Unity のパフォーマンスに関する推奨事項

今回は説明に記載されている[複合現実のパフォーマンスに関する推奨事項](understanding-performance-for-mixed-reality.md)が、Unity エンジンの環境に固有の教訓について説明します。

開発者が確認すること強くお勧めしますも、 [Unity 資料の環境の設定をお勧めします](Recommended-settings-for-unity.md)します。 この記事では、パフォーマンスの高い Mixed Reality アプリの構築においていくつかの最も重要なシーン構成内容を持っています。 これらの推奨設定の一部が強調表示の下にもします。

## <a name="how-to-profile-with-unity"></a>Unity でプロファイルする方法

Unity は、 **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** 組み込み優れたリソースが、特定のアプリのパフォーマンスの貴重な洞察を収集します。 エディターでプロファイラーを実行する 1 つは、これらのメトリックは、true のランタイム環境を表していないと、これからの結果があるため注意が必要です。 最も正確な実用的な情報をデバイスで実行中にアプリケーションをリモートでプロファイルに勧めします。 さらに、Unity の[フレーム デバッガー](https://docs.unity3d.com/Manual/FrameDebugger.html)も非常に強力なと分析情報ツールを利用します。

Unity では、優れたドキュメントを提供します。
1) 接続する方法、 [Unity profiler UWP アプリケーションをリモートで](https://docs.unity3d.com/Manual/windowsstore-profiler.html)
2) 方法を効果的に[Unity Profiler でパフォーマンスの問題の診断](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)

>[!NOTE]
> 接続されている Unity Profiler とは、GPU プロファイラーを追加した後 (を参照してください*追加 Profiler*右上隅で)、どの程度時間を要している CPU および GPU ではそれぞれ、プロファイラーの途中でいずれかを確認できます。 これにより、開発者は、アプリケーションが CPU または GPU の境界付けられた場合にクイック近似を取得できます。
>
> ![Unity CPU と GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>CPU のパフォーマンスに関する推奨事項

以下のコンテンツより詳細なパフォーマンス手法、Unity の特に対象となる &C#開発します。

#### <a name="cache-references"></a>キャッシュの参照

ベスト プラクティスの初期化時のすべての関連するコンポーネントおよび Gameobject に参照をキャッシュすることをお勧めします。 これなどの関数呼び出しを繰り返すため*[GetComponent\<T > ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* は相対メモリのポインターを格納するためにコストが大幅に高価です。 これにも当てはまりますに、非常に、定期的に使用する[Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html)します。 *Camera.main*に実際にしか使用*[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* 低いコスト カメラはシーン グラフを検索する下、 *"MainCamera"* タグ。

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

>[!NOTE] Avoid GetComponent(string) <br/>
> 使用する場合 *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)*、さまざまなオーバー ロードが多数があります。 このデータベースが、ベース型の実装としない文字列に基づく検索オーバー ロードを常に使用する重要です。 シーン内の文字列で検索することは、型を検索するよりも大幅に高額です。 <br/>
> (良好)コンポーネント GetComponent (型) <br/>
> (良好)T GetComponent\<T >) <br/>
> (不良)コンポーネント GetComponent(string) > <br/>

#### <a name="avoid-expensive-operations"></a>負荷の高い操作を回避します。

1) **使用を防ぐ[LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**

    LINQ は、非常にクリーンで読み取りし、書き込みを簡単にできますが、さらに多くの計算と特に多くのメモリ割り当て手動でアルゴリズムを記述するよりもが一般に必要です。

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) **一般的な Unity Api**

    特定の Unity Api 機能は便利を実行する非常にコストことがあります。 これらのほとんどは、Gameobject の一致するいくつか一覧については、シーン全体のグラフの検索に関連します。 これらの操作は、参照をキャッシュまたは実行時に参照を追跡するには、対象の Gameobject の manager コンポーネントの実装によって一般的に回避できます。

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> *[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* と*[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* 代価除去する必要があります。 これらの関数は、1000 x 関数を直接呼び出すよりも低速の順序指定できます。

3) **ボックス化に注意してください。**

    [ボックス化](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing)はのコア概念であり、C#言語とランタイム。 参照型の変数に char、int、bool などの値に型指定された変数の折り返しのプロセスです。 値に型指定された変数が"boxed"では、マネージ ヒープに格納されている System.Object 内部でラップされます。 したがって、メモリが割り当てられていると、最終的に破棄されたときに、ガベージ コレクターによって処理する必要があります。 これらの割り当てと解放、パフォーマンス コストが発生し、多くのシナリオでは必要ありませんまたは安価な代替手段によって簡単に置き換えることができます。

#### <a name="repeating-code-paths"></a>繰り返しのコード パス

繰り返しの Unity コールバック関数 (つまり、 更新プログラム) 1 秒あたり何度も実行されている、またはフレームを非常に慎重に記述する必要があります。 ここで負荷の高い操作には、パフォーマンスに大きく、一貫性のある可能性があります。

1) **空のコールバック関数**

    次のコードをすべて Unity スクリプト自動初期化を次のコード ブロックで以降は特に、アプリケーションをそのまま無害に見える可能性がありますこれら空のコールバックに非常に不経済実際になります。 Unity は、UnityEngine コードと、アプリケーション コードの間、コードのアンマネージ/マネージの境界を越えた双方向とは動作します。 実行するものがない場合でも、コンテキストのこのブリッジ経由での切り替えはかなり安価です。 これは、アプリがある空の繰り返し Unity コールバックのコンポーネントを持つ Gameobject の何百場合に特に問題になります。

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> Update() はこのパフォーマンスの問題の最も一般的な形が、次などの他の繰り返し Unity コールバックは均等に悪くない最悪の場合。FixedUpdate()、LateUpdate()、OnPostRender"、OnPreRender()、OnRenderImage() など。 

2) **操作 1 回実行しているどちらを優先するフレームごと**

    次の Unity Api は、Holographic アプリの多くの一般的な操作です。 常に可能ではない、ですが、これらの関数から結果を 1 回計算する非常によくし、結果は、特定のフレームのアプリケーション全体にわたって再利用します。

    専用シングルトン クラスまたはサービスを視線入力 Raycast をシーンに処理し、その他のシーン、すべてのコンポーネントごとに繰り返されると、実質的に同じ Raycast 操作を行う代わりにこの結果を再利用することをお勧めは通常、a)コンポーネント。 もちろん、一部のアプリケーションが raycasts またはに対して異なるさまざまな配信元からを必要があります[LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html)します。

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    b) で Update() のような繰り返しの Unity コールバックで GetComponent() 操作を回避する[の参照をキャッシュ](#cache-references)Start() または Awake()

        UnityEngine.Object.GetComponent()

    c) は初期化で使用可能であれば、すべてのオブジェクトをインスタンス化することをお勧め[オブジェクト プーリング](#object-pooling)リサイクルし、アプリケーションのランタイム全体にわたって Gameobject を再利用するには

        UnityEngine.Object.Instantiate()

3) **インターフェイスと仮想の構成要素を回避します。**

    Vs ダイレクト オブジェクトのインターフェイスを通じて関数呼び出しを起動または仮想関数を呼び出すことがよくありますできます直接コンストラクトまたは関数の直接呼び出しを使用するよりもはるかに高くなります。 仮想関数またはインターフェイスが必要な場合は、削除する必要があります。 ただし、パフォーマンスへのこれらの方法に影響は、通常のトレードオフの価値が開発のコラボレーション、コードの読みやすさ、およびコードの保守性を簡略化に利用する場合。 

4) **値構造体の受け渡しを避ける**

    クラスと異なり、構造体は、値型と関数に直接渡されると、新しく作成されたインスタンスにその内容がコピーされます。 このコピーは、コスト、スタックに追加のメモリと CPU を追加します。 小さな構造体は、効果は、通常は最小限にし、許容されるためです。 ただし、関数は、すべてのフレームを繰り返し呼び出すのと同様に大規模な構造体を取得する関数は可能であれば、参照渡しの関数定義を変更します。 [詳細はこちら](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a>その他

1) **物理学**

    a) 一般的には、物理運動を向上させるために簡単では、物理運動または 1 秒あたりのイテレーションの数に費やされた時間の量を制限します。 もちろん、これにより、シミュレーションの正確性が減少します。 参照してください[TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) Unity で

    b) Unity でコライダーの種類では、大きく異なるパフォーマンス特性があります。 以下の順番は、最低のパフォーマンスの高いコライダーを左から右へのほとんどのパフォーマンスの高いコライダーを一覧表示します。 プリミティブのコライダーよりも大幅に高価であるメッシュ コライダーを回避するために最も重要です。

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    参照してください[Unity 物理学のベスト プラクティス](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)の詳細

2) **アニメーション**

    Animator コンポーネントを無効にしてアイドル状態のアニメーションを無効にする (ゲーム オブジェクトを無効にすると同じ効果が)。 アニメーターが同じものを値を設定、ループ内に存在する設計パターンを回避します。 この手法でアプリケーションに影響をかなりのオーバーヘッドがあります。 [詳細について説明します。](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **複雑なアルゴリズム**

    簡単な方法を見つけたり、パフォーマンスに関連する設定を調整する場合は、アプリケーションは、複雑なアルゴリズム (インバース キネマティクス、パスの検索など) を使用して、なります

## <a name="cpu-to-gpu-performance-recommendations"></a>CPU、GPU にパフォーマンスに関する推奨事項

一般に、CPU、GPU にパフォーマンスが得られる下に、**描画呼び出し**グラフィックス カードに送信します。 描画呼び出しをパフォーマンスを向上させるのには、戦略的にする必要がある **) 削減**または**b) 再編成**最善の結果。 描画呼び出し自体は、リソース集中型であるためそれらを減らすために必要な作業は全体を削減できます。 描画呼び出し間の変更はコストのかかる検証を必要とし、グラフィックス ドライバーの変換のステップをさらに、状態にあり、したがって、制限の状態の変更 (つまり、アプリケーションの描画呼び出しの再構築 さまざまな資料など) は、パフォーマンスを向上させることができます。

Unity では、概要を説明し、そのプラットフォームの描画呼び出しをバッチ処理に踏み込みます優れた記事には。
- [Unity の描画呼び出しがバッチ処理](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a>1 回インスタンス化されたレンダリング

Unity での単一パス Instanced レンダリングで描画呼び出しをインスタンス化された 1 つの描画呼び出しに短縮する目ごとにできます。 2 つの描画呼び出し間のキャッシュの一貫性のためのパフォーマンスの向上も GPU 上でもあります。

Unity プロジェクトでこの機能を有効にするには
1)  開いている**Player XR 設定**(に移動**編集** > **プロジェクト設定** > **Player**  > **XR 設定**)
2) 選択**1 つ渡すインスタンス化**から、**ステレオのレンダリング方法**ドロップダウン メニュー (**仮想現実サポート**チェック ボックスを選択する必要があります)

詳細についてはこのレンダリング アプローチで、Unity から、次の記事を読み取ります。
- [AR および VR の高度なステレオ レンダリング パフォーマンスを最大化する方法](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [1 つのパスがインスタンス化](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> 1 つ渡すレンダリングをインスタンス化で 1 つの一般的な問題は、開発者が既に既存のカスタム シェーダーに書かれていない場合に発生します。 インスタンス化します。 この機能を有効にした後は、開発者は 1 つ目のいくつかの Gameobject のみレンダリングをことがあります。 これは、関連付けられているカスタムのシェーダーの適切なプロパティがあるないためにインスタンス化します。
>
> 参照してください[1 つ渡すステレオのレンダリング HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)から Unity のこの問題に対処する方法

#### <a name="static-batching"></a>静的なバッチ処理

Unity は、GPU の描画呼び出しを減らすために多くの静的オブジェクトをバッチ処理することです。 静的なバッチ処理のほとんどの動作[レンダラー](https://docs.unity3d.com/ScriptReference/Renderer.html) Unity 内のオブジェクトを**1) 同じ素材を共有する**と**は 2) としてマークされているすべて*静的*** (Unity でオブジェクトを選択し、上にあるチェック ボックスをオン、インスペクターの右)。 としてマークされている GameObjects*静的*アプリケーションのランタイム全体で移動することはできません。 したがって、静的なバッチ処理はほとんどすべてのオブジェクトが移動された、スケーリングなど、配置する必要がある HoloLens の活用の困難さできます。イマーシブ ヘッドセットの静的バッチ処理できます描画呼び出しを大幅に削減し、パフォーマンスが向上します。

読み取り*静的バッチ処理* [Unity でバッチ処理を呼び出す描画](https://docs.unity3d.com/Manual/DrawCallBatching.html)の詳細。

#### <a name="dynamic-batching"></a>動的なバッチ処理

オブジェクトとしてマークする問題であるため*静的*HoloLens の開発、動的なバッチ処理できるでこれを補正する優れたツール機能が不足しています。 もちろん、イマーシブ ヘッドセットもで役に立ちます。 Unity でバッチ処理を動的なは難しいが Gameobject にする必要がありますので、有効にする **) 共有は同じ素材**と**b) 多数の他の条件を満たす**します。

読み取り*動的バッチ処理* [Unity でバッチ処理を呼び出す描画](https://docs.unity3d.com/Manual/DrawCallBatching.html)完全な一覧についてはします。 ほとんどの場合、GameObjects は、バッチ処理する動的に関連付けられているメッシュ データとして使用できるは、300 個の頂点ので無効になります。

#### <a name="other-techniques"></a>その他の手法

バッチ処理と複数 GameObjects は同じ素材を共有することがある場合のみ実行できます。 通常、それぞれの素材に対する一意のテクスチャを持つ Gameobject のですが、ブロックされます。 1 つの大きなテクスチャと呼ばれるメソッドにテクスチャを結合するが一般的[テクスチャ Atlasing](https://en.wikipedia.org/wiki/Texture_atlas)します。

さらに、可能であり、適切な場所に 1 つの GameObject にメッシュを結合することをお勧めです。 Unity では、各レンダラーが、描画呼び出しの 1 つのレンダラーで結合されたメッシュの送信とが関連付けられています。 

>[!NOTE]
> Renderer.material の実行時のプロパティの変更とをマテリアルのコピーを作成し、したがってできなくなる可能性のバッチ処理します。 Renderer.sharedMaterial を使用すると、Gameobject の間で共有の素材プロパティを変更できます。

## <a name="gpu-performance-recommendations"></a>GPU のパフォーマンスに関する推奨事項

詳細については[Unity でのグラフィックス レンダリングの最適化](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)

#### <a name="reduce-poly-count"></a>ポリゴンの数を削減します。

いずれかで多角形の数が減少通常
1) シーンからオブジェクトを削除します。
2) 指定したメッシュの多角形の数が減少する資産デシメーション
3) 実装する、[詳細レベル (LOD) のシステム](https://docs.unity3d.com/Manual/LevelOfDetail.html)を離れた同じジオメトリの多角形の下のバージョンを持つオブジェクトを描画するアプリケーションに

#### <a name="limit-overdraw"></a>制限を範囲します。

Unity では、1 つを表示できますを切り替えることにより、そのシーンを描画できます、 [**モード メニューを描画**](https://docs.unity3d.com/Manual/ViewModes.html)の左上隅にある、**シーン ビュー**選択**アルファブレンディング**.

一般に、範囲を事前に、GPU に送信される前にオブジェクトをカリング軽減できます。 Unity を実装する方法の詳細を提供する[オクルー ジョン カリング](https://docs.unity3d.com/Manual/OcclusionCulling.html)のエンジン。

#### <a name="understanding-shaders-in-unity"></a>Unity でシェーダーを理解します。

パフォーマンスでシェーダーを比較する簡単な近似は、各操作の平均数を識別するために実行時に実行します。 これは、Unity で非常に簡単に行うことができます。

1) シェーダー資産を選択または素材を選択し、続いてインスペクター ウィンドウの上部右隅にある、歯車アイコンを選択し、 **「シェーダーの選択」**

    ![Unity でシェーダーを選択します。](images/Select-shader-unity.png)
2) 選択したシェーダー アセット、クリックして、 **「コンパイルし、コードの表示」** インスペクター ウィンドウの下のボタン

    ![Unity でシェーダー コードをコンパイルします。](images/compile-shader-code-unity.PNG)

3) コンパイルの後、結果に統計情報 セクションを検索、頂点とピクセル シェーダーのさまざまな操作の数 (注: ピクセル シェーダーでは、フラグメント シェーダーも多くの場合と呼ばれます)

    ![Unity シェーダーの標準的な操作](images/unity-standard-shader-compilation.png)

##### <a name="unity-standard-shader-alternatives"></a>Unity シェーダーの標準的な代替手段

効率的に利用して物理的にベースのレンダリング (PBR) やその他の高品質なシェーダーを使用せずに確認し、安価なシェーダー。 [実際にはツールキットを混在](https://github.com/Microsoft/MixedRealityToolkit-Unity)を提供します、[標準シェーダー](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/MixedRealityStandard.shader)複合現実プロジェクト向けに最適化されたをします。

Unity では、光源、なし、頂点が点灯している、高速比較が大幅に簡略化されたシェーダーの拡散、およびその他のオプションも、標準の Unity シェーダーに提供します。 参照してください[使用状況と組み込みのシェーダーのパフォーマンスを](https://docs.unity3d.com/Manual/shader-Performance.html)詳細な情報。

## <a name="memory-recommendations"></a>メモリの推奨事項

過剰なメモリの割り当てと割り当て解除の操作、holographic アプリケーションを一貫性のないパフォーマンス、固定されたフレーム、およびその他の好ましくない動作に影響を受けることができます。 これは、方法は、メモリ管理は、ガベージ コレクターによって制御されるため、Unity で開発するときは、メモリに関する考慮事項を理解するのには特に重要です。

#### <a name="garbage-collection"></a>ガベージ コレクション

Holographic アプリ、不要になったスコープの実行中にオブジェクトを分析する、GC がアクティブになるし、メモリにできる再利用できるようにリリースする必要があるガベージ コレクター (GC) の処理コンピューティング時間が失われます。 定数の割り当てと割り当て解除したがって傷つけるパフォーマンスとユーザー エクスペリエンスをより頻繁に実行するガベージ コレクターが一般に必要です。

Unity は、ガベージ コレクターのしくみを詳しく説明する優れたページとメモリ管理においてより効率的なコードを記述するためのヒントを提供しています。
- [Unity ゲームでのガベージ コレクションの最適化](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

過度なガベージ コレクションにつながる最も一般的なプラクティスの 1 つがコンポーネントおよび Unity 開発におけるクラスへの参照をキャッシュできません。 すべての参照は Start() または Awake() 中にキャプチャし、Update() LateUpdate() などの以降の関数で再利用する必要があります。

その他のクイック ヒント:
- 使用して、 [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C#クラスで動的に実行時に複雑な文字列をビルドするには
- Debug.Log() アプリのすべてのビルド バージョンで引き続き実行時に不要になったときに呼び出しを削除します
- Holographic アプリは、一般に、大量のメモリを必要とする場合は、呼び出すことを検討してください[ _**System.GC.Collect()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2)などのフェーズを読み込み中に、読み込みを提示するとき、または画面の切り替え

#### <a name="object-pooling"></a>オブジェクト プール

オブジェクト プールは、オブジェクトの割り当て解除 (&)、継続的な割り当てのコストを削減する、一般的な手法です。 これは、同一のオブジェクトの大きなプールを割り当てると、常に生成し、時間の経過と共にオブジェクトを破棄するのではなく、このプールから再アクティブでない、利用可能なインスタンスを使用して実行します。 オブジェクト プールは、アプリの中に変数の有効期間を持つ再利用可能なコンポーネントに適しています。

- [オブジェクト プールの Unity のチュートリアル](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>起動時のパフォーマンス

小規模のシーンをアプリを起動しを使用する必要があります*[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* を残りのシーンを読み込みます。 これにより、アプリをできる限り早く対話状態を取得できます。 対応をある可能性があります、大きな CPU スパイク新しいシーンがアクティブ化中に、レンダリングされたコンテンツが途切れこと」または「問題。 これを回避する方法の 1 つは、読み込まれているシーンで AsyncOperation.allowSceneActivation プロパティを false に設定、読み込み、黒に画面のクリア、および、戻るシーンのアクティブ化が完了する場合は true に設定してシーンの待機です。

スタートアップ シーンの読み込み中に、holographic のスプラッシュ スクリーンは、ユーザーに表示されることに注意してください。

## <a name="see-also"></a>関連項目
- [Unity ゲームのグラフィックス レンダリングの最適化](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [Unity ゲームでのガベージ コレクションの最適化](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- [物理運動のベスト プラクティス [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)
- [スクリプト [Unity] の最適化](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)
