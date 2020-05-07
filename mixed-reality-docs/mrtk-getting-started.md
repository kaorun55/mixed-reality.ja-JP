---
title: MRTK バージョン 2 の概要
description: MRTK の活用に関心がある開発初心者向け
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, テスト, Mixed Reality Toolkit, MRTK バージョン2, MRTK, ツール, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: fc9638f405604bed7c7531ace0977a88509e91b5
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2020
ms.locfileid: "74491107"
---
# <a name="getting-started-with-mrtk-v2"></a>MRTK v2 の概要

## <a name="mrtk-getting-started-guide"></a>MRTK 入門ガイド
MRTK V2 を使って作業を開始するうえでの詳細情報は、[MRTK の入門ガイド](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)を参照してください。

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Mixed Reality Toolkit (MRTK) とは
MRTK は、HoloLens が最初にリリースされて以来培われてきたすばらしいオープン ソースのツールキットであり、貢献してくれた開発者コミュニティの努力によって、現在の姿があります。 過去 3 年間で、Microsoft では開発者コミュニティのフィードバックを受け、最も重要な懸念事項に対応するために MRTK v2 を構築しました。  

Unity での MRTK v2 は、Mixed Reality アプリケーション向けのオープンソースのクロスプラットフォーム開発キットです。  MRTK バージョン 2 は、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォームをターゲットとしたアプリケーションの開発を加速することを目的としています。 プロジェクトでは、Mixed Reality アプリケーションを作成するにあたっての参入の障壁を減らし、私たち全員の成長とともにコミュニティに貢献することを目的としています。 

詳細については、[MRTK ドキュメント ポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)を参照してください。

## <a name="new-with-mrtk-v2"></a>MRTK v2 の新機能
これらのプラットフォーム ツールに込めた Microsoft の成果に注目して欲しいと考えています。  事実、Microsoft では MRTK バージョン 2 を活かして、セットアップ エクスペリエンス (OOBE) などのすぐに使えるエクスペリエンスや Mixed Reality Learning アプリケーションを開発しました。  また、新しい HoloLens 2 機能は、まずは MRTK 経由で公開されることを期待していただいてかまいません。Microsoft では、お客様が当社のプラットフォーム上で開発を行ううえで、それが最適な方法であると確信しているからです。 

### <a name="modular"></a>モジュール式
モジュール式の手法でビルドされているため、ツールキットのすべての機能をプロジェクトに組み込む必要はありません。  実際に、これにはいくつかの利点があります。  プロジェクトを小規模に保ち、管理を容易にすることができます。  さらに、スクリプト作成が可能なオブジェクトによってビルドされており、インターフェイス駆動型であるため、組み込みのコンポーネントをお客様独自のものに置き換えて、他のサービス、システム、およびプラットフォームをサポートすることも可能です。

### <a name="cross-platform"></a>クロスプラットフォーム
他のプラットフォームに関しては、クロスプラットフォームのサポートを備えています。  また、このことによって、何もしなくてもすべての単一プラットフォームがサポートされるわけではありませんが、ビルド ターゲットを他のプラットフォームに切り替えたときに、どのツールキットのコードも中断されないことを保証しています。  モジュール式の設計による堅牢性と拡張性を備えることから、適切な手法を利用して、ARCore、ARKit、および OpenVR などの複数のプラットフォームをサポートできます。

### <a name="performant"></a>高いパフォーマンス
モバイル プラットフォームに対応し、パフォーマンスを考慮して構築されています。  このことは非常に重要であり、Microsoft ではツールがお客様の妨げにならないことを保証したいと考えました。

## <a name="see-also"></a>関連項目
* [MRTK 入門ガイド](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [MRTK のドキュメント ホーム](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [ツールのインストール](install-the-tools.md)
* [HTK/MRTK から MRTK バージョン 2 への移植](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
