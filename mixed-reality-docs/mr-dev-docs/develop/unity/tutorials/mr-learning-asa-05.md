---
title: Azure Spatial Anchors チュートリアル - 5. Android と iOS 用の Azure Spatial Anchors
description: このコースを完了すると、Mixed Reality Toolkit (MRTK) と Azure Spatial Anchors を使用して Android および iOS に Unity プロジェクトをデプロイする方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, Android, iOS, MRTK, Mixed Reality Toolkit, UWP, Azure 空間アンカー, AR Foundation, ARCore, ARKit
ms.localizationpriority: high
ms.openlocfilehash: bee84db206dbb4e95272799c16d6dbd4e394e807
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679431"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="f6cb2-105">5.Android と iOS 用の Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="f6cb2-105">5. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="f6cb2-106">このチュートリアルでは、AR Foundation、ARCore XR Plugin、ARKit XR Plugin を使用して、Android デバイスや iOS デバイス用にプロジェクトをビルドする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-106">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="f6cb2-107">目標</span><span class="sxs-lookup"><span data-stu-id="f6cb2-107">Objectives</span></span>

* <span data-ttu-id="f6cb2-108">Unity の AR Foundation と ARCore XR Plugin を使用して、ご利用の Android デバイス用にプロジェクトをビルドする方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-108">Learn how to build your project to your Android device using Unity's AR Foundation and ARCore XR Plugin</span></span>
* <span data-ttu-id="f6cb2-109">Unity の AR Foundation と ARKit XR Plugin を使用して、ご利用の iOS デバイス用にプロジェクトをビルドする方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-109">Learn how to build your project to your iOS device using Unity's AR Foundation and ARKit XR Plugin</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="f6cb2-110">組み込みの Unity パッケージのインストール</span><span class="sxs-lookup"><span data-stu-id="f6cb2-110">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="f6cb2-111">このセクションでは、次の組み込みパッケージをアップグレードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-111">In this section, you will upgrade and install the following inbuilt packages:</span></span>

* <span data-ttu-id="f6cb2-112">AR Foundation 3.1.3</span><span class="sxs-lookup"><span data-stu-id="f6cb2-112">AR Foundation 3.1.3</span></span>
* <span data-ttu-id="f6cb2-113">XR Legacy Input Helpers 2.1.4</span><span class="sxs-lookup"><span data-stu-id="f6cb2-113">XR Legacy Input Helpers 2.1.4</span></span>
* <span data-ttu-id="f6cb2-114">ARCore XR Plugin 3.1.3 for Android のサポート</span><span class="sxs-lookup"><span data-stu-id="f6cb2-114">ARCore XR Plugin 3.1.3 for Android support</span></span>
* <span data-ttu-id="f6cb2-115">ARKit XR Plugin 3.1.3 for iOS のサポート</span><span class="sxs-lookup"><span data-stu-id="f6cb2-115">ARKit XR plugin 3.1.3 for iOS support</span></span>

> [!CAUTION]
> <span data-ttu-id="f6cb2-116">すべてのバージョンが MRTK と互換性があるわけではなく、特定のバージョンのみが連携して機能するため、必ず上記のバージョンをインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-116">Not all version are compatible with MRTK and only certain version works together, so make sure you install the exact versions listed above.</span></span>

<span data-ttu-id="f6cb2-117">Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[Package Manager]\(パッケージ マネージャー\)** の順に選択して、[Package Manager]\(パッケージ マネージャー\) ウィンドウを開きます。次に、 **[AR Foundation]**  >  **[3.1.3]** の順に選択し、 **[3.1.3 に更新します]** ボタンをクリックしてパッケージを更新します。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-117">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** > **3.1.3** and click the **Update to 3.1.3** button to update the package:</span></span>

![AR Foundation が選択されている [Package Manager]\(パッケージ マネージャー\) が表示された Unity](images/mr-learning-asa/asa-05-section1-step1-1.png)

<span data-ttu-id="f6cb2-119">必要に応じて、同じプロセスに従って残りのパッケージをインポートします。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-119">Follow the same process to import the remaining packages as needed.</span></span>

> [!NOTE]
> <span data-ttu-id="f6cb2-120">Android 用にこのプロジェクトを開発している場合は、ARKit XR Plugin パッケージをインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-120">If you are developing this project for Android, there is no need to install the ARKit XR Plugin package.</span></span> <span data-ttu-id="f6cb2-121">同様に、iOS 用にこのプロジェクトを開発している場合は、ARCore XR Plugin をインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-121">Similarly, if you are developing this project for iOS, you do not need to install the ARCore XR Plugin.</span></span>

## <a name="configure-mrtk-for-ar-foundation-camera"></a><span data-ttu-id="f6cb2-122">AR Foundation Camera 用に MRTK を構成する</span><span class="sxs-lookup"><span data-stu-id="f6cb2-122">Configure MRTK for AR Foundation Camera</span></span>

