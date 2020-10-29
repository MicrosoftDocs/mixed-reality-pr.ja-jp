---
title: MR と Azure 302b-カスタムビジョン
description: このコースでは、機械学習モデルをトレーニングし、トレーニング済みのモデルを使用して、mixed reality アプリケーション内で類似のオブジェクトを認識する方法を学習します。
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, チュートリアル, api, カスタムビジョン, hololens, イマーシブ, vr
ms.openlocfilehash: 857cdc00daa94db5bb4d4fda1d5adfcf0ba28822
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91688122"
---
# <a name="mr-and-azure-302b-custom-vision"></a><span data-ttu-id="498cc-104">MR と Azure 302b:カスタム ビジョン</span><span class="sxs-lookup"><span data-stu-id="498cc-104">MR and Azure 302b: Custom vision</span></span>

<br>

>[!NOTE]
><span data-ttu-id="498cc-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="498cc-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="498cc-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="498cc-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="498cc-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは " **_ありません_** "。</span><span class="sxs-lookup"><span data-stu-id="498cc-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="498cc-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="498cc-109">今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="498cc-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="498cc-110">この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>


<span data-ttu-id="498cc-111">このコースでは、混合現実アプリケーションで Azure Custom Vision の機能を使用して、提供されたイメージ内のカスタムビジュアルコンテンツを認識する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="498cc-111">In this course, you will learn how to recognize custom visual content within a provided image, using Azure Custom Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="498cc-112">このサービスでは、オブジェクトイメージを使用して機械学習モデルをトレーニングすることができます。</span><span class="sxs-lookup"><span data-stu-id="498cc-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="498cc-113">次に、トレーニング済みのモデルを使用して類似のオブジェクトを認識します。これは、Microsoft HoloLens のカメラキャプチャや、PC for イマーシブ (VR) ヘッドセットに接続されたカメラによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-113">You will then use the trained model to recognize similar objects, as provided by the camera capture of Microsoft HoloLens or a camera connected to your PC for immersive (VR) headsets.</span></span>

![コースの結果](images/AzureLabs-Lab302b-00.png)

