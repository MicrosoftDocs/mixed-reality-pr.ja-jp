---
title: MR と Azure 313 - IoT Hub サービス
description: Ubuntu 16.4 を実行している仮想マシンに Azure IoT Hub サービスを実装し、Microsoft HoloLens または VR ヘッドセットを使用してメッセージデータを視覚化する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: azure, mixed reality, academy, エッジ, iot edge, チュートリアル, api, 通知, 関数, テーブル, hololens, イマーシブ, vr, iot, 仮想マシン, ubuntu, python, Windows 10, Visual Studio
ms.openlocfilehash: 3c01c7351ee284b72a15fd7d5bdd3205fec91e49
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009302"
---
# <a name="mr-and-azure-313-iot-hub-service"></a><span data-ttu-id="bc14a-104">MR と Azure 313:IoT Hub サービス</span><span class="sxs-lookup"><span data-stu-id="bc14a-104">MR and Azure 313: IoT Hub Service</span></span>

>[!NOTE]
><span data-ttu-id="bc14a-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="bc14a-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="bc14a-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="bc14a-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="bc14a-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。</span><span class="sxs-lookup"><span data-stu-id="bc14a-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="bc14a-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="bc14a-109">今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="bc14a-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="bc14a-110">この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

![コースの結果](images/AzureLabs-Lab313-00.png)

<span data-ttu-id="bc14a-112">このコースでは、Ubuntu 16.4 オペレーティングシステムを実行している仮想マシンに **Azure IoT Hub サービス** を実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-112">In this course, you will learn how to implement an **Azure IoT Hub Service** on a virtual machine running the Ubuntu 16.4 operating system.</span></span> <span data-ttu-id="bc14a-113">**Azure Function App** は、Ubuntu VM からメッセージを受信するために使用され、その結果を **azure Table Service** 内に格納します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-113">An **Azure Function App** will then be used to receive messages from your Ubuntu VM, and store the result within an **Azure Table Service**.</span></span> <span data-ttu-id="bc14a-114">その後、Microsoft HoloLens またはイマーシブ (VR) ヘッドセットの **Power BI** を使用して、このデータを表示できるようになります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-114">You will then be able to view this data using **Power BI** on Microsoft HoloLens or immersive (VR) headset.</span></span>

<span data-ttu-id="bc14a-115">このコースの内容は IoT Edge デバイスに *適用されますが* 、このコースでは、物理エッジデバイスへのアクセスを必要としないように、仮想マシン環境に焦点が当てはまります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-115">The content of this course *is applicable* to IoT Edge devices, though for the purpose of this course, the focus will be on a virtual machine environment, so that access to a physical Edge device is not necessary.</span></span>

<span data-ttu-id="bc14a-116">このコースを完了すると、次のことを学習できます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-116">By completing this course, you will learn to:</span></span>

- <span data-ttu-id="bc14a-117">**IoT Edge モジュール** を仮想マシン (UBUNTU 16 OS) にデプロイします。これは、IoT デバイスを表します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-117">Deploy an **IoT Edge module** to a Virtual Machine (Ubuntu 16 OS), which will represent your IoT device.</span></span>
- <span data-ttu-id="bc14a-118">コンテナーに格納されているイメージを分析するコードを使用して、 **Azure Custom Vision の Azure Azure の "Azure" Azure** "のモデルを Edge モジュールに追加します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-118">Add an **Azure Custom Vision Tensorflow Model** to the Edge module, with code that will analyze images stored in the container.</span></span>
- <span data-ttu-id="bc14a-119">分析結果メッセージを **IoT Hub サービス** に返すようにモジュールを設定します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-119">Set up the module to send the analysis result message back to your **IoT Hub Service**.</span></span>
- <span data-ttu-id="bc14a-120">Azure **Function App** を使用して、 **azure テーブル** 内にメッセージを格納します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-120">Use an **Azure Function App** to store the message within an **Azure Table**.</span></span>
- <span data-ttu-id="bc14a-121">保存されたメッセージを収集してレポートを作成するように **Power BI** を設定します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-121">Set up **Power BI** to collect the stored message and create a report.</span></span>
- <span data-ttu-id="bc14a-122">**Power BI** 内で IoT メッセージデータを視覚化します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-122">Visualize your IoT message data within **Power BI**.</span></span>

<span data-ttu-id="bc14a-123">使用するサービスには次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-123">The Services you will use include:</span></span>

