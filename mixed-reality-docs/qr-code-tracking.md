---
title: QR コードの追跡
description: QR コードを Windows Mixed Reality 没入型 (VR) ヘッドセットの追跡を有効にする方法について説明し、VR アプリで機能を実装します。
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: vr、lbe、場所ベースのエンターテイメント、vr アーケード ゲームのイマーシブなアーケード ゲーム qr、qr コード
ms.openlocfilehash: 465056cf645a8b9dc9e0e2d3f9dacf887df67c52
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829982"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="0e6d7-104">QR コードの追跡</span><span class="sxs-lookup"><span data-stu-id="0e6d7-104">QR code tracking</span></span>

<span data-ttu-id="0e6d7-105">QR コードの追跡は、没入型の (VR) ヘッドセットの Windows Mixed Reality ドライバーに実装されます。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-105">QR code tracking is implemented in the Windows Mixed Reality driver for immersive (VR) headsets.</span></span> <span data-ttu-id="0e6d7-106">ヘッドセット ドライバーで QR コードの追跡ツールを有効にすると、ヘッドセットは QR コードのスキャンし、目的のアプリに報告されます。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-106">By enabling the QR code tracker in the headset driver, the headset scans for QR codes and they are reported to interested apps.</span></span> <span data-ttu-id="0e6d7-107">この機能としての使用のみ、 [Windows 10 年 2018年 10 月 Update (RS5 とも呼ばれます)](release-notes-october-2018.md)します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-107">This feature is only available as of the [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span>

>[!NOTE]
><span data-ttu-id="0e6d7-108">この記事のコード スニペットは現在の使用を示すC++/CX ではなく c++ 17 に準拠していませんC++/WinRT で使用するため、 [ C++ holographic プロジェクト テンプレート](creating-a-holographic-directx-project.md)します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="0e6d7-109">概念は、同等のC++/WinRT のプロジェクトがコードに変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="device-support"></a><span data-ttu-id="0e6d7-110">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="0e6d7-110">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="0e6d7-111"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="0e6d7-111"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="0e6d7-112"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="0e6d7-112"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="0e6d7-113"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="0e6d7-113"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="0e6d7-114">QR コードの追跡</span><span class="sxs-lookup"><span data-stu-id="0e6d7-114">QR code tracking</span></span></td>
        <td><span data-ttu-id="0e6d7-115">❌</span><span class="sxs-lookup"><span data-stu-id="0e6d7-115">❌</span></span></td>
        <td><span data-ttu-id="0e6d7-116">✔️</span><span class="sxs-lookup"><span data-stu-id="0e6d7-116">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a><span data-ttu-id="0e6d7-117">有効/無効の QR コードの追跡、ヘッドセットを</span><span class="sxs-lookup"><span data-stu-id="0e6d7-117">Enabling and disabling QR code tracking for your headset</span></span>
<span data-ttu-id="0e6d7-118">注:このセクションではのみ有効です[Windows 10 年 2018年 10 月 Update (RS5 とも呼ばれます)](release-notes-october-2018.md)します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-118">Note: This section is only valid for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span> <span data-ttu-id="0e6d7-119">19 h 1 ビルド以降からこれを行うことはありません。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-119">From 19h1 builds onwards you will not have to do this.</span></span>
<span data-ttu-id="0e6d7-120">追跡するには、QR コードを利用する mixed reality アプリを開発している場合も、これらのアプリのいずれかのお客様は、QR コードの履歴をヘッドセットのドライバーを手動で有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-120">Whether you're developing a mixed reality app that will leverage QR code tracking, or you're a customer of one of these apps, you'll need to manually turn on QR code tracking in your headset's driver.</span></span>

<span data-ttu-id="0e6d7-121">**QR コードの履歴を有効にする**没入型の (VR) ヘッドセットの。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-121">In order to **turn on QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="0e6d7-122">お使いの PC で複合現実のポータル アプリを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-122">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="0e6d7-123">お使いの PC からヘッドセットを取り外します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-123">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="0e6d7-124">コマンド プロンプトで次のスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-124">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. <span data-ttu-id="0e6d7-125">Pc、ヘッドセットを再接続します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-125">Reconnect your headset to your PC.</span></span>

