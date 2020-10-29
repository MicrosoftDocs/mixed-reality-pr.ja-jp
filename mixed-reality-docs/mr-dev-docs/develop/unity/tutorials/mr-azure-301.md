---
title: MR と Azure 301-言語翻訳
description: このコースでは、mixed reality アプリケーション内で Azure Translator Text API を実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, チュートリアル, api, 翻訳テキスト, hololens, イマーシブ, vr
ms.openlocfilehash: 2d5cf591d0dba3a3c516262dd9f78ec152afe2b5
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91688874"
---
# <a name="mr-and-azure-301-language-translation"></a>MR と Azure 301:言語翻訳

<br>

>[!NOTE]
>Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。  そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。  これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは " **_ありません_** "。  これらは、サポートされているデバイス上で継続して動作するように、保守されます。 今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。  この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。

<br>

このコースでは、Translator Text API と共に Azure Cognitive Services を使用して、混合の現実アプリケーションに翻訳機能を追加する方法について説明します。

![最終製品](images/AzureLabs-Lab1-00.png)

Translator Text API は、ほぼリアルタイムで動作する翻訳サービスです。 サービスはクラウドベースであり、REST API 呼び出しを使用して、アプリはニューラル機械翻訳テクノロジを利用してテキストを別の言語に変換できます。 詳細については、 [Azure Translator Text API のページ](https://azure.microsoft.com/services/cognitive-services/translator-text-api/)を参照してください。

このコースが完了すると、mixed reality アプリケーションが完成し、次のことができるようになります。

1.  ユーザーは、イマーシブ (VR) ヘッドセット (または HoloLens の内蔵マイク) に接続されているマイクに接続します。
2.  アプリはディクテーションをキャプチャし、Azure Translator Text API に送信します。
3.  翻訳結果は、Unity シーンの単純な UI グループに表示されます。

このコースでは、翻訳サービスから Unity ベースのサンプルアプリケーションに結果を取得する方法について説明します。 これらの概念は、構築しているカスタムアプリケーションに適用する必要があります。

## <a name="device-support"></a>デバイス サポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="../../../hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 301:言語翻訳</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> このコースでは主に Windows Mixed Reality イマーシブ (VR) ヘッドセットに焦点を当てていますが、このコースで学習した内容を Microsoft HoloLens に適用することもできます。 このコースに従うと、HoloLens をサポートするために必要となる可能性のある変更に関する注意事項が表示されます。 HoloLens を使用する場合、音声キャプチャ中にエコーが発生することがあります。

## <a name="prerequisites"></a>前提条件

> [!NOTE]
> このチュートリアルは、Unity と C# の基本的な経験がある開発者向けに設計されています。 また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証されたものを表します (2018 年5月)。 「 [ツールのインストール](../../install-the-tools.md) 」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に記載されているものよりも新しいソフトウェアで見つかったものと完全に一致するとは限りません。

このコースでは、次のハードウェアとソフトウェアをお勧めします。

- 開発用 PC で、 [Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) (VR) ヘッドセット開発と互換性があります。
- [開発者モードが有効になっている Windows 10 の作成者の更新プログラム (またはそれ以降)](../../install-the-tools.md#installation-checklist)
- [最新の Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- [Windows Mixed Reality イマーシブ (VR) ヘッドセット](../../../discover/immersive-headset-hardware-details.md)または開発者モードを有効にした[Microsoft HoloLens](../../../hololens-hardware-details.md)
- 内蔵マイク付きヘッドホンのセット (ヘッドセットにマイクとスピーカーが組み込まれていない場合)
- Azure のセットアップと翻訳の取得のためのインターネットアクセス

## <a name="before-you-start"></a>開始する前に

- このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。
- このチュートリアルのコードを使用すると、PC に接続されている既定のマイクデバイスから録音できます。 既定のマイクデバイスが、音声のキャプチャに使用する予定のデバイスに設定されていることを確認します。
- PC がディクテーションを有効にできるようにするには、[ **設定] > [プライバシー > 音声、インク & 入力** し、[ **音声サービスをオンに** する] ボタンを選択して、「候補」と入力します。
- ヘッドセットに接続されている (または内蔵されている) マイクとヘッドホンを使用している場合は、[ **オーディオと音声を > Mixed reality > 設定** ] で "ヘッドセットを磨耗したときにヘッドセットのマイクに切り替える" オプションがオンになっていることを確認してください。

   ![Mixed reality の設定](images/AzureLabs-Lab1-00-5.png)

   ![マイクの設定](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> このラボ用にイマーシブヘッドセットを開発している場合は、オーディオ出力デバイスの問題が発生する可能性があることに注意してください。 これは、unity の新しいバージョン (Unity 2018.2) で修正された Unity の問題に起因します。 この問題により、Unity は実行時に既定のオーディオ出力デバイスを変更できなくなります。 回避策として、上記の手順を完了していることを確認し、この問題が発生したときにエディターを閉じて再度開きます。

## <a name="chapter-1--the-azure-portal"></a>章 1-Azure Portal

Azure Translator API を使用するには、アプリケーションで使用できるようにサービスのインスタンスを構成する必要があります。

1.  [Azure Portal](https://portal.azure.com)にログインします。

    > [!NOTE]
    > まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。 このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。

2.  ログインしたら、左上隅にある [ **新規** ] をクリックし、"Translator Text API" を検索します。 **Enter** キーを押します。

    ![新しいリソース](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > 新しいポータルで、 **New** という単語が **リソースの作成** に置き換えられました。

3.  新しいページには、 *Translator Text API* サービスの説明が表示されます。 このページの左下にある [ **作成** ] ボタンを選択して、このサービスとの関連付けを作成します。

    ![Translator Text API サービスの作成](images/AzureLabs-Lab1-03.png)

4.  [ **作成** :

    1. このサービスインスタンスに必要な **名前** を挿入します。
    2. 適切な **サブスクリプション** を選択します。
    3. 適切な **価格レベル** を選択します。これが *Translator Text サービス* を初めて作成する場合は、free レベル (F0) を使用できます。
    4. リソースグループを選択するか、新しい **リソースグループ** を作成します。 リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。 1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのラボなど) を共通のリソースグループに保持することをお勧めします。

        > Azure リソースグループの詳細については、 [リソースグループ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)に関する記事をご覧ください。

    5. リソースグループの **場所** を決定します (新しいリソースグループを作成している場合)。 この場所は、アプリケーションを実行するリージョンに配置するのが理想的です。 一部の Azure 資産は、特定のリージョンでのみ利用できます。
    6. また、このサービスに適用されている使用条件を理解していることを確認する必要があります。
    7. **［作成］** を選択します

        ![[作成] ボタンを選択します。](images/AzureLabs-Lab1-04.png)

5.  [ **作成** ] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。
6.  サービスインスタンスが作成されると、ポータルに通知が表示されます。 

    ![Azure サービスの作成に関する通知](images/AzureLabs-Lab1-05.png)

7.  通知をクリックして、新しいサービスインスタンスを探索します。 

    ![リソースポップアップにアクセスします。](images/AzureLabs-Lab1-06.png)

8.  通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。 新しい Translator Text API サービスインスタンスが表示されます。 

    ![Translator Text API サービス] ページ](images/AzureLabs-Lab1-07.png)

9.  このチュートリアルでは、アプリケーションがサービスの呼び出しを行う必要があります。サービスは、サービスのサブスクリプションキーを使用して実行されます。 
10. *Translator Text* サービスの [ *クイックスタート* ] ページで、最初の手順に移動し、 *キーを取得* して [ **キー** ] をクリックします (これを行うには、[サービス] ナビゲーションメニューにある青いハイパーリンクキーをクリックします。これは、キーアイコンで示されます)。 これにより、サービス *キー* が表示されます。
11. 表示されているキーの1つをコピーします。これは、プロジェクトの後半で必要になります。 

## <a name="chapter-2--set-up-the-unity-project"></a>第2章: Unity プロジェクトを設定する

Mixed reality のイマーシブヘッドセットをセットアップしてテストします。

> [!NOTE]
> このコースでは、モーションコントローラーは必要ありません。 イマーシブヘッドセットの設定をサポートする必要がある場合は、 [次の手順に従っ](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)てください。

次に示すのは、mixed reality で開発するための一般的な設定であり、他のプロジェクトに適したテンプレートです。

1.  *Unity* を開き、[ **新規** ] をクリックします。 

    ![新しい Unity プロジェクトを開始します。](images/AzureLabs-Lab1-08.png)

2.  ここで、Unity プロジェクト名を指定する必要があります。 **MR_Translation** を挿入します。 プロジェクトの種類が **3d** に設定されていることを確認します。 場所を適切な *場所* に設定します (ルートディレクトリの方が適していることに注意してください)。 次に、[ **プロジェクトの作成** ] をクリックします。

    ![新しい Unity プロジェクトの詳細を指定します。](images/AzureLabs-Lab1-09.png)

3.  Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。 [ **> の設定の編集** ] に移動し、新しいウィンドウで [ **外部ツール** ] に移動します。 **外部スクリプトエディター** を **Visual Studio 2017** に変更します。 [ **基本設定** ] ウィンドウを閉じます。

    ![スクリプトエディターの設定を更新します。](images/AzureLabs-Lab1-10.png)

4.  次に、[ **ファイル > ビルド設定** ] に移動し、[プラットフォームの **切り替え** ] ボタンをクリックして、プラットフォームを **ユニバーサル Windows プラットフォーム** に切り替えます。

    ![[ビルドの設定] ウィンドウで、[プラットフォーム] を [UWP] に切り替えます。](images/AzureLabs-Lab1-11.png)

5.  [ **ファイル > ビルド設定** ] にアクセスし、次のことを確認します。

    1. **ターゲットデバイス** は **、任意のデバイス** に設定されます。

        > Microsoft HoloLens の場合は、 **ターゲットデバイス** を *HoloLens* に設定します。

    2. **ビルドの種類** が **D3D** に設定されています
    3. **SDK** は最新の **インストール** に設定されています
    4. **Visual Studio のバージョン** が、 **インストールされている最新** バージョンに設定されています
    5. **ビルドと実行** は **ローカルコンピューター** に設定されています
    6. シーンを保存し、ビルドに追加します。

        1. これを行うには、[開いている **シーンの追加** ] を選択します。 保存ウィンドウが表示されます。

            ![[開いているシーンを追加] ボタンをクリックする](images/AzureLabs-Lab1-12.png)

        2. この新しいフォルダーを作成し、今後のシーンに加えて、[ **新しいフォルダー** ] ボタンを選択します。新しいフォルダーを作成するには、名前を「 **シーン** 」にします。

            ![新しいスクリプトフォルダーの作成](images/AzureLabs-Lab1-13.png)

        3. 新しく作成した [ **シーン** ] フォルダーを開き、[ *ファイル名* : テキスト] フィールドに「 **MR_TranslationScene** 」と入力して、[ **保存** ] を押します。

            ![新しいシーンに名前を付けます。](images/AzureLabs-Lab1-14.png)

            > Unity プロジェクトに関連付けられている必要があるため、Unity のシーンを *Assets* フォルダー内に保存する必要があります。 Unity プロジェクトを構成する一般的な方法は、シーンフォルダー (およびその他の同様のフォルダー) を作成することです。

    7. それ以外の設定は、[ *ビルド設定* ] の [既定] のままにしておきます。

6. [ *ビルドの設定* ] ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 *インスペクター* が配置されている領域の関連パネルが開きます。 

    ![プレーヤーの設定を開きます。](images/AzureLabs-Lab1-15.png)

7. このパネルでは、いくつかの設定を確認する必要があります。

    1. [ **その他の設定** ] タブで、次のようにします。

        1. **スクリプトランタイムのバージョン** は **安定** している必要があります (.net 3.5 と同等)。
        2. **バックエンド** は **.net** である必要があります
        3. **API 互換性レベル** は **.net 4.6** である必要があります

            ![その他の設定を更新します。](images/AzureLabs-Lab1-16.png)
      
    2. [ **発行の設定** ] タブの [ **機能** ] で、次の項目を確認します。

        1. **InternetClient**
        2. **マイク**

            ![発行設定を更新しています。](images/AzureLabs-Lab1-17.png)

    3. パネルの下にある [ **XR settings** (発行の **設定** ] の下にあります) で、[ **サポートされている仮想現実** ] をティックし、 **Windows Mixed reality SDK** が追加されていることを確認します。

        ![X R の設定を更新します。](images/AzureLabs-Lab1-18.png)

8.  **ビルド設定** に戻ると、 *Unity C# プロジェクト* はグレーで表示されなくなりました。このの横にあるチェックボックスをオンにします。 
9.  [ビルド設定] ウィンドウを閉じます。
10. シーンとプロジェクトを保存します ([ **ファイル] > [シーン/ファイルの保存] > [プロジェクトの保存** ])。

## <a name="chapter-3--main-camera-setup"></a>第3章–メインカメラの設定

> [!IMPORTANT]
> このコースの *Unity セットアップ* コンポーネントをスキップしてコードに直接進む場合は、 [unitypackage をダウンロード](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage)し、 [*カスタムパッケージ*](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてから、 [第5章](#chapter-5--create-the-results-class)から続行してください。 引き続き Unity プロジェクトを作成する必要があります。

1.  [ *階層] パネル* には、 **メインカメラ** と呼ばれるオブジェクトが表示されます。このオブジェクトは、アプリケーションの "内側" にある "ヘッド" ポイントを表します。
2.  Unity ダッシュボードを前面に表示し、 **カメラのメイン** のユーザーオブジェクトを選択します。 [ *インスペクター] パネル* (通常はダッシュボード内の右側にあります) には、そのユーザーの *オブジェクト* のさまざまなコンポーネントが表示されます。これには、上部にある [ *変換* ]、[ *カメラ* ]、および他のコンポーネントがあります。 メインカメラの変換をリセットして、正しく配置されるようにする必要があります。
3.  これを行うには、カメラの *変換* コンポーネントの横にある **歯車** アイコンを選択し、[ **リセット** ] を選択します。 

    ![メインカメラの変換をリセットします。](images/AzureLabs-Lab1-19.png)
 
4.  *変換* コンポーネントは次のようになります。

    1. *位置* が **0、0、0** に設定されています。
    2. *回転* は **0、0、0** に設定されています
    3. と *Scale* が **1、1、1** に設定されます。

        ![カメラの変換情報](images/AzureLabs-Lab1-20.png)

5.  次に、 **メインカメラ** オブジェクトを選択した状態で、[ *インスペクター] パネル* の一番下にある [ **コンポーネントの追加** ] ボタンをクリックします。 
6.  そのボタンを選択し、次に示すように、 **オーディオソース** と呼ばれるコンポーネントの [検索] フィールドに「 *audio source* 」と入力するか、セクションを移動して検索します (enter キーを押すことによっても動作します)。
7.  次に示すように、 *オーディオソース* コンポーネントが **メインカメラ** に追加されます。

    ![オーディオソースコンポーネントを追加します。](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > Microsoft HoloLens の場合は、次の項目も変更する必要があります。これは、 **メインカメラ** の **カメラ** コンポーネントに含まれています。
    > - **フラグのクリア:** 純色。
    > - **背景** ' Black, Alpha 0 ' –16進数の色: #00000000。

## <a name="chapter-4--setup-debug-canvas"></a>第4章–セットアップのデバッグキャンバス

翻訳の入力と出力を表示するには、基本的な UI を作成する必要があります。 このコースでは、データを表示する複数の ' テキスト ' オブジェクトを含む Canvas UI オブジェクトを作成します。

1.  [ *階層] パネル* の空の領域を右クリックし、[ **UI** ] の下に **キャンバス** を追加します。

    ![新しいキャンバス UI オブジェクトを追加します。](images/AzureLabs-Lab1-22.png)

2.  キャンバスオブジェクトを選択した状態で、[ *インスペクター] パネル* (' canvas ' コンポーネント内) で、[ **レンダリングモード** ] を [ **ワールド空間** ] に変更します。 
3.  次に、 *インスペクターパネルの Rect 変換* で次のパラメーターを変更します。

    1. *POS*  -  **X** 0 **Y** 0 **Z** 40
    2. *幅* -500
    3. *高さ* -300
    4. *スケール*  - **X** 0.13 **Y** 0.13 **Z** 0.13

        ![キャンバスの rect 変換を更新します。](images/AzureLabs-Lab1-23.png)
 
4.  [ *階層] パネル* の **キャンバス** を右クリックし、[ **UI** ] をクリックして、 **パネル** を追加します。 この **パネル** には、シーンに表示されるテキストの背景が表示されます。
5.  [ *階層] パネル* の [ **UI** ] の下にある **パネル** を右クリックし、[ **テキスト] オブジェクト** を追加します。 合計で4つの UI テキストオブジェクトを作成した場合は、同じプロセスを繰り返します (ヒント: 最初の "テキスト" オブジェクトを選択している場合は、Ctrl キーを押し **ながら d** キーを押すだけで、合計4つまで)。 
6.  各 **テキストオブジェクト** を選択し、以下の表を使用して、[ *インスペクター] パネル* でパラメーターを設定します。

    1. *Rect 変換* コンポーネントの場合:

        | 名前                   | 変換- *位置*             | 幅      | [高さ]    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | マイクロ電話の Statuslabel  | **X** -80 **Y** 90 **Z** 0         | 300        | 30        |
        | AzureResponseLabel     | **X** -80 **Y** 30 **Z** 0         | 300        | 30        |
        | DictationLabel         | **X** -80 **Y** -30 **Z** 0        | 300        | 30        |
        | TranslationResultLabel | **X** -80 **Y** -90 **Z** 0        | 300        | 30        |


    2. **テキスト (スクリプト)** コンポーネントの場合:


        | 名前                   | テキスト               | フォント サイズ    |
        |:----------------------:|:------------------:|:------------:|
        | マイクロ電話の Statuslabel  | マイクの状態: | 20           |
        | AzureResponseLabel     | Azure Web 応答 | 20           |
        | DictationLabel         |   先ほど言ったことは、   | 20           |
        | TranslationResultLabel |    変換:    | 20           |

        ![UI ラベルに対応する値を入力します。](images/AzureLabs-Lab1-24.png)

    3. また、フォントスタイルを **太字** にします。 これにより、テキストが読みやすくなります。

        ![太字のフォント。](images/AzureLabs-Lab1-25.png)

7.  [第5章](#chapter-5--create-the-results-class)で作成された各 *ui テキストオブジェクト* に対して、新しい *子* **ui テキストオブジェクト** を作成します。 これらの子は、アプリケーションの出力を表示します。 *子* オブジェクトを作成するには、目的の親を右クリックし (例: *マイクロラベル statuslabel* )、[ **UI** ] を選択し、[ **テキスト** ] を選択します。
8.  これらの各子を選択し、以下の表を使用して、[インスペクター] パネルでパラメーターを設定します。

    1. **Rect 変換** コンポーネントの場合:

        | 名前                  | 変換- *位置* | 幅      | [高さ]    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | MicrophoneStatusText  | X 0 Y ~ 30 Z 0          | 300        | 30        |
        | AzureResponseText     | X 0 Y ~ 30 Z 0          | 300        | 30        |
        | DictationText         | X 0 Y ~ 30 Z 0          | 300        | 30        |
        | TranslationResultText | X 0 Y ~ 30 Z 0          | 300        | 30        |

    2. **テキスト (スクリプト)** コンポーネントの場合:

        | 名前                  | テキスト          | フォント サイズ    |
        |:---------------------:|:-------------:|:------------:|
        | MicrophoneStatusText  |      ??       | 20           |
        | AzureResponseText     |      ??       | 20           |
        | DictationText         |      ??       | 20           |
        | TranslationResultText |      ??       | 20           |

9. 次に、各テキストコンポーネントの [中央揃え] を選択します。

    ![テキストを整列します。](images/AzureLabs-Lab1-26.png)

10. **子 UI テキスト** オブジェクトが簡単に読み取れるようにするには、 *色* を変更します。 これを行うには、[ *色* ] の横にあるバー (現在は "Black") をクリックします。 

    ![UI テキストの出力に対応する値を入力します。](images/AzureLabs-Lab1-27.png)
 
11. 次に、新しい小さな *色* のウィンドウで、 *16 進数の色* を **0032EAFF** に変更します。

    ![色を青に更新します。](images/AzureLabs-Lab1-28.png)
 
12. **UI** の表示方法を次に示します。
    1.  [ *階層] パネル* で、次のようにします。

        ![指定された構造に階層があること。](images/AzureLabs-Lab1-29.png)

    2.  *シーン**ビューとゲームビュー* で、次のようにします。

        ![シーンビューとゲームビューを同じ構造にします。](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a>Chapter 5 – Results クラスを作成する

作成する必要のある最初のスクリプトは、 *results* クラスです。このクラスは、翻訳の結果を確認する手段を提供します。 クラスは、次のものを格納して表示します。 

- Azure からの応答結果。
- マイクの状態。 
- ディクテーションの結果 (音声テキスト)。
- 変換の結果。

このクラスを作成するには: 

1.  [ *プロジェクト] パネル* 内を右クリックし、[ **> フォルダーの作成** ] をクリックします。 フォルダーに **スクリプト** の名前を指定します。 
 
    ![Scripts フォルダーを作成します。](images/AzureLabs-Lab1-31.png)

    ![Scripts フォルダーを開きます。](images/AzureLabs-Lab1-32.png)
 
2.  **Scripts** フォルダー create を使用して、ダブルクリックして開きます。 次に、そのフォルダー内でを右クリックし、[ **Create >** Then **C# Script** ] を選択します。 スクリプトの *結果* に名前を指定します。 

    ![最初のスクリプトを作成します。](images/AzureLabs-Lab1-33.png)
 
3.  新しい *結果* スクリプトをダブルクリックして、 **Visual Studio** で開きます。
4.  次の名前空間を挿入します。

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  クラス内で、次の変数を挿入します。

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  次に、起動される *()* メソッドを追加します。このメソッドは、クラスの初期化時に呼び出されます。 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  最後に、さまざまな結果情報を UI に出力するメソッドを追加します。 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  *Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。

## <a name="chapter-6--create-the-microphonemanager-class"></a>Chapter 6 – *MicrophoneManager* クラスを作成する

2番目に作成するクラスは、 *MicrophoneManager* です。

このクラスの役割は次のとおりです。

- ヘッドセットまたはコンピューターに接続されている記録デバイスを検出する (どちらかの既定値)。
- オーディオ (音声) をキャプチャし、ディクテーションを使用して文字列として格納します。
- 音声が一時停止したら、ディクテーションを Translator クラスに送信します。
- 必要に応じて、音声キャプチャを停止できるメソッドをホストします。

このクラスを作成するには: 
1.  [ **Scripts** ] フォルダーをダブルクリックして開きます。 
2.  **Scripts** フォルダー内を右クリックし、[ **Create > C# Script** ] をクリックします。 スクリプトに *MicrophoneManager* という名前を指定します。 
3.  新しいスクリプトをダブルクリックして、Visual Studio で開きます。
4.  *MicrophoneManager* クラスの先頭にある次の名前空間を更新します。

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  次に、 *MicrophoneManager* クラス内に次の変数を追加します。

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  起動可能な *()* メソッドと *Start ()* メソッドのコードを追加する必要があります。 これらは、クラスの初期化時に呼び出されます。

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  *Update ()* メソッドは、このクラスでは使用されないため、 *削除* できます。
8.  次に、アプリが音声キャプチャを開始および停止するために使用するメソッドと、間もなくビルドする *Translator* クラスに渡すメソッドが必要です。 次のコードをコピーし、 *Start ()* メソッドの下に貼り付けます。

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > このアプリケーションではこれを使用しませんが、アプリケーションでのオーディオのキャプチャを停止する機能を実装する場合は、 *Stopcapturingaudio ()* メソッドもここで提供されています。

9.  次に、音声が停止したときに呼び出されるディクテーションハンドラーを追加する必要があります。 このメソッドは、ディクテーションされたテキストを *Translator* クラスに渡します。

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. Unity に戻る前に、変更内容を Visual Studio に保存してください。

> [!WARNING]  
> この時点で、 *Unity エディターのコンソール* パネルにエラーが表示されます ("Translator ' という名前は存在しません...")。 これは、コードが *トランスレーター* クラスを参照するためです。このクラスは、次の章で作成します。

## <a name="chapter-7--call-to-azure-and-translator-service"></a>第7章– Azure と translator サービスへの呼び出し

作成する必要がある最後のスクリプトは、 *Translator* クラスです。 

このクラスの役割は次のとおりです。

-   *Azure* を使用したアプリの認証 ( **認証トークン** の交換)。
-   **認証トークン** を使用して、翻訳するテキスト ( *MicrophoneManager* クラスから受信) を送信します。
-   変換された結果を受け取り、それを *結果* クラスに渡して UI で視覚化されるようにします。

このクラスを作成するには: 
1.  前に作成した **Scripts** フォルダーにアクセスします。 
2.  [ **プロジェクト] パネル** を右クリックし、[ **> C# スクリプト** ] を作成します。 スクリプト *変換* プログラムを呼び出します。
3.  新しい *Translator* スクリプトをダブルクリックして、 **Visual Studio で** 開きます。
4.  ファイルの先頭に次の名前空間を追加します。

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  次に、 *Translator* クラス内に次の変数を追加します。

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - 言語の **列挙** に挿入される言語は、単純な例です。 必要に応じて、さらに自由に追加できます。API は、 [60 を超える言語](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (Klingon を含む) をサポートしています。
    > - [使用可能な言語についてはより対話的なページ](https://www.microsoft.com/translator/business/languages/)がありますが、サイトの言語が ' ' に設定されている場合にのみページが動作しているように見えますが、Microsoft サイトではネイティブ言語にリダイレクトされる可能性があることに注意してください。 ページの下部にあるサイトの言語を変更するか、URL を変更することができます。
    > - 上記のコードスニペットの **Authorizationkey** 値は、 *Azure Translator Text API* をサブスクライブしたときに受け取った **キー** である必要があります。 これについては、 [第1章](#chapter-1--the-azure-portal)で説明しました。

6.  起動可能な *()* メソッドと *Start ()* メソッドのコードを追加する必要があります。 
7.  この場合、コードは、 *トークン* を取得するために、承認キーを使用して *Azure* を呼び出します。

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > トークンは10分後に期限切れになります。 アプリのシナリオによっては、同じコルーチン呼び出しを複数回行うことが必要になる場合があります。

8.  トークンを取得するコルーチンは次のとおりです。

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > IEnumerator メソッド **GetTokenCoroutine ()** の名前を編集する場合は、上記のコードの *StartCoroutine* と *StopCoroutine* の呼び出し文字列値を更新する必要があります。 [Unity のドキュメントに従って](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html)、特定の *コルーチン* を停止するには、文字列値メソッドを使用する必要があります。

9.  次に、 *MicrophoneManager* クラスによって受信されたテキストの翻訳を取得するために、("サポート" ストリームメソッドを含む) コルーチンを追加します。 このコードは、 *Azure Translator Text API* に送信するクエリ文字列を作成し、内部 Unity UnityWebRequest クラスを使用して、クエリ文字列を使用してエンドポイントへの ' Get ' 呼び出しを行います。 結果を使用して、結果オブジェクトの翻訳を設定します。 次のコードは、の実装を示しています。

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. *Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。

## <a name="chapter-8--configure-the-unity-scene"></a>Chapter 8 – Unity シーンの構成

1.  Unity エディターに戻り、[ **スクリプト** ] フォルダーの [ *Results* *] クラスを* クリックして、[ *階層] パネル* の [ **メインカメラ** ] オブジェクトにドラッグします。
2.  **メインカメラ** をクリックし、[ *インスペクター] パネル* を確認します。 新しく追加された *スクリプト* コンポーネント内には、空の値を持つ4つのフィールドがあることがわかります。 これらは、コード内のプロパティへの出力参照です。 
3.  次の図に示すように、該当する **テキスト** オブジェクトを [ *階層] パネル* から4つのスロットにドラッグします。

    ![指定された値でターゲット参照を更新します。](images/AzureLabs-Lab1-34.png)
  
4.  次に、[ **スクリプト** ] フォルダーの *Translator* クラスをクリックして、[ *階層] パネル* の [ **メインカメラ** ] オブジェクトにドラッグします。 
5.  次に、[ **スクリプト** ] フォルダーの *MicrophoneManager* クラスをクリックして、[ *階層] パネル* の [ **メインカメラ** ] オブジェクトにドラッグします。 
6.  最後に、 **メインカメラ** をクリックし、[ *インスペクター] パネル* を確認します。 ドラッグしたスクリプトには、2つのドロップダウンボックスがあり、それらを使用して言語を設定できることがわかります。
 
    ![目的の翻訳言語が入力されていることを確認します。](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a>第9章– mixed reality でのテスト

この時点で、シーンが正しく実装されていることをテストする必要があります。

次のことを確認します。

- [章 1](#chapter-1--the-azure-portal)で説明したすべての設定が正しく設定されています。 
- *Results* 、 *Translator* 、および *MicrophoneManager* の各スクリプトは、 **メインカメラ** オブジェクトにアタッチされます。 
- *Azure Translator Text API* サービス **キー** は、 *Translator* スクリプト内の **authorizationkey** 変数内に配置しました。  
- *メインカメラインスペクターパネル* のすべてのフィールドが適切に割り当てられます。
- マイクがシーンの実行中に機能している (そうでない場合、接続されているマイクが *既定* のデバイスであること、および [Windows 内で正しく設定](https://support.microsoft.com/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)されていることを確認してください)。

イマーシブヘッドセットをテストするには、 *Unity エディター* の [ **再生** ] ボタンを押します。
アプリは、接続されているイマーシブヘッドセットを介して機能している必要があります。

> [!WARNING]  
> 既定のオーディオデバイスの変更について Unity コンソールにエラーが表示される場合は、シーンが想定どおりに機能しない可能性があります。 これは、mixed reality ポータルが、ヘッドセットを持つヘッドホン用の組み込みマイクを扱う方法に起因します。 このエラーが表示された場合は、単にシーンを停止してからもう一度開始するだけで、期待どおりに動作するはずです。

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a>Chapter 10 –ローカルコンピューターに UWP ソリューションとサイドロードを構築する

このプロジェクトの Unity セクションに必要なものはすべて完了したので、Unity から構築します。

1.  **ビルド設定** に移動します: **ファイル > ビルド設定...**
2.  [ **ビルドの設定** ] ウィンドウで、[ **ビルド** ] をクリックします。

    ![Unity シーンをビルドします。](images/AzureLabs-Lab1-36.png)
  
3.  **Unity C# プロジェクト** をまだティックしていない場合は、ティックします。
4.  [ **ビルド** ] をクリックします。 Unity は *エクスプローラー* ウィンドウを起動します。このウィンドウでは、アプリを作成するフォルダーを作成して選択する必要があります。 ここでそのフォルダーを作成し、「 *App* 」という名前を指定します。 次に、 *アプリ* フォルダーを選択し、 **[フォルダーの選択]** をクリックします。 
5.  Unity は、 *アプリ* フォルダーへのプロジェクトのビルドを開始します。 
6.  Unity のビルドが完了すると (時間がかかる場合があります)、ビルドの場所で *ファイルエクスプローラー* ウィンドウを開きます (ウィンドウの上に常に表示されるとは限りませんが、新しいウィンドウが追加されたことが通知されます)。

## <a name="chapter-11--deploy-your-application"></a>第11章–アプリケーションのデプロイ

アプリケーションをデプロイするには:

1.  新しい Unity ビルド ( *アプリ* フォルダー) に移動し、 *Visual Studio* でソリューションファイルを開きます。
2.  ソリューション構成で、[ **デバッグ** ] を選択します。
3.  ソリューションプラットフォームで、[ **x86** , **ローカルコンピューター** ] を選択します。 

    > Microsoft HoloLens の場合、これを *リモートコンピューター* に設定する方が簡単な場合があります。これにより、コンピューターにテザリングさされることはありません。 ただし、次の手順も実行する必要があります。
    > - HoloLens の **IP アドレス** を確認します。これは、 *[設定 > ネットワーク & インターネット > Wi-fi > 詳細オプション]* にあります。IPv4 は、使用するアドレスです。 
    > - *開発者モード* が **オンに** なっていることを確認します。 *開発者向けのセキュリティ > の更新プログラム & の > の設定* にあります。

    ![Visual Studio からソリューションをデプロイします。](images/AzureLabs-Lab1-37.png)
    
 
4.  [ **ビルド] メニュー** の [ **ソリューションの配置** ] をクリックして、アプリケーションを PC にサイドロードします。
5.  アプリがインストール済みのアプリの一覧に表示され、起動できる状態になります。
6.  アプリを起動すると、マイクへのアクセスを承認するように求められます。 [ **はい** ] ボタンをクリックしてください。
7.  これで、翻訳を開始する準備ができました。

## <a name="your-finished-translation-text-api-application"></a>完成した翻訳テキスト API アプリケーション

これで、Azure Translation Text API を活用して音声を翻訳されたテキストに変換する、mixed reality アプリを構築しました。

![最終的な製品。](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a>ボーナス演習

### <a name="exercise-1"></a>演習1

音声合成機能をアプリに追加して、返されたテキストが読み上げられるようにすることができますか。

### <a name="exercise-2"></a>演習2

言語を変更するたびに、アプリを再構築する必要がないように、ユーザーがアプリ自体でソースと出力の言語 (' from ' と ' to ') を変更できるようにします。
