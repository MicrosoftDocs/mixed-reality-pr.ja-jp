---
title: ケーススタディ-HoloSketch の構築、空間レイアウト、および HoloLens 用の UX スケッチアプリ
description: HoloSketch は、holographic エクスペリエンスの構築に役立つ HoloLens 用のデバイス上の空間レイアウトおよび UX スケッチツールです。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, Windows Mixed Reality, スケッチ, アプリ
ms.openlocfilehash: 4cb5b6a0a0e057bafb7820d8893b2561b44a2d7e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686314"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a><span data-ttu-id="4b84c-104">ケーススタディ-HoloSketch の構築、空間レイアウト、および HoloLens 用の UX スケッチアプリ</span><span class="sxs-lookup"><span data-stu-id="4b84c-104">Case study - Building HoloSketch, a spatial layout and UX sketching app for HoloLens</span></span>

<span data-ttu-id="4b84c-105">HoloSketch は、holographic エクスペリエンスの構築に役立つ HoloLens 用のデバイス上の空間レイアウトおよび UX スケッチツールです。</span><span class="sxs-lookup"><span data-stu-id="4b84c-105">HoloSketch is an on-device spatial layout and UX sketching tool for HoloLens to help build holographic experiences.</span></span> <span data-ttu-id="4b84c-106">HoloSketch は、ペアになっている Bluetooth キーボードとマウス、およびジェスチャと音声コマンドで動作します。</span><span class="sxs-lookup"><span data-stu-id="4b84c-106">HoloSketch works with a paired Bluetooth keyboard and mouse as well as gesture and voice commands.</span></span> <span data-ttu-id="4b84c-107">HoloSketch の目的は、簡単な視覚エフェクトとイテレーションのための簡単な UX レイアウトツールを提供することです。</span><span class="sxs-lookup"><span data-stu-id="4b84c-107">The purpose of HoloSketch is to provide a simple UX layout tool for quick visualization and iteration.</span></span>

<span data-ttu-id="4b84c-108">![HoloSketch: HoloLens 用の空間レイアウトと UX スケッチアプリ。](images/holosketch-image-01-640px.png)</span><span class="sxs-lookup"><span data-stu-id="4b84c-108">![HoloSketch: A spatial layout and UX sketching app for HoloLens.](images/holosketch-image-01-640px.png)</span></span><br>
<span data-ttu-id="4b84c-109">*HoloSketch: HoloLens 用の空間レイアウトと UX スケッチアプリ*</span><span class="sxs-lookup"><span data-stu-id="4b84c-109">*HoloSketch: spatial layout and UX sketching app for HoloLens*</span></span>

<span data-ttu-id="4b84c-110">![シンプルな UX レイアウトツールで、視覚化とイテレーションを簡単に行うことができます。](images/holosketch-image-02.png)</span><span class="sxs-lookup"><span data-stu-id="4b84c-110">![A simple UX layout tool for quick visualization and iteration.](images/holosketch-image-02.png)</span></span><br>
<span data-ttu-id="4b84c-111">*シンプルな UX レイアウトツールで簡単に視覚化とイテレーションを行う*</span><span class="sxs-lookup"><span data-stu-id="4b84c-111">*A simple UX layout tool for quick visualization and iteration*</span></span>

## <a name="features"></a><span data-ttu-id="4b84c-112">特徴</span><span class="sxs-lookup"><span data-stu-id="4b84c-112">Features</span></span>

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a><span data-ttu-id="4b84c-113">クイックスタディとスケールのプロトタイプのプリミティブ</span><span class="sxs-lookup"><span data-stu-id="4b84c-113">Primitives for quick studies and scale-prototyping</span></span>

![プリミティブシェイプの使用](images/holosketch-primitives-giphy.gif)

