---
title: Unreal での空間オーディオ
description: Unreal エンジン用の空間オーディオ プラグインの詳細について学習します。
author: hferrone
ms.author: v-hferrone
ms.date: 06/15/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, ストリーミング, リモート処理, Mixed Reality, 開発, 入門, 機能, 新しいプロジェクト, エミュレーター, ドキュメント, ガイド, 特徴, ホログラム, ゲームの開発, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, 空間オーディオ
ms.openlocfilehash: 25fa60b4e55ec0f3bd0875ad88834981d198f7f5
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679801"
---
# <a name="spatial-audio-in-unreal"></a><span data-ttu-id="7613e-104">Unreal での空間オーディオ</span><span class="sxs-lookup"><span data-stu-id="7613e-104">Spatial Audio in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="7613e-105">概要</span><span class="sxs-lookup"><span data-stu-id="7613e-105">Overview</span></span>

<span data-ttu-id="7613e-106">視覚とは異なり、人間は 360 度のサラウンド サウンドを聞き取っています。</span><span class="sxs-lookup"><span data-stu-id="7613e-106">Unlike vision, humans hear in 360 degree surround sound.</span></span> <span data-ttu-id="7613e-107">立体音響では、人間の聴覚のしくみをエミュレートし、ワールド空間でサウンドの位置を識別するのに必要なキューを提供しています。</span><span class="sxs-lookup"><span data-stu-id="7613e-107">Spatial sound emulates how human hearing works, providing the cues needed to identify sound locations in world-space.</span></span> <span data-ttu-id="7613e-108">Mixed Reality アプリケーションに立体音響を追加すると、ユーザーが経験する没入感のレベルを向上できます。</span><span class="sxs-lookup"><span data-stu-id="7613e-108">When you add spatial sound in your mixed reality applications, you're enhancing the level of immersion your users experience.</span></span>  

<span data-ttu-id="7613e-109">高品質の立体音響処理は複雑であるため、HoloLens 2 には、それらのサウンド オブジェクトを処理するための専用ハードウェアが付属しています。</span><span class="sxs-lookup"><span data-stu-id="7613e-109">High quality spatial sound processing is complex, so the HoloLens 2 comes with dedicated hardware for processing those sound objects.</span></span>  <span data-ttu-id="7613e-110">このハードウェア処理のサポートを利用するには、Unreal プロジェクトに **MicrosoftSpatialSound** プラグインをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7613e-110">Before you can access this hardware processing support, you'll need to install the **MicrosoftSpatialSound** plugin in your Unreal project.</span></span> <span data-ttu-id="7613e-111">この記事では、そのプラグインのインストールと構成について説明し、Unreal Engine で立体音響を使用するのに役立つさらに詳細なリソースを紹介します。</span><span class="sxs-lookup"><span data-stu-id="7613e-111">This article will walk you through the installation and configuration of that plugin and point you towards more in-depth resources for using spatial sound in the Unreal engine.</span></span>

## <a name="installing-the-microsoft-spatial-sound-plugin"></a><span data-ttu-id="7613e-112">Microsoft 立体音響プラグインのインストール</span><span class="sxs-lookup"><span data-stu-id="7613e-112">Installing the Microsoft Spatial Sound plugin</span></span>

<span data-ttu-id="7613e-113">立体音響をプロジェクトに追加するには、最初に Microsoft 立体音響プラグインをインストールします。このプラグインは次の手順で見つけられます。</span><span class="sxs-lookup"><span data-stu-id="7613e-113">The first step to adding spatial sound to your project is installing the Microsoft Spatial Sound plugin, which you can find by:</span></span>

1. <span data-ttu-id="7613e-114">**[編集] > [プラグイン]** の順にクリックし、検索ボックスで「**MicrosoftSpatialSound**」を検索します。</span><span class="sxs-lookup"><span data-stu-id="7613e-114">Clicking **Edit > Plugins** and searching for **MicrosoftSpatialSound** in the search box.</span></span>
2. <span data-ttu-id="7613e-115">**MicrosoftSpatialSound** プラグインの **[有効]** チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="7613e-115">Selecting the **Enabled** checkbox in the **MicrosoftSpatialSound** plugin.</span></span>
3. <span data-ttu-id="7613e-116">[プラグイン] ページの **[今すぐ再起動]** を選択して、Unreal エディターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="7613e-116">Restarting the Unreal Editor by selecting **Restart Now** from the plugins page.</span></span>

