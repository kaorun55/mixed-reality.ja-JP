---
title: MR 240 - 複数の HoloLens デバイスの共有
description: このコーディング ホログラムの共有の詳細については、Unity、Visual Studio および HoloLens の使用に関するチュートリアルに従います。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit、mixedrealitytoolkit unity、共有、ネットワーク、academy, チュートリアル
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601391"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。  そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。  これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。  サポートされているデバイスで作業を続行するが保持されます。 一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。  この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a>MR 240 の共有:複数の HoloLens デバイス

ホログラムには、場所に残りの領域で移動によって、世界でのプレゼンスが与えられます。 HoloLens の場所でさまざまなを使用してホログラムを保持する[座標系](coordinate-systems.md)オブジェクトの向きと場所を追跡します。 私たちは、デバイス間でこれらの座標システムを共有する場合、共有 holographic 世界に参加できるようにする共有のエクスペリエンスを作成できます。

このチュートリアルでご紹介します。

* 共有のエクスペリエンスのためのネットワークをセットアップします。
* HoloLens デバイス間でホログラムを共有します。
* 共有の holographic 世界の他のユーザーを検出します。
* -その他のプレーヤーの対象を何々 弾丸を起動できる共有の対話型エクスペリエンスを作成します。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td>MR 240 の共有:複数の HoloLens デバイス</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>開始前の作業

### <a name="prerequisites"></a>前提条件

* 正しく構成されている Windows 10 PC[ツールがインストールされている](install-the-tools.md)インターネットにアクセスできます。
* 少なくとも 2 つの HoloLens デバイス[開発用に構成された](using-visual-studio.md#enabling-developer-mode)します。

### <a name="project-files"></a>プロジェクト ファイル

* ダウンロード、[ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip)プロジェクトに必要です。 Unity 2017.2 またはそれ以降が必要です。
  * Unity 5.6 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)します。
  * Unity 5.5 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip)します。
  * Unity 5.4 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)します。
* 解除アーカイブをデスクトップまたは場所に到達する簡単なその他のファイル。 フォルダー名として保持**SharedHolograms**します。

>[!NOTE]
>をダウンロードする前に、ソース コードを検索する場合がある[GitHub で入手できます](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms)します。

## <a name="chapter-1---holo-world"></a>第 1 章 - Holo 世界

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

この章で、最初の Unity プロジェクトとビルド手順のセットアップがされプロセスを展開します。

### <a name="objectives"></a>目標

* Holographic アプリを開発する Unity をセットアップします。
* ホログラムを参照してください。

### <a name="instructions"></a>手順

* Unity を起動します。
* **[開く]** を選択します。
* として場所を入力、 **SharedHolograms**フォルダーの以前にアーカイブ解除します。
* 選択**プロジェクト名**クリック**フォルダーの選択**。
* **階層**を右クリックし、 **Main Camera**選択**削除**します。
* **HoloToolkit 共有-240/プレハブ/カメラ**フォルダー、検索、 **Main Camera** prefab します。
* ドラッグ アンド ドロップ、 **Main Camera**に、**階層**します。
* **階層**、 をクリックして**作成**と**空アイテムの作成**です。
* 新しい右クリックして**GameObject**選択**の名前を変更**します。
* GameObject の名前を変更**HologramCollection**します。
* 選択、 **HologramCollection**オブジェクト、**階層**します。
* **インスペクター**設定、**位置を変換**に。**X:0、Y:-0.25、Z:2**.
* **ホログラム**フォルダーで、**プロジェクト パネル**、検索、 **EnergyHub**資産。
* ドラッグ アンド ドロップ、 **EnergyHub**オブジェクトから、**プロジェクト パネル**を**階層**として、 **HologramCollection の子**します。
* 選択**ファイル > としてシーンを保存しています.**
* 名前をシーン**SharedHolograms**  をクリック**保存**します。
* キーを押して、**再生**ホログラムをプレビューする Unity でボタンをクリックします。
* キーを押して**再生**をもう一度プレビュー モードを停止します。

