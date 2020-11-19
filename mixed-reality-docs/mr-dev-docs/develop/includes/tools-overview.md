---
ms.openlocfilehash: cd6541dd651573f31ddc2e2a388be53394059c5f
ms.sourcegitcommit: f459c7deb254409fd5db3967bcc875bcbc367e77
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94482422"
---
# <a name="unity"></a>[<span data-ttu-id="66951-101">Unity</span><span class="sxs-lookup"><span data-stu-id="66951-101">Unity</span></span>](#tab/unity)

![Unity のロゴ バナー](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a><span data-ttu-id="66951-103">1.最新バージョンをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="66951-103">1. Download the latest version</span></span>

<span data-ttu-id="66951-104">新しいプロジェクトを開始する際に使用する最適なバージョンとして、[Unity LTS (長期サポート)](https://unity3d.com/unity/qa/lts-releases) ストリームをお勧めします。最新の安定した修正プログラムを取得するには最新リビジョンに更新します。</span><span class="sxs-lookup"><span data-stu-id="66951-104">We recommend the [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) stream as the best version to use when starting new projects, updating to its latest revision to pick up the latest stable fixes.</span></span>
* <span data-ttu-id="66951-105">現在は、**Unity 2019** を使用することをお勧めしています。これは、以下の MRTK v2 に必要な LTS ビルドです。</span><span class="sxs-lookup"><span data-stu-id="66951-105">The current recommendation is to use **Unity 2019**, which is the LTS build required for MRTK v2 below.</span></span>
* <span data-ttu-id="66951-106">特定の理由から別のバージョンの Unity を使用する必要がある場合、Unity では異なるバージョンの side-by-side インストールをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="66951-106">If you need to use a different version of Unity for specific reasons, Unity supports side-by-side installs of different versions.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="66951-107">2.Mixed Reality Toolkit (MRTK) をインポートする</span><span class="sxs-lookup"><span data-stu-id="66951-107">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="66951-109">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) は、Mixed Reality アプリケーション向けのオープンソースのクロスプラットフォーム開発キットです。</span><span class="sxs-lookup"><span data-stu-id="66951-109">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="66951-110">MRTK には、空間でのインタラクションのための、クロスプラットフォームの入力システム、基本コンポーネント、共通の構成要素が備わっています。</span><span class="sxs-lookup"><span data-stu-id="66951-110">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="66951-111">このツールキットは、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォームをターゲットとしたアプリケーションの開発を加速することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="66951-111">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="66951-112">インストールについては、整理された [Unity 開発体験](../unity/unity-development-overview.md)の[「はじめに」セクション](../unity/unity-development-overview.md#1-getting-started)を完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="66951-112">For installation, we recommend completing the [Getting Started section](../unity/unity-development-overview.md#1-getting-started) of our curated [Unity development journey](../unity/unity-development-overview.md).</span></span> <span data-ttu-id="66951-113">既に Unity 開発体験に従っている読者は、以下にリストされている残りの設定手順を完了し、[HoloLens 2 入門チュートリアル](../unity/tutorials/mr-learning-base-01.md)に進んでください。</span><span class="sxs-lookup"><span data-stu-id="66951-113">If you're already following the Unity development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unity/tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="66951-114">インストール手順では MRTK と Unity リリースの最新の安定した組み合わせである **MRTK 2.4.0** と **Unity 2019.3.15** を対象としていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="66951-114">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.4.0** and **Unity 2019.3.15**.</span></span>

> [!NOTE]
> <span data-ttu-id="66951-115">Unity 用の MRTK を使用しない場合は、すべての対話式操作と動作のスクリプトを開発者が自分で作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66951-115">If you don't want to use MRTK for Unity, you'll need to script all interactions and behaviors yourself.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="66951-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity バナー](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="66951-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="66951-117">**Mixed Reality Toolkit-Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="66951-117">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a><span data-ttu-id="66951-118">その他のツール (省略可能)</span><span class="sxs-lookup"><span data-stu-id="66951-118">Other tools [optional]</span></span>
* <span data-ttu-id="66951-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - HoloLens やイマーシブ (VR) ヘッドセットで直接動作しない可能性があるコード ビットとコンポーネントですが、これらを組み合わせることで、Windows Mixed Reality をターゲットとしたエクスペリエンスを構築します。</span><span class="sxs-lookup"><span data-stu-id="66951-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="66951-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - 共有スクリプトとコンポーネントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="66951-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="66951-121">3.Mixed Reality 開発用 PC を設定する</span><span class="sxs-lookup"><span data-stu-id="66951-121">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="66951-122">Windows 10 SDK は、Windows 10 オペレーティング システムでの使用に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="66951-122">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="66951-123">この SDK は、Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 でもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="66951-123">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="66951-124">以前のオペレーティング システムでは、一部のツールがサポートされないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="66951-124">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="66951-125">HoloLens 用アプリ、VR イマーシブ ヘッドセット用アプリ、またはこれらの両方に使用できるアプリを開発して展開できます。</span><span class="sxs-lookup"><span data-stu-id="66951-125">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="66951-126">必要に応じて、以下の要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="66951-126">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="66951-127">HoloLens の開発の場合</span><span class="sxs-lookup"><span data-stu-id="66951-127">For HoloLens development</span></span>

<span data-ttu-id="66951-128">開発用の PC を HoloLens の開発用に設定するときは、<a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> と <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> の両方のシステム要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="66951-128">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="66951-129">HoloLens デバイスでアプリを実行するには、[Windows デバイス ポータルのセットアップ手順](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="66951-129">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="66951-130">[HoloLens エミュレーター](../platform-capabilities-and-apis/using-the-hololens-emulator.md)を使用する予定の場合は、お使いの PC が [HoloLens エミュレーターのシステム要件](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)も満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66951-130">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="66951-131">HoloLens エミュレーターを開始するには、「[Using the HoloLens emulator (HoloLens エミュレーターを使用する)](../platform-capabilities-and-apis/using-the-hololens-emulator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66951-131">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="66951-132">HoloLens と Windows Mixed Reality イマーシブ (VR) ヘッドセットの両方を対象とした開発を予定している場合は、以下のセクションに記載のシステムの推奨事項と要件をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="66951-132">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="66951-133">HoloLens のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="66951-133">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="66951-134">開発者モードの設定がグレー表示される</span><span class="sxs-lookup"><span data-stu-id="66951-134">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="66951-135">デバイスで開発者モードを有効にする際に問題が発生する場合は、自身が[デバイスの所有者](https://docs.microsoft.com/hololens/security-adminless-os)ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="66951-135">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](https://docs.microsoft.com/hololens/security-adminless-os).</span></span> <span data-ttu-id="66951-136">マルチユーザー モードでは、最初にデバイスを使用するユーザーがデバイスの所有者であり、それ以降のユーザーには、開発者モードまたはその他の構成の変更を有効にするために必要なアクセス許可は付与されません。</span><span class="sxs-lookup"><span data-stu-id="66951-136">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="66951-137">ただし、最初のユーザーがオートパイロット環境にいるためデバイスの所有者ではないという例外があります。詳しくは、[HoloLens のセキュリティに関するドキュメント](https://docs.microsoft.com/hololens/security-adminless-os#device-owner)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66951-137">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](https://docs.microsoft.com/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="66951-138">考えられる解決策:</span><span class="sxs-lookup"><span data-stu-id="66951-138">Possible solutions include:</span></span>

* <span data-ttu-id="66951-139">デバイスを他のユーザーまたは開発者に渡す前に、デバイス所有者に開発者モードをオンにさせます</span><span class="sxs-lookup"><span data-stu-id="66951-139">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="66951-140">IT/MDM 管理者が特定のデバイスまたは開発者のデバイス グループに対して CSP [ポリシー ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) を有効にすることを提案します。</span><span class="sxs-lookup"><span data-stu-id="66951-140">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="66951-141">このポリシーは、[プロビジョニング パッケージ](https://docs.microsoft.com/hololens/hololens-provisioning)を使うか、[HoloLens デバイス用 MDM](https://docs.microsoft.com/hololens/hololens-mdm-configure) 経由で設定できます。</span><span class="sxs-lookup"><span data-stu-id="66951-141">This policy can be set by [Provisioning Packages](https://docs.microsoft.com/hololens/hololens-provisioning) or via [MDM for HoloLens devices](https://docs.microsoft.com/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="66951-142">[Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery) を使用します</span><span class="sxs-lookup"><span data-stu-id="66951-142">Using the [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="66951-143">デバイス管理の詳細については、 **[HoloLens デバイス管理](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** の概要を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66951-143">You can learn more about device management in the **[HoloLens device management](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="66951-144">USB 経由で展開できない</span><span class="sxs-lookup"><span data-stu-id="66951-144">I can't deploy over USB</span></span>

<span data-ttu-id="66951-145">USB 経由で直接アプリケーションを展開できない場合は、上記のすべてのインストール要件を満たしていることを確認し、[ステップバイステップ チュートリアル](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2)に従ってください。</span><span class="sxs-lookup"><span data-stu-id="66951-145">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="66951-146">イマーシブ (VR) ヘッドセットの要件</span><span class="sxs-lookup"><span data-stu-id="66951-146">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="66951-147">以下のガイドラインは、イマーシブ (VR) ヘッドセットの *開発用 PC* に対する現在の最小かつ推奨仕様であり、定期的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="66951-147">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="66951-148">この仕様を、[PC ハードウェア互換性最小ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)と間違えないようにしてください。このガイドラインは、イマーシブ (VR) ヘッドセットのアプリまたはゲームの対象となる *コンシューマー PC の仕様* について説明するものです。</span><span class="sxs-lookup"><span data-stu-id="66951-148">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="66951-149">**Reverb G2** ヘッドセットを使用している場合は、**Microsoft-Valve OpenXR** プラグインをダウンロードします (TODO://必要なリンク)。</span><span class="sxs-lookup"><span data-stu-id="66951-149">If you're using a **Reverb G2** headset, download the **Microsoft-Valve OpenXR** plugin (TODO: // Need link).</span></span>

<span data-ttu-id="66951-150">イマーシブ ヘッドセット開発用 PC にフルサイズの HDMI および/または USB 3.0 ポートがない場合、ヘッドセットを接続するための[アダプター](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)が必要になります。</span><span class="sxs-lookup"><span data-stu-id="66951-150">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="66951-151">一部のハードウェア構成、特にハイブリッド グラフィックスを搭載したノートブックなどには、現在[既知の問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)があります。</span><span class="sxs-lookup"><span data-stu-id="66951-151">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="66951-152">最小</span><span class="sxs-lookup"><span data-stu-id="66951-152">Minimum</span></span></th><th> <span data-ttu-id="66951-153">推奨</span><span class="sxs-lookup"><span data-stu-id="66951-153">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="66951-154">プロセッサ</span><span class="sxs-lookup"><span data-stu-id="66951-154">Processor</span></span></td><td> <span data-ttu-id="66951-155"><b>ノートブック:</b>Intel Mobile Core i5 第 7 世代 CPU、ハイパー スレッディング対応デュアルコア <b>デスクトップ:</b>Intel Desktop i5 第 6 世代 CPU、ハイパー スレッディング対応デュアルコア<b>または</b> AMD FX4350 4.2GHz クワッドコア相当</span><span class="sxs-lookup"><span data-stu-id="66951-155"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="66951-156"><b>デスクトップ:</b>Intel Desktop i7 第 6 世代 (6 コア) <b>または</b> AMD Ryzen 5 1600 (6 コア、12 スレッド)</span><span class="sxs-lookup"><span data-stu-id="66951-156"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-157">GPU</span><span class="sxs-lookup"><span data-stu-id="66951-157">GPU</span></span></td><td> <span data-ttu-id="66951-158"><b>ノートブック:</b>NVIDIA GTX 965M、AMD RX 460M (2 GB) 相当またはそれ以上の DX12 対応 GPU <b>デスクトップ:</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="66951-158"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="66951-159"><b>デスクトップ:</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="66951-159"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-160">GPU ドライバー WDDM バージョン</span><span class="sxs-lookup"><span data-stu-id="66951-160">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="66951-161">WDDM 2.2 ドライバー</span><span class="sxs-lookup"><span data-stu-id="66951-161">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-162">熱設計電力</span><span class="sxs-lookup"><span data-stu-id="66951-162">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="66951-163">15 W 以上</span><span class="sxs-lookup"><span data-stu-id="66951-163">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-164">グラフィックス表示ポート</span><span class="sxs-lookup"><span data-stu-id="66951-164">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="66951-165">ヘッドセット用の使用可能なグラフィックス ディスプレイ ポート (60 Hz ヘッドセットの場合は HDMI 1.4 または DisplayPort 1.2、90 Hz ヘッドセットの場合は HDMI 2.0 または DisplayPort 1.2) x 1</span><span class="sxs-lookup"><span data-stu-id="66951-165">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-166">画面の解像度</span><span class="sxs-lookup"><span data-stu-id="66951-166">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="66951-167">解像度:SVGA (800 x 600) 以上のビットの深度:1 ピクセルあたり 32 ビット色</span><span class="sxs-lookup"><span data-stu-id="66951-167">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-168">メモリ</span><span class="sxs-lookup"><span data-stu-id="66951-168">Memory</span></span></td><td> <span data-ttu-id="66951-169">8&#160;GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="66951-169">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="66951-170">16 GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="66951-170">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-171">記憶域</span><span class="sxs-lookup"><span data-stu-id="66951-171">Storage</span></span></td><td colspan="2"> <span data-ttu-id="66951-172">&gt;10 GB の追加の空き領域</span><span class="sxs-lookup"><span data-stu-id="66951-172">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-173">USB ポート</span><span class="sxs-lookup"><span data-stu-id="66951-173">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="66951-174">ヘッドセット (USB 3.0 Type-A) の使用可能な USB ポート x 1<b>メモ:USB は、最低 900 mA を給電する必要があります</b></span><span class="sxs-lookup"><span data-stu-id="66951-174">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-175">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="66951-175">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="66951-176">Bluetooth 4.0 (アクセサリ接続用)</span><span class="sxs-lookup"><span data-stu-id="66951-176">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="66951-177">Unity を使用した MRTK 開発を初めて行う場合は、整理された Unity 開発体験に従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="66951-177">If you're new to MRTK development with Unity, we recommend following our curated Unity development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="66951-178">Unity の体験を開始する</span><span class="sxs-lookup"><span data-stu-id="66951-178">Start your Unity journey</span></span>](../unity/unity-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="66951-179">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="66951-179">Next Development Checkpoint</span></span>

<span data-ttu-id="66951-180">私たちが用意した Unity 開発チェックポイント体験に従っている場合、次のタスクは HoloLens 2 チュートリアル シリーズを実行することです。</span><span class="sxs-lookup"><span data-stu-id="66951-180">If you're following the Unity development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="66951-181">HoloLens 2 チュートリアル シリーズ</span><span class="sxs-lookup"><span data-stu-id="66951-181">HoloLens 2 tutorial series</span></span>](../unity/tutorials/mr-learning-base-01.md)

<span data-ttu-id="66951-182">いつでも [Unity 開発チェックポイント](../unity/unity-development-overview.md#1-getting-started)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="66951-182">You can always go back to the [Unity development checkpoints](../unity/unity-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="unreal"></a>[<span data-ttu-id="66951-183">Unreal</span><span class="sxs-lookup"><span data-stu-id="66951-183">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="66951-185">1.最新バージョンをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="66951-185">1. Download the latest version</span></span>

<span data-ttu-id="66951-186">組み込みの HoloLens サポートを最大限に活用するため、[Unreal Engine バージョン 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 以降をインストールすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="66951-186">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="66951-187">2.Mixed Reality Toolkit (MRTK) をインポートする</span><span class="sxs-lookup"><span data-stu-id="66951-187">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="66951-189">Mixed Reality Toolkit (MRTK) は、Mixed Reality アプリケーション向けのオープン ソースのクロスプラットフォーム開発キットです。</span><span class="sxs-lookup"><span data-stu-id="66951-189">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="66951-190">MRTK には、空間でのインタラクションのための、クロスプラットフォームの入力システム、基本コンポーネント、共通の構成要素が備わっています。</span><span class="sxs-lookup"><span data-stu-id="66951-190">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="66951-191">このツールキットは、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォームをターゲットとしたアプリケーションの開発を加速することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="66951-191">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="66951-192">インストールについては、整理された [ 開発体験](../unreal/unreal-development-overview.md)の[「はじめに」セクション](../unreal/unreal-development-overview.md#1-getting-started)を完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="66951-192">For installation, we recommend completing the [Getting Started section](../unreal/unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](../unreal/unreal-development-overview.md).</span></span> <span data-ttu-id="66951-193">既に Unreal 開発体験に従っている読者は、以下にリストされている残りの設定手順を完了し、[HoloLens 2 入門チュートリアル](../unreal/tutorials/unreal-uxt-ch1.md)に進んでください。</span><span class="sxs-lookup"><span data-stu-id="66951-193">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unreal/tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="66951-194"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity のロゴ画像](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="66951-194"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="66951-195">**Mixed Reality Toolkit-Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="66951-195">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="66951-196">Unreal 用の MRTK を使用しない場合は、すべての対話式操作と動作のスクリプトを開発者が自分で作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66951-196">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="66951-197">その他のツール (省略可能)</span><span class="sxs-lookup"><span data-stu-id="66951-197">Other tools [optional]</span></span>
* <span data-ttu-id="66951-198"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - HoloLens やイマーシブ (VR) ヘッドセットで直接動作しない可能性があるコード ビットとコンポーネントですが、これらを組み合わせることで、Windows Mixed Reality をターゲットとしたエクスペリエンスを構築します。</span><span class="sxs-lookup"><span data-stu-id="66951-198"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="66951-199"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - 共有スクリプトとコンポーネントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="66951-199"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="66951-200">3.Mixed Reality 開発用 PC を設定する</span><span class="sxs-lookup"><span data-stu-id="66951-200">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="66951-201">Windows 10 SDK は、Windows 10 オペレーティング システムでの使用に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="66951-201">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="66951-202">この SDK は、Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 でもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="66951-202">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="66951-203">以前のオペレーティング システムでは、一部のツールがサポートされないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="66951-203">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="66951-204">HoloLens 用アプリ、VR イマーシブ ヘッドセット用アプリ、またはこれらの両方に使用できるアプリを開発して展開できます。</span><span class="sxs-lookup"><span data-stu-id="66951-204">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="66951-205">必要に応じて、以下の要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="66951-205">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="66951-206">HoloLens の開発の場合</span><span class="sxs-lookup"><span data-stu-id="66951-206">For HoloLens development</span></span>

<span data-ttu-id="66951-207">HoloLens の開発用に開発用 PC を設定するときは、[Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) と <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> の両方のシステム要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="66951-207">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="66951-208">HoloLens デバイスでアプリを実行するには、[Windows デバイス ポータルのセットアップ手順](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="66951-208">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="66951-209">[HoloLens エミュレーター](../platform-capabilities-and-apis/using-the-hololens-emulator.md)を使用する予定の場合は、お使いの PC が [HoloLens エミュレーターのシステム要件](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)も満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66951-209">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="66951-210">HoloLens と Windows Mixed Reality イマーシブ (VR) ヘッドセットの両方を対象とした開発を予定している場合は、以下のセクションに記載のシステムの推奨事項と要件をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="66951-210">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="66951-211">HoloLens のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="66951-211">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="66951-212">開発者モードの設定がグレー表示される</span><span class="sxs-lookup"><span data-stu-id="66951-212">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="66951-213">デバイスで開発者モードを有効にする際に問題が発生する場合は、自身が[デバイスの所有者](https://docs.microsoft.com/hololens/security-adminless-os)ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="66951-213">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](https://docs.microsoft.com/hololens/security-adminless-os).</span></span> <span data-ttu-id="66951-214">マルチユーザー モードでは、最初にデバイスを使用するユーザーがデバイスの所有者であり、それ以降のユーザーには、開発者モードまたはその他の構成の変更を有効にするために必要なアクセス許可は付与されません。</span><span class="sxs-lookup"><span data-stu-id="66951-214">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="66951-215">ただし、最初のユーザーがオートパイロット環境にいるためデバイスの所有者ではないという例外があります。詳しくは、[HoloLens のセキュリティに関するドキュメント](https://docs.microsoft.com/hololens/security-adminless-os#device-owner)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66951-215">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](https://docs.microsoft.com/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="66951-216">考えられる解決策:</span><span class="sxs-lookup"><span data-stu-id="66951-216">Possible solutions include:</span></span>

* <span data-ttu-id="66951-217">デバイスを他のユーザーまたは開発者に渡す前に、デバイス所有者に開発者モードをオンにさせます</span><span class="sxs-lookup"><span data-stu-id="66951-217">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="66951-218">IT/MDM 管理者が特定のデバイスまたは開発者のデバイス グループに対して CSP [ポリシー ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) を有効にすることを提案します。</span><span class="sxs-lookup"><span data-stu-id="66951-218">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="66951-219">このポリシーは、[プロビジョニング パッケージ](https://docs.microsoft.com/hololens/hololens-provisioning)を使うか、[HoloLens デバイス用 MDM](https://docs.microsoft.com/hololens/hololens-mdm-configure) 経由で設定できます。</span><span class="sxs-lookup"><span data-stu-id="66951-219">This policy can be set by [Provisioning Packages](https://docs.microsoft.com/hololens/hololens-provisioning) or via [MDM for HoloLens devices](https://docs.microsoft.com/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="66951-220">[Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery) を使用します</span><span class="sxs-lookup"><span data-stu-id="66951-220">Using the [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="66951-221">デバイス管理の詳細については、 **[HoloLens デバイス管理](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** の概要を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66951-221">You can learn more about device management in the **[HoloLens device management](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="66951-222">USB 経由で展開できない</span><span class="sxs-lookup"><span data-stu-id="66951-222">I can't deploy over USB</span></span>

<span data-ttu-id="66951-223">USB 経由で直接アプリケーションを展開できない場合は、上記のすべてのインストール要件を満たしていることを確認し、[ステップバイステップ チュートリアル](../unreal/tutorials/unreal-uxt-ch6.md)に従ってください。</span><span class="sxs-lookup"><span data-stu-id="66951-223">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unreal/tutorials/unreal-uxt-ch6.md).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="66951-224">イマーシブ (VR) ヘッドセットの要件</span><span class="sxs-lookup"><span data-stu-id="66951-224">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="66951-225">以下のガイドラインは、イマーシブ (VR) ヘッドセットの *開発用 PC* に対する現在の最小かつ推奨仕様であり、定期的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="66951-225">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="66951-226">この仕様を、[PC ハードウェア互換性最小ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)と間違えないようにしてください。このガイドラインは、イマーシブ (VR) ヘッドセットのアプリまたはゲームの対象となる *コンシューマー PC の仕様* について説明するものです。</span><span class="sxs-lookup"><span data-stu-id="66951-226">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="66951-227">**Reverb G2** ヘッドセットを使用している場合は、**Microsoft-Valve OpenXR** プラグインをダウンロードします (TODO://必要なリンク)。</span><span class="sxs-lookup"><span data-stu-id="66951-227">If you're using a **Reverb G2** headset, download the **Microsoft-Valve OpenXR** plugin (TODO: // Need link).</span></span>

<span data-ttu-id="66951-228">イマーシブ ヘッドセット開発用 PC にフルサイズの HDMI および/または USB 3.0 ポートがない場合、ヘッドセットを接続するための[アダプター](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)が必要になります。</span><span class="sxs-lookup"><span data-stu-id="66951-228">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="66951-229">一部のハードウェア構成、特にハイブリッド グラフィックスを搭載したノートブックなどには、現在[既知の問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)があります。</span><span class="sxs-lookup"><span data-stu-id="66951-229">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="66951-230">最小</span><span class="sxs-lookup"><span data-stu-id="66951-230">Minimum</span></span></th><th> <span data-ttu-id="66951-231">推奨</span><span class="sxs-lookup"><span data-stu-id="66951-231">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="66951-232">プロセッサ</span><span class="sxs-lookup"><span data-stu-id="66951-232">Processor</span></span></td><td> <span data-ttu-id="66951-233"><b>ノートブック:</b>Intel Mobile Core i5 第 7 世代 CPU、ハイパー スレッディング対応デュアルコア <b>デスクトップ:</b>Intel Desktop i5 第 6 世代 CPU、ハイパー スレッディング対応デュアルコア<b>または</b> AMD FX4350 4.2GHz クワッドコア相当</span><span class="sxs-lookup"><span data-stu-id="66951-233"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="66951-234"><b>デスクトップ:</b>Intel Desktop i7 第 6 世代 (6 コア) <b>または</b> AMD Ryzen 5 1600 (6 コア、12 スレッド)</span><span class="sxs-lookup"><span data-stu-id="66951-234"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-235">GPU</span><span class="sxs-lookup"><span data-stu-id="66951-235">GPU</span></span></td><td> <span data-ttu-id="66951-236"><b>ノートブック:</b>NVIDIA GTX 965M、AMD RX 460M (2 GB) 相当またはそれ以上の DX12 対応 GPU <b>デスクトップ:</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="66951-236"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="66951-237"><b>デスクトップ:</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="66951-237"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-238">GPU ドライバー WDDM バージョン</span><span class="sxs-lookup"><span data-stu-id="66951-238">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="66951-239">WDDM 2.2 ドライバー</span><span class="sxs-lookup"><span data-stu-id="66951-239">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-240">熱設計電力</span><span class="sxs-lookup"><span data-stu-id="66951-240">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="66951-241">15 W 以上</span><span class="sxs-lookup"><span data-stu-id="66951-241">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-242">グラフィックス表示ポート</span><span class="sxs-lookup"><span data-stu-id="66951-242">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="66951-243">ヘッドセット用の使用可能なグラフィックス ディスプレイ ポート (60 Hz ヘッドセットの場合は HDMI 1.4 または DisplayPort 1.2、90 Hz ヘッドセットの場合は HDMI 2.0 または DisplayPort 1.2) x 1</span><span class="sxs-lookup"><span data-stu-id="66951-243">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-244">画面の解像度</span><span class="sxs-lookup"><span data-stu-id="66951-244">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="66951-245">解像度:SVGA (800 x 600) 以上のビットの深度:1 ピクセルあたり 32 ビット色</span><span class="sxs-lookup"><span data-stu-id="66951-245">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-246">メモリ</span><span class="sxs-lookup"><span data-stu-id="66951-246">Memory</span></span></td><td> <span data-ttu-id="66951-247">8&#160;GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="66951-247">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="66951-248">16 GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="66951-248">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-249">記憶域</span><span class="sxs-lookup"><span data-stu-id="66951-249">Storage</span></span></td><td colspan="2"> <span data-ttu-id="66951-250">&gt;10 GB の追加の空き領域</span><span class="sxs-lookup"><span data-stu-id="66951-250">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-251">USB ポート</span><span class="sxs-lookup"><span data-stu-id="66951-251">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="66951-252">ヘッドセット (USB 3.0 Type-A) の使用可能な USB ポート x 1<b>メモ:USB は、最低 900 mA を給電する必要があります</b></span><span class="sxs-lookup"><span data-stu-id="66951-252">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-253">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="66951-253">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="66951-254">Bluetooth 4.0 (アクセサリ接続用)</span><span class="sxs-lookup"><span data-stu-id="66951-254">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="66951-255">Unreal を使用した MRTK 開発を初めて行う場合は、整理された Unreal 開発体験に従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="66951-255">If you're new to MRTK development with Unreal, we recommend following our curated Unreal development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="66951-256">Unreal の体験を開始する</span><span class="sxs-lookup"><span data-stu-id="66951-256">Start your Unreal journey</span></span>](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="66951-257">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="66951-257">Next Development Checkpoint</span></span>

<span data-ttu-id="66951-258">私たちが用意した Unreal 開発チェックポイント体験に従っている場合、次のタスクは HoloLens 2 チュートリアル シリーズを実行することです。</span><span class="sxs-lookup"><span data-stu-id="66951-258">If you're following the Unreal development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="66951-259">HoloLens 2 チュートリアル シリーズ</span><span class="sxs-lookup"><span data-stu-id="66951-259">HoloLens 2 tutorial series</span></span>](../unreal/tutorials/unreal-uxt-ch1.md)

<span data-ttu-id="66951-260">いつでも [Unreal 開発チェックポイント](../unreal/unreal-development-overview.md#1-getting-started)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="66951-260">You can always go back to the [Unreal development checkpoints](../unreal/unreal-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="native-openxr"></a>[<span data-ttu-id="66951-261">ネイティブ (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="66951-261">Native (OpenXR)</span></span>](#tab/native)

 ![ネイティブ アプリ開発](../images/native_logo_banner.png)

<span data-ttu-id="66951-263">ネイティブな OpenXR 開発では、エンジンをダウンロードする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="66951-263">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="66951-264">「[OpenXR の概要](../native/openxr-getting-started.md)」に、開発を開始するために必要なものがすべて記載されています。</span><span class="sxs-lookup"><span data-stu-id="66951-264">You can find everything you need to begin development in the [Getting started with OpenXR](../native/openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="66951-265">1.Mixed Reality 開発用 PC を設定する</span><span class="sxs-lookup"><span data-stu-id="66951-265">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="66951-266">Windows 10 SDK は、Windows 10 オペレーティング システムでの使用に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="66951-266">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="66951-267">この SDK は、Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 でもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="66951-267">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="66951-268">以前のオペレーティング システムでは、一部のツールがサポートされないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="66951-268">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="66951-269">HoloLens の開発の場合</span><span class="sxs-lookup"><span data-stu-id="66951-269">For HoloLens development</span></span>

<span data-ttu-id="66951-270">HoloLens の開発用に開発用 PC を設定するときは、<a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> のシステム要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="66951-270">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="66951-271">HoloLens デバイスでアプリを実行するには、[Windows デバイス ポータルのセットアップ手順](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="66951-271">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="66951-272">[HoloLens エミュレーター](../platform-capabilities-and-apis/using-the-hololens-emulator.md)を使用する予定の場合は、お使いの PC が [HoloLens エミュレーターのシステム要件](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)も満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66951-272">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="66951-273">HoloLens と Windows Mixed Reality イマーシブ (VR) ヘッドセットの両方を対象とした開発を予定している場合は、以下のセクションに記載のシステムの推奨事項と要件をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="66951-273">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="66951-274">HoloLens 用アプリ、VR イマーシブ ヘッドセット用アプリ、またはこれらの両方に使用できるアプリを開発して展開できます。</span><span class="sxs-lookup"><span data-stu-id="66951-274">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="66951-275">必要に応じて、以下の要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="66951-275">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="66951-276">HoloLens のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="66951-276">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="66951-277">開発者モードの設定がグレー表示される</span><span class="sxs-lookup"><span data-stu-id="66951-277">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="66951-278">デバイスで開発者モードを有効にする際に問題が発生する場合は、自身が[デバイスの所有者](https://docs.microsoft.com/hololens/security-adminless-os)ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="66951-278">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](https://docs.microsoft.com/hololens/security-adminless-os).</span></span> <span data-ttu-id="66951-279">マルチユーザー モードでは、最初にデバイスを使用するユーザーがデバイスの所有者であり、それ以降のユーザーには、開発者モードまたはその他の構成の変更を有効にするために必要なアクセス許可は付与されません。</span><span class="sxs-lookup"><span data-stu-id="66951-279">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="66951-280">ただし、最初のユーザーがオートパイロット環境にいるためデバイスの所有者ではないという例外があります。詳しくは、[HoloLens のセキュリティに関するドキュメント](https://docs.microsoft.com/hololens/security-adminless-os#device-owner)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66951-280">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](https://docs.microsoft.com/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="66951-281">考えられる解決策:</span><span class="sxs-lookup"><span data-stu-id="66951-281">Possible solutions include:</span></span>

* <span data-ttu-id="66951-282">デバイスを他のユーザーまたは開発者に渡す前に、デバイス所有者に開発者モードをオンにさせます</span><span class="sxs-lookup"><span data-stu-id="66951-282">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="66951-283">IT/MDM 管理者が特定のデバイスまたは開発者のデバイス グループに対して CSP [ポリシー ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) を有効にすることを提案します。</span><span class="sxs-lookup"><span data-stu-id="66951-283">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="66951-284">このポリシーは、[プロビジョニング パッケージ](https://docs.microsoft.com/hololens/hololens-provisioning)を使うか、[HoloLens デバイス用 MDM](https://docs.microsoft.com/hololens/hololens-mdm-configure) 経由で設定できます。</span><span class="sxs-lookup"><span data-stu-id="66951-284">This policy can be set by [Provisioning Packages](https://docs.microsoft.com/hololens/hololens-provisioning) or via [MDM for HoloLens devices](https://docs.microsoft.com/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="66951-285">[Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery) を使用します</span><span class="sxs-lookup"><span data-stu-id="66951-285">Using the [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="66951-286">デバイス管理の詳細については、 **[HoloLens デバイス管理](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** の概要を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66951-286">You can learn more about device management in the **[HoloLens device management](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** overview.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="66951-287">イマーシブ (VR) ヘッドセットの要件</span><span class="sxs-lookup"><span data-stu-id="66951-287">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="66951-288">以下のガイドラインは、イマーシブ (VR) ヘッドセットの *開発用 PC* に対する現在の最小かつ推奨仕様であり、定期的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="66951-288">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="66951-289">この仕様を、[PC ハードウェア互換性最小ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)と間違えないようにしてください。このガイドラインは、イマーシブ (VR) ヘッドセットのアプリまたはゲームの対象となる *コンシューマー PC の仕様* について説明するものです。</span><span class="sxs-lookup"><span data-stu-id="66951-289">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="66951-290">イマーシブ ヘッドセット開発用 PC にフルサイズの HDMI および/または USB 3.0 ポートがない場合、ヘッドセットを接続するための[アダプター](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)が必要になります。</span><span class="sxs-lookup"><span data-stu-id="66951-290">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="66951-291">一部のハードウェア構成、特にハイブリッド グラフィックスを搭載したノートブックなどには、現在[既知の問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)があります。</span><span class="sxs-lookup"><span data-stu-id="66951-291">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="66951-292">最小</span><span class="sxs-lookup"><span data-stu-id="66951-292">Minimum</span></span></th><th> <span data-ttu-id="66951-293">推奨</span><span class="sxs-lookup"><span data-stu-id="66951-293">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="66951-294">プロセッサ</span><span class="sxs-lookup"><span data-stu-id="66951-294">Processor</span></span></td><td> <span data-ttu-id="66951-295"><b>ノートブック:</b>Intel Mobile Core i5 第 7 世代 CPU、ハイパー スレッディング対応デュアルコア <b>デスクトップ:</b>Intel Desktop i5 第 6 世代 CPU、ハイパー スレッディング対応デュアルコア<b>または</b> AMD FX4350 4.2GHz クワッドコア相当</span><span class="sxs-lookup"><span data-stu-id="66951-295"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="66951-296"><b>デスクトップ:</b>Intel Desktop i7 第 6 世代 (6 コア) <b>または</b> AMD Ryzen 5 1600 (6 コア、12 スレッド)</span><span class="sxs-lookup"><span data-stu-id="66951-296"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-297">GPU</span><span class="sxs-lookup"><span data-stu-id="66951-297">GPU</span></span></td><td> <span data-ttu-id="66951-298"><b>ノートブック:</b>NVIDIA GTX 965M、AMD RX 460M (2 GB) 相当またはそれ以上の DX12 対応 GPU <b>デスクトップ:</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="66951-298"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="66951-299"><b>デスクトップ:</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="66951-299"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-300">GPU ドライバー WDDM バージョン</span><span class="sxs-lookup"><span data-stu-id="66951-300">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="66951-301">WDDM 2.2 ドライバー</span><span class="sxs-lookup"><span data-stu-id="66951-301">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-302">熱設計電力</span><span class="sxs-lookup"><span data-stu-id="66951-302">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="66951-303">15 W 以上</span><span class="sxs-lookup"><span data-stu-id="66951-303">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-304">グラフィックス表示ポート</span><span class="sxs-lookup"><span data-stu-id="66951-304">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="66951-305">ヘッドセット用の使用可能なグラフィックス ディスプレイ ポート (60 Hz ヘッドセットの場合は HDMI 1.4 または DisplayPort 1.2、90 Hz ヘッドセットの場合は HDMI 2.0 または DisplayPort 1.2) x 1</span><span class="sxs-lookup"><span data-stu-id="66951-305">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-306">画面の解像度</span><span class="sxs-lookup"><span data-stu-id="66951-306">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="66951-307">解像度:SVGA (800 x 600) 以上のビットの深度:1 ピクセルあたり 32 ビット色</span><span class="sxs-lookup"><span data-stu-id="66951-307">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-308">メモリ</span><span class="sxs-lookup"><span data-stu-id="66951-308">Memory</span></span></td><td> <span data-ttu-id="66951-309">8&#160;GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="66951-309">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="66951-310">16 GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="66951-310">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-311">記憶域</span><span class="sxs-lookup"><span data-stu-id="66951-311">Storage</span></span></td><td colspan="2"> <span data-ttu-id="66951-312">&gt;10 GB の追加の空き領域</span><span class="sxs-lookup"><span data-stu-id="66951-312">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-313">USB ポート</span><span class="sxs-lookup"><span data-stu-id="66951-313">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="66951-314">ヘッドセット (USB 3.0 Type-A) の使用可能な USB ポート x 1<b>メモ:USB は、最低 900 mA を給電する必要があります</b></span><span class="sxs-lookup"><span data-stu-id="66951-314">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="66951-315">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="66951-315">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="66951-316">Bluetooth 4.0 (アクセサリ接続用)</span><span class="sxs-lookup"><span data-stu-id="66951-316">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="66951-317">MRTK を使用したネイティブ開発を初めて行う場合は、整理されたネイティブ開発体験に従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="66951-317">If you're new to Native development with MRTK, we recommend following our curated Native development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="66951-318">ネイティブの体験を開始する</span><span class="sxs-lookup"><span data-stu-id="66951-318">Start your Native journey</span></span>](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="66951-319">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="66951-319">Next Development Checkpoint</span></span>

<span data-ttu-id="66951-320">私たちが用意したネイティブ開発チェックポイント体験に従っている場合、次のタスクは HoloLens 2 の開発環境を構成することです。</span><span class="sxs-lookup"><span data-stu-id="66951-320">If you're following the Native development checkpoint journey we've laid out, your next task is to configure your development environment for HoloLens 2.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="66951-321">HoloLens 2 の設定</span><span class="sxs-lookup"><span data-stu-id="66951-321">Setup for HoloLens 2</span></span>](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

<span data-ttu-id="66951-322">いつでも[開発チェックポイント](../native/directx-development-overview.md#1-getting-started)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="66951-322">You can always go back to the [Native development checkpoints](../native/directx-development-overview.md#1-getting-started) at any time.</span></span>
