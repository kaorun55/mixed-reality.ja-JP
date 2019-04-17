---
title: Holographic DirectX プロジェクトを作成します。
description: Windows Mixed Reality アプリ テンプレートに基づく新しい holographic アプリを作成する方法について説明します。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、holographic アプリ、新しいアプリ、UWP アプリ、テンプレートのアプリ、ホログラム、新しいプロジェクト、チュートリアル、ダウンロード、サンプル コード
ms.openlocfilehash: 7d1ea0246cf823f74e68b4e67fbcfc275d081688
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605098"
---
# <a name="creating-a-holographic-directx-project"></a>Holographic DirectX プロジェクトを作成します。

HoloLens を作成する holographic アプリ、<a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">ユニバーサル Windows プラットフォーム (UWP) アプリ</a>します。  デスクトップの Windows Mixed Reality ヘッドセットを対象とする場合は、UWP アプリまたは Win32 アプリを作成できます。

DirectX 11 holographic UWP アプリ テンプレートとよく似ています、DirectX 11 の UWP アプリ テンプレートこれはプログラム ループ (または「ゲーム ループ」) が含まれます。、 **DeviceResources** Direct3D デバイスと、コンテキストを管理するクラスと簡略化されたコンテンツ レンダラー クラス。 また、 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>他の UWP アプリと同様、します。

Mixed reality アプリには、一般的な Direct3D 11 の UWP アプリではないいくつかの追加機能ただしがあります。 Windows Holographic のアプリ テンプレートができます。
* Holographic カメラに関連付けられている Direct3D デバイス リソースを処理します。
* システムからカメラのバック バッファーを取得します。
* 処理[視線](gaze.md)入力、および単純な認識[ジェスチャ](gestures.md)します。
* ステレオのレンダリングを全画面表示モードに移動します。

## <a name="how-do-i-get-started"></a>どのように始めればよいですか。

最初[ツールをインストールする](install-the-tools.md)、次の Visual Studio 2017 のダウンロードについてと Microsoft HoloLens のエミュレーター。 Microsoft HoloLens のエミュレーターと同じインストーラーには、holographic アプリ テンプレートが含まれます。 また、インストールする前に、テンプレートをインストールするオプションが選択されていることを確認します。

これで、DirectX 11 Windows Mixed Reality アプリを作成する準備ができました。 ただし、サンプルの内容を削除するには、コメント アウト、 **DRAW_SAMPLE_CONTENT**プリプロセッサ ディレクティブで*pch.h*。

## <a name="creating-a-uwp-project"></a>UWP プロジェクトを作成します。

ツールをインストールした後、holographic DirectX UWP プロジェクトを作成できます。 新しいプロジェクトを作成するには
1. 開始**Visual Studio**します。
2. **ファイル**メニューで、**新規**選択**プロジェクト**コンテキスト メニュー。 **新しいプロジェクト**ダイアログ ボックスが開きます。
3. 展開**インストール済み**左側を展開し、 **Visual C++** 言語ノード。
4. 移動し、 **Windows ユニバーサル > Holographic**ノード**Holographic DirectX 11 アプリ (ユニバーサル Windows) (C++/WinRT)** します。
   >[!IMPORTANT]
   >プロジェクト テンプレートの名前が含まれているかどうかを必ず"(C++/WinRT)"。  有効でない場合は、以前のバージョンのインストールされている holographic プロジェクト テンプレートがあります。  最新のプロジェクト テンプレートを取得する[最新 HoloLens のエミュレーターをインストール](using-the-hololens-emulator.md)します。
5. 入力、**名前**と**場所**テキスト ボックス、およびクリックまたはタップします**OK**。 Holographic アプリ プロジェクトが作成されます。
6. 開発のため、HoloLens 2 のみを対象とすることを確認、**ターゲット バージョン**と**最小バージョン**に設定されている**Windows 10、バージョンが 1903**。  HoloLens も対象とする場合 (第 1 世代) 設定するデスクトップの Windows Mixed Reality ヘッドセットまたは**最小バージョン**に**Windows 10、バージョンは 1809**代わりに、いくつかが必要ですが<a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">バージョン adapative チェック</a>HoloLens 2 の新機能を使用する場合、コードにします。

![Visual Studio で holographic アプリ プロジェクト テンプレートのスクリーン ショット](images/holographic-directx-app-cpp-new-project.png)<br>
*Visual Studio での holographic アプリ プロジェクト テンプレート*

