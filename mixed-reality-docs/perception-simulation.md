---
title: Perception シミュレーション
description: Perception シミュレーション ライブラリを使用して、シミュレートされた没入型アプリケーションの入力を自動化するためのガイド
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: HoloLens、シミュレーションのテスト
ms.openlocfilehash: 8152181bdbe8c83d2b706b34f1f2fb5d51f4c880
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414531"
---
# <a name="perception-simulation"></a><span data-ttu-id="136bd-104">Perception シミュレーション</span><span class="sxs-lookup"><span data-stu-id="136bd-104">Perception simulation</span></span>

<span data-ttu-id="136bd-105">アプリの自動テストをビルドしますか。</span><span class="sxs-lookup"><span data-stu-id="136bd-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="136bd-106">コンポーネント レベルの単体テストを超えるし、実際に、アプリのエンドを実行するためのテストを作成しますか。</span><span class="sxs-lookup"><span data-stu-id="136bd-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="136bd-107">Perception シミュレーションは、探しているものです。</span><span class="sxs-lookup"><span data-stu-id="136bd-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="136bd-108">Perception シミュレーション ライブラリが人間に送信し、テストを自動化できるように、世界がアプリにデータを入力します。</span><span class="sxs-lookup"><span data-stu-id="136bd-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="136bd-109">たとえば、人間、反復可能な特定の位置を検索およびジェスチャを実行することまたはのモーション コント ローラーを使用して入力をシミュレートできます。</span><span class="sxs-lookup"><span data-stu-id="136bd-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="136bd-110">Perception シミュレーションは、物理 HoloLens、HoloLens のエミュレーターに次のように、シミュレートされた入力を送信できます (第 1 世代)、2 つのエミュレーター、または Mixed Reality ポータルを使用した PC HoloLens をインストールします。</span><span class="sxs-lookup"><span data-stu-id="136bd-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="136bd-111">Perception Mixed Reality デバイスでライブのセンサーをバイパスし、シミュレーションでは、デバイスで実行されているアプリケーションへの入力をシミュレートします。</span><span class="sxs-lookup"><span data-stu-id="136bd-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="136bd-112">アプリケーションでは、同じ api を使用して、Perception シミュレーションを実行するいると実際のセンサーを実行している間の違いを見分けることはできませんが、常にこれらの入力イベントを受信します。</span><span class="sxs-lookup"><span data-stu-id="136bd-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="136bd-113">Perception シミュレーションは、シミュレートされた入力、HoloLens 仮想マシンに送信するために使用、HoloLens のエミュレーターと同じテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="136bd-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="136bd-114">コードでシミュレーションを使用するには、まず IPerceptionSimulationManager オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="136bd-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="136bd-115">、そのオブジェクトから、シミュレートされた「人事」、ヘッドの位置、手の形の位置、ジェスチャなどのプロパティを制御するためのコマンドを実行できると有効にし、アニメーション コント ローラーを操作できます。</span><span class="sxs-lookup"><span data-stu-id="136bd-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="136bd-116">Perception でシミュレーションするための Visual Studio プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="136bd-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="136bd-117">[HoloLens のエミュレーターをインストール](install-the-tools.md)開発 PC 上。</span><span class="sxs-lookup"><span data-stu-id="136bd-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="136bd-118">エミュレーターには、Perception シミュレーションに使用するライブラリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="136bd-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="136bd-119">作成する新しい Visual StudioC#デスクトップのプロジェクト (コンソール プロジェクトをうまくを開始する)。</span><span class="sxs-lookup"><span data-stu-id="136bd-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="136bd-120">次のバイナリをプロジェクトに参照として追加 (プロジェクトに追加]-> [-> 参照)。%Programfiles (x86) %\Microsoft XDE で検索することができます\\(バージョン) など、 **%programfiles (x86) %\Microsoft XDE\\10.0.18362.0** HoloLens のエミュレーターの 2。</span><span class="sxs-lookup"><span data-stu-id="136bd-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="136bd-121">(注: バイナリには、HoloLens 2 エミュレーターの一部が、でも正しく動作 Windows Mixed Reality のデスクトップ)。します。</span><span class="sxs-lookup"><span data-stu-id="136bd-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="136bd-122">管理 - PerceptionSimulationManager.Interop.dll C# Perception シミュレーション用のラッパーです。</span><span class="sxs-lookup"><span data-stu-id="136bd-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="136bd-123">b.</span><span class="sxs-lookup"><span data-stu-id="136bd-123">b.</span></span> <span data-ttu-id="136bd-124">PerceptionSimulationRest.dll - HoloLens またはエミュレーターへの web ソケット通信チャネルを設定するためのライブラリを使用します。</span><span class="sxs-lookup"><span data-stu-id="136bd-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="136bd-125">c.</span><span class="sxs-lookup"><span data-stu-id="136bd-125">c.</span></span> <span data-ttu-id="136bd-126">SimulationStream.Interop.dll のシミュレーションを共有する型。</span><span class="sxs-lookup"><span data-stu-id="136bd-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="136bd-127">実装を追加するプロジェクト バイナリ PerceptionSimulationManager.dll。</span><span class="sxs-lookup"><span data-stu-id="136bd-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="136bd-128">まず、プロジェクトに、バイナリとして追加 (プロジェクトに追加-> -> 既存項目の)。プロジェクトのソース フォルダーにコピーしないように、リンクとして保存します。</span><span class="sxs-lookup"><span data-stu-id="136bd-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="136bd-129">![PerceptionSimulationManager.dll をリンクとしてプロジェクトに追加](images/saveaslink.png)b。</span><span class="sxs-lookup"><span data-stu-id="136bd-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="136bd-130">確認し、ビルドの出力フォルダーにコピーすることがあるのです。</span><span class="sxs-lookup"><span data-stu-id="136bd-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="136bd-131">これは、バイナリのプロパティ シートです。</span><span class="sxs-lookup"><span data-stu-id="136bd-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="136bd-132">![マーク PerceptionSimulationManager.dll 出力ディレクトリにコピーするには](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="136bd-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="136bd-133">アクティブ ソリューション プラットフォームを x64 に設定します。</span><span class="sxs-lookup"><span data-stu-id="136bd-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="136bd-134">(使用の場合は、1 つは、x64 プラットフォーム エントリを作成する Configuration Manager が存在しない)</span><span class="sxs-lookup"><span data-stu-id="136bd-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="136bd-135">IPerceptionSimulation マネージャー オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="136bd-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="136bd-136">シミュレーションを制御するには、IPerceptionSimulationManager オブジェクトから取得したオブジェクトの更新プログラムを発行します。</span><span class="sxs-lookup"><span data-stu-id="136bd-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="136bd-137">最初の手順では、そのオブジェクトを取得し、ターゲット デバイスまたはエミュレーターに接続します。</span><span class="sxs-lookup"><span data-stu-id="136bd-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="136bd-138">デバイスのポータル をクリックして、エミュレーターの IP アドレスを取得できます、[ツールバー](using-the-hololens-emulator.md)</span><span class="sxs-lookup"><span data-stu-id="136bd-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="136bd-139">![デバイスのポータルを開く アイコン](images/emulator-deviceportal.png)**デバイス ポータルを開く**:エミュレーターで HoloLens OS の Windows デバイス ポータルを開きます。</span><span class="sxs-lookup"><span data-stu-id="136bd-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="136bd-140">For Windows Mixed Reality、これで取得できる"For developers"し、[更新とセキュリティ]、で、設定アプリで、"を使用して接続します""を有効にするデバイス ポータルです。"[] セクション。</span><span class="sxs-lookup"><span data-stu-id="136bd-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="136bd-141">必ず、IP アドレスとポートの両方に注意してください。</span><span class="sxs-lookup"><span data-stu-id="136bd-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="136bd-142">まず、RestSimulationStreamSink.Create RestSimulationStreamSink オブジェクトを取得すると呼んでいます。</span><span class="sxs-lookup"><span data-stu-id="136bd-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="136bd-143">これは、対象のデバイスまたはエミュレーターを http 接続を介して制御されます。</span><span class="sxs-lookup"><span data-stu-id="136bd-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="136bd-144">コマンドに渡され、によって処理されますが、 [Windows Device Portal](using-the-windows-device-portal.md)デバイスまたはエミュレーターで実行されています。</span><span class="sxs-lookup"><span data-stu-id="136bd-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="136bd-145">オブジェクトを作成する必要があります、4 つのパラメーターは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="136bd-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="136bd-146">Uri の uri、ターゲット デバイスの IP アドレス (例:"http://123.123.123.123 「または」 http://123.123.123.123:50080")</span><span class="sxs-lookup"><span data-stu-id="136bd-146">Uri uri - IP address of the target device (e.g., "http://123.123.123.123" or "http://123.123.123.123:50080")</span></span>
* <span data-ttu-id="136bd-147">System.Net.NetworkCredential 資格情報 - に接続するためには、ユーザー名/パスワード、 [Windows Device Portal](using-the-windows-device-portal.md)ターゲット デバイスまたはエミュレーターにします。</span><span class="sxs-lookup"><span data-stu-id="136bd-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="136bd-148">そのローカル アドレスを使用してエミュレーターに接続するかどうか (例: 168。 *。* 。 \*) 同じ pc では、すべての資格情報が受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="136bd-148">If you are connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="136bd-149">bool の通常の通常の優先順位、優先度の低いは false の場合は True。</span><span class="sxs-lookup"><span data-stu-id="136bd-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="136bd-150">一般にこれを設定する*true*テストのシナリオは、制御するためのテストを使用します。</span><span class="sxs-lookup"><span data-stu-id="136bd-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="136bd-151">エミュレーターと Windows Mixed Reality シミュレーションは、優先度の低い接続を使用します。</span><span class="sxs-lookup"><span data-stu-id="136bd-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="136bd-152">場合は、テストは、優先度の低い接続を使用しても、最も最近確立された接続は、コントロール内になります。</span><span class="sxs-lookup"><span data-stu-id="136bd-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="136bd-153">System.Threading.CancellationToken トークン - 非同期操作をキャンセルするトークンです。</span><span class="sxs-lookup"><span data-stu-id="136bd-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="136bd-154">2 つ目は、IPerceptionSimulationManager を作成します。</span><span class="sxs-lookup"><span data-stu-id="136bd-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="136bd-155">これは、使用してシミュレーションを制御するオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="136bd-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="136bd-156">これをも実行することで、非同期メソッドに注意してください。</span><span class="sxs-lookup"><span data-stu-id="136bd-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="136bd-157">シミュレートされたユーザーを制御します。</span><span class="sxs-lookup"><span data-stu-id="136bd-157">Control the simulated Human</span></span>

