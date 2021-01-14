---
title: Microsoft Store への発行
description: Unreal Mixed Reality アプリケーションをパッケージ化して認定し、Microsoft Store に公開する方法について説明します。
author: hferrone
ms.author: jacksonf
ms.date: 12/3/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, ドキュメント, ガイド, 機能, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, 発行, 配布, Microsoft Store
ms.openlocfilehash: 41f081f11cdb9ac2fdf96a81bb761a1321d1776f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010022"
---
# <a name="publishing-to-the-microsoft-store"></a><span data-ttu-id="3e4f5-104">Microsoft Store への発行</span><span class="sxs-lookup"><span data-stu-id="3e4f5-104">Publishing to the Microsoft Store</span></span>

<span data-ttu-id="3e4f5-105">Unreal アプリを世界に提供する準備ができたら、Microsoft Store に送信する前に更新する必要があるプロジェクト設定がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-105">When you're ready to get your Unreal app out to the world, there are a few project settings that need updating before you submit to the Microsoft Store.</span></span> <span data-ttu-id="3e4f5-106">これらの設定にはすべて既定値がありますが、アプリケーションが最適に提供されるよう運用環境向けに変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-106">All of these settings have default values, but should be changed for production to best represent the application.</span></span>

## <a name="project-settings-for-the-store-packaging"></a><span data-ttu-id="3e4f5-107">ストア パッケージ用のプロジェクト設定</span><span class="sxs-lookup"><span data-stu-id="3e4f5-107">Project settings for the store packaging</span></span>

1. <span data-ttu-id="3e4f5-108">最初に、 **[Project Settings]\(プロジェクトの設定\) > [Description]\(説明\)** 選択して、ゲームと発行元の情報を更新します。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-108">First, select **Project Settings > Description** and update the game and publisher information:</span></span> 
    * <span data-ttu-id="3e4f5-109">**[Game Name]\(ゲーム名\)** は、HoloLens のアプリ タイルに表示されます</span><span class="sxs-lookup"><span data-stu-id="3e4f5-109">The **Game Name** will appear in the app tile on the HoloLens</span></span>
    * <span data-ttu-id="3e4f5-110">**[Company Distinguished Name]\(会社の識別名\)** はプロジェクト証明書の生成時に使用され、次の形式にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-110">The **Company Distinguished Name** is used when generating the project certificate and should be in the format:</span></span> 
        * <span data-ttu-id="3e4f5-111">**CN=<一般名>, O=<組織名>, L=<市区町村等の名前>, S=<都道府県等の名前>, C=<国名>** :</span><span class="sxs-lookup"><span data-stu-id="3e4f5-111">**CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**:</span></span>

![プロジェクトの設定で説明セクションが展開された Unreal エディターのスクリーンショット](images/unreal-publishing-img-01.png)

2. <span data-ttu-id="3e4f5-113">プロジェクトの設定の **[HoloLens]** セクションを展開し、パッケージ リソースを更新します。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-113">Expand the **HoloLens** section of the project settings and update the packaging resources.</span></span>  <span data-ttu-id="3e4f5-114">これらのリソース名は、アプリケーションのストア ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-114">These resource names will be shown on the application’s store page:</span></span>

![プロジェクトの設定でパッケージ セクションが展開された Unreal エディターのスクリーンショット](images/unreal-publishing-img-02.png)

3. <span data-ttu-id="3e4f5-116">**[Images]\(画像\)** セクションを展開し、ストア アプリを表すテクスチャで既定のストア画像を更新します。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-116">Expand the **Images** section and update the default store images with textures that represent the store app.</span></span>  <span data-ttu-id="3e4f5-117">必要に応じて、 **[3D Logo]\(3D ロゴ\)** チェック ボックスをオンにし、アプリケーション起動時に 3D ライブ キューブとして使用する glb ファイルをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-117">Optionally, select the **3D Logo** checkbox to upload a glb file to use as a 3D live cube when launching the application:</span></span>

![プロジェクトの設定で画像セクションが展開された Unreal エディターのスクリーンショット](images/unreal-publishing-img-03.png)

