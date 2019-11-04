---
title: Unity での Vuforia の使用
description: Unity で Vuforia を活用して、Windows Mixed Reality アプリケーションを構築します。
author: thetuvix
ms.author: alexturn
ms.date: 01/28/2019
ms.topic: article
keywords: Vuforia、マーカー、座標、参照のフレーム、追跡
ms.openlocfilehash: 0ab87a6262cbe74fd116fdc0a7045961bf8695d9
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437139"
---
# <a name="using-vuforia-engine-with-unity"></a>Unity での Vuforia Engine の使用

Vuforia Engine は HoloLens に重要な機能を提供します。これは、環境内の特定のイメージとオブジェクトに AR エクスペリエンスを接続するための機能です。 この機能を使用して、工業企業向けの機械の上にガイド付きの手順を重ねたり、物理的な製品やゲームにデジタル機能やエクスペリエンスを追加したりすることができます。 

AR エクスペリエンスを開発する際の柔軟性を高めるために、Vuforia Engine は幅広い機能とターゲットを提供しています。 Vuforia モデルターゲットである最新の機能の1つは、商用と工業の両方の主要な機能です。 モデルターゲットを使用すると、アプリケーションはコンピューター、自動車、または toys などの物理オブジェクトを認識し、CAD モデルまたはデジタル3D モデルに基づいて追跡できます。 工業用途では、この機能を使用することにより、アセンブリワーカーやサービス技術者は、ファクトリまたは現場での作業手順や手順に関するガイダンスを提供することができます。 

携帯電話やタブレット用に構築された既存の Vuforia エンジンアプリは、HoloLens で動作するように Unity で簡単に構成できます。 Vuforia Engine を使用して、新しい HoloLens アプリを Windows 10 タブレット (Surface Pro 4 や Surface ブックなど) に移動することもできます。

## <a name="get-the-tools"></a>ツールの入手

[推奨されるバージョン](install-the-tools.md)の visual Studio と Unity をインストールし、visual studio と優先する IDE およびコンパイラを使用するように unity を構成します。 

Unity をインストールする場合は、必ず "Windows ストア .NET Scripting バックエンド" または "Windows Store IL2CPP Scripting バックエンド" をインストールしてください。 また、Unity 内で Vuforia Engine を有効にするには、必ず "Vuforia 補強 Reality Support" を選択してください。


## <a name="getting-started-with-vuforia-engine"></a>Vuforia Engine の概要

Vuforia Engine は Unity に統合されているため、開発者は追加のツールをダウンロードしたりインストールしたりする必要はありません。 Unity の推奨バージョンは、現在2017.3 にあり、Vuforia Engine 7.0.57 を含む LTS ストリームです。 Vuforia Engine を HoloLens で使用する方法について学習するための最適な出発点は、 [Vuforia Engine HoloLens サンプル](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553)(Unity 資産ストアで入手可能) を使用することです。 このサンプルには、HoloLens にデプロイできる事前構成済みのシーンを含む完全な HoloLens プロジェクトが用意されています。

このシーンでは、Vuforia イメージターゲットを使用してイメージを認識し、HoloLens エクスペリエンスでデジタルコンテンツを使用してイメージを拡張する方法を示します。 新しいバージョンの Unity と Vuforia を使用している開発者は、HoloLens でのモデルターゲットの使用状況を示すシーンを含む更新されたサンプルにアクセスできます。 独自のコンテンツを使用して、Vuforia Engine を使用する HoloLens アプリの作成を試すことができます。


## <a name="configuring-a-vuforia-app-for-hololens"></a>HoloLens 用の Vuforia アプリの構成

HoloLens 用の Vuforia Engine アプリの開発は、他のデバイス用の Vuforia Engine アプリの開発と基本的に同じです。 次に、以下のセクションで説明するビルド設定と構成を適用できます。 Vuforia Engine が HoloLens 空間マッピングおよび位置追跡システムと連携できるようにするために必要な操作はこれだけです。

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>HoloLens 用 Vuforia Engine サンプルをビルドして実行する
1.  Unity 資産ストアから[HoloLens 用の Vuforia Engine サンプル](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553)をダウンロードする
2.  [Power and performance に推奨される Unity エンジンオプション](performance-recommendations-for-unity.md)を適用する
3.  ビルドのシーンにサンプルシーンを追加します。
4.  ファイル > ビルド設定の "ユニバーサル Windows プラットフォーム" のプラットフォームビルドターゲットを設定します。
5.  次のプラットフォームビルド構成設定を選択します。 
   * ターゲットデバイス = HoloLens
   * ビルドの種類 = D3D
   * SDK = 最新のインストール
   * Visual Studio バージョン = 最新インストール済み
   * ビルドして実行する = ローカルコンピューター
