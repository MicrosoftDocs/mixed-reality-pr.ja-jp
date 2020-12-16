---
title: 認識シミュレーション
description: 知覚シミュレーションライブラリを使用して、イマーシブアプリケーションのシミュレートされた入力を自動化するためのガイド
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: HoloLens、シミュレーション、テスト
ms.openlocfilehash: 64028c3a1ad58cecfebc93aee325b73c3a6a649a
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530402"
---
# <a name="perception-simulation"></a><span data-ttu-id="a0823-104">認識シミュレーション</span><span class="sxs-lookup"><span data-stu-id="a0823-104">Perception simulation</span></span>

<span data-ttu-id="a0823-105">アプリの自動テストをビルドしますか?</span><span class="sxs-lookup"><span data-stu-id="a0823-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="a0823-106">テストをコンポーネントレベルの単体テストよりも先に実行し、アプリをエンドツーエンドで実際に練習しますか。</span><span class="sxs-lookup"><span data-stu-id="a0823-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="a0823-107">認識シミュレーションは、探しているものです。</span><span class="sxs-lookup"><span data-stu-id="a0823-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="a0823-108">認識シミュレーションライブラリは、アプリに人間と世界の入力データを送信して、テストを自動化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a0823-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="a0823-109">たとえば、特定の反復可能な位置を調べる人間の入力をシミュレートし、ジェスチャやモーションコントローラーを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="a0823-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then use a gesture or motion controller.</span></span>

<span data-ttu-id="a0823-110">認識シミュレーションでは、このようなシミュレートされた入力を物理 HoloLens、HoloLens エミュレーター (最初の gen)、HoloLens 2 エミュレーター、または Mixed Reality ポータルがインストールされている PC に送信できます。</span><span class="sxs-lookup"><span data-stu-id="a0823-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (first gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="a0823-111">認識シミュレーションは、混合の現実のデバイスでライブセンサーをバイパスし、デバイスで実行されているアプリケーションにシミュレートされた入力を送信します。</span><span class="sxs-lookup"><span data-stu-id="a0823-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="a0823-112">アプリケーションでは、これらの入力イベントを、常に使用するものと同じ Api を使用して受信します。実際のセンサーと認識シミュレーションのどちらで実行しても、違いを示すことはできません。</span><span class="sxs-lookup"><span data-stu-id="a0823-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus Perception Simulation.</span></span> <span data-ttu-id="a0823-113">認識シミュレーションは、シミュレートされた入力を HoloLens 仮想マシンに送信するために HoloLens エミュレーターで使用されるものと同じテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="a0823-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="a0823-114">コードでのシミュレーションの使用を開始するには、まず IPerceptionSimulationManager オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="a0823-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="a0823-115">そのオブジェクトから、コマンドを発行して、"人間" のようなシミュレートされた "ユーザー" のプロパティを制御できます。これには、head 位置、針、ジェスチャなどがあります。</span><span class="sxs-lookup"><span data-stu-id="a0823-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures.</span></span> <span data-ttu-id="a0823-116">また、モーションコントローラーを有効にしたり操作したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a0823-116">You can also enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="a0823-117">認識シミュレーションのための Visual Studio プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="a0823-117">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="a0823-118">開発用 PC に[HoloLens エミュレーターをインストール](../install-the-tools.md)します。</span><span class="sxs-lookup"><span data-stu-id="a0823-118">[Install the HoloLens emulator](../install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="a0823-119">エミュレーターには、認識シミュレーションに使用するライブラリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a0823-119">The emulator includes the libraries you' use for Perception Simulation.</span></span>
2. <span data-ttu-id="a0823-120">新しい Visual Studio C# デスクトッププロジェクトを作成します (コンソールプロジェクトは、開始するのに適しています)。</span><span class="sxs-lookup"><span data-stu-id="a0823-120">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="a0823-121">次のバイナリを参照としてプロジェクトに追加します (プロジェクト >追加 >参照...)。これらは、 \\ HoloLens 2 エミュレーターの% **ProgramFiles (x86)% \ MICROSOFT xde \\ 10.0.18362.0** など、% ProgramFiles (X86)% \ microsoft xde (バージョン) で見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="a0823-121">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="a0823-122">(注: バイナリは HoloLens 2 エミュレーターに含まれていますが、デスクトップ上の Windows Mixed Reality でも機能します)。ある.</span><span class="sxs-lookup"><span data-stu-id="a0823-122">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="a0823-123">認識シミュレーション用の PerceptionSimulationManager.Interop.dll マネージ C# ラッパー。</span><span class="sxs-lookup"><span data-stu-id="a0823-123">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="a0823-124">b.</span><span class="sxs-lookup"><span data-stu-id="a0823-124">b.</span></span> <span data-ttu-id="a0823-125">PerceptionSimulationRest.dll-HoloLens またはエミュレーターに対する web ソケット通信チャネルを設定するためのライブラリです。</span><span class="sxs-lookup"><span data-stu-id="a0823-125">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="a0823-126">c.</span><span class="sxs-lookup"><span data-stu-id="a0823-126">c.</span></span> <span data-ttu-id="a0823-127">シミュレーション用の SimulationStream.Interop.dll 共有型。</span><span class="sxs-lookup"><span data-stu-id="a0823-127">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="a0823-128">実装バイナリ PerceptionSimulationManager.dll をプロジェクト a に追加します。</span><span class="sxs-lookup"><span data-stu-id="a0823-128">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="a0823-129">まず、これをバイナリとしてプロジェクトに追加します (プロジェクト >追加 >既存の項目...)。プロジェクトソースフォルダーにコピーしないように、リンクとして保存します。</span><span class="sxs-lookup"><span data-stu-id="a0823-129">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="a0823-130">![PerceptionSimulationManager.dll をリンク b としてプロジェクトに追加し ](images/saveaslink.png) ます。</span><span class="sxs-lookup"><span data-stu-id="a0823-130">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="a0823-131">次に、ビルド時に出力フォルダーにコピーされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a0823-131">Then make sure that it gets copied to your output folder on build.</span></span> <span data-ttu-id="a0823-132">これは、バイナリのプロパティシートにあります。</span><span class="sxs-lookup"><span data-stu-id="a0823-132">This is in the property sheet for the binary.</span></span> <span data-ttu-id="a0823-133">![出力ディレクトリにコピーする PerceptionSimulationManager.dll をマークします](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="a0823-133">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="a0823-134">アクティブソリューションプラットフォームを x64 に設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-134">Set your active solution platform to x64.</span></span>  <span data-ttu-id="a0823-135">(まだ存在していない場合は、Configuration Manager を使用して、x64 用のプラットフォームエントリを作成します)。</span><span class="sxs-lookup"><span data-stu-id="a0823-135">(Use the Configuration Manager to create a Platform entry for x64 if one doesn't already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="a0823-136">IPerceptionSimulation Manager オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="a0823-136">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="a0823-137">シミュレーションを制御するには、IPerceptionSimulationManager オブジェクトから取得したオブジェクトに更新を発行します。</span><span class="sxs-lookup"><span data-stu-id="a0823-137">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="a0823-138">最初の手順では、そのオブジェクトを取得し、ターゲットデバイスまたはエミュレーターに接続します。</span><span class="sxs-lookup"><span data-stu-id="a0823-138">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="a0823-139">エミュレーターの IP アドレスを取得するには、[ツールバー](using-the-hololens-emulator.md)の [デバイスポータル] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0823-139">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="a0823-140">![デバイスポータルを開くアイコン開いている ](images/emulator-deviceportal.png) **デバイスポータル**: エミュレーターで HoloLens OS の Windows デバイスポータルを開きます。</span><span class="sxs-lookup"><span data-stu-id="a0823-140">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="a0823-141">Windows Mixed Reality の場合、この設定は、[デバイスポータルを有効にする] の下にある [Connect & Security] (セキュリティの更新) の下にある [設定] アプリで取得できます。</span><span class="sxs-lookup"><span data-stu-id="a0823-141">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="a0823-142">IP アドレスとポートの両方に注意してください。</span><span class="sxs-lookup"><span data-stu-id="a0823-142">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="a0823-143">まず、RestSimulationStreamSink を呼び出して、RestSimulationStreamSink オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-143">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="a0823-144">これは、http 接続を介して制御するターゲットデバイスまたはエミュレーターです。</span><span class="sxs-lookup"><span data-stu-id="a0823-144">This is the target device or emulator that you'll control over an http connection.</span></span> <span data-ttu-id="a0823-145">コマンドは、デバイスまたはエミュレーターで実行されている [Windows デバイスポータル](using-the-windows-device-portal.md) に渡され、処理されます。</span><span class="sxs-lookup"><span data-stu-id="a0823-145">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="a0823-146">オブジェクトを作成するには、次の4つのパラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="a0823-146">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="a0823-147">Uri uri-ターゲットデバイスの IP アドレス (例: " https://123.123.123.123 " または " https://123.123.123.123:50080 ")</span><span class="sxs-lookup"><span data-stu-id="a0823-147">Uri uri - IP address of the target device (e.g., "https://123.123.123.123" or "https://123.123.123.123:50080")</span></span>
* <span data-ttu-id="a0823-148">System .Net. NetworkCredential 資格情報-ターゲットデバイスまたはエミュレーターで [Windows デバイスポータル](using-the-windows-device-portal.md) に接続するためのユーザー名/パスワード。</span><span class="sxs-lookup"><span data-stu-id="a0823-148">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="a0823-149">ローカルアドレスを使用してエミュレーターに接続している場合 (例: 168 \*...\*\*) 同じ PC で、すべての資格情報が受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="a0823-149">If you're connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="a0823-150">bool normal-通常の優先度の場合は True、低優先度の場合は false。</span><span class="sxs-lookup"><span data-stu-id="a0823-150">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="a0823-151">テストシナリオでは、通常、これを *true* に設定して、テストで制御を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a0823-151">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="a0823-152">エミュレーターと Windows Mixed Reality のシミュレーションでは、優先順位の低い接続を使用します。</span><span class="sxs-lookup"><span data-stu-id="a0823-152">The emulator and Windows Mixed Reality simulation use low-priority connections.</span></span>  <span data-ttu-id="a0823-153">テストで優先度の低い接続も使用している場合は、最後に確立された接続が制御されます。</span><span class="sxs-lookup"><span data-stu-id="a0823-153">If your test also uses a low-priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="a0823-154">CancellationToken は、非同期操作を取り消すためのトークンです。</span><span class="sxs-lookup"><span data-stu-id="a0823-154">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="a0823-155">次に、IPerceptionSimulationManager を作成します。</span><span class="sxs-lookup"><span data-stu-id="a0823-155">Second, you'll create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="a0823-156">これは、シミュレーションの制御に使用するオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="a0823-156">This is the object you use to control simulation.</span></span> <span data-ttu-id="a0823-157">これは、非同期メソッドでも実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0823-157">This must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="a0823-158">シミュレートされた人間を制御する</span><span class="sxs-lookup"><span data-stu-id="a0823-158">Control the simulated Human</span></span>

