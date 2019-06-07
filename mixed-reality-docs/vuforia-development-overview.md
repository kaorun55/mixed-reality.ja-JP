---
title: Unity で Vuforia の使用
description: Unity での Windows Mixed Reality アプリケーションを構築する Vuforia を活用します。
author: ailyadis
ms.author: ''
ms.date: 01/28/2019
ms.topic: article
keywords: Vuforia、マーカー、座標、フレームの参照では、追跡
ms.openlocfilehash: c0d2f6d0707e1ddd3ee00d3eb80af9fb459f252b
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750345"
---
# <a name="using-vuforia-engine-with-unity"></a>Unity を使った Vuforia エンジンを使用します。

Vuforia エンジンでは、重要な機能を HoloLens に – AR を接続する power が特定のイメージを環境内のオブジェクトで発生します。 産業用のエンタープライズ向け機械の上にガイド付きの手順を重ね合わせる、または物理的な製品やゲームをデジタル機能とエクスペリエンスを追加するのには、この機能を使用することができます。 

柔軟性を高めるため、AR の開発で発生した場合、Vuforia エンジンはさまざまな特徴とターゲットを提供します。 最新の機能、Vuforia モデルのターゲットの 1 つは商用および産業の両方の用途のための主要な機能です。 ターゲットのモデルでは、物理オブジェクトを選択し、マシン、自動車、toys などの CAD またはデジタルの 3D モデルに基づく追跡を認識するアプリケーションを許可します。 産業は、この機能は、アセンブリのワーカーを提供でき、AR のサービス技術者の作業指示と、ファクトリで手順を説明または out フィールドにします。 

スマート フォンおよびタブレット用にビルドされた既存の Vuforia エンジン アプリは、HoloLens で実行する Unity で簡単に構成できます。 Surface Pro 4 や Surface Book などの Windows 10 タブレットをするため、新しい HoloLens アプリ Vuforia エンジンを使用することもできます。

## <a name="get-the-tools"></a>ツールの入手

[推奨されるバージョンをインストール](install-the-tools.md)の Visual Studio と Unity し、Visual Studio と優先 IDE およびコンパイラを使用する Unity を構成します。 

Unity をインストールするときに必ず、「Windows ストア .NET スクリプト バックエンド」または「Windows ストア il2cpp バック エンド Scripting バックエンド」のいずれかをインストールしてください。 また、「Vuforia 拡張現実サポート」Unity 内で Vuforia エンジンを有効にするを選択することを確認します。


## <a name="getting-started-with-vuforia-engine"></a>Vuforia エンジンの概要

Vuforia エンジンが Unity に内蔵されているために、開発者は、ダウンロードしたり、他のツールをインストールする必要はありません。 推奨されるバージョンの Unity は、LTS ストリームの現在位置 2017.3 あり Vuforia エンジン 7.0.57 が含まれています。 HoloLens で Vuforia エンジンを使用する方法の学習はでは、最適な開始点、 [Vuforia エンジン HoloLens サンプル](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553)(Unity Asset Store の使用可能)。 サンプルは、HoloLens をデプロイできる事前構成済みのシーンを含む完全な HoloLens プロジェクトを提供します。

バック グラウンドでは、Vuforia イメージのターゲットを使用してイメージを認識し、HoloLens の経験では、デジタル コンテンツを追加する方法を紹介します。 Unity と Vuforia のより新しいバージョンを使用している開発者では、HoloLens をターゲットのモデルの使用状況を示すシーンを含む更新されたサンプルにアクセスします。 Vuforia エンジンを使用している HoloLens アプリの作成を実験にシーンで独自のコンテンツを簡単に置き換えることができます。


## <a name="configuring-a-vuforia-app-for-hololens"></a>HoloLens の Vuforia アプリの構成

HoloLens の Vuforia エンジン アプリの開発は、その他のデバイス用アプリの Vuforia エンジン開発と同じでは根本的にします。 ビルド設定や以下のセクションで説明した構成を適用できます。 HoloLens 空間マッピングと連携してシステムを追跡位置指定 Vuforia エンジンを有効にするために必要なだけです。

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>ビルドおよび HoloLens の Vuforia エンジン サンプルを実行
1.  ダウンロード、 [HoloLens の Vuforia エンジン サンプル](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553)Unity Asset Store から
2.  適用、[能力とパフォーマンスの Unity エンジンのオプションをお勧めします。](performance-recommendations-for-unity.md)
3.  ビルド内のシーンには、サンプルのシーンを追加します。
4.  「ユニバーサル Windows プラットフォーム」のファイルで、プラットフォームのビルド ターゲットを設定 > ビルドの設定。
5.  次のプラットフォームのビルド構成設定を選択します。 
   * デバイスを対象に HoloLens を =
   * ビルドの種類 = D3D
   * SDK = 最新のインストール
   * Visual Studio のバージョン = 最新のインストール
   * ビルドおよび実行にローカル コンピューターを =
