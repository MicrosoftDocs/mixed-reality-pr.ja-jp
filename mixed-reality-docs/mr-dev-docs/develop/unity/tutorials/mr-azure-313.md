---
title: MR と Azure 313-IoT Hub サービス
description: このコースでは、Ubuntu 16.4 を実行している仮想マシンに Azure IoT Hub サービスを実装し、Microsoft HoloLens またはイマーシブ (VR) ヘッドセットを使用してメッセージデータを視覚化する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: azure, mixed reality, academy, エッジ, iot edge, チュートリアル, api, 通知, 関数, テーブル, hololens, イマーシブ, vr, iot, 仮想マシン, ubuntu, python
ms.openlocfilehash: 14b7eb3774de3cfdd74e7270de63e3a80384cdca
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91689946"
---
# <a name="mr-and-azure-313-iot-hub-service"></a>MR と Azure 313:IoT Hub サービス

>[!NOTE]
>Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。  そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。  これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは " **_ありません_** "。  これらは、サポートされているデバイス上で継続して動作するように、保守されます。 今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。  この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。

![コースの結果](images/AzureLabs-Lab313-00.png)

このコースでは、Ubuntu 16.4 オペレーティングシステムを実行している仮想マシンに **Azure IoT Hub サービス** を実装する方法について説明します。 **Azure Function App** は、Ubuntu VM からメッセージを受信するために使用され、その結果を **azure Table Service** 内に格納します。 その後、Microsoft HoloLens またはイマーシブ (VR) ヘッドセットの **Power BI** を使用して、このデータを表示できるようになります。

このコースの内容は IoT Edge デバイスに *適用されますが* 、このコースでは、物理エッジデバイスへのアクセスを必要としないように、仮想マシン環境に焦点が当てはまります。

このコースを完了すると、次のことを学習できます。

- **IoT Edge モジュール** を仮想マシン (UBUNTU 16 OS) にデプロイします。これは、IoT デバイスを表します。
- コンテナーに格納されているイメージを分析するコードを使用して、 **Azure Custom Vision の Azure Azure の "Azure" Azure** "のモデルを Edge モジュールに追加します。
- 分析結果メッセージを **IoT Hub サービス** に返すようにモジュールを設定します。
- Azure **Function App** を使用して、 **azure テーブル** 内にメッセージを格納します。
- 保存されたメッセージを収集してレポートを作成するように **Power BI** を設定します。
- **Power BI** 内で IoT メッセージデータを視覚化します。

使用するサービスには次のものがあります。

