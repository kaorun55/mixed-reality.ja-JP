---
title: HoloLens 2 のアプリを準備
description: HoloLens で既存のアプリを持っている開発者を対象と (第 1 世代) や MRTK、古くて MRTK バージョン 2 および HoloLens 2 にポートを検索します。
author: grbury
ms.author: grbury
ms.date: 04/12/19
ms.topic: article
keywords: Windows Mixed Reality、テスト、MRTK、MRTK バージョン 2、HoloLens 2
ms.openlocfilehash: 369470326d815ee711e96264939dd2e0487879b6
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873911"
---
# <a name="getting-your-existing-app-ready-for-hololens-2"></a>HoloLens 2 の既存のアプリを準備

このガイドは、HoloLens の既存の Unity アプリを持っている開発者に役立つ特別に用意されて新しい HoloLens 2 デバイス用アプリケーションを移植する (第 1 世代)。 4 つの主要手順、HoloLens を移植するときに (第 1 世代) HoloLens 2 Unity アプリ。 以下のセクションでは、各ステージの情報について詳しく説明します。 

| 手順 1 | 手順 2 | 手順 3. | 手順 4  |
|----------|-------------------|-------------------|-------------------|
| ![Visual Studio ロゴ](images/visualstudio_logo.png) | ![Unity のロゴ](images/unity_logo.png)| ![Unity のアイコン](images/hololens2_icon.jpg) | ![MRTK ロゴ](images/MRTKIcon.jpg) |
| 最新のツールをダウンロードします。 | Unity プロジェクトの更新 | ARM 用にコンパイルします | MRTK v2 への移行します。

**強くお勧めします**移植プロセスを開始する前に、開発者が利用ソース管理、アプリの元の状態のスナップショットを保存することです。 推奨されるさらに、*保存*プロセス中にさまざまな時点でのチェックポイントの状態。 ポート処理中にサイド バイ サイドで比較できるようにする、元のアプリの別の Unity インスタンスに解決に役立てることができます。 

> [!NOTE]
> 移植の前に、Windows Mixed Reality 開発用にインストールされた最新のツールがあることを確認します。 ほとんどの既存 HoloLens 開発者のこの主にプロセスでは最新の Visual Studio 2017 への更新と、適切な Windows SDK をインストールします。 以下の内容について詳しく学ぶ Unity バージョンが異なると Mixed Reality Toolkit バージョン 2 にさらにします。
>
> 詳細についてを参照してください[ツールをインストールする](install-the-tools.md)します。

## <a name="migrate-project-to-latest-version-of-unity"></a>最新バージョンの Unity プロジェクトに移行します。

MRTK v2 を使用して場合 2018 LTS の Unity は Unity または MRTK 互換性に影響する変更せずに最適な長期的なサポート パスになります。  上記"install ツール"ごと、推奨される Unity ビルドは、Unity 2018.3、これは、Unity 2018 の LTS リリースになります。  さらに、MRTK v2 は常に保証 Unity 2018 LTS のサポートされますが、Unity のすべてのイテレーションのサポートは必ずしも保証 2019.x します。 

Unity の他の相違点を明確に理解する 2018.3.x または Unity 2019.1.x、基準値の Unity 2019 で ARM64 用にコンパイルすることの主な違いでこれら 2 つのバージョン間でのアウトライン上のトレードオフ以下。 

