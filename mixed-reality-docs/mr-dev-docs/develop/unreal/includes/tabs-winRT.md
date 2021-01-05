---
ms.openlocfilehash: 6bed33ee9b41a4ee66ce4c1c579d398f0958143d
ms.sourcegitcommit: db01faaf76bccd4f0432cf6b383fefa04ab7a085
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2020
ms.locfileid: "97745730"
---
# <a name="426"></a>[<span data-ttu-id="e2d23-101">4.26</span><span class="sxs-lookup"><span data-stu-id="e2d23-101">4.26</span></span>](#tab/426)

## <a name="the-standard-winrt-apis"></a><span data-ttu-id="e2d23-102">標準の WinRT Api</span><span class="sxs-lookup"><span data-stu-id="e2d23-102">The standard WinRT APIs</span></span>

<span data-ttu-id="e2d23-103">WinRT を使用する最も一般的で簡単な方法は、WinSDK からメソッドを呼び出すことです。</span><span class="sxs-lookup"><span data-stu-id="e2d23-103">The most common and easiest way to use WinRT is to call methods from WinSDK.</span></span> <span data-ttu-id="e2d23-104">これを行うには、YourModule.Build.cs ファイルを開き、次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="e2d23-104">To do so, open YourModule.Build.cs file and add the following lines:</span></span>

```csharp
if (Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    // These parameters are mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.AddRange(new string[] { "shlwapi.lib", "runtimeobject.lib" });
    PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir,        
                                        "Include", 
                                        Target.WindowsPlatform.WindowsSdkVersion, 
                                        "cppwinrt"));
}
```

<span data-ttu-id="e2d23-105">次に、次の WinRT ヘッダーを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2d23-105">Next, you need to add the following WinRT headers:</span></span> 

```cpp
#if (PLATFORM_WINDOWS || PLATFORM_HOLOLENS) 
//Before writing any code, you need to disable common warnings in WinRT headers
#pragma warning(disable : 5205 4265 4268 4946)

#include "Windows/AllowWindowsPlatformTypes.h"
#include "Windows/AllowWindowsPlatformAtomics.h"
#include "Windows/PreWindowsApi.h"

#include <unknwn.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Perception.Spatial.h>
#include <winrt/Windows.Foundation.Collections.h>

#include "Windows/PostWindowsApi.h"
#include "Windows/HideWindowsPlatformAtomics.h"
#include "Windows/HideWindowsPlatformTypes.h"
#endif
```

<span data-ttu-id="e2d23-106">WinRT コードは、Win64 および HoloLens プラットフォームでのみコンパイルできるため、if ステートメントを使用すると、WinRT ライブラリが他のプラットフォームに含まれないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="e2d23-106">WinRT code can only be compiled in the Win64 and HoloLens platforms, so the if statement prevents WinRT libraries from being included on other platforms.</span></span> <span data-ttu-id="e2d23-107">IUnknown インターフェイスを持つために unknwn が追加されました。</span><span class="sxs-lookup"><span data-stu-id="e2d23-107">unknwn.h was added for having the IUnknown interface.</span></span> 


## <a name="winrt-from-a-nuget-package"></a><span data-ttu-id="e2d23-108">NuGet パッケージからの WinRT</span><span class="sxs-lookup"><span data-stu-id="e2d23-108">WinRT from a NuGet package</span></span>

<span data-ttu-id="e2d23-109">WinRT サポートを含む NuGet パッケージを追加する必要がある場合は、少し複雑になります。</span><span class="sxs-lookup"><span data-stu-id="e2d23-109">It’s a little more complicated if you need to add a NuGet package with WinRT support.</span></span> <span data-ttu-id="e2d23-110">この場合、Visual Studio は実質的にすべてのジョブを実行できますが、Unreal ビルドシステムでは実行できません。</span><span class="sxs-lookup"><span data-stu-id="e2d23-110">In this case, Visual Studio can do practically all job for you, but the Unreal build system can’t.</span></span> <span data-ttu-id="e2d23-111">さいわい、それほど難しくはありません。</span><span class="sxs-lookup"><span data-stu-id="e2d23-111">Luckily, it’s not too difficult.</span></span> <span data-ttu-id="e2d23-112">MixedReality パッケージをダウンロードする方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e2d23-112">Below is an example of how you would go about downloading the Microsoft.MixedReality.QR package.</span></span> <span data-ttu-id="e2d23-113">別のファイルに置き換えることができます。 winmd ファイルが失われていないことを確認し、正しい dll をコピーするだけです。</span><span class="sxs-lookup"><span data-stu-id="e2d23-113">You can replace it with another, just make sure you don’t lose the winmd file and copy the correct dll.</span></span> 

