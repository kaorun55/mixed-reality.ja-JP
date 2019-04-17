---
title: 複合現実の 2D の UWP アプリを更新します。
description: この記事では、HoloLens と Windows Mixed Reality イマーシブ ヘッドセットで実行する既存 2D ユニバーサル Windows プラットフォーム アプリの更新について説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 2D アプリ、UWP、フラットなアプリ、HoloLens、イマーシブ ヘッドセット、アプリ モデルでは、バックアップ、ボタン、アプリ バー、dpi スケールの解決
ms.openlocfilehash: 35a2e7774a79e35893821467f7e9ef8c004efa20
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602184"
---
# <a name="updating-2d-uwp-apps-for-mixed-reality"></a>複合現実の 2D の UWP アプリを更新します。

Windows Mixed Reality により、ユーザーを物理またはデジタルの世界では、周囲に適切な場合、ホログラムを参照してください。 基本的には、HoloLens とに、イマーシブ ヘッドセット アクセサリをアタッチするデスクトップ Pc の両方が Windows 10 デバイスです。これは、2D アプリとしてストアにほぼすべてのユニバーサル Windows プラットフォーム (UWP) アプリを実行することであることを意味します。

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a>複合現実の 2D の UWP アプリの作成

Mixed reality ヘッドセットを 2D アプリをお届けする最初の手順では、デスクトップ モニターでは、標準的な 2D アプリとして実行されているアプリを取得します。

### <a name="building-a-new-2d-uwp-app"></a>新しい 2D UWP アプリのビルド

複合現実用の新しい 2D アプリをビルドするには、標準的な 2D のユニバーサル Windows プラットフォーム (UWP) アプリをビルドするだけです。 その他のアプリの変更は、複合現実でスレート型として実行するには、そのアプリは必要ありません。

