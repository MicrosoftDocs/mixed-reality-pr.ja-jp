---
title: MR と Azure 307-Machine learning
description: このコースでは、mixed reality アプリケーション内で Azure Machine Learning Studio (クラシック) を実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、機械学習、ml、machine learning studio、hololens、イマーシブ、vr、Windows 10、Visual Studio
ms.openlocfilehash: 3bb50c146e11a340f4223d71dd401ac2b84dd6d4
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679481"
---
# <a name="mr-and-azure-307-machine-learning"></a>MR と Azure 307:機械学習

<br>

>[!NOTE]
>Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。  そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。  これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。  これらは、サポートされているデバイス上で継続して動作するように、保守されます。 今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。  この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。

<br>

![最終製品-開始](images/AzureLabs-Lab7-0.png)

このコースでは、Azure Machine Learning Studio (クラシック) を使用して Machine Learning (ML) 機能を mixed reality アプリケーションに追加する方法について説明します。

*Azure Machine Learning Studio (クラシック)* は Microsoft のサービスであり、開発者は大量の機械学習アルゴリズムを使用できます。これは、データの入力、出力、準備、および視覚化に役立ちます。 これらのコンポーネントから、予測分析実験を開発し、それを反復処理して、モデルのトレーニングに使用することができます。 次のトレーニングでは、Azure クラウド内でモデルを操作できるようになり、新しいデータをスコア付けできるようになります。 詳細については、 [Azure Machine Learning Studio (クラシック) のページ](https://azure.microsoft.com/services/machine-learning-studio/)を参照してください。

このコースを完了すると、現実のイマーシブヘッドセットアプリケーションが完成し、次の操作方法を学習できるようになります。

1.  *Azure Machine Learning Studio (クラシック)* ポータルに売上データのテーブルを提供し、人気のあるアイテムの将来の売上を予測するためのアルゴリズムを設計します。
2.  ML サービスから予測データを受信して解釈できる **Unity プロジェクト** を作成します。
3.  Predication データを **Unity プロジェクト** 内に視覚的に表示し、最も人気のある販売品目を棚に提供します。

アプリケーションでは、結果をデザインと統合する方法については、お客様のニーズに合わせてください。 このコースは、Azure サービスを Unity プロジェクトと統合する方法を説明することを目的としています。 このコースで得られた知識を使用して、mixed reality アプリケーションを強化することができます。

このコースは自己完結型のチュートリアルであり、他の Mixed Reality ラボに直接は関与しません。

## <a name="device-support"></a>デバイス サポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="../../../hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 307:機械学習</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> このコースでは主に Windows Mixed Reality イマーシブ (VR) ヘッドセットに焦点を当てていますが、このコースで学習した内容を Microsoft HoloLens に適用することもできます。 このコースに従うと、HoloLens をサポートするために必要となる可能性のある変更に関する注意事項が表示されます。 HoloLens を使用する場合、音声キャプチャ中にエコーが発生することがあります。

## <a name="prerequisites"></a>必須コンポーネント

> [!NOTE]
> このチュートリアルは、Unity と C# の基本的な経験がある開発者向けに設計されています。 また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証されたものを表します (2018 年5月)。 [「ツールのインストール](../../install-the-tools.md)」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に記載されているものよりも新しいソフトウェアで見つかったものと完全に一致するとは限りません。

このコースでは、次のハードウェアとソフトウェアをお勧めします。

- 開発用 PC で、 [Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) (VR) ヘッドセット開発と互換性があります。
- [開発者モードが有効になっている Windows 10 の作成者の更新プログラム (またはそれ以降)](../../install-the-tools.md#installation-checklist)
- [最新の Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- [Windows Mixed Reality イマーシブ (VR) ヘッドセット](../../../discover/immersive-headset-hardware-details.md)または開発者モードを有効にした[Microsoft HoloLens](../../../hololens-hardware-details.md)
- Azure のセットアップと ML のデータ取得のためのインターネットアクセス

## <a name="before-you-start"></a>開始する前に

このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。 

## <a name="chapter-1---azure-storage-account-setup"></a>章 1-Azure Storage アカウントのセットアップ

Azure Translator API を使用するには、アプリケーションで使用できるようにサービスのインスタンスを構成する必要があります。
1.  [Azure Portal](https://portal.azure.com)にログインします。

    > [!NOTE]
    > まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。 このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。

2.  ログインしたら、左側のメニューの [ **ストレージアカウント** ] をクリックします。

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > 新しいポータルで、 **New** という単語が **リソースの作成** に置き換えられました。

3.  [ **ストレージアカウント** ] タブで、[ **追加**] をクリックします。

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab7-2.png)

4.  [ **ストレージアカウントの作成** ] パネルで、次のようにします。

    1.  アカウントの **名前** を挿入します。このフィールドには数字と小文字のみを使用できることに注意してください。
    2.  [ **デプロイモデル] で、** [ **リソースマネージャー**] を選択します。
    3.  [ **アカウントの種類**] で、[ **ストレージ (汎用 v1)**] を選択します。
    4.  **[パフォーマンス]** には **[Standard]** を選択します
    5.  **レプリケーション** の場合は、[**読み取りアクセス-geo 冗長ストレージ (RA-GRS)**] を選択します。
    6.  **安全な転送** は無効のまま **に** しておく必要があります。
    7.  **サブスクリプション** を選択します。
    4. リソースグループを選択するか、新しい **リソースグループ** を作成します。 リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。 1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのラボなど) を共通のリソースグループに保持することをお勧めします。

        > Azure リソースグループの詳細については、 [リソースグループ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)に関する記事をご覧ください。
    
    5.  リソースグループの **場所** を決定します (新しいリソースグループを作成している場合)。 この場所は、アプリケーションを実行するリージョンに配置するのが理想的です。 一部の Azure 資産は、特定のリージョンでのみ利用できます。

5.  また、このサービスに適用されている使用条件を理解していることを確認する必要があります。

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab7-3.png)

6.  [ **作成**] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。

7.  サービスインスタンスが作成されると、ポータルに通知が表示されます。

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio--classic"></a>Chapter 2-Azure Machine Learning Studio (クラシック)

*Azure Machine Learning* を使用するには、アプリケーションで使用できるように Machine Learning サービスのインスタンスを構成する必要があります。

1.  Azure Portal で、左上隅にある [ **新規** ] をクリックし、 **Machine Learning Studio ワークスペース** を検索して **、enter キーを押します**。

    ![Azure Machine Learning Studio (クラシック)](images/AzureLabs-Lab7-5.png)

2.  新しいページには、 **Machine Learning Studio ワークスペース**  サービスの説明が表示されます。 このプロンプトの左下にある [ **作成** ] ボタンをクリックして、このサービスとの関連付けを作成します。

3.  [ **作成**] をクリックすると、新しい **Machine Learning Studio サービス** に関する詳細を指定する必要があるパネルが表示されます。

    1.  このサービスインスタンスに必要な **ワークスペース名** を挿入します。

    2.  **サブスクリプション** を選択します。

    3. リソースグループを選択するか、新しい **リソースグループ** を作成します。 リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。 1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのラボなど) を共通のリソースグループに保持することをお勧めします。 

        > Azure リソースグループの詳細については、 [リソースグループ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)に関する記事をご覧ください。

    4.  リソースグループの **場所** を決定します (新しいリソースグループを作成している場合)。 この場所は、アプリケーションを実行するリージョンに配置するのが理想的です。 一部の Azure 資産は、特定のリージョンでのみ利用できます。 前の章で Azure Storage の作成に使用したものと同じリソースグループを使用する必要があります。

    5.  [ **ストレージアカウント** ] セクションで、[既存のものを **使用**] をクリックし、ドロップダウンメニューをクリックします。そこから、最後の章で作成した **ストレージアカウント** をクリックします。

    6.  ドロップダウンメニューから適切な **ワークスペースの価格レベル** を選択します。

    7.  [ **Web サービスプラン** ] セクションで、[新規 **作成**] **を** クリックし、テキストフィールドに名前を挿入します。

    8.  [ **Web サービスプランの価格レベル** ] セクションで、選択した価格レベルを選択します。 **DEVTEST Standard** という開発テストレベルは、無料でご利用いただけます。

    9.  また、このサービスに適用されている使用条件を理解していることを確認する必要があります。

    10. **[作成]** をクリックします。

        ![Azure Machine Learning Studio (クラシック)](images/AzureLabs-Lab7-6.png)

