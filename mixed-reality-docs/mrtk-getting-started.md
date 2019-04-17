---
title: MRTK バージョン 2 の概要
description: 新しい開発者 MRTK を活用することに関心が向け
author: grbury
ms.author: grbury
ms.date: 02/22/19
ms.topic: article
keywords: Windows Mixed Reality、テスト、MRTK バージョン 2、MRTK、ツール、SDK、HoloLens、HoloLens 2
ms.openlocfilehash: 44e5fe0fd4384af68922eda4bcb0594d39a1c1b7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600031"
---
# <a name="getting-started-with-mrtk-version-2"></a>MRTK バージョン 2 の概要

MRTK は、HoloLens はリリース当初とでは、今せずに作成した開発者コミュニティの困難な作業はできないためにきました驚くようなオープン ソースのツールキットです。 過去 3 年の間、開発者コミュニティのフィードバックに応えし、する最大の懸念事項を考慮に入れて MRTK バージョン 2 を構築しました。  

Unity を使った MRTK バージョン 2 は、複合現実のアプリケーション用のオープン ソース クロス プラットフォーム開発キットです。  MRTK バージョン 2 の目的は、Microsoft HoloLens、Windows Mixed Reality 没入型 (VR) ヘッドセットと OpenVR プラットフォームを対象とするアプリケーションの開発を促進します。 プロジェクトの目的は、複合現実のアプリケーションを作成しすべての拡大に伴い、コミュニティに貢献するエントリに対する障壁を削減です。 


参照してください、 <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki/Getting-Started-with-MRTK-v2" target="_blank">MRTK バージョン 2 の wiki</a>概要および詳細について説明します。

## <a name="new-with-mrtk-version-2"></a>MRTK バージョン 2 で新しい
これらのプラットフォーム ツールに対するマイクロソフトのコミットメントを強調します。  実際には、セットアップ experience (OOBE) や Mixed Reality Learning アプリケーションなど、受信トレイ エクスペリエンスを開発する MRTK バージョン 2 を利用します。  最初は、プラットフォーム上で開発する最善の方法を考えているためです MRTK を通じて公開されている新しい HoloLens 2 機能を確認することも期待できます。 

### <a name="modular"></a>モジュール
ツールキットのすべてのビットをプロジェクトを考慮する必要はありませんようにして、モジュール方式で作成しましたがあります。  これを実際には、いくつかの利点があります。  プロジェクトのサイズを小さく維持だけでなく管理しやすくなります。  スクリプト可能なオブジェクトで構築されていますので、インターフェイス駆動ことも、その他のサービス、システム、およびプラットフォームをサポートするために、独自に含まれているコンポーネントを交換するため。


### <a name="cross-platform"></a>クロスプラットフォーム
その他のプラットフォームと言えば、クロス プラットフォーム サポートしています。  すべて 1 つのプラットフォームがサポートしているわけでは中、に他のプラットフォーム、ビルド ターゲットを切り替えたときに中断されます toolkit のことを確認されました。  堅牢性とモジュールの設計による拡張機能を ARCore、ARKit、OpenVR など、複数のプラットフォームをサポートできる適切なパスを設定します。


### <a name="performant"></a>パフォーマンスの高い
モバイル プラットフォームを使用 20050607 がパフォーマンスに注意してください。  これは非常に重要なツールが働きますしようとしていないことを確認したいです。


## <a name="see-also"></a>関連項目
* [ツールをインストールします。](install-the-tools.md)
* [HTK/MRTK から MRTK バージョン 2 への移植](mrtk-porting-guide.md)
