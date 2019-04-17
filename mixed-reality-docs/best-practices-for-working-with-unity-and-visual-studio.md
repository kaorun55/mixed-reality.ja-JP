---
title: Unity と Visual Studio を使用するためのベスト プラクティス
description: ヒントし、テクニックを Unity と Visual Studio での複合現実のアプリケーションの作成のワークフローを効率化します。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 展開、unity、visual studio、HoloLens、イマーシブ ヘッドセット
ms.openlocfilehash: 80a533851b3bee0d747a90dfececbaa558c4ec1f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604106"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a><span data-ttu-id="80e7b-104">Unity と Visual Studio を使用するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="80e7b-104">Best practices for working with Unity and Visual Studio</span></span>

<span data-ttu-id="80e7b-105">Unity を使用した複合現実のアプリケーションを作成する開発者は、HoloLens や、イマーシブ ヘッドセットに展開されているアプリケーション パッケージを作成するには、Unity と Visual Studio の間で切り替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="80e7b-105">A developer creating a mixed reality application with Unity will need to switch between Unity and Visual Studio to build the application package that is deployed to HoloLens and/or an immersive headset.</span></span> <span data-ttu-id="80e7b-106">既定で Visual Studio の 2 つのインスタンスは必要な (Unity のスクリプトを変更するもの) とデバッグとデバイスに展開する 1 つを使用します。</span><span class="sxs-lookup"><span data-stu-id="80e7b-106">By default two instances of Visual Studio are required (one to modify Unity scripts and one to deploy to the device and debug).</span></span> <span data-ttu-id="80e7b-107">次の手順により、1 つの Visual Studio インスタンスを使用して開発するには、Unity プロジェクトでは、エクスポートの頻度が削減され、デバッグ エクスペリエンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="80e7b-107">The following procedure allows development using single Visual Studio instance, reduces the frequency of exporting Unity projects, and improves the debugging experience.</span></span>

## <a name="improving-iteration-time"></a><span data-ttu-id="80e7b-108">イテレーションの時間を改善</span><span class="sxs-lookup"><span data-stu-id="80e7b-108">Improving iteration time</span></span>

<span data-ttu-id="80e7b-109">Unity と Visual Studio を使用する場合は、一般的なワークフロー問題には、複数の windows の Visual Studio の開いていると継続的に反復処理するには、Visual Studio と Unity の間で切り替える必要が発生しました。</span><span class="sxs-lookup"><span data-stu-id="80e7b-109">A common workflow problem when working with Unity and Visual Studio is having multiple windows of Visual Studio open and the need to constantly switch between Visual Studio and Unity to iterate.</span></span>
1. <span data-ttu-id="80e7b-110">**Unity** - シーンを変更すると、Visual Studio ソリューションをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="80e7b-110">**Unity** - for modifying the scene and exporting a Visual Studio solution</span></span>
2. <span data-ttu-id="80e7b-111">**Visual Studio (1)** - スクリプトを変更します。</span><span class="sxs-lookup"><span data-stu-id="80e7b-111">**Visual Studio (1)** - for modifying scripts</span></span>
3. <span data-ttu-id="80e7b-112">**Visual Studio (2)** - ビルドと展開、Unity は、デバイスに Visual Studio ソリューションをエクスポートするために</span><span class="sxs-lookup"><span data-stu-id="80e7b-112">**Visual Studio (2)** - for building and deploying the Unity exported Visual Studio solution to the device</span></span>

<span data-ttu-id="80e7b-113">さいわい、Visual Studio の単一のインスタンスを効率化し、Unity から頻繁にエクスポートを削減する方法があります。</span><span class="sxs-lookup"><span data-stu-id="80e7b-113">Luckily, there's a way to streamline to a single instance of Visual Studio and cut down on frequent exports from Unity.</span></span>

