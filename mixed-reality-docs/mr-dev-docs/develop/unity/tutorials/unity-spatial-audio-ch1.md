---
title: プロジェクトへの空間オーディオの追加
description: Microsoft Spatializer プラグインを Unity プロジェクトに追加して、HoloLens 2 HRTF ハードウェアオフロードにアクセスします。
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality、unity、チュートリアル、hololens2、空間オーディオ、MRTK、mixed reality toolkit、UWP、Windows 10、HRTF、head 関連の転送機能、リバーブ、Microsoft Spatializer
ms.openlocfilehash: 80bf19e8a091bd241e28afff0a42c13ca72e1d45
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007472"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="032b7-104">Unity プロジェクトへの空間オーディオの追加</span><span class="sxs-lookup"><span data-stu-id="032b7-104">Adding spatial audio to your Unity project</span></span>

<span data-ttu-id="032b7-105">HoloLens2 上の Unity の空間オーディオチュートリアルへようこそ。</span><span class="sxs-lookup"><span data-stu-id="032b7-105">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="032b7-106">このチュートリアルでは、次の手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="032b7-106">This tutorial sequence shows:</span></span>
* <span data-ttu-id="032b7-107">Unity の HoloLens 2 でヘッド関連の転送機能 (HRTF) オフロードを使用する方法</span><span class="sxs-lookup"><span data-stu-id="032b7-107">How to use head-related transfer function (HRTF) offload on HoloLens 2 in Unity</span></span>
* <span data-ttu-id="032b7-108">HRTF オフロードを使用するときにリバーブを有効にする方法</span><span class="sxs-lookup"><span data-stu-id="032b7-108">How to enable reverb when using HRTF offload</span></span>

