---
ms.openlocfilehash: cc29a6e9d358ba35d1e1ddd336b9df88ba68739b
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/21/2021
ms.locfileid: "98690018"
---
# <a name="426"></a>[4.26](#tab/426)

## <a name="the-standard-winrt-apis"></a>標準の WinRT Api

WinRT を使用する最も一般的で簡単な方法は、WinSDK からメソッドを呼び出すことです。 これを行うには、YourModule.Build.cs ファイルを開き、次の行を追加します。

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

次に、次の WinRT ヘッダーを追加する必要があります。 

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

WinRT コードは、Win64 および HoloLens プラットフォームでのみコンパイルできるため、if ステートメントを使用すると、WinRT ライブラリが他のプラットフォームに含まれないようにすることができます。 IUnknown インターフェイスを持つために unknwn が追加されました。 


## <a name="winrt-from-a-nuget-package"></a>NuGet パッケージからの WinRT

WinRT サポートを含む NuGet パッケージを追加する必要がある場合は、少し複雑になります。 この場合、Visual Studio は実質的にすべてのジョブを実行できますが、Unreal ビルドシステムでは実行できません。 さいわい、それほど難しくはありません。 MixedReality パッケージをダウンロードする方法の例を次に示します。 別のファイルに置き換えることができます。 winmd ファイルが失われていないことを確認し、正しい dll をコピーするだけです。 

前のセクションの Windows SDK dll は、OS によって処理されます。 NuGet の dll は、モジュール内のコードによって管理されている必要があります。 モジュールをダウンロードし、バイナリフォルダーにコピーして、モジュールの起動時にプロセスメモリに読み込むコードを追加することをお勧めします。

最初の手順では、 https://docs.microsoft.com/nuget/reference/packages-config) モジュールのルートフォルダーに packages.config を追加する必要があります。 ここでは、すべての依存関係を含め、ダウンロードするすべてのパッケージを追加する必要があります。 ここで、プライマリペイロードとして MixedReality を追加し、他の2つを依存関係として追加しました。 このファイルの形式は、Visual Studio の場合と同じです。

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.MixedReality.QR" version="0.5.2102" targetFramework="native" />
  <package id="Microsoft.VCRTForwarders.140" version="1.0.6" targetFramework="native" />
  <package id="Microsoft.Windows.CppWinRT" version="2.0.200729.8" targetFramework="native" />
