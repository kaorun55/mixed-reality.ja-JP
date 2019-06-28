---
title: 2019 の月のリリース ノート
description: HoloLens と Windows 10 用の Windows Mixed Reality リリース ノート 2019 は (19 H 1 とも呼ばれます) を更新できます。
author: mattzmsft
ms.author: mazeller
ms.date: 05/02/2019
ms.topic: article
keywords: リリース ノート、バージョン、windows 10、ビルド、19 h 1、os
ms.openlocfilehash: c1fa45eefb0abe702791d34801e84044afe48245
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416473"
---
# <a name="release-notes---may-2019"></a>2019 の月のリリース ノート

**[Windows 10 年 2018年 10 月 Update](https://blogs.windows.com/windowsexperience/2018/10/02/find-out-whats-new-in-windows-and-office-in-october/)** (RS5 とも呼ばれます) では、HoloLens と Windows Mixed Reality イマーシブ ヘッドセットを Pc に接続されている新しい機能が含まれています。 

HoloLens または PC で (Windows Mixed Reality 没入型の (VR) ヘッドセット) 用の最新のリリースに更新するには、開く、**設定**アプリに移動して**更新とセキュリティ**を選択し、**の確認更新プログラム**ボタンをクリックします。 Windows 10 pc で、Windows をインストールすることができますも手動で 10 年 2018年 10 月の更新を使用して、 [Windows メディアの作成ツール](https://www.microsoft.com/software-download/windows10)します。

**デスクトップの最新リリース:** Windows 10 年 2018年 10 月 Update (**10.0.17763.107**)<br>
**HoloLens の最新リリース:** Windows 10 年 2018年 10 月 Update (**10.0.17763.134**)<br>

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Windows Mixed Reality イマーシブ ヘッドセットの新機能

Windows 10 年 2018年 10 月には更新には、デスクトップ PC を Windows Mixed Reality 没入型 (VR) ヘッドセットを使用するための多くの機能強化が含まれています。

### <a name="for-everyone"></a>すべてのユーザー

* **実際に懐中電灯を混合**-、近くのだれかを参照してください、キーボードを検索する現実の世界にポータルを開くか、ヘッドセットを削除せず、環境について見て! 有効にできます Mixed Reality 懐中電灯スタート メニューからキーを押して Windows + グラブ アニメーション コント ローラーで、または「オン/オフ懐中電灯」と言って で足懐中電灯を使用するように、表示する方向に、コント ローラーをポイントします。

    ![Mixed Reality 懐中電灯](images/mr-flashlight.png)

* **新しいアプリやホーム複合現実でのコンテンツを起動する方法**
    * 使用している場合[SteamVR の Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)SteamVR タイトルに表示される [スタート] メニュー、および、ホーム複合現実でそれぞれのアプリ ランチャーを配置することができます。
    
        ![SteamVR アプリケーション ランチャー](images/steamvr-launchers.png)
        
    * 新しい*360 ビデオ*360 度のビデオの定期的に curated 選択範囲を検出するためのアプリ。
    * 新しい*WebVR ショーケース*WebVR の定期的に curated 選択範囲を検出するためのアプリで発生します。
    * 初めて Windows Mixed Reality 顧客は、Cliff 家を入力し、検索、お気に入りの体感型アプリとゲームを Microsoft Store からのいくつかの 3D アプリケーション ランチャーで設定済み。
    * Microsoft Edge の windows が追加されました、*共有*ボタンをクリックします。
* **クイック アクション メニューの**  -、没入型の複合現実アプリ内で押してできます簡単にアクセスする新しいクイック アクション メニューにアクセスする Windows ボタン*SteamVR メニュー*、*写真/ビデオ キャプチャ*、*懐中電灯*、および*ホーム*します。
* **Backpack Pc のサポート**-Windows Mixed Reality backpack Pc でセットアップが完了したら、ディスプレイ エミュレーターを必要とせず、没入型の (VR) ヘッドセットを実行します。
* **新しいオーディオ機能**-ヘッドセットで両方のオーディオ ジャック (またはヘッドフォン) Windows Mixed Reality エクスペリエンスからオーディオをミラー化することができますようになりました*と*オーディオ デバイスが (外部スピーカー) のような PC に接続します。 ヘッドセットの表示のボリューム レベルの視覚インジケーターが追加されました。
* **その他の改善**
    * 現実のポータルの更新を混在ようになりました経由で配信される Microsoft Store、Windows のメジャー リリース間の迅速な更新プログラムを有効にします。 これはデスクトップ アプリと Windows Mixed Reality ヘッドセットのエクスペリエンスにのみ適用されますが OS と引き続き更新します。 
    * スリープ状態になるとヘッドセット、Windows Mixed Reality アプリはの代わりに中断されます (Mixed Reality ポータルが閉じられる) までを終了します。
    
### <a name="for-developers"></a>開発者向け

* **[QR コードの追跡](qr-code-tracking.md)** -対象のアプリ、Windows Mixed Reality 没入型の (VR) ヘッドセット QR コードをスキャンし、それらをレポートすることができます、mixed reality アプリでの追跡を有効にする QR コードにバックアップします。
* **ハードウェア DRM を体感型アプリのサポート**-開発者は、アプリケーションのハードウェアで保護されたコンテンツを PlayReady などのソースから使用可能ディスプレイ ハードウェアでサポートされている場合、ここで要求バックバッファーのハードウェアで保護されたテクスチャをことができます。
* **[複合現実キャプチャ UI を体感型アプリに統合](mixed-reality-capture-for-developers.md#integrating-mrc-functionality-from-within-your-app)** -開発者を使用して、複合現実のキャプチャを組み込みの Windows を使用して、アプリに統合できます[カメラ キャプチャ UI](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)ほんの数行のコードでします。

## <a name="new-features-for-hololens"></a>HoloLens の新機能

Windows 10 年 2018年 10 月 Update は、HoloLens のすべての顧客に対して公開となど、多数改良にはが含まれています。

### <a name="for-everyone"></a>すべてのユーザー

* **クイック アクション メニューの**  -、没入型の複合現実アプリ内で押してできます簡単にアクセスする新しいクイック アクション メニューにアクセスする Windows ボタン*ビデオの録画を開始*、*撮影*、 *Mixed Reality ホーム*、*音量の変更*、および*Connect*します。
* **開始またはクイック アクション メニューからビデオのキャプチャを開始/停止**-ビデオ キャプチャを開始するには、スタート メニューまたはクイック アクション メニューから、ある場合と同じ場所から録画を停止することです。 (忘れず、常にこれを行う音声指示コマンドですぎます。)
* **Miracast 対応デバイスにプロジェクト**-プロジェクトの近くにある Surface デバイスまたはテレビまたはモニターにコンテンツを HoloLens Miracast 対応ディスプレイまたはアダプターを使用している場合。
* **新しい通知**-ビューと PC の場合と同様、HoloLens の通知に応答します。  
* **没入型の複合現実アプリで便利なオーバーレイ**-キーボード、ダイアログ ボックス、ファイル ピッカーなどのオーバーレイが表示されます、没入型を使用する場合などの複合現実アプリ。
* **ボリュームの変更の視覚インジケーター** - ボリュームを使用する/下向きの矢印ボタンで、HoloLens、ヘッドセットのボリューム レベルの視覚インジケーターが表示されます。
* **デバイスのブート用の新しいビジュアル**-読み込みインジケーターは、システムを読み込み中に視覚的フィードバックを提供するブート プロセス中に追加されました。
* **近接共有**-、近くの Windows デバイスとキャプチャを共有することができますが Windows 近くにある共有エクスペリエンス。  
* **Microsoft Edge から共有**-Microsoft Edge が含まれています、*共有*ボタンをクリックします。 

### <a name="for-developers"></a>開発者向け

* **[複合現実キャプチャ UI を体感型アプリに統合](mixed-reality-capture-for-developers.md#integrating-mrc-functionality-from-within-your-app)** -開発者を使用して、複合現実のキャプチャを組み込みの Windows を使用して、アプリに統合できます[カメラ キャプチャ UI](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)ほんの数行のコードでします。

### <a name="for-commercial-customers"></a>商用のお客様向け

* **セットアップ後のプロビジョニングを有効にする**-設定を使用して、いつでもプロビジョニング パッケージのランタイムを適用できるようになりました。
* **Azure AD グループへのアクセスを割り当てられている**-シングルまたはマルチ アプリ キオスク構成を設定するアクセス権を割り当てる Windows の構成の Azure AD グループを使用することができますようになりました。
* **サインイン画面からプロファイルのスイッチ上のサインインにピン留め**-サインインの暗証番号 (pin) は、サインイン画面で使用可能な「その他のユーザー」のようになりました。 
* **MDM を使用してデバイスのハードウェア情報を読み取る**-IT 管理者が参照してくださいし、MDM コンソールの デバイスのシリアル番号、HoloLens を追跡します。
* **MDM (名前の変更) を介した HoloLens デバイス名を設定**-IT 管理者が参照してください、HoloLens デバイスが MDM コンソールでの名前を変更します。

### <a name="for-international-customers"></a>顧客向け

簡体字中国語や日本語、Pinyin のローカライズされたキーボード、音声入力、音声合成 (TTS)、音声コマンドなどのローカライズされたユーザー インターフェイスを持つようになりました HoloLens を使用できます。

## <a name="known-issues"></a>既知の問題

優れた Windows Mixed Reality エクスペリエンスを提供する苦労しましたが、いくつかの既知の問題を管理するいるともいます。 他のユーザーが見つかったら、ください[フィードバック](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback)します。

### <a name="hololens"></a>HoloLens
 
#### <a name="after-update"></a>更新後に
Windows の 10 年 2018年 10 月を使用して、HoloLens の更新時に、次の問題に注意してください可能性があります。
* **アプリが通知から起動すると、サインインのループで最終的**– サインインが必要ないくつかのアプリでサインインが無限にから通知を起動すると終了-アップできます。 例として、これは Microsoft Store から Microsoft ポータル サイト アプリをインストールして、インストールの完了通知からの起動後に発生します。
* **アプリでサインイン ページが空白のページで実行できるすべて**– サインイン プロンプトがサインイン ページが閉じないし、代わりに空白 (黒) のページを表示、完了時に、アプリケーションを表示するときにあります。 空白のページを閉じるか、下にあるアプリケーションの発見に移動します。 たとえば、これのサインイン設定アプリからの MDM 登録時にします。 

## <a name="provide-feedback-and-report-issues"></a>フィードバックとレポートの問題を提供します。

使用してください、 [HoloLens または Windows 10 PC でフィードバック ハブ アプリ](give-us-feedback.md)フィードバックおよびレポートの問題を提供します。 フィードバック ハブを使用して、すべての必要な診断情報が含まれており、マイクロソフトのエンジニアは、迅速なデバッグし、問題を解決することをによりします。

>[!NOTE]
>フィードバック Hub ドキュメント フォルダーにアクセスするかどうかを確認するメッセージを受け入れるようにしてください (選択**はい**入力を求められたら)。

## <a name="prior-release-notes"></a>以前のリリース ノート

* [リリース ノート - 2018 の年 10 月](release-notes-october-2018.md)
* [リリース ノート - 2018 年 4 月](release-notes-april-2018.md)
* [リリース ノート - 2017 年 10 月](release-notes-october-2017.md)
* [リリース ノート - 2016 年 8 月](release-notes-august-2016.md)
* [リリース ノート - 2016 年 5 月](release-notes-may-2016.md)
* [リリース ノート - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>関連項目
* [イマーシブ ヘッドセット サポート (外部リンク)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [HoloLens のサポート (外部リンク)](https://support.microsoft.com/products/hololens)
* [ツールのインストール](install-the-tools.md)
* [フィードバックを送る](give-us-feedback.md)

