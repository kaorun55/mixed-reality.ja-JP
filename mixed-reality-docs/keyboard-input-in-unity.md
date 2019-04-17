---
title: Unity におけるキーボード入力
description: Unity では、使用可能な物理キーボードがない場合は、キーボード入力を受け入れるため TouchScreenKeyboard クラスを提供します。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: キーボードの入力、unity、touchscreenkeyboard
ms.openlocfilehash: 35f6f0df993931eea35db7b167110b341ea0c0f2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604888"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="02dbf-104">Unity におけるキーボード入力</span><span class="sxs-lookup"><span data-stu-id="02dbf-104">Keyboard input in Unity</span></span>

<span data-ttu-id="02dbf-105">\**名前空間:\*\*\*UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="02dbf-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="02dbf-106">**種類**:*[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="02dbf-106">**Type**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="02dbf-107">HoloLens などの Bluetooth キーボード入力の多くの形式がサポートされますが、ほとんどのアプリケーションがすべてのユーザーが使用可能な物理キーボードにあるを想定することはできません。</span><span class="sxs-lookup"><span data-stu-id="02dbf-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications cannot assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="02dbf-108">アプリケーションは、テキスト入力を必要とする場合スクリーン キーボード上の何らかの形式を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="02dbf-108">If your application requires text input, some form of on screen keyboard should be provided.</span></span>

<span data-ttu-id="02dbf-109">Unity は、 *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* 使用可能な物理キーボードがない場合は、キーボード入力を受け入れるためのクラス。</span><span class="sxs-lookup"><span data-stu-id="02dbf-109">Unity provides the *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there is no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="02dbf-110">Unity での HoloLens システム キーボード動作</span><span class="sxs-lookup"><span data-stu-id="02dbf-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="02dbf-111">HoloLens、上、 *TouchScreenKeyboard*スクリーン キーボード上のシステムを活用します。</span><span class="sxs-lookup"><span data-stu-id="02dbf-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on screen keyboard.</span></span> <span data-ttu-id="02dbf-112">スクリーン キーボード上のシステムは、キーボードを表示し、入力が送信された後に、帯域幅消費型のビューを返す 2D セカンダリ XAML ビューを作成するため、Unity は、帯域幅消費型ビューの上部にオーバーレイにできません。</span><span class="sxs-lookup"><span data-stu-id="02dbf-112">The system's on screen keyboard is unable to overlay on top of a volumetric view so Unity has to create a secondary 2D XAML view to show the keyboard then return back to the volumetric view once input has been submitted.</span></span> <span data-ttu-id="02dbf-113">ユーザー フローでは、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="02dbf-113">The user flow goes like this:</span></span>
1. <span data-ttu-id="02dbf-114">ユーザーが原因でアプリのコードを呼び出すアクションを実行*TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="02dbf-114">The user performs an action causing app code to call *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="02dbf-115">アプリの呼び出しの前に、アプリの一時停止状態の役目です*TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="02dbf-115">The app is responsible for pausing app state before calling *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="02dbf-116">これまで帯域幅消費型のビューに切り替える前に終了することが、アプリ</span><span class="sxs-lookup"><span data-stu-id="02dbf-116">The app may terminate before ever switching back to the volumetric view</span></span>
2. <span data-ttu-id="02dbf-117">Unity は、世界中の自動配置は 2D XAML ビューに切り替わります</span><span class="sxs-lookup"><span data-stu-id="02dbf-117">Unity switches to a 2D XAML view which is auto-placed in the world</span></span>
3. <span data-ttu-id="02dbf-118">ユーザーがシステム キーボードを使用してテキストを入力し、送信またはキャンセル</span><span class="sxs-lookup"><span data-stu-id="02dbf-118">The user enters text using the system keyboard and submits or cancels</span></span>
4. <span data-ttu-id="02dbf-119">Unity は、帯域幅消費型のビューに切り替える</span><span class="sxs-lookup"><span data-stu-id="02dbf-119">Unity switches back to the volumetric view</span></span>
    * <span data-ttu-id="02dbf-120">アプリを再開するため、アプリは、状態、 *TouchScreenKeyboard*は行われます</span><span class="sxs-lookup"><span data-stu-id="02dbf-120">The app is responsible for resuming app state when the *TouchScreenKeyboard* is done</span></span>
5. <span data-ttu-id="02dbf-121">送信されたテキストが表示されます、 *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="02dbf-121">Submitted text is available in the *TouchScreenKeyboard*</span></span>

