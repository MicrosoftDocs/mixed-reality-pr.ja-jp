---
title: MR と Azure 310 - 物体検出
description: このコースでは、機械学習モデルをトレーニングし、それを使用して、現実世界における類似したオブジェクトとその位置を認識する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, カスタムビジョン, オブジェクト検出, mixed reality, academy, unity, チュートリアル, api, hololens, Windows 10, Visual Studio
ms.openlocfilehash: 8f625ebc1e40edaa6364567686c345386ea37dbf
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010172"
---
# <a name="mr-and-azure-310-object-detection"></a><span data-ttu-id="1c87d-104">Mr と Azure 310: オブジェクトの検出</span><span class="sxs-lookup"><span data-stu-id="1c87d-104">Mr and Azure 310: Object detection</span></span>

>[!NOTE]
><span data-ttu-id="1c87d-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="1c87d-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="1c87d-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="1c87d-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="1c87d-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。</span><span class="sxs-lookup"><span data-stu-id="1c87d-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="1c87d-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="1c87d-109">今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="1c87d-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="1c87d-110">この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

<span data-ttu-id="1c87d-111">このコースでは、Azure Custom Vision 使用して、混合の現実アプリケーションの "オブジェクト検出" 機能を使用して、提供されたイメージ内でカスタムビジュアルコンテンツとその空間位置を認識する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-111">In this course, you will learn how to recognize custom visual content and its spatial position within a provided image, using Azure Custom Vision "Object Detection" capabilities in a mixed reality application.</span></span>

<span data-ttu-id="1c87d-112">このサービスでは、オブジェクトイメージを使用して機械学習モデルをトレーニングすることができます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="1c87d-113">次に、トレーニング済みのモデルを使用して、よく似たオブジェクトを認識し、実際の世界での場所を概算します。これは、Microsoft HoloLens のカメラキャプチャや、カメラが PC for イマーシブ (VR) ヘッドセットに接続することによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-113">You will then use the trained model to recognize similar objects and approximate their location in the real world, as provided by the camera capture of Microsoft HoloLens or a camera connect to a PC for immersive (VR) headsets.</span></span>

![コースの結果](images/AzureLabs-Lab310-00.png)

<span data-ttu-id="1c87d-115">**Azure Custom Vision、オブジェクト検出** は Microsoft のサービスであり、開発者はカスタムイメージ分類子を作成できます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-115">**Azure Custom Vision, Object Detection** is a Microsoft Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="1c87d-116">これらの分類子を新しいイメージと共に使用して、その新しいイメージ内のオブジェクトを検出し、イメージ内に **ボックスの境界** を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-116">These classifiers can then be used with new images to detect objects within that new image, by providing **Box Boundaries** within the image itself.</span></span> <span data-ttu-id="1c87d-117">このサービスは、シンプルで使いやすいオンラインポータルを提供して、このプロセスを効率化します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-117">The Service provides a simple, easy to use, online portal to streamline this process.</span></span> <span data-ttu-id="1c87d-118">詳細については、次のリンク先を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c87d-118">For more information, visit the following links:</span></span>

