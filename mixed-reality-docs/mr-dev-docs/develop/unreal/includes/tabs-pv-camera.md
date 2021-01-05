---
ms.openlocfilehash: eb51caa4caf0d425b5e49c3abca2a523b08fc312
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2020
ms.locfileid: "97718117"
---
# <a name="426"></a>[4.26](#tab/426) 

## <a name="pv-camera-feed-setup"></a>PV カメラのフィードの設定

- **[プロジェクト設定] > [HoloLens]** で、 **[Web カメラ]** 機能を有効にします。

![[Web カメラ] プロパティが強調表示されている HoloLens プロジェクト設定のスクリーンショット](../images/unreal-pvc-img-01.png)

- "CamCapture" という名前の新しいアクターを作成し、カメラ フィードをレンダリングするための平面を追加します。

![平面が追加されたアクターのスクリーンショット](../images/unreal-pvc-img-02.png)

- アクターをシーンに追加し、テクスチャ オブジェクト パラメーターとテクスチャ サンプルを使用して、CamTextureMaterial という名前の新しいマテリアルを作成します。  テクスチャの RGB データを出力放射色に送信します。

![マテリアルとテクスチャのサンプルのブループリント](../images/unreal-pvc-img-03.png)

## <a name="rendering-the-pv-camera-feed"></a>PV カメラ フィードのレンダリング

- CamCapture ブループリントで、PV カメラをオンにします。

![PV カメラがオンになっている ARCapture 切り替え関数のブループリント](../images/unreal-pvc-img-04.png)

- CamTextureMaterial から動的なマテリアル インスタンスを作成し、このマテリアルをアクターの平面に割り当てます。

![動的マテリアル インスタンス作成関数のブループリント](../images/unreal-pvc-img-05.png)

- カメラ フィードからテクスチャを取得し、有効な場合はそれを動的マテリアルに割り当てます。  テクスチャが有効でない場合は、タイマーを開始し、タイムアウト後に再試行します。

![動的マテリアルに割り当てられたカメラ フィード テクスチャのブループリント](../images/unreal-pvc-img-06.png)

- 最後に、カメラ画像の縦横比で平面を拡大縮小します。

![カメラ画像の縦横比に合わせて拡大縮小された平面のブループリント](../images/unreal-pvc-img-07.png)

## <a name="find-camera-positions-in-world-space"></a>ワールド空間でカメラの位置を検索する

HoloLens 2 のカメラは、デバイスの頭追跡から垂直方向にオフセットされます。  オフセットを考慮するために、ワールド空間内のカメラの位置を調べる関数がいくつかあります。

GetPVCameraToWorldTransform を使用すると、PV カメラのワールド空間内の変換が取得されて、カメラのレンズに配置されます。

![PVCamera からワールド空間への変換の取得関数のブループリント](../images/unreal-pvc-img-08.png)

GetWorldSpaceRayFromCameraPoint を使用すると、カメラ フレーム内のピクセルの内容を調べるため、カメラのレンズから Unreal ワールド空間内のシーンに光線がキャストされます。

![カメラ ポイントからのワールド空間の光線の取得のブループリント](../images/unreal-pvc-img-09.png)

GetPVCameraIntrinsics を使用すると、カメラの組み込み値が返されます。カメラ フレームでコンピューター ビジョン処理を行うときにそれを使用できます。

![PVCamera 組み込み関数取得のブループリント](../images/unreal-pvc-img-10.png)

ワールド空間の特定のピクセル座標に存在するものを調べるには、ワールド空間光線でライン トレースを使用します。

![ワールド空間の特定のピクセル座標に存在するものを調べるために使用されているワールド空間光線のブループリント](../images/unreal-pvc-img-11.png)

ここでは、フレームの左上から ¼ のカメラス空間位置に向けて、カメラのレンズから 2 メートルの光線をキャストします。  次に、ヒット結果を使用して、ワールド空間内のオブジェクトが存在する場所に何かをレンダリングします。