### <a name="available-keyboard-views"></a><span data-ttu-id="02dbf-122">使用可能なキーボード ビュー</span><span class="sxs-lookup"><span data-stu-id="02dbf-122">Available keyboard views</span></span>

<span data-ttu-id="02dbf-123">さまざまなキーボードの 6 つのビューを使用できます。</span><span class="sxs-lookup"><span data-stu-id="02dbf-123">There are six different keyboard views available:</span></span>
* <span data-ttu-id="02dbf-124">単一行のテキスト ボックス</span><span class="sxs-lookup"><span data-stu-id="02dbf-124">Single-line textbox</span></span>
* <span data-ttu-id="02dbf-125">タイトルを含む単一行の textbox</span><span class="sxs-lookup"><span data-stu-id="02dbf-125">Single-line textbox with title</span></span>
* <span data-ttu-id="02dbf-126">複数行テキスト ボックス</span><span class="sxs-lookup"><span data-stu-id="02dbf-126">Multi-line textbox</span></span>
* <span data-ttu-id="02dbf-127">タイトルを含む複数行の textbox</span><span class="sxs-lookup"><span data-stu-id="02dbf-127">Multi-line textbox with title</span></span>
* <span data-ttu-id="02dbf-128">単一行のパスワード ボックス</span><span class="sxs-lookup"><span data-stu-id="02dbf-128">Single-line password box</span></span>
* <span data-ttu-id="02dbf-129">単一行のパスワード ボックスのタイトル</span><span class="sxs-lookup"><span data-stu-id="02dbf-129">Single-line password box with title</span></span>

## <a name="how-to-enable-the-system-keyboard-in-unity"></a><span data-ttu-id="02dbf-130">Unity でシステム キーボードを有効にする方法</span><span class="sxs-lookup"><span data-stu-id="02dbf-130">How to enable the system keyboard in Unity</span></span>

