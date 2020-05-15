---
title: 1. はじめに
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用して簡単なチェス アプリをビルドするためのチュートリアルのパート 1
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, 入門, mrtk, uxt, UX ツール, ドキュメント
ms.openlocfilehash: 3ca47cfe7bb0a733932f3777cc8b531ef9df8e71
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840131"
---
# <a name="1-getting-started"></a>1.はじめに

このチュートリアルでは、Unreal Engine 4 を使用して、対話型の HoloLens 2 チェス アプリをビルドする方法をステップバイステップで説明します。 また、Unreal 向け Mixed Reality ツールキットの UX ツール プラグインを使用して、開発を高速化する方法についても説明します。 

## <a name="prerequisites"></a>前提条件

* Windows 10 1809 以降
* Windows 10 SDK 10.0.18362.0 以降
* Unreal Engine 4.25 以降
* [開発用に構成された](using-visual-studio.md#enabling-developer-mode) Microsoft HoloLens 2 デバイスまたはエミュレーター
* Visual Studio 2019 (以下のワークロードとコンポーネントを含む)

### <a name="installing-visual-studio-2019-workloads-and-components"></a>Visual Studio 2019、ワークロード、コンポーネントのインストール
1. 最新バージョンの Visual Studio 2019 のインストールまたは更新
* [Visual Studio 2019 をダウンロードする](https://visualstudio.microsoft.com/downloads/)
2. 次のワークロードをインストールします。
* C++ によるデスクトップ開発
* .NET デスクトップ開発
* ユニバーサル Windows プラットフォームの開発
3. 次の個々のコンポーネントをインストールします。
* コンパイラ、ビルド ツール、ランタイム > MSVC v142 - VS 2019 C++ ARM64 ビルド ツール (最新バージョン)

[次のセクション: 2.プロジェクトと最初のアプリケーションの初期化](unreal-uxt-ch2.md)