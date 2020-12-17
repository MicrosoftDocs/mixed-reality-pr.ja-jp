---
title: Unity に Mixed Reality OpenXR プラグインを使用する
description: Unity プロジェクトで Mixed Reality OpenXR プラグインを有効にする方法について説明します。
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 拡張現実, 仮想現実, mixed reality ヘッドセット, 学習, チュートリアル, 概要
ms.openlocfilehash: adb678d168d86dc2376ac46caa690e5db036099c
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2020
ms.locfileid: "97622981"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="415a9-104">Unity に Mixed Reality OpenXR プラグインを使用する</span><span class="sxs-lookup"><span data-stu-id="415a9-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="415a9-105">Unity バージョン2020.2 以降、Microsoft の Mixed Reality OpenXR プラグインパッケージは、Unity パッケージマネージャー (UPM) を使用して利用できます。</span><span class="sxs-lookup"><span data-stu-id="415a9-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="415a9-106">[前提条件]</span><span class="sxs-lookup"><span data-stu-id="415a9-106">Prerequisites</span></span>

*   <span data-ttu-id="415a9-107">Unity 2020.2 以降</span><span class="sxs-lookup"><span data-stu-id="415a9-107">Unity 2020.2 or later</span></span>
*   <span data-ttu-id="415a9-108">Unity OpenXR plugin 0.1.1 以降</span><span class="sxs-lookup"><span data-stu-id="415a9-108">Unity OpenXR plugin 0.1.1 or later</span></span>
*   <span data-ttu-id="415a9-109">Visual Studio 2019 以降</span><span class="sxs-lookup"><span data-stu-id="415a9-109">Visual Studio 2019 or later</span></span>
*   <span data-ttu-id="415a9-110">HoloLens 2 アプリの **UWP** プラットフォームサポートを Unity でインストールする</span><span class="sxs-lookup"><span data-stu-id="415a9-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="415a9-111">Windows PC で VR アプリケーションを構築している場合、Mixed Reality OpenXR プラグインは必ずしも必要ではありません。</span><span class="sxs-lookup"><span data-stu-id="415a9-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="415a9-112">ただし、HP リバーブ G2 コントローラーのコントローラーマッピングをカスタマイズしている場合、または HoloLens 2 と VR ヘッドセットの両方で動作するアプリを作成する場合は、プラグインをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="415a9-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="installing-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="415a9-113">Mixed Reality OpenXR プラグインのインストール</span><span class="sxs-lookup"><span data-stu-id="415a9-113">Installing the Mixed Reality OpenXR plugin</span></span>

<span data-ttu-id="415a9-114">Mixed Reality OpenXR プラグインを使用する前に、Unity の **OpenXR プラグイン** と **XR プラグインの管理** パッケージをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="415a9-114">Before using the Mixed Reality OpenXR Plugin, you need to install Unity’s **OpenXR Plugin** and **XR Plugin Management** packages:</span></span>

