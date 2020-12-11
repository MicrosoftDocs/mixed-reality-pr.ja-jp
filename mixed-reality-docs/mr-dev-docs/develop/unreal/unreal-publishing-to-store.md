---
title: Microsoft Store への発行
description: ''
author: hferrone
ms.author: jacksonf
ms.date: 12/3/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, ドキュメント, ガイド, 機能, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, 発行, 配布, Microsoft Store
ms.openlocfilehash: 37a17ba4a691ca8db6ce447abd485293454b8ae3
ms.sourcegitcommit: 9c640c96e2270ef69edd46f1b12acb00b373554d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96583949"
---
# <a name="publishing-to-the-microsoft-store"></a><span data-ttu-id="216e7-103">Microsoft Store への発行</span><span class="sxs-lookup"><span data-stu-id="216e7-103">Publishing to the Microsoft Store</span></span>

<span data-ttu-id="216e7-104">Unreal アプリを世界に提供する準備ができたら、Microsoft Store に送信する前に更新する必要があるプロジェクト設定がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="216e7-104">When you're ready to get your Unreal app out to the world, there are a few project settings that need updating before you submit to the Microsoft Store.</span></span> <span data-ttu-id="216e7-105">これらの設定にはすべて既定値がありますが、アプリケーションが最適に提供されるよう運用環境向けに変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="216e7-105">All of these settings have default values, but should be changed for production to best represent the application.</span></span>

## <a name="project-settings-for-the-store-packaging"></a><span data-ttu-id="216e7-106">ストア パッケージ用のプロジェクト設定</span><span class="sxs-lookup"><span data-stu-id="216e7-106">Project settings for the store packaging</span></span>

1. <span data-ttu-id="216e7-107">最初に、 **[Project Settings]\(プロジェクトの設定\) > [Description]\(説明\)** 選択して、ゲームと発行元の情報を更新します。</span><span class="sxs-lookup"><span data-stu-id="216e7-107">First, select **Project Settings > Description** and update the game and publisher information:</span></span> 
    * <span data-ttu-id="216e7-108">**[Game Name]\(ゲーム名\)** は、HoloLens のアプリ タイルに表示されます</span><span class="sxs-lookup"><span data-stu-id="216e7-108">The **Game Name** will appear in the app tile on the HoloLens</span></span>
    * <span data-ttu-id="216e7-109">**[Company Distinguished Name]\(会社の識別名\)** はプロジェクト証明書の生成時に使用され、次の形式にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="216e7-109">The **Company Distinguished Name** is used when generating the project certificate and should be in the format:</span></span> 
        * <span data-ttu-id="216e7-110">**CN=<一般名>, O=<組織名>, L=<市区町村等の名前>, S=<都道府県等の名前>, C=<国名>** :</span><span class="sxs-lookup"><span data-stu-id="216e7-110">**CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**:</span></span>

![プロジェクトの設定で説明セクションが展開された Unreal エディターのスクリーンショット](images/unreal-publishing-img-01.png)

2. <span data-ttu-id="216e7-112">プロジェクトの設定の **[HoloLens]** セクションを展開し、パッケージ リソースを更新します。</span><span class="sxs-lookup"><span data-stu-id="216e7-112">Expand the **HoloLens** section of the project settings and update the packaging resources.</span></span>  <span data-ttu-id="216e7-113">これらのリソース名は、アプリケーションのストア ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="216e7-113">These resource names will be shown on the application’s store page:</span></span>

![プロジェクトの設定でパッケージ セクションが展開された Unreal エディターのスクリーンショット](images/unreal-publishing-img-02.png)

3. <span data-ttu-id="216e7-115">**[Images]\(画像\)** セクションを展開し、ストア アプリを表すテクスチャで既定のストア画像を更新します。</span><span class="sxs-lookup"><span data-stu-id="216e7-115">Expand the **Images** section and update the default store images with textures that represent the store app.</span></span>  <span data-ttu-id="216e7-116">必要に応じて、 **[3D Logo]\(3D ロゴ\)** チェック ボックスをオンにし、アプリケーション起動時に 3D ライブ キューブとして使用する glb ファイルをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="216e7-116">Optionally, select the **3D Logo** checkbox to upload a glb file to use as a 3D live cube when launching the application:</span></span>

![プロジェクトの設定で画像セクションが展開された Unreal エディターのスクリーンショット](images/unreal-publishing-img-03.png)

