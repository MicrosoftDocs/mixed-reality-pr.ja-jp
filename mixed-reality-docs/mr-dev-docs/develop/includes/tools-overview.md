---
ms.openlocfilehash: b6e75419ef9cdd4595e23e6217ab1b1762cd134e
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98605304"
---
# <a name="unity"></a>[<span data-ttu-id="e11cb-101">Unity</span><span class="sxs-lookup"><span data-stu-id="e11cb-101">Unity</span></span>](#tab/unity)

![Unity のロゴ バナー](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a><span data-ttu-id="e11cb-103">1.最新バージョンをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="e11cb-103">1. Download the latest version</span></span>

<span data-ttu-id="e11cb-104">新しいプロジェクトを開始する際に使用する最適なバージョンとして、[Unity LTS (長期サポート)](https://unity3d.com/unity/qa/lts-releases) ストリームをお勧めします。最新の安定した修正プログラムを取得するには最新リビジョンに更新します。</span><span class="sxs-lookup"><span data-stu-id="e11cb-104">We recommend the [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) stream as the best version to use when starting new projects, updating to its latest revision to pick up the latest stable fixes.</span></span>
* <span data-ttu-id="e11cb-105">現在は、**Unity 2019** を使用することをお勧めしています。これは、以下の MRTK v2 に必要な LTS ビルドです。</span><span class="sxs-lookup"><span data-stu-id="e11cb-105">The current recommendation is to use **Unity 2019**, which is the LTS build required for MRTK v2 below.</span></span>
* <span data-ttu-id="e11cb-106">特定の理由から別のバージョンの Unity を使用する必要がある場合、Unity では異なるバージョンの side-by-side インストールをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="e11cb-106">If you need to use a different version of Unity for specific reasons, Unity supports side-by-side installs of different versions.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="e11cb-107">2.Mixed Reality Toolkit (MRTK) をインポートする</span><span class="sxs-lookup"><span data-stu-id="e11cb-107">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="e11cb-109">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) は、Mixed Reality アプリケーション向けのオープンソースのクロスプラットフォーム開発キットです。</span><span class="sxs-lookup"><span data-stu-id="e11cb-109">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="e11cb-110">MRTK には、空間でのインタラクションのための、クロスプラットフォームの入力システム、基本コンポーネント、共通の構成要素が備わっています。</span><span class="sxs-lookup"><span data-stu-id="e11cb-110">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="e11cb-111">このツールキットは、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォームをターゲットとしたアプリケーションの開発を加速することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="e11cb-111">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="e11cb-112">インストールについては、整理された [HoloLens](../unity/unity-development-overview.md#1-getting-started) または [VR](../unity/unity-development-wmr-overview.md#1-getting-started) の開発体験の概要セクションを完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e11cb-112">For installation, we recommend completing the getting started section in our curated [HoloLens](../unity/unity-development-overview.md#1-getting-started) or [VR](../unity/unity-development-wmr-overview.md#1-getting-started) development journeys.</span></span> <span data-ttu-id="e11cb-113">既に HoloLens 用 Unity 開発体験に従っている場合は、以下の一覧で示されている残りの設定手順を完了し、[HoloLens 2 入門チュートリアル](../unity/tutorials/mr-learning-base-01.md)に進んでください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-113">If you're already following the Unity development for HoloLens journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unity/tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e11cb-114">インストール手順では MRTK と Unity リリースの最新の安定した組み合わせである **MRTK 2.4.0** と **Unity 2019.3.15** を対象としていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-114">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.4.0** and **Unity 2019.3.15**.</span></span>

> [!NOTE]
> <span data-ttu-id="e11cb-115">Unity 用の MRTK を使用しない場合は、すべての対話式操作と動作のスクリプトを開発者が自分で作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e11cb-115">If you don't want to use MRTK for Unity, you'll need to script all interactions and behaviors yourself.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="e11cb-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity バナー](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="e11cb-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="e11cb-117">**Mixed Reality Toolkit-Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="e11cb-117">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a><span data-ttu-id="e11cb-118">その他のツール (省略可能)</span><span class="sxs-lookup"><span data-stu-id="e11cb-118">Other tools [optional]</span></span>
* <span data-ttu-id="e11cb-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - HoloLens やイマーシブ (VR) ヘッドセットで直接動作しない可能性があるコード ビットとコンポーネントですが、これらを組み合わせることで、Windows Mixed Reality をターゲットとしたエクスペリエンスを構築します。</span><span class="sxs-lookup"><span data-stu-id="e11cb-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="e11cb-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - 共有スクリプトとコンポーネントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="e11cb-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="e11cb-121">3.Mixed Reality 開発用 PC を設定する</span><span class="sxs-lookup"><span data-stu-id="e11cb-121">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="e11cb-122">Windows 10 SDK は、Windows 10 オペレーティング システムでの使用に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="e11cb-122">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="e11cb-123">この SDK は、Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 でもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e11cb-123">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="e11cb-124">以前のオペレーティング システムでは、一部のツールがサポートされないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-124">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="e11cb-125">HoloLens 用アプリ、VR イマーシブ ヘッドセット用アプリ、またはこれらの両方に使用できるアプリを開発して展開できます。</span><span class="sxs-lookup"><span data-stu-id="e11cb-125">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="e11cb-126">必要に応じて、以下の要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-126">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="e11cb-127">HoloLens の開発の場合</span><span class="sxs-lookup"><span data-stu-id="e11cb-127">For HoloLens development</span></span>

<span data-ttu-id="e11cb-128">開発用の PC を HoloLens の開発用に設定するときは、<a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> と <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> の両方のシステム要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-128">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="e11cb-129">HoloLens デバイスでアプリを実行するには、[Windows デバイス ポータルのセットアップ手順](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="e11cb-129">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="e11cb-130">[HoloLens エミュレーター](../platform-capabilities-and-apis/using-the-hololens-emulator.md)を使用する予定の場合は、お使いの PC が [HoloLens エミュレーターのシステム要件](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)も満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e11cb-130">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="e11cb-131">HoloLens エミュレーターを開始するには、「[Using the HoloLens emulator (HoloLens エミュレーターを使用する)](../platform-capabilities-and-apis/using-the-hololens-emulator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-131">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="e11cb-132">HoloLens と Windows Mixed Reality イマーシブ (VR) ヘッドセットの両方を対象とした開発を予定している場合は、以下のセクションに記載のシステムの推奨事項と要件をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-132">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="e11cb-133">HoloLens のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="e11cb-133">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="e11cb-134">開発者モードの設定がグレー表示される</span><span class="sxs-lookup"><span data-stu-id="e11cb-134">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="e11cb-135">デバイスで開発者モードを有効にする際に問題が発生する場合は、自身が[デバイスの所有者](/hololens/security-adminless-os)ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e11cb-135">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="e11cb-136">マルチユーザー モードでは、最初にデバイスを使用するユーザーがデバイスの所有者であり、それ以降のユーザーには、開発者モードまたはその他の構成の変更を有効にするために必要なアクセス許可は付与されません。</span><span class="sxs-lookup"><span data-stu-id="e11cb-136">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="e11cb-137">ただし、最初のユーザーがオートパイロット環境にいるためデバイスの所有者ではないという例外があります。詳しくは、[HoloLens のセキュリティに関するドキュメント](/hololens/security-adminless-os#device-owner)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-137">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="e11cb-138">考えられる解決策:</span><span class="sxs-lookup"><span data-stu-id="e11cb-138">Possible solutions include:</span></span>

* <span data-ttu-id="e11cb-139">デバイスを他のユーザーまたは開発者に渡す前に、デバイス所有者に開発者モードをオンにさせます</span><span class="sxs-lookup"><span data-stu-id="e11cb-139">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="e11cb-140">IT/MDM 管理者が特定のデバイスまたは開発者のデバイス グループに対して CSP [ポリシー ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) を有効にすることを提案します。</span><span class="sxs-lookup"><span data-stu-id="e11cb-140">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="e11cb-141">このポリシーは、[プロビジョニング パッケージ](/hololens/hololens-provisioning)を使うか、[HoloLens デバイス用 MDM](/hololens/hololens-mdm-configure) 経由で設定できます。</span><span class="sxs-lookup"><span data-stu-id="e11cb-141">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="e11cb-142">[Advanced Recovery Companion (ARC)](/hololens/hololens-recovery) を使用します</span><span class="sxs-lookup"><span data-stu-id="e11cb-142">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="e11cb-143">デバイス管理の詳細については、 **[HoloLens デバイス管理](/hololens/hololens-csp-policy-overview)** の概要を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-143">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="e11cb-144">USB 経由で展開できない</span><span class="sxs-lookup"><span data-stu-id="e11cb-144">I can't deploy over USB</span></span>

<span data-ttu-id="e11cb-145">USB 経由で直接アプリケーションを展開できない場合は、上記のすべてのインストール要件を満たしていることを確認し、[ステップバイステップ チュートリアル](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2)に従ってください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-145">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="e11cb-146">イマーシブ (VR) ヘッドセットの要件</span><span class="sxs-lookup"><span data-stu-id="e11cb-146">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="e11cb-147">以下のガイドラインは、イマーシブ (VR) ヘッドセットの *開発用 PC* に対する現在の最小かつ推奨仕様であり、定期的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="e11cb-147">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="e11cb-148">この仕様を、[PC ハードウェア互換性最小ガイドライン](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)と間違えないようにしてください。このガイドラインは、イマーシブ (VR) ヘッドセットのアプリまたはゲームの対象となる *コンシューマー PC の仕様* について説明するものです。</span><span class="sxs-lookup"><span data-stu-id="e11cb-148">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="e11cb-149">イマーシブ ヘッドセット開発用 PC にフルサイズの HDMI および/または USB 3.0 ポートがない場合、ヘッドセットを接続するための[アダプター](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)が必要になります。</span><span class="sxs-lookup"><span data-stu-id="e11cb-149">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="e11cb-150">一部のハードウェア構成、特にハイブリッド グラフィックスを搭載したノートブックなどには、現在[既知の問題](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)があります。</span><span class="sxs-lookup"><span data-stu-id="e11cb-150">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="e11cb-151">最小</span><span class="sxs-lookup"><span data-stu-id="e11cb-151">Minimum</span></span></th><th> <span data-ttu-id="e11cb-152">推奨</span><span class="sxs-lookup"><span data-stu-id="e11cb-152">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="e11cb-153">プロセッサ</span><span class="sxs-lookup"><span data-stu-id="e11cb-153">Processor</span></span></td><td> <span data-ttu-id="e11cb-154"><b>ノートブック:</b>Intel Mobile Core i5 第 7 世代 CPU、ハイパー スレッディング対応デュアルコア <b>デスクトップ:</b>Intel Desktop i5 第 6 世代 CPU、ハイパー スレッディング対応デュアルコア<b>または</b> AMD FX4350 4.2GHz クワッドコア相当</span><span class="sxs-lookup"><span data-stu-id="e11cb-154"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="e11cb-155"><b>デスクトップ:</b>Intel Desktop i7 第 6 世代 (6 コア) <b>または</b> AMD Ryzen 5 1600 (6 コア、12 スレッド)</span><span class="sxs-lookup"><span data-stu-id="e11cb-155"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-156">GPU</span><span class="sxs-lookup"><span data-stu-id="e11cb-156">GPU</span></span></td><td> <span data-ttu-id="e11cb-157"><b>ノートブック:</b>NVIDIA GTX 965M、AMD RX 460M (2 GB) 相当またはそれ以上の DX12 対応 GPU <b>デスクトップ:</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="e11cb-157"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="e11cb-158"><b>デスクトップ:</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="e11cb-158"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-159">GPU ドライバー WDDM バージョン</span><span class="sxs-lookup"><span data-stu-id="e11cb-159">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="e11cb-160">WDDM 2.2 ドライバー</span><span class="sxs-lookup"><span data-stu-id="e11cb-160">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-161">熱設計電力</span><span class="sxs-lookup"><span data-stu-id="e11cb-161">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="e11cb-162">15 W 以上</span><span class="sxs-lookup"><span data-stu-id="e11cb-162">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-163">グラフィックス表示ポート</span><span class="sxs-lookup"><span data-stu-id="e11cb-163">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="e11cb-164">ヘッドセット用の使用可能なグラフィックス ディスプレイ ポート (60 Hz ヘッドセットの場合は HDMI 1.4 または DisplayPort 1.2、90 Hz ヘッドセットの場合は HDMI 2.0 または DisplayPort 1.2) x 1</span><span class="sxs-lookup"><span data-stu-id="e11cb-164">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-165">画面の解像度</span><span class="sxs-lookup"><span data-stu-id="e11cb-165">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="e11cb-166">解像度:SVGA (800 x 600) 以上のビットの深度:1 ピクセルあたり 32 ビット色</span><span class="sxs-lookup"><span data-stu-id="e11cb-166">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-167">メモリ</span><span class="sxs-lookup"><span data-stu-id="e11cb-167">Memory</span></span></td><td> <span data-ttu-id="e11cb-168">8&#160;GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="e11cb-168">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="e11cb-169">16 GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="e11cb-169">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-170">記憶域</span><span class="sxs-lookup"><span data-stu-id="e11cb-170">Storage</span></span></td><td colspan="2"> <span data-ttu-id="e11cb-171">&gt;10 GB の追加の空き領域</span><span class="sxs-lookup"><span data-stu-id="e11cb-171">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-172">USB ポート</span><span class="sxs-lookup"><span data-stu-id="e11cb-172">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="e11cb-173">ヘッドセット (USB 3.0 Type-A) の使用可能な USB ポート x 1<b>メモ:USB は、最低 900 mA を給電する必要があります</b></span><span class="sxs-lookup"><span data-stu-id="e11cb-173">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-174">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="e11cb-174">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="e11cb-175">Bluetooth 4.0 (アクセサリ接続用)</span><span class="sxs-lookup"><span data-stu-id="e11cb-175">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="e11cb-176">Unity を使用した MRTK 開発を初めて行う場合は、整理された Unity 開発体験に従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e11cb-176">If you're new to MRTK development with Unity, we recommend following our curated Unity development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e11cb-177">HoloLens 向け Unity の体験を始める</span><span class="sxs-lookup"><span data-stu-id="e11cb-177">Start your Unity for HoloLens journey</span></span>](../unity/unity-development-overview.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="e11cb-178">VR 向け Unity の体験を始める</span><span class="sxs-lookup"><span data-stu-id="e11cb-178">Start your Unity for VR journey</span></span>](../unity/unity-development-wmr-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="e11cb-179">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="e11cb-179">Next Development Checkpoint</span></span>

<span data-ttu-id="e11cb-180">用意されている HoloLens 向け Unity 開発チェックポイント体験に従っている場合、次のタスクは HoloLens 2 チュートリアル シリーズに従って作業することです。</span><span class="sxs-lookup"><span data-stu-id="e11cb-180">If you're following the Unity for HoloLens development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e11cb-181">HoloLens 2 チュートリアル シリーズ</span><span class="sxs-lookup"><span data-stu-id="e11cb-181">HoloLens 2 tutorial series</span></span>](../unity/tutorials/mr-learning-base-01.md)

<span data-ttu-id="e11cb-182">VR 向け Unity の体験に従っている場合は、次のタスクはプロジェクトの設定です。</span><span class="sxs-lookup"><span data-stu-id="e11cb-182">If you're following the Unity for VR journey, your next task is to setup your project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e11cb-183">WMR 用のプロジェクトの構成</span><span class="sxs-lookup"><span data-stu-id="e11cb-183">Configuring your project for WMR</span></span>](../unity/configure-unity-project.md)

<span data-ttu-id="e11cb-184">いつでも [HoloLens](../unity/unity-development-overview.md#1-getting-started) および [VR](../unity/unity-development-wmr-overview.md#1-getting-started) の Unity 開発チェックポイントに戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="e11cb-184">You can always go back to the Unity development checkpoints for [HoloLens](../unity/unity-development-overview.md#1-getting-started) and [VR](../unity/unity-development-wmr-overview.md#1-getting-started) at any time.</span></span>

# <a name="unreal"></a>[<span data-ttu-id="e11cb-185">Unreal</span><span class="sxs-lookup"><span data-stu-id="e11cb-185">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="e11cb-187">1.最新バージョンをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="e11cb-187">1. Download the latest version</span></span>

<span data-ttu-id="e11cb-188">組み込みの HoloLens サポートを最大限に活用するため、[Unreal Engine バージョン 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 以降をインストールすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e11cb-188">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="e11cb-189">2.Mixed Reality Toolkit (MRTK) をインポートする</span><span class="sxs-lookup"><span data-stu-id="e11cb-189">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="e11cb-191">Mixed Reality Toolkit (MRTK) は、Mixed Reality アプリケーション向けのオープン ソースのクロスプラットフォーム開発キットです。</span><span class="sxs-lookup"><span data-stu-id="e11cb-191">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="e11cb-192">MRTK には、空間でのインタラクションのための、クロスプラットフォームの入力システム、基本コンポーネント、共通の構成要素が備わっています。</span><span class="sxs-lookup"><span data-stu-id="e11cb-192">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="e11cb-193">このツールキットは、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォームをターゲットとしたアプリケーションの開発を加速することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="e11cb-193">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="e11cb-194">インストールについては、整理された [ 開発体験](../unreal/unreal-development-overview.md)の[「はじめに」セクション](../unreal/unreal-development-overview.md#1-getting-started)を完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e11cb-194">For installation, we recommend completing the [Getting Started section](../unreal/unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](../unreal/unreal-development-overview.md).</span></span> <span data-ttu-id="e11cb-195">既に Unreal 開発体験に従っている読者は、以下にリストされている残りの設定手順を完了し、[HoloLens 2 入門チュートリアル](../unreal/tutorials/unreal-uxt-ch1.md)に進んでください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-195">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unreal/tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="e11cb-196"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity のロゴ画像](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="e11cb-196"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="e11cb-197">**Mixed Reality Toolkit-Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="e11cb-197">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="e11cb-198">Unreal 用の MRTK を使用しない場合は、すべての対話式操作と動作のスクリプトを開発者が自分で作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e11cb-198">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="e11cb-199">その他のツール (省略可能)</span><span class="sxs-lookup"><span data-stu-id="e11cb-199">Other tools [optional]</span></span>
* <span data-ttu-id="e11cb-200"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - HoloLens やイマーシブ (VR) ヘッドセットで直接動作しない可能性があるコード ビットとコンポーネントですが、これらを組み合わせることで、Windows Mixed Reality をターゲットとしたエクスペリエンスを構築します。</span><span class="sxs-lookup"><span data-stu-id="e11cb-200"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="e11cb-201"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - 共有スクリプトとコンポーネントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="e11cb-201"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="e11cb-202">3.Mixed Reality 開発用 PC を設定する</span><span class="sxs-lookup"><span data-stu-id="e11cb-202">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="e11cb-203">Windows 10 SDK は、Windows 10 オペレーティング システムでの使用に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="e11cb-203">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="e11cb-204">この SDK は、Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 でもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e11cb-204">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="e11cb-205">以前のオペレーティング システムでは、一部のツールがサポートされないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-205">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="e11cb-206">HoloLens 用アプリ、VR イマーシブ ヘッドセット用アプリ、またはこれらの両方に使用できるアプリを開発して展開できます。</span><span class="sxs-lookup"><span data-stu-id="e11cb-206">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="e11cb-207">必要に応じて、以下の要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-207">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="e11cb-208">HoloLens の開発の場合</span><span class="sxs-lookup"><span data-stu-id="e11cb-208">For HoloLens development</span></span>

<span data-ttu-id="e11cb-209">HoloLens の開発用に開発用 PC を設定するときは、[Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) と <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> の両方のシステム要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-209">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="e11cb-210">HoloLens デバイスでアプリを実行するには、[Windows デバイス ポータルのセットアップ手順](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="e11cb-210">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="e11cb-211">[HoloLens エミュレーター](../platform-capabilities-and-apis/using-the-hololens-emulator.md)を使用する予定の場合は、お使いの PC が [HoloLens エミュレーターのシステム要件](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)も満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e11cb-211">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="e11cb-212">HoloLens と Windows Mixed Reality イマーシブ (VR) ヘッドセットの両方を対象とした開発を予定している場合は、以下のセクションに記載のシステムの推奨事項と要件をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-212">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="e11cb-213">HoloLens のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="e11cb-213">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="e11cb-214">開発者モードの設定がグレー表示される</span><span class="sxs-lookup"><span data-stu-id="e11cb-214">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="e11cb-215">デバイスで開発者モードを有効にする際に問題が発生する場合は、自身が[デバイスの所有者](/hololens/security-adminless-os)ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e11cb-215">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="e11cb-216">マルチユーザー モードでは、最初にデバイスを使用するユーザーがデバイスの所有者であり、それ以降のユーザーには、開発者モードまたはその他の構成の変更を有効にするために必要なアクセス許可は付与されません。</span><span class="sxs-lookup"><span data-stu-id="e11cb-216">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="e11cb-217">ただし、最初のユーザーがオートパイロット環境にいるためデバイスの所有者ではないという例外があります。詳しくは、[HoloLens のセキュリティに関するドキュメント](/hololens/security-adminless-os#device-owner)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-217">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="e11cb-218">考えられる解決策:</span><span class="sxs-lookup"><span data-stu-id="e11cb-218">Possible solutions include:</span></span>

* <span data-ttu-id="e11cb-219">デバイスを他のユーザーまたは開発者に渡す前に、デバイス所有者に開発者モードをオンにさせます</span><span class="sxs-lookup"><span data-stu-id="e11cb-219">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="e11cb-220">IT/MDM 管理者が特定のデバイスまたは開発者のデバイス グループに対して CSP [ポリシー ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) を有効にすることを提案します。</span><span class="sxs-lookup"><span data-stu-id="e11cb-220">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="e11cb-221">このポリシーは、[プロビジョニング パッケージ](/hololens/hololens-provisioning)を使うか、[HoloLens デバイス用 MDM](/hololens/hololens-mdm-configure) 経由で設定できます。</span><span class="sxs-lookup"><span data-stu-id="e11cb-221">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="e11cb-222">[Advanced Recovery Companion (ARC)](/hololens/hololens-recovery) を使用します</span><span class="sxs-lookup"><span data-stu-id="e11cb-222">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="e11cb-223">デバイス管理の詳細については、 **[HoloLens デバイス管理](/hololens/hololens-csp-policy-overview)** の概要を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-223">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="e11cb-224">USB 経由で展開できない</span><span class="sxs-lookup"><span data-stu-id="e11cb-224">I can't deploy over USB</span></span>

<span data-ttu-id="e11cb-225">USB 経由で直接アプリケーションを展開できない場合は、上記のすべてのインストール要件を満たしていることを確認し、[ステップバイステップ チュートリアル](../unreal/tutorials/unreal-uxt-ch6.md)に従ってください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-225">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unreal/tutorials/unreal-uxt-ch6.md).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="e11cb-226">イマーシブ (VR) ヘッドセットの要件</span><span class="sxs-lookup"><span data-stu-id="e11cb-226">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="e11cb-227">以下のガイドラインは、イマーシブ (VR) ヘッドセットの *開発用 PC* に対する現在の最小かつ推奨仕様であり、定期的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="e11cb-227">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="e11cb-228">この仕様を、[PC ハードウェア互換性最小ガイドライン](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)と間違えないようにしてください。このガイドラインは、イマーシブ (VR) ヘッドセットのアプリまたはゲームの対象となる *コンシューマー PC の仕様* について説明するものです。</span><span class="sxs-lookup"><span data-stu-id="e11cb-228">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="e11cb-229">イマーシブ ヘッドセット開発用 PC にフルサイズの HDMI および/または USB 3.0 ポートがない場合、ヘッドセットを接続するための[アダプター](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)が必要になります。</span><span class="sxs-lookup"><span data-stu-id="e11cb-229">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="e11cb-230">一部のハードウェア構成、特にハイブリッド グラフィックスを搭載したノートブックなどには、現在[既知の問題](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)があります。</span><span class="sxs-lookup"><span data-stu-id="e11cb-230">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="e11cb-231">最小</span><span class="sxs-lookup"><span data-stu-id="e11cb-231">Minimum</span></span></th><th> <span data-ttu-id="e11cb-232">推奨</span><span class="sxs-lookup"><span data-stu-id="e11cb-232">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="e11cb-233">プロセッサ</span><span class="sxs-lookup"><span data-stu-id="e11cb-233">Processor</span></span></td><td> <span data-ttu-id="e11cb-234"><b>ノートブック:</b>Intel Mobile Core i5 第 7 世代 CPU、ハイパー スレッディング対応デュアルコア <b>デスクトップ:</b>Intel Desktop i5 第 6 世代 CPU、ハイパー スレッディング対応デュアルコア<b>または</b> AMD FX4350 4.2GHz クワッドコア相当</span><span class="sxs-lookup"><span data-stu-id="e11cb-234"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="e11cb-235"><b>デスクトップ:</b>Intel Desktop i7 第 6 世代 (6 コア) <b>または</b> AMD Ryzen 5 1600 (6 コア、12 スレッド)</span><span class="sxs-lookup"><span data-stu-id="e11cb-235"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-236">GPU</span><span class="sxs-lookup"><span data-stu-id="e11cb-236">GPU</span></span></td><td> <span data-ttu-id="e11cb-237"><b>ノートブック:</b>NVIDIA GTX 965M、AMD RX 460M (2 GB) 相当またはそれ以上の DX12 対応 GPU <b>デスクトップ:</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="e11cb-237"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="e11cb-238"><b>デスクトップ:</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="e11cb-238"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-239">GPU ドライバー WDDM バージョン</span><span class="sxs-lookup"><span data-stu-id="e11cb-239">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="e11cb-240">WDDM 2.2 ドライバー</span><span class="sxs-lookup"><span data-stu-id="e11cb-240">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-241">熱設計電力</span><span class="sxs-lookup"><span data-stu-id="e11cb-241">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="e11cb-242">15 W 以上</span><span class="sxs-lookup"><span data-stu-id="e11cb-242">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-243">グラフィックス表示ポート</span><span class="sxs-lookup"><span data-stu-id="e11cb-243">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="e11cb-244">ヘッドセット用の使用可能なグラフィックス ディスプレイ ポート (60 Hz ヘッドセットの場合は HDMI 1.4 または DisplayPort 1.2、90 Hz ヘッドセットの場合は HDMI 2.0 または DisplayPort 1.2) x 1</span><span class="sxs-lookup"><span data-stu-id="e11cb-244">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-245">画面の解像度</span><span class="sxs-lookup"><span data-stu-id="e11cb-245">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="e11cb-246">解像度:SVGA (800 x 600) 以上のビットの深度:1 ピクセルあたり 32 ビット色</span><span class="sxs-lookup"><span data-stu-id="e11cb-246">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-247">メモリ</span><span class="sxs-lookup"><span data-stu-id="e11cb-247">Memory</span></span></td><td> <span data-ttu-id="e11cb-248">8&#160;GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="e11cb-248">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="e11cb-249">16 GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="e11cb-249">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-250">記憶域</span><span class="sxs-lookup"><span data-stu-id="e11cb-250">Storage</span></span></td><td colspan="2"> <span data-ttu-id="e11cb-251">&gt;10 GB の追加の空き領域</span><span class="sxs-lookup"><span data-stu-id="e11cb-251">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-252">USB ポート</span><span class="sxs-lookup"><span data-stu-id="e11cb-252">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="e11cb-253">ヘッドセット (USB 3.0 Type-A) の使用可能な USB ポート x 1<b>メモ:USB は、最低 900 mA を給電する必要があります</b></span><span class="sxs-lookup"><span data-stu-id="e11cb-253">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-254">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="e11cb-254">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="e11cb-255">Bluetooth 4.0 (アクセサリ接続用)</span><span class="sxs-lookup"><span data-stu-id="e11cb-255">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="e11cb-256">Unreal を使用した MRTK 開発を初めて行う場合は、整理された Unreal 開発体験に従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e11cb-256">If you're new to MRTK development with Unreal, we recommend following our curated Unreal development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e11cb-257">Unreal の体験を開始する</span><span class="sxs-lookup"><span data-stu-id="e11cb-257">Start your Unreal journey</span></span>](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="e11cb-258">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="e11cb-258">Next Development Checkpoint</span></span>

<span data-ttu-id="e11cb-259">私たちが用意した Unreal 開発チェックポイント体験に従っている場合、次のタスクは HoloLens 2 チュートリアル シリーズを実行することです。</span><span class="sxs-lookup"><span data-stu-id="e11cb-259">If you're following the Unreal development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e11cb-260">HoloLens 2 チュートリアル シリーズ</span><span class="sxs-lookup"><span data-stu-id="e11cb-260">HoloLens 2 tutorial series</span></span>](../unreal/tutorials/unreal-uxt-ch1.md)

<span data-ttu-id="e11cb-261">いつでも [Unreal 開発チェックポイント](../unreal/unreal-development-overview.md#1-getting-started)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="e11cb-261">You can always go back to the [Unreal development checkpoints](../unreal/unreal-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="native-openxr"></a>[<span data-ttu-id="e11cb-262">ネイティブ (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="e11cb-262">Native (OpenXR)</span></span>](#tab/native)

 ![ネイティブ アプリ開発](../images/native_logo_banner.png)

<span data-ttu-id="e11cb-264">ネイティブな OpenXR 開発では、エンジンをダウンロードする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="e11cb-264">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="e11cb-265">「[OpenXR の概要](../native/openxr-getting-started.md)」に、開発を開始するために必要なものがすべて記載されています。</span><span class="sxs-lookup"><span data-stu-id="e11cb-265">You can find everything you need to begin development in the [Getting started with OpenXR](../native/openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="e11cb-266">1.Mixed Reality 開発用 PC を設定する</span><span class="sxs-lookup"><span data-stu-id="e11cb-266">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="e11cb-267">Windows 10 SDK は、Windows 10 オペレーティング システムでの使用に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="e11cb-267">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="e11cb-268">この SDK は、Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 でもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e11cb-268">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="e11cb-269">以前のオペレーティング システムでは、一部のツールがサポートされないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-269">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="e11cb-270">HoloLens の開発の場合</span><span class="sxs-lookup"><span data-stu-id="e11cb-270">For HoloLens development</span></span>

<span data-ttu-id="e11cb-271">HoloLens の開発用に開発用 PC を設定するときは、<a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> のシステム要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-271">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="e11cb-272">HoloLens デバイスでアプリを実行するには、[Windows デバイス ポータルのセットアップ手順](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="e11cb-272">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="e11cb-273">[HoloLens エミュレーター](../platform-capabilities-and-apis/using-the-hololens-emulator.md)を使用する予定の場合は、お使いの PC が [HoloLens エミュレーターのシステム要件](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)も満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e11cb-273">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="e11cb-274">HoloLens と Windows Mixed Reality イマーシブ (VR) ヘッドセットの両方を対象とした開発を予定している場合は、以下のセクションに記載のシステムの推奨事項と要件をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-274">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="e11cb-275">HoloLens 用アプリ、VR イマーシブ ヘッドセット用アプリ、またはこれらの両方に使用できるアプリを開発して展開できます。</span><span class="sxs-lookup"><span data-stu-id="e11cb-275">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="e11cb-276">必要に応じて、以下の要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-276">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="e11cb-277">HoloLens のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="e11cb-277">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="e11cb-278">開発者モードの設定がグレー表示される</span><span class="sxs-lookup"><span data-stu-id="e11cb-278">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="e11cb-279">デバイスで開発者モードを有効にする際に問題が発生する場合は、自身が[デバイスの所有者](/hololens/security-adminless-os)ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e11cb-279">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="e11cb-280">マルチユーザー モードでは、最初にデバイスを使用するユーザーがデバイスの所有者であり、それ以降のユーザーには、開発者モードまたはその他の構成の変更を有効にするために必要なアクセス許可は付与されません。</span><span class="sxs-lookup"><span data-stu-id="e11cb-280">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="e11cb-281">ただし、最初のユーザーがオートパイロット環境にいるためデバイスの所有者ではないという例外があります。詳しくは、[HoloLens のセキュリティに関するドキュメント](/hololens/security-adminless-os#device-owner)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-281">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="e11cb-282">考えられる解決策:</span><span class="sxs-lookup"><span data-stu-id="e11cb-282">Possible solutions include:</span></span>

* <span data-ttu-id="e11cb-283">デバイスを他のユーザーまたは開発者に渡す前に、デバイス所有者に開発者モードをオンにさせます</span><span class="sxs-lookup"><span data-stu-id="e11cb-283">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="e11cb-284">IT/MDM 管理者が特定のデバイスまたは開発者のデバイス グループに対して CSP [ポリシー ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) を有効にすることを提案します。</span><span class="sxs-lookup"><span data-stu-id="e11cb-284">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="e11cb-285">このポリシーは、[プロビジョニング パッケージ](/hololens/hololens-provisioning)を使うか、[HoloLens デバイス用 MDM](/hololens/hololens-mdm-configure) 経由で設定できます。</span><span class="sxs-lookup"><span data-stu-id="e11cb-285">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="e11cb-286">[Advanced Recovery Companion (ARC)](/hololens/hololens-recovery) を使用します</span><span class="sxs-lookup"><span data-stu-id="e11cb-286">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="e11cb-287">デバイス管理の詳細については、 **[HoloLens デバイス管理](/hololens/hololens-csp-policy-overview)** の概要を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e11cb-287">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="e11cb-288">イマーシブ (VR) ヘッドセットの要件</span><span class="sxs-lookup"><span data-stu-id="e11cb-288">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="e11cb-289">以下のガイドラインは、イマーシブ (VR) ヘッドセットの *開発用 PC* に対する現在の最小かつ推奨仕様であり、定期的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="e11cb-289">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="e11cb-290">この仕様を、[PC ハードウェア互換性最小ガイドライン](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)と間違えないようにしてください。このガイドラインは、イマーシブ (VR) ヘッドセットのアプリまたはゲームの対象となる *コンシューマー PC の仕様* について説明するものです。</span><span class="sxs-lookup"><span data-stu-id="e11cb-290">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="e11cb-291">イマーシブ ヘッドセット開発用 PC にフルサイズの HDMI および/または USB 3.0 ポートがない場合、ヘッドセットを接続するための[アダプター](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)が必要になります。</span><span class="sxs-lookup"><span data-stu-id="e11cb-291">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="e11cb-292">一部のハードウェア構成、特にハイブリッド グラフィックスを搭載したノートブックなどには、現在[既知の問題](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)があります。</span><span class="sxs-lookup"><span data-stu-id="e11cb-292">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="e11cb-293">最小</span><span class="sxs-lookup"><span data-stu-id="e11cb-293">Minimum</span></span></th><th> <span data-ttu-id="e11cb-294">推奨</span><span class="sxs-lookup"><span data-stu-id="e11cb-294">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="e11cb-295">プロセッサ</span><span class="sxs-lookup"><span data-stu-id="e11cb-295">Processor</span></span></td><td> <span data-ttu-id="e11cb-296"><b>ノートブック:</b>Intel Mobile Core i5 第 7 世代 CPU、ハイパー スレッディング対応デュアルコア <b>デスクトップ:</b>Intel Desktop i5 第 6 世代 CPU、ハイパー スレッディング対応デュアルコア<b>または</b> AMD FX4350 4.2GHz クワッドコア相当</span><span class="sxs-lookup"><span data-stu-id="e11cb-296"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="e11cb-297"><b>デスクトップ:</b>Intel Desktop i7 第 6 世代 (6 コア) <b>または</b> AMD Ryzen 5 1600 (6 コア、12 スレッド)</span><span class="sxs-lookup"><span data-stu-id="e11cb-297"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-298">GPU</span><span class="sxs-lookup"><span data-stu-id="e11cb-298">GPU</span></span></td><td> <span data-ttu-id="e11cb-299"><b>ノートブック:</b>NVIDIA GTX 965M、AMD RX 460M (2 GB) 相当またはそれ以上の DX12 対応 GPU <b>デスクトップ:</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="e11cb-299"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="e11cb-300"><b>デスクトップ:</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="e11cb-300"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-301">GPU ドライバー WDDM バージョン</span><span class="sxs-lookup"><span data-stu-id="e11cb-301">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="e11cb-302">WDDM 2.2 ドライバー</span><span class="sxs-lookup"><span data-stu-id="e11cb-302">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-303">熱設計電力</span><span class="sxs-lookup"><span data-stu-id="e11cb-303">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="e11cb-304">15 W 以上</span><span class="sxs-lookup"><span data-stu-id="e11cb-304">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-305">グラフィックス表示ポート</span><span class="sxs-lookup"><span data-stu-id="e11cb-305">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="e11cb-306">ヘッドセット用の使用可能なグラフィックス ディスプレイ ポート (60 Hz ヘッドセットの場合は HDMI 1.4 または DisplayPort 1.2、90 Hz ヘッドセットの場合は HDMI 2.0 または DisplayPort 1.2) x 1</span><span class="sxs-lookup"><span data-stu-id="e11cb-306">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-307">画面の解像度</span><span class="sxs-lookup"><span data-stu-id="e11cb-307">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="e11cb-308">解像度:SVGA (800 x 600) 以上のビットの深度:1 ピクセルあたり 32 ビット色</span><span class="sxs-lookup"><span data-stu-id="e11cb-308">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-309">メモリ</span><span class="sxs-lookup"><span data-stu-id="e11cb-309">Memory</span></span></td><td> <span data-ttu-id="e11cb-310">8&#160;GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="e11cb-310">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="e11cb-311">16 GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="e11cb-311">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-312">記憶域</span><span class="sxs-lookup"><span data-stu-id="e11cb-312">Storage</span></span></td><td colspan="2"> <span data-ttu-id="e11cb-313">&gt;10 GB の追加の空き領域</span><span class="sxs-lookup"><span data-stu-id="e11cb-313">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-314">USB ポート</span><span class="sxs-lookup"><span data-stu-id="e11cb-314">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="e11cb-315">ヘッドセット (USB 3.0 Type-A) の使用可能な USB ポート x 1<b>メモ:USB は、最低 900 mA を給電する必要があります</b></span><span class="sxs-lookup"><span data-stu-id="e11cb-315">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="e11cb-316">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="e11cb-316">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="e11cb-317">Bluetooth 4.0 (アクセサリ接続用)</span><span class="sxs-lookup"><span data-stu-id="e11cb-317">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="e11cb-318">MRTK を使用したネイティブ開発を初めて行う場合は、整理されたネイティブ開発体験に従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e11cb-318">If you're new to Native development with MRTK, we recommend following our curated Native development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e11cb-319">ネイティブの体験を開始する</span><span class="sxs-lookup"><span data-stu-id="e11cb-319">Start your Native journey</span></span>](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="e11cb-320">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="e11cb-320">Next Development Checkpoint</span></span>

<span data-ttu-id="e11cb-321">私たちが用意したネイティブ開発チェックポイント体験に従っている場合、次のタスクは HoloLens 2 の開発環境を構成することです。</span><span class="sxs-lookup"><span data-stu-id="e11cb-321">If you're following the Native development checkpoint journey we've laid out, your next task is to configure your development environment for HoloLens 2.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e11cb-322">HoloLens 2 の設定</span><span class="sxs-lookup"><span data-stu-id="e11cb-322">Setup for HoloLens 2</span></span>](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

<span data-ttu-id="e11cb-323">いつでも[開発チェックポイント](../native/directx-development-overview.md#1-getting-started)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="e11cb-323">You can always go back to the [Native development checkpoints](../native/directx-development-overview.md#1-getting-started) at any time.</span></span>