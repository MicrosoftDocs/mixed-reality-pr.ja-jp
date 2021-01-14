---
title: Unity の視線入力
description: アプリが混合現実で作成するホログラムをユーザーがターゲットにする主な方法として、宝石入力を使用する方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 視線、ヘッド・宝石、unity、ホログラム、mixed reality、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、unity、Mixed Reality ツールキット
ms.openlocfilehash: 7efc77eff90a164fdc0476a90912a0f52c9bb33d
ms.sourcegitcommit: a1bb77f729ee2e0b3dbd1c2c837bb7614ba7b9bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192640"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="c2af1-104">Unity でのヘッドを見つめます</span><span class="sxs-lookup"><span data-stu-id="c2af1-104">Head-gaze in Unity</span></span>

<span data-ttu-id="c2af1-105">アプリが[混合現実](../../discover/mixed-reality.md)で作成する[ホログラム](../../discover/hologram.md)をユーザーが対象とする主な方法は、[宝石](../../design/gaze-and-commit.md)です。</span><span class="sxs-lookup"><span data-stu-id="c2af1-105">[Gaze](../../design/gaze-and-commit.md) is the primary way for users to target [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>

## <a name="implementing-head-gaze"></a><span data-ttu-id="c2af1-106">ヘッド見つめを実装する</span><span class="sxs-lookup"><span data-stu-id="c2af1-106">Implementing head-gaze</span></span>

<span data-ttu-id="c2af1-107">概念的には、ユーザーのヘッドセットからの光を投射してヒットを確認することによって、 [頭を見つめ](../../design/gaze-and-commit.md) ます。</span><span class="sxs-lookup"><span data-stu-id="c2af1-107">Conceptually, you determine [head-gaze](../../design/gaze-and-commit.md) by projecting a ray forward from the user's headset to see what it hits.</span></span> <span data-ttu-id="c2af1-108">Unity では、ユーザーのヘッド位置と方向は、 [カメラ](camera-in-unity.md)を通じて公開されます (具体的には [unityengine](https://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform](https://docs.unity3d.com/ScriptReference/Transform-forward.html) と [Unityengine. Camera. main](https://docs.unity3d.com/ScriptReference/Camera-main.html)を変換します。[transform. position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="c2af1-108">In Unity, the user's head position and direction are exposed through the [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="c2af1-109">[RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html)を呼び出すと、 [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html)には、3d 衝突ポイントや、ヘッド宝石光がヒットした他のユーザーオブジェクトなど、衝突に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c2af1-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) gives you a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) containing information about the collision, including the 3D collision point and the other GameObject the head-gaze ray hit.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="c2af1-110">例: ヘッドを見つめて実装する</span><span class="sxs-lookup"><span data-stu-id="c2af1-110">Example: Implement head-gaze</span></span>

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a><span data-ttu-id="c2af1-111">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="c2af1-111">Best practices</span></span>

<span data-ttu-id="c2af1-112">上記の例では、update ループから1つの raycast を使用して、ユーザーのヘッドポイントの対象を検索しますが、1つのオブジェクトを使用してすべてのヘッドを見つめたプロセスを管理することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c2af1-112">While the example above fires a single raycast from the update loop to find the target the user's head points at, we recommended using a single object to manage all head-gaze processes.</span></span> <span data-ttu-id="c2af1-113">ヘッドを見つめたロジックを組み合わせると、アプリの貴重な処理能力が節約され、raycasting はフレームごとに1つに制限されます。</span><span class="sxs-lookup"><span data-stu-id="c2af1-113">Combining your head-gaze logic will save your app precious processing power and limit your raycasting to one per frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="c2af1-114">ヘッドを視覚化する</span><span class="sxs-lookup"><span data-stu-id="c2af1-114">Visualizing head-gaze</span></span>

<span data-ttu-id="c2af1-115">コンピューター上のマウスポインターと同じように、ユーザーの顔を示す [カーソル](../../design/cursors.md) を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2af1-115">Just like with a mouse pointer on a computer, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="c2af1-116">ユーザーが対象としているコンテンツを把握することで、ユーザーが操作しようとしている内容の信頼性が向上します。</span><span class="sxs-lookup"><span data-stu-id="c2af1-116">Knowing what content a user is targeting increases confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a><span data-ttu-id="c2af1-117">Mixed Reality ツールキットの頭を見つめます</span><span class="sxs-lookup"><span data-stu-id="c2af1-117">Head-gaze in the Mixed Reality Toolkit</span></span> 
<span data-ttu-id="c2af1-118">MRTK の [入力マネージャー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) から、ヘッドを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c2af1-118">You can access head-gaze from the [Input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="c2af1-119">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="c2af1-119">Next Development Checkpoint</span></span>

<span data-ttu-id="c2af1-120">Unity の開発に関する体験に従っている場合は、MRTK コアのビルディングブロックを調べています。</span><span class="sxs-lookup"><span data-stu-id="c2af1-120">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="c2af1-121">ここから、次の構成要素を続けることができます。</span><span class="sxs-lookup"><span data-stu-id="c2af1-121">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c2af1-122">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="c2af1-122">Motion controllers</span></span>](motion-controllers-in-unity.md)

<span data-ttu-id="c2af1-123">または、Mixed Reality プラットフォームの機能と API に移動します。</span><span class="sxs-lookup"><span data-stu-id="c2af1-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c2af1-124">共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="c2af1-124">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="c2af1-125">いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="c2af1-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="c2af1-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2af1-126">See also</span></span>
* [<span data-ttu-id="c2af1-127">カメラ</span><span class="sxs-lookup"><span data-stu-id="c2af1-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="c2af1-128">カーソル</span><span class="sxs-lookup"><span data-stu-id="c2af1-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="c2af1-129">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="c2af1-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
