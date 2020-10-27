---
title: 移植ガイド
description: 既存のイマーシブアプリケーションを Windows Mixed Reality に移植する手順を説明したチュートリアルです。
author: JBrentJ
ms.author: alexturn
ms.date: 07/07/2020
ms.topic: article
keywords: ポート、移植、unity、ミドルウェア、エンジン、UWP、Win32
ms.openlocfilehash: 9822976ab7dac9ae7567e5f38ca44ceee646d098
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638546"
---
# <a name="porting-guides"></a><span data-ttu-id="9c20e-104">移植ガイド</span><span class="sxs-lookup"><span data-stu-id="9c20e-104">Porting guides</span></span>

<span data-ttu-id="9c20e-105">Windows 10 には、イマーシブおよび holographic ヘッドセットの直接サポートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9c20e-105">Windows 10 includes direct support for immersive and holographic headsets.</span></span> <span data-ttu-id="9c20e-106">Oculus Rift や HTC Naopak など、他のデバイス用にコンテンツを構築した場合は、オペレーティングシステムのプラットフォーム API の上に存在するライブラリに依存関係があります。</span><span class="sxs-lookup"><span data-stu-id="9c20e-106">If you've built content for other devices, such as the Oculus Rift or HTC Vive, these have dependencies on libraries that exist above the operating system's platform API.</span></span> <span data-ttu-id="9c20e-107">既存の Win32 Unity VR アプリを Windows Mixed Reality に導入するには、ベンダー固有の VR Sdk を Unity のクロスベンダ VR Api に再ターゲット使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c20e-107">Bringing existing Win32 Unity VR apps over to Windows Mixed Reality involves retargeting usage of vendor-specific VR SDKs to Unity's cross-vendor VR APIs.</span></span>

## <a name="porting-overview"></a><span data-ttu-id="9c20e-108">移植の概要</span><span class="sxs-lookup"><span data-stu-id="9c20e-108">Porting overview</span></span>

<span data-ttu-id="9c20e-109">大まかに言えば、既存のコンテンツの移植には次の手順が関係します。</span><span class="sxs-lookup"><span data-stu-id="9c20e-109">At a high level, the following steps are involved in porting existing content:</span></span>
1. <span data-ttu-id="9c20e-110">**PC で Windows 10 の秋の作成者の更新プログラム (16299) が実行されていることを確認します。**</span><span class="sxs-lookup"><span data-stu-id="9c20e-110">**Make sure your PC is running the Windows 10 Fall Creators Update (16299).**</span></span> <span data-ttu-id="9c20e-111">内部からのプレビュービルドを受信することはお勧めできなくなりました。これらのビルドは、mixed reality 開発では最も安定していないためです。</span><span class="sxs-lookup"><span data-stu-id="9c20e-111">We no longer recommend receiving preview builds from the Insider Skip Ahead ring, as those builds won't be the most stable for mixed reality development.</span></span>
2. <span data-ttu-id="9c20e-112">**グラフィックスまたはゲームエンジンの最新バージョンにアップグレードします。**</span><span class="sxs-lookup"><span data-stu-id="9c20e-112">**Upgrade to the latest version of your graphics or game engine.**</span></span> <span data-ttu-id="9c20e-113">ゲームエンジンは、Windows 10 SDK バージョン 10.0.15063.0 (2017 年4月にリリース) 以降をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c20e-113">Game engines will need to support the Windows 10 SDK version 10.0.15063.0 (released in April 2017) or higher.</span></span>
3. <span data-ttu-id="9c20e-114">**任意のミドルウェア、プラグイン、またはコンポーネントをアップグレードします。**</span><span class="sxs-lookup"><span data-stu-id="9c20e-114">**Upgrade any middleware, plug-ins, or components.**</span></span> <span data-ttu-id="9c20e-115">アプリにコンポーネントが含まれている場合は、最新バージョンにアップグレードすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9c20e-115">If your app contains any components, it's a good idea to upgrade to the latest version.</span></span>
4. <span data-ttu-id="9c20e-116">**重複する sdk の依存関係を削除** します。</span><span class="sxs-lookup"><span data-stu-id="9c20e-116">**Remove dependencies on duplicate SDKs** .</span></span> <span data-ttu-id="9c20e-117">コンテンツがターゲットとしているデバイスによっては、その SDK を削除するか条件付きでコンパイルする必要があります (たとえば、SteamVR)。そのため、代わりに Windows Api を対象にすることができます。</span><span class="sxs-lookup"><span data-stu-id="9c20e-117">Depending on which device your content was targeting, you'll need to remove or conditionally compile out that SDK (for example, SteamVR) so you can target the Windows APIs instead.</span></span>
5. <span data-ttu-id="9c20e-118">**ビルドの問題を解決します。**</span><span class="sxs-lookup"><span data-stu-id="9c20e-118">**Work through build issues.**</span></span> <span data-ttu-id="9c20e-119">この時点で、移植の演習は、アプリ、エンジン、およびコンポーネントの依存関係に固有です。</span><span class="sxs-lookup"><span data-stu-id="9c20e-119">At this point, the porting exercise is specific to your app, your engine, and the component dependencies you have.</span></span>

## <a name="common-porting-steps"></a><span data-ttu-id="9c20e-120">一般的な移植手順</span><span class="sxs-lookup"><span data-stu-id="9c20e-120">Common porting steps</span></span>

### <a name="1-make-sure-you-have-the-right-development-hardware"></a><span data-ttu-id="9c20e-121">1. 適切な開発ハードウェアがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9c20e-121">1. Make sure you have the right development hardware</span></span>

