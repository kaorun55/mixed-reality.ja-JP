---
title: Mixed Reality 空間データパッケージャーのドキュメント
description: Mixed Reality 空間データパッケージャーの使用に関するドキュメント
author: alfred-msft
ms.author: yuripek
ms.date: 05/16/2019
ms.topic: article
keywords: lbe、MixedRealitySpatialDataPackager、MixedRealitySpatialDataPackager
ms.openlocfilehash: 3beb8f9168bfb6fd921d6d5c1eb6d250c70a714d
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539684"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a><span data-ttu-id="42ff3-104">Mixed Reality 空間データパッケージャーのドキュメント</span><span class="sxs-lookup"><span data-stu-id="42ff3-104">Mixed Reality Spatial Data Packager Documentation</span></span>

>[!NOTE]
> <span data-ttu-id="42ff3-105">このツールとその操作は、そのとおりに提供されます。</span><span class="sxs-lookup"><span data-stu-id="42ff3-105">This tool and its operation are offered as-is.</span></span> <span data-ttu-id="42ff3-106">予告なしに変更されることがあり、今後の Windows または Windows Mixed Reality のリリースと互換性がない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="42ff3-106">It is subject to change without any notice and may not be compatible with future Windows or Windows Mixed Reality HMD releases.</span></span>