<span data-ttu-id="136bd-158">IPerceptionSimulationManager には、ISimulatedHuman オブジェクトを返す人間プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="136bd-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="136bd-159">シミュレートされたユーザーを制御するには、このオブジェクトに対して操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="136bd-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="136bd-160">例:</span><span class="sxs-lookup"><span data-stu-id="136bd-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="136bd-161">基本的なサンプルC#コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="136bd-161">Basic Sample C# console application</span></span>

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
                        new Uri("http://169.254.227.115"),
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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="136bd-162">サンプルを拡張C#コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="136bd-162">Extended Sample C# console application</span></span>

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
                        new Uri("http://169.254.227.115"),
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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="136bd-163">6-自由度のコント ローラー上に注意してください。</span><span class="sxs-lookup"><span data-stu-id="136bd-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="136bd-164">シミュレートされた 6-自由度のコント ローラーのメソッドで、任意のプロパティを呼び出す前に、コント ローラーをアクティブ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="136bd-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="136bd-165">そうしないと、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="136bd-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="136bd-166">可能性があります 2019 の更新を Windows 10 以降では、シミュレートされた 6-自由度のコント ローラーをインストールおよび SimulatedSixDofControllerStatus.Active ISimulatedSixDofController オブジェクトの Status プロパティを設定してアクティブ化されることができます。</span><span class="sxs-lookup"><span data-stu-id="136bd-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="136bd-167">Windows 10 年 2018年 10 月の更新前に、インストールしてする必要がありますとは別に、シミュレートされた 6-自由度のコント ローラー最初 \Windows\System32 フォルダーにある PerceptionSimulationDevice ツールを呼び出すことによって。</span><span class="sxs-lookup"><span data-stu-id="136bd-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="136bd-168">このツールの使用状況は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="136bd-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="136bd-169">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="136bd-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="136bd-170">サポートされているアクションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="136bd-170">Supported actions are:</span></span>
* <span data-ttu-id="136bd-171">インストールを =</span><span class="sxs-lookup"><span data-stu-id="136bd-171">i = install</span></span>
* <span data-ttu-id="136bd-172">q = クエリ</span><span class="sxs-lookup"><span data-stu-id="136bd-172">q = query</span></span>
* <span data-ttu-id="136bd-173">r = 削除</span><span class="sxs-lookup"><span data-stu-id="136bd-173">r = remove</span></span>

