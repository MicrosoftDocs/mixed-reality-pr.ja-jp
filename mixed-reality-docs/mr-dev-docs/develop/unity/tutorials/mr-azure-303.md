---
title: MR と Azure 303-自然言語の理解 (LUIS)
description: このコースでは、mixed reality アプリケーション内に Azure Language Understanding インテリジェンスサービス (LUIS) を実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, チュートリアル, api, 言語についてのインテリジェンスサービス, luis, hololens, イマーシブ, vr, Windows 10, Visual Studio
ms.openlocfilehash: a91fcd2e20ce1e1731bd398fa72923f6ff5e8406
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583429"
---
# <a name="mr-and-azure-303-natural-language-understanding-luis"></a>MR と Azure 303: 自然言語について (LUIS)

<br>

>[!NOTE]
>Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。  そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。  これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。  これらは、サポートされているデバイス上で継続して動作するように、保守されます。 今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。  この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。

<br>

このコースでは、Language Understanding を Azure Cognitive Services を使用する mixed reality アプリケーションに Language Understanding API と統合する方法について説明します。

![ラボの結果](images/AzureLabs-Lab3-000.png)

*Language Understanding (LUIS)* は Microsoft Azure サービスです。これにより、アプリケーションは、ユーザーが必要とするものを抽出するなどして、ユーザーの入力を除外することができます。 これは機械学習を通じて実現されます。 machine learning では、入力情報を認識して学習した後、詳細な関連情報を返信できます。 詳細については、 [Azure Language Understanding (LUIS) のページ](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)を参照してください。

このコースを完了すると、現実のイマーシブヘッドセットアプリケーションが完成し、次のことができるようになります。

1.  イマーシブヘッドセットに接続されているマイクを使用して、ユーザー入力音声をキャプチャします。 
2.  キャプチャしたディクテーションを *Azure Language Understanding Intelligent Service* (*LUIS*) に送信します。 
3.  LUIS では、送信情報から意味を抽出して分析し、ユーザーの要求の意図を判断しようとします。

開発には、ユーザーが音声や宝石を使用してシーン内のオブジェクトのサイズと色を変更できるアプリの作成が含まれます。 モーションコントローラーの使用については説明しません。

アプリケーションでは、結果をデザインと統合する方法については、お客様のニーズに合わせてください。 このコースは、Azure サービスを Unity プロジェクトと統合する方法を説明することを目的としています。 このコースで得られた知識を使用して、mixed reality アプリケーションを強化することができます。

