---
title: ケース スタディ - Mixed Reality で穴から覗く
description: このケーススタディでは、HoloLens での "マジックウィンドウ" 効果の実装について説明します。これにより、ユーザーは、壁の背後、床の下、および仮想の開口部を見ることができます。
author: ericrehmeyer
ms.author: bestruku
ms.date: 10/18/2019
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、マジックウィンドウ、視差
ms.openlocfilehash: 018e45a79d88cbc8e28204f023106fbe5dae39bc
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010112"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a><span data-ttu-id="978b8-104">ケース スタディ - Mixed Reality で穴から覗く</span><span class="sxs-lookup"><span data-stu-id="978b8-104">Case study - Looking through holes in your reality</span></span>

<span data-ttu-id="978b8-105">混合現実と、Microsoft HoloLens で実行できることを考える人は、通常、「どのオブジェクトをどのようにしてルームに追加できるか」といった質問になります。</span><span class="sxs-lookup"><span data-stu-id="978b8-105">When people think about mixed reality and what they can do with Microsoft HoloLens, they usually stick to questions like "What objects can I add to my room?"</span></span> <span data-ttu-id="978b8-106">または、「どのようにして自分のスペースにレイヤーを持たせることができますか」ということです。</span><span class="sxs-lookup"><span data-stu-id="978b8-106">or “What can I layer on top of my space?"</span></span> <span data-ttu-id="978b8-107">ここでは、同じテクノロジを使用して、実際の物理的なオブジェクトを検索したり、そこから見たりすることができる別の領域を強調することができます。</span><span class="sxs-lookup"><span data-stu-id="978b8-107">I’d like to highlight another area you can consider—essentially a magic trick—using the same technology to look into or through real physical objects around you.</span></span>

## <a name="the-tech"></a><span data-ttu-id="978b8-108">技術</span><span class="sxs-lookup"><span data-stu-id="978b8-108">The tech</span></span>

<span data-ttu-id="978b8-109">**[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)** 内の壁を異星人、fought で壁を突破した **[場合、また](case-study-creating-an-immersive-experience-in-fragments.md)** は **[2015 の E3 でハロー5エクスペリエンス](https://www.youtube.com/watch?v=QDw5QjDtFy8)** の unsc 無限大の hangar を確認するのに十分な経験がある場合は、私が話していることを見てきました。</span><span class="sxs-lookup"><span data-stu-id="978b8-109">If you've fought aliens as they break through your walls in **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**, unlocked a wall safe in **[Fragments](case-study-creating-an-immersive-experience-in-fragments.md)**, or were lucky enough to see the UNSC Infinity hangar in the **[Halo 5 experience at E3 in 2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)**, then you've seen what I'm talking about.</span></span> <span data-ttu-id="978b8-110">想像に応じて、この視覚的なトリックを使用して、drywall に一時的な穴を置いたり、疎 floorboard でワールドを隠したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="978b8-110">Depending on your imagination, this visual trick can be used to put temporary holes in your drywall or to hide worlds under a loose floorboard.</span></span>

![RoboRaid は、3次元パイプと、壁の背後にあるその他の構造を追加します。これは、侵入の中断として作成された穴によってのみ表示されます。](../develop/unity/images/roboraid-640px.png)

<span data-ttu-id="978b8-112">RoboRaid は、3次元パイプと、壁の背後にあるその他の構造を追加します。これは、侵入の中断として作成された穴によってのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="978b8-112">RoboRaid adds three-dimensional pipes and other structure behind your walls, visible only through holes created as the invaders break through.</span></span>

<span data-ttu-id="978b8-113">HoloLens でこれらの固有のホログラムの1つを使用すると、アプリでは、実際のウィンドウを通じて自然に表示されるのと同じ方法で、壁の背後やフロアを介してコンテンツの錯覚を提供できます。</span><span class="sxs-lookup"><span data-stu-id="978b8-113">Using one of these unique holograms on HoloLens, an app can provide the illusion of content behind your walls or through your floor in the same way that reality presents itself through an actual window.</span></span> <span data-ttu-id="978b8-114">左側に移動すると、右側に何があるかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="978b8-114">Move yourself left, and you can see whatever is on the right side.</span></span> <span data-ttu-id="978b8-115">詳細については、さらに詳しく見ていきましょう。</span><span class="sxs-lookup"><span data-stu-id="978b8-115">Get closer, and you can see a bit more of everything.</span></span> <span data-ttu-id="978b8-116">大きな違いは、実際の穴によって、魔法の holographic コンテンツに stubbornly ことができないことです。</span><span class="sxs-lookup"><span data-stu-id="978b8-116">The major difference is that real holes allow you through, while your floor stubbornly won't let you climb through to that magical holographic content.</span></span> <span data-ttu-id="978b8-117">(バックログにタスクを追加します)。</span><span class="sxs-lookup"><span data-stu-id="978b8-117">(I'll add a task to the backlog.)</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="978b8-118">バックグラウンド処理</span><span class="sxs-lookup"><span data-stu-id="978b8-118">Behind the scenes</span></span>

