---
title: MR 入力 211 のジェスチャ
description: ジェスチャの概念の詳細については、Unity、Visual Studio は、HoloLens を使用してこのコーディング チュートリアルに従ってください。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit unity、academy、チュートリアルでは、ジェスチャ
ms.openlocfilehash: 76d2b4c0ac3d0a3783b091f7dc8c39548a18b548
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603386"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。  そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。  これらのチュートリアルは**_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。  サポートされているデバイスで作業を続行するが保持されます。 一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。  この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。

# <a name="mr-input-211-gesture"></a>MR 入力 211:ジェスチャ

[ジェスチャ](gestures.md)をアクションにユーザーの意図を変換します。 ジェスチャでは、ユーザーはホログラムと対話できます。 このコースでユーザーの手を追跡、ユーザーの入力に応答する方法について説明し、ユーザーに与えるフィードバック ベースの一方で状態と位置。

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

[MR 基本 101](holograms-101.md)、単純なエア タップ ジェスチャを使用して、ホログラムと対話します。 ここで、エア タップのジェスチャだけにとどまらないし、新しい概念を検証します。、

* ユーザーの手が追跡されていることを検出し、ユーザーにフィードバックを提供します。
* ホログラムを回転するのにには、ナビゲーションのジェスチャを使用します。
* ユーザーの手がビューの外に出るときに、フィードバックを提供します。
* 操作イベントを使用して、自分の手でホログラムを移動します。

このコースで Unity プロジェクトを再度**モデル エクスプ ローラー**に組み込まれています[MR 入力 210](holograms-210.md)します。 「宇宙飛行士友人は、これら新しいジェスチャ概念のところ役立ちますに戻っています。

>[!IMPORTANT]
>以前のバージョンの Unity と Mixed Reality Toolkit を使用して、以下の各章に埋め込まれたビデオが記録されています。 詳細な手順については、正確かつ最新ですが、スクリプトとは、無効な対応するビデオの中でビジュアルを表示があります。 ビデオでは、後生のために含まれる保持され、概念説明のため、引き続き適用されます。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td>MR 入力 211:ジェスチャ</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始前の作業

### <a name="prerequisites"></a>前提条件

