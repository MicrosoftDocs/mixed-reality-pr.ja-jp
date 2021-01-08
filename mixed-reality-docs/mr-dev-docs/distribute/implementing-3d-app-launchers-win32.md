---
title: 3D アプリ起動ツールの実装 (Win32 アプリ)
description: '[スタート] メニューと [ホーム] 環境用に、Win32 VR アプリとゲーム用の3D アプリランチャーおよびロゴを作成する方法について説明します。'
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D、ロゴ、アイコン、モデリング、ランチャー、3D ランチャー、タイル、live cube、win32、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、マニフェスト
ms.openlocfilehash: 63b07664cb09f51e6d0588fdc50d141ad8985093
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009671"
---
# <a name="implement-3d-app-launchers-win32-apps"></a><span data-ttu-id="c8664-104">3D アプリ起動ツールの実装 (Win32 アプリ)</span><span class="sxs-lookup"><span data-stu-id="c8664-104">Implement 3D app launchers (Win32 apps)</span></span>

> [!NOTE]
> <span data-ttu-id="c8664-105">この機能は、最新の [Windows Insider](https://insider.windows.com) 便 (RS5)、ビルド17704以降を実行している pc でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c8664-105">This feature is only available to PCs running the latest [Windows Insider](https://insider.windows.com) flights (RS5), build 17704 and newer.</span></span>

<span data-ttu-id="c8664-106">[Windows Mixed Reality ホーム](../discover/navigating-the-windows-mixed-reality-home.md)は、アプリケーションを起動する前にユーザーが移動する開始点です。</span><span class="sxs-lookup"><span data-stu-id="c8664-106">The [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="c8664-107">既定では、Windows Mixed Reality の [スタート] メニューの [すべてのアプリ] 一覧に表示されない、ヘッドセットの外部からイマーシブ Win32 VR アプリとゲームを起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8664-107">By default, you need to launch immersive Win32 VR apps and games from outside the headset and won't appear in the "All apps" list on the Windows Mixed Reality Start menu.</span></span> <span data-ttu-id="c8664-108">この記事に記載されている手順に従って3D アプリランチャーを実装すると、Windows Mixed Reality の [スタート] メニューと [ホーム] 環境内からイマーシブ Win32 VR エクスペリエンスを起動できます。</span><span class="sxs-lookup"><span data-stu-id="c8664-108">If you follow the instructions in this article to implement a 3D app launcher, your immersive Win32 VR experience can be launched from within the Windows Mixed Reality Start menu and home environment.</span></span>

<span data-ttu-id="c8664-109">これは、蒸気の外部で分散されたイマーシブ Win32 VR エクスペリエンスの場合にのみ当てはまります。</span><span class="sxs-lookup"><span data-stu-id="c8664-109">This is only true for immersive Win32 VR experiences distributed outside of Steam.</span></span> <span data-ttu-id="c8664-110">[ストリームによって配布](../develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)される VR エクスペリエンスについては、Windows [Mixed Reality For Steamvr Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800)と最新の windows Insider RS5 フライトを更新しました。これにより、既定のランチャーを使用して、"すべてのアプリ" リストの windows Mixed reality の [スタート] メニューに steamvr タイトルが自動的に表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="c8664-110">For VR experiences [distributed through Steam](../develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md), we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest Windows Insider RS5 flights so that SteamVR titles show up in the Windows Mixed Reality Start menu in the "All apps" list automatically using a default launcher.</span></span> <span data-ttu-id="c8664-111">言い換えると、この記事で説明されている方法は SteamVR タイトルには不要であり、Windows Mixed Reality for SteamVR Beta 機能によって上書きされます。</span><span class="sxs-lookup"><span data-stu-id="c8664-111">In other words, the method described in this article is unnecessary for SteamVR titles and will be overridden by the Windows Mixed Reality for SteamVR Beta functionality.</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="c8664-112">3D アプリランチャー作成プロセス</span><span class="sxs-lookup"><span data-stu-id="c8664-112">3D app launcher creation process</span></span>

<span data-ttu-id="c8664-113">3D アプリランチャーを作成するには、次の3つの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="c8664-113">There are three steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="c8664-114">設計と concepting</span><span class="sxs-lookup"><span data-stu-id="c8664-114">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="c8664-115">モデリングとエクスポート</span><span class="sxs-lookup"><span data-stu-id="c8664-115">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="c8664-116">アプリケーションへの統合 (この記事)</span><span class="sxs-lookup"><span data-stu-id="c8664-116">Integrating it into your application (this article)</span></span>

<span data-ttu-id="c8664-117">アプリケーションのランチャーとして使用する3D アセットは、互換性を確保するために、 [Windows Mixed Reality オーサリングガイドライン](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) を使用して作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8664-117">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="c8664-118">このオーサリング仕様に合わなかった資産は、Windows Mixed Reality ホームではレンダリングされません。</span><span class="sxs-lookup"><span data-stu-id="c8664-118">Assets that fail to meet this authoring specification won't be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="c8664-119">3D ランチャーの構成</span><span class="sxs-lookup"><span data-stu-id="c8664-119">Configuring the 3D launcher</span></span>

<span data-ttu-id="c8664-120">Win32 アプリケーションは、Windows Mixed Reality の [スタート] メニューの [すべてのアプリ] の一覧に表示されます (3D アプリランチャーを作成した場合)。</span><span class="sxs-lookup"><span data-stu-id="c8664-120">Win32 applications will appear in the "All apps" list on the Windows Mixed Reality Start menu if you create a 3D app launcher for them.</span></span> <span data-ttu-id="c8664-121">これを行うには、次の手順に従って、3D アプリランチャーを参照する [ビジュアル要素マニフェスト](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="c8664-121">To do that, create a [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML file referencing the 3D App Launcher by following these steps:</span></span>

1. <span data-ttu-id="c8664-122">**3D アプリランチャー ASSET GLB ファイル** を作成します (「[モデリングとエクスポート](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="c8664-122">Create a **3D App Launcher asset GLB file** (See [Modeling and exporting](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span></span>
2. <span data-ttu-id="c8664-123">アプリケーションの **[ビジュアル要素マニフェスト](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** を作成します。</span><span class="sxs-lookup"><span data-stu-id="c8664-123">Create a **[Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** for your application.</span></span>
    1. <span data-ttu-id="c8664-124">[次のサンプル](#sample-visual-elements-manifest)から始めることができます。</span><span class="sxs-lookup"><span data-stu-id="c8664-124">You can start with the [sample below](#sample-visual-elements-manifest).</span></span>  <span data-ttu-id="c8664-125">詳細については、 [ビジュアル要素](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) の完全なマニフェストに関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8664-125">See the full [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) documentation for more details.</span></span>
    2. <span data-ttu-id="c8664-126">アプリの PNG/JPG/GIF で **Square150x150Logo** と **Square70x70Logo** を更新します。</span><span class="sxs-lookup"><span data-stu-id="c8664-126">Update **Square150x150Logo** and **Square70x70Logo** with a PNG/JPG/GIF for your app.</span></span>
        * <span data-ttu-id="c8664-127">これらは、Windows Mixed Reality のすべてのアプリの一覧とデスクトップの [スタート] メニューのアプリの2D ロゴに使用されます。</span><span class="sxs-lookup"><span data-stu-id="c8664-127">These will be used for the app’s 2D logo in the Windows Mixed Reality All Apps list and for the Start Menu on desktop.</span></span>
        * <span data-ttu-id="c8664-128">ファイルパスは、ビジュアル要素マニフェストを含むフォルダーに基づいています。</span><span class="sxs-lookup"><span data-stu-id="c8664-128">The file path is based on the folder containing the Visual Elements Manifest.</span></span>
        * <span data-ttu-id="c8664-129">その場合でも、標準のメカニズムを使用して、アプリのデスクトップの [スタート] メニューアイコンを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8664-129">You still need to provide a desktop Start Menu icon for your app through the standard mechanisms.</span></span> <span data-ttu-id="c8664-130">これは、実行可能ファイルまたは作成したショートカットに直接配置できます。</span><span class="sxs-lookup"><span data-stu-id="c8664-130">This can either be directly in the executable or in the shortcut you create.</span></span> <span data-ttu-id="c8664-131">たとえば、IShellLink:: SetIconLocation を使用します。</span><span class="sxs-lookup"><span data-stu-id="c8664-131">For example, via IShellLink::SetIconLocation.</span></span>
        * <span data-ttu-id="c8664-132">*省略可能:* MRT.DLL がさまざまな解像度スケールとハイコントラストテーマに対して複数のアセットサイズを提供する場合は、リソースの pri ファイルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c8664-132">*Optional:* You can use a resources.pri file if you would like for MRT to provide multiple asset sizes for different resolution scales and high contrast themes.</span></span>
    3. <span data-ttu-id="c8664-133">3D アプリランチャーの GLB をポイントするように **MixedRealityModel パス** を更新します。</span><span class="sxs-lookup"><span data-stu-id="c8664-133">Update the **MixedRealityModel Path** to point to the GLB for your 3D App Launcher</span></span>
    4. <span data-ttu-id="c8664-134">実行可能ファイルと同じ名前でファイルを保存し、拡張子を ".VisualElementsManifest.xml" にして、同じディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="c8664-134">Save the file with the same name as your executable file, with an extension of ".VisualElementsManifest.xml" and save it in the same directory.</span></span> <span data-ttu-id="c8664-135">たとえば、実行可能ファイル "contoso.exe" の場合、付随する XML ファイルには "contoso.visualelementsmanifest.xml" という名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="c8664-135">For example, for the executable file "contoso.exe", the accompanying XML file is named "contoso.visualelementsmanifest.xml".</span></span>
3. <span data-ttu-id="c8664-136">アプリケーションへの **ショートカットを** デスクトップの [スタート] メニューに追加します。</span><span class="sxs-lookup"><span data-stu-id="c8664-136">**Add a shortcut** to your application to the desktop Windows Start Menu.</span></span> <span data-ttu-id="c8664-137">C++ の実装例については、 [次のサンプル](#sample-app-launcher-shortcut-creation) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8664-137">See the [sample below](#sample-app-launcher-shortcut-creation) for an example C++ implementation.</span></span> 
    * <span data-ttu-id="c8664-138">%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) または%APPDATA%\Microsoft\Windows\Start Menu\Programs (user) で作成する</span><span class="sxs-lookup"><span data-stu-id="c8664-138">Create it in %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) or %APPDATA%\Microsoft\Windows\Start Menu\Programs (user)</span></span>
    * <span data-ttu-id="c8664-139">更新によって、ビジュアル要素マニフェストまたはそれによって参照される資産が変更された場合、更新プログラムによって、マニフェストが再解析され、キャッシュされたアセットが更新されるようにショートカットが更新されます。</span><span class="sxs-lookup"><span data-stu-id="c8664-139">If an update changes your visual elements manifest or the assets referenced by it, the updater or installer should update the shortcut such that the manifest is reparsed and cached assets are updated.</span></span>
4. <span data-ttu-id="c8664-140">*省略可能:* デスクトップショートカットがアプリケーションの EXE を直接指していない場合 (たとえば、"myapp://" のようなカスタムプロトコルハンドラーが呼び出された場合)、[スタート] メニューはアプリの VisualElementsManifest.xml ファイルを自動的に検索しません。</span><span class="sxs-lookup"><span data-stu-id="c8664-140">*Optional:* If your desktop shortcut doesn't point directly to your application’s EXE (for example, if it invokes a custom protocol handler like “myapp://”), the Start Menu won’t automatically find the app’s VisualElementsManifest.xml file.</span></span> <span data-ttu-id="c8664-141">これを解決するには、ショートカットで VisualElementsManifestHintPath () を使用して、ビジュアル要素マニフェストのファイルパスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8664-141">To resolve this, the shortcut should specify the file path of the Visual Elements Manifest using System.AppUserModel.VisualElementsManifestHintPath ().</span></span> <span data-ttu-id="c8664-142">これは、System.AppUserModel.ID と同じ手法を使用して、ショートカットで設定できます。</span><span class="sxs-lookup"><span data-stu-id="c8664-142">This can be set in the shortcut using the same techniques as System.AppUserModel.ID.</span></span> <span data-ttu-id="c8664-143">System.AppUserModel.ID を使用する必要はありませんが、アプリケーションの明示的なアプリケーションユーザーモデル ID が使用されている場合は、そのショートカットに一致させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8664-143">You aren't required to use System.AppUserModel.ID but you may do so if you wish for the shortcut to match the explicit Application User Model ID of the application if one is used.</span></span>  <span data-ttu-id="c8664-144">C++ のサンプルについては、以下の [サンプルアプリランチャーのショートカットの作成](#sample-app-launcher-shortcut-creation) に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8664-144">See the [sample app launcher shortcut creation](#sample-app-launcher-shortcut-creation) section below for a C++ sample.</span></span>

### <a name="sample-visual-elements-manifest"></a><span data-ttu-id="c8664-145">ビジュアル要素マニフェストのサンプル</span><span class="sxs-lookup"><span data-stu-id="c8664-145">Sample Visual Elements Manifest</span></span>

```xml
<Application xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance">
  <VisualElements
    ShowNameOnSquare150x150Logo="on"
    Square150x150Logo="YOUR_APP_LOGO_150X150.png"
    Square70x70Logo=" YOUR_APP_LOGO_70X70.png"
    ForegroundText="light"
    BackgroundColor="#000000">
    <MixedRealityModel Path="YOUR_3D_APP_LAUNCHER_ASSET.glb">
        <SpatialBoundingBox Center="0,0,0" Extents="Auto" />
    </MixedRealityModel>
  </VisualElements>
</Application>
```

### <a name="sample-app-launcher-shortcut-creation"></a><span data-ttu-id="c8664-146">サンプルアプリランチャーショートカットの作成</span><span class="sxs-lookup"><span data-stu-id="c8664-146">Sample app launcher shortcut creation</span></span>

<span data-ttu-id="c8664-147">次のサンプルコードは、C++ でショートカットを作成する方法を示しています。これには、ビジュアル要素マニフェスト XML ファイルへのパスのオーバーライドも含まれます。</span><span class="sxs-lookup"><span data-stu-id="c8664-147">The sample code below shows how you can create a shortcut in C++, including overriding the path to the Visual Elements Manifest XML file.</span></span> <span data-ttu-id="c8664-148">注: このオーバーライドは、ショートカットがマニフェストに関連付けられている EXE を直接指していない場合にのみ必要です (たとえば、ショートカットで "myapp://" のようなカスタムプロトコルハンドラーが使用されている場合)。</span><span class="sxs-lookup"><span data-stu-id="c8664-148">Note the override is only required in cases where your shortcut doesn't point directly to the EXE associated with the manifest (for example, your shortcut uses a custom protocol handler like "myapp://").</span></span>

#### <a name="sample-lnk-shortcut-creation-c"></a><span data-ttu-id="c8664-149">サンプル.LNK ショートカットの作成 (C++)</span><span class="sxs-lookup"><span data-stu-id="c8664-149">Sample .LNK shortcut creation (C++)</span></span>

```cpp
#include <windows.h>
#include <propkey.h>
#include <shlobj_core.h>
#include <shlwapi.h>
#include <propvarutil.h>
#include <wrl.h>

#include <memory>

using namespace Microsoft::WRL;

#define RETURN_IF_FAILED(x) do { HRESULT hr = x; if (FAILED(hr)) { return hr; } } while(0)
#define RETURN_IF_WIN32_BOOL_FALSE(x) do { DWORD res = x; if (res == 0) { return HRESULT_FROM_WIN32(GetLastError()); } } while(0)

int wmain()
{
    RETURN_IF_FAILED(CoInitializeEx(nullptr, COINIT_APARTMENTTHREADED));

    ComPtr<IShellLink> shellLink;
    RETURN_IF_FAILED(CoCreateInstance(__uuidof(ShellLink), nullptr, CLSCTX_INPROC_SERVER, IID_PPV_ARGS(&shellLink)));
    RETURN_IF_FAILED(shellLink->SetPath(L"MyLauncher://launch/app-identifier"));

    // It is also possible to use an icon file in another location. For example, "C:\Program Files (x86)\MyLauncher\assets\app-identifier.ico".
    RETURN_IF_FAILED(shellLink->SetIconLocation(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.exe", 0 /*iIcon*/));

    ComPtr<IPropertyStore> propStore;
    RETURN_IF_FAILED(shellLink.As(&propStore));

    {
        // Optional: If the application has an explict Application User Model ID, then you should usually specify it in the shortcut.
        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"ExplicitAppUserModelID", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_ID, propVar));
        PropVariantClear(&propVar);
    }

    {
        // A hint path to the manifest is only necessary if the target path of the shortcut is not a file path to the executable.
        // By convention the manifest is named <executable name>.VisualElementsManifest.xml and is in the same folder as the executable
        // (and resources.pri if applicable). Assets referenced by the manifest are relative to the folder containing the manifest.

        //
        // PropKey.h
        //
        //  Name:     System.AppUserModel.VisualElementsManifestHintPath -- PKEY_AppUserModel_VisualElementsManifestHintPath
        //  Type:     String -- VT_LPWSTR  (For variants: VT_BSTR)
        //  FormatID: {9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}, 31
        //  
        //  Suggests where to look for the VisualElementsManifest for a Win32 app
        //
        // DEFINE_PROPERTYKEY(PKEY_AppUserModel_VisualElementsManifestHintPath, 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3, 31);
        // #define INIT_PKEY_AppUserModel_VisualElementsManifestHintPath { { 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3 }, 31 }

        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.visualelementsmanifest.xml", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_VisualElementsManifestHintPath, propVar));
        PropVariantClear(&propVar);
    }

    constexpr PCWSTR shortcutPath = L"%APPDATA%\\Microsoft\\Windows\\Start Menu\\Programs\\game.lnk";
    const DWORD requiredBufferLength = ExpandEnvironmentStrings(shortcutPath, nullptr, 0);
    RETURN_IF_WIN32_BOOL_FALSE(requiredBufferLength);

    const auto expandedShortcutPath = std::make_unique<wchar_t[]>(requiredBufferLength);
    RETURN_IF_WIN32_BOOL_FALSE(ExpandEnvironmentStrings(shortcutPath, expandedShortcutPath.get(), requiredBufferLength));

    ComPtr<IPersistFile> persistFile;
    RETURN_IF_FAILED(shellLink.As(&persistFile));
    RETURN_IF_FAILED(persistFile->Save(expandedShortcutPath.get(), FALSE));

    return 0;
}
```

#### <a name="sample-url-launcher-shortcut"></a><span data-ttu-id="c8664-150">サンプル.URL ランチャーショートカット</span><span class="sxs-lookup"><span data-stu-id="c8664-150">Sample .URL launcher shortcut</span></span> 

```
[{9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}]
Prop31=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.visualelementsmanifest.xml
Prop5=ExplicitAppUserModelID

[{000214A0-0000-0000-C000-000000000046}]
Prop3=19,0

[InternetShortcut]
IDList=
URL=MyLauncher://launch/app-identifier
IconFile=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.exe
IconIndex=0
```

## <a name="see-also"></a><span data-ttu-id="c8664-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8664-151">See also</span></span>

* <span data-ttu-id="c8664-152">3D アプリランチャーを含む[Mixed reality モデルサンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)。</span><span class="sxs-lookup"><span data-stu-id="c8664-152">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="c8664-153">3D アプリ起動ツールの設計ガイダンス</span><span class="sxs-lookup"><span data-stu-id="c8664-153">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="c8664-154">Windows Mixed Reality ホームで使用するための3D モデルの作成</span><span class="sxs-lookup"><span data-stu-id="c8664-154">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="c8664-155">3D アプリランチャーの実装 (UWP アプリ)</span><span class="sxs-lookup"><span data-stu-id="c8664-155">Implementing 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="c8664-156">Windows Mixed Reality ホームのナビゲーション</span><span class="sxs-lookup"><span data-stu-id="c8664-156">Navigating the Windows Mixed Reality home</span></span>](../discover/navigating-the-windows-mixed-reality-home.md)
