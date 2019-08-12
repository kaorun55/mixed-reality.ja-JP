---
title: Holographic DirectX プロジェクトの作成
description: Windows Mixed Reality アプリテンプレートに基づいて新しい holographic アプリを作成する方法について説明します。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, holographic アプリ, 新しいアプリ, UWP アプリ, テンプレートアプリ, ホログラム, 新しいプロジェクト, チュートリアル, ダウンロード, サンプルコード
ms.openlocfilehash: 24f217021cd448f19a744696de42f580f139f76f
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387617"
---
# <a name="creating-a-holographic-directx-project"></a>Holographic DirectX プロジェクトの作成

HoloLens 用に作成した holographic アプリは、<a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">ユニバーサル Windows プラットフォーム (UWP) アプリ</a>になります。  デスクトップ Windows Mixed Reality ヘッドセットを対象とする場合は、UWP アプリまたは Win32 アプリを作成できます。

DirectX 11 holographic UWP アプリテンプレートは DirectX 11 UWP アプリテンプレートとよく似ています。これには、プログラムループ (または "ゲームループ")、Direct3D デバイスとコンテキストを管理するための**DeviceResources**クラス、および簡略化されたコンテンツレンダラークラスが含まれます。 他の UWP アプリと同じように、 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>もあります。

ただし、mixed reality アプリには、一般的な Direct3D 11 UWP アプリには存在しないいくつかの追加機能があります。 Windows Holographic アプリケーションテンプレートでは、次のことができます。
* Holographic カメラに関連付けられている Direct3D デバイスリソースを処理します。
* システムからカメラバックバッファーを取得します。
* [見つめ](gaze.md)入力を処理し、簡単な[ジェスチャ](gestures.md)を認識します。
* 全画面表示のステレオレンダリングモードに切り替えます。

## <a name="how-do-i-get-started"></a>操作方法開始しますか?

まず、Visual Studio 2019 と Microsoft HoloLens emulator のダウンロードに関する説明に従って、[ツールをインストール](install-the-tools.md)します。 Holographic アプリテンプレートは、Microsoft HoloLens エミュレーターと同じインストーラーに含まれています。 また、インストールする前に、テンプレートをインストールするオプションが選択されていることを確認してください。

これで、DirectX 11 Windows Mixed Reality アプリを作成する準備ができました。 サンプルコンテンツを削除するには、 *pch*の**DRAW_SAMPLE_CONTENT**プリプロセッサディレクティブをコメントアウトします。

## <a name="creating-a-uwp-project"></a>UWP プロジェクトの作成

[ツールがインストールさ](install-the-tools.md)れたら、HOLOGRAPHIC DirectX UWP プロジェクトを作成できます。

新しいプロジェクトを作成するには:
1. **Visual Studio**を起動します。
2. [**ファイル**] メニューの [**新規作成**] をポイントし、コンテキストメニューの [**プロジェクト**] をクリックします。 [**新しいプロジェクト**] ダイアログボックスが開きます。
3. 左側にある [**インストール済み**] を展開し、[**ビジュアルC++** 言語] ノードを展開します。
4. [ **Windows Universal > Holographic** ] ノードに移動し、[ **Holographic DirectX 11 App (Universal WindowsC++) (/WinRT)** ] を選択します。
   ![Visual Studio の Holographic DirectX 11 C++/WinRT UWP アプリプロジェクトテンプレートのスクリーンショット](images/holographic-directx-app-cpp-new-project.png)<br>
   *Visual Studio でC++の Holographic DirectX 11/WinRT UWP アプリプロジェクトテンプレート*
   >[!IMPORTANT]
   >プロジェクトテンプレートの名前に "(C++/WinRT)" が含まれていることを確認してください。  それ以外の場合は、古いバージョンの holographic プロジェクトテンプレートがインストールされています。  最新のプロジェクトテンプレートを入手するには、[最新の HoloLens エミュレーターをインストール](using-the-hololens-emulator.md)します。
