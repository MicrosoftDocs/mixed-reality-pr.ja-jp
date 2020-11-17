---
title: Unity の視線入力
description: アプリが混合現実で作成するホログラムをユーザーが対象にする主な方法は、宝石です。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 視線、ヘッド・宝石、unity、ホログラム、mixed reality、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、unity、Mixed Reality ツールキット
ms.openlocfilehash: 0c62de9cb1b7ea892831ea2cedbeb23be5ea7b37
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677511"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="29812-104">Unity でのヘッドを見つめます</span><span class="sxs-lookup"><span data-stu-id="29812-104">Head-gaze in Unity</span></span>

<span data-ttu-id="29812-105">アプリが[混合現実](../../discover/mixed-reality.md)で作成する[ホログラム](../../discover/hologram.md)をユーザーが対象にする主な方法は、[宝石](../../design/gaze-and-commit.md)です。</span><span class="sxs-lookup"><span data-stu-id="29812-105">[Gaze](../../design/gaze-and-commit.md) is a primary way for users to target the [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="29812-106">ヘッド見つめを実装する</span><span class="sxs-lookup"><span data-stu-id="29812-106">Implementing head-gaze</span></span>

<span data-ttu-id="29812-107">概念的には、ヘッド・ [宝石](../../design/gaze-and-commit.md) は、ヘッドセットがあるユーザーのヘッドから、接続している前方方向に、射線がどのように衝突しているかを判断することによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="29812-107">Conceptually, [head-gaze](../../design/gaze-and-commit.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span>
<span data-ttu-id="29812-108">Unity では、ユーザーの head 位置と方向は、Unity のメイン [カメラ](camera-in-unity.md)(具体的には [unityengine](https://docs.unity3d.com/ScriptReference/Camera-main.html)) を介して公開されます。[transform](https://docs.unity3d.com/ScriptReference/Transform-forward.html) と [Unityengine. Camera. main](https://docs.unity3d.com/ScriptReference/Camera-main.html)を変換します。[transform. position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="29812-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="29812-109">[RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html)を呼び出すと、衝突が発生した3d ポイントや、その他の競合しがを使用している他のオブジェクトを含む、衝突に関する情報を含む[RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html)構造が生成されます。</span><span class="sxs-lookup"><span data-stu-id="29812-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the head-gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="29812-110">例: ヘッドを見つめて実装する</span><span class="sxs-lookup"><span data-stu-id="29812-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="29812-111">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="29812-111">Best practices</span></span>

<span data-ttu-id="29812-112">上記の例では、update ループで1つの raycast を実行してユーザーのヘッドポイントの対象を見つける方法を示していますが、この操作は、gazed されているオブジェクトに関係する可能性があるすべてのオブジェクトではなく、頭を見つめて管理する1つのオブジェクトで行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="29812-112">While the example above demonstrates how to do a single raycast in an update loop to find the target the user's head points at, it is recommended to do this in a single object managing head-gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="29812-113">これにより、各フレームに1つのヘッドを raycast するだけで、アプリの処理を保存できます。</span><span class="sxs-lookup"><span data-stu-id="29812-113">This lets your app save processing by doing just one head-gaze raycast each frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="29812-114">ヘッドを視覚化する</span><span class="sxs-lookup"><span data-stu-id="29812-114">Visualizing head-gaze</span></span>

<span data-ttu-id="29812-115">マウスポインターを使用してコンテンツをターゲットにして操作するデスクトップと同様に、ユーザーの顔を示す [カーソル](../../design/cursors.md) を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="29812-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="29812-116">これにより、ユーザーが操作しようとしている内容に自信を持っています。</span><span class="sxs-lookup"><span data-stu-id="29812-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a><span data-ttu-id="29812-117">Mixed Reality Toolkit v2 でのヘッドを見つめます</span><span class="sxs-lookup"><span data-stu-id="29812-117">Head-gaze in the Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="29812-118">MRTK v2 の [入力マネージャー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) から、ヘッドを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="29812-118">You can access head-gaze from the [Input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="29812-119">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="29812-119">Next Development Checkpoint</span></span>

<span data-ttu-id="29812-120">私たちが用意した Unity 開発チェックポイント体験に従っている場合、読者は MRTK コア構成要素を探索している段階にいます。</span><span class="sxs-lookup"><span data-stu-id="29812-120">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="29812-121">ここから、次の構成要素に進むことができます。</span><span class="sxs-lookup"><span data-stu-id="29812-121">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="29812-122">ジェスチャとモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="29812-122">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)

<span data-ttu-id="29812-123">または、Mixed Reality プラットフォームの機能と API に移動します。</span><span class="sxs-lookup"><span data-stu-id="29812-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="29812-124">共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="29812-124">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="29812-125">いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="29812-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="29812-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="29812-126">See also</span></span>
* [<span data-ttu-id="29812-127">カメラ</span><span class="sxs-lookup"><span data-stu-id="29812-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="29812-128">カーソル</span><span class="sxs-lookup"><span data-stu-id="29812-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="29812-129">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="29812-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
