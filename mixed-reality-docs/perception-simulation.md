---
title: Perception シミュレーション
description: Perception シミュレーション ライブラリを使用して、シミュレートされた没入型アプリケーションの入力を自動化するためのガイド
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、シミュレーションのテスト
ms.openlocfilehash: 693750eb753bd11cbe7d7cfb47e04f1a3506ca9a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602204"
---
# <a name="perception-simulation"></a><span data-ttu-id="6e70e-104">Perception シミュレーション</span><span class="sxs-lookup"><span data-stu-id="6e70e-104">Perception simulation</span></span>

<span data-ttu-id="6e70e-105">アプリの自動テストをビルドしますか。</span><span class="sxs-lookup"><span data-stu-id="6e70e-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="6e70e-106">コンポーネント レベルの単体テストを超えるし、実際に、アプリのエンドを実行するためのテストを作成しますか。</span><span class="sxs-lookup"><span data-stu-id="6e70e-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="6e70e-107">Perception シミュレーションは、探しているものです。</span><span class="sxs-lookup"><span data-stu-id="6e70e-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="6e70e-108">Perception シミュレーション ライブラリ偽の人間と送信の世界の入力データをアプリに、テストを自動化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="6e70e-108">The Perception Simulation library sends fake human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="6e70e-109">たとえば、左と右に人間の検索とジェスチャを実行することの入力をシミュレートできます。</span><span class="sxs-lookup"><span data-stu-id="6e70e-109">For example, you can simulate the input of a human looking left and right and then performing a gesture.</span></span>

<span data-ttu-id="6e70e-110">Perception シミュレーションでは、物理 HoloLens、HoloLens のエミュレーター、またはインストールされている混合の現実ポータルを使用した PC にこのようなシミュレーションの入力を送信できます。</span><span class="sxs-lookup"><span data-stu-id="6e70e-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="6e70e-111">Perception Mixed Reality デバイスでライブのセンサーをバイパスし、シミュレーションでは、デバイスで実行されているアプリケーションへの入力をシミュレートします。</span><span class="sxs-lookup"><span data-stu-id="6e70e-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="6e70e-112">アプリケーションでは、使用、および知覚のシミュレーションを実行するいると実際のセンサーを実行している間の違いを見分けることはできませんが、常に、同じ Api を介してこれら偽の入力イベントを受信します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-112">Applications receive these fake input events through the same APIs they always use, and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="6e70e-113">Perception シミュレーションは、シミュレートされた入力、HoloLens 仮想マシンに送信するために使用、HoloLens のエミュレーターと同じテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="6e70e-113">Perception Simulation is the same technology used by the HoloLens emulator to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="6e70e-114">シミュレーションでは、まず、IPerceptionSimulationManager オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-114">Simulation starts by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="6e70e-115">そのオブジェクトは、シミュレートされた「人事」、ヘッドの位置、手の形の位置、ジェスチャなどのプロパティを制御するためのコマンドを発行できます。</span><span class="sxs-lookup"><span data-stu-id="6e70e-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="6e70e-116">Perception でシミュレーションするための Visual Studio プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="6e70e-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="6e70e-117">[HoloLens のエミュレーターをインストール](install-the-tools.md)開発 PC 上。</span><span class="sxs-lookup"><span data-stu-id="6e70e-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="6e70e-118">エミュレーターには、Perception シミュレーションに使用するライブラリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6e70e-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="6e70e-119">作成する新しい Visual StudioC#デスクトップのプロジェクト (コンソール プロジェクトをうまくを開始する)。</span><span class="sxs-lookup"><span data-stu-id="6e70e-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="6e70e-120">次のバイナリをプロジェクトに参照として追加 (プロジェクトに追加]-> [-> 参照)。検索できます **%programfiles (x86) %\Microsoft XDE\10.0.11082.0**をします。</span><span class="sxs-lookup"><span data-stu-id="6e70e-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in **%ProgramFiles(x86)%\Microsoft XDE\10.0.11082.0** a.</span></span> <span data-ttu-id="6e70e-121">管理 - PerceptionSimulationManager.Interop.dll C# Perception シミュレーション用のラッパーです。</span><span class="sxs-lookup"><span data-stu-id="6e70e-121">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="6e70e-122">b. </span><span class="sxs-lookup"><span data-stu-id="6e70e-122">b.</span></span> <span data-ttu-id="6e70e-123">PerceptionSimulationRest.dll - HoloLens またはエミュレーターへの web ソケット通信チャネルを設定するためのライブラリを使用します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-123">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="6e70e-124">c.</span><span class="sxs-lookup"><span data-stu-id="6e70e-124">c.</span></span> <span data-ttu-id="6e70e-125">SimulationStream.Interop.dll のシミュレーションを共有する型。</span><span class="sxs-lookup"><span data-stu-id="6e70e-125">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="6e70e-126">実装を追加するプロジェクト バイナリ PerceptionSimulationManager.dll。</span><span class="sxs-lookup"><span data-stu-id="6e70e-126">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="6e70e-127">まず、プロジェクトに、バイナリとして追加 (プロジェクトに追加-> -> 既存項目の)。プロジェクトのソース フォルダーにコピーしないように、リンクとして保存します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-127">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="6e70e-128">![PerceptionSimulationManager.dll をリンクとしてプロジェクトに追加](images/saveaslink.png)b。</span><span class="sxs-lookup"><span data-stu-id="6e70e-128">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="6e70e-129">確認し、ビルドの出力フォルダーにコピーすることがあるのです。</span><span class="sxs-lookup"><span data-stu-id="6e70e-129">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="6e70e-130">これは、バイナリのプロパティ シートです。</span><span class="sxs-lookup"><span data-stu-id="6e70e-130">This is in the property sheet for the binary .</span></span> <span data-ttu-id="6e70e-131">![マーク PerceptionSimulationManager.dll 出力ディレクトリにコピーするには](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="6e70e-131">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="6e70e-132">IPerceptionSimulation マネージャー オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-132">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="6e70e-133">シミュレーションを制御するには、IPerceptionSimulationManager オブジェクトから取得したオブジェクトの更新プログラムを発行します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-133">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="6e70e-134">最初の手順では、そのオブジェクトを取得し、ターゲット デバイスまたはエミュレーターに接続します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-134">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="6e70e-135">デバイスのポータル をクリックして、エミュレーターの IP アドレスを取得できます、[ツールバー](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)</span><span class="sxs-lookup"><span data-stu-id="6e70e-135">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)</span></span>

