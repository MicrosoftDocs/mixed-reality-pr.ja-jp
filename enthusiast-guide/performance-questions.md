---
title: パフォーマンスに関する FAQ
description: パフォーマンスに関する Windows Mixed Reality のトラブルシューティングは、標準のコンシューマーサポートドキュメントを超えています。
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、トラブルシューティング、エラー、ヘルプ、サポート、パフォーマンス
appliesto:
- Windows 10
ms.openlocfilehash: dea2e81d53bfbb16a8803fc3f7c4e011741dfce6
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726003"
---
# <a name="performance-faqs"></a><span data-ttu-id="cfe28-104">パフォーマンスに関する FAQ</span><span class="sxs-lookup"><span data-stu-id="cfe28-104">Performance FAQs</span></span>

## <a name="is-my-windows-mixed-reality-headset-rendering-at-60-hz-or-90-hz-framerate"></a><span data-ttu-id="cfe28-105">Windows Mixed Reality ヘッドセットのレンダリングは 60 Hz または 90 Hz のフレームレートで表示されます</span><span class="sxs-lookup"><span data-stu-id="cfe28-105">Is my Windows Mixed Reality headset rendering at 60 Hz or 90-Hz framerate</span></span>

<span data-ttu-id="cfe28-106">HDMI 2.0 ポートを備えた独立した GPU と4つ以上の物理コアを搭載した CPU がある場合は、90 Hz である必要があります。</span><span class="sxs-lookup"><span data-stu-id="cfe28-106">If you have a discrete GPU with HDMI 2.0 ports and a CPU with four or more physical cores, you should be getting 90 Hz.</span></span> <span data-ttu-id="cfe28-107">確認するには、 **デバイスポータル >** の [パフォーマンス] タブを確認します。</span><span class="sxs-lookup"><span data-stu-id="cfe28-107">To confirm, check the **Device Portal > Performance** tab.</span></span>

