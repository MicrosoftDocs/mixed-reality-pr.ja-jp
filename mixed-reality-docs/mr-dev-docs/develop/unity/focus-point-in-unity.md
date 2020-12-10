---
title: Unity でのフォーカス ポイント
description: フォーカスポイントを設定して Unity のホログラムの安定性を手動で調整する
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, フォーカスポイント, フォーカスプレーン, 安定化平面, 安定化ポイント, reprojection, LSR, 深度バッファー, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: d2708dcf39f1d2c67ab1abf69f8330f9dd536ab0
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010273"
---
# <a name="focus-point-in-unity"></a><span data-ttu-id="cfb7b-104">Unity でのフォーカス ポイント</span><span class="sxs-lookup"><span data-stu-id="cfb7b-104">Focus point in Unity</span></span>

<span data-ttu-id="cfb7b-105">**名前空間:** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="cfb7b-105">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="cfb7b-106">**型**: *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="cfb7b-106">**Type**: *HolographicSettings*</span></span>

<span data-ttu-id="cfb7b-107">現在表示されているホログラムを最適に安定させる方法についてのヒントを HoloLens に提供するには、 [フォーカスポイント](../platform-capabilities-and-apis/hologram-stability.md#reprojection) を使用します。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-107">Use the [focus point](../platform-capabilities-and-apis/hologram-stability.md#reprojection) to provide HoloLens with a hint about how to best stabilize the holograms currently being displayed.</span></span>

<span data-ttu-id="cfb7b-108">Unity でフォーカスポイントを設定する場合は、 *HolographicSettings. SetFocusPointForFrame ()* を使用してすべてのフレームを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-108">If you want to set the Focus Point in Unity, it needs to be set every frame using *HolographicSettings.SetFocusPointForFrame()*.</span></span> <span data-ttu-id="cfb7b-109">フレームにフォーカスポイントが設定されていない場合、既定の安定化平面が使用されます。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-109">When the Focus Point isn't set for a frame, the default stabilization plane is used.</span></span>

> [!NOTE]
> <span data-ttu-id="cfb7b-110">既定では、新しい Unity プロジェクトの [深度バッファーの共有を有効にする] オプションが設定されています。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-110">By default, new Unity projects have the "Enable Depth Buffer Sharing" option set.</span></span>  <span data-ttu-id="cfb7b-111">このオプションを使用すると、アプリでフォーカスポイントを指定しなくても、イマーシブデスクトップヘッドセットまたは Windows 10 April 2018 更新プログラム (RS4) 以降を実行する HoloLens で実行されている Unity アプリが Windows に深度バッファーを送信し、ホログラムの安定性を自動的に最適化します。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-111">With this option, a Unity app running on either an immersive desktop headset or a HoloLens running the Windows 10 April 2018 Update (RS4) or later will submit your depth buffer to Windows to optimize hologram stability automatically, without your app specifying a focus point:</span></span>
> * <span data-ttu-id="cfb7b-112">イマーシブデスクトップヘッドセットでは、これにより、ピクセルごとの深度ベースの再プロジェクションが有効になります。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-112">On an immersive desktop headset, this will enable per-pixel depth-based reprojection.</span></span>
> * <span data-ttu-id="cfb7b-113">Windows 10 April 2018 Update 以降を実行している HoloLens では、これにより深度バッファーが分析され、最適な安定化平面が自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-113">On a HoloLens running the Windows 10 April 2018 Update or later, this will analyze the depth buffer to pick an optimal stabilization plane automatically.</span></span>
>
> <span data-ttu-id="cfb7b-114">どちらの方法も、各フレームのフォーカスポイントを選択するために、アプリによる明示的な作業を行わずに、より優れたイメージ品質を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-114">Either approach should provide even better image quality without explicit work by your app to select a focus point for each frame.</span></span>  <span data-ttu-id="cfb7b-115">フォーカスポイントを手動で指定すると、上記の自動動作がオーバーライドされ、通常はホログラムの安定性が低下します。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-115">Note that if you do provide a focus point manually, that will override the automatic behavior described above, and will usually reduce hologram stability.</span></span>  <span data-ttu-id="cfb7b-116">一般に、アプリが HoloLens で実行されている場合は、Windows 10 April 2018 更新プログラムにまだ更新されていない場合にのみ、手動のフォーカスポイントを指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-116">Generally, you should only specify a manual focus point when your app is running on a HoloLens that has not yet been updated to the Windows 10 April 2018 Update.</span></span>

### <a name="example"></a><span data-ttu-id="cfb7b-117">例</span><span class="sxs-lookup"><span data-stu-id="cfb7b-117">Example</span></span>

<span data-ttu-id="cfb7b-118">*SetFocusPointForFrame* 静的関数で使用できるオーバーロードによって提案されているように、フォーカスポイントを設定するにはさまざまな方法があります。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-118">There are many ways to set the Focus Point, as suggested by the overloads available on the *SetFocusPointForFrame* static function.</span></span> <span data-ttu-id="cfb7b-119">次に示すのは、各フレームに対して指定されたオブジェクトにフォーカス平面を設定する簡単な例です。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-119">Presented below is a simple example to set the focus plane to the provided object for each frame:</span></span>

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to
    // the normal of the plane and ensure the user does not pass through the
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

> [!NOTE]
> <span data-ttu-id="cfb7b-120">上の単純なコードでは、フォーカスのあるオブジェクトがユーザーの背後で終了した場合に、ホログラムの安定性が低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-120">The simple code above may reduce hologram stability if the focused object ends up behind the user.</span></span> <span data-ttu-id="cfb7b-121">通常は、フォーカスポイントを手動で指定する代わりに、[ \*\*[深度バッファーの共有を有効にする] を設定することを](camera-in-unity.md#sharing-your-depth-buffers-with-windows)\*\* お勧めします。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-121">We generally recommend setting **[Enable Depth Buffer Sharing](camera-in-unity.md#sharing-your-depth-buffers-with-windows)** instead of manually specifying a focus point.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="cfb7b-122">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="cfb7b-122">Next Development Checkpoint</span></span>

<span data-ttu-id="cfb7b-123">これまでに説明した Unity 開発の取り組みに従っている場合は、Mixed Reality プラットフォームの機能と Api を試してみることになります。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-123">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="cfb7b-124">ここからは、次のトピックに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-124">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cfb7b-125">追跡の損失</span><span class="sxs-lookup"><span data-stu-id="cfb7b-125">Tracking loss</span></span>](tracking-loss-in-unity.md)

<span data-ttu-id="cfb7b-126">または、デバイスまたはエミュレーターへのアプリの配置操作に直接移動します。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-126">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cfb7b-127">HoloLens または Windows Mixed Reality イマーシブヘッドセットへのデプロイ</span><span class="sxs-lookup"><span data-stu-id="cfb7b-127">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="cfb7b-128">いつでも [Unity 開発チェックポイント](unity-development-overview.md#3-platform-capabilities-and-apis)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="cfb7b-128">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

### <a name="see-also"></a><span data-ttu-id="cfb7b-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="cfb7b-129">See also</span></span>
* [<span data-ttu-id="cfb7b-130">安定化平面</span><span class="sxs-lookup"><span data-stu-id="cfb7b-130">Stabilization plane</span></span>](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
