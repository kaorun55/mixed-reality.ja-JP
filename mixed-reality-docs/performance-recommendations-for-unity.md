---
title: Unity のパフォーマンスに関する推奨事項
description: Mixed Reality アプリのパフォーマンスを向上させるための Unity 固有のヒント。
author: troy-ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: グラフィックス, cpu, gpu, レンダリング, ガベージ コレクション, hololens
ms.localizationpriority: high
ms.openlocfilehash: 28f09986cdb8c562aedfc9deae7b0369214ebc05
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2020
ms.locfileid: "81277570"
---
# <a name="performance-recommendations-for-unity"></a><span data-ttu-id="ec6de-104">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="ec6de-104">Performance recommendations for Unity</span></span>

<span data-ttu-id="ec6de-105">この記事は、[Mixed Reality のパフォーマンスに関する推奨事項](understanding-performance-for-mixed-reality.md)についての記事の内容が基になっていますが、Unity エンジン環境に固有の学習に焦点を当てています。</span><span class="sxs-lookup"><span data-stu-id="ec6de-105">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md) but focuses on learnings specific to the Unity engine environment.</span></span>

## <a name="use-recommended-unity-project-settings"></a><span data-ttu-id="ec6de-106">推奨される Unity プロジェクト設定を使用する</span><span class="sxs-lookup"><span data-stu-id="ec6de-106">Use recommended Unity project settings</span></span>

<span data-ttu-id="ec6de-107">Unity で Mixed Reality アプリのパフォーマンスを最適化する際に最も重要な初めのステップは、[推奨される Unity の環境設定](recommended-settings-for-unity.md)を使用しているかどうかを確認することです。</span><span class="sxs-lookup"><span data-stu-id="ec6de-107">The most important first step when optimizing performance of mixed reality apps in Unity is to be sure you are using the [recommended environment settings for Unity](recommended-settings-for-unity.md).</span></span> <span data-ttu-id="ec6de-108">この記事には、パフォーマンスに優れた Mixed Reality アプリを構築するための最も重要なシーン構成に関するコンテンツが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ec6de-108">That article contains content with some of the most important scene configurations for building performant Mixed Reality apps.</span></span> <span data-ttu-id="ec6de-109">これらの推奨設定の一部は、以下でも強調して示されています。</span><span class="sxs-lookup"><span data-stu-id="ec6de-109">Some of these recommended settings are highlighted below, as well.</span></span>

## <a name="how-to-profile-with-unity"></a><span data-ttu-id="ec6de-110">Unity でプロファイルする方法</span><span class="sxs-lookup"><span data-stu-id="ec6de-110">How to profile with Unity</span></span>

