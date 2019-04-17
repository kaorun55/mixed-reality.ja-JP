---
title: MR と Azure 312 - Bot の統合
description: 作成し、Microsoft Bot Framework v4 を使用して、ボットをデプロイする方法については、このコースを完了し、複合現実のアプリケーションで通信します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、コンピューター ビジョン、hololens、没入型、vr、microsoft bot framework v4、web app bot、bot framework、microsoft bot
ms.openlocfilehash: b828aa4415103d280459bd2c666004c994b3e59d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604981"
---
>[!NOTE]
>Mixed Reality Academy チュートリアルでは、HoloLens として設計された (第 1 世代) と混在の現実イマーシブ ヘッドセットに注意してください。  そのため、これらのデバイス向けの開発にガイダンスがまだ必要な開発者のための場所でこれらのチュートリアルのままにすることが重要と思われます。  これらのチュートリアルは**_いない_** 最新のツールセットや相互作用が使用されている HoloLens 2 で更新されます。  サポートされているデバイスで作業を続行するが保持されます。 一連の新しい HoloLens 2 を開発する方法を示すチュートリアルは、今後投稿があります。  この通知が投稿されるときにこれらのチュートリアルへのリンクが更新されます。

# <a name="mr-and-azure-312-bot-integration"></a>MR と Azure 312:ボットの統合

このコースでは、作成して、Microsoft Bot Framework V4 を使用してボットをデプロイし、Windows Mixed Reality アプリケーションを介して通信する方法を学びます。 

![](images/AzureLabs-Lab312-00.png)

