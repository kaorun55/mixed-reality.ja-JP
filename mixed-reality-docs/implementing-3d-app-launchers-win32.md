---
title: 3D アプリ ランチャー (Win32 アプリ) の実装します。
description: 3D アプリ ランチャーと Win32 VR アプリやゲームの (ストリームの外部で配布) のロゴを作成するため、表示、Windows の混合実際には [スタート] メニューとホーム環境でどのようにします。
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D、ロゴ、アイコン、モデリング、ランチャー、3 D ランチャー、タイル、ライブのキューブ、win32
ms.openlocfilehash: ac3d5e17614bcd1072f6843a46bf0525f441f130
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600994"
---
# <a name="implement-3d-app-launchers-win32-apps"></a>3D アプリ ランチャー (Win32 アプリ) の実装します。

> [!NOTE]
> この機能は、最新バージョンを実行しているコンピューターのみ[Windows Insider](https://insider.windows.com)フライト (RS5)、17704 と新しいビルドします。

[Windows Mixed Reality ホーム](navigating-the-windows-mixed-reality-home.md)始めるユーザーがアプリケーションを起動する前に配置する場所です。 既定では、没入型の Win32 VR アプリやゲームはヘッドセットの外部から起動する必要があるし、Windows Mixed Reality スタート メニューのすべてのアプリ 一覧に表示されません。 ただし、3D アプリ ランチャーを実装するためには、この記事の手順では、Win32 VR エクスペリエンスを作り出すから起動できます Windows Mixed Reality スタート メニューとホーム環境にします。

ストリームの外部での Win32 VR エクスペリエンス distributied の没入型の場合のみです。 VR エクスペリエンスのため[蒸気経由で配布](updating-your-steamvr-application-for-windows-mixed-reality.md)、しました[SteamVR ベータ版の Windows Mixed Reality を更新](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800)最新の Windows Insider RS5 と共に、Windows での表示をタイトル SteamVR ようにのフライト既定の起動ツールを使用して自動的にすべてのアプリ] 一覧で混合の実際には [スタート] メニューは。 つまり、この記事で説明されているメソッドでは、SteamVR タイトルの必要はありませんし、SteamVR ベータ機能の Windows Mixed Reality によってオーバーライドされます。

## <a name="3d-app-launcher-creation-process"></a>3D アプリ起動ツールの作成プロセス

