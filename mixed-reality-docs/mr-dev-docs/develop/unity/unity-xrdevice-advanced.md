---
title: Unity での Mixed Reality ネイティブ オブジェクト
description: Unity の基になる Holographic ネイティブオブジェクトへのアクセスを取得します。
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: unity、mixed reality、native、xrdevice、spatialcoordinatesystem、holographicframe、holographiccamera、ispatialcoordinatesystem、iholographicframe、iholographiccamera、get ptr、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット
ms.openlocfilehash: a64deb46db82e6d0401a803e45dcbbd854476745
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679931"
---
# <a name="mixed-reality-native-objects-in-unity"></a><span data-ttu-id="00828-104">Unity での Mixed Reality ネイティブ オブジェクト</span><span class="sxs-lookup"><span data-stu-id="00828-104">Mixed Reality native objects in Unity</span></span>

<span data-ttu-id="00828-105">[HolographicSpace を取得](../native/getting-a-holographicspace.md) することは、カメラデータの受信とフレームのレンダリングを開始する前に、すべての Mixed Reality アプリで実行されます。</span><span class="sxs-lookup"><span data-stu-id="00828-105">[Getting a HolographicSpace](../native/getting-a-holographicspace.md) is what every Mixed Reality app does before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="00828-106">Unity では、エンジンはこれらの手順を自動的に処理し、レンダリングループの一部として Holographic オブジェクトと更新を内部的に処理します。</span><span class="sxs-lookup"><span data-stu-id="00828-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and updates internally as part of its render loop.</span></span>

<span data-ttu-id="00828-107">ただし、高度なシナリオでは、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> や現在の <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>など、基になるネイティブオブジェクトへのアクセスが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="00828-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span> <span data-ttu-id="00828-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">Unityengine. XR. XRDevice</a> は、これらのネイティブオブジェクトへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="00828-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> is what provides access to these native objects.</span></span>

## <a name="xrdevice"></a><span data-ttu-id="00828-109">XRDevice</span><span class="sxs-lookup"><span data-stu-id="00828-109">XRDevice</span></span> 

<span data-ttu-id="00828-110">**名前空間:** *unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="00828-110">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="00828-111">**型:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="00828-111">**Type:** *XRDevice*</span></span>

<span data-ttu-id="00828-112">*XRDevice* 型を使用すると、<a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">表示 ptr</a>メソッドを使用して、基になるネイティブオブジェクトにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="00828-112">The *XRDevice* type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="00828-113">Getによって返される値は、プラットフォームによって異なります。</span><span class="sxs-lookup"><span data-stu-id="00828-113">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="00828-114">ユニバーサル Windows プラットフォームで、Windows Mixed Reality XR SDK を対象とする場合、XRDevice は次の構造にポインター (IntPtr) を返します。</span><span class="sxs-lookup"><span data-stu-id="00828-114">On the Universal Windows Platform, when targeting the Windows Mixed Reality XR SDK, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span> 

```cs
using System;
using System.Runtime.InteropServices;

[StructLayout(LayoutKind.Sequential)]
struct HolographicFrameNativeData
{
    public uint VersionNumber;
    public uint MaxNumberOfCameras;
    public IntPtr ISpatialCoordinateSystemPtr; // Windows::Perception::Spatial::ISpatialCoordinateSystem
    public IntPtr IHolographicFramePtr; // Windows::Graphics::Holographic::IHolographicFrame 
    public IntPtr IHolographicCameraPtr; // // Windows::Graphics::Holographic::IHolographicCamera
}
```
<span data-ttu-id="00828-115">Marshal.ptrtostructure メソッドを使用して HolographicFrameNativeData に変換できます。</span><span class="sxs-lookup"><span data-stu-id="00828-115">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
<span data-ttu-id="00828-116">***IHolographicCameraPtr** は、unmanagedtype.bool としてマーシャリングされた IntPtr の配列であり、長さは MaxNumberOfCameras と同じです。*</span><span class="sxs-lookup"><span data-stu-id="00828-116">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span> 

### <a name="unmarshaling-native-pointers"></a><span data-ttu-id="00828-117">マーシャリング (ネイティブポインターを)</span><span class="sxs-lookup"><span data-stu-id="00828-117">Unmarshaling native pointers</span></span>

<span data-ttu-id="00828-118">[MixedReality](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT)を使用している場合は、メソッドを使用してネイティブポインターからマネージオブジェクトを構築できます。 `FromNativePtr()`</span><span class="sxs-lookup"><span data-stu-id="00828-118">If you are using [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) you can construct a managed object from a native pointer using the `FromNativePtr()` method:</span></span>

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(hfd.ISpatialCoordinateSystemPtr);
```

<span data-ttu-id="00828-119">それ以外の場合は、を使用 `Marshal.GetObjectForIUnknown()` し、目的の型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="00828-119">Otherwise, use `Marshal.GetObjectForIUnknown()` and cast to the desired type:</span></span>

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = (Windows.Perception.Spatial.SpatialCoordinateSystem)Marshal.GetObjectForIUnknown(hfd.ISpatialCoordinateSystemPtr);
#endif
```

### <a name="converting-between-coordinate-systems"></a><span data-ttu-id="00828-120">座標系の変換</span><span class="sxs-lookup"><span data-stu-id="00828-120">Converting between coordinate systems</span></span>