<span data-ttu-id="0e6d7-126">**QR コードの追跡をオフに**没入型の (VR) ヘッドセットの。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-126">In order to **turn off QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="0e6d7-127">お使いの PC で複合現実のポータル アプリを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-127">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="0e6d7-128">お使いの PC からヘッドセットを取り外します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-128">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="0e6d7-129">コマンド プロンプトで次のスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-129">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. <span data-ttu-id="0e6d7-130">Pc、ヘッドセットを再接続します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-130">Reconnect your headset to your PC.</span></span> <span data-ttu-id="0e6d7-131">これにより、検出された、QR コード「以外の場所を特定できる」</span><span class="sxs-lookup"><span data-stu-id="0e6d7-131">This will make any discovered QR codes "non-locatable."</span></span>

## <a name="printing-codes"></a><span data-ttu-id="0e6d7-132">印刷コード</span><span class="sxs-lookup"><span data-stu-id="0e6d7-132">Printing codes</span></span>

<span data-ttu-id="0e6d7-133">何よりもまず、 [QR コードの spec](https://www.qrcode.com/en/howto/code.html)という"QR コード シンボルの領域が必要です、余白または「quiet ゾーン」を使用するのには、します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-133">First and foremost, the [spec for QR codes](https://www.qrcode.com/en/howto/code.html) says "The QR Code symbol area requires a margin or "quiet zone" around it to be used.</span></span> <span data-ttu-id="0e6d7-134">余白は、何も出力されませんシンボルに関する明確領域です。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-134">The margin is a clear area around a symbol where nothing is printed.</span></span> <span data-ttu-id="0e6d7-135">QR コードが必要です、シンボルのすべての辺に 4 モジュール優勢。"</span><span class="sxs-lookup"><span data-stu-id="0e6d7-135">QR Code requires a four-module wide margin at all sides of a symbol."</span></span> <span data-ttu-id="0e6d7-136">これは、モジュールのコードに黒い四角を 1 つのサイズの 4 倍の各側で、幅がある必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-136">This needs to have a width, on every side, of four times the size of a module - a single black square in the code.</span></span> <span data-ttu-id="0e6d7-137">仕様のページには、QR コードを印刷し、特定サイズの QR コードのために必要な領域を把握する方法に関するアドバイスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-137">The spec page contains advice on how to print QR codes and figure out the area required to make a certain sized QR code.</span></span>

<span data-ttu-id="0e6d7-138">現在 QR コードの品質の検出は、さまざまな照明と背景を受けやすくなります。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-138">Currently QR code detection quality is susceptible to varying illumination and backdrop.</span></span> <span data-ttu-id="0e6d7-139">この、照明に注意してくださいし、適切なコードを印刷します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-139">To combat this, note your illumination and print the appropriate code.</span></span> <span data-ttu-id="0e6d7-140">特に明るい光のシーンでは、グレーの背景の上に黒のコードを印刷します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-140">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="0e6d7-141">で、光量不足シーン、白のしくみは黒です。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-141">Under a low-light scene, black on white works.</span></span> <span data-ttu-id="0e6d7-142">同様に、コードに背景が特にダークの場合は、お試しください灰色のコードには黒を検出、レートが低い場合。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-142">Likewise, if the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="0e6d7-143">それ以外の場合、背景が明るいの場合は、正規のコードは問題なく機能する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-143">Otherwise, if the backdrop is lighter, a regular code should work fine.</span></span>

## <a name="qrtracking-api"></a><span data-ttu-id="0e6d7-144">QRTracking API</span><span class="sxs-lookup"><span data-stu-id="0e6d7-144">QRTracking API</span></span>

<span data-ttu-id="0e6d7-145">QRTracking プラグインでは、QR コードを追跡するための Api を公開します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-145">The QRTracking plugin exposes the APIs for QR code tracking.</span></span> <span data-ttu-id="0e6d7-146">プラグインを使用する次の種類を使用する必要があります、 *QRCodesTrackerPlugin*名前空間。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-146">To use the plugin, you will need to use the following types from the *QRCodesTrackerPlugin* namespace.</span></span>

```cs
 // QRTracker plugin namespace
 namespace QRCodesTrackerPlugin
 {
    // Encapsulates information about a labeled QR code element.
    public class QRCode
    {        
        // Unique id that identifies this QR code for this session.
        public Guid Id { get; private set; }
           
        // Version of this QR code.
        public Int32 Version { get; private set; }
        
        // PhysicalSizeMeters of this QR code.
        public float PhysicalSizeMeters { get; private set; }
        
        // QR code Data.
        public string Code { get; private set; }
        
        // QR code DataStream this is the error corrected data stream
        public Byte[] CodeStream { get; private set; }
        
        // QR code last detected QPC ticks.
        public Int64 LastDetectedQPCTicks { get; private set; }
    };
    
    // The type of a QR Code added event.
    public class QRCodeAddedEventArgs
    {   
        // Gets the QR Code that was added
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code removed event.
    public class QRCodeRemovedEventArgs
    {
        // Gets the QR Code that was removed.
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code updated event.
    public class QRCodeUpdatedEventArgs
    {
        // Gets the QR Code that was updated.
        public QRCode Code { get; private set; }
    };
    
    // A callback for handling the QR Code added event.
    public delegate void QRCodeAddedHandler(QRCodeAddedEventArgs args);
    
    // A callback for handling the QR Code removed event.
    public delegate void QRCodeRemovedHandler(QRCodeRemovedEventArgs args);
    
    // A callback for handling the QR Code updated event.
    public delegate void QRCodeUpdatedHandler(QRCodeUpdatedEventArgs args);
    
    // Enumerates the possible results of a start of QRTracker.
    public enum QRTrackerStartResult
    {
        // The start has succeeded.
        Success = 0,
        
        //  The currently no device is connected.
        DeviceNotConnected = 1,
        
        // The QRTracking Feature is not supported by the current HMD driver
        // systems
        FeatureNotSupported = 2,
        
        // The access is denide. Administrator needs to enable QR tracker feature.
        AccessDenied = 3,
    };
    
    // QRTracker
    public class QRTracker
    {
        // Constructs a new QRTracker.
        public QRTracker(){}
        
        // Gets the QRTracker.
        public static QRTracker Get()
        {
            return new QRTracker();
        }
        
        // Start the QRTracker. Returns QRTrackerStartResult.
        public QRTrackerStartResult Start()
        {
            throw new NotImplementedException();
        }
        
        // Stops tracking QR codes.
        public void Stop() {}

        // Not Implemented
        Windows.Foundation.Collections.IVector<QRCode> GetList() { throw new NotImplementedException(); }
        
        // Event representing the addition of a QR Code.
        public event QRCodeAddedHandler Added = delegate { };
        
        // Event representing the removal of a QR Code.
        public event QRCodeRemovedHandler Removed = delegate { };
        
        // Event representing the update of a QR Code.
        public event QRCodeUpdatedHandler Updated = delegate { };
    };
}
```

## <a name="implementing-qr-code-tracking-in-unity"></a><span data-ttu-id="0e6d7-147">Unity での追跡、QR コードを実装します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-147">Implementing QR code tracking in Unity</span></span>

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a><span data-ttu-id="0e6d7-148">Unity シーン MRTK (Mixed Reality Toolkit) のサンプルします。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-148">Sample Unity scenes in MRTK (Mixed Reality Toolkit)</span></span>

<span data-ttu-id="0e6d7-149">Mixed Reality toolkit QR 追跡 API を使用する方法の例が見つかります[GitHub サイト](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-149">You can find an example for how to use the QR Tracking API in the Mixed Reality Toolkit [GitHub site](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).</span></span>

<span data-ttu-id="0e6d7-150">MRTK では、使用状況の追跡 QR simpilify に必要なスクリプトを実装しました。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-150">MRTK has implemented the needed scripts to simpilify the QR tracking usage.</span></span> <span data-ttu-id="0e6d7-151">QR 追跡アプリを開発するために必要なすべての資産は、"QRTracker"フォルダーには。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-151">All necessary assets to develop QR tracking apps are in the "QRTracker" folder.</span></span> <span data-ttu-id="0e6d7-152">2 つのシーンがある: 1 つ目が検出され、2 つ目は QR コードにアタッチされている座標系を使用して、ホログラムを表示する方法を示します、単に QR コードの詳細を表示するサンプルに示します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-152">There are two scenes: the first is a sample to simply show details of the QR codes as they are detected, and the second demonstrates how to use the coordinate system attached to the QR code to display holograms.</span></span>
<span data-ttu-id="0e6d7-153">Prefab"QRScanner"QRCodes を使用する処理に必要なすべてのスクリプトを追加します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-153">There is a prefab "QRScanner" which added all the necessary scripts to the scenes to use QRCodes.</span></span> <span data-ttu-id="0e6d7-154">QRCodeManager スクリプトは、QRCode API を実装するシングルトン クラスです。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-154">The script QRCodeManager is a singleton class that implements the QRCode API.</span></span> <span data-ttu-id="0e6d7-155">これは、シーンに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-155">This needs to be added to your scene.</span></span> <span data-ttu-id="0e6d7-156">スクリプト"AttachToQRCode"を使用して、QR コードの座標系にホログラムをアタッチする、このスクリプトは、ホログラムのいずれかに追加できます。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-156">The script "AttachToQRCode" is used to attach holograms to the QR Code coordinate systems, this script can be added to any of your holograms.</span></span> <span data-ttu-id="0e6d7-157">"SpatialGraphCoordinateSystem"は、QRCode 座標系を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-157">The "SpatialGraphCoordinateSystem" shows how to use the QRCode coordinate system.</span></span> <span data-ttu-id="0e6d7-158">としてこれらのスクリプトを使用できるのプロジェクトでシーンまたは書き込める独自直接プラグインを使用して、前述のようです。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-158">These scripts can be used as-is in your project scenes or you can write your own directly using the plugin as described above.</span></span>

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a><span data-ttu-id="0e6d7-159">QR コードが Unity MRTK なしで追跡を実装します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-159">Implementing QR code tracking in Unity without MRTK</span></span>

<span data-ttu-id="0e6d7-160">MRTK に依存することがなく、Unity で QR 追跡 API を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-160">You can also use the QR Tracking API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="0e6d7-161">API を使用するためには、次の命令を使用してプロジェクトを準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-161">In order to use the API, you will need to prepare your project with the following instruction:</span></span>

1. <span data-ttu-id="0e6d7-162">名前の unity プロジェクトの assets フォルダーに新しいフォルダーを作成します。「プラグイン」されます。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-162">Create a new folder in the assets folder of your unity project with the name: "Plugins".</span></span>
2. <span data-ttu-id="0e6d7-163">すべての必要なファイル コピー[このフォルダー](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins)作成したローカルの「プラグイン」フォルダーにします。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-163">Copy all the required files from [this folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) into the local "Plugins" folder you just created.</span></span>
3. <span data-ttu-id="0e6d7-164">スクリプトを追跡する QR を使用することができます、 [MRTK scripts フォルダー](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts)または独自に作成します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-164">You can use the QR tracking scripts in the [MRTK scripts folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) or write your own.</span></span>
<span data-ttu-id="0e6d7-165">注:これらのプラグインは、専用です[Windows 10 年 2018年 10 月 Update (RS5 とも呼ばれます)](release-notes-october-2018.md)をビルドします。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-165">Note: These plugins are only for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md) builds.</span></span> <span data-ttu-id="0e6d7-166">プラグインは、次の windows リリースで更新されます。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-166">The plugins will be updated with the next windows release.</span></span> <span data-ttu-id="0e6d7-167">実験的な現在のプラグイン、windows の将来のバージョンに対しては機能しません。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-167">The current plugins were experimental and will not work for future version of the windows.</span></span> <span data-ttu-id="0e6d7-168">次の windows リリースから使用できる新しいプラグインが発行されますれされません下位互換および RS5 では動作しません)。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-168">New plugins will be published which can be used from next windows release and they will not be backwards compatable and will not work with RS5).</span></span>

## <a name="implementing-qr-code-tracking-in-directx"></a><span data-ttu-id="0e6d7-169">QR コードを DirectX での追跡を実装します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-169">Implementing QR code tracking in DirectX</span></span>

<span data-ttu-id="0e6d7-170">使用するには、QRTrackingPlugin Visual Studio では、.winmd に、QRTrackingPlugin の参照を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-170">To use the QRTrackingPlugin in Visual Studio, you will need to add reference of the QRTrackingPlugin to the .winmd.</span></span> <span data-ttu-id="0e6d7-171">検索することができます、[ファイルにサポートされているプラットフォームをここで必要な](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA)します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-171">You can find the [required files for supported platforms here](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span></span>

```cpp
// MyClass.h
public ref class MyClass
{
    private:
      QRCodesTrackerPlugin::QRTracker^ m_qrtracker;
      // Handlers
      void OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args);
      void OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args);
      void OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args);
    ..
};
```

```cpp
// MyClass.cpp
MyClass::MyClass()
{
    // Create the tracker and register the callbacks
    m_qrtracker = ref new QRCodesTrackerPlugin::QRTracker();
    m_qrtracker->Added += ref new QRCodesTrackerPlugin::QRCodeAddedHandler(this, &OnAddedQRCode);
    m_qrtracker->Updated += ref new QRCodesTrackerPlugin::QRCodeUpdatedHandler(this, &OnUpdatedQRCode);
    m_qrtracker->Removed += ref new QRCodesTrackerPlugin::QRCodeRemovedHandler(this, &QOnRemovedQRCode);

    // Start the tracker
    if (m_qrtracker->Start() != QRCodesTrackerPlugin::QRTrackerStartResult::Success)
    {
      // Handle the failure
      // It can fail for multiple reasons and can be handled properly 
    }
}

void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    // use args->Code add to own list  
}

void MyClass::OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args)
{
    // use args->Code update the existing one with the new one in own list 
}

void MyClass::OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args)
{
    // use args->Code remove from own list.
}
```

## <a name="getting-a-coordinate-system"></a><span data-ttu-id="0e6d7-172">座標系を取得します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-172">Getting a coordinate system</span></span>

<span data-ttu-id="0e6d7-173">左上の高速検出正方形の左上隅にある QR コードに揃えて配置右手座標系を定義します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-173">We define a right-hand coordinate system aligned with the QR code at the top left corner of the fast detection square in the top left.</span></span> <span data-ttu-id="0e6d7-174">座標系は、以下に示します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-174">The coordinate system is shown below.</span></span> <span data-ttu-id="0e6d7-175">(非表示)、ホワイト ペーパーには z 軸が指しているが、Unity、z 軸は、用紙と左手座標系。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-175">The Z-axis is pointing into the paper (not shown), but in Unity the z-axis is out of the paper and left-handed.</span></span>

<span data-ttu-id="0e6d7-176">示すように配置される、SpatialCoordinateSystem が定義されます。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-176">A SpatialCoordinateSystem is defined that is aligned as shown.</span></span> <span data-ttu-id="0e6d7-177">この座標系は、API を使用して、プラットフォームから取得できます*Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-177">This coordinate system can be obtained from the platform using the API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.</span></span>

![QR コードの座標系](images/Qr-coordinatesystem.png) 

<span data-ttu-id="0e6d7-179">QRCode から ^ コード オブジェクトを次のコードは、四角形を作成して QR 座標系に配置する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-179">From QRCode^ Code object, the following code shows how to create a rectangle and put it in QR coordinate system:</span></span>

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> SpatialStageManager::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0,  0, 0 };
    vertices[1] = { width,  0, 0 };
    vertices[2] = { width,  height, 0 };
    vertices[3] = { 0,  height, 0 };

    return vertices;
}
```

<span data-ttu-id="0e6d7-180">物理サイズを使用すると、QR 四角形を作成します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-180">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

<span data-ttu-id="0e6d7-181">座標系は、QR コードを描画するか、場所にホログラムをアタッチを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-181">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

<span data-ttu-id="0e6d7-182">*QRCodesTrackerPlugin::QRCodeAddedHandler*は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-182">Altogether, your *QRCodesTrackerPlugin::QRCodeAddedHandler* may look something like this:</span></span>

```cpp
void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    std::vector<float3> qrVertices = CreateRectangle(args->Code->PhysicalSizeMeters, args->Code->PhysicalSizeMeters);
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem =  Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(args->Code->Id);
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            reinterpret_cast<std::vector<XMFLOAT3>&>(qrVertices),
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="troubleshooting-and-faq"></a><span data-ttu-id="0e6d7-183">トラブルシューティングとよく寄せられる質問</span><span class="sxs-lookup"><span data-stu-id="0e6d7-183">Troubleshooting and FAQ</span></span>

