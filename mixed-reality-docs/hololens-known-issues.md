---
title: HoloLens の既知の問題
description: これは、HoloLens の開発者に影響を与える既知の問題の一覧です。
author: mattzmsft
ms.author: mazeller
ms.date: 07/10/2019
ms.topic: article
keywords: トラブルシューティングについては、既知の問題のヘルプ
ms.openlocfilehash: 1ef9e9f411e16d2f604930f3146ede1d03d7c0f6
ms.sourcegitcommit: c36b8c8573f51afa79504c4a17084e4f55d2f664
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67789490"
---
# <a name="hololens-known-issues"></a>HoloLens の既知の問題

これは、現在 HoloLens に影響を与える開発者に関する既知の問題の一覧です。 まずここで、異常な動作が生じる場合。 この一覧は、新しい問題が発見または報告、または将来 HoloLens のソフトウェア更新プログラムの問題については、更新された保持するは。

## <a name="unable-to-connect-and-deploy-to-hololens-through-visual-studio"></a>接続し、Visual Studio での HoloLens にデプロイすることができません。

>[!NOTE]
>最終更新:7/8 午後 7時 25分 - @ チームが、根本原因を特定およびは現在修正に取り組んでいます。 回避策は以下の利用。 

この問題の根本原因を特定できませんでした。 Visual Studio 2015 または Visual Studio 2017 の以前のリリースを展開し、HoloLens のアプリケーションをデバッグするために使用して、その後、Visual Studio 2017 または Visual Studio 2019 の最新バージョンを同じ HoloLens で使用するユーザーに影響があります。 

Visual Studio のそれ以降のリリースは、コンポーネントの新しいバージョンを展開しますが、古いバージョンのファイルが原因で失敗する、新しいバージョン、デバイスで残されました。  これにより、次のエラー メッセージ。DEP0100:そのターゲット デバイスが開発者モードが有効になっていることを確認してください。 開発者用ライセンスを取得できませんでした<ip>80004005 のエラーが原因です。
 
**対応策**: 