<span data-ttu-id="00828-121">Unity は、左手座標系を使用します。一方、Windows 認識 Api は、右手座標系を使用します。</span><span class="sxs-lookup"><span data-stu-id="00828-121">Unity uses a left-handed coordinate system, while the Windows Perception APIs use right-handed coordinate systems.</span></span> <span data-ttu-id="00828-122">これらの2つの規則間で変換を行うには、次のヘルパーを使用します。</span><span class="sxs-lookup"><span data-stu-id="00828-122">To convert between these two conventions, you can use the following helpers:</span></span>

```cs
namespace NumericsConversion
{
    public static class NumericsConversionExtensions
    {
        public static UnityEngine.Vector3 ToUnity(this System.Numerics.Vector3 v) => new UnityEngine.Vector3(v.X, v.Y, -v.Z);
        public static UnityEngine.Quaternion ToUnity(this System.Numerics.Quaternion q) => new UnityEngine.Quaternion(-q.X, -q.Y, q.Z, q.W);
        public static UnityEngine.Matrix4x4 ToUnity(this System.Numerics.Matrix4x4 m) => new UnityEngine.Matrix4x4(
            new Vector4( m.M11,  m.M12, -m.M13,  m.M14),
            new Vector4( m.M21,  m.M22, -m.M23,  m.M24),
            new Vector4(-m.M31, -m.M32,  m.M33, -m.M34),
            new Vector4( m.M41,  m.M42, -m.M43,  m.M44));

        public static System.Numerics.Vector3 ToSystem(this UnityEngine.Vector3 v) => new System.Numerics.Vector3(v.x, v.y, -v.z);
        public static System.Numerics.Quaternion ToSystem(this UnityEngine.Quaternion q) => new System.Numerics.Quaternion(-q.x, -q.y, q.z, q.w);
        public static System.Numerics.Matrix4x4 ToSystem(this UnityEngine.Matrix4x4 m) => new System.Numerics.Matrix4x4(
            m.m00,  m.m10, -m.m20,  m.m30,
            m.m01,  m.m11, -m.m21,  m.m31,
           -m.m02, -m.m12,  m.m22, -m.m32,
            m.m03,  m.m13, -m.m23,  m.m33);
    }
}
```

### <a name="using-holographicframe-native-data"></a><span data-ttu-id="00828-123">HolographicFrame ネイティブデータの使用</span><span class="sxs-lookup"><span data-stu-id="00828-123">Using HolographicFrame native data</span></span>

> [!NOTE]
> <span data-ttu-id="00828-124">HolographicFrameNativeData を使用して受信したネイティブオブジェクトの状態を変更すると、予期しない動作やレンダリングアーティファクトが発生する可能性があります。また、Unity でも同じ状態が理由である場合は特にそうです</span><span class="sxs-lookup"><span data-stu-id="00828-124">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behaviour and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="00828-125">たとえば、HolographicFrame を呼び出さないでください。そうしないと、Unity がそのフレームでレンダリングする原因が、Windows が期待するようなものと同期しなくなります。これにより、 [ホログラムの安定性](../platform-capabilities-and-apis/hologram-stability.md)が低下します。</span><span class="sxs-lookup"><span data-stu-id="00828-125">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](../platform-capabilities-and-apis/hologram-stability.md).</span></span>

<span data-ttu-id="00828-126">ネイティブインターフェイスへのアクセスは、ネイティブプラグインまたは C# コードで、レンダリングやデバッグの目的で必要な場合に、HolographicFrameNativeData のデータを使用できます。</span><span class="sxs-lookup"><span data-stu-id="00828-126">You can use data from HolographicFrameNativeData when access to native interfaces is required for rendering or debugging purposes, in your native plugins or C# code.</span></span> 

<span data-ttu-id="00828-127">HolographicFrameNativeData を使用して、photon 時間の現在のフレームの予測を取得する方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="00828-127">Here is an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time.</span></span> 
```cs
using System;
using System.Runtime.InteropServices;

public static bool GetCurrentFrameDateTime(out DateTime frameDateTime)
{
#if (!UNITY_EDITOR && UNITY_WSA) || ENABLE_WINMD_SUPPORT
    IntPtr nativeStruct = UnityEngine.XR.XRDevice.GetNativePtr();

    if (nativeStruct != IntPtr.Zero)
    {
        HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativeStruct);

        if (hfd.IHolographicFramePtr != IntPtr.Zero)
        {
            var holographicFrame = (Windows.Graphics.Holographic.HolographicFrame)Marshal.GetObjectForIUnknown(hfd.IHolographicFramePtr);
            frameDateTime = holographicFrame.CurrentPrediction.Timestamp.TargetTime.DateTime;
            return true;
        }
    }

#endif

    frameDateTime = DateTime.MinValue;
    return false;
}

```

## <a name="see-also"></a><span data-ttu-id="00828-128">参照</span><span class="sxs-lookup"><span data-stu-id="00828-128">See Also</span></span>
* [<span data-ttu-id="00828-129">Windows 名前空間と HoloLens 用 Unity アプリの使用</span><span class="sxs-lookup"><span data-stu-id="00828-129">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <span data-ttu-id="00828-130"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span><span class="sxs-lookup"><span data-stu-id="00828-130"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="00828-131"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="00828-131"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="00828-132"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="00828-132"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="00828-133">DirectX でのレンダリング</span><span class="sxs-lookup"><span data-stu-id="00828-133">Rendering in DirectX</span></span>](../native/rendering-in-directx.md)
