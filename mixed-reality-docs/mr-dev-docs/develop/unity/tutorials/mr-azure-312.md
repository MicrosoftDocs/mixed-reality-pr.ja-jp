---
title: MR と Azure 312 - ボットの統合
description: このコースでは、Microsoft Bot Framework v4 を使用して bot を作成およびデプロイし、mixed reality アプリケーションでそれと通信する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, チュートリアル, api, コンピュータービジョン, hololens, イマーシブ, vr, microsoft bot framework v4, web アプリボット, bot framework, microsoft bot, Windows 10, Visual Studio
ms.openlocfilehash: 6b8b4624615a3c3f62800b396803572b0b67ad1a
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582468"
---
# <a name="mr-and-azure-312-bot-integration"></a>MR と Azure 312:ボットの統合

>[!NOTE]
>Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。  そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。  これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。  これらは、サポートされているデバイス上で継続して動作するように、保守されます。 今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。  この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。

このコースでは、Microsoft Bot Framework V4 を使用して bot を作成およびデプロイし、Windows Mixed Reality アプリケーションを介してそれと通信する方法について説明します。 

![](images/AzureLabs-Lab312-00.png)

**Microsoft Bot Framework V4** は、拡張可能でスケーラブルな Bot アプリケーションを構築するためのツールを開発者に提供するために設計された api のセットです。 詳細については、 [Microsoft Bot Framework のページ](https://dev.botframework.com/) または [V4 Git リポジトリ](https://github.com/Microsoft/botbuilder-dotnet/wiki)を参照してください。

このコースを完了すると、Windows Mixed Reality アプリケーションが構築されます。これにより、次のことができるようになります。

1. **Tap ジェスチャ** を使用して、ユーザーの声をリッスンしているボットを開始します。
2. ユーザーが何かを言い、bot は応答の提供を試みます。
3. ボットの近くに、Unity のシーンで bot の応答をテキストとして表示します。

アプリケーションでは、結果をデザインと統合する方法については、お客様のニーズに合わせてください。 このコースは、Azure サービスを Unity プロジェクトと統合する方法を説明することを目的としています。 このコースで得られた知識を使用して、mixed reality アプリケーションを強化することができます。

## <a name="device-support"></a>デバイス サポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 312:ボットの統合</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> このコースでは主に HoloLens に焦点を当てていますが、このコースで学習する内容を Windows Mixed Reality イマーシブ (VR) ヘッドセットにも適用できます。 イマーシブ (VR) ヘッドセットにはアクセス可能なカメラがないため、外部カメラが PC に接続されている必要があります。 コースを進めると、イマーシブ (VR) ヘッドセットをサポートするために必要な変更についての注意事項が表示されます。

## <a name="prerequisites"></a>前提条件

> [!NOTE]
> このチュートリアルは、Unity と C# の基本的な経験がある開発者向けに設計されています。 また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証された内容 (2018 年7月) を表しています。 「 [ツールのインストール](../../install-the-tools.md) 」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に記載されているものより新しいソフトウェアの内容と完全に一致するとは限りません。

このコースでは、次のハードウェアとソフトウェアをお勧めします。

- 開発用 PC で、 [Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) (VR) ヘッドセット開発と互換性があります。
- [開発者モードが有効になっている Windows 10 の作成者の更新プログラム (またはそれ以降)](../../install-the-tools.md#installation-checklist)
- [最新の Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- [Windows Mixed Reality イマーシブ (VR) ヘッドセット](../../../discover/immersive-headset-hardware-details.md)または開発者モードを有効にした[Microsoft HoloLens](/hololens/hololens1-hardware)
- Azure および Azure Bot の取得のためのインターネットアクセス。 詳細については、こちらのリンクを参照し [てください](https://dev.botframework.com/)。

### <a name="before-you-start"></a>開始する前に

1.  このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。
2.  HoloLens をセットアップしてテストします。 HoloLens のセットアップをサポートする必要がある場合は、 [hololens セットアップに関する記事にアクセスして](/hololens/hololens-setup)ください。 
3.  新しい HoloLens アプリの開発を開始するときは、調整とセンサーのチューニングを実行することをお勧めします (ユーザーごとにこれらのタスクを実行するのに役立つ場合があります)。 

調整の詳細については、 [「HoloLens の調整に関する記事へのリンク」を](/hololens/hololens-calibration#hololens-2)参照してください。

センサーチューニングの詳細については、 [HoloLens センサーチューニングに関する記事へのリンクを](/hololens/hololens-updates)参照してください。

## <a name="chapter-1--create-the-bot-application"></a>第1章: Bot アプリケーションの作成

最初の手順は、bot をローカル ASP.Net Core Web アプリケーションとして作成することです。 完了してテストした後は、Azure Portal に発行します。

1.  Visual Studio を開きます。 新しいプロジェクトを作成し、プロジェクトの種類として [ **ASP NET Core Web アプリケーション** ] を選択し (サブセクション .net core の下にあります)、 **mybot** を呼び出します。 **[OK]** をクリックします。

2.  表示されるウィンドウで、[ **空**] を選択します。 また、ターゲットが **ASP NET Core 2.0** に設定されており、認証が [ **認証なし**] に設定されていることを確認します。 **[OK]** をクリックします。  

    ![Bot アプリケーションを作成する](images/AzureLabs-Lab312-01.png)

3.  これで、ソリューションが開きます。 **ソリューションエクスプローラー** でソリューション **mybot** を右クリックし、[**ソリューションの NuGet パッケージの管理**] をクリックします。 

    ![Bot アプリケーションを作成する](images/AzureLabs-Lab312-02.png)

4.  [ **参照** ] タブで、「 **Microsoft... Integration. AspNet. Core** 」を検索します ( **プレリリースがオンに** なっていることを確認してください)。 パッケージバージョン **4.0.1-preview** を選択し、プロジェクトのボックスをオンにします。 [ **インストール**] をクリックします。 これで、 **Bot Framework v4** に必要なライブラリがインストールされました。 NuGet ページを閉じます。

    ![Bot アプリケーションを作成する](images/AzureLabs-Lab312-03.png)

5.  **ソリューションエクスプローラー** で *プロジェクト* の **mybot** を右クリックし、[クラスの **追加**] をクリックし **|** ます。

    ![Bot アプリケーションを作成する](images/AzureLabs-Lab312-04.png)

6.  クラスに **Mybot** という名前を指定し、[ **追加**] をクリックします。

    ![Bot アプリケーションを作成する](images/AzureLabs-Lab312-05.png)

7.  前の点を繰り返して、 **ConversationContext** という名前の別のクラスを作成します。 

8.  **ソリューションエクスプローラー** で **wwwroot** を右クリックし、[新しい項目の **追加**] をクリックし **|** ます。 **HTML ページ** を選択します (サブセクション Web の下にあります)。 ファイル **default.html** という名前を指定します。 **[追加]** をクリックします。

    ![Bot アプリケーションを作成する](images/AzureLabs-Lab312-06.png)

9.  **ソリューションエクスプローラー** 内のクラス/オブジェクトの一覧は次の図のようになります。

    ![Bot アプリケーションを作成する](images/AzureLabs-Lab312-07.png)

10. **ConversationContext** クラスをダブルクリックします。 このクラスは、bot が使用する変数を保持して、メッセージ交換のコンテキストを維持する役割を担います。 これらのメッセージ交換コンテキスト値は、このクラスのインスタンスで保持されます。これは、アクティビティが受信されるたびに **Mybot** クラスのインスタンスが更新されるためです。 このクラスに次のコードを追加します。

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

11. **Mybot** クラスをダブルクリックします。 このクラスは、顧客からのすべての受信アクティビティによって呼び出されるハンドラーをホストします。 このクラスでは、bot と顧客の間の会話を構築するために使用されるコードを追加します。 既に説明したように、このクラスのインスタンスは、アクティビティが受信されるたびに初期化されます。 このクラスに次のコードを追加します。

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

12. **Startup** クラスをダブルクリックします。 このクラスは bot を初期化します。 このクラスに次のコードを追加します。

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

13. **Program** クラスファイルを開き、内のコードが次のコードと同じであることを確認します。

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

14. 変更内容を保存してください。そのためには、  >  Visual Studio の上部にあるツールバーから [ファイル] [**すべてを保存**] の順に開きます。

## <a name="chapter-2---create-the-azure-bot-service"></a>第2章-Azure Bot Service の作成

Bot 用のコードを作成したので、Azure Portal で *Web アプリボット* サービスのインスタンスに発行する必要があります。 この章では、Azure でボットサービスを作成および構成し、そのサービスにコードを発行する方法について説明します。

1.  まず、Azure ポータル () にログインし https://portal.azure.com) ます。 

    1. まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。 このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。

2.  ログインしたら、左上隅にある [ **リソースの作成** ] をクリックし、[ *Web アプリボット*] を検索して、 **Enter キー** を押します。

    ![Azure Bot Service を作成する](images/AzureLabs-Lab312-08.png)
 
3.  新しいページには、 *Web アプリボット* サービスの説明が表示されます。 このページの左下にある [ **作成** ] ボタンを選択して、このサービスとの関連付けを作成します。

    ![Azure Bot Service を作成する](images/AzureLabs-Lab312-09.png)
 
4.  [ **作成**:

    1. このサービスインスタンスに必要な **名前** を挿入します。
    2. **サブスクリプション** を選択します。
    3. リソースグループを選択するか、新しい **リソースグループ** を作成します。 リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。 1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのコースなど) を共通のリソースグループに保持することをお勧めします。

        > Azure リソースグループの詳細については、こちらのリンクを参照 [してください。](/azure/azure-resource-manager/resource-group-portal)

    4. リソースグループの場所を決定します (新しいリソースグループを作成している場合)。 この場所は、アプリケーションを実行するリージョンに配置するのが理想的です。 一部の Azure 資産は、特定のリージョンでのみ利用できます。
    5. 適切な **価格レベル** を選択します。これが *Web アプリボット* サービスを初めて作成する場合は、free レベル (F0) をご利用いただけます。
    6. **アプリ名** は *Bot 名* と同じままにすることができます。 
    7. *Bot テンプレート* は **Basic (C#)** のままにしておきます。
    8. *App service プラン/場所* は、アカウントに対して自動入力されている必要があります。
    9. Bot をホストするために使用する **Azure Storage** を設定します。 まだお持ちでない場合は、ここで作成できます。
    10. また、このサービスに適用されている使用条件を理解していることを確認する必要があります。
    11. [作成] をクリックします。
 
        ![Azure Bot Service を作成する](images/AzureLabs-Lab312-10.png)

5.  [ **作成**] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。

6.  サービスインスタンスが作成されると、ポータルに通知が表示されます。

    ![Azure Bot Service を作成する](images/AzureLabs-Lab312-11.png) 
 
7.  通知をクリックして、新しいサービスインスタンスを探索します。 

    ![Azure Bot Service を作成する](images/AzureLabs-Lab312-12.png)
 
8. 通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。 新しい Azure サービスインスタンスが表示されます。 

    ![Azure Bot Service を作成する](images/AzureLabs-Lab312-13.png)
 
9.  この時点で、クライアントアプリケーションがこのボットサービスと通信できるように、 **ダイレクトライン** と呼ばれる機能を設定する必要があります。 [ **チャンネル**] をクリックし、[ **おすすめチャネルの追加** ] セクションで、[ **ダイレクトラインチャネルの構成**] をクリックします。

    ![Azure Bot Service を作成する](images/AzureLabs-Lab312-14.png)

10. このページでは、クライアントアプリが bot で認証できるようにする **秘密キー** を見つけます。 [ **表示** ] ボタンをクリックし、表示されているキーの1つをコピーします。これは、プロジェクトの後半で必要になります。 

    ![Azure Bot Service を作成する](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a>第3章: Bot を Azure Web アプリボットサービスに発行する

サービスの準備ができたので、先ほどビルドした Bot コードを、新しく作成した Web アプリボットサービスに発行する必要があります。

> [!NOTE] 
> Bot ソリューション/コードに変更を加えるたびに、Bot を Azure サービスに発行する必要があります。

1.  前に作成した Visual Studio ソリューションに戻ります。 
2.  **ソリューションエクスプローラー** で **mybot** プロジェクトを右クリックし、[**発行**] をクリックします。

    ![Bot を Azure Web アプリボットサービスに発行する](images/AzureLabs-Lab312-16.png)

3.  [ *発行先の選択* ] ページで、 **[App Service**] をクリックし、[既存] を **選択** します。最後に、[ **プロファイルの作成** ] をクリックします (表示されていない場合は、[ *発行* ] ボタンの横にあるドロップダウンの矢印をクリックする必要があります)。

    ![Bot を Azure Web アプリボットサービスに発行する](images/AzureLabs-Lab312-17.png)

4. Microsoft アカウントにまだログインしていない場合は、ここで実行する必要があります。
5. [**発行**] ページでは、 *Web アプリボット* サービスの作成に使用したものと同じ **サブスクリプション** を設定する必要があることがわかります。 次に、 **ビュー** を **リソースグループ** として設定し、ドロップダウンフォルダー構造で、前に作成した **リソースグループ** を選択します。 **[OK]** をクリックします。 

    ![Bot を Azure Web アプリボットサービスに発行する](images/AzureLabs-Lab312-18.png)

6.  [ **発行** ] ボタンをクリックし、Bot が公開されるまで待ちます (数分かかる場合があります)。

    ![Bot を Azure Web アプリボットサービスに発行する](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a>章 4-Unity プロジェクトを設定する

次に示すのは、mixed reality で開発するための一般的な設定です。そのため、他のプロジェクトに適したテンプレートです。

1.  *Unity* を開き、[**新規**] をクリックします。 

    ![Unity プロジェクトを設定する](images/AzureLabs-Lab312-20.png)

2.  ここで、Unity プロジェクト名を指定する必要があります。 **HoloLens Bot** を挿入します。 プロジェクトテンプレートが **3d** に設定されていることを確認します。 場所を適切な **場所** に設定します (ルートディレクトリの方が適していることに注意してください)。 次に、[ **プロジェクトの作成**] をクリックします。

    ![Unity プロジェクトを設定する](images/AzureLabs-Lab312-21.png)

3.  Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。 [ **> の設定の編集** ] に移動し、新しいウィンドウで [ **外部ツール**] に移動します。 **外部スクリプトエディター** を **Visual Studio 2017** に変更します。 [ **基本設定** ] ウィンドウを閉じます。

    ![Unity プロジェクトを設定する](images/AzureLabs-Lab312-22.png)

4.  次に、[ **ファイル > ビルド設定** ] に移動し、[ **ユニバーサル Windows プラットフォーム**] を選択します。次に、[ **プラットフォームの切り替え** ] ボタンをクリックして選択内容を適用します。

    ![Unity プロジェクトを設定する](images/AzureLabs-Lab312-23.png)

5.  それでも **ファイル > ビルド設定** を行い、次のことを確認します。

    1.  **ターゲットデバイス** が **HoloLens** に設定されています

        > イマーシブヘッドセットの場合は、 **ターゲットデバイス** を *任意のデバイス* に設定します。

    2.  **ビルドの種類** が **D3D** に設定されています

    3.  **SDK** は最新の **インストール** に設定されています

    4.  **Visual Studio のバージョン** が、**インストールされている最新** バージョンに設定されています

    5.  **ビルドと実行** は **ローカルコンピューター** に設定されています

    6.  シーンを保存し、ビルドに追加します。 

        1. これを行うには、[開いている **シーンの追加**] を選択します。 保存ウィンドウが表示されます。
        
            ![Unity プロジェクトを設定する](images/AzureLabs-Lab312-24.png)

        2. この新しいフォルダーを作成し、今後のシーンに加えて、[ **新しいフォルダー** ] ボタンを選択します。新しいフォルダーを作成するには、名前を「 **シーン**」にします。

             ![Unity プロジェクトを設定する](images/AzureLabs-Lab312-25.png)

        3. 新しく作成した [ **シーン** ] フォルダーを開き、[ *ファイル名*: テキスト] フィールドに「 **BotScene**」と入力し、[ **保存**] をクリックします。

            ![Unity プロジェクトを設定する](images/AzureLabs-Lab312-26.png)

    7. それ以外の設定は、[ **ビルド設定**] の [既定] のままにしておきます。

6. [ *ビルドの設定* ] ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 *インスペクター* が配置されている領域の関連パネルが開きます。 

    ![Unity プロジェクトを設定する](images/AzureLabs-Lab312-27.png)

7. このパネルでは、いくつかの設定を確認する必要があります。

    1. [ **その他の設定** ] タブで、次のようにします。

        1. **Scripting Runtime のバージョン** は **実験的 (NET 4.6 と同等)** である必要があります。これを変更するには、エディターを再起動する必要があります。
        2. **バックエンド** は **.net** である必要があります
        3. **API 互換性レベル** は **.net 4.6** である必要があります

            ![Unity プロジェクトを設定する](images/AzureLabs-Lab312-28.png)
      
    2. [ **発行の設定** ] タブの [ **機能**] で、次の項目を確認します。

        - **InternetClient**
        - **マイク**

            ![Unity プロジェクトを設定する](images/AzureLabs-Lab312-29.png)

    3. パネルの下にある [ **XR settings** (発行の **設定**] の下にあります) で、[ **サポートされている仮想現実**] をティックし、 **Windows Mixed reality SDK** が追加されていることを確認します。

        ![Unity プロジェクトを設定する](images/AzureLabs-Lab312-30.png)

8.  *ビルド設定* に戻る _Unity C#_ プロジェクトはグレーで表示されなくなりました。このの横にあるチェックボックスをオンにします。 
9.  [ビルド設定] ウィンドウを閉じます。
10. シーンとプロジェクトを保存します ([**ファイル] > [シーン/ファイルの保存] > [プロジェクトの保存**])。


## <a name="chapter-5--camera-setup"></a>第5章–カメラの設定

> [!IMPORTANT]
> このコースの *Unity セットアップ* コンポーネントをスキップし、コードに直接進む場合は、 [312 この unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage)をダウンロードして、 [**カスタムパッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてから、 [第7章](#chapter-8--create-the-botobjects-class)から続行することをお勧めします。

1.  [ *階層] パネル* で、 **メインカメラ** を選択します。 
2.  選択すると、 **メインカメラ** のすべてのコンポーネントが [ *インスペクター] パネル* に表示されます。

    1. **カメラオブジェクト** は **メインカメラ** という名前にする必要があります (スペルに注意してください)。
    2. メインカメラ **タグ** を **maincamera** に設定する必要があります (スペルに注意してください)。
    3. **変換位置** が **0、0、0** に設定されていることを確認します。
    4. **クリアフラグ** を **純色** に設定します。
    5. カメラコンポーネントの **背景** 色を **黒、アルファ 0 (16 進コード: #00000000)** に設定します。

    ![カメラの設定](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a>Chapter 6 – Newtonsoft ライブラリをインポートする

受信して Bot サービスに送信されたオブジェクトを逆シリアル化およびシリアル化できるようにするには、 **Newtonsoft** ライブラリをダウンロードする必要があります。 [互換性のあるバージョンが、適切な Unity フォルダー構造で既に構成されている](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage)ことがわかります。 

Newtonsoft ライブラリをプロジェクトにインポートするには、このコースに付属している Unity パッケージを使用します。

1.  [  **アセット**  >  **インポートパッケージ** の  >  **カスタムパッケージ**] メニューオプションを使用して、unitypackage を Unity に追加します。

    ![Newtonsoft ライブラリをインポートする](images/AzureLabs-Lab312-34.png)

2.  ポップアップ表示された [ **Unity パッケージのインポート** ] ボックスで、 **プラグイン** (およびそれを含む) のすべてが選択されていることを確認します。

    ![Newtonsoft ライブラリをインポートする](images/AzureLabs-Lab312-35.png)

3.  [ **インポート** ] ボタンをクリックして、プロジェクトに項目を追加します。

4.  プロジェクトビューの [**プラグイン**] の下にある **newtonsoft** フォルダーにアクセスし、newtonsoft プラグインを選択します。

    ![](images/AzureLabs-Lab312-35b.png)

5.  Newtonsoft プラグインを選択した状態で、 **任意のプラットフォーム** が **オフ** になっていることを確認し、[ **wsaplayer** ] も **オフ** になっていることを確認してから、[ **適用**] をクリックします。 これは、ファイルが正しく構成されていることを確認するためのものです。

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > これらのプラグインをマークすると、Unity エディターでのみ使用するように構成されます。 WSA フォルダーには、Unity からプロジェクトがエクスポートされた後に使用される、異なるセットがあります。

6.  次に、 **Newtonsoft** フォルダー内の **WSA** フォルダーを開く必要があります。 先ほど構成したものと同じファイルのコピーが表示されます。 ファイルを選択し、インスペクターで次のことを確認します。
    -   **すべてのプラットフォーム** が **オフ** になっています 
    -    **wsaplayer** のみが **チェック** されます
    -   **処理** されないかどうかを **確認** します

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a>第7章– BotTag を作成する

1.  **BotTag** という名前の新しい **タグ** オブジェクトを作成します。 シーンのメインカメラを選択します。 [インスペクター] パネルの [タグ] ドロップダウンメニューをクリックします。 [ **タグの追加**] をクリックします。

    ![カメラの設定](images/AzureLabs-Lab312-32.png)
 
2.  シンボルをクリックし **+** ます。 新しい **タグ** に **BotTag** という名前を *付けて保存* します。

    ![カメラの設定](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> メインカメラに **BotTag** を適用しない **で** ください。 この操作を誤って行った場合は、メインカメラのタグを必ず *Maincamera* に戻してください。

## <a name="chapter-8--create-the-botobjects-class"></a>Chapter 8 – BotObjects クラスを作成する

作成する必要のある最初のスクリプトは、 **BotObjects** クラスです。このクラスは、他の一連のクラスオブジェクトを同じスクリプト内に格納し、シーン内の他のスクリプトからアクセスできるようにするために作成された空のクラスです。

このクラスの作成は、純粋にアーキテクチャを選択したものです。これらのオブジェクトは、このコースの後半で作成する Bot スクリプトでホストすることができます。

このクラスを作成するには: 

1.  [ *プロジェクト] パネル* 内を右クリックし、[ **> フォルダーの作成**] をクリックします。 フォルダーに **スクリプト** の名前を指定します。 

    ![Scripts フォルダーを作成します。](images/AzureLabs-Lab312-36.png)

2.  [ **Scripts** ] フォルダーをダブルクリックして開きます。 次に、そのフォルダー内でを右クリックし、[ **Create > C# Script**] を選択します。 スクリプトに **BotObjects** という名前を指定します。 

3.  新しい **BotObjects** スクリプトをダブルクリックして、 **Visual Studio** で開きます。

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

6.  *Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。

## <a name="chapter-9--create-the-gazeinput-class"></a>第9章: GazeInput クラスを作成する

次に作成するクラスは、 **GazeInput** クラスです。 このクラスの役割は次のとおりです。

- プレーヤーの *宝石* を表すカーソルを作成する。
- プレーヤーの見つめによってヒットしたオブジェクトを検出し、検出されたオブジェクトへの参照を保持します。

このクラスを作成するには: 

1.  前に作成した **Scripts** フォルダーにアクセスします。 
2.  フォルダー内を右クリックし、[ **Create > C# Script**] をクリックします。 スクリプト **GazeInput** を呼び出します。 
3.  新しい **GazeInput** スクリプトをダブルクリックして、 **Visual Studio** で開きます。
4.  クラス名の上に次の行を挿入します。

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  次に、 **Start ()** メソッドの上に、 **GazeInput** クラス内に次の変数を追加します。

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

6.  **Start ()** メソッドのコードを追加する必要があります。 このは、クラスの初期化時に呼び出されます。

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

7.  見つめカーソルをインスタンス化して設定するメソッドを実装します。 

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

8.  メインカメラから Raycast を設定するメソッドを実装します。これにより、現在フォーカスがあるオブジェクトが追跡されます。

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
 
9.  *Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。

## <a name="chapter-10--create-the-bot-class"></a>Chapter 10 – Bot クラスを作成する

ここで作成するスクリプトは **Bot** と呼ばれます。 これはアプリケーションのコアクラスであり、次のものが格納されます。 

- Web アプリボットの資格情報
- ユーザーの音声コマンドを収集するメソッド
- Web アプリボットとのメッセージ交換を開始するために必要なメソッド 
- Web アプリボットにメッセージを送信するために必要なメソッド 

Bot サービスにメッセージを送信するために、 **Sendmessagetobot ()** コルーチンはアクティビティを作成します。これは、bot Framework によってユーザーによって送信されたデータとして認識されるオブジェクトです。 
 
このクラスを作成するには: 

1. [ **Scripts** ] フォルダーをダブルクリックして開きます。 
2. **Scripts** フォルダー内を右クリックし、[ **Create > C# Script**] をクリックします。 スクリプト **ボット** にという名前を指定します。 
3. 新しいスクリプトをダブルクリックして、Visual Studio で開きます。
4. **Bot** クラスの上部で、次の名前空間を更新します。

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. **Bot** クラス内で、次の変数を追加します。

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
    > **Bot シークレットキー** を **botSecret** 変数に挿入していることを確認します。 **Bot の秘密鍵** は、このコースの最初に、 **[第2章](#chapter-2---create-the-azure-bot-service)の手順 10** で説明しました。

7. 起動可能な **()** と **Start ()** のコードを追加する必要があります。 

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

8. 音声キャプチャの開始時と終了時に speech ライブラリによって呼び出される2つのハンドラーを追加します。 *DictationRecognizer* は、ユーザーが読み上げを停止したときに、ユーザーの音声のキャプチャを自動的に停止します。

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

1. 次のハンドラーは、ユーザーの音声入力の結果を収集し、Web アプリボットサービスへのメッセージの送信を担当するコルーチンを呼び出します。

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

10. Bot とのメッセージ交換を開始するために、次のコルーチンが呼び出されます。 メッセージ交換の呼び出しが完了すると、Bot サービスに空のメッセージとしてアクティビティが送信されるように設定する一連のパラメーターを渡すことによって、 **SendMessageToCoroutine ()** が呼び出されます。 これは、Bot サービスにダイアログを開始するように求めるメッセージを表示するために行われます。

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

11. Bot サービスに送信されるアクティビティをビルドするために、次のコルーチンが呼び出されます。 

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

12. 次のコルーチンは、Bot サービスにアクティビティを送信した後に応答を要求するために呼び出されます。 

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

13. このクラスに最後に追加されるメソッドは、シーンにメッセージを表示するために必要です。

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
    > Unity エディターコンソールで、 **SceneOrganiser** クラスがないというエラーが表示されることがあります。 このメッセージは無視してください。このチュートリアルの後半で、このクラスを作成します。

14.  *Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。

## <a name="chapter-11--create-the-interactions-class"></a>第11章–相互作用クラスを作成する

ここで作成するクラスは、" **相互作用**" と呼ばれます。 このクラスは、ユーザーからの HoloLens タップ入力を検出するために使用されます。 

シーン内の *bot* オブジェクトを見ているときにユーザーがタップしたときに、bot が音声入力をリッスンする準備ができている場合、bot オブジェクトは色を **赤** に変更し、音声入力のリッスンを開始します。 

このクラスは、 **GazeInput** クラスから継承されます。したがって、このクラスの **Start ()** メソッドと変数を参照できます。これは、 **base** を使用することによって示されます。 
 
このクラスを作成するには:

1.  [ **Scripts** ] フォルダーをダブルクリックして開きます。 
2.  **Scripts** フォルダー内を右クリックし、[ **Create > C# Script**] をクリックします。 スクリプトの **操作** に名前を指定します。 
3.  新しいスクリプトをダブルクリックして、Visual Studio で開きます。
4.  **相互作用** クラスの上部で、次のように名前空間とクラスの継承を更新します。

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  **相互作用** クラス内で、次の変数を追加します。

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  次に、 **Start ()** メソッドを追加します。

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

7.  ユーザーが HoloLens カメラの前で tap ジェスチャを実行したときにトリガーされるハンドラーを追加します。

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

8. *Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。

## <a name="chapter-12--create-the-sceneorganiser-class"></a>第12章: SceneOrganiser クラスを作成する

このラボに必要な最後のクラスは、 **SceneOrganiser** と呼ばれます。 このクラスは、メインカメラにコンポーネントとスクリプトを追加し、シーンに適切なオブジェクトを作成することによって、シーンをプログラムによって設定します。
 
このクラスを作成するには:

1.  [ **Scripts** ] フォルダーをダブルクリックして開きます。 
2.  **Scripts** フォルダー内を右クリックし、[ **Create > C# Script**] をクリックします。 スクリプトに **SceneOrganiser** という名前を指定します。 
3.  新しいスクリプトをダブルクリックして、Visual Studio で開きます。
4.  **SceneOrganiser** クラス内で、次の変数を追加します。

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

6.  次に、起動 ( **)** および **開始 ()** の各メソッドを追加します。

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

7.  シーンに Bot オブジェクトを作成し、パラメーターとコンポーネントを設定する次のメソッドを追加します。

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

7.  次のメソッドを追加します。これは、Bot からの応答を表す、シーン内の UI オブジェクトの作成を担当します。

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

8.  *Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。
9.  Unity エディターで、 **SceneOrganiser** スクリプトを Scripts フォルダーからメインカメラにドラッグします。 次の図に示すように、シーン Organiser コンポーネントがメインカメラオブジェクトに表示されます。

    ![Azure Bot Service を作成する](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a>第13章: ビルド前

アプリケーションの徹底的なテストを実行するには、アプリケーションを HoloLens にサイドロードする必要があります。
これを行う前に、次のことを確認してください。

-   [**章 4**](#chapter-4--set-up-the-unity-project)で説明したすべての設定が正しく設定されています。 
-   スクリプト **SceneOrganiser** は、 **メインカメラ** オブジェクトにアタッチされます。 
-   **Bot** クラスで、 **bot シークレットキー** が **botSecret** 変数に挿入されていることを確認します。

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a>第14章– HoloLens へのビルドとサイドロード

このプロジェクトの Unity セクションに必要なものはすべて完了したので、Unity から構築します。

1.  **ビルド設定**、**ファイル > ビルド設定** に移動します。
2.  [ **ビルドの設定** ] ウィンドウで、[ **ビルド**] をクリックします。

    ![Unity からアプリをビルドする](images/AzureLabs-Lab312-38.png)

3.  **Unity C# プロジェクト** をまだティックしていない場合は、ティックします。
4.  [**ビルド**] をクリックします。 Unity は **エクスプローラー** ウィンドウを起動します。このウィンドウでは、アプリを作成するフォルダーを作成して選択する必要があります。 ここでそのフォルダーを作成し、「 **App**」という名前を指定します。 次に、 **アプリ** フォルダーを選択し、[ **フォルダーの選択**] をクリックします。 
5.  Unity は、 **アプリ** フォルダーへのプロジェクトのビルドを開始します。 
6.  Unity のビルドが完了すると (時間がかかる場合があります)、ビルドの場所で **ファイルエクスプローラー** ウィンドウを開きます (ウィンドウの上に常に表示されるとは限りませんが、新しいウィンドウが追加されたことが通知されます)。

## <a name="chapter-15--deploy-to-hololens"></a>第15章– HoloLens への展開

HoloLens に展開するには:

1.  Hololens が **開発者モード** になっていることを確認するには、HOLOLENS の IP アドレス (リモートデプロイ用) が必要です。 これを行うには、次の手順を実行します。

    1. HoloLens を装着した後、 **設定** を開きます。
    2. **[Network & Internet > Wi-Fi > 詳細オプション]** にアクセスします。
    3. **IPv4** アドレスをメモしておきます。
    4. 次に、[**設定**] に戻り、**開発者向けの & セキュリティ > を更新** します。 
    5. 開発者モードをに設定します。

2.  新しい Unity ビルド ( **アプリ** フォルダー) に移動し、 **Visual Studio** でソリューションファイルを開きます。
3.  **ソリューション構成** で、[**デバッグ**] を選択します。
4.  **ソリューションプラットフォーム** で、[ **X86**、**リモートコンピューター**] を選択します。 

    ![Visual Studio からソリューションをデプロイします。](images/AzureLabs-Lab312-39.png)
 
5.  [ **ビルド] メニュー** の [ソリューションの **配置**] をクリックして、アプリケーションを HoloLens にサイドロードします。
6.  アプリが HoloLens にインストールされているアプリの一覧に表示され、起動できる状態になります。

    > [!NOTE]
    > イマーシブヘッドセットにデプロイするには **、ソリューションプラットフォーム** を *ローカルコンピューター* に設定し、**プラットフォーム** として *x86* を使用して、**構成** を [*デバッグ*] に設定します。 次に、[ **ビルド] メニュー** の [ *ソリューションの配置*] をクリックして、ローカルコンピューターに配置します。 

## <a name="chapter-16--using-the-application-on-the-hololens"></a>Chapter 16 – HoloLens でのアプリケーションの使用

- アプリケーションを起動すると、その前に Bot が青い球として表示されます。

- メッセージ交換を開始するには、 **タップジェスチャ** を使用します。 
 
- メッセージ交換が開始されるのを待ちます (UI は、発生したときにメッセージを表示します)。 Bot からの入門メッセージを受信したら、Bot でもう一度タップして、赤に変わり、音声の聞き取りを開始します。 

- 会話を終了すると、アプリケーションから Bot にメッセージが送信され、UI に表示される応答がすぐに表示されます。 

- プロセスを繰り返して、Bot にさらにメッセージを送信します (メッセージを送信するたびにタップする必要があります)。

このメッセージ交換では、Bot が情報 (自分の名前) を保持しながら、既知の情報 (在庫品目など) も提供する方法を説明します。

#### <a name="some-questions-to-ask-the-bot"></a>Bot に質問することができます。

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a>完成した Web アプリボット (v4) アプリケーション

これで、Azure Web アプリボットである Microsoft Bot Framework v4 を活用する mixed reality アプリが作成されました。

![最終製品](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a>ボーナス演習

### <a name="exercise-1"></a>演習1

このラボのメッセージ交換の構造は非常に基本的なものです。 Microsoft LUIS を使用して、bot の自然言語に関する機能を提供します。

### <a name="exercise-2"></a>演習2

この例では、メッセージ交換を終了し、新しいメッセージ交換を再開することはありません。 Bot 機能を完成させるには、メッセージ交換にクロージャを実装してみてください。