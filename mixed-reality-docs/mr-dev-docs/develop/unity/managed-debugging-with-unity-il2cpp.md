---
title: Unity IL2CPP を使用したマネージド デバッグ
description: この記事では、Unity IL2CPP UWP プロジェクトでマネージデバッガーを実行する方法について説明します。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity, visual studio, デバッグ, il2cpp, HoloLens, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想 reality ヘッドセット, UWP
ms.openlocfilehash: 4b21e4888e467e6bd5f1938024a1b8312d8ecbcb
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010243"
---
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="ee9cc-104">Unity IL2CPP を使用したマネージド デバッグ</span><span class="sxs-lookup"><span data-stu-id="ee9cc-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="ee9cc-105">次の手順に従って、マネージデバッガーを HoloLens と HoloLens 2 用の Unity IL2CPP UWP ビルドにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="ee9cc-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="ee9cc-106">[マルチキャスト](https://en.wikipedia.org/wiki/Multicast)をサポートしているネットワーク上に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee9cc-106">You'll need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
2. <span data-ttu-id="ee9cc-107">**UWP 発行設定機能** にアクセスし、 **Internetclientserver** と **PrivateNetworkClientServer** を確認します。</span><span class="sxs-lookup"><span data-stu-id="ee9cc-107">Go to **UWP Publishing Settings Capabilities** and check **InternetClientServer** and **PrivateNetworkClientServer**:</span></span>

    ![UWP 発行設定機能](images/il2cpp-debugging-capabilities.png)

3. <span data-ttu-id="ee9cc-109">Unity UWP ビルド設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="ee9cc-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="ee9cc-110">開発のビルド</span><span class="sxs-lookup"><span data-stu-id="ee9cc-110">Development Build</span></span>
    - <span data-ttu-id="ee9cc-111">スクリプト デバッグ</span><span class="sxs-lookup"><span data-stu-id="ee9cc-111">Script Debugging</span></span>
    - <span data-ttu-id="ee9cc-112">マネージデバッガーを待機する (省略可能)</span><span class="sxs-lookup"><span data-stu-id="ee9cc-112">Wait for Managed Debugger (optional)</span></span>

    ![UWP ビルドの設定](images/il2cpp-debugging-build.png)

4. <span data-ttu-id="ee9cc-114">Unity でビルドします。</span><span class="sxs-lookup"><span data-stu-id="ee9cc-114">Build in Unity.</span></span>
5. <span data-ttu-id="ee9cc-115">Visual Studio ソリューションからデバイスにビルドしてデプロイします。</span><span class="sxs-lookup"><span data-stu-id="ee9cc-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="ee9cc-116">**デバッグ** 構成または **リリース** 構成を使用してビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee9cc-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="ee9cc-117">**マスター** 構成によって Unity プロファイラーが無効になり、最適なデバッグができなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ee9cc-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="ee9cc-118">必要に応じて、ソリューションの package.appxmanifest の [機能] ボックスの一覧で、 **インターネット (クライアント & サーバー)** と **プライベートネットワーク (クライアント & サーバー)** を確認します。</span><span class="sxs-lookup"><span data-stu-id="ee9cc-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
6. <span data-ttu-id="ee9cc-119">デバイスが PC と同じネットワークに接続されていることを確認し、デバイスでアプリを起動します。</span><span class="sxs-lookup"><span data-stu-id="ee9cc-119">Make sure your device is connected to the same network as your PC and start the app on your device.</span></span>
7. <span data-ttu-id="ee9cc-120">デバイスが USB 経由で PC に接続されて **いない** ことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ee9cc-120">Make sure the device **is not** connected to your PC via USB.</span></span>
8. <span data-ttu-id="ee9cc-121">Unity のスクリプトの1つをダブルクリックし、開いた Visual Studio ソリューションにアクセスして表示と編集を行います。</span><span class="sxs-lookup"><span data-stu-id="ee9cc-121">Double-click one of your scripts in Unity and go to the Visual Studio solution that opens to view and edit.</span></span>
9. <span data-ttu-id="ee9cc-122">デバッグ-> Unity デバッガーをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="ee9cc-122">Debug -> Attach Unity Debugger.</span></span>

    ![Unity デバッガーのアタッチ](images/il2cpp-debugging-attach.png)

10. <span data-ttu-id="ee9cc-124">一覧からデバイスを選択し、[OK] をクリックして接続します。</span><span class="sxs-lookup"><span data-stu-id="ee9cc-124">Select your device in the list and click "OK" to attach.</span></span>

    ![デバイス一覧](images/il2cpp-debugging-machines.png)