<span data-ttu-id="978b8-119">このトリックは、2つの効果を組み合わせたものです。</span><span class="sxs-lookup"><span data-stu-id="978b8-119">This trick is a combination of two effects.</span></span> <span data-ttu-id="978b8-120">まず、holographic コンテンツが "空間アンカー" を使用して世界にピン留めされます。</span><span class="sxs-lookup"><span data-stu-id="978b8-120">First, holographic content is pinned to the world using "spatial anchors."</span></span> <span data-ttu-id="978b8-121">アンカーを使用してそのコンテンツを "世界ロック" にすることは、移動したり、基になる空間マッピングシステムが部屋の3D モデルを更新したりしても、周囲の物理的なオブジェクトからは視覚的にずれないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="978b8-121">Using anchors to make that content "world-locked" means that what you're looking at doesn't visually drift away from the physical objects near it, even as you move or the underlying spatial mapping system updates its 3D model of your room.</span></span>

<span data-ttu-id="978b8-122">2つ目は、holographic コンテンツが非常に特殊な領域に視覚的に限定されているので、実際にはその穴だけを見ることができるからです。</span><span class="sxs-lookup"><span data-stu-id="978b8-122">Secondly, that holographic content is visually limited to a very specific space, so you can only see through the hole in your reality.</span></span> <span data-ttu-id="978b8-123">このオクルージョンは、トリックを販売する論理的な穴、ウィンドウ、または入室を探す必要があるために必要です。</span><span class="sxs-lookup"><span data-stu-id="978b8-123">That occlusion is necessary to require looking through a logical hole, window, or doorway, which sells the trick.</span></span> <span data-ttu-id="978b8-124">ほとんどのビューがブロックされていなくても、secret Jurassic ディメンションへの領域の亀裂は、適切に配置されていない恐竜のように見えます。</span><span class="sxs-lookup"><span data-stu-id="978b8-124">Without something blocking most of the view, a crack in space to a secret Jurassic dimension might just look like a poorly placed dinosaur.</span></span>

![これは実際のスクリーンショットではありませんが、MR 基本101の secret 黄泉が HoloLens を検索する方法を示しています。](images/origamiholecomposited-640px.png)

