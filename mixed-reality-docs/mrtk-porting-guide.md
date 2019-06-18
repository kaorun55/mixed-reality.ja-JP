---
title: アプリを HoloLens 2 で利用できるようにする
description: HoloLens (第 1 世代) または古い MRTK の既存アプリがあり、MRTK バージョン 2 および HoloLens 2 への移植を考えている開発者が対象です。
author: grbury
ms.author: grbury
ms.date: 04/12/19
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, テスト, MRTK, MRTK バージョン 2, HoloLens 2
ms.openlocfilehash: 02dabd21b7a6add2ce53fe291a447e49057184d0
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66270394"
---
# <a name="getting-your-existing-app-ready-for-hololens-2"></a>既存のアプリを HoloLens 2 で利用できるようにする

このガイドは、HoloLens (第 1 世代) 用の既存 Unity アプリがある開発者が新しい HoloLens 2 デバイス用のアプリケーションに移植する際に特に役立ちます。 4 つの主要手順で、HoloLens (第 1 世代) の Unity アプリを HoloLens 2 に移植することができます。 以下のセクションでは、各ステージについて詳しく説明します。 

| 手順 1 | 手順 2 | 手順 3 | 手順 4 |
|----------|-------------------|-------------------|-------------------|
| ![Visual Studio のロゴ](images/visualstudio_logo.png) | ![Unity のロゴ](images/unity_logo.png)| ![Unity のアイコン](images/hololens2_icon.jpg) | ![MRTK のロゴ](images/MRTKIcon.jpg) |
| 最新のツールのダウンロード | Unity プロジェクトの更新 | ARM 用にコンパイル | MRTK v2 に移行

移植プロセスを開始する前に、開発者がソース管理を利用してアプリの元の状態のスナップショットを保存しておくことを**強くお勧めします**。 さらに、プロセス中のさまざまな時点でチェックポイントの状態を*保存*することを推奨します。 移植プロセスの中で、元のアプリの別の Unity インスタンスを並べて比較できるようにするのも非常に便利です。 

> [!NOTE]
> 移植の前に、Windows Mixed Reality の開発用に最新のツールがインストールされていることを確認します。 ほとんどの既存 HoloLens 開発者は、主に最新の Visual Studio 2017 への更新と適切な Windows SDK のインストールを行うことになります。 以下の内容では、Unity のさまざまなバージョンと Mixed Reality Toolkit バージョン 2 についてさらに詳しく説明します。
>
> 詳しくは、[ツールのインストール](install-the-tools.md)に関するページをご覧ください。

## <a name="migrate-project-to-latest-version-of-unity"></a>プロジェクトを最新バージョンの Unity に移行する

MRTK v2 を使用している場合、Unity または MRTK で互換性に影響する変更が発生しない最適な長期サポート パスは Unity 2018 LTS になります。  上記のツールのインストールに関するページでは、推奨される Unity ビルドは Unity 2018.3 です。今後これが Unity 2018 の LTS リリースになります。  また、MRTK v2 は Unity 2018 LTS のサポートを常に保証していますが、必ずしも Unity 2019.x のすべてのイテレーションのサポートが保証されるわけではありません。 

Unity 2018.3.x または Unity 2019.1.x との間の他の相違点を明らかにするために、以下では、これら 2 つのバージョン間でのトレードオフについて説明します。主な違いは、Unity 2019 で ARM64 用にコンパイルする機能です。 

