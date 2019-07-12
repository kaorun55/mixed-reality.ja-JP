---
title: Unity のパフォーマンスに関する推奨事項
description: 複合現実アプリを使用してパフォーマンスを向上させるために unity に固有のヒント。
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: 表示、ガベージ コレクション、hololens、グラフィック、cpu、gpu
ms.openlocfilehash: b0821f07184bff8630f6b6af0d0fc461f6fcd133
ms.sourcegitcommit: 8f3ff9738397d9b9fdf4703b14b89d416f0186a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2019
ms.locfileid: "67843334"
---
# <a name="performance-recommendations-for-unity"></a><span data-ttu-id="2193a-104">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="2193a-104">Performance recommendations for Unity</span></span>

<span data-ttu-id="2193a-105">今回は説明に記載されている[複合現実のパフォーマンスに関する推奨事項](understanding-performance-for-mixed-reality.md)が、Unity エンジンの環境に固有の教訓について説明します。</span><span class="sxs-lookup"><span data-stu-id="2193a-105">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md) but focuses on learnings specific to the Unity engine environment.</span></span>

<span data-ttu-id="2193a-106">開発者が確認すること強くお勧めしますも、 [Unity 資料の環境の設定をお勧めします](Recommended-settings-for-unity.md)します。</span><span class="sxs-lookup"><span data-stu-id="2193a-106">It is also highly advisable that developers review the [recommended environment settings for Unity article](Recommended-settings-for-unity.md).</span></span> <span data-ttu-id="2193a-107">この記事では、パフォーマンスの高い Mixed Reality アプリの構築においていくつかの最も重要なシーン構成内容を持っています。</span><span class="sxs-lookup"><span data-stu-id="2193a-107">This article has content with some of the most important scene configurations in regards to building performant Mixed Reality apps.</span></span> <span data-ttu-id="2193a-108">これらの推奨設定の一部が強調表示の下にもします。</span><span class="sxs-lookup"><span data-stu-id="2193a-108">Some of these recommended settings are highlighted below as well.</span></span>

## <a name="how-to-profile-with-unity"></a><span data-ttu-id="2193a-109">Unity でプロファイルする方法</span><span class="sxs-lookup"><span data-stu-id="2193a-109">How to profile with Unity</span></span>