<span data-ttu-id="0e6d7-184">**一般的なトラブルシューティング**</span><span class="sxs-lookup"><span data-stu-id="0e6d7-184">**General troubleshooting**</span></span>

* <span data-ttu-id="0e6d7-185">Windows を実行しているは 10 年 2018年 10 月の更新ですか?</span><span class="sxs-lookup"><span data-stu-id="0e6d7-185">Is your PC running the Windows 10 October 2018 Update?</span></span>
* <span data-ttu-id="0e6d7-186">レジストリ キーを設定するか。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-186">Have you set the reg key?</span></span> <span data-ttu-id="0e6d7-187">その後、デバイスを再起動しますか。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-187">Restarted the device afterwards?</span></span>
* <span data-ttu-id="0e6d7-188">QR コードのバージョンのサポートされているバージョンですか。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-188">Is the QR code version a supported version?</span></span> <span data-ttu-id="0e6d7-189">QR コードのバージョンの 20 まで現在の API のサポート。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-189">Current API supports up to QR Code Version 20.</span></span> <span data-ttu-id="0e6d7-190">バージョン 5 を使用して一般的な使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-190">We recommend using version 5 for general usage.</span></span> 
* <span data-ttu-id="0e6d7-191">QR コードに近づけるか。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-191">Are you close enough to the QR code?</span></span> <span data-ttu-id="0e6d7-192">近ければ近いほど、カメラは QR コードには、大きいほど、QR コードのバージョン、API をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-192">The closer the camera is to the QR code, the higher the QR code version the API can support.</span></span>  

