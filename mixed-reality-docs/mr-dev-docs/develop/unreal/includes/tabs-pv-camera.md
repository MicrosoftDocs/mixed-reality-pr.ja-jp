---
ms.openlocfilehash: eb51caa4caf0d425b5e49c3abca2a523b08fc312
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2020
ms.locfileid: "97718117"
---
# <a name="426"></a>[<span data-ttu-id="e97ee-101">4.26</span><span class="sxs-lookup"><span data-stu-id="e97ee-101">4.26</span></span>](#tab/426) 

## <a name="pv-camera-feed-setup"></a><span data-ttu-id="e97ee-102">PV カメラのフィードの設定</span><span class="sxs-lookup"><span data-stu-id="e97ee-102">PV Camera Feed Setup</span></span>

- <span data-ttu-id="e97ee-103">**[プロジェクト設定] > [HoloLens]** で、 **[Web カメラ]** 機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="e97ee-103">In **Project Settings > HoloLens**, enable the **Webcam** capability:</span></span>

![[Web カメラ] プロパティが強調表示されている HoloLens プロジェクト設定のスクリーンショット](../images/unreal-pvc-img-01.png)

- <span data-ttu-id="e97ee-105">"CamCapture" という名前の新しいアクターを作成し、カメラ フィードをレンダリングするための平面を追加します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-105">Create a new actor called “CamCapture” and add a plane to render the camera feed:</span></span>

![平面が追加されたアクターのスクリーンショット](../images/unreal-pvc-img-02.png)

- <span data-ttu-id="e97ee-107">アクターをシーンに追加し、テクスチャ オブジェクト パラメーターとテクスチャ サンプルを使用して、CamTextureMaterial という名前の新しいマテリアルを作成します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-107">Add the actor to your scene, create a new material called CamTextureMaterial with a Texture Object Parameter, and a texture sample.</span></span>  <span data-ttu-id="e97ee-108">テクスチャの RGB データを出力放射色に送信します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-108">Send the texture’s rgb data to the output emissive color:</span></span>

![マテリアルとテクスチャのサンプルのブループリント](../images/unreal-pvc-img-03.png)

## <a name="rendering-the-pv-camera-feed"></a><span data-ttu-id="e97ee-110">PV カメラ フィードのレンダリング</span><span class="sxs-lookup"><span data-stu-id="e97ee-110">Rendering the PV Camera Feed</span></span>

- <span data-ttu-id="e97ee-111">CamCapture ブループリントで、PV カメラをオンにします。</span><span class="sxs-lookup"><span data-stu-id="e97ee-111">In the CamCapture blueprint, turn on the PV Camera:</span></span>

![PV カメラがオンになっている ARCapture 切り替え関数のブループリント](../images/unreal-pvc-img-04.png)

- <span data-ttu-id="e97ee-113">CamTextureMaterial から動的なマテリアル インスタンスを作成し、このマテリアルをアクターの平面に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e97ee-113">Create a dynamic material instance from CamTextureMaterial and assign this material to the actor’s plane:</span></span>

![動的マテリアル インスタンス作成関数のブループリント](../images/unreal-pvc-img-05.png)

- <span data-ttu-id="e97ee-115">カメラ フィードからテクスチャを取得し、有効な場合はそれを動的マテリアルに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e97ee-115">Get the texture from the camera feed and assign it to the dynamic material if it's valid.</span></span>  <span data-ttu-id="e97ee-116">テクスチャが有効でない場合は、タイマーを開始し、タイムアウト後に再試行します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-116">If the texture isn't valid, start a timer and try again after the timeout:</span></span>

![動的マテリアルに割り当てられたカメラ フィード テクスチャのブループリント](../images/unreal-pvc-img-06.png)

- <span data-ttu-id="e97ee-118">最後に、カメラ画像の縦横比で平面を拡大縮小します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-118">Finally, scale the plane by the camera image’s aspect ratio:</span></span>

![カメラ画像の縦横比に合わせて拡大縮小された平面のブループリント](../images/unreal-pvc-img-07.png)