**Microsoft Bot Framework V4**一連の Api は、拡張可能かつスケーラブルなボットをビルドするツールを開発者に提供するように設計されてアプリケーション。 詳細については、次を参照してください。、 [Microsoft Bot Framework ページ](https://dev.botframework.com/)または[V4 の Git リポジトリ](https://github.com/Microsoft/botbuilder-dotnet/wiki)します。

このコースを完了するは、次のことが Windows Mixed Reality アプリケーションを構築したは。

1. 使用して、**タップ ジェスチャ**ボット ユーザー ボイスのリッスンを開始します。
2. 何か、ユーザーが話したが、ボットは、応答を提供しようとします。
3. Unity シーンでボットに近くに配置されたテキストとしてボットの応答を表示します。

アプリケーションでは、責任ですが、設計と、結果を統合する方法について。 このコースは、Unity プロジェクトで Azure サービスを統合する方法を説明する設計されています。 複合現実アプリを強化するためには、このコース得た知識を使用することがあります。

## <a name="device-support"></a>デバイスのサポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 312:ボットの統合</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> このコースは、HoloLens で主にフォーカスします、Windows Mixed Reality 没入型 (VR) ヘッドセットには、このコースで学習する内容を適用することもできます。 (VR) のイマーシブ ヘッドセットはアクセス可能な cameras があるないため、外部のカメラを PC に接続されている必要があります。 コースを実行するとき、没入型の (VR) ヘッドセットをサポートするために使用する必要があります変更でノートが表示されます。

## <a name="prerequisites"></a>前提条件

> [!NOTE]
> このチュートリアルは、Unity を使用した基本的な経験がある開発者向けに設計およびC#します。 また、前提条件やこのドキュメント内の書面の手順を表すテストおよび (2018 年 7 月) の書き込み時に検証されたがどのようなことに注意してください。 内に一覧表示するには自由に最新のソフトウェアを使用して、[ツールをインストールする](install-the-tools.md)にする必要がありますが想定されていなかったことについては、このコースでとまったく同じで記載されているものよりも新しいソフトウェアで表示されますが、記事以下に。

次のハードウェアとソフトウェアこのコースをお勧めします。

- 開発用 PC、a [Windows Mixed Reality と互換性のある](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)(VR) ヘッドセットの没入型の開発
- [Windows 10 Fall Creators Update (またはそれ以降) で開発者モードが有効になっています。](install-the-tools.md#installation-checklist)
- [最新の Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- A [Windows Mixed Reality 没入型 (VR) ヘッドセット](immersive-headset-hardware-details.md)または[Microsoft HoloLens](hololens-hardware-details.md)開発者モードが有効
- Azure と Azure Bot 取得するためのインターネット アクセス。 詳細については、[このリンクに従ってください](https://dev.botframework.com/)します。

### <a name="before-you-start"></a>開始前の作業

1.  このプロジェクトのビルドの問題の発生を避けるため、強くお勧めのルートまたはルート近くフォルダーでこのチュートリアルで説明したようにプロジェクトを作成すること (長いフォルダー パスはビルド時に問題を発生できます)。
2.  設定して、HoloLens をテストします。 場合は、HoloLens の設定をサポートする必要がある[HoloLens のセットアップ記事を参照してください。 確認](https://docs.microsoft.com/hololens/hololens-setup)します。 
3.  (場合によって役立ちますユーザーごとにこれらのタスクを実行する) 新しい HoloLens アプリの開発を始めるときに、調整とセンサーのチューニングを実行することをお勧めします。 

調整に関するヘルプを参照するに従ってくださいこの[HoloLens 調整記事へのリンク](calibration.md#hololens)します。

センサーの調整に関する詳細についてに従ってくださいこの[HoloLens センサー チューニング記事へのリンク](sensor-tuning.md)します。

## <a name="chapter-1--create-the-bot-application"></a>第 1 章 – ボット アプリケーションを作成します。

最初の手順では、ローカル ASP.Net Core Web アプリケーションとしてのお客様のボットを作成します。 完了し、テストが、Azure ポータルに発行します。

1.  Visual Studio を開きます。 新しいプロジェクトを作成**ASP NET Core Web アプリケーション**(は検索、.NET Core のサブセクションの下) プロジェクトの種類として、呼び出す**MyBot**します。 **[OK]** をクリックします。

2.  表示されるウィンドウで**空**します。 またことを確認して、ターゲットに設定されて**ASP NET Core 2.0** 、認証に設定されてと**認証なし**。 **[OK]** をクリックします。  

    ![ボット アプリケーションを作成します。](images/AzureLabs-Lab312-01.png)

3.  ソリューションを開きます。 ソリューションを右クリックして**Mybot**で、**ソリューション エクスプ ローラー**  をクリック**ソリューションの NuGet パッケージの管理**します。 

    ![ボット アプリケーションを作成します。](images/AzureLabs-Lab312-02.png)

4.  **参照** タブで、検索**Microsoft.Bot.Builder.Integration.AspNet.Core** (があるかどうかを確認**プレリリースを含める**チェック)。 パッケージのバージョンを選択します。 **4.0.1-preview**、し、プロジェクトのボックスをオンにします。 をクリックして**インストール**します。 必要なライブラリがインストールされているようになりました、 **Bot Framework v4**します。 NuGet ページを閉じます。

    ![ボット アプリケーションを作成します。](images/AzureLabs-Lab312-03.png)

5.  右クリックし、*プロジェクト*、 **MyBot**の**ソリューション エクスプ ローラー**  をクリック**追加** **|****クラス**します。

    ![ボット アプリケーションを作成します。](images/AzureLabs-Lab312-04.png)

6.  クラスの名前**MyBot**  をクリック**追加**します。

    ![ボット アプリケーションを作成します。](images/AzureLabs-Lab312-05.png)

7.  という名前の別のクラスを作成する前のポイントを繰り返して**ConversationContext**します。 

8.  右クリックして**wwwroot**で、**ソリューション エクスプ ローラー** ] をクリック**追加** **|** **[新しい項目**. 選択**HTML ページ**(が見つかったら Web サブセクションの下)。 ファイルに名前を**default.html**します。 **[追加]** をクリックします。

    ![ボット アプリケーションを作成します。](images/AzureLabs-Lab312-06.png)

9.  クラスの一覧内のオブジェクト/、**ソリューション エクスプ ローラー**次の図のようになります。

    ![ボット アプリケーションを作成します。](images/AzureLabs-Lab312-07.png)

10. ダブルクリックして、 **ConversationContext**クラス。 このクラスは、メッセージ交換のコンテキストを維持するために、ボットで使用される変数を保持する責任を負います。 ため、これらのメッセージ交換コンテキスト値が、このクラスのインスタンスで保持されるの任意のインスタンス、 **MyBot**クラスは、アクティビティが受信されるたびに更新されます。 このクラスに次のコードを追加します。

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. ダブルクリックして、 **MyBot**クラス。 このクラスは、顧客から任意の受信アクティビティによって呼び出されるハンドラーをホストします。 このクラスは、ボットと顧客の間でメッセージ交換を構築するために使用するコードを追加します。 前述のように、このクラスのインスタンスはアクティビティが受信されるたびに初期化されます。 このクラスには、次のコードを追加します。

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. ダブルクリックして、**スタートアップ**クラス。 このクラスは、ボットを初期化します。 このクラスに次のコードを追加します。

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. 開く、**プログラム**クラス ファイルおよび内のコードは、次の場合と同じことを確認します。

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. 移動するためには、変更を保存する**ファイル** > **すべて保存**、Visual Studio の上部にあるツールバーから。

## <a name="chapter-2---create-the-azure-bot-service"></a>Chapter 2 - Azure Bot Service を作成します。

インスタンスに公開がお客様のボットのコードを作成したら、これで、 *Web App Bot* Azure Portal でのサービスです。 この章では、作成、azure Bot Service を構成して、コードを発行する方法を示します。

1.  最初に、Azure ポータルにログイン (https://portal.azure.com)します。 

    1. Azure アカウントがいない場合は、1 つを作成する必要があります。 クラスルームまたはラボのような状況では、このチュートリアルをフォローしている場合は、講師または新しいアカウントのセットアップについて proctors のいずれかにお問い合わせください。

2.  ログインした後は、をクリックして**リソースの作成**左上隅にある検索して*Web App bot*、 をクリック**Enter**します。

    ![Azure Bot Service を作成します。](images/AzureLabs-Lab312-08.png)
 
3.  新しいページがの説明を入力、 *Web App Bot*サービス。 このページの左下にある at、**作成**ボタンは、この関連付けサービスを作成します。

    ![Azure Bot Service を作成します。](images/AzureLabs-Lab312-09.png)
 
4.  クリックすると**作成**:

    1. 必要な挿入**名前**このサービス インスタンス。
    2. 選択、**サブスクリプション**します。
    3. 選択、**リソース グループ**か新規に作成します。 リソース グループは、監視、プロビジョニングのアクセスを制御および Azure の資産のコレクションの課金を管理する方法を提供します。 勧めします (例: これらのコース) などの 1 つのプロジェクトに共通のリソース グループの下の Azure サービスに関連付けられているすべて保持する)。

        > 詳細にする場合、Azure リソース グループについて[このリンクに従ってください](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4. (新しいリソース グループを作成する) 場合は、リソース グループの場所を決定します。 場所は、アプリケーションが実行リージョンにあるが理想的です。 一部の Azure 資産は特定のリージョンでのみ使用できます。
    5. 選択、**価格レベル**場合、これは、最初に、適切な時間を作成する、 *Web App Bot*サービス、(F0 という名前)、free レベルを使用可能にする必要があります
    6. **アプリ名**だけおくことができますと同じ、*ボット名*します。 
    7. ままに、 *Bot テンプレート*として**基本的な (C#)** します。
    8. *App service プラン/場所*アカウントに自動的に入力されている必要があります。
    9. 設定、 **Azure Storage**を使用して、ボットをホストします。 既にいずれかがあるない場合、ここで作成することができます。
    10. また、このサービスに適用される条件を理解したことを確認する必要があります。
    11. [作成] をクリックします。
 
        ![Azure Bot Service を作成します。](images/AzureLabs-Lab312-10.png)

5.  クリックすると**作成**サービスを作成するを待機する必要があります、これは少し時間がかかる場合があります。

6.  通知は、サービス インスタンスが作成されたら、ポータルに表示されます。

    ![Azure Bot Service を作成します。](images/AzureLabs-Lab312-11.png) 
 
7.  新しいサービス インスタンスを探索する通知をクリックします。 

    ![Azure Bot Service を作成します。](images/AzureLabs-Lab312-12.png)
 
8. をクリックして、**リソースに移動**通知では、新しいサービス インスタンスを表示するボタンをクリックします。 新しい Azure サービス インスタンスに表示されます。 

    ![Azure Bot Service を作成します。](images/AzureLabs-Lab312-13.png)
 
9.  この時点でと呼ばれる機能をセットアップする必要があります**Direct Line**このボット サービスと通信するクライアント アプリケーションを許可します。 をクリックして**チャネル**、次に、**おすすめチャンネルの追加**セクションで、をクリックして**構成 Direct Line channel**します。

    ![Azure Bot Service を作成します。](images/AzureLabs-Lab312-14.png)

10. このページでは紹介、**秘密鍵**クライアント アプリ、ボットと認証を行うことができます。 をクリックして、**表示**ボタンをクリックし、プロジェクトの後半で必要になるように、表示されているキーの 1 つのコピーを作成します。 

    ![Azure Bot Service を作成します。](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a>第 3 章 – ボットを Azure Web App Bot のサービスに発行します。

準備ができたら、サービス、以前は、新しく作成された Web App Bot Service を作成したボット コードを発行する必要があります。

> [!NOTE] 
> ボットのソリューションに変更を加えるたびに、Azure サービスにお客様のボットを発行する必要があります/コードします。

1.  以前作成した Visual Studio ソリューションに戻ります。 
2.  右クリックし、 **MyBot**プロジェクトの**ソリューション エクスプ ローラー**の **発行**します。

    ![ボットを Azure Web App Bot Service に発行します。](images/AzureLabs-Lab312-16.png)

3.  *発行先を選択* ページで  **App Service**、し**既存の**、最後に、をクリックして**プロファイルの作成**(する必要があります横のドロップダウン矢印をクリックして、*発行*ボタンが表示されない場合)。

    ![ボットを Azure Web App Bot Service に発行します。](images/AzureLabs-Lab312-17.png)

4. まだログインいない Microsoft アカウントに場合に、ここで行う必要。
5. **発行**ページには、同じように設定する必要がある**サブスクリプション**に使用した、 *Web App Bot*サービスの作成。 設定し、**ビュー**として**リソース グループ**し、フォルダー構造ドロップダウンで選択、**リソース グループ**以前に作成しました。 **[OK]** をクリックします。 

    ![ボットを Azure Web App Bot Service に発行します。](images/AzureLabs-Lab312-18.png)

6.  ここでをクリックして、**発行**ボタンをクリックし、ボットを発行するまで待ちます (少し時間がかかる場合があります)。

    ![ボットを Azure Web App Bot Service に発行します。](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a>第 4 章 – Unity プロジェクトの設定

次のコード例が複合現実での開発の一般的な設定して、そのため、他のプロジェクトの適切なテンプレートには。

1.  開いている*Unity*クリック**新規**します。 

    ![Unity プロジェクトを設定します。](images/AzureLabs-Lab312-20.png)

2.  これで、Unity プロジェクトの名前を指定する必要があります。 挿入**Hololens ボット**します。 必ず、プロジェクト テンプレートに設定されて**3D**します。 設定、**場所**に該当する別の場所 (ただし、ルート ディレクトリに近づけるためのより良い)。 をクリックし、**プロジェクトの作成**です。

    ![Unity プロジェクトを設定します。](images/AzureLabs-Lab312-21.png)

3.  既定値を確認する必要が開いている Unity、**スクリプト エディター**に設定されている**Visual Studio**します。 移動して**編集 > 設定**し、新しいウィンドウに移動**外部ツール**します。 変更**External Script Editor**に**Visual Studio 2017**します。 閉じる、**設定**ウィンドウ。

    ![Unity プロジェクトを設定します。](images/AzureLabs-Lab312-22.png)

4.  次に移動**ファイル > Build Settings**を選択し、**ユニバーサル Windows プラットフォーム**、をクリックして、**スイッチ プラットフォーム**選択内容を適用するボタンをクリックします。

    ![Unity プロジェクトを設定します。](images/AzureLabs-Lab312-23.png)

5.  **ファイル > Build Settings**ことを確認してください。

    1.  **デバイスを対象に**に設定されている**Hololens**

        > イマーシブ ヘッドセット、設定**ターゲット デバイス**に*任意のデバイス*します。

    2.  **ビルドの種類**に設定されている**D3D**

    3.  **SDK**に設定されている**インストールされている最新**

    4.  **Visual Studio バージョン**に設定されている**インストールされている最新**

    5.  **ビルドおよび実行**に設定されている**ローカル マシン**

    6.  シーンを保存し、ビルドに追加します。 

        1. これには、選択**開くシーンを追加**します。 保存ウィンドウが表示されます。
        
            ![Unity プロジェクトを設定します。](images/AzureLabs-Lab312-24.png)

        2. 新しいフォルダーを作成と、任意の将来、シーン、し、選択、**新しいフォルダー**ボタンは、新しいフォルダーを作成する名前を付けます**シーン**します。

             ![Unity プロジェクトを設定します。](images/AzureLabs-Lab312-25.png)

        3. 新たに作成した開く**シーン**フォルダー、し、*ファイル名*: テキスト フィールドに「 **BotScene**、[] をクリック**保存**。

            ![Unity プロジェクトを設定します。](images/AzureLabs-Lab312-26.png)

    7. 設定に残っている**Build Settings**、ここでは既定値として残しておく必要があります。

6. *Build Settings*ウィンドウの**プレーヤー設定**ボタン、領域に関連するパネルが開き、*インスペクター*が配置されています。 

    ![Unity プロジェクトを設定します。](images/AzureLabs-Lab312-27.png)

7. このパネルは、いくつかの設定を確認する必要があります。

    1. **その他の設定** タブ。

        1. **ランタイム バージョンをスクリプト**する必要があります**試験的 (NET 4.6 Equivalent)**; を変更すると、エディターの再起動が必要です。
        2. **バックエンドの scripting**べき **.NET**
        3. **API の互換性レベル**べき **.NET 4.6**

            ![Unity プロジェクトを設定します。](images/AzureLabs-Lab312-28.png)
      
    2. 内で、**発行の設定**] タブの [**機能**、確認してください。

        - **InternetClient**
        - **マイク**

            ![Unity プロジェクトを設定します。](images/AzureLabs-Lab312-29.png)

    3. パネル、下の方に**XR 設定**(次に示します**発行設定**)、ティック**仮想現実サポート**、ことを確認、 **Windows Mixed Reality SDK**が追加されます。

        ![Unity プロジェクトを設定します。](images/AzureLabs-Lab312-30.png)

8.  戻り*Build Settings* _Unity C#_ プロジェクトが不要になったグレー; これの横にあるチェック ボックスをオンにします。 
9.  ビルド設定ウィンドウを閉じます。
10. シーンとプロジェクトを保存 (**ファイル > SAVE SCENE/ファイル > プロジェクトの保存**)。


## <a name="chapter-5--camera-setup"></a>第 5 章 – カメラのセットアップ

> [!IMPORTANT]
> スキップする場合、 *Unity を設定する*コンポーネントのこのコースで、コードにまっすぐコンティニュし、自由にこれをダウンロード[Azure MR 312 Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage)、としてプロジェクトにインポート[**カスタム パッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)から続けて[第 7 章](#chapter-7-–-create-the-botobjects-class)します。

1.  *階層パネル*を選択、 **Main Camera**します。 
2.  すべてのコンポーネントを参照してください。 選択すると、ができる、 **Main Camera**で、*インスペクター パネル*します。

    1. **Camera オブジェクト**名前を指定する必要があります**Main Camera** (スペルに注意してください)
    2. Main Camera**タグ**に設定する必要があります**MainCamera** (スペルに注意してください)
    3. 必ず、**変換位置**に設定されている**0, 0, 0**
    4. 設定**フラグをクリア**に**単色**します。
    5. 設定、**バック グラウンド**にカメラのコンポーネントの色**黒、アルファ 0 (16 進コード: #00000000)**

    ![カメラのセットアップ](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a>第 6 章 – Newtonsoft ライブラリのインポート

逆シリアル化し、Bot Service の送受信にオブジェクトをシリアル化するのに役立つダウンロードする必要があります、 **Newtonsoft**ライブラリ。 [互換性のあるバージョンが既に適切な Unity のフォルダー構造を持つ編成](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage)します。 

プロジェクトに Newtonsoft ライブラリをインポートするには、このコースに付属する Unity パッケージを使用します。

1.  追加、 *.unitypackage*に Unity を使用して、**資産** > **パッケージのインポート** > **カスタム パッケージ**メニュー オプション。

    ![Newtonsoft ライブラリをインポートします。](images/AzureLabs-Lab312-34.png)

2.  **Unity パッケージのインポート**その pop をボックスで、(およびなど)、すべてのことを確認**プラグイン**が選択されています。

    ![Newtonsoft ライブラリをインポートします。](images/AzureLabs-Lab312-35.png)

3.  をクリックして、**インポート**をプロジェクトにアイテムを追加するボタンをクリックします。

4.  移動して、 **Newtonsoft**の下のフォルダー**プラグイン**プロジェクト ビューと、Newtonsoft のプラグインを選びます。

    ![](images/AzureLabs-Lab312-35b.png)

5.  Newtonsoft プラグインを選択することを確認**Any プラットフォーム**は**unchecked**、ことを確認します**WSAPlayer**も**unchecked**、クリックして**適用**します。 これは、ファイルが正しく構成されていることを確認するだけです。

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > これらのプラグインをマークする Unity エディターでのみ使用することを構成します。 これらのプロジェクトは Unity からエクスポートした後に使用される、WSA フォルダー内の異なるセットがあります。

6.  次を開く必要があります、 **WSA**フォルダー内で、 **Newtonsoft**フォルダー。 構成した同じファイルのコピーが表示されます。 ファイルを選択し、インスペクターのことを確認します
    -   **任意のプラットフォーム**は**オフ** 
    -   **のみ** **WSAPlayer**は**チェック**
    -   **処理されないように**は**チェック**

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a>第 7 – 章、BotTag を作成します。

1.  新規作成**タグ**と呼ばれるオブジェクト**BotTag**します。 シーンでは、メイン カメラを選択します。 タグのドロップダウン インスペクターのパネルでメニューをクリックします。 をクリックして**タグを追加**します。

    ![カメラのセットアップ](images/AzureLabs-Lab312-32.png)
 
2.  をクリックして、 **+** シンボル。 新しい名前**タグ**として**BotTag**、*保存*します。

    ![カメラのセットアップ](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> **しない**適用、 **BotTag**メイン カメラにします。 誤ってこれを実行して場合、タグを Main Camera の変更を必ず*MainCamera*します。

## <a name="chapter-8--create-the-botobjects-class"></a>第 8 章 – BotObjects クラスを作成します。

最初のスクリプトを作成する必要がありますが、 **BotObjects**クラスは、空のクラスと同じスクリプト内で、一連の他のクラス オブジェクトを格納できるように、作成し、シーン内の他のスクリプトでアクセスします。

このクラスの作成はアーキテクチャの選択肢では純粋で、これらのオブジェクトは、このコースの後半で作成するボット スクリプトでホストされる代わりに可能性があります。

このクラスを作成します。 

1.  右クリックし、*プロジェクト パネル*、し**作成 > フォルダー**します。 フォルダーの名前**スクリプト**します。 

    ![[スクリプト] フォルダーを作成します。](images/AzureLabs-Lab312-36.png)

2.  ダブルクリックして、**スクリプト**フォルダーを開きます。 そのフォルダーを右クリックし、内**作成 >C#スクリプト**します。 スクリプトの名前**BotObjects**します。 

3.  ダブルクリックして、新しい**BotObjects**スクリプト ファイルを開く**Visual Studio**します。

4.  スクリプトの内容を削除し、次のコードに置き換えます。

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。

## <a name="chapter-9--create-the-gazeinput-class"></a>第 9 章 – GazeInput クラスを作成します。

次のクラスを作成することには、 **GazeInput**クラス。 このクラスは、責任を負います。

- カーソルの作成を表す、*視線*プレーヤーの。
- ヒットして、player の視線入力オブジェクトを検出して、検出されたオブジェクトへの参照を保持しています。

このクラスを作成します。 

1.  移動して、**スクリプト**以前に作成したフォルダーです。 
2.  フォルダー内を右クリックして**作成 >C#スクリプト**します。 スクリプトを呼び出す**GazeInput**します。 
3.  ダブルクリックして、新しい**GazeInput**スクリプト ファイルを開く**Visual Studio**します。
4.  クラス名の右側で最上位の次の行を挿入します。

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  内で、次の変数を追加し、 **GazeInput**クラス上、 **Start()** メソッド。

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  コードを**Start()** メソッドを追加する必要があります。 これが、クラスの初期化時に呼び出されます。

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  インスタンス化し、視線の先のカーソルを設定するメソッドを実装します。 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  メイン カメラから Raycast をセットアップしはの追跡、現在フォーカスがあるオブジェクト メソッドを実装します。

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        internal virtual void Update()
        {
            _gazeOrigin = Camera.main.transform.position;

            _gazeDirection = Camera.main.transform.forward;

            UpdateRaycast();
        }


        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;
                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。

## <a name="chapter-10--create-the-bot-class"></a>第 10 章 – ボット クラスを作成します。

作成しようとするスクリプトを呼び出すようになりました**ボット**します。 これは、アプリケーションのコア クラス、格納されます。 

- Web App Bot 資格情報
- ユーザーの音声コマンドを収集する方法
- Web アプリのボットと会話を開始するために必要なメソッド 
- Web アプリのお客様のボットにメッセージを送信するために必要なメソッド 

ボット サービスにメッセージを送信する、 **SendMessageToBot()** コルーチンは、ユーザーによって送信されるデータとして、Bot Framework によって認識されるオブジェクトでは、アクティビティを作成します。 
 
このクラスを作成します。 

1. ダブルクリックして、**スクリプト**フォルダーを開きます。 
2. 内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成 >C#スクリプト**。 スクリプトの名前**ボット**します。 
3. Visual Studio で開くことに新しいスクリプトをダブルクリックします。
4. 上部にある、次と同じである名前空間の更新、**ボット**クラス。

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. 内で、**ボット**クラスは、次の変数を追加します。

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > 挿入することを確認、**ボットのシークレット キー**に、 **botSecret**変数。 メモは、**ボットのシークレット キー**のこのコースでは、先頭に**[第 2 章](#chapter-2---create-the-azure-bot-service)、手順 10**。

7. コードを**Awake()** と**Start()** を追加する必要があります。 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. 音声のキャプチャの開始し、終了時に、音声ライブラリによって呼び出される 2 つのハンドラーを追加します。 *DictationRecognizer*言うと、ユーザーが停止したときに、ユーザーの声をキャプチャが自動的に停止します。

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. 次のハンドラーでは、ユーザーの音声入力の結果を収集し、Web アプリのボット サービスにメッセージを送信、コルーチンを呼び出します。

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. 次のコルーチンがボットとのメッセージ交換を開始すると呼ばれます。 メッセージ交換の呼び出しが完了したら、それを呼び出すことがわかります、 **SendMessageToCoroutine()** 一連の空のメッセージとして、Bot Service に送信するアクティビティを設定するパラメーターを渡すことによって。 これは、ダイアログを開始するボット サービスを要求します。

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. 次のコルーチンは、Bot Service に送信するアクティビティを構築すると呼ばれます。 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. 次のコルーチンがアクティビティ ボット サービスに送信される応答を要求すると呼ばれます。 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. シーン内のメッセージを表示するには、このクラスは、追加する最後のメソッドが必要です。

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > 見つからない場合の Unity エディターのコンソール内でエラーが生じる、 **SceneOrganiser**クラス。 チュートリアルの後半でこのクラスを作成すると、このメッセージを無視してください。

14.  変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。

## <a name="chapter-11--create-the-interactions-class"></a>第 11 章 – 相互作用クラスを作成します。

作成しようとするクラスを今すぐ呼びます**の相互作用**します。 このクラスは、ユーザーから、HoloLens をタップして入力を検出するために使用されます。 

見ながら、ユーザーがタップした場合、*ボット*ボット、シーン内のオブジェクトが音声入力をリッスンする準備ができて、ボットのオブジェクトが色を変更**赤い**および音声入力のリッスンを開始します。 

このクラスから継承、 **GazeInput**クラス、およびそのため、参照できるように、 **Start()** メソッドと変数を使用して示される、そのクラスから**基本**します。 
 
このクラスを作成します。

1.  ダブルクリックして、**スクリプト**フォルダーを開きます。 
2.  内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成 >C#スクリプト**。 スクリプトの名前**の相互作用**します。 
3.  Visual Studio で開くことに新しいスクリプトをダブルクリックします。
4.  名前空間と同一の上部にある、次のようにするクラスの継承を更新、**の相互作用**クラス。

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  内で、**の相互作用**クラスは、次の変数を追加します。

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  追加し、 **Start()** メソッド。

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  ユーザーは、HoloLens のカメラの前に、タップ ジェスチャを実行するときにトリガーされるハンドラーを追加します。

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. 変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。

## <a name="chapter-12--create-the-sceneorganiser-class"></a>第 12 章 – SceneOrganiser クラスを作成します。

このラボで必要な最後のクラスと呼びます**SceneOrganiser**します。 このクラスは、メイン カメラをコンポーネントとスクリプトを追加し、シーン内の適切なオブジェクトを作成するプログラムでは、シーンがセットアップされます。
 
このクラスを作成します。

1.  ダブルクリックして、**スクリプト**フォルダーを開きます。 
2.  内側を右クリックし、**スクリプト**フォルダー、をクリックして**作成 >C#スクリプト**。 スクリプトの名前**SceneOrganiser**します。 
3.  Visual Studio で開くことに新しいスクリプトをダブルクリックします。
4.  内で、 **SceneOrganiser**クラスは、次の変数を追加します。

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  追加し、 **Awake()** と**Start()** メソッド。

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  シーンでボット オブジェクトを作成し、パラメーターとコンポーネントを設定する責任を負いますの次のメソッドを追加します。

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  ボットからの応答を表す、シーン内の UI オブジェクトの作成を担当する次のメソッドを追加します。

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  変更を保存することを確認する*Visual Studio*に戻る前に*Unity*します。
9.  Unity エディターで、ドラッグ、 **SceneOrganiser** Main Camera をスクリプト フォルダーのスクリプト。 シーンの開催者のコンポーネントは、次の図に示すようにようになりました、Main Camera オブジェクトに表示されます。

    ![Azure Bot Service を作成します。](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a>ビルド前に第 13 章

アプリケーションの徹底的なテストを実行するには、必要がありますをサイドロードすること、HoloLens にします。
実行する前にいることを確認します。

-   説明されているすべての設定、 [**第 4 章**](#Chapter-4-–-Set-up-the-unity-project)が正しく設定されています。 
-   スクリプト**SceneOrganiser**にアタッチされて、 **Main Camera**オブジェクト。 
-   **ボット**クラスを挿入したかどうかを確認、**ボットのシークレット キー**に、 **botSecret**変数。

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a>第 14 章 – ビルドと、HoloLens へのサイドロード

このプロジェクトの Unity のセクションの必要なすべてが今すぐ完了したら、ので、Unity から構築するための時間。

1.  移動します**ビルド設定**、**ファイル > の設定を作成しています.**.
2.  **Build Settings**ウィンドウで、をクリックして**ビルド**します。

    ![Unity からのアプリの構築](images/AzureLabs-Lab312-38.png)

3.  まだ行っていない場合、ティック**UnityC#プロジェクト**します。
4.  **[Build]** をクリックします。 Unity を起動、**ファイル エクスプ ローラー**ウィンドウを作成しにアプリをビルドするフォルダーを選択する必要があります。 ここで、そのフォルダーを作成し、名前**アプリ**します。 使用し、**アプリ**フォルダーを選択すると、クリックして**フォルダーの選択**します。 
5.  Unity にプロジェクトをビルドを開始、**アプリ**フォルダー。 
6.  1 回 Unity には、(少し時間がかかる場合があります) ビルドが完了したが開き、**ファイル エクスプ ローラー**ビルドの位置にあるウィンドウ (上の windows では、常に表示されないの新しい追加の通知をタスク バーを確認ウィンドウ)。

## <a name="chapter-15--deploy-to-hololens"></a>HoloLens に章 – 15 をデプロイします。

HoloLens の展開。

1.  必要になります、HoloLens の IP アドレス (リモート) を展開し、HoloLens をことを確認するには**開発者モード**します。 これには、次の手順を実行します。

    1. ソックスを着けずに、HoloLens 中を開く、**設定**します。
    2. 移動して**ネットワークとインターネット > Wi-fi > 詳細オプション**
    3. 注、 **IPv4**アドレス。
    4. 次に移動します**設定**、し**更新とセキュリティ > 開発者向け** 
    5. 開発者モードを設定します。

2.  新しい Unity ビルドに移動します (、**アプリ**フォルダー) とソリューション ファイルを開くと**Visual Studio**します。
3.  **ソリューション構成**選択**デバッグ**します。
4.  **ソリューション プラットフォーム**、 **x86**、**リモート マシン**します。 

    ![Visual Studio からソリューションをデプロイします。](images/AzureLabs-Lab312-39.png)
 
5.  移動して、**ビルド メニューの** をクリック**ソリューションの配置**サイドロード、HoloLens をアプリケーションにします。
6.  アプリが、起動する準備ができて、HoloLens にインストールされているアプリの一覧に表示されます。

    > [!NOTE]
    > イマーシブ ヘッドセットを展開するには、設定、**ソリューション プラットフォーム**に*ローカル マシン*、設定と、**構成**に*デバッグ*で*x86*として、**プラットフォーム**します。 ローカルにデプロイし、machine を使用して、**ビルド メニューの**選択*ソリューションの配置*します。 

## <a name="chapter-16--using-the-application-on-the-hololens"></a>第 16 章 –、HoloLens でアプリケーションを使用します。

- アプリケーションを起動するとする前にある青い球としてボットが表示されます。

- 使用して、**タップ ジェスチャ**メッセージ交換を開始する球体に gazing は中です。 
 
- メッセージ交換を開始するまで待ちます (UI メッセージが表示されます、そのような場合)。 ボットから最初のメッセージが表示されたら、もう一度タップ ボットで赤に変わり、音声にリッスンするように開始されます。 

- 通信を停止して、ボットに、メッセージの送信は、アプリケーション UI に表示される応答が迅速に届きます。 

- (たびにメッセージを送信する をタップする必要がある)、ボットにより多くのメッセージを送信するプロセスを繰り返します。

このメッセージ交換では、ボットが (名)、情報を保持する方法を示します (在庫品目) などの既知の情報も提供中です。

#### <a name="some-questions-to-ask-the-bot"></a>ボットに質問をいくつかの質問には:

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a>完成した Web App Bot (v4) アプリケーション

これで、Azure Web App Bot、Microsoft Bot Framework v4 を利用している mixed reality アプリを構築します。

![最終的な製品](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a>ボーナスの演習

### <a name="exercise-1"></a>手順 1

このラボでは、メッセージ交換の構造は非常に基本的なです。 Microsoft LUIS を使用して、お客様のボットに自然言語理解機能を提供します。

### <a name="exercise-2"></a>手順 2

この例は、メッセージ交換を終了して、新しいものを再起動するには含まれません。 ボットの機能を完了するために、メッセージ交換をクロージャを実装するためにしてください。
