---
title: Azure Spatial Anchors チュートリアル - 3. Azure Spatial Anchors の保存、取得、および共有
description: このコースを完了すると Mixed Reality アプリケーション内に Azure Spatial Anchors を実装する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: edbbfa6bb4027e6d0d0d37a46575eafdb1d6e631
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91700330"
---
# <a name="3-saving-retrieving-and-sharing-azure-spatial-anchors"></a>3.Azure Spatial Anchors の保存、取得、および共有

このチュートリアルでは、HoloLens 2 のストレージにアンカー ID を保存することにより、複数のアプリ セッションにわたって Azure Spatial Anchors を保存する方法について学習します。 また、このアンカー ID を他のデバイスと共有して、複数デバイスのアンカーの位置合わせ行う方法についても学習します。

## <a name="objectives"></a>目標

* 複数のアプリ セッション間で空間的な位置合わせを実現する方法を学習する。
* 複数のデバイス間で空間的な位置合わせを実現する方法を学習する。

## <a name="preparing-the-scene"></a>シーンの準備

[階層] ウィンドウで、 **[ButtonParent]** オブジェクトを展開します。 **最後の 4 つの子ボタン** のオブジェクトを選択します。 [インスペクター] ウィンドウで、名前フィールドの横にあるチェックボックスを **オンにして** 、すべてのオブジェクトをアクティブにします。

![mr-learning-asa](images/mr-learning-asa/asa-03-section1-step1-1.png)

[階層] ウィンドウで、 **[ButtonParent]** オブジェクトを選択します。 次に、[インスペクター] ウィンドウで **[GridObjectCollection]** コンポーネントを見つけ、 **[Update Collection]\(コレクションの更新\)** ボタンをクリックして、すべての **[ButtonParent]** オブジェクトの子オブジェクトの位置を更新します。

![mr-learning-asa](images/mr-learning-asa/asa-03-section1-step1-2.png)

## <a name="persisting-azure-spatial-anchors-between-app-sessions"></a>アプリ セッション間での Azure Spatial Anchors の永続化

このセクションでは、Azure Anchor ID を HoloLens のローカル ディスクに保存したり、そこから取得したりする方法について学習します。 これにより、異なるアプリ セッション間で同じアンカー ID の Azure に対してクエリを実行できます。 固定されたホログラムを前のアプリ セッションと同じ場所に配置できるようになります。

[階層] ウィンドウで **[ButtonParent]** オブジェクトを展開し、 **SaveAzureAnchorIdToDisk** と **GetAzureAnchorIdFromDisk** という名前の 2 つのボタンを探します。

![mr-learning-asa](images/mr-learning-asa/asa-03-section2-step1-1.png)

前のチュートリアルの [シーンを操作するためのボタンの構成](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene)と同じ手順に従い、 **[Interactable (Script)]** コンポーネントを次の 2 つのボタンそれぞれに対して構成します。

* **[SaveAzureAnchorIdToDisk]** ボタン オブジェクトの場合、[AnchorModuleScript] を **[SaveAzureAnchorIdToDisk ()]** 関数に割り当てます。
* **[GetAzureAnchorIdFromDisk]** ボタン オブジェクトの場合、[AnchorModuleScript] を **[GetAzureAnchorIdFromDisk ()]** 関数に割り当てます。

更新されたアプリを HoloLens にビルドすると、Azure Anchor ID を保存することで、アプリ セッション間で Azure Spatial Anchors を永続化できるようになります。 これをテストするには、次の手順を実行します。

1. Rover Explorer を目的の場所に移動します
2. Azure セッションを開始します
3. Azure Anchor を作成します (Rover Explorer の場所にアンカーを作成します)
4. Azure Anchor ID をディスクに保存します
5. アプリを再起動します
6. ディスクから Azure Anchor を取得します (保存したアンカー ID を読み込みます)
7. Azure セッションを開始します
8. Azure Anchor を見つけます (手順 3 の場所に Rover Explorer を配置します)

> [!NOTE]
> アプリを完全に再起動するには、イマーシブ アプリ ビューを終了した後、[スタート] メニューからこれを再起動する前に、Mixed Reality ホームのアプリ ウィンドウを閉じる必要があります。 詳細については、「[HoloLens でアプリを使用する](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens)」のドキュメントを参照してください。

