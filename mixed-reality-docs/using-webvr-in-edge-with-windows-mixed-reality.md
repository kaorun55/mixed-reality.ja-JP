---
title: Windows Mixed Reality WebVR を Microsoft Edge でを使用しました。
description: 使用して、Windows Mixed Reality で WebVR 用の開発の概要
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: WebVR、WebXR、WinMR、WebAR、vr を web、web xr、mr を web、web ar、360、360 のビデオ、360 ビデオ、360 の写真、360 の写真、360 コンテンツ、没入型の web、immersiveweb、インフォメーション ワーカー
ms.openlocfilehash: fab17f4dcecc34d8f1ca4836dce6de90522899cd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604638"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a>Windows Mixed Reality WebVR を Microsoft Edge でを使用しました。

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a>Windows Mixed reality を WebVR コンテンツ イマーシブ ヘッドセットを作成します。

WebVR 1.1 は Windows 10 Fall Creators Update 以降の Microsoft Edge で使用できます。 今すぐ開発者は、この API を使用して、web で没入型の VR エクスペリエンスを作成することができます。

WebVR API では、ッドマウントにステレオ WebGL シーンをレンダリングするために使用できるページにッドマウント姿勢のデータを提供します。 API のサポートの詳細についてで使用できる、 [Microsoft Edge プラットフォームの状態ページ](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/)します。 WebVR API サーフェス領域は、Microsoft Edge 内で常に存在します。 ただし、シミュレーターがオンにされましたかヘッドセット接続されている場合、getVRDisplays() への呼び出しはヘッドセットを返すのみです。

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a>Windows Mixed Reality イマーシブ ヘッドセットで WebVR コンテンツを表示

イマーシブ ヘッドセット WebVR コンテンツにアクセスするための手順が記載されて、[愛好家のガイド](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr)します。

## <a name="see-also"></a>関連項目
* [WebVR 情報](http://webvr.info)
* [WebVR 仕様](https://w3c.github.io/webvr/)
* [WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)
* [WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* [Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)と[ゲームパッドの拡張機能](https://w3c.github.io/gamepad/extensions.html)
* [WebGL でコンテキストが失われる処理](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](http://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [Babylon.js を使用して WebVR を有効にするには](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)

