---
title: Unity のパフォーマンスに関する推奨事項
description: Mixed reality アプリのパフォーマンスを向上させるための Unity 固有のヒント。
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: グラフィックス、cpu、gpu、レンダリング、ガベージコレクション、hololens
ms.openlocfilehash: b0821f07184bff8630f6b6af0d0fc461f6fcd133
ms.sourcegitcommit: 8f3ff9738397d9b9fdf4703b14b89d416f0186a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2019
ms.locfileid: "67843334"
---
# <a name="performance-recommendations-for-unity"></a><span data-ttu-id="d982b-104">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="d982b-104">Performance recommendations for Unity</span></span>

<span data-ttu-id="d982b-105">この記事は、「 [mixed reality のパフォーマンスに関する推奨事項](understanding-performance-for-mixed-reality.md)」で説明されている説明に基づいていますが、Unity エンジン環境に固有の学習に重点を置いています。</span><span class="sxs-lookup"><span data-stu-id="d982b-105">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md) but focuses on learnings specific to the Unity engine environment.</span></span>

<span data-ttu-id="d982b-106">また、開発者が[Unity の推奨される環境設定](Recommended-settings-for-unity.md)を確認することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d982b-106">It is also highly advisable that developers review the [recommended environment settings for Unity article](Recommended-settings-for-unity.md).</span></span> <span data-ttu-id="d982b-107">この記事には、パフォーマンスに優れた Mixed Reality アプリの構築に関して、最も重要なシーン構成の一部が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d982b-107">This article has content with some of the most important scene configurations in regards to building performant Mixed Reality apps.</span></span> <span data-ttu-id="d982b-108">これらの推奨設定の一部も下に強調表示されています。</span><span class="sxs-lookup"><span data-stu-id="d982b-108">Some of these recommended settings are highlighted below as well.</span></span>

## <a name="how-to-profile-with-unity"></a><span data-ttu-id="d982b-109">Unity でプロファイルする方法</span><span class="sxs-lookup"><span data-stu-id="d982b-109">How to profile with Unity</span></span>