テンプレートを使用してプロジェクトを生成する<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>、標準に準拠した c++ 17 コンパイラをサポートする Windows ランタイム Api の c++ 17 の言語プロジェクションです。  プロジェクトでは、ユーザーからの 2 つのメーターが配置される世界ロックされているキューブを作成する方法を示します。 ユーザーは[エア タップ](gestures.md#air-tap)でユーザーの指定された別の位置に、キューブを配置するコント ローラーのボタンを押してまたは[視線](gaze.md)します。 すべての複合現実アプリを作成するには、このプロジェクトを変更できます。

使用して新しいプロジェクトを作成する代わりに、 **Visual C#**  holographic プロジェクト テンプレート、SharpDX に基づいています。  場合、holographic C# Windows Holographic のアプリ テンプレートからプロジェクトは開始されませんでした、Windows Mixed Reality から ms.fxcompile.targets ファイルをコピーする必要がありますC#HLSL をコンパイルするためにファイルで、.csproj プロジェクト テンプレートとインポートプロジェクトに追加するファイル。

レビュー[を配置およびデバッグ Visual Studio を使用して](using-visual-studio.md)構築し、HoloLens、PC に接続されている、没入型のデバイスまたはエミュレーターにデプロイする方法についてはします。

以下の手順の残りの部分を使用するいると仮定してC++アプリをビルドできます。

### <a name="uwp-app-entry-point"></a>UWP アプリのエントリ ポイント

Holographic UWP アプリケーションの起動時、 **wWinMain** AppView.cpp 内の関数。 **WWinMain**関数は、アプリの作成<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>を開始し、 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a>とします。

**AppView.cpp**:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

その時点からは、AppView クラスは、Windows の基本的な入力イベント、CoreWindow イベント メッセージング、およびなどとの対話を処理します。 アプリで使用される HolographicSpace も作成されます。

## <a name="creating-a-win32-project"></a>Win32 プロジェクトの作成

適応 holographic プロジェクトは、Win32 の構築を開始する最も簡単な方法、 <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram* Win32 サンプル</a>します。

この Win32 サンプルを使用して<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>、標準に準拠した c++ 17 コンパイラをサポートする Windows ランタイム Api の c++ 17 の言語プロジェクションです。  プロジェクトでは、ユーザーからの 2 つのメーターが配置される世界ロックされているキューブを作成する方法を示します。 ユーザーがユーザーによって指定されている別の位置に、キューブを配置するコント ローラーのボタンを押す[視線](gaze.md)します。 すべての複合現実アプリを作成するには、このプロジェクトを変更できます。

### <a name="win32-app-entry-point"></a>Win32 アプリのエントリ ポイント

Holographic Win32 アプリケーションの起動時、 **wWinMain** AppMain.cpp 内の関数。 **WWinMain**関数し、メッセージ ループを開始するアプリケーションの HWND を作成します。

**AppMain.cpp**:

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

その時点からは、AppMain クラスは、基本的なウィンドウのメッセージとの対話を処理します。 アプリで使用される HolographicSpace も作成されます。

## <a name="render-holographic-content"></a>Holographic のコンテンツをレンダリングします。

プロジェクトの**コンテンツ**フォルダーにはでレンダリング ホログラム用のクラスが含まれています、 [holographic 領域](getting-a-holographicspace.md)します。 テンプレートの既定ホログラムは、ユーザーからの 2 つのメーターが配置される、回転するキューブです。 このキューブの描画では実装されて**SpinningCubeRenderer.cpp**がこれらの主要メソッド。

|  メソッド  |  説明 | 
|----------|----------|
|  `CreateDeviceDependentResources` |  シェーダーの読み込みをキューブのメッシュを作成します。 | 
|  `PositionHologram` |  提供されている指定された位置に、ホログラムが配置<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>します。 | 
|  `Update` |  キューブを回転し、モデルの行列を設定します。 | 
|  `Render` |  頂点とピクセル シェーダーを使用してフレームをレンダリングします。 | 

**シェーダー**サブフォルダーには、次の 4 つの既定のシェーダー実装が含まれています。

|  シェーダー  |  説明 | 
|----------|----------|
|  `GeometryShader.hlsl` |  変更されていないジオメトリをパススルーします。 | 
|  `PixelShader.hlsl` |  データの色を通過します。 色のデータが補間し、ラスタライズ ステップでピクセルに割り当てられています。 | 
|  `VertexShader.hlsl` |  GPU で頂点処理を行う単純なシェーダー。 | 
|  `VPRTVertexShader.hlsl` |  Windows Mixed Reality ステレオ レンダリング用に最適化された GPU で頂点処理を行う単純なシェーダー。 | 

`VertexShaderShared.hlsl` 間で共有される共通のコードを含む`VertexShader.hlsl`と`VPRTVertexShader.hlsl`します。

プロジェクトをビルドするとで読み込まれているときに、シェーダーがコンパイルされる、 **SpinningCubeRenderer::CreateDeviceDependentResources**メソッド。

## <a name="interact-with-your-holograms"></a>ホログラムとの対話します。

ユーザー入力の処理で、 **SpatialInputHandler**クラスを取得、 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a>インスタンスし、サブスクライブする、 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a>イベント。 これにより、エア タップ ジェスチャとその他の空間の入力イベントを検出できます。

## <a name="update-holographic-content"></a>Holographic のコンテンツを更新します。

既定で実装されているゲームのループで、複合現実アプリの更新プログラム、 **Update**メソッド`AppMain.cpp`します。 **Update**メソッドは、回転するキューブのように、シーンのオブジェクトを更新しを返します、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>を最新の状態の表示および投影マトリックスを取得し、スワップ チェーンを表示するに使用されるオブジェクト。

**レンダリング**メソッド`AppMain.cpp`は、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>し、現在のアプリと空間配置の状態に従って各 holographic カメラの現在のフレームをレンダリングします。

## <a name="see-also"></a>関連項目
* [HolographicSpace を取得します。](getting-a-holographicspace.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [DirectX でのレンダリング](rendering-in-directx.md)
* [Visual Studio を使用してデプロイをデバッグします。](using-visual-studio.md)
* [HoloLens のエミュレーターを使用する](using-the-hololens-emulator.md)
* [Holographic の DirectX アプリでの XAML の使用](using-xaml-with-holographic-directx-apps.md)
