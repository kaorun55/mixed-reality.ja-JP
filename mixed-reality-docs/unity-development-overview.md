---
title: Unity 開発の概要
description: 構築の作業開始の複合現実アプリ Unity でします。
author: thetuvix
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity では、実際には、開発、作業の開始、新しいプロジェクト、移植、機能、カメラ、シミュレーション、エミュレーション、ドキュメントの混在
ms.openlocfilehash: 24217b4c61bf2d438ebc1c4114bc9dc20dc62f64
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414521"
---
# <a name="unity-development-overview"></a>Unity 開発の概要

最も高速パスのビルド方法、 [mixed reality アプリ](app-views.md)は[Unity](http://aka.ms/HoloLensUnity)。 調査に時間がかかることをお勧め、 [Unity チュートリアル](https://unity3d.com/learn/tutorials)します。 Unity が包括的で資産が必要な場合[Asset Store](https://www.assetstore.unity3d.com/)します。 アクセスすることができます、Unity の基本的な知識を蓄積した後、[チュートリアル](tutorials.md)を Unity での複合現実開発の詳細を参照してください。 参照してください、 [Unity Mixed Reality フォーラム](http://forum.unity3d.com/forums/hololens.102/)が発生する問題の解決策を見つけて、コミュニティの構築、Unity での複合現実アプリの残りの部分とかかわります。


まず、Unity を使用した複合現実アプリの構築を開始する[ツールをインストールする](install-the-tools.md)します。 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>Mixed Reality ツールキットを使用して新しい Unity プロジェクト 

Unity での開発に最も簡単な方法は、Mixed Reality ツールキットのヘルプです。 プロジェクトのセットアップのヘルプを自動的に、一連の開発を促進する複合現実の機能が提供されます。 チェック アウトしてください[Mixed Reality Toolkit v2](mrtk-getting-started.md)詳細と開始します。 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Windows Mixed Reality への既存の Unity アプリの移植

Windows Mixed Reality を移植する既存の Unity プロジェクトを使用する場合はと共にに従って、 [Unity 移植のガイド](porting-guides.md)を開始します。

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>新しい Unity プロジェクトを Windows Mixed Reality の構成

Mixed Reality ツールキットをインポートせず、新しい Unity プロジェクトを作成したい場合は、少数の Unity の設定が Windows Mixed Reality を手動で変更する必要があります。 2 つのカテゴリに分かれています。 プロジェクトごとおよびシーンごと。 ステップ バイ ステップ ガイドについてはこちらを参照してください[新しい Unity プロジェクトの Windows Mixed Reality を構成する。](Configure-Unity-Project.md)

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>複合現実の機能および入力の追加

プロジェクトとセットアップ MRTK V2 をしたか、前述のように、プロジェクトを構成すると、(カメラ) などの標準の Unity ゲーム オブジェクトが点灯直後の**取り付けられているスケール エクスペリエンス**カメラの位置を更新自動的にユーザーとして、世界中から自分の頭に移動します。

Windows Mixed Reality の機能のサポートを追加するなど、[空間ステージ](coordinate-systems.md#spatial-coordinate-systems)、[ジェスチャ、モーションのコント ローラー](gestures-and-motion-controllers-in-unity.md)または[音声入力](voice-input-in-unity.md)に直接組み込まれている Api を使用して実現されますUnity です。 

最初に、確認、[スケールが発生する](coordinate-systems.md)applicatioin を対象とします。
* ビルドに必要な場合、**向き専用**または**取り付けられているスケール エクスペリエンス**、設定する必要があります Unity に領域の種類の追跡の[静止](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。
* ビルドに必要な場合、**継続スケール**または**ルーム スケール エクスペリエンス**、Unity のことを確認する必要がありますに正常に設定されて領域の種類を追跡[RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)します。
* ビルドに必要な場合、**世界規模**エクスペリエンスでユーザーが 5 m を超えるローミングできる HoloLens、使用する必要があります、 [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience)コンポーネント。

すべての複合現実のアプリケーション用のコア ビルディング ブロックは、その他の Unity Api を使用した一貫性のある方法で公開されます。 Mixed Reality Toolkit を使用します。
* [カメラ](camera-in-unity.md)
* [座標系](coordinate-systems-in-unity.md)
* [視線入力](gaze-in-unity.md)
* [ジェスチャとアニメーション コント ローラー](gestures-and-motion-controllers-in-unity.md)
* [音声入力](voice-input-in-unity.md)
* [永続化](persistence-in-unity.md)
* [立体音響](spatial-sound-in-unity.md)
* [空間マッピング](spatial-mapping-in-unity.md)

その他のキーの機能が多く、複合現実には、アプリケーションを使用する Unity アプリにも公開されています。
* [共有エクスペリエンス](shared-experiences-in-unity.md)
* [場所を特定できるカメラ](locatable-camera-in-unity.md)
* [フォーカス ポイント](focus-point-in-unity.md)
* [損失の追跡](tracking-loss-in-unity.md)
* [[キーボード]](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>実際、またはシミュレートされたデバイスで Unity プロジェクトを実行しています。

次の手順はようになったら、holographic の Unity プロジェクトをテストするための準備ができて、[をエクスポートし、Unity Visual Studio ソリューションをビルド](exporting-and-building-a-unity-visual-studio-solution.md)。

手の形でその VS ソリューションとできますし、アプリケーションを実行する 3 つの方法のいずれかでいずれかを使用して実際またはシミュレーション上のデバイス。
* [実際 HoloLens や Windows Mixed Reality イマーシブ ヘッドセットを展開します。](using-visual-studio.md)
* [HoloLens のエミュレーターへのデプロイします。](using-the-hololens-emulator.md)
* [Windows Mixed Reality イマーシブ ヘッドセット シミュレーターへのデプロイします。](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Unity のドキュメント

このドキュメントの他使用可能な Windows デベロッパー センターでは、Unity は Unity エディターと共に Windows Mixed Reality 機能のドキュメントをインストールします。 Unity のドキュメントには、2 つのセクションが含まれています。 提供されています。
1. **Unity スクリプトのリファレンス**
    * ドキュメントのこのセクションには、Unity が提供するスクリプト API の詳細が含まれています。
    * Unity エディターからを通じてアクセス可能な**ヘルプ > スクリプトのリファレンス**
2. **Unity マニュアル**
    * このマニュアルは、高度な基本的な手法から Unity を使用する方法を学習するために設計されています。
    * Unity エディターからを通じてアクセス可能な**ヘルプ > 手動**

## <a name="see-also"></a>関連項目
* [複合現実 Toolkit v2](mrtk-getting-started.md)
* [MR の基本 100:Unity の概要](holograms-100.md)
* [Unity で推奨される設定](recommended-settings-for-unity.md)
* [Unity のパフォーマンスに関する推奨事項](performance-recommendations-for-unity.md)
* [Unity Visual Studio ソリューションのエクスポートとビルド](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows 名前空間と HoloLens 用 Unity アプリの使用](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Unity と Visual Studio を使用するためのベスト プラクティス](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity の再生モード](unity-play-mode.md)
* [移植のガイド](porting-guides.md)