<span data-ttu-id="a0823-159">IPerceptionSimulationManager には、ISimulatedHuman オブジェクトを返すヒューマンプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="a0823-159">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="a0823-160">シミュレートされた人間を制御するには、このオブジェクトに対して操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="a0823-160">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="a0823-161">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="a0823-161">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="a0823-162">C# コンソールアプリケーションの基本的なサンプル</span><span class="sxs-lookup"><span data-stu-id="a0823-162">Basic Sample C# console application</span></span>

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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="a0823-163">拡張サンプル C# コンソールアプリケーション</span><span class="sxs-lookup"><span data-stu-id="a0823-163">Extended Sample C# console application</span></span>

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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="a0823-164">6つの自由度コントローラーに関する注意</span><span class="sxs-lookup"><span data-stu-id="a0823-164">Note on 6-DOF controllers</span></span>

<span data-ttu-id="a0823-165">シミュレートされた6つの自由コントローラーでメソッドのプロパティを呼び出す前に、コントローラーをアクティブにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0823-165">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="a0823-166">そうしないと、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="a0823-166">Not doing so will result in an exception.</span></span>  <span data-ttu-id="a0823-167">Windows 10 2019 年5月の更新プログラムでは、ISimulatedSixDofController オブジェクトの Status プロパティを SimulatedSixDofControllerStatus に設定することにより、シミュレートされた6つの自由度コントローラーをインストールしてアクティブ化することができます。</span><span class="sxs-lookup"><span data-stu-id="a0823-167">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="a0823-168">Windows 10 10 月2018更新プログラムおよびそれ以前のバージョンでは、\Windows\System32 フォルダーにある PerceptionSimulationDevice ツールを呼び出して、シミュレートされた6自由コントローラーを最初に個別にインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0823-168">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="a0823-169">このツールの使用方法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a0823-169">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="a0823-170">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="a0823-170">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="a0823-171">サポートされているアクションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a0823-171">Supported actions are:</span></span>
* <span data-ttu-id="a0823-172">i = インストール</span><span class="sxs-lookup"><span data-stu-id="a0823-172">i = install</span></span>
* <span data-ttu-id="a0823-173">q = クエリ</span><span class="sxs-lookup"><span data-stu-id="a0823-173">q = query</span></span>
* <span data-ttu-id="a0823-174">r = 削除</span><span class="sxs-lookup"><span data-stu-id="a0823-174">r = remove</span></span>

<span data-ttu-id="a0823-175">サポートされているインスタンスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a0823-175">Supported instances are:</span></span>
* <span data-ttu-id="a0823-176">1 = 左6自由コントローラー</span><span class="sxs-lookup"><span data-stu-id="a0823-176">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="a0823-177">2 = 右6自由コントローラー</span><span class="sxs-lookup"><span data-stu-id="a0823-177">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="a0823-178">プロセスの終了コードは、成功 (ゼロの戻り値) または失敗 (0 以外の戻り値) を示します。</span><span class="sxs-lookup"><span data-stu-id="a0823-178">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="a0823-179">' Q ' アクションを使用してコントローラーがインストールされているかどうかを照会する場合、コントローラーがまだインストールされていない場合、またはコントローラーがインストールされている場合は (1)、戻り値はゼロ (0) になります。</span><span class="sxs-lookup"><span data-stu-id="a0823-179">When using the 'q' action to query whether a controller is installed, the return value will be zero (0) if the controller isn't already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="a0823-180">Windows 10 10 月2018更新プログラムまたはそれ以前のバージョンでコントローラーを削除する場合は、最初に API を使用して状態を Off に設定してから、PerceptionSimulationDevice ツールを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a0823-180">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="a0823-181">このツールは、管理者として実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0823-181">This tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="a0823-182">API リファレンス</span><span class="sxs-lookup"><span data-stu-id="a0823-182">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="a0823-183">PerceptionSimulation. SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="a0823-183">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="a0823-184">シミュレートされたデバイスの種類について説明します</span><span class="sxs-lookup"><span data-stu-id="a0823-184">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="a0823-185">**PerceptionSimulation. SimulatedDeviceType**</span><span class="sxs-lookup"><span data-stu-id="a0823-185">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="a0823-186">架空の参照デバイス (PerceptionSimulationManager の既定値)</span><span class="sxs-lookup"><span data-stu-id="a0823-186">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="a0823-187">PerceptionSimulation... Trackermode</span><span class="sxs-lookup"><span data-stu-id="a0823-187">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="a0823-188">ヘッドトラッカーモードについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a0823-188">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="a0823-189">**PerceptionSimulation。既定値の場合**</span><span class="sxs-lookup"><span data-stu-id="a0823-189">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="a0823-190">既定のヘッド追跡。</span><span class="sxs-lookup"><span data-stu-id="a0823-190">Default Head Tracking.</span></span> <span data-ttu-id="a0823-191">これは、システムが実行時の状況に基づいて最適なヘッド追跡モードを選択することを意味します。</span><span class="sxs-lookup"><span data-stu-id="a0823-191">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="a0823-192">**PerceptionSimulation のようになります。**</span><span class="sxs-lookup"><span data-stu-id="a0823-192">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="a0823-193">方向のみのヘッド追跡。</span><span class="sxs-lookup"><span data-stu-id="a0823-193">Orientation Only Head Tracking.</span></span> <span data-ttu-id="a0823-194">これは、追跡される位置が信頼できない可能性があり、head 位置に依存する一部の機能が使用できない場合があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="a0823-194">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="a0823-195">**PerceptionSimulation を移動します。**</span><span class="sxs-lookup"><span data-stu-id="a0823-195">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="a0823-196">位置指定のヘッド追跡。</span><span class="sxs-lookup"><span data-stu-id="a0823-196">Positional Head Tracking.</span></span> <span data-ttu-id="a0823-197">これは、追跡されるヘッドの位置と向きは両方とも信頼できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="a0823-197">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="a0823-198">PerceptionSimulation. SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="a0823-198">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="a0823-199">シミュレートされたジェスチャについて説明します</span><span class="sxs-lookup"><span data-stu-id="a0823-199">Describes a simulated gesture</span></span>

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

<span data-ttu-id="a0823-200">**PerceptionSimulation. SimulatedGesture**</span><span class="sxs-lookup"><span data-stu-id="a0823-200">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="a0823-201">ジェスチャがないことを示すために使用される sentinel 値。</span><span class="sxs-lookup"><span data-stu-id="a0823-201">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="a0823-202">**PerceptionSimulation. SimulatedGesture. FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="a0823-202">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="a0823-203">指押下ジェスチャ。</span><span class="sxs-lookup"><span data-stu-id="a0823-203">A finger pressed gesture.</span></span>