<span data-ttu-id="f6cb2-123">このセクションでは、モバイル デバイスに展開するために MRTK を構成する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-123">In this section, you will learn how to configure MRTK for deploying to a mobile device.</span></span>

<span data-ttu-id="f6cb2-124">[Hierarchy]\(階層\) ウィンドウで、 **[MixedRealityToolkit]** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-124">In the Hierarchy window, select the **MixedRealityToolkit** object.</span></span> <span data-ttu-id="f6cb2-125">次に、[Inspector]\(インスペクター\) ウィンドウで、 **[Camera]\(カメラ\)** タブを選択し、カメラ プロファイルを複製して、それに適切な名前 (たとえば **AzureSpatialAnchors_ARCameraProfile**) を付けます。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-125">Then in the Inspector window, select the **Camera** tab, clone the camera profile, and give it a suitable name, for example, **AzureSpatialAnchors_ARCameraProfile**:</span></span>

![新しく作成された ARCameraProfile が選択されている Unity](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="f6cb2-127">MRTK プロファイルを複製する方法については、[Mixed Reality ツールキット プロファイルの構成](mr-learning-base-03.md)に関するページにある手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-127">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the Mixed Reality Toolkit profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="f6cb2-128">[Inspector]\(インスペクター\) ウィンドウで **[Camera]\(カメラ\)** タブを選択したままにして、 **[Camera Setting Providers]\(カメラ設定プロバイダー\)** を展開し、 **[+ Add Camera Setting Provider]\(+ カメラ設定プロバイダーの追加\)** ボタンをクリックします。次に、新しく追加した **[New data provider 1]\(新しいデータ プロバイダー 1\)** を展開します。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-128">With the **Camera** tab still selected in the Inspector window, expand the **Camera Setting Providers** and click the **+ Add Camera Setting Provider** button, then expand the newly added **New data provider 1**:</span></span>

![新しいデータ プロバイダーが追加された ARCameraProfile が表示された Unity](images/mr-learning-asa/asa-05-section2-step1-2.png)

<span data-ttu-id="f6cb2-130">**[Type]\(種類\)** ドロップダウンを使用して、種類を **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings** に変更します。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-130">Using the **Type** dropdown, change the type to **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span></span>

![データ プロバイダーの種類を選択するためのパスを含む ARCameraProfile が表示された Unity](images/mr-learning-asa/asa-05-section2-step1-3.png)

<span data-ttu-id="f6cb2-132">[Hierarchy]\(階層\) ウィンドウで **[MixedRealityToolkit]** オブジェクトを選択したままにして、[Inspector]\(インスペクター\) ウィンドウの **[Add Component]\(コンポーネントの追加\)** ボタンを使用して、次のコンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-132">With the **MixedRealityToolkit** object still selected in the Hierarchy window, use the **Add Component** button in the Inspector window to add the following components:</span></span>

* <span data-ttu-id="f6cb2-133">AR Anchor Manager (スクリプト)</span><span class="sxs-lookup"><span data-stu-id="f6cb2-133">AR Anchor Manager (Script)</span></span>
* <span data-ttu-id="f6cb2-134">DisableDiagnosticsSystem (スクリプト)</span><span class="sxs-lookup"><span data-stu-id="f6cb2-134">DisableDiagnosticsSystem (Script)</span></span>

![<span data-ttu-id="f6cb2-135">AR Anchor Manager と DisableDiagnosticsSystem コンポーネントが追加された MixedRealityToolkit オブジェクトが表示された Unity</span><span class="sxs-lookup"><span data-stu-id="f6cb2-135">Unity MixedRealityToolkit object with AR Anchor Manager and DisableDiagnosticsSystem components added</span></span> ](images/mr-learning-asa/asa-05-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="f6cb2-136">AR Reference Point Manager (スクリプト) コンポーネントを追加すると、AR Session Origin (スクリプト) コンポーネントも自動的に追加されます。AR Reference Point Manager (スクリプト) コンポーネントで必要になるためです。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-136">When you add the AR Reference Point Manager (Script) component, the AR Session Origin (Script) component is automatically added because it is required by the AR Reference Point Manager (Script) component.</span></span>

## <a name="building-your-application-to-your-android-device"></a><span data-ttu-id="f6cb2-137">ご利用の Android デバイス用のアプリケーションのビルド</span><span class="sxs-lookup"><span data-stu-id="f6cb2-137">Building your application to your Android device</span></span>

<span data-ttu-id="f6cb2-138">このセクションでは、プロジェクトを Android デバイス用にビルドして配置するように構成する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-138">In this section, you will learn how to configure your project to build and deploy it to an Android device.</span></span>

<span data-ttu-id="f6cb2-139">Unity メニューで、 **[File]\(ファイル\)**  >  **[Build Settings...]\(ビルド設定...\)** の順に選択し、[Build Settings]\(ビルド設定\) ウィンドウを開いて、プラットフォームを Android に変更します。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-139">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and then switch the platform to Android:</span></span>

![Android プラットフォームが選択されている [Build Settings]\(ビルド設定\) ウィンドウが表示された Unity](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="f6cb2-141">ビルド プラットフォームを切り替える方法については、「[ビルド プラットフォームの切り替え](mr-learning-base-02.md#switching-the-build-platform)」にある手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-141">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="f6cb2-142">[ビルド設定] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-142">Close the Build Settings window.</span></span>

<span data-ttu-id="f6cb2-143">Unity メニューで、 **[Mixed Reality ツールキット]**  >  **[Utilities]\(ユーティリティ\)**  >  **[Configure Unity Project]\(Unity プロジェクトの構成\)** の順に選択して、 **[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\)** ウィンドウを開きます。すべてのオプションを確実に選択してから、 **[Apply]\(適用\)** ボタンをクリックして設定を適用します。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-143">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![Android の [MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウが表示された Unity](images/mr-learning-asa/asa-05-section3-step1-2.png)

<span data-ttu-id="f6cb2-145">Unity メニューで **[Edit]\(編集\)**  >  **[Project Settings...]\(プロジェクトの設定...\)** の順に選択して、[Player Settings]\(プレーヤーの設定\) ウィンドウを開きます。次に、 **[Player]\(プレーヤー\)**  >   **[他の設定]** セクションを見つけます。 **[Vulkan]** を選択してから、 **"-"** シンボルをクリックしてそれを削除します。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-145">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, select **Vulkan** and remove it by clicking the **"-"** symbol:</span></span>

![[Vulcan] が選択されている [他の設定] が表示された Unity](images/mr-learning-asa/asa-05-section3-step1-3.png)

<span data-ttu-id="f6cb2-147">[Player Settings]\(プレーヤーの設定\) ウィンドウを閉じ、もう一度 [ビルド設定] ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-147">Close the Player Settings window and open the Build Settings window again.</span></span>

<span data-ttu-id="f6cb2-148">[ビルドの設定] ウィンドウで、 **[Add Open Scenes]\(オープン シーンの追加\)** ボタンをクリックして、 **[Scenes in Build]\(ビルド内のシーン\)** リストに現在のシーンを追加します。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-148">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span> <span data-ttu-id="f6cb2-149">次に、USB ケーブルを使用して、使用する Android デバイスを自分のコンピューターに接続し、 **[Run Device]\(デバイスの実行\)** ドロップダウンからそれを選択します。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-149">Then, use a USB cable, connect your Android device to your computer and select it from the **Run Device** dropdown:</span></span>

![シーンが追加され、[Run Device]\(デバイスの実行\) が選択されている [Build Settings]\(ビルド設定\) ウィンドウが表示された Unity](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> <span data-ttu-id="f6cb2-151">そのデバイスが [Run Device]\(デバイスの実行\) ドロップダウンに表示されない場合は、ドロップダウンの横にある [更新] ボタンを押してみてください。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-151">If your device does not appear in the Run Device dropdown, you might need to press the Refresh button next to the dropdown.</span></span>

<span data-ttu-id="f6cb2-152">[ビルド設定] ウィンドウで、 **[ビルドして実行]** ボタンをクリックして、[Android のビルド] ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-152">In the Build Settings window, click the **Build And Run** button to open the Build Android window.</span></span>

<span data-ttu-id="f6cb2-153">ビルドを格納するのに適切な場所 (たとえば _D:\MixedRealityLearning\Builds_) を選択してから、apk に適切な名前 (_たとえば、MRTKTutorials-AzureSpatialAnchors_) を指定し、 **[保存]** ボタンをクリックしてビルド プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-153">Choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, then give the apk a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and click the **Save** button to start the build process:</span></span>

![[保存] プロンプト ウィンドウが表示されている Android の [Build Settings]\(ビルド設定\) ウィンドウが表示された Unity](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
<span data-ttu-id="f6cb2-155">Unity コンソール ウィンドウに、Android SDK、NDK、または JDK モジュールに関連するエラーが表示される場合は、Unity ハブを開き、その関連する Android ビルド サポート モジュールをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-155">If you get any error in the Unity Console window related to Android SDK, NDK, or JDK modules, you need to open Unity Hub and install the associated Android Build Support modules.</span></span>

<span data-ttu-id="f6cb2-156">ビルド プロセスが完了すると、アプリがご利用の Android デバイスに自動的に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-156">When the build process is complete, your apps should automatically load on your Android device.</span></span>

## <a name="building-your-application-to-your-ios-device"></a><span data-ttu-id="f6cb2-157">ご利用の iOS デバイス用のアプリケーションのビルド</span><span class="sxs-lookup"><span data-stu-id="f6cb2-157">Building your application to your iOS device</span></span>

<span data-ttu-id="f6cb2-158">このセクションでは、プロジェクトを iOS デバイス用にビルドして配置するように構成する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-158">In this section, you will learn how to configure your project, to build and deploy it to your iOS device.</span></span>

<span data-ttu-id="f6cb2-159">Unity メニューで、 **[File]\(ファイル\)**  >  **[Build Settings...]\(ビルド設定...\)** の順に選択し、[Build Settings]\(ビルド設定\) ウィンドウを開き、プラットフォームを iOS に変更します。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-159">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and switch platform to iOS:</span></span>

![iOS が選択されている [Build Settings]\(ビルド設定\) ウィンドウが表示された Unity](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="f6cb2-161">ビルド プラットフォームを切り替える方法については、「[ビルド プラットフォームの切り替え](mr-learning-base-02.md#switching-the-build-platform)」にある手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-161">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="f6cb2-162">[ビルド設定] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-162">Close the Build Settings window.</span></span>

<span data-ttu-id="f6cb2-163">Unity メニューで、 **[Mixed Reality ツールキット]**  >  **[Utilities]\(ユーティリティ\)**  >  **[Configure Unity Project]\(Unity プロジェクトの構成\)** の順に選択して、 **[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\)** ウィンドウを開きます。すべてのオプションを確実に選択してから、 **[Apply]\(適用\)** ボタンをクリックして設定を適用します。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-163">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![iOS の [MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウが表示された Unity](images/mr-learning-asa/asa-05-section4-step1-2.png)

<span data-ttu-id="f6cb2-165">Unity メニューで **[Edit]\(編集\)**  >  **[Project Settings...]\(プロジェクトの設定...\)** の順に選択して、[Player Settings]\(プレーヤーの設定\) ウィンドウを開きます。次に、 **[Player]\(プレーヤー\)**  >   **[他の設定]** セクションを見つけます。 **[Strip Engine Code]\(ストリップ エンジン コード\)** チェックボックスをオフにして、それを無効にします。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-165">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, uncheck the **Strip Engine Code** checkbox to disable it:</span></span>

![[Strip Engine Code]\(ストリップ エンジン コード\) が無効にされている [他の設定] が表示された Unity](images/mr-learning-asa/asa-05-section4-step1-3.png)

<span data-ttu-id="f6cb2-167">[Player Settings]\(プレーヤーの設定\) ウィンドウを閉じ、もう一度 **[ビルド設定]** ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-167">Close the Player Settings window and open the **Build Settings** window again.</span></span>

<span data-ttu-id="f6cb2-168">[ビルドの設定] ウィンドウで、 **[Add Open Scenes]\(オープン シーンの追加\)** ボタンをクリックして、 **[Scenes in Build]\(ビルド内のシーン\)** リストに現在のシーンを追加します。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-168">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list:</span></span>

![シーンが追加されている [Build Settings]\(ビルド設定\) ウィンドウが表示された Unity](images/mr-learning-asa/asa-05-section4-step1-4.png)

<span data-ttu-id="f6cb2-170">[ビルド設定] ウィンドウで、 **[ビルド]** ボタンをクリックして、[iOS のビルド] ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-170">In the Build Settings window, click the **Build** button to open the Build iOS window.</span></span>

<span data-ttu-id="f6cb2-171">Xcode プロジェクトを格納するのに適切な場所 (たとえば _D:\MixedRealityLearning\Builds_) を選択し、新しいフォルダーを作成してそれに適切な名前 (たとえば _MRTKTutorials-AzureSpatialAnchors_) を指定してから、 **[Select Folder]\(フォルダーの選択\)** ボタンをクリックしてビルド処理を開始します。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-171">Choose a suitable location to store your Xcode project, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and then click the **Select Folder** button to start the build process:</span></span>

![[保存] プロンプト ウィンドウが表示されている iOS の [Build Settings]\(ビルド設定\) ウィンドウが表示された Unity](images/mr-learning-asa/asa-05-section4-step1-5.png)

<span data-ttu-id="f6cb2-173">ビルド プロセスが完了したら、「[Xcode プロジェクトをエクスポートする](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project)」にある手順に従って、Xcode プロジェクトを iOS デバイスにデプロイする方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-173">When the build process is complete, follow the [Export the Xcode project](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) instructions to learn to deploy your Xcode project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="f6cb2-174">結論</span><span class="sxs-lookup"><span data-stu-id="f6cb2-174">Congratulations</span></span>

<span data-ttu-id="f6cb2-175">このチュートリアルでは、AR Foundation、ARCore XR Plugin、ARKit XR Plugin を使用して、Android デバイスや iOS デバイス用にプロジェクトをビルドする方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="f6cb2-175">In this tutorial, you learned how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>