<span data-ttu-id="136bd-174">サポートされているインスタンスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="136bd-174">Supported instances are:</span></span>
* <span data-ttu-id="136bd-175">1 = の左側の 6-自由度のコント ローラー</span><span class="sxs-lookup"><span data-stu-id="136bd-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="136bd-176">2 = 右 6-自由度のコント ローラー</span><span class="sxs-lookup"><span data-stu-id="136bd-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="136bd-177">(0 は、値を返す) の成功または失敗 (0 以外の戻り値)、プロセスの終了コードを示します。</span><span class="sxs-lookup"><span data-stu-id="136bd-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="136bd-178">'Q' のアクションを使用して、コント ローラーがインストールされているかどうかを照会する、戻り値は必要コント ローラーがインストールされている場合はゼロ (0)、コント ローラーが既にインストールされていない場合、または 1 (1) とになります。</span><span class="sxs-lookup"><span data-stu-id="136bd-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="136bd-179">Windows 上のコント ローラーを削除するときに、10 年 2018年 10 月の更新または以前では、オフ、API を使用して最初に、呼び出して PerceptionSimulationDevice ツールには、その状態を設定します。</span><span class="sxs-lookup"><span data-stu-id="136bd-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="136bd-180">このツールは、管理者として実行する必要がありますに注意してください。</span><span class="sxs-lookup"><span data-stu-id="136bd-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="136bd-181">API リファレンス</span><span class="sxs-lookup"><span data-stu-id="136bd-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="136bd-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="136bd-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="136bd-183">シミュレートされたデバイスの種類について説明します</span><span class="sxs-lookup"><span data-stu-id="136bd-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="136bd-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span><span class="sxs-lookup"><span data-stu-id="136bd-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="136bd-185">架空の参照のデバイスでは、PerceptionSimulationManager の既定値</span><span class="sxs-lookup"><span data-stu-id="136bd-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="136bd-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="136bd-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="136bd-187">ヘッド トラッカー モードについて説明します</span><span class="sxs-lookup"><span data-stu-id="136bd-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="136bd-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span><span class="sxs-lookup"><span data-stu-id="136bd-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="136bd-189">既定の Head が追跡します。</span><span class="sxs-lookup"><span data-stu-id="136bd-189">Default Head Tracking.</span></span> <span data-ttu-id="136bd-190">つまり、システムは、追跡モードの実行時の条件に基づいて最適なヘッドを選択ことがあります。</span><span class="sxs-lookup"><span data-stu-id="136bd-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="136bd-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span><span class="sxs-lookup"><span data-stu-id="136bd-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="136bd-192">印刷の向きのみヘッドが追跡します。</span><span class="sxs-lookup"><span data-stu-id="136bd-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="136bd-193">つまり、追跡対象の位置は、信頼性が高く、できない場合があります、ヘッドの位置に依存する一部の機能を利用できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="136bd-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="136bd-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span><span class="sxs-lookup"><span data-stu-id="136bd-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="136bd-195">ヘッドの位置指定の追跡。</span><span class="sxs-lookup"><span data-stu-id="136bd-195">Positional Head Tracking.</span></span> <span data-ttu-id="136bd-196">つまり、追跡されているヘッドの位置と向きの両方がある信頼性の高い</span><span class="sxs-lookup"><span data-stu-id="136bd-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="136bd-197">Microsoft.PerceptionSimulation.SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="136bd-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="136bd-198">シミュレートされたジェスチャを説明します。</span><span class="sxs-lookup"><span data-stu-id="136bd-198">Describes a simulated gesture</span></span>

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

<span data-ttu-id="136bd-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span><span class="sxs-lookup"><span data-stu-id="136bd-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="136bd-200">ジェスチャがない場合に使用される sentinel 値。</span><span class="sxs-lookup"><span data-stu-id="136bd-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="136bd-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="136bd-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="136bd-202">指では、ジェスチャが押されました。</span><span class="sxs-lookup"><span data-stu-id="136bd-202">A finger pressed gesture.</span></span>

<span data-ttu-id="136bd-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="136bd-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="136bd-204">指では、ジェスチャがリリースされました。</span><span class="sxs-lookup"><span data-stu-id="136bd-204">A finger released gesture.</span></span>

<span data-ttu-id="136bd-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span><span class="sxs-lookup"><span data-stu-id="136bd-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="136bd-206">ホーム/システム ジェスチャ。</span><span class="sxs-lookup"><span data-stu-id="136bd-206">The home/system gesture.</span></span>

<span data-ttu-id="136bd-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span><span class="sxs-lookup"><span data-stu-id="136bd-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="136bd-208">最大の有効なジェスチャ。</span><span class="sxs-lookup"><span data-stu-id="136bd-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="136bd-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="136bd-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="136bd-210">シミュレートされた 6-自由度のコント ローラーの状態。</span><span class="sxs-lookup"><span data-stu-id="136bd-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="136bd-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span><span class="sxs-lookup"><span data-stu-id="136bd-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="136bd-212">6-自由度のコント ローラーがオフになります。</span><span class="sxs-lookup"><span data-stu-id="136bd-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="136bd-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span><span class="sxs-lookup"><span data-stu-id="136bd-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="136bd-214">6-自由度のコント ローラーが有効になり、追跡。</span><span class="sxs-lookup"><span data-stu-id="136bd-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="136bd-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="136bd-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="136bd-216">6-自由度のコント ローラーは、有効になってが追跡することはできません。</span><span class="sxs-lookup"><span data-stu-id="136bd-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="136bd-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="136bd-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="136bd-218">シミュレートされた 6-自由度のコント ローラーでサポートされているボタン。</span><span class="sxs-lookup"><span data-stu-id="136bd-218">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="136bd-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span><span class="sxs-lookup"><span data-stu-id="136bd-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="136bd-220">ボタンがない場合に使用される sentinel 値。</span><span class="sxs-lookup"><span data-stu-id="136bd-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="136bd-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span><span class="sxs-lookup"><span data-stu-id="136bd-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="136bd-222">[ホーム] ボタンが押されました。</span><span class="sxs-lookup"><span data-stu-id="136bd-222">The Home button is pressed.</span></span>

<span data-ttu-id="136bd-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span><span class="sxs-lookup"><span data-stu-id="136bd-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="136bd-224">メニュー ボタンが押されました。</span><span class="sxs-lookup"><span data-stu-id="136bd-224">The Menu button is pressed.</span></span>

<span data-ttu-id="136bd-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span><span class="sxs-lookup"><span data-stu-id="136bd-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="136bd-226">グリップのボタンが押されました。</span><span class="sxs-lookup"><span data-stu-id="136bd-226">The Grip button is pressed.</span></span>

<span data-ttu-id="136bd-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="136bd-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="136bd-228">タッチパッドが押されました。</span><span class="sxs-lookup"><span data-stu-id="136bd-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="136bd-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span><span class="sxs-lookup"><span data-stu-id="136bd-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="136bd-230">[選択] ボタンが押されました。</span><span class="sxs-lookup"><span data-stu-id="136bd-230">The Select button is pressed.</span></span>

<span data-ttu-id="136bd-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="136bd-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="136bd-232">タッチパッドをタッチするとします。</span><span class="sxs-lookup"><span data-stu-id="136bd-232">The TouchPad is touched.</span></span>

<span data-ttu-id="136bd-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span><span class="sxs-lookup"><span data-stu-id="136bd-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="136bd-234">スティックが押されました。</span><span class="sxs-lookup"><span data-stu-id="136bd-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="136bd-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span><span class="sxs-lookup"><span data-stu-id="136bd-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="136bd-236">有効なボタンの最大値。</span><span class="sxs-lookup"><span data-stu-id="136bd-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="136bd-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="136bd-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="136bd-238">シミュレートされた目の調整状態</span><span class="sxs-lookup"><span data-stu-id="136bd-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="136bd-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span><span class="sxs-lookup"><span data-stu-id="136bd-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="136bd-240">目の調整は、ご利用いただけません。</span><span class="sxs-lookup"><span data-stu-id="136bd-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="136bd-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span><span class="sxs-lookup"><span data-stu-id="136bd-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="136bd-242">目が調整されています。</span><span class="sxs-lookup"><span data-stu-id="136bd-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="136bd-243">これが既定値です。</span><span class="sxs-lookup"><span data-stu-id="136bd-243">This is the default value.</span></span>

<span data-ttu-id="136bd-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span><span class="sxs-lookup"><span data-stu-id="136bd-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="136bd-245">目が調整されています。</span><span class="sxs-lookup"><span data-stu-id="136bd-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="136bd-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="136bd-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="136bd-247">目では、調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="136bd-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="136bd-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="136bd-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="136bd-249">針のジョイントの追跡の精度。</span><span class="sxs-lookup"><span data-stu-id="136bd-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="136bd-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span><span class="sxs-lookup"><span data-stu-id="136bd-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="136bd-251">ジョイントは追跡されません。</span><span class="sxs-lookup"><span data-stu-id="136bd-251">The joint is not tracked.</span></span>

