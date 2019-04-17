---
title: MR 基本 101E のエミュレーターを使用した完全なプロジェクト
description: このコーディング holographic アプリケーションの基礎を習得する Unity、Visual Studio および HoloLens のエミュレーターの使用に関するチュートリアルに従います。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、複合現実、ホログラム、academy、チュートリアル、エミュレーター
ms.openlocfilehash: 77f7d497396937bf471a69fa514cef84ab0b699d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599404"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。  そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。  これらのチュートリアルは**_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。  サポートされているデバイスで作業を続行するが保持されます。 一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。  この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a>MR 基礎 101E:エミュレーターを使用した完全なプロジェクト

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

このチュートリアルでは、HoloLens などのコア Windows Mixed Reality 機能を示すには、Unity でビルドされた完全なプロジェクトを通じて[視線](gaze.md)、[ジェスチャ](gestures.md)、[音声入力](voice-input.md)、[空間サウンド](spatial-sound.md)と[空間マッピング](spatial-mapping.md)します。 このチュートリアルを完了するには約 1 時間になります。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td>MR 基礎 101E:エミュレーターを使用した完全なプロジェクト</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>開始前の作業

### <a name="prerequisites"></a>前提条件

* 正しく構成されている Windows 10 PC[ツールがインストールされている](install-the-tools.md)します。

### <a name="project-files"></a>プロジェクト ファイル

* ダウンロード、[ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip)プロジェクトに必要です。 Unity 2017.2 またはそれ以降が必要です。
  * Unity 5.6 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)します。
  * Unity 5.5 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)します。
  * Unity 5.4 のサポートを引き続き必要がある場合を使用してください[このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)します。
* 解除アーカイブをデスクトップまたは場所に到達する簡単なその他のファイル。 フォルダー名として保持**Origami**します。

>[!NOTE]
>をダウンロードする前に、ソース コードを検索する場合がある[GitHub で入手できます](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)します。

## <a name="chapter-1---holo-world"></a>第 1 章 -"Holo"world

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

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
* 新しいシーンを保存します。**ファイル** / **としてシーンを保存**します。
* シーンという名前を**Origami**キーを押すと、**保存**ボタンをクリックします。

#### <a name="setup-the-main-camera"></a>メイン カメラのセットアップ

* **階層パネル**、 **Main Camera**します。
* **インスペクター**にトランス フォームの位置を設定**0,0,0**します。
* 検索、**フラグをクリア**プロパティ、ドロップダウン リストからの変更と**スカイ ボックス**に**純色**。
* をクリックして、**バック グラウンド**フィールドをカラー ピッカーを開きます。
* 設定**R、G、B、および A**に**0**します。

#### <a name="setup-the-scene"></a>シーンのセットアップ

* **階層パネル**、 をクリックして**作成**と**空アイテムの作成**です。
* 新しい右クリックして**GameObject**名前の変更を選択します。 GameObject の名前を変更**OrigamiCollection**します。
* **ホログラム**フォルダーで、**プロジェクト パネル**:
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
* 選択**Windows ストア**で、**プラットフォーム**を一覧表示し、をクリックして**スイッチ プラットフォーム**します。
* 設定**SDK**に**ユニバーサル 10**と**ビルドの種類**に**D3D**します。
* 確認**UnityC#プロジェクト**します。
* をクリックして**開くシーンを追加**シーンを追加します。
* クリックして**プレーヤー設定しています.**.
* Inspector パネルの選択で、 **Windows ストア ロゴ**します。 選び**公開設定**します。
* **機能**セクションで、**マイク**と**SpatialPerception**機能します。
* ビルドの詳細設定 ウィンドウに戻り**ビルド**します。
* 作成、**新しいフォルダー** "App"という名前です。
* 1 回のクリック、**アプリ フォルダー**します。
* キーを押して**フォルダーを選択します**します。
* Unity を完了すると、ファイル エクスプ ローラー ウィンドウが表示されます。
* 開く、**アプリ**フォルダー。
* 開く、 **Origami Visual Studio ソリューション**します。
* デバッグからターゲットを変更する Visual Studio で、上部のツールバーを使用して**リリース**を ARM から**X86**します。
  * デバイスのボタンの横の矢印をクリックし、 **HoloLens のエミュレーター**します。
  * クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。
  * しばらくエミュレーター折り紙プロジェクトで開始されます。 最初に起動するときに、[エミュレーター](using-the-hololens-emulator.md)エミュレーターが起動までに 15 分の時間がかかることができます。 起動した場合は閉じないでください。

## <a name="chapter-2---gaze"></a>第 2 章 – 視線入力

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

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

            // Move thecursor to the point where the raycast hit.
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
* 以前はエミュレーターにデプロイするために使用する Visual Studio ソリューションに戻ります。
* 'すべて再読み込み' が表示されたら選択します。
* クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。
* Xbox コント ローラーを使用して、シーンを中心になります。 カーソルがオブジェクトの形状と対話する方法に注意してください。

## <a name="chapter-3---gestures"></a>第 3 章 - ジェスチャ

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

