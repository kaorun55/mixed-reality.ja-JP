---
title: HoloLens の既知の問題
description: これは、HoloLens 開発者に影響を与える可能性がある既知の問題の一覧です。
author: mattzmsft
ms.author: mazeller
ms.date: 07/10/2019
ms.topic: article
keywords: トラブルシューティング、既知の問題、ヘルプ
ms.openlocfilehash: 1ef9e9f411e16d2f604930f3146ede1d03d7c0f6
ms.sourcegitcommit: c36b8c8573f51afa79504c4a17084e4f55d2f664
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67789490"
---
# <a name="hololens-known-issues"></a>HoloLens の既知の問題

これは、HoloLens が開発者に影響を与える既知の問題の現在の一覧です。 奇妙な動作が見られる場合は、まずこのチェックボックスをオンにします。 この一覧は、新しい問題が検出または報告されたとき、または将来の HoloLens ソフトウェア更新プログラムで問題が解決されると、更新されたままになります。

## <a name="unable-to-connect-and-deploy-to-hololens-through-visual-studio"></a>Visual Studio を使用して HoloLens に接続して展開できない

>[!NOTE]
>最終更新日時:7/8 @ 7: 25PM-チームは根本原因を特定し、現在修正を行っています。 回避策を以下に示します。 

この問題の根本原因を特定できました。 Visual studio 2015 または Visual Studio 2017 の初期リリースを使用して、HoloLens でアプリケーションをデプロイおよびデバッグした後、同じ HoloLens を使用した最新バージョンの Visual Studio 2017 または Visual Studio 2019 を使用したユーザーは、影響を受けます。 

新しいリリースの Visual Studio では、新しいバージョンのコンポーネントが配置されますが、古いバージョンのファイルはデバイス上に残されるため、新しいバージョンのエラーが発生します。  これにより、次のエラーメッセージが表示されます。DEP0100:ターゲットデバイスの開発者モードが有効になっていることを確認してください。 エラー80004005が発生したため<ip> 、で開発者ライセンスを取得できませんでした。
 
**対応策**: 

現在、チームは修正を行っています。 それまでの間は、次の手順を使用して問題を回避し、デプロイとデバッグのブロックを解除できます。  
1. Visual Studio を開く
2. ファイル > の新しい > プロジェクト
3. Visual C# > Windows デスクトップ-> コンソールアプリ (.NET Framework)
4. プロジェクトに名前 (例: HoloLensDeploymentFix) を付け、フレームワークが少なくとも .NET Framework 4.5 に設定されていることを確認してから、[OK] をクリックします。
5. ソリューションエクスプローラーの [参照] ノードを右クリックし、次の参照を追加します ([参照] セクションをクリックし、[参照] をクリックします)。ボタン):
    ```
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Deploy.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Connectivity.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\SirepInterop.dll
    ```
    >[!NOTE]
    >10.0.18362.0 がインストールされていない場合は、最新バージョンを使用します。
 
6. ソリューションエクスプローラーでプロジェクトを右クリックし、[既存項目の追加 >] を選択します。
 
7. C:\Program Files (x86) \Windows Kits\10\bin\10.0.18362.0\x86 を参照し、フィルターを "すべてのファイル (\*.\*)" に変更します。
 
8. SirepClient と SshClient の両方を選択し、[追加] をクリックします。
 
9. ソリューションエクスプローラーで両方のファイルを見つけて選択し (ファイルの一覧の一番下にある必要があります)、プロパティウィンドウの [出力ディレクトリにコピー] を [常にコピーする] に変更します。
 
10. ファイルの先頭で、' using ' ステートメントの既存のリストに次の行を追加します。 
    ```
    using Microsoft.Tools.Deploy;
    using System.Net;
    ```
 
11. "Static void Main (...)" 内で、次のコードを追加します。
    ```
    RemoteDeployClient client = RemoteDeployClient.CreateRemoteDeployClient();
    client.Connect(new ConnectionOptions()
    {
        Credentials = new NetworkCredential("DevToolsUser", string.Empty),
        IPAddress = IPAddress.Parse(args[0])
    });
    client.RemoteDevice.DeleteFile(@"C:\Data\Users\DefaultAccount\AppData\Local\DevelopmentFiles\VSRemoteTools\x86\CoreCLR\mscorlib.ni.dll");
    ```
12. ビルド > ビルドソリューション
 
13. コンパイルされた .exe を含むフォルダー (例: C:\MyProjects\HoloLensDeploymentFix\bin\Debug) に対してコマンドプロンプトを開きます。
 
