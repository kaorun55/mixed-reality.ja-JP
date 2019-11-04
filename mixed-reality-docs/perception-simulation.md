---
title: 認識シミュレーション
description: 知覚シミュレーションライブラリを使用して、イマーシブアプリケーションのシミュレートされた入力を自動化するためのガイド
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: HoloLens、シミュレーション、テスト
ms.openlocfilehash: 503533bc5a2e9307b7c5217632d42670285aac0a
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437548"
---
# <a name="perception-simulation"></a><span data-ttu-id="8a1b2-104">認識シミュレーション</span><span class="sxs-lookup"><span data-stu-id="8a1b2-104">Perception simulation</span></span>

<span data-ttu-id="8a1b2-105">アプリの自動テストをビルドしますか?</span><span class="sxs-lookup"><span data-stu-id="8a1b2-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="8a1b2-106">テストをコンポーネントレベルの単体テストよりも先に実行し、アプリをエンドツーエンドで実際に練習しますか。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="8a1b2-107">認識シミュレーションは、探しているものです。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="8a1b2-108">認識シミュレーションライブラリは、アプリに人間と世界の入力データを送信して、テストを自動化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="8a1b2-109">たとえば、特定の反復可能な位置に対する人間の入力をシミュレートし、ジェスチャを実行したり、モーションコントローラーを使用したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="8a1b2-110">認識シミュレーションでは、このようなシミュレートされた入力を物理 HoloLens、HoloLens エミュレーター (第1世代)、HoloLens 2 エミュレーター、または Mixed Reality ポータルがインストールされている PC に送信できます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="8a1b2-111">認識シミュレーションは、混合の現実のデバイスでライブセンサーをバイパスし、デバイスで実行されているアプリケーションにシミュレートされた入力を送信します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="8a1b2-112">アプリケーションでは、これらの入力イベントを、常に使用するものと同じ Api を使用して受信します。また、実際のセンサーでの実行と知覚シミュレーションでの実行の違いを示すことはできません。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="8a1b2-113">認識シミュレーションは、シミュレートされた入力を HoloLens 仮想マシンに送信するために HoloLens エミュレーターで使用されるものと同じテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="8a1b2-114">コードでのシミュレーションの使用を開始するには、まず IPerceptionSimulationManager オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="8a1b2-115">そのオブジェクトから、コマンドを発行して、"人間" のようなシミュレートされた "ユーザー" のプロパティを制御することができます。これには、head 位置、針、ジェスチャなどがあります。また、モーションコントローラーを有効にしたり操作したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="8a1b2-116">認識シミュレーションのための Visual Studio プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="8a1b2-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="8a1b2-117">開発用 PC に[HoloLens エミュレーターをインストール](install-the-tools.md)します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="8a1b2-118">エミュレーターには、認識シミュレーションに使用するライブラリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="8a1b2-119">新しい Visual Studio C#デスクトッププロジェクトを作成します (コンソールプロジェクトは、作業を開始するのに適しています)。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="8a1b2-120">次のバイナリを参照としてプロジェクトに追加します (プロジェクト > 追加 > 参照...)。これらは、HoloLens 2 エミュレーターの% **ProgramFiles (x86)% \ microsoft xde\\10.0.18362.0**などの% ProgramFiles (x86)% \ microsoft xde\\(バージョン) で見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="8a1b2-121">(注: バイナリは HoloLens 2 エミュレーターに含まれていますが、デスクトップ上の Windows Mixed Reality でも機能します)。ある.</span><span class="sxs-lookup"><span data-stu-id="8a1b2-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="8a1b2-122">認識シミュレーション用の PerceptionSimulationManager マネージC#ラッパー。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="8a1b2-123">b.</span><span class="sxs-lookup"><span data-stu-id="8a1b2-123">b.</span></span> <span data-ttu-id="8a1b2-124">PerceptionSimulationRest-HoloLens またはエミュレーターに対する web ソケット通信チャネルを設定するためのライブラリ。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="8a1b2-125">c.</span><span class="sxs-lookup"><span data-stu-id="8a1b2-125">c.</span></span> <span data-ttu-id="8a1b2-126">SimulationStream-シミュレーション用の共有型。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="8a1b2-127">実装バイナリ PerceptionSimulationManager をプロジェクト a に追加します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="8a1b2-128">まず、これをバイナリとしてプロジェクトに追加します (プロジェクト > 追加 > 既存の項目...)。プロジェクトソースフォルダーにコピーしないように、リンクとして保存します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="8a1b2-129">PerceptionSimulationManager をリンクとしてプロジェクトに追加 ![b](images/saveaslink.png) ます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="8a1b2-130">次に、ビルド時に出力フォルダーにコピーされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="8a1b2-131">これは、バイナリのプロパティシートにあります。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="8a1b2-132">PerceptionSimulationManager マークを付けて、出力ディレクトリにコピー ![](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="8a1b2-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="8a1b2-133">アクティブソリューションプラットフォームを x64 に設定します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="8a1b2-134">(Configuration Manager を使用して、x64 用のプラットフォームエントリがまだ存在しない場合は作成します)。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="8a1b2-135">IPerceptionSimulation Manager オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="8a1b2-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="8a1b2-136">シミュレーションを制御するには、IPerceptionSimulationManager オブジェクトから取得したオブジェクトに更新を発行します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="8a1b2-137">最初の手順では、そのオブジェクトを取得し、ターゲットデバイスまたはエミュレーターに接続します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="8a1b2-138">エミュレーターの IP アドレスを取得するには、[ツールバー](using-the-hololens-emulator.md)の [デバイスポータル] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="8a1b2-139">![デバイスポータルを開く アイコン](images/emulator-deviceportal.png) 開いている**デバイスポータル**: エミュレーターで HoloLens OS の Windows デバイスポータルを開きます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="8a1b2-140">Windows Mixed Reality の場合、この設定は、[デバイスポータルを有効にする] の下にある [Connect & Security] (セキュリティの更新) の下にある [設定] アプリで取得できます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="8a1b2-141">IP アドレスとポートの両方に注意してください。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="8a1b2-142">まず、RestSimulationStreamSink を呼び出して、RestSimulationStreamSink オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="8a1b2-143">これは、http 接続を介して制御するターゲットデバイスまたはエミュレーターです。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="8a1b2-144">コマンドは、デバイスまたはエミュレーターで実行されている[Windows デバイスポータル](using-the-windows-device-portal.md)に渡され、処理されます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="8a1b2-145">オブジェクトを作成するには、次の4つのパラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="8a1b2-146">Uri uri-ターゲットデバイスの IP アドレス (例: "https://123.123.123.123" または "https://123.123.123.123:50080")</span><span class="sxs-lookup"><span data-stu-id="8a1b2-146">Uri uri - IP address of the target device (e.g., "https://123.123.123.123" or "https://123.123.123.123:50080")</span></span>
* <span data-ttu-id="8a1b2-147">System .Net. NetworkCredential 資格情報-ターゲットデバイスまたはエミュレーターで[Windows デバイスポータル](using-the-windows-device-portal.md)に接続するためのユーザー名/パスワード。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="8a1b2-148">ローカルアドレスを使用してエミュレーターに接続している場合 (例: 168 *...* \*) 同じ PC で、すべての資格情報が受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-148">If you are connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="8a1b2-149">bool normal-通常の優先度の場合は True、低優先度の場合は false。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="8a1b2-150">テストシナリオでは、通常、これを*true*に設定して、テストで制御を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="8a1b2-151">エミュレーターと Windows Mixed Reality のシミュレーションでは、優先度の低い接続を使用します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="8a1b2-152">テストで優先度の低い接続も使用している場合は、最後に確立された接続が制御されます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="8a1b2-153">CancellationToken は、非同期操作を取り消すためのトークンです。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="8a1b2-154">次に、IPerceptionSimulationManager を作成します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="8a1b2-155">これは、シミュレーションの制御に使用するオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="8a1b2-156">これは、非同期メソッドでも実行する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="8a1b2-157">シミュレートされた人間を制御する</span><span class="sxs-lookup"><span data-stu-id="8a1b2-157">Control the simulated Human</span></span>

