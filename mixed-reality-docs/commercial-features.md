---
title: 商用機能
description: Microsoft HoloLens 商用 Suite には、企業が HoloLens デバイスを簡単に管理できるようにする機能が含まれています。  HoloLens 2 は、既定では商用機能を equipt しています。
author: scooley
ms.author: scooley
ms.date: 05/23/2019
ms.topic: article
keywords: HoloLens, 商用, 機能, mdm, モバイルデバイス管理, キオスクモード
ms.openlocfilehash: 4da540072fd32ac99692f0a13eb5852337c493bb
ms.sourcegitcommit: aba33a8ad1416f7598048ac35ae9ab1734bd5c37
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/28/2019
ms.locfileid: "66270358"
---
# <a name="commercial-features"></a>商用機能

Microsoft HoloLens 商用 Suite には、企業が HoloLens デバイスを簡単に管理できるようにする機能が含まれています。

HoloLens には、開発者ライセンスと商用ライセンスという2つのライセンスオプションが付属しています。  Developer liense から商用ライセンスにアップグレードして、HoloLens の商用 capabilitis のロックを解除します。  Microsoft HoloLens 商用スイートを購入するには、ローカルの Microsoft アカウントマネージャーに問い合わせてください。

**Hololens 2 の新**機能-hololens 2 すべてのデバイスで利用可能な市販の機能が付属しています。

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

## <a name="key-commercial-features"></a>主要商用機能

* **キオスクモード。** HoloLens キオスクモードでは、実行するアプリを制限してデモやショーケースを有効にすることができます。

  ![キオスクモードでは、HoloLens は選択したアプリに直接起動します。](images/201608-kioskmode-400px.png)

* **HoloLens 用のモバイルデバイス管理 (MDM)。** IT 部門は、Microsoft Intune などのソリューションを使用して、複数の HoloLens デバイスを同時に管理できます。 設定の管理、インストールするアプリの選択、組織のニーズに合わせたセキュリティ構成の設定を行うことができます。

  ![HoloLens のモバイルデバイス管理は、複数のデバイスにわたるエンタープライズレベルのデバイス管理を提供します。](images/201608-enterprisemanagement-400px.png)
   
* **ビジネス向け Windows Update。** デバイスに対するオペレーティングシステムの更新と、長期的なサービスブランチのサポートを制御します。
* **データのセキュリティ。** HoloLens で BitLocker データ暗号化が有効になっているため、他の Windows デバイスと同じレベルのセキュリティ保護が提供されます。
* **職場へのアクセス。** 組織内のすべてのユーザーが、HoloLens の仮想プライベートネットワークを介して企業ネットワークにリモート接続できます。 HoloLens は、資格情報を必要とする Wi-fi ネットワークにアクセスすることもできます。
* **ビジネス向け Microsoft Store。** また、IT 部門は、特定の HoloLens 使用量について会社のアプリのみを含むエンタープライズプライベートストアをセットアップすることもできます。 エンタープライズユーザーの選択したグループにエンタープライズソフトウェアを安全に配布します。

## <a name="development-edition-vs-commercial-suite"></a>開発エディションと商用スイート

<table>
<tr>
<th>機能</th><th>HoloLens 開発エディション</th><th>HoloLens Commercial Suite</th><th>HoloLens 2</th>
</tr><tr>
<td>デバイスの暗号化 (Bitlocker)</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>仮想プライベート ネットワーク (VPN)</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="using-the-windows-device-portal.md#kiosk-mode">キオスクモード</a></td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 管理と展開</th>
</tr><tr>
<td>モバイル デバイス管理 (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>登録解除をブロックする機能</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>証明書ベースの会社の Wi-fi アクセス</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (コンシューマー)</td><td style="text-align: center;">者</td><td style="text-align: center;">MDM を使用したフィルター処理</td><td style="text-align: center;">MDM を使用したフィルター処理</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">ビジネスストアポータル</a></td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> セキュリティと ID</th>
</tr><tr>
<td>Azure Active Directory を使用したログイン (AAD)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft アカウント (MSA) を使用してログインする</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>PIN のロック解除を含む次世代の資格情報</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">セキュア ブート</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> サービスとサポート</th>
</tr><tr>
<td>自動的にシステムを更新する</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">ビジネス向け Windows Update</a></td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>長期的なサービスブランチ</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr>
</table>



## <a name="enabling-commercial-features"></a>商用機能の有効化

Microsoft Store for Business、キオスクモード、エンタープライズ Wi-fi アクセスなどの商用機能は、組織の IT 管理者によって設定されます。[WINDOWS IT Center For HoloLens](https://docs.microsoft.com/hololens)では、デバイスの登録と Microsoft Store for Business からのアプリのインストールについて、詳細な手順を説明しています。

## <a name="see-also"></a>関連項目
* [HoloLens 向け IT プロフェッショナルガイド](https://technet.microsoft.com/itpro/hololens/index)
* [キオスクモード](using-the-windows-device-portal.md#kiosk-mode)
* [Windows Holographic for enterprise でサポートされている Csp](https://msdn.microsoft.com/library/windows/hardware/dn920025(v=vs.85).aspx#HoloLens)
* [ビジネスアプリケーションと基幹業務アプリケーションの Microsoft Store](https://blogs.technet.microsoft.com/sbucci/2016/04/13/windows-store-for-business-and-line-of-business-applications/)
* [基幹業務アプリの操作](https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps)
