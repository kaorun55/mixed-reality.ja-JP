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
# <a name="perception-simulation"></a>Perception シミュレーション

アプリの自動テストをビルドしますか。 コンポーネント レベルの単体テストを超えるし、実際に、アプリのエンドを実行するためのテストを作成しますか。 Perception シミュレーションは、探しているものです。 Perception シミュレーション ライブラリが人間に送信し、テストを自動化できるように、世界がアプリにデータを入力します。 たとえば、人間、反復可能な特定の位置を検索およびジェスチャを実行することまたはのモーション コント ローラーを使用して入力をシミュレートできます。

Perception シミュレーションは、物理 HoloLens、HoloLens のエミュレーターに次のように、シミュレートされた入力を送信できます (第 1 世代)、2 つのエミュレーター、または Mixed Reality ポータルを使用した PC HoloLens をインストールします。 Perception Mixed Reality デバイスでライブのセンサーをバイパスし、シミュレーションでは、デバイスで実行されているアプリケーションへの入力をシミュレートします。 アプリケーションでは、同じ api を使用して、Perception シミュレーションを実行するいると実際のセンサーを実行している間の違いを見分けることはできませんが、常にこれらの入力イベントを受信します。 Perception シミュレーションは、シミュレートされた入力、HoloLens 仮想マシンに送信するために使用、HoloLens のエミュレーターと同じテクノロジです。

コードでシミュレーションを使用するには、まず IPerceptionSimulationManager オブジェクトを作成します。 、そのオブジェクトから、シミュレートされた「人事」、ヘッドの位置、手の形の位置、ジェスチャなどのプロパティを制御するためのコマンドを実行できると有効にし、アニメーション コント ローラーを操作できます。

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>Perception でシミュレーションするための Visual Studio プロジェクトの設定
1. [HoloLens のエミュレーターをインストール](install-the-tools.md)開発 PC 上。 エミュレーターには、Perception シミュレーションに使用するライブラリが含まれています。
2. 作成する新しい Visual StudioC#デスクトップのプロジェクト (コンソール プロジェクトをうまくを開始する)。
3. 次のバイナリをプロジェクトに参照として追加 (プロジェクトに追加]-> [-> 参照)。%Programfiles (x86) %\Microsoft XDE で検索することができます\\(バージョン) など、 **%programfiles (x86) %\Microsoft XDE\\10.0.18362.0** HoloLens のエミュレーターの 2。  (注: バイナリには、HoloLens 2 エミュレーターの一部が、でも正しく動作 Windows Mixed Reality のデスクトップ)。します。 管理 - PerceptionSimulationManager.Interop.dll C# Perception シミュレーション用のラッパーです。
    b. PerceptionSimulationRest.dll - HoloLens またはエミュレーターへの web ソケット通信チャネルを設定するためのライブラリを使用します。
    c. SimulationStream.Interop.dll のシミュレーションを共有する型。
4. 実装を追加するプロジェクト バイナリ PerceptionSimulationManager.dll。 まず、プロジェクトに、バイナリとして追加 (プロジェクトに追加-> -> 既存項目の)。プロジェクトのソース フォルダーにコピーしないように、リンクとして保存します。 ![PerceptionSimulationManager.dll をリンクとしてプロジェクトに追加](images/saveaslink.png)b。 確認し、ビルドの出力フォルダーにコピーすることがあるのです。 これは、バイナリのプロパティ シートです。 ![マーク PerceptionSimulationManager.dll 出力ディレクトリにコピーするには](images/copyalways.png)
5. アクティブ ソリューション プラットフォームを x64 に設定します。  (使用の場合は、1 つは、x64 プラットフォーム エントリを作成する Configuration Manager が存在しない)

## <a name="creating-an-iperceptionsimulation-manager-object"></a>IPerceptionSimulation マネージャー オブジェクトを作成します。

シミュレーションを制御するには、IPerceptionSimulationManager オブジェクトから取得したオブジェクトの更新プログラムを発行します。 最初の手順では、そのオブジェクトを取得し、ターゲット デバイスまたはエミュレーターに接続します。 デバイスのポータル をクリックして、エミュレーターの IP アドレスを取得できます、[ツールバー](using-the-hololens-emulator.md)

