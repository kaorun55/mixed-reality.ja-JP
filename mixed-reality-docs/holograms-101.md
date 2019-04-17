---
title: MR 基本 101 - デバイスでの完全なプロジェクト
description: Unity、Visual Studio および HoloLens を使用して、Windows Mixed Reality の基本を学習するこのコーディング チュートリアルに従ってください。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: 実際には、Windows Mixed Reality、HoloLens、混合ホログラム, academy, チュートリアル
ms.openlocfilehash: 043ffac8f30a4e29586478b5dca6ecccc2b5afd3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599361"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。  そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。  これらのチュートリアルは**_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。  サポートされているデバイスで作業を続行するが保持されます。 一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。  この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。

<br>

# <a name="mr-basics-101-complete-project-with-device"></a>MR 基礎 101:デバイスとの完全なプロジェクト

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

このチュートリアルでは、HoloLens などのコア Windows Mixed Reality 機能を示すには、Unity でビルドされた完全なプロジェクトを通じて[視線](gaze.md)、[ジェスチャ](gestures.md)、[音声入力](voice-input.md)、[空間サウンド](spatial-sound.md)と[空間マッピング](spatial-mapping.md)します。

このチュートリアルを完了するには約 1 時間になります。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td>MR 基礎 101:デバイスとの完全なプロジェクト</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>開始前の作業

### <a name="prerequisites"></a>前提条件

* 正しく構成されている Windows 10 PC[ツールがインストールされている](install-the-tools.md)します。
* HoloLens デバイス[開発用に構成された](using-visual-studio.md#enabling-developer-mode)します。

### <a name="project-files"></a>プロジェクト ファイル

* ダウンロード、[ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip)プロジェクトに必要です。 Unity 2017.2 またはそれ以降が必要です。
  * Unity 5.6 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)します。
  * Unity 5.5 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)します。
  * Unity 5.4 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)します。
* 解除アーカイブをデスクトップまたは場所に到達する簡単なその他のファイル。 フォルダー名として保持**Origami**します。

>[!NOTE]
>をダウンロードする前に、ソース コードを検索する場合がある[GitHub で入手できます](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)します。

## <a name="chapter-1---holo-world"></a>第 1 章 -"Holo"world

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

この章で、最初の Unity プロジェクトとビルド手順のセットアップがされプロセスを展開します。

### <a name="objectives"></a>目標

* Holographic 開発のために、Unity を設定します。
* ホログラムを確認します。
* 行ったホログラムを参照してください。

### <a name="instructions"></a>手順

* Unity を起動します。
* **[開く]** を選択します。
* として場所を入力、 **Origami**フォルダー アーカイブされた以前のことです。
* 選択**Origami**クリック**フォルダーの選択**。
* 以降、 **Origami**プロジェクトに空の既定のシーンを使用して新しいファイルに保存、シーンが含まれていません。**ファイル** / **としてシーンを保存**します。
* 新しいシーンを名前**Origami**キーを押すと、**保存**ボタンをクリックします。

#### <a name="setup-the-main-virtual-camera"></a>メインの仮想のカメラのセットアップ

* **階層パネル**、 **Main Camera**します。
* **インスペクター**にトランス フォームの位置を設定**0,0,0**します。
* 検索、**フラグをクリア**プロパティ、ドロップダウン リストからの変更と**スカイ ボックス**に**純色**。
* をクリックして、**バック グラウンド**フィールドをカラー ピッカーを開きます。
* 設定**R、G、B、および A**に**0**します。

#### <a name="setup-the-scene"></a>シーンのセットアップ

* **階層パネル**、 をクリックして**作成**と**空アイテムの作成**です。
* 新しい右クリックして**GameObject**名前の変更を選択します。 GameObject の名前を変更**OrigamiCollection**します。
* **ホログラム**プロジェクト パネル内のフォルダー (資産の展開しホログラムを選択します。 または [プロジェクト] パネルでホログラム フォルダーをダブルクリックします)。
  * ドラッグ**ステージ**の子に階層に**OrigamiCollection**します。
  * ドラッグ**Sphere1**の子に階層に**OrigamiCollection**します。
  * ドラッグ**Sphere2**の子に階層に**OrigamiCollection**します。