## <a name="find-camera-positions-in-world-space"></a><span data-ttu-id="e97ee-120">ワールド空間でカメラの位置を検索する</span><span class="sxs-lookup"><span data-stu-id="e97ee-120">Find Camera Positions in World Space</span></span>

<span data-ttu-id="e97ee-121">HoloLens 2 のカメラは、デバイスの頭追跡から垂直方向にオフセットされます。</span><span class="sxs-lookup"><span data-stu-id="e97ee-121">The camera on the HoloLens 2 is offset vertically from the device’s head tracking.</span></span>  <span data-ttu-id="e97ee-122">オフセットを考慮するために、ワールド空間内のカメラの位置を調べる関数がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="e97ee-122">A few functions exist to locate the camera in world space to account for the offset.</span></span>

<span data-ttu-id="e97ee-123">GetPVCameraToWorldTransform を使用すると、PV カメラのワールド空間内の変換が取得されて、カメラのレンズに配置されます。</span><span class="sxs-lookup"><span data-stu-id="e97ee-123">GetPVCameraToWorldTransform gets the transform in world space of the PV Camera and will be positioned on the camera lens:</span></span>

![PVCamera からワールド空間への変換の取得関数のブループリント](../images/unreal-pvc-img-08.png)

<span data-ttu-id="e97ee-125">GetWorldSpaceRayFromCameraPoint を使用すると、カメラ フレーム内のピクセルの内容を調べるため、カメラのレンズから Unreal ワールド空間内のシーンに光線がキャストされます。</span><span class="sxs-lookup"><span data-stu-id="e97ee-125">GetWorldSpaceRayFromCameraPoint casts a ray from the camera lens into the scene in Unreal world space to find a pixel's content in the camera frame:</span></span>

![カメラ ポイントからのワールド空間の光線の取得のブループリント](../images/unreal-pvc-img-09.png)

<span data-ttu-id="e97ee-127">GetPVCameraIntrinsics を使用すると、カメラの組み込み値が返されます。カメラ フレームでコンピューター ビジョン処理を行うときにそれを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e97ee-127">GetPVCameraIntrinsics returns the camera intrinsic values, which can be used when doing computer vision processing on a camera frame:</span></span>

![PVCamera 組み込み関数取得のブループリント](../images/unreal-pvc-img-10.png)

<span data-ttu-id="e97ee-129">ワールド空間の特定のピクセル座標に存在するものを調べるには、ワールド空間光線でライン トレースを使用します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-129">To find what exists in world space at a particular pixel coordinate, use a line trace with the world space ray:</span></span>

![ワールド空間の特定のピクセル座標に存在するものを調べるために使用されているワールド空間光線のブループリント](../images/unreal-pvc-img-11.png)

<span data-ttu-id="e97ee-131">ここでは、フレームの左上から ¼ のカメラス空間位置に向けて、カメラのレンズから 2 メートルの光線をキャストします。</span><span class="sxs-lookup"><span data-stu-id="e97ee-131">Here we cast a 2-meter ray from the camera lens to the camera-space position ¼ from the top left of the frame.</span></span>  <span data-ttu-id="e97ee-132">次に、ヒット結果を使用して、ワールド空間内のオブジェクトが存在する場所に何かをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="e97ee-132">Then use the hit result to render something where the object exists in world space:</span></span>

![フレームの左上から 1/4 のカメラス空間位置に向けてカメラのレンズからキャストされる 2 メートルの光線のブループリント](../images/unreal-pvc-img-12.png)

<span data-ttu-id="e97ee-134">空間マッピングを使用している場合、このヒット位置はカメラで見ているサーフェスと一致します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-134">When using spatial mapping, this hit position will match the surface that the camera is seeing.</span></span>

## <a name="rendering-the-pv-camera-feed-in-c"></a><span data-ttu-id="e97ee-135">C++ での PV カメラ フィードのレンダリング</span><span class="sxs-lookup"><span data-stu-id="e97ee-135">Rendering the PV Camera Feed in C++</span></span>

