---
title: エクスポートして、Unity Visual Studio ソリューションを構築します。
description: この記事では、複合現実プロジェクトをビルドし、Visual Studio でデプロイできるように Unity からエクスポートします。
author: ''
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: unity では、visual studio は、エクスポート、ビルド、展開.
ms.openlocfilehash: 68c86fdfe0e589536dafe2bf53c7d4e5dffcc514
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603698"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a><span data-ttu-id="1bc3c-104">エクスポートして、Unity Visual Studio ソリューションを構築します。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-104">Exporting and building a Unity Visual Studio solution</span></span>

<span data-ttu-id="1bc3c-105">使用するという推奨設定は、システムのキーボードを使用して、アプリケーションでの予定がない場合*D3D*アプリケーションが若干低いメモリを使用し、わずかに高速起動時間があります。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-105">If you don't intend on using the system keyboard in your application, our recommendation is to use *D3D* as your application will use slightly less memory and have a slightly faster launch time.</span></span> <span data-ttu-id="1bc3c-106">システムのキーボードを使用して、プロジェクトで TouchScreenKeyboard API を使用する場合は、としてエクスポートする必要があります。 *XAML*します。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-106">If you are using the TouchScreenKeyboard API in your project to use the system keyboard, you need to export as *XAML*.</span></span>

## <a name="how-to-export-from-unity"></a><span data-ttu-id="1bc3c-107">Unity からエクスポートする方法</span><span class="sxs-lookup"><span data-stu-id="1bc3c-107">How to export from Unity</span></span>

<span data-ttu-id="1bc3c-108">![Unity ビルド設定](images/unitybuildsettings-300px.png)</span><span class="sxs-lookup"><span data-stu-id="1bc3c-108">![Unity build settings](images/unitybuildsettings-300px.png)</span></span><br>
<span data-ttu-id="1bc3c-109">*Unity ビルド設定*</span><span class="sxs-lookup"><span data-stu-id="1bc3c-109">*Unity build settings*</span></span>

1. <span data-ttu-id="1bc3c-110">Unity からプロジェクトをエクスポートする準備ができたら、開く、**ファイル**メニュー選択し、**ビルド設定しています.**</span><span class="sxs-lookup"><span data-stu-id="1bc3c-110">When you are ready to export your project from Unity, open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="1bc3c-111">クリックして**開くシーンを追加**ビルドにシーンを追加します。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-111">Click **Add Open Scenes** to add your scene to the build.</span></span>
3. <span data-ttu-id="1bc3c-112">**Build Settings**ダイアログ ボックスで、HoloLens をエクスポートする次のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-112">In the **Build Settings** dialog, choose the following options to export for HoloLens:</span></span>
   * <span data-ttu-id="1bc3c-113">**プラットフォーム:**  *ユニバーサル Windows プラットフォーム* を必ず選択して **スイッチ プラットフォーム** 選択を有効にします。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-113">**Platform:** *Universal Windows Platform* and be sure to select **Switch Platform** for your selection to take effect.</span></span>
   * <span data-ttu-id="1bc3c-114">**SDK:**  *ユニバーサル 10*します。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-114">**SDK:** *Universal 10*.</span></span>
   * <span data-ttu-id="1bc3c-115">**UWP のビルドの種類:**  *D3D*します。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-115">**UWP Build Type:** *D3D*.</span></span>
4. <span data-ttu-id="1bc3c-116">**省略可能な**:**UnityC#プロジェクト。** チェックされています。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-116">**Optional**: **Unity C# Projects:** Checked.</span></span>

>[!NOTE]
><span data-ttu-id="1bc3c-117">このボックスをオンすることができます。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-117">Checking this box allows you to:</span></span>
>* <span data-ttu-id="1bc3c-118">Visual Studio リモート デバッガーでアプリケーションをデバッグします。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-118">Debug your app in the Visual Studio remote debugger.</span></span>
>* <span data-ttu-id="1bc3c-119">Unity でスクリプトを編集C#WinRT Api を IntelliSense を使用しながらプロジェクト。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-119">Edit scripts in the Unity C# project while using IntelliSense for WinRT APIs.</span></span>