1. <span data-ttu-id="415a9-115">Unity エディターで、[ **> プロジェクトの設定の編集] > [パッケージマネージャー** ] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="415a9-115">In the Unity Editor, navigate to **Edit > Project Settings > Package Manager**</span></span>
2. <span data-ttu-id="415a9-116">[スコープされた **レジストリ** ] セクションを展開し、次の情報を入力して、[ **保存**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="415a9-116">Expand the **Scoped Registries** section, enter the following information, and select **Save**:</span></span>   
    * <span data-ttu-id="415a9-117">**名前** を **Microsoft Mixed Reality** に設定する</span><span class="sxs-lookup"><span data-stu-id="415a9-117">Set **Name** to **Microsoft Mixed Reality**</span></span>
    * <span data-ttu-id="415a9-118">**URL** をに設定 **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span><span class="sxs-lookup"><span data-stu-id="415a9-118">Set **URL** to **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span></span>
    * <span data-ttu-id="415a9-119">**スコープ** を mixedreality に設定し **ます。**</span><span class="sxs-lookup"><span data-stu-id="415a9-119">Set **Scope(s)** to **com.microsoft.mixedreality**</span></span>

3. <span data-ttu-id="415a9-120">[**詳細設定**] で、[**プレビューパッケージを有効にする**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="415a9-120">Under **Advanced Settings**, select **Enable Preview Packages**</span></span>

![[プロジェクトの設定] で開いている Unity パッケージマネージャーウィンドウのスクリーンショット](images/openxr-img-01.png)

<span data-ttu-id="415a9-122">Unity パッケージマネージャーでは、 *manifest.js* という名前のマニフェストファイルを使用して、インストールするパッケージとインストール可能なレジストリを決定します。</span><span class="sxs-lookup"><span data-stu-id="415a9-122">The Unity Package Manager uses a manifest file named *manifest.json* to determine which packages to install and the registries they can be installed from.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="415a9-123">OpenXR は引き続き Unity で試験段階であり、開発者エクスペリエンスを最適化するために作業するため、このプロセスは時間の経過と共に変わる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="415a9-123">OpenXR is still experimental in Unity and this process may change over time as we work to optimize the developer experience.</span></span>

### <a name="registering-the-mixed-reality-dependency"></a><span data-ttu-id="415a9-124">Mixed Reality 依存関係を登録しています</span><span class="sxs-lookup"><span data-stu-id="415a9-124">Registering the Mixed Reality dependency</span></span>

<span data-ttu-id="415a9-125">Microsoft Mixed Reality スコープのレジストリがマニフェストに追加されたら、OpenXR パッケージを指定できます。</span><span class="sxs-lookup"><span data-stu-id="415a9-125">Once the Microsoft Mixed Reality scoped registry has been added to the manifest, the OpenXR package can be specified.</span></span>

<span data-ttu-id="415a9-126">OpenXR パッケージを追加するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="415a9-126">To add the OpenXR package:</span></span>

1. <span data-ttu-id="415a9-127">次のようなテキストエディターで、 **<projectRoot> /パッケージ/manifest.jsを** 開き Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="415a9-127">Open **<projectRoot>/Packages/manifest.json** in a text editor like Visual Studio Code</span></span>
2. <span data-ttu-id="415a9-128">次のように、ファイルの *Packages/manifest.js* の dependencies セクションを変更します。</span><span class="sxs-lookup"><span data-stu-id="415a9-128">Modify the dependencies section of the *Packages/manifest.json* file as follows:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="415a9-129">マニフェストファイルには、ここに示されている以上の依存関係がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="415a9-129">There may be more dependencies in your manifest file than shown here.</span></span> <span data-ttu-id="415a9-130">これらのいずれも削除しないでください。リストに OpenXR 依存関係を追加するだけです。</span><span class="sxs-lookup"><span data-stu-id="415a9-130">Don't delete any of them, just add the OpenXR dependency to the list.</span></span>

```
  "dependencies": {
    "com.microsoft.mixedreality.openxr": "0.1.0",
  }
```

3. <span data-ttu-id="415a9-131">ファイルを保存し、Unity エディターに戻り、 **パッケージマネージャー** を開いて、プラグインがインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="415a9-131">Save the file, switch back to the Unity Editor, and open the **Package Manager** to confirm the plugin is installed:</span></span> 

![Mixed Reality OpenXR プラグインが強調表示されている unity エディターで開く Unity パッケージマネージャーのスクリーンショット](images/openxr-img-03.png)

> [!Note] 
> <span data-ttu-id="415a9-133">Unity パッケージマネージャーを使用して OpenXR パッケージを削除した場合は、前に説明した手順を使用して、パッケージを再度追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="415a9-133">If the OpenXR package is removed using the Unity Package Manager, you'll have to re-add it using the previously described steps.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="415a9-134">OpenXR の XR Plugin Management の構成</span><span class="sxs-lookup"><span data-stu-id="415a9-134">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="415a9-135">Unity のランタイムとして OpenXR を設定するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="415a9-135">To set OpenXR as the the runtime in Unity:</span></span> 

1. <span data-ttu-id="415a9-136">Unity エディターで、[ **Edit > プロジェクトの設定**] に移動します。</span><span class="sxs-lookup"><span data-stu-id="415a9-136">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="415a9-137">設定の一覧で、[ **XR Plugin Management** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="415a9-137">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="415a9-138">**[XR On Startup** and **OpenXR (プレビュー)** ] ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="415a9-138">Check the **Initialize XR on Startup** and **OpenXR (Preview)** boxes</span></span>
4. <span data-ttu-id="415a9-139">HoloLens 2 を対象とする場合は、UWP プラットフォームを使用していることを確認し、[ **Microsoft HoloLens] 機能セット** を選択します。</span><span class="sxs-lookup"><span data-stu-id="415a9-139">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![XR プラグイン管理が強調表示されている Unity エディターで開いているプロジェクト設定パネルのスクリーンショット](images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="415a9-141">**OpenXR Plugin (Preview)** の横に赤い警告アイコンが表示された場合は、アイコンをクリックし、[**すべて修正**] を選択してから続行します。</span><span class="sxs-lookup"><span data-stu-id="415a9-141">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="415a9-142">変更を有効にするには、Unity エディター自体を再起動することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="415a9-142">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![OpenXR プロジェクト検証ウィンドウのスクリーンショット](images/openxr-img-06.png)

<span data-ttu-id="415a9-144">Unity で OpenXR を使用して開発を始める準備ができました。</span><span class="sxs-lookup"><span data-stu-id="415a9-144">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="415a9-145">OpenXR サンプルの使用方法については、次のセクションに進んでください。</span><span class="sxs-lookup"><span data-stu-id="415a9-145">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="optimization"></a><span data-ttu-id="415a9-146">Optimization</span><span class="sxs-lookup"><span data-stu-id="415a9-146">Optimization</span></span>

<span data-ttu-id="415a9-147">HoloLens 2 用に開発している場合は、 **Mixed Reality> > OpenXR に移動し、hololens 2 に推奨されるプロジェクト設定を適用して** 、アプリのパフォーマンスを向上させます。</span><span class="sxs-lookup"><span data-stu-id="415a9-147">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![OpenXR が選択された状態で開いている mixed reality メニュー項目のスクリーンショット](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="415a9-149">Unity のサンプルシーンを試す</span><span class="sxs-lookup"><span data-stu-id="415a9-149">Try out the Unity sample scenes</span></span>

<span data-ttu-id="415a9-150">1つ以上の例を使用するには、**パッケージ Manager** から [arfoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="415a9-150">To utilize one or more of the examples, install [ARFoundation 4.0+](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) from the **Pacakage Manager**:</span></span>

![Unity エディターで、AR Foundation が強調表示されている Unity パッケージマネージャーを開くスクリーンショット](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a><span data-ttu-id="415a9-152">HoloLens 2 のサンプル</span><span class="sxs-lookup"><span data-stu-id="415a9-152">HoloLens 2 samples</span></span>

1. <span data-ttu-id="415a9-153">Unity エディターで、[ **] ウィンドウ > [パッケージマネージャー]** の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="415a9-153">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="415a9-154">パッケージの一覧で [ **Mixed Reality OpenXR Plugin** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="415a9-154">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="415a9-155">**サンプル一覧で** サンプルを探し、[**インポート**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="415a9-155">Locate the sample in the **Samples** list and select **Import**</span></span>

![Unity エディターで開く Unity パッケージマネージャーのスクリーンショット Mixed Reality OpenXR プラグインが選択され、サンプルのインポートボタンが強調表示されている](images/openxr-img-10.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
>  <span data-ttu-id="415a9-157">パッケージが更新されると、Unity にはインポートされたサンプルを更新するオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="415a9-157">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="415a9-158">インポートしたサンプルを更新すると、サンプルおよび関連付けられている資産に加えられた変更が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="415a9-158">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="next-steps"></a><span data-ttu-id="415a9-159">次のステップ</span><span class="sxs-lookup"><span data-stu-id="415a9-159">Next steps</span></span> 

<span data-ttu-id="415a9-160">プロジェクトが OpenXR 用に構成され、サンプルにアクセスできるようになったので、OpenXR プラグインで現在サポートされている [機能](openxr-supported-features.md) を確認してください。</span><span class="sxs-lookup"><span data-stu-id="415a9-160">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="see-also"></a><span data-ttu-id="415a9-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="415a9-161">See also</span></span>
* [<span data-ttu-id="415a9-162">MRTK を使用しないプロジェクトの構成</span><span class="sxs-lookup"><span data-stu-id="415a9-162">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="415a9-163">Unity で推奨される設定</span><span class="sxs-lookup"><span data-stu-id="415a9-163">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="415a9-164">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="415a9-164">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)