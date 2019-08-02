---
title: Holographic Remoting を使用したセキュリティで保護された接続の確立
description: このページでは、Holographic リモート処理の使用時にセキュリティで保護された暗号化接続を確立する方法について説明します。
author: bethau
ms.author: bethau
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理
ms.openlocfilehash: 5bc039d7a1e500f577c4a30d2d082b718a45a8b4
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718076"
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
>WinRT インターフェイスの実装は、/winrtを使用してC++簡単に行うことができます。 この詳細については、「[作成 api」をC++](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/author-apis)参照してください。

>[!IMPORTANT]
>NuGet ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```パッケージ内には、セキュリティで保護された接続に関連する API の詳細なドキュメントが含まれています。

1) ```ICertificate```インターフェイスを実装する必要がある証明書オブジェクト。

    * メソッドを```GetCertificatePfx```使用して、pfx 証明書のバイナリコンテンツを返します。 .Pfx ファイルのバイナリコンテンツと同じです。
    * 証明書のサブジェクト名を```GetSubjectName```から返します。
    * を介して```GetPfxPassword```pfx パスワードを返します。 保護されていない pfx の空の文字列を返します。

2) ```GetCertificate```メソッドで要求され```ICertificateProvider```たときに証明書を提供するインターフェイスを実装する証明書プロバイダー。

3) ```ICertificateValidator```インターフェイスを実装する証明書検証コントロール。 このタスクでは、受信証明書を確認します。
    * この```PerformSystemValidation```メソッドは、 ```true```基になるプラットフォームが受信証明書チェーンを検証```false```する必要がある場合にを返します。それ以外の場合はを返します。
    * ```ValidateCertificate```は、証明書の検証を要求するためにクライアントコンテキストによって呼び出されます。 このメソッドは、証明書チェーン (最初の証明書がサブジェクト証明書である)、接続が確立されているサーバーの名前、および失効確認を強制的に行うかどうかを指定します。 基になるシステムによる検証が要求された場合、システム検証の結果が提供されます。 適切な結果```CertificateValidated```を使用して処理を```Cancel```続行する場合、または渡さ```ICertificateValidationCallback```れたに対して検証をキャンセルする必要がある場合は。

さらに、セキュリティで保護されたトークンを交換できるようにするには、次のオブジェクトを実装する必要があります。

1) インターフェイスを```IAuthenticationProvider```実装する認証プロバイダー。 クライアント```GetToken```の認証のためのトークンを要求するために、そのメソッドがクライアントコンテキストによって呼び出されます。 認証トークンを提供して接続```Cancel```プロセスを続行するかキャンセルするには、渡さ```IAuthenticationProviderCallback```れたに対してプロセスを呼び出す必要があります。 ```TokenReceived```
2) インターフェイスを```IAuthenticationReceiver```実装する認証受信者。 このタスクでは、受信トークンを検証します。
    * メソッド```GetRealm```は、認証領域の名前を返します。
    * ```ValidateToken```メソッドは、クライアント認証トークンの検証を要求するために、サーバーネットワークコンテキストによって呼び出されます。 を呼び出して検証```ValidationCompleted```の完了を通知するか、 ```Cancel```クライアント接続を拒否するには、を呼び出します。 クライアント接続は、に```ValidationCompleted```渡された検証結果に基づいて、受け付けまたは拒否されます。 

これらのオブジェクトを実装```ListenSecure```した後は、リモートコンテキスト```ConnectSecure```およびプレーヤー ```Connect```コンテキストではなく、との```Listen```代わりにを呼び出す必要があります。 ```ListenSecure```で```Listen```は、追加の証明書プロバイダーと認証レシーバーが必要です。 ```ConnectSecure```で```Connect```は、追加の認証プロバイダーと証明書検証を行う必要があります。

## <a name="see-also"></a>関連項目
* [Holographic Remoting ホストアプリの作成](holographic-remoting-create-host.md)
* [カスタム Holographic リモート処理プレーヤーアプリの作成](holographic-remoting-create-player.md)
* [Holographic リモート処理のトラブルシューティングと制限事項](holographic-remoting-troubleshooting.md)
* [Holographic リモート処理ソフトウェアライセンス条項](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft のプライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)