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
# <a name="perception-simulation"></a><span data-ttu-id="fd0a1-104">認識シミュレーション</span><span class="sxs-lookup"><span data-stu-id="fd0a1-104">Perception simulation</span></span>

<span data-ttu-id="fd0a1-105">アプリの自動テストをビルドしますか?</span><span class="sxs-lookup"><span data-stu-id="fd0a1-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="fd0a1-106">テストをコンポーネントレベルの単体テストよりも先に実行し、アプリをエンドツーエンドで実際に練習しますか。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="fd0a1-107">認識シミュレーションは、探しているものです。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="fd0a1-108">認識シミュレーションライブラリは、アプリに人間と世界の入力データを送信して、テストを自動化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="fd0a1-109">たとえば、特定の反復可能な位置に対する人間の入力をシミュレートし、ジェスチャを実行したり、モーションコントローラーを使用したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="fd0a1-110">認識シミュレーションでは、このようなシミュレートされた入力を物理 HoloLens、HoloLens エミュレーター (第1世代)、HoloLens 2 エミュレーター、または Mixed Reality ポータルがインストールされている PC に送信できます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="fd0a1-111">認識シミュレーションは、混合の現実のデバイスでライブセンサーをバイパスし、デバイスで実行されているアプリケーションにシミュレートされた入力を送信します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="fd0a1-112">アプリケーションでは、これらの入力イベントを、常に使用するものと同じ Api を使用して受信します。また、実際のセンサーでの実行と知覚シミュレーションでの実行の違いを示すことはできません。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="fd0a1-113">認識シミュレーションは、シミュレートされた入力を HoloLens 仮想マシンに送信するために HoloLens エミュレーターで使用されるものと同じテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="fd0a1-114">コードでのシミュレーションの使用を開始するには、まず IPerceptionSimulationManager オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="fd0a1-115">そのオブジェクトから、コマンドを発行して、"人間" のようなシミュレートされた "ユーザー" のプロパティを制御することができます。これには、head 位置、針、ジェスチャなどがあります。また、モーションコントローラーを有効にしたり操作したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="fd0a1-116">認識シミュレーションのための Visual Studio プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="fd0a1-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="fd0a1-117">開発用 PC に[HoloLens エミュレーターをインストール](../install-the-tools.md)します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-117">[Install the HoloLens emulator](../install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="fd0a1-118">エミュレーターには、認識シミュレーションに使用するライブラリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="fd0a1-119">新しい Visual Studio C# デスクトッププロジェクトを作成します (コンソールプロジェクトは、開始するのに適しています)。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="fd0a1-120">次のバイナリを参照としてプロジェクトに追加します (プロジェクト >追加 >参照...)。これらは、 \\ HoloLens 2 エミュレーターの% **ProgramFiles (x86)% \ MICROSOFT xde \\ 10.0.18362.0** など、% ProgramFiles (X86)% \ microsoft xde (バージョン) で見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="fd0a1-121">(注: バイナリは HoloLens 2 エミュレーターに含まれていますが、デスクトップ上の Windows Mixed Reality でも機能します)。ある.</span><span class="sxs-lookup"><span data-stu-id="fd0a1-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="fd0a1-122">認識シミュレーション用の PerceptionSimulationManager.Interop.dll マネージ C# ラッパー。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="fd0a1-123">b.</span><span class="sxs-lookup"><span data-stu-id="fd0a1-123">b.</span></span> <span data-ttu-id="fd0a1-124">PerceptionSimulationRest.dll-HoloLens またはエミュレーターに対する web ソケット通信チャネルを設定するためのライブラリです。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="fd0a1-125">c.</span><span class="sxs-lookup"><span data-stu-id="fd0a1-125">c.</span></span> <span data-ttu-id="fd0a1-126">シミュレーション用の SimulationStream.Interop.dll 共有型。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="fd0a1-127">実装バイナリ PerceptionSimulationManager.dll をプロジェクト a に追加します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="fd0a1-128">まず、これをバイナリとしてプロジェクトに追加します (プロジェクト >追加 >既存の項目...)。プロジェクトソースフォルダーにコピーしないように、リンクとして保存します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="fd0a1-129">![PerceptionSimulationManager.dll をリンク b としてプロジェクトに追加し ](images/saveaslink.png) ます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="fd0a1-130">次に、ビルド時に出力フォルダーにコピーされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="fd0a1-131">これは、バイナリのプロパティシートにあります。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="fd0a1-132">![出力ディレクトリにコピーする PerceptionSimulationManager.dll をマークします](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="fd0a1-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="fd0a1-133">アクティブソリューションプラットフォームを x64 に設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="fd0a1-134">(Configuration Manager を使用して、x64 用のプラットフォームエントリがまだ存在しない場合は作成します)。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="fd0a1-135">IPerceptionSimulation Manager オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="fd0a1-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="fd0a1-136">シミュレーションを制御するには、IPerceptionSimulationManager オブジェクトから取得したオブジェクトに更新を発行します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="fd0a1-137">最初の手順では、そのオブジェクトを取得し、ターゲットデバイスまたはエミュレーターに接続します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="fd0a1-138">エミュレーターの IP アドレスを取得するには、[ツールバー](using-the-hololens-emulator.md)の [デバイスポータル] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="fd0a1-139">![デバイスポータルを開くアイコン開いている ](images/emulator-deviceportal.png) **デバイスポータル** : エミュレーターで HoloLens OS の Windows デバイスポータルを開きます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal** : Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="fd0a1-140">Windows Mixed Reality の場合、この設定は、[デバイスポータルを有効にする] の下にある [Connect & Security] (セキュリティの更新) の下にある [設定] アプリで取得できます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="fd0a1-141">IP アドレスとポートの両方に注意してください。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="fd0a1-142">まず、RestSimulationStreamSink を呼び出して、RestSimulationStreamSink オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="fd0a1-143">これは、http 接続を介して制御するターゲットデバイスまたはエミュレーターです。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="fd0a1-144">コマンドは、デバイスまたはエミュレーターで実行されている [Windows デバイスポータル](using-the-windows-device-portal.md) に渡され、処理されます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="fd0a1-145">オブジェクトを作成するには、次の4つのパラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="fd0a1-146">Uri uri-ターゲットデバイスの IP アドレス (例: " https://123.123.123.123 " または " https://123.123.123.123:50080 ")</span><span class="sxs-lookup"><span data-stu-id="fd0a1-146">Uri uri - IP address of the target device (e.g., "https://123.123.123.123" or "https://123.123.123.123:50080")</span></span>
* <span data-ttu-id="fd0a1-147">System .Net. NetworkCredential 資格情報-ターゲットデバイスまたはエミュレーターで [Windows デバイスポータル](using-the-windows-device-portal.md) に接続するためのユーザー名/パスワード。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="fd0a1-148">ローカルアドレスを使用してエミュレーターに接続している場合 (例: 168 *...* \*) 同じ PC で、すべての資格情報が受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-148">If you are connecting to the emulator via its local address (e.g., 168. *.* .\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="fd0a1-149">bool normal-通常の優先度の場合は True、低優先度の場合は false。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="fd0a1-150">テストシナリオでは、通常、これを *true* に設定して、テストで制御を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="fd0a1-151">エミュレーターと Windows Mixed Reality のシミュレーションでは、優先度の低い接続を使用します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="fd0a1-152">テストで優先度の低い接続も使用している場合は、最後に確立された接続が制御されます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="fd0a1-153">CancellationToken は、非同期操作を取り消すためのトークンです。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="fd0a1-154">次に、IPerceptionSimulationManager を作成します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="fd0a1-155">これは、シミュレーションの制御に使用するオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="fd0a1-156">これは、非同期メソッドでも実行する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="fd0a1-157">シミュレートされた人間を制御する</span><span class="sxs-lookup"><span data-stu-id="fd0a1-157">Control the simulated Human</span></span>

