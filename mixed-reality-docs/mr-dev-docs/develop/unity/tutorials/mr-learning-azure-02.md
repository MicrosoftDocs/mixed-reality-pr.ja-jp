---
title: Azure Cloud チュートリアル - 2. Azure Storage の統合
description: このコースを完了すると、Azure Table Storage と Azure Blob Storage を HoloLens 2 アプリケーション内に実装する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, HoloLens, HoloLens 2, Azure Storage
ms.localizationpriority: high
ms.openlocfilehash: 64e4aaadf13c03272a4fc9c552a7e4b31e82fdbb
ms.sourcegitcommit: 520c69eb761ad6083b36f448bbcfab89e343e40d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2020
ms.locfileid: "94549105"
---
# <a name="2-integrating-azure-storage"></a>2.Azure Storage の統合

このチュートリアルでは、エンティティ データを Azure Table Storage に、そしてサムネイル画像を Azure Blob Storage に保存する方法について学習します。 この機能を使用すると、ID、名前、サムネイル画像などのデータを含む "*追跡オブジェクト*" を、セッションおよびデバイスを介してクラウドとの間で保存および取得することができます。

## <a name="objectives"></a>目標

* Azure Storage の基本について学習する
* Table Storage に対してデータの格納、変更、および取得を行う方法を学習する
* Blob Storage に対して画像の格納および削除を行う方法を学習する

## <a name="understanding-azure-storage"></a>Azure Storage について

**Azure Storage** は、クラウドでの Microsoft のストレージ ソリューションであり、多くのシナリオと要件に対応できます。 非常に大規模なスケーリングが可能で、開発者が簡単に使用できます。 すべてのサービスを、**Azure ストレージ アカウント** の包括的なサービスとして利用することができます。 このユース ケースでは、*Table Storage* と *Blob Storage* を使用します。

詳細については、[Azure ストレージ サービス](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-overview)に関するページを参照してください。

### <a name="azure-table-storage"></a>Azure Table Storage

このサービスを使用すると、NoSQL 形式でデータを格納することができます。このプロジェクトでは、それを使用して、名前、説明、空間アンカー ID など、"*追跡オブジェクト*" に関する情報を格納します。

デモ アプリケーションのコンテキストでは、2 つのテーブルが必要です。1 つは、プロジェクトに関する情報とトレーニング済みモデルの状態に関する情報 (詳細についてはチュートリアル「[Azure Custom Vision の統合](mr-learning-azure-03.md)」を参照) を格納するテーブルであり、もう 1 つは "*追跡オブジェクト*" に関する情報を格納するものです。