<span data-ttu-id="8a1b2-158">IPerceptionSimulationManager には、ISimulatedHuman オブジェクトを返すヒューマンプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="8a1b2-159">シミュレートされた人間を制御するには、このオブジェクトに対して操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="8a1b2-160">次に、例を示します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="8a1b2-161">基本的なC#サンプルコンソールアプリケーション</span><span class="sxs-lookup"><span data-stu-id="8a1b2-161">Basic Sample C# console application</span></span>

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
                RestSimulationStreamSink sink = null;
                CancellationToken token = new System.Threading.CancellationToken();

                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }

                // Always close the sink to return control to the previous application.
                if (sink != null)
                {
                    await sink.Close(token);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="8a1b2-162">拡張サンプルC#コンソールアプリケーション</span><span class="sxs-lookup"><span data-stu-id="8a1b2-162">Extended Sample C# console application</span></span>

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
            RestSimulationStreamSink sink = null;
            CancellationToken token = new System.Threading.CancellationToken();

            Task.Run(async () =>
            {
                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

                    // Activate the right hand
                    manager.Human.RightHand.Activated = true;

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

            // Always close the sink to return control to the previous application.
            if (sink != null)
            {
                sink.Close(token);
            }
        }
    }
}
```

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="8a1b2-163">6つの自由度コントローラーに関する注意</span><span class="sxs-lookup"><span data-stu-id="8a1b2-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="8a1b2-164">シミュレートされた6つの自由コントローラーでメソッドのプロパティを呼び出す前に、コントローラーをアクティブにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="8a1b2-165">そうしないと、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="8a1b2-166">Windows 10 2019 年5月の更新プログラムでは、ISimulatedSixDofController オブジェクトの Status プロパティを SimulatedSixDofControllerStatus に設定することにより、シミュレートされた6つの自由度コントローラーをインストールしてアクティブ化することができます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="8a1b2-167">Windows 10 10 月2018更新プログラムおよびそれ以前のバージョンでは、\Windows\System32 フォルダーにある PerceptionSimulationDevice ツールを呼び出して、シミュレートされた6自由コントローラーを最初に個別にインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="8a1b2-168">このツールの使用方法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="8a1b2-169">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="8a1b2-170">サポートされているアクションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-170">Supported actions are:</span></span>
* <span data-ttu-id="8a1b2-171">i = インストール</span><span class="sxs-lookup"><span data-stu-id="8a1b2-171">i = install</span></span>
* <span data-ttu-id="8a1b2-172">q = クエリ</span><span class="sxs-lookup"><span data-stu-id="8a1b2-172">q = query</span></span>
* <span data-ttu-id="8a1b2-173">r = 削除</span><span class="sxs-lookup"><span data-stu-id="8a1b2-173">r = remove</span></span>

<span data-ttu-id="8a1b2-174">サポートされているインスタンスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-174">Supported instances are:</span></span>
* <span data-ttu-id="8a1b2-175">1 = 左6自由コントローラー</span><span class="sxs-lookup"><span data-stu-id="8a1b2-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="8a1b2-176">2 = 右6自由コントローラー</span><span class="sxs-lookup"><span data-stu-id="8a1b2-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="8a1b2-177">プロセスの終了コードは、成功 (ゼロの戻り値) または失敗 (0 以外の戻り値) を示します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="8a1b2-178">' Q ' アクションを使用してコントローラーがインストールされているかどうかを照会する場合、コントローラーがまだインストールされていない場合は戻り値が0になり、コントローラーがインストールされている場合は1が返されます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="8a1b2-179">Windows 10 10 月2018更新プログラムまたはそれ以前のバージョンでコントローラーを削除する場合は、最初に API を使用して状態を Off に設定してから、PerceptionSimulationDevice ツールを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="8a1b2-180">このツールは管理者として実行する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="8a1b2-181">API リファレンス</span><span class="sxs-lookup"><span data-stu-id="8a1b2-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="8a1b2-182">PerceptionSimulation. SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="8a1b2-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="8a1b2-183">シミュレートされたデバイスの種類について説明します</span><span class="sxs-lookup"><span data-stu-id="8a1b2-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="8a1b2-184">**PerceptionSimulation. SimulatedDeviceType**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="8a1b2-185">架空の参照デバイス (PerceptionSimulationManager の既定値)</span><span class="sxs-lookup"><span data-stu-id="8a1b2-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="8a1b2-186">PerceptionSimulation... Trackermode</span><span class="sxs-lookup"><span data-stu-id="8a1b2-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="8a1b2-187">ヘッドトラッカーモードについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="8a1b2-188">**PerceptionSimulation。既定値の場合**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="8a1b2-189">既定のヘッド追跡。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-189">Default Head Tracking.</span></span> <span data-ttu-id="8a1b2-190">これは、システムが実行時の状況に基づいて最適なヘッド追跡モードを選択することを意味します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="8a1b2-191">**PerceptionSimulation のようになります。**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="8a1b2-192">方向のみのヘッド追跡。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="8a1b2-193">これは、追跡される位置が信頼できない可能性があり、head 位置に依存する一部の機能が使用できない場合があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="8a1b2-194">**PerceptionSimulation を移動します。**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="8a1b2-195">位置指定のヘッド追跡。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-195">Positional Head Tracking.</span></span> <span data-ttu-id="8a1b2-196">これは、追跡されるヘッドの位置と向きは両方とも信頼できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="8a1b2-197">PerceptionSimulation. SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="8a1b2-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="8a1b2-198">シミュレートされたジェスチャについて説明します</span><span class="sxs-lookup"><span data-stu-id="8a1b2-198">Describes a simulated gesture</span></span>

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

<span data-ttu-id="8a1b2-199">**PerceptionSimulation. SimulatedGesture**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="8a1b2-200">ジェスチャがないことを示すために使用される sentinel 値。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="8a1b2-201">**PerceptionSimulation. SimulatedGesture. FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="8a1b2-202">指押下ジェスチャ。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-202">A finger pressed gesture.</span></span>

<span data-ttu-id="8a1b2-203">**PerceptionSimulation. SimulatedGesture. FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="8a1b2-204">指で離されたジェスチャ。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-204">A finger released gesture.</span></span>

<span data-ttu-id="8a1b2-205">**PerceptionSimulation. SimulatedGesture**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="8a1b2-206">ホーム/システムジェスチャ。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-206">The home/system gesture.</span></span>

<span data-ttu-id="8a1b2-207">**PerceptionSimulation. SimulatedGesture**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="8a1b2-208">有効なジェスチャの最大数。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="8a1b2-209">PerceptionSimulation. SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="8a1b2-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="8a1b2-210">シミュレートされた6自由コントローラーの可能性のある状態。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="8a1b2-211">**PerceptionSimulation. SimulatedSixDofControllerStatus**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="8a1b2-212">6自由コントローラーがオフになっています。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="8a1b2-213">**PerceptionSimulation. SimulatedSixDofControllerStatus**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="8a1b2-214">6自由コントローラーが有効になり、追跡されます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="8a1b2-215">**PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="8a1b2-216">6自由度コントローラーはオンになっていますが、追跡することはできません。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="8a1b2-217">PerceptionSimulation. SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="8a1b2-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="8a1b2-218">シミュレートされた6自由コントローラーでサポートされるボタン。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-218">The supported buttons on a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerButton
{
    None = 0,
    Home = 1,
    Menu = 2,
    Grip = 4,
    TouchpadPress = 8,
    Select = 16,
    TouchpadTouch = 32,
    Thumbstick = 64,
    Max = Thumbstick
}
```

