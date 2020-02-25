---
title: 入門チュートリアル-3. ユーザーインターフェイスを作成し、Mixed Reality Toolkit を構成する
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: f1d042150d1c81940e672b174c6c02ac71e05883
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554883"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a><span data-ttu-id="4d7bd-105">3. ユーザーインターフェイスを作成し、Mixed Reality Toolkit を構成する</span><span class="sxs-lookup"><span data-stu-id="4d7bd-105">3. Creating user interface and configure Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

<span data-ttu-id="4d7bd-106">前のチュートリアルでは、HoloLens 2 の最初のアプリケーションを開始することで、Mixed Reality Toolkit (MRTK) が提供する必要のある機能の一部について学習しました。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-106">In the previous tutorial, you learned about some of the capabilities the Mixed Reality Toolkit (MRTK) has to offer by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="4d7bd-107">このチュートリアルでは、UI テキストパネルと共にボタンを作成および整理し、既定の対話機能 (タッチ) を使用して各ボタンを操作する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-107">In this tutorial you will learn how to create and organize buttons along with UI text panels, and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="4d7bd-108">また、オブジェクトのサイズ、音、色の変更など、単純なアクションや効果の追加も調査します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-108">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="4d7bd-109">このモジュールでは、[空間マッピング](spatial-mapping.md)メッシュの視覚化を無効にしてから、MRTK プロファイルの変更に関する基本的な概念を紹介します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-109">This module will introduce basic concepts about modifying MRTK profiles, starting with turning off the [spatial mapping](spatial-mapping.md) mesh visualization.</span></span>

## <a name="objectives"></a><span data-ttu-id="4d7bd-110">目標</span><span class="sxs-lookup"><span data-stu-id="4d7bd-110">Objectives</span></span>

* <span data-ttu-id="4d7bd-111">Mixed Reality ツールキット プロファイルをカスタマイズおよび構成する</span><span class="sxs-lookup"><span data-stu-id="4d7bd-111">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="4d7bd-112">UI 要素とボタンを使用したホログラムとの対話</span><span class="sxs-lookup"><span data-stu-id="4d7bd-112">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="4d7bd-113">基本的な手の追跡の入力と操作</span><span class="sxs-lookup"><span data-stu-id="4d7bd-113">Basic hand-tracking input and interactions</span></span>

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="4d7bd-114">Mixed Reality Toolkit プロファイルを構成する方法 (空間認識表示オプションの変更)</span><span class="sxs-lookup"><span data-stu-id="4d7bd-114">How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

<span data-ttu-id="4d7bd-115">このセクションでは、既定の MRTK プロファイルをカスタマイズして構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-115">In this section, you will learn how to customize and configure the default MRTK profiles.</span></span>

<span data-ttu-id="4d7bd-116">この特定の例では、空間メッシュオブザーバーの設定を変更して、空間認識メッシュを非表示にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-116">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="4d7bd-117">ただし、これらの同じ原則に従って、MRTK プロファイルの設定または値をカスタマイズすることもできます。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-117">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="4d7bd-118">空間認識メッシュを非表示にするには、主に次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-118">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="4d7bd-119">既定の構成プロファイルの複製</span><span class="sxs-lookup"><span data-stu-id="4d7bd-119">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="4d7bd-120">空間認識システムを有効にする</span><span class="sxs-lookup"><span data-stu-id="4d7bd-120">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="4d7bd-121">既定の空間認識システムプロファイルを複製する</span><span class="sxs-lookup"><span data-stu-id="4d7bd-121">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="4d7bd-122">既定の空間認識メッシュオブザーバープロファイルを複製します</span><span class="sxs-lookup"><span data-stu-id="4d7bd-122">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="4d7bd-123">空間認識メッシュの可視性を変更する</span><span class="sxs-lookup"><span data-stu-id="4d7bd-123">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="4d7bd-124">既定では、MRTK プロファイルは編集できません。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-124">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="4d7bd-125">これらは、編集する前に複製する必要がある既定のプロファイルテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-125">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="4d7bd-126">プロファイルには、入れ子になったレイヤーがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-126">There are several nested layers of profiles.</span></span> <span data-ttu-id="4d7bd-127">そのため、1つまたは複数の設定を構成するときに、複数のプロファイルを複製して編集するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-127">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="4d7bd-128">1. 既定の構成プロファイルを複製します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-128">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="4d7bd-129">構成プロファイルは最上位レベルのプロファイルです。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-129">The Configuration Profile is the top level profile.</span></span> <span data-ttu-id="4d7bd-130">そのため、他のプロファイルを編集できるようにするには、まず、構成プロファイルを複製する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-130">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="4d7bd-131">[階層] ウィンドウで**MixedRealityToolkit**オブジェクトを選択し、[インスペクター] ウィンドウで Mixed Reality Toolkit**構成プロファイル**を**DefaultHoloLens2ConfigurationProfile**に変更します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-131">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, change the Mixed Reality Toolkit **Configuration Profile** to **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

