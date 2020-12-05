---
title: Unreal での UMG とキーボード
description: Unrealm Motion グラフィックスを使用して、ウィジェットから UI システムを作成する方法について説明します。
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Windows Mixed Reality、ホログラム、HoloLens 2、視線追跡、宝石入力、ヘッドマウントディスプレイ、Unreal engine、mixed reality ヘッドセット、windows mixed reality ヘッドセット、仮想リアリティヘッドセット、ウィジェット、UI、UMG、Unreal Motion Graphics、Unreal Engine、UE-V、UE4
ms.openlocfilehash: 59ad108a0e27298256f4f0d1661381a4f1748777
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609763"
---
# <a name="umg-and-keyboard-in-unreal"></a><span data-ttu-id="55fbe-104">Unreal での UMG とキーボード</span><span class="sxs-lookup"><span data-stu-id="55fbe-104">UMG and keyboard in Unreal</span></span>

<span data-ttu-id="55fbe-105">Unreal Motion Graphics (UMG) は、メニューやテキストボックスなどのインターフェイスを作成するために使用される Unreal Engine の組み込み UI システムです。</span><span class="sxs-lookup"><span data-stu-id="55fbe-105">Unreal Motion Graphics (UMG) is Unreal Engine’s built-in UI system, used to create interfaces such as menus and text boxes.</span></span> <span data-ttu-id="55fbe-106">UMG で作成されたユーザーインターフェイスは、ウィジェットで構成されます。</span><span class="sxs-lookup"><span data-stu-id="55fbe-106">User interfaces built with UMG consist of widgets.</span></span> <span data-ttu-id="55fbe-107">新しいウィジェットを作成し、ワールド空間に追加して、システムキーボードを使用した対話を例として有効にする手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="55fbe-107">We'll guide you through creating a new widget, adding it to world space, and enabling interaction using the system keyboard as an example.</span></span> <span data-ttu-id="55fbe-108">UMG の詳細については、公式の Unreal Engine の [ドキュメント](https://docs.unrealengine.com/en-US/Engine/UMG/index.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55fbe-108">You can learn more about UMG in the official Unreal Engine [documentation](https://docs.unrealengine.com/en-US/Engine/UMG/index.html).</span></span> 

## <a name="create-a-new-widget"></a><span data-ttu-id="55fbe-109">新しいウィジェットを作成する</span><span class="sxs-lookup"><span data-stu-id="55fbe-109">Create a new widget</span></span>

- <span data-ttu-id="55fbe-110">ゲームの UI をレイアウトするウィジェットのブループリントを作成します。</span><span class="sxs-lookup"><span data-stu-id="55fbe-110">Create a Widget Blueprint to lay out the game’s UI:</span></span>

![Unreal メニューからウィジェットのブループリントを追加するスクリーンショット](images/unreal-umg-img-01.png)

- <span data-ttu-id="55fbe-112">新しいブループリントを開き、パレットからキャンバスにコンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="55fbe-112">Open the new blueprint and add components from the Palette to the canvas.</span></span>  <span data-ttu-id="55fbe-113">この例では、"Input" セクションから2つのテキストボックスコンポーネントを追加しました。</span><span class="sxs-lookup"><span data-stu-id="55fbe-113">In this case, we've added two Text Box components from the “Input” section:</span></span>

![テキストウィジェットコンポーネントが強調表示され、展開されている [階層] ウィンドウのスクリーンショット](images/unreal-umg-img-02.png)

- <span data-ttu-id="55fbe-115">階層またはデザイナーウィンドウでウィジェットを選択し、[詳細] パネルでパラメーターを変更します。</span><span class="sxs-lookup"><span data-stu-id="55fbe-115">Select a widget in the Hierarchy or Designer window and modify parameters in the details panel.</span></span>  <span data-ttu-id="55fbe-116">この例では、既定の "ヒントテキスト" と、テキストボックスの上にマウスポインターを置いたときに表示される濃淡の色を追加しました。</span><span class="sxs-lookup"><span data-stu-id="55fbe-116">In this case, we’ve added some default “Hint Text” and a tint color that appears when you hover over the text box.</span></span>  <span data-ttu-id="55fbe-117">テキストボックスは、次の操作を行うときに HoloLens で仮想キーボードをポップアップ表示します。</span><span class="sxs-lookup"><span data-stu-id="55fbe-117">A text box will pop up a virtual keyboard on HoloLens when it's interacted with:</span></span>

