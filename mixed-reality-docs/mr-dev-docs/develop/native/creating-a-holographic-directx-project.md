---
title: ホログラフィック DirectX プロジェクトを作成する
description: Windows Mixed Reality アプリテンプレートに基づいて新しい holographic アプリを作成する方法について説明します。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, holographic アプリ, 新しいアプリ, UWP アプリ, テンプレートアプリ, ホログラム, 新しいプロジェクト, チュートリアル, ダウンロード, サンプルコード, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: 08adbf6a4148e0e1d3b808d993011a7407fbf086
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678131"
---
# <a name="creating-a-holographic-directx-project"></a>ホログラフィック DirectX プロジェクトを作成する

> [!NOTE]
> この記事は、従来の WinRT ネイティブ Api に関連しています。  新しいネイティブアプリプロジェクトの場合は、 **[OPENXR API](openxr-getting-started.md)** を使用することをお勧めします。

HoloLens 用に作成した holographic アプリは、 <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">ユニバーサル Windows プラットフォーム (UWP) アプリ</a>になります。  デスクトップ Windows Mixed Reality ヘッドセットを対象とする場合は、UWP アプリまたは Win32 アプリを作成できます。

DirectX 11 holographic UWP アプリテンプレートは DirectX 11 UWP アプリテンプレートとよく似ています。これには、プログラムループ (または "ゲームループ")、Direct3D デバイスとコンテキストを管理するための **DeviceResources** クラス、および簡略化されたコンテンツレンダラークラスが含まれます。 他の UWP アプリと同じように、 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>もあります。

