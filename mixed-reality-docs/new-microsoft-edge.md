---
title: Windows Mixed Reality と新しい Microsoft Edge
description: Windows Mixed Reality のドキュメントに投稿する方法。
author: mattzmsft
ms.author: mazeller
ms.date: 01/07/2020
ms.topic: article
keywords: edge、新規、イマーシブ web、microsoft edge、browser、vr
ms.openlocfilehash: cb0f96069ffaa8f7d40b64bae55ab2749f5f02c6
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75727049"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Windows Mixed Reality と新しい Microsoft Edge

ご存知かもしれませんが、[新しい Microsoft Edge は近日公開されてい](https://blogs.windows.com/windowsexperience/2019/11/04/introducing-the-new-microsoft-edge-and-bing/)ます。 2020年1月15日を対象とした一般提供では、Windows Mixed Reality VR ヘッドセットのお客様に、新しい Microsoft Edge からの期待内容を知らせ、Windows Mixed での web 閲覧エクスペリエンスを向上させる保留中の更新について通知します。実際.

## <a name="introducing-the-new-microsoft-edge"></a>新しい Microsoft Edge の紹介

新しい Microsoft Edge は、 [Chromium のオープンソースプロジェクト](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/)をデスクトップ上に採用しているため、より優れた web 互換性をユーザーに提供し、すべての web 開発者が web の断片化を減らすことができます。 また、WebVR の代わりに、VR ヘッドセット用のイマーシブ web エクスペリエンスを作成するための新しい標準である WebXR at launch もサポートします。

## <a name="getting-ready-for-the-new-microsoft-edge"></a>新しい Microsoft Edge の準備

Mixed reality ホームで新しい Microsoft Edge を使用する windows Mixed Reality VR ヘッドセットのお客様は、mixed reality ホームで**Win32 アプリケーション (新しい Microsoft edge など) をネイティブでサポートするために、windows 10 バージョン1903以降にアップグレード**する必要があります。 Windows Update を確認[するか、Windows 10 の最新バージョンを手動でインストールして](https://www.microsoft.com/en-us/software-download/windows10)ください。

混合現実のホームで Microsoft Edge エクスペリエンスを最大限に活用するために、windows **10 バージョン 1903 (またはそれ以降) の2020-01 累積的な更新プログラムが適用された新しい Microsoft edge の Windows Mixed reality 最適化の主要**な部分を待機することもお勧めします。これは、1月の最後まで Windows Update で利用可能になります。

>[!IMPORTANT]
>これらの更新を行う前に新しい Microsoft Edge をダウンロードすることを選択した場合は、Windows Mixed Reality でのその動作に関する既知の問題がいくつかあります (下記を参照してください)。

## <a name="known-issues"></a>既知の問題

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Windows 10 バージョン 1903 (またはそれ以降) の2020-01 累積更新プログラムによって解決された既知の問題

- 新しい Microsoft Edge を含む任意の Win32 アプリを起動すると、ヘッドセットの表示が短時間フリーズします。
- Microsoft Edge タイルは、Windows Mixed Reality の [スタート] メニューから消えます ("クラシックアプリ" フォルダーで見つけることができます)。
- 以前の Microsoft Edge からの Windows は、mixed reality ホームの周囲に配置されていますが、使用することはできません。 これらのウィンドウをアクティブ化しようとすると、デスクトップアプリ内で Edge が起動します。
- Mixed reality ホームでハイパーリンクを選択すると、mixed reality ホームではなく、デスクトップで web ブラウザーが起動します。
- Webvr ショーケースアプリは、WebVR がサポートされなくなっても、mixed reality ホームに存在します。
- キーボード起動とビジュアルの全般的な機能強化。

### <a name="additional-known-issues"></a>その他の既知の問題

-   Windows Mixed reality で開かれている web サイトは、Mixed reality ポータルが閉じたときに失われます。ただし、Microsoft Edge ウィンドウは、mixed reality ホームに配置された場所に残ります。
-   Microsoft Edge ウィンドウからのオーディオは spatialized ません。
-   Windows Mixed Reality で YouTube から360ビデオを開くと、ヘッドセットでビデオがゆがんでしまう可能性があります。 YouTube ビデオのページを更新し、360ビデオを再起動すると、問題が解決されます。
-   Windows Mixed Reality セッション中に、設定 の > システム > 表示に汎用物理モニターとして表示されます。