4. <span data-ttu-id="216e7-118">最後に、 **[Generate New]\(新規生成\)** を選択して、プロジェクト名と会社の識別名から署名証明書を生成します</span><span class="sxs-lookup"><span data-stu-id="216e7-118">Lastly, select **Generate New** to generate a signing certificate from the project name and company distinguished name</span></span>  
    * <span data-ttu-id="216e7-119">ストア画像の透明ピクセルの代わりに表示される **[Tile Background Color]\(タイルの背景色\)** を設定します。</span><span class="sxs-lookup"><span data-stu-id="216e7-119">Set a **Tile Background Color**, which will appear in place of any transparent pixels in the store images.</span></span>
    * <span data-ttu-id="216e7-120">リテールでロックされ、開発環境でロック解除されていないデバイスで実行するには、ドロップダウンを展開して **[Use Retail Windows Store Environment]\(リテール Windows ストア環境を使用する\)** を有効にします。</span><span class="sxs-lookup"><span data-stu-id="216e7-120">Expand the dropdown and enable **Use Retail Windows Store Environment** to run on retail-locked, not dev-unlocked, devices.</span></span>

![プロジェクトの設定で証明書生成セクションが展開された Unreal エディターのスクリーンショット](images/unreal-publishing-img-04.png)

## <a name="optional-app-installer"></a><span data-ttu-id="216e7-122">オプションのアプリ インストーラー</span><span class="sxs-lookup"><span data-stu-id="216e7-122">Optional App Installer</span></span>

<span data-ttu-id="216e7-123">アプリ インストーラー ファイルは、 **[Project Settings]\(プロジェクトの設定\) > [HoloLens]** から作成できます。これを使用して、ストアの外部にアプリケーションを配布できます。</span><span class="sxs-lookup"><span data-stu-id="216e7-123">An App Installer file can be created from **Project Settings > HoloLens**, which can be used to distribute the application outside of the store.</span></span>  <span data-ttu-id="216e7-124">**[Should Create App Installer]\(アプリ インストーラーを作成する\)** チェック ボックスをオンにし、ゲームの appxbundle を格納する URL またはネットワーク パスを設定します。</span><span class="sxs-lookup"><span data-stu-id="216e7-124">Enable the **Should Create App Installer** checkbox and set a URL or network path where you'd like the game’s appxbundle to be stored.</span></span>  

![プロジェクトの設定でアプリ インストーラー セクションが展開された Unreal エディターのスクリーンショット](images/unreal-publishing-img-05.png)

<span data-ttu-id="216e7-126">アプリをパッケージ化すると、appxbundle と appinstaller の両方が生成されます。</span><span class="sxs-lookup"><span data-stu-id="216e7-126">When the app is being packaged, both the appxbundle and appinstaller will be generated.</span></span>  <span data-ttu-id="216e7-127">appxbundle をインストール URL にアップロードした後、appinstaller を起動してネットワーク上の場所からアプリをインストールします。</span><span class="sxs-lookup"><span data-stu-id="216e7-127">Upload the appxbundle to the installation URL, then launch the appinstaller to install the app from the network location.</span></span>

## <a name="windows-app-certification-kit"></a><span data-ttu-id="216e7-128">Windows アプリ認定キット</span><span class="sxs-lookup"><span data-stu-id="216e7-128">Windows App Certification Kit</span></span>

<span data-ttu-id="216e7-129">Windows 10 SDK には、ストアへのパッケージのアップロードに影響する可能性がある一般的な問題を検証するための Windows アプリ認定キット (WACK) が付属しています。</span><span class="sxs-lookup"><span data-stu-id="216e7-129">The Windows 10 SDK ships with the Windows App Certification Kit (WACK) to validate common issues that could affect uploading a package to the store.</span></span>  <span data-ttu-id="216e7-130">WACK は、Windows キットのディレクトリ (通常は次のパスの下) にあります。</span><span class="sxs-lookup"><span data-stu-id="216e7-130">You can find the WACK in the Windows Kits directory, usually under the following path:</span></span> 

```
C:\Program Files (x86)\Windows Kits\10\App Certification Kit.
```

1. <span data-ttu-id="216e7-131">発行用に appx ファイルをパッケージ化した後、**appcertui.exe** を実行し、プロンプトに従って appx をスキャンします。</span><span class="sxs-lookup"><span data-stu-id="216e7-131">After your appx file is packaged for publication, run **appcertui.exe** and follow the prompts to scan the appx:</span></span>

![Windows アプリ認定キットで検証対象として選択されているアプリのスクリーンショット](images/unreal-publishing-img-06.png)

2. <span data-ttu-id="216e7-133">**[ストア アプリの検証]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="216e7-133">Select **Validate Store App**:</span></span>

![Windows アプリ認定キットでの検証の選択のスクリーンショット](images/unreal-publishing-img-07.png)

3. <span data-ttu-id="216e7-135">上部のセクションで appx を参照し、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="216e7-135">Browse for the appx in the top section and select **Next**:</span></span>

![Windows アプリ認定キットでのテストの選択のスクリーンショット](images/unreal-publishing-img-08.png)

