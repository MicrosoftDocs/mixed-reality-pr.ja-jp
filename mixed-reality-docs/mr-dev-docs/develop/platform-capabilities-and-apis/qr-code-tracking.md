---
title: QR コードの追跡
description: HoloLens 2 で、mixed reality アプリで QR コードを検出し、web カメラ機能を追加し、座標系を管理する方法について説明します。
author: dorreneb
ms.author: dobrown
ms.date: 05/15/2019
ms.topic: article
keywords: vr, lbe, 位置情報ベースのエンターテインメント, vr アーケード, アーケード, イマーシブ, qr, qr コード, hololens2
ms.openlocfilehash: 08ed651deaab0c230142f45b93858f41ee300323
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583148"
---
# <a name="qr-code-tracking"></a>QR コードの追跡

HoloLens 2 を使用すると、ヘッドセット周辺の環境内の QR コードを検出し、各コードの実際の場所で座標系を確立することができます。

## <a name="device-support"></a>デバイス サポート

<table>
<tr>
<th>特徴量</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens (最初の世代)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td> QR コードの検出</td><td style="text-align: center;">️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">✔️</td>
</tr>
</table>

>[!NOTE]
>デスクトップ Pc でのイマーシブ Windows Mixed Reality ヘッドセットを使用した QR コードの追跡は、Windows 10 バージョン2004以降でサポートされています。 MixedReality () API を使用して、機能が現在のデバイスでサポートされているかどうかを判断します。

## <a name="getting-the-qr-package"></a>QR パッケージの取得

