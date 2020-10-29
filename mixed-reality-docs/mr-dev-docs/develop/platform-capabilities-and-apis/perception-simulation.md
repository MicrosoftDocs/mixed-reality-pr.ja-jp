---
title: 認識シミュレーション
description: 知覚シミュレーションライブラリを使用して、イマーシブアプリケーションのシミュレートされた入力を自動化するためのガイド
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: HoloLens、シミュレーション、テスト
ms.openlocfilehash: d4cd9497f9adcea03ece222f09124ce593ea73cf
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91685015"
---
# <a name="perception-simulation"></a>認識シミュレーション

アプリの自動テストをビルドしますか? テストをコンポーネントレベルの単体テストよりも先に実行し、アプリをエンドツーエンドで実際に練習しますか。 認識シミュレーションは、探しているものです。 認識シミュレーションライブラリは、アプリに人間と世界の入力データを送信して、テストを自動化できるようにします。 たとえば、特定の反復可能な位置に対する人間の入力をシミュレートし、ジェスチャを実行したり、モーションコントローラーを使用したりすることができます。

認識シミュレーションでは、このようなシミュレートされた入力を物理 HoloLens、HoloLens エミュレーター (第1世代)、HoloLens 2 エミュレーター、または Mixed Reality ポータルがインストールされている PC に送信できます。 認識シミュレーションは、混合の現実のデバイスでライブセンサーをバイパスし、デバイスで実行されているアプリケーションにシミュレートされた入力を送信します。 アプリケーションでは、これらの入力イベントを、常に使用するものと同じ Api を使用して受信します。また、実際のセンサーでの実行と知覚シミュレーションでの実行の違いを示すことはできません。 認識シミュレーションは、シミュレートされた入力を HoloLens 仮想マシンに送信するために HoloLens エミュレーターで使用されるものと同じテクノロジです。

コードでのシミュレーションの使用を開始するには、まず IPerceptionSimulationManager オブジェクトを作成します。 そのオブジェクトから、コマンドを発行して、"人間" のようなシミュレートされた "ユーザー" のプロパティを制御することができます。これには、head 位置、針、ジェスチャなどがあります。また、モーションコントローラーを有効にしたり操作したりすることができます。

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>認識シミュレーションのための Visual Studio プロジェクトの設定
1. 開発用 PC に[HoloLens エミュレーターをインストール](../install-the-tools.md)します。 エミュレーターには、認識シミュレーションに使用するライブラリが含まれています。
2. 新しい Visual Studio C# デスクトッププロジェクトを作成します (コンソールプロジェクトは、開始するのに適しています)。
3. 次のバイナリを参照としてプロジェクトに追加します (プロジェクト >追加 >参照...)。これらは、 \\ HoloLens 2 エミュレーターの% **ProgramFiles (x86)% \ MICROSOFT xde \\ 10.0.18362.0** など、% ProgramFiles (X86)% \ microsoft xde (バージョン) で見つけることができます。  (注: バイナリは HoloLens 2 エミュレーターに含まれていますが、デスクトップ上の Windows Mixed Reality でも機能します)。ある. 認識シミュレーション用の PerceptionSimulationManager.Interop.dll マネージ C# ラッパー。
    b. PerceptionSimulationRest.dll-HoloLens またはエミュレーターに対する web ソケット通信チャネルを設定するためのライブラリです。
    c. シミュレーション用の SimulationStream.Interop.dll 共有型。
4. 実装バイナリ PerceptionSimulationManager.dll をプロジェクト a に追加します。 まず、これをバイナリとしてプロジェクトに追加します (プロジェクト >追加 >既存の項目...)。プロジェクトソースフォルダーにコピーしないように、リンクとして保存します。 ![PerceptionSimulationManager.dll をリンク b としてプロジェクトに追加し ](images/saveaslink.png) ます。 次に、ビルド時に出力フォルダーにコピーされていることを確認します。 これは、バイナリのプロパティシートにあります。 ![出力ディレクトリにコピーする PerceptionSimulationManager.dll をマークします](images/copyalways.png)
5. アクティブソリューションプラットフォームを x64 に設定します。  (Configuration Manager を使用して、x64 用のプラットフォームエントリがまだ存在しない場合は作成します)。

## <a name="creating-an-iperceptionsimulation-manager-object"></a>IPerceptionSimulation Manager オブジェクトの作成

シミュレーションを制御するには、IPerceptionSimulationManager オブジェクトから取得したオブジェクトに更新を発行します。 最初の手順では、そのオブジェクトを取得し、ターゲットデバイスまたはエミュレーターに接続します。 エミュレーターの IP アドレスを取得するには、[ツールバー](using-the-hololens-emulator.md)の [デバイスポータル] ボタンをクリックします。

