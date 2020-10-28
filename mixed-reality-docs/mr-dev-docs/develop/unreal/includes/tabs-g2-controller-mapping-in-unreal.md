---
ms.openlocfilehash: 85792491eb4c349eea3dac4ae227c6736d7a90c2
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638727"
---
# <a name="all-platforms"></a>[<span data-ttu-id="e62a0-101">すべてのプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="e62a0-101">All platforms</span></span>](#tab/all)

<span data-ttu-id="e62a0-102">ゲームの入力プロジェクト設定では、同じアクションと軸のマッピングを C++ から使用できます。</span><span class="sxs-lookup"><span data-stu-id="e62a0-102">The same action and axis mappings in the game’s input project settings can be used from C++.</span></span>

1. <span data-ttu-id="e62a0-103">ファイル/新しい C++ クラスを使用して新しい C++ クラスを作成します...</span><span class="sxs-lookup"><span data-stu-id="e62a0-103">Create a new C++ Class with File/New C++ Class...</span></span>

![新しい C++ クラスの作成](../images/reverb-g2-img-11.png)

2. <span data-ttu-id="e62a0-105">ポーンを作成する</span><span class="sxs-lookup"><span data-stu-id="e62a0-105">Create a pawn</span></span>

![ポーンの作成](../images/reverb-g2-img-12.png)

3. <span data-ttu-id="e62a0-107">プロジェクトの Visual Studio ソリューションで、新しいポーンクラスを見つけて、それを入力用に構成します。</span><span class="sxs-lookup"><span data-stu-id="e62a0-107">In the project’s Visual Studio solution, find the new Pawn class and configure it for input.</span></span>
* <span data-ttu-id="e62a0-108">まず、コンストラクターで、AutoPossessPlayer を最初のプレーヤーに設定して、入力をポーンにルーティングします。</span><span class="sxs-lookup"><span data-stu-id="e62a0-108">First, in the constructor, set AutoPossessPlayer to the first player to route input to the pawn.</span></span>

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* <span data-ttu-id="e62a0-109">次に、SetupPlayerInputComponent で、アクションと軸イベントをプロジェクトの入力設定のアクション名にバインドします。</span><span class="sxs-lookup"><span data-stu-id="e62a0-109">Then in SetupPlayerInputComponent, bind actions and axis events to the action names from the project’s input settings.</span></span>

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* <span data-ttu-id="e62a0-110">クラスにコールバック関数を追加します。</span><span class="sxs-lookup"><span data-stu-id="e62a0-110">Add the callback functions to the class:</span></span>

```cpp
void AMyPawn::XPressed()
{
    UE_LOG(LogTemp, Log, TEXT("X Pressed"));
}

void AMyPawn::LeftGripAxis(float AxisValue)
{
    if(AxisValue != 0.0f) 
    {
        UE_LOG(LogTemp, Log, TEXT("Left Grip Axis Valule: %f"), AxisValue);
    }
}
```

* <span data-ttu-id="e62a0-111">次のコールバック関数定義で、ポーンのヘッダーを更新します。</span><span class="sxs-lookup"><span data-stu-id="e62a0-111">Update the Pawn’s header with the callback function definitions:</span></span>

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. <span data-ttu-id="e62a0-112">新しいポーンでエディターを起動するには、Visual Studio からコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="e62a0-112">Compile from Visual Studio to launch the editor with the new pawn.</span></span> <span data-ttu-id="e62a0-113">コンテンツブラウザーからポーンをゲームにドラッグアンドドロップすると、入力が押されたときにポーンがコールバックを実行するようになります。</span><span class="sxs-lookup"><span data-stu-id="e62a0-113">Drag and drop the pawn from the content browser into the game and the pawn will now execute the callbacks when input is pressed.</span></span>

# <a name="steamvr"></a>[<span data-ttu-id="e62a0-114">SteamVR</span><span class="sxs-lookup"><span data-stu-id="e62a0-114">SteamVR</span></span>](#tab/steamvr)

<span data-ttu-id="e62a0-115">サムスティック軸イベントを使用する場合、軸イベントの名前は、使用するキーに対応する "_X" または "_Y" で終わる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e62a0-115">When using thumbstick axis events, the name of the axis event must end in “_X” or “_Y” corresponding to the key used.</span></span>

![サムスティックイベントの使用](../images/reverb-g2-img-09.png)

<span data-ttu-id="e62a0-117">最後に、[プロジェクトの設定] の [ **アクションマニフェストの再生成** ] ボタンと [ **コントローラーのバインドの再生成** ] ボタンを使用して、steamvr でゲームにアクションを登録します > 蒸気 VR 入力します。</span><span class="sxs-lookup"><span data-stu-id="e62a0-117">Finally, register the actions in the game with SteamVR by using the **Regenerate Action Manifest** and **Regenerate Controller Bindings** buttons in Project Settings > Steam VR Input.</span></span>

![プロジェクト設定でのアクションの登録](../images/reverb-g2-img-10.png)

