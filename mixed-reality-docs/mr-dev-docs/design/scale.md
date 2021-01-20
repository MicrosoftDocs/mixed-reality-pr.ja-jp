---
title: スケール
description: ホログラフィック形式で現実的に見えるようにコンテンツを表示する鍵は、現実世界の視覚的な統計に可能な限り近付けることです。
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、Style、design、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual Reality ヘッドセット、HoloLens、scale、ホログラム
ms.openlocfilehash: 12b1c96146f76274831c9bc3427cef93bb326f70
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583314"
---
# <a name="scale"></a><span data-ttu-id="065da-104">スケール</span><span class="sxs-lookup"><span data-stu-id="065da-104">Scale</span></span>

<span data-ttu-id="065da-105">現実的な holographic コンテンツを表示するための鍵は、現実世界の視覚的な統計をできるだけ近づけることです。</span><span class="sxs-lookup"><span data-stu-id="065da-105">The key to displaying realistic holographic content is mimicking the visual statistics of the real world as closely as possible.</span></span> <span data-ttu-id="065da-106">視覚的な手掛かりを組み込むことで、オブジェクトの場所、オブジェクトの大きさ、およびオブジェクトの構成を実際のユーザーが理解できるようにします。</span><span class="sxs-lookup"><span data-stu-id="065da-106">Incorporate visual cues to help real-world users understand where objects are, how big they are, and what they’re made of.</span></span> <span data-ttu-id="065da-107">オブジェクトのスケールは、オブジェクトのサイズや位置の手掛かりをビューアーに認識させるため、最も重要な視覚的な手掛かりの1つです。</span><span class="sxs-lookup"><span data-stu-id="065da-107">The scale of an object is one of the most important visual cues because it gives viewer a sense of the objects size and cues to its location.</span></span> <span data-ttu-id="065da-108">さらに、実際のスケールでのオブジェクトの表示は、従来の画面ベースの表示では実現できなかったものです。</span><span class="sxs-lookup"><span data-stu-id="065da-108">Further, viewing objects at real scale is one of the key experience differentiators for mixed reality in general – something that hasn’t been possible on previous screen-based viewing.</span></span>

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a><span data-ttu-id="065da-109">オブジェクトと環境のスケールを提案する方法</span><span class="sxs-lookup"><span data-stu-id="065da-109">How to suggest the scale of objects and environments</span></span>

<span data-ttu-id="065da-110">オブジェクトのスケールを提案する方法は多数ありますが、その中には他の知覚要因にも影響を与えるものがあります。</span><span class="sxs-lookup"><span data-stu-id="065da-110">There are many ways to suggest the scale of an object, some of which have possible effects on other perceptual factors.</span></span> <span data-ttu-id="065da-111">重要なのは、オブジェクトを ' real ' のサイズで表示し、ユーザーが移動するときにその現実的なサイズを維持することです。</span><span class="sxs-lookup"><span data-stu-id="065da-111">The key one is to display objects at a ‘real’ size, and maintain that realistic size as users move.</span></span> <span data-ttu-id="065da-112">ホログラムは、実際のオブジェクトの場合と同じように、ユーザーが近くまたはさらに離れたときに、ユーザーの視覚的な角度を取得します。</span><span class="sxs-lookup"><span data-stu-id="065da-112">Holograms will take up a different amount of a user’s visual angle of a user as they come closer or further away, the same way that real objects do.</span></span>

### <a name="use-the-distance-of-objects-as-theyre-presented-to-the-user"></a><span data-ttu-id="065da-113">ユーザーに表示されるオブジェクトの距離を使用する</span><span class="sxs-lookup"><span data-stu-id="065da-113">Use the distance of objects as they're presented to the user</span></span>

