---
ms.openlocfilehash: 283bfffb2d59d92712e86e12c05be8974f04fae6
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2020
ms.locfileid: "97717945"
---
# <a name="unity"></a>[<span data-ttu-id="7197c-101">Unity</span><span class="sxs-lookup"><span data-stu-id="7197c-101">Unity</span></span>](#tab/unity)

![Unity のロゴ バナー](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a><span data-ttu-id="7197c-103">1.最新バージョンをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="7197c-103">1. Download the latest version</span></span>

<span data-ttu-id="7197c-104">新しいプロジェクトを開始する際に使用する最適なバージョンとして、[Unity LTS (長期サポート)](https://unity3d.com/unity/qa/lts-releases) ストリームをお勧めします。最新の安定した修正プログラムを取得するには最新リビジョンに更新します。</span><span class="sxs-lookup"><span data-stu-id="7197c-104">We recommend the [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) stream as the best version to use when starting new projects, updating to its latest revision to pick up the latest stable fixes.</span></span>
* <span data-ttu-id="7197c-105">現在は、**Unity 2019** を使用することをお勧めしています。これは、以下の MRTK v2 に必要な LTS ビルドです。</span><span class="sxs-lookup"><span data-stu-id="7197c-105">The current recommendation is to use **Unity 2019**, which is the LTS build required for MRTK v2 below.</span></span>
* <span data-ttu-id="7197c-106">特定の理由から別のバージョンの Unity を使用する必要がある場合、Unity では異なるバージョンの side-by-side インストールをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="7197c-106">If you need to use a different version of Unity for specific reasons, Unity supports side-by-side installs of different versions.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="7197c-107">2.Mixed Reality Toolkit (MRTK) をインポートする</span><span class="sxs-lookup"><span data-stu-id="7197c-107">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="7197c-109">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) は、Mixed Reality アプリケーション向けのオープンソースのクロスプラットフォーム開発キットです。</span><span class="sxs-lookup"><span data-stu-id="7197c-109">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="7197c-110">MRTK には、空間でのインタラクションのための、クロスプラットフォームの入力システム、基本コンポーネント、共通の構成要素が備わっています。</span><span class="sxs-lookup"><span data-stu-id="7197c-110">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="7197c-111">このツールキットは、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォームをターゲットとしたアプリケーションの開発を加速することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="7197c-111">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="7197c-112">インストールについては、整理された [Unity 開発体験](../unity/unity-development-overview.md)の[「はじめに」セクション](../unity/unity-development-overview.md#1-getting-started)を完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7197c-112">For installation, we recommend completing the [Getting Started section](../unity/unity-development-overview.md#1-getting-started) of our curated [Unity development journey](../unity/unity-development-overview.md).</span></span> <span data-ttu-id="7197c-113">既に Unity 開発体験に従っている読者は、以下にリストされている残りの設定手順を完了し、[HoloLens 2 入門チュートリアル](../unity/tutorials/mr-learning-base-01.md)に進んでください。</span><span class="sxs-lookup"><span data-stu-id="7197c-113">If you're already following the Unity development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unity/tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7197c-114">インストール手順では MRTK と Unity リリースの最新の安定した組み合わせである **MRTK 2.4.0** と **Unity 2019.3.15** を対象としていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7197c-114">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.4.0** and **Unity 2019.3.15**.</span></span>

> [!NOTE]
> <span data-ttu-id="7197c-115">Unity 用の MRTK を使用しない場合は、すべての対話式操作と動作のスクリプトを開発者が自分で作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7197c-115">If you don't want to use MRTK for Unity, you'll need to script all interactions and behaviors yourself.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="7197c-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity バナー](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="7197c-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="7197c-117">**Mixed Reality Toolkit-Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="7197c-117">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a><span data-ttu-id="7197c-118">その他のツール (省略可能)</span><span class="sxs-lookup"><span data-stu-id="7197c-118">Other tools [optional]</span></span>
* <span data-ttu-id="7197c-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - HoloLens やイマーシブ (VR) ヘッドセットで直接動作しない可能性があるコード ビットとコンポーネントですが、これらを組み合わせることで、Windows Mixed Reality をターゲットとしたエクスペリエンスを構築します。</span><span class="sxs-lookup"><span data-stu-id="7197c-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="7197c-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - 共有スクリプトとコンポーネントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="7197c-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="7197c-121">3.Mixed Reality 開発用 PC を設定する</span><span class="sxs-lookup"><span data-stu-id="7197c-121">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="7197c-122">Windows 10 SDK は、Windows 10 オペレーティング システムでの使用に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="7197c-122">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="7197c-123">この SDK は、Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 でもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7197c-123">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="7197c-124">以前のオペレーティング システムでは、一部のツールがサポートされないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="7197c-124">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="7197c-125">HoloLens 用アプリ、VR イマーシブ ヘッドセット用アプリ、またはこれらの両方に使用できるアプリを開発して展開できます。</span><span class="sxs-lookup"><span data-stu-id="7197c-125">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="7197c-126">必要に応じて、以下の要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="7197c-126">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="7197c-127">HoloLens の開発の場合</span><span class="sxs-lookup"><span data-stu-id="7197c-127">For HoloLens development</span></span>

<span data-ttu-id="7197c-128">開発用の PC を HoloLens の開発用に設定するときは、<a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> と <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> の両方のシステム要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="7197c-128">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="7197c-129">HoloLens デバイスでアプリを実行するには、[Windows デバイス ポータルのセットアップ手順](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="7197c-129">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="7197c-130">[HoloLens エミュレーター](../platform-capabilities-and-apis/using-the-hololens-emulator.md)を使用する予定の場合は、お使いの PC が [HoloLens エミュレーターのシステム要件](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)も満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7197c-130">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="7197c-131">HoloLens エミュレーターを開始するには、「[Using the HoloLens emulator (HoloLens エミュレーターを使用する)](../platform-capabilities-and-apis/using-the-hololens-emulator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7197c-131">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="7197c-132">HoloLens と Windows Mixed Reality イマーシブ (VR) ヘッドセットの両方を対象とした開発を予定している場合は、以下のセクションに記載のシステムの推奨事項と要件をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="7197c-132">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="7197c-133">HoloLens のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="7197c-133">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="7197c-134">開発者モードの設定がグレー表示される</span><span class="sxs-lookup"><span data-stu-id="7197c-134">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="7197c-135">デバイスで開発者モードを有効にする際に問題が発生する場合は、自身が[デバイスの所有者](https://docs.microsoft.com/hololens/security-adminless-os)ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7197c-135">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](https://docs.microsoft.com/hololens/security-adminless-os).</span></span> <span data-ttu-id="7197c-136">マルチユーザー モードでは、最初にデバイスを使用するユーザーがデバイスの所有者であり、それ以降のユーザーには、開発者モードまたはその他の構成の変更を有効にするために必要なアクセス許可は付与されません。</span><span class="sxs-lookup"><span data-stu-id="7197c-136">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="7197c-137">ただし、最初のユーザーがオートパイロット環境にいるためデバイスの所有者ではないという例外があります。詳しくは、[HoloLens のセキュリティに関するドキュメント](https://docs.microsoft.com/hololens/security-adminless-os#device-owner)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7197c-137">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](https://docs.microsoft.com/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="7197c-138">考えられる解決策:</span><span class="sxs-lookup"><span data-stu-id="7197c-138">Possible solutions include:</span></span>

* <span data-ttu-id="7197c-139">デバイスを他のユーザーまたは開発者に渡す前に、デバイス所有者に開発者モードをオンにさせます</span><span class="sxs-lookup"><span data-stu-id="7197c-139">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="7197c-140">IT/MDM 管理者が特定のデバイスまたは開発者のデバイス グループに対して CSP [ポリシー ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) を有効にすることを提案します。</span><span class="sxs-lookup"><span data-stu-id="7197c-140">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="7197c-141">このポリシーは、[プロビジョニング パッケージ](https://docs.microsoft.com/hololens/hololens-provisioning)を使うか、[HoloLens デバイス用 MDM](https://docs.microsoft.com/hololens/hololens-mdm-configure) 経由で設定できます。</span><span class="sxs-lookup"><span data-stu-id="7197c-141">This policy can be set by [Provisioning Packages](https://docs.microsoft.com/hololens/hololens-provisioning) or via [MDM for HoloLens devices](https://docs.microsoft.com/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="7197c-142">[Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery) を使用します</span><span class="sxs-lookup"><span data-stu-id="7197c-142">Using the [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="7197c-143">デバイス管理の詳細については、 **[HoloLens デバイス管理](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** の概要を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7197c-143">You can learn more about device management in the **[HoloLens device management](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="7197c-144">USB 経由で展開できない</span><span class="sxs-lookup"><span data-stu-id="7197c-144">I can't deploy over USB</span></span>

<span data-ttu-id="7197c-145">USB 経由で直接アプリケーションを展開できない場合は、上記のすべてのインストール要件を満たしていることを確認し、[ステップバイステップ チュートリアル](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2)に従ってください。</span><span class="sxs-lookup"><span data-stu-id="7197c-145">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="7197c-146">イマーシブ (VR) ヘッドセットの要件</span><span class="sxs-lookup"><span data-stu-id="7197c-146">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="7197c-147">以下のガイドラインは、イマーシブ (VR) ヘッドセットの *開発用 PC* に対する現在の最小かつ推奨仕様であり、定期的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="7197c-147">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="7197c-148">この仕様を、[PC ハードウェア互換性最小ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)と間違えないようにしてください。このガイドラインは、イマーシブ (VR) ヘッドセットのアプリまたはゲームの対象となる *コンシューマー PC の仕様* について説明するものです。</span><span class="sxs-lookup"><span data-stu-id="7197c-148">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="7197c-149">イマーシブ ヘッドセット開発用 PC にフルサイズの HDMI および/または USB 3.0 ポートがない場合、ヘッドセットを接続するための[アダプター](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)が必要になります。</span><span class="sxs-lookup"><span data-stu-id="7197c-149">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="7197c-150">一部のハードウェア構成、特にハイブリッド グラフィックスを搭載したノートブックなどには、現在[既知の問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)があります。</span><span class="sxs-lookup"><span data-stu-id="7197c-150">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="7197c-151">最小</span><span class="sxs-lookup"><span data-stu-id="7197c-151">Minimum</span></span></th><th> <span data-ttu-id="7197c-152">推奨</span><span class="sxs-lookup"><span data-stu-id="7197c-152">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="7197c-153">プロセッサ</span><span class="sxs-lookup"><span data-stu-id="7197c-153">Processor</span></span></td><td> <span data-ttu-id="7197c-154"><b>ノートブック:</b>Intel Mobile Core i5 第 7 世代 CPU、ハイパー スレッディング対応デュアルコア <b>デスクトップ:</b>Intel Desktop i5 第 6 世代 CPU、ハイパー スレッディング対応デュアルコア<b>または</b> AMD FX4350 4.2GHz クワッドコア相当</span><span class="sxs-lookup"><span data-stu-id="7197c-154"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="7197c-155"><b>デスクトップ:</b>Intel Desktop i7 第 6 世代 (6 コア) <b>または</b> AMD Ryzen 5 1600 (6 コア、12 スレッド)</span><span class="sxs-lookup"><span data-stu-id="7197c-155"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-156">GPU</span><span class="sxs-lookup"><span data-stu-id="7197c-156">GPU</span></span></td><td> <span data-ttu-id="7197c-157"><b>ノートブック:</b>NVIDIA GTX 965M、AMD RX 460M (2 GB) 相当またはそれ以上の DX12 対応 GPU <b>デスクトップ:</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="7197c-157"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="7197c-158"><b>デスクトップ:</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="7197c-158"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-159">GPU ドライバー WDDM バージョン</span><span class="sxs-lookup"><span data-stu-id="7197c-159">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="7197c-160">WDDM 2.2 ドライバー</span><span class="sxs-lookup"><span data-stu-id="7197c-160">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-161">熱設計電力</span><span class="sxs-lookup"><span data-stu-id="7197c-161">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="7197c-162">15 W 以上</span><span class="sxs-lookup"><span data-stu-id="7197c-162">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-163">グラフィックス表示ポート</span><span class="sxs-lookup"><span data-stu-id="7197c-163">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="7197c-164">ヘッドセット用の使用可能なグラフィックス ディスプレイ ポート (60 Hz ヘッドセットの場合は HDMI 1.4 または DisplayPort 1.2、90 Hz ヘッドセットの場合は HDMI 2.0 または DisplayPort 1.2) x 1</span><span class="sxs-lookup"><span data-stu-id="7197c-164">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-165">画面の解像度</span><span class="sxs-lookup"><span data-stu-id="7197c-165">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="7197c-166">解像度:SVGA (800 x 600) 以上のビットの深度:1 ピクセルあたり 32 ビット色</span><span class="sxs-lookup"><span data-stu-id="7197c-166">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-167">メモリ</span><span class="sxs-lookup"><span data-stu-id="7197c-167">Memory</span></span></td><td> <span data-ttu-id="7197c-168">8&#160;GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="7197c-168">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="7197c-169">16 GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="7197c-169">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-170">記憶域</span><span class="sxs-lookup"><span data-stu-id="7197c-170">Storage</span></span></td><td colspan="2"> <span data-ttu-id="7197c-171">&gt;10 GB の追加の空き領域</span><span class="sxs-lookup"><span data-stu-id="7197c-171">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-172">USB ポート</span><span class="sxs-lookup"><span data-stu-id="7197c-172">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="7197c-173">ヘッドセット (USB 3.0 Type-A) の使用可能な USB ポート x 1<b>メモ:USB は、最低 900 mA を給電する必要があります</b></span><span class="sxs-lookup"><span data-stu-id="7197c-173">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-174">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="7197c-174">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="7197c-175">Bluetooth 4.0 (アクセサリ接続用)</span><span class="sxs-lookup"><span data-stu-id="7197c-175">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="7197c-176">Unity を使用した MRTK 開発を初めて行う場合は、整理された Unity 開発体験に従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7197c-176">If you're new to MRTK development with Unity, we recommend following our curated Unity development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7197c-177">Unity の体験を開始する</span><span class="sxs-lookup"><span data-stu-id="7197c-177">Start your Unity journey</span></span>](../unity/unity-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="7197c-178">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="7197c-178">Next Development Checkpoint</span></span>

<span data-ttu-id="7197c-179">私たちが用意した Unity 開発チェックポイント体験に従っている場合、次のタスクは HoloLens 2 チュートリアル シリーズを実行することです。</span><span class="sxs-lookup"><span data-stu-id="7197c-179">If you're following the Unity development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7197c-180">HoloLens 2 チュートリアル シリーズ</span><span class="sxs-lookup"><span data-stu-id="7197c-180">HoloLens 2 tutorial series</span></span>](../unity/tutorials/mr-learning-base-01.md)

<span data-ttu-id="7197c-181">いつでも [Unity 開発チェックポイント](../unity/unity-development-overview.md#1-getting-started)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="7197c-181">You can always go back to the [Unity development checkpoints](../unity/unity-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="unreal"></a>[<span data-ttu-id="7197c-182">Unreal</span><span class="sxs-lookup"><span data-stu-id="7197c-182">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="7197c-184">1.最新バージョンをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="7197c-184">1. Download the latest version</span></span>

<span data-ttu-id="7197c-185">組み込みの HoloLens サポートを最大限に活用するため、[Unreal Engine バージョン 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 以降をインストールすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7197c-185">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="7197c-186">2.Mixed Reality Toolkit (MRTK) をインポートする</span><span class="sxs-lookup"><span data-stu-id="7197c-186">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="7197c-188">Mixed Reality Toolkit (MRTK) は、Mixed Reality アプリケーション向けのオープン ソースのクロスプラットフォーム開発キットです。</span><span class="sxs-lookup"><span data-stu-id="7197c-188">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="7197c-189">MRTK には、空間でのインタラクションのための、クロスプラットフォームの入力システム、基本コンポーネント、共通の構成要素が備わっています。</span><span class="sxs-lookup"><span data-stu-id="7197c-189">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="7197c-190">このツールキットは、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォームをターゲットとしたアプリケーションの開発を加速することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="7197c-190">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="7197c-191">インストールについては、整理された [ 開発体験](../unreal/unreal-development-overview.md)の[「はじめに」セクション](../unreal/unreal-development-overview.md#1-getting-started)を完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7197c-191">For installation, we recommend completing the [Getting Started section](../unreal/unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](../unreal/unreal-development-overview.md).</span></span> <span data-ttu-id="7197c-192">既に Unreal 開発体験に従っている読者は、以下にリストされている残りの設定手順を完了し、[HoloLens 2 入門チュートリアル](../unreal/tutorials/unreal-uxt-ch1.md)に進んでください。</span><span class="sxs-lookup"><span data-stu-id="7197c-192">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unreal/tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="7197c-193"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity のロゴ画像](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="7197c-193"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="7197c-194">**Mixed Reality Toolkit-Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="7197c-194">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="7197c-195">Unreal 用の MRTK を使用しない場合は、すべての対話式操作と動作のスクリプトを開発者が自分で作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7197c-195">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="7197c-196">その他のツール (省略可能)</span><span class="sxs-lookup"><span data-stu-id="7197c-196">Other tools [optional]</span></span>
* <span data-ttu-id="7197c-197"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - HoloLens やイマーシブ (VR) ヘッドセットで直接動作しない可能性があるコード ビットとコンポーネントですが、これらを組み合わせることで、Windows Mixed Reality をターゲットとしたエクスペリエンスを構築します。</span><span class="sxs-lookup"><span data-stu-id="7197c-197"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="7197c-198"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - 共有スクリプトとコンポーネントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="7197c-198"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="7197c-199">3.Mixed Reality 開発用 PC を設定する</span><span class="sxs-lookup"><span data-stu-id="7197c-199">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="7197c-200">Windows 10 SDK は、Windows 10 オペレーティング システムでの使用に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="7197c-200">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="7197c-201">この SDK は、Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 でもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7197c-201">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="7197c-202">以前のオペレーティング システムでは、一部のツールがサポートされないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="7197c-202">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="7197c-203">HoloLens 用アプリ、VR イマーシブ ヘッドセット用アプリ、またはこれらの両方に使用できるアプリを開発して展開できます。</span><span class="sxs-lookup"><span data-stu-id="7197c-203">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="7197c-204">必要に応じて、以下の要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="7197c-204">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="7197c-205">HoloLens の開発の場合</span><span class="sxs-lookup"><span data-stu-id="7197c-205">For HoloLens development</span></span>

<span data-ttu-id="7197c-206">HoloLens の開発用に開発用 PC を設定するときは、[Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) と <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> の両方のシステム要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="7197c-206">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="7197c-207">HoloLens デバイスでアプリを実行するには、[Windows デバイス ポータルのセットアップ手順](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="7197c-207">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="7197c-208">[HoloLens エミュレーター](../platform-capabilities-and-apis/using-the-hololens-emulator.md)を使用する予定の場合は、お使いの PC が [HoloLens エミュレーターのシステム要件](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)も満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7197c-208">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="7197c-209">HoloLens と Windows Mixed Reality イマーシブ (VR) ヘッドセットの両方を対象とした開発を予定している場合は、以下のセクションに記載のシステムの推奨事項と要件をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="7197c-209">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="7197c-210">HoloLens のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="7197c-210">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="7197c-211">開発者モードの設定がグレー表示される</span><span class="sxs-lookup"><span data-stu-id="7197c-211">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="7197c-212">デバイスで開発者モードを有効にする際に問題が発生する場合は、自身が[デバイスの所有者](https://docs.microsoft.com/hololens/security-adminless-os)ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7197c-212">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](https://docs.microsoft.com/hololens/security-adminless-os).</span></span> <span data-ttu-id="7197c-213">マルチユーザー モードでは、最初にデバイスを使用するユーザーがデバイスの所有者であり、それ以降のユーザーには、開発者モードまたはその他の構成の変更を有効にするために必要なアクセス許可は付与されません。</span><span class="sxs-lookup"><span data-stu-id="7197c-213">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="7197c-214">ただし、最初のユーザーがオートパイロット環境にいるためデバイスの所有者ではないという例外があります。詳しくは、[HoloLens のセキュリティに関するドキュメント](https://docs.microsoft.com/hololens/security-adminless-os#device-owner)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7197c-214">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](https://docs.microsoft.com/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="7197c-215">考えられる解決策:</span><span class="sxs-lookup"><span data-stu-id="7197c-215">Possible solutions include:</span></span>

* <span data-ttu-id="7197c-216">デバイスを他のユーザーまたは開発者に渡す前に、デバイス所有者に開発者モードをオンにさせます</span><span class="sxs-lookup"><span data-stu-id="7197c-216">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="7197c-217">IT/MDM 管理者が特定のデバイスまたは開発者のデバイス グループに対して CSP [ポリシー ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) を有効にすることを提案します。</span><span class="sxs-lookup"><span data-stu-id="7197c-217">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="7197c-218">このポリシーは、[プロビジョニング パッケージ](https://docs.microsoft.com/hololens/hololens-provisioning)を使うか、[HoloLens デバイス用 MDM](https://docs.microsoft.com/hololens/hololens-mdm-configure) 経由で設定できます。</span><span class="sxs-lookup"><span data-stu-id="7197c-218">This policy can be set by [Provisioning Packages](https://docs.microsoft.com/hololens/hololens-provisioning) or via [MDM for HoloLens devices](https://docs.microsoft.com/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="7197c-219">[Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery) を使用します</span><span class="sxs-lookup"><span data-stu-id="7197c-219">Using the [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="7197c-220">デバイス管理の詳細については、 **[HoloLens デバイス管理](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** の概要を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7197c-220">You can learn more about device management in the **[HoloLens device management](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="7197c-221">USB 経由で展開できない</span><span class="sxs-lookup"><span data-stu-id="7197c-221">I can't deploy over USB</span></span>

<span data-ttu-id="7197c-222">USB 経由で直接アプリケーションを展開できない場合は、上記のすべてのインストール要件を満たしていることを確認し、[ステップバイステップ チュートリアル](../unreal/tutorials/unreal-uxt-ch6.md)に従ってください。</span><span class="sxs-lookup"><span data-stu-id="7197c-222">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unreal/tutorials/unreal-uxt-ch6.md).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="7197c-223">イマーシブ (VR) ヘッドセットの要件</span><span class="sxs-lookup"><span data-stu-id="7197c-223">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="7197c-224">以下のガイドラインは、イマーシブ (VR) ヘッドセットの *開発用 PC* に対する現在の最小かつ推奨仕様であり、定期的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="7197c-224">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="7197c-225">この仕様を、[PC ハードウェア互換性最小ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)と間違えないようにしてください。このガイドラインは、イマーシブ (VR) ヘッドセットのアプリまたはゲームの対象となる *コンシューマー PC の仕様* について説明するものです。</span><span class="sxs-lookup"><span data-stu-id="7197c-225">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="7197c-226">イマーシブ ヘッドセット開発用 PC にフルサイズの HDMI および/または USB 3.0 ポートがない場合、ヘッドセットを接続するための[アダプター](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)が必要になります。</span><span class="sxs-lookup"><span data-stu-id="7197c-226">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="7197c-227">一部のハードウェア構成、特にハイブリッド グラフィックスを搭載したノートブックなどには、現在[既知の問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)があります。</span><span class="sxs-lookup"><span data-stu-id="7197c-227">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="7197c-228">最小</span><span class="sxs-lookup"><span data-stu-id="7197c-228">Minimum</span></span></th><th> <span data-ttu-id="7197c-229">推奨</span><span class="sxs-lookup"><span data-stu-id="7197c-229">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="7197c-230">プロセッサ</span><span class="sxs-lookup"><span data-stu-id="7197c-230">Processor</span></span></td><td> <span data-ttu-id="7197c-231"><b>ノートブック:</b>Intel Mobile Core i5 第 7 世代 CPU、ハイパー スレッディング対応デュアルコア <b>デスクトップ:</b>Intel Desktop i5 第 6 世代 CPU、ハイパー スレッディング対応デュアルコア<b>または</b> AMD FX4350 4.2GHz クワッドコア相当</span><span class="sxs-lookup"><span data-stu-id="7197c-231"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="7197c-232"><b>デスクトップ:</b>Intel Desktop i7 第 6 世代 (6 コア) <b>または</b> AMD Ryzen 5 1600 (6 コア、12 スレッド)</span><span class="sxs-lookup"><span data-stu-id="7197c-232"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-233">GPU</span><span class="sxs-lookup"><span data-stu-id="7197c-233">GPU</span></span></td><td> <span data-ttu-id="7197c-234"><b>ノートブック:</b>NVIDIA GTX 965M、AMD RX 460M (2 GB) 相当またはそれ以上の DX12 対応 GPU <b>デスクトップ:</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="7197c-234"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="7197c-235"><b>デスクトップ:</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="7197c-235"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-236">GPU ドライバー WDDM バージョン</span><span class="sxs-lookup"><span data-stu-id="7197c-236">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="7197c-237">WDDM 2.2 ドライバー</span><span class="sxs-lookup"><span data-stu-id="7197c-237">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-238">熱設計電力</span><span class="sxs-lookup"><span data-stu-id="7197c-238">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="7197c-239">15 W 以上</span><span class="sxs-lookup"><span data-stu-id="7197c-239">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-240">グラフィックス表示ポート</span><span class="sxs-lookup"><span data-stu-id="7197c-240">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="7197c-241">ヘッドセット用の使用可能なグラフィックス ディスプレイ ポート (60 Hz ヘッドセットの場合は HDMI 1.4 または DisplayPort 1.2、90 Hz ヘッドセットの場合は HDMI 2.0 または DisplayPort 1.2) x 1</span><span class="sxs-lookup"><span data-stu-id="7197c-241">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-242">画面の解像度</span><span class="sxs-lookup"><span data-stu-id="7197c-242">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="7197c-243">解像度:SVGA (800 x 600) 以上のビットの深度:1 ピクセルあたり 32 ビット色</span><span class="sxs-lookup"><span data-stu-id="7197c-243">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-244">メモリ</span><span class="sxs-lookup"><span data-stu-id="7197c-244">Memory</span></span></td><td> <span data-ttu-id="7197c-245">8&#160;GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="7197c-245">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="7197c-246">16 GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="7197c-246">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-247">記憶域</span><span class="sxs-lookup"><span data-stu-id="7197c-247">Storage</span></span></td><td colspan="2"> <span data-ttu-id="7197c-248">&gt;10 GB の追加の空き領域</span><span class="sxs-lookup"><span data-stu-id="7197c-248">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-249">USB ポート</span><span class="sxs-lookup"><span data-stu-id="7197c-249">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="7197c-250">ヘッドセット (USB 3.0 Type-A) の使用可能な USB ポート x 1<b>メモ:USB は、最低 900 mA を給電する必要があります</b></span><span class="sxs-lookup"><span data-stu-id="7197c-250">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-251">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="7197c-251">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="7197c-252">Bluetooth 4.0 (アクセサリ接続用)</span><span class="sxs-lookup"><span data-stu-id="7197c-252">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="7197c-253">Unreal を使用した MRTK 開発を初めて行う場合は、整理された Unreal 開発体験に従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7197c-253">If you're new to MRTK development with Unreal, we recommend following our curated Unreal development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7197c-254">Unreal の体験を開始する</span><span class="sxs-lookup"><span data-stu-id="7197c-254">Start your Unreal journey</span></span>](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="7197c-255">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="7197c-255">Next Development Checkpoint</span></span>

<span data-ttu-id="7197c-256">私たちが用意した Unreal 開発チェックポイント体験に従っている場合、次のタスクは HoloLens 2 チュートリアル シリーズを実行することです。</span><span class="sxs-lookup"><span data-stu-id="7197c-256">If you're following the Unreal development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7197c-257">HoloLens 2 チュートリアル シリーズ</span><span class="sxs-lookup"><span data-stu-id="7197c-257">HoloLens 2 tutorial series</span></span>](../unreal/tutorials/unreal-uxt-ch1.md)

<span data-ttu-id="7197c-258">いつでも [Unreal 開発チェックポイント](../unreal/unreal-development-overview.md#1-getting-started)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="7197c-258">You can always go back to the [Unreal development checkpoints](../unreal/unreal-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="native-openxr"></a>[<span data-ttu-id="7197c-259">ネイティブ (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="7197c-259">Native (OpenXR)</span></span>](#tab/native)

 ![ネイティブ アプリ開発](../images/native_logo_banner.png)

<span data-ttu-id="7197c-261">ネイティブな OpenXR 開発では、エンジンをダウンロードする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7197c-261">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="7197c-262">「[OpenXR の概要](../native/openxr-getting-started.md)」に、開発を開始するために必要なものがすべて記載されています。</span><span class="sxs-lookup"><span data-stu-id="7197c-262">You can find everything you need to begin development in the [Getting started with OpenXR](../native/openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="7197c-263">1.Mixed Reality 開発用 PC を設定する</span><span class="sxs-lookup"><span data-stu-id="7197c-263">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="7197c-264">Windows 10 SDK は、Windows 10 オペレーティング システムでの使用に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="7197c-264">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="7197c-265">この SDK は、Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 でもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7197c-265">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="7197c-266">以前のオペレーティング システムでは、一部のツールがサポートされないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="7197c-266">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="7197c-267">HoloLens の開発の場合</span><span class="sxs-lookup"><span data-stu-id="7197c-267">For HoloLens development</span></span>

<span data-ttu-id="7197c-268">HoloLens の開発用に開発用 PC を設定するときは、<a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> のシステム要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="7197c-268">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="7197c-269">HoloLens デバイスでアプリを実行するには、[Windows デバイス ポータルのセットアップ手順](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="7197c-269">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="7197c-270">[HoloLens エミュレーター](../platform-capabilities-and-apis/using-the-hololens-emulator.md)を使用する予定の場合は、お使いの PC が [HoloLens エミュレーターのシステム要件](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)も満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7197c-270">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="7197c-271">HoloLens と Windows Mixed Reality イマーシブ (VR) ヘッドセットの両方を対象とした開発を予定している場合は、以下のセクションに記載のシステムの推奨事項と要件をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="7197c-271">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="7197c-272">HoloLens 用アプリ、VR イマーシブ ヘッドセット用アプリ、またはこれらの両方に使用できるアプリを開発して展開できます。</span><span class="sxs-lookup"><span data-stu-id="7197c-272">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="7197c-273">必要に応じて、以下の要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="7197c-273">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="7197c-274">HoloLens のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="7197c-274">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="7197c-275">開発者モードの設定がグレー表示される</span><span class="sxs-lookup"><span data-stu-id="7197c-275">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="7197c-276">デバイスで開発者モードを有効にする際に問題が発生する場合は、自身が[デバイスの所有者](https://docs.microsoft.com/hololens/security-adminless-os)ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7197c-276">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](https://docs.microsoft.com/hololens/security-adminless-os).</span></span> <span data-ttu-id="7197c-277">マルチユーザー モードでは、最初にデバイスを使用するユーザーがデバイスの所有者であり、それ以降のユーザーには、開発者モードまたはその他の構成の変更を有効にするために必要なアクセス許可は付与されません。</span><span class="sxs-lookup"><span data-stu-id="7197c-277">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="7197c-278">ただし、最初のユーザーがオートパイロット環境にいるためデバイスの所有者ではないという例外があります。詳しくは、[HoloLens のセキュリティに関するドキュメント](https://docs.microsoft.com/hololens/security-adminless-os#device-owner)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7197c-278">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](https://docs.microsoft.com/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="7197c-279">考えられる解決策:</span><span class="sxs-lookup"><span data-stu-id="7197c-279">Possible solutions include:</span></span>

* <span data-ttu-id="7197c-280">デバイスを他のユーザーまたは開発者に渡す前に、デバイス所有者に開発者モードをオンにさせます</span><span class="sxs-lookup"><span data-stu-id="7197c-280">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="7197c-281">IT/MDM 管理者が特定のデバイスまたは開発者のデバイス グループに対して CSP [ポリシー ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) を有効にすることを提案します。</span><span class="sxs-lookup"><span data-stu-id="7197c-281">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="7197c-282">このポリシーは、[プロビジョニング パッケージ](https://docs.microsoft.com/hololens/hololens-provisioning)を使うか、[HoloLens デバイス用 MDM](https://docs.microsoft.com/hololens/hololens-mdm-configure) 経由で設定できます。</span><span class="sxs-lookup"><span data-stu-id="7197c-282">This policy can be set by [Provisioning Packages](https://docs.microsoft.com/hololens/hololens-provisioning) or via [MDM for HoloLens devices](https://docs.microsoft.com/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="7197c-283">[Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery) を使用します</span><span class="sxs-lookup"><span data-stu-id="7197c-283">Using the [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="7197c-284">デバイス管理の詳細については、 **[HoloLens デバイス管理](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** の概要を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7197c-284">You can learn more about device management in the **[HoloLens device management](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** overview.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="7197c-285">イマーシブ (VR) ヘッドセットの要件</span><span class="sxs-lookup"><span data-stu-id="7197c-285">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="7197c-286">以下のガイドラインは、イマーシブ (VR) ヘッドセットの *開発用 PC* に対する現在の最小かつ推奨仕様であり、定期的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="7197c-286">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="7197c-287">この仕様を、[PC ハードウェア互換性最小ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)と間違えないようにしてください。このガイドラインは、イマーシブ (VR) ヘッドセットのアプリまたはゲームの対象となる *コンシューマー PC の仕様* について説明するものです。</span><span class="sxs-lookup"><span data-stu-id="7197c-287">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="7197c-288">イマーシブ ヘッドセット開発用 PC にフルサイズの HDMI および/または USB 3.0 ポートがない場合、ヘッドセットを接続するための[アダプター](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)が必要になります。</span><span class="sxs-lookup"><span data-stu-id="7197c-288">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="7197c-289">一部のハードウェア構成、特にハイブリッド グラフィックスを搭載したノートブックなどには、現在[既知の問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)があります。</span><span class="sxs-lookup"><span data-stu-id="7197c-289">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="7197c-290">最小</span><span class="sxs-lookup"><span data-stu-id="7197c-290">Minimum</span></span></th><th> <span data-ttu-id="7197c-291">推奨</span><span class="sxs-lookup"><span data-stu-id="7197c-291">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="7197c-292">プロセッサ</span><span class="sxs-lookup"><span data-stu-id="7197c-292">Processor</span></span></td><td> <span data-ttu-id="7197c-293"><b>ノートブック:</b>Intel Mobile Core i5 第 7 世代 CPU、ハイパー スレッディング対応デュアルコア <b>デスクトップ:</b>Intel Desktop i5 第 6 世代 CPU、ハイパー スレッディング対応デュアルコア<b>または</b> AMD FX4350 4.2GHz クワッドコア相当</span><span class="sxs-lookup"><span data-stu-id="7197c-293"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="7197c-294"><b>デスクトップ:</b>Intel Desktop i7 第 6 世代 (6 コア) <b>または</b> AMD Ryzen 5 1600 (6 コア、12 スレッド)</span><span class="sxs-lookup"><span data-stu-id="7197c-294"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-295">GPU</span><span class="sxs-lookup"><span data-stu-id="7197c-295">GPU</span></span></td><td> <span data-ttu-id="7197c-296"><b>ノートブック:</b>NVIDIA GTX 965M、AMD RX 460M (2 GB) 相当またはそれ以上の DX12 対応 GPU <b>デスクトップ:</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="7197c-296"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="7197c-297"><b>デスクトップ:</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="7197c-297"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-298">GPU ドライバー WDDM バージョン</span><span class="sxs-lookup"><span data-stu-id="7197c-298">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="7197c-299">WDDM 2.2 ドライバー</span><span class="sxs-lookup"><span data-stu-id="7197c-299">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-300">熱設計電力</span><span class="sxs-lookup"><span data-stu-id="7197c-300">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="7197c-301">15 W 以上</span><span class="sxs-lookup"><span data-stu-id="7197c-301">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-302">グラフィックス表示ポート</span><span class="sxs-lookup"><span data-stu-id="7197c-302">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="7197c-303">ヘッドセット用の使用可能なグラフィックス ディスプレイ ポート (60 Hz ヘッドセットの場合は HDMI 1.4 または DisplayPort 1.2、90 Hz ヘッドセットの場合は HDMI 2.0 または DisplayPort 1.2) x 1</span><span class="sxs-lookup"><span data-stu-id="7197c-303">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-304">画面の解像度</span><span class="sxs-lookup"><span data-stu-id="7197c-304">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="7197c-305">解像度:SVGA (800 x 600) 以上のビットの深度:1 ピクセルあたり 32 ビット色</span><span class="sxs-lookup"><span data-stu-id="7197c-305">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-306">メモリ</span><span class="sxs-lookup"><span data-stu-id="7197c-306">Memory</span></span></td><td> <span data-ttu-id="7197c-307">8&#160;GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="7197c-307">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="7197c-308">16 GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="7197c-308">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-309">記憶域</span><span class="sxs-lookup"><span data-stu-id="7197c-309">Storage</span></span></td><td colspan="2"> <span data-ttu-id="7197c-310">&gt;10 GB の追加の空き領域</span><span class="sxs-lookup"><span data-stu-id="7197c-310">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-311">USB ポート</span><span class="sxs-lookup"><span data-stu-id="7197c-311">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="7197c-312">ヘッドセット (USB 3.0 Type-A) の使用可能な USB ポート x 1<b>メモ:USB は、最低 900 mA を給電する必要があります</b></span><span class="sxs-lookup"><span data-stu-id="7197c-312">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="7197c-313">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="7197c-313">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="7197c-314">Bluetooth 4.0 (アクセサリ接続用)</span><span class="sxs-lookup"><span data-stu-id="7197c-314">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="7197c-315">MRTK を使用したネイティブ開発を初めて行う場合は、整理されたネイティブ開発体験に従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7197c-315">If you're new to Native development with MRTK, we recommend following our curated Native development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7197c-316">ネイティブの体験を開始する</span><span class="sxs-lookup"><span data-stu-id="7197c-316">Start your Native journey</span></span>](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="7197c-317">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="7197c-317">Next Development Checkpoint</span></span>

<span data-ttu-id="7197c-318">私たちが用意したネイティブ開発チェックポイント体験に従っている場合、次のタスクは HoloLens 2 の開発環境を構成することです。</span><span class="sxs-lookup"><span data-stu-id="7197c-318">If you're following the Native development checkpoint journey we've laid out, your next task is to configure your development environment for HoloLens 2.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7197c-319">HoloLens 2 の設定</span><span class="sxs-lookup"><span data-stu-id="7197c-319">Setup for HoloLens 2</span></span>](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

<span data-ttu-id="7197c-320">いつでも[開発チェックポイント](../native/directx-development-overview.md#1-getting-started)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="7197c-320">You can always go back to the [Native development checkpoints](../native/directx-development-overview.md#1-getting-started) at any time.</span></span>