<span data-ttu-id="ec6de-111">Unity に組み込まれている **[Unity プロファイラー](https://docs.unity3d.com/Manual/Profiler.html)** は、特定のアプリに関する貴重なパフォーマンスの分析情報を収集するための優れたリソースです。</span><span class="sxs-lookup"><span data-stu-id="ec6de-111">Unity provides the **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** built-in, which is a great resource to gather valuable performance insights for your particular app.</span></span> <span data-ttu-id="ec6de-112">エディターでプロファイラーを実行できますが、これらのメトリックは実際のランタイム環境を表していないため、その結果は慎重に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-112">Although one can run the profiler in-editor, these metrics do not represent the true runtime environment and thus, results from this should be used cautiously.</span></span> <span data-ttu-id="ec6de-113">最も正確で実用的な分析情報を得るには、デバイスでアプリケーションを実行しながらリモートでプロファイルすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ec6de-113">It is recommended to remotely profile your application while running on device for most accurate and actionable insights.</span></span> <span data-ttu-id="ec6de-114">さらに、Unity の [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html) も、利用すると非常に強力な分析情報ツールです。</span><span class="sxs-lookup"><span data-stu-id="ec6de-114">Further, Unity's [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html) is also a very powerful and insight tool to utilize.</span></span>

<span data-ttu-id="ec6de-115">Unity では、次のことに関する優れたドキュメントが提供されています。</span><span class="sxs-lookup"><span data-stu-id="ec6de-115">Unity provides great documentation for:</span></span>
1) <span data-ttu-id="ec6de-116">[Unity プロファイラーを UWP アプリケーションにリモート](https://docs.unity3d.com/Manual/windowsstore-profiler.html)で接続する方法</span><span class="sxs-lookup"><span data-stu-id="ec6de-116">How to connect the [Unity profiler to UWP applications remotely](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span></span>
2) <span data-ttu-id="ec6de-117">[Unity プロファイラーでパフォーマンスの問題を効果的に診断する](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)方法</span><span class="sxs-lookup"><span data-stu-id="ec6de-117">How to effectively [diagnose performance problems with the Unity Profiler](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span></span>

>[!NOTE]
> <span data-ttu-id="ec6de-118">Unity プロファイラーを接続し、GPU プロファイラーを追加した後 (右上隅の「*プロファイラーの追加*」を参照)、プロファイラーの中央で CPU と GPU それぞれで費やされている時間を確認できます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-118">With the Unity Profiler connected and after adding the GPU profiler (see *Add Profiler* in top right corner), one can see how much time is being spent on the CPU & GPU respectively in the middle of the profiler.</span></span> <span data-ttu-id="ec6de-119">これにより、開発者は簡単に、アプリケーションが CPU バウンドか GPU バウンドかをだいたい確認できます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-119">This allows the developer to get a quick approximation if their application is CPU or GPU bounded.</span></span>
>
> ![Unity の CPU と GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a><span data-ttu-id="ec6de-121">CPU のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="ec6de-121">CPU performance recommendations</span></span>

<span data-ttu-id="ec6de-122">以下では、特に Unity と C# の開発でのパフォーマンスに関する慣例についてさらに詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="ec6de-122">The content below covers more in-depth performance practices, especially targeted for Unity & C# development.</span></span>

#### <a name="cache-references"></a><span data-ttu-id="ec6de-123">参照をキャッシュする</span><span class="sxs-lookup"><span data-stu-id="ec6de-123">Cache references</span></span>

<span data-ttu-id="ec6de-124">初期化時に、関連するすべてのコンポーネントと GameObject への参照をキャッシュするのがベスト プラクティスです。</span><span class="sxs-lookup"><span data-stu-id="ec6de-124">It is best practice to cache references to all relevant components and GameObjects at initialization.</span></span> <span data-ttu-id="ec6de-125">これは、 *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* のような関数呼び出しを繰り返すと、ポインターを格納するためのコストの方がメモリ コストよりかなり大きくなるためです。</span><span class="sxs-lookup"><span data-stu-id="ec6de-125">This is because repeating function calls such as *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* are significantly more expensive relative to the memory cost to store a pointer.</span></span> <span data-ttu-id="ec6de-126">これはまた、非常によく使用される [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html) にも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-126">This also applies to to the very regularly used [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).</span></span> <span data-ttu-id="ec6de-127">*Camera.main* では実際には基になっている *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* が使用されるだけであり、そこで行われるシーン グラフでの *"MainCamera"* タグの付いたカメラ オブジェクトの検索にはコストがかかります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-127">*Camera.main* actually just uses *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* underneath, which expensively searches your scene graph for a camera object with the *"MainCamera"* tag.</span></span>

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
> <span data-ttu-id="ec6de-128">GetComponent(string) を使用しない</span><span class="sxs-lookup"><span data-stu-id="ec6de-128">Avoid GetComponent(string)</span></span> <br/>
> <span data-ttu-id="ec6de-129">*[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* を使用と、いくつかの異なるオーバーロードが発生します。</span><span class="sxs-lookup"><span data-stu-id="ec6de-129">When using *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)*, there are a handful of different overloads.</span></span> <span data-ttu-id="ec6de-130">常に、型ベースの実装を使用し、文字列ベースの検索オーバーロードは使用しないことが重要です。</span><span class="sxs-lookup"><span data-stu-id="ec6de-130">It is important to always use the Type-based implementations and never the string-based searching overload.</span></span> <span data-ttu-id="ec6de-131">シーンでの文字列による検索は、型での検索よりかなりコストがかかります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-131">Searching by string in your scene is significantly more costly than searching by Type.</span></span> <br/>
> <span data-ttu-id="ec6de-132">(正しい) Component GetComponent(Type type)</span><span class="sxs-lookup"><span data-stu-id="ec6de-132">(Good) Component GetComponent(Type type)</span></span> <br/>
> <span data-ttu-id="ec6de-133">(正しい) T GetComponent\<T>()</span><span class="sxs-lookup"><span data-stu-id="ec6de-133">(Good) T GetComponent\<T>()</span></span> <br/>
> <span data-ttu-id="ec6de-134">(正しくない) Component GetComponent(string)></span><span class="sxs-lookup"><span data-stu-id="ec6de-134">(Bad) Component GetComponent(string)></span></span> <br/>

#### <a name="avoid-expensive-operations"></a><span data-ttu-id="ec6de-135">コストのかかる操作を避ける</span><span class="sxs-lookup"><span data-stu-id="ec6de-135">Avoid expensive operations</span></span>

1) <span data-ttu-id="ec6de-136">**[LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq) を使わないようにする**</span><span class="sxs-lookup"><span data-stu-id="ec6de-136">**Avoid use of [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span></span>

    <span data-ttu-id="ec6de-137">LINQ は非常にすっきりしていて、読みことも書くことも簡単な場合がありますが、一般に、アルゴリズムを手作業で記述するより、計算と、特にメモリの割り当てが、はるかに多く必要になります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-137">Although LINQ can be very clean and easy to read and write, it generally requires much more computation and particularly more memory allocation than writing the algorithm out manually.</span></span>

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) <span data-ttu-id="ec6de-138">**一般的な Unity API**</span><span class="sxs-lookup"><span data-stu-id="ec6de-138">**Common Unity APIs**</span></span>

    <span data-ttu-id="ec6de-139">特定の Unity API は便利ですが、実行コストが非常に大きくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-139">Certain Unity APIs, although useful, can be very expensive to execute.</span></span> <span data-ttu-id="ec6de-140">それらの多くには、シーン グラフ全体での、一致する GameObject のリストの検索が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-140">Most of these involve searching your entire scene graph for some matching list of GameObjects.</span></span> <span data-ttu-id="ec6de-141">これらの操作は、一般に、参照をキャッシュするか、問題のある GameObject に対するマネージャー コンポーネントを実装して実行時に参照を追跡することで回避できます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-141">These operations can generally be avoided by caching references or implementing a manager component for the GameObjects in question to track the references at runtime.</span></span>

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> <span data-ttu-id="ec6de-142">*[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* と *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* は、絶対に除去する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-142">*[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* and *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* should be eliminated at all costs.</span></span> <span data-ttu-id="ec6de-143">これらの関数は、関数を直接呼び出すより 1,000 倍も遅くなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-143">These functions can be on the order of 1000x slower than direct function calls.</span></span>

3) <span data-ttu-id="ec6de-144">**ボックス化に注意する**</span><span class="sxs-lookup"><span data-stu-id="ec6de-144">**Beware of boxing**</span></span>

    <span data-ttu-id="ec6de-145">[ボックス化](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing)は、C# 言語とランタイムの中核となる概念です。</span><span class="sxs-lookup"><span data-stu-id="ec6de-145">[Boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) is a core concept of the C# language and runtime.</span></span> <span data-ttu-id="ec6de-146">これは、char、int、bool などの値型変数を参照型変数の中にラップするプロセスです。</span><span class="sxs-lookup"><span data-stu-id="ec6de-146">It is the process of wrapping value-typed variables such as char, int, bool, etc. into reference-typed variables.</span></span> <span data-ttu-id="ec6de-147">値型変数が "ボックス化" されると、マネージド ヒープに格納される System.Object の内部にラップされます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-147">When a value-typed variable is "boxed", it is wrapped inside of a System.Object which is stored on the managed heap.</span></span> <span data-ttu-id="ec6de-148">したがって、メモリが割り当てられ、最終的に破棄されるときは、ガベージ コレクターによって処理される必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-148">Thus, memory is allocated and eventually when disposed must be processed by the garbage collector.</span></span> <span data-ttu-id="ec6de-149">これらの割り当てと割り当て解除は、パフォーマンス コストの原因になり、多くのシナリオでは、不要であるか、低コストの代替手段で簡単に置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-149">These allocations and deallocations incur a performance cost and in many scenarios are unnecessary or can be easily replaced by a less expensive alternative.</span></span>

    <span data-ttu-id="ec6de-150">開発でのボックス化の最も一般的な形式の 1 つは、[null 許容値型](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/)の使用です。</span><span class="sxs-lookup"><span data-stu-id="ec6de-150">One of the most common forms of boxing in development is the use of [nullable value types](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/).</span></span> <span data-ttu-id="ec6de-151">関数で値型に対して null を返すことができるようにするのはよくあることであり、値を取得しようとして操作が失敗する可能性がある場合は特にそうです。</span><span class="sxs-lookup"><span data-stu-id="ec6de-151">It is common to want to be able to return null for a value type in a function, especially when the operation may fail trying to get the value.</span></span> <span data-ttu-id="ec6de-152">この方法で発生する可能性のある問題は、ヒープで割り当てを行ったため、後でガベージ コレクションが必要になることです。</span><span class="sxs-lookup"><span data-stu-id="ec6de-152">The potential problem with this approach is that allocation now occurs on the heap and consequently needs to be garbage collected later.</span></span>

    <span data-ttu-id="ec6de-153">**C# でのボックス化の例**</span><span class="sxs-lookup"><span data-stu-id="ec6de-153">**Example of boxing in C#**</span></span>

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

    <span data-ttu-id="ec6de-154">**null 許容値型を使用したことで問題のあるボックス化の例**</span><span class="sxs-lookup"><span data-stu-id="ec6de-154">**Example of problematic boxing via nullable value types**</span></span>

    <span data-ttu-id="ec6de-155">このコードは、Unity プロジェクトで作成する可能性のあるダミー パーティクル クラスを示したものです。</span><span class="sxs-lookup"><span data-stu-id="ec6de-155">This code demonstrates a dummy particle class that one may create in a Unity project.</span></span> <span data-ttu-id="ec6de-156">`TryGetSpeed()` の呼び出しにより、後でガベージ コレクションが必要になるオブジェクトの割り当てがヒープで行われます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-156">A call to `TryGetSpeed()` will cause object allocation on the heap which will need to be garbage collected at a later point in time.</span></span> <span data-ttu-id="ec6de-157">この例の場合、1000 個またはそれよりずっと多くのパーティクルがシーン内にあり、それぞれに対して現在の速度が要求されるため、特に問題になります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-157">This example is particularly problematic as there may be 1000+ or many more particles in a scene, each being asked for their current speed.</span></span> <span data-ttu-id="ec6de-158">したがって、何千個ものオブジェクトが割り当てられ、結果としてすべてのフレームが割り当て解除されるため、パフォーマンスが大幅に低下します。</span><span class="sxs-lookup"><span data-stu-id="ec6de-158">Thus, 1000's of objects would be allocated and consequently de-allocated every frame, which would greatly diminish performance.</span></span> <span data-ttu-id="ec6de-159">エラーが発生したことを示す -1 などの負の値を返すように関数を書き直すと、この問題は回避され、メモリがスタックに保持されます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-159">Re-writing the function to return a negative value such as -1 to indicate a failure would avoid this issue and keep memory on the stack.</span></span>

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

#### <a name="repeating-code-paths"></a><span data-ttu-id="ec6de-160">コード パスの繰り返し</span><span class="sxs-lookup"><span data-stu-id="ec6de-160">Repeating code paths</span></span>

<span data-ttu-id="ec6de-161">繰り返し実行される Unity コールバック関数 (</span><span class="sxs-lookup"><span data-stu-id="ec6de-161">Any repeating Unity callback functions (i.e</span></span> <span data-ttu-id="ec6de-162">Update など) で、1 秒間またはフレームごとの実行回数多いものは、非常に慎重に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-162">Update) that are executed many times per second and/or frame should be written very carefully.</span></span> <span data-ttu-id="ec6de-163">ここでコストのかかる操作を行うと、パフォーマンスが常に大きな影響を受けるようになります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-163">Any expensive operations here will have huge and consistent impact on performance.</span></span>

1) <span data-ttu-id="ec6de-164">**空のコールバック関数**</span><span class="sxs-lookup"><span data-stu-id="ec6de-164">**Empty callback functions**</span></span>

    <span data-ttu-id="ec6de-165">次のようなコードはアプリケーション内に残しても害がないように見えますが、特にすべての Unity スクリプトがこのコード ブロックで自動的に初期化するため、これらの空のコールバックは実際には非常に高コストになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-165">Although the code below may seem innocent to leave in your application, especially since every Unity script auto-initializes with this code block, these empty callbacks can actually become very expensive.</span></span> <span data-ttu-id="ec6de-166">Unity では、UnityEngine コードとアプリケーション コードの間で、アンマネージド コードとマネージド コードの境界を越えて行き来する動作が発生します。</span><span class="sxs-lookup"><span data-stu-id="ec6de-166">Unity operates back and forth over an unmanaged/managed code boundary, between UnityEngine code and your application code.</span></span> <span data-ttu-id="ec6de-167">実行するものがない場合であっても、このブリッジを越えるコンテキストの切り替えには大きなコストがかかります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-167">Context switching over this bridge is fairly expensive, even if there is nothing to execute.</span></span> <span data-ttu-id="ec6de-168">繰り返し呼び出される空の Unity コールバックを持つコンポーネントが含まれる GameObject がアプリに何百個もある場合、これは特に問題になります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-168">This becomes especially problematic if your app has 100's of GameObjects with components that have empty repeating Unity callbacks.</span></span>

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> <span data-ttu-id="ec6de-169">このようなパフォーマンスの問題の原因として最も一般的なものは Update() ですが、次のような他の反復的な Unity コールバックも、さらに悪くはないにしても、同程度に悪影響を及ぼす可能性があります: FixedUpdate()、LateUpdate()、OnPostRender()、OnPreRender()、OnRenderImage() など。</span><span class="sxs-lookup"><span data-stu-id="ec6de-169">Update() is the most common manifestation of this performance issue but other repeating Unity callbacks, such as the following can be equally as bad, if not worse: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc.</span></span> 

2) <span data-ttu-id="ec6de-170">**フレームごとに 1 回実行したくなる操作**</span><span class="sxs-lookup"><span data-stu-id="ec6de-170">**Operations to favor running once per frame**</span></span>

    <span data-ttu-id="ec6de-171">次の Unity API は、多くのホログラフィック アプリで一般的な操作です。</span><span class="sxs-lookup"><span data-stu-id="ec6de-171">The following Unity APIs are common operations for many Holographic Apps.</span></span> <span data-ttu-id="ec6de-172">常に可能であるとは限りませんが、これらの関数の結果は、1 回計算すれば、アプリケーション全体で特定のフレームに対して再利用できることが非常によくあります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-172">Although not always possible, the results from these functions can very commonly be computed once and the results re-utilized across the application for a given frame.</span></span>

    <span data-ttu-id="ec6de-173">a) 一般に、基本的に同じ Raycast 操作をコンポーネントごとに繰り返し行うのではなく、シーンに対する視線 Raycast を処理する専用のシングルトン クラスまたはサービスを用意し、他のすべてのシーン コンポーネントではこの結果を再利用することがよい方法です。</span><span class="sxs-lookup"><span data-stu-id="ec6de-173">a) Generally it is good practice to have a dedicated Singleton class or service to handle your gaze Raycast into the scene and then re-use this result in all other scene components, instead of making repeated and essentially identical Raycast operations by each component.</span></span> <span data-ttu-id="ec6de-174">もちろん、アプリケーションによっては、異なるオリジンからの Raycast、または異なる [LayerMask](https://docs.unity3d.com/ScriptReference/LayerMask.html) に対する Raycast が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-174">Of course, some applications may require raycasts from different origins or against different [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html).</span></span>

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    <span data-ttu-id="ec6de-175">b) Update() などの繰り返される Unity コールバックでの GetComponent() 操作は、Start() または Awake() で[参照をキャッシュする](#cache-references)ことによって回避します</span><span class="sxs-lookup"><span data-stu-id="ec6de-175">b) Avoid GetComponent() operations in repeated Unity callbacks like Update() by [caching references](#cache-references) in Start() or Awake()</span></span>

        UnityEngine.Object.GetComponent()

    <span data-ttu-id="ec6de-176">c) 可能であれば、初期化時にすべてのオブジェクトをインスタンス化し、[オブジェクト プーリング](#object-pooling)を使用して、アプリケーションの実行時全体を通して GameObject を再利用するのがよい方法です</span><span class="sxs-lookup"><span data-stu-id="ec6de-176">c) It is good practice to instantiate all objects, if possible, at initialization and use [object pooling](#object-pooling) to recycle and re-use GameObjects throughout runtime of your application</span></span>

        UnityEngine.Object.Instantiate()

3) <span data-ttu-id="ec6de-177">**インターフェイスと仮想コンストラクトを避ける**</span><span class="sxs-lookup"><span data-stu-id="ec6de-177">**Avoid interfaces and virtual constructs**</span></span>

    <span data-ttu-id="ec6de-178">直接オブジェクトではなくインターフェイスを介した関数の呼び出し、または仮想関数の呼び出しは、直接コンストラクトまたは直接関数呼び出しを利用するより、はるかにコストがかかることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-178">Invoking function calls through interfaces vs direct objects or calling virtual functions can often times be much more expensive than utilizing direct constructs or direct function calls.</span></span> <span data-ttu-id="ec6de-179">仮想関数またはインターフェイスが不要な場合は、削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-179">If the virtual function or interface is unnecessary, then it should be removed.</span></span> <span data-ttu-id="ec6de-180">ただし、開発の共同作業、コードの読みやすさ、コードの保守性を容易にするためにこれらの方法を利用する場合は、一般に、これらの方法によるパフォーマンスへの影響とトレードオフする価値があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-180">However, the performance hit for these approaches are generally worth the trade-off if utilizing them simplifies development collaboration, code readability, and code maintainability.</span></span>

    <span data-ttu-id="ec6de-181">一般に、このメンバーを上書きする必要があると明確に予想される場合を除き、フィールドや関数を仮想としてマークしないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ec6de-181">Generally, the recommendation is to not mark fields and functions as virtual unless there is a clear expectation that this member needs to be overwritten.</span></span> <span data-ttu-id="ec6de-182">`UpdateUI()` メソッドなど、フレームごとに何回も呼び出される高頻度のコード パスは (フレームごとに 1 回であっても)、特に注意して使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-182">One should be especially careful around high-frequency code paths that are called many times per frame or even once per frame such as an `UpdateUI()` method.</span></span>

