---
title: Unreal での WinRT
description: Unreal Engine 用の空間オーディオ プラグインの概要。
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 07/08/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, ストリーミング, リモート処理, Mixed Reality, 開発, 入門, 機能, 新しいプロジェクト, エミュレーター, ドキュメント, ガイド, 特徴, ホログラム, ゲームの開発
ms.openlocfilehash: d7c94ebb7fc6cc16916f1f577b8e54e374b9db1f
ms.sourcegitcommit: e1de7caa7bd46afe9766186802fa4254d33d1ca6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/20/2020
ms.locfileid: "92240769"
---
# <a name="winrt-in-unreal"></a>Unreal での WinRT

## <a name="overview"></a>概要

HoloLens 開発の過程で、WinRT を使用して機能を作成することが必要になる場合があります。 たとえば、HoloLens アプリケーションでファイルのダイアログを開くには、FileSavePicker ヘッダーファイルに含まれている必要があります。  Unreal は WinRT コードをネイティブにコンパイルしないため、独立したバイナリをビルドし、Unreal のビルドシステムで使用できるようにすることができます。 このチュートリアルでは、このようなシナリオについて説明します。

## <a name="objectives"></a>目標
- FileSaveDialogue を開くユニバーサル Windows DLL を作成する
- その DLL を Unreal game プロジェクトにリンクする
- 新しい DLL を使用して、不要なブループリントから HoloLens にファイルを保存する

