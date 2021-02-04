---
ms.openlocfilehash: c205e3b812eeb7a85bfe361d4fd83f9aec7b7999
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2021
ms.locfileid: "99244849"
---
# <a name="unity"></a>[<span data-ttu-id="ea053-101">Unity</span><span class="sxs-lookup"><span data-stu-id="ea053-101">Unity</span></span>](#tab/unity)

![Unity のロゴ バナー](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a><span data-ttu-id="ea053-103">1.最新バージョンをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="ea053-103">1. Download the latest version</span></span>

<span data-ttu-id="ea053-104">新しいプロジェクトを開始する際に使用する最適なバージョンとして、[Unity LTS (長期サポート)](https://unity3d.com/unity/qa/lts-releases) ストリームをお勧めします。最新の安定した修正プログラムを取得するには最新リビジョンに更新します。</span><span class="sxs-lookup"><span data-stu-id="ea053-104">We recommend the [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) stream as the best version to use when starting new projects, updating to its latest revision to pick up the latest stable fixes.</span></span>
* <span data-ttu-id="ea053-105">現在は、 **[Unity 2019.4 LTS](https://unity3d.com/unity/qa/lts-releases?version=2019.4)** を使用することをお勧めしています。これは、以下の MRTK v2 に必要な LTS ビルドです。</span><span class="sxs-lookup"><span data-stu-id="ea053-105">The current recommendation is to use **[Unity 2019.4 LTS](https://unity3d.com/unity/qa/lts-releases?version=2019.4)**, which is the LTS build required for MRTK v2 below.</span></span>
* <span data-ttu-id="ea053-106">特定の理由から別のバージョンの Unity を使用する必要がある場合、Unity では異なるバージョンの side-by-side インストールをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="ea053-106">If you need to use a different version of Unity for specific reasons, Unity supports side-by-side installs of different versions.</span></span>

### <a name="2-install-the-mixed-reality-feature-tool"></a><span data-ttu-id="ea053-107">2.Mixed Reality Feature Tool をインストールする</span><span class="sxs-lookup"><span data-stu-id="ea053-107">2. Install the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="ea053-108">[Mixed Reality Feature Tool](../unity/welcome-to-mr-feature-tool.md) は、開発者が Mixed Reality 機能パッケージを検出し、Unity プロジェクトに追加するための新しい方法です。</span><span class="sxs-lookup"><span data-stu-id="ea053-108">The [Mixed Reality Feature Tool](../unity/welcome-to-mr-feature-tool.md) is a new way for developers to discover and add Mixed Reality feature packages into Unity projects.</span></span> 

<span data-ttu-id="ea053-109">名前またはカテゴリでパッケージを検索し、それらの依存関係を確認し、インポートする前にプロジェクト マニフェスト ファイルに提案された変更を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="ea053-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="ea053-110">必要なパッケージを検証すると、Mixed Reality Feature Tool によって、それらが選択したプロジェクトにダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="ea053-110">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

#### <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="ea053-111">Mixed Reality Toolkit をインポートする</span><span class="sxs-lookup"><span data-stu-id="ea053-111">Importing the Mixed Reality Toolkit</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="ea053-113">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) は、Mixed Reality アプリケーション向けのオープンソースのクロスプラットフォーム開発キットです。</span><span class="sxs-lookup"><span data-stu-id="ea053-113">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> 

* <span data-ttu-id="ea053-114">[インストールと使用方法の手順](../unity/welcome-to-mr-feature-tool.md#system-requirements)に関するページに従い、**Mixed Reality Toolkit Foundation** パッケージを選択して、Mixed Reality Toolkit パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="ea053-114">Install the Mixed Reality Toolkit package by following the [installation and usage instructions](../unity/welcome-to-mr-feature-tool.md#system-requirements) and selecting the **Mixed Reality Toolkit Foundation** package.</span></span>

<span data-ttu-id="ea053-115">整理された [HoloLens](../unity/unity-development-overview.md#1-getting-started) または [VR](../unity/unity-development-wmr-overview.md#1-getting-started) の開発体験の概要セクションを完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ea053-115">We recommend completing the getting started section in our curated [HoloLens](../unity/unity-development-overview.md#1-getting-started) or [VR](../unity/unity-development-wmr-overview.md#1-getting-started) development journeys.</span></span> <span data-ttu-id="ea053-116">既に HoloLens 用 Unity 開発体験に従っている場合は、以下の一覧で示されている残りの設定手順を完了し、[HoloLens 2 入門チュートリアル](../unity/tutorials/mr-learning-base-01.md)に進んでください。</span><span class="sxs-lookup"><span data-stu-id="ea053-116">If you're already following the Unity development for HoloLens journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unity/tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ea053-117">インストール手順では MRTK と Unity リリースの最新の安定した組み合わせである **MRTK 2.5.1** と **Unity 2019.4 LTS** を対象としていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ea053-117">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.5.1** and **Unity 2019.4 LTS**.</span></span>

> [!NOTE]
> <span data-ttu-id="ea053-118">Unity 用の MRTK を使用しない場合は、[すべての対話式操作と動作のスクリプトを開発者が自分で作成する](../unity/configure-unity-project.md)必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea053-118">If you don't want to use MRTK for Unity, you'll need to [script all interactions and behaviors yourself](../unity/configure-unity-project.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="ea053-119"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity バナー](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="ea053-119"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="ea053-120">**Mixed Reality Toolkit-Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="ea053-120">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a><span data-ttu-id="ea053-121">その他のツール (省略可能)</span><span class="sxs-lookup"><span data-stu-id="ea053-121">Other tools [optional]</span></span>
* <span data-ttu-id="ea053-122"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - HoloLens やイマーシブ (VR) ヘッドセットで直接動作しない可能性があるコード ビットとコンポーネントですが、これらを組み合わせることで、Windows Mixed Reality をターゲットとしたエクスペリエンスを構築します。</span><span class="sxs-lookup"><span data-stu-id="ea053-122"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="ea053-123"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - 共有スクリプトとコンポーネントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="ea053-123"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="ea053-124">3.Mixed Reality 開発用 PC を設定する</span><span class="sxs-lookup"><span data-stu-id="ea053-124">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="ea053-125">Windows 10 SDK は、Windows 10 オペレーティング システムでの使用に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="ea053-125">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="ea053-126">この SDK は、Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 でもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ea053-126">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="ea053-127">以前のオペレーティング システムでは、一部のツールがサポートされないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="ea053-127">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="ea053-128">HoloLens 用アプリ、VR イマーシブ ヘッドセット用アプリ、またはこれらの両方に使用できるアプリを開発して展開できます。</span><span class="sxs-lookup"><span data-stu-id="ea053-128">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="ea053-129">必要に応じて、以下の要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="ea053-129">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="ea053-130">HoloLens の開発の場合</span><span class="sxs-lookup"><span data-stu-id="ea053-130">For HoloLens development</span></span>

<span data-ttu-id="ea053-131">開発用の PC を HoloLens の開発用に設定するときは、<a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> と <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> の両方のシステム要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="ea053-131">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="ea053-132">HoloLens デバイスでアプリを実行するには、[Windows デバイス ポータルのセットアップ手順](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea053-132">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="ea053-133">[HoloLens エミュレーター](../platform-capabilities-and-apis/using-the-hololens-emulator.md)を使用する予定の場合は、お使いの PC が [HoloLens エミュレーターのシステム要件](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)も満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea053-133">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="ea053-134">HoloLens エミュレーターを開始するには、「[Using the HoloLens emulator (HoloLens エミュレーターを使用する)](../platform-capabilities-and-apis/using-the-hololens-emulator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea053-134">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="ea053-135">HoloLens と Windows Mixed Reality イマーシブ (VR) ヘッドセットの両方を対象とした開発を予定している場合は、以下のセクションに記載のシステムの推奨事項と要件をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="ea053-135">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="ea053-136">HoloLens のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="ea053-136">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="ea053-137">開発者モードの設定がグレー表示される</span><span class="sxs-lookup"><span data-stu-id="ea053-137">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="ea053-138">デバイスで開発者モードを有効にする際に問題が発生する場合は、自身が[デバイスの所有者](/hololens/security-adminless-os)ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ea053-138">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="ea053-139">マルチユーザー モードでは、最初にデバイスを使用するユーザーがデバイスの所有者であり、それ以降のユーザーには、開発者モードまたはその他の構成の変更を有効にするために必要なアクセス許可は付与されません。</span><span class="sxs-lookup"><span data-stu-id="ea053-139">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="ea053-140">ただし、最初のユーザーがオートパイロット環境にいるためデバイスの所有者ではないという例外があります。詳しくは、[HoloLens のセキュリティに関するドキュメント](/hololens/security-adminless-os#device-owner)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea053-140">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="ea053-141">考えられる解決策:</span><span class="sxs-lookup"><span data-stu-id="ea053-141">Possible solutions include:</span></span>

* <span data-ttu-id="ea053-142">デバイスを他のユーザーまたは開発者に渡す前に、デバイス所有者に開発者モードをオンにさせます</span><span class="sxs-lookup"><span data-stu-id="ea053-142">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="ea053-143">IT/MDM 管理者が特定のデバイスまたは開発者のデバイス グループに対して CSP [ポリシー ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) を有効にすることを提案します。</span><span class="sxs-lookup"><span data-stu-id="ea053-143">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="ea053-144">このポリシーは、[プロビジョニング パッケージ](/hololens/hololens-provisioning)を使うか、[HoloLens デバイス用 MDM](/hololens/hololens-mdm-configure) 経由で設定できます。</span><span class="sxs-lookup"><span data-stu-id="ea053-144">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="ea053-145">[Advanced Recovery Companion (ARC)](/hololens/hololens-recovery) を使用します</span><span class="sxs-lookup"><span data-stu-id="ea053-145">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="ea053-146">デバイス管理の詳細については、 **[HoloLens デバイス管理](/hololens/hololens-csp-policy-overview)** の概要を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea053-146">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="ea053-147">USB 経由で展開できない</span><span class="sxs-lookup"><span data-stu-id="ea053-147">I can't deploy over USB</span></span>

<span data-ttu-id="ea053-148">USB 経由で直接アプリケーションを展開できない場合は、上記のすべてのインストール要件を満たしていることを確認し、[ステップバイステップ チュートリアル](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2)に従ってください。</span><span class="sxs-lookup"><span data-stu-id="ea053-148">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="ea053-149">イマーシブ (VR) ヘッドセットの要件</span><span class="sxs-lookup"><span data-stu-id="ea053-149">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="ea053-150">以下のガイドラインは、イマーシブ (VR) ヘッドセットの *開発用 PC* に対する現在の最小かつ推奨仕様であり、定期的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="ea053-150">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="ea053-151">この仕様を、[PC ハードウェア互換性最小ガイドライン](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)と間違えないようにしてください。このガイドラインは、イマーシブ (VR) ヘッドセットのアプリまたはゲームの対象となる *コンシューマー PC の仕様* について説明するものです。</span><span class="sxs-lookup"><span data-stu-id="ea053-151">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="ea053-152">イマーシブ ヘッドセット開発用 PC にフルサイズの HDMI および/または USB 3.0 ポートがない場合、ヘッドセットを接続するための[アダプター](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)が必要になります。</span><span class="sxs-lookup"><span data-stu-id="ea053-152">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="ea053-153">一部のハードウェア構成、特にハイブリッド グラフィックスを搭載したノートブックなどには、現在[既知の問題](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)があります。</span><span class="sxs-lookup"><span data-stu-id="ea053-153">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="ea053-154">最小</span><span class="sxs-lookup"><span data-stu-id="ea053-154">Minimum</span></span></th><th> <span data-ttu-id="ea053-155">推奨</span><span class="sxs-lookup"><span data-stu-id="ea053-155">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="ea053-156">プロセッサ</span><span class="sxs-lookup"><span data-stu-id="ea053-156">Processor</span></span></td><td> <span data-ttu-id="ea053-157"><b>ノートブック:</b>Intel Mobile Core i5 第 7 世代 CPU、ハイパー スレッディング対応デュアルコア <b>デスクトップ:</b>Intel Desktop i5 第 6 世代 CPU、ハイパー スレッディング対応デュアルコア<b>または</b> AMD FX4350 4.2GHz クワッドコア相当</span><span class="sxs-lookup"><span data-stu-id="ea053-157"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="ea053-158"><b>デスクトップ:</b>Intel Desktop i7 第 6 世代 (6 コア) <b>または</b> AMD Ryzen 5 1600 (6 コア、12 スレッド)</span><span class="sxs-lookup"><span data-stu-id="ea053-158"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-159">GPU</span><span class="sxs-lookup"><span data-stu-id="ea053-159">GPU</span></span></td><td> <span data-ttu-id="ea053-160"><b>ノートブック:</b>NVIDIA GTX 965M、AMD RX 460M (2 GB) 相当またはそれ以上の DX12 対応 GPU <b>デスクトップ:</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="ea053-160"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="ea053-161"><b>デスクトップ:</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="ea053-161"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-162">GPU ドライバー WDDM バージョン</span><span class="sxs-lookup"><span data-stu-id="ea053-162">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="ea053-163">WDDM 2.2 ドライバー</span><span class="sxs-lookup"><span data-stu-id="ea053-163">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-164">熱設計電力</span><span class="sxs-lookup"><span data-stu-id="ea053-164">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="ea053-165">15 W 以上</span><span class="sxs-lookup"><span data-stu-id="ea053-165">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-166">グラフィックス表示ポート</span><span class="sxs-lookup"><span data-stu-id="ea053-166">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="ea053-167">ヘッドセット用の使用可能なグラフィックス ディスプレイ ポート (60 Hz ヘッドセットの場合は HDMI 1.4 または DisplayPort 1.2、90 Hz ヘッドセットの場合は HDMI 2.0 または DisplayPort 1.2) x 1</span><span class="sxs-lookup"><span data-stu-id="ea053-167">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-168">画面の解像度</span><span class="sxs-lookup"><span data-stu-id="ea053-168">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="ea053-169">解像度:SVGA (800 x 600) 以上のビットの深度:1 ピクセルあたり 32 ビット色</span><span class="sxs-lookup"><span data-stu-id="ea053-169">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-170">メモリ</span><span class="sxs-lookup"><span data-stu-id="ea053-170">Memory</span></span></td><td> <span data-ttu-id="ea053-171">8&#160;GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="ea053-171">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="ea053-172">16 GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="ea053-172">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-173">記憶域</span><span class="sxs-lookup"><span data-stu-id="ea053-173">Storage</span></span></td><td colspan="2"> <span data-ttu-id="ea053-174">&gt;10 GB の追加の空き領域</span><span class="sxs-lookup"><span data-stu-id="ea053-174">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-175">USB ポート</span><span class="sxs-lookup"><span data-stu-id="ea053-175">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="ea053-176">ヘッドセット (USB 3.0 Type-A) の使用可能な USB ポート x 1<b>メモ:USB は、最低 900 mA を給電する必要があります</b></span><span class="sxs-lookup"><span data-stu-id="ea053-176">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-177">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="ea053-177">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="ea053-178">Bluetooth 4.0 (アクセサリ接続用)</span><span class="sxs-lookup"><span data-stu-id="ea053-178">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="ea053-179">Unity を使用した MRTK 開発を初めて行う場合は、整理された Unity 開発体験に従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ea053-179">If you're new to MRTK development with Unity, we recommend following our curated Unity development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ea053-180">HoloLens 向け Unity の体験を始める</span><span class="sxs-lookup"><span data-stu-id="ea053-180">Start your Unity for HoloLens journey</span></span>](../unity/unity-development-overview.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="ea053-181">VR 向け Unity の体験を始める</span><span class="sxs-lookup"><span data-stu-id="ea053-181">Start your Unity for VR journey</span></span>](../unity/unity-development-wmr-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="ea053-182">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="ea053-182">Next Development Checkpoint</span></span>

<span data-ttu-id="ea053-183">用意されている HoloLens 向け Unity 開発チェックポイント体験に従っている場合、次のタスクは HoloLens 2 チュートリアル シリーズに従って作業することです。</span><span class="sxs-lookup"><span data-stu-id="ea053-183">If you're following the Unity for HoloLens development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ea053-184">HoloLens 2 チュートリアル シリーズ</span><span class="sxs-lookup"><span data-stu-id="ea053-184">HoloLens 2 tutorial series</span></span>](../unity/tutorials/mr-learning-base-01.md)

<span data-ttu-id="ea053-185">VR 向け Unity の体験に従っている場合は、次のタスクはプロジェクトの設定です。</span><span class="sxs-lookup"><span data-stu-id="ea053-185">If you're following the Unity for VR journey, your next task is to setup your project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ea053-186">WMR 用のプロジェクトの構成</span><span class="sxs-lookup"><span data-stu-id="ea053-186">Configuring your project for WMR</span></span>](../unity/configure-unity-project.md)

<span data-ttu-id="ea053-187">いつでも [HoloLens](../unity/unity-development-overview.md#1-getting-started) および [VR](../unity/unity-development-wmr-overview.md#1-getting-started) の Unity 開発チェックポイントに戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="ea053-187">You can always go back to the Unity development checkpoints for [HoloLens](../unity/unity-development-overview.md#1-getting-started) and [VR](../unity/unity-development-wmr-overview.md#1-getting-started) at any time.</span></span>

# <a name="unreal"></a>[<span data-ttu-id="ea053-188">Unreal</span><span class="sxs-lookup"><span data-stu-id="ea053-188">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="ea053-190">1.最新バージョンをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="ea053-190">1. Download the latest version</span></span>

<span data-ttu-id="ea053-191">組み込みの HoloLens サポートを最大限に活用するため、[Unreal Engine バージョン 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 以降をインストールすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ea053-191">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="ea053-192">2.Mixed Reality Toolkit (MRTK) をインポートする</span><span class="sxs-lookup"><span data-stu-id="ea053-192">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="ea053-194">Mixed Reality Toolkit (MRTK) は、Mixed Reality アプリケーション向けのオープン ソースのクロスプラットフォーム開発キットです。</span><span class="sxs-lookup"><span data-stu-id="ea053-194">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="ea053-195">MRTK には、空間でのインタラクションのための、クロスプラットフォームの入力システム、基本コンポーネント、共通の構成要素が備わっています。</span><span class="sxs-lookup"><span data-stu-id="ea053-195">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="ea053-196">このツールキットは、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォームをターゲットとしたアプリケーションの開発を加速することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="ea053-196">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="ea053-197">インストールについては、整理された [ 開発体験](../unreal/unreal-development-overview.md)の[「はじめに」セクション](../unreal/unreal-development-overview.md#1-getting-started)を完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ea053-197">For installation, we recommend completing the [Getting Started section](../unreal/unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](../unreal/unreal-development-overview.md).</span></span> <span data-ttu-id="ea053-198">既に Unreal 開発体験に従っている読者は、以下にリストされている残りの設定手順を完了し、[HoloLens 2 入門チュートリアル](../unreal/tutorials/unreal-uxt-ch1.md)に進んでください。</span><span class="sxs-lookup"><span data-stu-id="ea053-198">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unreal/tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="ea053-199"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity のロゴ画像](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="ea053-199"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="ea053-200">**Mixed Reality Toolkit-Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="ea053-200">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="ea053-201">Unreal 用の MRTK を使用しない場合は、すべての対話式操作と動作のスクリプトを開発者が自分で作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea053-201">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="ea053-202">その他のツール (省略可能)</span><span class="sxs-lookup"><span data-stu-id="ea053-202">Other tools [optional]</span></span>
* <span data-ttu-id="ea053-203"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - HoloLens やイマーシブ (VR) ヘッドセットで直接動作しない可能性があるコード ビットとコンポーネントですが、これらを組み合わせることで、Windows Mixed Reality をターゲットとしたエクスペリエンスを構築します。</span><span class="sxs-lookup"><span data-stu-id="ea053-203"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="ea053-204"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - 共有スクリプトとコンポーネントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="ea053-204"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="ea053-205">3.Mixed Reality 開発用 PC を設定する</span><span class="sxs-lookup"><span data-stu-id="ea053-205">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="ea053-206">Windows 10 SDK は、Windows 10 オペレーティング システムでの使用に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="ea053-206">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="ea053-207">この SDK は、Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 でもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ea053-207">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="ea053-208">以前のオペレーティング システムでは、一部のツールがサポートされないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="ea053-208">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="ea053-209">HoloLens 用アプリ、VR イマーシブ ヘッドセット用アプリ、またはこれらの両方に使用できるアプリを開発して展開できます。</span><span class="sxs-lookup"><span data-stu-id="ea053-209">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="ea053-210">必要に応じて、以下の要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="ea053-210">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="ea053-211">HoloLens の開発の場合</span><span class="sxs-lookup"><span data-stu-id="ea053-211">For HoloLens development</span></span>

<span data-ttu-id="ea053-212">HoloLens の開発用に開発用 PC を設定するときは、[Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) と <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> の両方のシステム要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="ea053-212">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="ea053-213">HoloLens デバイスでアプリを実行するには、[Windows デバイス ポータルのセットアップ手順](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea053-213">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="ea053-214">[HoloLens エミュレーター](../platform-capabilities-and-apis/using-the-hololens-emulator.md)を使用する予定の場合は、お使いの PC が [HoloLens エミュレーターのシステム要件](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)も満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea053-214">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="ea053-215">HoloLens と Windows Mixed Reality イマーシブ (VR) ヘッドセットの両方を対象とした開発を予定している場合は、以下のセクションに記載のシステムの推奨事項と要件をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="ea053-215">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="ea053-216">HoloLens のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="ea053-216">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="ea053-217">開発者モードの設定がグレー表示される</span><span class="sxs-lookup"><span data-stu-id="ea053-217">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="ea053-218">デバイスで開発者モードを有効にする際に問題が発生する場合は、自身が[デバイスの所有者](/hololens/security-adminless-os)ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ea053-218">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="ea053-219">マルチユーザー モードでは、最初にデバイスを使用するユーザーがデバイスの所有者であり、それ以降のユーザーには、開発者モードまたはその他の構成の変更を有効にするために必要なアクセス許可は付与されません。</span><span class="sxs-lookup"><span data-stu-id="ea053-219">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="ea053-220">ただし、最初のユーザーがオートパイロット環境にいるためデバイスの所有者ではないという例外があります。詳しくは、[HoloLens のセキュリティに関するドキュメント](/hololens/security-adminless-os#device-owner)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea053-220">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="ea053-221">考えられる解決策:</span><span class="sxs-lookup"><span data-stu-id="ea053-221">Possible solutions include:</span></span>

* <span data-ttu-id="ea053-222">デバイスを他のユーザーまたは開発者に渡す前に、デバイス所有者に開発者モードをオンにさせます</span><span class="sxs-lookup"><span data-stu-id="ea053-222">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="ea053-223">IT/MDM 管理者が特定のデバイスまたは開発者のデバイス グループに対して CSP [ポリシー ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) を有効にすることを提案します。</span><span class="sxs-lookup"><span data-stu-id="ea053-223">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="ea053-224">このポリシーは、[プロビジョニング パッケージ](/hololens/hololens-provisioning)を使うか、[HoloLens デバイス用 MDM](/hololens/hololens-mdm-configure) 経由で設定できます。</span><span class="sxs-lookup"><span data-stu-id="ea053-224">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="ea053-225">[Advanced Recovery Companion (ARC)](/hololens/hololens-recovery) を使用します</span><span class="sxs-lookup"><span data-stu-id="ea053-225">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="ea053-226">デバイス管理の詳細については、 **[HoloLens デバイス管理](/hololens/hololens-csp-policy-overview)** の概要を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea053-226">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="ea053-227">USB 経由で展開できない</span><span class="sxs-lookup"><span data-stu-id="ea053-227">I can't deploy over USB</span></span>

<span data-ttu-id="ea053-228">USB 経由で直接アプリケーションを展開できない場合は、上記のすべてのインストール要件を満たしていることを確認し、[ステップバイステップ チュートリアル](../unreal/tutorials/unreal-uxt-ch6.md)に従ってください。</span><span class="sxs-lookup"><span data-stu-id="ea053-228">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unreal/tutorials/unreal-uxt-ch6.md).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="ea053-229">イマーシブ (VR) ヘッドセットの要件</span><span class="sxs-lookup"><span data-stu-id="ea053-229">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="ea053-230">以下のガイドラインは、イマーシブ (VR) ヘッドセットの *開発用 PC* に対する現在の最小かつ推奨仕様であり、定期的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="ea053-230">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="ea053-231">この仕様を、[PC ハードウェア互換性最小ガイドライン](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)と間違えないようにしてください。このガイドラインは、イマーシブ (VR) ヘッドセットのアプリまたはゲームの対象となる *コンシューマー PC の仕様* について説明するものです。</span><span class="sxs-lookup"><span data-stu-id="ea053-231">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="ea053-232">イマーシブ ヘッドセット開発用 PC にフルサイズの HDMI および/または USB 3.0 ポートがない場合、ヘッドセットを接続するための[アダプター](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)が必要になります。</span><span class="sxs-lookup"><span data-stu-id="ea053-232">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="ea053-233">一部のハードウェア構成、特にハイブリッド グラフィックスを搭載したノートブックなどには、現在[既知の問題](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)があります。</span><span class="sxs-lookup"><span data-stu-id="ea053-233">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="ea053-234">最小</span><span class="sxs-lookup"><span data-stu-id="ea053-234">Minimum</span></span></th><th> <span data-ttu-id="ea053-235">推奨</span><span class="sxs-lookup"><span data-stu-id="ea053-235">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="ea053-236">プロセッサ</span><span class="sxs-lookup"><span data-stu-id="ea053-236">Processor</span></span></td><td> <span data-ttu-id="ea053-237"><b>ノートブック:</b>Intel Mobile Core i5 第 7 世代 CPU、ハイパー スレッディング対応デュアルコア <b>デスクトップ:</b>Intel Desktop i5 第 6 世代 CPU、ハイパー スレッディング対応デュアルコア<b>または</b> AMD FX4350 4.2GHz クワッドコア相当</span><span class="sxs-lookup"><span data-stu-id="ea053-237"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="ea053-238"><b>デスクトップ:</b>Intel Desktop i7 第 6 世代 (6 コア) <b>または</b> AMD Ryzen 5 1600 (6 コア、12 スレッド)</span><span class="sxs-lookup"><span data-stu-id="ea053-238"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-239">GPU</span><span class="sxs-lookup"><span data-stu-id="ea053-239">GPU</span></span></td><td> <span data-ttu-id="ea053-240"><b>ノートブック:</b>NVIDIA GTX 965M、AMD RX 460M (2 GB) 相当またはそれ以上の DX12 対応 GPU <b>デスクトップ:</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="ea053-240"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="ea053-241"><b>デスクトップ:</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="ea053-241"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-242">GPU ドライバー WDDM バージョン</span><span class="sxs-lookup"><span data-stu-id="ea053-242">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="ea053-243">WDDM 2.2 ドライバー</span><span class="sxs-lookup"><span data-stu-id="ea053-243">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-244">熱設計電力</span><span class="sxs-lookup"><span data-stu-id="ea053-244">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="ea053-245">15 W 以上</span><span class="sxs-lookup"><span data-stu-id="ea053-245">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-246">グラフィックス表示ポート</span><span class="sxs-lookup"><span data-stu-id="ea053-246">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="ea053-247">ヘッドセット用の使用可能なグラフィックス ディスプレイ ポート (60 Hz ヘッドセットの場合は HDMI 1.4 または DisplayPort 1.2、90 Hz ヘッドセットの場合は HDMI 2.0 または DisplayPort 1.2) x 1</span><span class="sxs-lookup"><span data-stu-id="ea053-247">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-248">画面の解像度</span><span class="sxs-lookup"><span data-stu-id="ea053-248">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="ea053-249">解像度:SVGA (800 x 600) 以上のビットの深度:1 ピクセルあたり 32 ビット色</span><span class="sxs-lookup"><span data-stu-id="ea053-249">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-250">メモリ</span><span class="sxs-lookup"><span data-stu-id="ea053-250">Memory</span></span></td><td> <span data-ttu-id="ea053-251">8&#160;GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="ea053-251">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="ea053-252">16 GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="ea053-252">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-253">記憶域</span><span class="sxs-lookup"><span data-stu-id="ea053-253">Storage</span></span></td><td colspan="2"> <span data-ttu-id="ea053-254">&gt;10 GB の追加の空き領域</span><span class="sxs-lookup"><span data-stu-id="ea053-254">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-255">USB ポート</span><span class="sxs-lookup"><span data-stu-id="ea053-255">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="ea053-256">ヘッドセット (USB 3.0 Type-A) の使用可能な USB ポート x 1<b>メモ:USB は、最低 900 mA を給電する必要があります</b></span><span class="sxs-lookup"><span data-stu-id="ea053-256">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-257">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="ea053-257">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="ea053-258">Bluetooth 4.0 (アクセサリ接続用)</span><span class="sxs-lookup"><span data-stu-id="ea053-258">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="ea053-259">Unreal を使用した MRTK 開発を初めて行う場合は、整理された Unreal 開発体験に従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ea053-259">If you're new to MRTK development with Unreal, we recommend following our curated Unreal development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ea053-260">Unreal の体験を開始する</span><span class="sxs-lookup"><span data-stu-id="ea053-260">Start your Unreal journey</span></span>](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="ea053-261">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="ea053-261">Next Development Checkpoint</span></span>

<span data-ttu-id="ea053-262">私たちが用意した Unreal 開発チェックポイント体験に従っている場合、次のタスクは HoloLens 2 チュートリアル シリーズを実行することです。</span><span class="sxs-lookup"><span data-stu-id="ea053-262">If you're following the Unreal development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ea053-263">HoloLens 2 チュートリアル シリーズ</span><span class="sxs-lookup"><span data-stu-id="ea053-263">HoloLens 2 tutorial series</span></span>](../unreal/tutorials/unreal-uxt-ch1.md)

<span data-ttu-id="ea053-264">いつでも [Unreal 開発チェックポイント](../unreal/unreal-development-overview.md#1-getting-started)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="ea053-264">You can always go back to the [Unreal development checkpoints](../unreal/unreal-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="native-openxr"></a>[<span data-ttu-id="ea053-265">ネイティブ (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="ea053-265">Native (OpenXR)</span></span>](#tab/native)

 ![ネイティブ アプリ開発](../images/native_logo_banner.png)

<span data-ttu-id="ea053-267">ネイティブな OpenXR 開発では、エンジンをダウンロードする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ea053-267">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="ea053-268">「[OpenXR の概要](../native/openxr-getting-started.md)」に、開発を開始するために必要なものがすべて記載されています。</span><span class="sxs-lookup"><span data-stu-id="ea053-268">You can find everything you need to begin development in the [Getting started with OpenXR](../native/openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="ea053-269">1.Mixed Reality 開発用 PC を設定する</span><span class="sxs-lookup"><span data-stu-id="ea053-269">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="ea053-270">Windows 10 SDK は、Windows 10 オペレーティング システムでの使用に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="ea053-270">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="ea053-271">この SDK は、Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 でもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ea053-271">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="ea053-272">以前のオペレーティング システムでは、一部のツールがサポートされないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="ea053-272">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="ea053-273">HoloLens の開発の場合</span><span class="sxs-lookup"><span data-stu-id="ea053-273">For HoloLens development</span></span>

<span data-ttu-id="ea053-274">HoloLens の開発用に開発用 PC を設定するときは、<a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> のシステム要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="ea053-274">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="ea053-275">HoloLens デバイスでアプリを実行するには、[Windows デバイス ポータルのセットアップ手順](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea053-275">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="ea053-276">[HoloLens エミュレーター](../platform-capabilities-and-apis/using-the-hololens-emulator.md)を使用する予定の場合は、お使いの PC が [HoloLens エミュレーターのシステム要件](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)も満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea053-276">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="ea053-277">HoloLens と Windows Mixed Reality イマーシブ (VR) ヘッドセットの両方を対象とした開発を予定している場合は、以下のセクションに記載のシステムの推奨事項と要件をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="ea053-277">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="ea053-278">HoloLens 用アプリ、VR イマーシブ ヘッドセット用アプリ、またはこれらの両方に使用できるアプリを開発して展開できます。</span><span class="sxs-lookup"><span data-stu-id="ea053-278">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="ea053-279">必要に応じて、以下の要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="ea053-279">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="ea053-280">HoloLens のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="ea053-280">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="ea053-281">開発者モードの設定がグレー表示される</span><span class="sxs-lookup"><span data-stu-id="ea053-281">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="ea053-282">デバイスで開発者モードを有効にする際に問題が発生する場合は、自身が[デバイスの所有者](/hololens/security-adminless-os)ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ea053-282">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="ea053-283">マルチユーザー モードでは、最初にデバイスを使用するユーザーがデバイスの所有者であり、それ以降のユーザーには、開発者モードまたはその他の構成の変更を有効にするために必要なアクセス許可は付与されません。</span><span class="sxs-lookup"><span data-stu-id="ea053-283">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="ea053-284">ただし、最初のユーザーがオートパイロット環境にいるためデバイスの所有者ではないという例外があります。詳しくは、[HoloLens のセキュリティに関するドキュメント](/hololens/security-adminless-os#device-owner)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea053-284">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="ea053-285">考えられる解決策:</span><span class="sxs-lookup"><span data-stu-id="ea053-285">Possible solutions include:</span></span>

* <span data-ttu-id="ea053-286">デバイスを他のユーザーまたは開発者に渡す前に、デバイス所有者に開発者モードをオンにさせます</span><span class="sxs-lookup"><span data-stu-id="ea053-286">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="ea053-287">IT/MDM 管理者が特定のデバイスまたは開発者のデバイス グループに対して CSP [ポリシー ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) を有効にすることを提案します。</span><span class="sxs-lookup"><span data-stu-id="ea053-287">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="ea053-288">このポリシーは、[プロビジョニング パッケージ](/hololens/hololens-provisioning)を使うか、[HoloLens デバイス用 MDM](/hololens/hololens-mdm-configure) 経由で設定できます。</span><span class="sxs-lookup"><span data-stu-id="ea053-288">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="ea053-289">[Advanced Recovery Companion (ARC)](/hololens/hololens-recovery) を使用します</span><span class="sxs-lookup"><span data-stu-id="ea053-289">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="ea053-290">デバイス管理の詳細については、 **[HoloLens デバイス管理](/hololens/hololens-csp-policy-overview)** の概要を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea053-290">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="ea053-291">イマーシブ (VR) ヘッドセットの要件</span><span class="sxs-lookup"><span data-stu-id="ea053-291">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="ea053-292">以下のガイドラインは、イマーシブ (VR) ヘッドセットの *開発用 PC* に対する現在の最小かつ推奨仕様であり、定期的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="ea053-292">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="ea053-293">この仕様を、[PC ハードウェア互換性最小ガイドライン](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)と間違えないようにしてください。このガイドラインは、イマーシブ (VR) ヘッドセットのアプリまたはゲームの対象となる *コンシューマー PC の仕様* について説明するものです。</span><span class="sxs-lookup"><span data-stu-id="ea053-293">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="ea053-294">イマーシブ ヘッドセット開発用 PC にフルサイズの HDMI および/または USB 3.0 ポートがない場合、ヘッドセットを接続するための[アダプター](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)が必要になります。</span><span class="sxs-lookup"><span data-stu-id="ea053-294">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="ea053-295">一部のハードウェア構成、特にハイブリッド グラフィックスを搭載したノートブックなどには、現在[既知の問題](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)があります。</span><span class="sxs-lookup"><span data-stu-id="ea053-295">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="ea053-296">最小</span><span class="sxs-lookup"><span data-stu-id="ea053-296">Minimum</span></span></th><th> <span data-ttu-id="ea053-297">推奨</span><span class="sxs-lookup"><span data-stu-id="ea053-297">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="ea053-298">プロセッサ</span><span class="sxs-lookup"><span data-stu-id="ea053-298">Processor</span></span></td><td> <span data-ttu-id="ea053-299"><b>ノートブック:</b>Intel Mobile Core i5 第 7 世代 CPU、ハイパー スレッディング対応デュアルコア <b>デスクトップ:</b>Intel Desktop i5 第 6 世代 CPU、ハイパー スレッディング対応デュアルコア<b>または</b> AMD FX4350 4.2GHz クワッドコア相当</span><span class="sxs-lookup"><span data-stu-id="ea053-299"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="ea053-300"><b>デスクトップ:</b>Intel Desktop i7 第 6 世代 (6 コア) <b>または</b> AMD Ryzen 5 1600 (6 コア、12 スレッド)</span><span class="sxs-lookup"><span data-stu-id="ea053-300"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-301">GPU</span><span class="sxs-lookup"><span data-stu-id="ea053-301">GPU</span></span></td><td> <span data-ttu-id="ea053-302"><b>ノートブック:</b>NVIDIA GTX 965M、AMD RX 460M (2 GB) 相当またはそれ以上の DX12 対応 GPU <b>デスクトップ:</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="ea053-302"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="ea053-303"><b>デスクトップ:</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="ea053-303"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-304">GPU ドライバー WDDM バージョン</span><span class="sxs-lookup"><span data-stu-id="ea053-304">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="ea053-305">WDDM 2.2 ドライバー</span><span class="sxs-lookup"><span data-stu-id="ea053-305">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-306">熱設計電力</span><span class="sxs-lookup"><span data-stu-id="ea053-306">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="ea053-307">15 W 以上</span><span class="sxs-lookup"><span data-stu-id="ea053-307">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-308">グラフィックス表示ポート</span><span class="sxs-lookup"><span data-stu-id="ea053-308">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="ea053-309">ヘッドセット用の使用可能なグラフィックス ディスプレイ ポート (60 Hz ヘッドセットの場合は HDMI 1.4 または DisplayPort 1.2、90 Hz ヘッドセットの場合は HDMI 2.0 または DisplayPort 1.2) x 1</span><span class="sxs-lookup"><span data-stu-id="ea053-309">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-310">画面の解像度</span><span class="sxs-lookup"><span data-stu-id="ea053-310">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="ea053-311">解像度:SVGA (800 x 600) 以上のビットの深度:1 ピクセルあたり 32 ビット色</span><span class="sxs-lookup"><span data-stu-id="ea053-311">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-312">メモリ</span><span class="sxs-lookup"><span data-stu-id="ea053-312">Memory</span></span></td><td> <span data-ttu-id="ea053-313">8&#160;GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="ea053-313">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="ea053-314">16 GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="ea053-314">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-315">記憶域</span><span class="sxs-lookup"><span data-stu-id="ea053-315">Storage</span></span></td><td colspan="2"> <span data-ttu-id="ea053-316">&gt;10 GB の追加の空き領域</span><span class="sxs-lookup"><span data-stu-id="ea053-316">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-317">USB ポート</span><span class="sxs-lookup"><span data-stu-id="ea053-317">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="ea053-318">ヘッドセット (USB 3.0 Type-A) の使用可能な USB ポート x 1<b>メモ:USB は、最低 900 mA を給電する必要があります</b></span><span class="sxs-lookup"><span data-stu-id="ea053-318">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="ea053-319">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="ea053-319">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="ea053-320">Bluetooth 4.0 (アクセサリ接続用)</span><span class="sxs-lookup"><span data-stu-id="ea053-320">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="ea053-321">MRTK を使用したネイティブ開発を初めて行う場合は、整理されたネイティブ開発体験に従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ea053-321">If you're new to Native development with MRTK, we recommend following our curated Native development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ea053-322">ネイティブの体験を開始する</span><span class="sxs-lookup"><span data-stu-id="ea053-322">Start your Native journey</span></span>](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="ea053-323">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="ea053-323">Next Development Checkpoint</span></span>

<span data-ttu-id="ea053-324">私たちが用意したネイティブ開発チェックポイント体験に従っている場合、次のタスクは HoloLens 2 の開発環境を構成することです。</span><span class="sxs-lookup"><span data-stu-id="ea053-324">If you're following the Native development checkpoint journey we've laid out, your next task is to configure your development environment for HoloLens 2.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ea053-325">HoloLens 2 の設定</span><span class="sxs-lookup"><span data-stu-id="ea053-325">Setup for HoloLens 2</span></span>](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

<span data-ttu-id="ea053-326">いつでも[開発チェックポイント](../native/directx-development-overview.md#1-getting-started)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="ea053-326">You can always go back to the [Native development checkpoints](../native/directx-development-overview.md#1-getting-started) at any time.</span></span>