<span data-ttu-id="978b8-128">これは実際のスクリーンショットではありませんが、 [MR 基本 101](../develop/unity/tutorials/holograms-101.md) のシークレットが HoloLens でどのように見えるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="978b8-128">This is not an actual screenshot, but an illustration of how the secret underworld from the [MR Basics 101](../develop/unity/tutorials/holograms-101.md) looks on HoloLens.</span></span> <span data-ttu-id="978b8-129">黒いエンクロージャは表示されませんが、仮想の穴でコンテンツを見ることができます。</span><span class="sxs-lookup"><span data-stu-id="978b8-129">The black enclosure doesn’t show up, but you can see content through a virtual hole.</span></span> <span data-ttu-id="978b8-130">(実際のデバイスを参照している場合、フロアはそれ以上に見えなくなるように見えます。これは、それほど離れているように見えます。</span><span class="sxs-lookup"><span data-stu-id="978b8-130">(When looking through an actual device, the floor would seem to disappear even more because your eyes focus at a further distance as if it’s not even there.)</span></span>

### <a name="world-locking-holographic-content"></a><span data-ttu-id="978b8-131">ワールド-holographic コンテンツのロック</span><span class="sxs-lookup"><span data-stu-id="978b8-131">World-locking holographic content</span></span>

<span data-ttu-id="978b8-132">Unity では、WorldAnchor コンポーネントを追加するのと同じように、holographic コンテンツを世界中にロックしたままにすることができます。</span><span class="sxs-lookup"><span data-stu-id="978b8-132">In Unity, causing holographic content to stay world-locked is as easy as adding a WorldAnchor component:</span></span>

```
myObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="978b8-133">WorldAnchor コンポーネントは、近くの物理オブジェクトとの間で安定した状態を維持するために、そのオブジェクト (階層内のそのオブジェクトの下) の位置と回転を絶えず調整します。</span><span class="sxs-lookup"><span data-stu-id="978b8-133">The WorldAnchor component will constantly adjust the position and rotation of its GameObject (and thus anything else under that object in the hierarchy) to keep it stable relative to nearby physical objects.</span></span> <span data-ttu-id="978b8-134">コンテンツを作成するときは、オブジェクトのルートピボットがこの仮想ホールの中央に配置されるように作成します。</span><span class="sxs-lookup"><span data-stu-id="978b8-134">When authoring your content, create it in such a way that the root pivot of your object is centered at this virtual hole.</span></span> <span data-ttu-id="978b8-135">(オブジェクトのピボットが壁の中で深い場合、位置と回転の微妙な微調整ははるかに目立つようになり、穴が非常に安定していない可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="978b8-135">(If your object's pivot is deep in the wall, its slight tweaks in position and rotation will be much more noticeable, and the hole may not look very stable.)</span></span>

### <a name="occluding-everything-but-the-virtual-hole"></a><span data-ttu-id="978b8-136">仮想ホールを除いてすべてを Occluding</span><span class="sxs-lookup"><span data-stu-id="978b8-136">Occluding everything but the virtual hole</span></span>

<span data-ttu-id="978b8-137">ビューを選択的にブロックして、壁面で非表示にする方法はさまざまです。</span><span class="sxs-lookup"><span data-stu-id="978b8-137">There are a variety of ways to selectively block the view to what is hidden in your walls.</span></span> <span data-ttu-id="978b8-138">最も簡単なのは、HoloLens が加法ディスプレイを使用するという事実を利用することです。つまり、完全に黒のオブジェクトは非表示になります。</span><span class="sxs-lookup"><span data-stu-id="978b8-138">The simplest one takes advantage of the fact that HoloLens uses an additive display, which means that fully black objects appear invisible.</span></span> <span data-ttu-id="978b8-139">これは、特殊なシェーダーや素材を使用せずに Unity で行うことができます。黒の素材を作成して、コンテンツ内のボックスを持つオブジェクトに割り当てるだけです。</span><span class="sxs-lookup"><span data-stu-id="978b8-139">You can do this in Unity without doing any special shader or material tricks— just create a black material and assign it to an object that boxes in your content.</span></span> <span data-ttu-id="978b8-140">3D モデリングを実行したくない場合は、いくつかの既定の Quad オブジェクトを使用して、わずかに重なります。</span><span class="sxs-lookup"><span data-stu-id="978b8-140">If you don't feel like doing 3D modeling, just use a handful of default Quad objects and overlap them slightly.</span></span> <span data-ttu-id="978b8-141">このアプローチにはいくつかの欠点がありますが、動作を実現するための最も簡単な方法ですが、後でリファクタリングする可能性があると思われる場合でも、非常に忠実度の高い概念実証を利用することができます。</span><span class="sxs-lookup"><span data-stu-id="978b8-141">There are a number of drawbacks to this approach, but it is the fastest way to get something working, and getting a low-fidelity proof of concept working is great, even if you suspect you might want to refactor it later.</span></span>

<span data-ttu-id="978b8-142">上記の "ブラックボックス" アプローチの大きな欠点の1つは、写真が適切ではないことです。</span><span class="sxs-lookup"><span data-stu-id="978b8-142">One major drawback to the above "black box" approach is that it doesn't photograph well.</span></span> <span data-ttu-id="978b8-143">お客様の影響は HoloLens の表示によって完璧に見える場合がありますが、どのスクリーンショットを使用しても、壁やフロアの残りの部分ではなく、大きな黒のオブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="978b8-143">While your effect might look perfect through the display of HoloLens, any screenshots you take will show a large black object instead of what remains of your wall or floor.</span></span> <span data-ttu-id="978b8-144">その理由は、物理的なハードウェアとスクリーンショットは、複合ホログラムと現実が異なることです。</span><span class="sxs-lookup"><span data-stu-id="978b8-144">The reason for this is that the physical hardware and screenshots composite holograms and reality differently.</span></span> <span data-ttu-id="978b8-145">それでは、いくつかの偽の数値に迂回てみましょう。</span><span class="sxs-lookup"><span data-stu-id="978b8-145">Let's detour for a moment into some fake math...</span></span>

<span data-ttu-id="978b8-146">*偽の算術アラートです。これらの数値と数式は、正確なメトリックではなく、ポイントを示すことを目的としています。*</span><span class="sxs-lookup"><span data-stu-id="978b8-146">*Fake math alert! These numbers and formulas are meant to illustrate a point, not to be any sort of accurate metric!*</span></span>

<span data-ttu-id="978b8-147">HoloLens を通じて表示するもの:</span><span class="sxs-lookup"><span data-stu-id="978b8-147">What you see through HoloLens:</span></span>

```
( Reality * darkening_amount ) + Holograms
```

<span data-ttu-id="978b8-148">スクリーンショットとビデオには次のような内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="978b8-148">What you see in screenshots and video:</span></span>

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

<span data-ttu-id="978b8-149">英語の場合: HoloLens を通じて表示されるものは、(サングラスを通じてのように) 暗い現実の単純な組み合わせで、アプリが表示する必要のあるホログラムです。</span><span class="sxs-lookup"><span data-stu-id="978b8-149">In English: What you see through HoloLens is a simple combination of darkened reality (like through sunglasses) and whatever holograms the app wants to show.</span></span> <span data-ttu-id="978b8-150">しかし、スクリーンショットを撮ると、ピクセルごとの透明度の値に応じて、カメラのイメージがアプリのホログラムとブレンドされます。</span><span class="sxs-lookup"><span data-stu-id="978b8-150">But when you take a screenshot, the camera's image is blended with the app's holograms according to the per-pixel transparency value.</span></span>

<span data-ttu-id="978b8-151">この問題を回避する方法の1つとして、"ブラックボックス" の素材を変更して、深度バッファーに書き込むだけで、他の不透明な素材をすべて使用して並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="978b8-151">One way to get around this is to change the "black box" material to only write to the depth buffer, and sort with all the other opaque materials.</span></span> <span data-ttu-id="978b8-152">この例については、GitHub の [MixedRealityToolkit ファイル](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="978b8-152">For an example of this, check out the [WindowOcclusion.shader file in the MixedRealityToolkit on GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader).</span></span> <span data-ttu-id="978b8-153">関連する行がここにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="978b8-153">The relevant lines are copied here:</span></span>

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

<span data-ttu-id="978b8-154">("Offset 50, 100" という行は、関連のない問題に対処するものであるため、そのままにしておくとよいでしょう)。</span><span class="sxs-lookup"><span data-stu-id="978b8-154">(Note the "Offset 50, 100" line is to deal with unrelated issues, so it'd probably make sense to leave that out.)</span></span>

<span data-ttu-id="978b8-155">そのような非表示の遮蔽物を実装すると、アプリでは、画面と mixed reality のスクリーンショットで適切に見える箱を描くことができます。</span><span class="sxs-lookup"><span data-stu-id="978b8-155">Implementing an invisible occlusion material like that will let your app draw a box that looks correct in the display and in mixed-reality screenshots.</span></span> <span data-ttu-id="978b8-156">ボーナスポイントについては、このボックスのパフォーマンスをさらに向上させることができます。これには、少しの見えないピクセルを描画することができますが、それは雑草になる可能性があり、通常は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="978b8-156">For bonus points, you can try to improve the performance of that box even further by doing clever things to draw even fewer invisible pixels, but that can really get into the weeds and usually won't be necessary.</span></span>

![次に示すのは、occluding ボックスの外側の部分を除いて、Unity によって描画される MR の基本101のシークレットです。](images/underworld-occluded-640px.png)

<span data-ttu-id="978b8-159">次に示すのは、occluding ボックスの外側の部分を除いて、Unity によって描画される [MR の基本 101](../develop/unity/tutorials/holograms-101.md) のシークレットです。</span><span class="sxs-lookup"><span data-stu-id="978b8-159">Here is the secret underworld from [MR Basics 101](../develop/unity/tutorials/holograms-101.md) as Unity draws it, except for the outer parts of the occluding box.</span></span> <span data-ttu-id="978b8-160">黄泉の方のために、この図は箱の中央にあります。これにより、穴をできるだけ安定した状態に保つことができます。</span><span class="sxs-lookup"><span data-stu-id="978b8-160">Note that the pivot for the underworld is at the center of the box, which helps keep the hole as stable as possible relative to your actual floor.</span></span>

## <a name="do-it-yourself"></a><span data-ttu-id="978b8-161">自分で実行する</span><span class="sxs-lookup"><span data-stu-id="978b8-161">Do it yourself</span></span>

<span data-ttu-id="978b8-162">HoloLens を所有していて、その効果を試す必要がある場合は、</span><span class="sxs-lookup"><span data-stu-id="978b8-162">Have a HoloLens and want to try out the effect for yourself?</span></span> <span data-ttu-id="978b8-163">最も簡単な方法は (コーディングが不要)、無料の3D ビューアーアプリをインストールし、 [GitHub で提供した fbx ファイルをダウンロード](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) して、部屋に花ポットモデルを表示することです。</span><span class="sxs-lookup"><span data-stu-id="978b8-163">The easiest thing you can do (no coding required) is to install the free 3D Viewer app and then load the [download the.fbx file I've provided on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) to view a flower pot model in your room.</span></span> <span data-ttu-id="978b8-164">これを HoloLens に読み込んで、仕事ができていることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="978b8-164">Load it on HoloLens, and you can see the illusion at work.</span></span> <span data-ttu-id="978b8-165">モデルの前にいる場合は、小さな穴だけを見ることができます。他のすべての要素は非表示になります。</span><span class="sxs-lookup"><span data-stu-id="978b8-165">When you're in front of the model, you can only see into the small hole—everything else is invisible.</span></span> <span data-ttu-id="978b8-166">モデルを他の側から見ると、完全に消えます。</span><span class="sxs-lookup"><span data-stu-id="978b8-166">Look at the model from any other side and it disappears entirely.</span></span> <span data-ttu-id="978b8-167">3D ビューアーの移動、回転、およびスケールのコントロールを使用して、いくつかのアイデアを生成するために考えられる垂直方向の表面に仮想ホールを配置します。</span><span class="sxs-lookup"><span data-stu-id="978b8-167">Use the movement, rotation, and scale controls of 3D Viewer to position the virtual hole against any vertical surface you can think of to generate some ideas!</span></span>

![Unity エディターでこのモデルを表示すると、flowerpot の周りに大きな黒いボックスが表示されます。](images/magicwindowflowerpotineditor.png)

<span data-ttu-id="978b8-170">Unity エディターでこのモデルを表示すると、flowerpot の周りに大きな黒いボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="978b8-170">Viewing this model in your Unity editor will show a large black box around the flowerpot.</span></span> <span data-ttu-id="978b8-171">HoloLens では、ボックスが消え、マジックウィンドウ効果が提供されます。</span><span class="sxs-lookup"><span data-stu-id="978b8-171">On HoloLens, the box disappears, giving way to a magic window effect.</span></span>

<span data-ttu-id="978b8-172">この手法を使用するアプリをビルドする場合は、「 [Mixed Reality チュートリアル](../develop/unity/tutorials.md)」の[MR 基本101チュートリアル](../develop/unity/tutorials/holograms-101.md)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="978b8-172">If you want to build an app that uses this technique, check out the [MR Basics 101 tutorial](../develop/unity/tutorials/holograms-101.md) in the [Mixed Reality tutorials](../develop/unity/tutorials.md).</span></span> <span data-ttu-id="978b8-173">第7章は、隠れている (上の図のように) 隠れた黄泉を示すフロアの爆発で終わります。</span><span class="sxs-lookup"><span data-stu-id="978b8-173">Chapter 7 ends with an explosion in your floor that reveals a hidden underworld (as pictured above).</span></span> <span data-ttu-id="978b8-174">チュートリアルを行ったのは退屈ですか。</span><span class="sxs-lookup"><span data-stu-id="978b8-174">Who said tutorials had to be boring?</span></span>

<span data-ttu-id="978b8-175">ここでは、次のアイデアを参考にしてください。</span><span class="sxs-lookup"><span data-stu-id="978b8-175">Here are some ideas of where you can take this idea next:</span></span>
* <span data-ttu-id="978b8-176">仮想ホール内のコンテンツを対話形式で作成する方法について考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="978b8-176">Think of ways to make the content inside the virtual hole interactive.</span></span> <span data-ttu-id="978b8-177">ユーザーが壁を越える影響を与えることで、このトリックによって得られる不思議な意義を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="978b8-177">Letting your users have some impact beyond their walls can really improve the sense of wonder that this trick can provide.</span></span>
* <span data-ttu-id="978b8-178">オブジェクトを使用して既知の領域に戻る方法を考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="978b8-178">Think of ways to see through objects back to known areas.</span></span> <span data-ttu-id="978b8-179">たとえば、holographic 穴をコーヒーテーブルに配置し、その下にフロアを表示するにはどうすればよいでしょうか。</span><span class="sxs-lookup"><span data-stu-id="978b8-179">For example, how can you put a holographic hole in your coffee table and see your floor beneath it?</span></span>

## <a name="about-the-author"></a><span data-ttu-id="978b8-180">筆者について</span><span class="sxs-lookup"><span data-stu-id="978b8-180">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><span data-ttu-id="978b8-181"><b>Eric Rehmeyer</b></span><span class="sxs-lookup"><span data-stu-id="978b8-181"><b>Eric Rehmeyer</b></span></span><br><span data-ttu-id="978b8-182">シニアソフトウェアエンジニア @Microsoft</span><span class="sxs-lookup"><span data-stu-id="978b8-182">Senior Software Engineer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="978b8-183">関連項目</span><span class="sxs-lookup"><span data-stu-id="978b8-183">See also</span></span>
* [<span data-ttu-id="978b8-184">MR の基本 101:デバイスを使用した完全なプロジェクト</span><span class="sxs-lookup"><span data-stu-id="978b8-184">MR Basics 101: Complete project with device</span></span>](../develop/unity/tutorials/holograms-101.md)
* [<span data-ttu-id="978b8-185">座標系</span><span class="sxs-lookup"><span data-stu-id="978b8-185">Coordinate systems</span></span>](../design/coordinate-systems.md)
* [<span data-ttu-id="978b8-186">空間アンカー</span><span class="sxs-lookup"><span data-stu-id="978b8-186">Spatial anchors</span></span>](../design/spatial-anchors.md)
* [<span data-ttu-id="978b8-187">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="978b8-187">Spatial mapping</span></span>](../design/spatial-mapping.md)