私たちのチームは、現在、修正プログラムは取り組んでいます。 それまでは、問題を回避して、デプロイとデバッグをブロック解除のために、次の手順を使用できます。  
1. Visual Studio を開く
2. 新しいファイル]-> [プロジェクト]-> [
3. Visual C# Windows]-> [デスクトップ] の [コンソール アプリ (.NET Framework)
4. フレームワークが以上に設定かどうかを確認して、プロジェクトの名前 (例: HoloLensDeploymentFix) .NET Framework 4.5 は、[ok] をクリックします。
5. ソリューション エクスプ ローラーで [参照] ノードを右クリックし、次の参照の追加 ('参照' セクションをクリックし、[参照...] をクリックします。button):
    ```
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Deploy.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Connectivity.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\SirepInterop.dll
    ```
    >[!NOTE]
    >インストールされている 10.0.18362.0 を持っていない場合は、必要のある最新バージョンを使用します。
 
6. ソリューション エクスプ ローラーでプロジェクトを右クリックし、追加 メニューの 既存の項目。
 
7. C:\Program Files (x86) \Windows Kits\10\bin\10.0.18362.0\x86 を参照し、フィルターを適用して"すべてのファイル (\*.\*)"
 
8. SirepClient.dll と SshClient.dll の両方を選択し、[追加] をクリックします。
 
9. 検索して (ファイルの一覧の下部にある必要があります) のソリューション エクスプ ローラーで両方のファイルを選択し、「常にコピー」を「出力ディレクトリにコピー」プロパティ ウィンドウでの変更
 
10. ファイルの上部にある既存の 'using' ステートメントの一覧に、次を追加します。 
    ```
    using Microsoft.Tools.Deploy;
    using System.Net;
    ```
 
11. "静的 void Main(...)"、内部では、次のコードを追加します。
    ```
    RemoteDeployClient client = RemoteDeployClient.CreateRemoteDeployClient();
    client.Connect(new ConnectionOptions()
    {
        Credentials = new NetworkCredential("DevToolsUser", string.Empty),
        IPAddress = IPAddress.Parse(args[0])
    });
    client.RemoteDevice.DeleteFile(@"C:\Data\Users\DefaultAccount\AppData\Local\DevelopmentFiles\VSRemoteTools\x86\CoreCLR\mscorlib.ni.dll");
    ```
12. ビルド ソリューションのビルド]-> [します。
 
13. コンパイル済みの .exe (C:\MyProjects\HoloLensDeploymentFix\bin\Debug など) を格納するフォルダへのコマンド プロンプトを開きます
 
14. 実行可能ファイルを実行し、コマンドライン引数として、デバイスの IP アドレスを指定します。  (USB 経由で接続している場合をできます 127.0.0.1 を使用して、デバイスの WiFi の IP アドレスを使用して、それ以外の場合)たとえば、"HoloLensDeploymentFix 127.0.0.1"
 
15. ツールは、すべてのメッセージ (する必要がありますのみかかる数秒) せずに終了しましたとを展開して、Visual Studio 2017 からデバッグまたはそれ以降がなります。  ツールの利用を継続するには必要はありません。

さらに更新プログラムが使用可能になります。

## <a name="issues-launching-the-microsoft-store-and-apps-on-hololens"></a>Microsoft Store と HoloLens でアプリの起動の問題

>[!NOTE]
>最終更新:午前 10 時の問題を解決 @ 4/2。 

Microsoft Store および HoloLens でアプリを起動しようとしています。 問題が発生する可能性があります。 バック グラウンド アプリの更新プログラム展開フレームワーク パッケージで 1 つの中に特定のシーケンス内の新しいバージョンまたはその依存するアプリの詳細はまだ実行しているときに問題が発生するを確認します。 この場合、新しいバージョンの .NET ネイティブ Framework (バージョン 10.0.25531 に 10.0.27413) に配信されたアプリの自動更新では、正しくない更新プログラム、framework の以前のバージョンを使用するすべての実行中のアプリを実行しているアプリが発生します。  Framework 更新プログラム用のフローのとおりです:-

1.  新しいフレームワーク パッケージをストアからダウンロードおよびインストール
2.  以前の framework を使用してすべてのアプリが ' 更新される '、新しいバージョンを使用するには

手順 2. が完了する前に中断された場合は、[スタート] メニューから起動する、新しいフレームワークが登録されているすべてのアプリが失敗します。  HoloLens のすべてのアプリはこの問題を受ける可能性があると考えています。

一部のユーザーは、ハングしたアプリケーションを閉じると、フィードバック Hub などの他のアプリの起動、3 D のビューアーと写真が解決される、それらの問題を報告するただし、これが機能しない 100% の時間があります。

ある根本原因を正しく処理されて、ネイティブ .NET framework の更新プログラムは OS でこの問題のバグが、更新プログラム自体、原因がないです。 修正プログラムを識別し、(OS バージョン 17763.380) 更新プログラムをリリースしたことをお知らせは、修正プログラムを格納しています。 

デバイスで、更新プログラムのかかることができますくださいかどうかを参照してください。

1.  設定 アプリに移動し、"更新プログラムとセキュリティ を開く
2.  "更新プログラムの確認 をクリックします。
3.  17763.380 する更新プログラムを使用できる場合、ハングするアプリのバグの修正プログラムを受信するには、このビルドに更新してください。
4.  このバージョンの OS を更新、時に、アプリは正常に動作する必要があります。

さらに、すべて HoloLens の OS のリリースでは、私たちが投稿した FFU イメージに Microsoft ダウンロード センターに https://aka.ms/hololensdownload/10.0.17763.380 します。 

更新プログラムを実行したいしない場合は、3/29 の時点で、Microsoft Store の UWP アプリの新しいバージョンをリリースしました。 ストアの更新バージョンを作成したら。

1) ストアを開くし、読み込まれることを確認します。
2) 「Bloom ジェスチャを使用して、メニューを開きます。
3) 既に中断されているアプリを開くしようとしてください。
3) 場合は、まだを起動できません、タップし切断されたアプリのアイコンを保持し、アンインストール を選択します。
4) Resinstall これらのアプリ ストアから。

デバイスがアプリを読み込むことができない場合で、ダウンロード センターを通じて、.NET ネイティブ フレームワークとランタイムのバージョンのサイドローディングを行う実行できます。

1)  ダウンロードしてください[この zip ファイル](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip)Microsoft ダウンロード センターから。  解凍すると、2 つのファイルが生成されます。  Microsoft.NET.Native.Runtime.1.7.appx と Microsoft.NET.Native.Framework.1.7.appx
2)  デバイスがロックを解除するデベロッパーであることを確認してください。  そのための手順は、前に実行していない場合[ここ](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0)します。
3)  Windows Device Portal のに取得するとするとします。  USB 経由でこれを行うし、入力してようになります http://127.0.0.1:10080 をブラウザーにします。  
4)  「サイドローディング」にする必要があることを Windows Device Portal したら、2 つのファイルをダウンロードしています。  これを行うには、「アプリ」セクションにアクセスして「アプリ」をクリックするまで左側にあるバーを移動する必要があります。
5)  次のような画面が表示されますし、下。  「アプリをインストールする」ことを示すセクションに移動し、これら 2 つの APPX ファイルを解凍した場所に移動します。  だけは一度に 1 つずつ、そのため、1 つ目を選択した後順にクリックします [移動] [デプロイ] セクションできます。  これを 2 番目の APPX ファイルを行います。 
  ![Windows Device Portal のサイド ロード アプリをインストールするには](images/20190322-DevicePortal.png)<br>