![[階層] ウィンドウで変更されたパラメーターのスクリーンショット](images/unreal-umg-img-03.png)

- <span data-ttu-id="55fbe-119">[詳細] パネルでは、イベントをサブスクライブすることもできます。</span><span class="sxs-lookup"><span data-stu-id="55fbe-119">Events can also be subscribed to in the details panel:</span></span>

![[詳細] パネルのイベントのスクリーンショット](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a><span data-ttu-id="55fbe-121">ワールド空間にウィジェットを追加する</span><span class="sxs-lookup"><span data-stu-id="55fbe-121">Add a Widget to World Space</span></span>

- <span data-ttu-id="55fbe-122">新しいアクターを作成し、ウィジェットコンポーネントを追加して、アクターをシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="55fbe-122">Create a new Actor, add a Widget component, and add the actor to the scene:</span></span>

![ウィジェットがアタッチされているアクターのスクリーンショット](images/unreal-umg-img-05.png)

- <span data-ttu-id="55fbe-124">ウィジェットの詳細パネルで、 **ウィジェットクラス** を、前に作成したウィジェットのブループリントに設定します。</span><span class="sxs-lookup"><span data-stu-id="55fbe-124">In the details panel for the Widget, set the **Widget Class** to the Widget Blueprint created earlier:</span></span>

![ウィジェットクラスが設定されたブループリント詳細パネルのスクリーンショット](images/unreal-umg-img-06.png)

- <span data-ttu-id="55fbe-126">テキストウィジェットの場合は、[ **ハードウェア入力の受信** ] がオフになっていることを確認します。これにより、仮想キーボードからのみテキストが更新されます。</span><span class="sxs-lookup"><span data-stu-id="55fbe-126">For a text Widget, ensure **Receive Hardware Input** is unchecked so we only update its text from the virtual keyboard:</span></span>

![[受信ハードウェアの入力] の [相互作用] セクションのスクリーンショットがオフになっている](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a><span data-ttu-id="55fbe-128">ウィジェットの相互作用</span><span class="sxs-lookup"><span data-stu-id="55fbe-128">Widget Interaction</span></span>

<span data-ttu-id="55fbe-129">UMG ウィジェットは、通常、マウスから入力を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="55fbe-129">UMG Widgets typically receive input from a mouse.</span></span>  <span data-ttu-id="55fbe-130">HoloLens または VR では、同じイベントを取得するために、ウィジェットの対話コンポーネントでマウスをシミュレートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="55fbe-130">On HoloLens or VR, we need to simulate a mouse with a Widget Interaction component to get the same events.</span></span>

- <span data-ttu-id="55fbe-131">新しいアクターを作成し、 **ウィジェットの相互作用** コンポーネントを追加して、アクターをシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="55fbe-131">Create a new Actor, add a **Widget Interaction** component, and add the actor to your scene:</span></span>

![ウィジェットの相互作用コンポーネントが強調表示されている新しいアクターのスクリーンショット](images/unreal-umg-img-08.png)

- <span data-ttu-id="55fbe-133">ウィジェットの対話コンポーネントの詳細パネルで、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="55fbe-133">In the details panel for the Widget Interaction component:</span></span>
    - <span data-ttu-id="55fbe-134">通信距離を希望の距離の値に設定します。</span><span class="sxs-lookup"><span data-stu-id="55fbe-134">Set the interaction distance to the distance value you want</span></span>
    - <span data-ttu-id="55fbe-135">**相互作用ソース** を **カスタム** に設定する</span><span class="sxs-lookup"><span data-stu-id="55fbe-135">Set the **Interaction Source** to **custom**</span></span>
    - <span data-ttu-id="55fbe-136">開発の場合は、[ **デバッグを表示]** を **true** に設定します。</span><span class="sxs-lookup"><span data-stu-id="55fbe-136">For development, set **Show Debug** to **true**:</span></span>

![ウィジェットの相互作用とデバッグコンポーネントのプロパティのスクリーンショット](images/unreal-umg-img-09.png)

<span data-ttu-id="55fbe-138">相互作用ソースの既定値は "World" で、ウィジェット相互作用コンポーネントの世界の位置に基づいて raycasts を送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55fbe-138">The default for Interaction Source is “World”, which should send raycasts based on the world position of the Widget Interaction component.</span></span> <span data-ttu-id="55fbe-139">AR および VR では、そうではありません。</span><span class="sxs-lookup"><span data-stu-id="55fbe-139">In AR and VR, that's not the case.</span></span>  <span data-ttu-id="55fbe-140">[デバッグの表示] を有効にし、ウィジェットにポイント濃淡を追加することは、ウィジェットの相互作用コンポーネントが期待どおりに実行していることを確認するために重要です。</span><span class="sxs-lookup"><span data-stu-id="55fbe-140">Enabling “Show Debug” and adding a hover tint to widgets is important to check the widget interaction component is doing what you expect.</span></span>  <span data-ttu-id="55fbe-141">この回避策は、カスタムソースを使用し、ハンドレイのイベントグラフで raycast を設定することです。</span><span class="sxs-lookup"><span data-stu-id="55fbe-141">The workaround is to use a custom source and set the raycast in the event graph from the hand ray.</span></span>  

<span data-ttu-id="55fbe-142">ここでは、イベントティックからこれを呼び出しています。</span><span class="sxs-lookup"><span data-stu-id="55fbe-142">Here we're calling this from Event Tick:</span></span>

![イベントティックのブループリント](images/unreal-umg-img-10.png)

<span data-ttu-id="55fbe-144">次に、HoloLens 入力に反応するウィジェット対話コンポーネントに仮想マウスポインターイベントを追加します。</span><span class="sxs-lookup"><span data-stu-id="55fbe-144">Then add virtual mouse pointer events to the widget interaction component reacting to HoloLens input.</span></span>  <span data-ttu-id="55fbe-145">この例では、手が grasped のときにマウスの左押しイベントを送信し、grasped がない場合はマウスの左解放イベントを送信します。</span><span class="sxs-lookup"><span data-stu-id="55fbe-145">In this case, send a Left Mouse press event when the hand is grasped, and a Left Mouse release event when not grasped:</span></span>

![仮想マウスポインターイベントが追加されたブループリント](images/unreal-umg-img-13.png)

<span data-ttu-id="55fbe-147">これで、HoloLens 2 にアプリを展開するときに、右側から手の光が伸びることがわかります。</span><span class="sxs-lookup"><span data-stu-id="55fbe-147">Now, when you deploy the app to the HoloLens 2, you’ll see a hand ray extending from your right hand.</span></span> <span data-ttu-id="55fbe-148">編集可能なテキストボックスとエアタップのいずれかでダイレクトすると、システムキーボードが手前に表示され、テキストを入力できるようになります。</span><span class="sxs-lookup"><span data-stu-id="55fbe-148">If you direct it at one of the editable text boxes and air tap, the system keyboard will appear in front of you and allow you to enter text.</span></span> 
 
> [!NOTE]
> <span data-ttu-id="55fbe-149">HoloLens システムキーボードには、Unreal Engine 4.26 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="55fbe-149">The HoloLens system keyboard requires Unreal Engine 4.26 or later.</span></span> <span data-ttu-id="55fbe-150">また、アプリがデバイスで実行されている場合にのみ、アプリが Unreal エディターからヘッドセットにストリーミングされても、キーボードは表示されません。</span><span class="sxs-lookup"><span data-stu-id="55fbe-150">Additionally, the keyboard will not appear when your app is being streamed from the Unreal editor to the headset, only when the app is running on device.</span></span>

## <a name="see-also"></a><span data-ttu-id="55fbe-151">参照:</span><span class="sxs-lookup"><span data-stu-id="55fbe-151">See Also:</span></span>
* [<span data-ttu-id="55fbe-152">Unreal の UMG ドキュメント</span><span class="sxs-lookup"><span data-stu-id="55fbe-152">Unreal's UMG documentation</span></span>](https://docs.unrealengine.com/Engine/UMG/index.html)
* [<span data-ttu-id="55fbe-153">Unreal の UMG チュートリアル</span><span class="sxs-lookup"><span data-stu-id="55fbe-153">Unreal's UMG tutorials</span></span>](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
