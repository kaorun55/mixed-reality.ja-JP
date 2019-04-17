---
title: Spectator ビュー
description: 外付けディスプレイでの複合現実エクスペリエンスのデモまたは複合現実エクスペリエンスのビデオを記録するための手段として、外部デバイスからホログラムを視覚化します。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Spectator ビュー、iPhone、iOS、iPad、OpenCV、カメラ、ARKit、HoloLens、Mixed Reality、MixedRealityToolkit、デモでは、レコード
ms.openlocfilehash: 77102cf5fb1c23f27f7f2d651c6ca1ae9df5a1d1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602271"
---
# <a name="spectator-view-for-hololens"></a>HoloLens の spectator ビュー

![Marker](images/SpecViewPhoneHero.jpg)


## <a name="current-refactor"></a>現在のリファクタリング

> [!NOTE]
>HoloLens の spectator ビューのリファクタリングがアクティブにされています。 この作業は、プレビューを統合するためのものが、それをコードベースし、Pro HoloLens 2 のサポートを拡張します。 

現在の表示 Spectator ビューのリファクタリングの状態は MixedRealityToolkit と MixedRealityToolkit Unity の両方のリポジトリにある '機能/spectatorView' ブランチを参照してください。

https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/feature/spectatorView/Assets/MixedRealityToolkit.Extensions/SpectatorView

、

https://github.com/Microsoft/MixedRealityToolkit/tree/feature/spectatorView/SpectatorViewPlugin

## <a name="overview"></a>概要

ソックスを着けずに、HoloLens、ときに多くの場合、忘れている人を持たないことはできる信じられないことが発生することができません。 Spectator ビューを使用して、HoloLens ユーザーが自分の世界では 2D 画面に表示する使用できます。
Spectator ビュー (プレビュー) は、Spectator ビュー Pro ホログラムのプロ品質の記録の目的は、HD でホログラムの記録に高速で低コストのアプローチです。

次の表は、両方のオプションとその機能を示します。 ビデオ記録のニーズに最適なオプションを選択します。

|                                      | Spectator ビュー (プレビュー) |              Spectator Pro の表示              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| HD 品質                         |         フル HD         |        映画 (DSLR によって決定されます)、プロの品質      |
| 簡単なカメラの動き                      |            ✔            |                                             |
| 3 人目のビュー                    |            ✔            |                      ✔                      |
| 画面にストリームすることができます。           |            ✔            |                      ✔                      |
| 移植性があります。                             |            ✔            |                                             |
| ワイヤレス                             |            ✔            |                                             |
| 必要なハードウェアの追加         |     (iPhone または iPad)    | HoloLens + リモート テスト マシン群 + 三脚 + DSLR + PC + Unity |
| ハードウェアへの投資                  |           低           |                     高                    |
| クロスプラットフォーム                       |           iOS           |                                             |
| ビューアーが対話することができます。                  |            ✔            |                                             |
| ネットワークも不要です (UNET スクリプト) |            ✔            |                      ✔                      |
| ランタイムのセットアップの実行時間               |         インスタント         |                     スロー (低速)                    |

## <a name="spectator-view-preview"></a>Spectator ビュー (プレビュー)

![Marker](images/SpecViewPhoneDemo.jpg)

### <a name="use-cases"></a>使用事例

- HD の映画ホログラム:Spectator ビュー (プレビュー) を使用して、iPhone を使用して、複合現実エクスペリエンスを記録できます。 フル HD に記録し、ホログラムともシャドウにアンチエイリアシングを適用します。 ホログラムのビデオをキャプチャするコスト効率に優れた、簡単な方法です。
- ライブ デモ:IPhone または iPad では、lag フリーから直接、Apple TV エクスペリエンス Stream ライブ複合現実です。
- ゲストのエクスペリエンスを共有します。HoloLens 以外のユーザーのスマート フォンまたはタブレットから直接ホログラムが発生することができるようにします。

### <a name="current-features"></a>現在の機能

- スマート フォンをセッションに追加するための自動検出をネットワークです。
- セッションの自動処理をため、ユーザーが正しいセッションに追加されます。
- ホログラム、ホログラム正確な同じ場所に表示されるすべてのユーザーのための空間同期します。
- iOS では、(ARKit が有効なデバイス) をサポートします。
- IOS の複数のゲストです。
- ビデオ + ホログラム + 環境音ホログラム サウンドの録音。
- ビデオを保存、電子メール、またはその他のサポートのアプリと共有するために、シートを共有します。


>[!NOTE] 
>Spectator ビュー (プレビュー) のコードは、Spectator ビュー Pro バージョンのコードでは使用できません。 ホログラムのビデオ記録が必要な場合、新しいプロジェクトでの実装をお勧めします。