4.  [ **作成**] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。

5.  サービスインスタンスが作成されると、ポータルに通知が表示されます。

    ![Azure Machine Learning Studio (クラシック)](images/AzureLabs-Lab7-7.png)

6.  通知をクリックして、新しいサービスインスタンスを探索します。

    ![Azure Machine Learning Studio (クラシック)](images/AzureLabs-Lab7-8.png)

7.  通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。

8.  表示されたページの [ **追加リンク** ] セクションで [ **Machine Learning Studio の起動**] をクリックすると、ブラウザーが **Machine Learning Studio** ポータルに送信されます。

    ![Azure Machine Learning Studio (クラシック)](images/AzureLabs-Lab7-9.png)

9.  右上または中央にある [ **サインイン** ] ボタンを使用して、Machine Learning Studio (クラシック) にログインします。

    ![Azure Machine Learning Studio (クラシック)](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-classic-dataset-setup"></a>第3章-Machine Learning Studio (クラシック): データセットのセットアップ

Machine Learning アルゴリズムが動作する方法の1つは、既存のデータを分析し、既存のデータセットに基づいて将来の結果を予測することです。 これは一般に、既存のデータが多いほど、将来の結果を予測するアルゴリズムの方が優れていることを意味します。

このコースでは、 [Productstablecsv と](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip)いうサンプルテーブルが提供されており、ここでダウンロードできます。

> [!IMPORTANT]
> 上記の .zip ファイルには、 **Productstablecsv** と **unitypackage** の両方が含まれています。これについては、 [第6章](#chapter-6---importing-the-mlproducts-unity-package)で必要になります。 このパッケージは、この章にも記載されていますが、csv ファイルとは別のものです。

このサンプルデータセットには、2017年の各日の1時間ごとに最適な販売オブジェクトのレコードが含まれています。
        
![Machine Learning Studio (クラシック): データセットのセットアップ](images/AzureLabs-Lab7-11.png)

たとえば、2017年の午前1時に、1pm (時間 13) では、最も売れた項目がソルトと胡椒になりました。

このサンプルテーブルには、9998のエントリが含まれています。

1.  **Machine Learning Studio (クラシック)** ポータルに戻り、このテーブルを ML の **データセット** として追加します。 これを行うには、画面の左下隅にある [ **+ 新規** ] ボタンをクリックします。

    ![Machine Learning Studio (クラシック): データセットのセットアップ](images/AzureLabs-Lab7-12.png)

2.  セクションは下部に表示され、左側にナビゲーションパネルがあります。 [ **データセット**] をクリックし、右側の [ **ローカルファイル**] をクリックします。

    ![Machine Learning Studio (クラシック): データセットのセットアップ](images/AzureLabs-Lab7-13.png)

3.  新しい **データセット** をアップロードするには、次の手順を実行します。

    1. [アップロード] ウィンドウが表示されます。このウィンドウで、新しいデータセットのハードドライブを **参照** できます。

        ![Machine Learning Studio (クラシック): データセットのセットアップ](images/AzureLabs-Lab7-14.png)

    2.  選択してアップロードウィンドウに戻ると、チェックボックスはオンのままにしておきます。

    3.  下のテキストフィールドで、データセットの名前として「 **ProductsTableCSV.csv** 」と入力します (ただし、自動的に追加されます)。

    4.  [ **種類**] のドロップダウンメニューを使用して、 **ヘッダー (.csv) を含む汎用 CSV ファイル** を選択します。

    5.  アップロードウィンドウの右下にあるティックを押すと、 **データセット** がアップロードされます。

## <a name="chapter-4---the-machine-learning-studio-classic-the-experiment"></a>Chapter 4-Machine Learning Studio (クラシック): 実験

機械学習システムを構築する前に、実験を作成して、データに関する理論を検証する必要があります。 結果によって、さらに多くのデータが必要かどうか、またはデータと考えられる結果の間に相関関係がないかどうかがわかります。

実験の作成を開始するには:

1.  ページの左下にある [ **+ 新規**] ボタンをもう一度クリックし、[**実験** 用の空の実験] をクリックし  >  **Blank Experiment** ます。

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-15.png)

2.  空の実験で新しいページが表示されます。

3.  左側のパネルで、[**保存されたデータセット**  >  **マイデータセット**] を展開し、[ **productstablecsv** ] を **実験キャンバス** にドラッグします。

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-16.png)