* [<span data-ttu-id="1c87d-119">Azure Custom Vision ページ</span><span class="sxs-lookup"><span data-stu-id="1c87d-119">Azure Custom Vision page</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [<span data-ttu-id="1c87d-120">制限とクォータ</span><span class="sxs-lookup"><span data-stu-id="1c87d-120">Limits and Quotas</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

<span data-ttu-id="1c87d-121">このコースが完了すると、mixed reality アプリケーションが完成し、次のことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-121">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1. <span data-ttu-id="1c87d-122">ユーザーは、Azure Custom Vision Service、オブジェクト検出を使用してトレーニングされたオブジェクトを *見つめ* ます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-122">The user will be able to *gaze* at an object, which they have trained using the Azure Custom Vision Service, Object Detection.</span></span> 
2. <span data-ttu-id="1c87d-123">ユーザーは *Tap* ジェスチャを使用して、表示内容のイメージをキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-123">The user will use the *Tap* gesture to capture an image of what they are looking at.</span></span>
3. <span data-ttu-id="1c87d-124">アプリは、Azure Custom Vision Service にイメージを送信します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-124">The app will send the image to the Azure Custom Vision Service.</span></span>
4. <span data-ttu-id="1c87d-125">サービスからの応答が表示されます。これにより、認識の結果がワールドスペーステキストとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-125">There will be a reply from the Service which will display the result of the recognition as world-space text.</span></span> <span data-ttu-id="1c87d-126">これは、認識されたオブジェクトの世界の位置を理解し、イメージで検出された *タグ* を使用してラベルテキストを提供する方法として、Microsoft HoloLens の空間トラッキングを利用することで実現します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-126">This will be accomplished through utilizing the Microsoft HoloLens' Spatial Tracking, as a way of understanding the world position of the recognized object, and then using the *Tag* associated with what is detected in the image, to provide the label text.</span></span>

<span data-ttu-id="1c87d-127">また、イメージを手動でアップロードする方法、タグを作成する方法、サービスをトレーニングする方法についても説明します。このコースでは、送信するイメージ内の *境界ボックス* を設定することによって、さまざまなオブジェクト (例では、カップ) を認識します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-127">The course will also cover manually uploading images, creating tags, and training the Service, to recognize different objects (in the provided example, a cup), by setting the *Boundary Box* within the image you submit.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="1c87d-128">アプリの作成と使用の後、開発者は Azure Custom Vision Service に戻り、サービスによって行われた予測を特定して、それらが適切かどうかを判断する必要があります (サービスに何かタグを付け、 *境界ボックス* を調整します)。</span><span class="sxs-lookup"><span data-stu-id="1c87d-128">Following the creation and use of the app, the developer should navigate back to the Azure Custom Vision Service, and identify the predictions made by the Service, and determine whether they were correct or not (through tagging anything the Service missed, and adjusting the *Bounding Boxes*).</span></span> <span data-ttu-id="1c87d-129">その後、サービスを再トレーニングできます。これにより、実際のオブジェクトを認識する確率が高まります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-129">The Service can then be re-trained, which will increase the likelihood of it recognizing real world objects.</span></span>

<span data-ttu-id="1c87d-130">このコースでは、Azure Custom Vision Service のオブジェクト検出から Unity ベースのサンプルアプリケーションに結果を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-130">This course will teach you how to get the results from the Azure Custom Vision Service, Object Detection, into a Unity-based sample application.</span></span> <span data-ttu-id="1c87d-131">これらの概念は、構築しているカスタムアプリケーションに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-131">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="1c87d-132">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="1c87d-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1c87d-133">コース</span><span class="sxs-lookup"><span data-stu-id="1c87d-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="1c87d-134"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1c87d-134"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1c87d-135"><a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="1c87d-135"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="1c87d-136">MR と Azure 310:物体検出</span><span class="sxs-lookup"><span data-stu-id="1c87d-136">MR and Azure 310: Object detection</span></span></td><td style="text-align: center;"> <span data-ttu-id="1c87d-137">✔️</span><span class="sxs-lookup"><span data-stu-id="1c87d-137">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="1c87d-138">前提条件</span><span class="sxs-lookup"><span data-stu-id="1c87d-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="1c87d-139">このチュートリアルは、Unity と C# の基本的な経験がある開発者向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="1c87d-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="1c87d-140">また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証された内容 (2018 年7月) を表しています。</span><span class="sxs-lookup"><span data-stu-id="1c87d-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="1c87d-141">「 [ツールのインストール](../../install-the-tools.md) 」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に記載されているものより新しいソフトウェアの内容と完全に一致するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="1c87d-141">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="1c87d-142">このコースでは、次のハードウェアとソフトウェアをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="1c87d-143">開発用 PC</span><span class="sxs-lookup"><span data-stu-id="1c87d-143">A development PC</span></span>
- [<span data-ttu-id="1c87d-144">開発者モードが有効になっている Windows 10 の作成者の更新プログラム (またはそれ以降)</span><span class="sxs-lookup"><span data-stu-id="1c87d-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="1c87d-145">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="1c87d-145">The latest Windows 10 SDK</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="1c87d-146">Unity 2017.4 LTS</span><span class="sxs-lookup"><span data-stu-id="1c87d-146">Unity 2017.4 LTS</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="1c87d-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="1c87d-147">Visual Studio 2017</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- <span data-ttu-id="1c87d-148">開発者モードが有効になっている[Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details)</span><span class="sxs-lookup"><span data-stu-id="1c87d-148">A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) with Developer mode enabled</span></span>
- <span data-ttu-id="1c87d-149">Azure のセットアップと Custom Vision Service の取得のためのインターネットアクセス</span><span class="sxs-lookup"><span data-stu-id="1c87d-149">Internet access for Azure setup and Custom Vision Service retrieval</span></span>
-  <span data-ttu-id="1c87d-150">Custom Vision が認識するオブジェクトごとに、少なくとも 15 (15) のイメージが必要です)。</span><span class="sxs-lookup"><span data-stu-id="1c87d-150">A series of at least fifteen (15) images are required) for each object that you would like the Custom Vision to recognize.</span></span> <span data-ttu-id="1c87d-151">必要に応じて、このコースで既に提供されているイメージ、 [一連のカップ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-151">If you wish, you can use the images already provided with this course, [a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="1c87d-152">アップグレードを開始する前に</span><span class="sxs-lookup"><span data-stu-id="1c87d-152">Before you start</span></span>

1.  <span data-ttu-id="1c87d-153">このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="1c87d-153">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="1c87d-154">HoloLens をセットアップしてテストします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-154">Set up and test your HoloLens.</span></span> <span data-ttu-id="1c87d-155">HoloLens のセットアップをサポートする必要がある場合は、 [hololens セットアップに関する記事にアクセスして](https://docs.microsoft.com/hololens/hololens-setup)ください。</span><span class="sxs-lookup"><span data-stu-id="1c87d-155">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="1c87d-156">新しい HoloLens アプリの開発を開始するときは、調整とセンサーのチューニングを実行することをお勧めします (ユーザーごとにこれらのタスクを実行するのに役立つ場合があります)。</span><span class="sxs-lookup"><span data-stu-id="1c87d-156">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="1c87d-157">調整の詳細については、 [「HoloLens の調整に関する記事へのリンク」を](../../../calibration.md#hololens-2)参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c87d-157">For help on Calibration, please follow this [link to the HoloLens Calibration article](../../../calibration.md#hololens-2).</span></span>

<span data-ttu-id="1c87d-158">センサーチューニングの詳細については、 [HoloLens センサーチューニングに関する記事へのリンクを](../../../sensor-tuning.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c87d-158">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](../../../sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-portal"></a><span data-ttu-id="1c87d-159">章 1-Custom Vision ポータル</span><span class="sxs-lookup"><span data-stu-id="1c87d-159">Chapter 1 - The Custom Vision Portal</span></span>

<span data-ttu-id="1c87d-160">**Azure Custom Vision Service** を使用するには、アプリケーションで使用できるようにするインスタンスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-160">To use the **Azure Custom Vision Service**, you will need to configure an instance of it to be made available to your application.</span></span>

1.  <span data-ttu-id="1c87d-161">[ **Custom Vision Service** メインページに](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)移動します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-161">Navigate [to the **Custom Vision Service** main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="1c87d-162">[ **はじめに**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-162">Click on **Getting Started**.</span></span>

    ![](images/AzureLabs-Lab310-01.png)

3.  <span data-ttu-id="1c87d-163">Custom Vision ポータルにサインインします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-163">Sign in to the Custom Vision Portal.</span></span>

    ![](images/AzureLabs-Lab310-02.png)

4.  <span data-ttu-id="1c87d-164">まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-164">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="1c87d-165">このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。</span><span class="sxs-lookup"><span data-stu-id="1c87d-165">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

5.  <span data-ttu-id="1c87d-166">初めてログインした後は、 *サービスパネルの使用条件* を確認するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-166">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="1c87d-167">*条件に同意* するには、チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-167">Click the checkbox to *agree to the terms*.</span></span> <span data-ttu-id="1c87d-168">[ **同意** する] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-168">Then click **I agree**.</span></span>

    ![](images/AzureLabs-Lab310-03.png)

6.  <span data-ttu-id="1c87d-169">使用条件に同意すると、 *[マイプロジェクト* ] セクションが表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-169">Having agreed to the terms, you are now in the *My Projects* section.</span></span> <span data-ttu-id="1c87d-170">[ **新しいプロジェクト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-170">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab310-04.png)

7.  <span data-ttu-id="1c87d-171">右側にタブが表示され、プロジェクトのフィールドを指定するように求められます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-171">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="1c87d-172">プロジェクトの名前を挿入する</span><span class="sxs-lookup"><span data-stu-id="1c87d-172">Insert a name for your project</span></span>

    2.  <span data-ttu-id="1c87d-173">プロジェクトの説明を挿入します (**省略可能**)</span><span class="sxs-lookup"><span data-stu-id="1c87d-173">Insert a description for your project (**Optional**)</span></span>

    3.  <span data-ttu-id="1c87d-174">リソースグループを選択するか、新しい **リソースグループ** を作成します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-174">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="1c87d-175">リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-175">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="1c87d-176">1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのコースなど) を共通のリソースグループに保持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-176">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > <span data-ttu-id="1c87d-177">[Azure リソースグループの詳細については、関連するドキュメントを](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c87d-177">If you wish to [read more about Azure Resource Groups, navigate to the associated Docs](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4.  <span data-ttu-id="1c87d-178">プロジェクトの **種類** を **オブジェクト検出 (プレビュー)** として設定します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-178">Set the **Project Types** as **Object Detection (preview)**.</span></span>

8.  <span data-ttu-id="1c87d-179">操作が完了すると、[ **プロジェクトの作成**] をクリックすると、Custom Vision Service プロジェクトページにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-179">Once you are finished, click on **Create project**, and you will be redirected to the Custom Vision Service project page.</span></span>


## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="1c87d-180">第2章-Custom Vision プロジェクトのトレーニング</span><span class="sxs-lookup"><span data-stu-id="1c87d-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="1c87d-181">Custom Vision ポータルでは、主な目的は、イメージ内の特定のオブジェクトを認識するようにプロジェクトをトレーニングすることです。</span><span class="sxs-lookup"><span data-stu-id="1c87d-181">Once in the Custom Vision Portal, your primary objective is to train your project to recognize specific objects in images.</span></span>

<span data-ttu-id="1c87d-182">アプリケーションで認識するオブジェクトごとに、少なくとも15個のイメージが必要です。</span><span class="sxs-lookup"><span data-stu-id="1c87d-182">You need at least fifteen (15) images for each object that you would like your application to recognize.</span></span> <span data-ttu-id="1c87d-183">このコースに用意されているイメージ ([一連のカップ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-183">You can use the images provided with this course ([a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

<span data-ttu-id="1c87d-184">Custom Vision プロジェクトをトレーニングするには:</span><span class="sxs-lookup"><span data-stu-id="1c87d-184">To train your Custom Vision project:</span></span>

1.  <span data-ttu-id="1c87d-185">[タグ] の横にあるボタンをクリックし **+** ます。 </span><span class="sxs-lookup"><span data-stu-id="1c87d-185">Click on the **+** button next to **Tags**.</span></span>

    ![](images/AzureLabs-Lab310-06.png)

2.  <span data-ttu-id="1c87d-186">イメージを関連付けるために使用されるタグの **名前** を追加します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-186">Add a **name** for the tag that will be used to associate your images with.</span></span> <span data-ttu-id="1c87d-187">この例では、認識に cups のイメージを使用しているため、この **カップ** にタグを付けます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-187">In this example we are using images of cups for recognition, so have named the tag for this, **Cup**.</span></span> <span data-ttu-id="1c87d-188">[ **保存** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-188">Click **Save** once finished.</span></span>

    ![](images/AzureLabs-Lab310-07.png)

3.  <span data-ttu-id="1c87d-189">**タグ** が追加されていることがわかります (表示するには、ページの再読み込みが必要になる場合があります)。</span><span class="sxs-lookup"><span data-stu-id="1c87d-189">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> 

    ![](images/AzureLabs-Lab310-08.png)

4.  <span data-ttu-id="1c87d-190">ページの中央にある [ **イメージの追加** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-190">Click on **Add images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab310-09.png)

5.  <span data-ttu-id="1c87d-191">[ **ローカルファイルの参照**] をクリックし、1つのオブジェクトに対してアップロードするイメージを選択します。最小値は 15 (15) です。</span><span class="sxs-lookup"><span data-stu-id="1c87d-191">Click on **Browse local files**, and browse to the images you would like to upload for one object, with the minimum being fifteen (15).</span></span>

    > [!TIP]
    >  <span data-ttu-id="1c87d-192">アップロードには、一度に複数のイメージを選択できます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-192">You can select several images at a time, to upload.</span></span>

    ![](images/AzureLabs-Lab310-10.png)

6.  <span data-ttu-id="1c87d-193">プロジェクトをトレーニングするすべてのイメージを選択したら、[ **ファイルのアップロード (ファイルのアップロード** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-193">Press **Upload files** once you have selected all the images you would like to train the project with.</span></span> <span data-ttu-id="1c87d-194">ファイルのアップロードが開始されます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-194">The files will begin uploading.</span></span> <span data-ttu-id="1c87d-195">アップロードの確認が完了したら、[ **完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-195">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab310-11.png)

7.  <span data-ttu-id="1c87d-196">この時点で、画像はアップロードされますが、タグは付けられません。</span><span class="sxs-lookup"><span data-stu-id="1c87d-196">At this point your images are uploaded, but not tagged.</span></span>

    ![](images/AzureLabs-Lab310-12.png)

8.  <span data-ttu-id="1c87d-197">画像にタグを付けるには、マウスを使用します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-197">To tag your images, use your mouse.</span></span> <span data-ttu-id="1c87d-198">画像にマウスポインターを合わせると、選択の強調表示によって、オブジェクトの周囲に自動的に選択が描画されます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-198">As you hover over your image, a selection highlight will aid you by automatically drawing a selection around your object.</span></span> <span data-ttu-id="1c87d-199">正確でない場合は、独自のものを描画できます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-199">If it is not accurate, you can draw your own.</span></span> <span data-ttu-id="1c87d-200">これを実現するには、マウスを左クリックし、選択領域をドラッグしてオブジェクトを格納します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-200">This is accomplished by holding left-click on the mouse, and dragging the selection region to encompass your object.</span></span> 

    ![](images/AzureLabs-Lab310-13.png) 

9. <span data-ttu-id="1c87d-201">画像内のオブジェクトを選択した後、小さなプロンプトで *Region タグを追加* するように求められます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-201">Following the selection of your object within the image, a small prompt will ask for you to *Add Region Tag*.</span></span> <span data-ttu-id="1c87d-202">以前に作成したタグ (上の例では "カップ") を選択するか、さらにタグを追加する場合は、に「」と入力し、[ **+] (プラス)** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-202">Select your previously created tag ('Cup', in the above example), or if you are adding more tags, type that in and click the **+ (plus)** button.</span></span>

    ![](images/AzureLabs-Lab310-14.png) 

10. <span data-ttu-id="1c87d-203">次の画像にタグを付けるには、ブレードの右側にある矢印をクリックするか、[タグ] ブレードを閉じます (ブレードの右上隅にある [ **X** ] をクリックします)。次の画像をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-203">To tag the next image, you can click the arrow to the right of the blade, or close the tag blade (by clicking the **X** in the top-right corner of the blade) and then click the next image.</span></span> <span data-ttu-id="1c87d-204">次のイメージの準備ができたら、同じ手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-204">Once you have the next image ready, repeat the same procedure.</span></span> <span data-ttu-id="1c87d-205">すべてのタグが付けられるまで、アップロードしたすべてのイメージに対してこの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="1c87d-205">Do this for all the images you have uploaded, until they are all tagged.</span></span> 

    > [!NOTE]
    >  <span data-ttu-id="1c87d-206">次の画像のように、同じイメージ内の複数のオブジェクトを選択できます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-206">You can select several objects in the same image, like the image below:</span></span> 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. <span data-ttu-id="1c87d-207">すべてのタグを付けたら、画面の左側にある **タグ** 付きボタンをクリックして、タグ付けされたイメージを表示します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-207">Once you have tagged them all, click on the **tagged** button, on the left of the screen, to reveal the tagged images.</span></span> 

    ![](images/AzureLabs-Lab310-16.png)

12. <span data-ttu-id="1c87d-208">これで、サービスをトレーニングする準備ができました。</span><span class="sxs-lookup"><span data-stu-id="1c87d-208">You are now ready to train your Service.</span></span> <span data-ttu-id="1c87d-209">[ **トレーニング** ] ボタンをクリックすると、最初のトレーニングイテレーションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-209">Click the **Train** button, and the first training iteration will begin.</span></span>

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. <span data-ttu-id="1c87d-210">ビルドされると、[ **既定** の **URL と予測 URL**] という2つのボタンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-210">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="1c87d-211">[ **既定値** に設定] をクリックし、[ **予測 URL**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-211">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > <span data-ttu-id="1c87d-212">このから提供されるエンドポイントは、既定としてマークされている *反復処理* のいずれかに設定されます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-212">The endpoint which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="1c87d-213">そのため、後で新しい *イテレーション* を作成して既定として更新する場合は、コードを変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1c87d-213">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

14. <span data-ttu-id="1c87d-214">**予測 URL** をクリックしたら、*メモ帳* を開き、 **Url** ("**予測エンドポイント**" とも呼ばれます) と **サービス予測キー** をコピーして貼り付けます。これにより、コードの後で必要になったときに取得できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-214">Once you have clicked on **Prediction URL**, open *Notepad*, and copy and paste the **URL** (also called your **Prediction-Endpoint**) and the **Service Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="1c87d-215">章 3-Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="1c87d-215">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="1c87d-216">次に示すのは、mixed reality で開発するための一般的な設定です。そのため、他のプロジェクトに適したテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="1c87d-216">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="1c87d-217">**Unity** を開き、[**新規**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-217">Open **Unity** and click **New**.</span></span>

    ![](images/AzureLabs-Lab310-21.png)

2.  <span data-ttu-id="1c87d-218">ここで、Unity プロジェクト名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-218">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="1c87d-219">**CustomVisionObjDetection** を挿入します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-219">Insert **CustomVisionObjDetection**.</span></span> <span data-ttu-id="1c87d-220">プロジェクトの種類が **3d** に設定されていることを確認し、場所を適切な **場所** に設定します (ルートディレクトリの方が適していることに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="1c87d-220">Make sure the project type is set to **3D**, and set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="1c87d-221">次に、[ **プロジェクトの作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-221">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab310-22.png)

3.  <span data-ttu-id="1c87d-222">Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-222">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="1c87d-223">[ \* >  *設定* の編集\*] に移動し、新しいウィンドウで [**外部ツール**] に移動します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-223">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="1c87d-224">**外部スクリプトエディター** を **Visual Studio** に変更します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-224">Change **External Script Editor** to **Visual Studio**.</span></span> <span data-ttu-id="1c87d-225">[ **基本設定** ] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-225">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab310-23.png)

4.  <span data-ttu-id="1c87d-226">次に、[ **ファイル > ビルド設定** ] に移動し、 **プラットフォーム** を *ユニバーサル Windows プラットフォーム* に切り替えて、[ **プラットフォームの切り替え** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-226">Next, go to **File > Build Settings** and switch the **Platform** to *Universal Windows Platform*, and then clicking on the **Switch Platform** button.</span></span>

    ![](images/AzureLabs-Lab310-24.png)

5.  <span data-ttu-id="1c87d-227">同じ [ **ビルドの設定** ] ウィンドウで、次の項目が設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-227">In the same **Build Settings** window, ensure the following are set:</span></span>

    1.  <span data-ttu-id="1c87d-228">**ターゲットデバイス** が **HoloLens** に設定されています</span><span class="sxs-lookup"><span data-stu-id="1c87d-228">**Target Device** is set to **HoloLens**</span></span>        
    2.  <span data-ttu-id="1c87d-229">**ビルドの種類** が **D3D** に設定されています</span><span class="sxs-lookup"><span data-stu-id="1c87d-229">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="1c87d-230">**SDK** は最新の **インストール** に設定されています</span><span class="sxs-lookup"><span data-stu-id="1c87d-230">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="1c87d-231">**Visual Studio のバージョン** が、**インストールされている最新** バージョンに設定されています</span><span class="sxs-lookup"><span data-stu-id="1c87d-231">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="1c87d-232">**ビルドと実行** は **ローカルコンピューター** に設定されています</span><span class="sxs-lookup"><span data-stu-id="1c87d-232">**Build and Run** is set to **Local Machine**</span></span>            
    6.  <span data-ttu-id="1c87d-233">それ以外の設定は、[ **ビルド設定**] の [既定] のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-233">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab310-25.png)

6.  <span data-ttu-id="1c87d-234">同じ **ビルド設定** ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 **インスペクター** が配置されている領域の関連パネルが開きます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-234">In the same **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7. <span data-ttu-id="1c87d-235">このパネルでは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-235">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="1c87d-236">[ **その他の設定** ] タブで、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-236">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="1c87d-237">**Scripting Runtime のバージョン** は **実験的** (.net 4.6 と同等) である必要があります。これにより、エディターを再起動する必要が生じます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-237">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="1c87d-238">**スクリプトバックエンド** は **.net** である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-238">**Scripting Backend** should be **.NET**.</span></span>

        3. <span data-ttu-id="1c87d-239">**API の互換性レベル** は **.net 4.6** である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-239">**API Compatibility Level** should be **.NET 4.6**.</span></span>

            ![](images/AzureLabs-Lab310-26.png)

    2.  <span data-ttu-id="1c87d-240">[ **発行の設定** ] タブの [ **機能**] で、次の項目を確認します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-240">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="1c87d-241">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="1c87d-241">**InternetClient**</span></span>

        2.  <span data-ttu-id="1c87d-242">**Web カメラ**</span><span class="sxs-lookup"><span data-stu-id="1c87d-242">**Webcam**</span></span>

        3. <span data-ttu-id="1c87d-243">**SpatialPerception**</span><span class="sxs-lookup"><span data-stu-id="1c87d-243">**SpatialPerception**</span></span>

            <span data-ttu-id="1c87d-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span><span class="sxs-lookup"><span data-stu-id="1c87d-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span></span>

    3.  <span data-ttu-id="1c87d-245">パネルの下にある [ **XR settings** (発行の **設定**] の下にあります) で、[ **Virtual reality がサポートされる**] を選択し、 **Windows Mixed reality SDK** が追加されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, then make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab310-29.png)

8.  <span data-ttu-id="1c87d-246">**ビルド設定** に戻り、 *Unity C \# プロジェクト* はグレーで表示されなくなりました。この横にあるチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-246">Back in **Build Settings**, *Unity C\# Projects* is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="1c87d-247">**[ビルド設定]** ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-247">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="1c87d-248">**エディター** で、[プロジェクト設定の **編集**] [グラフィック] の順にクリックし  >    >  ます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-248">In the **Editor**, click on **Edit** > **Project Settings** > **Graphics**.</span></span>

    ![](images/AzureLabs-Lab310-30.png)

11. <span data-ttu-id="1c87d-249">[ **インスペクター] パネル** で、 *グラフィックスの設定* が開きます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-249">In the **Inspector Panel** the *Graphics Settings* will be open.</span></span> <span data-ttu-id="1c87d-250">" **常にシェーダーを含める**" という配列が表示されるまで下にスクロールします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-250">Scroll down until you see an array called **Always Include Shaders**.</span></span> <span data-ttu-id="1c87d-251">**サイズ** 変数を1つ増やしてスロットを追加します (この例では8であるため、9にしました)。</span><span class="sxs-lookup"><span data-stu-id="1c87d-251">Add a slot by increasing the **Size** variable by one (in this example, it was 8 so we made it 9).</span></span> <span data-ttu-id="1c87d-252">次に示すように、配列の最後の位置に新しいスロットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-252">A new slot will appear, in the last position of the array, as shown below:</span></span>

    ![](images/AzureLabs-Lab310-31.png)

12. <span data-ttu-id="1c87d-253">スロットで、スロットの横にある小さなターゲット円をクリックして、シェーダーの一覧を開きます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-253">In the slot, click on the small target circle next to the slot to open a list of shaders.</span></span> <span data-ttu-id="1c87d-254">**レガシシェーダー/透明/拡散** シェーダーを探し、ダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-254">Look for the **Legacy Shaders/Transparent/Diffuse** shader and double-click it.</span></span> 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a><span data-ttu-id="1c87d-255">第4章-CustomVisionObjDetection Unity パッケージのインポート</span><span class="sxs-lookup"><span data-stu-id="1c87d-255">Chapter 4 - Importing the CustomVisionObjDetection Unity package</span></span>

<span data-ttu-id="1c87d-256">このコースでは、 **unitypackage** という名前の Unity 資産パッケージが提供されています。</span><span class="sxs-lookup"><span data-stu-id="1c87d-256">For this course you are provided with a Unity Asset Package called **Azure-MR-310.unitypackage**.</span></span> 

> <span data-ttu-id="1c87d-257">形Unity でサポートされているすべてのオブジェクト (シーン全体を含む) は、 **unitypackage** ファイルにパッケージ化し、他のプロジェクトでエクスポート/インポートできます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-257">[TIP] Any objects supported by Unity, including entire scenes, can be packaged into a **.unitypackage** file, and exported / imported in other projects.</span></span> <span data-ttu-id="1c87d-258">これは、さまざまな **Unity プロジェクト** 間でアセットを移動する最も安全で効率的な方法です。</span><span class="sxs-lookup"><span data-stu-id="1c87d-258">It is the safest, and most efficient, way to move assets between different **Unity projects**.</span></span>

<span data-ttu-id="1c87d-259">[ダウンロードする必要がある AZURE MR-310 パッケージ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)については、こちらを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c87d-259">You can find the [Azure-MR-310 package that you need to download here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span></span>

1.  <span data-ttu-id="1c87d-260">Unity ダッシュボードを使用して、画面の上部にあるメニューの [ **アセット** ] をクリックし、[ **パッケージのインポート > カスタムパッケージ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-260">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![](images/AzureLabs-Lab310-33.png)

2.  <span data-ttu-id="1c87d-261">ファイルピッカーを使用して **unitypackage** パッケージを選択し、[ **開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-261">Use the file picker to select the **Azure-MR-310.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="1c87d-262">この資産のコンポーネントの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-262">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="1c87d-263">インポートを確認するには、[ **インポート** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-263">Confirm the import by clicking the **Import** button.</span></span>

    ![](images/AzureLabs-Lab310-34.png)

3.  <span data-ttu-id="1c87d-264">インポートが完了すると、パッケージのフォルダーが [ **Assets** ] フォルダーに追加されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-264">Once it has finished importing, you will notice that folders from the package have now been added to your **Assets** folder.</span></span> <span data-ttu-id="1c87d-265">この種のフォルダー構造は、Unity プロジェクトで一般的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-265">This kind of folder structure is typical for a Unity project.</span></span>

    ![](images/AzureLabs-Lab310-35.png)

    1.  <span data-ttu-id="1c87d-266">**素材** フォルダーには、**見つめカーソル** によって使用される素材が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1c87d-266">The **Materials** folder contains the material used by the **Gaze Cursor**.</span></span> 

    2.  <span data-ttu-id="1c87d-267">**プラグイン** フォルダーには、サービス web 応答を逆シリアル化するためにコードによって使用される Newtonsoft DLL が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1c87d-267">The **Plugins** folder contains the Newtonsoft DLL used by the code to deserialize the Service web response.</span></span> <span data-ttu-id="1c87d-268">フォルダーに含まれる2つの異なるバージョン (2) は、ライブラリを Unity エディターと UWP ビルドの両方で使用およびビルドできるようにするために必要です。</span><span class="sxs-lookup"><span data-stu-id="1c87d-268">The two (2) different versions contained in the folder, and sub-folder, are necessary to allow the library to be used and built by both the Unity Editor and the UWP build.</span></span> 

    3.  <span data-ttu-id="1c87d-269">**Prefabs** フォルダーには、シーンに含まれる Prefabs が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1c87d-269">The **Prefabs** folder contains the prefabs contained in the scene.</span></span> <span data-ttu-id="1c87d-270">これらには次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-270">Those are:</span></span>

        1.  <span data-ttu-id="1c87d-271">**GazeCursor** は、アプリケーションで使用されるカーソルです。</span><span class="sxs-lookup"><span data-stu-id="1c87d-271">The **GazeCursor**, the cursor used in the application.</span></span> <span data-ttu-id="1c87d-272">は、SpatialMapping prefab と連携して、物理オブジェクト上のシーンに配置できます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-272">Will work together with the SpatialMapping prefab to be able to be placed in the scene on top of physical objects.</span></span>
        2.  <span data-ttu-id="1c87d-273">**ラベル**。これは、必要に応じてシーンにオブジェクトタグを表示するために使用される UI オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="1c87d-273">The **Label**, which is the UI object used to display the object tag in the scene when required.</span></span>
        3.  <span data-ttu-id="1c87d-274">**SpatialMapping**。これは、アプリケーションが Microsoft HoloLens の空間トラッキングを使用して仮想マップの作成を使用できるようにするオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="1c87d-274">The **SpatialMapping**, which is the object that enables the application to use create a virtual map, using the Microsoft HoloLens' spatial tracking.</span></span>

    4.  <span data-ttu-id="1c87d-275">このコースの構築済みシーンが現在含まれている **シーン** フォルダー。</span><span class="sxs-lookup"><span data-stu-id="1c87d-275">The **Scenes** folder which currently contains the pre-built scene for this course.</span></span>

4.  <span data-ttu-id="1c87d-276">[**プロジェクト] パネル** で [**シーン**] フォルダーを開き、 **ObjDetectionScene** をダブルクリックして、このコースで使用するシーンを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-276">Open the **Scenes** folder, in the **Project Panel**, and double-click on the **ObjDetectionScene**, to load the scene that you will use for this course.</span></span>

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  <span data-ttu-id="1c87d-277">**コードは含ま** れていません。このコースに従ってコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-277">**No code is included**, you will write the code by following this course.</span></span>

## <a name="chapter-5---create-the-customvisionanalyser-class"></a><span data-ttu-id="1c87d-278">Chapter 5-CustomVisionAnalyser クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-278">Chapter 5 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="1c87d-279">この時点で、コードを記述する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="1c87d-279">At this point you are ready to write some code.</span></span> <span data-ttu-id="1c87d-280">最初に、 **CustomVisionAnalyser** クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-280">You will begin with the **CustomVisionAnalyser** class.</span></span>

> [!NOTE]
> <span data-ttu-id="1c87d-281">次に示すコードで作成された **Custom Vision Service** への呼び出しは、 **Custom Vision REST API** を使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-281">The calls to the **Custom Vision Service**, made in the code shown below, are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="1c87d-282">これを使用すると、この API を実装して使用する方法を確認できます (独自のものを実装する方法を理解するために役立ちます)。</span><span class="sxs-lookup"><span data-stu-id="1c87d-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="1c87d-283">Microsoft では、サービスの呼び出しを行うために使用できる **CUSTOM VISION SDK** を提供していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1c87d-283">Be aware, that Microsoft offers a **Custom Vision SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="1c87d-284">詳細については、 [CUSTOM VISION SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1c87d-284">For more information visit the [Custom Vision SDK article](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span></span>

<span data-ttu-id="1c87d-285">このクラスの役割は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1c87d-285">This class is responsible for:</span></span>

- <span data-ttu-id="1c87d-286">バイト配列としてキャプチャされた最新のイメージを読み込んでいます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-286">Loading the latest image captured as an array of bytes.</span></span>

- <span data-ttu-id="1c87d-287">分析のために、Azure **Custom Vision Service** インスタンスにバイト配列を送信しています。</span><span class="sxs-lookup"><span data-stu-id="1c87d-287">Sending the byte array to your Azure **Custom Vision Service** instance for analysis.</span></span>

- <span data-ttu-id="1c87d-288">JSON 文字列として応答を受信しています。</span><span class="sxs-lookup"><span data-stu-id="1c87d-288">Receiving the response as a JSON string.</span></span>

- <span data-ttu-id="1c87d-289">応答を逆シリアル化し、結果の **予測** を **SceneOrganiser** クラスに渡します。これにより、応答の表示方法が決まります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-289">Deserializing the response and passing the resulting **Prediction** to the **SceneOrganiser** class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="1c87d-290">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="1c87d-290">To create this class:</span></span>

1.  <span data-ttu-id="1c87d-291">[**プロジェクト] パネル** にある **アセットフォルダー** を右クリックし、[フォルダーの **作成**] をクリックし  >  ます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-291">Right-click in the **Asset Folder**, located in the **Project Panel**, then click **Create** > **Folder**.</span></span> <span data-ttu-id="1c87d-292">フォルダー **スクリプト** を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab310-37.png)

2.  <span data-ttu-id="1c87d-293">新しく作成したフォルダーをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-293">Double-click on the newly created folder, to open it.</span></span>

3.  <span data-ttu-id="1c87d-294">フォルダー内を右クリックし、[   >  **C \# スクリプト** の作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="1c87d-295">スクリプトに CustomVisionAnalyser という名前を指定 **します。**</span><span class="sxs-lookup"><span data-stu-id="1c87d-295">Name the script **CustomVisionAnalyser.**</span></span>

4.  <span data-ttu-id="1c87d-296">新しい **CustomVisionAnalyser** スクリプトをダブルクリックして、 **Visual Studio で開きます。**</span><span class="sxs-lookup"><span data-stu-id="1c87d-296">Double-click on the new **CustomVisionAnalyser** script to open it with **Visual Studio.**</span></span>

5.  <span data-ttu-id="1c87d-297">ファイルの先頭で次の名前空間が参照されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-297">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="1c87d-298">**CustomVisionAnalyser** クラスに、次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-298">In the **CustomVisionAnalyser** class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="1c87d-299">**PredictionKey** 変数に **サービス予測キー** を挿入し、**予測エンドポイント** を **predictionEndpoint** 変数に挿入してください。</span><span class="sxs-lookup"><span data-stu-id="1c87d-299">Make sure you insert your **Service Prediction-Key** into the **predictionKey** variable and your **Prediction-Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="1c87d-300">[前の手順14でメモ帳](#chapter-2---training-your-custom-vision-project)にコピーしました。</span><span class="sxs-lookup"><span data-stu-id="1c87d-300">You copied these to [Notepad earlier, in Chapter 2, Step 14](#chapter-2---training-your-custom-vision-project).</span></span>

7.  <span data-ttu-id="1c87d-301">インスタンス変数を初期化するには、起動前 **()** のコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="1c87d-302">コルーチンを (static **GetImageAsByteArray ()** メソッドを使用して) 追加します。これにより、 **imagecapture** クラスによってキャプチャされたイメージの分析結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-302">Add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image, captured by the **ImageCapture** class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1c87d-303">**分析 Seimagecapture** コルーチンには、まだ作成していない **SceneOrganiser** クラスの呼び出しがあります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-303">In the **AnalyseImageCapture** coroutine, there is a call to the **SceneOrganiser** class that you are yet to create.</span></span> <span data-ttu-id="1c87d-304">そのため、 **これらの行はコメントの付いたままに** しておきます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-304">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

9. <span data-ttu-id="1c87d-305">**Start ()** および **Update ()** メソッドは使用されないため、削除します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-305">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span> 

10.  <span data-ttu-id="1c87d-306">**Unity** に戻る前に、変更内容を **Visual Studio** に保存しておいてください。</span><span class="sxs-lookup"><span data-stu-id="1c87d-306">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1c87d-307">前に説明したように、エラーが発生する可能性があるコードについては気にしないでください。これにより、後でさらにクラスを修正します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-307">As mentioned earlier, do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-6---create-the-customvisionobjects-class"></a><span data-ttu-id="1c87d-308">Chapter 6-CustomVisionObjects クラスの作成</span><span class="sxs-lookup"><span data-stu-id="1c87d-308">Chapter 6 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="1c87d-309">ここで作成するクラスは、 **CustomVisionObjects** クラスです。</span><span class="sxs-lookup"><span data-stu-id="1c87d-309">The class you will create now is the **CustomVisionObjects** class.</span></span>

<span data-ttu-id="1c87d-310">このスクリプトには、Custom Vision Service に対する呼び出しをシリアル化および逆シリアル化するために、他のクラスによって使用される多数のオブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1c87d-310">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the Custom Vision Service.</span></span>

<span data-ttu-id="1c87d-311">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="1c87d-311">To create this class:</span></span>

1.  <span data-ttu-id="1c87d-312">**Scripts** フォルダー内を右クリックし、[ **Create**  >  **C \# Script**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-312">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="1c87d-313">スクリプト CustomVisionObjects を呼び出し **ます。**</span><span class="sxs-lookup"><span data-stu-id="1c87d-313">Call the script **CustomVisionObjects.**</span></span>

2.  <span data-ttu-id="1c87d-314">新しい **CustomVisionObjects** スクリプトをダブルクリックして、 **Visual Studio で開きます。**</span><span class="sxs-lookup"><span data-stu-id="1c87d-314">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="1c87d-315">ファイルの先頭で次の名前空間が参照されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-315">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="1c87d-316">**CustomVisionObjects** クラス内の **Start ()** および **Update ()** メソッドを削除します。このクラスは空になります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-316">Delete the **Start()** and **Update()** methods inside the **CustomVisionObjects** class, this class should now be empty.</span></span>

    > [!WARNING]
    > <span data-ttu-id="1c87d-317">次の手順に従うことが重要です。</span><span class="sxs-lookup"><span data-stu-id="1c87d-317">It is important you follow the next instruction carefully.</span></span> <span data-ttu-id="1c87d-318">**CustomVisionObjects** クラス内に新しいクラス宣言を配置すると、 **AnalysisRootObject** と **BoundingBox** が見つからないことを示す [10 章](#chapter-10---create-the-imagecapture-class)のコンパイルエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-318">If you put the new class declarations inside the **CustomVisionObjects** class, you will get compile errors in [chapter 10](#chapter-10---create-the-imagecapture-class), stating that **AnalysisRootObject** and **BoundingBox** are not found.</span></span>

5.  <span data-ttu-id="1c87d-319">**CustomVisionObjects** クラスの *外* に次のクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-319">Add the following classes *outside* the **CustomVisionObjects** class.</span></span> <span data-ttu-id="1c87d-320">これらのオブジェクトは、応答データをシリアル化および逆シリアル化するために **Newtonsoft** ライブラリによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-320">These objects are used by the **Newtonsoft** library to serialize and deserialize the response data:</span></span>

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  <span data-ttu-id="1c87d-321">**Unity** に戻る前に、変更内容を **Visual Studio** に保存しておいてください。</span><span class="sxs-lookup"><span data-stu-id="1c87d-321">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-spatialmapping-class"></a><span data-ttu-id="1c87d-322">第7章-SpatialMapping クラスの作成</span><span class="sxs-lookup"><span data-stu-id="1c87d-322">Chapter 7 - Create the SpatialMapping class</span></span>

<span data-ttu-id="1c87d-323">このクラスは、仮想オブジェクトと実際のオブジェクト間の競合を検出できるように、シーンで **空間マッピング Collider** を設定します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-323">This class will set the **Spatial Mapping Collider** in the scene so to be able to detect collisions between virtual objects and real objects.</span></span>

<span data-ttu-id="1c87d-324">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="1c87d-324">To create this class:</span></span>

1.  <span data-ttu-id="1c87d-325">**Scripts** フォルダー内を右クリックし、[ **Create**  >  **C \# Script**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-325">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="1c87d-326">スクリプト SpatialMapping を呼び出し **ます。**</span><span class="sxs-lookup"><span data-stu-id="1c87d-326">Call the script **SpatialMapping.**</span></span>

2.  <span data-ttu-id="1c87d-327">新しい **SpatialMapping** スクリプトをダブルクリックして、 **Visual Studio で開きます。**</span><span class="sxs-lookup"><span data-stu-id="1c87d-327">Double-click on the new **SpatialMapping** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="1c87d-328">**SpatialMapping** クラスの上に参照されている次の名前空間があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-328">Make sure you have the following namespaces referenced above the **SpatialMapping** class:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  <span data-ttu-id="1c87d-329">次に、 **Start ()** メソッドの上に、 **SpatialMapping** クラス内に次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-329">Then, add the following variables inside the **SpatialMapping** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  <span data-ttu-id="1c87d-330">起動した **()** を追加し、 **Start ()** を追加します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-330">Add the **Awake()** and **Start()**:</span></span>

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  <span data-ttu-id="1c87d-331">**Update ()** メソッドを削除します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-331">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="1c87d-332">**Unity** に戻る前に、変更内容を **Visual Studio** に保存しておいてください。</span><span class="sxs-lookup"><span data-stu-id="1c87d-332">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>


## <a name="chapter-8---create-the-gazecursor-class"></a><span data-ttu-id="1c87d-333">章 8-GazeCursor クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="1c87d-333">Chapter 8 - Create the GazeCursor class</span></span>

<span data-ttu-id="1c87d-334">このクラスは、前の章で作成した **SpatialMappingCollider** を使用することによって、実際の場所にカーソルを適切な位置に設定する役割を担います。</span><span class="sxs-lookup"><span data-stu-id="1c87d-334">This class is responsible for setting up the cursor in the correct location in real space, by making use of the **SpatialMappingCollider**, created in the previous chapter.</span></span>

<span data-ttu-id="1c87d-335">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="1c87d-335">To create this class:</span></span>

1.  <span data-ttu-id="1c87d-336">**Scripts** フォルダー内を右クリックし、[ **Create**  >  **C \# Script**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-336">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="1c87d-337">**GazeCursor** スクリプトを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-337">Call the script **GazeCursor**</span></span>

2.  <span data-ttu-id="1c87d-338">新しい **GazeCursor** スクリプトをダブルクリックして、 **Visual Studio で開きます。**</span><span class="sxs-lookup"><span data-stu-id="1c87d-338">Double-click on the new **GazeCursor** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="1c87d-339">**GazeCursor** クラスの上に、次の名前空間が参照されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-339">Make sure you have the following namespace referenced above the **GazeCursor** class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="1c87d-340">次に、 **Start ()** メソッドの上に、 **GazeCursor** クラス内に次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-340">Then add the following variable inside the **GazeCursor** class, above the **Start()** method.</span></span> 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  <span data-ttu-id="1c87d-341">**Start ()** メソッドを次のコードで更新します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-341">Update the **Start()** method with the following code:</span></span>

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  <span data-ttu-id="1c87d-342">**Update ()** メソッドを次のコードで更新します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-342">Update the **Update()** method with the following code:</span></span>

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > <span data-ttu-id="1c87d-343">**SceneOrganiser** クラスが見つからない場合のエラーについては、次の章で作成します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-343">Do not worry about the error for the **SceneOrganiser** class not being found, you will create it in the next chapter.</span></span>

7. <span data-ttu-id="1c87d-344">**Unity** に戻る前に、変更内容を **Visual Studio** に保存しておいてください。</span><span class="sxs-lookup"><span data-stu-id="1c87d-344">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-9---create-the-sceneorganiser-class"></a><span data-ttu-id="1c87d-345">第9章-SceneOrganiser クラスの作成</span><span class="sxs-lookup"><span data-stu-id="1c87d-345">Chapter 9 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="1c87d-346">このクラスは次のことを行います。</span><span class="sxs-lookup"><span data-stu-id="1c87d-346">This class will:</span></span>

-   <span data-ttu-id="1c87d-347">適切なコンポーネントをアタッチして、 *メインカメラ* を設定します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-347">Set up the *Main Camera* by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="1c87d-348">オブジェクトが検出されると、実際の世界での位置を計算し、適切な **タグ名** の近くに **タグラベル** を配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-348">When an object is detected, it will be responsible for calculating its position in the real world and place a **Tag Label** near it with the appropriate **Tag Name**.</span></span>    

<span data-ttu-id="1c87d-349">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="1c87d-349">To create this class:</span></span>

1.  <span data-ttu-id="1c87d-350">**Scripts** フォルダー内を右クリックし、[ **Create**  >  **C \# Script**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-350">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="1c87d-351">スクリプトに **SceneOrganiser** という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-351">Name the script **SceneOrganiser**.</span></span>

2.  <span data-ttu-id="1c87d-352">新しい **SceneOrganiser** スクリプトをダブルクリックして、 **Visual Studio で開きます。**</span><span class="sxs-lookup"><span data-stu-id="1c87d-352">Double-click on the new **SceneOrganiser** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="1c87d-353">**SceneOrganiser** クラスの上に参照されている次の名前空間があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-353">Make sure you have the following namespaces referenced above the **SceneOrganiser** class:</span></span>

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  <span data-ttu-id="1c87d-354">次に、 **Start ()** メソッドの上に、 **SceneOrganiser** クラス内に次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-354">Then add the following variables inside the **SceneOrganiser** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  <span data-ttu-id="1c87d-355">**Start ()** および **Update ()** メソッドを削除します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-355">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="1c87d-356">変数の下に、起動前 **()** メソッドを追加します。このメソッドは、クラスを初期化し、シーンを設定します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-356">Underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  <span data-ttu-id="1c87d-357">**PlaceAnalysisLabel ()** メソッドを追加します。このメソッドは、シーン内のラベルを *インスタンス化* します (この時点ではユーザーには表示されません)。</span><span class="sxs-lookup"><span data-stu-id="1c87d-357">Add the **PlaceAnalysisLabel()** method, which will *Instantiate* the label in the scene (which at this point is invisible to the user).</span></span> <span data-ttu-id="1c87d-358">また、イメージが配置されている四角形も、実際の世界と重複しています。</span><span class="sxs-lookup"><span data-stu-id="1c87d-358">It also places the quad (also invisible) where the image is placed, and overlaps with the real world.</span></span> <span data-ttu-id="1c87d-359">これが重要なのは、分析後にサービスから取得したボックスの座標が、実際のオブジェクトのおおよその場所を決定するために、このクワッドにトレースされます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-359">This is important because the box coordinates retrieved from the Service after analysis are traced back into this quad to determined the approximate location of the object in the real world.</span></span> 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  <span data-ttu-id="1c87d-360">**FinaliseLabel ()** メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-360">Add the **FinaliseLabel()** method.</span></span> <span data-ttu-id="1c87d-361">以下の処理を担当します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-361">It is responsible for:</span></span>

    *   <span data-ttu-id="1c87d-362">*ラベル* のテキストに、最も信頼度の高い予測の *タグ* を設定します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-362">Setting the *Label* text with the *Tag* of the Prediction with the highest confidence.</span></span>
    *   <span data-ttu-id="1c87d-363">前に配置した、四角形の *境界ボックス* の計算を呼び出し、そのラベルをシーンに配置します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-363">Calling the calculation of the *Bounding Box* on the quad object, positioned previously, and placing the label in the scene.</span></span>
    *   <span data-ttu-id="1c87d-364">*境界ボックス* に向かって Raycast を使用してラベルの深さを調整します。これは、実際の世界のオブジェクトに対して競合します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-364">Adjusting the label depth by using a Raycast towards the *Bounding Box*, which should collide against the object in the real world.</span></span>
    * <span data-ttu-id="1c87d-365">キャプチャプロセスをリセットして、ユーザーが別のイメージをキャプチャできるようにします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-365">Resetting the capture process to allow the user to capture another image.</span></span>

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  <span data-ttu-id="1c87d-366">**CalculateBoundingBoxPosition ()** メソッドを追加します。このメソッドは、サービスから取得された *境界ボックス* 座標を変換するために必要な多数の計算をホストし、それらを4つに均等に再作成します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-366">Add the **CalculateBoundingBoxPosition()** method, which hosts a number of calculations necessary to translate the *Bounding Box* coordinates retrieved from the Service and recreate them proportionally on the quad.</span></span>

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. <span data-ttu-id="1c87d-367">**Unity** に戻る前に、変更内容を **Visual Studio** に保存しておいてください。</span><span class="sxs-lookup"><span data-stu-id="1c87d-367">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="1c87d-368">続行する前に、 **CustomVisionAnalyser** クラスを開き、 **AnalyseLastImageCaptured ()** メソッド内で次の行を *コメント* 解除します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-368">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> <span data-ttu-id="1c87d-369">**Imagecapture** クラス ' found ' が見つからないことを心配しないでください。このメッセージは、次の章で作成します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-369">Do not worry about the **ImageCapture** class 'could not be found' message, you will create it in the next chapter.</span></span>


## <a name="chapter-10---create-the-imagecapture-class"></a><span data-ttu-id="1c87d-370">Chapter 10-ImageCapture クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="1c87d-370">Chapter 10 - Create the ImageCapture class</span></span>

<span data-ttu-id="1c87d-371">次に作成するクラスは、 **Imagecapture** クラスです。</span><span class="sxs-lookup"><span data-stu-id="1c87d-371">The next class you are going to create is the **ImageCapture** class.</span></span>

<span data-ttu-id="1c87d-372">このクラスの役割は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1c87d-372">This class is responsible for:</span></span>

*   <span data-ttu-id="1c87d-373">HoloLens カメラを使用してイメージをキャプチャし、 *アプリ* フォルダーに格納します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-373">Capturing an image using the HoloLens camera and storing it in the *App* folder.</span></span>
*   <span data-ttu-id="1c87d-374">ユーザーからの *Tap* ジェスチャを処理します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-374">Handling *Tap* gestures from the user.</span></span>

<span data-ttu-id="1c87d-375">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="1c87d-375">To create this class:</span></span>

1.  <span data-ttu-id="1c87d-376">前に作成した **Scripts** フォルダーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-376">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="1c87d-377">フォルダー内を右クリックし、[   >  **C \# スクリプト** の作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-377">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="1c87d-378">スクリプトに「 **Imagecapture**」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-378">Name the script **ImageCapture**.</span></span>

3.  <span data-ttu-id="1c87d-379">新しい **Imagecapture** スクリプトをダブルクリックして、 **Visual Studio で開きます。**</span><span class="sxs-lookup"><span data-stu-id="1c87d-379">Double-click on the new **ImageCapture** script to open it with **Visual Studio.**</span></span>

4.  <span data-ttu-id="1c87d-380">ファイルの先頭にある名前空間を次のように置き換えます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-380">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="1c87d-381">次に、 **Start ()** メソッドの上に、 **imagecapture** クラス内に次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-381">Then add the following variables inside the **ImageCapture** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="1c87d-382">起動可能な **()** メソッドと **Start ()** メソッドのコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-382">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="1c87d-383">Tap ジェスチャが発生したときに呼び出されるハンドラーを実装します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-383">Implement a handler that will be called when a Tap gesture occurs:</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="1c87d-384">カーソルが **緑色** の場合は、カメラを使用してイメージを撮影できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-384">When the cursor is **green**, it means the camera is available to take the image.</span></span> <span data-ttu-id="1c87d-385">カーソルが **赤** の場合、カメラがビジー状態であることを示します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-385">When the cursor is **red**, it means the camera is busy.</span></span>

8.  <span data-ttu-id="1c87d-386">アプリケーションがイメージキャプチャプロセスを開始してイメージを格納するために使用するメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-386">Add the method that the application uses to start the image capture process and store the image:</span></span>

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });
        }
    ```

9.  <span data-ttu-id="1c87d-387">写真がキャプチャされ、分析の準備ができたときに呼び出されるハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-387">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="1c87d-388">結果は、分析のために **CustomVisionAnalyser** に渡されます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-388">The result is then passed to the **CustomVisionAnalyser** for analysis.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="1c87d-389">**Unity** に戻る前に、変更内容を **Visual Studio** に保存しておいてください。</span><span class="sxs-lookup"><span data-stu-id="1c87d-389">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a><span data-ttu-id="1c87d-390">Chapter 11-シーンでのスクリプトの設定</span><span class="sxs-lookup"><span data-stu-id="1c87d-390">Chapter 11 - Setting up the scripts in the scene</span></span>

<span data-ttu-id="1c87d-391">このプロジェクトに必要なすべてのコードを記述したので、次はシーンでスクリプトを設定し、prefabs でスクリプトを正しく動作させるための時間です。</span><span class="sxs-lookup"><span data-stu-id="1c87d-391">Now that you have written all of the code necessary for this project, is time to set up the scripts in the scene, and on the prefabs, for them to behave correctly.</span></span>

1.  <span data-ttu-id="1c87d-392">**Unity エディター** で、[**階層] パネル** の **メインカメラ** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-392">Within the **Unity Editor**, in the **Hierarchy Panel**, select the **Main Camera**.</span></span>
2.  <span data-ttu-id="1c87d-393">[ **インスペクター] パネル** で、 **メインカメラ** を選択した状態で [ **コンポーネントの追加**] をクリックし、 **SceneOrganiser** script を検索して、ダブルクリックして追加します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-393">In the **Inspector Panel**, with the **Main Camera** selected, click on **Add Component**, then search for **SceneOrganiser** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-38.png)

3.  <span data-ttu-id="1c87d-394">[**プロジェクト] パネル** で、 **Prefabs フォルダー** を開き、次の図に示すように、*メインカメラ* に追加した **SceneOrganiser** スクリプト内の [空の参照ターゲットの *ラベルのラベル*] に "prefab" と **いうラベルを** ドラッグします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-394">In the **Project Panel**, open the **Prefabs folder**, drag the **Label** prefab into the *Label* empty reference target input area, in the **SceneOrganiser** script that you have just added to the *Main Camera*, as shown in the image below:</span></span>

    ![](images/AzureLabs-Lab310-39.png)

4.  <span data-ttu-id="1c87d-395">[**階層] パネル** で、**メインカメラ** の **GazeCursor** 子を選択します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-395">In the **Hierarchy Panel**, select the **GazeCursor** child of the **Main Camera**.</span></span>
5.  <span data-ttu-id="1c87d-396">[ **インスペクター] パネル** で、 **GazeCursor** を選択した状態で [ **コンポーネントの追加**] をクリックし、 **GazeCursor** スクリプトを検索して、ダブルクリックして追加します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-396">In the **Inspector Panel**, with the **GazeCursor** selected, click on **Add Component**, then search for **GazeCursor** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-40.png)

6.  <span data-ttu-id="1c87d-397">ここでも、[**階層] パネル** で、**メインカメラ** の **SpatialMapping** 子を選択します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-397">Again, in the **Hierarchy Panel**, select the **SpatialMapping** child of the **Main Camera**.</span></span>
7.  <span data-ttu-id="1c87d-398">[ **インスペクター] パネル** で、 **SpatialMapping** を選択した状態で [ **コンポーネントの追加**] をクリックし、 **SpatialMapping** スクリプトを検索して、ダブルクリックして追加します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-398">In the **Inspector Panel**, with the **SpatialMapping** selected, click on **Add Component**, then search for **SpatialMapping** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-41.png)

<span data-ttu-id="1c87d-399">まだ設定していない残りのスクリプトは、実行時に **SceneOrganiser** スクリプトのコードによって追加されます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-399">The remaining scripts thats you have not set will be added by the code in the **SceneOrganiser** script, during runtime.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="1c87d-400">第12章-ビルド前</span><span class="sxs-lookup"><span data-stu-id="1c87d-400">Chapter 12 - Before building</span></span>

<span data-ttu-id="1c87d-401">アプリケーションの徹底的なテストを実行するには、Microsoft HoloLens にサイドロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-401">To perform a thorough test of your application you will need to sideload it onto your Microsoft HoloLens.</span></span>

<span data-ttu-id="1c87d-402">これを行う前に、次のことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1c87d-402">Before you do, ensure that:</span></span>

-  <span data-ttu-id="1c87d-403">[章 3](#chapter-3---set-up-the-unity-project)で説明したすべての設定が正しく設定されています。</span><span class="sxs-lookup"><span data-stu-id="1c87d-403">All the settings mentioned in the [Chapter 3](#chapter-3---set-up-the-unity-project) are set correctly.</span></span>
- <span data-ttu-id="1c87d-404">スクリプト **SceneOrganiser** は、 **メインカメラ** オブジェクトにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-404">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>
- <span data-ttu-id="1c87d-405">スクリプト **GazeCursor** は、 **GazeCursor** オブジェクトにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-405">The script **GazeCursor** is attached to the **GazeCursor** object.</span></span>
- <span data-ttu-id="1c87d-406">スクリプト **SpatialMapping** は、 **SpatialMapping** オブジェクトにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-406">The script **SpatialMapping** is attached to the **SpatialMapping** object.</span></span>
- <span data-ttu-id="1c87d-407">[第5章](#chapter-5---create-the-customvisionanalyser-class)の手順 6:</span><span class="sxs-lookup"><span data-stu-id="1c87d-407">In [Chapter 5](#chapter-5---create-the-customvisionanalyser-class), Step 6:</span></span>

    - <span data-ttu-id="1c87d-408">**サービス予測キー** を **predictionKey** 変数に挿入していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-408">Make sure you insert your **Service Prediction Key** into the **predictionKey** variable.</span></span>
    - <span data-ttu-id="1c87d-409">**予測エンドポイント** を **predictionEndpoint** クラスに挿入しました。</span><span class="sxs-lookup"><span data-stu-id="1c87d-409">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** class.</span></span>

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a><span data-ttu-id="1c87d-410">第13章-UWP ソリューションのビルドとアプリケーションのサイドロード</span><span class="sxs-lookup"><span data-stu-id="1c87d-410">Chapter 13 - Build the UWP solution and sideload your application</span></span>

<span data-ttu-id="1c87d-411">これで、Microsoft HoloLens にデプロイできる UWP ソリューションとしてアプリケーションを構築する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="1c87d-411">You are now ready to build you application as a UWP Solution that you will be able to deploy on to the Microsoft HoloLens.</span></span> <span data-ttu-id="1c87d-412">ビルドプロセスを開始するには:</span><span class="sxs-lookup"><span data-stu-id="1c87d-412">To begin the build process:</span></span>

1.  <span data-ttu-id="1c87d-413">**ファイル > ビルド設定** にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-413">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="1c87d-414">**Unity C \# プロジェクト** をティックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-414">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="1c87d-415">[開いている **シーンの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-415">Click on **Add Open Scenes**.</span></span> <span data-ttu-id="1c87d-416">これにより、現在開いているシーンがビルドに追加されます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-416">This will add the currently open scene to the build.</span></span>

    ![](images/AzureLabs-Lab310-42.png)

4.  <span data-ttu-id="1c87d-417">[**ビルド**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-417">Click **Build**.</span></span> <span data-ttu-id="1c87d-418">Unity は *エクスプローラー* ウィンドウを起動します。このウィンドウでは、アプリを作成するフォルダーを作成して選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-418">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="1c87d-419">ここでそのフォルダーを作成し、「 **App**」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-419">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="1c87d-420">次に、 **アプリ** フォルダーを選択し、[ **フォルダーの選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-420">Then with the **App** folder selected, click **Select Folder**.</span></span>

5.  <span data-ttu-id="1c87d-421">Unity は、 **アプリ** フォルダーへのプロジェクトのビルドを開始します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-421">Unity will begin building your project to the **App** folder.</span></span>

6.  <span data-ttu-id="1c87d-422">Unity のビルドが完了すると (時間がかかる場合があります)、ビルドの場所で **ファイルエクスプローラー** ウィンドウを開きます (ウィンドウの上に常に表示されるとは限りませんが、新しいウィンドウが追加されたことが通知されます)。</span><span class="sxs-lookup"><span data-stu-id="1c87d-422">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

7.  <span data-ttu-id="1c87d-423">Microsoft HoloLens にデプロイするには、そのデバイスの IP アドレス (リモートデプロイの場合) が必要であり、 **開発者モード** も設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-423">To deploy on to Microsoft HoloLens, you will need the IP Address of that device (for Remote Deploy), and to ensure that it also has **Developer Mode** set.</span></span> <span data-ttu-id="1c87d-424">これを行うには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-424">To do this:</span></span>

    1.  <span data-ttu-id="1c87d-425">HoloLens を装着した後、 **設定** を開きます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-425">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="1c87d-426">[**ネットワーク & インターネット**  >  **wi-fi**  >  **詳細オプション]** にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-426">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="1c87d-427">**IPv4** アドレスをメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-427">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="1c87d-428">次に、[**設定**] に戻り、   >  **開発者の**& セキュリティを更新します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-428">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="1c87d-429">\**開発者モード\*\*\*をに* 設定します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-429">Set **Developer Mode** *On*.</span></span>

8.  <span data-ttu-id="1c87d-430">新しい Unity ビルド ( **アプリ** フォルダー) に移動し、 **Visual Studio** でソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-430">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

9.  <span data-ttu-id="1c87d-431">ソリューション構成で、[ **デバッグ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-431">In the Solution Configuration select **Debug**.</span></span>

10. <span data-ttu-id="1c87d-432">ソリューションプラットフォームで、[ **x86、リモートコンピューター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-432">In the Solution Platform, select **x86, Remote Machine**.</span></span> <span data-ttu-id="1c87d-433">リモートデバイスの **IP アドレス** (この場合は、メモした Microsoft HoloLens) を挿入するように求められます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-433">You will be prompted to insert the **IP address** of a remote device (the Microsoft HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab310-43.png)

11. <span data-ttu-id="1c87d-434">[ **ビルド** ] メニューの [ソリューションの **配置** ] をクリックして、アプリケーションを HoloLens にサイドロードします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-434">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

12. <span data-ttu-id="1c87d-435">アプリが Microsoft HoloLens のインストール済みアプリの一覧に表示され、起動できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-435">Your app should now appear in the list of installed apps on your Microsoft HoloLens, ready to be launched!</span></span>

### <a name="to-use-the-application"></a><span data-ttu-id="1c87d-436">アプリケーションを使用するには:</span><span class="sxs-lookup"><span data-stu-id="1c87d-436">To use the application:</span></span>

* <span data-ttu-id="1c87d-437">**Azure Custom Vision Service、オブジェクト検出** でトレーニングしたオブジェクトを調べ、 **Tap ジェスチャ** を使用します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-437">Look at an object, which you have trained with your **Azure Custom Vision Service, Object Detection**, and use the **Tap gesture**.</span></span>
* <span data-ttu-id="1c87d-438">オブジェクトが正常に検出された場合は、ワールドスペースの *ラベルのテキスト* がタグ名と共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-438">If the object is successfully detected, a world-space *Label Text* will appear with the tag name.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1c87d-439">写真をキャプチャしてサービスに送信するたびに、サービスページに戻り、新しくキャプチャしたイメージでサービスを再トレーニングすることができます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-439">Every time you capture a photo and send it to the Service, you can go back to the Service page and retrain the Service with the newly captured images.</span></span> <span data-ttu-id="1c87d-440">最初に、 *境界ボックス* を修正して、より正確でサービスを再トレーニングする必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-440">At the beginning, you will probably also have to correct the *Bounding Boxes* to be more accurate and retrain the Service.</span></span>

> [!NOTE]
> <span data-ttu-id="1c87d-441">Microsoft HoloLens センサーや Unity の SpatialTrackingComponent が、実際のオブジェクトに対する適切な colliders の配置に失敗した場合、オブジェクトの近くにラベルのテキストが表示されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="1c87d-441">The Label Text placed might not appear near the object when the Microsoft HoloLens sensors and/or the SpatialTrackingComponent in Unity fails to place the appropriate colliders, relative to the real world objects.</span></span> <span data-ttu-id="1c87d-442">そのような場合は、別の画面でアプリケーションを使用してみてください。</span><span class="sxs-lookup"><span data-stu-id="1c87d-442">Try to use the application on a different surface if that is the case.</span></span>

## <a name="your-custom-vision-object-detection-application"></a><span data-ttu-id="1c87d-443">Custom Vision、オブジェクト検出アプリケーション</span><span class="sxs-lookup"><span data-stu-id="1c87d-443">Your Custom Vision, Object Detection application</span></span>

<span data-ttu-id="1c87d-444">これで、Azure Custom Vision、オブジェクト検出 API を活用する mixed reality アプリが作成されました。これにより、イメージからオブジェクトを認識し、3D 空間でそのオブジェクトのおおよその位置を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1c87d-444">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision, Object Detection API, which can recognize an object from an image, and then provide an approximate position for that object in 3D space.</span></span>

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="1c87d-445">ボーナス演習</span><span class="sxs-lookup"><span data-stu-id="1c87d-445">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="1c87d-446">演習1</span><span class="sxs-lookup"><span data-stu-id="1c87d-446">Exercise 1</span></span>

<span data-ttu-id="1c87d-447">テキストラベルにを追加する場合は、半透明のキューブを使用して、3D *境界ボックス* に実際のオブジェクトをラップします。</span><span class="sxs-lookup"><span data-stu-id="1c87d-447">Adding to the Text Label, use a semi-transparent cube to wrap the real object in a 3D *Bounding Box*.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="1c87d-448">演習2</span><span class="sxs-lookup"><span data-stu-id="1c87d-448">Exercise 2</span></span>

<span data-ttu-id="1c87d-449">Custom Vision Service をトレーニングして、より多くのオブジェクトを認識します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-449">Train your Custom Vision Service to recognize more objects.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="1c87d-450">演習3</span><span class="sxs-lookup"><span data-stu-id="1c87d-450">Exercise 3</span></span>

<span data-ttu-id="1c87d-451">オブジェクトが認識されたときにサウンドを再生します。</span><span class="sxs-lookup"><span data-stu-id="1c87d-451">Play a sound when an object is recognized.</span></span>

### <a name="exercise-4"></a><span data-ttu-id="1c87d-452">演習4</span><span class="sxs-lookup"><span data-stu-id="1c87d-452">Exercise 4</span></span>

<span data-ttu-id="1c87d-453">API を使用して、アプリが分析しているのと同じイメージでサービスを再トレーニングします。これにより、サービスの精度が向上します (予測とトレーニングの両方を同時に行うことができます)。</span><span class="sxs-lookup"><span data-stu-id="1c87d-453">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