<br>

>[!VIDEO https://www.youtube.com/embed/3fXlPw_FGLg]


### <a name="licenses"></a>ライセンス

- [OpenCV - (3 句 BSD ライセンス)](https://opencv.org/license.html)
- [Unity ARKit - (MIT ライセンス)](https://bitbucket.org/Unity-Technologies/unity-arkit-plugin/src/3691df77caca2095d632c5e72ff4ffa68ced111f/LICENSES/MIT_LICENSE?at=default&fileviewer=file-view-default)

## <a name="how-to-set-up-spectator-view-preview"></a>Spectator ビュー (プレビュー) を設定する方法

### <a name="requirements"></a>要件

- [Spectator ビュー プラグインと必要な OpenCV バイナリ](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin)-Spectator ビューのネイティブ プラグインを構築する方法の詳細については下にあります。 生成されたバイナリからは、次の必要があります。

    - opencv_aruco343.dll
    - opencv_calib3d343.dll
    - opencv_core343.dll
    - opencv_features2d343.dll
    - opencv_flann343.dll
    - opencv_imgproc343.dll

    - zlib1.dll
    - SpectatorViewPlugin.dll
- Spectator ビューでは、そのネットワークの検出と空間的な同期の Unity Networking (UNET) を使用します。 つまり、アプリケーションの中にすべての対話機能をデバイス間で同期する必要があります。
- Unity 2017.2.1p2 またはそれ以降
- ハードウェア
    - HoloLens、
    - Windows 10 を実行している Windows PC
    - ARKit 互換性のあるデバイス (iPhone 6 s 以降/iPad Pro 2016 以降/iPad 2017 以降)-iOS 11 を実行している以上
    - Mac で xcode 9.2 以降
- Apple 開発者アカウント、無料または[有料](https://developer.apple.com/)
- Microsoft Visual Studio 2017

### <a name="building-the-spectator-view-native-plugin"></a>Spectator ビューのネイティブ プラグインを構築

必要なファイルを生成するには、次の手順を実行します。 https://github.com/Microsoft/MixedRealityToolkit/blob/master/SpectatorViewPlugin/README.md

### <a name="project-setup"></a>プロジェクトのセットアップ

1. シーン内のすべての見える gameobjects は、世界のルート gameobject の下に含まれていることを確認、シーンを準備します。

    ![世界のルート](images/SpecViewPhoneWorldRoot2.PNG)

2. SpectatorView プレハブの追加 ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab)) シーンにします。
3. SpectatorViewNetworking プレハブの追加 ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab)) シーンにします。
4. SpectatorViewNetworking gameobject を選択し、SpectatorViewNetworkingManager コンポーネントには、いくつかの点をリンクすることができます。 左はそのまま残る場合、このコンポーネントは、実行時に必要なスクリプトの検索されます。
    - マーカー検出 HoloLens SpectatorView/Hololens/MarkerDetection を -> します。
    - マーカー生成 3D SpectatorView、IPhone、SyncMarker/3DMarker を -> します。

    ![SpectatorView ネットワーク探索](images/SpecViewPhoneNetworkDiscovery.PNG)

### <a name="networking-your-app"></a>アプリのネットワーク

