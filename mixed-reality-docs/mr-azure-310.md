---
title: MR および Azure 310 - オブジェクトの検出
description: 機械学習モデルをトレーニングする方法については、このコースを完了し、同等のオブジェクトと複合現実のアプリケーション内から現実の世界での位置を認識して、トレーニング済みモデルを使用します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure では、カスタム ビジョンは、オブジェクトの検出、実際に、アカデミー、unity、チュートリアル、api、hololens の混在
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597651"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。  そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。  これらのチュートリアルは **_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。  サポートされているデバイスで作業を続行するが保持されます。 一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。  この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。

# <a name="mr-and-azure-310-object-detection"></a>Mr と Azure 310:オブジェクトの検出

このコースでは方法を学習しますカスタム ビジュアルのコンテンツと、指定されたイメージに含まれる空間位置を認識して Azure の Custom Vision を使用して、複合現実のアプリケーションでは「オブジェクトの検出」機能します。

このサービスを使用して、オブジェクトのイメージを使用して機械学習モデルのトレーニングにはできます。 Microsoft HoloLens のカメラ キャプチャによって提供される同等のオブジェクトを認識し、おおよその現実の世界での場所に、トレーニング済みモデルを使用してまたは没入型の (VR) ヘッドセットの PC にカメラを接続します。

![コースの結果](images/AzureLabs-Lab310-00.png)

**Azure の Custom Vision、オブジェクトの検出**Microsoft サービスで、開発者がカスタム イメージ分類モデルを構築します。 提供することで、そのイメージ内のオブジェクトを検出するために新しいイメージでこれらの分類モデルが使用しできます**ボックス境界**はイメージ自体。 サービスは、このプロセスを効率化のシンプルで使いやすい、オンライン ポータルを提供します。 詳細については、次のリンクを参照してください。

