---
title: 入門チュートリアル - 3. ユーザー インターフェイスの作成と Mixed Reality Toolkit の構成
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: c389c7a3d16770dcbf57d9acdcfd81c6507f7cd6
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376139"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a><span data-ttu-id="72c32-105">3.ユーザー インターフェイスの作成と Mixed Reality Toolkit の構成</span><span class="sxs-lookup"><span data-stu-id="72c32-105">3. Creating user interface and configure Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

<span data-ttu-id="72c32-106">前のチュートリアルでは、HoloLens 2 の最初のアプリケーションを開始することにより、Mixed Reality Toolkit (MRTK) で提供されている機能のいくつかを学習しました。</span><span class="sxs-lookup"><span data-stu-id="72c32-106">In the previous tutorial, you learned about some of the capabilities the Mixed Reality Toolkit (MRTK) has to offer by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="72c32-107">このチュートリアルでは、ボタンを UI テキスト パネルと共に作成して整理し、既定の対話式操作 (タッチ) を使用して各ボタンを操作する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="72c32-107">In this tutorial you will learn how to create and organize buttons along with UI text panels, and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="72c32-108">また、オブジェクトのサイズ、音、色の変更など、単純なアクションや効果の追加も調査します。</span><span class="sxs-lookup"><span data-stu-id="72c32-108">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="72c32-109">このモジュールでは、[空間マッピング](spatial-mapping.md) メッシュの可視化をオフにすることから始めて、MRTK プロファイルの変更に関する基本的な概念を紹介します。</span><span class="sxs-lookup"><span data-stu-id="72c32-109">This module will introduce basic concepts about modifying MRTK profiles, starting with turning off the [spatial mapping](spatial-mapping.md) mesh visualization.</span></span>

## <a name="objectives"></a><span data-ttu-id="72c32-110">目標</span><span class="sxs-lookup"><span data-stu-id="72c32-110">Objectives</span></span>

* <span data-ttu-id="72c32-111">Mixed Reality ツールキット プロファイルをカスタマイズおよび構成する</span><span class="sxs-lookup"><span data-stu-id="72c32-111">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="72c32-112">UI 要素とボタンを使用してホログラムを操作する</span><span class="sxs-lookup"><span data-stu-id="72c32-112">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="72c32-113">基本的な手の追跡の入力と操作</span><span class="sxs-lookup"><span data-stu-id="72c32-113">Basic hand-tracking input and interactions</span></span>

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="72c32-114">Mixed Reality Toolkit プロファイルを構成する方法 (空間認識の表示オプションの変更)</span><span class="sxs-lookup"><span data-stu-id="72c32-114">How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

<span data-ttu-id="72c32-115">このセクションでは、既定の MRTK プロファイルをカスタマイズして構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="72c32-115">In this section, you will learn how to customize and configure the default MRTK profiles.</span></span>

<span data-ttu-id="72c32-116">この特定の例では、空間メッシュ オブザーバーの設定を変更して、空間認識メッシュを非表示にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="72c32-116">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="72c32-117">ただし、次の同じ原則に従って、MRTK プロファイルのすべての設定または値をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="72c32-117">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="72c32-118">空間認識メッシュを非表示にするための主な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="72c32-118">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="72c32-119">既定の構成プロファイルを複製する</span><span class="sxs-lookup"><span data-stu-id="72c32-119">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="72c32-120">空間認識システムを有効にする</span><span class="sxs-lookup"><span data-stu-id="72c32-120">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="72c32-121">既定の空間認識システムのプロファイルを複製する</span><span class="sxs-lookup"><span data-stu-id="72c32-121">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="72c32-122">既定の空間認識メッシュ オブザーバーのプロファイルを複製する</span><span class="sxs-lookup"><span data-stu-id="72c32-122">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="72c32-123">空間認識メッシュの可視性を変更する</span><span class="sxs-lookup"><span data-stu-id="72c32-123">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="72c32-124">既定では、MRTK プロファイルは編集できません。</span><span class="sxs-lookup"><span data-stu-id="72c32-124">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="72c32-125">これらは、編集する前に複製する必要がある既定プロファイルのテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="72c32-125">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="72c32-126">入れ子になったプロファイル レイヤーがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="72c32-126">There are several nested layers of profiles.</span></span> <span data-ttu-id="72c32-127">そのため、1 つ以上の設定を構成するときは、複数のプロファイルを複製して編集するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="72c32-127">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="72c32-128">1.既定の構成プロファイルを複製する</span><span class="sxs-lookup"><span data-stu-id="72c32-128">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="72c32-129">構成プロファイルは最上位のプロファイルです。</span><span class="sxs-lookup"><span data-stu-id="72c32-129">The Configuration Profile is the top level profile.</span></span> <span data-ttu-id="72c32-130">そのため、他のプロファイルを編集できるようにするには、まず構成プロファイルを複製する必要があります。</span><span class="sxs-lookup"><span data-stu-id="72c32-130">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="72c32-131">[Hierarchy]\(階層\) ウィンドウで **MixedRealityToolkit** オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで、Mixed Reality Toolkit の**構成プロファイル**を **[DefaultHoloLens2ConfigurationProfile]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="72c32-131">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, change the Mixed Reality Toolkit **Configuration Profile** to **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