<span data-ttu-id="fd0a1-158">IPerceptionSimulationManager には、ISimulatedHuman オブジェクトを返すヒューマンプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="fd0a1-159">シミュレートされた人間を制御するには、このオブジェクトに対して操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="fd0a1-160">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="fd0a1-161">C# コンソールアプリケーションの基本的なサンプル</span><span class="sxs-lookup"><span data-stu-id="fd0a1-161">Basic Sample C# console application</span></span>

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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="fd0a1-162">拡張サンプル C# コンソールアプリケーション</span><span class="sxs-lookup"><span data-stu-id="fd0a1-162">Extended Sample C# console application</span></span>

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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="fd0a1-163">6つの自由度コントローラーに関する注意</span><span class="sxs-lookup"><span data-stu-id="fd0a1-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="fd0a1-164">シミュレートされた6つの自由コントローラーでメソッドのプロパティを呼び出す前に、コントローラーをアクティブにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="fd0a1-165">そうしないと、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="fd0a1-166">Windows 10 2019 年5月の更新プログラムでは、ISimulatedSixDofController オブジェクトの Status プロパティを SimulatedSixDofControllerStatus に設定することにより、シミュレートされた6つの自由度コントローラーをインストールしてアクティブ化することができます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="fd0a1-167">Windows 10 10 月2018更新プログラムおよびそれ以前のバージョンでは、\Windows\System32 フォルダーにある PerceptionSimulationDevice ツールを呼び出して、シミュレートされた6自由コントローラーを最初に個別にインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="fd0a1-168">このツールの使用方法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="fd0a1-169">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="fd0a1-170">サポートされているアクションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-170">Supported actions are:</span></span>
* <span data-ttu-id="fd0a1-171">i = インストール</span><span class="sxs-lookup"><span data-stu-id="fd0a1-171">i = install</span></span>
* <span data-ttu-id="fd0a1-172">q = クエリ</span><span class="sxs-lookup"><span data-stu-id="fd0a1-172">q = query</span></span>
* <span data-ttu-id="fd0a1-173">r = 削除</span><span class="sxs-lookup"><span data-stu-id="fd0a1-173">r = remove</span></span>

<span data-ttu-id="fd0a1-174">サポートされているインスタンスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-174">Supported instances are:</span></span>
* <span data-ttu-id="fd0a1-175">1 = 左6自由コントローラー</span><span class="sxs-lookup"><span data-stu-id="fd0a1-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="fd0a1-176">2 = 右6自由コントローラー</span><span class="sxs-lookup"><span data-stu-id="fd0a1-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="fd0a1-177">プロセスの終了コードは、成功 (ゼロの戻り値) または失敗 (0 以外の戻り値) を示します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="fd0a1-178">' Q ' アクションを使用してコントローラーがインストールされているかどうかを照会する場合、コントローラーがまだインストールされていない場合は戻り値が0になり、コントローラーがインストールされている場合は1が返されます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="fd0a1-179">Windows 10 10 月2018更新プログラムまたはそれ以前のバージョンでコントローラーを削除する場合は、最初に API を使用して状態を Off に設定してから、PerceptionSimulationDevice ツールを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="fd0a1-180">このツールは管理者として実行する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="fd0a1-181">API リファレンス</span><span class="sxs-lookup"><span data-stu-id="fd0a1-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="fd0a1-182">PerceptionSimulation. SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="fd0a1-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="fd0a1-183">シミュレートされたデバイスの種類について説明します</span><span class="sxs-lookup"><span data-stu-id="fd0a1-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="fd0a1-184">**PerceptionSimulation. SimulatedDeviceType**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="fd0a1-185">架空の参照デバイス (PerceptionSimulationManager の既定値)</span><span class="sxs-lookup"><span data-stu-id="fd0a1-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="fd0a1-186">PerceptionSimulation... Trackermode</span><span class="sxs-lookup"><span data-stu-id="fd0a1-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="fd0a1-187">ヘッドトラッカーモードについて説明します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="fd0a1-188">**PerceptionSimulation。既定値の場合**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="fd0a1-189">既定のヘッド追跡。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-189">Default Head Tracking.</span></span> <span data-ttu-id="fd0a1-190">これは、システムが実行時の状況に基づいて最適なヘッド追跡モードを選択することを意味します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="fd0a1-191">**PerceptionSimulation のようになります。**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="fd0a1-192">方向のみのヘッド追跡。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="fd0a1-193">これは、追跡される位置が信頼できない可能性があり、head 位置に依存する一部の機能が使用できない場合があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="fd0a1-194">**PerceptionSimulation を移動します。**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="fd0a1-195">位置指定のヘッド追跡。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-195">Positional Head Tracking.</span></span> <span data-ttu-id="fd0a1-196">これは、追跡されるヘッドの位置と向きは両方とも信頼できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="fd0a1-197">PerceptionSimulation. SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="fd0a1-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="fd0a1-198">シミュレートされたジェスチャについて説明します</span><span class="sxs-lookup"><span data-stu-id="fd0a1-198">Describes a simulated gesture</span></span>

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

<span data-ttu-id="fd0a1-199">**PerceptionSimulation. SimulatedGesture**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="fd0a1-200">ジェスチャがないことを示すために使用される sentinel 値。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="fd0a1-201">**PerceptionSimulation. SimulatedGesture. FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="fd0a1-202">指押下ジェスチャ。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-202">A finger pressed gesture.</span></span>

