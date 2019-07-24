---
title: QR コードの追跡
description: Windows Mixed Reality イマーシブ (VR) ヘッドセットの QR コード追跡をオンにして、その機能を VR アプリに実装する方法について説明します。
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: vr、lbe、位置情報ベースのエンターテインメント、vr アーケード、アーケード、イマーシブ、qr、qr コード
ms.openlocfilehash: 465056cf645a8b9dc9e0e2d3f9dacf887df67c52
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829982"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="40d58-104">QR コードの追跡</span><span class="sxs-lookup"><span data-stu-id="40d58-104">QR code tracking</span></span>

<span data-ttu-id="40d58-105">QR コードの追跡は、Windows Mixed Reality driver for イマーシブ (VR) ヘッドセットに実装されています。</span><span class="sxs-lookup"><span data-stu-id="40d58-105">QR code tracking is implemented in the Windows Mixed Reality driver for immersive (VR) headsets.</span></span> <span data-ttu-id="40d58-106">ヘッドセットドライバーで QR コードトラッカーを有効にすることで、ヘッドセットは QR コードをスキャンし、関心のあるアプリに報告します。</span><span class="sxs-lookup"><span data-stu-id="40d58-106">By enabling the QR code tracker in the headset driver, the headset scans for QR codes and they are reported to interested apps.</span></span> <span data-ttu-id="40d58-107">この機能は、 [Windows 10 10 月2018更新プログラム (RS5 とも呼ば](release-notes-october-2018.md)れます) の時点でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="40d58-107">This feature is only available as of the [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span>

>[!NOTE]
><span data-ttu-id="40d58-108">この記事のコードスニペットでは、現在、 C++ [ C++ holographic プロジェクトテンプレート](creating-a-holographic-directx-project.md)で使用されてC++いる C + c++ 17 準拠の/WinRT ではなく、/cx の使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="40d58-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="40d58-109">これらの概念は、プロジェクトC++の場合と同じですが、コードを変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40d58-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="device-support"></a><span data-ttu-id="40d58-110">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="40d58-110">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="40d58-111"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="40d58-111"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="40d58-112"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="40d58-112"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="40d58-113"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="40d58-113"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="40d58-114">QR コードの追跡</span><span class="sxs-lookup"><span data-stu-id="40d58-114">QR code tracking</span></span></td>
        <td><span data-ttu-id="40d58-115">❌</span><span class="sxs-lookup"><span data-stu-id="40d58-115">❌</span></span></td>
        <td><span data-ttu-id="40d58-116">✔️</span><span class="sxs-lookup"><span data-stu-id="40d58-116">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a><span data-ttu-id="40d58-117">ヘッドセットの QR コード追跡の有効化と無効化</span><span class="sxs-lookup"><span data-stu-id="40d58-117">Enabling and disabling QR code tracking for your headset</span></span>
<span data-ttu-id="40d58-118">注:このセクションは、 [Windows 10 10 月2018更新プログラム (RS5 とも呼ば](release-notes-october-2018.md)れます) に対してのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="40d58-118">Note: This section is only valid for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span> <span data-ttu-id="40d58-119">19h1 ビルド以降、これを行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="40d58-119">From 19h1 builds onwards you will not have to do this.</span></span>
<span data-ttu-id="40d58-120">QR コード追跡を活用する mixed reality アプリを開発している場合でも、これらのアプリのいずれかのお客様の場合も、ヘッドセットのドライバーで QR コードの追跡を手動で有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="40d58-120">Whether you're developing a mixed reality app that will leverage QR code tracking, or you're a customer of one of these apps, you'll need to manually turn on QR code tracking in your headset's driver.</span></span>

<span data-ttu-id="40d58-121">イマーシブ (VR) ヘッドセットの**QR コード追跡を有効**にするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="40d58-121">In order to **turn on QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="40d58-122">PC で Mixed Reality ポータルアプリを閉じます。</span><span class="sxs-lookup"><span data-stu-id="40d58-122">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="40d58-123">PC からヘッドセットを取り外します。</span><span class="sxs-lookup"><span data-stu-id="40d58-123">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="40d58-124">コマンドプロンプトで次のスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="40d58-124">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. <span data-ttu-id="40d58-125">ヘッドセットを PC に再接続します。</span><span class="sxs-lookup"><span data-stu-id="40d58-125">Reconnect your headset to your PC.</span></span>

<span data-ttu-id="40d58-126">イマーシブ (VR) ヘッドセットの**QR コード追跡を無効**にするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="40d58-126">In order to **turn off QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="40d58-127">PC で Mixed Reality ポータルアプリを閉じます。</span><span class="sxs-lookup"><span data-stu-id="40d58-127">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="40d58-128">PC からヘッドセットを取り外します。</span><span class="sxs-lookup"><span data-stu-id="40d58-128">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="40d58-129">コマンドプロンプトで次のスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="40d58-129">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. <span data-ttu-id="40d58-130">ヘッドセットを PC に再接続します。</span><span class="sxs-lookup"><span data-stu-id="40d58-130">Reconnect your headset to your PC.</span></span> <span data-ttu-id="40d58-131">これにより、検出された QR コードが "検出不可能" になります。</span><span class="sxs-lookup"><span data-stu-id="40d58-131">This will make any discovered QR codes "non-locatable."</span></span>

## <a name="printing-codes"></a><span data-ttu-id="40d58-132">印刷コード</span><span class="sxs-lookup"><span data-stu-id="40d58-132">Printing codes</span></span>

<span data-ttu-id="40d58-133">まず、 [qr コードの仕様](https://www.qrcode.com/en/howto/code.html)によれば、qr コードの仕様には、使用するための余白または "quiet ゾーン" が必要です。</span><span class="sxs-lookup"><span data-stu-id="40d58-133">First and foremost, the [spec for QR codes](https://www.qrcode.com/en/howto/code.html) says "The QR Code symbol area requires a margin or "quiet zone" around it to be used.</span></span> <span data-ttu-id="40d58-134">余白は、何も印刷されないシンボルの周りの明確な領域です。</span><span class="sxs-lookup"><span data-stu-id="40d58-134">The margin is a clear area around a symbol where nothing is printed.</span></span> <span data-ttu-id="40d58-135">QR コードでは、記号の両側に4つのモジュールのワイドマージンが必要です。 "</span><span class="sxs-lookup"><span data-stu-id="40d58-135">QR Code requires a four-module wide margin at all sides of a symbol."</span></span> <span data-ttu-id="40d58-136">これは、モジュールのサイズの4倍の幅を持つ必要があります。コードの1つの黒い四角形です。</span><span class="sxs-lookup"><span data-stu-id="40d58-136">This needs to have a width, on every side, of four times the size of a module - a single black square in the code.</span></span> <span data-ttu-id="40d58-137">[仕様] ページには、QR コードを印刷する方法に関するアドバイスと、特定のサイズの QR コードを作成するために必要な領域が表示されます。</span><span class="sxs-lookup"><span data-stu-id="40d58-137">The spec page contains advice on how to print QR codes and figure out the area required to make a certain sized QR code.</span></span>

<span data-ttu-id="40d58-138">現在 QR コード検出の品質は、さまざまな照明と背景に影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="40d58-138">Currently QR code detection quality is susceptible to varying illumination and backdrop.</span></span> <span data-ttu-id="40d58-139">これに対処するには、照明をメモして、適切なコードを出力します。</span><span class="sxs-lookup"><span data-stu-id="40d58-139">To combat this, note your illumination and print the appropriate code.</span></span> <span data-ttu-id="40d58-140">特に明るい照明を持つシーンでは、グレーの背景に黒のコードを印刷します。</span><span class="sxs-lookup"><span data-stu-id="40d58-140">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="40d58-141">低光のシーンでは、黒の白で動作します。</span><span class="sxs-lookup"><span data-stu-id="40d58-141">Under a low-light scene, black on white works.</span></span> <span data-ttu-id="40d58-142">同様に、コードの背景が特に暗い場合は、検出率が低い場合はグレーのコードでブラックを試します。</span><span class="sxs-lookup"><span data-stu-id="40d58-142">Likewise, if the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="40d58-143">それ以外の場合、背景が薄い場合は、通常のコードが正常に動作します。</span><span class="sxs-lookup"><span data-stu-id="40d58-143">Otherwise, if the backdrop is lighter, a regular code should work fine.</span></span>

## <a name="qrtracking-api"></a><span data-ttu-id="40d58-144">QRTracking API</span><span class="sxs-lookup"><span data-stu-id="40d58-144">QRTracking API</span></span>

<span data-ttu-id="40d58-145">QRTracking プラグインは、QR コード追跡用の Api を公開します。</span><span class="sxs-lookup"><span data-stu-id="40d58-145">The QRTracking plugin exposes the APIs for QR code tracking.</span></span> <span data-ttu-id="40d58-146">プラグインを使用するには、 *Qrcodestrackerplugin*名前空間の次の型を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40d58-146">To use the plugin, you will need to use the following types from the *QRCodesTrackerPlugin* namespace.</span></span>

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

## <a name="implementing-qr-code-tracking-in-unity"></a><span data-ttu-id="40d58-147">Unity で QR コード追跡を実装する</span><span class="sxs-lookup"><span data-stu-id="40d58-147">Implementing QR code tracking in Unity</span></span>

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a><span data-ttu-id="40d58-148">MRTK の Unity シーンのサンプル (Mixed Reality ツールキット)</span><span class="sxs-lookup"><span data-stu-id="40d58-148">Sample Unity scenes in MRTK (Mixed Reality Toolkit)</span></span>

<span data-ttu-id="40d58-149">QR 追跡 API の使用方法の例については、「Mixed Reality Toolkit [GitHub サイト](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40d58-149">You can find an example for how to use the QR Tracking API in the Mixed Reality Toolkit [GitHub site](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).</span></span>

<span data-ttu-id="40d58-150">MRTK には、QR 追跡の使用状況を簡略化するために必要なスクリプトが実装されています。</span><span class="sxs-lookup"><span data-stu-id="40d58-150">MRTK has implemented the needed scripts to simpilify the QR tracking usage.</span></span> <span data-ttu-id="40d58-151">QR 追跡アプリの開発に必要なすべての資産は、"QRTracker" フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="40d58-151">All necessary assets to develop QR tracking apps are in the "QRTracker" folder.</span></span> <span data-ttu-id="40d58-152">2つのシーンがあります。1つ目は、検出された QR コードの詳細を表示するサンプルです。2つ目は、QR コードにアタッチされた座標系を使用してホログラムを表示する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="40d58-152">There are two scenes: the first is a sample to simply show details of the QR codes as they are detected, and the second demonstrates how to use the coordinate system attached to the QR code to display holograms.</span></span>
<span data-ttu-id="40d58-153">Prefab "QRScanner" を使用すると、必要なすべてのスクリプトをバックグラウンドに追加して Qrscanner を使用できます。</span><span class="sxs-lookup"><span data-stu-id="40d58-153">There is a prefab "QRScanner" which added all the necessary scripts to the scenes to use QRCodes.</span></span> <span data-ttu-id="40d58-154">スクリプト QRCodeManager は、QRCode API を実装するシングルトンクラスです。</span><span class="sxs-lookup"><span data-stu-id="40d58-154">The script QRCodeManager is a singleton class that implements the QRCode API.</span></span> <span data-ttu-id="40d58-155">これはシーンに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40d58-155">This needs to be added to your scene.</span></span> <span data-ttu-id="40d58-156">スクリプト "AttachToQRCode" は、ホログラムを QR コードの座標系に接続するために使用されます。このスクリプトは、どのホログラムにでも追加できます。</span><span class="sxs-lookup"><span data-stu-id="40d58-156">The script "AttachToQRCode" is used to attach holograms to the QR Code coordinate systems, this script can be added to any of your holograms.</span></span> <span data-ttu-id="40d58-157">"SpatialGraphCoordinateSystem" は、QRCode 座標系の使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="40d58-157">The "SpatialGraphCoordinateSystem" shows how to use the QRCode coordinate system.</span></span> <span data-ttu-id="40d58-158">これらのスクリプトは、プロジェクトシーンでそのまま使用することも、前に説明したように、プラグインを使用して直接作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="40d58-158">These scripts can be used as-is in your project scenes or you can write your own directly using the plugin as described above.</span></span>

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a><span data-ttu-id="40d58-159">MRTK を使用せずに Unity で QR コード追跡を実装する</span><span class="sxs-lookup"><span data-stu-id="40d58-159">Implementing QR code tracking in Unity without MRTK</span></span>

<span data-ttu-id="40d58-160">MRTK に依存せずに、Unity で QR 追跡 API を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="40d58-160">You can also use the QR Tracking API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="40d58-161">API を使用するには、次の指示に従ってプロジェクトを準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40d58-161">In order to use the API, you will need to prepare your project with the following instruction:</span></span>

1. <span data-ttu-id="40d58-162">Unity プロジェクトの assets フォルダーに、次の名前で新しいフォルダーを作成します。"プラグイン"。</span><span class="sxs-lookup"><span data-stu-id="40d58-162">Create a new folder in the assets folder of your unity project with the name: "Plugins".</span></span>
2. <span data-ttu-id="40d58-163">[このフォルダー](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins)のすべての必要なファイルを、先ほど作成したローカルの "プラグイン" フォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="40d58-163">Copy all the required files from [this folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) into the local "Plugins" folder you just created.</span></span>
3. <span data-ttu-id="40d58-164">[Mrtk scripts フォルダー](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts)内の QR 追跡スクリプトを使用することも、独自に作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="40d58-164">You can use the QR tracking scripts in the [MRTK scripts folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) or write your own.</span></span>
<span data-ttu-id="40d58-165">注:これらのプラグインは、 [Windows 10 10 月2018更新プログラム (RS5 とも呼ば](release-notes-october-2018.md)れます) のビルドに対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="40d58-165">Note: These plugins are only for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md) builds.</span></span> <span data-ttu-id="40d58-166">プラグインは、次の windows リリースで更新されます。</span><span class="sxs-lookup"><span data-stu-id="40d58-166">The plugins will be updated with the next windows release.</span></span> <span data-ttu-id="40d58-167">現在のプラグインは試験段階であり、今後のバージョンの windows では機能しません。</span><span class="sxs-lookup"><span data-stu-id="40d58-167">The current plugins were experimental and will not work for future version of the windows.</span></span> <span data-ttu-id="40d58-168">新しいプラグインは発行されます。このプラグインは、次の windows リリースから使用でき、後方互換性ではなく、RS5 では動作しません)。</span><span class="sxs-lookup"><span data-stu-id="40d58-168">New plugins will be published which can be used from next windows release and they will not be backwards compatable and will not work with RS5).</span></span>

