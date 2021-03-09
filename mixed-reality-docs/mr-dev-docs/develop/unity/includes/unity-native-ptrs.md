---
ms.openlocfilehash: 612168d7a1e56f74350ee8244e26e5ad886503c2
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475078"
---
# <a name="mrtk"></a>[<span data-ttu-id="0d56b-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="0d56b-101">MRTK</span></span>](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a><span data-ttu-id="0d56b-102">WindowsMixedRealityUtilities</span><span class="sxs-lookup"><span data-stu-id="0d56b-102">WindowsMixedRealityUtilities</span></span>

<span data-ttu-id="0d56b-103">**名前空間:** *MixedReality。 WindowsMixedReality*</span><span class="sxs-lookup"><span data-stu-id="0d56b-103">**Namespace:** *Microsoft.MixedReality.Toolkit.WindowsMixedReality*</span></span><br>
<span data-ttu-id="0d56b-104">**種類:** *windowsmixedrealityutilities*</span><span class="sxs-lookup"><span data-stu-id="0d56b-104">**Type:** *WindowsMixedRealityUtilities*</span></span>

<span data-ttu-id="0d56b-105">MRTK は、 **Windowsmixedrealityutilities** クラスを介して、従来の WSA と XR SDK の両方で既にマーシャリングされた型を提供します。</span><span class="sxs-lookup"><span data-stu-id="0d56b-105">MRTK provides already-marshalled types across both legacy WSA and XR SDK through the **WindowsMixedRealityUtilities** class.</span></span>

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="xr-sdk"></a>[<span data-ttu-id="0d56b-106">XR SDK</span><span class="sxs-lookup"><span data-stu-id="0d56b-106">XR SDK</span></span>](#tab/xr)

## <a name="windowsmrenvironment"></a><span data-ttu-id="0d56b-107">WindowsMREnvironment</span><span class="sxs-lookup"><span data-stu-id="0d56b-107">WindowsMREnvironment</span></span>

<span data-ttu-id="0d56b-108">**名前空間:** *UNITYENGINE. XR. windowsmr*</span><span class="sxs-lookup"><span data-stu-id="0d56b-108">**Namespace:** *UnityEngine.XR.WindowsMR*</span></span><br>
<span data-ttu-id="0d56b-109">**種類:** *windowsmrenvironment*</span><span class="sxs-lookup"><span data-stu-id="0d56b-109">**Type:** *WindowsMREnvironment*</span></span>

<span data-ttu-id="0d56b-110">静的 **Windowsmrenvironment** クラスを使用すると、いくつかのネイティブポインターにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="0d56b-110">The static **WindowsMREnvironment** class provides access to several native pointers.</span></span>

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="0d56b-111">従来の WSA</span><span class="sxs-lookup"><span data-stu-id="0d56b-111">Legacy WSA</span></span>](#tab/wsa)

## <a name="xrdevice"></a><span data-ttu-id="0d56b-112">XRDevice</span><span class="sxs-lookup"><span data-stu-id="0d56b-112">XRDevice</span></span>

<span data-ttu-id="0d56b-113">**名前空間:** *unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="0d56b-113">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="0d56b-114">**型:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="0d56b-114">**Type:** *XRDevice*</span></span>

<span data-ttu-id="0d56b-115"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a>型を使用すると、<a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">表示 ptr</a>メソッドを使用して、基になるネイティブオブジェクトにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="0d56b-115">The <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a> type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="0d56b-116">Getによって返される値は、プラットフォームによって異なります。</span><span class="sxs-lookup"><span data-stu-id="0d56b-116">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="0d56b-117">Windows Mixed Reality を対象とするユニバーサル Windows プラットフォームでは、XRDevice は次の構造にポインター (IntPtr) を返します。</span><span class="sxs-lookup"><span data-stu-id="0d56b-117">On the Universal Windows Platform when targeting Windows Mixed Reality, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span>

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
    public IntPtr IHolographicCameraPtr; // Windows::Graphics::Holographic::IHolographicCamera
}
```

<span data-ttu-id="0d56b-118">Marshal.ptrtostructure メソッドを使用して HolographicFrameNativeData に変換できます。</span><span class="sxs-lookup"><span data-stu-id="0d56b-118">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

<span data-ttu-id="0d56b-119">***IHolographicCameraPtr** は、unmanagedtype.bool としてマーシャリングされた IntPtr の配列であり、長さは MaxNumberOfCameras と同じです。*</span><span class="sxs-lookup"><span data-stu-id="0d56b-119">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span>
