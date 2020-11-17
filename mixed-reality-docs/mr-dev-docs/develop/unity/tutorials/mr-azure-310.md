---
title: MR と Azure 310 - 物体検出
description: このコースでは、機械学習モデルをトレーニングする方法を学習してから、トレーニング済みのモデルを使用して、類似したオブジェクトと、実際の世界でのその位置を混合の現実アプリケーションから認識します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, カスタムビジョン, オブジェクト検出, mixed reality, academy, unity, チュートリアル, api, hololens, Windows 10, Visual Studio
ms.openlocfilehash: 10f3b2b8f8422a20c39a4d89568e42ca530683c2
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679461"
---
# <a name="mr-and-azure-310-object-detection"></a>Mr と Azure 310: オブジェクトの検出

>[!NOTE]
>Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。  そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。  これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。  これらは、サポートされているデバイス上で継続して動作するように、保守されます。 今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。  この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。

<br>

このコースでは、Azure Custom Vision 使用して、混合の現実アプリケーションの "オブジェクト検出" 機能を使用して、提供されたイメージ内でカスタムビジュアルコンテンツとその空間位置を認識する方法を学習します。

このサービスでは、オブジェクトイメージを使用して機械学習モデルをトレーニングすることができます。 次に、トレーニング済みのモデルを使用して、よく似たオブジェクトを認識し、実際の世界での場所を概算します。これは、Microsoft HoloLens のカメラキャプチャや、カメラが PC for イマーシブ (VR) ヘッドセットに接続することによって提供されます。

![コースの結果](images/AzureLabs-Lab310-00.png)

**Azure Custom Vision、オブジェクト検出** は Microsoft のサービスであり、開発者はカスタムイメージ分類子を作成できます。 これらの分類子を新しいイメージと共に使用して、その新しいイメージ内のオブジェクトを検出し、イメージ内に **ボックスの境界** を指定することができます。 このサービスは、シンプルで使いやすいオンラインポータルを提供して、このプロセスを効率化します。 詳細については、次のリンク先を参照してください。