<span data-ttu-id="e2d23-114">前のセクションの Windows SDK dll は、OS によって処理されます。</span><span class="sxs-lookup"><span data-stu-id="e2d23-114">Windows SDK dlls from the previous section are handled by the OS.</span></span> <span data-ttu-id="e2d23-115">NuGet の dll は、モジュール内のコードによって管理されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2d23-115">NuGet’s dlls must be managed by the code in your module.</span></span> <span data-ttu-id="e2d23-116">モジュールをダウンロードし、バイナリフォルダーにコピーして、モジュールの起動時にプロセスメモリに読み込むコードを追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e2d23-116">We recommend adding code to download them, copying into binaries folder, and load into the process memory at the module startup.</span></span>

<span data-ttu-id="e2d23-117">最初の手順では、 https://docs.microsoft.com/nuget/reference/packages-config) モジュールのルートフォルダーに packages.config を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2d23-117">At the first step, you should add a packages.config (https://docs.microsoft.com/nuget/reference/packages-config) into the root folder of your module.</span></span> <span data-ttu-id="e2d23-118">ここでは、すべての依存関係を含め、ダウンロードするすべてのパッケージを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2d23-118">There you should add all packages you want to download, including all their dependencies.</span></span> <span data-ttu-id="e2d23-119">ここで、プライマリペイロードとして MixedReality を追加し、他の2つを依存関係として追加しました。</span><span class="sxs-lookup"><span data-stu-id="e2d23-119">Here I added Microsoft.MixedReality.QR as a primary payload and two others as dependencies to it.</span></span> <span data-ttu-id="e2d23-120">このファイルの形式は、Visual Studio の場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="e2d23-120">The format of that file is same as in Visual Studio:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.MixedReality.QR" version="0.5.2102" targetFramework="native" />
  <package id="Microsoft.VCRTForwarders.140" version="1.0.6" targetFramework="native" />
  <package id="Microsoft.Windows.CppWinRT" version="2.0.200729.8" targetFramework="native" />
