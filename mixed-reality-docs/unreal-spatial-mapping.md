---
title: Unreal での空間マッピング
description: Unreal で空間マッピングを使用するためのガイド
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, 空間マッピング
ms.openlocfilehash: 32f8247010745b23bf73c5161c378bc1284169ef
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840081"
---
# <a name="spatial-mapping-in-unreal"></a>Unreal での空間マッピング

HoloLens で空間マッピングを有効にするには、[プロジェクト設定] > [プラットフォーム] > [HoloLens] > [機能] の下にある Unreal エディターで、"空間認識" 機能を確実にオンにします。  

HoloLens ゲームで空間マッピングの使用をオプトインするには、ARSessionConfig で [Generate Mesh Data from Tracked Geometry]\(追跡されたジオメトリからメッシュ データを生成する\) を有効にします。  これで、HoloLens プラグインが、空間マッピング データを非同期的に取得し、MRMesh を介してそのデータを Unreal に表示します。 

![空間アンカー ストア準備完了](images/unreal-spatialmapping-arsettings.PNG)

空間マッピング メッシュのデバッグ視覚エフェクトを表示するには、ARSessionConfig の [Render Mesh Data in Wireframe]\(ワイヤーフレームでメッシュ データをレンダリングする\) チェックボックスをオンにして、MRMesh 内のすべての三角形の白いワイヤーフレームのアウトラインを表示します。 

[プロジェクト設定] > [プラットフォーム] > [HoloLens] > [空間マッピング] で、次のパラメーターを変更すると、空間マッピングの実行時の動作を更新できます。 

![空間アンカーのプロジェクト設定](images/unreal-spatialmapping-projectsettings.PNG)

[Max Triangles Per Cubic Meter]\(立方メートルあたりの最大三角形数\) で、空間マッピング メッシュの三角形の密度が更新されます。  [Spatial Meshing Volume Size]\(空間メッシュのボリューム サイズ\) は、空間マッピング データをレンダリングおよび更新するための、プレーヤー周りのキューブのサイズを示します。  予想されるアプリケーションの実行時環境が大きくなると思われる場合は、このフィールドを現実世界のスペースに合わせて大きくしなければならない場合があります。  逆に、アプリケーションでユーザーの周囲の表面にホログラムを配置するだけであれば、このフィールドを小さくすることができます。  ユーザーが移動するにつれて、空間マッピングのボリュームも移動します。 

実行時に MRMesh にアクセスするには、最初に、ブループリント アクターに AR Trackable Notify コンポーネントを追加します。 

![空間アンカーの AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

次に、コンポーネントの詳細にアクセスし、監視するイベントの緑色の [+] ボタンをクリックします。 

![空間アンカーのイベント](images/unreal-spatialmapping-events.PNG)

この場合は、[On Add Tracked Geometry]\(追跡ジオメトリの追加\) のイベントを監視し、空間マッピング データに対応する有効なワールド メッシュを探し、メッシュの素材を変更します。 

![空間アンカーの例](images/unreal-spatialmapping-example.PNG)

C++ では、OnTrackableAdded デリゲートをサブスクライブして、使用可能になったらすぐに ARTrackedGeometry を取得することができます。  更新および削除されたイベントでも、類似のデリゲートがあります。AddOnTrackableUpdatedDelegate_Handle と AddOnTrackableRemovedDelegate_Handle です。 

![空間アンカーの例の C++ コード](images/unreal-spatialmapping-examplecode.PNG)

"ARBlueprintLibrary.h" および "MRMesh" をインクルードして MRMesh の UARTrackedGeometry コンポーネントを検査するには、プロジェクトの build.cs に、PublicDependencyModuleNames リストの "AugmentedReality" が含まれている必要があります。 

空間マッピングは、ARTrackedGeometries によって表示される唯一の種類のデータではないので、まずは、EARObjectClassification が World であることを確認します。これは、それが空間マッピング ジオメトリであることを示します。 

## <a name="see-also"></a>関連項目
* [空間マッピング](spatial-mapping.md)