* [Azure Custom Vision ページ](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [制限とクォータ](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

このコースが完了すると、mixed reality アプリケーションが完成し、次のことができるようになります。

1. ユーザーは、Azure Custom Vision Service、オブジェクト検出を使用してトレーニングされたオブジェクトを *見つめ* ます。 
2. ユーザーは *Tap* ジェスチャを使用して、表示内容のイメージをキャプチャします。
3. アプリは、Azure Custom Vision Service にイメージを送信します。
4. サービスからの応答が表示されます。これにより、認識の結果がワールドスペーステキストとして表示されます。 これは、認識されたオブジェクトの世界の位置を理解し、イメージで検出された *タグ* を使用してラベルテキストを提供する方法として、Microsoft HoloLens の空間トラッキングを利用することで実現します。

また、イメージを手動でアップロードする方法、タグを作成する方法、サービスをトレーニングする方法についても説明します。このコースでは、送信するイメージ内の *境界ボックス* を設定することによって、さまざまなオブジェクト (例では、カップ) を認識します。 

> [!IMPORTANT]
> アプリの作成と使用の後、開発者は Azure Custom Vision Service に戻り、サービスによって行われた予測を特定して、それらが適切かどうかを判断する必要があります (サービスに何かタグを付け、 *境界ボックス* を調整します)。 その後、サービスを再トレーニングできます。これにより、実際のオブジェクトを認識する確率が高まります。

このコースでは、Azure Custom Vision Service のオブジェクト検出から Unity ベースのサンプルアプリケーションに結果を取得する方法について説明します。 これらの概念は、構築しているカスタムアプリケーションに適用する必要があります。

## <a name="device-support"></a>デバイス サポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="../../../hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 310:物体検出</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>必須コンポーネント

> [!NOTE]
> このチュートリアルは、Unity と C# の基本的な経験がある開発者向けに設計されています。 また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証された内容 (2018 年7月) を表しています。 「 [ツールのインストール](../../install-the-tools.md) 」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に記載されているものより新しいソフトウェアの内容と完全に一致するとは限りません。

このコースでは、次のハードウェアとソフトウェアをお勧めします。

- 開発用 PC
- [開発者モードが有効になっている Windows 10 の作成者の更新プログラム (またはそれ以降)](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [最新の Windows 10 SDK](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Unity 2017.4 LTS](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Visual Studio 2017](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- 開発者モードが有効になっている[Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details)
- Azure のセットアップと Custom Vision Service の取得のためのインターネットアクセス
-  Custom Vision が認識するオブジェクトごとに、少なくとも 15 (15) のイメージが必要です)。 必要に応じて、このコースで既に提供されているイメージ、 [一連のカップ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)) を使用できます。

## <a name="before-you-start"></a>開始する前に

1.  このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。
2.  HoloLens をセットアップしてテストします。 HoloLens のセットアップをサポートする必要がある場合は、 [hololens セットアップに関する記事にアクセスして](https://docs.microsoft.com/hololens/hololens-setup)ください。 
3.  新しい HoloLens アプリの開発を開始するときは、調整とセンサーのチューニングを実行することをお勧めします (ユーザーごとにこれらのタスクを実行するのに役立つ場合があります)。 

調整の詳細については、 [「HoloLens の調整に関する記事へのリンク」を](../../../calibration.md#hololens-2)参照してください。

センサーチューニングの詳細については、 [HoloLens センサーチューニングに関する記事へのリンクを](../../../sensor-tuning.md)参照してください。

## <a name="chapter-1---the-custom-vision-portal"></a>章 1-Custom Vision ポータル

**Azure Custom Vision Service** を使用するには、アプリケーションで使用できるようにするインスタンスを構成する必要があります。

1.  [ **Custom Vision Service** メインページに](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)移動します。

2.  [ **はじめに**] をクリックします。

    ![](images/AzureLabs-Lab310-01.png)

3.  Custom Vision ポータルにサインインします。

    ![](images/AzureLabs-Lab310-02.png)

4.  まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。 このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。

5.  初めてログインした後は、 *サービスパネルの使用条件* を確認するメッセージが表示されます。 *条件に同意* するには、チェックボックスをオンにします。 [ **同意** する] をクリックします。

    ![](images/AzureLabs-Lab310-03.png)

6.  使用条件に同意すると、 *[マイプロジェクト* ] セクションが表示されるようになります。 [ **新しいプロジェクト**] をクリックします。

    ![](images/AzureLabs-Lab310-04.png)

7.  右側にタブが表示され、プロジェクトのフィールドを指定するように求められます。

    1.  プロジェクトの名前を挿入する

    2.  プロジェクトの説明を挿入します (**省略可能**)

    3.  リソースグループを選択するか、新しい **リソースグループ** を作成します。 リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。 1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのコースなど) を共通のリソースグループに保持することをお勧めします。

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > [Azure リソースグループの詳細については、関連するドキュメントを](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)参照してください。

    4.  プロジェクトの **種類** を **オブジェクト検出 (プレビュー)** として設定します。

8.  操作が完了すると、[ **プロジェクトの作成**] をクリックすると、Custom Vision Service プロジェクトページにリダイレクトされます。


## <a name="chapter-2---training-your-custom-vision-project"></a>第2章-Custom Vision プロジェクトのトレーニング

Custom Vision ポータルでは、主な目的は、イメージ内の特定のオブジェクトを認識するようにプロジェクトをトレーニングすることです。

アプリケーションで認識するオブジェクトごとに、少なくとも15個のイメージが必要です。 このコースに用意されているイメージ ([一連のカップ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)) を使用できます。

Custom Vision プロジェクトをトレーニングするには:

1.  [タグ] の横にあるボタンをクリックし **+** ます。 **Tags**

    ![](images/AzureLabs-Lab310-06.png)

2.  イメージを関連付けるために使用されるタグの **名前** を追加します。 この例では、認識に cups のイメージを使用しているため、この **カップ** にタグを付けます。 [ **保存** ] をクリックします。

    ![](images/AzureLabs-Lab310-07.png)

3.  **タグ** が追加されていることがわかります (表示するには、ページの再読み込みが必要になる場合があります)。 

    ![](images/AzureLabs-Lab310-08.png)

4.  ページの中央にある [ **イメージの追加** ] をクリックします。

    ![](images/AzureLabs-Lab310-09.png)

5.  [ **ローカルファイルの参照**] をクリックし、1つのオブジェクトに対してアップロードするイメージを選択します。最小値は 15 (15) です。

    > [!TIP]
    >  アップロードには、一度に複数のイメージを選択できます。

    ![](images/AzureLabs-Lab310-10.png)

6.  プロジェクトをトレーニングするすべてのイメージを選択したら、[ **ファイルのアップロード (ファイルのアップロード** ) をクリックします。 ファイルのアップロードが開始されます。 アップロードの確認が完了したら、[ **完了**] をクリックします。

    ![](images/AzureLabs-Lab310-11.png)

7.  この時点で、画像はアップロードされますが、タグは付けられません。

    ![](images/AzureLabs-Lab310-12.png)

8.  画像にタグを付けるには、マウスを使用します。 画像にマウスポインターを合わせると、選択の強調表示によって、オブジェクトの周囲に自動的に選択が描画されます。 正確でない場合は、独自のものを描画できます。 これを実現するには、マウスを左クリックし、選択領域をドラッグしてオブジェクトを格納します。 

    ![](images/AzureLabs-Lab310-13.png) 

9. 画像内のオブジェクトを選択した後、小さなプロンプトで *Region タグを追加* するように求められます。 以前に作成したタグ (上の例では "カップ") を選択するか、さらにタグを追加する場合は、に「」と入力し、[ **+] (プラス)** ボタンをクリックします。

    ![](images/AzureLabs-Lab310-14.png) 

10. 次の画像にタグを付けるには、ブレードの右側にある矢印をクリックするか、[タグ] ブレードを閉じます (ブレードの右上隅にある [ **X** ] をクリックします)。次の画像をクリックします。 次のイメージの準備ができたら、同じ手順を繰り返します。 すべてのタグが付けられるまで、アップロードしたすべてのイメージに対してこの操作を行います。 

    > [!NOTE]
    >  次の画像のように、同じイメージ内の複数のオブジェクトを選択できます。 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. すべてのタグを付けたら、画面の左側にある **タグ** 付きボタンをクリックして、タグ付けされたイメージを表示します。 

    ![](images/AzureLabs-Lab310-16.png)

12. これで、サービスをトレーニングする準備ができました。 [ **トレーニング** ] ボタンをクリックすると、最初のトレーニングイテレーションが開始されます。

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. ビルドされると、[ **既定** の **URL と予測 URL**] という2つのボタンが表示されます。 [ **既定値** に設定] をクリックし、[ **予測 URL**] をクリックします。

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > このから提供されるエンドポイントは、既定としてマークされている *反復処理* のいずれかに設定されます。 そのため、後で新しい *イテレーション* を作成して既定として更新する場合は、コードを変更する必要はありません。

14. **予測 URL** をクリックしたら、*メモ帳* を開き、 **Url** ("**予測エンドポイント**" とも呼ばれます) と **サービス予測キー** をコピーして貼り付けます。これにより、コードの後で必要になったときに取得できるようになります。

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>章 3-Unity プロジェクトの設定

次に示すのは、mixed reality で開発するための一般的な設定です。そのため、他のプロジェクトに適したテンプレートです。

1.  **Unity** を開き、[**新規**] をクリックします。

    ![](images/AzureLabs-Lab310-21.png)

2.  ここで、Unity プロジェクト名を指定する必要があります。 **CustomVisionObjDetection** を挿入します。 プロジェクトの種類が **3d** に設定されていることを確認し、場所を適切な **場所** に設定します (ルートディレクトリの方が適していることに注意してください)。 次に、[ **プロジェクトの作成**] をクリックします。

    ![](images/AzureLabs-Lab310-22.png)

3.  Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。 [ **Edit*  >  *設定* の編集*] に移動し、新しいウィンドウで [**外部ツール**] に移動します。 **外部スクリプトエディター** を **Visual Studio** に変更します。 [ **基本設定** ] ウィンドウを閉じます。

    ![](images/AzureLabs-Lab310-23.png)

4.  次に、[ **ファイル > ビルド設定** ] に移動し、 **プラットフォーム** を *ユニバーサル Windows プラットフォーム* に切り替えて、[ **プラットフォームの切り替え** ] ボタンをクリックします。

    ![](images/AzureLabs-Lab310-24.png)

5.  同じ [ **ビルドの設定** ] ウィンドウで、次の項目が設定されていることを確認します。

    1.  **ターゲットデバイス** が **HoloLens** に設定されています        
    2.  **ビルドの種類** が **D3D** に設定されています
    3.  **SDK** は最新の **インストール** に設定されています
    4.  **Visual Studio のバージョン** が、**インストールされている最新** バージョンに設定されています
    5.  **ビルドと実行** は **ローカルコンピューター** に設定されています            
    6.  それ以外の設定は、[ **ビルド設定**] の [既定] のままにしておきます。

        ![](images/AzureLabs-Lab310-25.png)

6.  同じ **ビルド設定** ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 **インスペクター** が配置されている領域の関連パネルが開きます。

7. このパネルでは、いくつかの設定を確認する必要があります。

    1.  [ **その他の設定** ] タブで、次のようにします。

        1.  **Scripting Runtime のバージョン** は **実験的** (.net 4.6 と同等) である必要があります。これにより、エディターを再起動する必要が生じます。

        2. **スクリプトバックエンド** は **.net** である必要があります。

        3. **API の互換性レベル** は **.net 4.6** である必要があります。

            ![](images/AzureLabs-Lab310-26.png)

    2.  [ **発行の設定** ] タブの [ **機能**] で、次の項目を確認します。

        1. **InternetClient**

        2.  **Web カメラ**

        3. **SpatialPerception**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  パネルの下にある [ **XR settings** (発行の **設定**] の下にあります) で、[ **Virtual reality がサポートされる**] を選択し、 **Windows Mixed reality SDK** が追加されていることを確認します。

        ![](images/AzureLabs-Lab310-29.png)

8.  **ビルド設定** に戻り、 *Unity C \# プロジェクト* はグレーで表示されなくなりました。この横にあるチェックボックスをオンにします。

9.  **[ビルド設定]** ウィンドウを閉じます。

10. **エディター** で、[プロジェクト設定の **編集**] [グラフィック] の順にクリックし  >  **Project Settings**  >  **Graphics** ます。

    ![](images/AzureLabs-Lab310-30.png)

11. [ **インスペクター] パネル** で、 *グラフィックスの設定* が開きます。 " **常にシェーダーを含める**" という配列が表示されるまで下にスクロールします。 **サイズ** 変数を1つ増やしてスロットを追加します (この例では8であるため、9にしました)。 次に示すように、配列の最後の位置に新しいスロットが表示されます。

    ![](images/AzureLabs-Lab310-31.png)

12. スロットで、スロットの横にある小さなターゲット円をクリックして、シェーダーの一覧を開きます。 **レガシシェーダー/透明/拡散** シェーダーを探し、ダブルクリックします。 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>第4章-CustomVisionObjDetection Unity パッケージのインポート

このコースでは、 **unitypackage** という名前の Unity 資産パッケージが提供されています。 

> 形Unity でサポートされているすべてのオブジェクト (シーン全体を含む) は、 **unitypackage** ファイルにパッケージ化し、他のプロジェクトでエクスポート/インポートできます。 これは、さまざまな **Unity プロジェクト** 間でアセットを移動する最も安全で効率的な方法です。

[ダウンロードする必要がある AZURE MR-310 パッケージ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)については、こちらを参照してください。

1.  Unity ダッシュボードを使用して、画面の上部にあるメニューの [ **アセット** ] をクリックし、[ **パッケージのインポート > カスタムパッケージ**] をクリックします。

    ![](images/AzureLabs-Lab310-33.png)

2.  ファイルピッカーを使用して **unitypackage** パッケージを選択し、[ **開く**] をクリックします。 この資産のコンポーネントの一覧が表示されます。 インポートを確認するには、[ **インポート** ] ボタンをクリックします。

    ![](images/AzureLabs-Lab310-34.png)

3.  インポートが完了すると、パッケージのフォルダーが [ **Assets** ] フォルダーに追加されていることがわかります。 この種のフォルダー構造は、Unity プロジェクトで一般的に使用されます。

    ![](images/AzureLabs-Lab310-35.png)

    1.  **素材** フォルダーには、**見つめカーソル** によって使用される素材が含まれています。 

    2.  **プラグイン** フォルダーには、サービス web 応答を逆シリアル化するためにコードによって使用される Newtonsoft DLL が含まれています。 フォルダーに含まれる2つの異なるバージョン (2) は、ライブラリを Unity エディターと UWP ビルドの両方で使用およびビルドできるようにするために必要です。 

    3.  **Prefabs** フォルダーには、シーンに含まれる Prefabs が含まれています。 これらには次のようなものがあります。

        1.  **GazeCursor** は、アプリケーションで使用されるカーソルです。 は、SpatialMapping prefab と連携して、物理オブジェクト上のシーンに配置できます。
        2.  **ラベル**。これは、必要に応じてシーンにオブジェクトタグを表示するために使用される UI オブジェクトです。
        3.  **SpatialMapping**。これは、アプリケーションが Microsoft HoloLens の空間トラッキングを使用して仮想マップの作成を使用できるようにするオブジェクトです。

    4.  このコースの構築済みシーンが現在含まれている **シーン** フォルダー。

4.  [**プロジェクト] パネル** で [**シーン**] フォルダーを開き、 **ObjDetectionScene** をダブルクリックして、このコースで使用するシーンを読み込みます。

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  **コードは含ま** れていません。このコースに従ってコードを記述します。

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>Chapter 5-CustomVisionAnalyser クラスを作成します。

この時点で、コードを記述する準備ができました。 最初に、 **CustomVisionAnalyser** クラスを使用します。

> [!NOTE]
> 次に示すコードで作成された **Custom Vision Service** への呼び出しは、 **Custom Vision REST API** を使用して行われます。 これを使用すると、この API を実装して使用する方法を確認できます (独自のものを実装する方法を理解するために役立ちます)。 Microsoft では、サービスの呼び出しを行うために使用できる **CUSTOM VISION SDK** を提供していることに注意してください。 詳細については、 [CUSTOM VISION SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)に関する記事をご覧ください。

このクラスの役割は次のとおりです。

- バイト配列としてキャプチャされた最新のイメージを読み込んでいます。

- 分析のために、Azure **Custom Vision Service** インスタンスにバイト配列を送信しています。

- JSON 文字列として応答を受信しています。

- 応答を逆シリアル化し、結果の **予測** を **SceneOrganiser** クラスに渡します。これにより、応答の表示方法が決まります。

このクラスを作成するには:

1.  [**プロジェクト] パネル** にある **アセットフォルダー** を右クリックし、[フォルダーの **作成**] をクリックし  >  **Folder** ます。 フォルダー **スクリプト** を呼び出します。

    ![](images/AzureLabs-Lab310-37.png)

2.  新しく作成したフォルダーをダブルクリックして開きます。

3.  フォルダー内を右クリックし、[ **Create**  >  **C \# スクリプト** の作成] をクリックします。 スクリプトに CustomVisionAnalyser という名前を指定 **します。**

4.  新しい **CustomVisionAnalyser** スクリプトをダブルクリックして、 **Visual Studio で開きます。**

5.  ファイルの先頭で次の名前空間が参照されていることを確認します。

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  **CustomVisionAnalyser** クラスに、次の変数を追加します。

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > **PredictionKey** 変数に **サービス予測キー** を挿入し、**予測エンドポイント** を **predictionEndpoint** 変数に挿入してください。 [前の手順14でメモ帳](#chapter-2---training-your-custom-vision-project)にコピーしました。

7.  インスタンス変数を初期化するには、起動前 **()** のコードを追加する必要があります。

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  コルーチンを (static **GetImageAsByteArray ()** メソッドを使用して) 追加します。これにより、 **imagecapture** クラスによってキャプチャされたイメージの分析結果が得られます。

    > [!NOTE]
    > **分析 Seimagecapture** コルーチンには、まだ作成していない **SceneOrganiser** クラスの呼び出しがあります。 そのため、 **これらの行はコメントの付いたままに** しておきます。

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

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

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
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

9. **Start ()** および **Update ()** メソッドは使用されないため、削除します。 

10.  **Unity** に戻る前に、変更内容を **Visual Studio** に保存しておいてください。

> [!IMPORTANT]
> 前に説明したように、エラーが発生する可能性があるコードについては気にしないでください。これにより、後でさらにクラスを修正します。

## <a name="chapter-6---create-the-customvisionobjects-class"></a>Chapter 6-CustomVisionObjects クラスの作成

ここで作成するクラスは、 **CustomVisionObjects** クラスです。

このスクリプトには、Custom Vision Service に対する呼び出しをシリアル化および逆シリアル化するために、他のクラスによって使用される多数のオブジェクトが含まれています。

このクラスを作成するには:

1.  **Scripts** フォルダー内を右クリックし、[ **Create**  >  **C \# Script**] をクリックします。 スクリプト CustomVisionObjects を呼び出し **ます。**

2.  新しい **CustomVisionObjects** スクリプトをダブルクリックして、 **Visual Studio で開きます。**

3.  ファイルの先頭で次の名前空間が参照されていることを確認します。

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  **CustomVisionObjects** クラス内の **Start ()** および **Update ()** メソッドを削除します。このクラスは空になります。

    > [!WARNING]
    > 次の手順に従うことが重要です。 **CustomVisionObjects** クラス内に新しいクラス宣言を配置すると、 **AnalysisRootObject** と **BoundingBox** が見つからないことを示す [10 章](#chapter-10---create-the-imagecapture-class)のコンパイルエラーが発生します。

5.  **CustomVisionObjects** クラスの *外* に次のクラスを追加します。 これらのオブジェクトは、応答データをシリアル化および逆シリアル化するために **Newtonsoft** ライブラリによって使用されます。

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
    /// JSON of images submitted
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
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  **Unity** に戻る前に、変更内容を **Visual Studio** に保存しておいてください。

## <a name="chapter-7---create-the-spatialmapping-class"></a>第7章-SpatialMapping クラスの作成

このクラスは、仮想オブジェクトと実際のオブジェクト間の競合を検出できるように、シーンで **空間マッピング Collider** を設定します。

このクラスを作成するには:

1.  **Scripts** フォルダー内を右クリックし、[ **Create**  >  **C \# Script**] をクリックします。 スクリプト SpatialMapping を呼び出し **ます。**

2.  新しい **SpatialMapping** スクリプトをダブルクリックして、 **Visual Studio で開きます。**

3.  **SpatialMapping** クラスの上に参照されている次の名前空間があることを確認します。

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  次に、 **Start ()** メソッドの上に、 **SpatialMapping** クラス内に次の変数を追加します。

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  起動した **()** を追加し、 **Start ()** を追加します。

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  **Update ()** メソッドを削除します。

7.  **Unity** に戻る前に、変更内容を **Visual Studio** に保存しておいてください。


## <a name="chapter-8---create-the-gazecursor-class"></a>章 8-GazeCursor クラスを作成する

このクラスは、前の章で作成した **SpatialMappingCollider** を使用することによって、実際の場所にカーソルを適切な位置に設定する役割を担います。

このクラスを作成するには:

1.  **Scripts** フォルダー内を右クリックし、[ **Create**  >  **C \# Script**] をクリックします。 **GazeCursor** スクリプトを呼び出します。

2.  新しい **GazeCursor** スクリプトをダブルクリックして、 **Visual Studio で開きます。**

3.  **GazeCursor** クラスの上に、次の名前空間が参照されていることを確認します。

    ```csharp
    using UnityEngine;
    ```

4.  次に、 **Start ()** メソッドの上に、 **GazeCursor** クラス内に次の変数を追加します。 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  **Start ()** メソッドを次のコードで更新します。

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  **Update ()** メソッドを次のコードで更新します。

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > **SceneOrganiser** クラスが見つからない場合のエラーについては、次の章で作成します。

7. **Unity** に戻る前に、変更内容を **Visual Studio** に保存しておいてください。

## <a name="chapter-9---create-the-sceneorganiser-class"></a>第9章-SceneOrganiser クラスの作成

このクラスは次のことを行います。

-   適切なコンポーネントをアタッチして、 *メインカメラ* を設定します。

-   オブジェクトが検出されると、実際の世界での位置を計算し、適切な **タグ名** の近くに **タグラベル** を配置する必要があります。    

このクラスを作成するには:

1.  **Scripts** フォルダー内を右クリックし、[ **Create**  >  **C \# Script**] をクリックします。 スクリプトに **SceneOrganiser** という名前を指定します。

2.  新しい **SceneOrganiser** スクリプトをダブルクリックして、 **Visual Studio で開きます。**

3.  **SceneOrganiser** クラスの上に参照されている次の名前空間があることを確認します。

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  次に、 **Start ()** メソッドの上に、 **SceneOrganiser** クラス内に次の変数を追加します。

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  **Start ()** および **Update ()** メソッドを削除します。

6.  変数の下に、起動前 **()** メソッドを追加します。このメソッドは、クラスを初期化し、シーンを設定します。

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  **PlaceAnalysisLabel ()** メソッドを追加します。このメソッドは、シーン内のラベルを *インスタンス化* します (この時点ではユーザーには表示されません)。 また、イメージが配置されている四角形も、実際の世界と重複しています。 これが重要なのは、分析後にサービスから取得したボックスの座標が、実際のオブジェクトのおおよその場所を決定するために、このクワッドにトレースされます。 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  **FinaliseLabel ()** メソッドを追加します。 以下の処理を担当します。

    *   *ラベル* のテキストに、最も信頼度の高い予測の *タグ* を設定します。
    *   前に配置した、四角形の *境界ボックス* の計算を呼び出し、そのラベルをシーンに配置します。
    *   *境界ボックス* に向かって Raycast を使用してラベルの深さを調整します。これは、実際の世界のオブジェクトに対して競合します。
    * キャプチャプロセスをリセットして、ユーザーが別のイメージをキャプチャできるようにします。

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  **CalculateBoundingBoxPosition ()** メソッドを追加します。このメソッドは、サービスから取得された *境界ボックス* 座標を変換するために必要な多数の計算をホストし、それらを4つに均等に再作成します。

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. **Unity** に戻る前に、変更内容を **Visual Studio** に保存しておいてください。

    > [!IMPORTANT]
    > 続行する前に、 **CustomVisionAnalyser** クラスを開き、 **AnalyseLastImageCaptured ()** メソッド内で次の行を *コメント* 解除します。
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> **Imagecapture** クラス ' found ' が見つからないことを心配しないでください。このメッセージは、次の章で作成します。


## <a name="chapter-10---create-the-imagecapture-class"></a>Chapter 10-ImageCapture クラスを作成する

次に作成するクラスは、 **Imagecapture** クラスです。

このクラスの役割は次のとおりです。

*   HoloLens カメラを使用してイメージをキャプチャし、 *アプリ* フォルダーに格納します。
*   ユーザーからの *Tap* ジェスチャを処理します。

このクラスを作成するには:

1.  前に作成した **Scripts** フォルダーにアクセスします。

2.  フォルダー内を右クリックし、[ **Create**  >  **C \# スクリプト** の作成] をクリックします。 スクリプトに「 **Imagecapture**」という名前を指定します。

3.  新しい **Imagecapture** スクリプトをダブルクリックして、 **Visual Studio で開きます。**

4.  ファイルの先頭にある名前空間を次のように置き換えます。

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  次に、 **Start ()** メソッドの上に、 **imagecapture** クラス内に次の変数を追加します。

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

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
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
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > カーソルが **緑色** の場合は、カメラを使用してイメージを撮影できることを意味します。 カーソルが **赤** の場合、カメラがビジー状態であることを示します。

8.  アプリケーションがイメージキャプチャプロセスを開始してイメージを格納するために使用するメソッドを追加します。

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
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

9.  写真がキャプチャされ、分析の準備ができたときに呼び出されるハンドラーを追加します。 結果は、分析のために **CustomVisionAnalyser** に渡されます。

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. **Unity** に戻る前に、変更内容を **Visual Studio** に保存しておいてください。

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>Chapter 11-シーンでのスクリプトの設定

このプロジェクトに必要なすべてのコードを記述したので、次はシーンでスクリプトを設定し、prefabs でスクリプトを正しく動作させるための時間です。

1.  **Unity エディター** で、[**階層] パネル** の **メインカメラ** を選択します。
2.  [ **インスペクター] パネル** で、 **メインカメラ** を選択した状態で [ **コンポーネントの追加**] をクリックし、 **SceneOrganiser** script を検索して、ダブルクリックして追加します。

    ![](images/AzureLabs-Lab310-38.png)

3.  [**プロジェクト] パネル** で、 **Prefabs フォルダー** を開き、次の図に示すように、*メインカメラ* に追加した **SceneOrganiser** スクリプト内の [空の参照ターゲットの *ラベルのラベル*] に "prefab" と **いうラベルを** ドラッグします。

    ![](images/AzureLabs-Lab310-39.png)

4.  [**階層] パネル** で、**メインカメラ** の **GazeCursor** 子を選択します。
5.  [ **インスペクター] パネル** で、 **GazeCursor** を選択した状態で [ **コンポーネントの追加**] をクリックし、 **GazeCursor** スクリプトを検索して、ダブルクリックして追加します。

    ![](images/AzureLabs-Lab310-40.png)

6.  ここでも、[**階層] パネル** で、**メインカメラ** の **SpatialMapping** 子を選択します。
7.  [ **インスペクター] パネル** で、 **SpatialMapping** を選択した状態で [ **コンポーネントの追加**] をクリックし、 **SpatialMapping** スクリプトを検索して、ダブルクリックして追加します。

    ![](images/AzureLabs-Lab310-41.png)

まだ設定していない残りのスクリプトは、実行時に **SceneOrganiser** スクリプトのコードによって追加されます。

## <a name="chapter-12---before-building"></a>第12章-ビルド前

アプリケーションの徹底的なテストを実行するには、Microsoft HoloLens にサイドロードする必要があります。

これを行う前に、次のことを確認してください。

-  [章 3](#chapter-3---set-up-the-unity-project)で説明したすべての設定が正しく設定されています。
- スクリプト **SceneOrganiser** は、 **メインカメラ** オブジェクトにアタッチされます。
- スクリプト **GazeCursor** は、 **GazeCursor** オブジェクトにアタッチされます。
- スクリプト **SpatialMapping** は、 **SpatialMapping** オブジェクトにアタッチされます。
- [第5章](#chapter-5---create-the-customvisionanalyser-class)の手順 6:

    - **サービス予測キー** を **predictionKey** 変数に挿入していることを確認します。
    - **予測エンドポイント** を **predictionEndpoint** クラスに挿入しました。

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>第13章-UWP ソリューションのビルドとアプリケーションのサイドロード

これで、Microsoft HoloLens にデプロイできる UWP ソリューションとしてアプリケーションを構築する準備ができました。 ビルドプロセスを開始するには:

1.  **ファイル > ビルド設定** にアクセスします。

2.  **Unity C \# プロジェクト** をティックします。

3.  [開いている **シーンの追加**] をクリックします。 これにより、現在開いているシーンがビルドに追加されます。

    ![](images/AzureLabs-Lab310-42.png)

4.  [**ビルド**] をクリックします。 Unity は *エクスプローラー* ウィンドウを起動します。このウィンドウでは、アプリを作成するフォルダーを作成して選択する必要があります。 ここでそのフォルダーを作成し、「 **App**」という名前を指定します。 次に、 **アプリ** フォルダーを選択し、[ **フォルダーの選択**] をクリックします。

5.  Unity は、 **アプリ** フォルダーへのプロジェクトのビルドを開始します。

6.  Unity のビルドが完了すると (時間がかかる場合があります)、ビルドの場所で **ファイルエクスプローラー** ウィンドウを開きます (ウィンドウの上に常に表示されるとは限りませんが、新しいウィンドウが追加されたことが通知されます)。

7.  Microsoft HoloLens にデプロイするには、そのデバイスの IP アドレス (リモートデプロイの場合) が必要であり、 **開発者モード** も設定されていることを確認します。 この操作を行うには、次の手順を実行します。

    1.  HoloLens を装着した後、 **設定** を開きます。

    2.  [**ネットワーク & インターネット**  >  **wi-fi**  >  **詳細オプション]** にアクセスします。

    3.  **IPv4** アドレスをメモしておきます。

    4.  次に、[**設定**] に戻り、 **Update & Security**  >  **開発者の**& セキュリティを更新します。

    5.  **開発者モード***をに* 設定します。

8.  新しい Unity ビルド ( **アプリ** フォルダー) に移動し、 **Visual Studio** でソリューションファイルを開きます。

9.  ソリューション構成で、[ **デバッグ**] を選択します。

10. ソリューションプラットフォームで、[ **x86、リモートコンピューター**] を選択します。 リモートデバイスの **IP アドレス** (この場合は、メモした Microsoft HoloLens) を挿入するように求められます。

    ![](images/AzureLabs-Lab310-43.png)

11. [ **ビルド** ] メニューの [ソリューションの **配置** ] をクリックして、アプリケーションを HoloLens にサイドロードします。

12. アプリが Microsoft HoloLens のインストール済みアプリの一覧に表示され、起動できる状態になります。

### <a name="to-use-the-application"></a>アプリケーションを使用するには:

* **Azure Custom Vision Service、オブジェクト検出** でトレーニングしたオブジェクトを調べ、 **Tap ジェスチャ** を使用します。
* オブジェクトが正常に検出された場合は、ワールドスペースの *ラベルのテキスト* がタグ名と共に表示されます。

> [!IMPORTANT]
> 写真をキャプチャしてサービスに送信するたびに、サービスページに戻り、新しくキャプチャしたイメージでサービスを再トレーニングすることができます。 最初に、 *境界ボックス* を修正して、より正確でサービスを再トレーニングする必要がある場合もあります。

> [!NOTE]
> Microsoft HoloLens センサーや Unity の SpatialTrackingComponent が、実際のオブジェクトに対する適切な colliders の配置に失敗した場合、オブジェクトの近くにラベルのテキストが表示されないことがあります。 そのような場合は、別の画面でアプリケーションを使用してみてください。

## <a name="your-custom-vision-object-detection-application"></a>Custom Vision、オブジェクト検出アプリケーション

これで、Azure Custom Vision、オブジェクト検出 API を活用する mixed reality アプリが作成されました。これにより、イメージからオブジェクトを認識し、3D 空間でそのオブジェクトのおおよその位置を指定できます。

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>ボーナス演習

### <a name="exercise-1"></a>演習1

テキストラベルにを追加する場合は、半透明のキューブを使用して、3D *境界ボックス* に実際のオブジェクトをラップします。

### <a name="exercise-2"></a>演習2

Custom Vision Service をトレーニングして、より多くのオブジェクトを認識します。

### <a name="exercise-3"></a>演習3

オブジェクトが認識されたときにサウンドを再生します。

### <a name="exercise-4"></a>演習4

API を使用して、アプリが分析しているのと同じイメージでサービスを再トレーニングします。これにより、サービスの精度が向上します (予測とトレーニングの両方を同時に行うことができます)。
