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
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a><span data-ttu-id="d1e3e-104">HoloLens 用 Unity アプリでの Windows 名前空間の使用</span><span class="sxs-lookup"><span data-stu-id="d1e3e-104">Using the Windows namespace with Unity apps for HoloLens</span></span>

<span data-ttu-id="d1e3e-105">このページでは、HoloLens の Unity プロジェクトで WinRT Api を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1e3e-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="d1e3e-106">条件付きで WinRT API 呼び出しを含める</span><span class="sxs-lookup"><span data-stu-id="d1e3e-106">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="d1e3e-107">WinRT Api は、ユニバーサル Windows プラットフォームと Xbox One プラットフォーム用に構築された Unity プロジェクトに利用できます。WinRT Api を対象とする Unity スクリプトで作成するすべてのコードは、それらのビルドに対して条件付きで含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1e3e-107">WinRT APIs can be leveraged for Unity projects built for the Universal Windows Platform and Xbox One platform; any code that you write in Unity scripts that target WinRT APIs must be conditionally included for only those builds.</span></span> 

<span data-ttu-id="d1e3e-108">これは、Unity の2つの手順で行うことができます。</span><span class="sxs-lookup"><span data-stu-id="d1e3e-108">This can be done via two steps in Unity:</span></span>
1) <span data-ttu-id="d1e3e-109">プレーヤーの設定で、API 互換性レベルを **.net 4.6**または **.NET Standard 2.0**に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1e3e-109">API compatibility level must be set to **.NET 4.6** or **.NET Standard 2.0** in the player settings</span></span>
    - <span data-ttu-id="d1e3e-110"> > **プロジェクト設定**   プレーヤー構成 Api の互換性レベルを .net 4.6 または .NET Standard 2.0 に編集する >  >  > </span><span class="sxs-lookup"><span data-stu-id="d1e3e-110">**Edit** > **Project Settings** > **Player** > **Configuration** > **Api Compatibility Level** to **.NET 4.6** or **.NET Standard 2.0**</span></span>
2) <span data-ttu-id="d1e3e-111">プリプロセッサディレクティブ**ENABLE_WINMD_SUPPORT**は、WinRT を利用したコードをラップする必要があります</span><span class="sxs-lookup"><span data-stu-id="d1e3e-111">The preprocessor directive **ENABLE_WINMD_SUPPORT** must be wrapped around any WinRT-leveraged code</span></span>

<span data-ttu-id="d1e3e-112">次のコードスニペットは、ユニバーサル Windows プラットフォームの[Unity の手動ページから抜粋したものです。スクリプト](http://docs.unity3d.com/Manual/windowsstore-scripts.html)内のC# WinRT API。</span><span class="sxs-lookup"><span data-stu-id="d1e3e-112">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](http://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="d1e3e-113">この例では、広告 ID が返されますが、UWP と Xbox One のみがビルドされます。</span><span class="sxs-lookup"><span data-stu-id="d1e3e-113">In this example, an advertising ID is returned, but only on UWP and Xbox One builds:</span></span>

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="d1e3e-114">Unity C#プロジェクトでスクリプトを編集する</span><span class="sxs-lookup"><span data-stu-id="d1e3e-114">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="d1e3e-115">Unity エディターでスクリプトをダブルクリックすると、既定ではエディタープロジェクトでスクリプトが起動されます。</span><span class="sxs-lookup"><span data-stu-id="d1e3e-115">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="d1e3e-116">Visual Studio プロジェクトで Windows ランタイムが参照されていないため、WinRT Api は不明であるように見えます。</span><span class="sxs-lookup"><span data-stu-id="d1e3e-116">The WinRT APIs will appear to be unknown because the Visual Studio project does not reference the Windows Runtime.</span></span> <span data-ttu-id="d1e3e-117">さらに、 **ENALBE_WINMD_SUPPORT**ディレクティブは未定義になり、ラップされたコード *#if*は、プロジェクトを UWP Visual Studio ソリューションにビルドするまで無視されます。</span><span class="sxs-lookup"><span data-stu-id="d1e3e-117">Further, the **ENALBE_WINMD_SUPPORT** directive will be undefined and any *#if* wrapped code will be ignored until you build your project into a UWP Visual Studio solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="d1e3e-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1e3e-118">See also</span></span>
* [<span data-ttu-id="d1e3e-119">Unity Visual Studio ソリューションのエクスポートとビルド</span><span class="sxs-lookup"><span data-stu-id="d1e3e-119">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="d1e3e-120">Unity のサポート Windows ランタイム</span><span class="sxs-lookup"><span data-stu-id="d1e3e-120">Windows Runtime Support Unity</span></span>](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)