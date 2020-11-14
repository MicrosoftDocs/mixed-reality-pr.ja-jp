---
title: Unreal での WinRT
description: Unreal Engine 用の空間オーディオ プラグインの概要。
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 07/08/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, ストリーミング, リモート処理, Mixed Reality, 開発, 入門, 機能, 新しいプロジェクト, エミュレーター, ドキュメント, ガイド, 特徴, ホログラム, ゲームの開発
ms.openlocfilehash: 09d90af95d9433772563fdc292f31d118b3dd846
ms.sourcegitcommit: 8a80613f025b05a83393845d4af4da26a7d3ea9c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2020
ms.locfileid: "94573296"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="052a5-104">Unreal での WinRT</span><span class="sxs-lookup"><span data-stu-id="052a5-104">WinRT in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="052a5-105">概要</span><span class="sxs-lookup"><span data-stu-id="052a5-105">Overview</span></span>

<span data-ttu-id="052a5-106">HoloLens 開発の過程で、WinRT を使用して機能を作成することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="052a5-106">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="052a5-107">たとえば、HoloLens アプリケーションでファイルのダイアログを開くには、FileSavePicker ヘッダーファイルに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="052a5-107">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span>  <span data-ttu-id="052a5-108">Unreal は WinRT コードをネイティブにコンパイルしないため、独立したバイナリをビルドし、Unreal のビルドシステムで使用できるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="052a5-108">Since Unreal doesn't natively compile WinRT code, it's your job to build a separate binary and that can be consumed by Unreal’s build system.</span></span> <span data-ttu-id="052a5-109">このチュートリアルでは、このようなシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="052a5-109">This tutorial will walk you through just such a scenario.</span></span>

## <a name="objectives"></a><span data-ttu-id="052a5-110">目標</span><span class="sxs-lookup"><span data-stu-id="052a5-110">Objectives</span></span>
- <span data-ttu-id="052a5-111">FileSaveDialogue を開くユニバーサル Windows DLL を作成する</span><span class="sxs-lookup"><span data-stu-id="052a5-111">Create a Universal Windows DLL that opens a FileSaveDialogue</span></span>
- <span data-ttu-id="052a5-112">その DLL を Unreal game プロジェクトにリンクする</span><span class="sxs-lookup"><span data-stu-id="052a5-112">Link that DLL to an Unreal game project</span></span>
- <span data-ttu-id="052a5-113">新しい DLL を使用して、不要なブループリントから HoloLens にファイルを保存する</span><span class="sxs-lookup"><span data-stu-id="052a5-113">Save a file on the HoloLens from an Unreal blueprint using the new DLL</span></span>

