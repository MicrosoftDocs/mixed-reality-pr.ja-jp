---
title: Azure Spatial Anchors の共有エクスペリエンスへの統合
description: このコースを完了すると、Azure Spatial Anchors を使用して共有マルチユーザー HoloLens 2 アプリケーション内でオブジェクトを固定する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, マルチユーザー機能, Photon, MRTK, Mixed Reality Toolkit, UWP, Azure 空間アンカー
ms.localizationpriority: high
ms.openlocfilehash: 4eb7470487a584ef820be82f651ed9bd16392395
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590224"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a>5.Azure Spatial Anchors の共有エクスペリエンスへの統合

このチュートリアルでは、Azure Spatial Anchors (ASA) を共有エクスペリエンスに統合する方法を学習します。 ASA により複数のデバイスが現実の世界への共通の参照を持てるようになり、ユーザーは互いの姿をその現実の物理的な位置に見たり、共有エクスペリエンスを同じ場所で見たりすることができるようになります。

## <a name="objectives"></a>目標

* ASA を共有エクスペリエンスに統合し、複数デバイスで位置合わせする
* ASA がローカル共有エクスペリエンスのコンテキストでどのように機能するかについての基本を学ぶ

## <a name="preparing-the-scene"></a>シーンの準備

[Hierarchy]\(ヒエラルキー\) ウィンドウで **SharedPlayground** オブジェクトを展開し、**TableAnchor** オブジェクトを展開してその子オブジェクトを公開します。

![SharedPlayground と TableAnchor オブジェクトが展開された Unity](images/mr-learning-sharing/sharing-05-section1-step1-1.png)

[Project]\(プロジェクト\) ウィンドウで **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.MultiUserCapabilities]**  >  **[Prefabs]\(プレハブ\)** フォルダーの順に移動して、**Buttons** プレハブを **TableAnchor** 子オブジェクト上にドラッグし、TableAnchor オブジェクトの子としてシーンに追加します。

