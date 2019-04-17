---
title: 3D アプリ ランチャー (UWP アプリ) の実装します。
description: HoloLens と没入型の (VR) ヘッドセットの両方で 3D アプリ ランチャーと Windows Mixed Reality UWP アプリとゲーム (Microsoft Store を介して配布)、ロゴを作成する方法。
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D、ロゴ、アイコン、モデリング、ランチャー、3D ランチャー、タイル、ライブのキューブ、ディープ リンク、secondarytile、UWP、セカンダリ タイル
ms.openlocfilehash: 4a8d4a696ff6ef19d7332b20580f1f5ee67bf045
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604858"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a><span data-ttu-id="1202b-104">3D アプリ ランチャー (UWP アプリ) の実装します。</span><span class="sxs-lookup"><span data-stu-id="1202b-104">Implement 3D app launchers (UWP apps)</span></span>

> [!NOTE]
> <span data-ttu-id="1202b-105">この機能は、イマーシブ ヘッドセットの 2017 の Fall Creators Update (RS3) の一部としてが追加され、HoloLens と Windows ではサポートされて 10 April 2018 Update。</span><span class="sxs-lookup"><span data-stu-id="1202b-105">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive headsets and is supported by HoloLens with the  Windows 10 April 2018 Update.</span></span> <span data-ttu-id="1202b-106">アプリケーションには、イマーシブ ヘッドセットで 10.0.16299 以上 10.0.17125 HoloLens では、Windows SDK のバージョンが対象とすることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1202b-106">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive Headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="1202b-107">最新の Windows SDK を検索する[ここ](https://developer.microsoft.com/windows/downloads/windows-10-sdk)します。</span><span class="sxs-lookup"><span data-stu-id="1202b-107">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="1202b-108">[Windows Mixed Reality ホーム](navigating-the-windows-mixed-reality-home.md)始めるユーザーがアプリケーションを起動する前に配置する場所です。</span><span class="sxs-lookup"><span data-stu-id="1202b-108">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="1202b-109">Windows Mixed Reality の UWP アプリケーションを作成する、既定では、そのアプリのロゴで 2D スレートとしてアプリが起動されます。</span><span class="sxs-lookup"><span data-stu-id="1202b-109">When creating a UWP application for Windows Mixed Reality, by default, apps are launched as 2D slates with their app's logo.</span></span> <span data-ttu-id="1202b-110">Windows Mixed Reality のエクスペリエンスを開発する際に 3D ランチャーは、アプリケーションの既定の 2D ランチャーをオーバーライドする必要に応じて定義できます。</span><span class="sxs-lookup"><span data-stu-id="1202b-110">When developing experiences for Windows Mixed Reality, a 3D launcher can optionally be defined to override the default 2D launcher for your application.</span></span> <span data-ttu-id="1202b-111">一般に、ランチャーが 3D がインプレース アクティブ化されると、アプリは、既定の 2D ランチャーは優先のユーザーからホーム Windows Mixed Reality を取る没入型アプリケーションを起動するためお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1202b-111">In general, 3D launchers are recommended for launching immersive applications that take users out of the Windows Mixed Reality home whereas the default 2D launcher is preferred when the app is activated in place.</span></span> <span data-ttu-id="1202b-112">作成することも、 [3D ディープ リンク (secondaryTile)](#3d-deep-links-secondarytiles) 2D の UWP アプリ内のコンテンツへの 3D ランチャーとして。</span><span class="sxs-lookup"><span data-stu-id="1202b-112">You can also create a [3D deep link (secondaryTile)](#3d-deep-links-secondarytiles) as a 3D launcher to content within a 2D UWP app.</span></span>

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="1202b-113">3D アプリ起動ツールの作成プロセス</span><span class="sxs-lookup"><span data-stu-id="1202b-113">3D app launcher creation process</span></span>

<span data-ttu-id="1202b-114">3D アプリ起動ツールを作成する 3 つの手順があります。</span><span class="sxs-lookup"><span data-stu-id="1202b-114">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="1202b-115">デザインと concepting</span><span class="sxs-lookup"><span data-stu-id="1202b-115">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="1202b-116">モデリングとエクスポート</span><span class="sxs-lookup"><span data-stu-id="1202b-116">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="1202b-117">(この記事)、アプリケーションに統合します。</span><span class="sxs-lookup"><span data-stu-id="1202b-117">Integrating it into your application (this article)</span></span>

<span data-ttu-id="1202b-118">3D アセットを使用して、アプリケーションの起動ツールを作成する必要がありますとして使用する、[ガイドラインの authoring Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)互換性を確保します。</span><span class="sxs-lookup"><span data-stu-id="1202b-118">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="1202b-119">このオーサリングの仕様を満たすために失敗した資産は、ホーム Windows Mixed Reality ではレンダリングされません。</span><span class="sxs-lookup"><span data-stu-id="1202b-119">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="1202b-120">3D の起動ツールを構成します。</span><span class="sxs-lookup"><span data-stu-id="1202b-120">Configuring the 3D launcher</span></span>

<span data-ttu-id="1202b-121">Visual Studio で新しいプロジェクトを作成すると、アプリの名前とロゴを表示する単純な既定のタイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1202b-121">When you create a new project in Visual Studio, it creates a simple default tile that displays your app's name and logo.</span></span> <span data-ttu-id="1202b-122">この 2D を置き換えるには、カスタムの 3D モデルで表現は、"MixedRealityModel"要素を既定のタイルの定義の一部として含める、アプリケーションのアプリケーション マニフェストを編集します。</span><span class="sxs-lookup"><span data-stu-id="1202b-122">To replace this 2D representation with a custom 3D model edit the app manifest of your application to include the “MixedRealityModel” element as part of your default tile definition.</span></span> <span data-ttu-id="1202b-123">だけランチャーは 2D に戻すには、マニフェストから MixedRealityModel 定義を削除します。</span><span class="sxs-lookup"><span data-stu-id="1202b-123">To revert to the 2D launcher just remove the MixedRealityModel definition from the manifest.</span></span>

### <a name="xml"></a><span data-ttu-id="1202b-124">XML</span><span class="sxs-lookup"><span data-stu-id="1202b-124">XML</span></span>

<span data-ttu-id="1202b-125">最初に、現在のプロジェクトで、アプリ パッケージのマニフェストを見つけます。</span><span class="sxs-lookup"><span data-stu-id="1202b-125">First, locate the app package manifest in your current project.</span></span> <span data-ttu-id="1202b-126">既定では、マニフェストの Package.appxmanifest を名前されるは。</span><span class="sxs-lookup"><span data-stu-id="1202b-126">By default, the manifest will be named Package.appxmanifest.</span></span> <span data-ttu-id="1202b-127">Visual Studio を使用している場合は、ソリューション エクスプ ローラーで、マニフェストを右クリックし、選択**ソースの表示**を編集するための xml を開きます。</span><span class="sxs-lookup"><span data-stu-id="1202b-127">If you're using Visual Studio, then right-click the manifest in your solution viewer and select **View source** to open the xml for editing.</span></span> 

<span data-ttu-id="1202b-128">マニフェストの上部にある uap5 スキーマを追加し、無視できる名前空間として含めます。</span><span class="sxs-lookup"><span data-stu-id="1202b-128">At the top of the manifest, add the uap5 schema and include it as an ignorable namespace:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

<span data-ttu-id="1202b-129">次に、アプリケーションの既定のタイルに"MixedRealityModel"を指定します。</span><span class="sxs-lookup"><span data-stu-id="1202b-129">Next specify the "MixedRealityModel" in the default tile for your application:</span></span>

```xml
<Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="ExampleApp.App">
      <uap:VisualElements
        DisplayName="ExampleApp"
        Square150x150Logo="Assets\Logo.png"
        Square44x44Logo="Assets\SmallLogo.png"
        Description="ExampleApp"
        BackgroundColor="#464646">
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb" />
        </uap:DefaultTile>
        <uap:SplashScreen Image="Assets\SplashScreen.png" />
      </uap:VisualElements>
    </Application>
</Applications>
```

<span data-ttu-id="1202b-130">MixedRealityModel 要素は、アプリ パッケージに格納されている 3D 資産へのファイル パスを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="1202b-130">The MixedRealityModel elements accepts a file path pointing to a 3D asset stored in your app package.</span></span> <span data-ttu-id="1202b-131">のみの 3D モデルが現在 .glb ファイル形式を使用して配信され、に対して作成される、 [Windows Mixed Reality 3D アセットの作成手順については](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)はサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1202b-131">Currently only 3D models delivered using the .glb file format and authored against the [Windows Mixed Reality 3D asset authoring instructions](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) are supported.</span></span> <span data-ttu-id="1202b-132">資産は、アプリ パッケージに格納する必要があり、アニメーションが現在サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="1202b-132">Assets must be stored in the app package and animation is not currently supported.</span></span> <span data-ttu-id="1202b-133">"Path"パラメーターが空白の場合、Windows は 3D ランチャーではなく 2D スレートを表示します。</span><span class="sxs-lookup"><span data-stu-id="1202b-133">If the “Path” parameter is left blank Windows will show the 2D slate instead of the 3D launcher.</span></span> <span data-ttu-id="1202b-134">**注:** .glb 資産としてマークされる必要「コンテンツ」のビルド設定でのビルドと、アプリを実行する前にします。</span><span class="sxs-lookup"><span data-stu-id="1202b-134">**Note:** the .glb asset must be marked as "Content" in your build settings before building and running your app.</span></span>


<span data-ttu-id="1202b-135">![ソリューション エクスプ ローラーで、.glb を選択し、[プロパティ] セクションを使用して、ビルド設定で"Content"としてマーク](images/buildsetting-content-300px.png)</span><span class="sxs-lookup"><span data-stu-id="1202b-135">![Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings](images/buildsetting-content-300px.png)</span></span><br>
<span data-ttu-id="1202b-136">*ソリューション エクスプ ローラーで、.glb を選択し、[プロパティ] セクションを使用して、ビルド設定で"Content"としてマーク*</span><span class="sxs-lookup"><span data-stu-id="1202b-136">*Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings*</span></span>

### <a name="bounding-box"></a><span data-ttu-id="1202b-137">境界ボックス</span><span class="sxs-lookup"><span data-stu-id="1202b-137">Bounding box</span></span>

<span data-ttu-id="1202b-138">必要に応じて、オブジェクトの周囲の追加のバッファー領域を追加する、境界ボックスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="1202b-138">A bounding box can be used to optionally add an additional buffer region around the object.</span></span> <span data-ttu-id="1202b-139">境界ボックスは、中心点と、境界ボックスの中央から各軸に沿った端までの距離を示すエクステントを使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="1202b-139">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="1202b-140">境界ボックスのユニットを 1 ユニットにマップすることができます = 1 メートルです。</span><span class="sxs-lookup"><span data-stu-id="1202b-140">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="1202b-141">境界ボックスが指定されていない場合、1 つは自動的に格納オブジェクトのメッシュに。</span><span class="sxs-lookup"><span data-stu-id="1202b-141">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="1202b-142">指定された境界ボックスは、モデルよりも小さい場合は、メッシュに合わせてに変更されます。</span><span class="sxs-lookup"><span data-stu-id="1202b-142">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

<span data-ttu-id="1202b-143">境界ボックスの属性のサポートが付属 RS4 の Windows 更新プログラムをプロパティとして MixedRealityModel 要素。</span><span class="sxs-lookup"><span data-stu-id="1202b-143">Support for the bounding box attribute will come with the Windows RS4 update as a property on the MixedRealityModel element.</span></span> <span data-ttu-id="1202b-144">最初に、アプリの上部にある境界ボックスを定義するマニフェストが uap6 スキーマを追加し、そのを含める無視できない名前空間として。</span><span class="sxs-lookup"><span data-stu-id="1202b-144">To define a bounding box first at the top of the app manifest add the uap6 schema and include it them as ignorable namespaces:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
<span data-ttu-id="1202b-145">次に、MixedRealityModel 上には、境界ボックスを定義する SpatialBoundingBox プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="1202b-145">Next, on the MixedRealityModel set the SpatialBoundingBox property to define the bounding box:</span></span> 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a><span data-ttu-id="1202b-146">Unity を使用します。</span><span class="sxs-lookup"><span data-stu-id="1202b-146">Using Unity</span></span>

<span data-ttu-id="1202b-147">Unity を使用する場合、プロジェクトのビルドし、アプリケーション マニフェストを編集する前に、Visual Studio で開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="1202b-147">When working with Unity the project must be built and opened in Visual Studio before the App Manifest can be edited.</span></span> 

>[!NOTE]
><span data-ttu-id="1202b-148">3D の起動ツールは、ビルド、および Unity からの新しい Visual Studio ソリューションを展開するときに、マニフェストで再定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1202b-148">The 3D launcher must be redefined in the manifest when building and deploying a new Visual Studio solution from Unity.</span></span>

## <a name="3d-deep-links-secondarytiles"></a><span data-ttu-id="1202b-149">3D のディープ リンク (secondaryTiles)</span><span class="sxs-lookup"><span data-stu-id="1202b-149">3D deep links (secondaryTiles)</span></span>

> [!NOTE]
> <span data-ttu-id="1202b-150">(VR) のイマーシブ ヘッドセットの 2017 の Fall Creators Update (RS3) の一部として、2018 年 4 月の一部として、この機能は追加された HoloLens 用の更新プログラム (RS4)。</span><span class="sxs-lookup"><span data-stu-id="1202b-150">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive (VR) headsets and as part of the April 2018 Update (RS4) for HoloLens.</span></span> <span data-ttu-id="1202b-151">アプリケーションが (VR) のイマーシブ ヘッドセットで 10.0.16299 以上 10.0.17125 HoloLens での Windows SDK のバージョンを対象とすることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1202b-151">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive (VR) headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="1202b-152">最新の Windows SDK を検索する[ここ](https://developer.microsoft.com/windows/downloads/windows-10-sdk)します。</span><span class="sxs-lookup"><span data-stu-id="1202b-152">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

>[!IMPORTANT]
><span data-ttu-id="1202b-153">3D のディープ リンク (secondaryTiles) は、2 D の UWP アプリでのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="1202b-153">3D deep links (secondaryTiles) only work with 2D UWP apps.</span></span> <span data-ttu-id="1202b-154">ただし、作成することができます、 [3D アプリ起動ツール](implementing-3d-app-launchers.md)ホーム Windows Mixed Reality から排他のアプリを起動します。</span><span class="sxs-lookup"><span data-stu-id="1202b-154">You can, however, create a [3D app launcher](implementing-3d-app-launchers.md) to launch an exclusive app from the Windows Mixed Reality home.</span></span>

<span data-ttu-id="1202b-155">アプリからの 3D モデルを配置する機能を追加することによって Windows Mixed Reality を 2D アプリケーションを強化できる、 [Windows Mixed Reality ホーム](navigating-the-windows-mixed-reality-home.md)2D アプリ内のコンテンツにディープ リンクとしてと同じように[2D セカンダリタイル](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles)Windows [スタート] メニュー。</span><span class="sxs-lookup"><span data-stu-id="1202b-155">Your 2D applications can be enhanced for Windows Mixed Reality by adding the ability to place 3D models from your app into the [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) as deep links to content within your 2D app, just like [2D secondary tiles](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) on the Windows Start menu.</span></span> <span data-ttu-id="1202b-156">たとえば、360 ° のフォト ビューアー アプリに直接リンクまたはユーザーが作成者についての詳細ページに表示された資産のコレクションから 3D コンテンツを配置できるようにする 360 ° photospheres を作成できます。</span><span class="sxs-lookup"><span data-stu-id="1202b-156">For example, you can create 360° photospheres that link directly into a 360° photo viewer app, or let users place 3D content from a collection of assets that opens a details page about the author.</span></span> <span data-ttu-id="1202b-157">これらは、3 D コンテンツを使用して 2D のアプリケーションの機能を拡張する、いくつかの方法です。</span><span class="sxs-lookup"><span data-stu-id="1202b-157">These are just a couple ways to expand the functionality of your 2D application with 3D content.</span></span>

### <a name="creating-a-3d-secondarytile"></a><span data-ttu-id="1202b-158">3D"secondaryTile"を作成します。</span><span class="sxs-lookup"><span data-stu-id="1202b-158">Creating a 3D “secondaryTile”</span></span>

<span data-ttu-id="1202b-159">作成時に、複合現実のモデルを定義することで"secondaryTiles"を使用して、アプリケーションからは、3 D コンテンツを配置できます。</span><span class="sxs-lookup"><span data-stu-id="1202b-159">You can place 3D content from your application using “secondaryTiles” by defining a mixed reality model at creation time.</span></span> <span data-ttu-id="1202b-160">複合現実のモデルは、アプリ パッケージ内の 3D アセットを参照して、必要に応じて境界ボックスを定義して作成されます。</span><span class="sxs-lookup"><span data-stu-id="1202b-160">Mixed reality models are created by referencing a 3D asset in your app package and optionally defining a bounding box.</span></span> 

> [!NOTE]
> <span data-ttu-id="1202b-161">排他のビュー内からの"secondaryTiles"の作成は現在サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="1202b-161">Creating “secondaryTiles” from within an exclusive view is not currently supported.</span></span>

```cs
using Windows.UI.StartScreen;
using Windows.Foundation.Numerics;
using Windows.Perception.Spatial;

// Initialize the tile
SecondaryTile tile = new SecondaryTile("myTileId")
{
    DisplayName = "My Tile",
    Arguments = "myArgs"
};

tile.VisualElements.Square150x150Logo = new Uri("ms-appx:///Assets/MyTile/Square150x150Logo.png");

//Assign 3D model (only ms-appx and ms-appdata are allowed)
TileMixedRealityModel model = tile.VisualElements.MixedRealityModel;
model.Uri = new Uri("ms-appx:///Assets/MyTile/MixedRealityModel.glb");
model.ActivationBehavior = TileMixedRealityModelActivationBehavior.Default;
model.BoundingBox = new SpatialBoundingBox
{
    Center = new Vector3 { X = 1, Y = 0, Z = 0 },
    Extents = new Vector3 { X = 3, Y = 5, Z = 4 }
};

// And place it
await tile.RequestCreateAsync();
```

### <a name="bounding-box"></a><span data-ttu-id="1202b-162">境界ボックス</span><span class="sxs-lookup"><span data-stu-id="1202b-162">Bounding box</span></span>

<span data-ttu-id="1202b-163">オブジェクトの周囲、追加のバッファー領域を追加するのには、境界ボックスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="1202b-163">A bounding box can be used to add an additional buffer region around the object.</span></span> <span data-ttu-id="1202b-164">境界ボックスは、中心点と、境界ボックスの中央から各軸に沿った端までの距離を示すエクステントを使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="1202b-164">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="1202b-165">境界ボックスのユニットを 1 ユニットにマップすることができます = 1 メートルです。</span><span class="sxs-lookup"><span data-stu-id="1202b-165">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="1202b-166">境界ボックスが指定されていない場合、1 つは自動的に格納オブジェクトのメッシュに。</span><span class="sxs-lookup"><span data-stu-id="1202b-166">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="1202b-167">指定された境界ボックスは、モデルよりも小さい場合は、メッシュに合わせてに変更されます。</span><span class="sxs-lookup"><span data-stu-id="1202b-167">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="1202b-168">アクティブ化の動作</span><span class="sxs-lookup"><span data-stu-id="1202b-168">Activation behavior</span></span>

> [!NOTE]
> <span data-ttu-id="1202b-169">この機能はサポートされている Windows RS4 更新の時点でします。</span><span class="sxs-lookup"><span data-stu-id="1202b-169">This feature will be supported as of the Windows RS4 update.</span></span> <span data-ttu-id="1202b-170">この機能を使用する場合、アプリケーションは 10.0.17125 以上の Windows SDK のバージョンを対象とするかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="1202b-170">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.17125 if you plan to use this feature</span></span>

<span data-ttu-id="1202b-171">ユーザーに選択するときの反応を制御する 3D secondaryTile のアクティブ化の動作を定義できます。</span><span class="sxs-lookup"><span data-stu-id="1202b-171">You can define the activation behavior for a 3D secondaryTile to control how it reacts when a user selects it.</span></span> <span data-ttu-id="1202b-172">これは、複合現実でホーム purley 有益または装飾用である 3D オブジェクトを配置に使用できます。</span><span class="sxs-lookup"><span data-stu-id="1202b-172">This can be used to place 3D objects in the Mixed Reality home that are purley informative or decorative.</span></span> <span data-ttu-id="1202b-173">次のライセンス認証の動作の種類がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1202b-173">The following activation behavior types are supported:</span></span>
1. <span data-ttu-id="1202b-174">既定:アプリがアクティブにユーザーが 3D の secondaryTile を選択</span><span class="sxs-lookup"><span data-stu-id="1202b-174">Default: When a user selects the 3D secondaryTile the app is activated</span></span>
2. <span data-ttu-id="1202b-175">None:ユーザーが何も起こりません 3D secondaryTile とアプリを選択すると、アクティブ化されません。</span><span class="sxs-lookup"><span data-stu-id="1202b-175">None: When the users selects the 3D secondaryTile nothing happens and the app is not activated.</span></span>

### <a name="obtaining-and-updating-an-existing-secondarytile"></a><span data-ttu-id="1202b-176">取得して、既存の"secondaryTile"を更新しています</span><span class="sxs-lookup"><span data-stu-id="1202b-176">Obtaining and updating an existing “secondaryTile”</span></span>

<span data-ttu-id="1202b-177">開発者は、バックアップ以前に指定するプロパティが含まれる、既存のセカンダリ タイルの一覧を取得できます。</span><span class="sxs-lookup"><span data-stu-id="1202b-177">Developers can get back a list of their existing secondary tiles, which includes the properties that they previously specified.</span></span> <span data-ttu-id="1202b-178">値を変更して、UpdateAsync() を呼び出すことによって、プロパティを更新することもできます。</span><span class="sxs-lookup"><span data-stu-id="1202b-178">They can also update the properties by changing the value and then calling UpdateAsync().</span></span>

```cs
// Grab the existing secondary tile
SecondaryTile tile = (await SecondaryTile.FindAllAsync()).First();

Uri updatedUri = new Uri("ms-appdata:///local/MixedRealityUpdated.glb");

// See if the model needs updating
if (!tile.VisualElements.MixedRealityModel.Uri.Equals(updatedUri))
{
    // Update it
    tile.VisualElements.MixedRealityModel.Uri = updatedUri;

    // And apply the changes
    await tile.UpdateAsync();
}
```

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a><span data-ttu-id="1202b-179">ユーザーが、Windows Mixed Reality をチェックします。</span><span class="sxs-lookup"><span data-stu-id="1202b-179">Checking that the user is in Windows Mixed Reality</span></span>

<span data-ttu-id="1202b-180">3D のディープ リンク (secondaryTiles) は、ビューは、Windows Mixed Reality ヘッドセットで表示されているときにのみ作成できます。</span><span class="sxs-lookup"><span data-stu-id="1202b-180">3D deep links (secondaryTiles) can only be created while the view is being displayed in a Windows Mixed Reality headset.</span></span> <span data-ttu-id="1202b-181">Windows Mixed Reality ヘッドセットされていないビューに表示されている場合は、エントリ ポイントを非表示か、エラー メッセージを表示してこれを適切に処理をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1202b-181">When your view isn't being presented in a Windows Mixed Reality headset we recommend gracefully handling this by either hiding the entry point or showing an error message.</span></span> <span data-ttu-id="1202b-182">これを確認するにはクエリを実行して[IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)します。</span><span class="sxs-lookup"><span data-stu-id="1202b-182">You can check this by querying [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span></span>

## <a name="tile-notifications"></a><span data-ttu-id="1202b-183">タイル通知</span><span class="sxs-lookup"><span data-stu-id="1202b-183">Tile notifications</span></span>

<span data-ttu-id="1202b-184">現在、タイル通知が 3D アセットの更新を送信するサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="1202b-184">Tile notifications do not currently support sending an update with a 3D asset.</span></span> <span data-ttu-id="1202b-185">つまり、開発者は、以下を実行できません。</span><span class="sxs-lookup"><span data-stu-id="1202b-185">This means that developers will not be able to do the following</span></span>
* <span data-ttu-id="1202b-186">プッシュ通知</span><span class="sxs-lookup"><span data-stu-id="1202b-186">Push Notifications</span></span>
* <span data-ttu-id="1202b-187">定期的なポーリング</span><span class="sxs-lookup"><span data-stu-id="1202b-187">Periodic Polling</span></span>
* <span data-ttu-id="1202b-188">スケジュールされた通知</span><span class="sxs-lookup"><span data-stu-id="1202b-188">Scheduled Notifications</span></span>

<span data-ttu-id="1202b-189">詳細については、他のタイルの機能と、属性とその 2D のタイルの使用方法を参照してください。、[ドキュメントについては UWP アプリのタイル](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles)します。</span><span class="sxs-lookup"><span data-stu-id="1202b-189">For more information on the other tiles features and attributes and how they are used for 2D tiles refer to the [Tiles for UWP Apps documentation](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span></span>

## <a name="see-also"></a><span data-ttu-id="1202b-190">関連項目</span><span class="sxs-lookup"><span data-stu-id="1202b-190">See also</span></span>

* <span data-ttu-id="1202b-191">[複合現実モデル サンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)3D アプリ ランチャーを格納しています。</span><span class="sxs-lookup"><span data-stu-id="1202b-191">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="1202b-192">3D アプリ起動ツールの設計ガイダンス</span><span class="sxs-lookup"><span data-stu-id="1202b-192">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="1202b-193">Windows Mixed Reality 自宅で使用するための 3D モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="1202b-193">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="1202b-194">3D アプリ ランチャー (Win32 アプリ) を実装します。</span><span class="sxs-lookup"><span data-stu-id="1202b-194">Implementing 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
* [<span data-ttu-id="1202b-195">Windows Mixed Reality ホームに移動します。</span><span class="sxs-lookup"><span data-stu-id="1202b-195">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