<span data-ttu-id="4b84c-115">プリミティブな図形を使用して、クイック massing スタディとスケールプロトタイプを構築します。</span><span class="sxs-lookup"><span data-stu-id="4b84c-115">Use primitive shapes for quick massing studies and scale-prototyping.</span></span>

### <a name="import-objects-through-onedrive"></a><span data-ttu-id="4b84c-116">OneDrive を使用してオブジェクトをインポートする</span><span class="sxs-lookup"><span data-stu-id="4b84c-116">Import objects through OneDrive</span></span>

![オブジェクトのインポート](images/holosketch-importobjects-giphy.gif)

<span data-ttu-id="4b84c-118">PNG/JPG イメージまたは 3D FBX オブジェクト (Unity でパッケージ化する必要があります) を、OneDrive を通じて mixed reality スペースにインポートします。</span><span class="sxs-lookup"><span data-stu-id="4b84c-118">Import PNG/JPG images or 3D FBX objects(requires packaging in Unity) into the mixed reality space through OneDrive.</span></span>

### <a name="manipulate-objects"></a><span data-ttu-id="4b84c-119">オブジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="4b84c-119">Manipulate objects</span></span>

![オブジェクトの操作](images/manipulate-objects-640px.jpg)

<span data-ttu-id="4b84c-121">使い慣れた3D オブジェクトインターフェイスを使用して、オブジェクト (移動/回転/スケール) を操作します。</span><span class="sxs-lookup"><span data-stu-id="4b84c-121">Manipulate objects (move/rotate/scale) with a familiar 3D object interface.</span></span>

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a><span data-ttu-id="4b84c-122">Bluetooth、マウス/キーボード、ジェスチャ、音声コマンド</span><span class="sxs-lookup"><span data-stu-id="4b84c-122">Bluetooth, mouse/keyboard, gestures and voice commands</span></span>

![Bluetooth をサポートする](images/supports-bluetooth-640px.jpg)

<span data-ttu-id="4b84c-124">HoloSketch では、Bluetooth マウス/キーボード、ジェスチャ、音声コマンドがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="4b84c-124">HoloSketch supports Bluetooth mouse/keyboard, gestures and voice commands.</span></span>

## <a name="background"></a><span data-ttu-id="4b84c-125">バックグラウンド</span><span class="sxs-lookup"><span data-stu-id="4b84c-125">Background</span></span>

### <a name="importance-of-experiencing-your-design-in-the-device"></a><span data-ttu-id="4b84c-126">デバイスで設計が発生する重要性</span><span class="sxs-lookup"><span data-stu-id="4b84c-126">Importance of experiencing your design in the device</span></span>

<span data-ttu-id="4b84c-127">HoloLens 向けに設計する場合は、デバイスで設計を行うことが重要です。</span><span class="sxs-lookup"><span data-stu-id="4b84c-127">When you design something for HoloLens, it is important to experience your design in the device.</span></span> <span data-ttu-id="4b84c-128">Mixed reality アプリ設計の最大の課題の1つは、特に従来の2D スケッチを通じて、スケール、位置、深さの意味を得るのが難しいことです。</span><span class="sxs-lookup"><span data-stu-id="4b84c-128">One of the biggest challenges in mixed reality app design is that it is hard to get the sense of scale, position and depth, especially through traditional 2D sketches.</span></span>

### <a name="cost-of-2d-based-communication"></a><span data-ttu-id="4b84c-129">2D ベースの通信のコスト</span><span class="sxs-lookup"><span data-stu-id="4b84c-129">Cost of 2D based communication</span></span>