14. 実行可能ファイルを実行し、デバイスの IP アドレスをコマンドライン引数として指定します。  (USB 経由で接続されている場合は、127.0.0.1 を使用できます。それ以外の場合は、デバイスの WiFi IP アドレスを使用します)。たとえば、"HoloLensDeploymentFix 127.0.0.1" のようになります。
 
15. ツールがメッセージなしで終了すると (これには数秒しかかかりません)、Visual Studio 2017 以降からデプロイおよびデバッグできるようになります。  ツールを引き続き使用する必要はありません。

利用可能になると、さらに更新プログラムを提供します。

## <a name="issues-launching-the-microsoft-store-and-apps-on-hololens"></a>HoloLens での Microsoft Store とアプリの起動に関する問題

>[!NOTE]
>最終更新日時:4/2 @ 10 AM-問題が解決されました。 

HoloLens で Microsoft Store とアプリを起動しようとすると、問題が発生することがあります。 この問題が発生するのは、バックグラウンドアプリの更新プログラムによって、特定のシーケンスで新しいバージョンのフレームワークパッケージが配置されているにもかかわらず、1つまたは複数の依存アプリがまだ実行中である場合です。 この場合、アプリの自動更新によって新しいバージョンの .NET ネイティブ Framework (バージョン10.0.25531 から 10.0.27413) が提供されたため、以前のバージョンのフレームワークを使用している実行中のすべてのアプリに対して、実行中のアプリが正しく更新されませんでした。  Framework 更新のフローは次のとおりです。-

1.  新しいフレームワークパッケージがストアからダウンロードされ、インストールされます。
2.  古いフレームワークを使用しているすべてのアプリは、新しいバージョンを使用するように "更新" されます。

手順 2. が完了する前に中断された場合、新しいフレームワークが登録されていないアプリは [スタート] メニューから起動できません。  HoloLens のアプリは、この問題の影響を受ける可能性があります。

一部のユーザーは、ハングしたアプリを終了し、フィードバックハブ、3D ビューアー、写真などの他のアプリを起動すると、問題が解決しますが、100% の時間は機能しません。

根本が発生したため、この問題は更新プログラム自体の原因ではなく、.NET ネイティブ framework の更新プログラムが正しく処理されなかった OS のバグが発生しました。 修正を特定し、修正を含む更新プログラム (OS バージョン 17763.380) をリリースしたことをお知らせします。 

デバイスで更新プログラムを取得できるかどうかを確認するには、次のようにします。

1.  [設定] アプリにアクセスし、[Update & Security] を開きます。
2.  [更新プログラムの確認] をクリックします。
3.  17763.380 への更新が利用可能な場合は、このビルドに更新して、アプリのハングのバグの修正を受け取るようにしてください。
4.  このバージョンの OS に更新すると、アプリは想定どおりに動作するはずです。

また、HoloLens OS のリリースごとに、Microsoft ダウンロードセンター https://aka.ms/hololensdownload/10.0.17763.380 のに ffu イメージを投稿しました。 

更新を希望しない場合は、3/29 の時点で Microsoft Store UWP アプリの新しいバージョンをリリースしました。 更新されたバージョンのストアを作成したら、次のようにします。

1) ストアを開き、それが読み込まれることを確認します。
2) ブルームジェスチャを使用してメニューを開きます。
3) 以前に破損したアプリを開こうとしました
3) それでも起動できない場合は、壊れているアプリのアイコンをタップしたままにして、[アンインストール] を選択します。
4) これらのアプリをストアからインストールします。

デバイスがまだアプリを読み込むことができない場合は、次の手順を実行して、ダウンロードセンターで .NET ネイティブ Framework および Runtime のバージョンをサイドロードできます。

1)  [この zip ファイル](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip)は、Microsoft ダウンロードセンターからダウンロードしてください。  解凍すると2つのファイルが生成されます。  .NET........................... .net
2)  デバイスのロックが解除されていることを確認してください。  これを実行していない場合は、[こちら](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0)の手順に従ってください。
3)  次に、Windows デバイスポータルにアクセスします。  USB 経由でこれを行うことをお勧めします。これを http://127.0.0.1:10080 行うには、ブラウザーに「」と入力します。  
4)  Windows デバイスポータルを作成したら、ダウンロードした2つのファイルの "サイドロード" を行う必要があります。  これを行うには、[アプリ] セクションに移動して [アプリ] をクリックするまで、左側のバーを下に表示する必要があります。
5)  次のような画面が表示されます。  "アプリのインストール" というセクションに移動し、これら2つの APPX ファイルを解凍した場所を参照します。  一度に1つだけ実行できます。そのため、最初の1つを選択した後、[デプロイ] セクションで [実行] をクリックします。  次に、2番目の APPX ファイルに対してこれを実行します。 
  ![サイドロードアプリをインストールするための Windows デバイスポータル](images/20190322-DevicePortal.png)<br>
