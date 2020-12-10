---
title: Unity Visual Studio ソリューションのエクスポートとビルド
description: この記事では、Visual Studio でビルドおよびデプロイできるように、Unity からの mixed reality プロジェクトをエクスポートする方法について説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: unity, visual studio, エクスポート, ビルド, デプロイ, HoloLens, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実ヘッドセット, UWP, 展開
ms.openlocfilehash: 4da20a30375c7204c532a19c129c9265c0fa27d9
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010413"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a><span data-ttu-id="0a723-104">Unity Visual Studio ソリューションのエクスポートとビルド</span><span class="sxs-lookup"><span data-stu-id="0a723-104">Exporting and building a Unity Visual Studio solution</span></span>

<span data-ttu-id="0a723-105">アプリがシステムキーボードを必要としない場合は、アプリケーションがわずかにメモリを使い、起動時間を短縮できるように、 *D3D* を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0a723-105">If your app doesn't need the system keyboard, our recommendation is to use *D3D* so that your app uses slightly less memory and a faster launch time.</span></span> <span data-ttu-id="0a723-106">ただし、TouchScreenKeyboard API を使用してシステムキーボードを使用している場合は、プロジェクトを *XAML* としてエクスポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a723-106">However, if you're using the system keyboard through the TouchScreenKeyboard API, you need to export the project as *XAML*.</span></span>

## <a name="how-to-export-from-unity"></a><span data-ttu-id="0a723-107">Unity からエクスポートする方法</span><span class="sxs-lookup"><span data-stu-id="0a723-107">How to export from Unity</span></span>

<span data-ttu-id="0a723-108">![Unity のビルド設定](images/unitybuildsettings-300px.png)</span><span class="sxs-lookup"><span data-stu-id="0a723-108">![Unity build settings](images/unitybuildsettings-300px.png)</span></span><br>
<span data-ttu-id="0a723-109">*Unity エディターでのビルド設定*</span><span class="sxs-lookup"><span data-stu-id="0a723-109">*Build settings in Unity editor*</span></span>

