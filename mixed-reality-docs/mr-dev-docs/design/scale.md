---
title: スケール
description: ホログラフィック形式で現実的に見えるようにコンテンツを表示する鍵は、現実世界の視覚的な統計に可能な限り近付けることです。
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、Style、design
ms.openlocfilehash: 7d35da2d86d8d3b7f444974d87e5aa10e58ed2c8
ms.sourcegitcommit: 9a489e8a3bf90b20f1b61606eea42c859c833424
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2020
ms.locfileid: "94340660"
---
# <a name="scale"></a><span data-ttu-id="352ae-104">スケール</span><span class="sxs-lookup"><span data-stu-id="352ae-104">Scale</span></span>

<span data-ttu-id="352ae-105">ホログラフィック形式で現実的に見えるようにコンテンツを表示する鍵は、現実世界の視覚的な統計に可能な限り近付けることです。</span><span class="sxs-lookup"><span data-stu-id="352ae-105">A key to displaying content that looks realistic in holographic form is to mimic the visual statistics of the real world as closely as possible.</span></span> <span data-ttu-id="352ae-106">これは、オブジェクトがどこにあるか、どのくらいの大きさか、何でできているのかを (現実世界で) 理解するのに役立つ視覚的な手掛かりを、できる限り多く組み込むことを意味します。</span><span class="sxs-lookup"><span data-stu-id="352ae-106">This means incorporating as many of the visual cues as we can that help us (in the real world) understand where objects are, how big they are, and what they’re made of.</span></span> <span data-ttu-id="352ae-107">オブジェクトの小数点以下桁数は、これらの視覚的な手掛かりのうち最も重要なものの1つであり、ビューアーはオブジェクトのサイズや場所の手掛かり (特に既知のサイズを持つオブジェクトの場合) を意味します。</span><span class="sxs-lookup"><span data-stu-id="352ae-107">The scale of an object is one of the most important of those visual cues, giving a viewer a sense of the size of an object as well as cues to its location (especially for objects which have a known size).</span></span> <span data-ttu-id="352ae-108">さらに、実際の規模でのオブジェクトの表示は、従来の混合現実の主要なエクスペリエンスの差別化要因の1つとして表示されています。</span><span class="sxs-lookup"><span data-stu-id="352ae-108">Further, viewing objects at real scale has been seen as one of the key experience differentiators for mixed reality in general – something that hasn’t been possible on screen-based viewing previously.</span></span>

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a><span data-ttu-id="352ae-109">オブジェクトと環境のスケールを提案する方法</span><span class="sxs-lookup"><span data-stu-id="352ae-109">How to suggest the scale of objects and environments</span></span>

<span data-ttu-id="352ae-110">オブジェクトのスケールを提案する方法は多数ありますが、その中には他の知覚要因にも影響を与えるものがあります。</span><span class="sxs-lookup"><span data-stu-id="352ae-110">There are many ways to suggest the scale of an object, some of which have possible effects on other perceptual factors.</span></span> <span data-ttu-id="352ae-111">重要なのは、オブジェクトを ' real ' のサイズで表示し、ユーザーの移動に合わせて実際のサイズを維持することです。</span><span class="sxs-lookup"><span data-stu-id="352ae-111">The key one is to simply display objects at a ‘real’ size, and maintain that realistic size as users move.</span></span> <span data-ttu-id="352ae-112">つまり、ホログラムは、実際のオブジェクトの場合と同じように、ユーザーが近くまたはさらに離れたときに、ユーザーの視覚的な角度を取得します。</span><span class="sxs-lookup"><span data-stu-id="352ae-112">This means holograms will take up a different amount of a user’s visual angle of a user as they come closer or further away, the same way that real objects do.</span></span>

### <a name="utilize-the-distance-of-objects-as-they-are-presented-to-the-user"></a><span data-ttu-id="352ae-113">ユーザーに表示されるオブジェクトの距離を利用する</span><span class="sxs-lookup"><span data-stu-id="352ae-113">Utilize the distance of objects as they are presented to the user</span></span>