開発者は、現在プロジェクトに存在するすべての[プラグインの依存関係](https://docs.unity3d.com/Manual/Plugins.html)と、DLL が ARM64 でビルドできるかどうかを評価する必要があります。 ARM64 でハードに依存するプラグインをビルドできない場合は、Unity 2018 LTS を使用しなければなりません。


| Unity 2018.3.x | Unity 2019.1+ |
|----------|-------------------|
| ARM32 ビルドのサポート | ARM32 および ARM64 ビルドのサポート |
| 安定版の LTS ビルド リリース | ベータ版の安定性 |
| [.NET スクリプト バックエンド](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *非推奨* | [.NET スクリプト バックエンド](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *削除済み* |
| UNET Networking *非推奨* | UNET Networking *削除済み* |

## <a name="update-sceneproject-settings-in-unity"></a>Unity でシーンまたはプロジェクト設定を更新する

デバイスで最適な結果を得るために、Unity 2018.3.x または Unity 2019 以降に更新した後、Unity を特定の設定に更新すること をお勧めします。 この設定については、 **[Unity の推奨設定](Recommended-settings-for-Unity.md)** で詳しく説明しています。

もう一度お伝えしますが、[.NET スクリプト バックエンド](https://docs.unity3d.com/Manual/windowsstore-dotnet.html)は、Unity 2018 で非推奨となり、Unity 2019 で*削除*されているため、開発者はプロジェクトを [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html) に切り替えることを検討する必要があります。 

> [!NOTE]
> IL2CPP スクリプト バックエンドを使用すると、Unity から Visual Studio へのビルド時間が長くなる場合があります。そのため、開発者はコンピューターをセットアップするため[IL2CPP ビルド時間の最適化](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)を行う必要があります。
> 特に、大きなアセット (スクリプト ファイルを除く) がある場合や、常にシーンやアセットを変更する Unity プロジェクトの場合は、[キャッシュ サーバー](https://docs.unity3d.com/Manual/CacheServer.html)をセットアップするとよいでしょう。 プロジェクトを開く際に、Unity は条件を満たすアセットを内部キャッシュ フォーマットで開発者のコンピューターに格納します。 項目を変更した場合は、再インポートして再処理されるようにする必要があります。 このプロセスが 1 回実行されると、キャッシュ サーバーに保存され、すべての開発者に共有されます。すべての開発者がローカルで新しい変更の再インポート処理を行う必要がなくなるので、時間を節約できます。

開発者は、更新した Unity のバージョンに移行し、互換性のない変更に対処した後、HoloLens (第 1 世代) で現在のアプリをビルドしてテストする必要があります。 また、この時点でソース管理にコミットを作成し、保存しておくとよいでしょう。 

## <a name="compile-dependenciesplugins-for-arm-processor"></a>ARM プロセッサ用の依存関係およびプラグインのコンパイル

HoloLens (第 1 世代) は、x86 プロセッサ上でアプリケーションを実行しますが、新しい HoloLens 2 デバイスは、ARM プロセッサを利用します。 したがって、既存のアプリケーションは、ARM をサポートするように移植する必要があります。 前述のように、Unity 2018 は ARM32 アプリのコンパイルをサポートしますが、Unity 2019 以降は ARM64 アプリのコンパイルをサポートします。 一般的に、パフォーマンスに重要な相違があるため、ARM64 アプリケーションでの開発が推奨されます。 ただし、そのためには、すべての[プラグインの依存関係](https://docs.unity3d.com/Manual/Plugins.html)も ARM64 でビルドする必要があります。 

現在のアプリケーション内のすべての DLL 依存関係を確認してください。 依存関係が不要になった場合は、プロジェクトから削除することをお勧めします。 必要な残りのプラグインについて、Unity プロジェクトにそれぞれ ARM32 または ARM64 バイナリを取り込みます。 

関連する DLL を取り込んだ後、Unity から Visual Studio ソリューションをビルドし、アプリケーションが ARM プロセッサでビルドできるかどうかを試すために、Visual Studio で AppX を ARM 向けにコンパイルします。 ここが、ソース管理ソリューションでコミットを保存することが推奨されるもう 1 つのポイントです。 

## <a name="update-to-mrtk-version-2"></a>MRTK バージョン 2 に更新する

MRTK バージョン 2 は、Unity をベースにした新しいツールキットで、HoloLens (第 1 世代) と HoloLens 2 の両方をサポートしています。また、手による操作や視線追跡など、すべての HoloLens 2 の新機能が追加されています。

### <a name="prepare-for-the-migration"></a>移行を準備する

新しい [MRTK v2 用の *.unitypackage ファイル](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)を取り込む前に、**1) MRTK v1 を組み込んだ任意のカスタム ビルド コード**と、**2) 入力操作や UX コンポーネントのカスタム ビルド コード**のインベントリを取得することを推奨します。 Mixed Reality 開発者が新しい MRTK v2 を取り込む際に最も競合が起きやすいのは、入力と操作に関係する部分です。 そのため、[MRTK v2 入力モデル](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)を読んで理解しておくことをお勧めします。

最後に、新しい MRTK v2 は、スクリプトのモデルおよびシーン内マネージャー オブジェクトから、構成およびサービス プロバイダー アーキテクチャに移行されています。 これにより、シーンの階層とアーキテクチャのモデルがクリーンになりますが、新しい構成プロファイルを習得する必要があります。 したがって、重要な設定やプロファイルについて理解し、アプリケーションのニーズに合わせて調整することができるように、[Mixed Reality ツールキット構成ガイド](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)を参照してください。 

### <a name="perform-the-migration"></a>移行する

MRTK v2 をインポートすると、Unity プロジェクトでたくさんのコンパイラ関連エラーが発生します。 多くの場合、これらの原因は新しい名前空間の構造と新しいコンポーネント名です。 スクリプトの名前空間とコンポーネントを新しいものに変更し、これらのエラーを解決します。 

HTK/MRTK と MRTK バージョン 2 の具体的な API の相違点の詳細については、 [MRTK バージョン 2 wiki](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html) の移植ガイドをご覧ください。

### <a name="best-practices"></a>ベスト プラクティス

- MRTK 標準シェーダーの使用を優先する
- 互換性に影響する種類の変更には 1 つずつ対応する (例:IFocusable を IMixedRealityFocusHandler に)
- 変更のたびにテストし、ソース管理を利用する
- 可能な場合は既定の MRTK UX (ボタン、スレートなど) を使用する
- MRTK ファイルを直接変更するのは避け、MRTK コンポーネントのラッパーを作成する
    - 将来の MRTK の取り込みや更新プログラムの影響を受けなくなる
- MRTK で提供されているサンプルのシーンを確認する (特に *HandInteractionExamples.scene*)
- キャンバス ベースの UI を四角形、コライダー、TextMeshPro テキストで再構築する

### <a name="testing-your-application"></a>アプリケーションのテスト

[RC1](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/tag/v2.0.0-RC1) 時点で、HoloLens 2 のコンポーネントおよび機能が MRTK バージョン 2 で使用できるようになっています。そのため、手による操作を直接 Unity でシミュレートし、手による操作と視線追跡の新しい API を使って開発を行うことができます。  優れたエクスペリエンスを作成するには HoloLens 2 デバイスが必要ですが、少なくとも、ツールと説明書の学習を始めることはできます。 また、MRTK v2 は HoloLens (第 1 世代) の開発をサポートしています。そのため、エア タップによる選択などの従来の入力モデルは、引き続き HoloLens (第 1 世代) デバイスでテストできます。 

## <a name="updating-interaction-model-for-hololens-2"></a>HoloLens 2 の操作モデルの更新

アプリを移植して HoloLens 2 に対応できたら、操作モデルやホログラムの設計および配置の更新を検討する準備が整います。
もともと HoloLens (第 1 世代) のアプリだったため、視線入力とコミットによる操作モデルが使われており、視野に収まるようにホログラムがかなり遠くにある可能性が高いはずです。

アプリの設計を HoloLens 2 に最適にする手順は、以下のとおりです。
1.  MRTK コンポーネント:事前の作業で MRTK v2 を追加した場合は、HoloLens 2 用に設計および最適化されているさまざまなコンポーネントやスクリプトを活用できます。

2.  操作モデル:操作モデルを更新することを検討します。  ほとんどのシナリオでは、視線入力とコミットを手に切り替えることをお勧めします。  通常、ホログラムは手の届かないところにあるので、手に切り替えることで、ポインティング レイやグラブ ジェスチャによる遠隔インタラクションを利用することになります。
注: ツールを持っているタスク ワーカーなど、手を使わない操作モデルが必要なシナリオもあります。このような場合に向けた特別な設計ガイダンスが存在します。 

3.  ホログラムの配置:手による操作モデルに切り替えた後は、直接手で近接インタラクションのグラブ ジェスチャを使用した操作を行えるように、ホログラムを近くに移動することを検討します。  直接つかんだり操作を行ったりするために近くに移動させることが推奨されるホログラムの種類は、小さなターゲット メニュー、コントロール、ボタン、およびグラブしたり調べたりしても HoloLens 2 の視野に収まる小さなホログラムです。
<br>
どのアプリやシナリオにも同じものはないので、フィードバックや継続する学習に基づいて設計ガイダンスを見直し、掲載し続ける予定です。


## <a name="additional-learnings-from-moving-apps-from-x86-to-arm"></a>x86 から ARM へのアプリを移植するにあたっての追加情報

- 単純な Unity アプリは、ARM appx バンドルをビルドしてデバイスに直接配置すれば実行できるので、簡単です。
問題は、Unity アプリがネイティブ プラグインを使用する場合です。  すべてのネイティブ プラグインは、VS2017 にアップグレードして ARM 用にビルドしなおす必要があります。Unity 2019 では、ARM64 用にビルドしなおします。

- Unity で AudioKinetic Wwise プラグインを使用しているあるアプリでは、使用されているバージョンに UWP ARM プラグインがありませんでした。 アプリケーションのサウンドを見直して ARM で動作するようになるまで、数日がかかりました。

- 他にも、アプリに必要なプラグインの UWP/ARM プラグインが存在しないため、移植して HoloLens 2 で実行することができない場合もあるかもしれません。  これに対処して ARM をサポートするには、プラグインのプロバイダーによる作業が必要になる可能性もあります。

- HoloLen 2 では、シェーダーの minfloat (および min16float、minint などのバリアント) の動作が HoloLens (第 1 世代) と異なる場合があります。 具体的には、「少なくとも指定された数のビットが使われる」ことが保証されます。 ほとんどの Intel/Nvidia の GPU では、単なる 32 ビットとして扱われます。 ARM では、指定されたビット数が実際に使用されます。 実際には、HoloLens 2 でのこれらの数値の精度や範囲は、HoloLens (第 1 世代) よりも小さくなります。

- ARM では _asm 命令は動作しないと見られるので、_asm 命令を使っているコードはすべて書き直す必要があります。

- ARM では、SIMD 命令セットがサポートされていません。 そのため、ARM では xmmintrin.h、emmintrin.h、tmmintrin.h、および immintrin.h などの各種ヘッダーは使用できません。

- ARM のシェーダー コンパイラは、シェーダーの読み込み時ではなく、シェーダーが読み込まれた後またはシェーダーが依存するものが変更された後の最初の描画呼び出しの中で実行されます。 コンパイルする必要があるシェーダーの数によっては、フレーム レートへの影響が顕著になる場合があります。 この点から、HoloLens 2 と HoloLens (第 1 世代) でどのようにシェーダーの処理/パッケージ化/更新の方法を変えるべきかについて、さまざまなことがわかります。

## <a name="see-also"></a>関連項目
* [MRTK バージョン 2 をお使いになる前に](mrtk-getting-started.md)
* [MRTK バージョン 2 の使用方法](https://microsoft.github.io/MixedRealityToolkit-Unity/External/HowTo/README.html)
* [ツールのインストール](install-the-tools.md)
* [Unity で推奨される設定](recommended-settings-for-unity.md)
* [Mixed Reality のパフォーマンスを理解する](understanding-performance-for-mixed-reality.md)

