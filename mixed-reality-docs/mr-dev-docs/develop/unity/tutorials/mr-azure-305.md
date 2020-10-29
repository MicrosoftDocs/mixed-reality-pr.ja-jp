---
title: MR と Azure 305-Functions と storage
description: このコースでは、mixed reality アプリケーション内で Azure Storage と関数を実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, チュートリアル, api, 関数, ストレージ, hololens, イマーシブ, vr
ms.openlocfilehash: 83da419fe780368962af9e4d833ebe86d46f1b81
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91687847"
---
# <a name="mr-and-azure-305-functions-and-storage"></a>MR と Azure 305:機能とストレージ

<br>

>[!NOTE]
>Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。  そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。  これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは " **_ありません_** "。  これらは、サポートされているデバイス上で継続して動作するように、保守されます。 今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。  この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。

<br> 

![最終製品-開始](images/AzureLabs-Lab5-00.png)

このコースでは、Azure Functions を作成して使用し、混合の現実アプリケーション内で Azure Storage リソースを使用してデータを格納する方法について説明します。

*Azure Functions* は Microsoft のサービスであり、開発者は Azure で小さなコードである "Functions" を実行できます。 これにより、ローカルアプリケーションではなく、クラウドに作業を委任することができます。これには多くのメリットがあります。 *Azure Functions* は、C \# 、F \# 、Node.js、Java、PHP など、いくつかの開発言語をサポートしています。 詳細については、 [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview)に関する記事をご覧ください。

*Azure Storage* は Microsoft のクラウドサービスであり、開発者はデータを格納できます。このサービスは、高可用性、セキュリティ、耐久性、拡張性、および冗長性を備えています。 これは、Microsoft がすべてのメンテナンスと重大な問題を処理することを意味します。 詳細については、 [Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-introduction)に関する記事をご覧ください。

このコースを完了すると、現実のイマーシブヘッドセットアプリケーションが完成し、次のことができるようになります。

1.  ユーザーがシーンを見つめていることを許可します。
2.  ユーザーが 3D ' ボタン ' で gazes たときにオブジェクトの生成をトリガーします。
3.  生成されたオブジェクトは、Azure 関数によって選択されます。
4.  各オブジェクトが生成されると、アプリケーションは *Azure Storage* にある *Azure ファイル* にオブジェクトの種類を格納します。
5.  もう一度読み込むと、 *Azure ファイル* データが取得され、アプリケーションの前のインスタンスから生成されたアクションの再生に使用されます。

アプリケーションでは、結果をデザインと統合する方法については、お客様のニーズに合わせてください。 このコースは、Azure サービスを Unity プロジェクトと統合する方法を説明することを目的としています。 このコースで得られた知識を使用して、mixed reality アプリケーションを強化することができます。

## <a name="device-support"></a>デバイス サポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="../../../hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td>MR と Azure 305:機能とストレージ</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> このコースでは主に Windows Mixed Reality イマーシブ (VR) ヘッドセットに焦点を当てていますが、このコースで学習した内容を Microsoft HoloLens に適用することもできます。 このコースに従うと、HoloLens をサポートするために必要となる可能性のある変更に関する注意事項が表示されます。

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
- Azure リソースを作成するための Azure アカウントへのサブスクリプション
- Azure のセットアップとデータ取得のためのインターネットアクセス

## <a name="before-you-start"></a>開始する前に

このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。

## <a name="chapter-1---the-azure-portal"></a>章 1-Azure Portal

**Azure Storage サービス** を使用するには、Azure portal で **ストレージアカウント** を作成し、構成する必要があります。