ただし、mixed reality アプリには、一般的な Direct3D UWP アプリには存在しないいくつかの追加機能があります。 Windows Mixed Reality アプリテンプレートでは、次のことができます。
* Holographic カメラに関連付けられている Direct3D デバイスリソースを処理します。
* システムからカメラのバックバッファーを取得します。または (Direct3D12 の場合)、holographic バックバッファーリソースを作成し、リソースの有効期間を管理します。
* [見つめ](../../design/gaze-and-commit.md)入力を処理し、簡単な[ジェスチャ](../../design/gaze-and-commit.md#composite-gestures)を認識します。
* 全画面表示のステレオレンダリングモードに切り替えます。

## <a name="how-do-i-get-started"></a>開始するには?

まず、Visual Studio 2019 および Windows Mixed Reality アプリテンプレートのダウンロードに関する説明に従って、 [ツールをインストール](../install-the-tools.md)します。 混合 reality アプリテンプレートは、Visual Studio marketplace の [web ダウンロード](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)として、または VISUAL studio UI を使用して拡張機能としてインストールすることによって入手できます。

これで、DirectX 11 Windows Mixed Reality アプリを作成する準備ができました。 サンプルコンテンツを削除するには、 *pch* の **DRAW_SAMPLE_CONTENT** プリプロセッサディレクティブをコメントアウトします。

## <a name="creating-a-uwp-project"></a>UWP プロジェクトの作成

[ツールがインストールさ](../install-the-tools.md)れたら、HOLOGRAPHIC DirectX UWP プロジェクトを作成できます。

Visual Studio 2019 で新しいプロジェクトを作成するには:
1. **Visual Studio** を起動します。
2. 右側の [ **はじめ** に] セクションで、[ **新しいプロジェクトの作成**] を選択します。
3. [ **新しいプロジェクトの作成** ] ダイアログボックスのドロップダウンメニューで、[ **C++**]、[ **Windows Mixed Reality**]、[ **UWP**] の順に選択します。
4. **Holographic DirectX 11 アプリ (ユニバーサル Windows) (C++/WinRT)** を選択します。
   ![Visual Studio 2019 の Holographic DirectX 11 C++/WinRT UWP アプリプロジェクトテンプレートのスクリーンショット](images/holographic-directx-app-cpp-new-project-2019.png)<br>
   *Visual Studio 2019 の Holographic DirectX 11 C++/WinRT UWP アプリプロジェクトテンプレート*
   >[!IMPORTANT]
   >プロジェクトテンプレートの名前に "(C++/WinRT)" が含まれていることを確認してください。  それ以外の場合は、古いバージョンの holographic プロジェクトテンプレートがインストールされています。  最新のプロジェクトテンプレートを入手するには、Visual Studio 2019 の拡張機能として [インストール](../install-the-tools.md) します。
5. **[次へ]** をクリックします。
5. [ **プロジェクト名** ] と [ **場所** ] のテキストボックスに入力し、[ **作成**] をクリックまたはタップします。 Holographic app プロジェクトが作成されます。
6. HoloLens 2 のみを対象とする開発では、 **ターゲットバージョン** と **最小バージョン** が **Windows 10 バージョン 1903** に設定されていることを確認します。  HoloLens (第1世代) またはデスクトップ Windows Mixed Reality ヘッドセットも対象としている場合は、代わりに、 **最小バージョン** を **Windows 10 バージョン 1809** に設定できます。ただし、hololens 2 の新機能を使用する場合は、コードに <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">バージョンのアダプティブチェック</a> が必要になります。
   ![ターゲットバージョンと最小バージョンとして Windows 10 バージョン1903を設定するスクリーンショット](images/new-uwp-project.png)<br>
   *ターゲットバージョンと最小バージョンとして **Windows 10 バージョン1903を** 設定する*
   >[!IMPORTANT]
   >オプションとして **windows 10 バージョン 1903** が表示されない場合は、最新の WINDOWS 10 SDK がインストールされていません。  このオプションを表示するに <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">は、Windows 10 SDK のバージョン10.0.18362.0 以降をインストール</a>します。

Visual Studio 2017 で新しいプロジェクトを作成するには:
1. **Visual Studio** を起動します。
2. [ **ファイル** ] メニューの [ **新規作成** ] をポイントし、コンテキストメニューの [ **プロジェクト** ] をクリックします。 **[新しいプロジェクト]** ダイアログ ボックスが開きます。
3. 左側の [ **インストール済み** ] を展開し、[ **Visual C++** 言語] ノードを展開します。
4. [ **Windows Universal > Holographic** ] ノードに移動し、[ **Holographic DirectX 11 App (ユニバーサル Windows) (C++/WinRT)**] を選択します。
   ![Visual Studio 2017 の Holographic DirectX 11 C++/WinRT UWP アプリプロジェクトテンプレートのスクリーンショット](images/holographic-directx-app-cpp-new-project.png)<br>
   *Visual Studio 2017 の Holographic DirectX 11 C++/WinRT UWP アプリプロジェクトテンプレート*
   >[!IMPORTANT]
   >プロジェクトテンプレートの名前に "(C++/WinRT)" が含まれていることを確認してください。  それ以外の場合は、古いバージョンの holographic プロジェクトテンプレートがインストールされています。  最新のプロジェクトテンプレートを入手するには、Visual Studio 2017 の拡張機能として [インストール](../install-the-tools.md) します。
5. [ **名前** ] と [ **場所** ] のテキストボックスに入力し、[ **OK**] をクリックまたはタップします。 Holographic app プロジェクトが作成されます。
6. HoloLens 2 のみを対象とする開発では、 **ターゲットバージョン** と **最小バージョン** が **Windows 10 バージョン 1903** に設定されていることを確認します。  HoloLens (第1世代) またはデスクトップ Windows Mixed Reality ヘッドセットも対象としている場合は、代わりに、 **最小バージョン** を **Windows 10 バージョン 1809** に設定できます。ただし、hololens 2 の新機能を使用する場合は、コードに <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">バージョンのアダプティブチェック</a> が必要になります。
   ![ターゲットバージョンと最小バージョンとして Windows 10 バージョン1903を設定するスクリーンショット](images/new-uwp-project.png)<br>
   *ターゲットバージョンと最小バージョンとして **Windows 10 バージョン1903を** 設定する*
   >[!IMPORTANT]
   >オプションとして **windows 10 バージョン 1903** が表示されない場合は、最新の WINDOWS 10 SDK がインストールされていません。  このオプションを表示するに <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">は、Windows 10 SDK のバージョン10.0.18362.0 以降をインストール</a>します。

このテンプレートは、c++ <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">/WinRT</a>を使用してプロジェクトを生成します。これは、標準に準拠している c++ 17 コンパイラをサポートする Windows ランタイム Api の c++ 17 言語の射影です。  このプロジェクトは、ユーザーから2メートル離れたワールドロックキューブを作成する方法を示しています。 ユーザーは、コントローラー上のボタンを使用して、ユーザーの[宝石](../../design/gaze-and-commit.md)によって指定された別の位置にキューブを[配置できます](../../design/gaze-and-commit.md#composite-gestures)。 このプロジェクトを変更して、mixed reality アプリを作成できます。

または、SharpDX に基づく **Visual C#** holographic プロジェクトテンプレートを使用して、新しいプロジェクトを作成することもできます。  Holographic C# プロジェクトが Windows Holographic アプリテンプレートから開始されなかった場合は、プロジェクトに追加した HLSL ファイルをコンパイルするために、Windows Mixed Reality C# テンプレートプロジェクトからファイルをコピーし、.csproj ファイルにインポートする必要があります。 Direct3D 12 テンプレートは、Visual Studio の Windows Mixed Reality アプリテンプレート拡張機能にも用意されています。

[「Visual Studio を使用してデプロイとデバッグ](../platform-capabilities-and-apis/using-visual-studio.md)を行う」で、HoloLens、PC にデバイスが接続されている PC、またはエミュレーターにサンプルを構築してデプロイする方法について確認します。

次の手順の残りの部分では、C++ を使用してアプリをビルドしていることを前提としています。

### <a name="uwp-app-entry-point"></a>UWP アプリのエントリポイント

Holographic UWP アプリは、AppView .cpp の **Wwinmain** 関数で開始されます。 **Wwinmain** 関数は、アプリの <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>を作成し、それを使用して <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a>を開始します。

**Appview .cpp** から:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

この時点から、AppView クラスは、Windows 基本入力イベント、CoreWindow イベントとメッセージングなどとの対話を処理します。 また、アプリで使用される HolographicSpace も作成されます。

## <a name="creating-a-win32-project"></a>Win32 プロジェクトの作成

Win32 holographic プロジェクトの構築を開始する最も簡単な方法は、 <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *basichologram* win32 サンプル</a>を調整することです。

この Win32 サンプルでは、標準に準拠している C++ 17 コンパイラをサポートする Windows ランタイム Api の C++ 17language プロジェクションである <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">c++/WinRT</a>を使用します。  このプロジェクトは、ユーザーから2メートル離れたワールドロックキューブを作成する方法を示しています。 ユーザーは、コントローラー上のボタンをクリックして、ユーザーの [宝石](../../design/gaze-and-commit.md)によって指定された別の位置にキューブを配置できます。 このプロジェクトを変更して、mixed reality アプリを作成できます。

### <a name="win32-app-entry-point"></a>Win32 アプリのエントリポイント

Holographic Win32 アプリは、AppMain の **Wwinmain** 関数で開始されます。 **Wwinmain** 関数は、アプリの HWND を作成し、そのメッセージループを開始します。

**Appmain .cpp** から:

```cpp
int APIENTRY wWinMain(
    _In_     HINSTANCE hInstance,
    _In_opt_ HINSTANCE hPrevInstance,
    _In_     LPWSTR    lpCmdLine,
    _In_     int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    winrt::init_apartment();

    App app;

    // Initialize global strings, and perform application initialization.
    app.Initialize(hInstance);

    // Create the HWND and the HolographicSpace.
    app.CreateWindowAndHolographicSpace(hInstance, nCmdShow);

    // Main message loop:
    app.Run(hInstance);

    // Perform application teardown.
    app.Uninitialize();

    return 0;
}
```

この時点から、AppMain クラスは基本的なウィンドウメッセージとの対話を処理します。 また、アプリで使用される HolographicSpace も作成されます。

## <a name="render-holographic-content"></a>Holographic コンテンツのレンダリング

プロジェクトの **コンテンツ** フォルダーには、 [holographic 空間](getting-a-holographicspace.md)にホログラムをレンダリングするためのクラスが含まれています。 テンプレートの既定のホログラムは、ユーザーから2メートル離れた位置にある回転する立方体です。 このキューブの描画は、次の主要なメソッドを含む SpinningCubeRenderer に実装されてい **ます**。

|  メソッド  |  説明 | 
|----------|----------|
|  `CreateDeviceDependentResources` |  シェーダーを読み込み、キューブメッシュを作成します。 | 
|  `PositionHologram` |  指定した <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>によって指定された場所にホログラムを配置します。 | 
|  `Update` |  キューブを回転させ、モデルマトリックスを設定します。 | 
|  `Render` |  頂点シェーダーとピクセルシェーダーを使用してフレームをレンダリングします。 | 

**シェーダー** サブフォルダーには、4つの既定のシェーダー実装が含まれています。

|  シェーダー  |  説明 | 
|----------|----------|
|  `GeometryShader.hlsl` |  ジオメトリを変更せずに残すパススルー。 | 
|  `PixelShader.hlsl` |  カラーデータを通過します。 色データが補間され、ラスタライズの手順でピクセルに割り当てられます。 | 
|  `VertexShader.hlsl` |  GPU で頂点処理を行うための単純なシェーダー。 | 
|  `VPRTVertexShader.hlsl` |  Windows Mixed Reality ステレオレンダリング用に最適化された、GPU で頂点処理を行うための単純なシェーダー。 | 

`VertexShaderShared.hlsl` との間で共有される共通のコード `VertexShader.hlsl` を格納 `VPRTVertexShader.hlsl` します。

注: Direct3D 12 アプリケーションテンプレートにもが含まれてい `ViewInstancingVertexShader.hlsl` ます。 このバリアントでは、D3D12 のオプション機能を使用して、ステレオ画像をより効率的にレンダリングします。

シェーダーは、プロジェクトのビルド時にコンパイルされ、 **SpinningCubeRenderer:: CreateDeviceDependentResources** メソッドに読み込まれます。

## <a name="interact-with-your-holograms"></a>ホログラムを操作する

ユーザー入力は **SpatialInputHandler** クラスで処理されます。このクラスは <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> インスタンスを取得し、 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">sourcepressed</a> イベントをサブスクライブします。 これにより、エアタップジェスチャとその他の空間入力イベントを検出できるようになります。

## <a name="update-holographic-content"></a>Holographic コンテンツの更新

混合 reality アプリの更新は、既定ではの **Update** メソッドに実装されているゲームループで更新され `AppMain.cpp` ます。 **Update** メソッドは、回転するキューブなどのシーンオブジェクトを更新し、最新のビューおよび射影マトリックスを取得して、スワップチェーンを表示するために使用される <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>オブジェクトを返します。

の **Render** メソッドは、 `AppMain.cpp` 現在のアプリと空間ポジショニングの状態に従って、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> を受け取り、現在のフレームを各 holographic カメラにレンダリングします。

## <a name="notes"></a>メモ

Windows Mixed Reality アプリケーションテンプレートで、Spectre 軽減フラグが有効になっているコンパイル (/Qspectre) がサポートされるようになりました。 Spectre 軽減策が有効になっている構成をコンパイルする前に、Microsoft Visual C++ Spectre (MSVC) ランタイムライブラリを必ずインストールしてください。 Spectre の緩和された C++ ライブラリをインストールするには、Visual Studio インストーラーを起動し、[ **変更**] を選択します。 個々の **コンポーネント** に移動し、"spectre" を検索します。 Spectre コードをコンパイルするために必要なターゲットプラットフォームと MSVC のバージョンに対応するボックスを選択し、[ **変更** ] をクリックしてインストールを開始します。

## <a name="see-also"></a>関連項目
* [HolographicSpace を入手する](getting-a-holographicspace.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [DirectX でのレンダリング](rendering-in-directx.md)
* [Visual Studio を使用してデプロイおよびデバッグする](../platform-capabilities-and-apis/using-visual-studio.md)
* [HoloLens エミュレーターを使用する](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [XAML とホログラフィック DirectX アプリの使用](../platform-capabilities-and-apis/using-xaml-with-holographic-directx-apps.md)
