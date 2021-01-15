---
title: アプリの配布
description: サポートされているさまざまなプラットフォームおよび公開ストアのさまざまなディストリビューションオプションの概要です。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens、Mixed Reality、イマーシブヘッドセット、アプリ、uwp、送信、送信、フィルター、メタデータ、システム要件、キーワード、wack、認定、パッケージ、appx、販売促進
ms.openlocfilehash: b729bd65413587d3ad3b05bef495349b60a6fffd
ms.sourcegitcommit: 47a5c86b4694449c825902631777a9962a40e332
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98215977"
---
# <a name="distributing-your-apps"></a><span data-ttu-id="42780-104">アプリの配布</span><span class="sxs-lookup"><span data-stu-id="42780-104">Distributing your apps</span></span>

![WMR ホームの Floaty 鳥3D アプリ lancher](images/distribute-hero-image.png)

<span data-ttu-id="42780-106">アプリをユーザーの手に入れたり、世界に painstaking たりすることは、開発作業の中で最も重要で、場合によっては、その一部となることがあります。</span><span class="sxs-lookup"><span data-stu-id="42780-106">Getting your apps into the hands of your users or out into the world is the most important, and sometimes painstaking, part of any development effort.</span></span> <span data-ttu-id="42780-107">このプロセスは、お客様またはお客様のチームに最適なディストリビューションおよびデプロイシナリオに応じて、一連のリソースに簡略化されています。</span><span class="sxs-lookup"><span data-stu-id="42780-107">We've simplified the process into a set of resources, which depend on the distribution and deployment scenario that's best suited for you or your team.</span></span>

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a><span data-ttu-id="42780-108">[分布] オプション</span><span class="sxs-lookup"><span data-stu-id="42780-108">Distribution options</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="42780-109">別のパーティとアプリを共有している場合は、appx ファイルをビルドして提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="42780-109">If you're sharing your app with another party, you need to build and supply the appx file.</span></span> 
>     * <span data-ttu-id="42780-110">アプリインストーラーを使用している場合は、ユーザーと証明書を共有する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="42780-110">If you're using App Installer, you'll also need to share the certificate with the user.</span></span>
> 
> * <span data-ttu-id="42780-111">組織と共有している場合は、職場または学校のアカウントがあり、組織の [MDM (モバイルデバイス管理)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) インフラストラクチャにアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="42780-111">If you're sharing with an organization, you need a work or school account and access to the organizations [MDM (Mobile Device Management)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) infrastructure.</span></span>  
>    * <span data-ttu-id="42780-112">共有パーティの場合は、テナントの管理者であり、 [Microsoft Endpoint Manager 管理センター](https://docs.microsoft.com/mem/intune/apps/apps-deploy) を使用してアプリを利用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="42780-112">If you're the sharing party, you need to be an Admin in your tenant and use the [Microsoft Endpoint Manager admin center](https://docs.microsoft.com/mem/intune/apps/apps-deploy) to make the app available.</span></span> <span data-ttu-id="42780-113">別の方法として、appx ファイルとアプリの依存関係をエンドユーザーと共有することもできます。</span><span class="sxs-lookup"><span data-stu-id="42780-113">Another option is to share the appx file and the app dependencies with your end user.</span></span>
>    * <span data-ttu-id="42780-114">エンドユーザーの場合、アプリは、共有組織のテナントに登録すると、自動的にダウンロードされるか、ダウンロードできるようになります。</span><span class="sxs-lookup"><span data-stu-id="42780-114">If you're the end user, the app will either automatically download or be available for download once you enroll with the sharing organization's tenant.</span></span> 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><span data-ttu-id="42780-115"><strong>シナリオ</strong></span><span class="sxs-lookup"><span data-stu-id="42780-115"><strong>Scenario</strong></span></span></td>
    <td><span data-ttu-id="42780-116"><strong>ローカルデバイスのインストール</strong></span><span class="sxs-lookup"><span data-stu-id="42780-116"><strong>Local device installs</strong></span></span></td>
    <td><span data-ttu-id="42780-117"><strong>だれとでも共有</strong></span><span class="sxs-lookup"><span data-stu-id="42780-117"><strong>Share with anyone</strong></span></span></td>
    <td><span data-ttu-id="42780-118"><strong>組織と共有する</strong></span><span class="sxs-lookup"><span data-stu-id="42780-118"><strong>Share with an organization</strong></span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="42780-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>アプリのインストーラー</strong></span><span class="sxs-lookup"><span data-stu-id="42780-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>App Installer</strong></span></span></td>
    <td><span data-ttu-id="42780-120">✔️</span><span class="sxs-lookup"><span data-stu-id="42780-120">✔️</span></span></td>
    <td><span data-ttu-id="42780-121">✔️</span><span class="sxs-lookup"><span data-stu-id="42780-121">✔️</span></span></td>
    <td>❌</td>
</tr>
<tr>
    <td><span data-ttu-id="42780-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM-ポータルサイト</strong></a></span><span class="sxs-lookup"><span data-stu-id="42780-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM - Company Portal</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="42780-123">✔️</span><span class="sxs-lookup"><span data-stu-id="42780-123">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="42780-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM-必須アプリのインストール</strong></a></span><span class="sxs-lookup"><span data-stu-id="42780-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM - Required App Install</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="42780-125">✔️</span><span class="sxs-lookup"><span data-stu-id="42780-125">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="42780-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span><span class="sxs-lookup"><span data-stu-id="42780-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span></span></td>
    <td>❌</td>
    <td><span data-ttu-id="42780-127">✔️</span><span class="sxs-lookup"><span data-stu-id="42780-127">✔️</span></span></td>
    <td><span data-ttu-id="42780-128">✔️</span><span class="sxs-lookup"><span data-stu-id="42780-128">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="42780-129"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>ビジネス向け Microsoft Store</strong></a></span><span class="sxs-lookup"><span data-stu-id="42780-129"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store for Business</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="42780-130">✔️</span><span class="sxs-lookup"><span data-stu-id="42780-130">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="42780-131"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>プロビジョニングパッケージ</strong></a></span><span class="sxs-lookup"><span data-stu-id="42780-131"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Provisioning Package</strong></a></span></span></td>
    <td><span data-ttu-id="42780-132">✔️</span><span class="sxs-lookup"><span data-stu-id="42780-132">✔️</span></span></td>
    <td><span data-ttu-id="42780-133">✔️</span><span class="sxs-lookup"><span data-stu-id="42780-133">✔️</span></span></td>
    <td><span data-ttu-id="42780-134">✔️</span><span class="sxs-lookup"><span data-stu-id="42780-134">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="42780-135"><a href="#other-scenarios"><strong>カスタム Win32 展開</strong></a> (HoloLens デバイスでは使用できません。下記を参照)</span><span class="sxs-lookup"><span data-stu-id="42780-135"><a href="#other-scenarios"><strong>Custom Win32 deployment</strong></a> (Not available for HoloLens devices - see below)</span></span></td>
    <td><span data-ttu-id="42780-136">✔️</span><span class="sxs-lookup"><span data-stu-id="42780-136">✔️</span></span></td>
    <td><span data-ttu-id="42780-137">✔️</span><span class="sxs-lookup"><span data-stu-id="42780-137">✔️</span></span></td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="42780-138">アプリインストーラーは、現在、管理対象デバイスまたは HoloLens (第1世代) デバイスでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="42780-138">App Installer isn't currently available for managed devices or HoloLens (1st Gen) devices.</span></span>

## <a name="other-scenarios"></a><span data-ttu-id="42780-139">その他のシナリオ</span><span class="sxs-lookup"><span data-stu-id="42780-139">Other scenarios</span></span>

* <span data-ttu-id="42780-140">Win32 を作成できます。ストリームとゲームパスを含む、Win32 アプリケーションのデプロイのために Unity からの PC スタンドアロンビルドターゲットを使用する EXE ファイル。</span><span class="sxs-lookup"><span data-stu-id="42780-140">You can produce a Win32 .EXE file using the PC Standalone build target from Unity for Win32 application deployment, including Steam and Game Pass.</span></span> <span data-ttu-id="42780-141">を作成したら、EXE を使用して、選択したプラットフォームに通常どおりにアプリを送信できます。</span><span class="sxs-lookup"><span data-stu-id="42780-141">Once you have the .EXE, you can submit your apps as normal to your chosen platform.</span></span> 

* <span data-ttu-id="42780-142">オフライン中に HoloLens 2 アプリケーションをインストールする必要がある場合は、オフラインの [Secure HoloLens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) の手順を参照するか、開発者モードを有効にせずにプロビジョニングパッケージを使用してアプリをインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="42780-142">If you need to install a HoloLens 2 application while you're offline, refer to the [offline secure HoloLens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) instructions or install the app through a Provisioning Package without enabling developer mode.</span></span>

* <span data-ttu-id="42780-143">また、ビルドをデバイスに配置し、開発者モードが有効になっている他の開発者と共有することもできます。これには、 [Visual Studio でのデプロイとデバッグ](../develop/platform-capabilities-and-apis/using-visual-studio.md) 、または [デバイスポータルを使用したアプリケーションパッケージのインストール](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#sideloading-applications)が含まれます。</span><span class="sxs-lookup"><span data-stu-id="42780-143">You can also deploy builds to your device and share them with other developers who have Developer Mode enabled by [deploying and debugging with Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) or [installing an application package with the Device Portal](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#sideloading-applications).</span></span>

## <a name="see-also"></a><span data-ttu-id="42780-144">こちらもご覧ください</span><span class="sxs-lookup"><span data-stu-id="42780-144">See also</span></span>
* [<span data-ttu-id="42780-145">Microsoft Store からのアプリケーションの検索、インストール、およびアンインストール</span><span class="sxs-lookup"><span data-stu-id="42780-145">Finding, installing, and uninstalling applications from the Microsoft Store</span></span>](https://docs.microsoft.com/hololens/holographic-store-apps)