4. <span data-ttu-id="3e4f5-119">最後に、 **[Generate New]\(新規生成\)** を選択して、プロジェクト名と会社の識別名から署名証明書を生成します</span><span class="sxs-lookup"><span data-stu-id="3e4f5-119">Lastly, select **Generate New** to generate a signing certificate from the project name and company distinguished name</span></span>  
    * <span data-ttu-id="3e4f5-120">ストア画像の透明ピクセルの代わりに表示される **[Tile Background Color]\(タイルの背景色\)** を設定します。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-120">Set a **Tile Background Color**, which will appear in place of any transparent pixels in the store images.</span></span>
    * <span data-ttu-id="3e4f5-121">リテールでロックされ、開発環境でロック解除されていないデバイスで実行するには、ドロップダウンを展開して **[Use Retail Windows Store Environment]\(リテール Windows ストア環境を使用する\)** を有効にします。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-121">Expand the dropdown and enable **Use Retail Windows Store Environment** to run on retail-locked, not dev-unlocked, devices.</span></span>

![プロジェクトの設定で証明書生成セクションが展開された Unreal エディターのスクリーンショット](images/unreal-publishing-img-04.png)

## <a name="optional-app-installer"></a><span data-ttu-id="3e4f5-123">オプションのアプリ インストーラー</span><span class="sxs-lookup"><span data-stu-id="3e4f5-123">Optional App Installer</span></span>

<span data-ttu-id="3e4f5-124">アプリ インストーラー ファイルは、 **[Project Settings]\(プロジェクトの設定\) > [HoloLens]** から作成できます。これを使用して、ストアの外部にアプリケーションを配布できます。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-124">An App Installer file can be created from **Project Settings > HoloLens**, which can be used to distribute the application outside of the store.</span></span>  <span data-ttu-id="3e4f5-125">**[Should Create App Installer]\(アプリ インストーラーを作成する\)** チェック ボックスをオンにし、ゲームの appxbundle を格納する URL またはネットワーク パスを設定します。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-125">Enable the **Should Create App Installer** checkbox and set a URL or network path where you'd like the game’s appxbundle to be stored.</span></span>  

![プロジェクトの設定でアプリ インストーラー セクションが展開された Unreal エディターのスクリーンショット](images/unreal-publishing-img-05.png)

<span data-ttu-id="3e4f5-127">アプリをパッケージ化すると、appxbundle と appinstaller の両方が生成されます。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-127">When the app is being packaged, both the appxbundle and appinstaller will be generated.</span></span>  <span data-ttu-id="3e4f5-128">appxbundle をインストール URL にアップロードした後、appinstaller を起動してネットワーク上の場所からアプリをインストールします。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-128">Upload the appxbundle to the installation URL, then launch the appinstaller to install the app from the network location.</span></span>

## <a name="windows-app-certification-kit"></a><span data-ttu-id="3e4f5-129">Windows アプリ認定キット</span><span class="sxs-lookup"><span data-stu-id="3e4f5-129">Windows App Certification Kit</span></span>

<span data-ttu-id="3e4f5-130">Windows 10 SDK には、ストアへのパッケージのアップロードに影響する可能性がある一般的な問題を検証するための Windows アプリ認定キット (WACK) が付属しています。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-130">The Windows 10 SDK ships with the Windows App Certification Kit (WACK) to validate common issues that could affect uploading a package to the store.</span></span>  <span data-ttu-id="3e4f5-131">WACK は、Windows キットのディレクトリ (通常は次のパスの下) にあります。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-131">You can find the WACK in the Windows Kits directory, usually under the following path:</span></span> 

```
C:\Program Files (x86)\Windows Kits\10\App Certification Kit.
```

1. <span data-ttu-id="3e4f5-132">発行用に appx ファイルをパッケージ化した後、**appcertui.exe** を実行し、プロンプトに従って appx をスキャンします。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-132">After your appx file is packaged for publication, run **appcertui.exe** and follow the prompts to scan the appx:</span></span>

![Windows アプリ認定キットで検証対象として選択されているアプリのスクリーンショット](images/unreal-publishing-img-06.png)

2. <span data-ttu-id="3e4f5-134">**[ストア アプリの検証]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-134">Select **Validate Store App**:</span></span>

![Windows アプリ認定キットでの検証の選択のスクリーンショット](images/unreal-publishing-img-07.png)

3. <span data-ttu-id="3e4f5-136">上部のセクションで appx を参照し、 **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-136">Browse for the appx in the top section and select **Next**:</span></span>

![Windows アプリ認定キットでのテストの選択のスクリーンショット](images/unreal-publishing-img-08.png)

4. <span data-ttu-id="3e4f5-138">**[次へ]** を選択し、テストを実行してレポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-138">Select **Next** to run the tests and create a report:</span></span>
    * <span data-ttu-id="3e4f5-139">ホスト PC で実行できるすべての使用可能なテストが、既定で有効になります</span><span class="sxs-lookup"><span data-stu-id="3e4f5-139">All available tests that can be run on the host PC will be enabled by default</span></span>

