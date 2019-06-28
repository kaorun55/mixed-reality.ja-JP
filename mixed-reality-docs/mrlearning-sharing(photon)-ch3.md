---
title: ラーニング モジュールを共有 HoloLens 2 を MR
description: このコースでは、HoloLens 2 アプリケーション内でのマルチ ユーザー共有機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 33f265c6333f12f7ec73ecb0c1e5730b168d4bde
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415913"
---
# <a name="connecting-multiple-users"></a>**複数のユーザーを接続します。** 

このレッスンでは、ライブの共有エクスペリエンスの一部として複数のユーザーを接続する方法を学びます。 このレッスンの目的は、することが、複数のデバイスでアプリケーションを開き、「アバター」表現 (アバターの球体をによって表される) を結合する各ユーザーの表示 

目標:

- アプリケーション内でだじゃれを構成します。
- プレーヤーを構成します。
- 複数のユーザー エクスペリエンスの共有に接続する方法について説明します

### <a name="instructions"></a>手順

1. 資産 > リソース > Prefabs フォルダー プロジェクト パネル、ドラッグ アンド ドロップ"NetworkLobby"で、階層にプレハブの次の図に示すようにします。


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. Prefab"NetworkLobby"を展開すると、"NetworkRoom"と呼ばれる子オブジェクトが表示されます。 選択されていると、インスペクター パネルに移動し、「コンポーネントを追加します」をクリックしてください "PhotonView"を検索し、コンポーネントを追加します。

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. 階層内の新しい空のゲーム オブジェクトの作成 (階層内を右クリックし、コンテキスト メニューから「空」を選択します)。 位置 x に設定されていることを確認 = 0、y = 0、z = 0 およびオブジェクトの名前を"PhotonUser"。

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. 「コンポーネントの追加」ボタンをクリックしてと"汎用 Net Sync"を入力し、汎用の差分同期クラスを選択します。 クラスが表示されたらは、有効にする「ユーザー」のチェック ボックスをクリックします。 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. もう一度「コンポーネントの追加」をクリックし、入力"Photon View"し、ドロップダウン リストで表示される Photon ビュー クラスを選択します。

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. 今すぐジェネリック Net 同期クラスの場合にファイルのアイコンをクリックし、ドラッグし、Photon ビューの「コンポーネントの監視」フィールドにドロップします。 ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. 次に、共有のエクスペリエンスを結合する各ユーザーを表す球体を作成します。 作成した"PhotonUser"オブジェクトを右クリックし、「3D オブジェクト」に移動し、「球」をクリックしてください これにより、PhotonUser オブジェクトの子として、球体のゲーム オブジェクトが作成されます。

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. X に球をスケール = 0.06、y = 0.06、ad z 0.06 を = です。

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. [プロジェクト] パネルで「プレハブ」フォルダーには、"PhotonUser"ゲーム オブジェクトをドラッグします。 次に、シーンから削除します。 今すぐ生成または共有のエクスペリエンスで新しいプレーヤーをインスタンス化するときに使用されるプレハブを作成しました。

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> 注: は、ゲーム オブジェクトが、階層から削除する前に正常に"prefabs"フォルダーにコピーされたいることを確認します。

10. (手順 3 のような手順を使用)、階層内の新しいオブジェクトを作成し、"SharedPlayground"という名前を付けます 「コンポーネントの追加」と「一般的なネットワーク マネージャー」の検索 をクリックし、クリックして、汎用ネットワーク マネージャー コンポーネントを追加します。 オブジェクトの位置を x に変更 = 0、y = 0、および z = 0。

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>結論

上記すべての手順が完了すると、再生ボタンをクリックし、HoloLens 2 を接続するときに、ビルド プロセスが完了すると頭を移動すると、移動、球が表示されます。 これは、Unity プロジェクトを結合するすべてのユーザーに対して表示されます。

[次のレッスン:Sharing(Photon) レッスン 4](mrlearning-sharing(photon)-ch4.md)

