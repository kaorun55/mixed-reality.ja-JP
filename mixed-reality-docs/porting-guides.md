---
title: 移植ガイド
description: 既存のイマーシブアプリケーションを Windows Mixed Reality に移植する手順を説明したチュートリアルです。
author: JBrentJ
ms.author: alexturn
ms.date: 07/07/2020
ms.topic: article
keywords: ポート、移植、unity、ミドルウェア、エンジン、UWP、Win32
ms.openlocfilehash: ed6c613c8aa3649cffb42d08dbb18661f06b9a53
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476934"
---
# <a name="porting-guides"></a>移植ガイド

## <a name="overview"></a>概要

Windows 10 には、イマーシブおよび holographic ヘッドセットの直接サポートが含まれています。 Oculus Rift や HTC Naopak など、他のデバイス用にコンテンツを構築した場合は、オペレーティングシステムのプラットフォーム API の上に存在するライブラリに依存関係があります。 既存の Win32 Unity VR アプリを Windows Mixed Reality に導入するには、ベンダー固有の VR Sdk を Unity のクロスベンダ VR Api に再ターゲット使用する必要があります。


## <a name="porting-overview"></a>移植の概要

大まかに言えば、既存のコンテンツの移植には次の手順が関係します。
1. **PC で Windows 10 の秋の作成者の更新プログラム (16299) が実行されていることを確認します。** 内部からのプレビュービルドを受信することはお勧めできなくなりました。これらのビルドは、mixed reality 開発では最も安定していないためです。
2. **グラフィックスまたはゲームエンジンの最新バージョンにアップグレードします。** ゲームエンジンは、Windows 10 SDK バージョン 10.0.15063.0 (2017 年4月にリリース) 以降をサポートする必要があります。
3. **任意のミドルウェア、プラグイン、またはコンポーネントをアップグレードします。** アプリにコンポーネントが含まれている場合は、最新バージョンにアップグレードすることをお勧めします。
4. **重複する sdk の依存関係を削除**します。 コンテンツがターゲットとしているデバイスによっては、その SDK を削除するか条件付きでコンパイルする必要があります (たとえば、SteamVR)。そのため、代わりに Windows Api を対象にすることができます。
5. **ビルドの問題を解決します。** この時点で、移植の演習は、アプリ、エンジン、およびコンポーネントの依存関係に固有です。

## <a name="common-porting-steps"></a>一般的な移植手順

### <a name="common-step-1-make-sure-you-have-the-right-development-hardware"></a>一般的な手順 1: 適切な開発ハードウェアがあることを確認する