<span data-ttu-id="136bd-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span><span class="sxs-lookup"><span data-stu-id="136bd-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="136bd-253">共同の位置が推論されます。</span><span class="sxs-lookup"><span data-stu-id="136bd-253">The joint position is inferred.</span></span>

<span data-ttu-id="136bd-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span><span class="sxs-lookup"><span data-stu-id="136bd-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="136bd-255">ジョイントがすべて記録します。</span><span class="sxs-lookup"><span data-stu-id="136bd-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="136bd-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="136bd-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="136bd-257">針のジョイントの追跡の精度。</span><span class="sxs-lookup"><span data-stu-id="136bd-257">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="136bd-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span><span class="sxs-lookup"><span data-stu-id="136bd-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="136bd-259">手の本の指の結合は、閉じた姿勢を反映するように構成されます。</span><span class="sxs-lookup"><span data-stu-id="136bd-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="136bd-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span><span class="sxs-lookup"><span data-stu-id="136bd-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="136bd-261">手の本の指の結合は、オープンの姿勢を反映するように構成されます。</span><span class="sxs-lookup"><span data-stu-id="136bd-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="136bd-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span><span class="sxs-lookup"><span data-stu-id="136bd-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="136bd-263">手の本の指ジョイントがポインティング姿勢を反映するように構成されます。</span><span class="sxs-lookup"><span data-stu-id="136bd-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="136bd-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span><span class="sxs-lookup"><span data-stu-id="136bd-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="136bd-265">手の本の指の結合は、ピンチ姿勢を反映するように構成されます。</span><span class="sxs-lookup"><span data-stu-id="136bd-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="136bd-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span><span class="sxs-lookup"><span data-stu-id="136bd-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="136bd-267">SimulatedHandPose の最大の有効な値。</span><span class="sxs-lookup"><span data-stu-id="136bd-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="136bd-268">Microsoft.PerceptionSimulation.PlaybackState</span><span class="sxs-lookup"><span data-stu-id="136bd-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="136bd-269">再生の状態について説明します。</span><span class="sxs-lookup"><span data-stu-id="136bd-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="136bd-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span><span class="sxs-lookup"><span data-stu-id="136bd-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="136bd-271">記録は、現在停止と再生の準備完了です。</span><span class="sxs-lookup"><span data-stu-id="136bd-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="136bd-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span><span class="sxs-lookup"><span data-stu-id="136bd-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="136bd-273">記録を再生中。</span><span class="sxs-lookup"><span data-stu-id="136bd-273">The recording is currently playing.</span></span>

<span data-ttu-id="136bd-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span><span class="sxs-lookup"><span data-stu-id="136bd-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="136bd-275">記録を一時停止されています。</span><span class="sxs-lookup"><span data-stu-id="136bd-275">The recording is currently paused.</span></span>

<span data-ttu-id="136bd-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span><span class="sxs-lookup"><span data-stu-id="136bd-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="136bd-277">記録は、末尾に達した。</span><span class="sxs-lookup"><span data-stu-id="136bd-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="136bd-278">Microsoft.PerceptionSimulation.Vector3</span><span class="sxs-lookup"><span data-stu-id="136bd-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="136bd-279">点または 3D 空間でベクターを表す場合があります、3 つのコンポーネントのベクターをについて説明します。</span><span class="sxs-lookup"><span data-stu-id="136bd-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="136bd-280">**Microsoft.PerceptionSimulation.Vector3.X**</span><span class="sxs-lookup"><span data-stu-id="136bd-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="136bd-281">ベクトルの X 成分。</span><span class="sxs-lookup"><span data-stu-id="136bd-281">The X component of the vector.</span></span>

<span data-ttu-id="136bd-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span><span class="sxs-lookup"><span data-stu-id="136bd-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="136bd-283">ベクトルの Y 成分。</span><span class="sxs-lookup"><span data-stu-id="136bd-283">The Y component of the vector.</span></span>

<span data-ttu-id="136bd-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span><span class="sxs-lookup"><span data-stu-id="136bd-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="136bd-285">ベクトルの Z 成分。</span><span class="sxs-lookup"><span data-stu-id="136bd-285">The Z component of the vector.</span></span>

<span data-ttu-id="136bd-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="136bd-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="136bd-287">新しい Vector3 を構築します。</span><span class="sxs-lookup"><span data-stu-id="136bd-287">Construct a new Vector3.</span></span>

<span data-ttu-id="136bd-288">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136bd-288">Parameters</span></span>
* <span data-ttu-id="136bd-289">x - ベクターの x 成分。</span><span class="sxs-lookup"><span data-stu-id="136bd-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="136bd-290">y のベクターの y 成分。</span><span class="sxs-lookup"><span data-stu-id="136bd-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="136bd-291">z のベクトルの z 成分。</span><span class="sxs-lookup"><span data-stu-id="136bd-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="136bd-292">Microsoft.PerceptionSimulation.Rotation3</span><span class="sxs-lookup"><span data-stu-id="136bd-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="136bd-293">3 つのコンポーネントの回転について説明します。</span><span class="sxs-lookup"><span data-stu-id="136bd-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="136bd-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span><span class="sxs-lookup"><span data-stu-id="136bd-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="136bd-295">回転のピッチ コンポーネントは、X 軸を中心にダウンします。</span><span class="sxs-lookup"><span data-stu-id="136bd-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="136bd-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span><span class="sxs-lookup"><span data-stu-id="136bd-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="136bd-297">Y 軸の周囲の回転のヨー コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="136bd-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="136bd-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span><span class="sxs-lookup"><span data-stu-id="136bd-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="136bd-299">Z 軸の周囲の回転のロールのコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="136bd-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="136bd-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="136bd-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="136bd-301">新しい Rotation3 を構築します。</span><span class="sxs-lookup"><span data-stu-id="136bd-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="136bd-302">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136bd-302">Parameters</span></span>
* <span data-ttu-id="136bd-303">ピッチの回転の声の高さコンポーネント。</span><span class="sxs-lookup"><span data-stu-id="136bd-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="136bd-304">ヨー、回転のヨー コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="136bd-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="136bd-305">ロールの回転のロールのコンポーネント。</span><span class="sxs-lookup"><span data-stu-id="136bd-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="136bd-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="136bd-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="136bd-307">シミュレートされた手の形で、共同の構成について説明します。</span><span class="sxs-lookup"><span data-stu-id="136bd-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="136bd-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span><span class="sxs-lookup"><span data-stu-id="136bd-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="136bd-309">ジョイントの位置。</span><span class="sxs-lookup"><span data-stu-id="136bd-309">The position of the joint.</span></span>

<span data-ttu-id="136bd-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span><span class="sxs-lookup"><span data-stu-id="136bd-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="136bd-311">ジョイントの回転。</span><span class="sxs-lookup"><span data-stu-id="136bd-311">The rotation of the joint.</span></span>