<span data-ttu-id="8a1b2-219">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="8a1b2-220">ボタンを指定するために使用される sentinel 値。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="8a1b2-221">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="8a1b2-222">[ホーム] ボタンが押された状態になります。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-222">The Home button is pressed.</span></span>

<span data-ttu-id="8a1b2-223">**PerceptionSimulation. SimulatedSixDofControllerButton. メニュー**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="8a1b2-224">メニューボタンが押された状態になります。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-224">The Menu button is pressed.</span></span>

<span data-ttu-id="8a1b2-225">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="8a1b2-226">グリップボタンが押された状態になります。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-226">The Grip button is pressed.</span></span>

<span data-ttu-id="8a1b2-227">**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="8a1b2-228">タッチパッドが押された状態になります。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="8a1b2-229">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="8a1b2-230">[選択] ボタンが押された状態になります。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-230">The Select button is pressed.</span></span>

<span data-ttu-id="8a1b2-231">**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="8a1b2-232">タッチパッドがタッチされます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-232">The TouchPad is touched.</span></span>

<span data-ttu-id="8a1b2-233">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="8a1b2-234">サムスティックが押されています。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="8a1b2-235">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="8a1b2-236">最大有効なボタン。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="8a1b2-237">PerceptionSimulation. SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="8a1b2-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="8a1b2-238">シミュレートされた目の調整状態</span><span class="sxs-lookup"><span data-stu-id="8a1b2-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="8a1b2-239">**PerceptionSimulation. SimulatedEyesCalibrationState.**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="8a1b2-240">目の調整は使用できません。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="8a1b2-241">**PerceptionSimulation. SimulatedEyesCalibrationState**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="8a1b2-242">目が調整されました。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="8a1b2-243">これは既定値です。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-243">This is the default value.</span></span>

<span data-ttu-id="8a1b2-244">**PerceptionSimulation. SimulatedEyesCalibrationState**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="8a1b2-245">目が調整されています。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="8a1b2-246">**PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="8a1b2-247">目を調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="8a1b2-248">PerceptionSimulation. SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="8a1b2-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="8a1b2-249">手の継手の追跡精度。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="8a1b2-250">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy.**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="8a1b2-251">ジョイントは追跡されません。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-251">The joint is not tracked.</span></span>

<span data-ttu-id="8a1b2-252">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="8a1b2-253">ジョイント位置が推論されます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-253">The joint position is inferred.</span></span>

