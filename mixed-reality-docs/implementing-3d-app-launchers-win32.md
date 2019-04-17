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
# <a name="implement-3d-app-launchers-win32-apps"></a><span data-ttu-id="fec47-104">3D アプリ ランチャー (Win32 アプリ) の実装します。</span><span class="sxs-lookup"><span data-stu-id="fec47-104">Implement 3D app launchers (Win32 apps)</span></span>

> [!NOTE]
> <span data-ttu-id="fec47-105">この機能は、最新バージョンを実行しているコンピューターのみ[Windows Insider](https://insider.windows.com)フライト (RS5)、17704 と新しいビルドします。</span><span class="sxs-lookup"><span data-stu-id="fec47-105">This feature is only available to PCs running the latest [Windows Insider](https://insider.windows.com) flights (RS5), build 17704 and newer.</span></span>

<span data-ttu-id="fec47-106">[Windows Mixed Reality ホーム](navigating-the-windows-mixed-reality-home.md)始めるユーザーがアプリケーションを起動する前に配置する場所です。</span><span class="sxs-lookup"><span data-stu-id="fec47-106">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="fec47-107">既定では、没入型の Win32 VR アプリやゲームはヘッドセットの外部から起動する必要があるし、Windows Mixed Reality スタート メニューのすべてのアプリ 一覧に表示されません。</span><span class="sxs-lookup"><span data-stu-id="fec47-107">By default, immersive Win32 VR apps and games have to be launched from outside the headset and won't appear in the "All apps" list on the Windows Mixed Reality Start menu.</span></span> <span data-ttu-id="fec47-108">ただし、3D アプリ ランチャーを実装するためには、この記事の手順では、Win32 VR エクスペリエンスを作り出すから起動できます Windows Mixed Reality スタート メニューとホーム環境にします。</span><span class="sxs-lookup"><span data-stu-id="fec47-108">However, by following the instructions in this article to implement a 3D app launcher, your immersive Win32 VR experience can be launched from within the Windows Mixed Reality Start menu and home environment.</span></span>

<span data-ttu-id="fec47-109">ストリームの外部での Win32 VR エクスペリエンス distributied の没入型の場合のみです。</span><span class="sxs-lookup"><span data-stu-id="fec47-109">This is only true for immersive Win32 VR experiences distributied outside of Steam.</span></span> <span data-ttu-id="fec47-110">VR エクスペリエンスのため[蒸気経由で配布](updating-your-steamvr-application-for-windows-mixed-reality.md)、しました[SteamVR ベータ版の Windows Mixed Reality を更新](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800)最新の Windows Insider RS5 と共に、Windows での表示をタイトル SteamVR ようにのフライト既定の起動ツールを使用して自動的にすべてのアプリ] 一覧で混合の実際には [スタート] メニューは。</span><span class="sxs-lookup"><span data-stu-id="fec47-110">For VR experiences [distributed through Steam](updating-your-steamvr-application-for-windows-mixed-reality.md), we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest Windows Insider RS5 flights so that SteamVR titles show up in the Windows Mixed Reality Start menu in the "All apps" list automatically using a default launcher.</span></span> <span data-ttu-id="fec47-111">つまり、この記事で説明されているメソッドでは、SteamVR タイトルの必要はありませんし、SteamVR ベータ機能の Windows Mixed Reality によってオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="fec47-111">In other words, the method described in this article is unnecessary for SteamVR titles and will be overridden by the Windows Mixed Reality for SteamVR Beta functionality.</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="fec47-112">3D アプリ起動ツールの作成プロセス</span><span class="sxs-lookup"><span data-stu-id="fec47-112">3D app launcher creation process</span></span>

<span data-ttu-id="fec47-113">3D アプリ起動ツールを作成する 3 つの手順があります。</span><span class="sxs-lookup"><span data-stu-id="fec47-113">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="fec47-114">デザインと concepting</span><span class="sxs-lookup"><span data-stu-id="fec47-114">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="fec47-115">モデリングとエクスポート</span><span class="sxs-lookup"><span data-stu-id="fec47-115">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="fec47-116">(この記事)、アプリケーションに統合します。</span><span class="sxs-lookup"><span data-stu-id="fec47-116">Integrating it into your application (this article)</span></span>

