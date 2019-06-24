---
title: MR Learning ASA モジュール HoloLens 2 での Azure 空間アンカー
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 4dc36aec4d885fa75ea490446c2d682264049725
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326891"
---
# <a name="persistence-and-sharing-of-azure-spatial-anchors"></a>永続化と Azure の空間アンカーの共有

このレッスンでは、HoloLens 2 のディスクにアンカー情報を保存することによって、複数のアプリケーション セッション間で、Azure の空間アンカーを永続化する方法を学びます。 マルチ デバイスのアンカーの配置に関するその他のデバイスには、このアンカー情報を共有する方法も説明します。

## <a name="objectives"></a>目標

* 保存し、アプリ セッションの間で永続化のため、HoloLens 2 のローカル ディスクから Azure 空間アンカー情報を取得する方法について説明します

* マルチ デバイスのシナリオでユーザーの間での Azure 空間アンカー情報を共有する方法について説明します

  

## <a name="instructions"></a>手順

### <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>ディスクにアンカー ID 保存 - アプリのセッション間での Azure のアンカーを永続化します。

1. 検索し、"SaveAnchorToDisk"プレハブをシーンに追加します。 これらには、2 つのボタン、HoloLens 2 ディスクとディスクから任意の Id を取得するために、使用可能な Azure アンカー Id を保存するための 1 つのボタンが含まれます。

   ![module2chapter2step1im](images/module2chapter2step1im.PNG)

2. 以下の手順に従って各ボタンを構成します。
   - "SaveToDisk"をという名前のボタン、イベント トリガーの「ボタンが押されている」と「クリックして」イベント トリガーの下に新しいイベントを作成します。 空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから SaveAzureAnchorIDToDisk() メソッドを割り当てます。
   
     > 注: 他のボタン、シーン内の重複をボタンがあります。 自由に、ボタンの位置を調整します。
   

  ![module2chapter2step2aim](images/module2chapter2step2aim.PNG)

![module2chapter2step2aim](images/module2chapter2step2bim.PNG)

![module2chapter2step2aim](images/module2chapter2step2cim.PNG)

   - "GetFromDisk"をという名前のボタン、イベント トリガーの「ボタンが押されている」と「クリックして」イベント トリガーの下に新しいイベントを作成します。 空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから LoadAzureAnchorIDsFromDisk() メソッドを割り当てます。

3. デバイスに更新されたアプリケーションを作成するレッスン 1 の指示に従います。 Azure アンカー"作成"ボタンをクリックして、前のレッスンで行ったよう保存すると Azure アンカー ID をディスクにキーを押してボタンをディスクに保存します。

4. アプリケーションを再起動して、Azure セッションを開始、"負荷アンカー ID"をクリックし、およびディスクに保存した ID に関連付けられているアンカーを検索する「Azure アンカーの検索」ボタンを押します。 シーン全体を今すぐスナップ位置に、位置の前に保存したアンカーです。

### <a name="share-azure-anchors-between-multiple-devices"></a>Azure のアンカーを複数のデバイス間で共有します。

このセクションで説明、複数のデバイス間で Azure アンカー ID を共有する方法をします。 これにより、複数のデバイスの同じアンカー ID を Azure のクエリを実行する、固定ホログラムとシーン空間的に配置することができます。 (複数のデバイス間で同じ物理的な場所で同じホログラムが表示される) 空間の配置では、HoloLens 2 でのキーをローカルの共有エクスペリエンスです。 チュートリアルの Azure 空間アンカーの共有エクスペリエンスで説明したメソッドを含む、すべてのデバイス間の関連の azure Id 情報を転送する方法はたくさんあります (TODO: リンクを追加します)。この例では、単純な web サービスを使用して、アップロードし、デバイス間でアンカー Id をダウンロードします。

1. 階層に"ShareAnchor"プレハブを追加します。 このプレハブ; シーンに 2 つの新しいボタンを追加しますアンカー ID 情報とダウンロード用に別のアップロードの 1 つは、ID 情報を固定します。 

   ![module2chapter2step5im](images/module2chapter2step5im.PNG)

