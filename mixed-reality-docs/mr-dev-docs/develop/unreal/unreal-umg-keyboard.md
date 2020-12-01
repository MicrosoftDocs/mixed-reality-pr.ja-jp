---
title: Unreal の UMG とキーボード
description: Unrealm Motion グラフィックスを使用して、ウィジェットから UI システムを作成する方法について説明します。
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Windows Mixed Reality、ホログラム、HoloLens 2、視線追跡、宝石入力、ヘッドマウントディスプレイ、Unreal engine、mixed reality ヘッドセット、windows mixed reality ヘッドセット、仮想リアリティヘッドセット、ウィジェット、UI、UMG、Unreal Motion Graphics、Unreal Engine、UE-V、UE4
ms.openlocfilehash: 9f22a5f7a13732727b6b122d385aad7e708a1343
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/30/2020
ms.locfileid: "96355408"
---
# <a name="umg-and-keyboard-in-unreal"></a><span data-ttu-id="c4940-104">Unreal の UMG とキーボード</span><span class="sxs-lookup"><span data-stu-id="c4940-104">UMG and keyboard in Unreal</span></span>

<span data-ttu-id="c4940-105">Unreal Motion Graphics (UMG) は、メニューやテキストボックスなどのインターフェイスを作成するために使用される Unreal Engine の組み込み UI システムです。</span><span class="sxs-lookup"><span data-stu-id="c4940-105">Unreal Motion Graphics (UMG) is Unreal Engine’s built-in UI system, used to create interfaces such as menus and text boxes.</span></span> <span data-ttu-id="c4940-106">UMG で作成されたユーザーインターフェイスは、ウィジェットで構成されます。</span><span class="sxs-lookup"><span data-stu-id="c4940-106">User interfaces built with UMG consist of widgets.</span></span> <span data-ttu-id="c4940-107">このガイドでは、システムキーボードを例として使用して、新しいウィジェットを作成し、ワールド空間に追加し、そのウィジェットとの対話を mixed reality で有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c4940-107">This guide will show you how to create a new widget, add it to world space, and enable interaction with that widget in mixed reality, using the system keyboard as an example.</span></span> <span data-ttu-id="c4940-108">UMG の詳細については、公式の Unreal Engine の [ドキュメント](https://docs.unrealengine.com/en-US/Engine/UMG/index.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4940-108">You can learn more about UMG in the official Unreal Engine [documentation](https://docs.unrealengine.com/en-US/Engine/UMG/index.html).</span></span> 

## <a name="create-a-new-widget"></a><span data-ttu-id="c4940-109">新しいウィジェットを作成する</span><span class="sxs-lookup"><span data-stu-id="c4940-109">Create a new widget</span></span>

- <span data-ttu-id="c4940-110">ゲームの UI をレイアウトするウィジェットのブループリントを作成します。</span><span class="sxs-lookup"><span data-stu-id="c4940-110">Create a Widget Blueprint to lay out the game’s UI:</span></span>

![Unreal メニューからウィジェットのブループリントを追加するスクリーンショット](images/unreal-umg-img-01.png)

- <span data-ttu-id="c4940-112">新しいブループリントを開き、パレットからキャンバスにコンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="c4940-112">Open the new blueprint and add components from the Palette to the canvas.</span></span>  <span data-ttu-id="c4940-113">この例では、"Input" セクションから2つのテキストボックスコンポーネントを追加しました。</span><span class="sxs-lookup"><span data-stu-id="c4940-113">In this case we have added two Text Box components from the “Input” section:</span></span>

![テキストウィジェットコンポーネントが強調表示され、展開されている [階層] ウィンドウのスクリーンショット](images/unreal-umg-img-02.png)

- <span data-ttu-id="c4940-115">階層またはデザイナーウィンドウでウィジェットを選択し、[詳細] パネルでパラメーターを変更します。</span><span class="sxs-lookup"><span data-stu-id="c4940-115">Select a widget in the Hierarchy or Designer window and modify parameters in the details panel.</span></span>  <span data-ttu-id="c4940-116">この例では、テキストボックス上にカーソルを合わせると、既定の "ヒントテキスト" と濃淡の色が追加されています。これにより、ウィジェットとの対話が可能になります。</span><span class="sxs-lookup"><span data-stu-id="c4940-116">In this case, we’ve added some default “Hint Text” and a tint color when the cursor is hovering over the text box to give feedback that the widget is ready to be interacted with.</span></span>  <span data-ttu-id="c4940-117">次のような操作を行うと、テキストボックスによって HoloLens の仮想キーボードがポップアップ表示されます。</span><span class="sxs-lookup"><span data-stu-id="c4940-117">A text box will pop up a virtual keyboard on HoloLens when it is interacted with:</span></span>

![[階層] ウィンドウで変更されたパラメーターのスクリーンショット](images/unreal-umg-img-03.png)

- <span data-ttu-id="c4940-119">[詳細] パネルでは、イベントをサブスクライブすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c4940-119">Events can also be subscribed to in the details panel:</span></span>

![[詳細] パネルのイベントのスクリーンショット](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a><span data-ttu-id="c4940-121">ワールド空間にウィジェットを追加する</span><span class="sxs-lookup"><span data-stu-id="c4940-121">Add a Widget to World Space</span></span>

- <span data-ttu-id="c4940-122">新しいアクターを作成し、ウィジェットコンポーネントを追加して、アクターをシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="c4940-122">Create a new Actor, add a Widget component, and add the actor to the scene:</span></span>

![ウィジェットがアタッチされているアクターのスクリーンショット](images/unreal-umg-img-05.png)

- <span data-ttu-id="c4940-124">ウィジェットの詳細パネルで、 **ウィジェットクラス** を、前に作成したウィジェットのブループリントに設定します。</span><span class="sxs-lookup"><span data-stu-id="c4940-124">In the details panel for the Widget, set the **Widget Class** to the Widget Blueprint created earlier:</span></span>

![ウィジェットクラスが設定されたブループリント詳細パネルのスクリーンショット](images/unreal-umg-img-06.png)

- <span data-ttu-id="c4940-126">テキストウィジェットの場合は、[ **ハードウェア入力の受信** ] がオフになっていることを確認します。これにより、仮想キーボードからのみテキストが更新されます。</span><span class="sxs-lookup"><span data-stu-id="c4940-126">For a text Widget, ensure **Receive Hardware Input** is unchecked so we only update its text from the virtual keyboard:</span></span>

![[受信ハードウェアの入力] の [相互作用] セクションのスクリーンショットがオフになっている](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a><span data-ttu-id="c4940-128">ウィジェットの相互作用</span><span class="sxs-lookup"><span data-stu-id="c4940-128">Widget Interaction</span></span>

<span data-ttu-id="c4940-129">UMG ウィジェットは、通常、マウスから入力を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c4940-129">UMG Widgets typically receive input from a mouse.</span></span>  <span data-ttu-id="c4940-130">HoloLens または VR では、同じイベントを取得するために、ウィジェットの対話コンポーネントでマウスをシミュレートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4940-130">On HoloLens or VR, we need to simulate a mouse with a Widget Interaction component to get the same events.</span></span>

- <span data-ttu-id="c4940-131">新しいアクターを作成し、 **ウィジェットの相互作用** コンポーネントを追加して、アクターをシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="c4940-131">Create a new Actor, add a **Widget Interaction** component, and add the actor to your scene:</span></span>

![ウィジェットの相互作用コンポーネントが強調表示されている新しいアクターのスクリーンショット](images/unreal-umg-img-08.png)

- <span data-ttu-id="c4940-133">ウィジェット対話コンポーネントの [詳細] パネルで、[対話距離] を目的の距離に設定し、[ **相互作用ソース** ] を [ **カスタム**] に設定し、開発用に [ **デバッグの表示** ] を **true** に設定します。</span><span class="sxs-lookup"><span data-stu-id="c4940-133">In the details panel for the Widget Interaction component, set the interaction distance to the desired distance, set the **Interaction Source** to **custom**, and for development, set **Show Debug** to **true**:</span></span>

![ウィジェットの相互作用とデバッグコンポーネントのプロパティのスクリーンショット](images/unreal-umg-img-09.png)

<span data-ttu-id="c4940-135">相互作用ソースの既定値は "World" で、ウィジェット相互作用コンポーネントの世界の位置に基づいて raycasts を送信する必要がありますが、AR と VR ではこのような状況が発生しないように見えます。</span><span class="sxs-lookup"><span data-stu-id="c4940-135">The default for Interaction Source is “World”, which should send raycasts based on the world position of the Widget Interaction component, but in AR and VR this does not appear to be the case.</span></span>  <span data-ttu-id="c4940-136">[デバッグの表示] を有効にして、開発中のウィジェットに hover の濃淡を追加することは、ウィジェットの相互作用コンポーネントが期待どおりに実行していることを確認するために重要です。</span><span class="sxs-lookup"><span data-stu-id="c4940-136">Enabling “Show Debug” and adding a hover tint to widgets while developing is important to sanity check the widget interaction component is doing what you expect.</span></span>  <span data-ttu-id="c4940-137">この回避策は、カスタムソースを使用し、ハンドレイのイベントグラフで raycast を設定することです。</span><span class="sxs-lookup"><span data-stu-id="c4940-137">The workaround is to use a custom source and set the raycast in the event graph from the hand ray.</span></span>  

<span data-ttu-id="c4940-138">ここでは、イベントティックからこれを呼び出しています。</span><span class="sxs-lookup"><span data-stu-id="c4940-138">Here we are calling this from Event Tick:</span></span>

![イベントティックのブループリント](images/unreal-umg-img-10.png)

<span data-ttu-id="c4940-140">次に、HoloLens 入力に反応するウィジェット対話コンポーネントに仮想マウスポインターイベントを追加します。</span><span class="sxs-lookup"><span data-stu-id="c4940-140">Then add virtual mouse pointer events to the widget interaction component reacting to HoloLens input.</span></span>  <span data-ttu-id="c4940-141">この例では、手が grasped のときにマウスの左押しイベントを送信し、grasped がない場合はマウスの左解放イベントを送信します。</span><span class="sxs-lookup"><span data-stu-id="c4940-141">In this case, send a Left Mouse press event when the hand is grasped, and a Left Mouse release event when not grasped:</span></span>

![仮想マウスポインターイベントが追加されたブループリント](images/unreal-umg-img-13.png)

<span data-ttu-id="c4940-143">これで、HoloLens 2 にアプリを展開するときに、右側から手の光が伸びることがわかります。</span><span class="sxs-lookup"><span data-stu-id="c4940-143">Now, when you deploy the app to the HoloLens 2, you’ll see a hand ray extending from your right hand.</span></span> <span data-ttu-id="c4940-144">編集可能なテキストボックスとエアタップのいずれかでダイレクトすると、システムキーボードが手前に表示され、テキストを入力できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c4940-144">If you direct it at one of the editable text boxes and air tap, the system keyboard will appear in front of you and allow you to enter text.</span></span> 
 
> [!NOTE]
> <span data-ttu-id="c4940-145">HoloLens システムキーボードには、Unreal Engine 4.26 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="c4940-145">The HoloLens system keyboard requires Unreal Engine 4.26 or later.</span></span> <span data-ttu-id="c4940-146">また、アプリがデバイスで実行されている場合にのみ、アプリが Unreal エディターからヘッドセットにストリーミングされても、キーボードは表示されません。</span><span class="sxs-lookup"><span data-stu-id="c4940-146">Additionally, the keyboard will not appear when your app is being streamed from the Unreal editor to the headset, only when the app is running on device.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4940-147">参照:</span><span class="sxs-lookup"><span data-stu-id="c4940-147">See Also:</span></span>
* [<span data-ttu-id="c4940-148">Unreal の UMG ドキュメント</span><span class="sxs-lookup"><span data-stu-id="c4940-148">Unreal's UMG documentation</span></span>](https://docs.unrealengine.com/Engine/UMG/index.html)
* [<span data-ttu-id="c4940-149">Unreal の UMG チュートリアル</span><span class="sxs-lookup"><span data-stu-id="c4940-149">Unreal's UMG tutorials</span></span>](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