5. <span data-ttu-id="1bc3c-120">**ビルド設定しています.** ウィンドウを開いて、**プレーヤー設定しています.**</span><span class="sxs-lookup"><span data-stu-id="1bc3c-120">From the **Build Settings...** window, open **Player Settings...**</span></span>
6. <span data-ttu-id="1bc3c-121">選択、**ユニバーサル Windows プラットフォームの設定**タブ。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-121">Select the **Settings for Universal Windows Platform** tab.</span></span>
7. <span data-ttu-id="1bc3c-122">展開、 **XR 設定**グループ。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-122">Expand the **XR Settings** group.</span></span>
8. <span data-ttu-id="1bc3c-123">**XR 設定** セクションで、チェック、**仮想現実サポート**新しいを追加するチェック ボックスをオン**仮想現実デバイス**ボックスの一覧を確認します **"Windows 混在実際には"** サポートされているデバイスとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-123">In the **XR Settings** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list and confirm **"Windows Mixed Reality"** is listed as a supported device.</span></span>
9. <span data-ttu-id="1bc3c-124">戻り、 **Build Settings**ダイアログ。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-124">Return to the **Build Settings** dialog.</span></span>
10. <span data-ttu-id="1bc3c-125">選択**ビルド**します。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-125">Select **Build**.</span></span>
11. <span data-ttu-id="1bc3c-126">Windows エクスプ ローラー ダイアログ ボックスが表示される Unity のビルド出力を格納する新しいフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-126">In the Windows Explorer dialog that appears, create a new folder to hold Unity's build output.</span></span> <span data-ttu-id="1bc3c-127">一般に、名前、フォルダーの"App"を付けます。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-127">Generally, we name the folder "App".</span></span>
12. <span data-ttu-id="1bc3c-128">新しく作成したフォルダーを選択し、クリックして**フォルダーの選択**します。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-128">Select the newly created folder and click **Select Folder**.</span></span>
13. <span data-ttu-id="1bc3c-129">Unity のビルドが完了すると、Windows エクスプ ローラー ウィンドウがプロジェクトのルート ディレクトリを開きます。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-129">Once Unity has finished building, a Windows Explorer window will open to the project root directory.</span></span> <span data-ttu-id="1bc3c-130">新しく作成したフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-130">Navigate into the newly created folder.</span></span>
14. <span data-ttu-id="1bc3c-131">このフォルダー内にある生成された Visual Studio ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-131">Open the generated Visual Studio solution file located inside this folder.</span></span>

## <a name="when-to-re-export-from-unity"></a><span data-ttu-id="1bc3c-132">Unity から再エクスポートします。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-132">When to re-export from Unity</span></span>

<span data-ttu-id="1bc3c-133">チェック、"C#プロジェクト"チェック ボックスを Unity からアプリをエクスポートする Visual Studio のソリューションを作成すると、すべての Unity スクリプト ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-133">Checking the "C# Projects" checkbox when exporting your app from Unity creates a Visual Studio solution that includes all your Unity script files.</span></span> <span data-ttu-id="1bc3c-134">これにより、Unity から再エクスポートせずに、スクリプトで反復処理することができます。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-134">This allows you to iterate on your scripts without re-exporting from Unity.</span></span> <span data-ttu-id="1bc3c-135">ただし、スクリプトの内容を変更するだけは、プロジェクトを変更する場合は、Unity からエクスポートして再必要があります。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-135">However, if you want to make changes to your project that aren't just changing the contents of scripts, you will need to re-export from Unity.</span></span> <span data-ttu-id="1bc3c-136">Unity から再エクスポートする必要がある回数のいくつかの例は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-136">Some examples of times you need to re-export from Unity are:</span></span>
* <span data-ttu-id="1bc3c-137">追加し、[プロジェクト] タブで資産を削除します。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-137">You add or remove assets in the Project tab.</span></span>
* <span data-ttu-id="1bc3c-138">[Inspector] タブの任意の値を変更します。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-138">You change any value in the Inspector tab.</span></span>
* <span data-ttu-id="1bc3c-139">追加し、階層 タブからオブジェクトを削除します。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-139">You add or remove objects from the Hierarchy tab.</span></span>
* <span data-ttu-id="1bc3c-140">Unity プロジェクト設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-140">You change any Unity project settings</span></span>

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a><span data-ttu-id="1bc3c-141">構築および Unity Visual Studio ソリューションを展開します。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-141">Building and deploying a Unity Visual Studio solution</span></span>