4.  左側のパネルで、[**データ変換** の  >  **サンプルと分割**] を展開します。 次に、[ **データの分割** ] 項目を **実験キャンバス** にドラッグします。 データの分割項目によって、データセットが2つの部分に分割されます。 機械学習アルゴリズムのトレーニングに使用する1つのパート。 2番目の部分は、生成されたアルゴリズムの精度を評価するために使用されます。

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-17.png)

5.  右側のパネル (キャンバスの [データの分割] 項目が選択されている状態) で、 **最初の出力データセットの行の割合** を **0.7** に変更します。 これにより、データは2つの部分に分割され、最初の部分はデータの70% になり、2番目の部分は残りの30% になります。 データがランダムに分割されるようにするには、[ **ランダム分割** ] チェックボックスがオンのままになっていることを確認します。

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-18.png)

6.  キャンバスの **Productstablecsv** 項目のベースから分割データ項目の一番上に接続をドラッグします。 これにより、項目が接続され、 **Productstablecsv** データセットの出力 (データ) が分割データ入力に送信されます。  

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-19.png)

7.  左側の **実験** パネルで、[ **Machine Learning** トレーニング] を展開し  >  **Train** ます。 [ **モデルのトレーニング** ] 項目を実験キャンバスにドラッグします。 キャンバスは次のようになります。

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-20.png)

