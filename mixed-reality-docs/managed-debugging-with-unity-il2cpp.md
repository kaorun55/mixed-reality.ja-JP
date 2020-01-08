---
title: Unity を使用したマネージデバッグ IL2CPP
description: この記事では、Unity IL2CPP UWP プロジェクトでマネージデバッガーを実行する方法について説明します。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity、visual studio、デバッグ、il2cpp
ms.openlocfilehash: 970d3000df995e7c6e331a41d10e25dc5aa370a8
ms.sourcegitcommit: 7e8b9de561cbc8483e84511f3e9cbd779f3a999f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/27/2019
ms.locfileid: "75502663"
---
# <a name="managed-debugging-with-unity-il2cpp"></a>Unity を使用したマネージデバッグ IL2CPP

マネージデバッガーを Unity IL2CPP UWP ビルドにアタッチするには、次の手順に従います。 このガイドは、初めて HoloLens および HoloLens 2 用に開発されました。

1. [マルチキャスト](https://en.wikipedia.org/wiki/Multicast)をサポートしているネットワーク上に配置する必要があります。
1. UWP 発行設定機能の下で、 **Internet Clientserver**と**PrivateNetworkClientServer**が Unity でチェックインされていることを確認します。

    ![UWP 発行設定機能](images/il2cpp-debugging-capabilities.png)

1. Unity UWP ビルド設定を構成します。
    - 開発のビルド
    - スクリプト デバッグ
    - マネージデバッガーを待機する (省略可能)

    ![UWP ビルドの設定](images/il2cpp-debugging-build.png)

1. Unity でビルドします。
1. Visual Studio ソリューションからデバイスにビルドしてデプロイします。 **デバッグ**構成または**リリース**構成を使用してビルドする必要があります。 **マスター**構成によって Unity プロファイラーが無効になり、最適なデバッグができなくなる可能性があります。 必要に応じて、ソリューションの package.appxmanifest の [機能] ボックスの一覧で、**インターネット (クライアント & サーバー)** と**プライベートネットワーク (クライアント & サーバー)** を確認します。
1. デバイスでアプリを起動します。 デバイスが PC と同じネットワークに接続されていることを確認します。
1. デバイスが USB 経由で PC に接続されて**いない**ことを確認します。
1. Unity でスクリプトをダブルクリックすると作成される Visual Studio ソリューションに移動します。ここでスクリプトを表示および編集C#できます。
1. デバッグ-> Unity デバッガーをアタッチします。

    ![Unity デバッガーのアタッチ](images/il2cpp-debugging-attach.png)

1. 一覧からデバイスを選択し、[OK] をクリックして接続します。

    ![デバイス一覧](images/il2cpp-debugging-machines.png)
