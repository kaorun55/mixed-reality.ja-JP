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
# <a name="mixed-reality-spatial-data-packager-documentation"></a>複合現実の空間データ パッケー ジャーのドキュメント

>[!NOTE]
> このツールと、その操作として提供されているは。 今後の Windows と互換性がない可能性があり、予告なく変更される可能性がまたは Windows Mixed Reality ッドマウントを解放します。

## <a name="download"></a>ダウンロード
 ダウンロード[MixedRealitySpatialDataPackager ここ](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)

## <a name="quickstart"></a>クイック スタート

Mixed Reality 空間データ Packager ツールは、2 つの手順は、別の PC のエクスポートおよびインポート プロセスのいずれかからターゲット アプリの空間データをコピーします。 このツールは、管理者特権で実行する必要があり、インポート時に既存の空間データを削除します。 エクスポートは、そのまま既存の空間データを残されます。

主な要件と制限事項:

1. ツールは、管理者特権で実行する必要があります。 
2. ツールの実行後は Mixed Reality ポータルが安定しない場合は、PC を再起動する必要があります。
3. 空間データのバージョンの不一致または互換性の問題が発生した場合、ツールは実行されません。
4. インポート時に既存の空間データを消去するツール
5. 以前にエクスポートすることによってバックアップされていない場合にデータを復元できません前にインポート プロセスが失敗した場合
6. マップの空間データの「読み取り専用」モードで臨時のインポート機能の品質
***

## <a name="mapping-best-practices"></a>マッピングのベスト プラクティス

1. コントロール パネルから既存のマップをクリア (設定]、[Mixed Reality 環境]-> [-> オフ環境データ)
2. 適切な追跡およびかどうかはロックされているマップ モードで動作する光源を維持するためにしてみてくださいのための十分なライティングを確認します。
3. 可能な場合ライト ダイナミック レンジを低く抑えるため、暗い、シャドウされた領域の横に高の照明を回避します。
4. 空白を最小限に抑える、textureless サーフェスは、白い壁のさまざまなポスターの範囲を配置する例。
5. マップ領域でユーザーを移動するなど、シーン内の動的オブジェクトなし
6. インポート (Insider Preview で使用可能) で、マップをロックします。
7. マップのロックを解除し、品質の追跡が低下や (照明またはオブジェクトのレイアウトの変更) 環境で変更があるときに、環境を再スキャン
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a>コンパニオン スクリプトの実行中の Mixed Reality 空間データ パッケー ジャー

マップ パッケー ジャー、ツールを実行している MRSpatialPackagerHelperScript.ps1 を用意しました。 


以下は、スクリプトのパラメーターが定義されています。

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

### <a name="powershell-script-example-usage-and-output"></a>Powershell スクリプトの使用例と出力

.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0
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

### <a name="how-to-export-using-mixedrealitypackagerexe"></a>MixedRealityPackager.exe を使用してエクスポートする方法
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

デバイスの電源オフのマップをエクスポートするには、2 つの mapx ファイル、het.mapx と sa.mapx が生成されます。 エクスポート プロセス中にすべての空間アンカー (存在する) 場合、指定したアプリとユーザーが作成した境界を除く削除されます。 ソースのパッケージ ファミリ名は、既存のインストールされているアプリと一致する必要があります。 または exe は失敗します。

### <a name="how-to-import-using-mixedrealitypackagerexe"></a>MixedRealityPackager.exe を使用してインポートする方法
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
インポートでは、既存の空間データを削除し、指定したディレクトリからデータに置き換えられます。 アプリ名の入力は、空間のアンカーを対象となるアプリのパッケージ名のためにインポートする必要があります、ターゲット ユーザーの SID は、インポートされた空間アンカーへのアクセス権をユーザーを指定を指定します。 ターゲットのパッケージ ファミリ名とユーザーの Sid が PC 上の既存の値に一致する必要があります。 または exe は失敗します。


***
## <a name="error-messages"></a>エラー メッセージ
さらに以下のエラーのエラー メッセージも伴います HRESULT

### <a name="if-there-was-an-error-invalid-arguments"></a>無効な引数エラーが発生した場合
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a>管理者モードで実行可能ファイルが実行されていない場合
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a>有効にするか、ドライバーを無効にすると、エラーが発生した場合
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a>空間データベースのバージョンを検証中にエラーが発生した場合
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a>インポート/エクスポートの対象のアプリのパッケージ ファミリ名を検証中にエラーが発生した場合
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a>ユーザーの SID を検証中にエラーが発生した場合
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a>移行先またはソースの空間データに関連するエラーが、ファイルを使用するがあった場合
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stoping-spectrumsharedrealitysvc"></a>開始および停止スペクトル/SharedRealitySvc に関連するエラーが発生しました
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
