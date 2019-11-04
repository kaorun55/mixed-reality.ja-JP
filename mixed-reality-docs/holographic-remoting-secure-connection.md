---
title: Holographic Remoting を使用したセキュリティで保護された接続の確立
description: このページでは、Holographic リモート処理の使用時にセキュリティで保護された暗号化接続を確立する方法について説明します。
author: bethau
ms.author: bethau
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理
ms.openlocfilehash: 1142ba3bd8b0d05202ccd04885de5d70165872d1
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434197"
---
# <a name="establishing-a-secure-connection-with-holographic-remoting"></a>Holographic Remoting を使用したセキュリティで保護された接続の確立

>[!IMPORTANT]
>このガイダンスは、HoloLens 2 の Holographic リモート処理に固有のものです。

このページでは、Holographic リモート処理の使用時にセキュリティで保護された暗号化接続を確立する方法について説明します。

オープン WiFi やインターネットなど、セキュリティで保護されていないネットワーク経由で HoloLens 2 にコンテンツをストリーミングする場合は、暗号化された接続を使用することを強くお勧めします。

>[!IMPORTANT]
>信頼されたローカル WiFi を使用している場合でも、暗号化された接続を使用することを検討してください。

暗号化された接続を使用できるようにするには、[カスタムプレーヤー](holographic-remoting-create-player.md)と[カスタムホストアプリ](holographic-remoting-create-host.md)の両方を実装する必要があります。

暗号化は、基になるプラットフォームの TLS 実装を使用して実現されます。

## <a name="basics-of-an-encrypted-connection"></a>暗号化された接続の基礎

証明書の交換を可能にするには、次のオブジェクトを実装する必要があります。

>[!TIP]
>WinRT インターフェイスの実装は、/winrtを使用してC++簡単に行うことができます。 この詳細については、「[作成 api」をC++](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis)参照してください。

>[!IMPORTANT]
>NuGet パッケージ内の ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` には、セキュリティで保護された接続に関連する API の詳細なドキュメントが含まれています。

1) ```ICertificate``` インターフェイスを実装する必要がある証明書オブジェクト。

    * ```GetCertificatePfx``` メソッドを使用して、pfx 証明書のバイナリコンテンツを返します。 .Pfx ファイルのバイナリコンテンツと同じです。
    * ```GetSubjectName```を使用して証明書のサブジェクト名を返します。
    * ```GetPfxPassword```を使用して pfx パスワードを返します。 保護されていない pfx の空の文字列を返します。

2) ```GetCertificate``` メソッドで要求されたときに証明書を提供する ```ICertificateProvider``` インターフェイスを実装する証明書プロバイダー。

3) ```ICertificateValidator``` インターフェイスを実装する証明書検証コントロール。 このタスクでは、受信証明書を確認します。
    * ```PerformSystemValidation``` メソッドは、基になるプラットフォームが受信証明書チェーンを検証する必要がある場合に ```true``` を返す必要があります。それ以外の場合は ```false``` ます。
    * ```ValidateCertificate``` は、証明書の検証を要求するためにクライアントコンテキストによって呼び出されます。 このメソッドは、証明書チェーン (最初の証明書がサブジェクト証明書である)、接続が確立されているサーバーの名前、および失効確認を強制的に行うかどうかを指定します。 基になるシステムによる検証が要求された場合、システム検証の結果が提供されます。 適切な結果を使用して ```CertificateValidated``` の処理を続行するには、または ```Cancel``` 渡された ```ICertificateValidationCallback```で検証をキャンセルする必要があります。

さらに、セキュリティで保護されたトークンを交換できるようにするには、次のオブジェクトを実装する必要があります。

1) ```IAuthenticationProvider``` インターフェイスを実装する認証プロバイダー。 クライアントの認証のためのトークンを要求するために、```GetToken``` メソッドがクライアントコンテキストによって呼び出されます。 ```TokenReceived``` を続行するには、認証トークンを指定して接続プロセスを続行するか ```Cancel``` をキャンセルするには、渡された ```IAuthenticationProviderCallback```に対してプロセスを呼び出す必要があります。
2) ```IAuthenticationReceiver``` インターフェイスを実装する認証受信者。 このタスクでは、受信トークンを検証します。
    * ```GetRealm``` メソッドは、認証領域の名前を返す必要があります。
    * ```ValidateToken``` メソッドは、クライアント認証トークンの検証を要求するために、サーバーネットワークコンテキストによって呼び出されます。 続行するには、```ValidationCompleted``` を呼び出して検証の完了を通知するか、```Cancel``` してクライアント接続を拒否します。 ```ValidationCompleted```に渡された検証結果に基づいて、クライアント接続が受け付けまたは拒否されます。 

これらのオブジェクトを実装した後は、リモートコンテキストとプレーヤーコンテキストでは ```Connect``` なく、```Listen``` と ```ConnectSecure``` ではなく ```ListenSecure``` を呼び出す必要があります。 ```ListenSecure``` には、```Listen```経由で追加の証明書プロバイダーと認証受信者が必要です。 ```ConnectSecure``` には、追加の認証プロバイダーと、```Connect```に対する証明書検証が必要です。

## <a name="see-also"></a>参照
* [Holographic Remoting ホストアプリの作成](holographic-remoting-create-host.md)
* [カスタム Holographic リモート処理プレーヤーアプリの作成](holographic-remoting-create-player.md)
* [Holographic リモート処理のトラブルシューティングと制限事項](holographic-remoting-troubleshooting.md)
* [Holographic Remoting ソフトウェア ライセンス条項](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft のプライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)
