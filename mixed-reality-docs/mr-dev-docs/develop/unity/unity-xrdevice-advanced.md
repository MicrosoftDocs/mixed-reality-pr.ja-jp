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
# <a name="mixed-reality-native-objects-in-unity"></a>Unity での Mixed Reality ネイティブ オブジェクト

[HolographicSpace を取得](../native/getting-a-holographicspace.md) することは、カメラデータの受信とフレームのレンダリングを開始する前に、すべての Mixed Reality アプリで実行されます。 Unity では、エンジンはこれらの手順を自動的に処理し、レンダリングループの一部として Holographic オブジェクトと更新を内部的に処理します。

ただし、高度なシナリオでは、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> や現在の <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>など、基になるネイティブオブジェクトへのアクセスが必要になる場合があります。 <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">Unityengine. XR. XRDevice</a> は、これらのネイティブオブジェクトへのアクセスを提供します。

## <a name="xrdevice"></a>XRDevice 

**名前空間:** *unityengine. XR*<br>
**型:** *XRDevice*

*XRDevice* 型を使用すると、<a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">表示 ptr</a>メソッドを使用して、基になるネイティブオブジェクトにアクセスできます。 Getによって返される値は、プラットフォームによって異なります。 ユニバーサル Windows プラットフォームで、Windows Mixed Reality XR SDK を対象とする場合、XRDevice は次の構造にポインター (IntPtr) を返します。 

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
Marshal.ptrtostructure メソッドを使用して HolographicFrameNativeData に変換できます。
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
***IHolographicCameraPtr** は、unmanagedtype.bool としてマーシャリングされた IntPtr の配列であり、長さは MaxNumberOfCameras と同じです。* 

### <a name="unmarshaling-native-pointers"></a>マーシャリング (ネイティブポインターを)

[MixedReality](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT)を使用している場合は、メソッドを使用してネイティブポインターからマネージオブジェクトを構築できます。 `FromNativePtr()`

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(hfd.ISpatialCoordinateSystemPtr);
```

それ以外の場合は、を使用 `Marshal.GetObjectForIUnknown()` し、目的の型にキャストします。

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = (Windows.Perception.Spatial.SpatialCoordinateSystem)Marshal.GetObjectForIUnknown(hfd.ISpatialCoordinateSystemPtr);
#endif
```

### <a name="converting-between-coordinate-systems"></a>座標系の変換

Unity は、左手座標系を使用します。一方、Windows 認識 Api は、右手座標系を使用します。 これらの2つの規則間で変換を行うには、次のヘルパーを使用します。

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

### <a name="using-holographicframe-native-data"></a>HolographicFrame ネイティブデータの使用

> [!NOTE]
> HolographicFrameNativeData を使用して受信したネイティブオブジェクトの状態を変更すると、予期しない動作やレンダリングアーティファクトが発生する可能性があります。また、Unity でも同じ状態が理由である場合は特にそうです  たとえば、HolographicFrame を呼び出さないでください。そうしないと、Unity がそのフレームでレンダリングする原因が、Windows が期待するようなものと同期しなくなります。これにより、 [ホログラムの安定性](../platform-capabilities-and-apis/hologram-stability.md)が低下します。

ネイティブインターフェイスへのアクセスは、ネイティブプラグインまたは C# コードで、レンダリングやデバッグの目的で必要な場合に、HolographicFrameNativeData のデータを使用できます。 

HolographicFrameNativeData を使用して、photon 時間の現在のフレームの予測を取得する方法の例を次に示します。 
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

## <a name="see-also"></a>参照
* [Windows 名前空間と HoloLens 用 Unity アプリの使用](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [DirectX でのレンダリング](../native/rendering-in-directx.md)