**Visual Studio Unity からプロジェクトにエクスポートします。**
* Unity の select で**ファイル > Build Settings**します。
* をクリックして**開くシーンを追加**シーンを追加します。
* 選択**ユニバーサル Windows プラットフォーム**で、**プラットフォーム**を一覧表示し、クリックして**スイッチ プラットフォーム**します。
* 設定**SDK**に**ユニバーサル 10**します。
* 設定**ターゲット デバイス**に**HoloLens**と**UWP ビルド タイプ**に**D3D**します。
* 確認**UnityC#プロジェクト**します。
* **[Build]** をクリックします。
* ファイル エクスプ ローラー ウィンドウが表示されますが、作成、**新しいフォルダー** "App"という名前です。
* 1 回のクリック、**アプリ**フォルダー。
* キーを押して**フォルダーを選択します**します。
* Unity を完了すると、ファイル エクスプ ローラー ウィンドウが表示されます。
* 開く、**アプリ**フォルダー。
* 開いている**SharedHolograms.sln** Visual Studio を起動します。
* デバッグからターゲットを変更する Visual Studio で、上部のツールバーを使用して**リリース**を ARM から**X86**します。
* ローカル コンピューターの横にあるドロップダウン矢印をクリックし、**リモート デバイス**します。
    * 設定、**アドレス**HoloLens の IP アドレス、名前にします。 デバイスの IP アドレスがわからない場合に参照**設定 > ネットワークとインターネット > 詳細オプション**Cortana に質問してまたは **」「コルタナさん自分の IP アドレスは何ですか?**
    * ままに、**認証モード**設定**ユニバーサル**します。
    * クリックして**を選択します**
