---
title: MR と Azure 302-コンピュータービジョン
description: このコースでは、混合現実アプリケーションで Azure Computer Vision を使用して、提供されたイメージ内のビジュアルコンテンツを認識する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, チュートリアル, api, コンピュータービジョン, hololens, イマーシブ, vr
ms.openlocfilehash: 4c8566a2654eb92a4dab2a933bd8afb0b745cfce
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91688303"
---
# <a name="mr-and-azure-302-computer-vision"></a>MR と Azure 302:コンピューター ビジョン

<br>

>[!NOTE]
>Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。  そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。  これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは " **_ありません_** "。  これらは、サポートされているデバイス上で継続して動作するように、保守されます。 今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。  この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。

<br>

このコースでは、混合現実アプリケーションで Azure Computer Vision 機能を使用して、提供されたイメージ内のビジュアルコンテンツを認識する方法を学習します。

認識結果は、説明的なタグとして表示されます。 このサービスは、機械学習モデルをトレーニングすることなく使用できます。 実装に機械学習モデルのトレーニングが必要な場合は、「 [MR」と「Azure 302b](mr-azure-302b.md)」を参照してください。

![ラボの結果](images/AzureLabs-Lab2-000.png)

Microsoft Computer Vision は、開発者がクラウドから高度なアルゴリズムを使用して、イメージの処理と分析 (戻り情報を含む) を提供するように設計された Api のセットです。 開発者がイメージまたはイメージの URL をアップロードすると、Microsoft Computer Vision API アルゴリズムによって、ユーザーが選択した入力に基づいてビジュアルコンテンツが分析されます。これにより、画像の種類と品質の特定、人物顔の検出 (座標の取得)、タグ付け、画像の分類などを行うことができます。 詳細については、 [Azure Computer Vision API のページ](https://azure.microsoft.com/services/cognitive-services/computer-vision/)を参照してください。

このコースを完了すると、mixed reality HoloLens アプリケーションが完成します。これにより、次のことができるようになります。

1.  Tap ジェスチャを使用すると、HoloLens のカメラによってイメージがキャプチャされます。
2.  イメージは、Azure Computer Vision API サービスに送信されます。 
3.  認識されたオブジェクトは、Unity シーンに配置された単純な UI グループに一覧表示されます。

アプリケーションでは、結果をデザインと統合する方法については、お客様のニーズに合わせてください。 このコースは、Azure サービスを Unity プロジェクトと統合する方法を説明することを目的としています。 このコースで得られた知識を使用して、mixed reality アプリケーションを強化することができます。

## <a name="device-support"></a>デバイス サポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="../../../hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 302:コンピューター ビジョン</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> このコースでは主に HoloLens に焦点を当てていますが、このコースで学習する内容を Windows Mixed Reality イマーシブ (VR) ヘッドセットにも適用できます。 イマーシブ (VR) ヘッドセットにはアクセス可能なカメラがないため、外部カメラが PC に接続されている必要があります。 コースを進めると、イマーシブ (VR) ヘッドセットをサポートするために必要な変更についての注意事項が表示されます。

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
- PC に接続されているカメラ (イマーシブヘッドセット開発用)
- Azure のセットアップと Computer Vision API の取得のためのインターネットアクセス

## <a name="before-you-start"></a>開始する前に

1.  このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。
2.  HoloLens をセットアップしてテストします。 HoloLens のセットアップをサポートする必要がある場合は、 [hololens セットアップに関する記事にアクセスして](https://docs.microsoft.com/hololens/hololens-setup)ください。 
3.  新しい HoloLens アプリの開発を開始するときは、調整とセンサーのチューニングを実行することをお勧めします (ユーザーごとにこれらのタスクを実行するのに役立つ場合があります)。 

調整の詳細については、 [「HoloLens の調整に関する記事へのリンク」を](../../../calibration.md#hololens-2)参照してください。

センサーチューニングの詳細については、 [HoloLens センサーチューニングに関する記事へのリンクを](../../../sensor-tuning.md)参照してください。

## <a name="chapter-1--the-azure-portal"></a>章 1-Azure Portal

Azure で *Computer Vision API* サービスを使用するには、アプリケーションで使用できるようにサービスのインスタンスを構成する必要があります。

1.  まず、 [Azure Portal](https://portal.azure.com)にログインします。 

    > [!NOTE]
    > まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。 このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。

2.  ログインしたら、左上隅にある [ **新規** ] をクリックし、 *Computer Vision API* を検索して、 **Enter キー** を押します。

    ![Azure での新しいリソースの作成](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > 新しいポータルで、 **New** という単語が **リソースの作成** に置き換えられました。
 
3.  新しいページには、 *Computer Vision API* サービスの説明が表示されます。 このページの左下にある [ **作成** ] ボタンを選択して、このサービスとの関連付けを作成します。

    ![コンピュータービジョン api サービスについて](images/AzureLabs-Lab2-01.png)
 
4.  [ **作成** :

    1. このサービスインスタンスに必要な **名前** を挿入します。
    2. **サブスクリプション** を選択します。
    3. 適切な **価格レベル** を選択します。これが *Computer Vision API* サービスを初めて作成する場合は、free レベル (F0) を使用できます。
    4. リソースグループを選択するか、新しい **リソースグループ** を作成します。 リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。 1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのラボなど) を共通のリソースグループに保持することをお勧めします。 

        > Azure リソースグループの詳細については、 [リソースグループ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)に関する記事をご覧ください。

    5. リソースグループの場所を決定します (新しいリソースグループを作成している場合)。 この場所は、アプリケーションを実行するリージョンに配置するのが理想的です。 一部の Azure 資産は、特定のリージョンでのみ利用できます。

    6. また、このサービスに適用されている使用条件を理解していることを確認する必要があります。
    7. [作成] をクリックします。

        ![サービスの作成に関する情報](images/AzureLabs-Lab2-02.png)

5.  [ **作成** ] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。
6.  サービスインスタンスが作成されると、ポータルに通知が表示されます。

    ![新しいサービスの新しい通知を確認する](images/AzureLabs-Lab2-03.png) 
 
7.  通知をクリックして、新しいサービスインスタンスを探索します。 

    ![[リソースへの移行] ボタンを選択します。](images/AzureLabs-Lab2-04.png)
 
8. 通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。 新しい Computer Vision API サービスインスタンスが表示されます。 

    ![新しい Computer Vision API サービスイメージ](images/AzureLabs-Lab2-05.png)
 
9.  このチュートリアルでは、アプリケーションがサービスの呼び出しを行う必要があります。サービスは、サービスのサブスクリプションキーを使用して実行されます。
10. *Computer Vision API* サービスの [ *クイックスタート* ] ページで、最初の手順に移動し、 *キーを取得* して、[ **キー** ] をクリックします (これを行うには、[サービス] ナビゲーションメニューにある青いハイパーリンクキーをクリックします。これは、キーアイコンで示されます)。 これにより、サービス *キー* が表示されます。
11. 表示されているキーの1つをコピーします。これは、プロジェクトの後半で必要になります。 

12. [ *クイックスタート* ] ページに戻り、そこからエンドポイントを取得します。 お客様の地域によっては異なる場合があることに注意してください (その場合は、後でコードを変更する必要があります)。 後で使用するために、このエンドポイントのコピーを取得します。

    ![新しい Computer Vision API サービス](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > [ここで](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)は、さまざまなエンドポイントを確認できます。 

## <a name="chapter-2--set-up-the-unity-project"></a>第2章: Unity プロジェクトを設定する

次に示すのは、mixed reality で開発するための一般的な設定です。そのため、他のプロジェクトに適したテンプレートです。

1.  *Unity* を開き、[ **新規** ] をクリックします。 

    ![新しい Unity プロジェクトを開始します。](images/AzureLabs-Lab2-06.png)

2.  ここで、Unity プロジェクト名を指定する必要があります。 **MR_ComputerVision** を挿入します。 プロジェクトの種類が **3d** に設定されていることを確認します。 場所を適切な **場所** に設定します (ルートディレクトリの方が適していることに注意してください)。 次に、[ **プロジェクトの作成** ] をクリックします。

    ![新しい Unity プロジェクトの詳細を指定します。](images/AzureLabs-Lab2-07.png)

3.  Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。 [ **> の設定の編集** ] に移動し、新しいウィンドウで [ **外部ツール** ] に移動します。 **外部スクリプトエディター** を **Visual Studio 2017** に変更します。 [ **基本設定** ] ウィンドウを閉じます。

    ![スクリプトエディターの設定を更新します。](images/AzureLabs-Lab2-08.png)

4.  次に、[ **ファイル > ビルド設定** ] に移動し、[ **ユニバーサル Windows プラットフォーム** ] を選択します。次に、[ **プラットフォームの切り替え** ] ボタンをクリックして選択内容を適用します。

    ![[ビルドの設定] ウィンドウで、[プラットフォーム] を [UWP] に切り替えます。](images/AzureLabs-Lab2-10.png)

5.  それでも **ファイル > ビルド設定** を行い、次のことを確認します。

    1. **ターゲットデバイス** が **HoloLens** に設定されています

        > イマーシブヘッドセットの場合は、 **ターゲットデバイス** を *任意のデバイス* に設定します。

    2. **ビルドの種類** が **D3D** に設定されています
    3. **SDK** は最新の **インストール** に設定されています
    4. **Visual Studio のバージョン** が、 **インストールされている最新** バージョンに設定されています
    5. **ビルドと実行** は **ローカルコンピューター** に設定されています
    6. シーンを保存し、ビルドに追加します。

        1. これを行うには、[開いている **シーンの追加** ] を選択します。 保存ウィンドウが表示されます。
        
            ![[開いているシーンを追加] ボタンをクリックする](images/AzureLabs-Lab2-11.png)

        2. この新しいフォルダーを作成し、今後のシーンに加えて、[ **新しいフォルダー** ] ボタンを選択します。新しいフォルダーを作成するには、名前を「 **シーン** 」にします。

            ![新しいスクリプトフォルダーの作成](images/AzureLabs-Lab2-12.png)

        3. 新しく作成した [ **シーン** ] フォルダーを開き、[ *ファイル名* : テキスト] フィールドに「 **MR_ComputerVisionScene** 」と入力し、[ **保存** ] をクリックします。

            ![新しいシーンに名前を付けます。](images/AzureLabs-Lab2-13.png)

            > Unity プロジェクトに関連付けられている必要があるため、Unity のシーンを *Assets* フォルダー内に保存する必要があります。 Unity プロジェクトを構成する一般的な方法は、シーンフォルダー (およびその他の同様のフォルダー) を作成することです。

    7. それ以外の設定は、[ *ビルド設定* ] の [既定] のままにしておきます。

6. [ *ビルドの設定* ] ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 *インスペクター* が配置されている領域の関連パネルが開きます。 

    ![プレーヤーの設定を開きます。](images/AzureLabs-Lab2-14.png)

7. このパネルでは、いくつかの設定を確認する必要があります。

    1. [ **その他の設定** ] タブで、次のようにします。

        1. **スクリプトランタイムのバージョン** は **安定** している必要があります (.net 3.5 と同等)。
        2. **バックエンド** は **.net** である必要があります
        3. **API 互換性レベル** は **.net 4.6** である必要があります

            ![その他の設定を更新します。](images/AzureLabs-Lab2-15.png)
      
    2. [ **発行の設定** ] タブの [ **機能** ] で、次の項目を確認します。

        1. **InternetClient**
        2. **Web カメラ**

            ![発行設定を更新しています。](images/AzureLabs-Lab2-16.png)

    3. パネルの下にある [ **XR settings** (発行の **設定** ] の下にあります) で、[ **サポートされている仮想現実** ] をティックし、 **Windows Mixed reality SDK** が追加されていることを確認します。

        ![X R の設定を更新します。](images/AzureLabs-Lab2-17.png)

8.  *ビルド設定* に戻る _Unity C#_ プロジェクトはグレーで表示されなくなりました。このの横にあるチェックボックスをオンにします。 
9.  [ビルド設定] ウィンドウを閉じます。
10. シーンとプロジェクトを保存します ([ **ファイル] > [シーン/ファイルの保存] > [プロジェクトの保存** ])。

## <a name="chapter-3--main-camera-setup"></a>第3章–メインカメラの設定

> [!IMPORTANT]
> このコースの *Unity セットアップ* コンポーネントをスキップしてコードに直接進む場合は、 [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage)をダウンロードし、 [カスタムパッケージ](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてから、 [第5章](#chapter-5--create-the-resultslabel-class)から続行してください。

1.  [ *階層] パネル* で、 **メインカメラ** を選択します。 
2.  選択すると、 **メインカメラ** のすべてのコンポーネントが [ *インスペクター] パネル* に表示されます。

    1. **カメラオブジェクト** は **メインカメラ** という名前にする必要があります (スペルに注意してください)。
    2. メインカメラの **タグ** は、 **maincamera** に設定する必要があります (スペルに注意してください)。
    3. **変換位置** が **0、0、0** に設定されていることを確認します。
    4. **クリアフラグ** を **純色** に設定します (イマーシブヘッドセットの場合は無視します)。
    5. カメラコンポーネントの **背景** 色を **黒、アルファ 0 (16 進コード: #00000000)** に設定します (イマーシブヘッドセットの場合は無視します)。

        ![カメラコンポーネントを更新します。](images/AzureLabs-Lab2-18.png)
 
3.  次に、 **メインカメラ** に接続された単純な "Cursor" オブジェクトを作成する必要があります。これは、アプリケーションの実行時にイメージ分析出力を配置するのに役立ちます。 このカーソルによって、カメラフォーカスの中心点が決まります。

カーソルを作成するには、次のようにします。

1.  [ *階層] パネル* で、 **メインカメラ** を右クリックします。 [ **3D オブジェクト** ] で、[ **球** ] をクリックします。

    ![Cursor オブジェクトを選択します。](images/AzureLabs-Lab2-19.png)
 
2.  **球** の名前を **カーソル** に変更します (カーソルオブジェクトをダブルクリックするか、オブジェクトが選択された状態で F2 キーを押します)。 **メインカメラ** の子として配置されていることを確認します。

3.  [ *階層] パネル* で、 **カーソル** を左クリックします。 カーソルを選択した状態で、[ *インスペクター] パネル* で次の変数を調整します。

    1. *変換位置* を **0、0、5** に設定します。
    2. *スケール* を **0.02、0.02、0.02** に設定します。

        ![変換位置とスケールを更新します。](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>Chapter 4 –ラベルシステムのセットアップ

HoloLens のカメラを使用してイメージをキャプチャすると、そのイメージが分析のために *Azure Computer Vision API* サービスインスタンスに送信されます。 

この分析の結果は、 **タグ** と呼ばれる認識されたオブジェクトの一覧になります。 

これらのタグは、写真が撮影された場所に表示されるように、(ワールド空間の3D テキストとして) 使用します。

次の手順では、 **Label** オブジェクトを設定する方法について説明します。

1.  [階層] パネル内の任意の場所を右クリックし (この時点では場所は関係ありません)、[ **3D オブジェクト** ] の下に **3d テキスト** を追加します。 **Labeltext** という名前を指定します。

    ![3D テキストオブジェクトを作成します。](images/AzureLabs-Lab2-21.png)
 
2.  [ *階層] パネル* で、 **labeltext** を左クリックします。 **Labeltext** を選択した状態で、[ *インスペクター] パネル* で次の変数を調整します。

    1. **位置** を **0、0、0** に設定します。
    2. **スケール** を **0.01、0.01、0.01** に設定します。
    3. コンポーネント **テキストメッシュ** で、次のようにします。
    4. **テキスト** 内のすべてのテキストを "..." で置き換えます。        
    5. **アンカー** を **中央** 中央に設定する
    6. **配置** を **中央** に設定する
    7. **タブサイズ** を **4** に設定します。
    8. **フォントサイズ** を **50** に設定します。
    9. **色** を **#FFFFFFFF** に設定します

    ![テキストコンポーネント](images/AzureLabs-Lab2-21-5.png)

3.  [ *プロジェクト] パネル* の内の [ *階層] パネル* から [ *アセット] フォルダー* に **labeltext** をドラッグします。 これにより、コードでインスタンス化できるように **Labeltext** が事前 fab になります。

    ![LabelText オブジェクトの事前 fab を作成します。](images/AzureLabs-Lab2-22.png)
 
4.  [ *階層] パネル* から **labeltext** を削除して、開いているシーンには表示されないようにする必要があります。 現在は、Assets フォルダーから個々のインスタンスに対して呼び出す prefab であるため、シーン内に保持する必要はありません。 
5.  *階層パネル* の最終的なオブジェクト構造は、次の図に示すようになります。

    ![階層パネルの最終構造。](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>第5章–生成されるのは、そのためのラベルクラス

作成する必要のある最初のスクリプトは、次の処理を行うための、次のような、べき条件の *ラベル* クラスです。 

- カメラの位置を基準にして、適切なワールド空間にラベルを作成します。
- イメージ Anaysis のタグを表示します。

このクラスを作成するには: 

1.  [ *プロジェクト] パネル* 内を右クリックし、[ **> フォルダーの作成** ] をクリックします。 フォルダーに **スクリプト** の名前を指定します。 

    ![Scripts フォルダーを作成します。](images/AzureLabs-Lab2-24.png)

2.  **Scripts** フォルダー create を使用して、ダブルクリックして開きます。 次に、そのフォルダー内でを右クリックし、[ **Create >** Then **C# Script** ] を選択します。 スクリプトのラベルに「」という名前を *付け* ます。 

3.  新しいスクリプト *ラベル* スクリプトをダブルクリックして、 **Visual Studio** で開きます。

4.  クラス内で、次のコードを入力 *します* 。

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  *Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。
7.  *Unity エディター* に戻り、[ **スクリプト** ] フォルダーの [の履歴] クラスをクリックし *て、[* *階層] パネル* の [ **メインカメラ** ] オブジェクトにドラッグします。
8.  **メインカメラ** をクリックし、[ *インスペクター] パネル* を確認します。

カメラにドラッグしたスクリプトから、 **Cursor** と **Label prefab** の2つのフィールドがあることがわかります。

9.  次の図に示すように、[ *階層] パネル***から [カーソル]** というオブジェクトを [ **カーソル** ] という名前のスロットにドラッグします。
10. 次の図に示すように、[ *プロジェクト] パネル* の [ *アセット] フォルダー* から **labeltext** という名前のオブジェクトを **label prefab** という名前のスロットにドラッグします。 

    ![Unity 内で参照ターゲットを設定します。](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>Chapter 6 – ImageCapture クラスを作成する

次に作成するクラスは、 *Imagecapture* クラスです。 このクラスの役割は次のとおりです。

-   HoloLens カメラを使用してイメージをキャプチャし、アプリフォルダーに格納します。
-   ユーザーからタップジェスチャをキャプチャしています。

このクラスを作成するには: 

1.  前に作成した **Scripts** フォルダーにアクセスします。 
2.  フォルダー内を右クリックし、[ **Create > C# Script** ] をクリックします。 スクリプト *Imagecapture* を呼び出します。 
3.  新しい *Imagecapture* スクリプトをダブルクリックして、 **Visual Studio** で開きます。
4.  ファイルの先頭に次の名前空間を追加します。

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  次に、 *Start ()* メソッドの上に、 *imagecapture* クラス内に次の変数を追加します。

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
**TapsCount** 変数には、ユーザーからキャプチャしたタップジェスチャの数が格納されます。 この数値は、キャプチャしたイメージの名前付けに使用されます。

6.  起動可能な *()* メソッドと *Start ()* メソッドのコードを追加する必要があります。 これらは、クラスの初期化時に呼び出されます。

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  Tap ジェスチャが発生したときに呼び出されるハンドラーを実装します。 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
*TapHandler ()* メソッドは、ユーザーからキャプチャされたタップの数を増やし、現在のカーソル位置を使用して、新しいラベルを配置する場所を決定します。

次に、このメソッドは、 *Executeimagecapを Andanalysis ()* メソッドを呼び出して、このアプリケーションのコア機能を開始します。

8.  イメージをキャプチャして保存すると、次のハンドラーが呼び出されます。 プロセスが成功した場合、結果は分析のために (まだ作成していない) *VisionManager* に渡されます。

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  次に、アプリケーションがイメージキャプチャプロセスを開始するために使用するメソッドを追加し、イメージを格納します。

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> この時点で、 *Unity エディターのコンソールパネル* にエラーが表示されます。 これは、次の章で作成する *VisionManager* クラスをコードが参照するためです。

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>第7章-Azure への呼び出しとイメージ分析

作成する必要がある最後のスクリプトは、 *VisionManager* クラスです。 

このクラスの役割は次のとおりです。

-   バイト配列としてキャプチャされた最新のイメージを読み込んでいます。
-   分析のために、バイト配列を *Azure Computer Vision API* サービスインスタンスに送信しています。
-   JSON 文字列として応答を受信しています。
-   応答を逆シリアル化 *し、結果* として得られるタグを結果のタグに渡します。
 
このクラスを作成するには:

1.  [ **Scripts** ] フォルダーをダブルクリックして開きます。 
2.  **Scripts** フォルダー内を右クリックし、[ **Create > C# Script** ] をクリックします。 スクリプトに *VisionManager* という名前を指定します。 
3.  新しいスクリプトをダブルクリックして、Visual Studio で開きます。
4.  *VisionManager* クラスの先頭にある次の名前空間を更新します。

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  スクリプトの先頭にある *VisionManager* クラス *内* ( *Start ()* メソッドの上) で、Azure からの逆シリアル化された JSON 応答を表す2つの *クラス* を作成する必要があります。

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > *Tagdata* クラスと Analytics *sedobject* クラスでは、Unity ライブラリを使用して逆シリアル化できるようにする前に、 *[system.string]* 属性を追加する必要があります。

6.  VisionManager クラスでは、次の変数を追加する必要があります。

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > **認証キー** が **authorizationkey** 変数に挿入されていることを確認します。 **認証キー** については、このコースの [第1章](#chapter-1--the-azure-portal)で説明しました。

    > [!WARNING] 
    > **VisionAnalysisEndpoint** 変数は、この例で指定したものとは異なる場合があります。 **米国西部** は、米国西部リージョン用に作成されたサービスインスタンスを厳密に参照します。 これを [エンドポイント URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)で更新します。次に例をいくつか示します。
    > - 西ヨーロッパ: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - 東南アジア: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - オーストラリア東部: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  起動するためのコードを追加する必要があります。 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  次に、コルーチン (その下に静的ストリームメソッドを含む) を追加します。これにより、 *Imagecapture* クラスによってキャプチャされたイメージの分析結果が得られます。 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  *Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。
10. Unity エディターに戻り、[ **スクリプト** ] フォルダーの *VisionManager* および *imagecapture* クラスをクリックして、[ *階層] パネル* の [ **メインカメラ** ] オブジェクトにドラッグします。 

## <a name="chapter-8--before-building"></a>章 8-ビルド前

アプリケーションの徹底的なテストを実行するには、アプリケーションを HoloLens にサイドロードする必要があります。
これを行う前に、次のことを確認してください。

-   [第2章](#chapter-2--set-up-the-unity-project)で説明したすべての設定が正しく設定されています。 
-   すべてのスクリプトが **メインカメラ** オブジェクトにアタッチされます。 
-   *メインカメラインスペクターパネル* のすべてのフィールドが適切に割り当てられます。
-   **認証キー** が **authorizationkey** 変数に挿入されていることを確認します。
-   *VisionManager* スクリプトでエンドポイントも確認し、地域に合わせて配置されていることを確認します (このドキュメントで *は、既定* で *米国西部* が使用されています)。

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>第9章– UWP ソリューションをビルドし、アプリケーションをサイドロードする
このプロジェクトの Unity セクションに必要なものはすべて完了したので、Unity から構築します。

1.  *ビルド設定*  -  **ファイル > ビルド設定** に移動します...
2.  [ *ビルドの設定* ] ウィンドウで、[ **ビルド** ] をクリックします。

    ![Unity からアプリをビルドする](images/AzureLabs-Lab2-26.png)

3.  **Unity C# プロジェクト** をまだティックしていない場合は、ティックします。
4.  [ **ビルド** ] をクリックします。 Unity は *エクスプローラー* ウィンドウを起動します。このウィンドウでは、アプリを作成するフォルダーを作成して選択する必要があります。 ここでそのフォルダーを作成し、「 *App* 」という名前を指定します。 次に、 *アプリ* フォルダーを選択し、 **[フォルダーの選択]** をクリックします。 
5.  Unity は、 *アプリ* フォルダーへのプロジェクトのビルドを開始します。 
6.  Unity のビルドが完了すると (時間がかかる場合があります)、ビルドの場所で *ファイルエクスプローラー* ウィンドウを開きます (ウィンドウの上に常に表示されるとは限りませんが、新しいウィンドウが追加されたことが通知されます)。

## <a name="chapter-10--deploy-to-hololens"></a>第10章– HoloLens へのデプロイ

HoloLens に展開するには:

1.  Hololens が **開発者モード** になっていることを確認するには、HOLOLENS の IP アドレス (リモートデプロイ用) が必要です。 これを行うには、次の手順を実行します。

    1. HoloLens を装着した後、 **設定** を開きます。
    2. **[ネットワーク & インターネット > wi-fi > 詳細オプション]** にアクセス
    3. **IPv4** アドレスをメモしておきます。
    4. 次に、[ **設定** ] に戻り、 **開発者向けの & セキュリティ > を更新** します。 
    5. 開発者モードをに設定します。

2.  新しい Unity ビルド ( *アプリ* フォルダー) に移動し、 *Visual Studio* でソリューションファイルを開きます。
3.  ソリューション構成で、[ **デバッグ** ] を選択します。
4.  ソリューションプラットフォームで、[ **x86** 、 **リモートコンピューター** ] を選択します。 

    ![Visual Studio からソリューションをデプロイします。](images/AzureLabs-Lab2-27.png)
 
5.  [ **ビルド] メニュー** の [ソリューションの **配置** ] をクリックして、アプリケーションを HoloLens にサイドロードします。
6.  アプリが HoloLens にインストールされているアプリの一覧に表示され、起動できる状態になります。

> [!NOTE]
> イマーシブヘッドセットにデプロイするには **、ソリューションプラットフォーム** を *ローカルコンピューター* に設定し、 **プラットフォーム** として *x86* を使用して、 **構成** を [ *デバッグ* ] に設定します。 次に、[ **ビルド] メニュー** の [ *ソリューションの配置* ] をクリックして、ローカルコンピューターに配置します。 

## <a name="your-finished-computer-vision-api-application"></a>完成した Computer Vision API アプリケーション

これで、Azure Computer Vision API を利用して実際のオブジェクトを認識し、表示されている内容の信頼性を表示する、mixed reality アプリを構築しました。

![ラボの結果](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>ボーナス演習

### <a name="exercise-1"></a>演習1

*Tags* パラメーターを使用したのと同じように ( *VisionManager* 内で使用される *エンドポイント* 内での説明に従って)、他の情報を検出するようにアプリを拡張します。他にアクセスできるパラメーターについては、 [こちら](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)を参照してください。

### <a name="exercise-2"></a>演習2

返された Azure データをより多くの会話で表示し、読みやすい方法で表示します (数値を非表示にするなど)。 Bot はユーザーと話し合っているかもしれません。