![デバイスのポータルを開く アイコン](images/emulator-deviceportal.png)**デバイス ポータルを開く**:エミュレーターで HoloLens OS の Windows デバイス ポータルを開きます。  For Windows Mixed Reality、これで取得できる"For developers"し、[更新とセキュリティ]、で、設定アプリで、"を使用して接続します""を有効にするデバイス ポータルです。"[] セクション。  必ず、IP アドレスとポートの両方に注意してください。

まず、RestSimulationStreamSink.Create RestSimulationStreamSink オブジェクトを取得すると呼んでいます。 これは、対象のデバイスまたはエミュレーターを http 接続を介して制御されます。 コマンドに渡され、によって処理されますが、 [Windows Device Portal](using-the-windows-device-portal.md)デバイスまたはエミュレーターで実行されています。 オブジェクトを作成する必要があります、4 つのパラメーターは次のとおりです。
* Uri の uri、ターゲット デバイスの IP アドレス (例:"http://123.123.123.123 「または」 http://123.123.123.123:50080")
* System.Net.NetworkCredential 資格情報 - に接続するためには、ユーザー名/パスワード、 [Windows Device Portal](using-the-windows-device-portal.md)ターゲット デバイスまたはエミュレーターにします。 そのローカル アドレスを使用してエミュレーターに接続するかどうか (例: 168。 *。* 。 *) 同じ pc では、すべての資格情報が受け入れられます。
* bool の通常の通常の優先順位、優先度の低いは false の場合は True。 一般にこれを設定する*true*テストのシナリオは、制御するためのテストを使用します。  エミュレーターと Windows Mixed Reality シミュレーションは、優先度の低い接続を使用します。  場合は、テストは、優先度の低い接続を使用しても、最も最近確立された接続は、コントロール内になります。
* System.Threading.CancellationToken トークン - 非同期操作をキャンセルするトークンです。

2 つ目は、IPerceptionSimulationManager を作成します。 これは、使用してシミュレーションを制御するオブジェクトです。 これをも実行することで、非同期メソッドに注意してください。

## <a name="control-the-simulated-human"></a>シミュレートされたユーザーを制御します。

IPerceptionSimulationManager には、ISimulatedHuman オブジェクトを返す人間プロパティがあります。 シミュレートされたユーザーを制御するには、このオブジェクトに対して操作を実行します。 例:

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

## <a name="note-on-6-dof-controllers"></a>6-自由度のコント ローラー上に注意してください。

シミュレートされた 6-自由度のコント ローラーのメソッドで、任意のプロパティを呼び出す前に、コント ローラーをアクティブ化する必要があります。  そうしないと、例外が発生します。  可能性があります 2019 の更新を Windows 10 以降では、シミュレートされた 6-自由度のコント ローラーをインストールおよび SimulatedSixDofControllerStatus.Active ISimulatedSixDofController オブジェクトの Status プロパティを設定してアクティブ化されることができます。
Windows 10 年 2018年 10 月の更新前に、インストールしてする必要がありますとは別に、シミュレートされた 6-自由度のコント ローラー最初 \Windows\System32 フォルダーにある PerceptionSimulationDevice ツールを呼び出すことによって。  このツールの使用状況は次のとおりです。


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

次に例を示します。

```
    PerceptionSimulationDevice.exe i 6dof 1
```

サポートされているアクションは次のとおりです。
* インストールを =
* q = クエリ
* r = 削除

サポートされているインスタンスは次のとおりです。
* 1 = の左側の 6-自由度のコント ローラー
* 2 = 右 6-自由度のコント ローラー

(0 は、値を返す) の成功または失敗 (0 以外の戻り値)、プロセスの終了コードを示します。  'Q' のアクションを使用して、コント ローラーがインストールされているかどうかを照会する、戻り値は必要コント ローラーがインストールされている場合はゼロ (0)、コント ローラーが既にインストールされていない場合、または 1 (1) とになります。

Windows 上のコント ローラーを削除するときに、10 年 2018年 10 月の更新または以前では、オフ、API を使用して最初に、呼び出して PerceptionSimulationDevice ツールには、その状態を設定します。

このツールは、管理者として実行する必要がありますに注意してください。




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

ジェスチャがない場合に使用される sentinel 値。

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**

指では、ジェスチャが押されました。

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**

指では、ジェスチャがリリースされました。

**Microsoft.PerceptionSimulation.SimulatedGesture.Home**