* クリックして**デバッグ > デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。 最初に、デバイスに展開するには、する必要があります[Visual Studio をペアリング](using-visual-studio.md#pairing-your-device-hololens)します。
* EnergyHub ホログラム、HoloLens の配置を見つけてください。

## <a name="chapter-2---interaction"></a>第 2 章 – 相互作用

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

この章で、ホログラムを操作します。 最初に、視覚化するためのカーソルが追加、[視線](gaze.md)します。 次に、追加します[ジェスチャ](gestures.md)手の形を使用して、ホログラムを領域に配置するとします。

### <a name="objectives"></a>目標

* カーソルを制御する入力視線の先を使用します。
* ホログラムと対話する入力ジェスチャを使用します。

### <a name="instructions"></a>手順

**視線入力**
* **階層パネル**選択、 **HologramCollection**オブジェクト。
* **インスペクター パネル** をクリックして、**コンポーネントの追加**ボタンをクリックします。
* メニューで、検索ボックスに入力**視線 Manager**します。 検索結果を選択します。
* **HoloToolkit 共有 240\Prefabs\Input**フォルダー、検索、**カーソル**資産。
* ドラッグ アンド ドロップ、**カーソル**上に資産、**階層**します。

**ジェスチャ**
* **階層パネル**選択、 **HologramCollection**オブジェクト。
* をクリックして**コンポーネントの追加**と種類**ジェスチャ マネージャー**検索フィールドにします。 検索結果を選択します。
* **階層パネル**、展開**HologramCollection**します。
* 子を選択**EnergyHub**オブジェクト。
* **インスペクター パネル** をクリックして、**コンポーネントの追加**ボタンをクリックします。
* メニューで、検索ボックスに入力**ホログラム配置**します。 検索結果を選択します。
* シーンを選択して保存**ファイル > Save Scene**します。

**展開し、利用**
* 構築し、前の章の手順を使用して、HoloLens にデプロイします。
* アプリが起動して、HoloLens、頭の中を移動、EnergyHub が、視線の先を追跡する方法に注意してください。
* カーソルの場合、ホログラム時にこれが表示されますおよびホログラムでない gazing とポイント ライトに変更確認します。
* ホログラムを配置するエア タップを実行します。 プロジェクト内のこの時点でのみホログラムを 1 回 (もう一度お試しに再デプロイ) を配置することができます。

## <a name="chapter-3---shared-coordinates"></a>第 3 章 - 共有座標します。

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

楽しくホログラムで表示し、操作するですが、さらに見ていきましょう。 最初共有経験にまとめて確認できるホログラムを設定します。

### <a name="objectives"></a>目標

* 共有のエクスペリエンスのためのネットワークをセットアップします。
* 一般的な参照ポイントを確立します。
* 座標系は、デバイス間で共有します。
* すべてのユーザーには、同じホログラムが表示されます。

>[!NOTE]
>**InternetClientServer**と**PrivateNetworkClientServer**共有サーバーに接続するアプリの機能を宣言する必要があります。 これを行うことを既にホログラム 240 が独自のプロジェクトに注意してください。 保存しておきます。
>1. Unity エディターは、「> プロジェクトの設定 > プレーヤーの編集」に移動して、player の設定に移動します。
>2. "Windows Store" タブをクリックします。
>3. 「発行の設定 > 機能」セクションでは、確認、 **InternetClientServer**機能と**PrivateNetworkClientServer**機能

### <a name="instructions"></a>手順

* **プロジェクト パネル**に移動し、 **HoloToolkit 共有 240\Prefabs\Sharing**フォルダー。
* ドラッグ アンド ドロップ、**共有**にプレハブ、**階層パネル**します。

次に、共有サービスを起動する必要があります。 のみ**1 台の PC**共有で発生するこの手順を実行する必要があります。
* Unity - の上のメニューの選択、 **HoloToolkit 共有 240 メニュー**します。
* 選択、**共有サービスの起動**ドロップダウン リスト内の項目。
* チェック、**プライベート ネットワーク**オプションを選択し、をクリックして**アクセスを許可する**ファイアウォール プロンプトが表示されます。
* 共有サービスのコンソール ウィンドウに表示される IPv4 アドレスをメモします。 これは、上、サービスが実行されているマシンと同じ ip アドレスです。

残りの手順に従って、**すべての Pc**共有エクスペリエンスに参加します。
* **階層**を選択、**共有**オブジェクト。
* **インスペクター**の**共有ステージ**コンポーネント、変更、**サーバー アドレス**SharingService.exe を実行しているコンピューターの IPv4 アドレスに 'localhost' から。
* **階層**選択、 **HologramCollection**オブジェクト。
* **インスペクター**クリックして、**コンポーネントの追加**ボタンをクリックします。
* 検索ボックスに「**インポート エクスポート アンカー マネージャー**します。 検索結果を選択します。
* **プロジェクト パネル**に移動し、**スクリプト**フォルダー。
* ダブルクリックして、 **HologramPlacement**スクリプトを Visual Studio で開きます。
* 内容を次のコードに置き換えます。

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;
        
        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* Unity でバックアップを選択、 **HologramCollection**で、**階層パネル**します。
* **インスペクター パネル** をクリックして、**コンポーネントの追加**ボタンをクリックします。
* メニューで、検索ボックスに入力**アプリ状態マネージャー**します。 検索結果を選択します。

**展開し、利用**
* HoloLens デバイス プロジェクトをビルドします。
* 最初に展開する 1 つの HoloLens を指定します。 アンカー、EnergyHub を配置する前に、サービスにアップロードするを待機する必要があります (かかることが最大で 30 ~ 60 秒)。 アップロードが完了するまで、タップ ジェスチャは無視されます。
* EnergyHub を配置した後の場所は、サービスにアップロードして、し、他のすべての HoloLens デバイスに展開することができます。
* 新しい HoloLens 最初に参加させるとき、セッション、EnergyHub の場所をそのデバイスに正しいできない可能性があります。 ただし、アンカーと EnergyHub 場所をサービスからダウンロードすると、すぐ、EnergyHub は、新しい共有の場所にジャンプする必要があります。 30 ~ 60 内でこれが発生しない場合 (秒単位) は、複数の環境の手がかりを収集するためにアンカーを設定するときの元の HoloLens がについて説明します。 場所はロックしない場合、デバイスへの再デプロイします。
* デバイスがすべて準備完了と、EnergyHub を探して、アプリが実行されます。 ホログラムの場所に同意できるすべての方向、テキストが直面しているとしますか?

## <a name="chapter-4---discovery"></a>第 4 章 - 検出

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

同じホログラムを確認できるようになりました。 ここでそれ以外の場合、共有 holographic 世界に接続されているすべてのユーザーを見てみましょう。 この章で、ヘッドの場所と同じ共有セッションで他のすべての HoloLens デバイスの回転角度を取得します。

### <a name="objectives"></a>目標

* 共有の経験には、互いを検出します。
* 選択して、プレーヤーのアバターを共有します。
* すべてのユーザーの頭の横にある player アバターをアタッチします。

### <a name="instructions"></a>手順

* **プロジェクト パネル**に移動し、**ホログラム**フォルダー。
* ドラッグ アンド ドロップ、 **PlayerAvatarStore**に、**階層**します。
* **プロジェクト パネル**に移動し、**スクリプト**フォルダー。
* ダブルクリックして、 **AvatarSelector**スクリプトを Visual Studio で開きます。
* 内容を次のコードに置き換えます。

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);        
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* **階層**選択、 **HologramCollection**オブジェクト。
* **インスペクター**クリックして**コンポーネントの追加**します。
* 検索ボックスに「**ローカル Player Manager**します。 検索結果を選択します。
* **階層**選択、 **HologramCollection**オブジェクト。
* **インスペクター**クリックして**コンポーネントの追加**します。
* 検索ボックスに「**リモート Player Manager**します。 検索結果を選択します。
* 開く、 **HologramPlacement** Visual Studio でのスクリプト。
* 内容を次のコードに置き換えます。

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* 開く、 **AppStateManager** Visual Studio でのスクリプト。
* 内容を次のコードに置き換えます。

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