- <span data-ttu-id="e97ee-136">CamCapture という名前の新しい C++ アクターを作成します</span><span class="sxs-lookup"><span data-stu-id="e97ee-136">Create a new C++ actor called CamCapture</span></span>
- <span data-ttu-id="e97ee-137">プロジェクトの build.cs で、"AugmentedReality" を PublicDependencyModuleNames リストに追加します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-137">In the project’s build.cs, add “AugmentedReality” to the PublicDependencyModuleNames list:</span></span>

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

- <span data-ttu-id="e97ee-138">CamCapture.h で、ARBlueprintLibrary.h をインクルードします</span><span class="sxs-lookup"><span data-stu-id="e97ee-138">In CamCapture.h, include ARBlueprintLibrary.h</span></span>

```cpp
#include "ARBlueprintLibrary.h"
```

- <span data-ttu-id="e97ee-139">また、メッシュとマテリアルのローカル変数を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e97ee-139">You also need to add local variables for the mesh and material:</span></span>

```cpp
private:
    UStaticMesh* StaticMesh;
    UStaticMeshComponent* StaticMeshComponent;
    UMaterialInstanceDynamic* DynamicMaterial;
    bool IsTextureParamSet = false;
```

- <span data-ttu-id="e97ee-140">CamCapture.cpp で、静的メッシュをシーンに追加するようにコンストラクターを更新します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-140">In CamCapture.cpp, update the constructor to add a static mesh to the scene:</span></span>

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

<span data-ttu-id="e97ee-141">BeginPlay で、プロジェクトのカメラ マテリアルから動的マテリアルのインスタンスを作成し、それを静的メッシュ コンポーネントに適用して、HoloLens カメラを開始します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-141">In BeginPlay create a dynamic material instance from the project’s camera material, apply it to the static mesh component, and start the HoloLens camera.</span></span> 
 
<span data-ttu-id="e97ee-142">エディターのコンテンツ ブラウザーで CamTextureMaterial を右クリックし、[参照のコピー] を選択して、CameraMatPath の文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-142">In the editor, right-click on the CamTextureMaterial in the content browser and select “Copy Reference” to get the string for CameraMatPath.</span></span>

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

<span data-ttu-id="e97ee-143">Tick で、カメラからテクスチャを取得し、それを CamTextureMaterial マテリアルのテクスチャ パラメーターに設定して、カメラ フレームの縦横比で静的メッシュ コンポーネントを拡大縮小します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-143">In Tick get the texture from the camera, set it to the texture parameter in the CamTextureMaterial material, and scale the static mesh component by the camera frame’s aspect ratio:</span></span>

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

# <a name="425"></a>[<span data-ttu-id="e97ee-144">4.25</span><span class="sxs-lookup"><span data-stu-id="e97ee-144">4.25</span></span>](#tab/425)

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="e97ee-145">MRC 用の PV カメラからのレンダリング</span><span class="sxs-lookup"><span data-stu-id="e97ee-145">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="e97ee-146">これには **Unreal Engine 4.25** 以降のバージョンが必要です。</span><span class="sxs-lookup"><span data-stu-id="e97ee-146">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="e97ee-147">システムとカスタム MRC レコーダーにより、PV カメラをアプリによってレンダリングされたホログラムと組み合わせることにより、Mixed Reality キャプチャが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e97ee-147">The system and custom MRC recorders create mixed reality captures by combining the PV Camera with holograms rendered by the app.</span></span>

