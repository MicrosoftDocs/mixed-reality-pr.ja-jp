---
ms.openlocfilehash: c74a6c0c22439376a84ecb8254b945295c8988a2
ms.sourcegitcommit: b13c517df19179ca281362a1f006914289c58ad4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98052781"
---
# <a name="unity"></a>[Unity](#tab/unity)

![Unity](../images/unity_logo_banner.png)<br>

Unity を使用して、クロスプラットフォームのフル機能を備えた Mixed Reality アプリを構築します。 HoloLens または Windows Mixed Reality イマーシブ ヘッドセット向けの Unity 開発を開始するには、「[Unity 開発の概要](../unity/unity-development-overview.md)」を参照してください。

## <a name="available-hardware-platforms"></a>使用可能なハードウェア プラットフォーム

Unity を使用して Mixed Reality アプリを構築する場合、ハードウェアとエミュレーターのオプションがいくつか用意されています。 Microsoft の開発者向けドキュメントでは HoloLens デバイスに焦点を当てていますが、イマーシブ ヘッドセットの展開についての情報が必要な場合は、デバイス サポート セクションをご覧いただけます。

**拡張現実デバイス**
* [HoloLens (第 1 世代)](https://docs.microsoft.com/hololens/hololens1-hardware)
* [HoloLens 2](https://docs.microsoft.com/hololens/hololens2-hardware)

**イマーシブ VR ヘッドセット**
* HP Reverb および Reverb G2
* Samsung Odyssey および Odyssey+
* HP Windows Mixed Reality ヘッドセット
* Lenovo Explorer
* Acer AH101
* Dell Visor
* Asus HC102
* Acer OJO 500

## <a name="available-tools-and-sdks"></a>使用可能なツールと SDK

|  ツールまたは SDK  |  説明  |
| --- | --- |
| [Unity 用 Mixed Reality ツールキット](../unity/mrtk-getting-started.md) | Unity 用 Mixed Reality ツールキットは、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォームをターゲットとしたアプリケーションの開発を加速するために構築された、オープンソースのクロスプラットフォーム開発キットです。 |

## <a name="cloud-services"></a>クラウド サービス

Unity に組み込まれている Mixed Reality プロジェクトに統合できるクラウド サービスがいくつかあります。具体的には、**Azure Remote Rendering** と **Azure Spatial Anchors** です。 これらのサービスは、アプリケーションに共有ホログラフィック コンテンツとリアルタイム 3D レンダリングを追加することで、アプリケションをユーザーにとってより魅力的でイマーシブにすることができます。

これらのすべてのサービスは、[HoloLens 向け Unity 開発体験](../unity/unity-development-overview.md)のコースで説明されています。**Unity を使用する Mixed Reality についての学習パスとして、このコースを強くお勧めします**。 既にこのパスに入っているので、このまま読み続け、記事の下部にある大きな青いボタンで先に進んでください。 ただし、より高度な開発段階にある方で、すぐに作業を始めたい場合は、[クラウド サービスの概要](../mixed-reality-cloud-services.md)を確認するか、[サービス リソース](../unity/unity-development-overview.md#5-adding-services)に直接移動してください。

## <a name="dynamics-365-guides"></a>Dynamics 365 Guides

**Microsoft Dynamics 365 Guides** を使用すると、アプリの仮想環境にホログラフィックな指示をビジュアルにテザリングし、必要なときに必要な場所で重要な情報をユーザーに提供できます。 この機能については HoloLens 向け Unity 開発体験でも説明されていますが、先に進みたい場合は、[こちら](../unity/unity-development-overview.md#5-adding-services)で **[Dynamics 365]** タブを選択して、何が提供されているかを確認できます。

## <a name="examples"></a>例

Microsoft では、オープンソースの[サンプル アプリ](../unity/samples.md)をいくつか用意しています。これらをダウンロードして試してみることにより、Unity の Mixed Reality 製品の感覚を体験できます。 また、特定の機能をテストするための MRTK サンプル シーンも用意されています。
* [Unity 用ハンド インタラクション サンプル シーン (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#open-and-run-the-handinteractionexamples-scene-in-editor) - HandInteractionExamples.unity のサンプル シーンには、多関節ハンド入力が強調されているさまざまな種類の操作と UI コントロールが含まれています。

* [Unity 用視線追跡サンプル (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_ExamplesOverview.html) - このページでは、提供されている MRTK の視線追跡サンプルを基に構築することにより、MRTK での視線追跡をすばやく開始する方法について説明します。

>[!NOTE]
>どちらの MRTK サンプル シーンでも、MRTK Foundation パッケージとサンプル Unity パッケージがインストールされている必要があります。

# <a name="unreal"></a>[Unreal](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

Unreal を使用して、クロスプラットフォームのフル機能を備えた Mixed Reality アプリを構築します。 HoloLens 向けの Unreal 開発を開始するには、「[Unreal 開発の概要](../unreal/unreal-development-overview.md)」を参照してください。

## <a name="available-hardware-platforms"></a>使用可能なハードウェア プラットフォーム

Unreal Engine を使用して Mixed Reality アプリを構築する場合、ハードウェア、エミュレーター、ストリーミングのオプションがいくつか用意されています。 Microsoft の開発者向けドキュメントでは HoloLens デバイスに焦点を当てていますが、Unreal プロジェクトを x64 デスクトップ アプリとしてパッケージ化して、イマーシブ ヘッドセットで実行することもできます。

**拡張現実デバイス**
* [HoloLens (第 1 世代)](https://docs.microsoft.com/hololens/hololens1-hardware)
* [HoloLens 2](https://docs.microsoft.com/hololens/hololens2-hardware)

**イマーシブ VR ヘッドセット**
* HP Reverb および Reverb G2
* Samsung Odyssey および Odyssey+
* HP Windows Mixed Reality ヘッドセット
* Lenovo Explorer
* Acer AH101
* Dell Visor
* Asus HC102
* Acer OJO 500

## <a name="available-tools-and-sdks"></a>使用可能なツールと SDK

|  ツールまたは SDK  |  説明  |
| --- | --- |
| [Unreal 用 Mixed Reality ツールキット](https://github.com/microsoft/MixedRealityToolkit-Unreal) | Unreal 用 Mixed Reality ツールキット (MRTK-Unreal) は、Unreal Engine を使用して Mixed Reality アプリケーションの開発を促進するように設計されたプラグイン、サンプル、ドキュメントの形式で構成された一連のコンポーネントです。 |

## <a name="cloud-services"></a>クラウド サービス

Unreal で Mixed Reality アプリを構築する場合は、**Azure Spatial Anchors** と呼ばれる強力なクラウド サービスにアクセスできます。これを使用すると、さまざまなデバイス間でホログラフィック コンテンツを追加、永続化、および共有できます。 

Azure Spatial Anchors は、[Unreal 開発体験](../unreal/unreal-development-overview.md)のコースで説明されています。**Unreal を使用する Mixed Reality についての学習パスとして、このコースを強く推奨します**。 既にこのパスに入っているので、このまま読み続け、記事の下部にある大きな青いボタンで先に進んでください。 ただし、より高度な開発段階にある方で、すぐに作業を始めたい場合は、[クラウド サービスの概要](../mixed-reality-cloud-services.md)を確認するか、[サービス リソース](../unreal/unreal-development-overview.md#5-adding-services)に直接移動してください。

## <a name="dynamics-365-guides"></a>Dynamics 365 Guides

**Microsoft Dynamics 365 Guides** を使用すると、アプリの仮想環境にホログラフィックな指示をビジュアルにテザリングし、必要なときに必要な場所で重要な情報をユーザーに提供できます。 この機能については Unreal 開発体験でも説明されていますが、先に進みたい場合は、[こちら](../unreal/unreal-development-overview.md#5-adding-services)で **[Dynamics 365]** タブを選択して、何が提供されているかを確認できます。

## <a name="examples"></a>例

* [Kippy's Escape](../unreal/unreal-kippys-escape.md) - Kippy's Escape は、Unreal Engine 4 と Mixed Reality UX Tools for Unreal で構築された、オープンソースの HoloLens 2 サンプル アプリです。 このゲームでは、HoloLens 2 ハードウェアの固有の機能と、Mixed Reality UX Tools の開発力が紹介されています。


# <a name="javascript"></a>[JavaScript](#tab/web)

![Web](../images/javascript_logo_banner.png)

WebXR Device API は、Mixed Reality アプリを任意のプラットフォームのブラウザーで体験できるようにするオープン仕様です。 [JavaScript 開発の概要](../web/javascript-development-overview.md) をご確認いただくと、任意のプラットフォーム向けに Mixed Reality アプリの構築を開始できます。


# <a name="native-openxr"></a>[ネイティブ (OpenXR)](#tab/native)

 ![ネイティブ](../images/native_logo_banner.png)

Windows Mixed Reality API と直接通信する Mixed Reality アプリを作成します。 HoloLens 2 または Windows Mixed Reality イマーシブ ヘッドセット向けに OpenXR または従来の WinRT を使用してネイティブ アプリ開発を開始するには、「[ネイティブ開発の概要](../native/directx-development-overview.md)」を参照してください。 Windows Mixed Reality API では C++ と C# で記述されたアプリケーションがサポートされており、どちらの言語でも独自のフレームワークやミドルウェアを構築できます。

## <a name="available-hardware-platforms"></a>使用可能なハードウェア プラットフォーム

OpenXR 開発で Mixed Reality アプリを構築する場合、ハードウェア、エミュレーター、ストリーミングのオプションがいくつか用意されています。 

**拡張現実デバイス**
* [HoloLens 2](https://docs.microsoft.com/hololens/hololens2-hardware)

**イマーシブ VR ヘッドセット**
* HP Reverb および Reverb G2
* Samsung Odyssey および Odyssey+
* HP Windows Mixed Reality ヘッドセット
* Lenovo Explorer
* Acer AH101
* Dell Visor
* Asus HC102
* Acer OJO 500

## <a name="available-tools-and-sdks"></a>使用可能なツールと SDK

|  ツールまたは SDK  |  説明  |
| --- | --- |
| [OpenXR 開発者ツール](../native/openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) | OpenXR のさまざまな機能を実行するデモ シーンに加えて、アクティブなランタイムと現在のヘッドセットに関する重要な情報を提供するシステム ステータス ページを提供します。 |
| [OpenXR の仕様](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html) |  OpenXR の概要、機能、プロジェクトへの実装方法について説明しています。 |
| [OpenXR ローダー](../native/openxr-getting-started.md#integrate-the-openxr-loader-into-a-project) | デバイス上のアクティブな OpenXR ランタイムが検出され、実装されているコア関数と拡張関数へのアクセスが提供されます。 |

## <a name="examples"></a>例

サンプル アプリを自由に試して、Native 開発と Mixed Reality で何が実現できるかをご体験ください。

<!-- Go to actual GH link for more samples -->
* [BasicXrApp](https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp) - 2 つの Visual Studio プロジェクト ファイルを使用した OpenXR の簡単なサンプルを示します。1 つは Win32 デスクトップ アプリ、もう 1 つは UWP HoloLens 2 アプリ向けです。

また、Visual Studio での OpenXR API のすべての主要コンポーネントのことがわかる、BasicXrApp に関する 60 分のチュートリアルもご覧いただけます。
>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]
