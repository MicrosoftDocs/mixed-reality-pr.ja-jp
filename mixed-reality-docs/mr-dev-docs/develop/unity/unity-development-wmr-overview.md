---
title: VR 向けの Unity の開発
description: VR と Windows Mixed Reality イマーシブ ヘッドセットを対象とする Unity での Mixed Reality アプリの構築の概要。
author: hferrone
ms.author: kurtie
ms.date: 12/11/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, Mixed Reality, 開発, 作業の開始, 新しいプロジェクト, 移植, 機能, カメラ, シミュレーション, エミュレーション, ドキュメント, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, 仮想現実とは, 拡張現実とは, MRTK, Mixed Reality Toolkit, 音声入力, 場所を特定できるカメラ, エミュレーター, Azure, チュートリアル
ms.openlocfilehash: edd75def71ad31a1d29a480d0b2a7f7ffbd8c037
ms.sourcegitcommit: be7473bbebc1872d8c9df6f2da837efd3279dee6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226431"
---
# <a name="unity-development-for-vr-and-windows-mixed-reality"></a><span data-ttu-id="6ce85-104">VR と Windows Mixed Reality 向けの Unity 開発</span><span class="sxs-lookup"><span data-stu-id="6ce85-104">Unity development for VR and Windows Mixed Reality</span></span>

![Unity のバナー ロゴ](../images/unity_logo_banner.png)

<span data-ttu-id="6ce85-106">Unity を初めて使用する場合は、続行する前に、Unity Learn プラットフォームで初級レベルの[チュートリアル](https://unity3d.com/learn/tutorials)を確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6ce85-106">If you're brand new to Unity, we recommend that you explore the beginner level [tutorials](https://unity3d.com/learn/tutorials) on the Unity Learn platform before continuing.</span></span> <span data-ttu-id="6ce85-107">また、[Unity Mixed Reality フォーラム](https://forum.unity3d.com/forums/hololens.102/)にアクセスして、Mixed Reality アプリを構築しているオンライン コミュニティに参加することもお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6ce85-107">It's also a good idea to visit the [Unity Mixed Reality forums](https://forum.unity3d.com/forums/hololens.102/) to engage with the online community building mixed reality apps.</span></span> <span data-ttu-id="6ce85-108">想像を超えたすばらしい資産やソリューションを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="6ce85-108">You never know what cool assets or solutions you might find out in the wild.</span></span> <span data-ttu-id="6ce85-109">MRTK の使用を開始する準備ができたら、次の開発チェックポイントに進んでください。</span><span class="sxs-lookup"><span data-stu-id="6ce85-109">When you're ready to get started with MRTK head to the development checkpoints below!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6ce85-110">既存の Unity プロジェクトを Windows Mixed Reality イマーシブ ヘッドセットに移植したい場合は、 **[移植ガイド](../porting-apps/porting-overview.md)** を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ce85-110">Take a look at our **[porting guides](../porting-apps/porting-overview.md)** if you have an existing Unity project that you want to bring over to a Windows Mixed Reality immersive headset.</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="6ce85-111">開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="6ce85-111">Development checkpoints</span></span>

<span data-ttu-id="6ce85-112">次のチェックポイントを使用して、Unity のゲームやアプリケーションを Mixed Reality の世界に移植することができます。</span><span class="sxs-lookup"><span data-stu-id="6ce85-112">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span> 

### <a name="1-getting-started"></a><span data-ttu-id="6ce85-113">1.はじめに</span><span class="sxs-lookup"><span data-stu-id="6ce85-113">1. Getting started</span></span>

<span data-ttu-id="6ce85-114">Unity には、Windows Mixed Reality と VR の開発用に手動で変更する必要がある小さな設定のセットがあります。</span><span class="sxs-lookup"><span data-stu-id="6ce85-114">There are a small set of Unity settings you'll need to manually change for Windows Mixed Reality and VR developoment.</span></span> <span data-ttu-id="6ce85-115">これらは、プロジェクトごととシーンごとの 2 つのカテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="6ce85-115">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="6ce85-116">このセクションが済むと、ツールとプロジェクトの設定は独自のアプリの作成を始められるようになっています。</span><span class="sxs-lookup"><span data-stu-id="6ce85-116">By the end of this section, you'll have the tools and project settings to start creating your own apps!</span></span>

|  <span data-ttu-id="6ce85-117">Checkpoint</span><span class="sxs-lookup"><span data-stu-id="6ce85-117">Checkpoint</span></span>  |  <span data-ttu-id="6ce85-118">結果</span><span class="sxs-lookup"><span data-stu-id="6ce85-118">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="6ce85-119">最新のツールをインストールする</span><span class="sxs-lookup"><span data-stu-id="6ce85-119">Install the latest tools</span></span>](../install-the-tools.md) | <span data-ttu-id="6ce85-120">最新の Unity パッケージをダウンロードしてインストールし、Mixed Reality 用のプロジェクトをセットアップできます</span><span class="sxs-lookup"><span data-stu-id="6ce85-120">Download and install the latest Unity package and setup your project for mixed reality</span></span> |
| [<span data-ttu-id="6ce85-121">WMR 用のプロジェクトの構成</span><span class="sxs-lookup"><span data-stu-id="6ce85-121">Configuring your project for WMR</span></span>](configure-unity-project.md) | <span data-ttu-id="6ce85-122">ホログラフィックおよび VR ディスプレイ デバイスにデジタル コンテンツをレンダリングするアプリケーションを構築する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="6ce85-122">Learn how to build applications that render digital content on holographic and VR display devices</span></span> |