## <a name="implementing-qr-code-tracking-in-directx"></a><span data-ttu-id="40d58-169">DirectX での QR コード追跡の実装</span><span class="sxs-lookup"><span data-stu-id="40d58-169">Implementing QR code tracking in DirectX</span></span>

<span data-ttu-id="40d58-170">Visual Studio で QRTrackingPlugin を使用するには、winmd に QRTrackingPlugin の参照を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40d58-170">To use the QRTrackingPlugin in Visual Studio, you will need to add reference of the QRTrackingPlugin to the .winmd.</span></span> <span data-ttu-id="40d58-171">[サポートされているプラットフォームに必要なファイルについ](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA)ては、こちらを参照してください。</span><span class="sxs-lookup"><span data-stu-id="40d58-171">You can find the [required files for supported platforms here](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span></span>

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

## <a name="getting-a-coordinate-system"></a><span data-ttu-id="40d58-172">座標系を取得する</span><span class="sxs-lookup"><span data-stu-id="40d58-172">Getting a coordinate system</span></span>

<span data-ttu-id="40d58-173">上の左にある高速検出の四角形の左上隅にある QR コードに合わせて、右側の座標系を定義します。</span><span class="sxs-lookup"><span data-stu-id="40d58-173">We define a right-hand coordinate system aligned with the QR code at the top left corner of the fast detection square in the top left.</span></span> <span data-ttu-id="40d58-174">座標系は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="40d58-174">The coordinate system is shown below.</span></span> <span data-ttu-id="40d58-175">Z 軸は用紙を指しています (図には示されていません) が、Unity では、z 軸は紙でも左手でもありません。</span><span class="sxs-lookup"><span data-stu-id="40d58-175">The Z-axis is pointing into the paper (not shown), but in Unity the z-axis is out of the paper and left-handed.</span></span>

