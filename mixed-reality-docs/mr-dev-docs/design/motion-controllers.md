---
title: モーション コントローラー
description: Mixed Reality モーションコントローラーの詳細。
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 6dof コントローラー、モーションコントローラー、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、スクロール、グリップ、状態
ms.openlocfilehash: a1af86ca174bc574ab8030d8aebd128649b6515f
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703158"
---
# <a name="motion-controllers"></a>モーション コントローラー

:::row:::
    :::column:::
        モーションコントローラーは、ユーザーが mixed reality でアクションを実行できるようにする [ハードウェアアクセサリ](../discover/hardware-accessories.md) です。 [ジェスチャ](gaze-and-commit.md#composite-gestures)を使用したモーションコントローラーの利点は、コントローラーが領域内に正確な位置を持ち、デジタルオブジェクトと詳細に対話できることです。 Windows Mixed Reality イマーシブヘッドセットの場合、モーションコントローラーは、ユーザーが世界中でアクションを実行する主な方法です。<br>
        <br>
        *イメージ: Windows Mixed Reality モーションコントローラー*
    :::column-end:::
        :::column:::
       ![Windows Mixed Reality モーションコントローラー](images/winmr-ck-1080x1080-350px.jpg)<br> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="device-support"></a>デバイス サポート

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>機能</strong></td>
     <td><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
</tr>
<tr>
     <td>モーション コントローラー</td>
     <td>❌</td>
     <td>❌</td>
     <td>✔️</td>
</tr>
</table>

## <a name="hardware-details"></a>ハードウェアの詳細

<iframe width="940" height="530" src="https://www.youtube.com/embed/1nlcdDNOdm8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Windows Mixed Reality モーションコントローラーは、イマーシブヘッドセットのセンサーを使用して、ビューのフィールド内の移動を正確かつ迅速に追跡できます。つまり、領域内の壁にハードウェアを取り付ける必要はありません。 これらのモーションコントローラーは、Windows Mixed Reality のイマーシブヘッドセットと同じように簡単なセットアップと移植性を提供します。 デバイスパートナーは、この休日を利用して、これらのコントローラーを小売店で販売し、販売する予定です。

![コントローラーを知る](images/controllerimage-750px.png)<br>
*コントローラーを知る*

**機能:**
* 光学式の追跡
* トリガー
* グラブボタン
* スティック
* Touchpad

## <a name="setup"></a>セットアップ

### <a name="before-you-begin"></a>始める前に

**以下のものが必要になります。**
* 2つのモーションコントローラーのセット。
* 4つの AA バッテリ。
* Bluetooth 4.0 に対応した PC。

**Windows、Unity、ドライバーの更新プログラムを確認する**
* Mixed reality 開発については、「Windows、Unity、その他のバージョン用の [ツールをインストール](../develop/install-the-tools.md) する」を参照してください。
* 最新の [ヘッドセットとモーションコントローラードライバー](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)があることを確認します。

### <a name="pairing-controllers"></a>コントローラーのペアリング

モーションコントローラーは、他の Bluetooth デバイスと同様に、Windows 設定を使用してホスト PC と結合できます。

1. 2つの AA 乾電池をコントローラーの背面に挿入します。 ここではバッテリカバーをオフのままにします。
2. 組み込みの Bluetooth ラジオではなく外部 USB Bluetooth アダプターを使用している場合は、先に進む前に、 [bluetooth のベストプラクティス](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) を確認してください。 組み込みのラジオを使用したデスクトップ構成の場合は、アンテナが接続されていることを確認します。
3. [ **Windows 設定**  ->  ] [**デバイス**  ->  ] を開き、**bluetooth またはその他のデバイス**  ->  **bluetooth** を追加し、以前の "motion controller – Right" と "motion controller – Left" のインスタンスをすべて削除します。 一覧の下部にある [その他のデバイス] カテゴリも確認します。
4. [ **Bluetooth またはその他のデバイスの追加** ] を選択すると、bluetooth デバイスの検出が開始されます。
5. コントローラーの [Windows] ボタンを押してコントローラーをオンにすると、buzzes すると解放されます。
6. Led の発するが開始されるまで、ペアリングボタン (バッテリコンパートメントのタブ) を押したままにします。

:::row:::
    :::column:::
7. リストの一番下に "Motion controller-Left" または "Motion controller-Right" が表示されるまで待ちます。 ペアにする場合に選択します。 接続されると、コントローラーは1回バイブレーションされます。<br>
        <br>
        *イメージ: ペアにする "モーションコントローラー" を選択します。複数のインスタンスがある場合は、一覧の一番下から1つを選択します。*
    :::column-end:::
        :::column:::
       ![ペアにするモーションコントローラーを選択します。複数のインスタンスがある場合は、一覧の下部に表示されます。](images/450px-bluetooth-add-a-device-300px.png)<br> 
    :::column-end:::
:::row-end:::
   
8. [**マウス、キーボード、& ペン] カテゴリ** の [Bluetooth 設定] にコントローラーが表示 **されます。** この時点で、ファームウェアの更新プログラムを入手できます。 [次のセクション](motion-controllers.md#updating-controller-firmware)を参照してください。
9. バッテリカバーを再接続します。
10. 2番目のコントローラーに対して手順1-9 を繰り返します。

<br>

:::row:::
    :::column:::
        両方のコントローラーが正常にペアリングされると、設定は次のようになります。 [**マウス、キーボード、& ペン] カテゴリ** の下に表示されます。 <br>
        <br>
        *画像: モーションコントローラーが接続されました*
    :::column-end:::
        :::column:::
       ![接続コントローラー](images/450px-motion-controller-connected-300px.png)<br>
    :::column-end:::
:::row-end:::

ペアリング後にコントローラーがオフになっている場合、それらの状態はペアとして表示されます。 コントローラーが "その他のデバイス" カテゴリのままになっている場合は、ペアリングが部分的にしか完了していないため、コントローラーを機能させるにはもう一度実行する必要があります。

### <a name="updating-controller-firmware"></a>コントローラーのファームウェアを更新しています

* イマーシブヘッドセットが PC に接続されていて、新しいコントローラーファームウェアが利用可能な場合、次に電源がオンになったときに、そのファームウェアが自動的にモーションコントローラーにプッシュされます。 コントローラーファームウェアの更新プログラムは、円形の動きにおける LED のある領域を照明するパターンによって示され、1-2 分かかります。


:::row:::
    :::column:::
* ファームウェアの更新が完了すると、コントローラーが再起動して再接続されます。 両方のコントローラーがすぐに接続されている必要があります。 <br>
        <br>
        *イメージ: Bluetooth 設定で接続されているコントローラー*
    :::column-end:::
        :::column:::
       ![接続されたコントローラー](images/cyk-connected-300px.jpg)<br>
    :::column-end:::
:::row-end:::


* コントローラーが正常に動作することを確認します。
    1. **Mixed Reality ポータル** を起動し、Mixed reality ホームを入力します。
    2. コントローラーを移動し、追跡、テストボタンを確認して、 [テレ](../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) を確認します。 そうでない場合は、「 [モーションコントローラーのトラブルシューティング](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers)」をご覧ください。

## <a name="gazing-and-pointing"></a>ガスとポイント

Windows Mixed Reality では、対話のために2つの主要なモデルがサポートされます。 **宝石を見つめ、コミット** して、 **ポイントアンドコミット** します。
* ユーザーは、 **宝石とコミット** を使用して、オブジェクトを [宝石](gaze-and-commit.md) として選択し、ハンドタップ、ゲームパッド、clicker、または音声を使用してオブジェクトを選択します。
* **ポイントとコミット** を使用すると、ユーザーは、ポイント対応のモーションコントローラーをターゲットオブジェクトでターゲットにして、コントローラーのトリガーを持つオブジェクトを選択できます。

また、モーションコントローラーを使用したポイントをサポートするアプリでは、可能な場合は、ユーザーが使用する入力デバイスにユーザーが選択できるようにすることもできます。

### <a name="managing-recoil-when-pointing"></a>ポイント時の recoil の管理

モーションコントローラーを使用してポイントアンドコミットする場合、ユーザーはコントローラーを使用してターゲットを指定し、トリガーをプルすることによってアクションを実行します。 トリガーの vigorously を取得したユーザーは、意図したものよりも、トリガーをプルした時点よりも先にコントローラーの位置を上げる可能性があります。

ユーザーがトリガーをプルしたときに発生する可能性のある recoil を管理するために、トリガーのアナログ軸の値が0.0 を超えたときに、アプリでターゲットの射線をスナップできます。 その後、最後の押しが短い時間枠で実行される限り、後で、トリガー値が1.0 になると、そのターゲットを使用してアクションを実行できます。 高レベルの [複合タップジェスチャ](gaze-and-commit.md#composite-gestures)を使用すると、このターゲット設定を制御することになります。

## <a name="grip-pose-vs-pointing-pose"></a>グリップポーズとポインティングポーズ

Windows Mixed Reality では、さまざまなフォームファクターでモーションコントローラーがサポートされています。各コントローラーの設計は、ユーザーの手の位置と、アプリがコントローラーを表示するときに使用する自然な "進む" 方向との間の関係において異なります。

これらのコントローラーをより適切に表現するために、相互作用ソースごとに調査できる2種類の方法があります。 **グリップ** と **ポインター** があります。

### <a name="grip-pose"></a>グリップの原因

**グリップ** は、HoloLens によって検出された、または運動コントローラーを持つパームのいずれかの場所を表します。

イマーシブヘッドセットでは、グリップは、 **ユーザーの手** や、剣や銃など、 **ユーザーの手に保持** されているオブジェクトをレンダリングするために最適です。 また、このグリップは、モーションコントローラーを視覚化するときにも使用されます。これは、モーションコントローラー用に Windows によって提供される **描画モデル** が、グリップを原点と回転の中心として使用するためです。

グリップは、次のように明確に定義されます。
* **グリップの位置**: コントローラーを自然に保持するときのパーム重心。グリップ内の位置を中央に配置するように左右に調整されます。 Windows Mixed Reality モーションコントローラーでは、通常、この位置はボタンをつかみに揃えて配置されます。
* **グリップの向きの右軸**: 手を完全に開いて平らな5本の指を作成した場合 (左側のパームから前方、右側のパームから後方)、
* **グリップの向きの前方軸**: ハンドを部分的に閉じた場合 (コントローラーを保持している場合と同様)、非表示の指で形成されたチューブを通過する光線。
* **グリップの向きの上位軸**: 右および順方向の定義によって暗黙的に示される上位軸。

### <a name="pointer-pose"></a>ポインターのポーズ

**ポインター** は、前方にあるコントローラーの先端を表します。

システム指定のポインターの raycast は、 **コントローラーモデル自体をレンダリング** するときに最もよく使用されます。 仮想銃など、コントローラーの代わりに他の仮想オブジェクトをレンダリングする場合は、アプリ定義の銃モデルの胴体に沿って移動する射線など、その仮想オブジェクトに最も適した光線をポイントする必要があります。 ユーザーは物理コントローラーではなく仮想オブジェクトを見ることができるため、仮想オブジェクトをポイントすると、アプリを使用している方がより自然な場合があります。

## <a name="controller-tracking-state"></a>コントローラー追跡状態

ヘッドセットと同様に、Windows Mixed Reality モーションコントローラーでは、外部の追跡センサーを設定する必要がありません。 代わりに、コントローラーはヘッドセット自体のセンサーによって追跡されます。

ユーザーがヘッドセットのビューのフィールドからコントローラーを移動した場合、ほとんどの場合、Windows はコントローラーの位置を推測してアプリに提供し続けます。 コントローラーのビジュアル追跡が十分に失われた場合、コントローラーの位置はおおよその精度の位置にドロップします。

この時点で、システムはコントローラーをユーザーにボディロックし、ユーザーが移動したときの位置を追跡しながら、内部方向センサーを使用してコントローラーの真向きを公開します。 UI 要素をポイントしてアクティブ化するためにコントローラーを使用する多くのアプリは、ユーザーに気付かなくても、おおよその精度で正常に動作できます。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/rkDpRllbLII" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### <a name="reasoning-about-tracking-state-explicitly"></a>状態の明示的な追跡に関する推論

追跡の状態に基づいて位置を異なる方法で処理する必要があるアプリは、さらに詳細になり、コントローラーの状態 (SourceLossRisk や PositionAccuracy など) のプロパティを検査することができます。

<table>
<tr>
<th> 状態の追跡 </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>高精度</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>高精度 (消失のリスク)</b> </td><td style="background-color: orange"> = = 1.0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>おおよその精度</b> </td><td style="background-color: orange"> = = 1.0 </td><td style="background-color: orange"> Approximate </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>位置なし</b> </td><td style="background-color: orange"> = = 1.0 </td><td style="background-color: orange"> Approximate </td><td style="background-color: orange"> False</td>
</tr>
</table>



これらのモーションコントローラーの追跡状態は、次のように定義されています。
* **高精度:** モーションコントローラーは、ヘッドセットのビューに含まれていますが、通常、ビジュアルの追跡に基づいて高精度の位置を提供します。 ビューまたはのフィールドから瞬間的に見えない移動コントローラーは、(ユーザーの他の手によって) ヘッドセットセンサーから瞬間的に見えなくなっていることに注意してください。これは、コントローラー自体の慣性追跡に基づいて、短時間で高精度のポーズを返します。
* **高精度 (損失のリスク):** ユーザーが、ヘッドセットのビューの端を越えてモーションコントローラーを動かすと、ヘッドセットはすぐにコントローラーの位置を視覚的に追跡できなくなります。 アプリでは、 **SourceLossRisk** が1.0 に到達して、コントローラーがこの視界の境界に達したことを認識します。 その時点で、アプリは、非常に高品質なポーズの安定したストリームを必要とするコントローラージェスチャを一時停止することを選択できます。
* **おおよその精度:** コントローラーのビジュアル追跡が十分に失われた場合、コントローラーの位置はおおよその精度の位置にドロップします。 この時点で、システムはコントローラーをユーザーにボディロックし、ユーザーが移動したときの位置を追跡しながら、内部方向センサーを使用してコントローラーの真向きを公開します。 UI 要素をポイントしてアクティブ化するためにコントローラーを使用する多くのアプリは、ユーザーに気付かずに正確な精度で、通常どおりに動作できます。 入力要件が重いアプリでは、 **positionaccuracy** プロパティを調べることによって、精度が **高い** ことを **意味します**。たとえば、この期間中にユーザーに対して、オフスクリーンのターゲットに対してより多くのヒットボックスを与えることができます。
* **位置なし:** コントローラーは長時間の精度で実行できますが、本体でロックされている位置が現時点では意味を持たないことをシステムが認識している場合があります。 たとえば、電源が入っていたコントローラーが視覚的に観察されていない場合や、ユーザーがコントローラーを停止した後に他のユーザーが選択した場合などです。 これらのタイミングでは、システムはアプリに位置を提供せず、 **TryGetPosition** は false を返します。

## <a name="interactions-low-level-spatial-input"></a>相互作用: 低レベルの空間入力

ハンズオンコントローラーとモーションコントローラーの間の主要な相互作用は、 **選択**、 **メニュー**、 **つかみ**、 **タッチパッド**、 **サムスティック**、および **ホーム** です。
* **選択** は、ホログラムをアクティブにするための主要な相互作用です。これは、プレスとその後のリリースで構成されます。 モーションコントローラーの場合は、コントローラーのトリガーを使用して、選択したプレスを実行します。 選択を実行する他の方法として、 [音声コマンド](voice-input.md) "Select" を読み上げます。 同じ選択操作を任意のアプリ内で使用できます。 Select は、マウスのクリックと同等のものと考えることができます。1回学習してからすべてのアプリに適用する、ユニバーサルアクション。
* **メニュー** は、オブジェクトを操作するための二次的な相互作用であり、コンテキストメニューを取得したり、他のセカンダリアクションを実行したりするために使用されます。 モーションコントローラーを使用すると、コントローラーの *メニュー* ボタンを使用してメニュー操作を行うことができます。 (例: ハンバーガー "menu" アイコンが付いたボタン)
* **理解** することは、ユーザーが直接オブジェクトを操作して操作できるようにする方法です。 モーションコントローラーを使用すると、最初に厳密につかんで操作を実行できます。 モーションコントローラーは、グラブボタン、パームトリガー、またはその他のセンサーを使用して、つかみを検出する場合があります。
* **タッチパッド** を使用すると、ユーザーは、モーションコントローラーのタッチパッドの表面に沿って2つのディメンションのアクションを調整し、タッチパッドの [下へ] をクリックしてアクションをコミットできます。 タッチパッド向けは、押された状態、タッチされた状態、および正規化された XY 座標を提供します。 X と Y の範囲は、円形のタッチパッドの範囲で、中央は (0, 0) です。 X の場合、-1 は左に、1は右側にあります。 Y の場合、-1 が一番下にあり、1が一番上にあります。
* **サムスティック** を使用すると、ユーザーは、モーションコントローラーのサムスティックを円形の範囲内に移動することで、2つのディメンションのアクションを調整できます。これにより、サムスティック上で [下へ] をクリックしてアクションをコミットできます。 Thumbsticks は、押された状態と正規化された XY 座標も提供します。 X と Y の範囲は、円形のタッチパッドの範囲で、中央は (0, 0) です。 X の場合、-1 は左に、1は右側にあります。 Y の場合、-1 が一番下にあり、1が一番上にあります。
* **Home** は、[スタート] メニューに戻るために使用される特殊なシステムアクションです。 これは、キーボード上で Windows キーを押すか、Xbox コントローラーの Xbox ボタンを押すことと似ています。 モーションコントローラーの Windows ボタンを押すと、ホームに進むことができます。 まず、"Cortana, 帰宅してください" と言うと、いつでも開始できます。 アプリは、システムによって処理されるため、特にホームアクションに対応することはできません。

## <a name="composite-gestures-high-level-spatial-input"></a>複合ジェスチャ: 高度な空間入力

[ハンドジェスチャ](gaze-and-commit.md#composite-gestures)とモーションコントローラーはどちらも、高レベルの **[複合ジェスチャ](gaze-and-commit.md#composite-gestures)** の共通セットを検出するために、時間の経過と共に追跡できます。 これにより、アプリは、ユーザーがハンドまたはコントローラーを使用するかどうかにかかわらず、高レベルの **タップ**、 **保持**、 **操作** 、および **ナビゲーション** ジェスチャを検出できます。

## <a name="rendering-the-motion-controller-model"></a>モーションコントローラーモデルのレンダリング

**3d コントローラーモデル** Windows は、システムで現在アクティブになっている各モーションコントローラーの描画モデルをアプリで使用できるようにします。 アプリケーションが実行時にこれらのシステム提供のコントローラーモデルを動的に読み込んで明確にすることにより、アプリが将来のコントローラー設計に確実に上位互換性を持つようにすることができます。

これらの描画モデルは、モデルの原点が物理的な世界のこのポイントにアラインされるため、コントローラーの **グリップ** によってレンダリングされる必要があります。 コントローラーモデルをレンダリングしている場合は、コントローラーの物理的な設計に基づいて、ユーザーが自然に指していることを示す光線を表す、 **ポインターのポーズ** からシーンに raycast することができます。

Unity でコントローラーモデルを動的に読み込む方法の詳細については、「 [unity でのモーションコントローラーモデルのレンダリング](../develop/unity/gestures-and-motion-controllers-in-unity.md#rendering-the-motion-controller-model-in-unity) 」セクションを参照してください。

**2d コントローラーのラインアート** App controller のヒントとコマンドを app controller モデル自体にアタッチすることをお勧めしますが、開発者によっては、単純な "チュートリアル" または "操作方法" の UI で、モーションコントローラーの2D ラインアート表現を使用することをお勧めします。 これらの開発者にとっては、次の黒と白の両方で、.png のモーションコントローラーのラインアートファイルを使用できるようにしました (右クリックして保存します)。

![モーションコントローラーのラインアートのプレビュー](images/motioncontrollers-black-preview-300px.png)

[' ' ' 白 ' ' ' の完全解像度のモーションコントローラーのラインアート](images/motioncontrollers-white.png)
 
[' ' ' Black ' ' ' の完全解像度のモーションコントローラーのラインアート](images/motioncontrollers-black.png)

## <a name="faq"></a>よく寄せられる質問

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a>複数の Pc にモーションコントローラーを組み合わせることはできますか。

モーションコントローラーは、1台の PC とのペアリングをサポートしています。 [モーションコントローラーのセットアップ](motion-controllers.md#setup)の指示に従って、コントローラーをペアリングします。

### <a name="how-do-i-update-motion-controller-firmware"></a>モーションコントローラーのファームウェアを更新操作方法ますか?

モーションコントローラーのファームウェアはヘッドセットドライバーの一部であり、必要に応じて、接続時に自動的に更新されます。 通常、ファームウェアの更新は、Bluetooth ラジオとリンクの品質に応じて1-2 分かかります。 まれに、コントローラーのファームウェアの更新に最大で10分かかる場合があります。これは、Bluetooth 接続や無線の干渉が低いことを示している可能性があります。 接続の問題をトラブルシューティングする方法について [は、「Bluetooth のベストプラクティス](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) 」を参照してください。 ファームウェアの更新後、コントローラーは再起動し、ホスト PC に再接続します (Led が監視に対して明るくなることがあります)。 ファームウェアの更新が中断された場合 (たとえば、コントローラーの電源が切れている場合)、次にコントローラーの電源がオンになったときにもう一度試行されます。

### <a name="how-i-can-check-battery-level"></a>バッテリレベルを確認するにはどうすればよいですか。

[Windows Mixed Reality ホーム](../discover/navigating-the-windows-mixed-reality-home.md)では、コントローラーの電源を入れて、仮想モデルの反対側のバッテリレベルを確認できます。 物理的なバッテリレベルインジケーターはありません。

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>ヘッドセットなしでこれらのコントローラーを使用できますか。 ジョイスティック/トリガー/その他の入力に対してのみ

ユニバーサル Windows アプリケーションでは使用できません。

## <a name="troubleshooting"></a>トラブルシューティング

ファンガイドの「 [モーションコントローラーのトラブルシューティング](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers) 」を参照してください。

## <a name="filing-motion-controller-feedbackbugs"></a>モーションコントローラーのフィードバック/バグのファイリング

"Mixed Reality-> 入力" カテゴリを使用してフィードバックハブに[フィードバックをお](../give-us-feedback.md)寄せください。

## <a name="see-also"></a>関連項目
* [Unity でのジェスチャとモーション コントローラー](../develop/unity/gestures-and-motion-controllers-in-unity.md)
* [DirectX での手とモーション コントローラー](../develop/native/hands-and-motion-controllers-in-directx.md)
* [ジェスチャ](gaze-and-commit.md#composite-gestures)
* [愛好家ガイド: Windows Mixed Reality ホーム](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [愛好家ガイド: Windows Mixed Reality でのゲーム & アプリの使用](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [インサイドアウト追跡のしくみ](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/tracking-system)
