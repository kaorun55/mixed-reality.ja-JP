---
title: Azure 空間アンカーチュートリアル-2. Azure 空間アンカーの保存、取得、共有
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: d03579bf04081f3729baa7d8d76d92586a416184
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539711"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2. Azure 空間アンカーを保存、取得、共有する

このチュートリアルでは、HoloLens 2 のストレージにアンカー情報を保存することで、複数のアプリセッションにわたって Azure 空間アンカーを保存する方法について説明します。 また、このアンカー情報を、複数デバイスのアンカーの配置のために他のデバイスと共有する方法についても説明します。

## <a name="objectives"></a>目標

* アプリセッション間の永続化のために、HoloLens 2 ローカルディスクから Azure 空間アンカー情報を保存および取得する方法について説明します。

* マルチデバイスシナリオでユーザー間で Azure 空間アンカー情報を共有する方法について説明します。

## <a name="instructions"></a>手順

### <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>アプリセッション間で Azure のアンカーを保持する-アンカー ID をディスクに保存する

1. SaveAnchorToDisk prefab を検索し、シーンに追加します。 これには、2つのボタンがあります。1つのボタンで、使用可能な Azure Anchor Id を HoloLens 2 ストレージに保存し、別のボタンを使用してディスクから Id を取得します。

![module2chapter2step1im](images/module2chapter2step1im.PNG)

2. 次の手順に従って各ボタンを構成します。

   - SaveToDisk という名前のボタンについては、Click イベントトリガーと On Click イベントトリガーの両方に新しいイベントを作成します。 ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから SaveAzureAnchorIDToDisk () メソッドを割り当てます。
   
     > 注: 一部のボタンは、シーン内の他のボタンと重なって表示される場合があります。 ボタンの位置を自由に調整できます。

![module2chapter2step2aim](images/module2chapter2step2aim.PNG)

![module2chapter2step2aim](images/module2chapter2step2bim.PNG)

![module2chapter2step2aim](images/module2chapter2step2cim.PNG)


   - GetFromDisk という名前のボタンに対して、Click イベントトリガーと On Click イベントトリガーの下に新しいイベントを作成します。 ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから LoadAzureAnchorIDsFromDisk () メソッドを割り当てます。

3. チュートリアル1の指示に従って、更新されたアプリケーションをデバイスにビルドします。 前のレッスンで行ったように、[Azure アンカーの作成] ボタンを押した後、[ディスクに保存] ボタンを押して、Azure Anchor ID をディスクに保存できるようになりました。

4. アプリケーションを再起動し、Azure セッションを開始して、[Load Anchor ID] を押します。次に、[Azure アンカーの検索] をクリックして、ディスクに保存した ID に関連付けられているアンカーを探します。 これで、以前にアンカーを保存した場所で、シーン全体が位置にスナップされるようになりました。

### <a name="share-azure-anchors-between-multiple-devices"></a>複数のデバイス間で Azure アンカーを共有する

このセクションでは、複数のデバイス間で Azure Anchor ID を共有する方法について説明します。 これにより、複数のデバイスが同じアンカー ID に対して Azure に対してクエリを実行できるようになり、固定されたホログラムとシーンを空間的に調整できるようになります。 空間の配置 (複数のデバイス間で同じ物理的な場所にある同じホログラムが表示されます) は、HoloLens 2 のローカル共有エクスペリエンスにとって重要です。 デバイス間で azure Id に関する情報を転送するには、さまざまな方法があります。 Azure 空間アンカー共有エクスペリエンスチュートリアルの[チュートリアル](mrlearning-sharing(photon)-ch1.md)に記載されている方法があります。 この例では、単純な web サービスを使用して、デバイス間でアンカー Id をアップロードしてダウンロードします。

1. 階層に編成アンカーの事前作成を追加します。 この prefab は、シーンに2つの新しいボタンを追加します。1つはアンカー ID 情報をアップロードするためのもので、もう1つはアンカー ID 情報をダウンロードするためのものです。 

![module2chapter2step5im](images/module2chapter2step5im.PNG)