</packages>
```

これで、NuGet や必要なパッケージをダウンロードしたり、NuGet の [ドキュメント](/nuget/consume-packages/install-use-packages-nuget-cli)を参照したりできるようになりました。

YourModule.Build.cs を開き、次のコードを追加します。

```csharp
// WinRT with Nuget support
if (Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    // these parameters mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.AddRange(new string [] { "shlwapi.lib", "runtimeobject.lib" });

    // prepare everything for nuget
    string MyModuleName = GetType().Name;
    string NugetFolder = Path.Combine(PluginDirectory, "Intermediate", "Nuget", MyModuleName);
    Directory.CreateDirectory(NugetFolder);

    string BinariesSubFolder = Path.Combine("Binaries", "ThirdParty", Target.Type.ToString(), Target.Platform.ToString(), Target.Architecture);

    PrivateDefinitions.Add(string.Format("THIRDPARTY_BINARY_SUBFOLDER=\"{0}\"", BinariesSubFolder.Replace(@"\", @"\\")));

    string BinariesFolder = Path.Combine(PluginDirectory, BinariesSubFolder);
    Directory.CreateDirectory(BinariesFolder);

    ExternalDependencies.Add("packages.config");

    // download nuget
    string NugetExe = Path.Combine(NugetFolder, "nuget.exe");
    if (!File.Exists(NugetExe))
    {
        using (System.Net.WebClient myWebClient = new System.Net.WebClient())
        {
            // we aren't focusing on a specific nuget version, we can use any of them but the latest one is preferable
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

    // get list of the installed packages, that's needed because the code should get particular versions of the installed packages
    string[] InstalledPackages = Utils.RunLocalProcessAndReturnStdOut(NugetExe, string.Format("list -Source \"{0}\"", NugetFolder)).Split(new char[] { '\r', '\n' });

    // winmd files of the packages
    List<string> WinMDFiles = new List<string>();

    // WinRT lib for some job
    string QRPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.MixedReality.QR"));
    if (!string.IsNullOrEmpty(QRPackage))
    {
        string QRFolderName = QRPackage.Replace(" ", ".");

        // copying dll and winmd binaries to our local binaries folder
        // !!!!! please make sure that you use the path of file! Unreal can't do it for you !!!!!
        string WinMDFile = Path.Combine(NugetFolder, QRFolderName, @"lib\uap10.0.18362\Microsoft.MixedReality.QR.winmd");
        SafeCopy(WinMDFile, Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        SafeCopy(Path.Combine(NugetFolder, QRFolderName, string.Format(@"runtimes\win10-{0}\native\Microsoft.MixedReality.QR.dll", Target.WindowsPlatform.Architecture.ToString())),
            Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));

        // also both both binaries must be in RuntimeDependencies, unless you get failures in Hololens platform
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        //add winmd file to the list for further processing using cppwinrt.exe
        WinMDFiles.Add(WinMDFile);
    }

    if (Target.Platform == UnrealTargetPlatform.Win64)
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

    // get WinRT package 
    string CppWinRTPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.Windows.CppWinRT"));
    if (!string.IsNullOrEmpty(CppWinRTPackage))
    {
        string CppWinRTName = CppWinRTPackage.Replace(" ", ".");
        string CppWinRTExe = Path.Combine(NugetFolder, CppWinRTName, "bin", "cppwinrt.exe");
        string CppWinRTFolder = Path.Combine(PluginDirectory, "Intermediate", CppWinRTName, MyModuleName);
        Directory.CreateDirectory(CppWinRTFolder);

        // all downloaded winmd file with WinSDK to be processed by cppwinrt.exe
        var WinMDFilesStringbuilder = new System.Text.StringBuilder();
        foreach (var winmd in WinMDFiles)
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
        // fall back to default WinSDK headers if no winrt package in our list
        PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir, "Include", Target.WindowsPlatform.WindowsSdkVersion, "cppwinrt"));
    }
}
```

SafeCopy メソッドは次のように定義する必要があります。

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

NuGet Dll は、Win32 プロセスメモリに手動で読み込む必要があります。モジュールの startup メソッドに手動読み込みを追加することをお勧めします。

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

最後に、前のセクションで説明したように、WinRT ヘッダーをコードに含めることができます。

# <a name="425"></a>[4.25](#tab/425)

Unreal はバージョン4.25 で WinRT コードをネイティブにコンパイルしないので、実際のビルドシステムが使用できない別のバイナリを構築するのは仕事です。 

## <a name="objectives"></a>目標

- FileSaveDialogue を開くユニバーサル Windows DLL を作成する
- その DLL を Unreal game プロジェクトにリンクする
- 新しい DLL を使用して、不要なブループリントから HoloLens にファイルを保存する

## <a name="getting-started"></a>作業の開始

1. すべての [必要なツール](../tutorials/unreal-uxt-ch1.md) がインストールされていることを確認する
2. [新しい Unreal プロジェクトを作成](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project)し、 **Consumewinrt** という名前を指定します。
3. HoloLens 開発に [必要なプラグイン](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) を有効にする
4. デバイスまたはエミュレーターに[配置するためのセットアップ](../tutorials/unreal-uxt-ch6.md)

## <a name="creating-a-winrt-dll"></a>WinRT DLL の作成 

1. 新しい Visual Studio プロジェクトを開き、Unreal game の **uproject** ファイルと同じディレクトリに **DLL (ユニバーサル Windows)** プロジェクトを作成します。 

![DLL の作成](../images/unreal-winrt-img-01.png)

2. プロジェクトに **HoloLensWinrtDLL** という名前を付け、その場所を **ThirdParty** サブディレクトリとして、unreal game の uproject ファイルに設定します。 
    * 後でパスを簡単に検索するには **、[ソリューションとプロジェクトを同じディレクトリに配置** する] を選択します。 

![DLL の構成](../images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> 新しいプロジェクトがコンパイルされた後、空白の cpp ファイルとヘッダーファイルに特に注意してください。それぞれ **HoloLensWinrtDLL** と **HoloLensWinrtDLL** という名前が付けられています。 ヘッダーは、Unreal の DLL を使用するインクルードファイルです。 cpp は、エクスポートした関数の本体を保持し、それ以外の場合はコンパイルできない WinRT コードを含みます。 

3. コードを追加する前に、必要な WinRT コードをコンパイルできるように、プロジェクトのプロパティを更新する必要があります。 
    * HoloLensWinrtDLL プロジェクトを右クリックし、[**プロパティ**] を選択します。  
    * **構成** ドロップダウンを [**すべての構成**] に変更し、[**プラットフォーム**] ドロップダウンを [**すべてのプラットフォーム**] に変更します。  
    * [ **構成プロパティ] で> C/c + +> すべてのオプション**] を選択します。
        * 非同期タスクを待機できるように、 **await** を **追加のオプション** に追加します。  
        * **C++ 言語標準** を **ISO c++ 17 標準 (/std: C++ 17)** に変更して WinRT コードを含める

![プロジェクトプロパティのアップグレード](../images/unreal-winrt-img-03.png)

プロジェクトは、ファイルダイアログを開き、ファイルを HoloLens ディスクに保存する WinRT コードを使用して、DLL のソースを更新する準備ができています。  

## <a name="adding-the-dll-code"></a>DLL コードの追加

1. **HoloLensWinrtDLL** を開き、dll のエクスポート関数を追加して、unreal に使用します。 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. **HoloLensWinrtDLL** を開き、クラスで使用するすべてのヘッダーを追加します。  

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
> すべての WinRT コードは **HoloLensWinrtDLL** に格納されているため、unreal はヘッダーを参照するときに winrt コードを含めようとしません。 

3. **HoloLensWinrtDLL** の中で、OpenFileDialogue () およびサポートされているすべてのコードの関数本体を追加します。 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. SaveGameManager クラスを **HoloLensWinrtDLL** に追加して、ファイルのダイアログを処理し、ファイルを保存します。 

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

5. **Release > ARM64** のソリューションをビルドして、dll ソリューションから ARM64/Release/HoloLensWinrtDLL 子ディレクトリに dll をビルドします。 

## <a name="adding-the-winrt-binary-to-unreal"></a>WinRT バイナリを Unreal に追加する 
アン Real で DLL をリンクして使用するには、C++ プロジェクトが必要です。 ブループリントプロジェクトを使用している場合は、C++ クラスを追加することで、C++ プロジェクトに簡単に変換できます。  

1. Unreal エディターで、[**ファイル > 新しい C++ クラス...** ] を開きます。 次に、 **Winrtactor** という名前の新しい **アクター** を作成し、DLL 内のコードを実行します。 

![新しいアクターの作成](../images/unreal-winrt-img-04.png)

> [!NOTE]
> Uproject ファイルと同じディレクトリに、Source/ConsumeWinRT/ConsumeWinRT という名前の新しいビルドスクリプトと共にソリューションが作成されました。

2. ソリューションを開き、 **game/ConsumeWinRT/Source/consumewinrt** フォルダーを参照し、 **ConsumeWinRT.build.cs** を開きます。

![ConsumeWinRT.build.cs ファイルを開く](../images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a>DLL のリンク
1. **ConsumeWinRT.build.cs** で、プロパティを追加して、DLL のインクルードパス (HoloLensWinrtDLL を含むディレクトリ) を検索します。 DLL は、インクルードパスの子ディレクトリにあるため、このプロパティはバイナリルートディレクトリとして使用されます。

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

2. クラスコンストラクターで、次のコードを追加してインクルードパスを更新し、新しい lib をリンクして、遅延読み込みを行い、DLL をパッケージ化された appx の場所にコピーします。

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

3. **Winrtactor** を開き、1つの関数定義を追加します。1つは、ブループリントによって呼び出されます。 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. **Winrtactor** を開き、beginplay を更新して DLL を読み込みます。 

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
> DLL は、その関数のいずれかを呼び出す前に読み込む必要があります。

### <a name="building-the-game"></a>ゲームを構築する
1. ゲームソリューションをビルドして、game プロジェクトで開かれている Unreal エディターを起動します。 
    * [ **アクターの配置** ] タブで、新しい **winrtactor** を検索し、シーンにドラッグします。 
    * レベルブループリントを開き、 **Winrtactor** でブループリント呼び出し可能関数を実行します。 

![WinrtActor をシーンに配置する](../images/unreal-winrt-img-06.png)

2. **世界** 中では、前にシーンにドロップした **Windrtactor** を見つけて、レベルのブループリントにドラッグします。 

![WinrtActor をレベルブループリントにドラッグする](../images/unreal-winrt-img-07.png)

3. レベルブループリントで、[出力] ノードを WinrtActor からドラッグし、[ **ファイルを開く] ダイアログ** を検索して、任意のユーザー入力からノードをルーティングします。  この場合、[ファイルを開く] ダイアログが音声イベントから呼び出されます。 

![レベルブループリントでのノードの構成](../images/unreal-winrt-img-08.png)

4. [このゲームを HoloLens 用にパッケージ化](../tutorials/unreal-uxt-ch6.md)し、展開して、を実行します。  

Unreal が OpenFileDialogue を呼び出すと、ファイルのダイアログが表示され、HoloLens のファイル名を要求するメッセージが表示されます。  ファイルが保存されたら、デバイスポータルの [ **ファイルエクスプローラー** ] タブにアクセスして、"Hello WinRT" という内容を表示します。 

## <a name="summary"></a>まとめ 

このチュートリアルは、Windows と同じファイルダイアログを使用して HoloLens ディスクにファイルを保存する必要がある場合に、Unreal で WinRT コードを使用するための出発点として使用することをお勧めします。  このプロセスは、HoloLensWinrtDLL ヘッダーから追加の関数をエクスポートし、Unreal で使用する場合にも適用されます。  バックグラウンド MTA スレッドで非同期 WinRT コードを待機する DLL コードに特に注意してください。これによって、Unreal game スレッドのデッドロックが回避されます。