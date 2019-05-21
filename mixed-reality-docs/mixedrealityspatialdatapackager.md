---
title: 複合現実の空間データ パッケー ジャーのドキュメント
description: Mixed Reality 空間データ Packager を使用するためのドキュメント
author: alfred-msft
ms.author: alreynol
ms.date: 05/16/2019
ms.topic: article
keywords: lbe MixedRealitySpatialDataPackager.exe、MixedRealitySpatialDataPackager
ms.openlocfilehash: 7ad1159af9eecd3ca3622dd25cc1f49fb0b1700a
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942108"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a><span data-ttu-id="b0ce1-104">複合現実の空間データ パッケー ジャーのドキュメント</span><span class="sxs-lookup"><span data-stu-id="b0ce1-104">Mixed Reality Spatial Data Packager Documentation</span></span>

>[!NOTE]
> <span data-ttu-id="b0ce1-105">このツールと、その操作として提供されているは。</span><span class="sxs-lookup"><span data-stu-id="b0ce1-105">This tool and its operation are offered as-is.</span></span> <span data-ttu-id="b0ce1-106">今後の Windows と互換性がない可能性があり、予告なく変更される可能性がまたは Windows Mixed Reality ッドマウントを解放します。</span><span class="sxs-lookup"><span data-stu-id="b0ce1-106">It is subject to change without any notice and may not be compatible with future Windows or Windows Mixed Reality HMD releases.</span></span>