<span data-ttu-id="136bd-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="136bd-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="136bd-313">ジョイントの追跡の精度。</span><span class="sxs-lookup"><span data-stu-id="136bd-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="136bd-314">Microsoft.PerceptionSimulation.Frustum</span><span class="sxs-lookup"><span data-stu-id="136bd-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="136bd-315">カメラで通常使用される視錐台をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="136bd-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="136bd-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span><span class="sxs-lookup"><span data-stu-id="136bd-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="136bd-317">視錐台に含まれている最小の距離です。</span><span class="sxs-lookup"><span data-stu-id="136bd-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="136bd-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span><span class="sxs-lookup"><span data-stu-id="136bd-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="136bd-319">最大距離の視錐台に含まれています。</span><span class="sxs-lookup"><span data-stu-id="136bd-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="136bd-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="136bd-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="136bd-321">ラジアン (PI よりも小さい) 視錐台の横のフィールドの表示。</span><span class="sxs-lookup"><span data-stu-id="136bd-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="136bd-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="136bd-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="136bd-323">垂直ビューのフィールドへの水平視野の比率です。</span><span class="sxs-lookup"><span data-stu-id="136bd-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="136bd-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="136bd-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="136bd-325">デバイスの制御に使用されるパケットを生成するためのルートです。</span><span class="sxs-lookup"><span data-stu-id="136bd-325">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="136bd-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span><span class="sxs-lookup"><span data-stu-id="136bd-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="136bd-327">シミュレートされた人と、シミュレートされた世界を解釈するシミュレートされたデバイス オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-327">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="136bd-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span><span class="sxs-lookup"><span data-stu-id="136bd-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="136bd-329">シミュレートされたユーザーを制御するオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-329">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="136bd-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span><span class="sxs-lookup"><span data-stu-id="136bd-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="136bd-331">シミュレーションを既定の状態にリセットします。</span><span class="sxs-lookup"><span data-stu-id="136bd-331">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="136bd-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="136bd-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="136bd-333">シミュレートされた世界でシミュレートされた人間を解釈し、デバイスを記述するインターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="136bd-333">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="136bd-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="136bd-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="136bd-335">シミュレートされたデバイスから、ヘッドの追跡ツールを取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-335">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="136bd-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span><span class="sxs-lookup"><span data-stu-id="136bd-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="136bd-337">シミュレートされたデバイスからの手の形の追跡ツールを取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-337">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="136bd-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="136bd-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="136bd-339">指定されたデバイスの種類に一致するように、シミュレートされたデバイスのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="136bd-339">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="136bd-340">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136bd-340">Parameters</span></span>
* <span data-ttu-id="136bd-341">シミュレートされたデバイスの新しい種類を入力します。</span><span class="sxs-lookup"><span data-stu-id="136bd-341">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="136bd-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="136bd-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="136bd-343">シミュレートされた人間の頭を追跡するシミュレートされたデバイスの部分を記述するインターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="136bd-343">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="136bd-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="136bd-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="136bd-345">取得し、現在のトラッカーのヘッド モードを設定します。</span><span class="sxs-lookup"><span data-stu-id="136bd-345">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="136bd-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="136bd-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="136bd-347">シミュレートされた人間の手を追跡するシミュレートされたデバイスの部分を記述するインターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="136bd-347">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="136bd-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="136bd-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="136bd-349">メートル単位で、世界中とに関してノードの位置を取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-349">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="136bd-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span><span class="sxs-lookup"><span data-stu-id="136bd-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="136bd-351">取得し、ヘッドの中央を基準、シミュレートされた手トラッカーの位置を設定します。</span><span class="sxs-lookup"><span data-stu-id="136bd-351">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="136bd-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span><span class="sxs-lookup"><span data-stu-id="136bd-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="136bd-353">取得し、シミュレートされた手トラッカーの下向きのピッチを設定します。</span><span class="sxs-lookup"><span data-stu-id="136bd-353">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="136bd-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="136bd-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="136bd-355">取得し、シミュレートされた手トラッカーの視錐台を無視するかどうかを設定します。</span><span class="sxs-lookup"><span data-stu-id="136bd-355">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="136bd-356">無視される場合、両方の手は常に表示します。</span><span class="sxs-lookup"><span data-stu-id="136bd-356">When ignored, both hands are always visible.</span></span> <span data-ttu-id="136bd-357">(既定値) を無視しない場合に手は手トラッカーの視錐台内にあるときに、表示のみです。</span><span class="sxs-lookup"><span data-stu-id="136bd-357">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="136bd-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span><span class="sxs-lookup"><span data-stu-id="136bd-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="136bd-359">取得し、手がシミュレートされた手の追跡ツールに表示されるかどうかを判断するための視錐台プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="136bd-359">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="136bd-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="136bd-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="136bd-361">シミュレートされたユーザーを制御するための最上位レベル インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="136bd-361">Top level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="136bd-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="136bd-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="136bd-363">取得し、メートル単位で、世界中とに関してノードの位置を設定します。</span><span class="sxs-lookup"><span data-stu-id="136bd-363">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="136bd-364">位置は、人間のフィートの中央にある点に対応します。</span><span class="sxs-lookup"><span data-stu-id="136bd-364">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="136bd-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span><span class="sxs-lookup"><span data-stu-id="136bd-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="136bd-366">取得し、世界中でシミュレートされた人の顔の方向を設定します。</span><span class="sxs-lookup"><span data-stu-id="136bd-366">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="136bd-367">負の Z 軸を 0 ラジアンに直面します。</span><span class="sxs-lookup"><span data-stu-id="136bd-367">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="136bd-368">Y 軸の正のラジアンは右回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="136bd-368">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="136bd-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span><span class="sxs-lookup"><span data-stu-id="136bd-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="136bd-370">取得し、メートル単位でシミュレーションの人間の高さを設定します。</span><span class="sxs-lookup"><span data-stu-id="136bd-370">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="136bd-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span><span class="sxs-lookup"><span data-stu-id="136bd-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="136bd-372">シミュレートされた人間の左側を取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-372">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="136bd-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span><span class="sxs-lookup"><span data-stu-id="136bd-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="136bd-374">シミュレートされた人間の右側を取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-374">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="136bd-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span><span class="sxs-lookup"><span data-stu-id="136bd-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="136bd-376">シミュレートされた人間の先頭を取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-376">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="136bd-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="136bd-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="136bd-378">メートル単位で、現在位置を基準として、シミュレートされた人間に移動します。</span><span class="sxs-lookup"><span data-stu-id="136bd-378">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="136bd-379">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136bd-379">Parameters</span></span>
* <span data-ttu-id="136bd-380">翻訳に移動して、現在の位置を基準に変換します。</span><span class="sxs-lookup"><span data-stu-id="136bd-380">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="136bd-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span><span class="sxs-lookup"><span data-stu-id="136bd-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="136bd-382">Y 軸を中心に時計回りに現在方向の基準とした、シミュレートされた人間を回転します。</span><span class="sxs-lookup"><span data-stu-id="136bd-382">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="136bd-383">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136bd-383">Parameters</span></span>
* <span data-ttu-id="136bd-384">ラジアンの Y 軸に沿って回転する量。</span><span class="sxs-lookup"><span data-stu-id="136bd-384">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="136bd-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="136bd-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="136bd-386">ISimulatedHuman2 に ISimulatedHuman をキャストすることによって、追加のプロパティは使用可能です</span><span class="sxs-lookup"><span data-stu-id="136bd-386">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="136bd-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span><span class="sxs-lookup"><span data-stu-id="136bd-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="136bd-388">左側の 6-自由度のコント ローラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-388">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="136bd-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span><span class="sxs-lookup"><span data-stu-id="136bd-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="136bd-390">右側の 6-自由度のコント ローラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-390">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="136bd-391">Microsoft.PerceptionSimulation.ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="136bd-391">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="136bd-392">シミュレートされた人間の手の形を記述するインターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="136bd-392">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="136bd-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="136bd-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="136bd-394">メートル単位で、世界中とに関してノードの位置を取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-394">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="136bd-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span><span class="sxs-lookup"><span data-stu-id="136bd-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="136bd-396">取得し、メートル単位で、人間の基準とした、シミュレートされた手の形の位置を設定します。</span><span class="sxs-lookup"><span data-stu-id="136bd-396">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="136bd-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span><span class="sxs-lookup"><span data-stu-id="136bd-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="136bd-398">取得し、手の形が現在アクティブかどうかを設定します。</span><span class="sxs-lookup"><span data-stu-id="136bd-398">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="136bd-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span><span class="sxs-lookup"><span data-stu-id="136bd-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="136bd-400">手のアイコンが (つまり、かどうかは、HandTracker によって検出された位置に) SimulatedDevice に現在表示されているかどうかを取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-400">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="136bd-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="136bd-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="136bd-402">SimulatedDevice に表示されるようにして手のアイコンに移動します。</span><span class="sxs-lookup"><span data-stu-id="136bd-402">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="136bd-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="136bd-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="136bd-404">メートル単位で、現在位置を基準として、シミュレートされた手の形の位置を移動します。</span><span class="sxs-lookup"><span data-stu-id="136bd-404">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="136bd-405">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136bd-405">Parameters</span></span>
* <span data-ttu-id="136bd-406">翻訳 - シミュレートされた手の形を平行移動量。</span><span class="sxs-lookup"><span data-stu-id="136bd-406">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="136bd-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="136bd-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="136bd-408">シミュレートされたして手のアイコンを使用するジェスチャを実行します。</span><span class="sxs-lookup"><span data-stu-id="136bd-408">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="136bd-409">のみ検出されます、システムによって、手が有効になっている場合。</span><span class="sxs-lookup"><span data-stu-id="136bd-409">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="136bd-410">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136bd-410">Parameters</span></span>
* <span data-ttu-id="136bd-411">ジェスチャのジェスチャを実行します。</span><span class="sxs-lookup"><span data-stu-id="136bd-411">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="136bd-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="136bd-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="136bd-413">追加のプロパティは、ISimulatedHand ISimulatedHand2 にキャストすることによって利用可能です。</span><span class="sxs-lookup"><span data-stu-id="136bd-413">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="136bd-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span><span class="sxs-lookup"><span data-stu-id="136bd-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="136bd-415">取得またはシミュレートされた針の回転を設定します。</span><span class="sxs-lookup"><span data-stu-id="136bd-415">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="136bd-416">軸に検索するときに、正のラジアンは右回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="136bd-416">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="136bd-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="136bd-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="136bd-418">ISimulatedHand ISimulatedHand3 にキャストすることによって、追加のプロパティは使用可能です</span><span class="sxs-lookup"><span data-stu-id="136bd-418">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="136bd-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="136bd-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="136bd-420">指定された共同の共同構成を取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-420">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="136bd-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="136bd-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="136bd-422">共同の指定された複合的な構成を設定します。</span><span class="sxs-lookup"><span data-stu-id="136bd-422">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="136bd-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="136bd-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="136bd-424">既知の姿勢をアニメーション化するオプションのフラグを使用して手のアイコンに設定します。</span><span class="sxs-lookup"><span data-stu-id="136bd-424">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="136bd-425">注: をアニメーション化力感の最終的な複合的な構成をすぐに反映されません。</span><span class="sxs-lookup"><span data-stu-id="136bd-425">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="136bd-426">Microsoft.PerceptionSimulation.ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="136bd-426">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="136bd-427">シミュレートされた人間の頭を記述するインターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="136bd-427">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="136bd-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="136bd-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="136bd-429">メートル単位で、世界中とに関してノードの位置を取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-429">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="136bd-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span><span class="sxs-lookup"><span data-stu-id="136bd-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="136bd-431">シミュレートされた先頭の回転角度を取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-431">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="136bd-432">軸に検索するときに、正のラジアンは右回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="136bd-432">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="136bd-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span><span class="sxs-lookup"><span data-stu-id="136bd-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="136bd-434">シミュレートされた先頭の直径を取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-434">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="136bd-435">この値は、ヘッドのセンター (回転のポイント) を確認するに使用されます。</span><span class="sxs-lookup"><span data-stu-id="136bd-435">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="136bd-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="136bd-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="136bd-437">現在、回転の基準としたシミュレートされたヘッドを回転します。</span><span class="sxs-lookup"><span data-stu-id="136bd-437">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="136bd-438">軸に検索するときに、正のラジアンは右回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="136bd-438">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="136bd-439">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136bd-439">Parameters</span></span>
* <span data-ttu-id="136bd-440">回転の回転する量。</span><span class="sxs-lookup"><span data-stu-id="136bd-440">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="136bd-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="136bd-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="136bd-442">ISimulatedHead ISimulatedHead2 にキャストすることによって、追加のプロパティは使用可能です</span><span class="sxs-lookup"><span data-stu-id="136bd-442">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="136bd-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span><span class="sxs-lookup"><span data-stu-id="136bd-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="136bd-444">シミュレートされた人間の目を取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-444">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="136bd-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="136bd-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="136bd-446">シミュレートされたユーザーに関連付けられている 6 自由度のコント ローラーを記述するインターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="136bd-446">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="136bd-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="136bd-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="136bd-448">メートル単位で、世界中とに関してノードの位置を取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-448">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="136bd-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span><span class="sxs-lookup"><span data-stu-id="136bd-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="136bd-450">取得またはコント ローラーの現在の状態を設定します。</span><span class="sxs-lookup"><span data-stu-id="136bd-450">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="136bd-451">コント ローラーの状態は、オフ呼び出しの前に、移動、回転、またはキーを押してボタンは成功以外の値に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="136bd-451">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="136bd-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span><span class="sxs-lookup"><span data-stu-id="136bd-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="136bd-453">取得またはメートル単位で、人間の基準とした、シミュレートされたコント ローラーの位置を設定します。</span><span class="sxs-lookup"><span data-stu-id="136bd-453">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="136bd-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span><span class="sxs-lookup"><span data-stu-id="136bd-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="136bd-455">取得またはシミュレートされたコント ローラーの向きを設定します。</span><span class="sxs-lookup"><span data-stu-id="136bd-455">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="136bd-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="136bd-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="136bd-457">メートル単位で、現在位置を基準として、シミュレートされたコント ローラーの位置を移動します。</span><span class="sxs-lookup"><span data-stu-id="136bd-457">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="136bd-458">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136bd-458">Parameters</span></span>
* <span data-ttu-id="136bd-459">翻訳 - シミュレートされたコント ローラーの平行移動量。</span><span class="sxs-lookup"><span data-stu-id="136bd-459">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="136bd-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="136bd-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="136bd-461">シミュレートされたコント ローラー上のボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="136bd-461">Press a button on the simulated controller.</span></span>  <span data-ttu-id="136bd-462">のみ検出されます、システムによって、コント ローラーが有効になっている場合。</span><span class="sxs-lookup"><span data-stu-id="136bd-462">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="136bd-463">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136bd-463">Parameters</span></span>
* <span data-ttu-id="136bd-464">ボタン - キーを押すボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="136bd-464">button - The button to press.</span></span>

