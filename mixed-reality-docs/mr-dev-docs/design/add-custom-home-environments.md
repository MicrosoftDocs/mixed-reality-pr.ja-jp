---
title: 独自のイマーシブ環境を設計する
description: 独自の Windows Mixed Reality ホーム環境を作成する方法について説明します。
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、Home、Custom Environment、地名、崖ハウス、skyloft、user、create、Mixed reality ヘッドセット、windows Mixed reality ヘッドセット、Virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: ca6a41f8388a767b1191ddc3b377822567a603a6
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583301"
---
# <a name="design-your-own-immersive-environments"></a><span data-ttu-id="f736f-104">独自のイマーシブ環境を設計する</span><span class="sxs-lookup"><span data-stu-id="f736f-104">Design your own immersive environments</span></span>

>[!NOTE]
><span data-ttu-id="f736f-105">これは試験段階の機能です。</span><span class="sxs-lookup"><span data-stu-id="f736f-105">This is an experimental feature.</span></span> <span data-ttu-id="f736f-106">試してみてください。しかし、すべてが期待どおりに動作しない場合、驚かれることはありません。</span><span class="sxs-lookup"><span data-stu-id="f736f-106">Give it a try and have fun with it, but don't be surprised if everything doesn't quite work as expected.</span></span> <span data-ttu-id="f736f-107">この機能の有効性を評価し、それを使用することに関心があるので、 [開発者フォーラム](https://forums.hololens.com/categories/custom-home-environments)で、経験 (および発見したバグ) についてご意見をお聞かせください。</span><span class="sxs-lookup"><span data-stu-id="f736f-107">We're evaluating the viability of this feature and interest in using it, so please tell us about your experience (and any bugs you've found) in the [developer forums](https://forums.hololens.com/categories/custom-home-environments).</span></span>

<span data-ttu-id="f736f-108">[Windows 10 April 2018 update](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)以降では、 [windows Mixed Reality ホーム](../discover/navigating-the-windows-mixed-reality-home.md)として使用するカスタム環境を [スタート] メニューの [場所] ピッカーに追加できる実験的な機能が有効になりました。</span><span class="sxs-lookup"><span data-stu-id="f736f-108">Starting with the [Windows 10 April 2018 update](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018), we've enabled an experimental feature that lets you add custom environments to the Places picker (on the Start menu) to use as the [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md).</span></span> <span data-ttu-id="f736f-109">Windows Mixed Reality には、崖ハウスと Skyloft という2つの既定の環境があります。ホームとして選択できます。</span><span class="sxs-lookup"><span data-stu-id="f736f-109">Windows Mixed Reality has two default environments, Cliff House and Skyloft, you can choose as your home.</span></span> <span data-ttu-id="f736f-110">カスタム環境を作成すると、自分で作成したリストを拡張することができます。</span><span class="sxs-lookup"><span data-stu-id="f736f-110">Creating custom environments allows you to expand the list with your own creations.</span></span> <span data-ttu-id="f736f-111">この機能を早期の状態で使用できるようにして、作成者や開発者からの関心を評価しています。</span><span class="sxs-lookup"><span data-stu-id="f736f-111">We're making this feature available in an early state to evaluate interest from creators and developers.</span></span> <span data-ttu-id="f736f-112">さまざまな作成ツールの使用方法について理解を深め、どのような方法で作業するかをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="f736f-112">See what kinds of worlds you create and understand how you work with different authoring tools.</span></span>

<span data-ttu-id="f736f-113">カスタム環境を使用すると、Skyloft が崖家やの場合と同じように、テレ移植、アプリとの対話、およびホログラムの配置が行われます。</span><span class="sxs-lookup"><span data-stu-id="f736f-113">When using a custom environment you'll notice that teleporting, interacting with apps, and placing holograms works just like it does in the Cliff House and Skyloft.</span></span> <span data-ttu-id="f736f-114">Web を fantasy ランドスケープで閲覧したり、ホログラムを使用して futuristic の都市を埋めることができます。可能性は無限です。</span><span class="sxs-lookup"><span data-stu-id="f736f-114">You can browse the web in a fantasy landscape or fill a futuristic city with holograms - the possibilities are endless!</span></span>

## <a name="device-support"></a><span data-ttu-id="f736f-115">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="f736f-115">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f736f-116"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="f736f-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="f736f-117"><a href="/hololens/hololens2-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="f736f-117"><a href="/hololens/hololens2-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="f736f-118"><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="f736f-118"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f736f-119">カスタムホーム環境</span><span class="sxs-lookup"><span data-stu-id="f736f-119">Custom home environments</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="f736f-120">✔️</span><span class="sxs-lookup"><span data-stu-id="f736f-120">✔️</span></span></td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a><span data-ttu-id="f736f-121">サンプル環境を試す</span><span class="sxs-lookup"><span data-stu-id="f736f-121">Trying a sample environment</span></span>

<span data-ttu-id="f736f-122">カスタムホーム環境の独創的な可能性を示すサンプル環境を作成しました。</span><span class="sxs-lookup"><span data-stu-id="f736f-122">We've created a sample environment that shows off some of the creative possibilities of custom home environments.</span></span> <span data-ttu-id="f736f-123">次の手順に従って試してみてください。</span><span class="sxs-lookup"><span data-stu-id="f736f-123">Follow these steps to try it out:</span></span>
1. <span data-ttu-id="f736f-124">[サンプル Fantasy アイランド環境](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (自己解凍形式の実行可能ファイルへのリンクポイント) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="f736f-124">[Download our sample Fantasy Island environment](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (link points to self-extracting executable).</span></span>

    <span data-ttu-id="f736f-125">![Fantasy 島のサンプル環境](images/FantasyLand.jpg)</span><span class="sxs-lookup"><span data-stu-id="f736f-125">![Fantasy Island sample environment](images/FantasyLand.jpg)</span></span><br>
    <span data-ttu-id="f736f-126">*Fantasy 島のサンプル環境*</span><span class="sxs-lookup"><span data-stu-id="f736f-126">*Fantasy Island sample environment*</span></span><br>

2. <span data-ttu-id="f736f-127">ダウンロードした **Fantasy_Island.exe** ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="f736f-127">Run the **Fantasy_Island.exe** file you downloaded.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f736f-128">Web からダウンロードした .exe ファイルを実行しようとすると (この例のように)、"Windows で保護されている PC" ポップアップが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="f736f-128">When attempting to run a .exe file downloaded from the web (like this one), you may encounter a "Windows protected your PC" pop-up.</span></span> <span data-ttu-id="f736f-129">このポップアップから Fantasy_Island.exe を実行するには、[ **詳細情報** ] を選択し、その **まま実行** します。</span><span class="sxs-lookup"><span data-stu-id="f736f-129">To run Fantasy_Island.exe from this pop-up, select **More info** and then **Run anyway**.</span></span> <span data-ttu-id="f736f-130">このセキュリティ設定は、信頼しないファイルのダウンロードを防止するためのものであるため、ファイルのソースを信頼する場合にのみ、このオプションを選択してください。</span><span class="sxs-lookup"><span data-stu-id="f736f-130">This security setting is meant to protect you from downloading files you may not want to trust, so please only choose this option when you trust the source of the file.</span></span>

3. <span data-ttu-id="f736f-131">**ファイルエクスプローラー** を開き、アドレスバーに次のファイルの場所を貼り付けて、[環境] フォルダーに移動します `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState` 。</span><span class="sxs-lookup"><span data-stu-id="f736f-131">Open **File Explorer** and navigate to the environments folder by pasting the following file location in the address bar: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`.</span></span>
4. <span data-ttu-id="f736f-132">ダウンロードしたサンプル環境をこのフォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="f736f-132">Copy the sample environment that you downloaded into this folder.</span></span>
5. <span data-ttu-id="f736f-133">**Mixed Reality ポータル** を再起動して、[場所] ピッカーで環境の一覧を更新します。</span><span class="sxs-lookup"><span data-stu-id="f736f-133">Restart **Mixed Reality Portal** to refresh the list of environments in the Places picker.</span></span>
6. <span data-ttu-id="f736f-134">ヘッドセットに配置します。</span><span class="sxs-lookup"><span data-stu-id="f736f-134">Put on your headset.</span></span> <span data-ttu-id="f736f-135">自宅にいる場合は、コントローラーで [Windows] ボタンを使用して [ **スタート] メニュー** を開きます。</span><span class="sxs-lookup"><span data-stu-id="f736f-135">Once you're in the home, open the **Start menu** using the Windows button your controller.</span></span>
7. <span data-ttu-id="f736f-136">ピン留めされたアプリの一覧の上にある [ **場所** ] アイコンを選択して、ホーム環境を選択します。</span><span class="sxs-lookup"><span data-stu-id="f736f-136">Select the **Places** icon above the list of pinned apps to choose a home environment.</span></span>
8. <span data-ttu-id="f736f-137">ダウンロードした Fantasy アイランド環境が、場所の一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="f736f-137">You'll find the Fantasy Island environment that you downloaded in your list of places.</span></span> <span data-ttu-id="f736f-138">[ **Fantasy 島** ] を選択して、新しいカスタムホーム環境に入ります。</span><span class="sxs-lookup"><span data-stu-id="f736f-138">Select **Fantasy Island** to enter your new custom home environment!</span></span>

## <a name="creating-your-own-custom-environment"></a><span data-ttu-id="f736f-139">独自のカスタム環境を作成する</span><span class="sxs-lookup"><span data-stu-id="f736f-139">Creating your own custom environment</span></span>

<span data-ttu-id="f736f-140">このサンプル環境を使用するだけでなく、お好きな3D 編集ソフトウェアを使用して、独自のカスタム環境をエクスポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="f736f-140">In addition to using our sample environments, you can export your own custom environments using your favorite 3D editing software.</span></span> 

### <a name="modeling-guidelines"></a><span data-ttu-id="f736f-141">モデリングガイドライン</span><span class="sxs-lookup"><span data-stu-id="f736f-141">Modeling guidelines</span></span>

<span data-ttu-id="f736f-142">環境をモデリングする場合は、次の推奨事項を念頭に置いて、ユーザーが believably サイズの世界で正しい方向になるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="f736f-142">When modeling your environment, keep the following recommendations in mind so that users spawns in the correct orientation in a believably sized world:</span></span>

1. <span data-ttu-id="f736f-143">ユーザーは 0, 0, 0 で起動するので、元の場所を中心に配置します。</span><span class="sxs-lookup"><span data-stu-id="f736f-143">Users will spawn at 0,0,0 so center your spawn location around the origin.</span></span>
2. <span data-ttu-id="f736f-144">資産を世界規模で作成できるように、作業単位をメーターに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f736f-144">Working Units should be set to meters so that assets can be authored at world scale.</span></span>
3. <span data-ttu-id="f736f-145">上の軸を "Y" に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f736f-145">The Up axis should be set to “Y”.</span></span>
4. <span data-ttu-id="f736f-146">資産は正の Z 軸に "進む" ようになります。</span><span class="sxs-lookup"><span data-stu-id="f736f-146">The asset should face “forward” towards the positive Z axis.</span></span>
5. <span data-ttu-id="f736f-147">すべてのメッシュを結合する必要はありませんが、リソースを制限するデバイスを対象としている場合にお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f736f-147">You don't have to combine all your meshes, but it's recommended if you're targeting resource-constrained devices.</span></span>

### <a name="exporting-your-environment"></a><span data-ttu-id="f736f-148">環境のエクスポート</span><span class="sxs-lookup"><span data-stu-id="f736f-148">Exporting your environment</span></span>

<span data-ttu-id="f736f-149">Windows Mixed Reality は、環境の資産配信形式としてバイナリ glTF (. glb) に依存しています。</span><span class="sxs-lookup"><span data-stu-id="f736f-149">Windows Mixed Reality relies on binary glTF (.glb) as the asset delivery format for environments.</span></span> <span data-ttu-id="f736f-150">glTF は、Khronos グループによって維持される、3D 資産配信用のロイヤリティフリーオープンスタンダードです。</span><span class="sxs-lookup"><span data-stu-id="f736f-150">glTF is a royalty free open standard for 3D asset delivery maintained by the Khronos group.</span></span> <span data-ttu-id="f736f-151">Microsoft では、Windows アプリとエクスペリエンス全体の形式のサポートは、相互運用可能な3D コンテンツの業界標準としての glTF の進化に伴って増加しています。</span><span class="sxs-lookup"><span data-stu-id="f736f-151">Microsoft’s support for the format across Windows apps and experiences will grow as glTF evolves as an industry standard for interoperable 3D content.</span></span>

<span data-ttu-id="f736f-152">カスタムホーム環境として使用するアセットをエクスポートする最初の手順として、glTF 2.0 モデルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f736f-152">The first step in exporting assets to be used as custom home environments is generating a glTF 2.0 model.</span></span> <span data-ttu-id="f736f-153">GlTF 作業グループは、 [サポートされているエクスポーターとコンバーターの一覧](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) を保持し、gltf 2.0 モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f736f-153">The glTF working group maintains a [list of supported exporters and converters](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) to create a glTF 2.0 model.</span></span> <span data-ttu-id="f736f-154">開始するには、このページに記載されているいずれかのプログラムを使用して、glTF 2.0 モデルを作成してエクスポートするか、サポートされているいずれかのコンバーターを使用して既存のモデルを変換します。</span><span class="sxs-lookup"><span data-stu-id="f736f-154">To get started, use one of the programs listed on this page to create and export a glTF 2.0 model, or convert an existing model using one of the supported converters.</span></span>

<span data-ttu-id="f736f-155">また、[この役に立つ記事] をご覧ください。この記事では、Blender と 3DS Max から直接、glTF モデルをエクスポートするためのアートワークフローの概要を説明しています。</span><span class="sxs-lookup"><span data-stu-id="f736f-155">Additionally, check out [this helpful article, which provides an overview of an art workflow for exporting glTF models from Blender and 3DS Max directly.</span></span> 

### <a name="environment-limits"></a><span data-ttu-id="f736f-156">環境の制限</span><span class="sxs-lookup"><span data-stu-id="f736f-156">Environment limits</span></span>

<span data-ttu-id="f736f-157">すべての環境は 256 mbs < なければなりません。</span><span class="sxs-lookup"><span data-stu-id="f736f-157">All environments must be < 256 mbs.</span></span> <span data-ttu-id="f736f-158">256 mbs を超える環境では、ユーザーを囲む既定のスカイボックスのみを使用して、空の世界への読み込みとフォールバックが失敗します。</span><span class="sxs-lookup"><span data-stu-id="f736f-158">Environments larger than 256 mbs will fail to load and fall back to an empty world with just the default skybox surrounding the user.</span></span> <span data-ttu-id="f736f-159">モデルの作成時には、このファイルサイズの制限に留意してください。</span><span class="sxs-lookup"><span data-stu-id="f736f-159">Keep this file size limit in mind when creating your models.</span></span> <span data-ttu-id="f736f-160">さらに、以下で説明するように WindowsMRAssetConverter を使用して環境を最適化する場合は、ファイルサイズが大きく、読み込みが高速になるテクスチャを作成するときにテクスチャサイズが増加することを cognizant してください。</span><span class="sxs-lookup"><span data-stu-id="f736f-160">Additionally, if you plan to optimize your environment using the WindowsMRAssetConverter as described below, be cognizant that the texture size will increase as the optimizer creates textures that have a larger file size, but load faster.</span></span> 

### <a name="optimizing-your-environment"></a><span data-ttu-id="f736f-161">環境の最適化</span><span class="sxs-lookup"><span data-stu-id="f736f-161">Optimizing your environment</span></span>

<span data-ttu-id="f736f-162">Windows Mixed Reality では、環境の読み込み時間を大幅に短縮するオプションの最適化が多数サポートされています。</span><span class="sxs-lookup"><span data-stu-id="f736f-162">Windows Mixed Reality supports many optional optimizations that can significantly reduce your environment load times.</span></span> <span data-ttu-id="f736f-163">多くのテクスチャを持つ環境では特に注意してください。読み込み中にタイムアウトすることがあります。</span><span class="sxs-lookup"><span data-stu-id="f736f-163">Pay special attention with environments that have lots of textures, as they'll sometimes time out while loading.</span></span> <span data-ttu-id="f736f-164">一般に、すべての資産に対してこの手順をお勧めします。ただし、少数または低解像度のテクスチャを使用する小規模な環境では、常に必要になるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="f736f-164">In general, we recommend this step for all assets, however, smaller environments with few or low-resolution textures won't always require it.</span></span> 

<span data-ttu-id="f736f-165">このプロセスを簡単にするために、 [Windows Mixed Reality アセットコンバーター (GitHub で入手できます)](https://github.com/Microsoft/glTF-Toolkit/releases) を作成し、最適化を行いました。</span><span class="sxs-lookup"><span data-stu-id="f736f-165">To make this process easier, we've created the [Windows Mixed Reality Asset Converter (available on GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases) to do your optimizations.</span></span> <span data-ttu-id="f736f-166">このツールでは、Microsoft glTF toolkit で使用できる一連のユーティリティを使用して、追加のテクスチャのパッキング、圧縮、および解像度のスケールダウンを実行することで、標準の 2.0 glTF または glb を最適化します。</span><span class="sxs-lookup"><span data-stu-id="f736f-166">This tool uses a set of utilities available in the Microsoft glTF toolkit to optimize any standard 2.0 glTF or.glb by performing an extra texture packing, compression, and resolution down-scaling.</span></span> 

<span data-ttu-id="f736f-167">コンバーターは、現在、最適化の正確な動作を調整するいくつかのフラグをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f736f-167">The converter currently supports several flags to tweak the exact behavior of the optimizations.</span></span> <span data-ttu-id="f736f-168">最良の結果を得るには、次のフラグを使用してを実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f736f-168">We recommend running with the following flags for best results:</span></span>

<span data-ttu-id="f736f-169">フラグ</span><span class="sxs-lookup"><span data-stu-id="f736f-169">Flag</span></span>|<span data-ttu-id="f736f-170">推奨値</span><span class="sxs-lookup"><span data-stu-id="f736f-170">Recommended Value(s)</span></span>|<span data-ttu-id="f736f-171">説明</span><span class="sxs-lookup"><span data-stu-id="f736f-171">Description</span></span>
---|---|---
<span data-ttu-id="f736f-172">-max-テクスチャ-サイズ</span><span class="sxs-lookup"><span data-stu-id="f736f-172">-max-texture-size</span></span>|<span data-ttu-id="f736f-173">1024または2048</span><span class="sxs-lookup"><span data-stu-id="f736f-173">1024 or 2048</span></span>| <span data-ttu-id="f736f-174">テクスチャの品質を向上させるために値を微調整します。既定値は512x512 です。</span><span class="sxs-lookup"><span data-stu-id="f736f-174">Tweak the value to improve the quality of the textures, default is 512x512.</span></span> <span data-ttu-id="f736f-175">大きな値を指定すると、環境のファイルサイズに大きく影響するため、256 mb の制限を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="f736f-175">A larger value will significantly impact the file size of the environment so keep the 256-mb limit in mind</span></span>
<span data-ttu-id="f736f-176">-最小バージョン</span><span class="sxs-lookup"><span data-stu-id="f736f-176">-min-version</span></span>|<span data-ttu-id="f736f-177">1803</span><span class="sxs-lookup"><span data-stu-id="f736f-177">1803</span></span>|<span data-ttu-id="f736f-178">カスタム環境は、windows >= 1803 のバージョンでのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f736f-178">Custom environments are only supported on versions of windows >= 1803.</span></span> <span data-ttu-id="f736f-179">このフラグは、古いバージョンのテクスチャを削除し、最終的な資産のファイルサイズを縮小します</span><span class="sxs-lookup"><span data-stu-id="f736f-179">This flag will remove textures for older versions and reduce the file size of the final asset</span></span>

<span data-ttu-id="f736f-180">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="f736f-180">For example:</span></span>

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a><span data-ttu-id="f736f-181">環境のテスト</span><span class="sxs-lookup"><span data-stu-id="f736f-181">Testing your environment</span></span>

<span data-ttu-id="f736f-182">Glb 環境が完成したら、ヘッドセットでテストする準備が整います。</span><span class="sxs-lookup"><span data-stu-id="f736f-182">Once you have your final.glb environment, you're ready to test it out in the headset.</span></span> <span data-ttu-id="f736f-183">カスタム環境を mixed reality ホームとして使用する場合は、 [「サンプル環境を試す」](#trying-a-sample-environment) セクションの手順2から開始します。</span><span class="sxs-lookup"><span data-stu-id="f736f-183">Start at step 2 in the ["Trying a sample environment"](#trying-a-sample-environment) section to use your custom environment as the mixed reality home.</span></span> 

## <a name="sending-feedback"></a><span data-ttu-id="f736f-184">フィードバックの送信</span><span class="sxs-lookup"><span data-stu-id="f736f-184">Sending feedback</span></span>

<span data-ttu-id="f736f-185">この試験的な機能を評価していますが、ここでは、カスタム環境の使用方法、検出される可能性があるすべてのバグ、および機能の好みについて学習します。</span><span class="sxs-lookup"><span data-stu-id="f736f-185">While we're evaluating this experimental feature, we're interested in learning how you're using custom environments, any bugs you may find, and how you like the feature.</span></span> <span data-ttu-id="f736f-186">[開発者フォーラム](https://forums.hololens.com/categories/custom-home-environments)でカスタムホーム環境を作成および使用するためのフィードバックを共有します。</span><span class="sxs-lookup"><span data-stu-id="f736f-186">Share any feedback for creating and using custom home environments in the [developer forums](https://forums.hololens.com/categories/custom-home-environments).</span></span>

## <a name="troubleshooting-and-tips"></a><span data-ttu-id="f736f-187">トラブルシューティングとヒント</span><span class="sxs-lookup"><span data-stu-id="f736f-187">Troubleshooting and tips</span></span>

### <a name="how-do-i-change-the-name-of-the-environment"></a><span data-ttu-id="f736f-188">環境の名前を変更操作方法には</span><span class="sxs-lookup"><span data-stu-id="f736f-188">How do I change the name of the environment?</span></span>

<span data-ttu-id="f736f-189">[環境] フォルダー内のファイル名は、[場所の選択] で使用されます。</span><span class="sxs-lookup"><span data-stu-id="f736f-189">The file name in the environments folder will be used in the Places picker.</span></span> <span data-ttu-id="f736f-190">環境の名前を変更するには、環境のファイル名を変更し、Mixed Reality ポータルを再起動します。</span><span class="sxs-lookup"><span data-stu-id="f736f-190">To change the name of your environment, rename the environment file name, and then restart Mixed Reality Portal.</span></span>

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a><span data-ttu-id="f736f-191">マイプレースピッカーからカスタム環境を削除操作方法には</span><span class="sxs-lookup"><span data-stu-id="f736f-191">How do I remove custom environments from my Places picker?</span></span>

<span data-ttu-id="f736f-192">カスタム環境を削除するには、PC () の環境フォルダーを開き、 `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState` 環境を削除します。</span><span class="sxs-lookup"><span data-stu-id="f736f-192">To remove a custom environment, open the environments folder on your PC (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) and delete the environment.</span></span> <span data-ttu-id="f736f-193">Mixed Reality ポータルを再起動すると、この環境は [場所の選択] に表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="f736f-193">Once you restart Mixed Reality Portal, this environment will no longer appear in the Places picker.</span></span> 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a><span data-ttu-id="f736f-194">お気に入りのカスタム環境に既定操作方法しますか?</span><span class="sxs-lookup"><span data-stu-id="f736f-194">How do I default to my favorite custom environment?</span></span>

<span data-ttu-id="f736f-195">現在、既定の環境を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="f736f-195">You can't currently change the default environment.</span></span> <span data-ttu-id="f736f-196">Mixed Reality ポータルを再起動するたびに、崖ハウス環境に戻ります。</span><span class="sxs-lookup"><span data-stu-id="f736f-196">Each time you restart Mixed Reality Portal, you'll be returned to the Cliff House environment.</span></span> 

### <a name="i-spawn-into-a-blank-space"></a><span data-ttu-id="f736f-197">空のスペースを生成する</span><span class="sxs-lookup"><span data-stu-id="f736f-197">I spawn into a blank space</span></span>

<span data-ttu-id="f736f-198">Windows Mixed Reality [では、256 mb を超える環境はサポートされていません](#environment-limits)。</span><span class="sxs-lookup"><span data-stu-id="f736f-198">Windows Mixed Reality [doesn't support environments that exceed 256 mb](#environment-limits).</span></span> <span data-ttu-id="f736f-199">環境がこの制限を超えると、モデルのない空のスカイボックスに移動します。</span><span class="sxs-lookup"><span data-stu-id="f736f-199">When an environment exceeds this limit, you'll land in the empty sky box with no model.</span></span>

### <a name="it-takes-a-long-time-to-load-my-environment"></a><span data-ttu-id="f736f-200">環境の読み込みに時間がかかる</span><span class="sxs-lookup"><span data-stu-id="f736f-200">It takes a long time to load my environment</span></span>

<span data-ttu-id="f736f-201">環境にオプションの最適化を追加して、読み込みを高速化することができます。</span><span class="sxs-lookup"><span data-stu-id="f736f-201">You can add optional optimizations to your environment to make it load faster.</span></span> <span data-ttu-id="f736f-202">詳細については [、「環境の最適化」](#optimizing-your-environment) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f736f-202">See ["Optimizing your environment"](#optimizing-your-environment) for details.</span></span>

### <a name="the-scale-of-my-environment-is-incorrect"></a><span data-ttu-id="f736f-203">環境のスケールが正しくありません</span><span class="sxs-lookup"><span data-stu-id="f736f-203">The scale of my environment is incorrect</span></span>

<span data-ttu-id="f736f-204">Windows Mixed Reality は、環境の読み込み時に glTF units を1メートルに変換します。</span><span class="sxs-lookup"><span data-stu-id="f736f-204">Windows Mixed Reality translates glTF units to 1 meter when loading environments.</span></span> <span data-ttu-id="f736f-205">環境で予期しないスケールが読み込まれる場合は、エクスポーターを再確認して、1メートルのスケールでモデル化されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f736f-205">If your environment loads up an unexpected scale, double check your exporter to ensure that you're modeling at a 1-meter scale.</span></span> 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a><span data-ttu-id="f736f-206">環境内の生成場所が正しくありません</span><span class="sxs-lookup"><span data-stu-id="f736f-206">The spawn location in my environment is incorrect</span></span>

<span data-ttu-id="f736f-207">既定の生成場所は、環境内の0、0、0にあります。</span><span class="sxs-lookup"><span data-stu-id="f736f-207">The default spawn location is located at 0,0,0 in the environment.</span></span> <span data-ttu-id="f736f-208">現在、この場所をカスタマイズすることはできません。そのため、必要な生成ポイントに配置された元の環境をエクスポートして、生成ポイントを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f736f-208">It's not currently possible to customize this location, so you must modify the spawn point by exporting your environment with the origin positioned at the spawn point you want.</span></span>

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a><span data-ttu-id="f736f-209">環境内のオーディオが正しく聞こえない</span><span class="sxs-lookup"><span data-stu-id="f736f-209">The audio doesn't sound correct in the environment</span></span>

<span data-ttu-id="f736f-210">カスタム環境を作成すると、作成した物理空間に一致しない acoustics レンダリングシミュレーションが使用されます。</span><span class="sxs-lookup"><span data-stu-id="f736f-210">When you create your custom environment, it will be using an acoustics rendering simulation that doesn't match the physical space you've created.</span></span> <span data-ttu-id="f736f-211">サウンドが間違った方向にある可能性があり、muffled が聞こえる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f736f-211">Sound may come from the wrong directions and may sound muffled.</span></span> 

## <a name="see-also"></a><span data-ttu-id="f736f-212">関連項目</span><span class="sxs-lookup"><span data-stu-id="f736f-212">See also</span></span>
* [<span data-ttu-id="f736f-213">Windows Mixed Reality 資産コンバーター (GitHub)</span><span class="sxs-lookup"><span data-stu-id="f736f-213">Windows Mixed Reality Asset Converter (on GitHub)</span></span>](https://github.com/Microsoft/glTF-Toolkit/releases)