8.  **_ 分割データ項目 *の* _bottom left_** 左下の [**モデルのトレーニング**] 項目の **右上** にある [接続] をドラッグします。 データセットからの最初の70% の分割は、アルゴリズムをトレーニングするために Train モデルによって使用されます。

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-21.png)

9.  キャンバスで [ **モデルのトレーニング** ] 項目を選択し、[ **プロパティ** ] パネル (ブラウザーウィンドウの右側) で、[ **列セレクターの起動** ] ボタンをクリックします。

10. テキストボックスに「 **product** 」と入力し、 **enter** キーを押します。 *製品* は、予測をトレーニングするための列として設定されます。 次に、右下隅にある **目盛り** をクリックして、選択ダイアログを閉じます。

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-22.png)

11. **多クラスロジスティック回帰** アルゴリズムをトレーニングして、その日の時間と日付に基づいて販売された **製品** を予測します。 Azure Machine Learning studio によって提供されるさまざまなアルゴリズムの詳細については、このドキュメントでは説明しません。ただし、 [Machine Learning アルゴリズム](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)の詳細については、「」を参照してください。

12. 左側の [実験項目] パネルで [ **Machine Learning**  >  のモデル分類の **初期化**] を展開  >  **Classification** し、**多クラスロジスティック回帰** 項目を実験キャンバスにドラッグします。

13. **多クラスロジスティック回帰** の一番下にある出力を、[**モデルのトレーニング**] 項目の左上の入力に接続します。

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-23.png)

14. 左側のパネルにある実験項目の一覧で [ **Machine Learning**  >  **スコア**] を展開し、[**モデルのスコア** 付け] 項目をキャンバスにドラッグします。

15. **トレーニングモデル** の下部にある出力を、**スコアモデル** の左上の入力に接続します。

16. 分割された **データ** から、 **モデルのスコア** 付け項目の右上の入力に、右下の出力を接続します。

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-24.png)

17. 左側のパネルにある **実験** 項目の一覧で、[ **Machine Learning**  >  **評価**] を展開し、[**モデルの評価**] 項目をキャンバスにドラッグします。

18. **スコアモデル** の出力を、**評価モデル** の左上の入力に接続します。

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-25.png)

19. 最初の Machine Learning 実験を作成しました。 これで、実験を保存して実行できるようになりました。 ページの下部にあるメニューで、[ **保存** ] ボタンをクリックして実験を保存し、[ **実行** ] をクリックして実験を開始します。

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-26.png)

20. キャンバスの右上にある実験の **状態** を確認できます。 実験が終了するまでしばらく待ちます。

    > ビッグ (実際の) データセットがある場合は、実験の実行に時間がかかる可能性があります。

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-27.png)

21. キャンバスで [ **モデルの評価** ] 項目を右クリックし、コンテキストメニューから、 **評価結果** にマウスポインターを移動して、[ **視覚化**] を選択します。

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-28.png)

22. 予測された結果と実際の結果を示す評価結果が表示されます。 これにより、前に分割した元のデータセットの30% がモデルの評価に使用されます。 結果が最適ではないことがわかります。各行の最大数が列の強調表示された項目になるのが理想的です。

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-29.png)

23. **結果** を閉じます。