ホーム/システム ジェスチャ。

**Microsoft.PerceptionSimulation.SimulatedGesture.Max**

最大の有効なジェスチャ。

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a>Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus

シミュレートされた 6-自由度のコント ローラーの状態。

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**

6-自由度のコント ローラーがオフになります。

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**

6-自由度のコント ローラーが有効になり、追跡。

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**

6-自由度のコント ローラーは、有効になってが追跡することはできません。

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a>Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton

シミュレートされた 6-自由度のコント ローラーでサポートされているボタン。

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

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**

ボタンがない場合に使用される sentinel 値。

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**

[ホーム] ボタンが押されました。

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**

メニュー ボタンが押されました。

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**

グリップのボタンが押されました。

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**

タッチパッドが押されました。

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**

[選択] ボタンが押されました。

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**

タッチパッドをタッチするとします。

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**

スティックが押されました。

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**

有効なボタンの最大値。


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a>Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState

シミュレートされた目の調整状態

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**

目の調整は、ご利用いただけません。

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**

目が調整されています。  これが既定値です。

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**

目が調整されています。

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**

目では、調整する必要があります。

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a>Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy

針のジョイントの追跡の精度。

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**

ジョイントは追跡されません。

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**

共同の位置が推論されます。

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**

ジョイントがすべて記録します。

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a>Microsoft.PerceptionSimulation.SimulatedHandPose

針のジョイントの追跡の精度。

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

**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**

手の本の指の結合は、閉じた姿勢を反映するように構成されます。

**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**

手の本の指の結合は、オープンの姿勢を反映するように構成されます。

**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**

手の本の指ジョイントがポインティング姿勢を反映するように構成されます。

**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**

手の本の指の結合は、ピンチ姿勢を反映するように構成されます。

**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**

SimulatedHandPose の最大の有効な値。


### <a name="microsoftperceptionsimulationplaybackstate"></a>Microsoft.PerceptionSimulation.PlaybackState

再生の状態について説明します。

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

記録は、現在停止と再生の準備完了です。

**Microsoft.PerceptionSimulation.PlaybackState.Playing**

記録を再生中。

**Microsoft.PerceptionSimulation.PlaybackState.Paused**

記録を一時停止されています。

**Microsoft.PerceptionSimulation.PlaybackState.End**

記録は、末尾に達した。

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

ベクトルの X 成分。

**Microsoft.PerceptionSimulation.Vector3.Y**

ベクトルの Y 成分。

**Microsoft.PerceptionSimulation.Vector3.Z**

ベクトルの Z 成分。

**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**

新しい Vector3 を構築します。

パラメーター
* x - ベクターの x 成分。
* y のベクターの y 成分。
* z のベクトルの z 成分。

### <a name="microsoftperceptionsimulationrotation3"></a>Microsoft.PerceptionSimulation.Rotation3

3 つのコンポーネントの回転について説明します。

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

回転のピッチ コンポーネントは、X 軸を中心にダウンします。

**Microsoft.PerceptionSimulation.Rotation3.Yaw**

Y 軸の周囲の回転のヨー コンポーネントです。

**Microsoft.PerceptionSimulation.Rotation3.Roll**

Z 軸の周囲の回転のロールのコンポーネントです。

**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**

新しい Rotation3 を構築します。

パラメーター
* ピッチの回転の声の高さコンポーネント。
* ヨー、回転のヨー コンポーネント。
* ロールの回転のロールのコンポーネント。

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a>Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration

シミュレートされた手の形で、共同の構成について説明します。

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**

ジョイントの位置。

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**

ジョイントの回転。

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**

ジョイントの追跡の精度。


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

視錐台に含まれている最小の距離です。

**Microsoft.PerceptionSimulation.Frustum.Far**

最大距離の視錐台に含まれています。

**Microsoft.PerceptionSimulation.Frustum.FieldOfView**

ラジアン (PI よりも小さい) 視錐台の横のフィールドの表示。

**Microsoft.PerceptionSimulation.Frustum.AspectRatio**

垂直ビューのフィールドへの水平視野の比率です。

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.IPerceptionSimulationManager

デバイスの制御に使用されるパケットを生成するためのルートです。

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

取得し、シミュレートされた手トラッカーの下向きのピッチを設定します。

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**