<span data-ttu-id="352ae-114">一般的な方法の1つは、ユーザーに表示されるオブジェクトの距離を利用することです。</span><span class="sxs-lookup"><span data-stu-id="352ae-114">One common method is to utilize the distance of objects as they are presented to the user.</span></span> <span data-ttu-id="352ae-115">たとえば、ユーザーの前に大規模な大型車を視覚化することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="352ae-115">For example, consider visualizing a large family car in front of the user.</span></span> <span data-ttu-id="352ae-116">車が arm の長さで直接前面に配置されている場合は、ユーザーのビューのフィールドには収まりません。</span><span class="sxs-lookup"><span data-stu-id="352ae-116">If the car were directly in front of them, within arm’s length, it would be too large to fit in the user’s field of view.</span></span> <span data-ttu-id="352ae-117">この場合、オブジェクト全体を理解するために、ユーザーはヘッドと本文を移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="352ae-117">This would require the user to move their head and body to understand the entirety of the object.</span></span> <span data-ttu-id="352ae-118">車が (部屋を越えて) 離れた場所にある場合、ユーザーは、そのオブジェクト全体をビューのフィールドに表示し、それに近い場所に移動して領域の詳細を調べることで、スケールの感覚を確立できます。</span><span class="sxs-lookup"><span data-stu-id="352ae-118">If the car were placed further away (across the room), the user can establish a sense of scale by seeing the entirety of the object in their field of view, then moving themselves closer to it to inspect areas in detail.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="352ae-119">**[Volvo は、この手法を使用](https://www.youtube.com/watch?v=DilzwF90vec)** して、ユーザーにとって現実的で直観的な方法で holographic 自動車のスケールを利用し、新しい自動車の showroom エクスペリエンスを作成していました。</span><span class="sxs-lookup"><span data-stu-id="352ae-119">**[Volvo used this technique to create a showroom](https://www.youtube.com/watch?v=DilzwF90vec)** experience for a new car, utilizing the scale of the holographic car in a way that felt realistic and intuitive to the user.</span></span> <span data-ttu-id="352ae-120">このエクスペリエンスは、物理テーブルの自動車のホログラムから始まり、ユーザーはモデルの合計サイズと形状を把握できます。</span><span class="sxs-lookup"><span data-stu-id="352ae-120">The experience begins with a hologram of the car on a physical table, allowing the user to understand the total size and shape of the model.</span></span> <span data-ttu-id="352ae-121">このエクスペリエンスの後の方で、車はより大きな規模に拡大します (デバイスのビューのサイズを超えています) が、ユーザーが小さいモデルから参照のフレームを既に取得しているため、車の特徴を適切に移動できます。</span><span class="sxs-lookup"><span data-stu-id="352ae-121">Later in the experience, the car expands to a larger scale (beyond the size of the device's field of view) but, since the user already acquired a frame of reference from the smaller model, they can adequately navigate around features of the car.</span></span><br>
        <br>
        <span data-ttu-id="352ae-122">*イメージ: HoloLens の Volvo カーエクスペリエンス*</span><span class="sxs-lookup"><span data-stu-id="352ae-122">*Image: Volvo Cars experience for HoloLens*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens の volvo 車のエクスペリエンス](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

### <a name="use-holograms-to-modify-the-users-real-space"></a><span data-ttu-id="352ae-124">ホログラムを使用してユーザーの実際のスペースを変更する</span><span class="sxs-lookup"><span data-stu-id="352ae-124">Use holograms to modify the user's real space</span></span>

<span data-ttu-id="352ae-125">もう1つの方法として、ホログラムを使用してユーザーの実際のスペースを変更し、既存の壁面または天井を環境に置き換えるか、' ホール ' または ' windows ' を追加して、サイズの大きなオブジェクトが物理的な領域を "分割" するようにします。</span><span class="sxs-lookup"><span data-stu-id="352ae-125">Another method is to use holograms to modify the user's real space, replacing the existing walls or ceilings with environments or appending ‘holes’ or ‘windows’, allowing over-sized objects to seemingly 'break-through' the physical space.</span></span> <span data-ttu-id="352ae-126">たとえば、大規模なツリーは、ほとんどのユーザーの生きた部屋には収まりませんが、仮想化を天井に配置することによって、物理空間は仮想に展開されます。</span><span class="sxs-lookup"><span data-stu-id="352ae-126">For example, a large tree might not fit in most users’ living rooms, but by putting a virtual sky on their ceiling, the physical space expands into the virtual.</span></span> <span data-ttu-id="352ae-127">これにより、ユーザーは仮想ツリーのベースを段階的に確認し、実際の状態に表示されていることを確認したうえで、ルームの物理的な領域を超えて拡大することを確認できます。</span><span class="sxs-lookup"><span data-stu-id="352ae-127">This allows the user to walk around the base of the virtual tree, and gather a sense of scale of how it would appear in real life, then look up to see it extend far beyond the physical space of the room.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="352ae-128">**[Minecraft](https://minecraft.net/)** は、同様の手法を使用して概念のエクスペリエンスを開発しました。</span><span class="sxs-lookup"><span data-stu-id="352ae-128">**[Minecraft developed a concept experiences](https://minecraft.net/)** using a similar technique.</span></span> <span data-ttu-id="352ae-129">部屋の物理的な面に仮想ウィンドウを追加することにより、ルーム内の既存のオブジェクトは、部屋の物理的なスケール制限を超えて、非常に大規模な環境のコンテキストに配置されます。</span><span class="sxs-lookup"><span data-stu-id="352ae-129">By adding a virtual window to a physical surface in a room, the existing objects in the room are placed in the context of a vastly larger environment, beyond the physical scale limitations of the room.</span></span><br>
        <br>
        <span data-ttu-id="352ae-130">*イメージ: HoloLens での Minecraft コンセプトエクスペリエンス*</span><span class="sxs-lookup"><span data-stu-id="352ae-130">*Image: Minecraft concept experience for HoloLens*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens の minecraft コンセプトエクスペリエンス](images/800px-minecraftwindow-640px.jpg)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="experimenting-with-scale"></a><span data-ttu-id="352ae-132">スケールを試してみる</span><span class="sxs-lookup"><span data-stu-id="352ae-132">Experimenting with scale</span></span>

