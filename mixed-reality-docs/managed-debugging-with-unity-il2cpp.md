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
# <a name="managed-debugging-with-unity-il2cpp"></a>Unity il2cpp バック エンドを使用したデバッグの管理

マネージ デバッガーを Unity il2cpp バック エンド UWP ビルドにアタッチするこれらの手順に従います。 このガイドは、もともと HoloLens と HoloLens 2 開発されました。

1. いることを確認**InternetClientServer**と**PrivateNetworkClientServer** Unity UWP 公開設定機能の下でチェックされます。

    ![UWP 設定機能を公開](images/il2cpp-debugging-capabilities.png)

1. UWP の Unity ビルド設定を構成するには。
    - 開発のビルド
    - スクリプト デバッグ
    - マネージ デバッガー (省略可能) の待機

    ![UWP のビルド設定](images/il2cpp-debugging-build.png)

1. Unity でビルドします。
1. ビルドし、Visual Studio ソリューションからデバイスにデプロイします。 ビルドする必要があります、**デバッグ**または**リリース**構成します。 **マスター**構成は、Unity profiler を無効にし、最適なデバッグするを防ぐことができます。 必要に応じて、確認**インターネット (クライアントとサーバー)** と**プライベート ネットワーク (クライアントとサーバー)** Package.appxmanifest の中に、ソリューション内の機能の一覧にします。
1. デバイスでアプリを起動します。 デバイスが、PC と同じネットワークに接続されていることを確認します。
1. デバイスを必ず**でない**USB 経由で PC に接続します。
1. Unity を表示および編集できますでスクリプトをダブルクリックするときに作成される Visual Studio ソリューションに移動して、C#スクリプト。
1. デバッグ]、[Unity デバッガーをアタッチします。

    ![Unity デバッガーをアタッチします。](images/il2cpp-debugging-attach.png)

1. 一覧で、デバイスを選択して、アタッチするには、[OK] をクリックします。

    ![デバイスの一覧](images/il2cpp-debugging-machines.png)