2. 以下の手順に従って各ボタンを構成します。

   - "SendSharedAnchor"をという名前のボタン、イベント トリガーの「ボタンが押されている」と「クリックして」イベント トリガーの下に新しいイベントを作成します。 空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから ShareAnchor() メソッドを割り当てます。

     ![module2chapter2step6aim](images/module2chapter2step6aim.PNG)

     ![module2chapter2step6bim](images/module2chapter2step6bim.PNG)

     

   - "GetSharedAnchor"をという名前のボタン、イベント トリガーの「ボタンが押されている」と「クリックして」イベント トリガーの下に新しいイベントを作成します。 空のフィールドに ParentAnchor オブジェクトをドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから GetSharedAzureAnchor() メソッドを割り当てます。

3. 指示に従って[レッスン 1](mrlearning-base-ch1.md)します。 デバイスに更新されたアプリケーションを構築します。 Azure アンカー"作成"ボタンを押した後に、前のレッスンで行ったよう、その他のデバイスを共有するボタンを押して、他のデバイスに Azure アンカー ID を共有可能性がありますようになりました。

   > 注:親アンカーを選択して、親のアンカー スクリプトまで下へスクロールします。 共有した場合、これが共有しているお客様がわかるように、"パブリック共有 pin"が一意であることを確認します。 これにより、正しい Azure アンカーを共有していることを確認するために、Azure のアンカーを共有しているユーザーの何千もの可能性があります。

4. 別の HoloLens 2 デバイスがあれば、アプリケーションを起動し、Azure セッションを開始します。 "共有アンカー ID の取得"ボタンを押すし、ディスクに保存した ID に関連付けられているアンカーを検索する"Azure アンカーの検索 ボタンを押します。 シーン全体を位置にスナップする必要があるようになりました where でその他の HoloLens 2 デバイスに配置された場合。 HoloLens 2 を 1 つだけの場合する可能性がありますもテスト機能、アプリケーションを再起動することによって Azure セッションを開始して"共有アンカー ID の取得"ボタンを押し、Azure アンカー"検索"ボタンに関連付けられているアンカーを検索するキーを押しますID ディスクに保存しました。 シーン全体を今すぐスナップ位置に、位置の前に保存したアンカーです。

## <a name="congratulations"></a>結論
このレッスンでは、アプリ セッションとアプリの再起動の間、HoloLens 2 のローカル ディスクに Azure 空間アンカー ID を保存することによって Azure 空間アンカーを永続化する方法について説明しました。 複数のデバイス、共有、基本のマルチ ユーザーの静的なホログラム エクスペリエンスの間で Azure 空間アンカーを共有する方法も学習しました。

共有モジュールの最後のレッスンの中に完全にインタラクティブなローカル共有エクスペリエンスの一部として Azure 空間アンカーを実装する方法について説明します。 ローカル共有のエクスペリエンスは、各ユーザーの同期済みの 3D オブジェクトの位置、回転、およびスケール、識別子などの機能を含めることができ、アプリケーションの状態を共有します。 Azure 空間アンカーは、物理的に同じ場所に仮想オブジェクトを表示するすべてのユーザーが共通のアンカーを持つ各参加者を提供することでこれらの共有のシナリオを強化します。 これは、HoloLens、Android、および iOS デバイスを含め、デバイス プラットフォームの範囲にわたる場合は true。 共有のエクスペリエンスを開発する方法については、共有モジュール内のすべてのレッスンを完了してください。

次のレッスンでは、リアルタイムのフィードバックをユーザーに提供する方法を学びます。 このフィードバックは、アンカーの作成、環境の理解の品質および Azure のセッションの状態に関する情報が含まれます。 フィードバック、ユーザーご存じないアンカーを Azure にアップロードが正常かどうか、環境の品質がアンカーの作成、または現在の状態のための十分なかどうか。

[次のレッスン:ASA Lesson 3](mrlearning-asa-ch3.md)