</packages>
```

<span data-ttu-id="e2d23-121">これで、NuGet や必要なパッケージをダウンロードしたり、NuGet の [ドキュメント](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-nuget-cli)を参照したりできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="e2d23-121">Now you can download the NuGet, the required packages, or refer to the NuGet [documentation](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-nuget-cli).</span></span>

<span data-ttu-id="e2d23-122">YourModule.Build.cs を開き、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e2d23-122">Open YourModule.Build.cs and add the following code:</span></span>

```csharp
if(Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    string MyModuleName = GetType().Name;

    // these parameters mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.Add("shlwapi.lib");
    PublicSystemLibraries.Add("runtimeobject.lib");

    // prepare everything for nuget
    string NugetFolder = Path.Combine(PluginDirectory, "Intermediate", "Nuget", MyModuleName);
    Directory.CreateDirectory(NugetFolder);

    string BinariesSubFolder = Path.Combine("Binaries", "ThirdParty", Target.Type.ToString(), Target.Platform.ToString(), Target.Architecture);

    PrivateDefinitions.Add(string.Format("THIRDPARTY_BINARY_SUBFOLDER=\"{0}\"", BinariesSubFolder.Replace(@"\", @"\\")));

    string BinariesFolder = Path.Combine(PluginDirectory, BinariesSubFolder);
    Directory.CreateDirectory(BinariesFolder);

    // download nuget
    string NugetExe = Path.Combine(NugetFolder, "nuget.exe");
    if(!File.Exists(NugetExe))
    {
        using (System.Net.WebClient myWebClient = new System.Net.WebClient())
        {
            myWebClient.DownloadFile(@"https://dist.nuget.org/win-x86-commandline/latest/nuget.exe", NugetExe);
        }
    }

    // run nuget to update the packages
    {
        var StartInfo = new System.Diagnostics.ProcessStartInfo(NugetExe, string.Format("install \"{0}\" -OutputDirectory \"{1}\"", Path.Combine(ModuleDirectory, "packages.config"), NugetFolder));
        StartInfo.UseShellExecute = false;
        StartInfo.CreateNoWindow = true;
        var ExitCode = Utils.RunLocalProcessAndPrintfOutput(StartInfo);
        if (ExitCode < 0)
        {
            throw new BuildException("Failed to get nuget packages.  See log for details.");
        }
    }
            
    // get list of the installed packages
    string[] InstalledPackages = Utils.RunLocalProcessAndReturnStdOut(NugetExe, string.Format("list -Source \"{0}\"", NugetFolder)).Split(new char[] {'\r', '\n' });

    // get WinRT package 
    string CppWinRTPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.Windows.CppWinRT"));
    if(!string.IsNullOrEmpty(CppWinRTPackage))
    {
        string CppWinRTName = CppWinRTPackage.Replace(" ", ".");
        string CppWinRTExe = Path.Combine(NugetFolder, CppWinRTName, "bin", "cppwinrt.exe");
        string CppWinRTFolder = Path.Combine(PluginDirectory, "Intermediate", CppWinRTName, MyModuleName);
        Directory.CreateDirectory(CppWinRTFolder);

        // search all downloaded packages for winmd files
        string[] WinMDFiles = Directory.GetFiles(NugetFolder, "*.winmd", SearchOption.AllDirectories);

        // all downloaded winmd file with WinSDK to be processed by cppwinrt.exe
        var WinMDFilesStringbuilder = new System.Text.StringBuilder();
        foreach(var winmd in WinMDFiles)
        {
            WinMDFilesStringbuilder.Append(" -input \"");
            WinMDFilesStringbuilder.Append(winmd);
            WinMDFilesStringbuilder.Append("\"");
        }

        // generate winrt headers and add them into include paths
        var StartInfo = new System.Diagnostics.ProcessStartInfo(CppWinRTExe, string.Format("{0} -input \"{1}\" -output \"{2}\"", WinMDFilesStringbuilder, Target.WindowsPlatform.WindowsSdkVersion, CppWinRTFolder));
        StartInfo.UseShellExecute = false;
        StartInfo.CreateNoWindow = true;
        var ExitCode = Utils.RunLocalProcessAndPrintfOutput(StartInfo);
        if (ExitCode < 0)
        {
            throw new BuildException("Failed to get generate WinRT headers.  See log for details.");
        }

        PrivateIncludePaths.Add(CppWinRTFolder);
    }
    else
    {
        // fall back to default WinSDK headers
        PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir, "Include", Target.WindowsPlatform.WindowsSdkVersion, "cppwinrt"));
    }

    // WinRT lib for some job
    string QRPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.MixedReality.QR"));
    if (!string.IsNullOrEmpty(QRPackage))
    {
        string QRFolderName = QRPackage.Replace(" ", ".");

        // copying dll and winmd binaries to our local binaries folder
        // !!!!! please make sure that you use the path of file! Unreal can't do it for you !!!!!
        SafeCopy(Path.Combine(NugetFolder, QRFolderName, @"lib\uap10.0.18362\Microsoft.MixedReality.QR.winmd"), 
        Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        SafeCopy(Path.Combine(NugetFolder, QRFolderName, string.Format(@"runtimes\win10-{0}\native\Microsoft.MixedReality.QR.dll", Target.WindowsPlatform.Architecture.ToString())), 
        Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));

        // also both both binaries must be in RuntimeDependencies, unless you get failures in Hololens platform
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));
    }

    if(Target.Platform == UnrealTargetPlatform.Win64)
    {
        // Microsoft.VCRTForwarders.140 is needed to run WinRT dlls in Win64 platforms
        string VCRTForwardersPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.VCRTForwarders.140"));
        if (!string.IsNullOrEmpty(VCRTForwardersPackage))
        {
            string VCRTForwardersName = VCRTForwardersPackage.Replace(" ", ".");
            foreach (var Dll in Directory.EnumerateFiles(Path.Combine(NugetFolder, VCRTForwardersName, "runtimes/win10-x64/native/release"), "*_app.dll"))
            {
                string newDll = Path.Combine(BinariesFolder, Path.GetFileName(Dll));
                SafeCopy(Dll, newDll);
                RuntimeDependencies.Add(newDll);
            }
        }
    }