<span data-ttu-id="498cc-115">Azure Custom Vision は、開発者がカスタムイメージ分類子を構築できる Microsoft 認知サービスです。</span><span class="sxs-lookup"><span data-stu-id="498cc-115">Azure Custom Vision is a Microsoft Cognitive Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="498cc-116">これらの分類子を新しいイメージと共に使用して、新しいイメージ内のオブジェクトを認識したり、分類したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="498cc-116">These classifiers can then be used with new images to recognize, or classify, objects within that new image.</span></span> <span data-ttu-id="498cc-117">このサービスでは、簡単で使いやすいオンラインポータルを使用して、プロセスを効率化できます。</span><span class="sxs-lookup"><span data-stu-id="498cc-117">The Service provides a simple, easy to use, online portal to streamline the process.</span></span> <span data-ttu-id="498cc-118">詳細については、 [Azure Custom Vision Service のページ](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="498cc-118">For more information, visit the [Azure Custom Vision Service page](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span></span>

<span data-ttu-id="498cc-119">このコースが完了すると、2つのモードで動作できる mixed reality アプリケーションが完成します。</span><span class="sxs-lookup"><span data-stu-id="498cc-119">Upon completion of this course, you will have a mixed reality application which will be able to work in two modes:</span></span>

-   <span data-ttu-id="498cc-120">**分析モード** : イメージをアップロードし、タグを作成し、さまざまなオブジェクト (この場合はマウスとキーボード) を認識するようにサービスをトレーニングすることによって、Custom Vision Service を手動で設定します。</span><span class="sxs-lookup"><span data-stu-id="498cc-120">**Analysis Mode** : setting up the Custom Vision Service manually by uploading images, creating tags, and training the Service to recognize different objects (in this case mouse and keyboard).</span></span> <span data-ttu-id="498cc-121">次に、カメラを使用してイメージをキャプチャする HoloLens アプリを作成し、実際の環境でそれらのオブジェクトを認識します。</span><span class="sxs-lookup"><span data-stu-id="498cc-121">You will then create a HoloLens app that will capture images using the camera, and try to recognize those objects in the real world.</span></span>

-   <span data-ttu-id="498cc-122">**トレーニングモード** : アプリで "トレーニングモード" を有効にするコードを実装します。</span><span class="sxs-lookup"><span data-stu-id="498cc-122">**Training Mode** : you will implement code that will enable a "Training Mode" in your app.</span></span> <span data-ttu-id="498cc-123">トレーニングモードでは、HoloLens のカメラを使用してイメージをキャプチャし、キャプチャしたイメージをサービスにアップロードして、カスタムビジョンモデルをトレーニングすることができます。</span><span class="sxs-lookup"><span data-stu-id="498cc-123">The training mode will allow you to capture images using the HoloLens' camera, upload the captured images to the Service, and train the custom vision model.</span></span>

<span data-ttu-id="498cc-124">このコースでは、Custom Vision Service から Unity ベースのサンプルアプリケーションに結果を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="498cc-124">This course will teach you how to get the results from the Custom Vision Service into a Unity-based sample application.</span></span> <span data-ttu-id="498cc-125">これらの概念は、構築しているカスタムアプリケーションに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="498cc-125">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="498cc-126">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="498cc-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="498cc-127">コース</span><span class="sxs-lookup"><span data-stu-id="498cc-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="498cc-128"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="498cc-128"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="498cc-129"><a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="498cc-129"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="498cc-130">MR と Azure 302b:カスタム ビジョン</span><span class="sxs-lookup"><span data-stu-id="498cc-130">MR and Azure 302b: Custom vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="498cc-131">✔️</span><span class="sxs-lookup"><span data-stu-id="498cc-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="498cc-132">✔️</span><span class="sxs-lookup"><span data-stu-id="498cc-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="498cc-133">このコースでは主に HoloLens に焦点を当てていますが、このコースで学習する内容を Windows Mixed Reality イマーシブ (VR) ヘッドセットにも適用できます。</span><span class="sxs-lookup"><span data-stu-id="498cc-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="498cc-134">イマーシブ (VR) ヘッドセットにはアクセス可能なカメラがないため、外部カメラが PC に接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="498cc-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="498cc-135">コースを進めると、イマーシブ (VR) ヘッドセットをサポートするために必要な変更についての注意事項が表示されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="498cc-136">前提条件</span><span class="sxs-lookup"><span data-stu-id="498cc-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="498cc-137">このチュートリアルは、Unity と C# の基本的な経験がある開発者向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="498cc-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="498cc-138">また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証された内容 (2018 年7月) を表しています。</span><span class="sxs-lookup"><span data-stu-id="498cc-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="498cc-139">「 [ツールのインストール](../../install-the-tools.md) 」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に記載されているものより新しいソフトウェアの内容と完全に一致するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="498cc-139">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="498cc-140">このコースでは、次のハードウェアとソフトウェアをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="498cc-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="498cc-141">開発用 PC で、 [Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) (VR) ヘッドセット開発と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="498cc-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="498cc-142">開発者モードが有効になっている Windows 10 の作成者の更新プログラム (またはそれ以降)</span><span class="sxs-lookup"><span data-stu-id="498cc-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="498cc-143">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="498cc-143">The latest Windows 10 SDK</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="498cc-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="498cc-144">Unity 2017.4</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="498cc-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="498cc-145">Visual Studio 2017</span></span>](../../install-the-tools.md#installation-checklist)
- <span data-ttu-id="498cc-146">[Windows Mixed Reality イマーシブ (VR) ヘッドセット](../../../discover/immersive-headset-hardware-details.md)または開発者モードを有効にした[Microsoft HoloLens](../../../hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="498cc-146">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md) or [Microsoft HoloLens](../../../hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="498cc-147">PC に接続されているカメラ (イマーシブヘッドセット開発用)</span><span class="sxs-lookup"><span data-stu-id="498cc-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="498cc-148">Azure セットアップと Custom Vision API の取得のためのインターネットアクセス</span><span class="sxs-lookup"><span data-stu-id="498cc-148">Internet access for Azure setup and Custom Vision API retrieval</span></span>
- <span data-ttu-id="498cc-149">Custom Vision Service が認識するオブジェクトごとに、少なくとも5つのイメージ (10) が推奨されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-149">A series of at least five (5) images (ten (10) recommended) for each object that you would like the Custom Vision Service to recognize.</span></span> <span data-ttu-id="498cc-150">必要に応じて、 [このコースで既に提供されているイメージ (コンピューターマウスとキーボード) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)を使用できます。</span><span class="sxs-lookup"><span data-stu-id="498cc-150">If you wish, you can use [the images already provided with this course (a computer mouse and a keyboard) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="498cc-151">開始する前に</span><span class="sxs-lookup"><span data-stu-id="498cc-151">Before you start</span></span>

1.  <span data-ttu-id="498cc-152">このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="498cc-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="498cc-153">HoloLens をセットアップしてテストします。</span><span class="sxs-lookup"><span data-stu-id="498cc-153">Set up and test your HoloLens.</span></span> <span data-ttu-id="498cc-154">HoloLens のセットアップをサポートする必要がある場合は、 [hololens セットアップに関する記事にアクセスして](https://docs.microsoft.com/hololens/hololens-setup)ください。</span><span class="sxs-lookup"><span data-stu-id="498cc-154">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="498cc-155">新しい HoloLens アプリの開発を開始するときは、調整とセンサーのチューニングを実行することをお勧めします (ユーザーごとにこれらのタスクを実行するのに役立つ場合があります)。</span><span class="sxs-lookup"><span data-stu-id="498cc-155">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="498cc-156">調整の詳細については、 [「HoloLens の調整に関する記事へのリンク」を](../../../calibration.md#hololens-2)参照してください。</span><span class="sxs-lookup"><span data-stu-id="498cc-156">For help on Calibration, please follow this [link to the HoloLens Calibration article](../../../calibration.md#hololens-2).</span></span>

<span data-ttu-id="498cc-157">センサーチューニングの詳細については、 [HoloLens センサーチューニングに関する記事へのリンクを](../../../sensor-tuning.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="498cc-157">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](../../../sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-service-portal"></a><span data-ttu-id="498cc-158">章 1-Custom Vision Service ポータル</span><span class="sxs-lookup"><span data-stu-id="498cc-158">Chapter 1 - The Custom Vision Service Portal</span></span>

<span data-ttu-id="498cc-159">Azure で *Custom Vision Service* を使用するには、アプリケーションで使用できるようにサービスのインスタンスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="498cc-159">To use the *Custom Vision Service* in Azure, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="498cc-160">最初に、 [ *Custom Vision Service* メインページに移動](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)します。</span><span class="sxs-lookup"><span data-stu-id="498cc-160">First, [navigate to the *Custom Vision Service* main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="498cc-161">**[Get Started]** (開始) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-161">Click on the **Get Started** button.</span></span>

    ![Custom Vision Service を使ってみる](images/AzureLabs-Lab302b-01.png)

3.  <span data-ttu-id="498cc-163">*Custom Vision Service* ポータルにサインインします。</span><span class="sxs-lookup"><span data-stu-id="498cc-163">Sign in to the *Custom Vision Service* Portal.</span></span>

    ![ポータルへのサインイン](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > <span data-ttu-id="498cc-165">まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="498cc-165">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="498cc-166">このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。</span><span class="sxs-lookup"><span data-stu-id="498cc-166">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

4.  <span data-ttu-id="498cc-167">初めてログインした後は、 *サービスパネルの使用条件* を確認するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-167">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="498cc-168">条件に同意するには、チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="498cc-168">Click on the checkbox to agree to the terms.</span></span> <span data-ttu-id="498cc-169">[ **同意** する] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-169">Then click on **I agree** .</span></span>

    ![サービス使用条件](images/AzureLabs-Lab302b-03.png)

5.  <span data-ttu-id="498cc-171">使用条件に同意すると、ポータルの [ *プロジェクト* ] セクションに移動します。</span><span class="sxs-lookup"><span data-stu-id="498cc-171">Having agreed to the Terms, you will be navigated to the *Projects* section of the Portal.</span></span> <span data-ttu-id="498cc-172">[ **新しいプロジェクト** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-172">Click on **New Project** .</span></span>

    ![新しいプロジェクトの作成](images/AzureLabs-Lab302b-04.png)

6.  <span data-ttu-id="498cc-174">右側にタブが表示され、プロジェクトのフィールドを指定するように求められます。</span><span class="sxs-lookup"><span data-stu-id="498cc-174">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="498cc-175">プロジェクトの *名前* を挿入します。</span><span class="sxs-lookup"><span data-stu-id="498cc-175">Insert a *Name* for your project.</span></span>

    2.  <span data-ttu-id="498cc-176">プロジェクトの *説明* を挿入します ( *省略可能* )。</span><span class="sxs-lookup"><span data-stu-id="498cc-176">Insert a *Description* for your project ( *optional* ).</span></span>

    3.  <span data-ttu-id="498cc-177">リソースグループを選択するか、新しい *リソースグループ* を作成します。</span><span class="sxs-lookup"><span data-stu-id="498cc-177">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="498cc-178">リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="498cc-178">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="498cc-179">1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのコースなど) を共通のリソースグループに保持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="498cc-179">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    4. <span data-ttu-id="498cc-180">プロジェクトの *種類* を **分類** に設定する</span><span class="sxs-lookup"><span data-stu-id="498cc-180">Set the *Project Types* to **Classification**</span></span>
    
    5. <span data-ttu-id="498cc-181">*ドメイン* を **全般** として設定します。</span><span class="sxs-lookup"><span data-stu-id="498cc-181">Set the *Domains* as **General** .</span></span>

        ![ドメインを設定する](images/AzureLabs-Lab302b-05.png)

        > <span data-ttu-id="498cc-183">Azure リソースグループの詳細については、 [リソースグループ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="498cc-183">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

7.  <span data-ttu-id="498cc-184">完了すると、[プロジェクトの **作成** ] をクリックすると、[Custom Vision Service、プロジェクト] ページにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="498cc-184">Once you are finished, click on **Create project** , you will be redirected to the Custom Vision Service, project page.</span></span>

## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="498cc-185">第2章-Custom Vision プロジェクトのトレーニング</span><span class="sxs-lookup"><span data-stu-id="498cc-185">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="498cc-186">Custom Vision ポータルでは、主な目的は、イメージ内の特定のオブジェクトを認識するようにプロジェクトをトレーニングすることです。</span><span class="sxs-lookup"><span data-stu-id="498cc-186">Once in the Custom Vision portal, your primary objective is to train your project to recognize specific objects in images.</span></span> <span data-ttu-id="498cc-187">アプリケーションで認識するオブジェクトごとに、少なくとも5つのイメージが必要ですが、10 (10) が推奨されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-187">You need at least five (5) images, though ten (10) is preferred, for each object that you would like your application to recognize.</span></span> <span data-ttu-id="498cc-188">[このコースに用意されているイメージ (コンピューターマウスとキーボード) を使用でき](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)ます。</span><span class="sxs-lookup"><span data-stu-id="498cc-188">[You can use the images provided with this course (a computer mouse and a keyboard)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span> 

<span data-ttu-id="498cc-189">Custom Vision Service プロジェクトをトレーニングするには:</span><span class="sxs-lookup"><span data-stu-id="498cc-189">To train your Custom Vision Service project:</span></span>

1.  <span data-ttu-id="498cc-190">[タグ] の横にあるボタンをクリックし **+** **ます。**</span><span class="sxs-lookup"><span data-stu-id="498cc-190">Click on the **+** button next to **Tags.**</span></span>

    ![新しいタグを追加する](images/AzureLabs-Lab302b-06.png)

2.  <span data-ttu-id="498cc-192">認識するオブジェクトの **名前** を追加します。</span><span class="sxs-lookup"><span data-stu-id="498cc-192">Add the **name** of the object you would like to recognize.</span></span> <span data-ttu-id="498cc-193">**[Save]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-193">Click on **Save** .</span></span>

    ![オブジェクト名を追加して保存](images/AzureLabs-Lab302b-07.png)

3.  <span data-ttu-id="498cc-195">**タグ** が追加されていることがわかります (表示するには、ページの再読み込みが必要になる場合があります)。</span><span class="sxs-lookup"><span data-stu-id="498cc-195">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> <span data-ttu-id="498cc-196">まだ確認されていない場合は、新しいタグの横にあるチェックボックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-196">Click the checkbox alongside your new tag, if it is not already checked.</span></span>

    ![新しいタグを有効にする](images/AzureLabs-Lab302b-08.png)

4.  <span data-ttu-id="498cc-198">ページの中央にある [ **イメージの追加** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-198">Click on **Add Images** in the center of the page.</span></span>

    ![画像の追加](images/AzureLabs-Lab302b-09.png)

5.  <span data-ttu-id="498cc-200">[ **ローカルファイルの参照** ] をクリックし、アップロードするイメージを検索して選択します。最小値は 5 (5) です。</span><span class="sxs-lookup"><span data-stu-id="498cc-200">Click on **Browse local files** , and search, then select, the images you would like to upload, with the minimum being five (5).</span></span> <span data-ttu-id="498cc-201">これらのイメージには、トレーニングするオブジェクトが含まれている必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="498cc-201">Remember all of these images should contain the object which you are training.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="498cc-202">アップロードには、一度に複数のイメージを選択できます。</span><span class="sxs-lookup"><span data-stu-id="498cc-202">You can select several images at a time, to upload.</span></span>

6.  <span data-ttu-id="498cc-203">タブに画像が表示されたら、 **[マイタグ** ] ボックスで適切なタグを選択します。</span><span class="sxs-lookup"><span data-stu-id="498cc-203">Once you can see the images in the tab, select the appropriate tag in the **My Tags** box.</span></span>

    ![タグの選択](images/AzureLabs-Lab302b-10.png)

7.  <span data-ttu-id="498cc-205">[ **ファイルのアップロード** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-205">Click on **Upload files** .</span></span> <span data-ttu-id="498cc-206">ファイルのアップロードが開始されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-206">The files will begin uploading.</span></span> <span data-ttu-id="498cc-207">アップロードの確認が完了したら、[ **完了** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-207">Once you have confirmation of the upload, click **Done** .</span></span>

    ![ファイルのアップロード](images/AzureLabs-Lab302b-11.png)

8.  <span data-ttu-id="498cc-209">同じプロセスを繰り返して、 **キーボード** という名前の新しい **タグ** を作成し、適切な写真をアップロードします。</span><span class="sxs-lookup"><span data-stu-id="498cc-209">Repeat the same process to create a new **Tag** named **Keyboard** and upload the appropriate photos for it.</span></span> <span data-ttu-id="498cc-210">新しいタグを作成したら、 *マウス* を **オフ** にして、[イメージの *追加* ] ウィンドウを表示します。</span><span class="sxs-lookup"><span data-stu-id="498cc-210">Make sure to **uncheck** *Mouse* once you have created the new tags, so to show the *Add images* window.</span></span>

9.  <span data-ttu-id="498cc-211">両方のタグが設定されたら、[ **トレーニング** ] をクリックすると、最初のトレーニングイテレーションがビルドを開始します。</span><span class="sxs-lookup"><span data-stu-id="498cc-211">Once you have both Tags set up, click on **Train** , and the first training iteration will start building.</span></span>

    ![トレーニングイテレーションの有効化](images/AzureLabs-Lab302b-12.png)

10. <span data-ttu-id="498cc-213">ビルドが完了すると、[既定と **予測 URL** の **作成** ] という2つのボタンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-213">Once it's built, you'll be able to see two buttons called **Make default** and **Prediction URL** .</span></span> <span data-ttu-id="498cc-214">[ **既定値** に設定] をクリックし、[ **予測 URL** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-214">Click on **Make default** first, then click on **Prediction URL** .</span></span>

    ![既定の URL と予測 URL を作成する](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > <span data-ttu-id="498cc-216">このから提供されるエンドポイント URL は、既定としてマークされている *イテレーション* のいずれかに設定されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-216">The endpoint URL which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="498cc-217">そのため、後で新しい *イテレーション* を作成して既定として更新する場合は、コードを変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="498cc-217">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

11. <span data-ttu-id="498cc-218">*予測 url* をクリックしたら、 *メモ帳* を開き、 **url** と **予測キー** をコピーして貼り付けます。これにより、後でコード内で必要になったときに取得できるようになります。</span><span class="sxs-lookup"><span data-stu-id="498cc-218">Once you have clicked on *Prediction URL* , open *Notepad* , and copy and paste the **URL** and the **Prediction-Key** , so that you can retrieve it when you need it later in the code.</span></span>

    ![URL と予測キーのコピーと貼り付け](images/AzureLabs-Lab302b-14.png)

12. <span data-ttu-id="498cc-220">画面の右上にある **歯車** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-220">Click on the **Cog** at the top right of the screen.</span></span>

    ![歯車アイコンをクリックして設定を開く](images/AzureLabs-Lab302b-15.png)

13. <span data-ttu-id="498cc-222">**トレーニングキー** をコピーし、 *メモ帳* に貼り付けて、後で使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="498cc-222">Copy the **Training Key** and paste it into a *Notepad* , for later use.</span></span>

    ![トレーニングキーのコピー](images/AzureLabs-Lab302b-16.png)

14. <span data-ttu-id="498cc-224">また、 **プロジェクト Id** もコピーし、 *メモ帳* ファイルに貼り付けて、後で使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="498cc-224">Also copy your **Project Id** , and also paste it into your *Notepad* file, for later use.</span></span>

    ![プロジェクト id のコピー](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="498cc-226">章 3-Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="498cc-226">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="498cc-227">次に示すのは、mixed reality で開発するための一般的な設定です。そのため、他のプロジェクトに適したテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="498cc-227">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="498cc-228">*Unity* を開き、[ **新規** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-228">Open *Unity* and click **New** .</span></span>

    ![新しい Unity プロジェクトを作成する](images/AzureLabs-Lab302b-17.png)

2.  <span data-ttu-id="498cc-230">ここで、Unity プロジェクト名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="498cc-230">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="498cc-231">**AzureCustomVision を挿入します。**</span><span class="sxs-lookup"><span data-stu-id="498cc-231">Insert **AzureCustomVision.**</span></span> <span data-ttu-id="498cc-232">プロジェクトテンプレートが **3d** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="498cc-232">Make sure the project template is set to **3D** .</span></span> <span data-ttu-id="498cc-233">場所を適切な **場所** に設定します (ルートディレクトリの方が適していることに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="498cc-233">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="498cc-234">次に、[ **プロジェクトの作成** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-234">Then, click **Create project** .</span></span>

    ![プロジェクト設定の構成](images/AzureLabs-Lab302b-18.png)

3.  <span data-ttu-id="498cc-236">Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="498cc-236">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio** .</span></span> <span data-ttu-id="498cc-237">[ **Edit*  >  *設定* の編集* ] に移動し、新しいウィンドウで [ **外部ツール** ] に移動します。</span><span class="sxs-lookup"><span data-stu-id="498cc-237">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools** .</span></span> <span data-ttu-id="498cc-238">**外部スクリプトエディター** を **Visual Studio 2017** に変更します。</span><span class="sxs-lookup"><span data-stu-id="498cc-238">Change **External Script Editor** to **Visual Studio 2017** .</span></span> <span data-ttu-id="498cc-239">[ **基本設定** ] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="498cc-239">Close the **Preferences** window.</span></span>

    ![外部ツールの構成](images/AzureLabs-Lab302b-19.png)

4.  <span data-ttu-id="498cc-241">次に、[ **ファイル > ビルド設定** ] に移動し、[ **ユニバーサル Windows プラットフォーム** ] を選択します。次に、[ **プラットフォームの切り替え** ] ボタンをクリックして選択内容を適用します。</span><span class="sxs-lookup"><span data-stu-id="498cc-241">Next, go to **File > Build Settings** and select **Universal Windows Platform** , then click on the **Switch Platform** button to apply your selection.</span></span>

    ![<span data-ttu-id="498cc-242">ビルド設定の構成</span><span class="sxs-lookup"><span data-stu-id="498cc-242">Configure build settings</span></span> ](images/AzureLabs-Lab302b-20.png)

5.  <span data-ttu-id="498cc-243">それでも **ファイル > ビルド設定** を行い、次のことを確認します。</span><span class="sxs-lookup"><span data-stu-id="498cc-243">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="498cc-244">**ターゲットデバイス** が **HoloLens** に設定されています</span><span class="sxs-lookup"><span data-stu-id="498cc-244">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="498cc-245">イマーシブヘッドセットの場合は、 **ターゲットデバイス** を *任意のデバイス* に設定します。</span><span class="sxs-lookup"><span data-stu-id="498cc-245">For the immersive headsets, set **Target Device** to *Any Device* .</span></span>
        
    2.  <span data-ttu-id="498cc-246">**ビルドの種類** が **D3D** に設定されています</span><span class="sxs-lookup"><span data-stu-id="498cc-246">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="498cc-247">**SDK** は最新の **インストール** に設定されています</span><span class="sxs-lookup"><span data-stu-id="498cc-247">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="498cc-248">**Visual Studio のバージョン** が、 **インストールされている最新** バージョンに設定されています</span><span class="sxs-lookup"><span data-stu-id="498cc-248">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="498cc-249">**ビルドと実行** は **ローカルコンピューター** に設定されています</span><span class="sxs-lookup"><span data-stu-id="498cc-249">**Build and Run** is set to **Local Machine**</span></span>
    6.  <span data-ttu-id="498cc-250">シーンを保存し、ビルドに追加します。</span><span class="sxs-lookup"><span data-stu-id="498cc-250">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="498cc-251">これを行うには、[開いている **シーンの追加** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="498cc-251">Do this by selecting **Add Open Scenes** .</span></span> <span data-ttu-id="498cc-252">保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-252">A save window will appear.</span></span>

            ![開いているシーンをビルドリストに追加](images/AzureLabs-Lab302b-21.png)

        2. <span data-ttu-id="498cc-254">この新しいフォルダーを作成し、今後のシーンに加えて、[ **新しいフォルダー** ] ボタンを選択します。新しいフォルダーを作成するには、名前を「 **シーン** 」にします。</span><span class="sxs-lookup"><span data-stu-id="498cc-254">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes** .</span></span>

            ![新しいシーンフォルダーの作成](images/AzureLabs-Lab302b-22.png)

        3. <span data-ttu-id="498cc-256">新しく作成した [ **シーン** ] フォルダーを開き、[ *ファイル名:* テキスト] フィールドに「 **CustomVisionScene** 」と入力し、[ **保存** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-256">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **CustomVisionScene** , then click on **Save** .</span></span>

            ![新しいシーンファイルに名前を指定](images/AzureLabs-Lab302b-23.png)

            > <span data-ttu-id="498cc-258">Unity プロジェクトに関連付けられている必要があるため、Unity のシーンを *Assets* フォルダー内に保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="498cc-258">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="498cc-259">Unity プロジェクトを構成する一般的な方法は、シーンフォルダー (およびその他の同様のフォルダー) を作成することです。</span><span class="sxs-lookup"><span data-stu-id="498cc-259">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>
            
    7.  <span data-ttu-id="498cc-260">それ以外の設定は、[ *ビルド設定* ] の [既定] のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="498cc-260">The remaining settings, in *Build Settings* , should be left as default for now.</span></span>

        ![既定のビルド設定](images/AzureLabs-Lab302b-24.png)

6.  <span data-ttu-id="498cc-262">[ *ビルドの設定* ] ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 *インスペクター* が配置されている領域の関連パネルが開きます。</span><span class="sxs-lookup"><span data-stu-id="498cc-262">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

7. <span data-ttu-id="498cc-263">このパネルでは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="498cc-263">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="498cc-264">[ **その他の設定** ] タブで、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="498cc-264">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="498cc-265">**Scripting Runtime のバージョン** は **実験的 (.Net 4.6 と同等)** である必要があります。これにより、エディターを再起動する必要が生じます。</span><span class="sxs-lookup"><span data-stu-id="498cc-265">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)** , which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="498cc-266">**バックエンド** は **.net** である必要があります</span><span class="sxs-lookup"><span data-stu-id="498cc-266">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="498cc-267">**API 互換性レベル** は **.net 4.6** である必要があります</span><span class="sxs-lookup"><span data-stu-id="498cc-267">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![API compantiblity の設定](images/AzureLabs-Lab302b-25.png)

    2.  <span data-ttu-id="498cc-269">[ **発行の設定** ] タブの [ **機能** ] で、次の項目を確認します。</span><span class="sxs-lookup"><span data-stu-id="498cc-269">Within the **Publishing Settings** tab, under **Capabilities** , check:</span></span>

        1. <span data-ttu-id="498cc-270">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="498cc-270">**InternetClient**</span></span>

        2.  <span data-ttu-id="498cc-271">**Web カメラ**</span><span class="sxs-lookup"><span data-stu-id="498cc-271">**Webcam**</span></span>

        3. <span data-ttu-id="498cc-272">**マイク**</span><span class="sxs-lookup"><span data-stu-id="498cc-272">**Microphone**</span></span>

        ![発行の設定を構成する](images/AzureLabs-Lab302b-26.png)

    3.  <span data-ttu-id="498cc-274">パネルの下にある [ **XR settings** (発行の **設定** ] の下にあります) で、[ **サポートされている仮想現実** ] をティックし、 **Windows Mixed reality SDK** が追加されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="498cc-274">Further down the panel, in **XR Settings** (found below **Publish Settings** ), tick **Virtual Reality Supported** , make sure the **Windows Mixed Reality SDK** is added.</span></span>

    ![XR 設定の構成](images/AzureLabs-Lab302b-27.png)

8.  <span data-ttu-id="498cc-276">*ビルド設定* に戻る *Unity C \# プロジェクト* はグレーで表示されなくなりました。この横にあるチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="498cc-276">Back in *Build Settings* *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="498cc-277">[ビルド設定] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="498cc-277">Close the Build Settings window.</span></span>

10.  <span data-ttu-id="498cc-278">シーンとプロジェクトを保存します ([ **ファイル] > [シーン/ファイルの保存] > [プロジェクトの保存** ])。</span><span class="sxs-lookup"><span data-stu-id="498cc-278">Save your Scene and project ( **FILE > SAVE SCENE / FILE > SAVE PROJECT** ).</span></span>


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a><span data-ttu-id="498cc-279">章 4-Unity での Newtonsoft DLL のインポート</span><span class="sxs-lookup"><span data-stu-id="498cc-279">Chapter 4 - Importing the Newtonsoft DLL in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="498cc-280">このコースの *Unity セットアップ* コンポーネントをスキップし、コードに直接進む場合は、この [Azure-MR-302b](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage)をダウンロードし、 [**カスタムパッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてから、 [第6章](#chapter-6---create-the-customvisionanalyser-class)から続行してください。</span><span class="sxs-lookup"><span data-stu-id="498cc-280">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 6](#chapter-6---create-the-customvisionanalyser-class).</span></span>

<span data-ttu-id="498cc-281">このコースでは、 **Newtonsoft** ライブラリを使用する必要があります。これは、アセットに DLL として追加できます。</span><span class="sxs-lookup"><span data-stu-id="498cc-281">This course requires the use of the **Newtonsoft** library, which you can add as a DLL to your assets.</span></span> <span data-ttu-id="498cc-282">このライブラリを含むパッケージは、 [このリンクからダウンロードでき](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage)ます。</span><span class="sxs-lookup"><span data-stu-id="498cc-282">The package containing [this library can be downloaded from this Link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span></span>
<span data-ttu-id="498cc-283">Newtonsoft ライブラリをプロジェクトにインポートするには、このコースに付属している Unity パッケージを使用します。</span><span class="sxs-lookup"><span data-stu-id="498cc-283">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="498cc-284">[ **アセット*  >  *インポート\*\*パッケージ* の  >  *カスタム\*\*パッケージ** ] メニューオプションを使用して、 *unitypackage* を Unity に追加します。</span><span class="sxs-lookup"><span data-stu-id="498cc-284">Add the *.unitypackage* to Unity by using the **Assets* > *Import* *Package* > *Custom* *Package** menu option.</span></span>

2.  <span data-ttu-id="498cc-285">ポップアップ表示された [ **Unity パッケージのインポート** ] ボックスで、 **プラグイン** (およびそれを含む) のすべてが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="498cc-285">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![すべてのパッケージアイテムをインポートする](images/AzureLabs-Lab302b-28.png)

3.  <span data-ttu-id="498cc-287">[ **インポート** ] ボタンをクリックして、プロジェクトに項目を追加します。</span><span class="sxs-lookup"><span data-stu-id="498cc-287">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="498cc-288">プロジェクトビューの [ **プラグイン** ] の下にある **newtonsoft** フォルダーにアクセスし、プラグインの [ *Newtonsoft.Js* ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="498cc-288">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the *Newtonsoft.Json plugin* .</span></span>

    ![Newtonsoft プラグインを選択します。](images/AzureLabs-Lab302b-29.png)

5.  <span data-ttu-id="498cc-290">[ *Newtonsoft.Jsのプラグイン* ] を選択した状態で、任意の **プラットフォーム** が **オフ** になっていることを確認し、[ **wsaplayer** ] も **オフ** になっていることを確認して、[ **適用** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-290">With the *Newtonsoft.Json plugin* selected, ensure that **Any Platform** is **unchecked** , then ensure that **WSAPlayer** is also **unchecked** , then click **Apply** .</span></span> <span data-ttu-id="498cc-291">これは、ファイルが正しく構成されていることを確認するためのものです。</span><span class="sxs-lookup"><span data-stu-id="498cc-291">This is just to confirm that the files are configured correctly.</span></span>

    ![Newtonsoft プラグインの構成](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > <span data-ttu-id="498cc-293">これらのプラグインをマークすると、Unity エディターでのみ使用するように構成されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-293">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="498cc-294">WSA フォルダーには、Unity からプロジェクトがエクスポートされた後に使用される、異なるセットがあります。</span><span class="sxs-lookup"><span data-stu-id="498cc-294">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="498cc-295">次に、 **Newtonsoft** フォルダー内の **WSA** フォルダーを開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="498cc-295">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="498cc-296">先ほど構成したものと同じファイルのコピーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-296">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="498cc-297">ファイルを選択し、インスペクターで次のことを確認します。</span><span class="sxs-lookup"><span data-stu-id="498cc-297">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="498cc-298">**すべてのプラットフォーム** が **オフ** になっています</span><span class="sxs-lookup"><span data-stu-id="498cc-298">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="498cc-299">**only** **wsaplayer** のみが **チェック** されます</span><span class="sxs-lookup"><span data-stu-id="498cc-299">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="498cc-300">**処理** されないかどうかを **確認** します</span><span class="sxs-lookup"><span data-stu-id="498cc-300">**Dont process** is **checked**</span></span>

    ![Newtonsoft plugin platform の設定を構成する](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a><span data-ttu-id="498cc-302">第5章-カメラの設定</span><span class="sxs-lookup"><span data-stu-id="498cc-302">Chapter 5 - Camera setup</span></span>

1.  <span data-ttu-id="498cc-303">[階層] パネルで、 *メインカメラ* を選択します。</span><span class="sxs-lookup"><span data-stu-id="498cc-303">In the Hierarchy Panel, select the *Main Camera* .</span></span>

2.  <span data-ttu-id="498cc-304">選択すると、 *メインカメラ* のすべてのコンポーネントが [ *インスペクター] パネル* に表示されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-304">Once selected, you will be able to see all the components of the *Main Camera* in the *Inspector Panel* .</span></span>

    1.  <span data-ttu-id="498cc-305">*カメラ* オブジェクトは **メインカメラ** という名前にする必要があります (スペルに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="498cc-305">The *camera* object must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="498cc-306">メインカメラの **タグ** は、 **maincamera** に設定する必要があります (スペルに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="498cc-306">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="498cc-307">**変換位置** が **0、0、0** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="498cc-307">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="498cc-308">**クリアフラグ** を **純色** に設定します (イマーシブヘッドセットの場合は無視します)。</span><span class="sxs-lookup"><span data-stu-id="498cc-308">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>

    5.  <span data-ttu-id="498cc-309">カメラコンポーネントの **背景** 色を **黒、アルファ 0 (16 進コード: #00000000)** に設定します (イマーシブヘッドセットの場合は無視します)。</span><span class="sxs-lookup"><span data-stu-id="498cc-309">Set the **Background** Color of the camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

    ![カメラコンポーネントのプロパティの構成](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a><span data-ttu-id="498cc-311">Chapter 6-CustomVisionAnalyser クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="498cc-311">Chapter 6 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="498cc-312">この時点で、コードを記述する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="498cc-312">At this point you are ready to write some code.</span></span>

<span data-ttu-id="498cc-313">最初に、 *CustomVisionAnalyser* クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="498cc-313">You will begin with the *CustomVisionAnalyser* class.</span></span>

> [!NOTE]
> <span data-ttu-id="498cc-314">次に示すコードで行われた **Custom Vision Service** の呼び出しは、 **Custom Vision REST API** を使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="498cc-314">The calls to the **Custom Vision Service** made in the code shown below are made using the **Custom Vision REST API** .</span></span> <span data-ttu-id="498cc-315">これを使用すると、この API を実装して使用する方法を確認できます (独自のものを実装する方法を理解するために役立ちます)。</span><span class="sxs-lookup"><span data-stu-id="498cc-315">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="498cc-316">Microsoft では、サービスの呼び出しを行うために使用できる **CUSTOM VISION SERVICE SDK** を提供していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="498cc-316">Be aware, that Microsoft offers a **Custom Vision Service SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="498cc-317">詳細については、 [CUSTOM VISION SERVICE SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="498cc-317">For more information visit the [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) article.</span></span>

<span data-ttu-id="498cc-318">このクラスの役割は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="498cc-318">This class is responsible for:</span></span>

-   <span data-ttu-id="498cc-319">バイト配列としてキャプチャされた最新のイメージを読み込んでいます。</span><span class="sxs-lookup"><span data-stu-id="498cc-319">Loading the latest image captured as an array of bytes.</span></span>

-   <span data-ttu-id="498cc-320">分析のために、Azure *Custom Vision Service* インスタンスにバイト配列を送信しています。</span><span class="sxs-lookup"><span data-stu-id="498cc-320">Sending the byte array to your Azure *Custom Vision Service* instance for analysis.</span></span>

-   <span data-ttu-id="498cc-321">JSON 文字列として応答を受信しています。</span><span class="sxs-lookup"><span data-stu-id="498cc-321">Receiving the response as a JSON string.</span></span>

-   <span data-ttu-id="498cc-322">応答を逆シリアル化し、結果の *予測* を *SceneOrganiser* クラスに渡します。これにより、応答の表示方法が決まります。</span><span class="sxs-lookup"><span data-stu-id="498cc-322">Deserializing the response and passing the resulting *Prediction* to the *SceneOrganiser* class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="498cc-323">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="498cc-323">To create this class:</span></span>

1.  <span data-ttu-id="498cc-324">[ *プロジェクト] パネル* にある [ *アセット] フォルダー* を右クリックし、[ **> フォルダーの作成** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-324">Right-click in the *Asset Folder* located in the *Project Panel* , then click **Create > Folder** .</span></span> <span data-ttu-id="498cc-325">フォルダー **スクリプト** を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="498cc-325">Call the folder **Scripts** .</span></span>

    ![スクリプトフォルダーの作成](images/AzureLabs-Lab302b-33.png)

2.  <span data-ttu-id="498cc-327">作成したばかりのフォルダーをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="498cc-327">Double-click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="498cc-328">フォルダー内を右クリックし、[ **Create**  >  **C \# スクリプト** の作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-328">Right-click inside the folder, then click **Create** > **C\# Script** .</span></span> <span data-ttu-id="498cc-329">スクリプトに *CustomVisionAnalyser* という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="498cc-329">Name the script *CustomVisionAnalyser* .</span></span>

4.  <span data-ttu-id="498cc-330">新しい *CustomVisionAnalyser* スクリプトをダブルクリックして、 **Visual Studio** で開きます。</span><span class="sxs-lookup"><span data-stu-id="498cc-330">Double-click on the new *CustomVisionAnalyser* script to open it with **Visual Studio** .</span></span>

5.  <span data-ttu-id="498cc-331">ファイルの先頭にある名前空間を次のように更新します。</span><span class="sxs-lookup"><span data-stu-id="498cc-331">Update the namespaces at the top of your file to match the following:</span></span>

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  <span data-ttu-id="498cc-332">*CustomVisionAnalyser* クラスに、次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="498cc-332">In the *CustomVisionAnalyser* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="498cc-333">**予測キー** を **predictionKey** 変数に挿入し、 **予測エンドポイント** を **predictionEndpoint** 変数に挿入してください。</span><span class="sxs-lookup"><span data-stu-id="498cc-333">Make sure you insert your **Prediction Key** into the **predictionKey** variable and your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="498cc-334">これらは、コースの前の *メモ帳* にコピーしました。</span><span class="sxs-lookup"><span data-stu-id="498cc-334">You copied these to *Notepad* earlier in the course.</span></span>

7.  <span data-ttu-id="498cc-335">インスタンス変数を初期化するには、起動前 **()** のコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="498cc-335">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="498cc-336">**Start ()** および **Update ()** メソッドを削除します。</span><span class="sxs-lookup"><span data-stu-id="498cc-336">Delete the methods **Start()** and **Update()** .</span></span>

9.  <span data-ttu-id="498cc-337">次に、コルーチン (static **GetImageAsByteArray ()** メソッドをその下に追加) を追加します。これにより、 *imagecapture* クラスによってキャプチャされたイメージの分析結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="498cc-337">Next, add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="498cc-338">**分析 Seimagecapture** コルーチンには、まだ作成していない *SceneOrganiser* クラスの呼び出しがあります。</span><span class="sxs-lookup"><span data-stu-id="498cc-338">In the **AnalyseImageCapture** coroutine, there is a call to the *SceneOrganiser* class that you are yet to create.</span></span> <span data-ttu-id="498cc-339">そのため、 **これらの行はコメントの付いたままに** しておきます。</span><span class="sxs-lookup"><span data-stu-id="498cc-339">Therefore, **leave those lines commented for now** .</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
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

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
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

10.  <span data-ttu-id="498cc-340">**Unity** に戻る前に、変更内容を **Visual Studio** に保存してください。</span><span class="sxs-lookup"><span data-stu-id="498cc-340">Be sure to save your changes in **Visual Studio** before returning to **Unity** .</span></span>

## <a name="chapter-7---create-the-customvisionobjects-class"></a><span data-ttu-id="498cc-341">第7章-CustomVisionObjects クラスの作成</span><span class="sxs-lookup"><span data-stu-id="498cc-341">Chapter 7 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="498cc-342">ここで作成するクラスは、 *CustomVisionObjects* クラスです。</span><span class="sxs-lookup"><span data-stu-id="498cc-342">The class you will create now is the *CustomVisionObjects* class.</span></span>

<span data-ttu-id="498cc-343">このスクリプトには、 *Custom Vision Service* に対する呼び出しをシリアル化および逆シリアル化するために、他のクラスによって使用される多数のオブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="498cc-343">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the *Custom Vision Service* .</span></span>

> [!WARNING]
> <span data-ttu-id="498cc-344">次の JSON 構造が [*Custom Vision 予測*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290)v2.0 で動作するように設定されているため、Custom Vision Service によって提供されるエンドポイントをメモしておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="498cc-344">It is important that you take note of the endpoint that the Custom Vision Service provides you, as the below JSON structure has been set up to work with [*Custom Vision Prediction v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span></span> <span data-ttu-id="498cc-345">バージョンが異なる場合は、以下の構造を更新する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="498cc-345">If you have a different version, you may need to update the below structure.</span></span>

<span data-ttu-id="498cc-346">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="498cc-346">To create this class:</span></span>

1.  <span data-ttu-id="498cc-347">**Scripts** フォルダー内を右クリックし、[ **Create**  >  **C \# Script** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-347">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script** .</span></span> <span data-ttu-id="498cc-348">スクリプト *CustomVisionObjects* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="498cc-348">Call the script *CustomVisionObjects* .</span></span>

2.  <span data-ttu-id="498cc-349">新しい **CustomVisionObjects** スクリプトをダブルクリックして、 **Visual Studio** で開きます。</span><span class="sxs-lookup"><span data-stu-id="498cc-349">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio** .</span></span>

3.  <span data-ttu-id="498cc-350">ファイルの先頭に次の名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="498cc-350">Add the following namespaces to the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="498cc-351">*CustomVisionObjects* クラス内の **Start ()** および **Update ()** メソッドを削除します。これで、このクラスは空になります。</span><span class="sxs-lookup"><span data-stu-id="498cc-351">Delete the **Start()** and **Update()** methods inside the *CustomVisionObjects* class; this class should now be empty.</span></span>

5.  <span data-ttu-id="498cc-352">*CustomVisionObjects* クラスの **外** に次のクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="498cc-352">Add the following classes **outside** the *CustomVisionObjects* class.</span></span> <span data-ttu-id="498cc-353">これらのオブジェクトは、応答データをシリアル化および逆シリアル化するために *Newtonsoft* ライブラリによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-353">These objects are used by the *Newtonsoft* library to serialize and deserialize the response data:</span></span>

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
    /// JSON of Images submitted
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
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a><span data-ttu-id="498cc-354">章 8-VoiceRecognizer クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="498cc-354">Chapter 8 - Create the VoiceRecognizer class</span></span>

<span data-ttu-id="498cc-355">このクラスは、ユーザーからの音声入力を認識します。</span><span class="sxs-lookup"><span data-stu-id="498cc-355">This class will recognize the voice input from the user.</span></span>

<span data-ttu-id="498cc-356">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="498cc-356">To create this class:</span></span>

1.  <span data-ttu-id="498cc-357">**Scripts** フォルダー内を右クリックし、[ **Create**  >  **C \# Script** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-357">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script** .</span></span> <span data-ttu-id="498cc-358">スクリプト *VoiceRecognizer* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="498cc-358">Call the script *VoiceRecognizer* .</span></span>

2.  <span data-ttu-id="498cc-359">新しい **VoiceRecognizer** スクリプトをダブルクリックして、 **Visual Studio** で開きます。</span><span class="sxs-lookup"><span data-stu-id="498cc-359">Double-click on the new **VoiceRecognizer** script to open it with **Visual Studio** .</span></span>

3.  <span data-ttu-id="498cc-360">*VoiceRecognizer* クラスの上に次の名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="498cc-360">Add the following namespaces above the *VoiceRecognizer* class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  <span data-ttu-id="498cc-361">次に、 *Start ()* メソッドの上に、 *VoiceRecognizer* クラス内に次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="498cc-361">Then add the following variables inside the *VoiceRecognizer* class, above the *Start()* method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  <span data-ttu-id="498cc-362">起動前 **()** および **開始 ()** メソッドを追加します。後者の場合、タグをイメージに関連付けるときに認識されるユーザー *キーワード* が設定されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-362">Add the **Awake()** and **Start()** methods, the latter of which will set up the user *keywords* to be recognized when associating a tag to an image:</span></span>

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
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  <span data-ttu-id="498cc-363">**Update ()** メソッドを削除します。</span><span class="sxs-lookup"><span data-stu-id="498cc-363">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="498cc-364">次のハンドラーを追加します。これは、音声入力が認識されるたびに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-364">Add the following handler, which is called whenever voice input is recognized:</span></span>

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  <span data-ttu-id="498cc-365">**Unity** に戻る前に、変更内容を **Visual Studio** に保存してください。</span><span class="sxs-lookup"><span data-stu-id="498cc-365">Be sure to save your changes in **Visual Studio** before returning to **Unity** .</span></span>

> [!NOTE]
> <span data-ttu-id="498cc-366">エラーが発生する可能性のあるコードについては気にしないでください。これにより、後でクラスを修正することになります。</span><span class="sxs-lookup"><span data-stu-id="498cc-366">Do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-9---create-the-customvisiontrainer-class"></a><span data-ttu-id="498cc-367">第9章-CustomVisionTrainer クラスの作成</span><span class="sxs-lookup"><span data-stu-id="498cc-367">Chapter 9 - Create the CustomVisionTrainer class</span></span>

<span data-ttu-id="498cc-368">このクラスは、一連の web 呼び出しをチェーンして、 *Custom Vision Service* をトレーニングします。</span><span class="sxs-lookup"><span data-stu-id="498cc-368">This class will chain a series of web calls to train the *Custom Vision Service* .</span></span> <span data-ttu-id="498cc-369">各呼び出しの詳細については、コードの上に説明します。</span><span class="sxs-lookup"><span data-stu-id="498cc-369">Each call will be explained in detail right above the code.</span></span>

<span data-ttu-id="498cc-370">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="498cc-370">To create this class:</span></span>

1.  <span data-ttu-id="498cc-371">**Scripts** フォルダー内を右クリックし、[ **Create**  >  **C \# Script** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-371">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script** .</span></span> <span data-ttu-id="498cc-372">スクリプト *CustomVisionTrainer* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="498cc-372">Call the script *CustomVisionTrainer* .</span></span>

2.  <span data-ttu-id="498cc-373">新しい *CustomVisionTrainer* スクリプトをダブルクリックして、 **Visual Studio** で開きます。</span><span class="sxs-lookup"><span data-stu-id="498cc-373">Double-click on the new *CustomVisionTrainer* script to open it with **Visual Studio** .</span></span>

3.  <span data-ttu-id="498cc-374">*CustomVisionTrainer* クラスの上に次の名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="498cc-374">Add the following namespaces above the *CustomVisionTrainer* class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="498cc-375">次に、 **Start ()** メソッドの上に、 *CustomVisionTrainer* クラス内に次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="498cc-375">Then add the following variables inside the *CustomVisionTrainer* class, above the **Start()** method.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="498cc-376">ここで使用されているトレーニング URL は *Custom Vision トレーニング 1.2* のドキュメントに記載されており、の構造は次のとおりです。 https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span><span class="sxs-lookup"><span data-stu-id="498cc-376">The training URL used here is provided within the *Custom Vision Training 1.2* documentation, and has a structure of: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span></span>  
    > <span data-ttu-id="498cc-377">詳細については、 [*Custom Vision トレーニング v2.0 リファレンス API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="498cc-377">For more information, visit the [*Custom Vision Training v1.2 reference API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span>

    > [!WARNING]
    > <span data-ttu-id="498cc-378">Custom Vision Service がトレーニングモード用に提供するエンドポイントをメモしておくことが重要です。これは、( **CustomVisionObjects** クラス内で使用される) JSON 構造が [*Custom Vision トレーニング*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)v1.0 で動作するように設定されているためです。</span><span class="sxs-lookup"><span data-stu-id="498cc-378">It is important that you take note of the endpoint that the Custom Vision Service provides you for the training mode, as the JSON structure used (within the **CustomVisionObjects** class) has been set up to work with [*Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span> <span data-ttu-id="498cc-379">バージョンが異なる場合は、 *オブジェクト* の構造を更新することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="498cc-379">If you have a different version, you may need to update the *Objects* structure.</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="498cc-380">前にメモしておいた、 **サービスキー** (トレーニングキー) 値と **プロジェクト Id** 値を必ず追加してください。これらは、コースの [前の段階でポータルから収集した値です (第2章、手順10以降)](#chapter-2---training-your-custom-vision-project)。</span><span class="sxs-lookup"><span data-stu-id="498cc-380">Ensure that you add your **Service Key** (Training Key) value and **Project Id** value, which you noted down previous; these are the values you [collected from the portal earlier in the course (Chapter 2, step 10 onwards)](#chapter-2---training-your-custom-vision-project).</span></span>

5.  <span data-ttu-id="498cc-381">次の **Start ()** および「起動前 **()** 」の各メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="498cc-381">Add the following **Start()** and **Awake()** methods.</span></span> <span data-ttu-id="498cc-382">これらのメソッドは初期化時に呼び出され、UI を設定するための呼び出しを含みます。</span><span class="sxs-lookup"><span data-stu-id="498cc-382">Those methods are called on initialization and contain the call to set up the UI:</span></span>

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
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  <span data-ttu-id="498cc-383">**Update ()** メソッドを削除します。</span><span class="sxs-lookup"><span data-stu-id="498cc-383">Delete the **Update()** method.</span></span> <span data-ttu-id="498cc-384">このクラスは、このクラスを必要としません。</span><span class="sxs-lookup"><span data-stu-id="498cc-384">This class will not need it.</span></span>

7.  <span data-ttu-id="498cc-385">**Requesttagselection ()** メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="498cc-385">Add the **RequestTagSelection()** method.</span></span> <span data-ttu-id="498cc-386">このメソッドは、イメージをキャプチャしてデバイスに格納し、 *Custom Vision Service* に送信してトレーニングする準備ができたときに最初に呼び出されるメソッドです。</span><span class="sxs-lookup"><span data-stu-id="498cc-386">This method is the first to be called when an image has been captured and stored in the device and is now ready to be submitted to the *Custom Vision Service* , to train it.</span></span> <span data-ttu-id="498cc-387">このメソッドは、トレーニング UI に、キャプチャされたイメージをタグ付けするためにユーザーが使用できる一連のキーワードを表示します。</span><span class="sxs-lookup"><span data-stu-id="498cc-387">This method displays, in the training UI, a set of keywords the user can use to tag the image that has been captured.</span></span> <span data-ttu-id="498cc-388">また、 *VoiceRecognizer* クラスに対して、ユーザーの音声入力のリッスンを開始するように通知します。</span><span class="sxs-lookup"><span data-stu-id="498cc-388">It also alerts the *VoiceRecognizer* class to begin listening to the user for voice input.</span></span>

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  <span data-ttu-id="498cc-389">**Verifytag ()** メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="498cc-389">Add the **VerifyTag()** method.</span></span> <span data-ttu-id="498cc-390">このメソッドは、 **VoiceRecognizer** クラスによって認識される音声入力を受け取り、その有効性を確認してから、トレーニングプロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="498cc-390">This method will receive the voice input recognized by the **VoiceRecognizer** class and verify its validity, and then begin the training process.</span></span>

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  <span data-ttu-id="498cc-391">**SubmitImageForTraining ()** メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="498cc-391">Add the **SubmitImageForTraining()** method.</span></span> <span data-ttu-id="498cc-392">このメソッドは Custom Vision Service トレーニングプロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="498cc-392">This method will begin the Custom Vision Service training process.</span></span> <span data-ttu-id="498cc-393">最初の手順では、ユーザーからの検証済み音声入力に関連付けられているサービスから **タグ Id** を取得します。</span><span class="sxs-lookup"><span data-stu-id="498cc-393">The first step is to retrieve the **Tag Id** from the Service which is associated with the validated speech input from the user.</span></span> <span data-ttu-id="498cc-394">**タグ Id** がイメージと共にアップロードされます。</span><span class="sxs-lookup"><span data-stu-id="498cc-394">The **Tag Id** will then be uploaded along with the image.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. <span data-ttu-id="498cc-395">**TrainCustomVisionProject ()** メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="498cc-395">Add the **TrainCustomVisionProject()** method.</span></span> <span data-ttu-id="498cc-396">イメージが送信され、タグが付けられると、このメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-396">Once the image has been submitted and tagged, this method will be called.</span></span> <span data-ttu-id="498cc-397">これにより、サービスに送信された以前のすべてのイメージに加え、アップロードしたイメージを使用してトレーニングされる新しいイテレーションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-397">It will create a new Iteration that will be trained with all the previous images submitted to the Service plus the image just uploaded.</span></span> <span data-ttu-id="498cc-398">トレーニングが完了すると、このメソッドはメソッドを呼び出して、新しく作成された **イテレーション** を **既定** として設定します。これにより、分析に使用するエンドポイントがトレーニング済みの最新のイテレーションになります。</span><span class="sxs-lookup"><span data-stu-id="498cc-398">Once the training has been completed, this method will call a method to set the newly created **Iteration** as **Default** , so that the endpoint you are using for analysis is the latest trained iteration.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. <span data-ttu-id="498cc-399">**Setdefaultiterfrom()** メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="498cc-399">Add the **SetDefaultIteration()** method.</span></span> <span data-ttu-id="498cc-400">このメソッドは、以前に作成され、トレーニングされたイテレーションを *既定* として設定します。</span><span class="sxs-lookup"><span data-stu-id="498cc-400">This method will set the previously created and trained iteration as *Default* .</span></span> <span data-ttu-id="498cc-401">完了すると、このメソッドは、サービス内の既存のイテレーションを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="498cc-401">Once completed, this method will have to delete the previous iteration existing in the Service.</span></span> <span data-ttu-id="498cc-402">このコースの執筆時点では、サービスに同時に存在できるイテレーションは最大で10個までに制限されています。</span><span class="sxs-lookup"><span data-stu-id="498cc-402">At the time of writing this course, there is a limit of a maximum ten (10) iterations allowed to exist at the same time in the Service.</span></span>

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. <span data-ttu-id="498cc-403">**DeletePreviousIteration ()** メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="498cc-403">Add the **DeletePreviousIteration()** method.</span></span> <span data-ttu-id="498cc-404">このメソッドは、以前の既定以外のイテレーションを見つけて削除します。</span><span class="sxs-lookup"><span data-stu-id="498cc-404">This method will find and delete the previous non-default iteration:</span></span>

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. <span data-ttu-id="498cc-405">このクラスに最後に追加するメソッドは、 **GetImageAsByteArray ()** メソッドです。このメソッドは、キャプチャしたイメージをバイト配列に変換するために、web 呼び出しで使用されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-405">The last method to add in this class is the **GetImageAsByteArray()** method, used on the web calls to convert the image captured into a byte array.</span></span>

    ```csharp
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

14. <span data-ttu-id="498cc-406">**Unity** に戻る前に、変更内容を **Visual Studio** に保存してください。</span><span class="sxs-lookup"><span data-stu-id="498cc-406">Be sure to save your changes in **Visual Studio** before returning to **Unity** .</span></span>

## <a name="chapter-10---create-the-sceneorganiser-class"></a><span data-ttu-id="498cc-407">Chapter 10-SceneOrganiser クラスの作成</span><span class="sxs-lookup"><span data-stu-id="498cc-407">Chapter 10 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="498cc-408">このクラスは次のことを行います。</span><span class="sxs-lookup"><span data-stu-id="498cc-408">This class will:</span></span>

-   <span data-ttu-id="498cc-409">メインカメラに接続するための **Cursor** オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="498cc-409">Create a **Cursor** object to attach to the Main Camera.</span></span>

-   <span data-ttu-id="498cc-410">サービスが実際のオブジェクトを認識したときに表示される **ラベル** オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="498cc-410">Create a **Label** object that will appear when the Service recognizes the real-world objects.</span></span>

-   <span data-ttu-id="498cc-411">適切なコンポーネントをアタッチして、メインカメラを設定します。</span><span class="sxs-lookup"><span data-stu-id="498cc-411">Set up the Main Camera by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="498cc-412">**分析モード** では、実行時に、メインカメラの位置を基準とした適切なワールド空間でラベルが生成され、Custom Vision Service から受信したデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-412">When in **Analysis Mode** , spawn the Labels at runtime, in the appropriate world space relative to the position of the Main Camera, and display the data received from the Custom Vision Service.</span></span>

-   <span data-ttu-id="498cc-413">**トレーニングモード** では、トレーニングプロセスのさまざまな段階を表示する UI を生成します。</span><span class="sxs-lookup"><span data-stu-id="498cc-413">When in **Training Mode** , spawn the UI that will display the different stages of the training process.</span></span>

<span data-ttu-id="498cc-414">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="498cc-414">To create this class:</span></span>

1.  <span data-ttu-id="498cc-415">**Scripts** フォルダー内を右クリックし、[ **Create**  >  **C \# Script** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-415">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script** .</span></span> <span data-ttu-id="498cc-416">スクリプトに *SceneOrganiser* という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="498cc-416">Name the script *SceneOrganiser* .</span></span>

2.  <span data-ttu-id="498cc-417">新しい *SceneOrganiser* スクリプトをダブルクリックして、 **Visual Studio** で開きます。</span><span class="sxs-lookup"><span data-stu-id="498cc-417">Double-click on the new *SceneOrganiser* script to open it with **Visual Studio** .</span></span>

3.  <span data-ttu-id="498cc-418">必要な名前空間は1つだけです。 *SceneOrganiser* クラスの上から他の名前空間を削除します。</span><span class="sxs-lookup"><span data-stu-id="498cc-418">You will only need one namespace, remove the others from above the *SceneOrganiser* class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="498cc-419">次に、 **Start ()** メソッドの上に、 *SceneOrganiser* クラス内に次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="498cc-419">Then add the following variables inside the *SceneOrganiser* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  <span data-ttu-id="498cc-420">**Start ()** および **Update ()** メソッドを削除します。</span><span class="sxs-lookup"><span data-stu-id="498cc-420">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="498cc-421">変数のすぐ下に、起動前 **()** メソッドを追加します。このメソッドは、クラスを初期化し、シーンを設定します。</span><span class="sxs-lookup"><span data-stu-id="498cc-421">Right underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  <span data-ttu-id="498cc-422">次に、メインカメラカーソルを作成して配置する **CreateCameraCursor ()** メソッドを追加し、 **CreateLabel ()** メソッドを追加して、 **分析ラベル** オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="498cc-422">Now add the **CreateCameraCursor()** method that creates and positions the Main Camera cursor, and the **CreateLabel()** method, which creates the **Analysis Label** object.</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. <span data-ttu-id="498cc-423">**SetCameraStatus ()** メソッドを追加します。このメソッドは、カメラの状態を提供するテキストメッシュを目的としたメッセージを処理します。</span><span class="sxs-lookup"><span data-stu-id="498cc-423">Add the **SetCameraStatus()** method, which will handle messages intended for the text mesh providing the status of the camera.</span></span>

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. <span data-ttu-id="498cc-424">**PlaceAnalysisLabel ()** メソッドと **SetTagsToLastLabel ()** メソッドを追加します。これにより、Custom Vision Service のデータが生成され、シーンに表示されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-424">Add the **PlaceAnalysisLabel()** and **SetTagsToLastLabel()** methods, which will spawn and display the data from the Custom Vision Service into the scene.</span></span>

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. <span data-ttu-id="498cc-425">最後に、 **CreateTrainingUI ()** メソッドを追加します。これにより、アプリケーションがトレーニングモードのときにトレーニングプロセスの複数のステージを表示する UI が生成されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-425">Lastly, add the **CreateTrainingUI()** method, which will spawn the UI displaying the multiple stages of the training process when the application is in Training Mode.</span></span> <span data-ttu-id="498cc-426">このメソッドは、カメラの状態オブジェクトを作成するためにも開花されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-426">This method will also be harnessed to create the camera status object.</span></span>

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. <span data-ttu-id="498cc-427">**Unity** に戻る前に、変更内容を **Visual Studio** に保存してください。</span><span class="sxs-lookup"><span data-stu-id="498cc-427">Be sure to save your changes in **Visual Studio** before returning to **Unity** .</span></span>

> [!IMPORTANT]
> <span data-ttu-id="498cc-428">続行する前に、 **CustomVisionAnalyser** クラスを開き、 **AnalyseLastImageCaptured ()** メソッド内で次の行を *コメント* 解除します。</span><span class="sxs-lookup"><span data-stu-id="498cc-428">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a><span data-ttu-id="498cc-429">第11章-ImageCapture クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="498cc-429">Chapter 11 - Create the ImageCapture class</span></span>

<span data-ttu-id="498cc-430">次に作成するクラスは、 *Imagecapture* クラスです。</span><span class="sxs-lookup"><span data-stu-id="498cc-430">The next class you are going to create is the *ImageCapture* class.</span></span>

<span data-ttu-id="498cc-431">このクラスの役割は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="498cc-431">This class is responsible for:</span></span>

-   <span data-ttu-id="498cc-432">HoloLens カメラを使用してイメージをキャプチャし、 *アプリ* フォルダーに格納します。</span><span class="sxs-lookup"><span data-stu-id="498cc-432">Capturing an image using the HoloLens camera and storing it in the *App* Folder.</span></span>

-   <span data-ttu-id="498cc-433">ユーザーからの Tap ジェスチャを処理します。</span><span class="sxs-lookup"><span data-stu-id="498cc-433">Handling Tap gestures from the user.</span></span>

-   <span data-ttu-id="498cc-434">アプリケーションを *分析* モードと *トレーニング* モードのどちらで実行するかを決定する *列挙* 値を保持する。</span><span class="sxs-lookup"><span data-stu-id="498cc-434">Maintaining the *Enum* value that determines if the application will run in *Analysis* mode or *Training* Mode.</span></span>

<span data-ttu-id="498cc-435">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="498cc-435">To create this class:</span></span>

1.  <span data-ttu-id="498cc-436">前に作成した **Scripts** フォルダーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="498cc-436">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="498cc-437">フォルダー内を右クリックし、[ **Create > C \# Script** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-437">Right-click inside the folder, then click **Create > C\# Script** .</span></span> <span data-ttu-id="498cc-438">スクリプトに「 *Imagecapture* 」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="498cc-438">Name the script *ImageCapture* .</span></span>

3.  <span data-ttu-id="498cc-439">新しい **Imagecapture** スクリプトをダブルクリックして、 **Visual Studio** で開きます。</span><span class="sxs-lookup"><span data-stu-id="498cc-439">Double-click on the new **ImageCapture** script to open it with **Visual Studio** .</span></span>

4.  <span data-ttu-id="498cc-440">ファイルの先頭にある名前空間を次のように置き換えます。</span><span class="sxs-lookup"><span data-stu-id="498cc-440">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="498cc-441">次に、 **Start ()** メソッドの上に、 *imagecapture* クラス内に次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="498cc-441">Then add the following variables inside the *ImageCapture* class, above the **Start()** method:</span></span>

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
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="498cc-442">起動可能な **()** メソッドと **Start ()** メソッドのコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="498cc-442">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
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

            // Subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  <span data-ttu-id="498cc-443">Tap ジェスチャが発生したときに呼び出されるハンドラーを実装します。</span><span class="sxs-lookup"><span data-stu-id="498cc-443">Implement a handler that will be called when a Tap gesture occurs.</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="498cc-444">*分析* モードでは、 **TapHandler** メソッドはフォトキャプチャループを開始または停止するためのスイッチとして機能します。</span><span class="sxs-lookup"><span data-stu-id="498cc-444">In *Analysis* mode, the **TapHandler** method acts as a switch to start or stop the photo capture loop.</span></span>
    >
    > <span data-ttu-id="498cc-445">*トレーニング* モードでは、カメラからイメージをキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="498cc-445">In *Training* mode, it will capture an image from the camera.</span></span>
    >
    > <span data-ttu-id="498cc-446">カーソルが緑色の場合は、カメラを使用してイメージを撮影できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="498cc-446">When the cursor is green, it means the camera is available to take the image.</span></span>
    >
    > <span data-ttu-id="498cc-447">カーソルが赤の場合、カメラがビジー状態であることを示します。</span><span class="sxs-lookup"><span data-stu-id="498cc-447">When the cursor is red, it means the camera is busy.</span></span>

8.  <span data-ttu-id="498cc-448">アプリケーションがイメージキャプチャプロセスを開始してイメージを格納するために使用するメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="498cc-448">Add the method that the application uses to start the image capture process and store the image.</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
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

9.  <span data-ttu-id="498cc-449">写真がキャプチャされ、分析の準備ができたときに呼び出されるハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="498cc-449">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="498cc-450">次に、コードが設定されているモードに応じて、結果が *CustomVisionAnalyser* または *CustomVisionTrainer* に渡されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-450">The result is then passed to the *CustomVisionAnalyser* or the *CustomVisionTrainer* depending on which mode the code is set on.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="498cc-451">**Unity** に戻る前に、変更内容を **Visual Studio** に保存してください。</span><span class="sxs-lookup"><span data-stu-id="498cc-451">Be sure to save your changes in **Visual Studio** before returning to **Unity** .</span></span>

11. <span data-ttu-id="498cc-452">すべてのスクリプトが完了したので、Unity エディターに戻り、[ **スクリプト** ] フォルダーの **SceneOrganiser** クラスをクリックして、 *階層パネル* の **メインカメラ** オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="498cc-452">Now that all the scripts have been completed, go back in the Unity Editor, then click and drag the **SceneOrganiser** class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel* .</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="498cc-453">第12章-ビルド前</span><span class="sxs-lookup"><span data-stu-id="498cc-453">Chapter 12 - Before building</span></span>

<span data-ttu-id="498cc-454">アプリケーションの徹底的なテストを実行するには、アプリケーションを HoloLens にサイドロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="498cc-454">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="498cc-455">これを行う前に、次のことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="498cc-455">Before you do, ensure that:</span></span>

- <span data-ttu-id="498cc-456">[章 2](#chapter-2---training-your-custom-vision-project)で説明したすべての設定が正しく設定されています。</span><span class="sxs-lookup"><span data-stu-id="498cc-456">All the settings mentioned in the [Chapter 2](#chapter-2---training-your-custom-vision-project) are set correctly.</span></span>

- <span data-ttu-id="498cc-457">**メインカメラ** の [インスペクター] パネルのすべてのフィールドが適切に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="498cc-457">All the fields in the **Main Camera** , Inspector Panel, are assigned properly.</span></span>

- <span data-ttu-id="498cc-458">スクリプト **SceneOrganiser** は、 **メインカメラ** オブジェクトにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="498cc-458">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>

- <span data-ttu-id="498cc-459">必ず、 **予測キー** を **predictionKey** 変数に挿入してください。</span><span class="sxs-lookup"><span data-stu-id="498cc-459">Make sure you insert your **Prediction Key** into the **predictionKey** variable.</span></span>

- <span data-ttu-id="498cc-460">**予測エンドポイント** を **predictionEndpoint** 変数に挿入しました。</span><span class="sxs-lookup"><span data-stu-id="498cc-460">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span>

- <span data-ttu-id="498cc-461">**トレーニングキー** を *CustomVisionTrainer* クラスの **trainingKey** 変数に挿入しました。</span><span class="sxs-lookup"><span data-stu-id="498cc-461">You have inserted your **Training Key** into the **trainingKey** variable, of the *CustomVisionTrainer* class.</span></span>

- <span data-ttu-id="498cc-462">**プロジェクト ID** が *CustomVisionTrainer* クラスの **projectId** 変数に挿入されました。</span><span class="sxs-lookup"><span data-stu-id="498cc-462">You have inserted your **Project ID** into the **projectId** variable, of the *CustomVisionTrainer* class.</span></span>

## <a name="chapter-13---build-and-sideload-your-application"></a><span data-ttu-id="498cc-463">第13章-アプリケーションのビルドとサイドロード</span><span class="sxs-lookup"><span data-stu-id="498cc-463">Chapter 13 - Build and sideload your application</span></span>

<span data-ttu-id="498cc-464">*ビルド* プロセスを開始するには:</span><span class="sxs-lookup"><span data-stu-id="498cc-464">To begin the *Build* process:</span></span>

1.  <span data-ttu-id="498cc-465">**ファイル > ビルド設定** にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="498cc-465">Go to **File > Build Settings** .</span></span>

2.  <span data-ttu-id="498cc-466">**Unity C \# プロジェクト** をティックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-466">Tick **Unity C\# Projects** .</span></span>

3.  <span data-ttu-id="498cc-467">[ **ビルド** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-467">Click **Build** .</span></span> <span data-ttu-id="498cc-468">Unity は **エクスプローラー** ウィンドウを起動します。このウィンドウでは、アプリを作成するフォルダーを作成して選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="498cc-468">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="498cc-469">ここでそのフォルダーを作成し、「 **App** 」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="498cc-469">Create that folder now, and name it **App** .</span></span> <span data-ttu-id="498cc-470">次に、 **アプリ** フォルダーを選択し、[ **フォルダーの選択** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-470">Then with the **App** folder selected, click on **Select Folder** .</span></span>

4.  <span data-ttu-id="498cc-471">Unity は、 **アプリ** フォルダーへのプロジェクトのビルドを開始します。</span><span class="sxs-lookup"><span data-stu-id="498cc-471">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="498cc-472">Unity のビルドが完了すると (時間がかかる場合があります)、ビルドの場所で **ファイルエクスプローラー** ウィンドウを開きます (ウィンドウの上に常に表示されるとは限りませんが、新しいウィンドウが追加されたことが通知されます)。</span><span class="sxs-lookup"><span data-stu-id="498cc-472">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

<span data-ttu-id="498cc-473">HoloLens に展開するには:</span><span class="sxs-lookup"><span data-stu-id="498cc-473">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="498cc-474">Hololens が **開発者モード** になっていることを確認するには、HOLOLENS の IP アドレス (リモートデプロイ用) が必要です。</span><span class="sxs-lookup"><span data-stu-id="498cc-474">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode** .</span></span> <span data-ttu-id="498cc-475">これを行うには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="498cc-475">To do this:</span></span>

    1.  <span data-ttu-id="498cc-476">HoloLens を装着した後、 **設定** を開きます。</span><span class="sxs-lookup"><span data-stu-id="498cc-476">Whilst wearing your HoloLens, open the **Settings** .</span></span>

    2.  <span data-ttu-id="498cc-477">[ **ネットワーク & インターネット**  >  **wi-fi**  >  **詳細オプション]** にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="498cc-477">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="498cc-478">**IPv4** アドレスをメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="498cc-478">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="498cc-479">次に、[ **設定** ] に戻り、 **Update & Security**  >  **開発者の** & セキュリティを更新します。</span><span class="sxs-lookup"><span data-stu-id="498cc-479">Next, navigate back to **Settings** , and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="498cc-480">**開発者モードをに** 設定します。</span><span class="sxs-lookup"><span data-stu-id="498cc-480">Set **Developer Mode On** .</span></span>

2.  <span data-ttu-id="498cc-481">新しい Unity ビルド ( **アプリ** フォルダー) に移動し、 **Visual Studio** でソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="498cc-481">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio** .</span></span>

3.  <span data-ttu-id="498cc-482">*ソリューション構成* で、[ **デバッグ** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="498cc-482">In the *Solution Configuration* select **Debug** .</span></span>

4.  <span data-ttu-id="498cc-483">*ソリューションプラットフォーム* で、[ **X86、リモートコンピューター** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="498cc-483">In the *Solution Platform* , select **x86, Remote Machine** .</span></span> <span data-ttu-id="498cc-484">リモートデバイスの **IP アドレス** (この場合は、ここでメモした HoloLens) を挿入するように求められます。</span><span class="sxs-lookup"><span data-stu-id="498cc-484">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![IP アドレスの設定](images/AzureLabs-Lab302b-34.png)

5. <span data-ttu-id="498cc-486">[ **ビルド** ] メニューの [ **ソリューションの配置** ] をクリックして、アプリケーションを HoloLens にサイドロードします。</span><span class="sxs-lookup"><span data-stu-id="498cc-486">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6. <span data-ttu-id="498cc-487">アプリが HoloLens にインストールされているアプリの一覧に表示され、起動できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="498cc-487">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="498cc-488">イマーシブヘッドセットにデプロイするには **、ソリューションプラットフォーム** を *ローカルコンピューター* に設定し、 **プラットフォーム** として *x86* を使用して、 **構成** を [ *デバッグ* ] に設定します。</span><span class="sxs-lookup"><span data-stu-id="498cc-488">To deploy to immersive headset, set the **Solution Platform** to *Local Machine* , and set the **Configuration** to *Debug* , with *x86* as the **Platform** .</span></span> <span data-ttu-id="498cc-489">次に、[ **ビルド** ] メニュー項目を使用して [ *ソリューションの配置* ] を選択し、ローカルコンピューターに配置します。</span><span class="sxs-lookup"><span data-stu-id="498cc-489">Then deploy to the local machine, using the **Build** menu item, selecting *Deploy Solution* .</span></span> 

## <a name="to-use-the-application"></a><span data-ttu-id="498cc-490">アプリケーションを使用するには:</span><span class="sxs-lookup"><span data-stu-id="498cc-490">To use the application:</span></span>

<span data-ttu-id="498cc-491">*トレーニング* モードと *予測* モードの間でアプリの機能を切り替えるには、 *imagecapture* クラス内にある、起動前の **()** メソッドにある **appmode** 変数を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="498cc-491">To switch the app functionality between *Training* mode and *Prediction* mode you need to update the **AppMode** variable, located in the **Awake()** method located within the *ImageCapture* class.</span></span>

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
<span data-ttu-id="498cc-492">または</span><span class="sxs-lookup"><span data-stu-id="498cc-492">or</span></span>
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

<span data-ttu-id="498cc-493">*トレーニング* モードの場合:</span><span class="sxs-lookup"><span data-stu-id="498cc-493">In *Training* mode:</span></span>

- <span data-ttu-id="498cc-494">**マウス** または **キーボード** を見て、 **Tap ジェスチャ** を使用します。</span><span class="sxs-lookup"><span data-stu-id="498cc-494">Look at **Mouse** or **Keyboard** and use the **Tap gesture** .</span></span>

- <span data-ttu-id="498cc-495">次に、タグの入力を求めるテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-495">Next, text will appear asking you to provide a tag.</span></span>

- <span data-ttu-id="498cc-496">**マウス** または **キーボード** のいずれかを言います。</span><span class="sxs-lookup"><span data-stu-id="498cc-496">Say either **Mouse** or **Keyboard** .</span></span>


<span data-ttu-id="498cc-497">*予測* モードの場合:</span><span class="sxs-lookup"><span data-stu-id="498cc-497">In *Prediction* mode:</span></span>

- <span data-ttu-id="498cc-498">オブジェクトを確認し、 **Tap ジェスチャ** を使用します。</span><span class="sxs-lookup"><span data-stu-id="498cc-498">Look at an object and use the **Tap gesture** .</span></span>

- <span data-ttu-id="498cc-499">オブジェクトが検出され、確率が最も高い (これは正規化されている) ことを示すテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-499">Text will appear providing the object detected, with the highest probability (this is normalized).</span></span>

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a><span data-ttu-id="498cc-500">第14章-Custom Vision モデルの評価と改善</span><span class="sxs-lookup"><span data-stu-id="498cc-500">Chapter 14 - Evaluate and improve your Custom Vision model</span></span>

<span data-ttu-id="498cc-501">サービスの精度を高めるには、予測に使用するモデルのトレーニングを続行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="498cc-501">To make your Service more accurate, you will need to continue to train the model used for prediction.</span></span> <span data-ttu-id="498cc-502">これは、 *トレーニング* と *予測* の両方のモードで新しいアプリケーションを使用することによって実現されます。後者の場合はポータルにアクセスする必要があります。これについては、この章で説明します。</span><span class="sxs-lookup"><span data-stu-id="498cc-502">This is accomplished through using your new application, with both the *training* and *prediction* modes, with the latter requiring you to visit the portal, which is what is covered in this Chapter.</span></span> <span data-ttu-id="498cc-503">モデルを継続的に改善するために、ポータルに何度も再訪問できるように準備してください。</span><span class="sxs-lookup"><span data-stu-id="498cc-503">Be prepared to revisit your portal many times, to continually improve your model.</span></span>

1. <span data-ttu-id="498cc-504">Azure Custom Vision ポータルにもう一度移動します。プロジェクトが表示されたら、[ *予測* ] タブ (ページの上部中央) を選択します。</span><span class="sxs-lookup"><span data-stu-id="498cc-504">Head to your Azure Custom Vision Portal again, and once you are in your project, select the *Predictions* tab (from the top center of the page):</span></span>

    ![[予測] タブの選択](images/AzureLabs-Lab302b-35.png)

2. <span data-ttu-id="498cc-506">アプリケーションの実行中にサービスに送信されたすべてのイメージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-506">You will see all the images which were sent to your Service whilst your application was running.</span></span> <span data-ttu-id="498cc-507">画像にマウスポインターを合わせると、その画像に対して行われた予測が表示されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-507">If you hover over the images, they will provide you with the predictions that were made for that image:</span></span>

    ![予測イメージの一覧](images/AzureLabs-Lab302b-36.png)

3. <span data-ttu-id="498cc-509">イメージの1つを選択して開きます。</span><span class="sxs-lookup"><span data-stu-id="498cc-509">Select one of your images to open it.</span></span> <span data-ttu-id="498cc-510">開いた後、そのイメージの予測が右側に表示されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-510">Once open, you will see the predictions made for that image to the right.</span></span> <span data-ttu-id="498cc-511">予測が適切で、このイメージをサービスのトレーニングモデルに追加する場合は、[ *マイタグ* ] 入力ボックスをクリックし、関連付けるタグを選択します。</span><span class="sxs-lookup"><span data-stu-id="498cc-511">If you the predictions were correct, and you wish to add this image to your Service's training model, click the *My Tags* input box, and select the tag you wish to associate.</span></span> <span data-ttu-id="498cc-512">操作が完了したら、右下にある [ *保存して閉じる* ] ボタンをクリックし、次の画像に進みます。</span><span class="sxs-lookup"><span data-stu-id="498cc-512">When you are finished, click the *Save and close* button to the bottom right, and continue on to the next image.</span></span>

    ![開くイメージの選択](images/AzureLabs-Lab302b-37.png)

4. <span data-ttu-id="498cc-514">画像のグリッドに戻ると、タグを追加した (および保存した) イメージが削除されます。</span><span class="sxs-lookup"><span data-stu-id="498cc-514">Once you are back to the grid of images, you will notice the images which you have added tags to (and saved), will be removed.</span></span> <span data-ttu-id="498cc-515">タグ付けされた項目がないと思われるイメージが見つかった場合は、そのイメージの目盛りをクリックし (複数のイメージに対してこれを実行できます)、グリッドページの右上隅にある [ *削除* ] をクリックすることで、イメージを削除できます。</span><span class="sxs-lookup"><span data-stu-id="498cc-515">If you find any images which you think do not have your tagged item within them, you can delete them, by clicking the tick on that image (can do this for several images) and then clicking *Delete* in the upper right corner of the grid page.</span></span> <span data-ttu-id="498cc-516">次のポップアップで、[はい]、[ *削除* ]、または [ *いいえ* ] をクリックして、それぞれ削除を確認するか、キャンセルします。</span><span class="sxs-lookup"><span data-stu-id="498cc-516">On the popup that follows, you can click either *Yes, delete* or *No* , to confirm the deletion or cancel it, respectively.</span></span> 

    ![イメージを削除する](images/AzureLabs-Lab302b-38.png)

5. <span data-ttu-id="498cc-518">操作を続行する準備ができたら、右上にある緑色の [ *Train* ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="498cc-518">When you are ready to proceed, click the green *Train* button in the top right.</span></span> <span data-ttu-id="498cc-519">サービスモデルは、現在提供されているすべてのイメージでトレーニングされます (これにより、より正確になります)。</span><span class="sxs-lookup"><span data-stu-id="498cc-519">Your Service model will be trained with all the images which you have now provided (which will make it more accurate).</span></span> <span data-ttu-id="498cc-520">トレーニングが完了したら、[ *既定値* に設定] ボタンをもう一度クリックし、 *予測 URL* がサービスの最新のイテレーションを引き続き使用するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="498cc-520">Once the training is complete, make sure to click the *Make default* button once more, so that your *Prediction URL* continues to use the most up-to-date iteration of your Service.</span></span>

    <span data-ttu-id="498cc-521">![トレーニングサービスモデルの開始 ](images/AzureLabs-Lab302b-39.png) ![ [既定の設定] オプションの選択](images/AzureLabs-Lab302b-40.png)</span><span class="sxs-lookup"><span data-stu-id="498cc-521">![Start training service model](images/AzureLabs-Lab302b-39.png) ![Select make default option](images/AzureLabs-Lab302b-40.png)</span></span>

## <a name="your-finished-custom-vision-api-application"></a><span data-ttu-id="498cc-522">完成した Custom Vision API アプリケーション</span><span class="sxs-lookup"><span data-stu-id="498cc-522">Your finished Custom Vision API application</span></span>

<span data-ttu-id="498cc-523">これで、Azure Custom Vision API を活用して実際のオブジェクトを認識し、サービスモデルをトレーニングし、表示されている内容の信頼性を表示する、mixed reality アプリを構築しました。</span><span class="sxs-lookup"><span data-stu-id="498cc-523">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision API to recognize real world objects, train the Service model, and display confidence of what has been seen.</span></span>

![完成したプロジェクトの例](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="498cc-525">ボーナス演習</span><span class="sxs-lookup"><span data-stu-id="498cc-525">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="498cc-526">演習1</span><span class="sxs-lookup"><span data-stu-id="498cc-526">Exercise 1</span></span>

<span data-ttu-id="498cc-527">**Custom Vision Service** をトレーニングして、より多くのオブジェクトを認識します。</span><span class="sxs-lookup"><span data-stu-id="498cc-527">Train your **Custom Vision Service** to recognize more objects.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="498cc-528">演習2</span><span class="sxs-lookup"><span data-stu-id="498cc-528">Exercise 2</span></span>

<span data-ttu-id="498cc-529">学習した内容を拡張する方法として、次の演習を実行します。</span><span class="sxs-lookup"><span data-stu-id="498cc-529">As a way to expand on what you have learned, complete the following exercises:</span></span>

<span data-ttu-id="498cc-530">オブジェクトが認識されたときにサウンドを再生します。</span><span class="sxs-lookup"><span data-stu-id="498cc-530">Play a sound when an object is recognized.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="498cc-531">演習3</span><span class="sxs-lookup"><span data-stu-id="498cc-531">Exercise 3</span></span>

<span data-ttu-id="498cc-532">API を使用して、アプリが分析しているのと同じイメージでサービスを再トレーニングします。これにより、サービスの精度が向上します (予測とトレーニングの両方を同時に行うことができます)。</span><span class="sxs-lookup"><span data-stu-id="498cc-532">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
