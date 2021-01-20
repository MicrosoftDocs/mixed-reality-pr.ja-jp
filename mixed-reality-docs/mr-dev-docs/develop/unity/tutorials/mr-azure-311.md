---
title: MR と Azure 311 - Microsoft Graph
description: このコースでは、Microsoft Graph を活用する方法と、混合の現実アプリケーション内で生産性を向上させるデータに接続する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, チュートリアル, api, microsoft graph, hololens, イマーシブ, vr, Windows 10, Visual Studio
ms.openlocfilehash: 699e520fb9db8d8d3b5bab8b98d92fa39f0acb2d
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583446"
---
# <a name="mr-and-azure-311---microsoft-graph"></a>MR と Azure 311 - Microsoft Graph

>[!NOTE]
>Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。  そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。  これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。  これらは、サポートされているデバイス上で継続して動作するように、保守されます。 今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。  この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。

このコースでは、 *Microsoft Graph* を使用して、mixed reality アプリケーション内でセキュリティ保護された認証を使用して Microsoft アカウントにログインする方法について説明します。 次に、スケジュールされた会議をアプリケーションインターフェイスで取得して表示します。

![](images/AzureLabs-Lab311-00.png)

*Microsoft Graph* は、Microsoft の多くのサービスにアクセスできるように設計された api のセットです。 Microsoft では、リレーションシップによって接続されるリソースのマトリックスとして Microsoft Graph について説明します。これは、アプリケーションが接続されたあらゆる種類のユーザーデータにアクセスできるようにすることを意味します 詳細については、 [Microsoft Graph のページ](https://developer.microsoft.com/graph)を参照してください。

開発にはアプリの作成が含まれます。このアプリでは、ユーザーが宝石を見つめ、球をタップするように指示され、ユーザーは Microsoft アカウントに安全にログインするように求められます。 自分のアカウントにログインすると、その日にスケジュールされている会議の一覧を表示できるようになります。

このコースを完了すると、mixed reality HoloLens アプリケーションが完成します。これにより、次のことができるようになります。

1.  Tap ジェスチャを使用して、オブジェクトをタップします。これにより、ユーザーは Microsoft アカウントにログインするように求められます (アプリの外に移動してログインし、再びアプリに戻す)。
2.  その日にスケジュールされている会議の一覧を表示します。 

アプリケーションでは、結果をデザインと統合する方法については、お客様のニーズに合わせてください。 このコースは、Azure サービスを Unity プロジェクトと統合する方法を説明することを目的としています。 このコースで得られた知識を使用して、mixed reality アプリケーションを強化することができます。

## <a name="device-support"></a>デバイス サポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 311:Microsoft Graph</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>前提条件

> [!NOTE]
> このチュートリアルは、Unity と C# の基本的な経験がある開発者向けに設計されています。 また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証された内容 (2018 年7月) を表しています。 「 [ツールのインストール](../../install-the-tools.md) 」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に記載されているものより新しいソフトウェアの内容と完全に一致するとは限りません。

このコースでは、次のハードウェアとソフトウェアをお勧めします。

- 開発用 PC
- [開発者モードが有効になっている Windows 10 の作成者の更新プログラム (またはそれ以降)](../../install-the-tools.md#installation-checklist)
- [最新の Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- 開発者モードが有効になっている[Microsoft HoloLens](/hololens/hololens1-hardware)
- Azure セットアップとデータ取得のためのインターネットアクセス Microsoft Graph
- 有効な **Microsoft アカウント** (個人または職場/学校)
- 同じ Microsoft アカウントを使用して、現在の日にスケジュールされているいくつかの会議

### <a name="before-you-start"></a>開始する前に

1.  このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。
2.  HoloLens をセットアップしてテストします。 HoloLens のセットアップをサポートする必要がある場合は、 [hololens セットアップに関する記事にアクセスして](/hololens/hololens-setup)ください。 
3.  新しい HoloLens アプリの開発を開始するときは、調整とセンサーのチューニングを実行することをお勧めします (ユーザーごとにこれらのタスクを実行するのに役立つ場合があります)。 

調整の詳細については、 [「HoloLens の調整に関する記事へのリンク」を](/hololens/hololens-calibration#hololens-2)参照してください。

センサーチューニングの詳細については、 [HoloLens センサーチューニングに関する記事へのリンクを](/hololens/hololens-updates)参照してください。

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a>第1章-アプリケーション登録ポータルでのアプリの作成

まず、アプリケーション **登録ポータル** でアプリケーションを作成し、登録する必要があります。

この章では、アカウントコンテンツにアクセスするために *Microsoft Graph* を呼び出すことができるサービスキーについても説明します。

1.  [Microsoft アプリケーション登録ポータル](https://apps.dev.microsoft.com)に移動し、microsoft アカウントでログインします。 ログインすると、 **アプリケーション登録ポータル** にリダイレクトされます。

2.  **[マイアプリケーション**] セクションで、[アプリの **追加**] ボタンをクリックします。

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > 以前に *Microsoft Graph* を操作したかどうかによって、**アプリケーション登録ポータル** が異なる場合があります。 以下のスクリーンショットには、これらの異なるバージョンが表示されています。

3.  アプリケーションの名前を追加し、[ **作成**] をクリックします。

    ![](images/AzureLabs-Lab311-03.png)

4.  アプリケーションが作成されると、アプリケーションのメインページにリダイレクトされます。 **アプリケーション Id** をコピーし、この値が安全な場所にあることを確認してください。コードですぐに使用します。

    ![](images/AzureLabs-Lab311-04.png)

5.  [ **プラットフォーム** ] セクションで、[ **ネイティブアプリケーション** ] が表示されていることを確認します。 それ *以外* の場合は、[ **プラットフォームの追加** ] をクリックし、[ **ネイティブアプリケーション**] を選択します。

    ![](images/AzureLabs-Lab311-05.png)

6.  同じページを下にスクロールし、[Microsoft Graph の **アクセス許可** ] というセクションで、アプリケーションに対する追加のアクセス許可を追加する必要があります。 [委任された **アクセス許可**] の横にある [**追加**] をクリックします。

    ![](images/AzureLabs-Lab311-06.png)

7.  アプリケーションでユーザーの予定表にアクセスできるようにするには、[カレンダー] というボックスをオンにし **ます。 [読み取り** ] をクリックし、[ **OK**] をクリックします。

    ![](images/AzureLabs-Lab311-07.png)

8.  一番下までスクロールし、[ **保存** ] ボタンをクリックします。

    ![](images/AzureLabs-Lab311-08.png)

9.  保存が確認され、 **アプリケーション登録ポータル** からログアウトできます。

## <a name="chapter-2---set-up-the-unity-project"></a>Chapter 2-Unity プロジェクトの設定

次に示すのは、mixed reality で開発するための一般的な設定です。そのため、他のプロジェクトに適したテンプレートです。

1.  *Unity* を開き、[**新規**] をクリックします。

    ![](images/AzureLabs-Lab311-09.png)

2.  Unity プロジェクト名を指定する必要があります。 **Msgraphmr** を挿入します。 プロジェクトテンプレートが **3d** に設定されていることを確認します。 場所を適切な **場所** に設定します (ルートディレクトリの方が適していることに注意してください)。 次に、[ **プロジェクトの作成**] をクリックします。

    ![](images/AzureLabs-Lab311-10.png)

3.  Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。 [設定の **編集**] に移動し、  >  新しいウィンドウで [**外部ツール**] に移動します。 **外部スクリプトエディター** を **Visual Studio 2017** に変更します。 [ **基本設定** ] ウィンドウを閉じます。

    ![](images/AzureLabs-Lab311-11.png)

4.  ファイルの  >  **ビルド設定** に移動して [**ユニバーサル Windows プラットフォーム**] を選択し、[**プラットフォームの切り替え**] ボタンをクリックして選択内容を適用します。

    ![](images/AzureLabs-Lab311-12.png)

5.  **ファイル** の  >  **ビルド設定** でも、次のことを確認してください。

    1. **ターゲットデバイス** が **HoloLens** に設定されています
    2. **ビルドの種類** が **D3D** に設定されています
    3. **SDK** は最新の **インストール** に設定されています
    4. **Visual Studio のバージョン** が、**インストールされている最新** バージョンに設定されています
    5. **ビルドと実行** は **ローカルコンピューター** に設定されています
    6. シーンを保存し、ビルドに追加します。

        1. これを行うには、[開いている **シーンの追加**] を選択します。 保存ウィンドウが表示されます。

            ![](images/AzureLabs-Lab311-13.png)

        2. この、および将来のシーン用に新しいフォルダーを作成します。 [ **新しいフォルダー** ] ボタンを選択し、新しいフォルダーを作成するには、「 **シーン**」という名前を指定します。

            ![](images/AzureLabs-Lab311-14.png)

        3. 新しく作成した [ **シーン** ] フォルダーを開き、[ *ファイル名*: テキスト] フィールドに「 **MR_ComputerVisionScene**」と入力し、[ **保存**] をクリックします。

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > Unity プロジェクトに関連付けられている必要があるため、Unity のシーンを *Assets* フォルダー内に保存する必要があります。 Unity プロジェクトを構成する一般的な方法は、シーンフォルダー (およびその他の同様のフォルダー) を作成することです。

    7.  それ以外の設定は、[ *ビルド設定*] の [既定] のままにしておきます。

6.  [ *ビルドの設定* ] ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 *インスペクター* が配置されている領域の関連パネルが開きます。 

    ![](images/AzureLabs-Lab311-16.png)

7. このパネルでは、いくつかの設定を確認する必要があります。

    1. [ **その他の設定** ] タブで、次のようにします。

        1.  **Scripting** **Runtime のバージョン** は **実験的** (.net 4.6 と同等) である必要があります。これにより、エディターを再起動する必要が生じます。

        2. **バックエンド** は **.net** である必要があります

        3. **API 互換性レベル** は **.net 4.6** である必要があります

            ![](images/AzureLabs-Lab311-17.png)

    2.  [ **発行の設定** ] タブの [ **機能**] で、次の項目を確認します。

        - **InternetClient**

            ![](images/AzureLabs-Lab311-18.png)

    3.  パネルの下にある [ **XR settings** ( **発行設定**] の下にあります) で、[ **Virtual reality がサポートさ** れる] をオンにして、 **Windows Mixed reality SDK** が追加されていることを確認します。

        ![](images/AzureLabs-Lab311-19.png)

8.  *ビルド設定* に戻ると、 *Unity C# プロジェクト* はグレーで表示されなくなりました。この横にあるチェックボックスをオンにします。

9.  *[ビルド設定]* ウィンドウを閉じます。

10.  シーンとプロジェクトを保存します (**ファイル**  >  **保存シーン/ファイル**  >  **保存プロジェクト**)。

## <a name="chapter-3---import-libraries-in-unity"></a>章 3-Unity でライブラリをインポートする

> [!IMPORTANT]
> このコースの *Unity セットアップ* コンポーネントをスキップしてコードに直接進む場合は、unitypackage をダウンロードして、[**カスタムパッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてから、[第5章](#chapter-5---create-meetingsui-class)から続行することをお勧めします [。](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage)

Unity 内で *Microsoft Graph* を使用するには、  **Microsoft Identity. Client** DLL を使用する必要があります。 Microsoft Graph SDK を使用することもできますが、Unity プロジェクトをビルドした後に NuGet パッケージを追加する必要があります (つまり、プロジェクトのビルド後に編集することになります)。 必要な Dll を Unity に直接インポートする方が簡単であると考えられます。

> [!NOTE]
> 現在、Unity には、インポート後にプラグインを再構成する必要がある既知の問題があります。 バグが解決された後、これらの手順 (このセクションでは 4-7) は不要になりました。

*Microsoft Graph* を独自のプロジェクトにインポートするには、 [MSGraph_LabPlugins.zip ファイルをダウンロード](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage)します。 このパッケージは、テスト済みのライブラリのバージョンで作成されています。

カスタム Dll を Unity プロジェクトに追加する方法の詳細については、次の [リンク](https://docs.unity3d.com/Manual/UsingDLL.html)先を参照してください。

パッケージをインポートするには:

1.  [**アセット**  >  **インポートパッケージ**  >  **カスタムパッケージ**] メニューオプションを使用して unity に unity パッケージを追加します。 ダウンロードしたパッケージを選択します。

2.  ポップアップ表示された [ **Unity パッケージのインポート** ] ボックスで、 **プラグイン** (およびそれを含む) のすべてが選択されていることを確認します。

    ![](images/AzureLabs-Lab311-20.png)

3.  [ **インポート** ] ボタンをクリックして、プロジェクトに項目を追加します。

4.  [*プロジェクト] パネル* の [**プラグイン**] の下にある **msgraph** フォルダーにアクセスし、[ **Microsoft. Identity. Client**] という名前のプラグインを選択します。

    ![](images/AzureLabs-Lab311-21.png)

5.  *プラグイン* を選択した状態で、**任意のプラットフォーム** がオフになっていることを確認し、[ **wsaplayer** ] もオフになっていることを確認してから、[**適用**] をクリックします。 これは、ファイルが正しく構成されていることを確認するためのものです。

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > これらのプラグインをマークすると、Unity エディターでのみ使用するように構成されます。 WSA フォルダーには、プロジェクトが Unity からユニバーサル Windows アプリケーションとしてエクスポートされた後に使用される、異なる Dll のセットがあります。

6.  次に、 **Msgraph** フォルダー内の **WSA** フォルダーを開く必要があります。 先ほど構成したものと同じファイルのコピーが表示されます。 ファイルを選択し、次にインスペクターで次のようにします。

    -   すべての **プラットフォーム** が **オフ** になっていて、 **wsaplayer** **のみ** が **チェック** されていることを確認します。

    -   **SDK** が **UWP** に設定され、**スクリプトバックエンド** が **ドット Net** に設定されていることを確認します。

    -   " **処理しない** " が **オン** になっていることを確認します。

        ![](images/AzureLabs-Lab311-23.png)

7.  **[Apply]** をクリックします。

## <a name="chapter-4---camera-setup"></a>第4章-カメラの設定

この章では、シーンのメインカメラを設定します。

1.  [ *階層] パネル* で、 **メインカメラ** を選択します。

2.  選択すると、 **メインカメラ** のすべてのコンポーネントが [ *インスペクター* ] パネルに表示されます。

    1.  **カメラオブジェクト** は **メインカメラ** という名前にする必要があります (スペルに注意してください)。

    2.  メインカメラの **タグ** は、 **maincamera** に設定する必要があります (スペルに注意してください)。

    3.  **変換位置** が **0、0、0** に設定されていることを確認します。

    4.  **クリアフラグ** を **純色** に設定する

    5.  カメラコンポーネントの **背景色** を **黒、アルファ 0** **(16 進コード: #00000000)** に設定します。

        ![](images/AzureLabs-Lab311-24.png)

3.  *階層パネル* の最終的なオブジェクト構造は、次の図に示すようになります。

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a>Chapter 5-MeetingsUI クラスを作成する

作成する必要のある最初のスクリプトは **MeetingsUI** です。これは、アプリケーションの UI (ウェルカムメッセージ、指示、および会議の詳細) をホストおよび設定する役割を担います。

このクラスを作成するには:

1.  [*プロジェクト] パネル* の [**アセット**] フォルダーを右クリックし、[フォルダーの **作成**] を選択し  >  ます。 フォルダーに **スクリプト** の名前を指定します。

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  **Scripts** フォルダーを開き、そのフォルダー内で右クリックして、 [  >  **C# スクリプト** の作成] をクリックします。 スクリプトに MeetingsUI という名前を指定 **します。**

    ![](images/AzureLabs-Lab311-28.png)

3.  新しい **MeetingsUI** スクリプトをダブルクリックして、 *Visual Studio* で開きます。

4.  次の名前空間を挿入します。

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  クラス内で、次の変数を挿入します。

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  次に、 **Start ()** メソッドを置き換え、起動前 **()** メソッドを追加します。 これらは、クラスの初期化時に呼び出されます。

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  *ミーティング UI* を作成し、要求されたときに現在の会議に設定するためのメソッドを追加します。

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. **Update ()** メソッドを **削除** し、Unity に戻る前に変更を Visual Studio に **保存** します。 

## <a name="chapter-6---create-the-graph-class"></a>Chapter 6-Graph クラスの作成

次に作成するスクリプトは、 **グラフ** スクリプトです。 このスクリプトは、ユーザーを認証し、現在の日のスケジュールされた会議をユーザーの予定表から取得するための呼び出しを行います。

このクラスを作成するには:

1.  [ **Scripts** ] フォルダーをダブルクリックして開きます。

2.  **Scripts** フォルダー内を右クリックし、[   >  **C# スクリプト** の作成] をクリックします。 スクリプト **グラフ** にという名前を指定します。

3.  スクリプトをダブルクリックして、Visual Studio で開きます。

4.  次の名前空間を挿入します。

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > このスクリプトのコードの一部は、 [プリコンパイルディレクティブ](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html)にラップされていることに注意してください。これは、Visual Studio ソリューションをビルドするときにライブラリの問題を回避するためです。

5.  **Start ()** および **Update ()** メソッドは使用されないため、削除します。

6.  **Graph** クラスの外部で、次のオブジェクトを挿入します。これは、毎日スケジュールされた会議を表す JSON オブジェクトを逆シリアル化するために必要です。

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  **Graph** クラス内に、次の変数を追加します。

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > **AppId** の値を、 **[第1章](#chapter-1---create-your-app-in-the-application-registration-portal)の手順 4**. でメモした **アプリ Id** に変更します。 この値は、アプリケーション登録 **ポータル** のアプリケーション登録ページに表示される値と同じである必要があります。

8.  **Graph** クラス内で、 **SignInAsync ()** メソッドと **AquireTokenAsync ()** メソッドを追加します。これにより、ユーザーはログイン資格情報を挿入するように求められます。

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successful, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  次の2つのメソッドを追加します。

    1.  **BuildTodayCalendarEndpoint ()**。スケジュールされた会議を取得する日付と期間を指定する URI を作成します。

    2.  **List面会 Sasync ()** は、スケジュールされた会議を *Microsoft Graph* から要求します。

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. これで、 **グラフ** スクリプトが完成しました。 Unity に戻る前に **、変更** を Visual Studio に保存します。

## <a name="chapter-7---create-the-gazeinput-script"></a>第7章-GazeInput スクリプトの作成

次に、 **GazeInput** を作成します。 このクラスは、**メインカメラ** からの **Raycast** を使用して、前に射影したユーザーの宝石を処理し、追跡します。

スクリプトを作成するには:

1.  [ **Scripts** ] フォルダーをダブルクリックして開きます。

2.  **Scripts** フォルダー内を右クリックし、[   >  **C# スクリプト** の作成] をクリックします。 スクリプトに **GazeInput** という名前を指定します。

3.  スクリプトをダブルクリックして、Visual Studio で開きます。

4.  シリアル化できるように、次のいずれかに一致するように名前空間コードを変更し、 **GazeInput** クラスの上に "**\[ Serializable \]**" タグを追加します。

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  **GazeInput** クラス内で、次の変数を追加します。

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

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

6.  **CreateCursor ()** メソッドを追加し、シーンに HoloLens カーソルを作成し、 **Start ()** メソッドからメソッドを呼び出します。

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  次のメソッドを使用すると、Raycast を有効にし、フォーカスのあるオブジェクトを追跡できます。

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
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
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
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  Unity に戻る前に **、変更** を Visual Studio に保存します。

## <a name="chapter-8---create-the-interactions-class"></a>章 8-相互作用クラスを作成する

ここで、次の操作を行う **相互作用** スクリプトを作成する必要があります。

-   **タップ** 操作と **カメラを見つめ** て処理します。これにより、ユーザーはシーン内のログイン "ボタン" と対話できます。

-   ユーザーが操作を行うためのシーンに "button" オブジェクトのログインを作成します。

スクリプトを作成するには:

1.  [ **Scripts** ] フォルダーをダブルクリックして開きます。

2.  **Scripts** フォルダー内を右クリックし、[   >  **C# スクリプト** の作成] をクリックします。 スクリプトの **操作** に名前を指定します。

3.  スクリプトをダブルクリックして、Visual Studio で開きます。

4.  次の名前空間を挿入します。

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  **相互作用** クラスの継承を、GazeInput *に変更* します。

    ~~パブリッククラスの相互作用: モノの動作~~

    ```csharp
    public class Interactions : GazeInput
    ```

6.  **相互作用** クラス内で、次の変数を挿入します。

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  **Start** メソッドを置き換えます。これはオーバーライドメソッドであることに注意してください。このメソッドは、"base" を使用して、"このメソッドを呼び出します。 **Start ()** は、クラスが初期化され、入力認識に登録され、シーンに [サインイン *] ボタン* が作成されるときに呼び出されます。

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  次のように、シーンの [サインイン *] ボタン* をインスタンス化し、そのプロパティを設定する、/**ボタン ()** メソッドを追加します。

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  *Tap* ユーザーイベントに対応する **GestureRecognizer_Tapped ()** メソッドを追加します。

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. **Update ()** メソッドを **削除** してから、Unity に戻る前に Visual Studio に **変更を保存** します。

## <a name="chapter-9---set-up-the-script-references"></a>章 9-スクリプト参照の設定

この章では、 **対話** スクリプトを **メインカメラ** に配置する必要があります。 そのスクリプトは、必要な場所にある他のスクリプトの配置を処理します。

-  次の図に示すように、[*プロジェクト] パネル* の [**スクリプト**] フォルダーで、スクリプトの **対話** を **メインカメラ** オブジェクトにドラッグします。

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a>Chapter 10-タグの設定

宝石を処理するコードは、タグ **SignInButton** を使用して、ユーザーが *Microsoft Graph* にサインインするために対話するオブジェクトを識別します。

タグを作成するには、次のようにします。

1.  Unity エディターで、[*階層] パネル* の **メインカメラ** をクリックします。

2.  [ *インスペクター] パネル* の [ **maincamera** ] *タグ* をクリックして、ドロップダウンリストを開きます。 [**タグの追加**] をクリックします。

    ![](images/AzureLabs-Lab311-30.png)

3.  ボタンをクリックし **+** ます。

    ![](images/AzureLabs-Lab311-31.png)

4.  タグ名を **SignInButton** として書き込み、[保存] をクリックします。

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a>第11章-UWP に Unity プロジェクトをビルドする

このプロジェクトの Unity セクションに必要なものはすべて完了したので、Unity から構築します。

1.  [ *ビルドの設定* ] (* [*ファイル* > * [ビルドの設定] * *) に移動します。

    ![](images/AzureLabs-Lab311-33.png)

2.  まだ存在しない場合は、 **Unity C \# プロジェクト** をティックします。

3.  [**ビルド**] をクリックします。 Unity は **エクスプローラー** ウィンドウを起動します。このウィンドウでは、アプリを作成するフォルダーを作成して選択する必要があります。 ここでそのフォルダーを作成し、「 **App**」という名前を指定します。 次に、 **アプリ** フォルダーを選択し、[ **フォルダーの選択**] をクリックします。

4.  Unity は、 **アプリ** フォルダーへのプロジェクトのビルドを開始します。

5.  Unity のビルドが完了すると (時間がかかる場合があります)、ビルドの場所で **ファイルエクスプローラー** ウィンドウを開きます (ウィンドウの上に常に表示されるとは限りませんが、新しいウィンドウが追加されたことが通知されます)。

## <a name="chapter-12---deploy-to-hololens"></a>第12章-HoloLens へのデプロイ

HoloLens に展開するには:

1.  Hololens が **開発者モード** になっていることを確認するには、HOLOLENS の IP アドレス (リモートデプロイ用) が必要です。 これを行うには、次の手順を実行します。

    1.  HoloLens を装着した後、 **設定** を開きます。

    2.  [**ネットワーク & インターネット**  >  **wi-fi**  >  **詳細オプション]** にアクセスします。

    3.  **IPv4** アドレスをメモしておきます。

    4.  次に、[**設定**] に戻り、   >  **開発者の**& セキュリティを更新します。

    5.  **開発者モードをに** 設定します。

2.  新しい Unity ビルド ( **アプリ** フォルダー) に移動し、 **Visual Studio** でソリューションファイルを開きます。

3.  **ソリューション構成** で、[**デバッグ**] を選択します。

4.  **ソリューションプラットフォーム** で、[ **X86、リモートコンピューター**] を選択します。 リモートデバイスの **IP アドレス** (この場合は、ここでメモした HoloLens) を挿入するように求められます。

    ![](images/AzureLabs-Lab311-34.png)

5.  [ **ビルド** ] メニューの [ **ソリューションの配置** ] をクリックして、アプリケーションを HoloLens にサイドロードします。

6.  アプリが HoloLens にインストールされているアプリの一覧に表示され、起動できる状態になります。

## <a name="your-microsoft-graph-hololens-application"></a>Microsoft Graph HoloLens アプリケーション

これで、Microsoft Graph を利用してユーザーカレンダーデータを読み取り、表示する mixed reality アプリが作成されました。

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a>ボーナス演習

### <a name="exercise-1"></a>演習1

Microsoft Graph を使用して、ユーザーに関するその他の情報を表示する

-   ユーザーの電子メール/電話番号/プロファイルの画像

### <a name="exercise-1"></a>演習1

音声制御を実装して、Microsoft Graph UI に移動します。