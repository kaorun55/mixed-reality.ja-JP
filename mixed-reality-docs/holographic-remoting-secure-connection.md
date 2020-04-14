---
title: Holographic Remoting を使用したセキュリティで保護された接続の確立
description: このページでは、Holographic リモート処理の使用時にセキュリティで保護された暗号化接続を確立する方法について説明します。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理
ms.openlocfilehash: 4006a317ed2ecfd7a1e67336a80a4e536d45e554
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278230"
---
# <a name="establishing-a-secure-connection-with-holographic-remoting"></a><span data-ttu-id="04138-104">Holographic Remoting を使用したセキュリティで保護された接続の確立</span><span class="sxs-lookup"><span data-stu-id="04138-104">Establishing a secure connection with Holographic Remoting</span></span>

>[!IMPORTANT]
><span data-ttu-id="04138-105">このガイダンスは、HoloLens 2 の Holographic リモート処理に固有のものです。</span><span class="sxs-lookup"><span data-stu-id="04138-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="04138-106">このページでは、Holographic リモート処理の使用時にセキュリティで保護された暗号化接続を確立する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="04138-106">This page explains how to establish a secure encrypted connection when using Holographic Remoting.</span></span>

<span data-ttu-id="04138-107">オープン WiFi やインターネットなど、セキュリティで保護されていないネットワーク経由で HoloLens 2 にコンテンツをストリーミングする場合は、暗号化された接続を使用することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="04138-107">When streaming content to HoloLens 2 over a insecure Network such as an open WiFi or the internet it is highly recommended to use an encrypted connection.</span></span>

>[!IMPORTANT]
><span data-ttu-id="04138-108">信頼されたローカル WiFi を使用している場合でも、暗号化された接続を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="04138-108">Even when using a trusted local WiFi using an encrypted connection should be considered.</span></span>

<span data-ttu-id="04138-109">暗号化された接続を使用できるようにするには、[カスタムプレーヤー](holographic-remoting-create-player.md)と[カスタムリモートアプリ](holographic-remoting-create-host.md)の両方を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04138-109">To be able to use a encrypted connection you will need to implement both a [custom player](holographic-remoting-create-player.md) and a [custom remote app](holographic-remoting-create-host.md).</span></span>

<span data-ttu-id="04138-110">暗号化は、基になるプラットフォームの TLS 実装を使用して実現されます。</span><span class="sxs-lookup"><span data-stu-id="04138-110">The encryption is achieved by using the underlying platforms TLS implementation.</span></span>

## <a name="basics-of-an-encrypted-connection"></a><span data-ttu-id="04138-111">暗号化された接続の基礎</span><span class="sxs-lookup"><span data-stu-id="04138-111">Basics of an encrypted connection</span></span>

<span data-ttu-id="04138-112">証明書の交換を可能にするには、次のオブジェクトを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04138-112">The following objects need to be implemented to allow for a certificate exchange.</span></span>

>[!TIP]
><span data-ttu-id="04138-113">WinRT インターフェイスの実装は、/winrtを使用してC++簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="04138-113">Implementing WinRT interfaces can easily be done using C++/WinRT.</span></span> <span data-ttu-id="04138-114">この詳細については、「[作成 api」をC++](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis)参照してください。</span><span class="sxs-lookup"><span data-stu-id="04138-114">The [Author APIs with C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) chapter describes this in detail.</span></span>

