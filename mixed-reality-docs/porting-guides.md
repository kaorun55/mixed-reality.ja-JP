---
title: 移植ガイド
description: Windows Mixed Reality を既存の没入型アプリケーションを移植する方法を説明するステップ バイ ステップ チュートリアルです。
author: ChimeraScorn
ms.author: cwhite
ms.date: 10/02/2018
ms.topic: article
keywords: ポート、移植、unity、ミドルウェア、エンジンを UWP
ms.openlocfilehash: a4a8c78f1c45fd8e3b85a767d139bae9f67540e0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602181"
---
# <a name="porting-guides"></a>移植ガイド

> [!NOTE]
> HoloLens 2 に固有のガイダンスについて[近日](index.md#news-and-notes)します。

Windows 10 では、没入型および holographic ヘッドセットのサポートは直接含まれています。 オペレーティング システムのプラットフォーム API の上に存在するライブラリに依存関係を持つこれらのコンテンツを Oculus Rift や HTC Vive などの別のデバイスをビルドした場合。 Windows Mixed Reality を経由で既存のコンテンツを使えるようにするには、Windows Api にその他のこれらの Sdk の使用状況の再ターゲットする必要があります。 [複合現実の Windows プラットフォーム Api](https://docs.microsoft.com/uwp/api/Windows.Perception)ユニバーサル Windows プラットフォーム (UWP) アプリ モデルでのみ動作します。 したがって移植エクスペリエンスの一部が場合は、アプリは UWP の既には構築されずからになります UWP に移植します。

## <a name="porting-overview"></a>移植の概要

大まかに、これらは既存のコンテンツを移植するための手順です。
1. **お使いの PC には、Windows 10 Fall Creators Update (16299) が実行されていることを確認します。** 推奨されなく Insider スキップ先リングからビルドのプレビューを受け取るようにそれらのビルドを複合現実の開発で最も安定したことはできません。
2. **グラフィックスやゲーム エンジンの最新バージョンにアップグレードします。** ゲーム エンジンは、Windows 10 SDK バージョン 10.0.15063.0 (2017 年 4 月リリース) をサポートする必要がありますまたはそれ以降。
3. **すべてのミドルウェア、プラグインまたはコンポーネントをアップグレードします。** アプリに任意のコンポーネントが含まれている場合は、最新バージョンにアップグレードすることをお勧めします。 最も一般的なプラグインの新しいバージョンでは、UWP のサポートがあります。
4. **重複する Sdk の依存関係を削除**します。 コンテンツの対象デバイス、によっては、削除するか、その SDK (例: SteamVR) を条件付きでコンパイルする必要がありますので、Windows Api を代わりに対象にできます。
5. **ビルドの問題に取り組みます。** この時点では、移植の演習では、アプリ、エンジン、およびコンポーネントの依存関係がある場合に固有です。

## <a name="common-porting-steps"></a>移植の一般的な手順

### <a name="common-step-1-make-sure-you-have-the-right-development-hardware"></a>一般的な手順 1:適切な開発のハードウェアがあるかどうかを確認します。

[ツールをインストールする](install-the-tools.md#for-immersive-vr-headset-development)ページは、開発の推奨されるハードウェアを一覧表示されます。

### <a name="common-step-2-upgrade-to-the-latest-flight-of-windows-10"></a>一般的な手順 2:Windows 10 の最新のフライトへのアップグレードします。

Windows Mixed Reality プラットフォームは、まだアクティブの開発中に最も効果的なは、ためお勧めします"Windows Insider Fast"フライト中します。 Windows のフライトへのアクセスを確保するためにする必要があります[Windows Insider Program に参加](https://insider.windows.com/)します。
1. インストール、 [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)
2. [参加](https://insider.windows.com/)Windows Insider プログラム。
3. 有効にする[開発者モード](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
4. 切り替えて、 [Windows Insider Fast フライト](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview)設定を使用して、更新プログラムとセキュリティ セクション-->

### <a name="common-step-3-upgrade-to-the-most-recent-build-of-visual-studio"></a>一般的な手順 3:Visual Studio の最新のビルドにアップグレードします。
* 参照してください[ツールをインストールする](install-the-tools.md#installation-checklist)] ページ [Visual Studio 2017

### <a name="common-step-4-be-ready-for-the-store"></a>一般的な手順 4:ストアの準備が完了します。
* 使用[Windows アプリ認定キット](https://developer.microsoft.com/windows/develop/app-certification-kit)(WACK とも呼ばれます) 早い段階で多くの場合。
* 使用[Portability Analyzer](https://docs.microsoft.com/dotnet/standard/portability-analyzer) ([ダウンロード](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer))

### <a name="common-step-5-choose-the-correct-adapter"></a>一般的な手順 5:正しいアダプターを選択します。
* 2 つの Gpu と notebook のようなシステムで[正しいアダプターを対象](rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications)します。 これに適用されます、Unity アプリをさらに、ID3D11Device が作成される場所明示的または暗黙的にネイティブの DirectX アプリ (Media Foundation)、その機能。

## <a name="unity-porting-guidance"></a>Unity の移植のガイダンス

### <a name="unity-step-1-follow-the-common-porting-steps"></a>Unity の手順 1:一般的な移植の手順に従います

すべての一般的な手順に従います。 手順 3 で選択、 **Unity によるゲーム開発の**ワークロード。 以下の手順から Unity の新しいバージョンをインストールするしますので、Unity エディターのオプション コンポーネントの選択を解除することがあります。

### <a name="unity-step-2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>Unity の手順 2:Windows MR サポートと Unity の最新のパブリック ビルドへのアップグレードします。
1. 最新バージョンをダウンロード[Unity のパブリック ビルドの推奨](install-the-tools.md)複合現実をサポートします。
2. 開始する前に、プロジェクトのコピーを保存します。
3. レビュー、[ドキュメント](https://docs.unity3d.com/Manual/UpgradeGuides.html)移植の Unity から入手できます。
4. に従って、[指示](https://docs.unity3d.com/Manual/APIUpdater.html)自動の API の更新ツールを使用するための Unity のサイト
5. 確認しを実行しているプロジェクトを取得するために必要な追加の変更があるかどうかを参照してください、残りエラーと警告を使用します。 注:依存するミドルウェアをした場合は、(下の手順 3 で他の詳細) を開始するには、そのミドルウェアを更新する必要があります。

### <a name="unity-step-3-upgrade-your-middleware-to-the-latest-versions"></a>Unity の手順 3:ミドルウェアを最新バージョンにアップグレードします。

更新では、Unity、ゲームまたはアプリケーションが依存している 1 つまたは複数のミドルウェア パッケージを更新する必要がある可能性があります。 さらに、すべてのミドルウェアの最新バージョンで、移植プロセスの残りの部分で成功する可能性が向上します。 多くのミドルウェア パッケージは、ユニバーサル Windows プラットフォーム (UWP) のサポートを最近追加したし、最新のバージョンにアップグレードすると、その作業を活用することです。

### <a name="unity-step-4-target-your-application-to-run-on-universal-windows-platform-uwp"></a>Unity の手順 4:対象とするユニバーサル Windows プラットフォーム (UWP) でを実行するアプリケーション

ツールをインストールした後は、アプリをユニバーサル Windows アプリとして実行する必要があります。
* に従って、[詳しいステップ バイ ステップ チュートリアル](https://unity3d.com/partners/microsoft/porting-guides)Unity によって提供されます。 最新 LTS リリース (20xx.4 のリリース) の Windows MR で維持する必要があることに注意してください。
* その他の UWP 開発リソースを参照してください、 [Windows 10 ゲームの開発ガイド](https://docs.microsoft.com/windows/uwp/gaming/e2e)します。
* Unity の il2cpp バック エンドのサポートを強化し続けていることに注意してください。Il2cpp バック エンドは、いくつかの UWP ポート大幅に簡素化します。 場合は、.Net バックエンドのスクリプトを対象としている現在、代わりに、il2cpp バック エンドのバックエンドを利用する変換を検討してください。

注:アプリケーションにすべての依存関係がある場合は、ストリームから一致などの特定のサービス、デバイスでは、この手順で無効にする必要があります。 後では、Windows が提供する同等のサービスにフックすることができます。

### <a name="unity-step-5-deprecated"></a>Unity の手順 5:(非推奨)

手順 5 では、必要なくなりました。 私たち離職する人が、ここでは同じ手順のインデックスを作成できるようにします。

### <a name="unity-step-6-get-your-windows-mixed-reality-hardware-set-up"></a>Unity の手順 6:Windows Mixed Reality ハードウェア設定の取得します。
1. 確認手順[イマーシブ ヘッドセットのセットアップ](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)
2. について[Windows Mixed Reality シミュレーターを使用して](using-the-windows-mixed-reality-simulator.md)と[Windows Mixed Reality ホームに移動します。](navigating-the-windows-mixed-reality-home.md)

### <a name="unity-step-7-target-your-application-to-run-on-windows-mixed-reality"></a>Unity の手順 7:対象とするアプリケーションを Windows Mixed Reality を実行するには
1. 最初に、削除するか、特定 VR SDK ライブラリ サポートを条件付きでコンパイルする必要があります。 これらの資産は、設定と Windows Mixed Reality などの他の VR Sdk と互換性のない方法で、プロジェクトのプロパティを頻繁に変更します。
    * たとえば、SteamVR SDK をプロジェクトに参照する場合、Windows ストアのビルド ターゲットをエクスポートするときに、それらのプレハブとスクリプト API の呼び出しを除外するプロジェクトを更新する必要があります。
    * その他の VR Sdk を条件付きで除外するための特定の手順は近日公開予定。
2. Unity プロジェクトで、[対象 Windows 10 SDK](holograms-100.md#target-windows-10-sdk)
3. 各シーンの[カメラのセットアップ](holograms-100.md#chapter-2---setup-the-camera)

### <a name="unity-step-8-use-the-stage-to-place-content-on-the-floor"></a>Unity の手順 8:ステージを使用して、床の上のコンテンツを配置するには

複合現実エクスペリエンスをビルドするには幅広いの[スケールが発生する](coordinate-systems.md)します。

移植する場合、**取り付けられているスケールのエクスペリエンス**、Unity に設定されていることを確認する必要があります、**静止**領域の種類の追跡。

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

追跡するために Unity のワールド座標系を設定、[フレームの静止した基準](coordinate-systems.md#spatial-coordinate-systems)します。 カメラの既定の場所の前に、エディターで、静止した追跡モードでコンテンツが配置されます (フォワードは ~ Z)、アプリの起動時にも、ユーザーが表示されます。 配信元が、ユーザーを戻します取り付けられて、Unity の呼び出すことができます[XR します。InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)メソッド。

移植する場合、**継続スケール エクスペリエンス**または**ルーム スケール エクスペリエンス**コンテンツ、フロアの基準とした配置します。 ユーザーの理解を使用して floor、 **[空間ステージ](coordinate-systems.md#spatial-coordinate-systems)**、現場レベルの配信元と省略可能な領域の境界を表す、ユーザーの定義、初回実行時に設定します。 これらのエクスペリエンス向けに設定されている Unity を確認する必要があります、 **RoomScale**領域の種類を追跡します。 RoomScale 既定では、中に明示的に設定し、ユーザーが調整、部屋から自分のコンピューターを移動が、状況をキャッチする true に戻すを取得することを確認する必要があります。

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

アプリが正常に RoomScale の空間型で、y に、コンテンツの追跡を設定すると、0、床の上にプレーンが表示されますを = です。 原点 (0, 0, 0) は、特定の場所 - セットアップ時に直面していましたが、順方向を表す Z で部屋のセットアップ中に、ユーザー縦位置、床の上になります。

スクリプトのコードでできますを TryGetGeometry メソッドを呼び出している、境界の多角形を取得する UnityEngine.Experimental.XR.Boundary 型 TrackedArea の境界の種類を指定します。 ユーザーに (戻る頂点のリスト) の境界が定義されている場合、配信するには、安全ではわかって、**ルーム スケール エクスペリエンス**をユーザーに場所がシーンを中心ご説明を作成します。

エントリのユーザーがそれに近づくと、システムは境界がレンダリングに自動的に注意してください。 アプリは、それ自体の境界を表示するためにこの多角形を使用する必要はありません。

詳細については、次を参照してください。、 [Unity の座標系](coordinate-systems-in-unity.md)ページ。

一部のアプリケーションでは、その相関関係を制限するのに四角形を使用します。 囲む四角形の最大の取得は直接サポートされていません、UWP API または Unity でします。 コード例下記のリンクを示しますトレースの境界内の四角形を検索する方法。 ただし、結果が期待と一貫性のある一般的には、ヒューリスティックに基づいている最適なソリューションが見つからないことがあるためにです。 アルゴリズムのパラメーターを調整することで、処理時間がより正確な結果を検索します。 アルゴリズムは、MRTP バージョンの Unity 5.6 のプレビューを使用する混在現実ツールキットのフォークでは。 これは、市販されていません。 コードは、2017.2 以降のバージョンの Unity で直接使用する必要があります。 コードは、近い将来に現在 MRTK に移植されます。

[GitHub でコードの zip ファイル](https://github.com/KevinKennedy/MixedRealityToolkit-Unity/releases/tag/5.6.MRTP20)重要なファイル。
* Assets/HoloToolkit/Stage/Scripts/StageManager.cs - 使用方法の例
* Assets/HoloToolkit/Stage/Scripts/LargestRectangle.cs - アルゴリズムの実装
* Assets/HoloToolkit-UnitTests/Editor/Stage/LargestRectangleTest.cs - アルゴリズムの単純なテスト

結果の例:

![結果の例](images/largestrectangle-400px.jpg)

アルゴリズムは、Daniel Smilkov でブログに基づいています。[最も大きな四角形を多角形](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)

### <a name="unity-step-9-work-through-your-input-model"></a>Unity の手順 9:入力モデルを使用します。

各ゲームや既存のッドマウントを対象とするアプリケーションは、一連の動作は、必要な入力とこれらの入力を取得するために呼び出す特定の Api の種類は、処理する入力のがあります。 Windows Mixed Reality で使用可能な入力を活用するためにできる限り単純さにしようとでの投資を行いました。
1. 目を通してください、 **[移植 for Unity ガイド入力](input-porting-guide-for-unity.md)** Windows Mixed Reality 方法の詳細については、入力が公開して、今すぐ行うことができます、どのようなアプリケーションにマップされる方法です。
2. Unity のクロス-VR-SDK 入力 API を活用しようとするまたは、MR 固有 API を入力するかどうかを選択します。 今日の Unity VR アプリで使用する一般的な Input.GetButton/Input.GetAxis Api [Oculus 入力](https://docs.unity3d.com/Manual/OculusControllers.html)と[OpenVR 入力](https://docs.unity3d.com/Manual/OpenVRControllers.html)します。 既にアプリがモーションのコント ローラーのこれらの Api を使用して、これは、最も簡単なパスにボタンと Input Manager での軸を再マップする必要があるだけです。
    * いずれかの一般的なクロス-VR-SDK Input.GetButton/Input.GetAxis Api または MR 固有の UnityEngine.XR.WSA.Input Api を使用して Unity でのモーション コント ローラーのデータにアクセスすることができます。 (以前の Unity 5.6 で UnityEngine.XR.WSA.Input 名前空間)
    * 参照してください、 [toolkit の使用例](https://github.com/Microsoft/HoloToolkit-Unity/pull/572)ゲームパッド、モーションのコント ローラーを結合します。

### <a name="unity-step-10-performance-testing-and-tuning"></a>Unity 手順 10:パフォーマンス テストとチューニング

Windows Mixed Reality はデバイスの広範なクラスで使用できる、高の範囲 Pc のゲームを終了、広範な市場に Pc をメイン ストリームします。 どのような市場を対象としている、によって、アプリケーションの利用可能なコンピューティングおよびグラフィックスの予算に大きな違いは。 この移植の演習では、可能性が高い premium の PC を活用することをアプリに大きなコンピューティングおよびグラフィックス ・予算の利用があった。 テストし、でアプリをプロファイリングする必要がありますより広範な対象ユーザーにアプリを使用できるようにする場合は、[する代表的なハードウェア ターゲット](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)します。

両方[Unity](https://docs.unity3d.com/Manual/Profiler.html)と[Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index)パフォーマンス プロファイラーでは、両方は、 [Microsoft](understanding-performance-for-mixed-reality.md)と[Intel](https://software.intel.com/articles/vr-content-developer-guide)発行のガイドラインパフォーマンスのプロファイリングおよび最適化します。 パフォーマンスの詳細については、[パフォーマンスと for Mixed Reality](understanding-performance-for-mixed-reality.md)します。 さらに、Unity の詳細データがある[for Unity のパフォーマンスに関する推奨事項](performance-recommendations-for-unity.md)します。

## <a name="see-also"></a>関連項目
* [Unity のガイドの移植の入力](input-porting-guide-for-unity.md)
* [Windows Mixed Reality 最小 PC ハードウェアの互換性ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [複合現実のパフォーマンスを理解](understanding-performance-for-mixed-reality.md)
* [Unity のパフォーマンスに関する推奨事項](performance-recommendations-for-unity.md)
* [UWP の Unity に Xbox Live のサポートを追加します。](https://docs.microsoft.com/windows/uwp/xbox-live/get-started-with-partner/partner-add-xbox-live-to-unity-uwp)