<span data-ttu-id="0e6d7-193">**近いか、QR コードを検出する必要があるのでしょうか。**</span><span class="sxs-lookup"><span data-stu-id="0e6d7-193">**How close do I need to be to the QR code to detect it?**</span></span>

<span data-ttu-id="0e6d7-194">これは、QR コードのサイズに依存し、またどのようなバージョンが。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-194">This will depend on the size of the QR code, and also what version it is.</span></span> <span data-ttu-id="0e6d7-195">25 cm 辺を 5 cm 側からのさまざまなバージョン 1 の QR コードでは、最小検出間隔は 0.15 メーターから 0.5 m 範囲です。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-195">For a version 1 QR code varying from 5 cm sides to 25 cm sides, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> <span data-ttu-id="0e6d7-196">最も遠い離れたから検出されたこれら小さい QR コードのターゲットの約 0.3 メーターからに移動の規模が大きいほど 1.4 メーターします。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-196">The farthest away these can be detected from goes from about 0.3 meters for the smaller QR code targets to 1.4 meters for the bigger.</span></span> <span data-ttu-id="0e6d7-197">QR コードをよりも大きく、次を見積もることができます。サイズの検出間隔が直線的に増加します。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-197">For QR codes bigger than that, you can estimate; the detection distance for size increases linearly.</span></span> <span data-ttu-id="0e6d7-198">当社の追跡ツールでは機能しません辺の QR コード 5 cm より小さい。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-198">Our tracker does not work with QR codes with sides smaller than 5 cm.</span></span>

