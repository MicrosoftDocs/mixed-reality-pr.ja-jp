---
title: Unity での Mixed Reality ネイティブ オブジェクト
description: XR 名前空間を使用して、Unity の基になる Holographic native オブジェクトにアクセスする方法について説明します。
author: vladkol
ms.author: vladkol
ms.date: 02/25/2021
ms.topic: article
keywords: unity、mixed reality、native、xrdevice、spatialcoordinatesystem、holographicframe、holographiccamera、ispatialcoordinatesystem、iholographicframe、iholographiccamera、get ptr、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット
ms.openlocfilehash: c202c698fe55bcd3215850579166ebcb8d4b8910
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475077"
---
# <a name="mixed-reality-native-interop-in-unity"></a><span data-ttu-id="2b085-104">Unity における Mixed Reality ネイティブ相互運用</span><span class="sxs-lookup"><span data-stu-id="2b085-104">Mixed Reality native interop in Unity</span></span>

<span data-ttu-id="2b085-105">各 Mixed Reality アプリは、カメラデータの受信とフレームのレンダリングを開始する前に [、HolographicSpace を取得し](../native/getting-a-holographicspace.md) ます。</span><span class="sxs-lookup"><span data-stu-id="2b085-105">Every Mixed Reality app [gets a HolographicSpace](../native/getting-a-holographicspace.md) before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="2b085-106">Unity では、エンジンはこれらの手順を自動的に処理し、Holographic オブジェクトを処理し、レンダリングループの一部として内部的に更新します。</span><span class="sxs-lookup"><span data-stu-id="2b085-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and internally updating as part of its render loop.</span></span>

<span data-ttu-id="2b085-107">ただし、高度なシナリオでは、 <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> や現在の <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>など、基になるネイティブオブジェクトへのアクセスが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2b085-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span>

[!INCLUDE[](includes/unity-native-ptrs.md)]

### <a name="unmarshaling-native-pointers"></a><span data-ttu-id="2b085-108">マーシャリング (ネイティブポインターを)</span><span class="sxs-lookup"><span data-stu-id="2b085-108">Unmarshaling native pointers</span></span>

<span data-ttu-id="2b085-109">`IntPtr`上記のいずれかのメソッド (MRTK では不要) からを取得した後、次のコードスニペットを使用してそれらをマネージオブジェクトにマーシャリングします。</span><span class="sxs-lookup"><span data-stu-id="2b085-109">After obtaining the `IntPtr` from one of the methods above (not needed for MRTK), use the following code snippets to marshal them to managed objects.</span></span>

<span data-ttu-id="2b085-110">[MixedReality](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT)を使用している場合は、メソッドを使用してネイティブポインターからマネージオブジェクトを構築できます。 `FromNativePtr()`</span><span class="sxs-lookup"><span data-stu-id="2b085-110">If you are using [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT), you can construct a managed object from a native pointer using the `FromNativePtr()` method:</span></span>

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(spatialCoordinateSystemPtr);
```

<span data-ttu-id="2b085-111">それ以外の場合は、を使用 `Marshal.GetObjectForIUnknown()` して、目的の型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="2b085-111">Otherwise, use `Marshal.GetObjectForIUnknown()` and cast to the type you want:</span></span>

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = Marshal.GetObjectForIUnknown(spatialCoordinateSystemPtr) as Windows.Perception.Spatial.SpatialCoordinateSystem;
#endif
```

### <a name="converting-between-coordinate-systems"></a><span data-ttu-id="2b085-112">座標系の変換</span><span class="sxs-lookup"><span data-stu-id="2b085-112">Converting between coordinate systems</span></span>

<span data-ttu-id="2b085-113">Unity は、左手座標系を使用します。一方、Windows 認識 Api は、右手座標系を使用します。</span><span class="sxs-lookup"><span data-stu-id="2b085-113">Unity uses a left-handed coordinate system, while the Windows Perception APIs use right-handed coordinate systems.</span></span> <span data-ttu-id="2b085-114">これらの2つの規則間で変換を行うには、次のヘルパーを使用します。</span><span class="sxs-lookup"><span data-stu-id="2b085-114">To convert between these two conventions, you can use the following helpers:</span></span>

