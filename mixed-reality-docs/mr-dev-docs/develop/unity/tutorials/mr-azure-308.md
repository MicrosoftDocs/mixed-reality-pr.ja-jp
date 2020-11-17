---
title: MR と Azure 308 - クロスデバイス通知
description: このコースでは、Azure Notification Hubs、Azure Functions、および Azure Storage テーブルを mixed reality アプリケーション内に実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, チュートリアル, api, 通知, 関数, テーブル, 通知ハブ, hololens, イマーシブ, vr, Windows 10, Visual Studio
ms.openlocfilehash: 4b71968eb546cc5d7a5cd767f2ecafae102c763c
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679541"
---
# <a name="mr-and-azure-308-cross-device-notifications"></a>MR と Azure 308:クロスデバイス通知

<br>

>[!NOTE]
>Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。  そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。  これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。  これらは、サポートされているデバイス上で継続して動作するように、保守されます。 今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。  この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。

<br>

![最終製品-開始](images/AzureLabs-Lab8-00.png)

このコースでは、Azure Notification Hubs、Azure テーブル、および Azure Functions を使用して、Notification Hubs 機能を mixed reality アプリケーションに追加する方法について説明します。

**Azure Notification Hubs** は Microsoft のサービスであり、開発者は、クラウド内のすべてのプラットフォームにおいて、対象となるパーソナライズされたプッシュ通知を任意のプラットフォームに送信できます。 これにより、開発者はシナリオに応じて、エンドユーザーと通信したり、さまざまなアプリケーション間で通信したりできるようになります。 詳細については、 **Azure Notification Hubs** の [ページ](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview)を参照してください。

**Azure Functions** は Microsoft のサービスであり、開発者は Azure で小さなコードである "Functions" を実行できます。 これにより、ローカルアプリケーションではなく、クラウドに作業を委任することができます。これには多くのメリットがあります。 **Azure Functions** は、C \# 、F \# 、Node.js、Java、PHP など、いくつかの開発言語をサポートしています。 詳細については、 **Azure Functions** の [ページ](https://docs.microsoft.com/azure/azure-functions/functions-overview)を参照してください。

**Azure テーブル** は Microsoft のクラウドサービスであり、開発者は構造化されていない SQL データをクラウドに保存できるため、どこからでも簡単にアクセスできます。 このサービスでは、必要に応じてテーブルを進化させることができるため、スキーマなしの設計が非常に優れているため、非常に柔軟性があります。 詳細については、 **Azure のテーブル** に関する [ページ](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)を参照してください。

このコースを完了すると、現実のイマーシブヘッドセットアプリケーションと、次のようなデスクトップ PC アプリケーションを使用できるようになります。

1. デスクトップ PC アプリを使用すると、ユーザーはマウスを使用して、2D 空間 (X および Y) 内のオブジェクトを移動できます。

2. PC アプリ内のオブジェクトの移動は、JSON を使用してクラウドに送信されます。 JSON は、オブジェクト ID、型、および変換情報 (X および Y 座標) を含む文字列の形式になります。 

3. デスクトップアプリと同一のシーンを持つ mixed reality アプリは、Notification Hubs サービス (デスクトップ PC アプリによって更新されたばかり) から、オブジェクトの移動に関する通知を受け取ります。 

4. オブジェクト ID、種類、および変換情報が含まれる通知を受け取ると、mixed reality アプリによって、受信した情報が独自のシーンに適用されます。

アプリケーションでは、結果をデザインと統合する方法については、お客様のニーズに合わせてください。 このコースは、Azure サービスを Unity プロジェクトと統合する方法を説明することを目的としています。 このコースで得られた知識を使用して、mixed reality アプリケーションを強化することができます。 このコースは自己完結型のチュートリアルであり、他の Mixed Reality ラボに直接は関与しません。

## <a name="device-support"></a>デバイス サポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="../../../hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 308:クロスデバイス通知</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> このコースでは主に Windows Mixed Reality イマーシブ (VR) ヘッドセットに焦点を当てていますが、このコースで学習した内容を Microsoft HoloLens に適用することもできます。 このコースに従うと、HoloLens をサポートするために必要となる可能性のある変更に関する注意事項が表示されます。 HoloLens を使用する場合、音声キャプチャ中にエコーが発生することがあります。

## <a name="prerequisites"></a>必須コンポーネント

> [!NOTE]
> このチュートリアルは、Unity と C# の基本的な経験がある開発者向けに設計されています。 また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証されたものを表します (2018 年5月)。 「 [ツールのインストール](../../install-the-tools.md) 」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に記載されているものよりも新しいソフトウェアで見つかったものと完全に一致するとは限りません。

このコースでは、次のハードウェアとソフトウェアをお勧めします。