>[!IMPORTANT]
><span data-ttu-id="04138-115">NuGet パッケージ内の ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` には、セキュリティで保護された接続に関連する API の詳細なドキュメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="04138-115">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API related to secure connections.</span></span>

1) <span data-ttu-id="04138-116">```ICertificate``` インターフェイスを実装する必要がある証明書オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="04138-116">A certificate object, which needs to implement the ```ICertificate``` interface.</span></span>

    * <span data-ttu-id="04138-117">```GetCertificatePfx``` メソッドを使用して、pfx 証明書のバイナリコンテンツを返します。</span><span class="sxs-lookup"><span data-stu-id="04138-117">Return the binary contents of the pfx certificate through the ```GetCertificatePfx``` method.</span></span> <span data-ttu-id="04138-118">.Pfx ファイルのバイナリコンテンツと同じです。</span><span class="sxs-lookup"><span data-stu-id="04138-118">Same as the binary contents of a .pfx file.</span></span>
    * <span data-ttu-id="04138-119">```GetSubjectName```を使用して証明書のサブジェクト名を返します。</span><span class="sxs-lookup"><span data-stu-id="04138-119">Return the certificate subject name through ```GetSubjectName```.</span></span>
    * <span data-ttu-id="04138-120">```GetPfxPassword```を使用して pfx パスワードを返します。</span><span class="sxs-lookup"><span data-stu-id="04138-120">Return the pfx password through ```GetPfxPassword```.</span></span> <span data-ttu-id="04138-121">保護されていない pfx の空の文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="04138-121">Return an empty string for an unprotected pfx.</span></span>

2) <span data-ttu-id="04138-122">```GetCertificate``` メソッドで要求されたときに証明書を提供する ```ICertificateProvider``` インターフェイスを実装する証明書プロバイダー。</span><span class="sxs-lookup"><span data-stu-id="04138-122">A certificate provider implementing the ```ICertificateProvider``` interface which provides a certificate when asked through the ```GetCertificate``` method.</span></span>

3) <span data-ttu-id="04138-123">```ICertificateValidator``` インターフェイスを実装する証明書検証コントロール。</span><span class="sxs-lookup"><span data-stu-id="04138-123">A certificate validator implementing the ```ICertificateValidator``` interface.</span></span> <span data-ttu-id="04138-124">このタスクでは、受信証明書を確認します。</span><span class="sxs-lookup"><span data-stu-id="04138-124">Its task is to verify incoming certificates.</span></span>
    * <span data-ttu-id="04138-125">```PerformSystemValidation``` メソッドは、基になるプラットフォームが受信証明書チェーンを検証する必要がある場合に ```true``` を返す必要があります。それ以外の場合は ```false``` ます。</span><span class="sxs-lookup"><span data-stu-id="04138-125">The ```PerformSystemValidation``` method should return ```true``` when the underlying platform should validate the incoming certificate chain, ```false``` otherwise.</span></span>
    * <span data-ttu-id="04138-126">```ValidateCertificate``` は、証明書の検証を要求するためにクライアントコンテキストによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="04138-126">```ValidateCertificate``` is called by the client context to request validation of a certificate.</span></span> <span data-ttu-id="04138-127">このメソッドは、証明書チェーン (最初の証明書がサブジェクト証明書である)、接続が確立されているサーバーの名前、および失効確認を強制的に行うかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="04138-127">This method accepts the certificate chain (with the first certificate being the subject certificate), the name of the server the connection is being established with, and whether a revocation check should be forced.</span></span> <span data-ttu-id="04138-128">基になるシステムによる検証が要求された場合、システム検証の結果が提供されます。</span><span class="sxs-lookup"><span data-stu-id="04138-128">The system validation result will be provided if validation by the underlying system has been requested.</span></span> <span data-ttu-id="04138-129">適切な結果を使用して ```CertificateValidated``` の処理を続行するには、または ```Cancel``` 渡された ```ICertificateValidationCallback```で検証をキャンセルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="04138-129">To continue processing either ```CertificateValidated``` with the appropriate result or ```Cancel``` to cancel validation needs to be called on the passed ```ICertificateValidationCallback```.</span></span>

<span data-ttu-id="04138-130">さらに、セキュリティで保護されたトークンを交換できるようにするには、次のオブジェクトを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04138-130">Furthermore, to allow for the exchange of a secure token the following objects need to be implemented.</span></span>

1) <span data-ttu-id="04138-131">```IAuthenticationProvider``` インターフェイスを実装する認証プロバイダー。</span><span class="sxs-lookup"><span data-stu-id="04138-131">An authentication provider implementing the ```IAuthenticationProvider``` interface.</span></span> <span data-ttu-id="04138-132">クライアントの認証のためのトークンを要求するために、```GetToken``` メソッドがクライアントコンテキストによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="04138-132">Its ```GetToken``` method is called by the client context to request a token for client authentication.</span></span> <span data-ttu-id="04138-133">```TokenReceived``` を続行するには、認証トークンを指定して接続プロセスを続行するか ```Cancel``` をキャンセルするには、渡された ```IAuthenticationProviderCallback```に対してプロセスを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="04138-133">To continue either ```TokenReceived``` to provide the authentication token and continue the connection process or ```Cancel``` to cancel the process needs to be called on the passed ```IAuthenticationProviderCallback```.</span></span>
2) <span data-ttu-id="04138-134">```IAuthenticationReceiver``` インターフェイスを実装する認証受信者。</span><span class="sxs-lookup"><span data-stu-id="04138-134">An authentication receiver implementing the ```IAuthenticationReceiver``` interface.</span></span> <span data-ttu-id="04138-135">このタスクでは、受信トークンを検証します。</span><span class="sxs-lookup"><span data-stu-id="04138-135">Its task is to validate incoming tokens.</span></span>
    * <span data-ttu-id="04138-136">```GetRealm``` メソッドは、認証領域の名前を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="04138-136">The ```GetRealm``` method should return the name of the authentication realm.</span></span>
    * <span data-ttu-id="04138-137">```ValidateToken``` メソッドは、クライアント認証トークンの検証を要求するために、サーバーネットワークコンテキストによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="04138-137">The ```ValidateToken``` method is called by the server network context to request validation of a client authentication token.</span></span> <span data-ttu-id="04138-138">続行するには、```ValidationCompleted``` を呼び出して検証の完了を通知するか、```Cancel``` してクライアント接続を拒否します。</span><span class="sxs-lookup"><span data-stu-id="04138-138">To continue either call ```ValidationCompleted``` to signal completion of the validation or ```Cancel``` to reject the client connection..</span></span> <span data-ttu-id="04138-139">```ValidationCompleted```に渡された検証結果に基づいて、クライアント接続が受け付けまたは拒否されます。</span><span class="sxs-lookup"><span data-stu-id="04138-139">The client connection will be admitted or rejected based on the validation result passed to ```ValidationCompleted```.</span></span> 

<span data-ttu-id="04138-140">これらのオブジェクトを実装した後は、リモートコンテキストとプレーヤーコンテキストでは ```Connect``` なく、```Listen``` と ```ConnectSecure``` ではなく ```ListenSecure``` を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="04138-140">Once these objects are implemented ```ListenSecure``` needs to be called instead of ```Listen``` and ```ConnectSecure``` instead of ```Connect``` on the remote context and player context respectively.</span></span> <span data-ttu-id="04138-141">```ListenSecure``` には、```Listen```経由で追加の証明書プロバイダーと認証受信者が必要です。</span><span class="sxs-lookup"><span data-stu-id="04138-141">```ListenSecure``` requires an additional certificate provider and authentication receiver over ```Listen```.</span></span> <span data-ttu-id="04138-142">```ConnectSecure``` には、追加の認証プロバイダーと、```Connect```に対する証明書検証が必要です。</span><span class="sxs-lookup"><span data-stu-id="04138-142">```ConnectSecure``` requires an additional authentication provider and certificate validator over ```Connect```.</span></span>

## <a name="see-also"></a><span data-ttu-id="04138-143">参照</span><span class="sxs-lookup"><span data-stu-id="04138-143">See Also</span></span>
* [<span data-ttu-id="04138-144">Holographic リモート処理リモートアプリの作成</span><span class="sxs-lookup"><span data-stu-id="04138-144">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="04138-145">カスタム Holographic リモート処理プレーヤーアプリの作成</span><span class="sxs-lookup"><span data-stu-id="04138-145">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="04138-146">Holographic リモート処理のトラブルシューティングと制限事項</span><span class="sxs-lookup"><span data-stu-id="04138-146">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="04138-147">Holographic Remoting ソフトウェア ライセンス条項</span><span class="sxs-lookup"><span data-stu-id="04138-147">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="04138-148">Microsoft のプライバシーに関する声明</span><span class="sxs-lookup"><span data-stu-id="04138-148">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
