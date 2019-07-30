---
title: OpenXR
description: ポータブル OpenXR API 標準を使用してエンジンをビルドし、Windows Mixed Reality と HoloLens 2 ヘッドセットに展開します。
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、Mixed Reality OpenXR 開発者ポータル、DirectX、ネイティブ、ネイティブアプリカスタムエンジン、ミドルウェア
ms.openlocfilehash: 057d01527163f2ffcfe10d2e105592f07ff9e9e2
ms.sourcegitcommit: 23e172664c2ee1220fe3b4468c104b37ef3ceda9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/29/2019
ms.locfileid: "68601600"
---
# <a name="openxr"></a>OpenXR

OpenXR は、 [Khronos](https://www.khronos.org/)のオープンなロイヤリティフリー API 標準です。これにより、さまざまなベンダーの幅広いデバイスにエンジンがネイティブでアクセスできるようになり、[混合現実](mixed-reality.md)の範囲を超えています。

デスクトップ上の HoloLens 2 または Windows Mixed Reality の OpenXR を使用して開発することができます。  ヘッドセットへのアクセス権がない場合は、代わりに HoloLens 2 エミュレーターまたは Windows Mixed Reality シミュレーターを使用できます。

## <a name="why-openxr"></a>OpenXR の理由

OpenXR を使用すると、holographic デバイス (HoloLens 2 など) の両方を対象とするエンジンを構築できます。これにより、実際の世界にデジタルコンテンツを配置し、イマーシブデバイス (デスクトップ Pc 用の Windows Mixed Reality ヘッドセットなど) を物理的に隠すことができます。それをデジタル体験に置き換えることができます。  OpenXR を使用すると、さまざまなハードウェアプラットフォームで移植可能なコードを一度記述できます。

OpenXR API は、アプリケーションをヘッドセットのネイティブプラットフォームサポートに直接接続するローダーを使用します。  これにより、エンドユーザーは、Windows Mixed Reality ヘッドセットとその他のヘッドセットのどちらを使用しているかにかかわらず、最大のパフォーマンスと最小待機時間を実現できます。

## <a name="what-is-openxr"></a>OpenXR とは

Core OpenXR 1.0 API は、HoloLens 2、Windows Mixed Reality ヘッドセットなどのイマーシブデバイスの両方を対象とするエンジンを構築するために必要な基本機能を提供します。
* システム + セッション
* 参照スペース (view、local、stage)
* 構成の表示 (mono、ステレオ)
* スワップチェーン + フレームのタイミング
* コンポジションレイヤー
* Input および haptics
* グラフィックス API + プラットフォーム統合

OpenXR API の詳細については、 [OpenXR 1.0 仕様](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html)と[OpenXR 1.0 api リファレンス](https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/)をご覧ください。  詳細については、 [Khronos OpenXR のページ](https://www.khronos.org/openxr/)を参照してください。

HoloLens 2 の全機能セットを対象にするには、クロスベンダおよびベンダー固有の OpenXR 拡張機能を使用します。これにより、OpenXR 1.0 コア以外の追加機能が可能になります。これには、トレーラーによる追跡、視線追跡、空間マッピング、空間アンカーなどがあります。  今年後半に登場する拡張機能の詳細については、後の「[ロードマップ」セクション](openxr.md#roadmap)を参照してください。

OpenXR は、それ自体が mixed reality エンジンではないことに注意してください。  代わりに、OpenXR では、Unity や Unreal などのエンジンがポータブルコードを一度記述できるようになります。これにより、そのプラットフォームを構築したベンダーに関係なく、ユーザーの holographic またはイマーシブデバイスのネイティブプラットフォーム機能にアクセスできます。

## <a name="getting-started-with-openxr-for-hololens-2"></a>OpenXR for HoloLens 2 の概要

HoloLens 2 用の OpenXR アプリケーションの開発を開始するには:

1. HoloLens 2 をセットアップするか、「 [hololens 2 エミュレーターをインストール](using-the-hololens-emulator.md)するには」の手順に従います。
1. デバイスまたはエミュレーター内からストアアプリを起動し、すべてのアプリが更新されていることを確認します。  これにより、HoloLens の OpenXR ランタイムが OpenXR 1.0 に更新されます。  エミュレーターを使用する場合は、エミュレーターでのストアアプリの使用に役立つ[エミュレーターの入力手順](using-the-hololens-emulator.md#basic-emulator-input)を参照することをお勧めします。

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>OpenXR for Windows Mixed Reality ヘッドセットの概要

イマーシブ Windows Mixed Reality ヘッドセット用の OpenXR アプリケーションの開発を開始するには:

1. Windows 10 2019 更新プログラム (1903) を実行していることを確認してください。これは、Windows Mixed Reality エンドユーザーが OpenXR アプリケーションを実行するための最小要件です。  以前のバージョンの Windows 10 を使用している場合は、 [windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10)を使用して、2019年5月の更新プログラムにアップグレードできます。  PC を更新できない場合は、 [2018 年10月の更新プログラム (1809) を使用して OpenXR アプリを開発](openxr.md#developing-on-windows-10-october-2018-update)することもできますが、パフォーマンスが低下したり、その他の問題が発生する可能性があります。
1. Windows Mixed reality ヘッドセットを設定するか、指示に従って[Windows Mixed reality シミュレーターを有効](using-the-windows-mixed-reality-simulator.md)にします。
1. [Mixed Reality OpenXR 開発者ポータルアプリ](https://www.microsoft.com/store/productId/9n5cvvl23qbt)をインストールします。  このアプリをインストールすると、Mixed Reality OpenXR Runtime が自動的にインストールされます。  OpenXR ランタイムをインストールすると、Microsoft Store によってランタイムが最新の状態に保たれます。
1. [スタート] メニューから Mixed Reality OpenXR 開発者ポータルアプリを実行し、指示に従ってランタイムをアクティブにします。

![Mixed Reality OpenXR 開発者ポータルアプリ](images/mixed-reality-openxr-developer-portal.png)

> [!NOTE]
> Mixed reality OpenXR Runtime は、Mixed Reality ポータルアプリを通じて、すべての Windows Mixed Reality エンドユーザーが間もなく使用できるようになります。

## <a name="building-a-sample-openxr-app"></a>サンプル OpenXR アプリのビルド

[BasicXrApp](https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp)プロジェクトでは、2つの Visual Studio プロジェクトファイルを含む単純な OpenXR サンプルを示しています。1つは Win32 デスクトップアプリ用で、もう1つは UWP HoloLens 2 アプリ用です。  ソリューションには HoloLens UWP プロジェクトが含まれているため、Visual Studio にインストールされた[ユニバーサル Windows プラットフォームの開発ワークロード](install-the-tools.md#installation-checklist)を完全に開く必要があります。

Win32 と UWP のプロジェクトファイルは、パッケージ化と配置の違いによって分離されていますが、各プロジェクト内のアプリコード100は同じであることに注意してください。

## <a name="roadmap"></a>ロードマップ

OpenXR 仕様では、ランタイム実装者が[Base OpenXR 1.0 仕様](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html)で定義されている[コア機能](openxr.md#what-is-openxr)以外の機能を公開できるようにする拡張機構を定義しています。

OpenXR 拡張機能には、次の3種類があります。
* **ベンダ拡張機能 (例: MSFT):** ハードウェアまたはソフトウェアの機能でベンダーごとのイノベーションを実現します。  任意のランタイムベンダは、いつでもベンダ拡張機能を導入および出荷できます。
* **拡張機能:** 複数の企業が定義および実装するクロスベンダーの拡張機能。  関心のある企業のグループは、いつでも拡張機能を導入できます。
* **KHR 拡張機能:** Khronos の公式拡張機能は、コア仕様リリースの一部として批准されています。  KHR 拡張機能は、コア仕様自体と同じライセンスによってカバーされます。

今年の終わりまでに、Mixed Reality OpenXR ランタイムは、HoloLens 2 の機能の完全なセットを OpenXR アプリケーションに取り込む、MSFT と EXT の一連の拡張機能をサポートしています。
* [無制限の参照スペース (ワールドスケールエクスペリエンス)](coordinate-systems.md#building-a-world-scale-experience)
* [空間アンカー + ストレージ](spatial-anchors.md)
* [手 articulation + 手メッシュ](hands-and-tools.md)
* [目の視線入力](eye-tracking.md)
* [セカンダリビューの構成 (Mixed Reality キャプチャ)](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)
* [空間マッピング](spatial-mapping.md)
* Windows SDK Api との相互運用

これらの拡張機能の一部は、ベンダー固有の MSFT 拡張機能として開始される場合がありますが、Microsoft およびその他の OpenXR runtime ベンダーが連携して、これらの機能領域の多くについて、クロスベンダーの EXT または KHR 拡張機能を設計します。  これにより、コア仕様と同様に、これらの機能用に記述したコードをランタイムベンダー間で移植可能にすることができます。

## <a name="troubleshooting"></a>トラブルシューティング

Mixed Reality OpenXR Runtime のトラブルシューティングのヒントを次に示します。  [OpenXR 1.0 の仕様](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html)に関して他に質問がある場合は、 [Khronos OpenXR フォーラム](https://community.khronos.org/c/openxr)または[余裕期間 #openxr チャネル](https://khr.io/slack)にアクセスしてください。

### <a name="developing-on-windows-10-october-2018-update"></a>Windows 10 10 月2018更新プログラムの開発

開発用 PC を2019年5月[の更新プログラムにアップグレード](https://www.microsoft.com/en-us/software-download/windows10)できない場合は、もう1つの手順に従って、Windows 10 10 月2018更新プログラム (1809) PC を開発用にセットアップできます。

1. 上記の手順に従って、デスクトップ PC で OpenXR を開始します。
1. Mixed Reality OpenXR Runtime をシステムのアクティブ OpenXR ランタイムとして設定するには、 [Mixed Reality OpenXR Developer Compatibility Pack](https://aka.ms/openxr-compat)をインストールします。

> [!NOTE]
> OpenXR アプリケーションを開発するときに Windows 10 10 月2018更新プログラム (1809) を使用できますが、windows 10 月2019更新プログラム (1903) は、エンドユーザーが Windows Mixed Reality で OpenXR を使用するための最小要件となります。  2018年10月の更新で OpenXR アプリを実行すると、パフォーマンスやその他の問題が発生する可能性があります。  開発用 PC を Windows 10 5 月2019更新プログラム (1903) にアップグレードすることを強くお勧めします。

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>OpenXR app が Windows Mixed Reality を開始しない

実行時に OpenXR アプリが Windows Mixed Reality を起動していない場合、Mixed Reality OpenXR Runtime がアクティブなランタイムとして設定されていない可能性があります。  Mixed Reality OpenXR 開発者ポータルアプリを実行し、手順に従ってランタイムをアクティブにしてください。

### <a name="mixed-reality-openxr-developer-portal-app-cannot-be-installed"></a>Mixed Reality OpenXR 開発者ポータルアプリをインストールできません 

少なくとも Windows 10 10 月2018更新プログラム (1809) を実行していることを確認してください。  以前のバージョンの Windows 10 を使用している場合は、 [windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10)を使用して、2019年5月の更新プログラム (1903) にアップグレードすることができます。

Mixed Reality OpenXR 開発者ポータルアプリの [インストール] ボタンによって、2018年10月の更新プログラムに対して何も実行されない場合は、システムでアプリケーションの古いシステム要件がキャッシュされている可能性があります。  コマンドプロンプトからコマンド`wsreset.exe`を実行して、キャッシュをクリアすることができます。

## <a name="see-also"></a>関連項目

* [OpenXR の詳細情報](https://www.khronos.org/openxr/)
* [OpenXR 1.0 仕様](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html)
* [OpenXR 1.0 API リファレンス](https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/)
* [OpenXR 1.0 クイックリファレンスガイド](https://www.khronos.org/registry/OpenXR/specs/1.0/refguide/OpenXR-1.0-web.pdf)
