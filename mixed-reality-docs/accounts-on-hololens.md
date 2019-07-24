---
title: HoloLens のアカウント
description: HoloLens でユーザーアカウントを設定および管理する方法。
author: ''
ms.author: toddly
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、user、account、aad、adfs、microsoft アカウント、msa、資格情報
ms.openlocfilehash: 14f43b08b6ccb396bcf39c4082c840c65ac78cf9
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516813"
---
# <a name="accounts-on-hololens"></a>HoloLens のアカウント

初回の HoloLens セットアップ中に、ユーザーは、デバイスで使用するアカウントでサインインする必要があります。 このアカウントは、Azure Active Directory (AAD) または Active Directory フェデレーションサービス (AD FS) (ADFS) で構成されたコンシューマー Microsoft アカウントまたはエンタープライズアカウントのいずれかになります。

セットアップ中にこのアカウントにサインインすると、ユーザーがサインインに使用できるユーザープロファイルがデバイスに作成され、すべてのアプリにそのデータが保存されます。 この同じアカウントでは、Windows アカウントマネージャー Api を使用して Edge や Skype などのアプリのシングルサインオンを行うこともできます。

さらに、デバイスのエンタープライズアカウントまたは組織アカウントにサインインするときに、IT 管理者によって構成されている場合は、モバイルデバイス管理 (MDM) ポリシーが適用されることもあります。

デバイスが再起動されるか、スタンバイから再開されるたびに、このアカウントの資格情報が再度サインインに使用されます。 [明示的なサインインを適用する] オプションが [設定] で有効になっている場合、ユーザーは資格情報を再度入力する必要があります。 OS 更新プログラムを受け取って適用した後、デバイスが再起動されるたびに、明示的なサインインが必要になります。

## <a name="multi-user-support"></a>マルチユーザーサポート

>[!NOTE]
>[Windows Holographic For Business の](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise)機能であるため、マルチユーザーサポートには商用スイートが必要です。

[Windows 10 April 2018 Update](release-notes-april-2018.md)以降では、HoloLens は同じ AAD テナント内から複数のユーザーをサポートしています。 これを使用するには、最初に、組織に属するアカウントを使用してデバイスを設定する必要があります。 その後、同じテナントの他のユーザーは、サインイン画面からデバイスにサインインできます。または、[スタート] パネルのユーザータイルをタップして既存のユーザーをサインアウトさせることができます。 

デバイスにインストールされているアプリは、他のすべてのユーザーが使用できるようになりますが、それぞれのアプリのデータと設定は異なります。 ただし、アプリを削除すると、他のすべてのユーザーに対しても削除されます。 

デバイスからデバイスのユーザーを削除して、[設定]、[他のユーザー] > の [> アカウント] に移動して、領域を再利用することができます。 これにより、デバイスから他のユーザーのアプリデータもすべて削除されます。 

## <a name="linked-accounts"></a>リンクされたアカウント

ユーザーは、1つのデバイスアカウント内で、アプリ内で簡単にアクセスできるように、追加の web アカウント資格情報をリンクしたり (ストアなど)、デスクトップバージョンの Windows と同様に、個人リソースと仕事用リソースへのアクセスを組み合わせることができます。 この方法で追加のアカウントにサインインしても、イメージやダウンロードなど、デバイス上に作成されたユーザーデータは分離されません。 1つのアカウントがデバイスに接続されると、アプリはアクセス許可を使用して、各アプリに個別にサインインする必要が少なくなります。

## <a name="using-single-sign-on-within-an-app"></a>アプリ内でのシングルサインオンの使用

アプリ開発者は、他の Windows デバイスと同様に、 [Windows アカウントマネージャー api](https://msdn.microsoft.com/library/windows/apps/xaml/windows.security.authentication.web.core.aspx)を使用して HoloLens に接続された id を持つことができます。 これらの Api のコードサンプルについては、[こちら](http://go.microsoft.com/fwlink/p/?LinkId=620621)を参照してください。

アカウント情報や2要素認証などのユーザーの同意要求など、発生する可能性のあるアカウントの割り込みは、アプリが認証トークンを要求するときに処理する必要があります。

前にリンクされていない特定の種類のアカウントがアプリに必要な場合は、アプリでユーザーにメッセージを追加するように求めるメッセージを表示することができます。 これにより、アプリのモーダル子として [アカウント設定] ウィンドウが起動されます。 2D アプリの場合、このウィンドウはアプリの中央に直接表示され、Unity アプリでは、この子ウィンドウがレンダリングされるように、holographic アプリからユーザーを簡単に移動できます。 このウィンドウでのコマンドとアクションのカスタマイズについては、[こちら](https://msdn.microsoft.com/library/windows/apps/windows.ui.applicationsettings.webaccountcommand.aspx)を参照してください。

## <a name="enterprise-and-other-authentication"></a>エンタープライズ認証とその他の認証

アプリが NTLM、基本、Kerberos などの他の種類の認証を使用している場合は、 [Windows 資格情報 UI](https://msdn.microsoft.com/library/windows/apps/windows.security.credentials.ui.aspx)を使用して、ユーザーの資格情報を収集、処理、および保存できます。 これらの資格情報を収集するためのユーザーエクスペリエンスは、他のクラウド駆動型のアカウント割り込みと非常によく似ており、2D アプリの上部に子アプリとして表示されるか、または Unity アプリを一時的に中断して UI を表示します。

## <a name="deprecated-apis"></a>非推奨の Api

HoloLens on Desktop で開発する場合の違いの1つは、 [Onlineidauthenticator](https://msdn.microsoft.com/library/windows/apps/windows.security.authentication.onlineid.onlineidauthenticator.aspx) API が完全にはサポートされていないことです。 プライマリアカウントが良好な場合はトークンを返しますが、上記のような割り込みはユーザーの UI を表示せず、アカウントを正しく認証できません。