この章では、サポートを追加します[ジェスチャ](gestures.md)します。 ユーザーは、ホワイト ペーパーの球体を選択するときに、Unity の物理運動エンジンを使用して重力を有効にして分類、球体にしましょう。

### <a name="objectives"></a>目標

* ジェスチャに、ホログラムを制御します。

### <a name="instructions"></a>手順

選択ジェスチャを検出できるよりもスクリプトの作成から始めます。

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
    void Start()
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

* エクスポートし、ビルド、HoloLens のエミュレーターにアプリを展開します。
* シーン、少し調べてみるし、球の 1 つの中央します。
* キーを押して、 **A** Xbox コント ローラーでボタンをクリックしてまたは選択ジェスチャをシミュレートするために Space キーを押します。

## <a name="chapter-4---voice"></a>第 4 章 - 音声

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

この章では、2 つのサポートを追加します[音声コマンド](voice-input.md):"リセット world"には、元の場所にドロップされた球体と"ドロップ sphere"を返します、球体を分類します。

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

* エクスポートし、ビルド、HoloLens のエミュレーターにアプリを展開します。
* エミュレーターを PC のマイクをサポートし、音声応答: 球体のいずれかの上にカーソルが、表示を調整し、"ドロップ Sphere"。
* たとえば"**世界のリセット**"最初の位置に戻すにします。

## <a name="chapter-5---spatial-sound"></a>第 5 章 - 空間のサウンド

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

この章で、アプリに音楽を追加し、特定のアクションでのサウンド効果をトリガーします。 使用する[空間サウンド](spatial-sound.md)サウンド 3D 空間で特定の場所を提供します。

### <a name="objectives"></a>目標

* 世界でホログラムお話しします。

### <a name="instructions"></a>手順

* 上部のメニューから Unity の選択で**編集 > プロジェクトの設定 > オーディオ**
* 検索、**立体音場プラグイン**設定および  **MS HRTF 立体音場**します。
* **ホログラム**フォルダー、ドラッグ、**アンビエンス**オブジェクト、 **OrigamiCollection**階層パネル内のオブジェクト。
* 選択**OrigamiCollection**を見つけて、**オーディオ ソース**コンポーネント。 これらのプロパティを変更します。
  * チェック、 **Spatialize**プロパティ。
  * チェック、**起動状態で再生**します。
  * 変更**空間 Blend**に**3D**に右側のスライダーをドラッグしています。
  * チェック、**ループ**プロパティ。
  * 展開**3D サウンド設定**、入力と**0.1**の**ドップラー レベル**します。
  * 設定**ボリューム ロールオフ**に**対数ロールオフ**します。
  * 設定**最大距離**に**20**します。
* **スクリプト**フォルダー、という名前のスクリプト作成**SphereSounds**します。
* ドラッグ**SphereSounds**を**Sphere1**と**Sphere2**階層内のオブジェクト。
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
* エクスポートし、ビルド、HoloLens のエミュレーターにアプリを展開します。
* 完全な効果を取得し、サウンドを変更するステージから離れたと緊密に移動、ヘッドホンを着用します。

## <a name="chapter-6---spatial-mapping"></a>第 6 章 - 空間のマッピング

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

ここでは、使用する[空間マッピング](spatial-mapping.md)現実の世界での実際のオブジェクトにゲーム ボードを配置します。

### <a name="objectives"></a>目標

* 仮想世界に、現実の世界を表示します。
* ここが最も重要なホログラムを配置します。

### <a name="instructions"></a>手順

* をクリックして、**ホログラム**プロジェクト パネル内のフォルダー。
* ドラッグ、**空間マッピング**のルートに資産、**階層**します。
* をクリックして、**空間マッピング**階層内のオブジェクト。
* **インスペクター パネル**、次のプロパティを変更します。
  * チェック、 **Visual メッシュの描画**ボックス。
  * 検索**描画マテリアル**右側の円をクリックします。 型"**ワイヤー フレーム**"上部にある検索フィールドにします。 [結果] をクリックし、ウィンドウを閉じます。
* エクスポートし、ビルド、HoloLens のエミュレーターにアプリを展開します。
* アプリの実行時に以前スキャンされた実際のリビング ルームのメッシュをワイヤー フレームでレンダリングされます。
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
* Gazing ことによって、特定の場所にゲームを配置できるようになりましたに、ここでは選択ジェスチャを使用して (**A**または space キーを押す)、新しい場所に移動して、もう一度選択ジェスチャを使用します。

## <a name="the-end"></a>最後です

このチュートリアルは終わりです。

学習内容。

* Unity で holographic アプリを作成する方法。
* 作成する方法の視線、ジェスチャ、音声、サウンド、および空間マッピングを使用します。
* ビルドして、Visual Studio を使用してアプリをデプロイする方法。

Holographic アプリの作成を開始する準備が整いました。

## <a name="see-also"></a>関連項目

* [MR 基礎 101:デバイスとの完全なプロジェクト](holograms-101.md)
* [視線入力](gaze.md)
* [ジェスチャ](gestures.md)
* [音声入力](voice-input.md)
* [空間のサウンド](spatial-sound.md)
* [空間マッピング](spatial-mapping.md)