<span data-ttu-id="02dbf-131">HoloLens システム キーボードでは、「UWP ビルドの種類」"XAML"に設定と共にエクスポートされる Unity アプリケーションで使用できるのみです。</span><span class="sxs-lookup"><span data-stu-id="02dbf-131">The HoloLens system keyboard is only available to Unity applications that are exported with the "UWP Build Type" set to "XAML".</span></span> <span data-ttu-id="02dbf-132">"XAML"を「UWP ビルドの種類」として"D3D"を選択するときにすることのトレードオフがあります。</span><span class="sxs-lookup"><span data-stu-id="02dbf-132">There are tradeoffs you make when you choose "XAML" as the "UWP Build Type" over "D3D".</span></span> <span data-ttu-id="02dbf-133">調査になる場合、これらのトレードオフに慣れていない、[ソリューションの代替入力](#alternative-keyboard-options)システム キーボードにします。</span><span class="sxs-lookup"><span data-stu-id="02dbf-133">If you aren't comfortable with those tradeoffs, you may wish to explore an [alternative input solution](#alternative-keyboard-options) to the system keyboard.</span></span>
1. <span data-ttu-id="02dbf-134">開く、**ファイル**メニュー選択し、**ビルド設定しています.**</span><span class="sxs-lookup"><span data-stu-id="02dbf-134">Open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="02dbf-135">確認、**プラットフォーム**に設定されている**Windows ストア**、 **SDK**に設定されている**ユニバーサル 10**、設定と、 **UWP ビルドの種類**に**XAML**します。</span><span class="sxs-lookup"><span data-stu-id="02dbf-135">Ensure the **Platform** is set to **Windows Store**, the **SDK** is set to **Universal 10**, and set the **UWP Build Type** to **XAML**.</span></span>
3. <span data-ttu-id="02dbf-136">**Build Settings**ダイアログ ボックスで、をクリックして、**プレーヤー設定しています.** ボタン</span><span class="sxs-lookup"><span data-stu-id="02dbf-136">In the **Build Settings** dialog, click the **Player Settings...** button</span></span>
4. <span data-ttu-id="02dbf-137">選択、 **Windows Store 用の設定に** タブ</span><span class="sxs-lookup"><span data-stu-id="02dbf-137">Select the **Settings for Windows Store** tab</span></span>
5. <span data-ttu-id="02dbf-138">展開、**その他の設定**グループ</span><span class="sxs-lookup"><span data-stu-id="02dbf-138">Expand the **Other Settings** group</span></span>
6. <span data-ttu-id="02dbf-139">**レンダリング** セクションで、チェック、**仮想現実サポート**新しいを追加するチェック ボックスをオン**仮想現実デバイス**一覧</span><span class="sxs-lookup"><span data-stu-id="02dbf-139">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list</span></span>
7. <span data-ttu-id="02dbf-140">確認**Windows Holographic**仮想現実 Sdk の一覧に表示されます</span><span class="sxs-lookup"><span data-stu-id="02dbf-140">Ensure **Windows Holographic** appears in the list of Virtual Reality SDKs</span></span>

>[!NOTE]
><span data-ttu-id="02dbf-141">HoloLens デバイスと仮想現実のサポートとして、ビルドをマークしないで、プロジェクトは 2D XAML アプリとしてエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="02dbf-141">If you don't mark the build as Virtual Reality Supported with the HoloLens device, the project will export as a 2D XAML app.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="02dbf-142">Unity アプリでシステム キーボードの使用</span><span class="sxs-lookup"><span data-stu-id="02dbf-142">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="02dbf-143">キーボードを宣言します。</span><span class="sxs-lookup"><span data-stu-id="02dbf-143">Declare the keyboard</span></span>

<span data-ttu-id="02dbf-144">クラスを格納する変数を宣言、 *TouchScreenKeyboard*し、キーボード、文字列を保持する変数を返します。</span><span class="sxs-lookup"><span data-stu-id="02dbf-144">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="02dbf-145">キーボードを呼び出す</span><span class="sxs-lookup"><span data-stu-id="02dbf-145">Invoke the keyboard</span></span>

<span data-ttu-id="02dbf-146">イベントが発生するキーボード入力を要求しているときに、必要な入力の種類に応じて、これらの関数のいずれかを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="02dbf-146">When an event occurs requesting keyboard input, call one of these functions depending upon the type of input desired.</span></span> <span data-ttu-id="02dbf-147">タイトルが textPlaceholder パラメーターで指定されたことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="02dbf-147">Note that the title is specified in the textPlaceholder parameter.</span></span>

```cs
// Single-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);

// Single-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false, "Single-line title");

// Multi-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false);

// Multi-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false, "Multi-line Title");

// Single-line password box
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false);

// Single-line password box with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false, "Secure Single-line Title");
```

### <a name="retrieve-typed-contents"></a><span data-ttu-id="02dbf-148">型指定されたコンテンツを取得します。</span><span class="sxs-lookup"><span data-stu-id="02dbf-148">Retrieve typed contents</span></span>

<span data-ttu-id="02dbf-149">Update ループでは、キーボードが新しい入力を受信するかどうか、他の場所で使用するため保存できます。</span><span class="sxs-lookup"><span data-stu-id="02dbf-149">In the update loop, check if the keyboard received new input and store it for use elsewhere.</span></span>

```cs
if (TouchScreenKeyboard.visible == false && keyboard != null)
{
       if (keyboard.done == true)
       {
           keyboardText = keyboard.text;
           keyboard = null;
       }
}
```

## <a name="alternative-keyboard-options"></a><span data-ttu-id="02dbf-150">代替キーボード オプション</span><span class="sxs-lookup"><span data-stu-id="02dbf-150">Alternative keyboard options</span></span>

<span data-ttu-id="02dbf-151">切り替え元の帯域幅消費型のビューを 2D のビューに、ユーザーから入力されたテキストを取得するための望ましい方法ではないことを認識しています。</span><span class="sxs-lookup"><span data-stu-id="02dbf-151">We understand that switching out of a volumetric view into a 2D view isn't the ideal way to get text input from the user.</span></span>

<span data-ttu-id="02dbf-152">Unity からシステム キーボードを利用するための現在の代替手段は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="02dbf-152">The current alternatives to leveraging the system keyboard through Unity include:</span></span>
* <span data-ttu-id="02dbf-153">入力に対して音声認識を使用して (<b>注:</b>間違いやすく、辞書で見つからなかった単語は、多くの場合、これと、パスワードの入力には適していません)</span><span class="sxs-lookup"><span data-stu-id="02dbf-153">Using speech dictation for input (<b>Note:</b> this is often error prone for words not found in the dictionary and is not suitable for password entry)</span></span>
* <span data-ttu-id="02dbf-154">アプリケーションのビューが排他的で動作するキーボードを作成します。</span><span class="sxs-lookup"><span data-stu-id="02dbf-154">Create a keyboard that works in your applications exclusive view</span></span>