<span data-ttu-id="fd0a1-203">**PerceptionSimulation. SimulatedGesture. FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="fd0a1-204">指で離されたジェスチャ。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-204">A finger released gesture.</span></span>

<span data-ttu-id="fd0a1-205">**PerceptionSimulation. SimulatedGesture**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="fd0a1-206">ホーム/システムジェスチャ。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-206">The home/system gesture.</span></span>

<span data-ttu-id="fd0a1-207">**PerceptionSimulation. SimulatedGesture**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="fd0a1-208">有効なジェスチャの最大数。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="fd0a1-209">PerceptionSimulation. SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="fd0a1-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="fd0a1-210">シミュレートされた6自由コントローラーの可能性のある状態。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="fd0a1-211">**PerceptionSimulation. SimulatedSixDofControllerStatus**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="fd0a1-212">6自由コントローラーがオフになっています。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="fd0a1-213">**PerceptionSimulation. SimulatedSixDofControllerStatus**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="fd0a1-214">6自由コントローラーが有効になり、追跡されます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="fd0a1-215">**PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="fd0a1-216">6自由度コントローラーはオンになっていますが、追跡することはできません。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="fd0a1-217">PerceptionSimulation. SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="fd0a1-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="fd0a1-218">シミュレートされた6自由コントローラーでサポートされるボタン。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-218">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="fd0a1-219">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="fd0a1-220">ボタンを指定するために使用される sentinel 値。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="fd0a1-221">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="fd0a1-222">[ホーム] ボタンが押された状態になります。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-222">The Home button is pressed.</span></span>

<span data-ttu-id="fd0a1-223">**PerceptionSimulation. SimulatedSixDofControllerButton. メニュー**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="fd0a1-224">メニューボタンが押された状態になります。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-224">The Menu button is pressed.</span></span>

<span data-ttu-id="fd0a1-225">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="fd0a1-226">グリップボタンが押された状態になります。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-226">The Grip button is pressed.</span></span>

<span data-ttu-id="fd0a1-227">**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="fd0a1-228">タッチパッドが押された状態になります。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="fd0a1-229">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="fd0a1-230">[選択] ボタンが押された状態になります。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-230">The Select button is pressed.</span></span>

<span data-ttu-id="fd0a1-231">**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="fd0a1-232">タッチパッドがタッチされます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-232">The TouchPad is touched.</span></span>

<span data-ttu-id="fd0a1-233">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="fd0a1-234">サムスティックが押されています。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="fd0a1-235">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="fd0a1-236">最大有効なボタン。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="fd0a1-237">PerceptionSimulation. SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="fd0a1-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="fd0a1-238">シミュレートされた目の調整状態</span><span class="sxs-lookup"><span data-stu-id="fd0a1-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="fd0a1-239">**PerceptionSimulation. SimulatedEyesCalibrationState.**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="fd0a1-240">目の調整は使用できません。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="fd0a1-241">**PerceptionSimulation. SimulatedEyesCalibrationState**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="fd0a1-242">目が調整されました。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="fd0a1-243">これが既定値です。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-243">This is the default value.</span></span>

<span data-ttu-id="fd0a1-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configpostman**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="fd0a1-245">目が調整されています。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="fd0a1-246">**PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="fd0a1-247">目を調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="fd0a1-248">PerceptionSimulation. SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="fd0a1-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="fd0a1-249">手の継手の追跡精度。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="fd0a1-250">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy.**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="fd0a1-251">ジョイントは追跡されません。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-251">The joint is not tracked.</span></span>

<span data-ttu-id="fd0a1-252">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="fd0a1-253">ジョイント位置が推論されます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-253">The joint position is inferred.</span></span>

<span data-ttu-id="fd0a1-254">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="fd0a1-255">ジョイントは完全に追跡されます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="fd0a1-256">PerceptionSimulation. SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="fd0a1-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="fd0a1-257">手の継手の追跡精度。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-257">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="fd0a1-258">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="fd0a1-259">ハンドの指継手は、終了したポーズを反映するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="fd0a1-260">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="fd0a1-261">手の指継手は、オープンなポーズを反映するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="fd0a1-262">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="fd0a1-263">ハンドの指継手は、ポイントのポーズを反映するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="fd0a1-264">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="fd0a1-265">手の指継手は、ピンチのポーズを反映するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="fd0a1-266">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="fd0a1-267">SimulatedHandPose の最大有効値。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="fd0a1-268">PerceptionSimulation の状態</span><span class="sxs-lookup"><span data-stu-id="fd0a1-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="fd0a1-269">再生の状態を記述します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="fd0a1-270">**PerceptionSimulation が停止しました。**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="fd0a1-271">記録は現在停止しており、再生の準備ができています。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="fd0a1-272">**PerceptionSimulation を再生します。**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="fd0a1-273">記録は現在再生中です。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-273">The recording is currently playing.</span></span>

<span data-ttu-id="fd0a1-274">**PerceptionSimulation が一時停止しました。**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="fd0a1-275">記録は現在一時停止されています。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-275">The recording is currently paused.</span></span>

<span data-ttu-id="fd0a1-276">**PerceptionSimulation を終了します。**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="fd0a1-277">記録が最後に達しました。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="fd0a1-278">PerceptionSimulation. Vector3</span><span class="sxs-lookup"><span data-stu-id="fd0a1-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="fd0a1-279">3D 空間の点またはベクターを表す3つのコンポーネントベクターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="fd0a1-280">**PerceptionSimulation. Vector3**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="fd0a1-281">ベクトルの X 成分。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-281">The X component of the vector.</span></span>

<span data-ttu-id="fd0a1-282">**PerceptionSimulation. Vector3**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="fd0a1-283">ベクトルの Y 成分。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-283">The Y component of the vector.</span></span>

<span data-ttu-id="fd0a1-284">**PerceptionSimulation. Vector3**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="fd0a1-285">ベクトルの Z 成分。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-285">The Z component of the vector.</span></span>

<span data-ttu-id="fd0a1-286">**#Ctor PerceptionSimulation (system.string、system.string、system.string) を (system.string) します。**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="fd0a1-287">新しい Vector3 を構築します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-287">Construct a new Vector3.</span></span>