## <a name="sharing-azure-spatial-anchors-between-devices"></a>デバイス間での Azure Spatial Anchors の共有

このセクションでは、複数のデバイス間で Azure Anchor ID を共有する方法について学習します。 これにより、複数のデバイスが同じアンカー ID を Azure に対してクエリできるようになり、固定されたホログラムを空間的に位置合わせできるようになります。 空間的な位置合わせ、つまり複数のデバイス間で同じ物理的な場所に同じホログラムを表示できることは、HoloLens 2 のローカル共有エクスペリエンスにとって重要です。

Azure Anchor ID をデバイス間で転送するには、[マルチユーザー機能のチュートリアル](mr-learning-sharing-02.md) シリーズで説明されている方法など、さまざまな方法があります。 この例では、デバイス間でアンカー ID をアップロードおよびダウンロードする単純な Web サービスを使用します。

[階層] ウィンドウで、 **[ButtonParent]** オブジェクトを展開します。   **ShareAzureAnchorIdToNetwork** と、 **GetAzureAnchorIdFromNetwork** という名前の 2 つのボタンを見つけます。

![mr-learning-asa](images/mr-learning-asa/asa-03-section3-step1-1.png)

前のチュートリアルの [シーンを操作するためのボタンの構成](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene)と同じ手順に従い、 **[Interactable (Script)]** コンポーネントを次の 2 つのボタンそれぞれに対して構成します。

* **[ShareAzureAnchorIdToNetwork]** オブジェクトの場合は、[AnchorModuleScript] > **[ShareAzureAnchorIdToNetwork ()]** 関数を割り当てます。
* **[GetAzureAnchorIdFromNetwork]** オブジェクトの場合は、[AnchorModuleScript] > **[GetAzureAnchorIdFromNetwork ()]** 関数を割り当てます。

更新されたアプリを 2 つの HoloLens デバイスにビルドすると、Azure Anchor ID を共有することで、空間的な位置合わせを実現できるようになります。 これをテストするには、次の手順を実行します。

1. HoloLens デバイス 1 で次のようにします。Rover Explorer を目的の場所に移動します。
2. HoloLens デバイス 1 で次のようにします。Azure セッションを開始します。
3. HoloLens デバイス 1 で次のようにします。Azure Anchor を作成します (Rover Explorer の場所にアンカーを作成します)。
4. HoloLens デバイス 1 で次のようにします。Azure Anchor ID をネットワークに共有します。
5. HoloLens デバイス 2 で次のようにします。アプリを起動します。
6. HoloLens デバイス 2 で次のようにします。ネットワークから共有アンカー ID を取得します (HoloLens デバイス 1 から共有されたアンカー ID を取得します)。
7. HoloLens デバイス 2 で次のようにします。Azure セッションを開始します。
8. HoloLens デバイス 2 で次のようにします。Azure Anchor を見つけます (手順 3 の場所に Rover Explorer を配置します)。

> [!TIP]
> HoloLens が 1 つしかない場合でも、2 つ目の HoloLens デバイスを使用する代わりにアプリを再起動することで、機能をテストできます。

## <a name="congratulations"></a>結論

このチュートリアルでは、Azure Spatial Anchor ID を HoloLens のローカル ディスクに保存して、アプリのセッションとアプリの再起動の間で Azure Spatial Anchors を永続化する方法について学習しました。 また、Azure Spatial Anchors を複数のデバイス間で共有し、基本的なマルチユーザーの静的ホログラム共有エクスペリエンスを実現する方法についても学習しました。

次のチュートリアルでは、リアルタイムのフィードバックをユーザーに提供する方法について学習します。 このフィードバックには、アンカーの作成、環境の品質についての理解、および Azure セッションの状態に関する情報が含まれています。 フィードバックがなければ、アンカーが Azure に正常にアップロードされたかどうか、環境の品質がアンカーの作成に十分であるかどうか、または現在の状態をユーザーが知ることができません。

> [!div class="nextstepaction"]
> [次のチュートリアル:4.Azure Spatial Anchors フィードバックの表示](mr-learning-asa-04.md)
