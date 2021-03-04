---
title: オブジェクト コレクション
description: オブジェクトコレクションはレイアウトコントロールであり、定義済みの3次元図形内のオブジェクトの配列をレイアウトするのに役立ちます。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、コントロール、デザイン、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual Reality ヘッドセット、HoloLens、オブジェクトコレクション、2D、3D、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: 53ec99b998f1c65fdd3ca8b5d935b43ff0070500
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759153"
---
# <a name="object-collection"></a><span data-ttu-id="29234-104">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="29234-104">Object collection</span></span>

![Elements アプリの定期テーブルで使用されるオブジェクトコレクション](images/UX_Hero_ObjectCollection.jpg)<br>

<span data-ttu-id="29234-106">オブジェクトコレクションはレイアウトコントロールであり、定義済みの3次元図形内のオブジェクトの配列をレイアウトするのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="29234-106">Object collection is a layout control, which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="29234-107">さまざまな表面スタイル (\* \* 平面、円柱、球、 **放射状**) がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="29234-107">It supports various surface styles - \*\*plane, cylinder, sphere, and **radial**.</span></span> <span data-ttu-id="29234-108">オブジェクトの半径とサイズ、およびそれらの間の間隔を調整できます。</span><span class="sxs-lookup"><span data-stu-id="29234-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="29234-109">オブジェクトコレクションでは、Unity からのすべてのオブジェクト (2D と3D の両方) がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="29234-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="29234-110">**[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** では、オブジェクトコレクションの作成に役立つ Unity スクリプトと例を作成しました。</span><span class="sxs-lookup"><span data-stu-id="29234-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="29234-111">オブジェクトコレクションの例</span><span class="sxs-lookup"><span data-stu-id="29234-111">Object collection examples</span></span>

<span data-ttu-id="29234-112">[要素の周期](../develop/unity/periodic-table-of-the-elements.md) 的な表は、オブジェクトコレクションのしくみを示すサンプルアプリです。</span><span class="sxs-lookup"><span data-stu-id="29234-112">[Periodic Table of the Elements](../develop/unity/periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="29234-113">オブジェクトコレクションを使用して、さまざまな形状の3D 化学要素ボックスをレイアウトします。</span><span class="sxs-lookup"><span data-stu-id="29234-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="29234-114">![Elements アプリの定期テーブルに表示されるオブジェクトコレクションの例](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="29234-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="29234-115">*Elements サンプルアプリの定期的な表に示されているオブジェクトコレクションの例*</span><span class="sxs-lookup"><span data-stu-id="29234-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="29234-116">3D オブジェクト</span><span class="sxs-lookup"><span data-stu-id="29234-116">3D objects</span></span>

<span data-ttu-id="29234-117">オブジェクトコレクションを使用すると、インポートされた3D オブジェクトをレイアウトできます。</span><span class="sxs-lookup"><span data-stu-id="29234-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="29234-118">次の例では、一部の3D 椅子オブジェクトの平面および円柱レイアウトを示しています。</span><span class="sxs-lookup"><span data-stu-id="29234-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="29234-119">![3D オブジェクトの平面レイアウトと円柱レイアウトの例](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="29234-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="29234-120">*3D オブジェクトの平面レイアウトと円柱レイアウトの例*</span><span class="sxs-lookup"><span data-stu-id="29234-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="29234-121">2D オブジェクト</span><span class="sxs-lookup"><span data-stu-id="29234-121">2D objects</span></span>

<span data-ttu-id="29234-122">オブジェクトコレクションと共に2D イメージを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="29234-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="29234-123">次の例では、グリッドに2D イメージを表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="29234-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![オブジェクトコレクションを含む2D イメージの例](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="29234-125">![2D イメージでオブジェクトコレクションを使用する例](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="29234-125">![Examples of using object collection with 2D images](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="29234-126">*2D イメージでオブジェクトコレクションを使用する例*</span><span class="sxs-lookup"><span data-stu-id="29234-126">*Examples of using object collection with 2D images*</span></span>

<br>

---

## <a name="object-collection-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="29234-127">Unity 用の MRTK (Mixed Reality Toolkit) のオブジェクトコレクション</span><span class="sxs-lookup"><span data-stu-id="29234-127">Object collection in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="29234-128">MRTK-オブジェクトコレクション</span><span class="sxs-lookup"><span data-stu-id="29234-128">MRTK - Object collection</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/object-collection.md)

<br>

---

## <a name="see-also"></a><span data-ttu-id="29234-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="29234-129">See also</span></span>

* [<span data-ttu-id="29234-130">カーソル</span><span class="sxs-lookup"><span data-stu-id="29234-130">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="29234-131">ハンド レイ</span><span class="sxs-lookup"><span data-stu-id="29234-131">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="29234-132">ボタン</span><span class="sxs-lookup"><span data-stu-id="29234-132">Button</span></span>](button.md)
* [<span data-ttu-id="29234-133">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="29234-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="29234-134">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="29234-134">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="29234-135">操作</span><span class="sxs-lookup"><span data-stu-id="29234-135">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="29234-136">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="29234-136">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="29234-137">メニューの近く</span><span class="sxs-lookup"><span data-stu-id="29234-137">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="29234-138">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="29234-138">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="29234-139">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="29234-139">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="29234-140">キーボード</span><span class="sxs-lookup"><span data-stu-id="29234-140">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="29234-141">ヒント</span><span class="sxs-lookup"><span data-stu-id="29234-141">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="29234-142">スレート</span><span class="sxs-lookup"><span data-stu-id="29234-142">Slate</span></span>](slate.md)
* [<span data-ttu-id="29234-143">スライダー</span><span class="sxs-lookup"><span data-stu-id="29234-143">Slider</span></span>](slider.md)
* [<span data-ttu-id="29234-144">シェーダー</span><span class="sxs-lookup"><span data-stu-id="29234-144">Shader</span></span>](shader.md)
* [<span data-ttu-id="29234-145">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="29234-145">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="29234-146">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="29234-146">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="29234-147">表面吸着</span><span class="sxs-lookup"><span data-stu-id="29234-147">Surface magnetism</span></span>](surface-magnetism.md)