<span data-ttu-id="2193a-110">Unity は、 **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** 組み込み優れたリソースが、特定のアプリのパフォーマンスの貴重な洞察を収集します。</span><span class="sxs-lookup"><span data-stu-id="2193a-110">Unity provides the **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** built-in which is a great resource to gather valuable performance insights for your particular app.</span></span> <span data-ttu-id="2193a-111">エディターでプロファイラーを実行する 1 つは、これらのメトリックは、true のランタイム環境を表していないと、これからの結果があるため注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="2193a-111">Although one can run the profiler in-editor, these metrics do not represent the true runtime environment and thus, results from this should be used cautiously.</span></span> <span data-ttu-id="2193a-112">最も正確な実用的な情報をデバイスで実行中にアプリケーションをリモートでプロファイルに勧めします。</span><span class="sxs-lookup"><span data-stu-id="2193a-112">It is recommended to remotely profile your application while running on device for most accurate and actionable insights.</span></span> <span data-ttu-id="2193a-113">さらに、Unity の[フレーム デバッガー](https://docs.unity3d.com/Manual/FrameDebugger.html)も非常に強力なと分析情報ツールを利用します。</span><span class="sxs-lookup"><span data-stu-id="2193a-113">Further, Unity's [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html)  is also a very powerful and insight tool to utilize.</span></span>

<span data-ttu-id="2193a-114">Unity では、優れたドキュメントを提供します。</span><span class="sxs-lookup"><span data-stu-id="2193a-114">Unity provides great documentation for:</span></span>
1) <span data-ttu-id="2193a-115">接続する方法、 [Unity profiler UWP アプリケーションをリモートで](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span><span class="sxs-lookup"><span data-stu-id="2193a-115">How to connect the [Unity profiler to UWP applications remotely](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span></span>
2) <span data-ttu-id="2193a-116">方法を効果的に[Unity Profiler でパフォーマンスの問題の診断](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span><span class="sxs-lookup"><span data-stu-id="2193a-116">How to effectively [diagnose performance problems with the Unity Profiler](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span></span>

>[!NOTE]
> <span data-ttu-id="2193a-117">接続されている Unity Profiler とは、GPU プロファイラーを追加した後 (を参照してください*追加 Profiler*右上隅で)、どの程度時間を要している CPU および GPU ではそれぞれ、プロファイラーの途中でいずれかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="2193a-117">With the Unity Profiler connected and after adding the GPU profiler (see *Add Profiler* in top right corner), one can see how much time is being spent on the CPU & GPU respectively in the middle of the profiler.</span></span> <span data-ttu-id="2193a-118">これにより、開発者は、アプリケーションが CPU または GPU の境界付けられた場合にクイック近似を取得できます。</span><span class="sxs-lookup"><span data-stu-id="2193a-118">This allows the developer to get a quick approximation if their application is CPU or GPU bounded.</span></span>
>
> ![Unity CPU と GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a><span data-ttu-id="2193a-120">CPU のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="2193a-120">CPU performance recommendations</span></span>

<span data-ttu-id="2193a-121">以下のコンテンツより詳細なパフォーマンス手法、Unity の特に対象となる &C#開発します。</span><span class="sxs-lookup"><span data-stu-id="2193a-121">The content below covers more in-depth performance practices, especially targeted for Unity & C# development.</span></span>

#### <a name="cache-references"></a><span data-ttu-id="2193a-122">キャッシュの参照</span><span class="sxs-lookup"><span data-stu-id="2193a-122">Cache references</span></span>

<span data-ttu-id="2193a-123">ベスト プラクティスの初期化時のすべての関連するコンポーネントおよび Gameobject に参照をキャッシュすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2193a-123">It is best practice to cache references to all relevant components and GameObjects at initialization.</span></span> <span data-ttu-id="2193a-124">これなどの関数呼び出しを繰り返すため *[GetComponent\<T > ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* は相対メモリのポインターを格納するためにコストが大幅に高価です。</span><span class="sxs-lookup"><span data-stu-id="2193a-124">This is because repeating function calls such as *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* are significantly more expensive relative to the memory cost to store a pointer.</span></span> <span data-ttu-id="2193a-125">これにも当てはまりますに、非常に、定期的に使用する[Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html)します。</span><span class="sxs-lookup"><span data-stu-id="2193a-125">This also applies to to the very, regularly used [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).</span></span> <span data-ttu-id="2193a-126">*Camera.main*に実際にしか使用 *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* 低いコスト カメラはシーン グラフを検索する下、 *"MainCamera"* タグ。</span><span class="sxs-lookup"><span data-stu-id="2193a-126">*Camera.main* actually just uses *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* underneath which expensively searches your scene graph for a camera object with the *"MainCamera"* tag.</span></span>

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
> <span data-ttu-id="2193a-127">Avoid GetComponent(string)</span><span class="sxs-lookup"><span data-stu-id="2193a-127">Avoid GetComponent(string)</span></span> <br/>
> <span data-ttu-id="2193a-128">使用する場合 *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 、さまざまなオーバー ロードが多数があります。</span><span class="sxs-lookup"><span data-stu-id="2193a-128">When using *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)*, there are a handful of different overloads.</span></span> <span data-ttu-id="2193a-129">このデータベースが、ベース型の実装としない文字列に基づく検索オーバー ロードを常に使用する重要です。</span><span class="sxs-lookup"><span data-stu-id="2193a-129">It is important to always use the Type based implementations and never the string-based searching overload.</span></span> <span data-ttu-id="2193a-130">シーン内の文字列で検索することは、型を検索するよりも大幅に高額です。</span><span class="sxs-lookup"><span data-stu-id="2193a-130">Searching by string in your scene is significantly more costly than searching by Type.</span></span> <br/>
> <span data-ttu-id="2193a-131">(良好)コンポーネント GetComponent (型)</span><span class="sxs-lookup"><span data-stu-id="2193a-131">(Good) Component GetComponent(Type type)</span></span> <br/>
> <span data-ttu-id="2193a-132">(良好)T GetComponent\<T >)</span><span class="sxs-lookup"><span data-stu-id="2193a-132">(Good) T GetComponent\<T>()</span></span> <br/>
> <span data-ttu-id="2193a-133">(不良)コンポーネント GetComponent(string) ></span><span class="sxs-lookup"><span data-stu-id="2193a-133">(Bad) Component GetComponent(string)></span></span> <br/>

#### <a name="avoid-expensive-operations"></a><span data-ttu-id="2193a-134">負荷の高い操作を回避します。</span><span class="sxs-lookup"><span data-stu-id="2193a-134">Avoid expensive operations</span></span>

1) <span data-ttu-id="2193a-135">**使用を防ぐ[LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span><span class="sxs-lookup"><span data-stu-id="2193a-135">**Avoid use of [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span></span>

    <span data-ttu-id="2193a-136">LINQ は、非常にクリーンで読み取りし、書き込みを簡単にできますが、さらに多くの計算と特に多くのメモリ割り当て手動でアルゴリズムを記述するよりもが一般に必要です。</span><span class="sxs-lookup"><span data-stu-id="2193a-136">Although LINQ can be very clean and easy to read and write, it generally requires much more computation and particularly more memory allocation than writing the algorithm out manually.</span></span>

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) <span data-ttu-id="2193a-137">**一般的な Unity Api**</span><span class="sxs-lookup"><span data-stu-id="2193a-137">**Common Unity APIs**</span></span>

    <span data-ttu-id="2193a-138">特定の Unity Api 機能は便利を実行する非常にコストことがあります。</span><span class="sxs-lookup"><span data-stu-id="2193a-138">Certain Unity APIs, although useful, can be very expensive to execute.</span></span> <span data-ttu-id="2193a-139">これらのほとんどは、Gameobject の一致するいくつか一覧については、シーン全体のグラフの検索に関連します。</span><span class="sxs-lookup"><span data-stu-id="2193a-139">Most of these involve searching your entire scene graph for some matching list of GameObjects.</span></span> <span data-ttu-id="2193a-140">これらの操作は、参照をキャッシュまたは実行時に参照を追跡するには、対象の Gameobject の manager コンポーネントの実装によって一般的に回避できます。</span><span class="sxs-lookup"><span data-stu-id="2193a-140">These operations can generally be avoided by caching references or implementing a manager component for the GameObjects in question to track the references at runtime.</span></span>

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> <span data-ttu-id="2193a-141">*[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* と *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* 代価除去する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2193a-141">*[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* and *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* should be eliminated at all costs.</span></span> <span data-ttu-id="2193a-142">これらの関数は、1000 x 関数を直接呼び出すよりも低速の順序指定できます。</span><span class="sxs-lookup"><span data-stu-id="2193a-142">These functions can be on the order of 1000x slower than direct function calls.</span></span>

3) <span data-ttu-id="2193a-143">**ボックス化に注意してください。**</span><span class="sxs-lookup"><span data-stu-id="2193a-143">**Beware of boxing**</span></span>

    <span data-ttu-id="2193a-144">[ボックス化](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing)はのコア概念であり、C#言語とランタイム。</span><span class="sxs-lookup"><span data-stu-id="2193a-144">[Boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) is a core concept of the C# language and runtime.</span></span> <span data-ttu-id="2193a-145">参照型の変数に char、int、bool などの値に型指定された変数の折り返しのプロセスです。</span><span class="sxs-lookup"><span data-stu-id="2193a-145">It is the process of wrapping value-typed variables such as char, int, bool, etc. into reference-typed variables.</span></span> <span data-ttu-id="2193a-146">値に型指定された変数が"boxed"では、マネージ ヒープに格納されている System.Object 内部でラップされます。</span><span class="sxs-lookup"><span data-stu-id="2193a-146">When a value-typed variable is "boxed", it is wrapped inside of a System.Object which is stored on the managed heap.</span></span> <span data-ttu-id="2193a-147">したがって、メモリが割り当てられていると、最終的に破棄されたときに、ガベージ コレクターによって処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2193a-147">Thus, memory is allocated and eventually when disposed must be processed by the garbage collector.</span></span> <span data-ttu-id="2193a-148">これらの割り当てと解放、パフォーマンス コストが発生し、多くのシナリオでは必要ありませんまたは安価な代替手段によって簡単に置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="2193a-148">These allocations and deallocations incur a performance cost and in many scenarios are unnecessary or can be easily replaced by a less expensive alternative.</span></span>

#### <a name="repeating-code-paths"></a><span data-ttu-id="2193a-149">繰り返しのコード パス</span><span class="sxs-lookup"><span data-stu-id="2193a-149">Repeating code paths</span></span>

<span data-ttu-id="2193a-150">繰り返しの Unity コールバック関数 (つまり、</span><span class="sxs-lookup"><span data-stu-id="2193a-150">Any repeating Unity callback functions (i.e</span></span> <span data-ttu-id="2193a-151">更新プログラム) 1 秒あたり何度も実行されている、またはフレームを非常に慎重に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2193a-151">Update) that are executed many times per second and/or frame should be written very carefully.</span></span> <span data-ttu-id="2193a-152">ここで負荷の高い操作には、パフォーマンスに大きく、一貫性のある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2193a-152">Any expensive operations here will have huge and consistent impact on performance.</span></span>

1) <span data-ttu-id="2193a-153">**空のコールバック関数**</span><span class="sxs-lookup"><span data-stu-id="2193a-153">**Empty callback functions**</span></span>

    <span data-ttu-id="2193a-154">次のコードをすべて Unity スクリプト自動初期化を次のコード ブロックで以降は特に、アプリケーションをそのまま無害に見える可能性がありますこれら空のコールバックに非常に不経済実際になります。</span><span class="sxs-lookup"><span data-stu-id="2193a-154">Although the code below may seem innocent to leave in your application, especially since every Unity script auto-initializes with this code block, these empty callbacks can actually become very expensive.</span></span> <span data-ttu-id="2193a-155">Unity は、UnityEngine コードと、アプリケーション コードの間、コードのアンマネージ/マネージの境界を越えた双方向とは動作します。</span><span class="sxs-lookup"><span data-stu-id="2193a-155">Unity operates back and forth over an unmanaged/managed code boundary, between UnityEngine code and your application code.</span></span> <span data-ttu-id="2193a-156">実行するものがない場合でも、コンテキストのこのブリッジ経由での切り替えはかなり安価です。</span><span class="sxs-lookup"><span data-stu-id="2193a-156">Context switching over this bridge is fairly expensive even if there is nothing to execute.</span></span> <span data-ttu-id="2193a-157">これは、アプリがある空の繰り返し Unity コールバックのコンポーネントを持つ Gameobject の何百場合に特に問題になります。</span><span class="sxs-lookup"><span data-stu-id="2193a-157">This becomes especially problematic if your app has 100's of GameObjects with components that have empty repeating Unity callbacks.</span></span>

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> <span data-ttu-id="2193a-158">Update() はこのパフォーマンスの問題の最も一般的な形が、次などの他の繰り返し Unity コールバックは均等に悪くない最悪の場合。FixedUpdate()、LateUpdate()、OnPostRender"、OnPreRender()、OnRenderImage() など。</span><span class="sxs-lookup"><span data-stu-id="2193a-158">Update() is the most common manifestation of this performance issue but other repeating Unity callbacks such as the following can be equally as bad if not worse: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc.</span></span> 

2) <span data-ttu-id="2193a-159">**操作 1 回実行しているどちらを優先するフレームごと**</span><span class="sxs-lookup"><span data-stu-id="2193a-159">**Operations to favor running once per frame**</span></span>

    <span data-ttu-id="2193a-160">次の Unity Api は、Holographic アプリの多くの一般的な操作です。</span><span class="sxs-lookup"><span data-stu-id="2193a-160">The following Unity APIs are common operations for many Holographic Apps.</span></span> <span data-ttu-id="2193a-161">常に可能ではない、ですが、これらの関数から結果を 1 回計算する非常によくし、結果は、特定のフレームのアプリケーション全体にわたって再利用します。</span><span class="sxs-lookup"><span data-stu-id="2193a-161">Although not always possible, the results from these functions can very commonly be computed once and the results re-utilized across the application for a given frame.</span></span>

    <span data-ttu-id="2193a-162">専用シングルトン クラスまたはサービスを視線入力 Raycast をシーンに処理し、その他のシーン、すべてのコンポーネントごとに繰り返されると、実質的に同じ Raycast 操作を行う代わりにこの結果を再利用することをお勧めは通常、a)コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="2193a-162">a) Generally it is good practice to have a dedicated Singleton class or service to handle your gaze Raycast into the scene and then re-use this result in all other scene components, instead of making repeated and essentially identical Raycast operations by each component.</span></span> <span data-ttu-id="2193a-163">もちろん、一部のアプリケーションが raycasts またはに対して異なるさまざまな配信元からを必要があります[LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html)します。</span><span class="sxs-lookup"><span data-stu-id="2193a-163">Of course, some applications may require raycasts from different origins or against different [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html).</span></span>

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    <span data-ttu-id="2193a-164">b) で Update() のような繰り返しの Unity コールバックで GetComponent() 操作を回避する[の参照をキャッシュ](#cache-references)Start() または Awake()</span><span class="sxs-lookup"><span data-stu-id="2193a-164">b) Avoid GetComponent() operations in repeated Unity callbacks like Update() by [caching references](#cache-references) in Start() or Awake()</span></span>

        UnityEngine.Object.GetComponent()

    <span data-ttu-id="2193a-165">c) は初期化で使用可能であれば、すべてのオブジェクトをインスタンス化することをお勧め[オブジェクト プーリング](#object-pooling)リサイクルし、アプリケーションのランタイム全体にわたって Gameobject を再利用するには</span><span class="sxs-lookup"><span data-stu-id="2193a-165">c) It is good practice to instantiate all objects, if possible, at initialization and use [object pooling](#object-pooling) to recycle and re-use GameObjects throughout runtime of your application</span></span>

        UnityEngine.Object.Instantiate()

3) <span data-ttu-id="2193a-166">**インターフェイスと仮想の構成要素を回避します。**</span><span class="sxs-lookup"><span data-stu-id="2193a-166">**Avoid interfaces and virtual constructs**</span></span>

    <span data-ttu-id="2193a-167">Vs ダイレクト オブジェクトのインターフェイスを通じて関数呼び出しを起動または仮想関数を呼び出すことがよくありますできます直接コンストラクトまたは関数の直接呼び出しを使用するよりもはるかに高くなります。</span><span class="sxs-lookup"><span data-stu-id="2193a-167">Invoking function calls through interfaces vs direct objects or calling virtual functions can often times be much more expensive than utilizing direct constructs or direct function calls.</span></span> <span data-ttu-id="2193a-168">仮想関数またはインターフェイスが必要な場合は、削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2193a-168">If the virtual function or interface is unnecessary, then it should be removed.</span></span> <span data-ttu-id="2193a-169">ただし、パフォーマンスへのこれらの方法に影響は、通常のトレードオフの価値が開発のコラボレーション、コードの読みやすさ、およびコードの保守性を簡略化に利用する場合。</span><span class="sxs-lookup"><span data-stu-id="2193a-169">However, the performance hit for these approaches are generally worth the trade-off if utilizing them simplifies development collaboration, code readability, and code maintainability.</span></span> 

