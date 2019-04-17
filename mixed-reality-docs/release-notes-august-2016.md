---
title: 2016 年 8 月のリリース ノート
description: Windows 10 Anniversary リリース (2016 年秋) の HoloLens のリリース ノート
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、リリース ノート、os、プラットフォーム、機能、商用のスイート
ms.openlocfilehash: 2fde8665f3572589abd3dcdfb3747ca487b66afb
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603666"
---
# <a name="release-notes---august-2016"></a>2016 年 8 月のリリース ノート

HoloLens チームは、開発者が取り組みの優先順位を Windows Insider Program からフィードバックをリッスンします。 引き続き[フィードバックを提供](give-us-feedback.md)フィードバック ハブ経由、[デベロッパー フォーラム](https://forums.hololens.com)と[経由で Twitter @HoloLens ](https://twitter.com/hololens)。 Windows 10 Anniversary Update、HoloLens のチームが配信を支配はホログラフィック操作にさらに向上させます。 この更新で大規模な修正、改善、および企業と、Microsoft HoloLens Commercial Suite で使用可能な要求された概要の機能に注目します。

**最新リリース:** Windows Holographic の 2016 年 8 月の更新プログラム (**10.0.14393.0**、Windows 10 Anniversary リリース)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

[現在のリリースに更新](updating-hololens.md)、オープン、*設定*に移動して、アプリ*更新とセキュリティ*を選択し、*更新プログラムの確認*ボタンをクリックします。

## <a name="new-features"></a>新しい機能

**プロセスのデバッグにアタッチ**HoloLens はプロセスにアタッチ デバッグ サポートしているようになりました。 Visual Studio 2015 Update 3 を使用するには、HoloLens の実行中のアプリに接続して[デバッグを開始](using-visual-studio.md#debugging-an-installed-or-running-app)します。 これは、Visual Studio プロジェクトからデプロイする必要はありません。

**HoloLens のエミュレーターを更新**HoloLens のエミュレーターの更新バージョンもリリースしました。

**Gamepad サポート**ペアリングし、HoloLens で Bluetooth ゲームパッドを使用できます。 新たにリリースされた Xbox のワイヤレス コント ローラー S は機能 Bluetooth 機能と、ゲームパッドが有効なお気に入りのゲームとアプリを再生するために使用できます。 A[コント ローラーの更新](http://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)HoloLens と Xbox のワイヤレス コント ローラーの秒を接続する前に適用する必要があります。 Xbox のワイヤレス コント ローラーの S がでサポートされて[XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx)と[Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) Api。 Bluetooth コント ローラーの追加のモデルをアクセス、 [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API。

## <a name="improvements-and-fixes"></a>機能強化と修正

Hololens の個々 の修正に加えてもから受信するすべての適合度プラットフォームの信頼性とパフォーマンスを向上させる Windows 更新プログラムがあるため、Windows 10 Anniversary update での残りの部分との同期が。 フィードバックは高い値し、リリースで修正プログラムの優先順位を設定します。

以下のエクスペリエンスを改善しました。
* エクスペリエンスにログインします。
* 社内参加します。
* デバイスの電源の状態遷移の電力効率。
* 安定性 Mixed Reality をキャプチャします。
* Bluetooth 接続の信頼性
* マルチ アプリのシナリオでホログラム永続化します。

次の問題を修正しました。
* Visual Studio プロファイラーとグラフィックス デバッガーの接続に失敗します。
* 写真とドキュメントは表示されません、デバイス ポータル ファイル エクスプ ローラー。
* アプリ バーは、調整モードでは、上にカーソルが配置されるときに点滅します。
* 調整モードの場合、目注視ドット カーソルに変わります 4 矢印カーソルいずれかの時点より緩やかに変化します。
* "こんにちは Cortana で音楽を再生"Groove は起動しません。
* 前回の更新後に"移動 Home"と答えるとが正しく表示されませんピン パネル。

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Microsoft HoloLens の商用 Suite の概要

Microsoft HoloLens Commercial Suite エンタープライズ展開の準備ができました。 頻繁に要求されるいくつか追加しました[商用機能](commercial-features.md)早期のビジネス パートナーから。

Microsoft HoloLens Commercial Suite を購入する、ローカルのマイクロソフト アカウント マネージャーにお問い合わせください。

### <a name="key-commercial-features"></a>キーの商用機能 

* **キオスク モード。** HoloLens のキオスク モードでは、デモまたはショーケースのエクスペリエンスを有効にするを実行するアプリを制限できます。<br>
  ![キオスク モードでは、HoloLens は好みのアプリに直接起動します。](images/201608-kioskmode-400px.png)
* **HoloLens のモバイル デバイス管理 (MDM)。** IT 部門は、Microsoft Intune などのソリューションを使用して同時に複数の HoloLens デバイスを管理できます。 設定の管理、インストールするアプリの選択、組織のニーズに合わせたセキュリティ構成の設定を行うことができます。<br>
  ![HoloLens でモバイル デバイス管理は、複数のデバイスでのエンタープライズ グレードのデバイス管理を提供します。](images/201608-enterprisemanagement-400px.png)
* **Windows Update for Business。** デバイスおよび long-term servicing branch のサポートにオペレーティング システムの更新プログラムを制御します。
* **データのセキュリティ。** 同じレベルの他の Windows デバイスのセキュリティ保護を提供する、HoloLens の BitLocker データ暗号化が有効です。
* **職場のアクセス。** 組織内のすべてのユーザーは、HoloLens で仮想プライベート ネットワーク経由で企業ネットワークにリモートで接続できます。 HoloLens の資格情報を必要とする Wi-fi ネットワークにアクセスできます。
* **ビジネス向け Microsoft Store。** IT 部門はことができますも、特定 HoloLens 使用量、会社のアプリのみを格納しているエンタープライズ プライベート ストアの場合を設定します。 エンタープライズ ユーザーの選択したグループに、エンタープライズ ソフトウェアを安全に配信します。

### <a name="development-edition-vs-commercial-suite"></a>開発エディションとCommercial Suite

<table>
<tr>
<th>機能</th><th>Development Edition</th><th>Commercial Suite</th>
</tr><tr>
<td>デバイスの暗号化 (Bitlocker)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>仮想プライベート ネットワーク (VPN)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="using-the-windows-device-portal.md#kiosk-mode">キオスク モード</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 管理と展開</th>
</tr><tr>
<td>モバイル デバイス管理 (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>登録解除をブロックする機能</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>証明書ベースの企業の Wi-fi アクセス</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (コンシューマー)</td><td style="text-align: center;">コンシューマー</td><td style="text-align: center;">MDM を介したフィルタ リング</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">ビジネス ストア ポータル</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> セキュリティと ID</th>
</tr><tr>
<td>Azure Active Directory (AAD) でログイン</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft アカウント (MSA) でログイン</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>暗証番号 (pin) と [次へ] の生成の資格情報のロックを解除します。</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">セキュア ブート</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> サービスとサポート</th>
</tr><tr>
<td>システムの自動更新が到着します。</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Windows Update for Business</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>長期的なサービス ブランチ</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>以前のリリース ノート
* [2016 年 5 月のリリース ノート](release-notes-may-2016.md)
* [2016 年 3 月のリリース ノート](release-notes-march-2016.md)

## <a name="see-also"></a>関連項目
* [HoloLens の既知の問題](hololens-known-issues.md)
* [商用機能](commercial-features.md)
* [ツールをインストールします。](install-the-tools.md)
* [HoloLens のエミュレーターを使用する](using-the-hololens-emulator.md)
