---
title: ラーニング モジュールを共有 HoloLens 2 を MR
description: このコースでは、HoloLens 2 アプリケーション内でのマルチ ユーザー共有機能を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.openlocfilehash: 4625acfcb3353e9537961a444012452139705359
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465213"
---
# <a name="connecting-multiple-users"></a>**複数のユーザーを接続します。** 

このレッスンでは、ライブの共有エクスペリエンスの一部として複数のユーザーを接続する方法について説明します。 このレッスンの目的は、複数のデバイスでアプリケーションを開き、球体の場合、結合する人の表現によって表される、アバターを表示するようになります。 

目標:

- アプリケーション内でだじゃれを構成します。
- プレーヤーを構成します。
- 複数のユーザー エクスペリエンスの共有に接続する方法について説明します

### <a name="instructions"></a>手順

1. 資産-> リソース メニューの プロジェクト パネルで Prefabs フォルダーにドラッグ アンド次の図に示すように、階層で NetworkLobby プレハブを削除します。


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. NetworkLobby を展開すると、NetworkRoom と呼ばれる子オブジェクトを確認します。 NetworkRoom が選択されている、Inspector パネルに移動し、コンポーネントの追加 をクリックします。 PhotonView を検索し、コンポーネントを追加します。

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. 階層内の新しい空のゲーム オブジェクトを作成します。 階層内を右クリックし、コンテキスト メニューから空を選択します。 位置 x に設定されていることを確認 = 0、y = 0、z = 0 および PhotonUser、オブジェクトの名前を付けます。

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. [コンポーネントの追加] をクリックし、汎用の差分同期を入力します。ジェネリックの差分同期クラスを選択します。 クラスが表示されたら、有効にするには、ユーザー チェック ボックスをクリックします。 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. ここでも、コンポーネントの追加 をクリックし、Photon ビューを入力します。 ドロップダウン リストで表示される Photon ビュー クラスを選択します。

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. ジェネリックの差分同期クラスのファイルのアイコンをクリックします。 ドラッグ アンド ドロップ Photon ビューのコンポーネントの検出フィールド。 ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. 次に、共有のエクスペリエンスを結合する各ユーザーを表す球体を作成します。 作成した PhotonUser オブジェクトと scrolldown を右クリックして"3 D オブジェクトをクリックして、球。 これにより、PhotonUser オブジェクトの子として、球体のゲーム オブジェクトが作成されます。

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. X に球をスケール = 0.06、y = 0.06、ad z 0.06 を = です。

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. プロジェクト パネルで、Prefabs フォルダーに PhotonUser ゲーム オブジェクトをドラッグし、シーンから削除します。 今すぐ生成または共有のエクスペリエンスで新しいプレーヤーをインスタンス化するときに使用できるプレハブを作成しました。

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> 注: は、ゲーム オブジェクトが、階層から削除する前に正常に Prefabs フォルダーにコピーされたいることを確認します。

10. 手順 3 での手順に従って、階層内の新しいオブジェクトを作成し、SharedPlayground という名前を付けます。 [コンポーネントの追加] をクリックし汎用ネットワーク マネージャーを検索し、クリックして、汎用ネットワーク マネージャー コンポーネントを追加します。 オブジェクトの位置を x に変更 = 0、y = 0、および z = 0。

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>結論

上記の手順が完了すると、ビルド プロセスが完了することも、後は、再生ボタンをクリックし、HoloLens 2 を接続します。 頭の中を移動すると、移動、球が表示されます。 これは、Unity プロジェクトを結合するすべてのユーザーに対して表示されます。

[次のレッスン:Sharing(Photon) レッスン 4](mrlearning-sharing(photon)-ch4.md)