- Spectator 表示では、そのネットワークの UNET が使われのすべてのホスト クライアント接続を管理します。
- アプリの特定のデータは、同期され、SyncVars、NetworkTransform、NetworkBehavior などを使用して実装する必要があります。
- Unity のネットワークの詳細については次を参照してください[マルチ プレーヤーとネットワーク](https://docs.unity3d.com/Manual/UNet.html)します。 (注。UNet は非推奨とされました。Spectator ビュー コードベースの現在のリファクタリングは、この問題に対処されます)

### <a name="building-for-each-platform-hololens-or-ios"></a>HoloLens (iOS) は、各プラットフォームの構築

- IOS をビルドする場合は、まだこのプラットフォームと互換性はないために、MRTK の GLTF コンポーネントを削除するを確認します。
- SpectatorView プレハブの最上位レベルでは、' プラットフォーム スイッチャー ' と呼ばれるコンポーネントです。 ビルドするプラットフォームを選択します。
    - 'Hololens' を選択した場合、非アクティブになる SpectatorView プレハブで iPhone gameobject の下にあるすべての gameobject とアクティブになる 'Hololens' 下のすべての gameobject が表示されます。
    - これは少し時間がかかるプラットフォームによって選択すると、HoloToolkit されているプロジェクトの追加または削除します。

    ![プラットフォームのスイッチャー](images/SpecViewPhoneSwitcher.PNG)

- Unity と未解決の問題により同じ Unity エディターのインスタンス (do 間終了させない Unity のビルド) を使用してアプリケーションのすべてのバージョンをビルドすることを確認します。

### <a name="running-your-app"></a>アプリケーションを実行します。

作成すると、デプロイするアプリケーションの iPhone と HoloLens のバージョンが、これらを接続することができる必要があります。

1. デバイスの両方を同じ Wi-fi ネットワークにあることを確認します。
2. 不特定の順序で、両デバイスでアプリケーションを起動します。 Iphone の場合、アプリケーションを開始するプロセスは、HoloLens のカメラをオンにし、写真が撮影を開始をトリガーする必要があります。
3. IPhone アプリが起動するとすぐに、床やテーブルなどのサーフェスを検索します。 サーフェスが見つかった場合は、次のようなマーカーが表示されます。 HoloLens にこのマーカーを表示します。

    ![Marker](images/SpecViewPhoneMarker.PNG)

4. マーカーが検出されましたが非表示、HoloLens とデバイスの両方の接続し空間的に同期する必要があります。

### <a name="recording-video"></a>記録のビデオ

1. IPhone からビデオを保存して、キャプチャをタップし、1 秒間、画面を保持します。 これにより、記録メニューが開きます。
2. 赤い録画ボタンをタップして、画面の記録を開始する前に、カウント ダウンが開始されます。
3. 記録タップを終了し、別の 1 秒間、画面を押しながら、し、[停止] ボタンをタップします。
4. プレビュー ボタン (青色のボタン) が表示されます、録画されたビデオが読み込まれたら、録画したビデオを見るにタップします。
5. 共有のシートを開き、カメラ ロールに保存 を選択します。

### <a name="example-scene"></a>シーンの例

例のシーンが見つかります[HoloToolkit-Examples\SpectatorView\Scenes\SpectatorViewExample.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpectatorView/Scenes/SpectatorViewExample.unity)

### <a name="troubleshooting"></a>トラブルシューティング

**Unity エディターは、HoloLens デバイスによってホストされているセッションに接続できません。**

- これは、Windows ファイアウォールで可能性があります。
- Windows ファイアウォールのオプションに移動します。
- アプリまたは Windows ファイアウォールを使用して機能を許可します。
- すべてのインスタンスの一覧のティックで Unity エディターのドメイン、プライベートおよびパブリック。
- Windows ファイアウォールのオプションに戻ります。
- [詳細設定] をクリックします。
- [受信の規則] をクリックします。
- Unity エディターのすべてのインスタンスには、緑色のチェックが必要です。
- Unity エディターのすべてのインスタンスに対して、緑のチェック マークがないです。
    - ダブルクリックしてください。
    - アクションでは、ダイアログは、接続を許可するを選択します。
    - [OK] をクリックします。
    - Unity エディターを再起動します。

**実行時に、iPhone 画面の質問「を検索するフロア…」AR マーカーは表示されません。**

- 水平画面ので試してくださいフロアまたはテーブルの方に iPhone カメラを指すは、iPhone を探します。 これによって、ARKit HoloLens と空間的に同期するために必要なサーフェスを検索します。

**HoloLens のカメラを有効にしません iPhone が参加を試むときに自動的にします。**

- HoloLens と iPhone の両方が同じ Wi-fi ネットワークで実行されていることを確認します。

**モバイル デバイス上の Spectator ビュー アプリケーションを起動するときにそのカメラ Spectator ビューの他のアプリを実行している他の hololens 有効にします。**

- Goto NewDeviceDiscovery コンポーネントと 2 つの一意の値にブロードキャスト キーおよびブロードキャストの両方のポートを変更します。
- SpectatorViewDiscovery に移動し、別のセットの一意の番号に、キーのブロードキャストとブロードキャストのポートを変更します。

**Mac の Unity エディターで、HoloLens を接続できません。**

- これは、Unity のバージョンにリンクできますが、既知の問題です。 IPhone を構築する必要がありますも動作し、通常どおりに接続します。

**HoloLens カメラでは、オンが、マーカーをスキャンすることではありません。**

- Unity エディターの同じインスタンス (do 間終了させない Unity のビルド) を使用して、アプリケーションのすべてのバージョンを作成することを確認します。 Unity の不明な問題が原因になります。

## <a name="spectator-view-pro"></a>Spectator Pro の表示

![Spectator 設定の表示](images/spectatorview-300px.png)

Spectator ビューの Pro を使用して、これら 4 つのコンポーネントが含まれます。
1. 基づく spectator ビューを有効にするには、具体的にはビルドされたアプリ[複合現実での経験を共有](shared-experiences-in-mixed-reality.md)します。
2. ソックスを着けずに HoloLens、アプリを使用してユーザー。
3. 人称視点のビデオを提供する、spectator ビュー カメラ装置です。
4. 実行しているアプリの共有エクスペリエンスおよび複合、ホログラム spectator ビューのビデオにデスクトップ PC。

![Spectator ビューの Pro 設定](images/hololensspectatorview-500px.jpg) 

### <a name="use-cases"></a>使用事例

>[!VIDEO https://www.youtube.com/embed/DgIHjxoPy_c]


*Spectator ビューは、静止画像、ビデオ クリップ、またはライブ デモになるかどうか、holographic せましょうの共有を使用できます。*


このテクノロジと連動する次の 3 つの主要なシナリオがあります。

**1.写真をキャプチャ**<br>
このテクノロジを使用して、ホログラムの高解像度のイメージをキャプチャできます。 これらのイメージは、イベントのマーケティング コンテンツを紹介するを潜在的なクライアントに送信または Windows Store にアプリケーションを送信することもできます。 どの写真のカメラを使用してこれらのイメージをキャプチャしたいのかを決定する、そのため、品質 DSLR カメラこともできます。


![Spectator ビュー Pro 写真キャプチャのサンプル](images/fall-350px.jpg)<br>
*写真のキャプチャの例 - 溶岩をから床面が見えるようにされます。*


**2.ビデオのキャプチャ**<br>
ビデオは、多くの人と holographic アプリ エクスペリエンスを共有するためのメカニズムを示す最適なストーリーです。 Spectator ビューでは、最も適したアプリを紹介する方法をカメラ、レンズは、フレームを選択できます。 これは、ビデオ ハードウェアに基づくビデオ品質のコントロールで使用可能ながあります。

![Spectator ビュー Pro ビデオ キャプチャ例](images/spectatorviewvideo.gif)<br>
*ビデオ キャプチャ例 - 複合現実のコラボレーション エクスペリエンスを記録します。*


**3.ライブ デモ**<br>
Spectator ビューはライブ デモに対して推奨されるアプローチ安定または制御されたカメラの位置のままです。 高品質なビデオ_カメラを使用するため、大きな画面向けの高品質なイメージを作成することもします。 これは、ストリーミングが有効にするは、行で待機している一括の参加者に可能性があります、画面上のライブ デモに適したも。

### <a name="comparing-video-capture-techniques"></a>ビデオ キャプチャ手法の比較

[実際のキャプチャを混合](mixed-reality-capture.md)(MRC) の最初のユーザーの観点から、HoloLens のユーザーが表示されるコンポジット ビデオを提供します。 Spectator ビューでは、ホログラムとソックスを着けずに HoloLens デバイス ユーザーの環境を表示するビデオのオブザーバーを許可する - 3 人目の観点からビデオを生成します。 カメラの選択肢があるために、高い解像度と MRC イメージを使用する組み込み HoloLens カメラより優れた品質の画像が spectator ビューに生成もできます。 このため、spectator ビューよりマーケティングのビデオ、Windows ストア アプリの画像やユーザー向けのライブ ビューを射影は適しています。

![Microsoft での基調講演のプレゼンテーションで使用されるビューの Pro professional カメラを spectator](images/spectator-view-professional-red-camera-300px.jpg)<br>
*Microsoft での基調講演のプレゼンテーションで使用されるビューの Pro professional カメラを spectator*


Spectator ビューには、Microsoft HoloLens がの表示方法エクスペリエンスの対象ユーザーを非常に当初から、製品が 2015 年 1 月に発表したときの重要な要素がされました。 Professional の設定では、多くの要求と負荷の高い価格タグを必要があります。 たとえば、カメラは genlock 信号を使用して、追跡システム HoloLens と連携して正確なタイミングを確認します。 このセットアップでは、spectator ビュー カメラを移動が可能な他のユーザーが多い、HoloLens で直接開発のエクスペリエンスを一致するように安定したホログラムを維持しながら。

Spectator ビューのオープン ソースのバージョンと引き換え全体的なセットアップのコストを大幅に削減するためにカメラのリモート テスト マシン群を移動する機能が無効です。 このプロジェクトでは、剛体、HoloLens にマウントされている外部のカメラを使用して、高解像度写真の撮影と holographic Unity プロジェクトのビデオ。 **ライブ デモ、中には、カメラは、固定位置に残っている必要があります。** カメラの動きは、ホログラム ジッターや誤差につながることができます。 これは、ビデオのフレームのタイミングと、PC でホログラムのレンダリングは正確に同期できないためにです。 そのため、カメラを安定した保持するか、移動を制限すると、HoloLens を着ている人が確認できるものに近い結果が生成されます。

アプリを spectator ビューに対応するためには、ビルドする必要があります、[エクスペリエンスを共有](holograms-240.md)アプリ HoloLens と Unity エディターでデスクトップの両方でアプリを実行できることを確認します。 デスクトップ バージョンのアプリには、その複合ビデオ フィード表示ホログラムに組み込まれている追加のコンポーネントがあります。

## <a name="how-to-set-up-spectator-view-pro"></a>Spectator ビューの Pro を設定する方法 

### <a name="requirements"></a>必要条件

![Spectator ビュー Pro リモート テスト マシン群](images/spectatorviewrig-350px.jpg)

#### <a name="hardware-shopping-list"></a>ハードウェアのショッピング リスト

以下は、ハードウェアの推奨される一覧ですが、他の互換性のある単位での実験も。 

|ハードウェア コンポーネント                                                                     |推奨               | 
|:--------------------------------------------------------------------------------------|:----------------------------|
|HoloLens のエミュレーターを使用した holographic の開発に適している PC の構成  |                              | 
|カメラを HDMI または写真をキャプチャ SDK                                             | 写真とビデオのキャプチャは、テストしましたが、 [Canon EOS 5 D マーク III](https://www.amazon.com/Canon-Frame-Full-HD-Digital-Camera/dp/B007FGYZFI/ref=sr_1_3?s=photo&ie=UTF8&qid=1480537693&sr=1-3&keywords=Canon+5D+Mark+III)カメラ。 ライブ デモをテストしましたが、 [Blackmagic デザイン運用カメラ 4 K](https://www.amazon.com/Blackmagic-Design-Production-Camera-Mount/dp/B00CWLSHYG/ref=sr_1_1?s=photo&ie=UTF8&qid=1480537790&sr=1-1&keywords=blackmagic+design+production+camera+4k)します。<br><br>(例: GoPro) out HDMI でカメラが動作する必要がありますに注意してください。 ビデオの多くを使用して、 [Canon EF 14 mm f/2.8 L II USM: ultra Wide 角度固定レンズ](https://www.amazon.com/Canon-Ultra-Wide-Angle-Digital-Cameras/dp/B000V5P94Q)がニーズを満たすカメラのレンズを選択する必要があります。 | 
|キャプチャ、リモート テスト マシン群を調整して合成シーンをプレビューするには、カメラからフレームの色を取得する PC のカード |  テストしましたが、 [Blackmagic デザイン強度 Pro 4 K キャプチャ カード](https://www.amazon.com/dp/B00U3QNP7Q)します。 | 
|ケーブル (複数)                                                                                 |  [ミニ HDMI を HDMI](https://www.amazon.com/AmazonBasics-High-Speed-Mini-HDMI-HDMI-Cable/dp/B014I8UHXE?ie=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o03_s00)キャプチャ カード、カメラを接続します。 カメラに合った HDMI フォーム ファクターを購入することを確認します。 (GoPro は、たとえば、経由で出力[マイクロ HDMI](https://www.amazon.com/dp/B014I8U33I/ref=twister_B0198TA40O?_encoding=UTF8&psc=1))。<br><br>[HDMI ケーブル](https://www.amazon.com/dp/B014I8TC4E/ref=twister_B016I3XG0S?_encoding=UTF8&th=1)複合プレビュー モニターまたはテレビでフィードを表示します。 | 
|カメラに接続、HoloLens、アルミニウム角かっこを加工します。 | [アルミニウム角かっこ](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/HoloLens_Mount.stp)   | 
|3D では、HoloLens のマウントをカメラ hotshoe に接続するアダプターを印刷します。| [3D 印刷アダプター](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/Mount_Adapter.stl)  | 
|Hotshoe fastener hotshoe アダプターをマウントするには                                       |  [Hotshoe Fastener](https://www.amazon.com/Fotasy-SCX2-Adapter-Premier-Cleaning/dp/B00HPAPFNU/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) | 
|さまざまなナットやボルト、ツール                                                |  [1/4-20"ナット](https://www.amazon.com/Hillman-Group-150003-20-Inch-100-Pack/dp/B000BPEPNW/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img)<br>[1/4-20"× 3/4"ボルト](https://www.amazon.com/Hard-Find-Fastener-014973100032-4-20-Inch/dp/B004S6RZPK/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) <br>[7/16 ナット ドライバー](https://www.amazon.com/Klein-Tools-630-7-Cushion-Grip-Hollow-Shank/dp/B000BPG4CW/ref=sr_1_1?ie=UTF8&qid=1479853212&sr=8-1)<br>[T15 Torx](https://www.amazon.com/Stanley-60-011-Standard-Torx-Screwdriver/dp/B000KFXDWW/ref=sr_1_1?ie=UTF8&qid=1479853303&sr=8-1)<br>[T7 Torx](https://www.amazon.com/SE-7542ST-6-Piece-Professional-Screwdriver/dp/B000ST3K3W/ref=sr_1_1?ie=UTF8&qid=1479853479&sr=8-1) | 

#### <a name="software-components"></a>ソフトウェア コンポーネント

1. ソフトウェアをダウンロード、 [spectator ビュー用の GitHub プロジェクト](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView)します。
2. [Blackmagic キャプチャ カード SDK](https://www.blackmagicdesign.com/support)\。
 デスクトップのビデオ Developer「最新のダウンロード」で SDK を検索します。
3. [Blackmagic デスクトップ ビデオ ランタイム](https://www.blackmagicdesign.com/support)\。
 「最新版のダウンロード」でデスクトップのビデオのソフトウェア更新プログラムを検索します \。
 バージョン番号と一致する SDK のバージョンを確認します。
4. [OpenCV 3.1](https://opencv.org/releases.html)調整または Blackmagic キャプチャのカードがないビデオ キャプチャします。
5. [Canon SDK](https://www.usa.canon.com/internet/portal/us/home/explore/solutions-services/digital-camera-sdk-information) (省略可能). \
 Canon カメラを使用しているし、Canon SDK へのアクセスがある場合より高い解像度のイメージを実行する PC にカメラを使用できます。
6. Holographic アプリ開発の unity \。
 OSS プロジェクトでは、サポートされているバージョンを確認できます。
7. 最新の更新プログラムの visual Studio 2015。

### <a name="building-your-own-spectator-view-pro-camera"></a>Spectator ビュー Pro カメラの構築

**通知および免責事項:** 基本的な (など、HoloLens「spectator ビュー」の設定に限定されません)、HoloLens のハードウェアの変更を行うときに安全に関する注意事項に従って常にする必要があります。 すべての変更を加える前に、すべての手順については、マニュアルを読み取る。 すべての手順し、ツールを使用して、指示に従ってユーザーの責任になります。 購入または制限付き保証または保証の免責、HoloLens のライセンスを取得した可能性があります。 該当するをお読みください[HoloLens の使用許諾契約書または使用条件および販売](https://www.microsoft.com/hololens/support/warranty)保証オプションについて理解します。

<br>

>[!VIDEO https://www.youtube.com/embed/aKX8UMejtWc]

#### <a name="rig-assembly"></a>リモート テスト マシン群のアセンブリ

![HoloLens と DSLR カメラに組み立てられた Spectator ビュー Pro 装置です。](images/assembly.gif)<br>
*HoloLens と DSLR カメラに組み立てられた Spectator ビューの Pro を発する*


* T7 ドライバーを使用して、HoloLens から、ヘッドバンドを削除します。 ねじが疎、もう一方の側からのクリップでそれらを開けます。
* 内側にネジ cap を削除小型マイナス ドライバーでの HoloLens のハイパーバイザーの表面。
* T15 ドライバーを使用して、削除、HoloLens の角かっこから小さな torx ボルトを削除して添付ファイルのフック形します。
* 角かっこ、角かっこの前面の 3-d 図形を使用して、公開されている、ハイパーバイザーの内側の穴に通します、HoloLens を配置します。 角かっこの下部にあるピンでインプレース HoloLens の腕を保持する必要があります。
* 再アタッチして、HoloLens、角かっこをセキュリティで保護するフックの形の添付ファイル。
* カメラの hotshoe に hotshoe fastener をアタッチします。
* マウントのアダプターを hotshoe fastener にアタッチします。
* 狭い側が転送に接続するためのアダプターとカメラのレンズに並列的に回転させます。
* 7/16 ナット ドライバーを使用して、1/4"ナッツと場所のアダプターをセキュリティで保護します。
* HoloLens のハイパーバイザーの前面カメラのレンズの前にできるだけ近いので、アダプターに対して角かっこを配置します。
* 4 の 1/4"とは比べ物 7/16 ナット ドライバーを使用すると、角かっこをアタッチします。

#### <a name="pc-setup"></a>PC のセットアップ
* ソフトウェアのコンポーネント セクションからソフトウェアをインストールします。
* マザーボード上の開いている PCIe スロットにキャプチャ カードを追加します。
* 外部の HDMI スロットに、カメラからの HDMI ケーブル (HDMI) 上でキャプチャ カード。
* 省略可能なプレビュー モニターにキャプチャ カードで center HDMI スロット (HDMI アウト) から HDMI ケーブルを接続します。

#### <a name="camera-setup"></a>カメラのセットアップ
* ビデオ モードをカメラが 3:4 写真の解像度、トリミングではなく、完全な解像度 1920 x 1080 で出力には、それを変更します。
* カメラの HDMI 設定を有効にする見つけて**ミラーリング**または**デュアル モニター**します。
* 1080 P. に出力解像度を設定します。
* オフにする**ビューの画面にライブ**画面のオーバーレイは、フィード、合成には表示されないようにします。
* カメラの**ライブ ビュー**します。
* 使用する場合、 **Canon SDK** flash 単位を使用して、無効にして**サイレント LV 撮影**します。
* 外部の HDMI スロットにカメラからの HDMI ケーブル (HDMI) 上でキャプチャ カード。

#### <a name="calibration"></a>調整

Spectator ビュー リモート テスト マシン群を設定した後、HoloLens にカメラの位置と回転のオフセットを取得するために調整する必要があります。
* Calibration\Calibration.sln の下の調整の Visual Studio ソリューションを開きます。
* このソリューションでは、ファイル dependencies.props inc の場所については、サード パーティのソースのマクロを作成します。 これが表示されます。
* このファイルを更新する場所をインストールした OpenCV 3.1、Blackmagic SDK、および Canon SDK (該当する場合)

![Visual Studio での依存関係の場所のスナップショット](images/dependencies-600px.png)<br>
*Visual Studio での依存関係の場所のスナップショット*


* フラット、剛体の画面で、調整パターン Calibration\CalibrationPatterns\2_66_grid_FULL.png を出力します。
* お使いの PC に、HoloLens を USB 経由で接続します。
* プリプロセッサの定義を更新**HOLOLENS_USER**と**HOLOLENS_PW**で**stdafx.h** HoloLens のデバイス ポータルの資格情報を使用します。
* HDMI 経由でキャプチャ カード、カメラを接続し、オンにします。
* 調整のソリューションを実行します。
* このようなビューを囲むチェッカー ボード パターンを移動します。

![Spectator ビュー Pro リモート テスト マシン群の調整](images/calibration.gif)<br>
*Spectator ビュー Pro リモート テスト マシン群の調整*


* チェッカーがビューに表示するとき、画像が自動的に実行されます。 [次へ] の姿勢を進める前に、HoloLens のハイパーバイザー上の白いライトを探します。
* 完了したら、次のようにキーを押します**Enter**調整でアプリを作成するフォーカスで、 **CalibrationData.txt**ファイル。
* このファイルに保存されます**Documents\CalibrationFiles\CalibrationData.txt**
* このファイルを調整データが正確かどうかを検査します。
   * **DSLR RMS** 0 に近いする必要があります。
   * **HoloLens RMS** 0 に近いする必要があります。
   * **ステレオ RMS**が 20 50、これは許容可能なために、2 つのカメラの視野が異なる場合があります。
   * **翻訳**接続されたカメラのレンズを HoloLens のカメラからの距離です。 これは、メーターです。
   * **回転**identity 近づく必要があります。
   * **DSLR_fov** y の値は、レンズの焦点距離と、カメラの本文のトリミング要素から予想される垂直ビューのフィールドの近くにする必要があります。
* 意味を理解する上記の値のいずれかが表示されない場合の再補正します。
* このファイルのコピー、**資産**Unity プロジェクトのディレクトリ。

### <a name="compositor"></a>Compositor

コンポジターが Unity エディターのウィンドウとして実行される Unity 拡張機能です。 これを有効にするには、コンポジター Visual Studio ソリューションまず必要がありますを構築します。
* Compositor\Compositor.sln コンポジターの Visual Studio ソリューションを開く
* 上記の調整のソリューションと同じ条件では、dependencies.props を更新します。 調整手順を実行する場合、このファイルは既に更新されました。
* リリースと Unity のバージョンのアーキテクチャに合致するアーキテクチャ ソリューション全体をビルドします。 不明な場合に、x86 と x64 の両方をビルドします。
* X64 用のソリューションをビルドした場合は、HoloLens 上で実行されますので、x86 として SpatialPerceptionHelper プロジェクトをビルドもします。
* アプリケーションが実行されている場合は、Unity を閉じます。 Unity は、実行時に Dll が変更された場合は再起動する必要があります。
* Unity プロジェクトにこのソリューションからビルドされた Dll をコピーする Compositor\CopyDLL.cmd を実行します。 このスクリプトは、含まれているサンプル プロジェクトに Dll をコピーします。 独自のプロジェクトを設定した後もコピーして、プロジェクトの Assets ディレクトリを指すコマンドライン引数を指定して CopyDLL を行うことができます。
* サンプルの Unity アプリを起動します。

### <a name="unity-app"></a>Unity アプリ

Unity エディターのウィンドウとして、コンポジターが実行されます。 含まれているサンプル プロジェクトには、spectator 表示を 1 回のコンポジターの Dll がコピー操作にするよう設定すべてが含まれます。

Spectator ビューが、アプリケーションとして実行する必要があります、[エクスペリエンスを共有](holograms-240.md)します。 つまり、HoloLens で発生するアプリケーションの状態の変更は、Unity でも実行されているアプリを更新するネットワーク経由で接続する必要があります。

新しい Unity プロジェクトから開始する場合は最初にいくつかの設定を行う必要があります。
* コピー**資産/アドオン/HolographicCameraRig**をプロジェクトにサンプル プロジェクトから。
* 最新の MixedRealityToolkit をプロジェクトに追加を含む**共有**、 **csc.rsp**、 **gmcs.rsp**、および**smcs.rsp**します。
* 追加、 **CalibrationData.txt** Assets ディレクトリにファイル。

![Unity のアセットのディレクトリのスナップショット](images/files-400px.png)

* 追加、 **HolographicCameraRig\Prefabs\SpectatorViewManager** prefab シーンにし、フィールドに入力します。
   * **HolographicCameraManager** HolographicCameraRig プレハブ ディレクトリから HolographicCameraManager プレハブを設定する必要があります。
   * **アンカー** HolographicCameraRig プレハブ ディレクトリからアンカー プレハブを設定する必要があります。
   * **共有**MixedRealityToolkit から共有プレハブを設定する必要があります。
   * 注:プロジェクト階層で既にがあるこれらのプレハブの場合はこれらのものではなく既存のプレハブが使用されます。
   * **Spectator ビュー IP** spectator ビュー リモート テスト マシン群にアタッチされている、HoloLens の ip アドレスにする必要があります。
   * **共有サービスの IP** MixedRealityToolkit SharingService を実行している PC の ip アドレスにする必要があります。
   * 省略可能: 複数の spectator が複数の PC に接続されているリモート テスト マシン群を表示した場合の**ローカル コンピューターの IP** spectator ビューのリモート テスト マシン群が通信する PC に設定する必要があります。

![Unity で spectator ビュー マネージャーのプロパティ](images/spectatorviewmanager-500px.png)

* 開始、MixedRealityToolkit**共有サービス**
* ビルドおよび spectator ビューのリモート テスト マシン群に接続されている、HoloLens に D3D の UWP アプリを展開します。
* エクスペリエンスで他の HoloLens デバイスにアプリをデプロイします。
* チェック、**バック グラウンドで実行**下のチェック ボックス**編集/プロジェクトの設定/プレーヤー**します。

![Unity で設定をバック グラウンドで実行します。](images/run-in-bg-400px.png)
* コンポジターのウィンドウを起動**コンポジター/Spectator ビュー**

![Unity で spectator ビューのコンポジターの表示](images/compositor-500px.png)

* このウィンドウを使用するできます。
   * ビデオの録画を開始します。
   * 写真を撮る
   * ホログラム不透明度を変更します。
   * (これはキャプチャ カードの待機時間に対応する色のタイムスタンプを調整) フレームのオフセットを変更します。
   * キャプチャに保存するディレクトリを開く
   * (プロジェクト内に存在する SpatialMappingManager) 場合は、spectator ビュー カメラから空間マッピング データを要求します。
   * シーンの複合ビューだけでなく色、ホログラム、およびアルファ チャネルを個別に視覚化します。
   * カメラの電源をオンにします。
   * Unity でキーを押して再生します。
   * カメラを移動すると、Unity でホログラムにフィードのカメラの色の基準とした現実の世界にいる必要があります。

## <a name="see-also"></a>関連項目

* [複合現実のキャプチャ](mixed-reality-capture.md) 
* [開発者向けの実際のキャプチャの混在](mixed-reality-capture-for-developers.md)
* [複合現実での経験を共有](shared-experiences-in-mixed-reality.md)
* [Spectator GitHub でコードの表示 (プレビュー)](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/SpectatorView)
* [Spectator GitHub でのネイティブ コードの表示 (プレビュー)](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin)
* [GitHub で spectator ビュー Pro コード](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView)
