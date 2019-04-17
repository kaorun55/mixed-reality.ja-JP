---
title: MR とビデオのストリーミング - Azure 306
description: このコースでは、複合現実のアプリケーション内で Azure Media Services を実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、メディア サービス、ストリーミング ビデオ、360、没入型、vr
ms.openlocfilehash: f6974ab6a72828a557649d5dc65b4e505a7484ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599484"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。  そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。  これらのチュートリアルは**_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。  サポートされているデバイスで作業を続行するが保持されます。 一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。  この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。

<br> 

# <a name="mr-and-azure-306-streaming-video"></a>MR と Azure 306:ビデオのストリーミング

![最終的な製品-開始](images/AzureLabs-Lab6-00.png)
![最終製品-開始](images/AzureLabs-Lab6-01.png)

このコースでは、学習イマーシブ ヘッドセットでビデオの再生を 360 度のストリーミングを許可する Windows Mixed Reality VR エクスペリエンスに、Azure Media Services を接続する方法。 

**Azure Media Services**は今日の最も人気のあるモバイル デバイスでより多くのユーザーに到達するブロードキャスト品質ビデオ ストリーミング サービスを提供するサービスのコレクションです。 詳細については、次を参照してください。、 [Azure Media Services ページ](https://azure.microsoft.com/services/media-services)します。

このコースを完了するは、次のことが、複合現実イマーシブ ヘッドセット アプリケーションが用意されます。

1. 360 度のビデオを取得、 **Azure Storage**を使用して、 **Azure Media Service**します。

2. Unity シーン内で取得した 360 度のビデオを表示します。

3. 2 つの異なるビデオで、2 つのシーン間を移動します。

アプリケーションでは、責任ですが、設計と、結果を統合する方法について。 このコースは、Unity プロジェクトで Azure サービスを統合する方法を説明する設計されています。 複合現実アプリを強化するためには、このコース得た知識を使用することがあります。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 306:ビデオのストリーミング</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>前提条件

> [!NOTE]
> このチュートリアルは、Unity を使用した基本的な経験がある開発者向けに設計およびC#します。 また、前提条件やこのドキュメント内の書面の手順を表すテストおよび (2018 年 5 月) の書き込み時に検証されたがどのようなことに注意してください。 内に一覧表示するには自由に最新のソフトウェアを使用して、[インストール ツール記事](install-the-tools.md)ことについては、このコースでとまったく同じで見つかりますの下に記載されているものよりも新しいソフトウェアでどのようなことは仮定されませんが、.

次のハードウェアとソフトウェアこのコースをお勧めします。

- 開発用 PC、a [Windows Mixed Reality と互換性のある](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)(VR) ヘッドセットの没入型の開発
- [Windows 10 Fall Creators Update (またはそれ以降) で開発者モードが有効になっています。](install-the-tools.md#installation-checklist)
- [最新の Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- A [Windows Mixed Reality 没入型 (VR) ヘッドセット](immersive-headset-hardware-details.md)
- Azure のセットアップやデータの取得のためのインターネット アクセス
- Mp4 形式で 2 つの 360 度ビデオ (いくつか使用料無料のビデオを検索する[このダウンロードのページにある](https://www.mettle.com/360vr-master-series-free-360-downloads-page))

## <a name="before-you-start"></a>開始前の作業

1.  このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。
2.  設定し、混合 Reality イマーシブ ヘッドセットをテストします。

    > [!NOTE]
    > **いない**このコースのモーションのコント ローラーが必要です。 イマーシブ ヘッドセットの設定をサポートする場合をクリックしてください[Windows Mixed Reality を設定する方法についてのリンク](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)します。

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a>1 - Azure Portal の章: Azure ストレージ アカウントの作成

使用する、 **Azure ストレージ サービス**、作成および構成する必要があります、**ストレージ アカウント**Azure portal でします。

1.  [Azure ポータル](https://portal.azure.com) にログインします。

    > [!NOTE]
    > Azure アカウントがいない場合は、1 つを作成する必要があります。 クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。

2.  ログインした後は、をクリックして**ストレージ アカウント**左側のメニュー。

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab6-02.png)

3.  **ストレージ アカウント** タブで、をクリックして**追加**します。

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab6-03.png)

4.  **ストレージ アカウントを作成する** タブ。

    1.  挿入、**名前**お使いのアカウントに、数字と小文字のみこのフィールドを受け入れるに注意してください。

    2.  **デプロイ モデルでは、** 選択**Resource manager**します。

    3.  **アカウントの種類**、**ストレージ (汎用 v1)** します。

    4.  **パフォーマンス**、 **Standard *。**

    5.  **レプリケーション**選択**ローカル冗長ストレージ (LRS)** します。

    6.  まま**転送が必須のセキュリティで保護された**として**無効になっている**します。

    7.  選択、**サブスクリプション**します。

    8.  選択、**リソース グループ**か新規に作成します。 リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。

    9.  確認、**場所**(新しいリソース グループを作成する) 場合は、リソース グループ。 場所は、アプリケーションが実行リージョンにあるが理想的です。 一部の Azure 資産は特定のリージョンでのみ使用できます。

5.  このサービスに適用される条件を読んで理解したことを確認する必要があります。

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab6-04.png)

6.  クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。

7.  通知は、サービス インスタンスが作成されたら、ポータルに表示されます。

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab6-05.png)

8.  この時点で次のリソースは、[次へ] の章に進みます。 単純にする必要はありません。

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a>2 - Azure Portal の章: メディア サービスの作成

Azure メディア サービスを使用するには、(アカウント保有者が必要管理者である場合)、アプリケーションに使用可能にするサービスのインスタンスを構成する必要があります。

1.  Azure Portal をクリックして**リソースの作成**左上隅にある検索して**メディア サービス、** キーを押して **」と入力**します。 現在、目的のリソースがピンク色のアイコン。この新しいページを表示する をクリックします。

    ![Azure Portal](images/AzureLabs-Lab6-06.png)

2.  新しいページがの説明を入力、**メディア サービス**します。 このダイアログ ボックスの左下にある at をクリックして、**作成**ボタンは、このサービスとの関連付けを作成します。

    ![Azure Portal](images/AzureLabs-Lab6-07.png)

3.  クリックすると**作成**新しいメディア サービスについての詳細を提供する必要があるパネルが表示されます。

    1.  必要な挿入**アカウント名**このサービス インスタンス。

    2.  選択、**サブスクリプション**します。

    3. 選択、**リソース グループ**か新規に作成します。 リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。 勧めします (例: これらのラボ) など一般的なリソース グループの下の 1 つのプロジェクトに関連付けられているすべての Azure サービスを保持する)。 
    
    > 詳細にする場合は、Azure リソース グループに従ってくださいこの[Azure リソース グループを管理する方法についてのリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    4.  確認、**場所**(新しいリソース グループを作成する) 場合は、リソース グループ。 場所は、アプリケーションが実行リージョンにあるが理想的です。 一部の Azure 資産は特定のリージョンでのみ使用できます。

    5.  **ストレージ アカウント**セクションで、、**を選択してください.** セクションで、クリック、**ストレージ アカウント**最後の章で作成しました。

    6.  また、このサービスに適用される条件を理解したことを確認する必要があります。

    7.  **[作成]** をクリックします。

        ![Azure Portal](images/AzureLabs-Lab6-08.png)

4.  クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。

5.  通知は、サービス インスタンスが作成されたら、ポータルに表示されます。

    ![Azure Portal](images/AzureLabs-Lab6-09.png)

6.  新しいサービス インスタンスを探索する通知をクリックします。

    ![Azure Portal](images/AzureLabs-Lab6-10.png)

7.  をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。

8.  新しいメディア サービス ページの左側で、パネル内では、をクリックして、**資産**偶数の一覧については、リンク。

9.  次のページで、ページの左上隅にある クリックして**アップロード**します。

    ![Azure Portal](images/AzureLabs-Lab6-11.png)

10. をクリックして、**フォルダー**アイコン ファイルを参照し、最初に 360 ビデオをストリーミングしたいを選択します。 
    
    > これを利用できる[サンプル ビデオをダウンロードするリンク](https://vimeo.com/214401712)します。

    ![Azure Portal](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> 長いファイル名は、エンコーダーで問題を生じさせる可能性があります: ためにビデオの問題がないことを確認するには、ビデオ ファイル名の長さを短縮することを検討してください。

11. ビデオのアップロードが完了すると、進行状況バーが緑色になります。

    ![Azure Portal](images/AzureLabs-Lab6-13.png)

12. 上記のテキストをクリックして (**yourservicename - 資産**) に戻る、**資産**ページ。

13. ビデオが正常にアップロードされていることがわかります。 これをクリックします。

    ![Azure Portal](images/AzureLabs-Lab6-14.png)

14. ビデオに関する詳細情報にリダイレクトされるページが表示されます。 をクリックして、エンコードする必要がある、ビデオを使用できる、**エンコード**ページの上部左にあるボタンをクリックします。

    ![Azure Portal](images/AzureLabs-Lab6-15.png)

15. いることができます、ファイルのオプションのエンコーディングを設定する右側で、新しいパネルが表示されます。 (一部は既に既定で設定)、次のプロパティを設定します。

    1.  **メディア エンコーダー名*Media Encoder Standard***

    2.  **エンコード プリセット*コンテンツ アダプティブ マルチビット レート MP4***

    3.  **ジョブ名*Video1.mp4 の Media Encoder Standard の処理***

    4.  **出力メディア資産名*Video1.mp4--Media Encoder Standard のエンコード***

        ![Azure Portal](images/AzureLabs-Lab6-16.png)

16. **[作成]** をクリックします。

17. 使用して、バーが表示されます**追加エンコード ジョブ**そのバーをクリックして、パネルが表示されているエンコードの進行状況で表示されます。

    ![Azure Portal](images/AzureLabs-Lab6-17.png)

    ![Azure Portal](images/AzureLabs-Lab6-18.png)

18. ジョブが完了するまで待ちます。 これを完了すると、自由に、そのパネルの右上にある 'X' でパネルを閉じます。

    ![Azure Portal](images/AzureLabs-Lab6-19.png)

    ![Azure Portal](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > これにより、時間は、ビデオのファイルのサイズによって異なります。 このプロセスには、かなりの時間がかかります。

19. ビデオのエンコードされたバージョンを作成すると、アクセスできるようにすることを発行できます。 これを行うには、青色のリンクをクリックします。**資産**資産のページに戻ります。

    ![Azure Portal](images/AzureLabs-Lab6-21.png)

20. 別のあると共に、ビデオが表示されます * * 資産の種類 * マルチビット レート MP4 * * *。

    ![Azure Portal](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > 初期ビデオ、と共に、新しい資産がであることがわかります*不明な*、に対しては、'0' バイトを持つと**サイズ**、だけを更新するため、ウィンドウを更新します。

21. この新しい資産をクリックします。

    ![Azure Portal](images/AzureLabs-Lab6-23.png)

22. 前に、さまざまな資産は、これを使用したものと同様のパネルが表示されます。 をクリックして、**発行**ページの上部中央にあるボタンをクリックします。

    ![Azure Portal](images/AzureLabs-Lab6-24.png)

23. 設定を求め、**ロケーター**ファイル/秒で、資産へのエントリ ポイントであります。 自分のシナリオには、次のプロパティを設定します。

    1.  **ロケーターの種類** > **プログレッシブ**します。

    2.  **日付**と**時間**に設定されますが、現在の日付から、将来の時刻 (ここでは 100 年)。 か、変更に合わせてままにします。

    > [!NOTE]
    > 詳細については、ロケーター、および選択することができます、次を参照してください。、 [Azure Media Services のドキュメント](https://docs.microsoft.com/azure/media-services/media-services-concepts)します。

24. そのパネルの下部で、をクリックして、**追加**ボタンをクリックします。

    ![Azure Portal](images/AzureLabs-Lab6-25.png)

25. ビデオが発行されましたと、そのエンドポイントを使用してストリーミングできます。 ページがダウンをさらに、**ファイル**セクション。 これは、ビデオのエンコードされたバージョンが表示されます。 いずれかの最も高い解像度を選択します (下の画像が 1920 x 960 ファイル) とし、右側のパネルが表示されます。 サイトでは、**ダウンロード URL**します。 このコピー**エンドポイント**コードで使用するためです。

    ![Azure Portal](images/AzureLabs-Lab6-26.png)    

    ![Azure Portal](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > 押すことも、**再生**ボタン、ビデオを再生し、テストします。

26. このラボで使用する 2 番目のビデオをアップロードする必要があります。 2 番目のビデオに同じプロセスを繰り返し、上記の手順に従います。 2 番目のコピー**エンドポイント**もします。 次を使用して、 [2 番目のビデオをダウンロードするリンク](https://vimeo.com/214402865)します。

27. 両方のビデオが公開されると、次のチャプターに移動する準備が整いました。

## <a name="chapter-3---setting-up-the-unity-project"></a>第 3 章 - Unity プロジェクトの設定

次のコード例が Mixed Reality での開発の一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。

1.  開いている**Unity**クリック**新規**します。 

    ![Azure Portal](images/AzureLabs-Lab6-28.png)

2.  Unity プロジェクト名を指定する必要がありますこれで挿入**MR\_360VideoStreaming。** します。 必ず、プロジェクトの種類に設定されて**3D**します。 場所で該当する別の場所を設定します (ただし、ルート ディレクトリに近づけるためのより良い)。 をクリックし、**プロジェクトの作成**です。

    ![Azure Portal](images/AzureLabs-Lab6-29.png)

3.  既定値を確認する必要が開いている Unity、**スクリプト エディター**に設定されている**Visual Studio。** 移動して***編集**設定*** し、新しいウィンドウに移動**外部ツール**します。 変更**External Script Editor**に**Visual Studio 2017**します。 閉じる、**設定**ウィンドウ。

    ![Azure Portal](images/AzureLabs-Lab6-30.png)

4.  次に移動***ファイル* *Build Settings*** にプラットフォームを切り替えると**ユニバーサル Windows プラットフォーム**をクリックして**スイッチ プラットフォーム**ボタンをクリックします。

5.  確認します。

    1. **デバイスを対象に**に設定されている**任意のデバイス。**
    
    2.  **ビルドの種類**に設定されている**D3D します。**

    3.  **SDK**に設定されている**最新バージョンをインストールします。**

    4.  **Visual Studio バージョン**に設定されている**最新バージョンをインストールします。**

    5.  **ビルドおよび実行**に設定されている**ローカル コンピューター。**

    6.  設定する方法について気にかけないように**シーン**今を後でこの設定は、します。

    7.  残りの設定は、ここでは、既定値として残しておく必要があります。

        ![Unity プロジェクトの設定](images/AzureLabs-Lab6-31.png)

6.  **Build Settings**ウィンドウの**プレーヤー設定**ボタン、領域に関連するパネルが開き、**インスペクター**が配置されています。 

7. このパネルは、いくつかの設定を確認する必要があります。

    1.  **その他の設定** タブ。

        1.  **Scripting** **ランタイム バージョン**する必要があります**安定した**(.NET 3.5 相当)。

        2. **バックエンドの scripting**べき **.NET。**

        3. **API の互換性レベル**べき **.NET 4.6 です。**

            ![Unity プロジェクトの設定](images/AzureLabs-Lab6-32.png)

    2.  パネル、下の方に**XR 設定**(次に示します**発行設定**)、ティック**仮想現実サポート**、ことを確認、 **Windows Mixed Reality SDK**が追加されます。

        ![Unity プロジェクトの設定](images/AzureLabs-Lab6-33.png)

    3.  内で、**発行の設定**] タブの [**機能**、確認してください。

        - **InternetClient**

            ![Unity プロジェクトの設定](images/AzureLabs-Lab6-34.png)

8.  これらの変更を行った場合、閉じる、 **Build Settings**ウィンドウ。

9.  プロジェクトを保存 **ファイル** * * プロジェクトを保存します。



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a>第 4 章 - InsideOutSphere Unity パッケージをインポートします。

> [!IMPORTANT]
> スキップする場合、 *Unity を設定する*コンポーネントのこのコースで、コードにまっすぐコンティニュし、自由にこれをダウンロード[.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage)、としてプロジェクトにインポート、 [ **カスタム パッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)から続けて**第 5 章**します。 Unity プロジェクトを作成する必要があります。

このコースは Unity Asset のパッケージをダウンロードする必要がありますと呼ばれる[ **InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage)します。

インポートの操作方法に関する、 **unitypackage**:

1.  前 [Unity ダッシュ ボード] をクリックして**資産**画面の上部にあるメニューでクリックして**パッケージのインポート > カスタム パッケージ**します。

    ![InsideOutSphere Unity パッケージをインポートします。](images/AzureLabs-Lab6-35.png)

2.  ファイル ピッカーを使用して、 **InsideOutSphere.unitypackage**パッケージ化し、をクリックして**オープン**します。 この資産のコンポーネントの一覧が表示されます。 クリックして、インポートを確認します。**インポート**します。

    ![InsideOutSphere Unity パッケージをインポートします。](images/AzureLabs-Lab6-36.png)

3.  これには、インポートが完了したら後、は、3 つの新しいフォルダーが表示されます**資料**、**モデル**、および**プレハブ**に追加されている、**資産**フォルダー。 このようなフォルダー構造は、Unity プロジェクトの一般的なものです。

    ![InsideOutSphere Unity パッケージをインポートします。](images/AzureLabs-Lab6-37.png)

    1.  開く、**モデル**フォルダーが表示されますが、 **InsideOutSphere**モデルがインポートされています。

    2.  内で、**資料**フォルダーが表示されます、 **InsideOutSpheres**マテリアル*lambert1*と呼ばれるマテリアルと共に*ButtonMaterial*、すぐに表示される GazeButton によって使用されます。

    3.  **プレハブ**フォルダーが含まれています、 **InsideOutSphere**プレハブの両方を含む、 **InsideOutSphere** *モデル*と、 *GazeButton*します。

    4.  **コードが含まれていない**、このコースで、コードを記述します。


4.  内で、**階層**を選択、 **Main Camera**オブジェクトし、次のコンポーネントの更新します。

    1.  **変換**

        1.  位置 = **X**:0、 **Y**:0、 **Z**:0。

        2. 回転 = **X**:0、 **Y**:0、 **Z**:0。

        3. スケール**X**:1、 **Y**:1、 **Z**:1. 

    2.  **カメラ**

        1. **フラグをクリア**:純色です。

        2.  **Clipping**:ほぼ。0.1、はるかに:6。

            ![InsideOutSphere Unity パッケージをインポートします。](images/AzureLabs-Lab6-38.png)

5.  移動し、**プレハブ**フォルダー、およびドラッグ、 **InsideOutSphere**にプレハブ、**階層**パネル。

    ![InsideOutSphere Unity パッケージをインポートします。](images/AzureLabs-Lab6-39.png)

6.  展開、 **InsideOutSphere**オブジェクト内の**階層**を横にある小さな矢印をクリックします。 表示されます、**子**と呼ばれるその下にあるオブジェクト**GazeButton**します。 シーンおよびビデオを変更するために使用されます。

    ![InsideOutSphere Unity パッケージをインポートします。](images/AzureLabs-Lab6-40.png)

7.  インスペクター ウィンドウをクリックして、 **InsideOutSphere**の変換コンポーネントを次のプロパティを設定することを確認します。

    |            |    変換の位置   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |    変換の回転   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** -50        |  **Z** 0  |

    |            |     変換のスケール     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![InsideOutSphere Unity パッケージをインポートします。](images/AzureLabs-Lab6-41.png)

8.  をクリックして、 **GazeButton** 、子オブジェクトとその**変換**次のように。

    |            |    変換の位置   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 3.6|          **Y** 1.3        |  **Z** 0  |

    |            |    変換の回転   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     変換のスケール     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![InsideOutSphere Unity パッケージをインポートします。](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a>5 - 章 VideoController クラスを作成します。

**VideoController**クラスは、Azure メディア サービスからコンテンツをストリーミングに使用される 2 つのビデオのエンドポイントをホストします。

このクラスを作成します。

1.  右クリックし、**アセット フォルダー**にある、**プロジェクト**パネル をクリックします**作成 > フォルダー**します。 フォルダーの名前**スクリプト**します。

    ![VideoController クラスを作成します。](images/AzureLabs-Lab6-43.png)

    ![VideoController クラスを作成します。](images/AzureLabs-Lab6-44.png)

2.  ダブルクリック、**スクリプト**フォルダーを開きます。

3.  フォルダー内を右クリックし、をクリックして**作成 > C\#スクリプト**します。 スクリプトの名前**VideoController**します。

    ![VideoController クラスを作成します。](images/AzureLabs-Lab6-45.png)

4.  新しいをダブルクリックします。 **VideoController**スクリプト ファイルを開く**Visual Studio 2017。**

    ![VideoController クラスを作成します。](images/AzureLabs-Lab6-46.png)

5.  次のように、コード ファイルの上部にある名前空間を更新します。

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  次の変数を入力、 **VideoController**クラス、と共に、 **Awake()** メソッド。

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  ここは、Azure Media Service のビデオから、エンドポイントを入力します。

    1.  最初に、 *video1endpoint*変数。
    
    2.  2 番目に、 *video2endpoint*変数。

    > [!WARNING]
    > 使用して既知の問題がある*https*バージョン 2017.4.1f1 で、Unity 内で。 ビデオでは、プレイのエラーを提供する場合、は、'http' を代わりを使用してみてください。

8.  次に、 **Start()** メソッドを編集する必要があります。 このメソッドは、ユーザーは、視線のボタンを調べることでシーン (その結果、ビデオの切り替え) を切り替えるたびにトリガーされます。

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  次の**Start()** メソッド、挿入、 **PlayVideo()** *IEnumerator*メソッドは、シームレスに (そのため途切れるは表示されません)、ビデオを開始するために使用されます。

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. このクラスは必要がある最後のメソッド、 **ChangeScene()** メソッドは、シーンの間でスワップするために使用されます。

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > **ChangeScene()** メソッドは便利な C を使用して\#と呼ばれる機能、*条件演算子*します。 これにより、条件をチェックできるし、値に基づいて返される 1 つのステートメント内ですべてのチェックの結果。 この後に[条件演算子の詳細へのリンク](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator)します。

11. Visual Studio で Unity に戻る前に、変更を保存します。

12. 戻る Unity エディターで、をクリックし、ドラッグ、 **VideoController** [から] {.underline} クラス、**スクリプト**フォルダーを**Main Camera**オブジェクト、 **階層**パネル。

13. をクリックして、 **Main Camera**を見て、**インスペクター パネル**します。 新しく追加されたスクリプト コンポーネント内が空の値を持つフィールドが表示されます。 これは、参照フィールドが、コード内のパブリック変数を対象としたものです。

14. ドラッグ、 **InsideOutSphere**オブジェクトから、**階層パネル**を**球**スロット、次の図に示すようにします。

    ![VideoController クラスを作成](images/AzureLabs-Lab6-47.png)
    ![VideoController クラスを作成](images/AzureLabs-Lab6-48.png)

## <a name="chapter-6---create-the-gaze-class"></a>第 6 章 - 視線の先クラスを作成します。

作成するため、このクラスは、 **Raycast**は beprojected を転送することから、 **Main Camera**ユーザーが見るオブジェクトを検出します。 この場合、 **Raycast**で、ユーザーが探している場合を識別する必要があります、 **GazeButton**シーン内のオブジェクトし、動作をトリガーします。

このクラスを作成します。

1.  移動して、**スクリプト**以前に作成したフォルダーです。

2.  右クリックし、**プロジェクト**パネルで、**作成** C\#スクリプト * *。 スクリプトの名前**視線**します。

3.  新しいをダブルクリックします。***視線***スクリプト ファイルを開く**Visual Studio 2017。**

4.  次の名前空間は、スクリプトの上部にあることを確認し、その他の要素を削除します。

    ```csharp
    using UnityEngine;
    ```

5.  内で、次の変数を追加し、**視線**クラス。

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  コードを**Awake()** と**Start()** 今すぐメソッドを追加する必要があります。

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  次のコードを追加、 **Update()** メソッドは、Raycast のプロジェクトをターゲット ヒットを検出します。

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  Visual Studio で Unity に戻る前に、変更を保存します。

9.  クリックしてドラッグし、**視線**Scripts フォルダーからクラスの Main Camera オブジェクトを**階層**パネル。

## <a name="chapter-7---setup-the-two-unity-scenes"></a>第 7 章 – セットアップ、2 つの Unity シーン

この章の目的は、2 つのシーンでは、ビデオ ストリームを各ホストをセットアップすることです。 既に作成してシーンを重複していますが必要はありません、もう一度設定するには、新しいシーンを編集し、ように、 *GazeButton*オブジェクトは、別の場所ではあり、異なる外観です。 これは、シーンの間で変更する方法を説明します。

1.  これには**ファイル > としてシーンを保存しています.**.保存ウィンドウが表示されます。 をクリックして、**新しいフォルダー**ボタンをクリックします。

    ![第 7 章 – セットアップ、2 つの Unity シーン](images/AzureLabs-Lab6-49.png)

2.  フォルダーの名前**シーン**します。

3.  **Save Scene**ウィンドウは開いたままになっています。 新たに作成した開く**シーン**フォルダー。

4.  **ファイル名:** テキスト フィールドに「 **VideoScene1**、キーを押します**保存**します。

5.  Unity で開く、**シーン**フォルダー、および左クリック、 **VideoScene1**ファイル。 キーボードを使用してキーを押します**Ctrl + D**そのシーンは、重複します。

    > [!TIP]
    > **複製**に移動してコマンドを実行することも**編集 > が重複しています**します。

6.  Unity は自動的に、シーン名の番号をインクリメントが、以前に挿入されたコードと一致することを確認するか、チェックします。

    >  おく**VideoScene1**と**VideoScene2**します。

7.  移動すると、2 つのシーン**ファイル > Build Settings**します。 **Build Settings**ウィンドウを開いて、ドラッグ、シーン、**ビルド内のシーン**セクション。

    ![第 7 章 - 2 つの Unity シーンをセットアップします。](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > シーンの両方を選択することができます、**シーン**で保持しているフォルダに、 **Ctrl**ボタンをクリックすると、各シーンを左クリックし、最後に両方の間でドラッグします。

8.  閉じる、 **Build Settings**ウィンドウ、およびダブルクリック**VideoScene2**します。

9.  開いている 2 つ目のシーンを をクリックして、 **GazeButton**の子オブジェクト、 **InsideOutSphere**、し、その変換を次のように設定します。

    |            |    変換の位置   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |         **Y** 1.3         | **Z** 3.6 |

    |            |    変換の回転   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     変換のスケール     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

10. **GazeButton**が選択されている参照に子、**インスペクター**で、**メッシュ フィルター**します。 次に、ほとんどのターゲットをクリックして、**メッシュ**参照フィールド。

    ![第 7 章 - 2 つの Unity シーンをセットアップします。](images/AzureLabs-Lab6-51.png)

11. A**メッシュ選択**ポップアップ ウィンドウが表示されます。 ダブルクリックして、**キューブ**の一覧からメッシュ**資産**します。

    ![第 7 章 - 2 つの Unity シーンをセットアップします。](images/AzureLabs-Lab6-52.png)

12. **メッシュ フィルター**更新、およびようになりますが、**キューブ**します。 をクリックして、**歯車**隣にアイコン**球 Collider**  をクリック**コンポーネントの削除**、このオブジェクトから、コライダーを削除します。

    ![第 7 章 - 2 つの Unity シーンをセットアップします。](images/AzureLabs-Lab6-53.png)

13. **GazeButton**クリックしてが選択されている、**コンポーネントの追加**の下部にあるボタン、**インスペクター**します。 検索フィールドに「**ボックス**、および**足場に Box Collider**オプションを選択できます--を追加する をクリック、**足場に Box Collider**を**GazeButton**オブジェクト.

    ![第 7 章 - 2 つの Unity シーンをセットアップします。](images/AzureLabs-Lab6-54.png)

14. **GazeButton**が部分的に更新されました、外観が異なる、ただしはこれで新規に作成する**マテリアル**いるため、まったく違ってしてよりも、別のオブジェクトとして認識する方が簡単ですが、最初のシーン内のオブジェクト。

15. 移動し、**資料**フォルダー内で、**プロジェクト パネル**します。 重複しています、 **ButtonMaterial**マテリアル (キーを押して**Ctrl** + **D**キーボード、または左クリックで、**マテリアル**、し、**編集**ファイル メニュー オプションを選択し**複製**)。

    ![第 7 章 - セットアップ、2 つの Unity シーン](images/AzureLabs-Lab6-55.png)
    ![章 7 - 2 つの Unity シーンをセットアップします。](images/AzureLabs-Lab6-56.png)

16. 新しい**ButtonMaterial**マテリアル (という名前**ButtonMaterial 1**)、内で、**インスペクター**、クリックして、 **Albedo**色ウィンドウです。 ポップアップが表示され、別の色を選択できます (などのどちらを選択) し、ポップアップを閉じます。 マテリアルは独自のインスタンスをしては異なる元。

    ![第 7 章 - 2 つの Unity シーンをセットアップします。](images/AzureLabs-Lab6-57.png)

17. 新しいドラッグ**マテリアル**上に、 **GazeButton**子がここでは最初のシーン ボタンから簡単に区別できるように完全にそのファイルの場所を更新します。

    ![第 7 章 - 2 つの Unity シーンをセットアップします。](images/AzureLabs-Lab6-58.png)

18. この時点で、UWP プロジェクトをビルドする前に、エディターでプロジェクトをテストできます。

    -  キーを押して、**再生**ボタン、**エディター**ヘッドホンを着用とします。

        ![第 7 章 - 2 つの Unity シーンをセットアップします。](images/AzureLabs-Lab6-59.png)

19. 2 つを見て**GazeButton**最初と 2 番目のビデオを切り替えるオブジェクト。

## <a name="chapter-8---build-the-uwp-solution"></a>第 8 章 - UWP ソリューションのビルド

エディターにエラーが含まれていないことを確認して後、は、ビルドする準備が整ったらします。

作成する方法。

1.  現在のシーンを保存 をクリックして**ファイル > 保存**します。

2.  チェック ボックスと呼ばれる**Unity C\#プロジェクト**(これは重要なビルドが完了した後に、クラスを編集することを許可することがあるため)。

3.  移動して**ファイル > Build Settings**、 をクリックして**ビルド**します。

4.  ソリューションを構築するフォルダーを選択するように促されます。

5.  作成、**ビルド**フォルダーとそのフォルダー内には、任意の適切な名前を別のフォルダーを作成します。

6.  新しいフォルダーをクリックし、クリックして**フォルダーの選択**、その場所にビルドを開始する、そのフォルダーを選択するようにします。

    ![第 8 章 - UWP ソリューションをビルドする](images/AzureLabs-Lab6-60.png)
    ![章 - 8 UWP ソリューションをビルドします。](images/AzureLabs-Lab6-61.png)

7.  1 回 Unity には、(少し時間がかかる場合があります) ビルドが完了したが開き、**ファイル エクスプ ローラー**ビルドの位置にあるウィンドウ。

## <a name="chapter-9---deploy-on-local-machine"></a>9 -」の章をローカル コンピューターに展開します。

ビルドが完了したら、**ファイル エクスプ ローラー**ビルドの場所にウィンドウが表示されます。 という名前のフォルダーをビルドを開き、Visual Studio 2017 でのソリューションを開くには、そのフォルダー内のソリューション (.sln) ファイルをダブルクリックします。

実行するですだけが、コンピューターにアプリのデプロイ (または*ローカル マシン*)。

ローカル コンピューターに展開します。

1.  **Visual Studio 2017**が作成されたソリューション ファイルを開きます。

2.  **ソリューション プラットフォーム**、 **x86、ローカル コンピューター**します。

3.  **ソリューション構成**選択**デバッグ**します。

    ![ローカル コンピューター上の第 9 章 - 展開します。](images/AzureLabs-Lab6-62.png)

4.  これで、ソリューションにすべてのパッケージを復元する必要があります。 右クリックし、**ソリューション**、 をクリック**ソリューションの NuGet パッケージを復元しています.**

    > [!NOTE] 
    > これは Unity が組み込まれているパッケージは、ローカル コンピューターの参照を使用する対象とする必要があるためです。

5.  移動して**ビルド メニューの** をクリック**ソリューションの配置**をコンピューターにアプリケーションをサイドローディングします。 Visual Studio は最初にビルドし、アプリケーションをデプロイします。

6.  アプリが起動する準備ができて、インストールされているアプリの一覧に表示されます。

    ![ローカル コンピューター上の第 9 章 - 展開します。](images/AzureLabs-Lab6-63.png)

内には、複合現実のアプリケーションを実行するときに、 **InsideOutSphere**アプリ内で使用したモデル。 この球体になります、ビデオをストリーミングするのには、(これは、この種類のパースペクティブのアスペクトが)、受信するビデオの 360 度ビューを提供します。 驚かないでください、アプリが、使用可能なインターネットの速度の対象は、ビデオがいくつかの読み込みに数秒を受け取る場合にフェッチされ、ダウンロードし、アプリにストリーミングするために、ビデオが必要です。
準備ができたら、シーンを変更して、gazing 赤い球にして、2 番目のビデオを開きます。 自由に戻ると、2 つ目のシーン内の青色の立方を使用して!

## <a name="your-finished-azure-media-service-application"></a>完成した Azure Media Service アプリケーション
 
これで、360 ビデオをストリーミングする Azure Media Service を利用している mixed reality アプリを構築します。

![ラボの結果](images/AzureLabs-Lab6-00.png)

![ラボの結果](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a>ボーナスの演習

**手順 1**

のみ 1 つのシーンを使用して、このチュートリアルでビデオを変更することは可能になります。 アプリケーションを試してみてを 1 つのシーンに! おそらく、ミックスにも別のビデオを追加します。

**手順 2**

Azure と Unity、実験し、ビデオをインターネット接続の強度によって、別のファイル サイズを自動的に選択するアプリの機能を実装しようとしてください。


