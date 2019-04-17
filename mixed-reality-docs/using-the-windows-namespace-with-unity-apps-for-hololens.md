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
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a><span data-ttu-id="3afc2-104">HoloLens の Unity アプリを使用して Windows 名前空間の使用</span><span class="sxs-lookup"><span data-stu-id="3afc2-104">Using the Windows namespace with Unity apps for HoloLens</span></span>

<span data-ttu-id="3afc2-105">このページでは、HoloLens の Unity プロジェクトでの WinRT Api を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3afc2-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="3afc2-106">条件付きで WinRT API 呼び出しが含まれます</span><span class="sxs-lookup"><span data-stu-id="3afc2-106">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="3afc2-107">WinRT Api は、Windows 8、Windows 8.1、またはユニバーサル Windows プラットフォームを対象とする Unity プロジェクトのビルドでのみ使用されます。WinRT Api を対象とする Unity のスクリプトで記述するコードは、それらのビルドの条件付きで含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="3afc2-107">WinRT APIs will only be used in Unity project builds that target Windows 8, Windows 8.1, or the Universal Windows Platform; any code that you write in Unity scripts that targets WinRT APIs must be conditionally included for only those builds.</span></span> <span data-ttu-id="3afc2-108">これは NETFX_CORE または WINDOWS_UWP プリプロセッサ定義を使用します。</span><span class="sxs-lookup"><span data-stu-id="3afc2-108">This is done using the NETFX_CORE or WINDOWS_UWP preprocessor definitions.</span></span> <span data-ttu-id="3afc2-109">このルールは、他のコードと同様に、ステートメントを使用してに適用されます。</span><span class="sxs-lookup"><span data-stu-id="3afc2-109">This rule applies to using statements, as well as other code.</span></span>

<span data-ttu-id="3afc2-110">次のコード スニペットは、Unity マニュアル ページをから[ユニバーサル Windows プラットフォーム。内の WinRT APIC#スクリプト](http://docs.unity3d.com/Manual/windowsstore-scripts.html)します。</span><span class="sxs-lookup"><span data-stu-id="3afc2-110">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](http://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="3afc2-111">この例で、広告 ID が返されます、Windows 8.0 または高いターゲットでのみビルド。</span><span class="sxs-lookup"><span data-stu-id="3afc2-111">In this example, an advertising ID is returned, but only on Windows 8.0 or higher target builds:</span></span>

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="3afc2-112">Unity のスクリプトを編集C#プロジェクト</span><span class="sxs-lookup"><span data-stu-id="3afc2-112">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="3afc2-113">Unity エディターでスクリプトをダブルクリックするは既定で起動し、プロジェクトのエディターでスクリプト。</span><span class="sxs-lookup"><span data-stu-id="3afc2-113">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="3afc2-114">WinRT Api は、2 つの理由が正常に表示されます。NETFX_CORE がこの環境で定義されていないと、プロジェクトは、Windows ランタイムを参照していません。</span><span class="sxs-lookup"><span data-stu-id="3afc2-114">The WinRT APIs will appear to be unknown for two reasons: NETFX_CORE is not defined in this environment, and the project does not reference the Windows Runtime.</span></span> <span data-ttu-id="3afc2-115">使用する場合、[およびエクスポートを推奨します設定が組み込まれて](exporting-and-building-a-unity-visual-studio-solution.md)、代わりにそのプロジェクト内のスクリプトを編集、NETFX_CORE を定義しインプレース; この構成では、Windows ランタイムへの参照を含めることも、、WinRT Api になりますし、。IntelliSense で使用できます。</span><span class="sxs-lookup"><span data-stu-id="3afc2-115">If you use the [recommended export and built settings](exporting-and-building-a-unity-visual-studio-solution.md), and edit the scripts in that project instead, it will define NETFX_CORE and also include a reference to the Windows Runtime; with this configuration in place, WinRT APIs will be available for IntelliSense.</span></span>

<span data-ttu-id="3afc2-116">なお、UnityC#プロジェクトを使用してリモート デバッグの Visual Studio で f5 キーを使用してスクリプトをデバッグすることもできます。</span><span class="sxs-lookup"><span data-stu-id="3afc2-116">Note that your Unity C# project can also be used to debug through your scripts using F5 remote debugging in Visual Studio.</span></span> <span data-ttu-id="3afc2-117">IntelliSense が初めて、Unity を開く操作が表示されない場合C#プロジェクト、プロジェクトを閉じて、再び開くにします。</span><span class="sxs-lookup"><span data-stu-id="3afc2-117">If you do not see IntelliSense working the first time that you open your Unity C# project, close the project and re-open it.</span></span> <span data-ttu-id="3afc2-118">IntelliSense では、作業を開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3afc2-118">IntelliSense should start working.</span></span>

## <a name="see-also"></a><span data-ttu-id="3afc2-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="3afc2-119">See also</span></span>
* [<span data-ttu-id="3afc2-120">エクスポートして、Unity Visual Studio ソリューションを構築します。</span><span class="sxs-lookup"><span data-stu-id="3afc2-120">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