![フレームの左上から 1/4 のカメラス空間位置に向けてカメラのレンズからキャストされる 2 メートルの光線のブループリント](../images/unreal-pvc-img-12.png)

空間マッピングを使用している場合、このヒット位置はカメラで見ているサーフェスと一致します。

## <a name="rendering-the-pv-camera-feed-in-c"></a>C++ での PV カメラ フィードのレンダリング

- CamCapture という名前の新しい C++ アクターを作成します
- プロジェクトの build.cs で、"AugmentedReality" を PublicDependencyModuleNames リストに追加します。

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",
        "AugmentedReality"
});
```

- CamCapture.h で、ARBlueprintLibrary.h をインクルードします

```cpp
#include "ARBlueprintLibrary.h"
```

- また、メッシュとマテリアルのローカル変数を追加する必要があります。

```cpp
private:
    UStaticMesh* StaticMesh;
    UStaticMeshComponent* StaticMeshComponent;
    UMaterialInstanceDynamic* DynamicMaterial;
    bool IsTextureParamSet = false;
```

- CamCapture.cpp で、静的メッシュをシーンに追加するようにコンストラクターを更新します。

```cpp
ACamCapture::ACamCapture()
{
    PrimaryActorTick.bCanEverTick = true;

    // Load a mesh from the engine to render the camera feed to.
    StaticMesh = LoadObject<UStaticMesh>(nullptr, TEXT("/Engine/EngineMeshes/Cube.Cube"), nullptr, LOAD_None, nullptr);

    // Create a static mesh component to render the static mesh
    StaticMeshComponent = CreateDefaultSubobject<UStaticMeshComponent>(TEXT("CameraPlane"));
    StaticMeshComponent->SetStaticMesh(StaticMesh);

    // Scale and add to the scene
    StaticMeshComponent->SetWorldScale3D(FVector(0.1f, 1, 1));
    this->SetRootComponent(StaticMeshComponent);
}
```

BeginPlay で、プロジェクトのカメラ マテリアルから動的マテリアルのインスタンスを作成し、それを静的メッシュ コンポーネントに適用して、HoloLens カメラを開始します。 
 
エディターのコンテンツ ブラウザーで CamTextureMaterial を右クリックし、[参照のコピー] を選択して、CameraMatPath の文字列を取得します。

```cpp
void ACamCapture::BeginPlay()
{
    Super::BeginPlay();

    // Create a dynamic material instance from the game's camera material.
    // Right-click on a material in the project and select "Copy Reference" to get this string.
    FString CameraMatPath("Material'/Game/Materials/CamTextureMaterial.CamTextureMaterial'");
    UMaterial* BaseMateriall = (UMaterial*)StaticLoadObject(UMaterial::StaticClass(), nullptr, *CameraMatPath, nullptr, LOAD_None, nullptr);
    DynamicMaterial = UMaterialInstanceDynamic::Create(BaseMaterial, this);

    // Use the dynamic material instance when rendering the camera mesh.
    StaticMeshComponent->SetMaterial(0, DynamicMaterial);

    // Start the webcam.
    UARBlueprintLibrary::ToggleARCapture(true, EARCaptureType::Camera);
}
```

Tick で、カメラからテクスチャを取得し、それを CamTextureMaterial マテリアルのテクスチャ パラメーターに設定して、カメラ フレームの縦横比で静的メッシュ コンポーネントを拡大縮小します。

```cpp
void ACamCapture::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);

    // Dynamic material instance only needs to be set once.
    if(IsTextureParamSet)
    {
        return;
    }

    // Get the texture from the camera.
    UARTexture* ARTexture = UARBlueprintLibrary::GetARTexture(EARTextureType::CameraImage);
    if(ARTexture != nullptr)
    {
        // Set the shader's texture parameter (named "Param") to the camera image.
        DynamicMaterial->SetTextureParameterValue("Param", ARTexture);
        IsTextureParamSet = true;

        // Get the camera instrincs
        FARCameraIntrinsics Intrinsics;
        UARBlueprintLibrary::GetCameraIntrinsics(Intrinsics);

        // Scale the camera mesh by the aspect ratio.
        float R = (float)Intrinsics.ImageResolution.X / (float)Intrinsics.ImageResolution.Y;
        StaticMeshComponent->SetWorldScale3D(FVector(0.1f, R, 1));
    }
}
```

# <a name="425"></a>[4.25](#tab/425)

## <a name="render-from-the-pv-camera-for-mrc"></a>MRC 用の PV カメラからのレンダリング

> [!NOTE]
> これには **Unreal Engine 4.25** 以降のバージョンが必要です。

システムとカスタム MRC レコーダーにより、PV カメラをアプリによってレンダリングされたホログラムと組み合わせることにより、Mixed Reality キャプチャが作成されます。

既定では、Mixed Reality キャプチャでは、右目のホログラフィック出力が使用されます。 イマーシブ アプリによって [PV カメラ](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)からのレンダリングが選択された場合は、それが代わりに使用されます。 PV カメラからレンダリングすることにより、現実世界と MRC ビデオのホログラムとの間のマッピングが向上します。

PV カメラからの表示をオプトインするには、次のようにします。

1. **SetEnabledMixedRealityCamera** および **ResizeMixedRealityCamera** の呼び出し
    * **サイズ X** および **サイズ Y** の値を使用して、ビデオのディメンションを設定します。

![第 3 のカメラ](../../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

その後、Unreal は MRC からのリクエストを処理して、PV カメラの視点からレンダリングします。

> [!NOTE]
> [Mixed Reality キャプチャ](../../../mixed-reality-capture.md)がトリガーされた場合にのみ、アプリは写真/ビデオ カメラの視点からレンダリングするよう求められます。

## <a name="using-the-pv-camera"></a>PV カメラの使用

Web カメラ テクスチャは実行時にゲームで入手できますが、エディターの **[編集] > [プロジェクトの設定]** で有効にする必要があります。
1. **[プラットフォーム] > [HoloLens] > [機能]** に移動し、**Web カメラ** を確認します。
    * 実行時に Web カメラを使用するには、**StartCameraCapture** 関数を使用し、記録を停止するには、**StopCameraCapture** 関数を使用します。

![カメラの開始と停止](../images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a>イメージのレンダリング
カメラ イメージをレンダリングするには次のようにします。
1. 以下のスクリーンショットでは **PVCamMat** という名前のプロジェクトのマテリアルに基づいて、ダイナミック マテリアル インスタンスを作成します。  
2. ダイナミック マテリアル インスタンスを **Material Instance Dynamic Object Reference** 変数に設定します。  
3. カメラ フィードをレンダリングするシーン内のオブジェクトのマテリアルを、この新しいダイナミック マテリアル インスタンスに設定します。
    * カメラ イメージをマテリアルにバインドするために使用されるタイマーを開始します。

![カメラのレンダリング](../images/unreal-camera-render.PNG)

4. このタイマーに新しい関数 (この場合は **MaterialTimer**) を作成し、**GetARCameraImage** を呼び出して、Web カメラからテクスチャを取得します。  
5. このテクスチャが有効な場合は、シェーダーのテクスチャ パラメーターをこのイメージに設定します。  そうでない場合は、もう一度素材のタイマーを開始します。

![Web カメラからのカメラ テクスチャ](../images/unreal-camera-texture.PNG)

5. マテリアルに、カラー エントリにバインドされている **SetTextureParameterValue** の名前と一致するパラメーターがあることを確認します。 パラメーターがないと、カメラ イメージを正しく表示できません。

![カメラのテクスチャ](../images/unreal-camera-material.PNG)

