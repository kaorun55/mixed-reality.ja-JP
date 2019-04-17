---
title: リリース ノート - 2018 年 4 月
description: HoloLens と Windows Mixed Reality リリース ノート、Windows 10 April 2018 は、(RS4 とも呼ばれます) を更新します。
author: mattzmsft
ms.author: mazeller
ms.date: 05/21/2018
ms.topic: article
keywords: リリース ノート、バージョン、windows 10、ビルド、rs4、os
ms.openlocfilehash: 1fc1b43b0581234e835379fd553b78121108086e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600904"
---
# <a name="release-notes---april-2018"></a>リリース ノート - 2018 年 4 月

**[Windows 10 April 2018 Update](https://blogs.windows.com/windowsexperience/2018/04/30/whats-new-in-the-windows-10-april-2018-update)** (RS4 とも呼ばれます) では、HoloLens と Windows Mixed Reality イマーシブ ヘッドセットを Pc に接続されている新しい機能が含まれています。 

をいずれかのデバイスの種類の最新のリリースに更新するには、開く、**設定**に移動して、アプリ**更新とセキュリティ**を選択し、、**更新プログラムの確認**ボタンをクリックします。 Windows 10 pc で、Windows をインストールすることができますも手動で 10 April 2018 Update を使用して、 [Windows メディアの作成ツール](https://www.microsoft.com/software-download/windows10)します。

**デスクトップの最新リリース:** Windows 10 April 2018 Update (**10.0.17134.1**)<br>
**HoloLens の最新リリース:** Windows 10 April 2018 Update (**10.0.17134.80**)<br>
<br>

>[!VIDEO https://www.youtube.com/embed/O-84oWjSbr0]

*Alex Kipman と複合現実の新機能、Windows の概要からメッセージを 10 April 2018 Update します。*

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Windows Mixed Reality イマーシブ ヘッドセットの新機能

Windows 10 April 2018 には Update にはなど、デスクトップ PC に Windows Mixed Reality 没入型 (VR) ヘッドセットを使用するための多くの機能強化が含まれます。 

* **ホーム複合現実の環境を新しい**-選択して、Cliff 家と新しい Skyloft 環境から選択できるよう**場所**[スタート] メニュー。 追加しました[、試験的な機能](add-custom-home-environments.md)作成したカスタム環境を使用することができますが。
* **複合現実のキャプチャにすばやくアクセス**-モーションのコント ローラーを使用して、複合現実写真を行えるようになりました。 Windows ボタンを押したままし、トリガーをタップします。 これは、環境およびアプリ、DRM で保護されたコンテンツは取得されませんが。
* **起動して、コンテンツをサイズ変更用の新しいオプション**-アプリを自動的に配置する前にここで、[スタート] メニューを起動するとします。 端とウィンドウの隅をドラッグして 2D アプリ サイズを変更することもできます。
* **「テレポート」音声コマンドを使用してコンテンツを簡単にジャンプ**-できるようになりましたすばやくテレポート コンテンツ gazing して「テレポート」という Windows Mixed Reality ホームのコンテンツの前にする。
* **[3D アプリ ランチャーをアニメーション化](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#animation-guidelines)と[装飾的な 3D オブジェクト](enable-placement-of-3d-models-in-the-home.md)ホーム複合現実の**-3D アプリ ランチャーにアニメーションを追加しに web ページまたは 2D アプリからの装飾的な 3D モデルを配置するユーザーを許可できます、Windows Mixed Reality ホーム。
* **[Windows Mixed Reality SteamVR for の機能強化](updating-your-steamvr-application-for-windows-mixed-reality.md)** -SteamVR の Windows Mixed Reality が新しいアップグレードを「早期アクセス」外: モーション コント ローラー、パフォーマンスの向上および信頼性を使用する場合のハプティクス フィードバックとSteamVR でモーション コント ローラーの外観を改善します。
* **その他の改善**-より最適化されたエクスペリエンスを提供するパフォーマンスの自動設定が更新されました (できます[を手動でオーバーライド](#visual-quality)この設定)。 セットアップは、USB 3.0 コント ローラーとグラフィックス カードのある一般的な互換性の問題に関する情報の詳細を提供します。

## <a name="new-features-for-hololens"></a>HoloLens の新機能

Windows 10 April 2018 Update は、HoloLens のすべてのお客様に到達しました。 この更新プログラムには、HoloLens のソフトウェアでの最後のメジャー リリースから導入された機能強化が詰め込まれて[2016 年 8 月](release-notes-august-2016.md)します。

### <a name="for-everyone"></a>すべてのユーザー

<table>
  <tr>
    <th>機能</th><th>詳細</th><th>手順</th>
  </tr>
  <tr>
    <td>起動時に、2 D および 3D コンテンツの自動配置</td><td>2D アプリ ランチャーまたは 2D UWP のアプリを自動で、最適なサイズと距離に配置するユーザーを要求する代わりに起動したときに、世界中で配置します。 場合、<a href="app-views.md">イマーシブ アプリ</a>の代わりに、2 D のアプリ起動ツールを使用して、 <a href="3d-app-launcher-design-guidance.md">3D アプリ起動ツール</a>、没入型のアプリが自動起動され、2 D アプリ起動ツールから同じ RS1 のようにします。<br><br>[スタート] メニューから 3D アプリ ランチャーも自動-場所の世界でします。 アプリを自動起動するには、代わりに、ユーザーは、体感型アプリを起動する起動ツールをクリックし、ことができます。 3D コンテンツが開かれていてエッジからホログラム アプリからも自動-場所の世界でします。</td><td>[スタート] メニューからアプリを開くときに不要になった求められます、世界中に配置します。<br><br>場合 2D アプリ/<a href="3d-app-launcher-design-guidance.md">3D アプリ起動ツール</a>配置が最適ではない、簡単に移動できます以下で説明する新しいの滑らかなアプリ操作を使用します。 「移動」と答えるとし、コンテンツを再配置視線の先を使用して 2D アプリ ランチャー/3 D コンテンツを再配置してもできます。</td>
  </tr>
  <tr>
    <td>滑らかなアプリの操作</td><td>移動、サイズ変更、および「調整」モードに切り替わることがなく 2D と 3D のコンテンツを回転します。</td><td>2D の UWP アプリまたは 2D アプリ起動ツールを移動するに単に、アプリ バーを見つめますと、tap を使用して保持 + ジェスチャをドラッグします。 タップして、保持 + + ドラッグを使用してとオブジェクトの任意の場所に gazing によって 3D コンテンツを移動できます。<br><br>2D のコンテンツのサイズを変更するには、その隅を見つめます。 視線入力カーソルは、サイズ変更カーソルに変わりますしすることができますをタップして保持 + のサイズをドラッグします。 縦または横が 2D のコンテンツによってそのエッジを見ると、ドラッグすることもできます。<br><br>3D コンテンツのサイズを変更するには、ジェスチャのフレームに本の指の両方、手を持ち上げます準備完了の位置。 少し手を 2 つの状態に有効にする、カーソルが表示されます。 タップを行い、両手でジェスチャを保持します。 近くまたは遠く離れている手を移動すると、オブジェクトのサイズが変更されます。 前方と後方互いに手を移動すると、オブジェクトを回転します。 回転することもサイズ変更/2D コンテンツこのようにします。</td>
  </tr>
  <tr>
    <td>2D アプリのリフローで水平方向のサイズを変更します。</td><td>縦横比より多くのアプリのコンテンツを表示するには、広い 2D の UWP アプリを作成します。 たとえば、プレビュー ウィンドウを表示するのに十分なメール アプリを行っています。</td><td>単に、サイズ変更カーソルを参照してください。、tap を使用し、保持 + サイズを変更するジェスチャをドラッグする 2D の UWP アプリの左端または右端を見つめます。</td>
  </tr>
  <tr>
    <td>展開された音声コマンドのサポート</td><td>単に音声を使って詳細に行うことができます。</td><td>これらの音声コマンドを再試行してください。<ul><li>"[スタート] - [スタート] メニューが表示されますか、終了、<a href="app-views.md">没入型のアプリ</a>します。</li><li>「移動」のオブジェクトを移動することができます。</li></ul></td>
  </tr>
  <tr>
    <td>ホログラムや写真の更新されたアプリ</td><td>新しいホログラムでホログラム アプリを更新します。 更新された写真アプリ。</td><td>ホログラムや写真のアプリを最新の外観が表示されます。 ホログラム アプリには、いくつかの新しいホログラムとテキストを簡単に作成するためのラベル メーカーが含まれています。</td>
  </tr>
  <tr>
    <td>複合現実のキャプチャの向上</td><td>ハードウェアのショートカットの開始と終了 MRC ビデオ。</td><td>Volume Up + MRC 録画を開始する 3 秒間ダウンを保持します。 ブルーム ジェスチャを使用して、終了または両方をもう一度タップします。</td>
  </tr>
  <tr>
    <td>統合のスペース</td><td>1 つのスペースにホログラムの空間の管理を簡略化します。</td><td>HoloLens では、自動的には、自分のスペースを検索し、不要になった管理またはスペースを選択する必要があります。 ホログラム周囲で問題がある場合に進んで<b>設定 > システム > ホログラム > ホログラム近くにある削除</b>します。 必要な場合、選択することも<b>削除すべてホログラム</b>します。</td>
  </tr>
  <tr>
    <td>オーディオ immersion の向上</td><td>ノイズの多い環境でより HoloLens を再生し、デバイスによって検出された実際の壁、サウンドが隠されるアプリケーションからよりリアルなサウンドを体験できます。</td><td>強化された空間サウンドをご利用いただくに何もする必要はありません。</td>
  </tr>
  <tr>
    <td>エクスプローラー</td><td>移動し、HoloLens 内からファイルを削除します。</td><td>使用することができます、<b>ファイル エクスプ ローラー</b>アプリに移動し、HoloLens 内からファイルを削除します。<br><br><b>クォータを調整する</b>すべてのファイルが見つからない場合は、「最近」フィルターがアクティブな可能性があります (時計のアイコンが左側のウィンドウで強調表示されます)。 を解決するには、選択、<b>このデバイスを</b>(下に時計アイコン) で、左側のウィンドウでアイコンのドキュメントまたはメニューを開き、選択<b>このデバイスを</b>します。
</td>
  </tr>
  <tr>
    <td>MTP (Media Transfer Protocol) のサポート</td><td>HoloLens で転送ツール向け (写真、ビデオ、ドキュメント)、ライブラリにアクセスするデスクトップ PC をできます。</td><td>同様に他のモバイル デバイス、HoloLens を起動する PC に接続する<b>ファイル エクスプ ローラー</b>転送しやすいように、HoloLens ライブラリ (写真、ビデオ、ドキュメント) にアクセスします。<br><br><b>ヒント:</b><ul><li>すべてのファイルが表示されない場合は、データへのアクセスを有効にする、HoloLens にサインインするようにしてください。</li><li><b>ファイル エクスプ ローラー</b>選択することができます、PC に<b>デバイス プロパティ</b>を Windows Holographic の OS バージョン番号 (ファームウェアのバージョン) とデバイスのシリアル番号を参照してください。</li></ul><b>既知の問題:</b>経由での HoloLens の名前を変更する<b>ファイル エクスプ ローラー</b> PC では有効になっていません。</td>
  </tr>
  <tr>
    <td>セットアップ中に captive portal のネットワークのサポート</td><td>ホテル、会議センター、小売り店、または captive portal を使用している企業でゲスト ネットワーク上、HoloLens を設定することができますようになりました。</td><td>セットアップ中に、ネットワークを選択し、必要な場合、自動的に接続を確認する画面の指示に従って、ネットワークの情報を入力します。</td>
  </tr>
  <tr>
    <td>OneDrive アプリによる写真とビデオの同期</td><td>写真アプリから直接の代わりに Microsoft Store からの OneDrive アプリ経由では、写真やビデオ HoloLens からは同期されますようになりました。</td><td>このセットアップをダウンロードして、ストアから OneDrive アプリを起動します。 初回実行時に自動的に写真を OneDrive にアップロード要求する必要があります。 またはアプリの設定オプションを見つけることができます。</td>
  </tr>
</table>

### <a name="for-developers"></a>開発者向け

<table>
  <tr>
    <th>機能</th><th>詳細</th><th>手順</th>
  </tr>
  <tr>
    <td>空間マッピングの機能強化</td><td>品質、簡略化、およびパフォーマンスの向上。</td><td>空間マッピングのメッシュを簡潔に表示されます: 同じ詳細レベルを表す数の三角形が必要です。 シーン内の三角形の密度の変更があります。</td>
  </tr>
  <tr>
    <td>フォーカス ポイントの深度バッファーのベースの自動選択</td><td>HoloLens ホログラム安定性を最適化するには、自動的にフォーカス ポイントを選択するは、Windows に深度バッファーを送信できます。</td><td>Unity に移動します<b>編集 > プロジェクトの設定 > Player > ユニバーサル Windows プラットフォーム タブ > XR 設定</b>、展開、 <b>Windows Mixed Reality SDK</b>項目を確認してください。<b>深度バッファーを有効にする。共有</b>がチェックされます。 これは、新しいプロジェクトの自動的にチェックするされます。<br><br>DirectX アプリで呼び出すことを確認して、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer">CommitDirect3D11DepthBuffer</a>メソッド<b>HolographicRenderingParameters</b>深度バッファー Windows を指定するには、各フレーム。
</td>
  </tr>
  <tr>
    <td>Holographic reprojection モード</td><td>360 度のビデオなどの厳格本文-ロックされているコンテンツのホログラム安定性を向上させるために HoloLens で位置指定 reprojection を無効にするようになりました。</td><td>Unity では、次のように設定します。 <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html">HolographicSettings.ReprojectionMode</a>に<a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html">HolographicReprojectionMode.OrientationOnly</a>とすべてのコンテンツ ビューには厳格本文-ロックされています。<br><br>DirectX アプリでは、次のように設定します。 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.reprojectionmode"> HolographicCameraRenderingParameters.ReprojectionMode</a>に<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicreprojectionmode">HolographicReprojectionMode.OrientationOnly</a>とすべてのコンテンツ ビューには厳格本文-ロックされています。</td>
  </tr>
  <tr>
    <td>アプリの適合化 Api</td><td>Windows Api では、デバイスの表示は、(HoloLens) を透明または不透明な (型イマーシブ ヘッドセット) かどうかや、UWP アプリの 2D のビューに holographic のシェルで表示されているかどうかなどについて、アプリが実行されている詳細します。</td><td>Unity が手動で公開していた<a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html">HolographicSettings.IsDisplayOpaque</a>このビルドよりも前に動作していたようにします。<br><br>DirectX アプリでのように既存の Api を今すぐにアクセスできる<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.isopaque">HolographicDisplay.GetDefault() します。IsOpaque</a>と<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview.iscurrentviewpresentedonholographicdisplay">HolographicApplicationPreview.IsCurrentViewPresentedOnHolographicDisplay</a> HoloLens のようにします。
</td>
  </tr>
  <tr>
      <td>研究モード</td><td>により、開発者のコンピューター ビジョンとロボット工学のフィールドに新しいアイデアをテストする教育機関、および産業用のアプリケーションを構築するときにキー HoloLens センサーへのアクセスを含みます。<ul><li>4 つのカメラを追跡する環境</li><li>マッピングの深さカメラ データの 2 つのバージョン</li><li>IR 反射ストリームの 2 つのバージョン</li></ul></td><td><a href="research-mode.md">Research モードのドキュメント</a><br><a href="https://github.com/Microsoft/HoloLensForCV">Research モードのサンプル アプリ</a></td>
  </tr>
</table>

### <a name="for-commercial-customers"></a>商用のお客様向け

<table>
  <tr>
    <th>機能</th><th>詳細</th><th>手順</th>
  </tr>
  <tr>
    <td>複数の Azure Active Directory ユーザー アカウントを使用して、1 つのデバイス</td><td>複数の Azure AD ユーザーがそれぞれ独自のユーザー設定とデバイス上のユーザー データ、HoloLens を共有します。</td><td><a href="https://docs.microsoft.com/hololens/hololens-multiple-users">IT Pro Center:複数のユーザーと共有 HoloLens</a></td>
  </tr>
  <tr>
    <td>サインイン時に、Wi-fi ネットワークを変更します。</td><td>最初に、Azure AD ユーザー アカウントでサインインするユーザーをさまざまな場所にデバイスを共有し、ジョブのサイトを許可する別のユーザーを有効にするにはサインインする前に、Wi-fi ネットワークを変更します。</td><td>サインイン画面で、ネットワークに接続する、パスワード フィールドの下のネットワーク アイコンを使用できます。 これは、デバイスへのサインインを初めて行うときに便利です。</td>
  </tr>
  <tr>
    <td>統一された登録</td><td>HoloLens ユーザーにとって、デバイスを職場アカウント (Azure AD) を追加して、デバイスが MDM サーバーを参加させる、個人の Microsoft アカウントを設定することができます。</td><td>単に、Azure AD アカウントでサインインし、登録が自動的に行われます。</td>
  </tr>
  <tr>
    <td>MDM 登録なしのメールの同期</td><td>MDM の登録を必要とせず、Exchange Active Sync (EAS) メール同期のサポート。</td><td>MDM. に登録することがなく電子メールを同期できるようになりました Microsoft アカウントを使用してデバイスを設定するしてダウンロードし、メール アプリをインストールするか、および職場の電子メール アカウントを直接追加できます。</td>
  </tr>
</table>

### <a name="for-it-pros"></a>IT 技術者の場合

<table>
  <tr>
    <th>機能</th><th>詳細</th><th>手順</th>
  </tr>
  <tr>
    <td>新しい"Windows Holographic for Business"OS 名</td><td>HoloLens の商用 Suite の機能が有効になっているときに、エディションのアップグレード ライセンス アプリケーションを混同しないように名前付けのエディションをオフにします。</td><td>デバイス上の Windows Holographic エディションがわかります<b>設定 > システム > に関する</b>します。 Commercial Suite の機能を有効にするエディションの更新プログラムを適用している場合、"Windows Holographic for Business"のメッセージが表示されます。 学習方法<a href="https://docs.microsoft.com/hololens/hololens-upgrade-enterprise">機能の Windows Holographic for Business のロックを解除</a>します。</td>
  </tr>
  <tr>
  <td>Windows Configuration Designer (WCD)</td><td>作成し、更新された WCD アプリ経由での HoloLens を構成するプロビジョニング パッケージを編集します。 エディションの更新プログラム、構成可能な OOBE、リージョン/タイム ゾーン、一括の Azure AD のトークン、ネットワーク、および開発者 CSP の単純な HoloLens ウィザード。 HoloLens でフィルター処理、高度なエディターには、割り当てのアクセスやアカウント管理の Csp などのオプションがサポートされています。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro Center:プロビジョニング パッケージを使用して HoloLens を構成します。</a></td>
  </tr>
  <tr>
    <td>構成可能なセットアップ (OOBE)</td><td>セットアップ中には、調整、ジェスチャ/視線の先のトレーニング、および Wi-fi の構成画面を非表示にします。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning#create-a-provisioning-package-for-hololens-using-the-hololens-wizard">IT Pro Center:プロビジョニング パッケージを使用して HoloLens を構成します。</a></td>
  </tr>
  <tr>
    <td>一括トークンの Azure AD のサポート</td><td>Azure AD ディレクトリ テナントにユーザー セットアップ フローを高速のデバイスを事前登録します。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro Center:プロビジョニング パッケージを使用して HoloLens を構成します。</a></td>
  </tr>
  <tr>
  <td>DeveloperSetup CSP</td><td>開発者モードでの HoloLens を設定するプロファイルを展開します。 開発とデモの両方のデバイスに便利です。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro Center:プロビジョニング パッケージを使用して HoloLens を構成します。</a></td>
  </tr>
  <tr>
  <td>AccountManagement CSP</td><td>HoloLens デバイスを共有し、後のユーザー データを削除するサインアウトまたは一時的に使用できる非アクティブ/記憶域のしきい値。 Azure AD アカウントをサポートしています。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro Center:プロビジョニング パッケージを使用して HoloLens を構成します。</a></td>
  </tr>
  <tr>
  <td>割り当てられたアクセス</td><td>Windows では、最初の行の作業者またはデモのアクセスが割り当てられます。 1 つまたは複数のアプリのロックダウンします。 ロック解除開発者に必要はありません。</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk">IT Pro Center:キオスク モードでの HoloLens を設定します。</a></td>
  </tr>
  <tr>
  <td>デバイスのキオスクのゲスト アクセス</td><td>Windows では、デモのためのパスワードのないゲスト アカウントによるアクセスが割り当てられます。 1 つまたは複数のアプリのロックダウンします。 ロック解除開発者に必要はありません。</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk#guest">IT Pro Center:キオスク モードでの HoloLens を設定します。</a></td>
  </tr>
  <tr>
    <td>(OOBE) 診断を設定します。</td><td>Azure AD サインイン エラーを解決するには、(前のサインインが失敗したユーザーにフィードバック ハブがある) に、ために、HoloLens から診断ログを取得します。</td><td>セットアップまたはサインインが失敗すると、選択、新しい<b>情報の収集</b>トラブルシューティングのための診断ログを取得するにはオプションです。</td>
  </tr>
  <tr>
    <td>ローカル アカウント パスワードが無期限の有効期限</td><td>ローカル アカウントのパスワードの有効期限が切れるときにリセットするデバイスの中断を削除します。</td><td>42 日おきにパスワードを変更するが、ローカル アカウントをプロビジョニングするときに不要になった<b>設定</b>など、アカウントのパスワードが期限切れになくなりました。</td>
  </tr>
  <tr>
    <td>MDM の同期状態と詳細</td><td>MDM の同期状態と HoloLens 内からの詳細を理解する標準の Windows 機能です。</td><td>デバイスに MDM の同期状態を確認できます<b>設定 > アカウント > のアクセスの職場または学校 > 情報</b>します。 <b>デバイス同期ステータス<b> セクションで、同期の開始、MDM によって管理される領域が表示し作成し、高度な診断レポートをエクスポートします。</td>
  </tr>
</table>

## <a name="known-issues"></a>既知の問題

優れた Windows Mixed Reality エクスペリエンスを提供する苦労しましたが、いくつかの既知の問題を管理するいるともいます。 他のユーザーが見つかったら、ください[フィードバック](give-us-feedback.md)します。

### <a name="hololens"></a>HoloLens

#### <a name="after-update"></a>更新後に

RS1 から、HoloLens の RS4 への更新後に、次の問題が発生する可能性があります。
* **Pin リセット**-3 x 3 の [スタート] メニューにピン留めするアプリは、更新後に、既定値にリセットされます。 
* **アプリと配置されたホログラム リセット**-アプリの世界に配置の更新の後が削除され、領域全体で再配置する必要があります。 
* **フィードバック ハブはすぐに起動しない可能性があります**-自体を更新するときに、フィードバック Hub などのいくつかの受信トレイ アプリを起動する前に数分かかります、更新後すぐにします。 
* **企業の Wi-fi 証明書を再同期する必要がある**-企業の証明書に再接続する前に、デバイスに再同期するために別のネットワークに接続している HoloLens の必要な問題を調査しています企業ネットワークが証明書を使用します。 
* **H.265 HEVC ビデオの再生が機能しない**-H.265 ビデオを再生しようとするアプリケーション エラー メッセージが表示されます。 回避するには[Windows Device Portal のアクセス](using-the-windows-device-portal.md)を選択します**アプリ**、左側のナビゲーション バーで、**削除**HEVC アプリケーション。 次に、最新版をインストール[HEVC ビデオ拡張機能](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7)Microsoft Store から。 この問題を調査しています。 

#### <a name="for-developers-updating-hololens-apps-for-devices-running-windows-10-april-2018-update"></a>開発者向け: 10 April 2018 Update の Windows を実行しているデバイスの HoloLens のアプリを更新します。

一覧と共に[の新機能](#new-features-for-hololens)、Windows 10 April 2018 Update (RS4) HoloLens の以前のバージョンではありませんでした一部のコードの動作を適用します。
* **機密性の高いリソース (カメラ、マイクなど) を使用するアクセス許可の要求** -RS4 HoloLens のカメラまたはマイクなどの機密リソースにアクセスするアプリのアクセス許可の要求が適用されます。 これらのメッセージでは、HoloLens の RS1 が強制されないため、アプリは、これらのリソースへのアクセスを引き受けると、それがクラッシュする RS4 で (ユーザーは、要求されたリソースへのアクセス許可を付与) 場合でもです。 関連するをお読みください[UWP アプリの機能宣言記事](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations)詳細についてはします。
* **独自の外部のアプリへの呼び出し**-HoloLens で RS4 の適切な使用が適用されます、 [ *Windows.System.Launcher*クラス](https://docs.microsoft.com/uwp/api/Windows.System.Launcher)独自から別のアプリを起動します。 たとえば、問題を呼び出すアプリを説明しました*Windows.System.Launcher.LaunchUriForResultsAsync* ASTA UI 以外のスレッドから。 これは、HoloLens の RS1 で成功しますが、RS4 には、UI スレッドで実行される呼び出しが必要です。

### <a name="windows-mixed-reality-on-desktop"></a>デスクトップ上の Windows Mixed Reality

#### <a name="visual-quality"></a>画質

* グラフィックスが前よりぼやけること、またはビューのフィールドが、ヘッドセットに小さいことに、Windows 10 April 2018 の更新後にする場合は、パフォーマンスの自動設定が変更された可能性が少ない強力で十分なフレーム レートを維持するために(Nvidia 1050 年頃) などのグラフィックス カード。 手動でこれをオーバーライドできます (選択した場合) に移動して**設定 > 複合現実 > ヘッドセット表示 > エクスペリエンス オプション > 変更**し"90 Hz"を"自動"に変更。 変更することもできます**画質**([設定] ページと同じ) に「高」にします。

#### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality セットアップ

* 接続されているヘッドセットで Windows を設定する場合、PC モニターが空白にします。 Windows セットアップを完了する PC のモニターに出力を有効にする、ヘッドセットを取り外します。
* ヘッドホンを接続していない場合は、home、Windows Mixed Reality を最初にアクセスすると、その他のヒントをされない場合があります。
* 他の Bluetooth デバイスには、アニメーション コント ローラーへの干渉を可能性があります。 アニメーション コント ローラーを確認、Bluetooth 無線 (外付けドングル)、接続/ペアリング/追跡の問題がある場合は、障害物の無い場所に、すぐに別の Bluetooth ドングルの横にある接続されます。 それが役立つ場合に表示する Windows Mixed Reality セッション中に他の Bluetooth 周辺機器の電源にもお試しください。

#### <a name="games-and-apps-from-the-microsoft-store"></a>ゲームや Microsoft Store からアプリ

* Forza モーター スポーツの 7 のように、いくつかの視覚的に処理を要するゲームでは、Windows Mixed Reality 内での再生時に小さい対応の Pc で、パフォーマンスの問題を引き起こす可能性が。

#### <a name="audio"></a>オーディオ

* Cortana は、Windows Mixed Reality ヘッドセットを使用する前に、ホスト PC で有効にした場合は、Windows Mixed Reality ホームの周囲に配置するアプリに適用する空間のサウンド シミュレーションを失う可能性があります。 
   * 回避にも、ヘッドセットに接続されているオーディオ デバイス、PC に接続されているすべてのオーディオ デバイスで「Windows Sonic のヘッドフォン」を有効にするのには。
      1. スピーカーのアイコンをデスクトップ タスク バーでをクリックし、オーディオ デバイスの一覧から選択します。
      2. スピーカー アイコンをデスクトップ タスク バーを右クリックし、「スピーカーの設定」メニューで「Windows Sonic のヘッドフォン」を選択します。
      3. すべてのオーディオ デバイス (エンドポイント) には、次の手順を繰り返します。
   * 別のオプションは「Hey Cortana に Let Cortana 対応」無効**設定** > **Cortana** Windows Mixed Reality を起動する前に、デスクトップ上。
* (Web カメラ) などの別のマルチ メディア USB デバイスは、Windows Mixed Reality ヘッドセットと (外部またはお使いの PC 内) は、同じ USB ハブを共有する場合のまれなケースでヘッドセットのオーディオ ジャック/ヘッドホンがありますか音がかすまたは音声の入っていないすべての。 この操作は、USB ポートを他のデバイスでは、同じハブの共有またはない切断/無効にするその他の USB マルチ メディア デバイスに、ヘッドホンで修正できます。
* 非常にまれな場合は、ホスト PC の USB ハブは、Windows Mixed Reality ヘッドセットに十分な能力を提供できないし、ヘッドセットに接続されているヘッドホンからのノイズのバーストことがわかります。

#### <a name="holograms"></a>ホログラム

* ホログラムの数が多い home、Windows Mixed Reality で、配置されている場合はいくつか非表示になります、周りに再び表示可能性があります。 これを回避するには、Windows Mixed Reality ホーム領域に、ホログラムの一部を削除します。

#### <a name="motion-controllers"></a>アニメーション コント ローラー

* 入力はヘッドセットにルーティングされている、ルーム境界の横に保持されているときに、アニメーション コント ローラーはなくなりますについて簡単に。 デスクトップ モニター間で青いバナーがあることを確認するには、Win + Y キーを押すと、この解決できます。 
* 場合によっては、Microsoft Edge での web ページをクリックすると、コンテンツはクリックの代わりにズームします。

#### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Windows Mixed Reality ホームでデスクトップ アプリ

* Snipping Tool は、デスクトップ アプリでは機能しません。
* デスクトップ アプリでは、再起動時に設定は保持されません。
* Windows Mixed Reality ホームで、デスクトップ アプリを開くときに、デスクトップに Mixed Reality ポータル プレビューを使用している、無限のミラーの効果のことを確認可能性があります。 
* デスクトップ アプリを実行している可能性がありますが発生するパフォーマンスの問題で非-Ultra Windows 混合現実 Pc;その操作は推奨されません。  
* デスクトップ アプリが自動起動デスクトップ上の非表示のウィンドウにフォーカスがあるためです。 
* デスクトップのユーザー アカウント制御プロンプトにより、ヘッドセット、プロンプトが完了するまでに黒を表示します。

#### <a name="windows-mixed-reality-for-steamvr"></a>SteamVR の Windows Mixed Reality

* Mixed Reality ポータルを起動する必要がありますを更新した後、Windows 10 April 2018 の必要なソフトウェア更新プログラムを確実に更新が完了 SteamVR を起動する前にします。 
* SteamVR、Windows との互換性を維持するための Windows Mixed Reality の最新のバージョンである必要があります 10 April 2018 Update。 自動更新をオン for Windows Mixed Reality SteamVR、ストリームのライブラリの「ソフトウェア」セクションにあるのを確認します。  

#### <a name="other-issues"></a>その他の問題

>[!IMPORTANT]
>初期のバージョンの Windows 10 April 2018 Update (バージョン 17134.5) 内部関係者にプッシュには、Windows Mixed Reality を実行するために必要なソフトウェアの一部がありませんでした。 Windows Mixed Reality を使用する場合は、このバージョンを回避することをお勧めします。 

今後の更新プログラムの更新プログラムで修正に取り組んでいるこの更新プログラム (10.0.17134.1) の最初のリリースで Surface Book 2 を使用する場合、パフォーマンスの低下を特定できました。 これは手動で更新または通常を展開する更新プログラムの待機の前に修正されましたまで待機していることをお勧めします。

## <a name="provide-feedback-and-report-issues"></a>フィードバックとレポートの問題を提供します。

使用してください、 [HoloLens または Windows 10 PC でフィードバック ハブ アプリ](give-us-feedback.md)フィードバックおよびレポートの問題を提供します。 フィードバック ハブを使用して、すべての必要な診断情報が含まれており、マイクロソフトのエンジニアは、迅速なデバッグし、問題を解決することをによりします。

>[!NOTE]
>フィードバック Hub ドキュメント フォルダーにアクセスするかどうかを確認するメッセージを受け入れるようにしてください (選択**はい**入力を求められたら)。

## <a name="prior-release-notes"></a>以前のリリース ノート

* [2017 年 10 月のリリース ノート](release-notes-october-2017.md)
* [2016 年 8 月のリリース ノート](release-notes-august-2016.md)
* [2016 年 5 月のリリース ノート](release-notes-may-2016.md)
* [2016 年 3 月のリリース ノート](release-notes-march-2016.md)

## <a name="see-also"></a>関連項目
* [イマーシブ ヘッドセット サポート (外部リンク)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [HoloLens のサポート (外部リンク)](https://support.microsoft.com/products/hololens)
* [ツールをインストールします。](install-the-tools.md)
* [フィードバックを提供します。](give-us-feedback.md)

