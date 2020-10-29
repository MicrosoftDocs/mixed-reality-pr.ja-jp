---
title: MR と Azure 306-ストリーミングビデオ
description: このコースでは、mixed reality アプリケーション内で Azure Media Services を実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, チュートリアル, api, media services, ストリーミングビデオ, 360, イマーシブ, vr
ms.openlocfilehash: bf58c0c7a972e35b7330b15412174464ba28ac6d
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683146"
---
# <a name="mr-and-azure-306-streaming-video"></a>MR と Azure 306:ビデオのストリーム配信

<br>

>[!NOTE]
>Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。  そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。  これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは " **_ありません_** "。  これらは、サポートされているデバイス上で継続して動作するように、保守されます。 今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。  この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。

<br> 

![最終的な製品の開始- ](images/AzureLabs-Lab6-00.png)
 ![ 開始](images/AzureLabs-Lab6-01.png)

このコースでは、Azure Media Services を Windows Mixed Reality VR エクスペリエンスに接続して、イマーシブヘッドセットでのストリーミング360度のビデオ再生を許可する方法について説明します。 

**Azure Media Services** は、今日の最も人気のあるモバイルデバイスで、より多くのユーザーに配信するためのブロードキャスト品質のビデオストリーミングサービスを提供するサービスのコレクションです。 詳細については、 [Azure Media Services のページ](https://azure.microsoft.com/services/media-services)を参照してください。

このコースを完了すると、mixed reality イマーシブヘッドセットアプリケーションが完成します。これにより、次のことができるようになります。

1. **Azure Media Service** を使用して、 **Azure Storage** から360度のビデオを取得します。

2. Unity シーン内で取得した360度ビデオを表示します。

3. 2つの異なるビデオを使用して、2つのシーン間を移動します。

アプリケーションでは、結果をデザインと統合する方法については、お客様のニーズに合わせてください。 このコースは、Azure サービスを Unity プロジェクトと統合する方法を説明することを目的としています。 このコースで得られた知識を使用して、mixed reality アプリケーションを強化することができます。

## <a name="device-support"></a>デバイス サポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="../../../hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 306:ビデオのストリーム配信</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>前提条件

> [!NOTE]
> このチュートリアルは、Unity と C# の基本的な経験がある開発者向けに設計されています。 また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証されたものを表します (2018 年5月)。 [「ツールのインストール](../../install-the-tools.md)」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に記載されているものよりも新しいソフトウェアで見つかったものと完全に一致するとは限りません。

このコースでは、次のハードウェアとソフトウェアをお勧めします。

- 開発用 PC で、 [Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) (VR) ヘッドセット開発と互換性があります。
- [開発者モードが有効になっている Windows 10 の作成者の更新プログラム (またはそれ以降)](../../install-the-tools.md#installation-checklist)
- [最新の Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- [Windows Mixed Reality イマーシブ (VR) ヘッドセット](../../../discover/immersive-headset-hardware-details.md)
- Azure のセットアップとデータ取得のためのインターネットアクセス
- 2 360-mp4 形式のビデオ ( [このダウンロードページに](https://www.mettle.com/360vr-master-series-free-360-downloads-page)は、ロイヤリティフリーのビデオが掲載される場合があります)

## <a name="before-you-start"></a>開始する前に

1.  このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。
2.  Mixed Reality のイマーシブヘッドセットをセットアップしてテストします。

    > [!NOTE]
    > このコースでは、モーションコントローラーは必要 **ありません** 。 イマーシブヘッドセットの設定をサポートする必要がある場合は、 [Windows Mixed Reality のセットアップ方法に関するリンク](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)をクリックしてください。

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a>章 1-Azure Portal: Azure Storage アカウントの作成

**Azure Storage サービス** を使用するには、Azure portal で **ストレージアカウント** を作成し、構成する必要があります。

1.  [Azure Portal](https://portal.azure.com) にログインします。

    > [!NOTE]
    > まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。 このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。

2.  ログインしたら、左側のメニューの [ **ストレージアカウント** ] をクリックします。

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab6-02.png)

3.  [ **ストレージアカウント** ] タブで、[ **追加** ] をクリックします。

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab6-03.png)

4.  [ **ストレージアカウントの作成** ] タブで、次のようにします。

    1.  アカウントの **名前** を挿入します。このフィールドには数字と小文字のみを使用できることに注意してください。

    2.  [ **デプロイモデル] で、** [ **リソースマネージャー** ] を選択します。

    3.  [ **アカウントの種類** ] で、[ **ストレージ (汎用 v1)** ] を選択します。

    4.  [ **パフォーマンス** ] で [標準] * を選択し **ます。**

    5.  **レプリケーション** の場合は **、[ローカル冗長ストレージ (LRS)** ] を選択します。

    6.  **安全な転送** は無効のまま **に** しておく必要があります。

    7.  **サブスクリプション** を選択します。

    8.  リソースグループを選択するか、新しい **リソースグループ** を作成します。 リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。

    9.  リソースグループの **場所** を決定します (新しいリソースグループを作成している場合)。 この場所は、アプリケーションを実行するリージョンに配置するのが理想的です。 一部の Azure 資産は、特定のリージョンでのみ利用できます。

5.  このサービスに適用されている使用条件を理解していることを確認する必要があります。

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab6-04.png)

6.  [ **作成** ] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。

7.  サービスインスタンスが作成されると、ポータルに通知が表示されます。

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab6-05.png)

8.  この時点で、リソースに従う必要はありません。次の章に移動するだけです。

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a>章 2-Azure Portal: メディアサービスの作成

Azure Media Service を使用するには、アプリケーションで使用できるようにサービスのインスタンスを構成する必要があります (アカウント所有者は管理者である必要があります)。

1.  Azure Portal で、左上隅にある [ **リソースの作成** ] をクリックし、[ **メディアサービス]** を検索して、 **enter** キーを押します。 現在必要なリソースにはピンク色のアイコンが付いています。新しいページを表示するには、これをクリックします。

    ![Azure portal](images/AzureLabs-Lab6-06.png)

2.  新しいページには、 **メディアサービス** の説明が表示されます。 このプロンプトの左下にある [ **作成** ] ボタンをクリックして、このサービスとの関連付けを作成します。

    ![Azure portal](images/AzureLabs-Lab6-07.png)

3.  [ **作成** ] をクリックすると、新しいメディアサービスに関する詳細を指定する必要があるパネルが表示されます。

    1.  このサービスインスタンスに必要な **アカウント名** を挿入します。

    2.  **サブスクリプション** を選択します。

    3. リソースグループを選択するか、新しい **リソースグループ** を作成します。 リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。 1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのラボなど) を共通のリソースグループに保持することをお勧めします。 
    
    > Azure リソースグループの詳細については、 [Azure リソースグループの管理方法に関するこちらのリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)先を参照してください。

    4.  リソースグループの **場所** を決定します (新しいリソースグループを作成している場合)。 この場所は、アプリケーションを実行するリージョンに配置するのが理想的です。 一部の Azure 資産は、特定のリージョンでのみ利用できます。

    5.  [ **ストレージアカウント** ] セクションで、[ **選択...** ] セクションをクリックし、最後の章で作成した **ストレージアカウント** をクリックします。

    6.  また、このサービスに適用されている使用条件を理解していることを確認する必要があります。

    7.  **Create** をクリックしてください。

        ![Azure portal](images/AzureLabs-Lab6-08.png)

4.  [ **作成** ] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。

5.  サービスインスタンスが作成されると、ポータルに通知が表示されます。

    ![Azure portal](images/AzureLabs-Lab6-09.png)

6.  通知をクリックして、新しいサービスインスタンスを探索します。

    ![Azure portal](images/AzureLabs-Lab6-10.png)

7.  通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。

8.  [新しいメディアサービス] ページで、左側のパネルの [ **Assets** ] リンクをクリックします。

9.  次のページで、ページの左上隅にある [ **アップロード** ] をクリックします。

    ![Azure portal](images/AzureLabs-Lab6-11.png)

10. **フォルダー** アイコンをクリックしてファイルを参照し、ストリーミングする最初の360ビデオを選択します。 
    
    > このリンクを使用して [、サンプルビデオをダウンロード](https://vimeo.com/214401712)できます。

    ![Azure portal](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> ファイル名が長いと、エンコーダーで問題が発生する可能性があります。そのため、ビデオに問題がないことを確認するには、ビデオファイル名の長さを短くすることを検討してください。

11. ビデオのアップロードが完了すると、進行状況バーが緑色になります。

    ![Azure portal](images/AzureLabs-Lab6-13.png)

12. 上のテキスト ( **servicename-assets** ) をクリックして、[ **資産** ] ページに戻ります。

13. ビデオが正常にアップロードされたことがわかります。 そのタイルをクリックします。

    ![Azure portal](images/AzureLabs-Lab6-14.png)

14. リダイレクト先のページには、ビデオに関する詳細情報が表示されます。 ビデオを使用できるようにするには、ページの左上にある [ **エンコード** ] ボタンをクリックして、ビデオをエンコードする必要があります。

    ![Azure portal](images/AzureLabs-Lab6-15.png)

15. 新しいパネルが右側に表示されます。ここで、ファイルのエンコードオプションを設定することができます。 次のプロパティを設定します (一部は既に既定で設定されています)。

    1.  **メディアエンコーダー名 *Media Encoder Standard***

    2.  **エンコードプリセット *コンテンツアダプティブマルチビットレート MP4***

    3.  **ジョブ名 *Media Encoder Standard Video1.mp4の処理***

    4.  **出力メディアのアセット名 *Video1.mp4--Media Encoder Standard エンコード* されています**

        ![Azure portal](images/AzureLabs-Lab6-16.png)

16. **[作成]** ボタンをクリックします。

17. **エンコードジョブが追加さ** れたバーが表示され、そのバーをクリックすると、エンコードの進行状況を示すパネルが表示されます。

    ![Azure portal](images/AzureLabs-Lab6-17.png)

    ![Azure portal](images/AzureLabs-Lab6-18.png)

18. ジョブが完了するまで待ちます。 完了したら、パネルの右上にある [X] を自由に閉じます。

    ![Azure portal](images/AzureLabs-Lab6-19.png)

    ![Azure portal](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > これにかかる時間は、ビデオのファイルサイズによって異なります。 このプロセスにはかなりの時間がかかることがあります。

19. エンコードされたバージョンのビデオが作成されたので、それを公開してアクセスできるようにします。 これを行うには、青いリンク **アセット** をクリックして [アセット] ページに戻ります。

    ![Azure portal](images/AzureLabs-Lab6-21.png)

20. ビデオは、 **資産の種類が _マルチビットレート MP4_** である別のものと共に表示されます。

    ![Azure portal](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > 最初のビデオと共に新しい資産は *不明* であり、 **サイズ** が ' 0 ' バイトであることがわかります。更新するには、ウィンドウを更新するだけで済みます。

21. [この新しい資産] をクリックします。

    ![Azure portal](images/AzureLabs-Lab6-23.png)

22. 以前に使用したものと似たパネルが表示されますが、これは異なる資産です。 ページの上部中央にある [ **発行** ] ボタンをクリックします。

    ![Azure portal](images/AzureLabs-Lab6-24.png)

23. 資産内の file/s への **ロケーター** (エントリポイント) を設定するように求められます。 シナリオでは、次のプロパティを設定します。

    1.  **ロケーターの種類**  > **プログレッシブ** 。

    2.  **日付** と **時刻** は、現在の日付から将来の時刻 (この場合は100年) に設定されます。 そのままにするか、またはそれに合わせて変更します。

    > [!NOTE]
    > ロケーターの詳細および選択できる内容については、Azure Media Services の [ドキュメント](https://docs.microsoft.com/azure/media-services/media-services-concepts)を参照してください。

24. パネルの下部にある [ **追加** ] ボタンをクリックします。

    ![Azure portal](images/AzureLabs-Lab6-25.png)

25. ビデオが公開され、エンドポイントを使用してストリームできるようになりました。 さらに下のページは **ファイル** セクションです。 ここでは、ビデオのエンコードされたさまざまなバージョンを示します。 可能な限り最高の解像度を選択すると (下の図の1920x960 ファイル)、右側のパネルが表示されます。 **ダウンロード URL** が表示されます。 この **エンドポイント** は、後でコードで使用するのと同じようにコピーします。

    ![Azure portal](images/AzureLabs-Lab6-26.png)    

    ![Azure portal](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > [ **再生** ] ボタンをクリックしてビデオを再生し、テストすることもできます。

26. ここでは、このラボで使用する2番目のビデオをアップロードする必要があります。 上記の手順に従って、2番目のビデオと同じ手順を繰り返します。 2番目の **エンドポイント** もコピーするようにしてください。 [2 番目のビデオをダウンロードするに](https://vimeo.com/214402865)は、次のリンクを使用してください。

27. 両方のビデオが公開されたら、次の章に進むことができます。

## <a name="chapter-3---setting-up-the-unity-project"></a>章 3-Unity プロジェクトの設定

次に示すのは、Mixed Reality で開発するための一般的な設定です。そのため、他のプロジェクトに適したテンプレートです。

1.  **Unity** を開き、[ **新規** ] をクリックします。 

    ![Azure portal](images/AzureLabs-Lab6-28.png)

2.  ここで、Unity プロジェクト名を指定する必要があります。挿入 **MR \_ 360videostreaming.** プロジェクトの種類が **3d** に設定されていることを確認します。 場所を適切な場所に設定します (ルートディレクトリの方が適していることに注意してください)。 次に、[ **プロジェクトの作成** ] をクリックします。

    ![Azure portal](images/AzureLabs-Lab6-29.png)

3.  Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。 [ ***Edit* *設定* の編集** ] に移動し、新しいウィンドウで [ **外部ツール** ] に移動します。 **外部スクリプトエディター** を **Visual Studio 2017** に変更します。 [ **基本設定** ] ウィンドウを閉じます。

    ![Azure portal](images/AzureLabs-Lab6-30.png)

4.  次に、[ ***ファイル* *Build Settings*** ] [ビルドの設定] の順に移動し、[ **プラットフォームの切り替え** ] ボタンをクリックして、プラットフォームを **ユニバーサル Windows プラットフォーム** に切り替えます。

5.  また、次のことを確認してください。

    1. **ターゲットデバイス** は **、任意のデバイス** に設定されます。
    
    2.  **ビルドの種類** が D3D に設定されてい **ます。**

    3.  **SDK** は、 **インストールされている最新のバージョン** に設定されます。

    4.  **Visual Studio のバージョン** が、 **インストールされている最新** のバージョンに設定されています。

    5.  **ビルドと実行** はローカルコンピューターに設定されて **います。**

    6.  後で設定するため、 **今すぐ設定** することは心配しないでください。

    7.  ここでは、残りの設定は既定値のままにしておきます。

        ![Unity プロジェクトの設定](images/AzureLabs-Lab6-31.png)

6.  [ **ビルドの設定** ] ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 **インスペクター** が配置されている領域の関連パネルが開きます。 

7. このパネルでは、いくつかの設定を確認する必要があります。

    1.  [ **その他の設定** ] タブで、次のようにします。

        1.  **スクリプト****ランタイムのバージョン** は **安定** している必要があります (.net 3.5 と同等)。

        2. **スクリプトバックエンド** は .net である必要があり **ます。**

        3. **API の互換性レベル** は **.net 4.6** である必要があります。

            ![Unity プロジェクトの設定](images/AzureLabs-Lab6-32.png)

    2.  パネルの下にある [ **XR settings** (発行の **設定** ] の下にあります) で、[ **サポートされている仮想現実** ] をティックし、 **Windows Mixed reality SDK** が追加されていることを確認します。

        ![Unity プロジェクトの設定](images/AzureLabs-Lab6-33.png)

    3.  [ **発行の設定** ] タブの [ **機能** ] で、次の項目を確認します。

        - **InternetClient**

            ![Unity プロジェクトの設定](images/AzureLabs-Lab6-34.png)

8.  これらの変更を行ったら、[ **ビルドの設定** ] ウィンドウを閉じます。

9.  プロジェクトを保存します * *ファイル* * プロジェクトの保存 * *。



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a>Chapter 4-InsideOutSphere Unity パッケージのインポート

> [!IMPORTANT]
> このコースの *Unity セットアップ* コンポーネントをスキップしてコードに直接進む場合は、 [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage)をダウンロードし、 [**カスタムパッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてから、 **第5章** から続行してください。 引き続き Unity プロジェクトを作成する必要があります。

このコースでは、 [**unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage)という名前の Unity アセットパッケージをダウンロードする必要があります。

**Unitypackage** をインポートする方法:

1.  Unity ダッシュボードを使用して、画面の上部にあるメニューの [ **アセット** ] をクリックし、[ **パッケージのインポート > カスタムパッケージ** ] をクリックします。

    ![InsideOutSphere Unity パッケージをインポートしています](images/AzureLabs-Lab6-35.png)

2.  ファイルピッカーを使用して **Insideoutsphere** パッケージを選択し、[ **開く** ] をクリックします。 この資産のコンポーネントの一覧が表示されます。 インポートを確認するには、[ **インポート** ] をクリックします。

    ![InsideOutSphere Unity パッケージをインポートしています](images/AzureLabs-Lab6-36.png)

3.  インポートが完了すると、3つの新しいフォルダー、 **素材** 、 **モデル** 、および **Prefabs** が **Assets** フォルダーに追加されていることがわかります。 この種のフォルダー構造は、Unity プロジェクトで一般的に使用されます。

    ![InsideOutSphere Unity パッケージをインポートしています](images/AzureLabs-Lab6-37.png)

    1.  [ **モデル** ] フォルダーを開くと、 **Insideoutsphere** モデルがインポートされていることがわかります。

    2.  **素材** フォルダー内には、 **Insideoutspheres** マテリアル *lambert1* と、GazeButton によって使用される *buttonmaterial* と呼ばれる素材があります。これは近日中に表示されます。

    3.  **Prefabs** フォルダーには、 **insideoutsphere** *モデル* と *GazeButton* の両方を含む **insideoutsphere** prefab が含まれています。

    4.  **コードは含ま** れていません。このコースに従ってコードを記述します。


4.  **階層** 内で、 **メインカメラ** オブジェクトを選択し、次のコンポーネントを更新します。

    1.  **変換**

        1.  位置 = **X** : 0、 **Y** : 0、 **Z** : 0。

        2. 回転 = **X** : 0、 **Y** : 0、 **Z** : 0。

        3. Scale **X** : 1, **Y** : 1, **Z** : 1.

    2.  **カメラ**

        1. **クリアフラグ** : 純色。

        2.  **クリッピングプレーン** : Near: 0.1、Far: 6。

            ![InsideOutSphere Unity パッケージをインポートしています](images/AzureLabs-Lab6-38.png)

5.  **Prefab** フォルダーに移動し、[ **Insideoutsphere** ] を [ **階層** ] パネルにドラッグします。

    ![InsideOutSphere Unity パッケージをインポートしています](images/AzureLabs-Lab6-39.png)

6.  **階層** 内の **Insideoutsphere** オブジェクトの横にある小さな矢印をクリックして展開します。 **GazeButton** という名前の **子** オブジェクトがその下に表示されます。 これは、シーンとビデオを変更するために使用されます。

    ![InsideOutSphere Unity パッケージをインポートしています](images/AzureLabs-Lab6-40.png)

7.  [インスペクター] ウィンドウで、 **Insideoutsphere** の変換コンポーネントをクリックし、次のプロパティが設定されていることを確認します。

    |            |    変換-位置   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |    変換-回転   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** -50        |  **Z** 0  |

    |            |     変換-スケール     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![InsideOutSphere Unity パッケージをインポートしています](images/AzureLabs-Lab6-41.png)

8.  **GazeButton** 子オブジェクトをクリックし、その **変換** を次のように設定します。

    |            |    変換-位置   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 3.6|          **Y** 1.3        |  **Z** 0  |

    |            |    変換-回転   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     変換-スケール     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![InsideOutSphere Unity パッケージをインポートしています](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a>第5章-VideoController クラスの作成

**Videocontroller** クラスは、Azure Media Service からコンテンツをストリーミングするために使用される2つのビデオエンドポイントをホストします。

このクラスを作成するには:

1.  [ **プロジェクト** ] パネルにある **Asset フォルダー** を右クリックし、[ **> フォルダーの作成** ] をクリックします。 フォルダーに **スクリプト** の名前を指定します。

    ![VideoController クラスを作成する](images/AzureLabs-Lab6-43.png)

    ![VideoController クラスを作成する](images/AzureLabs-Lab6-44.png)

2.  [ **Scripts** ] フォルダーをダブルクリックして開きます。

3.  フォルダー内を右クリックし、[ **Create > C \# Script** ] をクリックします。 スクリプトに「 **Videocontroller** 」という名前を指定します。

    ![VideoController クラスを作成する](images/AzureLabs-Lab6-45.png)

4.  新しい **Videocontroller** スクリプトをダブルクリックして、 **Visual Studio 2017 で開きます。**

    ![VideoController クラスを作成する](images/AzureLabs-Lab6-46.png)

5.  コードファイルの先頭にある名前空間を次のように更新します。

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  **Videocontroller** クラスに次の変数を、起動前 **()** メソッドと共に入力します。

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

7.  Azure Media Service のビデオからエンドポイントを入力する時間は次のようになります。

    1.  最初のを *video1endpoint* 変数に挿入します。
    
    2.  2番目のを *video2endpoint* 変数に挿入します。

    > [!WARNING]
    > Unity での *https* の使用に関する既知の問題があります。バージョン 2017.4.1 f1 を使用します。 ビデオの再生時にエラーが発生した場合は、代わりに ' http ' を使用してみてください。

8.  次に、 **Start ()** メソッドを編集する必要があります。 このメソッドは、ユーザーが宝石ボタンを見てシーンを切り替えるたびにトリガーされます (その結果、ビデオが切り替わります)。

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  **Start ()** メソッドの後に、 **playvideo ()** *IEnumerator* メソッドを挿入します。これは、ビデオをシームレスに開始するために使用されます (そのため、動きが見られません)。

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

10. このクラスに必要な最後のメソッドは、"設定の切り替え **" メソッドです** 。このメソッドは、シーンの入れ替えに使用されます。

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > この **メソッドは** 、 \# *条件演算子* と呼ばれる便利な C 機能を使用します。 これにより、条件を確認してから、チェックの結果に基づいて値が返されます。すべて1つのステートメント内になります。 [条件演算子の詳細については、こちらのリンクを参照して](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator)ください。

11. Unity に戻る前に、変更を Visual Studio に保存します。

12. Unity エディターに戻り、 **Videocontroller** クラス [from] {. アンダーライン} **Scripts** フォルダーを、[ **階層** ] パネルの **メインカメラ** オブジェクトにドラッグします。

13. **メインカメラ** をクリックし、[ **インスペクター] パネル** を確認します。 新しく追加されたスクリプトコンポーネント内に、空の値を持つフィールドがあることがわかります。 これは参照フィールドで、コード内のパブリック変数を対象とします。

14. 次の図に示すように、[ **階層] パネル** の [ **Insideoutsphere** ] オブジェクトを [ **球体** ] スロットにドラッグします。

    ![VideoController クラスを作成する ](images/AzureLabs-Lab6-47.png)
     ![ videocontroller クラスを作成する](images/AzureLabs-Lab6-48.png)

## <a name="chapter-6---create-the-gaze-class"></a>Chapter 6-"宝石" クラスを作成する

このクラスは、ユーザーが参照しているオブジェクトを検出するために、 **メインカメラ** から投影される **Raycast** を作成します。 この場合、 **Raycast** は、ユーザーがシーン内の **GazeButton** オブジェクトを調べて動作をトリガーするかどうかを識別する必要があります。

このクラスを作成するには:

1.  前に作成した **Scripts** フォルダーにアクセスします。

2.  [ **プロジェクト** ] パネル内を右クリックし、* [* C スクリプトの *作成* ] * * をクリック \# します。 スクリプトに「」という名前を **指定します** 。

3.  新しい ***宝石*** のスクリプトをダブルクリックして、 **Visual Studio 2017 で開きます。**

4.  次の名前空間がスクリプトの先頭にあることを確認し、その他の名前空間を削除します。

    ```csharp
    using UnityEngine;
    ```

5.  次に、次の変数を、 **宝石** クラス内に追加します。

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

6.  起動可能な **()** メソッドと **Start ()** メソッドのコードを追加する必要があります。

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

7.  **Update ()** メソッドに次のコードを追加して、Raycast を射影し、ターゲットのヒットを検出します。

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

8.  Unity に戻る前に、変更を Visual Studio に保存します。

9.  [スクリプト] フォルダーから、[ **階層** ] パネルの [メインカメラ] オブジェクトに、 **見つめ** クラスをクリックしてドラッグします。

## <a name="chapter-7---setup-the-two-unity-scenes"></a>第7章-Unity の2つのシーンの設定

この章の目的は、ストリーミングするビデオをそれぞれホストする2つのシーンを設定することです。 作成済みのシーンを複製して、もう一度設定する必要がないようにします。ただし、 *GazeButton* オブジェクトが別の場所にあり、外観が異なるように、新しいシーンを編集します。 これは、シーン間で変更する方法を示すためのものです。

1.  これを行うには、ファイルに移動し **て、シーンに名前を付けて保存... >** します。保存ウィンドウが表示されます。 [ **新しいフォルダー** ] ボタンをクリックします。

    ![第7章-Unity の2つのシーンの設定](images/AzureLabs-Lab6-49.png)

2.  フォルダーの名前を「 **シーン** 」にします。

3.  [ **シーンの保存** ] ウィンドウは開いたままです。 新しく作成した **シーン** フォルダーを開きます。

4.  [ **ファイル名:** テキスト] フィールドに「 **VideoScene1** 」と入力し、[ **保存** ] をクリックします。

5.  Unity に戻り、[ **シーン** ] フォルダーを開き、 **VideoScene1** ファイルを左クリックします。 キーボードを使用して Ctrl キーを押し **ながら D** キーを押すと、そのシーンが複製されます。

    > [!TIP]
    > 重複 **するコマンドは** 、[ **編集 > 複製** ] に移動して実行することもできます。

6.  Unity では、シーン名の番号が自動的にインクリメントされますが、それが前に挿入されたコードと一致することを確認してください。

    >  **VideoScene1** と **VideoScene2** が必要です。

7.  2つのシーンを使用して、[ **ファイル > ビルド設定** ] にアクセスします。 [ **ビルドの設定** ] ウィンドウを開いた状態で、[ビルド] セクションの **シーン** にシーンをドラッグします。

    ![第7章--2 つの Unity シーンの設定](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > **シーンフォルダーから** 両方のシーンを選択するには、 **Ctrl** ボタンを押しながら各シーンを左クリックし、最後に両方をドラッグします。

8.  [ **ビルドの設定** ] ウィンドウを閉じ、[ **VideoScene2** ] をダブルクリックします。

9.  2番目のシーンを開いた状態で、 **Insideoutsphere** の **GazeButton** 子オブジェクトをクリックし、その変換を次のように設定します。

    |            |    変換-位置   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |         **Y** 1.3         | **Z** 3.6 |

    |            |    変換-回転   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     変換-スケール     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

10. **GazeButton** 子が選択された状態で、 **インスペクター** と **メッシュフィルター** を確認します。 [ **メッシュ** 参照] フィールドの横にある小さなターゲットをクリックします。

    ![第7章--2 つの Unity シーンの設定](images/AzureLabs-Lab6-51.png)

11. **[メッシュの選択** ] ポップアップウィンドウが表示されます。 **アセット** の一覧から **キューブ** メッシュをダブルクリックします。

    ![第7章--2 つの Unity シーンの設定](images/AzureLabs-Lab6-52.png)

12. **メッシュフィルター** が更新され、現在は **キューブ** になります。 ここで、[ **球 Collider** ] の横にある **歯車** アイコンをクリックし、[ **コンポーネントの削除** ] をクリックして、このオブジェクトから Collider を削除します。

    ![第7章--2 つの Unity シーンの設定](images/AzureLabs-Lab6-53.png)

13. **GazeButton** を選択したまま、 **インスペクター** の下部にある [ **コンポーネントの追加** ] ボタンをクリックします。 検索フィールドに「 **box** 」と入力します。 box **collider** がオプションになります。これをクリックすると、 **box collider** が **GazeButton** オブジェクトに追加されます。

    ![第7章--2 つの Unity シーンの設定](images/AzureLabs-Lab6-54.png)

14. **GazeButton** が部分的に更新されるようになりました。別の外観になるように、新しい **素材** を作成します。これにより、最初のシーンのオブジェクトとは異なるオブジェクトとして認識しやすくなります。

15. [ **プロジェクト] パネル** 内の [ **素材** ] フォルダーに移動します。 **Buttonmaterial** マテリアルを複製します (キーボードの **Ctrl**  +  **D** キーを押すか、 **素材** を左クリックし、[ファイルの **編集** ] メニューオプションから [ **複製** ] を選択します)。

    ![第7章--2 つの Unity シーンのセットアップ ](images/AzureLabs-Lab6-55.png)
     ![ 第7章: 2 つの unity シーンの設定](images/AzureLabs-Lab6-56.png)

16. 新しい **buttonmaterial** マテリアル (ここでは **buttonmaterial 1** という名前) を選択し、 **インスペクター** 内で [ **albedo** 色] ウィンドウをクリックします。 ポップアップが表示されます。ここで別の色を選択し (任意のものを選択)、ポップアップを閉じます。 素材は独自のインスタンスであり、元のインスタンスとは異なります。

    ![第7章--2 つの Unity シーンの設定](images/AzureLabs-Lab6-57.png)

17. 新しい **素材** を **GazeButton** 子にドラッグして、その外観を完全に更新します。これにより、最初のシーンボタンから簡単に識別できるようになります。

    ![第7章--2 つの Unity シーンの設定](images/AzureLabs-Lab6-58.png)

18. この時点で、UWP プロジェクトをビルドする前に、エディターでプロジェクトをテストすることができます。

    -  **エディター** の [ **再生** ] ボタンを押して、ヘッドセットを磨耗します。

        ![第7章--2 つの Unity シーンの設定](images/AzureLabs-Lab6-59.png)

19. 2つの **GazeButton** オブジェクトを見て、1番目と2番目のビデオを切り替えます。

## <a name="chapter-8---build-the-uwp-solution"></a>章 8-UWP ソリューションのビルド

エディターにエラーがないことを確認したら、ビルドすることができます。

ビルドするには:

1.  [ **ファイル > 保存** ] をクリックして、現在のシーンを保存します。

2.  **Unity C \# プロジェクト** と呼ばれるチェックボックスをオンにします (ビルドの完了後にクラスを編集できるため、これは重要です)。

3.  [ **ファイル > ビルド設定** ] にアクセスし、[ **ビルド** ] をクリックします。

4.  ソリューションをビルドするフォルダーを選択するように求められます。

5.  **ビルド** フォルダーを作成し、そのフォルダー内で、適切な名前を指定して別のフォルダーを作成します。

6.  新しいフォルダーをクリックし、[ **フォルダーの選択** ] をクリックします。そのフォルダーを選択して、その場所でビルドを開始します。

    ![第8章--UWP ソリューションのビルド ](images/AzureLabs-Lab6-60.png)
     ![ chapter 8--uwp ソリューションのビルド](images/AzureLabs-Lab6-61.png)

7.  Unity のビルドが完了すると (時間がかかる場合があります)、ビルドの場所で **ファイルエクスプローラー** ウィンドウが開きます。

## <a name="chapter-9---deploy-on-local-machine"></a>第9章-ローカルコンピューターへのデプロイ

ビルドが完了すると、ビルドの場所に [ **ファイルエクスプローラー** ] ウィンドウが表示されます。 という名前で作成したフォルダーを開き、そのフォルダー内のソリューション (.sln) ファイルをダブルクリックして、Visual Studio 2017 でソリューションを開きます。

残りの作業は、お使いのコンピューター (または *ローカルコンピューター* ) にアプリを配置することだけです。

ローカルコンピューターに配置するには:

1.  **Visual Studio 2017** で、先ほど作成したソリューションファイルを開きます。

2.  **ソリューションプラットフォーム** で、[ **X86, ローカルコンピューター** ] を選択します。

3.  **ソリューション構成** で、[ **デバッグ** ] を選択します。

    ![第9章--ローカルコンピューターへのデプロイ](images/AzureLabs-Lab6-62.png)

4.  次に、ソリューションにパッケージを復元する必要があります。 **ソリューション** を右クリックし、[ **ソリューションの NuGet パッケージの復元...** ] をクリックします。

    > [!NOTE] 
    > これは、Unity によって構築されたパッケージが、ローカルマシン参照を操作するためにターゲットにする必要があるためです。

5.  [ **ビルド] メニュー** の [ **ソリューションの配置** ] をクリックして、アプリケーションをコンピューターにサイドロードします。 まず、Visual Studio によってアプリケーションがビルドされ、配置されます。

6.  アプリがインストール済みのアプリの一覧に表示され、起動できる状態になります。

    ![第9章--ローカルコンピューターへのデプロイ](images/AzureLabs-Lab6-63.png)

Mixed Reality アプリケーションを実行すると、アプリ内で使用した **Insideoutsphere** モデル内に配置されます。 この球は、ビデオがストリーミングされる場所になります。これにより、着信ビデオ (この観点では客席でした) の360度のビューが提供されます。 ビデオが読み込まれるまでに数秒かかる場合、アプリには、使用可能なインターネット速度が適用されます。ビデオをフェッチしてからダウンロードする必要があるので、アプリにストリーミングします。
準備ができたら、シーンを変更し、2番目のビデオを開いて、赤い球で整理します。 次に、2番目のシーンで blue キューブを使用して、戻ってもかまいません。

## <a name="your-finished-azure-media-service-application"></a>完成した Azure Media Service アプリケーション
 
これで、Azure Media Services を利用して360ビデオをストリーミングする mixed reality アプリが作成されました。

![ラボの結果](images/AzureLabs-Lab6-00.png)

![ラボの結果](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a>ボーナスの演習

**演習1**

このチュートリアルでは、1つのシーンのみを使用してビデオを変更することができます。 アプリケーションを試し、1つのシーンにします。 場合によっては、ミックスに別のビデオを追加することもできます。

**演習2**

Azure と Unity を試し、インターネット接続の強度に応じて、別のファイルサイズでビデオを自動的に選択するアプリの機能を実装します。