3D アプリ起動ツールを作成する 3 つの手順があります。
1. [デザインと concepting](3d-app-launcher-design-guidance.md)
2. [モデリングとエクスポート](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. (この記事)、アプリケーションに統合します。

3D アセットを使用して、アプリケーションの起動ツールを作成する必要がありますとして使用する、[ガイドラインの authoring Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)互換性を確保します。 このオーサリングの仕様を満たすために失敗した資産は、ホーム Windows Mixed Reality ではレンダリングされません。

## <a name="configuring-the-3d-launcher"></a>3D の起動ツールを構成します。

Win32 アプリケーションは、3 D のアプリ起動ツールを作成する場合、Windows Mixed Reality スタート メニューのすべてのアプリ 一覧に表示されます。 作成、 [Visual 要素マニフェスト](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)次の手順で 3D アプリ起動ツールを参照する XML ファイル。

1. 作成、 **3D アプリ起動ツール資産 GLB ファイル**(を参照してください[モデリングおよびエクスポート](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md))。
2. 作成、  **[Visual 要素マニフェスト](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** アプリケーション用。
    1. 使用することができます、[以下のサンプル](#sample-visual-elements-manifest)します。  完全を参照してください。 [Visual 要素マニフェスト](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)詳細についてはドキュメントです。
    2. 更新**Square150x150Logo**と**Square70x70Logo** PNG/JPG または gif 形式、アプリを使用します。
        * これらは、Windows Mixed Reality のすべてのアプリの一覧で、アプリの 2D ロゴおよびデスクトップで [スタート] メニューに使用されます。
        * ファイルのパスでは、ビジュアル要素マニフェストを含むフォルダーの相対パスです。
        * 標準のメカニズムを通じて、アプリ、デスクトップの [スタート] メニューのアイコンを指定する必要があります。 実行可能ファイルなのか (例: IShellLink::SetIconLocation) 経由で作成したショートカットを指定できます。
        * *省略可能。* 別の解像度のスケールとハイ コントラスト テーマの複数の資産のサイズを指定する MRT に必要な場合は、resources.pri ファイルを使用できます。
    3. 更新プログラム、 **MixedRealityModel パス**GLB を指す、3D アプリ起動ツールの
    4. 拡張機能で、実行可能ファイルと同じ名前のファイルを保存"します。VisualElementsManifest.xml"と同じディレクトリに保存します。 たとえば、"contoso.exe"実行可能ファイルの付随する XML ファイルの名前は"contoso.visualelementsmanifest.xml"。
3. **ショートカットを追加する**デスクトップでの Windows の [スタート] メニューをアプリケーションにします。 参照してください、[以下のサンプル](#sample-app-launcher-shortcut-creation)例については、C++実装します。 
    * %ALLUSERSPROFILE%\Microsoft\Windows\Start menu \programs (コンピューター) または %APPDATA%\Microsoft\Windows\Start menu \programs (ユーザー) で作成します。
    * 視覚的要素マニフェストまたはその参照先資産の更新プログラムが変更された場合 updater またはインストーラーする必要がありますショートカットを更新、マニフェストが再解析され、キャッシュしたアセットが更新されるようにします。
4. *省略可能。* デスクトップ ショートカットが、アプリケーションの EXE の直接を指していないかどうか (などのカスタム プロトコル ハンドラーを呼び出す場合など、"myapp://")、[スタート] メニューは、アプリの VisualElementsManifest.xml ファイルに自動的に検出しません。 これを解決するには、ショートカットが System.AppUserModel.VisualElementsManifestHintPath () を使用して視覚的要素マニフェストのファイル パスを指定する必要があります。 これは、System.AppUserModel.ID として同じ手法を使用して、ショートカットに設定できます。 System.AppUserModel.ID を使用する必要はありませんが、ショートカットを使用している場合、アプリケーションの明示的なアプリケーション ユーザー モデル ID に一致する場合はする可能性があります。  参照してください、[アプリ起動ツールのショートカットの作成のサンプル](#sample-app-launcher-shortcut-creation)下の「、C++サンプル。

### <a name="sample-visual-elements-manifest"></a>サンプルの Visual 要素マニフェスト

```xml
<Application xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <VisualElements
    ShowNameOnSquare150x150Logo="on"
    Square150x150Logo="YOUR_APP_LOGO_150X150.png"
    Square70x70Logo=" YOUR_APP_LOGO_70X70.png"
    ForegroundText="light"
    BackgroundColor="#000000">
    <MixedRealityModel Path="YOUR_3D_APP_LAUNCHER_ASSET.glb">
        <SpatialBoundingBox Center="0,0,0" Extents="Auto" />
    </MixedRealityModel>
  </VisualElements>
</Application>
```

### <a name="sample-app-launcher-shortcut-creation"></a>サンプル アプリ起動ツールのショートカットの作成

次のサンプル コードでショートカットを作成する方法を示しています。 C++、などの Visual 要素マニフェスト XML ファイルへのパスをオーバーライドします。 場所のショートカットは、直接 (例: マニフェストに関連付けられている実行可能ファイルをポイントしていない場合、上書きが必要なだけに注意してください。 ショートカットのようにカスタム プロトコル ハンドラーを使用して"myapp://")。

#### <a name="sample-lnk-shortcut-creation-c"></a>サンプルです。LNK ショートカットの作成 (C++)

```cpp
#include <windows.h>
#include <propkey.h>
#include <shlobj_core.h>
#include <shlwapi.h>
#include <propvarutil.h>
#include <wrl.h>

#include <memory>

using namespace Microsoft::WRL;

#define RETURN_IF_FAILED(x) do { HRESULT hr = x; if (FAILED(hr)) { return hr; } } while(0)
#define RETURN_IF_WIN32_BOOL_FALSE(x) do { DWORD res = x; if (res == 0) { return HRESULT_FROM_WIN32(GetLastError()); } } while(0)

int wmain()
{
    RETURN_IF_FAILED(CoInitializeEx(nullptr, COINIT_APARTMENTTHREADED));

    ComPtr<IShellLink> shellLink;
    RETURN_IF_FAILED(CoCreateInstance(__uuidof(ShellLink), nullptr, CLSCTX_INPROC_SERVER, IID_PPV_ARGS(&shellLink)));
    RETURN_IF_FAILED(shellLink->SetPath(L"MyLauncher://launch/app-identifier"));

    // It is also possible to use an icon file in another location. For example, "C:\Program Files (x86)\MyLauncher\assets\app-identifier.ico".
    RETURN_IF_FAILED(shellLink->SetIconLocation(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.exe", 0 /*iIcon*/));

    ComPtr<IPropertyStore> propStore;
    RETURN_IF_FAILED(shellLink.As(&propStore));

    {
        // Optional: If the application has an explict Application User Model ID, then you should usually specify it in the shortcut.
        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"ExplicitAppUserModelID", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_ID, propVar));
        PropVariantClear(&propVar);
    }

    {
        // A hint path to the manifest is only necessary if the target path of the shortcut is not a file path to the executable.
        // By convention the manifest is named <executable name>.VisualElementsManifest.xml and is in the same folder as the executable
        // (and resources.pri if applicable). Assets referenced by the manifest are relative to the folder containing the manifest.

        //
        // PropKey.h
        //
        //  Name:     System.AppUserModel.VisualElementsManifestHintPath -- PKEY_AppUserModel_VisualElementsManifestHintPath
        //  Type:     String -- VT_LPWSTR  (For variants: VT_BSTR)
        //  FormatID: {9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}, 31
        //  
        //  Suggests where to look for the VisualElementsManifest for a Win32 app
        //
        // DEFINE_PROPERTYKEY(PKEY_AppUserModel_VisualElementsManifestHintPath, 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3, 31);
        // #define INIT_PKEY_AppUserModel_VisualElementsManifestHintPath { { 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3 }, 31 }

        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.visualelementsmanifest.xml", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_VisualElementsManifestHintPath, propVar));
        PropVariantClear(&propVar);
    }

    constexpr PCWSTR shortcutPath = L"%APPDATA%\\Microsoft\\Windows\\Start Menu\\Programs\\game.lnk";
    const DWORD requiredBufferLength = ExpandEnvironmentStrings(shortcutPath, nullptr, 0);
    RETURN_IF_WIN32_BOOL_FALSE(requiredBufferLength);

    const auto expandedShortcutPath = std::make_unique<wchar_t[]>(requiredBufferLength);
    RETURN_IF_WIN32_BOOL_FALSE(ExpandEnvironmentStrings(shortcutPath, expandedShortcutPath.get(), requiredBufferLength));

    ComPtr<IPersistFile> persistFile;
    RETURN_IF_FAILED(shellLink.As(&persistFile));
    RETURN_IF_FAILED(persistFile->Save(expandedShortcutPath.get(), FALSE));

    return 0;
}
```

#### <a name="sample-url-launcher-shortcut"></a>サンプルです。URL のランチャー ショートカット 

```
[{9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}]
Prop31=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.visualelementsmanifest.xml
Prop5=ExplicitAppUserModelID

[{000214A0-0000-0000-C000-000000000046}]
Prop3=19,0

[InternetShortcut]
IDList=
URL=MyLauncher://launch/app-identifier
IconFile=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.exe
IconIndex=0
```

## <a name="see-also"></a>関連項目

* [複合現実モデル サンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)3D アプリ ランチャーを格納しています。
* [3D アプリ起動ツールの設計ガイダンス](3d-app-launcher-design-guidance.md)
* [Windows Mixed Reality 自宅で使用するための 3D モデルを作成します。](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [3D アプリ ランチャー (UWP アプリ) を実装します。](implementing-3d-app-launchers.md)
* [Windows Mixed Reality ホームに移動します。](navigating-the-windows-mixed-reality-home.md)