4. <span data-ttu-id="216e7-137">**[次へ]** を選択し、テストを実行してレポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="216e7-137">Select **Next** to run the tests and create a report:</span></span>
    * <span data-ttu-id="216e7-138">ホスト PC で実行できるすべての使用可能なテストが、既定で有効になります</span><span class="sxs-lookup"><span data-stu-id="216e7-138">All available tests that can be run on the host PC will be enabled by default</span></span>

![Windows アプリ認定キットでのアプリ検証の進行状況のスクリーンショット](images/unreal-publishing-img-09.png)

5. <span data-ttu-id="216e7-140">テストが終了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="216e7-140">Wait for the tests to finish.</span></span> <span data-ttu-id="216e7-141">完了すると、最後のウィンドウに合格または不合格の結果が表示されます。これは、保存されたレポートで確認できます。</span><span class="sxs-lookup"><span data-stu-id="216e7-141">Once complete, the final window will show a pass or fail result, which can be viewed in the saved report.</span></span>

![Windows アプリ認定キットでの最終的なレポート結果のスクリーンショット](images/unreal-publishing-img-10.png)

## <a name="known-wack-failure-with-425"></a><span data-ttu-id="216e7-143">4\.25 での既知の WACK エラー</span><span class="sxs-lookup"><span data-stu-id="216e7-143">Known WACK failure with 4.25</span></span>

<span data-ttu-id="216e7-144">HoloLens 向けのパッケージ化の間に一部の x64 バイナリが組み込まれるため、Unreal 4.25 の Windows Mixed Reality プラグインでは WACK が失敗します。</span><span class="sxs-lookup"><span data-stu-id="216e7-144">The Windows Mixed Reality plugin in Unreal 4.25 will fail WACK because some x64 binaries are included while packaging for HoloLens.</span></span> <span data-ttu-id="216e7-145">エラーは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="216e7-145">The failure will look like this:</span></span>

![Windows アプリ認定キットでバイナリ アナライザーおよびサポートされている API のために失敗した結果のスクリーンショット](images/unreal-publishing-img-11.png)

<span data-ttu-id="216e7-147">問題を修正するには:</span><span class="sxs-lookup"><span data-stu-id="216e7-147">To fix the issue:</span></span>
1. <span data-ttu-id="216e7-148">Unreal プロジェクトを開いて Unreal のインストールまたはソース ディレクトリのルートを参照し、タスク バーの Unreal アイコンを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="216e7-148">Browse to the Unreal installation or source directory root by opening an Unreal project and right-click on the Unreal icon in the taskbar.</span></span>
2. <span data-ttu-id="216e7-149">UE4Editor を右クリックし、[properties]\(プロパティ\) を選択して、 **[Location]\(場所\)** エントリのパスを参照します。</span><span class="sxs-lookup"><span data-stu-id="216e7-149">Right-click on UE4Editor, select properties, and browse to the path in the **Location** entry:</span></span>

```
Open Engine\Plugins\Runtime\WindowsMixedReality\Source\WindowsMixedRealityHMD\WindowsMixedRealityHMD.Build.cs.
```

3. <span data-ttu-id="216e7-150">**WindowsMixedRealityHMD.Build.cs** で、**32 行目** を変更します。</span><span class="sxs-lookup"><span data-stu-id="216e7-150">In **WindowsMixedRealityHMD.Build.cs**, modify **line 32** from:</span></span>

```cpp
if(Target.Platform != UnrealTargetPlatform.Win32)
```

<span data-ttu-id="216e7-151">を次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="216e7-151">to:</span></span>

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64)

```

4. <span data-ttu-id="216e7-152">Unreal を閉じ、プロジェクトを再び開いて、HoloLens を再度パッケージ化します。</span><span class="sxs-lookup"><span data-stu-id="216e7-152">Close Unreal, reopen the project, and repackage for HoloLens.</span></span>  <span data-ttu-id="216e7-153">WACK を再実行すると、エラーが発生しなくなります。</span><span class="sxs-lookup"><span data-stu-id="216e7-153">Rerun WACK and the error will be gone.</span></span> 

## <a name="see-also"></a><span data-ttu-id="216e7-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="216e7-154">See also</span></span>
* [<span data-ttu-id="216e7-155">Microsoft Store へのアプリの送信</span><span class="sxs-lookup"><span data-stu-id="216e7-155">Submitting an app to the Microsoft Store</span></span>](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [<span data-ttu-id="216e7-156">Windows アプリ認定キット</span><span class="sxs-lookup"><span data-stu-id="216e7-156">Windows App Certification Kit</span></span>](https://developer.microsoft.com/windows/downloads/app-certification-kit)
* [<span data-ttu-id="216e7-157">アプリ インストーラー ファイルの手動作成</span><span class="sxs-lookup"><span data-stu-id="216e7-157">Create an App Installer file manually</span></span>](https://docs.microsoft.com/windows/msix/app-installer/how-to-create-appinstaller-file)