## <a name="getting-started"></a><span data-ttu-id="052a5-114">作業の開始</span><span class="sxs-lookup"><span data-stu-id="052a5-114">Getting started</span></span>
1. <span data-ttu-id="052a5-115">すべての [必要なツール](tutorials/unreal-uxt-ch1.md) がインストールされていることを確認する</span><span class="sxs-lookup"><span data-stu-id="052a5-115">Check that you have all [required tools](tutorials/unreal-uxt-ch1.md) installed</span></span>
2. <span data-ttu-id="052a5-116">[新しい Unreal プロジェクトを作成](tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project)し、 **Consumewinrt** という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="052a5-116">[Create a new Unreal project](tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) and name it **Consumewinrt**</span></span>
3. <span data-ttu-id="052a5-117">HoloLens 開発に [必要なプラグイン](tutorials/unreal-uxt-ch2.md#enabling-required-plugins) を有効にする</span><span class="sxs-lookup"><span data-stu-id="052a5-117">Enable the [required plugins](tutorials/unreal-uxt-ch2.md#enabling-required-plugins) for HoloLens development</span></span>
4. <span data-ttu-id="052a5-118">デバイスまたはエミュレーターに[配置するためのセットアップ](tutorials/unreal-uxt-ch6.md)</span><span class="sxs-lookup"><span data-stu-id="052a5-118">[Setup for deployment](tutorials/unreal-uxt-ch6.md) to a device or emulator</span></span>

## <a name="creating-a-winrt-dll"></a><span data-ttu-id="052a5-119">WinRT DLL の作成</span><span class="sxs-lookup"><span data-stu-id="052a5-119">Creating a WinRT DLL</span></span> 
1. <span data-ttu-id="052a5-120">新しい Visual Studio プロジェクトを開き、Unreal game の **uproject** ファイルと同じディレクトリに **DLL (ユニバーサル Windows)** プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="052a5-120">Open a new Visual Studio project and create a **DLL (Universal Windows)** project in the same directory to the Unreal game’s **uproject** file.</span></span> 

![DLL の作成](images/unreal-winrt-img-01.png)

2. <span data-ttu-id="052a5-122">プロジェクトに **HoloLensWinrtDLL** という名前を付け、その場所を **ThirdParty** サブディレクトリとして、unreal game の uproject ファイルに設定します。</span><span class="sxs-lookup"><span data-stu-id="052a5-122">Name the project **HoloLensWinrtDLL** and set the location as a **ThirdParty** subdirectory to the Unreal game’s uproject file.</span></span> 
    * <span data-ttu-id="052a5-123">後でパスを簡単に検索するには **、[ソリューションとプロジェクトを同じディレクトリに配置** する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="052a5-123">Select **Place solution and project in the same directory** to simplify looking for paths later.</span></span> 

![DLL の構成](images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> <span data-ttu-id="052a5-125">新しいプロジェクトがコンパイルされた後、空白の cpp ファイルとヘッダーファイルに特に注意する必要があります。これには、それぞれ **HoloLensWinrtDLL** と **HoloLensWinrtDLL** という名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="052a5-125">After the new project compiles, you want to pay special attention to the blank cpp and header files, named **HoloLensWinrtDLL.cpp** and **HoloLensWinrtDLL.h** respectively.</span></span> <span data-ttu-id="052a5-126">ヘッダーは、Unreal の DLL を使用するインクルードファイルです。 cpp は、エクスポートした関数の本体を保持し、それ以外の場合はコンパイルできない WinRT コードを含みます。</span><span class="sxs-lookup"><span data-stu-id="052a5-126">The header is the include file that uses the DLL in Unreal, while the cpp holds the body of any functions you export and includes any WinRT code that Unreal wouldn't otherwise be able to compile.</span></span> 

3. <span data-ttu-id="052a5-127">コードを追加する前に、必要な WinRT コードをコンパイルできるように、プロジェクトのプロパティを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="052a5-127">Before you add any code, you need to update the project properties to ensure the WinRT code you need can compile:</span></span> 
    * <span data-ttu-id="052a5-128">HoloLensWinrtDLL プロジェクトを右クリックし、[ **プロパティ** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="052a5-128">Right click on the HoloLensWinrtDLL project and select **properties**</span></span>  
    * <span data-ttu-id="052a5-129">**構成** ドロップダウンを [ **すべての構成** ] に変更し、[ **プラットフォーム** ] ドロップダウンを [ **すべてのプラットフォーム** ] に変更します。</span><span class="sxs-lookup"><span data-stu-id="052a5-129">Change the **Configuration** dropdown to **All Configurations** and the **Platform** dropdown to **All Platforms**</span></span>  
    * <span data-ttu-id="052a5-130">[ **構成プロパティ] で> C/c + +> すべてのオプション** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="052a5-130">Under **Configuration Properties> C/C++> All Options** :</span></span>
        * <span data-ttu-id="052a5-131">非同期タスクを待機できるように、 **await** を **追加のオプション** に追加します。</span><span class="sxs-lookup"><span data-stu-id="052a5-131">Add **await** to **Additional Options** to ensure we can wait on async tasks</span></span>  
        * <span data-ttu-id="052a5-132">**C++ 言語標準** を **ISO c++ 17 標準 (/std: C++ 17)** に変更して WinRT コードを含める</span><span class="sxs-lookup"><span data-stu-id="052a5-132">Change **C++ Language Standard** to **ISO C++17 Standard (/std:c++17)** to include any WinRT code</span></span>

![プロジェクトプロパティのアップグレード](images/unreal-winrt-img-03.png)

<span data-ttu-id="052a5-134">プロジェクトは、ファイルダイアログを開き、ファイルを HoloLens ディスクに保存する WinRT コードを使用して、DLL のソースを更新する準備ができています。</span><span class="sxs-lookup"><span data-stu-id="052a5-134">Your project is ready to update the DLL’s source with WinRT code that opens a file dialogue and saves a file to the HoloLens disk.</span></span>  

## <a name="adding-the-dll-code"></a><span data-ttu-id="052a5-135">DLL コードの追加</span><span class="sxs-lookup"><span data-stu-id="052a5-135">Adding the DLL code</span></span>
1. <span data-ttu-id="052a5-136">**HoloLensWinrtDLL** を開き、dll のエクスポート関数を追加して、unreal に使用します。</span><span class="sxs-lookup"><span data-stu-id="052a5-136">Open **HoloLensWinrtDLL.h** and add a dll exported function for Unreal to consume:</span></span> 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. <span data-ttu-id="052a5-137">**HoloLensWinrtDLL** を開き、クラスで使用するすべてのヘッダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="052a5-137">Open **HoloLensWinrtDLL.cpp** and add all headers the class will use:</span></span>  

```cpp
#include "pch.h"
#include "HoloLensWinrtDLL.h"

#include <winrt/Windows.Storage.h>
#include <winrt/Windows.Storage.Streams.h>
#include <winrt/Windows.Storage.Pickers.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Foundation.Collections.h>

#include <string>
#include <vector>
#include <thread>
```

> [!NOTE]
> <span data-ttu-id="052a5-138">すべての WinRT コードは **HoloLensWinrtDLL** に格納されているため、unreal はヘッダーを参照するときに winrt コードを含めようとしません。</span><span class="sxs-lookup"><span data-stu-id="052a5-138">All WinRT code is stored in **HoloLensWinrtDLL.cpp** so Unreal doesn't try to include any WinRT code when referencing the header.</span></span> 

3. <span data-ttu-id="052a5-139">**HoloLensWinrtDLL** の中で、OpenFileDialogue () およびサポートされているすべてのコードの関数本体を追加します。</span><span class="sxs-lookup"><span data-stu-id="052a5-139">Still in **HoloLensWinrtDLL.cpp** , add a function body for OpenFileDialogue() and all supported code:</span></span> 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. <span data-ttu-id="052a5-140">SaveGameManager クラスを **HoloLensWinrtDLL** に追加して、ファイルのダイアログを処理し、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="052a5-140">Add a SaveGameManager class to **HoloLensWinrtDLL.cpp** to handle the file dialogue and saving the file:</span></span> 

```cpp
class SaveGameManager
{
public:
    SaveGameManager()
    {
    }

    ~SaveGameManager()
    {
        // Wait for currently running thread to complete before terminating.
        if(m_thread.joinable())
        {
            m_thread.join();
        }
    }

    void SaveGame()
    {
        OpenFileDialogueAction();
    }

private:
    winrt::Windows::Storage::StorageFile m_file = winrt::Windows::Storage::StorageFile(nullptr);
    std::thread m_thread;

    winrt::Windows::Foundation::IAsyncAction OpenFileDialogueAction()
    {
        std::vector<winrt::hstring> extensions;
        extensions.push_back(L".txt");

        auto picker = winrt::Windows::Storage::Pickers::FileSavePicker();

        // FileSavePicker needs a file type to open without errors.
        picker.FileTypeChoices().Insert(L"Plain Text",
                                        winrt::single_threaded_vector<winrt::hstring>(
                                        std::move(extensions)));

        // Opening the FilePicker must be done on the Game UI thread.
        // Any other IAsyncOperations should be done on a background thread.
        m_file = co_await picker.PickSaveFileAsync();

        if(m_file)
        {
            // Unreal's game thread is an STA, async tasks need to run on
            // a background MTA thread, or waiting on them will deadlock.    
            std::thread thread([this]() { RunThread(); });
            m_thread = std::move(thread);
        }
    }

    void RunThread()
    {
        // Ensure this thread is an MTA
        winrt::init_apartment();
        Run().get();
    }

    winrt::Windows::Foundation::IAsyncAction Run()
    {
        co_await winrt::Windows::Storage::FileIO::WriteTextAsync(
                m_file, L"Hello WinRT");
    }
};
```

5. <span data-ttu-id="052a5-141">**Release > ARM64** のソリューションをビルドして、dll ソリューションから ARM64/Release/HoloLensWinrtDLL 子ディレクトリに dll をビルドします。</span><span class="sxs-lookup"><span data-stu-id="052a5-141">Build the solution for **Release > ARM64** to build the DLL to the child directory ARM64/Release/HoloLensWinrtDLL from the DLL solution.</span></span> 

## <a name="adding-the-winrt-binary-to-unreal"></a><span data-ttu-id="052a5-142">WinRT バイナリを Unreal に追加する</span><span class="sxs-lookup"><span data-stu-id="052a5-142">Adding the WinRT binary to Unreal</span></span> 
<span data-ttu-id="052a5-143">アン Real で DLL をリンクして使用するには、C++ プロジェクトが必要です。</span><span class="sxs-lookup"><span data-stu-id="052a5-143">Linking and using a DLL in Unreal requires a C++ project.</span></span> <span data-ttu-id="052a5-144">ブループリントプロジェクトを使用している場合は、C++ クラスを追加することで、C++ プロジェクトに簡単に変換できます。</span><span class="sxs-lookup"><span data-stu-id="052a5-144">If you're using a Blueprint project, it can be easily converted to a C++ project by adding a C++ class:</span></span>  

1. <span data-ttu-id="052a5-145">Unreal エディターで、[ **ファイル > 新しい C++ クラス...** ] を開きます。</span><span class="sxs-lookup"><span data-stu-id="052a5-145">In the Unreal editor, open **File > New C++ Class…**</span></span> <span data-ttu-id="052a5-146">次に、 **Winrtactor** という名前の新しい **アクター** を作成し、DLL 内のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="052a5-146">and create a new **Actor** named **WinrtActor** to run the code in the DLL:</span></span> 

![新しいアクターの作成](images/unreal-winrt-img-04.png)

> [!NOTE]
> <span data-ttu-id="052a5-148">Uproject ファイルと同じディレクトリに、Source/ConsumeWinRT/ConsumeWinRT という名前の新しいビルドスクリプトと共にソリューションが作成されました。</span><span class="sxs-lookup"><span data-stu-id="052a5-148">A solution has now been created in the same directory as the uproject file along with a new build script named Source/ConsumeWinRT/ConsumeWinRT.Build.cs.</span></span>

2. <span data-ttu-id="052a5-149">ソリューションを開き、 **game/ConsumeWinRT/Source/consumewinrt** フォルダーを参照し、 **ConsumeWinRT.build.cs** を開きます。</span><span class="sxs-lookup"><span data-stu-id="052a5-149">Open the solution, browse for the **Games/ConsumeWinRT/Source/ConsumeWinRT** folder, and open **ConsumeWinRT.build.cs** :</span></span>

![ConsumeWinRT.build.cs ファイルを開く](images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a><span data-ttu-id="052a5-151">DLL のリンク</span><span class="sxs-lookup"><span data-stu-id="052a5-151">Linking the DLL</span></span>
1. <span data-ttu-id="052a5-152">**ConsumeWinRT.build.cs** で、プロパティを追加して、DLL のインクルードパス (HoloLensWinrtDLL を含むディレクトリ) を検索します。</span><span class="sxs-lookup"><span data-stu-id="052a5-152">In **ConsumeWinRT.build.cs** , add a property to find the include path for the DLL (the directory containing HoloLensWinrtDLL.h).</span></span> <span data-ttu-id="052a5-153">DLL は、インクルードパスの子ディレクトリにあるため、このプロパティはバイナリルートディレクトリとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="052a5-153">The DLL is in a child directory to the include path, so this property will be used as the binary root dir:</span></span>

```cs
using System.IO;

public class ConsumeWinRT : ModuleRules
{
    private string WinrtIncPath
    {
        get 
        {
            string ModulePath = Path.GetDirectoryName(
                   RulesCompiler.GetFileNameFromType(this.GetType()));

            // Third party directory is at the project root,
            // which is two directories up from the game .exe (Binaries/HoloLens)
            return Path.GetFullPath(
                   Path.Combine(ModulePath,
                   "../../ThirdParty/HoloLensWinrtDLL"));
        }
    }
}
```

2. <span data-ttu-id="052a5-154">クラスコンストラクターで、次のコードを追加してインクルードパスを更新し、新しい lib をリンクして、遅延読み込みを行い、DLL をパッケージ化された appx の場所にコピーします。</span><span class="sxs-lookup"><span data-stu-id="052a5-154">In the class constructor, add the following code to update the include path, link the new lib, and delay-load and copy the DLL to the packaged appx location:</span></span>

```cs
public ConsumeWinRT(ReadOnlyTargetRules target) : base(Target)
{
    // This is the directory the DLL's include header is in.
    PublicIncludePaths.Add(WinrtIncPath);

    // The code in HoloLensWinrtDLL will only work in a Windows Store app.
    // Only link these binaries for HoloLens.
    // Similar code can be written for desktop and similarly linked 
    // to use the same features when using Holographic Remoting.
    if(Target.Platform == UnrealTargetPlatform.HoloLens)
    {
        // Link the lib
        PublicAdditionalLibraries.Add(Path.Combine(
              WinrtIncPath, "ARM64", "Release",
              "HoloLensWinrtDLL","HoloLensWinrtDLL.lib"));

        string winrtDLL = "HoloLensWinrtDLL.dll";
        // Mark the dll to be DelayLoaded
        PublicDelayLoadDLLs.Add(winrtDLL);
        // RuntimeDependencies are included in packaged builds.
        RuntimeDependencies.Add(Path.Combine(WinrtIncPath,
                "ARM64", "Release", "HoloLensWinrtDLL", winrtDLL));
    }

    // Preserve the original code in build.cs below:
}
```

3. <span data-ttu-id="052a5-155">**Winrtactor** を開き、1つの関数定義を追加します。1つは、ブループリントによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="052a5-155">Open **WinrtActor.h** and add one function definition, one that a blueprint will call:</span></span> 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. <span data-ttu-id="052a5-156">**Winrtactor** を開き、beginplay を更新して DLL を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="052a5-156">Open **WinrtActor.cpp** and update BeginPlay to load the DLL:</span></span> 

```cpp
void AWinrtActor::BeginPlay()
{
    Super::BeginPlay();

    // Gets path to DLL location
    const FString BinDir = FPaths::ProjectDir() / 
        "ThirdParty" / "HoloLensWinrtDLL" / 
        "arm64" / "Release" / "HoloLensWinrtDLL";

    // Loads DLL into application
    void * dllHandle = FPlatformProcess::GetDllHandle(
        *(BinDir / "HoloLensWinrtDLL.dll"));
}

void AWinrtActor::OpenFileDialogue()
{
#if PLATFORM_HOLOLENS
    HoloLensWinrtDLL::OpenFileDialogue();
#endif
}
``` 

>[!CAUTION]
> <span data-ttu-id="052a5-157">DLL は、その関数のいずれかを呼び出す前に読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="052a5-157">The DLL must be loaded before calling any of its functions.</span></span>

### <a name="building-the-game"></a><span data-ttu-id="052a5-158">ゲームを構築する</span><span class="sxs-lookup"><span data-stu-id="052a5-158">Building the game</span></span>
1. <span data-ttu-id="052a5-159">ゲームソリューションをビルドして、game プロジェクトで開かれている Unreal エディターを起動します。</span><span class="sxs-lookup"><span data-stu-id="052a5-159">Build the game solution to launch the Unreal editor opened to the game project:</span></span> 
    * <span data-ttu-id="052a5-160">[ **アクターの配置** ] タブで、新しい **winrtactor** を検索し、シーンにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="052a5-160">In the **Place Actors** tab, search for the new **WinrtActor** and drag it into the scene</span></span> 
    * <span data-ttu-id="052a5-161">レベルブループリントを開き、 **Winrtactor** でブループリント呼び出し可能関数を実行します。</span><span class="sxs-lookup"><span data-stu-id="052a5-161">Open the level blueprint to execute the blueprint callable function in the **WinrtActor**</span></span> 

![WinrtActor をシーンに配置する](images/unreal-winrt-img-06.png)

2. <span data-ttu-id="052a5-163">**世界** 中では、前にシーンにドロップした **Windrtactor** を見つけて、レベルのブループリントにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="052a5-163">In the **World Outliner** , find the **WindrtActor** previously dropped into the scene and drag it into the level blueprint:</span></span> 

![WinrtActor をレベルブループリントにドラッグする](images/unreal-winrt-img-07.png)

3. <span data-ttu-id="052a5-165">レベルブループリントで、[出力] ノードを WinrtActor からドラッグし、[ **ファイルを開く] ダイアログ** を検索して、任意のユーザー入力からノードをルーティングします。</span><span class="sxs-lookup"><span data-stu-id="052a5-165">In the level blueprint, drag the output node from WinrtActor, search for **Open File Dialogue** , then route the node from any user input.</span></span>  <span data-ttu-id="052a5-166">この場合、[ファイルを開く] ダイアログが音声イベントから呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="052a5-166">In this case, Open File Dialogue is being called from a speech event:</span></span> 

![レベルブループリントでのノードの構成](images/unreal-winrt-img-08.png)

4. <span data-ttu-id="052a5-168">[このゲームを HoloLens 用にパッケージ化](tutorials/unreal-uxt-ch6.md)し、展開して、を実行します。</span><span class="sxs-lookup"><span data-stu-id="052a5-168">[Package this game for HoloLens](tutorials/unreal-uxt-ch6.md), deploy it, and run.</span></span>  

<span data-ttu-id="052a5-169">Unreal が OpenFileDialogue を呼び出すと、ファイルのダイアログが表示され、HoloLens のファイル名を要求するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="052a5-169">When Unreal calls OpenFileDialogue, a File Dialogue opens on the HoloLens prompting for a .txt file name.</span></span>  <span data-ttu-id="052a5-170">ファイルが保存されたら、デバイスポータルの [ **ファイルエクスプローラー** ] タブにアクセスして、"Hello WinRT" という内容を表示します。</span><span class="sxs-lookup"><span data-stu-id="052a5-170">After the file is saved, go to the **File explorer** tab in the device portal to see the contents “Hello WinRT”.</span></span> 

## <a name="summary"></a><span data-ttu-id="052a5-171">まとめ</span><span class="sxs-lookup"><span data-stu-id="052a5-171">Summary</span></span> 

<span data-ttu-id="052a5-172">このチュートリアルのコードは、Unreal で WinRT コードを使用するための出発点として使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="052a5-172">We encourage you to use the code in this tutorial as a starting point for consuming WinRT code in Unreal.</span></span>  <span data-ttu-id="052a5-173">Windows と同じファイルを使用して、ユーザーが HoloLens ディスクにファイルを保存できるようにします。</span><span class="sxs-lookup"><span data-stu-id="052a5-173">It allows users to save files to the HoloLens disk using the same file dialogue as Windows.</span></span>  <span data-ttu-id="052a5-174">同じプロセスに従って、HoloLensWinrtDLL ヘッダーから他の関数をエクスポートし、Unreal で使用します。</span><span class="sxs-lookup"><span data-stu-id="052a5-174">Follow the same process to export any additional functions from the HoloLensWinrtDLL header and used in Unreal.</span></span>  <span data-ttu-id="052a5-175">バックグラウンド MTA スレッドで非同期 WinRT コードを待機する DLL コードに注意してください。これにより、Unreal game スレッドのデッドロックが回避されます。</span><span class="sxs-lookup"><span data-stu-id="052a5-175">Note the DLL code that waits on any async WinRT code in a background MTA thread, which avoids deadlocking the Unreal game thread.</span></span> 

## <a name="next-development-checkpoint"></a><span data-ttu-id="052a5-176">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="052a5-176">Next Development Checkpoint</span></span>

<span data-ttu-id="052a5-177">私たちが用意した Unreal 開発チェックポイント体験に従っている場合、読者は Mixed Reality プラットフォームの機能と API を探索している段階にいます。</span><span class="sxs-lookup"><span data-stu-id="052a5-177">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="052a5-178">ここから、任意の [トピック](unreal-development-overview.md#3-platform-capabilities-and-apis) に進み、デバイスまたはエミュレーターへのアプリのデプロイに直接進むことができます。</span><span class="sxs-lookup"><span data-stu-id="052a5-178">From here, you can proceed to any [topic](unreal-development-overview.md#3-platform-capabilities-and-apis) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="052a5-179">デバイスへの配置</span><span class="sxs-lookup"><span data-stu-id="052a5-179">Deploying to device</span></span>](unreal-deploying.md)

## <a name="see-also"></a><span data-ttu-id="052a5-180">関連項目</span><span class="sxs-lookup"><span data-stu-id="052a5-180">See also</span></span>
* [<span data-ttu-id="052a5-181">C++/WinRT Api</span><span class="sxs-lookup"><span data-stu-id="052a5-181">C++/WinRT APIs</span></span>](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="052a5-182">FileSavePicker クラス</span><span class="sxs-lookup"><span data-stu-id="052a5-182">FileSavePicker class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="052a5-183">Unreal サードパーティ製ライブラリ</span><span class="sxs-lookup"><span data-stu-id="052a5-183">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
