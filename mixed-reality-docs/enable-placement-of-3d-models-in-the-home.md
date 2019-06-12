---
title: 自宅での 3D モデルの配置を有効にします。
description: Windows Mixed Reality ホームで、web サイトまたはアプリケーションからの 3D モデルを配置する方法
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D、モデル、自宅内の場所、場所、world、モデリング、複合現実のホーム、web、アプリ
ms.openlocfilehash: 954086b79e3614e1b75ceb7560f9fc87435530fa
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829732"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a><span data-ttu-id="a741c-104">ホーム複合現実での 3D モデルの配置を有効にします。</span><span class="sxs-lookup"><span data-stu-id="a741c-104">Enable placement of 3D models in the mixed reality home</span></span>

> [!NOTE]
> <span data-ttu-id="a741c-105">この機能は、の一部として追加された、 [Windows 10 April 2018 Update](release-notes-april-2018.md)します。</span><span class="sxs-lookup"><span data-stu-id="a741c-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md).</span></span> <span data-ttu-id="a741c-106">Windows の以前のバージョンは、この機能と互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="a741c-106">Older versions of Windows are not compatible with this feature.</span></span>

<span data-ttu-id="a741c-107">[Windows Mixed Reality ホーム](navigating-the-windows-mixed-reality-home.md)始めるユーザーがアプリケーションを起動する前に配置する場所です。</span><span class="sxs-lookup"><span data-stu-id="a741c-107">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="a741c-108">一部のシナリオでは、(ホログラム アプリ) のような 2D アプリは、装飾、またはフル 3D でさらなる調査用に 3D モデルの複合現実ホームに直接配置を有効にします。</span><span class="sxs-lookup"><span data-stu-id="a741c-108">In some scenarios, 2D apps (like the Holograms app) enable placement of 3D models directly into the mixed reality home as decorations or for further inspection in full 3D.</span></span> <span data-ttu-id="a741c-109">*モデル プロトコルを追加*3D モデルを web サイトや自宅、Windows Mixed Reality に直接アプリケーションから送信するために保持されますがなど[3D アプリ ランチャー](3d-app-launcher-design-guidance.md)、2D のアプリ、およびホログラム。</span><span class="sxs-lookup"><span data-stu-id="a741c-109">The *add model protocol* allows you to send a 3D model from your website or application directly into the Windows Mixed Reality home, where it will persist like [3D app launchers](3d-app-launcher-design-guidance.md), 2D apps, and holograms.</span></span> 

<span data-ttu-id="a741c-110">たとえば、3 D の家具、領域をデザインするためのカタログを表示するアプリケーションを開発している場合、ことができますを使用する、*モデル プロトコルを追加*カタログからこれらの家具を 3D モデルを配置するユーザーを許可します。</span><span class="sxs-lookup"><span data-stu-id="a741c-110">For example, if you're developing an application that surfaces a catalog of 3D furniture for designing a space, you can use the *add model protocol* to allow users to place those 3D furniture models from the catalog.</span></span> <span data-ttu-id="a741c-111">ユーザーが移動できる、世界では、配置し、サイズを変更すると、自宅で他のホログラムと同じようにこれらの 3D モデルを削除します。</span><span class="sxs-lookup"><span data-stu-id="a741c-111">Once placed in the world, users can move, resize, and remove these 3D models just like other holograms in the home.</span></span> <span data-ttu-id="a741c-112">この記事では実装の概要、*モデル プロトコルを追加*アプリまたは web から 3D オブジェクトは、自分の世界を修飾するためのユーザーの有効化を開始できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a741c-112">This article provides an overview of implementing the *add model protocol* so that you can start enabling users to decorate their world with 3D objects from your app or the web.</span></span>

## <a name="device-support"></a><span data-ttu-id="a741c-113">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="a741c-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a741c-114"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="a741c-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="a741c-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="a741c-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="a741c-116"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="a741c-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a741c-117">モデルのプロトコルを追加します。</span><span class="sxs-lookup"><span data-stu-id="a741c-117">Add model protocol</span></span></td>
        <td><span data-ttu-id="a741c-118">✔️</span><span class="sxs-lookup"><span data-stu-id="a741c-118">✔️</span></span></td>
        <td><span data-ttu-id="a741c-119">✔️</span><span class="sxs-lookup"><span data-stu-id="a741c-119">✔️</span></span></td>
    </tr>
</table>

## <a name="overview"></a><span data-ttu-id="a741c-120">概要</span><span class="sxs-lookup"><span data-stu-id="a741c-120">Overview</span></span>