取得し、シミュレートされた手トラッカーの視錐台を無視するかどうかを設定します。 無視される場合、両方の手は常に表示します。 (既定値) を無視しない場合に手は手トラッカーの視錐台内にあるときに、表示のみです。

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**

取得し、手がシミュレートされた手の追跡ツールに表示されるかどうかを判断するための視錐台プロパティを設定します。

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>Microsoft.PerceptionSimulation.ISimulatedHuman

シミュレートされたユーザーを制御するための最上位レベル インターフェイスです。

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

取得し、メートル単位でシミュレーションの人間の高さを設定します。

**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**

シミュレートされた人間の左側を取得します。

**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**

シミュレートされた人間の右側を取得します。

**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**

シミュレートされた人間の先頭を取得します。

**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**

メートル単位で、現在位置を基準として、シミュレートされた人間に移動します。

パラメーター
* 翻訳に移動して、現在の位置を基準に変換します。

**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**

Y 軸を中心に時計回りに現在方向の基準とした、シミュレートされた人間を回転します。

パラメーター
* ラジアンの Y 軸に沿って回転する量。

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a>Microsoft.PerceptionSimulation.ISimulatedHuman2

ISimulatedHuman2 に ISimulatedHuman をキャストすることによって、追加のプロパティは使用可能です

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**

左側の 6-自由度のコント ローラーを取得します。

**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**

右側の 6-自由度のコント ローラーを取得します。


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
* 翻訳 - シミュレートされた手の形を平行移動量。

**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**

シミュレートされたして手のアイコンを使用するジェスチャを実行します。  のみ検出されます、システムによって、手が有効になっている場合。

パラメーター
* ジェスチャのジェスチャを実行します。

### <a name="microsoftperceptionsimulationisimulatedhand2"></a>Microsoft.PerceptionSimulation.ISimulatedHand2

追加のプロパティは、ISimulatedHand ISimulatedHand2 にキャストすることによって利用可能です。
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**

取得またはシミュレートされた針の回転を設定します。  軸に検索するときに、正のラジアンは右回りに回転します。

### <a name="microsoftperceptionsimulationisimulatedhand3"></a>Microsoft.PerceptionSimulation.ISimulatedHand3

ISimulatedHand ISimulatedHand3 にキャストすることによって、追加のプロパティは使用可能です
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**

指定された共同の共同構成を取得します。

**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**

共同の指定された複合的な構成を設定します。

**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**

既知の姿勢をアニメーション化するオプションのフラグを使用して手のアイコンに設定します。  注: をアニメーション化力感の最終的な複合的な構成をすぐに反映されません。


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
* 回転の回転する量。

### <a name="microsoftperceptionsimulationisimulatedhead2"></a>Microsoft.PerceptionSimulation.ISimulatedHead2

ISimulatedHead ISimulatedHead2 にキャストすることによって、追加のプロパティは使用可能です

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**

シミュレートされた人間の目を取得します。

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a>Microsoft.PerceptionSimulation.ISimulatedSixDofController

シミュレートされたユーザーに関連付けられている 6 自由度のコント ローラーを記述するインターフェイスします。

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

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**

メートル単位で、世界中とに関してノードの位置を取得します。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**

取得またはコント ローラーの現在の状態を設定します。  コント ローラーの状態は、オフ呼び出しの前に、移動、回転、またはキーを押してボタンは成功以外の値に設定する必要があります。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**

取得またはメートル単位で、人間の基準とした、シミュレートされたコント ローラーの位置を設定します。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**

取得またはシミュレートされたコント ローラーの向きを設定します。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**

メートル単位で、現在位置を基準として、シミュレートされたコント ローラーの位置を移動します。

パラメーター
* 翻訳 - シミュレートされたコント ローラーの平行移動量。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**

シミュレートされたコント ローラー上のボタンを押します。  のみ検出されます、システムによって、コント ローラーが有効になっている場合。

パラメーター
* ボタン - キーを押すボタンをクリックします。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**

シミュレートされたコント ローラー上のボタンを離します。  のみ検出されます、システムによって、コント ローラーが有効になっている場合。

パラメーター
* ボタン - を解放するボタンをクリックします。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition (out float、float を)**

シミュレートされた、シミュレートされたコント ローラーのタッチパッド本の指の位置を取得します。

