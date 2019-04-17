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
# <a name="perception-simulation"></a>Perception シミュレーション

アプリの自動テストをビルドしますか。 コンポーネント レベルの単体テストを超えるし、実際に、アプリのエンドを実行するためのテストを作成しますか。 Perception シミュレーションは、探しているものです。 Perception シミュレーション ライブラリ偽の人間と送信の世界の入力データをアプリに、テストを自動化できるようにします。 たとえば、左と右に人間の検索とジェスチャを実行することの入力をシミュレートできます。

Perception シミュレーションでは、物理 HoloLens、HoloLens のエミュレーター、またはインストールされている混合の現実ポータルを使用した PC にこのようなシミュレーションの入力を送信できます。 Perception Mixed Reality デバイスでライブのセンサーをバイパスし、シミュレーションでは、デバイスで実行されているアプリケーションへの入力をシミュレートします。 アプリケーションでは、使用、および知覚のシミュレーションを実行するいると実際のセンサーを実行している間の違いを見分けることはできませんが、常に、同じ Api を介してこれら偽の入力イベントを受信します。 Perception シミュレーションは、シミュレートされた入力、HoloLens 仮想マシンに送信するために使用、HoloLens のエミュレーターと同じテクノロジです。

シミュレーションでは、まず、IPerceptionSimulationManager オブジェクトを作成します。 そのオブジェクトは、シミュレートされた「人事」、ヘッドの位置、手の形の位置、ジェスチャなどのプロパティを制御するためのコマンドを発行できます。

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>Perception でシミュレーションするための Visual Studio プロジェクトの設定
1. [HoloLens のエミュレーターをインストール](install-the-tools.md)開発 PC 上。 エミュレーターには、Perception シミュレーションに使用するライブラリが含まれています。
2. 作成する新しい Visual StudioC#デスクトップのプロジェクト (コンソール プロジェクトをうまくを開始する)。
3. 次のバイナリをプロジェクトに参照として追加 (プロジェクトに追加]-> [-> 参照)。検索できます **%programfiles (x86) %\Microsoft XDE\10.0.11082.0**をします。 管理 - PerceptionSimulationManager.Interop.dll C# Perception シミュレーション用のラッパーです。
    b.  PerceptionSimulationRest.dll - HoloLens またはエミュレーターへの web ソケット通信チャネルを設定するためのライブラリを使用します。
    c. SimulationStream.Interop.dll のシミュレーションを共有する型。
4. 実装を追加するプロジェクト バイナリ PerceptionSimulationManager.dll。 まず、プロジェクトに、バイナリとして追加 (プロジェクトに追加-> -> 既存項目の)。プロジェクトのソース フォルダーにコピーしないように、リンクとして保存します。 ![PerceptionSimulationManager.dll をリンクとしてプロジェクトに追加](images/saveaslink.png)b。 確認し、ビルドの出力フォルダーにコピーすることがあるのです。 これは、バイナリのプロパティ シートです。 ![マーク PerceptionSimulationManager.dll 出力ディレクトリにコピーするには](images/copyalways.png)

## <a name="creating-an-iperceptionsimulation-manager-object"></a>IPerceptionSimulation マネージャー オブジェクトを作成します。

シミュレーションを制御するには、IPerceptionSimulationManager オブジェクトから取得したオブジェクトの更新プログラムを発行します。 最初の手順では、そのオブジェクトを取得し、ターゲット デバイスまたはエミュレーターに接続します。 デバイスのポータル をクリックして、エミュレーターの IP アドレスを取得できます、[ツールバー](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)

![デバイスのポータルを開く アイコン](images/emulator-deviceportal.png)**デバイス ポータルを開く**:エミュレーターでの HoloLens os、Windows Device Portal を開きます。

まず、RestSimulationStreamSink.Create RestSimulationStreamSink オブジェクトを取得すると呼んでいます。 これは、対象のデバイスまたはエミュレーターを http 接続を介して制御されます。 コマンドに渡され、によって処理されますが、 [Windows Device Portal](using-the-windows-device-portal.md)デバイスまたはエミュレーターで実行されています。 オブジェクトを作成する必要があります、4 つのパラメーターは次のとおりです。
* Uri の uri、ターゲット デバイスの IP アドレス (例:"http://123.123.123.123")
* System.Net.NetworkCredential 資格情報 - に接続するためには、ユーザー名/パスワード、 [Windows Device Portal](using-the-windows-device-portal.md)ターゲット デバイスまたはエミュレーターにします。 そのローカル 168 を使用してエミュレーターに接続しています。 場合、*.*。 * アドレス同じ pc では、すべての資格情報が受け入れられます。
* bool の通常の通常の優先順位、優先度の低いは false の場合は True。 一般にこれを設定する*true*テスト シナリオ用。
* System.Threading.CancellationToken トークン - 非同期操作をキャンセルするトークンです。