<span data-ttu-id="6e70e-136">![デバイスのポータルを開く アイコン](images/emulator-deviceportal.png)**デバイス ポータルを開く**:エミュレーターでの HoloLens os、Windows Device Portal を開きます。</span><span class="sxs-lookup"><span data-stu-id="6e70e-136">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>

<span data-ttu-id="6e70e-137">まず、RestSimulationStreamSink.Create RestSimulationStreamSink オブジェクトを取得すると呼んでいます。</span><span class="sxs-lookup"><span data-stu-id="6e70e-137">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="6e70e-138">これは、対象のデバイスまたはエミュレーターを http 接続を介して制御されます。</span><span class="sxs-lookup"><span data-stu-id="6e70e-138">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="6e70e-139">コマンドに渡され、によって処理されますが、 [Windows Device Portal](using-the-windows-device-portal.md)デバイスまたはエミュレーターで実行されています。</span><span class="sxs-lookup"><span data-stu-id="6e70e-139">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="6e70e-140">オブジェクトを作成する必要があります、4 つのパラメーターは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6e70e-140">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="6e70e-141">Uri の uri、ターゲット デバイスの IP アドレス (例:"http://123.123.123.123")</span><span class="sxs-lookup"><span data-stu-id="6e70e-141">Uri uri - IP address of the target device (e.g., "http://123.123.123.123")</span></span>
* <span data-ttu-id="6e70e-142">System.Net.NetworkCredential 資格情報 - に接続するためには、ユーザー名/パスワード、 [Windows Device Portal](using-the-windows-device-portal.md)ターゲット デバイスまたはエミュレーターにします。</span><span class="sxs-lookup"><span data-stu-id="6e70e-142">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="6e70e-143">そのローカル 168 を使用してエミュレーターに接続しています。 場合、*.*。 \* アドレス同じ pc では、すべての資格情報が受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="6e70e-143">If you are connecting to the emulator via its local 168.*.*.\* address on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="6e70e-144">bool の通常の通常の優先順位、優先度の低いは false の場合は True。</span><span class="sxs-lookup"><span data-stu-id="6e70e-144">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="6e70e-145">一般にこれを設定する*true*テスト シナリオ用。</span><span class="sxs-lookup"><span data-stu-id="6e70e-145">You generally want to set this to *true* for test scenarios.</span></span>
* <span data-ttu-id="6e70e-146">System.Threading.CancellationToken トークン - 非同期操作をキャンセルするトークンです。</span><span class="sxs-lookup"><span data-stu-id="6e70e-146">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="6e70e-147">2 つ目は、IPerceptionSimulationManager を作成します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-147">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="6e70e-148">これは、使用してシミュレーションを制御するオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="6e70e-148">This is the object you use to control simulation.</span></span> <span data-ttu-id="6e70e-149">これをも実行することで、非同期メソッドに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6e70e-149">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="6e70e-150">シミュレートされたユーザーを制御します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-150">Control the simulated Human</span></span>