<span data-ttu-id="d982b-110">Unity には、特定のアプリの貴重なパフォーマンスの洞察を収集するための優れたリソースである **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="d982b-110">Unity provides the **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** built-in which is a great resource to gather valuable performance insights for your particular app.</span></span> <span data-ttu-id="d982b-111">エディターでプロファイラーを実行できますが、これらのメトリックは実際のランタイム環境を表すものではないため、このような結果は慎重に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d982b-111">Although one can run the profiler in-editor, these metrics do not represent the true runtime environment and thus, results from this should be used cautiously.</span></span> <span data-ttu-id="d982b-112">デバイスでの実行中に、正確で実用的な洞察を得るために、アプリケーションをリモートでプロファイリングすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d982b-112">It is recommended to remotely profile your application while running on device for most accurate and actionable insights.</span></span> <span data-ttu-id="d982b-113">さらに、Unity の[フレームデバッガー](https://docs.unity3d.com/Manual/FrameDebugger.html)は、利用するための非常に強力な洞察ツールでもあります。</span><span class="sxs-lookup"><span data-stu-id="d982b-113">Further, Unity's [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html)  is also a very powerful and insight tool to utilize.</span></span>

<span data-ttu-id="d982b-114">Unity は、次のことに関する優れたドキュメントを提供します。</span><span class="sxs-lookup"><span data-stu-id="d982b-114">Unity provides great documentation for:</span></span>
1) <span data-ttu-id="d982b-115">[Unity profiler をリモートで UWP アプリケーションに](https://docs.unity3d.com/Manual/windowsstore-profiler.html)接続する方法</span><span class="sxs-lookup"><span data-stu-id="d982b-115">How to connect the [Unity profiler to UWP applications remotely](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span></span>
2) <span data-ttu-id="d982b-116">[Unity Profiler でパフォーマンスの問題](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)を効果的に診断する方法</span><span class="sxs-lookup"><span data-stu-id="d982b-116">How to effectively [diagnose performance problems with the Unity Profiler](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span></span>

>[!NOTE]
> <span data-ttu-id="d982b-117">Unity プロファイラーが接続され、GPU プロファイラーを追加した後 (「Profiler を右上隅に*追加*する」を参照してください)、プロファイラーの途中で CPU & GPU でどのくらいの時間がかかっているかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="d982b-117">With the Unity Profiler connected and after adding the GPU profiler (see *Add Profiler* in top right corner), one can see how much time is being spent on the CPU & GPU respectively in the middle of the profiler.</span></span> <span data-ttu-id="d982b-118">これにより、開発者は、アプリケーションが CPU または GPU で制限されている場合に、簡単に近似できます。</span><span class="sxs-lookup"><span data-stu-id="d982b-118">This allows the developer to get a quick approximation if their application is CPU or GPU bounded.</span></span>
>
> ![Unity CPU と GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a><span data-ttu-id="d982b-120">CPU パフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="d982b-120">CPU performance recommendations</span></span>

<span data-ttu-id="d982b-121">以下のコンテンツでは、特に Unity & C#開発を対象とした、より詳細なパフォーマンスプラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d982b-121">The content below covers more in-depth performance practices, especially targeted for Unity & C# development.</span></span>

#### <a name="cache-references"></a><span data-ttu-id="d982b-122">キャッシュ参照</span><span class="sxs-lookup"><span data-stu-id="d982b-122">Cache references</span></span>

<span data-ttu-id="d982b-123">初期化時に、関連するすべてのコンポーネントとオブジェクトへの参照をキャッシュすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d982b-123">It is best practice to cache references to all relevant components and GameObjects at initialization.</span></span> <span data-ttu-id="d982b-124">これは、 *[getcomponent\<T > ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* などの繰り返し関数呼び出しの方が、ポインターを格納するためのメモリコストに比べてかなりコストが高くなるためです。</span><span class="sxs-lookup"><span data-stu-id="d982b-124">This is because repeating function calls such as *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* are significantly more expensive relative to the memory cost to store a pointer.</span></span> <span data-ttu-id="d982b-125">これは、非常に頻繁に使用される[カメラ](https://docs.unity3d.com/ScriptReference/Camera-main.html)にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="d982b-125">This also applies to to the very, regularly used [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).</span></span> <span data-ttu-id="d982b-126">*Camera. main は、* 実際には findexpensively を使用します。この *[タグ](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* は、 *"maincamera"* タグを持つカメラオブジェクトのシーングラフを検索します。</span><span class="sxs-lookup"><span data-stu-id="d982b-126">*Camera.main* actually just uses *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* underneath which expensively searches your scene graph for a camera object with the *"MainCamera"* tag.</span></span>

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
> <span data-ttu-id="d982b-127">GetComponent (string) を避けます。</span><span class="sxs-lookup"><span data-stu-id="d982b-127">Avoid GetComponent(string)</span></span> <br/>
> <span data-ttu-id="d982b-128">*[Getcomponent ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* を使用する場合、いくつかの異なるオーバーロードがあります。</span><span class="sxs-lookup"><span data-stu-id="d982b-128">When using *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)*, there are a handful of different overloads.</span></span> <span data-ttu-id="d982b-129">常に型ベースの実装を使用し、文字列ベースの検索オーバーロードは使用しないことが重要です。</span><span class="sxs-lookup"><span data-stu-id="d982b-129">It is important to always use the Type based implementations and never the string-based searching overload.</span></span> <span data-ttu-id="d982b-130">シーンでの文字列による検索は、型での検索よりもかなりコストがかかります。</span><span class="sxs-lookup"><span data-stu-id="d982b-130">Searching by string in your scene is significantly more costly than searching by Type.</span></span> <br/>
> <span data-ttu-id="d982b-131">正常コンポーネント GetComponent (型の型)</span><span class="sxs-lookup"><span data-stu-id="d982b-131">(Good) Component GetComponent(Type type)</span></span> <br/>
> <span data-ttu-id="d982b-132">正常T getcomponent\<t > ()</span><span class="sxs-lookup"><span data-stu-id="d982b-132">(Good) T GetComponent\<T>()</span></span> <br/>
> <span data-ttu-id="d982b-133">不良コンポーネント GetComponent (文字列) ></span><span class="sxs-lookup"><span data-stu-id="d982b-133">(Bad) Component GetComponent(string)></span></span> <br/>

#### <a name="avoid-expensive-operations"></a><span data-ttu-id="d982b-134">コストのかかる操作を避ける</span><span class="sxs-lookup"><span data-stu-id="d982b-134">Avoid expensive operations</span></span>

1) <span data-ttu-id="d982b-135">**[LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)の使用を避ける**</span><span class="sxs-lookup"><span data-stu-id="d982b-135">**Avoid use of [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span></span>

    <span data-ttu-id="d982b-136">LINQ は非常にクリーンで、読み取りと書き込みが簡単ですが、通常はアルゴリズムを手動で記述するよりもはるかに多くの計算と、特にメモリの割り当てが必要になります。</span><span class="sxs-lookup"><span data-stu-id="d982b-136">Although LINQ can be very clean and easy to read and write, it generally requires much more computation and particularly more memory allocation than writing the algorithm out manually.</span></span>

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) <span data-ttu-id="d982b-137">**共通 Unity Api**</span><span class="sxs-lookup"><span data-stu-id="d982b-137">**Common Unity APIs**</span></span>

    <span data-ttu-id="d982b-138">特定の Unity Api は便利ですが、実行するのは非常にコストがかかります。</span><span class="sxs-lookup"><span data-stu-id="d982b-138">Certain Unity APIs, although useful, can be very expensive to execute.</span></span> <span data-ttu-id="d982b-139">ほとんどの場合、シーングラフ全体を検索して、一致するオブジェクトの一覧を検索します。</span><span class="sxs-lookup"><span data-stu-id="d982b-139">Most of these involve searching your entire scene graph for some matching list of GameObjects.</span></span> <span data-ttu-id="d982b-140">これらの操作は、通常、参照をキャッシュするか、問題のあるオブジェクトのマネージャーコンポーネントを実装して実行時に参照を追跡することで回避できます。</span><span class="sxs-lookup"><span data-stu-id="d982b-140">These operations can generally be avoided by caching references or implementing a manager component for the GameObjects in question to track the references at runtime.</span></span>

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> <span data-ttu-id="d982b-141">*[SendMessage ()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* と *[BroadcastMessage ()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* は、すべてのコストで排除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d982b-141">*[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* and *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* should be eliminated at all costs.</span></span> <span data-ttu-id="d982b-142">これらの関数は、直接の関数呼び出しよりも1,000 倍の速度で実行できます。</span><span class="sxs-lookup"><span data-stu-id="d982b-142">These functions can be on the order of 1000x slower than direct function calls.</span></span>

3) <span data-ttu-id="d982b-143">**ボックス化に注意してください**</span><span class="sxs-lookup"><span data-stu-id="d982b-143">**Beware of boxing**</span></span>

    <span data-ttu-id="d982b-144">[ボックス](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing)化は、 C#言語とランタイムの中核となる概念です。</span><span class="sxs-lookup"><span data-stu-id="d982b-144">[Boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) is a core concept of the C# language and runtime.</span></span> <span data-ttu-id="d982b-145">これは、char、int、bool などの値で型指定された変数を参照型の変数にラップするプロセスです。</span><span class="sxs-lookup"><span data-stu-id="d982b-145">It is the process of wrapping value-typed variables such as char, int, bool, etc. into reference-typed variables.</span></span> <span data-ttu-id="d982b-146">値型の変数が "ボックス化" されている場合は、マネージヒープに格納されている System.object の内部にラップされます。</span><span class="sxs-lookup"><span data-stu-id="d982b-146">When a value-typed variable is "boxed", it is wrapped inside of a System.Object which is stored on the managed heap.</span></span> <span data-ttu-id="d982b-147">したがって、ガベージコレクターによって破棄される必要がある場合は、メモリが割り当てられ、最終的にはメモリが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="d982b-147">Thus, memory is allocated and eventually when disposed must be processed by the garbage collector.</span></span> <span data-ttu-id="d982b-148">これらの割り当てと割り当て解除には、パフォーマンスコストが発生します。また、多くのシナリオでは不要であるか、低コストの代替手段で簡単に置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="d982b-148">These allocations and deallocations incur a performance cost and in many scenarios are unnecessary or can be easily replaced by a less expensive alternative.</span></span>

#### <a name="repeating-code-paths"></a><span data-ttu-id="d982b-149">繰り返しコードパス</span><span class="sxs-lookup"><span data-stu-id="d982b-149">Repeating code paths</span></span>

<span data-ttu-id="d982b-150">すべての繰り返し Unity コールバック関数 (</span><span class="sxs-lookup"><span data-stu-id="d982b-150">Any repeating Unity callback functions (i.e</span></span> <span data-ttu-id="d982b-151">更新) 1 秒間に何度も実行されるか、またはフレームが非常に慎重に書き込まれる必要があります。</span><span class="sxs-lookup"><span data-stu-id="d982b-151">Update) that are executed many times per second and/or frame should be written very carefully.</span></span> <span data-ttu-id="d982b-152">ここで高価な操作を行うと、パフォーマンスに大きな影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="d982b-152">Any expensive operations here will have huge and consistent impact on performance.</span></span>

1) <span data-ttu-id="d982b-153">**空のコールバック関数**</span><span class="sxs-lookup"><span data-stu-id="d982b-153">**Empty callback functions**</span></span>

    <span data-ttu-id="d982b-154">以下のコードは、アプリケーション内に残すことができないように見えることがありますが、特にすべての Unity スクリプトがこのコードブロックで自動的に初期化するため、これらの空のコールバックは実際には非常にコストが高くなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d982b-154">Although the code below may seem innocent to leave in your application, especially since every Unity script auto-initializes with this code block, these empty callbacks can actually become very expensive.</span></span> <span data-ttu-id="d982b-155">Unity はアンマネージコードとマネージコードの境界を越えて、UnityEngine コードとアプリケーションコードの間で動作します。</span><span class="sxs-lookup"><span data-stu-id="d982b-155">Unity operates back and forth over an unmanaged/managed code boundary, between UnityEngine code and your application code.</span></span> <span data-ttu-id="d982b-156">このブリッジに対するコンテキストの切り替えは、実行するものがない場合でもかなりコストがかかります。</span><span class="sxs-lookup"><span data-stu-id="d982b-156">Context switching over this bridge is fairly expensive even if there is nothing to execute.</span></span> <span data-ttu-id="d982b-157">これは、アプリに空の Unity コールバックを持つコンポーネントを含む100のユーザーオブジェクトがある場合に特に問題になります。</span><span class="sxs-lookup"><span data-stu-id="d982b-157">This becomes especially problematic if your app has 100's of GameObjects with components that have empty repeating Unity callbacks.</span></span>

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> <span data-ttu-id="d982b-158">Update () は、このパフォーマンスの問題の最も一般的な取り組みですが、次のようなその他の反復的な Unity コールバックは、悪くない場合にも同様の問題になることがあります。FixedUpdate ()、Behaviour ()、OnPostRender "、OnPreRender ()、OnRenderImage () など。</span><span class="sxs-lookup"><span data-stu-id="d982b-158">Update() is the most common manifestation of this performance issue but other repeating Unity callbacks such as the following can be equally as bad if not worse: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc.</span></span> 

2) <span data-ttu-id="d982b-159">**フレームごとに1回実行を優先する操作**</span><span class="sxs-lookup"><span data-stu-id="d982b-159">**Operations to favor running once per frame**</span></span>

    <span data-ttu-id="d982b-160">次の Unity Api は、多くの Holographic アプリで一般的な操作です。</span><span class="sxs-lookup"><span data-stu-id="d982b-160">The following Unity APIs are common operations for many Holographic Apps.</span></span> <span data-ttu-id="d982b-161">これらの関数の結果は、常に可能であるとは限りませんが、通常は1回計算し、その結果を特定のフレームのアプリケーション全体で再利用することができます。</span><span class="sxs-lookup"><span data-stu-id="d982b-161">Although not always possible, the results from these functions can very commonly be computed once and the results re-utilized across the application for a given frame.</span></span>

    <span data-ttu-id="d982b-162">a) 一般に、1つのシーンに対して Raycast を処理する専用のシングルトンクラスまたはサービスを用意し、その後、それぞれの Raycast 操作を繰り返すのではなく、他のすべてのシーンコンポーネントで再利用することをお勧めします。成分.</span><span class="sxs-lookup"><span data-stu-id="d982b-162">a) Generally it is good practice to have a dedicated Singleton class or service to handle your gaze Raycast into the scene and then re-use this result in all other scene components, instead of making repeated and essentially identical Raycast operations by each component.</span></span> <span data-ttu-id="d982b-163">もちろん、アプリケーションによっては、異なるオリジンまたは異なる[レイヤーマスク](https://docs.unity3d.com/ScriptReference/LayerMask.html)の raycasts が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d982b-163">Of course, some applications may require raycasts from different origins or against different [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html).</span></span>

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    <span data-ttu-id="d982b-164">b) Start () または起動 () で[参照をキャッシュ](#cache-references)することで、Update () のような Unity コールバックを繰り返し実行する場合は、getcomponent () 操作を避けてください。</span><span class="sxs-lookup"><span data-stu-id="d982b-164">b) Avoid GetComponent() operations in repeated Unity callbacks like Update() by [caching references](#cache-references) in Start() or Awake()</span></span>

        UnityEngine.Object.GetComponent()

    <span data-ttu-id="d982b-165">c) 初期化時にすべてのオブジェクトをインスタンス化し、[オブジェクトプーリング](#object-pooling)を使用して、アプリケーションの実行時にユーザーオブジェクトをリサイクルして再利用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d982b-165">c) It is good practice to instantiate all objects, if possible, at initialization and use [object pooling](#object-pooling) to recycle and re-use GameObjects throughout runtime of your application</span></span>

        UnityEngine.Object.Instantiate()

3) <span data-ttu-id="d982b-166">**インターフェイスと仮想コンストラクトを避ける**</span><span class="sxs-lookup"><span data-stu-id="d982b-166">**Avoid interfaces and virtual constructs**</span></span>

    <span data-ttu-id="d982b-167">インターフェイスと直接のオブジェクトまたは呼び出し元の仮想関数を使用した関数呼び出しの呼び出しは、直接コンストラクトや直接関数呼び出しを利用するよりもはるかにコストがかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="d982b-167">Invoking function calls through interfaces vs direct objects or calling virtual functions can often times be much more expensive than utilizing direct constructs or direct function calls.</span></span> <span data-ttu-id="d982b-168">仮想関数またはインターフェイスが不要な場合は、削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d982b-168">If the virtual function or interface is unnecessary, then it should be removed.</span></span> <span data-ttu-id="d982b-169">ただし、これらのアプローチを利用すると、開発コラボレーション、コードの読みやすさ、およびコードの保守性が簡単になるため、一般に、これらの方法のパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="d982b-169">However, the performance hit for these approaches are generally worth the trade-off if utilizing them simplifies development collaboration, code readability, and code maintainability.</span></span> 

