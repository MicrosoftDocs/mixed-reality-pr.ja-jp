---
title: Unity に Mixed Reality OpenXR プラグインを使用する
description: Unity プロジェクトで Mixed Reality OpenXR プラグインを有効にする方法について説明します。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 拡張現実, 仮想現実, mixed reality ヘッドセット, 学習, チュートリアル, 概要
ms.openlocfilehash: 1adfb979cfc22be5da18ed990c9db55e6bad97f3
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2021
ms.locfileid: "99238141"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="648e6-104">Unity に Mixed Reality OpenXR プラグインを使用する</span><span class="sxs-lookup"><span data-stu-id="648e6-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="648e6-105">Unity バージョン2020.2 以降、Microsoft の Mixed Reality OpenXR プラグインパッケージは、Unity パッケージマネージャー (UPM) を使用して利用できます。</span><span class="sxs-lookup"><span data-stu-id="648e6-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="648e6-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="648e6-106">Prerequisites</span></span>

* <span data-ttu-id="648e6-107">Unity 2020.2 以降</span><span class="sxs-lookup"><span data-stu-id="648e6-107">Unity 2020.2 or later</span></span>
* <span data-ttu-id="648e6-108">Unity OpenXR plugin 0.1.2 以降</span><span class="sxs-lookup"><span data-stu-id="648e6-108">Unity OpenXR plugin 0.1.2 or later</span></span>
* <span data-ttu-id="648e6-109">Visual Studio 2019 以降</span><span class="sxs-lookup"><span data-stu-id="648e6-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="648e6-110">HoloLens 2 アプリの **UWP** プラットフォームサポートを Unity でインストールする</span><span class="sxs-lookup"><span data-stu-id="648e6-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="648e6-111">Windows PC で VR アプリケーションを構築している場合、Mixed Reality OpenXR プラグインは必ずしも必要ではありません。</span><span class="sxs-lookup"><span data-stu-id="648e6-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="648e6-112">ただし、HP リバーブ G2 コントローラーのコントローラーマッピングをカスタマイズしている場合、または HoloLens 2 と VR ヘッドセットの両方で動作するアプリを作成する場合は、プラグインをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="648e6-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="installing-openxr-with-the-mixed-reality-feature-tool"></a><span data-ttu-id="648e6-113">Mixed Reality 機能ツールを使用した OpenXR のインストール</span><span class="sxs-lookup"><span data-stu-id="648e6-113">Installing OpenXR with the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="648e6-114">新しい Mixed Reality 機能ツールアプリケーションを使用して OpenXR プラグインをインストールします。</span><span class="sxs-lookup"><span data-stu-id="648e6-114">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="648e6-115">[インストールと使用に関する指示](welcome-to-mr-feature-tool.md)に従って、Mixed reality Toolkit カテゴリで **Mixed reality OpenXR プラグイン** パッケージを選択します。</span><span class="sxs-lookup"><span data-stu-id="648e6-115">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Open xr plugin が強調表示されている Mixed Reality 機能ツールパッケージウィンドウ](images/feature-tool-openxr.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="648e6-117">OpenXR の XR Plugin Management の構成</span><span class="sxs-lookup"><span data-stu-id="648e6-117">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="648e6-118">Unity のランタイムとして OpenXR を設定するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="648e6-118">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="648e6-119">Unity エディターで、[ **Edit > プロジェクトの設定**] に移動します。</span><span class="sxs-lookup"><span data-stu-id="648e6-119">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="648e6-120">設定の一覧で、[ **XR Plugin Management** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="648e6-120">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="648e6-121">**[XR On Startup** and **OpenXR (プレビュー)** ] ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="648e6-121">Check the **Initialize XR on Startup** and **OpenXR (Preview)** boxes</span></span>
4. <span data-ttu-id="648e6-122">HoloLens 2 を対象とする場合は、UWP プラットフォームを使用していることを確認し、[ **Microsoft HoloLens] 機能セット** を選択します。</span><span class="sxs-lookup"><span data-stu-id="648e6-122">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![XR プラグイン管理が強調表示されている Unity エディターで開いているプロジェクト設定パネルのスクリーンショット](images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="648e6-124">**OpenXR Plugin (Preview)** の横に赤い警告アイコンが表示された場合は、アイコンをクリックし、[**すべて修正**] を選択してから続行します。</span><span class="sxs-lookup"><span data-stu-id="648e6-124">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="648e6-125">変更を有効にするには、Unity エディター自体を再起動することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="648e6-125">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![OpenXR プロジェクト検証ウィンドウのスクリーンショット](images/openxr-img-06.png)

<span data-ttu-id="648e6-127">Unity で OpenXR を使用して開発を始める準備ができました。</span><span class="sxs-lookup"><span data-stu-id="648e6-127">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="648e6-128">OpenXR サンプルの使用方法については、次のセクションに進んでください。</span><span class="sxs-lookup"><span data-stu-id="648e6-128">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="optimization"></a><span data-ttu-id="648e6-129">Optimization</span><span class="sxs-lookup"><span data-stu-id="648e6-129">Optimization</span></span>

<span data-ttu-id="648e6-130">HoloLens 2 用に開発している場合は、 **Mixed Reality> > OpenXR に移動し、hololens 2 に推奨されるプロジェクト設定を適用して** 、アプリのパフォーマンスを向上させます。</span><span class="sxs-lookup"><span data-stu-id="648e6-130">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![OpenXR が選択された状態で開いている mixed reality メニュー項目のスクリーンショット](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="648e6-132">Unity のサンプルシーンを試す</span><span class="sxs-lookup"><span data-stu-id="648e6-132">Try out the Unity sample scenes</span></span>

<span data-ttu-id="648e6-133">1つ以上の例を使用するには、**パッケージマネージャー** から [arfoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="648e6-133">To utilize one or more of the examples, install [ARFoundation 4.0+](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) from the **Package Manager**:</span></span>

![Unity エディターで、AR Foundation が強調表示されている Unity パッケージマネージャーを開くスクリーンショット](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a><span data-ttu-id="648e6-135">HoloLens 2 のサンプル</span><span class="sxs-lookup"><span data-stu-id="648e6-135">HoloLens 2 samples</span></span>

1. <span data-ttu-id="648e6-136">Unity エディターで、[ **] ウィンドウ > [パッケージマネージャー]** の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="648e6-136">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="648e6-137">パッケージの一覧で [ **Mixed Reality OpenXR Plugin** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="648e6-137">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="648e6-138">**サンプル一覧で** サンプルを探し、[**インポート**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="648e6-138">Locate the sample in the **Samples** list and select **Import**</span></span>

![Unity エディターで開く Unity パッケージマネージャーのスクリーンショット Mixed Reality OpenXR プラグインが選択され、サンプルのインポートボタンが強調表示されている](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="648e6-140">パッケージが更新されると、Unity にはインポートされたサンプルを更新するオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="648e6-140">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="648e6-141">インポートしたサンプルを更新すると、サンプルおよび関連付けられている資産に加えられた変更が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="648e6-141">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="648e6-142">OpenXR サポートでの MRTK の使用</span><span class="sxs-lookup"><span data-stu-id="648e6-142">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="648e6-143">MRTK Unity では、2.5.3 リリース以降の Mixed Reality OpenXR プラグインがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="648e6-143">MRTK Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>  

1. <span data-ttu-id="648e6-144">[Mixed Reality 機能ツール](welcome-to-mr-feature-tool.md)をもう一度開き、プラットフォームサポートカテゴリで **Mixed reality OpenXR プラグイン** パッケージを選択します。</span><span class="sxs-lookup"><span data-stu-id="648e6-144">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again and select the **Mixed Reality OpenXR Plugin** package in the Platform Support category</span></span>

<!-- MRTK plugins can be installed from the same scoped registries as you set up when [installing the Mixed Reality OpenXR plugin](#installing-the-mixed-reality-openxr-plugin). You can find more detailed information in the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/usingupm.html#registering-the-mixed-reality-component-server).

1. Add following packages in your **[projectRoot]/Packages/manifest.json** file:

```json
"dependencies": {
    "com.microsoft.mixedreality.toolkit.foundation": "2.5.3",
    "com.microsoft.mixedreality.toolkit.tools": "2.5.3",
    "com.microsoft.mixedreality.toolkit.examples": "2.5.3",
    …
}
``` -->

2. <span data-ttu-id="648e6-145">インスペクターの MixedReality Toolkit コンポーネントスクリプトに移動し、 **DefaultOpenXRConfigurationProfile** プロファイルに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="648e6-145">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

![インスペクターの Mixed Reality Toolkit コンポーネントでの MRTK 構成の切り替えのスクリーンショット](images/openxr-img-11.png)

### <a name="known-issues"></a><span data-ttu-id="648e6-147">既知の問題</span><span class="sxs-lookup"><span data-stu-id="648e6-147">Known issues</span></span> 

<span data-ttu-id="648e6-148">ハンドトラッキング機能を使用する場合は、 **Assets/MixedRealityToolkit/link.xml** ファイルに次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="648e6-148">When using the Hand Tracking feature, add following line in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>

```
<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
```

## <a name="next-steps"></a><span data-ttu-id="648e6-149">次の手順</span><span class="sxs-lookup"><span data-stu-id="648e6-149">Next steps</span></span>

<span data-ttu-id="648e6-150">プロジェクトが OpenXR 用に構成され、サンプルにアクセスできるようになったので、OpenXR プラグインで現在サポートされている [機能](openxr-supported-features.md) を確認してください。</span><span class="sxs-lookup"><span data-stu-id="648e6-150">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="648e6-151">フィードバックがありますか?</span><span class="sxs-lookup"><span data-stu-id="648e6-151">Have Feedback?</span></span>

<span data-ttu-id="648e6-152">OpenXR は依然として試験的であるため、お客様からのフィードバックをお寄せください。</span><span class="sxs-lookup"><span data-stu-id="648e6-152">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="648e6-153">[](https://aka.ms/unityforums) **Microsoft**  +  **OpenXR** と **HoloLens 2** または **Windows Mixed Reality** でフォーラム投稿にタグを付けて、Unity フォーラムをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="648e6-153">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="648e6-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="648e6-154">See also</span></span>

* [<span data-ttu-id="648e6-155">MRTK を使用しないプロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="648e6-155">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="648e6-156">Unity で推奨される設定</span><span class="sxs-lookup"><span data-stu-id="648e6-156">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="648e6-157">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="648e6-157">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