4) <span data-ttu-id="ec6de-183">**構造体を値で渡さないようにする**</span><span class="sxs-lookup"><span data-stu-id="ec6de-183">**Avoid passing structs by value**</span></span>

    <span data-ttu-id="ec6de-184">クラスとは異なり、構造体は値型であり、関数に直接渡すと、その内容が新しく作成されるインスタンスにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-184">Unlike classes, structs are value-types and when passed directly to a function, their contents are copied into a newly created instance.</span></span> <span data-ttu-id="ec6de-185">このコピーにより、CPU コストが発生し、スタックにメモリが追加されます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-185">This copy adds CPU cost, as well as additional memory on the stack.</span></span> <span data-ttu-id="ec6de-186">小さい構造体であれば、通常、影響は最小限であるため、許容されます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-186">For small structs, the effect is usually very minimal and thus acceptable.</span></span> <span data-ttu-id="ec6de-187">しかし、すべてのフレームで繰り返し呼び出される関数や、大きな構造体を受け取る関数の場合は、可能であれば、関数定義を変更して参照渡しにします。</span><span class="sxs-lookup"><span data-stu-id="ec6de-187">However, for functions repeatedly invoked every frame as well as functions taking large structs, if possible modify the function definition to pass by reference.</span></span> [<span data-ttu-id="ec6de-188">詳細については、こちらを参照してください</span><span class="sxs-lookup"><span data-stu-id="ec6de-188">Learn more here</span></span>](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a><span data-ttu-id="ec6de-189">その他</span><span class="sxs-lookup"><span data-stu-id="ec6de-189">Miscellaneous</span></span>