![新しく追加された Buttons プレハブが選択されている Unity](images/mr-learning-sharing/sharing-05-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a>シーンを操作するためのボタンの構成

このセクションでは一連のボタン イベントを構成して、Azure Spatial Anchors を使用して共有エクスペリエンスでの空間的な位置合わせを実現する方法の基本を示します。

[Hierarchy]\(ヒエラルキー\) ウィンドウで **Button** オブジェクトを展開し、**StartAzureSession** という名前の最初の子ボタン オブジェクトを選択します。

![StartAzureSession ボタン オブジェクトが選択されている Unity](images/mr-learning-sharing/sharing-05-section2-step1-1.png)

[Inspector]\(インスペクター\) ウィンドウで **Interactable (Script)** コンポーネントを探し、**OnClick ()** イベントを次のように構成します。

* **[None (Object)]\(なし (オブジェクト))\** フィールドに、**TableAnchor** オブジェクトを割り当てる
* **[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  > **StartAzureSession ()** 関数の順に選択する

![StartAzureSession ボタンの OnClick イベントが構成された Unity](images/mr-learning-sharing/sharing-05-section2-step1-2.png)

[Hierarchy]\(ヒエラルキー\) ウィンドウで **CreateAzureAnchor** という名前の 2 番目の子ボタン オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで **Interactable (Script)** コンポーネントを探して **OnClick ()** イベントを次のように構成します。

* **[None (Object)]\(なし (オブジェクト))\** フィールドに、**TableAnchor** オブジェクトを割り当てる
* **[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  > **CreateAzureAnchor()** 関数の順に選択する
* 表示される新しい **"None (Game Object)"(なし (ゲーム オブジェクト))** フィールドに、**TableAnchor** オブジェクトを割り当てる

![CreateAzureAnchor ボタンの OnClick イベントが構成された Unity](images/mr-learning-sharing/sharing-05-section2-step1-3.png)

[Hierarchy]\(ヒエラルキー\) ウィンドウで **ShareAzureAnchor** という名前の 3 番目の子ボタン オブジェクトを選択して、[Inspector]\(インスペクター\) ウィンドウで **Interactable (Script)** コンポーネントを探して **OnClick ()** イベントを次のように構成します。

* **[None (Object)]\(なし (オブジェクト))\** フィールドに、**TableAnchor** オブジェクトを割り当てる
* **[No Function]** (関数なし) ドロップダウンから、 **[SharingModuleScript]**  > **ShareAzureAnchor()** 関数の順に選択する

![ShareAzureAnchor ボタンの OnClick イベントが構成された Unity](images/mr-learning-sharing/sharing-05-section2-step1-4.png)

[Hierarchy]\(階層\) ウィンドウで **GetAzureAnchor** という名前の 4 番目の子ボタン オブジェクトを選択して、[Inspector]\(インスペクター\) ウィンドウで **Interactable (Script)** コンポーネントを探して **OnClick ()** イベントを次のように構成します。

* **[None (Object)]\(なし (オブジェクト))\** フィールドに、**TableAnchor** オブジェクトを割り当てる
* **[No Function]** (関数なし) ドロップダウンから、 **[SharingModuleScript]**  > **GetAzureAnchor()** 関数の順に選択する

![GetAzureAnchor ボタンの OnClick イベントが構成された Unity](images/mr-learning-sharing/sharing-05-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>シーンを Azure リソースに接続する

[Hierarchy]\(ヒエラルキー\) ウィンドウで **SharedPlayground** オブジェクトを展開し、**TableAnchor** オブジェクトを選択します。

[Inspector]\(インスペクター\) ウィンドウで **Spatial Anchor Manager (Script)** コンポーネントを探し、このチュートリアル シリーズの「[前提条件](mr-learning-sharing-01.md#prerequisites)」の部分で作成した Azure Spatial Anchors アカウントからの資格情報を使用して、 **[Credentials]\(資格情報\)** セクションを構成します。

* **"Spatial Anchors Account ID"(Spatial Anchors アカウント ID)** フィールドに、Azure Spatial Anchors アカウントからの **アカウント ID** を貼り付ける
* **"Spatial Anchors Account Key"(Spatial Anchors アカウント キー)** フィールドに、Azure Spatial Anchors アカウントからのプライマリまたはセカンダリ **アクセス キー** を貼り付ける

![Spatial Anchor Manager が構成された Unity](images/mr-learning-sharing/sharing-05-section3-step1-1.png)

> [!TIP]
> シーン内で空間アンカー アカウント ID およびキーを設定するのでなく、プロジェクト全体に対してそれを設定することもできます。ASA を使用して複数のシーンを用意する場合は、これが有利です。 それを行うには、[Project]\(プロジェクト\) ウィンドウで、[Assets]\(アセット\) > [AzureSpatialAnchors.SDK] > [Resources]\(リソース\) > **[SpatialAnchorConfig]** アセットの順に移動し、次に [Inspector]\(インスペクター\) ウィンドウで値を設定します。

[Hierarchy]\(階層\) ウィンドウで、 **[TableAnchor]** オブジェクトを選択してから、[Inspector]\(インスペクター\) ウィンドウで **Anchor Module (Script)** コンポーネントを探し、それを次のように構成します。

* **[Public Sharing Pin]\(パブリック共有ピン\)** フィールドで、いくつかの数字を変更します。これにより、ピンが自分のプロジェクトに固有のものとなります。

![Anchor Module Script が構成された Unity](images/mr-learning-sharing/sharing-05-section3-step1-2.png)

**TableAnchor** オブジェクトを選択したまま、[Inspector]\(インスペクター\) ウィンドウですべてのスクリプト コンポーネントが **有効** になっていることを確認します。

* **Spatial Anchor Manager (Script)** コンポーネントの隣にあるチェックボックスをオンにして有効にする
* **Anchor Module Script (Script)** コンポーネントの隣にあるチェックボックスをオンにして有効にする
* **Sharing Module Script (Script)** コンポーネントの隣にあるチェックボックスをオンにして有効にする

![TableAnchor スクリプト コンポーネントが有効にされた Unity](images/mr-learning-sharing/sharing-05-section3-step1-3.png)

## <a name="trying-the-experience-with-spatial-alignment"></a>空間的な位置合わせのエクスペリエンスを試す

> [!NOTE]
> Azure Spatial Anchors を Unity で実行することはできません。 そのため、Azure Spatial Anchors の機能をテストするには、最低 2 台のデバイスにプロジェクトを配置する必要があります。

Unity プロジェクトをビルドして 2 台のデバイスに配置すると、Azure Anchor ID を共有してデバイス間で空間的な位置合わせを実現できます。 これをテストするには、次の手順を実行します。

1. デバイス 1 の場合: **アプリを開始する** (Rover エクスプローラーのインスタンスが作成され、テーブルに配置されます)
2. デバイス 2 の場合: **アプリを開始する** (両方のユーザーが Rover エクスプローラーのあるテーブルを見ることができますが、テーブルは同じ場所には表示されず、ユーザー アバターはユーザーが実際にいるところに表示されません)
3. デバイス 1 の場合: **[Start Azure Session]\(Azure セッションの開始\)** ボタンを押す
4. デバイス 1 の場合: **[Create Azure Anchor]\(Azure Anchor の作成\)** ボタンを押す (TableAnchor オブジェクトの場所にアンカーが作成され、アンカーの情報が Azure リソースに保存されます)。
5. デバイス 1 の場合: **[Share Azure Anchor]\(Azure Anchor の共有\)** ボタンを押す (他のユーザーとアンカー ID がリアルタイムで共有されます)
6. デバイス 2 の場合: **[Start Azure Session]\(Azure セッションの開始\)** ボタンを押す
7. デバイス 2 の場合: **[Get Azure Anchor]\(Azure Anchor の取得\)** ボタンを押す (Azure リソースに接続して共有アンカー ID のアンカー情報が取得され、TableAnchor オブジェクトはデバイス 1 でアンカーを作成した場所に移動します)

> [!TIP]
> 2 台の HoloLens デバイスへのアクセス権がない場合は、[モバイル デバイス用の Azure Spatial Anchors のビルド](mr-learning-asa-05.md)に関するページに従って、ご利用のモバイル デバイスにプロジェクトを配置することができます。

## <a name="congratulations"></a>結論

このチュートリアルでは、Azure の強力な Spatial Anchors を統合して、複数のデバイスを共有エクスペリエンスの中に配置する方法を学習しました。

これでこのチュートリアル シリーズは終了となります。Photon アカウントを設定し、PUN アプリを作成し、PUN を Unity プロジェクトに統合し、ユーザー アバターと共有オブジェクトを構成し、最後に Azure Spatial Anchors を使用して複数の参加者を配置する方法を学習しました。
