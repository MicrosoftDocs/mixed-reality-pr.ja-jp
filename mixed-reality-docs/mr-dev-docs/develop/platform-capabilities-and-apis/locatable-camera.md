---
title: 場所を特定できるカメラ
description: HoloLens のフロント接続カメラに関する一般的な情報、そのしくみ、および開発者が使用できるプロファイルと解決方法について説明します。
author: cdedmonds
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: カメラ、hololens、カラーカメラ、フロント接続、hololens 2、cv、コンピュータービジョン、基準、マーカー、qr コード、qr、写真、ビデオ
ms.openlocfilehash: f34973fee56f9469632b320a62dd441ed32e5805
ms.sourcegitcommit: 63b7f6d5237327adc51486afcd92424b79e6118b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2021
ms.locfileid: "98810152"
---
# <a name="locatable-camera"></a>場所を特定できるカメラ

HoloLens には、デバイスの前面に取り付けられている世界中のカメラが搭載されています。これにより、アプリはユーザーに表示される内容を確認できます。 スマートフォン、ノートブック、またはデスクトップのカラーカメラの場合と同じように、開発者はカメラのアクセスと制御を行うことができます。 モバイルおよびデスクトップで動作する同じユニバーサル windows [media capture](/uwp/api/Windows.Media.Capture.MediaCapture) および windows Media foundation Api が HoloLens で動作します。 Unity は、HoloLens でカメラの使用機能を抽象化するために、 [これらの Windows api をラップ](../unity/locatable-camera-in-unity.md) しています。 機能のタスクには、通常の写真やビデオを (ホログラムの有無にかかわらず) 撮影したり、カメラの位置をシーン上で検索したりする作業が含まれます。

## <a name="device-camera-information"></a>デバイスカメラ情報

### <a name="hololens-first-generation"></a>HoloLens (最初世代)

* 自動白バランス、自動露出、および完全なイメージ処理パイプラインを使用して、フォーカスされたフォト/ビデオ (PV) カメラを修正します。
* 世界中のホワイトプライバシー LED は、カメラがアクティブになるたびに点灯します
* カメラは、30、24、20、15、および 5 fps で、次のモード (すべてのモードが16:9 の縦横比) をサポートしています。

  |  ビデオ  |  プレビュー  |  それでもなお  |  ビューの水平方向のフィールド (H 視界) |  推奨される使用方法 | 
  |----------|----------|----------|----------|----------|
  |  1280 x 720 |  1280 x 720 |  1280 x 720 |  45度  |  (ビデオ安定化を使用した既定のモード) | 
  |  N/A |  N/A |  2048x1152 |  67度 |  高解像度の静止画像 | 
  |  1408x792 |  1408x792 |  1408x792 |  48度 |  ビデオ安定化前のオーバースキャン (埋め込み) 解像度 | 
  |  1344x756 |  1344x756 |  1344x756 |  67度 |  オーバースキャンによる大規模な視界のビデオモード | 
  |  896x504 |  896x504 |  896x504 |  48度 |  イメージ処理タスクの低電力/低解像度モード | 

### <a name="hololens-2"></a>HoloLens 2

