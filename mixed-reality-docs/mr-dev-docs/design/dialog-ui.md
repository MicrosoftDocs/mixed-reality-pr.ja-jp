---
title: ダイアログ
description: ダイアログのオーバーレイと、混合現実のアプリケーションでの使用方法について説明します。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Mixed Reality、HoloLens、UI コントロール、相互作用、UI、ux、UX デザイン、空間 UI、空間相互作用、3D UI、3D UX、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: 752c4cc03c90e498664c61fa3c53b303a2a83a2f
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847455"
---
# <a name="dialog"></a><span data-ttu-id="54f57-104">ダイアログ</span><span class="sxs-lookup"><span data-stu-id="54f57-104">Dialog</span></span>

![[はい] ボタンと [いいえ] ボタンが表示されたダイアログオーバーレイ (HoloLens) のスクリーンショット](images/MRTK_UX_Dialog.jpg)

<span data-ttu-id="54f57-106">ダイアログコントロールは、コンテキストアプリの情報を提供する UI オーバーレイです。多くの場合、ユーザーの操作を要求します。</span><span class="sxs-lookup"><span data-stu-id="54f57-106">Dialog controls are UI overlays that provide contextual app information, often requesting a user action.</span></span> <span data-ttu-id="54f57-107">ダイアログを使用して、ユーザーに重要な情報を提供したり、アクションを完了する前に確認や追加情報を要求したりします。</span><span class="sxs-lookup"><span data-stu-id="54f57-107">Use dialogs to give users important information and request confirmation or extra information before an action can be completed.</span></span>

<br>

---

## <a name="dialog-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="54f57-108">Unity の MRTK (Mixed Reality Toolkit) のダイアログ</span><span class="sxs-lookup"><span data-stu-id="54f57-108">Dialog in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="54f57-109">MRTK は、1つまたは2つのボタンオプションを持つ3つのサイズのダイアログコントロールを提供します。</span><span class="sxs-lookup"><span data-stu-id="54f57-109">MRTK provides dialog control in three sizes with one or two button options.</span></span> <span data-ttu-id="54f57-110">また、ほぼまたは遠くの相互作用範囲の配置距離を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="54f57-110">You can also specify the placement distance for near or far interaction range.</span></span> 

- <span data-ttu-id="54f57-111">DialogSmall_192x96。 prefab: 192x96mm</span><span class="sxs-lookup"><span data-stu-id="54f57-111">DialogSmall_192x96.prefab: 192x96mm</span></span>
- <span data-ttu-id="54f57-112">DialogMedium_192x128。 prefab: 192x128mm</span><span class="sxs-lookup"><span data-stu-id="54f57-112">DialogMedium_192x128.prefab: 192x128mm</span></span>
- <span data-ttu-id="54f57-113">DialogLarge_192x192。 prefab: 192x192mm</span><span class="sxs-lookup"><span data-stu-id="54f57-113">DialogLarge_192x192.prefab: 192x192mm</span></span>

![HoloLens で実行されているさまざまなサイズのダイアログのオーバーレイのスクリーンショット](images/MRTK_UX_Dialog_Types.jpg)


* <span data-ttu-id="54f57-115">詳細については、「 [Mrtk-Dialog](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/Dialog/README_Dialog.html)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54f57-115">For more information, see [MRTK - Dialog](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/Dialog/README_Dialog.html).</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="54f57-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="54f57-116">See also</span></span>

* [<span data-ttu-id="54f57-117">カーソル</span><span class="sxs-lookup"><span data-stu-id="54f57-117">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="54f57-118">ハンド レイ</span><span class="sxs-lookup"><span data-stu-id="54f57-118">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="54f57-119">ボタン</span><span class="sxs-lookup"><span data-stu-id="54f57-119">Button</span></span>](button.md)
* [<span data-ttu-id="54f57-120">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="54f57-120">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="54f57-121">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="54f57-121">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="54f57-122">操作</span><span class="sxs-lookup"><span data-stu-id="54f57-122">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="54f57-123">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="54f57-123">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="54f57-124">メニューの近く</span><span class="sxs-lookup"><span data-stu-id="54f57-124">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="54f57-125">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="54f57-125">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="54f57-126">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="54f57-126">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="54f57-127">キーボード</span><span class="sxs-lookup"><span data-stu-id="54f57-127">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="54f57-128">ヒント</span><span class="sxs-lookup"><span data-stu-id="54f57-128">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="54f57-129">スレート</span><span class="sxs-lookup"><span data-stu-id="54f57-129">Slate</span></span>](slate.md)
* [<span data-ttu-id="54f57-130">スライダー</span><span class="sxs-lookup"><span data-stu-id="54f57-130">Slider</span></span>](slider.md)
* [<span data-ttu-id="54f57-131">シェーダー</span><span class="sxs-lookup"><span data-stu-id="54f57-131">Shader</span></span>](shader.md)
* [<span data-ttu-id="54f57-132">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="54f57-132">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="54f57-133">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="54f57-133">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="54f57-134">表面吸着</span><span class="sxs-lookup"><span data-stu-id="54f57-134">Surface magnetism</span></span>](surface-magnetism.md)
