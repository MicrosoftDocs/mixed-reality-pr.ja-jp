---
title: Holographic Remoting プレーヤーの記述
description: リモートコンピューター上にレンダリングされたコンテンツを HoloLens 2 に表示するカスタム Hologaphic リモート処理アプリを作成します。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理、NuGet、アプリケーションマニフェスト、プレーヤーコンテキスト、リモートアプリ、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット
ms.openlocfilehash: 391650025398b4bdd89e30db1df7df5e3d6ab5f2
ms.sourcegitcommit: 63b7f6d5237327adc51486afcd92424b79e6118b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2021
ms.locfileid: "98810124"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a>カスタム Holographic リモート処理プレーヤーアプリの作成

>[!IMPORTANT]
>このドキュメントでは、HoloLens 2 用のカスタムプレーヤーアプリケーションの作成について説明します。 HoloLens 2 向けに作成されたカスタムプレーヤーは、HoloLens 1 用に作成されたリモートアプリケーションと互換性がありません。 これは、両方のアプリケーションが NuGet **パッケージバージョン 2.x** を使用する必要があることを意味します。

カスタム Holographic リモート処理プレーヤーアプリを作成することにより、HoloLens 2 のリモートコンピューター上のから [イマーシブビュー](../../design/app-views.md) を表示できるカスタムアプリケーションを作成できます。 このページのすべてのコードと作業中のプロジェクトは、 [Holographic リモート処理のサンプル github リポジトリ](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)にあります。

Holographic リモート処理プレーヤーを使用すると、アプリは、デスクトップ PC または UWP デバイスに [レンダリング](rendering.md) された Holographic コンテンツを、より多くのシステムリソースにアクセスできるようになります。 Holographic Remoting player アプリは、入力データを Holographic リモート処理リモートアプリケーションにストリーミングし、ビデオとオーディオストリームとしてイマーシブビューを受信します。 接続は標準の Wi-fi を使用して行われます。 プレーヤーアプリを作成するには、NuGet パッケージを使用して Holographic Remoting を UWP アプリに追加します。 次に、接続を処理し、イマーシブビューを表示するコードを記述します。 

## <a name="prerequisites"></a>前提条件

開始点としては、既に Windows Mixed Reality API を対象としている、動作する DirectX ベースの UWP アプリを使用することをお勧めします。 詳細については、「 [DirectX 開発の概要](../native/directx-development-overview.md)」を参照してください。 既存のアプリがなく、最初から開始する場合は、 [C++ holographic プロジェクトテンプレート](../native/creating-a-holographic-directx-project.md) を使用することをお勧めします。

>[!IMPORTANT]
>Holographic リモート処理を使用するすべてのアプリは、 [マルチスレッドアパートメント](/windows/win32/com/multithreaded-apartments)を使用するように作成する必要があります。 [シングルスレッドアパートメント](/windows/win32/com/single-threaded-apartments)の使用はサポートされていますが、パフォーマンスが低下し、再生中に途切れが生じる可能性があります。 C++ を使用している場合、winrt [winrt:: init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) 、マルチスレッドアパートメントが既定値です。

## <a name="get-the-holographic-remoting-nuget-package"></a>Holographic リモート処理 NuGet パッケージを取得する

Visual Studio で NuGet パッケージをプロジェクトに追加するには、次の手順を実行する必要があります。
1. Visual Studio でプロジェクトを開きます。
2. プロジェクトノードを右クリックし、[ **NuGet パッケージの管理...** ] を選択します。
3. 表示されるパネルで、[ **参照** ] を選択し、"Holographic Remoting" を検索します。
4. [ **Holographic**] を選択し、最新の2.x バージョンを選択して [**インストール**] を選択 **します。**
5. [ **プレビュー** ] ダイアログが表示されたら、[ **OK]** を選択します。
6. [使用許諾契約書が表示されたら **同意** する] を選択します。

>[!IMPORTANT]
><a name="idl"></a>```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```NuGet パッケージ内には、Holographic Remoting によって公開される API に関する詳細なドキュメントが含まれています。

## <a name="modify-the-packageappxmanifest-of-the-application"></a>アプリケーションの package.appxmanifest を変更する

NuGet パッケージによって追加された Microsoft.Holographic.AppRemoting.dll をアプリケーションが認識できるようにするには、次の手順をプロジェクトで実行する必要があります。

1. ソリューションエクスプローラーで **package.appxmanifest** ファイルを右クリックし、[**プログラムから開く**] を選択します。
2. **XML (テキスト) エディター** を選択し、[ **OK]** を選択します。
3. 次の行をファイルに追加して保存します。
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a>プレーヤーのコンテキストを作成する

