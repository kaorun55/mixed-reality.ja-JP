---
title: Unity の入力移植ガイド
description: Unity で Windows Mixed Reality の入力を処理する方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 入力、unity、移植
ms.openlocfilehash: 20e8efa09d20b0a9eaa246015d9c185884f9c216
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515498"
---
# <a name="input-porting-guide-for-unity"></a>Unity の入力移植ガイド

2つの方法のいずれかを使用して、入力ロジックを Windows Mixed Reality に移植できます。 Unity の一般的な入力です。複数のプラットフォームにまたがっている GetButton/GetAxis Api、または Windows 固有の XR です。付い.モーションコントローラーと HoloLens ハンド専用の豊富なデータを提供する入力 Api。

## <a name="general-inputgetbuttongetaxis-apis"></a>一般的な入力。 GetButton/GetAxis Api

Unity では、現在、一般的な入力である GetButton/GetAxis Api を使用して[、OCULUS sdk](https://docs.unity3d.com/Manual/OculusControllers.html)と[openvr sdk](https://docs.unity3d.com/Manual/OpenVRControllers.html)の入力を公開しています。 アプリが既にこれらの Api を入力に使用している場合は、これが Windows Mixed Reality でのモーションコントローラーをサポートするための最も簡単なパスです。入力マネージャーでボタンと軸を再マップするだけで済みます。

詳細については、「 [unity のボタン/軸マッピングテーブル](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)」と「[共通 unity api の概要](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)」を参照してください。

## <a name="windows-specific-xrwsainput-apis"></a>Windows 固有の XR。付い.入力 Api

アプリが各プラットフォームのカスタム入力ロジックを既に作成している場合は、 **XR**名前空間の下で Windows 固有の空間入力 api を使用することを選択できます。 これにより、位置の精度やソースの種類などの追加情報にアクセスして、HoloLens で両手とコントローラーを区別できるようになります。

詳細については、「 [UnityEngine. XR api の概要](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)」を参照してください。

## <a name="grip-pose-vs-pointing-pose"></a>グリップポーズとポインティングポーズ

Windows Mixed Reality では、さまざまなフォームファクターでのモーションコントローラーがサポートされています。各コントローラーの設計は、ユーザーの手の形と、アプリがレンダリングするときに使用する自然な "進む" 方向との間の関係で異なります。コントロール.

これらのコントローラーをより適切に表現するために、相互作用ソースごとに調査できる2種類の方法があります。

* **グリップ**は、HoloLens によって検出されたハンドの位置を表します。または、運動コントローラーを持つパームです。
    * イマーシブヘッドセットでは、この方法を使用して、**ユーザーの手**や、剣や銃などの**ユーザーの手に保持**されているオブジェクトをレンダリングすることをお勧めします。
    * **グリップの位置**:コントローラーを自然に保持すると、パーム重心が調整され、グリップ内の位置を中心として左右に調整されます。
    * **グリップの向きの右軸**:ハンドを完全に開いて、5つの指が平らになるようにするには、(左側のパームから、右のパームから後方に)、パームに通常ある光線を使用します。
    * **グリップの向きの前方軸**:(コントローラーを保持している場合と同様に) 手を部分的に閉じた場合、非表示の指で形成されたチューブによって "前方" を指します。
    * **グリップの方向の上位軸**:右および順方向の定義によって暗黙的に示される上位軸。
    * このグリップには、Unity のクロスベンダ入力 API (XR) を使用してアクセスでき **[ます。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/Rotation**) または Windows 固有の API (**TryGetPosition/rotation**) を使用して、グリップを要求します。
* **ポインター**は、前方を指し示すコントローラーの先端を表します。
    * この方法は、コントローラーモデル自体をレンダリングするときに**UI をポイント**するときに raycast するために使用することをお勧めします。
    * 現時点では、ポインターのポーズは、Windows 固有の API (**Sourcestate/Rotation**) を介してのみ使用でき、ポインターのポーズを要求します。

これらの発生座標はすべて Unity のワールド座標で表現されます。

## <a name="see-also"></a>関連項目
* [モーション コントローラー](motion-controllers.md)
* [Unity でのジェスチャとモーション コントローラー](gestures-and-motion-controllers-in-unity.md)
* [UnityEngine. XR](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR 追跡](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [移植のガイド](porting-guides.md)