4) <span data-ttu-id="d982b-170">**構造体を値で渡さないようにする**</span><span class="sxs-lookup"><span data-stu-id="d982b-170">**Avoid passing structs by value**</span></span>

    <span data-ttu-id="d982b-171">クラスとは異なり、構造体は値型であり、関数に直接渡されると、その内容が新しく作成されたインスタンスにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="d982b-171">Unlike classes, structs are value-types and when passed directly to a function, their contents are copied into a newly created instance.</span></span> <span data-ttu-id="d982b-172">このコピーにより、CPU コストとスタックの追加メモリが追加されます。</span><span class="sxs-lookup"><span data-stu-id="d982b-172">This copy adds CPU cost as well as additional memory on the stack.</span></span> <span data-ttu-id="d982b-173">小さい構造体の場合、通常、影響は最小限に抑えられるため、許容されます。</span><span class="sxs-lookup"><span data-stu-id="d982b-173">For small structs, the effect is usually very minimal and thus acceptable.</span></span> <span data-ttu-id="d982b-174">ただし、すべてのフレームと、大きな構造体を取得する関数を繰り返し呼び出す関数の場合は、可能であれば、参照渡しで渡すように関数定義を変更します。</span><span class="sxs-lookup"><span data-stu-id="d982b-174">However, for functions repeatedly invoked every frame as well as functions taking large structs, if possible modify the function definition to pass by reference.</span></span> [<span data-ttu-id="d982b-175">詳細情報</span><span class="sxs-lookup"><span data-stu-id="d982b-175">Learn more here</span></span>](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a><span data-ttu-id="d982b-176">その他</span><span class="sxs-lookup"><span data-stu-id="d982b-176">Miscellaneous</span></span>

1) <span data-ttu-id="d982b-177">**物理**</span><span class="sxs-lookup"><span data-stu-id="d982b-177">**Physics**</span></span>

    <span data-ttu-id="d982b-178">a) 一般に、物理機能を改善する最も簡単な方法は、物理または1秒あたりの反復回数にかかる時間を制限することです。</span><span class="sxs-lookup"><span data-stu-id="d982b-178">a) Generally, easiest way to improve physics is to limit the amount of time spent on Physics or the number of iterations per second.</span></span> <span data-ttu-id="d982b-179">もちろん、これによりシミュレーションの精度が低下します。</span><span class="sxs-lookup"><span data-stu-id="d982b-179">Of course, this will reduce simulation accuracy.</span></span> <span data-ttu-id="d982b-180">Unity の[TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d982b-180">See [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) in Unity</span></span>

    <span data-ttu-id="d982b-181">b) Unity の colliders の種類には、さまざまなパフォーマンス特性があります。</span><span class="sxs-lookup"><span data-stu-id="d982b-181">b) The type of colliders in Unity have widely different performance characteristics.</span></span> <span data-ttu-id="d982b-182">次の順序では、最もパフォーマンスの高い colliders を左から右へと最もパフォーマンスの低い colliders に一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="d982b-182">The order below lists the most performant colliders to least performant colliders from left to right.</span></span> <span data-ttu-id="d982b-183">メッシュの Colliders を回避することは、プリミティブな Colliders よりはるかに高価であることを避けることが最も重要です。</span><span class="sxs-lookup"><span data-stu-id="d982b-183">It is most important to avoid Mesh Colliders which are substantially more expensive than the primitive colliders.</span></span>

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    <span data-ttu-id="d982b-184">詳細については、「 [Unity の物理ベストプラクティス](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d982b-184">See [Unity Physics Best Practices](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) for more info</span></span>

2) <span data-ttu-id="d982b-185">**動画**</span><span class="sxs-lookup"><span data-stu-id="d982b-185">**Animations**</span></span>

    <span data-ttu-id="d982b-186">アニメーターコンポーネントを無効にして、アイドル状態のアニメーションを無効にします (game オブジェクトを無効にしても効果はありません)。</span><span class="sxs-lookup"><span data-stu-id="d982b-186">Disable idle animations by disabling the Animator component (disabling the game object won't have the same effect).</span></span> <span data-ttu-id="d982b-187">ループ内にアニメーターがあるときに値を同じものに設定する設計パターンは避けてください。</span><span class="sxs-lookup"><span data-stu-id="d982b-187">Avoid design patterns where an animator sits in a loop setting a value to the same thing.</span></span> <span data-ttu-id="d982b-188">この手法にはかなりのオーバーヘッドがあり、アプリケーションに影響はありません。</span><span class="sxs-lookup"><span data-stu-id="d982b-188">There is considerable overhead for this technique, with no effect on the application.</span></span> [<span data-ttu-id="d982b-189">詳細については、こちらをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d982b-189">Learn more here.</span></span>](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) <span data-ttu-id="d982b-190">**複雑なアルゴリズム**</span><span class="sxs-lookup"><span data-stu-id="d982b-190">**Complex algorithms**</span></span>

    <span data-ttu-id="d982b-191">アプリケーションで、逆のキネマティック、パス検索などの複雑なアルゴリズムを使用している場合は、より単純なアプローチを見つけたり、パフォーマンスに関連する設定を調整したりします。</span><span class="sxs-lookup"><span data-stu-id="d982b-191">If your application is using complex algorithms such as inverse kinematics, path finding, etc, look to find a simpler approach or adjust relevant settings for their performance</span></span>

## <a name="cpu-to-gpu-performance-recommendations"></a><span data-ttu-id="d982b-192">CPU と GPU のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="d982b-192">CPU-to-GPU performance recommendations</span></span>

<span data-ttu-id="d982b-193">一般に、CPU と GPU のパフォーマンスは、グラフィックスカードに送信される**描画呼び出し**に対して行われます。</span><span class="sxs-lookup"><span data-stu-id="d982b-193">Generally, CPU-to-GPU performance comes down to the **draw calls** submitted to the graphics card.</span></span> <span data-ttu-id="d982b-194">パフォーマンスを向上させるには、描画呼び出しが戦略的に再構築 **)** 、最適な結果を得るために**b)** 必要があります。</span><span class="sxs-lookup"><span data-stu-id="d982b-194">To improve performance, draw calls need to be strategically **a) reduced** or **b) restructured** for optimal results.</span></span> <span data-ttu-id="d982b-195">描画呼び出し自体はリソースを集中的に使用するため、必要な作業全体を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="d982b-195">Since draw calls themselves are resource-intensive, reducing them will reduce overall work required.</span></span> <span data-ttu-id="d982b-196">さらに、描画呼び出し間の状態変更には、グラフィックスドライバーでのコストの高い検証と変換の手順が必要です。したがって、状態の変化を制限するためにアプリケーションの描画呼び出しを再構築する必要があります (つまり、</span><span class="sxs-lookup"><span data-stu-id="d982b-196">Further, state changes between draw calls requires costly validation and translation steps in the graphics driver and thus, restructuring of your application's draw calls to limit state changes(i.e</span></span> <span data-ttu-id="d982b-197">さまざまな素材など) によってパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="d982b-197">different materials, etc) can boost performance.</span></span>

<span data-ttu-id="d982b-198">Unity には、概要を説明し、そのプラットフォームの描画呼び出しをバッチ処理するためのダイブがあります。</span><span class="sxs-lookup"><span data-stu-id="d982b-198">Unity has a great article that gives an overview and dives into batching draw calls for their platform.</span></span>
- [<span data-ttu-id="d982b-199">Unity 描画呼び出しのバッチ処理</span><span class="sxs-lookup"><span data-stu-id="d982b-199">Unity Draw Call Batching</span></span>](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a><span data-ttu-id="d982b-200">シングルパスインスタンスレンダリング</span><span class="sxs-lookup"><span data-stu-id="d982b-200">Single pass instanced rendering</span></span>

<span data-ttu-id="d982b-201">Unity での単一パスのインスタンスレンダリングでは、各視点の描画呼び出しを1つのインスタンス化描画呼び出しに減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="d982b-201">Single Pass Instanced Rendering in Unity allows for draw calls for each eye to be reduced down to one instanced draw call.</span></span> <span data-ttu-id="d982b-202">2つの描画呼び出しの間のキャッシュの一貫性により、GPU にもパフォーマンスが向上しています。</span><span class="sxs-lookup"><span data-stu-id="d982b-202">Due to cache coherency between two draw calls, there is also some performance improvement on the GPU as well.</span></span>

<span data-ttu-id="d982b-203">Unity プロジェクトでこの機能を有効にするには</span><span class="sxs-lookup"><span data-stu-id="d982b-203">To enable this feature in your Unity Project</span></span>
1)  <span data-ttu-id="d982b-204">**プレーヤーの XR の設定**を開く ([**プロジェクト設定** > の**編集** > ] にアクセスして、**プレーヤー** > **XR 設定**を編集)</span><span class="sxs-lookup"><span data-stu-id="d982b-204">Open **Player XR Settings** (go to **Edit** > **Project Settings** > **Player** > **XR Settings**)</span></span>
2) <span data-ttu-id="d982b-205">[**ステレオレンダリングメソッド**] ドロップダウンメニューから [**シングルパスインスタンス**] を選択します ([**Virtual Reality がサポートさ**れる] チェックボックスをオンにする必要があります)</span><span class="sxs-lookup"><span data-stu-id="d982b-205">Select **Single Pass Instanced** from the **Stereo Rendering Method** drop-down menu (**Virtual Reality Supported** checkbox must be checked)</span></span>