最初の手順として、アプリケーションでプレーヤーコンテキストを作成する必要があります。

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting remote app and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
>Holographic リモート処理は、Windows の一部である Windows Mixed Reality ランタイムをリモート処理固有のランタイムに置き換えることによって機能します。 これは、プレーヤーのコンテキストの作成時に実行されます。 そのため、プレーヤーコンテキストを作成する前に Windows Mixed Reality API を呼び出すと、予期しない動作が発生する可能性があります。 推奨される方法は、任意の混合 Reality API と対話する前に、可能な限り早くプレーヤーコンテキストを作成することです。 Windows Mixed Reality API を使用して作成または取得したオブジェクトを、 ```PlayerContext::Create``` 後で作成または取得したオブジェクトで混在させないでください。

次に、 [HolographicSpace](/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)を呼び出して、HolographicSpace を作成します。

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a>リモートアプリに接続する

プレーヤーアプリがコンテンツを表示できる状態になったら、リモートアプリへの接続を確立できます。

接続は、次のいずれかの方法で確立できます。
1) HoloLens 2 で実行されているプレーヤーアプリは、リモートアプリに接続します。
2) リモートアプリは、HoloLens 2 で実行されているプレーヤーアプリに接続します。

プレーヤーアプリからリモートアプリに接続するには、 ```Connect``` ホスト名とポートを指定して、プレーヤーのコンテキストでメソッドを呼び出します。 既定のポートは **8265** です。

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
>C++/WinRT API と同様に、 ```Connect``` 処理する必要がある winrt:: hresult_error をスローすることがあります。

プレーヤーアプリで着信接続をリッスンするには、メソッドを呼び出し ```Listen``` ます。 この呼び出しでは、ハンドシェイクポートとトランスポートポートの両方を指定できます。 ハンドシェイクポートは、初期ハンドシェイクに使用されます。 データは、トランスポートポートを介して送信されます。 既定では、ポート番号 **8265** と **8266** が使用されます。

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a>接続関連のイベントの処理

は、 ```PlayerContext``` 接続の状態を監視するために3つのイベントを公開します。
1) OnConnected: リモートアプリへの接続が正常に確立されたときにトリガーされます。
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) OnDisconnected: 確立された接続が終了した場合、または接続が確立できなかった場合にトリガーされます。
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
>指定できる ```ConnectionFailureReason``` 値は、ファイルに記載されてい ```Microsoft.Holographic.AppRemoting.idl``` [](#idl)ます。

3) OnListening: 受信接続のリッスンが開始されます。
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

さらに、プレーヤーのコンテキストでプロパティを使用して接続状態を照会することもでき ```ConnectionState``` ます。
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>リモートで描画されたフレームを表示する

リモートでレンダリングされるコンテンツを表示するには、 ```PlayerContext::BlitRemoteFrame``` [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe)のレンダリング中にを呼び出します。 

```BlitRemoteFrame``` 現在の HolographicFrame のバックバッファーがレンダーターゲットとしてバインドされている必要があります。 バックバッファーは、 [Direct3D11BackBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer)プロパティを介して[HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters)から受け取ることができます。