[[ツールのインストール](install-the-tools.md#immersive-vr-headset-requirements)] ページに、推奨される開発ハードウェアの一覧が表示されます。

### <a name="common-step-2-upgrade-to-the-latest-flight-of-windows-10"></a>一般的な手順 2: Windows 10 の最新のフライトにアップグレードする

Windows Mixed Reality プラットフォームは、まだアクティブな開発中です。 "Windows Insider Fast" のフライトにアクセスするには[、Windows Insider program に参加](https://insider.windows.com/)することをお勧めします。
1. Windows 10 の作成者の[更新プログラム](https://www.microsoft.com/software-download/windows10)をインストールする
2. Windows Insider プログラムに[参加](https://insider.windows.com/)します。
3. [開発者モード](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)を有効にする
4. [**設定 > 更新 & セキュリティ] セクション**で、 [Windows Insider Fast のフライト](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview)に切り替えます。

### <a name="common-step-3-upgrade-to-the-most-recent-build-of-visual-studio"></a>一般的な手順 3: Visual Studio の最新のビルドにアップグレードする
* Visual Studio を使用している場合は、最新のビルドにアップグレードします。
* 「Visual Studio 2019 で[のツールページのインストール」を](install-the-tools.md#installation-checklist)参照してください。

### <a name="common-step-4-choose-the-correct-adapter"></a>一般的な手順 4: 正しいアダプターを選択する
* 2つの Gpu を持つ notebook などのシステムでは、[正しいアダプターをターゲット](rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications)にします。 これは、Unity とネイティブ DirectX アプリに適用されます。 ID3D11Device は、明示的に、または暗黙的に (メディアファンデーション) 機能に対して作成されます。

## <a name="unity-porting-guidance"></a>Unity の移植に関するガイダンス

### <a name="unity-step-1-review-the-common-porting-steps-listed-above"></a>Unity 手順 1: 上記の一般的な移植手順を確認する

開発環境が正しく設定されていることを確認するために、上記の一般的な手順を確認してください。 Visual Studio を使用している場合は、手順 #3 で、[ **Unity を使用したゲーム開発**] ワークロードを選択する必要があります。 次の手順で新しいバージョンの Unity をインストールするため、"Unity エディターオプション" コンポーネントの選択を解除できます。

### <a name="unity-step-2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>Unity 手順 2: Windows MR サポートを使用して Unity の最新のパブリックビルドにアップグレードする
1. Mixed reality サポートを使用して、 [Unity の最新の推奨パブリックビルド](install-the-tools.md)をダウンロードします。
2. 作業を開始する前にプロジェクトのコピーを保存する
3. 以前のバージョンの Unity でプロジェクトがビルドされている場合は、アップグレード時に Unity から入手できる[ドキュメント](https://docs.unity3d.com/Manual/UpgradeGuides.html)を確認してください。
4. Unity のサイトで自動 API アップデーターを使用する[手順](https://docs.unity3d.com/Manual/APIUpdater.html)に従います。
5. プロジェクトを実行するために必要な追加の変更があるかどうかを確認し、残りのエラーと警告を解決します。 

> [!Note] 
> 依存しているミドルウェアがある場合は、最新のリリースを使用していることを確認してください (以下の手順 3. の詳細)。

### <a name="unity-step-3-upgrade-your-middleware-to-the-latest-versions"></a>Unity 手順 3: ミドルウェアを最新バージョンにアップグレードする

Unity の更新プログラムでは、ゲームまたはアプリケーションが依存している1つ以上のミドルウェアパッケージを更新することが必要になる可能性があります。 さらに、最新のミドルウェアで最新の状態になると、移植プロセスの残りの部分全体で成功の可能性が高まります。

### <a name="unity-step-4-target-your-application-to-run-on-win32"></a>Unity 手順 4: Win32 で実行するようにアプリケーションをターゲットにする

Unity アプリケーション内から:

* ファイル > のビルド設定に移動します
* [PC、Mac、Linux スタンドアロン] を選択します。
* ターゲットプラットフォームを "Windows" に設定します
* アーキテクチャを "x86" に設定し、[プラットフォームの切り替え] を選択します。

> [!NOTE] 
> アプリケーションがデバイス固有のサービスに依存している場合 (ストリームからの照合など)、この手順で無効にする必要があります。 後で Windows が提供する同等のサービスにフックできます。

### <a name="unity-step-5-setup-your-windows-mixed-reality-hardware"></a>Unity 手順 5: Windows Mixed Reality ハードウェアをセットアップする
1. [イマーシブヘッドセットのセットアップ](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)の手順を確認する
2. [Windows Mixed reality シミュレーターを使用する](using-the-windows-mixed-reality-simulator.md)方法と[windows mixed Reality ホームを移動](navigating-the-windows-mixed-reality-home.md)する方法について説明します。

### <a name="unity-step-6-target-your-application-to-run-on-windows-mixed-reality"></a>Unity 手順 6: Windows Mixed Reality で実行するようにアプリケーションをターゲットにする
1. まず、特定の VR SDK に固有の他のライブラリサポートを削除するか、条件に応じてコンパイルする必要があります。 これらの資産は、Windows Mixed Reality などの他の VR Sdk と互換性のない方法でプロジェクトの設定とプロパティを頻繁に変更します。
    * たとえば、プロジェクトが SteamVR SDK を参照している場合は、代わりに、Windows Mixed Reality と SteamVR の両方をサポートする Unity の一般的な VR Api を使用するようにプロジェクトを更新する必要があります。
    * 条件付きで他の VR Sdk を除外するための具体的な手順は近日対応予定です。
2. Unity プロジェクトで、 [Windows 10 SDK を対象とする](holograms-100.md#target-windows-10-sdk)
3. シーンごとに、[カメラを設定します](holograms-100.md#chapter-2---setup-the-camera)。

### <a name="unity-step-7-use-the-stage-to-place-content-on-the-floor"></a>Unity 手順 7: ステージを使用して、床にコンテンツを配置する

さまざまな[エクスペリエンススケール](coordinate-systems.md)にわたって、混合した現実のエクスペリエンスを構築できます。

取り付けられている**スケールエクスペリエンス**を移植する場合は、Unity が**固定**の追跡領域の種類に設定されていることを確認する必要があります。

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

上記のコードでは、Unity のワールド座標系を設定して、[参照の静止フレーム](coordinate-systems.md#spatial-coordinate-systems)を追跡します。 静止の追跡モードでは、アプリの起動時に、カメラの既定の場所 (フォワードが Z) の前にエディターに配置されたコンテンツがユーザーの前に表示されます。 ユーザーが recenter した元の位置を確認するには、Unity の XR を呼び出すことができ[ます。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)メソッド。

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

スクリプトコードでは、TrackedArea の境界の種類を指定して、境界ポリゴンを取得するために、XR 型の TryGetGeometry メソッドを呼び出すことができます。 ユーザーが境界を定義している場合 (頂点の一覧を取得した場合)、ユーザーに**ルームスケールエクスペリエンス**を提供し、ユーザーが作成したシーンを周囲にたどることができます。

ユーザーがこの境界に近づいたときに、境界が自動的に表示されます。 アプリでは、境界自体をレンダリングするためにこの多角形を使用する必要はありません。

詳細については、「 [Unity の座標系](coordinate-systems-in-unity.md)」ページを参照してください。

一部のアプリケーションでは、四角形を使用して相互作用を制限しています。 多くのものを持つ四角形を取得することは、UWP API または Unity で直接サポートされるわけではありません。 次にリンクされているコード例では、トレースされた境界内で四角形を検索する方法を示しています。 これはヒューリスティックベースであるため、最適なソリューションを見つけることができない場合がありますが、結果は期待どおりであると考えられます。 アルゴリズムのパラメーターをチューニングして、処理時間のコストでより正確な結果を見つけることができます。 このアルゴリズムは、Unity の 5.6 preview MRTP バージョンを使用する Mixed Reality Toolkit のフォークに含まれています。 これは公開されていません。 このコードは、2017.2 以降のバージョンの Unity で直接使用できます。 このコードは、近い将来、現在の MRTK に移植されます。

[GitHub のコードの zip ファイル](https://github.com/KevinKennedy/MixedRealityToolkit-Unity/releases/tag/5.6.MRTP20)重要なファイル:
* Assets/HoloToolkit/Stage/Scripts/StageManager-使用例
* Assets/HoloToolkit/Stage/Scripts/LargestRectangle-アルゴリズムの実装
* Assets/HoloToolkit-UnitTests/Editor/Stage/LargestRectangleTest-アルゴリズムの簡易テスト

結果の例:

![結果の例](images/largestrectangle-400px.jpg)

アルゴリズムは、Daniel Smilkov: [polygon 内の最大の四角形](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)によるブログに基づいています

### <a name="unity-step-8-work-through-your-input-model"></a>Unity 手順 8: 入力モデルを処理する

既存の HMD を対象とする各ゲームまたはアプリケーションには、処理する入力のセット、エクスペリエンスに必要な入力の種類、およびそれらの入力を取得するために呼び出す特定の Api が含まれます。 Windows Mixed Reality で利用可能な入力を活用するために、可能な限りシンプルで単純なものにするために投資してきました。
1. 詳細については、「 **[Unity の入力移植ガイド」](input-porting-guide-for-unity.md)** を参照してください。これは、Windows Mixed Reality が入力を公開する方法と、その方法がアプリケーションにどのように対応しているかについて詳しく説明します。
2. Unity のクロス VR SDK 入力 API または MR 固有の入力 API を活用するかどうかを選択します。 [Oculus 入力](https://docs.unity3d.com/Manual/OculusControllers.html)と[openvr 入力](https://docs.unity3d.com/Manual/OpenVRControllers.html)については、現在 Unity VR apps で使用されているのは、GetAxis api です。 アプリが既にモーションコントローラー用のこれらの Api を使用している場合は、これが最も簡単なパスです。入力マネージャーでボタンと軸を再マップするだけで済みます。
    * Unity のモーションコントローラーデータにアクセスするには、一般的な GetAxis Api または MR 固有の UnityEngine. XR Api を使用します (複数の場合があります)。 (以前は Unity 5.6 の UnityEngine. XR 名前空間にあります)
    * ゲームパッドとモーションコントローラーを組み合わせた[ツールキットの例](https://github.com/Microsoft/HoloToolkit-Unity/pull/572)を参照してください。

### <a name="unity-step-9-performance-testing-and-tuning"></a>Unity 手順 9: パフォーマンステストとチューニング

Windows Mixed Reality は、ハイエンドゲーム Pc から広範な市場メインストリーム Pc まで、さまざまな種類のデバイスで利用できます。 対象となる市場によっては、アプリケーションに対して使用可能なコンピューティングとグラフィックの予算に大きな違いがあります。 この移植の演習では、premium PC を利用している可能性があります。また、アプリで使用できるコンピューティングとグラフィックの大きな予算があります。 アプリをより広範囲のユーザーが使用できるようにする場合は、[対象とする代表的なハードウェア](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)でアプリをテストしてプロファイリングする必要があります。

[Unity](https://docs.unity3d.com/Manual/Profiler.html)と[Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index)のどちらにも、パフォーマンスプロファイラーと、パフォーマンスプロファイルと最適化に関する[Microsoft](understanding-performance-for-mixed-reality.md)と[Intel](https://software.intel.com/articles/vr-content-developer-guide)の両方の発行ガイドラインが含まれています。 [混合現実のパフォーマンスを理解](understanding-performance-for-mixed-reality.md)することで、パフォーマンスに関する広範な説明があります。 さらに、unity の[パフォーマンスに関する推奨事項](performance-recommendations-for-unity.md)には、unity に関する具体的な詳細があります。

## <a name="see-also"></a>こちらもご覧ください
* [Unity 用入力移植ガイド](input-porting-guide-for-unity.md)
* [Windows Mixed Reality の PC ハードウェアの最小互換性ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Mixed Reality のパフォーマンスについて](understanding-performance-for-mixed-reality.md)
* [Unity のパフォーマンスに関する推奨事項](performance-recommendations-for-unity.md)
