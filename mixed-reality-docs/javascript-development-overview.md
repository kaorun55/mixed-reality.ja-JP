---
title: JavaScript Mixed Reality 開発の概要
description: Web、モバイル、および windows のイマーシブヘッドセットの JavaScript を使用した Mixed Reality 開発の概要。
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR、WinMR、WebAR、WebVR、WindowsMixedReality、HoloLens、windows mixed reality、web vr、web xr、web mr、web ar、360、360 video、360ビデオ、360 photo、360 photos、360コンテンツ、イマーシブ web、イマーシブ-web、IW、immersiveweb
ms.openlocfilehash: 5756af9f48f4bb25477e75fb1f7c09e7239bdab9
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278483"
---
# <a name="mixed-reality-development-with-javascript-overview"></a>JavaScript を使用した Mixed Reality 開発の概要

## <a name="mixed-reality-applications-on-the-web"></a>Web 上の Mixed Reality アプリケーション

[WebXR Device api](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)と [Deprecated webvr api] ([WebXR の概要](webxr-overview.md)) を使用して、web で Mixed Reality 機能を使用できます。 WebXR の全機能をサポートしていないブラウザーでは、 [WebXR Polyfills](https://github.com/immersive-web/webxr-polyfill)を web サイトに追加できます。

## <a name="what-is-webxr-polyfill"></a>WebXR ポリフィルとは

WebXR Device API の JavaScript 実装と WebXR ゲームパッドモジュール。 このポリフィルを使用すると、開発者は最新の仕様に対する書き込みを行うことができ、WebVR 1.1 仕様を実装するブラウザーで実行する場合はサポートが提供され、WebVR/WebXR をまったくサポートしないモバイルデバイスではサポートが提供されます。

## <a name="javascript-libraries-to-build-mixed-reality-applications-on-the-web"></a>Web 上に Mixed Reality アプリケーションを構築するための JavaScript ライブラリ

## <a name="babylonjs"></a>Babylon

Babylon は、3D コンテンツとイマーシブアプリケーションを簡単に開発できるようにする JavaScript 3D エンジンです。 イマーシブアプリケーションの使用を開始する前に、Babylon 開発の基本について学習することをお勧めします。

[「作業の開始」セクション](https://doc.babylonjs.com/)で、Babylon を使用して mixed reality アプリケーションを構築する方法について説明します。 [Babylon プレイグラウンド](https://doc.babylonjs.com/examples/)を使用して、3d の例とそのソースコードを再生します。 詳細については、ドキュメントの[「WebXR」セクションを参照](https://doc.babylonjs.com/how_to/introduction_to_webxr)してください。 

## <a name="a-frame"></a>A-フレーム

-Frame は、web で仮想現実を開始するための宣言型の JavaScript フレームワークです。 詳細について[は、A フレームのドキュメント](https://aframe.io/)を参照してください。

## <a name="threejs"></a>3 .js

3つの .js は、イマーシブエクスペリエンスを作成するための一般的な3D ライブラリです。 [3. .js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene)の詳細については、ドキュメントページと[例](https://threejs.org/examples/#webgl_animation_cloth)を参照してください。

## <a name="webgl"></a>WebGL

WebGL Api を使用して、WebXR デバイス Api に直接アクセスできます。 WebGL (Web グラフィックスライブラリ) は、プラグインを使用せずに、互換性のある web ブラウザー内に高パフォーマンスの対話型3D グラフィックスおよび2D グラフィックスをレンダリングするための JavaScript API です。 [Webgl api](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)の詳細については、こちらを参照してください。

## <a name="mixed-reality-native-mobile-applications-using-javascript"></a>JavaScript を使用した Mixed Reality ネイティブモバイルアプリケーション

JavaScript ライブラリが少ないので、mixed reality エクスペリエンスを一度記述し、web および Windows Mixed Reality ヘッドセット、Android、iOS デバイスなどのネイティブプラットフォームにデプロイすることができます。

## <a name="babylon-native"></a>Babylon ネイティブ

[Babylon ネイティブ](https://www.babylonjs.com/native/)プラットフォームを使用すると、だれでも Babylon コードを取得し、それを使用してネイティブアプリケーションを構築し、ネイティブテクノロジの機能をロック解除することができます。 [Github で Babylon native](https://github.com/BabylonJS/BabylonNative)をダウンロードし、 [Babylon のブログ](https://medium.com/@babylonjs/babylon-native-821f1694fffc)で詳細を読むことができます。

## <a name="react-native"></a>React Native

[ネイティブ](https://reactnative.dev/)への対応は、開発者が JavaScript を使用してビルドし、複数のプラットフォームに配置できる、もう1つのオープンソースライブラリです。 [Github でのネイティブな応答](https://github.com/facebook/react-native)をダウンロードし、その詳細については、[ネイティブブログの応答](https://reactnative.dev/blog/)に関するページを参照してください。

## <a name="see-also"></a>参照

* [WebXR の概要](webxr-overview.md)
* [WebXR Device API 仕様](https://immersive-web.github.io/webxr/)
* [WebXR Device API のドキュメント](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Immersiveweb](https://immersiveweb.dev/)
* [WebXR のサンプル](https://immersive-web.github.io/webxr-samples/)
* [Babylon を使用して WebXR エクスペリエンスを作成する](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [Windows Mixed Reality と新しい Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [イマーシブ Web W3C Github](https://github.com/immersive-web)
* [WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* [ゲームパッド API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)と[ゲームパッド拡張機能](https://w3c.github.io/gamepad/extensions.html)
* [WebVR の概要](webvr-overview.md)