<span data-ttu-id="a0823-204">**PerceptionSimulation. SimulatedGesture. FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="a0823-204">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="a0823-205">指で離されたジェスチャ。</span><span class="sxs-lookup"><span data-stu-id="a0823-205">A finger released gesture.</span></span>

<span data-ttu-id="a0823-206">**PerceptionSimulation. SimulatedGesture**</span><span class="sxs-lookup"><span data-stu-id="a0823-206">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="a0823-207">ホーム/システムジェスチャ。</span><span class="sxs-lookup"><span data-stu-id="a0823-207">The home/system gesture.</span></span>

<span data-ttu-id="a0823-208">**PerceptionSimulation. SimulatedGesture**</span><span class="sxs-lookup"><span data-stu-id="a0823-208">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="a0823-209">有効なジェスチャの最大数。</span><span class="sxs-lookup"><span data-stu-id="a0823-209">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="a0823-210">PerceptionSimulation. SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="a0823-210">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="a0823-211">シミュレートされた6自由コントローラーの可能性のある状態。</span><span class="sxs-lookup"><span data-stu-id="a0823-211">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="a0823-212">**PerceptionSimulation. SimulatedSixDofControllerStatus**</span><span class="sxs-lookup"><span data-stu-id="a0823-212">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="a0823-213">6自由コントローラーがオフになっています。</span><span class="sxs-lookup"><span data-stu-id="a0823-213">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="a0823-214">**PerceptionSimulation. SimulatedSixDofControllerStatus**</span><span class="sxs-lookup"><span data-stu-id="a0823-214">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="a0823-215">6自由コントローラーが有効になり、追跡されます。</span><span class="sxs-lookup"><span data-stu-id="a0823-215">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="a0823-216">**PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="a0823-216">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="a0823-217">6自由度コントローラーはオンになっていますが、追跡することはできません。</span><span class="sxs-lookup"><span data-stu-id="a0823-217">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="a0823-218">PerceptionSimulation. SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="a0823-218">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="a0823-219">シミュレートされた6自由コントローラーでサポートされるボタン。</span><span class="sxs-lookup"><span data-stu-id="a0823-219">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="a0823-220">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="a0823-220">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="a0823-221">ボタンを指定するために使用される sentinel 値。</span><span class="sxs-lookup"><span data-stu-id="a0823-221">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="a0823-222">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="a0823-222">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="a0823-223">[ホーム] ボタンが押された状態になります。</span><span class="sxs-lookup"><span data-stu-id="a0823-223">The Home button is pressed.</span></span>

<span data-ttu-id="a0823-224">**PerceptionSimulation. SimulatedSixDofControllerButton. メニュー**</span><span class="sxs-lookup"><span data-stu-id="a0823-224">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="a0823-225">メニューボタンが押された状態になります。</span><span class="sxs-lookup"><span data-stu-id="a0823-225">The Menu button is pressed.</span></span>

<span data-ttu-id="a0823-226">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="a0823-226">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="a0823-227">グリップボタンが押された状態になります。</span><span class="sxs-lookup"><span data-stu-id="a0823-227">The Grip button is pressed.</span></span>

<span data-ttu-id="a0823-228">**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="a0823-228">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="a0823-229">タッチパッドが押された状態になります。</span><span class="sxs-lookup"><span data-stu-id="a0823-229">The TouchPad is pressed.</span></span>

<span data-ttu-id="a0823-230">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="a0823-230">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="a0823-231">[選択] ボタンが押された状態になります。</span><span class="sxs-lookup"><span data-stu-id="a0823-231">The Select button is pressed.</span></span>

<span data-ttu-id="a0823-232">**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="a0823-232">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="a0823-233">タッチパッドがタッチされます。</span><span class="sxs-lookup"><span data-stu-id="a0823-233">The TouchPad is touched.</span></span>

<span data-ttu-id="a0823-234">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="a0823-234">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="a0823-235">サムスティックが押されています。</span><span class="sxs-lookup"><span data-stu-id="a0823-235">The Thumbstick is pressed.</span></span>

<span data-ttu-id="a0823-236">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="a0823-236">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="a0823-237">最大有効なボタン。</span><span class="sxs-lookup"><span data-stu-id="a0823-237">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="a0823-238">PerceptionSimulation. SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="a0823-238">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="a0823-239">シミュレートされた目の調整状態</span><span class="sxs-lookup"><span data-stu-id="a0823-239">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="a0823-240">**PerceptionSimulation. SimulatedEyesCalibrationState.**</span><span class="sxs-lookup"><span data-stu-id="a0823-240">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="a0823-241">目の調整は使用できません。</span><span class="sxs-lookup"><span data-stu-id="a0823-241">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="a0823-242">**PerceptionSimulation. SimulatedEyesCalibrationState**</span><span class="sxs-lookup"><span data-stu-id="a0823-242">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="a0823-243">目が調整されました。</span><span class="sxs-lookup"><span data-stu-id="a0823-243">The eyes have been calibrated.</span></span>  <span data-ttu-id="a0823-244">これが既定値です。</span><span class="sxs-lookup"><span data-stu-id="a0823-244">This is the default value.</span></span>

<span data-ttu-id="a0823-245">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configpostman**</span><span class="sxs-lookup"><span data-stu-id="a0823-245">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="a0823-246">目が調整されています。</span><span class="sxs-lookup"><span data-stu-id="a0823-246">The eyes are being calibrated.</span></span>

<span data-ttu-id="a0823-247">**PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="a0823-247">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="a0823-248">目を調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0823-248">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="a0823-249">PerceptionSimulation. SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="a0823-249">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="a0823-250">手の継手の追跡精度。</span><span class="sxs-lookup"><span data-stu-id="a0823-250">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="a0823-251">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy.**</span><span class="sxs-lookup"><span data-stu-id="a0823-251">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="a0823-252">ジョイントは追跡されません。</span><span class="sxs-lookup"><span data-stu-id="a0823-252">The joint isn't tracked.</span></span>

<span data-ttu-id="a0823-253">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="a0823-253">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="a0823-254">ジョイント位置が推論されます。</span><span class="sxs-lookup"><span data-stu-id="a0823-254">The joint position is inferred.</span></span>

<span data-ttu-id="a0823-255">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="a0823-255">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="a0823-256">ジョイントは完全に追跡されます。</span><span class="sxs-lookup"><span data-stu-id="a0823-256">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="a0823-257">PerceptionSimulation. SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="a0823-257">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="a0823-258">手の継手の追跡精度。</span><span class="sxs-lookup"><span data-stu-id="a0823-258">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="a0823-259">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="a0823-259">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="a0823-260">ハンドの指継手は、終了したポーズを反映するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="a0823-260">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="a0823-261">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="a0823-261">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="a0823-262">手の指継手は、オープンなポーズを反映するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="a0823-262">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="a0823-263">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="a0823-263">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="a0823-264">ハンドの指継手は、ポイントのポーズを反映するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="a0823-264">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="a0823-265">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="a0823-265">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="a0823-266">手の指継手は、ピンチのポーズを反映するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="a0823-266">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="a0823-267">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="a0823-267">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="a0823-268">SimulatedHandPose の最大有効値。</span><span class="sxs-lookup"><span data-stu-id="a0823-268">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="a0823-269">PerceptionSimulation の状態</span><span class="sxs-lookup"><span data-stu-id="a0823-269">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="a0823-270">再生の状態を記述します。</span><span class="sxs-lookup"><span data-stu-id="a0823-270">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="a0823-271">**PerceptionSimulation が停止しました。**</span><span class="sxs-lookup"><span data-stu-id="a0823-271">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="a0823-272">記録は現在停止しており、再生の準備ができています。</span><span class="sxs-lookup"><span data-stu-id="a0823-272">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="a0823-273">**PerceptionSimulation を再生します。**</span><span class="sxs-lookup"><span data-stu-id="a0823-273">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="a0823-274">記録は現在再生中です。</span><span class="sxs-lookup"><span data-stu-id="a0823-274">The recording is currently playing.</span></span>

<span data-ttu-id="a0823-275">**PerceptionSimulation が一時停止しました。**</span><span class="sxs-lookup"><span data-stu-id="a0823-275">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="a0823-276">記録は現在一時停止されています。</span><span class="sxs-lookup"><span data-stu-id="a0823-276">The recording is currently paused.</span></span>

<span data-ttu-id="a0823-277">**PerceptionSimulation を終了します。**</span><span class="sxs-lookup"><span data-stu-id="a0823-277">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="a0823-278">記録が最後に達しました。</span><span class="sxs-lookup"><span data-stu-id="a0823-278">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="a0823-279">PerceptionSimulation. Vector3</span><span class="sxs-lookup"><span data-stu-id="a0823-279">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="a0823-280">3D 空間の点またはベクターを表す3つのコンポーネントベクターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a0823-280">Describes a three components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="a0823-281">**PerceptionSimulation. Vector3**</span><span class="sxs-lookup"><span data-stu-id="a0823-281">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="a0823-282">ベクトルの X 成分。</span><span class="sxs-lookup"><span data-stu-id="a0823-282">The X component of the vector.</span></span>