<span data-ttu-id="40d58-176">SpatialCoordinateSystem は、示されているように定義されています。</span><span class="sxs-lookup"><span data-stu-id="40d58-176">A SpatialCoordinateSystem is defined that is aligned as shown.</span></span> <span data-ttu-id="40d58-177">この座標系は、API *Windows::P erception:: 空間::P review:: SpatialGraphInteropPreview:: CreateCoordinateSystemForNode*を使用してプラットフォームから取得できます。</span><span class="sxs-lookup"><span data-stu-id="40d58-177">This coordinate system can be obtained from the platform using the API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.</span></span>

![QR コードの座標系](images/Qr-coordinatesystem.png) 

<span data-ttu-id="40d58-179">QRCode ^ Code オブジェクトから、次のコードは、四角形を作成して QR 座標系に配置する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="40d58-179">From QRCode^ Code object, the following code shows how to create a rectangle and put it in QR coordinate system:</span></span>

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

<span data-ttu-id="40d58-180">次のように、物理的なサイズを使用して QR 四角形を作成できます。</span><span class="sxs-lookup"><span data-stu-id="40d58-180">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

<span data-ttu-id="40d58-181">座標系は、QR コードを描画したり、場所にホログラムをアタッチしたりするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="40d58-181">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

<span data-ttu-id="40d58-182">*Qrcodestrackerplugin:: QRCodeAddedHandler*は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="40d58-182">Altogether, your *QRCodesTrackerPlugin::QRCodeAddedHandler* may look something like this:</span></span>

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