### <a name="2-core-building-blocks"></a><span data-ttu-id="6ce85-123">2. コア構成要素</span><span class="sxs-lookup"><span data-stu-id="6ce85-123">2. Core building blocks</span></span>

<span data-ttu-id="6ce85-124">新しいイマーシブ プロジェクトを開始した後は、イマーシブ アプリを開発するための基本的な構成要素がいくつか必要になります。</span><span class="sxs-lookup"><span data-stu-id="6ce85-124">After starting a new immersive project, you'll need some basic building blocks to develop immersive apps.</span></span> <span data-ttu-id="6ce85-125">Mixed Reality アプリケーションのコアな構成要素はすべて、他の Unity API と一貫した手法で公開されています。</span><span class="sxs-lookup"><span data-stu-id="6ce85-125">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="6ce85-126">そのすべてが一度に必要になるわけではありませんが、事前に確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6ce85-126">You might not need all of them at once, but we recommend exploring early on.</span></span> <span data-ttu-id="6ce85-127">以下のコア構成要素について確認したら、VR プロジェクトに統合できるさまざまな機能が用意されたツールボックスを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="6ce85-127">After diving into the core building blocks listed below, you'll have a toolbox full of features you can integrate into a VR project.</span></span>

[!INCLUDE[](../includes/unity-building-blocks-wmr.md)]

### <a name="3-advanced-features"></a><span data-ttu-id="6ce85-128">3.高度な機能</span><span class="sxs-lookup"><span data-stu-id="6ce85-128">3. Advanced features</span></span>

<span data-ttu-id="6ce85-129">イマーシブ アプリケーションで役割を果たすその他の主要な機能は、Unity API を通じて利用できます。追加のパッケージやセットアップは不要です。</span><span class="sxs-lookup"><span data-stu-id="6ce85-129">Other key features that play a role in immersive applications are available through Unity APIs without any extra packages or setup.</span></span> <span data-ttu-id="6ce85-130">Unity によって提供される高度な機能について確認したら、より高度で複雑な VR アプリを構築することができるようになります。</span><span class="sxs-lookup"><span data-stu-id="6ce85-130">After diving into the more advanced capabilities that Unity offers, you'll be able to build deeper, complex VR apps.</span></span>

|  <span data-ttu-id="6ce85-131">機能</span><span class="sxs-lookup"><span data-stu-id="6ce85-131">Feature</span></span>  |  <span data-ttu-id="6ce85-132">機能</span><span class="sxs-lookup"><span data-stu-id="6ce85-132">Capabilities</span></span>  |
| --- | --- |
| [<span data-ttu-id="6ce85-133">追跡の損失</span><span class="sxs-lookup"><span data-stu-id="6ce85-133">Tracking loss</span></span>](tracking-loss-in-unity.md) | <span data-ttu-id="6ce85-134">アプリケーションのワールド空間でデバイスがそれ自体の位置を特定できなくなった場合のシナリオを処理できます</span><span class="sxs-lookup"><span data-stu-id="6ce85-134">Handle scenarios where your device can't locate itself in the applications world space</span></span> |
| [<span data-ttu-id="6ce85-135">キーボード入力</span><span class="sxs-lookup"><span data-stu-id="6ce85-135">Keyboard input</span></span>](keyboard-input-in-unity.md) | <span data-ttu-id="6ce85-136">アプリで、実際のキーボードや Mixed Reality のキーボードから入力を取得できます</span><span class="sxs-lookup"><span data-stu-id="6ce85-136">Get input from real-world and Mixed Reality keyboards in your apps</span></span> |

### <a name="4-deploying-to-a-device-or-emulator"></a><span data-ttu-id="6ce85-137">4.デバイスまたはエミュレーターへのデプロイ</span><span class="sxs-lookup"><span data-stu-id="6ce85-137">4. Deploying to a device or emulator</span></span>