2D の UWP アプリの構築を開始、チェック アウト、[最初のアプリを作成する](https://docs.microsoft.com/windows/uwp/get-started/your-first-app)記事。

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a>UWP への既存の 2D ストア アプリの追加

ストアで 2D Windows アプリを既にがある場合、Windows 10 ユニバーサル Windows プラットフォーム (UWP) が対象とする最初ようにする必要があります。 ストア アプリで今すぐ必要がありますすべて、潜在的な開始点を次に示します。
<br>

|  開始点  |  AppX マニフェストのプラットフォーム ターゲット  |  このユニバーサルにする方法は? | 
|----------|----------|----------|
|  Windows Phone (Silverlight)  |  Silverlight アプリケーションのマニフェスト |  [WinRT に移行します。](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx) | 
|  Windows Phone 8.1 ユニバーサル  |  8.1 プラットフォーム ターゲットが含まれていない AppX マニフェスト  |  [アプリをユニバーサル Windows プラットフォームに移行します。](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows ストア 8  |  プラットフォーム ターゲットが含まれていない 8 AppX マニフェスト  |  [アプリをユニバーサル Windows プラットフォームに移行します。](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows ストア 8.1 ユニバーサル  |  8.1 プラットフォーム ターゲットが含まれていない AppX マニフェスト  |  [アプリをユニバーサル Windows プラットフォームに移行します。](https://msdn.microsoft.com/library/mt148501.aspx) | 

今日 (「PC、Mac、Linux のスタンドアロン」ビルド ターゲット) の Win32 アプリとしてビルド 2D Unity アプリがある場合は、Unity を代わりに「ユニバーサル Windows プラットフォーム」ビルドのターゲットに切り替えることで、複合現実を対象ことができます。

HoloLens Windows.Holographic のデバイス ファミリを使用して具体的には、アプリを制限することができますの方法について説明します[下](#publish-and-maintain-your-universal-app)します。

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a>Windows Mixed Reality イマーシブ ヘッドセットで 2D アプリを実行します。

2D アプリは、場所を開発し、モニターで試して、デスクトップ コンピューターに配置した、没入型のデスクトップ ヘッドセットで試す準備ができている既に!

Mixed reality ヘッドセット内で [スタート] メニューに移動し、そこからアプリを起動するだけです。 デスクトップ シェルおよび holographic シェルは、UWP アプリの同じセットを共有するので、アプリが既に存在している Visual Studio からデプロイすると、.

## <a name="targeting-both-immersive-headsets-and-hololens"></a>イマーシブ ヘッドセットと HoloLens の両方を対象とします。

これで終了です。 アプリは、Windows 10 ユニバーサル Windows プラットフォーム (UWP) を使用しています。

アプリは、デスクトップ、モバイル、Xbox、Windows Mixed Reality イマーシブ ヘッドセット、HoloLens も、将来の Windows デバイスなど、今日の Windows デバイスで実行できるようになりました。 ただし、実際にこれらのデバイスのすべてを対象とするアプリでは Windows.Universal デバイス ファミリをターゲットとすることを確認する必要があります。

### <a name="change-your-device-family-to-windowsuniversal"></a>Windows.Universal をデバイス ファミリに変更します。

これで、Windows 10 UWP アプリは HoloLens で実行できるようにする、AppX マニフェストに進みましょう。
* アプリのソリューション ファイルを開く**Visual Studio**アプリ パッケージのマニフェストに移動します
* 右クリックして、 **Package.appxmanifest**ソリューション内のファイルしに移動**コードの表示**<br>
  ![ソリューション エクスプ ローラーで package.appxmanifest](images/openappxmanifest-500px.png)<br>
* ターゲット プラットフォームが依存関係セクション Windows.Universal であることを確認します。
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* 保存してください。

開発環境 Visual Studio を使用しない場合は、開く**AppXManifest.xml**対象にしていることを確認する任意のテキスト エディターで、 **Windows.Universal** *TargetDeviceFamily*します。

### <a name="run-in-the-hololens-emulator"></a>HoloLens のエミュレーターで実行します。

UWP アプリが"Windows.Universal"を対象となったみましょうアプリのビルドし、で実行、 [HoloLens のエミュレーター](using-the-hololens-emulator.md)します。
* 必ず確保[HoloLens のエミュレーターがインストールされている](install-the-tools.md)します。
* Visual Studio で、選択、 **x86**ビルド アプリの構成

  ![x86 ビルドの Visual Studio での構成](images/x86setting.png)<br>
* 選択**HoloLens のエミュレーター**で、デプロイ ターゲット ドロップダウン メニュー

  ![配置ターゲット リスト HoloLens のエミュレーター](images/deployemulator-500px.png)<br>
* 選択**デバッグ > [デバッグ開始]** アプリを展開およびデバッグを開始します。
* エミュレーターが起動し、アプリを実行します。
* キーボード、マウス、または Xbox コント ローラーを使用して起動する世界では、アプリを配置します。

  ![HoloLens のエミュレーターが UWP サンプルの読み込み](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a>次のステップ

この時点では、次の 2 つのいずれかが発生することができます。
1. アプリはそのスプラッシュを表示して、エミュレーターに配置されて後の実行を開始! すごい！
2. または、2D ホログラムの読み込みアニメーションを確認した後は読み込みを停止し、アプリのスプラッシュ スクリーンにだけ表示されます。 つまり、何らかの問題を複合現実でのアプリを実現方法を理解するのには追加の調査がかかります。

HoloLens で開始する UWP アプリの原因の下部に取得する、デバッグする必要があります。

### <a name="running-your-uwp-app-in-the-debugger"></a>デバッガーでの UWP アプリを実行します。

次の手順で、Visual Studio デバッガーを使用して、UWP アプリのデバッグを説明します。
* これをいない場合は、Visual Studio でソリューションを開きます。 ターゲットへの変更、 **HoloLens のエミュレーター**し、ビルド構成を**x86**します。
* 選択**デバッグ > [デバッグ開始]** アプリを展開およびデバッグを開始します。
* 世界、マウス、キーボード、または Xbox コント ローラーで、アプリを配置します。
* ここで、アプリ コードでどこかに visual Studio が分割する必要があります。
  - アプリのクラッシュまたはハンドルされないエラーのため、デバッガーを中断しないすぐは、すべてが実行されていることを確認および機能へのアプリのコア機能のテスト パスを移動します。 (内部例外が処理されている) 下図のようにエラーが発生する可能性があります。 アプリのエクスペリエンスに影響する内部エラーを見逃すことはないことを確認するには、すべてが期待どおりに動作を確認する単体テスト、自動テストを実行します。

![HoloLens のエミュレーターは、システムの例外を示す UWP サンプルと共に読み込まれる](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a>UI を更新します。

これで、UWP アプリは、イマーシブ ヘッドセットまたは 2D ホログラムとして HoloLens で実行されているが、次にしましょう美しい見た目を確認します。 考慮事項を次に示します。
* 853 x 480 有効ピクセルに固定の解像度とは、相当 DPI で、Windows Mixed Reality は 2D のすべてのアプリを実行します。 設計にこのスケールの微調整が必要なかどうかを考慮し、HoloLens、イマーシブ ヘッドセットを改善するために以下の設計ガイダンスを確認します。
* Windows Mixed Reality[はサポートしていません](app-model.md)2D のライブ タイルです。 その情報をアプリに戻すを検討してください、コア機能には、ライブ タイルに情報が表示されている場合、または探索[3D アプリ ランチャー](3d-app-launcher-design-guidance.md)します。

### <a name="2d-app-view-resolution-and-scale-factor"></a>2D アプリの表示解像度とスケール係数

![レスポンシブ デザインから](images/scale-500px.png)

Windows 10 では、すべてのビジュアル デ ザインを移動する実際の画面のピクセルから**有効ピクセル**します。 開発者は、次の Windows 10 ヒューマン インターフェイス ガイドラインの有効ピクセルは、その UI を設計し、Windows スケーリングにより、その有効ピクセルは適切なサイズ、つまり複数のデバイス、解像度、DPI、使いやすさなどです。これを参照してください[msdn 優れた読み取り](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx)これと詳細については、[ビルド プレゼンテーション](http://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx)します。

距離の範囲で、世界中のアプリを配置する独自の機能を使用しても、テレビのような表示距離は、最善の読みやすさと視線の先/ジェスチャとの対話を生成するためにお勧めします。 そのため、Mixed Reality 自宅で仮想スレートでフラットな UWP ビューが表示されます。

**1280 x 720、150 %dpi** (853 x 480 有効ピクセル数)

この解決方法には、いくつかの利点があります。
* この有効ピクセル レイアウトは、タブレットや小規模のデスクトップと同じ情報密度について必要があります。
* これは、固定 DPI とデバイス間でシームレスなエクスペリエンスを有効にする Xbox One で実行されている UWP アプリの有効ピクセルと一致します。
* 動作して、世界中のアプリの距離の範囲の間でスケールするとき、このサイズは大丈夫です。

### <a name="2d-app-view-interface-design-best-practices"></a>2D アプリ ビュー インターフェイス設計のベスト プラクティス

**操作を行います。**
* に従って、 [Windows 10 ヒューマン インターフェイス ガイドライン (HIG)](https://dev.windows.com/design)スタイル、フォント サイズ、およびボタンのサイズ。 HoloLens では、互換性のあるアプリのパターン、判読できるテキストのサイズ、および適切なヒット ターゲットのサイズ変更、アプリを設定するために処理を行います。
* UI 次の手順のためのベスト プラクティスを確認します[レスポンシブ デザイン](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx)HoloLen の一意の解像度と DPI で最適に表示します。
* Windows の"light"の色のテーマの推奨事項を使用します。

**できません：**
* ユーザーが使い慣れたヘッドセットとの間に、複合現実で UI をも大幅に変更します。

### <a name="understand-the-app-model"></a>アプリ モデルを理解します。

[アプリ モデル](app-model.md)の多くのアプリがまとめて live、Mixed Reality ホームを使用する複合現実は設計されています。 これと考える複合現実と同等のデスクトップで、一度にで多くの 2D アプリを実行します。 これは、アプリのライフ サイクル、タイル、およびその他のアプリの主な機能に影響を与えます。

### <a name="app-bar-and-back-button"></a>アプリ バーと [戻る] ボタン

2D のビューは、そのコンテンツの上にアプリ バーで装飾されます。 アプリ バーでは、アプリ固有のパーソナル化の 2 つの点があります。

**タイトル:** が表示されます、 *displayname*のアプリ インスタンスに関連付けられたタイル

**: [戻る] ボタン**発生させる、 *[BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* 押されたときにイベント。 戻るボタンの可視性がによって制御される *[SystemNavigationManager.AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)* します。

![アプリ バーの 2D アプリ ビューでの UI](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)<br>
*アプリ バーの 2D アプリ ビューでの UI*

### <a name="test-your-2d-apps-design"></a>テストの 2D アプリの設計

テキストを読み取ることが、ボタンが不要、およびアプリ全体が正しく思わかどうかを確認するアプリのテストは重要です。 できます[テスト](testing-your-app-on-hololens.md)デスクトップ ヘッドセット、HoloLens、エミュレーター、または解像度が 1280 x 720 に設定を使用したタッチ デバイスで@150%。

## <a name="new-input-possibilities"></a>新しい入力可能性

HoloLens では、高度な深さセンサーを使用して、世界中のユーザーを参照しています。 これによりなどの高度な手のジェスチャ[ブルーム](gestures.md#bloom)と[エア タップ](gestures.md#air-tap)します。 強力なマイクも有効にする[エクスペリエンスを音声](voice-input.md)します。

デスクトップ ヘッドセットは、ユーザーがアプリをポイントし、アクションを実行するアニメーション コント ローラーを使用できます。 自分の視線の先を持つオブジェクトを対象とする、ゲーム パッドを使用することもできます。

変換する UWP アプリでは、このような複雑さのすべての処理は、Windows、[視線](gaze.md)、ジェスチャ、音声およびモーションをコント ローラーの入力[ポインター イベント](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events)入力メカニズムを抽象化します。 たとえば、ユーザーが自分の手でエア タップの完了またはアニメーション コント ローラーで、トリガーのプルが 2D のアプリケーションは、入力の取得元、タッチ スクリーンでとしてを押すと、2 D touch だけ表示そこを知る必要はありません。

HoloLens を UWP アプリを移行することと、入力を理解する必要が高レベルの概念やシナリオを次に示します。
* [視線](gaze.md)ホバー イベントは、メニューのフライアウトまたはアプリの周囲 gazing するだけでポップアップ表示するその他のユーザー インターフェイス要素をトリガーできますが予期せずに変わります。
* 視線の先が正確に表すマウス入力ではありません。 使用は、HoloLens、タッチ対応のモバイル アプリケーションと同様のヒット ターゲットを適切にサイズ。 アプリの端の小さな要素は、非常に困難と対話します。
* ユーザーは、2 本の指のパンにドラッグするスクロールから移動する入力モードを切り替える必要があります。 アプリは、タッチ入力用に設計された、2 本の指のパンの背後にある主要な機能がロックされていないことを確認を検討してください。 そうである場合は、2 本の指のパンを開始できるボタンのような代替入力手段のことを検討します。 やなどのマップ アプリ 2 本の指のパンとズームできますが、マイナス、プラス記号がシングル クリックで同じズーム相互作用をシミュレートするためにボタンを回転します。

[音声入力](voice-input.md)複合現実エクスペリエンスの重要な部分です。 音声ヘッドセットを使用する場合は、Cortana を強化する Windows 10 では、Api を設けました。

## <a name="publish-and-maintain-your-universal-app"></a>発行し、ユニバーサル アプリの管理

アプリが稼働するいると、アプリのパッケージ化する[Microsoft Store に提出](submitting-an-app-to-the-microsoft-store.md)します。

## <a name="see-also"></a>関連項目
* [アプリ モデル](app-model.md)
* [視線入力](gaze.md)
* [ジェスチャ](gestures.md)
* [アニメーション コント ローラー](motion-controllers.md)
* [音声](voice-input.md)
* [Microsoft Store にアプリの提出](submitting-an-app-to-the-microsoft-store.md)
* [HoloLens のエミュレーターを使用する](using-the-hololens-emulator.md)