<span data-ttu-id="80e7b-114">ときに[Unity からプロジェクトをエクスポートする](exporting-and-building-a-unity-visual-studio-solution.md)、確認、 **UnityC#プロジェクト**"ファイル > のビルド設定 メニューのチェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="80e7b-114">When [exporting your project from Unity](exporting-and-building-a-unity-visual-studio-solution.md), check the **Unity C# Projects** checkbox in the "File > Build Settings" menu.</span></span> <span data-ttu-id="80e7b-115">ここで、Unity からエクスポートしたプロジェクトを含むすべてのプロジェクトのC#スクリプトし、いくつかの利点があります。</span><span class="sxs-lookup"><span data-stu-id="80e7b-115">Now, the project you export from Unity includes all of your project's C# scripts and has several benefits:</span></span>
* <span data-ttu-id="80e7b-116">Visual Studio の同じインスタンスを使用して、スクリプトを記述すると、プロジェクトのビルド/展開</span><span class="sxs-lookup"><span data-stu-id="80e7b-116">Use the same instance of Visual Studio for writing scripts and building/deploying your project</span></span>
* <span data-ttu-id="80e7b-117">シーンが Unity エディターで変更されたときにのみ、Unity からのエクスポートします。再度エクスポートすることがなく、Visual Studio でしてスクリプトの内容の変更を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="80e7b-117">Export from Unity only when the scene is changed in the Unity Editor; changing the contents of scripts can be done in Visual Studio without re-exporting.</span></span>

<span data-ttu-id="80e7b-118">**UnityC#プロジェクト**有効にすると、各プログラムの 1 つだけのインスタンスを開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="80e7b-118">With **Unity C# Projects** enabled, only one instance of each program need be opened:</span></span>
1. <span data-ttu-id="80e7b-119">**Unity** - シーンを変更すると、Visual Studio ソリューションをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="80e7b-119">**Unity** - for modifying the scene and exporting a Visual Studio solution</span></span>
2. <span data-ttu-id="80e7b-120">**Visual Studio** - ビルドと展開、Unity は、デバイスに Visual Studio ソリューションをエクスポートし、スクリプトを変更します。</span><span class="sxs-lookup"><span data-stu-id="80e7b-120">**Visual Studio** - for modifying scripts then building and deploying the Unity exported Visual Studio solution to the device</span></span>

## <a name="visual-studio-tools-for-unity"></a><span data-ttu-id="80e7b-121">Visual Studio Tools for Unity</span><span class="sxs-lookup"><span data-stu-id="80e7b-121">Visual Studio Tools for Unity</span></span>

<span data-ttu-id="80e7b-122">ダウンロード[Visual Studio Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)</span><span class="sxs-lookup"><span data-stu-id="80e7b-122">Download [Visual Studio Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)</span></span>

<span data-ttu-id="80e7b-123">**Visual Studio Tools for Unity の利点があります。**</span><span class="sxs-lookup"><span data-stu-id="80e7b-123">**Benefits of Visual Studio Tools for Unity**</span></span>
* <span data-ttu-id="80e7b-124">Visual Studio から Unity エディターでの再生モードは、変数や複雑な式を評価するブレークポイントを配置することでデバッグします。</span><span class="sxs-lookup"><span data-stu-id="80e7b-124">Debug Unity in-editor play mode from Visual Studio by putting breakpoints, evaluating variables and complex expressions.</span></span>
* <span data-ttu-id="80e7b-125">Unity プロジェクト エクスプ ローラーを使用すると、Unity を表示する正確な同じ階層に、スクリプトを検索できます。</span><span class="sxs-lookup"><span data-stu-id="80e7b-125">Use the Unity Project Explorer to find your script with the exact same hierarchy that Unity displays.</span></span>
* <span data-ttu-id="80e7b-126">Visual Studio 内から直接、Unity コンソールを取得します。</span><span class="sxs-lookup"><span data-stu-id="80e7b-126">Get the Unity console directly inside Visual Studio.</span></span>
* <span data-ttu-id="80e7b-127">ウィザードを使用して、迅速に作成またはスクリプトに移動します。</span><span class="sxs-lookup"><span data-stu-id="80e7b-127">Use wizards to quickly create or navigate to scripts.</span></span>

