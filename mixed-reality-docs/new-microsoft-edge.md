---
title: Windows Mixed Reality と新しい Microsoft Edge
description: Windows Mixed Reality の新しい Microsoft Edge の準備をします。 予想される変更、検索対象の更新、および既知の問題が含まれます。
author: mattzmsft
ms.author: mazeller
ms.date: 01/15/2020
ms.topic: article
keywords: edge、新規、イマーシブ web、microsoft edge、browser、vr
ms.openlocfilehash: 2576762786c9234377308f226036c830e01d9133
ms.sourcegitcommit: d73d9012941fa1b13eb7d2f45ccc481d6365827a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76885622"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Windows Mixed Reality と新しい Microsoft Edge

[新しい Microsoft Edge をダウンロードできるようになりました](https://blogs.windows.com/windowsexperience/?p=173496)が、今後数か月の間に測定されたロールアウトアプローチに従って、 [Windows 10 の今後の更新プログラムにインストールされるのを待つ](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/)こともできます。 

この記事では、 **Windows Mixed reality のヘッドセットのお客様に、新しい Microsoft Edge から期待されることを知らせ、Windows Mixed reality での web 閲覧エクスペリエンスを向上させる保留中の更新**について通知します。

## <a name="introducing-the-new-microsoft-edge"></a>新しい Microsoft Edge の紹介

新しい Microsoft Edge は、 [Chromium のオープンソースプロジェクト](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/)をデスクトップ上に採用しているため、より優れた web 互換性をユーザーに提供し、すべての web 開発者が web の断片化を減らすことができます。 また、WebVR の代わりに、VR ヘッドセット用のイマーシブ web エクスペリエンスを作成するための新しい標準である WebXR at launch もサポートします。

>[!IMPORTANT]
>Microsoft Edge を最新の Windows 10 デバイスにインストールすると、PC 上の以前の (レガシ) バージョンが置き換えられます。

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
-   **360 Viewer 拡張機能のバージョン 2.3.8**: Windows Mixed Reality で YouTube から360ビデオを開くと、ヘッドセットでビデオがゆがんでしまう可能性があります。 Edge を再起動して、この問題を解決するには、360 Viewer 拡張機能を非表示にする必要があります。 アドレスバーに `edge://system/` を入力し、[拡張機能] の横にある**展開**ボタンを選択すると、使用している拡張機能のバージョンを確認できます。
-   Windows Mixed Reality セッション中に、設定 の > システム > 表示に汎用物理モニターとして表示されます。