呼び出されると、 ```BlitRemoteFrame``` リモートアプリケーションから最後に受信したフレームを HolographicFrame の BackBuffer にコピーします。 さらに、リモートアプリケーションがリモートフレームのレンダリング中にフォーカスポイントを指定している場合は、フォーカスポイントが設定されます。

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame``` 現在のフレームのフォーカスポイントを上書きする可能性があります。 
>- フォールバックフォーカスポイントを指定するには、前に [HolographicCameraRenderingParameters:: SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) を呼び出し ```PlayerContext::BlitRemoteFrame``` ます。 
>- リモートフォーカスポイントを上書きするには、 [HolographicCameraRenderingParameters:: SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  を呼び出し ```PlayerContext::BlitRemoteFrame``` ます。

成功した場合、は ```BlitRemoteFrame``` を返し ```BlitResult::Success_Color``` ます。 それ以外の場合は、エラーの理由を返します。
- ```BlitResult::Failed_NoRemoteFrameAvailable```: 使用可能なリモートフレームがないため、失敗しました。
- ```BlitResult::Failed_NoCamera```: カメラが存在しないために失敗しました。
- ```BlitResult::Failed_RemoteFrameTooOld```: リモートフレームが古すぎるため失敗しました (PlayerContext:: BlitRemoteFrameTimeout プロパティを参照してください)。

>[!IMPORTANT]
> バージョン [2.1.0](holographic-remoting-version-history.md#v2.1.0) 以降では、カスタムプレーヤーが Holographic リモート処理を介して深さの再投影を使用できるようになります。

```BlitResult``` は ```BlitResult::Success_Color_Depth``` 、次の条件下でもを返すことができます。

- リモートアプリは、HolographicCameraRenderingParameters を使用して深度バッファーをコミットしました。 [CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)。
- カスタムプレーヤーアプリは、を呼び出す前に有効な深度バッファーをバインドしました ```BlitRemoteFrame``` 。

これらの条件が満たされる ```BlitRemoteFrame``` と、リモートの深さが現在バインドされているローカルの深度バッファーに array.blit ます。 その後、追加のローカルコンテンツをレンダリングできます。これには、リモートでレンダリングされるコンテンツとの深さの積集合があります。 さらに、カスタムプレーヤーで [HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) を使用してローカル深度バッファーをコミットし、リモートおよびローカルでレンダリングされるコンテンツの深さを再予測することもできます。 詳細については、「 [深度 Reprojection](hologram-stability.md#reprojection) 」を参照してください。

### <a name="projection-transform-mode"></a>プロジェクション変換モード

問題の1つは、Holographic リモート処理を使用して深さの reprojection を使用しているときに、カスタムプレーヤーアプリによって直接レンダリングされるローカルコンテンツとは別のプロジェクション変換を使用してリモートコンテンツをレンダリングできることです。 一般的なユースケースでは、プレーヤー側とリモート側で ( [HolographicCamera:: SetNearPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) と [HolographicCamera:: SetFarPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)を使用して) 近距離および遠平面に対して異なる値を指定します。 この場合、プレーヤー側の射影変換にリモートの近距離/遠距離またはローカルの距離が反映されているかどうかは明確ではありません。

バージョン [2.1.0](holographic-remoting-version-history.md#v2.1.0) 以降では、を使用して投影変換モードを制御でき ```PlayerContext::ProjectionTransformConfig``` ます。 サポートされる値は次のとおりです。

- ```Local``` - [HolographicCameraPose::P rojectiontransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) は、HolographicCamera 上のカスタムプレーヤーアプリによって設定された近距離/遠平面距離を反映する射影変換を返します。
- ```Remote``` -射影変換は、リモートアプリによって指定された近距離距離と遠距離を反映します。
- ```Merged``` -リモートアプリとカスタムプレーヤーアプリとの間の距離が近い場合は、統合されます。 既定では、これを行うには、近距離距離の最小値と、遠くの平面距離の最大値を取得します。 リモート側またはローカル側のどちらか一方が反転している場合は、遠く < 近くにあるとしても、遠くと遠くに離れた距離の距離が反転します。

## <a name="optional-set-blitremoteframetimeout"></a>省略可能: Set BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a>
>[!IMPORTANT]
> ```PlayerContext::BlitRemoteFrameTimeout``` は、バージョン [2.0.9](holographic-remoting-version-history.md#v2.0.9)以降でサポートされています。 

プロパティは、 ```PlayerContext::BlitRemoteFrameTimeout``` 新しいリモートフレームが受信されなかった場合に、リモートフレームが再利用される時間を指定します。 

一般的なユースケースでは、一定の時間、新しいフレームが受信されなかった場合に、BlitRemoteFrame timeout で空の画面が表示されるようにします。 有効にすると、メソッドの戻り値の型を使用して、 ```BlitRemoteFrame``` ローカルに表示されるフォールバックコンテンツに切り替えることもできます。 

タイムアウトを有効にするには、プロパティ値を100ミリ秒以上の期間に設定します。 タイムアウトを無効にするには、プロパティをゼロ期間に設定します。 タイムアウトが有効になっていて、set duration のリモートフレームが受信されなかった場合、BlitRemoteFrame は失敗し、 ```Failed_RemoteFrameTooOld``` 新しいリモートフレームが受信されるまで戻ります。

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a>省略可能: 最後のリモートフレームに関する統計を取得する

パフォーマンスまたはネットワークの問題を診断するために、プロパティを使用して最後のリモートフレームに関する統計を取得でき ```PlayerContext::LastFrameStatistics``` ます。 統計は [HolographicFrame::P](/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)の呼び出し中に更新されます。 current予測。

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

詳細については、ファイルのドキュメントを参照してください ```PlayerFrameStatistics``` ```Microsoft.Holographic.AppRemoting.idl``` [](#idl)。

## <a name="optional-custom-data-channels"></a>省略可能: カスタムデータチャネル

カスタムデータチャネルは、既に確立されているリモート処理接続を介してユーザーデータを送信するために使用できます。 詳細については、「 [カスタムデータチャネル](holographic-remoting-custom-data-channels.md) 」を参照してください。

## <a name="see-also"></a>参照
* [Windows Mixed Reality Api を使用した Holographic リモート処理リモートアプリの作成](holographic-remoting-create-remote-wmr.md)
* [OpenXR Api を使用した Holographic リモート処理リモートアプリの作成](holographic-remoting-create-remote-openxr.md)
* [カスタムの Holographic Remoting データ チャネル](holographic-remoting-custom-data-channels.md)
* [Holographic Remoting を使用したセキュリティで保護された接続の確立](holographic-remoting-secure-connection.md)
* [Holographic リモート処理のトラブルシューティングと制限事項](holographic-remoting-troubleshooting.md)
* [Holographic Remoting ソフトウェア ライセンス条項](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)