6)  この時点で、アプリケーションが再び動作を開始し、ストアにもアクセスできると思われます。
7)  場合によっては、影響を受けるアプリが起動する前に3D ビューアーアプリを起動する追加手順を実行する必要があります。 

この問題を解決するためのプロセスが完了したので、しばらくお待ちください。マイクロソフトのコミュニティと連携して、成功した Mixed Reality エクスペリエンスを作成してください。

## <a name="connecting-to-wifi"></a>WiFi に接続しています

OOBE & 設定では、資格情報のタイムアウトは2分です。 ユーザー名/パスワードは2分以内に入力する必要があります。そうしないと、ユーザー名フィールドが自動的にクリアされます。

長いパスワードを入力する場合は、Bluetooth キーボードを使用することをお勧めします。

## <a name="device-update"></a>デバイスの更新
* 30秒新しい更新の後、シェルが1回消えることがあります。 **ブルーム**ジェスチャを実行してセッションを再開してください。

## <a name="visual-studio"></a>Visual Studio
* 「HoloLens 開発に推奨される Visual Studio の最新バージョン用の[ツールをインストール](install-the-tools.md)する」を参照してください。
* アプリを Visual Studio から HoloLens にデプロイすると、次のエラーが表示される場合があります。**ユーザーマップセクションが開いているファイルに対して、要求された操作を実行することはできません。(HRESULT からの例外: 0x800704C8)** 。 この問題が発生した場合は、もう一度やり直してください。通常、配置は成功します。

## <a name="emulator"></a>エミュレーター
* Microsoft Store の一部のアプリは、エミュレーターと互換性がありません。 たとえば、若い Conker とフラグメントは、エミュレーターでは再生できません。
* エミュレーターでは、PC の web カメラを使用できません。
* Windows デバイスポータルのライブプレビュー機能は、エミュレーターでは機能しません。 混合した現実のビデオとイメージをキャプチャすることもできます。

## <a name="unity"></a>Unity
* 「HoloLens の開発に推奨される最新バージョンの Unity 用の[ツールをインストール](install-the-tools.md)する」を参照してください。
* Unity HoloLens Technical Preview の既知の問題については、 [Hololens Unity フォーラム](http://forum.unity3d.com/threads/known-issues.394627/)に記載されています。

## <a name="windows-device-portal"></a>Windows Device Portal
* Mixed Reality キャプチャのライブプレビュー機能は、数秒の待機時間が発生する場合があります。
* [仮想入力] ページで、[仮想ジェスチャ] セクションのジェスチャとスクロールコントロールが機能していません。 使用すると、効果はありません。 同じページ上の仮想キーボードが正常に動作します。
* [設定] で開発者モードを有効にした後、デバイスポータルをオンにするスイッチが有効になるまで数秒かかることがあります。

## <a name="api"></a>API
* アプリケーションがユーザーの背後にある[フォーカスポイント](focus-point-in-unity.md)を設定した場合、または通常はカメラから移動した場合、ホログラムは混合の現実キャプチャの写真またはビデオには表示されません。 Windows でこのバグが修正されるまでは、アプリケーションが[フォーカスポイント](focus-point-in-unity.md)をアクティブに設定している場合は、平面法線が反対のカメラフォワード (たとえば、normal =-camera. forward) に設定されていることを確認する必要があります。

## <a name="xbox-wireless-controller"></a>Xbox ワイヤレスコントローラー
* Xbox ワイヤレスコントローラーは、HoloLens で使用する前に更新する必要があります。 コントローラーを HoloLens とペアリングする前に、最新の状態[に](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)なっていることを確認してください。
* Xbox ワイヤレスコントローラーが接続されている間に HoloLens を再起動すると、コントローラーは HoloLens に自動的に再接続されません。 番組ガイドボタンのライトは、コントローラーが3分後に電源オフになるまで、ゆっくりと点滅します。 コントローラーをすぐに再接続するには、[ガイド] ボタンを押して、ライトがオフになるまでコントローラーの電源をオフにします。 コントローラーの電源を再度オンにすると、HoloLens に再接続されます。
* Xbox ワイヤレスコントローラーが接続されている間に HoloLens がスタンバイ状態になると、コントローラー上の入力があれば HoloLens がウェイクアップされます。 コントローラーの使用が完了したら、コントローラーの電源をオフにすることで回避できます。
