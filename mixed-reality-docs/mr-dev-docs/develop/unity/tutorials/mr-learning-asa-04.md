---
title: Azure Spatial Anchors チュートリアル - 4. Azure Spatial Anchors フィードバックの表示
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure Spatial Anchors からのフィードバックを表示する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 4c35af1f5a2a723df6603fbdf41dd18a2e9ee45d
ms.sourcegitcommit: 63c228af55379810ab2ee4f09f20eded1bb76229
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2020
ms.locfileid: "93353340"
---
# <a name="4-displaying-feedback-from-azure-spatial-anchors"></a><span data-ttu-id="21ee0-105">4.Azure Spatial Anchors からのフィードバックを表示する</span><span class="sxs-lookup"><span data-stu-id="21ee0-105">4. Displaying feedback from Azure Spatial Anchors</span></span>

<span data-ttu-id="21ee0-106">このチュートリアルでは、Azure Spatial Anchors (ASA) を使用したアンカーの検出、イベント、状態に関するフィードバックをユーザーに提供する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="21ee0-106">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="21ee0-107">目標</span><span class="sxs-lookup"><span data-stu-id="21ee0-107">Objectives</span></span>

* <span data-ttu-id="21ee0-108">現在の ASA セッションに関する不可欠な情報を表示する UI パネルを設定する方法を理解する</span><span class="sxs-lookup"><span data-stu-id="21ee0-108">Learn how to set up a UI panel that displays essential information about the current ASA session</span></span>
* <span data-ttu-id="21ee0-109">ASA SDK によってユーザーに提供されるフィードバック要素を理解し、確認する</span><span class="sxs-lookup"><span data-stu-id="21ee0-109">learn about and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="setting-up-asa-feedback-panel"></a><span data-ttu-id="21ee0-110">ASA フィードバック パネルの設定</span><span class="sxs-lookup"><span data-stu-id="21ee0-110">Setting up ASA feedback panel</span></span>

<span data-ttu-id="21ee0-111">[階層] ウィンドウで、 **[手順]** の **[TextContent]** オブジェクトを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="21ee0-111">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object.</span></span> <span data-ttu-id="21ee0-112">**[3D オブジェクト]** 、 **[テキスト - TextMeshPro]** の順に選択し、[指示] の [TextContent] オブジェクトの子として TextMeshPro テキスト オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="21ee0-112">Select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object:</span></span>

![新しく作成された TextMeshPro オブジェクトが選択されている Unity](images/mr-learning-asa/asa-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="21ee0-114">シーンを簡単に操作できるようにするには、ParentAnchor オブジェクトの左側にある目のアイコンをクリックして、そのオブジェクトの<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">シーンの可視性</a>をオフに設定します。</span><span class="sxs-lookup"><span data-stu-id="21ee0-114">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="21ee0-115">これにより、ゲーム中の可視性を変更することなく、[Scene]\(シーン\) ウィンドウ内のオブジェクトが非表示になります。</span><span class="sxs-lookup"><span data-stu-id="21ee0-115">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="21ee0-116">新しく作成した [テキスト (TMP)] オブジェクトに **Feedback** という名前を付け、[Inspector]\(インスペクター\) ウィンドウでその位置とサイズを変更して、指示テキストの下に配置されるようにします。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="21ee0-116">Rename the newly created Text (TMP) object **Feedback**, then, in the Inspector window, change its position and size, so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="21ee0-117">[Rect Transform]\(四角形の変換\) コンポーネントの **[Pos Y]\(位置 Y\)** を -0.24 に変更します。</span><span class="sxs-lookup"><span data-stu-id="21ee0-117">Change the Rect Transform component's **Pos Y** to -0.24.</span></span>
* <span data-ttu-id="21ee0-118">[Rect Transform]\(四角形の変換\) コンポーネントの **[幅]** を 0.555 に変更します。</span><span class="sxs-lookup"><span data-stu-id="21ee0-118">Change the Rect Transform component's **Width** to 0.555.</span></span>
* <span data-ttu-id="21ee0-119">[Rect Transform]\(四角形の変換\) コンポーネントの **[高さ]** を 0.1 に変更します。</span><span class="sxs-lookup"><span data-stu-id="21ee0-119">Change the Rect Transform component's **Height** to 0.1.</span></span>

<span data-ttu-id="21ee0-120">次に、テキスト領域内にテキストがうまく適合するように、フォントのプロパティを選択します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="21ee0-120">Then choose font properties, so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="21ee0-121">[TextMeshPro - テキスト] コンポーネントの **[フォント スタイル]** を [ボールド] に変更します。</span><span class="sxs-lookup"><span data-stu-id="21ee0-121">Change the TextMeshPro - Text component's **Font Style** to Bold.</span></span>
* <span data-ttu-id="21ee0-122">[TextMeshPro - テキスト] コンポーネントの **[フォント サイズ]** を 0.17 に変更します。</span><span class="sxs-lookup"><span data-stu-id="21ee0-122">Change the TextMeshPro - Text component's **Font Size** to 0.17.</span></span>
* <span data-ttu-id="21ee0-123">[TextMeshPro - テキスト] コンポーネントの **[配置]** を中央揃えに変更します。</span><span class="sxs-lookup"><span data-stu-id="21ee0-123">Change the TextMeshPro - Text component's **Alignment** to Center and Middle.</span></span>

![Feedback オブジェクトが構成された Unity](images/mr-learning-asa/asa-04-section1-step1-2.png)

<span data-ttu-id="21ee0-125">[階層] ウィンドウで、 **[フィードバック]** オブジェクトを選択します。次に、[Inspector]\(インスペクター\) ウィンドウで **[コンポーネントの追加]** ボタンを使用し、 **[Anchor Feedback Script (Script)]\(Anchor フィードバック スクリプト (スクリプト)\)** コンポーネントを配置して、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="21ee0-125">In the Hierarchy window, select the **Feedback** object still, then in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="21ee0-126">**Feedback** オブジェクト自体を **Anchor Feedback Script (Script)** コンポーネントの **[Feedback Text]\(フィードバック テキスト\)** フィールドに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="21ee0-126">Assign the **Feedback** object itself to the **Anchor Feedback Script (Script)** component's **Feedback Text** field.</span></span>

![Anchor Feedback Script コンポーネントが構成された Unity](images/mr-learning-asa/asa-04-section1-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="21ee0-128">結論</span><span class="sxs-lookup"><span data-stu-id="21ee0-128">Congratulations</span></span>

<span data-ttu-id="21ee0-129">このチュートリアルでは、UI パネルを作成する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="21ee0-129">In this tutorial, you learned how to create a UI panel.</span></span> <span data-ttu-id="21ee0-130">リアルタイム フィードバックをユーザーに提供する Azure Spatial Anchors 体験の現在の状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="21ee0-130">It displays the current status of the Azure Spatial Anchors experience for providing users with real-time feedback.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="21ee0-131">次のチュートリアル:5.Android と iOS 用の Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="21ee0-131">Next Tutorial: 5. Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)
