---
title: HoloLens 2 用 MR Learning 共有モジュール
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 53519d7bb2832fe8ce500f1ee146c91488b09366
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485657"
---
# <a name="3-connecting-multiple-users"></a>3.複数のユーザーの接続

このレッスンでは、ライブ共有エクスペリエンスの一部として複数のユーザーを接続する方法について説明します。 このレッスンを終了すると、複数のデバイスでアプリケーションを開くことができます。また、アバターは、参加する各ユーザーの球体で表現されます。 

事項

- アプリケーション内でさしあたっを構成する
- プレーヤーの構成
- 共有エクスペリエンスで複数のユーザーを接続する方法について説明します。

## <a name="instructions"></a>手順

1. 次の図に示すように、[アセット-> Resources-> Prefabs] フォルダーの [プロジェクト] パネルで、NetworkLobby prefab を階層にドラッグアンドドロップします。

![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. NetworkLobby を展開すると、Networklobby という子オブジェクトが表示されます。 NetworkRoom を選択した状態で、[インスペクター] パネルにアクセスし、[コンポーネントの追加] をクリックします。 PhotonView を検索し、コンポーネントを追加します。

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. 階層内に新しい空のゲームオブジェクトを作成します。 階層内を右クリックし、コンテキストメニューから [空] を選択します。 位置が x = 0、y = 0、z = 0 に設定されていることを確認し、オブジェクトに PhotonUser という名前を指定します。

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. [コンポーネントの追加] をクリックし、「Generic Net Sync」と入力します。汎用 Net Sync クラスを選択します。 クラスが表示されたら、[ユーザー] チェックボックスをクリックしてオンにします。 

![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. [コンポーネントの追加] をもう一度クリックし、「Photon View」と入力します。 ドロップダウンリストに表示される Photon View クラスを選択します。

![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. 汎用 Net Sync クラスのファイルアイコンをクリックします。 Photon ビューの [観測されたコンポーネント] フィールドにドラッグアンドドロップします。 

![module3chapter3updateStep6im](images/module3chapter3updateStep6im.png) 

7. 次に、共有エクスペリエンスに参加する各ユーザーを表す球体を作成します。 先ほど作成した PhotonUser オブジェクトを右クリックし、[3D オブジェクト] までスクロールして [球] をクリックします。 これにより、PhotonUser オブジェクトの子として球ゲームオブジェクトが作成されます。

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. 球を x = 0.06、y = 0.06、ad z = 0.06 にスケールダウンします。

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. PhotonUser game オブジェクトを [プロジェクト] パネルの Prefabs フォルダーにドラッグし、シーンから削除します。 これで、共有エクスペリエンスで新しいプレーヤーを生成またはインスタンス化するときに使用できる事前 fab が作成されました。

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> 注: Prefabs フォルダーを階層から削除する前に、game オブジェクトが正常にコピーされていることを確認してください。

10. 手順 3. の指示に従って、階層内に新しいオブジェクトを作成し、SharedPlayground グラウンドという名前を指定します。 次に、[コンポーネントの追加] をクリックし、[汎用ネットワークマネージャー] を検索して、それをクリックして汎用ネットワークマネージャーコンポーネントを追加します。 オブジェクトの位置を x = 0、y = 0、z = 0 に変更します。

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>結論

上記のすべての手順が完了し、ビルドプロセスも完了したら、[再生] ボタンをクリックして HoloLens 2 に接続します。 頭を移動すると球が動いていることがわかります。 これは、Unity プロジェクトに参加するすべてのユーザーに表示されます。

[次のレッスン:4。オブジェクトの動きの複数のユーザーとの共有](mrlearning-sharing(photon)-ch4.md)