<span data-ttu-id="d982b-206">この表示方法の詳細については、Unity から次の記事をお読みください。</span><span class="sxs-lookup"><span data-stu-id="d982b-206">Read the following articles from Unity for details with this rendering approach.</span></span>
- [<span data-ttu-id="d982b-207">高度なステレオレンダリングを使用して AR と VR のパフォーマンスを最大化する方法</span><span class="sxs-lookup"><span data-stu-id="d982b-207">How to maximize AR and VR performance with advanced stereo rendering</span></span>](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [<span data-ttu-id="d982b-208">シングルパスのインスタンス化</span><span class="sxs-lookup"><span data-stu-id="d982b-208">Single Pass Instancing</span></span>](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> <span data-ttu-id="d982b-209">単一パスのインスタンス化に関する一般的な問題の1つは、開発者が既にインスタンス化用に作成されていない既存のカスタムシェーダーを持っている場合です。</span><span class="sxs-lookup"><span data-stu-id="d982b-209">One common issue with Single Pass Instanced Rendering occurs if developers already have existing custom shaders not written for instancing.</span></span> <span data-ttu-id="d982b-210">この機能を有効にした後、開発者は、一部のオブジェクトが1つの目にしか表示されないことに気付く場合があります。</span><span class="sxs-lookup"><span data-stu-id="d982b-210">After enabling this feature, developers may notice some GameObjects only render in one eye.</span></span> <span data-ttu-id="d982b-211">これは、関連付けられたカスタムシェーダーに、インスタンス化するための適切なプロパティがないためです。</span><span class="sxs-lookup"><span data-stu-id="d982b-211">This is because the associated custom shaders do not have the appropriate properties for instancing.</span></span>
>
> <span data-ttu-id="d982b-212">この問題への対処方法については、Unity[の HoloLens のシングルパスステレオレンダリング](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d982b-212">See [Single Pass Stereo Rendering for HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) from Unity for how to address this problem</span></span>

#### <a name="static-batching"></a><span data-ttu-id="d982b-213">静的バッチ処理</span><span class="sxs-lookup"><span data-stu-id="d982b-213">Static batching</span></span>

<span data-ttu-id="d982b-214">Unity では、多くの静的オブジェクトをバッチ処理して、GPU への描画呼び出しを減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="d982b-214">Unity is able to batch many static objects to reduce draw calls to the GPU.</span></span> <span data-ttu-id="d982b-215">静的バッチ処理は、Unity では **、1) 同じ素材を共有**し、 **2) すべてが*静的*としてマークされ**ている (unity のオブジェクトを選択し、インスペクターの右上のチェックボックスをクリックする) ため、ほとんどの[レンダラー](https://docs.unity3d.com/ScriptReference/Renderer.html)オブジェクトで動作します)。</span><span class="sxs-lookup"><span data-stu-id="d982b-215">Static Batching works for most [Renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) objects in Unity that **1) share the same material** and **2) are all marked as *Static*** (Select an object in Unity and click the checkbox in the top right of the inspector).</span></span> <span data-ttu-id="d982b-216">*Static*とマークされたユーザーオブジェクトは、アプリケーションのランタイム全体で移動できません。</span><span class="sxs-lookup"><span data-stu-id="d982b-216">GameObjects marked as *Static* cannot be moved throughout your application's runtime.</span></span> <span data-ttu-id="d982b-217">そのため、事実上、すべてのオブジェクトの配置、移動、スケーリングなどを必要とする HoloLens では、静的バッチ処理を利用することが困難になります。イマーシブヘッドセットの場合、静的なバッチ処理によって描画呼び出しが大幅に減少し、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="d982b-217">Thus, static batching can be difficult to leverage on HoloLens where virtually every object needs to be placed, moved, scaled, etc. For immersive headsets, static batching can dramatically reduce draw calls and thus improve performance.</span></span>

<span data-ttu-id="d982b-218">詳細については、「 [Unity での描画呼び出しのバッチ](https://docs.unity3d.com/Manual/DrawCallBatching.html)処理」の「*静的バッチ*」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d982b-218">Read *Static Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for more details.</span></span>

#### <a name="dynamic-batching"></a><span data-ttu-id="d982b-219">動的バッチ処理</span><span class="sxs-lookup"><span data-stu-id="d982b-219">Dynamic batching</span></span>

<span data-ttu-id="d982b-220">HoloLens 開発ではオブジェクトを*静的*としてマークするのは問題なので、動的バッチ処理は、このような機能がないことを補うために優れたツールとなります。</span><span class="sxs-lookup"><span data-stu-id="d982b-220">Since it is problematic to mark objects as *Static* for HoloLens development, dynamic batching can be a great tool to compensate for this lacking feature.</span></span> <span data-ttu-id="d982b-221">もちろん、イマーシブヘッドセットにも役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="d982b-221">Of course, it is can also be useful on immersive headsets as well.</span></span> <span data-ttu-id="d982b-222">Unity で動的バッチ処理を有効にすることは困難ですが、このよう**なオブジェクトは、を**使用する必要があります) 同じ素材を共有し、 **b) 他の条件の長いリストを満たす**ことができます。</span><span class="sxs-lookup"><span data-stu-id="d982b-222">Dynamic batching in Unity can be difficult though to enable because GameObjects must **a) share the same Material** and **b) meet a long list of other criteria**.</span></span>