1) <span data-ttu-id="ec6de-190">**物理計算**</span><span class="sxs-lookup"><span data-stu-id="ec6de-190">**Physics**</span></span>

    <span data-ttu-id="ec6de-191">a) 一般に、物理計算を改善する最も簡単な方法は、物理計算にかける時間または 1 秒あたりの反復回数を制限することです。</span><span class="sxs-lookup"><span data-stu-id="ec6de-191">a) Generally, the easiest way to improve physics is to limit the amount of time spent on Physics or the number of iterations per second.</span></span> <span data-ttu-id="ec6de-192">もちろん、これによりシミュレーションの精度は低下します。</span><span class="sxs-lookup"><span data-stu-id="ec6de-192">Of course, this will reduce simulation accuracy.</span></span> <span data-ttu-id="ec6de-193">Unity の [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) を参照してください</span><span class="sxs-lookup"><span data-stu-id="ec6de-193">See [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) in Unity</span></span>

    <span data-ttu-id="ec6de-194">b) Unity でのコライダーの種類には、さまざまなパフォーマンス特性があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-194">b) The type of colliders in Unity have widely different performance characteristics.</span></span> <span data-ttu-id="ec6de-195">次に示すのは、コライダーをパフォーマンスが最もよいもの (左端) から最も悪いもの (右端) まで順に並べたものです。</span><span class="sxs-lookup"><span data-stu-id="ec6de-195">The order below lists the most performant colliders to least performant colliders from left to right.</span></span> <span data-ttu-id="ec6de-196">メッシュ コライダーを避けることが最も重要です。メッシュ コライダーは、プリミティブ コライダーよりはるかにコストが高くなります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-196">It is most important to avoid Mesh Colliders, which are substantially more expensive than the primitive colliders.</span></span>

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    <span data-ttu-id="ec6de-197">詳細については、[Unity の物理計算のベスト プラクティス](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)に関するページを参照してください</span><span class="sxs-lookup"><span data-stu-id="ec6de-197">See [Unity Physics Best Practices](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) for more info</span></span>

2) <span data-ttu-id="ec6de-198">**アニメーション**</span><span class="sxs-lookup"><span data-stu-id="ec6de-198">**Animations**</span></span>

    <span data-ttu-id="ec6de-199">Animator コンポーネントを無効にして、アイドル状態のアニメーションを無効にします (ゲーム オブジェクトを無効にしても同じ効果は得られません)。</span><span class="sxs-lookup"><span data-stu-id="ec6de-199">Disable idle animations by disabling the Animator component (disabling the game object won't have the same effect).</span></span> <span data-ttu-id="ec6de-200">同じものに値を設定するループ内にアニメーターを配置する設計パターンは避けます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-200">Avoid design patterns where an animator sits in a loop setting a value to the same thing.</span></span> <span data-ttu-id="ec6de-201">この方法にはかなりのオーバーヘッドがありますが、アプリケーションへの効果はありません。</span><span class="sxs-lookup"><span data-stu-id="ec6de-201">There is considerable overhead for this technique, with no effect on the application.</span></span> [<span data-ttu-id="ec6de-202">詳細については、こちらを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec6de-202">Learn more here.</span></span>](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) <span data-ttu-id="ec6de-203">**複雑なアルゴリズム**</span><span class="sxs-lookup"><span data-stu-id="ec6de-203">**Complex algorithms**</span></span>

    <span data-ttu-id="ec6de-204">アプリケーションで、逆キネマティクスやパス ファインディングなどの複雑なアルゴリズムを使用している場合は、より簡単なアプローチを見つけたり、パフォーマンスに関連する設定を調整したりします</span><span class="sxs-lookup"><span data-stu-id="ec6de-204">If your application is using complex algorithms such as inverse kinematics, path finding, etc, look to find a simpler approach or adjust relevant settings for their performance</span></span>

## <a name="cpu-to-gpu-performance-recommendations"></a><span data-ttu-id="ec6de-205">CPU と GPU のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="ec6de-205">CPU-to-GPU performance recommendations</span></span>

<span data-ttu-id="ec6de-206">一般に、CPU と GPU のパフォーマンスは、グラフィックスカードに送信される**描画呼び出し**に行き着きます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-206">Generally, CPU-to-GPU performance comes down to the **draw calls** submitted to the graphics card.</span></span> <span data-ttu-id="ec6de-207">パフォーマンスを向上させるには、最適な結果が得られるように描画呼び出しを戦略的に **a) 減らす**か、または **b) 再構築する**必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-207">To improve performance, draw calls need to be strategically **a) reduced** or **b) restructured** for optimal results.</span></span> <span data-ttu-id="ec6de-208">描画呼び出し自体がリソースを集中的に使用するため、呼び出しを減らすと必要な作業全体が減ります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-208">Since draw calls themselves are resource-intensive, reducing them will reduce overall work required.</span></span> <span data-ttu-id="ec6de-209">さらに、描画呼び出し間の状態変化には、グラフィックス ドライバーでコストのかかる検証と変換のステップが必要であるため、アプリケーションの描画呼び出しを再構築して状態の変化を制限すると (つまり、</span><span class="sxs-lookup"><span data-stu-id="ec6de-209">Further, state changes between draw calls requires costly validation and translation steps in the graphics driver and thus, restructuring of your application's draw calls to limit state changes (i.e</span></span> <span data-ttu-id="ec6de-210">異なる素材など) パフォーマンスが向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-210">different materials, etc) can boost performance.</span></span>

<span data-ttu-id="ec6de-211">Unity には、それらのプラットフォームに対する描画呼び出しのバッチ処理に関する概要と詳細がわかる優れた記事があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-211">Unity has a great article that gives an overview and dives into batching draw calls for their platform.</span></span>
- [<span data-ttu-id="ec6de-212">Unity の描画呼び出しのバッチ処理</span><span class="sxs-lookup"><span data-stu-id="ec6de-212">Unity Draw Call Batching</span></span>](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a><span data-ttu-id="ec6de-213">単一パス インスタンス化レンダリング</span><span class="sxs-lookup"><span data-stu-id="ec6de-213">Single pass instanced rendering</span></span>

<span data-ttu-id="ec6de-214">Unity の単一パス インスタンス化レンダリングを使用すると、各視点に対する描画呼び出しを 1 つのインスタンス化描画呼び出しに減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-214">Single Pass Instanced Rendering in Unity allows for draw calls for each eye to be reduced down to one instanced draw call.</span></span> <span data-ttu-id="ec6de-215">2 つの描画呼び出し間のキャッシュの一貫性により、GPU のパフォーマンスもある程度向上します。</span><span class="sxs-lookup"><span data-stu-id="ec6de-215">Due to cache coherency between two draw calls, there is also some performance improvement on the GPU as well.</span></span>

<span data-ttu-id="ec6de-216">Unity プロジェクトでこの機能を有効にするには</span><span class="sxs-lookup"><span data-stu-id="ec6de-216">To enable this feature in your Unity Project</span></span>
1)  <span data-ttu-id="ec6de-217">**[Player XR Settings]\(プレーヤー XR 設定\)** を開きます ( **[Edit]\(編集\)**  >  **[Project Settings]\(プロジェクト設定\)**  >  **[Player]\(プレーヤー\)**  >  **[XR Settings]\(XR 設定\)** )</span><span class="sxs-lookup"><span data-stu-id="ec6de-217">Open **Player XR Settings** (go to **Edit** > **Project Settings** > **Player** > **XR Settings**)</span></span>
2) <span data-ttu-id="ec6de-218">**[Stereo Rendering Method]\(ステレオ レンダリング方法\)** ドロップダウン メニューから **[Single Pass Instanced]\(単一パス インスタンス化\)** を選択します ( **[Virtual Reality Supported]\(仮想現実のサポート\)** チェック ボックスをオンにする必要があります)</span><span class="sxs-lookup"><span data-stu-id="ec6de-218">Select **Single Pass Instanced** from the **Stereo Rendering Method** drop-down menu (**Virtual Reality Supported** checkbox must be checked)</span></span>

