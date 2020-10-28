---
title: OpenXR
description: ポータブル OpenXR API 標準を使用してエンジンをビルドし、Windows Mixed Reality と HoloLens 2 ヘッドセットに展開します。
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、ネイティブ、ネイティブアプリ、カスタムエンジン、ミドルウェア
ms.openlocfilehash: 4822f0d6c413b68c19894cf42a456808ffd894b9
ms.sourcegitcommit: d063c767117c055dc5d40c2bd5a680728fca95fb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2020
ms.locfileid: "92886860"
---
# <a name="openxr"></a>OpenXR

<img align="right" src="images/openxr.png" alt="OpenXR logo">

OpenXR は、 <a href="https://www.khronos.org/" target="_blank">Khronos</a> のオープンなロイヤリティフリー API 標準です。これにより、さまざまなベンダーの幅広いデバイスにエンジンがネイティブでアクセスできるようになり、 [混合現実](../../discover/mixed-reality.md)の範囲を超えています。

HoloLens 2 で OpenXR を使用するか、デスクトップで Windows Mixed Reality イマーシブ ヘッドセットを使用して開発できます。  ヘッドセットへのアクセス権がない場合は、代わりに HoloLens 2 エミュレーターまたは Windows Mixed Reality シミュレーターを使用できます。

## <a name="why-openxr"></a>OpenXR の理由

OpenXR を使用すると、holographic デバイス (HoloLens 2 など) の両方を対象とするエンジンを構築して、実際の世界にデジタルコンテンツを配置することができます。また、デスクトップ Pc 用の Windows Mixed Reality ヘッドセットと同様に、物理的な世界を隠し、デジタル体験で置き換えることもできます。  OpenXR を使用すると、さまざまなハードウェアプラットフォームで移植可能なコードを一度記述できます。

OpenXR API は、アプリケーションをヘッドセットのネイティブプラットフォームサポートに直接接続するローダーを使用します。  これにより、エンドユーザーは、Windows Mixed Reality ヘッドセットとその他のヘッドセットのどちらを使用しているかにかかわらず、最大のパフォーマンスと最小待機時間を実現できます。

## <a name="what-is-openxr"></a>OpenXR とは

OpenXR API は、コアの予測、フレームのタイミング、および空間入力の機能を提供します。これは、HoloLens 2 のような holographic デバイスと、Windows Mixed Reality ヘッドセットのようなイマーシブデバイスの両方を対象とするエンジンを構築するために必要です。

OpenXR API の詳細については、OpenXR 1.0 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">仕様</a>、 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API リファレンス</a> 、および <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">クイックリファレンスガイド</a>を参照してください。  詳細については、 <a href="https://www.khronos.org/openxr/" target="_blank">Khronos OpenXR のページ</a>を参照してください。