* [Azure の Custom Vision ページ](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [制限とクォータ](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

このコースを修了、以下を実行できる必要が複合現実のアプリケーションが用意されます。

1. ユーザーができるようになります*視線*Azure Custom Vision Service オブジェクトの検出を使用して、トレーニングがオブジェクトにします。 
2. ユーザーが使用する、*タップ*で目的のイメージをキャプチャするジェスチャ。
3. アプリはイメージを Azure の Custom Vision Service に送信します。
4. ワールド空間テキストとして認識の結果が表示されるサービスからの応答があります。 これは、Microsoft HoloLens の空間追跡、認識されているオブジェクトのワールド位置を理解して使用し、方法として利用するによって実現されますが、*タグ*イメージ内に検出された内容に関連付けられています。ラベルのテキストを提供します。

コースは、タグを作成、アップロードを手動でのイメージも説明し、トレーニング異なるを認識する、サービス オブジェクト (指定の例では、杯) での設定、*境界ボックス*を送信する、イメージ内で。 

> [!IMPORTANT]
> 次の作成とアプリの使用、開発者する必要があります Azure の Custom Vision Service に戻るを特定、サービスによって行われた予測しかどうかが正しいかどうかを判断する (サービスを何もタグ付けによってがなくと調整、*境界ボックス*)。 サービス、再トレーニングできます、現実世界のオブジェクトを認識することの可能性が高くなりますが。

このコースでは、Azure の Custom Vision Service、オブジェクトの検出から Unity に基づくサンプル アプリケーションに結果を取得する方法を説明します。 最大をカスタム アプリケーションをビルドしている場合にこれらの概念を適用することがあります。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 310:オブジェクトの検出</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>前提条件

> [!NOTE]
> このチュートリアルは、Unity を使用した基本的な経験がある開発者向けに設計およびC#します。 また、前提条件やこのドキュメント内の書面の手順を表すテストおよび (2018 年 7 月) の書き込み時に検証されたがどのようなことに注意してください。 内に一覧表示するには自由に最新のソフトウェアを使用して、[ツールをインストールする](https://docs.microsoft.com/windows/mixed-reality/install-the-tools)にする必要がありますが想定されていなかったことについては、このコースでとまったく同じで記載されているものよりも新しいソフトウェアで表示されますが、記事以下に。

次のハードウェアとソフトウェアこのコースをお勧めします。

- 開発用 PC
- [Windows 10 Fall Creators Update (またはそれ以降) で開発者モードが有効になっています。](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [最新の Windows 10 SDK](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Unity 2017.4 LTS](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Visual Studio 2017](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details)開発者モードが有効
- Azure のセットアップおよび Custom Vision Service 取得するためのインターネット アクセス
-  一連のイメージには少なくとも 15 (15) が必要です) を認識するカスタム ビジョンを希望するオブジェクトごとにします。 かどうかに、既にこのコースで提供されるイメージを使用する[一連の cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))。

## <a name="before-you-start"></a>開始前の作業

1.  このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。
2.  設定して、HoloLens をテストします。 場合は、HoloLens の設定をサポートする必要がある[HoloLens のセットアップ記事を参照してください。 確認](https://docs.microsoft.com/hololens/hololens-setup)します。 
3.  (場合によって役立ちますユーザーごとにこれらのタスクを実行する) 新しい HoloLens アプリの開発を始めるときに、調整とセンサーのチューニングを実行することをお勧めします。 

調整に関するヘルプを参照するに従ってくださいこの[HoloLens 調整記事へのリンク](calibration.md#hololens)します。

センサーの調整に関する詳細についてに従ってくださいこの[HoloLens センサー チューニング記事へのリンク](sensor-tuning.md)します。

## <a name="chapter-1---the-custom-vision-portal"></a>第 1 章 - Custom Vision ポータル

使用する、 **Azure Custom Vision Service**、そのアプリケーションに使用可能にするインスタンスを構成する必要があります。

1.  移動[を**Custom Vision Service**メイン ページ](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)します。

2.  をクリックして**Getting Started**します。

    ![](images/AzureLabs-Lab310-01.png)

3.  Custom Vision ポータルにサインインします。

    ![](images/AzureLabs-Lab310-02.png)

4.  Azure アカウントがいない場合は、1 つを作成する必要があります。 クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。

5.  求められます初めてログインした後、*サービス利用規約*パネル。 チェック ボックスをクリックして*条項に同意*します。 クリックして**同意**します。

    ![](images/AzureLabs-Lab310-03.png)

6.  条項に同意したこと、れるので、*マイ プロジェクト*セクション。 をクリックして**新しいプロジェクト**します。

    ![](images/AzureLabs-Lab310-04.png)

7.  プロジェクトの一部のフィールドを指定するように求められますが、右側にあるタブが表示されます。

    1.  プロジェクトの名前を挿入します。

    2.  プロジェクトの説明を挿入 (**(省略可能)**)

    3.  選択、**リソース グループ**か新規に作成します。 リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。 勧めします (例: これらのコース) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > たい場合[読み取りの詳細は、Azure リソース グループの詳細については、関連付けられているドキュメントに移動します。](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4.  設定、**プロジェクトの種類**として**オブジェクトの検出 (プレビュー)** します。

8.  終了したらをクリックして**プロジェクトの作成**、し、Custom Vision Service プロジェクトのページにリダイレクトされます。


## <a name="chapter-2---training-your-custom-vision-project"></a>第 2 章 – Custom Vision プロジェクトのトレーニング

1 回、Custom Vision ポータルの主な目的はイメージ内の特定のオブジェクトを認識するようにプロジェクトのトレーニングには。

各オブジェクトを認識するアプリケーションを少なくとも 15 (15) イメージが必要です。 このコースで提供されるイメージを使用することができます ([一連の cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))。

Custom Vision プロジェクトのトレーニング。

1.  をクリックして、 **+** 横に**タグ**します。

    ![](images/AzureLabs-Lab310-06.png)

2.  追加、**名前**タグのによって、イメージを関連付けるために使用されます。 認識のため、これは、タグを付けた、カップのイメージを使用しているがこの例では**Cup**します。 クリックして**保存**完了後します。

    ![](images/AzureLabs-Lab310-07.png)

3.  **タグ**が追加されました (表示するページを再読み込みする必要があります)。 

    ![](images/AzureLabs-Lab310-08.png)

4.  をクリックして**イメージを追加**ページの中央にします。

    ![](images/AzureLabs-Lab310-09.png)

5.  をクリックして**ローカル ファイルを参照**とに 1 つのオブジェクト、15、最小されていると (15) をアップロードするイメージを参照します。

    > [!TIP]
    >  一度にアップロードするいくつかのイメージを選択できます。

    ![](images/AzureLabs-Lab310-10.png)

6.  キーを押して**ファイルをアップロード**トレーニングを使用してプロジェクトにするすべてのイメージを選択するとします。 ファイル アップロードが開始されます。 アップロードの確認したら、クリックして**完了**します。

    ![](images/AzureLabs-Lab310-11.png)

7.  この時点で、イメージがアップロードされるが、タグ付けされていません。

    ![](images/AzureLabs-Lab310-12.png)

8.  イメージをタグにマウスを使用します。 イメージをポイントするよう選択の強調表示する助けとなります、オブジェクトの周りに選択範囲を自動的に描画することで。 正確でない場合を描画できます独自。 これは、マウスの左クリックを保持していると、オブジェクトを囲むように選択した領域にドラッグすることによって実現されます。 

    ![](images/AzureLabs-Lab310-13.png) 

9. 次のイメージ内のオブジェクトの選択、小規模なプロンプトがするように求められます*リージョン タグを追加*します。 以前に作成したタグ ('Cup'、上記の例では) を選択するかその他のタグを追加する場合でを入力し、をクリックして、 **+ (正符号 +)** ボタンをクリックします。

    ![](images/AzureLabs-Lab310-14.png) 

10. 次の画像をタグ付けする、ブレードの右側にある矢印をクリックします。 または、[タグ] ブレードを閉じます (をクリックして、 **X**ブレードの右上隅にある) を次の画像をクリックします。 次のイメージを準備した後は、同じ手順を繰り返します。 これまで、すべてタグ付けされている、アップロードしたすべてのイメージを行います。 

    > [!NOTE]
    >  次の図のように、同じイメージでは、いくつかのオブジェクトを選択できます。 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. それらすべてにタグが、クリックして、**タグが付けられた**タグが付けられたイメージを表示する画面の左側にボタンをクリックします。 

    ![](images/AzureLabs-Lab310-16.png)

12. サービスをトレーニングする準備が整いました。 をクリックして、**トレーニング**ボタン、および最初のトレーニングのイテレーションが開始されます。

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. ビルドされたらという 2 つのボタンを表示できるが**既定**と**予測 URL**します。 をクリックして**既定**でクリックし、最初に、**予測 URL**します。

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > これにより、提供されているエンドポイントがどちらに設定されている*イテレーション*が既定としてマークされました。 このため、後で行った場合、新しい*イテレーション*と既定値として更新して、コードを変更する必要はありません。

14. クリックすると**予測 URL**、オープン*メモ帳*、コピーして貼り付け、 **URL** (とも呼ばれます、**予測エンドポイント**)**サービス予測キー**コードの後半で必要なときに取得できるようにします。

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>第 3 章 - Unity プロジェクトの設定

次のコード例が複合現実での開発の一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。

1.  開いている**Unity**クリック**新規**します。

    ![](images/AzureLabs-Lab310-21.png)

2.  これで、Unity プロジェクトの名前を指定する必要があります。 挿入**CustomVisionObjDetection**します。 必ず、プロジェクトの種類に設定されて**3D**、設定と、**場所**で該当する別の場所を (ただし、ルート ディレクトリに近づけるためのより良い)。 をクリックし、**プロジェクトの作成**です。

    ![](images/AzureLabs-Lab310-22.png)

3.  既定値を確認する必要が開いている Unity、 **スクリプト エディター** に設定されている **Visual Studio** します。 移動して **編集* > *設定** し、新しいウィンドウに移動 **外部ツール** します。 変更 **External Script Editor** に **Visual Studio** します。 閉じる、**設定**ウィンドウ。

    ![](images/AzureLabs-Lab310-23.png)

4.  移動して次に、**ファイル > Build Settings**スイッチと、**プラットフォーム**に*ユニバーサル Windows プラットフォーム*をクリックし、 **プラットフォームの切り替え**ボタンをクリックします。

    ![](images/AzureLabs-Lab310-24.png)

5.  同じ**Build Settings**ウィンドウで、次を設定してください。

    1.  **デバイスを対象に**に設定されている**HoloLens**        
    2.  **ビルドの種類**に設定されている**D3D**
    3.  **SDK**に設定されている**インストールされている最新**
    4.  **Visual Studio バージョン**に設定されている**インストールされている最新**
    5.  **ビルドおよび実行**に設定されている**ローカル マシン**            
    6.  設定に残っている**Build Settings**、ここでは既定値として残しておく必要があります。

        ![](images/AzureLabs-Lab310-25.png)

6.  同じ**Build Settings**ウィンドウで、をクリックして、**プレーヤー設定**ボタン、領域に関連するパネルが開き、**インスペクター**が配置されています。

7. このパネルは、いくつかの設定を確認する必要があります。

    1.  **その他の設定** タブ。

        1.  **ランタイム バージョンをスクリプト**する必要があります**試験的**(.NET 4.6 Equivalent)、エディターを再起動する必要があるします。

        2. **バックエンドの scripting**べき **.NET**します。

        3. **API の互換性レベル**べき **.NET 4.6**します。

            ![](images/AzureLabs-Lab310-26.png)

    2.  内で、**発行の設定**] タブの [**機能**、確認してください。

        1. **InternetClient**

        2.  **Web カメラ**

        3. **SpatialPerception**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  パネル、下の方に**XR 設定**(次に示します**発行設定**)、ティック**仮想現実サポート**、確認してください、 **Windows 混在実際には SDK**が追加されます。

        ![](images/AzureLabs-Lab310-29.png)

8.  戻り**Build Settings**、 *Unity C\#プロジェクト*が不要になったグレー: この横にあるチェック ボックスをオンにします。

9.  閉じる、 **Build Settings**ウィンドウ。

10. **エディター**、 をクリックして**編集** > **プロジェクト設定** > **グラフィックス**します。

    ![](images/AzureLabs-Lab310-30.png)

11. **インスペクター パネル**、*グラフィックス設定*開きます。 呼ばれる配列が表示されるまで下にスクロール**シェーダーを常に含める**します。 スロットの追加を増やすことで、**サイズ**で 1 つは、変数 (この例でこれが 8 のでが 9)。 新しいスロットが表示されます、配列の最後の位置に次に示すよう。

    ![](images/AzureLabs-Lab310-31.png)

12. スロットでは、シェーダーのリストを開いて、スロットの横にあるターゲットの小さな円をクリックします。 探して、**レガシ シェーダー/Transparent 拡散**シェーダーし、ダブルクリックします。 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>第 4 章 - CustomVisionObjDetection Unity パッケージをインポートします。

このコースには、Unity Asset のパッケージと呼ばれる**Azure-MR-310.unitypackage**します。 

> [ヒント]シーンの全体を含む、Unity でサポートされているすべてのオブジェクトをパッケージ化できます、 **.unitypackage**ファイル、およびエクスポート/その他のプロジェクトにインポートされています。 別の間で資産を移動する最も安全な最も効率的な方法は**Unity プロジェクト**します。

検索することができます、[ここからダウンロードする必要がある Azure-MR-310 パッケージ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)します。

1.  前 [Unity ダッシュ ボード] をクリックして**資産**画面の上部にあるメニューでクリックして**パッケージのインポート > カスタム パッケージ**します。

    ![](images/AzureLabs-Lab310-33.png)

2.  ファイル ピッカーを使用して、 **Azure-MR-310.unitypackage**パッケージ化し、をクリックして**オープン**します。 この資産のコンポーネントの一覧が表示されます。 クリックして、インポートの確認、**インポート**ボタンをクリックします。

    ![](images/AzureLabs-Lab310-34.png)

3.  これには、インポートが完了したら後に、パッケージからのフォルダーが追加されたようになりましたことがわかりますが、**資産**フォルダー。 このようなフォルダー構造は、Unity プロジェクトの一般的なものです。

    ![](images/AzureLabs-Lab310-35.png)

    1.  **資料**フォルダーにはで使用される材料が含まれています、**視線カーソル**します。 

    2.  **プラグイン**フォルダーには、サービスの web 応答を逆シリアル化するコードで使用、Newtonsoft DLL が含まれています。 2 つの異なるバージョンにフォルダーとサブフォルダーに含まれているを使用でき、Unity エディターと UWP ビルドの両方でビルドされたライブラリを許可するために必要です。 

    3.  **プレハブ**フォルダーには、シーン内に含まれているプレハブが含まれています。 これらは。

        1.  **GazeCursor**アプリケーションで使用するカーソル。 物理オブジェクト上にシーンに配置することができる SpatialMapping プレハブと共に動作します。
        2.  **ラベル**、必要な場合に、シーン内のオブジェクト タグの表示に使用される UI オブジェクトであります。
        3.  **SpatialMapping**これを使用するアプリケーションを有効にするオブジェクトは、Microsoft HoloLens の空間の追跡を使用して、仮想のマップを作成します。

    4.  **シーン**フォルダーには現在このコースの既成のシーンが含まれています。

4.  開く、**シーン**フォルダーで、**プロジェクト パネル**、ダブルクリックして、 **ObjDetectionScene**、このコースで使用するシーンを読み込む。

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  **コードが含まれていない**、このコースで、コードを記述します。

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>5 -」の章では、CustomVisionAnalyser クラスを作成します。

この時点でコードを記述する準備が整いました。 開始するが、 **CustomVisionAnalyser**クラス。

> [!NOTE]
> 呼び出し、 **Custom Vision Service**、以下に示すコードで行われたを使用して、 **Custom Vision REST API**します。 これを使用して、実装して (ような画面が独自に実装する方法を理解するために役立ちます) この API を使用する方法が表示されます。 対応しており、Microsoft が提供する、**カスタム ビジョン SDK**をサービスを呼び出すことにも使用できます。 詳細については、次を参照してください。、[カスタム ビジョン SDK の記事](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)します。

このクラスは、責任を負います。

- バイト配列としてキャプチャされた最新のイメージを読み込んでいます。

- バイト配列を Azure に送信する**Custom Vision Service**分析のインスタンス。

- JSON 文字列としての応答を受信します。

- 応答を逆シリアル化し、その結果を渡して**予測**を**SceneOrganiser**クラスは、応答の表示方法の考慮されます。

このクラスを作成します。

1.  右クリックし、**アセット フォルダー**にある、**プロジェクト パネル**、順にクリックします**作成** > **フォルダー**します。 フォルダーを呼び出す**スクリプト**します。

    ![](images/AzureLabs-Lab310-37.png)

2.  新しく作成された フォルダーを開きをダブルクリックします。

3.  フォルダー内を右クリックし、をクリックして**作成** > **C\#スクリプト**します。 スクリプトの名前**CustomVisionAnalyser します。**

4.  ダブルクリックして、新しい**CustomVisionAnalyser**スクリプト ファイルを開く**Visual Studio。**

5.  次のファイルの上部にある参照される名前空間を確認してください。

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  **CustomVisionAnalyser**クラスで、次の変数を追加します。

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > 挿入することを確認、**サービス予測キー**に、 **predictionKey**変数、および**予測エンドポイント**に、 **predictionEndpoint**変数。 これらをコピーした[メモ帳以前では、第 2 章の手順 14](#chapter-2---training-your-custom-vision-project)します。

7.  コードを**Awake()** インスタンス変数を初期化するために追加する必要があります。

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  コルーチンを追加 (静的で**GetImageAsByteArray()** 下にあるメソッド)、によってキャプチャされたイメージの分析の結果を取得するが、 **ImageCapture**クラス。

    > [!NOTE]
    > **AnalyseImageCapture**コルーチンへの呼び出しがある、 **SceneOrganiser**クラスを作成することはまだです。 そのため、**は省略します線は、ここではコメント**します。

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

9. 削除、 **Start()** と**Update()** メソッドを使用できません。 

10.  変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。

> [!IMPORTANT]
> 前述のように、あまり心配しないでコード クラスすぐに、これらを修正するをさらに提供されますが、エラーを表示する可能性があります。

## <a name="chapter-6---create-the-customvisionobjects-class"></a>第 6 章 - CustomVisionObjects クラスを作成します。

クラスの作成はここでは、 **CustomVisionObjects**クラス。

このスクリプトには、Custom Vision Service への呼び出しを逆シリアル化およびシリアル化する他のクラスによって使用されるオブジェクト数が含まれています。

このクラスを作成します。

1.  内で右クリック、**スクリプト**フォルダー、 をクリックし、**作成** > **C\#スクリプト**します。 スクリプトを呼び出す**CustomVisionObjects します。**

2.  ダブルクリックして、新しい**CustomVisionObjects**スクリプト ファイルを開く**Visual Studio。**

3.  次のファイルの上部にある参照される名前空間を確認してください。

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  削除、 **Start()** と**Update()** 内のメソッド、 **CustomVisionObjects**クラス、このクラスは空になります。

    > [!WARNING]
    > 慎重に次の手順に従ってくださいが重要です。 新しいクラスの宣言内に配置した場合、 **CustomVisionObjects**クラスにコンパイル エラーが表示されます[第 10 章](#chapter-10---create-the-imagecapture-class)というを**AnalysisRootObject**と**BoundingBox**が見つかりません。

5.  次のクラスを追加*外*、 **CustomVisionObjects**クラス。 これらのオブジェクトを使って、 **Newtonsoft**および応答データを逆シリアル化するライブラリ。

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。

## <a name="chapter-7---create-the-spatialmapping-class"></a>7 - 章 SpatialMapping クラスを作成します。

このクラスは設定、**空間マッピング Collider**仮想オブジェクトと実際のオブジェクト間の競合を検出できるようにするシーンにします。

このクラスを作成します。

1.  内で右クリック、**スクリプト**フォルダー、 をクリックし、**作成** > **C\#スクリプト**します。 スクリプトを呼び出す**SpatialMapping します。**

2.  ダブルクリックして、新しい**SpatialMapping**スクリプト ファイルを開く**Visual Studio。**

3.  上記の次の名前空間があるかどうかを確認、 **SpatialMapping**クラス。

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  次に、内部では、次の変数を追加、 **SpatialMapping**クラス上、 **Start()** メソッド。

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  追加、 **Awake()** と**Start()**:

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  削除、 **Update()** メソッド。

7.  変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。


## <a name="chapter-8---create-the-gazecursor-class"></a>8 - 章 GazeCursor クラスを作成します。

このクラスは実際の領域で、正しい位置にカーソルを設定するための使用することで、 **SpatialMappingCollider**前の章で作成された。

このクラスを作成します。

1.  内で右クリック、**スクリプト**フォルダー、 をクリックし、**作成** > **C\#スクリプト**します。 スクリプトを呼び出す**GazeCursor**

2.  ダブルクリックして、新しい**GazeCursor**スクリプト ファイルを開く**Visual Studio。**

3.  上記の次の名前空間があるかどうかを確認、 **GazeCursor**クラス。

    ```csharp
    using UnityEngine;
    ```

4.  内の次の変数を追加し、 **GazeCursor**クラス上、 **Start()** メソッド。 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  更新プログラム、 **Start()** メソッドを次のコード。

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  更新プログラム、 **Update()** メソッドを次のコード。

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > エラーをあまり心配しないで、 **SceneOrganiser**クラスが、[次へ] の章では作成します。

7. 変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。

## <a name="chapter-9---create-the-sceneorganiser-class"></a>9 - 章 SceneOrganiser クラスを作成します。

このクラスは。

-   設定する、 *Main Camera*に適切なコンポーネントをアタッチしています。

-   オブジェクトが検出されたときに、現実の世界と配置内の位置を計算する責任を負いますなります、**タグ ラベル**と、該当の近く**タグ名**します。    

このクラスを作成します。

1.  内で右クリック、**スクリプト**フォルダー、 をクリックし、**作成** > **C\#スクリプト**します。 スクリプトの名前**SceneOrganiser**します。

2.  ダブルクリックして、新しい**SceneOrganiser**スクリプト ファイルを開く**Visual Studio。**

3.  上記の次の名前空間があるかどうかを確認、 **SceneOrganiser**クラス。

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  内で、次の変数を追加し、 **SceneOrganiser**クラス上、 **Start()** メソッド。

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  削除、 **Start()** と**Update()** メソッド。

6.  変数の下に追加、 **Awake()** メソッドはクラスを初期化し、シーンを設定します。

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  追加、 **PlaceAnalysisLabel()** メソッドは*Instantiate* (これは、この時点では、ユーザーに表示される)、シーン内のラベル。 クアッド (も非表示)、イメージが配置されると、し、現実の世界と重複しても配置されます。 これは、機能は、分析は、実際のオブジェクトのおおよその場所を決定するには、このクアッドにまでトレースした後、ボックスの座標が、サービスから取得したため、重要です。 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  追加、 **FinaliseLabel()** メソッド。 担当します。

    *   設定、*ラベル*テキストを*タグ*の最高の信頼性と予測します。
    *   計算を呼び出す、*境界ボックス*クアッドのオブジェクトでは、以前は、配置およびシーン内のラベルを配置することにします。
    *   に向けての Raycast を使用して、ラベルの深さを調整すること、*境界ボックス*、現実の世界でオブジェクトが衝突する必要があります。
    * 別のイメージをキャプチャするユーザーを許可するキャプチャ プロセスをリセットしています。

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  追加、 **CalculateBoundingBoxPosition()** メソッドは、さまざまな変換に必要な計算をホストする、*境界ボックス*座標は、サービスから取得され、再作成します。クアッド比例的に。

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. 変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。

    > [!IMPORTANT]
    > 続行する前に開いて、 **CustomVisionAnalyser**クラス内で、 **AnalyseLastImageCaptured()** メソッド、*をコメント解除します*次の行。
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> 心配しないで、 **ImageCapture** '見つかりませんでした' メッセージのクラス、[次へ] の章では作成します。


## <a name="chapter-10---create-the-imagecapture-class"></a>10 - 章 ImageCapture クラスを作成します。

次のクラスを作成することには、 **ImageCapture**クラス。

このクラスは、責任を負います。

*   HoloLens のカメラを使用して、格納することでイメージのキャプチャ、*アプリ*フォルダー。
*   処理*タップ*ユーザーからのジェスチャ。

このクラスを作成します。

1.  移動して、**スクリプト**以前に作成したフォルダーです。

2.  フォルダー内を右クリックし、をクリックして**作成** > **C\#スクリプト**します。 スクリプトの名前**ImageCapture**します。

3.  ダブルクリックして、新しい**ImageCapture**スクリプト ファイルを開く**Visual Studio。**

4.  次のように、ファイルの上部にある名前空間に置き換えます。

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  内で、次の変数を追加し、 **ImageCapture**クラス上、 **Start()** メソッド。

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  コードを**Awake()** と**Start()** 今すぐメソッドを追加する必要があります。

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  タップ ジェスチャが発生したときに呼び出されるハンドラーを実装します。

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > カーソルがある場合**緑色**カメラが、イメージを意味します。 カーソルがある場合**赤い**カメラがビジー状態になります。

8.  イメージのキャプチャ プロセスを開始し、イメージを格納するアプリケーションが使用するメソッドを追加します。

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });
        }
    ```

9.  写真をキャプチャおよび分析する準備ができ次第の呼び出されるハンドラーを追加します。 渡されますが、結果、 **CustomVisionAnalyser**分析します。

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. 変更を保存することを確認する**Visual Studio**に戻る前に**Unity**します。

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>第 11 章 – シーン内のスクリプトの設定

これですべてのこのプロジェクトに必要なコードを記述して、シーンと正しく動作するように、プレハブのスクリプトを設定するには

1.  内で、 **Unity エディター**の**階層パネル**を選択、 **Main Camera**します。
2.  **インスペクター パネル**で、 **Main Camera**選択すると、をクリックして**コンポーネントの追加**、検索し**SceneOrganiser**スクリプトと追加するをダブルクリックします。

    ![](images/AzureLabs-Lab310-38.png)

3.  **プロジェクト パネル**、オープン、 **Prefabs フォルダー**、ドラッグ、**ラベル**にプレハブ、*ラベル*空の参照先の領域を入力する、**SceneOrganiser**に追加したスクリプト、 *Main Camera*次の図に示すように、します。

    ![](images/AzureLabs-Lab310-39.png)

4.  **階層パネル**を選択、 **GazeCursor**の子、 **Main Camera**します。
5.  **インスペクター パネル**で、 **GazeCursor**選択すると、をクリックして**コンポーネントの追加**を検索し**GazeCursor**スクリプトと追加するをダブルクリックします。

    ![](images/AzureLabs-Lab310-40.png)

6.  もう一度、**階層パネル**を選択、 **SpatialMapping**の子、 **Main Camera**。
7.  **インスペクター パネル**で、 **SpatialMapping**選択すると、をクリックして**コンポーネントの追加**を検索し**SpatialMapping**スクリプトそれを追加する をダブルクリックします。

    ![](images/AzureLabs-Lab310-41.png)

残りのスクリプトをするがないセット内のコードで追加されます、 **SceneOrganiser**スクリプトの実行時に、します。

## <a name="chapter-12---before-building"></a>第 12 章 - ビルドの前に

アプリケーションの徹底的なテストを実行するには、必要がありますをサイドロードすること、Microsoft HoloLens にします。

実行する前にいることを確認します。

-  説明されているすべての設定、[第 3 章](#chapter-3---set-up-the-unity-project)が正しく設定されています。
- スクリプト**SceneOrganiser**にアタッチされて、 **Main Camera**オブジェクト。
- スクリプト**GazeCursor**にアタッチされて、 **GazeCursor**オブジェクト。
- スクリプト**SpatialMapping**にアタッチされて、 **SpatialMapping**オブジェクト。
- [第 5 章](#chapter-5---create-the-customvisionanalyser-class)手順 6。

    - 挿入することを確認、**サービス予測キー**に、 **predictionKey**変数。
    - 挿入した、**予測エンドポイント**に、 **predictionEndpoint**クラス。

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>章 13 - アプリケーションを作成、UWP のソリューションとサイドロードします。

Microsoft HoloLens にデプロイすることができますを UWP ソリューションとしてのアプリケーションを構築する準備が整いました。 ビルド プロセスを開始します。

1.  移動して**ファイル > のビルド設定**します。

2.  ティック**Unity C\#プロジェクト**します。

3.  をクリックして**開くシーンを追加**します。 これにより、ビルドに現在開いているシーンが追加されます。

    ![](images/AzureLabs-Lab310-42.png)

4.  **[Build]** をクリックします。 Unity を起動、*ファイル エクスプ ローラー*ウィンドウを作成しにアプリをビルドするフォルダーを選択する必要があります。 ここで、そのフォルダーを作成し、名前**アプリ**します。 使用し、**アプリ**フォルダーを選択すると、クリックして**フォルダーの選択**します。

5.  Unity にプロジェクトをビルドを開始、**アプリ**フォルダー。

6.  1 回 Unity には、(少し時間がかかる場合があります) ビルドが完了したが開き、**ファイル エクスプ ローラー**ビルドの位置にあるウィンドウ (上の windows では、常に表示されないの新しい追加の通知をタスク バーを確認ウィンドウ)。

7.  Microsoft HoloLens を展開する必要がありますそのデバイスの IP アドレス (リモート) をデプロイ用ともいることを確認するのには**開発者モード**を設定します。 これには、次の手順を実行します。

    1.  ソックスを着けずに、HoloLens 中を開く、**設定**します。

    2.  移動して**ネットワークとインターネット** > **Wi-fi** > **詳細オプション**

    3.  注、 **IPv4**アドレス。

    4.  次に移動します**設定**、し**更新とセキュリティ** > **開発者向け**

    5.  設定**開発者モード***で*します。

8.  新しい Unity ビルドに移動します (、**アプリ**フォルダー) とソリューション ファイルを開くと**Visual Studio**します。

9.  ソリューション構成の選択で**デバッグ**します。

10. ソリューション プラットフォーム で選択**x86、リモート コンピューター**します。 挿入を求め、 **IP アドレス**のリモート デバイス (、Microsoft HoloLens、ここでは、メモしたもの)。

    ![](images/AzureLabs-Lab310-43.png)

11. 移動して、**ビルド**メニューをクリックします**ソリューションの配置**サイドロード、HoloLens をアプリケーションにします。

12. アプリが、Microsoft HoloLens、起動の準備完了にインストールされているアプリの一覧に表示されます。

### <a name="to-use-the-application"></a>アプリケーションを使用します。

* トレーニングがオブジェクトを見て、 **Azure Custom Vision Service、オブジェクトの検出**を使用して、**タップ ジェスチャ**します。
* 場合は、オブジェクトが正常に検出されると、ワールド空間*ラベル テキスト*タグ名と共に表示されます。

> [!IMPORTANT]
> 写真をキャプチャして、サービスに送信するたびには、サービスのページに戻るし、新しくキャプチャされたイメージのサービスの再トレーニングします。 を先頭には、おそらく修正する必要も、*境界ボックス*より正確になるし、サービスの再トレーニングします。

> [!NOTE]
> 配置ラベルのテキストは可能性があります、現実世界のオブジェクトを基準とした、適切なコライダーを配置する Microsoft HoloLens のセンサーや Unity で SpatialTrackingComponent が失敗したときに、オブジェクトの近くは表示されません。 その場合は、異なる画面で、アプリケーションを使用してください。

## <a name="your-custom-vision-object-detection-application"></a>カスタム ビジョン、アプリケーションのオブジェクトの検出

これで、Azure の Custom Vision がイメージからオブジェクトを認識して 3D 空間でそのオブジェクトのおおよその位置を提供し、オブジェクト検出 API を利用している mixed reality アプリを構築します。

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>ボーナスの演習

### <a name="exercise-1"></a>手順 1

3D に実際のオブジェクトをラップする半透明にするキューブを使用して、テキスト ラベルを追加する*境界ボックス*します。

### <a name="exercise-2"></a>手順 2

複数のオブジェクトを認識する、Custom Vision Service をトレーニングします。

### <a name="exercise-3"></a>手順 3

オブジェクトが認識されると、サウンドを再生します。

### <a name="exercise-4"></a>手順 4

API を使用して、アプリの分析は、同じイメージのサービスの再トレーニングに、そのため、サービスをより正確に (予測と同時にトレーニングを行う)。