![デバイスポータルを開くアイコン開いている ](images/emulator-deviceportal.png) **デバイスポータル** : エミュレーターで HoloLens OS の Windows デバイスポータルを開きます。  Windows Mixed Reality の場合、この設定は、[デバイスポータルを有効にする] の下にある [Connect & Security] (セキュリティの更新) の下にある [設定] アプリで取得できます。  IP アドレスとポートの両方に注意してください。

まず、RestSimulationStreamSink を呼び出して、RestSimulationStreamSink オブジェクトを取得します。 これは、http 接続を介して制御するターゲットデバイスまたはエミュレーターです。 コマンドは、デバイスまたはエミュレーターで実行されている [Windows デバイスポータル](using-the-windows-device-portal.md) に渡され、処理されます。 オブジェクトを作成するには、次の4つのパラメーターが必要です。
* Uri uri-ターゲットデバイスの IP アドレス (例: " https://123.123.123.123 " または " https://123.123.123.123:50080 ")
* System .Net. NetworkCredential 資格情報-ターゲットデバイスまたはエミュレーターで [Windows デバイスポータル](using-the-windows-device-portal.md) に接続するためのユーザー名/パスワード。 ローカルアドレスを使用してエミュレーターに接続している場合 (例: 168 *...* *) 同じ PC で、すべての資格情報が受け入れられます。
* bool normal-通常の優先度の場合は True、低優先度の場合は false。 テストシナリオでは、通常、これを *true* に設定して、テストで制御を行うことができます。  エミュレーターと Windows Mixed Reality のシミュレーションでは、優先度の低い接続を使用します。  テストで優先度の低い接続も使用している場合は、最後に確立された接続が制御されます。
* CancellationToken は、非同期操作を取り消すためのトークンです。

次に、IPerceptionSimulationManager を作成します。 これは、シミュレーションの制御に使用するオブジェクトです。 これは、非同期メソッドでも実行する必要があることに注意してください。

## <a name="control-the-simulated-human"></a>シミュレートされた人間を制御する

