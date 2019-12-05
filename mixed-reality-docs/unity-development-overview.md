---
title: Unity 開発の概要
description: Unity で Mixed Reality アプリのビルドを開始します。
author: thetuvix
ms.author: kurtie
ms.date: 10/25/2018
ms.topic: article
ms.localizationpriority: high
keywords: Unity, Mixed Reality, 開発, 概要, 新しいプロジェクト, 移植, 機能, カメラ, シミュレーション, エミュレーション, ドキュメント
ms.openlocfilehash: 23b3d9a3fe419911e774722a7d2db6809c2955cf
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491096"
---
# <a name="unity-development-overview"></a>Unity 開発の概要

[Mixed Reality アプリ](app-views.md)を構築する最速の方法は、[Unity](https://unity.com) を使用することです。 時間を取って、[Unity のチュートリアル](https://unity3d.com/learn/tutorials)をご覧になることをお勧めします。 資産が必要な場合、Unity には包括的な[資産ストア](https://www.assetstore.unity3d.com/)があります。 Unity についての基本的な理解ができたら、[チュートリアル](tutorials.md)にアクセスして、Unity を使用した Mixed Reality 開発の詳細を確認できます。 [Unity Mixed Reality フォーラム](https://forum.unity3d.com/forums/hololens.102/)にアクセスして、Unity で Mixed Reality アプリを構築する他のコミュニティと協働し、遭遇しがちな問題の解決策を見つけてください。

Unity を使用して Mixed Reality アプリの構築を開始するには、まず、[ツールをインストール](install-the-tools.md)します。 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>Mixed Reality Toolkit による新しい Unity プロジェクト 

Unity で開発する場合の最も簡単な方法は、Mixed Reality Toolkit を使用することです。 これにより、プロジェクトでの設定を自動的に行い、一連の Mixed Reality 機能を提供して開発を促進できます。 詳細を確認して使い始めるには、[Mixed Reality Toolkit v2](mrtk-getting-started.md) に関する記事をご覧ください。 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>既存の Unity アプリを Windows Mixed Reality に移植する

Windows Mixed Reality への移植を予定している既存の Unity プロジェクトがある場合は、[Unity 移植ガイド](porting-guides.md)に従って作業を開始してください。

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>Windows Mixed Reality 用に新しい Unity プロジェクトを構成する

Mixed Reality Toolkit をインポートせずに新しい Unity プロジェクトを作成する場合には、Windows Mixed Reality 用に手動で変更する必要がある小規模な Unity 設定のセットがあります。 これらは、プロジェクトごととシーンごとの 2 つのカテゴリに分類されます。 ステップ バイ ステップ ガイドについては、こちらの「[Windows Mixed Reality 用の新しい Unity プロジェクトを構成する](Configure-Unity-Project.md)」を参照してください。

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Mixed Reality の機能と入力値を追加する

プロジェクトに MRTK V2 をセットアップするか、前述のようにプロジェクトを構成したら、標準の Unity ゲーム オブジェクト (カメラなど) が **座位のエクスペリエンス**に対応してすぐに点灯します。ユーザーが頭を移動すると、カメラの位置が自動的に更新されます。

Unity に直接組み込まれている API を使用して、[空間ステージ](coordinate-systems.md#spatial-coordinate-systems)、[ジェスチャ、モーション コントローラー](gestures-and-motion-controllers-in-unity.md)、[音声入力](voice-input-in-unity.md)など、Windows Mixed Reality 機能のサポートを追加できます。 

まず、お使いのアプリケーションが対象にできる[エクスペリエンスのスケール](coordinate-systems.md)を確認します。
* **向き限定**や**座位のエクスペリエンス**を構築する場合は、Unity 上で追跡する空間の種類を [[ひな形]](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) に設定する必要があります。
* **立位**または**空間スケールのエクスペリエンス**を構築する場合は、Unity 上で追跡する空間の種類を確実に [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) に設定する必要があります。
* ユーザーが 5 メートルを超えてローミングできるようにする**ワールドスケール**のエクスペリエンスを HoloLens 上で構築する場合は、[WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) コンポーネントを使用する必要があります。

Mixed Reality アプリケーションのコアな構成要素はすべて、他の Unity API と一貫した手法で公開されています。 また、Mixed Reality Toolkit を通じて入手することもできます。
* [カメラ](camera-in-unity.md)
* [座標系](coordinate-systems-in-unity.md)
* [視線入力](gaze-in-unity.md)
* [ジェスチャとモーション コントローラー](gestures-and-motion-controllers-in-unity.md)
* [音声入力](voice-input-in-unity.md)
* [永続化](persistence-in-unity.md)
* [立体音響](spatial-sound-in-unity.md)
* [空間マッピング](spatial-mapping-in-unity.md)

以下に示す、多くの Mixed Reality アプリケーション上で使用される他の重要な機能も、Unity アプリに公開されています。
* [共有エクスペリエンス](shared-experiences-in-unity.md)
* [場所を特定できるカメラ](locatable-camera-in-unity.md)
* [フォーカス ポイント](focus-point-in-unity.md)
* [追跡の損失](tracking-loss-in-unity.md)
* [キーボード](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>実際のデバイスまたはシミュレートされたデバイス上で Unity プロジェクトを実行する

ホログラフィック Unity プロジェクトをテストする準備ができたら、次の手順として、[Unity Visual Studio ソリューションをエクスポートしてビルド](exporting-and-building-a-unity-visual-studio-solution.md)します。

その VS ソリューションが手元にあれば、実際のデバイスまたはシミュレートされたデバイスのどちらかを使用して、次の 3 つの方法のいずかでアプリケーションを実行できます。
* [実際の HoloLens または Windows Mixed Reality イマーシブ ヘッドセットにデプロイする](using-visual-studio.md)
* [HoloLens エミュレーターにデプロイする](using-the-hololens-emulator.md)
* [Windows Mixed Reality イマーシブ ヘッドセット シミュレーターにデプロイする](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Unity のドキュメント

このドキュメントは docs.microsoft.com 上で入手できますが、Unity では、Windows Mixed Reality 機能に関するドキュメントが Unity エディターと共にインストールされます。 Unity が提供するドキュメントには、次の 2 つのセクションがあります。
1. **Unity スクリプト リファレンス**
    * ドキュメントのこのセクションには、Unity が提供するスクリプト作成 API の詳細が含まれています。
    * **[ヘルプ] > [Scripting Reference]\(スクリプト作成のリファレンス\)**  を使用して、Unity エディターからアクセス可能です
2. **Unity マニュアル**
    * このマニュアルは、基本的な手法から高度な手法まで、Unity の使用方法を学習できるように編成されています。
    * **[ヘルプ] > [マニュアル]** を使用して、Unity エディターからアクセス可能です

## <a name="see-also"></a>関連項目
* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [MR の基本 100:Unity の概要](holograms-100.md)
* [Unity で推奨される設定](recommended-settings-for-unity.md)
* [Unity のパフォーマンスに関する推奨事項](performance-recommendations-for-unity.md)
* [Unity Visual Studio ソリューションのエクスポートとビルド](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows 名前空間と HoloLens 用 Unity アプリの使用](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Unity と Visual Studio を使用するためのベスト プラクティス](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity の再生モード](unity-play-mode.md)
* [移植ガイド](porting-guides.md)
