---
title: OpenXR トラブルシューティング
description: OpenXR アプリケーションの問題をトラブルシューティングします。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、ネイティブ、ネイティブアプリ、カスタムエンジン、ミドルウェア、トラブルシューティング
ms.openlocfilehash: 269982596ed6162d9c2f1ec999a446bcecd6ba2a
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83228007"
---
# <a name="openxr-troubleshooting"></a>OpenXR トラブルシューティング

Windows Mixed Reality OpenXR Runtime を使用して OpenXR アプリを開発する際のトラブルシューティングのヒントを次に示します。  <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 の仕様</a>に関して他に質問がある場合は、 <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR フォーラム</a>または<a href="https://khr.io/slack" target="_blank">余裕期間 #openxr チャネル</a>にアクセスしてください。

>[!NOTE]
>X86 アプリでの現在の Windows Mixed Reality OpenXR ランタイムには既知の問題があります。  現時点では、x64 用のデスクトップ OpenXR アプリを構築する必要があります。

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>OpenXR app が Windows Mixed Reality を開始しない

実行時に OpenXR アプリが Windows Mixed Reality を起動していない場合は、Windows Mixed Reality OpenXR ランタイムがアクティブなランタイムとして設定されていない可能性があります。  前の手順に従って、 [Windows Mixed Reality ヘッドセットの OpenXR を使用](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets)してランタイムをアクティブにしてください。

また、 [Windows Mixed Reality OpenXR 開発者ツール](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools)を実行して、システム上の Windows Mixed Reality OpenXR ランタイムの状態に関する追加のトラブルシューティングを行うこともできます。

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a>Mixed Reality ポータルに [OpenXR の設定] メニュー項目が表示されない

少なくとも Windows 10 10 月2018更新プログラム (1809) を実行していることを確認してください。  以前のバージョンの Windows 10 を使用している場合は、 [windows 10 Update Assistant](https://www.microsoft.com//software-download/windows10)を使用して、2019年5月の更新プログラム (1903) にアップグレードすることができます。

以前のバージョンの Mixed Reality ポータルアプリを使用している場合は、[OpenXR の設定] メニュー項目を使用できないことがあります。  [Mixed Reality ポータルアプリの更新プログラム](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m)を確認して、最新バージョンがあることを確認します。

Windows Mixed Reality OpenXR Runtime が既にインストールされ、アクティブになっている場合は、[OpenXR の設定] メニュー項目が表示されないことに注意してください。  [Windows Mixed Reality OpenXR 開発者ツール](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools)をインストールして、システム上の OpenXR ランタイムの現在の状態を確認できます。