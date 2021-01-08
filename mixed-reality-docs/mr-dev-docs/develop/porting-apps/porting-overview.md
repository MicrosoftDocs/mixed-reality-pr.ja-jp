---
title: 移植の概要
description: 既存のアプリケーションを HoloLens および VR 用に Mixed Reality にするためのさまざまな移植オプションの概要を説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: 移植, unity, ミドルウェア, エンジン, UWP, Win32
ms.openlocfilehash: 5a57c73481e80e5ab6fac1bd02b83c5d3dfaabb6
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007492"
---
# <a name="porting-overview"></a><span data-ttu-id="ce4e8-104">移植の概要</span><span class="sxs-lookup"><span data-stu-id="ce4e8-104">Porting overview</span></span>

<span data-ttu-id="ce4e8-105">既存のプロジェクトを混在させて移植またはアップグレードする場合は、アプリが Unity または Unreal のエンジンでビルドされているかどうか、および HoloLens (第1世代) と HoloLens 2、または SteamVR のどちらを対象とするかによって、移植の方法が異なります。</span><span class="sxs-lookup"><span data-stu-id="ce4e8-105">When it comes to porting or upgrading your existing projects for Mixed Reality, your porting journey depends on whether your app is built with Unity or Unreal Engine, and targets HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="ce4e8-106">この概要ページには、各プラットフォームとデバイスの現在の推奨事項が含まれています。これらのプロセスが常に変化しているため、必ず確認してください。</span><span class="sxs-lookup"><span data-stu-id="ce4e8-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="ce4e8-107">まず、 [Unity](#unity) と [unreal](#unreal) の推奨事項のいずれかに基づいてプロジェクトターゲットを設定し、次に1つ以上の移植シナリオに従います。</span><span class="sxs-lookup"><span data-stu-id="ce4e8-107">First, set up your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="ce4e8-108">HoloLens (第1世代) から HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ce4e8-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="ce4e8-109">Windows Mixed Reality ヘッドセット</span><span class="sxs-lookup"><span data-stu-id="ce4e8-109">Windows Mixed Reality headsets</span></span>](#windows-mixed-reality-headsets)
- [<span data-ttu-id="ce4e8-110">SteamVR アプリ</span><span class="sxs-lookup"><span data-stu-id="ce4e8-110">SteamVR apps</span></span>](#steamvr-applications)
- [<span data-ttu-id="ce4e8-111">2D UWP アプリ</span><span class="sxs-lookup"><span data-stu-id="ce4e8-111">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="ce4e8-112">推奨されるプロジェクトターゲット</span><span class="sxs-lookup"><span data-stu-id="ce4e8-112">Recommended project targets</span></span>

<span data-ttu-id="ce4e8-113">アプリを別のターゲットデバイスに移植するかどうかにかかわらず、プロジェクトを最新の状態に保つことが重要です。</span><span class="sxs-lookup"><span data-stu-id="ce4e8-113">It's important to keep your projects up to date, whether your porting an app to another target device.</span></span> <span data-ttu-id="ce4e8-114">現在の推奨事項については、以下に示すエンジンベースのリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce4e8-114">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="ce4e8-115">Unity</span><span class="sxs-lookup"><span data-stu-id="ce4e8-115">Unity</span></span>

<span data-ttu-id="ce4e8-116">Unity を Mixed Reality で開発するための現在の推奨事項は **、従来の XR パッケージを使用した unity 2019 LTS** です。</span><span class="sxs-lookup"><span data-stu-id="ce4e8-116">Our current recommendation for Unity development with Mixed Reality is **Unity 2019 LTS using the Legacy XR package**.</span></span> <span data-ttu-id="ce4e8-117">プロジェクトで Mixed Reality Toolkit を使用している場合は、最新バージョン (現在は **Mrtk-Unity 2.5**) であることを再度確認します。</span><span class="sxs-lookup"><span data-stu-id="ce4e8-117">If your project uses the Mixed Reality Toolkit, double-check that you're on the latest version, which is currently **MRTK-Unity 2.5**.</span></span>

> [!CAUTION]
> <span data-ttu-id="ce4e8-118">XR SDK はこのバージョンの Unity で使用できますが、現在、Azure 空間アンカーはこのセットアップと互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="ce4e8-118">While the XR SDK is available with this version of Unity, Azure Spatial Anchors is not currently compatible with this setup.</span></span> <span data-ttu-id="ce4e8-119">この推奨事項は、Unity 用 Azure 空間アンカーパッケージの今後のリリースで更新されます。</span><span class="sxs-lookup"><span data-stu-id="ce4e8-119">This recommendation will be updated with a future release of the Azure Spatial Anchors package for Unity.</span></span> 
> 
> * <span data-ttu-id="ce4e8-120">Azure 空間アンカーが不要な場合は、 [XR 用に Unity プロジェクトを構成](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) し、 [MRTK と XR SDK を使っ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html)てみることができます。</span><span class="sxs-lookup"><span data-stu-id="ce4e8-120">If you don't need Azure Spatial Anchors, you can [configure your Unity project for XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) and [get started with MRTK and XR SDK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html).</span></span>
> 
> * <span data-ttu-id="ce4e8-121">現在プロジェクトで XR SDK を使用していて、Azure 空間アンカーを使用する場合は、XR SDK をアンインストールし、レガシ XR パッケージを再インストールしてプロジェクト設定を元に戻します。</span><span class="sxs-lookup"><span data-stu-id="ce4e8-121">If you're currently using the XR SDK in your project and want to use Azure Spatial Anchors, uninstall XR SDK and reinstall the Legacy XR package to revert your project settings.</span></span>


### <a name="unreal"></a><span data-ttu-id="ce4e8-122">Unreal</span><span class="sxs-lookup"><span data-stu-id="ce4e8-122">Unreal</span></span> 

<span data-ttu-id="ce4e8-123">Mixed Reality での Unreal development の現在の推奨事項は、 **Unreal Engine 4.26** です。</span><span class="sxs-lookup"><span data-stu-id="ce4e8-123">Our current recommendation for Unreal development with Mixed Reality is **Unreal Engine 4.26**.</span></span> <span data-ttu-id="ce4e8-124">プロジェクトで Mixed Reality Toolkit UX ツールが使用されている場合は、最新バージョン (現在は **Uxt 0.10**) を使用していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ce4e8-124">If your project uses the Mixed Reality Toolkit UX Tools, make sure you're using the latest version, which is currently **UXT 0.10**.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="ce4e8-125">移植のシナリオ</span><span class="sxs-lookup"><span data-stu-id="ce4e8-125">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="ce4e8-126">HoloLens (第1世代) Unity アプリから HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ce4e8-126">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="ce4e8-127">HoloLens 2 に移植する既存の HoloLens (第1世代) Unity アプリケーションがある場合は、 [hololens 移植](../unity/mrtk-porting-guide.md)に関する記事の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="ce4e8-127">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](../unity/mrtk-porting-guide.md).</span></span>

### <a name="windows-mixed-reality-headsets"></a><span data-ttu-id="ce4e8-128">Windows Mixed Reality ヘッドセット</span><span class="sxs-lookup"><span data-stu-id="ce4e8-128">Windows Mixed Reality headsets</span></span>

<span data-ttu-id="ce4e8-129">Oculus Rift や HP リバーブ G2 などの他のデバイス用にコンテンツを構築している場合は、ベンダー固有の VR Sdk および可能性のある入力マッピング Api を再ターゲットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce4e8-129">If you've built content for other devices, such as the Oculus Rift or HP Reverb G2, you'll need to retarget vendor-specific VR SDKs and potentially input-mapping APIs.</span></span> <span data-ttu-id="ce4e8-130">Unity と Unreal の両方の移植のシナリオについては、 [イマーシブアプリの移植ガイド](porting-guides.md)に記載されています。</span><span class="sxs-lookup"><span data-stu-id="ce4e8-130">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

### <a name="steamvr-applications"></a><span data-ttu-id="ce4e8-131">SteamVR アプリケーション</span><span class="sxs-lookup"><span data-stu-id="ce4e8-131">SteamVR applications</span></span>

<span data-ttu-id="ce4e8-132">Windows Mixed Reality ヘッドセット用に更新する SteamVR エクスペリエンスについては、 [steamvr 更新ガイド](updating-your-steamvr-application-for-windows-mixed-reality.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce4e8-132">For any SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="ce4e8-133">2D ユニバーサル Windows アプリケーション</span><span class="sxs-lookup"><span data-stu-id="ce4e8-133">2D Universal Windows applications</span></span>

<span data-ttu-id="ce4e8-134">Windows Mixed Reality のイマーシブヘッドセットまたは HoloLens に移植する既存の 2D UWP アプリがある場合は、「 [Windows Mixed reality 向けの 2D uwp アプリの移植」の](building-2d-apps.md) 手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="ce4e8-134">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) instructions.</span></span>