5. [**名前**] と [**場所**] のテキストボックスに入力し、[ **OK**] をクリックまたはタップします。 Holographic app プロジェクトが作成されます。
6. HoloLens 2 のみを対象とする開発では、**ターゲットバージョン**と**最小バージョン**が**Windows 10 バージョン 1903**に設定されていることを確認します。  HoloLens (第1世代) またはデスクトップ Windows Mixed Reality ヘッドセットも対象としている場合は、代わりに、[**最小バージョン**] を**Windows 10 バージョン 1809**に設定できます。ただし、これには、新しいを使用するときに、コードにいくつかの<a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">バージョンのアダプティブチェック</a>が必要になります。HoloLens 2 の機能。
   ![ターゲットバージョンと最小バージョンとして Windows 10 バージョン1903を設定するスクリーンショット](images/new-uwp-project.png)<br>
   *ターゲットバージョンと最小バージョンとして**Windows 10 バージョン1903を**設定する*
   >[!IMPORTANT]
   >オプションとして**windows 10 バージョン 1903**が表示されない場合は、最新の WINDOWS 10 SDK がインストールされていません。  このオプションを表示するに<a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">は、Windows 10 SDK のバージョン10.0.18362.0 以降をインストール</a>します。

このテンプレートは、標準に準拠している c++ 17 コンパイラをサポートする Windows ランタイム api の c++ 17 言語プロジェクションである<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>を使用してプロジェクトを生成します。  このプロジェクトは、ユーザーから2メートル離れたワールドロックキューブを作成する方法を示しています。 ユーザーは、コントローラー上のボタンを使用して、ユーザーの[宝石](gaze.md)によって指定された別の位置にキューブを[配置できます](gestures.md#air-tap)。 このプロジェクトを変更して、mixed reality アプリを作成できます。

または、SharpDX に基づく**Visual C#**  holographic プロジェクトテンプレートを使用して、新しいプロジェクトを作成することもできます。  Holographic C#プロジェクトが windows holographic アプリテンプレートから開始されなかった場合は、Windows Mixed Reality C#テンプレートプロジェクトから ms. fxcompile .targets ファイルをコピーして、HLSL ファイルにインポートして HLSL をコンパイルする必要があります。プロジェクトに追加するファイル。

[「Visual Studio を使用してデプロイとデバッグ](using-visual-studio.md)を行う」で、HoloLens、PC にデバイスが接続されている PC、またはエミュレーターにサンプルを構築してデプロイする方法について確認します。

次の手順の残りの部分では、を使用C++してアプリをビルドすることを前提としています。

### <a name="uwp-app-entry-point"></a>UWP アプリのエントリポイント

Holographic UWP アプリは、AppView .cpp の**Wwinmain**関数で開始されます。 **Wwinmain**関数は、アプリの<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>を作成し、それを使用して<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a>を開始します。

**Appview .cpp**から:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

この時点から、AppView クラスは、Windows 基本入力イベント、CoreWindow イベントとメッセージングなどとの対話を処理します。 また、アプリで使用される HolographicSpace も作成されます。

## <a name="creating-a-win32-project"></a>Win32 プロジェクトの作成

Win32 holographic プロジェクトの構築を開始する最も簡単な方法は、 <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *basichologram* win32 サンプル</a>を調整することです。

この Win32 サンプルでは、標準に準拠している c++ 17 コンパイラをサポートする Windows ランタイム api の c++ 17 言語プロジェクションである<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>を使用します。  このプロジェクトは、ユーザーから2メートル離れたワールドロックキューブを作成する方法を示しています。 ユーザーは、コントローラー上のボタンをクリックして、ユーザーの[宝石](gaze.md)によって指定された別の位置にキューブを配置できます。 このプロジェクトを変更して、mixed reality アプリを作成できます。

### <a name="win32-app-entry-point"></a>Win32 アプリのエントリポイント

Holographic Win32 アプリは、AppMain の**Wwinmain**関数で開始されます。 **Wwinmain**関数は、アプリの HWND を作成し、そのメッセージループを開始します。

**Appmain .cpp**から:

```cpp
int APIENTRY wWinMain(
    _In_     HINSTANCE hInstance,
    _In_opt_ HINSTANCE hPrevInstance,
    _In_     LPWSTR    lpCmdLine,
    _In_     int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    winrt::init_apartment();

    App app;

    // Initialize global strings, and perform application initialization.
    app.Initialize(hInstance);

    // Create the HWND and the HolographicSpace.
    app.CreateWindowAndHolographicSpace(hInstance, nCmdShow);

    // Main message loop:
    app.Run(hInstance);

    // Perform application teardown.
    app.Uninitialize();

    return 0;
}
```

この時点から、AppMain クラスは基本的なウィンドウメッセージとの対話を処理します。 また、アプリで使用される HolographicSpace も作成されます。

## <a name="render-holographic-content"></a>Holographic コンテンツのレンダリング

プロジェクトの**コンテンツ**フォルダーには、 [holographic 空間](getting-a-holographicspace.md)にホログラムをレンダリングするためのクラスが含まれています。 テンプレートの既定のホログラムは、ユーザーから2メートル離れた位置にある回転する立方体です。 このキューブの描画は、次の主要なメソッドを含む SpinningCubeRenderer に実装されてい**ます**。

|  メソッド  |  説明 | 
|----------|----------|
|  `CreateDeviceDependentResources` |  シェーダーを読み込み、キューブメッシュを作成します。 | 
|  `PositionHologram` |  指定した<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>によって指定された場所にホログラムを配置します。 | 
|  `Update` |  キューブを回転させ、モデルマトリックスを設定します。 | 
|  `Render` |  頂点シェーダーとピクセルシェーダーを使用してフレームをレンダリングします。 | 

**シェーダー**サブフォルダーには、4つの既定のシェーダー実装が含まれています。

|  シェーダー  |  説明 | 
|----------|----------|
|  `GeometryShader.hlsl` |  ジオメトリを変更せずに残すパススルー。 | 
|  `PixelShader.hlsl` |  カラーデータを通過します。 色データが補間され、ラスタライズの手順でピクセルに割り当てられます。 | 
|  `VertexShader.hlsl` |  GPU で頂点処理を行うための単純なシェーダー。 | 
|  `VPRTVertexShader.hlsl` |  Windows Mixed Reality ステレオレンダリング用に最適化された、GPU で頂点処理を行うための単純なシェーダー。 | 

`VertexShaderShared.hlsl`との間で`VertexShader.hlsl`共有される共通のコードを`VPRTVertexShader.hlsl`格納します。

シェーダーは、プロジェクトのビルド時にコンパイルされ、 **SpinningCubeRenderer:: CreateDeviceDependentResources**メソッドに読み込まれます。

## <a name="interact-with-your-holograms"></a>ホログラムを操作する

ユーザー入力は**SpatialInputHandler**クラスで処理されます。このクラスは<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a>インスタンスを取得し、 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">sourcepressed</a>イベントをサブスクライブします。 これにより、エアタップジェスチャとその他の空間入力イベントを検出できるようになります。

## <a name="update-holographic-content"></a>Holographic コンテンツの更新

混合 reality アプリの更新は、既定ではの`AppMain.cpp` **Update**メソッドに実装されているゲームループで更新されます。 **Update**メソッドは、回転するキューブなどのシーンオブジェクトを更新し、最新のビューおよび射影マトリックスを取得して、スワップチェーンを表示するために使用される<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>オブジェクトを返します。

の `AppMain.cpp` Render メソッドは、現在のアプリと空間ポジショニングの状態に従って、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>を受け取り、現在のフレームを各 holographic カメラにレンダリングします。

## <a name="see-also"></a>関連項目
* [HolographicSpace を入手する](getting-a-holographicspace.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [DirectX でのレンダリング](rendering-in-directx.md)
* [Visual Studio を使用してデプロイおよびデバッグする](using-visual-studio.md)
* [HoloLens のエミュレーターを使用する](using-the-hololens-emulator.md)
* [XAML とホログラフィック DirectX アプリの使用](using-xaml-with-holographic-directx-apps.md)