```cs
namespace NumericsConversion
{
    public static class NumericsConversionExtensions
    {
        public static UnityEngine.Vector3 ToUnity(this System.Numerics.Vector3 v) => new UnityEngine.Vector3(v.X, v.Y, -v.Z);
        public static UnityEngine.Quaternion ToUnity(this System.Numerics.Quaternion q) => new UnityEngine.Quaternion(q.X, q.Y, -q.Z, -q.W);
        public static UnityEngine.Matrix4x4 ToUnity(this System.Numerics.Matrix4x4 m) => new UnityEngine.Matrix4x4(
            new Vector4( m.M11,  m.M12, -m.M13,  m.M14),
            new Vector4( m.M21,  m.M22, -m.M23,  m.M24),
            new Vector4(-m.M31, -m.M32,  m.M33, -m.M34),
            new Vector4( m.M41,  m.M42, -m.M43,  m.M44));

        public static System.Numerics.Vector3 ToSystem(this UnityEngine.Vector3 v) => new System.Numerics.Vector3(v.x, v.y, -v.z);
        public static System.Numerics.Quaternion ToSystem(this UnityEngine.Quaternion q) => new System.Numerics.Quaternion(q.x, q.y, -q.z, -q.w);
        public static System.Numerics.Matrix4x4 ToSystem(this UnityEngine.Matrix4x4 m) => new System.Numerics.Matrix4x4(
            m.m00,  m.m10, -m.m20,  m.m30,
            m.m01,  m.m11, -m.m21,  m.m31,
           -m.m02, -m.m12,  m.m22, -m.m32,
            m.m03,  m.m13, -m.m23,  m.m33);
    }
}
```

### <a name="using-holographicframe-native-data"></a><span data-ttu-id="2b085-115">HolographicFrame ネイティブデータの使用</span><span class="sxs-lookup"><span data-stu-id="2b085-115">Using HolographicFrame native data</span></span>

> [!NOTE]
> <span data-ttu-id="2b085-116">HolographicFrameNativeData 経由で受信したネイティブオブジェクトの状態を変更すると、予期しない動作やレンダリングの成果物が生じる可能性があります。特に Unity でも同じ状態になることが理由で発生します。</span><span class="sxs-lookup"><span data-stu-id="2b085-116">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behavior and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="2b085-117">たとえば、HolographicFrame を呼び出さないでください。そうしないと、Unity がそのフレームでレンダリングする原因が、Windows が期待するようなものと同期しなくなります。これにより、 [ホログラムの安定性](../platform-capabilities-and-apis/hologram-stability.md)が低下します。</span><span class="sxs-lookup"><span data-stu-id="2b085-117">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](../platform-capabilities-and-apis/hologram-stability.md).</span></span>

<span data-ttu-id="2b085-118">レンダリングまたはデバッグのためにネイティブインターフェイスにアクセスする必要がある場合は、ネイティブプラグインまたは C# コードで HolographicFrameNativeData からのデータを使用します。</span><span class="sxs-lookup"><span data-stu-id="2b085-118">If you need access to native interfaces for rendering or debugging purposes, use data from HolographicFrameNativeData in your native plugins or C# code.</span></span>

<span data-ttu-id="2b085-119">HolographicFrameNativeData を使用して、XR SDK 拡張機能を使用して photon time の現在のフレームの予測を取得する方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="2b085-119">Here's an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time using the XR SDK extensions.</span></span>

```cs
using System;
using System.Runtime.InteropServices;

public static bool GetCurrentFrameDateTime(out DateTime frameDateTime)
{
#if ENABLE_WINMD_SUPPORT
    IntPtr holographicFramePtr = UnityEngine.XR.WindowsMR.WindowsMREnvironment.CurrentHolographicRenderFrame;

    if (holographicFramePtr != IntPtr.Zero)
    {
        var holographicFrame = Marshal.GetObjectForIUnknown(holographicFramePtr) as Windows.Graphics.Holographic.HolographicFrame;
        frameDateTime = holographicFrame.CurrentPrediction.Timestamp.TargetTime.DateTime;
        return true;
    }
#endif

    frameDateTime = DateTime.MinValue;
    return false;
}
```

## <a name="see-also"></a><span data-ttu-id="2b085-120">参照</span><span class="sxs-lookup"><span data-stu-id="2b085-120">See Also</span></span>

* [<span data-ttu-id="2b085-121">Windows 名前空間と HoloLens 用 Unity アプリの使用</span><span class="sxs-lookup"><span data-stu-id="2b085-121">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <span data-ttu-id="2b085-122"><a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span><span class="sxs-lookup"><span data-stu-id="2b085-122"><a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="2b085-123"><a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="2b085-123"><a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="2b085-124"><a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="2b085-124"><a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="2b085-125">DirectX でのレンダリング</span><span class="sxs-lookup"><span data-stu-id="2b085-125">Rendering in DirectX</span></span>](../native/rendering-in-directx.md)
