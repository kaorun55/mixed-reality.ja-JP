---
title: HoloLens のアカウント
description: HoloLens でアカウントを設定して、ユーザーを管理する方法。
author: ''
ms.author: toddly
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, user, account, aad, adfs, microsoft account, msa, credentials
ms.openlocfilehash: 14f43b08b6ccb396bcf39c4082c840c65ac78cf9
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599831"
---
# <a name="accounts-on-hololens"></a>HoloLens のアカウント

HoloLens の初期セットアップ中には、デバイスで使用するアカウントでサインインするユーザーが必要です。 このアカウントは、コンシューマー Microsoft アカウントまたは Azure Active Directory (AAD) または Active Directory フェデレーション サービス (ADFS) で構成されているエンタープライズ アカウントのいずれかにできます。

セットアップ中にこのアカウントにサインインをユーザーが使用できるデバイスでユーザー プロファイルが作成、サインインするすべてのアプリのデータの格納とします。 この同じアカウントは、Edge、または Windows アカウント マネージャー Api を使用して、Skype などのアプリのシングル サインオンも提供します。

さらに、エンタープライズまたはデバイス上の組織のアカウントをサインインするときに可能性がありますもモバイル デバイス管理 (MDM) ポリシーを適用する、IT 管理者によって構成されている場合

デバイスが再起動またはスタンバイから再開、されるたびに、このアカウントの資格情報は、もう一度サインインに使用されます。 設定で、明示的なサインインを適用するオプションが有効な場合、ユーザーが自分の資格情報をもう一度入力する必要があります。 デバイスが再起動を受信し、OS の更新プログラムを適用した後、いつでも、明示的なサインインが必要です。

## <a name="multi-user-support"></a>マルチ ユーザー サポート

>[!NOTE]
>これはマルチ ユーザー サポートは、商用のスイートが必要です、 [Windows Holographic for Business](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise)機能します。

以降では、 [Windows 10 April 2018 Update](release-notes-april-2018.md)HoloLens、同じ AAD テナント内から複数のユーザーをサポートしています。 これを使用するには、お客様の組織に属しているアカウントを使用して最初にデバイスを設定する必要があります。 その後、同じテナントから他のユーザーは、既存のユーザーをサインアウトするサインイン画面から、または [スタート] パネルのユーザー タイルをタップして、デバイスにサインインすることになります。 

その他のすべてのユーザーに利用できるデバイスにインストールされているアプリしますが、それぞれ独自のアプリのデータと設定。 アプリを削除するも削除されますが他のすべてのユーザーが。 

デバイスのユーザーを削除するには設定に移動して領域を再利用するデバイスから > アカウント > 他のユーザー。 また、デバイスからすべての他のユーザーのアプリ データこれも削除されます。 

## <a name="linked-accounts"></a>リンクされたアカウント

(ストア) などのアプリ内で簡単にアクセスするために、追加の web アカウントの資格情報をリンクする、1 つのデバイス アカウント内または個人と職場のリソース、Windows のデスクトップ バージョンのようなへのアクセスを結合します。 この方法で追加のアカウントにサインインは、イメージなど、デバイスで作成されたユーザー データを分離しないまたはダウンロードします。 アプリを作成できるアカウントをデバイスに接続すると、アプリごとに個別にサインインすることを削減する、アクセス許可を持つことの使用します。

## <a name="using-single-sign-on-within-an-app"></a>アプリ内でのシングル サインオンを使用してください。

アプリ開発者の場合での HoloLens で接続されている id を格納する利点を行う、 [Windows アカウント マネージャー Api](https://msdn.microsoft.com/library/windows/apps/xaml/windows.security.authentication.web.core.aspx)上の他の Windows デバイスの場合と同様、します。 これらの Api のいくつかのコード サンプルは[ここ](http://go.microsoft.com/fwlink/p/?LinkId=620621)します。

アカウント情報の要求元のユーザーなどになる可能性があるアカウント割り込みに同意するものをアプリは、認証トークンを要求すると、2 要素認証などを処理する必要があります。

アプリでは、以前にリンクされていない特定のアカウントの種類を必要とする場合、アプリは、1 つ追加するユーザー入力を求めるシステムを要求できます。 これにより、アプリの子のモーダルとして起動されるようにアカウント設定 ウィンドウがトリガーされます。 2D アプリは、Unity アプリのアプリのセンター経由で直接このウィンドウを表示、この子ウィンドウが表示できるように、これについて簡単に holographic アプリからユーザーにかかるは。 コマンドおよびウィンドウでこの操作のカスタマイズが説明されている[ここ](https://msdn.microsoft.com/library/windows/apps/windows.ui.applicationsettings.webaccountcommand.aspx)します。

## <a name="enterprise-and-other-authentication"></a>Enterprise およびその他の認証

アプリが行う場合の他の種類の認証を使用して、NTLM、Basic、または Kerberos などを使用できます[Windows 資格情報の UI](https://msdn.microsoft.com/library/windows/apps/windows.security.credentials.ui.aspx)を収集、処理、およびユーザーの資格情報を格納します。 これらの資格情報を収集するためのユーザー エクスペリエンスは現在アカウント割り込み駆動型の他のクラウドによく似ていますと 2D アプリ上に子アプリとして表示されます、または、UI を表示する Unity アプリを簡単に中断されます。

## <a name="deprecated-apis"></a>非推奨の Api

デスクトップから HoloLens での開発の違いの 1 つは[OnlineIDAuthenticator](https://msdn.microsoft.com/library/windows/apps/windows.security.authentication.onlineid.onlineidauthenticator.aspx) API が完全にサポートされていません。 などの割り込み優良、プライマリのアカウントがある場合、トークンが返されますが上記で説明した、ユーザーの UI は表示されませんしは、アカウントを正しく認証に失敗します。