4) <span data-ttu-id="2193a-170">**値構造体の受け渡しを避ける**</span><span class="sxs-lookup"><span data-stu-id="2193a-170">**Avoid passing structs by value**</span></span>

    <span data-ttu-id="2193a-171">クラスと異なり、構造体は、値型と関数に直接渡されると、新しく作成されたインスタンスにその内容がコピーされます。</span><span class="sxs-lookup"><span data-stu-id="2193a-171">Unlike classes, structs are value-types and when passed directly to a function, their contents are copied into a newly created instance.</span></span> <span data-ttu-id="2193a-172">このコピーは、コスト、スタックに追加のメモリと CPU を追加します。</span><span class="sxs-lookup"><span data-stu-id="2193a-172">This copy adds CPU cost as well as additional memory on the stack.</span></span> <span data-ttu-id="2193a-173">小さな構造体は、効果は、通常は最小限にし、許容されるためです。</span><span class="sxs-lookup"><span data-stu-id="2193a-173">For small structs, the effect is usually very minimal and thus acceptable.</span></span> <span data-ttu-id="2193a-174">ただし、関数は、すべてのフレームを繰り返し呼び出すのと同様に大規模な構造体を取得する関数は可能であれば、参照渡しの関数定義を変更します。</span><span class="sxs-lookup"><span data-stu-id="2193a-174">However, for functions repeatedly invoked every frame as well as functions taking large structs, if possible modify the function definition to pass by reference.</span></span> [<span data-ttu-id="2193a-175">詳細はこちら</span><span class="sxs-lookup"><span data-stu-id="2193a-175">Learn more here</span></span>](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a><span data-ttu-id="2193a-176">その他</span><span class="sxs-lookup"><span data-stu-id="2193a-176">Miscellaneous</span></span>

1) <span data-ttu-id="2193a-177">**物理学**</span><span class="sxs-lookup"><span data-stu-id="2193a-177">**Physics**</span></span>

    <span data-ttu-id="2193a-178">a) 一般的には、物理運動を向上させるために簡単では、物理運動または 1 秒あたりのイテレーションの数に費やされた時間の量を制限します。</span><span class="sxs-lookup"><span data-stu-id="2193a-178">a) Generally, easiest way to improve physics is to limit the amount of time spent on Physics or the number of iterations per second.</span></span> <span data-ttu-id="2193a-179">もちろん、これにより、シミュレーションの正確性が減少します。</span><span class="sxs-lookup"><span data-stu-id="2193a-179">Of course, this will reduce simulation accuracy.</span></span> <span data-ttu-id="2193a-180">参照してください[TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) Unity で</span><span class="sxs-lookup"><span data-stu-id="2193a-180">See [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) in Unity</span></span>

    <span data-ttu-id="2193a-181">b) Unity でコライダーの種類では、大きく異なるパフォーマンス特性があります。</span><span class="sxs-lookup"><span data-stu-id="2193a-181">b) The type of colliders in Unity have widely different performance characteristics.</span></span> <span data-ttu-id="2193a-182">以下の順番は、最低のパフォーマンスの高いコライダーを左から右へのほとんどのパフォーマンスの高いコライダーを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="2193a-182">The order below lists the most performant colliders to least performant colliders from left to right.</span></span> <span data-ttu-id="2193a-183">プリミティブのコライダーよりも大幅に高価であるメッシュ コライダーを回避するために最も重要です。</span><span class="sxs-lookup"><span data-stu-id="2193a-183">It is most important to avoid Mesh Colliders which are substantially more expensive than the primitive colliders.</span></span>

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    <span data-ttu-id="2193a-184">参照してください[Unity 物理学のベスト プラクティス](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)の詳細</span><span class="sxs-lookup"><span data-stu-id="2193a-184">See [Unity Physics Best Practices](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) for more info</span></span>