## <a name="download"></a><span data-ttu-id="b0ce1-107">ダウンロード</span><span class="sxs-lookup"><span data-stu-id="b0ce1-107">Download</span></span>
 <span data-ttu-id="b0ce1-108">ダウンロード[MixedRealitySpatialDataPackager ここ](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span><span class="sxs-lookup"><span data-stu-id="b0ce1-108">Download [MixedRealitySpatialDataPackager here](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span></span>

## <a name="quickstart"></a><span data-ttu-id="b0ce1-109">クイック スタート</span><span class="sxs-lookup"><span data-stu-id="b0ce1-109">Quickstart</span></span>

<span data-ttu-id="b0ce1-110">Mixed Reality 空間データ Packager ツールは、2 つの手順は、別の PC のエクスポートおよびインポート プロセスのいずれかからターゲット アプリの空間データをコピーします。</span><span class="sxs-lookup"><span data-stu-id="b0ce1-110">The Mixed Reality Spatial Data Packager tool copies the spatial data of a target app from one PC to another through a two step export and import process.</span></span> <span data-ttu-id="b0ce1-111">このツールは、管理者特権で実行する必要があり、インポート時に既存の空間データを削除します。</span><span class="sxs-lookup"><span data-stu-id="b0ce1-111">The tool must be run with administrator privileges and deletes the existing spatial data on import.</span></span> <span data-ttu-id="b0ce1-112">エクスポートは、そのまま既存の空間データを残されます。</span><span class="sxs-lookup"><span data-stu-id="b0ce1-112">Export leaves the existing spatial data intact.</span></span>

<span data-ttu-id="b0ce1-113">主な要件と制限事項:</span><span class="sxs-lookup"><span data-stu-id="b0ce1-113">Key requirements and limitations:</span></span>

1. <span data-ttu-id="b0ce1-114">ツールは、管理者特権で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0ce1-114">Tool must be run with administrator privileges</span></span> 
2. <span data-ttu-id="b0ce1-115">ツールの実行後は Mixed Reality ポータルが安定しない場合は、PC を再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0ce1-115">You may have to restart PC if Mixed Reality Portal is unstable after running the tool</span></span>
3. <span data-ttu-id="b0ce1-116">空間データのバージョンの不一致または互換性の問題が発生した場合、ツールは実行されません。</span><span class="sxs-lookup"><span data-stu-id="b0ce1-116">Tool will not run when encountering spatial data version mismatches or incompatibilities</span></span>
4. <span data-ttu-id="b0ce1-117">インポート時に既存の空間データを消去するツール</span><span class="sxs-lookup"><span data-stu-id="b0ce1-117">Tool will erase existing spatial data on import</span></span>
5. <span data-ttu-id="b0ce1-118">以前にエクスポートすることによってバックアップされていない場合にデータを復元できません前にインポート プロセスが失敗した場合</span><span class="sxs-lookup"><span data-stu-id="b0ce1-118">If import process fails previous data cannot be restored unless it has been backed up by exporting previously</span></span>
6. <span data-ttu-id="b0ce1-119">マップの空間データの「読み取り専用」モードで臨時のインポート機能の品質</span><span class="sxs-lookup"><span data-stu-id="b0ce1-119">Quality of import functionality contingent on “Read-Only” mode for spatial map data</span></span>
***

## <a name="mapping-best-practices"></a><span data-ttu-id="b0ce1-120">マッピングのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="b0ce1-120">Mapping Best Practices</span></span>

1. <span data-ttu-id="b0ce1-121">コントロール パネルから既存のマップをクリア (設定]、[Mixed Reality 環境]-> [-> オフ環境データ)</span><span class="sxs-lookup"><span data-stu-id="b0ce1-121">Clear existing maps from the Control Panel (Settings -> Mixed Reality -> Environment -> Clear environment data)</span></span>
2. <span data-ttu-id="b0ce1-122">適切な追跡およびかどうかはロックされているマップ モードで動作する光源を維持するためにしてみてくださいのための十分なライティングを確認します。</span><span class="sxs-lookup"><span data-stu-id="b0ce1-122">Ensure sufficient lighting for good tracking and if running locked map mode try to maintain the same lighting</span></span>
3. <span data-ttu-id="b0ce1-123">可能な場合ライト ダイナミック レンジを低く抑えるため、暗い、シャドウされた領域の横に高の照明を回避します。</span><span class="sxs-lookup"><span data-stu-id="b0ce1-123">When possible keep the lighting dynamic range low by avoiding areas of high illumination next to dark, shadowed areas</span></span>
4. <span data-ttu-id="b0ce1-124">空白を最小限に抑える、textureless サーフェスは、白い壁のさまざまなポスターの範囲を配置する例。</span><span class="sxs-lookup"><span data-stu-id="b0ce1-124">Minimize blank, textureless surfaces e.g. place a range of different posters on white walls</span></span>
5. <span data-ttu-id="b0ce1-125">マップ領域でユーザーを移動するなど、シーン内の動的オブジェクトなし</span><span class="sxs-lookup"><span data-stu-id="b0ce1-125">Map the space without dynamic objects in the scene such as moving people</span></span>
6. <span data-ttu-id="b0ce1-126">インポート (Insider Preview で使用可能) で、マップをロックします。</span><span class="sxs-lookup"><span data-stu-id="b0ce1-126">Lock the map on import (available via Insider Preview)</span></span>
7. <span data-ttu-id="b0ce1-127">マップのロックを解除し、品質の追跡が低下や (照明またはオブジェクトのレイアウトの変更) 環境で変更があるときに、環境を再スキャン</span><span class="sxs-lookup"><span data-stu-id="b0ce1-127">Unlock the map and rescan the enviornment when tracking quality degrades and/or there are changes in the environment (lighting or changes in object layout)</span></span>
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a><span data-ttu-id="b0ce1-128">コンパニオン スクリプトの実行中の Mixed Reality 空間データ パッケー ジャー</span><span class="sxs-lookup"><span data-stu-id="b0ce1-128">Running Mixed Reality Spatial Data Packager with Companion Script</span></span>

<span data-ttu-id="b0ce1-129">マップ パッケー ジャー、ツールを実行している MRSpatialPackagerHelperScript.ps1 を用意しました。</span><span class="sxs-lookup"><span data-stu-id="b0ce1-129">We have provided MRSpatialPackagerHelperScript.ps1 that runs the map packager the tools.</span></span> 


<span data-ttu-id="b0ce1-130">以下は、スクリプトのパラメーターが定義されています。</span><span class="sxs-lookup"><span data-stu-id="b0ce1-130">The script parameters are defined below:</span></span>

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
    This functionality requires an updated driver from Insider Preview Builds with the Map Locking feature

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a><span data-ttu-id="b0ce1-131">Powershell スクリプトの使用例と出力</span><span class="sxs-lookup"><span data-stu-id="b0ce1-131">Powershell Script Example Usage and Output</span></span>

<span data-ttu-id="b0ce1-132">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span><span class="sxs-lookup"><span data-stu-id="b0ce1-132">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span></span>
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value succesfully set to 0

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

### <a name="how-to-export-using-mixedrealitypackagerexe"></a><span data-ttu-id="b0ce1-133">MixedRealityPackager.exe を使用してエクスポートする方法</span><span class="sxs-lookup"><span data-stu-id="b0ce1-133">How to Export using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

<span data-ttu-id="b0ce1-134">デバイスの電源オフのマップをエクスポートするには、2 つの mapx ファイル、het.mapx と sa.mapx が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b0ce1-134">Exporting maps off device generates two mapx files, het.mapx and sa.mapx.</span></span> <span data-ttu-id="b0ce1-135">エクスポート プロセス中にすべての空間アンカー (存在する) 場合、指定したアプリとユーザーが作成した境界を除く削除されます。</span><span class="sxs-lookup"><span data-stu-id="b0ce1-135">During the export process all spatial anchors are removed except for the specified app and the user-created boundary (if it exists).</span></span> <span data-ttu-id="b0ce1-136">ソースのパッケージ ファミリ名は、既存のインストールされているアプリと一致する必要があります。 または exe は失敗します。</span><span class="sxs-lookup"><span data-stu-id="b0ce1-136">The source package family name must match an existing installed app or the exe will fail.</span></span>

### <a name="how-to-import-using-mixedrealitypackagerexe"></a><span data-ttu-id="b0ce1-137">MixedRealityPackager.exe を使用してインポートする方法</span><span class="sxs-lookup"><span data-stu-id="b0ce1-137">How to Import using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
<span data-ttu-id="b0ce1-138">インポートでは、既存の空間データを削除し、指定したディレクトリからデータに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="b0ce1-138">Import deletes the existing spatial data and replaces it with the data from the specified directory.</span></span> <span data-ttu-id="b0ce1-139">アプリ名の入力は、空間のアンカーを対象となるアプリのパッケージ名のためにインポートする必要があります、ターゲット ユーザーの SID は、インポートされた空間アンカーへのアクセス権をユーザーを指定を指定します。</span><span class="sxs-lookup"><span data-stu-id="b0ce1-139">The app name input specifies the package name of the target app that like the spatial anchors should be imported for and the target user SID specifies the user that should have access to the imported spatial anchors.</span></span> <span data-ttu-id="b0ce1-140">ターゲットのパッケージ ファミリ名とユーザーの Sid が PC 上の既存の値に一致する必要があります。 または exe は失敗します。</span><span class="sxs-lookup"><span data-stu-id="b0ce1-140">The target package family name and user SIDs must match existing values on the PC or the exe will fail.</span></span>


***
## <a name="error-messages"></a><span data-ttu-id="b0ce1-141">エラー メッセージ</span><span class="sxs-lookup"><span data-stu-id="b0ce1-141">Error Messages</span></span>
<span data-ttu-id="b0ce1-142">さらに以下のエラーのエラー メッセージも伴います HRESULT</span><span class="sxs-lookup"><span data-stu-id="b0ce1-142">In addition the error messages below failures will also be accompanied with an HRESULT</span></span>

### <a name="if-there-was-an-error-invalid-arguments"></a><span data-ttu-id="b0ce1-143">無効な引数エラーが発生した場合</span><span class="sxs-lookup"><span data-stu-id="b0ce1-143">If there was an error invalid arguments</span></span>
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a><span data-ttu-id="b0ce1-144">管理者モードで実行可能ファイルが実行されていない場合</span><span class="sxs-lookup"><span data-stu-id="b0ce1-144">If the executable was not run in administrator mode</span></span>
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a><span data-ttu-id="b0ce1-145">有効にするか、ドライバーを無効にすると、エラーが発生した場合</span><span class="sxs-lookup"><span data-stu-id="b0ce1-145">If there was an error enabling or disabling the driver</span></span>
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a><span data-ttu-id="b0ce1-146">空間データベースのバージョンを検証中にエラーが発生した場合</span><span class="sxs-lookup"><span data-stu-id="b0ce1-146">If there was an error validating the spatial database version</span></span>
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a><span data-ttu-id="b0ce1-147">インポート/エクスポートの対象のアプリのパッケージ ファミリ名を検証中にエラーが発生した場合</span><span class="sxs-lookup"><span data-stu-id="b0ce1-147">If there was an error validating the package family name provided for target import/export app</span></span>
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a><span data-ttu-id="b0ce1-148">ユーザーの SID を検証中にエラーが発生した場合</span><span class="sxs-lookup"><span data-stu-id="b0ce1-148">If there was an error validating the user SID</span></span>
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a><span data-ttu-id="b0ce1-149">移行先またはソースの空間データに関連するエラーが、ファイルを使用するがあった場合</span><span class="sxs-lookup"><span data-stu-id="b0ce1-149">If there was an error related to the destination or source spatial data files</span></span>
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stoping-spectrumsharedrealitysvc"></a><span data-ttu-id="b0ce1-150">開始および停止スペクトル/SharedRealitySvc に関連するエラーが発生しました</span><span class="sxs-lookup"><span data-stu-id="b0ce1-150">If there was an error related to starting and stoping Spectrum/SharedRealitySvc</span></span>
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