> [!NOTE]
> <span data-ttu-id="7613e-117">まだインストールしていない場合は、**Microsoft Windows Mixed Reality** プラグインと **HoloLens** プラグインをインストールする必要があります。インストールの手順については、Unreal チュートリアル シリーズの **[プロジェクトの初期化](tutorials/unreal-uxt-ch2.md)** に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7613e-117">If you haven't already, you'll need to install the **Microsoft Windows Mixed Reality** and **HoloLens** plugins by following the instructions in the **[Initializing your project](tutorials/unreal-uxt-ch2.md)** section of our Unreal tutorial series.</span></span>

![Unreal の空間オーディオ プラグイン](images/unreal-spatial-audio-img-01.png)

<span data-ttu-id="7613e-119">エディターが再起動すると、プロジェクトの設定はすべて完了です。</span><span class="sxs-lookup"><span data-stu-id="7613e-119">Once the editor restarts, your project is all set!</span></span>


## <a name="setting-the-spatialization-plugin-for-hololens-2-platform"></a><span data-ttu-id="7613e-120">HoloLens 2 プラットフォーム用の空間化プラグインの設定</span><span class="sxs-lookup"><span data-stu-id="7613e-120">Setting the spatialization plugin for HoloLens 2 platform</span></span>
<span data-ttu-id="7613e-121">空間化プラグインの構成は、プラットフォームごとに行います。</span><span class="sxs-lookup"><span data-stu-id="7613e-121">Configuring the spatialization plugin is done on a per-platform basis.</span></span>  <span data-ttu-id="7613e-122">HoloLens 2 用の Microsoft 立体音響プラグインは、次の手順で有効にできます。</span><span class="sxs-lookup"><span data-stu-id="7613e-122">You can enable the Microsoft Spatial Sound plugin for the HoloLens 2 by:</span></span>
1. <span data-ttu-id="7613e-123">**[編集] > [プロジェクトの設定]** の順に選択し、 **[プラットフォーム]** までスクロールして、 **[HoloLens]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7613e-123">Selecting **Edit > Project Settings**, scrolling to **Platforms** and clicking **HoloLens**.</span></span>
2. <span data-ttu-id="7613e-124">**[オーディオ]** プロパティを展開し、 **[Spatialization Plugin]\(空間化プラグイン\)** フィールドを **[Microsoft 立体音響]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="7613e-124">Expanding the **Audio** properties and setting the **Spatialization Plugin** field to **Microsoft Spatial Sound**.</span></span>

![HoloLens プラットフォーム用の空間化プラグイン](images/unreal-spatial-audio-img-02.png)

<span data-ttu-id="7613e-126">デスクトップ PC の Unreal エディターでアプリケーションをプレビューする場合は、**Windows** プラットフォームに対して上記の手順を繰り返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="7613e-126">If you're going to be previewing your application in the Unreal editor on a desktop PC, you'll need to repeat the above steps for the **Windows** platform:</span></span>

![Windows プラットフォーム用の空間プラグイン](images/unreal-spatial-audio-img-05.png)

## <a name="enabling-spatial-audio-on-your-workstation"></a><span data-ttu-id="7613e-128">ワークステーションでの空間オーディオの有効化</span><span class="sxs-lookup"><span data-stu-id="7613e-128">Enabling spatial audio on your workstation</span></span>
<span data-ttu-id="7613e-129">空間オーディオは、デスクトップ バージョンの Windows では既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="7613e-129">Spatial audio is disabled by default on desktop versions of Windows.</span></span> <span data-ttu-id="7613e-130">次の手順で空間オーディオを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="7613e-130">You can enable it by:</span></span>
* <span data-ttu-id="7613e-131">タスク バーの **[ボリューム]** アイコンを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="7613e-131">Right-clicking on the **volume** icon in the task bar.</span></span>
    + <span data-ttu-id="7613e-132">**[立体音響] -> [Windows Sonic for Headphones]** の順に選択することで、HoloLens 2 で聞こえる内容を最適に再生できるようになります。</span><span class="sxs-lookup"><span data-stu-id="7613e-132">Choose **Spatial sound -> Windows Sonic for Headphones** to get the best representation of what you'll hear on HoloLens 2.</span></span>

![空間化プラグイン](images/unreal-spatial-audio-img-04.png)

> [!NOTE]
><span data-ttu-id="7613e-134">この設定は、プロジェクトを Unreal エディターでテストする場合にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="7613e-134">This setting is only required if you plan to test your project in the Unreal editor.</span></span>

## <a name="creating-attenuation-objects"></a><span data-ttu-id="7613e-135">減衰オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="7613e-135">Creating Attenuation objects</span></span>
<span data-ttu-id="7613e-136">必要なプラグインのインストールと構成を完了した後に、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="7613e-136">After you've installed and configured the necessary plugins:</span></span>
1. <span data-ttu-id="7613e-137">**[Place Actors]\(アクターの配置\)** ウィンドウで **[Ambient Sound]\(アンビエント サウンド\)** アクターを検索し、 **[シーン]** ウィンドウにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7613e-137">Search for an **Ambient Sound** actor in the **Place Actors** window and drag it into the **Scene** window.</span></span>

