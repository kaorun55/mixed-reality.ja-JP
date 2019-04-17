---
title: -ビルド HoloSketch、レイアウト空間および HoloLens 用アプリのスケッチ UX のケース スタディ
description: HoloSketch はデバイス上の空間レイアウトおよび holographic エクスペリエンスの構築に役立つ HoloLens 用ツールのスケッチ UX です。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: アプリのスケッチ HoloSketch、HoloLens、Windows Mixed Reality
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600134"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a><span data-ttu-id="f047c-104">-ビルド HoloSketch、レイアウト空間および HoloLens 用アプリのスケッチ UX のケース スタディ</span><span class="sxs-lookup"><span data-stu-id="f047c-104">Case study - Building HoloSketch, a spatial layout and UX sketching app for HoloLens</span></span>

<span data-ttu-id="f047c-105">HoloSketch はデバイス上の空間レイアウトおよび holographic エクスペリエンスの構築に役立つ HoloLens 用ツールのスケッチ UX です。</span><span class="sxs-lookup"><span data-stu-id="f047c-105">HoloSketch is an on-device spatial layout and UX sketching tool for HoloLens to help build holographic experiences.</span></span> <span data-ttu-id="f047c-106">HoloSketch はペアになっている Bluetooth キーボードとマウスだけでなくジェスチャと音声コマンドでは動作します。</span><span class="sxs-lookup"><span data-stu-id="f047c-106">HoloSketch works with a paired Bluetooth keyboard and mouse as well as gesture and voice commands.</span></span> <span data-ttu-id="f047c-107">HoloSketch では、クイック ビジュアル化およびイテレーションの単純な UX レイアウト ツールを提供します。</span><span class="sxs-lookup"><span data-stu-id="f047c-107">The purpose of HoloSketch is to provide a simple UX layout tool for quick visualization and iteration.</span></span>

<span data-ttu-id="f047c-108">![HoloSketch:空間のレイアウトと UX HoloLens 用アプリのスケッチをします。](images/holosketch-image-01-640px.png)</span><span class="sxs-lookup"><span data-stu-id="f047c-108">![HoloSketch: A spatial layout and UX sketching app for HoloLens.](images/holosketch-image-01-640px.png)</span></span><br>
<span data-ttu-id="f047c-109">*HoloSketch: 空間的なレイアウトと UX HoloLens 用アプリのスケッチ*</span><span class="sxs-lookup"><span data-stu-id="f047c-109">*HoloSketch: spatial layout and UX sketching app for HoloLens*</span></span>

<span data-ttu-id="f047c-110">![簡単な視覚エフェクトとイテレーションの単純な UX レイアウト ツールです。](images/holosketch-image-02.png)</span><span class="sxs-lookup"><span data-stu-id="f047c-110">![A simple UX layout tool for quick visualization and iteration.](images/holosketch-image-02.png)</span></span><br>
<span data-ttu-id="f047c-111">*簡単な視覚エフェクトとイテレーションの単純な UX レイアウト ツール*</span><span class="sxs-lookup"><span data-stu-id="f047c-111">*A simple UX layout tool for quick visualization and iteration*</span></span>

## <a name="features"></a><span data-ttu-id="f047c-112">機能</span><span class="sxs-lookup"><span data-stu-id="f047c-112">Features</span></span>

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a><span data-ttu-id="f047c-113">クイック スタディとスケール プロトタイプ作成用のプリミティブ</span><span class="sxs-lookup"><span data-stu-id="f047c-113">Primitives for quick studies and scale-prototyping</span></span>

![プリミティブ図形を使用します。](images/holosketch-primitives-giphy.gif)

<span data-ttu-id="f047c-115">クイック massing スタディとスケール-プロトタイプの作成には、プリミティブ図形を使用します。</span><span class="sxs-lookup"><span data-stu-id="f047c-115">Use primitive shapes for quick massing studies and scale-prototyping.</span></span>

### <a name="import-objects-through-onedrive"></a><span data-ttu-id="f047c-116">OneDrive からオブジェクトのインポート</span><span class="sxs-lookup"><span data-stu-id="f047c-116">Import objects through OneDrive</span></span>

![オブジェクトのインポート](images/holosketch-importobjects-giphy.gif)

