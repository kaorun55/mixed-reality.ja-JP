---
title: アプリ内購入
description: アプリ内購入は、複合現実アプリでサポートされますが、それらを設定するには、いくつか作業があります。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: アプリ内購入、hololens
ms.openlocfilehash: bc96893d1777e94295285736982fd9a7167240a4
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602881"
---
# <a name="in-app-purchases"></a>アプリ内購入

アプリ内購入は、HoloLens でサポートされますが、それらを設定するには、いくつか作業があります。

アプリの購入を利用するために、機能する必要があります。
* 作成、XAML [2D ビュー](app-views.md)スレート型として表示するには
* 没入型のビューを離れる配置をアクティブ化するために切り替える
* Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

この API は、アプリ内購入の名前、説明、および価格を表示する株価の Windows OS ポップアップが表示されます。 ユーザーは、購入に関するオプションを選択できます。 アプリは、ユーザーに戻るには、UI を提示する必要がありますアクションが完了すると、その[没入型ビュー](app-views.md)します。

デスクトップ ベースの Windows Mixed Reality イマーシブ ヘッドセットを対象としたアプリ、RequestProductPurchaseAsync API を呼び出す前に、XAML ビューに手動で切り替えることは必要はありません。
