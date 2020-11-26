---
title: Azure Cloud のチュートリアル - 4. Azure Spatial Anchors の統合
description: このコースでは、HoloLens 2 アプリケーション内で Azure Spatial Anchors を実装する方法を学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, Hololens 2, Azure Spatial Anchors, Azure クラウド サービス, Azure Custom Vision, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 5245f3522e7822c16ebc0d0113634f152f223086
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679341"
---
# <a name="4-integrating-azure-spatial-anchors"></a>4.Azure Spatial Anchors の統合

このチュートリアルでは、**Azure Spatial Anchors** を使用する方法を学習します。 **追跡対象のオブジェクト** の場所を Azure Spatial Anchor として格納します。 アンカーに対してクエリを実行すると、場所を指す矢印が表示されます。

## <a name="objectives"></a>目標

* Azure Spatial Anchors の基本を学習する。
* このプロジェクトで Azure Spatial Anchors を使用するシーンをセットアップする方法を学習する。
* 場所の格納とクエリを統合する方法を学習する。

## <a name="understanding-azure-spatial-anchors"></a>Azure Spatial Anchors について

 **Azure Spatial Anchors** は Azure Cloud Services ファミリーに含まれており、アンカーの場所を保存するために使用します。 保存されたアンカーの場所は、*アンカー ID* に基づいてクラウドから取得できます。 このアンカーの場所は、HoloLens、iOS、Android デバイスなどのマルチプラットフォーム デバイスで共有およびアクセスできます。

[Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/overview) の詳細をご確認ください。

## <a name="preparing-azure-spatial-anchors"></a>Azure Spatial Anchors の準備

開始する前に、Azure portal で空間アンカー リソースを作成する必要があります。
[空間アンカー リソース](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource)を作成する方法を学習します。

## <a name="preparing-the-scene"></a>シーンの準備

このセクションでは、シーンを構成して、必要な変更を行う方法を学習します。

[プロジェクト] ウィンドウで、 **[アセット] > [MRTK.Tutorials.AzureCloudServices] > [Prefabs]\(プレハブ\) > [マネージャー]** に移動します

![AnchorManager プレハブが選択されている Unity](images/mr-learning-azure/tutorial4-section1-step1-1.png)

**[マネージャー]** フォルダーで、プレハブ **[Anchor Manager]** をシーン階層にドラッグ アンド ドロップします。

階層内の **[Anchor Manager]** GameObject を選択すると、[インスペクター] セクションに **[Spatial Anchor Manager]** (Script) が表示されます。 アカウント ID とキー フィールドを検索し、前の段階で前提条件に作成した資格情報を追加します。

![新しく追加された AnchorManager プレハブがまだ選択されている Unity](images/mr-learning-azure/tutorial4-section1-step2-1.png)

ここで、シーン階層で **[Scene Controller]\(シーン コントローラー\)** オブジェクトを見つけて選択します。 **[Scene Controller]\(シーン コントローラー\)** インスペクターが表示されます。

![SceneController スクリプト コンポーネントが構成された Unity](images/mr-learning-azure/tutorial4-section1-step3-1.png)

**[Scene Controller]\(シーン コントローラー\)** コンポーネントの **[Anchor Manager]** フィールドが空であることを確認し、 **[Anchor Manager]** をシーンの階層からそのフィールドにドラッグ アンド ドロップしてシーンを保存します。

## <a name="build-and-deploy-the-app-to-your-hololens-2"></a>アプリをビルドして HoloLens 2 にデプロイする

Azure Spatial Anchors は Unity では実行できないため、Azure Spatial Anchors の機能をテストするには、プロジェクトをお使いのデバイスにデプロイする必要があります。

> [!TIP]
> HoloLens 2 に Unity プロジェクトをビルドしてデプロイする方法については、[HoloLens 2 にアプリをビルドする](mr-learning-base-02.md#building-your-application-to-your-hololens-2)手順に関するページを参照してください。

## <a name="run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>HoloLens 2 でアプリを実行し、アプリ内の指示に従う

### <a name="create-an-anchor-to-store-a-location"></a>場所を格納するアンカーを作成する

このセクションでは、オブジェクトの場所を保存する方法を確認します。

アプリケーションを実行し、エクスペリエンスのメイン メニューで **[Set Object]\(オブジェクトの設定\)** をクリックします。

保存するオブジェクトの **名前** を指定し、 **[Set Object]\(オブジェクトの設定\)** をクリックして続行します。 オブジェクトに関する詳細情報を追加するには、**画像** を選択し、オブジェクトについて説明します。

場所を保存するには **[場所の保存]** をクリックします

表示されている **アンカー ポインター** を移動して、保存する場所に配置することができます。 その後、確認のポップアップが表示されます。 場所を確認して保存する場合は、 **[はい]** をクリックします。そうでない場合は、 **[いいえ]** をクリックして場所をもう一度選択することによって、場所を変更できます。

**[はい]** をクリックして場所を確認すると、場所とアンカー ID が Azure クラウド ストレージに保存されます。 保存すると、オブジェクトの名前が指定された **オブジェクト タグ** がアンカーに表示されます。

これで、オブジェクトの場所が正常に保存されました。

### <a name="query-for-finding-an-anchor-location"></a>アンカーの場所を検索するためのクエリ

アンカーの場所が正常に保存されたら、メイン メニューで **[オブジェクトの検索]** を選択してアンカーの場所を検索できるようになります。

**[オブジェクトの検索]** をクリックすると、新しいウィンドウが表示されます。そこで、検索するオブジェクトの名前を指定する必要があります。

オブジェクトの名前を入力し、 **[オブジェクトの検索]** をクリックします。 オブジェクトが既に保存されていて、データベースに存在する場合は、以前に保存したオブジェクトのすべての詳細を含むオブジェクト カードが表示されます。

これで、 **[Show Location]\(場所の表示\)** をクリックしてオブジェクトを検索できるようになります。 **[Show Location]\(場所の表示\)** をクリックすると、システムによってクラウド ストレージからオブジェクト アドレスに対してクエリが実行されます。

場所を正常に取得できたら、**矢印** に従ってオブジェクトの場所に移動します。 オブジェクトの場所が見つかるまで、矢印マークに従います。

オブジェクトが見つかったら、オブジェクト名が上部に表示され、矢印マークが消えます。これで、**オブジェクト タグ** をクリックしてオブジェクトの詳細を確認できます。

## <a name="congratulations"></a>結論

このチュートリアルでは、Azure Spatial Anchors を使用して、Hololense 2 でオブジェクトの場所を保存および取得する方法を学習しました。

最後のチュートリアルでは、**Azure Bot Service** を使用して、アプリケーションの新しい相互作用方式として自然言語を追加する方法を学習します。

> [!div class="nextstepaction"]
> [次のチュートリアル: 5.Azure Bot Service と LUIS との統合](mr-learning-azure-05.md)