## <a name="troubleshooting-and-faq"></a><span data-ttu-id="40d58-183">トラブルシューティングと FAQ</span><span class="sxs-lookup"><span data-stu-id="40d58-183">Troubleshooting and FAQ</span></span>

<span data-ttu-id="40d58-184">**一般的なトラブルシューティング**</span><span class="sxs-lookup"><span data-stu-id="40d58-184">**General troubleshooting**</span></span>

* <span data-ttu-id="40d58-185">PC は2018年10月の更新プログラムを実行していますか?</span><span class="sxs-lookup"><span data-stu-id="40d58-185">Is your PC running the Windows 10 October 2018 Update?</span></span>
* <span data-ttu-id="40d58-186">Reg キーを設定していますか?</span><span class="sxs-lookup"><span data-stu-id="40d58-186">Have you set the reg key?</span></span> <span data-ttu-id="40d58-187">その後、デバイスを再起動しましたか?</span><span class="sxs-lookup"><span data-stu-id="40d58-187">Restarted the device afterwards?</span></span>
* <span data-ttu-id="40d58-188">QR コードのバージョンはサポートされているバージョンですか。</span><span class="sxs-lookup"><span data-stu-id="40d58-188">Is the QR code version a supported version?</span></span> <span data-ttu-id="40d58-189">現在の API では、最大 QR コードバージョン20がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="40d58-189">Current API supports up to QR Code Version 20.</span></span> <span data-ttu-id="40d58-190">一般的な使用には、バージョン5を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="40d58-190">We recommend using version 5 for general usage.</span></span> 
* <span data-ttu-id="40d58-191">QR コードに十分に近づいていますか?</span><span class="sxs-lookup"><span data-stu-id="40d58-191">Are you close enough to the QR code?</span></span> <span data-ttu-id="40d58-192">カメラが QR コードに近いほど、API がサポートできる QR コードバージョンが大きくなります。</span><span class="sxs-lookup"><span data-stu-id="40d58-192">The closer the camera is to the QR code, the higher the QR code version the API can support.</span></span>  

