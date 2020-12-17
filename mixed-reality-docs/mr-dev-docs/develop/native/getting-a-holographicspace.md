---
title: HolographicSpace を入手する
description: HolographicSpace API について説明します。これは、holographic レンダリングと空間入力の中核となる概念です。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality、HolographicSpace、CoreWindow、空間入力、レンダリング、スワップチェーン、holographic frame、update loop、game loop、reference of reference、locatability、sample code、チュートリアル、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual Reality ヘッドセット
ms.openlocfilehash: 3b0e31b8d3bf0d7741e7976edd2069db68ea5121
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613016"
---
# <a name="getting-a-holographicspace"></a>HolographicSpace を入手する

> [!NOTE]
> この記事は、従来の WinRT ネイティブ Api に関連しています。  新しいネイティブアプリプロジェクトの場合は、 **[OPENXR API](openxr-getting-started.md)** を使用することをお勧めします。

<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>クラスは、holographic 世界のポータルです。 これは、イマーシブレンダリングを制御し、カメラデータを提供し、空間の推論 Api にアクセスできるようにします。 UWP アプリの <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">Corewindow</a> または Win32 アプリの HWND 用に1つ作成します。

## <a name="set-up-the-holographic-space"></a>Holographic space を設定する

Holographic space オブジェクトの作成は、Windows Mixed Reality アプリを作成するための最初の手順です。 従来の Windows アプリは、アプリケーションビューのコアウィンドウ用に作成された Direct3D スワップチェーンにレンダリングします。 このスワップチェーンは、holographic UI のスレートに表示されます。 アプリケーションが2D スレートではなく holographic を表示するようにするには、スワップチェーンではなく、コアウィンドウの holographic 領域を作成します。 この holographic space によって作成された holographic フレームを表示すると、アプリが全画面表示モードになります。

[ *Holographic DirectX 11 アプリ (ユニバーサル Windows) テンプレート* から開始](creating-a-holographic-directx-project.md)する **UWP アプリ** の場合は、appview .cpp の **setwindow** メソッドで次のコードを探します。

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