* 正しく構成されている Windows 10 PC[ツールがインストールされている](install-the-tools.md)します。
* 基本的なC#プログラミング機能。
* 完了する必要があります[MR 基本 101](holograms-101.md)します。
* 完了する必要があります[MR 入力 210](holograms-210.md)します。
* HoloLens デバイス[開発用に構成された](using-visual-studio.md#enabling-developer-mode)します。

### <a name="project-files"></a>プロジェクト ファイル

* ダウンロード、[ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip)プロジェクトに必要です。 Unity 2017.2 またはそれ以降が必要です。
* 解除アーカイブをデスクトップまたは場所に到達する簡単なその他のファイル。

>[!NOTE]
>をダウンロードする前に、ソース コードを検索する場合がある[GitHub で入手できます](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture)します。

### <a name="errata-and-notes"></a>正誤表と注意事項

* 「マイ コードのみを有効にする」無効にする必要があります (*unchecked*) -> ツールの Visual Studio でのオプションには、デバッグ、コードにブレークポイントをヒットするには-> です。

## <a name="chapter-0---unity-setup"></a>0 - Unity のセットアップ」の章

### <a name="instructions"></a>手順

1. Unity を起動します。
2. **[開く]** を選択します。
3. 移動し、**ジェスチャ**フォルダー以前されていないアーカイブします。
4. 検索し、選択、**開始**/**モデル エクスプ ローラー**フォルダー。
5. をクリックして、**フォルダーの選択**ボタンをクリックします。
6. **プロジェクト**パネルで、展開、**シーン**フォルダー。
7. ダブルクリック**ModelExplorer**シーン Unity で読み込めません。

### <a name="building"></a>ビルド

1. Unity では、次のように選択します。**ファイル > Build Settings**します。
2. 場合**シーン/ModelExplorer**に記載されていない**Scenes In Build**、 をクリックして**開くシーンを追加**シーンを追加します。
3. 具体的には、HoloLens の開発中、設定**ターゲット デバイス**に**HoloLens**します。 それ以外の場合、残して**任意のデバイス**します。
4. 確認**ビルド タイプ**に設定されている**D3D**と**SDK**に設定されている**インストールされている最新**(16299 またはそれ以降の SDK がある必要があります)。
5. **[Build]** をクリックします。
6. 作成、**新しいフォルダー** "App"という名前です。
7. 1 回のクリック、**アプリ**フォルダー。
8. キーを押して**フォルダーの選択**Unity は Visual Studio のプロジェクトのビルドを開始します。

Unity を完了すると、ファイル エクスプ ローラー ウィンドウが表示されます。

1. 開く、**アプリ**フォルダー。
2. 開く、 **ModelExplorer Visual Studio ソリューション**します。

HoloLens へのデプロイ: 場合

1. デバッグからターゲットを変更する Visual Studio で、上部のツールバーを使用して**リリース**を ARM から**x86**します。
2. ローカル コンピューター] ボタンの横の矢印のドロップダウンをクリックし、[**リモート マシン**します。
3. 入力**HoloLens デバイスの IP アドレス**認証モードを設定および**ユニバーサル (暗号化されていないプロトコル)** します。 クリックして**選択**します。 デバイスの IP アドレスがわからない場合に参照**設定 > ネットワークとインターネット > 詳細オプション**します。
4. 上部のメニュー バーで、クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。 最初に、デバイスに展開するには、する必要があります[Visual Studio をペアリング](using-visual-studio.md#pairing-your-device-hololens)します。
5. アプリが展開されると、消去、 **Fitbox**で、**ジェスチャ を選択**します。

場合は、イマーシブ ヘッドセットへのデプロイ。

1. デバッグからターゲットを変更する Visual Studio で、上部のツールバーを使用して**リリース**を ARM から**x64**します。
2. 必ず、配置ターゲットに設定されて**ローカル マシン**します。
3. 上部のメニュー バーで、クリックして**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。
4. アプリが展開されると、消去、 **Fitbox**アニメーション コント ローラーで、トリガーを取得することによって。

>[!NOTE]
>Visual Studio でエラー パネルの赤いエラーの一部が分かります。 それらを無視しても安全になります。 ビルドの進行状況を実際に表示する出力パネルへの切り替え。 エラー出力 パネルにでは修正プログラム (ほとんどの多くの場合、スクリプトで間違いに起因) を作成することが必要です。

## <a name="chapter-1---hand-detected-feedback"></a>第 1 章 - 手の形にフィードバックが検出されました

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>目標

* 追跡イベントを渡すためにサブスクライブします。
* 手の形が追跡されているときにユーザーを表示するのにには、カーソルのフィードバックを使用します。

### <a name="instructions"></a>手順

* **階層**パネルで、展開、 **InputManager**オブジェクト。
* 探し、選択、 **GesturesInput**オブジェクト。

**InteractionInputSource.cs**スクリプトは、次の手順を実行します。

1. InteractionSourceDetected と InteractionSourceLost イベントをサブスクライブします。
2. HandDetected 状態を設定します。
3. InteractionSourceDetected と InteractionSourceLost イベントからアンサブスク ライブします。

次に、アップグレード、カーソルから[MR 入力 210](holograms-210.md)フィードバックによって、ユーザーのアクションを示す 1 つにします。

1. **階層**パネルで、**カーソル**オブジェクトし、それを削除します。
2. **プロジェクト**パネルで、検索**CursorWithFeedback**までドラッグし、**階層**パネル。
3. をクリックして**InputManager**で、**階層**をドラッグして、パネル、 **CursorWithFeedback**オブジェクトから、**階層**に、InputManager の**SimpleSinglePointerSelector**の**カーソル**フィールドでは、下部にある、**インスペクター**します。
4. をクリックして、 **CursorWithFeedback**で、**階層**します。
5. **インスペクター**パネルで、展開**カーソル状態データ**上、**オブジェクト カーソル**スクリプト。

**カーソル状態データ**これと同様に動作します。

* すべて**監視**状態の意味は手が検出されなかった場合、ユーザーを探し、単にします。
* すべて**Interact**状態では、手動またはコント ローラーが検出されたことを意味します。
* すべて**ホバー**状態の意味は、ユーザーはホログラム見る。

### <a name="build-and-deploy"></a>構築し、デプロイ

* Unity では、次のように使用します。**ファイル > Build Settings** 、アプリケーションをリビルドします。
* 開く、**アプリ**フォルダー。
* 開くことがまだ開いていない場合、 **ModelExplorer Visual Studio ソリューション**します。
  * (既にビルド/展開して Visual Studio では、このプロジェクトのセットアップ中に場合、し、VS のインスタンスを開いて 'すべて再読み込み' が表示されたらクリックします)。
* Visual Studio で、次のようにクリックします。**デバッグ]、[デバッグなしで開始**またはキーを押します**ctrl キーを押しながら f5 キーを押して**します。
* アプリケーションのデプロイは、HoloLens 後、は、エア タップ ジェスチャを使用して fitbox を無視します。
* ビューに手を移動し、人差し指をハンドの追跡を開始する、空にします。
* 自分の手を左に移動、右、上下します。
* 手が検出され、ビューから失われたときに、カーソルがどのように変化するかをご覧ください。
* 場合は、イマーシブ ヘッドセットの場合は、接続し、コント ローラーを切断する必要があります。 このフィードバックは、接続されているコント ローラーは常に使用できる""、没入型のデバイスでは、重要なになります。

## <a name="chapter-2---navigation"></a>第 2 章 - ナビゲーション

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>目標

* 「宇宙飛行士を回転するには、ナビゲーション ジェスチャ イベントをを使用します。

### <a name="instructions"></a>手順

アプリケーションのナビゲーションのジェスチャを使用する編集するつもりは**GestureAction.cs**ナビゲーション ジェスチャが発生したときに、オブジェクトを回転します。 さらに、ナビゲーションが使用可能なときに表示されるカーソルにフィードバックを追加します。

1. **階層**パネルで、展開**CursorWithFeedback**します。
2. **ホログラム**フォルダー、検索、 **ScrollFeedback**資産。
3. ドラッグ アンド ドロップ、 **ScrollFeedback**にプレハブ、 **CursorWithFeedback**の GameObject、**階層**します。
4. をクリックして**CursorWithFeedback**します。
5. **インスペクター**パネルで、をクリックして、**コンポーネントの追加**ボタンをクリックします。
6. メニューで、検索ボックスに入力**CursorFeedback**します。 検索結果を選択します。
7. ドラッグ アンド ドロップ、 **ScrollFeedback**オブジェクトから、**階層**上に、**スクロール ゲーム オブジェクトの検出**プロパティ、**カーソル フィードバック**コンポーネント、**インスペクター**します。
8. **階層**パネルで、 **AstroMan**オブジェクト。
9. **インスペクター**パネルで、をクリックして、**コンポーネントの追加**ボタンをクリックします。
10. メニューで、検索ボックスに入力**ジェスチャによる操作**します。 検索結果を選択します。

次に、 **GestureAction.cs** Visual Studio でします。 コーディングの練習 2. c には、次のスクリプトを編集します。

1. **回転、AstroMan**オブジェクトのナビゲーションのジェスチャを実行するたびにします。
2. 計算、 **rotationFactor**オブジェクトに適用する回転の量を制御します。
3. **オブジェクトを回転させる**左または右に、ユーザーが、手の形を移動したときに、y 軸を中心。

2. c では、スクリプト、または置換下の完成したソリューションを使用してコードを実行する完全なコーディングします。

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

いくつかの情報を使用して、その他のナビゲーション イベントが既に入力されて表示されます。 ツールキットの上に GameObject プッシュ InputSystem のモーダル スタック、回転が始まった後に、「宇宙飛行士フォーカスを維持するために、ユーザーがないようにします。 同様に、ジェスチャが完了すると、スタックからポップ GameObject ポップします。

### <a name="build-and-deploy"></a>構築し、デプロイ

1. Unity でアプリケーションをリビルドし、ビルドして、HoloLens で実行する Visual Studio からデプロイします。
2. 見つめます、飛行士カーソルの両側に 2 つの矢印が表示されます。 この新しいビジュアルは、「宇宙飛行士を回転できることを示します。
3. 準備ができて位置 (インデックスの指が空を指して) に手を設定するため、HoloLens は手の追跡を開始します。
4. 回転するには、「宇宙飛行士をピンチ位置、人差し指を削減し、左または右 NavigationX ジェスチャをトリガーする、手の形を移動します。

## <a name="chapter-3---hand-guidance"></a>第 3 章 - 手の形のガイダンス

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>目標

* 使用**ガイダンスのスコアを渡す**追跡手が失われる場合の予測をサポートします。
* 提供**カーソル上でフィードバック**ときに、ユーザーの手の形に近いビューのカメラのエッジを表示します。

### <a name="instructions"></a>手順

1. **階層**パネルで、 **CursorWithFeedback**オブジェクト。
2. **インスペクター**パネルで、をクリックして、**コンポーネントの追加**ボタンをクリックします。
3. メニューで、検索ボックスに入力**手ガイダンス**します。 検索結果を選択します。
4. **プロジェクト**パネル**ホログラム**フォルダー、検索、 **HandGuidanceFeedback**資産。
5. ドラッグ アンド ドロップ、 **HandGuidanceFeedback**上に資産、**手ガイダンス インジケーター**プロパティ、**インスペクター**パネル。

### <a name="build-and-deploy"></a>構築し、デプロイ

* Unity でアプリケーションをリビルドし構築、HoloLens でアプリを体験する Visual Studio からデプロイします。
* 手を表示し、追跡する際、人差し指を発生させます。
* ナビゲーションのジェスチャに「宇宙飛行士回転を開始 (インデックス指によるピンチ ジェスチャと一緒に thumb)。
* 実際には、左端、右端、上下に移動します。
* 矢印が横に表示する必要がありますを手がジェスチャのフレームの端に近づくと、追跡手札を警告する、カーソルが失われます。 矢印は、損失を防止の追跡を防ぐために手を移動する方向を示します。

## <a name="chapter-4---manipulation"></a>第 4 章 - 操作

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>目標

* 操作イベントを使用すると、自分の手で「宇宙飛行士を移動できます。
* ユーザーが操作を使用するタイミングを把握できるカーソル上でフィードバックを提供します。

### <a name="instructions"></a>手順

GestureManager.cs と AstronautManager.cs により、次の操作。

1. 音声キーワードを使用して"**移動「宇宙飛行士**"有効にする**操作**ジェスチャと"**回転飛行士**"を無効にします。
2. 応答に切り替えて、**操作のジェスチャ レコグナイザー**します。

それでは始めましょう。

1. **階層**パネルで、新しい空の GameObject を作成します。 名前を付けます"**AstronautManager**"。
2. **インスペクター**パネルで、をクリックして、**コンポーネントの追加**ボタンをクリックします。
3. メニューで、検索ボックスに入力**飛行士 Manager**します。 検索結果を選択します。
4. **インスペクター**パネルで、をクリックして、**コンポーネントの追加**ボタンをクリックします。
5. メニューで、検索ボックスに入力**音声入力ソース**します。 検索結果を選択します。

これで、「宇宙飛行士の相互作用の状態を制御するために必要な音声コマンドを追加します。

1. 展開、**キーワード**セクション、**インスペクター**します。
2. をクリックして、 **+** 右側に新しいキーワードを追加します。
3. As キーワードを入力 **「宇宙飛行士を移動**します。 自由に必要な場合は、キーのショートカットを追加します。
4. をクリックして、 **+** 右側に新しいキーワードを追加します。
5. As キーワードを入力 **「宇宙飛行士を回転**します。 自由に必要な場合は、キーのショートカットを追加します。
6. 対応するハンドラーのコードが見つかります**GestureAction.cs**の**ISpeechHandler.OnSpeechKeywordRecognized**ハンドラー。

![第 4 章の音声入力ソースをセットアップする方法](images/holograms211-speech.png)

次に、カーソル上で操作のフィードバックを設定します。

1. **プロジェクト**パネル**ホログラム**フォルダー、検索、 **PathingFeedback**資産。
2. ドラッグ アンド ドロップ、 **PathingFeedback**にプレハブ、 **CursorWithFeedback**オブジェクト、**階層**します。
3. **階層**パネルで、をクリックして**CursorWithFeedback**します。
4. ドラッグ アンド ドロップ、 **PathingFeedback**オブジェクトから、**階層**上に、**のゲーム オブジェクトの検出パス**プロパティ、**カーソル フィードバック**コンポーネント、**インスペクター**します。

コードを追加する必要があります**GestureAction.cs**以下を有効にします。

1. コードを追加、 **IManipulationHandler.OnManipulationUpdated** 、関数は、「宇宙飛行士を移動するときに、**操作**ジェスチャが検出されました。
2. 計算、**動きベクトル**飛行士の移動先を決定するベースの手元に位置します。
3. **移動**を新しい位置に「宇宙飛行士します。

4.a を練習する完全なコーディング**GestureAction.cs**、または完成したソリューションは、以下を使用します。

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a>構築し、デプロイ

* Unity で再構築し、ビルドして、HoloLens でアプリを実行する Visual Studio からデプロイします。
* HoloLens の前に手を移動し、追跡できるように、人差し指を発生させます。
* 「宇宙飛行士経由でカーソルをを注目します。
* 操作のジェスチャに「宇宙飛行士を移動する ' 飛行士の移動 と答えてください。
* 4 つの矢印は、プログラムが操作イベントに応答するようになりましたことを示すカーソルの周囲に表示されます。
* 親指まで、人差し指を削減し、一緒に挟まれてしておきます。
* 「宇宙飛行士はも移動手周囲を移動すると、(これは操作です)。
* 「宇宙飛行士操作を停止する際人差し指を発生させます。
* 注:手を移動する前に、' 飛行士移動 ' はいないと答えるとは、ナビゲーションのジェスチャを代わりに使用されます。
* '回転「宇宙飛行士' 回転可能な状態に戻すことあるとします。

## <a name="chapter-5---model-expansion"></a>第 5 章「モデルの拡張

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>目標

* 複数「宇宙飛行士モデルを展開しユーザーが対話できることをより小さな部分。
* 移動および操作のジェスチャを使用して個別に各部分に移動します。

### <a name="instructions"></a>手順

このセクションでは、次のタスクを行いましています。

1. New キーワードを追加"**展開モデル**"を「宇宙飛行士モデルを展開します。
2. New キーワードを追加"**リセット モデル**"に、モデルを元のフォームに戻ります。

前の章から音声入力ソースに 2 つ以上のキーワードを追加することでこれを実行します。 認識のイベントを処理する別の方法も示します。

1. [戻る] をクリックして**AstronautManager**で、**インスペクター**を展開し、**キーワード**セクション、**インスペクター**します。
2. をクリックして、 **+** 右側に新しいキーワードを追加します。
3. As キーワードを入力**展開モデル**します。 自由に必要な場合は、キーのショートカットを追加します。
4. をクリックして、 **+** 右側に新しいキーワードを追加します。
5. As キーワードを入力**モデルをリセット**します。 自由に必要な場合は、キーのショートカットを追加します。
6. **インスペクター**パネルで、をクリックして、**コンポーネントの追加**ボタンをクリックします。
7. メニューで、検索ボックスに入力**音声入力ハンドラー**します。 検索結果を選択します。
8. 確認**はグローバル リスナー**を絞っているこれらのコマンドを GameObject に関係なく機能するため、します。
9. をクリックして、 **+** ボタンをクリックし、選択**展開モデル**キーワードのドロップダウン リストから。
10. をクリックして、 **+** 応答、およびドラッグ下、 **AstronautManager**から、**階層**に、 **None (オブジェクト)** フィールド。
11. をクリックして、**いいえ関数**] ドロップダウンで、[ **AstronautManager**、し**ExpandModelCommand**します。
12. 音声入力ハンドラーをクリックします。 **+** ボタンをクリックし、選択**リセット モデル**キーワードのドロップダウン リストから。
13. をクリックして、 **+** 応答、およびドラッグ下、 **AstronautManager**から、**階層**に、 **None (オブジェクト)** フィールド。
14. をクリックして、**いいえ関数**] ドロップダウンで、[ **AstronautManager**、し**ResetModelCommand**します。

![第 5 章のセットアップ、音声入力ソースとハンドラーする方法](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>構築し、デプロイ

* お試しください。 ビルドして、アプリ、HoloLens をデプロイします。
* たとえば**展開モデル**に展開されている「宇宙飛行士モデルを参照してください。
* 使用**ナビゲーション**飛行士スーツの各部分を回転させる。
* たとえば**移動「宇宙飛行士**しを使用して**操作**飛行士スーツの各部分を移動しますします。
* たとえば**回転飛行士**部分を再度回転。
* たとえば**リセット モデル**に、「宇宙飛行士元フォームに戻ります。

## <a name="the-end"></a>最後です

これで終了です。 完了したので**MR 入力 211。ジェスチャ**します。

* 検出し、追跡、ナビゲーション、および操作イベントを渡すために応答する方法を理解します。
* 移動および操作のジェスチャの違いを理解します。
* 手の形が検出されると、手が失われると、オブジェクトが別の相互作用 (ナビゲーション vs 操作) をサポートする場合は、視覚的なフィードバックを提供する、カーソルを変更する方法を理解します。