2. 次の手順に従って各ボタンを構成します。

   - SendSharedAnchor という名前のボタンに対して、Click イベントトリガーと On Click イベントトリガーの下に新しいイベントを作成します。 ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから、"/" メソッドを割り当てます。

![module2chapter2step6aim](images/module2chapter2step6aim.PNG)

![module2chapter2step6bim](images/module2chapter2step6bim.PNG)

   - GetSharedAnchor という名前のボタンに対して、Click イベントトリガーと On Click イベントトリガーの下に新しいイベントを作成します。 ParentAnchor オブジェクトを空のフィールドにドラッグし、ParentAnchor オブジェクトの ASAmoduleScript コンポーネントから GetSharedAzureAnchor () メソッドを割り当てます。

3. [チュートリアル 1](mrlearning-base-ch1.md)の指示に従って、更新されたアプリケーションをデバイスにビルドします。 前のレッスンで行ったように、[Azure アンカーの作成] ボタンを押した後、[他のデバイスに共有] ボタンを押すと、Azure アンカー ID を他のデバイスに共有できるようになります。

   > 注: 親アンカーを選択し、親アンカースクリプトまで下にスクロールします。 パブリック共有 pin が一意であることを確認してください (pin を別の番号に変更することもできます)。共有すると、共有していることがわかります。 多数のユーザーが Azure のアンカーを共有している可能性があります。これにより、適切な Azure アンカーを共有していることを確認できます。
   > 

![module2chapter2step7bim](images/module2chapter2step7bim.PNG)

4. 別の HoloLens 2 デバイスがある場合は、アプリケーションを起動し、Azure セッションを開始します。 [共有アンカー ID の取得] ボタンをクリックし、[Azure アンカーの検索] ボタンを押して、web サービスを使用して共有した ID に関連付けられているアンカーを探します。 シーン全体が、他の HoloLens 2 デバイスに配置された位置にスナップするようになります。 HoloLens 2 が1つしかない場合は、アプリケーションを再起動して Azure セッションを開始し、[共有アンカー ID の取得] ボタンをクリックしてから [Azure アンカーの検索] ボタンを押して、ID に関連付けられているアンカーを見つけることで、機能をテストできます。ディスクに保存されます。 これで、以前にアンカーを保存した場所で、シーン全体が位置にスナップされるようになりました。

## <a name="congratulations"></a>結論
このレッスンでは、azure 空間アンカー ID を HoloLens 2 のローカルディスクに保存することで、アプリケーションセッションとアプリケーションの再起動の間で Azure 空間アンカーを永続化する方法について学習しました。 また、複数のデバイス間で Azure 空間アンカーを共有し、基本的なマルチユーザーの静的なホログラム共有エクスペリエンスを実現する方法についても学習しました。

共有モジュールの最後のレッスンで、完全に対話型のローカル共有エクスペリエンスの一部として Azure 空間アンカーを実装する方法について説明します。 ローカル共有エクスペリエンスには、同期された3D オブジェクトの位置、回転、スケール、各ユーザーの識別子、共有アプリケーションの状態などの機能が含まれる場合があります。 Azure 空間アンカーは、各参加者に共通のアンカーを提供することで、これらの共有シナリオを強化します。これにより、すべてのユーザーが同じ物理的な場所に仮想オブジェクトを表示できるようになります。 これは、HoloLens、Android、iOS デバイスなど、さまざまなデバイスプラットフォームで当てはまります。 共有エクスペリエンスを開発する方法については、共有モジュールのすべてのレッスンを完了してください。

次のレッスンでは、リアルタイムのフィードバックをユーザーに提供する方法について説明します。 このフィードバックには、アンカーの作成、環境の理解の質、Azure セッションの状態に関する情報が含まれています。 フィードバックがないと、アンカーが Azure に正常にアップロードされたかどうか、環境の品質がアンカーの作成に十分であるか、現在の状態であるかをユーザーが知ることができません。

[次のレッスン: 3. Azure 空間アンカーフィードバックの表示](mrlearning-asa-ch3.md)

