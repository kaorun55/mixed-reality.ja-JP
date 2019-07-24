---
title: HoloLens 用 Unity アプリでの Windows 名前空間の使用
description: HoloLens の Unity プロジェクトで WinRT Api を使用する方法について説明します。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、WinRT、windows mixed reality、API、チュートリアル
ms.openlocfilehash: fd25548de8eeb3c8157a3f9de283dc5004ed1180
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548735"
---
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a>HoloLens 用 Unity アプリでの Windows 名前空間の使用

このページでは、HoloLens の Unity プロジェクトで WinRT Api を使用する方法について説明します。

## <a name="conditionally-include-winrt-api-calls"></a>条件付きで WinRT API 呼び出しを含める

WinRT Api は、ユニバーサル Windows プラットフォームと Xbox One プラットフォーム用に構築された Unity プロジェクトに利用できます。WinRT Api を対象とする Unity スクリプトで作成するすべてのコードは、それらのビルドに対して条件付きで含める必要があります。 

これは、Unity の2つの手順で行うことができます。
1) プレーヤーの設定で、API 互換性レベルを **.net 4.6**または **.NET Standard 2.0**に設定する必要があります。
    -  > **プロジェクト設定**   プレーヤー構成 Api の互換性レベルを .net 4.6 または .NET Standard 2.0 に編集する >  >  > 
2) プリプロセッサディレクティブ**ENABLE_WINMD_SUPPORT**は、WinRT を利用したコードをラップする必要があります

次のコードスニペットは、ユニバーサル Windows プラットフォームの[Unity の手動ページから抜粋したものです。スクリプト](http://docs.unity3d.com/Manual/windowsstore-scripts.html)内のC# WinRT API。 この例では、広告 ID が返されますが、UWP と Xbox One のみがビルドされます。

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if ENABLE_WINMD_SUPPORT
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Unity C#プロジェクトでスクリプトを編集する

Unity エディターでスクリプトをダブルクリックすると、既定ではエディタープロジェクトでスクリプトが起動されます。 Visual Studio プロジェクトで Windows ランタイムが参照されていないため、WinRT Api は不明であるように見えます。 さらに、 **ENALBE_WINMD_SUPPORT**ディレクティブは未定義になり、ラップされたコード *#if*は、プロジェクトを UWP Visual Studio ソリューションにビルドするまで無視されます。

## <a name="see-also"></a>関連項目
* [Unity Visual Studio ソリューションのエクスポートとビルド](exporting-and-building-a-unity-visual-studio-solution.md)
* [Unity のサポート Windows ランタイム](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)