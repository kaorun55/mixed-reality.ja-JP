---
title: 自宅での 3D モデルの配置を有効にします。
description: Windows Mixed Reality ホームで、web サイトまたはアプリケーションからの 3D モデルを配置する方法
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D、モデル、自宅内の場所、場所、world、モデリング、複合現実のホーム、web、アプリ
ms.openlocfilehash: 3a50353aae8e03c3ebb3ee9ec2f642f21836e925
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605021"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>ホーム複合現実での 3D モデルの配置を有効にします。

> [!NOTE]
> この機能は、の一部として追加された、 [Windows 10 April 2018 Update](release-notes-april-2018.md)します。 Windows の以前のバージョンは、この機能と互換性がありません。

[Windows Mixed Reality ホーム](navigating-the-windows-mixed-reality-home.md)始めるユーザーがアプリケーションを起動する前に配置する場所です。 一部のシナリオでは、(ホログラム アプリ) のような 2D アプリは、装飾、またはフル 3D でさらなる調査用に 3D モデルの複合現実ホームに直接配置を有効にします。 *モデル プロトコルを追加*3D モデルを web サイトや自宅、Windows Mixed Reality に直接アプリケーションから送信するために保持されますがなど[3D アプリ ランチャー](3d-app-launcher-design-guidance.md)、2D のアプリ、およびホログラム。 

たとえば、3 D の家具、領域をデザインするためのカタログを表示するアプリケーションを開発している場合、ことができますを使用する、*モデル プロトコルを追加*カタログからこれらの家具を 3D モデルを配置するユーザーを許可します。 ユーザーが移動できる、世界では、配置し、サイズを変更すると、自宅で他のホログラムと同じようにこれらの 3D モデルを削除します。 この記事では実装の概要、*モデル プロトコルを追加*アプリまたは web から 3D オブジェクトは、自分の世界を修飾するためのユーザーの有効化を開始できるようにします。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>機能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td>モデルのプロトコルを追加します。</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="overview"></a>概要

Windows Mixed Reality ホームの 3D モデルの配置を有効にする 2 つの手順があります。
1. [3D モデルが Windows Mixed Reality ホームと互換性のあることを確認して](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)します。
2. 実装、*モデル プロトコルを追加*アプリケーションまたは web ページ (この記事)。

## <a name="implementing-the-add-model-protocol"></a>実装する、 *model プロトコルの追加*

作成したら、 [3D モデルを互換性のある](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)、実装することができます、*モデル プロトコルを追加*で任意の web ページまたはアプリケーションから次の URI をアクティブ化します。

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

URI は、リモート リソースをポイントしている場合が自動的にダウンロードされ家庭内に配置します。 ローカル リソースは、家庭内に配置する前に、複合現実ホームのアプリのデータ フォルダーにコピーされます。 アカウントのユーザー可能性がありますが実行されている以前のバージョンの Windows ボタンを非表示または可能であれば無効にすることによってこの機能をサポートしないシナリオのエクスペリエンスを設計することをお勧めします。 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>呼び出す、*モデル プロトコルを追加*ユニバーサル Windows プラットフォーム アプリから。

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>呼び出す、*モデル プロトコルを追加*web ページから。

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>(VR) のイマーシブ ヘッドセットに関する考慮事項

* 呼び出す前に実行されているがない混合現実ポータル没入型の (VR) ヘッドセット場合、*モデル プロトコルを追加*します。 ここで、*モデル プロトコルを追加*が Mixed Reality ポータルを起動し、直接、ヘッドセットは検索ホーム複合現実で到着すると、オブジェクトします。 
* 呼び出すときに、*モデル プロトコルを追加*既に実行されている混合現実ポータルを使用したデスクトップで、ヘッドセットが「起動」ことを確認します。 それ以外の場合は、配置は成功しません。 

## <a name="see-also"></a>関連項目

* [Windows Mixed Reality 自宅で使用するための 3D モデルを作成します。](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Windows Mixed Reality ホームに移動します。](navigating-the-windows-mixed-reality-home.md)