<span data-ttu-id="1bc3c-142">構築とアプリの展開の残りの部分が行われます[Visual Studio](using-visual-studio.md)します。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-142">The remainder of building and deploying apps happens in [Visual Studio](using-visual-studio.md).</span></span> <span data-ttu-id="1bc3c-143">Unity のビルド構成を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-143">You will need to specify a Unity build configuration.</span></span> <span data-ttu-id="1bc3c-144">Unity の名前付け規則は、何を通常はご利用いただけますを Visual Studio で異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-144">Unity's naming conventions may differ from what you're usually used to in Visual Studio:</span></span>

|  <span data-ttu-id="1bc3c-145">構成</span><span class="sxs-lookup"><span data-stu-id="1bc3c-145">Configuration</span></span>  |  <span data-ttu-id="1bc3c-146">説明</span><span class="sxs-lookup"><span data-stu-id="1bc3c-146">Explanation</span></span> | 
|----------|----------|
|  <span data-ttu-id="1bc3c-147">デバッグ</span><span class="sxs-lookup"><span data-stu-id="1bc3c-147">Debug</span></span>  |  <span data-ttu-id="1bc3c-148">オフのすべての最適化と、プロファイラーが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-148">All optimizations off and the profiler is enabled.</span></span> <span data-ttu-id="1bc3c-149">スクリプトをデバッグするために使用します。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-149">Used to debug scripts.</span></span> | 
|  <span data-ttu-id="1bc3c-150">マスタ</span><span class="sxs-lookup"><span data-stu-id="1bc3c-150">Master</span></span>  |  <span data-ttu-id="1bc3c-151">すべての最適化をオンにし、プロファイラーを無効にします。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-151">All optimizations are turned on and the profiler is disabled.</span></span> <span data-ttu-id="1bc3c-152">アプリをストアに送信するために使用します。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-152">Used to submit apps to the Store.</span></span> | 
|  <span data-ttu-id="1bc3c-153">リリース</span><span class="sxs-lookup"><span data-stu-id="1bc3c-153">Release</span></span>  |  <span data-ttu-id="1bc3c-154">すべての最適化をオンにし、プロファイラーを有効にします。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-154">All optimizations are turned on and the profiler is enabled.</span></span> <span data-ttu-id="1bc3c-155">アプリのパフォーマンスを評価するために使用します。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-155">Used to evaluate app performance.</span></span> | 

<span data-ttu-id="1bc3c-156">上記のリストを生成する必要があります。 Visual Studio プロジェクトを原因となる一般的なトリガーのサブセットであるに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-156">Note, the above list is a subset of the common triggers that will cause the Visual Studio project to need to be generated.</span></span> <span data-ttu-id="1bc3c-157">一般に、Visual Studio 内からの .cs ファイルを編集しても、Unity 内から再生成するプロジェクトには必要ありません。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-157">In general, editing .cs files from within Visual Studio will not require the project to be regenerated from within Unity.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="1bc3c-158">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="1bc3c-158">Troubleshooting</span></span>

<span data-ttu-id="1bc3c-159">場合は、.cs ファイルの編集の認識されて、Visual Studio プロジェクトではいないことを確認することを確認します。"UnityC#プロジェクト"Unity のビルド メニューから VS プロジェクトを生成する場合はオンになっています。</span><span class="sxs-lookup"><span data-stu-id="1bc3c-159">If you find that edits to your .cs files are not being recognized in your Visual Studio project, ensure that "Unity C# Projects" is checked when you generate the VS project from Unity's Build menu.</span></span>