HoloLens 2 の全機能セットを対象にするには、クロスベンダおよびベンダー固有の OpenXR 拡張機能を使用します。これにより、OpenXR 1.0 コア以外の追加機能が可能になります。これには、トレーラーによる追跡、視線追跡、空間マッピング、空間アンカーなどがあります。  今年の後半に登場する拡張機能の詳細については、後の [「ロードマップ」セクション](#roadmap) を参照してください。

OpenXR は、それ自体が mixed reality エンジンではないことに注意してください。  代わりに、OpenXR では、Unity や Unreal などのエンジンがポータブルコードを一度記述できるようになります。これにより、そのプラットフォームを構築したベンダーに関係なく、ユーザーの holographic またはイマーシブデバイスのネイティブプラットフォーム機能にアクセスできます。

## <a name="roadmap"></a>ロードマップ

OpenXR 仕様では、ランタイム実装者が<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Base OpenXR 1.0 仕様</a>で定義されている[コア機能](#what-is-openxr)以外の機能を公開できるようにする拡張機構を定義しています。

OpenXR 拡張機能には、次の3種類があります。
* **ベンダー拡張機能 (例 `MSFT` :):** ハードウェアまたはソフトウェアの機能でベンダーごとのイノベーションを実現します。  任意のランタイムベンダは、いつでもベンダ拡張機能を導入および出荷できます。
  * **試験的なベンダーの拡張機能 (例 `MSFT_preview` :):** フィードバックを収集するためにプレビューされている試験的なベンダーの拡張機能。  `MSFT_preview` 拡張機能は開発者向けデバイスのみを対象としており、実際の拡張機能が出荷されると削除されます。  試してみるには、 [開発者デバイスでプレビュー拡張機能を有効に](openxr-getting-started.md#using-preview-extensions)します。
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
| 他の HoloLens Sdk との相互運用<br />(例: [QR](../platform-capabilities-and-apis/qr-code-tracking.md))<p>*HoloLens 2 のみ*</p> | **`MSFT` ランタイム102でリリースされた拡張機能:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code> |
| [Mixed Reality キャプチャ <br /> (PV カメラからの3番目のレンダリング)](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*HoloLens 2 のみ*</p> | **`MSFT` ランタイム102でリリースされた拡張機能:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_secondary_view_configuration">XR_MSFT_secondary_view_configuration</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_first_person_observer">XR_MSFT_first_person_observer</a></code> |
| UWP CoreWindow API との相互運用<br />(例: キーボード/マウス) | **`MSFT_preview`[プレビューランタイム 102](openxr-getting-started.md#using-preview-extensions)の拡張機能:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_holographic_window_attachment_preview">XR_MSFT_holographic_window_attachment_preview</a></code><p>**`MSFT` プレビュー版の拡張機能** : 2020 年8月 *(計画済み)*</p>
| [モーションコントローラーレンダリングモデル](../../design/motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT_preview`[プレビューランタイム](openxr-getting-started.md#using-preview-extensions)の拡張機能:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_controller_model_preview">XR_MSFT_controller_model_preview</a></code><p>**`MSFT` プレビュー版の拡張機能** : 2020 年9月 *(計画)*</p> |
| [シーンの理解 (平面、メッシュ)](../../design/scene-understanding.md)<p>*HoloLens 2 のみ*</p> | <p>**[プレビューのランタイム 102](openxr-getting-started.md#using-preview-extensions):**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code>シーンで[SDK](../platform-capabilities-and-apis/scene-understanding-sdk.md)を使用して使用する</p><p>**`MSFT_preview` 将来のプレビューランタイムの拡張機能** *(計画済み)*</p> |
| その他のクロスベンダ拡張機能 | <p>**正式な拡張機能がリリースされました `KHR` :**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><p>**`EXT` リリースされた拡張機能:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code> |

これらの拡張機能の一部はベンダー固有の拡張機能として開始される場合があり `MSFT` ますが、Microsoft およびその他の OpenXR runtime ベンダーは、 `EXT` `KHR` これらの機能領域の多くに対してクロスベンダーまたは拡張機能を設計するために連携しています。  これにより、コア仕様と同様に、これらの機能用に記述したコードをランタイムベンダー間で移植可能にすることができます。

## <a name="get-started-with-openxr"></a>OpenXR で作業を始める

HoloLens 2 で OpenXR を使用するか、デスクトップで Windows Mixed Reality イマーシブ ヘッドセットを使用して開発できます。  ヘッドセットへのアクセス権がない場合は、代わりに HoloLens 2 エミュレーターまたは Windows Mixed Reality シミュレーターを使用できます。

HoloLens 2 またはイマーシブ Windows Mixed Reality ヘッドセットの OpenXR アプリケーションの開発を開始するには、「 [OpenXR development の使用を開始する方法](openxr-getting-started.md)」を参照してください。

OpenXR API の主要なコンポーネントと、OpenXR を使用した実際のアプリケーションの例については、こちらの60分のチュートリアルビデオをご覧ください。

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="see-also"></a>関連項目

* <a href="https://www.khronos.org/openxr/" target="_blank">OpenXR の詳細情報</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 仕様</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">OpenXR 1.0 API リファレンス</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">OpenXR 1.0 クイックリファレンスガイド</a>