6.  HoloLens にインストールするときにアプリの名前として機能する一意の**製品名**を **[プレーヤーの設定]** で定義します。
7.  **プレーヤー設定 > XR 設定**で**サポートされている** **Vuforia 拡張現実**と仮想現実を確認する
8.  また、 **[XR の設定]** で、Windows Mixed reality が  **[Virtual Reality sdk]** の一覧に追加されていることを確認します。
9.  プレーヤーの設定 > 発行設定で次の機能を確認します。 
   * InternetClient
   * WebCam
   * SpatialPerception-Surface オブザーバー API を使用する場合
10. [ビルド] を選択して Visual Studio プロジェクトを生成します
11. Visual Studio から実行可能ファイルをビルドし、HoloLens にインストールする

注: バージョン7.2 以降、HoloLens の Vuforia Engine サンプルには、モデルターゲットの使用例を含むサンプルシーンが含まれています。

## <a name="the-vuforia-developer-portal"></a>Vuforia 開発者ポータル

Vuforia Engine と HoloLens で独自の AR エクスペリエンスを作成しようとしている開発者は、 [developer.vuforia.com](https://developer.vuforia.com/)の Vuforia 開発者ポータルでサインアップする必要があります。 ポータルでは、開発者は[Vuforia Engine フォーラム](https://developer.vuforia.com/forum)にアクセスできます。このフォーラムでは、コミュニティディスカッションに参加できます。[ライブラリ](https://library.vuforia.com/)には、すべての Vuforia Engine 機能に関する詳細なドキュメントが含まれています。また、 [Vuforia Target Manager](https://developer.vuforia.com/target-manager)を使用してユーザーが独自のカスタムターゲットを作成します。 開発者は、 [Vuforia License Manager](https://developer.vuforia.com/license-manager)を使用して無料の開発者ライセンスにサインアップすることもできます。

## <a name="extended-tracking-with-vuforia"></a>Vuforia を使用した拡張追跡

[拡張追跡](https://library.vuforia.com/articles/Training/Extended-Tracking)は、ターゲットがビューに存在しなくなった場合でも、追跡を維持する環境のマップを作成します。 Vuforia エンジンは、HoloLens によって実行される空間マッピングに相当します。 ターゲットで拡張追跡を有効にすると、そのターゲットが空間マッピングシステムに渡されるようにすることができます。 このようにして、Vuforia Engine システムと HoloLens 空間座標系の両方にターゲットを同時に配置することはできません。

![Unity の設定 ウィンドウ](images/vuforia-extendedtracking.png)<br>
*Unity の設定ウィンドウ*

**ターゲットでの拡張追跡の有効化**

Vuforia Engine は、拡張追跡を使用するターゲットのポーズを HoloLens 空間座標系に自動的に変換します。 これにより、HoloLens は追跡を引き継ぎ、コンテンツの補強をターゲットの環境の空間マッピングに統合できます。 このプロセスは、Unity の Vuforia Engine と mixed reality Api の間で発生し、開発者によるプログラミングは必要ありません。自動的に処理されます。

**次のような処理が行われます。**
1. Vuforia のターゲットトラッカーはターゲットを認識します
2. 次に、ターゲットの追跡を初期化します。
3. ターゲットの位置と回転を分析して、HoloLens が使用する堅牢な予測を提供します。
4. Vuforia は、ターゲットの原因を HoloLens 空間マッピングの座標空間に変換します。
5. HoloLens が追跡を引き継ぎ、Vuforia tracker が非アクティブ化される

開発者は、TargetBehaviour の拡張追跡を無効にすることによって、このプロセスを制御して、制御を Vuforia に返すことができます。

**注:** Vuforia 7.2 以降では、拡張追跡はターゲットごとに有効になりません。 代わりに、開発者はデバイスの追跡を有効にして、シーン内のすべてのターゲットで同様の機能を有効にすることができます。


## <a name="see-also"></a>関連項目
* [ツールのインストール](install-the-tools.md)
* [座標系](coordinate-systems.md)
* [空間マッピング](spatial-mapping.md)
* [Unity のカメラ](camera-in-unity.md)
* [Unity Visual Studio ソリューションのエクスポートとビルド](exporting-and-building-a-unity-visual-studio-solution.md)
* [Vuforia のドキュメント: Unity での Windows 10 向けの開発](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [Vuforia のドキュメント: Vuforia Unity 拡張機能のインストール方法](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [Vuforia のドキュメント: Unity での HoloLens サンプルの使用](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [Vuforia のドキュメント: Vuforia の拡張追跡](https://library.vuforia.com/articles/Training/Extended-Tracking)
