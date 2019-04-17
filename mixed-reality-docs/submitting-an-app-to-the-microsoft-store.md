---
title: Microsoft Store にアプリの提出
description: この記事では、複合現実アプリをパッケージ化して、アプリと証明書を渡すし、ストアでアプリの探索可能性を支援するためのヒントをテストする方法など、Microsoft Store に提出に関するヒントを提供します。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: アプリケーションでは、uwp、送信、送信、フィルター、メタデータ、システム要件、キーワード、wack、認定、パッケージ、appx、販売促進
ms.openlocfilehash: 4eb69fbaa22f4864305f09d5e1bf1c1860a0d31f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600864"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>Microsoft Store にアプリの提出

両方[HoloLens](hololens-hardware-details.md)および Windows 10 PC の強化、[イマーシブ ヘッドセット](immersive-headset-hardware-details.md)ユニバーサル Windows プラットフォーム アプリを実行します。 HoloLens または PC (またはその両方) をサポートするアプリを送信するかどうかを Microsoft Store にアプリを送信するします[パートナー センター](https://partner.microsoft.com/dashboard)します。

パートナー センターの開発者アカウントがない場合は、[今すぐサインアップ](https://developer.microsoft.com/store/register)します。

## <a name="packaging-a-mixed-reality-app"></a>Mixed reality アプリをパッケージ化

### <a name="prepare-image-assets-included-in-the-appx"></a>Appx に含まれるイメージのアセットを準備します。

Appx パッケージに、ストアに送信するアプリケーションをビルド、appx ツールの構築に必要ないくつかのイメージ アセットがあります。 詳細について確認できます[タイルおよびアイコンのアセット ガイドライン](https://msdn.microsoft.com/library/windows/apps/mt412102.aspx)msdn です。

| 必要な資産 | 推奨されるスケール | イメージの形式 | これが表示される場所ですか。 | 
|----------|----------|----------|------------------|
| 71 x 71 の正方形のロゴ | 任意 |  PNG | なし | 
| 150 x 150 の正方形のロゴ | 150 x 150 (100% スケール) または 225 x 225 (150% スケール) | PNG | ピンをすべてのアプリを起動し、(310 x 310 が提供されていない) 場合、ストアの検索候補、ストアを一覧表示するページで、ストアの参照、ストアの検索 | 
|  ワイド 310 ロゴ |  任意  |  PNG  |  なし | 
|  ストア ロゴ |  75 x 75 (150% スケール)  |  PNG  |  パートナー センターで報告書アプリなど、レビュー、ライブラリの書き込み | 
|  スプラッシュ スクリーン |  930 x 450 (150% スケール)  |  PNG  |  2D アプリ起動ツール (スレート) | 

HoloLens を利用する一部の推奨される資産もあります。

| 推奨される資産 | 推奨されるスケール | これが表示される場所ですか。 | 
|----------|----------|----------|
|  310 x 310 の正方形のロゴ |  310 x 310 (150% スケール) |  Pin とすべてのアプリを開始します。 | 

### <a name="live-tile-requirements"></a>ライブ タイルの要件

HoloLens で [スタート] メニューでは、最大の四角いタイルが含まれるイメージを使用します。

マイクロソフトによって発行されたいくつかのアプリにある、アプリケーションの 3D ランチャーに表示されます。 開発者を使用して、アプリ用の 3D の起動ツールを追加できる[手順](implementing-3d-app-launchers.md)します。

### <a name="specifying-target-and-minimum-version-of-windows"></a>ターゲットと Windows の最小バージョンを指定します。

Mixed reality アプリには、特定のバージョンの Windows に固有の機能が含まれている場合は、ターゲットとユニバーサル Windows アプリケーションをサポートするプラットフォームの最小バージョンを指定する必要があります。

**これは特に対象とするアプリの場合は true [Windows Mixed Reality イマーシブ ヘッドセット](immersive-headset-hardware-details.md)、少なくとも Windows 10 Fall Creators Update (10.0; が必要な。ビルド 16299) を正常に機能します。**

Visual Studio で新しいユニバーサル Windows プロジェクトを作成するときに、ターゲットと Windows の最小バージョンを設定するように促されます。 ドロップダウン メニューの下部にある [プロジェクト] メニュー、し、[< アプリ名の > プロパティ] で既存のプロジェクトに対してこの設定を変更することもできます。

![最小値を設定し、Visual Studio 2017 でのプラットフォームのバージョンをターゲット](images/visual-studio-min-version-500px.png)<br>
最小値を設定して、Visual Studio でのプラットフォーム バージョンを対象

### <a name="specifying-target-device-families"></a>ターゲット デバイス ファミリを指定します。

Windows Mixed Reality アプリケーション (両方の[HoloLens](hololens-hardware-details.md)と[イマーシブ ヘッドセット](immersive-headset-hardware-details.md))、次のようにユニバーサル Windows プラットフォームのため、アプリ パッケージの一部である、[対象のデバイス ファミリ](https://msdn.microsoft.com/library/windows/apps/dn986903.aspx)"Windows.Universal"のイマーシブ ヘッドセットと HoloLens または Windows 10 Pc で実行可能です。 ただし、アプリケーション マニフェストでターゲットのデバイス ファミリを指定しない場合は、誤ってを開くことが意図しない Windows 10 デバイスのようにアプリ。 目的の Windows 10 デバイス ファミリを指定する次の手順に従ってし、[ストアに送信するパートナー センターでアプリケーション パッケージをアップロードするときに、適切なデバイス ファミリを選択することを再確認してください。](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

Visual Studio では、このフィールドを設定するには、Package.appxmanifest を右クリックして、「「表示コード」を選択し、TargetDeviceFamily 名フィールドが見つかりません。 既定では、次のようになります。

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

場合は、アプリが作成されます**HoloLens**、それだけにインストールされている HoloLens"Windows.Holographic"のターゲット デバイス ファミリを指定することによってをことを確認します。 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

場合は、アプリが作成されます**Windows Mixed Reality イマーシブ ヘッドセット**、のみにインストールされている Windows 10 Fall Creators Update (Windows Mixed Reality するために必要) を使用して Windows 10 Pc でターゲットを指定することを確認できます"Windows.Desktop"と「10.0.16299.0」の MinVersion のデバイス ファミリ。

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

最後に、アプリの両方を実行する場合は**HoloLens と Windows Mixed Reality イマーシブ ヘッドセット**、アプリのみ利用可能になっている 2 つのデバイス ファミリにすると同時に、適切な各ターゲットを確認しますそれぞれ、MinVersion を各ターゲット デバイス ファミリ用の行を含めることによって Windows の最小バージョン。

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

デバイス ファミリを読み取ることによって対象設定についての詳細については、 [TargetDeviceFamily UWP ドキュメント](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily)します。

### <a name="associate-app-with-the-store"></a>アプリケーションをストアと関連付ける

Visual Studio ソリューションの [プロジェクト] メニューから「Store > を関連付けるアプリ ストアと」を選択します。 これを行う場合は、アプリ内購入および通知シナリオをテストできます。 ストアからアプリを関連付けるときに、これらの値は、ローカル コンピューターに現在のプロジェクトのアプリ マニフェスト ファイルにダウンロードされます。
* パッケージ表示名
* パッケージ名
* 発行者 ID
* 発行者表示名
* バージョン

マニフェストのカスタム .xml ファイルを作成し、既定の package.appxmanifest ファイルを上書きした場合は、ストアでアプリを関連付けることはできません。 カスタム マニフェスト ファイルをストアに関連付けるしようとすると、エラー メッセージが表示されます。

### <a name="creating-an-upload-package"></a>アップロード パッケージの作成

ガイドラインに従う[Windows 10 用のパッケージ化のユニバーサル Windows アプリ](https://msdn.microsoft.com/library/hh454036.aspx#Anchor_2)します。

パッケージを使用して、アップロード パッケージの作成の最後の手順を検証、 [Windows アプリ認定キット](#windows-app-certification-kit)します。

詳細についてはするがも追加するパッケージ HoloLens 専用の他の Windows 10 デバイス ファミリで利用可能な既存の製品に場合、[特定の顧客に配信されるバージョン番号がパッケージに影響する方法](https://msdn.microsoft.com/library/windows/apps/mt188602.aspx)、および[さまざまなオペレーティング システムにパッケージの配布方法](https://msdn.microsoft.com/library/windows/apps/mt188601.aspx)します。

一般的なガイダンスは、ストアによって分散のいずれかをデバイスに適用される最高バージョン番号パッケージで指定されます。

Windows.Universal パッケージと Windows.Holographic パッケージがある Windows.Universal パッケージがより高いバージョン番号を持つ場合は、HoloLens のユーザーはパッケージをダウンロードより高いバージョン番号 Windows.Universal、Windows.Holographic ではなくパッケージです。 この問題を解決するいくつかあります。
1. Windows.Holographic に常に Windows.Universal など、プラットフォームに依存しないパッケージより新しいバージョン番号があるなど、プラットフォームの特定のパッケージを確認します
2. Windows.Universal 場合、プラットフォーム固有のパッケージの代わりにパッケージ化することで使用できる特定のプラットフォームの Windows.Universal パッケージようにアプリをパッケージされません。

>[!NOTE]
> 複数のターゲット デバイス ファミリに適用される 1 つのパッケージを宣言することができます。

3. すべてのプラットフォーム間で機能する 1 つの Windows.Universal パッケージを作成します。 このサポートはありません今ため、上記の解決はお勧めします。

## <a name="testing-your-app"></a>アプリのテスト

### <a name="windows-app-certification-kit"></a>Windows アプリ認定キット

Visual Studio でのパートナー センターに送信するアプリ パッケージを作成するときに、アプリ パッケージの作成ウィザードには作成されるパッケージに対して、Windows アプリ認定キットを実行することが求められます。 ストアに滑らかな送信プロセスを確保するためにされていることを確認することをお、 [Windows アプリ認定キット テスト](https://msdn.microsoft.com/library/windows/apps/jj657973.aspx)ストアに提出する前に、ローカル コンピューターに、アプリに対する渡します。 Windows アプリ認定キットをリモート HoloLens で実行されているは現在サポートされていません。

### <a name="run-on-all-targeted-device-families"></a>すべての対象となるデバイス ファミリで実行します。

Windows ユニバーサル プラットフォームでは、すべての Windows 10 デバイス ファミリで動作する 1 つのアプリケーションを作成できます。 ただし、すべてのデバイス ファミリでユニバーサル Windows アプリの動作を保証しません。 アプリを HoloLens または他の Windows 10 ターゲット デバイス ファミリで使用できるようにすることを選択することが重要した[アプリをテストする](testing-your-app-on-hololens.md)良好なエクスペリエンスをそれらのデバイス ファミリの各します。

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>複合現実アプリ ストアを送信します。

Unity プロジェクトに基づいている mixed reality アプリを送信する場合を参照してください[ビデオ](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app)最初。

HoloLens やイマーシブ ヘッドセットで動作するアプリは、Microsoft Store の任意の UWP アプリを送信するように一般に、Windows Mixed Reality の送信です。 すると[名前を予約して、アプリを作成した](https://docs.microsoft.com/windows/uwp/publish/create-your-app-by-reserving-a-name)、従う必要があります、 [UWP 送信チェックリスト](https://docs.microsoft.com/windows/uwp/publish/app-submissions)します。

最初に行うことの 1 つは[カテゴリおよびサブカテゴリを選択](https://docs.microsoft.com/windows/uwp/publish/category-and-subcategory-table)複合現実エクスペリエンス。 重要ですした**アプリの最も正確なカテゴリを選択**ストアの適切なカテゴリで、アプリケーションを販売して関連する検索クエリを使用して表示することを確認できます。 **VR タイトルを一覧表示するように、アプリより優れた公開ゲームは発生しません**と調整の詳細については、カテゴリ内でいっぱいに表示されないことができない可能性があります。

ただし、mixed reality 固有項目を選択する先が送信プロセスには 4 つの主要な領域があります。
1. **[製品宣言](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** セクション[プロパティ](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)します。
2. **[システム要件](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** セクション[プロパティ](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)します。
3. **[デバイス ファミリ可用性](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** セクション[パッケージ](https://docs.microsoft.com/windows/uwp/publish/upload-app-packages)します。
4. いくつか、 **[ストアの一覧ページ](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** フィールド。

### <a name="mixed-reality-product-declarations"></a>複合現実の製品の宣言

**[プロパティ](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** ページのアプリの提出プロセスでの複合現実に関連するいくつかのオプションがあります、 **[製品宣言](https://docs.microsoft.com/windows/uwp/publish/app-declarations)** セクション。

![複合現実の製品の宣言](images/product-declarations-900px.png)<br>
複合現実の製品の宣言

最初に、アプリが複合現実エクスペリエンスを提供する対象のデバイスの種類を識別するためにします。 これにより、アプリがストアでの Windows Mixed Reality コレクションに含まれていると、イマーシブ ヘッドセットを接続した後 (または HoloLens のストアを参照するときに)、ストアを閲覧するユーザーに提示されること。

横に"このエクスペリエンスは Windows Mixed Reality に適しています"。
* チェック、 **PC**イマーシブ ヘッドセットがユーザーの PC に接続されているときに、アプリは、VR エクスペリエンスを提供する場合にのみボックスします。 アプリは、イマーシブ ヘッドセットの実行にのみ設計されて かどうか、または、標準的な PC ゲーム/アプリ ヘッドセットが接続されている場合は、複合現実のモードやボーナスのコンテンツを提供するかどうかは、このボックスを確認する必要があります。
* チェック、 **HoloLens** HoloLens で実行した場合、アプリは holographic のエクスペリエンスを提供する場合にのみボックスします。
* 確認**両方**で両方のデバイスの種類など、アプリが複合現実を提供する場合、ボックスのエクスペリエンス、 [Mixed Reality Academy「プロジェクト アイランド」アプリ](mixed-reality-250.md)Build 2017 から。

上記の"PC"を選択した場合、「mixed reality のセットアップ」を設定します (アクティビティ レベル). これは、HoloLens の複合現実アプリは世界規模と、ユーザーは、セットアップ中に境界を定義しないと、イマーシブ ヘッドセットに接続されている Pc 上で実行する複合現実エクスペリエンスにのみ適用されます。
* 選択**Seated + 継続**場合は、アプリには、ユーザーが 1 つの位置 (例があります、ゲーム、航空機のコックピットに取り付けられている場所) で保持される意図は設計されています。
* 選択**すべてエクスペリエンス**かどうか、アプリがあり、ユーザーは、セットアップ中に、そのユーザーが定義されている境界内の周りでについて説明しますが、目的に設計された (たとえばがゲームの場所にあります側ステップとアヒルが攻撃を避ける)。

### <a name="mixed-reality-system-requirements"></a>複合現実のシステム要件

**[プロパティ](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** ページのアプリの提出プロセスでの複合現実に関連するいくつかのオプションがあります、 **[システム要件](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties#system-requirements)** セクション。

![システム要件](images/system-reqs-800px.png)<br>
システム要件

このセクションでは、for、mixed reality アプリ (必須) ハードウェアの最小および推奨される (省略可能) のハードウェアを識別します。

**ハードウェアの入力:**

アプリがサポートしているかを潜在顧客に指示する、チェック ボックスを使用して**マイク**(の[音声入力](voice-input.md))、  **[Xbox コント ローラーまたはゲームパッド](hardware-accessories.md#bluetooth-gamepads)**、や **[Windows Mixed Reality モーションのコント ローラー](motion-controllers.md)** します。 この情報がストアでアプリの製品詳細ページが提示され、アプリのアプリ、ゲームの適切なコレクションに含めるに役立つ (たとえば、コレクションからアニメーション コント ローラーをサポートするすべてのゲームの存在可能性があります)。

「ハードウェアの最小」または入力の種類に対して「推奨ハードウェア」のチェック ボックスを選択する方法について熟慮します。 

次に、例を示します。 
* ゲームでは、アニメーション コント ローラーが必要ですが、マイクを使用して音声入力を受け付けるの場合は、「Windows Mixed Reality アニメーション コント ローラー、」の横にある「ハードウェアの最小」チェック ボックスが「マイク」の横にある「推奨されるハードウェア」のチェック ボックスを選択します 
* か、Xbox コント ローラー/ゲームパッドやアニメーション コント ローラーと、ゲームをプレイすることができます、「Xbox コント ローラーまたはゲームパッド」の横にある「ハードウェアの最小」チェック ボックスをオンし、"Windows Mixed Reality モーションの横にある「推奨されるハードウェア」のチェック ボックスをオンする可能性があります。コント ローラー"モーションのコント ローラーとして可能性があります、ゲームパッドからエクスペリエンスにステップ アップが提供されます。

**Windows Mixed Reality イマーシブ ヘッドセット。**

イマーシブ ヘッドセットが、アプリを使用するために必要なまたは省略可能でかどうかを示すは、顧客満足度および教育機関向けに重要です。

場合は、アプリでは、*のみ*イマーシブ ヘッドセットを使用する、「Windows Mixed Reality イマーシブ ヘッドセット」の横にある「ハードウェアの最小」チェック ボックスをオン これが提示されるストアのアプリの製品詳細ページで購入ボタンの上を警告としては従来のデスクトップ アプリのように自分の PC で動作するアプリを購入している、顧客の考えしないようにします。

アプリは、従来の PC のアプリのように、デスクトップで実行されますは、イマーシブ ヘッドセットが接続されている場合に、VR エクスペリエンスを提供する場合、アプリの完全な内容が、使用できるかどうか (一部のみ)、"の Windows Mixed Reality の横にある「推奨されるハードウェア」のチェック ボックスをオンイマーシブ ヘッドセット。" 警告は発生しません購入ボタンの上、アプリの製品詳細ページで、イマーシブ ヘッドセットせず、従来のデスクトップ アプリとして関数アプリが接続されている場合。

**PC の仕様:**

できるだけ Windows Mixed Reality ヘッドセット没入型のユーザーの数に到達するアプリを実行する場合に、たい[ターゲット](understanding-performance-for-mixed-reality.md)PC 仕様[統合型グラフィックスを使用して Windows Mixed Reality Pc](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)します。

かどうか、mixed reality アプリの対象を Windows Mixed Reality PC の最小要件または特定の PC 構成が必要です (などの専用 GPU、 [Windows Mixed Reality Ultra PC](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)、関連するで示す必要があります「ハードウェアの最小」列の仕様を PC。

良くし、または特定の PC 構成またはグラフィックス カード上の高解像度画像を提供する、mixed reality アプリが設計されている場合は、「推奨されるハードウェア」列に関連する PC の仕様をことを示す必要があります。

これは、mixed reality アプリが PC に接続されている、イマーシブ ヘッドセットを使用してのみに適用されます。 HoloLens でのみ、mixed reality アプリを実行する場合は、HoloLens は 1 つだけのハードウェア構成を持つ PC の仕様を示す必要はありません。

### <a name="device-family-availability"></a>デバイス ファミリの利用可否

したら[アプリを正しくパッケージ化されて](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements)Visual Studio で、アプリの提出プロセスの [パッケージ] ページにアップロードする必要がありますのテーブルが生成、アプリが使用可能になりますデバイス ファミリを特定します。

![デバイス ファミリ可用性テーブル](images/device-family-table-900px.png)<br>
デバイス ファミリ可用性テーブル

イマーシブ ヘッドセット、mixed reality アプリが動作する場合は、テーブルの最低の"Windows 10 Desktop"を選択してください。 場合は、mixed reality アプリの動作にし、HoloLens、少なくとも"Windows 10 Holographic"が選択されます。 Windows Mixed Reality ヘッドセットの両方の種類で、アプリを実行する場合と同様、 [Mixed Reality Academy「プロジェクト アイランド」アプリ](mixed-reality-250.md)、"Windows 10 Desktop"と"Windows 10 Holographic"の両方を選択する必要があります。

>[!TIP]
>多くの開発者は、パッケージ マニフェストとパートナー センターでアプリとパブリッシャー アカウント情報の間の不一致に関連するアプリのパッケージをアップロードするときにエラーを実行します。 これらのエラーは、Windows 開発者アカウント (パートナー センターにサインインに使用するもの) に関連付けられている同じアカウントで Visual Studio にサインインして多くの場合、回避できます。 同じアカウントを使用する場合にパッケージ化する前に、アプリを Microsoft Store では、その id に関連付けることができます。

![Microsoft Store アプリを関連付ける](images/associate-your-app-700px.png)<br>
Visual Studio での Microsoft Store アプリを関連付ける

### <a name="store-listing-page"></a>ストアの一覧ページ

[ストア一覧](https://docs.microsoft.com/windows/uwp/publish/create-app-store-listings)アプリの提出のページ処理、有用な情報を追加するには、mixed reality アプリに関するいくつかの場所があります。

>[!IMPORTANT]
>追加する必要があります、アプリが正しく、ストアによって分類され、Windows Mixed Reality 顧客に探索できるように、 **"Windows Mixed Reality"** (見つかります検索語句を展開して、アプリの「検索語句」の 1 つとして「フィールドを共有」セクション)。

![検索語句を Windows Mixed Reality を追加します。](images/search-terms-800px.png)<br>
"Windows Mixed Reality"の検索語句を追加します。

## <a name="offering-a-free-trial-for-your-game-or-app"></a>ゲームまたはアプリの無料試用版の提供

多くのコンシューマーは Windows Mixed Reality イマーシブ ヘッドセットを購入する前に仮想現実と未経験に制限されます。 大量のゲームの内容はわかりません、没入型エクスペリエンスで、独自の快適性しきい値に馴染みがない可能性があります。 多くのお客様と用バッジの付いたいない Pc で Windows Mixed Reality イマーシブ ヘッドセットを試みることができますも[Windows Mixed Reality Pc](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)します。 これらの考慮事項により強くお勧めオファリングを[無料試用版](https://docs.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#free-trial)有料の複合現実アプリやゲームをします。

## <a name="see-also"></a>関連項目
* [Mixed Reality](mixed-reality.md)
* [開発の概要](development-overview.md)
* [アプリのビュー](app-views.md)
* [複合現実のパフォーマンスを理解](understanding-performance-for-mixed-reality.md)
* [Unity のパフォーマンスに関する推奨事項](performance-recommendations-for-unity.md)
* [HoloLens でアプリのテスト](testing-your-app-on-hololens.md)
* [Windows Mixed Reality 最小 PC ハードウェアの互換性ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