* 右クリックし、**指向性光**内のオブジェクト、**階層パネル**選択と**削除**します。
* **ホログラム**フォルダー、ドラッグ**ライト**のルートに、**階層パネル**します。
* **階層**を選択、 **OrigamiCollection**します。
* **インスペクター**、変換の位置を設定**0、-0.5、2.0**します。
* キーを押して、**再生**ホログラムをプレビューする Unity でボタンをクリックします。
* プレビュー ウィンドウの Origami オブジェクトが表示されます。
* キーを押して**再生**をもう一度プレビュー モードを停止します。

#### <a name="export-the-project-from-unity-to-visual-studio"></a>Visual Studio Unity からプロジェクトにエクスポートします。

* Unity の select で**ファイル > Build Settings**します。
* 選択**ユニバーサル Windows プラットフォーム**で、**プラットフォーム**を一覧表示し、クリックして**スイッチ プラットフォーム**します。
* 設定**SDK**に**ユニバーサル 10**と**ビルドの種類**に**D3D**します。
* 確認**UnityC#プロジェクト**します。
* をクリックして**開くシーンを追加**シーンを追加します。
* **[Build]** をクリックします。
* ファイル エクスプ ローラー ウィンドウが表示されますが、作成、**新しいフォルダー** "App"という名前です。
* 1 回のクリック、**アプリ フォルダー**します。
* キーを押して**フォルダーを選択します**します。
* Unity を完了すると、ファイル エクスプ ローラー ウィンドウが表示されます。
* 開く、**アプリ**フォルダー。
* 開く (ダブルクリック) **Origami.sln**します。
* デバッグからターゲットを変更する Visual Studio で、上部のツールバーを使用して**リリース**を ARM から**X86**します。
* デバイスのボタンの横の矢印をクリックし、**リモート マシン**Wi-fi 経由で展開します。
  * 設定、**アドレス**HoloLens の IP アドレス、名前にします。 デバイスの IP アドレスがわからない場合に参照**設定 > ネットワークとインターネット > 詳細オプション**Cortana に質問してまたは **」「コルタナさん自分の IP アドレスは何ですか?**
  * 代わりに選択しますが、HoloLens が USB 経由で接続されている場合**デバイス**USB 経由で展開します。
  * ままに、**認証モード**設定**ユニバーサル**します。
  * クリックして**を選択します**

