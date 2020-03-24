---
title: マルチユーザー機能のチュートリアル - 5. Azure Spatial Anchors の共有エクスペリエンスへの統合
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法を学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 7fb8cd03b2f3739037dee38786493bfd9012f6ce
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031685"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a>5.Azure Spatial Anchors の共有エクスペリエンスへの統合

このレッスンでは、Azure Spatial Anchors (ASA) を共有エクスペリエンスに統合する方法を学習します。 ASA を使用すると、併置された複数のデバイスは、その物理的環境が仮想エクスペリエンスを支えてすべての参加者が同じ物理的な場所でオブジェクトを見るようにする場合、共通参照を持つことができます。

## <a name="objectives"></a>目標

* ASA をマルチデバイス配置の共有エクスペリエンスに統合する。
* ASA がローカル共有エクスペリエンスのコンテキストでどのように機能するかについての基本を学ぶ。

## <a name="instructions"></a>手順

1. MixedRealityPlayspace 親オブジェクトの下にある TableAnchor プレハブを選択し、削除します。

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. [Project]\(プロジェクト\) ビューで、[Assets]\(アセット\) -> [Resources]\(リソース\) -> [Prefabs]\(プレハブ\) の順に移動し、TableAnchor プレハブを SharedPlayground オブジェクトの上にドラッグして子にします。

3. MixedRealityPlayspace 親オブジェクト、TableAnchor オブジェクトを展開し、Buttons オブジェクトも展開します。

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. 次に、階層内で [ShareAzureAnchorButton] を選択し、[Inspector]\(インスペクター\) パネルに注目します。 下にスクロールして、次の図に示されているドロップダウン メニューまで移動し、[AnchorModuleScript] を選択して、[ShareAnchorNetwork()] をクリックします。

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. [GetAzureAnchorButton] (手順 4 を参照) を選択し、再び [Inspector]\(インスペクター\) パネルに注目します。 下にスクロールして、次の図に示されているドロップダウン メニューまで移動し、[AnchorModuleScript] を選択して、[ShareAnchorNetwork()] をクリックし、保存します。

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. 手順 4 を繰り返して、StartAzureSession () 関数を StartAzureSessionButton にフックします。

7. 手順 4 を繰り返して、CreateAzureAnchor () 関数を CreateAzureAnchorButton にフックし、TableAnchor オブジェクトが関数のパラメーター "Game Object" フィールドに割り当てられていることを確認します。

8. 「[シーンを Azure リソースに接続する](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource)」の手順に従って、Azure Spatial Anchors サービスの資格情報を追加します。

9. 共有モジュールをテストするには、[Start Azure ASA Session]\(Azure ASA セッションの開始\) ボタンをクリックして Azure Spatial Anchors セッションを開始し、次に、[Create Azure Anchor]\(Azure アンカーの作成\) ボタンをクリックして Azure アンカーを作成します。 Azure アンカーが作成されるまで待ちます。 Azure アンカーが作成されたら、[Share Azure Anchor]\(Azure アンカーの共有\) ボタンをクリックして、作成した Azure アンカーを HoloLens から共有します。

10. 別の HoloLens で共有 Azure アンカーを受け取るには、[Start Azure ASA Session]\(Azure ASA セッションの開始\) をクリックして、現在の ASA セッションを開始します。

11. [Get Azure Anchor]\(Azure アンカーの取得\) ボタンをクリックして、もう一方の HoloLens から共有 Azure アンカーを取得します。

## <a name="congratulations"></a>結論

このレッスンでは、Azure の強力で新しい Spatial Anchors を統合して、併置されたデバイスを共有エクスペリエンスに配置する方法を学習しました。 これにより、共有モジュールも完了しました。 新しい Photon アカウントを設定し、Photon と PUN を新しい Unity アプリケーションに統合し、アバターと共有オブジェクトを構成し、最後に ASA を使用して複数の参加者を配置する方法を学習しました。