24. 新しくトレーニングされた Machine Learning モデルを使用するには、 **Web サービス** として公開する必要があります。 これを行うには、ページの下部にあるメニューの [ **Web サービスの設定** ] メニュー項目をクリックし、[ **予測 Web サービス**] をクリックします。

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-30.png)

25. 新しいタブが作成され、新しい web サービスを作成するためにトレーニングモデルが結合されます。 

26. ページの下部にあるメニューで [ **保存**] をクリックし、[ **実行**] をクリックします。 実験キャンバスの右上隅に更新された状態が表示されます。

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-31.png)

27. 実行が完了すると、[ **Web サービスのデプロイ** ] ボタンがページの下部に表示されます。 これで、web サービスをデプロイする準備が整いました。 ページの下部にあるメニューで、[ **Deploy Web Service** (クラシック)] をクリックします。

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-32.png)

    > ブラウザーでポップアップ **を許可する** ように求められる場合があります。ただし、[デプロイ] ページが表示されない場合は、[ **Web サービスのデプロイ** ] をもう一度クリックする必要があります。 

28. 実験が作成されると、 **API キー** が表示される **ダッシュボード** ページにリダイレクトされます。 その時点でメモ帳にコピーします。コードですぐに必要になります。 API キーを書き留めたら、キーの下にある [**既定のエンドポイント**] セクションの [**要求/応答**] ボタンをクリックします。

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > このページで [テスト] をクリックすると、入力データを入力して出力を表示できるようになります。 **日付** と **時刻** を入力します。 **製品** エントリを空白のままにします。 次に、[ **確認** ] ボタンをクリックします。 ページの下部にある出力には、各製品が選択されている可能性を表す JSON が表示されます。

29. 新しい web ページが開き、Machine Learning Studio (クラシック) で必要とされる要求構造に関する指示といくつかの例が表示されます。 このページに表示されている **要求 URI** をメモ帳にコピーします。

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-34.png)

これで、過去の購入データに基づいて販売される可能性の高い製品を提供する機械学習システムが構築されました。これは、その年の日付と時刻に関連付けられています。

Web サービスを呼び出すには、サービスエンドポイントの URL とサービスの API キーが必要です。 上部のメニューから [ **使用** ] タブをクリックします。

[ **従量課金** 情報] ページには、コードから web サービスを呼び出すために必要な情報が表示されます。 **プライマリキー** と **要求-応答** URL のコピーを取得します。 これらは、次の章で必要になります。

## <a name="chapter-5---setting-up-the-unity-project"></a>章 5-Unity プロジェクトの設定

Mixed Reality のイマーシブヘッドセットをセットアップしてテストします。

> [!NOTE]
>  このコースでは、モーションコントローラーは必要 **ありません** 。 イマーシブヘッドセットの設定をサポートする必要がある場合は、 [ここ](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)をクリックしてください。

1.  **Unity** を開き、MR の "e" という名前の新しい unity プロジェクトを作成し **\_ ます。** プロジェクトの種類が **3d** に設定されていることを確認します。

2.  Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。 [設定の **編集**] に移動し、  >  **Preferences** 新しいウィンドウで [**外部ツール**] に移動します。 **外部スクリプトエディター** を **Visual Studio 2017** に変更します。 [ **基本設定** ] ウィンドウを閉じます。

3.  次に、[**ファイル**  >  ] [**ビルドの設定**] に移動し、[プラットフォームの *_切り替え_*] _ ボタンをクリックして、プラットフォームを **ユニバーサル Windows プラットフォーム** に切り替えます。

4.  また、次のことを確認してください。

    1.  _ *ターゲットデバイス** は **任意のデバイス** に設定されます。

        > Microsoft HoloLens の場合は、 **ターゲットデバイス** を *HoloLens* に設定します。

    2.  **ビルドの種類** が **D3D** に設定されています。

    3.  **SDK** は、 **インストールされている最新のバージョン** に設定されます。

    4.  **Visual Studio のバージョン** が、 **インストールされている最新** のバージョンに設定されています。

    5.  **ビルドと実行** は **ローカルコンピューター** に設定されています。

    6.  後で提供されているように、現時点で **は設定に** ついて心配しないでください。

    7.  ここでは、残りの設定は既定値のままにしておきます。

        ![Unity プロジェクトの設定](images/AzureLabs-Lab7-35.png)

5.  [ **ビルドの設定** ] ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 **インスペクター** が配置されている領域の関連パネルが開きます。 

