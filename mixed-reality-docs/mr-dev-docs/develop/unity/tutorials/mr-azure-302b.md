---
title: MR と Azure 302b-カスタムビジョン
description: このコースでは、機械学習モデルをトレーニングし、トレーニング済みのモデルを使用して、mixed reality アプリケーション内で類似のオブジェクトを認識する方法を学習します。
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, チュートリアル, api, カスタムビジョン, hololens, イマーシブ, vr
ms.openlocfilehash: 857cdc00daa94db5bb4d4fda1d5adfcf0ba28822
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91688122"
---
# <a name="mr-and-azure-302b-custom-vision"></a>MR と Azure 302b:カスタム ビジョン

<br>

>[!NOTE]
>Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。  そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。  これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは " **_ありません_** "。  これらは、サポートされているデバイス上で継続して動作するように、保守されます。 今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。  この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。

<br>


このコースでは、混合現実アプリケーションで Azure Custom Vision の機能を使用して、提供されたイメージ内のカスタムビジュアルコンテンツを認識する方法を学習します。

このサービスでは、オブジェクトイメージを使用して機械学習モデルをトレーニングすることができます。 次に、トレーニング済みのモデルを使用して類似のオブジェクトを認識します。これは、Microsoft HoloLens のカメラキャプチャや、PC for イマーシブ (VR) ヘッドセットに接続されたカメラによって提供されます。

![コースの結果](images/AzureLabs-Lab302b-00.png)

Azure Custom Vision は、開発者がカスタムイメージ分類子を構築できる Microsoft 認知サービスです。 これらの分類子を新しいイメージと共に使用して、新しいイメージ内のオブジェクトを認識したり、分類したりすることができます。 このサービスでは、簡単で使いやすいオンラインポータルを使用して、プロセスを効率化できます。 詳細については、 [Azure Custom Vision Service のページ](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)を参照してください。

このコースが完了すると、2つのモードで動作できる mixed reality アプリケーションが完成します。

-   **分析モード** : イメージをアップロードし、タグを作成し、さまざまなオブジェクト (この場合はマウスとキーボード) を認識するようにサービスをトレーニングすることによって、Custom Vision Service を手動で設定します。 次に、カメラを使用してイメージをキャプチャする HoloLens アプリを作成し、実際の環境でそれらのオブジェクトを認識します。

-   **トレーニングモード** : アプリで "トレーニングモード" を有効にするコードを実装します。 トレーニングモードでは、HoloLens のカメラを使用してイメージをキャプチャし、キャプチャしたイメージをサービスにアップロードして、カスタムビジョンモデルをトレーニングすることができます。

このコースでは、Custom Vision Service から Unity ベースのサンプルアプリケーションに結果を取得する方法について説明します。 これらの概念は、構築しているカスタムアプリケーションに適用する必要があります。

## <a name="device-support"></a>デバイス サポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="../../../hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 302b:カスタム ビジョン</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
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
- [Windows Mixed Reality イマーシブ (VR) ヘッドセット](../../../discover/immersive-headset-hardware-details.md)または開発者モードを有効にした[Microsoft HoloLens](../../../hololens-hardware-details.md)
- PC に接続されているカメラ (イマーシブヘッドセット開発用)
- Azure セットアップと Custom Vision API の取得のためのインターネットアクセス
- Custom Vision Service が認識するオブジェクトごとに、少なくとも5つのイメージ (10) が推奨されます。 必要に応じて、 [このコースで既に提供されているイメージ (コンピューターマウスとキーボード) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)を使用できます。

## <a name="before-you-start"></a>開始する前に