IPerceptionSimulationManager には、ISimulatedHuman オブジェクトを返すヒューマンプロパティがあります。 シミュレートされた人間を制御するには、このオブジェクトに対して操作を実行します。 次に例を示します。

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a>C# コンソールアプリケーションの基本的なサンプル

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Task.Run(async () =>
            {
                RestSimulationStreamSink sink = null;
                CancellationToken token = new System.Threading.CancellationToken();

                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }

                // Always close the sink to return control to the previous application.
                if (sink != null)
                {
                    await sink.Close(token);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a>拡張サンプル C# コンソールアプリケーション

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            RestSimulationStreamSink sink = null;
            CancellationToken token = new System.Threading.CancellationToken();

            Task.Run(async () =>
            {
                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

                    // Activate the right hand
                    manager.Human.RightHand.Activated = true;

                    // Simulate Bloom gesture, which should cause Shell to disappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... this time, Shell should reappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate a Head rotation down around the X axis
                    // This should cause gaze to aim about the center of the screen
                    manager.Human.Head.Rotate(new Rotation3(0.04f, 0.0f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a finger press & release
                    // Should cause a tap on the center tile, thus launching it
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate a second finger press & release
                    // Should activate the app that was launched when the center tile was clicked
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(5000);

                    // Simulate a Head rotation towards the upper right corner
                    manager.Human.Head.Rotate(new Rotation3(-0.14f, 0.17f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a third finger press & release
                    // Should press the Remove button on the app
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... bringing the Shell back once more
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();

            // Always close the sink to return control to the previous application.
            if (sink != null)
            {
                sink.Close(token);
            }
        }
    }
}
```

## <a name="note-on-6-dof-controllers"></a>6つの自由度コントローラーに関する注意

シミュレートされた6つの自由コントローラーでメソッドのプロパティを呼び出す前に、コントローラーをアクティブにする必要があります。  そうしないと、例外が発生します。  Windows 10 2019 年5月の更新プログラムでは、ISimulatedSixDofController オブジェクトの Status プロパティを SimulatedSixDofControllerStatus に設定することにより、シミュレートされた6つの自由度コントローラーをインストールしてアクティブ化することができます。
Windows 10 10 月2018更新プログラムおよびそれ以前のバージョンでは、\Windows\System32 フォルダーにある PerceptionSimulationDevice ツールを呼び出して、シミュレートされた6自由コントローラーを最初に個別にインストールする必要があります。  このツールの使用方法は次のとおりです。


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

次に例を示します。

```
    PerceptionSimulationDevice.exe i 6dof 1
```

サポートされているアクションは次のとおりです。
* i = インストール
* q = クエリ
* r = 削除

サポートされているインスタンスは次のとおりです。
* 1 = 左6自由コントローラー
* 2 = 右6自由コントローラー

プロセスの終了コードは、成功 (ゼロの戻り値) または失敗 (0 以外の戻り値) を示します。  ' Q ' アクションを使用してコントローラーがインストールされているかどうかを照会する場合、コントローラーがまだインストールされていない場合は戻り値が0になり、コントローラーがインストールされている場合は1が返されます。

Windows 10 10 月2018更新プログラムまたはそれ以前のバージョンでコントローラーを削除する場合は、最初に API を使用して状態を Off に設定してから、PerceptionSimulationDevice ツールを呼び出します。

このツールは管理者として実行する必要があることに注意してください。




## <a name="api-reference"></a>API リファレンス

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a>PerceptionSimulation. SimulatedDeviceType

シミュレートされたデバイスの種類について説明します

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

**PerceptionSimulation. SimulatedDeviceType**

架空の参照デバイス (PerceptionSimulationManager の既定値)

### <a name="microsoftperceptionsimulationheadtrackermode"></a>PerceptionSimulation... Trackermode

ヘッドトラッカーモードについて説明します。

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

**PerceptionSimulation。既定値の場合**

既定のヘッド追跡。 これは、システムが実行時の状況に基づいて最適なヘッド追跡モードを選択することを意味します。

**PerceptionSimulation のようになります。**

方向のみのヘッド追跡。 これは、追跡される位置が信頼できない可能性があり、head 位置に依存する一部の機能が使用できない場合があることを意味します。

**PerceptionSimulation を移動します。**

位置指定のヘッド追跡。 これは、追跡されるヘッドの位置と向きは両方とも信頼できることを意味します。

### <a name="microsoftperceptionsimulationsimulatedgesture"></a>PerceptionSimulation. SimulatedGesture

シミュレートされたジェスチャについて説明します

```
public enum SimulatedGesture
{
    None = 0,
    FingerPressed = 1,
    FingerReleased = 2,
    Home = 4,
    Max = Home
}
```

**PerceptionSimulation. SimulatedGesture**

ジェスチャがないことを示すために使用される sentinel 値。

**PerceptionSimulation. SimulatedGesture. FingerPressed**

指押下ジェスチャ。

**PerceptionSimulation. SimulatedGesture. FingerReleased**

指で離されたジェスチャ。

**PerceptionSimulation. SimulatedGesture**

ホーム/システムジェスチャ。

**PerceptionSimulation. SimulatedGesture**

有効なジェスチャの最大数。

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a>PerceptionSimulation. SimulatedSixDofControllerStatus

シミュレートされた6自由コントローラーの可能性のある状態。

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

**PerceptionSimulation. SimulatedSixDofControllerStatus**

6自由コントローラーがオフになっています。

**PerceptionSimulation. SimulatedSixDofControllerStatus**

6自由コントローラーが有効になり、追跡されます。

**PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**

6自由度コントローラーはオンになっていますが、追跡することはできません。

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a>PerceptionSimulation. SimulatedSixDofControllerButton

シミュレートされた6自由コントローラーでサポートされるボタン。

```
public enum SimulatedSixDofControllerButton
{
    None = 0,
    Home = 1,
    Menu = 2,
    Grip = 4,
    TouchpadPress = 8,
    Select = 16,
    TouchpadTouch = 32,
    Thumbstick = 64,
    Max = Thumbstick
}
```

**PerceptionSimulation. SimulatedSixDofControllerButton**

ボタンを指定するために使用される sentinel 値。

**PerceptionSimulation. SimulatedSixDofControllerButton**

[ホーム] ボタンが押された状態になります。

**PerceptionSimulation. SimulatedSixDofControllerButton. メニュー**

メニューボタンが押された状態になります。

**PerceptionSimulation. SimulatedSixDofControllerButton**

グリップボタンが押された状態になります。

**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**

タッチパッドが押された状態になります。

**PerceptionSimulation. SimulatedSixDofControllerButton**

[選択] ボタンが押された状態になります。

**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**

タッチパッドがタッチされます。

**PerceptionSimulation. SimulatedSixDofControllerButton**

サムスティックが押されています。

**PerceptionSimulation. SimulatedSixDofControllerButton**

最大有効なボタン。


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a>PerceptionSimulation. SimulatedEyesCalibrationState

シミュレートされた目の調整状態

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

**PerceptionSimulation. SimulatedEyesCalibrationState.**

目の調整は使用できません。

**PerceptionSimulation. SimulatedEyesCalibrationState**

目が調整されました。  これが既定値です。

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configpostman**

目が調整されています。

**PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**

目を調整する必要があります。

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a>PerceptionSimulation. SimulatedHandJointTrackingAccuracy

手の継手の追跡精度。

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

**PerceptionSimulation. SimulatedHandJointTrackingAccuracy.**

ジョイントは追跡されません。

**PerceptionSimulation. SimulatedHandJointTrackingAccuracy**

ジョイント位置が推論されます。

**PerceptionSimulation. SimulatedHandJointTrackingAccuracy**

ジョイントは完全に追跡されます。

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a>PerceptionSimulation. SimulatedHandPose

手の継手の追跡精度。

```
public enum SimulatedHandPose
{
    Closed = 0,
    Open = 1,
    Point = 2,
    Pinch = 3,
    Max = Pinch
}
```

**PerceptionSimulation. SimulatedHandPose**

ハンドの指継手は、終了したポーズを反映するように構成されています。

**PerceptionSimulation. SimulatedHandPose**

手の指継手は、オープンなポーズを反映するように構成されています。

**PerceptionSimulation. SimulatedHandPose**

ハンドの指継手は、ポイントのポーズを反映するように構成されています。

**PerceptionSimulation. SimulatedHandPose**

手の指継手は、ピンチのポーズを反映するように構成されています。

**PerceptionSimulation. SimulatedHandPose**

SimulatedHandPose の最大有効値。


### <a name="microsoftperceptionsimulationplaybackstate"></a>PerceptionSimulation の状態

再生の状態を記述します。

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

**PerceptionSimulation が停止しました。**

記録は現在停止しており、再生の準備ができています。

**PerceptionSimulation を再生します。**

記録は現在再生中です。

**PerceptionSimulation が一時停止しました。**

記録は現在一時停止されています。

**PerceptionSimulation を終了します。**

記録が最後に達しました。

### <a name="microsoftperceptionsimulationvector3"></a>PerceptionSimulation. Vector3

3D 空間の点またはベクターを表す3つのコンポーネントベクターについて説明します。

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

**PerceptionSimulation. Vector3**

ベクトルの X 成分。

**PerceptionSimulation. Vector3**

ベクトルの Y 成分。

**PerceptionSimulation. Vector3**

ベクトルの Z 成分。

**#Ctor PerceptionSimulation (system.string、system.string、system.string) を (system.string) します。**

新しい Vector3 を構築します。

パラメーター
* x-ベクトルの x 成分。
* y-ベクトルの y 成分。
* z-ベクトルの z 成分。

### <a name="microsoftperceptionsimulationrotation3"></a>PerceptionSimulation. Rotation3

3つのコンポーネントのローテーションについて説明します。

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

**PerceptionSimulation. Rotation3**

X 軸を中心とする回転のピッチ成分。

**PerceptionSimulation. Rotation3**

Y 軸を中心とする回転のヨー要素。

**PerceptionSimulation. Rotation3**

Z 軸を中心とする回転のロールコンポーネント。

**#Ctor PerceptionSimulation (system.string、system.string、system.string) を (system.string) します。**

新しい Rotation3 を構築します。

パラメーター
* ピッチ-回転のピッチ成分。
* ヨー-回転のヨーコンポーネント。
* roll-回転のロールコンポーネント。

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a>PerceptionSimulation. SimulatedHandJointConfiguration

シミュレートされたハンドでのジョイントの構成について説明します。

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

**PerceptionSimulation. SimulatedHandJointConfiguration**

ジョイントの位置。

**PerceptionSimulation. SimulatedHandJointConfiguration**

ジョイントの回転。

**PerceptionSimulation. SimulatedHandJointConfiguration の精度**

ジョイントの追跡精度。


### <a name="microsoftperceptionsimulationfrustum"></a>PerceptionSimulation

カメラで一般的に使用される、視錐のビューについて説明します。

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

**PerceptionSimulation。 Near**

視錐に含まれる最小距離。

**PerceptionSimulation です。**

視錐に含まれる最大距離。

**PerceptionSimulation. FieldOfView**

視錐のビューの水平方向のフィールド (π未満のラジアン)。

**PerceptionSimulation. AspectRatio**

ビューの垂直方向のフィールドから、ビューの垂直方向のフィールドまでの比率。

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a>PerceptionSimulation. SimulatedDisplayConfiguration

シミュレートされたヘッドセットの表示の構成について説明します。

```
public struct SimulatedDisplayConfiguration
{
    public Vector3 LeftEyePosition;
    public Rotation3 LeftEyeRotation;
    public Vector3 RightEyePosition;
    public Rotation3 RightEyeRotation;
    public float Ipd;
    public bool ApplyEyeTransforms;
    public bool ApplyIpd;
}
```

**PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyePosition**

ステレオレンダリングの目的で、ヘッドの中心から左目への変換。

**PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyeRotation**

ステレオレンダリングの目的での左目の回転。

**PerceptionSimulation. SimulatedDisplayConfiguration. RightEyePosition**

ステレオレンダリングの目的で、ヘッドの中心から右目への変換。

**PerceptionSimulation. SimulatedDisplayConfiguration. RightEyeRotation**

ステレオレンダリングの目的での右目の回転。

**PerceptionSimulation. SimulatedDisplayConfiguration. Ipd**

ステレオレンダリングのためにシステムによって報告された Ipd 値。

**PerceptionSimulation. SimulatedDisplayConfiguration (変換)**

左辺と右辺の変換に指定された値が有効であると見なされ、実行中のシステムに適用されるかどうか。

**PerceptionSimulation. SimulatedDisplayConfiguration. ApplyIpd**

Ipd に指定された値が有効であると見なされ、実行中のシステムに適用されるかどうか。


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>PerceptionSimulation. IPerceptionSimulationManager

デバイスの制御に使用されるパケットを生成するためのルート。

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

**PerceptionSimulation. IPerceptionSimulationManager**

シミュレートされた人間とシミュレートされた世界を解釈する、シミュレートされたデバイスオブジェクトを取得します。

**PerceptionSimulation. IPerceptionSimulationManager**

シミュレートされた人間を制御するオブジェクトを取得します。

**PerceptionSimulation. IPerceptionSimulationManager**

シミュレーションを既定の状態にリセットします。

### <a name="microsoftperceptionsimulationisimulateddevice"></a>PerceptionSimulation. ISimulatedDevice

シミュレートされた世界とシミュレートされた人間を解釈するデバイスを記述するインターフェイス

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

**PerceptionSimulation. ISimulatedDevice Tracker**

シミュレートされたデバイスからヘッドトラッカーを取得します。

**PerceptionSimulation. ISimulatedDevice Tracker**

シミュレートされたデバイスからハンドトラッカーを取得します。

**PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType (PerceptionSimulation. SimulatedDeviceType)**

シミュレートされたデバイスのプロパティを、指定したデバイスの種類に合わせて設定します。

パラメーター
* type-シミュレートされたデバイスの新しい種類

### <a name="microsoftperceptionsimulationisimulateddevice2"></a>PerceptionSimulation. ISimulatedDevice2

ISimulatedDevice を ISimulatedDevice2 にキャストすると、追加のプロパティを使用できます。

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

**PerceptionSimulation. ISimulatedDevice2. IsUserPresent**

シミュレートされた人間がヘッドセットをアクティブに装着しているかどうかを取得または設定します。

**PerceptionSimulation. ISimulatedDevice2. DisplayConfiguration**

シミュレートされた表示のプロパティを取得または設定します。

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a>PerceptionSimulation. ISimulatedHeadTracker

シミュレートされた人間の頭を追跡する、シミュレートされたデバイスの部分を説明するインターフェイスです。

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

**PerceptionSimulation. ISimulatedHeadTracker.-Trackermode**

現在のヘッドトラッカーモードを取得して設定します。

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a>PerceptionSimulation. ISimulatedHandTracker

シミュレートされた人間の手を追跡するシミュレートされたデバイスの部分を説明するインターフェイス

```
public interface ISimulatedHandTracker
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    float Pitch { get; set; }
    bool FrustumIgnored { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    Frustum Frustum { get; set; }
}
```

**PerceptionSimulation. ISimulatedHandTracker. WorldPosition**

世界のリレーションを使用してノードの位置をメートル単位で取得します。

**PerceptionSimulation. ISimulatedHandTracker**

頭の中心を基準とした、シミュレートされたハンドトラッカーの位置を取得して設定します。

**PerceptionSimulation. ISimulatedHandTracker**

シミュレートされたハンドトラッカーの下向きのピッチを取得して設定します。

**PerceptionSimulation は無視されました。**

シミュレートされたハンドトラッカーを無視するかどうかを取得して設定します。 無視すると、両方のハンドが常に表示されます。 無視しない場合 (既定)、ハンドトラッカーの視錐の内側にいる場合にのみ表示されます。

**PerceptionSimulation. ISimulatedHandTracker**

ハンドがシミュレートされたハンドトラッカーに表示されるかどうかを判断するために使用する、視錐のプロパティを取得および設定します。

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>PerceptionSimulation. ISimulatedHuman

シミュレートされた人間を制御する最上位のインターフェイス。

```
public interface ISimulatedHuman 
{
    Vector3 WorldPosition { get; set; }
    float Direction { get; set; }
    float Height { get; set; }
    ISimulatedHand LeftHand { get; }
    ISimulatedHand RightHand { get; }
    ISimulatedHead Head { get; }
    void Move(Vector3 translation);
    void Rotate(float radians);
}
```

**PerceptionSimulation. ISimulatedHuman. WorldPosition**

世界中のノードの位置をメートル単位で取得して設定します。 この位置は、人間のフィートの中央の点に対応しています。

**PerceptionSimulation. ISimulatedHuman**

世界中のシミュレートされた人間の顔の方向を取得して設定します。 0ラジアンは負の Z 軸を中心にします。 正のラジアンは、Y 軸について時計回りに回転します。

**PerceptionSimulation. ISimulatedHuman**

シミュレートされた人間の高さをメートル単位で取得して設定します。

**PerceptionSimulation. ISimulatedHuman. LeftHand**

シミュレートされた人間の左側を取得します。

**PerceptionSimulation. ISimulatedHuman. 右**

シミュレートされた人間の右側を取得します。

**PerceptionSimulation. ISimulatedHuman**

シミュレートされた人間の先頭を取得します。

**PerceptionSimulation (ISimulatedHuman) (PerceptionSimulation. Vector3)**

シミュレートされた人間を、現在の位置を基準としてメートル単位で移動します。

パラメーター
* translation-現在の位置を基準とした、移動する平行移動。

**PerceptionSimulation. ISimulatedHuman (System. Single)**

現在の方向を基準にして、シミュレートされた人間を Y 軸に対して時計回りに回転させます

パラメーター
* ラジアン-Y 軸を中心に回転する量。

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a>PerceptionSimulation. ISimulatedHuman2

ISimulatedHuman を ISimulatedHuman2 にキャストすると、追加のプロパティを使用できます。

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

**PerceptionSimulation. ISimulatedHuman2 Controller**

左6自由コントローラーを取得します。

**PerceptionSimulation. ISimulatedHuman2 コントローラー**

右6自由コントローラーを取得します。


### <a name="microsoftperceptionsimulationisimulatedhand"></a>PerceptionSimulation. ISimulatedHand

シミュレートされた人間の手を記述するインターフェイス

```
public interface ISimulatedHand
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    bool Activated { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    bool Visible { [return: MarshalAs(UnmanagedType.Bool)] get; }
    void EnsureVisible();
    void Move(Vector3 translation);
    void PerformGesture(SimulatedGesture gesture);
}
```

**PerceptionSimulation. ISimulatedHand. WorldPosition**

世界のリレーションを使用してノードの位置をメートル単位で取得します。

**PerceptionSimulation. ISimulatedHand**

人間に対するシミュレートされたハンドの位置をメートル単位で取得して設定します。

**PerceptionSimulation. ISimulatedHand**

ハンドが現在アクティブになっているかどうかを取得して設定します。

**PerceptionSimulation. ISimulatedHand**

SimulatedDevice に手が現在表示されているかどうかを取得します (この位置が、[ツール] で検出される位置にあるかどうか)。

**PerceptionSimulation. ISimulatedHand. Ensurevisible\**

SimulatedDevice に見えるようにハンドを移動します。

**PerceptionSimulation (ISimulatedHand) (PerceptionSimulation. Vector3)**

シミュレートされたハンドの位置を、現在の位置を基準としてメートル単位で移動します。

パラメーター
* translation-シミュレートされたハンドを変換する量。

**ISimulatedHand (PerceptionSimulation) () (PerceptionSimulation)**

シミュレートされたハンドを使用してジェスチャを実行します。  ハンドが有効になっている場合にのみ、システムによって検出されます。

パラメーター
* ジェスチャ-実行するジェスチャ。

### <a name="microsoftperceptionsimulationisimulatedhand2"></a>PerceptionSimulation. ISimulatedHand2

ISimulatedHand を ISimulatedHand2 にキャストすると、追加のプロパティを使用できます。
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

**PerceptionSimulation. ISimulatedHand2**

シミュレートされたハンドの回転を取得または設定します。  正のラジアンは、軸に沿って表示すると時計回りに回転します。

### <a name="microsoftperceptionsimulationisimulatedhand3"></a>PerceptionSimulation. ISimulatedHand3

ISimulatedHand を ISimulatedHand3 にキャストすると、追加のプロパティを使用できます。
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

**PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**

指定されたジョイントの共同構成を取得します。

**PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**

指定されたジョイントの結合構成を設定します。

**PerceptionSimulation. ISimulatedHand3. SetHandPose**

アニメーション化するオプションのフラグを持つ既知のポーズにハンドを設定します。  注: アニメーション化によって、最終的な結合構成がすぐに反映されることはありません。


### <a name="microsoftperceptionsimulationisimulatedhead"></a>PerceptionSimulation. ISimulatedHead

シミュレートされた人間の先頭を記述するインターフェイス。

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

**PerceptionSimulation. ISimulatedHead. WorldPosition**

世界のリレーションを使用してノードの位置をメートル単位で取得します。

**PerceptionSimulation. ISimulatedHead**

シミュレートされたヘッドの回転を取得します。 正のラジアンは、軸に沿って表示すると時計回りに回転します。

**PerceptionSimulation. ISimulatedHead**

シミュレートされたヘッドの直径を取得します。 この値は、ヘッドの中心 (回転点) を決定するために使用されます。

**PerceptionSimulation (ISimulatedHead) (PerceptionSimulation. Rotation3)**

シミュレートされた頭を現在の回転に対して回転します。 正のラジアンは、軸に沿って表示すると時計回りに回転します。

パラメーター
* rotation-回転する量。

### <a name="microsoftperceptionsimulationisimulatedhead2"></a>PerceptionSimulation. ISimulatedHead2

ISimulatedHead を ISimulatedHead2 にキャストすると、追加のプロパティを使用できます。

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

**PerceptionSimulation. ISimulatedHead2**

シミュレートされた人間の目を取得します。

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a>PerceptionSimulation. ISimulatedSixDofController

シミュレートされた人間に関連付けられた6自由コントローラーを記述するインターフェイス。

```
public interface ISimulatedSixDofController
{
    Vector3 WorldPosition { get; }
    SimulatedSixDofControllerStatus Status { get; set; }
    Vector3 Position { get; }
    Rotation3 Orientation { get; set; }
    void Move(Vector3 translation);
    void PressButton(SimulatedSixDofControllerButton button);
    void ReleaseButton(SimulatedSixDofControllerButton button);
    void GetTouchpadPosition(out float x, out float y);
    void SetTouchpadPosition(float x, float y);
}
```

**PerceptionSimulation. ISimulatedSixDofController. WorldPosition**

世界のリレーションを使用してノードの位置をメートル単位で取得します。

**PerceptionSimulation. ISimulatedSixDofController**

コントローラーの現在の状態を取得または設定します。  移動、回転、または押すボタンの呼び出しが成功する前に、コントローラーの状態が Off 以外の値に設定されている必要があります。

**PerceptionSimulation. ISimulatedSixDofController**

ユーザーに対してシミュレートされたコントローラーの位置をメートル単位で取得または設定します。

**PerceptionSimulation. ISimulatedSixDofController**

シミュレートされたコントローラーの向きを取得または設定します。

**PerceptionSimulation (ISimulatedSixDofController) (PerceptionSimulation. Vector3)**

シミュレートされたコントローラーの位置を、現在の位置 (メートル単位) に相対的に移動します。

パラメーター
* translation-シミュレートされたコントローラーを変換する量。

**ISimulatedSixDofController (SimulatedSixDofControllerButton) () PerceptionSimulation**

シミュレートされたコントローラーでボタンを押します。  コントローラーが有効になっている場合にのみ、システムによって検出されます。

パラメーター
* button-押すボタン。

**PerceptionSimulation (ISimulatedSixDofController) (SimulatedSixDofControllerButton)**

シミュレートされたコントローラーでボタンを離します。  コントローラーが有効になっている場合にのみ、システムによって検出されます。

パラメーター
* ボタン-リリースするボタン。

**PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition (out float, out float)**

シミュレートされたコントローラーのタッチパッド上でシミュレートされた指の位置を取得します。

パラメーター
* x-指の水平方向の位置。
* y-指の垂直方向の位置。

**PerceptionSimulation (float, float) の位置を ISimulatedSixDofController します。**

シミュレートされたコントローラーのタッチパッドでシミュレートされた指の位置を設定します。

パラメーター
* x-指の水平方向の位置。
* y-指の垂直方向の位置。

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a>PerceptionSimulation. ISimulatedSixDofController2

ISimulatedSixDofController を ISimulatedSixDofController2 にキャストすると、追加のプロパティとメソッドを使用できます。

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

**PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition (out float, out float)**

シミュレートされたコントローラー上のシミュレートされたサムスティックの位置を取得します。

パラメーター
* x-サムスティックの水平方向の位置。
* y-サムスティックの垂直方向の位置。

**PerceptionSimulation. ISimulatedSixDofController2. SetThumbstickPosition (float, float)**

シミュレートされたコントローラーのシミュレートされたサムスティックの位置を設定します。

パラメーター
* x-サムスティックの水平方向の位置。
* y-サムスティックの垂直方向の位置。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**

シミュレートされたコントローラーのバッテリレベルを取得または設定します。  値は0.0 より大きく、100.0 以下でなければなりません。


### <a name="microsoftperceptionsimulationisimulatedeyes"></a>PerceptionSimulation. ISimulatedEyes

シミュレートされた人間の目を表すインターフェイス。

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

**PerceptionSimulation. ISimulatedEyes**

シミュレートされた目の回転を取得します。 正のラジアンは、軸に沿って表示すると時計回りに回転します。

**PerceptionSimulation (ISimulatedEyes) (PerceptionSimulation. Rotation3)**

現在の回転と比較して、シミュレートされた目を回転します。 正のラジアンは、軸に沿って表示すると時計回りに回転します。

パラメーター
* rotation-回転する量。

**PerceptionSimulation. ISimulatedEyes. CalibrationState**

シミュレートされた目の調整状態を取得または設定します。

**PerceptionSimulation. ISimulatedEyes. WorldPosition**

世界のリレーションを使用してノードの位置をメートル単位で取得します。


### <a name="microsoftperceptionsimulationisimulationrecording"></a>PerceptionSimulation. ISimulationRecording

再生用に読み込まれた単一の記録と対話するためのインターフェイス。

```
public interface ISimulationRecording
{
    StreamDataTypes DataTypes { get; }
    PlaybackState State { get; }
    void Play();
    void Pause();
    void Seek(UInt64 ticks);
    void Stop();
};
```

**PerceptionSimulation. ISimulationRecording**

記録内のデータ型の一覧を取得します。

**PerceptionSimulation. ISimulationRecording**

記録の現在の状態を取得します。

**PerceptionSimulation. ISimulationRecording**

再生を開始します。 記録が一時停止されている場合は、一時停止した場所から再生が再開されます。停止した場合は、最初から再生が開始されます。 既に再生中の場合、この呼び出しは無視されます。

**PerceptionSimulation. ISimulationRecording**

現在の場所で再生を一時停止します。 記録が停止している場合、呼び出しは無視されます。

**PerceptionSimulation. ISimulationRecording (System. UInt64)**

指定した時間 (先頭から100ナノ秒単位) に記録をシークし、その位置で一時停止します。 時刻が記録の末尾を越えている場合は、最後のフレームで一時停止します。

パラメーター
* ティック-シークする時刻。

**PerceptionSimulation. ISimulationRecording**

再生を停止し、位置を先頭にリセットします。

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>PerceptionSimulation. ISimulationRecordingCallback

再生中に状態の変更を受信するためのインターフェイス。

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged (PerceptionSimulation. PlaybackState)**

ISimulationRecording の再生状態が変更されたときに呼び出されます。

パラメーター
* newState-記録の新しい状態。

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>PerceptionSimulation. PerceptionSimulationManager

認識シミュレーションオブジェクトを作成するためのルートオブジェクト。

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager (PerceptionSimulation. ISimulationStreamSink)**

シミュレートされたパケットを生成し、指定したシンクに配信するために、オブジェクトでを作成します。

パラメーター
* sink-生成されたすべてのパケットを受信するシンク。

戻り値

作成されたマネージャー。

**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording (System.string)**

指定されたパスのファイルに受信したすべてのパケットを格納するシンクを作成します。

パラメーター
* path-作成するファイルのパス。

戻り値

作成されたシンク。

**PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System.string, PerceptionSimulation.. ISimulationStreamSinkFactory)**

指定されたファイルから記録を読み込みます。

パラメーター
* path-読み込むファイルのパス。
* factory-必要なときに ISimulationStreamSink を作成するために記録によって使用されるファクトリ。

戻り値

読み込まれた記録。

**PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System.string, PerceptionSimulation ISimulationStreamSinkFactory, PerceptionSimulation. ISimulationRecordingCallback..)**

指定されたファイルから記録を読み込みます。

パラメーター
* path-読み込むファイルのパス。
* factory-必要なときに ISimulationStreamSink を作成するために記録によって使用されるファクトリ。
* callback-更新を受け取るコールバックで、記録の状態を再適用します。

戻り値

読み込まれた記録。

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>PerceptionSimulation データ型

さまざまな種類のストリームデータについて説明します。

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    SixDofControllers = 0x40,
    Eyes = 0x80,
    DisplayConfiguration = 0x100
    All = None | Head | Hands | SpatialMapping | Calibration | Environment | SixDofControllers | Eyes | DisplayConfiguration
}
```

**PerceptionSimulation のデータ型はありません。**

ストリームデータ型がないことを示すために使用される sentinel 値。

**PerceptionSimulation のデータ型**

ヘッドの位置と向きに関するデータのストリーム。

**PerceptionSimulation のデータ型**

ハンドの位置とジェスチャに関するデータのストリーム。

**PerceptionSimulation. SpatialMapping.**

環境の空間マッピングに関するデータのストリーム。

**PerceptionSimulation のデータ型**

デバイスの調整に関するデータのストリーム。 調整パケットは、リモートモードのシステムでのみ受け入れられます。

**PerceptionSimulation のデータ型**

デバイスの環境に関するデータのストリーム。

**PerceptionSimulation. SixDofControllers.**

モーションコントローラーに関するデータのストリーム。

**PerceptionSimulation のデータ型**

シミュレートされた人間の目に関するデータのストリーム。

**PerceptionSimulation を構成します。**

デバイスのディスプレイ構成に関するデータのストリーム。

**PerceptionSimulation のデータ型**

すべての記録されたデータ型を示すために使用される sentinel 値。

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>PerceptionSimulation. ISimulationStreamSink

シミュレーションストリームからデータパケットを受信するオブジェクト。

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**PerceptionSimulation. ISimulationStreamSink (uint length, byte [] パケット数)**

内部的に型指定され、バージョン管理される1つのパケットを受信します。

パラメーター
* length-パケットの長さ。
* パケット-パケットのデータ。

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>PerceptionSimulation. ISimulationStreamSinkFactory

ISimulationStreamSink を作成するオブジェクト。

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**PerceptionSimulation. ISimulationStreamSinkFactory-Ationstreamsink ()**

ISimulationStreamSink の1つのインスタンスを作成します。

戻り値

作成されたシンク。