<span data-ttu-id="a0823-283">**PerceptionSimulation. Vector3**</span><span class="sxs-lookup"><span data-stu-id="a0823-283">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="a0823-284">ベクトルの Y 成分。</span><span class="sxs-lookup"><span data-stu-id="a0823-284">The Y component of the vector.</span></span>

<span data-ttu-id="a0823-285">**PerceptionSimulation. Vector3**</span><span class="sxs-lookup"><span data-stu-id="a0823-285">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="a0823-286">ベクトルの Z 成分。</span><span class="sxs-lookup"><span data-stu-id="a0823-286">The Z component of the vector.</span></span>

<span data-ttu-id="a0823-287">**#Ctor PerceptionSimulation (system.string、system.string、system.string) を (system.string) します。**</span><span class="sxs-lookup"><span data-stu-id="a0823-287">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="a0823-288">新しい Vector3 を構築します。</span><span class="sxs-lookup"><span data-stu-id="a0823-288">Construct a new Vector3.</span></span>

<span data-ttu-id="a0823-289">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0823-289">Parameters</span></span>
* <span data-ttu-id="a0823-290">x-ベクトルの x 成分。</span><span class="sxs-lookup"><span data-stu-id="a0823-290">x - The x component of the vector.</span></span>
* <span data-ttu-id="a0823-291">y-ベクトルの y 成分。</span><span class="sxs-lookup"><span data-stu-id="a0823-291">y - The y component of the vector.</span></span>
* <span data-ttu-id="a0823-292">z-ベクトルの z 成分。</span><span class="sxs-lookup"><span data-stu-id="a0823-292">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="a0823-293">PerceptionSimulation. Rotation3</span><span class="sxs-lookup"><span data-stu-id="a0823-293">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="a0823-294">3つのコンポーネントのローテーションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a0823-294">Describes a three components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="a0823-295">**PerceptionSimulation. Rotation3**</span><span class="sxs-lookup"><span data-stu-id="a0823-295">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="a0823-296">X 軸を中心とする回転のピッチ成分。</span><span class="sxs-lookup"><span data-stu-id="a0823-296">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="a0823-297">**PerceptionSimulation. Rotation3**</span><span class="sxs-lookup"><span data-stu-id="a0823-297">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="a0823-298">Y 軸を中心とする回転のヨー要素。</span><span class="sxs-lookup"><span data-stu-id="a0823-298">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="a0823-299">**PerceptionSimulation. Rotation3**</span><span class="sxs-lookup"><span data-stu-id="a0823-299">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="a0823-300">Z 軸を中心とする回転のロールコンポーネント。</span><span class="sxs-lookup"><span data-stu-id="a0823-300">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="a0823-301">**#Ctor PerceptionSimulation (system.string、system.string、system.string) を (system.string) します。**</span><span class="sxs-lookup"><span data-stu-id="a0823-301">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="a0823-302">新しい Rotation3 を構築します。</span><span class="sxs-lookup"><span data-stu-id="a0823-302">Construct a new Rotation3.</span></span>

<span data-ttu-id="a0823-303">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0823-303">Parameters</span></span>
* <span data-ttu-id="a0823-304">ピッチ-回転のピッチ成分。</span><span class="sxs-lookup"><span data-stu-id="a0823-304">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="a0823-305">ヨー-回転のヨーコンポーネント。</span><span class="sxs-lookup"><span data-stu-id="a0823-305">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="a0823-306">roll-回転のロールコンポーネント。</span><span class="sxs-lookup"><span data-stu-id="a0823-306">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="a0823-307">PerceptionSimulation. SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="a0823-307">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="a0823-308">シミュレートされたハンドでのジョイントの構成について説明します。</span><span class="sxs-lookup"><span data-stu-id="a0823-308">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="a0823-309">**PerceptionSimulation. SimulatedHandJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="a0823-309">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="a0823-310">ジョイントの位置。</span><span class="sxs-lookup"><span data-stu-id="a0823-310">The position of the joint.</span></span>

<span data-ttu-id="a0823-311">**PerceptionSimulation. SimulatedHandJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="a0823-311">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="a0823-312">ジョイントの回転。</span><span class="sxs-lookup"><span data-stu-id="a0823-312">The rotation of the joint.</span></span>

<span data-ttu-id="a0823-313">**PerceptionSimulation. SimulatedHandJointConfiguration の精度**</span><span class="sxs-lookup"><span data-stu-id="a0823-313">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="a0823-314">ジョイントの追跡精度。</span><span class="sxs-lookup"><span data-stu-id="a0823-314">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="a0823-315">PerceptionSimulation</span><span class="sxs-lookup"><span data-stu-id="a0823-315">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="a0823-316">カメラで一般的に使用される、視錐のビューについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a0823-316">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="a0823-317">**PerceptionSimulation。 Near**</span><span class="sxs-lookup"><span data-stu-id="a0823-317">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="a0823-318">視錐に含まれる最小距離。</span><span class="sxs-lookup"><span data-stu-id="a0823-318">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="a0823-319">**PerceptionSimulation です。**</span><span class="sxs-lookup"><span data-stu-id="a0823-319">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="a0823-320">視錐に含まれる最大距離。</span><span class="sxs-lookup"><span data-stu-id="a0823-320">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="a0823-321">**PerceptionSimulation. FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="a0823-321">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="a0823-322">視錐のビューの水平方向のフィールド (π未満のラジアン)。</span><span class="sxs-lookup"><span data-stu-id="a0823-322">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="a0823-323">**PerceptionSimulation. AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="a0823-323">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="a0823-324">ビューの垂直方向のフィールドから、ビューの垂直方向のフィールドまでの比率。</span><span class="sxs-lookup"><span data-stu-id="a0823-324">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a><span data-ttu-id="a0823-325">PerceptionSimulation. SimulatedDisplayConfiguration</span><span class="sxs-lookup"><span data-stu-id="a0823-325">Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration</span></span>

<span data-ttu-id="a0823-326">シミュレートされたヘッドセットの表示の構成について説明します。</span><span class="sxs-lookup"><span data-stu-id="a0823-326">Describes the configuration of the simulated headset's display.</span></span>

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

<span data-ttu-id="a0823-327">**PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyePosition**</span><span class="sxs-lookup"><span data-stu-id="a0823-327">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyePosition**</span></span>

<span data-ttu-id="a0823-328">ステレオレンダリングの目的で、ヘッドの中心から左目への変換。</span><span class="sxs-lookup"><span data-stu-id="a0823-328">The transform from the center of the head to the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="a0823-329">**PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="a0823-329">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyeRotation**</span></span>

<span data-ttu-id="a0823-330">ステレオレンダリングの目的での左目の回転。</span><span class="sxs-lookup"><span data-stu-id="a0823-330">The rotation of the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="a0823-331">**PerceptionSimulation. SimulatedDisplayConfiguration. RightEyePosition**</span><span class="sxs-lookup"><span data-stu-id="a0823-331">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyePosition**</span></span>

<span data-ttu-id="a0823-332">ステレオレンダリングの目的で、ヘッドの中心から右目への変換。</span><span class="sxs-lookup"><span data-stu-id="a0823-332">The transform from the center of the head to the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="a0823-333">**PerceptionSimulation. SimulatedDisplayConfiguration. RightEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="a0823-333">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyeRotation**</span></span>

<span data-ttu-id="a0823-334">ステレオレンダリングの目的での右目の回転。</span><span class="sxs-lookup"><span data-stu-id="a0823-334">The rotation of the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="a0823-335">**PerceptionSimulation. SimulatedDisplayConfiguration. Ipd**</span><span class="sxs-lookup"><span data-stu-id="a0823-335">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.Ipd**</span></span>

<span data-ttu-id="a0823-336">ステレオレンダリングのためにシステムによって報告された Ipd 値。</span><span class="sxs-lookup"><span data-stu-id="a0823-336">The Ipd value reported by the system for purposes of stereo rendering.</span></span>

<span data-ttu-id="a0823-337">**PerceptionSimulation. SimulatedDisplayConfiguration (変換)**</span><span class="sxs-lookup"><span data-stu-id="a0823-337">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyEyeTransforms**</span></span>

<span data-ttu-id="a0823-338">左辺と右辺の変換に指定された値が有効であると見なされ、実行中のシステムに適用されるかどうか。</span><span class="sxs-lookup"><span data-stu-id="a0823-338">Whether the values provided for left and right eye transforms should be considered valid and applied to the running system.</span></span>

<span data-ttu-id="a0823-339">**PerceptionSimulation. SimulatedDisplayConfiguration. ApplyIpd**</span><span class="sxs-lookup"><span data-stu-id="a0823-339">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyIpd**</span></span>