2 つ目は、IPerceptionSimulationManager を作成します。 これは、使用してシミュレーションを制御するオブジェクトです。 これをも実行することで、非同期メソッドに注意してください。

## <a name="control-the-simulated-human"></a>シミュレートされたユーザーを制御します。

IPerceptionSimulationManager には、ISimulatedHuman オブジェクトを返す人間プロパティがあります。 シミュレートされたユーザーを制御するには、このオブジェクトに対して操作を実行します。 次に、例を示します。

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a>基本的なサンプルC#コンソール アプリケーション

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

## <a name="extended-sample-c-console-application"></a>サンプルを拡張C#コンソール アプリケーション

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

## <a name="api-reference"></a>API リファレンス

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a>Microsoft.PerceptionSimulation.SimulatedDeviceType

シミュレートされたデバイスの種類について説明します

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**

架空の参照のデバイスでは、PerceptionSimulationManager の既定値

### <a name="microsoftperceptionsimulationheadtrackermode"></a>Microsoft.PerceptionSimulation.HeadTrackerMode

ヘッド トラッカー モードについて説明します

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**

既定の Head が追跡します。 つまり、システムは、追跡モードの実行時の条件に基づいて最適なヘッドを選択ことがあります。

**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**

印刷の向きのみヘッドが追跡します。 つまり、追跡対象の位置は、信頼性が高く、できない場合があります、ヘッドの位置に依存する一部の機能を利用できない可能性があります。

**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**

ヘッドの位置指定の追跡。 つまり、追跡されているヘッドの位置と向きの両方がある信頼性の高い

### <a name="microsoftperceptionsimulationsimulatedgesture"></a>Microsoft.PerceptionSimulation.SimulatedGesture

シミュレートされたジェスチャを説明します。

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

**Microsoft.PerceptionSimulation.SimulatedGesture.None**

ジェスチャがない場合に使用される sentinel 値

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**

ジェスチャが押された指

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**

リリースの指のジェスチャ

**Microsoft.PerceptionSimulation.SimulatedGesture.Home**

ホームのジェスチャ

**Microsoft.PerceptionSimulation.SimulatedGesture.Max**

最大の有効なジェスチャ

### <a name="microsoftperceptionsimulationplaybackstate"></a>Microsoft.PerceptionSimulation.PlaybackState

再生の状態について説明します

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

**Microsoft.PerceptionSimulation.PlaybackState.Stopped**

記録の停止と再生の準備ができては現在

**Microsoft.PerceptionSimulation.PlaybackState.Playing**

記録を再生中

**Microsoft.PerceptionSimulation.PlaybackState.Paused**

記録が現在一時停止しています

**Microsoft.PerceptionSimulation.PlaybackState.End**

記録が末尾に達した

### <a name="microsoftperceptionsimulationvector3"></a>Microsoft.PerceptionSimulation.Vector3

点または 3D 空間でベクターを表す場合があります、3 つのコンポーネントのベクターをについて説明します。

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

**Microsoft.PerceptionSimulation.Vector3.X**

ベクターの X コンポーネント

**Microsoft.PerceptionSimulation.Vector3.Y**

ベクターの Y コンポーネント

**Microsoft.PerceptionSimulation.Vector3.Z**

ベクトルの Z 成分

**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**

新しい Vector3 を構築します。

パラメーター
* ベクターの x、x コンポーネント
* y 軸ベクターの、y コンポーネント
* ベクトルの z、z 成分

### <a name="microsoftperceptionsimulationrotation3"></a>Microsoft.PerceptionSimulation.Rotation3

3 つのコンポーネントの回転をについて説明します。

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

**Microsoft.PerceptionSimulation.Rotation3.Pitch**

回転のピッチ コンポーネントは、X 軸の周りのダウン

**Microsoft.PerceptionSimulation.Rotation3.Yaw**

Y 軸の周囲の回転のヨー コンポーネント

**Microsoft.PerceptionSimulation.Rotation3.Roll**

Z 軸の周囲の回転のロールのコンポーネント

**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**

新しい Rotation3 を構築します。

パラメーター
* ピッチの回転のピッチ コンポーネント
* ヨー、回転のヨー コンポーネント
* ロールの回転のロールのコンポーネント

### <a name="microsoftperceptionsimulationfrustum"></a>Microsoft.PerceptionSimulation.Frustum

