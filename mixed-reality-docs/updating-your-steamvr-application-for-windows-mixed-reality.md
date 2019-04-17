---
title: Windows Mixed Reality を SteamVR アプリケーションを更新しています
description: Windows Mixed Reality ヘッドセットとの互換性を最大化する SteamVR アプリケーションを更新するためのベスト プラクティス。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR、互換性
ms.openlocfilehash: db21651df8e586edf500f0d05def4b1ea5474284
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597854"
---
# <a name="updating-your-steamvr-application-for-windows-mixed-reality"></a>Windows Mixed Reality を SteamVR アプリケーションを更新しています

開発者がテストし、Windows Mixed Reality ヘッドセットで実行するには、その SteamVR エクスペリエンスを最適化することをお勧めします。 このドキュメントでは、開発者が Windows Mixed Reality でエクスペリエンスを優れた実行することを確認すること、一般的な機能強化について説明します。

## <a name="initial-setup-instructions"></a>初期セットアップ手順

最初のフォローを確認して、ゲームや Windows Mixed Reality でアプリをテストを開始する、[ファースト ステップ ガイドです。](http://aka.ms/WindowsMixedRealitySteamVR)

## <a name="controller-models"></a>コント ローラー モデル
1. 場合は、アプリは、コント ローラー モデルを表示します。
    * 使用して、 [Windows Mixed Reality 運動コント ローラー モデル](motion-controllers.md#rendering-the-motion-controller-model)
    * (例: 変換コンポーネント パーツを使用して IVRRenderModel::GetComponentState ローカルを取得するには ポインターの姿勢)
2. 処理の概念のエクスペリエンスは、Api コント ローラーを区別するために、入力からヒントを取得する必要があります[(Unity など)](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)

## <a name="controls"></a>コントロール

設計または調整するときに、コントロールのレイアウトに注意してください、次の予約済みのコマンド セットしてください。
1. をクリックして、**左と右アナログ スティック**に予約されている、**蒸気のダッシュ ボード**します。
2. **Windows ボタン**Windows Mixed reality ホーム ユーザーは常に返します。

Thumb スティックを既定の teleportation と一致するベース可能であれば、 [Windows Mixed Reality ホーム](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)teleportation 動作

## <a name="tooltips-and-ui"></a>ツールヒントと UI

多くの VR ゲームでは、アニメーション コント ローラー ツールチップとオーバーレイ、ゲームまたはアプリの最も重要なコマンドをユーザーに教えるの活用します。 Windows Mixed reality 用のアプリケーションのチューニング時に、Windows のコント ローラー モデルにマップするツールヒントを確認するには、エクスペリエンスのこの部分のレビューをお勧めします。

さらがある場合は、コント ローラーのイメージを表示するエクスペリエンスで任意のポイント Windows Mixed Reality アニメーション コント ローラーを使用して更新されたイメージを提供することを確認してください。

## <a name="haptics"></a>Haptics

以降では、 [Windows 10 April 2018 Update](release-notes-april-2018.md)、Windows Mixed Reality を SteamVR のエクスペリエンスのために haptics はサポートされています。 SteamVR アプリやゲーム haptics のサポートが既に含まれている場合も動作するはずようになりました (追加作業がない) で[Windows Mixed Reality モーションのコント ローラー](motion-controllers.md)します。

Windows Mixed Reality モーションのコント ローラーは、いくつか他 SteamVR モーションのコント ローラー、若干異なるが予想以上のユーザー エクスペリエンスにつながる可能性のある線形アクチュエータではなく、標準 haptics モーターを使用します。 そのため、テストとチューニングの Windows Mixed Reality モーションのコント ローラーで haptics の設計お勧めします。 たとえば、ハプティクス パルスの短いことがあります (5 ~ 10 ミリ秒) は Windows Mixed Reality モーションのコント ローラーに小さくします。 顕著なパルスを生成するには、もう一度電源が指示される前に、長い「クリック」(40 70ms) を迅速に作成する自動車の多くの時間の送信を試してください。

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>Windows Mixed Reality スタート メニューから SteamVR アプリの起動

ストリームによって配布、VR エクスペリエンスのしました[SteamVR ベータ版の Windows Mixed Reality を更新](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800)最新と共に[Windows Insider](https://insider.windows.com) RS5 フライト SteamVR タイトルに表示されるように、"すべてのアプリ] で Windows 混合実際には [スタート] メニューが自動的に一覧表示します。 ソフトウェア バージョンがインストールされているこれらでは、お客様は Windows Mixed Reality ホーム内から直接 SteamVR タイトルをヘッドセットを削除せず今すぐ起動できます。

## <a name="windows-mixed-reality-logo"></a>Windows Mixed Reality ロゴ

Windows Mixed Reality サポートをタイトルを表示するには、移動、アプリのランディング ページに「ストア ページの編集」リンクに"基本情報 タブをクリックし、「仮想現実です」まで下へスクロール "非表示にする Windows Mixed Reality"をオフにし、ストアに発行します。

## <a name="bugs-and-feedback"></a>バグやフィードバック

Windows Mixed Reality SteamVR エクスペリエンスを向上する際、お客様のフィードバックは貴重ではありません。 すべてのフィードバックと使用してバグを送信してください、 [Windows フィードバック Hub](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback)します。 いくつか紹介[SteamVR フィードバックを参考になったできるだけさせる方法に関するヒント](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)します。

質問またはコメントを共有する場合もアドレスで、[蒸気フォーラム](http://steamcommunity.com/app/719950/discussions/)します。

## <a name="faqs-and-troubleshooting"></a>FAQ とトラブルシューティング

設定するか、エクスペリエンスの再生の一般的な問題が発生した場合[をチェック アウト、最新のトラブルシューティング手順](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)します。

## <a name="see-also"></a>関連項目
* [ツールをインストールします。](install-the-tools.md)
* [ヘッドセットとアニメーション コント ローラーのドライバーの履歴](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Windows Mixed Reality 最小 PC ハードウェアの互換性ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