<span data-ttu-id="136bd-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="136bd-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="136bd-466">シミュレートされたコント ローラー上のボタンを離します。</span><span class="sxs-lookup"><span data-stu-id="136bd-466">Release a button on the simulated controller.</span></span>  <span data-ttu-id="136bd-467">のみ検出されます、システムによって、コント ローラーが有効になっている場合。</span><span class="sxs-lookup"><span data-stu-id="136bd-467">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="136bd-468">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136bd-468">Parameters</span></span>
* <span data-ttu-id="136bd-469">ボタン - を解放するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="136bd-469">button - The button to release.</span></span>

<span data-ttu-id="136bd-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition (out float、float を)**</span><span class="sxs-lookup"><span data-stu-id="136bd-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="136bd-471">シミュレートされた、シミュレートされたコント ローラーのタッチパッド本の指の位置を取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-471">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="136bd-472">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136bd-472">Parameters</span></span>
* <span data-ttu-id="136bd-473">x 軸の指の水平位置。</span><span class="sxs-lookup"><span data-stu-id="136bd-473">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="136bd-474">y の指の垂直位置。</span><span class="sxs-lookup"><span data-stu-id="136bd-474">y - The vertical position of the finger.</span></span>

<span data-ttu-id="136bd-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="136bd-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="136bd-476">シミュレートされたコント ローラーのタッチパッドでシミュレートされた本の指の位置を設定します。</span><span class="sxs-lookup"><span data-stu-id="136bd-476">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="136bd-477">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136bd-477">Parameters</span></span>
* <span data-ttu-id="136bd-478">x 軸の指の水平位置。</span><span class="sxs-lookup"><span data-stu-id="136bd-478">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="136bd-479">y の指の垂直位置。</span><span class="sxs-lookup"><span data-stu-id="136bd-479">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="136bd-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="136bd-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="136bd-481">追加のプロパティとメソッドは、使用可能な ISimulatedSixDofController ISimulatedSixDofController2 にキャストすることによって</span><span class="sxs-lookup"><span data-stu-id="136bd-481">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="136bd-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition (out float、float を)**</span><span class="sxs-lookup"><span data-stu-id="136bd-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="136bd-483">シミュレートされたコント ローラーでシミュレートされたスティックの位置を取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-483">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="136bd-484">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136bd-484">Parameters</span></span>
* <span data-ttu-id="136bd-485">x - スティックの水平位置。</span><span class="sxs-lookup"><span data-stu-id="136bd-485">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="136bd-486">y スティックの垂直位置。</span><span class="sxs-lookup"><span data-stu-id="136bd-486">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="136bd-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="136bd-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="136bd-488">シミュレートされたコント ローラーで、シミュレートされたスティックの位置を設定します。</span><span class="sxs-lookup"><span data-stu-id="136bd-488">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="136bd-489">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136bd-489">Parameters</span></span>
* <span data-ttu-id="136bd-490">x - スティックの水平位置。</span><span class="sxs-lookup"><span data-stu-id="136bd-490">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="136bd-491">y スティックの垂直位置。</span><span class="sxs-lookup"><span data-stu-id="136bd-491">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="136bd-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="136bd-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="136bd-493">取得またはシミュレートされたコント ローラーのバッテリ レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="136bd-493">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="136bd-494">値は 0.0 より大きくする必要があります、100.0 以下。</span><span class="sxs-lookup"><span data-stu-id="136bd-494">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="136bd-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="136bd-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="136bd-496">シミュレートされた人間の目を記述するインターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="136bd-496">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="136bd-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span><span class="sxs-lookup"><span data-stu-id="136bd-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="136bd-498">シミュレートされた目の回転角度を取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-498">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="136bd-499">軸に検索するときに、正のラジアンは右回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="136bd-499">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="136bd-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="136bd-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="136bd-501">現在、回転の基準としたシミュレートされた目を回転します。</span><span class="sxs-lookup"><span data-stu-id="136bd-501">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="136bd-502">軸に検索するときに、正のラジアンは右回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="136bd-502">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="136bd-503">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136bd-503">Parameters</span></span>
* <span data-ttu-id="136bd-504">回転の回転する量。</span><span class="sxs-lookup"><span data-stu-id="136bd-504">rotation - The amount to rotate.</span></span>