<span data-ttu-id="fec47-117">3D アセットを使用して、アプリケーションの起動ツールを作成する必要がありますとして使用する、[ガイドラインの authoring Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)互換性を確保します。</span><span class="sxs-lookup"><span data-stu-id="fec47-117">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="fec47-118">このオーサリングの仕様を満たすために失敗した資産は、ホーム Windows Mixed Reality ではレンダリングされません。</span><span class="sxs-lookup"><span data-stu-id="fec47-118">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="fec47-119">3D の起動ツールを構成します。</span><span class="sxs-lookup"><span data-stu-id="fec47-119">Configuring the 3D launcher</span></span>

<span data-ttu-id="fec47-120">Win32 アプリケーションは、3 D のアプリ起動ツールを作成する場合、Windows Mixed Reality スタート メニューのすべてのアプリ 一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="fec47-120">Win32 applications will appear in the "All apps" list on the Windows Mixed Reality Start menu if you create a 3D app launcher for them.</span></span> <span data-ttu-id="fec47-121">作成、 [Visual 要素マニフェスト](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)次の手順で 3D アプリ起動ツールを参照する XML ファイル。</span><span class="sxs-lookup"><span data-stu-id="fec47-121">To do that, create a [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML file referencing the 3D App Launcher by following these steps:</span></span>

1. <span data-ttu-id="fec47-122">作成、 **3D アプリ起動ツール資産 GLB ファイル**(を参照してください[モデリングおよびエクスポート](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md))。</span><span class="sxs-lookup"><span data-stu-id="fec47-122">Create a **3D App Launcher asset GLB file** (See [Modeling and exporting](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span></span>
2. <span data-ttu-id="fec47-123">作成、  **[Visual 要素マニフェスト](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** アプリケーション用。</span><span class="sxs-lookup"><span data-stu-id="fec47-123">Create a **[Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** for your application.</span></span>
    1. <span data-ttu-id="fec47-124">使用することができます、[以下のサンプル](#sample-visual-elements-manifest)します。</span><span class="sxs-lookup"><span data-stu-id="fec47-124">You can start with the [sample below](#sample-visual-elements-manifest).</span></span>  <span data-ttu-id="fec47-125">完全を参照してください。 [Visual 要素マニフェスト](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)詳細についてはドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="fec47-125">See the full [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) documentation for more details.</span></span>
    2. <span data-ttu-id="fec47-126">更新**Square150x150Logo**と**Square70x70Logo** PNG/JPG または gif 形式、アプリを使用します。</span><span class="sxs-lookup"><span data-stu-id="fec47-126">Update **Square150x150Logo** and **Square70x70Logo** with a PNG/JPG/GIF for your app.</span></span>
        * <span data-ttu-id="fec47-127">これらは、Windows Mixed Reality のすべてのアプリの一覧で、アプリの 2D ロゴおよびデスクトップで [スタート] メニューに使用されます。</span><span class="sxs-lookup"><span data-stu-id="fec47-127">These will be used for the app’s 2D logo in the Windows Mixed Reality All Apps list and for the Start Menu on desktop.</span></span>
        * <span data-ttu-id="fec47-128">ファイルのパスでは、ビジュアル要素マニフェストを含むフォルダーの相対パスです。</span><span class="sxs-lookup"><span data-stu-id="fec47-128">The file path is relative to the folder containing the Visual Elements Manifest.</span></span>
        * <span data-ttu-id="fec47-129">標準のメカニズムを通じて、アプリ、デスクトップの [スタート] メニューのアイコンを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fec47-129">You still need to provide a desktop Start Menu icon for your app through the standard mechanisms.</span></span> <span data-ttu-id="fec47-130">実行可能ファイルなのか (例: IShellLink::SetIconLocation) 経由で作成したショートカットを指定できます。</span><span class="sxs-lookup"><span data-stu-id="fec47-130">This can either be directly in the executable or in the shortcut you create (e.g. via IShellLink::SetIconLocation).</span></span>
        * <span data-ttu-id="fec47-131">*省略可能。* 別の解像度のスケールとハイ コントラスト テーマの複数の資産のサイズを指定する MRT に必要な場合は、resources.pri ファイルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fec47-131">*Optional:* You can use a resources.pri file if you would like for MRT to provide multiple asset sizes for different resolution scales and high contrast themes.</span></span>
    3. <span data-ttu-id="fec47-132">更新プログラム、 **MixedRealityModel パス**GLB を指す、3D アプリ起動ツールの</span><span class="sxs-lookup"><span data-stu-id="fec47-132">Update the **MixedRealityModel Path** to point to the GLB for your 3D App Launcher</span></span>
    4. <span data-ttu-id="fec47-133">拡張機能で、実行可能ファイルと同じ名前のファイルを保存"します。VisualElementsManifest.xml"と同じディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="fec47-133">Save the file with the same name as your executable file, with an extension of ".VisualElementsManifest.xml" and save it in the same directory.</span></span> <span data-ttu-id="fec47-134">たとえば、"contoso.exe"実行可能ファイルの付随する XML ファイルの名前は"contoso.visualelementsmanifest.xml"。</span><span class="sxs-lookup"><span data-stu-id="fec47-134">For example, for the executable file "contoso.exe", the accompanying XML file is named "contoso.visualelementsmanifest.xml".</span></span>
3. <span data-ttu-id="fec47-135">**ショートカットを追加する**デスクトップでの Windows の [スタート] メニューをアプリケーションにします。</span><span class="sxs-lookup"><span data-stu-id="fec47-135">**Add a shortcut** to your application to the desktop Windows Start Menu.</span></span> <span data-ttu-id="fec47-136">参照してください、[以下のサンプル](#sample-app-launcher-shortcut-creation)例については、C++実装します。</span><span class="sxs-lookup"><span data-stu-id="fec47-136">See the [sample below](#sample-app-launcher-shortcut-creation) for an example C++ implementation.</span></span> 
    * <span data-ttu-id="fec47-137">%ALLUSERSPROFILE%\Microsoft\Windows\Start menu \programs (コンピューター) または %APPDATA%\Microsoft\Windows\Start menu \programs (ユーザー) で作成します。</span><span class="sxs-lookup"><span data-stu-id="fec47-137">Create it in %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) or %APPDATA%\Microsoft\Windows\Start Menu\Programs (user)</span></span>
    * <span data-ttu-id="fec47-138">視覚的要素マニフェストまたはその参照先資産の更新プログラムが変更された場合 updater またはインストーラーする必要がありますショートカットを更新、マニフェストが再解析され、キャッシュしたアセットが更新されるようにします。</span><span class="sxs-lookup"><span data-stu-id="fec47-138">If an update changes your visual elements manifest or the assets referenced by it, the updater or installer should update the shortcut such that the manifest is reparsed and cached assets are updated.</span></span>
4. <span data-ttu-id="fec47-139">*省略可能。* デスクトップ ショートカットが、アプリケーションの EXE の直接を指していないかどうか (などのカスタム プロトコル ハンドラーを呼び出す場合など、"myapp://")、[スタート] メニューは、アプリの VisualElementsManifest.xml ファイルに自動的に検出しません。</span><span class="sxs-lookup"><span data-stu-id="fec47-139">*Optional:* If your desktop shortcut does not point directly to your application’s EXE (e.g., if it invokes a custom protocol handler like “myapp://”), the Start Menu won’t automatically find the app’s VisualElementsManifest.xml file.</span></span> <span data-ttu-id="fec47-140">これを解決するには、ショートカットが System.AppUserModel.VisualElementsManifestHintPath () を使用して視覚的要素マニフェストのファイル パスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fec47-140">To resolve this, the shortcut should specify the file path of the Visual Elements Manifest using System.AppUserModel.VisualElementsManifestHintPath ().</span></span> <span data-ttu-id="fec47-141">これは、System.AppUserModel.ID として同じ手法を使用して、ショートカットに設定できます。</span><span class="sxs-lookup"><span data-stu-id="fec47-141">This can be set in the shortcut using the same techniques as System.AppUserModel.ID.</span></span> <span data-ttu-id="fec47-142">System.AppUserModel.ID を使用する必要はありませんが、ショートカットを使用している場合、アプリケーションの明示的なアプリケーション ユーザー モデル ID に一致する場合はする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fec47-142">You are not required to use System.AppUserModel.ID but you may do so if you wish for the shortcut to match the explicit Application User Model ID of the application if one is used.</span></span>  <span data-ttu-id="fec47-143">参照してください、[アプリ起動ツールのショートカットの作成のサンプル](#sample-app-launcher-shortcut-creation)下の「、C++サンプル。</span><span class="sxs-lookup"><span data-stu-id="fec47-143">See the [sample app launcher shortcut creation](#sample-app-launcher-shortcut-creation) section below for a C++ sample.</span></span>

### <a name="sample-visual-elements-manifest"></a><span data-ttu-id="fec47-144">サンプルの Visual 要素マニフェスト</span><span class="sxs-lookup"><span data-stu-id="fec47-144">Sample Visual Elements Manifest</span></span>

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

### <a name="sample-app-launcher-shortcut-creation"></a><span data-ttu-id="fec47-145">サンプル アプリ起動ツールのショートカットの作成</span><span class="sxs-lookup"><span data-stu-id="fec47-145">Sample app launcher shortcut creation</span></span>

<span data-ttu-id="fec47-146">次のサンプル コードでショートカットを作成する方法を示しています。 C++、などの Visual 要素マニフェスト XML ファイルへのパスをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="fec47-146">The sample code below shows how you can create a shortcut in C++, including overriding the path to the Visual Elements Manifest XML file.</span></span> <span data-ttu-id="fec47-147">場所のショートカットは、直接 (例: マニフェストに関連付けられている実行可能ファイルをポイントしていない場合、上書きが必要なだけに注意してください。</span><span class="sxs-lookup"><span data-stu-id="fec47-147">Note the override is only required in cases where your shortcut does not point directly to the EXE associated with the manifest (eg.</span></span> <span data-ttu-id="fec47-148">ショートカットのようにカスタム プロトコル ハンドラーを使用して"myapp://")。</span><span class="sxs-lookup"><span data-stu-id="fec47-148">your shortcut uses a custom protocol handler like "myapp://").</span></span>

#### <a name="sample-lnk-shortcut-creation-c"></a><span data-ttu-id="fec47-149">サンプルです。LNK ショートカットの作成 (C++)</span><span class="sxs-lookup"><span data-stu-id="fec47-149">Sample .LNK shortcut creation (C++)</span></span>

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

#### <a name="sample-url-launcher-shortcut"></a><span data-ttu-id="fec47-150">サンプルです。URL のランチャー ショートカット</span><span class="sxs-lookup"><span data-stu-id="fec47-150">Sample .URL launcher shortcut</span></span> 

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

## <a name="see-also"></a><span data-ttu-id="fec47-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="fec47-151">See also</span></span>

* <span data-ttu-id="fec47-152">[複合現実モデル サンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)3D アプリ ランチャーを格納しています。</span><span class="sxs-lookup"><span data-stu-id="fec47-152">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="fec47-153">3D アプリ起動ツールの設計ガイダンス</span><span class="sxs-lookup"><span data-stu-id="fec47-153">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="fec47-154">Windows Mixed Reality 自宅で使用するための 3D モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="fec47-154">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="fec47-155">3D アプリ ランチャー (UWP アプリ) を実装します。</span><span class="sxs-lookup"><span data-stu-id="fec47-155">Implementing 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="fec47-156">Windows Mixed Reality ホームに移動します。</span><span class="sxs-lookup"><span data-stu-id="fec47-156">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
