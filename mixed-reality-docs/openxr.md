---
title: OpenXR
description: Provisional OpenXR 0.90 API Mixed Reality OpenXR Developer Preview を試してください。
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

OpenXR は無償のオープン標準[Khronos](https://www.khronos.org/)全体にわたる多くのベンダーからさまざまなデバイスにネイティブなアクセスを提供する、[複合現実スペクトル](mixed-reality.md)します。

OpenXR では、実際に存在した場合と同じ、現実の世界でデジタル コンテンツを配置する (HoloLens 2) などの holographic デバイスと非表示にする (デスクトップ Pc の Windows Mixed Reality ヘッドセット) などの没入型のデバイスの両方を対象とするアプリケーションを構築できます、現実の世界とデジタル エクスペリエンスに置き換えます。  OpenXR では、これが、移植可能なさまざまなハードウェア プラットフォーム間でコードを記述することができます。

OpenXR 標準は、一時的な段階では、現在のフィードバック向けにリリースされた最初の OpenXR 0.90 仕様には。  OpenXR へのアクセスなどの詳細については、 [provisional 0.90 仕様](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)と[ヘッダー](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)を参照してください、 [Khronos OpenXR ページ](https://www.khronos.org/openxr/)します。 

HoloLens 2 または Mixed Reality OpenXR Developer Preview を使用してデスクトップ PC で provisional OpenXR 0.90 API を試すことができます。  この初期のランタイム HoloLens 2 またはデスクトップ上の Windows Mixed Reality イマーシブ ヘッドセットを対象に OpenXR 0.90 API を対象とするアプリケーションで実行できます。

ヘッドセットへのアクセスを持っていない場合は、HoloLens 2 エミュレーターまたは Windows Mixed Reality シミュレーター代わりに使用します。

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-hololens-2"></a>HoloLens 2 Mixed Reality OpenXR Developer Preview のセットアップ

HoloLens 2 の現実の混合 OpenXR Developer Preview の概要。

1. HoloLens 2 を設定または指示に従って、 [HoloLens 2 エミュレーターをインストール](using-the-hololens-emulator.md)します。
1. デバイスまたはエミュレーター内からのストア アプリを起動し、すべてのアプリが更新されることを確認します。  これにより、そのデバイス上のアプリで使用するため、混在現実 OpenXR Developer Preview がインストールされます。  Emulator を使用する場合を参照してくださいたい、[エミュレーターが命令を入力](using-the-hololens-emulator.md#basic-emulator-input)エミュレーター内でストア アプリを使用できるようにします。

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-immersive-desktop-headsets"></a>没入型のデスクトップ ヘッドセットの Mixed Reality OpenXR Developer Preview のセットアップ

デスクトップ PC に実際の混合 OpenXR Developer Preview の概要。

1. Windows を実行しているかどうかを必ず 10 年 2018年 10 月 Update (1809) または Windows 10 は 2019 更新 (1903)。  月 2019年をアップグレードすることができる場合、以前のバージョンの Windows 10 の場合は、更新を使用して、 [Windows 10 更新プログラムのアシスタント](https://www.microsoft.com/en-us/software-download/windows10)します。
1. Windows Mixed Reality ヘッドセットを設定または指示に従って、 [Windows Mixed Reality シミュレーターを有効にする](using-the-windows-mixed-reality-simulator.md)します。
1. インストール、 [Mixed Reality OpenXR 開発者がアプリをプレビュー](https://www.microsoft.com/store/productId/9n5cvvl23qbt)します。  このアプリの取得を設定するプレビュー OpenXR ランタイムと windows 10 年 2018年 10 月 Update (1809) またはそれ以降。  このアプリをインストールした後、Windows ストアは、ランタイムに保ちます。
1. [スタート] メニューから Mixed Reality OpenXR 開発者プレビュー アプリを実行し、ランタイムがアクティブにする指示に従います。  すぐに、このアプリを調べることができますもその他の OpenXR デバッグ情報。

![Mixed Reality OpenXR 開発者がアプリをプレビュー](images/mixed-reality-openxr-developer-preview.png)

### <a name="support-for-windows-10-october-2018-update"></a>Windows 10 年 2018年 10 月の更新プログラムのサポート

Windows を実行している場合、10 月 2019年 (1903) を更新し、上記の手順を実行、Mixed Reality OpenXR Developer Preview を使用する準備ができます。

準備ができていない場合[デスクトップ PC に月 2019年アップグレード Update](https://www.microsoft.com/en-us/software-download/windows10)、windows のするつもりは 10 年 2018年 10 月は、1 つのステップに従って (1809) を更新します。

1. Mixed Reality OpenXR Developer Preview をインストールする前の手順に従います。
1. システムのアクティブな OpenXR ランタイムとしては、Mixed Reality OpenXR Developer Preview を設定するには、インストール、 [Mixed Reality OpenXR 開発者プレビュー互換機能パック](https://aka.ms/openxr-compat)します。

## <a name="building-a-sample-openxr-app"></a>サンプルの OpenXR アプリの構築

[BasicXrApp](https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp)プロジェクトは、両方 Win32 デスクトップ アプリのいずれかと、HoloLens 2 の UWP アプリ用に 1 つ、2 つの Visual Studio プロジェクト ファイルで簡単な OpenXR サンプルを示します。  ソリューションには、HoloLens の UWP プロジェクトが含まれています、する必要があります、[ユニバーサル Windows プラットフォーム開発ワークロード](install-the-tools.md#installation-checklist)を完全に開き、Visual Studio にインストールします。

Win32 および UWP プロジェクト ファイルは別のパッケージ化と配置、各プロジェクト内のアプリ コードの違いにより 100% 同じであることに注意してください。

## <a name="feedback"></a>Feedback

に関するフィードバックを提供する、 [OpenXR 一時的な 0.90 仕様](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)を参照してください、 [Khronos OpenXR フォーラム](https://community.khronos.org/c/openxr)、 [#openxr を Slack チャネル](https://khr.io/slack)と[仕様問題追跡ツール](https://github.com/KhronosGroup/OpenXR-Docs/issues)します。

## <a name="troubleshooting"></a>トラブルシューティング

ここでは、Mixed Reality OpenXR Developer Preview のトラブルシューティングのヒントです。  その他の問題が発生する場合を参照してください、 [Khronos OpenXR フォーラム](https://community.khronos.org/c/openxr)または[#openxr を Slack チャネル](https://khr.io/slack)します。

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>Windows Mixed Reality を起動しない OpenXR アプリ

OpenXR アプリは、実行するときに、Windows Mixed Reality を起動しないが、Mixed Reality OpenXR Developer Preview は、アクティブなランタイムとして設定できません。  Mixed Reality OpenXR 開発者プレビュー アプリを実行し、指示に従って、ランタイムがアクティブにしてください。

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a>Mixed Reality OpenXR 開発者プレビュー アプリをインストールすることはできません。 

必ず、実行している、少なくとも、Windows 10 年 2018年 10 月の更新 (1809)。  以前のバージョンの Windows 10 の場合は場合、は、2019年 5 月にアップグレードすることができます (1903) を使用して更新、 [Windows 10 更新プログラムのアシスタント](https://www.microsoft.com/en-us/software-download/windows10)します。

Mixed Reality OpenXR Developer Preview アプリのボタンでは、インストールは Windows では何も 10 年 2018年 10 月更新場合、アプリの古いシステムの要件が、システムによってキャッシュします。  コマンドを実行する`wsreset.exe`キャッシュをクリアするコマンド プロンプトからです。

## <a name="see-also"></a>関連項目

* [詳細については、OpenXR](https://www.khronos.org/openxr/)
* [OpenXR 一時的な 0.90 仕様](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [OpenXR 一時的な 0.90 API リファレンス](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [OpenXR 一時的な 0.90 ヘッダー](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
* [OpenXR 一時的な 0.90 クイック リファレンス ガイド](https://www.khronos.org/registry/OpenXR/specs/0.90/refguide/OpenXR-0.90-web.pdf)
