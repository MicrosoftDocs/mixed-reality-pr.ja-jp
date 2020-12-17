---
title: OpenXR
description: ポータブル OpenXR API 標準を使用してエンジンをビルドし、Windows Mixed Reality と HoloLens 2 ヘッドセットに展開します。
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、ネイティブ、ネイティブアプリ、カスタムエンジン、ミドルウェア
ms.openlocfilehash: ba03799ff42d3a4c27799dcf2f4035d408360120
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613132"
---
# <a name="openxr"></a>OpenXR

<img align="right" src="images/openxr.png" alt="OpenXR logo">

OpenXR は、 <a href="https://www.khronos.org/" target="_blank">Khronos</a>のオープンなロイヤリティフリー API 標準であり、 [混合現実](../../discover/mixed-reality.md)の範囲内のさまざまなデバイスにネイティブでアクセスできるエンジンを提供します。

HoloLens 2 で OpenXR を使用するか、デスクトップで Windows Mixed Reality イマーシブ ヘッドセットを使用して開発できます。  ヘッドセットへのアクセス権がない場合は、代わりに HoloLens 2 エミュレーターまたは Windows Mixed Reality シミュレーターを使用できます。

## <a name="why-openxr"></a>OpenXR の理由

OpenXR を使用すると、HoloLens 2 のような holographic デバイスとイマーシブデバイス (デスクトップ Pc 用の Windows Mixed Reality ヘッドセットなど) の両方を対象とするエンジンを構築できます。 OpenXR を使用すると、さまざまなハードウェアプラットフォームで移植可能なコードを一度記述できます。

OpenXR API はローダーを使用して、アプリケーションをヘッドセットのネイティブプラットフォームサポートに直接接続します。 エンドユーザーは、Windows Mixed Reality とその他のヘッドセットのどちらを使用しているかにかかわらず、最大のパフォーマンスと最小待機時間を実現します。

## <a name="what-is-openxr"></a>OpenXR とは

OpenXR API は、holographic デバイスとイマーシブデバイスの両方を対象とするエンジンを構築するために必要な、コアの予測、フレームのタイミング、および空間入力の機能を提供します。

OpenXR API の詳細については、OpenXR 1.0 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">仕様</a>、 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API リファレンス</a>、および <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">クイックリファレンスガイド</a>を参照してください。  詳細については、 <a href="https://www.khronos.org/openxr/" target="_blank">Khronos OpenXR のページ</a>を参照してください。