<span data-ttu-id="4b84c-130">UX フローとシナリオを効果的に他のユーザーに伝達するために、デザイナーでは、Illustrator、Photoshop、PowerPoint などの従来の2D ツールを使用して、アセットの作成に時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="4b84c-130">To effectively communicate UX flows and scenarios to others, a designer may end up spending a lot of time creating assets using traditional 2D tools such as Illustrator, Photoshop and PowerPoint.</span></span> <span data-ttu-id="4b84c-131">これらの2D デザインでは、多くの場合、3D に変換するための追加の作業が必要になります。</span><span class="sxs-lookup"><span data-stu-id="4b84c-131">These 2D designs often require additional effort to convert them it into 3D.</span></span> <span data-ttu-id="4b84c-132">2D から3D への変換では、いくつかのアイデアが失われています。</span><span class="sxs-lookup"><span data-stu-id="4b84c-132">Some ideas are lost in this translation from 2D to 3D.</span></span>

### <a name="complex-deployment-process"></a><span data-ttu-id="4b84c-133">複雑な展開プロセス</span><span class="sxs-lookup"><span data-stu-id="4b84c-133">Complex deployment process</span></span>

<span data-ttu-id="4b84c-134">Mixed reality は新しいキャンバスであるため、さまざまな設計イテレーションと評価と、その性質によるエラーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4b84c-134">Since mixed reality is a new canvas for us, it involves a lot of design iteration and trial and error by its nature.</span></span> <span data-ttu-id="4b84c-135">Unity や Visual Studio などのツールに慣れていないデザイナーの場合、HoloLens で簡単にまとめることはできません。</span><span class="sxs-lookup"><span data-stu-id="4b84c-135">For designer who are not familiar with tools such as Unity and Visual Studio, it is not easy to put something together in HoloLens.</span></span> <span data-ttu-id="4b84c-136">通常は、次の手順に従って、デバイス内の 2D/3D アートワークを表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b84c-136">Typically you have to go through the process below to see your 2D/3D artwork in the device.</span></span> <span data-ttu-id="4b84c-137">これは、設計者がアイデアやシナリオを迅速に反復処理するための大きな障壁でした。</span><span class="sxs-lookup"><span data-stu-id="4b84c-137">This was a big barrier for designers iterating on ideas and scenarios quickly.</span></span>

