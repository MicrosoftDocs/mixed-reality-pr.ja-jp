---
title: 開発者向け複合現実キャプチャ
description: 開発者向けの mixed reality キャプチャを有効化、使用、および表示するためのベストプラクティスについて説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc、写真、ビデオ、キャプチャ、カメラ
ms.openlocfilehash: 88b31d139f01c6cbe0567203e39f7640270f7716
ms.sourcegitcommit: e24715fffa815c24ca411fa93eed9576ae729337
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2021
ms.locfileid: "98247725"
---
# <a name="mixed-reality-capture-for-developers"></a>開発者向け複合現実キャプチャ

> [!NOTE]
> HoloLens 2 の新しい MRC 機能に関するガイダンスについては、以下の [PV カメラのレンダー](#render-from-the-pv-camera-opt-in) に関する説明を参照してください。

[Mixed reality キャプチャ](../../mixed-reality-capture.md)(MRC) の写真またはビデオをいつでも実行できますが、アプリケーションの開発時に注意すべき点はほとんどありません。 これには、MRC ビジュアル品質のベストプラクティスと、MRCs のキャプチャ中にシステムの変更に応答するためのベストプラクティスが含まれています。

開発者は、混合現実のキャプチャと挿入をシームレスにアプリに統合することもできます。

HoloLens の MRC (最初世代) では、720p までのビデオと写真がサポートされています。 HoloLens 2 の MRC では、最大1080p および最大4K 解像度までのビデオがサポートされています。

## <a name="the-importance-of-quality-mrc"></a>品質の MRC の重要性

Microsoft Store のページ上に mixed reality スクリーンショットがあるか、またはソーシャルネットワークでキャプチャコンテンツを共有する他のユーザーであるかにかかわらず、Mixed Reality キャプチャメディアは多くの場合、ユーザーがアプリに最初にさらされます。 MRC を使用して、アプリをデモし、ユーザーを教育し、世界中の対話を共有するようユーザーに促すことができます。また、ユーザーの調査や問題の解決にも対応できます。

## <a name="how-mrc-impacts-your-app"></a>MRC がアプリに与える影響

### <a name="enabling-mrc-in-your-app"></a>アプリでの MRC の有効化

既定では、アプリは、ユーザーが混合現実のキャプチャを実行できるようにするために何も行う必要はありません。

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>アプリでの MRC のアラインメントの向上を可能にする

既定では、mixed reality キャプチャは、右目の holographic 出力と写真/ビデオ (PV) カメラを結合します。 この2つのソースは、現在実行中のイマーシブアプリによって設定されたフォーカスポイントを使用して結合されます。

これは、PV カメラと右ディスプレイの間に物理的な距離があるため、フォーカス平面外のホログラムが配置されないことを意味します。

#### <a name="set-the-focus-point"></a>フォーカスポイントを設定する

イマーシブアプリ (HoloLens) では、安定化平面を使用する場所の [フォーカスポイント](../unity/focus-point-in-unity.md) を設定する必要があります。 これにより、ヘッドセットと mixed reality キャプチャの両方で最適なアラインメントが実現されます。

フォーカスポイントが設定されていない場合、安定化平面の既定値は2メートルになります。

#### <a name="render-from-the-pv-camera-opt-in"></a>PV カメラからのレンダリング (オプトイン)

HoloLens 2 では、mixed reality キャプチャが実行されている間に、アプリが **PV カメラからレンダリング** する機能を追加します。 アプリで追加のレンダリングが正しくサポートされるようにするには、アプリでこの機能を有効にする必要があります。

PV カメラからのレンダリングでは、既定の MRC エクスペリエンスに対して次の点が改善されています。
* 物理的な環境に対するホログラムのアラインメントとほぼ相互作用のための手は、すべての距離で正確である必要があります。 既定の MRC で見られるように、フォーカスポイント以外の距離にオフセットを設定しないようにします。
* ヘッドセットの右目は、MRC 出力のホログラムをレンダリングするために使用されないため、侵害されることはありません。

PV カメラからのレンダリングを有効にするには、次の3つの手順を実行します。
1. PhotoVideoCamera HolographicViewConfiguration を有効にする
2. 追加の HolographicCamera render を処理する
3. この追加の HolographicCamera からシェーダーとコードが正しくレンダリングされることを確認します。

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-directx"></a>DirectX で PhotoVideoCamera HolographicViewConfiguration を有効にする

PV カメラからの表示をオプトインするには、アプリで PhotoVideoCamera の [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration)を有効にするだけです。
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfigurationKind.PhotoVideoCamera);
if (view != null)
{
    view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>DirectX で追加の HolographicCamera render を処理する

アプリが PV カメラから表示するオプトインを持っていて、mixed reality キャプチャが開始される場合:
1. HolographicSpace の CameraAdded イベントが発生します。 このイベントは、アプリがこの時点でカメラを処理できない場合に遅延する可能性があります。
2. 未処理の遅延がない状態でイベントが完了すると、HolographicCamera は次の HolographicFrame の AddedCameras の一覧に表示されます。

Mixed reality キャプチャが停止した場合 (または、mixed reality キャプチャが実行されているときにアプリがビューの構成を無効にした場合)、次の HolographicFrame の RemovedCameras の一覧に HolographicCamera が表示され、HolographicSpace の CameraRemoved イベントが発生します。

HolographicCamera に [viewconfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) プロパティが追加され、カメラが属している構成を識別できるようになりました。

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unity"></a>Unity で PhotoVideoCamera HolographicViewConfiguration を有効にする

> [!NOTE]
> これには、 **unity 2018.4.13 f1**、 **unity 2019.3.0 f1**、またはそれ以降が必要です。

[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)を使用しているときに、pv カメラからの表示をオプトインするには、 [Windows Mixed reality カメラ設定](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/CameraSystem/WindowsMixedRealityCameraSettings.html)プロバイダーを有効にし、 **pv カメラからのレンダー** をオンにします。

Mixed Reality Toolkit を使用していない場合は、コンポーネントを使用して、DirectX 用に前述したように [手動でオプトイン](#enable-the-photovideocamera-holographicviewconfiguration-in-directx) できます。

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>Unity で追加の HolographicCamera render を処理する

これは Unity によって自動的に行われます。

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unreal"></a>Unreal で PhotoVideoCamera HolographicViewConfiguration を有効にする

> [!NOTE]
> これには **Unreal Engine 4.25** 以降のバージョンが必要です。

PV カメラからの表示をオプトインするには、次のようにします。

1. **SetEnabledMixedRealityCamera** および **ResizeMixedRealityCamera** の呼び出し
    * **サイズ X** および **サイズ Y** の値を使用して、ビデオのディメンションを設定します。

![第 3 のカメラ](images/unreal-camera-3rd.PNG)

##### <a name="handle-the-additional-holographiccamera-render-in-unreal"></a>Unreal で追加の HolographicCamera render を処理する

これは、Unreal によって自動的に行われます。

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>シェーダーとコードがサポートする追加のカメラを確認する

Mixed reality キャプチャを実行し、異常な配置、コンテンツ不足、またはパフォーマンスの問題がないか確認します。 必要に応じてシェーダーとコードを更新します。

追加のカメラへのレンダリングをサポートできない特定のシーンがある場合は、PhotoVideoCamera の HolographicViewConfiguration を無効にすることができます。

### <a name="disabling-mrc-in-your-app"></a>アプリでの MRC の無効化

#### <a name="2d-app"></a>2D アプリ

次の方法で混合の現実のキャプチャを実行すると、2D アプリでビジュアルコンテンツを非表示にすることができます。
* [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present)フラグと共に存在する
* [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag)フラグを使用してアプリのスワップチェーンを作成する
* Windows 10 5 月2019更新プログラムで、ApplicationView の[IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)を設定します。

#### <a name="immersive-app"></a>イマーシブアプリ

イマーシブアプリでは、複合現実のキャプチャからビジュアルコンテンツを除外することを選択できます。
* HolographicCameraRenderingParameter の [Iscontentprotectionenabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) を設定して、関連付けられているフレームに対して mixed reality キャプチャを無効にしています
* HolographicCamera の [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) を設定して、関連付けられている holographic カメラの mixed reality キャプチャを無効にする

#### <a name="password-keyboard"></a>パスワードキーボード

Windows 10 5 月2019更新プログラムでは、パスワードまたは pin キーボードが表示されたときに、ビジュアルコンテンツが mixed reality キャプチャから自動的に除外されます。

### <a name="knowing-when-mrc-is-active"></a>MRC がアクティブであることを把握しています

アプリで [Appcapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture) クラスを使用すると、システムの混合現実のキャプチャが実行されているかどうかを知ることができます (オーディオまたはビデオのいずれか)。

>[!NOTE]
>デバイスで混合 reality キャプチャを利用できない場合、AppCapture の [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API は null を返すことがあります。 アプリが中断されたときに CapturingChanged イベントの登録を解除することも重要です。それ以外の場合、MRC はブロックされた状態になります。

### <a name="best-practices-hololens-specific"></a>ベストプラクティス (HoloLens 固有)

MRC は開発作業を追加せずに動作することが期待されていますが、最適な mixed reality キャプチャエクスペリエンスを提供するには、いくつかの点に注意する必要があります。

**MRC は、ホログラムのアルファチャネルを使用して、 [カメラ](locatable-camera.md) の画像とブレンドします。**

最も重要な手順は、アプリが不透明な黒にクリアするのではなく、透明な黒にクリアされるようにすることです。 Unity では、これは既定で MixedRealityToolkit を使用して実行されます。 Unity 以外で開発している場合は、1行の変更が必要になることがあります。

以下は、アプリが透明な黒にクリアされていない場合に、MRC に表示される可能性のあるアイテムの一部です。

**エラーの例**: コンテンツの周囲に黒い端がある (透明な黒にクリアできない)

<table>
<tr>
<td>
<img src="images/chessboardblackedges-300px.jpg" alt="Failure to clear to transparent black: black edge artifacts around holograms"/>
</td>
<td>
<img src="images/fieldblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
</tr>
</table>

**失敗の例**: ホログラムの背景シーン全体が黒で表示されます。 背景のアルファ値を1つに設定すると、黒の背景になります

![背景のアルファ値1を設定すると、背景が黒になります。](images/clearopaqueblack-300px.png)

**期待される結果**: ホログラムが現実の世界と適切にブレンドされている (透明な黒に消去する場合は予期される結果)

![透過的な黒に消去する場合に予期される結果](images/cleartransparentblack-300px.png)

**解決策**:
* アルファ値を0にするために、不透明な黒で表示されているコンテンツを変更します。
* アプリが透明な黒にクリアされていることを確認します。
* Unity の既定値は MixedRealityToolkit で自動的にクリアされますが、Unity 以外のアプリの場合は、ID3D11DeiceContext:: ClearRenderTargetView () で使用される色を変更する必要があります。 不透明な黒 (0、0、0、1) ではなく、透明な黒 (0、0、0、0) であることを確認する必要があります。

必要に応じてアセットのアルファ値を調整できるようになりましたが、通常は必要ありません。 ほとんどの場合、MRCs はすぐに使えるように見えます。 MRC は、前乗算したアルファを前提としています。 アルファ値は、MRC キャプチャにのみ影響します。

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>HoloLens が HoloLens で有効になっている場合に予期されること

以下は、特に明記されていない限り、HoloLens (第1世代) と HoloLens 2 の両方に適用されます。

* システムは、アプリケーションを 30 Hz でレンダリングするように調整します。 これにより、MRC を実行するためのヘッドルームが作成されるため、アプリは一定の予算予約を維持する必要がなく、30 fps の MRC ビデオレコードレートにも一致します。
* デバイスの右上にあるホログラムコンテンツは、録画/ストリーミングの場合、"スパーク" と表示されることがあります。テキストが読みにくくなり、ホログラムの端がより jaggy に見える可能性があります ( **HoloLens 2** で3番目のカメラのレンダリングをオプトインすると、この侵害が回避されます)。
* アプリケーションで有効になっている場合、MRC の写真やビデオによってアプリケーションの [フォーカスポイント](../unity/focus-point-in-unity.md) が尊重されます。これにより、ホログラムが正確に配置されます。 ビデオの場合、フォーカスポイントが滑らかになるため、フォーカスポイントの深さが大幅に変化した場合に、ホログラムが徐々にずれて表示されることがあります。 フォーカスポイントと異なる深さにあるホログラムは、実際の世界からのオフセットとして表示されることがあります (下の例を参照してください。フォーカスポイントが2メートルで設定されていますが、ホログラムは1メーターに配置されています)。

![2メートルのホログラムは、世界に完全に登録されます。 クローズまたは遠くの距離にあるホログラムは、若干オフセットする場合があります。](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>アプリ内からの MRC 機能の統合

混合の現実アプリでは、アプリ内から MRC 写真またはビデオキャプチャを開始できます。キャプチャされたコンテンツは、デバイスの "カメラロール" に格納されていなくてもアプリで利用できます。 カスタムの MRC レコーダーを作成することも、組み込みのカメラキャプチャ UI を利用することもできます。 

### <a name="mrc-with-built-in-camera-ui"></a>組み込みのカメラ UI を使用した MRC

開発者は、 *[カメラキャプチャ UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* を使用して、わずか数行のコードでユーザーがキャプチャした mixed reality の写真またはビデオを取得できます。

この API は組み込みの MRC カメラ UI を起動します。ユーザーは、写真やビデオを撮影し、結果として得られたキャプチャをアプリに返すことができます。 独自のカメラ UI または低レベルのアクセスをキャプチャストリームに追加する必要がある場合は、カスタム Mixed Reality キャプチャレコーダーを作成できます。

### <a name="creating-a-custom-mrc-recorder"></a>カスタム MRC レコーダーの作成

ユーザーは常にシステム MRC キャプチャサービスを使用して写真またはビデオをトリガーできますが、アプリケーションでは、MRC と同様にカメラストリームにホログラムを含むカスタムカメラアプリをビルドすることができます。 これにより、アプリケーションは、ユーザー入力からキャプチャを開始したり、カスタムの記録 UI を作成したり、MRC 設定をカスタマイズしていくつかの例に名前を設定したりできます。

**HoloStudio は、MRC 効果を使用してカスタム MRC カメラを追加します**

![HoloStudio は、MRC 効果を使用してカスタム MRC カメラを追加します](images/cameraiconholostudio-300px.jpg)

Unity アプリケーションでは、プロパティの [Locatable_camera_in_Unity](../unity/locatable-camera-in-unity.md) が表示され、ホログラムが有効になります。

その他のアプリケーションでは、 [Windows Media Capture api](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) を使用してカメラを制御し、ビデオとオーディオ効果を追加して、仮想ホログラムとアプリケーションオーディオを静止画やビデオに含めることができます。

アプリケーションには、効果を追加するためのオプションが2つあります。
* 以前の API: [MediaCapture. AddEffectAsync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync) 。
* 新しい Microsoft 推奨 API (オブジェクトを返し、動的プロパティを操作できるようにします)。 MediaCapture [MediaCapture](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync)() は、  /  [](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync)アプリが[IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition)と[IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition)の独自の実装を作成する必要があることを必要としますが、これに該当します。 例については、 [MRC サンプルアプリ](https://github.com/microsoft/Windows-universal-samples/tree/master/Samples/HolographicMixedRealityCapture) を参照してください。

>[!NOTE]
> MixedRealityCapture 名前空間は Visual Studio で認識されませんが、文字列はまだ有効です。

MRC ビデオ効果 (**MixedRealityCapture. MixedRealityCaptureVideoEffect**)

|  プロパティ名  |  Type  |  既定値  |  説明 |
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([Mediastreamtype](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))  |  1 (VideoRecord)  |  この効果がどのキャプチャストリームに使用されるかを説明します。 オーディオは使用できません。 |
|  HologramCompositionEnabled  |  boolean  |  TRUE  |  ビデオキャプチャのホログラムを有効または無効にするフラグ。 |
|  RecordingIndicatorEnabled  |  boolean  |  TRUE  |  ホログラムのキャプチャ中に画面の記録インジケーターを有効または無効にするフラグ。 |
|  VideoStabilizationEnabled  |  boolean  |  FALSE  |  HoloLens トラッカーを使用して、ビデオの安定化を有効または無効にするフラグ。 |
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  ビデオ安定化に使用する履歴フレームの数を設定します。 0は待機時間が0で、電源とパフォーマンスの観点からはほぼ "無料" です。 最大品質には15が推奨されます (待機時間とメモリの15フレームのコスト)。 |
|  GlobalOpacityCoefficient  |  float  |  0.9 (HoloLens) 1.0 (イマーシブヘッドセット)  |  0.0 (完全に透明) から 1.0 (完全に不透明) までの範囲内のホログラムのグローバル不透明度係数を設定します。 |
|  BlankOnProtectedContent  |  boolean  |  FALSE  |  保護されたコンテンツを示す 2d UWP アプリがある場合に空のフレームを返すことを有効または無効にするフラグ。 このフラグが false で、2d UWP アプリで保護されたコンテンツが表示されている場合、2d UWP アプリはヘッドセットと mixed reality キャプチャの両方で保護されたコンテンツテクスチャに置き換えられます。 |
|  ShowHiddenMesh  |  boolean  |  FALSE  |  Holographic カメラの非表示領域メッシュと隣接するコンテンツの表示を有効または無効にするフラグ。 |
| OutputSize | サイズ | 0, 0 | ビデオの安定化のトリミング後に、目的の出力サイズを設定します。 0または無効な出力サイズが指定されている場合は、既定のトリミングサイズが選択されます。 |
| PreferredHologramPerspective | UINT32 | Windows デバイスポータルでの **カメラ設定からのレンダリング** | キャプチャする holographic カメラビューの構成を示すために使用される列挙: 0 (ディスプレイ) は、アプリが写真/ビデオカメラからのレンダリングを要求されないことを意味します。 1 (PhotoVideoCamera) は、アプリが写真/ビデオカメラからレンダリングするように要求します (アプリがサポートしている場合)。 HoloLens 2 でのみサポートされます |

>[!NOTE]
> Windows デバイスポータルで **PreferredHologramPerspective** の既定値を変更するには、[ [Mixed Reality Capture] ページ](using-the-windows-device-portal.md#mixed-reality-capture) に移動し、[ **カメラからのレンダリング**] をオフにします。 この設定は既定で **1 (PhotoVideoCamera)** に設定されていますが、 **0 (表示)** に設定することはできません。
>
> **PreferredHologramPerspective** の既定値は、2020年6月の更新プログラム (windows Holographic、バージョン2004ビルド19041.1106、windows Holographic、バージョン1903ビルド 18362.1064 **) より前** のバージョンです。

MRC オーディオ効果 (**MixedRealityCapture. MixedRealityCaptureAudioEffect**)

| プロパティ名 | Type | 既定値 | 説明 |
|----------|----------|----------|----------|
| MixerMode | UINT32 | 2 (Mic とシステムオーディオ) | 使用するオーディオソースを示すために使用する列挙: 0 (Mic オーディオのみ)、1 (システムオーディオのみ)、2 (Mic およびシステムオーディオ) |
| LoopbackGain | float | Windows デバイスポータルでの **アプリオーディオゲイン** 設定 | システムオーディオボリュームに適用します。 範囲は 0.0 ~ 5.0 です。 HoloLens 2 でのみサポートされます |
| マイクロ電話の獲得 | float | Windows デバイスポータルでの **Mic オーディオゲイン** 設定 | Mic ボリュームに適用します。 範囲は 0.0 ~ 5.0 です。 HoloLens 2 でのみサポートされます |

>[!NOTE]
> Windows デバイスポータルでは、[ [Mixed Reality Capture] ページ](using-the-windows-device-portal.md#mixed-reality-capture)に移動し、それぞれの設定の横にあるスライダーを調整することにより、 **LoopbackGain** または **マイクロホップゲイン** の既定値を変更できます。 どちらの設定も既定で **1.0** に設定されていますが、 **0.0** から **5.0** までの任意の値に設定できます。
>
> Windows デバイスポータルを使用して既定のゲイン値を構成するには、2020年6月の更新プログラム (Windows Holographic、バージョン2004ビルド19041.1106、Windows Holographic、バージョン1903ビルド 18362.1064) が追加されました。

### <a name="simultaneous-mrc-limitations"></a>同時の MRC の制限事項

複数のアプリが同時に MRC にアクセスする場合は、特定の制限事項に注意する必要があります。

#### <a name="photovideo-camera-access"></a>写真/ビデオカメラへのアクセス

HoloLens 1 では、プロセスがビデオを録画したり写真を撮影したりしている間、MRC は写真のキャプチャやビデオのキャプチャに失敗します。 また、この逆も当てはまります。 MRC が実行されている場合、アプリケーションはカメラへのアクセスを取得できません。 

HoloLens 2 では、カメラへのアクセスを共有できます。 解像度やフレームレートを直接制御する必要がない場合は、 [Sharedmode プロパティ](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041) を sharedmode として使用して MediaCapture を初期化できます。  

##### <a name="built-in-mrc-photovideo-camera-access"></a>組み込みの MRC フォト/ビデオカメラアクセス

Windows 10 に組み込まれた MRC 機能 (Cortana、スタートメニュー、ハードウェアショートカット、Miracast、Windows デバイスポータル):

* 既定では ExclusiveControl を使用して実行されます

ただし、のサポートは、共有モードで動作するために、MRC サブシステムに追加されています。 

* アプリが写真/ビデオカメラへの ExclusiveControl アクセスを要求した場合、組み込みの MRC は、アプリの要求が成功するように、写真/ビデオカメラの使用を自動的に停止します。 
* アプリの ExclusiveControl 中に作成された MRC が開始された場合、組み込みの MRC は SharedReadOnly モードで実行されます 

この共有モード機能には、いくつかの制限があります。

* Cortana、ハードウェアショートカット、または [スタート] メニューを使用した写真: Windows 10 April 2018 更新プログラム (またはそれ以降) が必要
* Cortana、ハードウェアショートカット、または [スタート] メニューを使用したビデオ: Windows 10 April 2018 更新プログラム (またはそれ以降) が必要です。
* Miracast 経由のストリーミング MRC: Windows 10 10 月2018更新プログラム (またはそれ以降) が必要です。
* Windows デバイスポータルまたは HoloLens コンパニオンアプリを使用したストリーミング MRC: HoloLens 2 が必要です

>[!NOTE]
> 別のアプリが写真/ビデオカメラを使用している場合、組み込みの MRC カメラ UI の解像度とフレームレートは通常の値から小さくなることがあります。

#### <a name="mrc-access-for-developers"></a>開発者向けの MRC アクセス

MRC を使用する場合は、常にカメラに排他的な制御を要求することをお勧めします。 これにより、上記の制限事項を認識している限り、アプリケーションはカメラの設定を完全に制御できます。 

* [初期化設定](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings?view=winrt-19041)を使用してメディアキャプチャオブジェクトを作成する
* [Sharingmode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#Windows_Media_Capture_MediaCaptureInitializationSettings_SharingMode)プロパティを **exclusive** に設定します。

> [!CAUTION]
> 続行する前に、 [「Sharingmode の解説」](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#remarks) をよくお読みください。

* カメラを希望どおりにセットアップする
* アプリを起動し、start API でビデオフレームをキャプチャして、MRC を有効にします

> [!CAUTION]
> アプリを開始する前に、MRC を開始した場合、機能が期待どおりに動作することを保証できません。

上記のプロセスの完全なサンプルについては、 [holographic face tracking サンプル](https://docs.microsoft.com/samples/microsoft/windows-universal-samples/holographicfacetracking)を参照してください。

> [!NOTE]
> Windows 10 の2018年4月に更新される前は、アプリのカスタム MRC レコーダーはシステム MRC と同時に使用できませんでした (写真をキャプチャする、ビデオをキャプチャする、または Windows デバイスポータルからストリーミングする)。

## <a name="see-also"></a>関連項目

* [複合現実キャプチャ](../../mixed-reality-capture.md)
* [Spectator View](spectator-view.md)
* [Unity 開発の概要](../unity/unity-development-overview.md)
* [Unreal 開発の概要](../unreal/unreal-development-overview.md)