6. このパネルでは、いくつかの設定を確認する必要があります。

    1.  [ **その他の設定** ] タブで、次のようにします。

        1.  **Scripting** **Runtime のバージョン** は **実験的** である必要があります (.net 4.6 と同等)

        2. **スクリプトバックエンド** は **_.net_* _ である必要があります

        3. _ *API 互換性レベル** は **.net 4.6** である必要があります

            ![Unity プロジェクトの設定](images/AzureLabs-Lab7-36.png)

    2.  [ **発行の設定** ] タブの [ **機能**] で、次の項目を確認します。

        - **InternetClient**

            ![Unity プロジェクトの設定](images/AzureLabs-Lab7-37.png)

    3.  パネルの下の [ **XR settings** ( **発行の設定**] の下にあります) で、[ **サポートされている仮想現実**] をティックし、 **Windows Mixed reality SDK** が追加されていることを確認します。

        ![Unity プロジェクトの設定](images/AzureLabs-Lab7-38.png)

    

6.  **ビルド設定** に戻る *Unity C#* プロジェクトはグレーで表示されなくなりました。このの横にあるチェックボックスをオンにします。 

7.  [ビルド設定] ウィンドウを閉じます。

8.  プロジェクトを保存します (**ファイル > プロジェクトに保存** します)。

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a>第6章-MLProducts Unity パッケージのインポート

このコースでは、 [**unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage)という名前の Unity アセットパッケージをダウンロードする必要があります。 このパッケージは、すべてのオブジェクトがあらかじめ構築されているシーンで完成しているので、すべての作業に専念できます。 **ShelfKeeper** スクリプトが用意されていますが、シーンのセットアップ構造ではパブリック変数のみが保持されます。 他のすべてのセクションを実行する必要があります。 

このパッケージをインポートするには:

1.  Unity ダッシュボードを使用して、画面の上部にあるメニューの [ **アセット** ] をクリックし、[ **パッケージのインポート, カスタムパッケージ**] をクリックします。

    ![MLProducts Unity パッケージをインポートしています](images/AzureLabs-Lab7-39.png)

2.  ファイルピッカーを使用して **unitypackage** パッケージを選択し、[ **開く**] をクリックします。

3.  この資産のコンポーネントの一覧が表示されます。 インポートを確認するには、[ **インポート**] をクリックします。

    ![MLProducts Unity パッケージをインポートしています](images/AzureLabs-Lab7-40.png)

4.  インポートが完了すると、一部の新しいフォルダーが Unity の [ **プロジェクト] パネル** に表示されます。 これらは、3D モデルと、作業する事前に作成されたシーンの一部であるそれぞれのマテリアルです。 このコースでは、大部分のコードを記述します。

    ![MLProducts Unity パッケージをインポートしています](images/AzureLabs-Lab7-41.png)