1.  [Azure Portal](https://portal.azure.com)にログインします。

    > [!NOTE]
    > まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。 このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。

2.  ログインしたら、左上隅にある [ **新規** ] をクリックし、[ *ストレージアカウント* ] を検索して、 **Enter キー** を押します。

    ![azure storage の検索](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > 新しいポータルで、 **New** という単語が **リソースの作成** に置き換えられました。

3.  新しいページには、 *Azure Storage アカウント* サービスの説明が表示されます。 このプロンプトの左下にある [ **作成** ] ボタンを選択して、このサービスとの関連付けを作成します。

    ![サービスの作成](images/AzureLabs-Lab5-02.png)

4.  [ **作成** :

    1.  アカウントの *名前* を挿入します。このフィールドには数字と小文字のみを使用できることに注意してください。

    2.  [ *デプロイモデル* ] で、[ **リソースマネージャー** ] を選択します。

    3.  [ *アカウントの種類* ] で、[ **ストレージ (汎用 v1)** ] を選択します。

    4.  リソースグループの *場所* を決定します (新しいリソースグループを作成している場合)。 この場所は、アプリケーションを実行するリージョンに配置するのが理想的です。 一部の Azure 資産は、特定のリージョンでのみ利用できます。

    5.  *レプリケーション* の場合は、[ **読み取りアクセス-geo 冗長ストレージ (RA-GRS)** ] を選択します。

    6.  *[パフォーマンス]* には **[Standard]** を選択します

    7.  *安全な転送* は無効のまま **に** しておく必要があります。

    8.  *サブスクリプション* を選択します。

    9. リソースグループを選択するか、新しい *リソースグループ* を作成します。 リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。 1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのラボなど) を共通のリソースグループに保持することをお勧めします。 

        > Azure リソースグループの詳細については、 [リソースグループ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)に関する記事をご覧ください。

    10. また、このサービスに適用されている使用条件を理解していることを確認する必要があります。

    11. **［作成］** を選択します

        ![入力サービス情報](images/AzureLabs-Lab5-03.png)

5.  [ **作成** ] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。

6.  サービスインスタンスが作成されると、ポータルに通知が表示されます。

    ![azure ポータルでの新しい通知](images/AzureLabs-Lab5-04.png)

7.  通知をクリックして、新しいサービスインスタンスを探索します。

    ![リソースにアクセス](images/AzureLabs-Lab5-05.png)

8.  通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。 新しい *ストレージアカウント* のサービスインスタンスが表示されます。

    ![アクセス キー](images/AzureLabs-Lab5-06.png)

9.  [ *アクセスキー* ] をクリックして、このクラウドサービスのエンドポイントを表示します。 *メモ帳* または同様の方法を使用して、後で使用するためにいずれかのキーをコピーします。 また、 *接続文字列* の値もメモしておいてください。これは、後で作成する *azureservices* クラスで使用されるためです。

    ![接続文字列のコピー](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a>Chapter 2-Azure 関数の設定

次に、azure サービスで **azure** **関数** を作成します。

**Azure 関数** を使用すると、コード内で従来の関数を使用した場合とほぼ同じ処理を行うことができます。これは、azure アカウントにアクセスするための資格情報を持つ任意のアプリケーションからこの関数にアクセスできるという点です。

Azure 関数を作成するには、次のようにします。

1.  *Azure Portal* で、左上隅にある [ **新規** ] をクリックし、 *Function App* を検索して、 **Enter キー** を押します。

    ![function app の作成](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > 新しいポータルで、 **New** という単語が **リソースの作成** に置き換えられました。

2.  新しいページには、 *Azure Function App* サービスの説明が表示されます。 このプロンプトの左下にある [ **作成** ] ボタンを選択して、このサービスとの関連付けを作成します。

    ![関数アプリの情報](images/AzureLabs-Lab5-09.png)

3.  [ **作成** :

    1.  *アプリ名* を指定します。 ここでは、文字と数字のみを使用できます (大文字または小文字を使用できます)。

    2.  任意の *サブスクリプション* を選択します。

    3. リソースグループを選択するか、新しい *リソースグループ* を作成します。 リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。 1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのラボなど) を共通のリソースグループに保持することをお勧めします。 

        > Azure リソースグループの詳細については、 [リソースグループ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)に関する記事をご覧ください。

    4.  この演習では、選択した **OS** として [ *Windows* ] を選択します。

    5.  **ホスティングプラン** の *従量課金プラン* を選択します。

    6.  リソースグループの *場所* を決定します (新しいリソースグループを作成している場合)。 この場所は、アプリケーションを実行するリージョンに配置するのが理想的です。 一部の Azure 資産は、特定のリージョンでのみ利用できます。 最適なパフォーマンスを得るには、ストレージアカウントと同じリージョンを選択します。

    7.  [ *ストレージ* ] で、[既存のものを **使用** ] を選択し、ドロップダウンメニューを使用して、以前に作成したストレージを検索します。

    8.  この演習では、 *Application Insights* オフのままにします。

        ![入力関数アプリの詳細](images/AzureLabs-Lab5-10.png)

4.  **[作成]** ボタンをクリックします。

5.  [ **作成** ] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。

6.  サービスインスタンスが作成されると、ポータルに通知が表示されます。

    ![新しい azure portal の通知](images/AzureLabs-Lab5-11.png)

7.  通知をクリックして、新しいサービスインスタンスを探索します。 

    ![リソース関数アプリにアクセス](images/AzureLabs-Lab5-12.png)

8.  通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。 新しい *Function App* サービスインスタンスが表示されます。

9.  *Function App* ダッシュボードで、左側のパネルにある *関数* の上にマウスポインターを置き、 **プラス記号 (+)** をクリックします。

    ![新しい関数の作成](images/AzureLabs-Lab5-13.png)

10. 次のページで、[ **Webhook + API** ] が選択されていることを確認し、[ *言語の選択]* で [ **CSharp** ] を選択します。このチュートリアルで使用する言語です。 最後に、[ **この関数を作成** ] ボタンをクリックします。

    ![web フック csharp を選択します](images/AzureLabs-Lab5-14.png)

11. コードページ (csx を実行します) に移動します (ただし、それ以外の場合は、左側のパネル内の [関数] ボックスの一覧で新しく作成した関数をクリックします)。

    ![新しい関数を開く](images/AzureLabs-Lab5-15.png)

12. 関数に次のコードをコピーします。 この関数は、呼び出されたときに、0から2までのランダムな整数を返します。 既存のコードについて心配しないでください。一番上に貼り付けてもかまいません。

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. **[保存]** を選択します。

14. 結果は次の図のようになります。

15. [ **関数の URL の取得** ] をクリックし、表示されている *エンドポイント* を書き留めます。 このコースの後半で作成する *Azureservices* クラスに挿入する必要があります。

    ![関数エンドポイントを取得する](images/AzureLabs-Lab5-16.png)

    ![関数エンドポイントの挿入](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a>章 3-Unity プロジェクトの設定

次に示すのは、Mixed Reality で開発するための一般的な設定です。そのため、他のプロジェクトに適したテンプレートです。

Mixed reality のイマーシブヘッドセットをセットアップしてテストします。

> [!NOTE]
> このコースでは、モーションコントローラーは必要 **ありません** 。 イマーシブヘッドセットの設定をサポートする必要がある場合は、 [mixed reality のセットアップ](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)に関する記事をご覧ください。

1.  Unity を開き、[ **新規** ] をクリックします。

    ![新しい unity プロジェクトの作成](images/AzureLabs-Lab5-17.png)

2.  ここで、Unity プロジェクト名を指定する必要があります。 **MR_Azure_Functions** を挿入します。 プロジェクトの種類が **3d** に設定されていることを確認します。 場所を適切な *場所* に設定します (ルートディレクトリの方が適していることに注意してください)。 次に、[ **プロジェクトの作成** ] をクリックします。

    ![新しい unity プロジェクトに名前を付ける](images/AzureLabs-Lab5-18.png)

3.  Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。 [設定の **編集** ] に移動し、  >  **Preferences** 新しいウィンドウで [ **外部ツール** ] に移動します。 **外部スクリプトエディター** を **Visual Studio 2017** に変更します。 [ **基本設定** ] ウィンドウを閉じます。

    ![visual studio をスクリプトエディターとして設定する](images/AzureLabs-Lab5-19.png)

4.  次に、[ **ファイル**  >  ] [ **ビルドの設定** ] の順に移動し、[ **プラットフォームの切り替え** ] ボタンをクリックして、プラットフォームを **ユニバーサル Windows プラットフォーム** に切り替えます。

    ![プラットフォームを uwp に切り替える](images/AzureLabs-Lab5-20.png)

5.  **ファイル**  >  の **ビルド設定** にアクセスして、次のことを確認してください。

    1. **ターゲットデバイス** は **、任意のデバイス** に設定されます。

        > Microsoft HoloLens の場合は、 **ターゲットデバイス** を *HoloLens* に設定します。

    2. **ビルドの種類** が **D3D** に設定されています

    3. **SDK** は最新の **インストール** に設定されています

    4. **Visual Studio のバージョン** が、 **インストールされている最新** バージョンに設定されています

    5. **ビルドと実行** は **ローカルコンピューター** に設定されています

    6. シーンを保存し、ビルドに追加します。

        1.  これを行うには、[開いている **シーンの追加** ] を選択します。 保存ウィンドウが表示されます。

            ![オープンシーンを追加する](images/AzureLabs-Lab5-21.png)

        2.  この新しいフォルダーを作成し、今後のシーンに加えて、[ **新しいフォルダー** ] ボタンを選択します。新しいフォルダーを作成するには、名前を「 **シーン** 」にします。

            ![シーンフォルダーの作成](images/AzureLabs-Lab5-22.png)

        3.  新しく作成された [ **シーン** ] フォルダーを開き、[ **ファイル名:** テキスト] フィールドに「[アプリケーション]」 **と入力し、[****保存** ] をクリックします。

            ![関数シーンの保存](images/AzureLabs-Lab5-23.png)

6.  それ以外の設定は、[ **ビルド設定** ] の [既定] のままにしておきます。

    ![既定のビルド設定をそのまま使用する](images/AzureLabs-Lab5-24.png)

7.  [ *ビルドの設定* ] ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 *インスペクター* が配置されている領域の関連パネルが開きます。

    ![インスペクターのプレーヤー設定](images/AzureLabs-Lab5-25.png)

8.  このパネルでは、いくつかの設定を確認する必要があります。

    1.  [ **その他の設定** ] タブで、次のようにします。

        1.  **Scripting Runtime のバージョン** は **実験的** (.net 4.6 と同等) である必要があります。これにより、エディターを再起動する必要が生じます。
        2.  **バックエンド** は **.net** である必要があります
        3.  **API 互換性レベル** は **.net 4.6** である必要があります

    2.  [ **発行の設定** ] タブの [ **機能** ] で、次の項目を確認します。
        
        -  **InternetClient**

            ![機能の設定](images/AzureLabs-Lab5-26.png)

    3.  パネルの下にある [ **XR settings** ( **発行設定** ] の下にあります) で、[ **Virtual Reality がサポートされている** ] をオンにして、 **Windows Mixed reality SDK** が追加されていることを確認します。

        ![XR 設定の設定](images/AzureLabs-Lab5-27.png)

9.  *ビルド設定* に戻る *Unity C# プロジェクト* はグレーで表示されなくなりました。このの横にあるチェックボックスをオンにします。

    ![c# プロジェクトの tick](images/AzureLabs-Lab5-28.png)

10.  [ビルド設定] ウィンドウを閉じます。

11. シーンとプロジェクトを保存します ( **ファイル**  >  **保存シーン/ファイル**  >  **保存プロジェクト** )。

## <a name="chapter-4---setup-main-camera"></a>第4章-セットアップのメインカメラ

> [!IMPORTANT]
> このコースの構成要素をスキップし *て、コード* に直接進む場合は、unitypackage を [ダウンロード](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)して、 [カスタムパッケージ](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてください。 これには、次の章の Dll も含まれます。 インポート後、 [第7章](#chapter-7---create-the-azureservices-class)から続行します。 

1.  [ *階層] パネル* には、 **メインカメラ** と呼ばれるオブジェクトが表示されます。このオブジェクトは、アプリケーションの "内側" にある "ヘッド" ポイントを表します。

2.  Unity ダッシュボードを前面に表示し、 **カメラのメイン** のユーザーオブジェクトを選択します。 [ *インスペクター] パネル* (通常はダッシュボード内の右側にあります) には、そのユーザーの *オブジェクト* のさまざまなコンポーネントが表示されます。これには、上部にある [ *変換* ]、[ *カメラ* ]、および他のコンポーネントがあります。 メインカメラの変換をリセットして、正しく配置されるようにする必要があります。

3.  これを行うには、カメラの *変換* コンポーネントの横にある **歯車** アイコンを選択し、[ **リセット** ] を選択します。

    ![変換のリセット](images/AzureLabs-Lab5-29.png)

4.  次に、 **変換** コンポーネントを次のように更新します。

    |         |    変換-位置   |       |
    | :-----: | :-----------------------: | :----:|
    | **X**   | **Y**                     | **Z** |
    | 0       | 1                         | 0     |    

    |       | 変換-回転 |       |
    | :---: | :------------------: | :----:|
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 0     |

    |       | 変換-スケール |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 1     | 1                 | 1     |

    ![カメラの変換の設定](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a>章 5-Unity シーンの設定

1.  [ *階層] パネル* の空の領域を右クリックし、[ **3d オブジェクト** ] の下に **平面** を追加します。

    ![新しい平面の作成](images/AzureLabs-Lab5-31.png)

2.  [ **平面** ] オブジェクトを選択した状態で、[ *インスペクター] パネル* の次のパラメーターを変更します。

    |       | 変換-位置 |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 4     |

    |       | 変換-スケール |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 10    | 1                 | 10    |

    ![平面の位置とスケールの設定](images/AzureLabs-Lab5-32.png)

    ![平面のシーンビュー](images/AzureLabs-Lab5-33.png)

3.  [ *階層] パネル* の空の領域を右クリックし、[ **3d オブジェクト** ] の下に **キューブ** を追加します。

    1.  キューブの名前を **GazeButton** に変更します (キューブが選択されている状態で、[F2] を押します)。

    2.  [ *インスペクター] パネル* で、次のパラメーターを変更します。

        |       | 変換-位置 |       |
        | :---: | :------------------: |:-----:|
        | **X** | **Y**                | **Z** |
        | 0     | 3                    | 5     |


        ![宝石ボタンの変換の設定](images/AzureLabs-Lab5-34.png)

        ![宝石ボタンシーンビュー](images/AzureLabs-Lab5-35.png)

    3.  [ **タグ] ドロップダウン** ボタンをクリックし、[ **タグの追加** ] をクリックして [ *タグ & レイヤー] ペイン* を開きます。

        ![新しいタグの追加](images/AzureLabs-Lab5-36.png)

        ![プラスを選択](images/AzureLabs-Lab5-37.png)

    4.  **+ (正符号)** ボタンを選択し、[ *新しいタグ名* ] フィールドに「 **GazeButton** 」と入力して、[ **保存** ] をクリックします。

        ![新しいタグに名前を付ける](images/AzureLabs-Lab5-38.png)

    5.  *階層パネル* で **GazeButton** オブジェクトをクリックし、[ *インスペクター] パネル* で新しく作成された **GazeButton** タグを割り当てます。

        ![新しいタグを宝石ボタンに割り当てる](images/AzureLabs-Lab5-39.png)

4.  [ *階層] パネル* で **GazeButton** オブジェクトを右クリックし、[ **空** のオブジェクト] ( *子* オブジェクトとして追加される) を追加します。

5.  新しいオブジェクトを選択し、名前を **ShapeSpawnPoint** に変更します。

    1.  [ *インスペクター] パネル* で、次のパラメーターを変更します。

        |       | 変換-位置 |       |
        | :---: | :------------------: |:----: |
        | **X** |**Y**                 | **Z** |
        | 0     | -1                   | 0     |

        ![図形生成ポイント変換の更新](images/AzureLabs-Lab5-40.png)

        ![シェイプ生成ポイントシーンビュー](images/AzureLabs-Lab5-41.png)

6.  次に、Azure サービスの状態に関するフィードバックを提供する **3D テキスト** オブジェクトを作成します。

    階層パネルで **GazeButton** をもう一度右クリックし、 **3d オブジェクト**  >  **3d テキスト** オブジェクトを *子* として追加します。

    ![新しい3D テキストオブジェクトの作成](images/AzureLabs-Lab5-42.png)

7.  **3D テキスト** オブジェクトの名前を **AzureStatusText** に変更します。

8.  **AzureStatusText** オブジェクトの変換を次のように変更します。

    |       | 変換-位置 |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | -0.6  |

    |       | 変換-スケール |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 0.1   | 0.1               | 0.1   |


    > [!NOTE]
    > 次のテキストメッシュコンポーネントが更新されたときに修正されるため、センター外であるように見える場合は心配しないでください。

9.  次のように **テキストメッシュ** コンポーネントを変更します。

    ![テキストメッシュコンポーネントの設定](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > ここで選択した色は、16進数の色です。 **000000Ff** でも自由に選択できますが、読み取り可能であることを確認してください。

10. 階層パネルの構造は次のようになります。

    ![階層内のテキストメッシュ](images/AzureLabs-Lab5-43b.png)

10. シーンは次のようになります。

    ![シーンビューのテキストメッシュ](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a>Chapter 6-Unity 用の Azure Storage のインポート

Azure Storage for Unity を使用します (これ自体が .Net SDK for Azure を利用します)。 詳細については、 [「Unity の Azure Storage](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)」を参照してください。

現在、Unity には、インポート後にプラグインを再構成する必要がある既知の問題があります。 バグが解決された後、これらの手順 (このセクションでは 4-7) は不要になりました。

SDK を独自のプロジェクトにインポートするには、最新の [". unitypackage" を GitHub から](https://aka.ms/azstorage-unitysdk)ダウンロードしていることを確認します。 次に、以下を実行します。

1.  [ **.unitypackage** **Assets**  >  **Import package**  >  **Custom package (カスタムパッケージ** のインポート)] メニューオプションを使用して、unitypackage ファイルを Unity に追加します。

2.  ポップアップ表示される [ **Unity パッケージのインポート** ] ボックスで、[ **プラグイン** ストレージ] の下のすべてを選択でき  >  **Storage** ます。 このコースでは不要なため、他のすべてをオフにします。

    ![パッケージへのインポート](images/AzureLabs-Lab5-45.png)

3.  [ **インポート** ] ボタンをクリックして、プロジェクトに項目を追加します。

4.  [プロジェクト] ビューの [ *プラグイン* ] の下にある *ストレージ* フォルダーにアクセスし、次のプラグイン *のみ* を選択します。

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

        ![プラットフォームをすべてオフにする](images/AzureLabs-Lab5-46.png)

5.  *これらの特定のプラグイン* を選択した状態で、任意の *プラットフォーム* を **オフ****にし、** [ *wsaplayer* ]、[ **適用** ] の順にクリックします。

    ![プラットフォーム dll を適用する](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > これらの特定のプラグインを Unity エディターでのみ使用するようにマークしています。 これは、プロジェクトが Unity からエクスポートされた後に使用される、WSA フォルダー内に同じプラグインの異なるバージョンがあるためです。

6.  [ *ストレージ* プラグイン] フォルダーで、[のみ] を選択します。

    -   Microsoft.Data.Services.Client

        ![dll のプロセスを設定しない](images/AzureLabs-Lab5-48.png)

7.  [ *プラットフォームの設定* ] の [ **処理しない** ] チェックボックスをオンにし、[ **適用** ] をクリックします。

    ![処理を適用しない](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > Unity アセンブリ patcher がこのプラグインを処理するのが困難であるため、このプラグインを "処理しない" としてマークしています。 このプラグインは、処理されていなくても動作します。

## <a name="chapter-7---create-the-azureservices-class"></a>第7章-AzureServices クラスの作成

最初に作成するクラスは、 *Azureservices* クラスです。

*Azureservices* クラスは次のことを担当します。

-   Azure アカウントの資格情報を保存しています。

-   Azure アプリ関数を呼び出しています。

-   Azure クラウドストレージ内のデータファイルのアップロードとダウンロード。

このクラスを作成するには:

1.  [プロジェクト] パネルの [フォルダーの **作成** ] で、 *アセット* フォルダーを右クリックし  >  **Folder** ます。 フォルダーに **スクリプト** の名前を指定します。

    ![新しいフォルダーの作成](images/AzureLabs-Lab5-50.png)

    ![呼び出しフォルダー-スクリプト](images/AzureLabs-Lab5-51.png)

2.  先ほど作成したフォルダーをダブルクリックして開きます。

3.  フォルダー内を右クリックし、[C# スクリプトの **作成** ] をクリック  >  **C# Script** します。 *Azureservices* スクリプトを呼び出します。

4.  新しい *Azureservices* クラスをダブルクリックして、 *Visual Studio* で開きます。

5.  *Azureservices* の先頭に次の名前空間を追加します。

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  *Azureservices* クラス内に次のインスペクターフィールドを追加します。

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  次に、 *Azureservices* クラス内に次のメンバー変数を追加します。

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > *エンドポイント* と *接続文字列* の値は、azure Portal の azure storage の値に置き換えてください。

8.  起動可能な *()* メソッドと *Start ()* メソッドのコードを追加する必要があります。 これらのメソッドは、クラスの初期化時に呼び出されます。

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > *CallAzureFunctionForNextShape ()* のコードについては、今後の [章](#chapter-10---completing-the-azureservices-class)で説明します。

9.  *Update ()* メソッドは、このクラスでは使用されないため、削除します。

10. 変更内容を Visual Studio に保存し、Unity に戻ります。

11. [スクリプト] フォルダーの [ *Azureservices* ] クラスをクリックし、[ *階層] パネル* の [メインカメラ] オブジェクトにドラッグします。

12. メインカメラを選択し、 **GazeButton** オブジェクトの下にある **AzureStatusText** 子オブジェクトを取得します。次に、このオブジェクトを *インスペクター* の **AzureStatusText** reference Target フィールド内に配置して、 *azureservices* スクリプトへの参照を指定します。

    ![azure 状態テキスト参照ターゲットの割り当て](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a>章 8-図形ファクトリクラスを作成する

次に作成するスクリプトは、 *図形ファクトリ* クラスです。 このクラスの役割は、要求されたときに新しい図形を作成し、 *図形の履歴リスト* に作成された図形の履歴を保持することです。 図形が作成されるたびに、 *Azureservice* クラスで *図形の履歴リスト* が更新され、 *Azure Storage* に格納されます。 アプリケーションの起動時に、 *Azure Storage* に格納されているファイルが見つかった場合は、 *図形の履歴リスト* が取得され、再生されます。これには、生成された図形がストレージからのものであるか、新しいものであるかを示す **3d テキスト** オブジェクトがあります。

このクラスを作成するには:

1.  前に作成した **Scripts** フォルダーにアクセスします。

2.  フォルダー内を右クリックし、[C# スクリプトの **作成** ] をクリック  >  **C# Script** します。 スクリプト *図形ファクトリ* を呼び出します。

3.  新しい [ *図形ファクトリ* ] スクリプトをダブルクリックして、 *Visual Studio* で開きます。

4.  *図形ファクトリ* クラスに次の名前空間が含まれていることを確認します。

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  次に示す変数を [ *図形ファクトリ* ] クラスに追加し、 *Start ()* 関数と [起動前 *(* )] 関数を次の関数に置き換えます。

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  *CreateShape ()* メソッドは、指定された *整数* パラメーターに基づいて、プリミティブ形状を生成します。 ブール型パラメーターを使用して、現在作成されている図形がストレージからのものであるか、または新しいものであるかを指定します。 次のコードを、前のメソッドの下にある *図形ファクトリ* クラスに配置します。

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  Unity に戻る前に、変更内容を Visual Studio に保存してください。

8.  Unity エディターに戻り、[ **スクリプト** ] フォルダーの [ *図形ファクトリ* ] クラスをクリックして、[ *階層] パネル* の [ **メインカメラ** ] オブジェクトにドラッグします。

9. メインカメラを選択すると、[ *図形ファクトリ* スクリプトコンポーネントに *生成ポイント* 参照がありません。 この問題を解決するには、 **ShapeSpawnPoint** オブジェクトを [ *階層] パネル* から [ **生成ポイント** 参照] ターゲットにドラッグします。

    ![図形ファクトリ参照ターゲットの設定](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a>第9章-宝石クラスを作成する

作成する必要がある最後のスクリプトは、 *宝石* クラスです。

このクラスは、ユーザーが参照しているオブジェクトを検出するために、メインカメラから投影される **Raycast** を作成します。 この場合、Raycast は、ユーザーがシーン内の **GazeButton** オブジェクトを調べて動作をトリガーするかどうかを識別する必要があります。

このクラスを作成するには:

1.  前に作成した **Scripts** フォルダーにアクセスします。

2.  [プロジェクト] パネル内を右クリック **Create** し、[  >  **C# スクリプト** の作成] をクリックします。 スクリプトを *見つめ* て呼び出します。

3.  新しい *宝石* のスクリプトをダブルクリックして、 *Visual Studio で開きます。*

4.  スクリプトの先頭に次の名前空間が含まれていることを確認します。

    ```csharp
        using UnityEngine;
    ```

5.  次に、次の変数を、 *宝石* クラス内に追加します。

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> これらの変数のいくつかは、 *エディター* で編集できます。

6.  起動可能な *()* メソッドと *Start ()* メソッドのコードを追加する必要があります。

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  次のコードを追加します。このコードは、start に cursor オブジェクトを作成し、 *Update ()* メソッドを実行します。このメソッドは、Raycast メソッドを実行します。このメソッドは、GazeEnabled ブール値が切り替えられる場所になります。

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. 次に、 *UpdateRaycast ()* メソッドを追加します。これにより、Raycast が射影され、ヒットターゲットが検出されます。

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

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

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. 最後に、 *ResetFocusedObject ()* メソッドを追加します。これにより、新しい図形を作成しているかどうかを示す、GazeButton オブジェクトの現在の色が切り替わります。

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  Unity に戻る前に、変更を Visual Studio に保存します。

11.  [スクリプト] フォルダーから、[ *階層] パネル* の [ **メインカメラ** ] オブジェクトに、 *見つめ* クラスをクリックしてドラッグします。

## <a name="chapter-10---completing-the-azureservices-class"></a>第10章-AzureServices クラスの完成

他のスクリプトが配置されたので、 *Azureservices* クラスを *完了* できるようになりました。 これは、次の方法で実現されます。

1.  *CreateCloudIdentityAsync ()* という名前の新しいメソッドを追加して、Azure との通信に必要な認証変数を設定します。

    > また、このメソッドは、シェイプリストを含む以前に格納されたファイルの存在を確認します。
    >
    > **ファイルが見つかった場合** は、 **Azure Storage ファイル** に格納されている図形のパターンに従って、ユーザーが *宝石* を無効にし、図形の作成をトリガーします。 **テキストメッシュ** によって ' Storage ' または ' New ' と表示されるのは、図形の原点によって異なります。
    >
    > **ファイルが見つからない場合** は、ユーザーがシーン内の **GazeButton** オブジェクトを見ているときに図形を作成できるよう *にします* 。

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  次のコードスニペットは、 *Start ()* メソッド内からのものです。 *CreateCloudIdentityAsync ()* メソッドに対して呼び出しが行われます。 次のようにして、現在の *Start ()* メソッドを自由にコピーしてください。

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  *CallAzureFunctionForNextShape ()* メソッドのコードを入力します。 以前に作成した *Azure Function App* を使用して、図形のインデックスを要求します。 新しい図形を受け取ると、このメソッドは図形をシェイプトゥイーン *ファクトリ* クラスに送信して、シーンに新しい図形を作成します。 次のコードを使用して、 *CallAzureFunctionForNextShape ()* の本文を完成させます。

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  図形の履歴リストに格納されている整数を連結して、 *Azure Storage ファイル* に保存することにより、文字列を作成するメソッドを追加します。

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  *Azure Storage ファイル* にあるファイルに格納されているテキストを取得し、それをリストに *逆シリアル* 化するメソッドを追加します。

6.  このプロセスが完了すると、メソッドは、ユーザーがシーンに図形を追加できるように、宝石を再び有効にします。

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  Unity に戻る前に、変更を Visual Studio に保存します。

## <a name="chapter-11---build-the-uwp-solution"></a>第11章-UWP ソリューションのビルド

ビルドプロセスを開始するには:

1.  ファイルの **File**  >  **ビルド設定** にアクセスします。

    ![アプリをビルドする](images/AzureLabs-Lab5-54.png)

2.  [ **ビルド** ] をクリックします。 Unity は *エクスプローラー* ウィンドウを起動します。このウィンドウでは、アプリを作成するフォルダーを作成して選択する必要があります。 ここでそのフォルダーを作成し、「 *App* 」という名前を指定します。 次に、 *アプリ* フォルダーを選択し、 **[フォルダーの選択]** をクリックします。

3.  Unity は、 *アプリ* フォルダーへのプロジェクトのビルドを開始します。

4.  Unity のビルドが完了すると (時間がかかる場合があります)、ビルドの場所で *ファイルエクスプローラー* ウィンドウを開きます (ウィンドウの上に常に表示されるとは限りませんが、新しいウィンドウが追加されたことが通知されます)。

## <a name="chapter-12---deploying-your-application"></a>第12章-アプリケーションのデプロイ

アプリケーションをデプロイするには:

1.  [最後の章](#chapter-11---build-the-uwp-solution)で作成した *アプリ* フォルダーに移動します。 アプリ名を含むファイルが表示されます。この拡張子は ".sln" で、ダブルクリックして *Visual Studio* 内で開く必要があります。

2.  **ソリューションプラットフォーム** で、[ **X86, ローカルコンピューター** ] を選択します。

3.  **ソリューション構成** で、[ **デバッグ** ] を選択します。

    > Microsoft HoloLens の場合、これを *リモートコンピューター* に設定する方が簡単な場合があります。これにより、コンピューターにテザリングさされることはありません。 ただし、次の手順も実行する必要があります。
    > - HoloLens の **IP アドレス** を確認します。これは、[ **設定**  >  ] [ **ネットワーク & [インターネット**  >  **wi-fi**  >  **詳細オプション]** にあります。 IPv4 は使用するアドレスです。 
    > - **開発者モード** が **オンに** なっていることを確認します。「 **設定** の更新」で、  >  開発者向けの **セキュリティ & セキュリティ** が見つかりました  >  **For developers** 。

    ![ソリューションの配置](images/AzureLabs-Lab5-55.png)

4.  [ **ビルド** ] メニューの [ソリューションの **配置** ] をクリックして、アプリケーションをコンピューターにサイドロードします。

5.  インストールされているアプリの一覧にアプリが表示され、起動してテストできる状態になります。

## <a name="your-finished-azure-functions-and-storage-application"></a>完成した Azure Functions およびストレージアプリケーション

これで、Azure Functions と Azure Storage の両方のサービスを活用する mixed reality アプリが作成されました。 アプリは、格納されているデータを描画し、そのデータに基づいてアクションを提供できます。

![最終製品-終了](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a>ボーナス演習

### <a name="exercise-1"></a>演習1

オブジェクトが作成されたポイントを生成する2番目の生成ポイントとレコードを作成します。 データファイルを読み込むときに、最初に作成された場所から生成された図形を再生します。

### <a name="exercise-2"></a>演習2

毎回アプリケーションを再起動するのではなく、アプリを再起動する方法を作成します。 **読み込みシーン** は、開始するのに適しています。 その後、 *Azure Storage* で格納されている一覧をクリアする方法を作成して、アプリから簡単にリセットできるようにします。 