- 開発用 PC で、 [Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) (VR) ヘッドセット開発と互換性があります。
- [開発者モードが有効になっている Windows 10 の作成者の更新プログラム (またはそれ以降)](../../install-the-tools.md#installation-checklist)
- [最新の Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- [Windows Mixed Reality イマーシブ (VR) ヘッドセット](../../../discover/immersive-headset-hardware-details.md)または開発者モードを有効にした[Microsoft HoloLens](../../../hololens-hardware-details.md)
- Azure セットアップのインターネットアクセスと Notification Hubs へのアクセス

## <a name="before-you-start"></a>開始する前に

- このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。
- Microsoft 開発者ポータルとアプリケーション登録ポータルの所有者である必要があります。そうしないと、 [第2章](#chapter-2---retrieve-your-new-apps-credentials)でアプリにアクセスするためのアクセス許可が付与されません。

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a>章 1-Microsoft 開発者ポータルでアプリケーションを作成する

**Azure Notification Hubs** サービスを使用するには、アプリケーションを登録する必要があるため、Microsoft 開発者ポータルでアプリケーションを作成する必要があります。これにより、アプリケーションは通知を送受信できるようになります。

1.  [Microsoft 開発者ポータル](https://developer.microsoft.com/dashboard)にログインします。

    > Microsoft アカウントにログインする必要があります。

2.  ダッシュボードで、[ **新しいアプリの作成**] をクリックします。

    ![アプリを作成する](images/AzureLabs-Lab8-01.png)

3.  ポップアップが表示され、新しいアプリの名前を予約する必要があります。 テキストボックスに、適切な名前を挿入します。選択した名前が使用可能な場合は、テキストボックスの右側にティックが表示されます。 使用可能な名前が挿入されたら、ポップアップの下左側にある [ **製品名の予約** ] ボタンをクリックします。

    ![名前を反転する](images/AzureLabs-Lab8-02.png)

4.  これでアプリが作成されたので、次の章に進むことができます。

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a>Chapter 2-新しいアプリの資格情報を取得する

新しいアプリが一覧表示されるアプリケーション登録ポータルにログインし、 **Azure Portal** 内で **Notification Hubs サービス** をセットアップするために使用される資格情報を取得します。

1.  [アプリケーション登録ポータル](https://apps.dev.microsoft.com)に移動します。

    ![アプリケーション登録ポータル](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > ログインするには、Microsoft アカウントを使用する必要があります。  
    > これは、Windows ストア開発者ポータルを使用して、前の [章](#chapter-1---create-an-application-on-the-microsoft-developer-portal)で使用した Microsoft アカウントである **必要があり** ます。

2.  アプリは [ **マイアプリケーション** ] セクションに表示されます。 見つかったら、それをクリックすると、アプリ名と **登録** を含む新しいページが表示されます。

    ![新しく登録されたアプリ](images/AzureLabs-Lab8-04.png)

3.  登録ページを下にスクロールして、 **アプリケーションのシークレット** セクションとアプリの **パッケージ SID** を探します。 次の章の **Azure Notification Hubs サービス** の設定で使用するために両方をコピーします。

    ![アプリケーションシークレット](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a>章 3-Azure Portal のセットアップ: Notification Hubs サービスの作成

アプリの資格情報を取得したら、azure ポータルに移動する必要があります。ここでは、Azure Notification Hubs サービスを作成します。

1.  [Azure Portal](https://portal.azure.com) にログインします。

    > [!NOTE] 
    > まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。 このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。

2.  ログインしたら、左上隅にある [ **新規** ] をクリックし、[ **Notification Hub**] を検索して、[**_Enter_* _] をクリックします。

    ![notification hub の検索](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > 新しいポータルで、 _*_New_*_ という単語が _ * [リソースの作成] * * に置き換えられています。

3.  新しいページには、 *Notification Hubs* サービスの説明が表示されます。 このプロンプトの左下にある [ **作成** ] ボタンを選択して、このサービスとの関連付けを作成します。

    ![notification hub インスタンスの作成](images/AzureLabs-Lab8-07.png)

4.  [**_作成_* _:

    1.  このサービスインスタンスに必要な名前を挿入します。

    2.  このアプリに関連付けることができる _ *名前空間** を指定します。

    3.  場所を選択し **ます。**

    4.  リソースグループを選択するか、新しい **リソースグループ** を作成します。 リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。 1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのラボなど) を共通のリソースグループに保持することをお勧めします。

        > Azure リソースグループの詳細については、 [リソースグループの管理方法に関するリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)を参照してください。 

    5.  適切な **サブスクリプション** を選択します。

    6.  また、このサービスに適用されている使用条件を理解していることを確認する必要があります。

    7. **[作成]** を選択します。

        ![サービスの詳細を入力](images/AzureLabs-Lab8-08.png)

5.  [ **作成**] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。

6.  サービスインスタンスが作成されると、ポータルに通知が表示されます。

    ![通知 (notification)](images/AzureLabs-Lab8-09.png)

7.  通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。 新しい **Notification Hub** サービスインスタンスが表示されます。

    ![リソースにアクセス](images/AzureLabs-Lab8-10.png)
    
8.  ページの中央にある [概要] ページで、[ **Windows (WNS)** ] をクリックします。 右側のパネルが変更され、以前に設定したアプリから、 **パッケージ SID** と **セキュリティキー** を必要とする2つのテキストフィールドが表示されるようになります。

    ![新しく作成されたハブサービス](images/AzureLabs-Lab8-11.png)

9. 詳細を正しいフィールドにコピーしたら、[ **保存**] をクリックすると、通知ハブが正常に更新されたときに通知が表示されます。

    ![セキュリティの詳細をコピーする](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a>第4章-Azure Portal のセットアップ: create Table Service

Notification Hubs サービスインスタンスを作成したら、Azure Portal に戻ります。ここでは、ストレージリソースを作成して Azure Tables Service を作成します。

1.  まだサインインしていない場合は、 [Azure Portal](https://portal.azure.com)にログインします。

2.  ログインしたら、左上隅にある [ **新規** ] をクリックし、[ **ストレージアカウント**] を検索して、 **Enter キー** を押します。

    > [!NOTE] 
    > 新しいポータルでは、New _ という語が **_New_ _ リソースの作成に *置き換えられている可能性があり*** ます。

3.  一覧から [ **ストレージアカウント-blob、file、table、queue** ] を選択します。

    ![ストレージアカウントの検索](images/AzureLabs-Lab8-13.png)

4.  新しいページには、 **ストレージアカウント** サービスの説明が表示されます。 このプロンプトの左下にある [ **作成** ] ボタンを選択して、このサービスのインスタンスを作成します。

    ![ストレージインスタンスの作成](images/AzureLabs-Lab8-14.png)

5.  [ **作成**] をクリックすると、パネルが表示されます。

    1. このサービスインスタンスに必要な **名前** を挿入します (すべて小文字にする必要があります)。

    2. [ **デプロイモデル**] で、[ **リソースマネージャー**] をクリックします。

    3.  [ **アカウントの種類**] で、ドロップダウンメニューを使用して、[ **ストレージ (汎用 v1)**] を選択します。

    4. 適切な **場所** を選択します。
    
    5.  [ **レプリケーション** ] ドロップダウンメニューで、[ **読み取りアクセス-geo 冗長ストレージ (RA-GRS)**] を選択します。

    6.  [ **パフォーマンス**] で [ **標準**] をクリックします。

    7.  [ **安全な転送が必要** ] セクションで、[ **無効**] を選択します。

    8.  [ **サブスクリプション** ] ドロップダウンメニューから、適切なサブスクリプションを選択します。

    9.  リソースグループを選択するか、新しい **リソースグループ** を作成します。 リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。 1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのラボなど) を共通のリソースグループに保持することをお勧めします。

        > Azure リソースグループの詳細については、 [リソースグループの管理方法に関するリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)を参照してください。

    10. このオプションが選択されている場合は、[ **仮想ネットワーク** ] を [無効] のまま **に** します。

    11. **[作成]** をクリックします。

        ![ストレージの詳細の入力](images/AzureLabs-Lab8-15.png)

6.  [ **作成**] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。

7.  サービスインスタンスが作成されると、ポータルに通知が表示されます。 通知をクリックして、新しいサービスインスタンスを探索します。

    ![新しいストレージ通知](images/AzureLabs-Lab8-16.png)

8.  通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。 新しいストレージサービスインスタンスの概要ページが表示されます。

    ![リソースにアクセス](images/AzureLabs-Lab8-17.PNG)

9. [概要] ページで、右側にある [ **テーブル**] をクリックします。
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. 右側のパネルが変化し、 **Table service** 情報が表示されます。新しいテーブルを追加する必要があります。 これを行うには、左上隅にある [ **+** **テーブル** ] ボタンをクリックします。

    ![テーブルを開く](images/AzureLabs-Lab8-19.png)

11. 新しいページが表示されます。ここには、 **テーブル名** を入力する必要があります。 これは、後の章でアプリケーション内のデータを参照するために使用する名前です。 適切な名前を挿入し、[ **OK]** をクリックします。

    ![新しいテーブルの作成](images/AzureLabs-Lab8-20.png)    

12. 新しいテーブルが作成されると、[ **Table service** ] ページ (下部) に表示されるようになります。

    ![新しいテーブルが作成されました](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a>第5章-Visual Studio での Azure テーブルの完成

**Table service** ストレージアカウントがセットアップされたので、それにデータを追加します。これは、情報の格納と取得に使用されます。 テーブルの編集は、 **Visual Studio** を使用して行うことができます。

1.  **Visual Studio** を開きます。

2.  メニューの [Cloud Explorer の **表示**] をクリックし  >  **Cloud Explorer** ます。

    ![cloud explorer を開く](images/AzureLabs-Lab8-22.png)

3.  **Cloud Explorer** がドッキングされたアイテムとして開きます (読み込みに時間がかかる場合があります)。

    > [!NOTE] 
    > *ストレージアカウント* の作成に使用したサブスクリプションが表示されない場合は、次のことを確認してください。 
    > - Azure Portal で使用したものと同じアカウントにログインします。
    > - [アカウント管理] ページからサブスクリプションを選択しました (アカウントの設定からフィルターを適用する必要がある場合があります)。  
    >
    >   ![サブスクリプションの検索](images/AzureLabs-Lab8-22-5.png)

4.  Azure cloud services が表示されます。 **ストレージアカウント** を検索し、左側の矢印をクリックしてアカウントを展開します。

    ![ストレージアカウントを開く](images/AzureLabs-Lab8-23.png)

5.  展開されると、新しく作成された **ストレージアカウント** を使用できるようになります。 ストレージの左側にある矢印をクリックし、展開された後、[ **テーブル** ] を見つけて、その横にある矢印をクリックし、最後の章で作成した **テーブル** を表示します。 **テーブル** をダブルクリックします。

    ![シーンオブジェクトテーブルを開く](images/AzureLabs-Lab8-24.png)

6.  テーブルが Visual Studio ウィンドウの中央に開きます。 [テーブル] アイコンをクリックし **+** ます。

    ![新しいテーブルの追加](images/AzureLabs-Lab8-25.png)

7.  *エンティティの追加* を求めるウィンドウが表示されます。 合計3つのエンティティを作成し、それぞれに複数のプロパティを付けます。 *Partitionkey* と *RowKey* は既に提供されています。これは、テーブルがデータを検索するために使用されるためです。 

    ![パーティションキーと行キー](images/AzureLabs-Lab8-26.png)

8. **Partitionkey** と **RowKey** の *値* を次のように更新します (追加する行プロパティごとにこの操作を行ってください。ただし、RowKey は毎回インクリメントします)。

    ![正しい値の追加](images/AzureLabs-Lab8-26-5.png)

9.  [ **プロパティの追加** ] をクリックして、余分な行のデータを追加します。 最初の空のテーブルを次の表のようにします。

10. 完了したら [ **OK]** をクリックします。

    ![完了したら [ok] をクリックします。](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > **X**、 **Y**、 **Z** の各エントリの **種類** を **Double** に変更したことを確認します。 

11. テーブルにデータ行があることがわかります。 **+**(プラス) アイコンをもう一度クリックして、別のエンティティを追加します。

    ![最初の行](images/AzureLabs-Lab8-27-5.png)

12. 追加のプロパティを作成し、次に示すように新しいエンティティの値を設定します。

    ![キューブの追加](images/AzureLabs-Lab8-28.png)

13. 別のエンティティを追加するには、最後の手順を繰り返します。 このエンティティの値を次に示すように設定します。

    ![円柱の追加](images/AzureLabs-Lab8-29.png)

14. テーブルは次のようになります。

    ![テーブルの完了](images/AzureLabs-Lab8-30.png)

15. これで、この章は終了です。 必ず保存してください。

## <a name="chapter-6---create-an-azure-function-app"></a>第6章-Azure Function App の作成

Azure Function App を作成します。これは、デスクトップアプリケーションによって呼び出され、 **テーブル** サービスを更新し、通知 **ハブ** を介して通知を送信します。

まず、必要なライブラリを Azure 関数で読み込むことができるファイルを作成する必要があります。

1.  **メモ帳** を開きます (Windows キーを押し、メモ帳を入力します)。

    ![メモ帳を開く](images/AzureLabs-Lab8-31.png)

2.  メモ帳を開いた状態で、次の JSON 構造を挿入します。 これが完了したら、 **project.js** としてデスクトップに保存します。 名前が .txt ファイル拡張子 **を持たない** ことを確認することが重要です。 このファイルは、関数が使用するライブラリを定義します。 NuGet を使用している場合は、見慣れたものになります。

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  [Azure Portal](https://portal.azure.com) にログインします。

4.  ログインしたら、左上隅にある [ **新規** ] をクリックし、 **Function App** を検索して、 **enter キーを** 押します。

    ![function app の検索](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > 新しいポータルで、 **New** という単語が **リソースの作成** に置き換えられました。

5.  新しいページには、 **Function App** サービスの説明が表示されます。 このプロンプトの左下にある [ **作成** ] ボタンを選択して、このサービスとの関連付けを作成します。

    ![function app インスタンス](images/AzureLabs-Lab8-33.png)

6.  [ **作成**] をクリックしたら、次のように入力します。

    1. [ **アプリ名**] に、このサービスインスタンスに必要な名前を挿入します。

    2. **サブスクリプション** を選択します。

    3. 適切な価格レベルを選択してください。 **Function App サービス** を初めて作成する場合は、free レベルをご利用いただけます。

    4. リソースグループを選択するか、新しい **リソースグループ** を作成します。 リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。 1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのラボなど) を共通のリソースグループに保持することをお勧めします。

        > Azure リソースグループの詳細については、 [リソースグループの管理方法に関するリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)を参照してください。

    5. **OS** の場合は、[Windows] をクリックします。これは目的のプラットフォームです。

    6. **ホスティングプラン** を選択します (このチュートリアルでは、**従量課金プラン** を使用しています。

    7. **場所** を選択します **(前の手順で作成したストレージと同じ場所を選択します)。**

    8. [ **ストレージ** ] セクションでは、 **前の手順で作成したストレージサービスを選択する必要があり** ます。

    9. このアプリで *Application Insights* は必要ありませ **ん。そのままにして** おいてもかまいません。

    10. **[作成]** をクリックします。

        ![新しいインスタンスの作成](images/AzureLabs-Lab8-34.png)

7.  [ **作成** ] をクリックすると、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。

8.  サービスインスタンスが作成されると、ポータルに通知が表示されます。

    ![新しい通知](images/AzureLabs-Lab8-35.png)

9.  通知をクリックして、新しいサービスインスタンスを探索します。

10. 通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。 

    ![リソースにアクセス](images/AzureLabs-Lab8-36.png)

11. [ **+** *関数*] の横にある (プラス記号) アイコンをクリックして、 *新しいを作成* します。

    ![新しい関数の追加](images/AzureLabs-Lab8-37.png)

12. 中央のパネル内に [ **関数** の作成] ウィンドウが表示されます。 パネルの上半分にある情報を無視し、[カスタム関数] をクリックします。 [ **カスタム関数**] は、下部 (青い領域) の近くにあります。

    ![カスタム関数](images/AzureLabs-Lab8-38.png)

13. ウィンドウ内の新しいページには、さまざまな関数の種類が表示されます。 下にスクロールして紫色の種類を表示し、[ **HTTP PUT** 要素] をクリックします。

    ![http put リンク](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > ページの下にスクロールする必要がある場合があります (Azure Portal の更新が実行されている場合、このイメージは正確には見えない可能性があります)。ただし、 *HTTP PUT* という要素を探している場合もあります。

14. [ **HTTP PUT** ] ウィンドウが表示されます。ここで、関数を構成する必要があります (イメージについては以下を参照してください)。

    1.  [ **言語] で** 、ドロップダウンメニューを使用して [C] を選択し \# ます。

    2.  **[名前]** には、適切な名前を入力します。

    3.  [ **認証レベル** ] ドロップダウンメニューで、[ **関数**] を選択します。

    4.  [ **テーブル名** ] セクションでは、以前に **テーブル** サービスの作成に使用したのと同じ名前を使用する必要があります (同じ大文字小文字を含む)。

    5.  [ **ストレージアカウント接続** ] セクションで、ドロップダウンメニューを使用して、そこからストレージアカウントを選択します。 表示されていない場合は、セクションタイトルと共に **新しい** ハイパーリンクをクリックして、ストレージアカウントが表示される別のパネルを表示します。

        ![新しいストレージ](images/AzureLabs-Lab8-40.png)

15. [ **作成** ] をクリックすると、設定が正常に更新されたことを示す通知が表示されます。

    ![関数の作成](images/AzureLabs-Lab8-41.png)

16. [ **作成**] をクリックすると、関数エディターにリダイレクトされます。

    ![関数コードの更新](images/AzureLabs-Lab8-42.png)

17. 関数エディターに次のコードを挿入します (関数内のコードを置き換えます)。

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > 関数は、含まれているライブラリを使用して、Unity シーン内で移動されたオブジェクトの名前と場所を受け取ります ( **Unityのオブジェクト** と呼ばれる C# オブジェクトとして)。 このオブジェクトは、作成されたテーブル内のオブジェクトパラメーターを更新するために使用されます。 次に、この関数は、作成された通知ハブサービスを呼び出します。これにより、すべてのサブスクライブ済みアプリケーションが通知されます。

18. コードを配置したら、[ **保存**] をクリックします。

19. 次に、 **\<** ページの右側にある (矢印) アイコンをクリックします。

    ![アップロードパネルを開く](images/AzureLabs-Lab8-43.png)

20. パネルが右側からスライドします。 そのパネルで [ **アップロード**] をクリックすると、ファイルブラウザーが表示されます。

21. に移動して、**メモ帳** で作成したファイルの **project.js** をクリックし、[**開く**] ボタンをクリックします。 このファイルは、関数が使用するライブラリを定義します。

    ![json のアップロード](images/AzureLabs-Lab8-44.png)

22. ファイルがアップロードされると、右側のパネルに表示されます。 このボタンをクリックすると、 **関数** エディター内で開かれます。 この値は、次のイメージと **まったく** 同じである必要があります (手順23以降)。

23. 次に、左側のパネルの [ **Functions**] の下にある [ **統合** ] リンクをクリックします。

    ![integration 関数](images/AzureLabs-Lab8-45.png)

24. 次のページの右上隅にある [ **詳細エディター** ] (次の手順を参照) をクリックします。

    ![詳細エディターの起動](images/AzureLabs-Lab8-46.png)

25. ファイル **のfunction.js** が中央のパネルに開き、次のコードスニペットで置き換える必要があります。 これにより、ビルドする関数と、関数に渡されるパラメーターが定義されます。

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. エディターは次の図のようになります。

    ![標準エディターに戻る](images/AzureLabs-Lab8-47.png)

27. 先ほど挿入した入力パラメーターがテーブルとストレージの詳細と一致しないため、情報を更新する必要があることがわかります。 次に説明するように、ここでは **この操作** を行わないでください。 ページの右上隅にある **標準のエディター** のリンクをクリックするだけで、戻ることができます。

28. **標準エディター** に戻り、[**入力**] の下にある [ **Azure Table Storage (テーブル)**] をクリックします。 
    
    ![テーブルの入力](images/AzureLabs-Lab8-47-5.png)

29. 次の手順に従って、異なる可能性があるため、情報に対して次の一致がある **ことを確認** します。

    1.  **テーブル名**: Azure Storage テーブルサービス内で作成したテーブルの名前。

    2.  [**ストレージアカウント接続]:** ドロップダウンメニューと共に表示される [**新規**] をクリックすると、ウィンドウの右側にパネルが表示されます。

        ![新しいストレージ](images/AzureLabs-Lab8-48.png)

        1.  以前に関数アプリをホストするために作成した **ストレージアカウント** を選択し **ます。**

        2. **ストレージアカウント** の接続値が作成されていることがわかります。

        3. 完了したら、必ず [ **保存** してください。

    3.  **入力** ページが次のようになり **、情報が** 表示されます。

        ![入力の完了](images/AzureLabs-Lab8-49.png)

30. 次に、[**出力**] の [ **Azure notification Hub (通知)** ] をクリックします。 次のものが異なる可能性があるため、以下 **の内容が情報と** 一致していることを確認してください (次の手順の下に画像があります)。

    1.  [ **Notification Hub 名**]: これは、前に作成した **notification hub** サービスインスタンスの名前です。

    2.  **Notification Hubs 名前空間接続**]: ドロップダウンメニューと共に表示される [ **新規**] をクリックします。

        ![出力の確認](images/AzureLabs-Lab8-50.png)

    3. **接続** ポップアップが表示されます (下図を参照)。ここでは、以前に設定した **通知ハブ** の **名前空間** を選択する必要があります。

    4. 中央のドロップダウンメニューから **通知ハブ** 名を選択します。

    5.  [ **ポリシー** ] ドロップダウンメニューを **Defaultfullsharedaccesssignature** に設定します。

    6. 戻るには、[ **選択** ] ボタンをクリックします。

        ![出力の更新](images/AzureLabs-Lab8-51.png)

31.  **出力** ページは次のようになりますが、**情報が代わりに使用** されます。 必ず [ **保存** してください。

> [!WARNING]
> *通知ハブ名を直接編集しない* でください (これは、前の手順に正しく従っていれば、 **詳細エディター** を使用して行う必要があります。

![出力の完了](images/AzureLabs-Lab8-50.png)

32. この時点で、関数が動作していることを確認するために、関数をテストする必要があります。 この操作を行うには、次の手順を実行します。 

    1. 関数のページにもう一度移動します。

        ![出力の完了](images/AzureLabs-Lab8-50-1.png)

    2. 関数のページに戻り、ページの右端にある [ **テスト** ] タブをクリックして、[ *テスト* ] ブレードを開きます。

        ![出力の完了](images/AzureLabs-Lab8-50-2.png)

    3. ブレードの [ **要求本文** ] ボックスに、次のコードを貼り付けます。

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. テストコードを配置した状態で、右下にある [ **実行** ] ボタンをクリックすると、テストが実行されます。 テストの出力ログは、関数コードの下のコンソール領域に表示されます。

        ![出力の完了](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > 上記のテストが失敗した場合は、上記の手順に厳密に従っていること、特に [ **統合] パネル** 内の設定を確認する必要があります。 

## <a name="chapter-7---set-up-desktop-unity-project"></a>第7章-デスクトップ Unity プロジェクトの設定

> [!IMPORTANT]
> 現在作成中のデスクトップアプリケーションは、Unity エディターでは動作し **ません** 。 これは、Visual Studio (またはデプロイされたアプリケーション) を使用して、アプリケーションのビルド後に、エディターの外部で実行する必要があります。 

次に示すのは、Unity と mixed reality で開発するための一般的な設定であり、そのため、他のプロジェクトに適したテンプレートです。

Mixed reality のイマーシブヘッドセットをセットアップしてテストします。

> [!NOTE] 
> このコースでは、モーションコントローラーは必要 **ありません** 。 イマーシブヘッドセットの設定をサポートする必要がある場合は、 [Windows Mixed Reality のセットアップ方法に関するリンク](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)を参照してください。

1.  **Unity** を開き、[**新規**] をクリックします。

    ![新しい unity プロジェクト](images/AzureLabs-Lab8-52.png)

2.  Unity プロジェクト名を指定する必要があります。 **UnityDesktopNotifHub** を挿入します。 プロジェクトの種類が **3d** に設定されていることを確認します。 場所を適切な **場所** に設定します (ルートディレクトリの方が適していることに注意してください)。 次に、[ **プロジェクトの作成**] をクリックします。

    ![プロジェクトの作成](images/AzureLabs-Lab8-53.png)

3.  Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。 [設定の **編集**] に移動し、  >  **Preferences** 新しいウィンドウで [**外部ツール**] に移動します。 **外部スクリプトエディター** を **Visual Studio 2017** に変更します。 [ **基本設定** ] ウィンドウを閉じます。

    ![外部 VS ツールの設定](images/AzureLabs-Lab8-54.png)

4.  次に、[**ファイル**] [ビルドの設定] に移動して [ユニバーサル Windows プラットフォーム] を選択し、[  >  **Build Settings** **プラットフォームの切り替え**] ボタンをクリックして選択内容を適用します。 **Universal Windows Platform**

    ![プラットフォームの切り替え](images/AzureLabs-Lab8-55.png)

5.  **ファイル** の  >  **ビルド設定** でも、次のことを確認してください。

    1.  **ターゲットデバイス** が **任意のデバイス** に設定されています

        > このアプリケーションはデスクトップ用であるため、**任意のデバイス** にする必要があります

    2.  **ビルドの種類** が **D3D** に設定されています

    3.  **SDK** は最新の **インストール** に設定されています

    4.  **Visual Studio のバージョン** が、**インストールされている最新** バージョンに設定されています

    5.  **ビルドと実行** は **ローカルコンピューター** に設定されています

    6.  ここでは、シーンを保存し、ビルドに追加する価値があります。

        1. これを行うには、[開いている **シーンの追加**] を選択します。 保存ウィンドウが表示されます。

            ![オープンシーンを追加する](images/AzureLabs-Lab8-56.png)

        2. この新しいフォルダーを作成し、今後のシーンに加えて、[ **新しいフォルダー** ] ボタンを選択します。新しいフォルダーを作成するには、名前を「 **シーン**」にします。

            ![新しいシーンフォルダー](images/AzureLabs-Lab8-57.png)

        3. 新しく作成した [ **シーン** ] フォルダーを開き、[ **ファイル名:** テキスト] フィールドに「 **NH \_ Desktop \_ Scene**」と入力し、[ **保存**] を押します。

            ![新しい NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  それ以外の設定は、[ **ビルド設定**] の [既定] のままにしておきます。

6.  同じウィンドウで、[プレーヤーの **設定** ] ボタンをクリックすると、 **インスペクター** が配置されている領域の関連パネルが開きます。

7.  このパネルでは、いくつかの設定を確認する必要があります。

    1.  [ **その他の設定** ] タブで、次のようにします。

        1.  **Scripting Runtime のバージョン** は実験的である必要があります **(.Net 4.6 と同等)**

        2. **バックエンド** は **.net** である必要があります

        3. **API 互換性レベル** は **.net 4.6** である必要があります

            ![4.6 net バージョン](images/AzureLabs-Lab8-59.png)

    2.  [ **発行の設定** ] タブの [ **機能**] で、次の項目を確認します。

        - **InternetClient**

            ![インターネットクライアントを刻む](images/AzureLabs-Lab8-60.png)

8.  **ビルド設定** に戻る *Unity C \# プロジェクト* はグレーで表示されなくなりました。この横にあるチェックボックスをオンにします。

9.  **[ビルド設定]** ウィンドウを閉じます。

10. シーンとプロジェクト **ファイル** の保存  >  **シーン/ファイル**  >  **保存プロジェクト** を保存します。

    > [!IMPORTANT]
    > このプロジェクトの *Unity セットアップ* コンポーネント (デスクトップアプリ) をスキップし、コードに直接進む場合は、 [unitypackage をダウンロード](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage)して、 [**カスタムパッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてから、 [9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)の手順を続行してください。  その場合でも、スクリプトコンポーネントを追加する必要があります。

## <a name="chapter-8---importing-the-dlls-in-unity"></a>章 8-Unity での Dll のインポート

Azure Storage for Unity を使用します (これ自体が .Net SDK for Azure を利用します)。 詳細については [、Unity の Azure Storage に関する](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)次のリンク先を参照してください。

現在、Unity には、インポート後にプラグインを再構成する必要がある既知の問題があります。 バグが解決された後、これらの手順 (このセクションでは 4-7) は不要になりました。

SDK を独自のプロジェクトにインポートするには、GitHub から最新の [**unitypackage**](https://aka.ms/azstorage-unitysdk) をダウンロードしていることを確認します。 次に、以下を実行します。

1.  [**アセット \> インポートパッケージの \> カスタムパッケージ**] メニューオプションを使用して、 **unitypackage** を Unity に追加します。

2.  ポップアップ表示された [ **Unity パッケージのインポート** ] ボックスで、* * [_プラグイン_* ストレージ] * * * の下にあるすべてを選択でき \> ます。  このコースでは不要なため、他のすべてをオフにします。

    ![パッケージへのインポート](images/AzureLabs-Lab8-61.png)

3.  [**_インポート_* _] ボタンをクリックして、プロジェクトに項目を追加します。

4.  プロジェクトビューの [**プラグイン**] にある _ *ストレージ** フォルダーにアクセスし、次のプラグイン *のみ* を選択します。

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

![プラットフォームをすべてオフにする](images/AzureLabs-Lab8-62.png)

5.  *これらの特定のプラグイン* を選択した状態で、任意の **プラットフォーム** を **オフ****にし、** [ **wsaplayer** ]、[**適用**] の順にクリックします。

    ![プラットフォーム dll を適用する](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > これらの特定のプラグインを Unity エディターでのみ使用するようにマークしています。 これは、プロジェクトが Unity からエクスポートされた後に使用される、WSA フォルダー内に同じプラグインの異なるバージョンがあるためです。

6.  [ **ストレージ** プラグイン] フォルダーで、[のみ] を選択します。

    -   Microsoft.Data.Services.Client

        ![dll のプロセスを設定しない](images/AzureLabs-Lab8-64.png)

7.  [**プラットフォームの設定**] の [**処理しない**] チェックボックスをオンにして、[**_適用_*] をクリックします。

    ![処理を適用しない](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > Unity アセンブリ patcher はこのプラグインを処理するのが困難であるため、このプラグインを "処理しない" としてマークしています。 このプラグインは、処理されていなくても動作します。

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a>第9章-Desktop Unity プロジェクトで TableToScene クラスを作成する

ここで、このアプリケーションを実行するコードを含むスクリプトを作成する必要があります。

作成する必要のある最初のスクリプトは、_ * TableToScene * * です。これは次の役割を担います。

-   Azure テーブル内のエンティティを読み取っています。
-   テーブルデータを使用して、生成するオブジェクトとその位置を決定します。

作成する必要がある2番目のスクリプトは **Cloudscene** です。これは次の役割を担います。

-   左クリックイベントを登録して、ユーザーがシーンの周りをドラッグできるようにします。
-   この Unity シーンからオブジェクトデータをシリアル化し、それを Azure Function App に送信します。

このクラスを作成するには:

1.  [プロジェクト] パネルにある [**アセット**] フォルダーを右クリックし、[フォルダーの **作成**] をクリックし  >  **Folder** ます。 フォルダーに **スクリプト** の名前を指定します。

    ![スクリプトフォルダーの作成](images/AzureLabs-Lab8-66.png)

    ![スクリプト作成フォルダー2](images/AzureLabs-Lab8-67.png)

2.  先ほど作成したフォルダーをダブルクリックして開きます。

3.  **Scripts** フォルダー内を右クリックし、[ **Create**  >  **C# スクリプト** の作成] をクリックします。 スクリプト **Tabletoscene** という名前を指定します。

    ![新しい c# スクリプト ](images/AzureLabs-Lab8-68.png)
     ![ tabletoscene の名前変更](images/AzureLabs-Lab8-69.png)

4.  スクリプトをダブルクリックして、Visual Studio 2017 で開きます。

5.  次の名前空間を追加します。

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  クラス内に、次の変数を挿入します。

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > **AccountName** 値を Azure Storage サービス名と **accountKey** 値に置き換え、Azure Storage サービスのキー値を Azure Portal (次の図を参照) に置き換えます。 
    >
    > ![アカウントキーを取得する](images/AzureLabs-Lab8-70.png)

7.  ここで、クラスを初期化する **Start () および起動** 前 **()** の各メソッドを追加します。

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  **Tabletoscene** クラス内で、Azure テーブルから値を取得し、それを使用してシーン内の適切なプリミティブを生成するメソッドを追加します。

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  **Tabletoscene** クラスの外部では、**テーブルエンティティ** をシリアル化および逆シリアル化するためにアプリケーションによって使用されるクラスを定義する必要があります。

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. Unity エディターに戻る前に、必ず **保存** してください。

11. [**階層**] パネルから **メインカメラ** をクリックして、そのプロパティが **インスペクター** に表示されるようにします。

12. **Scripts** フォルダーを開いた状態で、 **tabletoscene** のスクリプトファイルを選択し、**メインカメラ** にドラッグします。 結果は次のようになります。

    ![メインカメラにスクリプトを追加する](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a>Chapter 10-Desktop Unity プロジェクトで CloudScene クラスを作成する

作成する必要がある2番目のスクリプトは **Cloudscene** です。これは次の役割を担います。

-   左クリックイベントを登録して、ユーザーがシーンの周りをドラッグできるようにします。

-   この Unity シーンからオブジェクトデータをシリアル化し、それを Azure Function App に送信します。

2番目のスクリプトを作成するには:

1.  **Scripts** フォルダー内を右クリックし、[**作成**]、[ **C \# スクリプト**] の順にクリックします。 スクリプトに **Cloudscene** という名前を指定します
    
    ![新しい c# スクリプトの ](images/AzureLabs-Lab8-72.png)
     ![ 名前変更 cloudscene](images/AzureLabs-Lab8-73.png)

2.  次の名前空間を追加します。

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  次の変数を挿入します。

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  次の図に示すように、azure Portal の azure Function App サービスで見つかった Azure Function App URL で **azureFunctionEndpoint** 値を置き換えます。

    ![関数の URL の取得](images/AzureLabs-Lab8-74.png)

5.  ここで、クラスを初期化する **Start () および起動** 前 **()** の各メソッドを追加します。

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  **Update ()** メソッド内に次のコードを追加します。このコードは、マウス入力を検出してドラッグします。これにより、シーン内のオブジェクトが移動されます。 オブジェクトをドラッグアンドドロップした場合、オブジェクトの名前と座標がメソッド **UpdateCloudScene ()** に渡されます。このメソッドは azure Function App サービスを呼び出します。これにより、azure テーブルが更新され、通知がトリガーされます。

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  次のように、 **UpdateCloudScene ()** メソッドを追加します。

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  コードを保存して Unity に戻る

9.  **Cloudscene** スクリプトを **メインカメラ** にドラッグします。 

    1. [**階層**] パネルから **メインカメラ** をクリックして、そのプロパティが **インスペクター** に表示されるようにします。 

    2. **Scripts** フォルダーを開いた状態で **cloudscene** スクリプトを選択し、**メインカメラ** にドラッグします。 結果は次のようになります。

        > ![メインカメラにクラウドスクリプトをドラッグする](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a>第11章-UWP へのデスクトッププロジェクトのビルド

このプロジェクトの Unity セクションに必要なすべてが完了しました。

1.  [**ビルドの設定**] ([**ファイル**  >  **ビルドの設定**]) に移動します。

2.  [ **ビルドの設定** ] ウィンドウで、[ **ビルド**] をクリックします。

    ![プロジェクトのビルド](images/AzureLabs-Lab8-76.png)

3.  **ファイルエクスプローラー** ウィンドウがポップアップ表示され、ビルドする場所を入力するように求められます。 (左上隅にある [ **新しいフォルダー** ] をクリックして) 新しいフォルダーを作成し、 **ビルド** という名前を指定します。

    ![ビルド用の新しいフォルダー](images/AzureLabs-Lab8-77.png)

    1.  [新しい **ビルド** ] フォルダーを開き、別のフォルダーを作成し ( **新しいフォルダー** をもう一度使用)、 **NH \_ Desktop \_ App** という名前を指定します。

        ![フォルダー名 NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  **NH \_ デスクトップ \_ アプリ** を選択します。 [ **フォルダーの選択] を** クリックします。 プロジェクトがビルドされるまでに1分ほどかかります。

4.  次のビルドでは、新しいプロジェクトの場所を示す **ファイルエクスプローラー** が表示されます。 ただし、次のいくつかの章では、最初に他の Unity プロジェクトを作成する必要があるため、このファイルを開く必要はありません。


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a>第12章-Mixed Reality Unity プロジェクトの設定

次に示すのは、mixed reality で開発するための一般的な設定です。そのため、他のプロジェクトに適したテンプレートです。

1.  **Unity** を開き、[**新規**] をクリックします。

    ![新しい unity プロジェクト](images/AzureLabs-Lab8-79.png)

2.  ここで、Unity プロジェクト名を入力し、 **UnityMRNotifHub** を挿入する必要があります。 プロジェクトの種類が **3d** に設定されていることを確認します。 場所を適切な **場所** に設定します (ルートディレクトリの方が適していることに注意してください)。 次に、[ **プロジェクトの作成**] をクリックします。

    ![名前 UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。 [設定の **編集**] に移動し、  >  **Preferences** 新しいウィンドウで [**外部ツール**] に移動します。 **外部スクリプトエディター** を **Visual Studio 2017** に変更します。 [ **基本設定** ] ウィンドウを閉じます。

    ![外部エディターを VS に設定する](images/AzureLabs-Lab8-81.png)

4.  次に、[**ファイル**  >  ] [**ビルドの設定**] の順に移動し、[**プラットフォームの切り替え**] ボタンをクリックして、プラットフォームを **ユニバーサル Windows プラットフォーム** に切り替えます。

    ![プラットフォームを UWP に切り替える](images/AzureLabs-Lab8-82.png)

5.  **ファイル**  >  の **ビルド設定** にアクセスして、次のことを確認してください。

    1.  **ターゲットデバイス** が **任意のデバイス** に設定されています

        > Microsoft HoloLens の場合は、 **ターゲットデバイス** を *HoloLens* に設定します。

    2.  **ビルドの種類** が **D3D** に設定されています

    3.  **SDK** は最新の **インストール** に設定されています

    4.  **Visual Studio のバージョン** が、**インストールされている最新** バージョンに設定されています

    5.  **ビルドと実行** は **ローカルコンピューター** に設定されています

    6.  ここでは、シーンを保存し、ビルドに追加する価値があります。

        1. これを行うには、[開いている **シーンの追加**] を選択します。 保存ウィンドウが表示されます。

            ![オープンシーンを追加する](images/AzureLabs-Lab8-83.png)

        2. この新しいフォルダーを作成し、今後のシーンに加えて、[ **新しいフォルダー** ] ボタンを選択します。新しいフォルダーを作成するには、名前を「 **シーン**」にします。

            ![新しいシーンフォルダー](images/AzureLabs-Lab8-84.png)

        3. 新しく作成した [ **シーン** ] フォルダーを開き、[ **ファイル名:** テキスト] フィールドに「 **NH \_ MR \_ シーン**」と入力し、[ **保存**] を押します。

            ![新しいシーン-NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  それ以外の設定は、[ **ビルド設定**] の [既定] のままにしておきます。

6.  同じウィンドウで、[プレーヤーの **設定** ] ボタンをクリックすると、 **インスペクター** が配置されている領域の関連パネルが開きます。    

    ![プレーヤーの設定を開く](images/AzureLabs-Lab8-86.png)

7.  このパネルでは、いくつかの設定を確認する必要があります。

    1.  [ **その他の設定** ] タブで、次のようにします。

        1.  **Scripting Runtime のバージョン** は **実験的** である必要があります (.net 4.6 と同等)
        2.  **スクリプトバックエンド** は **_.net_* _ である必要があります
        3.  _ *API 互換性レベル** は **.net 4.6** である必要があります

            ![api の互換性](images/AzureLabs-Lab8-87.png)

    2.  パネルの下の [ **XR settings** ( **発行の設定**] の下にあります) で、[ **サポートされている仮想現実**] をティックし、 **Windows Mixed reality SDK** が追加されていることを確認します。

        ![xr 設定の更新](images/AzureLabs-Lab8-88.png)        

    3.  [ **発行の設定** ] タブの [ **機能**] で、次のようにします。

        - **InternetClient**           

            ![インターネットクライアントを刻む](images/AzureLabs-Lab8-89.png)

8.  **ビルド設定** に戻ると、 **Unity C# プロジェクト** はグレーで表示されなくなりました。このの横にあるチェックボックスをオンにします。

9.  これらの変更が完了したら、[ビルドの設定] ウィンドウを閉じます。

10. シーンとプロジェクト **ファイル** の保存  >  **シーン/ファイル**  >  **保存プロジェクト** を保存します。

    > [!IMPORTANT]
    > このプロジェクトの *Unity セットアップ* コンポーネント (Mixed reality アプリ) をスキップしてコードに直接進む場合は、 [unitypackage をダウンロード](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage)し、 [**カスタムパッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてから、 [14 章](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project)から続行してください。 その場合でも、スクリプトコンポーネントを追加する必要があります。

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a>第13章: Mixed Reality Unity プロジェクトでの Dll のインポート

Azure Storage for Unity library (.Net SDK for Azure を使用) が使用されます。 [Unity で Azure Storage を使用する方法については、こちらのリンクを](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)参照してください。
現在、Unity には、インポート後にプラグインを再構成する必要がある既知の問題があります。 バグが解決された後、これらの手順 (このセクションでは 4-7) は不要になりました。

SDK を独自のプロジェクトにインポートするには、 [unitypackage](https://aka.ms/azstorage-unitysdk)がダウンロードされていることを確認してください。 次に、以下を実行します。

1.  [**アセット**  >  **インポートパッケージ**  >  **カスタムパッケージ**] メニューオプションを使用して、上記からダウンロードした unitypackage を Unity に追加します。

2.  ポップアップ表示される [ **Unity パッケージのインポート**] ボックスで、[**プラグイン** ストレージ] の下のすべてを選択でき  >  **Storage** ます。

    ![パッケージのインポート](images/AzureLabs-Lab8-90.png)

3.  [ **インポート** ] ボタンをクリックして、プロジェクトに項目を追加します。

4.  プロジェクトビューの [**プラグイン**] の下にある **ストレージ** フォルダーにアクセスし、次のプラグイン *のみ* を選択します。

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

    ![プラグインの選択](images/AzureLabs-Lab8-91.png)

5.  *これらの特定のプラグイン* を選択した状態で、任意の **プラットフォーム** を **オフ****にし、** [ **wsaplayer** ]、[**適用**] の順にクリックします。

    ![プラットフォームの変更の適用](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > これらの特定のプラグインを Unity エディターでのみ使用するようにマークしています。 これは、プロジェクトが Unity からエクスポートされた後に使用される、WSA フォルダー内に同じプラグインの異なるバージョンがあるためです。

6.  [ **ストレージ** プラグイン] フォルダーで、[のみ] を選択します。

    -   Microsoft.Data.Services.Client

        ![データサービスクライアントの選択](images/AzureLabs-Lab8-93.png)

7.  [**プラットフォームの設定**] の [**処理しない**] チェックボックスをオンにし、[**適用**] をクリックします。

    ![処理しない](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > Unity アセンブリ patcher がこのプラグインを処理するのが困難であるため、このプラグインを "処理しない" とマークしています。 プラグインは処理されていなくても機能します。

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a>第14章: mixed reality Unity プロジェクトでの TableToScene クラスの作成

**Tabletoscene** クラスは、「 [9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)」で説明したものと同じです。 「 [9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)」で説明されている手順に従って、Mixed Reality Unity プロジェクトに同じクラスを作成します。

この章を完了すると、両方の **Unity プロジェクト** のメインカメラにこのクラスが設定されます。

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a>第15章: Mixed Reality Unity プロジェクトで NotificationReceiver クラスを作成する

作成する必要がある2番目のスクリプトは **Notificationreceiver** で、次の役割があります。

-   初期化時にアプリを通知ハブに登録しています。
-   通知ハブからの通知をリッスンしています。
-   受信した通知からオブジェクトデータを逆シリアル化します。
-   逆シリアル化されたデータに基づいて、シーン内のオブジェクトを移動します。

**Notificationreceiver** スクリプトを作成するには、次のようにします。

1.  **Scripts** フォルダー内を右クリックし、[**作成**]、[ **C \# スクリプト**] の順にクリックします。 スクリプトに **Notificationreceiver** という名前を指定します。

    ![新しい c# スクリプト名の作成 ](images/AzureLabs-Lab8-95.png)
     ![ notificationreceiver](images/AzureLabs-Lab8-96.png)

2.  スクリプトをダブルクリックして開きます。

3.  次の名前空間を追加します。

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  次の変数を挿入します。

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  **HubName** 値を通知ハブのサービス名に置き換え、 **hubListenEndpoint** の値を、Azure Portal の azure notification Hub サービスの [アクセスポリシー] タブにある [エンドポイント] の値に置き換えます (下の図を参照)。

    ![notification hub ポリシーエンドポイントの挿入](images/AzureLabs-Lab8-97.png)

6.  ここで、クラスを初期化する **Start () および起動** 前 **()** の各メソッドを追加します。

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  次のように、 **waitfornotification** メソッドを追加して、アプリがメインスレッドで競合するを使用せずに Notification Hub ライブラリから通知を受け取ることができるようにします。

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  次のメソッド **Initnotificationasync ()** を実行すると、初期化時にアプリケーションが Notification Hub サービスに登録されます。 Unity がプロジェクトをビルドできないため、コードはコメントアウトされています。 Visual Studio で Azure メッセージング Nuget パッケージをインポートすると、コメントが削除されます。

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  次のハンドラー ( **Channel \_ pushnotificationreceived ())** は、通知が受信されるたびにトリガーされます。 通知が逆シリアル化されます。これは、デスクトップアプリケーションで移動された Azure Table エンティティであり、MR シーン内の対応するオブジェクトを同じ位置に移動します。 
    
    > [!IMPORTANT]
    > コードがコメントアウトされるのは、Visual Studio 内で Nuget パッケージマネージャーを使用して Unity プロジェクトをビルドした後に追加する Azure メッセージングライブラリをコードが参照するためです。 そのため、Unity プロジェクトは、コメントアウトされていない限り、ビルドできません。プロジェクトをビルドし、Unity に戻る場合は、そのコードに **コメントを再** 記述する必要があることに注意してください。

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. Unity エディターに戻る前に、変更内容を保存しておいてください。

11. [**階層**] パネルから **メインカメラ** をクリックして、そのプロパティが **インスペクター** に表示されるようにします。

12. **Scripts** フォルダーを開いた状態で、 **notificationreceiver** スクリプトを選択し、**メインカメラ** にドラッグします。 結果は次のようになります。

    ![通知レシーバースクリプトをカメラにドラッグ](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > Microsoft HoloLens 用にこれを開発している場合は、次のように、 **メインカメラ** の *カメラ* コンポーネントを更新する必要があります。
    > - クリアフラグ: 純色
    > - 背景: 黒

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a>Chapter 16-UWP に対する Mixed Reality プロジェクトの構築

この章は、前のプロジェクトのビルドプロセスと同じです。 このプロジェクトの Unity セクションに必要なものはすべて完了したので、Unity から構築します。

1.  [**ビルドの設定**] ([**ファイル**  >  **ビルドの設定**]) に移動します。

2.  [ **ビルドの設定** ] メニューで、 **Unity C# プロジェクト** _ が表示されていることを確認します (このプロジェクトでは、ビルド後にこのプロジェクトのスクリプトを編集できます)。

3.  この操作が完了したら、[_ * ビルド] * * をクリックします。

    ![プロジェクトのビルド](images/AzureLabs-Lab8-99.png)

4.  **ファイルエクスプローラー** ウィンドウがポップアップ表示され、ビルドする場所を入力するように求められます。 (左上隅にある [ **新しいフォルダー** ] をクリックして) 新しいフォルダーを作成し、 **ビルド** という名前を指定します。

    ![ビルドフォルダーの作成](images/AzureLabs-Lab8-100.png)

    1.  [新しい **ビルド** ] フォルダーを開き、別のフォルダーを作成し ([ **新しいフォルダー** ] をもう一度使用)、「 **NH \_ MR \_ App**」という名前を指定します。

        ![NH_MR_Apps フォルダーの作成](images/AzureLabs-Lab8-101.png)

    2.  **NH \_ MR \_ アプリ** を選択します。 [ **フォルダーの選択] を** クリックします。 プロジェクトがビルドされるまでに1分ほどかかります。

5.  ビルドの後に、新しいプロジェクトの場所で **ファイルエクスプローラー** ウィンドウが開きます。



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a>Chapter 17-NuGet パッケージを UnityMRNotifHub ソリューションに追加する

> [!WARNING] 
> 次の NuGet パッケージを追加し (次の [章](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)のコードのコメントを解除すると)、Unity プロジェクト内で再度開いたときに、エラーが表示されることに注意してください。 引き続き Unity エディターで編集を続行する場合は、Visual Studio に戻ると、コードの一部をコメントにして、後で再度コメントする必要があります。 

Mixed reality ビルドが完了したら、ビルドした mixed reality プロジェクトに移動し、そのフォルダー内のソリューション (.sln) ファイルをダブルクリックして、Visual Studio 2017 でソリューションを開きます。
次に、 **Windowsazure.servicebus** NuGet パッケージを追加する必要があります。これは、通知ハブから通知を受信するために使用されるライブラリです。

NuGet パッケージをインポートするには:

1.  **ソリューションエクスプローラー** で、ソリューションを右クリックします。

2.  [ **NuGet パッケージの管理**] をクリックします。

    ![nuget マネージャーを開く](images/AzureLabs-Lab8-102.png)

3.  [ **_参照_*_] タブを選択し、_ windowsazure.servicebus を検索*** します。

    ![windows azure メッセージングパッケージの検索](images/AzureLabs-Lab8-103.png)

4.  次に示すように結果を選択し、右側のウィンドウで [ **Project**] の横にあるチェックボックスをオンにします。 これにより、[**プロジェクト**] の横にあるチェックボックスと、 **UnityMRNotifHub** **プロジェクトの横** のチェックボックスが表示されます。

    ![すべてのプロジェクトを目盛りする](images/AzureLabs-Lab8-104.png)

5.  最初に指定されたバージョンは、このプロジェクトと互換性が **ない可能性があり** ます。 そのため、[ **バージョン**] の横にあるドロップダウンメニューをクリックし、[ **バージョン 0.1.7.9**]、[ **インストール**] の順にクリックします。

6.  これで、NuGet パッケージのインストールが完了しました。 **Notificationreceiver** クラスに入力したコメントが付いているコードを見つけて、コメントを削除します。



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a>第18章-Edit UnityMRNotifHub application, NotificationReceiver クラス

**NuGet パッケージ** を追加した後、 **notificationreceiver** クラス内のコードの一部を *コメント* 解除する必要があります。

これには次のものが含まれます

1. 先頭にある名前空間:

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. **InitNotificationsAsync ()** メソッド内のすべてのコード:

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> 上記のコードにはコメントが含まれています。コメントが *誤って* コメント解除されていないことを確認してください (コードがを持っている場合はコンパイルされません)。

3. 最後に、 **Channel_PushNotificationReceived** イベントは次のようになります。

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

これらのコメントを解除したら、必ず保存し、次の章に進みます。

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a>第19章-mixed reality プロジェクトをストアアプリに関連付ける

ここで、ラボの開始時にで作成したストアアプリに **mixed reality** プロジェクトを関連付ける必要があります。

1.  ソリューションを開きます。

2.  ソリューションエクスプローラーパネルで UWP アプリプロジェクトを右クリックし、[ **ストア** に移行] をクリックして、 **アプリをストアに関連付け** ます。

    ![ストアの関連付けを開く](images/AzureLabs-Lab8-105.png)

3.  **[アプリを Windows ストアと関連付ける**] という新しいウィンドウが表示されます。 **[次へ]** をクリックします。

    ![次の画面に進む](images/AzureLabs-Lab8-106.png)

4.  これにより、ログインしたアカウントに関連付けられているすべてのアプリケーションが読み込まれます。 アカウントにログインしていない場合は、このページで **ログイン** できます。

5.  このチュートリアルの開始時に作成した **ストアアプリの名前** を探し、それを選択します。 続けて、 **[次へ]** をクリックします。

    ![ストア名を検索して選択します](images/AzureLabs-Lab8-107.png)

6.  **[関連付け]** をクリックします。

    ![アプリを関連付ける](images/AzureLabs-Lab8-108.png)

7.  これで、アプリがストアアプリに **関連付けら** れました。 これは、通知を有効にするために必要です。

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a>第20章-UnityMRNotifHub アプリケーションと UnityDesktopNotifHub アプリケーションのデプロイ

この章では、2人の方で簡単に実行できます。これは、実行中のアプリと、コンピューターのデスクトップで実行されているアプリと、イマーシブヘッドセット内のアプリの両方が含まれるためです。

イマーシブヘッドセットアプリは、シーンへの変更を受信するのを待機しています (ローカルのユーザーオブジェクトの位置の変更)。デスクトップアプリは、ローカルシーン (位置の変更) に変更を加えます。これは MR アプリに共有されます。 最初に MR アプリをデプロイし、次にデスクトップアプリを展開して、受信側がリッスンを開始できるようにすることが理にかなっています。

ローカルコンピューターに **UnityMRNotifHub** アプリをデプロイするには、次のようにします。

1.  **Visual Studio 2017** で **UnityMRNotifHub** アプリのソリューションファイルを開きます。

2.  **ソリューションプラットフォーム** で、[ **X86, ローカルコンピューター**] を選択します。

3.  **ソリューション構成** で、[**デバッグ**] を選択します。

    ![プロジェクト構成の設定](images/AzureLabs-Lab8-109.png)

4.  [ **ビルド] メニュー** の [ **ソリューションの配置** ] をクリックして、アプリケーションをコンピューターにサイドロードします。

5.  アプリがインストール済みのアプリの一覧に表示され、起動できる状態になります。

ローカルコンピューターに **UnityDesktopNotifHub** アプリをデプロイするには:

1.  **Visual Studio 2017** で **UnityDesktopNotifHub** アプリのソリューションファイルを開きます。

2.  **ソリューションプラットフォーム** で、[ **X86, ローカルコンピューター**] を選択します。

3.  **ソリューション構成** で、[**デバッグ**] を選択します。

    ![プロジェクト構成の設定](images/AzureLabs-Lab8-110.png)

4.  [ **ビルド] メニュー** の [ **ソリューションの配置** ] をクリックして、アプリケーションをコンピューターにサイドロードします。

5.  アプリがインストール済みのアプリの一覧に表示され、起動できる状態になります。

6.  Mixed reality アプリケーションを起動し、その後にデスクトップアプリケーションを起動します。

両方のアプリケーションを実行している状態で、(マウスの左ボタンを使用して) デスクトップシーンでオブジェクトを移動します。 これらの位置指定の変更は、ローカルでシリアル化され、Function App サービスに送信されます。 その後、Function App サービスによって、通知ハブと共にテーブルが更新されます。 更新を受信すると、通知ハブは、更新されたデータをすべての登録済みアプリケーション (この場合はイマーシブヘッドセットアプリ) に直接送信します。この場合、受信データが逆シリアル化され、ローカルオブジェクトに新しい位置指定データが適用され、シーン内で移動されます。


## <a name="your-finished-your-azure-notification-hubs-application"></a>Azure Notification Hubs アプリケーションが完成しました
 
これで、Azure Notification Hubs サービスを活用し、アプリ間の通信を可能にする mixed reality アプリを構築しました。
 
![最終製品-終了](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a>ボーナス演習

### <a name="exercise-1"></a>演習1

再生オブジェクトの色を変更し、その通知をシーンを表示している他のアプリに送信する方法はありますか。

### <a name="exercise-2"></a>演習2

MR アプリへのユーザーの移動を追加して、デスクトップアプリで更新されたシーンを表示できますか。