<span data-ttu-id="4b84c-138">![複雑な展開プロセス](images/holosketch-image-03-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="4b84c-138">![Complex deployment process](images/holosketch-image-03-1000px.png)</span></span><br>
<span data-ttu-id="4b84c-139">*デプロイ プロセス*</span><span class="sxs-lookup"><span data-stu-id="4b84c-139">*Deployment process*</span></span>

### <a name="simplified-process-with-holosketch"></a><span data-ttu-id="4b84c-140">HoloSketch を使用した簡素化されたプロセス</span><span class="sxs-lookup"><span data-stu-id="4b84c-140">Simplified process with HoloSketch</span></span>

<span data-ttu-id="4b84c-141">HoloSketch では、開発ツールとデバイスポータルのペアリングを使用しなくても、このプロセスを簡略化する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="4b84c-141">With HoloSketch, we wanted to simplify this process without involving development tools and device portal pairing.</span></span> <span data-ttu-id="4b84c-142">OneDrive を使用すると、ユーザーは簡単に 2D/3D アセットを HoloLens に入れることができます。</span><span class="sxs-lookup"><span data-stu-id="4b84c-142">Using OneDrive, users can easily put 2D/3D assets into HoloLens.</span></span>

<span data-ttu-id="4b84c-143">![HoloSketch を使用した簡素化されたプロセス](images/holosketch-image-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="4b84c-143">![Simplified process with HoloSketch](images/holosketch-image-04-1000px.png)</span></span><br>
<span data-ttu-id="4b84c-144">*HoloSketch を使用した簡素化されたプロセス*</span><span class="sxs-lookup"><span data-stu-id="4b84c-144">*Simplified process with HoloSketch*</span></span>

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a><span data-ttu-id="4b84c-145">3次元設計の考え方と解決策を奨励する</span><span class="sxs-lookup"><span data-stu-id="4b84c-145">Encouraging three-dimensional design thinking and solutions</span></span>

<span data-ttu-id="4b84c-146">このツールを使用すると、デザイナーは、真の3次元空間でソリューションを調査できるようになり、2D では動かなくなります。</span><span class="sxs-lookup"><span data-stu-id="4b84c-146">We thought this tool would give designers an opportunity to explore solutions in a truly three-dimensional space and not be stuck in 2D.</span></span> <span data-ttu-id="4b84c-147">HoloLens の場合、バックグラウンドは実際の世界であるため、UI の背景を作成することを考える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4b84c-147">They don’t have to think about creating a 3D background for their UI since the background is the real world in the case of HoloLens.</span></span> <span data-ttu-id="4b84c-148">HoloSketch を使用すると、デザイナーは HoloLens での3D デザインを簡単に調べることができます。</span><span class="sxs-lookup"><span data-stu-id="4b84c-148">HoloSketch opens up a way for designers to easily explore 3D design on HoloLens.</span></span>

## <a name="get-started"></a><span data-ttu-id="4b84c-149">はじめに</span><span class="sxs-lookup"><span data-stu-id="4b84c-149">Get Started</span></span>

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a><span data-ttu-id="4b84c-150">HoloSketch に2D イメージ (JPG/PNG) をインポートする方法</span><span class="sxs-lookup"><span data-stu-id="4b84c-150">How to import 2D images (JPG/PNG) into HoloSketch</span></span>

* <span data-ttu-id="4b84c-151">JPG/PNG イメージを OneDrive フォルダー ' Documents/HoloSketch ' にアップロードします。</span><span class="sxs-lookup"><span data-stu-id="4b84c-151">Upload JPG/PNG images to your OneDrive folder ‘Documents/HoloSketch’.</span></span>
* <span data-ttu-id="4b84c-152">HoloSketch の OneDrive メニューから、環境内にイメージを選択して配置することができます。</span><span class="sxs-lookup"><span data-stu-id="4b84c-152">From the OneDrive menu in HoloSketch, you will be able to select and place the image in the environment.</span></span>

<span data-ttu-id="4b84c-153">![2D イメージのインポート](images/import-2d-images-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4b84c-153">![Importing 2D images](images/import-2d-images-1000px.jpg)</span></span><br>
<span data-ttu-id="4b84c-154">*OneDrive を使用してイメージと3D オブジェクトをインポートする*</span><span class="sxs-lookup"><span data-stu-id="4b84c-154">*Importing images and 3D objects through OneDrive*</span></span>

### <a name="how-to-import-3d-objects-into-holosketch"></a><span data-ttu-id="4b84c-155">HoloSketch に3D オブジェクトをインポートする方法</span><span class="sxs-lookup"><span data-stu-id="4b84c-155">How to import 3D objects into HoloSketch</span></span>

<span data-ttu-id="4b84c-156">OneDrive フォルダーにアップロードする前に、次の手順に従って、3D オブジェクトを Unity 資産バンドルにパッケージ化してください。</span><span class="sxs-lookup"><span data-stu-id="4b84c-156">Before uploading to your OneDrive folder, please follow the steps below to package your 3D objects into a Unity asset bundle.</span></span> <span data-ttu-id="4b84c-157">このプロセスを使用して、Maya、映画4D、Microsoft Paint 3D などの3D ソフトウェアから FBX/OBJ ファイルをインポートできます。</span><span class="sxs-lookup"><span data-stu-id="4b84c-157">Using this process you can import your FBX/OBJ files from 3D software such as Maya, Cinema 4D and Microsoft Paint 3D.</span></span>

>[!IMPORTANT]
><span data-ttu-id="4b84c-158">現時点では、資産バンドルの作成は、Unity バージョン 5.4.5 f1 でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="4b84c-158">Currently, asset bundle creation is supported with Unity version 5.4.5f1.</span></span>

1. <span data-ttu-id="4b84c-159">Unity プロジェクト [' AssetBunlder_Unity '](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity)をダウンロードして開きます。</span><span class="sxs-lookup"><span data-stu-id="4b84c-159">Download and open the Unity project ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span></span> <span data-ttu-id="4b84c-160">この Unity プロジェクトには、バンドル資産生成用のスクリプトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4b84c-160">This Unity project includes the script for the bundle asset generation.</span></span>
2. <span data-ttu-id="4b84c-161">新しいオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="4b84c-161">Create a new GameObject.</span></span>
3. <span data-ttu-id="4b84c-162">内容に基づいて、このオブジェクトにという名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="4b84c-162">Name the GameObject based on the contents.</span></span>
4. <span data-ttu-id="4b84c-163">[インスペクター] パネルで、[コンポーネントの追加] をクリックし、[Box Collider] を追加します。</span><span class="sxs-lookup"><span data-stu-id="4b84c-163">In the Inspector panel, click ‘Add Component’ and add ‘Box Collider’.</span></span> 

   ![[インスペクター] パネルで、[コンポーネントの追加] をクリックし、[Box Collider] を追加します。](images/holosketch-10a-assetbundles-1000px.png)
   
   ![[インスペクター] パネルで、[コンポーネントの追加] をクリックし、[Box Collider] を追加し #2](images/holosketch-10b-assetbundles-1000px.png)

5. <span data-ttu-id="4b84c-166">3D FBX ファイルを [プロジェクト] パネルにドラッグして、インポートします。</span><span class="sxs-lookup"><span data-stu-id="4b84c-166">Import the 3D FBX file by dragging it into the project panel.</span></span>
6. <span data-ttu-id="4b84c-167">**新しいユーザーオブジェクトの下** にある [階層] パネルにオブジェクトをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4b84c-167">Drag the object into the Hierarchy panel **under your new GameObject** .</span></span>

   ![新しいユーザーオブジェクトの下にある [階層] パネルにオブジェクトをドラッグします。](images/holosketch-12-assetbundles-1000px.png)

7. <span data-ttu-id="4b84c-169">Collider ディメンションがオブジェクトと一致しない場合は、それを調整します。</span><span class="sxs-lookup"><span data-stu-id="4b84c-169">Adjust the collider dimension if it does not match the object.</span></span> <span data-ttu-id="4b84c-170">オブジェクトを **Z 軸** に回転します。</span><span class="sxs-lookup"><span data-stu-id="4b84c-170">Rotate the object to face **Z-axis** .</span></span>

   ![Collider ディメンションがオブジェクトと一致しない場合は調整します。](images/holosketch-13-assetbundles-1000px.png)

8. <span data-ttu-id="4b84c-172">オブジェクトを [階層] パネルから [プロジェクト] パネルにドラッグし **て、prefab** にします。</span><span class="sxs-lookup"><span data-stu-id="4b84c-172">Drag the object from the Hierarchy panel to the Project panel to **make it prefab** .</span></span>
9. <span data-ttu-id="4b84c-173">[インスペクター] パネルの下部にあるドロップダウンリストをクリックし、新しい一意の名前を作成して割り当てます。</span><span class="sxs-lookup"><span data-stu-id="4b84c-173">On the bottom of the inspector panel, click the dropdown, create and assign a new unique name.</span></span> <span data-ttu-id="4b84c-174">次の例では、AssetBundle 名に ' ' を追加して割り当てる方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4b84c-174">Below example shows adding and assigning 'brownchair' for the AssetBundle Name.</span></span> 

   ![[インスペクター] パネルの下部にあるドロップダウンをクリックし、新しい一意の名前を割り当てます。](images/holosketch-14-assetbundles-1000px.png)

10. <span data-ttu-id="4b84c-176">モデルオブジェクトのサムネイル画像を準備します。</span><span class="sxs-lookup"><span data-stu-id="4b84c-176">Prepare a thumbnail image for the model object.</span></span> 
   <span data-ttu-id="4b84c-177">![イメージを [プロジェクト] パネルにドラッグし、オブジェクトに使用する名前を割り当てます。](images/holosketch-15-assetbundles-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="4b84c-177">![Drag an image into the project panel and assign the name used for the object.](images/holosketch-15-assetbundles-1000px.png)</span></span>

11. <span data-ttu-id="4b84c-178">Unity プロジェクトの ' Asset ' フォルダーの下に ' Assetbundles ' という名前のフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="4b84c-178">Create a folder named ‘Assetbundles’ under the Unity project’s ‘Asset’ folder.</span></span>

12. <span data-ttu-id="4b84c-179">[アセット] メニューの [Build AssetBundles] を選択して、ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="4b84c-179">From the Assets menu, select ‘Build AssetBundles’ to generate file.</span></span> 
   <span data-ttu-id="4b84c-180">![[アセット] メニューの [Build AssetBundles] を選択して、ファイルを生成します。](images/holosketch-15a-assetbundles.png)</span><span class="sxs-lookup"><span data-stu-id="4b84c-180">![From the Assets menu, select ‘Build AssetBundles’ to generate file.](images/holosketch-15a-assetbundles.png)</span></span>


13. <span data-ttu-id="4b84c-181">**生成されたファイルを OneDrive の/Files/Documents/HoloSketch フォルダーにアップロードします。**</span><span class="sxs-lookup"><span data-stu-id="4b84c-181">**Upload the generated file to the /Files/Documents/HoloSketch folder on OneDrive.**</span></span> <span data-ttu-id="4b84c-182">Asset_unique_name ファイルのみをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="4b84c-182">Upload the asset_unique_name file only.</span></span> <span data-ttu-id="4b84c-183">マニフェストファイルまたは AssetBundles ファイルをアップロードする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4b84c-183">You don’t need to upload manifest files or AssetBundles file.</span></span> <br>
<span data-ttu-id="4b84c-184">![ファイル/ドキュメント/HoloSketch/フォルダーにファイルを追加 ](images/holosketch-onedriveupload-1000px.png)
 ![ すると、HoloSketch の OneDrive メニューに追加された3d オブジェクトが表示されます](images/holosketch-14-onedriveexample-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4b84c-184">![Add files to Files/Documents/HoloSketch/ folder](images/holosketch-onedriveupload-1000px.png)
![You will see added 3D object in HoloSketch's OneDrive menu](images/holosketch-14-onedriveexample-1000px.jpg)</span></span>

## <a name="how-to-manipulate-the-objects"></a><span data-ttu-id="4b84c-185">オブジェクトを操作する方法</span><span class="sxs-lookup"><span data-stu-id="4b84c-185">How to manipulate the objects</span></span>

<span data-ttu-id="4b84c-186">HoloSketch は、3D ソフトウェアで広く使用されている従来のインターフェイスをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="4b84c-186">HoloSketch supports the traditional interface that is widely used in 3D software.</span></span> <span data-ttu-id="4b84c-187">[移動]、[回転]、[ジェスチャとマウスを使用したオブジェクトの拡大/縮小] を使用できます。</span><span class="sxs-lookup"><span data-stu-id="4b84c-187">You can use move, rotate, scale the objects with gestures and a mouse.</span></span> <span data-ttu-id="4b84c-188">音声またはキーボードを使用して、さまざまなモードをすばやく切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="4b84c-188">You can quickly switch between different modes with voice or keyboard.</span></span>

### <a name="object-manipulation-modes"></a><span data-ttu-id="4b84c-189">オブジェクトの操作モード</span><span class="sxs-lookup"><span data-stu-id="4b84c-189">Object manipulation modes</span></span>

<span data-ttu-id="4b84c-190">![オブジェクトを操作する方法](images/holosketch-image-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="4b84c-190">![How to manipulate the objects](images/holosketch-image-06-1000px.png)</span></span><br>
<span data-ttu-id="4b84c-191">*オブジェクトを操作する方法*</span><span class="sxs-lookup"><span data-stu-id="4b84c-191">*How to manipulate the objects*</span></span>

### <a name="contextual-and-tool-belt-menus"></a><span data-ttu-id="4b84c-192">コンテキストとツールのベルトメニュー</span><span class="sxs-lookup"><span data-stu-id="4b84c-192">Contextual and Tool Belt menus</span></span>

<span data-ttu-id="4b84c-193">**コンテキストメニューの使用**</span><span class="sxs-lookup"><span data-stu-id="4b84c-193">**Using the Contextual Menu**</span></span>

<span data-ttu-id="4b84c-194">ダブルエアタップを押して、コンテキストメニューを開きます。</span><span class="sxs-lookup"><span data-stu-id="4b84c-194">Double air tap to open the Contextual Menu.</span></span> 

<span data-ttu-id="4b84c-195">メニュー項目:</span><span class="sxs-lookup"><span data-stu-id="4b84c-195">Menu items:</span></span>
* <span data-ttu-id="4b84c-196">**レイアウト画面:** これは 3D grid システムで、複数のオブジェクトをレイアウトし、グループとして管理できます。</span><span class="sxs-lookup"><span data-stu-id="4b84c-196">**Layout Surface:** This is a 3D grid system where you can layout multiple objects and manage them as a group.</span></span> <span data-ttu-id="4b84c-197">レイアウト画面をダブルエアタップして、オブジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="4b84c-197">Double air-tap on the Layout Surface to add objects to it.</span></span>
* <span data-ttu-id="4b84c-198">**プリミティブ:** Massing の研究には、キューブ、球体、円柱、およびコーンを使用します。</span><span class="sxs-lookup"><span data-stu-id="4b84c-198">**Primitives:** Use cubes, spheres, cylinders and cones for massing studies.</span></span>
* <span data-ttu-id="4b84c-199">**OneDrive:** OneDrive メニューを開き、オブジェクトをインポートします。</span><span class="sxs-lookup"><span data-stu-id="4b84c-199">**OneDrive:** Open the OneDrive menu to import objects.</span></span>
* <span data-ttu-id="4b84c-200">**ヘルプ:** ヘルプ画面を表示します。</span><span class="sxs-lookup"><span data-stu-id="4b84c-200">**Help:** Displays help screen.</span></span>

<span data-ttu-id="4b84c-201">![コンテキスト メニュー](images/holosketch-image-07.png)</span><span class="sxs-lookup"><span data-stu-id="4b84c-201">![Contextual menu](images/holosketch-image-07.png)</span></span><br>
<span data-ttu-id="4b84c-202">*コンテキスト メニュー*</span><span class="sxs-lookup"><span data-stu-id="4b84c-202">*Contextual menu*</span></span>

<span data-ttu-id="4b84c-203">**ツールベルトメニューの使用**</span><span class="sxs-lookup"><span data-stu-id="4b84c-203">**Using the Tool Belt Menu**</span></span>

<span data-ttu-id="4b84c-204">シーンの移動、回転、拡大/縮小、保存、読み込みは、ツールベルトメニューから行うことができます。</span><span class="sxs-lookup"><span data-stu-id="4b84c-204">Move, Rotate, Scale, Save, and Load Scene are available from the Tool Belt Menu.</span></span> 

## <a name="using-keyboard-gestures-and-voice-commands"></a><span data-ttu-id="4b84c-205">キーボード、ジェスチャ、音声コマンドの使用</span><span class="sxs-lookup"><span data-stu-id="4b84c-205">Using keyboard, gestures and voice commands</span></span>

<span data-ttu-id="4b84c-206">![キーボード、ジェスチャ、音声コマンド](images/holosketch-image-08-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="4b84c-206">![Keyboard, Gestures and Voice Commands](images/holosketch-image-08-1000px.png)</span></span><br>
<span data-ttu-id="4b84c-207">*キーボード、ジェスチャ、音声コマンド*</span><span class="sxs-lookup"><span data-stu-id="4b84c-207">*Keyboard, gestures, and voice commands*</span></span>

## <a name="download-the-app"></a><span data-ttu-id="4b84c-208">アプリのダウンロード</span><span class="sxs-lookup"><span data-stu-id="4b84c-208">Download the app</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><span data-ttu-id="4b84c-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Microsoft Store から無料で HoloSketch アプリをダウンロードしてインストールする</a>
</span><span class="sxs-lookup"><span data-stu-id="4b84c-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Download and install the HoloSketch app for free from the Microsoft Store</a>
</span></span></td>
</tr>
</table>

## <a name="known-issues"></a><span data-ttu-id="4b84c-210">既知の問題</span><span class="sxs-lookup"><span data-stu-id="4b84c-210">Known issues</span></span>
* <span data-ttu-id="4b84c-211">現在、資産バンドルの作成は、 **Unity バージョン 5.4.5 f1** でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="4b84c-211">Currently asset bundle creation is supported with **Unity version 5.4.5f1.**</span></span>
* <span data-ttu-id="4b84c-212">Onedrive のデータの量によっては、OneDrive コンテンツの読み込み中にアプリが停止したかのように表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="4b84c-212">Depending on the amount of data in your OneDrive, the app might appear as if it has stopped while loading OneDrive contents</span></span>
* <span data-ttu-id="4b84c-213">現在、保存および読み込み機能ではプリミティブオブジェクトのみがサポートされています</span><span class="sxs-lookup"><span data-stu-id="4b84c-213">Currently, Save and Load feature only supports primitive objects</span></span>
* <span data-ttu-id="4b84c-214">テキスト、サウンド、ビデオ、および写真メニューは、コンテキストメニューで無効になっています</span><span class="sxs-lookup"><span data-stu-id="4b84c-214">Text, Sound, Video and Photo menus are disabled on the contextual menu</span></span>
* <span data-ttu-id="4b84c-215">ツールベルトメニューの [再生] ボタンをクリックすると、操作ギズモがクリアされます。</span><span class="sxs-lookup"><span data-stu-id="4b84c-215">The Play button on the Tool Belt menu clears the manipulation gizmos</span></span>

## <a name="sharing-your-sketches"></a><span data-ttu-id="4b84c-216">スケッチを共有する</span><span class="sxs-lookup"><span data-stu-id="4b84c-216">Sharing your sketches</span></span>

<span data-ttu-id="4b84c-217">HoloLens でビデオ記録機能を使用するには、「Cortana、Start/Stop レコーディング」と言ってください。</span><span class="sxs-lookup"><span data-stu-id="4b84c-217">You can use the video recording feature in HoloLens by saying 'Hey Cortana, Start/Stop recording'.</span></span> <span data-ttu-id="4b84c-218">ボリュームの上下キーを押して、スケッチの画像を撮影します。</span><span class="sxs-lookup"><span data-stu-id="4b84c-218">Press the volume up/down key together to take a picture of your sketch.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="4b84c-219">著者について</span><span class="sxs-lookup"><span data-stu-id="4b84c-219">About the authors</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="../develop/unity/images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="4b84c-220"><b>駐車中</b></span><span class="sxs-lookup"><span data-stu-id="4b84c-220"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="4b84c-221">UX デザイナー @Microsoft</span><span class="sxs-lookup"><span data-stu-id="4b84c-221">UX Designer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="4b84c-222"><b>パトリック Sebring</b></span><span class="sxs-lookup"><span data-stu-id="4b84c-222"><b>Patrick Sebring</b></span></span><br><span data-ttu-id="4b84c-223">向け @Microsoft</span><span class="sxs-lookup"><span data-stu-id="4b84c-223">Developer @Microsoft</span></span></td>
</tr>
</table> 