2) <span data-ttu-id="2193a-185">**アニメーション**</span><span class="sxs-lookup"><span data-stu-id="2193a-185">**Animations**</span></span>

    <span data-ttu-id="2193a-186">Animator コンポーネントを無効にしてアイドル状態のアニメーションを無効にする (ゲーム オブジェクトを無効にすると同じ効果が)。</span><span class="sxs-lookup"><span data-stu-id="2193a-186">Disable idle animations by disabling the Animator component (disabling the game object won't have the same effect).</span></span> <span data-ttu-id="2193a-187">アニメーターが同じものを値を設定、ループ内に存在する設計パターンを回避します。</span><span class="sxs-lookup"><span data-stu-id="2193a-187">Avoid design patterns where an animator sits in a loop setting a value to the same thing.</span></span> <span data-ttu-id="2193a-188">この手法でアプリケーションに影響をかなりのオーバーヘッドがあります。</span><span class="sxs-lookup"><span data-stu-id="2193a-188">There is considerable overhead for this technique, with no effect on the application.</span></span> [<span data-ttu-id="2193a-189">詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="2193a-189">Learn more here.</span></span>](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) <span data-ttu-id="2193a-190">**複雑なアルゴリズム**</span><span class="sxs-lookup"><span data-stu-id="2193a-190">**Complex algorithms**</span></span>

    <span data-ttu-id="2193a-191">簡単な方法を見つけたり、パフォーマンスに関連する設定を調整する場合は、アプリケーションは、複雑なアルゴリズム (インバース キネマティクス、パスの検索など) を使用して、なります</span><span class="sxs-lookup"><span data-stu-id="2193a-191">If your application is using complex algorithms such as inverse kinematics, path finding, etc, look to find a simpler approach or adjust relevant settings for their performance</span></span>

## <a name="cpu-to-gpu-performance-recommendations"></a><span data-ttu-id="2193a-192">CPU、GPU にパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="2193a-192">CPU-to-GPU performance recommendations</span></span>

<span data-ttu-id="2193a-193">一般に、CPU、GPU にパフォーマンスが得られる下に、**描画呼び出し**グラフィックス カードに送信します。</span><span class="sxs-lookup"><span data-stu-id="2193a-193">Generally, CPU-to-GPU performance comes down to the **draw calls** submitted to the graphics card.</span></span> <span data-ttu-id="2193a-194">描画呼び出しをパフォーマンスを向上させるのには、戦略的にする必要がある **) 削減**または**b) 再編成**最善の結果。</span><span class="sxs-lookup"><span data-stu-id="2193a-194">To improve performance, draw calls need to be strategically **a) reduced** or **b) restructured** for optimal results.</span></span> <span data-ttu-id="2193a-195">描画呼び出し自体は、リソース集中型であるためそれらを減らすために必要な作業は全体を削減できます。</span><span class="sxs-lookup"><span data-stu-id="2193a-195">Since draw calls themselves are resource-intensive, reducing them will reduce overall work required.</span></span> <span data-ttu-id="2193a-196">描画呼び出し間の変更はコストのかかる検証を必要とし、グラフィックス ドライバーの変換のステップをさらに、状態にあり、したがって、制限の状態の変更 (つまり、アプリケーションの描画呼び出しの再構築</span><span class="sxs-lookup"><span data-stu-id="2193a-196">Further, state changes between draw calls requires costly validation and translation steps in the graphics driver and thus, restructuring of your application's draw calls to limit state changes(i.e</span></span> <span data-ttu-id="2193a-197">さまざまな資料など) は、パフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="2193a-197">different materials, etc) can boost performance.</span></span>

<span data-ttu-id="2193a-198">Unity では、概要を説明し、そのプラットフォームの描画呼び出しをバッチ処理に踏み込みます優れた記事には。</span><span class="sxs-lookup"><span data-stu-id="2193a-198">Unity has a great article that gives an overview and dives into batching draw calls for their platform.</span></span>
- [<span data-ttu-id="2193a-199">Unity の描画呼び出しがバッチ処理</span><span class="sxs-lookup"><span data-stu-id="2193a-199">Unity Draw Call Batching</span></span>](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a><span data-ttu-id="2193a-200">1 回インスタンス化されたレンダリング</span><span class="sxs-lookup"><span data-stu-id="2193a-200">Single pass instanced rendering</span></span>

<span data-ttu-id="2193a-201">Unity での単一パス Instanced レンダリングで描画呼び出しをインスタンス化された 1 つの描画呼び出しに短縮する目ごとにできます。</span><span class="sxs-lookup"><span data-stu-id="2193a-201">Single Pass Instanced Rendering in Unity allows for draw calls for each eye to be reduced down to one instanced draw call.</span></span> <span data-ttu-id="2193a-202">2 つの描画呼び出し間のキャッシュの一貫性のためのパフォーマンスの向上も GPU 上でもあります。</span><span class="sxs-lookup"><span data-stu-id="2193a-202">Due to cache coherency between two draw calls, there is also some performance improvement on the GPU as well.</span></span>

<span data-ttu-id="2193a-203">Unity プロジェクトでこの機能を有効にするには</span><span class="sxs-lookup"><span data-stu-id="2193a-203">To enable this feature in your Unity Project</span></span>
1)  <span data-ttu-id="2193a-204">開いている**Player XR 設定**(に移動**編集** > **プロジェクト設定** > **Player**  > **XR 設定**)</span><span class="sxs-lookup"><span data-stu-id="2193a-204">Open **Player XR Settings** (go to **Edit** > **Project Settings** > **Player** > **XR Settings**)</span></span>
2) <span data-ttu-id="2193a-205">選択**1 つ渡すインスタンス化**から、**ステレオのレンダリング方法**ドロップダウン メニュー (**仮想現実サポート**チェック ボックスを選択する必要があります)</span><span class="sxs-lookup"><span data-stu-id="2193a-205">Select **Single Pass Instanced** from the **Stereo Rendering Method** drop-down menu (**Virtual Reality Supported** checkbox must be checked)</span></span>