HoloLens 2 の全機能セットを対象にするには、クロスベンダおよびベンダー固有の OpenXR 拡張機能を使用します。これにより、OpenXR 1.0 コア以外の追加機能が可能になります。これには、トレーラーによる追跡、視線追跡、空間マッピング、空間アンカーなどがあります。 詳細については、この後の拡張機能に関する次の「 [ロードマップ」セクション](#roadmap) を参照してください。

OpenXR は、それ自体が mixed reality エンジンではありません。  代わりに、OpenXR は、Unity や Unreal などのエンジンがポータブルコードを一度記述できるようにします。これにより、ユーザーの holographic またはイマーシブデバイスのネイティブプラットフォーム機能にアクセスできるようになります。ベンダーによっては、そのプラットフォームが構築されています。

## <a name="roadmap"></a>ロードマップ

OpenXR 仕様では、ランタイム実装者が<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Base OpenXR 1.0 仕様</a>で定義されている[コア機能](#what-is-openxr)以外の機能を公開できるようにする拡張機構を定義しています。

OpenXR 拡張機能には、次の3種類があります。
* **ベンダー拡張機能 (たとえば、 `MSFT` ):** ハードウェアまたはソフトウェアの機能でベンダーごとのイノベーションを実現します。  任意のランタイムベンダは、いつでもベンダ拡張機能を導入および出荷できます。
  * **試験的なベンダーの拡張機能 (たとえば、 `MSFT_preview` ):** フィードバックを収集するためにプレビューされている試験的なベンダーの拡張機能。  `MSFT_preview` 拡張機能は開発者向けデバイスのみを対象としており、実際の拡張機能が出荷されると削除されます。  試してみるには、 [開発者デバイスでプレビュー拡張機能を有効に](openxr-getting-started.md#using-preview-extensions)します。
* **クロスベンダ `EXT` 拡張機能:** 複数の企業が定義および実装するクロスベンダーの拡張機能。  関心のある企業のグループは、いつでも拡張機能を導入できます。
* **公式の `KHR` 拡張機能:** 公式の Khronos extensions 批准は、コア仕様リリースの一部として機能します。  KHR 拡張機能は、コア仕様自体と同じライセンスによってカバーされます。

2020年7月の時点で、Windows Mixed Reality OpenXR ランタイムは、一連のおよび拡張機能をサポートして `MSFT` おり、 `EXT` すべての HoloLens 2 機能を OpenXR アプリケーションに提供します。

| Feature area (機能領域) | 拡張機能の可用性 |
|--------------|------------------------|
| システム + セッション | **OpenXR 1.0 コア仕様:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [参照スペース (view、local、stage)](../../design/coordinate-systems.md) | **OpenXR 1.0 コア仕様:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| 構成の表示 (mono、ステレオ) | **OpenXR 1.0 コア仕様:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [スワップチェーン](../platform-capabilities-and-apis/rendering.md)  + [フレームのタイミング](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) | **OpenXR 1.0 コア仕様:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| コンポジションレイヤー<br />(プロジェクション、クワッド) | **OpenXR 1.0 コア仕様:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [Input および haptics](../../design/interaction-fundamentals.md) | **OpenXR 1.0 コア仕様:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Direct3D 11 の統合 | **正式な拡張機能がリリースされました `KHR` :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code> |
| Direct3D 12 の統合 | **正式な拡張機能がリリースされました `KHR` :**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code> |
| [無制限の参照スペース <br /> (ワールドスケールエクスペリエンス)](../../design/coordinate-systems.md#building-a-world-scale-experience) | **`MSFT` リリースされた拡張機能:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [空間アンカー](../../design/spatial-anchors.md) | **`MSFT` リリースされた拡張機能:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code> |
| [ハンドの相互作用 <br /> (グリップ/aim、エアタップ、つかみ)](../../design/hands-and-tools.md)<p>*HoloLens 2 のみ*</p> | **`MSFT` リリースされた拡張機能:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_interaction">XR_MSFT_hand_interaction</a></code> |
| [手 articulation + 手メッシュ](../../design/hands-and-tools.md)<p>*HoloLens 2 のみ*</p> | <p>**`EXT` ランタイム102でリリースされた拡張機能:**<code><br /><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hand_tracking">XR_EXT_hand_tracking</a></code></p>**`MSFT` ランタイム102でリリースされた拡張機能:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_tracking_mesh">XR_MSFT_hand_tracking_mesh</a></code> |
| [目の視線入力](../../design/eye-tracking.md)<p>*HoloLens 2 のみ*</p> | **`EXT` リリースされた拡張機能:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code> |
| 他の HoloLens Sdk との相互運用<br />(例については、 [QR](../platform-capabilities-and-apis/qr-code-tracking.md))<p>*HoloLens 2 のみ*</p> | <p>**`MSFT` ランタイム102でリリースされた拡張機能:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code></p><p>**`MSFT`[プレビューランタイム 104](openxr-getting-started.md#using-preview-extensions)の拡張機能:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_perception_anchor_interop_preview">XR_MSFT_perception_anchor_interop_preview</a></code></p> |
| [Mixed Reality キャプチャ <br /> (PV カメラからの3番目のレンダリング)](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*HoloLens 2 のみ*</p> | **`MSFT` ランタイム102でリリースされた拡張機能:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_secondary_view_configuration">XR_MSFT_secondary_view_configuration</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_first_person_observer">XR_MSFT_first_person_observer</a></code> |
| UWP CoreWindow API との相互運用<br />(例、キーボード/マウス) | **`MSFT` ランタイム103でリリースされた拡張機能:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_holographic_window_attachment">XR_MSFT_holographic_window_attachment</a></code>
| モーションコントローラーの相互作用プロファイル (Samsung Odyssey および HP リバーブ G2) | **`MSFT` ランタイム103でリリースされた拡張機能:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_samsung_odyssey_controller">XR_EXT_samsung_odyssey_controller</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hp_mixed_reality_controller">XR_EXT_hp_mixed_reality_controller</a></code> |
| [モーションコントローラーレンダリングモデル](../../design/motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT`[プレビューランタイム 104](openxr-getting-started.md#using-preview-extensions)の拡張機能:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_controller_model">XR_MSFT_controller_model</a></code> |
| [シーンの理解 (平面、メッシュ)](../../design/scene-understanding.md)<p>*HoloLens 2 のみ*</p> | <p>**[Preview runtime 102](openxr-getting-started.md#using-preview-extensions)以降:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code>シーンで[SDK](../platform-capabilities-and-apis/scene-understanding-sdk.md)を使用して使用する</p><p>**`MSFT_preview` 将来のプレビューランタイムの拡張機能** *(計画済み)*</p> |
| その他のクロスベンダ拡張機能 | <p>**正式な拡張機能がリリースされました `KHR` :**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><p>**`EXT` リリースされた拡張機能:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code> |

これらの拡張機能の一部はベンダー固有の拡張機能として開始される場合があり `MSFT` ますが、Microsoft およびその他の OpenXR runtime ベンダーは、 `EXT` `KHR` これらの機能領域の多くに対してクロスベンダーまたは拡張機能を設計するために連携しています。 クロスベンダ拡張機能を使用すると、コア仕様と同様に、これらの機能のために記述したコードをランタイムベンダー間で移植できます。

## <a name="getting-started-with-openxr"></a>OpenXR の概要

![Mixed reality ヘッドセットを装着しているユーザーによって再生されている minecraft のスクリーンショット](images/openxr-minecraft.jpg)

*Minecraft の新しい RenderDragon エンジンは、OpenXR を使用してデスクトップの VR サポートを構築しています*

Microsoft は、Unity およびエピックゲームと連携して、HoloLens 2 だけでなく、 [HP の新しいリバーブ G2 ヘッドセット](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)を含む幅広い PC VR で、mixed reality の未来を確実に開いています。  HoloLens (第1世代) 向けの開発の詳細については、 [リリースノート](https://docs.microsoft.com/hololens/hololens1-release-notes)を参照してください。

Unity、Unreal Engine、または独自のエンジンで OpenXR を開始する方法については、「」を参照してください。

### <a name="openxr-in-unity"></a>Unity の OpenXR

現在、HoloLens 2、HoloLens (第1世代)、および Windows Mixed Reality ヘッドセットのサポートされている Unity 開発パスは、既存の WinRT API バックエンドとの **unity 2019 LTS** です。  [Unity で OpenXR](../unity/openxr-getting-started.md)に移動することができます。Unity 2019 アプリで新しい HP リバーブ G2 コントローラーを対象としている場合は、 [Hp リバーブ g2 の入力ドキュメント](../unity/unity-reverb-g2-controllers.md)を参照してください。

Unity **2020 LTS** 以降、Unity は HoloLens 2 および Windows Mixed Reality ヘッドセットをサポートする [OpenXR バックエンドを出荷](https://forum.unity.com/threads/unitys-plans-for-openxr.993225/) します。  これには、OpenXR 拡張機能のサポートが含まれます。これは、手動による監視、空間アンカー、HP リバーブ G2 コントローラーなど、 [HoloLens 2 および Windows Mixed Reality ヘッドセットの全機能](#roadmap)を備えています。  現在、OpenXR のサポートは [mrtk_development 分岐](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development) で開発中であり、その OpenXR preview パッケージと共に使用できます。 MRTK-Unity

**Unity 2021** 以降、OpenXR は、HoloLens 2 および Windows Mixed Reality ヘッドセットを対象とする唯一サポートされている unity バックエンドとして卒業します。

### <a name="openxr-in-unreal-engine"></a>Unreal Engine の OpenXR

**Unreal Engine 4.23** の場合、HoloLens 2 および Windows mixed reality ヘッドセットの完全なサポートは、Windows mixed Reality (WinRT) プラグインを通じて利用できます。

Unreal Engine 4.23 は、OpenXR 1.0 のプレビューサポートを出荷するための最初のメジャーゲームエンジンリリースでもありました。  **Unreal engine 4.26** では、HoloLens 2 のサポート、Windows Mixed Reality、およびその他のデスクトップ VR ヘッドセットは、 [unreal Engine の組み込み OpenXR プラグイン](https://github.com/microsoft/Microsoft-OpenXR-Unreal)を通じて利用できるようになりました。  Unreal Engine 4.26 は、OpenXR 拡張機能プラグインの最初のセットにも同梱されています。これにより、手動での対話と HP リバーブ G2 コントローラーのサポートが可能になり、 [HoloLens 2 および Windows Mixed Reality ヘッドセットの全機能セット](#roadmap)を利用できるようになります。  Unreal Engine 4.26 は、今年の後半で公開されている [エピックゲームランチャー](https://www.unrealengine.com/download/creators)のプレビューで現在ご利用いただけます。  OpenXR のサポートも、そのリリースと共に使用できるようになります。 MRTK-Unreal


### <a name="openxr-for-native-development"></a>ネイティブ開発用の OpenXR

HoloLens 2 で OpenXR を使用するか、デスクトップで Windows Mixed Reality イマーシブ ヘッドセットを使用して開発できます。  ヘッドセットへのアクセス権がない場合は、代わりに HoloLens 2 エミュレーターまたは Windows Mixed Reality シミュレーターを使用できます。

HoloLens 2 またはイマーシブ Windows Mixed Reality ヘッドセットの OpenXR アプリケーションの開発を開始するには、「 [OpenXR development の使用を開始する方法](openxr-getting-started.md)」を参照してください。

OpenXR API の主要なコンポーネントと、OpenXR を使用した実際のアプリケーションの例については、こちらの60分のチュートリアルビデオをご覧ください。

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="see-also"></a>関連項目

* <a href="https://www.khronos.org/openxr/" target="_blank">OpenXR の詳細情報</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 仕様</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">OpenXR 1.0 API リファレンス</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">OpenXR 1.0 クイックリファレンスガイド</a>