<span data-ttu-id="352ae-133">場合によっては、オブジェクトの1つの位置を維持しながら (オブジェクトの表示される ' real ' サイズを変更することによって) スケールを変更することによって、実際には移動せずに、ビューアーに近い位置にあるオブジェクトの概数を実験ことがあります。</span><span class="sxs-lookup"><span data-stu-id="352ae-133">In some cases, designers have experimented with modifying the scale (by changing the displayed ‘real’ size of the object) while maintaining a single position of the object, to approximate an object getting closer or further to a viewer without any actual movement.</span></span> <span data-ttu-id="352ae-134">このテストは、項目の表示をすぐに確認できるようにするための方法としてテストされていましたが、仮想コンテンツを表示することによる快適な制限を考慮することが推奨される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="352ae-134">This was tested in some cases as a way to simulate up-close viewing of items while still respecting potential comfort limitations of viewing virtual content closer than the “zone of comfort” would suggest.</span></span>

<span data-ttu-id="352ae-135">ただし、この操作では、次のようないくつかの成果物を作成できます。</span><span class="sxs-lookup"><span data-stu-id="352ae-135">This can create a few possible artifacts in the experience however:</span></span>
* <span data-ttu-id="352ae-136">ビューアーに対して ' 既知 ' のサイズのオブジェクトを表す仮想オブジェクトの場合、位置を変更せずにスケールを変更すると、視覚的な手掛かりが得られます (詳細については vergence [の記事を](comfort.md) 参照してください)。ただし、このサイズは、オブジェクトが近づいていることを示す monocular の手掛かりとして機能します。</span><span class="sxs-lookup"><span data-stu-id="352ae-136">For virtual objects that represent some object with a ‘known’ size to the viewer, changing the scale without changing the position leads to conflicting visual cues – the eyes may still ‘see’ the object at some depth due to vergence cues (see the [Comfort](comfort.md) article for more on this), but the size acts as a monocular cue that the object might be getting closer.</span></span> <span data-ttu-id="352ae-137">これらの競合する手掛かりによって混乱が生じるので、多くの場合、オブジェクトは (一定の深さの手掛かりによって) 維持されているように見えますが、急速に成長しています。</span><span class="sxs-lookup"><span data-stu-id="352ae-137">These conflicting cues lead to confused perceptions – viewers often see the object as staying in place (due to the constant depth cue) but growing rapidly.</span></span>
* <span data-ttu-id="352ae-138">場合によっては、スケールの変更が "looming" のキューとして表示されます。この場合、オブジェクトはビューアーによってスケールが変更されるか、または表示されない場合がありますが、ビューアーの目の目に直接移動しているように見えます (不快な人気になる可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="352ae-138">In some cases, change of scale is seen as a ‘looming’ cue instead, where the object may or may not be seen to change scale by a viewer, but does appear to be moving directly toward the viewer’s eyes (which can be an uncomfortable sensation).</span></span>
* <span data-ttu-id="352ae-139">実際の環境では、このようなスケーリングの変更は複数の軸に沿って位置が変化すると表示されることがあります。つまり、オブジェクトは、(場合によっては3D 移動の2D 投影に似ていますが) 近い位置に移動するのではなく、低下するように見えます。</span><span class="sxs-lookup"><span data-stu-id="352ae-139">With comparison surfaces in the real world, such scaling changes are sometimes seen as changing position along multiple axes – objects may appear to drop lower instead of moving closer (similar in a 2D projection of 3D movement in some cases).</span></span>
* <span data-ttu-id="352ae-140">最後に、既知の ' real world ' サイズのないオブジェクト (任意のサイズを持つ任意の図形、UI 要素など) では、スケールを変更することで、距離の変化を模倣する方法として機能的に機能する場合があります。ビューアーには、オブジェクトの実際のサイズまたは位置を理解するために必要な既存のトップダウンキュー</span><span class="sxs-lookup"><span data-stu-id="352ae-140">Finally, for objects without a known ‘real world’ size (e.g. arbitrary shapes with arbitrary sizes, UI elements, etc.), changing scale may act functionally as a way to mimic changes in distance – viewers do not have as many preexisting top-down cues by which to understand the object’s true size or location, so the scale can be processed as a more important cue.</span></span>

<br>

---

## <a name="next-discovery-checkpoint"></a><span data-ttu-id="352ae-141">次回の検出チェックポイント</span><span class="sxs-lookup"><span data-stu-id="352ae-141">Next Discovery Checkpoint</span></span>

<span data-ttu-id="352ae-142">ここまでに説明した [探索](../discover/get-started-with-mr.md) の取り組みに従っている場合は、最初の Foray が Mixed Reality の基礎になっています。</span><span class="sxs-lookup"><span data-stu-id="352ae-142">If you're following the [discovery journey](../discover/get-started-with-mr.md) we've laid out, you're at the end your initial foray into Mixed Reality foundations.</span></span> <span data-ttu-id="352ae-143">現実世界では、業界のパートナーが Mixed Reality で何を行っているのかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="352ae-143">You can either check out what industry partners are doing with Mixed Reality in the real world:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="352ae-144">業界のパートナーが Mixed Reality をどのように使用しているかを確認する</span><span class="sxs-lookup"><span data-stu-id="352ae-144">See how industry partners are using mixed reality</span></span>](../discover/get-started-with-mr.md#see-how-industry-partners-are-using-mixed-reality)

<span data-ttu-id="352ae-145">または、設計の取り組みに進んでください。</span><span class="sxs-lookup"><span data-stu-id="352ae-145">Or continue on to the design journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="352ae-146">デザインの体験を始める</span><span class="sxs-lookup"><span data-stu-id="352ae-146">Start your design journey</span></span>](../design/design.md)

## <a name="see-also"></a><span data-ttu-id="352ae-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="352ae-147">See also</span></span>
* [<span data-ttu-id="352ae-148">色、ライト、マテリアル</span><span class="sxs-lookup"><span data-stu-id="352ae-148">Color, light and materials</span></span>](../color,-light-and-materials.md)
* [<span data-ttu-id="352ae-149">文字体裁</span><span class="sxs-lookup"><span data-stu-id="352ae-149">Typography</span></span>](typography.md)
* [<span data-ttu-id="352ae-150">立体音響の設計</span><span class="sxs-lookup"><span data-stu-id="352ae-150">Spatial sound design</span></span>](spatial-sound-design.md)
