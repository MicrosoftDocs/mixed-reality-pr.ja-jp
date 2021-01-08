---
title: MR と Azure 304 - 顔認識
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, チュートリアル, api, 顔認識, hololens, イマーシブ, vr, Windows 10, Visual Studio
ms.openlocfilehash: a6578950039a0a9267b7191f5b96775dca366c01
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010152"
---
# <a name="mr-and-azure-304-face-recognition"></a>MR と Azure 304:顔認識

<br>

>[!NOTE]
>Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。  そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。  これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。  これらは、サポートされているデバイス上で継続して動作するように、保守されます。 今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。  この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。

<br>

![このコースの完了の結果](images/AzureLabs-Lab4-00.png)

このコースでは、Microsoft Face API と共に Azure Cognitive Services を使用して、mixed reality アプリケーションに顔認識機能を追加する方法について説明します。

*Azure Face API* は Microsoft のサービスであり、開発者が最も高度な顔アルゴリズムをクラウドで利用できます。 *Face API* には、属性付きの顔検出と顔認識の2つの主な機能があります。 これにより、開発者は、顔のグループのセットを設定し、後でクエリイメージをサービスに送信して、顔が属するユーザーを特定することができます。 詳細については、 [Azure の顔認識](https://azure.microsoft.com/services/cognitive-services/face/)に関するページを参照してください。

このコースを完了すると、mixed reality HoloLens アプリケーションが完成します。これにより、次のことができるようになります。

1. **タップジェスチャ** を使用して、ボード HoloLens カメラを使用してイメージのキャプチャを開始します。 
2. キャプチャしたイメージを *Azure Face API* サービスに送信します。
3. *Face API* アルゴリズムの結果を受け取ります。
4. 単純なユーザーインターフェイスを使用して、一致するユーザーの名前を表示します。

ここでは、Face API サービスから Unity ベースの mixed reality アプリケーションに結果を取得する方法について説明します。

アプリケーションでは、結果をデザインと統合する方法については、お客様のニーズに合わせてください。 このコースは、Azure サービスを Unity プロジェクトと統合する方法を説明することを目的としています。 このコースで得られた知識を使用して、mixed reality アプリケーションを強化することができます。

## <a name="device-support"></a>デバイス サポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="../../../hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 304:顔認識</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> このコースでは主に HoloLens に焦点を当てていますが、このコースで学習する内容を Windows Mixed Reality イマーシブ (VR) ヘッドセットにも適用できます。 イマーシブ (VR) ヘッドセットにはアクセス可能なカメラがないため、外部カメラが PC に接続されている必要があります。 コースを進めると、イマーシブ (VR) ヘッドセットをサポートするために必要な変更についての注意事項が表示されます。

## <a name="prerequisites"></a>前提条件

> [!NOTE]
> このチュートリアルは、Unity と C# の基本的な経験がある開発者向けに設計されています。 また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証されたものを表します (2018 年5月)。 「 [ツールのインストール](../../install-the-tools.md) 」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に記載されているものよりも新しいソフトウェアで見つかったものと完全に一致するとは限りません。

このコースでは、次のハードウェアとソフトウェアをお勧めします。

- 開発用 PC で、 [Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) (VR) ヘッドセット開発と互換性があります。
- [開発者モードが有効になっている Windows 10 の作成者の更新プログラム (またはそれ以降)](../../install-the-tools.md)
- [最新の Windows 10 SDK](../../install-the-tools.md)
- [Unity 2017.4](../../install-the-tools.md)
- [Visual Studio 2017](../../install-the-tools.md)
- [Windows Mixed Reality イマーシブ (VR) ヘッドセット](../../../discover/immersive-headset-hardware-details.md)または開発者モードを有効にした[Microsoft HoloLens](../../../hololens-hardware-details.md)
- PC に接続されているカメラ (イマーシブヘッドセット開発用)
- Azure のセットアップと Face API の取得のためのインターネットアクセス

## <a name="before-you-start"></a>アップグレードを開始する前に

1.  このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。
2.  HoloLens をセットアップしてテストします。 HoloLens のセットアップをサポートする必要がある場合は、 [hololens セットアップに関する記事にアクセスして](https://docs.microsoft.com/hololens/hololens-setup)ください。 
3.  新しい HoloLens アプリの開発を開始するときは、調整とセンサーのチューニングを実行することをお勧めします (ユーザーごとにこれらのタスクを実行するのに役立つ場合があります)。 

調整の詳細については、 [「HoloLens の調整に関する記事へのリンク」を](../../../calibration.md#hololens-2)参照してください。

センサーチューニングの詳細については、 [HoloLens センサーチューニングに関する記事へのリンクを](../../../sensor-tuning.md)参照してください。

## <a name="chapter-1---the-azure-portal"></a>章 1-Azure Portal

Azure で *Face API* サービスを使用するには、アプリケーションで使用できるようにサービスのインスタンスを構成する必要があります。

1.  まず、 [Azure Portal](https://portal.azure.com)にログインします。 

    > [!NOTE]
    > まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。 このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。

2.  ログインしたら、左上隅にある [ **新規** ] をクリックし、 *Face API* を検索して、 **enter キーを** 押します。

    ![face api の検索](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > 新しいポータルで、 **New** という単語が **リソースの作成** に置き換えられました。

3.  新しいページには、 *Face API* サービスの説明が表示されます。 このプロンプトの左下にある [ **作成** ] ボタンを選択して、このサービスとの関連付けを作成します。

    ![face api 情報](images/AzureLabs-Lab4-02.png)

4.  [ **作成**:

    1. このサービスインスタンスに必要な名前を挿入します。

    2. サブスクリプションを選択します。

    3. 適切な価格レベルを選択します。これが *Face API サービス* を初めて作成する場合は、free レベル (F0) を使用できます。

    4. リソースグループを選択するか、新しい **リソースグループ** を作成します。 リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。 1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのラボなど) を共通のリソースグループに保持することをお勧めします。 

        > Azure リソースグループの詳細については、 [リソースグループ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)に関する記事をご覧ください。

    5. 後で使用する UWP **アプリでは、場所** として "米国西部" を使用する必要があります。

    6. また、このサービスに適用されている使用条件を理解していることを確認する必要があります。

    7. [作成] * を選択し **ます。**

        ![face api サービスの作成](images/AzureLabs-Lab4-03.png)

5.  [ **作成] *** をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。

6.  サービスインスタンスが作成されると、ポータルに通知が表示されます。

    ![サービス作成の通知](images/AzureLabs-Lab4-04.png)

7.  通知をクリックして、新しいサービスインスタンスを探索します。

    ![リソース通知にアクセス](images/AzureLabs-Lab4-05.png)

8.  準備ができたら、通知の [ **リソースにアクセス** ] ボタンをクリックして、新しいサービスインスタンスを探索します。

    ![顔の api キーにアクセスする](images/AzureLabs-Lab4-06.png)

9.  このチュートリアルでは、アプリケーションがサービスの呼び出しを行う必要があります。サービスは、サービスのサブスクリプション ' key ' を使用して実行されます。 *Face API* サービスの [*クイックスタート*] ページでは、最初のポイントは番号1で、*キーを取得します。*

10. [ *サービス* ] ページで、[青い **キー** ] ハイパーリンク ([クイックスタート] ページの場合)、または [サービス] ナビゲーションメニューの **[キー] リンク (** 左側にある [キー] アイコンで示されます) を選択して、キーを表示します。

    > [!NOTE] 
    > 後で必要になるので、いずれかのキーを書き留め、保護します。

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>Chapter 2-"Person Maker" UWP アプリケーションの使用

「 [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip)」というビルド済みの UWP アプリケーションをダウンロードしてください。 このアプリは、このコースの最終的な製品ではなく、Azure エントリを作成するためのツールです。これは、それ以降のプロジェクトで利用されます。

**個人のメーカー** では、ユーザーとグループに関連付けられている Azure エントリを作成できます。 アプリケーションは、必要なすべての情報を、後で FaceAPI が使用できる形式で配置します。これにより、追加したユーザーの顔を認識することができます。 

> : **個人所有者** は、いくつかの基本的な調整を使用して、 **無料サブスクリプションレベル** で1分あたりのサービス呼び出し数を超えないようにします。 調整が行われると、上部の緑色のテキストが赤に変わり、' アクティブ ' として更新されます。この場合は、アプリケーションを待機するだけです (これは、次に顔サービスへのアクセスが続行されるまで待機し、再度使用できるように "IN-アクティブ" として更新します)。

このアプリケーションでは、 *ProjectOxford* ライブラリを使用します。これにより、Face API を最大限に活用することができます。 このライブラリは、NuGet パッケージとして無料で利用できます。 これと同様の Api の詳細については、 [api リファレンスの記事を参照して](https://docs.microsoft.com/azure/cognitive-services/face/apireference)ください。

> [!NOTE] 
> これらの手順は、必要な手順にすぎません。これらを実行する手順については、ドキュメントの後半で説明します。 **個人のメーカー** アプリでは、次のことが可能です。
>
> - *ユーザーグループ* を作成します。これは、関連付ける複数のユーザーで構成されるグループです。 Azure アカウントを使用すると、複数のユーザーグループをホストできます。
>
> - Person グループのメンバーである *ユーザー* を作成します。 各ユーザーには、多数の *顔* イメージが関連付けられています。
>
> -  *顔イメージ* を *担当者* に割り当てて、Azure Face API サービスが対応する *顔* によって *個人* を認識できるようにします。
>
> -  *Azure Face API サービス* を *トレーニング* します。

このため、このアプリをトレーニングしてユーザーを認識させるには、個人グループに追加する各ユーザーの 10 (10) の写真が必要です。 Windows 10 Cam アプリを使用すると、これらのアプリを簡単に実行できます。 各写真が明確になっていることを確認する必要があります (ぼかし、覆い、または大きすぎないようにしてください)。また、画像ファイルのサイズが **4 MB** 以下で、 **1 KB** 未満の画像を jpg または png ファイル形式にしてください。

> [!NOTE]
> このチュートリアルに従う場合は、お客様のトレーニングに独自の顔を使用しないでください。 HoloLens をオンにした場合は、自分で確認することはできません。 同僚や同僚の顔を使用します。

実行中の **ユーザーのメーカー**:

1.  [ **個人** ] フォルダーを開き、[個人] *ソリューション* をダブルクリックして *Visual Studio* で開きます。

2.  *個人メーカーソリューション* が開いたら、次のことを確認してください。

    1. *ソリューション構成* が **デバッグ** に設定されています。

    2. *ソリューションプラットフォーム* が **x86** に設定されている

    3. *ターゲットプラットフォーム* は **ローカルコンピューター** です。

    4.  また、 *Nuget パッケージの復元* が必要になる場合もあります ( *ソリューション* を右クリックし、[ **nuget パッケージの復元**] を選択します)。

3.  [ *ローカルコンピューター* ] をクリックすると、アプリケーションが起動します。 小さい画面では、すべてのコンテンツが表示されない場合があることに注意してください。ただし、下にスクロールして表示することもできます。

    ![個人のメーカーのユーザーインターフェイス](images/AzureLabs-Lab4-07.png)

4.  Azure 内の *Face API* サービスから、必要な **azure 認証キー** を挿入します。

5.  挿入: 

    1. *Person グループ* に割り当てる *ID* を指定します。 ID は小文字で指定する必要があります。スペースは使用できません。 この ID は、後で Unity プロジェクトで必要になるため、メモしておいてください。
    2. *Person グループ* に割り当てる *名前*(スペースを含めることができます)。


6.  [ **Person Group を作成** ] ボタンをクリックします。 ボタンの下に確認メッセージが表示されます。

> [!NOTE]
> "アクセスが拒否されました" というエラーが発生する場合は、Azure サービス用に設定した場所を確認します。 前述のように、このアプリは "米国西部" 向けに設計されています。

> [!IMPORTANT]
> [ **既知のグループをフェッチ** ] ボタンをクリックすることもできます。これは、ユーザーグループを既に作成していて、新しいものを作成するのではなく、そのグループを使用する必要がある場合に使用します。 ただし、[既知のグループを持つ *ユーザーグループを作成* する] をクリックすると、グループもフェッチされます。

7.  作成する *ユーザー* の *名前* を挿入します。

    1. [ **Create Person** ] ボタンをクリックします。

    2. ボタンの下に確認メッセージが表示されます。

    3. 以前に作成したユーザーを削除する場合は、名前をテキストボックスに入力し、del **person** キーを押します。

8.  グループに追加するユーザーの10枚の写真の場所がわかっていることを確認します。

9.  [ **作成** ] をクリックしてフォルダーを開き、ユーザーに関連付けられているフォルダーにエクスプローラーを開きます。 10個のイメージをフォルダーに追加します。 これらは、 *JPG* または *PNG* ファイル形式である必要があります。

10. [ **Azure への送信**] をクリックします。 カウンターには、送信の状態が表示され、その後、完了時にメッセージが表示されます。

11. カウンターが終了し、確認メッセージが表示されたら、[ **トレーニング** ] をクリックしてサービスをトレーニングします。

プロセスが完了すると、Unity に移行できるようになります。

## <a name="chapter-3---set-up-the-unity-project"></a>章 3-Unity プロジェクトの設定

次に示すのは、mixed reality で開発するための一般的な設定です。そのため、他のプロジェクトに適したテンプレートです。

1.  *Unity* を開き、[**新規**] をクリックします。 

    ![新しい Unity プロジェクトを開始します。](images/AzureLabs-Lab4-08.png)

2.  ここで、Unity プロジェクト名を指定する必要があります。 **MR_FaceRecognition** を挿入します。 プロジェクトの種類が **3d** に設定されていることを確認します。 場所を適切な **場所** に設定します (ルートディレクトリの方が適していることに注意してください)。 次に、[ **プロジェクトの作成**] をクリックします。

    ![新しい Unity プロジェクトの詳細を指定します。](images/AzureLabs-Lab4-09.png)

3.  Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。 [ **> の設定の編集** ] に移動し、新しいウィンドウで [ **外部ツール**] に移動します。 **外部スクリプトエディター** を **Visual Studio 2017** に変更します。 [ **基本設定** ] ウィンドウを閉じます。

    ![スクリプトエディターの設定を更新します。](images/AzureLabs-Lab4-10.png)

4.  次に、[**ファイル > ビルド設定**] に移動し、[プラットフォームの **切り替え**] ボタンをクリックして、プラットフォームを **ユニバーサル Windows プラットフォーム** に切り替えます。

    ![[ビルドの設定] ウィンドウで、[プラットフォーム] を [UWP] に切り替えます。](images/AzureLabs-Lab4-11.png)

5.  [ **ファイル > ビルド設定** ] にアクセスし、次のことを確認します。

    1. **ターゲットデバイス** が **HoloLens** に設定されています

        > イマーシブヘッドセットの場合は、 **ターゲットデバイス** を *任意のデバイス* に設定します。

    2. **ビルドの種類** が **D3D** に設定されています
    3. **SDK** は最新の **インストール** に設定されています
    4. **Visual Studio のバージョン** が、**インストールされている最新** バージョンに設定されています
    5. **ビルドと実行** は **ローカルコンピューター** に設定されています
    6. シーンを保存し、ビルドに追加します。 

        1. これを行うには、[開いている **シーンの追加**] を選択します。 保存ウィンドウが表示されます。

            ![[開いているシーンを追加] ボタンをクリックする](images/AzureLabs-Lab4-12.png)

        2. [ **新しいフォルダー** ] ボタンを選択し、新しいフォルダーを作成するには、「 **シーン**」という名前を指定します。

            ![新しいスクリプトフォルダーの作成](images/AzureLabs-Lab4-13.png)

        3. 新しく作成した [ **シーン** ] フォルダーを開き、[ **ファイル名**: テキスト] フィールドに「 **FaceRecScene**」と入力し、[ **保存**] を押します。

            ![新しいシーンに名前を付けます。](images/AzureLabs-Lab4-14.png)

    7. それ以外の設定は、[ *ビルド設定*] の [既定] のままにしておきます。

6. [ *ビルドの設定* ] ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 *インスペクター* が配置されている領域の関連パネルが開きます。 

    ![プレーヤーの設定を開きます。](images/AzureLabs-Lab4-15.png)

7. このパネルでは、いくつかの設定を確認する必要があります。

    1. [ **その他の設定** ] タブで、次のようにします。

        1. **Scripting** **Runtime のバージョン** は **実験的** である必要があります (.net 4.6 と同等)。 これを変更すると、エディターを再起動する必要が生じます。
        2. **バックエンド** は **.net** である必要があります
        3. **API 互換性レベル** は **.net 4.6** である必要があります

            ![その他の設定を更新します。](images/AzureLabs-Lab4-16.png)
      
    2. [ **発行の設定** ] タブの [ **機能**] で、次の項目を確認します。

        - **InternetClient**
        - **Web カメラ**

            ![発行設定を更新しています。](images/AzureLabs-Lab4-17.png)

    3. パネルの下にある [ **XR settings** (発行の **設定**] の下にあります) で、[ **サポートされている仮想現実**] をティックし、 **Windows Mixed reality SDK** が追加されていることを確認します。

        ![X R の設定を更新します。](images/AzureLabs-Lab4-18.png)

8.  *ビルド設定* に戻ると、 **Unity C# プロジェクト** はグレーで表示されなくなりました。このの横にあるチェックボックスをオンにします。 
9.  [ビルド設定] ウィンドウを閉じます。
10. シーンとプロジェクトを保存します ([**ファイル] > [シーン/ファイルの保存] > [プロジェクトの保存**])。

## <a name="chapter-4---main-camera-setup"></a>第4章-メインカメラのセットアップ

> [!IMPORTANT]
> このコースの *Unity セットアップ* コンポーネントをスキップし、コードに直接進む場合は、 [unitypackage をダウンロード](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)して、 [カスタムパッケージ](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてください。 このパッケージには、 [5 章](#chapter-5--import-the-newtonsoftjson-library)で説明されている *NEWTONSOFT DLL* のインポートも含まれることに注意してください。 インポートされたを使用して、 [6 章](#chapter-6---create-the-faceanalysis-class)から続行することができます。

1.  [ *階層* ] パネルで、 **メインカメラ** を選択します。

2.  選択すると、 **メインカメラ** のすべてのコンポーネントが [ *インスペクター] パネル* に表示されます。

    1. **カメラオブジェクト** は **メインカメラ** という名前にする必要があります (スペルに注意してください)。

    2. メインカメラの **タグ** は、 **maincamera** に設定する必要があります (スペルに注意してください)。

    3. **変換位置** が **0、0、0** に設定されていることを確認します。

    4. **クリアフラグ** を **純色** に設定する

    5. カメラコンポーネントの **背景** 色を **黒、アルファ 0 (16 進コード: #00000000)** に設定します。

        ![カメラコンポーネントの設定](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>Chapter 5 –ライブラリに Newtonsoft.Jsをインポートする

> [!IMPORTANT]
> [最後の章](#chapter-4---main-camera-setup)で "unitypackage" をインポートした場合は、この章をスキップできます。

受信して Bot サービスに送信されたオブジェクトを逆シリアル化およびシリアル化するには、ライブラリ *にNewtonsoft.Js* をダウンロードする必要があります。 この [unity パッケージファイル](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage)には、適切な unity フォルダー構造が既に構成されている互換性のあるバージョンがあります。 

ライブラリをインポートするには:

1.  Unity パッケージをダウンロードします。
2.  [ **資産**]、[ **パッケージのインポート**]、[ **カスタムパッケージ**] の順にクリックします。

    ![Newtonsoft.Jsのインポート](images/AzureLabs-Lab4-20.png)

3.  ダウンロードした Unity パッケージを探し、[開く] をクリックします。
4.  パッケージのすべてのコンポーネントが解除されていることを確認し、[ **インポート**] をクリックします。

    ![資産に Newtonsoft.Jsをインポートする](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>Chapter 6-FaceAnalysis クラスの作成

FaceAnalysis クラスの目的は、Azure Face 認識サービスとの通信に必要なメソッドをホストすることです。 

- サービスは、キャプチャイメージを送信した後、それを分析して内の顔を識別し、既知のユーザーに属しているかどうかを判断します。 
- 既知の人が見つかると、このクラスの名前が UI テキストとしてシーンに表示されます。

*FaceAnalysis* クラスを作成するには、次のようにします。

 1. [プロジェクト] パネルにある [*アセット] フォルダー* を右クリックし、[フォルダーの **作成**] をクリックし  >  ます。 フォルダー **スクリプト** を呼び出します。 

    ![FaceAnalysis クラスを作成します。](images/AzureLabs-Lab4-22.png)

2.  先ほど作成したフォルダーをダブルクリックして開きます。 
3.  フォルダー内を右クリックし、[   >  **C# スクリプト** の作成] をクリックします。 スクリプト *FaceAnalysis* を呼び出します。 
4.  新しい *FaceAnalysis* スクリプトをダブルクリックして、Visual Studio 2017 で開きます。
5.  *FaceAnalysis* クラスの上に次の名前空間を入力します。

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  次に、deserialising に使用されるすべてのオブジェクトを追加する必要があります。 これらのオブジェクトは、 *FaceAnalysis* スクリプトの **外側**(下かっこの下) に追加する必要があります。 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. *Start ()* および *Update ()* メソッドは使用されないため、ここで削除します。 

8.  *FaceAnalysis* クラス内で、次の変数を追加します。

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > **キー** および **ユーザーをサービスキーで置き換え**、前に作成したグループの Id に置き換えます。

9.  Initialises *()* メソッドを追加します。このメソッドは、クラスを作成し、 *Imagecapture* クラスをメインカメラに追加して、ラベルの作成メソッドを呼び出します。

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. *CreateLabel ()* メソッドを追加します。このメソッドは、分析結果を表示する *Label* オブジェクトを作成します。

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. 検出さ *れた* *GetImageAsByteArray ()* メソッドを追加します。 前者は、送信されたイメージで考えられる顔を検出するように顔認識サービスに要求します。後者の場合、キャプチャしたイメージをバイト配列に変換する必要があります。

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. *IdentifyFaces ()* メソッドを追加します。このメソッドは、送信されたイメージで以前に検出された既知の顔を識別するように *顔認識サービス* に要求します。 この要求は、識別されたユーザーの id を返しますが、名前は返しません。

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialize to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. *Getperson ()* メソッドを追加します。 このメソッドは、person id を指定することで、 *顔認識サービス* に対して、識別された人物の名前を返すよう要求します。

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  Unity エディターに戻る前に、変更を **保存** してください。
15.  Unity エディターで、[プロジェクト] パネルの [スクリプト] フォルダーから、[ *階層] パネル* のメインカメラオブジェクトに FaceAnalysis スクリプトをドラッグします。 新しいスクリプトコンポーネントがメインカメラに追加されます。 

![FaceAnalysis をメインカメラに配置する](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>第7章-ImageCapture クラスを作成する

*Imagecapture* クラスの目的は、 *Azure 顔認識サービス* との通信に必要なメソッドをホストして、キャプチャするイメージを分析し、そこで顔を特定し、既知のユーザーに属しているかどうかを判断することです。 既知の人が見つかると、このクラスの名前が UI テキストとしてシーンに表示されます。

*Imagecapture* クラスを作成するには、次のようにします。
 
1.  先ほど作成した **Scripts** フォルダー内を右クリックし、[ **作成**]、[ **C# スクリプト**] の順にクリックします。 スクリプト *Imagecapture* を呼び出します。 
2.  新しい *Imagecapture* スクリプトをダブルクリックして、Visual Studio 2017 で開きます。
3.  ImageCapture クラスの上に次の名前空間を入力します。

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  *Imagecapture* クラス内で、次の変数を追加します。

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  クラスを初期化するために必要な起動前 *()* および *開始 ()* メソッドを追加し、HoloLens がユーザーのジェスチャをキャプチャできるようにします。

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  ユーザーが *Tap* ジェスチャを実行したときに呼び出される *TapHandler ()* を追加します。

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  次のように、 *Executeimagecapの Andanalysis ()* メソッドを追加します。これにより、イメージキャプチャのプロセスが開始されます。

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  写真キャプチャプロセスが完了したときに呼び出されるハンドラーを追加します。

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. Unity エディターに戻る前に、変更を **保存** してください。

## <a name="chapter-8---building-the-solution"></a>第8章-ソリューションのビルド

アプリケーションの徹底的なテストを実行するには、アプリケーションを HoloLens にサイドロードする必要があります。

これを行う前に、次のことを確認してください。

-   章3で説明したすべての設定が正しく設定されています。 
-   スクリプト *FaceAnalysis* は、メインカメラオブジェクトにアタッチされます。 
-   **認証キー** と **グループ Id** の両方が *FaceAnalysis* スクリプト内で設定されています。

この時点で、ソリューションをビルドする準備ができました。 ソリューションがビルドされると、アプリケーションをデプロイする準備が整います。

ビルドプロセスを開始するには:

1.  [ファイル]、[保存] の順にクリックして、現在のシーンを保存します。
2.  [ファイル]、[ビルドの設定]、[開いているシーンの追加] の順にクリックします。
3.  Unity C# プロジェクトをティックするようにしてください。

    ![Visual Studio ソリューションをデプロイする](images/AzureLabs-Lab4-24.png)

4.  ビルドを押します。 これにより、Unity はエクスプローラーウィンドウを起動します。このウィンドウでは、アプリをビルドするフォルダーを作成して選択する必要があります。 Unity プロジェクト内でこのフォルダーを作成し、アプリを呼び出します。 次に、アプリフォルダーを選択し、[フォルダーの選択] をクリックします。 
5.  Unity は、アプリフォルダーにプロジェクトのビルドを開始します。 
6.  Unity のビルドが完了すると (時間がかかる場合があります)、ビルドの場所でファイルエクスプローラーウィンドウが開きます。

    ![Visual Studio からソリューションをデプロイする](images/AzureLabs-Lab4-25.png)

7.  アプリフォルダーを開き、新しいプロジェクトソリューションを開きます (前述のように、MR_FaceRecognition .sln)。


## <a name="chapter-9---deploying-your-application"></a>第9章-アプリケーションのデプロイ

HoloLens に展開するには:

1.  Hololens が **開発者モード** になっていることを確認するには、HOLOLENS の IP アドレス (リモートデプロイ用) が必要です。 これを行うには、次の手順を実行します。

    1. HoloLens を装着した後、 **設定** を開きます。
    2. **[Network & Internet > Wi-Fi > 詳細オプション]** にアクセスします。
    3. **IPv4** アドレスをメモしておきます。
    4. 次に、[**設定**] に戻り、**開発者向けの & セキュリティ > を更新** します。 
    5. 開発者モードをに設定します。

2.  新しい Unity ビルド ( *アプリ* フォルダー) に移動し、 *Visual Studio* でソリューションファイルを開きます。
3.  ソリューション構成で、[ **デバッグ**] を選択します。
4.  ソリューションプラットフォームで、[ **x86**、 **リモートコンピューター**] を選択します。 

    ![ソリューション構成の変更](images/AzureLabs-Lab4-26.png)
 
5.  [ **ビルド] メニュー** の [ソリューションの **配置**] をクリックして、アプリケーションを HoloLens にサイドロードします。
6.  アプリが HoloLens にインストールされているアプリの一覧に表示され、起動できる状態になります。

> [!NOTE]
> イマーシブヘッドセットにデプロイするには **、ソリューションプラットフォーム** を *ローカルコンピューター* に設定し、**プラットフォーム** として *x86* を使用して、**構成** を [*デバッグ*] に設定します。 次に、[ **ビルド] メニュー** の [ *ソリューションの配置*] をクリックして、ローカルコンピューターに配置します。 


## <a name="chapter-10---using-the-application"></a>章 10-アプリケーションの使用

1.  HoloLens を装着し、アプリを起動します。
2.  *Face API* に登録したユーザーを確認します。 次のことを確認してください。

    -  人の顔は遠くすぎて明確に見えません。
    -  環境の光源が暗すぎません

3.  Tap ジェスチャを使用して、人物の写真をキャプチャします。
4.  アプリが分析要求を送信し、応答を受信するまで待ちます。
5.  人が正常に認識された場合、ユーザー名は UI テキストとして表示されます。
6.  数秒ごとに tap ジェスチャを使用して、キャプチャプロセスを繰り返すことができます。

## <a name="your-finished-azure-face-api-application"></a>完成した Azure Face API アプリケーション

これで、Azure Face 認識サービスを活用してイメージ内の顔を検出し、既知の顔を識別する、mixed reality アプリを構築しました。

![このコースの完了の結果](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>ボーナス演習

### <a name="exercise-1"></a>演習1

**Azure Face API** は、1つのイメージで最大64の顔を検出するのに十分な性能を備えています。 アプリケーションを拡張して、他の多くの人の間で2つまたは3つの顔を認識できるようにします。

### <a name="exercise-2"></a>演習2

**Azure Face API** では、すべての種類の属性情報を返すこともできます。 これをアプリケーションに統合します。 これは、 [Emotion API](https://azure.microsoft.com/services/cognitive-services/emotion/)と組み合わせると、さらに興味深いものになる可能性があります。
