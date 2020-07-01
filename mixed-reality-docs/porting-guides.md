---
title: 移植ガイド
description: 既存のイマーシブアプリケーションを Windows Mixed Reality に移植する方法を説明するステップバイステップチュートリアル。
author: chimerascorn
ms.author: alexturn
ms.date: 10/02/2018
ms.topic: article
keywords: ポート、移植、unity、ミドルウェア、エンジン、UWP
ms.openlocfilehash: 73126ae90ed12988177cc9192b7db41bae30fcc2
ms.sourcegitcommit: f523b74a549721b6bec69cb5d2eca5b7673a793c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/30/2020
ms.locfileid: "85570318"
---
# <a name="porting-guides"></a>移植ガイド

Windows 10 では、イマーシブおよび holographic ヘッドセットが直接サポートされています。 Oculus Rift や HTC Naopak などの別のデバイス用にコンテンツを構築している場合は、オペレーティングシステムのプラットフォーム API の上に存在するライブラリに依存関係があります。 既存のコンテンツを Windows Mixed Reality に取り込むには、これらの他の Sdk を Windows Api に再ターゲット使用する必要があります。 [Mixed reality の Windows プラットフォーム api](https://docs.microsoft.com/uwp/api/Windows.Perception)は、ユニバーサル WINDOWS プラットフォーム (UWP) アプリモデルでのみ機能します。 そのため、アプリが UWP 用にまだビルドされていない場合は、UWP への移植が移植エクスペリエンスの一部になります。

## <a name="porting-overview"></a>移植の概要

大まかに言えば、既存のコンテンツの移植には次の手順が必要です。
1. **PC で Windows 10 の秋の作成者の更新プログラム (16299) が実行されていることを確認します。** 内部からのプレビュービルドを受信することはお勧めできなくなりました。これらのビルドは、mixed reality 開発では最も安定していないためです。
2. **グラフィックスまたはゲームエンジンの最新バージョンにアップグレードします。** ゲームエンジンは、Windows 10 SDK バージョン 10.0.15063.0 (2017 年4月にリリース) 以降をサポートする必要があります。
3. **任意のミドルウェア、プラグイン、またはコンポーネントをアップグレードします。** アプリにコンポーネントが含まれている場合は、最新バージョンにアップグレードすることをお勧めします。 最も一般的なプラグインの新しいバージョンでは、UWP がサポートされています。
4. **重複する sdk の依存関係を削除**します。 コンテンツがターゲットとしているデバイスによっては、その SDK (SteamVR など) を削除するか条件付きでコンパイルして、代わりに Windows Api を対象にする必要があります。
5. **ビルドの問題を解決します。** この時点で、移植の演習は、アプリ、エンジン、およびコンポーネントの依存関係に固有です。

## <a name="common-porting-steps"></a>一般的な移植手順

### <a name="common-step-1-make-sure-you-have-the-right-development-hardware"></a>一般的な手順 1: 適切な開発ハードウェアがあることを確認する

[[ツールのインストール](install-the-tools.md#for-immersive-vr-headset-development)] ページに、推奨される開発ハードウェアの一覧が表示されます。

### <a name="common-step-2-upgrade-to-the-latest-flight-of-windows-10"></a>一般的な手順 2: Windows 10 の最新のフライトにアップグレードする

Windows Mixed Reality プラットフォームは依然としてアクティブな開発中であり、最も効果的な方法として、"Windows Insider Fast" のフライトを使用することをお勧めします。 Windows のフライトにアクセスするには、 [Windows Insider program に参加](https://insider.windows.com/)する必要があります。
1. Windows 10 の作成者の[更新プログラム](https://www.microsoft.com/software-download/windows10)をインストールする
2. Windows Insider プログラムに[参加](https://insider.windows.com/)します。
3. [開発者モード](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)を有効にする
4. 設定を使用して[Windows Insider Fast のフライト](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview)に切り替える--> Update & Security セクション

### <a name="common-step-3-upgrade-to-the-most-recent-build-of-visual-studio"></a>一般的な手順 3: Visual Studio の最新のビルドにアップグレードする
* Visual Studio 2019 の [ツール] ページ[のインストールに](install-the-tools.md#installation-checklist)関するページを参照してください。

### <a name="common-step-4-be-ready-for-the-store"></a>共通手順 4: ストアの準備ができている
* [Windows アプリ認定キット](https://developer.microsoft.com/windows/develop/app-certification-kit)(wack) を早期に頻繁に使用します。
* [移植性アナライザー](https://docs.microsoft.com/dotnet/standard/portability-analyzer) ([ダウンロード](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)) を使用する

### <a name="common-step-5-choose-the-correct-adapter"></a>一般的な手順 5: 正しいアダプターを選択する
* 2つの Gpu を持つ notebook などのシステムでは、[正しいアダプターをターゲット](rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications)にします。 これは、ネイティブの DirectX アプリに加えて、ID3D11Device がその機能に対して明示的または暗黙的 (メディアファンデーション) に作成される場合にも、Unity アプリに適用されます。

## <a name="unity-porting-guidance"></a>Unity の移植に関するガイダンス

### <a name="unity-step-1-follow-the-common-porting-steps"></a>Unity 手順 1: 一般的な移植手順に従う

すべての一般的な手順を実行します。 手順 #3 で、[ **Unity を使用したゲーム開発**] ワークロードを選択します。 以下の手順から新しいバージョンの Unity をインストールするため、Unity エディターのオプションコンポーネントを選択解除することができます。

### <a name="unity-step-2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>Unity 手順 2: Windows MR サポートを使用して Unity の最新のパブリックビルドにアップグレードする
1. Mixed reality サポートを使用して、 [Unity の最新の推奨パブリックビルド](install-the-tools.md)をダウンロードします。
2. 作業を開始する前にプロジェクトのコピーを保存する
3. 移植時に Unity から入手できる[ドキュメント](https://docs.unity3d.com/Manual/UpgradeGuides.html)を確認します。
4. Unity のサイトで自動 API アップデーターを使用する[手順](https://docs.unity3d.com/Manual/APIUpdater.html)に従います。
5. プロジェクトを実行するために必要な追加の変更があるかどうかを確認し、残りのエラーと警告を解決します。 注: 依存しているミドルウェアがある場合は、そのミドルウェアを更新して実行する必要があります (以下の手順3の詳細については、こちらを参照してください)。

### <a name="unity-step-3-upgrade-your-middleware-to-the-latest-versions"></a>Unity 手順 3: ミドルウェアを最新バージョンにアップグレードする

Unity の更新プログラムでは、ゲームまたはアプリケーションが依存している1つ以上のミドルウェアパッケージを更新することが必要になる可能性があります。 また、すべてのミドルウェアの最新バージョンを使用すると、移植プロセスの残りの部分を通じて成功の可能性が高まります。 最近、多くのミドルウェアパッケージでユニバーサル Windows プラットフォーム (UWP) のサポートが追加され、最新バージョンにアップグレードすると、その作業を利用できるようになります。

### <a name="unity-step-4-target-your-application-to-run-on-universal-windows-platform-uwp"></a>Unity 手順 4: ユニバーサル Windows プラットフォーム (UWP) で実行するようにアプリケーションをターゲットにする

ツールをインストールしたら、アプリをユニバーサル Windows アプリとして実行する必要があります。

* Unity によって提供される[詳細な手順に](https://unity3d.com/partners/microsoft/porting-guides)従ってください。 Windows MR の最新の LTS リリース (すべての20xx リリース) をご確認ください。
* UWP 開発リソースの詳細については、「 [Windows 10 ゲーム開発ガイド」](https://docs.microsoft.com/windows/uwp/gaming/e2e)を参照してください。
* Unity は引き続き IL2CPP サポートを強化することに注意してください。IL2CPP を使用すると、いくつかの UWP ポートが非常に簡単になります。 .NET scripting バックエンドを現在対象としている場合は、代わりに IL2CPP バックエンドを活用するように変換することを検討してください。

注: アプリケーションがデバイス固有のサービス (ストリームからの一致など) に依存している場合は、この手順で無効にする必要があります。 後で、Windows が提供する同等のサービスにフックすることができます。

### <a name="unity-step-5-deprecated"></a>Unity 手順 5: (非推奨)

手順 5. は不要になりました。 ここでは、ステップのインデックス作成が変わらないようにします。

### <a name="unity-step-6-get-your-windows-mixed-reality-hardware-set-up"></a>Unity 手順 6: Windows Mixed Reality ハードウェアの設定を取得する
1. [イマーシブヘッドセットのセットアップ](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)の手順を確認する
2. [Windows Mixed reality シミュレーターを使用する](using-the-windows-mixed-reality-simulator.md)方法と[windows mixed Reality ホームを移動](navigating-the-windows-mixed-reality-home.md)する方法について説明します。

### <a name="unity-step-7-target-your-application-to-run-on-windows-mixed-reality"></a>Unity 手順 7: Windows Mixed Reality で実行するようにアプリケーションをターゲットにする
1. まず、特定の VR SDK に固有の他のライブラリサポートを削除するか、条件に応じてコンパイルする必要があります。 これらの資産は、Windows Mixed Reality などの他の VR Sdk と互換性のない方法でプロジェクトの設定とプロパティを頻繁に変更します。
    * たとえば、プロジェクトが SteamVR SDK を参照している場合は、Windows ストアビルドターゲットのエクスポート時に、プロジェクトを更新して、prefabs と script API 呼び出しを除外する必要があります。
    * 条件付きで他の VR Sdk を除外するための具体的な手順は近日対応予定です。
2. Unity プロジェクトで、 [Windows 10 SDK を対象とする](holograms-100.md#target-windows-10-sdk)
3. シーンごとに、[カメラを設定します](holograms-100.md#chapter-2---setup-the-camera)。

### <a name="unity-step-8-use-the-stage-to-place-content-on-the-floor"></a>Unity 手順 8: ステージを使用して、床にコンテンツを配置する

さまざまな[エクスペリエンススケール](coordinate-systems.md)にわたって、混合した現実のエクスペリエンスを構築できます。

取り付けられている**スケールエクスペリエンス**を移植する場合は、Unity が**固定**の追跡領域の種類に設定されていることを確認する必要があります。

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

これにより、Unity のワールド座標系が、[参照の静止フレーム](coordinate-systems.md#spatial-coordinate-systems)を追跡するように設定されます。 静止の追跡モードでは、アプリの起動時に、カメラの既定の場所 (前方が Z) の直前にあるエディターに配置されたコンテンツがユーザーの前に表示されます。 ユーザーが recenter した元の位置を確認するには、Unity の XR を呼び出すことができ[ます。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)メソッド。

継続的な**スケールエクスペリエンス**または**ルームスケールエクスペリエンス**を移植している場合は、フロアを基準にコンテンツを配置します。 ユーザーが定義したフロアレベルのオリジンとオプションの部屋の境界を表す**[空間ステージ](coordinate-systems.md#spatial-coordinate-systems)** を使用して、ユーザーのフロアについては、最初の実行時に設定します。 これらのエクスペリエンスについては、Unity が**RoomScale**の追跡領域の種類に設定されていることを確認する必要があります。 RoomScale が既定値であるのに対し、明示的に設定して、ユーザーが自分のコンピューターを調整した部屋から離れた状況を検出するために、true に戻すことをお勧めします。

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

アプリで RoomScale の追跡領域の種類が正常に設定されると、y = 0 平面に配置されたコンテンツがフロア上に表示されます。 (0, 0, 0) の原点は、部屋のセットアップ中にユーザーがそこしたフロア上の特定の場所になります。これは、セットアップ中に接続されていた前方方向を表す-Z です。

スクリプトコードでは、TrackedArea の境界の種類を指定して、境界ポリゴンを取得するために、XR 型の TryGetGeometry メソッドを呼び出すことができます。 ユーザーが境界を定義している場合 (頂点の一覧を取得した場合)、ユーザーに**ルームスケールエクスペリエンス**を提供するのが安全であることがわかっています。ユーザーは、作成したシーンを周囲に移動できます。

ユーザーが境界を操作すると、境界が自動的に表示されることに注意してください。 アプリでは、境界自体をレンダリングするためにこの多角形を使用する必要はありません。

詳細については、「 [Unity の座標系](coordinate-systems-in-unity.md)」ページを参照してください。

一部のアプリケーションでは、四角形を使用して相互作用を制限しています。 多くのものを持つ四角形を取得することは、UWP API または Unity で直接サポートされるわけではありません。 次にリンクされているコード例では、トレースされた境界内で四角形を検索する方法を示しています。 これはヒューリスティックベースであるため、最適なソリューションを見つけることができません。ただし、結果は通常、期待どおりに一致します。 アルゴリズムのパラメーターをチューニングして、処理時間のコストでより正確な結果を見つけることができます。 このアルゴリズムは、Unity の 5.6 preview MRTP バージョンを使用する Mixed Reality Toolkit のフォークに含まれています。 これはパブリックではありません。 このコードは、2017.2 以降のバージョンの Unity で直接使用できます。 このコードは、近い将来、現在の MRTK に移植されます。

[GitHub のコードの zip ファイル](https://github.com/KevinKennedy/MixedRealityToolkit-Unity/releases/tag/5.6.MRTP20)重要なファイル:
* Assets/HoloToolkit/Stage/Scripts/StageManager-使用例
* Assets/HoloToolkit/Stage/Scripts/LargestRectangle-アルゴリズムの実装
* Assets/HoloToolkit-UnitTests/Editor/Stage/LargestRectangleTest-アルゴリズムの簡易テスト

結果の例:

![結果の例](images/largestrectangle-400px.jpg)

アルゴリズムは、Daniel Smilkov: [polygon 内の最大の四角形](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)によるブログに基づいています

### <a name="unity-step-9-work-through-your-input-model"></a>Unity 手順 9: 入力モデルを操作する

既存の HMD を対象とする各ゲームまたはアプリケーションには、処理する入力のセット、エクスペリエンスに必要な入力の種類、およびそれらの入力を取得するために呼び出す特定の Api が含まれます。 Windows Mixed Reality で利用可能な入力を活用するために、可能な限りシンプルで単純なものにするために投資してきました。
1. 詳細については、「 **[Unity の入力移植ガイド」](input-porting-guide-for-unity.md)** を参照してください。これは、Windows Mixed Reality が入力を公開する方法と、その方法がアプリケーションにどのように対応しているかについて詳しく説明します。
2. Unity のクロス VR SDK 入力 API または MR 固有の入力 API を活用するかどうかを選択します。 [Oculus 入力](https://docs.unity3d.com/Manual/OculusControllers.html)と[openvr 入力](https://docs.unity3d.com/Manual/OpenVRControllers.html)については、現在 Unity VR apps で使用されているのは、GetAxis api です。 アプリが既にモーションコントローラー用のこれらの Api を使用している場合は、これが最も簡単なパスです。入力マネージャーでボタンと軸を再マップするだけで済みます。
    * Unity のモーションコントローラーデータにアクセスするには、一般的な GetAxis Api または MR 固有の UnityEngine. XR Api を使用します (複数の場合があります)。 (以前は Unity 5.6 の UnityEngine. XR 名前空間にあります)
    * ゲームパッドとモーションコントローラーを組み合わせた[ツールキットの例](https://github.com/Microsoft/HoloToolkit-Unity/pull/572)を参照してください。

### <a name="unity-step-10-performance-testing-and-tuning"></a>Unity 手順 10: パフォーマンステストとチューニング

Windows Mixed Reality は、ハイエンドゲーム Pc から広範な市場メインストリーム Pc まで、さまざまな種類のデバイスで利用できます。 対象となる市場によっては、アプリケーションに対して使用可能なコンピューティングとグラフィックの予算に大きな違いがあります。 この移植の演習では、premium PC を利用している可能性があります。また、アプリで使用できるコンピューティングとグラフィックの大きな予算があります。 アプリをより広範囲のユーザーが使用できるようにする場合は、[対象とする代表的なハードウェア](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)でアプリをテストしてプロファイリングする必要があります。

[Unity](https://docs.unity3d.com/Manual/Profiler.html)と[Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index)のどちらにも、パフォーマンスプロファイラーと、パフォーマンスプロファイルと最適化に関する[Microsoft](understanding-performance-for-mixed-reality.md)と[Intel](https://software.intel.com/articles/vr-content-developer-guide)の両方の発行ガイドラインが含まれています。 [混合現実のパフォーマンスを理解](understanding-performance-for-mixed-reality.md)することで、パフォーマンスの詳細な説明があります。 さらに、unity の[パフォーマンスに関する推奨事項](performance-recommendations-for-unity.md)には、unity に関する具体的な詳細があります。

## <a name="see-also"></a>関連項目
* [Unity 用入力移植ガイド](input-porting-guide-for-unity.md)
* [Windows Mixed Reality の PC ハードウェアの最小互換性ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Mixed Reality のパフォーマンスについて](understanding-performance-for-mixed-reality.md)
* [Unity のパフォーマンスに関する推奨事項](performance-recommendations-for-unity.md)
* [UWP のために Xbox Live サポートを Unity に追加する](https://docs.microsoft.com/windows/uwp/xbox-live/get-started-with-partner/partner-add-xbox-live-to-unity-uwp)
