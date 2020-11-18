---
title: 3D アプリ起動ツールの実装 (UWP アプリ)
description: HoloLens とイマーシブ (VR) ヘッドセットの両方で、Windows Mixed Reality UWP アプリとゲーム (Microsoft Store を通じて配布される) の3D アプリランチャーとロゴを作成する方法について説明します。
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D、ロゴ、アイコン、モデリング、ランチャー、3D ランチャー、タイル、live cube、ディープリンク、secondarytile、セカンダリタイル、UWP、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、XML、境界ボックス、unity
ms.openlocfilehash: 926d0b3bb337517b65986f85f6977b3dd1975735
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703198"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a><span data-ttu-id="8e568-104">3D アプリ起動ツールの実装 (UWP アプリ)</span><span class="sxs-lookup"><span data-stu-id="8e568-104">Implement 3D app launchers (UWP apps)</span></span>

> [!NOTE]
> <span data-ttu-id="8e568-105">この機能は、イマーシブヘッドセット用の2017フォール作成者更新プログラム (RS3) の一部として追加されました。 HoloLens では、Windows 10 April 2018 更新プログラムがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8e568-105">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive headsets and is supported by HoloLens with the  Windows 10 April 2018 Update.</span></span> <span data-ttu-id="8e568-106">アプリケーションが10.0.16299 のバージョンをターゲットにしていることを確認してください。これは Windows SDK、HoloLens でのイマーシブヘッドセットと10.0.17125 の以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e568-106">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive Headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="8e568-107">最新の Windows SDK については、 [こちら](https://developer.microsoft.com/windows/downloads/windows-10-sdk)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e568-107">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="8e568-108">[Windows Mixed Reality ホーム](../discover/navigating-the-windows-mixed-reality-home.md)は、アプリケーションを起動する前にユーザーが移動する開始点です。</span><span class="sxs-lookup"><span data-stu-id="8e568-108">The [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="8e568-109">Windows Mixed Reality の UWP アプリケーションを作成する場合、既定では、アプリはアプリのロゴを使用して2D スレートとして起動されます。</span><span class="sxs-lookup"><span data-stu-id="8e568-109">When creating a UWP application for Windows Mixed Reality, by default, apps are launched as 2D slates with their app's logo.</span></span> <span data-ttu-id="8e568-110">Windows Mixed Reality のエクスペリエンスを開発するときに、必要に応じて3D ランチャーを定義して、アプリケーションの既定の2D ランチャーをオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="8e568-110">When developing experiences for Windows Mixed Reality, a 3D launcher can optionally be defined to override the default 2D launcher for your application.</span></span> <span data-ttu-id="8e568-111">一般に、Windows Mixed Reality ホームからユーザーを取得するイマーシブアプリケーションを起動するには、3D ランチャーを使用することをお勧めします。一方、アプリが適切にアクティブ化されている場合は、既定の2D ランチャーが優先されます。</span><span class="sxs-lookup"><span data-stu-id="8e568-111">In general, 3D launchers are recommended for launching immersive applications that take users out of the Windows Mixed Reality home whereas the default 2D launcher is preferred when the app is activated in place.</span></span> <span data-ttu-id="8e568-112">[3d ディープリンク (secondaryTile)](#3d-deep-links-secondarytiles)は、2d UWP アプリ内のコンテンツへの3d ランチャーとして作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="8e568-112">You can also create a [3D deep link (secondaryTile)](#3d-deep-links-secondarytiles) as a 3D launcher to content within a 2D UWP app.</span></span>

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="8e568-113">3D アプリランチャー作成プロセス</span><span class="sxs-lookup"><span data-stu-id="8e568-113">3D app launcher creation process</span></span>

<span data-ttu-id="8e568-114">3D アプリランチャーを作成するには、次の3つの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="8e568-114">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="8e568-115">設計と concepting</span><span class="sxs-lookup"><span data-stu-id="8e568-115">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="8e568-116">モデリングとエクスポート</span><span class="sxs-lookup"><span data-stu-id="8e568-116">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="8e568-117">アプリケーションへの統合 (この記事)</span><span class="sxs-lookup"><span data-stu-id="8e568-117">Integrating it into your application (this article)</span></span>

<span data-ttu-id="8e568-118">アプリケーションのランチャーとして使用する3D アセットは、互換性を確保するために、 [Windows Mixed Reality オーサリングガイドライン](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) を使用して作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e568-118">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="8e568-119">このオーサリング仕様に合わなかった資産は、Windows Mixed Reality ホームではレンダリングされません。</span><span class="sxs-lookup"><span data-stu-id="8e568-119">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="8e568-120">3D ランチャーの構成</span><span class="sxs-lookup"><span data-stu-id="8e568-120">Configuring the 3D launcher</span></span>

<span data-ttu-id="8e568-121">Visual Studio で新しいプロジェクトを作成すると、アプリの名前とロゴを表示する単純な既定のタイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8e568-121">When you create a new project in Visual Studio, it creates a simple default tile that displays your app's name and logo.</span></span> <span data-ttu-id="8e568-122">この2D 表現をカスタム3D モデルに置き換えるには、アプリケーションのアプリケーションマニフェストを編集して、既定のタイル定義の一部として "MixedRealityModel" 要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="8e568-122">To replace this 2D representation with a custom 3D model edit the app manifest of your application to include the “MixedRealityModel” element as part of your default tile definition.</span></span> <span data-ttu-id="8e568-123">2D ランチャーに戻すには、マニフェストから MixedRealityModel 定義を削除するだけです。</span><span class="sxs-lookup"><span data-stu-id="8e568-123">To revert to the 2D launcher just remove the MixedRealityModel definition from the manifest.</span></span>

### <a name="xml"></a><span data-ttu-id="8e568-124">XML</span><span class="sxs-lookup"><span data-stu-id="8e568-124">XML</span></span>

<span data-ttu-id="8e568-125">最初に、現在のプロジェクトでアプリケーションパッケージマニフェストを見つけます。</span><span class="sxs-lookup"><span data-stu-id="8e568-125">First, locate the app package manifest in your current project.</span></span> <span data-ttu-id="8e568-126">既定では、マニフェストには package.appxmanifest という名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="8e568-126">By default, the manifest will be named Package.appxmanifest.</span></span> <span data-ttu-id="8e568-127">Visual Studio を使用している場合は、ソリューションビューアーでマニフェストを右クリックし、[ **ソースの表示** ] を選択して編集用の xml を開きます。</span><span class="sxs-lookup"><span data-stu-id="8e568-127">If you're using Visual Studio, then right-click the manifest in your solution viewer and select **View source** to open the xml for editing.</span></span> 

<span data-ttu-id="8e568-128">マニフェストの先頭に、uap5 スキーマを追加し、それを ignorable 名前空間として含めます。</span><span class="sxs-lookup"><span data-stu-id="8e568-128">At the top of the manifest, add the uap5 schema and include it as an ignorable namespace:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

<span data-ttu-id="8e568-129">次に、アプリケーションの既定のタイルで "MixedRealityModel" を指定します。</span><span class="sxs-lookup"><span data-stu-id="8e568-129">Next specify the "MixedRealityModel" in the default tile for your application:</span></span>

```xml
<Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="ExampleApp.App">
      <uap:VisualElements
        DisplayName="ExampleApp"
        Square150x150Logo="Assets\Logo.png"
        Square44x44Logo="Assets\SmallLogo.png"
        Description="ExampleApp"
        BackgroundColor="#464646">
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb" />
        </uap:DefaultTile>
        <uap:SplashScreen Image="Assets\SplashScreen.png" />
      </uap:VisualElements>
    </Application>
</Applications>
```

<span data-ttu-id="8e568-130">MixedRealityModel 要素は、アプリケーションパッケージに格納されている3D アセットを指すファイルパスを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="8e568-130">The MixedRealityModel elements accepts a file path pointing to a 3D asset stored in your app package.</span></span> <span data-ttu-id="8e568-131">現時点では、glb ファイル形式を使用して配信され、 [Windows Mixed Reality 3d アセットオーサリング手順](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) に対して作成された3d モデルのみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8e568-131">Currently only 3D models delivered using the .glb file format and authored against the [Windows Mixed Reality 3D asset authoring instructions](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) are supported.</span></span> <span data-ttu-id="8e568-132">アセットはアプリパッケージに保存する必要があり、アニメーションは現在サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8e568-132">Assets must be stored in the app package and animation is not currently supported.</span></span> <span data-ttu-id="8e568-133">"Path" パラメーターが空のままの場合、ウィンドウには3D ランチャーではなく2D スレートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e568-133">If the “Path” parameter is left blank Windows will show the 2D slate instead of the 3D launcher.</span></span> <span data-ttu-id="8e568-134">**注:** glb 資産は、アプリをビルドして実行する前に、ビルド設定で "コンテンツ" としてマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e568-134">**Note:** the .glb asset must be marked as "Content" in your build settings before building and running your app.</span></span>


<span data-ttu-id="8e568-135">![ソリューションエクスプローラーで. glb を選択し、[プロパティ] セクションを使用して、ビルド設定で "コンテンツ" としてマークします。](images/buildsetting-content-300px.png)</span><span class="sxs-lookup"><span data-stu-id="8e568-135">![Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings](images/buildsetting-content-300px.png)</span></span><br>
<span data-ttu-id="8e568-136">*ソリューションエクスプローラーで. glb を選択し、[プロパティ] セクションを使用して、ビルド設定で "コンテンツ" としてマークします。*</span><span class="sxs-lookup"><span data-stu-id="8e568-136">*Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings*</span></span>

### <a name="bounding-box"></a><span data-ttu-id="8e568-137">境界ボックス</span><span class="sxs-lookup"><span data-stu-id="8e568-137">Bounding box</span></span>

<span data-ttu-id="8e568-138">境界ボックスを使用すると、必要に応じて、オブジェクトの周囲に追加のバッファー領域を追加できます。</span><span class="sxs-lookup"><span data-stu-id="8e568-138">A bounding box can be used to optionally add an additional buffer region around the object.</span></span> <span data-ttu-id="8e568-139">境界ボックスは、中心点と範囲を使用して指定します。これは、境界ボックスの中心から各軸に沿った端までの距離を示します。</span><span class="sxs-lookup"><span data-stu-id="8e568-139">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="8e568-140">境界ボックスの単位は、1ユニット = 1 メーターにマップできます。</span><span class="sxs-lookup"><span data-stu-id="8e568-140">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="8e568-141">境界ボックスが指定されていない場合は、オブジェクトのメッシュに自動的に収まるようになります。</span><span class="sxs-lookup"><span data-stu-id="8e568-141">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="8e568-142">指定された境界ボックスがモデルより小さい場合、メッシュに合わせてサイズが変更されます。</span><span class="sxs-lookup"><span data-stu-id="8e568-142">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

<span data-ttu-id="8e568-143">境界ボックス属性のサポートには、MixedRealityModel 要素のプロパティとして Windows RS4 update が使用されます。</span><span class="sxs-lookup"><span data-stu-id="8e568-143">Support for the bounding box attribute will come with the Windows RS4 update as a property on the MixedRealityModel element.</span></span> <span data-ttu-id="8e568-144">最初にアプリケーションマニフェストの最上部にある境界ボックスを定義するには、uap6 スキーマを追加し、それを無視できる名前空間として含めます。</span><span class="sxs-lookup"><span data-stu-id="8e568-144">To define a bounding box first at the top of the app manifest add the uap6 schema and include it them as ignorable namespaces:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
<span data-ttu-id="8e568-145">次に、MixedRealityModel で、SpatialBoundingBox プロパティを設定して境界ボックスを定義します。</span><span class="sxs-lookup"><span data-stu-id="8e568-145">Next, on the MixedRealityModel set the SpatialBoundingBox property to define the bounding box:</span></span> 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a><span data-ttu-id="8e568-146">Unity の使用</span><span class="sxs-lookup"><span data-stu-id="8e568-146">Using Unity</span></span>

<span data-ttu-id="8e568-147">Unity を使用する場合は、アプリケーションマニフェストを編集する前に、Visual Studio でプロジェクトをビルドして開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e568-147">When working with Unity the project must be built and opened in Visual Studio before the App Manifest can be edited.</span></span> 

>[!NOTE]
><span data-ttu-id="8e568-148">新しい Visual Studio ソリューションをビルドして Unity からデプロイするときに、マニフェストで3D ランチャーを再定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e568-148">The 3D launcher must be redefined in the manifest when building and deploying a new Visual Studio solution from Unity.</span></span>

## <a name="3d-deep-links-secondarytiles"></a><span data-ttu-id="8e568-149">3D ディープリンク (secondaryTiles)</span><span class="sxs-lookup"><span data-stu-id="8e568-149">3D deep links (secondaryTiles)</span></span>

> [!NOTE]
> <span data-ttu-id="8e568-150">この機能は、2017秋の RS3 (イマーシブ) のヘッドセット用に、年 4 2018 月の更新プログラム (RS4) の一部として追加されました。</span><span class="sxs-lookup"><span data-stu-id="8e568-150">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive (VR) headsets and as part of the April 2018 Update (RS4) for HoloLens.</span></span> <span data-ttu-id="8e568-151">アプリケーションで Windows SDK のバージョンが対象になっていることを確認します。これは、HoloLens の 10.0.16299 on イマーシブ (VR) ヘッドセットと10.0.17125 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e568-151">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive (VR) headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="8e568-152">最新の Windows SDK については、 [こちら](https://developer.microsoft.com/windows/downloads/windows-10-sdk)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e568-152">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

>[!IMPORTANT]
><span data-ttu-id="8e568-153">3D ディープリンク (secondaryTiles) は、2D UWP アプリでのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="8e568-153">3D deep links (secondaryTiles) only work with 2D UWP apps.</span></span> <span data-ttu-id="8e568-154">ただし、Windows Mixed Reality ホームから排他的なアプリを起動するための [3d アプリランチャー](implementing-3d-app-launchers.md) を作成できます。</span><span class="sxs-lookup"><span data-stu-id="8e568-154">You can, however, create a [3D app launcher](implementing-3d-app-launchers.md) to launch an exclusive app from the Windows Mixed Reality home.</span></span>

<span data-ttu-id="8e568-155">Windows の [スタート] メニューの[2d セカンダリタイル](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles)と同じように、アプリから[windows mixed Reality ホーム](../discover/navigating-the-windows-mixed-reality-home.md)に3d モデルを配置する機能を、2d アプリ内のコンテンツへのディープリンクとして追加することで、windows Mixed reality 向けに2d アプリケーションを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="8e568-155">Your 2D applications can be enhanced for Windows Mixed Reality by adding the ability to place 3D models from your app into the [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) as deep links to content within your 2D app, just like [2D secondary tiles](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) on the Windows Start menu.</span></span> <span data-ttu-id="8e568-156">たとえば、360°フォトビューアーアプリに直接リンクする360°の球体を作成したり、ユーザーが資産のコレクションから3D コンテンツを配置して、作成者に関する詳細ページを開いたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="8e568-156">For example, you can create 360° photospheres that link directly into a 360° photo viewer app, or let users place 3D content from a collection of assets that opens a details page about the author.</span></span> <span data-ttu-id="8e568-157">3D コンテンツを使用して2D アプリケーションの機能を拡張するには、次の2つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="8e568-157">These are just a couple ways to expand the functionality of your 2D application with 3D content.</span></span>

### <a name="creating-a-3d-secondarytile"></a><span data-ttu-id="8e568-158">3D "secondaryTile" の作成</span><span class="sxs-lookup"><span data-stu-id="8e568-158">Creating a 3D “secondaryTile”</span></span>

<span data-ttu-id="8e568-159">作成時に mixed reality モデルを定義することで、"secondaryTiles" を使用してアプリケーションの3D コンテンツを配置できます。</span><span class="sxs-lookup"><span data-stu-id="8e568-159">You can place 3D content from your application using “secondaryTiles” by defining a mixed reality model at creation time.</span></span> <span data-ttu-id="8e568-160">混合現実モデルは、アプリケーションパッケージ内の3D アセットを参照し、必要に応じて境界ボックスを定義することによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="8e568-160">Mixed reality models are created by referencing a 3D asset in your app package and optionally defining a bounding box.</span></span> 

> [!NOTE]
> <span data-ttu-id="8e568-161">排他ビュー内から "secondaryTiles" を作成することは現在サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8e568-161">Creating “secondaryTiles” from within an exclusive view is not currently supported.</span></span>

```cs
using Windows.UI.StartScreen;
using Windows.Foundation.Numerics;
using Windows.Perception.Spatial;

// Initialize the tile
SecondaryTile tile = new SecondaryTile("myTileId")
{
    DisplayName = "My Tile",
    Arguments = "myArgs"
};

tile.VisualElements.Square150x150Logo = new Uri("ms-appx:///Assets/MyTile/Square150x150Logo.png");

//Assign 3D model (only ms-appx and ms-appdata are allowed)
TileMixedRealityModel model = tile.VisualElements.MixedRealityModel;
model.Uri = new Uri("ms-appx:///Assets/MyTile/MixedRealityModel.glb");
model.ActivationBehavior = TileMixedRealityModelActivationBehavior.Default;
model.BoundingBox = new SpatialBoundingBox
{
    Center = new Vector3 { X = 1, Y = 0, Z = 0 },
    Extents = new Vector3 { X = 3, Y = 5, Z = 4 }
};

// And place it
await tile.RequestCreateAsync();
```

### <a name="bounding-box"></a><span data-ttu-id="8e568-162">境界ボックス</span><span class="sxs-lookup"><span data-stu-id="8e568-162">Bounding box</span></span>

<span data-ttu-id="8e568-163">境界ボックスを使用すると、オブジェクトの周囲に追加のバッファー領域を追加できます。</span><span class="sxs-lookup"><span data-stu-id="8e568-163">A bounding box can be used to add an additional buffer region around the object.</span></span> <span data-ttu-id="8e568-164">境界ボックスは、中心点と範囲を使用して指定します。これは、境界ボックスの中心から各軸に沿った端までの距離を示します。</span><span class="sxs-lookup"><span data-stu-id="8e568-164">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="8e568-165">境界ボックスの単位は、1ユニット = 1 メーターにマップできます。</span><span class="sxs-lookup"><span data-stu-id="8e568-165">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="8e568-166">境界ボックスが指定されていない場合は、オブジェクトのメッシュに自動的に収まるようになります。</span><span class="sxs-lookup"><span data-stu-id="8e568-166">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="8e568-167">指定された境界ボックスがモデルより小さい場合、メッシュに合わせてサイズが変更されます。</span><span class="sxs-lookup"><span data-stu-id="8e568-167">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="8e568-168">アクティベーションの動作</span><span class="sxs-lookup"><span data-stu-id="8e568-168">Activation behavior</span></span>

> [!NOTE]
> <span data-ttu-id="8e568-169">この機能は、Windows RS4 update でサポートされる予定です。</span><span class="sxs-lookup"><span data-stu-id="8e568-169">This feature will be supported as of the Windows RS4 update.</span></span> <span data-ttu-id="8e568-170">この機能を使用する予定がある場合は Windows SDK、アプリケーションが10.0.17125 以上のバージョンを対象としていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8e568-170">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.17125 if you plan to use this feature</span></span>

<span data-ttu-id="8e568-171">3D secondaryTile のアクティベーション動作を定義して、ユーザーがそれを選択したときの反応を制御できます。</span><span class="sxs-lookup"><span data-stu-id="8e568-171">You can define the activation behavior for a 3D secondaryTile to control how it reacts when a user selects it.</span></span> <span data-ttu-id="8e568-172">これを使用すると、純粋な情報または装飾のある混合現実ホームに3D オブジェクトを配置できます。</span><span class="sxs-lookup"><span data-stu-id="8e568-172">This can be used to place 3D objects in the Mixed Reality home that are purely informative or decorative.</span></span> <span data-ttu-id="8e568-173">次のアクティブ化動作の種類がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8e568-173">The following activation behavior types are supported:</span></span>
1. <span data-ttu-id="8e568-174">既定: ユーザーが 3D secondaryTile を選択すると、アプリがアクティブ化されます</span><span class="sxs-lookup"><span data-stu-id="8e568-174">Default: When a user selects the 3D secondaryTile the app is activated</span></span>
2. <span data-ttu-id="8e568-175">None: ユーザーが 3D secondaryTile を選択しても何も起こりません。アプリはアクティブ化されません。</span><span class="sxs-lookup"><span data-stu-id="8e568-175">None: When the users selects the 3D secondaryTile nothing happens and the app is not activated.</span></span>

### <a name="obtaining-and-updating-an-existing-secondarytile"></a><span data-ttu-id="8e568-176">既存の "secondaryTile" の取得と更新</span><span class="sxs-lookup"><span data-stu-id="8e568-176">Obtaining and updating an existing “secondaryTile”</span></span>

<span data-ttu-id="8e568-177">開発者は、既存のセカンダリタイルの一覧を取得できます。これには、前に指定したプロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8e568-177">Developers can get back a list of their existing secondary tiles, which includes the properties that they previously specified.</span></span> <span data-ttu-id="8e568-178">また、値を変更し、UpdateAsync () を呼び出すことによって、プロパティを更新することもできます。</span><span class="sxs-lookup"><span data-stu-id="8e568-178">They can also update the properties by changing the value and then calling UpdateAsync().</span></span>

```cs
// Grab the existing secondary tile
SecondaryTile tile = (await SecondaryTile.FindAllAsync()).First();

Uri updatedUri = new Uri("ms-appdata:///local/MixedRealityUpdated.glb");

// See if the model needs updating
if (!tile.VisualElements.MixedRealityModel.Uri.Equals(updatedUri))
{
    // Update it
    tile.VisualElements.MixedRealityModel.Uri = updatedUri;

    // And apply the changes
    await tile.UpdateAsync();
}
```

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a><span data-ttu-id="8e568-179">ユーザーが Windows Mixed Reality であることを確認しています</span><span class="sxs-lookup"><span data-stu-id="8e568-179">Checking that the user is in Windows Mixed Reality</span></span>

<span data-ttu-id="8e568-180">3D ディープリンク (secondaryTiles) は、ビューが Windows Mixed Reality ヘッドセットに表示されている場合にのみ作成できます。</span><span class="sxs-lookup"><span data-stu-id="8e568-180">3D deep links (secondaryTiles) can only be created while the view is being displayed in a Windows Mixed Reality headset.</span></span> <span data-ttu-id="8e568-181">Windows Mixed Reality ヘッドセットにビューが表示されない場合は、エントリポイントを非表示にするか、エラーメッセージを表示することで、これを適切に処理することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8e568-181">When your view isn't being presented in a Windows Mixed Reality headset we recommend gracefully handling this by either hiding the entry point or showing an error message.</span></span> <span data-ttu-id="8e568-182">これを確認するには、 [IsCurrentViewPresentedOnHolographic ()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)に対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="8e568-182">You can check this by querying [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span></span>

## <a name="tile-notifications"></a><span data-ttu-id="8e568-183">タイル通知</span><span class="sxs-lookup"><span data-stu-id="8e568-183">Tile notifications</span></span>

<span data-ttu-id="8e568-184">タイルの通知では、3D アセットを使用した更新の送信は現在サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8e568-184">Tile notifications do not currently support sending an update with a 3D asset.</span></span> <span data-ttu-id="8e568-185">これは、開発者が次のことを行うことができないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="8e568-185">This means that developers will not be able to do the following</span></span>
* <span data-ttu-id="8e568-186">プッシュ通知</span><span class="sxs-lookup"><span data-stu-id="8e568-186">Push Notifications</span></span>
* <span data-ttu-id="8e568-187">定期的なポーリング</span><span class="sxs-lookup"><span data-stu-id="8e568-187">Periodic Polling</span></span>
* <span data-ttu-id="8e568-188">スケジュールされた通知</span><span class="sxs-lookup"><span data-stu-id="8e568-188">Scheduled Notifications</span></span>

<span data-ttu-id="8e568-189">その他のタイルの特徴と属性、およびそれらを2D タイルに使用する方法の詳細については、 [UWP アプリのドキュメントのタイル](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e568-189">For more information on the other tiles features and attributes and how they are used for 2D tiles refer to the [Tiles for UWP Apps documentation](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span></span>

## <a name="see-also"></a><span data-ttu-id="8e568-190">関連項目</span><span class="sxs-lookup"><span data-stu-id="8e568-190">See also</span></span>

* <span data-ttu-id="8e568-191">3D アプリランチャーを含む[Mixed reality モデルサンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)。</span><span class="sxs-lookup"><span data-stu-id="8e568-191">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="8e568-192">3D アプリ起動ツールの設計ガイダンス</span><span class="sxs-lookup"><span data-stu-id="8e568-192">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="8e568-193">Windows Mixed Reality ホームで使用するための3D モデルの作成</span><span class="sxs-lookup"><span data-stu-id="8e568-193">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="8e568-194">3D アプリランチャーの実装 (Win32 アプリ)</span><span class="sxs-lookup"><span data-stu-id="8e568-194">Implementing 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
* [<span data-ttu-id="8e568-195">Windows Mixed Reality ホームのナビゲーション</span><span class="sxs-lookup"><span data-stu-id="8e568-195">Navigating the Windows Mixed Reality home</span></span>](../discover/navigating-the-windows-mixed-reality-home.md)
