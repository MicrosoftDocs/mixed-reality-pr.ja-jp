---
title: HoloLens 用 Unity を使用した WinRT Api
description: HoloLens の Unity プロジェクトで WinRT Api (Windows 名前空間) を使用する方法について説明します。
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, windows mixed reality, API, チュートリアル, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実ヘッドセット, Mixed Reality Api
ms.openlocfilehash: ff12df7eb41350fe1f842b3450f3532e4ab8ffa1
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010583"
---
# <a name="winrt-apis-with-unity-for-hololens"></a>HoloLens 用 Unity を使用した WinRT Api

このページでは、HoloLens の Unity プロジェクトで WinRT Api を使用する方法について説明します。

## <a name="mixed-reality-apis"></a>Mixed Reality Api

Windows SDK のサブセットが混在している .NET Standard 2.0 互換性のある投影で使用できるようになりました。これは、プリプロセッサディレクティブなしでプロジェクトで使用できます。 Windows のほとんどの Api。 認識と Windows. UI. 空間名前空間が含まれており、将来的に追加の Api を含むように拡張される場合があります。 予測された Api は、エディターでの実行中に使用できます。これにより、 [再生モード](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode)を使用できるようになります。 この投影法を使用するには、プロジェクトに次の変更を加えます。

1) [Unity 用の nuget](https://github.com/GlitchEnzo/NuGetForUnity)を使用して、 [MixedReality](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT)の nuget パッケージへの参照を追加します。
2) 名前空間への参照のプレフィックスは `Windows` `Microsoft.` 次のとおりです。
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) ネイティブポインターキャストを次のものに置き換え `FromNativePtr` ます。
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a>条件付きで WinRT API 呼び出しを含める

また、プリプロセッサディレクティブを使用して、ユニバーサル Windows プラットフォームおよび Xbox One プラットフォーム用に構築された Unity プロジェクトで WinRT Api を使用することもできます。 WinRT Api を対象とする Unity スクリプトで作成するすべてのコードは、それらのビルドに対して条件付きで含める必要があります。 

これは、Unity の2つの手順で行うことができます。
1) プレーヤーの設定で、API 互換性レベルを **.net 4.6** または **.NET Standard 2.0** に設定する必要があります。
    - **編集**  > **プロジェクトの設定**  > **プレーヤー**  > **構成**  > **Api の互換性レベル** を **.net 4.6** または **.NET Standard 2.0** に
2) プリプロセッサディレクティブ **ENABLE_WINMD_SUPPORT** は、WinRT を利用したコードをラップする必要があります

次のコードスニペットは、 [C# スクリプトのユニバーサル Windows プラットフォーム: WINRT API](https://docs.unity3d.com/Manual/windowsstore-scripts.html)の Unity 手動ページから抜粋したものです。 この例では、広告 ID が返されますが、UWP と Xbox One のみがビルドされます。

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if ENABLE_WINMD_SUPPORT
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Unity C# プロジェクトでスクリプトを編集する

Unity エディターでスクリプトをダブルクリックすると、既定ではエディタープロジェクトでスクリプトが起動されます。 Visual Studio プロジェクトで Windows ランタイムが参照されていないため、WinRT Api は不明であるように見えます。 **ENABLE_WINMD_SUPPORT** ディレクティブは定義されておらず、 *#if* ラップされたコードはすべて、UWP Visual Studio ソリューションにプロジェクトをビルドするまで無視されます。

## <a name="see-also"></a>関連項目
* [Unity Visual Studio ソリューションのエクスポートとビルド](exporting-and-building-a-unity-visual-studio-solution.md)
* [Unity のサポート Windows ランタイム](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)