**展開し、利用**
* ビルドし、プロジェクト、HoloLens デバイスをデプロイします。
* Ping の音が聞こえるようにする場合は、選択メニューのアバターを見つけてエア タップ ジェスチャにアバターを選択します。
* サービスと通信している場合、HoloLens、ライト、カーソルの周囲のポイントが別の色に場合は、ホログラムが表示されていません: (濃い紫) の初期化中、インポート/エクスポートの場所データ (黄)、アンカー (緑) のダウンロードアンカー (青) をアップロードしています。 カーソルの周囲のライト、ポイントが既定の色 (明るい紫) の場合は、セッションで他のプレーヤーと対話できる状態には!
* 他のユーザーを見て、領域 - に接続されているがある holographic ロボットの肩の上に浮動小数点と、ヘッドの動きを模倣します。

## <a name="chapter-5---placement"></a>第 5 章 - 配置

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

この章では、アンカーの実際の画面に配置することをしましょう。 共有のエクスペリエンスに接続されているすべてのユーザーの間の中間点でそのアンカーを配置するのに共有の座標を使用します。

### <a name="objectives"></a>目標

* プレーヤーのヘッドの位置に基づく空間マップ ホログラムを配置します。

### <a name="instructions"></a>手順

* **プロジェクト パネル**に移動し、**ホログラム**フォルダー。
* ドラッグ アンド ドロップ、 **CustomSpatialMapping**にプレハブ、**階層**します。
* **プロジェクト パネル**に移動し、**スクリプト**フォルダー。
* ダブルクリックして、 **AppStateManager**スクリプトを Visual Studio で開きます。
* 内容を次のコードに置き換えます。

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to 
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a 
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* **プロジェクト パネル**に移動し、**スクリプト**フォルダー。
* ダブルクリックして、 **HologramPlacement**スクリプトを Visual Studio で開きます。
* 内容を次のコードに置き換えます。

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the 
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

**展開し、利用**
* ビルドし、プロジェクト、HoloLens デバイスをデプロイします。
* アプリの準備ができたら、円でし、EnergyHub がすべてのユーザーの中央に表示する方法に注意してください。
* EnergyHub を配置する をタップします。
* ホログラムを新しい場所に移動するには、音声コマンドをバックアップ、EnergyHub を選択し、グループとして連携して動作する 'ターゲットのリセット' を再試行してください。

## <a name="chapter-6---real-world-physics"></a>第 6 章 - 実際の物理運動

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

この章では、現実世界のサーフェスから跳ね返りますホログラムを追加します。 プロジェクトを開始して、友人の両方でいっぱいに自分のスペースをご覧ください。

### <a name="objectives"></a>目標

* 実際のサーフェスから跳ね返ります弾丸を起動します。
* 他のプレイヤーが確認できるように、弾丸を共有します。

### <a name="instructions"></a>手順

* **階層**選択、 **HologramCollection**オブジェクト。
* **インスペクター**クリックして**コンポーネントの追加**します。
* 検索ボックスに「**の光線ランチャー**します。 検索結果を選択します。

**展開し、利用**
* ビルドして、HoloLens デバイスに展開します。
* アプリは、すべてのデバイスで実行中は、現実世界のサーフェスでの光線を起動するエア タップを実行します。
* 別のプレーヤーのアバターの光線競合したときの動作を参照してください。

## <a name="chapter-7---grand-finale"></a>第 7 章 – フィナーレ

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

この章で、共同作業でのみ検出可能なポータルが明らかにします。

### <a name="objectives"></a>目標

* シークレットのポータルを明らかにするためのアンカーに十分な弾丸を起動するには、共同作業します。

### <a name="instructions"></a>手順

* **プロジェクト パネル**に移動し、**ホログラム**フォルダー。
* ドラッグ アンド ドロップ、**黄泉**資産として、 **HologramCollection の子**します。
* **HologramCollection**選択すると、をクリックして、**コンポーネントの追加**ボタン、**インスペクター**します。
* メニューで、検索ボックスに入力**ExplodeTarget**します。 検索結果を選択します。
* **HologramCollection**から、選択した、**階層**ドラッグ、 **EnergyHub**オブジェクトを**ターゲット**フィールドに、 **インスペクター**します。
* **HologramCollection**から、選択した、**階層**ドラッグ、**黄泉**オブジェクトを**黄泉**フィールド**Inspector**します。

**展開し、利用**
* ビルドして、HoloLens デバイスに展開します。
* アプリの起動時に、EnergyHub 弾丸を起動する共同します。
* 黄泉が表示されたら、弾丸黄泉ロボット (ヒット、ロボットを 3 回の楽し) でを起動します。
