---
title: Unity il2cpp バック エンドを使用したデバッグの管理
description: この記事では、マネージ デバッガーを Unity il2cpp バック エンドの UWP プロジェクトで実行する方法について説明します。
author: keveleigh
ms.author: kurtie
ms.date: 06/13/19
ms.topic: article
keywords: unity, visual studio, debugging, il2cpp
ms.openlocfilehash: eb4655633384fcb5d7f27546134e21857e5c5502
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148857"
---
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="53b03-104">Unity il2cpp バック エンドを使用したデバッグの管理</span><span class="sxs-lookup"><span data-stu-id="53b03-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="53b03-105">マネージ デバッガーを Unity il2cpp バック エンド UWP ビルドにアタッチするこれらの手順に従います。</span><span class="sxs-lookup"><span data-stu-id="53b03-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build.</span></span> <span data-ttu-id="53b03-106">このガイドは、もともと HoloLens と HoloLens 2 開発されました。</span><span class="sxs-lookup"><span data-stu-id="53b03-106">This guide was originally developed for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="53b03-107">いることを確認**InternetClientServer**と**PrivateNetworkClientServer** Unity UWP 公開設定機能の下でチェックされます。</span><span class="sxs-lookup"><span data-stu-id="53b03-107">Ensure that **InternetClientServer** and **PrivateNetworkClientServer** are checked in Unity under the UWP Publishing Settings Capabilities.</span></span>

    ![UWP 設定機能を公開](images/il2cpp-debugging-capabilities.png)

1. <span data-ttu-id="53b03-109">UWP の Unity ビルド設定を構成するには。</span><span class="sxs-lookup"><span data-stu-id="53b03-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="53b03-110">開発のビルド</span><span class="sxs-lookup"><span data-stu-id="53b03-110">Development Build</span></span>
    - <span data-ttu-id="53b03-111">スクリプト デバッグ</span><span class="sxs-lookup"><span data-stu-id="53b03-111">Script Debugging</span></span>
    - <span data-ttu-id="53b03-112">マネージ デバッガー (省略可能) の待機</span><span class="sxs-lookup"><span data-stu-id="53b03-112">Wait for Managed Debugger (optional)</span></span>

    ![UWP のビルド設定](images/il2cpp-debugging-build.png)

1. <span data-ttu-id="53b03-114">Unity でビルドします。</span><span class="sxs-lookup"><span data-stu-id="53b03-114">Build in Unity.</span></span>
1. <span data-ttu-id="53b03-115">ビルドし、Visual Studio ソリューションからデバイスにデプロイします。</span><span class="sxs-lookup"><span data-stu-id="53b03-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="53b03-116">ビルドする必要があります、**デバッグ**または**リリース**構成します。</span><span class="sxs-lookup"><span data-stu-id="53b03-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="53b03-117">**マスター**構成は、Unity profiler を無効にし、最適なデバッグするを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="53b03-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="53b03-118">必要に応じて、確認**インターネット (クライアントとサーバー)** と**プライベート ネットワーク (クライアントとサーバー)** Package.appxmanifest の中に、ソリューション内の機能の一覧にします。</span><span class="sxs-lookup"><span data-stu-id="53b03-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
1. <span data-ttu-id="53b03-119">デバイスでアプリを起動します。</span><span class="sxs-lookup"><span data-stu-id="53b03-119">Start the app on your device.</span></span> <span data-ttu-id="53b03-120">デバイスが、PC と同じネットワークに接続されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="53b03-120">Make sure your device is connected to the same network as your PC.</span></span>
1. <span data-ttu-id="53b03-121">デバイスを必ず**でない**USB 経由で PC に接続します。</span><span class="sxs-lookup"><span data-stu-id="53b03-121">Make sure the device **is not** connected to your PC via USB.</span></span>
1. <span data-ttu-id="53b03-122">Unity を表示および編集できますでスクリプトをダブルクリックするときに作成される Visual Studio ソリューションに移動して、C#スクリプト。</span><span class="sxs-lookup"><span data-stu-id="53b03-122">Go to the Visual Studio solution that's created when you double click a script in Unity, where you can view and edit your C# scripts.</span></span>
1. <span data-ttu-id="53b03-123">デバッグ]、[Unity デバッガーをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="53b03-123">Debug -> Attach Unity Debugger.</span></span>

    ![Unity デバッガーをアタッチします。](images/il2cpp-debugging-attach.png)

1. <span data-ttu-id="53b03-125">一覧で、デバイスを選択して、アタッチするには、[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="53b03-125">Select your device in the list and click "OK" to attach.</span></span>

    ![デバイスの一覧](images/il2cpp-debugging-machines.png)