<span data-ttu-id="a741c-121">Windows Mixed Reality ホームの 3D モデルの配置を有効にする 2 つの手順があります。</span><span class="sxs-lookup"><span data-stu-id="a741c-121">There are 2 steps to enabling the placement of 3D models in the Windows Mixed Reality home:</span></span>
1. <span data-ttu-id="a741c-122">[3D モデルが Windows Mixed Reality ホームと互換性のあることを確認して](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)します。</span><span class="sxs-lookup"><span data-stu-id="a741c-122">[Ensure your 3D model is compatible with the Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span></span>
2. <span data-ttu-id="a741c-123">実装、*モデル プロトコルを追加*アプリケーションまたは web ページ (この記事)。</span><span class="sxs-lookup"><span data-stu-id="a741c-123">Implement the *add model protocol* in your application or webpage (this article).</span></span>

## <a name="implementing-the-add-model-protocol"></a><span data-ttu-id="a741c-124">実装する、 *model プロトコルの追加*</span><span class="sxs-lookup"><span data-stu-id="a741c-124">Implementing the *add model protocol*</span></span>

<span data-ttu-id="a741c-125">作成したら、 [3D モデルを互換性のある](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)、実装することができます、*モデル プロトコルを追加*で任意の web ページまたはアプリケーションから次の URI をアクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="a741c-125">Once you have a [compatible 3D model](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), you can implement the *add model protocol* by activating the following URI from any webpage or application:</span></span>

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

<span data-ttu-id="a741c-126">URI は、リモート リソースをポイントしている場合が自動的にダウンロードされ家庭内に配置します。</span><span class="sxs-lookup"><span data-stu-id="a741c-126">If the URI points to a remote resource, then it will automatically be downloaded and placed in the home.</span></span> <span data-ttu-id="a741c-127">ローカル リソースは、家庭内に配置する前に、複合現実ホームのアプリのデータ フォルダーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="a741c-127">Local resources will be copied to the mixed reality home's app data folder before being placed in the home.</span></span> <span data-ttu-id="a741c-128">アカウントのユーザー可能性がありますが実行されている以前のバージョンの Windows ボタンを非表示または可能であれば無効にすることによってこの機能をサポートしないシナリオのエクスペリエンスを設計することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a741c-128">We recommend designing your experience to account for scenarios where the user might be running an older version of Windows that doesn't support this feature by hiding the button or disabling it if possible.</span></span> 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a><span data-ttu-id="a741c-129">呼び出す、*モデル プロトコルを追加*ユニバーサル Windows プラットフォーム アプリから。</span><span class="sxs-lookup"><span data-stu-id="a741c-129">Invoking the *add model protocol* from a Universal Windows Platform app:</span></span>

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a><span data-ttu-id="a741c-130">呼び出す、*モデル プロトコルを追加*web ページから。</span><span class="sxs-lookup"><span data-stu-id="a741c-130">Invoking the *add model protocol* from a webpage:</span></span>

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a><span data-ttu-id="a741c-131">(VR) のイマーシブ ヘッドセットに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="a741c-131">Considerations for immersive (VR) headsets</span></span>

* <span data-ttu-id="a741c-132">呼び出す前に実行されているがない混合現実ポータル没入型の (VR) ヘッドセット場合、*モデル プロトコルを追加*します。</span><span class="sxs-lookup"><span data-stu-id="a741c-132">For immersive (VR) headsets, the Mixed Reality Portal does not have to be running before invoking the *add model protocol*.</span></span> <span data-ttu-id="a741c-133">ここで、*モデル プロトコルを追加*が Mixed Reality ポータルを起動し、直接、ヘッドセットは検索ホーム複合現実で到着すると、オブジェクトします。</span><span class="sxs-lookup"><span data-stu-id="a741c-133">In this case, the *add model protocol* will launch the Mixed Reality Portal and place the object directly where the headset is looking once you arrive in the mixed reality home.</span></span> 
* <span data-ttu-id="a741c-134">呼び出すときに、*モデル プロトコルを追加*既に実行されている混合現実ポータルを使用したデスクトップで、ヘッドセットが「起動」ことを確認します。</span><span class="sxs-lookup"><span data-stu-id="a741c-134">When invoking the *add model protocol* from the desktop with the Mixed Reality Portal already running, ensure that the headset is "awake".</span></span> <span data-ttu-id="a741c-135">それ以外の場合は、配置は成功しません。</span><span class="sxs-lookup"><span data-stu-id="a741c-135">If not, the placement will not succeed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="a741c-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="a741c-136">See also</span></span>

* [<span data-ttu-id="a741c-137">Windows Mixed Reality 自宅で使用するための 3D モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="a741c-137">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="a741c-138">Windows Mixed Reality ホームのナビゲーション</span><span class="sxs-lookup"><span data-stu-id="a741c-138">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
