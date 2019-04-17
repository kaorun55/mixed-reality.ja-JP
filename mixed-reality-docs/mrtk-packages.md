---
title: MRTK パッケージ
description: この記事では、Microsoft Mixed Reality Toollkit を構成するパッケージについて説明します。
author: davidkline-ms
ms.author: davidkl
ms.date: 02/12/19
ms.topic: article
keywords: Windows Mixed Reality MRTK、コンポーネントのパッケージ
ms.openlocfilehash: 7e44d75e1c267cff0ba67dd86dabfaa51bce659d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604641"
---
# <a name="mrtk-packages"></a><span data-ttu-id="d02cb-104">MRTK パッケージ</span><span class="sxs-lookup"><span data-stu-id="d02cb-104">MRTK packages</span></span>

<span data-ttu-id="d02cb-105">Mixed Reality ツールキット (MRTK) は、コンポーネント化された方法での複合現実のハードウェアおよびプラットフォーム サポートを提供することでクロス プラットフォームの複合現実アプリケーションの開発が可能なパッケージのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="d02cb-105">The Mixed Reality Toolkit (MRTK) is a collection of packages that enable cross platform Mixed Reality application development by providing support for Mixed Reality hardware and platforms in a componentized manner.</span></span>

<span data-ttu-id="d02cb-106">MRTK パッケージの 3 つのカテゴリがあります。</span><span class="sxs-lookup"><span data-stu-id="d02cb-106">There are three categories of MRTK packages:</span></span> 

