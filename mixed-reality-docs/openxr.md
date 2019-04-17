---
title: OpenXR
description: Provisional OpenXR 0.90 API Mixed Reality OpenXR Developer Preview を試してください。
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: Mixed Reality OpenXR Developer Preview
ms.openlocfilehash: 0d8debf5c12cb88aaba402145c6a597f761491ee
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603661"
---
# <a name="openxr"></a>OpenXR

OpenXR は無償のオープン標準[Khronos](https://www.khronos.org/)全体にわたる多くのベンダーからさまざまなデバイスにネイティブなアクセスを提供する、[複合現実スペクトル](mixed-reality.md)します。

OpenXR では、実際に存在した場合と同じ、現実の世界でデジタル コンテンツを配置する (HoloLens 2) などの holographic デバイスと非表示にする (デスクトップ Pc の Windows Mixed Reality ヘッドセット) などの没入型のデバイスの両方を対象とするアプリケーションを構築できます、現実の世界とデジタル エクスペリエンスに置き換えます。  OpenXR では、これが、移植可能なさまざまなハードウェア プラットフォーム間でコードを記述することができます。

OpenXR 標準は、一時的な段階では、現在のフィードバック向けにリリースされた最初の OpenXR 0.90 仕様には。  OpenXR へのアクセスなどの詳細については、 [provisional 0.90 仕様](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)と[ヘッダー](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)を参照してください、 [Khronos OpenXR ページ](https://www.khronos.org/openxr/)します。

## <a name="setting-up-the-mixed-reality-openxr-developer-preview"></a>Mixed Reality OpenXR Developer Preview のセットアップ

Mixed Reality OpenXR Developer Preview を使用して、一時的な OpenXR 0.90 API を試すことができます。  この初期のランタイム ターゲット Windows Mixed Reality イマーシブ ヘッドセットをデスクトップ上に OpenXR 0.90 API を対象とするアプリケーションで実行できます。  ヘッドセットへのアクセスを持っていない場合は、Windows Mixed Reality シミュレーターを代わりに使用することができます。

Mixed Reality OpenXR Developer Preview の概要。

1. 必ず、実行している、少なくとも、Windows 10 年 2018年 10 月の更新します。  以前のバージョンの Windows 10 の場合は場合、は、年 2018年 10 月にアップグレードすることができますを使用して更新、 [Windows 10 更新プログラムのアシスタント](https://www.microsoft.com/en-us/software-download/windows10)します。  冒険は気分を場合、インストールできます、 [Windows 10 Insider Preview ビルド](https://insider.windows.com)します。
1. Windows Mixed Reality ヘッドセットを設定または指示に従って、 [Windows Mixed Reality シミュレーターを有効にする](using-the-windows-mixed-reality-simulator.md)します。
1. インストール、 [Mixed Reality OpenXR 開発者がアプリをプレビュー](https://www.microsoft.com/store/productId/9n5cvvl23qbt)します。  このアプリが取得 windows preview OpenXR ランタイムをセットアップする 10 年 2018年 10 月の更新またはそれ以降。  このアプリをインストールした後、Windows ストアは、ランタイムに保ちます。
1. [スタート] メニューから Mixed Reality OpenXR 開発者プレビュー アプリを実行し、ランタイムがアクティブにする指示に従います。  すぐに、このアプリを調べることができますもその他の OpenXR デバッグ情報。

![Mixed Reality OpenXR 開発者がアプリをプレビュー](images/mixed-reality-openxr-developer-preview.png)

## <a name="support-for-windows-10-october-2018-update"></a>Windows 10 年 2018年 10 月の更新プログラムのサポート

Windows Mixed Reality OpenXR 開発者プレビューを開始する 10 年 2018年 10 月の更新 (Windows の現在のバージョン)、さらに、いくつかの手順に従う必要があります。

1. Mixed Reality OpenXR Developer Preview をインストールする前の手順に従います。
1. システムのアクティブな OpenXR ランタイムとしては、Mixed Reality OpenXR Developer Preview を設定するには、インストール、 [Mixed Reality OpenXR 開発者プレビュー互換機能パック](https://aka.ms/openxr-compat)します。

## <a name="building-a-test-openxr-app"></a>テスト OpenXR アプリの構築

[Hello_xr](https://github.com/KhronosGroup/OpenXR-SDK/tree/master/src/tests/hello_xr) OpenXR テスト アプリが API のさまざまな部分の使用を示します。  これらを利用できる[構築手順](https://github.com/KhronosGroup/OpenXR-SDK/blob/master/BUILDING.md)、テスト アプリと OpenXR ヘッダー自体の両方を構築します。

## <a name="feedback"></a>Feedback

に関するフィードバックを提供する、 [OpenXR 一時的な 0.90 仕様](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)を参照してください、 [Khronos OpenXR フォーラム](https://community.khronos.org/c/openxr)、 [#openxr を Slack チャネル](https://khr.io/slack)と[仕様問題追跡ツール](https://github.com/KhronosGroup/OpenXR-Docs/issues)します。

## <a name="troubleshooting"></a>トラブルシューティング

ここでは、Mixed Reality OpenXR Developer Preview のトラブルシューティングのヒントです。  その他の問題が発生する場合を参照してください、 [Khronos OpenXR フォーラム](https://community.khronos.org/c/openxr)または[#openxr を Slack チャネル](https://khr.io/slack)します。

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>Windows Mixed Reality を起動しない OpenXR アプリ

OpenXR アプリは、実行するときに、Windows Mixed Reality を起動しないが、Mixed Reality OpenXR Developer Preview は、アクティブなランタイムとして設定できません。  Mixed Reality OpenXR 開発者プレビュー アプリを実行し、指示に従って、ランタイムがアクティブにしてください。

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a>Mixed Reality OpenXR 開発者プレビュー アプリをインストールすることはできません。 

必ず、実行している、少なくとも、Windows 10 年 2018年 10 月の更新します。  以前のバージョンの Windows 10 の場合は場合、は、年 2018年 10 月にアップグレードすることができますを使用して更新、 [Windows 10 更新プログラムのアシスタント](https://www.microsoft.com/en-us/software-download/windows10)します。

Mixed Reality OpenXR Developer Preview アプリのボタンでは、インストールは Windows では何も 10 年 2018年 10 月更新場合、アプリの古いシステムの要件が、システムによってキャッシュします。  コマンドを実行する`wsreset.exe`キャッシュをクリアするコマンド プロンプトからです。

## <a name="see-also"></a>関連項目

* [詳細については、OpenXR](https://www.khronos.org/openxr/)
* [OpenXR 一時的な 0.90 仕様](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [OpenXR 一時的な 0.90 API リファレンス](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [OpenXR 一時的な 0.90 ヘッダー](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
