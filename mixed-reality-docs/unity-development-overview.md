---
title: Unity 開発の概要
description: Unity での mixed reality アプリの構築の概要。
author: thetuvix
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, mixed reality, 開発, 作業の開始, 新しいプロジェクト, 移植, 機能, カメラ, シミュレーション, エミュレーション, ドキュメント
ms.openlocfilehash: b1384e886a2b4d0b3ed9f8008fca6af6ad4b78d5
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701790"
---
# <a name="unity-development-overview"></a>Unity 開発の概要

[Mixed reality アプリ](app-views.md)を構築する最速のパスは、 [Unity](http://aka.ms/HoloLensUnity)を使用することです。 [Unity のチュートリアル](https://unity3d.com/learn/tutorials)をご覧になることをお勧めします。 資産が必要な場合、Unity には包括的な[資産ストア](https://www.assetstore.unity3d.com/)があります。 Unity についての基本的な理解を構築したら、[チュートリアル](tutorials.md)にアクセスして unity を使用した mixed reality 開発の詳細を学習できます。 Unity で mixed reality アプリを構築するその他のコミュニティと連携するには、 [Unity Mixed reality フォーラム](http://forum.unity3d.com/forums/hololens.102/)にアクセスし、発生する可能性のある問題の解決策を見つけてください。

Unity を使用した mixed reality アプリの構築を開始するには、まず[ツールをインストール](install-the-tools.md)します。 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>Mixed Reality Toolkit を使用した新しい Unity プロジェクト 

Unity で開発する最も簡単な方法は、Mixed Reality Toolkit を使用することです。 これは、プロジェクトを自動的に設定し、開発を加速させる一連の mixed reality 機能を提供するのに役立ちます。 詳細については、「 [Mixed Reality Toolkit v2](mrtk-getting-started.md) 」をご覧ください。 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>既存の Unity アプリを Windows Mixed Reality に移植する

Windows Mixed Reality に移植している既存の Unity プロジェクトがある場合は、 [unity の移植](porting-guides.md)に関するガイドに従って作業を開始してください。

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>Windows Mixed Reality 用の新しい Unity プロジェクトの構成

混合 Reality ツールキットをインポートせずに新しい Unity プロジェクトを作成する場合は、Windows Mixed Reality で手動で変更する必要がある Unity 設定の小さなセットがあります。 これらは、プロジェクトごととシーン単位の2つのカテゴリに分類されます。 [Windows Mixed Reality 用の新しい Unity プロジェクトを構成](Configure-Unity-Project.md)するためのステップバイステップガイドについては、こちらをご覧ください

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Mixed reality 機能と入力の追加

プロジェクトで MRTK V2 を設定した後、または前述のようにプロジェクトを構成した後、標準 Unity ゲームオブジェクト (カメラなど) は、挿入された**スケールエクスペリエンス**のためにすぐに点灯します。カメラの位置は、ユーザーは、世界中を移動します。

[空間ステージ](coordinate-systems.md#spatial-coordinate-systems)、[ジェスチャ、モーションコントローラー](gestures-and-motion-controllers-in-unity.md) 、[音声入力](voice-input-in-unity.md)など、Windows Mixed Reality 機能のサポートを追加するには、Unity に直接組み込まれている api を使用します。 

まず、アプリケーションが対象とする[エクスペリエンススケール](coordinate-systems.md)を確認します。
* **向きのみ**または取り付けられた**スケールエクスペリエンス**を構築しようとしている場合は、Unity の追跡領域の種類を [[固定](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)] に設定する必要があります。
* 継続**スケール**または**ルームスケールのエクスペリエンス**を構築しようとしている場合は、Unity の追跡領域の種類が正常に[RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)に設定されていることを確認する必要があります。
* ユーザーが5メートルを超えてローミングできるようにするために、HoloLens で**世界規模**のエクスペリエンスを構築する場合は、 [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience)コンポーネントを使用する必要があります。

Mixed reality アプリケーションのすべてのコア構成要素は、他の Unity Api と一貫性のある方法で公開されます。 これらは、Mixed Reality Toolkit を通じて入手することもできます。
* [カメラ](camera-in-unity.md)
* [座標系](coordinate-systems-in-unity.md)
* [視線入力](gaze-in-unity.md)
* [ジェスチャとモーションコントローラー](gestures-and-motion-controllers-in-unity.md)
* [音声入力](voice-input-in-unity.md)
* [永続性](persistence-in-unity.md)
* [立体音響](spatial-sound-in-unity.md)
* [空間マッピング](spatial-mapping-in-unity.md)

Unity アプリにも公開されている多くの mixed reality アプリケーションでは、次のような重要な機能が使用されます。
* [共有エクスペリエンス](shared-experiences-in-unity.md)
* [場所を特定できるカメラ](locatable-camera-in-unity.md)
* [フォーカスポイント](focus-point-in-unity.md)
* [損失の追跡](tracking-loss-in-unity.md)
* [[キーボード]](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>実際のデバイスまたはシミュレートされたデバイスで Unity プロジェクトを実行する

Holographic Unity プロジェクトをテストする準備ができたら、次の手順として、 [Unity Visual Studio ソリューションをエクスポートしてビルド](exporting-and-building-a-unity-visual-studio-solution.md)します。

この VS ソリューションを使用すると、実際のデバイスまたはシミュレートされたデバイスのいずれかを使用して、次の3つの方法のいずれかでアプリケーションを実行できます。
* [Real HoloLens または Windows Mixed Reality の、イマーシブヘッドセットへのデプロイ](using-visual-studio.md)
* [HoloLens エミュレーターへのデプロイ](using-the-hololens-emulator.md)
* [Windows Mixed Reality のイマーシブヘッドセットシミュレーターにデプロイする](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Unity のドキュメント

Unity では、docs.microsoft.com で提供されているこのドキュメントに加えて、Unity エディターと共に Windows Mixed Reality 機能に関するドキュメントをインストールします。 Unity が提供するドキュメントには、次の2つのセクションがあります。
1. **Unity スクリプトリファレンス**
    * ドキュメントのこのセクションには、Unity が提供するスクリプト API の詳細が含まれています。
    * **ヘルプ > スクリプト参照**を使用して Unity エディターからアクセス可能
2. **Unity マニュアル**
    * このマニュアルは、基本的な手法から高度な手法まで、Unity の使用方法を学習できるように設計されています。
    * **ヘルプ > 手動**で、Unity エディターからアクセス可能

## <a name="see-also"></a>関連項目
* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [MR の基本 100:Unity の概要](holograms-100.md)
* [Unity で推奨される設定](recommended-settings-for-unity.md)
* [Unity のパフォーマンスに関する推奨事項](performance-recommendations-for-unity.md)
* [Unity Visual Studio ソリューションのエクスポートとビルド](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows 名前空間と HoloLens 用 Unity アプリの使用](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Unity と Visual Studio を使用するためのベスト プラクティス](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity の再生モード](unity-play-mode.md)
* [移植のガイド](porting-guides.md)