1. <span data-ttu-id="0a723-110">Unity からプロジェクトをエクスポートする準備ができたら、[**ファイル**] メニューを開き、[**ビルドの設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a723-110">When you're ready to export your project from Unity, open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="0a723-111">シーンをビルドに追加するには、[開いている **シーンを追加** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a723-111">Select **Add Open Scenes** to add your scene to the build.</span></span>
3. <span data-ttu-id="0a723-112">[ **ビルドの設定** ] ダイアログで、HoloLens をエクスポートする次のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="0a723-112">In the **Build Settings** dialog, choose the following options to export for HoloLens:</span></span>
   * <span data-ttu-id="0a723-113">**Platform:** *ユニバーサル Windows プラットフォーム* 、選択した内容を有効にするには、[ **プラットフォームの切り替え** ] を選択してください。</span><span class="sxs-lookup"><span data-stu-id="0a723-113">**Platform:** *Universal Windows Platform* and be sure to select **Switch Platform** for your selection to take effect.</span></span>
   * <span data-ttu-id="0a723-114">**SDK:** *Universal 10*。</span><span class="sxs-lookup"><span data-stu-id="0a723-114">**SDK:** *Universal 10*.</span></span>
   * <span data-ttu-id="0a723-115">**UWP ビルドの種類:** *D3D*。</span><span class="sxs-lookup"><span data-stu-id="0a723-115">**UWP Build Type:** *D3D*.</span></span>
4. <span data-ttu-id="0a723-116">**省略可能**: **Unity C# プロジェクト:** 確認済み。</span><span class="sxs-lookup"><span data-stu-id="0a723-116">**Optional**: **Unity C# Projects:** Checked.</span></span>

>[!NOTE]
><span data-ttu-id="0a723-117">このチェックボックスをオンにすると、次のことができます。</span><span class="sxs-lookup"><span data-stu-id="0a723-117">Checking this box allows you to:</span></span>
>* <span data-ttu-id="0a723-118">Visual Studio リモートデバッガーでアプリをデバッグします。</span><span class="sxs-lookup"><span data-stu-id="0a723-118">Debug your app in the Visual Studio remote debugger.</span></span>
>* <span data-ttu-id="0a723-119">WinRT Api に IntelliSense を使用しながら、Unity C# プロジェクトのスクリプトを編集します。</span><span class="sxs-lookup"><span data-stu-id="0a723-119">Edit scripts in the Unity C# project while using IntelliSense for WinRT APIs.</span></span>

5. <span data-ttu-id="0a723-120">[**ビルドの設定...** ] ウィンドウで、[プレーヤーの **設定**] を開きます。</span><span class="sxs-lookup"><span data-stu-id="0a723-120">From the **Build Settings...** window, open **Player Settings...**</span></span>
6. <span data-ttu-id="0a723-121">[ユニバーサル Windows プラットフォーム] タブ **の設定** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a723-121">Select the **Settings for Universal Windows Platform** tab.</span></span>
7. <span data-ttu-id="0a723-122">**[XR Settings]\(XR 設定\)** グループを展開します。</span><span class="sxs-lookup"><span data-stu-id="0a723-122">Expand the **XR Settings** group.</span></span>
8. <span data-ttu-id="0a723-123">[ **XR の設定** ] セクションで、[ **サポートさ** れている仮想 reality] チェックボックスをオンにして、新しい **仮想デバイス** の一覧を追加し、 **"Windows Mixed reality"** がサポートされているデバイスとして表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0a723-123">In the **XR Settings** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list and confirm **"Windows Mixed Reality"** is listed as a supported device.</span></span>
9. <span data-ttu-id="0a723-124">[ビルドの **設定** ] ダイアログに戻ります。</span><span class="sxs-lookup"><span data-stu-id="0a723-124">Return to the **Build Settings** dialog.</span></span>
10. <span data-ttu-id="0a723-125">**[Build]\(ビルド\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a723-125">Select **Build**.</span></span>
11. <span data-ttu-id="0a723-126">表示された [エクスプローラー] ダイアログボックスで、Unity のビルド出力を保持する新しいフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="0a723-126">In the Windows Explorer dialog that appears, create a new folder to hold Unity's build output.</span></span> <span data-ttu-id="0a723-127">一般に、"App" というフォルダーに名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="0a723-127">Generally, we name the folder "App".</span></span>
12. <span data-ttu-id="0a723-128">新しく作成したフォルダーを選択し、[ **フォルダーの選択**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a723-128">Select the newly created folder and select **Select Folder**.</span></span>
13. <span data-ttu-id="0a723-129">Unity のビルドが完了すると、Windows エクスプローラーウィンドウが開き、プロジェクトのルートディレクトリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a723-129">Once Unity has finished building, a Windows Explorer window will open to the project root directory.</span></span> <span data-ttu-id="0a723-130">新しく作成したフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="0a723-130">Navigate into the newly created folder.</span></span>
14. <span data-ttu-id="0a723-131">このフォルダー内にある生成された Visual Studio ソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="0a723-131">Open the generated Visual Studio solution file located inside this folder.</span></span>

## <a name="when-to-re-export-from-unity"></a><span data-ttu-id="0a723-132">Unity から再エクスポートする場合</span><span class="sxs-lookup"><span data-stu-id="0a723-132">When to re-export from Unity</span></span>

<span data-ttu-id="0a723-133">Unity からアプリをエクスポートするときに **C# プロジェクト** のチェックボックスをオンにすると、すべての unity スクリプトファイルを含む Visual Studio ソリューションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0a723-133">Checking the **C# Projects** checkbox when exporting your app from Unity creates a Visual Studio solution that includes all your Unity script files.</span></span> <span data-ttu-id="0a723-134">すべてのスクリプトを1つの場所に配置することで、Unity から再エクスポートせずに反復処理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="0a723-134">Having all your scripts in one place lets you iterate without re-exporting from Unity.</span></span> <span data-ttu-id="0a723-135">ただし、スクリプトの内容を変更するだけではないプロジェクトに変更を加える場合は、Unity から再エクスポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a723-135">However, if you make changes to your project that aren't just changing the contents of scripts, you'll need to re-export from Unity.</span></span> <span data-ttu-id="0a723-136">Unity から再エクスポートする必要のある時間の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0a723-136">Some examples of times you need to re-export from Unity are:</span></span>
* <span data-ttu-id="0a723-137">[プロジェクト] タブでアセットを追加または削除します。</span><span class="sxs-lookup"><span data-stu-id="0a723-137">You add or remove assets in the Project tab.</span></span>
* <span data-ttu-id="0a723-138">すべての値は、[インスペクター] タブで変更します。</span><span class="sxs-lookup"><span data-stu-id="0a723-138">You change any value in the Inspector tab.</span></span>
* <span data-ttu-id="0a723-139">[階層] タブでオブジェクトを追加または削除します。</span><span class="sxs-lookup"><span data-stu-id="0a723-139">You add or remove objects from the Hierarchy tab.</span></span>
* <span data-ttu-id="0a723-140">Unity プロジェクトの設定を変更します</span><span class="sxs-lookup"><span data-stu-id="0a723-140">You change any Unity project settings</span></span>

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a><span data-ttu-id="0a723-141">Unity Visual Studio ソリューションのビルドと配置</span><span class="sxs-lookup"><span data-stu-id="0a723-141">Building and deploying a Unity Visual Studio solution</span></span>

<span data-ttu-id="0a723-142">アプリのビルドと配置の残りの部分は、 [Visual Studio](../platform-capabilities-and-apis/using-visual-studio.md)で行われます。</span><span class="sxs-lookup"><span data-stu-id="0a723-142">The remainder of building and deploying apps happens in [Visual Studio](../platform-capabilities-and-apis/using-visual-studio.md).</span></span> <span data-ttu-id="0a723-143">Unity ビルド構成を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a723-143">You will need to specify a Unity build configuration.</span></span> <span data-ttu-id="0a723-144">Unity の名前付け規則は、Visual Studio で使用しているものとは異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0a723-144">Unity's naming conventions may differ from what you're used to in Visual Studio:</span></span>

|  <span data-ttu-id="0a723-145">構成</span><span class="sxs-lookup"><span data-stu-id="0a723-145">Configuration</span></span>  |  <span data-ttu-id="0a723-146">説明</span><span class="sxs-lookup"><span data-stu-id="0a723-146">Explanation</span></span> | 
|----------|----------|
|  <span data-ttu-id="0a723-147">デバッグ</span><span class="sxs-lookup"><span data-stu-id="0a723-147">Debug</span></span>  |  <span data-ttu-id="0a723-148">すべての最適化とプロファイラーが有効になります。</span><span class="sxs-lookup"><span data-stu-id="0a723-148">All optimizations off and the profiler is enabled.</span></span> <span data-ttu-id="0a723-149">スクリプトのデバッグに使用します。</span><span class="sxs-lookup"><span data-stu-id="0a723-149">Used to debug scripts.</span></span> | 
|  <span data-ttu-id="0a723-150">Master</span><span class="sxs-lookup"><span data-stu-id="0a723-150">Master</span></span>  |  <span data-ttu-id="0a723-151">すべての最適化が有効になり、プロファイラーは無効になります。</span><span class="sxs-lookup"><span data-stu-id="0a723-151">All optimizations are turned on and the profiler is disabled.</span></span> <span data-ttu-id="0a723-152">ストアにアプリを送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0a723-152">Used to submit apps to the Store.</span></span> | 
|  <span data-ttu-id="0a723-153">Release</span><span class="sxs-lookup"><span data-stu-id="0a723-153">Release</span></span>  |  <span data-ttu-id="0a723-154">すべての最適化が有効になり、プロファイラーが有効になります。</span><span class="sxs-lookup"><span data-stu-id="0a723-154">All optimizations are turned on and the profiler is enabled.</span></span> <span data-ttu-id="0a723-155">アプリのパフォーマンスを評価するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0a723-155">Used to evaluate app performance.</span></span> | 

<span data-ttu-id="0a723-156">上記の一覧は、Visual Studio プロジェクトを生成する必要がある一般的なトリガーのサブセットです。</span><span class="sxs-lookup"><span data-stu-id="0a723-156">Note, the above list is a subset of the common triggers that will cause the Visual Studio project to need to be generated.</span></span> <span data-ttu-id="0a723-157">一般に、Visual Studio 内から .cs ファイルを編集するには、Unity 内からプロジェクトを再生成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0a723-157">In general, editing .cs files from within Visual Studio won't require the project to be regenerated from within Unity.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="0a723-158">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="0a723-158">Troubleshooting</span></span>

<span data-ttu-id="0a723-159">.Cs ファイルの編集が Visual Studio プロジェクトで認識されない場合は、Unity の [ビルド] メニューから VS プロジェクトを生成するときに **Unity C# プロジェクト** がチェックされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0a723-159">If you find that edits to your .cs files aren't being recognized in your Visual Studio project, ensure that **Unity C# Projects** is checked when you generate the VS project from Unity's Build menu.</span></span>
