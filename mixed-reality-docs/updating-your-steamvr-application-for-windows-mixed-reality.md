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
# <a name="updating-your-steamvr-application-for-windows-mixed-reality"></a><span data-ttu-id="ff8d9-104">Windows Mixed Reality を SteamVR アプリケーションを更新しています</span><span class="sxs-lookup"><span data-stu-id="ff8d9-104">Updating your SteamVR application for Windows Mixed Reality</span></span>

<span data-ttu-id="ff8d9-105">開発者がテストし、Windows Mixed Reality ヘッドセットで実行するには、その SteamVR エクスペリエンスを最適化することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-105">We encourage developers to test and optimize their SteamVR experiences to run on Windows Mixed Reality headsets.</span></span> <span data-ttu-id="ff8d9-106">このドキュメントでは、開発者が Windows Mixed Reality でエクスペリエンスを優れた実行することを確認すること、一般的な機能強化について説明します。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-106">This documentation covers common improvements developers can make to ensure that their experience runs great on Windows Mixed Reality.</span></span>

## <a name="initial-setup-instructions"></a><span data-ttu-id="ff8d9-107">初期セットアップ手順</span><span class="sxs-lookup"><span data-stu-id="ff8d9-107">Initial setup instructions</span></span>

<span data-ttu-id="ff8d9-108">最初のフォローを確認して、ゲームや Windows Mixed Reality でアプリをテストを開始する、[ファースト ステップ ガイドです。](http://aka.ms/WindowsMixedRealitySteamVR)</span><span class="sxs-lookup"><span data-stu-id="ff8d9-108">To start testing out your game or app on Windows Mixed Reality make sure to first follow our [getting started guide.](http://aka.ms/WindowsMixedRealitySteamVR)</span></span>

## <a name="controller-models"></a><span data-ttu-id="ff8d9-109">コント ローラー モデル</span><span class="sxs-lookup"><span data-stu-id="ff8d9-109">Controller Models</span></span>
1. <span data-ttu-id="ff8d9-110">場合は、アプリは、コント ローラー モデルを表示します。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-110">If your app renders controller models:</span></span>
    * <span data-ttu-id="ff8d9-111">使用して、 [Windows Mixed Reality 運動コント ローラー モデル](motion-controllers.md#rendering-the-motion-controller-model)</span><span class="sxs-lookup"><span data-stu-id="ff8d9-111">Use the [Windows Mixed Reality motion controller models](motion-controllers.md#rendering-the-motion-controller-model)</span></span>
    * <span data-ttu-id="ff8d9-112">(例: 変換コンポーネント パーツを使用して IVRRenderModel::GetComponentState ローカルを取得するには</span><span class="sxs-lookup"><span data-stu-id="ff8d9-112">Use IVRRenderModel::GetComponentState to get local transforms to component parts (eg.</span></span> <span data-ttu-id="ff8d9-113">ポインターの姿勢)</span><span class="sxs-lookup"><span data-stu-id="ff8d9-113">Pointer pose)</span></span>
2. <span data-ttu-id="ff8d9-114">処理の概念のエクスペリエンスは、Api コント ローラーを区別するために、入力からヒントを取得する必要があります[(Unity など)](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)</span><span class="sxs-lookup"><span data-stu-id="ff8d9-114">Experiences that have a notion of handedness should get hints from the input APIs to differentiate controllers [(Unity example)](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)</span></span>

## <a name="controls"></a><span data-ttu-id="ff8d9-115">コントロール</span><span class="sxs-lookup"><span data-stu-id="ff8d9-115">Controls</span></span>

<span data-ttu-id="ff8d9-116">設計または調整するときに、コントロールのレイアウトに注意してください、次の予約済みのコマンド セットしてください。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-116">When designing or adjusting your control layout keep in mind the following set of reserved commands:</span></span>
1. <span data-ttu-id="ff8d9-117">をクリックして、**左と右アナログ スティック**に予約されている、**蒸気のダッシュ ボード**します。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-117">Clicking down the **left and right analog thumbstick** is reserved for the **Steam Dashboard**.</span></span>
2. <span data-ttu-id="ff8d9-118">**Windows ボタン**Windows Mixed reality ホーム ユーザーは常に返します。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-118">The **Windows button** will always return users to the Windows Mixed Reality home.</span></span>

<span data-ttu-id="ff8d9-119">Thumb スティックを既定の teleportation と一致するベース可能であれば、 [Windows Mixed Reality ホーム](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)teleportation 動作</span><span class="sxs-lookup"><span data-stu-id="ff8d9-119">If possible, default to thumb stick based teleportation to match the [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportation behavior</span></span>

## <a name="tooltips-and-ui"></a><span data-ttu-id="ff8d9-120">ツールヒントと UI</span><span class="sxs-lookup"><span data-stu-id="ff8d9-120">Tooltips and UI</span></span>

<span data-ttu-id="ff8d9-121">多くの VR ゲームでは、アニメーション コント ローラー ツールチップとオーバーレイ、ゲームまたはアプリの最も重要なコマンドをユーザーに教えるの活用します。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-121">Many VR games take advantage of motion controller tooltips and overlays to teach users the most important commands for their game or app.</span></span> <span data-ttu-id="ff8d9-122">Windows Mixed reality 用のアプリケーションのチューニング時に、Windows のコント ローラー モデルにマップするツールヒントを確認するには、エクスペリエンスのこの部分のレビューをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-122">When tuning your application for Windows Mixed reality we recommend reviewing this part of your experience to make sure the tooltips map to the Windows controller models.</span></span>

<span data-ttu-id="ff8d9-123">さらがある場合は、コント ローラーのイメージを表示するエクスペリエンスで任意のポイント Windows Mixed Reality アニメーション コント ローラーを使用して更新されたイメージを提供することを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-123">Additionally if there are any points in your experience where you display images of the controllers make sure to provide updated images using the Windows Mixed Reality motion controllers.</span></span>

## <a name="haptics"></a><span data-ttu-id="ff8d9-124">Haptics</span><span class="sxs-lookup"><span data-stu-id="ff8d9-124">Haptics</span></span>

<span data-ttu-id="ff8d9-125">以降では、 [Windows 10 April 2018 Update](release-notes-april-2018.md)、Windows Mixed Reality を SteamVR のエクスペリエンスのために haptics はサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-125">Beginning with the [Windows 10 April 2018 Update](release-notes-april-2018.md), haptics are now supported for SteamVR experiences on Windows Mixed Reality.</span></span> <span data-ttu-id="ff8d9-126">SteamVR アプリやゲーム haptics のサポートが既に含まれている場合も動作するはずようになりました (追加作業がない) で[Windows Mixed Reality モーションのコント ローラー](motion-controllers.md)します。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-126">If your SteamVR app or game already includes support for haptics, it should now work (with no additional work) with [Windows Mixed Reality motion controllers](motion-controllers.md).</span></span>

<span data-ttu-id="ff8d9-127">Windows Mixed Reality モーションのコント ローラーは、いくつか他 SteamVR モーションのコント ローラー、若干異なるが予想以上のユーザー エクスペリエンスにつながる可能性のある線形アクチュエータではなく、標準 haptics モーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-127">Windows Mixed Reality motion controllers use a standard haptics motor, as opposed to the linear actuators found in some other SteamVR motion controllers, which can lead to a slightly different-than-expected user experience.</span></span> <span data-ttu-id="ff8d9-128">そのため、テストとチューニングの Windows Mixed Reality モーションのコント ローラーで haptics の設計お勧めします。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-128">So, we recommend testing and tuning your haptics design with Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="ff8d9-129">たとえば、ハプティクス パルスの短いことがあります (5 ~ 10 ミリ秒) は Windows Mixed Reality モーションのコント ローラーに小さくします。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-129">For example, sometimes short haptic pulses (5-10 ms) are less noticeable on Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="ff8d9-130">顕著なパルスを生成するには、もう一度電源が指示される前に、長い「クリック」(40 70ms) を迅速に作成する自動車の多くの時間の送信を試してください。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-130">To produce a more noticeable pulse, experiment with sending a longer “click” (40-70ms) to give the motor more time to spin up before being told to power off again.</span></span>

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a><span data-ttu-id="ff8d9-131">Windows Mixed Reality スタート メニューから SteamVR アプリの起動</span><span class="sxs-lookup"><span data-stu-id="ff8d9-131">Launching SteamVR apps from Windows Mixed Reality Start menu</span></span>

<span data-ttu-id="ff8d9-132">ストリームによって配布、VR エクスペリエンスのしました[SteamVR ベータ版の Windows Mixed Reality を更新](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800)最新と共に[Windows Insider](https://insider.windows.com) RS5 フライト SteamVR タイトルに表示されるように、"すべてのアプリ] で Windows 混合実際には [スタート] メニューが自動的に一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-132">For VR experiences distributed through Steam, we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest [Windows Insider](https://insider.windows.com) RS5 flights so that SteamVR titles now show up in the Windows Mixed Reality Start menu in the "All apps" list automatically.</span></span> <span data-ttu-id="ff8d9-133">ソフトウェア バージョンがインストールされているこれらでは、お客様は Windows Mixed Reality ホーム内から直接 SteamVR タイトルをヘッドセットを削除せず今すぐ起動できます。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-133">With these software versions installed, your customers can now launch SteamVR titles directly from within the Windows Mixed Reality home without removing their headsets.</span></span>

## <a name="windows-mixed-reality-logo"></a><span data-ttu-id="ff8d9-134">Windows Mixed Reality ロゴ</span><span class="sxs-lookup"><span data-stu-id="ff8d9-134">Windows Mixed Reality logo</span></span>

<span data-ttu-id="ff8d9-135">Windows Mixed Reality サポートをタイトルを表示するには、移動、アプリのランディング ページに「ストア ページの編集」リンクに"基本情報 タブをクリックし、「仮想現実です」まで下へスクロール</span><span class="sxs-lookup"><span data-stu-id="ff8d9-135">To display Windows Mixed Reality support for your title, go to the "Edit Store Page" link on your App Landing Page, click the "Basic Info" tab, and scroll down to "Virtual Reality."</span></span> <span data-ttu-id="ff8d9-136">"非表示にする Windows Mixed Reality"をオフにし、ストアに発行します。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-136">Uncheck the "Hide Windows Mixed Reality" and then publish to the store.</span></span>

## <a name="bugs-and-feedback"></a><span data-ttu-id="ff8d9-137">バグやフィードバック</span><span class="sxs-lookup"><span data-stu-id="ff8d9-137">Bugs and feedback</span></span>

<span data-ttu-id="ff8d9-138">Windows Mixed Reality SteamVR エクスペリエンスを向上する際、お客様のフィードバックは貴重ではありません。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-138">Your feedback is invaluable when it comes to improving the Windows Mixed Reality SteamVR experience.</span></span> <span data-ttu-id="ff8d9-139">すべてのフィードバックと使用してバグを送信してください、 [Windows フィードバック Hub](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback)します。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-139">Please submit all feedback and bugs through the [Windows Feedback Hub](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback).</span></span> <span data-ttu-id="ff8d9-140">いくつか紹介[SteamVR フィードバックを参考になったできるだけさせる方法に関するヒント](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)します。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-140">Here are some [tips on how to make your SteamVR feedback as helpful as possible](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).</span></span>

<span data-ttu-id="ff8d9-141">質問またはコメントを共有する場合もアドレスで、[蒸気フォーラム](http://steamcommunity.com/app/719950/discussions/)します。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-141">If you have questions or comments to share, you can also reach us on our [Steam forum](http://steamcommunity.com/app/719950/discussions/).</span></span>

## <a name="faqs-and-troubleshooting"></a><span data-ttu-id="ff8d9-142">FAQ とトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="ff8d9-142">FAQs and troubleshooting</span></span>

<span data-ttu-id="ff8d9-143">設定するか、エクスペリエンスの再生の一般的な問題が発生した場合[をチェック アウト、最新のトラブルシューティング手順](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)します。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-143">If you're running into general issues setting up or playing your experience, [check out the latest troubleshooting steps](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="ff8d9-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff8d9-144">See also</span></span>
* [<span data-ttu-id="ff8d9-145">ツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="ff8d9-145">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="ff8d9-146">ヘッドセットとアニメーション コント ローラーのドライバーの履歴</span><span class="sxs-lookup"><span data-stu-id="ff8d9-146">Headset and motion controller driver history</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [<span data-ttu-id="ff8d9-147">Windows Mixed Reality 最小 PC ハードウェアの互換性ガイドライン</span><span class="sxs-lookup"><span data-stu-id="ff8d9-147">Windows Mixed Reality minimum PC hardware compatibility guidelines</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