6.  一意の定義**製品名**で、**プレーヤー設定**HoloLens にインストールされているときのアプリの名前として使用します。
7.  確認**Vuforia 拡張現実**と**サポートされている仮想現実**で**プレーヤー設定 > XR の設定**
8.  また**XR 設定**、"Windows Mixed Reality"に追加されていることを確認、**仮想現実 Sdk**一覧
9.  Player の設定は次の機能を確認してください > 発行設定 
   * internetClient
   * WebCam
   * SpatialPerception - 画面オブザーバー API を使用する場合
10. Visual Studio プロジェクトを生成するビルドを選択します。
11. Visual Studio から実行可能ファイルをビルドし、インストール、HoloLens

注:モデル ターゲットの使用例を含むサンプル シーンにはバージョン 7.2、HoloLens の Vuforia エンジン サンプルが含まれています

## <a name="the-vuforia-developer-portal"></a>Vuforia デベロッパー ポータル

Vuforia エンジンと、独自の AR を作成する開発者のエクスペリエンスし、HoloLens は、Vuforia 開発者ポータルにサインアップする必要があります[developer.vuforia.com](https://developer.vuforia.com/)します。 開発者ポータルへのアクセスがある、 [Vuforia エンジン フォーラム](https://developer.vuforia.com/forum)コミュニティのディスカッションに参加することができますが、[ライブラリ](https://library.vuforia.com/)Vuforia エンジンのすべての機能と、に詳細なドキュメント[Vuforia ターゲット マネージャー](https://developer.vuforia.com/target-manager)ユーザーが独自のカスタム ターゲットを作成できます。 開発者が使用して無料の開発者ライセンスにサインアップできますも、 [Vuforia License Manager](https://developer.vuforia.com/license-manager)します。

## <a name="extended-tracking-with-vuforia"></a>拡張追跡 Vuforia を

[拡張追跡](https://library.vuforia.com/articles/Training/Extended-Tracking)ターゲットが表示が不要になった場合でもの追跡を維持するために、環境のマップを作成します。 HoloLens によって実行空間のマッピングに Vuforia エンジンの対応することをお勧めします。 ターゲットの拡張追跡を有効にすると、空間のマッピング システムに渡されるを対象の姿勢が有効にします。 これにより、ターゲットが同時にではなく、Vuforia エンジンと HoloLens 空間座標系で存在できます。

![Unity の設定 ウィンドウ](images/vuforia-extendedtracking.png)<br>
*Unity の設定 ウィンドウ*

**ターゲットの拡張追跡を有効にします。**

Vuforia エンジンでは、HoloLens 空間座標系に拡張追跡を使用するターゲットの姿勢を自動的に変換されます。 これにより、HoloLens の追跡、引き継ぎし、ターゲットの周囲の空間のマップに追加することのコンテンツを統合するためです。 このプロセスは Vuforia エンジンや複合現実では、Unity Api の間で発生し、開発者が任意のプログラミングは必要ありません - 自動的に処理されます。

**ここでは、何が発生しています.**
1. Vuforia のターゲットの追跡ツールは、ターゲットを認識します。
2. 追跡対象が初期化されます。
3. 位置とターゲットの回転は、HoloLens を使用するための堅牢な姿勢見積もりを提供する分析します。
4. Vuforia は、HoloLens 空間マッピングの座標空間に、ターゲットの姿勢を変換します。
5. HoloLens は追跡され、Vuforia トラッカーが非アクティブ化

開発者は、TargetBehaviour で拡張追跡を無効にして、Vuforia に制御を返すにこのプロセスを制御できます。

**注:** Vuforia 7.2 以降では、拡張追跡を無効とターゲットごとにします。 代わりに、開発者は、デバイスが、シーン内のすべてのターゲット上で同様の機能を有効にする追跡を有効にできます。


## <a name="see-also"></a>関連項目
* [ツールのインストール](install-the-tools.md)
* [座標系](coordinate-systems.md)
* [空間マッピング](spatial-mapping.md)
* [Unity のカメラ](camera-in-unity.md)
* [Unity Visual Studio ソリューションのエクスポートとビルド](exporting-and-building-a-unity-visual-studio-solution.md)
* [Vuforia ドキュメント:Unity での Windows 10 用の開発](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [Vuforia ドキュメント:Vuforia Unity 拡張機能をインストールする方法](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [Vuforia ドキュメント:Unity での HoloLens サンプルの使用](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [Vuforia ドキュメント:Vuforia で拡張追跡](https://library.vuforia.com/articles/Training/Extended-Tracking)