6)  この時点で再度動作しているアプリケーションが起動し、ストアにも取得できますと考えます。
7)  場合によっては、必要がある影響を受けるアプリは起動する前に、3 D のビューアー アプリを起動する追加の手順を実行します。 

を経てこの問題を解決する、プロセスとおります成功 Mixed Reality を作成するコミュニティの使用を継続するエクスペリエンスお待ちしております。

## <a name="connecting-to-wifi"></a>WiFi に接続します。

OOBE & 設定では、中には、2 分間の資格情報のタイムアウトです。 ユーザー名/パスワードは、それ以外の場合、ユーザー名フィールドが自動的にクリアされる 2 分以内に入力する必要があります。

長いパスワードを入力するための Bluetooth キーボードを使用することをお勧めします。

## <a name="device-update"></a>デバイスの更新
* 30 秒後、新しい更新プログラム、シェルは、1 回で消えることがあります。 実行してください、**ブルーム**セッションを再開するジェスチャ。

## <a name="visual-studio"></a>Visual Studio
* 参照してください[ツールをインストールする](install-the-tools.md)HoloLens の開発をお勧めします。 Visual Studio の最新バージョン。
* Visual Studio から、HoloLens にアプリをデプロイするときにエラーが表示可能性があります。**ファイルを開いた状態でマップされたユーザー セクションでは、要求された操作を実行できません。(HRESULT からの例外: 0x800704C8)** します。 この場合、もう一度お試しくださいし、デプロイは一般に成功します。

## <a name="emulator"></a>エミュレーター
* Microsoft Store でのすべてのアプリがエミュレーターとの互換性です。 たとえば、Young Conker とフラグメントは、エミュレーターで使用できます。
* エミュレーターで、PC web カメラを使用することはできません。
* Windows Device Portal のライブ プレビュー機能は、エミュレーターでは機能しません。 Mixed Reality ビデオや画像をキャプチャできます。

## <a name="unity"></a>Unity
* 参照してください[ツールをインストールする](install-the-tools.md)の最新のバージョンの Unity の HoloLens の開発をお勧めします。
* Unity HoloLens の Technical Preview の既知の問題が記載されて、 [HoloLens Unity フォーラム](http://forum.unity3d.com/threads/known-issues.394627/)します。

## <a name="windows-device-portal"></a>Windows Device Portal
* Mixed Reality キャプチャ内のライブ プレビュー機能では、いくつかの秒の待機時間を示すことがあります。
* 仮想入力 ページで、仮想のジェスチャのセクションにあるジェスチャとスクロールのコントロールが機能しません。 それらを使用して効果がありません。 同じページで、仮想キーボードが正しく動作します。
* 設定で開発者モードを有効にした後、デバイス ポータルを有効にするスイッチを有効にするには数秒かかる場合があります。

## <a name="api"></a>API
* 設定されている場合、[フォーカス ポイント](focus-point-in-unity.md)Mixed Reality キャプチャ写真またはビデオに表示されませんホログラム ユーザーまたは camera.forward の法線、背後にあります。 アプリケーションがアクティブに設定する場合は、Windows でこのバグが修正されるまで、[フォーカス ポイント](focus-point-in-unity.md)平面の法線が逆のカメラ順方向が設定されていることを確認する必要があります (例: 通常 = - camera.forward)。

## <a name="xbox-wireless-controller"></a>Xbox のワイヤレス コント ローラー
* HoloLens のために使用できる前に、Xbox のワイヤレス コント ローラーの秒を更新する必要があります。 確認[最新](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)HoloLens、コント ローラーをペアリングする前にします。
* Xbox のワイヤレス コント ローラーが接続されている、HoloLens のコンピューターを再起動する場合、コント ローラーは、HoloLens には自動的に再接続できません。 ガイド ボタンのライトが点滅緩やかに変化コント ローラーの電源が切れるまでオフ 3 分後にします。 コント ローラー、すぐに電源オフ、ライトがオフにするまで、番組ガイド ボタンを押し、コント ローラーを再接続します。 コント ローラーをもう一度電源するときは、HoloLens に再接続されます。
* Xbox のワイヤレス コント ローラーが接続されているスタンバイ状態に入ると、HoloLens、コント ローラー上の任意の入力は、HoloLens をスリープ解除されます。 完了したら、コント ローラーを強化することによって、これを防ぐことができますを使用します。