* 自動ホワイトバランス、自動露出、完全な画像処理パイプラインを使用して、写真/ビデオ (PV) カメラを自動フォーカスします。
* 世界中のホワイトプライバシー LED は、カメラがアクティブになるたびに点灯します。
* HoloLens 2 では、さまざまなカメラプロファイルがサポートされています。 [カメラの機能を検出して選択](/windows/uwp/audio-video-camera/camera-profiles)する方法について説明します。
* カメラでは、次のプロファイルと解像度がサポートされています (すべてのビデオモードは16:9 縦横比です)。
  
  | [プロファイル]                                         | ビデオ     | プレビュー   | それでもなお     | フレーム レート | ビューの水平方向のフィールド (H 視界) | 推奨される使用方法                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | Legacy、0 BalancedVideoAndPhoto、100             | 2272x1278 | 2272x1278 |           | 15.30       | 64.69                            | 高画質のビデオ記録                |
  | Legacy、0 BalancedVideoAndPhoto、100             | 896x504   | 896x504   |           | 15.30       | 64.69                            | 高品質な写真キャプチャのためのプレビューストリーム |
  | Legacy、0 BalancedVideoAndPhoto、100             |           |           | 3904x2196 |             | 64.69                            | 高品質な写真キャプチャ                  |
  | BalancedVideoAndPhoto、120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15.30       | 64.69                            | 長期間のシナリオ                     |
  | BalancedVideoAndPhoto、120                       | 1504x84 6  | 1504x84 6  |           | 15.30       | 64.69                            | 長期間のシナリオ                     |
  | ビデオ会議、100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15、30、60    | 64.69                            | ビデオ会議、長期間のシナリオ |
  | ビデオ会議、100                           | 1504x84 6  | 1504x84 6  |           | 5、15、30、60  | 64.69                            | ビデオ会議、長期間のシナリオ |
  | ビデオ会議、100 BalancedVideoAndPhoto、120 | 1920 x 1080 | 1920 x 1080 | 1920 x 1080 | 15、30       | 64.69                            | ビデオ会議、長期間のシナリオ |
  | ビデオ会議、100 BalancedVideoAndPhoto、120 | 1280 x 720  | 1280 x 720  | 1280 x 720  | 15、30       | 64.69                            | ビデオ会議、長期間のシナリオ |
  | ビデオ会議、100 BalancedVideoAndPhoto、120 | 1128x636  |           |           | 15、30       | 64.69                            | ビデオ会議、長期間のシナリオ |
  | ビデオ会議、100 BalancedVideoAndPhoto、120 | 960 x 540   |           |           | 15、30       | 64.69                            | ビデオ会議、長期間のシナリオ |
  | ビデオ会議、100 BalancedVideoAndPhoto、120 | 760x428   |           |           | 15、30       | 64.69                            | ビデオ会議、長期間のシナリオ |
  | ビデオ会議、100 BalancedVideoAndPhoto、120 | 640 x 360   |           |           | 15、30       | 64.69                            | ビデオ会議、長期間のシナリオ |
  | ビデオ会議、100 BalancedVideoAndPhoto、120 | 500x282   |           |           | 15、30       | 64.69                            | ビデオ会議、長期間のシナリオ |
  | ビデオ会議、100 BalancedVideoAndPhoto、120 | 424x240   |           |           | 15、30       | 64.69                            | ビデオ会議、長期間のシナリオ |

> [!NOTE]
> [混合 reality キャプチャ](/hololens/holographic-photos-and-videos)を利用して、アプリのビデオや写真を撮ることができます。これには、ホログラムやビデオの安定化が含まれます。
>
>開発者にとっては、顧客がコンテンツをキャプチャしたときに可能な限り、アプリを作成する際に考慮する必要がある考慮事項があります。 また、アプリ内で直接、mixed reality キャプチャを有効 (およびカスタマイズ) することもできます。 詳細につい [ては、「開発者向けの混合現実のキャプチャ」を](mixed-reality-capture-for-developers.md)参照してください。

## <a name="locating-the-device-camera-in-the-world"></a>デバイスカメラを世界中に配置する

HoloLens が写真やビデオを撮影する場合、キャプチャされたフレームには、世界中のカメラの位置とカメラのレンズモデルが含まれます。 これにより、アプリケーションは、イメージのシナリオを強化するために、実際の環境におけるカメラの位置を理解することができます。 開発者は、お気に入りのイメージ処理またはカスタムコンピュータービジョンライブラリを使用して、独自のシナリオを独創ロールできます。

HoloLens ドキュメントの他の場所にある "カメラ" は、"仮想ゲームカメラ" (アプリがレンダリングするための、視錐) を指している場合があります。 特に明記しない限り、このページの "カメラ" は実際の RGB カラーカメラを表します。