1.  このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。
2.  HoloLens をセットアップしてテストします。 HoloLens のセットアップをサポートする必要がある場合は、 [hololens セットアップに関する記事にアクセスして](https://docs.microsoft.com/hololens/hololens-setup)ください。 
3.  新しい HoloLens アプリの開発を開始するときは、調整とセンサーのチューニングを実行することをお勧めします (ユーザーごとにこれらのタスクを実行するのに役立つ場合があります)。 

調整の詳細については、 [「HoloLens の調整に関する記事へのリンク」を](../../../calibration.md#hololens-2)参照してください。

センサーチューニングの詳細については、 [HoloLens センサーチューニングに関する記事へのリンクを](../../../sensor-tuning.md)参照してください。

## <a name="chapter-1---the-custom-vision-service-portal"></a>章 1-Custom Vision Service ポータル

Azure で *Custom Vision Service* を使用するには、アプリケーションで使用できるようにサービスのインスタンスを構成する必要があります。

1.  最初に、 [ *Custom Vision Service* メインページに移動](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)します。

2.  **[Get Started]** (開始) ボタンをクリックします。

    ![Custom Vision Service を使ってみる](images/AzureLabs-Lab302b-01.png)

3.  *Custom Vision Service* ポータルにサインインします。

    ![ポータルへのサインイン](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。 このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。

4.  初めてログインした後は、 *サービスパネルの使用条件* を確認するメッセージが表示されます。 条件に同意するには、チェックボックスをオンにします。 [ **同意** する] をクリックします。

    ![サービス使用条件](images/AzureLabs-Lab302b-03.png)

5.  使用条件に同意すると、ポータルの [ *プロジェクト* ] セクションに移動します。 [ **新しいプロジェクト** ] をクリックします。

    ![新しいプロジェクトの作成](images/AzureLabs-Lab302b-04.png)

6.  右側にタブが表示され、プロジェクトのフィールドを指定するように求められます。

    1.  プロジェクトの *名前* を挿入します。

    2.  プロジェクトの *説明* を挿入します ( *省略可能* )。

    3.  リソースグループを選択するか、新しい *リソースグループ* を作成します。 リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。 1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのコースなど) を共通のリソースグループに保持することをお勧めします。

    4. プロジェクトの *種類* を **分類** に設定する
    
    5. *ドメイン* を **全般** として設定します。

        ![ドメインを設定する](images/AzureLabs-Lab302b-05.png)

        > Azure リソースグループの詳細については、 [リソースグループ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)に関する記事をご覧ください。

7.  完了すると、[プロジェクトの **作成** ] をクリックすると、[Custom Vision Service、プロジェクト] ページにリダイレクトされます。

## <a name="chapter-2---training-your-custom-vision-project"></a>第2章-Custom Vision プロジェクトのトレーニング

Custom Vision ポータルでは、主な目的は、イメージ内の特定のオブジェクトを認識するようにプロジェクトをトレーニングすることです。 アプリケーションで認識するオブジェクトごとに、少なくとも5つのイメージが必要ですが、10 (10) が推奨されます。 [このコースに用意されているイメージ (コンピューターマウスとキーボード) を使用でき](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)ます。 

Custom Vision Service プロジェクトをトレーニングするには:

1.  [タグ] の横にあるボタンをクリックし **+** **ます。**

    ![新しいタグを追加する](images/AzureLabs-Lab302b-06.png)

2.  認識するオブジェクトの **名前** を追加します。 **[Save]** をクリックします。

    ![オブジェクト名を追加して保存](images/AzureLabs-Lab302b-07.png)

3.  **タグ** が追加されていることがわかります (表示するには、ページの再読み込みが必要になる場合があります)。 まだ確認されていない場合は、新しいタグの横にあるチェックボックスをクリックします。

    ![新しいタグを有効にする](images/AzureLabs-Lab302b-08.png)

4.  ページの中央にある [ **イメージの追加** ] をクリックします。

    ![画像の追加](images/AzureLabs-Lab302b-09.png)

5.  [ **ローカルファイルの参照** ] をクリックし、アップロードするイメージを検索して選択します。最小値は 5 (5) です。 これらのイメージには、トレーニングするオブジェクトが含まれている必要があることに注意してください。

    > [!NOTE]
    >  アップロードには、一度に複数のイメージを選択できます。

6.  タブに画像が表示されたら、 **[マイタグ** ] ボックスで適切なタグを選択します。

    ![タグの選択](images/AzureLabs-Lab302b-10.png)

7.  [ **ファイルのアップロード** ] をクリックします。 ファイルのアップロードが開始されます。 アップロードの確認が完了したら、[ **完了** ] をクリックします。

    ![ファイルのアップロード](images/AzureLabs-Lab302b-11.png)

8.  同じプロセスを繰り返して、 **キーボード** という名前の新しい **タグ** を作成し、適切な写真をアップロードします。 新しいタグを作成したら、 *マウス* を **オフ** にして、[イメージの *追加* ] ウィンドウを表示します。

9.  両方のタグが設定されたら、[ **トレーニング** ] をクリックすると、最初のトレーニングイテレーションがビルドを開始します。

    ![トレーニングイテレーションの有効化](images/AzureLabs-Lab302b-12.png)

10. ビルドが完了すると、[既定と **予測 URL** の **作成** ] という2つのボタンが表示されます。 [ **既定値** に設定] をクリックし、[ **予測 URL** ] をクリックします。

    ![既定の URL と予測 URL を作成する](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > このから提供されるエンドポイント URL は、既定としてマークされている *イテレーション* のいずれかに設定されます。 そのため、後で新しい *イテレーション* を作成して既定として更新する場合は、コードを変更する必要はありません。

11. *予測 url* をクリックしたら、 *メモ帳* を開き、 **url** と **予測キー** をコピーして貼り付けます。これにより、後でコード内で必要になったときに取得できるようになります。

    ![URL と予測キーのコピーと貼り付け](images/AzureLabs-Lab302b-14.png)

12. 画面の右上にある **歯車** をクリックします。

    ![歯車アイコンをクリックして設定を開く](images/AzureLabs-Lab302b-15.png)

13. **トレーニングキー** をコピーし、 *メモ帳* に貼り付けて、後で使用できるようにします。

    ![トレーニングキーのコピー](images/AzureLabs-Lab302b-16.png)

14. また、 **プロジェクト Id** もコピーし、 *メモ帳* ファイルに貼り付けて、後で使用できるようにします。

    ![プロジェクト id のコピー](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a>章 3-Unity プロジェクトの設定

次に示すのは、mixed reality で開発するための一般的な設定です。そのため、他のプロジェクトに適したテンプレートです。

1.  *Unity* を開き、[ **新規** ] をクリックします。

    ![新しい Unity プロジェクトを作成する](images/AzureLabs-Lab302b-17.png)

2.  ここで、Unity プロジェクト名を指定する必要があります。 **AzureCustomVision を挿入します。** プロジェクトテンプレートが **3d** に設定されていることを確認します。 場所を適切な **場所** に設定します (ルートディレクトリの方が適していることに注意してください)。 次に、[ **プロジェクトの作成** ] をクリックします。

    ![プロジェクト設定の構成](images/AzureLabs-Lab302b-18.png)

3.  Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。 [ **Edit*  >  *設定* の編集* ] に移動し、新しいウィンドウで [ **外部ツール** ] に移動します。 **外部スクリプトエディター** を **Visual Studio 2017** に変更します。 [ **基本設定** ] ウィンドウを閉じます。

    ![外部ツールの構成](images/AzureLabs-Lab302b-19.png)

4.  次に、[ **ファイル > ビルド設定** ] に移動し、[ **ユニバーサル Windows プラットフォーム** ] を選択します。次に、[ **プラットフォームの切り替え** ] ボタンをクリックして選択内容を適用します。

    ![ビルド設定の構成 ](images/AzureLabs-Lab302b-20.png)

5.  それでも **ファイル > ビルド設定** を行い、次のことを確認します。

    1.  **ターゲットデバイス** が **HoloLens** に設定されています

        > イマーシブヘッドセットの場合は、 **ターゲットデバイス** を *任意のデバイス* に設定します。
        
    2.  **ビルドの種類** が **D3D** に設定されています
    3.  **SDK** は最新の **インストール** に設定されています
    4.  **Visual Studio のバージョン** が、 **インストールされている最新** バージョンに設定されています
    5.  **ビルドと実行** は **ローカルコンピューター** に設定されています
    6.  シーンを保存し、ビルドに追加します。 

        1. これを行うには、[開いている **シーンの追加** ] を選択します。 保存ウィンドウが表示されます。

            ![開いているシーンをビルドリストに追加](images/AzureLabs-Lab302b-21.png)

        2. この新しいフォルダーを作成し、今後のシーンに加えて、[ **新しいフォルダー** ] ボタンを選択します。新しいフォルダーを作成するには、名前を「 **シーン** 」にします。

            ![新しいシーンフォルダーの作成](images/AzureLabs-Lab302b-22.png)

        3. 新しく作成した [ **シーン** ] フォルダーを開き、[ *ファイル名:* テキスト] フィールドに「 **CustomVisionScene** 」と入力し、[ **保存** ] をクリックします。

            ![新しいシーンファイルに名前を指定](images/AzureLabs-Lab302b-23.png)

            > Unity プロジェクトに関連付けられている必要があるため、Unity のシーンを *Assets* フォルダー内に保存する必要があります。 Unity プロジェクトを構成する一般的な方法は、シーンフォルダー (およびその他の同様のフォルダー) を作成することです。
            
    7.  それ以外の設定は、[ *ビルド設定* ] の [既定] のままにしておきます。

        ![既定のビルド設定](images/AzureLabs-Lab302b-24.png)

6.  [ *ビルドの設定* ] ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 *インスペクター* が配置されている領域の関連パネルが開きます。

7. このパネルでは、いくつかの設定を確認する必要があります。

    1.  [ **その他の設定** ] タブで、次のようにします。

        1.  **Scripting Runtime のバージョン** は **実験的 (.Net 4.6 と同等)** である必要があります。これにより、エディターを再起動する必要が生じます。

        2. **バックエンド** は **.net** である必要があります

        3. **API 互換性レベル** は **.net 4.6** である必要があります

        ![API compantiblity の設定](images/AzureLabs-Lab302b-25.png)

    2.  [ **発行の設定** ] タブの [ **機能** ] で、次の項目を確認します。

        1. **InternetClient**

        2.  **Web カメラ**

        3. **マイク**

        ![発行の設定を構成する](images/AzureLabs-Lab302b-26.png)

    3.  パネルの下にある [ **XR settings** (発行の **設定** ] の下にあります) で、[ **サポートされている仮想現実** ] をティックし、 **Windows Mixed reality SDK** が追加されていることを確認します。

    ![XR 設定の構成](images/AzureLabs-Lab302b-27.png)

8.  *ビルド設定* に戻る *Unity C \# プロジェクト* はグレーで表示されなくなりました。この横にあるチェックボックスをオンにします。

9.  [ビルド設定] ウィンドウを閉じます。

10.  シーンとプロジェクトを保存します ([ **ファイル] > [シーン/ファイルの保存] > [プロジェクトの保存** ])。


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a>章 4-Unity での Newtonsoft DLL のインポート

> [!IMPORTANT]
> このコースの *Unity セットアップ* コンポーネントをスキップし、コードに直接進む場合は、この [Azure-MR-302b](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage)をダウンロードし、 [**カスタムパッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてから、 [第6章](#chapter-6---create-the-customvisionanalyser-class)から続行してください。

このコースでは、 **Newtonsoft** ライブラリを使用する必要があります。これは、アセットに DLL として追加できます。 このライブラリを含むパッケージは、 [このリンクからダウンロードでき](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage)ます。
Newtonsoft ライブラリをプロジェクトにインポートするには、このコースに付属している Unity パッケージを使用します。

1.  [ **アセット*  >  *インポート**パッケージ* の  >  *カスタム**パッケージ** ] メニューオプションを使用して、 *unitypackage* を Unity に追加します。

2.  ポップアップ表示された [ **Unity パッケージのインポート** ] ボックスで、 **プラグイン** (およびそれを含む) のすべてが選択されていることを確認します。

    ![すべてのパッケージアイテムをインポートする](images/AzureLabs-Lab302b-28.png)

3.  [ **インポート** ] ボタンをクリックして、プロジェクトに項目を追加します。

4.  プロジェクトビューの [ **プラグイン** ] の下にある **newtonsoft** フォルダーにアクセスし、プラグインの [ *Newtonsoft.Js* ] を選択します。

    ![Newtonsoft プラグインを選択します。](images/AzureLabs-Lab302b-29.png)

5.  [ *Newtonsoft.Jsのプラグイン* ] を選択した状態で、任意の **プラットフォーム** が **オフ** になっていることを確認し、[ **wsaplayer** ] も **オフ** になっていることを確認して、[ **適用** ] をクリックします。 これは、ファイルが正しく構成されていることを確認するためのものです。

    ![Newtonsoft プラグインの構成](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > これらのプラグインをマークすると、Unity エディターでのみ使用するように構成されます。 WSA フォルダーには、Unity からプロジェクトがエクスポートされた後に使用される、異なるセットがあります。

6.  次に、 **Newtonsoft** フォルダー内の **WSA** フォルダーを開く必要があります。 先ほど構成したものと同じファイルのコピーが表示されます。 ファイルを選択し、インスペクターで次のことを確認します。
    -   **すべてのプラットフォーム** が **オフ** になっています 
    -   **only** **wsaplayer** のみが **チェック** されます
    -   **処理** されないかどうかを **確認** します

    ![Newtonsoft plugin platform の設定を構成する](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a>第5章-カメラの設定

1.  [階層] パネルで、 *メインカメラ* を選択します。

2.  選択すると、 *メインカメラ* のすべてのコンポーネントが [ *インスペクター] パネル* に表示されます。

    1.  *カメラ* オブジェクトは **メインカメラ** という名前にする必要があります (スペルに注意してください)。

    2.  メインカメラの **タグ** は、 **maincamera** に設定する必要があります (スペルに注意してください)。

    3.  **変換位置** が **0、0、0** に設定されていることを確認します。

    4.  **クリアフラグ** を **純色** に設定します (イマーシブヘッドセットの場合は無視します)。

    5.  カメラコンポーネントの **背景** 色を **黒、アルファ 0 (16 進コード: #00000000)** に設定します (イマーシブヘッドセットの場合は無視します)。

    ![カメラコンポーネントのプロパティの構成](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a>Chapter 6-CustomVisionAnalyser クラスを作成する

この時点で、コードを記述する準備ができました。

最初に、 *CustomVisionAnalyser* クラスを使用します。

> [!NOTE]
> 次に示すコードで行われた **Custom Vision Service** の呼び出しは、 **Custom Vision REST API** を使用して行われます。 これを使用すると、この API を実装して使用する方法を確認できます (独自のものを実装する方法を理解するために役立ちます)。 Microsoft では、サービスの呼び出しを行うために使用できる **CUSTOM VISION SERVICE SDK** を提供していることに注意してください。 詳細については、 [CUSTOM VISION SERVICE SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) に関する記事をご覧ください。

このクラスの役割は次のとおりです。

-   バイト配列としてキャプチャされた最新のイメージを読み込んでいます。

-   分析のために、Azure *Custom Vision Service* インスタンスにバイト配列を送信しています。

-   JSON 文字列として応答を受信しています。

-   応答を逆シリアル化し、結果の *予測* を *SceneOrganiser* クラスに渡します。これにより、応答の表示方法が決まります。

このクラスを作成するには:

1.  [ *プロジェクト] パネル* にある [ *アセット] フォルダー* を右クリックし、[ **> フォルダーの作成** ] をクリックします。 フォルダー **スクリプト** を呼び出します。

    ![スクリプトフォルダーの作成](images/AzureLabs-Lab302b-33.png)

2.  作成したばかりのフォルダーをダブルクリックして開きます。

3.  フォルダー内を右クリックし、[ **Create**  >  **C \# スクリプト** の作成] をクリックします。 スクリプトに *CustomVisionAnalyser* という名前を指定します。

4.  新しい *CustomVisionAnalyser* スクリプトをダブルクリックして、 **Visual Studio** で開きます。

5.  ファイルの先頭にある名前空間を次のように更新します。

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  *CustomVisionAnalyser* クラスに、次の変数を追加します。

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > **予測キー** を **predictionKey** 変数に挿入し、 **予測エンドポイント** を **predictionEndpoint** 変数に挿入してください。 これらは、コースの前の *メモ帳* にコピーしました。

7.  インスタンス変数を初期化するには、起動前 **()** のコードを追加する必要があります。

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  **Start ()** および **Update ()** メソッドを削除します。

9.  次に、コルーチン (static **GetImageAsByteArray ()** メソッドをその下に追加) を追加します。これにより、 *imagecapture* クラスによってキャプチャされたイメージの分析結果が得られます。

    > [!NOTE]
    > **分析 Seimagecapture** コルーチンには、まだ作成していない *SceneOrganiser* クラスの呼び出しがあります。 そのため、 **これらの行はコメントの付いたままに** しておきます。

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
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

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
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

10.  **Unity** に戻る前に、変更内容を **Visual Studio** に保存してください。

## <a name="chapter-7---create-the-customvisionobjects-class"></a>第7章-CustomVisionObjects クラスの作成

ここで作成するクラスは、 *CustomVisionObjects* クラスです。

このスクリプトには、 *Custom Vision Service* に対する呼び出しをシリアル化および逆シリアル化するために、他のクラスによって使用される多数のオブジェクトが含まれています。

> [!WARNING]
> 次の JSON 構造が [*Custom Vision 予測*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290)v2.0 で動作するように設定されているため、Custom Vision Service によって提供されるエンドポイントをメモしておくことが重要です。 バージョンが異なる場合は、以下の構造を更新する必要がある場合があります。

このクラスを作成するには:

1.  **Scripts** フォルダー内を右クリックし、[ **Create**  >  **C \# Script** ] をクリックします。 スクリプト *CustomVisionObjects* を呼び出します。

2.  新しい **CustomVisionObjects** スクリプトをダブルクリックして、 **Visual Studio** で開きます。

3.  ファイルの先頭に次の名前空間を追加します。

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  *CustomVisionObjects* クラス内の **Start ()** および **Update ()** メソッドを削除します。これで、このクラスは空になります。

5.  *CustomVisionObjects* クラスの **外** に次のクラスを追加します。 これらのオブジェクトは、応答データをシリアル化および逆シリアル化するために *Newtonsoft* ライブラリによって使用されます。

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
    /// JSON of Images submitted
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
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a>章 8-VoiceRecognizer クラスを作成する

このクラスは、ユーザーからの音声入力を認識します。

このクラスを作成するには:

1.  **Scripts** フォルダー内を右クリックし、[ **Create**  >  **C \# Script** ] をクリックします。 スクリプト *VoiceRecognizer* を呼び出します。

2.  新しい **VoiceRecognizer** スクリプトをダブルクリックして、 **Visual Studio** で開きます。

3.  *VoiceRecognizer* クラスの上に次の名前空間を追加します。

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  次に、 *Start ()* メソッドの上に、 *VoiceRecognizer* クラス内に次の変数を追加します。

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  起動前 **()** および **開始 ()** メソッドを追加します。後者の場合、タグをイメージに関連付けるときに認識されるユーザー *キーワード* が設定されます。

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
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  **Update ()** メソッドを削除します。

7.  次のハンドラーを追加します。これは、音声入力が認識されるたびに呼び出されます。

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  **Unity** に戻る前に、変更内容を **Visual Studio** に保存してください。

> [!NOTE]
> エラーが発生する可能性のあるコードについては気にしないでください。これにより、後でクラスを修正することになります。

## <a name="chapter-9---create-the-customvisiontrainer-class"></a>第9章-CustomVisionTrainer クラスの作成

このクラスは、一連の web 呼び出しをチェーンして、 *Custom Vision Service* をトレーニングします。 各呼び出しの詳細については、コードの上に説明します。

このクラスを作成するには:

1.  **Scripts** フォルダー内を右クリックし、[ **Create**  >  **C \# Script** ] をクリックします。 スクリプト *CustomVisionTrainer* を呼び出します。

2.  新しい *CustomVisionTrainer* スクリプトをダブルクリックして、 **Visual Studio** で開きます。

3.  *CustomVisionTrainer* クラスの上に次の名前空間を追加します。

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  次に、 **Start ()** メソッドの上に、 *CustomVisionTrainer* クラス内に次の変数を追加します。 

    > [!NOTE]
    > ここで使用されているトレーニング URL は *Custom Vision トレーニング 1.2* のドキュメントに記載されており、の構造は次のとおりです。 https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/  
    > 詳細については、 [*Custom Vision トレーニング v2.0 リファレンス API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)」を参照してください。

    > [!WARNING]
    > Custom Vision Service がトレーニングモード用に提供するエンドポイントをメモしておくことが重要です。これは、( **CustomVisionObjects** クラス内で使用される) JSON 構造が [*Custom Vision トレーニング*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)v1.0 で動作するように設定されているためです。 バージョンが異なる場合は、 *オブジェクト* の構造を更新することが必要になる場合があります。

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > 前にメモしておいた、 **サービスキー** (トレーニングキー) 値と **プロジェクト Id** 値を必ず追加してください。これらは、コースの [前の段階でポータルから収集した値です (第2章、手順10以降)](#chapter-2---training-your-custom-vision-project)。

5.  次の **Start ()** および「起動前 **()** 」の各メソッドを追加します。 これらのメソッドは初期化時に呼び出され、UI を設定するための呼び出しを含みます。

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
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  **Update ()** メソッドを削除します。 このクラスは、このクラスを必要としません。

7.  **Requesttagselection ()** メソッドを追加します。 このメソッドは、イメージをキャプチャしてデバイスに格納し、 *Custom Vision Service* に送信してトレーニングする準備ができたときに最初に呼び出されるメソッドです。 このメソッドは、トレーニング UI に、キャプチャされたイメージをタグ付けするためにユーザーが使用できる一連のキーワードを表示します。 また、 *VoiceRecognizer* クラスに対して、ユーザーの音声入力のリッスンを開始するように通知します。

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  **Verifytag ()** メソッドを追加します。 このメソッドは、 **VoiceRecognizer** クラスによって認識される音声入力を受け取り、その有効性を確認してから、トレーニングプロセスを開始します。

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  **SubmitImageForTraining ()** メソッドを追加します。 このメソッドは Custom Vision Service トレーニングプロセスを開始します。 最初の手順では、ユーザーからの検証済み音声入力に関連付けられているサービスから **タグ Id** を取得します。 **タグ Id** がイメージと共にアップロードされます。

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. **TrainCustomVisionProject ()** メソッドを追加します。 イメージが送信され、タグが付けられると、このメソッドが呼び出されます。 これにより、サービスに送信された以前のすべてのイメージに加え、アップロードしたイメージを使用してトレーニングされる新しいイテレーションが作成されます。 トレーニングが完了すると、このメソッドはメソッドを呼び出して、新しく作成された **イテレーション** を **既定** として設定します。これにより、分析に使用するエンドポイントがトレーニング済みの最新のイテレーションになります。

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. **Setdefaultiterfrom()** メソッドを追加します。 このメソッドは、以前に作成され、トレーニングされたイテレーションを *既定* として設定します。 完了すると、このメソッドは、サービス内の既存のイテレーションを削除する必要があります。 このコースの執筆時点では、サービスに同時に存在できるイテレーションは最大で10個までに制限されています。

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. **DeletePreviousIteration ()** メソッドを追加します。 このメソッドは、以前の既定以外のイテレーションを見つけて削除します。

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. このクラスに最後に追加するメソッドは、 **GetImageAsByteArray ()** メソッドです。このメソッドは、キャプチャしたイメージをバイト配列に変換するために、web 呼び出しで使用されます。

    ```csharp
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

14. **Unity** に戻る前に、変更内容を **Visual Studio** に保存してください。

## <a name="chapter-10---create-the-sceneorganiser-class"></a>Chapter 10-SceneOrganiser クラスの作成

このクラスは次のことを行います。

-   メインカメラに接続するための **Cursor** オブジェクトを作成します。

-   サービスが実際のオブジェクトを認識したときに表示される **ラベル** オブジェクトを作成します。

-   適切なコンポーネントをアタッチして、メインカメラを設定します。

-   **分析モード** では、実行時に、メインカメラの位置を基準とした適切なワールド空間でラベルが生成され、Custom Vision Service から受信したデータが表示されます。

-   **トレーニングモード** では、トレーニングプロセスのさまざまな段階を表示する UI を生成します。

このクラスを作成するには:

1.  **Scripts** フォルダー内を右クリックし、[ **Create**  >  **C \# Script** ] をクリックします。 スクリプトに *SceneOrganiser* という名前を指定します。

2.  新しい *SceneOrganiser* スクリプトをダブルクリックして、 **Visual Studio** で開きます。

3.  必要な名前空間は1つだけです。 *SceneOrganiser* クラスの上から他の名前空間を削除します。

    ```csharp
    using UnityEngine;
    ```

4.  次に、 **Start ()** メソッドの上に、 *SceneOrganiser* クラス内に次の変数を追加します。

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  **Start ()** および **Update ()** メソッドを削除します。

6.  変数のすぐ下に、起動前 **()** メソッドを追加します。このメソッドは、クラスを初期化し、シーンを設定します。

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  次に、メインカメラカーソルを作成して配置する **CreateCameraCursor ()** メソッドを追加し、 **CreateLabel ()** メソッドを追加して、 **分析ラベル** オブジェクトを作成します。

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. **SetCameraStatus ()** メソッドを追加します。このメソッドは、カメラの状態を提供するテキストメッシュを目的としたメッセージを処理します。

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. **PlaceAnalysisLabel ()** メソッドと **SetTagsToLastLabel ()** メソッドを追加します。これにより、Custom Vision Service のデータが生成され、シーンに表示されます。

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. 最後に、 **CreateTrainingUI ()** メソッドを追加します。これにより、アプリケーションがトレーニングモードのときにトレーニングプロセスの複数のステージを表示する UI が生成されます。 このメソッドは、カメラの状態オブジェクトを作成するためにも開花されます。

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. **Unity** に戻る前に、変更内容を **Visual Studio** に保存してください。

> [!IMPORTANT]
> 続行する前に、 **CustomVisionAnalyser** クラスを開き、 **AnalyseLastImageCaptured ()** メソッド内で次の行を *コメント* 解除します。
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a>第11章-ImageCapture クラスを作成する

次に作成するクラスは、 *Imagecapture* クラスです。

このクラスの役割は次のとおりです。

-   HoloLens カメラを使用してイメージをキャプチャし、 *アプリ* フォルダーに格納します。

-   ユーザーからの Tap ジェスチャを処理します。

-   アプリケーションを *分析* モードと *トレーニング* モードのどちらで実行するかを決定する *列挙* 値を保持する。

このクラスを作成するには:

1.  前に作成した **Scripts** フォルダーにアクセスします。

2.  フォルダー内を右クリックし、[ **Create > C \# Script** ] をクリックします。 スクリプトに「 *Imagecapture* 」という名前を指定します。

3.  新しい **Imagecapture** スクリプトをダブルクリックして、 **Visual Studio** で開きます。

4.  ファイルの先頭にある名前空間を次のように置き換えます。

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  次に、 **Start ()** メソッドの上に、 *imagecapture* クラス内に次の変数を追加します。

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
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  起動可能な **()** メソッドと **Start ()** メソッドのコードを追加する必要があります。

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
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

            // Subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  Tap ジェスチャが発生したときに呼び出されるハンドラーを実装します。

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > *分析* モードでは、 **TapHandler** メソッドはフォトキャプチャループを開始または停止するためのスイッチとして機能します。
    >
    > *トレーニング* モードでは、カメラからイメージをキャプチャします。
    >
    > カーソルが緑色の場合は、カメラを使用してイメージを撮影できることを意味します。
    >
    > カーソルが赤の場合、カメラがビジー状態であることを示します。

8.  アプリケーションがイメージキャプチャプロセスを開始してイメージを格納するために使用するメソッドを追加します。

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
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

9.  写真がキャプチャされ、分析の準備ができたときに呼び出されるハンドラーを追加します。 次に、コードが設定されているモードに応じて、結果が *CustomVisionAnalyser* または *CustomVisionTrainer* に渡されます。

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. **Unity** に戻る前に、変更内容を **Visual Studio** に保存してください。

11. すべてのスクリプトが完了したので、Unity エディターに戻り、[ **スクリプト** ] フォルダーの **SceneOrganiser** クラスをクリックして、 *階層パネル* の **メインカメラ** オブジェクトにドラッグします。

## <a name="chapter-12---before-building"></a>第12章-ビルド前

アプリケーションの徹底的なテストを実行するには、アプリケーションを HoloLens にサイドロードする必要があります。

これを行う前に、次のことを確認してください。

- [章 2](#chapter-2---training-your-custom-vision-project)で説明したすべての設定が正しく設定されています。

- **メインカメラ** の [インスペクター] パネルのすべてのフィールドが適切に割り当てられます。

- スクリプト **SceneOrganiser** は、 **メインカメラ** オブジェクトにアタッチされます。

- 必ず、 **予測キー** を **predictionKey** 変数に挿入してください。

- **予測エンドポイント** を **predictionEndpoint** 変数に挿入しました。

- **トレーニングキー** を *CustomVisionTrainer* クラスの **trainingKey** 変数に挿入しました。

- **プロジェクト ID** が *CustomVisionTrainer* クラスの **projectId** 変数に挿入されました。

## <a name="chapter-13---build-and-sideload-your-application"></a>第13章-アプリケーションのビルドとサイドロード

*ビルド* プロセスを開始するには:

1.  **ファイル > ビルド設定** にアクセスします。

2.  **Unity C \# プロジェクト** をティックします。

3.  [ **ビルド** ] をクリックします。 Unity は **エクスプローラー** ウィンドウを起動します。このウィンドウでは、アプリを作成するフォルダーを作成して選択する必要があります。 ここでそのフォルダーを作成し、「 **App** 」という名前を指定します。 次に、 **アプリ** フォルダーを選択し、[ **フォルダーの選択** ] をクリックします。

4.  Unity は、 **アプリ** フォルダーへのプロジェクトのビルドを開始します。

5.  Unity のビルドが完了すると (時間がかかる場合があります)、ビルドの場所で **ファイルエクスプローラー** ウィンドウを開きます (ウィンドウの上に常に表示されるとは限りませんが、新しいウィンドウが追加されたことが通知されます)。

HoloLens に展開するには:

1.  Hololens が **開発者モード** になっていることを確認するには、HOLOLENS の IP アドレス (リモートデプロイ用) が必要です。 これを行うには、次の手順を実行します。

    1.  HoloLens を装着した後、 **設定** を開きます。

    2.  [ **ネットワーク & インターネット**  >  **wi-fi**  >  **詳細オプション]** にアクセスします。

    3.  **IPv4** アドレスをメモしておきます。

    4.  次に、[ **設定** ] に戻り、 **Update & Security**  >  **開発者の** & セキュリティを更新します。

    5.  **開発者モードをに** 設定します。

2.  新しい Unity ビルド ( **アプリ** フォルダー) に移動し、 **Visual Studio** でソリューションファイルを開きます。

3.  *ソリューション構成* で、[ **デバッグ** ] を選択します。

4.  *ソリューションプラットフォーム* で、[ **X86、リモートコンピューター** ] を選択します。 リモートデバイスの **IP アドレス** (この場合は、ここでメモした HoloLens) を挿入するように求められます。

    ![IP アドレスの設定](images/AzureLabs-Lab302b-34.png)

5. [ **ビルド** ] メニューの [ **ソリューションの配置** ] をクリックして、アプリケーションを HoloLens にサイドロードします。

6. アプリが HoloLens にインストールされているアプリの一覧に表示され、起動できる状態になります。

> [!NOTE]
> イマーシブヘッドセットにデプロイするには **、ソリューションプラットフォーム** を *ローカルコンピューター* に設定し、 **プラットフォーム** として *x86* を使用して、 **構成** を [ *デバッグ* ] に設定します。 次に、[ **ビルド** ] メニュー項目を使用して [ *ソリューションの配置* ] を選択し、ローカルコンピューターに配置します。 

## <a name="to-use-the-application"></a>アプリケーションを使用するには:

*トレーニング* モードと *予測* モードの間でアプリの機能を切り替えるには、 *imagecapture* クラス内にある、起動前の **()** メソッドにある **appmode** 変数を更新する必要があります。

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
または
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

*トレーニング* モードの場合:

- **マウス** または **キーボード** を見て、 **Tap ジェスチャ** を使用します。

- 次に、タグの入力を求めるテキストが表示されます。

- **マウス** または **キーボード** のいずれかを言います。


*予測* モードの場合:

- オブジェクトを確認し、 **Tap ジェスチャ** を使用します。

- オブジェクトが検出され、確率が最も高い (これは正規化されている) ことを示すテキストが表示されます。

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a>第14章-Custom Vision モデルの評価と改善

サービスの精度を高めるには、予測に使用するモデルのトレーニングを続行する必要があります。 これは、 *トレーニング* と *予測* の両方のモードで新しいアプリケーションを使用することによって実現されます。後者の場合はポータルにアクセスする必要があります。これについては、この章で説明します。 モデルを継続的に改善するために、ポータルに何度も再訪問できるように準備してください。

1. Azure Custom Vision ポータルにもう一度移動します。プロジェクトが表示されたら、[ *予測* ] タブ (ページの上部中央) を選択します。

    ![[予測] タブの選択](images/AzureLabs-Lab302b-35.png)

2. アプリケーションの実行中にサービスに送信されたすべてのイメージが表示されます。 画像にマウスポインターを合わせると、その画像に対して行われた予測が表示されます。

    ![予測イメージの一覧](images/AzureLabs-Lab302b-36.png)

3. イメージの1つを選択して開きます。 開いた後、そのイメージの予測が右側に表示されます。 予測が適切で、このイメージをサービスのトレーニングモデルに追加する場合は、[ *マイタグ* ] 入力ボックスをクリックし、関連付けるタグを選択します。 操作が完了したら、右下にある [ *保存して閉じる* ] ボタンをクリックし、次の画像に進みます。

    ![開くイメージの選択](images/AzureLabs-Lab302b-37.png)

4. 画像のグリッドに戻ると、タグを追加した (および保存した) イメージが削除されます。 タグ付けされた項目がないと思われるイメージが見つかった場合は、そのイメージの目盛りをクリックし (複数のイメージに対してこれを実行できます)、グリッドページの右上隅にある [ *削除* ] をクリックすることで、イメージを削除できます。 次のポップアップで、[はい]、[ *削除* ]、または [ *いいえ* ] をクリックして、それぞれ削除を確認するか、キャンセルします。 

    ![イメージを削除する](images/AzureLabs-Lab302b-38.png)

5. 操作を続行する準備ができたら、右上にある緑色の [ *Train* ] ボタンをクリックします。 サービスモデルは、現在提供されているすべてのイメージでトレーニングされます (これにより、より正確になります)。 トレーニングが完了したら、[ *既定値* に設定] ボタンをもう一度クリックし、 *予測 URL* がサービスの最新のイテレーションを引き続き使用するようにしてください。

    ![トレーニングサービスモデルの開始 ](images/AzureLabs-Lab302b-39.png) ![ [既定の設定] オプションの選択](images/AzureLabs-Lab302b-40.png)

## <a name="your-finished-custom-vision-api-application"></a>完成した Custom Vision API アプリケーション

これで、Azure Custom Vision API を活用して実際のオブジェクトを認識し、サービスモデルをトレーニングし、表示されている内容の信頼性を表示する、mixed reality アプリを構築しました。

![完成したプロジェクトの例](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a>ボーナス演習

### <a name="exercise-1"></a>演習1

**Custom Vision Service** をトレーニングして、より多くのオブジェクトを認識します。

### <a name="exercise-2"></a>演習2

学習した内容を拡張する方法として、次の演習を実行します。

オブジェクトが認識されたときにサウンドを再生します。

### <a name="exercise-3"></a>演習3

API を使用して、アプリが分析しているのと同じイメージでサービスを再トレーニングします。これにより、サービスの精度が向上します (予測とトレーニングの両方を同時に行うことができます)。