<span data-ttu-id="6ce85-138">ホログラフィック Unity プロジェクトをテストする準備ができたら、次の手順として、Unity Visual Studio ソリューションをエクスポートしてビルドします。</span><span class="sxs-lookup"><span data-stu-id="6ce85-138">Once you've got your holographic Unity project ready for testing, your next step is to export and build a Unity Visual Studio solution.</span></span> <span data-ttu-id="6ce85-139">その VS ソリューションがあれば、実際のデバイスまたはシミュレートされたデバイスでアプリケーションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="6ce85-139">With that VS solution in hand, you can run your application on real or simulated devices.</span></span> <span data-ttu-id="6ce85-140">このセクションの最後まで進めば、開発のニーズに合ったデバイスまたはエミュレーターでアプリケーションをデプロイできるようになります。</span><span class="sxs-lookup"><span data-stu-id="6ce85-140">By the end of this section, you'll be able to deploy your application on a device or emulator that fits your development needs.</span></span>

* [<span data-ttu-id="6ce85-141">Windows Mixed Reality イマーシブ ヘッドセット</span><span class="sxs-lookup"><span data-stu-id="6ce85-141">Windows Mixed Reality immersive headset</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
* [<span data-ttu-id="6ce85-142">Windows Mixed Reality イマーシブ ヘッドセット シミュレーター</span><span class="sxs-lookup"><span data-stu-id="6ce85-142">Windows Mixed Reality immersive headset simulator</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="whats-next"></a><span data-ttu-id="6ce85-143">次の操作</span><span class="sxs-lookup"><span data-stu-id="6ce85-143">What's next?</span></span>

<span data-ttu-id="6ce85-144">開発者の仕事に終わりはありません。新しいツールや SDK について学ぶ場合は特にこれが当てはまります。</span><span class="sxs-lookup"><span data-stu-id="6ce85-144">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="6ce85-145">以降のセクションでは、既に終えた初級レベルの教材からは一歩進んだ領域について説明します。また、行き詰まった場合に役に立つリソースも紹介します。</span><span class="sxs-lookup"><span data-stu-id="6ce85-145">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="6ce85-146">これらのトピックとリソースは順番に並んでいるわけではないため、お好きなところから自由に参照することができます。</span><span class="sxs-lookup"><span data-stu-id="6ce85-146">Note that these topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="porting"></a><span data-ttu-id="6ce85-147">移植</span><span class="sxs-lookup"><span data-stu-id="6ce85-147">Porting</span></span>

<span data-ttu-id="6ce85-148">移植したい既存のアプリがある場合は、以下の記事を次に確認してください。</span><span class="sxs-lookup"><span data-stu-id="6ce85-148">If you have existing apps that you'd like to port over, the articles listed below are your next stop:</span></span>

* [<span data-ttu-id="6ce85-149">Windows Mixed Reality に VR アプリを移植する</span><span class="sxs-lookup"><span data-stu-id="6ce85-149">Porting VR apps to Windows Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project)
* [<span data-ttu-id="6ce85-150">Windows Mixed Reality 用に SteamVR アプリを更新する</span><span class="sxs-lookup"><span data-stu-id="6ce85-150">Updating SteamVR apps for Windows Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality)

### <a name="additional-resources"></a><span data-ttu-id="6ce85-151">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="6ce85-151">Additional resources</span></span>

<span data-ttu-id="6ce85-152">独自の Mixed Reality の世界に進む前に、さらに以下のドキュメントを参照することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6ce85-152">Before going out into the world of mixed reality on your own, we recommend taking a look at the extra documentation below.</span></span> 

* [<span data-ttu-id="6ce85-153">VR 技術者向けガイド</span><span class="sxs-lookup"><span data-stu-id="6ce85-153">VR enthusiast guide</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/vr-journey)
* [<span data-ttu-id="6ce85-154">Unity 資産ストア</span><span class="sxs-lookup"><span data-stu-id="6ce85-154">Unity Asset Store</span></span>](https://www.assetstore.unity3d.com)

## <a name="see-also"></a><span data-ttu-id="6ce85-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ce85-155">See also</span></span> 

* [<span data-ttu-id="6ce85-156">Unity で推奨される設定</span><span class="sxs-lookup"><span data-stu-id="6ce85-156">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="6ce85-157">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="6ce85-157">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="6ce85-158">Unity Visual Studio ソリューションのエクスポートとビルド</span><span class="sxs-lookup"><span data-stu-id="6ce85-158">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="6ce85-159">Unity と Visual Studio を使用するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="6ce85-159">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
