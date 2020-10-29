---
title: HoloLens 用 Unity を使用した WinRT Api
description: HoloLens の Unity プロジェクトで WinRT Api (Windows 名前空間) を使用する方法について説明します。
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、WinRT、windows mixed reality、API、チュートリアル
ms.openlocfilehash: 80f950d7571a936e93eb08490ad83dbb34a50b3a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91687255"
---
# <a name="winrt-apis-with-unity-for-hololens"></a><span data-ttu-id="d5d89-104">HoloLens 用 Unity を使用した WinRT Api</span><span class="sxs-lookup"><span data-stu-id="d5d89-104">WinRT APIs with Unity for HoloLens</span></span>

<span data-ttu-id="d5d89-105">このページでは、HoloLens の Unity プロジェクトで WinRT Api を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d5d89-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="mixed-reality-apis"></a><span data-ttu-id="d5d89-106">Mixed Reality Api</span><span class="sxs-lookup"><span data-stu-id="d5d89-106">Mixed Reality APIs</span></span>

<span data-ttu-id="d5d89-107">Windows SDK のサブセットが混在している .NET Standard 2.0 互換性のある投影で使用できるようになりました。これは、プリプロセッサディレクティブなしでプロジェクトで使用できます。</span><span class="sxs-lookup"><span data-stu-id="d5d89-107">A Mixed Reality focused subset of the Windows SDK has been made available in a .NET Standard 2.0 compatible projection, which you can use in your project without preprocessor directives.</span></span> <span data-ttu-id="d5d89-108">これには、ほとんどの Api が含まれています。このような名前空間には、後で追加の Api を含めるために拡張されることがあります。</span><span class="sxs-lookup"><span data-stu-id="d5d89-108">This includes most APIs in the Windows.Perception and Windows.UI.Input.Spatial namespaces, and may expand to include additional APIs in the future.</span></span> <span data-ttu-id="d5d89-109">予測された Api は、エディターでの実行中に使用できます。これにより、 [再生モード](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode)を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d5d89-109">The projected APIs can be used while running in the Editor, which enables the use of [Play Mode](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode).</span></span> <span data-ttu-id="d5d89-110">この投影法を使用するには、プロジェクトに次の変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="d5d89-110">To use this projection, make the following modifications to your project:</span></span>

1) <span data-ttu-id="d5d89-111">[Unity 用の nuget](https://github.com/GlitchEnzo/NuGetForUnity)を使用して、 [MixedReality](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT)の nuget パッケージへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="d5d89-111">Add a reference to the [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span>
2) <span data-ttu-id="d5d89-112">名前空間への参照のプレフィックスは `Windows` `Microsoft.` 次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d5d89-112">Prefix references to the `Windows` namespace with `Microsoft.`:</span></span>
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) <span data-ttu-id="d5d89-113">ネイティブポインターキャストを次のものに置き換え `FromNativePtr` ます。</span><span class="sxs-lookup"><span data-stu-id="d5d89-113">Replace native pointer casts with `FromNativePtr`:</span></span>
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="d5d89-114">条件付きで WinRT API 呼び出しを含める</span><span class="sxs-lookup"><span data-stu-id="d5d89-114">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="d5d89-115">また、プリプロセッサディレクティブを使用して、ユニバーサル Windows プラットフォームと Xbox One プラットフォーム用に構築された Unity プロジェクトに対して WinRT Api を活用することもできます。WinRT Api を対象とする Unity スクリプトで作成するすべてのコードは、それらのビルドに対して条件付きで含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5d89-115">Alternatively, WinRT APIs can be leveraged for Unity projects built for the Universal Windows Platform and Xbox One platform by using preprocessor directives; any code that you write in Unity scripts that target WinRT APIs must be conditionally included for only those builds.</span></span> 

<span data-ttu-id="d5d89-116">これは、Unity の2つの手順で行うことができます。</span><span class="sxs-lookup"><span data-stu-id="d5d89-116">This can be done via two steps in Unity:</span></span>
1) <span data-ttu-id="d5d89-117">プレーヤーの設定で、API 互換性レベルを **.net 4.6** または **.NET Standard 2.0** に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5d89-117">API compatibility level must be set to **.NET 4.6** or **.NET Standard 2.0** in the player settings</span></span>
    - <span data-ttu-id="d5d89-118">**編集**  > **プロジェクトの設定**  > **プレーヤー**  > **構成**  > **Api の互換性レベル** を **.net 4.6** または **.NET Standard 2.0** に</span><span class="sxs-lookup"><span data-stu-id="d5d89-118">**Edit** > **Project Settings** > **Player** > **Configuration** > **Api Compatibility Level** to **.NET 4.6** or **.NET Standard 2.0**</span></span>
2) <span data-ttu-id="d5d89-119">プリプロセッサディレクティブ **ENABLE_WINMD_SUPPORT** は、WinRT を利用したコードをラップする必要があります</span><span class="sxs-lookup"><span data-stu-id="d5d89-119">The preprocessor directive **ENABLE_WINMD_SUPPORT** must be wrapped around any WinRT-leveraged code</span></span>

<span data-ttu-id="d5d89-120">次のコードスニペットは、 [C# スクリプトのユニバーサル Windows プラットフォーム: WINRT API](https://docs.unity3d.com/Manual/windowsstore-scripts.html)の Unity 手動ページから抜粋したものです。</span><span class="sxs-lookup"><span data-stu-id="d5d89-120">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](https://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="d5d89-121">この例では、広告 ID が返されますが、UWP と Xbox One のみがビルドされます。</span><span class="sxs-lookup"><span data-stu-id="d5d89-121">In this example, an advertising ID is returned, but only on UWP and Xbox One builds:</span></span>

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="d5d89-122">Unity C# プロジェクトでスクリプトを編集する</span><span class="sxs-lookup"><span data-stu-id="d5d89-122">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="d5d89-123">Unity エディターでスクリプトをダブルクリックすると、既定ではエディタープロジェクトでスクリプトが起動されます。</span><span class="sxs-lookup"><span data-stu-id="d5d89-123">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="d5d89-124">Visual Studio プロジェクトで Windows ランタイムが参照されていないため、WinRT Api は不明であるように見えます。</span><span class="sxs-lookup"><span data-stu-id="d5d89-124">The WinRT APIs will appear to be unknown because the Visual Studio project does not reference the Windows Runtime.</span></span> <span data-ttu-id="d5d89-125">さらに、 **ENABLE_WINMD_SUPPORT** ディレクティブは未定義になり、 *#if* ラップされたコードは、UWP Visual Studio ソリューションにプロジェクトをビルドするまで無視されます。</span><span class="sxs-lookup"><span data-stu-id="d5d89-125">Further, the **ENABLE_WINMD_SUPPORT** directive will be undefined and any *#if* wrapped code will be ignored until you build your project into a UWP Visual Studio solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="d5d89-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5d89-126">See also</span></span>
* [<span data-ttu-id="d5d89-127">Unity Visual Studio ソリューションのエクスポートとビルド</span><span class="sxs-lookup"><span data-stu-id="d5d89-127">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="d5d89-128">Unity のサポート Windows ランタイム</span><span class="sxs-lookup"><span data-stu-id="d5d89-128">Windows Runtime Support Unity</span></span>](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)