パラメーター
* x 軸の指の水平位置。
* y の指の垂直位置。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition (float, float)**

シミュレートされたコント ローラーのタッチパッドでシミュレートされた本の指の位置を設定します。

パラメーター
* x 軸の指の水平位置。
* y の指の垂直位置。

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a>Microsoft.PerceptionSimulation.ISimulatedSixDofController2

追加のプロパティとメソッドは、使用可能な ISimulatedSixDofController ISimulatedSixDofController2 にキャストすることによって

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition (out float、float を)**

シミュレートされたコント ローラーでシミュレートされたスティックの位置を取得します。

パラメーター
* x - スティックの水平位置。
* y スティックの垂直位置。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition (float, float)**

シミュレートされたコント ローラーで、シミュレートされたスティックの位置を設定します。

パラメーター
* x - スティックの水平位置。
* y スティックの垂直位置。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**

取得またはシミュレートされたコント ローラーのバッテリ レベルを設定します。  値は 0.0 より大きくする必要があります、100.0 以下。


### <a name="microsoftperceptionsimulationisimulatedeyes"></a>Microsoft.PerceptionSimulation.ISimulatedEyes

シミュレートされた人間の目を記述するインターフェイスします。

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**

シミュレートされた目の回転角度を取得します。 軸に検索するときに、正のラジアンは右回りに回転します。

**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**

現在、回転の基準としたシミュレートされた目を回転します。 軸に検索するときに、正のラジアンは右回りに回転します。

パラメーター
* 回転の回転する量。

**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**

取得またはシミュレートされた目の調整状態を設定します。

**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**

メートル単位で、世界中とに関してノードの位置を取得します。


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

再生を停止し、先頭に位置をリセットします。

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>Microsoft.PerceptionSimulation.ISimulationRecordingCallback

再生中に状態の変更を受信するためのインターフェイスします。

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**

ISimulationRecording の再生の状態が変更されたときに呼び出されます。

パラメーター
* newState の記録の新しい状態。

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.PerceptionSimulationManager

Perception シミュレーション オブジェクトを作成するためのルート オブジェクト。

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
* シンクしますで生成されたすべてのパケットを受信するシンク。

戻り値

作成したマネージャー。

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**

指定したパスにあるファイルのすべての受信パケットを格納するシンクを作成します。

パラメーター
* パス - 作成するファイルのパス。

戻り値

作成したシンク。

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**

指定したファイルから録画を読み込みます。

パラメーター
* パス - 読み込むファイルのパス。
* 工場出荷時のために必要なときに、ISimulationStreamSink を作成するため、記録することによって使用されるファクトリ。

戻り値

読み込まれた記録します。

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory、Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**

指定したファイルから録画を読み込みます。

パラメーター
* パス - 読み込むファイルのパス。
* 工場出荷時のために必要なときに、ISimulationStreamSink を作成するため、記録することによって使用されるファクトリ。
* callback - コールバックを受信は、regrading 記録の状態を更新します。

戻り値

読み込まれた記録します。

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>Microsoft.PerceptionSimulation.StreamDataTypes

ストリーム データのさまざまな種類をについて説明します。

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

ストリームのデータ型がない場合に使用される sentinel 値。

**Microsoft.PerceptionSimulation.StreamDataTypes.Head**

Stream の位置と、先頭の向きに関するデータ。

**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**

Stream の位置と手のジェスチャに関するデータ。

**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**

Stream の環境の空間のマッピングに関するデータ。

**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**

デバイスの調整に関するデータの Stream。 調整のパケットは、リモート モードでのシステムでのみ受け入れられます。

**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**

デバイスの環境に関するデータの Stream。

**Microsoft.PerceptionSimulation.StreamDataTypes.All**

すべて記録されたデータ型を示すために使用される sentinel 値。

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>Microsoft.PerceptionSimulation.ISimulationStreamSink

シミュレーションのストリームからデータ パケットを受信するオブジェクト。

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived (uint の長さ、byte パケット)**

内部的に型指定されたおよびバージョン管理は、1 つのパケットを受信します。

パラメーター
* length - パケットの長さ。
* パケットのパケットのデータです。

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory

ISimulationStreamSink を作成するオブジェクト。

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**

ISimulationStreamSink の 1 つのインスタンスを作成します。

戻り値

作成したシンク。
