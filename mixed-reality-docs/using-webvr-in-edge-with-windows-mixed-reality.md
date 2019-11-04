---
title: Microsoft Edge での WebVR と Windows Mixed Reality の使用
description: Windows Mixed Reality での WebVR の使用と開発の概要
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: WebVR, WebXR, WinMR, WebAR, web vr, web xr, web mr, web ar, 360, 360 ビデオ, 360 ビデオ, 360 写真, 360 写真, 360 コンテンツ, イマーシブ web, immersiveweb, IW
ms.openlocfilehash: 87805d2c40e9e63cdf3e432189b9deb7d575a380
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437203"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a>Microsoft Edge での WebVR と Windows Mixed Reality の使用

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a>Windows Mixed reality イマーシブヘッドセットの WebVR コンテンツの作成

WebVR 1.1 は、Windows 10 の秋の作成者の更新プログラム以降、Microsoft Edge で利用できます。 開発者は、この API を使用して、web 上でイマーシブ VR エクスペリエンスを作成できるようになりました。

WebVR API は、HMD のデータをページに提供します。これを使用すると、ステレオ Webvr シーンを HMD に戻すことができます。 API サポートの詳細については、 [Microsoft Edge プラットフォームの状態](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/)に関するページを参照してください。 WebVR API のセキュリティ領域は、Microsoft Edge 内で常に存在します。 ただし、getVRDisplays () を呼び出すと、ヘッドセットが電源に接続されているか、シミュレーターが有効になっている場合にのみ、ヘッドセットが返されます。

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a>Windows Mixed Reality イマーシブヘッドセットの WebVR コンテンツの表示

イマーシブヘッドセットの WebVR コンテンツにアクセスする手順については、「[ユーザーズガイド](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr)」を参照してください。

## <a name="see-also"></a>参照
* [WebVR 情報](https://webvr.info)
* [WebVR 仕様](https://w3c.github.io/webvr/)
* [WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)
* [WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* [ゲームパッド API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)と[ゲームパッド拡張機能](https://w3c.github.io/gamepad/extensions.html)
* [WebGL での失われたコンテキストの処理](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock ロック](https://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [Babylon を使用して WebVR を有効にする](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)