<span data-ttu-id="f047c-118">PNG または JPG 画像や FBX の 3D オブジェクトのインポート (Unity でパッケージ化が必要) が OneDrive から複合現実領域。</span><span class="sxs-lookup"><span data-stu-id="f047c-118">Import PNG/JPG images or 3D FBX objects(requires packaging in Unity) into the mixed reality space through OneDrive.</span></span>

### <a name="manipulate-objects"></a><span data-ttu-id="f047c-119">オブジェクトを操作します。</span><span class="sxs-lookup"><span data-stu-id="f047c-119">Manipulate objects</span></span>

![オブジェクトの操作](images/manipulate-objects-640px.jpg)

<span data-ttu-id="f047c-121">3D オブジェクトを使い慣れたインターフェイスを持つオブジェクト (移動/回転/スケール) を操作します。</span><span class="sxs-lookup"><span data-stu-id="f047c-121">Manipulate objects (move/rotate/scale) with a familiar 3D object interface.</span></span>

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a><span data-ttu-id="f047c-122">Bluetooth、マウス/キーボード、ジェスチャと音声コマンド</span><span class="sxs-lookup"><span data-stu-id="f047c-122">Bluetooth, mouse/keyboard, gestures and voice commands</span></span>

![Bluetooth をサポートしています](images/supports-bluetooth-640px.jpg)

<span data-ttu-id="f047c-124">HoloSketch は、Bluetooth マウス/キーボード、ジェスチャ、音声コマンドをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f047c-124">HoloSketch supports Bluetooth mouse/keyboard, gestures and voice commands.</span></span>

## <a name="background"></a><span data-ttu-id="f047c-125">背景</span><span class="sxs-lookup"><span data-stu-id="f047c-125">Background</span></span>

### <a name="importance-of-experiencing-your-design-in-the-device"></a><span data-ttu-id="f047c-126">デバイスで、設計が発生していることの重要性</span><span class="sxs-lookup"><span data-stu-id="f047c-126">Importance of experiencing your design in the device</span></span>

<span data-ttu-id="f047c-127">HoloLens のものを設計するときは、デバイスで、設計が発生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f047c-127">When you design something for HoloLens, it is important to experience your design in the device.</span></span> <span data-ttu-id="f047c-128">複合現実アプリの設計では、最大の課題の 1 つは、従来の 2D スケッチを特にスケール、位置、および、深さの把握が困難であります。</span><span class="sxs-lookup"><span data-stu-id="f047c-128">One of the biggest challenges in mixed reality app design is that it is hard to get the sense of scale, position and depth, especially through traditional 2D sketches.</span></span>

### <a name="cost-of-2d-based-communication"></a><span data-ttu-id="f047c-129">2D のコスト ベースの通信</span><span class="sxs-lookup"><span data-stu-id="f047c-129">Cost of 2D based communication</span></span>

<span data-ttu-id="f047c-130">UX のフローおよび他のユーザー シナリオを効果的に通信するには、デザイナーは、多くの Illustrator、Photoshop、および PowerPoint などの従来の 2D ツールを使用して資産を作成する時間を費やすことになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f047c-130">To effectively communicate UX flows and scenarios to others, a designer may end up spending a lot of time creating assets using traditional 2D tools such as Illustrator, Photoshop and PowerPoint.</span></span> <span data-ttu-id="f047c-131">これらの 2D デザインは多くの場合に変換する追加の作業を必要と 3D にします。</span><span class="sxs-lookup"><span data-stu-id="f047c-131">These 2D designs often require additional effort to convert them it into 3D.</span></span> <span data-ttu-id="f047c-132">いくつかのアイデアは、3d 2D から変換時に失われます。</span><span class="sxs-lookup"><span data-stu-id="f047c-132">Some ideas are lost in this translation from 2D to 3D.</span></span>

### <a name="complex-deployment-process"></a><span data-ttu-id="f047c-133">複雑な展開プロセス</span><span class="sxs-lookup"><span data-stu-id="f047c-133">Complex deployment process</span></span>

