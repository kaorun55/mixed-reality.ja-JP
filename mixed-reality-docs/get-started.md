---
title: 作業開始
description: このガイドでは、mixed reality 開発を最大限に活用するための最も簡単な方法について説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 08/06/2018
ms.topic: article
keywords: はじめに、基本、HoloLens、イマーシブヘッドセット、ar、vr、unity、visual studio、クイックスタート、方法
ms.openlocfilehash: 4277de37ffe4a7ab03f382626452b96bf9157634
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873958"
---
# <a name="get-started"></a>作業開始

Mixed reality 開発の世界へようこそ! MR を初めてご利用の場合、このガイドはできるだけ早く稼働させることができます。 開発用に PC をセットアップし、デバイスを準備し、MR 開発プロセスを高速化するツールをインストールすることができます。 

## <a name="intro-to-mixed-reality"></a>Mixed reality の概要

"Mixed reality" によって何を意味するか、およびそれが拡張現実 (AR) と仮想現実 (VR) とどのように関連しているかについて、いくつかの質問があるかもしれません。 簡潔に言えば、混合現実とは、世界的な世界とデジタルの世界を合わせたものです。これは、実際の世界では、デジタルコンテンツが現実の世界に配置され、実質的にはほぼ完全にデジタルで置き換えられます。 

![HoloLens とイマーシブ (VR) ヘッドセットの両方をサポートする mixed reality アプリの例](images/mr-island.png)<br>
*Mixed reality アプリでは、HoloLens とイマーシブ (VR) ヘッドセットの両方をサポートできます。*

Windows Mixed Reality を1つの開発プラットフォームとして、MR スペクトルに対応できるツールのセットとして作成しました。現在、同じ範囲をカバーする2種類のデバイスをサポートしています。[Microsoft HoloLens](https://www.microsoft.com/hololens)は、世界初の自己完結型の holographic ヘッドセットであり、 [Windows Mixed reality のイマーシブヘッドセットとモーションコントローラー](https://www.microsoft.com/windows/windows-mixed-reality)で、強力な仮想現実エクスペリエンスを実現するために PC に接続します。 [Mixed reality] を確認できます。(詳細については、「」を参照してください。

## <a name="choose-your-development-path"></a>開発パスの選択

Mixed reality アプリを開発する最も簡単な方法は、ゲーム開発によく使用される強力で人気のあるミドルウェアツールである[Unity](https://unity3d.com)を使用することです。 カスタムエンジンを使用する場合は、 [DirectX に対してビルド](directx-development-overview.md)することもできますが、ほとんどの MR 開発者は、ゲームやアプリに Unity を使用します。 Unity を使用すると、HoloLens、イマーシブ (VR) ヘッドホン、またはその両方を対象とする mixed reality アプリを作成できます。

## <a name="prepare-your-pc-and-devices-for-development"></a>開発用に PC とデバイスを準備する

HoloLens、イマーシブ (VR) ヘッドホン、またはその両方を対象とする mixed reality アプリを構築している場合でも、一般的なツールと Api のセットを使用します。 また、お客様の PC が、開発を行うために十分な性能を備えていることを確認します。 

>[!NOTE]
>開発用 PC の仕様、各ソフトウェアツールのサポートされているバージョン、および関連する設定や構成に関する注意事項については、「[ツールのインストール](install-the-tools.md)」を参照してください。 以下のツールをインストールする前に、この記事を確認してください。

インストールするツール:
* [Unity](https://store.unity.com/download)
* [Visual Studio (Windows 10 SDK を使用)](https://developer.microsoft.com/windows/downloads)
* [Unity 用 Mixed Reality ツールキット](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)

また、[ターゲットデバイスを開発者モードにし、アプリをターゲットデバイスにデプロイするように Visual Studio を構成](using-visual-studio.md)することもできます。

### <a name="a-note-about-the-mixed-reality-toolkit-for-unity"></a>Mixed Reality Toolkit for Unity に関する注意事項

![Unity の MRTK](images/mrtkandunity.png)<br>

***具体化さんは、MRTK-UNITY が非常に優れていて、それがどのようなものであるのかを誰かに伝えて:) います。***

Mixed Reality Toolkit は、Microsoft HoloLens および Windows Mixed Reality ヘッドセットを対象とするアプリケーションの開発を促進するためのスクリプトとコンポーネントのコレクションです。 このプロジェクトは、Mixed Reality アプリケーション作成への参入の障壁を減らし、私たち全員の成長とともにコミュニティに貢献することを目的としています。

## <a name="start-your-first-mr-project"></a>最初の MR プロジェクトを開始する

PC とデバイスが設定されたので、Unity で最初の mixed reality プロジェクトを作成する準備ができました。 Mr の最初の mr academy コース、 [mr 基本100に従ってください。Unity](holograms-100.md)を使ってみると、複合現実のヘッドセットでキューブを作成し、実行することになります。

![Mixed reality Unity プロジェクトのキューブのスクリーンショット](images/mr-cube.PNG)<br>
*Unity の最初の mixed reality プロジェクト。*

## <a name="learn-more-and-get-help"></a>詳細情報とヘルプの表示

最初の MR プロジェクトが正常に作成されたので、もっと多くのことをお勧めします。 次のリソースを参考にしてください。
* [Mixed reality 開発者向けドキュメント](mixed-reality.md)-既にお持ちですが、技術ドキュメント、設計ガイダンス、サンプルプロジェクト、ケーススタディなど、さらに多くのことを確認できます。
* [Mixed reality チュートリアル](tutorials.md)-プロジェクトの設定、core mr 構成ブロックの実装、mr アプリへの Azure cloud services の統合に関するすべての情報を網羅したチュートリアルに従ってください。
* [Unity について説明](https://unity3d.com/learn)します。 unity の web サイトでは、学習のすべての段階で作成者のためのチュートリアル、プロジェクト、ライブトレーニングセッションを提供しています。

また、次のような優れたコミュニティリソースから支援を受けることもできます。
* [Mixed reality 開発](https://forums.hololens.com/)者向けフォーラム-mixed reality 開発者向けの公式フォーラムです。 Microsoft から直接寄せられた MR 開発ニュースである質問に回答したり、回答したりすることができます。
* [HoloDevelopers の余裕期間チャネル](https://holodevelopersslack.azurewebsites.net/)-最も堅牢かつ機知の外部混合の現実固有の開発者チャネル。ここでは、開発者を参考にしてください。
* [Unity フォーラム](https://forum.unity3d.com/)-unity の公式フォーラム。