5.  [ **プロジェクトパネル]** フォルダー内の [ **シーン** ] フォルダーをクリックし、内部のシーン ( **MR_MachineLearningScene**) をダブルクリックします。 シーンが開きます (下図を参照)。 赤いひし形が欠けている場合は、[**ゲーム] パネル** の右上にある [**ギズモ**] ボタンをクリックします。

    ![MLProducts Unity パッケージをインポートしています](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a>第7章-Unity での Dll のチェック

(シリアル化と逆シリアル化に使用される) JSON ライブラリの使用を活用するために、作成したパッケージに Newtonsoft DLL が実装されています。 ライブラリには適切な構成が必要です (特に、コードが動作していない問題が発生している場合)。 

そのためには次を行います。

-  プラグインフォルダー内の Newtonsoft ファイルを左クリックし、[ **インスペクター] パネル** を確認します。 **プラットフォーム** があることを確認します。 [ **UWP] タブ** にアクセスし、[ **処理が行われない** ようにする] もオンにします。

    ![Unity での Dll のインポート](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a>章 8-ShelfKeeper クラスを作成する

**ShelfKeeper** クラスは、シーンで生成された UI と製品を制御するメソッドをホストします。

インポートされたパッケージの一部として、このクラスは不完全ですが、指定されています。 このクラスは、次のように完了します。

1.  **ShelfKeeper** スクリプトを **Scripts** フォルダー内でダブルクリックして、 **Visual Studio 2017** で開きます。

2.  スクリプト内の既存のすべてのコードを次のコードに置き換えます。このコードは、時刻と日付を設定し、製品を表示するメソッドを持っています。

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  **Unity** に戻る前に、変更内容を **Visual Studio** に保存してください。

4.  Unity エディターに戻り、 **ShelfKeeper** クラスが次のようになっていることを確認します。

    ![ShelfKeeper クラスを作成する](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > スクリプトに参照ターゲット (つまり *Date (テキストメッシュ)*) がない場合は、対応するオブジェクトを **階層パネル** からターゲットフィールドにドラッグするだけです。 必要に応じて、以下の説明を参照してください。
    > 
    > 1.  **ShelfKeeper** コンポーネントスクリプト内の **生成ポイント** の配列を、左クリックして開きます。 サブセクションは、配列のサイズを示す **size** という名前で表示されます。 [**サイズ**] の横にあるテキストボックスに「 **3** 」と入力し、 **enter** キーを押すと、3つのスロットが下に作成されます。
    > 2. **階層** 内で、**時間表示** オブジェクトを展開します (横にある矢印を左クリックします)。 次に、 ***_ 階層内から*_メインカメラ_ _** をクリックして、**インスペクター** にその情報が表示されるようにします。
    > 3. [**階層] パネル** で **メインカメラ** を選択します。 [**階層] パネル** の **日付** と **時刻** のオブジェクトを、 **ShelfKeeper** コンポーネントの **メインカメラ** の **インスペクター** 内の [ **date text** ] および [ **time] テキスト** スロットにドラッグします。
    > 4. イメージに示されているように、[**階層] パネル**(*棚* オブジェクトの下) から、**生成ポイント** の配列の下にある **3** **要素** 参照ターゲットに **生成ポイント** をドラッグします。
    > 
    >     ![ShelfKeeper クラスを作成する](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a>第9章-ProductPrediction クラスを作成する

次に作成するクラスは、 **Productprediction** クラスです。

このクラスの役割は次のとおりです。

-   現在の日付と時刻を指定して、 **Machine Learning サービス** インスタンスを照会しています。

-   JSON 応答を使用可能なデータに逆シリアル化しています。

-   データを解釈し、3つの推奨される製品を取得します。

-   **ShelfKeeper** クラスのメソッドを呼び出して、シーンにデータを表示します。

このクラスを作成するには:

1.  [**プロジェクト] パネル** の [**スクリプト**] フォルダーにアクセスします。

2.  フォルダー内を右クリックし、[C# スクリプトの **作成**] をクリック  >  **C# Script** します。 **Productprediction** のスクリプトを呼び出します。

3.  新しい **Productprediction** スクリプトをダブルクリックして、 **Visual Studio 2017** で開きます。

4.  [ **ファイルの変更が検出されまし** た] ダイアログボックスが表示されたら、[ソリューションの *_再読み込み_*] をクリックします。

5.  ProductPrediction クラスの先頭に次の名前空間を追加します。

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  **Productprediction** クラス内で、複数の入れ子になったクラスで構成される次の2つのオブジェクトを挿入します。 これらのクラスは、Machine Learning サービスの JSON をシリアル化および逆シリアル化するために使用されます。

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  次に、前のコードの上に次の変数を追加します (JSON 関連のコードは、スクリプトの一番下にあり、他のすべてのコードの下にあります)。

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > Machine Learning ポータルから、 **主キー** と **要求-応答のエンドポイント** を、ここでの変数に挿入してください。 次の画像は、キーとエンドポイントを取得した場所を示しています。 
    >  
    > ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-53-2.png)

8.  このコードを **Start ()** メソッド内に挿入します。 **Start ()** メソッドは、クラスの初期化時に呼び出されます。

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  Windows から日付と時刻を収集し、Machine Learning 実験でテーブルに格納されているデータと比較するために使用できる形式に変換するメソッドを次に示します。

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. **Update ()** メソッドは、このクラスでは使用されないため、**削除** できます。

11. 次のメソッドを追加します。このメソッドは、現在の日付と時刻を Machine Learning エンドポイントに伝え、JSON 形式で応答を受信します。

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialize the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. 次のメソッドを追加します。このメソッドは、JSON 応答を逆シリアル化し、逆シリアル化の結果を **ShelfKeeper** クラスに伝達します。 この結果は、現在の日付と時刻を最も多く販売するために予測される3つの項目の名前になります。 次のコードを **Productprediction** クラスの前のメソッドの下に挿入します。

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. **Visual Studio** を保存し、 **Unity** に戻ります。

14. **Productprediction** クラススクリプトを **Script** フォルダーから **メインカメラ** オブジェクトにドラッグします。

15. シーンとプロジェクト **ファイル** の保存  >  **シーン/ファイル**  >  **保存プロジェクト** を保存します。

## <a name="chapter-10---build-the-uwp-solution"></a>第10章-UWP ソリューションのビルド

この時点で、プロジェクトを UWP ソリューションとしてビルドし、スタンドアロンアプリケーションとして実行できるようになりました。

ビルドするには:

1.  [**ファイル**] [保存] [シーン] をクリックして、現在のシーンを保存  >  **Save Scenes** します。

2.  ファイルの **File**  >  **ビルド設定** に進む

3.  **Unity C# プロジェクト** と呼ばれるチェックボックスをオンにします (ビルドの完了後にクラスを編集できるため、これは重要です)。

4.  [開いている **シーンの追加**] をクリックします。

5.  [**ビルド**] をクリックします。

    ![UWP ソリューションを構築する](images/AzureLabs-Lab7-54.png)

6.  ソリューションをビルドするフォルダーを選択するように求められます。

7.  **ビルド** フォルダーを作成し、そのフォルダー内で、適切な名前を指定して別のフォルダーを作成します。

8.  新しいフォルダーをクリックし、[ **フォルダーの選択**] をクリックして、その場所でビルドを開始します。

    ![UWP ソリューションを構築する](images/AzureLabs-Lab7-55.png)

    ![UWP ソリューションを構築する](images/AzureLabs-Lab7-56.png)

9.  Unity のビルドが完了すると (時間がかかる場合があります)、ビルドの場所で **ファイルエクスプローラー** ウィンドウを開きます (ウィンドウの上に常に表示されるとは限りませんが、新しいウィンドウが追加されたことが通知されます)。

## <a name="chapter-11---deploy-your-application"></a>第11章-アプリケーションのデプロイ

アプリケーションをデプロイするには:

1.  新しい Unity ビルド ( **アプリ** フォルダー) に移動し、 **Visual Studio** でソリューションファイルを開きます。

2.  Visual Studio を開いた状態で、NuGet パッケージを復元する必要があります。これを行うには、MachineLearningLab_Build ソリューションを右クリックし、(Visual Studio の右側にある) ソリューションエクスプローラーから [NuGet パッケージの復元] をクリックします。

    ![NuGet パッケージの追加](images/AzureLabs-Lab7-57.png)

3.  ソリューション構成で、[ **デバッグ**] を選択します。

4.  ソリューションプラットフォームで、[ **x86**, **ローカルコンピューター**] を選択します。 

    > Microsoft HoloLens の場合、これを *リモートコンピューター* に設定する方が簡単な場合があります。これにより、コンピューターにテザリングさされることはありません。 ただし、次の手順も実行する必要があります。
    > - HoloLens の **IP アドレス** を確認します。これは、 *[設定 > ネットワーク & インターネット > Wi-Fi > 詳細オプション]* にあります。IPv4 は、使用するアドレスです。 
    > - **開発者モード** が **オンに** なっていることを確認します。*開発者向けのセキュリティ > の更新プログラム & の > の設定* にあります。

    ![NuGet パッケージの追加](images/AzureLabs-Lab7-58.png)

5.  [ **ビルド] メニュー** の [ **ソリューションの配置** ] をクリックして、アプリケーションを PC にサイドロードします。

6.  アプリがインストール済みのアプリの一覧に表示され、起動できる状態になります。

Mixed Reality アプリケーションを実行すると、Unity シーンで設定されたベンチが表示されます。また、初期化時に、Azure 内に設定したデータがフェッチされます。 データはアプリケーション内で逆シリアル化され、現在の日付と時刻の上位3つの結果が、ベンチに3つのモデルとして視覚的に表示されます。


## <a name="your-finished-machine-learning-application"></a>完成した Machine Learning アプリケーション
 
これで、Azure Machine Learning を活用してデータ予測を行い、シーンに表示する mixed reality アプリを構築しました。

![NuGet パッケージの追加](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a>演習

**演習1**

アプリケーションの並べ替え順序を試して、3つの下位予測がシェルフに表示されるようにします。このデータも役に立つ可能性があるためです。

**演習2**

**Azure テーブル** を使用すると、新しいテーブルに気象情報が挿入され、データを使用して新しい実験が作成されます。