### <a name="using-unity"></a>Unity の使用

' CameraIntrinsics ' と ' CameraCoordinateSystem ' からアプリケーション/ワールド座標系に移行するには、 [Unity の検索カメラ](../unity/locatable-camera-in-unity.md) の記事に記載されている手順に従ってください。  CameraToWorldMatrix は PhotoCaptureFrame クラスによって自動的に提供されるため、以下で説明する CameraCoordinateSystem の変換について心配する必要はありません。

### <a name="using-mediaframereference"></a>MediaFrameReference の使用

これらの手順は、 [MediaFrameReference](/uwp/api/windows.media.capture.frames.mediaframereference) クラスを使用してカメラからイメージフレームを読み取る場合に適用されます。

各イメージフレーム (写真またはビデオ) には、キャプチャ時にカメラでルート化された[SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem)が含まれています。これには、 [MediaFrameReference](/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference)の[CoordinateSystem](/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem)プロパティを使用してアクセスできます。 各フレームには、カメラレンズモデルの説明が含まれています。このモデルは、 [CameraIntrinsics](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) プロパティにあります。 これらの変換は、ピクセルを生成した photons によって取得されたパスを表す3D 空間の光をピクセルごとに定義します。 これらの光線は、フレームの座標系から他の座標系 (例: [静止フレーム](../../design/coordinate-systems.md#stationary-frame-of-reference)から) への変換を取得することによって、アプリ内の他のコンテンツに関連付けることができます。 

各イメージフレームには次のものがあります。
* ピクセルデータ (RGB/NV12/JPEG/など)
* キャプチャの場所からの[SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem)
* カメラのレンズモードを含む [CameraIntrinsics](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) クラス

[HolographicFaceTracking サンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)は、カメラの座標系と独自のアプリケーション座標系との間の変換をクエリするための非常に簡単な方法を示しています。

### <a name="using-media-foundation"></a>メディアファンデーションの使用

カメラからイメージフレームを読み取るためにメディアファンデーション直接使用している場合は、次のサンプルコードに示すように、各フレームの [MFSampleExtension_CameraExtrinsics 属性](/windows/win32/medfound/mfsampleextension-cameraextrinsics) と [MFSampleExtension_PinholeCameraIntrinsics 属性](/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics) を使用して、アプリケーションの他の座標系を基準としたカメラフレームを見つけることができます。

```cpp
#include <winrt/windows.perception.spatial.preview.h>
#include <mfapi.h>
#include <mfidl.h>
 
using namespace winrt::Windows::Foundation;
using namespace winrt::Windows::Foundation::Numerics;
using namespace winrt::Windows::Perception;
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
 
class CameraFrameLocator
{
public:
    struct CameraFrameLocation
    {
        SpatialCoordinateSystem CoordinateSystem;
        float4x4 CameraViewToCoordinateSytemTransform;
        MFPinholeCameraIntrinsics Intrinsics;
    };
 
    std::optional<CameraFrameLocation> TryLocateCameraFrame(IMFSample* pSample)
    {
        MFCameraExtrinsics cameraExtrinsics;
        MFPinholeCameraIntrinsics cameraIntrinsics;
        UINT32 sizeCameraExtrinsics = 0;
        UINT32 sizeCameraIntrinsics = 0;
        UINT64 sampleTimeHns = 0;
 
        // query sample for calibration and validate
        if (FAILED(pSample->GetUINT64(MFSampleExtension_DeviceTimestamp, &sampleTimeHns)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_CameraExtrinsics, (UINT8*)& cameraExtrinsics, sizeof(cameraExtrinsics), &sizeCameraExtrinsics)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_PinholeCameraIntrinsics, (UINT8*)& cameraIntrinsics, sizeof(cameraIntrinsics), &sizeCameraIntrinsics)) ||
            (sizeCameraExtrinsics != sizeof(cameraExtrinsics)) ||
            (sizeCameraIntrinsics != sizeof(cameraIntrinsics)) ||
            (cameraExtrinsics.TransformCount == 0))
        {
            return std::nullopt;
        }
 
        // compute extrinsic transform
        const auto& calibratedTransform = cameraExtrinsics.CalibratedTransforms[0];
        const GUID& dynamicNodeId = calibratedTransform.CalibrationId;
        const float4x4 cameraToDynamicNode =
            make_float4x4_from_quaternion(quaternion{ calibratedTransform.Orientation.x, calibratedTransform.Orientation.y, calibratedTransform.Orientation.z, calibratedTransform.Orientation.w }) *
            make_float4x4_translation(calibratedTransform.Position.x, calibratedTransform.Position.y, calibratedTransform.Position.z);
 
        // update locator cache for dynamic node
        if (dynamicNodeId != m_currentDynamicNodeId || !m_locator)
        {
            m_locator = SpatialGraphInteropPreview::CreateLocatorForNode(dynamicNodeId);
            if (!m_locator)
            {
                return std::nullopt;
            }
 
            m_frameOfReference = m_locator.CreateAttachedFrameOfReferenceAtCurrentHeading();
            m_currentDynamicNodeId = dynamicNodeId;
        }
 
        // locate dynamic node
        auto timestamp = PerceptionTimestampHelper::FromSystemRelativeTargetTime(TimeSpan{ sampleTimeHns });
        auto coordinateSystem = m_frameOfReference.GetStationaryCoordinateSystemAtTimestamp(timestamp);
        auto location = m_locator.TryLocateAtTimestamp(timestamp, coordinateSystem);
        if (!location)
        {
            return std::nullopt;
        }
 
        const float4x4 dynamicNodeToCoordinateSystem = make_float4x4_from_quaternion(location.Orientation()) * make_float4x4_translation(location.Position());
 
        return CameraFrameLocation{ coordinateSystem, cameraToDynamicNode * dynamicNodeToCoordinateSystem, cameraIntrinsics };
    }

private:
    GUID m_currentDynamicNodeId{ GUID_NULL };
    SpatialLocator m_locator{ nullptr };
    SpatialLocatorAttachedFrameOfReference m_frameOfReference{ nullptr };
};
```

### <a name="distortion-error"></a>ディストーションエラー

HoloLens では、ビデオおよび静止画像ストリームは、アプリケーションでフレームを使用できるようになる前に、システムのイメージ処理パイプラインで undistorted されます (プレビューストリームには、元のゆがんだフレームが含まれます)。 使用できるのは CameraIntrinsics だけなので、アプリケーションではイメージフレームが完全な pinhole カメラを表すものと想定する必要があります。

HoloLens (第1世代) では、イメージプロセッサのディストーション関数は、フレームメタデータで CameraIntrinsics を使用しているときに最大10ピクセルのエラーを引き続き発生させる場合があります。 多くのユースケースでは、このエラーは発生しませんが、たとえば、ホログラムを実際のポスター/マーカーに配置している場合は、<10 px オフセット (2 m の位置にあるホログラムの場合は約 11 mm) が発生する可能性があります。 

## <a name="locatable-camera-usage-scenarios"></a>お持ちのカメラの使用シナリオ

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>キャプチャされた場所で写真またはビデオを表示する

デバイスカメラのフレームには、イメージがどこで撮影されたかを正確に示すために使用できる "カメラからワールドへの変換" 変換が付属しています。 たとえば、小さな holographic アイコンをこの場所 (CameraToWorld (Vector3)) に配置して、カメラが直面している方向に小さな矢印を描画する (CameraToWorld Yvector (Vector3)) ことができます ()。

### <a name="tag--pattern--poster--object-tracking"></a>タグ/パターン/ポスター/オブジェクトの追跡

多くの mixed reality アプリケーションでは、認識可能なイメージまたはビジュアルパターンを使用して、空間内の追跡可能なポイントを作成します。 その後、そのポイントを基準としてオブジェクトをレンダリングしたり、既知の場所を作成したりするために使用されます。 HoloLens の使用例としては、fiducials でタグ付けされた現実世界のオブジェクト (QR コードを使用したテレビモニターなど) の検索、fiducials に対するホログラムの配置、および Wi-fi を介して HoloLens と通信するように設定されているタブレットなどの非 HoloLens デバイスとの視覚的な組み合わせがあります。

ビジュアルパターンを認識し、アプリケーションのワールド空間にオブジェクトを配置するには、いくつかの作業が必要です。
1. 画像パターン認識ツールキット (QR コード、AR タグ、顔ファインダー、サークルトラッカー、OCR など)。
2. 実行時にイメージフレームを収集して認識レイヤーに渡す
3. 画像の位置を、世界中や世界中の写真に戻すことができます。 
4. これらの世界の場所に仮想モデルを配置する

いくつかの重要な画像処理リンクを次に示します。
* [OpenCV](https://opencv.org/)
* [QR タグ](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](https://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

対話型アプリケーションのフレームレートを維持することは、特に長時間実行されるイメージ認識アルゴリズムを扱う場合に重要です。 このため、一般的には次のパターンを使用します。
1. メインスレッド: カメラオブジェクトを管理します
2. メインスレッド: 新しいフレームの要求 (非同期)
3. メインスレッド: 新しいフレームを追跡スレッドに渡します
4. 追跡スレッド: キーポイントを収集するためのイメージの処理
5. メインスレッド: 検出されるキーポイントに一致するように仮想モデルを移動します
6. メインスレッド: 手順2の繰り返し

一部のイメージマーカーシステムは、1ピクセルの位置のみを提供します (他のユーザーが完全変換を提供します。このセクションは必要ありません)。これは、可能な場所の射線に相当します。 1つの3d 位置に移動するには、複数の光線を活用し、最終的な結果をおおよその交点で見つけることができます。 そのために必要な作業を次に示します。
1. 複数のカメライメージの収集を開始するループを取得する
2. 関連する特徴ポイントとそのワールド光線を検索する
3. 特徴のディクショナリ (それぞれが複数のワールド線を持つ) がある場合は、次のコードを使用して、これらの光線の交差部分を解決できます。

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

複数の追跡タグの場所を指定すると、ユーザーの現在のシナリオに合わせて、モデル化されたシーンを配置できます。 重力を想定できない場合は、3つのタグ位置が必要になります。 多くの場合、白の球体がリアルタイムの追跡タグの位置を表し、青の球体がモデル化されたタグの場所を表す配色を使用します。 これにより、ユーザーは配置品質を視覚的に測定できます。 ここでは、すべてのアプリケーションで次のセットアップを想定しています。
* 2つ以上のモデル化タグの場所
* シーン内の1つの ' 調整空間 ' は、タグの親です。
* カメラの機能識別子
* 動作は、モデル化されたタグをリアルタイムタグに合わせて調整領域を移動します (他の接続はその相対的な位置であるため、モデル化されたマーカー自体ではなく、親スペースを移動するのは注意してください)。

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>Led または他のレコグナイザーライブラリを使用して、タグ付き静止を追跡または特定したり、実際のオブジェクト/顔を移動したりします。

例 :
* Led のある工業ロボット (または低速な移動オブジェクトの QR コード)
* ルーム内のオブジェクトを識別して認識する
* 部屋の中の人間を識別して認識します。たとえば、顔に holographic の連絡先カードを配置します。

## <a name="see-also"></a>関連項目
* [お持ちのカメラのサンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
* [Unity での場所を特定できるカメラ](../unity/locatable-camera-in-unity.md)
* [複合現実キャプチャ](/hololens/holographic-photos-and-videos)
* [開発者向け複合現実キャプチャ](mixed-reality-capture-for-developers.md)
* [メディアキャプチャの概要](/windows/uwp/audio-video-camera/)
* [Holographic face tracking サンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)