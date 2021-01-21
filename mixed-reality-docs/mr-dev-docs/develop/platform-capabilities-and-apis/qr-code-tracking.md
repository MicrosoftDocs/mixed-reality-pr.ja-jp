---
title: QR コードの追跡
description: HoloLens 2 で、mixed reality アプリで QR コードを検出し、web カメラ機能を追加し、座標系を管理する方法について説明します。
author: dorreneb
ms.author: dobrown
ms.date: 01/21/2021
ms.topic: article
keywords: vr, lbe, 位置情報ベースのエンターテインメント, vr アーケード, アーケード, イマーシブ, qr, qr コード, hololens2
ms.openlocfilehash: 0f53b8def268b2d501c6efe3c3e40ea18f9323e0
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/21/2021
ms.locfileid: "98635434"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="1ea4f-104">QR コードの追跡</span><span class="sxs-lookup"><span data-stu-id="1ea4f-104">QR code tracking</span></span>

<span data-ttu-id="1ea4f-105">HoloLens 2 を使用すると、ヘッドセット周辺の環境内の QR コードを検出し、各コードの実際の場所で座標系を確立することができます。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-105">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span> <span data-ttu-id="1ea4f-106">デバイスの web カメラを有効にすると、Unreal または Unity のプロジェクトの最新バージョンで QR コードを認識できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-106">Once you enable your device's webcam, you'll be able to recognize QR codes in the latest versions of your Unreal or Unity projects.</span></span> <span data-ttu-id="1ea4f-107">運用環境に移行する前に、記事の最後に掲載した [ベストプラクティス](#best-practices-for-qr-code-detection) に従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-107">Before going to production, we recommend following the [best practices](#best-practices-for-qr-code-detection) we've laid at the end of the article.</span></span>

## <a name="device-support"></a><span data-ttu-id="1ea4f-108">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="1ea4f-108">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1ea4f-109">機能</span><span class="sxs-lookup"><span data-stu-id="1ea4f-109">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="1ea4f-110"><a href="/hololens/hololens1-hardware">HoloLens (最初の世代)</a></span><span class="sxs-lookup"><span data-stu-id="1ea4f-110"><a href="/hololens/hololens1-hardware">HoloLens (first gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="1ea4f-111">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="1ea4f-111">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="1ea4f-112"><a href="../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="1ea4f-112"><a href="../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="1ea4f-113">QR コードの検出</span><span class="sxs-lookup"><span data-stu-id="1ea4f-113">QR code detection</span></span></td><td style="text-align: center;"><span data-ttu-id="1ea4f-114">️</span><span class="sxs-lookup"><span data-stu-id="1ea4f-114">️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1ea4f-115">✔️</span><span class="sxs-lookup"><span data-stu-id="1ea4f-115">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="1ea4f-116">✔️</span><span class="sxs-lookup"><span data-stu-id="1ea4f-116">✔️</span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="1ea4f-117">デスクトップ Pc でのイマーシブ Windows Mixed Reality ヘッドセットを使用した QR コードの追跡は、Windows 10 バージョン2004以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-117">QR code tracking with immersive Windows Mixed Reality headsets on desktop PCs is supported on Windows 10 Version 2004 and higher.</span></span> <span data-ttu-id="1ea4f-118">MixedReality () API を使用して、機能が現在のデバイスでサポートされているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-118">Use the Microsoft.MixedReality.QRCodeWatcher.IsSupported() API to determine whether the feature is supported on the current device.</span></span>

## <a name="getting-the-qr-package"></a><span data-ttu-id="1ea4f-119">QR パッケージの取得</span><span class="sxs-lookup"><span data-stu-id="1ea4f-119">Getting the QR package</span></span>

<span data-ttu-id="1ea4f-120">QR コード検出用の NuGet パッケージは [こちら](https://nuget.org/Packages/Microsoft.MixedReality.QR)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-120">You can download the NuGet package for QR code detection [here](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span></span>

## <a name="detecting-qr-codes"></a><span data-ttu-id="1ea4f-121">QR コードの検出</span><span class="sxs-lookup"><span data-stu-id="1ea4f-121">Detecting QR codes</span></span>

### <a name="adding-the-webcam-capability"></a><span data-ttu-id="1ea4f-122">Web カメラ機能の追加</span><span class="sxs-lookup"><span data-stu-id="1ea4f-122">Adding the webcam capability</span></span>

<span data-ttu-id="1ea4f-123">QR コードを検出するには、マニフェストに機能を追加する必要があり `webcam` ます。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-123">You'll need to add the capability `webcam` to your manifest to detect QR codes.</span></span> <span data-ttu-id="1ea4f-124">この機能は、ユーザーの環境で検出されたコード内のデータに機密情報が含まれている場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-124">This capability is required as the data within detected codes in the user's environment may contain sensitive information.</span></span>

<span data-ttu-id="1ea4f-125">アクセス許可を要求するには、次のように呼び出し `QRCodeWatcher.RequestAccessAsync()` ます。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-125">Permission can be requested by calling `QRCodeWatcher.RequestAccessAsync()`:</span></span>

<span data-ttu-id="1ea4f-126">_Visual_</span><span class="sxs-lookup"><span data-stu-id="1ea4f-126">_C#:_</span></span>
```cs
await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="1ea4f-127">_C++_</span><span class="sxs-lookup"><span data-stu-id="1ea4f-127">_C++:_</span></span>
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="1ea4f-128">QRCodeWatcher オブジェクトを構築する前に、アクセス許可を要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-128">Permission must be requested before you construct a QRCodeWatcher object.</span></span>

<span data-ttu-id="1ea4f-129">QR コードの検出には機能が必要ですが、 `webcam` 検出はデバイスの追跡カメラを使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-129">While QR code detection requires the `webcam` capability, the detection occurs using the device's tracking cameras.</span></span> <span data-ttu-id="1ea4f-130">これにより、デバイスの写真/ビデオ (PV) カメラとの検出と比較して、より広範な検出とバッテリ寿命が提供されます。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-130">This provides a wider detection FOV and better battery life compared to detection with the device's photo/video (PV) camera.</span></span>

### <a name="detecting-qr-codes-in-unity"></a><span data-ttu-id="1ea4f-131">Unity での QR コードの検出</span><span class="sxs-lookup"><span data-stu-id="1ea4f-131">Detecting QR codes in Unity</span></span>

<span data-ttu-id="1ea4f-132">Unity の QR コード検出 API は、 [unity 用の nuget](https://github.com/GlitchEnzo/NuGetForUnity)を使用して nuget パッケージをインストールすることにより、MRTK をインポートせずに使用できます。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-132">You can use the QR code detection API in Unity without importing MRTK by installing the NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span> <span data-ttu-id="1ea4f-133">そのしくみを理解するには、 [Unity アプリのサンプル](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes)をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-133">If you want to get a feel for how it works, download the [sample Unity app](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes).</span></span> <span data-ttu-id="1ea4f-134">サンプルアプリには、QR コードや、GUID、物理サイズ、タイムスタンプ、デコードされたデータなどの関連データに対して holographic 二乗を表示する例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-134">The sample app has examples for displaying a holographic square over QR codes and associated data such as GUID, physical size, timestamp, and decoded data.</span></span>

### <a name="detecting-qr-codes-in-c"></a><span data-ttu-id="1ea4f-135">C++ での QR コードの検出</span><span class="sxs-lookup"><span data-stu-id="1ea4f-135">Detecting QR codes in C++</span></span>

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

## <a name="getting-the-coordinate-system-for-a-qr-code"></a><span data-ttu-id="1ea4f-136">QR コードの座標系を取得する</span><span class="sxs-lookup"><span data-stu-id="1ea4f-136">Getting the coordinate system for a QR code</span></span>

<span data-ttu-id="1ea4f-137">検出された各 QR コードは、左上にある高速検出の四角形の左上隅にある QR コードに一致する [空間座標システム](../../design/coordinate-systems.md) を公開します。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-137">Each detected QR code exposes a [spatial coordinate system](../../design/coordinate-systems.md) aligned with the QR code at the top-left corner of the fast detection square in the top left:</span></span>  

![QR コードの座標系](images/Qr-coordinatesystem.png) 

<span data-ttu-id="1ea4f-139">QR SDK を直接使用している場合、Z 軸は用紙を指しています (図には示されていません)。 Unity 座標に変換されると、Z 軸は用紙から外れ、左手で示されます。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-139">When directly using the QR SDK, the Z-axis is pointing into the paper (not shown) - when converted into Unity coordinates, the Z-axis points out of the paper and is left-handed.</span></span>

<span data-ttu-id="1ea4f-140">QR コードの SpatialCoordinateSystem は、示されているように配置されます。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-140">A QR code's SpatialCoordinateSystem aligns as shown.</span></span> <span data-ttu-id="1ea4f-141"><a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview:: CreateCoordinateSystemForNode</a>を呼び出し、コードの SpatialGraphNodeId を渡すことによって、プラットフォームから座標系を取得できます。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-141">You can get the coordinate system from the platform by calling <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> and passing in the code's SpatialGraphNodeId.</span></span>

<span data-ttu-id="1ea4f-142">次の C++ コードは、QR コードの座標系を使用して、四角形を作成して配置する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-142">The C++ code below shows how to create a rectangle and place it using the QR code's coordinate system:</span></span>

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

<span data-ttu-id="1ea4f-143">次のように、物理的なサイズを使用して QR 四角形を作成できます。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-143">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

<span data-ttu-id="1ea4f-144">座標系は、QR コードを描画したり、場所にホログラムをアタッチしたりするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-144">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

<span data-ttu-id="1ea4f-145">*QRCodeAddedHandler* は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-145">Altogether, your *QRCodeAddedHandler* may look something like this:</span></span>

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

## <a name="best-practices-for-qr-code-detection"></a><span data-ttu-id="1ea4f-146">QR コードの検出のベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="1ea4f-146">Best practices for QR code detection</span></span>

### <a name="quiet-zones-around-qr-codes"></a><span data-ttu-id="1ea4f-147">QR コードに関する非表示のゾーン</span><span class="sxs-lookup"><span data-stu-id="1ea4f-147">Quiet zones around QR Codes</span></span>

<span data-ttu-id="1ea4f-148">QR コードを正しく読み取るには、コードのすべての辺の周りに余白が必要です。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-148">To be read correctly, QR codes require a margin around all sides of the code.</span></span> <span data-ttu-id="1ea4f-149">この余白には、印刷されたコンテンツを含めることはできません。また、4つのモジュール (コード内の1つの黒い四角形) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-149">This margin must not contain any printed content and should be four modules (a single black square in the code) wide.</span></span> 

<span data-ttu-id="1ea4f-150">[QR 仕様](https://www.qrcode.com/en/howto/code.html)には、非表示ゾーンに関する詳細情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-150">The [QR spec](https://www.qrcode.com/en/howto/code.html) contains more information about quiet zones.</span></span>

### <a name="lighting-and-backdrop"></a><span data-ttu-id="1ea4f-151">照明と背景</span><span class="sxs-lookup"><span data-stu-id="1ea4f-151">Lighting and backdrop</span></span>
<span data-ttu-id="1ea4f-152">QR コード検出の品質は、さまざまな照明と背景に影響します。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-152">QR code detection quality is susceptible to varying illumination and backdrop.</span></span> 

<span data-ttu-id="1ea4f-153">明るい照明を持つシーンでは、黒のコードをグレーの背景で印刷します。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-153">In a scene with bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="1ea4f-154">それ以外の場合は、黒の QR コードを白い背景に印刷します。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-154">Otherwise, print a black QR code on a white background.</span></span>

<span data-ttu-id="1ea4f-155">コードの背景が濃い場合は、検出率が低い場合はグレーのコードで黒を試してみてください。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-155">If the backdrop to the code is dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="1ea4f-156">背景が比較的薄い場合は、通常のコードが正常に動作します。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-156">If the backdrop is relatively light, a regular code should work fine.</span></span>

### <a name="size-of-qr-codes"></a><span data-ttu-id="1ea4f-157">QR コードのサイズ</span><span class="sxs-lookup"><span data-stu-id="1ea4f-157">Size of QR codes</span></span>
<span data-ttu-id="1ea4f-158">Windows Mixed Reality デバイスは、それぞれ 5 cm 未満の QR コードでは動作しません。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-158">Windows Mixed Reality devices don't work with QR codes with sides smaller than 5 cm each.</span></span>

<span data-ttu-id="1ea4f-159">5 cm と 10 cm の長さの間の QR コードの場合、コードを検出するために非常に近い必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-159">For QR codes between 5 cm and 10-cm length sides, you must be fairly close to detect the code.</span></span> <span data-ttu-id="1ea4f-160">また、このサイズでコードを検出するのにも時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-160">It will also take longer to detect codes at this size.</span></span> 

<span data-ttu-id="1ea4f-161">コードを正確に検出するための正確な時間は、QR コードのサイズだけでなく、コードから離れている距離にも依存します。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-161">The exact time to detect codes depends not only on the size of the QR codes, but how far you're away from the code.</span></span> <span data-ttu-id="1ea4f-162">コードに近づけると、サイズの問題を相殺するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-162">Moving closer to the code will help offset issues with size.</span></span>

### <a name="distance-and-angular-position-from-the-qr-code"></a><span data-ttu-id="1ea4f-163">QR コードからの距離と角度の位置</span><span class="sxs-lookup"><span data-stu-id="1ea4f-163">Distance and angular position from the QR code</span></span>
<span data-ttu-id="1ea4f-164">追跡カメラは、特定のレベルの詳細のみを検出できます。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-164">The tracking cameras can only detect a certain level of detail.</span></span> <span data-ttu-id="1ea4f-165">小さいコードの場合は、両側に < 10 cm が必要です。非常に近いものにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-165">For small codes - < 10 cm along the sides - you must be fairly close.</span></span> <span data-ttu-id="1ea4f-166">10 cm から 25 cm までさまざまなバージョン1の QR コードの場合、最小検出距離は0.15 メートルから0.5 メートルの範囲内です。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-166">For a version 1 QR code varying from 10 cm to 25 cm wide, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> 

<span data-ttu-id="1ea4f-167">サイズの検出距離は直線的に増加します。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-167">The detection distance for size increases linearly.</span></span> 

<span data-ttu-id="1ea4f-168">QR 検出は、+ = 45 度の範囲で動作し、コードを検出するための適切な解決策があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-168">QR detection works with a range of angles += 45 deg to ensure we have proper resolution to detect the code.</span></span>

### <a name="qr-codes-with-logos"></a><span data-ttu-id="1ea4f-169">ロゴ付き QR コード</span><span class="sxs-lookup"><span data-stu-id="1ea4f-169">QR codes with logos</span></span>
<span data-ttu-id="1ea4f-170">ロゴ付きの QR コードはまだテストされていないため、現在サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-170">QR codes with logos haven't been tested and are currently unsupported.</span></span>

### <a name="managing-qr-code-data"></a><span data-ttu-id="1ea4f-171">QR コードデータの管理</span><span class="sxs-lookup"><span data-stu-id="1ea4f-171">Managing QR code data</span></span>
<span data-ttu-id="1ea4f-172">Windows Mixed Reality デバイスは、ドライバーのシステムレベルで QR コードを検出します。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-172">Windows Mixed Reality devices detect QR codes at the system level in the driver.</span></span> <span data-ttu-id="1ea4f-173">デバイスが再起動されると、検出された QR コードは失われ、次に新しいオブジェクトとして再検出されます。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-173">When the device is rebooted, the detected QR codes are gone and will be redetected as new objects next time.</span></span>

<span data-ttu-id="1ea4f-174">特定のタイムスタンプよりも古い QR コードを無視するようにアプリを構成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-174">We recommend configuring your app to ignore QR codes older than a specific timestamp.</span></span> <span data-ttu-id="1ea4f-175">現在、API は QR コード履歴のクリアをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-175">Currently, the API doesn't support clearing QR code history.</span></span>

### <a name="qr-code-placement-in-a-space"></a><span data-ttu-id="1ea4f-176">スペースでの QR コードの配置</span><span class="sxs-lookup"><span data-stu-id="1ea4f-176">QR code placement in a space</span></span>
<span data-ttu-id="1ea4f-177">QR コードを配置する場所と方法に関する推奨事項については、「 [HoloLens の環境に関する考慮事項](/hololens/hololens-environment-considerations)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ea4f-177">For recommendations on where and how to place QR codes, refer to [Environment considerations for HoloLens](/hololens/hololens-environment-considerations).</span></span>

## <a name="qr-api-reference"></a><span data-ttu-id="1ea4f-178">QR API リファレンス</span><span class="sxs-lookup"><span data-stu-id="1ea4f-178">QR API reference</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1ea4f-179">こちらもご覧ください</span><span class="sxs-lookup"><span data-stu-id="1ea4f-179">See also</span></span>
* [<span data-ttu-id="1ea4f-180">座標系</span><span class="sxs-lookup"><span data-stu-id="1ea4f-180">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* <span data-ttu-id="1ea4f-181"><a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="1ea4f-181"><a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span></span>