<span data-ttu-id="2193a-206">詳細についてはこのレンダリング アプローチで、Unity から、次の記事を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="2193a-206">Read the following articles from Unity for details with this rendering approach.</span></span>
- [<span data-ttu-id="2193a-207">AR および VR の高度なステレオ レンダリング パフォーマンスを最大化する方法</span><span class="sxs-lookup"><span data-stu-id="2193a-207">How to maximize AR and VR performance with advanced stereo rendering</span></span>](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [<span data-ttu-id="2193a-208">1 つのパスがインスタンス化</span><span class="sxs-lookup"><span data-stu-id="2193a-208">Single Pass Instancing</span></span>](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> <span data-ttu-id="2193a-209">1 つ渡すレンダリングをインスタンス化で 1 つの一般的な問題は、開発者が既に既存のカスタム シェーダーに書かれていない場合に発生します。 インスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="2193a-209">One common issue with Single Pass Instanced Rendering occurs if developers already have existing custom shaders not written for instancing.</span></span> <span data-ttu-id="2193a-210">この機能を有効にした後は、開発者は 1 つ目のいくつかの Gameobject のみレンダリングをことがあります。</span><span class="sxs-lookup"><span data-stu-id="2193a-210">After enabling this feature, developers may notice some GameObjects only render in one eye.</span></span> <span data-ttu-id="2193a-211">これは、関連付けられているカスタムのシェーダーの適切なプロパティがあるないためにインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="2193a-211">This is because the associated custom shaders do not have the appropriate properties for instancing.</span></span>
>
> <span data-ttu-id="2193a-212">参照してください[1 つ渡すステレオのレンダリング HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)から Unity のこの問題に対処する方法</span><span class="sxs-lookup"><span data-stu-id="2193a-212">See [Single Pass Stereo Rendering for HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) from Unity for how to address this problem</span></span>

#### <a name="static-batching"></a><span data-ttu-id="2193a-213">静的なバッチ処理</span><span class="sxs-lookup"><span data-stu-id="2193a-213">Static batching</span></span>

<span data-ttu-id="2193a-214">Unity は、GPU の描画呼び出しを減らすために多くの静的オブジェクトをバッチ処理することです。</span><span class="sxs-lookup"><span data-stu-id="2193a-214">Unity is able to batch many static objects to reduce draw calls to the GPU.</span></span> <span data-ttu-id="2193a-215">静的なバッチ処理のほとんどの動作[レンダラー](https://docs.unity3d.com/ScriptReference/Renderer.html) Unity 内のオブジェクトを**1) 同じ素材を共有する**と**は 2) としてマークされているすべて\*静的**\* (Unity でオブジェクトを選択し、上にあるチェック ボックスをオン、インスペクターの右)。</span><span class="sxs-lookup"><span data-stu-id="2193a-215">Static Batching works for most [Renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) objects in Unity that **1) share the same material** and **2) are all marked as *Static*** (Select an object in Unity and click the checkbox in the top right of the inspector).</span></span> <span data-ttu-id="2193a-216">としてマークされている GameObjects*静的*アプリケーションのランタイム全体で移動することはできません。</span><span class="sxs-lookup"><span data-stu-id="2193a-216">GameObjects marked as *Static* cannot be moved throughout your application's runtime.</span></span> <span data-ttu-id="2193a-217">したがって、静的なバッチ処理はほとんどすべてのオブジェクトが移動された、スケーリングなど、配置する必要がある HoloLens の活用の困難さできます。イマーシブ ヘッドセットの静的バッチ処理できます描画呼び出しを大幅に削減し、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="2193a-217">Thus, static batching can be difficult to leverage on HoloLens where virtually every object needs to be placed, moved, scaled, etc. For immersive headsets, static batching can dramatically reduce draw calls and thus improve performance.</span></span>

<span data-ttu-id="2193a-218">読み取り*静的バッチ処理* [Unity でバッチ処理を呼び出す描画](https://docs.unity3d.com/Manual/DrawCallBatching.html)の詳細。</span><span class="sxs-lookup"><span data-stu-id="2193a-218">Read *Static Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for more details.</span></span>

#### <a name="dynamic-batching"></a><span data-ttu-id="2193a-219">動的なバッチ処理</span><span class="sxs-lookup"><span data-stu-id="2193a-219">Dynamic batching</span></span>

<span data-ttu-id="2193a-220">オブジェクトとしてマークする問題であるため*静的*HoloLens の開発、動的なバッチ処理できるでこれを補正する優れたツール機能が不足しています。</span><span class="sxs-lookup"><span data-stu-id="2193a-220">Since it is problematic to mark objects as *Static* for HoloLens development, dynamic batching can be a great tool to compensate for this lacking feature.</span></span> <span data-ttu-id="2193a-221">もちろん、イマーシブ ヘッドセットもで役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="2193a-221">Of course, it is can also be useful on immersive headsets as well.</span></span> <span data-ttu-id="2193a-222">Unity でバッチ処理を動的なは難しいが Gameobject にする必要がありますので、有効にする **) 共有は同じ素材**と**b) 多数の他の条件を満たす**します。</span><span class="sxs-lookup"><span data-stu-id="2193a-222">Dynamic batching in Unity can be difficult though to enable because GameObjects must **a) share the same Material** and **b) meet a long list of other criteria**.</span></span>