<span data-ttu-id="4d7bd-133">**MixedRealityToolkit**オブジェクトを選択した状態で、インスペクター ウィンドウの **カスタマイズのコピー &** をクリックして、プロファイルの複製 ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-133">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

<span data-ttu-id="4d7bd-135">複製プロファイル ウィンドウで、**複製** ボタンをクリックして、 **DefaultHololens2ConfigurationProfile**の編集可能なコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-135">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

<span data-ttu-id="4d7bd-137">新しく作成された構成プロファイルが、シーンの構成プロファイルとして割り当てられました。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-137">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

<span data-ttu-id="4d7bd-139">Unity メニューで、[**ファイル** > **保存**] を選択してシーンを保存します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-139">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="4d7bd-140">チュートリアル全体で作業内容を保存してください。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-140">Remember to save your work throughout the tutorial.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="4d7bd-141">2. 空間認識システムを有効にする</span><span class="sxs-lookup"><span data-stu-id="4d7bd-141">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="4d7bd-142">階層 ウィンドウで**MixedRealityToolkit**オブジェクトを選択した状態で、インスペクター ウィンドウで **空間認識** タブを選択し、**空間認識システムを有効にする** チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-142">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="4d7bd-144">3. 既定の空間認識システムプロファイルを複製する</span><span class="sxs-lookup"><span data-stu-id="4d7bd-144">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="4d7bd-145">**空間認識** タブで、**複製** ボタンをクリックして プロファイルの複製 ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-145">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

<span data-ttu-id="4d7bd-147">複製プロファイル ウィンドウで、**複製** ボタンをクリックして、 **DefaultMixedRealitySpatialAwarenessSystemProfile**の編集可能なコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-147">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

<span data-ttu-id="4d7bd-149">新しく作成された空間認識システムプロファイルが、構成プロファイルに自動的に割り当てられるようになりました。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-149">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="4d7bd-151">4. 既定の空間認識メッシュオブザーバープロファイルを複製する</span><span class="sxs-lookup"><span data-stu-id="4d7bd-151">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="4d7bd-152">**空間認識** タブを選択したまま、**Windows Mixed Reality 空間メッシュオブザーバー** セクションを展開し、**複製** ボタンをクリックして プロファイルの複製 ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-152">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

<span data-ttu-id="4d7bd-154">複製プロファイル ウィンドウで、**複製** ボタンをクリックして、 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**の編集可能なコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-154">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