```

<span data-ttu-id="e2d23-123">SafeCopy メソッドは次のように定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2d23-123">You'll need to define the SafeCopy method as follows:</span></span>

```csharp
private void SafeCopy(string source, string destination)
{
    if(!File.Exists(source))
    {
        Log.TraceError("Class {0} can't find {1} file for copying", this.GetType().Name, source);
        return;
    }

    try
    {
        File.Copy(source, destination, true);
    }
    catch(IOException ex)
    {
        Log.TraceWarning("Failed to copy {0} to {1} with exception: {2}", source, destination, ex.Message);
        if (!File.Exists(destination))
        {
            Log.TraceError("Destination file {0} does not exist", destination);
            return;
        }

        Log.TraceWarning("Destination file {0} already existed and is probably in use.  The old file will be used for the runtime dependency.  This may happen when packaging a Win64 exe from the editor.", destination);
    }
}
```

<span data-ttu-id="e2d23-124">NuGet Dll は、Win32 プロセスメモリに手動で読み込む必要があります。モジュールの startup メソッドに手動読み込みを追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e2d23-124">NuGet DLLs needs to load into your Win32 process memory manually; we recommend adding manual loading into the startup method of your module:</span></span>

```cpp
void StartupModule() override
{
#if PLATFORM_WINDOWS
    const FString LibrariesDir = FPaths::ProjectPluginsDir() / "MyModule" / THIRDPARTY_BINARY_SUBFOLDER;
    FPlatformProcess::PushDllDirectory(*LibrariesDir);

    const FString DllName = "Microsoft.MixedReality.QR.dll";
    if (!FPlatformProcess::GetDllHandle(*DllName))
    {
        UE_LOG(LogHMD, Warning, TEXT("Dll \'%s\' can't be loaded from \'%s\'"), *DllName, *LibrariesDir);
    }

    FPlatformProcess::PopDllDirectory(*LibrariesDir);
#endif
}
```

<span data-ttu-id="e2d23-125">最後に、前のセクションで説明したように、WinRT ヘッダーをコードに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="e2d23-125">Finally, you can include WinRT headers into your code as described in the previous section.</span></span>

# <a name="425"></a>[<span data-ttu-id="e2d23-126">4.25</span><span class="sxs-lookup"><span data-stu-id="e2d23-126">4.25</span></span>](#tab/425)

<span data-ttu-id="e2d23-127">Unreal はバージョン4.25 で WinRT コードをネイティブにコンパイルしないので、実際のビルドシステムが使用できない別のバイナリを構築するのは仕事です。</span><span class="sxs-lookup"><span data-stu-id="e2d23-127">Unreal doesn't natively compile WinRT code in version 4.25, so it's your job to build a separate binary that Unreal’s build system can consume.</span></span> 

## <a name="objectives"></a><span data-ttu-id="e2d23-128">目標</span><span class="sxs-lookup"><span data-stu-id="e2d23-128">Objectives</span></span>

- <span data-ttu-id="e2d23-129">FileSaveDialogue を開くユニバーサル Windows DLL を作成する</span><span class="sxs-lookup"><span data-stu-id="e2d23-129">Create a Universal Windows DLL that opens a FileSaveDialogue</span></span>
- <span data-ttu-id="e2d23-130">その DLL を Unreal game プロジェクトにリンクする</span><span class="sxs-lookup"><span data-stu-id="e2d23-130">Link that DLL to an Unreal game project</span></span>
- <span data-ttu-id="e2d23-131">新しい DLL を使用して、不要なブループリントから HoloLens にファイルを保存する</span><span class="sxs-lookup"><span data-stu-id="e2d23-131">Save a file on the HoloLens from an Unreal blueprint using the new DLL</span></span>

## <a name="getting-started"></a><span data-ttu-id="e2d23-132">作業の開始</span><span class="sxs-lookup"><span data-stu-id="e2d23-132">Getting started</span></span>

1. <span data-ttu-id="e2d23-133">すべての [必要なツール](../tutorials/unreal-uxt-ch1.md) がインストールされていることを確認する</span><span class="sxs-lookup"><span data-stu-id="e2d23-133">Check that you have all [required tools](../tutorials/unreal-uxt-ch1.md) installed</span></span>
2. <span data-ttu-id="e2d23-134">[新しい Unreal プロジェクトを作成](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project)し、 **Consumewinrt** という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="e2d23-134">[Create a new Unreal project](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) and name it **Consumewinrt**</span></span>
3. <span data-ttu-id="e2d23-135">HoloLens 開発に [必要なプラグイン](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) を有効にする</span><span class="sxs-lookup"><span data-stu-id="e2d23-135">Enable the [required plugins](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) for HoloLens development</span></span>
4. <span data-ttu-id="e2d23-136">デバイスまたはエミュレーターに[配置するためのセットアップ](../tutorials/unreal-uxt-ch6.md)</span><span class="sxs-lookup"><span data-stu-id="e2d23-136">[Setup for deployment](../tutorials/unreal-uxt-ch6.md) to a device or emulator</span></span>

## <a name="creating-a-winrt-dll"></a><span data-ttu-id="e2d23-137">WinRT DLL の作成</span><span class="sxs-lookup"><span data-stu-id="e2d23-137">Creating a WinRT DLL</span></span> 

1. <span data-ttu-id="e2d23-138">新しい Visual Studio プロジェクトを開き、Unreal game の **uproject** ファイルと同じディレクトリに **DLL (ユニバーサル Windows)** プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="e2d23-138">Open a new Visual Studio project and create a **DLL (Universal Windows)** project in the same directory as the Unreal game’s **uproject** file.</span></span> 

![DLL の作成](../images/unreal-winrt-img-01.png)

2. <span data-ttu-id="e2d23-140">プロジェクトに **HoloLensWinrtDLL** という名前を付け、その場所を **ThirdParty** サブディレクトリとして、unreal game の uproject ファイルに設定します。</span><span class="sxs-lookup"><span data-stu-id="e2d23-140">Name the project **HoloLensWinrtDLL** and set the location as a **ThirdParty** subdirectory to the Unreal game’s uproject file.</span></span> 
    * <span data-ttu-id="e2d23-141">後でパスを簡単に検索するには **、[ソリューションとプロジェクトを同じディレクトリに配置** する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e2d23-141">Select **Place solution and project in the same directory** to simplify looking for paths later.</span></span> 

![DLL の構成](../images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> <span data-ttu-id="e2d23-143">新しいプロジェクトがコンパイルされた後、空白の cpp ファイルとヘッダーファイルに特に注意してください。それぞれ **HoloLensWinrtDLL** と **HoloLensWinrtDLL** という名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="e2d23-143">After the new project compiles, pay special attention to the blank cpp and header files, named **HoloLensWinrtDLL.cpp** and **HoloLensWinrtDLL.h** respectively.</span></span> <span data-ttu-id="e2d23-144">ヘッダーは、Unreal の DLL を使用するインクルードファイルです。 cpp は、エクスポートした関数の本体を保持し、それ以外の場合はコンパイルできない WinRT コードを含みます。</span><span class="sxs-lookup"><span data-stu-id="e2d23-144">The header is the include file that uses the DLL in Unreal, while the cpp holds the body of any functions you export and includes any WinRT code that Unreal wouldn't otherwise be able to compile.</span></span> 

3. <span data-ttu-id="e2d23-145">コードを追加する前に、必要な WinRT コードをコンパイルできるように、プロジェクトのプロパティを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2d23-145">Before you add any code, you need to update the project properties to ensure the WinRT code you need can compile:</span></span> 
    * <span data-ttu-id="e2d23-146">HoloLensWinrtDLL プロジェクトを右クリックし、[**プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e2d23-146">Right-click on the HoloLensWinrtDLL project and select **properties**</span></span>  
    * <span data-ttu-id="e2d23-147">**構成** ドロップダウンを [**すべての構成**] に変更し、[**プラットフォーム**] ドロップダウンを [**すべてのプラットフォーム**] に変更します。</span><span class="sxs-lookup"><span data-stu-id="e2d23-147">Change the **Configuration** dropdown to **All Configurations** and the **Platform** dropdown to **All Platforms**</span></span>  
    * <span data-ttu-id="e2d23-148">[ **構成プロパティ] で> C/c + +> すべてのオプション**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e2d23-148">Under **Configuration Properties> C/C++> All Options**:</span></span>
        * <span data-ttu-id="e2d23-149">非同期タスクを待機できるように、 **await** を **追加のオプション** に追加します。</span><span class="sxs-lookup"><span data-stu-id="e2d23-149">Add **await** to **Additional Options** to ensure we can wait on async tasks</span></span>  
        * <span data-ttu-id="e2d23-150">**C++ 言語標準** を **ISO c++ 17 標準 (/std: C++ 17)** に変更して WinRT コードを含める</span><span class="sxs-lookup"><span data-stu-id="e2d23-150">Change **C++ Language Standard** to **ISO C++17 Standard (/std:c++17)** to include any WinRT code</span></span>

![プロジェクトプロパティのアップグレード](../images/unreal-winrt-img-03.png)

<span data-ttu-id="e2d23-152">プロジェクトは、ファイルダイアログを開き、ファイルを HoloLens ディスクに保存する WinRT コードを使用して、DLL のソースを更新する準備ができています。</span><span class="sxs-lookup"><span data-stu-id="e2d23-152">Your project is ready to update the DLL’s source with WinRT code that opens a file dialogue and saves a file to the HoloLens disk.</span></span>  

## <a name="adding-the-dll-code"></a><span data-ttu-id="e2d23-153">DLL コードの追加</span><span class="sxs-lookup"><span data-stu-id="e2d23-153">Adding the DLL code</span></span>

1. <span data-ttu-id="e2d23-154">**HoloLensWinrtDLL** を開き、dll のエクスポート関数を追加して、unreal に使用します。</span><span class="sxs-lookup"><span data-stu-id="e2d23-154">Open **HoloLensWinrtDLL.h** and add a dll exported function for Unreal to consume:</span></span> 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. <span data-ttu-id="e2d23-155">**HoloLensWinrtDLL** を開き、クラスで使用するすべてのヘッダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="e2d23-155">Open **HoloLensWinrtDLL.cpp** and add all headers the class will use:</span></span>  

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
> <span data-ttu-id="e2d23-156">すべての WinRT コードは **HoloLensWinrtDLL** に格納されているため、unreal はヘッダーを参照するときに winrt コードを含めようとしません。</span><span class="sxs-lookup"><span data-stu-id="e2d23-156">All WinRT code is stored in **HoloLensWinrtDLL.cpp** so Unreal doesn't try to include any WinRT code when referencing the header.</span></span> 

3. <span data-ttu-id="e2d23-157">**HoloLensWinrtDLL** の中で、OpenFileDialogue () およびサポートされているすべてのコードの関数本体を追加します。</span><span class="sxs-lookup"><span data-stu-id="e2d23-157">Still in **HoloLensWinrtDLL.cpp**, add a function body for OpenFileDialogue() and all supported code:</span></span> 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. <span data-ttu-id="e2d23-158">SaveGameManager クラスを **HoloLensWinrtDLL** に追加して、ファイルのダイアログを処理し、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="e2d23-158">Add a SaveGameManager class to **HoloLensWinrtDLL.cpp** to handle the file dialogue and saving the file:</span></span> 

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

5. <span data-ttu-id="e2d23-159">**Release > ARM64** のソリューションをビルドして、dll ソリューションから ARM64/Release/HoloLensWinrtDLL 子ディレクトリに dll をビルドします。</span><span class="sxs-lookup"><span data-stu-id="e2d23-159">Build the solution for **Release > ARM64** to build the DLL to the child directory ARM64/Release/HoloLensWinrtDLL from the DLL solution.</span></span> 

## <a name="adding-the-winrt-binary-to-unreal"></a><span data-ttu-id="e2d23-160">WinRT バイナリを Unreal に追加する</span><span class="sxs-lookup"><span data-stu-id="e2d23-160">Adding the WinRT binary to Unreal</span></span> 
<span data-ttu-id="e2d23-161">アン Real で DLL をリンクして使用するには、C++ プロジェクトが必要です。</span><span class="sxs-lookup"><span data-stu-id="e2d23-161">Linking and using a DLL in Unreal requires a C++ project.</span></span> <span data-ttu-id="e2d23-162">ブループリントプロジェクトを使用している場合は、C++ クラスを追加することで、C++ プロジェクトに簡単に変換できます。</span><span class="sxs-lookup"><span data-stu-id="e2d23-162">If you're using a Blueprint project, it can be easily converted to a C++ project by adding a C++ class:</span></span>  

1. <span data-ttu-id="e2d23-163">Unreal エディターで、[**ファイル > 新しい C++ クラス...** ] を開きます。</span><span class="sxs-lookup"><span data-stu-id="e2d23-163">In the Unreal editor, open **File > New C++ Class…**</span></span> <span data-ttu-id="e2d23-164">次に、 **Winrtactor** という名前の新しい **アクター** を作成し、DLL 内のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="e2d23-164">and create a new **Actor** named **WinrtActor** to run the code in the DLL:</span></span> 

![新しいアクターの作成](../images/unreal-winrt-img-04.png)

> [!NOTE]
> <span data-ttu-id="e2d23-166">Uproject ファイルと同じディレクトリに、Source/ConsumeWinRT/ConsumeWinRT という名前の新しいビルドスクリプトと共にソリューションが作成されました。</span><span class="sxs-lookup"><span data-stu-id="e2d23-166">A solution has now been created in the same directory as the uproject file along with a new build script named Source/ConsumeWinRT/ConsumeWinRT.Build.cs.</span></span>

2. <span data-ttu-id="e2d23-167">ソリューションを開き、 **game/ConsumeWinRT/Source/consumewinrt** フォルダーを参照し、 **ConsumeWinRT.build.cs** を開きます。</span><span class="sxs-lookup"><span data-stu-id="e2d23-167">Open the solution, browse for the **Games/ConsumeWinRT/Source/ConsumeWinRT** folder, and open **ConsumeWinRT.build.cs**:</span></span>

![ConsumeWinRT.build.cs ファイルを開く](../images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a><span data-ttu-id="e2d23-169">DLL のリンク</span><span class="sxs-lookup"><span data-stu-id="e2d23-169">Linking the DLL</span></span>
1. <span data-ttu-id="e2d23-170">**ConsumeWinRT.build.cs** で、プロパティを追加して、DLL のインクルードパス (HoloLensWinrtDLL を含むディレクトリ) を検索します。</span><span class="sxs-lookup"><span data-stu-id="e2d23-170">In **ConsumeWinRT.build.cs**, add a property to find the include path for the DLL (the directory containing HoloLensWinrtDLL.h).</span></span> <span data-ttu-id="e2d23-171">DLL は、インクルードパスの子ディレクトリにあるため、このプロパティはバイナリルートディレクトリとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="e2d23-171">The DLL is in a child directory to the include path, so this property will be used as the binary root dir:</span></span>

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

2. <span data-ttu-id="e2d23-172">クラスコンストラクターで、次のコードを追加してインクルードパスを更新し、新しい lib をリンクして、遅延読み込みを行い、DLL をパッケージ化された appx の場所にコピーします。</span><span class="sxs-lookup"><span data-stu-id="e2d23-172">In the class constructor, add the following code to update the include path, link the new lib, and delay-load and copy the DLL to the packaged appx location:</span></span>

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

3. <span data-ttu-id="e2d23-173">**Winrtactor** を開き、1つの関数定義を追加します。1つは、ブループリントによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e2d23-173">Open **WinrtActor.h** and add one function definition, one that a blueprint will call:</span></span> 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. <span data-ttu-id="e2d23-174">**Winrtactor** を開き、beginplay を更新して DLL を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="e2d23-174">Open **WinrtActor.cpp** and update BeginPlay to load the DLL:</span></span> 

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
> <span data-ttu-id="e2d23-175">DLL は、その関数のいずれかを呼び出す前に読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2d23-175">The DLL must be loaded before calling any of its functions.</span></span>

### <a name="building-the-game"></a><span data-ttu-id="e2d23-176">ゲームを構築する</span><span class="sxs-lookup"><span data-stu-id="e2d23-176">Building the game</span></span>
1. <span data-ttu-id="e2d23-177">ゲームソリューションをビルドして、game プロジェクトで開かれている Unreal エディターを起動します。</span><span class="sxs-lookup"><span data-stu-id="e2d23-177">Build the game solution to launch the Unreal editor opened to the game project:</span></span> 
    * <span data-ttu-id="e2d23-178">[ **アクターの配置** ] タブで、新しい **winrtactor** を検索し、シーンにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e2d23-178">In the **Place Actors** tab, search for the new **WinrtActor** and drag it into the scene</span></span> 
    * <span data-ttu-id="e2d23-179">レベルブループリントを開き、 **Winrtactor** でブループリント呼び出し可能関数を実行します。</span><span class="sxs-lookup"><span data-stu-id="e2d23-179">Open the level blueprint to execute the blueprint callable function in the **WinrtActor**</span></span> 

![WinrtActor をシーンに配置する](../images/unreal-winrt-img-06.png)

2. <span data-ttu-id="e2d23-181">**世界** 中では、前にシーンにドロップした **Windrtactor** を見つけて、レベルのブループリントにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="e2d23-181">In the **World Outliner**, find the **WindrtActor** previously dropped into the scene and drag it into the level blueprint:</span></span> 

![WinrtActor をレベルブループリントにドラッグする](../images/unreal-winrt-img-07.png)

3. <span data-ttu-id="e2d23-183">レベルブループリントで、[出力] ノードを WinrtActor からドラッグし、[ **ファイルを開く] ダイアログ** を検索して、任意のユーザー入力からノードをルーティングします。</span><span class="sxs-lookup"><span data-stu-id="e2d23-183">In the level blueprint, drag the output node from WinrtActor, search for **Open File Dialogue**, then route the node from any user input.</span></span>  <span data-ttu-id="e2d23-184">この場合、[ファイルを開く] ダイアログが音声イベントから呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e2d23-184">In this case, Open File Dialogue is being called from a speech event:</span></span> 

![レベルブループリントでのノードの構成](../images/unreal-winrt-img-08.png)

4. <span data-ttu-id="e2d23-186">[このゲームを HoloLens 用にパッケージ化](../tutorials/unreal-uxt-ch6.md)し、展開して、を実行します。</span><span class="sxs-lookup"><span data-stu-id="e2d23-186">[Package this game for HoloLens](../tutorials/unreal-uxt-ch6.md), deploy it, and run.</span></span>  

<span data-ttu-id="e2d23-187">Unreal が OpenFileDialogue を呼び出すと、ファイルのダイアログが表示され、HoloLens のファイル名を要求するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e2d23-187">When Unreal calls OpenFileDialogue, a File Dialogue opens on the HoloLens prompting for a .txt file name.</span></span>  <span data-ttu-id="e2d23-188">ファイルが保存されたら、デバイスポータルの [ **ファイルエクスプローラー** ] タブにアクセスして、"Hello WinRT" という内容を表示します。</span><span class="sxs-lookup"><span data-stu-id="e2d23-188">After the file is saved, go to the **File explorer** tab in the device portal to see the contents “Hello WinRT”.</span></span> 

## <a name="summary"></a><span data-ttu-id="e2d23-189">まとめ</span><span class="sxs-lookup"><span data-stu-id="e2d23-189">Summary</span></span> 

<span data-ttu-id="e2d23-190">このチュートリアルは、Windows と同じファイルダイアログを使用して HoloLens ディスクにファイルを保存する必要がある場合に、Unreal で WinRT コードを使用するための出発点として使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e2d23-190">We encourage you to use this tutorial as a starting point for consuming WinRT code in Unreal when you need to save files to the HoloLens disk using the same file dialogue as Windows.</span></span>  <span data-ttu-id="e2d23-191">このプロセスは、HoloLensWinrtDLL ヘッダーから追加の関数をエクスポートし、Unreal で使用する場合にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="e2d23-191">The same process applies to exporting additional functions from the HoloLensWinrtDLL header and used in Unreal.</span></span>  <span data-ttu-id="e2d23-192">バックグラウンド MTA スレッドで非同期 WinRT コードを待機する DLL コードに特に注意してください。これによって、Unreal game スレッドのデッドロックが回避されます。</span><span class="sxs-lookup"><span data-stu-id="e2d23-192">Pay special attention to the DLL code that waits on async WinRT code in a background MTA thread, which avoids deadlocking the Unreal game thread.</span></span> 

