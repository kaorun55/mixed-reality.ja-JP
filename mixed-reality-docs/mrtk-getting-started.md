---
title: MRTK バージョン2の概要
description: MRTK の活用に関心がある新しい開発者向け
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
keywords: Windows Mixed Reality、test、Mixed Reality Toolkit、MRTK バージョン2、MRTK、tools、SDK、HoloLens、HoloLens 2
ms.openlocfilehash: bb958543aa68586dd689a2048665b233d6be7064
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913128"
---
# <a name="getting-started-with-mrtk-v2"></a>MRTK v2 の概要

## <a name="mrtk-getting-started-guide"></a>MRTK はじめにガイド
MRTK V2 の概要については、「 [mrtk ファーストステップガイド](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)」を参照してください。

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Mixed Reality Toolkit (MRTK) とは
MRTK は、HoloLens が最初にリリースされた後に行われていたすばらしいオープンソースのツールキットであり、現在のところ、開発者コミュニティが提供されているので、このツールキットを使用することはできません。 過去3年間、microsoft は開発者コミュニティのフィードバックを受け、最大の関心事を考慮するために MRTK v2 を構築しました。  

Unity での MRTK v2 は、Mixed Reality アプリケーション向けのオープンソースのクロスプラットフォーム開発キットです。  MRTK バージョン 2 は、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォームをターゲットとしたアプリケーションの開発を加速することを目的としています。 プロジェクトは、参加する障壁を減らすことを目的としています。これにより、複雑な現実アプリケーションを作成し、すべての拡大に応じてコミュニティに貢献できます。 

詳細については、 [Mrtk ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)を参照してください。

## <a name="new-with-mrtk-v2"></a>MRTK v2 の新バージョン
これらのプラットフォームツールに対するコミットメントを重視したいと考えています。  実際、MRTK バージョン2を利用して、setup experience (OOBE) や Mixed Reality Learning アプリケーションなどの受信トレイエクスペリエンスを開発しました。  また、プラットフォームで開発するのに最適な方法であると考えられるため、新しい HoloLens 2 機能が MRTK を通じて最初に公開されることが予想されます。 

### <a name="modular"></a>方式
モジュール型の方法でビルドしたので、ツールキットのすべての機能をプロジェクトに組み込む必要はありません。  これには、実際にいくつかの利点があります。  これにより、プロジェクトのサイズが小さくなり、管理が容易になります。  さらに、スクリプト可能なオブジェクトを使用して構築され、インターフェイス主導型であるため、独自のに含まれているコンポーネントを置き換えることで、他のサービス、システム、およびプラットフォームをサポートすることもできます。

### <a name="cross-platform"></a>クロスプラットフォーム
他のプラットフォームの場合は、クロスプラットフォームのサポートがあります。  これは、すべての単一プラットフォームが既定でサポートされているわけではありませんが、ビルドターゲットを他のプラットフォームに切り替えると、どのツールキットコードも破損しないようにしました。  モジュール型の設計による堅牢性と拡張性により、ARCore、Arcore、OpenVR などの複数のプラットフォームをサポートするための優れたパスを設定できます。

### <a name="performant"></a>パフォーマンス
モバイルプラットフォームを使用すると、パフォーマンスを考慮して構築されています。  これは非常に重要であり、ツールがお客様に対して機能しないようにする必要がありました。

## <a name="see-also"></a>関連項目
* [MRTK ファーストステップガイド](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [MRTK ドキュメントホーム](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [ツールのインストール](install-the-tools.md)
* [HTK/MRTK から MRTK バージョン2への移植](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
