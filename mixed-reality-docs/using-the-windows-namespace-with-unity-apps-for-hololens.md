---
title: HoloLens の Unity アプリを使用して Windows 名前空間の使用
description: HoloLens の Unity プロジェクトで、WinRT Api を使用する方法について説明します。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、WinRT、windows の混合実際には、API、チュートリアル
ms.openlocfilehash: ed65b5995d74c54057a49b878c1206d0f06394ca
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599871"
---
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a>HoloLens の Unity アプリを使用して Windows 名前空間の使用

このページでは、HoloLens の Unity プロジェクトでの WinRT Api を使用する方法について説明します。

## <a name="conditionally-include-winrt-api-calls"></a>条件付きで WinRT API 呼び出しが含まれます

WinRT Api は、Windows 8、Windows 8.1、またはユニバーサル Windows プラットフォームを対象とする Unity プロジェクトのビルドでのみ使用されます。WinRT Api を対象とする Unity のスクリプトで記述するコードは、それらのビルドの条件付きで含める必要があります。 これは NETFX_CORE または WINDOWS_UWP プリプロセッサ定義を使用します。 このルールは、他のコードと同様に、ステートメントを使用してに適用されます。

次のコード スニペットは、Unity マニュアル ページをから[ユニバーサル Windows プラットフォーム。内の WinRT APIC#スクリプト](http://docs.unity3d.com/Manual/windowsstore-scripts.html)します。 この例で、広告 ID が返されます、Windows 8.0 または高いターゲットでのみビルド。

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if NETFX_CORE
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Unity のスクリプトを編集C#プロジェクト

Unity エディターでスクリプトをダブルクリックするは既定で起動し、プロジェクトのエディターでスクリプト。 WinRT Api は、2 つの理由が正常に表示されます。NETFX_CORE がこの環境で定義されていないと、プロジェクトは、Windows ランタイムを参照していません。 使用する場合、[およびエクスポートを推奨します設定が組み込まれて](exporting-and-building-a-unity-visual-studio-solution.md)、代わりにそのプロジェクト内のスクリプトを編集、NETFX_CORE を定義しインプレース; この構成では、Windows ランタイムへの参照を含めることも、、WinRT Api になりますし、。IntelliSense で使用できます。

なお、UnityC#プロジェクトを使用してリモート デバッグの Visual Studio で f5 キーを使用してスクリプトをデバッグすることもできます。 IntelliSense が初めて、Unity を開く操作が表示されない場合C#プロジェクト、プロジェクトを閉じて、再び開くにします。 IntelliSense では、作業を開始する必要があります。

## <a name="see-also"></a>関連項目
* [エクスポートして、Unity Visual Studio ソリューションを構築します。](exporting-and-building-a-unity-visual-studio-solution.md)