QR コード検出用の NuGet パッケージは [こちら](https://nuget.org/Packages/Microsoft.MixedReality.QR)からダウンロードできます。

## <a name="detecting-qr-codes"></a>QR コードの検出

### <a name="adding-the-webcam-capability"></a>Web カメラ機能の追加

QR コードを検出するには、マニフェストに機能を追加する必要があり `webcam` ます。 この機能は、ユーザーの環境で検出されたコード内のデータに機密情報が含まれている場合に必要です。

アクセス許可を要求するには、次のように呼び出し `QRCodeWatcher.RequestAccessAsync()` ます。

_Visual_
```cs
await QRCodeWatcher.RequestAccessAsync();
```

_C++_
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

QRCodeWatcher オブジェクトを構築する前に、アクセス許可を要求する必要があります。

QR コードの検出には機能が必要ですが、 `webcam` 検出はデバイスの追跡カメラを使用して行われます。 これにより、デバイスの写真/ビデオ (PV) カメラとの検出と比較して、より広範な検出とバッテリ寿命が提供されます。

### <a name="detecting-qr-codes-in-unity"></a>Unity での QR コードの検出

Unity の QR コード検出 API は、 [unity 用の nuget](https://github.com/GlitchEnzo/NuGetForUnity)を使用して nuget パッケージをインストールすることにより、MRTK をインポートせずに使用できます。 そのしくみを理解するには、 [Unity アプリのサンプル](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes)をダウンロードします。 サンプルアプリには、QR コードや、GUID、物理サイズ、タイムスタンプ、デコードされたデータなどの関連データに対して holographic 二乗を表示する例が含まれています。

### <a name="detecting-qr-codes-in-c"></a>C++ での QR コードの検出

```cpp
using namespace winrt::Windows::Foundation;
using namespace winrt::Microsoft::MixedReality::QR;

class QRListHelper
{
public:
    QRListHelper(MyApplication& app) :
        m_app(app)
    {}

    IAsyncAction SetUpQRCodes()
    {
        if (QRCodeWatcher::IsSupported())
        {
            QRCodeWatcherAccessStatus status = co_await QRCodeWatcher::RequestAccessAsync();
            InitializeQR(status);
        }
    }

private:
    void OnAddedQRCode(const IInspectable&, const QRCodeAddedEventArgs& args)
    {
        m_app.OnAddedQRCode(args);
    }

    void OnUpdatedQRCode(const IInspectable&, const QRCodeUpdatedEventArgs& args)
    {
        m_app.OnUpdatedQRCode(args);
    }

    void OnEnumerationComplete(const IInspectable&, const IInspectable&)
    {
        m_app.OnEnumerationComplete();
    }

    MyApplication& m_app;
    QRCodeWatcher m_qrWatcher{ nullptr };

    void InitializeQR(QRCodeWatcherAccessStatus status)
    {
        if (status == QRCodeWatcherAccessStatus::Allowed)
        {
            m_qrWatcher = QRCodeWatcher();
            m_qrWatcher.Added({ this, &QRListHelper::OnAddedQRCode });
            m_qrWatcher.Updated({ this, &QRListHelper::OnUpdatedQRCode });
            m_qrWatcher.EnumerationCompleted({ this, &QRListHelper::OnEnumerationComplete });
            m_qrWatcher.Start();
        }
        else
        {
            // Permission denied by system or user
            // Handle the failures
        }
    }
};
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a>QR コードの座標系を取得する

検出された各 QR コードは、左上にある高速検出の四角形の左上隅にある QR コードに一致する [空間座標システム](../../design/coordinate-systems.md) を公開します。  

![QR コードの座標系](images/Qr-coordinatesystem.png) 

QR SDK を直接使用している場合、Z 軸は用紙を指しています (図には示されていません)。 Unity 座標に変換されると、Z 軸は用紙から外れ、左手で示されます。

QR コードの SpatialCoordinateSystem は、示されているように配置されます。 <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview:: CreateCoordinateSystemForNode</a>を呼び出し、コードの SpatialGraphNodeId を渡すことによって、プラットフォームから座標系を取得できます。

次の C++ コードは、QR コードの座標系を使用して、四角形を作成して配置する方法を示しています。

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> MyApplication::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

次のように、物理的なサイズを使用して QR 四角形を作成できます。

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

座標系は、QR コードを描画したり、場所にホログラムをアタッチしたりするために使用できます。

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

*QRCodeAddedHandler* は、次のようになります。

```cpp
void MyApplication::OnAddedQRCode(const QRCodeAddedEventArgs& args)
{
    QRCode code = args.Code();
    std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength());
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            qrVertices,
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="best-practices-for-qr-code-detection"></a>QR コードの検出のベストプラクティス

### <a name="quiet-zones-around-qr-codes"></a>QR コードに関する非表示のゾーン

QR コードを正しく読み取るには、コードのすべての辺の周りに余白が必要です。 この余白には、印刷されたコンテンツを含めることはできません。また、4つのモジュール (コード内の1つの黒い四角形) にする必要があります。 

[QR 仕様](https://www.qrcode.com/en/howto/code.html)には、非表示ゾーンに関する詳細情報が含まれています。

### <a name="lighting-and-backdrop"></a>照明と背景
QR コード検出の品質は、さまざまな照明と背景に影響します。 

明るい照明を持つシーンでは、黒のコードをグレーの背景で印刷します。 それ以外の場合は、黒の QR コードを白い背景に印刷します。

コードの背景が濃い場合は、検出率が低い場合はグレーのコードで黒を試してみてください。 背景が比較的薄い場合は、通常のコードが正常に動作します。

### <a name="size-of-qr-codes"></a>QR コードのサイズ
Windows Mixed Reality デバイスは、それぞれ 5 cm 未満の QR コードでは動作しません。

5 cm と 10 cm の長さの間の QR コードの場合、コードを検出するために非常に近い必要があります。 また、このサイズでコードを検出するのにも時間がかかります。 

コードを正確に検出するための正確な時間は、QR コードのサイズだけでなく、コードから離れている距離にも依存します。 コードに近づけると、サイズの問題を相殺するのに役立ちます。

### <a name="distance-and-angular-position-from-the-qr-code"></a>QR コードからの距離と角度の位置
追跡カメラは、特定のレベルの詳細のみを検出できます。 小さいコードの場合は、両側に < 10 cm が必要です。非常に近いものにする必要があります。 10 cm から 25 cm までさまざまなバージョン1の QR コードの場合、最小検出距離は0.15 メートルから0.5 メートルの範囲内です。 

サイズの検出距離は直線的に増加します。 

QR 検出は、+ = 45 度の範囲で動作し、コードを検出するための適切な解決策があることを確認します。

### <a name="qr-codes-with-logos"></a>ロゴ付き QR コード
ロゴ付きの QR コードはまだテストされていないため、現在サポートされていません。

### <a name="managing-qr-code-data"></a>QR コードデータの管理
Windows Mixed Reality デバイスは、ドライバーのシステムレベルで QR コードを検出します。 デバイスが再起動されると、検出された QR コードは失われ、次に新しいオブジェクトとして再検出されます。

特定のタイムスタンプよりも古い QR コードを無視するようにアプリを構成することをお勧めします。 現在、API は QR コード履歴のクリアをサポートしていません。

### <a name="qr-code-placement-in-a-space"></a>スペースでの QR コードの配置
QR コードを配置する場所と方法に関する推奨事項については、「 [HoloLens の環境に関する考慮事項](/hololens/hololens-environment-considerations)」を参照してください。

## <a name="qr-api-reference"></a>QR API リファレンス

```cs
namespace Microsoft.MixedReality.QR
{
    /// <summary>
    /// Represents a detected QR code.
    /// </remarks>
    public class QRCode
    {
        /// <summary>
        /// Unique id that identifies this QR code for this session.
        /// </summary>
        public Guid Id { get; }

        /// <summary>
        /// Spatial graph node id for this QR code to create a coordinate system.
        /// </summary>
        public Guid SpatialGraphNodeId { get; }

        /// <summary>
        /// Version of this QR code. Version 1-40 are regular QR codes and M1 to M4 are Micro QR code formats 1-4.
        /// </summary>
        public QRVersion Version { get; }

        /// <summary>
        /// Physical width and height of this QR code in meters.
        /// </summary>
        public float PhysicalSideLength { get; }

        /// <summary>
        /// Decoded QR code data.
        /// </summary>
        public String Data { get; }

        /// <summary>
        /// Size of the RawData of this QR code.
        /// </summary>
        public UInt32 RawDataSize { get; }

        /// <summary>
        /// Gets the error-corrected raw data bytes.
        /// Used when the platform is unable to decode the code's format,
        /// allowing your app to decode as needed.
        /// </summary>
        public void GetRawData(byte[] buffer);

        /// <summary>
        /// The last detected time in 100ns QPC ticks.
        /// </summary>
        public System.TimeSpan SystemRelativeLastDetectedTime { get; }

        /// <summary>
        /// The last detected time.
        /// </summary>
        public System.DateTimeOffset LastDetectedTime { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Added event.
    /// </summary>
    public class QRCodeAddedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was added
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Removed event.
    /// </summary>
    public class QRCodeRemovedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was removed.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Updated event.
    /// </summary>
    public class QRCodeUpdatedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was updated.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Represents the status of an access request for QR code detection.
    /// </summary>
    public enum QRCodeWatcherAccessStatus
    {
        /// <summary>
        /// The system has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedBySystem = 0,
        /// <summary>
        /// The app has not declared the webcam capability in its manifest.
        /// </summary>
        NotDeclaredByApp = 1,
        /// <summary>
        /// The user has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedByUser = 2,
        /// <summary>
        /// A user prompt is required to get permission to detect QR codes.
        /// </summary>
        UserPromptRequired = 3,
        /// <summary>
        /// The user has given permission to detect QR codes.
        /// </summary>
        Allowed = 4,
    }

    /// <summary>
    /// Detects QR codes in the user's environment.
    /// </summary>
    public class QRCodeWatcher
    {
        /// <summary>
        /// Gets whether QR code detection is supported on the current device.
        /// </summary>
        public static bool IsSupported();

        /// <summary>
        /// Request user consent before using QR code detection.
        /// </summary>
        public static IAsyncOperation<QRCodeWatcherAccessStatus> RequestAccessAsync();

        /// <summary>
        /// Constructs a new QRCodeWatcher.
        /// </summary>
        public QRCodeWatcher();

        /// <summary>
        /// Starts detecting QR codes.
        /// </summary>
        /// <remarks>
        /// Start should only be called once RequestAccessAsync has succeeded.
        /// Start should not be called if QR code detection is not supported.
        /// Check that IsSupported returns true before calling Start.
        /// </remarks>
        public void Start();

        /// <summary>
        /// Stops detecting QR codes.
        /// </summary>
        public void Stop();

        /// <summary>
        /// Get the list of QR codes detected.
        /// </summary>
        /// <remarks>
        /// </remarks>
        public IList<QRCode> GetList();

        /// <summary>
        /// Event representing the addition of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeAddedEventArgs> Added;

        /// <summary>
        /// Event representing the removal of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeRemovedEventArgs> Removed;

        /// <summary>
        /// Event representing the update of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeUpdatedEventArgs> Updated;

        /// <summary>
        /// Event representing the enumeration of QR Codes completing after a Start call.
        /// </summary>
        public event EventHandler<Object> EnumerationCompleted;
    }

    /// <summary>
    /// Version info for QR codes, including Micro QR codes.
    /// </summary>
    public enum QRVersion
    {
        QR1 = 1,
        QR2 = 2,
        QR3 = 3,
        QR4 = 4,
        QR5 = 5,
        QR6 = 6,
        QR7 = 7,
        QR8 = 8,
        QR9 = 9,
        QR10 = 10,
        QR11 = 11,
        QR12 = 12,
        QR13 = 13,
        QR14 = 14,
        QR15 = 15,
        QR16 = 16,
        QR17 = 17,
        QR18 = 18,
        QR19 = 19,
        QR20 = 20,
        QR21 = 21,
        QR22 = 22,
        QR23 = 23,
        QR24 = 24,
        QR25 = 25,
        QR26 = 26,
        QR27 = 27,
        QR28 = 28,
        QR29 = 29,
        QR30 = 30,
        QR31 = 31,
        QR32 = 32,
        QR33 = 33,
        QR34 = 34,
        QR35 = 35,
        QR36 = 36,
        QR37 = 37,
        QR38 = 38,
        QR39 = 39,
        QR40 = 40,
        MicroQRM1 = 41,
        MicroQRM2 = 42,
        MicroQRM3 = 43,
        MicroQRM4 = 44,
    }
}
```

## <a name="see-also"></a>関連項目
* [座標系](../../design/coordinate-systems.md)
* <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>