<span data-ttu-id="4d7bd-156">新しく作成された空間認識メッシュオブザーバーのプロファイルが、空間認識システムプロファイルに自動的に割り当てられるようになりました。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-156">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="4d7bd-158">5. 空間認識メッシュの可視性を変更する</span><span class="sxs-lookup"><span data-stu-id="4d7bd-158">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="4d7bd-159">**空間メッシュのオブザーバーの設定**で、**表示オプション**を **[オクルージョン]** に変更します。これにより、まだ機能している間に空間マッピングメッシュが非表示になります。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-159">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still being functional:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="4d7bd-161">空間マッピングメッシュは見えませんが、まだ存在し、機能しています。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-161">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="4d7bd-162">たとえば、物理的な壁の背後にあるホログラムなど、空間マッピングメッシュの背後にあるホログラムは、表示されません。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-162">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="4d7bd-163">ここまで、MRTK プロファイル内の設定を変更する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-163">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="4d7bd-164">ご覧のとおり、MRTK の設定をカスタマイズするには、最初に既定のプロファイルのコピーを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-164">As you can see, in order to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="4d7bd-165">既定のプロファイルは編集できないため、既定の設定に戻す場合は、常に参照として使用されます。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-165">Because the default profiles are not editable, you will always have them as reference if you want revert back to the default settings.</span></span> <span data-ttu-id="4d7bd-166">MRTK プロファイルとそのアーキテクチャの詳細については、 [Mrtk ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の[Mixed Reality Toolkit プロファイル構成ガイド](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-166">To learn more about MRTK profiles and their architecture, you can visit the [Mixed Reality Toolkit profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="4d7bd-167">ハンドトラッキングジェスチャと対話型ボタン</span><span class="sxs-lookup"><span data-stu-id="4d7bd-167">Hand tracking gestures and interactable buttons</span></span>

<span data-ttu-id="4d7bd-168">このセクションでは、ハンドトラッキングを使用してボタンをクリックし、イベントをトリガーして、ボタンが押されたときにアクションを発生させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-168">In this section, you will learn how to use hand tracking to press a button and trigger events to cause an action when the button is pressed.</span></span>

<span data-ttu-id="4d7bd-169">この特定の例では、ボタンが押されたときにキューブの色を変更し、ボタンが離されたときに元の色に戻るように変更する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-169">This particular example will show you how to change the color of a cube when the button is pressed and change it back to it's original color when the button is released.</span></span> <span data-ttu-id="4d7bd-170">ただし、同じ原則に従って他のイベントを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-170">However, you may follow these same principles to create other events.</span></span>

<span data-ttu-id="4d7bd-171">キューブの色を変更するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-171">The main steps you will take to change the color of the cube are:</span></span>

1. <span data-ttu-id="4d7bd-172">シーンに pressable button prefab を追加する</span><span class="sxs-lookup"><span data-stu-id="4d7bd-172">Add a pressable button prefab to the scene</span></span>
2. <span data-ttu-id="4d7bd-173">シーンへのキューブの追加</span><span class="sxs-lookup"><span data-stu-id="4d7bd-173">Add a cube to the scene</span></span>
3. <span data-ttu-id="4d7bd-174">InteractableOnPressReceiver イベントの種類を構成する</span><span class="sxs-lookup"><span data-stu-id="4d7bd-174">Configure the InteractableOnPressReceiver event type</span></span>
4. <span data-ttu-id="4d7bd-175">On Press イベントを受け取るようにキューブを構成する</span><span class="sxs-lookup"><span data-stu-id="4d7bd-175">Configure the cube to receive the On Press event</span></span>
5. <span data-ttu-id="4d7bd-176">On Press イベントによってトリガーされるアクションを定義します</span><span class="sxs-lookup"><span data-stu-id="4d7bd-176">Define the action to be triggered by the On Press event</span></span>
6. <span data-ttu-id="4d7bd-177">On Release イベントを受け取るようにキューブを構成する</span><span class="sxs-lookup"><span data-stu-id="4d7bd-177">Configure the cube to receive the On Release event</span></span>
7. <span data-ttu-id="4d7bd-178">On Release イベントによってトリガーされるアクションを定義します</span><span class="sxs-lookup"><span data-stu-id="4d7bd-178">Define the action to be triggered by the On Release event</span></span>
8. <span data-ttu-id="4d7bd-179">エディター内シミュレーションを使用してボタンをテストする</span><span class="sxs-lookup"><span data-stu-id="4d7bd-179">Test the button using the in-editor simulation</span></span>

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a><span data-ttu-id="4d7bd-180">1. シーンに pressable button prefab を追加する</span><span class="sxs-lookup"><span data-stu-id="4d7bd-180">1. Add a pressable button prefab to the scene</span></span>

> [!TIP]
> <span data-ttu-id="4d7bd-181"><a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">Prefab</a>は Unity アセットとして保存されている構成済みのユーザーオブジェクトであり、プロジェクト全体で再利用できます。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-181">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="4d7bd-182">[**プロジェクト] ウィンドウ**で、 **PressableButtonHoloLens2**を検索して、この例で使用する prefab を探します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-182">In the **Project window**, search for **PressableButtonHoloLens2** to locate the prefab you will use for this example:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

<span data-ttu-id="4d7bd-184">**検索**結果で**PressableButtonHoloLens2** prefab を選択し、それを **[階層]** ウィンドウに**ドラッグ**してシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-184">In the **Search** result, select the **PressableButtonHoloLens2** prefab and **drag** it into the **Hierarchy** window to add it to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="4d7bd-186">次の図に示すようにシーンを表示するには、[階層] ウィンドウで PressableButtonHoloLens2 オブジェクトをダブルクリックしてフォーカスを設定し、[シーン] ウィンドウの右上隅にある<a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">シーンの Gizmo</a>を使用して、前方 Z 軸に沿って表示角度を調整します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-186">To display your scene as shown in the image below, double-click the PressableButtonHoloLens2 object in the Hierarchy window to bring it into focus, then use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis.</span></span>

<span data-ttu-id="4d7bd-187">**PressableButtonHoloLens2**オブジェクトを選択したまま、 **[インスペクター]** ウィンドウで次のようにします。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-187">With the **PressableButtonHoloLens2** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="4d7bd-188">カメラの前に配置されるように変換**位置**を変更する (例: x = 0、y = 0、z = 0.5)</span><span class="sxs-lookup"><span data-stu-id="4d7bd-188">Change its Transform **Position** so it's positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="4d7bd-190">一般に、Unity の1つの位置単位は、物理的な世界では1メートルとほぼ同じです。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-190">In general, 1 position unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="4d7bd-191">ただし、オブジェクトがスケーリングされたオブジェクトの子である場合などに、この例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-191">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span>

### <a name="2-add-a-cube-to-the-scene"></a><span data-ttu-id="4d7bd-192">2. シーンにキューブを追加する</span><span class="sxs-lookup"><span data-stu-id="4d7bd-192">2. Add a cube to the scene</span></span>

<span data-ttu-id="4d7bd-193">[階層] ウィンドウ内の空の場所を右クリックし、[ **3D オブジェクト** > **キューブ**] を選択して、キューブをシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-193">Right-click on an empty spot inside the Hierarchy window and select **3D Object** > **Cube** to add a cube to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

<span data-ttu-id="4d7bd-195">**キューブ**オブジェクトを選択した状態で、 **[インスペクター]** ウィンドウで次のようにします。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-195">With the **Cube** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="4d7bd-196">Pressable ボタンの近くに配置されるように変換**位置**を変更します。ただし、x = 0、y = 0.04、z = 0.5 など、重複しないようにします。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-196">Change its Transform **Position** so its located near the pressable button, but not overlapping with it, for example, x = 0, y = 0.04, and z = 0.5</span></span>
* <span data-ttu-id="4d7bd-197">変換**スケール**を適切なサイズに変更します (たとえば、x = 0.02、y = 0.02、z = 0.02)。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-197">Change its Transform **Scale** to a suitable size, for example, x = 0.02, y = 0.02, and z = 0.02</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a><span data-ttu-id="4d7bd-199">3. InteractableOnPressReceiver イベントの種類を構成する</span><span class="sxs-lookup"><span data-stu-id="4d7bd-199">3. Configure the InteractableOnPressReceiver event type</span></span>

<span data-ttu-id="4d7bd-200">[階層] ウィンドウで、 **PressableButtonHoloLens2**オブジェクトを選択します。次に、 **[インスペクター]** ウィンドウ**ハンバーガーメニュー**で、 **[すべてのコンポーネントを折りたたむ]** を選択して、このオブジェクトのすべてのコンポーネントの概要を取得します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-200">In the Hierarchy window, select the **PressableButtonHoloLens2** object, then in the **Inspector** window **hamburger menu**, select **Collapse All Components** to get an overview of all components on this object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

<span data-ttu-id="4d7bd-202">**対話型 (スクリプト)** コンポーネントを展開し、[**イベント** > **レシーバー** ] セクションを探して展開します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-202">Expand the **Interactable (Script)** component, then locate and expand the **Events** > **Receivers** section:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

<span data-ttu-id="4d7bd-204">**[イベントの追加]** ボタンをクリックして、イベントレシーバーの種類が**Interactableonpressreceiver**の新しいイベントレシーバーを作成します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-204">Click the **Add Event** button, to create a new event receiver of Event Receiver Type **InteractableOnPressReceiver**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> <span data-ttu-id="4d7bd-206">InteractableOnPressReceiver という名前のイベントレシーバーの種類を使用すると、追跡したハンドがボタンを押したときに、ボタンが押されたイベントに応答できるようになります。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-206">The Event Receiver Type named InteractableOnPressReceiver allows the button to respond to a pressed event when a tracked hand presses the button.</span></span>

<span data-ttu-id="4d7bd-207">新しく作成されたイベントレシーバーについて、**相互作用フィルター**を**Near と Far**に変更します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-207">For the newly created event receiver, change the **Interaction Filter** to **Near and Far**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a><span data-ttu-id="4d7bd-209">4. On Press イベントを受け取るようにキューブを構成する</span><span class="sxs-lookup"><span data-stu-id="4d7bd-209">4. Configure the cube to receive the On Press event</span></span>

<span data-ttu-id="4d7bd-210">[階層] ウィンドウで、 **On press** () イベントの **[イベントのプロパティ]** オブジェクトフィールドに**キューブ**をクリックして**ドラッグ**します。これにより、on press () イベントの受信者としてキューブが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-210">From the Hierarchy window, **click-and-drag** the **Cube** into the **Event Properties** object field for the **On Press ()** event to assign the Cube as a receiver of the On Press () event:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a><span data-ttu-id="4d7bd-212">5. On Press イベントによってトリガーされるアクションを定義する</span><span class="sxs-lookup"><span data-stu-id="4d7bd-212">5. Define the action to be triggered by the On Press event</span></span>

<span data-ttu-id="4d7bd-213">[アクション] ドロップダウンをクリックし、[現在割り当てられている**関数はありません**] を選択し、[ **MeshRenderer** > **material material** ] を選択して、On Press () イベントがトリガーされたときに、キューブの material プロパティを変更するように設定します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-213">Click the action dropdown, currently assigned **No Function**, and select **MeshRenderer** > **Material material** to set the Cube's material property to be changed when the On Press () event is triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

<span data-ttu-id="4d7bd-215">[素材] フィールドの横にある小さい**円**アイコン (現在は**None (素材)** が設定されている) をクリックして、[素材の選択] ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-215">Click the small **circle** icon next to the material field, currently populated with **None (Material)**, to open the Select Material window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

<span data-ttu-id="4d7bd-217">[素材の選択] ウィンドウで**MRTK_Standard**を**検索**し、適切な素材を選択します。たとえば、ボタンが押されたときにキューブの色がシアンに変更されるように**MRTK_Standard_Cyan**します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-217">In the Select Material window, **search** for **MRTK_Standard** and select a suitable material, for example, **MRTK_Standard_Cyan** so the Cube's color changes to cyan when the button is pressed:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a><span data-ttu-id="4d7bd-219">6. On Release イベントを受け取るようにキューブを構成する</span><span class="sxs-lookup"><span data-stu-id="4d7bd-219">6. Configure the cube to receive the On Release event</span></span>

<span data-ttu-id="4d7bd-220">**繰り返し**On release イベントの手順4では、 **On release ()** イベントの受信者として**キューブ**を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-220">**Repeat** Step 4 for the On Release event to assign the **Cube** as a receiver of the **On Release ()** event.</span></span>

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a><span data-ttu-id="4d7bd-221">7. On Release イベントによってトリガーされるアクションを定義する</span><span class="sxs-lookup"><span data-stu-id="4d7bd-221">7. Define the action to be triggered by the On Release event</span></span>

<span data-ttu-id="4d7bd-222">**繰り返し**On Release イベントの場合は手順5ですが、ボタンが離されたときにキューブの色が元の明るい灰色の色に戻るように**MRTK_Standard_LightGray**素材を選択します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-222">**Repeat** Step 5 for the On Release event, but choose the **MRTK_Standard_LightGray** material so the Cube's color returns to its original light gray color when the button is released:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a><span data-ttu-id="4d7bd-224">8. エディター内シミュレーションを使用してボタンをテストする</span><span class="sxs-lookup"><span data-stu-id="4d7bd-224">8. Test the button using the in-editor simulation</span></span>

<span data-ttu-id="4d7bd-225">**再生**ボタンを押してゲームモードに入り、エディター内入力シミュレーションを使用して、新しく構成されたボタンをテストします。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-225">Press the **Play** button to enter Game mode and use the in-editor input simulation to test your newly configured button.</span></span>

<span data-ttu-id="4d7bd-226">押されていないボタン (space + マウススクロールホイール後方):</span><span class="sxs-lookup"><span data-stu-id="4d7bd-226">Button not pressed (spacebar + mouse scroll wheel backward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

<span data-ttu-id="4d7bd-228">押されたボタン (space + マウスのホイールを前方にスクロール):</span><span class="sxs-lookup"><span data-stu-id="4d7bd-228">Button pressed (spacebar + mouse scroll wheel forward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> <span data-ttu-id="4d7bd-230">エディター内入力シミュレーションの使用方法については、「エディターでの入力シミュレーションを使用して、 [Mrtk ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)でシーンガイドを[テストする](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-230">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="4d7bd-231">MRTK のグリッド オブジェクト コレクションを使用したボタンのパネルの作成</span><span class="sxs-lookup"><span data-stu-id="4d7bd-231">Creating a panel of buttons using MRTK’s Grid Object Collection</span></span>

<span data-ttu-id="4d7bd-232">このセクションでは、MRTK の Grid オブジェクトコレクションツールを使用して、複数のボタンを適切なユーザーインターフェイスに自動的に配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-232">In this section, you will learn how to automatically align multiple buttons into a neat user interface by using the MRTK’s Grid Object Collection tool.</span></span>

<span data-ttu-id="4d7bd-233">この例では、水平方向に配置された5つのボタンを持つパネルを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-233">This particular example will show you how to a create a panel with five buttons aligned horizontally.</span></span> <span data-ttu-id="4d7bd-234">ただし、同じ原則に従って他のレイアウトを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-234">However, you may follow these same principles to create other layouts.</span></span>

<span data-ttu-id="4d7bd-235">これを実現するには、主に次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-235">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="4d7bd-236">親オブジェクトに対するボタンオブジェクトの親</span><span class="sxs-lookup"><span data-stu-id="4d7bd-236">Parent the button objects to a parent object</span></span>
2. <span data-ttu-id="4d7bd-237">Grid オブジェクトコレクション (スクリプト) コンポーネントの追加と構成</span><span class="sxs-lookup"><span data-stu-id="4d7bd-237">Add and configure the Grid Object Collection (Script) component</span></span>
3. <span data-ttu-id="4d7bd-238">エディター内シミュレーションを使用してボタンをテストする</span><span class="sxs-lookup"><span data-stu-id="4d7bd-238">Test the buttons using the in-editor simulation</span></span>

### <a name="1-parent-the-button-objects-to-a-parent-object"></a><span data-ttu-id="4d7bd-239">1. 親オブジェクトにボタンオブジェクトを親とする</span><span class="sxs-lookup"><span data-stu-id="4d7bd-239">1. Parent the button objects to a parent object</span></span>

<span data-ttu-id="4d7bd-240">階層 ウィンドウ内の空の場所を右クリックし、**空の作成** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-240">Right-click on an empty spot inside the Hierarchy window and select **Create Empty**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

<span data-ttu-id="4d7bd-242">新しく作成したオブジェクトを右クリックし、 **[名前の変更]** を選択して、適切な名前を指定します (例: **buttoncollection**)。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-242">Right-click on the newly created object, select **Rename**, and give it a suitable name, for example, **ButtonCollection**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

<span data-ttu-id="4d7bd-244">**PressableButtonHoloLens2**オブジェクトを選択し、 **buttoncollection**オブジェクトの上に**ドラッグ**して、buttoncollection オブジェクトの子にします。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-244">Select the **PressableButtonHoloLens2** object and **drag** it on top of the **ButtonCollection** object to make it a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

<span data-ttu-id="4d7bd-246">**PressableButtonHoloLens2**オブジェクトを右クリックし、 **[複製]** を選択してコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-246">Right-click the **PressableButtonHoloLens2** object and select **Duplicate** to create a copy of it:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

<span data-ttu-id="4d7bd-248">合計5つの PressableButtonHoloLens2 オブジェクトが表示されるまで、この手順をさらに4回**繰り返し**ます。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-248">**Repeat** this step four more times until you have a total of five PressableButtonHoloLens2 objects.</span></span>

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="4d7bd-249">2. Grid オブジェクトコレクション (スクリプト) コンポーネントを追加して構成する</span><span class="sxs-lookup"><span data-stu-id="4d7bd-249">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="4d7bd-250">階層 ウィンドウで ButtonCollection オブジェクトを選択した状態で、インスペクター ウィンドウで **コンポーネントの追加** ボタンをクリックし、**grid オブジェクト**コレクション を検索して選択します。これにより、Grid オブジェクトコレクション (スクリプト) コンポーネントが buttoncollection オブジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-250">With the ButtonCollection object selected in the Hierarchy window, in the Inspector window, click the **Add Component** button, then search for and select **Grid Object Collection** to add a Grid Object Collection (Script) component to the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

<span data-ttu-id="4d7bd-252">次のように、Grid オブジェクトコレクション (スクリプト) を構成します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-252">Configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="4d7bd-253">**[Num Rows]** を1に変更すると、すべてのボタンが1つの行に合わせて調整されます。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-253">Change **Num Rows** to 1 to have all buttons aligned on one single row</span></span>
* <span data-ttu-id="4d7bd-254">**セルの幅**を0.05 に変更して、行内のボタンを空白にします。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-254">Change **Cell Width** to 0.05 to space out the buttons within the row</span></span>

<span data-ttu-id="4d7bd-255">次に、 **[コレクションの更新]** ボタンをクリックして、新しい構成を適用します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-255">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> <span data-ttu-id="4d7bd-257">適用した構成の変更は、ボタンを単一行に配置する目的を達成するために必要な最小限の変更を表します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-257">The configuration changes you just applied represent the minimum changes required to achieve the objective of placing the buttons in a single row.</span></span> <span data-ttu-id="4d7bd-258">ただし、今後のプロジェクトでは、親オブジェクトや子オブジェクトの向きなどの要因によっては、たとえば、方向の種類など、他の設定の調整が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-258">However, in future projects, depending on factors such as, for example, the orientation of the parent and child objects, you might need to adjust other settings such as, for example, the Orient Type.</span></span> <span data-ttu-id="4d7bd-259">MRTK の Grid オブジェクトコレクションの詳細については、 [Mrtk ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の[オブジェクトコレクションスクリプト](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts)に関するガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-259">To learn more about MRTK's Grid Object Collection, you can visit the [Object collection scripts](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

<span data-ttu-id="4d7bd-260">[階層] ウィンドウで [ButtonCollection] オブジェクトを選択した状態で、[インスペクター] ウィンドウの ButtonCollection オブジェクトの [変換**位置**] を変更して、子ボタンオブジェクトが、原点に配置されるカメラの前に配置されるようにします。たとえば、x = 0、y = 0、z = 0.5 のようになります。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-260">With the ButtonCollection object still selected in the Hierarchy window, in the Inspector window, change the ButtonCollection object's Transform **Position** so its child button objects are positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> <span data-ttu-id="4d7bd-262">前の「[ハンドトラッキングジェスチャと対話型 buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 」セクションでシーンに PressableButtonHoloLens2 prefab を初めて追加したときに、カメラの前に配置しました。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-262">When you first added the PressableButtonHoloLens2 prefab to the scene in the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) section above, you positioned it in front of the camera.</span></span> <span data-ttu-id="4d7bd-263">ただし、Grid オブジェクトコレクションはその直接の子オブジェクトの位置を制御するので、親値0からのグリッドオブジェクトコレクションの既定の距離に従って、PressableButtonHoloLens2 子オブジェクトの Z 位置が0にリセットされました。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-263">However, because the Grid Object Collection controls its immediate child objects' position, the PressableButtonHoloLens2 child objects' Z Position were reset to 0 according to the Grid Object Collection's default Distance from parent value of 0.</span></span> <span data-ttu-id="4d7bd-264">これにより、親/子の位置関係を整理したままにするために、親の ButtonCollection オブジェクトの位置を前方に移動するのは、親の値からの距離を構成するのではなく、PressableButtonHoloLens2 の子オブジェクトを前方に移動するためです。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-264">This, and to keep the parent/child positional relationship organized, is why we moved the parent ButtonCollection object's position forward instead of configuring the Distance from parent value to move the PressableButtonHoloLens2 child objects forward.</span></span>

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a><span data-ttu-id="4d7bd-265">3. エディター内シミュレーションを使用してボタンをテストする</span><span class="sxs-lookup"><span data-stu-id="4d7bd-265">3. Test the buttons using the in-editor simulation</span></span>

<span data-ttu-id="4d7bd-266">再生ボタンを押してゲームモードに入り、エディター内入力シミュレーションを使用して、新しく作成されたボタンのパネルにあるの各ボタンをテストします。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-266">Press the Play button to enter Game mode and use the in-editor input simulation to test each of the buttons in in your newly created panel of buttons:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> <span data-ttu-id="4d7bd-268">現在、5つのボタンのいずれかを押すと、キューブの色が水色に変わります。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-268">Currently, when your press any of the five buttons, the cube color changes to cyan.</span></span> <span data-ttu-id="4d7bd-269">エクスペリエンスをさらに興味深いものにするために、ここで学習したことを使用して、キューブを別の色に変更するように各ボタンを構成します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-269">To make the experience more interesting, use what you just learn to configure each button to change the cube to a different color.</span></span>

## <a name="adding-text-into-your-scene"></a><span data-ttu-id="4d7bd-270">シーンへのテキストの追加</span><span class="sxs-lookup"><span data-stu-id="4d7bd-270">Adding text into your scene</span></span>

<span data-ttu-id="4d7bd-271">このセクションでは、Unity の TextMesh Pro を使用して、mixed reality エクスペリエンスにテキストを追加する方法について説明します。これは、前のチュートリアルの「 [Textmesh pro の重要なリソースのインポート](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)」セクションで準備したものです。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-271">In this section, you will learn how to add text to your mixed reality experiences using Unity's TextMesh Pro, which you prepared in the [Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) section of the previous tutorial.</span></span>

<span data-ttu-id="4d7bd-272">この例では、前のセクションで作成したボタンコレクションの下に単純なラベルを追加します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-272">In this particular example, you will add a simple label underneath the button collection you created in the previous section.</span></span>

<span data-ttu-id="4d7bd-273">ButtonCollection オブジェクトを右クリックし、[ **3D オブジェクト** > **TextMeshPro** ] を選択して、TextMeshPro オブジェクトを buttoncollection オブジェクトの子として作成します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-273">Right-click on the ButtonCollection object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro object as a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

<span data-ttu-id="4d7bd-275">新しく作成された TextMeshPro オブジェクト (TMP) を選択したまま、[インスペクター] ウィンドウで、ボタンコレクションの下にラベルが表示されるように、その位置とサイズを変更します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-275">With the newly created TextMeshPro object, named Text (TMP), still selected, in the Inspector window change its position and size so the label is placed neatly underneath the button collection, for example:</span></span>

* <span data-ttu-id="4d7bd-276">Rect 変換**Pos Y**を-0.0425 に変更します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-276">Change the Rect Transform **Pos Y** to -0.0425</span></span>
* <span data-ttu-id="4d7bd-277">四角形の変換**幅**を0.24 に変更します</span><span class="sxs-lookup"><span data-stu-id="4d7bd-277">Change the Rect Transform **Width** to 0.24</span></span>
* <span data-ttu-id="4d7bd-278">四角形の変換の**高さ**を0.024 に変更します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-278">Change the Rect Transform **Height** to 0.024</span></span>

<span data-ttu-id="4d7bd-279">次に、ラベルの内容を反映するようにテキストを更新し、テキストがラベル内に収まるようにフォントプロパティを選択します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-279">Then update the text to reflect what the label is for and choose font properties so the text fits within the label, for example:</span></span>

* <span data-ttu-id="4d7bd-280">Text メッシュ Pro (スクリプト)**テキスト**をボタンコレクションに変更する</span><span class="sxs-lookup"><span data-stu-id="4d7bd-280">Change the Text Mesh Pro (Script) **Text** to Button Collection</span></span>
* <span data-ttu-id="4d7bd-281">Text メッシュ Pro (スクリプト) の**フォントスタイル**を太字に変更する</span><span class="sxs-lookup"><span data-stu-id="4d7bd-281">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="4d7bd-282">Text メッシュ Pro (スクリプト) の**フォントサイズ**を0.2 に変更します。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-282">Change the Text Mesh Pro (Script) **Font Size** to 0.2</span></span>
* <span data-ttu-id="4d7bd-283">Text メッシュ Pro (スクリプト) の**配置**を中央および中央に変更する</span><span class="sxs-lookup"><span data-stu-id="4d7bd-283">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="4d7bd-285">結論</span><span class="sxs-lookup"><span data-stu-id="4d7bd-285">Congratulations</span></span>

<span data-ttu-id="4d7bd-286">このチュートリアルでは、MRTK プロファイル設定を複製、カスタマイズ、および構成する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-286">In this tutorial, you learned how to clone, customize, and configure an MRTK profile setting.</span></span> <span data-ttu-id="4d7bd-287">また、HoloLens 2 で追跡されたハンズオンを使用してイベントをトリガーするボタンを操作する方法についても学習しました。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-287">You also learned how to interact with buttons to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="4d7bd-288">最後に、MRTK の Grid オブジェクトコレクションコンポーネントと Unity のテキストメッシュ Pro を使用して、単純な UI インターフェイスを作成する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="4d7bd-288">Finally, you learned how to create a simple UI interface using the MRTK's Grid Object Collection component and Unity's Text Mesh Pro.</span></span>

[<span data-ttu-id="4d7bd-289">次のチュートリアル: 4. 動的なコンテンツを配置し、ソルバーを使用する</span><span class="sxs-lookup"><span data-stu-id="4d7bd-289">Next Tutorial: 4. Placing dynamic content and using solvers</span></span>](mrlearning-base-ch3.md)
