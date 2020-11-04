---
ms.openlocfilehash: ad8f4a5ea9bda7915731f879da96cf7e007c58fb
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2020
ms.locfileid: "92755702"
---
# <a name="unity"></a>[<span data-ttu-id="66da9-101">Unity</span><span class="sxs-lookup"><span data-stu-id="66da9-101">Unity</span></span>](#tab/unity)

![Unity のロゴ バナー](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a><span data-ttu-id="66da9-103">1.最新バージョンをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="66da9-103">1. Download the latest version</span></span>

<span data-ttu-id="66da9-104">新しいプロジェクトを開始する際に使用する最適なバージョンとして、[Unity LTS (長期サポート)](https://unity3d.com/unity/qa/lts-releases) ストリームをお勧めします。最新の安定した修正プログラムを取得するには最新リビジョンに更新します。</span><span class="sxs-lookup"><span data-stu-id="66da9-104">We recommend the [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) stream as the best version to use when starting new projects, updating to its latest revision to pick up the latest stable fixes.</span></span>
* <span data-ttu-id="66da9-105">現在は、 **Unity 2019** を使用することをお勧めしています。これは、以下の MRTK v2 に必要な LTS ビルドです。</span><span class="sxs-lookup"><span data-stu-id="66da9-105">The current recommendation is to use **Unity 2019** , which is the LTS build required for MRTK v2 below.</span></span>
* <span data-ttu-id="66da9-106">特定の理由から別のバージョンの Unity を使用する必要がある場合、Unity では異なるバージョンの side-by-side インストールをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="66da9-106">If you need to use a different version of Unity for specific reasons, Unity supports side-by-side installs of different versions.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="66da9-107">2.Mixed Reality Toolkit (MRTK) をインポートする</span><span class="sxs-lookup"><span data-stu-id="66da9-107">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="66da9-109">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) は、Mixed Reality アプリケーション向けのオープンソースのクロスプラットフォーム開発キットです。</span><span class="sxs-lookup"><span data-stu-id="66da9-109">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="66da9-110">MRTK には、空間でのインタラクションのための、クロスプラットフォームの入力システム、基本コンポーネント、共通の構成要素が備わっています。</span><span class="sxs-lookup"><span data-stu-id="66da9-110">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="66da9-111">このツールキットは、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォームをターゲットとしたアプリケーションの開発を加速することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="66da9-111">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="66da9-112">インストールについては、整理された [Unity 開発体験](../unity/unity-development-overview.md)の[「はじめに」セクション](../unity/unity-development-overview.md#1-getting-started)を完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="66da9-112">For installation, we recommend completing the [Getting Started section](../unity/unity-development-overview.md#1-getting-started) of our curated [Unity development journey](../unity/unity-development-overview.md).</span></span> <span data-ttu-id="66da9-113">既に Unity 開発体験に従っている読者は、以下にリストされている残りの設定手順を完了し、[HoloLens 2 入門チュートリアル](../unity/tutorials/mr-learning-base-01.md)に進んでください。</span><span class="sxs-lookup"><span data-stu-id="66da9-113">If you're already following the Unity development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unity/tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="66da9-114">インストール手順では MRTK と Unity リリースの最新の安定した組み合わせである **MRTK 2.4.0** と **Unity 2019.3.15** を対象としていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="66da9-114">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.4.0** and **Unity 2019.3.15**.</span></span>

> [!NOTE]
> <span data-ttu-id="66da9-115">Unity 用の MRTK を使用しない場合は、すべての対話式操作と動作のスクリプトを開発者が自分で作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66da9-115">If you don't want to use MRTK for Unity, you'll need to script all interactions and behaviors yourself.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="66da9-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity バナー](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="66da9-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="66da9-117">**Mixed Reality Toolkit-Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="66da9-117">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a><span data-ttu-id="66da9-118">その他のツール (省略可能)</span><span class="sxs-lookup"><span data-stu-id="66da9-118">Other tools [optional]</span></span>
* <span data-ttu-id="66da9-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - HoloLens やイマーシブ (VR) ヘッドセットで直接動作しない可能性があるコード ビットとコンポーネントですが、これらを組み合わせることで、Windows Mixed Reality をターゲットとしたエクスペリエンスを構築します。</span><span class="sxs-lookup"><span data-stu-id="66da9-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="66da9-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - 共有スクリプトとコンポーネントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="66da9-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="66da9-121">3.Mixed Reality 開発用 PC を設定する</span><span class="sxs-lookup"><span data-stu-id="66da9-121">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="66da9-122">Windows 10 SDK は、Windows 10 オペレーティング システムでの使用に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="66da9-122">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="66da9-123">この SDK は、Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 でもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="66da9-123">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="66da9-124">以前のオペレーティング システムでは、一部のツールがサポートされないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="66da9-124">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="66da9-125">HoloLens 用アプリ、VR イマーシブ ヘッドセット用アプリ、またはこれらの両方に使用できるアプリを開発して展開できます。</span><span class="sxs-lookup"><span data-stu-id="66da9-125">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="66da9-126">必要に応じて、以下の要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="66da9-126">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="66da9-127">HoloLens の開発の場合</span><span class="sxs-lookup"><span data-stu-id="66da9-127">For HoloLens development</span></span>

<span data-ttu-id="66da9-128">開発用の PC を HoloLens の開発用に設定するときは、<a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> と <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> の両方のシステム要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="66da9-128">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="66da9-129">[HoloLens エミュレーター](../platform-capabilities-and-apis/using-the-hololens-emulator.md)を使用する予定の場合は、お使いの PC が [HoloLens エミュレーターのシステム要件](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)も満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66da9-129">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="66da9-130">HoloLens エミュレーターを開始するには、「[Using the HoloLens emulator (HoloLens エミュレーターを使用する)](../platform-capabilities-and-apis/using-the-hololens-emulator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66da9-130">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="66da9-131">HoloLens と Windows Mixed Reality イマーシブ (VR) ヘッドセットの両方を対象とした開発を予定している場合は、以下のセクションに記載のシステムの推奨事項と要件をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="66da9-131">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="66da9-132">イマーシブ (VR) ヘッドセットの要件</span><span class="sxs-lookup"><span data-stu-id="66da9-132">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="66da9-133">以下のガイドラインは、イマーシブ (VR) ヘッドセットの *開発用 PC* に対する現在の最小かつ推奨仕様であり、定期的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="66da9-133">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC* , and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="66da9-134">この仕様を、 [PC ハードウェア互換性最小ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)と間違えないようにしてください。このガイドラインは、イマーシブ (VR) ヘッドセットのアプリまたはゲームの対象となる *コンシューマー PC の仕様* について説明するものです。</span><span class="sxs-lookup"><span data-stu-id="66da9-134">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="66da9-135">**Reverb G2** ヘッドセットを使用している場合は、 **Microsoft-Valve OpenXR** プラグインをダウンロードします (TODO://必要なリンク)。</span><span class="sxs-lookup"><span data-stu-id="66da9-135">If you're using a **Reverb G2** headset, download the **Microsoft-Valve OpenXR** plugin (TODO: // Need link).</span></span>

<span data-ttu-id="66da9-136">イマーシブ ヘッドセット開発用 PC にフルサイズの HDMI および/または USB 3.0 ポートがない場合、ヘッドセットを接続するための[アダプター](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)が必要になります。</span><span class="sxs-lookup"><span data-stu-id="66da9-136">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="66da9-137">一部のハードウェア構成、特にハイブリッド グラフィックスを搭載したノートブックなどには、現在[既知の問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)があります。</span><span class="sxs-lookup"><span data-stu-id="66da9-137">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="66da9-138">最小</span><span class="sxs-lookup"><span data-stu-id="66da9-138">Minimum</span></span></th><th> <span data-ttu-id="66da9-139">推奨</span><span class="sxs-lookup"><span data-stu-id="66da9-139">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="66da9-140">プロセッサ</span><span class="sxs-lookup"><span data-stu-id="66da9-140">Processor</span></span></td><td> <span data-ttu-id="66da9-141"><b>ノートブック:</b>Intel Mobile Core i5 第 7 世代 CPU、ハイパー スレッディング対応デュアルコア <b>デスクトップ:</b>Intel Desktop i5 第 6 世代 CPU、ハイパー スレッディング対応デュアルコア<b>または</b> AMD FX4350 4.2GHz クワッドコア相当</span><span class="sxs-lookup"><span data-stu-id="66da9-141"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="66da9-142"><b>デスクトップ:</b>Intel Desktop i7 第 6 世代 (6 コア) <b>または</b> AMD Ryzen 5 1600 (6 コア、12 スレッド)</span><span class="sxs-lookup"><span data-stu-id="66da9-142"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-143">GPU</span><span class="sxs-lookup"><span data-stu-id="66da9-143">GPU</span></span></td><td> <span data-ttu-id="66da9-144"><b>ノートブック:</b>NVIDIA GTX 965M、AMD RX 460M (2 GB) 相当またはそれ以上の DX12 対応 GPU <b>デスクトップ:</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="66da9-144"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="66da9-145"><b>デスクトップ:</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="66da9-145"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-146">GPU ドライバー WDDM バージョン</span><span class="sxs-lookup"><span data-stu-id="66da9-146">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="66da9-147">WDDM 2.2 ドライバー</span><span class="sxs-lookup"><span data-stu-id="66da9-147">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-148">熱設計電力</span><span class="sxs-lookup"><span data-stu-id="66da9-148">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="66da9-149">15 W 以上</span><span class="sxs-lookup"><span data-stu-id="66da9-149">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-150">グラフィックス表示ポート</span><span class="sxs-lookup"><span data-stu-id="66da9-150">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="66da9-151">ヘッドセット用の使用可能なグラフィックス ディスプレイ ポート (60 Hz ヘッドセットの場合は HDMI 1.4 または DisplayPort 1.2、90 Hz ヘッドセットの場合は HDMI 2.0 または DisplayPort 1.2) x 1</span><span class="sxs-lookup"><span data-stu-id="66da9-151">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-152">画面の解像度</span><span class="sxs-lookup"><span data-stu-id="66da9-152">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="66da9-153">解像度:SVGA (800 x 600) 以上のビットの深度:1 ピクセルあたり 32 ビット色</span><span class="sxs-lookup"><span data-stu-id="66da9-153">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-154">メモリ</span><span class="sxs-lookup"><span data-stu-id="66da9-154">Memory</span></span></td><td> <span data-ttu-id="66da9-155">8&#160;GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="66da9-155">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="66da9-156">16 GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="66da9-156">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-157">記憶域</span><span class="sxs-lookup"><span data-stu-id="66da9-157">Storage</span></span></td><td colspan="2"> <span data-ttu-id="66da9-158">&gt;10 GB の追加の空き領域</span><span class="sxs-lookup"><span data-stu-id="66da9-158">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-159">USB ポート</span><span class="sxs-lookup"><span data-stu-id="66da9-159">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="66da9-160">ヘッドセット (USB 3.0 Type-A) の使用可能な USB ポート x 1<b>メモ:USB は、最低 900 mA を給電する必要があります</b></span><span class="sxs-lookup"><span data-stu-id="66da9-160">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-161">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="66da9-161">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="66da9-162">Bluetooth 4.0 (アクセサリ接続用)</span><span class="sxs-lookup"><span data-stu-id="66da9-162">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="66da9-163">Unity を使用した MRTK 開発を初めて行う場合は、整理された Unity 開発体験に従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="66da9-163">If you're new to MRTK development with Unity, we recommend following our curated Unity development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="66da9-164">Unity の体験を開始する</span><span class="sxs-lookup"><span data-stu-id="66da9-164">Start your Unity journey</span></span>](../unity/unity-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="66da9-165">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="66da9-165">Next Development Checkpoint</span></span>

<span data-ttu-id="66da9-166">私たちが用意した Unity 開発チェックポイント体験に従っている場合、次のタスクは HoloLens 2 チュートリアル シリーズを実行することです。</span><span class="sxs-lookup"><span data-stu-id="66da9-166">If you're following the Unity development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="66da9-167">HoloLens 2 チュートリアル シリーズ</span><span class="sxs-lookup"><span data-stu-id="66da9-167">HoloLens 2 tutorial series</span></span>](../unity/tutorials/mr-learning-base-01.md)

<span data-ttu-id="66da9-168">いつでも [Unity 開発チェックポイント](../unity/unity-development-overview.md#1-getting-started)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="66da9-168">You can always go back to the [Unity development checkpoints](../unity/unity-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="unreal"></a>[<span data-ttu-id="66da9-169">Unreal</span><span class="sxs-lookup"><span data-stu-id="66da9-169">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="66da9-171">1.最新バージョンをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="66da9-171">1. Download the latest version</span></span>

<span data-ttu-id="66da9-172">組み込みの HoloLens サポートを最大限に活用するため、[Unreal Engine バージョン 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 以降をインストールすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="66da9-172">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="66da9-173">2.Mixed Reality Toolkit (MRTK) をインポートする</span><span class="sxs-lookup"><span data-stu-id="66da9-173">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="66da9-175">Mixed Reality Toolkit (MRTK) は、Mixed Reality アプリケーション向けのオープン ソースのクロスプラットフォーム開発キットです。</span><span class="sxs-lookup"><span data-stu-id="66da9-175">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="66da9-176">MRTK には、空間でのインタラクションのための、クロスプラットフォームの入力システム、基本コンポーネント、共通の構成要素が備わっています。</span><span class="sxs-lookup"><span data-stu-id="66da9-176">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="66da9-177">このツールキットは、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォームをターゲットとしたアプリケーションの開発を加速することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="66da9-177">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="66da9-178">インストールについては、整理された [ 開発体験](../unreal/unreal-development-overview.md)の[「はじめに」セクション](../unreal/unreal-development-overview.md#1-getting-started)を完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="66da9-178">For installation, we recommend completing the [Getting Started section](../unreal/unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](../unreal/unreal-development-overview.md).</span></span> <span data-ttu-id="66da9-179">既に Unreal 開発体験に従っている読者は、以下にリストされている残りの設定手順を完了し、[HoloLens 2 入門チュートリアル](../unreal/tutorials/unreal-uxt-ch1.md)に進んでください。</span><span class="sxs-lookup"><span data-stu-id="66da9-179">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unreal/tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="66da9-180"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity のロゴ画像](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="66da9-180"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="66da9-181">**Mixed Reality Toolkit-Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="66da9-181">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="66da9-182">Unreal 用の MRTK を使用しない場合は、すべての対話式操作と動作のスクリプトを開発者が自分で作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66da9-182">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="66da9-183">その他のツール (省略可能)</span><span class="sxs-lookup"><span data-stu-id="66da9-183">Other tools [optional]</span></span>
* <span data-ttu-id="66da9-184"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - HoloLens やイマーシブ (VR) ヘッドセットで直接動作しない可能性があるコード ビットとコンポーネントですが、これらを組み合わせることで、Windows Mixed Reality をターゲットとしたエクスペリエンスを構築します。</span><span class="sxs-lookup"><span data-stu-id="66da9-184"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="66da9-185"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - 共有スクリプトとコンポーネントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="66da9-185"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="66da9-186">3.Mixed Reality 開発用 PC を設定する</span><span class="sxs-lookup"><span data-stu-id="66da9-186">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="66da9-187">Windows 10 SDK は、Windows 10 オペレーティング システムでの使用に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="66da9-187">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="66da9-188">この SDK は、Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 でもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="66da9-188">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="66da9-189">以前のオペレーティング システムでは、一部のツールがサポートされないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="66da9-189">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="66da9-190">HoloLens 用アプリ、VR イマーシブ ヘッドセット用アプリ、またはこれらの両方に使用できるアプリを開発して展開できます。</span><span class="sxs-lookup"><span data-stu-id="66da9-190">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="66da9-191">必要に応じて、以下の要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="66da9-191">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="66da9-192">HoloLens の開発の場合</span><span class="sxs-lookup"><span data-stu-id="66da9-192">For HoloLens development</span></span>

<span data-ttu-id="66da9-193">HoloLens の開発用に開発用 PC を設定するときは、[Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) と <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> の両方のシステム要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="66da9-193">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="66da9-194">[HoloLens エミュレーター](../platform-capabilities-and-apis/using-the-hololens-emulator.md)を使用する予定の場合は、お使いの PC が [HoloLens エミュレーターのシステム要件](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)も満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66da9-194">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="66da9-195">HoloLens と Windows Mixed Reality イマーシブ (VR) ヘッドセットの両方を対象とした開発を予定している場合は、以下のセクションに記載のシステムの推奨事項と要件をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="66da9-195">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="66da9-196">イマーシブ (VR) ヘッドセットの要件</span><span class="sxs-lookup"><span data-stu-id="66da9-196">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="66da9-197">以下のガイドラインは、イマーシブ (VR) ヘッドセットの *開発用 PC* に対する現在の最小かつ推奨仕様であり、定期的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="66da9-197">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC* , and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="66da9-198">この仕様を、 [PC ハードウェア互換性最小ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)と間違えないようにしてください。このガイドラインは、イマーシブ (VR) ヘッドセットのアプリまたはゲームの対象となる *コンシューマー PC の仕様* について説明するものです。</span><span class="sxs-lookup"><span data-stu-id="66da9-198">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="66da9-199">**Reverb G2** ヘッドセットを使用している場合は、 **Microsoft-Valve OpenXR** プラグインをダウンロードします (TODO://必要なリンク)。</span><span class="sxs-lookup"><span data-stu-id="66da9-199">If you're using a **Reverb G2** headset, download the **Microsoft-Valve OpenXR** plugin (TODO: // Need link).</span></span>

<span data-ttu-id="66da9-200">イマーシブ ヘッドセット開発用 PC にフルサイズの HDMI および/または USB 3.0 ポートがない場合、ヘッドセットを接続するための[アダプター](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)が必要になります。</span><span class="sxs-lookup"><span data-stu-id="66da9-200">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="66da9-201">一部のハードウェア構成、特にハイブリッド グラフィックスを搭載したノートブックなどには、現在[既知の問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)があります。</span><span class="sxs-lookup"><span data-stu-id="66da9-201">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="66da9-202">最小</span><span class="sxs-lookup"><span data-stu-id="66da9-202">Minimum</span></span></th><th> <span data-ttu-id="66da9-203">推奨</span><span class="sxs-lookup"><span data-stu-id="66da9-203">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="66da9-204">プロセッサ</span><span class="sxs-lookup"><span data-stu-id="66da9-204">Processor</span></span></td><td> <span data-ttu-id="66da9-205"><b>ノートブック:</b>Intel Mobile Core i5 第 7 世代 CPU、ハイパー スレッディング対応デュアルコア <b>デスクトップ:</b>Intel Desktop i5 第 6 世代 CPU、ハイパー スレッディング対応デュアルコア<b>または</b> AMD FX4350 4.2GHz クワッドコア相当</span><span class="sxs-lookup"><span data-stu-id="66da9-205"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="66da9-206"><b>デスクトップ:</b>Intel Desktop i7 第 6 世代 (6 コア) <b>または</b> AMD Ryzen 5 1600 (6 コア、12 スレッド)</span><span class="sxs-lookup"><span data-stu-id="66da9-206"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-207">GPU</span><span class="sxs-lookup"><span data-stu-id="66da9-207">GPU</span></span></td><td> <span data-ttu-id="66da9-208"><b>ノートブック:</b>NVIDIA GTX 965M、AMD RX 460M (2 GB) 相当またはそれ以上の DX12 対応 GPU <b>デスクトップ:</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="66da9-208"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="66da9-209"><b>デスクトップ:</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="66da9-209"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-210">GPU ドライバー WDDM バージョン</span><span class="sxs-lookup"><span data-stu-id="66da9-210">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="66da9-211">WDDM 2.2 ドライバー</span><span class="sxs-lookup"><span data-stu-id="66da9-211">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-212">熱設計電力</span><span class="sxs-lookup"><span data-stu-id="66da9-212">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="66da9-213">15 W 以上</span><span class="sxs-lookup"><span data-stu-id="66da9-213">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-214">グラフィックス表示ポート</span><span class="sxs-lookup"><span data-stu-id="66da9-214">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="66da9-215">ヘッドセット用の使用可能なグラフィックス ディスプレイ ポート (60 Hz ヘッドセットの場合は HDMI 1.4 または DisplayPort 1.2、90 Hz ヘッドセットの場合は HDMI 2.0 または DisplayPort 1.2) x 1</span><span class="sxs-lookup"><span data-stu-id="66da9-215">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-216">画面の解像度</span><span class="sxs-lookup"><span data-stu-id="66da9-216">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="66da9-217">解像度:SVGA (800 x 600) 以上のビットの深度:1 ピクセルあたり 32 ビット色</span><span class="sxs-lookup"><span data-stu-id="66da9-217">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-218">メモリ</span><span class="sxs-lookup"><span data-stu-id="66da9-218">Memory</span></span></td><td> <span data-ttu-id="66da9-219">8&#160;GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="66da9-219">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="66da9-220">16 GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="66da9-220">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-221">記憶域</span><span class="sxs-lookup"><span data-stu-id="66da9-221">Storage</span></span></td><td colspan="2"> <span data-ttu-id="66da9-222">&gt;10 GB の追加の空き領域</span><span class="sxs-lookup"><span data-stu-id="66da9-222">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-223">USB ポート</span><span class="sxs-lookup"><span data-stu-id="66da9-223">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="66da9-224">ヘッドセット (USB 3.0 Type-A) の使用可能な USB ポート x 1<b>メモ:USB は、最低 900 mA を給電する必要があります</b></span><span class="sxs-lookup"><span data-stu-id="66da9-224">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-225">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="66da9-225">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="66da9-226">Bluetooth 4.0 (アクセサリ接続用)</span><span class="sxs-lookup"><span data-stu-id="66da9-226">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="66da9-227">Unreal を使用した MRTK 開発を初めて行う場合は、整理された Unreal 開発体験に従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="66da9-227">If you're new to MRTK development with Unreal, we recommend following our curated Unreal development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="66da9-228">Unreal の体験を開始する</span><span class="sxs-lookup"><span data-stu-id="66da9-228">Start your Unreal journey</span></span>](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="66da9-229">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="66da9-229">Next Development Checkpoint</span></span>

<span data-ttu-id="66da9-230">私たちが用意した Unreal 開発チェックポイント体験に従っている場合、次のタスクは HoloLens 2 チュートリアル シリーズを実行することです。</span><span class="sxs-lookup"><span data-stu-id="66da9-230">If you're following the Unreal development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="66da9-231">HoloLens 2 チュートリアル シリーズ</span><span class="sxs-lookup"><span data-stu-id="66da9-231">HoloLens 2 tutorial series</span></span>](../unreal/tutorials/unreal-uxt-ch1.md)

<span data-ttu-id="66da9-232">いつでも [Unreal 開発チェックポイント](../unreal/unreal-development-overview.md#1-getting-started)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="66da9-232">You can always go back to the [Unreal development checkpoints](../unreal/unreal-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="native-openxr"></a>[<span data-ttu-id="66da9-233">ネイティブ (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="66da9-233">Native (OpenXR)</span></span>](#tab/native)

 ![ネイティブ アプリ開発](../images/native_logo_banner.png)

<span data-ttu-id="66da9-235">ネイティブな OpenXR 開発では、エンジンをダウンロードする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="66da9-235">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="66da9-236">「[OpenXR の概要](../native/openxr-getting-started.md)」に、開発を開始するために必要なものがすべて記載されています。</span><span class="sxs-lookup"><span data-stu-id="66da9-236">You can find everything you need to begin development in the [Getting started with OpenXR](../native/openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="66da9-237">1.Mixed Reality 開発用 PC を設定する</span><span class="sxs-lookup"><span data-stu-id="66da9-237">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="66da9-238">Windows 10 SDK は、Windows 10 オペレーティング システムでの使用に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="66da9-238">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="66da9-239">この SDK は、Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 でもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="66da9-239">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="66da9-240">以前のオペレーティング システムでは、一部のツールがサポートされないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="66da9-240">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="66da9-241">HoloLens の開発の場合</span><span class="sxs-lookup"><span data-stu-id="66da9-241">For HoloLens development</span></span>

<span data-ttu-id="66da9-242">HoloLens の開発用に開発用 PC を設定するときは、<a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> のシステム要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="66da9-242">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="66da9-243">[HoloLens エミュレーター](../platform-capabilities-and-apis/using-the-hololens-emulator.md)を使用する予定の場合は、お使いの PC が [HoloLens エミュレーターのシステム要件](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)も満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66da9-243">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="66da9-244">HoloLens と Windows Mixed Reality イマーシブ (VR) ヘッドセットの両方を対象とした開発を予定している場合は、以下のセクションに記載のシステムの推奨事項と要件をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="66da9-244">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="66da9-245">HoloLens 用アプリ、VR イマーシブ ヘッドセット用アプリ、またはこれらの両方に使用できるアプリを開発して展開できます。</span><span class="sxs-lookup"><span data-stu-id="66da9-245">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="66da9-246">必要に応じて、以下の要件を満たしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="66da9-246">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="66da9-247">イマーシブ (VR) ヘッドセットの要件</span><span class="sxs-lookup"><span data-stu-id="66da9-247">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="66da9-248">以下のガイドラインは、イマーシブ (VR) ヘッドセットの *開発用 PC* に対する現在の最小かつ推奨仕様であり、定期的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="66da9-248">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC* , and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="66da9-249">この仕様を、 [PC ハードウェア互換性最小ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)と間違えないようにしてください。このガイドラインは、イマーシブ (VR) ヘッドセットのアプリまたはゲームの対象となる *コンシューマー PC の仕様* について説明するものです。</span><span class="sxs-lookup"><span data-stu-id="66da9-249">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="66da9-250">イマーシブ ヘッドセット開発用 PC にフルサイズの HDMI および/または USB 3.0 ポートがない場合、ヘッドセットを接続するための[アダプター](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)が必要になります。</span><span class="sxs-lookup"><span data-stu-id="66da9-250">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="66da9-251">一部のハードウェア構成、特にハイブリッド グラフィックスを搭載したノートブックなどには、現在[既知の問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)があります。</span><span class="sxs-lookup"><span data-stu-id="66da9-251">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="66da9-252">最小</span><span class="sxs-lookup"><span data-stu-id="66da9-252">Minimum</span></span></th><th> <span data-ttu-id="66da9-253">推奨</span><span class="sxs-lookup"><span data-stu-id="66da9-253">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="66da9-254">プロセッサ</span><span class="sxs-lookup"><span data-stu-id="66da9-254">Processor</span></span></td><td> <span data-ttu-id="66da9-255"><b>ノートブック:</b>Intel Mobile Core i5 第 7 世代 CPU、ハイパー スレッディング対応デュアルコア <b>デスクトップ:</b>Intel Desktop i5 第 6 世代 CPU、ハイパー スレッディング対応デュアルコア<b>または</b> AMD FX4350 4.2GHz クワッドコア相当</span><span class="sxs-lookup"><span data-stu-id="66da9-255"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="66da9-256"><b>デスクトップ:</b>Intel Desktop i7 第 6 世代 (6 コア) <b>または</b> AMD Ryzen 5 1600 (6 コア、12 スレッド)</span><span class="sxs-lookup"><span data-stu-id="66da9-256"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-257">GPU</span><span class="sxs-lookup"><span data-stu-id="66da9-257">GPU</span></span></td><td> <span data-ttu-id="66da9-258"><b>ノートブック:</b>NVIDIA GTX 965M、AMD RX 460M (2 GB) 相当またはそれ以上の DX12 対応 GPU <b>デスクトップ:</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="66da9-258"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="66da9-259"><b>デスクトップ:</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 相当またはそれ以上の DX12 対応 GPU</span><span class="sxs-lookup"><span data-stu-id="66da9-259"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-260">GPU ドライバー WDDM バージョン</span><span class="sxs-lookup"><span data-stu-id="66da9-260">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="66da9-261">WDDM 2.2 ドライバー</span><span class="sxs-lookup"><span data-stu-id="66da9-261">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-262">熱設計電力</span><span class="sxs-lookup"><span data-stu-id="66da9-262">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="66da9-263">15 W 以上</span><span class="sxs-lookup"><span data-stu-id="66da9-263">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-264">グラフィックス表示ポート</span><span class="sxs-lookup"><span data-stu-id="66da9-264">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="66da9-265">ヘッドセット用の使用可能なグラフィックス ディスプレイ ポート (60 Hz ヘッドセットの場合は HDMI 1.4 または DisplayPort 1.2、90 Hz ヘッドセットの場合は HDMI 2.0 または DisplayPort 1.2) x 1</span><span class="sxs-lookup"><span data-stu-id="66da9-265">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-266">画面の解像度</span><span class="sxs-lookup"><span data-stu-id="66da9-266">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="66da9-267">解像度:SVGA (800 x 600) 以上のビットの深度:1 ピクセルあたり 32 ビット色</span><span class="sxs-lookup"><span data-stu-id="66da9-267">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-268">メモリ</span><span class="sxs-lookup"><span data-stu-id="66da9-268">Memory</span></span></td><td> <span data-ttu-id="66da9-269">8&#160;GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="66da9-269">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="66da9-270">16 GB 以上の RAM</span><span class="sxs-lookup"><span data-stu-id="66da9-270">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-271">記憶域</span><span class="sxs-lookup"><span data-stu-id="66da9-271">Storage</span></span></td><td colspan="2"> <span data-ttu-id="66da9-272">&gt;10 GB の追加の空き領域</span><span class="sxs-lookup"><span data-stu-id="66da9-272">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-273">USB ポート</span><span class="sxs-lookup"><span data-stu-id="66da9-273">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="66da9-274">ヘッドセット (USB 3.0 Type-A) の使用可能な USB ポート x 1<b>メモ:USB は、最低 900 mA を給電する必要があります</b></span><span class="sxs-lookup"><span data-stu-id="66da9-274">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="66da9-275">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="66da9-275">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="66da9-276">Bluetooth 4.0 (アクセサリ接続用)</span><span class="sxs-lookup"><span data-stu-id="66da9-276">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="66da9-277">MRTK を使用したネイティブ開発を初めて行う場合は、整理されたネイティブ開発体験に従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="66da9-277">If you're new to Native development with MRTK, we recommend following our curated Native development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="66da9-278">ネイティブの体験を開始する</span><span class="sxs-lookup"><span data-stu-id="66da9-278">Start your Native journey</span></span>](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="66da9-279">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="66da9-279">Next Development Checkpoint</span></span>

<span data-ttu-id="66da9-280">私たちが用意したネイティブ開発チェックポイント体験に従っている場合、次のタスクは HoloLens 2 の開発環境を構成することです。</span><span class="sxs-lookup"><span data-stu-id="66da9-280">If you're following the Native development checkpoint journey we've laid out, your next task is to configure your development environment for HoloLens 2.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="66da9-281">HoloLens 2 の設定</span><span class="sxs-lookup"><span data-stu-id="66da9-281">Setup for HoloLens 2</span></span>](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

<span data-ttu-id="66da9-282">いつでも[開発チェックポイント](../native/directx-development-overview.md#1-getting-started)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="66da9-282">You can always go back to the [Native development checkpoints](../native/directx-development-overview.md#1-getting-started) at any time.</span></span>