<span data-ttu-id="2193a-223">読み取り*動的バッチ処理* [Unity でバッチ処理を呼び出す描画](https://docs.unity3d.com/Manual/DrawCallBatching.html)完全な一覧についてはします。</span><span class="sxs-lookup"><span data-stu-id="2193a-223">Read *Dynamic Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for the full list.</span></span> <span data-ttu-id="2193a-224">ほとんどの場合、GameObjects は、バッチ処理する動的に関連付けられているメッシュ データとして使用できるは、300 個の頂点ので無効になります。</span><span class="sxs-lookup"><span data-stu-id="2193a-224">Most commonly, GameObjects become invalid to be batched dynamically because the associated mesh data can be no more than 300 vertices.</span></span>

#### <a name="other-techniques"></a><span data-ttu-id="2193a-225">その他の手法</span><span class="sxs-lookup"><span data-stu-id="2193a-225">Other techniques</span></span>

<span data-ttu-id="2193a-226">バッチ処理と複数 GameObjects は同じ素材を共有することがある場合のみ実行できます。</span><span class="sxs-lookup"><span data-stu-id="2193a-226">Batching can only occur if multiple GameObjects are able to share the same material.</span></span> <span data-ttu-id="2193a-227">通常、それぞれの素材に対する一意のテクスチャを持つ Gameobject のですが、ブロックされます。</span><span class="sxs-lookup"><span data-stu-id="2193a-227">Typically this will be blocked by the need for GameObjects to have a unique texture for their respective Material.</span></span> <span data-ttu-id="2193a-228">1 つの大きなテクスチャと呼ばれるメソッドにテクスチャを結合するが一般的[テクスチャ Atlasing](https://en.wikipedia.org/wiki/Texture_atlas)します。</span><span class="sxs-lookup"><span data-stu-id="2193a-228">It is common to combine Textures into one big Texture, a method known as [Texture Atlasing](https://en.wikipedia.org/wiki/Texture_atlas).</span></span>

<span data-ttu-id="2193a-229">さらに、可能であり、適切な場所に 1 つの GameObject にメッシュを結合することをお勧めです。</span><span class="sxs-lookup"><span data-stu-id="2193a-229">Further, it is generally preferable to combine meshes into one GameObject where possible and reasonable.</span></span> <span data-ttu-id="2193a-230">Unity では、各レンダラーが、描画呼び出しの 1 つのレンダラーで結合されたメッシュの送信とが関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="2193a-230">Each Renderer in Unity will have it's associated draw call(s) versus submitting a combined mesh under one Renderer.</span></span> 

>[!NOTE]
> <span data-ttu-id="2193a-231">Renderer.material の実行時のプロパティの変更とをマテリアルのコピーを作成し、したがってできなくなる可能性のバッチ処理します。</span><span class="sxs-lookup"><span data-stu-id="2193a-231">Modifying properties of Renderer.material at runtime will create a copy of the Material and thus potentially break batching.</span></span> <span data-ttu-id="2193a-232">Renderer.sharedMaterial を使用すると、Gameobject の間で共有の素材プロパティを変更できます。</span><span class="sxs-lookup"><span data-stu-id="2193a-232">Use Renderer.sharedMaterial to modify shared material properties across GameObjects.</span></span>

## <a name="gpu-performance-recommendations"></a><span data-ttu-id="2193a-233">GPU のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="2193a-233">GPU performance recommendations</span></span>

<span data-ttu-id="2193a-234">詳細については[Unity でのグラフィックス レンダリングの最適化](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)</span><span class="sxs-lookup"><span data-stu-id="2193a-234">Learn more about [optimizing graphics rendering in Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)</span></span> 

### <a name="optimize-depth-buffer-sharing"></a><span data-ttu-id="2193a-235">深度バッファーの共有を最適化します。</span><span class="sxs-lookup"><span data-stu-id="2193a-235">Optimize depth buffer sharing</span></span>

<span data-ttu-id="2193a-236">有効にすることをお勧め**深度バッファーの共有** **Player XR 設定**を最適化する[ホログラム安定性](Hologram-stability.md)します。</span><span class="sxs-lookup"><span data-stu-id="2193a-236">It is generally recommended to enable **Depth buffer sharing** under **Player XR Settings** to optimize for [hologram stability](Hologram-stability.md).</span></span> <span data-ttu-id="2193a-237">ただし、この設定で最終段階の深さに基づく reprojection を有効にする場合は、選択勧め**形式の 16 ビット深度**の代わりに**24 ビット深度形式**します。</span><span class="sxs-lookup"><span data-stu-id="2193a-237">When enabling depth-based late-stage reprojection with this setting however, it is recommended to select **16-bit depth format** instead of **24-bit depth format**.</span></span> <span data-ttu-id="2193a-238">帯域幅が大幅に減少 (および電源したがって)、16 ビットの深度バッファーは深度バッファーのトラフィックに関連します。</span><span class="sxs-lookup"><span data-stu-id="2193a-238">The 16-bit depth buffers will drastically reduces the bandwidth (and thus power) associated with depth buffer traffic.</span></span> <span data-ttu-id="2193a-239">ビッグ power win、入力できますが、経験と小規模の深さの範囲に対してのみ適用、 [z ファイティング](https://en.wikipedia.org/wiki/Z-fighting)は 16 ビットより 24 ビットで発生する可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="2193a-239">This can be a big power win, but is only applicable for experiences with a small depth range as [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) is more likely to occur with 16-bit than 24-bit.</span></span> <span data-ttu-id="2193a-240">これらの成果物を避けるためには、変更のほぼ/遠ク リップ面、 [Unity カメラ](https://docs.unity3d.com/Manual/class-Camera.html)精度が低いに対応します。</span><span class="sxs-lookup"><span data-stu-id="2193a-240">To avoid these artifacts, modify the near/far clip planes of the [Unity camera](https://docs.unity3d.com/Manual/class-Camera.html) to account for the lower precision.</span></span> <span data-ttu-id="2193a-241">HoloLens ベースのアプリケーションでは、z ファイティング通常 1000 m Unity の既定ではなく 50 m の遠ク リップ面から排除できます。</span><span class="sxs-lookup"><span data-stu-id="2193a-241">For HoloLens-based applications, a far clip plane of 50m instead of the Unity default 1000m can generally eliminate any z-fighting.</span></span>

### <a name="reduce-poly-count"></a><span data-ttu-id="2193a-242">ポリゴンの数を削減します。</span><span class="sxs-lookup"><span data-stu-id="2193a-242">Reduce poly count</span></span>

<span data-ttu-id="2193a-243">いずれかで多角形の数が減少通常</span><span class="sxs-lookup"><span data-stu-id="2193a-243">Polygon count is usually reduced by either</span></span>
1) <span data-ttu-id="2193a-244">シーンからオブジェクトを削除します。</span><span class="sxs-lookup"><span data-stu-id="2193a-244">Removing objects from a scene</span></span>
2) <span data-ttu-id="2193a-245">指定したメッシュの多角形の数が減少する資産デシメーション</span><span class="sxs-lookup"><span data-stu-id="2193a-245">Asset decimation which reduces the number of polygons for a given mesh</span></span>
3) <span data-ttu-id="2193a-246">実装する、[詳細レベル (LOD) のシステム](https://docs.unity3d.com/Manual/LevelOfDetail.html)を離れた同じジオメトリの多角形の下のバージョンを持つオブジェクトを描画するアプリケーションに</span><span class="sxs-lookup"><span data-stu-id="2193a-246">Implementing a [Level of Detail (LOD) System](https://docs.unity3d.com/Manual/LevelOfDetail.html) into your application which renders far away objects with lower-polygon version of the same geometry</span></span>

### <a name="understanding-shaders-in-unity"></a><span data-ttu-id="2193a-247">Unity でシェーダーを理解します。</span><span class="sxs-lookup"><span data-stu-id="2193a-247">Understanding shaders in Unity</span></span>

<span data-ttu-id="2193a-248">パフォーマンスでシェーダーを比較する簡単な近似は、各操作の平均数を識別するために実行時に実行します。</span><span class="sxs-lookup"><span data-stu-id="2193a-248">An easy approximation to compare shaders in performance is to identify the average number of operations each executes at runtime.</span></span> <span data-ttu-id="2193a-249">これは、Unity で簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="2193a-249">This can be done easily in Unity.</span></span>

1) <span data-ttu-id="2193a-250">シェーダー資産を選択または素材を選択し、続いてインスペクター ウィンドウの上部右隅にある、歯車アイコンを選択し、 **「シェーダーの選択」**</span><span class="sxs-lookup"><span data-stu-id="2193a-250">Select your shader asset or select a material, then in top right corner of the inspector window, select the gear icon and then **"Select Shader"**</span></span>

    ![Unity でシェーダーを選択します。](images/Select-shader-unity.png)
2) <span data-ttu-id="2193a-252">選択したシェーダー アセット、クリックして、 **「コンパイルし、コードの表示」** インスペクター ウィンドウの下のボタン</span><span class="sxs-lookup"><span data-stu-id="2193a-252">With the shader asset selected, click the **"Compile and show code"** button under the inspector window</span></span>

    ![Unity でシェーダー コードをコンパイルします。](images/compile-shader-code-unity.PNG)

3) <span data-ttu-id="2193a-254">コンパイルの後、結果に統計情報 セクションを検索、頂点とピクセル シェーダーのさまざまな操作の数 (注: ピクセル シェーダーでは、フラグメント シェーダーも多くの場合と呼ばれます)</span><span class="sxs-lookup"><span data-stu-id="2193a-254">After compiling, look for the statistics section in the results with the number of different operations for both the vertex and pixel shader (Note: pixel shaders are often also called fragment shaders)</span></span>

    ![Unity シェーダーの標準的な操作](images/unity-standard-shader-compilation.png)

#### <a name="optmize-pixel-shaders"></a><span data-ttu-id="2193a-256">ピクセル シェーダーの最適化</span><span class="sxs-lookup"><span data-stu-id="2193a-256">Optmize pixel shaders</span></span>