<span data-ttu-id="ec6de-219">このレンダリング方法の詳細については、Unity の次の記事をお読みください。</span><span class="sxs-lookup"><span data-stu-id="ec6de-219">Read the following articles from Unity for details with this rendering approach.</span></span>
- [<span data-ttu-id="ec6de-220">高度なステレオ レンダリングを使用して AR と VR のパフォーマンスを最大化する方法</span><span class="sxs-lookup"><span data-stu-id="ec6de-220">How to maximize AR and VR performance with advanced stereo rendering</span></span>](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [<span data-ttu-id="ec6de-221">単一パス インスタンス化</span><span class="sxs-lookup"><span data-stu-id="ec6de-221">Single Pass Instancing</span></span>](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> <span data-ttu-id="ec6de-222">単一パス インスタンス化レンダリングに関する一般的な問題の 1 つは、開発者がインスタンス化対応に作成されていない既存のカスタム シェーダーを持っている場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="ec6de-222">One common issue with Single Pass Instanced Rendering occurs if developers already have existing custom shaders not written for instancing.</span></span> <span data-ttu-id="ec6de-223">この機能を有効にした後、開発者は、一部の GameObject が 1 つの視線でしかレンダリングしないことに気付く場合があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-223">After enabling this feature, developers may notice some GameObjects only render in one eye.</span></span> <span data-ttu-id="ec6de-224">これは、関連付けられたカスタム シェーダーに、インスタンス化のための適切なプロパティがないためです。</span><span class="sxs-lookup"><span data-stu-id="ec6de-224">This is because the associated custom shaders do not have the appropriate properties for instancing.</span></span>
>
> <span data-ttu-id="ec6de-225">この問題への対処方法については、Unity から提供されている [HoloLens 用の単一パス ステレオ レンダリング](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)に関する記事を参照してください</span><span class="sxs-lookup"><span data-stu-id="ec6de-225">See [Single Pass Stereo Rendering for HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) from Unity for how to address this problem</span></span>

#### <a name="static-batching"></a><span data-ttu-id="ec6de-226">静的バッチ処理</span><span class="sxs-lookup"><span data-stu-id="ec6de-226">Static batching</span></span>

<span data-ttu-id="ec6de-227">Unity では、多くの静的オブジェクトをバッチ処理して、GPU への描画呼び出しを減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-227">Unity is able to batch many static objects to reduce draw calls to the GPU.</span></span> <span data-ttu-id="ec6de-228">静的バッチ処理は、**1) 同じ素材を共有し**、**2) *Static* とマークされている**、Unity のほとんどの [Renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) オブジェクトで動作します (Unity でオブジェクトを選択し、インスペクターの右上にあるチェック ボックスをオンにします)。</span><span class="sxs-lookup"><span data-stu-id="ec6de-228">Static Batching works for most [Renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) objects in Unity that **1) share the same material** and **2) are all marked as *Static*** (Select an object in Unity and click the checkbox in the top right of the inspector).</span></span> <span data-ttu-id="ec6de-229">*Static* とマークされている GameObject は、アプリケーションの実行時を通して移動できません。</span><span class="sxs-lookup"><span data-stu-id="ec6de-229">GameObjects marked as *Static* cannot be moved throughout your application's runtime.</span></span> <span data-ttu-id="ec6de-230">そのため、事実上すべてのオブジェクトの配置、移動、スケーリングなどを行う必要がある HoloLens では、静的バッチ処理を利用することが困難な場合があります。イマーシブ ヘッドセットの場合、静的バッチ処理によって描画呼び出しが大幅に減少し、パフォーマンスが向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-230">Thus, static batching can be difficult to leverage on HoloLens where virtually every object needs to be placed, moved, scaled, etc. For immersive headsets, static batching can dramatically reduce draw calls and thus improve performance.</span></span>

<span data-ttu-id="ec6de-231">詳細については、[Unity の描画呼び出しのバッチ処理](https://docs.unity3d.com/Manual/DrawCallBatching.html)に関する記事の「*静的バッチ処理*」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec6de-231">Read *Static Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for more details.</span></span>

#### <a name="dynamic-batching"></a><span data-ttu-id="ec6de-232">動的バッチ処理</span><span class="sxs-lookup"><span data-stu-id="ec6de-232">Dynamic batching</span></span>

<span data-ttu-id="ec6de-233">HoloLens の開発では *Static* としてオブジェクトをマークすることには問題であるため、動的バッチ処理が、この機能がないことを補う優れたツールになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-233">Since it is problematic to mark objects as *Static* for HoloLens development, dynamic batching can be a great tool to compensate for this lacking feature.</span></span> <span data-ttu-id="ec6de-234">もちろん、イマーシブ ヘッドセットにも役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-234">Of course, it can also be useful on immersive headsets, as well.</span></span> <span data-ttu-id="ec6de-235">ただし、GameObject が **a) 同じ素材を共有し**、**b) それ以外の条件の長い一覧を満たす**必要があるため、Unity で動的バッチ処理を有効にすることは難しい場合があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-235">However, dynamic batching in Unity can be difficult to enable because GameObjects must **a) share the same Material** and **b) meet a long list of other criteria**.</span></span>

<span data-ttu-id="ec6de-236">詳細については、[Unity の描画呼び出しのバッチ処理](https://docs.unity3d.com/Manual/DrawCallBatching.html)に関する記事の「*動的バッチ処理*」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec6de-236">Read *Dynamic Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for the full list.</span></span> <span data-ttu-id="ec6de-237">ほとんどの場合、関連付けられたメッシュ データは 300 個より多くの頂点を持つことができないため、GameObject は動的バッチ処理が無効になります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-237">Most commonly, GameObjects become invalid to be batched dynamically, because the associated mesh data can be no more than 300 vertices.</span></span>

#### <a name="other-techniques"></a><span data-ttu-id="ec6de-238">その他の手法</span><span class="sxs-lookup"><span data-stu-id="ec6de-238">Other techniques</span></span>

<span data-ttu-id="ec6de-239">バッチ処理は、複数の GameObject が同じ素材を共有できる場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-239">Batching can only occur if multiple GameObjects are able to share the same material.</span></span> <span data-ttu-id="ec6de-240">通常、これは、GameObject ではそれぞれの素材に対して固有のテクスチャを持つ必要があるため妨げられます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-240">Typically, this will be blocked by the need for GameObjects to have a unique texture for their respective Material.</span></span> <span data-ttu-id="ec6de-241">複数のテクスチャを 1 つの大きなテクスチャに結合するのが一般的であり、これは[テクスチャ アトラシング](https://en.wikipedia.org/wiki/Texture_atlas)と呼ばれる手法です。</span><span class="sxs-lookup"><span data-stu-id="ec6de-241">It is common to combine Textures into one big Texture, a method known as [Texture Atlasing](https://en.wikipedia.org/wiki/Texture_atlas).</span></span>

<span data-ttu-id="ec6de-242">さらに、一般に、可能かつ妥当であれば、複数のメッシュを 1 つの GameObject に結合することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ec6de-242">Furthermore, it is generally preferable to combine meshes into one GameObject where possible and reasonable.</span></span> <span data-ttu-id="ec6de-243">Unity では、各レンダラーには関連する描画呼び出しがあり、結合されたメッシュは 1 つのレンダラーで送信されます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-243">Each Renderer in Unity will have its associated draw call(s) versus submitting a combined mesh under one Renderer.</span></span>

>[!NOTE]
> <span data-ttu-id="ec6de-244">実行時に Renderer.material のプロパティを変更すると、素材のコピーが作成されるため、バッチ処理が損なわれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-244">Modifying properties of Renderer.material at runtime will create a copy of the Material and thus potentially break batching.</span></span> <span data-ttu-id="ec6de-245">GameObject 間で共有される素材のプロパティを変更するには、Renderer.sharedMaterial を使用します。</span><span class="sxs-lookup"><span data-stu-id="ec6de-245">Use Renderer.sharedMaterial to modify shared material properties across GameObjects.</span></span>

## <a name="gpu-performance-recommendations"></a><span data-ttu-id="ec6de-246">GPU のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="ec6de-246">GPU performance recommendations</span></span>

<span data-ttu-id="ec6de-247">詳細については、[Unity でのグラフィックス レンダリングの最適化](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)に関する記事を参照してください</span><span class="sxs-lookup"><span data-stu-id="ec6de-247">Learn more about [optimizing graphics rendering in Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)</span></span>

### <a name="optimize-depth-buffer-sharing"></a><span data-ttu-id="ec6de-248">深度バッファーの共有を最適化する</span><span class="sxs-lookup"><span data-stu-id="ec6de-248">Optimize depth buffer sharing</span></span>

<span data-ttu-id="ec6de-249">一般に、[ホログラム安定性](Hologram-stability.md)に対して最適化するには、 **[Player XR Settings]\(プレーヤー XR 設定\)** の **[Depth buffer sharing]\(深度バッファー共有\)** を有効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ec6de-249">It is generally recommended to enable **Depth buffer sharing** under **Player XR Settings** to optimize for [hologram stability](Hologram-stability.md).</span></span> <span data-ttu-id="ec6de-250">ただし、この設定を使用して深度ベースの遅延ステージ再投影を有効にする場合は、**24 ビット深度形式**ではなく、**16 ビット深度形式**を選択することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ec6de-250">When enabling depth-based late-stage reprojection with this setting however, it is recommended to select **16-bit depth format** instead of **24-bit depth format**.</span></span> <span data-ttu-id="ec6de-251">16 ビット深度バッファーを使用すると、深度バッファー トラフィックに関連付けられた帯域幅 (したがって電力) が大幅に減少します。</span><span class="sxs-lookup"><span data-stu-id="ec6de-251">The 16-bit depth buffers will drastically reduce the bandwidth (and thus power) associated with depth buffer traffic.</span></span> <span data-ttu-id="ec6de-252">これは、電力の削減とパフォーマンスの向上の両方に大きなメリットがあります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-252">This can be a big win both in power reduction and performance improvement.</span></span> <span data-ttu-id="ec6de-253">ただし、"*16 ビット深度形式*" を使用すると、2 つの悪影響が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-253">However, there are two possible negative outcomes by using *16-bit depth format*.</span></span>

<span data-ttu-id="ec6de-254">**Z ファイティング**</span><span class="sxs-lookup"><span data-stu-id="ec6de-254">**Z-Fighting**</span></span>

<span data-ttu-id="ec6de-255">深度範囲の忠実性を低くすると、24 ビットより 16 ビットの方が [Z ファイティング](https://en.wikipedia.org/wiki/Z-fighting)が発生しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-255">The reduced depth range fidelity makes [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) more likely to occur with 16-bit than 24-bit.</span></span> <span data-ttu-id="ec6de-256">これらのアーティファクトを回避するには、[Unity カメラ](https://docs.unity3d.com/Manual/class-Camera.html)のニア/ファー クリップ プレーンを変更して、低い精度に対応します。</span><span class="sxs-lookup"><span data-stu-id="ec6de-256">To avoid these artifacts, modify the near/far clip planes of the [Unity camera](https://docs.unity3d.com/Manual/class-Camera.html) to account for the lower precision.</span></span> <span data-ttu-id="ec6de-257">HoloLens ベースのアプリケーションでは、Unity の既定の1000 m ではなく、50 m のファー クリップ プレーンにすることで、一般に Z ファイティングを除去できます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-257">For HoloLens-based applications, a far clip plane of 50m instead of the Unity default 1000m can generally eliminate any z-fighting.</span></span>

<span data-ttu-id="ec6de-258">**ステンシル バッファーの無効化**</span><span class="sxs-lookup"><span data-stu-id="ec6de-258">**Disabled Stencil Buffer**</span></span>

<span data-ttu-id="ec6de-259">Unity で [16 ビット深度のレンダリング テクスチャ](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html)が作成されるときは、ステンシル バッファーは作成されません。</span><span class="sxs-lookup"><span data-stu-id="ec6de-259">When Unity creates a [Render Texture with 16-bit depth](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html), there is no stencil buffer created.</span></span> <span data-ttu-id="ec6de-260">Unity のドキュメントによると、24 ビット深度形式を選択した場合は、24 ビットの z バッファーと共に [8 ビットのステンシル バッファー](https://docs.unity3d.com/Manual/SL-Stencil.html) が作成されます (デバイスで 32 ビットが適用されている場合。HoloLens などではこれが一般的です)。</span><span class="sxs-lookup"><span data-stu-id="ec6de-260">Selecting 24-bit depth format, per Unity documentation, will create a 24-bit z-buffer, as well as an [8-bit stencil buffer] (https://docs.unity3d.com/Manual/SL-Stencil.html) (if 32-bit is applicable on a device, which is generally the case such as HoloLens).</span></span>

### <a name="avoid-full-screen-effects"></a><span data-ttu-id="ec6de-261">全画面効果を避ける</span><span class="sxs-lookup"><span data-stu-id="ec6de-261">Avoid full-screen effects</span></span>

<span data-ttu-id="ec6de-262">全画面に対して動作する手法は、すべてのフレームで数百万の操作が行われるため、非常にコストが高くなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-262">Techniques that operate on the full screen can be quite expensive since their order of magnitude is millions of operations every frame.</span></span> <span data-ttu-id="ec6de-263">したがって、アンチエイリアシングやブルームなどの[後処理効果](https://docs.unity3d.com/Manual/PostProcessingOverview.html)を回避することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ec6de-263">Thus, it is recommended to avoid [post-processing effects](https://docs.unity3d.com/Manual/PostProcessingOverview.html) such as anti-aliasing, bloom, and more.</span></span>

### <a name="optimal-lighting-settings"></a><span data-ttu-id="ec6de-264">最適な照明設定</span><span class="sxs-lookup"><span data-stu-id="ec6de-264">Optimal lighting settings</span></span>

<span data-ttu-id="ec6de-265">Unity で[リアルタイム全体照明](https://docs.unity3d.com/Manual/GIIntro.html)を使用すると、極めて優れたビジュアル結果を得ることができますが、非常に高コストの照明計算が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-265">[Real-time Global Illumination](https://docs.unity3d.com/Manual/GIIntro.html) in Unity can provide outstanding visual results but involves quite expensive lighting calculations.</span></span> <span data-ttu-id="ec6de-266">**[Window]\(ウィンドウ\)**  >  **[Rendering]\(レンダリング\)**  >  **[Lighting Settings]\(証明設定\)** で **[Real-time Global Illumination]\(リアルタイム全体照明\)** をオフにすることで、すべての Unity シーン ファイルでリアルタイム全体照明を無効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ec6de-266">It is recommended to disable Realtime Global Illumination for every Unity scene file via **Window** > **Rendering** > **Lighting Settings** > Uncheck **Real-time Global Illumination**.</span></span>

<span data-ttu-id="ec6de-267">また、シャドウ キャストも、Unity シーンに高コストの GPU パスが追加されるため、すべて無効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ec6de-267">Furthermore, it is recommended to disable all shadow casting as these also add expensive GPU passes onto a Unity scene.</span></span> <span data-ttu-id="ec6de-268">シャドウはライトごとに無効にできますが、品質設定を使用することでまとめて制御することもできます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-268">Shadows can be disable per light but can also be controlled holistically via Quality settings.</span></span>

<span data-ttu-id="ec6de-269">**[Edit]\(編集\)**  >  **[Project Settings]\(プロジェクト設定\)** で **[Quality]\(品質\)** カテゴリを選択し、UWP プラットフォームに対して **[Low Quality]\(低品質\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ec6de-269">**Edit** > **Project Settings**, then select the **Quality** category > Select **Low Quality** for the UWP Platform.</span></span> <span data-ttu-id="ec6de-270">また、 **[Shadows]\(シャドウ\)** プロパティを **[Disable Shadows]\(シャドウを無効にする\)** に設定するだけでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="ec6de-270">One can also just set the **Shadows** property to **Disable Shadows**.</span></span>

### <a name="reduce-poly-count"></a><span data-ttu-id="ec6de-271">多角形の数を減らす</span><span class="sxs-lookup"><span data-stu-id="ec6de-271">Reduce poly count</span></span>

<span data-ttu-id="ec6de-272">通常、多角形の数は次のようにすると減ります</span><span class="sxs-lookup"><span data-stu-id="ec6de-272">Polygon count is usually reduced by either</span></span>
1) <span data-ttu-id="ec6de-273">シーンからのオブジェクトの削除</span><span class="sxs-lookup"><span data-stu-id="ec6de-273">Removing objects from a scene</span></span>
2) <span data-ttu-id="ec6de-274">特定のメッシュに対する多角形の数が減る資産の間引き</span><span class="sxs-lookup"><span data-stu-id="ec6de-274">Asset decimation which reduces the number of polygons for a given mesh</span></span>
3) <span data-ttu-id="ec6de-275">遠く離れたオブジェクトが同じジオメトリのローポリ バージョンでレンダリングされる[詳細度 (LOD) システム](https://docs.unity3d.com/Manual/LevelOfDetail.html)のアプリケーションへの実装</span><span class="sxs-lookup"><span data-stu-id="ec6de-275">Implementing a [Level of Detail (LOD) System](https://docs.unity3d.com/Manual/LevelOfDetail.html) into your application which renders far away objects with lower-polygon version of the same geometry</span></span>

### <a name="understanding-shaders-in-unity"></a><span data-ttu-id="ec6de-276">Unity でのシェーダーについて</span><span class="sxs-lookup"><span data-stu-id="ec6de-276">Understanding shaders in Unity</span></span>

<span data-ttu-id="ec6de-277">パフォーマンスでのシェーダーの比較を近似する簡単な方法は、実行時に各操作が実行される平均操作数を特定することです。</span><span class="sxs-lookup"><span data-stu-id="ec6de-277">An easy approximation to compare shaders in performance is to identify the average number of operations each executes at runtime.</span></span> <span data-ttu-id="ec6de-278">Unity ではこれを簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-278">This can be done easily in Unity.</span></span>

1) <span data-ttu-id="ec6de-279">シェーダー資産をまたは素材を選択した後、インスペクター ウィンドウの右上隅にある歯車アイコンを選択して、 **[Select Shader]\(シェーダーの選択\)** を選択します</span><span class="sxs-lookup"><span data-stu-id="ec6de-279">Select your shader asset or select a material, then in the top right corner of the inspector window, select the gear icon followed by **"Select Shader"**</span></span>

    ![Unity でシェーダーを選択する](images/Select-shader-unity.png)
2) <span data-ttu-id="ec6de-281">シェーダー資産を選択した状態で、インスペクター ウィンドウの下の **[Compile and show code]\(コードのコンパイルと表示\)** ボタンをクリックします</span><span class="sxs-lookup"><span data-stu-id="ec6de-281">With the shader asset selected, click the **"Compile and show code"** button under the inspector window</span></span>

    ![Unity でシェーダー コードをコンパイルする](images/compile-shader-code-unity.PNG)

3) <span data-ttu-id="ec6de-283">コンパイル後、頂点シェーダーとピクセル シェーダーの両方について、異なる操作の数に関する結果の統計セクションを確認します (注: ピクセル シェーダーはフラグメント シェーダーとも呼ばれます)</span><span class="sxs-lookup"><span data-stu-id="ec6de-283">After compiling, look for the statistics section in the results with the number of different operations for both the vertex and pixel shader (Note: pixel shaders are often also called fragment shaders)</span></span>

    ![Unity での標準シェーダー操作](images/unity-standard-shader-compilation.png)

#### <a name="optimize-pixel-shaders"></a><span data-ttu-id="ec6de-285">ピクセル シェーダーを最適化する</span><span class="sxs-lookup"><span data-stu-id="ec6de-285">Optimize pixel shaders</span></span>

<span data-ttu-id="ec6de-286">上記の方法を使用してコンパイル済みの統計結果を調べると、平均して[フラグメント シェーダー](https://en.wikipedia.org/wiki/Shader#Pixel_shaders)では一般に[頂点シェーダー](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)より多くの操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-286">Looking at the compiled statistic results using the method above, the [fragment shader](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) will generally execute more operations than the [vertex shader](https://en.wikipedia.org/wiki/Shader#Vertex_shaders), on average.</span></span> <span data-ttu-id="ec6de-287">ピクセル シェーダーとも呼ばれるフラグメント シェーダーは、画面出力のピクセルごとに実行されます。一方、頂点シェーダーは、画面に描画されるすべてのメッシュの頂点ごとにだけ実行されます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-287">The fragment shader, also known as the pixel shader, is executed per pixel on the screen output while the vertex shader is only executed per-vertex of all meshes being drawn to the screen.</span></span> 

<span data-ttu-id="ec6de-288">したがって、すべての照明計算のために、フラグメント シェーダーには頂点シェーダーより多くの命令があるだけでなく、ほとんどの場合、フラグメント シェーダーは大きなデータセットに対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-288">Thus, not only do fragment shaders have more instructions than vertex shaders because of all the lighting calculations, fragment shaders are almost always executed on a larger dataset.</span></span> <span data-ttu-id="ec6de-289">たとえば、画面出力が 2k x 2k の画像の場合、フラグメント シェーダーは 2,000 \* 2,000 = 400 万回実行される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-289">For example, if the screen output is a 2k by 2k image, then the fragment shader can get executed 2,000\*2,000 = 4,000,000 times.</span></span> <span data-ttu-id="ec6de-290">2 つの視線をレンダリングする場合、2 つの画面があるため、この数は 2 倍になります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-290">If rendering two eyes, this number doubles since there are two screens.</span></span> <span data-ttu-id="ec6de-291">複合現実アプリケーションに複数のパス、全画面の後処理効果、または同じピクセルへの複数のメッシュのレンダリングがある場合は、この数が大幅に増加します。</span><span class="sxs-lookup"><span data-stu-id="ec6de-291">If a mixed reality application has multiple passes, full-screen post-processing effects, or rendering multiple meshes to the same pixel, this number will increase dramatically.</span></span> 

<span data-ttu-id="ec6de-292">したがって、フラグメント シェーダー内の操作の数を減らすと、通常、頂点シェーダーでの最適化より、はるかに大幅にパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="ec6de-292">Therefore, reducing the number of operations in the fragment shader can generally give far greater performance gains over optimizations in the vertex shader.</span></span>

#### <a name="unity-standard-shader-alternatives"></a><span data-ttu-id="ec6de-293">Unity 標準シェーダーの代替手段</span><span class="sxs-lookup"><span data-stu-id="ec6de-293">Unity Standard shader alternatives</span></span>

<span data-ttu-id="ec6de-294">物理ベースのレンダリング (PBR) や他の高品質シェーダーを使用する代わりに、より高パフォーマンスで低コストのシェーダーを利用することを検討します。</span><span class="sxs-lookup"><span data-stu-id="ec6de-294">Instead of using a physically based rendering (PBR) or another high-quality shader, look at utilizing a more performant and cheaper shader.</span></span> <span data-ttu-id="ec6de-295">[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) では、複合現実プロジェクト用に最適化された [MRTK 標準シェーダー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)が提供されています。</span><span class="sxs-lookup"><span data-stu-id="ec6de-295">The [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides the [MRTK standard shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) that has been optimized for mixed reality projects.</span></span>

<span data-ttu-id="ec6de-296">Unity では、unlit、vertex lit、および Unity 標準シェーダーより大幅に高速の他の単純化されたシェーダー オプションも提供されています。</span><span class="sxs-lookup"><span data-stu-id="ec6de-296">Unity also provides an unlit, vertex lit, diffuse, and other simplified shader options that are significantly faster compared to the Unity Standard shader.</span></span> <span data-ttu-id="ec6de-297">詳細については、「[組み込みシェーダーの使用とパフォーマンス](https://docs.unity3d.com/Manual/shader-Performance.html)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec6de-297">See [Usage and Performance of Built-in Shaders](https://docs.unity3d.com/Manual/shader-Performance.html) for more detailed information.</span></span>

#### <a name="shader-preloading"></a><span data-ttu-id="ec6de-298">シェーダーのプリロード</span><span class="sxs-lookup"><span data-stu-id="ec6de-298">Shader preloading</span></span>

<span data-ttu-id="ec6de-299">[シェーダーの読み込み時間](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html)を最適化するには、*シェーダーのプリロード*や他のテクニックを使用します。</span><span class="sxs-lookup"><span data-stu-id="ec6de-299">Use *Shader preloading* and other tricks to optimize [shader load time](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html).</span></span> <span data-ttu-id="ec6de-300">特に、シェーダーのプリロードは、シェーダーの実行時コンパイルによる遅延が発生しないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="ec6de-300">In particular, shader preloading means you won't see any hitches due to runtime shader compilation.</span></span>

### <a name="limit-overdraw"></a><span data-ttu-id="ec6de-301">オーバードローを制限する</span><span class="sxs-lookup"><span data-stu-id="ec6de-301">Limit overdraw</span></span>

<span data-ttu-id="ec6de-302">Unity では、**シーン ビュー**の左上隅にある[**描画モード メニュー**](https://docs.unity3d.com/Manual/ViewModes.html)を切り替えて **[Overdraw]\(オーバードロー\)** を選択することにより、シーンのオーバードローを表示できます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-302">In Unity, one can display overdraw for their scene, by toggling the [**draw mode menu**](https://docs.unity3d.com/Manual/ViewModes.html) in the top-left corner of the **Scene view** and selecting **Overdraw**.</span></span>

<span data-ttu-id="ec6de-303">一般に、GPU に送られる前にオブジェクトを事前にカリングすることで、オーバードローを軽減できます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-303">Generally, overdraw can be mitigated by culling objects ahead of time before they are sent to the GPU.</span></span> <span data-ttu-id="ec6de-304">Unity では、エンジンに[オクルージョン カリング](https://docs.unity3d.com/Manual/OcclusionCulling.html)を実装する詳しい方法が提供されています。</span><span class="sxs-lookup"><span data-stu-id="ec6de-304">Unity provides details on implementing [Occlusion Culling](https://docs.unity3d.com/Manual/OcclusionCulling.html) for their engine.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="ec6de-305">メモリに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="ec6de-305">Memory recommendations</span></span>

<span data-ttu-id="ec6de-306">過剰なメモリ割り当て操作と割り当て解除操作により、ホログラフィック アプリケーションに悪影響があり、その結果、一定しないパフォーマンス、フレームの凍結、その他の有害な動作が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-306">Excessive memory allocation & deallocation operations can have adverse effects on your holographic application, resulting in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="ec6de-307">メモリ管理はガベージ コレクターによって制御されるため、Unity で開発するときは、メモリに関する考慮事項を理解することが特に重要です。</span><span class="sxs-lookup"><span data-stu-id="ec6de-307">It is especially important to understand memory considerations when developing in Unity since memory management is controlled by the garbage collector.</span></span>

#### <a name="garbage-collection"></a><span data-ttu-id="ec6de-308">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="ec6de-308">Garbage collection</span></span>

<span data-ttu-id="ec6de-309">ホログラフィック アプリでは、ガベージ コレクター (GC) がアクティブ化されて、実行中にスコープ外になったオブジェクトを分析し、そのメモリを解放して再利用できるようにする必要がある場合、GC のために処理計算時間が失われます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-309">Holographic apps will lose processing compute time to the garbage collector (GC) when the GC is activated to analyze objects that are no longer in scope during execution and their memory needs to be released, so it can be made available for re-use.</span></span> <span data-ttu-id="ec6de-310">通常、継続的に割り当てと割り当て解除を行うと、より頻繁にガベージ コレクターを実行する必要があるため、パフォーマンスとユーザー エクスペリエンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="ec6de-310">Constant allocations and de-allocations will generally require the garbage collector to run more frequently, thus hurting performance and user experience.</span></span>

<span data-ttu-id="ec6de-311">Unity では、ガベージ コレクターの詳細なしくみと、メモリ管理に関してより効率的なコードを記述するためのヒントが説明された、優れたページが提供されています。</span><span class="sxs-lookup"><span data-stu-id="ec6de-311">Unity has provided an excellent page that explains in detail how the garbage collector works and tips to write more efficient code in regards to memory management.</span></span>
- [<span data-ttu-id="ec6de-312">Unity ゲームでのガベージ コレクションの最適化</span><span class="sxs-lookup"><span data-stu-id="ec6de-312">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

<span data-ttu-id="ec6de-313">ガベージ コレクションが過剰になる最も一般的な状況の 1 つは、Unity の開発においてコンポーネントとクラスへの参照をキャッシュしないことです。</span><span class="sxs-lookup"><span data-stu-id="ec6de-313">One of the most common practices that leads to excessive garbage collection is not caching references to components and classes in Unity development.</span></span> <span data-ttu-id="ec6de-314">Start() または Awake() の間にすべての参照をキャプチャし、後の Update() や LateUpdate() などの関数で再利用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-314">Any references should be captured during Start() or Awake() and re-used in later functions such as Update() or LateUpdate().</span></span>

<span data-ttu-id="ec6de-315">その他のクイックヒント:</span><span class="sxs-lookup"><span data-stu-id="ec6de-315">Other quick tips:</span></span>
- <span data-ttu-id="ec6de-316">C# の [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) クラスを使用して、実行時に複雑な文字列を動的に構築します</span><span class="sxs-lookup"><span data-stu-id="ec6de-316">Use the [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# class to dynamically build complex strings at runtime</span></span>
- <span data-ttu-id="ec6de-317">アプリのすべてのビルド バージョンで実行されるため、Debug.Log() の呼び出しは不要になったら削除します</span><span class="sxs-lookup"><span data-stu-id="ec6de-317">Remove calls to Debug.Log() when no longer needed, as they still execute in all build versions of an app</span></span>
- <span data-ttu-id="ec6de-318">ホログラフィック アプリで一般に多くのメモリが必要な場合は、読み込み中や移行中の画面を表示するときなど、読み込みフェーズの間に、[ _**System.GC.Collect()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) を呼び出すことを検討します</span><span class="sxs-lookup"><span data-stu-id="ec6de-318">If your holographic app generally requires lots of memory, consider calling  [_**System.GC.Collect()**_](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) during loading phases such as when presenting a loading or transition screen</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="ec6de-319">オブジェクト プーリング</span><span class="sxs-lookup"><span data-stu-id="ec6de-319">Object pooling</span></span>

<span data-ttu-id="ec6de-320">オブジェクト プーリングは、オブジェクトの継続的な割り当てと割り当て解除のコストを削減するための一般的な手法です。</span><span class="sxs-lookup"><span data-stu-id="ec6de-320">Object pooling is a popular technique to reduce the cost of continuous allocations & deallocations of objects.</span></span> <span data-ttu-id="ec6de-321">これを行うには、同一のオブジェクトの大規模なプールを割り当て、時間の経過と共にオブジェクトを絶えず生成して破棄するのではなく、このプールの非アクティブで使用可能なインスタンスを再利用します。</span><span class="sxs-lookup"><span data-stu-id="ec6de-321">This is done by allocating a large pool of identical objects and re-using inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="ec6de-322">オブジェクト プールは、アプリの間の有効期間が一定ではない再使用可能なコンポーネントに最適です。</span><span class="sxs-lookup"><span data-stu-id="ec6de-322">Object pools are great for re-useable components that have variable lifetime during an app.</span></span>

- [<span data-ttu-id="ec6de-323">Unity でのオブジェクト プーリングのチュートリアル</span><span class="sxs-lookup"><span data-stu-id="ec6de-323">Object Pooling Tutorial in Unity</span></span>](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a><span data-ttu-id="ec6de-324">開始時のパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="ec6de-324">Startup performance</span></span>

<span data-ttu-id="ec6de-325">比較的小さなシーンでアプリを開始してから、 *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* を使用して残りのシーンを読み込むことを検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec6de-325">You should consider starting your app with a smaller scene, then using *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* to load the rest of the scene.</span></span> <span data-ttu-id="ec6de-326">これにより、可能な限り速くアプリを対話状態にすることができます。</span><span class="sxs-lookup"><span data-stu-id="ec6de-326">This allows your app to get to an interactive state as fast as possible.</span></span> <span data-ttu-id="ec6de-327">新しいシーンをアクティブ化するときは大きな CPU スパイクが発生する可能性があること、およびレンダリングされるコンテンツが途切れたり停止したりする場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ec6de-327">Be aware that there may be a large CPU spike while the new scene is being activated and that any rendered content might stutter or hitch.</span></span> <span data-ttu-id="ec6de-328">これを回避する方法の 1 つは、読み込まれるシーンで AsyncOperation.allowSceneActivation プロパティを "false" に設定し、シーンが読み込まれるまで待った後、画面を黒にクリアしてから、"true" に戻してシーンのアクティブ化を完了することです。</span><span class="sxs-lookup"><span data-stu-id="ec6de-328">One way to work around this is to set the AsyncOperation.allowSceneActivation property to "false" on the scene being loaded, wait for the scene to load, clear the screen to black, and then set it back to "true" to complete the scene activation.</span></span>

<span data-ttu-id="ec6de-329">開始シーンが読み込まれている間、ユーザーにはホログラフィック スプラッシュ画面が表示されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ec6de-329">Remember that while the startup scene is loading, the holographic splash screen will be displayed to the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec6de-330">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec6de-330">See also</span></span>
- [<span data-ttu-id="ec6de-331">Unity ゲームでのグラフィックス レンダリングの最適化</span><span class="sxs-lookup"><span data-stu-id="ec6de-331">Optimizing graphics rendering in Unity games</span></span>](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [<span data-ttu-id="ec6de-332">Unity ゲームでのガベージ コレクションの最適化</span><span class="sxs-lookup"><span data-stu-id="ec6de-332">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- <span data-ttu-id="ec6de-333">[物理計算のベスト プラクティス [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span><span class="sxs-lookup"><span data-stu-id="ec6de-333">[Physics Best Practices [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span></span>
- <span data-ttu-id="ec6de-334">[スクリプトの最適化 [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span><span class="sxs-lookup"><span data-stu-id="ec6de-334">[Optimizing Scripts [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span></span>