## <a name="download"></a><span data-ttu-id="42ff3-107">[ダウンロード]</span><span class="sxs-lookup"><span data-stu-id="42ff3-107">Download</span></span>
 <span data-ttu-id="42ff3-108">[MixedRealitySpatialDataPackager をこちら](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)からダウンロード</span><span class="sxs-lookup"><span data-stu-id="42ff3-108">Download [MixedRealitySpatialDataPackager here](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span></span>

## <a name="device-support"></a><span data-ttu-id="42ff3-109">デバイスのサポート</span><span class="sxs-lookup"><span data-stu-id="42ff3-109">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="42ff3-110"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="42ff3-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="42ff3-111"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="42ff3-111"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="42ff3-112"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="42ff3-112"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="42ff3-113"><a href="immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="42ff3-113"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="42ff3-114">Mixed Reality 空間データパッケージャー</span><span class="sxs-lookup"><span data-stu-id="42ff3-114">Mixed Reality Spatial Data Packager</span></span></td>
        <td>❌</td>
        <td>❌</td>
        <td><span data-ttu-id="42ff3-115">✔️</span><span class="sxs-lookup"><span data-stu-id="42ff3-115">✔️</span></span></td>
    </tr>
</table>

## <a name="quickstart"></a><span data-ttu-id="42ff3-116">クィック</span><span class="sxs-lookup"><span data-stu-id="42ff3-116">Quickstart</span></span>

<span data-ttu-id="42ff3-117">Mixed Reality 空間データパッケージャーツールは、エクスポートとインポートの2つの手順を通じて、ターゲットアプリの空間データをある PC から別の PC にコピーします。</span><span class="sxs-lookup"><span data-stu-id="42ff3-117">The Mixed Reality Spatial Data Packager tool copies the spatial data of a target app from one PC to another through a two step export and import process.</span></span> <span data-ttu-id="42ff3-118">このツールは、管理者特権で実行する必要があり、インポート時に既存の空間データを削除します。</span><span class="sxs-lookup"><span data-stu-id="42ff3-118">The tool must be run with administrator privileges and deletes the existing spatial data on import.</span></span> <span data-ttu-id="42ff3-119">Export は、既存の空間データをそのまま残します。</span><span class="sxs-lookup"><span data-stu-id="42ff3-119">Export leaves the existing spatial data intact.</span></span>

<span data-ttu-id="42ff3-120">重要な要件と制限事項:</span><span class="sxs-lookup"><span data-stu-id="42ff3-120">Key requirements and limitations:</span></span>

1. <span data-ttu-id="42ff3-121">ツールは、管理者特権で実行する必要があります</span><span class="sxs-lookup"><span data-stu-id="42ff3-121">Tool must be run with administrator privileges</span></span> 
2. <span data-ttu-id="42ff3-122">ツールを実行した後に Mixed Reality ポータルが不安定な場合は、PC の再起動が必要になることがあります</span><span class="sxs-lookup"><span data-stu-id="42ff3-122">You may have to restart PC if Mixed Reality Portal is unstable after running the tool</span></span>
3. <span data-ttu-id="42ff3-123">空間データのバージョンの不一致または非互換性の検出時にツールが実行されない</span><span class="sxs-lookup"><span data-stu-id="42ff3-123">Tool will not run when encountering spatial data version mismatches or incompatibilities</span></span>
4. <span data-ttu-id="42ff3-124">インポート時に既存の空間データが消去されます</span><span class="sxs-lookup"><span data-stu-id="42ff3-124">Tool will erase existing spatial data on import</span></span>
5. <span data-ttu-id="42ff3-125">インポート処理が失敗した場合、以前のデータをエクスポートしてバックアップしていない限り、以前のデータを復元することはできません。</span><span class="sxs-lookup"><span data-stu-id="42ff3-125">If import process fails previous data cannot be restored unless it has been backed up by exporting previously</span></span>
6. <span data-ttu-id="42ff3-126">空間マップデータの "読み取り専用" モードでのインポート機能の品質</span><span class="sxs-lookup"><span data-stu-id="42ff3-126">Quality of import functionality contingent on “Read-Only” mode for spatial map data</span></span>
***

## <a name="mapping-best-practices"></a><span data-ttu-id="42ff3-127">マッピングのベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="42ff3-127">Mapping Best Practices</span></span>

1. <span data-ttu-id="42ff3-128">コントロールパネルから既存のマップをクリアする (設定 > Mixed Reality-> Environment-環境データをクリア >)</span><span class="sxs-lookup"><span data-stu-id="42ff3-128">Clear existing maps from the Control Panel (Settings -> Mixed Reality -> Environment -> Clear environment data)</span></span>
2. <span data-ttu-id="42ff3-129">適切な追跡に十分な照明を確保し、ロックされたマップモードを実行している場合は、同じ照明を維持します</span><span class="sxs-lookup"><span data-stu-id="42ff3-129">Ensure sufficient lighting for good tracking and if running locked map mode try to maintain the same lighting</span></span>
3. <span data-ttu-id="42ff3-130">可能な場合は、暗い領域、影付き領域の横に高い照明の領域を避けて、光源の範囲を小さくします。</span><span class="sxs-lookup"><span data-stu-id="42ff3-130">When possible keep the lighting dynamic range low by avoiding areas of high illumination next to dark, shadowed areas</span></span>
4. <span data-ttu-id="42ff3-131">空白の領域を最小化する (たとえば、異なるポスターの範囲をホワイトウォールに配置する)</span><span class="sxs-lookup"><span data-stu-id="42ff3-131">Minimize blank, textureless surfaces e.g. place a range of different posters on white walls</span></span>
5. <span data-ttu-id="42ff3-132">オブジェクトの移動など、シーンに動的オブジェクトを使用せずに領域をマップする</span><span class="sxs-lookup"><span data-stu-id="42ff3-132">Map the space without dynamic objects in the scene such as moving people</span></span>
6. <span data-ttu-id="42ff3-133">インポート時にマップをロックする (Insider Preview 経由で利用可能)</span><span class="sxs-lookup"><span data-stu-id="42ff3-133">Lock the map on import (available via Insider Preview)</span></span>
7. <span data-ttu-id="42ff3-134">品質の追跡が低下したとき、または環境に変化があった場合に、マップのロックを解除して環境を再スキャンする (照明またはオブジェクトのレイアウトの変更)</span><span class="sxs-lookup"><span data-stu-id="42ff3-134">Unlock the map and rescan the environment when tracking quality degrades and/or there are changes in the environment (lighting or changes in object layout)</span></span>
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a><span data-ttu-id="42ff3-135">コンパニオンスクリプトを使用した Mixed Reality 空間データパッケージャーの実行</span><span class="sxs-lookup"><span data-stu-id="42ff3-135">Running Mixed Reality Spatial Data Packager with Companion Script</span></span>

<span data-ttu-id="42ff3-136">マップツールを実行する MRSpatialPackagerHelperScript が用意されています。</span><span class="sxs-lookup"><span data-stu-id="42ff3-136">We have provided MRSpatialPackagerHelperScript.ps1 that runs the map packager the tools.</span></span> 


<span data-ttu-id="42ff3-137">スクリプトのパラメーターは次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="42ff3-137">The script parameters are defined below:</span></span>

```
-AppName <String>
    On export: The spatial anchors from the app of interest
    On import: The target app that spatial anchors should be imported for
    Returns a list of apps containing the input string if a unique app is not found

-UserName <String>
    Target username, will return a list of users if a unique match is not found

-Mode <String>
    import or export

-MapxPath <String>
    On export: Directory to export your mapx files
    On import: Directory where import mapx are stored

-LockMap <Int32>
    0 to unlock map
    1 to lock map

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a><span data-ttu-id="42ff3-138">Powershell スクリプトの使用例と出力</span><span class="sxs-lookup"><span data-stu-id="42ff3-138">Powershell Script Example Usage and Output</span></span>

<span data-ttu-id="42ff3-139">.\MRSpatialPackagerHelperScript.ps1-AppName holoshell-UserName Administrator-Mode export-MapxPath D:\temp\-LockMap 0</span><span class="sxs-lookup"><span data-stu-id="42ff3-139">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span></span>
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value successfully set to 0

Running: C:\bin\MixedRealitySpatialDataPackager.exe export D:\temp\ HoloShell_cw5n1h2txyewy S-1-5-21-1279937937-3984375698-1043392598-499

Attempting to disable Windows MR driver
Driver disabled
Validating spatial data version information...
Device spatial data version OK
External spatial data version OK
Importing spatial anchors for user account phguan
Stopping SPECTRUM
Stopped SPECTRUM
Stopping SHAREDREALITYSVC
Stopped SHAREDREALITYSVC
Space ID is {00000000-4321-0000-0000-000000000000}
SUCCESS: Unpacked Space from D:\temp\map\het.mapx to
C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors\{00000000-4321-0000-0000-000000000000}\
Space ID is {78FA06B5-4416-4815-BB00-B3CB5C983B7D}
SUCCESS: Unpacked Space from D:\temp\map\sa.mapx to
C:\ProgramData\Microsoft\Spectrum\PersistedSpatialAnchors\
Attempting to enable Windows MR driver
Driver enabled
Starting SHAREDREALITYSVC
Started SHAREDREALITYSVC
Starting SPECTRUM
Started SPECTRUM
IMPORT SUCCESS
```

### <a name="how-to-export-using-mixedrealitypackagerexe"></a><span data-ttu-id="42ff3-140">MixedRealityPackager を使用してエクスポートする方法</span><span class="sxs-lookup"><span data-stu-id="42ff3-140">How to Export using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

<span data-ttu-id="42ff3-141">デバイスからマップをエクスポートすると、het. mapx と sa. mapx という2つの mapx ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="42ff3-141">Exporting maps off device generates two mapx files, het.mapx and sa.mapx.</span></span> <span data-ttu-id="42ff3-142">エクスポートプロセスでは、指定されたアプリとユーザーが作成した境界 (存在する場合) を除き、すべての空間アンカーが削除されます。</span><span class="sxs-lookup"><span data-stu-id="42ff3-142">During the export process all spatial anchors are removed except for the specified app and the user-created boundary (if it exists).</span></span> <span data-ttu-id="42ff3-143">ソースパッケージファミリ名は、インストールされている既存のアプリと一致する必要があります。一致しないと、exe は失敗します。</span><span class="sxs-lookup"><span data-stu-id="42ff3-143">The source package family name must match an existing installed app or the exe will fail.</span></span>

### <a name="how-to-import-using-mixedrealitypackagerexe"></a><span data-ttu-id="42ff3-144">MixedRealityPackager を使用してインポートする方法</span><span class="sxs-lookup"><span data-stu-id="42ff3-144">How to Import using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
<span data-ttu-id="42ff3-145">インポートによって既存の空間データが削除され、指定したディレクトリのデータで置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="42ff3-145">Import deletes the existing spatial data and replaces it with the data from the specified directory.</span></span> <span data-ttu-id="42ff3-146">アプリ名の入力では、空間アンカーをインポートする対象アプリのパッケージ名を指定し、ターゲットユーザー SID で、インポートされた空間アンカーへのアクセス権を持つユーザーを指定します。</span><span class="sxs-lookup"><span data-stu-id="42ff3-146">The app name input specifies the package name of the target app that like the spatial anchors should be imported for and the target user SID specifies the user that should have access to the imported spatial anchors.</span></span> <span data-ttu-id="42ff3-147">ターゲットパッケージファミリ名とユーザー Sid が PC 上の既存の値と一致している必要があります。指定しないと、exe は失敗します。</span><span class="sxs-lookup"><span data-stu-id="42ff3-147">The target package family name and user SIDs must match existing values on the PC or the exe will fail.</span></span>


***
## <a name="error-messages"></a><span data-ttu-id="42ff3-148">エラー メッセージ</span><span class="sxs-lookup"><span data-stu-id="42ff3-148">Error Messages</span></span>
<span data-ttu-id="42ff3-149">さらに、次のエラーメッセージにも HRESULT が付随します。</span><span class="sxs-lookup"><span data-stu-id="42ff3-149">In addition the error messages below failures will also be accompanied with an HRESULT</span></span>

### <a name="if-there-was-an-error-invalid-arguments"></a><span data-ttu-id="42ff3-150">エラーが発生した場合は、無効な引数</span><span class="sxs-lookup"><span data-stu-id="42ff3-150">If there was an error invalid arguments</span></span>
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a><span data-ttu-id="42ff3-151">実行可能ファイルが管理者モードで実行されなかった場合</span><span class="sxs-lookup"><span data-stu-id="42ff3-151">If the executable was not run in administrator mode</span></span>
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a><span data-ttu-id="42ff3-152">ドライバーの有効化または無効化でエラーが発生した場合</span><span class="sxs-lookup"><span data-stu-id="42ff3-152">If there was an error enabling or disabling the driver</span></span>
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a><span data-ttu-id="42ff3-153">空間データベースバージョンの検証中にエラーが発生した場合</span><span class="sxs-lookup"><span data-stu-id="42ff3-153">If there was an error validating the spatial database version</span></span>
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a><span data-ttu-id="42ff3-154">ターゲットのインポート/エクスポートアプリに指定されたパッケージファミリ名の検証中にエラーが発生した場合</span><span class="sxs-lookup"><span data-stu-id="42ff3-154">If there was an error validating the package family name provided for target import/export app</span></span>
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a><span data-ttu-id="42ff3-155">ユーザー SID の検証中にエラーが発生した場合</span><span class="sxs-lookup"><span data-stu-id="42ff3-155">If there was an error validating the user SID</span></span>
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a><span data-ttu-id="42ff3-156">コピー先またはコピー元の空間データファイルに関連するエラーが発生した場合</span><span class="sxs-lookup"><span data-stu-id="42ff3-156">If there was an error related to the destination or source spatial data files</span></span>
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stopping-spectrumsharedrealitysvc"></a><span data-ttu-id="42ff3-157">スペクトラムの開始と停止に関連するエラーが発生した場合は、</span><span class="sxs-lookup"><span data-stu-id="42ff3-157">If there was an error related to starting and stopping Spectrum/SharedRealitySvc</span></span>
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