<span data-ttu-id="032b7-109">[Microsoft Spatializer GitHub リポジトリ](https://github.com/microsoft/spatialaudio-unity)には、このチュートリアルシーケンスの完成した Unity プロジェクトが用意されています。</span><span class="sxs-lookup"><span data-stu-id="032b7-109">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span> 

<span data-ttu-id="032b7-110">HRTF ベースの spatialization テクノロジを使用してサウンドを spatialize することの意味と、役に立つ場合の推奨事項については、「 [空間サウンドの設計](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="032b7-110">For an understanding about what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="032b7-111">HRTF offload とは</span><span class="sxs-lookup"><span data-stu-id="032b7-111">What is HRTF offload?</span></span>

<span data-ttu-id="032b7-112">HRTF ベースのアルゴリズムを使用してオーディオを処理するには、大量の特殊な計算が必要です。</span><span class="sxs-lookup"><span data-stu-id="032b7-112">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="032b7-113">HoloLens 2 には、アプリケーションプロセッサに負荷がかからないようにするために使用できる専用のハードウェアが含まれているため、HRTF ベースのアルゴリズムの処理を "オフロード" します。</span><span class="sxs-lookup"><span data-stu-id="032b7-113">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="032b7-114">Microsoft spatializer プラグインを使用すると、アプリケーションで専用の HRTF ハードウェアを利用して、空間オーディオ以外の操作でアプリケーションプロセッサをより多く使用できるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="032b7-114">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="032b7-115">目標</span><span class="sxs-lookup"><span data-stu-id="032b7-115">Objectives</span></span>

<span data-ttu-id="032b7-116">この最初の章では、次のことについて説明します。</span><span class="sxs-lookup"><span data-stu-id="032b7-116">In this first chapter, you'll:</span></span>
* <span data-ttu-id="032b7-117">Unity プロジェクトを作成して MRTK をインポートする</span><span class="sxs-lookup"><span data-stu-id="032b7-117">Create a Unity project and import MRTK</span></span>
* <span data-ttu-id="032b7-118">Microsoft spatializer プラグインをインポートする</span><span class="sxs-lookup"><span data-stu-id="032b7-118">Import the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="032b7-119">Microsoft spatializer プラグインを有効にする</span><span class="sxs-lookup"><span data-stu-id="032b7-119">Enable the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="032b7-120">開発者ワークステーションで空間オーディオを有効にする</span><span class="sxs-lookup"><span data-stu-id="032b7-120">Enable spatial audio on your developer workstation</span></span>

## <a name="create-a-project-and-add-nuget-for-unity"></a><span data-ttu-id="032b7-121">プロジェクトを作成し、Unity の NuGet を追加する</span><span class="sxs-lookup"><span data-stu-id="032b7-121">Create a project and add NuGet for Unity</span></span>

<span data-ttu-id="032b7-122">空の Unity プロジェクトから開始し、Unity 用に NuGet を追加して構成します。</span><span class="sxs-lookup"><span data-stu-id="032b7-122">Start with an empty Unity project, then add and configure NuGet for Unity:</span></span>
1. <span data-ttu-id="032b7-123">最新の NuGetForUnity をダウンロードし [ます。 unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span><span class="sxs-lookup"><span data-stu-id="032b7-123">Download the latest [NuGetForUnity .unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span></span>
2. <span data-ttu-id="032b7-124">Unity のメニューバーで、[ **資産-> インポートパッケージ-> カスタムパッケージ** ] をクリックし、NuGetForUnity パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="032b7-124">In the Unity menu bar, click **Assets -> Import Package -> Custom Package...** and install the NuGetForUnity package:</span></span>

![カスタムパッケージのインポート](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a><span data-ttu-id="032b7-126">Windows Mixed Reality パッケージを追加する</span><span class="sxs-lookup"><span data-stu-id="032b7-126">Add the Windows Mixed Reality package</span></span>

<span data-ttu-id="032b7-127">Unity 2019 以降での Windows Mixed Reality のサポートは、オプションのパッケージに含まれています。</span><span class="sxs-lookup"><span data-stu-id="032b7-127">Windows Mixed Reality support in Unity 2019 and later is contained in an optional package.</span></span> <span data-ttu-id="032b7-128">プロジェクトに追加するには、Unity のメニューバーから [ **Window-> Package Manager]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="032b7-128">To add it to your project, open **Window -> Package Manager** from the Unity menu bar:</span></span>

![パッケージマネージャーメニュー](images/spatial-audio/package-manager-menu.png)

<span data-ttu-id="032b7-130">次に、 **Windows Mixed Reality** パッケージを検索してインストールします。</span><span class="sxs-lookup"><span data-stu-id="032b7-130">Then find and install the **Windows Mixed Reality** package:</span></span>

![パッケージマネージャーウィンドウ](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a><span data-ttu-id="032b7-132">MRTK と Microsoft Spatializer をインストールする</span><span class="sxs-lookup"><span data-stu-id="032b7-132">Install MRTK and Microsoft Spatializer</span></span>

<span data-ttu-id="032b7-133">Unity 用の NuGet を使用して、MRTK と Microsoft Spatializer プラグインをインストールします。</span><span class="sxs-lookup"><span data-stu-id="032b7-133">Using NuGet for Unity, install the MRTK and Microsoft Spatializer plugins:</span></span>
1. <span data-ttu-id="032b7-134">Unity のメニューバーで、[ **nuget->] [Nuget パッケージの管理**] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="032b7-134">In the Unity menu bar, click on **NuGet -> Manage NuGet Packages**.</span></span>

![NuGet パッケージの管理](images/spatial-audio/manage-nuget-packages.png)

2. <span data-ttu-id="032b7-136">**検索** ボックスに「MixedReality」と入力し、MRTK コアパッケージ ( **MixedReality** ) をインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="032b7-136">In the **Search** box, enter "Microsoft.MixedReality.Toolkit" and install the MRTK core package: **Microsoft.MixedReality.Toolkit.Foundation**</span></span>

![MRTK NuGet パッケージ](images/spatial-audio/mrtk-nuget-package.png)

<span data-ttu-id="032b7-138">[Mrtk NuGet パッケージ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) には、追加のコンテキストと詳細があります。</span><span class="sxs-lookup"><span data-stu-id="032b7-138">[MRTK NuGet Package](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) has additional context and details.</span></span>

4. <span data-ttu-id="032b7-139">**検索** ボックスに「SpatialAudio」と入力し、microsoft Spatializer パッケージ: **SpatialAudio** をインストールします。</span><span class="sxs-lookup"><span data-stu-id="032b7-139">In the **Search** box, enter "Microsoft.SpatialAudio" and install the Microsoft Spatializer package: **Microsoft.SpatialAudio.Spatializer.Unity**</span></span>

![Spatializer プラグイン NuGet](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a><span data-ttu-id="032b7-141">プロジェクトでの MRTK の設定</span><span class="sxs-lookup"><span data-stu-id="032b7-141">Set up MRTK in your project</span></span>

1. <span data-ttu-id="032b7-142">[ビルドの設定] ウィンドウを開き、[ **ファイル > ビルドの設定**] に移動します。</span><span class="sxs-lookup"><span data-stu-id="032b7-142">Open the Build Settings window by going to **File -> Build Settings**.</span></span>

2. <span data-ttu-id="032b7-143">_ユニバーサル Windows プラットフォーム_ を選択し、[**プラットフォームの切り替え**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="032b7-143">Select the _Universal Windows Platform_ and click **Switch Platform**.</span></span>

3. <span data-ttu-id="032b7-144">[**ビルド] ウィンドウ** の [**プレーヤーの設定**] をクリックして、[**インスペクター** ] ウィンドウの [**プレーヤーの設定**] プロパティを開きます。</span><span class="sxs-lookup"><span data-stu-id="032b7-144">Click **Player Settings** in the **Build Window** to open the **Player Settings** properties in the **Inspector** pane.</span></span>
    * <span data-ttu-id="032b7-145">[ **XR の設定**] で、[ **Virtual Reality がサポート** する] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="032b7-145">Under **XR Settings**, check the **Virtual Reality Supported** checkbox</span></span>
    * <span data-ttu-id="032b7-146">[ **XR の設定**] で、 **ステレオレンダリングモード** を **シングルパスインスタンス** 化に変更します。</span><span class="sxs-lookup"><span data-stu-id="032b7-146">Under **XR Settings**, change the **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>
    * <span data-ttu-id="032b7-147">[**発行の設定**] で、[**機能**] セクションの [**空間の認識**] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="032b7-147">Under **Publishing Settings**, check the **Spatial Perception** checkbox in the **Capabilities** section</span></span>

4. <span data-ttu-id="032b7-148">メニューバーで [ **Mixed Reality Toolkit-> [シーンに追加] を** クリックし、[構成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="032b7-148">On the menu bar, click **Mixed Reality Toolkit -> Add to Scene and Configure..**</span></span> <span data-ttu-id="032b7-149">を使用して、シーンに MRTK を追加します。</span><span class="sxs-lookup"><span data-stu-id="032b7-149">to add MRTK to your scene.</span></span>

<span data-ttu-id="032b7-150">アプリをビルドして HoloLens 2 にデプロイする方法など、その他のガイダンスについては、 [MR ラーニングベースモジュールの第1章](../../../mrlearning-base-ch1.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="032b7-150">For additional guidance, including how to build your app and deploy to a HoloLens 2, see [Chapter 1 of the MR Learning Base Module](../../../mrlearning-base-ch1.md).</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="032b7-151">Microsoft Spatializer プラグインを有効にする</span><span class="sxs-lookup"><span data-stu-id="032b7-151">Enable the Microsoft Spatializer plugin</span></span>

<span data-ttu-id="032b7-152">**Microsoft Spatializer** プラグインを有効にします。</span><span class="sxs-lookup"><span data-stu-id="032b7-152">Enable the **Microsoft Spatializer** plugin.</span></span> <span data-ttu-id="032b7-153">[ **編集-> プロジェクトの設定-> オーディオ**] を開き、 **Spatializer プラグイン** を "Microsoft Spatializer" に変更します。</span><span class="sxs-lookup"><span data-stu-id="032b7-153">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span> <span data-ttu-id="032b7-154">**プロジェクト設定** の **Audio** セクションは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="032b7-154">The **Audio** section of the **Project Settings** will now look like this:</span></span>

![Spatializer プラグインを表示するプロジェクト設定](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="032b7-156">ワークステーションで空間オーディオを有効にする</span><span class="sxs-lookup"><span data-stu-id="032b7-156">Enable spatial audio on your workstation</span></span>

<span data-ttu-id="032b7-157">Windows のデスクトップバージョンでは、空間オーディオは既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="032b7-157">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="032b7-158">これを有効にするには、タスクバーのボリュームアイコンを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="032b7-158">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="032b7-159">HoloLens 2 で耳になる内容を最大限に活用するには、[ **空間サウンド > Windows Sonic For ヘッドホン**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="032b7-159">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![デスクトップ空間オーディオの設定](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> <span data-ttu-id="032b7-161">この設定は、Unity エディターでプロジェクトをテストする場合にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="032b7-161">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="next-steps"></a><span data-ttu-id="032b7-162">次のステップ</span><span class="sxs-lookup"><span data-stu-id="032b7-162">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="032b7-163">Unity 空間オーディオの第2章</span><span class="sxs-lookup"><span data-stu-id="032b7-163">Unity spatial audio chapter 2</span></span>](unity-spatial-audio-ch2.md)