* クリックして**デバッグ > デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。 最初に、デバイスに展開するには、する必要があります[Visual Studio をペアリング](using-visual-studio.md#pairing-your-device-hololens-(1st-gen))します。

* 折り紙プロジェクトは今すぐ、HoloLens を展開してビルドし、実行します。
* HoloLens にで、新しいホログラムを探します。

## <a name="chapter-2---gaze"></a>第 2 章 – 視線入力

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

この章で、最初の対話の 3 つの方法を紹介するつもりが、ホログラム--で[視線](gaze.md)します。

### <a name="objectives"></a>目標

* 世界中ロックされているカーソルを使用して、視線の先を視覚化します。

### <a name="instructions"></a>手順

* Unity プロジェクトに戻るしがまだ開いている場合は、ビルドの詳細設定 ウィンドウを閉じます。
* 選択、**ホログラム**フォルダーで、**プロジェクト パネル**します。
* ドラッグ、**カーソル**オブジェクトを**階層パネル**ルート レベルにします。
* ダブルクリックして、**カーソル**について詳しく見てを実行するオブジェクト。
* 右クリックし、**スクリプト**プロジェクト パネル内のフォルダー。
* をクリックして、**作成** をクリックします。
* 選択**C#スクリプト**します。
* スクリプトの名前**WorldCursor**します。 注:この名前では、大文字と小文字を区別します。 .Cs 拡張子を追加する必要はありません。
* 選択、**カーソル**オブジェクト、**階層パネル**します。
* ドラッグ アンド ドロップ、 **WorldCursor**にスクリプト、**インスペクター パネル**します。
* ダブルクリックして、 **WorldCursor**スクリプトを Visual Studio で開きます。
* このコードをコピーして**WorldCursor.cs**と**すべて保存**します。

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move the cursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* アプリをリビルド**ファイル > のビルド設定**します。
* 以前、HoloLens を展開するために使用する Visual Studio ソリューションに戻ります。
* 'すべて再読み込み' が表示されたら選択します。
* クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。
* ここでシーンを中心になり、カーソルがオブジェクトの形状と対話する方法に注意してください。

## <a name="chapter-3---gestures"></a>第 3 章 - ジェスチャ

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

この章では、サポートを追加します[ジェスチャ](gestures.md)します。 ユーザーは、ホワイト ペーパーの球体を選択するときに、Unity の物理運動エンジンを使用して重力を有効にして分類、球体にしましょう。

### <a name="objectives"></a>目標

* ジェスチャに、ホログラムを制御します。

### <a name="instructions"></a>手順

スクリプトの作成から始めます続いて選択ジェスチャを検出することができます。

* **スクリプト**フォルダー、という名前のスクリプト作成**GazeGestureManager**します。
* ドラッグ、 **GazeGestureManager**にスクリプト、 **OrigamiCollection**階層内のオブジェクト。
* 開く、 **GazeGestureManager** Visual Studio でスクリプトを作成し、次のコードを追加します。

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Awake()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* Scripts フォルダーでは、という名前のこの時点で別のスクリプトを作成**SphereCommands**します。
* 展開、 **OrigamiCollection**階層ビュー内のオブジェクト。
* ドラッグ、 **SphereCommands**にスクリプト、 **Sphere1**階層パネル内のオブジェクト。
* ドラッグ、 **SphereCommands**にスクリプト、 **Sphere2**階層パネル内のオブジェクト。
* 編集に関しては、Visual Studio でスクリプトを開くし、この既定のコードに置き換えます。

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* エクスポートし、ビルド、HoloLens にアプリを展開します。
* 球体は一層のいずれかを確認します。
* 選択ジェスチャを実行し、次の画面にドロップ球を確認します。

## <a name="chapter-4---voice"></a>第 4 章 - 音声

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

この章では、2 つのサポートを追加します[音声コマンド](voice-input.md):"リセット world"には、元の場所にドロップされた球体を返し、「球体をドロップ」分類球を作成します。

### <a name="objectives"></a>目標

* バック グラウンドでは、常にリッスンする音声コマンドを追加します。
* 音声コマンドに応答するホログラムを作成します。

### <a name="instructions"></a>手順

* **スクリプト**フォルダー、という名前のスクリプト作成**SpeechManager**します。
* ドラッグ、 **SpeechManager**にスクリプト、 **OrigamiCollection**階層内のオブジェクト
* 開く、 **SpeechManager** Visual Studio でのスクリプト。
* このコードをコピーして**SpeechManager.cs**と**すべて保存**:

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* 開く、 **SphereCommands** Visual Studio でのスクリプト。
* 次のようにスクリプトを更新します。

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* エクスポートし、ビルド、HoloLens にアプリを展開します。
* 球体のいずれかを確認し、"**球のドロップ**"。
* たとえば"**世界のリセット**"最初の位置に戻すにします。

## <a name="chapter-5---spatial-sound"></a>第 5 章 - 空間のサウンド

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

この章で、アプリに音楽を追加し、特定のアクションでのサウンド効果をトリガーします。 使用する[空間サウンド](spatial-sound.md)サウンド 3D 空間で特定の場所を提供します。

### <a name="objectives"></a>目標

* 世界でホログラムお話しします。

### <a name="instructions"></a>手順

* 上部のメニューから選択する Unity で**編集 > プロジェクトの設定 > オーディオ**
* 右側にある Inspector パネルで、検索、**立体音場プラグイン**設定および  **MS HRTF 立体音場**します。
* **ホログラム**プロジェクト パネルで、フォルダーをドラッグ、**アンビエンス**オブジェクト、 **OrigamiCollection**階層パネル内のオブジェクト。
* 選択**OrigamiCollection**を見つけて、**オーディオ ソース**インスペクター パネルの コンポーネント。 これらのプロパティを変更します。
  * チェック、 **Spatialize**プロパティ。
  * チェック、**起動状態で再生**します。
  * 変更**空間 Blend**に**3D**に右側のスライダーをドラッグしています。 値は、スライダーを移動するときに 0 から 1 に変更する必要があります。
  * チェック、**ループ**プロパティ。
  * 展開**3D サウンド設定**、入力と**0.1**の**ドップラー レベル**します。
  * 設定**ボリューム ロールオフ**に**対数ロールオフ**します。
  * 設定**最大距離**に**20**します。
* **スクリプト**フォルダー、という名前のスクリプト作成**SphereSounds**します。
* ドラッグ アンド ドロップ**SphereSounds**を**Sphere1**と**Sphere2**階層内のオブジェクト。
* 開いている**SphereSounds** Visual Studio で、次のコードを更新および**すべて保存**します。

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* スクリプトを保存し、Unity に戻ります。
* エクスポートし、ビルド、HoloLens にアプリを展開します。
* 近いとステージからかけ離れていますに移動し、サウンドを変更する並列を有効にします。

## <a name="chapter-6---spatial-mapping"></a>第 6 章 - 空間のマッピング

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

ここでは、使用する[空間マッピング](spatial-mapping.md)現実の世界での実際のオブジェクトにゲーム ボードを配置します。

### <a name="objectives"></a>目標

* 仮想世界に、現実の世界を表示します。
* ここが最も重要なホログラムを配置します。

### <a name="instructions"></a>手順

* Unity では、クリックして、**ホログラム**プロジェクト パネル内のフォルダー。
* ドラッグ、**空間マッピング**のルートに資産、**階層**します。
* をクリックして、**空間マッピング**階層内のオブジェクト。
* **インスペクター パネル**、次のプロパティを変更します。
  * チェック、 **Visual メッシュの描画**ボックス。
  * 検索**描画マテリアル**右側の円をクリックします。 型"**ワイヤー フレーム**"上部にある検索フィールドにします。 [結果] をクリックし、ウィンドウを閉じます。 これを行うときに、描画マテリアルの値は、ワイヤー フレームに設定を取得する必要があります。
* エクスポートし、ビルド、HoloLens にアプリを展開します。
* アプリを実行すると、ワイヤー フレーム メッシュは、現実の世界をオーバーレイします。
* この段階では、オフと床のローリング球はフォールバックをご覧ください。

現在、OrigamiCollection を新しい場所に移動する方法について説明します。

* **スクリプト**フォルダー、という名前のスクリプト作成**TapToPlaceParent**します。
* **階層**、展開、 **OrigamiCollection**を選択し、**ステージ**オブジェクト。
* ドラッグ、 **TapToPlaceParent**ステージ オブジェクトのスクリプト。
* 開く、 **TapToPlaceParent** Visual Studio でスクリプトを作成し、次に更新します。

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* ビルドをエクスポート、およびアプリを展開します。
* 今すぐに gazing、選択ジェスチャを使用して、新しい場所に移動しもう一度選択ジェスチャを使用して、特定の場所にゲームを配置できる必要がありますなります。

## <a name="chapter-7---holographic-fun"></a>第 7 章 – Holographic 楽しい

### <a name="objectives"></a>目標

* Holographic 黄泉の入り口を明らかになります。

### <a name="instructions"></a>手順

これを holographic 黄泉を明らかにする方法について説明します。

* **ホログラム**プロジェクト パネル内のフォルダー。
  * ドラッグ**黄泉**の子に階層に**OrigamiCollection**します。
* **スクリプト**フォルダー、という名前のスクリプト作成**HitTarget**します。
* **階層**、展開、 **OrigamiCollection**します。
* 展開、**ステージ**オブジェクトし、選択、**ターゲット**オブジェクト (青の展開)。
* ドラッグ、 **HitTarget**にスクリプト、**ターゲット**オブジェクト。
* 開く、 **HitTarget** Visual Studio でスクリプトを作成し、次に更新します。

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* Unity では、選択、**ターゲット**オブジェクト。
* 2 つのパブリック プロパティに表示されます、**ヒット ターゲット**コンポーネントと、シーン内のオブジェクトを参照する必要があります。
  * ドラッグ**黄泉**から、**階層**パネル、**黄泉**プロパティを**ヒット ターゲット**コンポーネント。
  * ドラッグ**ステージ**から、**階層**パネル、**オブジェクトを非表示にする**プロパティを**ヒット ターゲット**コンポーネント。
* ビルドをエクスポート、およびアプリを展開します。
* Origami コレクションをフロアに置き、選択ジェスチャを使用してドロップ球にします。
* 球に達すると、ターゲット (青の展開)、展開が発生します。 コレクションを非表示にして、黄泉に穴が表示されます。

## <a name="the-end"></a>最後です

このチュートリアルは終わりです。

学習内容。

* Unity で holographic アプリを作成する方法。
* 作成する方法、視線、ジェスチャ、音声、サウンドの使用と空間マッピング。
* ビルドして、Visual Studio を使用してアプリをデプロイする方法。

独自のホログラフィック操作の作成を開始する準備が整いました。

## <a name="see-also"></a>関連項目

* [MR 基礎 101E:エミュレーターを使用した完全なプロジェクト](holograms-101e.md)
* [視線入力](gaze.md)
* [ジェスチャ](gestures.md)
* [音声入力](voice-input.md)
* [空間のサウンド](spatial-sound.md)
* [空間マッピング](spatial-mapping.md)