<span data-ttu-id="72c32-133">**MixedRealityToolkit** オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで **[Copy & Customize]\(コピーしてカスタマイズ\)** ボタンをクリックして、[Clone Profile]\(プロファイルの複製\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="72c32-133">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

<span data-ttu-id="72c32-135">[Clone Profile]\(プロファイルの複製\) ウィンドウで **[Clone]\(複製\)** ボタンをクリックして、**DefaultHololens2ConfigurationProfile** の編集可能なコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="72c32-135">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

<span data-ttu-id="72c32-137">新しく作成された構成プロファイルが、シーンの構成プロファイルとして割り当てられました。</span><span class="sxs-lookup"><span data-stu-id="72c32-137">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

<span data-ttu-id="72c32-139">Unity メニューで、 **[File]\(ファイル\)**  >  **[Save]\(保存\)** の順に選択してシーンを保存します。</span><span class="sxs-lookup"><span data-stu-id="72c32-139">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="72c32-140">チュートリアルの実行中は、必ず作業を保存するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="72c32-140">Remember to save your work throughout the tutorial.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="72c32-141">2.空間認識システムを有効にする</span><span class="sxs-lookup"><span data-stu-id="72c32-141">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="72c32-142">[Hierarchy]\(階層\) ウィンドウで **MixedRealityToolkit** オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで **[Spatial Awareness]\(空間認識\)** タブを選択し、次に **[Enable Spatial Awareness System]\(空間認識システムを有効にする\)** チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="72c32-142">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="72c32-144">3.既定の空間認識システムのプロファイルを複製する</span><span class="sxs-lookup"><span data-stu-id="72c32-144">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="72c32-145">**[Spatial Awareness]\(空間認識\)** タブで、 **[Clone]\(複製\)** ボタンをクリックして [Clone Profile]\(プロファイルの複製\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="72c32-145">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

<span data-ttu-id="72c32-147">[Clone Profile]\(プロファイルの複製\) ウィンドウで **[Clone]\(複製\)** ボタンをクリックして、**DefaultMixedRealitySpatialAwarenessSystemProfile** の編集可能なコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="72c32-147">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

<span data-ttu-id="72c32-149">これで、新しく作成された空間認識システム プロファイルが、構成プロファイルに自動的に割り当てられるようになりました。</span><span class="sxs-lookup"><span data-stu-id="72c32-149">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="72c32-151">4.既定の空間認識メッシュ オブザーバーのプロファイルを複製する</span><span class="sxs-lookup"><span data-stu-id="72c32-151">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="72c32-152">**[Spatial Awareness]\(空間認識\)** タブを引き続き選択した状態で、 **[Windows Mixed Reality Spatial Mesh Observer]\(Windows Mixed Reality 空間メッシュ オブザーバー\)** セクションを展開し、 **[Clone]\(複製\)** ボタンをクリックして、[Clone Profile]\(プロファイルの複製\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="72c32-152">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

<span data-ttu-id="72c32-154">[Clone Profile]\(プロファイルの複製\) ウィンドウで **[Clone]\(複製\)** ボタンをクリックして、**DefaultMixedRealitySpatialAwarenessMeshObserverProfile** の編集可能なコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="72c32-154">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

<span data-ttu-id="72c32-156">これで、新しく作成された空間認識メッシュ オブザーバーが、空間認識システム プロファイルに自動的に割り当てられるようになりました。</span><span class="sxs-lookup"><span data-stu-id="72c32-156">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="72c32-158">5.空間認識メッシュの可視性を変更する</span><span class="sxs-lookup"><span data-stu-id="72c32-158">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="72c32-159">**[Spatial Mesh Observer Settings]\(空間メッシュ オブザーバーの設定\)** で、 **[Display Option]\(表示オプション\)** を **[Occlusion]\(オクルージョン\)** に変更して、空間マッピング メッシュを、機能している状態のまま非表示にします。</span><span class="sxs-lookup"><span data-stu-id="72c32-159">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still being functional:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="72c32-161">空間マッピング メッシュは非表示になっていますが、引き続き存在して、機能しています。</span><span class="sxs-lookup"><span data-stu-id="72c32-161">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="72c32-162">たとえば、物理的な壁の後ろのホログラムなど、空間マッピング メッシュの背後にあるホログラムは表示されません。</span><span class="sxs-lookup"><span data-stu-id="72c32-162">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="72c32-163">ここまで、MRTK プロファイル内の設定を変更する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="72c32-163">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="72c32-164">ご覧のように、MRTK の設定をカスタマイズするには、最初に既定のプロファイルのコピーを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="72c32-164">As you can see, in order to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="72c32-165">既定のプロファイルは編集できないため、既定の設定に戻す場合の参照として常に保持します。</span><span class="sxs-lookup"><span data-stu-id="72c32-165">Because the default profiles are not editable, you will always have them as reference if you want revert back to the default settings.</span></span> <span data-ttu-id="72c32-166">MRTK プロファイルとそのアーキテクチャの詳細については、[MRTK ドキュメント ポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)にある「[Mixed Reality Toolkit プロファイルの構成ガイド](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="72c32-166">To learn more about MRTK profiles and their architecture, you can visit the [Mixed Reality Toolkit profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="72c32-167">ハンド トラッキングのジェスチャと対話可能なボタン</span><span class="sxs-lookup"><span data-stu-id="72c32-167">Hand tracking gestures and interactable buttons</span></span>

<span data-ttu-id="72c32-168">このセクションでは、ハンド トラッキングを使用してボタンを押し、ボタンが押されるとアクションを実行するイベントをトリガーする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="72c32-168">In this section, you will learn how to use hand tracking to press a button and trigger events to cause an action when the button is pressed.</span></span>

<span data-ttu-id="72c32-169">この特定の例では、ボタンを押すとキューブの色が変わり、ボタンを離すと元の色に戻るように変更する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="72c32-169">This particular example will show you how to change the color of a cube when the button is pressed and change it back to it's original color when the button is released.</span></span> <span data-ttu-id="72c32-170">ただし、次の同じ原則に従って他のイベントを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="72c32-170">However, you may follow these same principles to create other events.</span></span>

<span data-ttu-id="72c32-171">キューブの色を変更するための主な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="72c32-171">The main steps you will take to change the color of the cube are:</span></span>

1. <span data-ttu-id="72c32-172">押しボタンのプレハブをシーンに追加する</span><span class="sxs-lookup"><span data-stu-id="72c32-172">Add a pressable button prefab to the scene</span></span>
2. <span data-ttu-id="72c32-173">キューブをシーンに追加する</span><span class="sxs-lookup"><span data-stu-id="72c32-173">Add a cube to the scene</span></span>
3. <span data-ttu-id="72c32-174">InteractableOnPressReceiver イベントの種類を構成する</span><span class="sxs-lookup"><span data-stu-id="72c32-174">Configure the InteractableOnPressReceiver event type</span></span>
4. <span data-ttu-id="72c32-175">On Press イベントを受け取るようにキューブを構成する</span><span class="sxs-lookup"><span data-stu-id="72c32-175">Configure the cube to receive the On Press event</span></span>
5. <span data-ttu-id="72c32-176">On Press イベントによってトリガーされるアクションを定義する</span><span class="sxs-lookup"><span data-stu-id="72c32-176">Define the action to be triggered by the On Press event</span></span>
6. <span data-ttu-id="72c32-177">On Release イベントを受け取るようにキューブを構成する</span><span class="sxs-lookup"><span data-stu-id="72c32-177">Configure the cube to receive the On Release event</span></span>
7. <span data-ttu-id="72c32-178">On Release イベントによってトリガーされるアクションを定義する</span><span class="sxs-lookup"><span data-stu-id="72c32-178">Define the action to be triggered by the On Release event</span></span>
8. <span data-ttu-id="72c32-179">エディター内シミュレーションを使用してボタンをテストする</span><span class="sxs-lookup"><span data-stu-id="72c32-179">Test the button using the in-editor simulation</span></span>

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a><span data-ttu-id="72c32-180">1.押しボタンのプレハブをシーンに追加する</span><span class="sxs-lookup"><span data-stu-id="72c32-180">1. Add a pressable button prefab to the scene</span></span>

> [!TIP]
> <span data-ttu-id="72c32-181"><a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">プレハブ</a>は、Unity アセットとして格納されている事前構成済みの GameObject であり、プロジェクト全体で再利用できます。</span><span class="sxs-lookup"><span data-stu-id="72c32-181">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="72c32-182">**[Project]\(プロジェクト\) ウィンドウ**で **PressableButtonHoloLens2** を検索して、この例で使用するプレハブを見つけます。</span><span class="sxs-lookup"><span data-stu-id="72c32-182">In the **Project window**, search for **PressableButtonHoloLens2** to locate the prefab you will use for this example:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

<span data-ttu-id="72c32-184">**検索**の結果から **[PressableButtonHoloLens2]** プレハブを選択し、 **[Hierarchy]\(階層\)** ウィンドウに**ドラッグ**してシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="72c32-184">In the **Search** result, select the **PressableButtonHoloLens2** prefab and **drag** it into the **Hierarchy** window to add it to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="72c32-186">次の図に示すようにシーンを表示するには、[Hierarchy]\(階層\) ウィンドウで PressableButtonHoloLens2 オブジェクトをダブルクリックしてフォーカスを当て、[Scene]\(シーン\) ウィンドウの右上隅にある <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a> を使用して、前の Z 軸に沿うように表示角度を調整します。</span><span class="sxs-lookup"><span data-stu-id="72c32-186">To display your scene as shown in the image below, double-click the PressableButtonHoloLens2 object in the Hierarchy window to bring it into focus, then use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis.</span></span>

<span data-ttu-id="72c32-187">**PressableButtonHoloLens2** オブジェクトを引き続き選択した状態で、 **[Inspector]\(インスペクター\)** ウィンドウで次を実行します。</span><span class="sxs-lookup"><span data-stu-id="72c32-187">With the **PressableButtonHoloLens2** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="72c32-188">[Transform]\(変換\) の **[Position]\(位置\)** を、原点に位置するカメラの前に配置されるように変更します (たとえば、x = 0、y = 0、z = 0.5)。</span><span class="sxs-lookup"><span data-stu-id="72c32-188">Change its Transform **Position** so it's positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="72c32-190">一般に、Unity での位置の単位 1 は、物理的世界のほぼ 1 m に相当します。</span><span class="sxs-lookup"><span data-stu-id="72c32-190">In general, 1 position unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="72c32-191">ただし、これには、あるオブジェクトがスケーリングされたオブジェクトの子である場合などの例外があります。</span><span class="sxs-lookup"><span data-stu-id="72c32-191">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span>

### <a name="2-add-a-cube-to-the-scene"></a><span data-ttu-id="72c32-192">2.キューブをシーンに追加する</span><span class="sxs-lookup"><span data-stu-id="72c32-192">2. Add a cube to the scene</span></span>

<span data-ttu-id="72c32-193">[Hierarchy]\(階層\) ウィンドウ内の何もない場所を右クリックし、 **[3D Object]\(3D オブジェクト\)**  >  **[Cube]** の順に選択して、キューブをシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="72c32-193">Right-click on an empty spot inside the Hierarchy window and select **3D Object** > **Cube** to add a cube to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

<span data-ttu-id="72c32-195">**Cube** オブジェクトを引き続き選択した状態で、 **[Inspector]\(インスペクター\)** ウィンドウで次を実行します。</span><span class="sxs-lookup"><span data-stu-id="72c32-195">With the **Cube** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="72c32-196">押しボタンの近くになるように (ただし、重ならないように)、[Transform]\(変換\) の **[Position]\(位置\)** を変更します (たとえば、x = 0、y = 0.04、z = 0.5)。</span><span class="sxs-lookup"><span data-stu-id="72c32-196">Change its Transform **Position** so its located near the pressable button, but not overlapping with it, for example, x = 0, y = 0.04, and z = 0.5</span></span>
* <span data-ttu-id="72c32-197">[Transform]\(変換\) の **[Scale]\(スケール\)** を適切なサイズに変更します (たとえば、x = 0.02、y = 0.02、z = 0.02)。</span><span class="sxs-lookup"><span data-stu-id="72c32-197">Change its Transform **Scale** to a suitable size, for example, x = 0.02, y = 0.02, and z = 0.02</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a><span data-ttu-id="72c32-199">3.InteractableOnPressReceiver イベントの種類を構成する</span><span class="sxs-lookup"><span data-stu-id="72c32-199">3. Configure the InteractableOnPressReceiver event type</span></span>

<span data-ttu-id="72c32-200">[Hierarchy]\(階層\) ウィンドウで **PressableButtonHoloLens2** オブジェクトを選択し、次に **[Inspector]\(インスペクター\)** ウィンドウの **ハンバーガー メニュー**で **[Collapse All Components]\(すべてのコンポーネントを折りたたむ\)** を選択して、このオブジェクトのすべてのコンポーネントの概要を取得します。</span><span class="sxs-lookup"><span data-stu-id="72c32-200">In the Hierarchy window, select the **PressableButtonHoloLens2** object, then in the **Inspector** window **hamburger menu**, select **Collapse All Components** to get an overview of all components on this object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

<span data-ttu-id="72c32-202">**Interactable (Script)** コンポーネントを展開し、次に、 **[Events]\(イベント\)**  >  **[Receivers]\(レシーバー\)** セクションを見つけて展開します。</span><span class="sxs-lookup"><span data-stu-id="72c32-202">Expand the **Interactable (Script)** component, then locate and expand the **Events** > **Receivers** section:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

<span data-ttu-id="72c32-204">**[Add Event]\(イベントの追加\)** ボタンをクリックして、イベント レシーバーの種類 **InteractableOnPressReceiver** の新しいイベント レシーバーを作成します。</span><span class="sxs-lookup"><span data-stu-id="72c32-204">Click the **Add Event** button, to create a new event receiver of Event Receiver Type **InteractableOnPressReceiver**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> <span data-ttu-id="72c32-206">InteractableOnPressReceiver というイベント レシーバーの種類を使用すると、追跡対象のハンドがボタンを押したときに、押されたイベントにボタンが応答できるようになります。</span><span class="sxs-lookup"><span data-stu-id="72c32-206">The Event Receiver Type named InteractableOnPressReceiver allows the button to respond to a pressed event when a tracked hand presses the button.</span></span>

<span data-ttu-id="72c32-207">新しく作成されたイベント レシーバーに対して、 **[Interaction Filter]\(対話式操作フィルター\)** を **[Near and Far]\(近くと遠く\)** に変更します。</span><span class="sxs-lookup"><span data-stu-id="72c32-207">For the newly created event receiver, change the **Interaction Filter** to **Near and Far**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a><span data-ttu-id="72c32-209">4.On Press イベントを受け取るようにキューブを構成する</span><span class="sxs-lookup"><span data-stu-id="72c32-209">4. Configure the cube to receive the On Press event</span></span>

<span data-ttu-id="72c32-210">[Hierarchy]\(階層\) ウィンドウから、**キューブ**を **On Press ()** イベントの **[Event Properties]** オブジェクト フィールドに**クリックアンドドラッグ**して、キューブを On Press () イベントのレシーバーとして割り当てます。</span><span class="sxs-lookup"><span data-stu-id="72c32-210">From the Hierarchy window, **click-and-drag** the **Cube** into the **Event Properties** object field for the **On Press ()** event to assign the Cube as a receiver of the On Press () event:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a><span data-ttu-id="72c32-212">5.On Press イベントによってトリガーされるアクションを定義する</span><span class="sxs-lookup"><span data-stu-id="72c32-212">5. Define the action to be triggered by the On Press event</span></span>

<span data-ttu-id="72c32-213">アクション ドロップダウン (現在は **[No Function]\(関数なし\)** が割り当てられている) をクリックし、 **[MeshRenderer]**  >  **[Material material]** の順に選択して、On Press () イベントがトリガーされたときにキューブのマテリアル プロパティが変更されるように設定します。</span><span class="sxs-lookup"><span data-stu-id="72c32-213">Click the action dropdown, currently assigned **No Function**, and select **MeshRenderer** > **Material material** to set the Cube's material property to be changed when the On Press () event is triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

<span data-ttu-id="72c32-215">現在 **[None (Material)]\(なし (マテリアル)\)** が設定されているマテリアル フィールドの横の小さな**円**のアイコンをクリックして、[Select Material]\(マテリアルの選択\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="72c32-215">Click the small **circle** icon next to the material field, currently populated with **None (Material)**, to open the Select Material window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

<span data-ttu-id="72c32-217">[Select Material]\(マテリアルの選択\) ウィンドウで、**MRTK_Standard** を**検索**し、適切なマテリアルを選択します。たとえば、**MRTK_Standard_Cyan** を選択して、ボタンを押したときにキューブの色がシアンに変わるようにします。</span><span class="sxs-lookup"><span data-stu-id="72c32-217">In the Select Material window, **search** for **MRTK_Standard** and select a suitable material, for example, **MRTK_Standard_Cyan** so the Cube's color changes to cyan when the button is pressed:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a><span data-ttu-id="72c32-219">6.On Release イベントを受け取るようにキューブを構成する</span><span class="sxs-lookup"><span data-stu-id="72c32-219">6. Configure the cube to receive the On Release event</span></span>

<span data-ttu-id="72c32-220">On Release イベントに対して手順 4 を**繰り返し**、**キューブ**を **On Release ()** イベントのレシーバーとして割り当てます。</span><span class="sxs-lookup"><span data-stu-id="72c32-220">**Repeat** Step 4 for the On Release event to assign the **Cube** as a receiver of the **On Release ()** event.</span></span>

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a><span data-ttu-id="72c32-221">7.On Release イベントによってトリガーされるアクションを定義する</span><span class="sxs-lookup"><span data-stu-id="72c32-221">7. Define the action to be triggered by the On Release event</span></span>

<span data-ttu-id="72c32-222">On Release イベントに対して手順 5 を**繰り返し**ます。ただし、**MRTK_Standard_LightGray** マテリアルを選択して、ボタンを離したときにキューブの色が元の薄い灰色に戻るようにします。</span><span class="sxs-lookup"><span data-stu-id="72c32-222">**Repeat** Step 5 for the On Release event, but choose the **MRTK_Standard_LightGray** material so the Cube's color returns to its original light gray color when the button is released:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a><span data-ttu-id="72c32-224">8.エディター内シミュレーションを使用してボタンをテストする</span><span class="sxs-lookup"><span data-stu-id="72c32-224">8. Test the button using the in-editor simulation</span></span>

<span data-ttu-id="72c32-225">**[Play]\(再生\)** ボタンを押してゲーム モードに入り、エディター内入力シミュレーションを使用して、新しく構成したボタンをテストします。</span><span class="sxs-lookup"><span data-stu-id="72c32-225">Press the **Play** button to enter Game mode and use the in-editor input simulation to test your newly configured button.</span></span>

<span data-ttu-id="72c32-226">ボタンが押されていない (スペース バー + 後方へのマウスのスクロール ホイール):</span><span class="sxs-lookup"><span data-stu-id="72c32-226">Button not pressed (spacebar + mouse scroll wheel backward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

<span data-ttu-id="72c32-228">ボタンが押されている (スペース バー + 前方へのマウスのスクロール ホイール):</span><span class="sxs-lookup"><span data-stu-id="72c32-228">Button pressed (spacebar + mouse scroll wheel forward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> <span data-ttu-id="72c32-230">エディター内入力シミュレーションの使用方法については、[MRTK ドキュメント ポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)で「[エディター内ハンド入力シミュレーションを使用したシーンのテスト](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)」ガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="72c32-230">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="72c32-231">MRTK の Grid Object Collection を使用したボタンのパネルの作成</span><span class="sxs-lookup"><span data-stu-id="72c32-231">Creating a panel of buttons using MRTK's Grid Object Collection</span></span>

<span data-ttu-id="72c32-232">このセクションでは、MRTK の Grid Object Collection ツールを使用して、整ったユーザー インターフェイスになるように複数のボタンを自動的に整列させる方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="72c32-232">In this section, you will learn how to automatically align multiple buttons into a neat user interface by using the MRTK's Grid Object Collection tool.</span></span>

<span data-ttu-id="72c32-233">この特定の例では、5 つのボタンが水平方向に一列に整列したパネルを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="72c32-233">This particular example will show you how to a create a panel with five buttons aligned horizontally.</span></span> <span data-ttu-id="72c32-234">ただし、次の同じ原則に従って他のレイアウトを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="72c32-234">However, you may follow these same principles to create other layouts.</span></span>

<span data-ttu-id="72c32-235">これを実現するための主な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="72c32-235">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="72c32-236">ボタン オブジェクトを親オブジェクトに従属させる</span><span class="sxs-lookup"><span data-stu-id="72c32-236">Parent the button objects to a parent object</span></span>
2. <span data-ttu-id="72c32-237">Grid Object Collection (Script) コンポーネントを追加して構成する</span><span class="sxs-lookup"><span data-stu-id="72c32-237">Add and configure the Grid Object Collection (Script) component</span></span>
3. <span data-ttu-id="72c32-238">エディター内シミュレーションを使用してボタンをテストする</span><span class="sxs-lookup"><span data-stu-id="72c32-238">Test the buttons using the in-editor simulation</span></span>

### <a name="1-parent-the-button-objects-to-a-parent-object"></a><span data-ttu-id="72c32-239">1.ボタン オブジェクトを親オブジェクトに従属させる</span><span class="sxs-lookup"><span data-stu-id="72c32-239">1. Parent the button objects to a parent object</span></span>

<span data-ttu-id="72c32-240">[Hierarchy]\(階層\) ウィンドウ内の何もない場所を右クリックし、 **[Create Empty]\(空の作成\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="72c32-240">Right-click on an empty spot inside the Hierarchy window and select **Create Empty**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

<span data-ttu-id="72c32-242">新しく作成されたオブジェクトを右クリックし、 **[Rename]\(名前の変更\)** を選択して、適切な名前を付けます (たとえば、**ButtonCollection**)。</span><span class="sxs-lookup"><span data-stu-id="72c32-242">Right-click on the newly created object, select **Rename**, and give it a suitable name, for example, **ButtonCollection**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

<span data-ttu-id="72c32-244">**PressableButtonHoloLens2** オブジェクトを選択し、それを **ButtonCollection** オブジェクトの上に**ドラッグ**して、ButtonCollection オブジェクトの子にします。</span><span class="sxs-lookup"><span data-stu-id="72c32-244">Select the **PressableButtonHoloLens2** object and **drag** it on top of the **ButtonCollection** object to make it a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

<span data-ttu-id="72c32-246">**PressableButtonHoloLens2** オブジェクトを右クリックし、 **[Duplicate]\(複製\)** を選択してコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="72c32-246">Right-click the **PressableButtonHoloLens2** object and select **Duplicate** to create a copy of it:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

<span data-ttu-id="72c32-248">合計 5 つの PressableButtonHoloLens2 オブジェクトを取得するまで、この手順をさらに 4 回**繰り返し**ます。</span><span class="sxs-lookup"><span data-stu-id="72c32-248">**Repeat** this step four more times until you have a total of five PressableButtonHoloLens2 objects.</span></span>

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="72c32-249">2.Grid Object Collection (Script) コンポーネントを追加して構成する</span><span class="sxs-lookup"><span data-stu-id="72c32-249">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="72c32-250">[Hierarchy]\(階層\) ウィンドウで ButtonCollection オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで **[Add Component]\(コンポーネントの追加\)** ボタンをクリックし、次に **Grid Object Collection** を検索して選択し、Grid Object Collection (Script) コンポーネントを ButtonCollection オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="72c32-250">With the ButtonCollection object selected in the Hierarchy window, in the Inspector window, click the **Add Component** button, then search for and select **Grid Object Collection** to add a Grid Object Collection (Script) component to the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

<span data-ttu-id="72c32-252">次のように、Grid Object Collection (Script) を構成します。</span><span class="sxs-lookup"><span data-stu-id="72c32-252">Configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="72c32-253">**[Num Rows]\(行数\)** を 1 に変更して、すべてのボタンを 1 行に整列させる</span><span class="sxs-lookup"><span data-stu-id="72c32-253">Change **Num Rows** to 1 to have all buttons aligned on one single row</span></span>
* <span data-ttu-id="72c32-254">**[Cell Width]\(セル幅\)** を 0.05 に変更して、行内でボタンを一定間隔で並べる</span><span class="sxs-lookup"><span data-stu-id="72c32-254">Change **Cell Width** to 0.05 to space out the buttons within the row</span></span>

<span data-ttu-id="72c32-255">次に、 **[Update Collection]\(コレクションの更新\)** ボタンをクリックして、新しい構成を適用します。</span><span class="sxs-lookup"><span data-stu-id="72c32-255">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> <span data-ttu-id="72c32-257">たった今適用した構成変更は、ボタンを 1 行に配置するという目的を達成するために必要な最小限の変更を表しています。</span><span class="sxs-lookup"><span data-stu-id="72c32-257">The configuration changes you just applied represent the minimum changes required to achieve the objective of placing the buttons in a single row.</span></span> <span data-ttu-id="72c32-258">ただし、今後のプロジェクトでは、たとえば、親と子のオブジェクトの向きなどの要因によっては、方向の種類など、他の設定の調整が必要になることもあります。</span><span class="sxs-lookup"><span data-stu-id="72c32-258">However, in future projects, depending on factors such as, for example, the orientation of the parent and child objects, you might need to adjust other settings such as, for example, the Orient Type.</span></span> <span data-ttu-id="72c32-259">MRTK の Grid Object Collection の詳細については、[MRTK ドキュメント ポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)にある「[Object Collection スクリプト](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts)」のガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="72c32-259">To learn more about MRTK's Grid Object Collection, you can visit the [Object collection scripts](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

<span data-ttu-id="72c32-260">[Hierarchy]\(階層\) ウィンドウで ButtonCollection オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで、ButtonCollection オブジェクトの [Transform]\(変換\) の **[Position]\(位置\)** を変更して、子ボタン オブジェクトがカメラの前に配置されるようにします (原点では、たとえば、x = 0、y = 0、z = 0.5 に配置されている)。</span><span class="sxs-lookup"><span data-stu-id="72c32-260">With the ButtonCollection object still selected in the Hierarchy window, in the Inspector window, change the ButtonCollection object's Transform **Position** so its child button objects are positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> <span data-ttu-id="72c32-262">上記の「[ハンド トラッキングのジェスチャと対話可能なボタン](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)」セクションで PressableButtonHoloLens2 プレハブを初めてシーンに追加したときに、それをカメラの前に配置しました。</span><span class="sxs-lookup"><span data-stu-id="72c32-262">When you first added the PressableButtonHoloLens2 prefab to the scene in the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) section above, you positioned it in front of the camera.</span></span> <span data-ttu-id="72c32-263">ただし、Grid Object Collection はその直接の子オブジェクトの位置を制御するので、PressableButtonHoloLens2 子オブジェクトの Z 位置は、Grid Object Collection での親値からの既定距離 0 に従って、0 にリセットされました。</span><span class="sxs-lookup"><span data-stu-id="72c32-263">However, because the Grid Object Collection controls its immediate child objects' position, the PressableButtonHoloLens2 child objects' Z Position were reset to 0 according to the Grid Object Collection's default Distance from parent value of 0.</span></span> <span data-ttu-id="72c32-264">このことにより、また、親/子の位置関係を整理しておくために、PressableButtonHoloLens2 子オブジェクトを前方に移動するように親値からの距離を構成するのではなく、親の ButtonCollection オブジェクトの位置を前方に移動しました。</span><span class="sxs-lookup"><span data-stu-id="72c32-264">This, and to keep the parent/child positional relationship organized, is why we moved the parent ButtonCollection object's position forward instead of configuring the Distance from parent value to move the PressableButtonHoloLens2 child objects forward.</span></span>

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a><span data-ttu-id="72c32-265">3.エディター内シミュレーションを使用してボタンをテストする</span><span class="sxs-lookup"><span data-stu-id="72c32-265">3. Test the buttons using the in-editor simulation</span></span>

<span data-ttu-id="72c32-266">[Play]\(再生\) ボタンを押してゲーム モードに入り、エディター内入力シミュレーションを使用して、新しく作成したボタンのパネルで各ボタンをテストします。</span><span class="sxs-lookup"><span data-stu-id="72c32-266">Press the Play button to enter Game mode and use the in-editor input simulation to test each of the buttons in in your newly created panel of buttons:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> <span data-ttu-id="72c32-268">現在、5 つのボタンのいずれかを押すと、キューブの色がシアンに変わります。</span><span class="sxs-lookup"><span data-stu-id="72c32-268">Currently, when your press any of the five buttons, the cube color changes to cyan.</span></span> <span data-ttu-id="72c32-269">エクスペリエンスをさらにおもしろくするために、たった今学習したことを使用して、キューブが別の色に変わるように各ボタンを構成します。</span><span class="sxs-lookup"><span data-stu-id="72c32-269">To make the experience more interesting, use what you just learn to configure each button to change the cube to a different color.</span></span>

## <a name="adding-text-into-your-scene"></a><span data-ttu-id="72c32-270">シーンへのテキストの追加</span><span class="sxs-lookup"><span data-stu-id="72c32-270">Adding text into your scene</span></span>

<span data-ttu-id="72c32-271">このセクションでは、前のチュートリアルの「[TextMesh Pro の Essential Resources (重要なリソース) をインポートする](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)」セクションで準備した Unity の TextMesh Pro を使用して、Mixed Reality エクスペリエンスにテキストを追加する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="72c32-271">In this section, you will learn how to add text to your mixed reality experiences using Unity's TextMesh Pro, which you prepared in the [Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) section of the previous tutorial.</span></span>

<span data-ttu-id="72c32-272">この特定の例では、前のセクションで作成したボタン コレクションの下に単純なラベルを追加します。</span><span class="sxs-lookup"><span data-stu-id="72c32-272">In this particular example, you will add a simple label underneath the button collection you created in the previous section.</span></span>

<span data-ttu-id="72c32-273">ButtonCollection オブジェクトを右クリックし、 **[3D Object]\(3D オブジェクト\)**  >  **[Text - TextMeshPro]\(テキスト - TextMeshPro\)** を選択して、ButtonCollection オブジェクトの子として TextMeshPro オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="72c32-273">Right-click on the ButtonCollection object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro object as a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

<span data-ttu-id="72c32-275">Text (TMP) という名前の新しく作成された TextMeshPro オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで、その位置とサイズを変更して、ラベルがボタン コレクションの下に正しく表示されるようにします。たとえば、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="72c32-275">With the newly created TextMeshPro object, named Text (TMP), still selected, in the Inspector window change its position and size so the label is placed neatly underneath the button collection, for example:</span></span>

* <span data-ttu-id="72c32-276">[Rect Transform]\(四角形の変換\) の **[Pos Y]\(位置 Y\)** を -0.0425 に変更する</span><span class="sxs-lookup"><span data-stu-id="72c32-276">Change the Rect Transform **Pos Y** to -0.0425</span></span>
* <span data-ttu-id="72c32-277">[Rect Transform]\(四角形の変換\) の **[幅]** を 0.24 に変更する</span><span class="sxs-lookup"><span data-stu-id="72c32-277">Change the Rect Transform **Width** to 0.24</span></span>
* <span data-ttu-id="72c32-278">[Rect Transform]\(四角形の変換\) の **[高さ]** を 0.024 に変更する</span><span class="sxs-lookup"><span data-stu-id="72c32-278">Change the Rect Transform **Height** to 0.024</span></span>

<span data-ttu-id="72c32-279">次に、ラベルの内容を反映するようにテキストを更新し、テキストがラベル内に収まるようにフォント プロパティを選択します。たとえば、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="72c32-279">Then update the text to reflect what the label is for and choose font properties so the text fits within the label, for example:</span></span>

* <span data-ttu-id="72c32-280">Text Mesh Pro (Script) の **[Text]\(テキスト\)** を Button Collection に変更する</span><span class="sxs-lookup"><span data-stu-id="72c32-280">Change the Text Mesh Pro (Script) **Text** to Button Collection</span></span>
* <span data-ttu-id="72c32-281">Text Mesh Pro (Script) の **[Font Style]\(フォント スタイル\)** を太字に変更する</span><span class="sxs-lookup"><span data-stu-id="72c32-281">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="72c32-282">Text Mesh Pro (Script) の **[Font Size]\(フォント サイズ\)** を 0.2 に変更する</span><span class="sxs-lookup"><span data-stu-id="72c32-282">Change the Text Mesh Pro (Script) **Font Size** to 0.2</span></span>
* <span data-ttu-id="72c32-283">Text Mesh Pro (Script) の **[Alignment]\(配置\)** を中央揃え中央に変更する</span><span class="sxs-lookup"><span data-stu-id="72c32-283">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="72c32-285">結論</span><span class="sxs-lookup"><span data-stu-id="72c32-285">Congratulations</span></span>

<span data-ttu-id="72c32-286">このチュートリアルでは、MRTK プロファイルの設定を複製、カスタマイズ、および構成する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="72c32-286">In this tutorial, you learned how to clone, customize, and configure an MRTK profile setting.</span></span> <span data-ttu-id="72c32-287">また、HoloLens 2 で追跡対象のハンドを使用してイベントをトリガーするようにボタンを操作する方法も学習しました。</span><span class="sxs-lookup"><span data-stu-id="72c32-287">You also learned how to interact with buttons to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="72c32-288">最後に、MRTK の Grid Object Collection コンポーネントと Unity の Text Mesh Pro を使用して単純な UI インターフェイスを作成する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="72c32-288">Finally, you learned how to create a simple UI interface using the MRTK's Grid Object Collection component and Unity's Text Mesh Pro.</span></span>

[<span data-ttu-id="72c32-289">次のチュートリアル:4.動的なコンテンツの配置とソルバーの使用</span><span class="sxs-lookup"><span data-stu-id="72c32-289">Next Tutorial: 4. Placing dynamic content and using solvers</span></span>](mrlearning-base-ch3.md)