<span data-ttu-id="40d58-193">**それを検出するには、QR コードにとってどのようにする必要がありますか。**</span><span class="sxs-lookup"><span data-stu-id="40d58-193">**How close do I need to be to the QR code to detect it?**</span></span>

<span data-ttu-id="40d58-194">これは、QR コードのサイズと、そのバージョンによって異なります。</span><span class="sxs-lookup"><span data-stu-id="40d58-194">This will depend on the size of the QR code, and also what version it is.</span></span> <span data-ttu-id="40d58-195">5 cm の辺から 25 cm の辺まで、バージョン1の QR コードの場合、最小検出距離は0.15 メートルから0.5 メートルの範囲内です。</span><span class="sxs-lookup"><span data-stu-id="40d58-195">For a version 1 QR code varying from 5 cm sides to 25 cm sides, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> <span data-ttu-id="40d58-196">最も遠いものは、より小さい QR コードターゲットの場合は約0.3 メートルから、それより大きい場合は1.4 メートルまでとなります。</span><span class="sxs-lookup"><span data-stu-id="40d58-196">The farthest away these can be detected from goes from about 0.3 meters for the smaller QR code targets to 1.4 meters for the bigger.</span></span> <span data-ttu-id="40d58-197">これよりも大きな QR コードの場合、を推定することができます。サイズの検出距離は直線的に増加します。</span><span class="sxs-lookup"><span data-stu-id="40d58-197">For QR codes bigger than that, you can estimate; the detection distance for size increases linearly.</span></span> <span data-ttu-id="40d58-198">トラッカーは、5 cm よりも小さい側の QR コードでは機能しません。</span><span class="sxs-lookup"><span data-stu-id="40d58-198">Our tracker does not work with QR codes with sides smaller than 5 cm.</span></span>