<span data-ttu-id="fd0a1-288">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0a1-288">Parameters</span></span>
* <span data-ttu-id="fd0a1-289">x-ベクトルの x 成分。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="fd0a1-290">y-ベクトルの y 成分。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="fd0a1-291">z-ベクトルの z 成分。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="fd0a1-292">PerceptionSimulation. Rotation3</span><span class="sxs-lookup"><span data-stu-id="fd0a1-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="fd0a1-293">3つのコンポーネントのローテーションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="fd0a1-294">**PerceptionSimulation. Rotation3**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="fd0a1-295">X 軸を中心とする回転のピッチ成分。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="fd0a1-296">**PerceptionSimulation. Rotation3**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="fd0a1-297">Y 軸を中心とする回転のヨー要素。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="fd0a1-298">**PerceptionSimulation. Rotation3**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="fd0a1-299">Z 軸を中心とする回転のロールコンポーネント。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="fd0a1-300">**#Ctor PerceptionSimulation (system.string、system.string、system.string) を (system.string) します。**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="fd0a1-301">新しい Rotation3 を構築します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="fd0a1-302">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0a1-302">Parameters</span></span>
* <span data-ttu-id="fd0a1-303">ピッチ-回転のピッチ成分。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="fd0a1-304">ヨー-回転のヨーコンポーネント。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="fd0a1-305">roll-回転のロールコンポーネント。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="fd0a1-306">PerceptionSimulation. SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="fd0a1-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="fd0a1-307">シミュレートされたハンドでのジョイントの構成について説明します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="fd0a1-308">**PerceptionSimulation. SimulatedHandJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="fd0a1-309">ジョイントの位置。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-309">The position of the joint.</span></span>

<span data-ttu-id="fd0a1-310">**PerceptionSimulation. SimulatedHandJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="fd0a1-311">ジョイントの回転。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-311">The rotation of the joint.</span></span>

<span data-ttu-id="fd0a1-312">**PerceptionSimulation. SimulatedHandJointConfiguration の精度**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="fd0a1-313">ジョイントの追跡精度。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="fd0a1-314">PerceptionSimulation</span><span class="sxs-lookup"><span data-stu-id="fd0a1-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="fd0a1-315">カメラで一般的に使用される、視錐のビューについて説明します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="fd0a1-316">**PerceptionSimulation。 Near**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="fd0a1-317">視錐に含まれる最小距離。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="fd0a1-318">**PerceptionSimulation です。**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="fd0a1-319">視錐に含まれる最大距離。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="fd0a1-320">**PerceptionSimulation. FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="fd0a1-321">視錐のビューの水平方向のフィールド (π未満のラジアン)。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="fd0a1-322">**PerceptionSimulation. AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="fd0a1-323">ビューの垂直方向のフィールドから、ビューの垂直方向のフィールドまでの比率。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a><span data-ttu-id="fd0a1-324">PerceptionSimulation. SimulatedDisplayConfiguration</span><span class="sxs-lookup"><span data-stu-id="fd0a1-324">Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration</span></span>

<span data-ttu-id="fd0a1-325">シミュレートされたヘッドセットの表示の構成について説明します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-325">Describes the configuration of the simulated headset's display.</span></span>

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

<span data-ttu-id="fd0a1-326">**PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyePosition**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-326">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyePosition**</span></span>

<span data-ttu-id="fd0a1-327">ステレオレンダリングの目的で、ヘッドの中心から左目への変換。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-327">The transform from the center of the head to the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="fd0a1-328">**PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-328">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyeRotation**</span></span>

<span data-ttu-id="fd0a1-329">ステレオレンダリングの目的での左目の回転。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-329">The rotation of the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="fd0a1-330">**PerceptionSimulation. SimulatedDisplayConfiguration. RightEyePosition**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-330">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyePosition**</span></span>

<span data-ttu-id="fd0a1-331">ステレオレンダリングの目的で、ヘッドの中心から右目への変換。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-331">The transform from the center of the head to the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="fd0a1-332">**PerceptionSimulation. SimulatedDisplayConfiguration. RightEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-332">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyeRotation**</span></span>

<span data-ttu-id="fd0a1-333">ステレオレンダリングの目的での右目の回転。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-333">The rotation of the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="fd0a1-334">**PerceptionSimulation. SimulatedDisplayConfiguration. Ipd**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-334">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.Ipd**</span></span>

<span data-ttu-id="fd0a1-335">ステレオレンダリングのためにシステムによって報告された Ipd 値。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-335">The Ipd value reported by the system for purposes of stereo rendering.</span></span>

<span data-ttu-id="fd0a1-336">**PerceptionSimulation. SimulatedDisplayConfiguration (変換)**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-336">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyEyeTransforms**</span></span>

<span data-ttu-id="fd0a1-337">左辺と右辺の変換に指定された値が有効であると見なされ、実行中のシステムに適用されるかどうか。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-337">Whether or not the values provided for left and right eye transforms should be considered valid and applied to the running system.</span></span>

<span data-ttu-id="fd0a1-338">**PerceptionSimulation. SimulatedDisplayConfiguration. ApplyIpd**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-338">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyIpd**</span></span>

<span data-ttu-id="fd0a1-339">Ipd に指定された値が有効であると見なされ、実行中のシステムに適用されるかどうか。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-339">Whether or not the value provided for Ipd should be considered valid and applied to the running system.</span></span>


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="fd0a1-340">PerceptionSimulation. IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="fd0a1-340">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="fd0a1-341">デバイスの制御に使用されるパケットを生成するためのルート。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-341">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="fd0a1-342">**PerceptionSimulation. IPerceptionSimulationManager**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-342">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="fd0a1-343">シミュレートされた人間とシミュレートされた世界を解釈する、シミュレートされたデバイスオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-343">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="fd0a1-344">**PerceptionSimulation. IPerceptionSimulationManager**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-344">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="fd0a1-345">シミュレートされた人間を制御するオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-345">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="fd0a1-346">**PerceptionSimulation. IPerceptionSimulationManager**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-346">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="fd0a1-347">シミュレーションを既定の状態にリセットします。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-347">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="fd0a1-348">PerceptionSimulation. ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="fd0a1-348">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="fd0a1-349">シミュレートされた世界とシミュレートされた人間を解釈するデバイスを記述するインターフェイス</span><span class="sxs-lookup"><span data-stu-id="fd0a1-349">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="fd0a1-350">**PerceptionSimulation. ISimulatedDevice Tracker**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-350">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="fd0a1-351">シミュレートされたデバイスからヘッドトラッカーを取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-351">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="fd0a1-352">**PerceptionSimulation. ISimulatedDevice Tracker**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-352">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="fd0a1-353">シミュレートされたデバイスからハンドトラッカーを取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-353">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="fd0a1-354">**PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType (PerceptionSimulation. SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-354">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="fd0a1-355">シミュレートされたデバイスのプロパティを、指定したデバイスの種類に合わせて設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-355">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="fd0a1-356">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0a1-356">Parameters</span></span>
* <span data-ttu-id="fd0a1-357">type-シミュレートされたデバイスの新しい種類</span><span class="sxs-lookup"><span data-stu-id="fd0a1-357">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice2"></a><span data-ttu-id="fd0a1-358">PerceptionSimulation. ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="fd0a1-358">Microsoft.PerceptionSimulation.ISimulatedDevice2</span></span>