- <span data-ttu-id="bc14a-124">**Azure IoT Hub** は、開発者が IoT 資産の接続、監視、管理を行うことができるようにする Microsoft Azure サービスです。</span><span class="sxs-lookup"><span data-stu-id="bc14a-124">**Azure IoT Hub** is a Microsoft Azure Service which allows developers to connect, monitor, and manage, IoT assets.</span></span> <span data-ttu-id="bc14a-125">詳細については、 [ **Azure IoT Hub サービス**](https://azure.microsoft.com/services/iot-hub/)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc14a-125">For more information, visit the [**Azure IoT Hub Service** page](https://azure.microsoft.com/services/iot-hub/).</span></span>

- <span data-ttu-id="bc14a-126">**Azure Container Registry** は、さまざまな種類のコンテナーについて、開発者がコンテナーイメージを格納できるようにする、Microsoft Azure サービスです。</span><span class="sxs-lookup"><span data-stu-id="bc14a-126">**Azure Container Registry** is a Microsoft Azure Service which allows developers to store container images, for various types of containers.</span></span> <span data-ttu-id="bc14a-127">詳細については、 [ **Azure Container Registry サービス**](https://azure.microsoft.com/services/container-registry/)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc14a-127">For more information, visit the [**Azure Container Registry Service** page](https://azure.microsoft.com/services/container-registry/).</span></span>

- <span data-ttu-id="bc14a-128">**Azure Function App** は Microsoft Azure サービスであり、開発者は azure で小さなコードである "functions" を実行できます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-128">**Azure Function App** is a Microsoft Azure Service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="bc14a-129">これにより、ローカルアプリケーションではなく、クラウドに作業を委任することができます。これには多くのメリットがあります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-129">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="bc14a-130">**Azure Functions** は、C \# 、F \# 、Node.js、Java、PHP など、いくつかの開発言語をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="bc14a-130">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="bc14a-131">詳細については、 [ **Azure Functions** のページ](https://docs.microsoft.com/azure/azure-functions/functions-overview)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc14a-131">For more information, visit the [**Azure Functions** page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

- <span data-ttu-id="bc14a-132">**Azure Storage: テーブル** は Microsoft Azure サービスです。これにより、開発者は構造化された SQL 以外のデータをクラウドに格納し、どこからでも簡単にアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-132">**Azure Storage: Tables** is a Microsoft Azure Service, which allows developers to store structured, non-SQL, data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="bc14a-133">このサービスでは、スキーマのない設計が非常に優れているため、必要に応じてテーブルを進化させることができるため、非常に柔軟性があります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-133">The Service boasts a schema-less design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="bc14a-134">詳細については、 [ **Azure のテーブル** に関するページを参照してください。](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="bc14a-134">For more information, visit the [**Azure Tables** page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="bc14a-135">このコースでは、IoT Hub サービスを設定して使用する方法と、デバイスによって提供される応答を視覚化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-135">This course will teach you how to setup and use the IoT Hub Service, and then visualize a response provided by a device.</span></span> <span data-ttu-id="bc14a-136">これらの概念は、作成するカスタム IoT Hub サービスのセットアップに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-136">It will be up to you to apply these concepts to a custom IoT Hub Service setup, which you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="bc14a-137">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="bc14a-137">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="bc14a-138">コース</span><span class="sxs-lookup"><span data-stu-id="bc14a-138">Course</span></span></th><th style="width:150px"> <span data-ttu-id="bc14a-139"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="bc14a-139"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="bc14a-140"><a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="bc14a-140"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="bc14a-141">MR と Azure 313:IoT Hub サービス</span><span class="sxs-lookup"><span data-stu-id="bc14a-141">MR and Azure 313: IoT Hub Service</span></span></td><td style="text-align: center;"> <span data-ttu-id="bc14a-142">✔️</span><span class="sxs-lookup"><span data-stu-id="bc14a-142">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="bc14a-143">✔️</span><span class="sxs-lookup"><span data-stu-id="bc14a-143">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="bc14a-144">前提条件</span><span class="sxs-lookup"><span data-stu-id="bc14a-144">Prerequisites</span></span>

<span data-ttu-id="bc14a-145">Microsoft HoloLens など、mixed reality を使用した開発に関する最新の前提条件については、 [ツールのインストール](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bc14a-145">For the most up-to-date prerequisites for developing with mixed reality, including with the Microsoft HoloLens, visit the [Install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article.</span></span>

> [!NOTE]
> <span data-ttu-id="bc14a-146">このチュートリアルは、Python の基本的な経験がある開発者向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="bc14a-146">This tutorial is designed for developers who have basic experience with Python.</span></span> <span data-ttu-id="bc14a-147">また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証された内容 (2018 年7月) を表しています。</span><span class="sxs-lookup"><span data-stu-id="bc14a-147">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="bc14a-148">「 [ツールのインストール](../../install-the-tools.md) 」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に示したソフトウェアより新しいソフトウェアでは完全に一致するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="bc14a-148">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than that listed below.</span></span>

<span data-ttu-id="bc14a-149">次のハードウェアとソフトウェアが必要です。</span><span class="sxs-lookup"><span data-stu-id="bc14a-149">The following hardware and software is required:</span></span>

- <span data-ttu-id="bc14a-150">Windows 10 の作成者の更新プログラム (またはそれ以降)、 **開発者モードが有効**</span><span class="sxs-lookup"><span data-stu-id="bc14a-150">Windows 10 Fall Creators Update (or later), **Developer Mode enabled**</span></span>

    > [!WARNING]
    > <span data-ttu-id="bc14a-151">Windows 10 Home Edition で Hyper-v を使用して仮想マシンを実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="bc14a-151">You cannot run a Virtual Machine using Hyper-V on Windows 10 Home Edition.</span></span>

- <span data-ttu-id="bc14a-152">Windows 10 SDK (最新バージョン)</span><span class="sxs-lookup"><span data-stu-id="bc14a-152">Windows 10 SDK (latest version)</span></span>
- <span data-ttu-id="bc14a-153">HoloLens、 **開発者モードが有効**</span><span class="sxs-lookup"><span data-stu-id="bc14a-153">A HoloLens, **Developer Mode enabled**</span></span>
- <span data-ttu-id="bc14a-154">Visual Studio 2017.15.4 (Azure Cloud Explorer へのアクセスにのみ使用)</span><span class="sxs-lookup"><span data-stu-id="bc14a-154">Visual Studio 2017.15.4 (Only used to access the Azure Cloud Explorer)</span></span>
- <span data-ttu-id="bc14a-155">Azure および IoT Hub サービス用のインターネットアクセス。</span><span class="sxs-lookup"><span data-stu-id="bc14a-155">Internet Access for Azure, and for IoT Hub Service.</span></span> <span data-ttu-id="bc14a-156">詳細については、こちらの[IoT Hub サービスへのリンクに関するページを](https://azure.microsoft.com/services/iot-hub/)参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc14a-156">For more information, please follow this [link to IoT Hub Service page](https://azure.microsoft.com/services/iot-hub/)</span></span>
- <span data-ttu-id="bc14a-157">機械学習モデル。</span><span class="sxs-lookup"><span data-stu-id="bc14a-157">A machine learning model.</span></span> <span data-ttu-id="bc14a-158">独自のモデルを使用する準備ができていない場合は、 [このコースで提供さ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)れているモデルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-158">If you do not have your own ready to use model, [you can use the model provided with this course](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span></span>
- <span data-ttu-id="bc14a-159">Windows 10 開発用コンピューターで **hyper-v** ソフトウェアが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="bc14a-159">**Hyper-V** software enabled on your Windows 10 development machine.</span></span>
- <span data-ttu-id="bc14a-160">Ubuntu (16.4 または 18.4) を実行している仮想マシンを開発用コンピューターで実行するか、または Linux を実行する別のコンピューター (Ubuntu 16.4 または 18.4) を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-160">A Virtual Machine running Ubuntu (16.4 or 18.4), running on your development machine or alternatively you can use a separate computer running Linux (Ubuntu 16.4 or 18.4).</span></span> <span data-ttu-id="bc14a-161">Hyper-v を使用して Windows 上で VM を作成する方法の詳細については、 [「開始する前に](#before-you-start)」の章を参照してください。(https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="bc14a-161">You can find more information on how to create a VM on Windows using Hyper-V in the ["Before you Start" chapter](#before-you-start).(https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span></span>  



### <a name="before-you-start"></a><span data-ttu-id="bc14a-162">アップグレードを開始する前に</span><span class="sxs-lookup"><span data-stu-id="bc14a-162">Before you start</span></span>

1. <span data-ttu-id="bc14a-163">HoloLens をセットアップしてテストします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-163">Set up and test your HoloLens.</span></span> <span data-ttu-id="bc14a-164">HoloLens のセットアップをサポートする必要がある場合は、 [hololens セットアップに関する記事にアクセスして](https://docs.microsoft.com/hololens/hololens-setup)ください。</span><span class="sxs-lookup"><span data-stu-id="bc14a-164">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span>
2. <span data-ttu-id="bc14a-165">新しい HoloLens アプリの開発を開始するときは、 **調整** と **センサーのチューニング** を実行することをお勧めします (ユーザーごとにこれらのタスクを実行するのに役立つ場合があります)。</span><span class="sxs-lookup"><span data-stu-id="bc14a-165">It is a good idea to perform **Calibration** and **Sensor Tuning** when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span>

<span data-ttu-id="bc14a-166">調整の詳細については、 [「HoloLens の調整に関する記事へのリンク」を](../../../calibration.md#hololens-2)参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc14a-166">For help on Calibration, please follow this [link to the HoloLens Calibration article](../../../calibration.md#hololens-2).</span></span>

<span data-ttu-id="bc14a-167">センサーチューニングの詳細については、 [HoloLens センサーチューニングに関する記事へのリンクを](../../../sensor-tuning.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc14a-167">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](../../../sensor-tuning.md).</span></span>

3. <span data-ttu-id="bc14a-168">**Hyper-v** を使用して **Ubuntu 仮想マシン** をセットアップします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-168">Set up your **Ubuntu Virtual Machine** using **Hyper-V**.</span></span> <span data-ttu-id="bc14a-169">このプロセスには、次のリソースが役立ちます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-169">The following resources will help you with the process.</span></span>
    1.  <span data-ttu-id="bc14a-170">まず、このリンクに従っ [て Ubuntu 16.04.4 LTS (Xenial Xerus) ISO をダウンロード](https://au.releases.ubuntu.com/16.04/)します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-170">First, follow this link to [download the Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](https://au.releases.ubuntu.com/16.04/).</span></span> <span data-ttu-id="bc14a-171">64ビット **PC (AMD64) デスクトップイメージ** を選択します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-171">Select the **64-bit PC (AMD64) desktop image**.</span></span>
    2.  <span data-ttu-id="bc14a-172">Windows 10 コンピューターで **hyper-v** が有効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-172">Make sure **Hyper-V** is enabled on your Windows 10 machine.</span></span> <span data-ttu-id="bc14a-173">[Windows 10 で hyper-v をインストールして有効](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)にする方法については、こちらのリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc14a-173">You can follow this link for guidance on [installing and enabling Hyper-V on Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span></span>
    3.  <span data-ttu-id="bc14a-174">Hyper-v を起動し、新しい Ubuntu VM を作成します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-174">Start Hyper-V and create a new Ubuntu VM.</span></span> <span data-ttu-id="bc14a-175">[Hyper-v を使用して VM を作成する手順](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine)については、こちらのリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc14a-175">You can follow this link for a [step by step guide on how to create a VM with Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span></span> <span data-ttu-id="bc14a-176">**[起動可能なイメージファイルからオペレーティングシステムをインストール** する] に要求された場合は、前の手順でダウンロードした **Ubuntu ISO** を選択します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-176">When requested to **"Install an operating system from a bootable image file"**, select the **Ubuntu ISO** you have download earlier.</span></span>

    > [!NOTE]
    > <span data-ttu-id="bc14a-177">**Hyper-v の簡易作成** を使用することは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="bc14a-177">Using **Hyper-V Quick Create** is not suggested.</span></span>  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a><span data-ttu-id="bc14a-178">第1章: Custom Vision モデルを取得する</span><span class="sxs-lookup"><span data-stu-id="bc14a-178">Chapter 1 - Retrieve the Custom Vision model</span></span>

<span data-ttu-id="bc14a-179">このコースでは、イメージからキーボードとマウスを検出する既成の [Custom Vision モデル](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-179">With this course you will have access to a [pre-built Custom Vision model](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) that detects keyboards and mice from images.</span></span> <span data-ttu-id="bc14a-180">これを使用する場合は、 [第2章](#chapter-2---the-container-registry-service)に進みます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-180">If you use this, proceed to [Chapter 2](#chapter-2---the-container-registry-service).</span></span>

<span data-ttu-id="bc14a-181">ただし、独自の Custom Vision モデルを使用する場合は、次の手順に従うことができます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-181">However, you can follow these steps if you wish to use your own Custom Vision model:</span></span>

1. <span data-ttu-id="bc14a-182">**Custom Vision プロジェクト** で、[**パフォーマンス**] タブにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-182">In your **Custom Vision Project** go to the **Performance** tab.</span></span>

    > [!WARNING]
    > <span data-ttu-id="bc14a-183">モデルをエクスポートするには、モデルで *コンパクト* ドメインを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-183">Your model must use a *compact* domain, to export the model.</span></span> <span data-ttu-id="bc14a-184">モデルドメインは、プロジェクトの設定で変更できます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-184">You can change your models domain in the settings for your project.</span></span>

    ![[パフォーマンス] タブ](images/AzureLabs-Lab313-01.png)

2. <span data-ttu-id="bc14a-186">エクスポートする **イテレーション** を選択し、[ **エクスポート**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-186">Select the **Iteration** you want to export and click on **Export**.</span></span> <span data-ttu-id="bc14a-187">ブレードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-187">A blade will appear.</span></span>

    ![ブレードのエクスポート](images/AzureLabs-Lab313-02.png)

3. <span data-ttu-id="bc14a-189">ブレードで [ **Docker File**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-189">In the blade click **Docker File**.</span></span>

    ![docker の選択](images/AzureLabs-Lab313-03.png)

4. <span data-ttu-id="bc14a-191">ドロップダウンメニューの [ **Linux** ] をクリックし、[ **ダウンロード**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-191">Click **Linux** in the drop-down menu and then click on **Download**.</span></span>

    ![[ダウンロード] をクリック](images/AzureLabs-Lab313-04.png)

5. <span data-ttu-id="bc14a-193">コンテンツを解凍します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-193">Unzip the content.</span></span> <span data-ttu-id="bc14a-194">このコースは、このコースの後半で使用します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-194">You will use it later in this course.</span></span>

## <a name="chapter-2---the-container-registry-service"></a><span data-ttu-id="bc14a-195">Chapter 2-Container Registry サービス</span><span class="sxs-lookup"><span data-stu-id="bc14a-195">Chapter 2 - The Container Registry Service</span></span>

<span data-ttu-id="bc14a-196">**Container Registry サービス** は、コンテナーをホストするために使用されるリポジトリです。</span><span class="sxs-lookup"><span data-stu-id="bc14a-196">The **Container Registry Service** is the repository used to host your containers.</span></span>

<span data-ttu-id="bc14a-197">このコースで構築して使用する **IoT Hub サービス** は、 **Container Registry サービス** を参照して、エッジデバイスにデプロイするコンテナーを取得します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-197">The **IoT Hub Service** that you will build and use in this course, refers to **Container Registry Service** to obtain the containers to deploy in your Edge Device.</span></span>

1. <span data-ttu-id="bc14a-198">最初に、 [Azure Portal へのリンク](https://portal.azure.com/)に従って、資格情報でログインします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-198">First, follow this [link to the Azure Portal](https://portal.azure.com/), and login with your credentials.</span></span>

2. <span data-ttu-id="bc14a-199">「 **リソースの作成** 」に進んで、 **Container Registry** を探します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-199">Go to **Create a resource** and look for **Container Registry**.</span></span>

    ![コンテナーレジストリ](images/AzureLabs-Lab313-05.png)

3. <span data-ttu-id="bc14a-201">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-201">Click on **Create**.</span></span>

    ![](images/AzureLabs-Lab313-06.png)

4. <span data-ttu-id="bc14a-202">サービスセットアップパラメーターを設定します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-202">Set the Service setup parameters:</span></span>

    1. <span data-ttu-id="bc14a-203">プロジェクトの名前を挿入します。この例では、 **IoTCRegistry** という名前です。</span><span class="sxs-lookup"><span data-stu-id="bc14a-203">Insert a name for your project, In this example its called **IoTCRegistry**.</span></span>

    2. <span data-ttu-id="bc14a-204">リソースグループを選択するか、新しい **リソースグループ** を作成します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-204">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="bc14a-205">リソースグループを使用すると、Azure 資産のコレクションの監視、アクセスの制御、プロビジョニング、管理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-205">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="bc14a-206">1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのコースなど) を共通のリソースグループに保持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-206">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    3. <span data-ttu-id="bc14a-207">サービスの場所を設定します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-207">Set the location of the Service.</span></span>

    4. <span data-ttu-id="bc14a-208">**有効** にするには、**管理者ユーザー** を設定します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-208">Set **Admin user** to **Enable**.</span></span>

    5. <span data-ttu-id="bc14a-209">**SKU** を **Basic** に設定します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-209">Set **SKU** to **Basic**.</span></span> 

    ![](images/AzureLabs-Lab313-07.png)

5. <span data-ttu-id="bc14a-210">[ **作成** ] をクリックし、サービスが作成されるまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-210">Click **Create** and wait for the Services to be created.</span></span> 

6. <span data-ttu-id="bc14a-211">*Container Registry* が正常に作成されたことを知らせる通知が表示されたら、[**リソースへのアクセス**] をクリックして、サービスページにリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-211">Once the notification pops up informing you of the successful creation of the *Container Registry*, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![](images/AzureLabs-Lab313-08.png)

7. <span data-ttu-id="bc14a-212">[サービスの *Container Registry* ] ページで、[ **アクセスキー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-212">In the *Container Registry* Service page, click on **Access keys**.</span></span>

8. <span data-ttu-id="bc14a-213">次のパラメーターのメモを控えておきます (メモ帳を使用できます)。</span><span class="sxs-lookup"><span data-stu-id="bc14a-213">Take note (you could use your Notepad) of the following parameters:</span></span>
    1. <span data-ttu-id="bc14a-214">**ログインサーバー**</span><span class="sxs-lookup"><span data-stu-id="bc14a-214">**Login Server**</span></span>
    2. <span data-ttu-id="bc14a-215">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="bc14a-215">**Username**</span></span>
    3. <span data-ttu-id="bc14a-216">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="bc14a-216">**Password**</span></span>

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a><span data-ttu-id="bc14a-217">第3章-IoT Hub サービス</span><span class="sxs-lookup"><span data-stu-id="bc14a-217">Chapter 3 - The IoT Hub Service</span></span>

<span data-ttu-id="bc14a-218">次に、 **IoT Hub サービス** の作成とセットアップを開始します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-218">Now you will begin the creation and setup of your **IoT Hub Service**.</span></span>

1. <span data-ttu-id="bc14a-219">まだサインインしていない場合は、 [Azure Portal](https://portal.azure.com)にログインします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-219">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="bc14a-220">ログインしたら、左上隅にある [ **リソースの作成** ] をクリックし、 **IoT Hub** を検索して、 **Enter キー** を押します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-220">Once logged in, click on **Create a resource** in the top left corner, and search for **IoT Hub**, and click **Enter**.</span></span>

 ![ストレージアカウントの検索](images/AzureLabs-Lab313-10.png)

3.  <span data-ttu-id="bc14a-222">新しいページには、 **ストレージアカウント** サービスの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-222">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="bc14a-223">このプロンプトの左下にある [ **作成** ] ボタンをクリックして、このサービスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-223">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![ストレージインスタンスの作成](images/AzureLabs-Lab313-11.png)

4.  <span data-ttu-id="bc14a-225">[ **作成**] をクリックすると、パネルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-225">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="bc14a-226">リソースグループを選択するか、新しい **リソースグループ** を作成します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-226">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="bc14a-227">リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-227">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="bc14a-228">1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのコースなど) を共通のリソースグループに保持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-228">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="bc14a-229">Azure リソースグループの詳細については、 [リソースグループの管理方法に関するリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc14a-229">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>


    2. <span data-ttu-id="bc14a-230">適切な **場所** を選択します (このコースで作成するすべてのサービスで同じ場所を使用します)。</span><span class="sxs-lookup"><span data-stu-id="bc14a-230">Select an appropriate **Location** (Use the same location across all the Services you create in this course).</span></span>

    3. <span data-ttu-id="bc14a-231">このサービスインスタンスに必要な **名前** を挿入します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-231">Insert your desired **Name** for this Service instance.</span></span>    

5.  <span data-ttu-id="bc14a-232">ページの下部にある [次の **サイズとスケール**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-232">On the bottom of the page click on **Next: Size and scale**.</span></span>

    ![ストレージインスタンスの作成](images/AzureLabs-Lab313-12.png)

6.  <span data-ttu-id="bc14a-234">このページで、 **価格とスケールレベル** を選択します (これが初めての IoT Hub サービスインスタンスの場合は、free レベルをご利用いただけます)。</span><span class="sxs-lookup"><span data-stu-id="bc14a-234">In this page, select your **Pricing and scale tier** (if this is your first IoT Hub Service instance, a free tier should be available to you).</span></span>  

7.  <span data-ttu-id="bc14a-235">[ **レビューと作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-235">Click on **Review + Create**.</span></span>

    ![ストレージインスタンスの作成](images/AzureLabs-Lab313-13.png)

8.  <span data-ttu-id="bc14a-237">設定を確認し、[ **作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-237">Review your settings and click on **Create**.</span></span>

    ![ストレージインスタンスの作成](images/AzureLabs-Lab313-14.png)

9. <span data-ttu-id="bc14a-239">*IoT Hub* サービスが正常に作成されたことを知らせる通知が表示されたら、[**リソースへのアクセス**] をクリックして、サービスページにリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-239">Once the notification pops up informing you of the successful creation of the *IoT Hub* Service, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![ストレージインスタンスの作成](images/AzureLabs-Lab313-15.png)

10. <span data-ttu-id="bc14a-241">[ *デバイスの自動管理*] が表示されるまで左側のサイドパネルをスクロールし、 **IoT Edge** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-241">Scroll the side panel on the left until you see *Automatic Device Management*, the click on **IoT Edge**.</span></span>

    ![ストレージインスタンスの作成](images/AzureLabs-Lab313-16.png)

11. <span data-ttu-id="bc14a-243">右側に表示されるウィンドウで、[ **IoT Edge デバイスの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-243">In the window that appears to the right, click on **Add IoT Edge Device**.</span></span> <span data-ttu-id="bc14a-244">ブレードが右側に表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-244">A blade will appear to the right.</span></span>

12. <span data-ttu-id="bc14a-245">ブレードで、新しいデバイスに **デバイス ID** (任意の名前) を入力します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-245">In the blade, provide your new device a **Device ID** (a name of your choice).</span></span> <span data-ttu-id="bc14a-246">その後、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-246">Then, click **Save**.</span></span> <span data-ttu-id="bc14a-247">**自動生成** が行われた場合、*プライマリ\*\*キーとセカンダリキー* は自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-247">The *Primary* and *Secondary Keys* will auto generate, if you have **Auto Generate** ticked.</span></span>

    ![ストレージインスタンスの作成](images/AzureLabs-Lab313-17.png)

13. <span data-ttu-id="bc14a-249">新しいデバイスが一覧表示される [ *IoT Edge デバイス* ] セクションに戻ります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-249">You will navigate back to the *IoT Edge Devices* section, where your new device will be listed.</span></span> <span data-ttu-id="bc14a-250">新しいデバイス (下の図の赤で囲まれています) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-250">Click on your new device (outlined in red in the below image).</span></span> 

    ![ストレージインスタンスの作成](images/AzureLabs-Lab313-18.png)

14. <span data-ttu-id="bc14a-252">表示される [ *デバイスの詳細* ] ページで、 **接続文字列** (主キー) のコピーを取得します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-252">On the *Device Details* page that appears, take a copy of the **Connection String** (primary key).</span></span>

    ![ストレージインスタンスの作成](images/AzureLabs-Lab313-19.png)

15. <span data-ttu-id="bc14a-254">左側のパネルに戻り、[ *共有アクセスポリシー*] をクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-254">Go back to the panel on the left, and click *Shared access policies*, to open it.</span></span> 

16. <span data-ttu-id="bc14a-255">表示されるページで [ **iothubowner**] をクリックすると、画面の右側にブレードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-255">On the page that appears, click **iothubowner**, and a blade will appear to the right of the screen.</span></span> 

17. <span data-ttu-id="bc14a-256">**接続** 文字列 (主キー) のメモ (メモ帳) を書き留めておきます。後でデバイスに *接続文字列* を設定するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-256">Take note (on your Notepad) of the **Connection string** (primary key), for later use when setting the *Connection String* to your device.</span></span>

    ![ストレージインスタンスの作成](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a><span data-ttu-id="bc14a-258">章 4-開発環境の設定</span><span class="sxs-lookup"><span data-stu-id="bc14a-258">Chapter 4 - Setting up the development environment</span></span>

<span data-ttu-id="bc14a-259">*IoT Hub Edge* のモジュールを作成してデプロイするには、Windows 10 を実行する開発用コンピューターに次のコンポーネントがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-259">In order to create and deploy modules for *IoT Hub Edge*, you will require the following components installed on your development machine running Windows 10:</span></span>

1.  <span data-ttu-id="bc14a-260">[Docker for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows)、ダウンロードできるアカウントを作成するように求められます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-260">[Docker for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), it will ask you to create an account to be able to download.</span></span> 

    <span data-ttu-id="bc14a-261">[![docker for windows のダウンロード](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span><span class="sxs-lookup"><span data-stu-id="bc14a-261">[![download docker for windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="bc14a-262">Docker を実行するには、 *windows 10 PRO*、 *Enterprise 14393*、または *windows Server 2016 RTM* が必要です。</span><span class="sxs-lookup"><span data-stu-id="bc14a-262">Docker requires *Windows 10 PRO*, *Enterprise 14393*, or *Windows Server 2016 RTM*, to run.</span></span> <span data-ttu-id="bc14a-263">他のバージョンの Windows 10 を実行している場合は、 [Docker ツールボックス](https://docs.docker.com/toolbox/toolbox_install_windows/)を使用して docker をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-263">If you are running other versions of Windows 10, you can try installing Docker using the [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).</span></span>

2.  <span data-ttu-id="bc14a-264">[Python 3.6](https://www.python.org/downloads/)。</span><span class="sxs-lookup"><span data-stu-id="bc14a-264">[Python 3.6](https://www.python.org/downloads/).</span></span>

    <span data-ttu-id="bc14a-265">[![python 3.6 のダウンロード](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span><span class="sxs-lookup"><span data-stu-id="bc14a-265">[![download python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span></span>

3.  <span data-ttu-id="bc14a-266">[Visual Studio Code (VS Code とも呼ば](https://code.visualstudio.com/download)れます)。</span><span class="sxs-lookup"><span data-stu-id="bc14a-266">[Visual Studio Code (also known as VS Code)](https://code.visualstudio.com/download).</span></span>

    <span data-ttu-id="bc14a-267">[![ダウンロード VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span><span class="sxs-lookup"><span data-stu-id="bc14a-267">[![download VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span></span>

<span data-ttu-id="bc14a-268">前述のソフトウェアをインストールしたら、コンピューターを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-268">After installing the software mentioned above, you will need to restart your machine.</span></span>

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a><span data-ttu-id="bc14a-269">章 5-Ubuntu 環境のセットアップ</span><span class="sxs-lookup"><span data-stu-id="bc14a-269">Chapter 5 - Setting up the Ubuntu environment</span></span>

<span data-ttu-id="bc14a-270">これで、 **UBUNTU OS を実行** しているデバイスのセットアップに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-270">Now you can move on to setting up your device **running Ubuntu OS**.</span></span> <span data-ttu-id="bc14a-271">次の手順に従って、ボードにコンテナーをデプロイするために必要なソフトウェアをインストールします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-271">Follow the steps below, to install the necessary software, to deploy your containers on your board:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bc14a-272">管理者ユーザーとして実行するには、ターミナルコマンドの前に常に **sudo** を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-272">You should always precede the terminal commands with **sudo** to run as admin user.</span></span> <span data-ttu-id="bc14a-273">:</span><span class="sxs-lookup"><span data-stu-id="bc14a-273">i.e:</span></span>
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  <span data-ttu-id="bc14a-274">**Ubuntu ターミナル** を開き、次のコマンドを使用して **pip** をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-274">Open the **Ubuntu Terminal**, and use the following command to install **pip**:</span></span>

    > <span data-ttu-id="bc14a-275">[!ヒント] キーボードショートカット ( **Ctrl + Alt + T**) を使用して、*ターミナル* を非常に簡単に開くことができます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-275">[!HINT] You can open *Terminal* very easily through using the keyboard shortcut: **Ctrl + Alt + T**.</span></span>

    ```bash
        sudo apt-get install python-pip
    ```

2.  <span data-ttu-id="bc14a-276">この章では、デバイスのストレージを使用するためのアクセス許可を *ターミナル* で確認するメッセージが表示される場合があります。また、 **y/n** (yes または no) を入力するには「 **y」** と入力し、 **enter キーを押して同意** します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-276">Throughout this Chapter, you may be prompted, by *Terminal*, for permission to use your device storage, and for you to input **y/n** (yes or no), type **'y'**, and then press the **Enter** key, to accept.</span></span>

3.  <span data-ttu-id="bc14a-277">コマンドが完了したら、次のコマンドを使用して **curl** をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-277">Once that command has completed, use the following command to install **curl**:</span></span>

    ```bash
        sudo apt install curl
    ```

4.  <span data-ttu-id="bc14a-278">**Pip** および **curl** がインストールされたら、次のコマンドを使用して **IoT Edge ランタイム** をインストールします。これは、ボードにモジュールをデプロイおよび制御するために必要です。</span><span class="sxs-lookup"><span data-stu-id="bc14a-278">Once **pip** and **curl** are installed, use the following command to install the **IoT Edge runtime**, this is necessary to deploy and control the modules on your board:</span></span>

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. <span data-ttu-id="bc14a-279">この時点で、 **IoT Hub サービス** を作成するときにメモしておいた (メモ帳でメモしておいた)**デバイス接続文字列** を挿入するために、*ランタイム構成ファイル* を開くように求められます ([手順14の章 3](#chapter-3---the-iot-hub-service))。</span><span class="sxs-lookup"><span data-stu-id="bc14a-279">At this point you will be prompted to open up the *runtime config file*, to insert the **Device Connection String**, that you noted down (in your Notepad), when creating the **IoT Hub Service** ([at step 14, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="bc14a-280">ターミナルで次の行を実行して、そのファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-280">Run the following line on the terminal to open that file:</span></span>

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. <span data-ttu-id="bc14a-281">次のように、 **構成の yaml** ファイルが表示され、編集できるようになります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-281">The **config.yaml** file will be displayed, ready for you to edit:</span></span>

    > [!WARNING]
    > <span data-ttu-id="bc14a-282">このファイルが開いたときに、多少紛らわしいことがあります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-282">When this file opens, it may be somewhat confusing.</span></span> <span data-ttu-id="bc14a-283">このファイルを *ターミナル* 内で編集するテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-283">You will be text editing this file, within the *Terminal* itself.</span></span> 

    1.  <span data-ttu-id="bc14a-284">キーボードの方向キーを使用して下にスクロールします (少し下にスクロールして、次の行に移動する必要があります)。</span><span class="sxs-lookup"><span data-stu-id="bc14a-284">Use the arrow keys on your keyboard to scroll down (you will need to scroll down a little way), to reach the line containing":</span></span>

        <span data-ttu-id="bc14a-285">"**\<ADD DEVICE CONNECTION STRING HERE>**".</span><span class="sxs-lookup"><span data-stu-id="bc14a-285">"**\<ADD DEVICE CONNECTION STRING HERE>**".</span></span>

    2. <span data-ttu-id="bc14a-286">前にメモした **デバイス接続文字列** を使用して、**角かっこを含め** た代替行を指定します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-286">Substitute line, **including the brackets**, with the **Device Connection String** you have noted earlier.</span></span>

7. <span data-ttu-id="bc14a-287">接続文字列を設定した状態で、キーボードの **Ctrl + X** キーを押してファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-287">With your Connection String in place, on your keyboard, press the **Ctrl-X** keys to save the file.</span></span> <span data-ttu-id="bc14a-288">「 **Y**」と入力すると、確認を求めるメッセージが表示されます。次に、 **enter** キーを押して確認します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-288">It will ask you to confirm by typing **Y**. Then, press the **Enter** key, to confirm.</span></span> <span data-ttu-id="bc14a-289">通常の *ターミナル* に戻ります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-289">You will go back to the regular *Terminal*.</span></span> 

8. <span data-ttu-id="bc14a-290">これらのコマンドがすべて正常に実行されると、 **IoT Edge ランタイム** がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-290">Once these commands have all run successfully, you will have installed the **IoT Edge Runtime**.</span></span> <span data-ttu-id="bc14a-291">初期化されると、デバイスの電源が入るたびにランタイムが自動的に起動し、バックグラウンドで実行され、モジュールが **IoT Hub サービス** からデプロイされるのを待ちます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-291">Once initialized, the runtime will start on its own every time the device is powered up, and will sit in the background, waiting for modules to be deployed from the **IoT Hub Service**.</span></span>

9.  <span data-ttu-id="bc14a-292">次のコマンドラインを実行して、 *IoT Edge ランタイム* を初期化します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-292">Run the following command line to initialize the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="bc14a-293">Yaml ファイルまたは上記のセットアップに変更を加える場合は、 *ターミナル* 内で上記の再起動行をもう一度実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-293">If you make changes to your .yaml file, or the above setup, you will need to run the above restart line again, within *Terminal*.</span></span>

10. <span data-ttu-id="bc14a-294">次のコマンドラインを実行して、 *IoT Edge ランタイム* の状態を確認します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-294">Check the *IoT Edge Runtime* status by running the following command line.</span></span> <span data-ttu-id="bc14a-295">ランタイムは、状態が [ **アクティブ] (実行中)** の緑色のテキストで表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-295">The runtime should appear with the status **active (running)** in green text.</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

11. <span data-ttu-id="bc14a-296">**Ctrl + C** キーを押して、[状態] ページを終了します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-296">Press the **Ctrl-C** keys, to exit the status page.</span></span> <span data-ttu-id="bc14a-297">次のコマンドを入力して、 *IoT Edge ランタイム* がコンテナーを正しくプルしていることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-297">You can verify that the *IoT Edge Runtime* is pulling the containers correctly by typing the following command:</span></span>

    ```bash
        sudo docker ps
    ```

12. <span data-ttu-id="bc14a-298">2つのコンテナーを含むリストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-298">A list with two (2) containers should appear.</span></span> <span data-ttu-id="bc14a-299">これらは、IoT Hub サービス (edgeAgent および edgeHub) によって自動的に作成される既定のモジュールです。</span><span class="sxs-lookup"><span data-stu-id="bc14a-299">These are the default modules that are automatically created by the IoT Hub Service (edgeAgent and edgeHub).</span></span> <span data-ttu-id="bc14a-300">独自のモジュールを作成してデプロイすると、既定のモジュールの下にこの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-300">Once you create and deploy your own modules, they will appear in this list, underneath the default ones.</span></span>

## <a name="chapter-6---install-the-extensions"></a><span data-ttu-id="bc14a-301">Chapter 6-拡張機能のインストール</span><span class="sxs-lookup"><span data-stu-id="bc14a-301">Chapter 6 - Install the extensions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bc14a-302">Windows 10 コンピューターでは、次のいくつかの章 (6-9) が実行されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-302">The next few Chapters (6-9) are to be performed on your Windows 10 machine.</span></span>

1. <span data-ttu-id="bc14a-303">**VS Code** を開きます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-303">Open **VS Code**.</span></span>

2. <span data-ttu-id="bc14a-304">VS Code の左側のバーにある [ **拡張機能** (四角)] ボタンをクリックして、[ **拡張機能] パネル** を開きます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-304">Click on the **Extensions** (square) button on the left bar of VS Code, to open the **Extensions panel**.</span></span>

3. <span data-ttu-id="bc14a-305">次の図に示すように、次の拡張機能を検索してインストールします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-305">Search for, and install, the following extensions (as shown in the image below):</span></span>

    1. <span data-ttu-id="bc14a-306">Azure IoT Edge</span><span class="sxs-lookup"><span data-stu-id="bc14a-306">Azure IoT Edge</span></span>
    2. <span data-ttu-id="bc14a-307">Azure IoT ツールキット</span><span class="sxs-lookup"><span data-stu-id="bc14a-307">Azure IoT Toolkit</span></span>
    3. <span data-ttu-id="bc14a-308">Docker</span><span class="sxs-lookup"><span data-stu-id="bc14a-308">Docker</span></span>   

    ![コンテナーを作成する](images/AzureLabs-Lab313-24.png)

4. <span data-ttu-id="bc14a-310">拡張機能がインストールされたら、VS Code を閉じてから開き直します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-310">Once the extensions are installed, close and re-open VS Code.</span></span>

5. <span data-ttu-id="bc14a-311">さらに VS Code 開いて、[   >  **統合ターミナル** の表示] に移動します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-311">With VS Code open once more, navigate to **View** > **Integrated terminal**.</span></span>

6. <span data-ttu-id="bc14a-312">次に、 **Cookiecutter** をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-312">You will now install **Cookiecutter**.</span></span> <span data-ttu-id="bc14a-313">ターミナルで、次の bash コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-313">In the terminal run the following bash command:</span></span>

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > <span data-ttu-id="bc14a-314">[!ヒント] このコマンドで問題が発生した場合は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-314">[!HINT] If you have trouble with this command:</span></span> 
    >1. <span data-ttu-id="bc14a-315">VS Code、またはコンピューターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-315">Restart VS Code, and/ or your computer.</span></span>
    >2. <span data-ttu-id="bc14a-316">**VS Code ターミナル** を、python のインストールに使用している **もの (特** に、python 環境がコンピューターに既にインストールされている場合) に切り替える必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-316">It might be necessary to switch the **VS Code Terminal** to the one you have been using to install Python, i.e. **Powershell** (especially in case the Python environment was already installed on your machine).</span></span> <span data-ttu-id="bc14a-317">ターミナルを開いた状態で、ターミナルの右側にドロップダウンメニューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-317">With the Terminal open, you will find the drop down menu on the right side of the Terminal.</span></span>
     <span data-ttu-id="bc14a-318">![コンテナーを作成する](images/AzureLabs-Lab313-24b.png)</span><span class="sxs-lookup"><span data-stu-id="bc14a-318">![Create your container](images/AzureLabs-Lab313-24b.png)</span></span> 
    >3. <span data-ttu-id="bc14a-319">**Python** インストールパスが **環境変数** としてコンピューターに追加されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-319">Make sure the **Python** installation path is added as **Environment Variable** on your machine.</span></span> <span data-ttu-id="bc14a-320">Cookiecutter は同じ場所のパスの一部にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-320">Cookiecutter should be part of the same location path.</span></span> <span data-ttu-id="bc14a-321">[環境変数の詳細につい](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx)ては、このリンクに従ってください。</span><span class="sxs-lookup"><span data-stu-id="bc14a-321">Please follow this [link for more information on Environment Variables](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span></span> 

7. <span data-ttu-id="bc14a-322">**Cookiecutter** のインストールが完了したら、コンピューターを再起動して、 **Cookiecutter** がシステムの環境内でコマンドとして認識されるようにします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-322">Once **Cookiecutter** has finished installing, you should restart your machine, so that **Cookiecutter** is recognized as a command, within your System's environment.</span></span>

## <a name="chapter-7---create-your-container-solution"></a><span data-ttu-id="bc14a-323">第7章-コンテナーソリューションを作成する</span><span class="sxs-lookup"><span data-stu-id="bc14a-323">Chapter 7 - Create your container solution</span></span>

<span data-ttu-id="bc14a-324">この時点で、モジュールを使用してコンテナーを作成し、 *Container Registry* にプッシュする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-324">At this point, you need to create the container, with the module, to be pushed into the *Container Registry*.</span></span> <span data-ttu-id="bc14a-325">コンテナーをプッシュしたら、 *IoT Hub Edge* サービスを使用して、 *IoT Edge ランタイム* を実行しているデバイスにデプロイします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-325">Once you have pushed your container, you will use the *IoT Hub Edge* Service to deploy it to your device, which is running the *IoT Edge runtime*.</span></span>

1. <span data-ttu-id="bc14a-326">VS Code で、[   >  **コマンドパレット** の表示] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-326">From VS Code, click **View** > **Command palette**.</span></span>

2. <span data-ttu-id="bc14a-327">パレットで、[ **Azure IoT Edge の新しい IoT Edge ソリューション**] を検索して実行します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-327">In the palette, search and run **Azure IoT Edge: New Iot Edge Solution**.</span></span>

3. <span data-ttu-id="bc14a-328">ソリューションを作成する場所を参照します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-328">Browse into a location where you want to create your solution.</span></span> <span data-ttu-id="bc14a-329">場所を受け入れるには、 **enter** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-329">Press the **Enter** key, to accept the location.</span></span>

4. <span data-ttu-id="bc14a-330">ソリューションに名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-330">Give a name to your solution.</span></span> <span data-ttu-id="bc14a-331">入力した名前を確認するには、 **enter** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-331">Press the **Enter** key, to confirm your provided name.</span></span>

5. <span data-ttu-id="bc14a-332">これで、ソリューションのテンプレートフレームワークを選択するように求められます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-332">Now you will be prompted to choose the template framework for your solution.</span></span> <span data-ttu-id="bc14a-333">[ **Python モジュール**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-333">Click **Python Module**.</span></span> <span data-ttu-id="bc14a-334">この選択を確定するには、 **enter** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-334">Press the **Enter** key, to confirm this choice.</span></span>

6. <span data-ttu-id="bc14a-335">モジュールに名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-335">Give a name to your module.</span></span> <span data-ttu-id="bc14a-336">**Enter** キーを押して、モジュールの名前を確認します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-336">Press the **Enter** key, to confirm the name of your module.</span></span> <span data-ttu-id="bc14a-337">後で使用するため、モジュール名のメモ (メモ帳を使用) を必ず実行してください。</span><span class="sxs-lookup"><span data-stu-id="bc14a-337">Make sure to take a note (with your Notepad) of the module name, as it is used later.</span></span>

7. <span data-ttu-id="bc14a-338">作成済みの *Docker イメージリポジトリ* アドレスがパレットに表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-338">You will notice a pre-built *Docker Image Repository* address will appear on the palette.</span></span> <span data-ttu-id="bc14a-339">次のようになります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-339">It will look like:</span></span>

    <span data-ttu-id="bc14a-340">**localhost: 5000/-モジュールの名前-**。</span><span class="sxs-lookup"><span data-stu-id="bc14a-340">**localhost:5000/-THE NAME OF YOUR MODULE-**.</span></span> 

8. <span data-ttu-id="bc14a-341">**Localhost: 5000** を削除し、その場所で、 **Container Registry サービス** を作成するときにメモした *Container Registry* **Login サーバー** のアドレスを挿入します ([手順8では、第2章を](#chapter-2---the-container-registry-service)参照してください)。</span><span class="sxs-lookup"><span data-stu-id="bc14a-341">Delete **localhost:5000**, and in its place insert the *Container Registry* **Login Server** address, which you noted when creating the **Container Registry Service** ([in step 8, of Chapter 2](#chapter-2---the-container-registry-service)).</span></span> <span data-ttu-id="bc14a-342">アドレスを確認するには、 **enter** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-342">Press the **Enter** key, to confirm the address.</span></span>

9. <span data-ttu-id="bc14a-343">この時点で、Python モジュールのテンプレートを含むソリューションが作成され、その構造が画面の左側の [ **探索] タブ**(VS Code) に表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-343">At this point, the solution containing the template for your Python module will be created and its structure will be displayed in the **Explore Tab**, of VS Code, on the left side of the screen.</span></span> <span data-ttu-id="bc14a-344">[ **探索] タブ** が開いていない場合は、左側のバーの一番上にあるボタンをクリックして開くことができます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-344">If the **Explore Tab** is not open, you can open it by clicking the top-most button, in the bar on the left.</span></span>

    ![コンテナーを作成する](images/AzureLabs-Lab313-25.png)

10. <span data-ttu-id="bc14a-346">この章の最後の手順では、[**探索] タブ** 内から、 **env ファイル** をクリックして開き、 *Container Registry* **ユーザー名** と **パスワード** を追加します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-346">The last step for this Chapter, is to click and open the **.env file**, from within the **Explore Tab**, and add your *Container Registry* **username** and **password**.</span></span> <span data-ttu-id="bc14a-347">このファイルは git によって無視されますが、コンテナーを構築すると、 **Container Registry サービス** にアクセスするための資格情報が設定されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-347">This file is ignored by git, but on building the container, will set the credentials to access the **Container Registry Service**.</span></span>

    ![コンテナーを作成する](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a><span data-ttu-id="bc14a-349">章 8-コンテナーソリューションの編集</span><span class="sxs-lookup"><span data-stu-id="bc14a-349">Chapter 8 - Editing your container solution</span></span>

<span data-ttu-id="bc14a-350">次のファイルを更新して、コンテナーソリューションを完成させます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-350">You will now complete the container solution, by updating the following files:</span></span>

- <span data-ttu-id="bc14a-351">*<span></span> .py* python スクリプト。</span><span class="sxs-lookup"><span data-stu-id="bc14a-351">*main<span></span>.py* python script.</span></span>
- <span data-ttu-id="bc14a-352">*requirements.txt*。</span><span class="sxs-lookup"><span data-stu-id="bc14a-352">*requirements.txt*.</span></span>
- <span data-ttu-id="bc14a-353">*deployment.template.js* します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-353">*deployment.template.json*.</span></span>
- <span data-ttu-id="bc14a-354">*Dockerfile. amd64*</span><span class="sxs-lookup"><span data-stu-id="bc14a-354">*Dockerfile.amd64*</span></span>

<span data-ttu-id="bc14a-355">次に、python スクリプトによって使用される *images* フォルダーを作成し、 *Custom Vision モデル* と照合するイメージを確認します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-355">You will then create the *images* folder, used by the python script to check for images to match against your *Custom Vision model*.</span></span> <span data-ttu-id="bc14a-356">最後に、モデルを読みやすくするために *labels.txt* ファイルを追加し、モデルとしてモデルの *pb* ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-356">Lastly, you will add the *labels.txt* file, to help read your model, and the *model.pb* file, which is your model.</span></span>

1. <span data-ttu-id="bc14a-357">VS Code 開いた状態で、モジュールフォルダーに移動し、 **<span></span> .py** という名前のスクリプトを探します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-357">With VS Code open, navigate to your module folder, and look for the script called **main<span></span>.py**.</span></span> <span data-ttu-id="bc14a-358">これをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-358">Double-click to open it.</span></span>

2. <span data-ttu-id="bc14a-359">ファイルの内容を削除し、次のコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-359">Delete the content of the file and insert the following code:</span></span>

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  <span data-ttu-id="bc14a-360">**requirements.txt** という名前のファイルを開き、その内容を次の内容に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-360">Open the file called **requirements.txt**, and substitute its content with the following:</span></span>

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  <span data-ttu-id="bc14a-361">deployment.template.jsという名前のファイルを **で** 開き、次のガイドラインに従って内容を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-361">Open the file called **deployment.template.json**, and substitute its content following the below guideline:</span></span>

    1. <span data-ttu-id="bc14a-362">独自の一意の JSON 構造があるため、(例をコピーするのではなく) 手作業で編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-362">Because you will have your own, unique, JSON structure, you will need to edit it by hand (rather than copying an example).</span></span> <span data-ttu-id="bc14a-363">これを簡単に行うには、次の図をガイドとして使用します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-363">To make this easy, use the below image as a guide.</span></span>
    2. <span data-ttu-id="bc14a-364">異なる領域が表示されますが、 **変更すべきではない領域は黄色で強調表示され** ます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-364">Areas which will look different to yours, but which you **should NOT change are highlighted yellow**.</span></span>
    3. <span data-ttu-id="bc14a-365">**削除する必要があるセクションは、赤で強調表示されています。**</span><span class="sxs-lookup"><span data-stu-id="bc14a-365">**Sections which you need to delete, are a highlighted red.**</span></span>
    4. <span data-ttu-id="bc14a-366">正しい角かっこを削除し、コンマも削除するように注意してください。</span><span class="sxs-lookup"><span data-stu-id="bc14a-366">Be careful to delete the correct brackets, and also remove the commas.</span></span>

        ![コンテナーを作成する](images/AzureLabs-Lab313-27.png)

    5. <span data-ttu-id="bc14a-368">完成した JSON は次の図のようになります (ただし、独自の違いがあります。 *ユーザー名/パスワード/モジュール名/モジュール参照*)。</span><span class="sxs-lookup"><span data-stu-id="bc14a-368">The completed JSON should look like the following image (though, with your unique differences: *username/password/module name/module references*):</span></span>

        ![コンテナーを作成する](images/AzureLabs-Lab313-28.png)

5.  <span data-ttu-id="bc14a-370">**Dockerfile. amd64** という名前のファイルを開き、その内容を次のように置き換えます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-370">Open the file called **Dockerfile.amd64**, and substitute its content with the following:</span></span>

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  <span data-ttu-id="bc14a-371">[ **モジュール** ] の下にあるフォルダー (前の例で指定した名前が付いています。さらに下の例では、 *python モジュール* と呼ばれます) を右クリックし、[ **新しいフォルダー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-371">Right-click on the folder beneath **modules** (it will have the name you provided previously; in the example further down, it is called *pythonmodule*), and click on **New Folder**.</span></span> <span data-ttu-id="bc14a-372">フォルダーに **画像** の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-372">Name the folder **images**.</span></span>

7.  <span data-ttu-id="bc14a-373">フォルダー内に、マウスまたはキーボードを含むいくつかのイメージを追加します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-373">Inside the folder, add some images containing mouse or keyboard.</span></span> <span data-ttu-id="bc14a-374">これらの画像は、このモデルによって分析されるイメージになります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-374">Those will be the images that will be analyzed by the Tensorflow model.</span></span>

    > [!WARNING]
    > <span data-ttu-id="bc14a-375">独自のモデルを使用している場合は、独自のモデルデータを反映するように変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-375">If you are using your own model, you will need to change this to reflect your own models data.</span></span>

8.  <span data-ttu-id="bc14a-376">次に、[第1章](#chapter-1---retrieve-the-custom-vision-model)で、以前にダウンロードした (または独自の **Custom Vision Service** から作成した) モデルフォルダーから、 **labels.txt** と **モデルの pb** ファイルを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-376">You will now need to retrieve the **labels.txt** and **model.pb** files from the model folder, which you previous downloaded (or created from your own **Custom Vision Service**), in [Chapter 1](#chapter-1---retrieve-the-custom-vision-model).</span></span> <span data-ttu-id="bc14a-377">ファイルを作成したら、他のファイルと共にソリューション内に配置します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-377">Once you have the files, place them within your solution, alongside the other files.</span></span> <span data-ttu-id="bc14a-378">最終的な結果は次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-378">The final result should look like the image below:</span></span>

    ![コンテナーを作成する](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a><span data-ttu-id="bc14a-380">第9章-ソリューションをコンテナーとしてパッケージ化する</span><span class="sxs-lookup"><span data-stu-id="bc14a-380">Chapter 9 - Package the solution as a container</span></span>

1.  <span data-ttu-id="bc14a-381">これで、ファイルをコンテナーとして "パッケージ化" し、 **Azure Container Registry** にプッシュできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="bc14a-381">You are now ready to "package" your files as a container and push it to your **Azure Container Registry**.</span></span> <span data-ttu-id="bc14a-382">VS Code で、*統合ターミナル*(  >  **統合** ターミナルまたは **Ctrl** を表示) を開き、次の行を使用して + **\`** **Docker** にログインします (コマンドの値は、 **Azure Container Registry (ACR)** の資格情報に置き換えてください)。</span><span class="sxs-lookup"><span data-stu-id="bc14a-382">Within VS Code, open the *Integrated Terminal* (**View** > **Integrated Terminal** or **Ctrl**+**\`**), and use the following line to login to **Docker** (substitute the values of the command with the credentials of your **Azure Container Registry (ACR)**):</span></span>

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. <span data-ttu-id="bc14a-383">**deployment.template.js** ファイルを右クリックし、[**ビルド IoT Edge ソリューション**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-383">Right-click on the file **deployment.template.json**, and click **Build IoT Edge Solution**.</span></span> <span data-ttu-id="bc14a-384">このビルドプロセスは、(デバイスによっては) かなりの時間がかかります。そのため、待機する準備を整えてください。</span><span class="sxs-lookup"><span data-stu-id="bc14a-384">This build process takes quite some time (depending on your device), so be prepared to wait.</span></span> <span data-ttu-id="bc14a-385">ビルドプロセスが完了すると、[ **config**] という名前の新しいフォルダー内 **にファイルのdeployment.js** が作成されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-385">After the build process finishes, a **deployment.json** file will have been created inside a new folder called **config**.</span></span>

    ![デプロイの作成](images/AzureLabs-Lab313-30.png)

3. <span data-ttu-id="bc14a-387">もう一度 **コマンドパレット** を開き、「 **Azure: Sign In**」を検索します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-387">Open the **Command Palette** again, and search for **Azure: Sign In**.</span></span> <span data-ttu-id="bc14a-388">Azure アカウントの資格情報を使用して、画面の指示に従います。VS Code には、 *コピーして開く* オプションが用意されています。これにより、すぐに必要なデバイスコードがコピーされ、既定の web ブラウザーが開きます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-388">Follow the prompts using your Azure Account credentials; VS Code will provide you with an option to *Copy and Open*, which will copy the device code you will soon need, and open your default web browser.</span></span> <span data-ttu-id="bc14a-389">プロンプトが表示されたら、デバイスコードを貼り付けて、コンピューターを認証します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-389">When asked, paste the device code, to authenticate your machine.</span></span>

    ![コピーして開く](images/AzureLabs-Lab313-31.png)

4. <span data-ttu-id="bc14a-391">サインインすると、[ *探索* ] パネルの下部に [ **Azure IoT Hub デバイス**] という新しいセクションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-391">Once signed in you will notice, on the bottom side of the *Explore* panel, a new section called **Azure IoT Hub Devices**.</span></span> <span data-ttu-id="bc14a-392">展開するには、このセクションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-392">Click this section to expand it.</span></span>

    ![エッジデバイス](images/AzureLabs-Lab313-32.png)

5. <span data-ttu-id="bc14a-394">デバイスがここにない場合は、[ *Azure IoT Hub デバイス*] を右クリックし、[ **IoT Hub 接続文字列の設定**] をクリックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-394">If your device is not here, you will need to right-click *Azure IoT Hub Devices*, and then click **Set IoT Hub Connection String**.</span></span> <span data-ttu-id="bc14a-395">**コマンドパレット**(VS Code の上部) で、*接続文字列* を入力するように求められます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-395">You will then see that the **Command Palette** (at the top of VS Code), will prompt you to input your *Connection String*.</span></span> <span data-ttu-id="bc14a-396">これは、[章 3](#chapter-3---the-iot-hub-service)の最後にメモした *接続文字列* です。</span><span class="sxs-lookup"><span data-stu-id="bc14a-396">This is the *Connection String* you noted down at the end of [Chapter 3](#chapter-3---the-iot-hub-service).</span></span> <span data-ttu-id="bc14a-397">で文字列を **コピーしたら、enter キーを** 押します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-397">Press the **Enter** key, once you have copied the string in.</span></span>    

6. <span data-ttu-id="bc14a-398">デバイスが読み込まれ、表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-398">Your device should load, and appear.</span></span> <span data-ttu-id="bc14a-399">デバイス名を右クリックし、[ **単一デバイスの展開の作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-399">Right-click on the device name, and then click, **Create Deployment for Single Device**.</span></span>

    ![デプロイの作成](images/AzureLabs-Lab313-33b.png)

7. <span data-ttu-id="bc14a-401">*ファイルエクスプローラー* のプロンプトが表示されます。ここで、 **config** フォルダーに移動し、ファイル **のdeployment.js** を選択します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-401">You will get a *File Explorer* prompt, where you can navigate to the **config** folder, and then select the **deployment.json** file.</span></span> <span data-ttu-id="bc14a-402">そのファイルを選択した状態で、[ **エッジ配置マニフェストの選択** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-402">With that file selected, click the **Select Edge Deployment Manifest** button.</span></span>

    ![デプロイの作成](images/AzureLabs-Lab313-34.png)

8. <span data-ttu-id="bc14a-404">この時点で、 **Azure Container Registry** からコンテナーをモジュールとしてデプロイし、実際にデバイスにデプロイするためのマニフェストを **IoT Hub サービス** に提供しました。</span><span class="sxs-lookup"><span data-stu-id="bc14a-404">At this point you have provided your **IoT Hub Service** with the manifest for it to deploy your container, as a module, from your **Azure Container Registry**, effectively deploying it to your device.</span></span>

9. <span data-ttu-id="bc14a-405">デバイスから IoT Hub に送信されたメッセージを表示するには、[**エクスプローラー** ] パネルの [ **Azure IoT Hub デバイス**] セクションでデバイス名をもう一度右クリックし、[**監視 D2C メッセージの開始**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-405">To view the messages sent from your device to the IoT Hub, right-click again on your device name in the **Azure IoT Hub Devices** section, in the **Explorer** panel, and click on **Start Monitoring D2C Message**.</span></span> <span data-ttu-id="bc14a-406">デバイスから送信されたメッセージが VS ターミナルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-406">The messages sent from your device should appear in the VS Terminal.</span></span> <span data-ttu-id="bc14a-407">しばらく時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-407">Be patient, as this may take some time.</span></span> <span data-ttu-id="bc14a-408">デバッグについては、次の章を参照してください。配置が成功したかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="bc14a-408">See the next Chapter for debugging, and checking if deployment was successful.</span></span>

<span data-ttu-id="bc14a-409">このモジュールは、各イテレーションで **images** フォルダー内のイメージを反復処理し、それらを分析します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-409">This module will now iterate between the images in the **images** folder and analyze them, with each iteration.</span></span> <span data-ttu-id="bc14a-410">これは明らかに、基本的な機械学習モデルを使用して IoT Edge デバイス環境で動作させる方法のデモにすぎません。</span><span class="sxs-lookup"><span data-stu-id="bc14a-410">This is obviously just a demonstration of how to get the basic machine learning model to work in an IoT Edge device environment.</span></span> 

<span data-ttu-id="bc14a-411">この例の機能を拡張するには、いくつかの方法を実行します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-411">To expand the functionality of this example, you could proceed in several ways.</span></span> <span data-ttu-id="bc14a-412">1つの方法として、コンテナーにいくつかのコードを含め、デバイスに接続されている web カメラから写真をキャプチャして、images フォルダーに保存する方法があります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-412">One way could be including some code in the container, that captures photos from a webcam that is connected to the device, and saves the images in the images folder.</span></span> 

<span data-ttu-id="bc14a-413">別の方法として、IoT デバイスからコンテナーにイメージをコピーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-413">Another way could be copying the images from the IoT device into the container.</span></span> <span data-ttu-id="bc14a-414">これを行う実際の方法として、IoT デバイスターミナルで次のコマンドを実行します (たとえば、プロセスを自動化する場合は、小規模なアプリでジョブを実行できます)。</span><span class="sxs-lookup"><span data-stu-id="bc14a-414">A practical way to do that is to run the following command in the IoT device Terminal (perhaps a small app could do the job, if you wished to automate the process).</span></span> <span data-ttu-id="bc14a-415">このコマンドは、ファイルが格納されているフォルダーの場所から手動で実行することでテストできます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-415">You can test this command by running it manually from the folder location where your files are stored:</span></span>

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a><span data-ttu-id="bc14a-416">第10章-IoT Edge ランタイムのデバッグ</span><span class="sxs-lookup"><span data-stu-id="bc14a-416">Chapter 10 - Debugging the IoT Edge Runtime</span></span>

<span data-ttu-id="bc14a-417">次に示すのは、 **Ubuntu デバイス** から *IoT Edge ランタイム* のメッセージングアクティビティを監視およびデバッグするのに役立つコマンドラインとヒントの一覧です。</span><span class="sxs-lookup"><span data-stu-id="bc14a-417">The following are a list of command lines, and tips, to help you monitor and debug the messaging activity of the *IoT Edge Runtime*, from your **Ubuntu device**.</span></span> 

- <span data-ttu-id="bc14a-418">次のコマンドラインを実行して、 *IoT Edge ランタイム* の状態を確認します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-418">Check the *IoT Edge Runtime* status by running the following command line:</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > <span data-ttu-id="bc14a-419">ステータスの表示を完了するには、 **Ctrl + C** キーを押してください。</span><span class="sxs-lookup"><span data-stu-id="bc14a-419">Remember to press **Ctrl + C**, to finish viewing the status.</span></span>

- <span data-ttu-id="bc14a-420">現在展開されているコンテナーを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-420">List the containers that are currently deployed.</span></span> <span data-ttu-id="bc14a-421">*IoT Hub サービス* がコンテナーを正常にデプロイした場合は、次のコマンドラインを実行すると表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-421">If the *IoT Hub Service* has deployed the containers successfully, they will be displayed by running the following command line:</span></span>

    ```bash
        sudo iotedge list
    ```

    <span data-ttu-id="bc14a-422">または</span><span class="sxs-lookup"><span data-stu-id="bc14a-422">Or</span></span>

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > <span data-ttu-id="bc14a-423">上記は、モジュールが正常にデプロイされているかどうかを確認するための優れた方法であり、一覧に表示されます。それ以外の場合は、 *edgeHub* と *edgeAgent\*\*\*のみ*\* が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-423">The above is a good way to check whether your module has been deployed successfully, as it will appear in the list; you will otherwise **only** see the *edgeHub* and *edgeAgent*.</span></span>

- <span data-ttu-id="bc14a-424">コンテナーのコードログを表示するには、次のコマンドラインを実行します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-424">To display the code logs of a container, run the following command line:</span></span>

    ```bash
        journalctl -u iotedge
    ```

<span data-ttu-id="bc14a-425">**IoT Edge ランタイムを管理するための便利なコマンド:**</span><span class="sxs-lookup"><span data-stu-id="bc14a-425">**Useful commands to manage the IoT Edge Runtime:**</span></span>

-  <span data-ttu-id="bc14a-426">ホスト内のすべてのコンテナーを削除するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-426">To delete all containers in the host:</span></span>

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  <span data-ttu-id="bc14a-427">*IoT Edge ランタイム* を停止するには:</span><span class="sxs-lookup"><span data-stu-id="bc14a-427">To stop the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a><span data-ttu-id="bc14a-428">第11章-Create Table Service</span><span class="sxs-lookup"><span data-stu-id="bc14a-428">Chapter 11 - Create Table Service</span></span> 

<span data-ttu-id="bc14a-429">Azure Portal に戻ります。ここでは、ストレージリソースを作成して、Azure Tables サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-429">Navigate back to your Azure Portal, where you will create an Azure Tables Service, by creating a Storage resource.</span></span>

1. <span data-ttu-id="bc14a-430">まだサインインしていない場合は、 [Azure Portal](https://portal.azure.com)にログインします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-430">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="bc14a-431">ログインしたら、左上隅にある [ **リソースの作成**] をクリックし、[ **ストレージアカウント**] を検索して、 **enter** キーを押して検索を開始します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-431">Once logged in, click on **Create a resource**, in the top left corner, and search for **Storage account**, and press the **Enter** key, to start the search.</span></span>

3. <span data-ttu-id="bc14a-432">表示されたら、一覧から [ **ストレージアカウント-blob、file、table、queue** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-432">Once it has appeared, click **Storage account - blob, file, table, queue** from the list.</span></span>

    ![ストレージアカウントの検索](images/AzureLabs-Lab313-35.png)

4. <span data-ttu-id="bc14a-434">新しいページには、 **ストレージアカウント** サービスの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-434">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="bc14a-435">このプロンプトの左下にある [ **作成** ] ボタンをクリックして、このサービスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-435">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![ストレージインスタンスの作成](images/AzureLabs-Lab313-36.png)

5. <span data-ttu-id="bc14a-437">[ **作成**] をクリックすると、パネルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-437">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="bc14a-438">このサービスインスタンスに必要な **名前** を挿入します (*すべて小文字にする必要があり* ます)。</span><span class="sxs-lookup"><span data-stu-id="bc14a-438">Insert your desired **Name** for this Service instance (*must be all lowercase*).</span></span>

    2. <span data-ttu-id="bc14a-439">[ **デプロイモデル**] で、[ **リソースマネージャー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-439">For **Deployment model**, click **Resource manager**.</span></span>

    3. <span data-ttu-id="bc14a-440">[ **アカウントの種類**] で、ドロップダウンメニューを使用して、[ **ストレージ (汎用 v1)**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-440">For **Account kind**, using the dropdown menu, click **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="bc14a-441">適切な **場所** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-441">Click an appropriate **Location**.</span></span>
    
    5. <span data-ttu-id="bc14a-442">[ **レプリケーション** ] ドロップダウンメニューで、[ **読み取りアクセス-geo 冗長ストレージ (RA-GRS)**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-442">For the **Replication** dropdown menu, click **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6. <span data-ttu-id="bc14a-443">[ **パフォーマンス**] で [ **標準**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-443">For **Performance**, click **Standard**.</span></span>

    7. <span data-ttu-id="bc14a-444">[ **安全な転送が必要** ] セクションで、[ **無効**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-444">Within the **Secure transfer required** section, click **Disabled**.</span></span>

    8. <span data-ttu-id="bc14a-445">[ **サブスクリプション** ] ドロップダウンメニューから、適切なサブスクリプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-445">From the **Subscription** dropdown menu, click an appropriate subscription.</span></span>

    9. <span data-ttu-id="bc14a-446">リソースグループを選択するか、新しい **リソースグループ** を作成します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-446">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="bc14a-447">リソースグループを使用すると、Azure 資産のコレクションの監視、アクセスの制御、プロビジョニング、管理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-447">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="bc14a-448">1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのコースなど) を共通のリソースグループに保持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-448">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="bc14a-449">Azure リソースグループの詳細については、 [リソースグループの管理方法に関するリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc14a-449">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="bc14a-450">このオプションが選択されている場合は、[ **仮想ネットワーク** ] を [ **無効**] のままにします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-450">Leave **Virtual networks** as **Disabled**, if this is an option for you.</span></span>

    11. <span data-ttu-id="bc14a-451">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-451">Click **Create**.</span></span>

        ![ストレージの詳細の入力](images/AzureLabs-Lab313-37.png)

6. <span data-ttu-id="bc14a-453">[ **作成**] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-453">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

7. <span data-ttu-id="bc14a-454">サービスインスタンスが作成されると、ポータルに通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-454">A notification will appear in the Portal once the Service instance is created.</span></span> <span data-ttu-id="bc14a-455">通知をクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-455">Click on the notifications to explore your new Service instance.</span></span>

    ![新しいストレージ通知](images/AzureLabs-Lab313-38.png)

8. <span data-ttu-id="bc14a-457">通知の [ **リソースに移動** ] ボタンをクリックすると、新しいストレージサービスインスタンスの概要ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-457">Click the **Go to resource** button in the notification, and you will be taken to your new Storage Service instance overview page.</span></span>

    ![リソースにアクセス](images/AzureLabs-Lab313-39.png)

9. <span data-ttu-id="bc14a-459">[概要] ページで、右側にある [ **テーブル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-459">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![表](images/AzureLabs-Lab313-40.png)

10. <span data-ttu-id="bc14a-461">右側のパネルが変更され、 **テーブルサービス** 情報が表示されます。新しいテーブルを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-461">The panel on the right will change to show the **Table Service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="bc14a-462">これを行うには、左上隅にある [ **+ テーブル** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-462">Do this by clicking the **+ Table** button to the top-left corner.</span></span>

    ![テーブルを開く](images/AzureLabs-Lab313-41.png)

11. <span data-ttu-id="bc14a-464">新しいページが表示されます。ここには、 **テーブル名** を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-464">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="bc14a-465">これは、後の章で (Function App を作成し、Power BI)、アプリケーション内のデータを参照するために使用する名前です。</span><span class="sxs-lookup"><span data-stu-id="bc14a-465">This is the name you will use to refer to the data in your application in later Chapters (creating Function App, and Power BI).</span></span> <span data-ttu-id="bc14a-466">名前として **Iotmessages** を挿入し (このドキュメントで後ほど使用する場合はそのままにしておきます)、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-466">Insert **IoTMessages** as the name (you can choose your own, just remember it when used later in this document) and click **OK**.</span></span> 

12. <span data-ttu-id="bc14a-467">新しいテーブルが作成されると、 **テーブルサービス** のページ (下部) に表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-467">Once the new table has been created, you will be able to see it within the **Table Service** page (at the bottom).</span></span>

    ![新しいテーブルが作成されました](images/AzureLabs-Lab313-42.png)  

13. <span data-ttu-id="bc14a-469">次に、[ **アクセスキー** ] をクリックし、 **ストレージアカウント名** と **キー** のコピーを作成します (メモ帳を使用)。 **Azure Function App** を作成するときに、このコースの後半でこれらの値を使用します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-469">Now click on **Access keys** and take a copy of the **Storage account name** and **Key** (using your Notepad), you will use these values later in this course, when creating the **Azure Function App**.</span></span>

    ![新しいテーブルが作成されました](images/AzureLabs-Lab313-43.png) 

14. <span data-ttu-id="bc14a-471">左側のパネルを再び使用して、[ *Table Service* ] \ (テーブルサービス \) セクションまでスクロールし、[ **tables** (または新しいポータルでの **テーブルの参照**)] をクリックして、テーブルの **URL** (メモ帳を使用) のコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-471">Using the panel on the left again, scroll to the *Table Service* section, and click **Tables** (or **Browse Tables**, in newer Portals) and take a copy of the **Table URL** (using your Notepad).</span></span> <span data-ttu-id="bc14a-472">この値は、テーブルを **Power BI** アプリケーションにリンクするときに、このコースの後半で使用します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-472">You will use this value later in this course, when linking your table to your **Power BI** application.</span></span>

    ![新しいテーブルが作成されました](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a><span data-ttu-id="bc14a-474">第12章-Azure テーブルの完成</span><span class="sxs-lookup"><span data-stu-id="bc14a-474">Chapter 12 - Completing the Azure Table</span></span>

<span data-ttu-id="bc14a-475">**Table Service** ストレージアカウントのセットアップが完了したので、それにデータを追加します。これは、情報の格納と取得に使用されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-475">Now that your **Table Service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="bc14a-476">テーブルの編集は、 **Visual Studio** を使用して行うことができます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-476">The editing of your Tables can be done through **Visual Studio**.</span></span>

1. <span data-ttu-id="bc14a-477">(Visual Studio Code で **はなく**) **Visual Studio** を開きます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-477">Open **Visual Studio** (**not** Visual Studio Code).</span></span>

2. <span data-ttu-id="bc14a-478">メニューの [Cloud Explorer の **表示**] をクリックし  >  ます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-478">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![cloud explorer を開く](images/AzureLabs-Lab313-45.png)

3. <span data-ttu-id="bc14a-480">**Cloud Explorer** がドッキングされたアイテムとして開きます (読み込みに時間がかかる場合があります)。</span><span class="sxs-lookup"><span data-stu-id="bc14a-480">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="bc14a-481">*ストレージアカウント* の作成に使用したサブスクリプションが表示されない場合は、次のことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="bc14a-481">If the subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="bc14a-482">Azure Portal で使用したものと同じアカウントにログインします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-482">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="bc14a-483">[アカウント管理] ページからサブスクリプションを選択しました (アカウントの設定からフィルターを適用する必要がある場合があります)。</span><span class="sxs-lookup"><span data-stu-id="bc14a-483">Selected your subscription from the Account Management page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![サブスクリプションの検索](images/AzureLabs-Lab313-46.png)

4. <span data-ttu-id="bc14a-485">Azure cloud Services が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-485">Your Azure cloud Services will be shown.</span></span> <span data-ttu-id="bc14a-486">**ストレージアカウント** を検索し、左側の矢印をクリックしてアカウントを展開します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-486">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![ストレージアカウントを開く](images/AzureLabs-Lab313-47.png)

5. <span data-ttu-id="bc14a-488">展開されると、新しく作成された **ストレージアカウント** を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-488">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="bc14a-489">ストレージの左側にある矢印をクリックし、展開された後、[ **テーブル** ] を見つけて、その横にある矢印をクリックし、最後の章で作成した **テーブル** を表示します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-489">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="bc14a-490">**テーブル** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-490">Double-click your **Table**.</span></span>

6. <span data-ttu-id="bc14a-491">テーブルが Visual Studio ウィンドウの中央に開きます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-491">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="bc14a-492">[テーブル] アイコンをクリックし **+** ます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-492">Click the table icon with the **+** (plus) on it.</span></span>

    ![新しいテーブルの追加](images/AzureLabs-Lab313-48.png)

7. <span data-ttu-id="bc14a-494">*エンティティの追加* を求めるウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-494">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="bc14a-495">エンティティは1つだけ作成しますが、3つのプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-495">You will create only one entity, though it will have three properties.</span></span> <span data-ttu-id="bc14a-496">*Partitionkey* と *RowKey* は既に提供されています。これは、テーブルがデータを検索するために使用されるためです。</span><span class="sxs-lookup"><span data-stu-id="bc14a-496">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![パーティションキーと行キー](images/AzureLabs-Lab313-49.png)

8. <span data-ttu-id="bc14a-498">次の値を更新します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-498">Update the following values:</span></span>

    - <span data-ttu-id="bc14a-499">名前: **Partitionkey**、Value: **PK_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="bc14a-499">Name: **PartitionKey**, Value: **PK_IoTMessages**</span></span> 

    - <span data-ttu-id="bc14a-500">名前: **RowKey**、値: **RK_1_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="bc14a-500">Name: **RowKey**, Value: **RK_1_IoTMessages**</span></span> 

9. <span data-ttu-id="bc14a-501">次に、[*エンティティの追加*] ウィンドウの左下にある [**プロパティの追加**] をクリックし、次のプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-501">Then, click **Add property** (to the lower left of the *Add Entity* window) and add the following property:</span></span>

    - <span data-ttu-id="bc14a-502">\**Messagecontent\*\*\*文字列* として使用する場合は、値を空のままにします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-502">**MessageContent**, as a *string*, leave the Value empty.</span></span>

10. <span data-ttu-id="bc14a-503">テーブルは、次の図に示すものと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-503">Your table should match the one in the image below:</span></span>

    ![正しい値の追加](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > <span data-ttu-id="bc14a-505">このエンティティの行キーの番号が1である理由は、さらに多くのメッセージを追加することが必要になる可能性があるためです。このコースをさらに試してみることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-505">The reason why the entity has the number 1 in the row key, is because you might want to add more messages, should you desire to experiment further with this course.</span></span>

11. <span data-ttu-id="bc14a-506">完了したら [ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-506">Click **OK** when you are finished.</span></span> <span data-ttu-id="bc14a-507">これで、テーブルを使用する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="bc14a-507">Your table is now ready to be used.</span></span>

## <a name="chapter-13---create-an-azure-function-app"></a><span data-ttu-id="bc14a-508">第13章-Azure Function App の作成</span><span class="sxs-lookup"><span data-stu-id="bc14a-508">Chapter 13 - Create an Azure Function App</span></span> 

<span data-ttu-id="bc14a-509">ここでは、 *Azure Function App* を作成します。これは、前の章で作成した **Table** service に *IoT Edge* デバイスメッセージを格納するために、 *IoT Hub サービス* によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-509">It is now time to create an *Azure Function App*, which will be called by the *IoT Hub Service* to store the *IoT Edge* device messages in the **Table** Service, which you created in the previous Chapter.</span></span>

<span data-ttu-id="bc14a-510">まず、必要なライブラリを Azure 関数で読み込むことができるファイルを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-510">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="bc14a-511">**メモ帳** を開きます ( *Windows キー* を押して、*メモ帳* を入力します)。</span><span class="sxs-lookup"><span data-stu-id="bc14a-511">Open **Notepad** (press the *Windows Key*, and type *notepad*).</span></span>

    ![メモ帳を開く](images/AzureLabs-Lab313-51.png)

2.  <span data-ttu-id="bc14a-513">メモ帳を開いた状態で、次の JSON 構造を挿入します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-513">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="bc14a-514">これが完了したら、 **project.js** としてデスクトップに保存します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-514">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="bc14a-515">このファイルは、関数が使用するライブラリを定義します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-515">This file defines the libraries your function will use.</span></span> <span data-ttu-id="bc14a-516">NuGet を使用している場合は、見慣れた外観になります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-516">If you have used NuGet, it will look familiar.</span></span>
    
    > [!WARNING]
    > <span data-ttu-id="bc14a-517">名前が正しいことが重要です。ファイル拡張子 **.txt が付いていないことを** 確認します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-517">It is important that the naming is correct; ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="bc14a-518">参照については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc14a-518">See below for reference:</span></span>
    >
    > ![JSON 保存](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  <span data-ttu-id="bc14a-520">[Azure Portal](https://portal.azure.com) にログインします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-520">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="bc14a-521">ログインしたら、左上隅にある [ **リソースの作成** ] をクリックし、 **Function App** を検索して、 **enter** キーを押して検索します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-521">Once you are logged in, click on **Create a resource** in the top left corner, and search for **Function App**, and press the **Enter** key, to search.</span></span> <span data-ttu-id="bc14a-522">結果の [ *Function App* ] をクリックして、新しいパネルを開きます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-522">Click *Function App* from the results, to open a new panel.</span></span>

    ![function app の検索](images/AzureLabs-Lab313-53.png)

5.  <span data-ttu-id="bc14a-524">新しいパネルには、 **Function App** サービスの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-524">The new panel will provide a description of the **Function App** Service.</span></span> <span data-ttu-id="bc14a-525">このパネルの左下にある [ **作成** ] ボタンをクリックして、このサービスとの関連付けを作成します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-525">At the bottom left of this panel, click the **Create** button, to create an association with this Service.</span></span>

    ![function app インスタンス](images/AzureLabs-Lab313-54.png)

6.  <span data-ttu-id="bc14a-527">[ **作成**] をクリックしたら、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-527">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="bc14a-528">[ **アプリ名**] に、このサービスインスタンスに必要な名前を挿入します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-528">For **App name**, insert your desired name for this Service instance.</span></span>

    2. <span data-ttu-id="bc14a-529">**サブスクリプション** を選択します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-529">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="bc14a-530">適切な価格レベルを選択してください。 **Function App サービス** を初めて作成する場合は、free レベルをご利用いただけます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-530">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="bc14a-531">リソースグループを選択するか、新しい **リソースグループ** を作成します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-531">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="bc14a-532">リソースグループを使用すると、Azure 資産のコレクションの監視、アクセスの制御、プロビジョニング、管理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-532">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="bc14a-533">1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのコースなど) を共通のリソースグループに保持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-533">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="bc14a-534">Azure リソースグループの詳細については、 [リソースグループの管理方法に関するリンク](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc14a-534">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="bc14a-535">**OS** の場合は、[Windows] をクリックします。これは目的のプラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="bc14a-535">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="bc14a-536">**ホスティングプラン** を選択します (このチュートリアルでは、**従量課金プラン** を使用しています。</span><span class="sxs-lookup"><span data-stu-id="bc14a-536">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="bc14a-537">**場所** を選択します (前の手順で作成したストレージと同じ場所を選択します)。</span><span class="sxs-lookup"><span data-stu-id="bc14a-537">Select a **Location** (choose the same location as the storage you have built in the previous step)</span></span>

    8. <span data-ttu-id="bc14a-538">[ **ストレージ** ] セクションでは、 **前の手順で作成したストレージサービスを選択する必要があり** ます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-538">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="bc14a-539">このアプリで *Application Insights* は必要ありませ **ん。そのままにして** おいてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="bc14a-539">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="bc14a-540">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-540">Click **Create**.</span></span>

        ![新しいインスタンスの作成](images/AzureLabs-Lab313-55.png)

7.  <span data-ttu-id="bc14a-542">[ **作成**] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-542">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="bc14a-543">サービスインスタンスが作成されると、ポータルに通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-543">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![新しい通知](images/AzureLabs-Lab313-56.png)

9.  <span data-ttu-id="bc14a-545">デプロイが正常に完了したら (完了した)、通知をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-545">Click on the notification, once deployment is successful (has finished).</span></span>

10. <span data-ttu-id="bc14a-546">通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-546">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![リソースにアクセス](images/AzureLabs-Lab313-57.png)

11. <span data-ttu-id="bc14a-548">新しいパネルの左側で、[関数] の横にある **+** (プラス記号) アイコンをクリックして、新しい関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-548">In the left side of the new panel, click the **+** (plus) icon next to *Functions*, to create a new function.</span></span>

    ![新しい関数の追加](images/AzureLabs-Lab313-58.png)

12. <span data-ttu-id="bc14a-550">中央のパネル内に [ **関数** の作成] ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-550">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="bc14a-551">さらに下にスクロールし、[ **カスタム関数**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-551">Scroll down further, and click on **Custom function**.</span></span>

    ![カスタム関数](images/AzureLabs-Lab313-59.png)

13. <span data-ttu-id="bc14a-553">次のページを下にスクロールして、 **IoT Hub (イベントハブ)** を見つけ、クリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-553">Scroll down the next page, until you find **IoT Hub (Event Hub)**, then click on it.</span></span>

    ![カスタム関数](images/AzureLabs-Lab313-60.png)

14. <span data-ttu-id="bc14a-555">[ **IoT Hub (イベントハブ)** ] ブレードで、 **言語** を **C#** に設定し、[ **新規**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-555">In the **IoT Hub (Event Hub)** blade, set the **Language** to **C#** and then click on **new**.</span></span>

    ![カスタム関数](images/AzureLabs-Lab313-61.png)

15. <span data-ttu-id="bc14a-557">表示されるウィンドウで、 **IoT Hub** が選択されていることを確認し、 *IoT Hub* フィールドの名前が、前に作成した *IoT Hub サービス* の名前と一致することを確認します ([手順8の第3章を](#chapter-3---the-iot-hub-service)参照)。</span><span class="sxs-lookup"><span data-stu-id="bc14a-557">In the window that will appear, make sure that **IoT Hub** is selected and the name of the *IoT Hub* field corresponds with the name of your *IoT Hub Service* that you have created previously ([in step 8, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="bc14a-558">次に、[ **選択** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-558">Then click the **Select** button.</span></span>

    ![カスタム関数](images/AzureLabs-Lab313-62.png)

16. <span data-ttu-id="bc14a-560">[ **IoT Hub (イベントハブ)** ] ブレードに戻り、[ **作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-560">Back on the **IoT Hub (Event Hub)** blade, click on **Create**.</span></span>

    ![カスタム関数](images/AzureLabs-Lab313-63.png)

17. <span data-ttu-id="bc14a-562">関数エディターにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-562">You will be redirected to the function editor.</span></span>

    ![カスタム関数](images/AzureLabs-Lab313-64.png)

18. <span data-ttu-id="bc14a-564">その中のすべてのコードを削除し、次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-564">Delete all the code in it and replace it with the following:</span></span>

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. <span data-ttu-id="bc14a-565">次の変数を変更して、**ストレージアカウント** に含まれる適切な値 ([手順 11. および 13. の](#chapter-11---create-table-service)**テーブル** と **ストレージ** の値) に対応するようにします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-565">Change the following variables, so that they correspond to the appropriate values (**Table** and **Storage** values, from [step 11 and 13, respectively, of Chapter 11](#chapter-11---create-table-service)), that you will find in your **Storage Account**:</span></span>

    - <span data-ttu-id="bc14a-566">**tableName**。**ストレージアカウント** 内にある **テーブル** の名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-566">**tableName**, with the name of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="bc14a-567">**tableurl**。**ストレージアカウント** 内にある **テーブル** の url を使用します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-567">**tableURL**, with the URL of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="bc14a-568">**Storageaccountname**。 **ストレージアカウント** 名に対応する値の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-568">**storageAccountName**, with the name of the value corresponding with the name of your **Storage Account** name.</span></span>
    - <span data-ttu-id="bc14a-569">**storageAccountKey** には、前に作成したストレージサービスで取得したキーを使用します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-569">**storageAccountKey**, with the Key you have obtained in the Storage Service you have created previously.</span></span>

    ![カスタム関数](images/AzureLabs-Lab313-65.png)

20. <span data-ttu-id="bc14a-571">コードを配置したら、[ **保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-571">With the code in place, click **Save**.</span></span>

21. <span data-ttu-id="bc14a-572">次に、 **\<** ページの右側にある (矢印) アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-572">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![カスタム関数](images/AzureLabs-Lab313-66.png)

22. <span data-ttu-id="bc14a-574">パネルが右側からスライドします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-574">A panel will slide in from the right.</span></span> <span data-ttu-id="bc14a-575">そのパネルで [ **アップロード**] をクリックすると、 *ファイルブラウザー* が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-575">In that panel, click **Upload**, and a *File Browser* will appear.</span></span>

23. <span data-ttu-id="bc14a-576">に移動して、**メモ帳** で作成したファイルの **project.js** をクリックし、[**開く**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-576">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="bc14a-577">このファイルは、関数が使用するライブラリを定義します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-577">This file defines the libraries that your function will use.</span></span>

    ![カスタム関数](images/AzureLabs-Lab313-67.png)

24. <span data-ttu-id="bc14a-579">ファイルがアップロードされると、右側のパネルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-579">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="bc14a-580">このボタンをクリックすると、 **関数** エディター内で開かれます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-580">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="bc14a-581">次の画像と **まったく** 同じ外観にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-581">It must look **exactly** the same as the next image.</span></span>

    ![カスタム関数](images/AzureLabs-Lab313-68.png)

25. <span data-ttu-id="bc14a-583">この時点で、 *テーブル* にメッセージを格納する関数の機能をテストすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-583">At this point it would be good to test the capability of your Function to store the message on your *Table*.</span></span> <span data-ttu-id="bc14a-584">ウィンドウの右上にある [ **テスト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-584">On the top right side of the window, click on **Test**.</span></span>

    ![カスタム関数](images/AzureLabs-Lab313-69.png)

26. <span data-ttu-id="bc14a-586">上の図に示されているように、 **要求本文** にメッセージを挿入し、[ **実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-586">Insert a message on the **Request body**, as shown in the image above, and click on **Run**.</span></span> 

27. <span data-ttu-id="bc14a-587">関数が実行され、結果の状態が表示されます ([*出力*] ウィンドウの上に緑の **状態 202** が表示されます。これは成功した呼び出しであることを意味します)。</span><span class="sxs-lookup"><span data-stu-id="bc14a-587">The function will run, displaying the result status (you will notice the green **Status 202 Accepted**, above the *Output* window, which means it was a successful call):</span></span>

    ![出力結果](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a><span data-ttu-id="bc14a-589">第14章-アクティブなメッセージの表示</span><span class="sxs-lookup"><span data-stu-id="bc14a-589">Chapter 14 - View active messages</span></span>

<span data-ttu-id="bc14a-590">(Visual Studio Code では **なく** ) Visual Studio を開いた場合、テストメッセージの結果は *messagecontent* 文字列領域に格納されるため、視覚化することができます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-590">If you now open Visual Studio (**not** Visual Studio Code), you can visualize your test message result, as it will be stored in the *MessageContent* string area.</span></span>

![カスタム関数](images/AzureLabs-Lab313-71.png)

<span data-ttu-id="bc14a-592">Table Service と Function App が配置されていると、Ubuntu デバイスのメッセージが *Iotmessages* テーブルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-592">With the Table Service and Function App in place, your Ubuntu device messages will appear in your *IoTMessages* Table.</span></span> <span data-ttu-id="bc14a-593">まだ実行されていない場合は、デバイスをもう一度起動すると、Visual Studio *Cloud Explorer* を使用して、デバイスとモジュールの結果メッセージをテーブル内に表示できるようになります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-593">If not already running, start your device again, and you will be able to see the result messages from your device, and module, within your Table, through using Visual Studio *Cloud Explorer*.</span></span>

![データの視覚化](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a><span data-ttu-id="bc14a-595">第15章-Power BI セットアップ</span><span class="sxs-lookup"><span data-stu-id="bc14a-595">Chapter 15 - Power BI Setup</span></span>

<span data-ttu-id="bc14a-596">IOT デバイスからデータを視覚化するには **Power BI** (デスクトップバージョン) をセットアップし、先ほど作成した *テーブル* サービスからデータを収集します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-596">To visualize the data from your IOT device you will setup **Power BI** (desktop version), to collect the data from the *Table* Service, which you just created.</span></span> <span data-ttu-id="bc14a-597">Power BI の *HoloLens* バージョンでは、そのデータを使用して結果が視覚化されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-597">The *HoloLens* version of Power BI will then use that data to visualize the result.</span></span>

1.  <span data-ttu-id="bc14a-598">Windows 10 で Microsoft Store を開き、 **Power BI Desktop** を検索します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-598">Open the Microsoft Store on Windows 10 and search for **Power BI Desktop**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  <span data-ttu-id="bc14a-600">アプリケーションをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-600">Download the application.</span></span> <span data-ttu-id="bc14a-601">ダウンロードが完了したら、それを開きます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-601">Once it has finished downloading, open it.</span></span>

3.  <span data-ttu-id="bc14a-602">**Microsoft 365 アカウント** を使用して *Power BI* にログインします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-602">Log into *Power BI* with your **Microsoft 365 account**.</span></span> <span data-ttu-id="bc14a-603">サインアップするには、ブラウザーにリダイレクトすることができます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-603">You may be redirected to a browser, to sign up.</span></span> <span data-ttu-id="bc14a-604">サインアップしたら、Power BI アプリに戻り、もう一度サインインします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-604">Once you are signed up, go back to the Power BI app, and sign in again.</span></span>

4.  <span data-ttu-id="bc14a-605">[ **データの取得** ] をクリックし、[ **詳細**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-605">Click on **Get Data** and then click on **More...**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  <span data-ttu-id="bc14a-607">[ **Azure**]、[ **azure Table Storage**] の順にクリックし、[ **接続**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-607">Click **Azure**, **Azure Table Storage**, then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  <span data-ttu-id="bc14a-609">テーブルサービスの作成時に、先ほど収集した **テーブル URL** ([第11章の手順 13](#chapter-11---create-table-service)) を挿入するように求められます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-609">You will be prompted to insert the **Table URL** that you collected earlier ([in step 13 of Chapter 11](#chapter-11---create-table-service)), while creating your Table Service.</span></span> <span data-ttu-id="bc14a-610">URL を挿入した後、テーブル "サブフォルダー" (このコースでは IoTMessages) を参照するパスの部分を削除します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-610">After inserting the URL, delete the portion of the path referring to the Table "sub-folder" (which was IoTMessages, in this course).</span></span> <span data-ttu-id="bc14a-611">最終的な結果は、次の図のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-611">The final result should be as displayed in the image below.</span></span> <span data-ttu-id="bc14a-612">[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-612">Then click on **OK**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  <span data-ttu-id="bc14a-614">Table Storage の作成時に、メモした **ストレージキー** ([第11章の手順 11](#chapter-11---create-table-service)) を挿入するように求められます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-614">You will be prompted to insert the **Storage Key** that you noted ([in step 11 of Chapter 11](#chapter-11---create-table-service)) earlier while creating your Table Storage.</span></span> <span data-ttu-id="bc14a-615">[ **接続**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-615">Then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. <span data-ttu-id="bc14a-617">[ **ナビゲーター] パネル** が表示されたら、テーブルの横にあるボックスをオンにして、[ **読み込み**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-617">A **Navigator Panel** will be displayed, tick the box next to your Table and click on **Load**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. <span data-ttu-id="bc14a-619">現在、テーブルは Power BI に読み込まれていますが、その値を表示するクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="bc14a-619">Your table has now been loaded on Power BI, but it requires a query to display the values in it.</span></span> <span data-ttu-id="bc14a-620">これを行うには、画面の右側にある [ **フィールド] パネル** にあるテーブル名を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-620">To do so, right-click on the table name located in the **FIELDS panel** at the right side of the screen.</span></span> <span data-ttu-id="bc14a-621">次に、[ **クエリの編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-621">Then click on **Edit Query**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. <span data-ttu-id="bc14a-623">新しいウィンドウとして **Power Query エディター**  が開き、テーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-623">A **Power Query Editor**  will open up as a new window, displaying your table.</span></span> <span data-ttu-id="bc14a-624">テーブルの [*コンテンツ*] 列の "**レコード**" をクリックして、保存されているコンテンツを視覚化します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-624">Click on the word **Record** within the *Content* column of the table, to visualize your stored content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. <span data-ttu-id="bc14a-626">ウィンドウの左上にある [ **テーブルに** 移動] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-626">Click on **Into Table**, at the top-left of the window.</span></span> 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. <span data-ttu-id="bc14a-628">[ **閉じる & 適用**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-628">Click on **Close & Apply**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. <span data-ttu-id="bc14a-630">クエリの読み込みが完了したら、[ **フィールド] パネル** の画面の右側で、パラメーターの **名前** と **値** に対応するボックスをオンにして、 **messagecontent** 列の内容を視覚化します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-630">Once it has finished loading the query, within the **FIELDS panel**, on the right side of the screen, tick the boxes corresponding to the parameters **Name** and **Value**, to visualize the **MessageContent** column content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. <span data-ttu-id="bc14a-632">ウィンドウの左上にある **青いディスクアイコン** をクリックして、選択したフォルダーに作業内容を保存します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-632">Click on the **blue disk icon** at the top left of the window to save your work in a folder of your choice.</span></span>

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. <span data-ttu-id="bc14a-634">[発行] ボタンをクリックして、ワークスペースにテーブルをアップロードできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="bc14a-634">You can now click on the Publish button to upload your table to your Workspace.</span></span> <span data-ttu-id="bc14a-635">メッセージが表示されたら、[ **マイワークスペース** ] をクリックし、[ *選択*] をクリックします</span><span class="sxs-lookup"><span data-stu-id="bc14a-635">When prompted, click **My workspace** and click *Select*.</span></span> <span data-ttu-id="bc14a-636">送信の成功した結果が表示されるまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-636">Wait for it to display the successful result of the submission.</span></span>

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> <span data-ttu-id="bc14a-639">次の章は HoloLens 固有です。</span><span class="sxs-lookup"><span data-stu-id="bc14a-639">The following Chapter is HoloLens specific.</span></span> <span data-ttu-id="bc14a-640">Power BI は現在イマーシブアプリケーションとして使用できませんが、デスクトップアプリを使用して、Windows Mixed Reality ポータル (崖家) でデスクトップバージョンを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-640">Power BI is not currently available as an immersive application, however you can run the desktop version in the Windows Mixed Reality Portal (aka Cliff House), through the Desktop app.</span></span>

## <a name="chapter-16---display-power-bi-data-on-hololens"></a><span data-ttu-id="bc14a-641">Chapter 16-HoloLens で Power BI データを表示する</span><span class="sxs-lookup"><span data-stu-id="bc14a-641">Chapter 16 - Display Power BI data on HoloLens</span></span>

1. <span data-ttu-id="bc14a-642">HoloLens で、アプリケーションの一覧のアイコンをタップして、 **Microsoft Store** にログインします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-642">On your HoloLens, log in to the **Microsoft Store**, by tapping on its icon in the applications list.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. <span data-ttu-id="bc14a-644">**Power BI** アプリケーションを検索してダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-644">Search and then download the **Power BI** application.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. <span data-ttu-id="bc14a-646">アプリケーションの一覧から **Power BI** を開始します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-646">Start **Power BI** from your applications list.</span></span> 

4. <span data-ttu-id="bc14a-647">**Power BI** によって、 **Microsoft 365 アカウント** へのログインが要求される場合があります。</span><span class="sxs-lookup"><span data-stu-id="bc14a-647">**Power BI** might ask you to login to your **Microsoft 365 account**.</span></span>

5. <span data-ttu-id="bc14a-648">アプリの内部では、次の図に示すように、既定でワークスペースが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-648">Once inside the app, the workspace should display by default as shown in the image below.</span></span> <span data-ttu-id="bc14a-649">この問題が発生しない場合は、ウィンドウの左側にあるワークスペースアイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-649">If that does not happen, simply click on the workspace icon on the left side of the window.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a><span data-ttu-id="bc14a-651">IoT Hub アプリケーションが完成しました</span><span class="sxs-lookup"><span data-stu-id="bc14a-651">Your finished your IoT Hub application</span></span>

<span data-ttu-id="bc14a-652">これで、シミュレートされた仮想マシンのエッジデバイスを使用して、IoT Hub サービスを正常に作成できました。</span><span class="sxs-lookup"><span data-stu-id="bc14a-652">Congratulations, you have successfully created an IoT Hub Service, with a simulated Virtual Machine Edge device.</span></span> <span data-ttu-id="bc14a-653">デバイスは、azure Function App によって容易に machine learning モデルの結果を Azure Table サービスに伝達できます。このサービスは、Power BI に読み込まれ、Microsoft HoloLens 内で視覚化されます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-653">Your device can  communicate the results of a machine learning model to an Azure Table Service, facilitated by an Azure Function App, which is read into Power BI, and visualized within a Microsoft HoloLens.</span></span>
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="bc14a-655">ボーナス演習</span><span class="sxs-lookup"><span data-stu-id="bc14a-655">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="bc14a-656">演習1</span><span class="sxs-lookup"><span data-stu-id="bc14a-656">Exercise 1</span></span>

<span data-ttu-id="bc14a-657">テーブルに格納されているメッセージング構造を展開し、グラフとして表示します。</span><span class="sxs-lookup"><span data-stu-id="bc14a-657">Expand the messaging structure stored in the table and display it as a graph.</span></span> <span data-ttu-id="bc14a-658">後で表示するために、さらに多くのデータを収集し、同じテーブルに格納することができます。</span><span class="sxs-lookup"><span data-stu-id="bc14a-658">You might want to collect more data and store it in the same table, to be later displayed.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="bc14a-659">演習2</span><span class="sxs-lookup"><span data-stu-id="bc14a-659">Exercise 2</span></span>

<span data-ttu-id="bc14a-660">IoT ボードにデプロイする追加の "カメラキャプチャ" モジュールを作成して、分析対象のカメラを通じてイメージをキャプチャできるようにします。</span><span class="sxs-lookup"><span data-stu-id="bc14a-660">Create an additional "camera capture" module to be deployed on the IoT board, so that it can capture images through the camera to be analyzed.</span></span>