カメラで通常使用される視錐台をについて説明します。

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

**Microsoft.PerceptionSimulation.Frustum.Near**

最小の距離の視錐台に含まれています。

**Microsoft.PerceptionSimulation.Frustum.Far**

最大距離の視錐台に含まれています。

**Microsoft.PerceptionSimulation.Frustum.FieldOfView**

ラジアン (PI よりも小さい) 視錐台の横のフィールドの表示

**Microsoft.PerceptionSimulation.Frustum.AspectRatio**

垂直ビューのフィールドへの水平視野の比率

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.IPerceptionSimulationManager

デバイスの制御に使用されるパケットを生成するためのルート

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**

シミュレートされた人と、シミュレートされた世界を解釈するシミュレートされたデバイス オブジェクトを取得します。

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**

シミュレートされたユーザーを制御するオブジェクトを取得します。

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**

シミュレーションを既定の状態にリセットします。

### <a name="microsoftperceptionsimulationisimulateddevice"></a>Microsoft.PerceptionSimulation.ISimulatedDevice

シミュレートされた世界でシミュレートされた人間を解釈し、デバイスを記述するインターフェイスします。

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**

シミュレートされたデバイスから、ヘッドの追跡ツールを取得します。

**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**

シミュレートされたデバイスからの手の形の追跡ツールを取得します。

**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**

指定されたデバイスの種類に一致するように、シミュレートされたデバイスのプロパティを設定します。

パラメーター
* シミュレートされたデバイスの新しい種類を入力します。

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHeadTracker

シミュレートされた人間の頭を追跡するシミュレートされたデバイスの部分を記述するインターフェイスします。

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**

取得し、現在のトラッカーのヘッド モードを設定します。

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHandTracker

シミュレートされた人間の手を追跡するシミュレートされたデバイスの部分を記述するインターフェイスします。

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

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**

メートル単位で、世界中とに関してノードの位置を取得します。

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**

取得し、ヘッドの中央を基準、シミュレートされた手トラッカーの位置を設定します。

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**

取得し、シミュレートされた手トラッカーの下向きのピッチの設定

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**

取得し、シミュレートされた手トラッカーの視錐台を無視するかどうかを設定します。 無視される場合、両方の手は常に表示します。 (既定値) を無視しない場合に手は手トラッカーの視錐台内にあるときに、表示のみです。

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**

取得し、手がシミュレートされた手の追跡ツールに表示されるかどうかを判断するための視錐台プロパティを設定します。

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>Microsoft.PerceptionSimulation.ISimulatedHuman

シミュレートされたユーザーを制御するための最上位レベル インターフェイス

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

**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**

取得し、メートル単位で、世界中とに関してノードの位置を設定します。 位置は、人間のフィートの中央にある点に対応します。

**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**

取得し、世界中でシミュレートされた人の顔の方向を設定します。 負の Z 軸を 0 ラジアンに直面します。 Y 軸の正のラジアンは右回りに回転します。

**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**

取得し、シミュレーションの人間の高さをメートル単位で設定

**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**

シミュレートされた人間の左側を取得します。

**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**

シミュレートされた人間の右側を取得します。

**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**

シミュレートされた人間の頭を取得します。

**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**

メートル単位で、現在位置を基準として、シミュレートされた人間を移動します。

パラメーター
* 翻訳に移動して、現在の位置を基準に変換

**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**

Y 軸を中心に時計回りに現在方向の基準とした、シミュレートされた人間を回転します。

パラメーター
* ラジアン単位の Y 軸に沿って回転する量

### <a name="microsoftperceptionsimulationisimulatedhand"></a>Microsoft.PerceptionSimulation.ISimulatedHand

シミュレートされた人間の手の形を記述するインターフェイスします。

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

**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**

メートル単位で、世界中とに関してノードの位置を取得します。

**Microsoft.PerceptionSimulation.ISimulatedHand.Position**

取得し、メートル単位で、人間の基準とした、シミュレートされた手の形の位置を設定します。

**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**

取得し、手の形が現在アクティブかどうかを設定します。

**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**

手のアイコンが (つまり、かどうかは、HandTracker によって検出された位置に) SimulatedDevice に現在表示されているかどうかを取得します。

**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**

SimulatedDevice に表示されるようにして手のアイコンに移動します。

**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**

メートル単位で、現在位置を基準として、シミュレートされた手の形の位置を移動します。

パラメーター
* 翻訳 - シミュレートされた手の形を平行移動量

**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**

(のみ検出されます、システムによって、手が有効になっている場合)、シミュレートされた手の形を使用するジェスチャを実行します。