<span data-ttu-id="6e70e-151">IPerceptionSimulationManager には、ISimulatedHuman オブジェクトを返す人間プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="6e70e-151">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="6e70e-152">シミュレートされたユーザーを制御するには、このオブジェクトに対して操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-152">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="6e70e-153">次に、例を示します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-153">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="6e70e-154">基本的なサンプルC#コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="6e70e-154">Basic Sample C# console application</span></span>

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Task.Run(async () =>
            {
                try
                {
                    RestSimulationStreamSink sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        new System.Threading.CancellationToken());

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="6e70e-155">サンプルを拡張C#コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="6e70e-155">Extended Sample C# console application</span></span>

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Task.Run(async () =>
            {
                try
                {
                    RestSimulationStreamSink sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        new System.Threading.CancellationToken());

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

                    // Simulate Bloom gesture, which should cause Shell to disappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... this time, Shell should reappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate a Head rotation down around the X axis
                    // This should cause gaze to aim about the center of the screen
                    manager.Human.Head.Rotate(new Rotation3(0.04f, 0.0f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a finger press & release
                    // Should cause a tap on the center tile, thus launching it
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate a second finger press & release
                    // Should activate the app that was launched when the center tile was clicked
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(5000);

                    // Simulate a Head rotation towards the upper right corner
                    manager.Human.Head.Rotate(new Rotation3(-0.14f, 0.17f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a third finger press & release
                    // Should press the Remove button on the app
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... bringing the Shell back once more
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="api-reference"></a><span data-ttu-id="6e70e-156">API リファレンス</span><span class="sxs-lookup"><span data-stu-id="6e70e-156">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="6e70e-157">Microsoft.PerceptionSimulation.SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="6e70e-157">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="6e70e-158">シミュレートされたデバイスの種類について説明します</span><span class="sxs-lookup"><span data-stu-id="6e70e-158">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="6e70e-159">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span><span class="sxs-lookup"><span data-stu-id="6e70e-159">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="6e70e-160">架空の参照のデバイスでは、PerceptionSimulationManager の既定値</span><span class="sxs-lookup"><span data-stu-id="6e70e-160">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="6e70e-161">Microsoft.PerceptionSimulation.HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="6e70e-161">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="6e70e-162">ヘッド トラッカー モードについて説明します</span><span class="sxs-lookup"><span data-stu-id="6e70e-162">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="6e70e-163">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span><span class="sxs-lookup"><span data-stu-id="6e70e-163">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="6e70e-164">既定の Head が追跡します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-164">Default Head Tracking.</span></span> <span data-ttu-id="6e70e-165">つまり、システムは、追跡モードの実行時の条件に基づいて最適なヘッドを選択ことがあります。</span><span class="sxs-lookup"><span data-stu-id="6e70e-165">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="6e70e-166">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span><span class="sxs-lookup"><span data-stu-id="6e70e-166">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="6e70e-167">印刷の向きのみヘッドが追跡します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-167">Orientation Only Head Tracking.</span></span> <span data-ttu-id="6e70e-168">つまり、追跡対象の位置は、信頼性が高く、できない場合があります、ヘッドの位置に依存する一部の機能を利用できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6e70e-168">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="6e70e-169">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span><span class="sxs-lookup"><span data-stu-id="6e70e-169">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="6e70e-170">ヘッドの位置指定の追跡。</span><span class="sxs-lookup"><span data-stu-id="6e70e-170">Positional Head Tracking.</span></span> <span data-ttu-id="6e70e-171">つまり、追跡されているヘッドの位置と向きの両方がある信頼性の高い</span><span class="sxs-lookup"><span data-stu-id="6e70e-171">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="6e70e-172">Microsoft.PerceptionSimulation.SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="6e70e-172">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="6e70e-173">シミュレートされたジェスチャを説明します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-173">Describes a simulated gesture</span></span>

```
public enum SimulatedGesture
{
    None = 0,
    FingerPressed = 1,
    FingerReleased = 2,
    Home = 4,
    Max = Home
}
```

<span data-ttu-id="6e70e-174">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span><span class="sxs-lookup"><span data-stu-id="6e70e-174">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="6e70e-175">ジェスチャがない場合に使用される sentinel 値</span><span class="sxs-lookup"><span data-stu-id="6e70e-175">A sentinel value used to indicate no gestures</span></span>

<span data-ttu-id="6e70e-176">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="6e70e-176">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="6e70e-177">ジェスチャが押された指</span><span class="sxs-lookup"><span data-stu-id="6e70e-177">A finger pressed gesture</span></span>

<span data-ttu-id="6e70e-178">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="6e70e-178">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="6e70e-179">リリースの指のジェスチャ</span><span class="sxs-lookup"><span data-stu-id="6e70e-179">A finger released gesture</span></span>

<span data-ttu-id="6e70e-180">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span><span class="sxs-lookup"><span data-stu-id="6e70e-180">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="6e70e-181">ホームのジェスチャ</span><span class="sxs-lookup"><span data-stu-id="6e70e-181">The home gesture</span></span>

<span data-ttu-id="6e70e-182">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span><span class="sxs-lookup"><span data-stu-id="6e70e-182">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="6e70e-183">最大の有効なジェスチャ</span><span class="sxs-lookup"><span data-stu-id="6e70e-183">The maximum valid gesture</span></span>

### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="6e70e-184">Microsoft.PerceptionSimulation.PlaybackState</span><span class="sxs-lookup"><span data-stu-id="6e70e-184">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="6e70e-185">再生の状態について説明します</span><span class="sxs-lookup"><span data-stu-id="6e70e-185">Describes the state of a playback</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="6e70e-186">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span><span class="sxs-lookup"><span data-stu-id="6e70e-186">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="6e70e-187">記録の停止と再生の準備ができては現在</span><span class="sxs-lookup"><span data-stu-id="6e70e-187">The recording is currently stopped and ready for playback</span></span>

<span data-ttu-id="6e70e-188">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span><span class="sxs-lookup"><span data-stu-id="6e70e-188">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="6e70e-189">記録を再生中</span><span class="sxs-lookup"><span data-stu-id="6e70e-189">The recording is currently playing</span></span>

<span data-ttu-id="6e70e-190">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span><span class="sxs-lookup"><span data-stu-id="6e70e-190">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="6e70e-191">記録が現在一時停止しています</span><span class="sxs-lookup"><span data-stu-id="6e70e-191">The recording is currently paused</span></span>

<span data-ttu-id="6e70e-192">**Microsoft.PerceptionSimulation.PlaybackState.End**</span><span class="sxs-lookup"><span data-stu-id="6e70e-192">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="6e70e-193">記録が末尾に達した</span><span class="sxs-lookup"><span data-stu-id="6e70e-193">The recording has reached the end</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="6e70e-194">Microsoft.PerceptionSimulation.Vector3</span><span class="sxs-lookup"><span data-stu-id="6e70e-194">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="6e70e-195">点または 3D 空間でベクターを表す場合があります、3 つのコンポーネントのベクターをについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-195">Describes a 3 components vector, which might describe a point or a vector in 3D space</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="6e70e-196">**Microsoft.PerceptionSimulation.Vector3.X**</span><span class="sxs-lookup"><span data-stu-id="6e70e-196">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="6e70e-197">ベクターの X コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6e70e-197">The X component of the vector</span></span>

<span data-ttu-id="6e70e-198">**Microsoft.PerceptionSimulation.Vector3.Y**</span><span class="sxs-lookup"><span data-stu-id="6e70e-198">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="6e70e-199">ベクターの Y コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6e70e-199">The Y component of the vector</span></span>

<span data-ttu-id="6e70e-200">**Microsoft.PerceptionSimulation.Vector3.Z**</span><span class="sxs-lookup"><span data-stu-id="6e70e-200">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="6e70e-201">ベクトルの Z 成分</span><span class="sxs-lookup"><span data-stu-id="6e70e-201">The Z component of the vector</span></span>

<span data-ttu-id="6e70e-202">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="6e70e-202">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="6e70e-203">新しい Vector3 を構築します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-203">Construct a new Vector3</span></span>

<span data-ttu-id="6e70e-204">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e70e-204">Parameters</span></span>
* <span data-ttu-id="6e70e-205">ベクターの x、x コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6e70e-205">x - The x component of the vector</span></span>
* <span data-ttu-id="6e70e-206">y 軸ベクターの、y コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6e70e-206">y - The y component of the vector</span></span>
* <span data-ttu-id="6e70e-207">ベクトルの z、z 成分</span><span class="sxs-lookup"><span data-stu-id="6e70e-207">z - The z component of the vector</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="6e70e-208">Microsoft.PerceptionSimulation.Rotation3</span><span class="sxs-lookup"><span data-stu-id="6e70e-208">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="6e70e-209">3 つのコンポーネントの回転をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-209">Describes a 3 components rotation</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="6e70e-210">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span><span class="sxs-lookup"><span data-stu-id="6e70e-210">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="6e70e-211">回転のピッチ コンポーネントは、X 軸の周りのダウン</span><span class="sxs-lookup"><span data-stu-id="6e70e-211">The Pitch component of the Rotation, down around the X axis</span></span>

<span data-ttu-id="6e70e-212">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span><span class="sxs-lookup"><span data-stu-id="6e70e-212">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="6e70e-213">Y 軸の周囲の回転のヨー コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6e70e-213">The Yaw component of the Rotation, right around the Y axis</span></span>

<span data-ttu-id="6e70e-214">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span><span class="sxs-lookup"><span data-stu-id="6e70e-214">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="6e70e-215">Z 軸の周囲の回転のロールのコンポーネント</span><span class="sxs-lookup"><span data-stu-id="6e70e-215">The Roll component of the Rotation, right around the Z axis</span></span>

<span data-ttu-id="6e70e-216">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="6e70e-216">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="6e70e-217">新しい Rotation3 を構築します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-217">Construct a new Rotation3</span></span>

<span data-ttu-id="6e70e-218">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e70e-218">Parameters</span></span>
* <span data-ttu-id="6e70e-219">ピッチの回転のピッチ コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6e70e-219">pitch - The pitch component of the Rotation</span></span>
* <span data-ttu-id="6e70e-220">ヨー、回転のヨー コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6e70e-220">yaw - The yaw component of the Rotation</span></span>
* <span data-ttu-id="6e70e-221">ロールの回転のロールのコンポーネント</span><span class="sxs-lookup"><span data-stu-id="6e70e-221">roll - The roll component of the Rotation</span></span>

### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="6e70e-222">Microsoft.PerceptionSimulation.Frustum</span><span class="sxs-lookup"><span data-stu-id="6e70e-222">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="6e70e-223">カメラで通常使用される視錐台をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-223">Describes a view frustum, as typically used by a camera</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="6e70e-224">**Microsoft.PerceptionSimulation.Frustum.Near**</span><span class="sxs-lookup"><span data-stu-id="6e70e-224">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="6e70e-225">最小の距離の視錐台に含まれています。</span><span class="sxs-lookup"><span data-stu-id="6e70e-225">The minimum distance that is contained in the frustum</span></span>

<span data-ttu-id="6e70e-226">**Microsoft.PerceptionSimulation.Frustum.Far**</span><span class="sxs-lookup"><span data-stu-id="6e70e-226">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="6e70e-227">最大距離の視錐台に含まれています。</span><span class="sxs-lookup"><span data-stu-id="6e70e-227">The maximum distance that is contained in the frustum</span></span>

<span data-ttu-id="6e70e-228">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="6e70e-228">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="6e70e-229">ラジアン (PI よりも小さい) 視錐台の横のフィールドの表示</span><span class="sxs-lookup"><span data-stu-id="6e70e-229">The horizontal field of view of the frustum, in radians (less than PI)</span></span>

<span data-ttu-id="6e70e-230">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="6e70e-230">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="6e70e-231">垂直ビューのフィールドへの水平視野の比率</span><span class="sxs-lookup"><span data-stu-id="6e70e-231">The ratio of horizontal field of view to vertical field of view</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="6e70e-232">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="6e70e-232">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="6e70e-233">デバイスの制御に使用されるパケットを生成するためのルート</span><span class="sxs-lookup"><span data-stu-id="6e70e-233">Root for generating the packets used to control a device</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="6e70e-234">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span><span class="sxs-lookup"><span data-stu-id="6e70e-234">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="6e70e-235">シミュレートされた人と、シミュレートされた世界を解釈するシミュレートされたデバイス オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-235">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="6e70e-236">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span><span class="sxs-lookup"><span data-stu-id="6e70e-236">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="6e70e-237">シミュレートされたユーザーを制御するオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-237">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="6e70e-238">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span><span class="sxs-lookup"><span data-stu-id="6e70e-238">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="6e70e-239">シミュレーションを既定の状態にリセットします。</span><span class="sxs-lookup"><span data-stu-id="6e70e-239">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="6e70e-240">Microsoft.PerceptionSimulation.ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="6e70e-240">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="6e70e-241">シミュレートされた世界でシミュレートされた人間を解釈し、デバイスを記述するインターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="6e70e-241">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="6e70e-242">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="6e70e-242">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="6e70e-243">シミュレートされたデバイスから、ヘッドの追跡ツールを取得します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-243">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="6e70e-244">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span><span class="sxs-lookup"><span data-stu-id="6e70e-244">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="6e70e-245">シミュレートされたデバイスからの手の形の追跡ツールを取得します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-245">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="6e70e-246">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="6e70e-246">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="6e70e-247">指定されたデバイスの種類に一致するように、シミュレートされたデバイスのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-247">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="6e70e-248">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e70e-248">Parameters</span></span>
* <span data-ttu-id="6e70e-249">シミュレートされたデバイスの新しい種類を入力します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-249">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="6e70e-250">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="6e70e-250">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="6e70e-251">シミュレートされた人間の頭を追跡するシミュレートされたデバイスの部分を記述するインターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="6e70e-251">Interface describing the portion of the simulated device that tracks the head of the simulated human</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="6e70e-252">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="6e70e-252">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="6e70e-253">取得し、現在のトラッカーのヘッド モードを設定します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-253">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="6e70e-254">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="6e70e-254">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="6e70e-255">シミュレートされた人間の手を追跡するシミュレートされたデバイスの部分を記述するインターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="6e70e-255">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

```
public interface ISimulatedHandTracker
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    float Pitch { get; set; }
    bool FrustumIgnored { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    Frustum Frustum { get; set; }
}
```

<span data-ttu-id="6e70e-256">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="6e70e-256">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="6e70e-257">メートル単位で、世界中とに関してノードの位置を取得します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-257">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="6e70e-258">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span><span class="sxs-lookup"><span data-stu-id="6e70e-258">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="6e70e-259">取得し、ヘッドの中央を基準、シミュレートされた手トラッカーの位置を設定します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-259">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="6e70e-260">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span><span class="sxs-lookup"><span data-stu-id="6e70e-260">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="6e70e-261">取得し、シミュレートされた手トラッカーの下向きのピッチの設定</span><span class="sxs-lookup"><span data-stu-id="6e70e-261">Retrieve and set the downward pitch of the simulated hand tracker</span></span>

<span data-ttu-id="6e70e-262">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="6e70e-262">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="6e70e-263">取得し、シミュレートされた手トラッカーの視錐台を無視するかどうかを設定します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-263">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="6e70e-264">無視される場合、両方の手は常に表示します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-264">When ignored, both hands are always visible.</span></span> <span data-ttu-id="6e70e-265">(既定値) を無視しない場合に手は手トラッカーの視錐台内にあるときに、表示のみです。</span><span class="sxs-lookup"><span data-stu-id="6e70e-265">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="6e70e-266">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span><span class="sxs-lookup"><span data-stu-id="6e70e-266">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="6e70e-267">取得し、手がシミュレートされた手の追跡ツールに表示されるかどうかを判断するための視錐台プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-267">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="6e70e-268">Microsoft.PerceptionSimulation.ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="6e70e-268">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="6e70e-269">シミュレートされたユーザーを制御するための最上位レベル インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6e70e-269">Top level interface for controlling the simulated human</span></span>

```
public interface ISimulatedHuman 
{
    Vector3 WorldPosition { get; set; }
    float Direction { get; set; }
    float Height { get; set; }
    ISimulatedHand LeftHand { get; }
    ISimulatedHand RightHand { get; }
    ISimulatedHead Head { get; }
    void Move(Vector3 translation);
    void Rotate(float radians);
}
```

<span data-ttu-id="6e70e-270">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="6e70e-270">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="6e70e-271">取得し、メートル単位で、世界中とに関してノードの位置を設定します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-271">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="6e70e-272">位置は、人間のフィートの中央にある点に対応します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-272">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="6e70e-273">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span><span class="sxs-lookup"><span data-stu-id="6e70e-273">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="6e70e-274">取得し、世界中でシミュレートされた人の顔の方向を設定します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-274">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="6e70e-275">負の Z 軸を 0 ラジアンに直面します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-275">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="6e70e-276">Y 軸の正のラジアンは右回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-276">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="6e70e-277">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span><span class="sxs-lookup"><span data-stu-id="6e70e-277">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="6e70e-278">取得し、シミュレーションの人間の高さをメートル単位で設定</span><span class="sxs-lookup"><span data-stu-id="6e70e-278">Retrieve and set the height of the simulated human, in meters</span></span>

<span data-ttu-id="6e70e-279">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span><span class="sxs-lookup"><span data-stu-id="6e70e-279">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="6e70e-280">シミュレートされた人間の左側を取得します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-280">Retrieve the left hand of the simulated human</span></span>

<span data-ttu-id="6e70e-281">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span><span class="sxs-lookup"><span data-stu-id="6e70e-281">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="6e70e-282">シミュレートされた人間の右側を取得します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-282">Retrieve the right hand of the simulated human</span></span>

<span data-ttu-id="6e70e-283">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span><span class="sxs-lookup"><span data-stu-id="6e70e-283">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="6e70e-284">シミュレートされた人間の頭を取得します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-284">Retrieve the head of the simulated human</span></span>

<span data-ttu-id="6e70e-285">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="6e70e-285">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="6e70e-286">メートル単位で、現在位置を基準として、シミュレートされた人間を移動します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-286">Move the simulated human relative to its current position, in meters</span></span>

<span data-ttu-id="6e70e-287">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e70e-287">Parameters</span></span>
* <span data-ttu-id="6e70e-288">翻訳に移動して、現在の位置を基準に変換</span><span class="sxs-lookup"><span data-stu-id="6e70e-288">translation - The translation to move, relative to current position</span></span>

<span data-ttu-id="6e70e-289">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span><span class="sxs-lookup"><span data-stu-id="6e70e-289">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="6e70e-290">Y 軸を中心に時計回りに現在方向の基準とした、シミュレートされた人間を回転します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-290">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="6e70e-291">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e70e-291">Parameters</span></span>
* <span data-ttu-id="6e70e-292">ラジアン単位の Y 軸に沿って回転する量</span><span class="sxs-lookup"><span data-stu-id="6e70e-292">radians - The amount to rotate around the Y axis</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="6e70e-293">Microsoft.PerceptionSimulation.ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="6e70e-293">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="6e70e-294">シミュレートされた人間の手の形を記述するインターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="6e70e-294">Interface describing a hand of the simulated human</span></span>

```
public interface ISimulatedHand
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    bool Activated { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    bool Visible { [return: MarshalAs(UnmanagedType.Bool)] get; }
    void EnsureVisible();
    void Move(Vector3 translation);
    void PerformGesture(SimulatedGesture gesture);
}
```

<span data-ttu-id="6e70e-295">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="6e70e-295">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="6e70e-296">メートル単位で、世界中とに関してノードの位置を取得します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-296">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="6e70e-297">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span><span class="sxs-lookup"><span data-stu-id="6e70e-297">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="6e70e-298">取得し、メートル単位で、人間の基準とした、シミュレートされた手の形の位置を設定します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-298">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="6e70e-299">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span><span class="sxs-lookup"><span data-stu-id="6e70e-299">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="6e70e-300">取得し、手の形が現在アクティブかどうかを設定します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-300">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="6e70e-301">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span><span class="sxs-lookup"><span data-stu-id="6e70e-301">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="6e70e-302">手のアイコンが (つまり、かどうかは、HandTracker によって検出された位置に) SimulatedDevice に現在表示されているかどうかを取得します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-302">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="6e70e-303">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="6e70e-303">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="6e70e-304">SimulatedDevice に表示されるようにして手のアイコンに移動します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-304">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="6e70e-305">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="6e70e-305">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="6e70e-306">メートル単位で、現在位置を基準として、シミュレートされた手の形の位置を移動します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-306">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="6e70e-307">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e70e-307">Parameters</span></span>
* <span data-ttu-id="6e70e-308">翻訳 - シミュレートされた手の形を平行移動量</span><span class="sxs-lookup"><span data-stu-id="6e70e-308">translation - The amount to translate the simulated hand</span></span>

<span data-ttu-id="6e70e-309">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="6e70e-309">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="6e70e-310">(のみ検出されます、システムによって、手が有効になっている場合)、シミュレートされた手の形を使用するジェスチャを実行します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-310">Perform a gesture using the simulated hand (it will only be detected by the system if the hand is enabled).</span></span>

<span data-ttu-id="6e70e-311">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e70e-311">Parameters</span></span>
* <span data-ttu-id="6e70e-312">ジェスチャのジェスチャを実行するには</span><span class="sxs-lookup"><span data-stu-id="6e70e-312">gesture - The gesture to perform</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="6e70e-313">Microsoft.PerceptionSimulation.ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="6e70e-313">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="6e70e-314">シミュレートされた人間の頭を記述するインターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="6e70e-314">Interface describing the head of the simulated human</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="6e70e-315">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="6e70e-315">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="6e70e-316">メートル単位で、世界中とに関してノードの位置を取得します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-316">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="6e70e-317">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span><span class="sxs-lookup"><span data-stu-id="6e70e-317">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="6e70e-318">シミュレートされた先頭の回転角度を取得します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-318">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="6e70e-319">軸に検索するときに、正のラジアンは右回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-319">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="6e70e-320">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span><span class="sxs-lookup"><span data-stu-id="6e70e-320">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="6e70e-321">シミュレートされた先頭の直径を取得します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-321">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="6e70e-322">この値は、ヘッドのセンター (回転のポイント) を確認するに使用されます。</span><span class="sxs-lookup"><span data-stu-id="6e70e-322">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="6e70e-323">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="6e70e-323">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="6e70e-324">現在、回転の基準としたシミュレートされたヘッドを回転します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-324">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="6e70e-325">軸に検索するときに、正のラジアンは右回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-325">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="6e70e-326">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e70e-326">Parameters</span></span>
* <span data-ttu-id="6e70e-327">回転の量を回転するには</span><span class="sxs-lookup"><span data-stu-id="6e70e-327">rotation - The amount to rotate</span></span>

### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="6e70e-328">Microsoft.PerceptionSimulation.ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="6e70e-328">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="6e70e-329">再生用に 1 つの記録と対話するためのインターフェイスが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="6e70e-329">Interface for interacting with a single recording loaded for playback.</span></span>

```
public interface ISimulationRecording
{
    StreamDataTypes DataTypes { get; }
    PlaybackState State { get; }
    void Play();
    void Pause();
    void Seek(UInt64 ticks);
    void Stop();
};
```

<span data-ttu-id="6e70e-330">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span><span class="sxs-lookup"><span data-stu-id="6e70e-330">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="6e70e-331">記録のデータ型の一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-331">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="6e70e-332">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span><span class="sxs-lookup"><span data-stu-id="6e70e-332">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="6e70e-333">記録の現在の状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-333">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="6e70e-334">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span><span class="sxs-lookup"><span data-stu-id="6e70e-334">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="6e70e-335">再生を開始します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-335">Start the playback.</span></span> <span data-ttu-id="6e70e-336">記録を一時停止すると、再生が一時停止中の場所から再開されます。停止した場合、先頭に再生が開始されます。</span><span class="sxs-lookup"><span data-stu-id="6e70e-336">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="6e70e-337">既に再生中の場合は、この呼び出しは無視されます。</span><span class="sxs-lookup"><span data-stu-id="6e70e-337">If already playing, this call is ignored.</span></span>

<span data-ttu-id="6e70e-338">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span><span class="sxs-lookup"><span data-stu-id="6e70e-338">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="6e70e-339">現在の場所で再生を一時停止します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-339">Pauses the playback at its current location.</span></span> <span data-ttu-id="6e70e-340">記録が停止している場合、呼び出しは無視されます。</span><span class="sxs-lookup"><span data-stu-id="6e70e-340">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="6e70e-341">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span><span class="sxs-lookup"><span data-stu-id="6e70e-341">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="6e70e-342">(最初から 100 ナノ秒間隔) で指定された時間に、記録をシークし、その場所に一時停止します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-342">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="6e70e-343">時間が、記録の末尾を越える場合、最後のフレームで一時停止中です。</span><span class="sxs-lookup"><span data-stu-id="6e70e-343">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="6e70e-344">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e70e-344">Parameters</span></span>
* <span data-ttu-id="6e70e-345">タイマー刻みの時刻をシークします。</span><span class="sxs-lookup"><span data-stu-id="6e70e-345">ticks - The time to which to seek</span></span>

<span data-ttu-id="6e70e-346">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span><span class="sxs-lookup"><span data-stu-id="6e70e-346">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="6e70e-347">再生を停止し、先頭に位置をリセット</span><span class="sxs-lookup"><span data-stu-id="6e70e-347">Stops the playback and resets the position to the beginning</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="6e70e-348">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="6e70e-348">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="6e70e-349">再生中に状態の変更を受信するためのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="6e70e-349">Interface for receiving state changes during playback</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="6e70e-350">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="6e70e-350">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="6e70e-351">ISimulationRecording の再生の状態が変更されたときに呼び出されます</span><span class="sxs-lookup"><span data-stu-id="6e70e-351">Called when an ISimulationRecording's playback state has changed</span></span>

<span data-ttu-id="6e70e-352">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e70e-352">Parameters</span></span>
* <span data-ttu-id="6e70e-353">newState の記録の新しい状態</span><span class="sxs-lookup"><span data-stu-id="6e70e-353">newState - The new state of the recording</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="6e70e-354">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="6e70e-354">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="6e70e-355">Perception シミュレーション オブジェクトを作成するためのルート オブジェクト</span><span class="sxs-lookup"><span data-stu-id="6e70e-355">Root object for creating Perception Simulation objects</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="6e70e-356">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="6e70e-356">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="6e70e-357">シミュレートされたパケットを生成すると、指定されたシンクへの配信にオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-357">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="6e70e-358">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e70e-358">Parameters</span></span>
* <span data-ttu-id="6e70e-359">生成されたすべてのパケットを受信するシンクをシンクします。</span><span class="sxs-lookup"><span data-stu-id="6e70e-359">sink - The sink that will receive all generated packets</span></span>

<span data-ttu-id="6e70e-360">戻り値</span><span class="sxs-lookup"><span data-stu-id="6e70e-360">Return value</span></span>

<span data-ttu-id="6e70e-361">作成したマネージャー</span><span class="sxs-lookup"><span data-stu-id="6e70e-361">The created Manager</span></span>

<span data-ttu-id="6e70e-362">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span><span class="sxs-lookup"><span data-stu-id="6e70e-362">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="6e70e-363">指定したパスにあるファイルのすべての受信パケットを格納するシンクを作成します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-363">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="6e70e-364">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e70e-364">Parameters</span></span>
* <span data-ttu-id="6e70e-365">パス - 作成するファイルのパス</span><span class="sxs-lookup"><span data-stu-id="6e70e-365">path - The path of the file to create</span></span>

<span data-ttu-id="6e70e-366">戻り値</span><span class="sxs-lookup"><span data-stu-id="6e70e-366">Return value</span></span>

<span data-ttu-id="6e70e-367">作成したシンク</span><span class="sxs-lookup"><span data-stu-id="6e70e-367">The created sink</span></span>

<span data-ttu-id="6e70e-368">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="6e70e-368">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="6e70e-369">指定したファイルから、記録を読み込む</span><span class="sxs-lookup"><span data-stu-id="6e70e-369">Load a recording from the specified file</span></span>

<span data-ttu-id="6e70e-370">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e70e-370">Parameters</span></span>
* <span data-ttu-id="6e70e-371">読み込むファイルのパスのパス</span><span class="sxs-lookup"><span data-stu-id="6e70e-371">path - The path of the file to load</span></span>
* <span data-ttu-id="6e70e-372">工場出荷時のために必要なときに、ISimulationStreamSink を作成するため、記録することによって使用されるファクトリ</span><span class="sxs-lookup"><span data-stu-id="6e70e-372">factory - A factory used by the recording for creating an ISimulationStreamSink when required</span></span>

<span data-ttu-id="6e70e-373">戻り値</span><span class="sxs-lookup"><span data-stu-id="6e70e-373">Return value</span></span>

<span data-ttu-id="6e70e-374">読み込まれた記録</span><span class="sxs-lookup"><span data-stu-id="6e70e-374">The loaded recording</span></span>

<span data-ttu-id="6e70e-375">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory、Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="6e70e-375">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="6e70e-376">指定したファイルから、記録を読み込む</span><span class="sxs-lookup"><span data-stu-id="6e70e-376">Load a recording from the specified file</span></span>

<span data-ttu-id="6e70e-377">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e70e-377">Parameters</span></span>
* <span data-ttu-id="6e70e-378">読み込むファイルのパスのパス</span><span class="sxs-lookup"><span data-stu-id="6e70e-378">path - The path of the file to load</span></span>
* <span data-ttu-id="6e70e-379">工場出荷時のために必要なときに、ISimulationStreamSink を作成するため、記録することによって使用されるファクトリ</span><span class="sxs-lookup"><span data-stu-id="6e70e-379">factory - A factory used by the recording for creating an ISimulationStreamSink when required</span></span>
* <span data-ttu-id="6e70e-380">callback - コールバックを受け取る更新 regrading 記録の状態</span><span class="sxs-lookup"><span data-stu-id="6e70e-380">callback - A callback which receives updates regrading the recording's status</span></span>

<span data-ttu-id="6e70e-381">戻り値</span><span class="sxs-lookup"><span data-stu-id="6e70e-381">Return value</span></span>

<span data-ttu-id="6e70e-382">読み込まれた記録</span><span class="sxs-lookup"><span data-stu-id="6e70e-382">The loaded recording</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="6e70e-383">Microsoft.PerceptionSimulation.StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="6e70e-383">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="6e70e-384">ストリーム データのさまざまな種類について説明します</span><span class="sxs-lookup"><span data-stu-id="6e70e-384">Describes the different types of stream data</span></span>

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    All = None | Head | Hands | SpatialMapping | Calibration | Environment
}
```

<span data-ttu-id="6e70e-385">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span><span class="sxs-lookup"><span data-stu-id="6e70e-385">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="6e70e-386">ストリームのデータ型がない場合に使用される sentinel 値</span><span class="sxs-lookup"><span data-stu-id="6e70e-386">A sentinel value used to indicate no stream data types</span></span>

<span data-ttu-id="6e70e-387">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span><span class="sxs-lookup"><span data-stu-id="6e70e-387">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="6e70e-388">位置と、先頭の向きに関するデータの Stream</span><span class="sxs-lookup"><span data-stu-id="6e70e-388">Stream of data regarding the position and orientation of the head</span></span>

<span data-ttu-id="6e70e-389">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span><span class="sxs-lookup"><span data-stu-id="6e70e-389">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="6e70e-390">位置と手のジェスチャに関するデータの Stream</span><span class="sxs-lookup"><span data-stu-id="6e70e-390">Stream of data regarding the position and gestures of hands</span></span>

<span data-ttu-id="6e70e-391">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="6e70e-391">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="6e70e-392">環境の空間のマッピングに関するデータの Stream</span><span class="sxs-lookup"><span data-stu-id="6e70e-392">Stream of data regarding spatial mapping of the environment</span></span>

<span data-ttu-id="6e70e-393">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span><span class="sxs-lookup"><span data-stu-id="6e70e-393">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="6e70e-394">デバイスの調整に関するデータの Stream。</span><span class="sxs-lookup"><span data-stu-id="6e70e-394">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="6e70e-395">調整のパケットは、リモート モードでのシステムでのみ受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="6e70e-395">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="6e70e-396">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span><span class="sxs-lookup"><span data-stu-id="6e70e-396">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="6e70e-397">デバイスの環境に関するデータの Stream</span><span class="sxs-lookup"><span data-stu-id="6e70e-397">Stream of data regarding the environment of the device</span></span>

<span data-ttu-id="6e70e-398">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span><span class="sxs-lookup"><span data-stu-id="6e70e-398">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="6e70e-399">すべて記録されたデータ型を示すために使用される sentinel 値</span><span class="sxs-lookup"><span data-stu-id="6e70e-399">A sentinel value used to indicate all recorded data types</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="6e70e-400">Microsoft.PerceptionSimulation.ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="6e70e-400">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="6e70e-401">シミュレーションのストリームからデータ パケットを受信するオブジェクト</span><span class="sxs-lookup"><span data-stu-id="6e70e-401">An object that receives data packets from a simulation stream</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="6e70e-402">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived (uint の長さ、byte パケット)**</span><span class="sxs-lookup"><span data-stu-id="6e70e-402">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="6e70e-403">内部的に型指定されたおよびバージョン管理は、1 つのパケットを受信します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-403">Receives a single packet, which is internally typed and versioned</span></span>

<span data-ttu-id="6e70e-404">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e70e-404">Parameters</span></span>
* <span data-ttu-id="6e70e-405">length - パケットの長さ</span><span class="sxs-lookup"><span data-stu-id="6e70e-405">length - The length of the packet</span></span>
* <span data-ttu-id="6e70e-406">パケットのパケットのデータ</span><span class="sxs-lookup"><span data-stu-id="6e70e-406">packet - The data of the packet</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="6e70e-407">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="6e70e-407">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="6e70e-408">ISimulationStreamSink を作成するオブジェクト</span><span class="sxs-lookup"><span data-stu-id="6e70e-408">An object that creates ISimulationStreamSink</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="6e70e-409">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span><span class="sxs-lookup"><span data-stu-id="6e70e-409">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="6e70e-410">ISimulationStreamSink の 1 つのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="6e70e-410">Creates a single instance of ISimulationStreamSink</span></span>

<span data-ttu-id="6e70e-411">戻り値</span><span class="sxs-lookup"><span data-stu-id="6e70e-411">Return value</span></span>

<span data-ttu-id="6e70e-412">作成したシンク</span><span class="sxs-lookup"><span data-stu-id="6e70e-412">The created sink</span></span>
