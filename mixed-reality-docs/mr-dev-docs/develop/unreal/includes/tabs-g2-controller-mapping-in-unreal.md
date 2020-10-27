---
ms.openlocfilehash: 85792491eb4c349eea3dac4ae227c6736d7a90c2
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638727"
---
# <a name="all-platforms"></a>[すべてのプラットフォーム](#tab/all)

ゲームの入力プロジェクト設定では、同じアクションと軸のマッピングを C++ から使用できます。

1. ファイル/新しい C++ クラスを使用して新しい C++ クラスを作成します...

![新しい C++ クラスの作成](../images/reverb-g2-img-11.png)

2. ポーンを作成する

![ポーンの作成](../images/reverb-g2-img-12.png)

3. プロジェクトの Visual Studio ソリューションで、新しいポーンクラスを見つけて、それを入力用に構成します。
* まず、コンストラクターで、AutoPossessPlayer を最初のプレーヤーに設定して、入力をポーンにルーティングします。

```cpp
AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;

    AutoPossessPlayer = EAutoReceiveInput::Player0;
}
```

* 次に、SetupPlayerInputComponent で、アクションと軸イベントをプロジェクトの入力設定のアクション名にバインドします。

```cpp
void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);

    PlayerInputComponent->BindAction("X_Button", IE_Pressed, this, &AMyPawn::XPressed);
    PlayerInputComponent->BindAction("L_GripAxis", this, &AMyPawn::LeftGripAxis);
}
```

* クラスにコールバック関数を追加します。

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

* 次のコールバック関数定義で、ポーンのヘッダーを更新します。

```cpp
private:
    void XPressed();
    void LeftGripAxis(float AxisValue);
```

4. 新しいポーンでエディターを起動するには、Visual Studio からコンパイルします。 コンテンツブラウザーからポーンをゲームにドラッグアンドドロップすると、入力が押されたときにポーンがコールバックを実行するようになります。

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

サムスティック軸イベントを使用する場合、軸イベントの名前は、使用するキーに対応する "_X" または "_Y" で終わる必要があります。

![サムスティックイベントの使用](../images/reverb-g2-img-09.png)

最後に、[プロジェクトの設定] の [ **アクションマニフェストの再生成** ] ボタンと [ **コントローラーのバインドの再生成** ] ボタンを使用して、steamvr でゲームにアクションを登録します > 蒸気 VR 入力します。

![プロジェクト設定でのアクションの登録](../images/reverb-g2-img-10.png)

