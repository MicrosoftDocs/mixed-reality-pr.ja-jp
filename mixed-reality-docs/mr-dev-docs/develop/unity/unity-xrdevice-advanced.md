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
# <a name="mixed-reality-native-interop-in-unity"></a>Unity における Mixed Reality ネイティブ相互運用

各 Mixed Reality アプリは、カメラデータの受信とフレームのレンダリングを開始する前に [、HolographicSpace を取得し](../native/getting-a-holographicspace.md) ます。 Unity では、エンジンはこれらの手順を自動的に処理し、Holographic オブジェクトを処理し、レンダリングループの一部として内部的に更新します。

ただし、高度なシナリオでは、 <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> や現在の <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>など、基になるネイティブオブジェクトへのアクセスが必要になる場合があります。

[!INCLUDE[](includes/unity-native-ptrs.md)]

### <a name="unmarshaling-native-pointers"></a>マーシャリング (ネイティブポインターを)

`IntPtr`上記のいずれかのメソッド (MRTK では不要) からを取得した後、次のコードスニペットを使用してそれらをマネージオブジェクトにマーシャリングします。

[MixedReality](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT)を使用している場合は、メソッドを使用してネイティブポインターからマネージオブジェクトを構築できます。 `FromNativePtr()`

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(spatialCoordinateSystemPtr);
```

それ以外の場合は、を使用 `Marshal.GetObjectForIUnknown()` して、目的の型にキャストします。

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = Marshal.GetObjectForIUnknown(spatialCoordinateSystemPtr) as Windows.Perception.Spatial.SpatialCoordinateSystem;
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

### <a name="using-holographicframe-native-data"></a>HolographicFrame ネイティブデータの使用

> [!NOTE]
> HolographicFrameNativeData 経由で受信したネイティブオブジェクトの状態を変更すると、予期しない動作やレンダリングの成果物が生じる可能性があります。特に Unity でも同じ状態になることが理由で発生します。  たとえば、HolographicFrame を呼び出さないでください。そうしないと、Unity がそのフレームでレンダリングする原因が、Windows が期待するようなものと同期しなくなります。これにより、 [ホログラムの安定性](../platform-capabilities-and-apis/hologram-stability.md)が低下します。

レンダリングまたはデバッグのためにネイティブインターフェイスにアクセスする必要がある場合は、ネイティブプラグインまたは C# コードで HolographicFrameNativeData からのデータを使用します。

HolographicFrameNativeData を使用して、XR SDK 拡張機能を使用して photon time の現在のフレームの予測を取得する方法の例を次に示します。

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

## <a name="see-also"></a>参照

* [Windows 名前空間と HoloLens 用 Unity アプリの使用](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [DirectX でのレンダリング](../native/rendering-in-directx.md)
