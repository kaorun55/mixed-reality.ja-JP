---
title: 3D アプリ ランチャー (UWP アプリ) の実装します。
description: HoloLens と没入型の (VR) ヘッドセットの両方で 3D アプリ ランチャーと Windows Mixed Reality UWP アプリとゲーム (Microsoft Store を介して配布)、ロゴを作成する方法。
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D、ロゴ、アイコン、モデリング、ランチャー、3D ランチャー、タイル、ライブのキューブ、ディープ リンク、secondarytile、UWP、セカンダリ タイル
ms.openlocfilehash: 4a8d4a696ff6ef19d7332b20580f1f5ee67bf045
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604858"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a>3D アプリ ランチャー (UWP アプリ) の実装します。

> [!NOTE]
> この機能は、イマーシブ ヘッドセットの 2017 の Fall Creators Update (RS3) の一部としてが追加され、HoloLens と Windows ではサポートされて 10 April 2018 Update。 アプリケーションには、イマーシブ ヘッドセットで 10.0.16299 以上 10.0.17125 HoloLens では、Windows SDK のバージョンが対象とすることを確認します。 最新の Windows SDK を検索する[ここ](https://developer.microsoft.com/windows/downloads/windows-10-sdk)します。

[Windows Mixed Reality ホーム](navigating-the-windows-mixed-reality-home.md)始めるユーザーがアプリケーションを起動する前に配置する場所です。 Windows Mixed Reality の UWP アプリケーションを作成する、既定では、そのアプリのロゴで 2D スレートとしてアプリが起動されます。 Windows Mixed Reality のエクスペリエンスを開発する際に 3D ランチャーは、アプリケーションの既定の 2D ランチャーをオーバーライドする必要に応じて定義できます。 一般に、ランチャーが 3D がインプレース アクティブ化されると、アプリは、既定の 2D ランチャーは優先のユーザーからホーム Windows Mixed Reality を取る没入型アプリケーションを起動するためお勧めします。 作成することも、 [3D ディープ リンク (secondaryTile)](#3d-deep-links-secondarytiles) 2D の UWP アプリ内のコンテンツへの 3D ランチャーとして。

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>3D アプリ起動ツールの作成プロセス

3D アプリ起動ツールを作成する 3 つの手順があります。
1. [デザインと concepting](3d-app-launcher-design-guidance.md)
2. [モデリングとエクスポート](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. (この記事)、アプリケーションに統合します。

3D アセットを使用して、アプリケーションの起動ツールを作成する必要がありますとして使用する、[ガイドラインの authoring Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)互換性を確保します。 このオーサリングの仕様を満たすために失敗した資産は、ホーム Windows Mixed Reality ではレンダリングされません。

## <a name="configuring-the-3d-launcher"></a>3D の起動ツールを構成します。

Visual Studio で新しいプロジェクトを作成すると、アプリの名前とロゴを表示する単純な既定のタイルが作成されます。 この 2D を置き換えるには、カスタムの 3D モデルで表現は、"MixedRealityModel"要素を既定のタイルの定義の一部として含める、アプリケーションのアプリケーション マニフェストを編集します。 だけランチャーは 2D に戻すには、マニフェストから MixedRealityModel 定義を削除します。

### <a name="xml"></a>XML

最初に、現在のプロジェクトで、アプリ パッケージのマニフェストを見つけます。 既定では、マニフェストの Package.appxmanifest を名前されるは。 Visual Studio を使用している場合は、ソリューション エクスプ ローラーで、マニフェストを右クリックし、選択**ソースの表示**を編集するための xml を開きます。 

マニフェストの上部にある uap5 スキーマを追加し、無視できる名前空間として含めます。

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

次に、アプリケーションの既定のタイルに"MixedRealityModel"を指定します。

```xml
<Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="ExampleApp.App">
      <uap:VisualElements
        DisplayName="ExampleApp"
        Square150x150Logo="Assets\Logo.png"
        Square44x44Logo="Assets\SmallLogo.png"
        Description="ExampleApp"
        BackgroundColor="#464646">
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb" />
        </uap:DefaultTile>
        <uap:SplashScreen Image="Assets\SplashScreen.png" />
      </uap:VisualElements>
    </Application>
</Applications>
```

MixedRealityModel 要素は、アプリ パッケージに格納されている 3D 資産へのファイル パスを受け入れます。 のみの 3D モデルが現在 .glb ファイル形式を使用して配信され、に対して作成される、 [Windows Mixed Reality 3D アセットの作成手順については](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)はサポートされています。 資産は、アプリ パッケージに格納する必要があり、アニメーションが現在サポートされていません。 "Path"パラメーターが空白の場合、Windows は 3D ランチャーではなく 2D スレートを表示します。 **注:** .glb 資産としてマークされる必要「コンテンツ」のビルド設定でのビルドと、アプリを実行する前にします。


![ソリューション エクスプ ローラーで、.glb を選択し、[プロパティ] セクションを使用して、ビルド設定で"Content"としてマーク](images/buildsetting-content-300px.png)<br>
*ソリューション エクスプ ローラーで、.glb を選択し、[プロパティ] セクションを使用して、ビルド設定で"Content"としてマーク*

### <a name="bounding-box"></a>境界ボックス

必要に応じて、オブジェクトの周囲の追加のバッファー領域を追加する、境界ボックスを使用できます。 境界ボックスは、中心点と、境界ボックスの中央から各軸に沿った端までの距離を示すエクステントを使用して指定します。 境界ボックスのユニットを 1 ユニットにマップすることができます = 1 メートルです。 境界ボックスが指定されていない場合、1 つは自動的に格納オブジェクトのメッシュに。 指定された境界ボックスは、モデルよりも小さい場合は、メッシュに合わせてに変更されます。

境界ボックスの属性のサポートが付属 RS4 の Windows 更新プログラムをプロパティとして MixedRealityModel 要素。 最初に、アプリの上部にある境界ボックスを定義するマニフェストが uap6 スキーマを追加し、そのを含める無視できない名前空間として。

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
次に、MixedRealityModel 上には、境界ボックスを定義する SpatialBoundingBox プロパティを設定します。 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>Unity を使用します。

Unity を使用する場合、プロジェクトのビルドし、アプリケーション マニフェストを編集する前に、Visual Studio で開く必要があります。 

>[!NOTE]
>3D の起動ツールは、ビルド、および Unity からの新しい Visual Studio ソリューションを展開するときに、マニフェストで再定義する必要があります。

## <a name="3d-deep-links-secondarytiles"></a>3D のディープ リンク (secondaryTiles)

> [!NOTE]
> (VR) のイマーシブ ヘッドセットの 2017 の Fall Creators Update (RS3) の一部として、2018 年 4 月の一部として、この機能は追加された HoloLens 用の更新プログラム (RS4)。 アプリケーションが (VR) のイマーシブ ヘッドセットで 10.0.16299 以上 10.0.17125 HoloLens での Windows SDK のバージョンを対象とすることを確認します。 最新の Windows SDK を検索する[ここ](https://developer.microsoft.com/windows/downloads/windows-10-sdk)します。

>[!IMPORTANT]
>3D のディープ リンク (secondaryTiles) は、2 D の UWP アプリでのみ機能します。 ただし、作成することができます、 [3D アプリ起動ツール](implementing-3d-app-launchers.md)ホーム Windows Mixed Reality から排他のアプリを起動します。

アプリからの 3D モデルを配置する機能を追加することによって Windows Mixed Reality を 2D アプリケーションを強化できる、 [Windows Mixed Reality ホーム](navigating-the-windows-mixed-reality-home.md)2D アプリ内のコンテンツにディープ リンクとしてと同じように[2D セカンダリタイル](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles)Windows [スタート] メニュー。 たとえば、360 ° のフォト ビューアー アプリに直接リンクまたはユーザーが作成者についての詳細ページに表示された資産のコレクションから 3D コンテンツを配置できるようにする 360 ° photospheres を作成できます。 これらは、3 D コンテンツを使用して 2D のアプリケーションの機能を拡張する、いくつかの方法です。

### <a name="creating-a-3d-secondarytile"></a>3D"secondaryTile"を作成します。

作成時に、複合現実のモデルを定義することで"secondaryTiles"を使用して、アプリケーションからは、3 D コンテンツを配置できます。 複合現実のモデルは、アプリ パッケージ内の 3D アセットを参照して、必要に応じて境界ボックスを定義して作成されます。 

> [!NOTE]
> 排他のビュー内からの"secondaryTiles"の作成は現在サポートされていません。

```cs
using Windows.UI.StartScreen;
using Windows.Foundation.Numerics;
using Windows.Perception.Spatial;

// Initialize the tile
SecondaryTile tile = new SecondaryTile("myTileId")
{
    DisplayName = "My Tile",
    Arguments = "myArgs"
};

tile.VisualElements.Square150x150Logo = new Uri("ms-appx:///Assets/MyTile/Square150x150Logo.png");

//Assign 3D model (only ms-appx and ms-appdata are allowed)
TileMixedRealityModel model = tile.VisualElements.MixedRealityModel;
model.Uri = new Uri("ms-appx:///Assets/MyTile/MixedRealityModel.glb");
model.ActivationBehavior = TileMixedRealityModelActivationBehavior.Default;
model.BoundingBox = new SpatialBoundingBox
{
    Center = new Vector3 { X = 1, Y = 0, Z = 0 },
    Extents = new Vector3 { X = 3, Y = 5, Z = 4 }
};

// And place it
await tile.RequestCreateAsync();
```

### <a name="bounding-box"></a>境界ボックス

オブジェクトの周囲、追加のバッファー領域を追加するのには、境界ボックスを使用できます。 境界ボックスは、中心点と、境界ボックスの中央から各軸に沿った端までの距離を示すエクステントを使用して指定します。 境界ボックスのユニットを 1 ユニットにマップすることができます = 1 メートルです。 境界ボックスが指定されていない場合、1 つは自動的に格納オブジェクトのメッシュに。 指定された境界ボックスは、モデルよりも小さい場合は、メッシュに合わせてに変更されます。

### <a name="activation-behavior"></a>アクティブ化の動作

> [!NOTE]
> この機能はサポートされている Windows RS4 更新の時点でします。 この機能を使用する場合、アプリケーションは 10.0.17125 以上の Windows SDK のバージョンを対象とするかどうかを確認します。

ユーザーに選択するときの反応を制御する 3D secondaryTile のアクティブ化の動作を定義できます。 これは、複合現実でホーム purley 有益または装飾用である 3D オブジェクトを配置に使用できます。 次のライセンス認証の動作の種類がサポートされています。
1. 既定:アプリがアクティブにユーザーが 3D の secondaryTile を選択
2. None:ユーザーが何も起こりません 3D secondaryTile とアプリを選択すると、アクティブ化されません。

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>取得して、既存の"secondaryTile"を更新しています

開発者は、バックアップ以前に指定するプロパティが含まれる、既存のセカンダリ タイルの一覧を取得できます。 値を変更して、UpdateAsync() を呼び出すことによって、プロパティを更新することもできます。

```cs
// Grab the existing secondary tile
SecondaryTile tile = (await SecondaryTile.FindAllAsync()).First();

Uri updatedUri = new Uri("ms-appdata:///local/MixedRealityUpdated.glb");

// See if the model needs updating
if (!tile.VisualElements.MixedRealityModel.Uri.Equals(updatedUri))
{
    // Update it
    tile.VisualElements.MixedRealityModel.Uri = updatedUri;

    // And apply the changes
    await tile.UpdateAsync();
}
```

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a>ユーザーが、Windows Mixed Reality をチェックします。

3D のディープ リンク (secondaryTiles) は、ビューは、Windows Mixed Reality ヘッドセットで表示されているときにのみ作成できます。 Windows Mixed Reality ヘッドセットされていないビューに表示されている場合は、エントリ ポイントを非表示か、エラー メッセージを表示してこれを適切に処理をお勧めします。 これを確認するにはクエリを実行して[IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)します。

## <a name="tile-notifications"></a>タイル通知

現在、タイル通知が 3D アセットの更新を送信するサポートしていません。 つまり、開発者は、以下を実行できません。
* プッシュ通知
* 定期的なポーリング
* スケジュールされた通知

詳細については、他のタイルの機能と、属性とその 2D のタイルの使用方法を参照してください。、[ドキュメントについては UWP アプリのタイル](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles)します。

## <a name="see-also"></a>関連項目

* [複合現実モデル サンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)3D アプリ ランチャーを格納しています。
* [3D アプリ起動ツールの設計ガイダンス](3d-app-launcher-design-guidance.md)
* [Windows Mixed Reality 自宅で使用するための 3D モデルを作成します。](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [3D アプリ ランチャー (Win32 アプリ) を実装します。](implementing-3d-app-launchers-win32.md)
* [Windows Mixed Reality ホームに移動します。](navigating-the-windows-mixed-reality-home.md)