<span data-ttu-id="9c20e-122">[ [ツールのインストール](../install-the-tools.md#immersive-vr-headset-requirements) ] ページに、推奨される開発ハードウェアの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c20e-122">The [install the tools](../install-the-tools.md#immersive-vr-headset-requirements) page lists the recommended development hardware.</span></span>

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a><span data-ttu-id="9c20e-123">2. Windows 10 の最新のフライトにアップグレードする</span><span class="sxs-lookup"><span data-stu-id="9c20e-123">2. Upgrade to the latest flight of Windows 10</span></span>

<span data-ttu-id="9c20e-124">Windows Mixed Reality プラットフォームは、まだアクティブな開発中です。</span><span class="sxs-lookup"><span data-stu-id="9c20e-124">The Windows Mixed Reality platform is still under active development.</span></span> <span data-ttu-id="9c20e-125">"Windows Insider Fast" のフライトにアクセスするには [、Windows Insider program に参加](https://insider.windows.com/) することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9c20e-125">We recommend [joining the Windows Insider Program](https://insider.windows.com/) to access the "Windows Insider Fast" flight.</span></span>
1. <span data-ttu-id="9c20e-126">Windows 10 の作成者の[更新プログラム](https://www.microsoft.com/software-download/windows10)をインストールする</span><span class="sxs-lookup"><span data-stu-id="9c20e-126">Install the [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)</span></span>
2. <span data-ttu-id="9c20e-127">Windows Insider プログラムに[参加](https://insider.windows.com/)します。</span><span class="sxs-lookup"><span data-stu-id="9c20e-127">[Join](https://insider.windows.com/) the Windows Insider Program.</span></span>
3. <span data-ttu-id="9c20e-128">[開発者モード](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)を有効にする</span><span class="sxs-lookup"><span data-stu-id="9c20e-128">Enable [Developer Mode](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)</span></span>
4. <span data-ttu-id="9c20e-129">[ **設定 > 更新 & セキュリティ] セクション** で、 [Windows Insider Fast のフライト](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview)に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="9c20e-129">Switch to the [Windows Insider Fast flights](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview) through **Settings > Update & Security Section**</span></span>

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a><span data-ttu-id="9c20e-130">3. Visual Studio の最新のビルドにアップグレードする</span><span class="sxs-lookup"><span data-stu-id="9c20e-130">3. Upgrade to the most recent build of Visual Studio</span></span>
* <span data-ttu-id="9c20e-131">Visual Studio を使用している場合は、最新のビルドにアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="9c20e-131">If you're using Visual Studio then upgrade to the most recent build</span></span>
* <span data-ttu-id="9c20e-132">「Visual Studio 2019 で [のツールページのインストール」を](../install-the-tools.md#installation-checklist) 参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c20e-132">See [Install the tools](../install-the-tools.md#installation-checklist) page under Visual Studio 2019</span></span>

### <a name="4-choose-the-correct-adapter"></a><span data-ttu-id="9c20e-133">4. 正しいアダプターを選択します</span><span class="sxs-lookup"><span data-stu-id="9c20e-133">4. Choose the correct Adapter</span></span>
* <span data-ttu-id="9c20e-134">2つの Gpu を持つ notebook などのシステムでは、 [正しいアダプターをターゲット](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications)にします。</span><span class="sxs-lookup"><span data-stu-id="9c20e-134">In systems like notebooks with two GPUs, [target the correct adapter](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications).</span></span> <span data-ttu-id="9c20e-135">これは、Unity とネイティブ DirectX アプリに適用されます。 ID3D11Device は、明示的に、または暗黙的に (メディアファンデーション) 機能に対して作成されます。</span><span class="sxs-lookup"><span data-stu-id="9c20e-135">This applies to Unity and native DirectX apps where a ID3D11Device is created, either explicitly or implicitly (Media Foundation), for its functionality.</span></span>

## <a name="unity-porting-guidance"></a><span data-ttu-id="9c20e-136">Unity の移植に関するガイダンス</span><span class="sxs-lookup"><span data-stu-id="9c20e-136">Unity porting guidance</span></span>

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a><span data-ttu-id="9c20e-137">Unreal の移植に関するガイダンス</span><span class="sxs-lookup"><span data-stu-id="9c20e-137">Unreal porting guidance</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9c20e-138">HP リバーブ G2 コントローラーを使用している場合は、追加の入力マッピング手順については、こちらの [記事](../unreal/unreal-reverb-g2-controllers.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c20e-138">If you're using HP Reverb G2 controllers, please refer to [this article](../unreal/unreal-reverb-g2-controllers.md) for additional input mapping instructions.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c20e-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c20e-139">See also</span></span>
* [<span data-ttu-id="9c20e-140">Windows Mixed Reality の PC ハードウェアの最小互換性ガイドライン</span><span class="sxs-lookup"><span data-stu-id="9c20e-140">Windows Mixed Reality minimum PC hardware compatibility guidelines</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [<span data-ttu-id="9c20e-141">Mixed Reality のパフォーマンスについて</span><span class="sxs-lookup"><span data-stu-id="9c20e-141">Understanding Performance for Mixed Reality</span></span>](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="9c20e-142">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="9c20e-142">Performance Recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
* [<span data-ttu-id="9c20e-143">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="9c20e-143">Motion controllers</span></span>](../../design/motion-controllers.md)
* [<span data-ttu-id="9c20e-144">Unity でのジェスチャとモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="9c20e-144">Gestures and motion controllers in Unity</span></span>](../unity/gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="9c20e-145">UnityEngine. XR</span><span class="sxs-lookup"><span data-stu-id="9c20e-145">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="9c20e-146">UnityEngine. XR 追跡</span><span class="sxs-lookup"><span data-stu-id="9c20e-146">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="9c20e-147">移植ガイド</span><span class="sxs-lookup"><span data-stu-id="9c20e-147">Porting guides</span></span>](porting-guides.md)