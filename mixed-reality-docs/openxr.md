---
title: OpenXR
description: Mixed Reality OpenXR Developer Preview を使用して、仮 OpenXR 0.90 API を試してみてください。
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: Mixed Reality OpenXR Developer Preview
ms.openlocfilehash: 723b0b85785d4b6dd735430aa76a24b9ce05b5c7
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039179"
---
# <a name="openxr"></a>OpenXR

OpenXR は、 [Khronos](https://www.khronos.org/)が提供するオープンなロイヤリティフリー標準であり、さまざまなベンダーの幅広いデバイスにネイティブでアクセスできるようにします。これは、[混合現実](mixed-reality.md)の範囲にまたがっています。

OpenXR を使用すると、holographic デバイス (HoloLens 2 など) の両方を対象とするアプリケーションを構築できます。これにより、実際の世界にデジタルコンテンツを配置したり、(デスクトップ Pc 用の Windows Mixed Reality ヘッドセットなどの) イマーシブデバイスを使用して、物理的な世界で、デジタル体験に置き換えてください。  OpenXR を使用すると、さまざまなハードウェアプラットフォームで移植可能なコードを一度記述できます。

現時点では、OpenXR 標準は、フィードバックのために最初の OpenXR 0.90 仕様がリリースされた一時的なフェーズになっています。  [仮0.90 の仕様](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)と[ヘッダー](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)へのアクセスなど、OpenXR の詳細については、 [Khronos OpenXR のページ](https://www.khronos.org/openxr/)を参照してください。 

HoloLens 2 またはデスクトップ PC で、Mixed Reality OpenXR Developer Preview を使用して、仮 OpenXR 0.90 API を試すことができます。  この初期のランタイムでは、OpenXR 0.90 API を対象とするアプリケーションは、デスクトップ上で HoloLens 2 または Windows Mixed Reality のイマーシブヘッドセットを対象にすることができます。

ヘッドセットへのアクセス権がない場合は、代わりに HoloLens 2 エミュレーターまたは Windows Mixed Reality シミュレーターを使用できます。

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-hololens-2"></a>HoloLens 2 用の Mixed Reality OpenXR Developer Preview の設定

HoloLens 2 で Mixed Reality OpenXR Developer Preview の使用を開始するには、次のようにします。

1. HoloLens 2 をセットアップするか、「 [hololens 2 エミュレーターをインストール](using-the-hololens-emulator.md)するには」の手順に従います。
1. デバイスまたはエミュレーター内からストアアプリを起動し、すべてのアプリが更新されていることを確認します。  これにより、混合 Reality OpenXR Developer Preview がインストールされ、そのデバイス上のアプリで使用できるようになります。  エミュレーターを使用する場合は、エミュレーターでのストアアプリの使用に役立つ[エミュレーターの入力手順](using-the-hololens-emulator.md#basic-emulator-input)を参照することをお勧めします。

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-immersive-desktop-headsets"></a>イマーシブデスクトップヘッドセット向けの Mixed Reality OpenXR Developer Preview の設定

デスクトップ PC で Mixed Reality OpenXR Developer Preview の使用を開始するには、次のようにします。

1. Windows 10 10 月2018更新プログラム (1809) または Windows 10 5 月2019更新プログラム (1903) を実行していることを確認してください。  以前のバージョンの Windows 10 を使用している場合は、 [windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10)を使用して、2019年5月の更新プログラムにアップグレードできます。
1. Windows Mixed reality ヘッドセットを設定するか、指示に従って[Windows Mixed reality シミュレーターを有効](using-the-windows-mixed-reality-simulator.md)にします。
1. [Mixed Reality OpenXR Developer Preview アプリ](https://www.microsoft.com/store/productId/9n5cvvl23qbt)をインストールします。  このアプリは、Windows 10 10 月2018更新プログラム (1809) 以降の preview OpenXR runtime を使用してセットアップします。  このアプリをインストールすると、Windows ストアによってランタイムが最新の状態に保たれます。
1. [スタート] メニューから Mixed Reality OpenXR Developer Preview アプリを実行し、指示に従ってランタイムをアクティブにします。  間もなく、このアプリで他の OpenXR デバッグ情報を調べることができます。

![Mixed Reality OpenXR Developer Preview アプリ](images/mixed-reality-openxr-developer-preview.png)

### <a name="support-for-windows-10-october-2018-update"></a>Windows 10 10 月2018更新プログラムのサポート

Windows 10 5 月2019更新プログラム (1903) を実行し、上記の手順に従っている場合は、Mixed Reality OpenXR Developer Preview を使用する準備ができています。

デスクトップ PC を2019年5月[の更新プログラムにアップグレード](https://www.microsoft.com/en-us/software-download/windows10)する準備ができていない場合は、もう1つの手順に従って、Windows 10 10 月2018更新プログラム (1809) に進むことができます。

1. 上記の手順に従って、Mixed Reality OpenXR Developer Preview をインストールします。
1. Mixed Reality OpenXR Developer Preview をシステムのアクティブな OpenXR ランタイムとして設定するには、 [Mixed Reality OpenXR Developer Preview 互換機能パック](https://aka.ms/openxr-compat)をインストールします。

## <a name="building-a-sample-openxr-app"></a>サンプル OpenXR アプリのビルド

[BasicXrApp](https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp)プロジェクトでは、2つの Visual Studio プロジェクトファイルを含む単純な OpenXR サンプルを示しています。1つは Win32 デスクトップアプリ用で、もう1つは UWP HoloLens 2 アプリ用です。  ソリューションには HoloLens UWP プロジェクトが含まれているため、Visual Studio にインストールされた[ユニバーサル Windows プラットフォームの開発ワークロード](install-the-tools.md#installation-checklist)を完全に開く必要があります。

Win32 と UWP のプロジェクトファイルは、パッケージ化と配置の違いによって分離されていますが、各プロジェクト内のアプリコード100は同じであることに注意してください。

## <a name="feedback"></a>フィードバック

[OpenXR の仮0.90 仕様](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)に関するフィードバックをお寄せいただくには、 [Khronos OpenXR フォーラム](https://community.khronos.org/c/openxr)、[余裕 #openxr チャネル](https://khr.io/slack)、および[仕様問題トラッカー](https://github.com/KhronosGroup/OpenXR-Docs/issues)に関するページを参照してください。

## <a name="troubleshooting"></a>トラブルシューティング

Mixed Reality OpenXR Developer Preview のトラブルシューティングのヒントを次に示します。  その他の問題が発生している場合は、 [Khronos OpenXR フォーラム](https://community.khronos.org/c/openxr)または[余裕期間 #openxr チャネル](https://khr.io/slack)にアクセスしてください。

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>OpenXR app が Windows Mixed Reality を開始しない

実行時に OpenXR アプリが Windows Mixed Reality を起動していない場合は、Mixed Reality OpenXR Developer Preview がアクティブなランタイムとして設定されていない可能性があります。  Mixed Reality OpenXR Developer Preview アプリを実行し、指示に従ってランタイムをアクティブにしてください。

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a>Mixed Reality OpenXR Developer Preview アプリをインストールできません 

少なくとも Windows 10 10 月2018更新プログラム (1809) を実行していることを確認してください。  以前のバージョンの Windows 10 を使用している場合は、 [windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10)を使用して、2019年5月の更新プログラム (1903) にアップグレードすることができます。

Mixed Reality OpenXR Developer Preview アプリの [インストール] ボタンが、2018年10月の更新プログラムでは何も実行しない場合、システムによって、アプリケーションの古いシステム要件がキャッシュされている可能性があります。  コマンドプロンプトからコマンド`wsreset.exe`を実行して、キャッシュをクリアすることができます。

## <a name="see-also"></a>関連項目

* [OpenXR の詳細情報](https://www.khronos.org/openxr/)
* [OpenXR の仮0.90 仕様](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [OpenXR の仮 0.90 API リファレンス](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [OpenXR の仮0.90 ヘッダー](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
* [OpenXR の暫定0.90 クイックリファレンスガイド](https://www.khronos.org/registry/OpenXR/specs/0.90/refguide/OpenXR-0.90-web.pdf)
