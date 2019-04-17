---
title: MRTK パッケージ
description: この記事では、Microsoft Mixed Reality Toollkit を構成するパッケージについて説明します。
author: davidkline-ms
ms.author: davidkl
ms.date: 02/12/19
ms.topic: article
keywords: Windows Mixed Reality MRTK、コンポーネントのパッケージ
ms.openlocfilehash: 7e44d75e1c267cff0ba67dd86dabfaa51bce659d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604641"
---
# <a name="mrtk-packages"></a>MRTK パッケージ

Mixed Reality ツールキット (MRTK) は、コンポーネント化された方法での複合現実のハードウェアおよびプラットフォーム サポートを提供することでクロス プラットフォームの複合現実アプリケーションの開発が可能なパッケージのコレクションです。

MRTK パッケージの 3 つのカテゴリがあります。 

* [Foundation](#foundation-packages)
* [拡張機能](#extension-packages)
* [実験用](#experimental-packages)

## <a name="foundation-packages"></a>Foundation パッケージ

混合現実 Toolkit Foundation は、Mixed Reality プラットフォーム間で共通の機能を活用するアプリケーションを有効にするパッケージのセットです。 これらのパッケージがリリースされ、ソース コードから Microsoft でサポートされている、 [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) GitHub 上の分岐。

![MRTK Foundation パッケージ](images/mrtk-foundation.jpg)

*Mixed Reality Toolkit Foundation パッケージ*

MRTK Foundation から成ります。

* [コア パッケージ](#core-package)
* [プラットフォーム プロバイダー](#platform-providers)
* [システム サービス](#system-services)
* [資産の機能](#feature-assets)

次のセクションでは、各カテゴリ内のパッケージの種類について説明します。

### <a name="core-package"></a>コア パッケージ

Core パッケージは、_必要_コンポーネント MRTK foundation のすべてのパッケージで依存関係として取得されます。

MRTK Core パッケージは次のとおりです。

* [共通のインターフェイス、クラス、およびデータ型](#common-interfaces-clases-and-data-types)
* [MixedRealityToolkit シーンのコンポーネント](#mixedrealitytoolkit-scene-component)
* [MRTK 標準シェーダー](#mrtk-standard-shader)
* [Unity 入力プロバイダー](#unity-input-provider)
* [パッケージの管理](#package-management)

#### <a name="common-interfaces-classes-and-data-types"></a>共通のインターフェイス、クラス、およびデータ型

混合現実ツールキットのコア パッケージには、すべてのクラスとその他のすべてのコンポーネントで使用されるデータ型は、一般的なインターフェイスの定義が含まれています。 アプリケーションがプラットフォーム間で最大限の互換性を有効にする、定義されたインターフェイスを通じてのみ MRTK コンポーネントをアクセスすることを強くお勧めします。

#### <a name="mixedrealitytoolkit-scene-component"></a>MixedRealityToolkit シーンのコンポーネント

MixedRealityToolkit シーンのコンポーネントは、Mixed Reality ツールキットの 1 つの一元的なリソース マネージャーです。 このコンポーネントはロード プラットフォームおよびサービス モジュールの有効期間を管理し、それらの構成設定にアクセスするシステム リソースを提供します。 

#### <a name="mrtk-standard-shader"></a>MRTK 標準シェーダー

MRTK 標準シェーダーは、MRTK によって提供されるマテリアルのほぼすべての基盤を提供します。 このシェーダーは、非常に柔軟で、さまざまな MRTK がサポートされているプラットフォーム向けに最適化します。 _高_アプリケーションの資料が最適なパフォーマンス MRTK 標準シェーダーを使用することをお勧めします。

#### <a name="unity-input-provider"></a>Unity 入力プロバイダー

Unity の入力プロバイダーは、ゲーム コント ローラーや 3D 空間マウス、タッチ スクリーンなどの一般的な入力デバイスへのアクセスを提供します。

#### <a name="package-management"></a>パッケージ管理

_近日公開_

混合現実ツールキットのコア パッケージは、検出およびオプションの foundation、拡張機能および MRTK の実験用のパッケージを管理するためのサポートを提供します。

### <a name="platform-providers"></a>プラットフォーム プロバイダー

MRTK プラットフォーム プロバイダー パッケージは、Mixed Reality ハードウェアをターゲットに混合現実 Toolkit とプラットフォームの機能を有効にするコンポーネントです。

サポートされているプラットフォームは次のとおりです。

* [Windows Mixed Reality](#windows-mixed-reality)
* [OpenVR](#openvr)
* [Windows Voice](#windows-voice)

#### <a name="windows-mixed-reality"></a>Windows Mixed Reality

Windows Mixed Reality パッケージでは、Microsoft HoloLens と Windows Mixed Reality 没入型のデバイスのサポートも提供します。 パッケージに含まれるすべてのプラットフォームのサポートを含みます。

* 視線の先を対象とします。
* ジェスチャ
* Windows Mixed Reality モーションのコント ローラー
* 空間マッピング

#### <a name="openvr"></a>OpenVR

OpenVR パッケージでは、OpenVR プラットフォームを使用してデバイスのハードウェアおよびプラットフォームのサポートを提供します。

#### <a name="windows-voice"></a>Windows Voice

Windows 音声パッケージは、Microsoft Windows 10 デバイスで、キーワード認識とディクテーション機能のサポートを提供します。

### <a name="system-services"></a>システム サービス

コア プラットフォームのサービスは、システム サービス パッケージで提供されます。 これらのパッケージには、Mixed Reality Toolkit の既定の実装で定義されているシステム サービスのインターフェイスが含まれて、 [core](#core-package)パッケージ。

MRTK foundation には、次のシステム サービスが含まれています。

* [システムの境界](#boundary-system)
* [診断システム](#diagnostic-system)
* [入力システム](#input-system)
* [空間認識システム](#spatial-awareness-system)
* [テレポート システム](#teleport-system)

#### <a name="boundary-system"></a>システムの境界

MRTK 境界システムに仮想現実に関するデータを提供する playspace します。 対象のユーザーが、境界を構成しているシステムでは、システムは、床面、四角形の playspace、追跡対象の領域、および提供できます。

#### <a name="diagnostic-system"></a>診断システム

MRTK 診断システムでは、アプリケーションのエクスペリエンス内でリアルタイムのパフォーマンス データを提供します。 概要、アプリケーションを使用すると、フレーム レート、プロセッサ時間およびその他の主要なパフォーマンス メトリックを表示することになります。

#### <a name="input-system"></a>入力システム

MRTK 入力システムには、アプリケーションにアクセスするには、クロス プラットフォームの方法で入力をユーザーのアクションを指定する最も適切なボタンとターゲット コント ローラーの軸にこれらのアクションを割り当てることができます。

#### <a name="spatial-awareness-system"></a>空間認識システム

MRTK 空間認識システムには、Microsoft HoloLens などのデバイスから実際の環境のデータにアクセスができるようにします。

#### <a name="teleport-system"></a>テレポート システム

MRTK テレポート システムは、仮想現実 locomotion サポートを提供します。

### <a name="feature-assets"></a>資産の機能

機能の資産は、Unity の資産とスクリプトとして提供される関連する機能のコレクションです。 これらの機能のいくつか挙げます。

* ユーザー インターフェイス コントロール
* Standard Assets
* more

## <a name="extension-packages"></a>拡張機能パッケージ

MRTK 拡張機能パッケージは、Mixed Reality ツールキットの機能強化のための拡張とを Microsoft およびコミュニティによって作成されたパッケージのコレクションです。 拡張機能の作成者は、必要な依存関係の状態、Mixed Reality Toolkit に互換性があるパッケージをマーク、ライセンスを提供およびされステートメントがサポートされます。

拡張機能パッケージには、新機能と新しいプラットフォームのサポートを提供できます。 時間の経過と共に拡張機能が、アシスタンスと作成者の承認に移行 MRTK Foundation 時点でそれらがリリースされ、Microsoft でサポートされています。

![MRTK 拡張機能パッケージ](images/mrtk-extensions.jpg)

*Mixed Reality Toolkit の拡張機能パッケージ*

## <a name="experimental-packages"></a>実験用のパッケージ

実験用のパッケージは、フライトのプロトタイプ機能、プレリリース版および魅力的な新しいアイデアに機能を提供します。 最も実験用のパッケージの目的は、新しい機能を試すと、お客様の関心をゲージにです。 多くの場合、プロトタイプ作成とテスト フェーズが完了すると、実験用のパッケージが拡張機能として再リリースがすべてではない場合。

![MRTK 実験用のパッケージ](images/mrtk-experimental.jpg)

*Mixed Reality Toolkit 実験的なパッケージ*

## <a name="conclusion"></a>まとめ

された炎のプロジェクトに含まれる不要なコンポーネントを必要とせず、エクスペリエンスに機能を構築するため、クリーンで単純なメソッドを有効にするのには、Mixed Reality Toolkit パッケージとパッケージ管理システムが設計されています。

時間の経過と共にパッケージ管理のサポートが追加され Mixed Reality Toolkit 内で強化されています。 フィードバックがあるプログラムへの参加を希望するかを参照してください、 [Mixed Reality Toolkit プロジェクト](https://github.com/Microsoft/MixedRealityToolkit-Unity)GitHub でします。 

## <a name="see-also"></a>関連項目

* [MixedRealityToolkit-Unity (GitHub)](https://github.com/Microsoft/MixedRealityToolkit-Unity)