<span data-ttu-id="136bd-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="136bd-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="136bd-506">取得またはシミュレートされた目の調整状態を設定します。</span><span class="sxs-lookup"><span data-stu-id="136bd-506">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="136bd-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="136bd-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="136bd-508">メートル単位で、世界中とに関してノードの位置を取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-508">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="136bd-509">Microsoft.PerceptionSimulation.ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="136bd-509">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="136bd-510">再生用に 1 つの記録と対話するためのインターフェイスが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="136bd-510">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="136bd-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span><span class="sxs-lookup"><span data-stu-id="136bd-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="136bd-512">記録のデータ型の一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-512">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="136bd-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span><span class="sxs-lookup"><span data-stu-id="136bd-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="136bd-514">記録の現在の状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="136bd-514">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="136bd-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span><span class="sxs-lookup"><span data-stu-id="136bd-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="136bd-516">再生を開始します。</span><span class="sxs-lookup"><span data-stu-id="136bd-516">Start the playback.</span></span> <span data-ttu-id="136bd-517">記録を一時停止すると、再生が一時停止中の場所から再開されます。停止した場合、先頭に再生が開始されます。</span><span class="sxs-lookup"><span data-stu-id="136bd-517">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="136bd-518">既に再生中の場合は、この呼び出しは無視されます。</span><span class="sxs-lookup"><span data-stu-id="136bd-518">If already playing, this call is ignored.</span></span>

<span data-ttu-id="136bd-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span><span class="sxs-lookup"><span data-stu-id="136bd-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="136bd-520">現在の場所で再生を一時停止します。</span><span class="sxs-lookup"><span data-stu-id="136bd-520">Pauses the playback at its current location.</span></span> <span data-ttu-id="136bd-521">記録が停止している場合、呼び出しは無視されます。</span><span class="sxs-lookup"><span data-stu-id="136bd-521">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="136bd-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span><span class="sxs-lookup"><span data-stu-id="136bd-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="136bd-523">(最初から 100 ナノ秒間隔) で指定された時間に、記録をシークし、その場所に一時停止します。</span><span class="sxs-lookup"><span data-stu-id="136bd-523">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="136bd-524">時間が、記録の末尾を越える場合、最後のフレームで一時停止中です。</span><span class="sxs-lookup"><span data-stu-id="136bd-524">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="136bd-525">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136bd-525">Parameters</span></span>
* <span data-ttu-id="136bd-526">タイマー刻みの時刻をシークします。</span><span class="sxs-lookup"><span data-stu-id="136bd-526">ticks - The time to which to seek.</span></span>

