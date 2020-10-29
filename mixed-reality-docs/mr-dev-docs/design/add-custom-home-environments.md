---
title: 独自のイマーシブ環境を設計する
description: 提供する Windows Mixed Reality ホーム環境に加えて、独自のを作成して使用することもできます。
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、Home、Custom Environment、地名、崖ハウス、skyloft、user、create
ms.openlocfilehash: 69fac9fcc0b3d7f199f4277c5d1b5a0c7df5f8c2
ms.sourcegitcommit: 838bebf6bacac4047feff493c0847d4e6371976f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2020
ms.locfileid: "91781531"
---
# <a name="design-your-own-immersive-environments"></a><span data-ttu-id="3966e-104">独自のイマーシブ環境を設計する</span><span class="sxs-lookup"><span data-stu-id="3966e-104">Design your own immersive environments</span></span>

>[!NOTE]
><span data-ttu-id="3966e-105">これは試験段階の機能です。</span><span class="sxs-lookup"><span data-stu-id="3966e-105">This is an experimental feature.</span></span> <span data-ttu-id="3966e-106">試してみてください。しかし、すべてが期待どおりに動作しない場合、驚かれることはありません。</span><span class="sxs-lookup"><span data-stu-id="3966e-106">Give it a try and have fun with it, but don't be surprised if everything doesn't quite work as expected.</span></span> <span data-ttu-id="3966e-107">この機能の有効性を評価し、それを使用することに関心があるので、 [開発者フォーラム](https://forums.hololens.com/categories/custom-home-environments)で、経験 (および発見したバグ) についてご意見をお聞かせください。</span><span class="sxs-lookup"><span data-stu-id="3966e-107">We're evaluating the viability of this feature and interest in using it, so please tell us about your experience (and any bugs you've found) in the [developer forums](https://forums.hololens.com/categories/custom-home-environments).</span></span>

<span data-ttu-id="3966e-108">[Windows 10 April 2018 update](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)以降では、 [windows Mixed Reality ホーム](../discover/navigating-the-windows-mixed-reality-home.md)として使用するカスタム環境を [スタート] メニューの [場所] ピッカーに追加できる実験的な機能が有効になりました。</span><span class="sxs-lookup"><span data-stu-id="3966e-108">Starting with the [Windows 10 April 2018 update](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018), we've enabled an experimental feature that lets you add custom environments to the Places picker (on the Start menu) to use as the [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md).</span></span> <span data-ttu-id="3966e-109">Windows Mixed Reality には、2つの既定の環境 (崖家と Skyloft) があり、これをホームとして選択することができます。</span><span class="sxs-lookup"><span data-stu-id="3966e-109">Windows Mixed Reality has two default environments, Cliff House and Skyloft, that you can choose as your home.</span></span> <span data-ttu-id="3966e-110">カスタム環境を作成すると、独自の作成でそのリストを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="3966e-110">Creating custom environments allows you to expand that list with your own creations.</span></span> <span data-ttu-id="3966e-111">これを早期の状態で使用できるようにして、作成者と開発者の関心を評価し、作成した世界の種類を確認し、さまざまな作成ツールの使用方法を理解します。</span><span class="sxs-lookup"><span data-stu-id="3966e-111">We are making this available in an early state to evaluate interest from creators and developers, see what kinds of worlds you create, and understand how you work with different authoring tools.</span></span>

<span data-ttu-id="3966e-112">カスタム環境を使用すると、Skyloft が崖家やの場合と同じように、テレ移植、アプリとの対話、およびホログラムの配置が行われます。</span><span class="sxs-lookup"><span data-stu-id="3966e-112">When using a custom environment you'll notice that teleporting, interacting with apps, and placing holograms works just like it does in the Cliff House and Skyloft.</span></span> <span data-ttu-id="3966e-113">Web を fantasy ランドスケープで閲覧したり、ホログラムを使用して futuristic の都市を埋めることができます。可能性は無限です。</span><span class="sxs-lookup"><span data-stu-id="3966e-113">You can browse the web in a fantasy landscape or fill a futuristic city with holograms - the possibilities are endless!</span></span>

## <a name="device-support"></a><span data-ttu-id="3966e-114">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="3966e-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="3966e-115"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="3966e-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="3966e-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="3966e-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="3966e-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="3966e-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="3966e-118">カスタムホーム環境</span><span class="sxs-lookup"><span data-stu-id="3966e-118">Custom home environments</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="3966e-119">✔️</span><span class="sxs-lookup"><span data-stu-id="3966e-119">✔️</span></span></td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a><span data-ttu-id="3966e-120">サンプル環境を試す</span><span class="sxs-lookup"><span data-stu-id="3966e-120">Trying a sample environment</span></span>

<span data-ttu-id="3966e-121">カスタムホーム環境の独創的な可能性を示すサンプル環境を作成しました。</span><span class="sxs-lookup"><span data-stu-id="3966e-121">We've created a sample environment that shows off some of the creative possibilities of custom home environments.</span></span> <span data-ttu-id="3966e-122">次の手順に従って試してみてください。</span><span class="sxs-lookup"><span data-stu-id="3966e-122">Follow these steps to try it out:</span></span>
1. <span data-ttu-id="3966e-123">[サンプル Fantasy アイランド環境](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (自己解凍形式の実行可能ファイルへのリンクポイント) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="3966e-123">[Download our sample Fantasy Island environment](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (link points to self-extracting executable).</span></span>

    <span data-ttu-id="3966e-124">![Fantasy 島のサンプル環境](images/FantasyLand.jpg)</span><span class="sxs-lookup"><span data-stu-id="3966e-124">![Fantasy Island sample environment](images/FantasyLand.jpg)</span></span><br>
    <span data-ttu-id="3966e-125">*Fantasy 島のサンプル環境*</span><span class="sxs-lookup"><span data-stu-id="3966e-125">*Fantasy Island sample environment*</span></span><br>

2. <span data-ttu-id="3966e-126">ダウンロードした **Fantasy_Island.exe** ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="3966e-126">Run the **Fantasy_Island.exe** file you just downloaded.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3966e-127">Web からダウンロードした .exe ファイルを実行しようとすると (この例のように)、"Windows で保護されている PC" ポップアップが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="3966e-127">When attempting to run a .exe file downloaded from the web (like this one), you may encounter a "Windows protected your PC" pop-up.</span></span> <span data-ttu-id="3966e-128">このポップアップから Fantasy_Island.exe を実行するには、[ **詳細情報** ] を選択し、その **まま実行** します。</span><span class="sxs-lookup"><span data-stu-id="3966e-128">To run Fantasy_Island.exe from this pop-up, select **More info** and then **Run anyway** .</span></span> <span data-ttu-id="3966e-129">このセキュリティ設定は、信頼しないファイルのダウンロードを防止するためのものであるため、ファイルのソースを信頼する場合にのみ、このオプションを選択してください。</span><span class="sxs-lookup"><span data-stu-id="3966e-129">This security setting is meant to protect you from downloading files you may not want to trust, so please only choose this option when you trust the source of the file.</span></span>

3. <span data-ttu-id="3966e-130">**ファイルエクスプローラー** を開き、アドレスバーに次のように貼り付けて、[環境] フォルダーに移動し `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState` ます。</span><span class="sxs-lookup"><span data-stu-id="3966e-130">Open **File Explorer** and navigate to the environments folder by pasting the following in the address bar: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`.</span></span>
4. <span data-ttu-id="3966e-131">ダウンロードしたサンプル環境をこのフォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="3966e-131">Copy the sample environment that you downloaded into this folder.</span></span>
5. <span data-ttu-id="3966e-132">**Mixed Reality ポータル** を再起動します。</span><span class="sxs-lookup"><span data-stu-id="3966e-132">Restart **Mixed Reality Portal** .</span></span> <span data-ttu-id="3966e-133">これにより、[場所の選択] の環境の一覧が更新されます。</span><span class="sxs-lookup"><span data-stu-id="3966e-133">This will refresh the list of environments in the Places picker.</span></span>
6. <span data-ttu-id="3966e-134">ヘッドセットに配置します。</span><span class="sxs-lookup"><span data-stu-id="3966e-134">Put on your headset.</span></span> <span data-ttu-id="3966e-135">自宅にいる場合は、コントローラーで [Windows] ボタンを使用して [ **スタート] メニュー** を開きます。</span><span class="sxs-lookup"><span data-stu-id="3966e-135">Once you're in the home, open the **Start menu** using the Windows button your controller.</span></span>
7. <span data-ttu-id="3966e-136">ピン留めされたアプリの一覧の上にある [ **場所** ] アイコンを選択して、ホーム環境を選択します。</span><span class="sxs-lookup"><span data-stu-id="3966e-136">Select the **Places** icon above the list of pinned apps to choose a home environment.</span></span>
8. <span data-ttu-id="3966e-137">ダウンロードした Fantasy アイランド環境が、場所の一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3966e-137">You will find the Fantasy Island environment that you downloaded in your list of places.</span></span> <span data-ttu-id="3966e-138">[ **Fantasy 島** ] を選択して、新しいカスタムホーム環境に入ります。</span><span class="sxs-lookup"><span data-stu-id="3966e-138">Select **Fantasy Island** to enter your new custom home environment!</span></span>

## <a name="creating-your-own-custom-environment"></a><span data-ttu-id="3966e-139">独自のカスタム環境を作成する</span><span class="sxs-lookup"><span data-stu-id="3966e-139">Creating your own custom environment</span></span>

<span data-ttu-id="3966e-140">このサンプル環境を使用するだけでなく、お好きな3D 編集ソフトウェアを使用して、独自のカスタム環境をエクスポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="3966e-140">In addition to using our sample environments, you can export your own custom environments using your favorite 3D editing software.</span></span> 

### <a name="modeling-guidelines"></a><span data-ttu-id="3966e-141">モデリングガイドライン</span><span class="sxs-lookup"><span data-stu-id="3966e-141">Modeling guidelines</span></span>

<span data-ttu-id="3966e-142">環境をモデリングする場合は、次の推奨事項を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="3966e-142">When modeling your environment, keep the following recommendations in mind.</span></span> <span data-ttu-id="3966e-143">これにより、ユーザーが believably サイズの世界で正しい向きで生成されるようになります。</span><span class="sxs-lookup"><span data-stu-id="3966e-143">This will help ensure the user spawns in the correct orientation in a believably-sized world:</span></span>

1. <span data-ttu-id="3966e-144">ユーザーは 0, 0, 0 で起動します。これにより、元の場所を中心にして目的の場所を作成できます。</span><span class="sxs-lookup"><span data-stu-id="3966e-144">Users will spawn at 0,0,0 so center your desired spawn location around the origin.</span></span>
2. <span data-ttu-id="3966e-145">資産を世界規模で作成できるように、作業単位をメーターに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3966e-145">Working Units should be set to meters so that assets can be authored at world scale.</span></span>
3. <span data-ttu-id="3966e-146">上の軸を "Y" に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3966e-146">The Up axis should be set to “Y”.</span></span>
4. <span data-ttu-id="3966e-147">資産は正の Z 軸に "進む" ようになります。</span><span class="sxs-lookup"><span data-stu-id="3966e-147">The asset should face “forward” towards the positive Z axis.</span></span>
5. <span data-ttu-id="3966e-148">すべてのメッシュを結合する必要はありませんが、リソースを制限するデバイスを対象とする場合にお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3966e-148">All meshes do not need to be combined, but it is recommended if you are targeting resource-constrained devices.</span></span>

### <a name="exporting-your-environment"></a><span data-ttu-id="3966e-149">環境のエクスポート</span><span class="sxs-lookup"><span data-stu-id="3966e-149">Exporting your environment</span></span>

<span data-ttu-id="3966e-150">Windows Mixed Reality は、環境の資産配信形式としてバイナリ glTF (. glb) に依存しています。</span><span class="sxs-lookup"><span data-stu-id="3966e-150">Windows Mixed Reality relies on binary glTF (.glb) as the asset delivery format for environments.</span></span> <span data-ttu-id="3966e-151">glTF は、Khronos グループによって維持される、3D 資産配信用のロイヤリティフリーオープンスタンダードです。</span><span class="sxs-lookup"><span data-stu-id="3966e-151">glTF is a royalty free open standard for 3D asset delivery maintained by the Khronos group.</span></span> <span data-ttu-id="3966e-152">GlTF は相互運用可能な3D コンテンツの業界標準として進化しているため、Microsoft は Windows アプリとエクスペリエンス全体の形式をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="3966e-152">As glTF evolves as an industry standard for interoperable 3D content, so will Microsoft’s support for the format across Windows apps and experiences.</span></span>

<span data-ttu-id="3966e-153">カスタムホーム環境として使用するアセットをエクスポートする最初の手順として、glTF 2.0 モデルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="3966e-153">The first step in exporting assets to be used as custom home environments is generating a glTF 2.0 model.</span></span> <span data-ttu-id="3966e-154">GlTF 作業グループは、 [サポートされているエクスポーターとコンバーターの一覧](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) を保持し、gltf 2.0 モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="3966e-154">The glTF working group maintains a [list of supported exporters and converters](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) to create a glTF 2.0 model.</span></span> <span data-ttu-id="3966e-155">開始するには、このページに記載されているいずれかのプログラムを使用して、glTF 2.0 モデルを作成してエクスポートするか、サポートされているいずれかのコンバーターを使用して既存のモデルを変換します。</span><span class="sxs-lookup"><span data-stu-id="3966e-155">To get started, use one of the programs listed on this page to create and export a glTF 2.0 model, or convert an existing model using one of the supported converters.</span></span>

<span data-ttu-id="3966e-156">また、Blender と 3DS Max から直接、glTF モデルをエクスポートするための最先端のワークフローの概要については、こちらの [役に立つ記事](https://www.khronos.org/blog/art-pipeline-for-gltf) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3966e-156">Additionally, check out [this helpful article](https://www.khronos.org/blog/art-pipeline-for-gltf) which provides an overview of an art workflow for exporting glTF models from Blender and 3DS Max directly.</span></span> 

### <a name="environment-limits"></a><span data-ttu-id="3966e-157">環境の制限</span><span class="sxs-lookup"><span data-stu-id="3966e-157">Environment limits</span></span>

<span data-ttu-id="3966e-158">すべての環境は 256 mbs < なければなりません。</span><span class="sxs-lookup"><span data-stu-id="3966e-158">All environments must be < 256 mbs.</span></span> <span data-ttu-id="3966e-159">256 mbs を超える環境では、ユーザーを囲む既定のスカイボックスのみを使用して、空の世界への読み込みとフォールバックが失敗します。</span><span class="sxs-lookup"><span data-stu-id="3966e-159">Environments larger than 256 mbs will fail to load and fall back to an empty world with just the default skybox surrounding the user.</span></span> <span data-ttu-id="3966e-160">モデルの作成時には、このファイルサイズの制限に留意してください。</span><span class="sxs-lookup"><span data-stu-id="3966e-160">Please keep this file size limit in mind when creating your models.</span></span> <span data-ttu-id="3966e-161">さらに、以下で説明するように WindowsMRAssetConverter を使用して環境を最適化する場合は、ファイルサイズが大きく、読み込みが高速になるテクスチャを作成するときにテクスチャサイズが増加することを cognizant してください。</span><span class="sxs-lookup"><span data-stu-id="3966e-161">Additionally, if you plan to optimize your environment using the WindowsMRAssetConverter as described below, be cognizant that the texture size will increase as the optimizer creates textures that have a larger file size, but load faster.</span></span> 

### <a name="optimizing-your-environment"></a><span data-ttu-id="3966e-162">環境の最適化</span><span class="sxs-lookup"><span data-stu-id="3966e-162">Optimizing your environment</span></span>

<span data-ttu-id="3966e-163">Windows Mixed Reality では、環境の読み込み時間を大幅に短縮する、いくつかのオプションの最適化がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="3966e-163">Windows Mixed Reality supports a number of optional optimizations that will significantly reduce the load time of your environments.</span></span> <span data-ttu-id="3966e-164">これは、多くのテクスチャを持つ環境では特に重要です。読み込み中にタイムアウトすることがあります。</span><span class="sxs-lookup"><span data-stu-id="3966e-164">This can be especially important for environments with many textures, as they will sometimes time out while loading.</span></span> <span data-ttu-id="3966e-165">一般に、すべての資産に対してこの手順をお勧めします。ただし、少数または低解像度のテクスチャを使用する小規模な環境では、常に必要になるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="3966e-165">In general, we recommend this step for all assets, however, smaller environments with few or low-resolution textures won't always require it.</span></span> 

<span data-ttu-id="3966e-166">このプロセスを簡単にするために、 [Windows Mixed Reality 資産コンバーター (GitHub で入手できます)](https://github.com/Microsoft/glTF-Toolkit/releases) を作成し、最適化を実行しました。</span><span class="sxs-lookup"><span data-stu-id="3966e-166">To make this process easier, we have created the [Windows Mixed Reality Asset Converter (available on GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases) to perform your optimizations.</span></span> <span data-ttu-id="3966e-167">このツールでは、Microsoft glTF toolkit で利用できる一連のユーティリティを使用して、追加のテクスチャパッキング、圧縮、および解像度のスケールダウンを実行することで、標準の 2.0 glTF または glb を最適化します。</span><span class="sxs-lookup"><span data-stu-id="3966e-167">This tool uses a set of utilities available in the Microsoft glTF toolkit to optimize any standard 2.0 glTF or .glb by performing an additional texture packing, compression and resolution down-scaling.</span></span> 

<span data-ttu-id="3966e-168">現在、コンバーターでは、最適化の正確な動作を調整するための多数のフラグがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="3966e-168">The converter currently supports a number of flags to tweak the exact behavior of the optimizations.</span></span> <span data-ttu-id="3966e-169">最良の結果を得るには、次のフラグを使用してを実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3966e-169">We recommend running with the following flags for best results:</span></span>

<span data-ttu-id="3966e-170">フラグ</span><span class="sxs-lookup"><span data-stu-id="3966e-170">Flag</span></span>|<span data-ttu-id="3966e-171">推奨値</span><span class="sxs-lookup"><span data-stu-id="3966e-171">Recommended Value(s)</span></span>|<span data-ttu-id="3966e-172">説明</span><span class="sxs-lookup"><span data-stu-id="3966e-172">Description</span></span>
---|---|---
<span data-ttu-id="3966e-173">-max-テクスチャ-サイズ</span><span class="sxs-lookup"><span data-stu-id="3966e-173">-max-texture-size</span></span>|<span data-ttu-id="3966e-174">1024または2048</span><span class="sxs-lookup"><span data-stu-id="3966e-174">1024 or 2048</span></span>| <span data-ttu-id="3966e-175">テクスチャの品質を向上させるためにこれを微調整します。既定値は512x512 です。</span><span class="sxs-lookup"><span data-stu-id="3966e-175">Tweak this to improve the quality of the textures, default is 512x512.</span></span> <span data-ttu-id="3966e-176">大きな値を指定すると、環境のファイルサイズに大きく影響するため、256 mb の制限を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="3966e-176">Note that a larger value will significantly impact the file size of the environment so keep the 256 mb limit in mind</span></span>
<span data-ttu-id="3966e-177">-最小バージョン</span><span class="sxs-lookup"><span data-stu-id="3966e-177">-min-version</span></span>|<span data-ttu-id="3966e-178">1803</span><span class="sxs-lookup"><span data-stu-id="3966e-178">1803</span></span>|<span data-ttu-id="3966e-179">カスタム環境は、windows >= 1803 のバージョンでのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="3966e-179">Custom environments are only supported on versions of windows >= 1803.</span></span> <span data-ttu-id="3966e-180">このフラグは、古いバージョンのテクスチャを削除し、最終的な資産のファイルサイズを縮小します</span><span class="sxs-lookup"><span data-stu-id="3966e-180">This flag will remove textures for older versions and reduce the file size of the final asset</span></span>

<span data-ttu-id="3966e-181">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="3966e-181">For example:</span></span>

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a><span data-ttu-id="3966e-182">環境のテスト</span><span class="sxs-lookup"><span data-stu-id="3966e-182">Testing your environment</span></span>

<span data-ttu-id="3966e-183">Glb 環境が完成したら、ヘッドセットでテストする準備が整います。</span><span class="sxs-lookup"><span data-stu-id="3966e-183">Once you have your final .glb environment you're ready to test it out in the headset.</span></span> <span data-ttu-id="3966e-184">カスタム環境を mixed reality ホームとして使用する場合は、 [「サンプル環境を試す」](#trying-a-sample-environment) セクションの手順2から開始します。</span><span class="sxs-lookup"><span data-stu-id="3966e-184">Start at step 2 in the ["Trying a sample environment"](#trying-a-sample-environment) section to use your custom environment as the mixed reality home.</span></span> 

## <a name="feedback"></a><span data-ttu-id="3966e-185">フィードバック</span><span class="sxs-lookup"><span data-stu-id="3966e-185">Feedback</span></span>

<span data-ttu-id="3966e-186">この試験的な機能を評価していますが、ここでは、カスタム環境の使用方法、発生する可能性があるすべてのバグ、および機能の好みについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3966e-186">While we're evaluating this experimental feature, we're interested in learning how you're using custom environments, any bugs you may encounter, and how you like the feature.</span></span> <span data-ttu-id="3966e-187">[開発者フォーラム](https://forums.hololens.com/categories/custom-home-environments)でカスタムホーム環境を作成および使用するためのすべてのフィードバックを共有してください。</span><span class="sxs-lookup"><span data-stu-id="3966e-187">Please share any and all feedback for creating and using custom home environments in the [developer forums](https://forums.hololens.com/categories/custom-home-environments).</span></span>

## <a name="troubleshooting-and-tips"></a><span data-ttu-id="3966e-188">トラブルシューティングとヒント</span><span class="sxs-lookup"><span data-stu-id="3966e-188">Troubleshooting and tips</span></span>

### <a name="how-do-i-change-the-name-of-the-environment"></a><span data-ttu-id="3966e-189">環境の名前を変更操作方法には</span><span class="sxs-lookup"><span data-stu-id="3966e-189">How do I change the name of the environment?</span></span>

<span data-ttu-id="3966e-190">[環境] フォルダー内のファイル名は、[場所の選択] で使用されます。</span><span class="sxs-lookup"><span data-stu-id="3966e-190">The file name in the environments folder will be used in the Places picker.</span></span> <span data-ttu-id="3966e-191">環境の名前を変更するには、環境のファイル名の名前を変更し、Mixed Reality ポータルを再起動します。</span><span class="sxs-lookup"><span data-stu-id="3966e-191">To change the name of your environment simply rename the environment file name, and then restart Mixed Reality Portal.</span></span>

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a><span data-ttu-id="3966e-192">マイプレースピッカーからカスタム環境を削除操作方法には</span><span class="sxs-lookup"><span data-stu-id="3966e-192">How do I remove custom environments from my Places picker?</span></span>

<span data-ttu-id="3966e-193">カスタム環境を削除するには、PC () の環境フォルダーを開き、 `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState` 環境を削除します。</span><span class="sxs-lookup"><span data-stu-id="3966e-193">To remove a custom environment, open the environments folder on your PC (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) and delete the environment.</span></span> <span data-ttu-id="3966e-194">Mixed Reality ポータルを再起動すると、この環境は [場所の選択] に表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="3966e-194">Once you restart Mixed Reality Portal, this environment will no longer appear in the Places picker.</span></span> 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a><span data-ttu-id="3966e-195">お気に入りのカスタム環境に既定操作方法しますか?</span><span class="sxs-lookup"><span data-stu-id="3966e-195">How do I default to my favorite custom environment?</span></span>

<span data-ttu-id="3966e-196">現在、既定の環境を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="3966e-196">You can't currently change the default environment.</span></span> <span data-ttu-id="3966e-197">Mixed Reality ポータルを再起動するたびに、崖ハウス環境に戻ります。</span><span class="sxs-lookup"><span data-stu-id="3966e-197">Each time you restart Mixed Reality Portal, you will be returned to the Cliff House environment.</span></span> 

### <a name="i-spawn-into-a-blank-space"></a><span data-ttu-id="3966e-198">空のスペースを生成する</span><span class="sxs-lookup"><span data-stu-id="3966e-198">I spawn into a blank space</span></span>

<span data-ttu-id="3966e-199">Windows Mixed Reality [では、256 mb を超える環境はサポートされていません](#environment-limits)。</span><span class="sxs-lookup"><span data-stu-id="3966e-199">Windows Mixed Reality [doesn't support environments that exceed 256 mb](#environment-limits).</span></span> <span data-ttu-id="3966e-200">環境がこの制限を超えると、モデルのない空のスカイボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3966e-200">When an environment exceeds this limit, you will land in the empty sky box with no model.</span></span>

### <a name="it-takes-a-long-time-to-load-my-environment"></a><span data-ttu-id="3966e-201">環境の読み込みに時間がかかる</span><span class="sxs-lookup"><span data-stu-id="3966e-201">It takes a long time to load my environment</span></span>

<span data-ttu-id="3966e-202">環境にオプションの最適化を追加して、読み込みを高速化することができます。</span><span class="sxs-lookup"><span data-stu-id="3966e-202">You can add optional optimizations to your environment to make it load faster.</span></span> <span data-ttu-id="3966e-203">詳細については [、「環境の最適化」](#optimizing-your-environment) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3966e-203">See ["Optimizing your environment"](#optimizing-your-environment) for details.</span></span>

### <a name="the-scale-of-my-environment-is-incorrect"></a><span data-ttu-id="3966e-204">環境のスケールが正しくありません</span><span class="sxs-lookup"><span data-stu-id="3966e-204">The scale of my environment is incorrect</span></span>

<span data-ttu-id="3966e-205">Windows Mixed Reality は、環境の読み込み時に glTF units を1メートルに変換します。</span><span class="sxs-lookup"><span data-stu-id="3966e-205">Windows Mixed Reality translates glTF units to 1 meter when loading environments.</span></span> <span data-ttu-id="3966e-206">環境で予期しないスケールが読み込まれる場合は、エクスポーターを再確認して、1メートルのスケールでモデル化されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3966e-206">If your environment loads up an unexpected scale, double check your exporter to ensure that you're modeling at a 1 meter scale.</span></span> 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a><span data-ttu-id="3966e-207">環境内の生成場所が正しくありません</span><span class="sxs-lookup"><span data-stu-id="3966e-207">The spawn location in my environment is incorrect</span></span>

<span data-ttu-id="3966e-208">既定の生成場所は、環境内の0、0、0にあります。</span><span class="sxs-lookup"><span data-stu-id="3966e-208">The default spawn location is located at 0,0,0 in the environment.</span></span> <span data-ttu-id="3966e-209">現在、この場所をカスタマイズすることはできません。そのため、必要な生成ポイントに配置された元の環境をエクスポートして、生成ポイントを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3966e-209">Its not currently possible to customize this location, so you must modify the spawn point by exporting your environment with the origin positioned at the desired spawn point.</span></span>

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a><span data-ttu-id="3966e-210">環境内のオーディオが正しく聞こえない</span><span class="sxs-lookup"><span data-stu-id="3966e-210">The audio doesn't sound correct in the environment</span></span>

<span data-ttu-id="3966e-211">カスタム環境を作成すると、作成した物理空間に一致しない acoustics レンダリングシミュレーションが使用されます。</span><span class="sxs-lookup"><span data-stu-id="3966e-211">When you create your custom environment, it will be using an acoustics rendering simulation that does not match the physical space you have created.</span></span> <span data-ttu-id="3966e-212">サウンドが間違った方向にある可能性があり、muffled が聞こえる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3966e-212">Sound may come from the wrong directions and may sound muffled.</span></span> 

## <a name="see-also"></a><span data-ttu-id="3966e-213">関連項目</span><span class="sxs-lookup"><span data-stu-id="3966e-213">See also</span></span>
* [<span data-ttu-id="3966e-214">Windows Mixed Reality 資産コンバーター (GitHub)</span><span class="sxs-lookup"><span data-stu-id="3966e-214">Windows Mixed Reality Asset Converter (on GitHub)</span></span>](https://github.com/Microsoft/glTF-Toolkit/releases)