<span data-ttu-id="d982b-223">完全な一覧については、「 [Unity での描画呼び出しのバッチ](https://docs.unity3d.com/Manual/DrawCallBatching.html)処理」の*動的バッチ*処理を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d982b-223">Read *Dynamic Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for the full list.</span></span> <span data-ttu-id="d982b-224">一般に、関連するメッシュデータは300の頂点を超えることができないため、多くの場合、このようなオブジェクトは、動的にバッチ処理されるように無効になります。</span><span class="sxs-lookup"><span data-stu-id="d982b-224">Most commonly, GameObjects become invalid to be batched dynamically because the associated mesh data can be no more than 300 vertices.</span></span>

#### <a name="other-techniques"></a><span data-ttu-id="d982b-225">その他の方法</span><span class="sxs-lookup"><span data-stu-id="d982b-225">Other techniques</span></span>

<span data-ttu-id="d982b-226">バッチ処理は、複数のオブジェクトが同じ素材を共有できる場合にのみ発生します。</span><span class="sxs-lookup"><span data-stu-id="d982b-226">Batching can only occur if multiple GameObjects are able to share the same material.</span></span> <span data-ttu-id="d982b-227">通常、これはブロックされます。これは、作成オブジェクトがそれぞれのマテリアルに対して一意のテクスチャを持つ必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="d982b-227">Typically this will be blocked by the need for GameObjects to have a unique texture for their respective Material.</span></span> <span data-ttu-id="d982b-228">テクスチャを1つの大きなテクスチャ ([テクスチャ](https://en.wikipedia.org/wiki/Texture_atlas)の atlasing 呼ばれるメソッド) にまとめるのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="d982b-228">It is common to combine Textures into one big Texture, a method known as [Texture Atlasing](https://en.wikipedia.org/wiki/Texture_atlas).</span></span>

<span data-ttu-id="d982b-229">さらに、一般に、可能であれば、メッシュを1つのオブジェクトに結合することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d982b-229">Further, it is generally preferable to combine meshes into one GameObject where possible and reasonable.</span></span> <span data-ttu-id="d982b-230">Unity の各レンダラーには、関連付けられた描画呼び出しと、1つのレンダラーの下で結合メッシュが送信されます。</span><span class="sxs-lookup"><span data-stu-id="d982b-230">Each Renderer in Unity will have it's associated draw call(s) versus submitting a combined mesh under one Renderer.</span></span> 

>[!NOTE]
> <span data-ttu-id="d982b-231">実行時にレンダラーのプロパティを変更すると、マテリアルのコピーが作成されるため、バッチ処理が中断される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d982b-231">Modifying properties of Renderer.material at runtime will create a copy of the Material and thus potentially break batching.</span></span> <span data-ttu-id="d982b-232">オブジェクト間で共有マテリアルのプロパティを変更するには、Renderer を使用します。</span><span class="sxs-lookup"><span data-stu-id="d982b-232">Use Renderer.sharedMaterial to modify shared material properties across GameObjects.</span></span>

## <a name="gpu-performance-recommendations"></a><span data-ttu-id="d982b-233">GPU のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="d982b-233">GPU performance recommendations</span></span>

<span data-ttu-id="d982b-234">[Unity でのグラフィックスレンダリングの最適化](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)についての詳細情報</span><span class="sxs-lookup"><span data-stu-id="d982b-234">Learn more about [optimizing graphics rendering in Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)</span></span> 

### <a name="optimize-depth-buffer-sharing"></a><span data-ttu-id="d982b-235">深度バッファーの共有を最適化する</span><span class="sxs-lookup"><span data-stu-id="d982b-235">Optimize depth buffer sharing</span></span>

<span data-ttu-id="d982b-236">通常は、**プレーヤーの XR 設定**で**深度バッファーの共有**を有効にして、[ホログラムの安定性](Hologram-stability.md)を最適化することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d982b-236">It is generally recommended to enable **Depth buffer sharing** under **Player XR Settings** to optimize for [hologram stability](Hologram-stability.md).</span></span> <span data-ttu-id="d982b-237">ただし、この設定で深さベースの遅延段階の再プロジェクションを有効にする場合は、 **24 ビットの深度形式**ではなく、 **16 ビットの深さ形式**を選択することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d982b-237">When enabling depth-based late-stage reprojection with this setting however, it is recommended to select **16-bit depth format** instead of **24-bit depth format**.</span></span> <span data-ttu-id="d982b-238">16ビットの深度バッファーによって、深度バッファートラフィックに関連付けられた帯域幅 (および電力) が大幅に減少します。</span><span class="sxs-lookup"><span data-stu-id="d982b-238">The 16-bit depth buffers will drastically reduces the bandwidth (and thus power) associated with depth buffer traffic.</span></span> <span data-ttu-id="d982b-239">これは、大きな威力を得ることができますが、 [z 戦い](https://en.wikipedia.org/wiki/Z-fighting)が24ビットより16ビットで発生する可能性が高いので、わずかな深度範囲の経験にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="d982b-239">This can be a big power win, but is only applicable for experiences with a small depth range as [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) is more likely to occur with 16-bit than 24-bit.</span></span> <span data-ttu-id="d982b-240">これらの成果物を回避するには、 [Unity カメラ](https://docs.unity3d.com/Manual/class-Camera.html)の近距離/遠クリッププレーンを変更して、精度を低くします。</span><span class="sxs-lookup"><span data-stu-id="d982b-240">To avoid these artifacts, modify the near/far clip planes of the [Unity camera](https://docs.unity3d.com/Manual/class-Camera.html) to account for the lower precision.</span></span> <span data-ttu-id="d982b-241">HoloLens ベースのアプリケーションでは、Unity の既定の1000m ではなく、50m の遠くのクリッププレーンによって、一般に z 戦いを排除できます。</span><span class="sxs-lookup"><span data-stu-id="d982b-241">For HoloLens-based applications, a far clip plane of 50m instead of the Unity default 1000m can generally eliminate any z-fighting.</span></span>

### <a name="reduce-poly-count"></a><span data-ttu-id="d982b-242">Poly 数を減らす</span><span class="sxs-lookup"><span data-stu-id="d982b-242">Reduce poly count</span></span>

<span data-ttu-id="d982b-243">通常、Polygon カウントは</span><span class="sxs-lookup"><span data-stu-id="d982b-243">Polygon count is usually reduced by either</span></span>
1) <span data-ttu-id="d982b-244">シーンからのオブジェクトの削除</span><span class="sxs-lookup"><span data-stu-id="d982b-244">Removing objects from a scene</span></span>
2) <span data-ttu-id="d982b-245">指定されたメッシュの多角形の数を減らす資産の決定</span><span class="sxs-lookup"><span data-stu-id="d982b-245">Asset decimation which reduces the number of polygons for a given mesh</span></span>
3) <span data-ttu-id="d982b-246">アプリケーションに[詳細レベル (LOD) システム](https://docs.unity3d.com/Manual/LevelOfDetail.html)を実装して、同じ geometry の低いポリゴンバージョンで遠く離れたオブジェクトをレンダリングする</span><span class="sxs-lookup"><span data-stu-id="d982b-246">Implementing a [Level of Detail (LOD) System](https://docs.unity3d.com/Manual/LevelOfDetail.html) into your application which renders far away objects with lower-polygon version of the same geometry</span></span>

### <a name="understanding-shaders-in-unity"></a><span data-ttu-id="d982b-247">Unity のシェーダーについて</span><span class="sxs-lookup"><span data-stu-id="d982b-247">Understanding shaders in Unity</span></span>

<span data-ttu-id="d982b-248">シェーダーをパフォーマンスで比較するための簡単な方法は、実行時に各操作が実行される平均操作数を特定することです。</span><span class="sxs-lookup"><span data-stu-id="d982b-248">An easy approximation to compare shaders in performance is to identify the average number of operations each executes at runtime.</span></span> <span data-ttu-id="d982b-249">これは、Unity で簡単に実行できます。</span><span class="sxs-lookup"><span data-stu-id="d982b-249">This can be done easily in Unity.</span></span>

1) <span data-ttu-id="d982b-250">シェーダー資産を選択するか、素材を選択します。次に、[インスペクター] ウィンドウの右上隅にある歯車アイコンを選択し、[**シェーダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d982b-250">Select your shader asset or select a material, then in top right corner of the inspector window, select the gear icon and then **"Select Shader"**</span></span>

    ![Unity でシェーダーを選択する](images/Select-shader-unity.png)
2) <span data-ttu-id="d982b-252">シェーダー資産を選択した状態で、[インスペクター] ウィンドウの下にある [**コードのコンパイルと表示**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d982b-252">With the shader asset selected, click the **"Compile and show code"** button under the inspector window</span></span>

    ![Unity でシェーダーコードをコンパイルする](images/compile-shader-code-unity.PNG)

3) <span data-ttu-id="d982b-254">コンパイル後、頂点シェーダーとピクセルシェーダーの両方の異なる操作の数を使用して、結果の統計セクションを探します (注: ピクセルシェーダーはフラグメントシェーダーとも呼ばれます)。</span><span class="sxs-lookup"><span data-stu-id="d982b-254">After compiling, look for the statistics section in the results with the number of different operations for both the vertex and pixel shader (Note: pixel shaders are often also called fragment shaders)</span></span>

    ![Unity の標準シェーダー操作](images/unity-standard-shader-compilation.png)

#### <a name="optmize-pixel-shaders"></a><span data-ttu-id="d982b-256">ピクセルシェーダーの最適化</span><span class="sxs-lookup"><span data-stu-id="d982b-256">Optmize pixel shaders</span></span>

<span data-ttu-id="d982b-257">上記のメソッドを使用してコンパイルされた統計結果を確認すると、通常、[フラグメントシェーダー](https://en.wikipedia.org/wiki/Shader#Pixel_shaders)は[頂点シェーダー](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)よりも多くの操作を平均で実行します。</span><span class="sxs-lookup"><span data-stu-id="d982b-257">Looking at the compiled statistic results using the method above, the [fragment shader](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) will generally execute more operations than the [vertex shader](https://en.wikipedia.org/wiki/Shader#Vertex_shaders) on average.</span></span> <span data-ttu-id="d982b-258">フラグメントシェーダーは、ピクセルシェーダーとも呼ばれ、画面出力のピクセルごとに実行されます。一方、頂点シェーダーは、画面に描画されるすべてのメッシュの頂点ごとに実行されます。</span><span class="sxs-lookup"><span data-stu-id="d982b-258">The fragment shader, also known as the pixel shader, is executed per pixel on the screen output while the vertex shader is only executed per-vertex of all meshes being drawn to the screen.</span></span> 

<span data-ttu-id="d982b-259">したがって、すべての光源の計算のために、頂点シェーダーよりも多くの命令を持つフラグメントシェーダーだけでなく、ほとんどの場合、フラグメントシェーダーは大規模なデータセットで実行されます。</span><span class="sxs-lookup"><span data-stu-id="d982b-259">Thus, not only do fragment shaders have more instructions than vertex shaders because of all the lighting calculations, fragment shaders are almost always executed on a larger dataset.</span></span> <span data-ttu-id="d982b-260">たとえば、画面出力が 2k x 2k のイメージの場合、フラグメントシェーダーは 2000 \* 2000 = 400万回実行されます。</span><span class="sxs-lookup"><span data-stu-id="d982b-260">For example, if the screen output is a 2k by 2k image, then the fragment shader can get executed 2,000\*2,000 = 4,000,000 times.</span></span> <span data-ttu-id="d982b-261">2つの画面が表示される場合、2つの画面があるため、この数は2倍になります。</span><span class="sxs-lookup"><span data-stu-id="d982b-261">If rendering two eyes, this number doubles since there are two screens.</span></span> <span data-ttu-id="d982b-262">混合の現実アプリケーションに複数のパス、全画面の処理後の影響、または複数のメッシュを同じピクセルにレンダリングする場合は、この数が大幅に増加します。</span><span class="sxs-lookup"><span data-stu-id="d982b-262">If a mixed reality application has multiple passes, full-screen post-processing effects, or rendering multiple meshes to the same pixel, this number will increase dramatically.</span></span> 

<span data-ttu-id="d982b-263">そのため、フラグメントシェーダー内の操作の数を減らすと、通常、頂点シェーダーの最適化よりもはるかに高いパフォーマンスが得られます。</span><span class="sxs-lookup"><span data-stu-id="d982b-263">Therefore, reducing the number of operations in the fragment shader can generally give far greater performance gains over optimizations in the vertex shader.</span></span>

#### <a name="unity-standard-shader-alternatives"></a><span data-ttu-id="d982b-264">Unity 標準シェーダーの代替手段</span><span class="sxs-lookup"><span data-stu-id="d982b-264">Unity Standard shader alternatives</span></span>

<span data-ttu-id="d982b-265">物理的ベースのレンダリング (.PBR) やその他の高品質シェーダーを使用する代わりに、より高性能で安価なシェーダーを利用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="d982b-265">Instead of using a physically based rendering (PBR) or other high-quality shader, look at utilizing a more performant and cheaper shader.</span></span> <span data-ttu-id="d982b-266">[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)には、mixed reality プロジェクト用に最適化された[mrtk standard shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)が用意されています。</span><span class="sxs-lookup"><span data-stu-id="d982b-266">The [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides the [MRTK standard shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) that has been optimized for mixed reality projects.</span></span>

<span data-ttu-id="d982b-267">Unity では、Unity 標準シェーダーと比較して、unlit、頂点の lit、拡散、およびその他の単純化されたシェーダーオプションも提供されます。</span><span class="sxs-lookup"><span data-stu-id="d982b-267">Unity also provides an unlit, vertex lit, diffuse, and other simplified shader options that are significantly faster compared to the Unity Standard shader.</span></span> <span data-ttu-id="d982b-268">詳細については[、「組み込みシェーダーの使用状況とパフォーマンス](https://docs.unity3d.com/Manual/shader-Performance.html)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d982b-268">See [Usage and Performance of Built-in Shaders](https://docs.unity3d.com/Manual/shader-Performance.html) for more detailed information.</span></span>

#### <a name="shader-preloading"></a><span data-ttu-id="d982b-269">シェーダーのプリロード</span><span class="sxs-lookup"><span data-stu-id="d982b-269">Shader preloading</span></span>

<span data-ttu-id="d982b-270">シェーダーの[読み込み時間](http://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html)を最適化するには、*シェーダーのプリ*ロードやその他のテクニックを使用します。</span><span class="sxs-lookup"><span data-stu-id="d982b-270">Use *Shader preloading* and other tricks to optimize [shader load time](http://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html).</span></span> <span data-ttu-id="d982b-271">特に、シェーダーのプリロードは、ランタイムシェーダーのコンパイルによって hitches が表示されないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="d982b-271">In particular, shader preloading means you won't see any hitches due to runtime shader compilation.</span></span>

### <a name="limit-overdraw"></a><span data-ttu-id="d982b-272">オーバードローを制限する</span><span class="sxs-lookup"><span data-stu-id="d982b-272">Limit overdraw</span></span>

<span data-ttu-id="d982b-273">Unity では、**シーンビュー**の左上隅にある [[**描画モード] メニュー**](https://docs.unity3d.com/Manual/ViewModes.html)を切り替えて、[**オーバードロー**] を選択すると、シーンのオーバードローを表示できます。</span><span class="sxs-lookup"><span data-stu-id="d982b-273">In Unity, one can display overdraw for their scene, by toggling the [**draw mode menu**](https://docs.unity3d.com/Manual/ViewModes.html) in the top left corner of the **Scene view** and selecting **Overdraw**.</span></span>

<span data-ttu-id="d982b-274">一般に、GPU に送信される前にオブジェクトを事前にカリングすることで、オーバードローを軽減できます。</span><span class="sxs-lookup"><span data-stu-id="d982b-274">Generally, overdraw can be mitigated by culling objects ahead of time before they are sent to the GPU.</span></span> <span data-ttu-id="d982b-275">Unity は、エンジンに対して[遮蔽カリング](https://docs.unity3d.com/Manual/OcclusionCulling.html)を実装する方法について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="d982b-275">Unity provides details on implementing [Occlusion Culling](https://docs.unity3d.com/Manual/OcclusionCulling.html) for their engine.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="d982b-276">メモリに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="d982b-276">Memory recommendations</span></span>

<span data-ttu-id="d982b-277">過剰なメモリ割り当て & 解放操作によって holographic アプリケーションに悪影響を及ぼす可能性があるため、パフォーマンスが低下したり、フレームが固定されたり、その他の有害な動作が発生したりする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d982b-277">Excessive memory allocation & deallocation operations can have adverse effects on your holographic application resulting in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="d982b-278">メモリ管理はガベージコレクターによって制御されるため、Unity で開発するときは、メモリに関する考慮事項を理解することが特に重要です。</span><span class="sxs-lookup"><span data-stu-id="d982b-278">It is especially important to understand memory considerations when developing in Unity since memory management is controlled by the garbage collector.</span></span>

#### <a name="garbage-collection"></a><span data-ttu-id="d982b-279">ガベージコレクション</span><span class="sxs-lookup"><span data-stu-id="d982b-279">Garbage collection</span></span>

<span data-ttu-id="d982b-280">Holographic アプリは、GC がアクティブ化され、実行中にスコープ外になったオブジェクトを分析し、そのメモリを解放して再利用できるようにする必要がある場合、ガベージコレクター (GC) への処理時間が緩やかになります。</span><span class="sxs-lookup"><span data-stu-id="d982b-280">Holographic apps will loose processing compute time to the garbage collector (GC) when the GC is activated to analyze objects that are no longer in scope during execution and their memory needs to be released so it can be made available for re-use.</span></span> <span data-ttu-id="d982b-281">通常、一定の割り当てと割り当て解除では、ガベージコレクターの実行頻度を高くする必要があります。その結果、低下のパフォーマンスとユーザーエクスペリエンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="d982b-281">Constant allocations and de-allocations will generally require the garbage collector to run more frequently thus hurting performance and user experience.</span></span>

<span data-ttu-id="d982b-282">Unity では、ガベージコレクターのしくみを詳しく説明する優れたページと、メモリ管理に関してより効率的なコードを記述するためのヒントが提供されています。</span><span class="sxs-lookup"><span data-stu-id="d982b-282">Unity has provided an excellent page that explains in detail how the garbage collector works and tips to write more efficient code in regards to memory management.</span></span>
- [<span data-ttu-id="d982b-283">Unity ゲームでのガベージコレクションの最適化</span><span class="sxs-lookup"><span data-stu-id="d982b-283">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

<span data-ttu-id="d982b-284">ガベージコレクションが過剰になる最も一般的な方法の1つは、Unity 開発のコンポーネントおよびクラスへの参照をキャッシュしないことです。</span><span class="sxs-lookup"><span data-stu-id="d982b-284">One of the most common practices that leads to excessive garbage collection is not caching references to components and classes in Unity development.</span></span> <span data-ttu-id="d982b-285">すべての参照は、Start () または起動中 () にキャプチャし、Update () や Behaviour () などの後の関数で再利用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d982b-285">Any references should be captured during Start() or Awake() and re-used in later functions such as Update() or LateUpdate().</span></span>

<span data-ttu-id="d982b-286">その他のクイックヒント:</span><span class="sxs-lookup"><span data-stu-id="d982b-286">Other quick tips:</span></span>
- <span data-ttu-id="d982b-287">[StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C#クラスを使用して、実行時に複雑な文字列を動的に構築する</span><span class="sxs-lookup"><span data-stu-id="d982b-287">Use the [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# class to dynamically build complex strings at runtime</span></span>
- <span data-ttu-id="d982b-288">アプリケーションのすべてのビルドバージョンでまだ実行されているため、必要がなくなったときに、デバッグログ () への呼び出しを削除します。</span><span class="sxs-lookup"><span data-stu-id="d982b-288">Remove calls to Debug.Log() when no longer needed as they still execute in all build versions of an app</span></span>
- <span data-ttu-id="d982b-289">Holographic アプリで一般的に多くのメモリが必要な場合は、読み込み中または移行画面を表示するときなど、読み込みフェーズ中に、 [ _**System. GC ()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2)を呼び出すことを検討してください。</span><span class="sxs-lookup"><span data-stu-id="d982b-289">If your holographic app generally requires lots of memory, consider calling  [_**System.GC.Collect()**_](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) during loading phases such as when presenting a loading or transition screen</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="d982b-290">オブジェクトプール</span><span class="sxs-lookup"><span data-stu-id="d982b-290">Object pooling</span></span>

<span data-ttu-id="d982b-291">オブジェクトプールは、オブジェクトの割り当て解除 & の継続的な割り当てのコストを削減するための一般的な手法です。</span><span class="sxs-lookup"><span data-stu-id="d982b-291">Object pooling is a popular technique to reduce the cost of continuous allocations & deallocations of objects.</span></span> <span data-ttu-id="d982b-292">これを行うには、同一のオブジェクトの大規模なプールを割り当て、時間の経過と共にオブジェクトを絶えず破棄するのではなく、このプールから使用可能な非アクティブなインスタンスを再利用します。</span><span class="sxs-lookup"><span data-stu-id="d982b-292">This is done by allocating a large pool of identical objects and re-using inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="d982b-293">オブジェクトプールは、アプリの有効期間が可変の再使用可能なコンポーネントに最適です。</span><span class="sxs-lookup"><span data-stu-id="d982b-293">Object pools are great for re-useable components that have variable lifetime during an app.</span></span>

- [<span data-ttu-id="d982b-294">Unity でのオブジェクトプールのチュートリアル</span><span class="sxs-lookup"><span data-stu-id="d982b-294">Object Pooling Tutorial in Unity</span></span>](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a><span data-ttu-id="d982b-295">起動時のパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="d982b-295">Startup performance</span></span>

<span data-ttu-id="d982b-296">より小さなシーンでアプリを起動し、 *[SceneManager](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* を使用してシーンの残りの部分を読み込むことを検討してください。</span><span class="sxs-lookup"><span data-stu-id="d982b-296">You should consider starting your app with a smaller scene, then using *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* to load the rest of the scene.</span></span> <span data-ttu-id="d982b-297">これにより、アプリは可能な限り高速に対話型状態になることができます。</span><span class="sxs-lookup"><span data-stu-id="d982b-297">This allows your app to get to an interactive state as fast as possible.</span></span> <span data-ttu-id="d982b-298">新しいシーンをアクティブ化し、レンダリングされたコンテンツが途切れたり順調したりする可能性がある場合は、CPU のスパイクが大きくなる可能性があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d982b-298">Be aware that there may be a large CPU spike while the new scene is being activated and that any rendered content might stutter or hitch.</span></span> <span data-ttu-id="d982b-299">この問題を回避する方法の1つとして、読み込まれるシーンで allowSceneActivation プロパティを false に設定し、シーンが読み込まれるまで待機します。次に、画面を黒にオフにし、AsyncOperation を true に設定してシーンのアクティブ化を完了します。</span><span class="sxs-lookup"><span data-stu-id="d982b-299">One way to work around this is to set the AsyncOperation.allowSceneActivation property to false on the scene being loaded, wait for the scene to load, clear the screen to black, and then set back to true to complete the scene activation.</span></span>

<span data-ttu-id="d982b-300">スタートアップシーンが読み込まれている間、holographic スプラッシュ画面がユーザーに表示されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d982b-300">Remember that while the startup scene is loading the holographic splash screen will be displayed to the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="d982b-301">関連項目</span><span class="sxs-lookup"><span data-stu-id="d982b-301">See also</span></span>
- [<span data-ttu-id="d982b-302">Unity ゲームでのグラフィックスレンダリングの最適化</span><span class="sxs-lookup"><span data-stu-id="d982b-302">Optimizing graphics rendering in Unity games</span></span>](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [<span data-ttu-id="d982b-303">Unity ゲームでのガベージコレクションの最適化</span><span class="sxs-lookup"><span data-stu-id="d982b-303">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- <span data-ttu-id="d982b-304">[物理的なベストプラクティス [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span><span class="sxs-lookup"><span data-stu-id="d982b-304">[Physics Best Practices [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span></span>
- <span data-ttu-id="d982b-305">[スクリプトの最適化 [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span><span class="sxs-lookup"><span data-stu-id="d982b-305">[Optimizing Scripts [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span></span>