<span data-ttu-id="136bd-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span><span class="sxs-lookup"><span data-stu-id="136bd-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="136bd-528">再生を停止し、先頭に位置をリセットします。</span><span class="sxs-lookup"><span data-stu-id="136bd-528">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="136bd-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="136bd-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="136bd-530">再生中に状態の変更を受信するためのインターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="136bd-530">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="136bd-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="136bd-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="136bd-532">ISimulationRecording の再生の状態が変更されたときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="136bd-532">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="136bd-533">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136bd-533">Parameters</span></span>
* <span data-ttu-id="136bd-534">newState の記録の新しい状態。</span><span class="sxs-lookup"><span data-stu-id="136bd-534">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="136bd-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="136bd-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="136bd-536">Perception シミュレーション オブジェクトを作成するためのルート オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="136bd-536">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="136bd-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="136bd-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="136bd-538">シミュレートされたパケットを生成すると、指定されたシンクへの配信にオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="136bd-538">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="136bd-539">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136bd-539">Parameters</span></span>
* <span data-ttu-id="136bd-540">シンクしますで生成されたすべてのパケットを受信するシンク。</span><span class="sxs-lookup"><span data-stu-id="136bd-540">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="136bd-541">戻り値</span><span class="sxs-lookup"><span data-stu-id="136bd-541">Return value</span></span>

<span data-ttu-id="136bd-542">作成したマネージャー。</span><span class="sxs-lookup"><span data-stu-id="136bd-542">The created Manager.</span></span>

<span data-ttu-id="136bd-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span><span class="sxs-lookup"><span data-stu-id="136bd-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="136bd-544">指定したパスにあるファイルのすべての受信パケットを格納するシンクを作成します。</span><span class="sxs-lookup"><span data-stu-id="136bd-544">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="136bd-545">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136bd-545">Parameters</span></span>
* <span data-ttu-id="136bd-546">パス - 作成するファイルのパス。</span><span class="sxs-lookup"><span data-stu-id="136bd-546">path - The path of the file to create.</span></span>

<span data-ttu-id="136bd-547">戻り値</span><span class="sxs-lookup"><span data-stu-id="136bd-547">Return value</span></span>

<span data-ttu-id="136bd-548">作成したシンク。</span><span class="sxs-lookup"><span data-stu-id="136bd-548">The created sink.</span></span>

<span data-ttu-id="136bd-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="136bd-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="136bd-550">指定したファイルから録画を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="136bd-550">Load a recording from the specified file.</span></span>

<span data-ttu-id="136bd-551">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136bd-551">Parameters</span></span>
* <span data-ttu-id="136bd-552">パス - 読み込むファイルのパス。</span><span class="sxs-lookup"><span data-stu-id="136bd-552">path - The path of the file to load.</span></span>
* <span data-ttu-id="136bd-553">工場出荷時のために必要なときに、ISimulationStreamSink を作成するため、記録することによって使用されるファクトリ。</span><span class="sxs-lookup"><span data-stu-id="136bd-553">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="136bd-554">戻り値</span><span class="sxs-lookup"><span data-stu-id="136bd-554">Return value</span></span>

<span data-ttu-id="136bd-555">読み込まれた記録します。</span><span class="sxs-lookup"><span data-stu-id="136bd-555">The loaded recording.</span></span>

<span data-ttu-id="136bd-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory、Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="136bd-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="136bd-557">指定したファイルから録画を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="136bd-557">Load a recording from the specified file.</span></span>

<span data-ttu-id="136bd-558">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136bd-558">Parameters</span></span>
* <span data-ttu-id="136bd-559">パス - 読み込むファイルのパス。</span><span class="sxs-lookup"><span data-stu-id="136bd-559">path - The path of the file to load.</span></span>
* <span data-ttu-id="136bd-560">工場出荷時のために必要なときに、ISimulationStreamSink を作成するため、記録することによって使用されるファクトリ。</span><span class="sxs-lookup"><span data-stu-id="136bd-560">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="136bd-561">callback - コールバックを受信は、regrading 記録の状態を更新します。</span><span class="sxs-lookup"><span data-stu-id="136bd-561">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="136bd-562">戻り値</span><span class="sxs-lookup"><span data-stu-id="136bd-562">Return value</span></span>

<span data-ttu-id="136bd-563">読み込まれた記録します。</span><span class="sxs-lookup"><span data-stu-id="136bd-563">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="136bd-564">Microsoft.PerceptionSimulation.StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="136bd-564">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="136bd-565">ストリーム データのさまざまな種類をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="136bd-565">Describes the different types of stream data.</span></span>

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

<span data-ttu-id="136bd-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span><span class="sxs-lookup"><span data-stu-id="136bd-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="136bd-567">ストリームのデータ型がない場合に使用される sentinel 値。</span><span class="sxs-lookup"><span data-stu-id="136bd-567">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="136bd-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span><span class="sxs-lookup"><span data-stu-id="136bd-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="136bd-569">Stream の位置と、先頭の向きに関するデータ。</span><span class="sxs-lookup"><span data-stu-id="136bd-569">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="136bd-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span><span class="sxs-lookup"><span data-stu-id="136bd-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="136bd-571">Stream の位置と手のジェスチャに関するデータ。</span><span class="sxs-lookup"><span data-stu-id="136bd-571">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="136bd-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="136bd-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="136bd-573">Stream の環境の空間のマッピングに関するデータ。</span><span class="sxs-lookup"><span data-stu-id="136bd-573">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="136bd-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span><span class="sxs-lookup"><span data-stu-id="136bd-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="136bd-575">デバイスの調整に関するデータの Stream。</span><span class="sxs-lookup"><span data-stu-id="136bd-575">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="136bd-576">調整のパケットは、リモート モードでのシステムでのみ受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="136bd-576">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="136bd-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span><span class="sxs-lookup"><span data-stu-id="136bd-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="136bd-578">デバイスの環境に関するデータの Stream。</span><span class="sxs-lookup"><span data-stu-id="136bd-578">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="136bd-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span><span class="sxs-lookup"><span data-stu-id="136bd-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="136bd-580">すべて記録されたデータ型を示すために使用される sentinel 値。</span><span class="sxs-lookup"><span data-stu-id="136bd-580">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="136bd-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="136bd-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="136bd-582">シミュレーションのストリームからデータ パケットを受信するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="136bd-582">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="136bd-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived (uint の長さ、byte パケット)**</span><span class="sxs-lookup"><span data-stu-id="136bd-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="136bd-584">内部的に型指定されたおよびバージョン管理は、1 つのパケットを受信します。</span><span class="sxs-lookup"><span data-stu-id="136bd-584">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="136bd-585">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136bd-585">Parameters</span></span>
* <span data-ttu-id="136bd-586">length - パケットの長さ。</span><span class="sxs-lookup"><span data-stu-id="136bd-586">length - The length of the packet.</span></span>
* <span data-ttu-id="136bd-587">パケットのパケットのデータです。</span><span class="sxs-lookup"><span data-stu-id="136bd-587">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="136bd-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="136bd-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="136bd-589">ISimulationStreamSink を作成するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="136bd-589">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="136bd-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span><span class="sxs-lookup"><span data-stu-id="136bd-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="136bd-591">ISimulationStreamSink の 1 つのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="136bd-591">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="136bd-592">戻り値</span><span class="sxs-lookup"><span data-stu-id="136bd-592">Return value</span></span>

<span data-ttu-id="136bd-593">作成したシンク。</span><span class="sxs-lookup"><span data-stu-id="136bd-593">The created sink.</span></span>