<span data-ttu-id="40d58-199">**ロゴ付きの QR コードを使用しますか?**</span><span class="sxs-lookup"><span data-stu-id="40d58-199">**Do QR codes with logos work?**</span></span>

<span data-ttu-id="40d58-200">ロゴ付きの QR コードはテストされていないため、現在サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="40d58-200">QR codes with logos have not been tested and are currently unsupported.</span></span>

<span data-ttu-id="40d58-201">**アプリから QR コードを消去して永続化操作方法には、**</span><span class="sxs-lookup"><span data-stu-id="40d58-201">**How do I clear QR codes from my app so they don't persist?**</span></span>

* <span data-ttu-id="40d58-202">QR コードは、ブートセッションでのみ保持されます。</span><span class="sxs-lookup"><span data-stu-id="40d58-202">QR codes are only persisted in the boot session.</span></span> <span data-ttu-id="40d58-203">再起動 (またはドライバーの再起動) が完了すると、次に新しいオブジェクトとして検出されます。</span><span class="sxs-lookup"><span data-stu-id="40d58-203">Once you reboot (or restart the driver), they will be gone and detected as new objects next time.</span></span>
* <span data-ttu-id="40d58-204">QR コードの履歴は、ドライバーセッションのシステムレベルで保存されますが、必要に応じて、特定のタイムスタンプよりも古い QR コードを無視するようにアプリを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="40d58-204">QR code history is saved at the system level in the driver session, but you can configure your app to ignore QR codes older than a specific timestamp if you want.</span></span> <span data-ttu-id="40d58-205">現在、API では、複数のアプリがデータに関心を持っている可能性があるため、QR コードの履歴のクリアをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="40d58-205">Currently the API does support clearing QR code history, as multiple apps might be interested in the data.</span></span>

<span data-ttu-id="40d58-206">**RS5 および将来のバージョンのプラグインは互換性ません**。RS5 バージョンのプラグインは RS5 に対してのみ機能し、今後のバージョンでは機能しません。</span><span class="sxs-lookup"><span data-stu-id="40d58-206">**The plugins for RS5 and future versions are not compatable** RS5 version of the plugin only works for RS5 and will not work for future versions.</span></span> <span data-ttu-id="40d58-207">Expermental プラグインは実際のプラグインに置き換えられ、今後のバージョンの windows で使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="40d58-207">The expermental plugin will be replaced with the real plugin and should be the one that we can use in future versions of the windows.</span></span>