<span data-ttu-id="065da-114">一般的な方法の1つとして、ユーザーに表示されるオブジェクトの距離を使用します。</span><span class="sxs-lookup"><span data-stu-id="065da-114">One common method is to use the distance of objects as they're presented to the user.</span></span> <span data-ttu-id="065da-115">たとえば、ユーザーの前に大規模な大型車を視覚化することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="065da-115">For example, consider visualizing a large family car in front of the user.</span></span> <span data-ttu-id="065da-116">車が arm の長さで直接前面に配置されていた場合、ユーザーのビューのフィールドに収まりきらないことがあります。</span><span class="sxs-lookup"><span data-stu-id="065da-116">If the car was directly in front of them within arm’s length, it would be too large to fit in the user’s field of view.</span></span> <span data-ttu-id="065da-117">Close オブジェクトでは、オブジェクトの全体を理解するために、ユーザーはヘッドと本文を移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="065da-117">Close objects require the user to move their head and body to understand the entirety of the object.</span></span> <span data-ttu-id="065da-118">車がさらに (部屋に) 移動した場合、ユーザーは、ビューのフィールドにオブジェクト全体を表示することで、スケールの意味を設定できます。</span><span class="sxs-lookup"><span data-stu-id="065da-118">If the car is placed further away (across the room), the user can establish a sense of scale by seeing the entire object in their field of view.</span></span> <span data-ttu-id="065da-119">ユーザーは、より詳細な検査のために、オブジェクトの近くに移動することができます。</span><span class="sxs-lookup"><span data-stu-id="065da-119">Users could then move themselves closer to the object for a more detailed inspection.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="065da-120">**[Volvo は、この手法を使用](https://www.youtube.com/watch?v=DilzwF90vec)** して、ユーザーにとって現実的で直感的な方法で holographic car のスケールを使用して、新しい車の showroom エクスペリエンスを作成していました。</span><span class="sxs-lookup"><span data-stu-id="065da-120">**[Volvo used this technique to create a showroom](https://www.youtube.com/watch?v=DilzwF90vec)** experience for a new car, using the scale of the holographic car in a way that felt realistic and intuitive to the user.</span></span> <span data-ttu-id="065da-121">このエクスペリエンスは、物理テーブルでの車両ホログラムによって開始され、ユーザーはモデルの合計サイズと形状を把握できます。</span><span class="sxs-lookup"><span data-stu-id="065da-121">The experience begins with the car hologram on a physical table, allowing the user to understand the total size and shape of the model.</span></span> <span data-ttu-id="065da-122">このエクスペリエンスの後で、車はデバイスのビューのサイズを超えるスケールに拡張されます。</span><span class="sxs-lookup"><span data-stu-id="065da-122">Later in the experience, the car expands to a scale beyond the size of the device's field of view.</span></span> <span data-ttu-id="065da-123">ユーザーは、小さいモデルから既に参照のフレームを取得しているため、車の機能を適切にナビゲートできます。</span><span class="sxs-lookup"><span data-stu-id="065da-123">Since the user already acquired a frame of reference from the smaller model, they can adequately navigate around features of the car.</span></span><br>
        <br>
        <span data-ttu-id="065da-124">*イメージ: HoloLens の Volvo カーエクスペリエンス*</span><span class="sxs-lookup"><span data-stu-id="065da-124">*Image: Volvo Cars experience for HoloLens*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens の volvo 車のエクスペリエンス](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

### <a name="use-holograms-to-modify-the-users-real-space"></a><span data-ttu-id="065da-126">ホログラムを使用してユーザーの実際のスペースを変更する</span><span class="sxs-lookup"><span data-stu-id="065da-126">Use holograms to modify the user's real space</span></span>

<span data-ttu-id="065da-127">もう1つの方法として、ホログラムを使用してユーザーの実際の空間を変更し、既存の壁面または雲を環境に置き換えるか、' 穴または ' windows ' を追加します。</span><span class="sxs-lookup"><span data-stu-id="065da-127">Another method is to use holograms to modify the user's real space, replacing the existing walls or ceilings with environments or appending ‘holes’ or ‘windows’.</span></span> <span data-ttu-id="065da-128">これにより、サイズの変更が可能なオブジェクトが物理領域を "中断" することができます。</span><span class="sxs-lookup"><span data-stu-id="065da-128">This allows over-sized objects to seemingly 'break-through' the physical space.</span></span> <span data-ttu-id="065da-129">たとえば、大規模なツリーは、ほとんどのユーザーの生きた部屋には収まりませんが、仮想化を天井に配置することによって、物理空間は仮想に展開されます。</span><span class="sxs-lookup"><span data-stu-id="065da-129">For example, a large tree might not fit in most users’ living rooms, but by putting a virtual sky on their ceiling, the physical space expands into the virtual.</span></span> <span data-ttu-id="065da-130">これにより、ユーザーは仮想ツリーのベースを説明し、スケールや実際の外観を理解することができます。</span><span class="sxs-lookup"><span data-stu-id="065da-130">This allows the user to walk around the base of the virtual tree and gather a sense of scale and real-world appearance.</span></span> <span data-ttu-id="065da-131">ユーザーは、部屋の物理的な領域を超えて拡張できることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="065da-131">Users can then look up to see it extend far beyond the physical space of the room.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="065da-132">**[Minecraft](https://minecraft.net/)** は、同様の手法を使用して概念のエクスペリエンスを開発しました。</span><span class="sxs-lookup"><span data-stu-id="065da-132">**[Minecraft developed a concept experiences](https://minecraft.net/)** using a similar technique.</span></span> <span data-ttu-id="065da-133">物理サーフェイスに仮想ウィンドウを追加することにより、ルーム内の既存のオブジェクトは、部屋の物理的なスケール制限を超えて、大幅に大規模な環境のコンテキストに配置されます。</span><span class="sxs-lookup"><span data-stu-id="065da-133">By adding a virtual window to a physical surface, the existing objects in the room are placed in the context of a vastly larger environment, beyond the physical scale limitations of the room.</span></span><br>
        <br>
        <span data-ttu-id="065da-134">*イメージ: HoloLens での Minecraft コンセプトエクスペリエンス*</span><span class="sxs-lookup"><span data-stu-id="065da-134">*Image: Minecraft concept experience for HoloLens*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens の minecraft コンセプトエクスペリエンス](images/800px-minecraftwindow-640px.jpg)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="experimenting-with-scale"></a><span data-ttu-id="065da-136">スケールを試してみる</span><span class="sxs-lookup"><span data-stu-id="065da-136">Experimenting with scale</span></span>

<span data-ttu-id="065da-137">デザイナーには、オブジェクトの表示される ' real ' のサイズを変更することによって、スケールを変更する実験があります。</span><span class="sxs-lookup"><span data-stu-id="065da-137">Designers have experimented with modifying the scale by changing the displayed ‘real’ size of the object.</span></span> <span data-ttu-id="065da-138">同時に、実際には移動せずに、ビューアーに移動するオブジェクトを模倣するために、1つのオブジェクトの位置を維持します。</span><span class="sxs-lookup"><span data-stu-id="065da-138">At the same time, they maintain a single object position to approximate an object moving towards the viewer without any actual movement.</span></span> <span data-ttu-id="065da-139">このテストは、項目の表示をすぐに確認できるようにするための方法としてテストされていましたが、仮想コンテンツを表示することによる快適な制限を考慮することが推奨される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="065da-139">This was tested in some cases as a way to simulate up-close viewing of items while still respecting potential comfort limitations of viewing virtual content closer than the “zone of comfort” would suggest.</span></span>

<span data-ttu-id="065da-140">ただし、この操作では、次のようないくつかの成果物を作成できます。</span><span class="sxs-lookup"><span data-stu-id="065da-140">This can create a few possible artifacts in the experience however:</span></span>
* <span data-ttu-id="065da-141">ビューアーに ' 既知 ' のサイズのオブジェクトを表す仮想オブジェクトの場合、位置を変更せずにスケールを変更すると、視覚的な手掛かりが競合します。Vergence の手掛かりがあるため、目に見えないことがあります。詳細については、 [快適](comfort.md) な記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="065da-141">For virtual objects that represent some object with a ‘known’ size to the viewer, changing the scale without changing the position leads to conflicting visual cues. The eyes may still ‘see’ the object at some depth because of vergence cues. For more information, see the [Comfort](comfort.md) article.</span></span> <span data-ttu-id="065da-142">このサイズは、オブジェクトが近づいている可能性があることを monocular 合図として機能します。</span><span class="sxs-lookup"><span data-stu-id="065da-142">The size acts as a monocular cue that the object might be getting closer.</span></span> <span data-ttu-id="065da-143">これらの競合する手掛かりによって混乱が生じるので、多くの場合、オブジェクトは (一定の深さの手掛かりによって) 維持されているように見えますが、急速に成長しています。</span><span class="sxs-lookup"><span data-stu-id="065da-143">These conflicting cues lead to confused perceptions – viewers often see the object as staying in place (because of the constant depth cue) but growing rapidly.</span></span>
* <span data-ttu-id="065da-144">場合によっては、スケールの変更が "looming" のキューとして表示されます。この場合、オブジェクトはビューアーによってスケールが変更されるか、または表示されない場合がありますが、ビューアーの目の目に直接移動しているように見えます (不快な人気になる可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="065da-144">In some cases, change of scale is seen as a ‘looming’ cue instead, where the object may or may not be seen to change scale by a viewer, but does appear to be moving directly toward the viewer’s eyes (which can be an uncomfortable sensation).</span></span>
* <span data-ttu-id="065da-145">実際の環境では、このようなスケーリングの変更は、複数の軸に沿った位置の変化として表示されることがあります。つまり、オブジェクトは、(場合によっては3D の動きの2D 投影に似ているように) 移動するのではなく、ドロップダウンとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="065da-145">With comparison surfaces in the real world, such scaling changes are sometimes seen as changing position along multiple axes – objects appear to drop lower instead of moving closer (similar in a 2D projection of 3D movement in some cases).</span></span>
* <span data-ttu-id="065da-146">最後に、既知の ' real world ' サイズのないオブジェクト (任意のサイズ、UI 要素などを持つ任意の図形) については、変更を模倣する方法として、スケールを変更すると機能的に機能する場合があります。</span><span class="sxs-lookup"><span data-stu-id="065da-146">Finally, for objects without a known ‘real world’ size (for example, arbitrary shapes with arbitrary sizes, UI elements, and so on), changing scale may act functionally as a way to mimic changes in distance.</span></span> <span data-ttu-id="065da-147">ビューアーには、オブジェクトの実際のサイズや場所を理解するために、既に存在している多数のトップダウンキューがないため、スケールをより重要なキューとして処理できます。</span><span class="sxs-lookup"><span data-stu-id="065da-147">Viewers don't have as many pre-existing top-down cues to understand the object’s true size or location, so the scale can be processed as a more important cue.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="065da-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="065da-148">See also</span></span>
* [<span data-ttu-id="065da-149">色、ライト、素材</span><span class="sxs-lookup"><span data-stu-id="065da-149">Color, light, and materials</span></span>](./color-light-and-materials.md)
* [<span data-ttu-id="065da-150">文字体裁</span><span class="sxs-lookup"><span data-stu-id="065da-150">Typography</span></span>](typography.md)
* [<span data-ttu-id="065da-151">立体音響の設計</span><span class="sxs-lookup"><span data-stu-id="065da-151">Spatial sound design</span></span>](spatial-sound-design.md)