<span data-ttu-id="cfe28-108">注: GPU に HDMI 1.4 出力しかない場合は、回避策として DisplayPort [2.0 アダプター](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="cfe28-108">Note: If your GPU only has an HDMI 1.4 output, you can use a DisplayPort to [HDMI 2.0 adapter](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) as a workaround.</span></span>

<span data-ttu-id="cfe28-109">注: "ヘッドセット表示" のビジュアル品質設定は、Windows Mixed Reality ホームエクスペリエンスのレンダリングにのみ影響します。</span><span class="sxs-lookup"><span data-stu-id="cfe28-109">Note: The visual quality settings in "Headset display" only affect the rendering of the Windows Mixed Reality home experience.</span></span>

## <a name="my-pc-is-running-slowly"></a><span data-ttu-id="cfe28-110">PC の動作が遅くなっています</span><span class="sxs-lookup"><span data-stu-id="cfe28-110">My PC is running slowly</span></span>

<span data-ttu-id="cfe28-111">システムは多くの理由で低速である可能性があり、通常はわずか数秒で持続します。</span><span class="sxs-lookup"><span data-stu-id="cfe28-111">The system may be slow for many reasons, usually lasting only a few seconds.</span></span> <span data-ttu-id="cfe28-112">長時間にわたってこの問題が発生する場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="cfe28-112">If you experience this problem over long periods of time:</span></span>

1. <span data-ttu-id="cfe28-113">デスクトップ上の未使用のアプリケーションをすべて閉じます。</span><span class="sxs-lookup"><span data-stu-id="cfe28-113">Close all unused application on the desktop.</span></span>
2. <span data-ttu-id="cfe28-114">ラップトップが電源に接続されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cfe28-114">Ensure that your laptop is plugged into a power source.</span></span>
3. <span data-ttu-id="cfe28-115">PC がウォームアップしていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="cfe28-115">Make sure that the PC isn't warming up.</span></span>
4. <span data-ttu-id="cfe28-116">Windows Mixed Reality ホームのビジュアル品質を下げます。</span><span class="sxs-lookup"><span data-stu-id="cfe28-116">Lower the visual quality in your Windows Mixed Reality home.</span></span>
5. <span data-ttu-id="cfe28-117">PC 用の最新の [グラフィックスドライバー](other-questions.md#my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors) があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cfe28-117">Ensure that you have the latest [graphics drivers](other-questions.md#my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors) for your PC.</span></span>

## <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a><span data-ttu-id="cfe28-118">私の PC は、Mixed Reality エクスペリエンスを実行するとウォームアップしています。</span><span class="sxs-lookup"><span data-stu-id="cfe28-118">My PC is warming up as I run the Mixed Reality experiences.</span></span> <span data-ttu-id="cfe28-119">操作方法クールに保つ</span><span class="sxs-lookup"><span data-stu-id="cfe28-119">How do I keep it cool</span></span>

1. <span data-ttu-id="cfe28-120">バッテリが充電され、電源が接続されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cfe28-120">Check that the battery is charged and the power source is plugged in.</span></span>
2. <span data-ttu-id="cfe28-121">PC ファンがブロックされていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="cfe28-121">Make sure that the PC fans aren't blocked.</span></span>
3. <span data-ttu-id="cfe28-122">比較的クールな環境で PC を使用します。</span><span class="sxs-lookup"><span data-stu-id="cfe28-122">Use the PC in a relatively cool environment.</span></span>
4. <span data-ttu-id="cfe28-123">PC で指されている熱源 (太陽や熱源など) がないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="cfe28-123">Make sure there are no heat sources (for example, the sun or heat vents) pointed at the PC.</span></span>

## <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a><span data-ttu-id="cfe28-124">視覚エフェクトが途切れている、読み込みに時間がかかる、または適切ではない</span><span class="sxs-lookup"><span data-stu-id="cfe28-124">My visuals are choppy, load slowly, or don't look good</span></span>

* <span data-ttu-id="cfe28-125">ヘッドセットが PC の正しいグラフィックスカードに接続されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cfe28-125">Make sure your headset is plugged into the correct graphics card on your PC.</span></span> <span data-ttu-id="cfe28-126">Pc によっては、統合グラフィックスカードと不連続グラフィックスカードの両方が搭載されています。</span><span class="sxs-lookup"><span data-stu-id="cfe28-126">Some PCs have both integrated and discrete graphics cards.</span></span> <span data-ttu-id="cfe28-127">通常、不連続カードは最適なパフォーマンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="cfe28-127">The discrete card will generally provide the best performance.</span></span> <span data-ttu-id="cfe28-128">[PC ハードウェアの詳細について](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)は、こちらを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cfe28-128">[Learn more about PC hardware](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).</span></span>
* <span data-ttu-id="cfe28-129">デスクトップで使用していないアプリケーションを閉じます。</span><span class="sxs-lookup"><span data-stu-id="cfe28-129">Close unused applications on your desktop.</span></span>
* <span data-ttu-id="cfe28-130">ヘッドセットがしっかり合っていることを確認します (下または右に移動するか、左右に移動します)。</span><span class="sxs-lookup"><span data-stu-id="cfe28-130">Make sure your headset fits snugly (move it lower and higher, or left and right, to adjust).</span></span>
* <span data-ttu-id="cfe28-131">[設定] で、ヘッドセットの表示設定を調整します。 **> Mixed reality > ヘッドセットの表示** になります。</span><span class="sxs-lookup"><span data-stu-id="cfe28-131">Adjust your headset's visual settings in **Settings > Mixed reality > Headset display**.</span></span> <span data-ttu-id="cfe28-132">"視覚品質" が "自動" に設定されている場合、PC の mixed reality エクスペリエンスが自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="cfe28-132">When "Visual quality" is set to "Automatic", the mixed reality experience for your PC will be chosen automatically.</span></span> <span data-ttu-id="cfe28-133">詳細を表示するには、"視覚品質" を "高" に設定します。</span><span class="sxs-lookup"><span data-stu-id="cfe28-133">For more visual detail, set "Visual quality" to "High".</span></span> <span data-ttu-id="cfe28-134">ビジュアルが途切れている場合は、下の設定を選択します。</span><span class="sxs-lookup"><span data-stu-id="cfe28-134">If your visuals are choppy, select a lower setting.</span></span>
* <span data-ttu-id="cfe28-135">ヘッドホン調整ノブを調整して、レンズが pupils (IPD) 間の正しい距離に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cfe28-135">Adjust the headset calibration knob to make sure that the lenses are set to the correct distance between your pupils (called IPD).</span></span> <span data-ttu-id="cfe28-136">IPD がわからない場合は、optometrist で測定できます。また、IPD を測定するために設計された web サイトを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="cfe28-136">If you don't know your IPD, an optometrist can measure it for you, or use a website designed to measure IPD.</span></span> <span data-ttu-id="cfe28-137">ヘッドセットに調整ノブがない場合は、[ **設定 > Mixed reality > ヘッドセットの表示** ] を選択し、[調整コントロール] を調整します。</span><span class="sxs-lookup"><span data-stu-id="cfe28-137">If the headset doesn't have a calibration knob, select **Settings > Mixed reality > Headset display** and adjust the "Calibration control".</span></span>
* <span data-ttu-id="cfe28-138">USB-C または DisplayPort を HDMI アダプターとして使用している場合は、別のアダプターを試してみてください。</span><span class="sxs-lookup"><span data-stu-id="cfe28-138">If you’re using a USB-C or DisplayPort to HDMI adapter, try a different one.</span></span> <span data-ttu-id="cfe28-139">[推奨されるアダプターを](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="cfe28-139">See [recommended adapters.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)</span></span>
* <span data-ttu-id="cfe28-140">PC のグラフィックスカードに接続されている可能性のある追加モニターを切断します。</span><span class="sxs-lookup"><span data-stu-id="cfe28-140">Disconnect any extra monitors that may be connected to your PC’s graphics card.</span></span>
* <span data-ttu-id="cfe28-141">Windows ストアからいくつかの異なる mixed reality アプリを試してみてください。コンピューターをセットアップすると、より適切に動作する場合があります。</span><span class="sxs-lookup"><span data-stu-id="cfe28-141">Try some different mixed reality apps from the Windows Store—some may work better with your computer setup.</span></span>