<span data-ttu-id="a0823-340">Ipd に指定された値が有効と見なされ、実行中のシステムに適用されるかどうか。</span><span class="sxs-lookup"><span data-stu-id="a0823-340">Whether the value provided for Ipd should be considered valid and applied to the running system.</span></span>


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="a0823-341">PerceptionSimulation. IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="a0823-341">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="a0823-342">デバイスの制御に使用されるパケットを生成するためのルート。</span><span class="sxs-lookup"><span data-stu-id="a0823-342">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="a0823-343">**PerceptionSimulation. IPerceptionSimulationManager**</span><span class="sxs-lookup"><span data-stu-id="a0823-343">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="a0823-344">シミュレートされた人間とシミュレートされた世界を解釈する、シミュレートされたデバイスオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-344">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="a0823-345">**PerceptionSimulation. IPerceptionSimulationManager**</span><span class="sxs-lookup"><span data-stu-id="a0823-345">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="a0823-346">シミュレートされた人間を制御するオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-346">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="a0823-347">**PerceptionSimulation. IPerceptionSimulationManager**</span><span class="sxs-lookup"><span data-stu-id="a0823-347">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="a0823-348">シミュレーションを既定の状態にリセットします。</span><span class="sxs-lookup"><span data-stu-id="a0823-348">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="a0823-349">PerceptionSimulation. ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="a0823-349">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="a0823-350">シミュレートされた世界とシミュレートされた人間を解釈する、デバイスを記述するインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0823-350">Interface describing the device, which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="a0823-351">**PerceptionSimulation. ISimulatedDevice Tracker**</span><span class="sxs-lookup"><span data-stu-id="a0823-351">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="a0823-352">シミュレートされたデバイスからヘッドトラッカーを取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-352">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="a0823-353">**PerceptionSimulation. ISimulatedDevice Tracker**</span><span class="sxs-lookup"><span data-stu-id="a0823-353">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="a0823-354">シミュレートされたデバイスからハンドトラッカーを取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-354">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="a0823-355">**PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType (PerceptionSimulation. SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="a0823-355">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="a0823-356">シミュレートされたデバイスのプロパティを、指定したデバイスの種類に合わせて設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-356">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="a0823-357">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0823-357">Parameters</span></span>
* <span data-ttu-id="a0823-358">type-シミュレートされたデバイスの新しい種類</span><span class="sxs-lookup"><span data-stu-id="a0823-358">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice2"></a><span data-ttu-id="a0823-359">PerceptionSimulation. ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="a0823-359">Microsoft.PerceptionSimulation.ISimulatedDevice2</span></span>

<span data-ttu-id="a0823-360">ISimulatedDevice を ISimulatedDevice2 にキャストすると、追加のプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a0823-360">Additional properties are available by casting the ISimulatedDevice to ISimulatedDevice2</span></span>

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

<span data-ttu-id="a0823-361">**PerceptionSimulation. ISimulatedDevice2. IsUserPresent**</span><span class="sxs-lookup"><span data-stu-id="a0823-361">**Microsoft.PerceptionSimulation.ISimulatedDevice2.IsUserPresent**</span></span>

<span data-ttu-id="a0823-362">シミュレートされた人間がヘッドセットをアクティブに装着しているかどうかを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-362">Retrieve or set whether or not the simulated human is actively wearing the headset.</span></span>

<span data-ttu-id="a0823-363">**PerceptionSimulation. ISimulatedDevice2. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="a0823-363">**Microsoft.PerceptionSimulation.ISimulatedDevice2.DisplayConfiguration**</span></span>

<span data-ttu-id="a0823-364">シミュレートされた表示のプロパティを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-364">Retrieve or set the properties of the simulated display.</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="a0823-365">PerceptionSimulation. ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="a0823-365">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="a0823-366">シミュレートされた人間の頭を追跡する、シミュレートされたデバイスの部分を説明するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="a0823-366">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="a0823-367">**PerceptionSimulation. ISimulatedHeadTracker.-Trackermode**</span><span class="sxs-lookup"><span data-stu-id="a0823-367">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="a0823-368">現在のヘッドトラッカーモードを取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-368">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="a0823-369">PerceptionSimulation. ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="a0823-369">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="a0823-370">シミュレートされた人間の手を追跡するシミュレートされたデバイスの部分を説明するインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0823-370">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="a0823-371">**PerceptionSimulation. ISimulatedHandTracker. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="a0823-371">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="a0823-372">世界のリレーションを使用してノードの位置をメートル単位で取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-372">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="a0823-373">**PerceptionSimulation. ISimulatedHandTracker**</span><span class="sxs-lookup"><span data-stu-id="a0823-373">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="a0823-374">頭の中心を基準とした、シミュレートされたハンドトラッカーの位置を取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-374">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="a0823-375">**PerceptionSimulation. ISimulatedHandTracker**</span><span class="sxs-lookup"><span data-stu-id="a0823-375">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="a0823-376">シミュレートされたハンドトラッカーの下向きのピッチを取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-376">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="a0823-377">**PerceptionSimulation は無視されました。**</span><span class="sxs-lookup"><span data-stu-id="a0823-377">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="a0823-378">シミュレートされたハンドトラッカーを無視するかどうかを取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-378">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="a0823-379">無視すると、両方のハンドが常に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a0823-379">When ignored, both hands are always visible.</span></span> <span data-ttu-id="a0823-380">無視しない場合 (既定)、ハンドトラッカーの視錐の内側にいる場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="a0823-380">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="a0823-381">**PerceptionSimulation. ISimulatedHandTracker**</span><span class="sxs-lookup"><span data-stu-id="a0823-381">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="a0823-382">ハンドがシミュレートされたハンドトラッカーに表示されるかどうかを判断するために使用する、視錐のプロパティを取得および設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-382">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="a0823-383">PerceptionSimulation. ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="a0823-383">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="a0823-384">シミュレートされた人間を制御するための最上位のインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="a0823-384">Top-level interface for controlling the simulated human.</span></span>

```
public interface ISimulatedHuman 
{
    Vector3 WorldPosition { get; set; }
    float Direction { get; set; }
    float Height { get; set; }
    ISimulatedHand LeftHand { get; }
    ISimulatedHand RightHand { get; }
    ISimulatedHead Head { get; }s
    void Move(Vector3 translation);
    void Rotate(float radians);
}
```