<span data-ttu-id="fd0a1-359">ISimulatedDevice を ISimulatedDevice2 にキャストすると、追加のプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-359">Additional properties are available by casting the ISimulatedDevice to ISimulatedDevice2</span></span>

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

<span data-ttu-id="fd0a1-360">**PerceptionSimulation. ISimulatedDevice2. IsUserPresent**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-360">**Microsoft.PerceptionSimulation.ISimulatedDevice2.IsUserPresent**</span></span>

<span data-ttu-id="fd0a1-361">シミュレートされた人間がヘッドセットをアクティブに装着しているかどうかを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-361">Retrieve or set whether or not the simulated human is actively wearing the headset.</span></span>

<span data-ttu-id="fd0a1-362">**PerceptionSimulation. ISimulatedDevice2. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-362">**Microsoft.PerceptionSimulation.ISimulatedDevice2.DisplayConfiguration**</span></span>

<span data-ttu-id="fd0a1-363">シミュレートされた表示のプロパティを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-363">Retrieve or set the properties of the simulated display.</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="fd0a1-364">PerceptionSimulation. ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="fd0a1-364">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="fd0a1-365">シミュレートされた人間の頭を追跡する、シミュレートされたデバイスの部分を説明するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-365">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="fd0a1-366">**PerceptionSimulation. ISimulatedHeadTracker.-Trackermode**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-366">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="fd0a1-367">現在のヘッドトラッカーモードを取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-367">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="fd0a1-368">PerceptionSimulation. ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="fd0a1-368">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="fd0a1-369">シミュレートされた人間の手を追跡するシミュレートされたデバイスの部分を説明するインターフェイス</span><span class="sxs-lookup"><span data-stu-id="fd0a1-369">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="fd0a1-370">**PerceptionSimulation. ISimulatedHandTracker. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-370">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="fd0a1-371">世界のリレーションを使用してノードの位置をメートル単位で取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-371">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="fd0a1-372">**PerceptionSimulation. ISimulatedHandTracker**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-372">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="fd0a1-373">頭の中心を基準とした、シミュレートされたハンドトラッカーの位置を取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-373">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="fd0a1-374">**PerceptionSimulation. ISimulatedHandTracker**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-374">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="fd0a1-375">シミュレートされたハンドトラッカーの下向きのピッチを取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-375">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="fd0a1-376">**PerceptionSimulation は無視されました。**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-376">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="fd0a1-377">シミュレートされたハンドトラッカーを無視するかどうかを取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-377">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="fd0a1-378">無視すると、両方のハンドが常に表示されます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-378">When ignored, both hands are always visible.</span></span> <span data-ttu-id="fd0a1-379">無視しない場合 (既定)、ハンドトラッカーの視錐の内側にいる場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-379">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="fd0a1-380">**PerceptionSimulation. ISimulatedHandTracker**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-380">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="fd0a1-381">ハンドがシミュレートされたハンドトラッカーに表示されるかどうかを判断するために使用する、視錐のプロパティを取得および設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-381">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="fd0a1-382">PerceptionSimulation. ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="fd0a1-382">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="fd0a1-383">シミュレートされた人間を制御する最上位のインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-383">Top level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="fd0a1-384">**PerceptionSimulation. ISimulatedHuman. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-384">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="fd0a1-385">世界中のノードの位置をメートル単位で取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-385">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="fd0a1-386">この位置は、人間のフィートの中央の点に対応しています。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-386">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="fd0a1-387">**PerceptionSimulation. ISimulatedHuman**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-387">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="fd0a1-388">世界中のシミュレートされた人間の顔の方向を取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-388">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="fd0a1-389">0ラジアンは負の Z 軸を中心にします。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-389">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="fd0a1-390">正のラジアンは、Y 軸について時計回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-390">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="fd0a1-391">**PerceptionSimulation. ISimulatedHuman**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-391">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="fd0a1-392">シミュレートされた人間の高さをメートル単位で取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-392">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="fd0a1-393">**PerceptionSimulation. ISimulatedHuman. LeftHand**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-393">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="fd0a1-394">シミュレートされた人間の左側を取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-394">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="fd0a1-395">**PerceptionSimulation. ISimulatedHuman. 右**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-395">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="fd0a1-396">シミュレートされた人間の右側を取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-396">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="fd0a1-397">**PerceptionSimulation. ISimulatedHuman**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-397">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="fd0a1-398">シミュレートされた人間の先頭を取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-398">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="fd0a1-399">**PerceptionSimulation (ISimulatedHuman) (PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-399">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="fd0a1-400">シミュレートされた人間を、現在の位置を基準としてメートル単位で移動します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-400">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="fd0a1-401">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0a1-401">Parameters</span></span>
* <span data-ttu-id="fd0a1-402">translation-現在の位置を基準とした、移動する平行移動。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-402">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="fd0a1-403">**PerceptionSimulation. ISimulatedHuman (System. Single)**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-403">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="fd0a1-404">現在の方向を基準にして、シミュレートされた人間を Y 軸に対して時計回りに回転させます</span><span class="sxs-lookup"><span data-stu-id="fd0a1-404">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="fd0a1-405">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0a1-405">Parameters</span></span>
* <span data-ttu-id="fd0a1-406">ラジアン-Y 軸を中心に回転する量。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-406">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="fd0a1-407">PerceptionSimulation. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="fd0a1-407">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="fd0a1-408">ISimulatedHuman を ISimulatedHuman2 にキャストすると、追加のプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-408">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="fd0a1-409">**PerceptionSimulation. ISimulatedHuman2 Controller**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-409">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="fd0a1-410">左6自由コントローラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-410">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="fd0a1-411">**PerceptionSimulation. ISimulatedHuman2 コントローラー**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-411">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="fd0a1-412">右6自由コントローラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-412">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="fd0a1-413">PerceptionSimulation. ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="fd0a1-413">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="fd0a1-414">シミュレートされた人間の手を記述するインターフェイス</span><span class="sxs-lookup"><span data-stu-id="fd0a1-414">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="fd0a1-415">**PerceptionSimulation. ISimulatedHand. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-415">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="fd0a1-416">世界のリレーションを使用してノードの位置をメートル単位で取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-416">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="fd0a1-417">**PerceptionSimulation. ISimulatedHand**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-417">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="fd0a1-418">人間に対するシミュレートされたハンドの位置をメートル単位で取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-418">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="fd0a1-419">**PerceptionSimulation. ISimulatedHand**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-419">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="fd0a1-420">ハンドが現在アクティブになっているかどうかを取得して設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-420">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="fd0a1-421">**PerceptionSimulation. ISimulatedHand**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-421">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="fd0a1-422">SimulatedDevice に手が現在表示されているかどうかを取得します (この位置が、[ツール] で検出される位置にあるかどうか)。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-422">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="fd0a1-423">\**PerceptionSimulation. ISimulatedHand. Ensurevisible\**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-423">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="fd0a1-424">SimulatedDevice に見えるようにハンドを移動します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-424">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="fd0a1-425">**PerceptionSimulation (ISimulatedHand) (PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-425">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="fd0a1-426">シミュレートされたハンドの位置を、現在の位置を基準としてメートル単位で移動します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-426">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="fd0a1-427">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0a1-427">Parameters</span></span>
* <span data-ttu-id="fd0a1-428">translation-シミュレートされたハンドを変換する量。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-428">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="fd0a1-429">**ISimulatedHand (PerceptionSimulation) () (PerceptionSimulation)**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-429">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="fd0a1-430">シミュレートされたハンドを使用してジェスチャを実行します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-430">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="fd0a1-431">ハンドが有効になっている場合にのみ、システムによって検出されます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-431">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="fd0a1-432">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0a1-432">Parameters</span></span>
* <span data-ttu-id="fd0a1-433">ジェスチャ-実行するジェスチャ。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-433">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="fd0a1-434">PerceptionSimulation. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="fd0a1-434">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="fd0a1-435">ISimulatedHand を ISimulatedHand2 にキャストすると、追加のプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-435">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="fd0a1-436">**PerceptionSimulation. ISimulatedHand2**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-436">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="fd0a1-437">シミュレートされたハンドの回転を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-437">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="fd0a1-438">正のラジアンは、軸に沿って表示すると時計回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-438">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="fd0a1-439">PerceptionSimulation. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="fd0a1-439">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="fd0a1-440">ISimulatedHand を ISimulatedHand3 にキャストすると、追加のプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-440">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="fd0a1-441">**PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-441">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="fd0a1-442">指定されたジョイントの共同構成を取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-442">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="fd0a1-443">**PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-443">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="fd0a1-444">指定されたジョイントの結合構成を設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-444">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="fd0a1-445">**PerceptionSimulation. ISimulatedHand3. SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-445">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="fd0a1-446">アニメーション化するオプションのフラグを持つ既知のポーズにハンドを設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-446">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="fd0a1-447">注: アニメーション化によって、最終的な結合構成がすぐに反映されることはありません。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-447">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="fd0a1-448">PerceptionSimulation. ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="fd0a1-448">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="fd0a1-449">シミュレートされた人間の先頭を記述するインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-449">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="fd0a1-450">**PerceptionSimulation. ISimulatedHead. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-450">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="fd0a1-451">世界のリレーションを使用してノードの位置をメートル単位で取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-451">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="fd0a1-452">**PerceptionSimulation. ISimulatedHead**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-452">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="fd0a1-453">シミュレートされたヘッドの回転を取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-453">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="fd0a1-454">正のラジアンは、軸に沿って表示すると時計回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-454">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="fd0a1-455">**PerceptionSimulation. ISimulatedHead**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-455">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="fd0a1-456">シミュレートされたヘッドの直径を取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-456">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="fd0a1-457">この値は、ヘッドの中心 (回転点) を決定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-457">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="fd0a1-458">**PerceptionSimulation (ISimulatedHead) (PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-458">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="fd0a1-459">シミュレートされた頭を現在の回転に対して回転します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-459">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="fd0a1-460">正のラジアンは、軸に沿って表示すると時計回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-460">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="fd0a1-461">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0a1-461">Parameters</span></span>
* <span data-ttu-id="fd0a1-462">rotation-回転する量。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-462">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="fd0a1-463">PerceptionSimulation. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="fd0a1-463">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="fd0a1-464">ISimulatedHead を ISimulatedHead2 にキャストすると、追加のプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-464">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="fd0a1-465">**PerceptionSimulation. ISimulatedHead2**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-465">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="fd0a1-466">シミュレートされた人間の目を取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-466">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="fd0a1-467">PerceptionSimulation. ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="fd0a1-467">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="fd0a1-468">シミュレートされた人間に関連付けられた6自由コントローラーを記述するインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-468">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="fd0a1-469">**PerceptionSimulation. ISimulatedSixDofController. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-469">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="fd0a1-470">世界のリレーションを使用してノードの位置をメートル単位で取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-470">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="fd0a1-471">**PerceptionSimulation. ISimulatedSixDofController**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-471">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="fd0a1-472">コントローラーの現在の状態を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-472">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="fd0a1-473">移動、回転、または押すボタンの呼び出しが成功する前に、コントローラーの状態が Off 以外の値に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-473">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="fd0a1-474">**PerceptionSimulation. ISimulatedSixDofController**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-474">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="fd0a1-475">ユーザーに対してシミュレートされたコントローラーの位置をメートル単位で取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-475">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="fd0a1-476">**PerceptionSimulation. ISimulatedSixDofController**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-476">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="fd0a1-477">シミュレートされたコントローラーの向きを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-477">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="fd0a1-478">**PerceptionSimulation (ISimulatedSixDofController) (PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-478">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="fd0a1-479">シミュレートされたコントローラーの位置を、現在の位置 (メートル単位) に相対的に移動します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-479">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="fd0a1-480">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0a1-480">Parameters</span></span>
* <span data-ttu-id="fd0a1-481">translation-シミュレートされたコントローラーを変換する量。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-481">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="fd0a1-482">**ISimulatedSixDofController (SimulatedSixDofControllerButton) () PerceptionSimulation**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="fd0a1-483">シミュレートされたコントローラーでボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-483">Press a button on the simulated controller.</span></span>  <span data-ttu-id="fd0a1-484">コントローラーが有効になっている場合にのみ、システムによって検出されます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-484">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="fd0a1-485">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0a1-485">Parameters</span></span>
* <span data-ttu-id="fd0a1-486">button-押すボタン。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-486">button - The button to press.</span></span>

<span data-ttu-id="fd0a1-487">**PerceptionSimulation (ISimulatedSixDofController) (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="fd0a1-488">シミュレートされたコントローラーでボタンを離します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-488">Release a button on the simulated controller.</span></span>  <span data-ttu-id="fd0a1-489">コントローラーが有効になっている場合にのみ、システムによって検出されます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-489">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="fd0a1-490">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0a1-490">Parameters</span></span>
* <span data-ttu-id="fd0a1-491">ボタン-リリースするボタン。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-491">button - The button to release.</span></span>

<span data-ttu-id="fd0a1-492">**PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="fd0a1-493">シミュレートされたコントローラーのタッチパッド上でシミュレートされた指の位置を取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-493">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="fd0a1-494">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0a1-494">Parameters</span></span>
* <span data-ttu-id="fd0a1-495">x-指の水平方向の位置。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-495">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="fd0a1-496">y-指の垂直方向の位置。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-496">y - The vertical position of the finger.</span></span>

<span data-ttu-id="fd0a1-497">**PerceptionSimulation (float, float) の位置を ISimulatedSixDofController します。**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-497">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="fd0a1-498">シミュレートされたコントローラーのタッチパッドでシミュレートされた指の位置を設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-498">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="fd0a1-499">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0a1-499">Parameters</span></span>
* <span data-ttu-id="fd0a1-500">x-指の水平方向の位置。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-500">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="fd0a1-501">y-指の垂直方向の位置。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-501">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="fd0a1-502">PerceptionSimulation. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="fd0a1-502">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="fd0a1-503">ISimulatedSixDofController を ISimulatedSixDofController2 にキャストすると、追加のプロパティとメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-503">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="fd0a1-504">**PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-504">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="fd0a1-505">シミュレートされたコントローラー上のシミュレートされたサムスティックの位置を取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-505">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="fd0a1-506">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0a1-506">Parameters</span></span>
* <span data-ttu-id="fd0a1-507">x-サムスティックの水平方向の位置。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-507">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="fd0a1-508">y-サムスティックの垂直方向の位置。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-508">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="fd0a1-509">**PerceptionSimulation. ISimulatedSixDofController2. SetThumbstickPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-509">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="fd0a1-510">シミュレートされたコントローラーのシミュレートされたサムスティックの位置を設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-510">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="fd0a1-511">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0a1-511">Parameters</span></span>
* <span data-ttu-id="fd0a1-512">x-サムスティックの水平方向の位置。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-512">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="fd0a1-513">y-サムスティックの垂直方向の位置。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-513">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="fd0a1-514">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-514">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="fd0a1-515">シミュレートされたコントローラーのバッテリレベルを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-515">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="fd0a1-516">値は0.0 より大きく、100.0 以下でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-516">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="fd0a1-517">PerceptionSimulation. ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="fd0a1-517">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="fd0a1-518">シミュレートされた人間の目を表すインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-518">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="fd0a1-519">**PerceptionSimulation. ISimulatedEyes**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-519">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="fd0a1-520">シミュレートされた目の回転を取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-520">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="fd0a1-521">正のラジアンは、軸に沿って表示すると時計回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-521">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="fd0a1-522">**PerceptionSimulation (ISimulatedEyes) (PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-522">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="fd0a1-523">現在の回転と比較して、シミュレートされた目を回転します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-523">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="fd0a1-524">正のラジアンは、軸に沿って表示すると時計回りに回転します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-524">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="fd0a1-525">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0a1-525">Parameters</span></span>
* <span data-ttu-id="fd0a1-526">rotation-回転する量。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-526">rotation - The amount to rotate.</span></span>

<span data-ttu-id="fd0a1-527">**PerceptionSimulation. ISimulatedEyes. CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-527">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="fd0a1-528">シミュレートされた目の調整状態を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-528">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="fd0a1-529">**PerceptionSimulation. ISimulatedEyes. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-529">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="fd0a1-530">世界のリレーションを使用してノードの位置をメートル単位で取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-530">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="fd0a1-531">PerceptionSimulation. ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="fd0a1-531">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="fd0a1-532">再生用に読み込まれた単一の記録と対話するためのインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-532">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="fd0a1-533">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-533">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="fd0a1-534">記録内のデータ型の一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-534">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="fd0a1-535">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-535">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="fd0a1-536">記録の現在の状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-536">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="fd0a1-537">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-537">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="fd0a1-538">再生を開始します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-538">Start the playback.</span></span> <span data-ttu-id="fd0a1-539">記録が一時停止されている場合は、一時停止した場所から再生が再開されます。停止した場合は、最初から再生が開始されます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-539">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="fd0a1-540">既に再生中の場合、この呼び出しは無視されます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-540">If already playing, this call is ignored.</span></span>

<span data-ttu-id="fd0a1-541">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-541">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="fd0a1-542">現在の場所で再生を一時停止します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-542">Pauses the playback at its current location.</span></span> <span data-ttu-id="fd0a1-543">記録が停止している場合、呼び出しは無視されます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-543">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="fd0a1-544">**PerceptionSimulation. ISimulationRecording (System. UInt64)**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-544">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="fd0a1-545">指定した時間 (先頭から100ナノ秒単位) に記録をシークし、その位置で一時停止します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-545">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="fd0a1-546">時刻が記録の末尾を越えている場合は、最後のフレームで一時停止します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-546">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="fd0a1-547">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0a1-547">Parameters</span></span>
* <span data-ttu-id="fd0a1-548">ティック-シークする時刻。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-548">ticks - The time to which to seek.</span></span>

<span data-ttu-id="fd0a1-549">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-549">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="fd0a1-550">再生を停止し、位置を先頭にリセットします。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-550">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="fd0a1-551">PerceptionSimulation. ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="fd0a1-551">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="fd0a1-552">再生中に状態の変更を受信するためのインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-552">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="fd0a1-553">**PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged (PerceptionSimulation. PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-553">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="fd0a1-554">ISimulationRecording の再生状態が変更されたときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-554">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="fd0a1-555">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0a1-555">Parameters</span></span>
* <span data-ttu-id="fd0a1-556">newState-記録の新しい状態。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-556">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="fd0a1-557">PerceptionSimulation. PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="fd0a1-557">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="fd0a1-558">認識シミュレーションオブジェクトを作成するためのルートオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-558">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="fd0a1-559">**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager (PerceptionSimulation. ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-559">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="fd0a1-560">シミュレートされたパケットを生成し、指定したシンクに配信するために、オブジェクトでを作成します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-560">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="fd0a1-561">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0a1-561">Parameters</span></span>
* <span data-ttu-id="fd0a1-562">sink-生成されたすべてのパケットを受信するシンク。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-562">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="fd0a1-563">戻り値</span><span class="sxs-lookup"><span data-stu-id="fd0a1-563">Return value</span></span>

<span data-ttu-id="fd0a1-564">作成されたマネージャー。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-564">The created Manager.</span></span>

<span data-ttu-id="fd0a1-565">**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording (System.string)**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-565">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="fd0a1-566">指定されたパスのファイルに受信したすべてのパケットを格納するシンクを作成します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-566">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="fd0a1-567">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0a1-567">Parameters</span></span>
* <span data-ttu-id="fd0a1-568">path-作成するファイルのパス。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-568">path - The path of the file to create.</span></span>

<span data-ttu-id="fd0a1-569">戻り値</span><span class="sxs-lookup"><span data-stu-id="fd0a1-569">Return value</span></span>

<span data-ttu-id="fd0a1-570">作成されたシンク。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-570">The created sink.</span></span>

<span data-ttu-id="fd0a1-571">**PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System.string, PerceptionSimulation.. ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-571">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="fd0a1-572">指定されたファイルから記録を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-572">Load a recording from the specified file.</span></span>

<span data-ttu-id="fd0a1-573">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0a1-573">Parameters</span></span>
* <span data-ttu-id="fd0a1-574">path-読み込むファイルのパス。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-574">path - The path of the file to load.</span></span>
* <span data-ttu-id="fd0a1-575">factory-必要なときに ISimulationStreamSink を作成するために記録によって使用されるファクトリ。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-575">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="fd0a1-576">戻り値</span><span class="sxs-lookup"><span data-stu-id="fd0a1-576">Return value</span></span>

<span data-ttu-id="fd0a1-577">読み込まれた記録。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-577">The loaded recording.</span></span>

<span data-ttu-id="fd0a1-578">**PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System.string, PerceptionSimulation ISimulationStreamSinkFactory, PerceptionSimulation. ISimulationRecordingCallback..)**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-578">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="fd0a1-579">指定されたファイルから記録を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-579">Load a recording from the specified file.</span></span>

<span data-ttu-id="fd0a1-580">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0a1-580">Parameters</span></span>
* <span data-ttu-id="fd0a1-581">path-読み込むファイルのパス。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-581">path - The path of the file to load.</span></span>
* <span data-ttu-id="fd0a1-582">factory-必要なときに ISimulationStreamSink を作成するために記録によって使用されるファクトリ。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-582">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="fd0a1-583">callback-更新を受け取るコールバックで、記録の状態を再適用します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-583">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="fd0a1-584">戻り値</span><span class="sxs-lookup"><span data-stu-id="fd0a1-584">Return value</span></span>

<span data-ttu-id="fd0a1-585">読み込まれた記録。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-585">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="fd0a1-586">PerceptionSimulation データ型</span><span class="sxs-lookup"><span data-stu-id="fd0a1-586">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="fd0a1-587">さまざまな種類のストリームデータについて説明します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-587">Describes the different types of stream data.</span></span>

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

<span data-ttu-id="fd0a1-588">**PerceptionSimulation のデータ型はありません。**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-588">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="fd0a1-589">ストリームデータ型がないことを示すために使用される sentinel 値。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-589">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="fd0a1-590">**PerceptionSimulation のデータ型**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-590">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="fd0a1-591">ヘッドの位置と向きに関するデータのストリーム。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-591">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="fd0a1-592">**PerceptionSimulation のデータ型**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-592">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="fd0a1-593">ハンドの位置とジェスチャに関するデータのストリーム。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-593">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="fd0a1-594">**PerceptionSimulation. SpatialMapping.**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-594">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="fd0a1-595">環境の空間マッピングに関するデータのストリーム。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-595">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="fd0a1-596">**PerceptionSimulation のデータ型**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-596">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="fd0a1-597">デバイスの調整に関するデータのストリーム。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-597">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="fd0a1-598">調整パケットは、リモートモードのシステムでのみ受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-598">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="fd0a1-599">**PerceptionSimulation のデータ型**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-599">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="fd0a1-600">デバイスの環境に関するデータのストリーム。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-600">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="fd0a1-601">**PerceptionSimulation. SixDofControllers.**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-601">**Microsoft.PerceptionSimulation.StreamDataTypes.SixDofControllers**</span></span>

<span data-ttu-id="fd0a1-602">モーションコントローラーに関するデータのストリーム。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-602">Stream of data regarding motion controllers.</span></span>

<span data-ttu-id="fd0a1-603">**PerceptionSimulation のデータ型**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-603">**Microsoft.PerceptionSimulation.StreamDataTypes.Eyes**</span></span>

<span data-ttu-id="fd0a1-604">シミュレートされた人間の目に関するデータのストリーム。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-604">Stream of data regarding the eyes of the simulated human.</span></span>

<span data-ttu-id="fd0a1-605">**PerceptionSimulation を構成します。**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-605">**Microsoft.PerceptionSimulation.StreamDataTypes.DisplayConfiguration**</span></span>

<span data-ttu-id="fd0a1-606">デバイスのディスプレイ構成に関するデータのストリーム。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-606">Stream of data regarding the display configuration of the device.</span></span>

<span data-ttu-id="fd0a1-607">**PerceptionSimulation のデータ型**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-607">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="fd0a1-608">すべての記録されたデータ型を示すために使用される sentinel 値。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-608">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="fd0a1-609">PerceptionSimulation. ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="fd0a1-609">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="fd0a1-610">シミュレーションストリームからデータパケットを受信するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-610">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="fd0a1-611">**PerceptionSimulation. ISimulationStreamSink (uint length, byte [] パケット数)**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-611">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="fd0a1-612">内部的に型指定され、バージョン管理される1つのパケットを受信します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-612">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="fd0a1-613">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0a1-613">Parameters</span></span>
* <span data-ttu-id="fd0a1-614">length-パケットの長さ。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-614">length - The length of the packet.</span></span>
* <span data-ttu-id="fd0a1-615">パケット-パケットのデータ。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-615">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="fd0a1-616">PerceptionSimulation. ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="fd0a1-616">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="fd0a1-617">ISimulationStreamSink を作成するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-617">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="fd0a1-618">**PerceptionSimulation. ISimulationStreamSinkFactory-Ationstreamsink ()**</span><span class="sxs-lookup"><span data-stu-id="fd0a1-618">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="fd0a1-619">ISimulationStreamSink の1つのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-619">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="fd0a1-620">戻り値</span><span class="sxs-lookup"><span data-stu-id="fd0a1-620">Return value</span></span>

<span data-ttu-id="fd0a1-621">作成されたシンク。</span><span class="sxs-lookup"><span data-stu-id="fd0a1-621">The created sink.</span></span>
