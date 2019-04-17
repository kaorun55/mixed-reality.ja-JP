---
title: Unity のガイドの移植の入力
description: Unity での Windows Mixed Reality の入力を処理する方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 入力、unity、移植
ms.openlocfilehash: 20e8efa09d20b0a9eaa246015d9c185884f9c216
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602791"
---
# <a name="input-porting-guide-for-unity"></a>Unity のガイドの移植の入力

Windows Mixed Reality を使用して、複数のプラットフォーム全体にわたる Unity の一般的な Input.GetButton/GetAxis Api または Windows 固有 XR の 2 つのアプローチの 1 つに、入力のロジックを移植することができます。WSA します。アニメーション コント ローラーと HoloLens 手を具体的には豊富なデータを提供する Api を入力します。

## <a name="general-inputgetbuttongetaxis-apis"></a>[全般] Input.GetButton/GetAxis Api

入力を公開する、その全般 Input.GetButton/Input.GetAxis Api を現在使用して unity [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html)と[OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)します。 Windows Mixed Reality でモーションのコント ローラーをサポートするための最も簡単なパスは既に、アプリは、これらの Api を使用して、入力は場合、: ボタンと Input Manager での軸を再マップする必要があるだけです。

詳細については、次を参照してください。、 [Unity ボタン/軸マッピング テーブル](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)と[一般的な Unity Api の概要](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)します。

## <a name="windows-specific-xrwsainput-apis"></a>Windows に固有のダンプします。WSA します。入力 Api

アプリが既に各プラットフォーム用のカスタム入力ロジックをビルドする場合は、Windows に固有の空間入力 Api を使用することもできます、 **UnityEngine.XR.WSA.Input**名前空間。 位置の精度などの追加情報または HoloLens の手と離れているコント ローラーを指示することができます、ソースの種類にアクセスできます。

詳細については、次を参照してください。、 [UnityEngine.XR.WSA.Input Api の概要](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)します。

## <a name="grip-pose-vs-pointing-pose"></a>グリップの姿勢ポインティング ポーズとの比較

Windows Mixed Reality は、さまざまなフォーム ファクターでモーションのコント ローラーをサポートしている、各コント ローラーの設計と、ユーザーの手の形の位置とそのアプリの方向を「転送」自然の間の関係の違いポイントを表示するときに使用する必要があります、コント ローラー。

これらのコント ローラーをより適切に表すには、各操作のソースを調査することができますが発生 2 つの種類があります。

* **グリップ姿勢**、片手で行うことによって、HoloLens、検出された手の形のまたはアニメーション コント ローラーを保持している片手で行うことのいずれかの場所を表します。
    * イマーシブ ヘッドセットは、この姿勢が最適な表示に使用**ユーザーの手**または**オブジェクトは、ユーザーの手の形で保持されている**剣やガンなど。
    * **位置を握って**:Palm 重心当然ながら、コント ローラーを保持しているときに、左または右中央にグリップ内の位置を調整します。
    * **向きの適切な軸を握って**:5 本の指フラットな姿勢を形成する完全に開くと、射線は、palm に通常 (順方向から左 palm、適切な palm から旧バージョンとの)
    * **向きの順方向軸を握って**:部分的に (場合と同様、コント ローラーを保持している) の手の閉じるときに、"forward"チューブを通じて非 thumb 指によって形成されるポイントの半径。
    * **軸の向きを握って**:右と前方参照の定義が含まれるアップ軸。
    * グリップの姿勢をベンダー間入力のいずれかの Unity の API を通じてアクセスできます (**[XR します。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)します。GetLocalPosition/Rotation**) または Windows 固有 API (**sourceState.sourcePose.TryGetPosition/Rotation**、グリップ姿勢を要求する)。
* **ポインター姿勢**、フォワード指し示すコント ローラーのヒントを表します。
    * この姿勢が raycast に適してとき**UI をポイント**コント ローラー モデル自体をレンダリングする場合。
    * 現時点では、ポインターの姿勢は、Windows 固有 API を通じてしか利用できません (**sourceState.sourcePose.TryGetPosition/Rotation**ポインターの姿勢を要求する)。

これらの姿勢座標がすべて Unity ワールド座標で表されます。

## <a name="see-also"></a>関連項目
* [アニメーション コント ローラー](motion-controllers.md)
* [ジェスチャと Unity のアニメーション コント ローラー](gestures-and-motion-controllers-in-unity.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [移植のガイド](porting-guides.md)