* [<span data-ttu-id="d02cb-107">Foundation</span><span class="sxs-lookup"><span data-stu-id="d02cb-107">Foundation</span></span>](#foundation-packages)
* [<span data-ttu-id="d02cb-108">拡張機能</span><span class="sxs-lookup"><span data-stu-id="d02cb-108">Extension</span></span>](#extension-packages)
* [<span data-ttu-id="d02cb-109">実験用</span><span class="sxs-lookup"><span data-stu-id="d02cb-109">Experimental</span></span>](#experimental-packages)

## <a name="foundation-packages"></a><span data-ttu-id="d02cb-110">Foundation パッケージ</span><span class="sxs-lookup"><span data-stu-id="d02cb-110">Foundation Packages</span></span>

<span data-ttu-id="d02cb-111">混合現実 Toolkit Foundation は、Mixed Reality プラットフォーム間で共通の機能を活用するアプリケーションを有効にするパッケージのセットです。</span><span class="sxs-lookup"><span data-stu-id="d02cb-111">The Mixed Reality Toolkit Foundation is the set of packages that enable your application to leverage common functionality across Mixed Reality Platforms.</span></span> <span data-ttu-id="d02cb-112">これらのパッケージがリリースされ、ソース コードから Microsoft でサポートされている、 [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) GitHub 上の分岐。</span><span class="sxs-lookup"><span data-stu-id="d02cb-112">These packages are released and supported by Microsoft from source code in the [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) branch on GitHub.</span></span>

![MRTK Foundation パッケージ](images/mrtk-foundation.jpg)

<span data-ttu-id="d02cb-114">*Mixed Reality Toolkit Foundation パッケージ*</span><span class="sxs-lookup"><span data-stu-id="d02cb-114">*Mixed Reality Toolkit Foundation packages*</span></span>

<span data-ttu-id="d02cb-115">MRTK Foundation から成ります。</span><span class="sxs-lookup"><span data-stu-id="d02cb-115">The MRTK Foundation is comprised of:</span></span>

* [<span data-ttu-id="d02cb-116">コア パッケージ</span><span class="sxs-lookup"><span data-stu-id="d02cb-116">Core Package</span></span>](#core-package)
* [<span data-ttu-id="d02cb-117">プラットフォーム プロバイダー</span><span class="sxs-lookup"><span data-stu-id="d02cb-117">Platform Providers</span></span>](#platform-providers)
* [<span data-ttu-id="d02cb-118">システム サービス</span><span class="sxs-lookup"><span data-stu-id="d02cb-118">System Services</span></span>](#system-services)
* [<span data-ttu-id="d02cb-119">資産の機能</span><span class="sxs-lookup"><span data-stu-id="d02cb-119">Feature Assets</span></span>](#feature-assets)

<span data-ttu-id="d02cb-120">次のセクションでは、各カテゴリ内のパッケージの種類について説明します。</span><span class="sxs-lookup"><span data-stu-id="d02cb-120">The following sections describe the types of packages in each category.</span></span>

### <a name="core-package"></a><span data-ttu-id="d02cb-121">コア パッケージ</span><span class="sxs-lookup"><span data-stu-id="d02cb-121">Core Package</span></span>

<span data-ttu-id="d02cb-122">Core パッケージは、_必要_コンポーネント MRTK foundation のすべてのパッケージで依存関係として取得されます。</span><span class="sxs-lookup"><span data-stu-id="d02cb-122">The core package is a _required_ component and is taken as a dependency by all MRTK foundation packages.</span></span>

<span data-ttu-id="d02cb-123">MRTK Core パッケージは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d02cb-123">The MRTK Core package includes:</span></span>

* [<span data-ttu-id="d02cb-124">共通のインターフェイス、クラス、およびデータ型</span><span class="sxs-lookup"><span data-stu-id="d02cb-124">Common interfaces, classes and data types</span></span>](#common-interfaces-clases-and-data-types)
* [<span data-ttu-id="d02cb-125">MixedRealityToolkit シーンのコンポーネント</span><span class="sxs-lookup"><span data-stu-id="d02cb-125">MixedRealityToolkit scene component</span></span>](#mixedrealitytoolkit-scene-component)
* [<span data-ttu-id="d02cb-126">MRTK 標準シェーダー</span><span class="sxs-lookup"><span data-stu-id="d02cb-126">MRTK Standard Shader</span></span>](#mrtk-standard-shader)
* [<span data-ttu-id="d02cb-127">Unity 入力プロバイダー</span><span class="sxs-lookup"><span data-stu-id="d02cb-127">Unity Input Provider</span></span>](#unity-input-provider)
* [<span data-ttu-id="d02cb-128">パッケージの管理</span><span class="sxs-lookup"><span data-stu-id="d02cb-128">Package Management</span></span>](#package-management)

#### <a name="common-interfaces-classes-and-data-types"></a><span data-ttu-id="d02cb-129">共通のインターフェイス、クラス、およびデータ型</span><span class="sxs-lookup"><span data-stu-id="d02cb-129">Common interfaces, classes and data types</span></span>

<span data-ttu-id="d02cb-130">混合現実ツールキットのコア パッケージには、すべてのクラスとその他のすべてのコンポーネントで使用されるデータ型は、一般的なインターフェイスの定義が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d02cb-130">The Mixed Reality Toolkit Core package contains the definitions for all of the common interfaces, classes and data types that are used by all other components.</span></span> <span data-ttu-id="d02cb-131">アプリケーションがプラットフォーム間で最大限の互換性を有効にする、定義されたインターフェイスを通じてのみ MRTK コンポーネントをアクセスすることを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d02cb-131">It is highly recommended that applications access MRTK components exclusively through the defined interfaces to enable the highest level of compatibility across platforms.</span></span>

#### <a name="mixedrealitytoolkit-scene-component"></a><span data-ttu-id="d02cb-132">MixedRealityToolkit シーンのコンポーネント</span><span class="sxs-lookup"><span data-stu-id="d02cb-132">MixedRealityToolkit scene component</span></span>

<span data-ttu-id="d02cb-133">MixedRealityToolkit シーンのコンポーネントは、Mixed Reality ツールキットの 1 つの一元的なリソース マネージャーです。</span><span class="sxs-lookup"><span data-stu-id="d02cb-133">The MixedRealityToolkit scene component is the single, centralized resource manager for the Mixed Reality Toolkit.</span></span> <span data-ttu-id="d02cb-134">このコンポーネントはロード プラットフォームおよびサービス モジュールの有効期間を管理し、それらの構成設定にアクセスするシステム リソースを提供します。</span><span class="sxs-lookup"><span data-stu-id="d02cb-134">This component loads and manages the lifespan of the platform and service modules and provides resources for the systems to access their configuration settings.</span></span> 

#### <a name="mrtk-standard-shader"></a><span data-ttu-id="d02cb-135">MRTK 標準シェーダー</span><span class="sxs-lookup"><span data-stu-id="d02cb-135">MRTK Standard Shader</span></span>

<span data-ttu-id="d02cb-136">MRTK 標準シェーダーは、MRTK によって提供されるマテリアルのほぼすべての基盤を提供します。</span><span class="sxs-lookup"><span data-stu-id="d02cb-136">The MRTK Standard Shader provides the basis for virtually all of the materials provided by the MRTK.</span></span> <span data-ttu-id="d02cb-137">このシェーダーは、非常に柔軟で、さまざまな MRTK がサポートされているプラットフォーム向けに最適化します。</span><span class="sxs-lookup"><span data-stu-id="d02cb-137">This shader is extremely flexible and optimized for the variety of platforms on which MRTK is supported.</span></span> <span data-ttu-id="d02cb-138">_高_アプリケーションの資料が最適なパフォーマンス MRTK 標準シェーダーを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d02cb-138">It is _highly_ recommended that your application's materials use the MRTK standard shader for optimal performance.</span></span>

#### <a name="unity-input-provider"></a><span data-ttu-id="d02cb-139">Unity 入力プロバイダー</span><span class="sxs-lookup"><span data-stu-id="d02cb-139">Unity Input Provider</span></span>

<span data-ttu-id="d02cb-140">Unity の入力プロバイダーは、ゲーム コント ローラーや 3D 空間マウス、タッチ スクリーンなどの一般的な入力デバイスへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="d02cb-140">The Unity Input Provider provides access to common input devices such as game controllers, touch screens and a 3D spatial mouse.</span></span>

#### <a name="package-management"></a><span data-ttu-id="d02cb-141">パッケージ管理</span><span class="sxs-lookup"><span data-stu-id="d02cb-141">Package Management</span></span>

<span data-ttu-id="d02cb-142">_近日公開_</span><span class="sxs-lookup"><span data-stu-id="d02cb-142">_Coming soon_</span></span>

<span data-ttu-id="d02cb-143">混合現実ツールキットのコア パッケージは、検出およびオプションの foundation、拡張機能および MRTK の実験用のパッケージを管理するためのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="d02cb-143">The Mixed Reality Toolkit Core package provides support for discovering and managing the optional foundation, extension and experimental MRTK packages.</span></span>

### <a name="platform-providers"></a><span data-ttu-id="d02cb-144">プラットフォーム プロバイダー</span><span class="sxs-lookup"><span data-stu-id="d02cb-144">Platform Providers</span></span>

<span data-ttu-id="d02cb-145">MRTK プラットフォーム プロバイダー パッケージは、Mixed Reality ハードウェアをターゲットに混合現実 Toolkit とプラットフォームの機能を有効にするコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="d02cb-145">The MRTK Platform Provider packages are the components that enable the Mixed Reality Toolkit to target Mixed Reality hardware and platform functionality.</span></span>

<span data-ttu-id="d02cb-146">サポートされているプラットフォームは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d02cb-146">Supported platforms include:</span></span>

* [<span data-ttu-id="d02cb-147">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="d02cb-147">Windows Mixed Reality</span></span>](#windows-mixed-reality)
* [<span data-ttu-id="d02cb-148">OpenVR</span><span class="sxs-lookup"><span data-stu-id="d02cb-148">OpenVR</span></span>](#openvr)
* [<span data-ttu-id="d02cb-149">Windows Voice</span><span class="sxs-lookup"><span data-stu-id="d02cb-149">Windows Voice</span></span>](#windows-voice)

#### <a name="windows-mixed-reality"></a><span data-ttu-id="d02cb-150">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="d02cb-150">Windows Mixed Reality</span></span>

<span data-ttu-id="d02cb-151">Windows Mixed Reality パッケージでは、Microsoft HoloLens と Windows Mixed Reality 没入型のデバイスのサポートも提供します。</span><span class="sxs-lookup"><span data-stu-id="d02cb-151">The Windows Mixed Reality package provides support for Microsoft HoloLens and Windows Mixed Reality Immersive devices.</span></span> <span data-ttu-id="d02cb-152">パッケージに含まれるすべてのプラットフォームのサポートを含みます。</span><span class="sxs-lookup"><span data-stu-id="d02cb-152">The package contains full platform support, including:</span></span>

* <span data-ttu-id="d02cb-153">視線の先を対象とします。</span><span class="sxs-lookup"><span data-stu-id="d02cb-153">Gaze targeting</span></span>
* <span data-ttu-id="d02cb-154">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="d02cb-154">Gestures</span></span>
* <span data-ttu-id="d02cb-155">Windows Mixed Reality モーションのコント ローラー</span><span class="sxs-lookup"><span data-stu-id="d02cb-155">Windows Mixed Reality Motion controllers</span></span>
* <span data-ttu-id="d02cb-156">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="d02cb-156">Spatial Mapping</span></span>

#### <a name="openvr"></a><span data-ttu-id="d02cb-157">OpenVR</span><span class="sxs-lookup"><span data-stu-id="d02cb-157">OpenVR</span></span>

<span data-ttu-id="d02cb-158">OpenVR パッケージでは、OpenVR プラットフォームを使用してデバイスのハードウェアおよびプラットフォームのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="d02cb-158">The OpenVR package provides hardware and platform support for devices using the OpenVR platform.</span></span>

#### <a name="windows-voice"></a><span data-ttu-id="d02cb-159">Windows Voice</span><span class="sxs-lookup"><span data-stu-id="d02cb-159">Windows Voice</span></span>

<span data-ttu-id="d02cb-160">Windows 音声パッケージは、Microsoft Windows 10 デバイスで、キーワード認識とディクテーション機能のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="d02cb-160">The Windows Voice package provides support for keyword recognition and dictation functionality on Microsoft Windows 10 devices.</span></span>

### <a name="system-services"></a><span data-ttu-id="d02cb-161">システム サービス</span><span class="sxs-lookup"><span data-stu-id="d02cb-161">System Services</span></span>

<span data-ttu-id="d02cb-162">コア プラットフォームのサービスは、システム サービス パッケージで提供されます。</span><span class="sxs-lookup"><span data-stu-id="d02cb-162">Core platform services are provided in system service packages.</span></span> <span data-ttu-id="d02cb-163">これらのパッケージには、Mixed Reality Toolkit の既定の実装で定義されているシステム サービスのインターフェイスが含まれて、 [core](#core-package)パッケージ。</span><span class="sxs-lookup"><span data-stu-id="d02cb-163">These packages contain the Mixed Reality Toolkit's default implementations of the system service interfaces, defined in the [core](#core-package) package.</span></span>

<span data-ttu-id="d02cb-164">MRTK foundation には、次のシステム サービスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d02cb-164">The MRTK foundation includes the following system services:</span></span>

* [<span data-ttu-id="d02cb-165">システムの境界</span><span class="sxs-lookup"><span data-stu-id="d02cb-165">Boundary System</span></span>](#boundary-system)
* [<span data-ttu-id="d02cb-166">診断システム</span><span class="sxs-lookup"><span data-stu-id="d02cb-166">Diagnostic System</span></span>](#diagnostic-system)
* [<span data-ttu-id="d02cb-167">入力システム</span><span class="sxs-lookup"><span data-stu-id="d02cb-167">Input System</span></span>](#input-system)
* [<span data-ttu-id="d02cb-168">空間認識システム</span><span class="sxs-lookup"><span data-stu-id="d02cb-168">Spatial Awareness System</span></span>](#spatial-awareness-system)
* [<span data-ttu-id="d02cb-169">テレポート システム</span><span class="sxs-lookup"><span data-stu-id="d02cb-169">Teleport System</span></span>](#teleport-system)

#### <a name="boundary-system"></a><span data-ttu-id="d02cb-170">システムの境界</span><span class="sxs-lookup"><span data-stu-id="d02cb-170">Boundary System</span></span>

<span data-ttu-id="d02cb-171">MRTK 境界システムに仮想現実に関するデータを提供する playspace します。</span><span class="sxs-lookup"><span data-stu-id="d02cb-171">The MRTK Boundary System provides data about the to virtual reality playspace.</span></span> <span data-ttu-id="d02cb-172">対象のユーザーが、境界を構成しているシステムでは、システムは、床面、四角形の playspace、追跡対象の領域、および提供できます。</span><span class="sxs-lookup"><span data-stu-id="d02cb-172">On systems for which the user has configured the boundary, the system can provide a floor plane, rectangular playspace, tracked area, and more.</span></span>

#### <a name="diagnostic-system"></a><span data-ttu-id="d02cb-173">診断システム</span><span class="sxs-lookup"><span data-stu-id="d02cb-173">Diagnostic System</span></span>

<span data-ttu-id="d02cb-174">MRTK 診断システムでは、アプリケーションのエクスペリエンス内でリアルタイムのパフォーマンス データを提供します。</span><span class="sxs-lookup"><span data-stu-id="d02cb-174">The MRTK Diagnostic System provides real-time performance data within your application experience.</span></span> <span data-ttu-id="d02cb-175">概要、アプリケーションを使用すると、フレーム レート、プロセッサ時間およびその他の主要なパフォーマンス メトリックを表示することになります。</span><span class="sxs-lookup"><span data-stu-id="d02cb-175">At a glace, you will be able to view frame rate, processor time and other key performance metrics as you use your application.</span></span>

#### <a name="input-system"></a><span data-ttu-id="d02cb-176">入力システム</span><span class="sxs-lookup"><span data-stu-id="d02cb-176">Input System</span></span>

<span data-ttu-id="d02cb-177">MRTK 入力システムには、アプリケーションにアクセスするには、クロス プラットフォームの方法で入力をユーザーのアクションを指定する最も適切なボタンとターゲット コント ローラーの軸にこれらのアクションを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="d02cb-177">The MRTK Input Systems enables applications to access input in a cross platform manner by specifying user actions and assigning those actions to the most appropriate buttons and axes on target controllers.</span></span>

#### <a name="spatial-awareness-system"></a><span data-ttu-id="d02cb-178">空間認識システム</span><span class="sxs-lookup"><span data-stu-id="d02cb-178">Spatial Awareness System</span></span>

<span data-ttu-id="d02cb-179">MRTK 空間認識システムには、Microsoft HoloLens などのデバイスから実際の環境のデータにアクセスができるようにします。</span><span class="sxs-lookup"><span data-stu-id="d02cb-179">The MRTK Spatial Awareness System enables access to real-world environmental data from devices such as the Microsoft HoloLens.</span></span>

#### <a name="teleport-system"></a><span data-ttu-id="d02cb-180">テレポート システム</span><span class="sxs-lookup"><span data-stu-id="d02cb-180">Teleport System</span></span>

<span data-ttu-id="d02cb-181">MRTK テレポート システムは、仮想現実 locomotion サポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="d02cb-181">The MRTK Teleport System provides virtual reality locomotion support.</span></span>

### <a name="feature-assets"></a><span data-ttu-id="d02cb-182">資産の機能</span><span class="sxs-lookup"><span data-stu-id="d02cb-182">Feature Assets</span></span>

<span data-ttu-id="d02cb-183">機能の資産は、Unity の資産とスクリプトとして提供される関連する機能のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="d02cb-183">Feature Assets are collections of related functionality delivered as Unity assets and scripts.</span></span> <span data-ttu-id="d02cb-184">これらの機能のいくつか挙げます。</span><span class="sxs-lookup"><span data-stu-id="d02cb-184">Some of these features include:</span></span>

* <span data-ttu-id="d02cb-185">ユーザー インターフェイス コントロール</span><span class="sxs-lookup"><span data-stu-id="d02cb-185">User Interface Controls</span></span>
* <span data-ttu-id="d02cb-186">Standard Assets</span><span class="sxs-lookup"><span data-stu-id="d02cb-186">Standard Assets</span></span>
* <span data-ttu-id="d02cb-187">more</span><span class="sxs-lookup"><span data-stu-id="d02cb-187">more</span></span>

## <a name="extension-packages"></a><span data-ttu-id="d02cb-188">拡張機能パッケージ</span><span class="sxs-lookup"><span data-stu-id="d02cb-188">Extension Packages</span></span>

<span data-ttu-id="d02cb-189">MRTK 拡張機能パッケージは、Mixed Reality ツールキットの機能強化のための拡張とを Microsoft およびコミュニティによって作成されたパッケージのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="d02cb-189">MRTK Extension packages are a collection of packages written by Microsoft and the Community that extend and enhance the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="d02cb-190">拡張機能の作成者は、必要な依存関係の状態、Mixed Reality Toolkit に互換性があるパッケージをマーク、ライセンスを提供およびされステートメントがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="d02cb-190">Extension authors will state any required dependencies, mark the package as compatible with the Mixed Reality Toolkit and provide licensing and support statements.</span></span>

<span data-ttu-id="d02cb-191">拡張機能パッケージには、新機能と新しいプラットフォームのサポートを提供できます。</span><span class="sxs-lookup"><span data-stu-id="d02cb-191">Extension packages may provide new features and new platform support.</span></span> <span data-ttu-id="d02cb-192">時間の経過と共に拡張機能が、アシスタンスと作成者の承認に移行 MRTK Foundation 時点でそれらがリリースされ、Microsoft でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d02cb-192">Over time, extensions may, with the assistance and approval of the authors, be migrated into the MRTK Foundation at which time they will be released and supported by Microsoft.</span></span>

![MRTK 拡張機能パッケージ](images/mrtk-extensions.jpg)

<span data-ttu-id="d02cb-194">*Mixed Reality Toolkit の拡張機能パッケージ*</span><span class="sxs-lookup"><span data-stu-id="d02cb-194">*Mixed Reality Toolkit Extension packages*</span></span>

## <a name="experimental-packages"></a><span data-ttu-id="d02cb-195">実験用のパッケージ</span><span class="sxs-lookup"><span data-stu-id="d02cb-195">Experimental Packages</span></span>

<span data-ttu-id="d02cb-196">実験用のパッケージは、フライトのプロトタイプ機能、プレリリース版および魅力的な新しいアイデアに機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="d02cb-196">Experimental packages provide the ability to flight prototype features, pre-releases and exciting new ideas.</span></span> <span data-ttu-id="d02cb-197">最も実験用のパッケージの目的は、新しい機能を試すと、お客様の関心をゲージにです。</span><span class="sxs-lookup"><span data-stu-id="d02cb-197">The goal of most experimental packages is to try something new and to gauge customer interest.</span></span> <span data-ttu-id="d02cb-198">多くの場合、プロトタイプ作成とテスト フェーズが完了すると、実験用のパッケージが拡張機能として再リリースがすべてではない場合。</span><span class="sxs-lookup"><span data-stu-id="d02cb-198">Many, though not all, experimental packages will be re-released as extensions once the prototyping and testing phase completes.</span></span>

![MRTK 実験用のパッケージ](images/mrtk-experimental.jpg)

<span data-ttu-id="d02cb-200">*Mixed Reality Toolkit 実験的なパッケージ*</span><span class="sxs-lookup"><span data-stu-id="d02cb-200">*Mixed Reality Toolkit Experimental packages*</span></span>

## <a name="conclusion"></a><span data-ttu-id="d02cb-201">まとめ</span><span class="sxs-lookup"><span data-stu-id="d02cb-201">Conclusion</span></span>

<span data-ttu-id="d02cb-202">された炎のプロジェクトに含まれる不要なコンポーネントを必要とせず、エクスペリエンスに機能を構築するため、クリーンで単純なメソッドを有効にするのには、Mixed Reality Toolkit パッケージとパッケージ管理システムが設計されています。</span><span class="sxs-lookup"><span data-stu-id="d02cb-202">The Mixed Reality Toolkit packages and package management system are designed to enable a clean and simple method for you to additively build features into your experiences without requiring unnecessary components to be included into the project.</span></span>

<span data-ttu-id="d02cb-203">時間の経過と共にパッケージ管理のサポートが追加され Mixed Reality Toolkit 内で強化されています。</span><span class="sxs-lookup"><span data-stu-id="d02cb-203">Over time, package management support will be added and enhanced within the Mixed Reality Toolkit.</span></span> <span data-ttu-id="d02cb-204">フィードバックがあるプログラムへの参加を希望するかを参照してください、 [Mixed Reality Toolkit プロジェクト](https://github.com/Microsoft/MixedRealityToolkit-Unity)GitHub でします。</span><span class="sxs-lookup"><span data-stu-id="d02cb-204">If you have feedback or wish to get involved, please visit the [Mixed Reality Toolkit project](https://github.com/Microsoft/MixedRealityToolkit-Unity) on GitHub.</span></span> 

## <a name="see-also"></a><span data-ttu-id="d02cb-205">関連項目</span><span class="sxs-lookup"><span data-stu-id="d02cb-205">See also</span></span>

* [<span data-ttu-id="d02cb-206">MixedRealityToolkit-Unity (GitHub)</span><span class="sxs-lookup"><span data-stu-id="d02cb-206">MixedRealityToolkit-Unity (GitHub)</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)