[ *Basichologram* win32 サンプルから始める](creating-a-holographic-directx-project.md#creating-a-win32-project) **win32 アプリ** を構築する場合は、「 **app:: CreateWindowAndHolographicSpace** 」で HWND の例を確認してください。 次に、関連付けられた <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>を作成して、それをイマーシブ HWND に変換できます。

```cpp
void App::CreateWindowAndHolographicSpace(HINSTANCE hInstance, int nCmdShow)
{
    // Store the instance handle in our class variable.
    m_hInst = hInstance;

    // Create the window for the HolographicSpace.
    hWnd = CreateWindowW(
        m_szWindowClass, 
        m_szTitle,
        WS_VISIBLE,
        CW_USEDEFAULT, 
        0, 
        CW_USEDEFAULT, 
        0, 
        nullptr, 
        nullptr, 
        hInstance, 
        nullptr);

    if (!hWnd)
    {
        winrt::check_hresult(E_FAIL);
    }

    {
        // Use WinRT factory to create the holographic space.
        using namespace winrt::Windows::Graphics::Holographic;
        winrt::com_ptr<IHolographicSpaceInterop> holographicSpaceInterop =
            winrt::get_activation_factory<HolographicSpace, IHolographicSpaceInterop>();
        winrt::com_ptr<ABI::Windows::Graphics::Holographic::IHolographicSpace> spHolographicSpace;
        winrt::check_hresult(holographicSpaceInterop->CreateForWindow(
            hWnd, __uuidof(ABI::Windows::Graphics::Holographic::IHolographicSpace),
            winrt::put_abi(spHolographicSpace)));

        if (!spHolographicSpace)
        {
            winrt::check_hresult(E_FAIL);
        }

        // Store the holographic space.
        m_holographicSpace = spHolographicSpace.as<HolographicSpace>();
    }

    // The DeviceResources class uses the preferred DXGI adapter ID from the holographic
    // space (when available) to create a Direct3D device. The HolographicSpace
    // uses this ID3D11Device to create and manage device-based resources such as
    // swap chains.
    m_deviceResources->SetHolographicSpace(m_holographicSpace);

    // The main class uses the holographic space for updates and rendering.
    m_main->SetHolographicSpace(hWnd, m_holographicSpace);

    // Show the window. This will activate the holographic view and switch focus
    // to the app in Windows Mixed Reality.
    ShowWindow(hWnd, nCmdShow);
    UpdateWindow(hWnd);
}
```

UWP CoreWindow または Win32 HWND の HolographicSpace を取得すると、HolographicSpace は holographic カメラの処理、座標系の作成、および holographic レンダリングを行うことができます。 現在の holographic space は、DirectX テンプレート内の複数の場所で使用されます。
* **DeviceResources** クラスは、Direct3D デバイスを作成するために、HolographicSpace オブジェクトからいくつかの情報を取得する必要があります。 これは、holographic ディスプレイに関連付けられている DXGI アダプター ID です。 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>クラスは、アプリの Direct3D 11 デバイスを使用して、デバイスベースのリソース (各 holographic カメラのバックバッファーなど) を作成し、管理します。 この関数が内部で何を行っているかについては、DeviceResources にあります。
* 関数 **DeviceResources:: InitializeUsingHolographicSpace** は、LUID を検索してアダプターを取得する方法と、優先アダプターが指定されていない場合に既定のアダプターを選択する方法を示しています。
* アプリのメインクラスは、更新とレンダリングのために **Appview:: SetWindow** または **App:: CreateWindowAndHolographicSpace** の holographic 空間を使用します。

>[!NOTE]
>以下のセクションでは、holographic UWP アプリテンプレートから開始したことを前提として、 **Appview:: SetWindow** のようなテンプレートの関数名について説明していますが、表示されるコードスニペットは、uwp アプリと Win32 アプリ間でも同様に適用されます。

次に、 **SetHolographicSpace** が appmain クラスで担当するセットアッププロセスについて説明します。

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>カメライベントのサブスクライブ、カメラリソースの作成と削除

アプリの holographic コンテンツは holographic 空間に存在し、1つまたは複数の holographic カメラを通じて表示されます。これはシーンのさまざまなパースペクティブを表します。 Holographic 領域が完成したので、holographic カメラのデータを受け取ることができます。

アプリは、そのカメラに固有のリソースを作成することによって、 **CameraAdded** イベントに応答する必要があります。 このようなリソースの例として、バックバッファーレンダーターゲットビューがあります。 このコードは、アプリが holographic フレームを作成する前に **Appview:: SetWindow** によって呼び出される **DeviceResources:: SetHolographicSpace** 関数で確認できます。

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

また、アプリは、そのカメラ用に作成されたリソースを解放することによって、 **CameraRemoved** イベントに応答する必要があります。

**DeviceResources:: SetHolographicSpace** から:

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

イベントハンドラーは、holographic レンダリングを滑らかにするために何らかの作業を完了し、アプリをまったくレンダリングする必要があります。 詳細については、コードとコメントを参照してください。 main クラスで **OnCameraAdded** と **OnCameraRemoved** を検索すると、 **DeviceResources** によって **m_cameraResources** マップがどのように処理されるかを理解できます。

ここでは、AppMain と、アプリが holographic カメラについて認識できるようにするためのセットアップに焦点を合わせています。 この点を考慮して、次の2つの要件を確認することが重要です。

1. **CameraAdded** イベントハンドラーでは、アプリを非同期に処理して、新しい holographic カメラのリソースの作成とアセットの読み込みを完了できます。 この作業を完了するために複数のフレームを使用するアプリでは、遅延を要求し、非同期読み込みの後で遅延を完了する必要があります。 [PPL タスク](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl)は、非同期処理を実行するために使用できます。 アプリは、イベントハンドラーが終了したとき、または遅延が完了したときに、そのカメラにすぐにレンダリングできるようにする必要があります。 イベントハンドラーを終了するか、遅延を完了すると、そのカメラを含む holographic フレームを受信する準備ができたことがシステムに通知されます。

2. アプリは、 **CameraRemoved** イベントを受け取ると、バックバッファーへのすべての参照を解放し、関数をすぐに終了する必要があります。 これには、レンダーターゲットビューや、 [Idxgiresource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource)への参照を保持する他のリソースが含まれます。 また、 **CameraResources:: ReleaseResourcesForBackBuffer** に示すように、アプリは、バックバッファーがレンダーターゲットとしてアタッチされていないことを確認する必要があります。 処理速度を向上させるために、アプリはバックバッファーを解放し、タスクを起動して、カメラのその他の破棄作業を非同期に完了させることができます。 Holographic アプリテンプレートには、この目的で使用できる PPL タスクが含まれています。

>[!NOTE]
>追加または削除されたカメラがフレームにどのように表示されるかを確認するには、 **HolographicFrame** [addedcameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) プロパティと [removedcameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) プロパティを使用します。

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>Holographic コンテンツの参照のフレームを作成する

HolographicSpace にレンダリングするには、アプリのコンテンツが [空間座標系](coordinate-systems-in-directx.md) に配置されている必要があります。 システムには2つの主要な参照フレームが用意されており、これを使用して、ホログラムの座標系を確立できます。

Windows Holographic には、デバイスに接続されている参照フレームと、デバイスがユーザーの環境を移動するときに静止している参照フレームの2種類があります。 Holographic アプリテンプレートでは、既定で静止参照フレームが使用されます。これは、世界中にロックされているホログラムをレンダリングする最も簡単な方法の1つです。

静止参照フレームは、デバイスの現在の場所の近くに位置を安定させるように設計されています。 これは、デバイスが周囲の領域についてさらに学習するため、デバイスからさらに多くの座標がユーザーの環境に対して若干ずれてくる可能性があることを意味します。 静止した参照フレームを作成するには、 [空間ステージ](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)から座標系を取得する方法と、既定の <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>を使用する方法の2つがあります。 イマーシブヘッドセット用の Windows Mixed Reality アプリを作成している場合、推奨される開始点は [空間ステージ](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)です。 また、空間ステージは、プレーヤーによって摩耗されたイマーシブヘッドセットの機能に関する情報も提供します。 ここでは、既定の <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>の使用方法について説明します。

空間ロケーターは、Windows Mixed Reality デバイスを表し、デバイスの動きを追跡し、位置に対して相対的に理解できる座標系を提供します。

**Appmain:: OnHolographicDisplayIsAvailableChanged** から:

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

アプリが起動されたときに、静止参照フレームを1回作成します。 これは、アプリが起動されたときに原点がデバイスの位置に配置された、ワールド座標系を定義することに似ています。 この参照フレームはデバイスと共に移動しません。

**Appmain:: SetHolographicSpace** から:

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

すべての参照フレームは重力に沿っています。つまり、y 軸はユーザーの環境に関連する "上" を指します。 Windows では "右手" 座標系が使用されるため、– z 軸の方向は、参照フレームの作成時にデバイスが接続している "前方" 方向と一致します。

>[!NOTE]
>アプリが個々のホログラムを正確に配置する必要がある場合は、 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> を使用して、個々のホログラムを実際の世界の位置に固定します。 たとえば、ユーザーが特別な関心のあるポイントを示す場合は、空間アンカーを使用します。 アンカー位置はずれませんが、調整することができます。 既定では、アンカーが調整されると、修正が行われた後、その位置が次の複数のフレームに配置されるようになります。 アプリケーションによっては、これが発生したときに、別の方法で調整を処理することが必要になる場合があります (たとえば、ホログラムが非表示になるまでは、このように遅延させます)。 これらのカスタマイズは、 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> プロパティと <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> イベントによって有効になります。

## <a name="respond-to-locatability-changed-events"></a>Locatability 変更イベントへの応答

世界中にロックされているホログラムをレンダリングするには、デバイスが世界中に配置されている必要があります。 これは、環境の状況によっては常に可能であるとは限りません。その場合、ユーザーは追跡の中断を視覚的に示すことが期待される可能性があります。 この視覚的な表示は、デバイスに接続されている参照フレームを使用して、世界に固定するのではなく、レンダリングする必要があります。

アプリは、何らかの理由で追跡が中断された場合に、通知を受け取るように要求できます。 Locatの変更後のイベントに登録して、デバイスが世界中に配置されているかどうかを検出します。 **Appmain:: SetHolographicSpace から:**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

次に、このイベントを使用して、ホログラムを世界にどのようにレンダリングするかを決定します。

## <a name="see-also"></a>関連項目
* [DirectX でのレンダリング](rendering-in-directx.md)
* [DirectX の座標系](coordinate-systems-in-directx.md)