LUIS を複数回トレーニングできるように準備します。これについては、 [12 章](#chapter-12--improving-your-luis-service)で説明します。 LUIS がトレーニングされると、より多くの結果が得られます。

## <a name="device-support"></a>デバイス サポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td>MR と Azure 303: 自然言語について (LUIS)</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> このコースでは主に Windows Mixed Reality イマーシブ (VR) ヘッドセットに焦点を当てていますが、このコースで学習した内容を Microsoft HoloLens に適用することもできます。 このコースに従うと、HoloLens をサポートするために必要となる可能性のある変更に関する注意事項が表示されます。 HoloLens を使用する場合、音声キャプチャ中にエコーが発生することがあります。

## <a name="prerequisites"></a>前提条件

> [!NOTE]
> このチュートリアルは、Unity と C# の基本的な経験がある開発者向けに設計されています。 また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証されたものを表します (2018 年5月)。 「 [ツールのインストール](../../install-the-tools.md) 」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に記載されているものよりも新しいソフトウェアで見つかったものと完全に一致するとは限りません。

このコースでは、次のハードウェアとソフトウェアをお勧めします。

- 開発用 PC で、 [Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) (VR) ヘッドセット開発と互換性があります。
- [開発者モードが有効になっている Windows 10 の作成者の更新プログラム (またはそれ以降)](../../install-the-tools.md)
- [最新の Windows 10 SDK](../../install-the-tools.md)
- [Unity 2017.4](../../install-the-tools.md)
- [Visual Studio 2017](../../install-the-tools.md)
- [Windows Mixed Reality イマーシブ (VR) ヘッドセット](../../../discover/immersive-headset-hardware-details.md)または開発者モードを有効にした[Microsoft HoloLens](/hololens/hololens1-hardware)
- 内蔵マイク付きヘッドホンのセット (ヘッドセットにマイクとスピーカーが組み込まれていない場合)
- Azure のセットアップと LUIS の取得のためのインターネットアクセス

## <a name="before-you-start"></a>開始する前に

1.  このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。 
2.  コンピューターがディクテーションを有効にできるようにするには、[ **Windows の設定] > [プライバシー > 音声、インク & 入力** し、[ **音声サービスの有効化**] をクリックして、[候補] を入力します。
3.  このチュートリアルのコードを使用すると、コンピューターに設定されている **既定のマイクデバイス** から記録できます。 既定のマイクデバイスが、音声をキャプチャするために使用するものとして設定されていることを確認します。
4.  ヘッドセットにマイクが内蔵されている場合は、 *Mixed Reality ポータル* の設定で *"ヘッドセットを磨耗したときにヘッドセットの mic に切り替える"* オプションがオンになっていることを確認してください。

    ![イマーシブヘッドセットの設定](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a>第1章: Azure Portal のセットアップ

Azure で *Language Understanding* サービスを使用するには、アプリケーションで使用できるようにサービスのインスタンスを構成する必要があります。

1.  [Azure Portal](https://portal.azure.com) にログインします。

    > [!NOTE]
    > まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。 このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。

2.  ログインしたら、左上隅にある [ **新規** ] をクリックし、 *Language Understanding* を検索して、 **Enter キー** を押します。 

    ![LUIS リソースの作成](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > 新しいポータルで、 **New** という単語が **リソースの作成** に置き換えられました。
 
3.  右側の新しいページには、Language Understanding サービスの説明が表示されます。 このページの左下にある [ **作成** ] ボタンを選択して、このサービスのインスタンスを作成します。

    ![LUIS サービスの作成-法的通知](images/AzureLabs-Lab3-02.png)
 
4.  [作成:

    1. このサービスインスタンスに必要な **名前** を挿入します。
    2. **サブスクリプション** を選択します。
    3. 適切な **価格レベル** を選択します。これが *LUIS サービス* を初めて作成する場合は、free レベル (F0) を使用できます。 このコースでは、無料の割り当ては十分ではありません。
    4. リソースグループを選択するか、新しい **リソースグループ** を作成します。 リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。 1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのコースなど) を共通のリソースグループに保持することをお勧めします。 

        > Azure リソースグループの詳細については、 [リソースグループ](/azure/azure-resource-manager/resource-group-portal)に関する記事をご覧ください。

    5. リソースグループの **場所** を決定します (新しいリソースグループを作成している場合)。 この場所は、アプリケーションを実行するリージョンに配置するのが理想的です。 一部の Azure 資産は、特定のリージョンでのみ利用できます。
    6. また、このサービスに適用されている使用条件を理解していることを確認する必要があります。
    7. **［作成］** を選択します

        ![Create LUIS service-ユーザー入力](images/AzureLabs-Lab3-03.png)
 
5.  [ **作成**] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。
6.  サービスインスタンスが作成されると、ポータルに通知が表示されます。 
 
    ![新しい Azure 通知イメージ](images/AzureLabs-Lab3-04.png)

7.  通知をクリックして、新しいサービスインスタンスを探索します。

    ![リソース作成の成功通知](images/AzureLabs-Lab3-05.png)
 
8.  通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。 新しい LUIS サービスインスタンスが表示されます。 
 
    ![LUIS キーへのアクセス](images/AzureLabs-Lab3-06.png)

9.  このチュートリアルでは、アプリケーションがサービスの呼び出しを行う必要があります。サービスは、サービスのサブスクリプションキーを使用して実行されます。
10. *LUIS API* サービスの [*クイックスタート*] ページで、最初の手順に移動し、*キーを取得* して、[**キー** ] をクリックします (これを行うには、[サービス] ナビゲーションメニューにある、キーアイコンで示されている青いハイパーリンクキーをクリックします)。 これにより、サービス *キー* が表示されます。
11. 表示されているキーの1つをコピーします。これは、プロジェクトの後半で必要になります。 
12. [ *サービス* ] ページで、[ *Language Understanding ポータル* ] をクリックして、LUIS アプリ内で新しいサービスの作成に使用する web ページにリダイレクトします。 

## <a name="chapter-2--the-language-understanding-portal"></a>第2章: Language Understanding ポータル

このセクションでは、LUIS ポータルで LUIS アプリを作成する方法について説明します。 

> [!IMPORTANT]
> この章内で *エンティティ*、 *インテント*、および *発話* を設定することは、LUIS サービスを構築するための最初の手順であることに注意してください。サービスを再トレーニングして、より正確なものにする必要もあります。 サービスの再トレーニングについては、このコースの [最後の章](#chapter-12--improving-your-luis-service) で説明されているため、完了していることを確認してください。

1.  *Language Understanding ポータル* に達したら、Azure portal と同じ資格情報を使用してログインする必要がある場合があります (まだログインしていない場合)。 

    ![LUIS ログインページ](images/AzureLabs-Lab3-07.png)
 
2.  LUIS を初めて使用する場合は、[ようこそ] ページの一番下までスクロールして [ **CREATE LUIS app (アプリの作成** )] ボタンを見つけてクリックする必要があります。

    ![LUIS アプリの作成ページ](images/AzureLabs-Lab3-08.png)
 
3.  ログインしたら、[ **マイアプリ** ] をクリックします (現在このセクションにない場合)。 [ **新しいアプリの作成**] をクリックします。

    ![LUIS-マイアプリのイメージ](images/AzureLabs-Lab3-09.png)
 
4.  アプリに *名前* を付けます。
5.  アプリが英語とは異なる言語を認識する場合は、 *カルチャ* を適切な言語に変更する必要があります。
6.  ここでは、新しい LUIS アプリの *説明* を追加することもできます。

    ![LUIS-新しいアプリを作成する](images/AzureLabs-Lab3-10.png)

7.  [**完了**] をクリックすると、新しい *LUIS* アプリケーションの [*ビルド*] ページが表示されます。
8.  ここで理解しておくべき重要な概念がいくつかあります。

    -   *インテント* は、ユーザーからのクエリに従って呼び出されるメソッドを表します。 *インテント* には、1つまたは複数の *エンティティ* を含めることができます。
    -   *エンティティ* は、 *インテント* に関連する情報を記述するクエリのコンポーネントです。
    -   *発話* は、開発者によって提供されるクエリの例であり、LUIS は自身をトレーニングするために使用します。

これらの概念が完全に明確でない場合は、心配しないでください。この章ではさらに詳しく説明します。

最初に、このコースを構築するために必要な *エンティティ* を作成します。

9.  ページの左側にある [ *エンティティ*] をクリックし、[ **新しいエンティティの作成**] をクリックします。

    ![新しいエンティティの作成](images/AzureLabs-Lab3-11.png)

10. 新しいエンティティの *色* を呼び出し、その種類を *Simple* に設定して、[ **完了**] を押します。

    ![単純なエンティティの作成-色](images/AzureLabs-Lab3-12.png)
 
11. このプロセスを繰り返して、次の3つの単純なエンティティを作成します。

    -   *まま*
    -   *ダウンサイズ*
    -   *target*

結果は次の図のようになります。

![エンティティ作成の結果](images/AzureLabs-Lab3-13.png)
 
この時点で、 *インテント* の作成を開始できます。 

> [!WARNING]
> インテントを削除しない **でください** 。

12. ページの左側にある [ **インテント**] をクリックし、[ **新しいインテントの作成**] をクリックします。

    ![新しいインテントの作成](images/AzureLabs-Lab3-14.png)

13. 新しい *インテント* **changeobjectcolor** を呼び出します。

    > [!IMPORTANT]
    > この *意図* 名は、このコースの後半でコード内で使用されます。したがって、最適な結果を得るために、この名前を指定されたとおりに使用してください。

名前を確認すると、インテントページにリダイレクトされます。

![LUIS ページ](images/AzureLabs-Lab3-15.png)

5つ以上の異なる *発話* を入力するよう求めるテキストボックスが表示されます。

> [!NOTE]
> LUIS は、すべての発話を小文字に変換します。

14. 上部のテキストボックスに次の *(発話)* を挿入します (現在、テキストの *種類は約5例です)。* ) を **入力** し、enter キーを押します。

```
The color of the cylinder must be red
```

新しい *(発話)* は、の下の一覧に表示されます。

同じプロセスに従って、次の6つの発話を挿入します。

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

作成した各 (発話) に対して、LUIS がエンティティとして使用する単語を識別する必要があります。 この例では、すべての色に *色* エンティティとしてラベルを付け、 *ターゲットエンティティとしてターゲットに* 使用できるすべての参照を指定する必要があります。

15. これを行うには、最初の (発話) の " *シリンダー* " をクリックし、[ *ターゲット*] を選択します。

    ![(発話) ターゲットの識別](images/AzureLabs-Lab3-16.png)
 
16. 次に、最初の (発話) の " *red* " という語をクリックして、[ *色*] を選択します。

    ![(発話) エンティティの識別](images/AzureLabs-Lab3-17.png)
 
17. 次の行にラベルを付けます。ここで、 *キューブ* は *ターゲット* にする必要があり、 *黒* は *色* にする必要があります。 また、" *this"*、 *"it"*、および *"this object"* という単語を使用しています。これにより、指定されていないターゲット型も使用できるようになります。 

18. すべての発話がラベル付きのエンティティを持つようになるまで、上記の手順を繰り返します。 ヘルプが必要な場合は、次の画像を参照してください。

    > [!TIP]
    > エンティティ ラベルを付ける単語を選択するときは:
    > - 単一の単語の場合は、単にクリックします。
    > - 2つ以上の単語のセットについては、セットの先頭と末尾にあるをクリックします。

    > [!NOTE]
    > [ *トークンビュー* ] トグルボタンを使用して、 **エンティティ/トークンビュー** を切り替えることができます。

19. 次の図に示すように結果が表示され、 **エンティティ/トークンビュー** が表示されます。

    ![トークン & エンティティビュー](images/AzureLabs-Lab3-18.png)
  
20. この時点で、ページの右上にある [ **Train** ] ボタンをクリックして、小さなラウンドインジケーターが緑色になるまで待ちます。 これは、この目的を認識するために LUIS が正常にトレーニングされたことを示します。

    ![LUIS のトレーニング](images/AzureLabs-Lab3-19.png)
 
21. この演習では、 *target*、*アップ* サイズ、および *ダウンサイズ* エンティティを使用して、 **changeobjectsize** という新しいインテントを作成します。
22. 前の意図と同じプロセスに従って、 *サイズ* を変更するために、次の8つの発話を挿入します。

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. 結果は次の図のようになります。

    ![ChangeObjectSize トークン/エンティティの設定](images/AzureLabs-Lab3-20.png) 

24. **Changeobjectcolor** と **changeobjectcolor** の両方の作成とトレーニングが完了したら、ページの上部にある [**発行**] ボタンをクリックします。

    ![LUIS サービスの発行](images/AzureLabs-Lab3-21.png)

25. [ *発行* ] ページで、LUIS アプリを完成させ、コードからアクセスできるように発行します。

    1. ドロップダウンを [**運用環境**]*に* 設定します。
    2. タイムゾーン *をタイム* ゾーンに設定します。
    3. チェックボックスをオンにして、予測される **すべてのインテントスコアを含め** ます。
    4. [ **運用スロットに発行**] をクリックします。

        ![発行の設定](images/AzureLabs-Lab3-22.png)

26. [ *リソースとキー*] セクションで、次の手順を実行します。

    1.  Azure Portal でサービスインスタンスに設定するリージョンを選択します。
    2.  次の **Starter_Key** 要素があることがわかりますが、無視します。
    3.  [ **キーの追加** ] をクリックし、サービスインスタンスを作成したときに Azure Portal で取得した *キー* を挿入します。 Azure と LUIS portal が同じユーザーにログインしている場合は、[ *テナント名*]、[ *サブスクリプション名*]、および使用する *キー* のドロップダウンメニューが表示されます (azure portal で以前に指定したものと同じ名前になります)。

    > [!IMPORTANT] 
    > *エンドポイント* の下で、挿入したキーに対応するエンドポイントのコピーを取得します。これは、すぐにコードで使用します。
 
## <a name="chapter-3--set-up-the-unity-project"></a>第3章: Unity プロジェクトの設定

次に示すのは、mixed reality で開発するための一般的な設定です。そのため、他のプロジェクトに適したテンプレートです。

1.  *Unity* を開き、[**新規**] をクリックします。 

    ![新しい Unity プロジェクトを開始します。](images/AzureLabs-Lab3-24.png)

2.  ここで、Unity プロジェクト名を指定し、 **MR_LUIS** を挿入する必要があります。 プロジェクトの種類が **3d** に設定されていることを確認します。 場所を適切な **場所** に設定します (ルートディレクトリの方が適していることに注意してください)。 次に、[ **プロジェクトの作成**] をクリックします。

    ![新しい Unity プロジェクトの詳細を指定します。](images/AzureLabs-Lab3-25.png)
 
3.  Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。 [> の設定の編集] に移動し、新しいウィンドウで [ **外部ツール**] に移動します。 **外部スクリプトエディター** を **Visual Studio 2017** に変更します。 [ **基本設定** ] ウィンドウを閉じます。

    ![スクリプトエディターの設定を更新します。](images/AzureLabs-Lab3-26.png)
 
4.  次に、[**ファイル > ビルド設定**] に移動し、[プラットフォームの **切り替え**] ボタンをクリックして、プラットフォームを **ユニバーサル Windows プラットフォーム** に切り替えます。

    ![[ビルドの設定] ウィンドウで、[プラットフォーム] を [UWP] に切り替えます。](images/AzureLabs-Lab3-27.png)
 
5.  [ **ファイル > ビルド設定** ] にアクセスし、次のことを確認します。

    1. **ターゲットデバイス** が **任意のデバイス** に設定されています

        > Microsoft HoloLens の場合は、 **ターゲットデバイス** を *HoloLens* に設定します。

    2. **ビルドの種類** が **D3D** に設定されています
    3. **SDK** は最新の **インストール** に設定されています
    4. **Visual Studio のバージョン** が、**インストールされている最新** バージョンに設定されています
    5. **ビルドと実行** は **ローカルコンピューター** に設定されています
    6. シーンを保存し、ビルドに追加します。

        1. これを行うには、[開いている **シーンの追加**] を選択します。 保存ウィンドウが表示されます。
        
            ![[開いているシーンを追加] ボタンをクリックする](images/AzureLabs-Lab3-28.png)

        2. この新しいフォルダーを作成し、今後のシーンに加えて、[ **新しいフォルダー** ] ボタンを選択します。新しいフォルダーを作成するには、名前を「 **シーン**」にします。

            ![新しいスクリプトフォルダーの作成](images/AzureLabs-Lab3-29.png)

        3. 新しく作成した [ **シーン** ] フォルダーを開き、[ *ファイル名*: テキスト] フィールドに「 **MR_LuisScene**」と入力して、[ **保存**] を押します。

            ![新しいシーンに名前を付けます。](images/AzureLabs-Lab3-30.png)

    7. それ以外の設定は、[ *ビルド設定*] の [既定] のままにしておきます。

6. [ *ビルドの設定* ] ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 *インスペクター* が配置されている領域の関連パネルが開きます。 

    ![プレーヤーの設定を開きます。](images/AzureLabs-Lab3-31.png) 
 
7. このパネルでは、いくつかの設定を確認する必要があります。

    1. [ **その他の設定** ] タブで、次のようにします。

        1. **スクリプトランタイムのバージョン** は **安定** している必要があります (.net 3.5 と同等)。
        2. **バックエンド** は **.net** である必要があります
        3. **API 互換性レベル** は **.net 4.6** である必要があります

            ![その他の設定を更新します。](images/AzureLabs-Lab3-32.png)
      
    2. [ **発行の設定** ] タブの [ **機能**] で、次の項目を確認します。

        1. **InternetClient**
        2. **マイク**

            ![発行設定を更新しています。](images/AzureLabs-Lab3-33.png)

    3. パネルの下にある [ **XR settings** (発行の **設定**] の下にあります) で、[ **サポートされている仮想現実**] をティックし、 **Windows Mixed reality SDK** が追加されていることを確認します。

        ![X R の設定を更新します。](images/AzureLabs-Lab3-34.png)

8.  *ビルド設定* に戻る _Unity C#_ プロジェクトはグレーで表示されなくなりました。このの横にあるチェックボックスをオンにします。 
9.  [ビルド設定] ウィンドウを閉じます。
10. シーンとプロジェクトを保存します ([**ファイル] > [シーン/ファイルの保存] > [プロジェクトの保存**])。

## <a name="chapter-4--create-the-scene"></a>章4–シーンを作成する

> [!IMPORTANT]
> このコースの *Unity セットアップ* コンポーネントをスキップしてコードに直接進む場合は、 [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage)をダウンロードし、 [カスタムパッケージ](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてから、 [第5章](#chapter-5--create-the-microphonemanager-class)から続行してください。 

1.  [ *階層] パネル* の空の領域を右クリックし、[ **3d オブジェクト**] の下に **平面** を追加します。

    ![平面を作成します。](images/AzureLabs-Lab3-35.png)

2.  *階層* 内を右クリックしてさらにオブジェクトを作成した場合、最後のオブジェクトを選択したままにすると、選択したオブジェクトが新しいオブジェクトの親になります。 階層内の空いている領域を左クリックし、右クリックしてください。

3.  上記の手順を繰り返して、次のオブジェクトを追加します。

    1. *Sphere*
    2. *シリンダ*
    3. *Cube*
    4. *3D テキスト*

4.  結果として得られるシーン *階層* は、次の図のようになります。

    ![シーン階層のセットアップ。](images/AzureLabs-Lab3-36.png)
 
5.  **メインカメラ** をクリックして選択し、[*インスペクター] パネル* で、すべてのコンポーネントを含むカメラオブジェクトを確認します。
6.  [*インスペクター] パネル* の下部にある [**コンポーネントの追加**] ボタンをクリックします。

    ![オーディオソースの追加](images/AzureLabs-Lab3-37.png)
 
7.  上記のように、[ *オーディオソース*] という名前のコンポーネントを検索します。
8.  また、メインカメラの *変換* コンポーネントが (0, 0, 0) に設定されていることを確認します。これを行うには、カメラの *変換* コンポーネントの横にある **歯車** アイコンを押し、[**リセット**] を選択します。 *変換* コンポーネントは次のようになります。

    1.  *Position* が **0、0、0** に設定されています。
    2.  *回転* は **0、0、0** に設定されます。

    > [!NOTE] 
    > Microsoft HoloLens の場合は、次のものも変更する必要があります。これは、**メインカメラ** の **カメラ** コンポーネントに含まれています。
    > - **フラグのクリア:** 純色。
    > - **背景** ' Black, Alpha 0 ' –16進数の色: #00000000。

9.  **平面** を左クリックして選択します。 [ *インスペクター] パネル* で、 *変換* コンポーネントに次の値を設定します。

    |   X 軸    | Y 軸 |   Z 軸    |
    |:-----:|:----------------------:|:-----:|
    | 0     | -1                     | 0     |


10. **球** を右クリックして選択します。 [ *インスペクター] パネル* で、 *変換* コンポーネントに次の値を設定します。

    |   X 軸    | Y 軸 |   Z 軸    |
    |:-----:|:----------------------:|:-----:|
    | 2     | 1                      | 2     |

11. **円柱** を左クリックして選択します。 [ *インスペクター] パネル* で、 *変換* コンポーネントに次の値を設定します。

    |   X 軸    | Y 軸 |   Z 軸    |
    |:-----:|:----------------------:|:-----:|
    | -2    | 1                      | 2     |

12. **キューブ** を左クリックして選択します。 [ *インスペクター] パネル* で、 *変換* コンポーネントに次の値を設定します。

    |        | 変換- *位置* |       |  \| |       | 変換- *回転* |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | **X** | **Y**                   | **Z** |  \| | **X** | **Y**                  | **Z** |
    | 0     | 1                       | 4     |  \| | 45    | 45                     | 0     | 

13. **新しいテキスト** オブジェクトを左クリックして選択します。 [ *インスペクター] パネル* で、 *変換* コンポーネントに次の値を設定します。

    |       | 変換- *位置* |       |  \| |       | 変換- *スケール* |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | **X** | **Y**                  | **Z** |  \| | **X** | **Y**               | **Z** |
    | -2    | 6                      | 9     |  \| | 0.1   | 0.1                 | 0.1   | 

14. **テキストメッシュ** コンポーネントの **フォントサイズ** を **50** に変更します。
15. **テキストメッシュ** オブジェクトの *名前* を **ディクテーションテキスト** に変更します。

    ![3D テキストオブジェクトの作成](images/AzureLabs-Lab3-38.png)
 
16. 階層パネルの構造は次のようになります。

    ![シーンビューのテキストメッシュ](images/AzureLabs-Lab3-38b.png)


17. 最終的なシーンは次の図のようになります。

    ![シーンビュー。](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a>Chapter 5 – MicrophoneManager クラスを作成する

最初に作成するスクリプトは、 *MicrophoneManager* クラスです。 次に、 *Luismanager* と *ビヘイビアー* クラスを作成します (これら *のクラスを* すべて自由に作成しておきますが、各章で説明します)。

*MicrophoneManager* クラスは次の役割を担います。

-   ヘッドセットまたはコンピューターに接続されている記録デバイスを検出しています (どちらか一方が既定値です)。
-   オーディオ (音声) をキャプチャし、ディクテーションを使用して文字列として格納します。
-   音声が一時停止したら、そのディクテーションを *Luismanager* クラスに送信します。 

このクラスを作成するには: 

1.  [ *プロジェクト] パネル* 内を右クリックし、 **> フォルダーを作成** します。 フォルダー **スクリプト** を呼び出します。 

    ![Scripts フォルダーを作成します。](images/AzureLabs-Lab3-40.png)
 
2.  **Scripts** フォルダーが作成されたら、それをダブルクリックして開きます。 次に、そのフォルダー内で右クリックし、[ **> C# スクリプトの作成**] をクリックします。 スクリプトに *MicrophoneManager* という名前を指定します。 

3.  *MicrophoneManager* をダブルクリックして、 *Visual Studio* で開きます。
4.  ファイルの先頭に次の名前空間を追加します。

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  次に、 *MicrophoneManager* クラス内に次の変数を追加します。

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  起動可能な *()* メソッドと *Start ()* メソッドのコードを追加する必要があります。 これらは、クラスの初期化時に呼び出されます。

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  ここで、音声キャプチャを開始および停止するためにアプリが使用するメソッドが必要であり、間もなくビルドされる *Luismanager* クラスに渡します。 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  音声が一時停止したときに呼び出される *ディクテーションハンドラー* を追加します。 このメソッドは、ディクテーションテキストを *Luismanager* クラスに渡します。

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > *Update ()* メソッドは、このクラスでは使用されないため、削除します。

9.  *Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。

    > [!NOTE]
    > この時点で、 *Unity エディターのコンソールパネル* にエラーが表示されます。 これは、次の章で作成する *Luismanager* クラスをコードが参照するためです。

## <a name="chapter-6--create-the-luismanager-class"></a>Chapter 6 – LUISManager クラスを作成する

ここで、 *Luismanager* クラスを作成します。これにより、Azure LUIS サービスが呼び出されます。 

このクラスの目的は、 *MicrophoneManager* クラスからディクテーションテキストを受け取り、それを分析対象の *Azure Language Understanding API* に送信することです。

このクラスは、 *JSON* 応答を逆シリアル化し、 *ビヘイビアー* クラスの適切なメソッドを呼び出してアクションをトリガーします。

このクラスを作成するには: 

1.  [ **Scripts** ] フォルダーをダブルクリックして開きます。 
2.  **Scripts** フォルダー内を右クリックし、[ **Create > C# Script**] をクリックします。 スクリプトに「 *Luismanager*」という名前を指定します。 
3.  スクリプトをダブルクリックして、Visual Studio で開きます。
4.  ファイルの先頭に次の名前空間を追加します。

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  最初に、 *Luismanager* クラス **内** に3つのクラス ( *Start ()* メソッドの上にある同じスクリプトファイル内) を作成し、Azure からの逆シリアル化された JSON 応答を表します。

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  次に、 *Luismanager* クラス内に次の変数を追加します。
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  LUIS エンドポイントを現在の場所 (LUIS ポータルから取得) に配置してください。

8.  起動前 *()* メソッドのコードを追加する必要があります。 このメソッドは、クラスの初期化時に呼び出されます。

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  ここで、 *MicrophoneManager* クラスから受け取ったディクテーションを *LUIS* に送信し、応答を受信して逆シリアル化するために、このアプリケーションが使用するメソッドが必要です。 
10. インテントの値と関連エンティティが決定されると、 *ビヘイビアー* クラスのインスタンスに渡され、目的のアクションがトリガーされます。

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. 結果として得られた *AnalysedQuery* を読み取ってエンティティを決定する、analytics *Ser onseelements ()* という名前の新しいメソッドを作成します。 これらのエンティティが決定されると、 *ビヘイビアー* クラスのインスタンスに渡され、アクションで使用されます。

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognized intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > *Start ()* および *Update ()* メソッドは、このクラスでは使用されないため、削除します。

12. *Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。

> [!NOTE]
> この時点で、 *Unity エディターのコンソールパネル* にいくつかのエラーが表示されます。 これは、次の章で作成する *ビヘイビアー* クラスをコードが参照するためです。

## <a name="chapter-7--create-the-behaviours-class"></a>第7章–ビヘイビアークラスの作成

*ビヘイビアー* クラスは、 *luismanager* クラスによって提供されるエンティティを使用してアクションをトリガーします。

このクラスを作成するには: 

1.  [ **Scripts** ] フォルダーをダブルクリックして開きます。 
2.  **Scripts** フォルダー内を右クリックし、[ **Create > C# Script**] をクリックします。 スクリプトに *ビヘイビアー* という名前を指定します。 
3.  スクリプトをダブルクリックして、 *Visual Studio* で開きます。
4.  次に、 *ビヘイビアー* クラス内に次の変数を追加します。

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  起動前 *()* メソッドのコードを追加します。 このメソッドは、クラスの初期化時に呼び出されます。

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  次のメソッドは、クエリの対象となるオブジェクトを判別するために、 *Luismanager* クラス (前に作成したもの) によって呼び出され、適切なアクションをトリガーします。

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  *Findtarget ()* メソッドを追加して、現在のインテントの対象となるのはどの *オブジェクト* かを判別します。 エンティティに明示的なターゲットが定義されていない場合、このメソッドは、ターゲット *オブジェクト* を既定の "gazed" に設定します。

    ```csharp
        /// <summary>
        /// Determines which object reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > *Start ()* および *Update ()* メソッドは、このクラスでは使用されないため、削除します。

8.  *Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。

## <a name="chapter-8--create-the-gaze-class"></a>章8–宝石クラスを作成する

このアプリを完成させるために必要な最後のクラスは、 *宝石* クラスです。 このクラスは、ユーザーのビジュアルフォーカス内に現在存在する *オブジェクト* への参照を更新します。

このクラスを作成するには: 

1.  [ **Scripts** ] フォルダーをダブルクリックして開きます。 
2.  **Scripts** フォルダー内を右クリックし、[ **Create > C# Script**] をクリックします。 スクリプトに「」という名前を *指定します*。 
3.  スクリプトをダブルクリックして、 *Visual Studio* で開きます。
4.  このクラスの次のコードを挿入します。

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  *Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。

## <a name="chapter-9--completing-the-scene-setup"></a>第9章: シーンのセットアップの完了

1.  シーンのセットアップを完了するには、作成した各スクリプトを [スクリプト] フォルダーから、[*階層] パネル* の [**メインカメラ**] オブジェクトにドラッグします。
2.  **メインカメラ** を選択して [*インスペクター] パネル* を表示すると、アタッチした各スクリプトを確認できます。また、設定されていない各スクリプトにはパラメーターがあることがわかります。

    ![カメラ参照ターゲットを設定しています。](images/AzureLabs-Lab3-41.png)

3.  これらのパラメーターを適切に設定するには、次の手順に従います。

    1. *MicrophoneManager*:

        - [ *階層] パネル* で、[ **ディクテーションテキスト** ] オブジェクトを [ **ディクテーションテキスト** のパラメーター値] ボックスにドラッグします。

    2. *ビヘイビアー*、 *階層パネル* から:

        - **球体** オブジェクトを [*球* 参照ターゲット] ボックスにドラッグします。
        - **円柱** を [*シリンダー* 参照ターゲット] ボックスにドラッグします。
        - **キューブ** を [*キューブ* 参照ターゲット] ボックスにドラッグします。

    3. *宝石*:

        - " *宝石の最大距離* " を **300** に設定します (まだ存在していない場合)。 

4.  結果は次の図のようになります。

    ![カメラ参照ターゲットを表示し、現在設定されています。](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a>Chapter 10-Unity エディターでのテスト

シーンのセットアップが正しく実装されていることをテストします。

次のことを確認します。

-   すべてのスクリプトが **メインカメラ** オブジェクトにアタッチされます。 
-   *メインカメラインスペクターパネル* のすべてのフィールドが適切に割り当てられます。

1.  *Unity エディター* で [**再生**] ボタンをクリックします。 アプリは、接続されているイマーシブヘッドセット内で実行されている必要があります。

2.  次のように、いくつかの発話を試してみてください。

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > 既定のオーディオデバイスの変更について Unity コンソールにエラーが表示される場合は、シーンが想定どおりに機能しない可能性があります。 これは、mixed reality ポータルが、ヘッドセットを持つヘッドホン用の組み込みマイクを扱う方法に起因します。 このエラーが表示された場合は、単にシーンを停止してからもう一度開始するだけで、期待どおりに動作するはずです。

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a>第11章– UWP ソリューションのビルドとサイドロード

Unity エディターでアプリケーションが動作していることを確認したら、ビルドと配置を行うことができます。

ビルドするには:

1.  [ **ファイル > 保存**] をクリックして、現在のシーンを保存します。
2.  **ファイル > ビルド設定** にアクセスします。
3.  **Unity C# プロジェクト** と呼ばれるボックスを目盛りします (UWP プロジェクトの作成後にコードを表示してデバッグする場合に便利です)。
4.  [開いている **シーンの追加**] をクリックし、[ **ビルド**] をクリックします。

    ![ビルドの設定ウィンドウ](images/AzureLabs-Lab3-43.png)

4.  ソリューションをビルドするフォルダーを選択するように求められます。 

5.  *ビルド* フォルダーを作成し、そのフォルダー内で、適切な名前を指定して別のフォルダーを作成します。 
6.  [ **フォルダーの選択** ] をクリックして、その場所でビルドを開始します。
 
    ![ビルドフォルダーの作成 ](images/AzureLabs-Lab3-44.png)
     ![ ビルドフォルダーの選択](images/AzureLabs-Lab3-45.png)
 
7.  Unity のビルドが完了すると (時間がかかる場合があります)、ビルドの場所で **ファイルエクスプローラー** ウィンドウを開きます。

ローカルコンピューターに配置するには:

1.  *Visual Studio* で、[前の章](#chapter-10--test-in-the-unity-editor)で作成したソリューションファイルを開きます。
2.  **ソリューションプラットフォーム** で、[ **X86**,**ローカルコンピューター**] を選択します。
3.  **ソリューション構成** で、[**デバッグ**] を選択します。

    > Microsoft HoloLens の場合、これを *リモートコンピューター* に設定する方が簡単な場合があります。これにより、コンピューターにテザリングさされることはありません。 ただし、次の手順も実行する必要があります。
    > - HoloLens の **IP アドレス** を確認します。これは、 *[設定 > ネットワーク & インターネット > Wi-Fi > 詳細オプション]* にあります。IPv4 は、使用するアドレスです。 
    > - **開発者モード** が **オンに** なっていることを確認します。*開発者向けのセキュリティ > の更新プログラム & の > の設定* にあります。

    ![アプリをデプロイする](images/AzureLabs-Lab3-46.png)
 
4.  [ **ビルド] メニュー** の [ソリューションの **配置** ] をクリックして、アプリケーションをコンピューターにサイドロードします。
5.  アプリがインストール済みアプリの一覧に表示され、起動できる状態になります。
6.  アプリを起動すると、 _マイク_ へのアクセスを承認するように求められます。 *モーションコントローラー*、*音声入力*、または *キーボード* を使用して、 **[はい**] ボタンを押します。 

## <a name="chapter-12--improving-your-luis-service"></a>第12章: LUIS サービスの向上

>[!IMPORTANT] 
> この章は非常に重要であり、LUIS サービスの精度を向上させるために複数回繰り返す必要がある場合があります。これを完了していることを確認してください。

LUIS によって提供される理解レベルを向上させるには、新しい発話をキャプチャし、それらを使用して LUIS アプリを再トレーニングする必要があります。

たとえば、"増加" と "アップサイズ" を理解するためにトレーニング済みの LUIS を使用しているとしても、アプリで "拡大" のような単語を理解したいとは思いませんか。

アプリケーションを数回使用した後は、前述のすべてのものが LUIS によって収集され、LUIS ポータルで利用できるようになります。

1.  この [リンク](https://www.luis.ai/home)に従ってポータルアプリケーションにアクセスし、ログインします。
2.  MS 資格情報でログインしたら、 *アプリ名* をクリックします。
3.  ページの左側にある [ **Review endpoint 発話** ] ボタンをクリックします。

    ![発話の確認](images/AzureLabs-Lab3-47.png)
 
4.  混合した現実のアプリケーションによって LUIS に送信された発話の一覧が表示されます。

    ![発話の一覧](images/AzureLabs-Lab3-48.png)
 
強調表示されている *エンティティ* がいくつかわかります。 

強調表示された各単語の上にマウスポインターを置くと、各 (発話) を確認し、正しく認識されたエンティティ、どのエンティティが間違っているか、どのエンティティが不足しているかを判断できます。

上記の例では、"スピアー" という単語はターゲットとして強調表示されているため、誤って修正する必要があります。これを行うには、マウスで単語をポイントし、[ **ラベルの削除**] をクリックします。

![チェック発話の ](images/AzureLabs-Lab3-49.png)
 ![ ラベルイメージの削除](images/AzureLabs-Lab3-50.png)
 
5.  完全に間違った発話が見つかった場合は、画面の右側にある [ **削除** ] ボタンを使用して削除できます。

    ![間違った発話の削除](images/AzureLabs-Lab3-51.png)

6.  または、LUIS が (発話) を正しく解釈したと思われる場合は、[固定された **インテントに追加** ] ボタンを使用して、その理解を検証することができます。

    ![固定されたインテントに追加](images/AzureLabs-Lab3-52.png)

7.  表示されているすべての発話を並べ替えた後、ページを再度読み込んで、使用できるかどうかを確認します。
8.  このプロセスをできるだけ多く繰り返して、アプリケーションの理解を向上させることが非常に重要です。 

**お楽しみください!**

## <a name="your-finished-luis-integrated-application"></a>完成した LUIS 統合アプリケーション

これで、Azure Language Understanding インテリジェンスサービスを活用する mixed reality アプリを構築し、ユーザーが何をしているかを把握し、その情報を操作できるようになりました。

![ラボの結果](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a>ボーナス演習

### <a name="exercise-1"></a>演習1

このアプリケーションを使用しているときに、Floor オブジェクトを見つめ、その色を変更するように要求すると、そのようになります。 アプリケーションでフロアの色を変更できないようにする方法はありますか。

### <a name="exercise-2"></a>演習2

LUIS とアプリの機能を拡張して、シーンにオブジェクトの機能を追加してみてください。例として、ユーザーの指示に応じて、宝石ヒットポイントに新しいオブジェクトを作成し、既存のコマンドを使用して、それらのオブジェクトを現在のシーンオブジェクトと共に使用できるようにします。