<span data-ttu-id="8a1b2-254">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="8a1b2-255">ジョイントは完全に追跡されます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="8a1b2-256">PerceptionSimulation. SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="8a1b2-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="8a1b2-257">手の継手の追跡精度。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-257">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandPose
{
    Closed = 0,
    Open = 1,
    Point = 2,
    Pinch = 3,
    Max = Pinch
}
```

<span data-ttu-id="8a1b2-258">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="8a1b2-259">ハンドの指継手は、終了したポーズを反映するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="8a1b2-260">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="8a1b2-261">手の指継手は、オープンなポーズを反映するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="8a1b2-262">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="8a1b2-263">ハンドの指継手は、ポイントのポーズを反映するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="8a1b2-264">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="8a1b2-265">手の指継手は、ピンチのポーズを反映するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="8a1b2-266">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="8a1b2-267">SimulatedHandPose の最大有効値。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="8a1b2-268">PerceptionSimulation の状態</span><span class="sxs-lookup"><span data-stu-id="8a1b2-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="8a1b2-269">再生の状態を記述します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="8a1b2-270">**PerceptionSimulation が停止しました。**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="8a1b2-271">記録は現在停止しており、再生の準備ができています。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="8a1b2-272">**PerceptionSimulation を再生します。**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="8a1b2-273">記録は現在再生中です。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-273">The recording is currently playing.</span></span>

<span data-ttu-id="8a1b2-274">**PerceptionSimulation が一時停止しました。**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="8a1b2-275">記録は現在一時停止されています。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-275">The recording is currently paused.</span></span>

<span data-ttu-id="8a1b2-276">**PerceptionSimulation を終了します。**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="8a1b2-277">記録が最後に達しました。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="8a1b2-278">PerceptionSimulation. Vector3</span><span class="sxs-lookup"><span data-stu-id="8a1b2-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="8a1b2-279">3D 空間の点またはベクターを表す3つのコンポーネントベクターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="8a1b2-280">**PerceptionSimulation. Vector3**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="8a1b2-281">ベクターの X 成分。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-281">The X component of the vector.</span></span>

<span data-ttu-id="8a1b2-282">**PerceptionSimulation. Vector3**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="8a1b2-283">ベクターの Y 成分。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-283">The Y component of the vector.</span></span>

<span data-ttu-id="8a1b2-284">**PerceptionSimulation. Vector3**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="8a1b2-285">ベクターの Z 成分。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-285">The Z component of the vector.</span></span>

<span data-ttu-id="8a1b2-286">**#Ctor PerceptionSimulation (system.string、system.string、system.string) を (system.string) します。**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="8a1b2-287">新しい Vector3 を構築します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-287">Construct a new Vector3.</span></span>

<span data-ttu-id="8a1b2-288">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a1b2-288">Parameters</span></span>
* <span data-ttu-id="8a1b2-289">x-ベクトルの x 成分。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="8a1b2-290">y-ベクトルの y 成分。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="8a1b2-291">z-ベクトルの z 成分。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="8a1b2-292">PerceptionSimulation. Rotation3</span><span class="sxs-lookup"><span data-stu-id="8a1b2-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="8a1b2-293">3つのコンポーネントのローテーションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="8a1b2-294">**PerceptionSimulation. Rotation3**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="8a1b2-295">X 軸を中心とする回転のピッチ成分。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="8a1b2-296">**PerceptionSimulation. Rotation3**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="8a1b2-297">Y 軸を中心とする回転のヨー要素。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="8a1b2-298">**PerceptionSimulation. Rotation3**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="8a1b2-299">Z 軸を中心とする回転のロールコンポーネント。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="8a1b2-300">**#Ctor PerceptionSimulation (system.string、system.string、system.string) を (system.string) します。**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="8a1b2-301">新しい Rotation3 を構築します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="8a1b2-302">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a1b2-302">Parameters</span></span>
* <span data-ttu-id="8a1b2-303">ピッチ-回転のピッチ成分。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="8a1b2-304">ヨー-回転のヨーコンポーネント。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="8a1b2-305">roll-回転のロールコンポーネント。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="8a1b2-306">PerceptionSimulation. SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="8a1b2-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="8a1b2-307">シミュレートされたハンドでのジョイントの構成について説明します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="8a1b2-308">**PerceptionSimulation. SimulatedHandJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="8a1b2-309">ジョイントの位置。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-309">The position of the joint.</span></span>

<span data-ttu-id="8a1b2-310">**PerceptionSimulation. SimulatedHandJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="8a1b2-311">ジョイントの回転。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-311">The rotation of the joint.</span></span>

<span data-ttu-id="8a1b2-312">**PerceptionSimulation. SimulatedHandJointConfiguration の精度**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="8a1b2-313">ジョイントの追跡精度。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="8a1b2-314">PerceptionSimulation</span><span class="sxs-lookup"><span data-stu-id="8a1b2-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="8a1b2-315">カメラで一般的に使用される、視錐のビューについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="8a1b2-316">**PerceptionSimulation。 Near**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="8a1b2-317">視錐に含まれる最小距離。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="8a1b2-318">**PerceptionSimulation です。**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="8a1b2-319">視錐に含まれる最大距離。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="8a1b2-320">**PerceptionSimulation. FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="8a1b2-321">視錐のビューの水平方向のフィールド (π未満のラジアン)。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="8a1b2-322">**PerceptionSimulation. AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="8a1b2-323">ビューの垂直方向のフィールドから、ビューの垂直方向のフィールドまでの比率。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="8a1b2-324">PerceptionSimulation. IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="8a1b2-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="8a1b2-325">デバイスの制御に使用されるパケットを生成するためのルート。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-325">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="8a1b2-326">**PerceptionSimulation. IPerceptionSimulationManager**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="8a1b2-327">シミュレートされた人間とシミュレートされた世界を解釈する、シミュレートされたデバイスオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-327">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="8a1b2-328">**PerceptionSimulation. IPerceptionSimulationManager**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="8a1b2-329">シミュレートされた人間を制御するオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-329">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="8a1b2-330">**PerceptionSimulation. IPerceptionSimulationManager**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="8a1b2-331">シミュレーションを既定の状態にリセットします。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-331">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="8a1b2-332">PerceptionSimulation. ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="8a1b2-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="8a1b2-333">シミュレートされた世界とシミュレートされた人間を解釈するデバイスを記述するインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8a1b2-333">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="8a1b2-334">**PerceptionSimulation. ISimulatedDevice Tracker**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="8a1b2-335">シミュレートされたデバイスからヘッドトラッカーを取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-335">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="8a1b2-336">**PerceptionSimulation. ISimulatedDevice Tracker**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="8a1b2-337">シミュレートされたデバイスからハンドトラッカーを取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-337">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="8a1b2-338">**PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType (PerceptionSimulation. SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="8a1b2-339">シミュレートされたデバイスのプロパティを、指定したデバイスの種類に合わせて設定します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-339">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="8a1b2-340">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a1b2-340">Parameters</span></span>
* <span data-ttu-id="8a1b2-341">type-シミュレートされたデバイスの新しい種類</span><span class="sxs-lookup"><span data-stu-id="8a1b2-341">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="8a1b2-342">PerceptionSimulation. ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="8a1b2-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="8a1b2-343">シミュレートされた人間の頭を追跡する、シミュレートされたデバイスの部分を説明するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-343">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="8a1b2-344">**PerceptionSimulation. ISimulatedHeadTracker.-Trackermode**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="8a1b2-345">現在のヘッドトラッカーモードを取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-345">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="8a1b2-346">PerceptionSimulation. ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="8a1b2-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="8a1b2-347">シミュレートされた人間の手を追跡するシミュレートされたデバイスの部分を説明するインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8a1b2-347">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="8a1b2-348">**PerceptionSimulation. ISimulatedHandTracker. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="8a1b2-349">世界のリレーションを使用してノードの位置をメートル単位で取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-349">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="8a1b2-350">**PerceptionSimulation. ISimulatedHandTracker**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="8a1b2-351">頭の中心を基準とした、シミュレートされたハンドトラッカーの位置を取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-351">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="8a1b2-352">**PerceptionSimulation. ISimulatedHandTracker**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="8a1b2-353">シミュレートされたハンドトラッカーの下向きのピッチを取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-353">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="8a1b2-354">**PerceptionSimulation は無視されました。**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="8a1b2-355">シミュレートされたハンドトラッカーを無視するかどうかを取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-355">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="8a1b2-356">無視すると、両方のハンドが常に表示されます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-356">When ignored, both hands are always visible.</span></span> <span data-ttu-id="8a1b2-357">無視しない場合 (既定)、ハンドトラッカーの視錐の内側にいる場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-357">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="8a1b2-358">**PerceptionSimulation. ISimulatedHandTracker**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="8a1b2-359">ハンドがシミュレートされたハンドトラッカーに表示されるかどうかを判断するために使用する、視錐のプロパティを取得および設定します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-359">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="8a1b2-360">PerceptionSimulation. ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="8a1b2-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="8a1b2-361">シミュレートされた人間を制御する最上位のインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-361">Top level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="8a1b2-362">**PerceptionSimulation. ISimulatedHuman. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="8a1b2-363">世界中のノードの位置をメートル単位で取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-363">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="8a1b2-364">この位置は、人間のフィートの中央の点に対応しています。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-364">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="8a1b2-365">**PerceptionSimulation. ISimulatedHuman**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="8a1b2-366">世界中のシミュレートされた人間の顔の方向を取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-366">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="8a1b2-367">0ラジアンは負の Z 軸を中心にします。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-367">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="8a1b2-368">正のラジアンは、Y 軸について時計回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-368">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="8a1b2-369">**PerceptionSimulation. ISimulatedHuman**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="8a1b2-370">シミュレートされた人間の高さをメートル単位で取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-370">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="8a1b2-371">**PerceptionSimulation. ISimulatedHuman. LeftHand**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="8a1b2-372">シミュレートされた人間の左側を取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-372">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="8a1b2-373">**PerceptionSimulation. ISimulatedHuman. 右**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="8a1b2-374">シミュレートされた人間の右側を取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-374">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="8a1b2-375">**PerceptionSimulation. ISimulatedHuman**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="8a1b2-376">シミュレートされた人間の先頭を取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-376">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="8a1b2-377">**PerceptionSimulation (ISimulatedHuman) (PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="8a1b2-378">シミュレートされた人間を、現在の位置を基準としてメートル単位で移動します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-378">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="8a1b2-379">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a1b2-379">Parameters</span></span>
* <span data-ttu-id="8a1b2-380">translation-現在の位置を基準とした、移動する平行移動。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-380">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="8a1b2-381">**PerceptionSimulation. ISimulatedHuman (System. Single)**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="8a1b2-382">現在の方向を基準にして、シミュレートされた人間を Y 軸に対して時計回りに回転させます</span><span class="sxs-lookup"><span data-stu-id="8a1b2-382">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="8a1b2-383">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a1b2-383">Parameters</span></span>
* <span data-ttu-id="8a1b2-384">ラジアン-Y 軸を中心に回転する量。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-384">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="8a1b2-385">PerceptionSimulation. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="8a1b2-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="8a1b2-386">ISimulatedHuman を ISimulatedHuman2 にキャストすると、追加のプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-386">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="8a1b2-387">**PerceptionSimulation. ISimulatedHuman2 Controller**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="8a1b2-388">左6自由コントローラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-388">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="8a1b2-389">**PerceptionSimulation. ISimulatedHuman2 コントローラー**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="8a1b2-390">右6自由コントローラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-390">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="8a1b2-391">PerceptionSimulation. ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="8a1b2-391">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="8a1b2-392">シミュレートされた人間の手を記述するインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8a1b2-392">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="8a1b2-393">**PerceptionSimulation. ISimulatedHand. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="8a1b2-394">世界のリレーションを使用してノードの位置をメートル単位で取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-394">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="8a1b2-395">**PerceptionSimulation. ISimulatedHand**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="8a1b2-396">人間に対するシミュレートされたハンドの位置をメートル単位で取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-396">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="8a1b2-397">**PerceptionSimulation. ISimulatedHand**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="8a1b2-398">ハンドが現在アクティブになっているかどうかを取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-398">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="8a1b2-399">**PerceptionSimulation. ISimulatedHand**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="8a1b2-400">SimulatedDevice に手が現在表示されているかどうかを取得します (この位置が、[ツール] で検出される位置にあるかどうか)。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-400">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="8a1b2-401">\**PerceptionSimulation. ISimulatedHand. Ensurevisible\**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="8a1b2-402">SimulatedDevice に見えるようにハンドを移動します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-402">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="8a1b2-403">**PerceptionSimulation (ISimulatedHand) (PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="8a1b2-404">シミュレートされたハンドの位置を、現在の位置を基準としてメートル単位で移動します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-404">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="8a1b2-405">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a1b2-405">Parameters</span></span>
* <span data-ttu-id="8a1b2-406">translation-シミュレートされたハンドを変換する量。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-406">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="8a1b2-407">**ISimulatedHand (PerceptionSimulation) () (PerceptionSimulation)**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="8a1b2-408">シミュレートされたハンドを使用してジェスチャを実行します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-408">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="8a1b2-409">ハンドが有効になっている場合にのみ、システムによって検出されます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-409">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="8a1b2-410">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a1b2-410">Parameters</span></span>
* <span data-ttu-id="8a1b2-411">ジェスチャ-実行するジェスチャ。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-411">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="8a1b2-412">PerceptionSimulation. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="8a1b2-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="8a1b2-413">ISimulatedHand を ISimulatedHand2 にキャストすると、追加のプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-413">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="8a1b2-414">**PerceptionSimulation. ISimulatedHand2**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="8a1b2-415">シミュレートされたハンドの回転を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-415">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="8a1b2-416">正のラジアンは、軸に沿って表示すると時計回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-416">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="8a1b2-417">PerceptionSimulation. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="8a1b2-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="8a1b2-418">ISimulatedHand を ISimulatedHand3 にキャストすると、追加のプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-418">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="8a1b2-419">**PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="8a1b2-420">指定されたジョイントの共同構成を取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-420">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="8a1b2-421">**PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="8a1b2-422">指定されたジョイントの結合構成を設定します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-422">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="8a1b2-423">**PerceptionSimulation. ISimulatedHand3. SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="8a1b2-424">アニメーション化するオプションのフラグを持つ既知のポーズにハンドを設定します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-424">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="8a1b2-425">注: アニメーション化によって、最終的な結合構成がすぐに反映されることはありません。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-425">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="8a1b2-426">PerceptionSimulation. ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="8a1b2-426">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="8a1b2-427">シミュレートされた人間の先頭を記述するインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-427">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="8a1b2-428">**PerceptionSimulation. ISimulatedHead. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="8a1b2-429">世界のリレーションを使用してノードの位置をメートル単位で取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-429">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="8a1b2-430">**PerceptionSimulation. ISimulatedHead**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="8a1b2-431">シミュレートされたヘッドの回転を取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-431">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="8a1b2-432">正のラジアンは、軸に沿って表示すると時計回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-432">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="8a1b2-433">**PerceptionSimulation. ISimulatedHead**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="8a1b2-434">シミュレートされたヘッドの直径を取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-434">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="8a1b2-435">この値は、ヘッドの中心 (回転点) を決定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-435">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="8a1b2-436">**PerceptionSimulation (ISimulatedHead) (PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="8a1b2-437">シミュレートされた頭を現在の回転に対して回転します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-437">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="8a1b2-438">正のラジアンは、軸に沿って表示すると時計回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-438">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="8a1b2-439">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a1b2-439">Parameters</span></span>
* <span data-ttu-id="8a1b2-440">rotation-回転する量。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-440">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="8a1b2-441">PerceptionSimulation. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="8a1b2-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="8a1b2-442">ISimulatedHead を ISimulatedHead2 にキャストすると、追加のプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-442">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="8a1b2-443">**PerceptionSimulation. ISimulatedHead2**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="8a1b2-444">シミュレートされた人間の目を取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-444">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="8a1b2-445">PerceptionSimulation. ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="8a1b2-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="8a1b2-446">シミュレートされた人間に関連付けられた6自由コントローラーを記述するインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-446">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

```
public interface ISimulatedSixDofController
{
    Vector3 WorldPosition { get; }
    SimulatedSixDofControllerStatus Status { get; set; }
    Vector3 Position { get; }
    Rotation3 Orientation { get; set; }
    void Move(Vector3 translation);
    void PressButton(SimulatedSixDofControllerButton button);
    void ReleaseButton(SimulatedSixDofControllerButton button);
    void GetTouchpadPosition(out float x, out float y);
    void SetTouchpadPosition(float x, float y);
}
```

<span data-ttu-id="8a1b2-447">**PerceptionSimulation. ISimulatedSixDofController. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="8a1b2-448">世界のリレーションを使用してノードの位置をメートル単位で取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-448">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="8a1b2-449">**PerceptionSimulation. ISimulatedSixDofController**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="8a1b2-450">コントローラーの現在の状態を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-450">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="8a1b2-451">移動、回転、または押すボタンの呼び出しが成功する前に、コントローラーの状態が Off 以外の値に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-451">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="8a1b2-452">**PerceptionSimulation. ISimulatedSixDofController**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="8a1b2-453">ユーザーに対してシミュレートされたコントローラーの位置をメートル単位で取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-453">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="8a1b2-454">**PerceptionSimulation. ISimulatedSixDofController**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="8a1b2-455">シミュレートされたコントローラーの向きを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-455">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="8a1b2-456">**PerceptionSimulation (ISimulatedSixDofController) (PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="8a1b2-457">シミュレートされたコントローラーの位置を、現在の位置 (メートル単位) に相対的に移動します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-457">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="8a1b2-458">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a1b2-458">Parameters</span></span>
* <span data-ttu-id="8a1b2-459">translation-シミュレートされたコントローラーを変換する量。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-459">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="8a1b2-460">**ISimulatedSixDofController (SimulatedSixDofControllerButton) () PerceptionSimulation**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="8a1b2-461">シミュレートされたコントローラーでボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-461">Press a button on the simulated controller.</span></span>  <span data-ttu-id="8a1b2-462">コントローラーが有効になっている場合にのみ、システムによって検出されます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-462">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="8a1b2-463">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a1b2-463">Parameters</span></span>
* <span data-ttu-id="8a1b2-464">button-押すボタン。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-464">button - The button to press.</span></span>

<span data-ttu-id="8a1b2-465">**PerceptionSimulation (ISimulatedSixDofController) (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="8a1b2-466">シミュレートされたコントローラーでボタンを離します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-466">Release a button on the simulated controller.</span></span>  <span data-ttu-id="8a1b2-467">コントローラーが有効になっている場合にのみ、システムによって検出されます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-467">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="8a1b2-468">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a1b2-468">Parameters</span></span>
* <span data-ttu-id="8a1b2-469">ボタン-リリースするボタン。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-469">button - The button to release.</span></span>

<span data-ttu-id="8a1b2-470">**PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="8a1b2-471">シミュレートされたコントローラーのタッチパッド上でシミュレートされた指の位置を取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-471">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="8a1b2-472">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a1b2-472">Parameters</span></span>
* <span data-ttu-id="8a1b2-473">x-指の水平方向の位置。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-473">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="8a1b2-474">y-指の垂直方向の位置。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-474">y - The vertical position of the finger.</span></span>

<span data-ttu-id="8a1b2-475">**PerceptionSimulation (float, float) の位置を ISimulatedSixDofController します。**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="8a1b2-476">シミュレートされたコントローラーのタッチパッドでシミュレートされた指の位置を設定します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-476">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="8a1b2-477">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a1b2-477">Parameters</span></span>
* <span data-ttu-id="8a1b2-478">x-指の水平方向の位置。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-478">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="8a1b2-479">y-指の垂直方向の位置。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-479">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="8a1b2-480">PerceptionSimulation. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="8a1b2-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="8a1b2-481">ISimulatedSixDofController を ISimulatedSixDofController2 にキャストすると、追加のプロパティとメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-481">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="8a1b2-482">**PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="8a1b2-483">シミュレートされたコントローラー上のシミュレートされたサムスティックの位置を取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-483">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="8a1b2-484">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a1b2-484">Parameters</span></span>
* <span data-ttu-id="8a1b2-485">x-サムスティックの水平方向の位置。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-485">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="8a1b2-486">y-サムスティックの垂直方向の位置。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-486">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="8a1b2-487">**PerceptionSimulation. ISimulatedSixDofController2. SetThumbstickPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="8a1b2-488">シミュレートされたコントローラーのシミュレートされたサムスティックの位置を設定します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-488">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="8a1b2-489">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a1b2-489">Parameters</span></span>
* <span data-ttu-id="8a1b2-490">x-サムスティックの水平方向の位置。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-490">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="8a1b2-491">y-サムスティックの垂直方向の位置。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-491">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="8a1b2-492">**PerceptionSimulation. ISimulatedSixDofController2. BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="8a1b2-493">シミュレートされたコントローラーのバッテリレベルを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-493">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="8a1b2-494">値は0.0 より大きく、100.0 以下でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-494">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="8a1b2-495">PerceptionSimulation. ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="8a1b2-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="8a1b2-496">シミュレートされた人間の目を表すインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-496">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="8a1b2-497">**PerceptionSimulation. ISimulatedEyes**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="8a1b2-498">シミュレートされた目の回転を取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-498">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="8a1b2-499">正のラジアンは、軸に沿って表示すると時計回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-499">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="8a1b2-500">**PerceptionSimulation (ISimulatedEyes) (PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="8a1b2-501">現在の回転と比較して、シミュレートされた目を回転します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-501">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="8a1b2-502">正のラジアンは、軸に沿って表示すると時計回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-502">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="8a1b2-503">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a1b2-503">Parameters</span></span>
* <span data-ttu-id="8a1b2-504">rotation-回転する量。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-504">rotation - The amount to rotate.</span></span>

<span data-ttu-id="8a1b2-505">**PerceptionSimulation. ISimulatedEyes. CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="8a1b2-506">シミュレートされた目の調整状態を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-506">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="8a1b2-507">**PerceptionSimulation. ISimulatedEyes. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="8a1b2-508">世界のリレーションを使用してノードの位置をメートル単位で取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-508">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="8a1b2-509">PerceptionSimulation. ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="8a1b2-509">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="8a1b2-510">再生用に読み込まれた単一の記録と対話するためのインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-510">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="8a1b2-511">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="8a1b2-512">記録内のデータ型の一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-512">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="8a1b2-513">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="8a1b2-514">記録の現在の状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-514">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="8a1b2-515">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="8a1b2-516">再生を開始します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-516">Start the playback.</span></span> <span data-ttu-id="8a1b2-517">記録が一時停止されている場合は、一時停止した場所から再生が再開されます。停止した場合は、最初から再生が開始されます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-517">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="8a1b2-518">既に再生中の場合、この呼び出しは無視されます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-518">If already playing, this call is ignored.</span></span>

<span data-ttu-id="8a1b2-519">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="8a1b2-520">現在の場所で再生を一時停止します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-520">Pauses the playback at its current location.</span></span> <span data-ttu-id="8a1b2-521">記録が停止している場合、呼び出しは無視されます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-521">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="8a1b2-522">**PerceptionSimulation. ISimulationRecording (System. UInt64)**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="8a1b2-523">指定した時間 (先頭から100ナノ秒単位) に記録をシークし、その位置で一時停止します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-523">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="8a1b2-524">時刻が記録の末尾を越えている場合は、最後のフレームで一時停止します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-524">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="8a1b2-525">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a1b2-525">Parameters</span></span>
* <span data-ttu-id="8a1b2-526">ティック-シークする時刻。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-526">ticks - The time to which to seek.</span></span>

<span data-ttu-id="8a1b2-527">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="8a1b2-528">再生を停止し、位置を先頭にリセットします。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-528">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="8a1b2-529">PerceptionSimulation. ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="8a1b2-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="8a1b2-530">再生中に状態の変更を受信するためのインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-530">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="8a1b2-531">**PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged (PerceptionSimulation. PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="8a1b2-532">ISimulationRecording の再生状態が変更されたときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-532">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="8a1b2-533">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a1b2-533">Parameters</span></span>
* <span data-ttu-id="8a1b2-534">newState-記録の新しい状態。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-534">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="8a1b2-535">PerceptionSimulation. PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="8a1b2-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="8a1b2-536">認識シミュレーションオブジェクトを作成するためのルートオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-536">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="8a1b2-537">**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager (PerceptionSimulation. ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="8a1b2-538">シミュレートされたパケットを生成し、指定したシンクに配信するために、オブジェクトでを作成します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-538">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="8a1b2-539">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a1b2-539">Parameters</span></span>
* <span data-ttu-id="8a1b2-540">sink-生成されたすべてのパケットを受信するシンク。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-540">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="8a1b2-541">戻り値</span><span class="sxs-lookup"><span data-stu-id="8a1b2-541">Return value</span></span>

<span data-ttu-id="8a1b2-542">作成されたマネージャー。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-542">The created Manager.</span></span>

<span data-ttu-id="8a1b2-543">**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording (System.string)**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="8a1b2-544">指定されたパスのファイルに受信したすべてのパケットを格納するシンクを作成します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-544">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="8a1b2-545">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a1b2-545">Parameters</span></span>
* <span data-ttu-id="8a1b2-546">path-作成するファイルのパス。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-546">path - The path of the file to create.</span></span>

<span data-ttu-id="8a1b2-547">戻り値</span><span class="sxs-lookup"><span data-stu-id="8a1b2-547">Return value</span></span>

<span data-ttu-id="8a1b2-548">作成されたシンク。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-548">The created sink.</span></span>

<span data-ttu-id="8a1b2-549">**PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System.string, PerceptionSimulation. ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="8a1b2-550">指定されたファイルから記録を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-550">Load a recording from the specified file.</span></span>

<span data-ttu-id="8a1b2-551">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a1b2-551">Parameters</span></span>
* <span data-ttu-id="8a1b2-552">path-読み込むファイルのパス。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-552">path - The path of the file to load.</span></span>
* <span data-ttu-id="8a1b2-553">factory-必要なときに ISimulationStreamSink を作成するために記録によって使用されるファクトリ。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-553">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="8a1b2-554">戻り値</span><span class="sxs-lookup"><span data-stu-id="8a1b2-554">Return value</span></span>

<span data-ttu-id="8a1b2-555">読み込まれた記録。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-555">The loaded recording.</span></span>

<span data-ttu-id="8a1b2-556">**PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System.string, PerceptionSimulation. ISimulationStreamSinkFactory,,PerceptionSimulation. ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="8a1b2-557">指定されたファイルから記録を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-557">Load a recording from the specified file.</span></span>

<span data-ttu-id="8a1b2-558">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a1b2-558">Parameters</span></span>
* <span data-ttu-id="8a1b2-559">path-読み込むファイルのパス。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-559">path - The path of the file to load.</span></span>
* <span data-ttu-id="8a1b2-560">factory-必要なときに ISimulationStreamSink を作成するために記録によって使用されるファクトリ。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-560">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="8a1b2-561">callback-更新を受け取るコールバックで、記録の状態を再適用します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-561">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="8a1b2-562">戻り値</span><span class="sxs-lookup"><span data-stu-id="8a1b2-562">Return value</span></span>

<span data-ttu-id="8a1b2-563">読み込まれた記録。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-563">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="8a1b2-564">PerceptionSimulation データ型</span><span class="sxs-lookup"><span data-stu-id="8a1b2-564">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="8a1b2-565">さまざまな種類のストリームデータについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-565">Describes the different types of stream data.</span></span>

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

<span data-ttu-id="8a1b2-566">**PerceptionSimulation のデータ型はありません。**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="8a1b2-567">ストリームデータ型がないことを示すために使用される sentinel 値。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-567">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="8a1b2-568">**PerceptionSimulation のデータ型**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="8a1b2-569">ヘッドの位置と向きに関するデータのストリーム。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-569">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="8a1b2-570">**PerceptionSimulation のデータ型**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="8a1b2-571">ハンドの位置とジェスチャに関するデータのストリーム。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-571">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="8a1b2-572">**PerceptionSimulation. SpatialMapping.**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="8a1b2-573">環境の空間マッピングに関するデータのストリーム。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-573">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="8a1b2-574">**PerceptionSimulation のデータ型**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="8a1b2-575">デバイスの調整に関するデータのストリーム。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-575">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="8a1b2-576">調整パケットは、リモートモードのシステムでのみ受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-576">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="8a1b2-577">**PerceptionSimulation のデータ型**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="8a1b2-578">デバイスの環境に関するデータのストリーム。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-578">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="8a1b2-579">**PerceptionSimulation のデータ型**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="8a1b2-580">すべての記録されたデータ型を示すために使用される sentinel 値。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-580">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="8a1b2-581">PerceptionSimulation. ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="8a1b2-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="8a1b2-582">シミュレーションストリームからデータパケットを受信するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-582">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="8a1b2-583">**PerceptionSimulation. ISimulationStreamSink (uint length, byte [] パケット数)**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="8a1b2-584">内部的に型指定され、バージョン管理される1つのパケットを受信します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-584">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="8a1b2-585">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a1b2-585">Parameters</span></span>
* <span data-ttu-id="8a1b2-586">length-パケットの長さ。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-586">length - The length of the packet.</span></span>
* <span data-ttu-id="8a1b2-587">パケット-パケットのデータ。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-587">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="8a1b2-588">PerceptionSimulation. ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="8a1b2-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="8a1b2-589">ISimulationStreamSink を作成するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-589">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="8a1b2-590">**PerceptionSimulation. ISimulationStreamSinkFactory-Ationstreamsink ()**</span><span class="sxs-lookup"><span data-stu-id="8a1b2-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="8a1b2-591">ISimulationStreamSink の1つのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-591">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="8a1b2-592">戻り値</span><span class="sxs-lookup"><span data-stu-id="8a1b2-592">Return value</span></span>

<span data-ttu-id="8a1b2-593">作成されたシンク。</span><span class="sxs-lookup"><span data-stu-id="8a1b2-593">The created sink.</span></span>
