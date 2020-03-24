---
title: マルチユーザー機能のチュートリアル - 3. 複数のユーザーの接続
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法を学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: cbe0d8d2db6c34ba262fe9c946b68366ed3dbb93
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031228"
---
# <a name="3-connecting-multiple-users"></a>3.複数のユーザーの接続

このレッスンでは、ライブ共有エクスペリエンスの一部として複数のユーザーを接続する方法を学習します。 このレッスンを終了すると、複数のデバイスでアプリケーションを開き、球体で表される、参加する各ユーザーのアバターを表示できるようになります。

## <a name="objectives"></a>目標

* アプリケーション内で PUN を構成する
* プレーヤーを構成する
* 共有エクスペリエンスで複数のユーザーを接続する方法を学習する

## <a name="instructions"></a>手順

1. 次の図に示すように、[Project]\(プロジェクト\) パネルの [Assets]\(アセット\) -> [Resources]\(リソース\) -> [Prefabs] フォルダーで、NetworkLobby プレハブを階層にドラッグ アンド ドロップします。

    ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. NetworkLobby を展開すると、NetworkRoom という子オブジェクトが表示されます。 NetworkRoom を選択した状態で、[Inspector]\(インスペクター\) パネルに移動し、[Add Component]\(コンポーネントの追加\) をクリックします。 PhotonView を検索し、このコンポーネントを追加します。

    ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. 階層内に新しい空のゲーム オブジェクトを作成します。 階層内を右クリックし、コンテキスト メニューから [Empty]\(空\) を選択します。 位置が x =0、y=0、z=0 に設定されていることを確認し、オブジェクトに PhotonUser という名前を付けます。

    ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. [Add Component]\(コンポーネントの追加\) をクリックし、「Generic Net Sync」と入力します。Generic Net Sync クラスを選択します。 クラスが表示されたら、[User]\(ユーザー\) チェック ボックスをクリックしてオンにします。

    ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. [Add Component]\(コンポーネントの追加\) をもう一度クリックし、「Photon View」と入力します。 ドロップダウン リストに表示される Photon View クラスを選択します。

    ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. Generic Net Sync クラスの [File]\(ファイル\) アイコンをクリックします。 それを Photon View の[Observed Components]\(観測されたコンポーネント\) フィールドにドラッグ アンド ドロップします。

    ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png)

7. 次に、共有エクスペリエンスに参加する各ユーザーを表す球体を作成します。 先ほど作成した PhotonUser オブジェクトを右クリックし、[3D Object]\(3D オブジェクト\) まで下にスクロールして、[Sphere]\(球体\) をクリックします。 これにより、PhotonUser オブジェクトの子として球体ゲーム オブジェクトが作成されます。

    ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. 球体を x=0.06、y=0.06、z=0.06 にスケール ダウンします。

    ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. PhotonUser ゲーム オブジェクトを [Project]\(プロジェクト\) パネルの [Prefabs] フォルダーにドラッグし、シーンから削除します。 これで、共有エクスペリエンスで新しいプレーヤーを生成またはインスタンス化するときに使用できるプレハブが作成されました。

    ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

    >[!NOTE]
    >階層から削除する前に、ゲーム オブジェクトが [Prefabs] フォルダーに正常にコピーされていることを確認します。

10. 手順 3 の指示に従って階層内に新しいオブジェクトを作成し、SharedPlayground という名前を付けます。 次に、[Add Component]\(コンポーネントの追加\) をクリックし、Generic Network Manager を検索します。  もう一度クリックして、Generic Network Manager コンポーネントを追加します。 オブジェクトの位置を x=0、y=0、z=0 に変更します。

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)

## <a name="congratulations"></a>結論

上記のすべての手順が完了し、ビルド プロセスも完了したら、[Play]\(プレイ\) ボタンを押し、HoloLens 2 を接続します。 頭を動かすと球体が動きまわるのを確認できます。 これは、Unity プロジェクトに参加しているすべてのユーザーに対して表示されます。

[次のレッスン:4.オブジェクトの動きの複数のユーザーとの共有](mrlearning-sharing(photon)-ch4.md)