<span data-ttu-id="0e6d7-199">**ロゴの作業で QR コードを実行しますか。**</span><span class="sxs-lookup"><span data-stu-id="0e6d7-199">**Do QR codes with logos work?**</span></span>

<span data-ttu-id="0e6d7-200">ロゴの QR コードがテストされていないは現在サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-200">QR codes with logos have not been tested and are currently unsupported.</span></span>

<span data-ttu-id="0e6d7-201">**クリアする方法は QR コード アプリからそれらが維持されないためですか。**</span><span class="sxs-lookup"><span data-stu-id="0e6d7-201">**How do I clear QR codes from my app so they don't persist?**</span></span>

* <span data-ttu-id="0e6d7-202">QR コードは、ブート セッションでのみ保存されます。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-202">QR codes are only persisted in the boot session.</span></span> <span data-ttu-id="0e6d7-203">再起動 (または再起動するドライバー) 後になったし、新しいオブジェクトの [次へ] の時刻として検出されます。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-203">Once you reboot (or restart the driver), they will be gone and detected as new objects next time.</span></span>
* <span data-ttu-id="0e6d7-204">QR コードの履歴はドライバー セッションで、システム レベルで保存されますが、QR コードの特定のタイムスタンプよりも古いを無視する場合に、アプリを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-204">QR code history is saved at the system level in the driver session, but you can configure your app to ignore QR codes older than a specific timestamp if you want.</span></span> <span data-ttu-id="0e6d7-205">現在、API で複数のアプリは、データの利用可能性があるクリアリング QR コードの履歴をサポートするは。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-205">Currently the API does support clearing QR code history, as multiple apps might be interested in the data.</span></span>

<span data-ttu-id="0e6d7-206">**RS5 および将来のバージョンのプラグインがないプレリリース**RS5 バージョンのプラグインが RS5 に対してのみ機能し、将来のバージョンは機能しません。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-206">**The plugins for RS5 and future versions are not compatable** RS5 version of the plugin only works for RS5 and will not work for future versions.</span></span> <span data-ttu-id="0e6d7-207">Expermental プラグインでは、実際のプラグインで置き換えられるしを使って、今後のバージョン、windows のものである必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e6d7-207">The expermental plugin will be replaced with the real plugin and should be the one that we can use in future versions of the windows.</span></span>