<span data-ttu-id="e97ee-148">既定では、Mixed Reality キャプチャでは、右目のホログラフィック出力が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e97ee-148">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="e97ee-149">イマーシブ アプリによって [PV カメラ](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)からのレンダリングが選択された場合は、それが代わりに使用されます。</span><span class="sxs-lookup"><span data-stu-id="e97ee-149">If an immersive app chooses to [render from the PV Camera](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), then that will be used instead.</span></span> <span data-ttu-id="e97ee-150">PV カメラからレンダリングすることにより、現実世界と MRC ビデオのホログラムとの間のマッピングが向上します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-150">Rendering from the PV Camera improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="e97ee-151">PV カメラからの表示をオプトインするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="e97ee-151">To opt in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="e97ee-152">**SetEnabledMixedRealityCamera** および **ResizeMixedRealityCamera** の呼び出し</span><span class="sxs-lookup"><span data-stu-id="e97ee-152">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="e97ee-153">**サイズ X** および **サイズ Y** の値を使用して、ビデオのディメンションを設定します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-153">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![第 3 のカメラ](../../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

<span data-ttu-id="e97ee-155">その後、Unreal は MRC からのリクエストを処理して、PV カメラの視点からレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="e97ee-155">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="e97ee-156">[Mixed Reality キャプチャ](../../../mixed-reality-capture.md)がトリガーされた場合にのみ、アプリは写真/ビデオ カメラの視点からレンダリングするよう求められます。</span><span class="sxs-lookup"><span data-stu-id="e97ee-156">Only when [Mixed Reality Capture](../../../mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="e97ee-157">PV カメラの使用</span><span class="sxs-lookup"><span data-stu-id="e97ee-157">Using the PV Camera</span></span>

<span data-ttu-id="e97ee-158">Web カメラ テクスチャは実行時にゲームで入手できますが、エディターの **[編集] > [プロジェクトの設定]** で有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e97ee-158">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="e97ee-159">**[プラットフォーム] > [HoloLens] > [機能]** に移動し、**Web カメラ** を確認します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-159">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="e97ee-160">実行時に Web カメラを使用するには、**StartCameraCapture** 関数を使用し、記録を停止するには、**StopCameraCapture** 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-160">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![カメラの開始と停止](../images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="e97ee-162">イメージのレンダリング</span><span class="sxs-lookup"><span data-stu-id="e97ee-162">Rendering an image</span></span>
<span data-ttu-id="e97ee-163">カメラ イメージをレンダリングするには次のようにします。</span><span class="sxs-lookup"><span data-stu-id="e97ee-163">To render the camera image:</span></span>
1. <span data-ttu-id="e97ee-164">以下のスクリーンショットでは **PVCamMat** という名前のプロジェクトのマテリアルに基づいて、ダイナミック マテリアル インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-164">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="e97ee-165">ダイナミック マテリアル インスタンスを **Material Instance Dynamic Object Reference** 変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-165">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="e97ee-166">カメラ フィードをレンダリングするシーン内のオブジェクトのマテリアルを、この新しいダイナミック マテリアル インスタンスに設定します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-166">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="e97ee-167">カメラ イメージをマテリアルにバインドするために使用されるタイマーを開始します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-167">Start a timer that will be used to bind the camera image to the material.</span></span>

![カメラのレンダリング](../images/unreal-camera-render.PNG)

4. <span data-ttu-id="e97ee-169">このタイマーに新しい関数 (この場合は **MaterialTimer**) を作成し、**GetARCameraImage** を呼び出して、Web カメラからテクスチャを取得します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-169">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="e97ee-170">このテクスチャが有効な場合は、シェーダーのテクスチャ パラメーターをこのイメージに設定します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-170">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="e97ee-171">そうでない場合は、もう一度素材のタイマーを開始します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-171">Otherwise, start the material timer again.</span></span>

![Web カメラからのカメラ テクスチャ](../images/unreal-camera-texture.PNG)

5. <span data-ttu-id="e97ee-173">マテリアルに、カラー エントリにバインドされている **SetTextureParameterValue** の名前と一致するパラメーターがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e97ee-173">Make sure the material has a parameter that matches the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="e97ee-174">パラメーターがないと、カメラ イメージを正しく表示できません。</span><span class="sxs-lookup"><span data-stu-id="e97ee-174">Without the parameter, the camera image can't be displayed properly.</span></span>

![カメラのテクスチャ](../images/unreal-camera-material.PNG)