<span data-ttu-id="2193a-257">上記のメソッドを使用してコンパイルされた統計結果を見て、[フラグメント シェーダー](https://en.wikipedia.org/wiki/Shader#Pixel_shaders)よりもより多くの操作は通常、実行、[頂点シェーダー](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)平均。</span><span class="sxs-lookup"><span data-stu-id="2193a-257">Looking at the compiled statistic results using the method above, the [fragment shader](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) will generally execute more operations than the [vertex shader](https://en.wikipedia.org/wiki/Shader#Vertex_shaders) on average.</span></span> <span data-ttu-id="2193a-258">頂点シェーダーがのみ実行される、頂点ごとの画面に描画されているすべてのメッシュの間、出力画面上のピクセルあたりフラグメント シェーダー、ピクセル シェーダーとも呼ばれますが実行されます。</span><span class="sxs-lookup"><span data-stu-id="2193a-258">The fragment shader, also known as the pixel shader, is executed per pixel on the screen output while the vertex shader is only executed per-vertex of all meshes being drawn to the screen.</span></span> 

<span data-ttu-id="2193a-259">したがって、だけでなく、フラグメント シェーダーは頂点シェーダーよりも詳細な手順について、すべてのライティング計算のため、フラグメント シェーダーは、大規模なデータセットでほぼ常に実行します。</span><span class="sxs-lookup"><span data-stu-id="2193a-259">Thus, not only do fragment shaders have more instructions than vertex shaders because of all the lighting calculations, fragment shaders are almost always executed on a larger dataset.</span></span> <span data-ttu-id="2193a-260">たとえば、画面出力が 2 k 画像によって 2 k の場合は、フラグメント シェーダーを取得できます 2, 000 \* 2, 000 = 大きく 4,000,000 の実行時間。</span><span class="sxs-lookup"><span data-stu-id="2193a-260">For example, if the screen output is a 2k by 2k image, then the fragment shader can get executed 2,000\*2,000 = 4,000,000 times.</span></span> <span data-ttu-id="2193a-261">2 つ目を表示するには、2 つの画面があるので、この数が 2 倍します。</span><span class="sxs-lookup"><span data-stu-id="2193a-261">If rendering two eyes, this number doubles since there are two screens.</span></span> <span data-ttu-id="2193a-262">複合現実のアプリケーションに複数のパス、全画面表示処理後の効果、または同一のピクセルに複数のメッシュをレンダリングがある場合は、この数が大幅に増加します。</span><span class="sxs-lookup"><span data-stu-id="2193a-262">If a mixed reality application has multiple passes, full-screen post-processing effects, or rendering multiple meshes to the same pixel, this number will increase dramatically.</span></span> 

<span data-ttu-id="2193a-263">そのため、フラグメント シェーダーの操作の数を減らすこと与えることが一般にはるかに大きなパフォーマンスの向上、頂点シェーダーでの最適化を。</span><span class="sxs-lookup"><span data-stu-id="2193a-263">Therefore, reducing the number of operations in the fragment shader can generally give far greater performance gains over optimizations in the vertex shader.</span></span>

#### <a name="unity-standard-shader-alternatives"></a><span data-ttu-id="2193a-264">Unity シェーダーの標準的な代替手段</span><span class="sxs-lookup"><span data-stu-id="2193a-264">Unity Standard shader alternatives</span></span>

<span data-ttu-id="2193a-265">効率的に利用して物理的にベースのレンダリング (PBR) やその他の高品質なシェーダーを使用せずに確認し、安価なシェーダー。</span><span class="sxs-lookup"><span data-stu-id="2193a-265">Instead of using a physically based rendering (PBR) or other high-quality shader, look at utilizing a more performant and cheaper shader.</span></span> <span data-ttu-id="2193a-266">[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供、 [MRTK 標準シェーダー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)複合現実プロジェクト向けに最適化されたをします。</span><span class="sxs-lookup"><span data-stu-id="2193a-266">The [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides the [MRTK standard shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) that has been optimized for mixed reality projects.</span></span>

<span data-ttu-id="2193a-267">Unity では、光源、なし、頂点が点灯している、高速比較が大幅に簡略化されたシェーダーの拡散、およびその他のオプションも、標準の Unity シェーダーに提供します。</span><span class="sxs-lookup"><span data-stu-id="2193a-267">Unity also provides an unlit, vertex lit, diffuse, and other simplified shader options that are significantly faster compared to the Unity Standard shader.</span></span> <span data-ttu-id="2193a-268">参照してください[使用状況と組み込みのシェーダーのパフォーマンスを](https://docs.unity3d.com/Manual/shader-Performance.html)詳細な情報。</span><span class="sxs-lookup"><span data-stu-id="2193a-268">See [Usage and Performance of Built-in Shaders](https://docs.unity3d.com/Manual/shader-Performance.html) for more detailed information.</span></span>

#### <a name="shader-preloading"></a><span data-ttu-id="2193a-269">シェーダーの事前読み込み</span><span class="sxs-lookup"><span data-stu-id="2193a-269">Shader preloading</span></span>

<span data-ttu-id="2193a-270">使用*シェーダー プリロード*とその他のテクニックを最適化する[シェーダーの読み込み時間](http://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html)します。</span><span class="sxs-lookup"><span data-stu-id="2193a-270">Use *Shader preloading* and other tricks to optimize [shader load time](http://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html).</span></span> <span data-ttu-id="2193a-271">具体的には、シェーダーの事前読み込みはランタイム シェーダーのコンパイルのためのすべての問題は表示されませんを意味します。</span><span class="sxs-lookup"><span data-stu-id="2193a-271">In particular, shader preloading means you won't see any hitches due to runtime shader compilation.</span></span>

### <a name="limit-overdraw"></a><span data-ttu-id="2193a-272">制限を範囲します。</span><span class="sxs-lookup"><span data-stu-id="2193a-272">Limit overdraw</span></span>

<span data-ttu-id="2193a-273">Unity では、1 つを表示できますを切り替えることにより、そのシーンを描画できます、 [**モード メニューを描画**](https://docs.unity3d.com/Manual/ViewModes.html)の左上隅にある、**シーン ビュー**選択**アルファブレンディング**.</span><span class="sxs-lookup"><span data-stu-id="2193a-273">In Unity, one can display overdraw for their scene, by toggling the [**draw mode menu**](https://docs.unity3d.com/Manual/ViewModes.html) in the top left corner of the **Scene view** and selecting **Overdraw**.</span></span>

<span data-ttu-id="2193a-274">一般に、範囲を事前に、GPU に送信される前にオブジェクトをカリング軽減できます。</span><span class="sxs-lookup"><span data-stu-id="2193a-274">Generally, overdraw can be mitigated by culling objects ahead of time before they are sent to the GPU.</span></span> <span data-ttu-id="2193a-275">Unity を実装する方法の詳細を提供する[オクルー ジョン カリング](https://docs.unity3d.com/Manual/OcclusionCulling.html)のエンジン。</span><span class="sxs-lookup"><span data-stu-id="2193a-275">Unity provides details on implementing [Occlusion Culling](https://docs.unity3d.com/Manual/OcclusionCulling.html) for their engine.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="2193a-276">メモリの推奨事項</span><span class="sxs-lookup"><span data-stu-id="2193a-276">Memory recommendations</span></span>

<span data-ttu-id="2193a-277">過剰なメモリの割り当てと割り当て解除の操作、holographic アプリケーションを一貫性のないパフォーマンス、固定されたフレーム、およびその他の好ましくない動作に影響を受けることができます。</span><span class="sxs-lookup"><span data-stu-id="2193a-277">Excessive memory allocation & deallocation operations can have adverse effects on your holographic application resulting in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="2193a-278">これは、方法は、メモリ管理は、ガベージ コレクターによって制御されるため、Unity で開発するときは、メモリに関する考慮事項を理解するのには特に重要です。</span><span class="sxs-lookup"><span data-stu-id="2193a-278">It is especially important to understand memory considerations when developing in Unity since memory management is controlled by the garbage collector.</span></span>

#### <a name="garbage-collection"></a><span data-ttu-id="2193a-279">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="2193a-279">Garbage collection</span></span>

<span data-ttu-id="2193a-280">Holographic アプリ、不要になったスコープの実行中にオブジェクトを分析する、GC がアクティブになるし、メモリにできる再利用できるようにリリースする必要があるガベージ コレクター (GC) の処理コンピューティング時間が失われます。</span><span class="sxs-lookup"><span data-stu-id="2193a-280">Holographic apps will loose processing compute time to the garbage collector (GC) when the GC is activated to analyze objects that are no longer in scope during execution and their memory needs to be released so it can be made available for re-use.</span></span> <span data-ttu-id="2193a-281">定数の割り当てと割り当て解除したがって傷つけるパフォーマンスとユーザー エクスペリエンスをより頻繁に実行するガベージ コレクターが一般に必要です。</span><span class="sxs-lookup"><span data-stu-id="2193a-281">Constant allocations and de-allocations will generally require the garbage collector to run more frequently thus hurting performance and user experience.</span></span>

<span data-ttu-id="2193a-282">Unity は、ガベージ コレクターのしくみを詳しく説明する優れたページとメモリ管理においてより効率的なコードを記述するためのヒントを提供しています。</span><span class="sxs-lookup"><span data-stu-id="2193a-282">Unity has provided an excellent page that explains in detail how the garbage collector works and tips to write more efficient code in regards to memory management.</span></span>
- [<span data-ttu-id="2193a-283">Unity ゲームでのガベージ コレクションの最適化</span><span class="sxs-lookup"><span data-stu-id="2193a-283">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

<span data-ttu-id="2193a-284">過度なガベージ コレクションにつながる最も一般的なプラクティスの 1 つがコンポーネントおよび Unity 開発におけるクラスへの参照をキャッシュできません。</span><span class="sxs-lookup"><span data-stu-id="2193a-284">One of the most common practices that leads to excessive garbage collection is not caching references to components and classes in Unity development.</span></span> <span data-ttu-id="2193a-285">すべての参照は Start() または Awake() 中にキャプチャし、Update() LateUpdate() などの以降の関数で再利用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2193a-285">Any references should be captured during Start() or Awake() and re-used in later functions such as Update() or LateUpdate().</span></span>

<span data-ttu-id="2193a-286">その他のクイック ヒント:</span><span class="sxs-lookup"><span data-stu-id="2193a-286">Other quick tips:</span></span>
- <span data-ttu-id="2193a-287">使用して、 [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C#クラスで動的に実行時に複雑な文字列をビルドするには</span><span class="sxs-lookup"><span data-stu-id="2193a-287">Use the [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# class to dynamically build complex strings at runtime</span></span>
- <span data-ttu-id="2193a-288">Debug.Log() アプリのすべてのビルド バージョンで引き続き実行時に不要になったときに呼び出しを削除します</span><span class="sxs-lookup"><span data-stu-id="2193a-288">Remove calls to Debug.Log() when no longer needed as they still execute in all build versions of an app</span></span>
- <span data-ttu-id="2193a-289">Holographic アプリは、一般に、大量のメモリを必要とする場合は、呼び出すことを検討してください[ _**System.GC.Collect()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2)などのフェーズを読み込み中に、読み込みを提示するとき、または画面の切り替え</span><span class="sxs-lookup"><span data-stu-id="2193a-289">If your holographic app generally requires lots of memory, consider calling  [_**System.GC.Collect()**_](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) during loading phases such as when presenting a loading or transition screen</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="2193a-290">オブジェクト プール</span><span class="sxs-lookup"><span data-stu-id="2193a-290">Object pooling</span></span>

<span data-ttu-id="2193a-291">オブジェクト プールは、オブジェクトの割り当て解除 (&)、継続的な割り当てのコストを削減する、一般的な手法です。</span><span class="sxs-lookup"><span data-stu-id="2193a-291">Object pooling is a popular technique to reduce the cost of continuous allocations & deallocations of objects.</span></span> <span data-ttu-id="2193a-292">これは、同一のオブジェクトの大きなプールを割り当てると、常に生成し、時間の経過と共にオブジェクトを破棄するのではなく、このプールから再アクティブでない、利用可能なインスタンスを使用して実行します。</span><span class="sxs-lookup"><span data-stu-id="2193a-292">This is done by allocating a large pool of identical objects and re-using inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="2193a-293">オブジェクト プールは、アプリの中に変数の有効期間を持つ再利用可能なコンポーネントに適しています。</span><span class="sxs-lookup"><span data-stu-id="2193a-293">Object pools are great for re-useable components that have variable lifetime during an app.</span></span>

- [<span data-ttu-id="2193a-294">オブジェクト プールの Unity のチュートリアル</span><span class="sxs-lookup"><span data-stu-id="2193a-294">Object Pooling Tutorial in Unity</span></span>](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a><span data-ttu-id="2193a-295">起動時のパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="2193a-295">Startup performance</span></span>

<span data-ttu-id="2193a-296">小規模のシーンをアプリを起動しを使用する必要があります *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* を残りのシーンを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="2193a-296">You should consider starting your app with a smaller scene, then using *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* to load the rest of the scene.</span></span> <span data-ttu-id="2193a-297">これにより、アプリをできる限り早く対話状態を取得できます。</span><span class="sxs-lookup"><span data-stu-id="2193a-297">This allows your app to get to an interactive state as fast as possible.</span></span> <span data-ttu-id="2193a-298">対応をある可能性があります、大きな CPU スパイク新しいシーンがアクティブ化中に、レンダリングされたコンテンツが途切れこと」または「問題。</span><span class="sxs-lookup"><span data-stu-id="2193a-298">Be aware that there may be a large CPU spike while the new scene is being activated and that any rendered content might stutter or hitch.</span></span> <span data-ttu-id="2193a-299">これを回避する方法の 1 つは、読み込まれているシーンで AsyncOperation.allowSceneActivation プロパティを false に設定、読み込み、黒に画面のクリア、および、戻るシーンのアクティブ化が完了する場合は true に設定してシーンの待機です。</span><span class="sxs-lookup"><span data-stu-id="2193a-299">One way to work around this is to set the AsyncOperation.allowSceneActivation property to false on the scene being loaded, wait for the scene to load, clear the screen to black, and then set back to true to complete the scene activation.</span></span>

<span data-ttu-id="2193a-300">スタートアップ シーンの読み込み中に、holographic のスプラッシュ スクリーンは、ユーザーに表示されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2193a-300">Remember that while the startup scene is loading the holographic splash screen will be displayed to the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="2193a-301">関連項目</span><span class="sxs-lookup"><span data-stu-id="2193a-301">See also</span></span>
- [<span data-ttu-id="2193a-302">Unity ゲームのグラフィックス レンダリングの最適化</span><span class="sxs-lookup"><span data-stu-id="2193a-302">Optimizing graphics rendering in Unity games</span></span>](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [<span data-ttu-id="2193a-303">Unity ゲームでのガベージ コレクションの最適化</span><span class="sxs-lookup"><span data-stu-id="2193a-303">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- <span data-ttu-id="2193a-304">[物理運動のベスト プラクティス [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span><span class="sxs-lookup"><span data-stu-id="2193a-304">[Physics Best Practices [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span></span>
- <span data-ttu-id="2193a-305">[スクリプト [Unity] の最適化](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span><span class="sxs-lookup"><span data-stu-id="2193a-305">[Optimizing Scripts [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span></span>