<span data-ttu-id="a0823-385">**PerceptionSimulation. ISimulatedHuman. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="a0823-385">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="a0823-386">世界中のノードの位置をメートル単位で取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-386">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="a0823-387">この位置は、人間のフィートの中央の点に対応しています。</span><span class="sxs-lookup"><span data-stu-id="a0823-387">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="a0823-388">**PerceptionSimulation. ISimulatedHuman**</span><span class="sxs-lookup"><span data-stu-id="a0823-388">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="a0823-389">世界中のシミュレートされた人間の顔の方向を取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-389">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="a0823-390">0ラジアンは負の Z 軸を中心にします。</span><span class="sxs-lookup"><span data-stu-id="a0823-390">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="a0823-391">正のラジアンは、Y 軸について時計回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="a0823-391">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="a0823-392">**PerceptionSimulation. ISimulatedHuman**</span><span class="sxs-lookup"><span data-stu-id="a0823-392">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="a0823-393">シミュレートされた人間の高さをメートル単位で取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-393">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="a0823-394">**PerceptionSimulation. ISimulatedHuman. LeftHand**</span><span class="sxs-lookup"><span data-stu-id="a0823-394">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="a0823-395">シミュレートされた人間の左側を取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-395">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="a0823-396">**PerceptionSimulation. ISimulatedHuman. 右**</span><span class="sxs-lookup"><span data-stu-id="a0823-396">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="a0823-397">シミュレートされた人間の右側を取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-397">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="a0823-398">**PerceptionSimulation. ISimulatedHuman**</span><span class="sxs-lookup"><span data-stu-id="a0823-398">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="a0823-399">シミュレートされた人間の先頭を取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-399">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="a0823-400">**PerceptionSimulation (ISimulatedHuman) (PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="a0823-400">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="a0823-401">シミュレートされた人間を、現在の位置を基準としてメートル単位で移動します。</span><span class="sxs-lookup"><span data-stu-id="a0823-401">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="a0823-402">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0823-402">Parameters</span></span>
* <span data-ttu-id="a0823-403">translation-現在の位置を基準とした、移動する平行移動。</span><span class="sxs-lookup"><span data-stu-id="a0823-403">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="a0823-404">**PerceptionSimulation. ISimulatedHuman (System. Single)**</span><span class="sxs-lookup"><span data-stu-id="a0823-404">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="a0823-405">現在の方向を基準にして、シミュレートされた人間を Y 軸に対して時計回りに回転させます</span><span class="sxs-lookup"><span data-stu-id="a0823-405">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="a0823-406">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0823-406">Parameters</span></span>
* <span data-ttu-id="a0823-407">ラジアン-Y 軸を中心に回転する量。</span><span class="sxs-lookup"><span data-stu-id="a0823-407">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="a0823-408">PerceptionSimulation. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="a0823-408">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="a0823-409">ISimulatedHuman を ISimulatedHuman2 にキャストすると、追加のプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a0823-409">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="a0823-410">**PerceptionSimulation. ISimulatedHuman2 Controller**</span><span class="sxs-lookup"><span data-stu-id="a0823-410">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="a0823-411">左6自由コントローラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-411">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="a0823-412">**PerceptionSimulation. ISimulatedHuman2 コントローラー**</span><span class="sxs-lookup"><span data-stu-id="a0823-412">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="a0823-413">右6自由コントローラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-413">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="a0823-414">PerceptionSimulation. ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="a0823-414">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="a0823-415">シミュレートされた人間の手を記述するインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0823-415">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="a0823-416">**PerceptionSimulation. ISimulatedHand. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="a0823-416">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="a0823-417">世界のリレーションを使用してノードの位置をメートル単位で取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-417">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="a0823-418">**PerceptionSimulation. ISimulatedHand**</span><span class="sxs-lookup"><span data-stu-id="a0823-418">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="a0823-419">人間に対するシミュレートされたハンドの位置をメートル単位で取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-419">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="a0823-420">**PerceptionSimulation. ISimulatedHand**</span><span class="sxs-lookup"><span data-stu-id="a0823-420">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="a0823-421">ハンドが現在アクティブになっているかどうかを取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-421">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="a0823-422">**PerceptionSimulation. ISimulatedHand**</span><span class="sxs-lookup"><span data-stu-id="a0823-422">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="a0823-423">ハンドが現在 SimulatedDevice に表示されているかどうかを取得します (つまり、そのハンドが、トラッカーによって検出される位置にあるかどうか)。</span><span class="sxs-lookup"><span data-stu-id="a0823-423">Retrieve whether the hand is currently visible to the SimulatedDevice (that is, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="a0823-424">\**PerceptionSimulation. ISimulatedHand. Ensurevisible\**</span><span class="sxs-lookup"><span data-stu-id="a0823-424">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="a0823-425">SimulatedDevice に見えるようにハンドを移動します。</span><span class="sxs-lookup"><span data-stu-id="a0823-425">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="a0823-426">**PerceptionSimulation (ISimulatedHand) (PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="a0823-426">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="a0823-427">シミュレートされたハンドの位置を、現在の位置を基準としてメートル単位で移動します。</span><span class="sxs-lookup"><span data-stu-id="a0823-427">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="a0823-428">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0823-428">Parameters</span></span>
* <span data-ttu-id="a0823-429">translation-シミュレートされたハンドを変換する量。</span><span class="sxs-lookup"><span data-stu-id="a0823-429">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="a0823-430">**ISimulatedHand (PerceptionSimulation) () (PerceptionSimulation)**</span><span class="sxs-lookup"><span data-stu-id="a0823-430">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="a0823-431">シミュレートされたハンドを使用してジェスチャを実行します。</span><span class="sxs-lookup"><span data-stu-id="a0823-431">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="a0823-432">ハンドが有効になっている場合にのみ、システムによって検出されます。</span><span class="sxs-lookup"><span data-stu-id="a0823-432">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="a0823-433">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0823-433">Parameters</span></span>
* <span data-ttu-id="a0823-434">ジェスチャ-実行するジェスチャ。</span><span class="sxs-lookup"><span data-stu-id="a0823-434">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="a0823-435">PerceptionSimulation. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="a0823-435">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="a0823-436">ISimulatedHand を ISimulatedHand2 にキャストすると、追加のプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a0823-436">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="a0823-437">**PerceptionSimulation. ISimulatedHand2**</span><span class="sxs-lookup"><span data-stu-id="a0823-437">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="a0823-438">シミュレートされたハンドの回転を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-438">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="a0823-439">正のラジアンは、軸に沿って表示すると時計回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="a0823-439">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="a0823-440">PerceptionSimulation. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="a0823-440">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="a0823-441">ISimulatedHand を ISimulatedHand3 にキャストすると、追加のプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a0823-441">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="a0823-442">**PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="a0823-442">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="a0823-443">指定されたジョイントの共同構成を取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-443">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="a0823-444">**PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="a0823-444">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="a0823-445">指定されたジョイントの結合構成を設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-445">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="a0823-446">**PerceptionSimulation. ISimulatedHand3. SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="a0823-446">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="a0823-447">アニメーション化するオプションのフラグを持つ既知のポーズにハンドを設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-447">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="a0823-448">注: アニメーション化によって、最終的な結合構成がすぐに反映されることはありません。</span><span class="sxs-lookup"><span data-stu-id="a0823-448">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="a0823-449">PerceptionSimulation. ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="a0823-449">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="a0823-450">シミュレートされた人間の先頭を記述するインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="a0823-450">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="a0823-451">**PerceptionSimulation. ISimulatedHead. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="a0823-451">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="a0823-452">世界のリレーションを使用してノードの位置をメートル単位で取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-452">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="a0823-453">**PerceptionSimulation. ISimulatedHead**</span><span class="sxs-lookup"><span data-stu-id="a0823-453">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="a0823-454">シミュレートされたヘッドの回転を取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-454">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="a0823-455">正のラジアンは、軸に沿って表示すると時計回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="a0823-455">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="a0823-456">**PerceptionSimulation. ISimulatedHead**</span><span class="sxs-lookup"><span data-stu-id="a0823-456">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="a0823-457">シミュレートされたヘッドの直径を取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-457">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="a0823-458">この値は、ヘッドの中心 (回転点) を決定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="a0823-458">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="a0823-459">**PerceptionSimulation (ISimulatedHead) (PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="a0823-459">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="a0823-460">シミュレートされた頭を現在の回転に対して回転します。</span><span class="sxs-lookup"><span data-stu-id="a0823-460">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="a0823-461">正のラジアンは、軸に沿って表示すると時計回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="a0823-461">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="a0823-462">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0823-462">Parameters</span></span>
* <span data-ttu-id="a0823-463">rotation-回転する量。</span><span class="sxs-lookup"><span data-stu-id="a0823-463">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="a0823-464">PerceptionSimulation. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="a0823-464">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="a0823-465">ISimulatedHead を ISimulatedHead2 にキャストすると、追加のプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a0823-465">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="a0823-466">**PerceptionSimulation. ISimulatedHead2**</span><span class="sxs-lookup"><span data-stu-id="a0823-466">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="a0823-467">シミュレートされた人間の目を取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-467">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="a0823-468">PerceptionSimulation. ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="a0823-468">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="a0823-469">シミュレートされた人間に関連付けられた6自由コントローラーを記述するインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="a0823-469">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="a0823-470">**PerceptionSimulation. ISimulatedSixDofController. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="a0823-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="a0823-471">世界のリレーションを使用してノードの位置をメートル単位で取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-471">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="a0823-472">**PerceptionSimulation. ISimulatedSixDofController**</span><span class="sxs-lookup"><span data-stu-id="a0823-472">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="a0823-473">コントローラーの現在の状態を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-473">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="a0823-474">移動、回転、または押すボタンの呼び出しが成功する前に、コントローラーの状態を [オフ] 以外の値に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0823-474">The controller status must be set to a value other than Off before any calls to move, rotate, or press buttons will succeed.</span></span>

<span data-ttu-id="a0823-475">**PerceptionSimulation. ISimulatedSixDofController**</span><span class="sxs-lookup"><span data-stu-id="a0823-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="a0823-476">ユーザーに対してシミュレートされたコントローラーの位置をメートル単位で取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-476">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="a0823-477">**PerceptionSimulation. ISimulatedSixDofController**</span><span class="sxs-lookup"><span data-stu-id="a0823-477">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="a0823-478">シミュレートされたコントローラーの向きを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-478">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="a0823-479">**PerceptionSimulation (ISimulatedSixDofController) (PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="a0823-479">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="a0823-480">シミュレートされたコントローラーの位置を、現在の位置 (メートル単位) に相対的に移動します。</span><span class="sxs-lookup"><span data-stu-id="a0823-480">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="a0823-481">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0823-481">Parameters</span></span>
* <span data-ttu-id="a0823-482">translation-シミュレートされたコントローラーを変換する量。</span><span class="sxs-lookup"><span data-stu-id="a0823-482">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="a0823-483">**ISimulatedSixDofController (SimulatedSixDofControllerButton) () PerceptionSimulation**</span><span class="sxs-lookup"><span data-stu-id="a0823-483">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="a0823-484">シミュレートされたコントローラーでボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="a0823-484">Press a button on the simulated controller.</span></span>  <span data-ttu-id="a0823-485">コントローラーが有効になっている場合にのみ、システムによって検出されます。</span><span class="sxs-lookup"><span data-stu-id="a0823-485">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="a0823-486">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0823-486">Parameters</span></span>
* <span data-ttu-id="a0823-487">button-押すボタン。</span><span class="sxs-lookup"><span data-stu-id="a0823-487">button - The button to press.</span></span>

<span data-ttu-id="a0823-488">**PerceptionSimulation (ISimulatedSixDofController) (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="a0823-488">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="a0823-489">シミュレートされたコントローラーでボタンを離します。</span><span class="sxs-lookup"><span data-stu-id="a0823-489">Release a button on the simulated controller.</span></span>  <span data-ttu-id="a0823-490">コントローラーが有効になっている場合にのみ、システムによって検出されます。</span><span class="sxs-lookup"><span data-stu-id="a0823-490">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="a0823-491">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0823-491">Parameters</span></span>
* <span data-ttu-id="a0823-492">ボタン-リリースするボタン。</span><span class="sxs-lookup"><span data-stu-id="a0823-492">button - The button to release.</span></span>

<span data-ttu-id="a0823-493">**PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="a0823-493">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="a0823-494">シミュレートされたコントローラーのタッチパッド上でシミュレートされた指の位置を取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-494">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="a0823-495">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0823-495">Parameters</span></span>
* <span data-ttu-id="a0823-496">x-指の水平方向の位置。</span><span class="sxs-lookup"><span data-stu-id="a0823-496">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="a0823-497">y-指の垂直方向の位置。</span><span class="sxs-lookup"><span data-stu-id="a0823-497">y - The vertical position of the finger.</span></span>

<span data-ttu-id="a0823-498">**PerceptionSimulation (float, float) の位置を ISimulatedSixDofController します。**</span><span class="sxs-lookup"><span data-stu-id="a0823-498">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="a0823-499">シミュレートされたコントローラーのタッチパッドでシミュレートされた指の位置を設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-499">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="a0823-500">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0823-500">Parameters</span></span>
* <span data-ttu-id="a0823-501">x-指の水平方向の位置。</span><span class="sxs-lookup"><span data-stu-id="a0823-501">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="a0823-502">y-指の垂直方向の位置。</span><span class="sxs-lookup"><span data-stu-id="a0823-502">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="a0823-503">PerceptionSimulation. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="a0823-503">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="a0823-504">ISimulatedSixDofController を ISimulatedSixDofController2 にキャストすると、追加のプロパティとメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a0823-504">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="a0823-505">**PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="a0823-505">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="a0823-506">シミュレートされたコントローラー上のシミュレートされたサムスティックの位置を取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-506">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="a0823-507">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0823-507">Parameters</span></span>
* <span data-ttu-id="a0823-508">x-サムスティックの水平方向の位置。</span><span class="sxs-lookup"><span data-stu-id="a0823-508">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="a0823-509">y-サムスティックの垂直方向の位置。</span><span class="sxs-lookup"><span data-stu-id="a0823-509">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="a0823-510">**PerceptionSimulation. ISimulatedSixDofController2. SetThumbstickPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="a0823-510">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="a0823-511">シミュレートされたコントローラーのシミュレートされたサムスティックの位置を設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-511">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="a0823-512">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0823-512">Parameters</span></span>
* <span data-ttu-id="a0823-513">x-サムスティックの水平方向の位置。</span><span class="sxs-lookup"><span data-stu-id="a0823-513">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="a0823-514">y-サムスティックの垂直方向の位置。</span><span class="sxs-lookup"><span data-stu-id="a0823-514">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="a0823-515">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="a0823-515">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="a0823-516">シミュレートされたコントローラーのバッテリレベルを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-516">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="a0823-517">値は0.0 より大きく、100.0 以下でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="a0823-517">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="a0823-518">PerceptionSimulation. ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="a0823-518">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="a0823-519">シミュレートされた人間の目を表すインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="a0823-519">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="a0823-520">**PerceptionSimulation. ISimulatedEyes**</span><span class="sxs-lookup"><span data-stu-id="a0823-520">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="a0823-521">シミュレートされた目の回転を取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-521">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="a0823-522">正のラジアンは、軸に沿って表示すると時計回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="a0823-522">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="a0823-523">**PerceptionSimulation (ISimulatedEyes) (PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="a0823-523">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="a0823-524">現在の回転と比較して、シミュレートされた目を回転します。</span><span class="sxs-lookup"><span data-stu-id="a0823-524">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="a0823-525">正のラジアンは、軸に沿って表示すると時計回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="a0823-525">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="a0823-526">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0823-526">Parameters</span></span>
* <span data-ttu-id="a0823-527">rotation-回転する量。</span><span class="sxs-lookup"><span data-stu-id="a0823-527">rotation - The amount to rotate.</span></span>

<span data-ttu-id="a0823-528">**PerceptionSimulation. ISimulatedEyes. CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="a0823-528">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="a0823-529">シミュレートされた目の調整状態を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="a0823-529">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="a0823-530">**PerceptionSimulation. ISimulatedEyes. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="a0823-530">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="a0823-531">世界のリレーションを使用してノードの位置をメートル単位で取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-531">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="a0823-532">PerceptionSimulation. ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="a0823-532">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="a0823-533">再生用に読み込まれた単一の記録と対話するためのインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="a0823-533">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="a0823-534">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="a0823-534">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="a0823-535">記録内のデータ型の一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-535">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="a0823-536">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="a0823-536">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="a0823-537">記録の現在の状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="a0823-537">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="a0823-538">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="a0823-538">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="a0823-539">再生を開始します。</span><span class="sxs-lookup"><span data-stu-id="a0823-539">Start the playback.</span></span> <span data-ttu-id="a0823-540">記録が一時停止されている場合は、一時停止した場所から再生が再開されます。停止した場合は、最初から再生が開始されます。</span><span class="sxs-lookup"><span data-stu-id="a0823-540">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="a0823-541">既に再生中の場合、この呼び出しは無視されます。</span><span class="sxs-lookup"><span data-stu-id="a0823-541">If already playing, this call is ignored.</span></span>

<span data-ttu-id="a0823-542">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="a0823-542">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="a0823-543">現在の場所で再生を一時停止します。</span><span class="sxs-lookup"><span data-stu-id="a0823-543">Pauses the playback at its current location.</span></span> <span data-ttu-id="a0823-544">記録が停止している場合、呼び出しは無視されます。</span><span class="sxs-lookup"><span data-stu-id="a0823-544">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="a0823-545">**PerceptionSimulation. ISimulationRecording (System. UInt64)**</span><span class="sxs-lookup"><span data-stu-id="a0823-545">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="a0823-546">指定した時間 (先頭から100ナノ秒単位) に記録をシークし、その位置で一時停止します。</span><span class="sxs-lookup"><span data-stu-id="a0823-546">Seeks the recording to the specified time (in 100-nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="a0823-547">時刻が記録の末尾を越えている場合は、最後のフレームで一時停止します。</span><span class="sxs-lookup"><span data-stu-id="a0823-547">If the time is beyond the end of the recording, it's paused at the last frame.</span></span>

<span data-ttu-id="a0823-548">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0823-548">Parameters</span></span>
* <span data-ttu-id="a0823-549">ティック-シークする時刻。</span><span class="sxs-lookup"><span data-stu-id="a0823-549">ticks - The time to which to seek.</span></span>

<span data-ttu-id="a0823-550">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="a0823-550">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="a0823-551">再生を停止し、位置を先頭にリセットします。</span><span class="sxs-lookup"><span data-stu-id="a0823-551">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="a0823-552">PerceptionSimulation. ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="a0823-552">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="a0823-553">再生中に状態の変更を受信するためのインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="a0823-553">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="a0823-554">**PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged (PerceptionSimulation. PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="a0823-554">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="a0823-555">ISimulationRecording の再生状態が変更されたときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a0823-555">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="a0823-556">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0823-556">Parameters</span></span>
* <span data-ttu-id="a0823-557">newState-記録の新しい状態。</span><span class="sxs-lookup"><span data-stu-id="a0823-557">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="a0823-558">PerceptionSimulation. PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="a0823-558">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="a0823-559">認識シミュレーションオブジェクトを作成するためのルートオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a0823-559">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="a0823-560">**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager (PerceptionSimulation. ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="a0823-560">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="a0823-561">シミュレートされたパケットを生成し、指定したシンクに配信するために、オブジェクトでを作成します。</span><span class="sxs-lookup"><span data-stu-id="a0823-561">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="a0823-562">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0823-562">Parameters</span></span>
* <span data-ttu-id="a0823-563">sink-生成されたすべてのパケットを受信するシンク。</span><span class="sxs-lookup"><span data-stu-id="a0823-563">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="a0823-564">戻り値</span><span class="sxs-lookup"><span data-stu-id="a0823-564">Return value</span></span>

<span data-ttu-id="a0823-565">作成されたマネージャー。</span><span class="sxs-lookup"><span data-stu-id="a0823-565">The created Manager.</span></span>

<span data-ttu-id="a0823-566">**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording (System.string)**</span><span class="sxs-lookup"><span data-stu-id="a0823-566">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="a0823-567">シンクを作成します。このシンクは、指定されたパスのファイルに受信したすべてのパケットを格納します。</span><span class="sxs-lookup"><span data-stu-id="a0823-567">Create a sink, which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="a0823-568">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0823-568">Parameters</span></span>
* <span data-ttu-id="a0823-569">path-作成するファイルのパス。</span><span class="sxs-lookup"><span data-stu-id="a0823-569">path - The path of the file to create.</span></span>

<span data-ttu-id="a0823-570">戻り値</span><span class="sxs-lookup"><span data-stu-id="a0823-570">Return value</span></span>

<span data-ttu-id="a0823-571">作成されたシンク。</span><span class="sxs-lookup"><span data-stu-id="a0823-571">The created sink.</span></span>

<span data-ttu-id="a0823-572">**PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System.string, PerceptionSimulation.. ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="a0823-572">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="a0823-573">指定されたファイルから記録を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="a0823-573">Load a recording from the specified file.</span></span>

<span data-ttu-id="a0823-574">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0823-574">Parameters</span></span>
* <span data-ttu-id="a0823-575">path-読み込むファイルのパス。</span><span class="sxs-lookup"><span data-stu-id="a0823-575">path - The path of the file to load.</span></span>
* <span data-ttu-id="a0823-576">factory-必要なときに ISimulationStreamSink を作成するために記録によって使用されるファクトリ。</span><span class="sxs-lookup"><span data-stu-id="a0823-576">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="a0823-577">戻り値</span><span class="sxs-lookup"><span data-stu-id="a0823-577">Return value</span></span>

<span data-ttu-id="a0823-578">読み込まれた記録。</span><span class="sxs-lookup"><span data-stu-id="a0823-578">The loaded recording.</span></span>

<span data-ttu-id="a0823-579">**PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System.string, PerceptionSimulation ISimulationStreamSinkFactory, PerceptionSimulation. ISimulationRecordingCallback..)**</span><span class="sxs-lookup"><span data-stu-id="a0823-579">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="a0823-580">指定されたファイルから記録を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="a0823-580">Load a recording from the specified file.</span></span>

<span data-ttu-id="a0823-581">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0823-581">Parameters</span></span>
* <span data-ttu-id="a0823-582">path-読み込むファイルのパス。</span><span class="sxs-lookup"><span data-stu-id="a0823-582">path - The path of the file to load.</span></span>
* <span data-ttu-id="a0823-583">factory-必要なときに ISimulationStreamSink を作成するために記録によって使用されるファクトリ。</span><span class="sxs-lookup"><span data-stu-id="a0823-583">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="a0823-584">callback-更新を受け取るコールバック。これにより、記録の状態が再適用されます。</span><span class="sxs-lookup"><span data-stu-id="a0823-584">callback - A callback, which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="a0823-585">戻り値</span><span class="sxs-lookup"><span data-stu-id="a0823-585">Return value</span></span>

<span data-ttu-id="a0823-586">読み込まれた記録。</span><span class="sxs-lookup"><span data-stu-id="a0823-586">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="a0823-587">PerceptionSimulation データ型</span><span class="sxs-lookup"><span data-stu-id="a0823-587">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="a0823-588">さまざまな種類のストリームデータについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a0823-588">Describes the different types of stream data.</span></span>

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

<span data-ttu-id="a0823-589">**PerceptionSimulation のデータ型はありません。**</span><span class="sxs-lookup"><span data-stu-id="a0823-589">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="a0823-590">ストリームデータ型がないことを示すために使用される sentinel 値。</span><span class="sxs-lookup"><span data-stu-id="a0823-590">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="a0823-591">**PerceptionSimulation のデータ型**</span><span class="sxs-lookup"><span data-stu-id="a0823-591">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="a0823-592">ヘッドの位置と向きに関するデータのストリーム。</span><span class="sxs-lookup"><span data-stu-id="a0823-592">Stream of data for the position and orientation of the head.</span></span>

<span data-ttu-id="a0823-593">**PerceptionSimulation のデータ型**</span><span class="sxs-lookup"><span data-stu-id="a0823-593">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="a0823-594">ハンドの位置とジェスチャのデータのストリーム。</span><span class="sxs-lookup"><span data-stu-id="a0823-594">Stream of data for the position and gestures of hands.</span></span>

<span data-ttu-id="a0823-595">**PerceptionSimulation. SpatialMapping.**</span><span class="sxs-lookup"><span data-stu-id="a0823-595">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="a0823-596">環境の空間マッピングのデータのストリーム。</span><span class="sxs-lookup"><span data-stu-id="a0823-596">Stream of data for spatial mapping of the environment.</span></span>

<span data-ttu-id="a0823-597">**PerceptionSimulation のデータ型**</span><span class="sxs-lookup"><span data-stu-id="a0823-597">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="a0823-598">デバイスを調整するためのデータのストリーム。</span><span class="sxs-lookup"><span data-stu-id="a0823-598">Stream of data for calibration of the device.</span></span> <span data-ttu-id="a0823-599">調整パケットは、リモートモードのシステムでのみ受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="a0823-599">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="a0823-600">**PerceptionSimulation のデータ型**</span><span class="sxs-lookup"><span data-stu-id="a0823-600">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="a0823-601">デバイスの環境のデータストリーム。</span><span class="sxs-lookup"><span data-stu-id="a0823-601">Stream of data for the environment of the device.</span></span>

<span data-ttu-id="a0823-602">**PerceptionSimulation. SixDofControllers.**</span><span class="sxs-lookup"><span data-stu-id="a0823-602">**Microsoft.PerceptionSimulation.StreamDataTypes.SixDofControllers**</span></span>

<span data-ttu-id="a0823-603">モーションコントローラーのデータストリーム。</span><span class="sxs-lookup"><span data-stu-id="a0823-603">Stream of data for motion controllers.</span></span>

<span data-ttu-id="a0823-604">**PerceptionSimulation のデータ型**</span><span class="sxs-lookup"><span data-stu-id="a0823-604">**Microsoft.PerceptionSimulation.StreamDataTypes.Eyes**</span></span>

<span data-ttu-id="a0823-605">シミュレートされた人間の目を持つデータのストリーム。</span><span class="sxs-lookup"><span data-stu-id="a0823-605">Stream of data with the eyes of the simulated human.</span></span>

<span data-ttu-id="a0823-606">**PerceptionSimulation を構成します。**</span><span class="sxs-lookup"><span data-stu-id="a0823-606">**Microsoft.PerceptionSimulation.StreamDataTypes.DisplayConfiguration**</span></span>

<span data-ttu-id="a0823-607">デバイスのディスプレイ構成を使用したデータのストリーム。</span><span class="sxs-lookup"><span data-stu-id="a0823-607">Stream of data with the display configuration of the device.</span></span>

<span data-ttu-id="a0823-608">**PerceptionSimulation のデータ型**</span><span class="sxs-lookup"><span data-stu-id="a0823-608">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="a0823-609">すべての記録されたデータ型を示すために使用される sentinel 値。</span><span class="sxs-lookup"><span data-stu-id="a0823-609">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="a0823-610">PerceptionSimulation. ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="a0823-610">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="a0823-611">シミュレーションストリームからデータパケットを受信するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a0823-611">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="a0823-612">**PerceptionSimulation. ISimulationStreamSink (uint length, byte [] パケット数)**</span><span class="sxs-lookup"><span data-stu-id="a0823-612">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="a0823-613">内部的に型指定され、バージョン管理される1つのパケットを受信します。</span><span class="sxs-lookup"><span data-stu-id="a0823-613">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="a0823-614">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0823-614">Parameters</span></span>
* <span data-ttu-id="a0823-615">length-パケットの長さ。</span><span class="sxs-lookup"><span data-stu-id="a0823-615">length - The length of the packet.</span></span>
* <span data-ttu-id="a0823-616">パケット-パケットのデータ。</span><span class="sxs-lookup"><span data-stu-id="a0823-616">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="a0823-617">PerceptionSimulation. ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="a0823-617">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="a0823-618">ISimulationStreamSink を作成するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a0823-618">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="a0823-619">**PerceptionSimulation. ISimulationStreamSinkFactory-Ationstreamsink ()**</span><span class="sxs-lookup"><span data-stu-id="a0823-619">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="a0823-620">ISimulationStreamSink の1つのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="a0823-620">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="a0823-621">戻り値</span><span class="sxs-lookup"><span data-stu-id="a0823-621">Return value</span></span>

<span data-ttu-id="a0823-622">作成されたシンク。</span><span class="sxs-lookup"><span data-stu-id="a0823-622">The created sink.</span></span>