![Windows アプリ認定キットでのアプリ検証の進行状況のスクリーンショット](images/unreal-publishing-img-09.png)

5. <span data-ttu-id="3e4f5-141">テストが終了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-141">Wait for the tests to finish.</span></span> <span data-ttu-id="3e4f5-142">完了すると、最後のウィンドウに合格または不合格の結果が表示されます。これは、保存されたレポートで確認できます。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-142">Once complete, the final window will show a pass or fail result, which can be viewed in the saved report.</span></span>

![Windows アプリ認定キットでの最終的なレポート結果のスクリーンショット](images/unreal-publishing-img-10.png)

## <a name="known-wack-failure-with-425"></a><span data-ttu-id="3e4f5-144">4\.25 での既知の WACK エラー</span><span class="sxs-lookup"><span data-stu-id="3e4f5-144">Known WACK failure with 4.25</span></span>

<span data-ttu-id="3e4f5-145">HoloLens 向けのパッケージ化の間に一部の x64 バイナリが組み込まれるため、Unreal 4.25 の Windows Mixed Reality プラグインでは WACK が失敗します。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-145">The Windows Mixed Reality plugin in Unreal 4.25 will fail WACK because some x64 binaries are included while packaging for HoloLens.</span></span> <span data-ttu-id="3e4f5-146">エラーは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-146">The failure will look like this:</span></span>

![Windows アプリ認定キットでバイナリ アナライザーおよびサポートされている API のために失敗した結果のスクリーンショット](images/unreal-publishing-img-11.png)

<span data-ttu-id="3e4f5-148">問題を修正するには:</span><span class="sxs-lookup"><span data-stu-id="3e4f5-148">To fix the issue:</span></span>
1. <span data-ttu-id="3e4f5-149">Unreal プロジェクトを開いて Unreal のインストールまたはソース ディレクトリのルートを参照し、タスク バーの Unreal アイコンを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-149">Browse to the Unreal installation or source directory root by opening an Unreal project and right-click on the Unreal icon in the taskbar.</span></span>
2. <span data-ttu-id="3e4f5-150">UE4Editor を右クリックし、[properties]\(プロパティ\) を選択して、 **[Location]\(場所\)** エントリのパスを参照します。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-150">Right-click on UE4Editor, select properties, and browse to the path in the **Location** entry:</span></span>

```
Open Engine\Plugins\Runtime\WindowsMixedReality\Source\WindowsMixedRealityHMD\WindowsMixedRealityHMD.Build.cs.
```

3. <span data-ttu-id="3e4f5-151">**WindowsMixedRealityHMD.Build.cs** で、**32 行目** を変更します。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-151">In **WindowsMixedRealityHMD.Build.cs**, modify **line 32** from:</span></span>

```cpp
if(Target.Platform != UnrealTargetPlatform.Win32)
```

<span data-ttu-id="3e4f5-152">を次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-152">to:</span></span>

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64)

```

4. <span data-ttu-id="3e4f5-153">Unreal を閉じ、プロジェクトを再び開いて、HoloLens を再度パッケージ化します。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-153">Close Unreal, reopen the project, and repackage for HoloLens.</span></span>  <span data-ttu-id="3e4f5-154">WACK を再実行すると、エラーが発生しなくなります。</span><span class="sxs-lookup"><span data-stu-id="3e4f5-154">Rerun WACK and the error will be gone.</span></span> 

## <a name="see-also"></a><span data-ttu-id="3e4f5-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e4f5-155">See also</span></span>

* [<span data-ttu-id="3e4f5-156">Microsoft Store へのアプリの送信</span><span class="sxs-lookup"><span data-stu-id="3e4f5-156">Submitting an app to the Microsoft Store</span></span>](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [<span data-ttu-id="3e4f5-157">Windows アプリ認定キット</span><span class="sxs-lookup"><span data-stu-id="3e4f5-157">Windows App Certification Kit</span></span>](https://developer.microsoft.com/windows/downloads/app-certification-kit)
* [<span data-ttu-id="3e4f5-158">アプリ インストーラー ファイルの手動作成</span><span class="sxs-lookup"><span data-stu-id="3e4f5-158">Create an App Installer file manually</span></span>](https://docs.microsoft.com/windows/msix/app-installer/how-to-create-appinstaller-file)