詳細については、[Azure Table Storage](https://docs.microsoft.com/azure/storage/tables/table-storage-overview) に関するページを参照してください。

### <a name="azure-blob-storage"></a>Azure Blob Storage

このサービスでは、大規模なバイナリ ファイルを格納することができます。"*追跡オブジェクト*" について撮影した写真をサムネイルとして格納するために、これを使用します。
デモ アプリケーションでは、画像を格納するために、BLOB コンテナーが 1 つ必要です。

詳細については、[Azure Blob Storage](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction) に関するページを参照してください。

## <a name="preparing-azure-storage"></a>Azure Storage の準備

Azure ストレージ サービスを利用するには、Azure ストレージ アカウントが必要です。 ストレージ アカウントを作成するには、[ストレージ アカウントの作成](https://docs.microsoft.com/azure/storage/common/storage-account-create?tabs=azure-portal)に関するページを参照してください。 ストレージ アカウントの詳細については、[Azure ストレージ アカウントの概要](https://docs.microsoft.com/azure/storage/common/storage-account-overview)に関するページを参照してください。

ストレージ アカウントを作成したら、このレッスンの次のセクションで必要となる接続文字列を **Azure portal** から取得できます。

### <a name="optional-azure-storage-explorer"></a>オプションの Azure Storage Explorer

アプリケーション内の UI からデータに関するすべての変更を表示および確認することができますが、[Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/) をインストールすることをお勧めします。 このツールを使用すると、Azure Storage 内のデータを視覚的に確認できるため、デバッグを行うときや学習するときに大いに役立ちます。

> [!TIP]
> Unity エディター内からテストする場合は、次のローカル エミュレーターを使用できます。
> * Windows 10 では、[Azure ストレージ エミュレーター](https://docs.microsoft.com/azure/storage/common/storage-use-emulator)を使用できます。
> * MacOS、Linux では、Docker 用の [Azurite Docker Image](https://hub.docker.com/_/microsoft-azure-storage-azurite) を使用できます。

## <a name="preparing-the-scene"></a>シーンの準備

[階層] ウィンドウで、**DataManager** オブジェクトを見つけて選択します。

![DataManager スクリプト コンポーネント構成フィールドがインスペクターに表示された Unity](images/mr-learning-azure/tutorial2-section4-step1-1.png)

[インスペクター] ウィンドウから、**DataManager (script)** コンポーネントは **Azure Storage** 関連のすべての設定が保持される場所であることがわかります。 関連する設定はすべて、既に設定されているので、"*接続文字列*" フィールドを、Azure portal から取得できるものに置き換えるだけで済みます。 ローカルの Azure ストレージ エミュレーター ソリューションを使用している場合は、既に指定されている "*接続文字列*" を保持できます。

**DataManager (スクリプト)** は、**Table Storage** および **Blob Storage** とやりとりすることが役割であり、UI コンポーネント上の他のコントローラー スクリプトによって利用されます。

## <a name="writing-and-reading-data-from-azure-table-storage"></a>Azure Table Storage に対するデータの書き込みと読み取り

すべての準備が整ったら、"*追跡オブジェクト*" を作成します。

ご利用の HoloLens 上でアプリケーションを開き、 **[オブジェクトの設定]** をクリックします。*EnterObjectName* オブジェクトが階層内でどのようにアクティブになるかがわかります。 このメニューで、"*検索バー*" をクリックし、"*追跡オブジェクト*" に付ける名前を入力します。 名前を指定したら、 **[オブジェクトの設定]** ボタンをクリックします。 これにより、Azure Table Storage に "*追跡オブジェクト*" が作成され、 **[オブジェクト カード]** が表示されるようになります。

この **[オブジェクト カード]** は、"*追跡オブジェクト*" の UI 表現であり、このチュートリアル シリーズでは重要な役割を何度も果たします。

次に、説明 "*テキスト ボックス*" をクリックし、「Car」と入力します。その後、 **[保存]** をクリックして、変更を保存します。 アプリケーションを停止してから、再実行します。

今度は、 **[オブジェクトの検索]** をクリックし、以前 "*追跡オブジェクト*" を作成するときに使用した名前を "*検索バー*" に入力します。 すべてのデータを含む **[オブジェクト カード]** が **Azure Table Storage** から取得されていることがわかります。

**[オブジェクト カード]** を閉じて、新しい "*追跡オブジェクト*" を作成し、そのデータを編集することも自由にできます。

> [!TIP]
> [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/) をインストール済みである場合、*objects* テーブルを参照すると、"*追跡対象*" オブジェクトが作成されていることがわかります。

## <a name="uploading-and-download-image-from-azure-blob-storage"></a>Azure Blob Storage への画像のアップロードおよびダウンロード

このセクションでは、Azure Blob Storage を使用して、"*追跡オブジェクト*" のサムネイルとして使用される画像をアップロードおよびダウンロードします。

> [!NOTE]
> このチュートリアルでは、アプリケーションによって、写真を撮影して、画像を BLOB ストレージにアップロードします。 それを Unity エディターからローカルに実行している場合は、Web カメラがコンピューターに接続されていることを確認してください。

ご利用の HoloLens 上でアプリケーションを開き、 **[Set Object]\(オブジェクトの設定\)** をクリックし、"*検索バー*" に「Car」という名前を入力します。 これで、 **[オブジェクト カード]** が表示されるので、 **[カメラ]** ボタンをクリックすると、AirTap を実行して写真を撮るように指示されます。 写真を撮影すると、アクティブなアップロードについて通知するメッセージが表示され、しばらくすると、プレースホルダーが以前にあった場所に、その画像が表示されます。

次に、アプリケーションを再実行し、"*追跡オブジェクト*" を検索します。前にアップロードした画像がサムネイルとして表示されます。

## <a name="deleting-image-from-azure-blob-storage"></a>Azure Blob Storage から画像を削除する

前のセクションでは、Azure Blob Storage に新しい画像をアップロードしました。このセクションでは、"*追跡オブジェクト*" のサムネイル画像を削除します。

ご利用の HoloLens 上でアプリケーションを開き、 **[Set Object]\(オブジェクトの設定\)** をクリックし、"*検索バー*" に「Car」という名前を入力します。 これで、サムネイル画像を伴って **[オブジェクト カード]** が表示されるので、 **[削除]** ボタンをクリックします。 サムネイル画像がプレースホルダー画像に置き換えられていることがわかります。

次に、アプリケーションを再実行して、前に削除したサムネイルの "*追跡オブジェクト*" を検索するとプレースホルダー画像のみが表示されます。

## <a name="congratulations"></a>結論

このチュートリアルでは、Azure ストレージ サービスを使用して非構造化データ (ここでは、クラウド上の **HoloLens 2** デモ アプリケーション用の "**追跡オブジェクト**" や、サムネイル画像の形式のバイナリなど) を保持する方法について学習しました。

次のチュートリアルでは、Azure Custom Vision を使用して、"*追跡オブジェクト*" に関連付けられている画像を検出する方法を学習します。

> [!div class="nextstepaction"]
> [次のチュートリアル: 3. Azure Custom Vision の統合](mr-learning-azure-03.md)