- **Azure IoT Hub** は、開発者が IoT 資産の接続、監視、管理を行うことができるようにする Microsoft Azure サービスです。 詳細については、 [ **Azure IoT Hub サービス**](https://azure.microsoft.com/services/iot-hub/)に関するページを参照してください。

- **Azure Container Registry** は、さまざまな種類のコンテナーについて、開発者がコンテナーイメージを格納できるようにする、Microsoft Azure サービスです。 詳細については、 [ **Azure Container Registry サービス**](https://azure.microsoft.com/services/container-registry/)に関するページを参照してください。

- **Azure Function App** は Microsoft Azure サービスであり、開発者は azure で小さなコードである "functions" を実行できます。 これにより、ローカルアプリケーションではなく、クラウドに作業を委任することができます。これには多くのメリットがあります。 **Azure Functions** は、C \# 、F \# 、Node.js、Java、PHP など、いくつかの開発言語をサポートしています。 詳細については、 [ **Azure Functions** のページ](https://docs.microsoft.com/azure/azure-functions/functions-overview)を参照してください。

- **Azure Storage: テーブル** は Microsoft Azure サービスです。これにより、開発者は構造化された SQL 以外のデータをクラウドに格納し、どこからでも簡単にアクセスできるようになります。 このサービスでは、スキーマのない設計が非常に優れているため、必要に応じてテーブルを進化させることができるため、非常に柔軟性があります。 詳細については、 [ **Azure のテーブル** に関するページを参照してください。](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

このコースでは、IoT Hub サービスを設定して使用する方法と、デバイスによって提供される応答を視覚化する方法について説明します。 これらの概念は、作成するカスタム IoT Hub サービスのセットアップに適用する必要があります。

## <a name="device-support"></a>デバイス サポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="../../../hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 313:IoT Hub サービス</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>前提条件

Microsoft HoloLens など、mixed reality を使用した開発に関する最新の前提条件については、 [ツールのインストール](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) に関する記事をご覧ください。

> [!NOTE]
> このチュートリアルは、Python の基本的な経験がある開発者向けに設計されています。 また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証された内容 (2018 年7月) を表しています。 「 [ツールのインストール](../../install-the-tools.md) 」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に示したソフトウェアより新しいソフトウェアでは完全に一致するとは限りません。

次のハードウェアとソフトウェアが必要です。

- Windows 10 の作成者の更新プログラム (またはそれ以降)、 **開発者モードが有効**

    > [!WARNING]
    > Windows 10 Home Edition で Hyper-v を使用して仮想マシンを実行することはできません。

- Windows 10 SDK (最新バージョン)
- HoloLens、 **開発者モードが有効**
- Visual Studio 2017.15.4 (Azure Cloud Explorer へのアクセスにのみ使用)
- Azure および IoT Hub サービス用のインターネットアクセス。 詳細については、こちらの[IoT Hub サービスへのリンクに関するページを](https://azure.microsoft.com/services/iot-hub/)参照してください。
- 機械学習モデル。 独自のモデルを使用する準備ができていない場合は、 [このコースで提供さ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)れているモデルを使用できます。
- Windows 10 開発用コンピューターで **hyper-v** ソフトウェアが有効になっています。
- Ubuntu (16.4 または 18.4) を実行している仮想マシンを開発用コンピューターで実行するか、または Linux を実行する別のコンピューター (Ubuntu 16.4 または 18.4) を使用することができます。 Hyper-v を使用して Windows 上で VM を作成する方法の詳細については、 [「開始する前に](#before-you-start)」の章を参照してください。(https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).  



### <a name="before-you-start"></a>開始する前に

1. HoloLens をセットアップしてテストします。 HoloLens のセットアップをサポートする必要がある場合は、 [hololens セットアップに関する記事にアクセスして](https://docs.microsoft.com/hololens/hololens-setup)ください。
2. 新しい HoloLens アプリの開発を開始するときは、 **調整** と **センサーのチューニング** を実行することをお勧めします (ユーザーごとにこれらのタスクを実行するのに役立つ場合があります)。

調整の詳細については、 [「HoloLens の調整に関する記事へのリンク」を](../../../calibration.md#hololens-2)参照してください。

センサーチューニングの詳細については、 [HoloLens センサーチューニングに関する記事へのリンクを](../../../sensor-tuning.md)参照してください。

3. **Hyper-v** を使用して **Ubuntu 仮想マシン** をセットアップします。 このプロセスには、次のリソースが役立ちます。
    1.  まず、このリンクに従っ [て Ubuntu 16.04.4 LTS (Xenial Xerus) ISO をダウンロード](https://au.releases.ubuntu.com/16.04/)します。 64ビット **PC (AMD64) デスクトップイメージ** を選択します。
    2.  Windows 10 コンピューターで **hyper-v** が有効になっていることを確認します。 [Windows 10 で hyper-v をインストールして有効](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)にする方法については、こちらのリンクを参照してください。
    3.  Hyper-v を起動し、新しい Ubuntu VM を作成します。 [Hyper-v を使用して VM を作成する手順](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine)については、こちらのリンクを参照してください。 **[起動可能なイメージファイルからオペレーティングシステムをインストール** する] に要求された場合は、前の手順でダウンロードした **Ubuntu ISO** を選択します。

    > [!NOTE]
    > **Hyper-v の簡易作成** を使用することは推奨されません。  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a>第1章: Custom Vision モデルを取得する

このコースでは、イメージからキーボードとマウスを検出する既成の [Custom Vision モデル](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) にアクセスできます。 これを使用する場合は、 [第2章](#chapter-2---the-container-registry-service)に進みます。

ただし、独自の Custom Vision モデルを使用する場合は、次の手順に従うことができます。

1. **Custom Vision プロジェクト** で、[ **パフォーマンス** ] タブにアクセスします。

    > [!WARNING]
    > モデルをエクスポートするには、モデルで *コンパクト* ドメインを使用する必要があります。 モデルドメインは、プロジェクトの設定で変更できます。

    ![[パフォーマンス] タブ](images/AzureLabs-Lab313-01.png)

2. エクスポートする **イテレーション** を選択し、[ **エクスポート** ] をクリックします。 ブレードが表示されます。

    ![ブレードのエクスポート](images/AzureLabs-Lab313-02.png)

3. ブレードで [ **Docker File** ] をクリックします。

    ![docker の選択](images/AzureLabs-Lab313-03.png)

4. ドロップダウンメニューの [ **Linux** ] をクリックし、[ **ダウンロード** ] をクリックします。

    ![[ダウンロード] をクリック](images/AzureLabs-Lab313-04.png)

5. コンテンツを解凍します。 このコースは、このコースの後半で使用します。

## <a name="chapter-2---the-container-registry-service"></a>Chapter 2-Container Registry サービス

**Container Registry サービス** は、コンテナーをホストするために使用されるリポジトリです。

このコースで構築して使用する **IoT Hub サービス** は、 **Container Registry サービス** を参照して、エッジデバイスにデプロイするコンテナーを取得します。

1. 最初に、 [Azure Portal へのリンク](https://portal.azure.com/)に従って、資格情報でログインします。

2. 「 **リソースの作成** 」に進んで、 **Container Registry** を探します。

    ![コンテナーレジストリ](images/AzureLabs-Lab313-05.png)

3. **[作成]** をクリックします。

    ![](images/AzureLabs-Lab313-06.png)

4. サービスセットアップパラメーターを設定します。

    1. プロジェクトの名前を挿入します。この例では、 **IoTCRegistry** という名前です。

    2. リソースグループを選択するか、新しい **リソースグループ** を作成します。 リソースグループを使用すると、Azure 資産のコレクションの監視、アクセスの制御、プロビジョニング、管理を行うことができます。 1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのコースなど) を共通のリソースグループに保持することをお勧めします。

    3. サービスの場所を設定します。

    4. **有効** にするには、 **管理者ユーザー** を設定します。

    5. **SKU** を **Basic** に設定します。 

    ![](images/AzureLabs-Lab313-07.png)

5. [ **作成** ] をクリックし、サービスが作成されるまで待ちます。 

6. *Container Registry* が正常に作成されたことを知らせる通知が表示されたら、[ **リソースへのアクセス** ] をクリックして、サービスページにリダイレクトします。

    ![](images/AzureLabs-Lab313-08.png)

7. [サービスの *Container Registry* ] ページで、[ **アクセスキー** ] をクリックします。

8. 次のパラメーターのメモを控えておきます (メモ帳を使用できます)。
    1. **ログインサーバー**
    2. **ユーザー名**
    3. **パスワード**

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a>第3章-IoT Hub サービス

次に、 **IoT Hub サービス** の作成とセットアップを開始します。

1. まだサインインしていない場合は、 [Azure Portal](https://portal.azure.com)にログインします。

2.  ログインしたら、左上隅にある [ **リソースの作成** ] をクリックし、 **IoT Hub** を検索して、 **Enter キー** を押します。

 ![ストレージアカウントの検索](images/AzureLabs-Lab313-10.png)

3.  新しいページには、 **ストレージアカウント** サービスの説明が表示されます。 このプロンプトの左下にある [ **作成** ] ボタンをクリックして、このサービスのインスタンスを作成します。

    ![ストレージインスタンスの作成](images/AzureLabs-Lab313-11.png)

4.  [ **作成** ] をクリックすると、パネルが表示されます。

    1. リソースグループを選択するか、新しい **リソースグループ** を作成します。 リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。 1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのコースなど) を共通のリソースグループに保持することをお勧めします。

        > Azure リソースグループの詳細については、 [リソースグループの管理方法に関するリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)を参照してください。


    2. 適切な **場所** を選択します (このコースで作成するすべてのサービスで同じ場所を使用します)。

    3. このサービスインスタンスに必要な **名前** を挿入します。    

5.  ページの下部にある [次の **サイズとスケール** ] をクリックします。

    ![ストレージインスタンスの作成](images/AzureLabs-Lab313-12.png)

6.  このページで、 **価格とスケールレベル** を選択します (これが初めての IoT Hub サービスインスタンスの場合は、free レベルをご利用いただけます)。  

7.  [ **レビューと作成** ] をクリックします。

    ![ストレージインスタンスの作成](images/AzureLabs-Lab313-13.png)

8.  設定を確認し、[ **作成** ] をクリックします。

    ![ストレージインスタンスの作成](images/AzureLabs-Lab313-14.png)

9. *IoT Hub* サービスが正常に作成されたことを知らせる通知が表示されたら、[ **リソースへのアクセス** ] をクリックして、サービスページにリダイレクトします。

    ![ストレージインスタンスの作成](images/AzureLabs-Lab313-15.png)

10. [ *デバイスの自動管理* ] が表示されるまで左側のサイドパネルをスクロールし、 **IoT Edge** をクリックします。

    ![ストレージインスタンスの作成](images/AzureLabs-Lab313-16.png)

11. 右側に表示されるウィンドウで、[ **IoT Edge デバイスの追加** ] をクリックします。 ブレードが右側に表示されます。

12. ブレードで、新しいデバイスに **デバイス ID** (任意の名前) を入力します。 その後、 **[保存]** をクリックします。 **自動生成** が行われた場合、 *プライマリ**キーとセカンダリキー* は自動的に生成されます。

    ![ストレージインスタンスの作成](images/AzureLabs-Lab313-17.png)

13. 新しいデバイスが一覧表示される [ *IoT Edge デバイス* ] セクションに戻ります。 新しいデバイス (下の図の赤で囲まれています) をクリックします。 

    ![ストレージインスタンスの作成](images/AzureLabs-Lab313-18.png)

14. 表示される [ *デバイスの詳細* ] ページで、 **接続文字列** (主キー) のコピーを取得します。

    ![ストレージインスタンスの作成](images/AzureLabs-Lab313-19.png)

15. 左側のパネルに戻り、[ *共有アクセスポリシー* ] をクリックして開きます。 

16. 表示されるページで [ **iothubowner** ] をクリックすると、画面の右側にブレードが表示されます。 

17. **接続** 文字列 (主キー) のメモ (メモ帳) を書き留めておきます。後でデバイスに *接続文字列* を設定するときに使用します。

    ![ストレージインスタンスの作成](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a>章 4-開発環境の設定

*IoT Hub Edge* のモジュールを作成してデプロイするには、Windows 10 を実行する開発用コンピューターに次のコンポーネントがインストールされている必要があります。

1.  [Docker for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows)、ダウンロードできるアカウントを作成するように求められます。 

    [![docker for windows のダウンロード](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)

    > [!IMPORTANT]
    > Docker を実行するには、 *windows 10 PRO* 、 *Enterprise 14393* 、または *windows Server 2016 RTM* が必要です。 他のバージョンの Windows 10 を実行している場合は、 [Docker ツールボックス](https://docs.docker.com/toolbox/toolbox_install_windows/)を使用して docker をインストールできます。

2.  [Python 3.6](https://www.python.org/downloads/)。

    [![python 3.6 のダウンロード](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)

3.  [Visual Studio Code (VS Code とも呼ば](https://code.visualstudio.com/download)れます)。

    [![ダウンロード VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)

前述のソフトウェアをインストールしたら、コンピューターを再起動する必要があります。

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a>章 5-Ubuntu 環境のセットアップ

これで、 **UBUNTU OS を実行** しているデバイスのセットアップに進むことができます。 次の手順に従って、ボードにコンテナーをデプロイするために必要なソフトウェアをインストールします。

> [!IMPORTANT]
> 管理者ユーザーとして実行するには、ターミナルコマンドの前に常に **sudo** を使用する必要があります。 :
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  **Ubuntu ターミナル** を開き、次のコマンドを使用して **pip** をインストールします。

    > [!ヒント] キーボードショートカット ( **Ctrl + Alt + T** ) を使用して、 *ターミナル* を非常に簡単に開くことができます。

    ```bash
        sudo apt-get install python-pip
    ```

2.  この章では、デバイスのストレージを使用するためのアクセス許可を *ターミナル* で確認するメッセージが表示される場合があります。また、 **y/n** (yes または no) を入力するには「 **y」** と入力し、 **enter キーを押して同意** します。

3.  コマンドが完了したら、次のコマンドを使用して **curl** をインストールします。

    ```bash
        sudo apt install curl
    ```

4.  **Pip** および **curl** がインストールされたら、次のコマンドを使用して **IoT Edge ランタイム** をインストールします。これは、ボードにモジュールをデプロイおよび制御するために必要です。

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. この時点で、 **IoT Hub サービス** を作成するときにメモしておいた (メモ帳でメモしておいた) **デバイス接続文字列** を挿入するために、 *ランタイム構成ファイル* を開くように求められます ( [手順14の章 3](#chapter-3---the-iot-hub-service))。 ターミナルで次の行を実行して、そのファイルを開きます。

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. 次のように、 **構成の yaml** ファイルが表示され、編集できるようになります。

    > [!WARNING]
    > このファイルが開いたときに、多少紛らわしいことがあります。 このファイルを *ターミナル* 内で編集するテキストが表示されます。 

    1.  キーボードの方向キーを使用して下にスクロールします (少し下にスクロールして、次の行に移動する必要があります)。

        " **\<ADD DEVICE CONNECTION STRING HERE>** ".

    2. 前にメモした **デバイス接続文字列** を使用して、 **角かっこを含め** た代替行を指定します。

7. 接続文字列を設定した状態で、キーボードの **Ctrl + X** キーを押してファイルを保存します。 「 **Y** 」と入力すると、確認を求めるメッセージが表示されます。次に、 **enter** キーを押して確認します。 通常の *ターミナル* に戻ります。 

8. これらのコマンドがすべて正常に実行されると、 **IoT Edge ランタイム** がインストールされます。 初期化されると、デバイスの電源が入るたびにランタイムが自動的に起動し、バックグラウンドで実行され、モジュールが **IoT Hub サービス** からデプロイされるのを待ちます。

9.  次のコマンドラインを実行して、 *IoT Edge ランタイム* を初期化します。

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > Yaml ファイルまたは上記のセットアップに変更を加える場合は、 *ターミナル* 内で上記の再起動行をもう一度実行する必要があります。

10. 次のコマンドラインを実行して、 *IoT Edge ランタイム* の状態を確認します。 ランタイムは、状態が [ **アクティブ] (実行中)** の緑色のテキストで表示されます。

    ```bash
        sudo systemctl status iotedge
    ```

11. **Ctrl + C** キーを押して、[状態] ページを終了します。 次のコマンドを入力して、 *IoT Edge ランタイム* がコンテナーを正しくプルしていることを確認できます。

    ```bash
        sudo docker ps
    ```

12. 2つのコンテナーを含むリストが表示されます。 これらは、IoT Hub サービス (edgeAgent および edgeHub) によって自動的に作成される既定のモジュールです。 独自のモジュールを作成してデプロイすると、既定のモジュールの下にこの一覧に表示されます。

## <a name="chapter-6---install-the-extensions"></a>Chapter 6-拡張機能のインストール

> [!IMPORTANT]
> Windows 10 コンピューターでは、次のいくつかの章 (6-9) が実行されます。

1. **VS Code** を開きます。

2. VS Code の左側のバーにある [ **拡張機能** (四角)] ボタンをクリックして、[ **拡張機能] パネル** を開きます。

3. 次の図に示すように、次の拡張機能を検索してインストールします。

    1. Azure IoT Edge
    2. Azure IoT ツールキット
    3. Docker   

    ![コンテナーを作成する](images/AzureLabs-Lab313-24.png)

4. 拡張機能がインストールされたら、VS Code を閉じてから開き直します。

5. さらに VS Code 開いて、[ **View**  >  **統合ターミナル** の表示] に移動します。

6. 次に、 **Cookiecutter** をインストールします。 ターミナルで、次の bash コマンドを実行します。

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [!ヒント] このコマンドで問題が発生した場合は、次のようになります。 
    >1. VS Code、またはコンピューターを再起動します。
    >2. **VS Code ターミナル** を、python のインストールに使用している **もの (特** に、python 環境がコンピューターに既にインストールされている場合) に切り替える必要がある場合があります。 ターミナルを開いた状態で、ターミナルの右側にドロップダウンメニューが表示されます。
     ![コンテナーを作成する](images/AzureLabs-Lab313-24b.png) 
    >3. **Python** インストールパスが **環境変数** としてコンピューターに追加されていることを確認します。 Cookiecutter は同じ場所のパスの一部にする必要があります。 [環境変数の詳細につい](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx)ては、このリンクに従ってください。 

7. **Cookiecutter** のインストールが完了したら、コンピューターを再起動して、 **Cookiecutter** がシステムの環境内でコマンドとして認識されるようにします。

## <a name="chapter-7---create-your-container-solution"></a>第7章-コンテナーソリューションを作成する

この時点で、モジュールを使用してコンテナーを作成し、 *Container Registry* にプッシュする必要があります。 コンテナーをプッシュしたら、 *IoT Hub Edge* サービスを使用して、 *IoT Edge ランタイム* を実行しているデバイスにデプロイします。

1. VS Code で、[ **View**  >  **コマンドパレット** の表示] をクリックします。

2. パレットで、[ **Azure IoT Edge の新しい IoT Edge ソリューション** ] を検索して実行します。

3. ソリューションを作成する場所を参照します。 場所を受け入れるには、 **enter** キーを押します。

4. ソリューションに名前を付けます。 入力した名前を確認するには、 **enter** キーを押します。

5. これで、ソリューションのテンプレートフレームワークを選択するように求められます。 [ **Python モジュール** ] をクリックします。 この選択を確定するには、 **enter** キーを押します。

6. モジュールに名前を付けます。 **Enter** キーを押して、モジュールの名前を確認します。 後で使用するため、モジュール名のメモ (メモ帳を使用) を必ず実行してください。

7. 作成済みの *Docker イメージリポジトリ* アドレスがパレットに表示されます。 次のようになります。

    **localhost: 5000/-モジュールの名前-** 。 

8. **Localhost: 5000** を削除し、その場所で、 **Container Registry サービス** を作成するときにメモした *Container Registry* **Login サーバー** のアドレスを挿入します ( [手順8では、第2章を](#chapter-2---the-container-registry-service)参照してください)。 アドレスを確認するには、 **enter** キーを押します。

9. この時点で、Python モジュールのテンプレートを含むソリューションが作成され、その構造が画面の左側の [ **探索] タブ** (VS Code) に表示されます。 [ **探索] タブ** が開いていない場合は、左側のバーの一番上にあるボタンをクリックして開くことができます。

    ![コンテナーを作成する](images/AzureLabs-Lab313-25.png)

10. この章の最後の手順では、[ **探索] タブ** 内から、 **env ファイル** をクリックして開き、 *Container Registry* **ユーザー名** と **パスワード** を追加します。 このファイルは git によって無視されますが、コンテナーを構築すると、 **Container Registry サービス** にアクセスするための資格情報が設定されます。

    ![コンテナーを作成する](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a>章 8-コンテナーソリューションの編集

次のファイルを更新して、コンテナーソリューションを完成させます。

- *<span></span> .py* python スクリプト。
- *requirements.txt* 。
- *deployment.template.js* します。
- *Dockerfile. amd64*

次に、python スクリプトによって使用される *images* フォルダーを作成し、 *Custom Vision モデル* と照合するイメージを確認します。 最後に、モデルを読みやすくするために *labels.txt* ファイルを追加し、モデルとしてモデルの *pb* ファイルを追加します。

1. VS Code 開いた状態で、モジュールフォルダーに移動し、 **<span></span> .py** という名前のスクリプトを探します。 これをダブルクリックして開きます。

2. ファイルの内容を削除し、次のコードを挿入します。

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  **requirements.txt** という名前のファイルを開き、その内容を次の内容に置き換えます。

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  deployment.template.jsという名前のファイルを **で** 開き、次のガイドラインに従って内容を置き換えます。

    1. 独自の一意の JSON 構造があるため、(例をコピーするのではなく) 手作業で編集する必要があります。 これを簡単に行うには、次の図をガイドとして使用します。
    2. 異なる領域が表示されますが、 **変更すべきではない領域は黄色で強調表示され** ます。
    3. **削除する必要があるセクションは、赤で強調表示されています。**
    4. 正しい角かっこを削除し、コンマも削除するように注意してください。

        ![コンテナーを作成する](images/AzureLabs-Lab313-27.png)

    5. 完成した JSON は次の図のようになります (ただし、独自の違いがあります。 *ユーザー名/パスワード/モジュール名/モジュール参照* )。

        ![コンテナーを作成する](images/AzureLabs-Lab313-28.png)

5.  **Dockerfile. amd64** という名前のファイルを開き、その内容を次のように置き換えます。

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  [ **モジュール** ] の下にあるフォルダー (前の例で指定した名前が付いています。さらに下の例では、 *python モジュール* と呼ばれます) を右クリックし、[ **新しいフォルダー** ] をクリックします。 フォルダーに **画像** の名前を指定します。

7.  フォルダー内に、マウスまたはキーボードを含むいくつかのイメージを追加します。 これらの画像は、このモデルによって分析されるイメージになります。

    > [!WARNING]
    > 独自のモデルを使用している場合は、独自のモデルデータを反映するように変更する必要があります。

8.  次に、 [第1章](#chapter-1---retrieve-the-custom-vision-model)で、以前にダウンロードした (または独自の **Custom Vision Service** から作成した) モデルフォルダーから、 **labels.txt** と **モデルの pb** ファイルを取得する必要があります。 ファイルを作成したら、他のファイルと共にソリューション内に配置します。 最終的な結果は次の図のようになります。

    ![コンテナーを作成する](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a>第9章-ソリューションをコンテナーとしてパッケージ化する

1.  これで、ファイルをコンテナーとして "パッケージ化" し、 **Azure Container Registry** にプッシュできるようになりました。 VS Code で、 *統合ターミナル* ( **View**  >  **統合** ターミナルまたは **Ctrl** を表示) を開き、次の行を使用して + **\`** **Docker** にログインします (コマンドの値は、 **Azure Container Registry (ACR)** の資格情報に置き換えてください)。

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. **deployment.template.js** ファイルを右クリックし、[ **ビルド IoT Edge ソリューション** ] をクリックします。 このビルドプロセスは、(デバイスによっては) かなりの時間がかかります。そのため、待機する準備を整えてください。 ビルドプロセスが完了すると、[ **config** ] という名前の新しいフォルダー内 **にファイルのdeployment.js** が作成されます。

    ![デプロイの作成](images/AzureLabs-Lab313-30.png)

3. もう一度 **コマンドパレット** を開き、「 **Azure: Sign In** 」を検索します。 Azure アカウントの資格情報を使用して、画面の指示に従います。VS Code には、 *コピーして開く* オプションが用意されています。これにより、すぐに必要なデバイスコードがコピーされ、既定の web ブラウザーが開きます。 プロンプトが表示されたら、デバイスコードを貼り付けて、コンピューターを認証します。

    ![コピーして開く](images/AzureLabs-Lab313-31.png)

4. サインインすると、[ *探索* ] パネルの下部に [ **Azure IoT Hub デバイス** ] という新しいセクションが表示されます。 展開するには、このセクションをクリックします。

    ![エッジデバイス](images/AzureLabs-Lab313-32.png)

5. デバイスがここにない場合は、[ *Azure IoT Hub デバイス* ] を右クリックし、[ **IoT Hub 接続文字列の設定** ] をクリックする必要があります。 **コマンドパレット** (VS Code の上部) で、 *接続文字列* を入力するように求められます。 これは、 [章 3](#chapter-3---the-iot-hub-service)の最後にメモした *接続文字列* です。 で文字列を **コピーしたら、enter キーを** 押します。    

6. デバイスが読み込まれ、表示されます。 デバイス名を右クリックし、[ **単一デバイスの展開の作成** ] をクリックします。

    ![デプロイの作成](images/AzureLabs-Lab313-33b.png)

7. *ファイルエクスプローラー* のプロンプトが表示されます。ここで、 **config** フォルダーに移動し、ファイル **のdeployment.js** を選択します。 そのファイルを選択した状態で、[ **エッジ配置マニフェストの選択** ] ボタンをクリックします。

    ![デプロイの作成](images/AzureLabs-Lab313-34.png)

8. この時点で、 **Azure Container Registry** からコンテナーをモジュールとしてデプロイし、実際にデバイスにデプロイするためのマニフェストを **IoT Hub サービス** に提供しました。

9. デバイスから IoT Hub に送信されたメッセージを表示するには、[ **エクスプローラー** ] パネルの [ **Azure IoT Hub デバイス** ] セクションでデバイス名をもう一度右クリックし、[ **監視 D2C メッセージの開始** ] をクリックします。 デバイスから送信されたメッセージが VS ターミナルに表示されます。 しばらく時間がかかることがあります。 デバッグについては、次の章を参照してください。配置が成功したかどうかを確認してください。

このモジュールは、各イテレーションで **images** フォルダー内のイメージを反復処理し、それらを分析します。 これは明らかに、基本的な機械学習モデルを使用して IoT Edge デバイス環境で動作させる方法のデモにすぎません。 

この例の機能を拡張するには、いくつかの方法を実行します。 1つの方法として、コンテナーにいくつかのコードを含め、デバイスに接続されている web カメラから写真をキャプチャして、images フォルダーに保存する方法があります。 

別の方法として、IoT デバイスからコンテナーにイメージをコピーすることもできます。 これを行う実際の方法として、IoT デバイスターミナルで次のコマンドを実行します (たとえば、プロセスを自動化する場合は、小規模なアプリでジョブを実行できます)。 このコマンドは、ファイルが格納されているフォルダーの場所から手動で実行することでテストできます。

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a>第10章-IoT Edge ランタイムのデバッグ

次に示すのは、 **Ubuntu デバイス** から *IoT Edge ランタイム* のメッセージングアクティビティを監視およびデバッグするのに役立つコマンドラインとヒントの一覧です。 

- 次のコマンドラインを実行して、 *IoT Edge ランタイム* の状態を確認します。

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > ステータスの表示を完了するには、 **Ctrl + C** キーを押してください。

- 現在展開されているコンテナーを一覧表示します。 *IoT Hub サービス* がコンテナーを正常にデプロイした場合は、次のコマンドラインを実行すると表示されます。

    ```bash
        sudo iotedge list
    ```

    または

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > 上記は、モジュールが正常にデプロイされているかどうかを確認するための優れた方法であり、一覧に表示されます。それ以外の場合は、 *edgeHub* と *edgeAgent***のみ** が表示されます。

- コンテナーのコードログを表示するには、次のコマンドラインを実行します。

    ```bash
        journalctl -u iotedge
    ```

**IoT Edge ランタイムを管理するための便利なコマンド:**

-  ホスト内のすべてのコンテナーを削除するには、次のようにします。

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  *IoT Edge ランタイム* を停止するには:

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a>第11章-Create Table Service 

Azure Portal に戻ります。ここでは、ストレージリソースを作成して、Azure Tables サービスを作成します。

1. まだサインインしていない場合は、 [Azure Portal](https://portal.azure.com)にログインします。

2. ログインしたら、左上隅にある [ **リソースの作成** ] をクリックし、[ **ストレージアカウント** ] を検索して、 **enter** キーを押して検索を開始します。

3. 表示されたら、一覧から [ **ストレージアカウント-blob、file、table、queue** ] をクリックします。

    ![ストレージアカウントの検索](images/AzureLabs-Lab313-35.png)

4. 新しいページには、 **ストレージアカウント** サービスの説明が表示されます。 このプロンプトの左下にある [ **作成** ] ボタンをクリックして、このサービスのインスタンスを作成します。

    ![ストレージインスタンスの作成](images/AzureLabs-Lab313-36.png)

5. [ **作成** ] をクリックすると、パネルが表示されます。

    1. このサービスインスタンスに必要な **名前** を挿入します ( *すべて小文字にする必要があり* ます)。

    2. [ **デプロイモデル** ] で、[ **リソースマネージャー** ] をクリックします。

    3. [ **アカウントの種類** ] で、ドロップダウンメニューを使用して、[ **ストレージ (汎用 v1)** ] をクリックします。

    4. 適切な **場所** をクリックします。
    
    5. [ **レプリケーション** ] ドロップダウンメニューで、[ **読み取りアクセス-geo 冗長ストレージ (RA-GRS)** ] をクリックします。

    6. [ **パフォーマンス** ] で [ **標準** ] をクリックします。

    7. [ **安全な転送が必要** ] セクションで、[ **無効** ] をクリックします。

    8. [ **サブスクリプション** ] ドロップダウンメニューから、適切なサブスクリプションをクリックします。

    9. リソースグループを選択するか、新しい **リソースグループ** を作成します。 リソースグループを使用すると、Azure 資産のコレクションの監視、アクセスの制御、プロビジョニング、管理を行うことができます。 1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのコースなど) を共通のリソースグループに保持することをお勧めします。

        > Azure リソースグループの詳細については、 [リソースグループの管理方法に関するリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)を参照してください。

    10. このオプションが選択されている場合は、[ **仮想ネットワーク** ] を [ **無効** ] のままにします。

    11. **Create** をクリックしてください。

        ![ストレージの詳細の入力](images/AzureLabs-Lab313-37.png)

6. [ **作成** ] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。

7. サービスインスタンスが作成されると、ポータルに通知が表示されます。 通知をクリックして、新しいサービスインスタンスを探索します。

    ![新しいストレージ通知](images/AzureLabs-Lab313-38.png)

8. 通知の [ **リソースに移動** ] ボタンをクリックすると、新しいストレージサービスインスタンスの概要ページが表示されます。

    ![リソースにアクセス](images/AzureLabs-Lab313-39.png)

9. [概要] ページで、右側にある [ **テーブル** ] をクリックします。
    
    ![テーブル](images/AzureLabs-Lab313-40.png)

10. 右側のパネルが変更され、 **テーブルサービス** 情報が表示されます。新しいテーブルを追加する必要があります。 これを行うには、左上隅にある [ **+ テーブル** ] ボタンをクリックします。

    ![テーブルを開く](images/AzureLabs-Lab313-41.png)

11. 新しいページが表示されます。ここには、 **テーブル名** を入力する必要があります。 これは、後の章で (Function App を作成し、Power BI)、アプリケーション内のデータを参照するために使用する名前です。 名前として **Iotmessages** を挿入し (このドキュメントで後ほど使用する場合はそのままにしておきます)、[ **OK]** をクリックします。 

12. 新しいテーブルが作成されると、 **テーブルサービス** のページ (下部) に表示されるようになります。

    ![新しいテーブルが作成されました](images/AzureLabs-Lab313-42.png)  

13. 次に、[ **アクセスキー** ] をクリックし、 **ストレージアカウント名** と **キー** のコピーを作成します (メモ帳を使用)。 **Azure Function App** を作成するときに、このコースの後半でこれらの値を使用します。

    ![新しいテーブルが作成されました](images/AzureLabs-Lab313-43.png) 

14. 左側のパネルを再び使用して、[ *Table Service* ] \ (テーブルサービス \) セクションまでスクロールし、[ **tables** (または新しいポータルでの **テーブルの参照** )] をクリックして、テーブルの **URL** (メモ帳を使用) のコピーを作成します。 この値は、テーブルを **Power BI** アプリケーションにリンクするときに、このコースの後半で使用します。

    ![新しいテーブルが作成されました](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a>第12章-Azure テーブルの完成

**Table Service** ストレージアカウントのセットアップが完了したので、それにデータを追加します。これは、情報の格納と取得に使用されます。 テーブルの編集は、 **Visual Studio** を使用して行うことができます。

1. (Visual Studio Code で **はなく** ) **Visual Studio** を開きます。

2. メニューの [Cloud Explorer の **表示** ] をクリックし  >  **Cloud Explorer** ます。

    ![cloud explorer を開く](images/AzureLabs-Lab313-45.png)

3. **Cloud Explorer** がドッキングされたアイテムとして開きます (読み込みに時間がかかる場合があります)。

    > [!WARNING] 
    > *ストレージアカウント* の作成に使用したサブスクリプションが表示されない場合は、次のことを確認してください。 
    > - Azure Portal で使用したものと同じアカウントにログインします。
    > - [アカウント管理] ページからサブスクリプションを選択しました (アカウントの設定からフィルターを適用する必要がある場合があります)。  
    >
    >   ![サブスクリプションの検索](images/AzureLabs-Lab313-46.png)

4. Azure cloud Services が表示されます。 **ストレージアカウント** を検索し、左側の矢印をクリックしてアカウントを展開します。

    ![ストレージアカウントを開く](images/AzureLabs-Lab313-47.png)

5. 展開されると、新しく作成された **ストレージアカウント** を使用できるようになります。 ストレージの左側にある矢印をクリックし、展開された後、[ **テーブル** ] を見つけて、その横にある矢印をクリックし、最後の章で作成した **テーブル** を表示します。 **テーブル** をダブルクリックします。

6. テーブルが Visual Studio ウィンドウの中央に開きます。 [テーブル] アイコンをクリックし **+** ます。

    ![新しいテーブルの追加](images/AzureLabs-Lab313-48.png)

7. *エンティティの追加* を求めるウィンドウが表示されます。 エンティティは1つだけ作成しますが、3つのプロパティがあります。 *Partitionkey* と *RowKey* は既に提供されています。これは、テーブルがデータを検索するために使用されるためです。 

    ![パーティションキーと行キー](images/AzureLabs-Lab313-49.png)

8. 次の値を更新します。

    - 名前: **Partitionkey** 、Value: **PK_IoTMessages** 

    - 名前: **RowKey** 、値: **RK_1_IoTMessages** 

9. 次に、[ *エンティティの追加* ] ウィンドウの左下にある [ **プロパティの追加** ] をクリックし、次のプロパティを追加します。

    - **Messagecontent***文字列* として使用する場合は、値を空のままにします。

10. テーブルは、次の図に示すものと一致している必要があります。

    ![正しい値の追加](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > このエンティティの行キーの番号が1である理由は、さらに多くのメッセージを追加することが必要になる可能性があるためです。このコースをさらに試してみることをお勧めします。

11. 完了したら [ **OK]** をクリックします。 これで、テーブルを使用する準備ができました。

## <a name="chapter-13---create-an-azure-function-app"></a>第13章-Azure Function App の作成 

ここでは、 *Azure Function App* を作成します。これは、前の章で作成した **Table** service に *IoT Edge* デバイスメッセージを格納するために、 *IoT Hub サービス* によって呼び出されます。

まず、必要なライブラリを Azure 関数で読み込むことができるファイルを作成する必要があります。

1.  **メモ帳** を開きます ( *Windows キー* を押して、 *メモ帳* を入力します)。

    ![メモ帳を開く](images/AzureLabs-Lab313-51.png)

2.  メモ帳を開いた状態で、次の JSON 構造を挿入します。 これが完了したら、 **project.js** としてデスクトップに保存します。 このファイルは、関数が使用するライブラリを定義します。 NuGet を使用している場合は、見慣れた外観になります。
    
    > [!WARNING]
    > 名前が正しいことが重要です。ファイル拡張子 **.txt が付いていないことを** 確認します。 参照については、以下を参照してください。
    >
    > ![JSON 保存](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  [Azure Portal](https://portal.azure.com) にログインします。

4.  ログインしたら、左上隅にある [ **リソースの作成** ] をクリックし、 **Function App** を検索して、 **enter** キーを押して検索します。 結果の [ *Function App* ] をクリックして、新しいパネルを開きます。

    ![function app の検索](images/AzureLabs-Lab313-53.png)

5.  新しいパネルには、 **Function App** サービスの説明が表示されます。 このパネルの左下にある [ **作成** ] ボタンをクリックして、このサービスとの関連付けを作成します。

    ![function app インスタンス](images/AzureLabs-Lab313-54.png)

6.  [ **作成** ] をクリックしたら、次のように入力します。

    1. [ **アプリ名** ] に、このサービスインスタンスに必要な名前を挿入します。

    2. **サブスクリプション** を選択します。

    3. 適切な価格レベルを選択してください。 **Function App サービス** を初めて作成する場合は、free レベルをご利用いただけます。

    4. リソースグループを選択するか、新しい **リソースグループ** を作成します。 リソースグループを使用すると、Azure 資産のコレクションの監視、アクセスの制御、プロビジョニング、管理を行うことができます。 1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのコースなど) を共通のリソースグループに保持することをお勧めします。

        > Azure リソースグループの詳細については、 [リソースグループの管理方法に関するリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)を参照してください。

    5. **OS** の場合は、[Windows] をクリックします。これは目的のプラットフォームです。

    6. **ホスティングプラン** を選択します (このチュートリアルでは、 **従量課金プラン** を使用しています。

    7. **場所** を選択します (前の手順で作成したストレージと同じ場所を選択します)。

    8. [ **ストレージ** ] セクションでは、 **前の手順で作成したストレージサービスを選択する必要があり** ます。

    9. このアプリで *Application Insights* は必要ありませ **ん。そのままにして** おいてもかまいません。

    10. **Create** をクリックしてください。

        ![新しいインスタンスの作成](images/AzureLabs-Lab313-55.png)

7.  [ **作成** ] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。

8.  サービスインスタンスが作成されると、ポータルに通知が表示されます。

    ![新しい通知](images/AzureLabs-Lab313-56.png)

9.  デプロイが正常に完了したら (完了した)、通知をクリックします。

10. 通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。 

    ![リソースにアクセス](images/AzureLabs-Lab313-57.png)

11. 新しいパネルの左側で、[関数] の横にある **+** (プラス記号) *Functions* アイコンをクリックして、新しい関数を作成します。

    ![新しい関数の追加](images/AzureLabs-Lab313-58.png)

12. 中央のパネル内に [ **関数** の作成] ウィンドウが表示されます。 さらに下にスクロールし、[ **カスタム関数** ] をクリックします。

    ![カスタム関数](images/AzureLabs-Lab313-59.png)

13. 次のページを下にスクロールして、 **IoT Hub (イベントハブ)** を見つけ、クリックします。

    ![カスタム関数](images/AzureLabs-Lab313-60.png)

14. [ **IoT Hub (イベントハブ)** ] ブレードで、 **言語** を **C#** に設定し、[ **新規** ] をクリックします。

    ![カスタム関数](images/AzureLabs-Lab313-61.png)

15. 表示されるウィンドウで、 **IoT Hub** が選択されていることを確認し、 *IoT Hub* フィールドの名前が、前に作成した *IoT Hub サービス* の名前と一致することを確認します ( [手順8の第3章を](#chapter-3---the-iot-hub-service)参照)。 次に、[ **選択** ] ボタンをクリックします。

    ![カスタム関数](images/AzureLabs-Lab313-62.png)

16. [ **IoT Hub (イベントハブ)** ] ブレードに戻り、[ **作成** ] をクリックします。

    ![カスタム関数](images/AzureLabs-Lab313-63.png)

17. 関数エディターにリダイレクトされます。

    ![カスタム関数](images/AzureLabs-Lab313-64.png)

18. その中のすべてのコードを削除し、次のコードに置き換えます。

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. 次の変数を変更して、 **ストレージアカウント** に含まれる適切な値 ( [手順 11. および 13. の](#chapter-11---create-table-service)**テーブル** と **ストレージ** の値) に対応するようにします。

    - **tableName** 。 **ストレージアカウント** 内にある **テーブル** の名前を使用します。
    - **tableurl** 。 **ストレージアカウント** 内にある **テーブル** の url を使用します。
    - **Storageaccountname** 。 **ストレージアカウント** 名に対応する値の名前を指定します。
    - **storageAccountKey** には、前に作成したストレージサービスで取得したキーを使用します。

    ![カスタム関数](images/AzureLabs-Lab313-65.png)

20. コードを配置したら、[ **保存** ] をクリックします。

21. 次に、 **\<** ページの右側にある (矢印) アイコンをクリックします。

    ![カスタム関数](images/AzureLabs-Lab313-66.png)

22. パネルが右側からスライドします。 そのパネルで [ **アップロード** ] をクリックすると、 *ファイルブラウザー* が表示されます。

23. に移動して、 **メモ帳** で作成したファイルの **project.js** をクリックし、[ **開く** ] ボタンをクリックします。 このファイルは、関数が使用するライブラリを定義します。

    ![カスタム関数](images/AzureLabs-Lab313-67.png)

24. ファイルがアップロードされると、右側のパネルに表示されます。 このボタンをクリックすると、 **関数** エディター内で開かれます。 次の画像と **まったく** 同じ外観にする必要があります。

    ![カスタム関数](images/AzureLabs-Lab313-68.png)

25. この時点で、 *テーブル* にメッセージを格納する関数の機能をテストすることをお勧めします。 ウィンドウの右上にある [ **テスト** ] をクリックします。

    ![カスタム関数](images/AzureLabs-Lab313-69.png)

26. 上の図に示されているように、 **要求本文** にメッセージを挿入し、[ **実行** ] をクリックします。 

27. 関数が実行され、結果の状態が表示されます ([ *出力* ] ウィンドウの上に緑の **状態 202** が表示されます。これは成功した呼び出しであることを意味します)。

    ![出力結果](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a>第14章-アクティブなメッセージの表示

(Visual Studio Code では **なく** ) Visual Studio を開いた場合、テストメッセージの結果は *messagecontent* 文字列領域に格納されるため、視覚化することができます。

![カスタム関数](images/AzureLabs-Lab313-71.png)

Table Service と Function App が配置されていると、Ubuntu デバイスのメッセージが *Iotmessages* テーブルに表示されます。 まだ実行されていない場合は、デバイスをもう一度起動すると、Visual Studio *Cloud Explorer* を使用して、デバイスとモジュールの結果メッセージをテーブル内に表示できるようになります。

![データの視覚化](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a>第15章-Power BI セットアップ

IOT デバイスからデータを視覚化するには **Power BI** (デスクトップバージョン) をセットアップし、先ほど作成した *テーブル* サービスからデータを収集します。 Power BI の *HoloLens* バージョンでは、そのデータを使用して結果が視覚化されます。

1.  Windows 10 で Microsoft Store を開き、 **Power BI Desktop** を検索します。

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  アプリケーションをダウンロードします。 ダウンロードが完了したら、それを開きます。

3.  **Microsoft 365 アカウント** を使用して *Power BI* にログインします。 サインアップするには、ブラウザーにリダイレクトすることができます。 サインアップしたら、Power BI アプリに戻り、もう一度サインインします。

4.  [ **データの取得** ] をクリックし、[ **詳細** ] をクリックします。

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  [ **Azure** ]、[ **azure Table Storage** ] の順にクリックし、[ **接続** ] をクリックします。

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  テーブルサービスの作成時に、先ほど収集した **テーブル URL** ( [第11章の手順 13](#chapter-11---create-table-service)) を挿入するように求められます。 URL を挿入した後、テーブル "サブフォルダー" (このコースでは IoTMessages) を参照するパスの部分を削除します。 最終的な結果は、次の図のように表示されます。 [ **OK]** をクリックします。

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  Table Storage の作成時に、メモした **ストレージキー** ( [第11章の手順 11](#chapter-11---create-table-service)) を挿入するように求められます。 [ **接続** ] をクリックします。

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. [ **ナビゲーター] パネル** が表示されたら、テーブルの横にあるボックスをオンにして、[ **読み込み** ] をクリックします。

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. 現在、テーブルは Power BI に読み込まれていますが、その値を表示するクエリが必要です。 これを行うには、画面の右側にある [ **フィールド] パネル** にあるテーブル名を右クリックします。 次に、[ **クエリの編集** ] をクリックします。

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. 新しいウィンドウとして **Power Query エディター**  が開き、テーブルが表示されます。 テーブルの [ *コンテンツ* ] 列の " **レコード** " をクリックして、保存されているコンテンツを視覚化します。

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. ウィンドウの左上にある [ **テーブルに** 移動] をクリックします。 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. [ **閉じる & 適用** ] をクリックします。

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. クエリの読み込みが完了したら、[ **フィールド] パネル** の画面の右側で、パラメーターの **名前** と **値** に対応するボックスをオンにして、 **messagecontent** 列の内容を視覚化します。

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. ウィンドウの左上にある **青いディスクアイコン** をクリックして、選択したフォルダーに作業内容を保存します。

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. [発行] ボタンをクリックして、ワークスペースにテーブルをアップロードできるようになりました。 メッセージが表示されたら、[ **マイワークスペース** ] をクリックし、[ *選択* ] をクリックします 送信の成功した結果が表示されるまで待ちます。

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> 次の章は HoloLens 固有です。 Power BI は現在イマーシブアプリケーションとして使用できませんが、デスクトップアプリを使用して、Windows Mixed Reality ポータル (崖家) でデスクトップバージョンを実行することができます。

## <a name="chapter-16---display-power-bi-data-on-hololens"></a>Chapter 16-HoloLens で Power BI データを表示する

1. HoloLens で、アプリケーションの一覧のアイコンをタップして、 **Microsoft Store** にログインします。

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. **Power BI** アプリケーションを検索してダウンロードします。

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. アプリケーションの一覧から **Power BI** を開始します。 

4. **Power BI** によって、 **Microsoft 365 アカウント** へのログインが要求される場合があります。

5. アプリの内部では、次の図に示すように、既定でワークスペースが表示されます。 この問題が発生しない場合は、ウィンドウの左側にあるワークスペースアイコンをクリックします。

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a>IoT Hub アプリケーションが完成しました

これで、シミュレートされた仮想マシンのエッジデバイスを使用して、IoT Hub サービスを正常に作成できました。 デバイスは、azure Function App によって容易に machine learning モデルの結果を Azure Table サービスに伝達できます。このサービスは、Power BI に読み込まれ、Microsoft HoloLens 内で視覚化されます。
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a>ボーナス演習

### <a name="exercise-1"></a>演習1

テーブルに格納されているメッセージング構造を展開し、グラフとして表示します。 後で表示するために、さらに多くのデータを収集し、同じテーブルに格納することができます。

### <a name="exercise-2"></a>演習2

IoT ボードにデプロイする追加の "カメラキャプチャ" モジュールを作成して、分析対象のカメラを通じてイメージをキャプチャできるようにします。