開発者は、いずれかを評価する必要があります[プラグインの依存関係](https://docs.unity3d.com/Manual/Plugins.html)現在のプロジェクトおよび ARM64 のこれらの Dll を作成できるかどうかに存在します。 ARM64 用ハードの依存関係のプラグインをビルドできない場合は、Unity 2018 LTS を使用する 1 つ必要があります。


| Unity 2018.3.x | Unity 2019.1 + |
|----------|-------------------|
| ARM32 ビルドのサポート | ARM32 および ARM64 のサポートを構築します。 |
| 安定した LTS リリースをビルドします。 | ベータ版の安定性 |
| [.NET スクリプトのバック エンド](https://docs.unity3d.com/Manual/windowsstore-dotnet.html)*非推奨とされます* | [.NET スクリプトのバック エンド](https://docs.unity3d.com/Manual/windowsstore-dotnet.html)*削除* |
| UNET ネットワーク*非推奨とされます* | UNET ネットワーク*削除* |

## <a name="update-sceneproject-settings-in-unity"></a>Unity でシーンまたはプロジェクト設定を更新します。

Unity に更新した後のデバイスで最適な結果を Unity で特定の設定を更新する 2018.3.x または Unity 2019 + をお勧めします。 これらの設定がで詳細に説明されている **[Unity に推奨される設定](Recommended-settings-for-Unity.md)** します。

再反復処理される必要があるを[.NET スクリプトのバック エンド](https://docs.unity3d.com/Manual/windowsstore-dotnet.html)Unity 2018 では非推奨と*削除*Unity 2019 およびそのため、開発者に強くお勧めへのプロジェクトの切り替え[Il2cpp バック エンド](https://docs.unity3d.com/Manual/IL2CPP.html)します。 

> [!NOTE]
> IL2CPP バック エンドのスクリプトは Visual Studio を Unity からビルド時間が長くなるを発生することができ、開発者が、開発者のコンピューターをセットアップするため[il2cpp バック エンド ビルド時間を最適化する](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)します。

開発者はビルドし、HoloLens で、現在のアプリをテストした後、重大な変更をアドレス指定、更新、Unity のバージョンに移行した後、(第 1 世代)。 さらに、これは、作成してソース管理のコミットを保存するには、出発点です。 

## <a name="compile-dependenciesplugins-for-arm-processor"></a>ARM プロセッサ用の依存関係/プラグインをコンパイルします。

HoloLens (第 1 世代)、x86 上でアプリケーションを実行する新しい HoloLens 2 デバイスは、ARM プロセッサを利用中のプロセッサ。 したがって、既存のアプリケーションは、ARM をサポートするために経由で移植する必要があります。 前述のように、Unity 2018 は、Unity 2019 + ARM64 アプリ用にコンパイルがサポートされますが、ARM32 アプリのコンパイルをサポートします。 ARM64 アプリケーション向けの開発は、パフォーマンスに数量単価型の違いは、一般に推奨されるは。 ただし、これはすべて[プラグインの依存関係](https://docs.unity3d.com/Manual/Plugins.html)も ARM64 用にビルドします。 

現在、アプリケーション内のすべての DLL 依存関係を確認します。 依存関係が不要になった場合は、プロジェクトから削除することをお勧めします。 必要な残りのプラグインを Unity プロジェクトにそれぞれ ARM32 または ARM64 バイナリを取り込みます。 

関連する Dll を取り込み後に、、Unity から Visual Studio ソリューションをビルドし、ARM (ARM プロセッサ向け)、アプリケーションを構築できることをテストする Visual Studio での AppX をコンパイルします。 別のポイントこのコミットをソース管理ソリューションに保存するは勧めします。 

## <a name="update-to-mrtk-version-2"></a>MRTK バージョン 2 に更新します。

MRTK バージョン 2 は、HoloLens の両方をサポートしている Unity の上に新しいツールキット (第 1 世代) と HoloLens 2 と、すべての HoloLens 2 の新機能が追加されていますなどの相互作用を渡すして追跡を注目します。

### <a name="prepare-for-the-migration"></a>移行を準備します。

新しい取り込む前に[MRTK v2 *.unitypackage ファイル](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)のインベントリを作成することを推奨**MRTK v1 と統合された 1) 任意のカスタム ビルド コード**と**2)、カスタム コード入力の相互作用や UX のコンポーネントの**します。 新しい MRTK v2 を取り込み、Mixed Reality 開発者の最も一般的なと普及している競合には、入力との相互作用が含まれます。 読み取りの開始をお勧めそのため、理解、 [MRTK v2 入力モデル](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)します。

最後に、新しい MRTK v2 がスクリプトとシーンでマネージャー オブジェクトのモデルから構成とサービス プロバイダーのアーキテクチャに遷移します。 これにより、シーンの階層とアーキテクチャのモデルをより明確な結果しますが、新しい構成プロファイルを理解するため、学習曲線が必要です。 したがって、参照してください、[混合現実ツールキットの構成ガイド](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)開始、アプリケーションのニーズに合わせて調整するには、重要な設定とプロファイルを理解します。 

### <a name="perform-the-migration"></a>移行を実行します。

MRTK v2 をインポートした後、Unity プロジェクトの場合の多くがコンパイラに関連するエラー。 これらは多くの場合、新しい名前空間の構造と新しいコンポーネント名が原因です。 新しい名前空間およびコンポーネントに、スクリプトを変更することによってこれらのエラーを解決するのには続行します。 

HTK/MRTK と MRTK バージョン 2 の特定の API の相違点の詳細については、上への移植のガイドを参照して、 [MRTK バージョン 2 の wiki](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)します。

### <a name="best-practices"></a>ベスト プラクティス

- MRTK 標準シェーダーの使用を優先します。
- 互換性に影響する 1 つの作業で型を変更する (例。IMixedRealityFocusHandler に IFocusable)
- 変更のたびにテストし、ソース管理を利用
- 既定の MRTK UX (ボタン、スレートなど) を使用可能な場合
- MRTK ファイルを直接変更することを控えるしようとしてください。 は、代わりに MRTK コンポーネント ラッパーを作成
    - これは将来 MRTK ingestions と更新プログラムに対して保護します。
- 確認し、MRTK で提供されるサンプルのシーンの調査 (特に*HandInteractionExamples.scene*)
- 代わりに四角形、コライダー TextMeshPro テキストとキャンバス ベースの UI を再構築します。

### <a name="testing-your-application"></a>アプリケーションのテスト

HoloLens 2 コンポーネントおよび機能は MRTK バージョン 2 で使用できたの[RC1](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/tag/v2.0.0-RC1)Unity で直接手の形の相互作用をシミュレートして手の形の相互作用と視線の新しい Api に対する開発します。  HoloLens 2 デバイスが、優れたエクスペリエンスを作成する必要ですが、ツールとドキュメントの学習を始めるには少なくとも 1 つできます。 さらに、MRTK v2 は HoloLens の開発をサポートしています (第 1 世代) エア タップ経由での選択は、HoloLens で引き続きテストできますなど、そのため、従来の入力をモデル化し、(第 1 世代) デバイス。 

## <a name="updating-interaction-model-for-hololens-2"></a>HoloLens 2 の相互作用モデルの更新

移植および HoloLens 2 の準備を行うアプリを作成したらの相互作用モデルとホログラム設計/配置の更新を検討する準備が整いました。
HoloLens から (第 1 世代) 可能性の高いアプリに注視し、コミット相互作用モデル ビューのフィールドに収まるように比較的離れたホログラムとします。

HoloLens 2 最適である、アプリの設計を更新する手順:
1.  MRTK コンポーネント:事前の作業単位 MRTK v2 では、追加した場合はスクリプトが存在さまざまなコンポーネント/を活用するように設計され、HoloLens 2 用に最適化されています。

2.  相互作用モデル:相互作用モデルを更新することを検討します。  ほとんどのシナリオでは視線入力からの切り替えをお勧めし、手をコミットします。  ホログラムが到達腕から通常中に、手への切り替えはポインティング光線の相手側の対話が発生し、ジェスチャを取得します。
注:、楽に相互作用モデルは、ツールを保持するタスク ワーカーなど、必要なこのような場合の特定の設計ガイダンスがあるシナリオがあります。 

3.  ホログラム配置:手の相互作用モデルに後に、いくつかホログラム近い近く相互作用グラブ ジェスチャを使用して、手をホログラムと直接対話する移動を検討してください。  ホログラムを直接取得や操作に近い場所に移動することが推奨の型は、小さなターゲット メニューのコントロール、ボタン、および取得と検査、ホログラム HoloLens 2 フィールドのビュー内に収まる小さいホログラムは。
<br>
すべてのアプリとシナリオが異なるとを調整し、投稿の設計ガイダンスからのフィードバックに基づいておよび学習を続けていく予定です。


## <a name="additional-learnings-from-moving-apps-from-x86-to-arm"></a>追加により、x86 から ARM へのアプリの移動

- 直線の Unity アプリは、実行されると、ARM appx バンドルをビルドまたはデバイスに直接配置することができます簡単です。
課題は、Unity アプリのネイティブ プラグインを使用する場合です。  すべてのネイティブ プラグインは、VS2017 にアップグレードしても、Unity 2019、ARM64 を使用して、ARM の再構築する必要があります。

- アプリを 1 つは for Unity、AudioKinetic Wwise プラグインを使用して、使用されているバージョンは UWP ARM プラグインがありませんでした。 ARM で動作するアプリケーションでサウンドを再作業には何日かかりました。

- その他の場合は、ポート、HoloLens 2 で実行する能力を妨げていないアプリに必要なプラグインの UWP/ARM プラグインが存在しません。  プラグインのプロバイダーとの契約は、ブロックを解除し、ARM をサポートする必要あります。

- シェーダーで minfloat (およびバリアントなど min16float、minint など) の動作が異なります HoloLens でより HoloLen 2 (第 1 世代)。 具体的には、これら保証"以上で、指定のビット数が使用されます"。 Intel/Nvidia の Gpu ではこれらだけ大きく、32 ビットとして扱われます。 ARM で指定されたビット数は実際に遵守されます。 実際には、これらの数値が小さい精度/範囲 HoloLens 2 よりも長く HoloLens のことを意味する (第 1 世代)。

- つまり _asm 命令を使用して任意のコードを書き直す必要は ARM で作業する _asm 指示が表示されません。

- ARM では、SIMD 命令のセットがサポートされていません。 さまざまなヘッダーは、このためなど、xmmintrin.h 内、emmintrin.h 内、tmmintrin.h、および immintrin.h は ARM で使用できません。

- ARM の実行後、シェーダーが読み込まれたまたはに依存するもの、シェーダーの最初の描画呼び出し中にシェーダー コンパイラは、シェーダーの読み込み時ではなく変わりました。 フレーム レートがへの影響をコンパイルする必要がどのように多くのシェーダーによって大きく異なることができます。 これは、さまざまな影響がどのようにシェーダーされる処理/パッケージ化/更新された HoloLens 2 vs HoloLens でそれぞれ異なる (第 1 世代)。

## <a name="see-also"></a>関連項目
* [MRTK バージョン 2 の概要](mrtk-getting-started.md)
* [MRTK バージョン 2 HowTo](https://microsoft.github.io/MixedRealityToolkit-Unity/External/HowTo/README.html)
* [ツールのインストール](install-the-tools.md)
* [Unity で推奨される設定](recommended-settings-for-unity.md)
* [複合現実のパフォーマンスを理解](understanding-performance-for-mixed-reality.md)