## <a name="expose-c-class-variables-for-easy-tuning"></a><span data-ttu-id="80e7b-128">公開C#容易なチューニング用の変数をクラス</span><span class="sxs-lookup"><span data-stu-id="80e7b-128">Expose C# class variables for easy tuning</span></span>

<span data-ttu-id="80e7b-129">クラスの変数を公開する 2 つの方法はあります。</span><span class="sxs-lookup"><span data-stu-id="80e7b-129">There are two ways to expose class variables.</span></span> <span data-ttu-id="80e7b-130">推奨される方法では、プライベート変数を [SerializeField] 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="80e7b-130">The recommended way to do so is to add the [SerializeField] attribute to your private variables.</span></span> <span data-ttu-id="80e7b-131">これにより、エディターからのアクセスがないプログラムで公開することができます。</span><span class="sxs-lookup"><span data-stu-id="80e7b-131">This allows them to be accessed from the editor but not programatically exposed.</span></span>  <span data-ttu-id="80e7b-132">その他のオプションはさせるC#クラス変数を public エディター UI で公開します。</span><span class="sxs-lookup"><span data-stu-id="80e7b-132">The other option is to make C# class variables public to expose them in the editor UI.</span></span> 

<span data-ttu-id="80e7b-133">両方のアプローチを使用すれば、エディターでの再生中に変数を簡単に調整できます。</span><span class="sxs-lookup"><span data-stu-id="80e7b-133">Both approaches make it possible to easily tweak variables while playing in-editor.</span></span> <span data-ttu-id="80e7b-134">これは、チューニング操作メカニック プロパティに特に便利です。</span><span class="sxs-lookup"><span data-stu-id="80e7b-134">This is especially useful for tuning interaction mechanic properties.</span></span>

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a><span data-ttu-id="80e7b-135">Windows SDK または Unity のアップグレード後は、UWP の Visual Studio ソリューションを再生成します。</span><span class="sxs-lookup"><span data-stu-id="80e7b-135">Regenerate UWP Visual Studio solutions after Windows SDK or Unity upgrade</span></span>

<span data-ttu-id="80e7b-136">UWP の Visual Studio ソリューションをソース管理にチェックインは、新しい Windows SDK または Unity エンジンへのアップグレード後に古いで取得できます。</span><span class="sxs-lookup"><span data-stu-id="80e7b-136">UWP Visual Studio solutions checked in to source control can get out-of-date after upgrading to a new Windows SDK or Unity engine.</span></span> <span data-ttu-id="80e7b-137">アップグレード後、Unity から新しい UWP ソリューションを構築し、チェックイン済みのソリューションに相違点をマージして、これを解決できます。</span><span class="sxs-lookup"><span data-stu-id="80e7b-137">You can resolve this after the upgrade by building a new UWP solution from Unity, then merging any differences into the checked-in solution.</span></span>

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a><span data-ttu-id="80e7b-138">変更内容を比較しやすいテキスト形式の資産を使用します。</span><span class="sxs-lookup"><span data-stu-id="80e7b-138">Use text-format assets for easy comparison of content changes</span></span>

<span data-ttu-id="80e7b-139">テキスト形式でアセットを格納すると、Visual Studio での差分をコンテンツの変更を確認しやすきます。</span><span class="sxs-lookup"><span data-stu-id="80e7b-139">Storing assets in text format makes it easier to review content change diffs in Visual Studio.</span></span> <span data-ttu-id="80e7b-140">有効にするこの「> プロジェクトの設定 > エディターの編集」に変更する**資産のシリアル化**モード**Force テキスト**します。</span><span class="sxs-lookup"><span data-stu-id="80e7b-140">You can enable this in "Edit > Project Settings > Editor" by changing **Asset Serialization** mode to **Force Text**.</span></span> <span data-ttu-id="80e7b-141">ただし、資産ファイルのテキストの変更をマージすることはエラーを起こしやすいし、ソース管理システムで排他的バイナリ チェック アウトを有効にするを検討、推奨されませんのでします。</span><span class="sxs-lookup"><span data-stu-id="80e7b-141">However, merging text asset file changes is error-prone and not recommended, so consider enabling exclusive binary checkouts in your source control system.</span></span>
