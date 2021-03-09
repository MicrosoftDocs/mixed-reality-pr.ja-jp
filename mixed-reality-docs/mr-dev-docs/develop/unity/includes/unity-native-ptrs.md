---
ms.openlocfilehash: 612168d7a1e56f74350ee8244e26e5ad886503c2
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475078"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a>WindowsMixedRealityUtilities

**名前空間:** *MixedReality。 WindowsMixedReality*<br>
**種類:** *windowsmixedrealityutilities*

MRTK は、 **Windowsmixedrealityutilities** クラスを介して、従来の WSA と XR SDK の両方で既にマーシャリングされた型を提供します。

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)

## <a name="windowsmrenvironment"></a>WindowsMREnvironment

**名前空間:** *UNITYENGINE. XR. windowsmr*<br>
**種類:** *windowsmrenvironment*

静的 **Windowsmrenvironment** クラスを使用すると、いくつかのネイティブポインターにアクセスできます。

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[従来の WSA](#tab/wsa)

## <a name="xrdevice"></a>XRDevice

**名前空間:** *unityengine. XR*<br>
**型:** *XRDevice*

<a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a>型を使用すると、<a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">表示 ptr</a>メソッドを使用して、基になるネイティブオブジェクトにアクセスできます。 Getによって返される値は、プラットフォームによって異なります。 Windows Mixed Reality を対象とするユニバーサル Windows プラットフォームでは、XRDevice は次の構造にポインター (IntPtr) を返します。

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

Marshal.ptrtostructure メソッドを使用して HolographicFrameNativeData に変換できます。

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

***IHolographicCameraPtr** は、unmanagedtype.bool としてマーシャリングされた IntPtr の配列であり、長さは MaxNumberOfCameras と同じです。*