<span data-ttu-id="f047c-134">複合現実は、私たちにとって新しいキャンバスであるために、その性質上のデザインの繰り返しおよび試行錯誤の多くが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f047c-134">Since mixed reality is a new canvas for us, it involves a lot of design iteration and trial and error by its nature.</span></span> <span data-ttu-id="f047c-135">Unity と Visual Studio などのツールに慣れていないデザイナーの HoloLens のものをまとめる簡単ではありません。</span><span class="sxs-lookup"><span data-stu-id="f047c-135">For designer who are not familiar with tools such as Unity and Visual Studio, it is not easy to put something together in HoloLens.</span></span> <span data-ttu-id="f047c-136">通常は、デバイスでの 2d/3d アートワークを表示するために以下のプロセスを通過する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f047c-136">Typically you have to go through the process below to see your 2D/3D artwork in the device.</span></span> <span data-ttu-id="f047c-137">これは、アイデアやシナリオをすばやく反復処理するデザイナーにとって大きな防策です。</span><span class="sxs-lookup"><span data-stu-id="f047c-137">This was a big barrier for designers iterating on ideas and scenarios quickly.</span></span>

<span data-ttu-id="f047c-138">![複雑な展開プロセス](images/holosketch-image-03-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="f047c-138">![Complex deployment process](images/holosketch-image-03-1000px.png)</span></span><br>
<span data-ttu-id="f047c-139">*展開プロセス*</span><span class="sxs-lookup"><span data-stu-id="f047c-139">*Deployment process*</span></span>

### <a name="simplified-process-with-holosketch"></a><span data-ttu-id="f047c-140">HoloSketch を簡略化されたプロセス</span><span class="sxs-lookup"><span data-stu-id="f047c-140">Simplified process with HoloSketch</span></span>

<span data-ttu-id="f047c-141">HoloSketch での開発ツールとデバイスのポータルのペアを使用することがなく、このプロセスを簡略化する考えました。</span><span class="sxs-lookup"><span data-stu-id="f047c-141">With HoloSketch, we wanted to simplify this process without involving development tools and device portal pairing.</span></span> <span data-ttu-id="f047c-142">OneDrive を使用して、ユーザーに簡単に配置できます 2d/3d 資産 HoloLens にします。</span><span class="sxs-lookup"><span data-stu-id="f047c-142">Using OneDrive, users can easily put 2D/3D assets into HoloLens.</span></span>

<span data-ttu-id="f047c-143">![HoloSketch を簡略化されたプロセス](images/holosketch-image-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="f047c-143">![Simplified process with HoloSketch](images/holosketch-image-04-1000px.png)</span></span><br>
<span data-ttu-id="f047c-144">*HoloSketch を簡略化されたプロセス*</span><span class="sxs-lookup"><span data-stu-id="f047c-144">*Simplified process with HoloSketch*</span></span>

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a><span data-ttu-id="f047c-145">3 次元のデザインの考え方とソリューションを促進</span><span class="sxs-lookup"><span data-stu-id="f047c-145">Encouraging three-dimensional design thinking and solutions</span></span>

<span data-ttu-id="f047c-146">このツールでも、デザイナーを本当に 3 次元空間でソリューションを確認して、2 D になっていないことできるようになりますと考えました。</span><span class="sxs-lookup"><span data-stu-id="f047c-146">We thought this tool would give designers an opportunity to explore solutions in a truly three-dimensional space and not be stuck in 2D.</span></span> <span data-ttu-id="f047c-147">バック グラウンドは Hololens の場合は、現実の世界であるため、UI の 3D のバック グラウンドの作成について考慮する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f047c-147">They don’t have to think about creating a 3D background for their UI since the background is the real world in the case of Hololens.</span></span> <span data-ttu-id="f047c-148">HoloSketch は、Hololens で 3D のデザインを簡単に探索するデザイナーが開きます。</span><span class="sxs-lookup"><span data-stu-id="f047c-148">HoloSketch opens up a way for designers to easily explore 3D design on Hololens.</span></span>

## <a name="get-started"></a><span data-ttu-id="f047c-149">はじめに</span><span class="sxs-lookup"><span data-stu-id="f047c-149">Get Started</span></span>

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a><span data-ttu-id="f047c-150">HoloSketch に 2 D 画像 (JPG または PNG) をインポートする方法</span><span class="sxs-lookup"><span data-stu-id="f047c-150">How to import 2D images (JPG/PNG) into HoloSketch</span></span>

* <span data-ttu-id="f047c-151">OneDrive フォルダー 'ドキュメント/HoloSketch' を JPG または PNG イメージをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="f047c-151">Upload JPG/PNG images to your OneDrive folder ‘Documents/HoloSketch’.</span></span>
* <span data-ttu-id="f047c-152">HoloSketch で、[OneDrive] メニューから選択し、環境にイメージを配置することができます。</span><span class="sxs-lookup"><span data-stu-id="f047c-152">From the OneDrive menu in HoloSketch, you will be able to select and place the image in the environment.</span></span>

<span data-ttu-id="f047c-153">![2D イメージをインポートします。](images/import-2d-images-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="f047c-153">![Importing 2D images](images/import-2d-images-1000px.jpg)</span></span><br>
<span data-ttu-id="f047c-154">*イメージと OneDrive を 3D オブジェクトをインポートします。*</span><span class="sxs-lookup"><span data-stu-id="f047c-154">*Importing images and 3D objects through OneDrive*</span></span>

### <a name="how-to-import-3d-objects-into-holosketch"></a><span data-ttu-id="f047c-155">HoloSketch に 3D オブジェクトをインポートする方法</span><span class="sxs-lookup"><span data-stu-id="f047c-155">How to import 3D objects into HoloSketch</span></span>

<span data-ttu-id="f047c-156">OneDrive フォルダーにアップロードする前に、Unity asset のバンドルにパッケージ化、3 D オブジェクトには、次の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="f047c-156">Before uploading to your OneDrive folder, please follow the steps below to package your 3D objects into a Unity asset bundle.</span></span> <span data-ttu-id="f047c-157">このプロセスを使用すると、Maya、シネマ 4 D Microsoft ペイントの 3 D などの 3D のソフトウェアから FBX/OBJ ファイルをインポートできます。</span><span class="sxs-lookup"><span data-stu-id="f047c-157">Using this process you can import your FBX/OBJ files from 3D software such as Maya, Cinema 4D and Microsoft Paint 3D.</span></span>

>[!IMPORTANT]
><span data-ttu-id="f047c-158">現時点では、Unity バージョン 5.4.5f1 資産バンドルの作成がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f047c-158">Currently, asset bundle creation is supported with Unity version 5.4.5f1.</span></span>

1. <span data-ttu-id="f047c-159">ダウンロードして、Unity プロジェクトを開く['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity)します。</span><span class="sxs-lookup"><span data-stu-id="f047c-159">Download and open the Unity project ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span></span> <span data-ttu-id="f047c-160">この Unity プロジェクトには、バンドルの資産の生成のためのスクリプトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f047c-160">This Unity project includes the script for the bundle asset generation.</span></span>
2. <span data-ttu-id="f047c-161">新しい GameObject を作成します。</span><span class="sxs-lookup"><span data-stu-id="f047c-161">Create a new GameObject.</span></span>
3. <span data-ttu-id="f047c-162">内容に基づく GameObject の名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="f047c-162">Name the GameObject based on the contents.</span></span>
4. <span data-ttu-id="f047c-163">Inspector パネルで、コンポーネントの追加 をクリックし、' 足場に Box Collider' を追加します。</span><span class="sxs-lookup"><span data-stu-id="f047c-163">In the Inspector panel, click ‘Add Component’ and add ‘Box Collider’.</span></span> 

   ![Inspector パネルで、コンポーネントの追加 をクリックし、' 足場に Box Collider' を追加](images/holosketch-10a-assetbundles-1000px.png)
   
   ![Inspector パネルで、コンポーネントの追加 をクリックし、' Box Collider'2 を追加](images/holosketch-10b-assetbundles-1000px.png)

5. <span data-ttu-id="f047c-166">[プロジェクト] パネルにドラッグして 3D FBX ファイルをインポートします。</span><span class="sxs-lookup"><span data-stu-id="f047c-166">Import the 3D FBX file by dragging it into the project panel.</span></span>
6. <span data-ttu-id="f047c-167">階層のパネルに、オブジェクトをドラッグ**下に新しい GameObject**します。</span><span class="sxs-lookup"><span data-stu-id="f047c-167">Drag the object into the Hierarchy panel **under your new GameObject**.</span></span>

   ![オブジェクトを階層のパネルに新しい GameObject の下にドラッグします。](images/holosketch-12-assetbundles-1000px.png)

7. <span data-ttu-id="f047c-169">オブジェクトが一致しない場合は、collider ディメンションを調整します。</span><span class="sxs-lookup"><span data-stu-id="f047c-169">Adjust the collider dimension if it does not match the object.</span></span> <span data-ttu-id="f047c-170">直面するオブジェクトを回転させる**z 軸**します。</span><span class="sxs-lookup"><span data-stu-id="f047c-170">Rotate the object to face **Z-axis**.</span></span>

   ![オブジェクトが一致しない場合は、コライダーのディメンションを調整します。](images/holosketch-13-assetbundles-1000px.png)

8. <span data-ttu-id="f047c-172">プロジェクト パネル、[階層] パネルからオブジェクトをドラッグ**prefab ように**します。</span><span class="sxs-lookup"><span data-stu-id="f047c-172">Drag the object from the Hierarchy panel to the Project panel to **make it prefab**.</span></span>
9. <span data-ttu-id="f047c-173">Inspector パネルの下部にある、ドロップダウンをクリックします。 作成して新しい一意の名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="f047c-173">On the bottom of the inspector panel, click the dropdown, create and assign a new unique name.</span></span> <span data-ttu-id="f047c-174">次の例の追加や AssetBundle 名 'brownchair' の割り当てを示しています。</span><span class="sxs-lookup"><span data-stu-id="f047c-174">Below example shows adding and assigning 'brownchair' for the AssetBundle Name.</span></span> 

   ![Inspector パネルの下部にある、ドロップダウン リストをクリックし、新しい一意の名前を割り当てます。](images/holosketch-14-assetbundles-1000px.png)

10. <span data-ttu-id="f047c-176">モデル オブジェクトのサムネイル イメージを準備します。</span><span class="sxs-lookup"><span data-stu-id="f047c-176">Prepare a thumbnail image for the model object.</span></span> 
   <span data-ttu-id="f047c-177">![[プロジェクト] パネルにイメージをドラッグし、オブジェクトに使用される名前を割り当てます。](images/holosketch-15-assetbundles-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="f047c-177">![Drag an image into the project panel and assign the name used for the object.](images/holosketch-15-assetbundles-1000px.png)</span></span>

11. <span data-ttu-id="f047c-178">Unity プロジェクトの '資産' フォルダーの下には、'Assetbundles' という名前のフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="f047c-178">Create a folder named ‘Assetbundles’ under the Unity project’s ‘Asset’ folder.</span></span>

12. <span data-ttu-id="f047c-179">資産 メニューからファイルを生成する ' AssetBundles のビルド を選択します。</span><span class="sxs-lookup"><span data-stu-id="f047c-179">From the Assets menu, select ‘Build AssetBundles’ to generate file.</span></span> 
   <span data-ttu-id="f047c-180">![[資産] メニューからファイルを生成する ' AssetBundles のビルド] を選択します。](images/holosketch-15a-assetbundles.png)</span><span class="sxs-lookup"><span data-stu-id="f047c-180">![From the Assets menu, select ‘Build AssetBundles’ to generate file.](images/holosketch-15a-assetbundles.png)</span></span>


13. <span data-ttu-id="f047c-181">**OneDrive 上の/Files/Documents/HoloSketch フォルダーに生成されたファイルをアップロードします。**</span><span class="sxs-lookup"><span data-stu-id="f047c-181">**Upload the generated file to the /Files/Documents/HoloSketch folder on OneDrive.**</span></span> <span data-ttu-id="f047c-182">Asset_unique_name ファイルのみアップロードします。</span><span class="sxs-lookup"><span data-stu-id="f047c-182">Upload the asset_unique_name file only.</span></span> <span data-ttu-id="f047c-183">マニフェスト ファイルまたは AssetBundles ファイルをアップロードする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f047c-183">You don’t need to upload manifest files or AssetBundles file.</span></span> <br>
<span data-ttu-id="f047c-184">![ファイル/ドキュメント/HoloSketch にファイルを追加/フォルダー](images/holosketch-onedriveupload-1000px.png)
![HoloSketch の OneDrive のメニューに追加された 3D オブジェクトが表示されます](images/holosketch-14-onedriveexample-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="f047c-184">![Add files to Files/Documents/HoloSketch/ folder](images/holosketch-onedriveupload-1000px.png)
![You will see added 3D object in HoloSketch's OneDrive menu](images/holosketch-14-onedriveexample-1000px.jpg)</span></span>

## <a name="how-to-manipulate-the-objects"></a><span data-ttu-id="f047c-185">オブジェクトを操作する方法</span><span class="sxs-lookup"><span data-stu-id="f047c-185">How to manipulate the objects</span></span>

<span data-ttu-id="f047c-186">HoloSketch は、3 D のソフトウェアで広く使用されている従来のインターフェイスをサポートします。</span><span class="sxs-lookup"><span data-stu-id="f047c-186">HoloSketch supports the traditional interface that is widely used in 3D software.</span></span> <span data-ttu-id="f047c-187">Move を使用して、回転、ジェスチャと、マウスを使ってオブジェクトを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="f047c-187">You can use move, rotate, scale the objects with gestures and a mouse.</span></span> <span data-ttu-id="f047c-188">音声、キーボードでの異なるモードをすばやく切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="f047c-188">You can quickly switch between different modes with voice or keyboard.</span></span>

### <a name="object-manipulation-modes"></a><span data-ttu-id="f047c-189">オブジェクトの操作モード</span><span class="sxs-lookup"><span data-stu-id="f047c-189">Object manipulation modes</span></span>

<span data-ttu-id="f047c-190">![オブジェクトを操作する方法](images/holosketch-image-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="f047c-190">![How to manipulate the objects](images/holosketch-image-06-1000px.png)</span></span><br>
<span data-ttu-id="f047c-191">*オブジェクトを操作する方法*</span><span class="sxs-lookup"><span data-stu-id="f047c-191">*How to manipulate the objects*</span></span>

### <a name="contextual-and-tool-belt-menus"></a><span data-ttu-id="f047c-192">コンテキストとツール ベルト メニュー</span><span class="sxs-lookup"><span data-stu-id="f047c-192">Contextual and Tool Belt menus</span></span>

<span data-ttu-id="f047c-193">**コンテキスト メニューを使用してください。**</span><span class="sxs-lookup"><span data-stu-id="f047c-193">**Using the Contextual Menu**</span></span>

<span data-ttu-id="f047c-194">コンテキスト メニューを開き二重のエア タップします。</span><span class="sxs-lookup"><span data-stu-id="f047c-194">Double air tap to open the Contextual Menu.</span></span> 

<span data-ttu-id="f047c-195">メニュー項目。</span><span class="sxs-lookup"><span data-stu-id="f047c-195">Menu items:</span></span>
* <span data-ttu-id="f047c-196">**画面のレイアウト:** これは 3D のグリッド システム レイアウトを複数のオブジェクトとそれらのグループとして管理します。</span><span class="sxs-lookup"><span data-stu-id="f047c-196">**Layout Surface:** This is a 3D grid system where you can layout multiple objects and manage them as a group.</span></span> <span data-ttu-id="f047c-197">オブジェクトを追加するのにレイアウト画面で二重のエア タップします。</span><span class="sxs-lookup"><span data-stu-id="f047c-197">Double air-tap on the Layout Surface to add objects to it.</span></span>
* <span data-ttu-id="f047c-198">**プリミティブ。** スタディ massing のキューブ、球体、円柱、および円錐を使用します。</span><span class="sxs-lookup"><span data-stu-id="f047c-198">**Primitives:** Use cubes, spheres, cylinders and cones for massing studies.</span></span>
* <span data-ttu-id="f047c-199">**OneDrive:** オブジェクトをインポートする [OneDrive] メニューを開きます。</span><span class="sxs-lookup"><span data-stu-id="f047c-199">**OneDrive:** Open the OneDrive menu to import objects.</span></span>
* <span data-ttu-id="f047c-200">**ヘルプ：** ヘルプ画面を表示します。</span><span class="sxs-lookup"><span data-stu-id="f047c-200">**Help:** Displays help screen.</span></span>

<span data-ttu-id="f047c-201">![コンテキスト メニュー](images/holosketch-image-07.png)</span><span class="sxs-lookup"><span data-stu-id="f047c-201">![Contextual menu](images/holosketch-image-07.png)</span></span><br>
<span data-ttu-id="f047c-202">*コンテキスト メニュー*</span><span class="sxs-lookup"><span data-stu-id="f047c-202">*Contextual menu*</span></span>

<span data-ttu-id="f047c-203">**ツール ベルトのメニューを使用してください。**</span><span class="sxs-lookup"><span data-stu-id="f047c-203">**Using the Tool Belt Menu**</span></span>

<span data-ttu-id="f047c-204">移動、回転、スケール、保存、および負荷のシーンはツール ベルトのメニューから利用できます。</span><span class="sxs-lookup"><span data-stu-id="f047c-204">Move, Rotate, Scale, Save, and Load Scene are available from the Tool Belt Menu.</span></span> 

## <a name="using-keyboard-gestures-and-voice-commands"></a><span data-ttu-id="f047c-205">キーボード、ジェスチャ、音声コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f047c-205">Using keyboard, gestures and voice commands</span></span>

<span data-ttu-id="f047c-206">![キーボード、ジェスチャ、音声コマンド](images/holosketch-image-08-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="f047c-206">![Keyboard, Gestures and Voice Commands](images/holosketch-image-08-1000px.png)</span></span><br>
<span data-ttu-id="f047c-207">*キーボード、ジェスチャ、音声コマンド*</span><span class="sxs-lookup"><span data-stu-id="f047c-207">*Keyboard, gestures, and voice commands*</span></span>

## <a name="download-the-app"></a><span data-ttu-id="f047c-208">アプリをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="f047c-208">Download the app</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><span data-ttu-id="f047c-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">ダウンロードして Microsoft Store から無料 HoloSketch アプリをインストール</a>
</span><span class="sxs-lookup"><span data-stu-id="f047c-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Download and install the HoloSketch app for free from the Microsoft Store</a>
</span></span></td>
</tr>
</table>

## <a name="known-issues"></a><span data-ttu-id="f047c-210">既知の問題</span><span class="sxs-lookup"><span data-stu-id="f047c-210">Known issues</span></span>
* <span data-ttu-id="f047c-211">資産のバンドルの作成がサポートされている現在**Unity バージョン 5.4.5f1 します。**</span><span class="sxs-lookup"><span data-stu-id="f047c-211">Currently asset bundle creation is supported with **Unity version 5.4.5f1.**</span></span>
* <span data-ttu-id="f047c-212">OneDrive の内容を読み込み中に停止した場合と、OneDrive 内のデータの量、によって、アプリが表示可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f047c-212">Depending on the amount of data in your OneDrive, the app might appear as if it has stopped while loading OneDrive contents</span></span>
* <span data-ttu-id="f047c-213">現時点では、保存し、読み込み機能は、プリミティブ オブジェクトのみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f047c-213">Currently, Save and Load feature only supports primitive objects</span></span>
* <span data-ttu-id="f047c-214">コンテキスト メニューのテキスト、サウンド、ビデオ、および写真のメニューが無効になっています</span><span class="sxs-lookup"><span data-stu-id="f047c-214">Text, Sound, Video and Photo menus are disabled on the contextual menu</span></span>
* <span data-ttu-id="f047c-215">[ツール] メニューの [再生] ボタンは、操作ギズモをクリアします。</span><span class="sxs-lookup"><span data-stu-id="f047c-215">The Play button on the Tool Belt menu clears the manipulation gizmos</span></span>

## <a name="sharing-your-sketches"></a><span data-ttu-id="f047c-216">スケッチの共有</span><span class="sxs-lookup"><span data-stu-id="f047c-216">Sharing your sketches</span></span>

<span data-ttu-id="f047c-217">HoloLens のビデオ記録の機能を使用することを示す ' Hey Cortana、開始/停止の記録 '。</span><span class="sxs-lookup"><span data-stu-id="f047c-217">You can use the video recording feature in HoloLens by saying 'Hey Cortana, Start/Stop recording'.</span></span> <span data-ttu-id="f047c-218">ボリューム上/下、スケッチの画像を撮影してキーを押します。</span><span class="sxs-lookup"><span data-stu-id="f047c-218">Press the volume up/down key together to take a picture of your sketch.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="f047c-219">著者について</span><span class="sxs-lookup"><span data-stu-id="f047c-219">About the authors</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="f047c-220"><b>ドン Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="f047c-220"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="f047c-221">UX デザイナー @Microsoft</span><span class="sxs-lookup"><span data-stu-id="f047c-221">UX Designer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="f047c-222"><b>Patrick Sebring</b></span><span class="sxs-lookup"><span data-stu-id="f047c-222"><b>Patrick Sebring</b></span></span><br><span data-ttu-id="f047c-223">開発者向け @Microsoft</span><span class="sxs-lookup"><span data-stu-id="f047c-223">Developer @Microsoft</span></span></td>
</tr>
</table> 