## <a name="getting-started"></a>作業の開始
1. すべての [必要なツール](tutorials/unreal-uxt-ch1.md) がインストールされていることを確認する
2. [新しい Unreal プロジェクトを作成](tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project)し、 **Consumewinrt**という名前を指定します。
3. HoloLens 開発に [必要なプラグイン](tutorials/unreal-uxt-ch2.md#enabling-required-plugins) を有効にする
4. デバイスまたはエミュレーターに[配置するためのセットアップ](tutorials/unreal-uxt-ch6.md)

## <a name="creating-a-winrt-dll"></a>WinRT DLL の作成 
1. 新しい Visual Studio プロジェクトを開き、Unreal game の**uproject**ファイルと同じディレクトリに**DLL (ユニバーサル Windows)** プロジェクトを作成します。 

![DLL の作成](images/unreal-winrt-img-01.png)

2. プロジェクトに **HoloLensWinrtDLL** という名前を付け、その場所を **ThirdParty** サブディレクトリとして、unreal game の uproject ファイルに設定します。 
    * 後でパスを簡単に検索するには **、[ソリューションとプロジェクトを同じディレクトリに配置** する] を選択します。 

![DLL の構成](images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> 新しいプロジェクトがコンパイルされた後、空白の cpp ファイルとヘッダーファイルに特に注意する必要があります。これには、それぞれ **HoloLensWinrtDLL** と **HoloLensWinrtDLL** という名前が付けられます。 ヘッダーは、Unreal の DLL を使用するインクルードファイルです。 cpp は、エクスポートした関数の本体を保持し、それ以外の場合はコンパイルできない WinRT コードを含みます。 

3. コードを追加する前に、必要な WinRT コードをコンパイルできるように、プロジェクトのプロパティを更新する必要があります。 
    * HoloLensWinrtDLL プロジェクトを右クリックし、[**プロパティ**] を選択します。  
    * **構成**ドロップダウンを [**すべての構成**] に変更し、[**プラットフォーム**] ドロップダウンを [**すべてのプラットフォーム**] に変更します。  
    * [ **構成プロパティ] で> C/c + +> すべてのオプション**] を選択します。
        * 非同期タスクを待機できるように、 **await** を **追加のオプション** に追加します。  
        * **C++ 言語標準**を**ISO c++ 17 標準 (/std: C++ 17)** に変更して WinRT コードを含める

![プロジェクトプロパティのアップグレード](images/unreal-winrt-img-03.png)

プロジェクトは、ファイルダイアログを開き、ファイルを HoloLens ディスクに保存する WinRT コードを使用して、DLL のソースを更新する準備ができています。  

## <a name="adding-the-dll-code"></a>DLL コードの追加
1. **HoloLensWinrtDLL**を開き、dll のエクスポート関数を追加して、unreal に使用します。 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. **HoloLensWinrtDLL**を開き、クラスで使用するすべてのヘッダーを追加します。  

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

3. **HoloLensWinrtDLL**の中で、OpenFileDialogue () およびサポートされているすべてのコードの関数本体を追加します。 

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

5. **Release > ARM64**のソリューションをビルドして、dll ソリューションから ARM64/Release/HoloLensWinrtDLL 子ディレクトリに dll をビルドします。 

## <a name="adding-the-winrt-binary-to-unreal"></a>WinRT バイナリを Unreal に追加する 
アン Real で DLL をリンクして使用するには、C++ プロジェクトが必要です。 ブループリントプロジェクトを使用している場合は、C++ クラスを追加することで、C++ プロジェクトに簡単に変換できます。  

1. Unreal エディターで、[**ファイル > 新しい C++ クラス...** ] を開きます。 次に、 **Winrtactor**という名前の新しい**アクター**を作成し、DLL 内のコードを実行します。 

![新しいアクターの作成](images/unreal-winrt-img-04.png)

> [!NOTE]
> Uproject ファイルと同じディレクトリに、Source/ConsumeWinRT/ConsumeWinRT という名前の新しいビルドスクリプトと共にソリューションが作成されました。

2. ソリューションを開き、 **game/ConsumeWinRT/Source/consumewinrt** フォルダーを参照し、 **ConsumeWinRT.build.cs**を開きます。

![ConsumeWinRT.build.cs ファイルを開く](images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a>DLL のリンク
1. **ConsumeWinRT.build.cs**で、プロパティを追加して、DLL のインクルードパス (HoloLensWinrtDLL を含むディレクトリ) を検索します。 DLL は、インクルードパスの子ディレクトリにあるため、このプロパティはバイナリルートディレクトリとして使用されます。

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

3. **Winrtactor**を開き、2つの関数定義を追加します。1つはブループリントで使用でき、もう1つは DLL コードを使用します。 
```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue;
```

4. **Winrtactor**を開き、DLL を beginplay に読み込みます。 

```cpp
void AWinfrtActor::BeginPlay()
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
    * レベルブループリントを開き、 **Winrtactor**でブループリント呼び出し可能関数を実行します。 

![WinrtActor をシーンに配置する](images/unreal-winrt-img-06.png)

2. **世界**中では、前にシーンにドロップした**Windrtactor**を見つけて、レベルのブループリントにドラッグします。 

![WinrtActor をレベルブループリントにドラッグする](images/unreal-winrt-img-07.png)

3. レベルブループリントで、[出力] ノードを WinrtActor からドラッグし、[ **ファイルを開く] ダイアログ**を検索して、任意のユーザー入力からノードをルーティングします。  この場合、[ファイルを開く] ダイアログが音声イベントから呼び出されます。 

![レベルブループリントでのノードの構成](images/unreal-winrt-img-08.png)

4. [このゲームを HoloLens 用にパッケージ化](tutorials/unreal-uxt-ch6.md)し、展開して、を実行します。  

Unreal が OpenFileDialogue を呼び出すと、ファイルのダイアログが表示され、HoloLens のファイル名を要求するメッセージが表示されます。  ファイルが保存されたら、デバイスポータルの [ **ファイルエクスプローラー** ] タブにアクセスして、"Hello WinRT" という内容を表示します。 

## <a name="summary"></a>まとめ 

このチュートリアルのコードは、Unreal で WinRT コードを使用するための出発点として使用することをお勧めします。  Windows と同じファイルを使用して、ユーザーが HoloLens ディスクにファイルを保存できるようにします。  同じプロセスに従って、HoloLensWinrtDLL ヘッダーから他の関数をエクスポートし、Unreal で使用します。  バックグラウンド MTA スレッドで非同期 WinRT コードを待機する DLL コードに注意してください。これにより、Unreal game スレッドのデッドロックが回避されます。 

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

私たちが用意した Unreal 開発チェックポイント体験に従っている場合、読者は Mixed Reality プラットフォームの機能と API を探索している段階にいます。 ここから、任意の [トピック](unreal-development-overview.md#3-platform-capabilities-and-apis) に進み、デバイスまたはエミュレーターへのアプリのデプロイに直接進むことができます。

> [!div class="nextstepaction"]
> [デバイスへの配置](unreal-deploying.md)

## <a name="see-also"></a>関連項目
* [C++/WinRT Api](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [FileSavePicker クラス](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [Unreal サードパーティ製ライブラリ](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