パラメーター
* ジェスチャのジェスチャを実行するには

### <a name="microsoftperceptionsimulationisimulatedhead"></a>Microsoft.PerceptionSimulation.ISimulatedHead

シミュレートされた人間の頭を記述するインターフェイスします。

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**

メートル単位で、世界中とに関してノードの位置を取得します。

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**

シミュレートされた先頭の回転角度を取得します。 軸に検索するときに、正のラジアンは右回りに回転します。

**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**

シミュレートされた先頭の直径を取得します。 この値は、ヘッドのセンター (回転のポイント) を確認するに使用されます。

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**

現在、回転の基準としたシミュレートされたヘッドを回転します。 軸に検索するときに、正のラジアンは右回りに回転します。

パラメーター
* 回転の量を回転するには

### <a name="microsoftperceptionsimulationisimulationrecording"></a>Microsoft.PerceptionSimulation.ISimulationRecording

再生用に 1 つの記録と対話するためのインターフェイスが読み込まれます。

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

**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**

記録のデータ型の一覧を取得します。

**Microsoft.PerceptionSimulation.ISimulationRecording.State**

記録の現在の状態を取得します。

**Microsoft.PerceptionSimulation.ISimulationRecording.Play**

再生を開始します。 記録を一時停止すると、再生が一時停止中の場所から再開されます。停止した場合、先頭に再生が開始されます。 既に再生中の場合は、この呼び出しは無視されます。

**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**

現在の場所で再生を一時停止します。 記録が停止している場合、呼び出しは無視されます。

**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**

(最初から 100 ナノ秒間隔) で指定された時間に、記録をシークし、その場所に一時停止します。 時間が、記録の末尾を越える場合、最後のフレームで一時停止中です。

パラメーター
* タイマー刻みの時刻をシークします。

**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**

再生を停止し、先頭に位置をリセット

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>Microsoft.PerceptionSimulation.ISimulationRecordingCallback

再生中に状態の変更を受信するためのインターフェイス

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**

ISimulationRecording の再生の状態が変更されたときに呼び出されます

パラメーター
* newState の記録の新しい状態

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.PerceptionSimulationManager

Perception シミュレーション オブジェクトを作成するためのルート オブジェクト

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**

シミュレートされたパケットを生成すると、指定されたシンクへの配信にオブジェクトを作成します。

パラメーター
* 生成されたすべてのパケットを受信するシンクをシンクします。

戻り値

作成したマネージャー

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**

指定したパスにあるファイルのすべての受信パケットを格納するシンクを作成します。

パラメーター
* パス - 作成するファイルのパス

戻り値

作成したシンク

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**

指定したファイルから、記録を読み込む

パラメーター
* 読み込むファイルのパスのパス
* 工場出荷時のために必要なときに、ISimulationStreamSink を作成するため、記録することによって使用されるファクトリ

戻り値

読み込まれた記録

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory、Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**

指定したファイルから、記録を読み込む

パラメーター
* 読み込むファイルのパスのパス
* 工場出荷時のために必要なときに、ISimulationStreamSink を作成するため、記録することによって使用されるファクトリ
* callback - コールバックを受け取る更新 regrading 記録の状態

戻り値

読み込まれた記録

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>Microsoft.PerceptionSimulation.StreamDataTypes

ストリーム データのさまざまな種類について説明します

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

**Microsoft.PerceptionSimulation.StreamDataTypes.None**

ストリームのデータ型がない場合に使用される sentinel 値

**Microsoft.PerceptionSimulation.StreamDataTypes.Head**

位置と、先頭の向きに関するデータの Stream

**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**

位置と手のジェスチャに関するデータの Stream

**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**

環境の空間のマッピングに関するデータの Stream

**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**

デバイスの調整に関するデータの Stream。 調整のパケットは、リモート モードでのシステムでのみ受け入れられます。

**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**

デバイスの環境に関するデータの Stream

**Microsoft.PerceptionSimulation.StreamDataTypes.All**

すべて記録されたデータ型を示すために使用される sentinel 値

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>Microsoft.PerceptionSimulation.ISimulationStreamSink

シミュレーションのストリームからデータ パケットを受信するオブジェクト

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived (uint の長さ、byte パケット)**

内部的に型指定されたおよびバージョン管理は、1 つのパケットを受信します。

パラメーター
* length - パケットの長さ
* パケットのパケットのデータ

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory

ISimulationStreamSink を作成するオブジェクト

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**

ISimulationStreamSink の 1 つのインスタンスを作成します。

戻り値

作成したシンク