![アンビエント サウンド アクターの追加](images/unreal-spatial-audio-img-07.png)

2. <span data-ttu-id="7613e-139">**アンビエント サウンド** アクターを、シーン内のビジュアル要素の子に設定します。</span><span class="sxs-lookup"><span data-stu-id="7613e-139">Make the **Ambient Sound** actor a child of a visual element in your scene.</span></span>
    * <span data-ttu-id="7613e-140">アンビエント サウンド アクターには、既定ではビジュアル表現がありません。このため、シーン内の配置された場所から音声が聞こえるだけになります。</span><span class="sxs-lookup"><span data-stu-id="7613e-140">An Ambient Sound actor doesn't have any visual representation by default, so you'll only hear a sound from its position in the scene.</span></span> <span data-ttu-id="7613e-141">このアクターをビジュアル要素にアタッチすると、他の資産と同様にアクターを表示し、移動することができます。</span><span class="sxs-lookup"><span data-stu-id="7613e-141">Attaching it to a visual element let's you see and move the actor like any other asset.</span></span>

3.  <span data-ttu-id="7613e-142">**コンテンツ ブラウザー** を右クリックし、 **[Create Advanced Asset]\(高度な資産の作成\) -> [サウンド] -> [Sound Attenuation]\(サウンドの減衰\)** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="7613e-142">Right-click on the **Content Browser** and selecting **Create Advanced Asset -> Sounds -> Sound Attenuation**:</span></span>

![サウンドの減衰資産の作成](images/unreal-spatial-audio-img-06.png)

4. <span data-ttu-id="7613e-144">**コンテンツ ブラウザー** ウィンドウで **[Sound Attenuation]\(サウンドの減衰\)** 資産を右クリックし、 **[編集]** オプションを選択して、[プロパティ] ウィンドウを表示します。</span><span class="sxs-lookup"><span data-stu-id="7613e-144">Right-click on the **Sound Attenuation** asset in the **Content Browser** window and select the **Edit** option to bring up the properties window.</span></span>
    * <span data-ttu-id="7613e-145">**[Spatialization Method]\(空間化メソッド\)** を **[Binaural]\(バイノーラル\)** に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="7613e-145">Switch the **Spatialization Method** to **Binaural**.</span></span>

![空間化メソッドの設定](images/unreal-spatial-audio-img-03.png)

5. <span data-ttu-id="7613e-147">**アンビエント サウンド** アクターを選択し、 **[詳細]** パネルの **[減衰]** セクションまで下にスクロールします。</span><span class="sxs-lookup"><span data-stu-id="7613e-147">Select the **Ambient Sound** actor and scroll down to the **Attenuation** section in the **Details** panel.</span></span>
    * <span data-ttu-id="7613e-148">**[減衰設定]** プロパティを、作成した **[Sound Attenuation]\(サウンドの減衰\)** 資産に設定します。</span><span class="sxs-lookup"><span data-stu-id="7613e-148">Set the **Attenuation Settings** property to the **Sound Attenuation** asset you created.</span></span>

![減衰設定の設定](images/unreal-spatial-audio-img-08.png)

6. <span data-ttu-id="7613e-150">アンビエント サウンド アクターの **[サウンド]** プロパティを更新して、使用する SoundAsset ファイルを指定することにより、アンビエント サウンド アクターにアタッチする **サウンド資産** を設定します。</span><span class="sxs-lookup"><span data-stu-id="7613e-150">Set the **Sound Asset** you want to attach to the Ambient Sound actor by updating the **Sound** property of the Ambient Sound actor to specify the SoundAsset file to use.</span></span>

![サウンド資産の設定](images/unreal-spatial-audio-img-09.png)

> [!NOTE]
> <span data-ttu-id="7613e-152">Microsoft 立体音響プラグインを使用して空間化するには、SoundAsset ファイルはモノラルである必要があります。</span><span class="sxs-lookup"><span data-stu-id="7613e-152">The SoundAsset file needs to be mono to be spatialized with the Microsoft Spatial Sound plug-in.</span></span> <span data-ttu-id="7613e-153">次のスクリーンショットに示すように、コンテンツ ブラウザー ウィンドウで資産にカーソルを合わせると、そのサウンド ファイルのプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7613e-153">You can find the sound file properties by hovering over the asset in the Content Browser window as shown in the screenshot below.</span></span>

![新しいサウンドの減衰資産](images/unreal-spatial-audio-img-10.png)

