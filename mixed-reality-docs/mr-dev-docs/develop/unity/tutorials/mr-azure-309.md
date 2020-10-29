---
title: MR と Azure 309-Application insights
description: このコースでは、Azure アプリケーション Insights サービスを使用して、mixed reality アプリケーション内でユーザーの動作に関する分析を収集する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, チュートリアル, api, application insights, hololens, イマーシブ, vr
ms.openlocfilehash: 51717ba8a2d0c46e18c66575497994d9d792184c
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91687706"
---
# <a name="mr-and-azure-309-application-insights"></a>MR と Azure 309:Application Insights

<br>

>[!NOTE]
>Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。  そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。  これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは " **_ありません_** "。  これらは、サポートされているデバイス上で継続して動作するように、保守されます。 今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。  この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。

<br>

![最終製品-開始](images/AzureLabs-Lab309-00.png)

このコースでは、Azure アプリケーション Insights API を使用してユーザーの行動に関する分析を収集することにより、Application Insights 機能を混合の現実アプリケーションに追加する方法について説明します。

Application Insights は Microsoft のサービスであり、開発者はアプリケーションから分析を収集し、使いやすいポータルから管理できます。 分析には、パフォーマンスから収集するカスタム情報まで、あらゆるものを選択できます。 詳細については、 [Application Insights のページ](https://azure.microsoft.com/services/application-insights/)を参照してください。

このコースを完了すると、現実のイマーシブヘッドセットアプリケーションが完成し、次のことができるようになります。

1.  シーンを見つめて移動することをユーザーに許可します。
2.  シーン内オブジェクトとの間での使用を通じて、 *Application Insights サービス* への分析の送信をトリガーします。
3.  また、アプリはサービスに対してを呼び出し、過去24時間以内にユーザーによって最も頻繁に近づいたオブジェクトに関する情報を取得します。 そのオブジェクトの色が緑色に変わります。

このコースでは、Application Insights サービスから Unity ベースのサンプルアプリケーションに結果を取得する方法について説明します。 これらの概念は、構築しているカスタムアプリケーションに適用する必要があります。

## <a name="device-support"></a>デバイス サポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="../../../hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> MR と Azure 309:Application Insights</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> このコースでは主に Windows Mixed Reality イマーシブ (VR) ヘッドセットに焦点を当てていますが、このコースで学習した内容を Microsoft HoloLens に適用することもできます。 このコースに従うと、HoloLens をサポートするために必要となる可能性のある変更に関する注意事項が表示されます。 HoloLens を使用する場合、音声キャプチャ中にエコーが発生することがあります。

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
- 内蔵マイク付きヘッドホンのセット (ヘッドセットにマイクとスピーカーが組み込まれていない場合)
- Azure セットアップとデータ取得のためのインターネットアクセス Application Insights

## <a name="before-you-start"></a>開始する前に

このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。

> [!WARNING] 
> *Application Insights* するデータには時間がかかるため、しばらくお待ちください。 サービスがデータを受信したかどうかを確認する場合は、 [14 章](#chapter-14---the-application-insights-service-portal)を参照してください。この章では、ポータル内を移動する方法を説明しています。

## <a name="chapter-1---the-azure-portal"></a>章 1-Azure Portal

*Application Insights* を使用するには、Azure portal で *Application Insights サービス* を作成および構成する必要があります。

1.  [Azure Portal](https://portal.azure.com) にログインします。

    > [!NOTE]
    > まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。 このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。

2.  ログインしたら、左上隅にある [ **新規** ] をクリックし、 *Application Insights* を検索して、 **Enter キー** を押します。

    > [!NOTE]
    > 新しいポータルで、 **New** という単語が **リソースの作成** に置き換えられました。

    ![Azure portal](images/AzureLabs-Lab309-01.png)

3.  右側の新しいページには、 *Azure アプリケーション Insights* サービスの説明が表示されます。 このページの左下にある [ **作成** ] ボタンを選択して、このサービスとの関連付けを作成します。

    ![Azure portal](images/AzureLabs-Lab309-02.png)

4.  [ **作成** :

    1.  このサービスインスタンスに必要な **名前** を挿入します。

    2.  **アプリケーションの種類** として [ **全般** ] を選択します。

    3.  適切な **サブスクリプション** を選択します。

    4.  リソースグループを選択するか、新しい **リソースグループ** を作成します。 リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。 1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのコースなど) を共通のリソースグループに保持することをお勧めします。

        > Azure リソースグループの詳細については、 [リソースグループ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)に関する記事をご覧ください。

    5.  **[場所]** を選択します。

    6.  また、このサービスに適用されている使用条件を理解していることを確認する必要があります。

    7.  **［作成］** を選択します

        ![Azure portal](images/AzureLabs-Lab309-03.png)

5.  [ **作成** ] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。

6.  サービスインスタンスが作成されると、ポータルに通知が表示されます。

    ![Azure portal](images/AzureLabs-Lab309-04.png)

7.  通知をクリックして、新しいサービスインスタンスを探索します。

    ![Azure portal](images/AzureLabs-Lab309-05.png)

8.  通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。 新しい *Application Insights サービス* インスタンスが表示されます。

    ![Azure portal](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  この web ページを開いたまま、簡単にアクセスできるようにします。収集されたデータを確認するために頻繁に使用します。

    > [!IMPORTANT]
    > Application Insights を実装するには、 **インストルメンテーションキー** 、 **アプリケーション ID** 、 **API キー** という3つの固有の値を使用する必要があります。 以下では、これらの値をサービスから取得する方法について説明します。 これらの値は、コードですぐに使用されるため、空の *メモ帳* ページでメモしておいてください。

9.  **インストルメンテーションキー** を検索するには、サービス関数の一覧を下にスクロールし、[ **プロパティ** ] をクリックする必要があります。表示されるタブに **サービスキー** が表示されます。

    ![Azure portal](images/AzureLabs-Lab309-07.png)

10. 以下の **プロパティ** を使用すると、クリックする必要がある **API アクセス** がわかります。 右側のパネルに、アプリの **アプリケーション ID** が表示されます。

    ![Azure portal](images/AzureLabs-Lab309-08.png)

11. [ **アプリケーション ID** ] パネルを開いたまま、[ **Api キーの作成** ] をクリックすると、[ *api キーの作成* ] パネルが開きます。

    ![Azure portal](images/AzureLabs-Lab309-09.png)

12. ここで、[ *API キーの作成* ] パネルを開き、説明を入力して、 **3 つのボックスを目盛り** します。

13. [ **キーの生成** ] をクリックします。 **API キー** が作成されて表示されます。 

    ![Azure portal](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > これは、 **サービスキー** が表示される唯一の時間であるため、ここでコピーを作成してください。

## <a name="chapter-2---set-up-the-unity-project"></a>Chapter 2-Unity プロジェクトの設定

次に示すのは、mixed reality で開発するための一般的な設定です。そのため、他のプロジェクトに適したテンプレートです。

1.  *Unity* を開き、[ **新規** ] をクリックします。

    ![Unity プロジェクトを設定する](images/AzureLabs-Lab309-11.png)

2.  ここで、Unity プロジェクト名を指定し、「 **MR \_ Azure \_ Application \_ Insights** 」と入力する必要があります。 *テンプレート* が **3d** に設定されていることを確認します。 場所を適切な *場所* に設定します (ルートディレクトリの方が適していることに注意してください)。 次に、[ **プロジェクトの作成** ] をクリックします。

    ![Unity プロジェクトを設定する](images/AzureLabs-Lab309-12.png)

3.  Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。 [ **\> 設定の編集** ] に移動し、新しいウィンドウで [ **外部ツール** ] に移動します。 **外部スクリプトエディター** を **Visual Studio 2017** に変更します。 [ **基本設定** ] ウィンドウを閉じます。

    ![Unity プロジェクトを設定する](images/AzureLabs-Lab309-13.png)

4.  次に、[ **ファイル \>** ] [ビルドの設定] の順に移動し、[ **プラットフォームの切り替え** ] ボタンをクリックして、プラットフォームを **ユニバーサル Windows プラットフォーム** に切り替えます。

    ![Unity プロジェクトを設定する](images/AzureLabs-Lab309-14.png)

5.  ファイルの **\> ビルド設定** にアクセスして、次のことを確認してください。

    1.  **ターゲットデバイス** が **任意のデバイス** に設定されています

        > Microsoft HoloLens の場合は、 **ターゲットデバイス** を *HoloLens* に設定します。

    2.  **ビルドの種類** が **D3D** に設定されています

    3.  **SDK** は最新の **インストール** に設定されています

    4.  **ビルドと実行** は **ローカルコンピューター** に設定されています

    5.  シーンを保存し、ビルドに追加します。

        1.  これを行うには、[開いている **シーンの追加** ] を選択します。 保存ウィンドウが表示されます。

            ![Unity プロジェクトを設定する](images/AzureLabs-Lab309-15.png)

        2. このための新しいフォルダーを作成し、その後のシーンで、[ **新しいフォルダー** ] ボタンをクリックして新しいフォルダーを作成し、その名前を「 **シーン** 」にします。

            ![Unity プロジェクトを設定する](images/AzureLabs-Lab309-16.png)

        3. 新しく作成した [ **シーン** ] フォルダーを開き、[ *ファイル名:* テキスト] フィールドに「 **ApplicationInsightsScene** 」と入力し、[ **保存** ] をクリックします。

            ![Unity プロジェクトを設定する](images/AzureLabs-Lab309-17.png)

6.  それ以外の設定は、[ **ビルド設定** ] の [既定] のままにしておきます。

7.  [ **ビルドの設定** ] ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 **インスペクター** が配置されている領域の関連パネルが開きます。

    ![Unity プロジェクトを設定する](images/AzureLabs-Lab309-18.png)

8. このパネルでは、いくつかの設定を確認する必要があります。

    1.  [ **その他の設定** ] タブで、次のようにします。

        1.  **Scripting** **Runtime のバージョン** は **実験的 (.net 4.6 と同等)** である必要があります。これにより、エディターを再起動する必要が生じます。

        2.  **バックエンド** は **.net** である必要があります

        3.  **API 互換性レベル** は **.net 4.6** である必要があります

        ![Unity プロジェクトを設定する](images/AzureLabs-Lab309-19.png)

    2.  [ **発行の設定** ] タブの [ **機能** ] で、次の項目を確認します。

        - **InternetClient**     

            ![Unity プロジェクトを設定する](images/AzureLabs-Lab309-20.png)

    3.  パネルの下にある [ **XR settings** ( **発行設定** ] の下にあります) で、[ **Virtual Reality がサポートされている** ] をオンにして、 **Windows Mixed reality SDK** が追加されていることを確認します。

        ![Unity プロジェクトを設定する](images/AzureLabs-Lab309-21.png)

9.  **ビルド設定** に戻ると、 **Unity C# プロジェクト** はグレーで表示されなくなりました。このの横にあるチェックボックスをオンにします。

10.  [ビルド設定] ウィンドウを閉じます。

11.  シーンとプロジェクトを保存します ( **ファイル**  >  **保存シーン/ファイル**  >  **保存プロジェクト** )。


## <a name="chapter-3---import-the-unity-package"></a>章 3-Unity パッケージをインポートする

> [!IMPORTANT]
> このコースの *構成要素をスキップし、コード* に直接移動する場合は、この [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage)を無料でダウンロードして、 [**カスタムパッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてください。 これには、次の章の Dll も含まれます。 インポート後、 [**第6章**](#chapter-6---create-the-applicationinsightstracker-class)から続行します。

> [!IMPORTANT]
> Unity 内で Application Insights を使用するには、その DLL を Newtonsoft DLL と共にインポートする必要があります。 現在、Unity には、インポート後にプラグインを再構成する必要がある既知の問題があります。 バグが解決された後、これらの手順 (このセクションでは 4-7) は不要になりました。

Application Insights を独自のプロジェクトにインポートするには、 [プラグインを含む ' unitypackage ' をダウンロード](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage)していることを確認してください。 次に、以下を実行します。

1.  [ **アセット \> インポートパッケージの \> カスタムパッケージ** ] メニューオプションを使用して、 **unitypackage** を Unity に追加します。

2.  ポップアップ表示された [ **Unity パッケージのインポート** ] ボックスで、 **プラグイン** (およびそれを含む) のすべてが選択されていることを確認します。

    ![Unity パッケージのインポート](images/AzureLabs-Lab309-22.png)

3.  [ **インポート** ] ボタンをクリックして、プロジェクトに項目を追加します。

4.  プロジェクトビューの [ **プラグイン** ] の下にある [ **Insights** ] フォルダーにアクセスし、次のプラグイン *のみ* を選択します。

    -   Microsoft.ApplicationInsights

    ![Unity パッケージのインポート](images/AzureLabs-Lab309-23.png)

5.  この *プラグイン* を選択した状態で、 **任意のプラットフォーム** が **オフ** になっていることを確認し、[ **wsaplayer** ] も **オフ** になっていることを確認して、[ **適用** ] をクリックします。 これを行うのは、ファイルが正しく構成されていることを確認することだけです。

    ![Unity パッケージのインポート](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > このようなプラグインをマークすると、Unity エディターでのみ使用されるように構成されます。 WSA フォルダーには、Unity からプロジェクトがエクスポートされた後に使用される、異なる Dll のセットがあります。

6.  次に、[ **Insights** ] フォルダー内の **WSA** フォルダーを開く必要があります。 先ほど構成したものと同じファイルのコピーが表示されます。 このファイルを選択し、インスペクターで、 **すべてのプラットフォーム** が **オフ** になっていることを確認してから、[ **wsaplayer** ] **のみ** が **オン** になっていることを確認します。 **[適用]** をクリックします。

    ![Unity パッケージのインポート](images/AzureLabs-Lab309-25.png)

7. ここで、 **手順 4-6** に従う必要がありますが、代わりに *newtonsoft* プラグインの場合は、 結果がどのように表示されるかについては、以下のスクリーンショットを参照してください。

    ![Unity パッケージのインポート](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a>Chapter 4-カメラとユーザーコントロールを設定する

この章では、カメラとコントロールを設定して、ユーザーがシーン内を表示して移動できるようにします。

1.  [階層] パネルの空の領域を右クリックし、[空の **作成** ] をクリックし  >  **Empty** ます。

    ![カメラとユーザーコントロールを設定する](images/AzureLabs-Lab309-26.png)

2.  新しい空の作成オブジェクトの名前を **Camera Parent** に変更します。

    ![カメラとユーザーコントロールを設定する](images/AzureLabs-Lab309-27.png)

3.  [階層] パネルの空の領域を右クリックし、[ **3D オブジェクト** ]、[ **球** ] の順にクリックします。

4.  球の名前を **右** に変更します。

5.  右側の **変換スケール** を **0.1、0.1、0.1** に設定します。

    ![カメラとユーザーコントロールを設定する](images/AzureLabs-Lab309-28.png)

6.  *球体 collider* コンポーネントの **歯車** をクリックし、[ **コンポーネントの削除** ] をクリックして、右側から **球の collider** コンポーネントを削除します。

    ![カメラとユーザーコントロールを設定する](images/AzureLabs-Lab309-29.png)

7.  [階層] パネルで、 **メインカメラ** と **右側** のオブジェクトをカメラの **親** オブジェクトにドラッグします。

    ![カメラとユーザーコントロールを設定する](images/AzureLabs-Lab309-30.png)

8.  **メインカメラ** と **右側** のオブジェクトの両方の **変換位置** を **0、0、0** に設定します。

    ![カメラとユーザーコントロールを設定する](images/AzureLabs-Lab309-31.png)

    ![カメラとユーザーコントロールを設定する](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a>章 5-Unity シーンでのオブジェクトの設定

ここで、ユーザーが対話できるシーンの基本図形をいくつか作成します。

1.  [ *階層] パネル* の空の領域を右クリックし、[ **3d オブジェクト** ] で [ **平面** ] を選択します。

2.  平面の **変換位置** を **0、-1、0** に設定します。

3.  平面の **変換スケール** を **5、1、5** に設定します。

    ![Unity シーンでのオブジェクトの設定](images/AzureLabs-Lab309-33.png)

4.  **平面** オブジェクトと共に使用する基本的な素材を作成して、他の図形が見やすくなるようにします。 *プロジェクトパネル* に移動し、を右クリックして、[ **作成** ] をクリックします。次に **フォルダー** を作成し、新しいフォルダーを作成します。 名前を「 **マテリアル** 」にします。

    ![Unity シーンでのオブジェクトの設定](images/AzureLabs-Lab309-34.png) ![Unity シーンでのオブジェクトの設定](images/AzureLabs-Lab309-35.png)

5.  [ **素材** ] フォルダーを開き、右クリックして [ **作成** ]、[ **素材** ] の順にクリックし、新しい素材を作成します。 **Blue** という名前を指定します。

    ![Unity シーンでのオブジェクトの設定](images/AzureLabs-Lab309-36.png) ![Unity シーンでのオブジェクトの設定](images/AzureLabs-Lab309-37.png)

6.  新しい **青色** のマテリアルを選択した状態で、 *インスペクター* を見て、[ **albedo** ] の横にある四角形のウィンドウをクリックします。 青い色を選択します (下の画像は、 **16 進数の色: \# 3592ffff** )。 選択したら、[閉じる] ボタンをクリックします。

    ![Unity シーンでのオブジェクトの設定](images/AzureLabs-Lab309-38.png)

7.  新しい素材を [ **マテリアル** ] フォルダーから、新しく作成した **平面** のシーンにドラッグします (または、 *階層* 内の [ **平面** ] オブジェクトにドロップします)。

    ![Unity シーンでのオブジェクトの設定](images/AzureLabs-Lab309-39.png)

8.  [ *階層] パネル* の空の領域を右クリックし、[ **3d オブジェクト]** の [カプセル] をクリックします。

    -  **カプセル** を選択した状態で、 **変換***位置* を **-10、1、0** に変更します。

9.  [ *階層] パネル* の空の領域を右クリックし、[ **3d オブジェクト]** の [キューブ] をクリックします。

    -  **キューブ** を選択した状態で、 **変換***位置* を **0、0、10** に変更します。

10. [ *階層] パネル* の空の領域を右クリックし、[ **3d オブジェクト]、[球** ] の順にクリックします。

    -  **球** を選択した状態で、 **変換***位置* を **10、0、0** に変更します。

    ![Unity シーンでのオブジェクトの設定](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > これらの *位置* の値は *提案* です。 オブジェクトの位置は自由に設定できますが、オブジェクトの距離がカメラから遠く離れていない場合は、アプリケーションのユーザーにとっても簡単です。

11. アプリケーションが実行されている場合は、シーン内のオブジェクトを識別できる必要があります。これを実現するには、そのオブジェクトにタグを付ける必要があります。 オブジェクトの1つを選択し、[ *インスペクター* ] パネルで [ **タグの追加...** ] をクリックします。これにより、 *インスペクター* と **タグ & レイヤー** パネルが表示されます。

    ![Unity シーン ](images/AzureLabs-Lab309-41.png) でのオブジェクトの設定 ![](images/AzureLabs-Lab309-42.png)

12. [+] 記号 **(プラス記号)** をクリックし、タグ名を「テキスト」 **として** 入力します。

    ![Unity シーンでのオブジェクトの設定](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > タグに別の名前を使用する場合は、シーン内でオブジェクトが検出され、検出されるように、この変更によって *DataFromAnalytics* 、 *Objecttrigger* 、および *宝石* のスクリプトも後で作成されるようにする必要があります。

13. タグを作成したら、3つのオブジェクトすべてに適用する必要があります。 *階層* から、 **shift** キーを押したまま、[ **カプセル** ]、[ **キューブ** ]、[ **球** ] のオブジェクトをクリックし、次に [ *インスペクター* ] の下にあるドロップダウン **メニューをクリック** します。次に、作成 *したオブジェクト* をクリックします。

    ![Unity シーン ](images/AzureLabs-Lab309-44.png) でのオブジェクトの設定 ![](images/AzureLabs-Lab309-45.png)

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a>Chapter 6-ApplicationInsightsTracker クラスの作成

作成する必要のある最初のスクリプトは **ApplicationInsightsTracker** です。これは次の役割を担います。

1.  ユーザーの操作に基づいてイベントを作成し、Azure アプリケーション Insights に送信します。

2. ユーザーの操作に応じて、適切なイベント名を作成します。

3. Application Insights サービスインスタンスにイベントを送信しています。

このクラスを作成するには:

1.  [ *プロジェクト] パネル* 内を右クリックし、[フォルダーの **作成** ] をクリックし  >  **Folder** ます。 フォルダーに **スクリプト** の名前を指定します。

    ![ApplicationInsightsTracker クラスを作成する](images/AzureLabs-Lab309-46.png)  ![ApplicationInsightsTracker クラスを作成する](images/AzureLabs-Lab309-47.png)

2.  **Scripts** フォルダーを作成したら、それをダブルクリックして開きます。 次に、そのフォルダー内で右クリックし **Create** 、[  >  **C# スクリプト** の作成] をクリックします。 スクリプトに **ApplicationInsightsTracker** という名前を指定します。

3.  新しい **ApplicationInsightsTracker** スクリプトをダブルクリックして、 **Visual Studio** で開きます。

4.  スクリプトの先頭にある名前空間を次のように更新します。

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  クラス内で、次の変数を挿入します。

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > 手順9の [章](#chapter-1---the-azure-portal)で説明したように、Azure Portal の *サービスキー* を使用して、 **instrumentationKey、applicationId、API_Key** の値を適切に設定します。

6.  次に、クラスが初期化されるときに呼び出される **Start ()** メソッドと起動前 **()** メソッドを追加します。

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  アプリケーションによって登録されたイベントとメトリックの送信を担当するメソッドを追加します。

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  *Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。

## <a name="chapter-7---create-the-gaze-script"></a>第7章-宝石のスクリプトを作成する

次に作成するスクリプトは、 **見つめ** スクリプトです。 このスクリプトは、ユーザーがどのオブジェクトを調べているかを検出するために、 *メインカメラ* から投影される *Raycast* を作成する役割を担います。 この場合、 *Raycast* は、ユーザーがオブジェクトでオブジェクトを見ているかどうかを特定 **し、その** オブジェクトに対するユーザーの *gazes* 時間をカウントする必要があります。

1.  [ **Scripts** ] フォルダーをダブルクリックして開きます。

2.  **Scripts** フォルダー内を右クリックし、[ **Create**  >  **C# スクリプト** の作成] をクリックします。 スクリプトに「」という名前を **指定します** 。

3.  スクリプトをダブルクリックして、Visual Studio で開きます。

4.  既存のコードを次のコードに置き換えます。

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  起動可能な **()** メソッドと **Start ()** メソッドのコードを追加する必要があります。

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  **見つめ** クラス内で、 **Update ()** メソッドに次のコードを追加して *Raycast* を射影し、ターゲットのヒットを検出します。

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  **ResetFocusedObject ()** メソッドを追加して、ユーザーがオブジェクトを参照したときに **Application Insights** にデータを送信します。

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  これで、 **宝石** スクリプトが完成しました。 *Unity* に戻る前に、変更を *Visual Studio* に保存します。

## <a name="chapter-8---create-the-objecttrigger-class"></a>章 8-ObjectTrigger クラスを作成する

次のスクリプトを作成する必要があります。 **Objecttrigger** は次の役割を担います。

- メインカメラとの競合に必要なコンポーネントを追加します。
- カメラがオブジェクトの近くにあるかどうか **を検出** しています。

スクリプトを作成するには:

1.  [ **Scripts** ] フォルダーをダブルクリックして開きます。

2.  **Scripts** フォルダー内を右クリックし、[ **Create**  >  **C# スクリプト** の作成] をクリックします。 スクリプト **Objecttrigger** にという名前を指定します。

3.  スクリプトをダブルクリックして、Visual Studio で開きます。 既存のコードを次のコードに置き換えます。

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  *Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。

## <a name="chapter-9---create-the-datafromanalytics-class"></a>第9章-DataFromAnalytics クラスの作成

次の役割を果たす **DataFromAnalytics** スクリプトを作成する必要があります。

- カメラによって最もよく使用されているオブジェクトに関する分析データをフェッチしています。
- *サービスキー* を使用して、Azure アプリケーション Insights サービスインスタンスと通信できるようにします。
- イベント数が最も多いに従って、シーン内のオブジェクトを並べ替えます。
- 最も近づいたオブジェクトのマテリアルの色を *緑色* に変更します。

スクリプトを作成するには:

1.  [ **Scripts** ] フォルダーをダブルクリックして開きます。

2.  **Scripts** フォルダー内を右クリックし、[ **Create**  >  **C# スクリプト** の作成] をクリックします。 スクリプトに **DataFromAnalytics** という名前を指定します。

3.  スクリプトをダブルクリックして、Visual Studio で開きます。

4.  次の名前空間を挿入します。

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  スクリプト内に次の内容を挿入します。

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  **DataFromAnalytics** クラス内で、 **Start ()** メソッドの直後に、 **fetchanalytics ()** という次のメソッドを追加します。 このメソッドは、キーと値のペアのリストを作成します。これには、設定 *オブジェクト* とプレースホルダーイベント数を指定します。 次に、 **Getwebrequest ()** コルーチンを初期化します。 *Application Insights* の呼び出しのクエリ構造は、 *クエリ URL* エンドポイントとしてもこのメソッド内にあります。

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  **Fetchanalytics ()** メソッドのすぐ下に、 *IEnumerator* を返す **getwebrequest ()** というメソッドを追加します。 このメソッドは、特定の *オブジェクト* に対応するイベントが *Application Insights* 内で呼び出された回数を要求します。 送信されたすべてのクエリが返されると、決定 **E勝者 ()** メソッドが呼び出されます。

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readability).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  次のメソッドは、最も高いイベント数に従って、判別 *オブジェクト* と *Int* のペアのリストを並べ替える、決定 **e勝者 ()** です。 次に、その *オブジェクト* の素材の色を *緑色* に変更します (最大カウントがあることに関するフィードバックとして)。 これにより、分析結果を含むメッセージが表示されます。

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  *Application Insights* から受信した JSON オブジェクトを逆シリアル化するために使用されるクラス構造を追加します。 これらのクラスは、クラス定義の **外部** にある **DataFromAnalytics** クラスファイルの一番下に追加します。

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. *Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。

## <a name="chapter-10---create-the-movement-class"></a>Chapter 10-移動クラスを作成する

**移動** スクリプトは、次に作成する必要があるスクリプトです。 以下の処理を担当します。

- カメラが見ている方向に従って、メインカメラを移動します。
- シーンオブジェクトに他のすべてのスクリプトを追加します。

スクリプトを作成するには:

1.  [ **Scripts** ] フォルダーをダブルクリックして開きます。

2.  **Scripts** フォルダー内を右クリックし、[ **Create**  >  **C# スクリプト** の作成] をクリックします。 スクリプトの **移動** に名前を指定します。

3.  スクリプトをダブルクリックして、 *Visual Studio* で開きます。

4.  既存のコードを次のコードに置き換えます。

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  **移動** クラス内で、空の **Update ()** メソッドの *下* に、ユーザーがハンドコントローラーを使用して仮想空間内を移動できるようにする次のメソッドを挿入します。

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  最後に、 **Update ()** メソッド内にメソッド呼び出しを追加します。

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  *Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。

## <a name="chapter-11---setting-up-the-scripts-references"></a>Chapter 11-スクリプト参照の設定

この章では、 **移動** スクリプトを **カメラの親** に配置し、その参照ターゲットを設定する必要があります。 そのスクリプトは、必要な場所にある他のスクリプトの配置を処理します。

1.  [ *プロジェクト] パネル* の [ **スクリプト** ] フォルダーで、[ *階層] パネル* にある [ **カメラ] 親** オブジェクトに **移動** スクリプトをドラッグします。

    ![Unity シーンでのスクリプト参照の設定](images/AzureLabs-Lab309-48.png)

2.  **カメラの親** をクリックします。 [ *階層] パネル* で、[ *階層]* パネルの **右側** のオブジェクトを [ *インスペクター] パネル* の [参照ターゲット] の [ **コントローラー** ] にドラッグします。 次の図に示すように、 **ユーザーの速度** を **5** に設定します。

    ![Unity シーンでのスクリプト参照の設定](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a>第12章-Unity プロジェクトのビルド

このプロジェクトの Unity セクションに必要なものはすべて完了したので、Unity から構築します。

1.  [ **ビルドの設定** ]、([ **ファイル**  >  **ビルドの設定** ]) の順に移動します。

2.  [ **ビルドの設定** ] ウィンドウで、[ **ビルド** ] をクリックします。

    ![Unity プロジェクトを UWP ソリューションにビルドする](images/AzureLabs-Lab309-50.png)

3.  **エクスプローラー** ウィンドウがポップアップ表示され、ビルドの場所を入力するように求められます。 (左上隅にある [ **新しいフォルダー** ] をクリックして) 新しいフォルダーを作成し、 **ビルド** という名前を指定します。

    ![Unity プロジェクトを UWP ソリューションにビルドする](images/AzureLabs-Lab309-51.png)

    1.  [新しい **ビルド** ] フォルダーを開き、別のフォルダーを作成し ([ **新しいフォルダー** ] をもう一度使用)、「 **MR \_ Azure \_ Application \_ Insights** 」という名前を指定します。

        ![Unity プロジェクトを UWP ソリューションにビルドする](images/AzureLabs-Lab309-52.png)

    2.  **MR \_ Azure \_ Application \_ Insights** フォルダーを選択した状態で、[ **フォルダーの選択** ] をクリックします。 プロジェクトがビルドされるまでに1分ほどかかります。

4.  次の *ビルド* では、新しいプロジェクトの場所を示す **ファイルエクスプローラー** が表示されます。

## <a name="chapter-13---deploy-mr_azure_application_insights-app-to-your-machine"></a>第13章: MR_Azure_Application_Insights アプリをコンピューターにデプロイする

ローカルコンピューターに **MR \_ Azure \_ Application \_ Insights** アプリをデプロイするには、次のようにします。

1.  **Visual Studio** で **MR \_ Azure \_ Application \_ Insights** アプリのソリューションファイルを開きます。

2.  **ソリューションプラットフォーム** で、[ **X86, ローカルコンピューター** ] を選択します。

3.  **ソリューション構成** で、[ **デバッグ** ] を選択します。

    ![Unity プロジェクトを UWP ソリューションにビルドする](images/AzureLabs-Lab309-53.png)

4.  [ **ビルド] メニュー** の [ **ソリューションの配置** ] をクリックして、アプリケーションをコンピューターにサイドロードします。

5.  アプリがインストール済みのアプリの一覧に表示され、起動できる状態になります。

6. Mixed reality アプリケーションを起動します。

7. シーン内を移動し、オブジェクトに近づいて、それらを確認すると、 *Azure Insights サービス* が十分なイベントデータを収集したときに、最も近いオブジェクトが緑色に設定されます。

> [!IMPORTANT] 
> サービスによって収集される *イベントとメトリック* の平均待機時間は約15分かかりますが、場合によっては最大1時間かかることがあります。

## <a name="chapter-14---the-application-insights-service-portal"></a>第14章-Application Insights サービスポータル

複数のオブジェクトでシーンと gazed を移動すると、 *Application Insights サービス* ポータルで収集されたデータを確認できます。

1.  Application Insights サービスポータルに戻ります。

2.  [ *メトリックスエクスプローラー* ] をクリックします。

    ![収集したデータの表示](images/AzureLabs-Lab309-54.png)

3.  これは、アプリケーションに関連する *イベントとメトリック* を表すグラフを含むタブで開きます。 前述のように、データがグラフに表示されるまでに時間がかかる場合があります (最大1時間)。

    ![収集したデータの表示](images/AzureLabs-Lab309-55.png)

4.  [アプリケーションバージョンごとの *イベントの総数* ] の *イベントバー* をクリックすると、イベントの詳細な内訳が名前と共に表示されます。

    ![収集したデータの表示](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a>Application Insights サービスアプリケーションが完成しました

これで、Application Insights サービスを活用してアプリ内でユーザーのアクティビティを監視する、mixed reality アプリが作成されました。

![コースの結果](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a>ボーナスの演習

**演習1**

オブジェクトを手動で作成するのではなく、オブジェクトを手動で作成し、スクリプト内の平面上に座標を設定します。 このようにして、最も人気のあるオブジェクト (つまり、宝石または近接の結果) を Azure に要求し、それらのオブジェクト *のうちの1つ* を生成することができます。

**演習2**

Application Insights の結果を時間で並べ替えて、最も関連性の高いデータを取得し、その時間に依存するデータをアプリケーションに実装します。