<span data-ttu-id="7613e-155">これらのすべての構成が完了したら、HoloLens 2 の専用ハードウェア オフロードのサポートを使用して、アンビエント サウンドを空間化することができます。</span><span class="sxs-lookup"><span data-stu-id="7613e-155">Once all of this is configured the ambient sound can be spatialized using the dedicated hardware offload support on HoloLens 2.</span></span>

## <a name="configuring-objects-for-spatialization"></a><span data-ttu-id="7613e-156">空間化のためのオブジェクトの構成</span><span class="sxs-lookup"><span data-stu-id="7613e-156">Configuring objects for spatialization</span></span>
<span data-ttu-id="7613e-157">空間オーディオを使用すると、仮想環境でのサウンドの動作を管理することが必要になります。</span><span class="sxs-lookup"><span data-stu-id="7613e-157">Working with spatial audio means you're in charge of managing how sound behaves in a virtual environment.</span></span> <span data-ttu-id="7613e-158">主に必要になるのは、ユーザーが接近すると音が大きくなり、ユーザーが離れると音が静かになるように感じられるサウンド オブジェクトを作成することです。</span><span class="sxs-lookup"><span data-stu-id="7613e-158">Your main focus is creating sound objects that appear louder when the user is close, and quieter when the user is far away.</span></span> <span data-ttu-id="7613e-159">これはサウンドの減衰と呼ばれ、これにより、サウンドが決まった地点に配置されているように感じられるようになります。</span><span class="sxs-lookup"><span data-stu-id="7613e-159">This is referred to as sound attenuation, making sounds appear as if they are positioned in a fixed spot.</span></span>

<span data-ttu-id="7613e-160">すべての減衰オブジェクトには、変更可能な次の設定が用意されています。</span><span class="sxs-lookup"><span data-stu-id="7613e-160">All attenuation objects come with modifiable settings for:</span></span>
* <span data-ttu-id="7613e-161">距離</span><span class="sxs-lookup"><span data-stu-id="7613e-161">Distance</span></span>
* <span data-ttu-id="7613e-162">空間化</span><span class="sxs-lookup"><span data-stu-id="7613e-162">Spatialization</span></span>
* <span data-ttu-id="7613e-163">空気吸収</span><span class="sxs-lookup"><span data-stu-id="7613e-163">Air Absorption</span></span>
* <span data-ttu-id="7613e-164">リスナー フォーカス</span><span class="sxs-lookup"><span data-stu-id="7613e-164">Listener Focus</span></span>
* <span data-ttu-id="7613e-165">リバーブ センド</span><span class="sxs-lookup"><span data-stu-id="7613e-165">Reverb Send</span></span>
* <span data-ttu-id="7613e-166">オクルージョン</span><span class="sxs-lookup"><span data-stu-id="7613e-166">Occlusion</span></span>

<span data-ttu-id="7613e-167">これらの各トピックに関する詳細と実装の仕様については、[Unreal のサウンドの減衰](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7613e-167">[Sound attenuation in Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) has details and implementation specifics on each of these topics.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="7613e-168">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="7613e-168">Next Development Checkpoint</span></span>

<span data-ttu-id="7613e-169">私たちが用意した Unreal 開発チェックポイント体験に従っている場合、読者は MRTK コア構成要素を探索している段階にいます。</span><span class="sxs-lookup"><span data-stu-id="7613e-169">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="7613e-170">ここから、次の構成要素に進むことができます。</span><span class="sxs-lookup"><span data-stu-id="7613e-170">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7613e-171">音声入力</span><span class="sxs-lookup"><span data-stu-id="7613e-171">Voice input</span></span>](unreal-voice-input.md)

<span data-ttu-id="7613e-172">または、Mixed Reality プラットフォームの機能と API に移動します。</span><span class="sxs-lookup"><span data-stu-id="7613e-172">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7613e-173">HoloLens カメラ</span><span class="sxs-lookup"><span data-stu-id="7613e-173">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="7613e-174">いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#2-core-building-blocks)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="7613e-174">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>


## <a name="see-also"></a><span data-ttu-id="7613e-175">関連項目</span><span class="sxs-lookup"><span data-stu-id="7613e-175">See also</span></span>
* [<span data-ttu-id="7613e-176">立体音響</span><span class="sxs-lookup"><span data-stu-id="7613e-176">Spatial Sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound)
* [<span data-ttu-id="7613e-177">立体音響の設計</span><span class="sxs-lookup"><span data-stu-id="7613e-177">Spatial Sound Design</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)
* [<span data-ttu-id="7613e-178">MR 空間 220:立体音響</span><span class="sxs-lookup"><span data-stu-id="7613e-178">MR Spatial 220: Spatial sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/holograms-220)
