---
title: 本能的な操作
description: Mixed Reality プラットフォーム全体に織り込まれている、シンプルで本能的な操作の理念について説明します。
author: shengkait
ms.author: shentan
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 視線入力, 視線入力ターゲット設定, 対話, 設計, HoloLens, MMR, マルチモーダル, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, HoloLens
ms.openlocfilehash: a4b4c8fed9bb74b12bfa4390e1675acab44b3eec
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703168"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="dffff-104">本能的な操作の概要</span><span class="sxs-lookup"><span data-stu-id="dffff-104">Introducing instinctual interactions</span></span>

![手で遠隔操作する](images/04_InteractionFundamentals.png)

<span data-ttu-id="dffff-106">シンプルで本能的な操作の理念は、Mixed Reality (MR) プラットフォーム全体に織り込まれています。</span><span class="sxs-lookup"><span data-stu-id="dffff-106">The philosophy of simple, instinctual interactions is interwoven throughout the mixed reality (MR) platform.</span></span> <span data-ttu-id="dffff-107">アプリケーションのデザイナーや開発者が顧客に簡単で直感的な操作を提供できるように、3 つの手順を使用しています。</span><span class="sxs-lookup"><span data-stu-id="dffff-107">We've taken three steps to ensure that application designers and developers can provide their customers with easy and intuitive interactions.</span></span> 

<span data-ttu-id="dffff-108">1 つ目として、センサーと入力のテクノロジ (自然言語入力に加え、手の追跡と視線追跡が含まれます) をまとめることで、シームレスなマルチモーダル操作モデルを実現できるようにしました。</span><span class="sxs-lookup"><span data-stu-id="dffff-108">First, we've made sure our sensors and input technologies (which includes hand and eye tracking along with natural language input) combine into seamless, multimodal interaction models.</span></span>  
<span data-ttu-id="dffff-109">調査によれば、本能的なエクスペリエンスを作成する鍵となるのは、個々の入力をベースとせずに、マルチモーダル フレームワーク内で設計や開発を行うことです。</span><span class="sxs-lookup"><span data-stu-id="dffff-109">Based on our research, designing and developing within a multimodal framework (and not based on individual inputs) is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="dffff-110">2 つ目として、多くの開発者が複数の HoloLens デバイス (HoloLens 2 と HoloLens (第 1 世代) 、HoloLens と VR など) をターゲットにしていることを認識しています。</span><span class="sxs-lookup"><span data-stu-id="dffff-110">Second, we recognize that many developers target multiple HoloLens devices, such as HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  
<span data-ttu-id="dffff-111">このため、各デバイスで入力テクノロジが異なる場合でも、複数のデバイスで動作するように操作モデルを設計しています。</span><span class="sxs-lookup"><span data-stu-id="dffff-111">So we've designed our interaction models to work across devices, even if the input technology varies on each device.</span></span>  
<span data-ttu-id="dffff-112">たとえば、6DoF コントローラーによる Windows イマーシブ ヘッドセットの遠隔操作や、HoloLens 2 での遠隔操作は、どちらも同じアフォーダンスとパターンを使用しているため、クロスデバイス アプリケーションを簡単に開発して、自然なユーザー操作を実現できます。</span><span class="sxs-lookup"><span data-stu-id="dffff-112">For example, far interaction on a Windows Immersive headset with a 6DoF controller and far interaction on a HoloLens 2 both use identical affordances and patterns, making it easy for cross-device application development and providing a natural feel to user interactions.</span></span> 

<span data-ttu-id="dffff-113">MR では効果的で魅力的な魔法のような何千もの操作が実現できますが、ユーザーが成功と優れたエクスペリエンスを実感できる最善の方法は、アプリケーションで意図的にエンドツーエンドの単一操作モデルを使用することであることがわかっています。</span><span class="sxs-lookup"><span data-stu-id="dffff-113">While we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we've found that intentionally employing a single interaction model end-to-end in an application is the best way to ensure users are successful and have a great experience.</span></span> <span data-ttu-id="dffff-114">そのため、この操作ガイドに次の 3 つのことを含めました。</span><span class="sxs-lookup"><span data-stu-id="dffff-114">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="dffff-115">3 つの主要な操作モデルと、それぞれに必要なコンポーネントとパターンに関する具体的なガイダンス。</span><span class="sxs-lookup"><span data-stu-id="dffff-115">Specific guidance around the three primary interaction models and the components and patterns required for each.</span></span>
* <span data-ttu-id="dffff-116">このプラットフォームが提供するその他のメリットに関する補足的なガイダンス。</span><span class="sxs-lookup"><span data-stu-id="dffff-116">Supplemental guidance about other benefits that our platform provides.</span></span>
* <span data-ttu-id="dffff-117">開発シナリオに適した操作モデルの選択に役立つ全般的なガイダンス。</span><span class="sxs-lookup"><span data-stu-id="dffff-117">General guidance to help select the appropriate interaction model for your development scenario.</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="dffff-118">マルチモーダル操作モデル</span><span class="sxs-lookup"><span data-stu-id="dffff-118">Multimodal interaction models</span></span>

<span data-ttu-id="dffff-119">調査とお客様からのフィードバックに基づき、3 つの主要な操作モデルが大半の Mixed Reality エクスペリエンスに適していることがわかりました。</span><span class="sxs-lookup"><span data-stu-id="dffff-119">Based on our research and feedback from customers, we've discovered that three primary interaction models suit the majority of mixed reality experiences.</span></span> <span data-ttu-id="dffff-120">多くの点で、操作モデルはワークフローの完了方法に関するユーザーのメンタル モデルです。</span><span class="sxs-lookup"><span data-stu-id="dffff-120">In many ways, the interaction model is the user's mental model for how to complete a workflow.</span></span> <span data-ttu-id="dffff-121">各操作モデルは一連の顧客ニーズに合わせて最適化されており、適切に使用すれば、どれもが強力かつ便利に使用できます。</span><span class="sxs-lookup"><span data-stu-id="dffff-121">Each of these interaction models is optimized for a set of customer needs and is convenient, powerful, and usable when used correctly.</span></span> 

<span data-ttu-id="dffff-122">次の表は、簡単な概要です。</span><span class="sxs-lookup"><span data-stu-id="dffff-122">The chart below is a simplified overview.</span></span> <span data-ttu-id="dffff-123">各操作モデルを使用するための詳細情報は、イメージとコード サンプルを含むページにリンクしています。</span><span class="sxs-lookup"><span data-stu-id="dffff-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dffff-124"><strong>Model</strong></span><span class="sxs-lookup"><span data-stu-id="dffff-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="dffff-125"><strong>シナリオ例</strong></span><span class="sxs-lookup"><span data-stu-id="dffff-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="dffff-126"><strong>適した使用方法</strong></span><span class="sxs-lookup"><span data-stu-id="dffff-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="dffff-127"><strong>ハードウェア</strong></span><span class="sxs-lookup"><span data-stu-id="dffff-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dffff-128"><a href="hands-and-tools.md">手とモーション コントローラー</a></span><span class="sxs-lookup"><span data-stu-id="dffff-128"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="dffff-129">空間レイアウトやデザインなどの 3D 空間エクスペリエンス、コンテンツの操作、またはシミュレーション。</span><span class="sxs-lookup"><span data-stu-id="dffff-129">3D spatial experiences, such as spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="dffff-130">音声、視線追跡、頭の視線入力と組み合わせると、新しいユーザーに最適。</span><span class="sxs-lookup"><span data-stu-id="dffff-130">Great for new users coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="dffff-131">習得が容易。</span><span class="sxs-lookup"><span data-stu-id="dffff-131">Low learning curve.</span></span> <span data-ttu-id="dffff-132">手の追跡と 6 DoF コントローラーで一貫性のある UX。</span><span class="sxs-lookup"><span data-stu-id="dffff-132">Consistent UX across hand tracking and 6DoF controllers.</span></span></td>
        <td><span data-ttu-id="dffff-133">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="dffff-133">HoloLens 2</span></span><br><span data-ttu-id="dffff-134">イマーシブ ヘッドセット</span><span class="sxs-lookup"><span data-stu-id="dffff-134">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dffff-135"><a href="hands-free.md">ハンズフリー</a></span><span class="sxs-lookup"><span data-stu-id="dffff-135"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="dffff-136">実地学習、メンテナンスなど、ユーザーの手がふさがっている場合のコンテキスト対応のエクスペリエンス。</span><span class="sxs-lookup"><span data-stu-id="dffff-136">Contextual experiences where a user's hands are occupied, such as on-the-job learning and maintenance.</span></span></td>
        <td><span data-ttu-id="dffff-137">いくらかの学習が必要。</span><span class="sxs-lookup"><span data-stu-id="dffff-137">Some learning required.</span></span> <span data-ttu-id="dffff-138">手が使用できない場合、デバイスにより音声と自然言語が組み合わされる。</span><span class="sxs-lookup"><span data-stu-id="dffff-138">If hands are unavailable, the device pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="dffff-139">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="dffff-139">HoloLens 2</span></span><br><span data-ttu-id="dffff-140">HoloLens (第 1 世代)</span><span class="sxs-lookup"><span data-stu-id="dffff-140">HoloLens (1st gen)</span></span><br><span data-ttu-id="dffff-141">イマーシブ ヘッドセット</span><span class="sxs-lookup"><span data-stu-id="dffff-141">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dffff-142"><a href="gaze-and-commit.md">視線入力とコミット</a></span><span class="sxs-lookup"><span data-stu-id="dffff-142"><a href="gaze-and-commit.md">Gaze and commit</a></span></span></td>
        <td><span data-ttu-id="dffff-143">3D プレゼンテーション、デモなどのクリック スルー エクスペリエンス。</span><span class="sxs-lookup"><span data-stu-id="dffff-143">Click-through experiences, e.g. 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="dffff-144">移動を除く HMD のトレーニングが必要。</span><span class="sxs-lookup"><span data-stu-id="dffff-144">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="dffff-145">アクセシビリティ コントローラーに最適。</span><span class="sxs-lookup"><span data-stu-id="dffff-145">Best for accessible controllers.</span></span> <span data-ttu-id="dffff-146">HoloLens (第 1 世代) に最適。</span><span class="sxs-lookup"><span data-stu-id="dffff-146">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="dffff-147">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="dffff-147">HoloLens 2</span></span><br><span data-ttu-id="dffff-148">HoloLens (第 1 世代)</span><span class="sxs-lookup"><span data-stu-id="dffff-148">HoloLens (1st gen)</span></span><br><span data-ttu-id="dffff-149">イマーシブ ヘッドセット</span><span class="sxs-lookup"><span data-stu-id="dffff-149">Immersive headsets</span></span><br><span data-ttu-id="dffff-150">モバイル AR</span><span class="sxs-lookup"><span data-stu-id="dffff-150">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="dffff-151">ユーザー操作エクスペリエンスのギャップをなくす最善の方法は、1 つのモデルのガイダンスに最初から最後まで従うことです。</span><span class="sxs-lookup"><span data-stu-id="dffff-151">To ensure that there are no gaps in the user interaction experience, it is best to follow the guidance for a single model from beginning to end.</span></span>

<span data-ttu-id="dffff-152">次のセクションでは、これらの操作モデルからいずれかを選択して実装する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="dffff-152">The sections below walk through the steps for selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="dffff-153">このページでは、以下についてのガイダンスを理解することができます。</span><span class="sxs-lookup"><span data-stu-id="dffff-153">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="dffff-154">顧客の操作モデルの選択</span><span class="sxs-lookup"><span data-stu-id="dffff-154">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="dffff-155">操作モデルの実装</span><span class="sxs-lookup"><span data-stu-id="dffff-155">Implementing the interaction model</span></span>
* <span data-ttu-id="dffff-156">操作モデル間の遷移</span><span class="sxs-lookup"><span data-stu-id="dffff-156">Transitioning between interaction models</span></span>
* <span data-ttu-id="dffff-157">次の手順の設計</span><span class="sxs-lookup"><span data-stu-id="dffff-157">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="dffff-158">顧客の操作モデルを選択する</span><span class="sxs-lookup"><span data-stu-id="dffff-158">Choose an interaction model for your customer</span></span>

<span data-ttu-id="dffff-159">通常、開発者と作成者は、顧客が使用できる操作の種類を考慮しています。</span><span class="sxs-lookup"><span data-stu-id="dffff-159">Typically, developers and creators have thought through the types of interactions that their customers can have.</span></span> <span data-ttu-id="dffff-160">顧客中心の設計アプローチを促進するために、次のガイダンスに従って、顧客向けに最適化された操作モデルを選択することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="dffff-160">To encourage a customer-focused approach to design, we recommend the following guidance for selecting the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="dffff-161">ガイダンスに従う理由</span><span class="sxs-lookup"><span data-stu-id="dffff-161">Why follow this guidance?</span></span>

* <span data-ttu-id="dffff-162">操作モデルは、物理効果、認識効果、直感性、学習性など、主観的および客観的な基準でテストされます。</span><span class="sxs-lookup"><span data-stu-id="dffff-162">Our interaction models are tested for objective and subjective criteria, such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="dffff-163">操作が異なるため、操作モデル間でビジュアルやオーディオのアフォーダンスやオブジェクトの動作が異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dffff-163">Because interactions differ, visual/audio affordances and object behavior might differ between interaction models.</span></span>  
* <span data-ttu-id="dffff-164">ハンド レイと頭の視線カーソルを同時に使用するなど、複数の操作モデルの一部を組み合わせると、アフォーダンスが競合するリスクが発生します。</span><span class="sxs-lookup"><span data-stu-id="dffff-164">Combining parts of multiple interaction models creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor.</span></span> <span data-ttu-id="dffff-165">その結果、ユーザーが困惑したり混乱したりする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dffff-165">This can overwhelm and confuse users.</span></span>

<span data-ttu-id="dffff-166">アフォーダンスと動作を最適化する例を操作モデルごとに示します。</span><span class="sxs-lookup"><span data-stu-id="dffff-166">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span> <span data-ttu-id="dffff-167">新しいユーザーから、 _「システムが動作していることはどうすればわかりますか」_ 、 _「何ができるかはどうすればわかりますか」_ 、 _「自分がしたことをシステムが理解していることはどうすればわかりますか」_ などの、よく似た質問をしばしば受けます。</span><span class="sxs-lookup"><span data-stu-id="dffff-167">We often see new users have similar questions, such as _"how do I know the system is working"_, _"how do I know what I can do"_, and _"how do I know if it understood what I just did?"_</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dffff-168"><strong>Model</strong></span><span class="sxs-lookup"><span data-stu-id="dffff-168"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="dffff-169"><strong>動作していることはどうすればわかりますか?</strong></span><span class="sxs-lookup"><span data-stu-id="dffff-169"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="dffff-170"><strong>何ができるかはどうすればわかりますか?</strong></span><span class="sxs-lookup"><span data-stu-id="dffff-170"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="dffff-171"><strong>自分が何をしたかはどうすればわかりますか?</strong></span><span class="sxs-lookup"><span data-stu-id="dffff-171"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dffff-172"><a href="hands-and-tools.md">手とモーション コントローラー</a></span><span class="sxs-lookup"><span data-stu-id="dffff-172"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="dffff-173">ハンド メッシュが見える、指先アフォーダンスまたは手やコントローラーの光線が見える。</span><span class="sxs-lookup"><span data-stu-id="dffff-173">I see a hand mesh, a fingertip affordance, or hand/controller rays.</span></span></td>
        <td><span data-ttu-id="dffff-174">オブジェクトに手を近づけると、グラブ可能なハンドルや境界ボックスが表示される。</span><span class="sxs-lookup"><span data-stu-id="dffff-174">I see grabbable handles, or a bounding box appears when my hand is near an object.</span></span></td>
        <td><span data-ttu-id="dffff-175">音が聞こえ、グラブやリリースのアニメーションが見える。</span><span class="sxs-lookup"><span data-stu-id="dffff-175">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dffff-176"><a href="gaze-and-commit.md">頭の視線入力とコミット</a></span><span class="sxs-lookup"><span data-stu-id="dffff-176"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="dffff-177">視野の中央にカーソルが見える。</span><span class="sxs-lookup"><span data-stu-id="dffff-177">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="dffff-178">カーソルを特定のオブジェクトに重ねると、カーソルの状態が変わる。</span><span class="sxs-lookup"><span data-stu-id="dffff-178">The cursor changes state when it's over certain objects.</span></span></td>
        <td><span data-ttu-id="dffff-179">行動すると、視覚または音声でわかる。</span><span class="sxs-lookup"><span data-stu-id="dffff-179">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="dffff-180"><a href="hands-free.md">ハンズフリー (頭の視線入力とドウェル)</a></span><span class="sxs-lookup"><span data-stu-id="dffff-180"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="dffff-181">視野の中央にカーソルが見える。</span><span class="sxs-lookup"><span data-stu-id="dffff-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="dffff-182">インタラクティブなオブジェクトにドウェルすると、進行状況のインジケーターが見える。</span><span class="sxs-lookup"><span data-stu-id="dffff-182">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="dffff-183">行動すると、視覚または音声でわかる。</span><span class="sxs-lookup"><span data-stu-id="dffff-183">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dffff-184"><a href="hands-free.md">ハンズフリー (音声コマンド)</a></span><span class="sxs-lookup"><span data-stu-id="dffff-184"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="dffff-185">リスニング インジケーターとシステムが聞いた音を表示するキャプションが見える。</span><span class="sxs-lookup"><span data-stu-id="dffff-185">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="dffff-186">音声プロンプトとヒントが聞こえる。</span><span class="sxs-lookup"><span data-stu-id="dffff-186">I get voice prompts and hints.</span></span> <span data-ttu-id="dffff-187">次のように言います。音声操作の項目</span><span class="sxs-lookup"><span data-stu-id="dffff-187">When I say: "What can I say?"</span></span> <span data-ttu-id="dffff-188">フィードバックが得られる。</span><span class="sxs-lookup"><span data-stu-id="dffff-188">I see feedback.</span></span></td>
        <td><span data-ttu-id="dffff-189">コマンドを与えると、視覚または音声でわかる。必要な場合は不明瞭解消用の UX が提供される。</span><span class="sxs-lookup"><span data-stu-id="dffff-189">I see/hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="dffff-190">ヘルプ チームが操作モデルを選択する際に使用している質問を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dffff-190">Below are questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="dffff-191">Q:ユーザーがホログラムにタッチして細かい操作を行うことはありますか?</span><span class="sxs-lookup"><span data-stu-id="dffff-191">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="dffff-192">A:その場合は、厳密なターゲット指定や操作を行うために、手とモーション コントローラーの操作モデルを確認します。</span><span class="sxs-lookup"><span data-stu-id="dffff-192">A:  If so, check out the Hands and motion controllers interaction model for precision targeting and manipulation.</span></span>
 
2.  <span data-ttu-id="dffff-193">Q:ユーザーは、現実世界で作業を行うために、手を空けておく必要がありますか?</span><span class="sxs-lookup"><span data-stu-id="dffff-193">Q:  Do my users need to keep their hands free for real-world tasks?</span></span><br><br>
<span data-ttu-id="dffff-194">A:その場合は、ハンズフリー操作モデルを確認します。このモデルは、視線入力または音声ベースの操作で優れたハンズフリー エクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="dffff-194">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="dffff-195">Q:ユーザーには MR アプリケーションの操作を学習する時間はありますか? それとも、最低限の学習で操作を行う必要がありますか?</span><span class="sxs-lookup"><span data-stu-id="dffff-195">Q:  Do my users have time to learn interactions for my MR application or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="dffff-196">A:最低限の学習で最も直感的に操作を行いたい場合、ユーザーが手を使って操作できるのであれば、手とモーション コントローラーのモデルをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="dffff-196">A:  For the lowest learning curve and most intuitive interactions, we recommend the Hands and motion controllers model, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="dffff-197">Q:ユーザーがポイントしたり操作したりする際、モーション コントローラーを使用しますか?</span><span class="sxs-lookup"><span data-stu-id="dffff-197">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="dffff-198">A:手とモーション コントローラーのモデルには、モーション コントローラーを使用してすばらしいエクスペリエンスを実現するためのガイダンスがすべて含まれています。</span><span class="sxs-lookup"><span data-stu-id="dffff-198">A:  The Hands and motion controllers model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="dffff-199">Q:ユーザーは、アクセシビリティ コントローラーやクリッカーなどの一般的な Bluetooth コントローラーを使用しますか?</span><span class="sxs-lookup"><span data-stu-id="dffff-199">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="dffff-200">A:すべての非追跡コントローラーには、頭の視線入力とコミットのモデルをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="dffff-200">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span> <span data-ttu-id="dffff-201">ユーザーが単純な「ターゲット指定とコミット」機構によるエクスペリエンス全体を利用できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="dffff-201">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanism.</span></span> 
 
6.  <span data-ttu-id="dffff-202">Q:ユーザーは、UI コントロールが詰まったレイアウトを操作するのではなく、「クリックスルー」によってのみエクスペリエンスを進行させることができますか (たとえば、3D スライド ショーのような環境)?</span><span class="sxs-lookup"><span data-stu-id="dffff-202">Q: Do my users only progress through an experience by "clicking through" (for example in a 3D slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="dffff-203">A:ユーザーが多くの UI を制御する必要がない場合は、頭の視線入力とコミットを使うと、ターゲットの指定について悩むことなく学習できるオプションを提供できます。</span><span class="sxs-lookup"><span data-stu-id="dffff-203">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="dffff-204">Q:ユーザーは HoloLens (第 1 世代) と HoloLens 2/Windows Mixed Reality イマーシブ ヘッドセット (VR) の両方を使用しますか?</span><span class="sxs-lookup"><span data-stu-id="dffff-204">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/Windows Mixed Reality immersive headsets (VR)?</span></span><br><br>
<span data-ttu-id="dffff-205">A:頭の視線入力とコミットは HoloLens (第 1 世代) の操作モデルであるため、HoloLens (第 1 世代) をサポートする作成者は、ユーザーが HoloLens (第 1 世代) ヘッドセットを使用する可能性があるすべての機能やモードで、頭の視線入力とコミットを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="dffff-205">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users will experience on a HoloLens (1st gen) headset.</span></span> <span data-ttu-id="dffff-206">複数の世代の HoloLens で優れたエクスペリエンスを作成する詳しい方法については、*操作モデルの遷移* について取り上げた次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dffff-206">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="dffff-207">Q:通常は移動可能 (広い領域をカバーする、またはスペース間を移動する) なユーザーと、1 つのスペースで作業することが多いユーザーを比較するとどうなりますか?</span><span class="sxs-lookup"><span data-stu-id="dffff-207">Q: What about users who are generally mobile, covering a large space or moving between spaces, versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="dffff-208">A:どの操作モデルでも、これらのユーザーに対応できます。</span><span class="sxs-lookup"><span data-stu-id="dffff-208">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="dffff-209">アプリの設計に特化したガイダンスは、[近日中に公開](../out-of-scope/news.md)します。</span><span class="sxs-lookup"><span data-stu-id="dffff-209">More guidance specific to app design [coming soon](../out-of-scope/news.md).</span></span>


## <a name="transitioning-interaction-models"></a><span data-ttu-id="dffff-210">操作モデルの遷移</span><span class="sxs-lookup"><span data-stu-id="dffff-210">Transitioning interaction models</span></span>
<span data-ttu-id="dffff-211">複数の操作モデルが必要になるユース ケースもあります。</span><span class="sxs-lookup"><span data-stu-id="dffff-211">There are also use cases that might require utilizing more than one interaction model.</span></span> <span data-ttu-id="dffff-212">たとえば、アプリケーションの作成フローで _"手とモーション コントローラー操作モデル"_ を利用しつつ、現場技術者向けにはハンズフリー モードを使用する場合などです。</span><span class="sxs-lookup"><span data-stu-id="dffff-212">For example, your application's creation flow utilizes the _"hands and motion controllers"_ interaction model, but you want to employ a hands-free mode for field technicians.</span></span>
<span data-ttu-id="dffff-213">エクスペリエンスに複数の操作モデルが必要な場合、あるモデルから別のモデルに遷移する際に、多くのユーザー (特に、Mixed Reality を初めて使用するユーザー) が困難を感じることに留意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dffff-213">If your experience does require multiple interaction models, please keep in mind that many users might encounter difficulty when transitioning from one model to another, especially users who are new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="dffff-214">開発者やデザイナーが使用できるガイダンスの作成に常に取り組んでおり、複数の MR 操作モデルを使用するための方法、タイミング、および理由についてお知らせしています。</span><span class="sxs-lookup"><span data-stu-id="dffff-214">We're constantly working on more guidance that will be available to developers and designers, informing them about the how, when, and why for using multiple MR interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="dffff-215">関連項目</span><span class="sxs-lookup"><span data-stu-id="dffff-215">See also</span></span>
* [<span data-ttu-id="dffff-216">快適性</span><span class="sxs-lookup"><span data-stu-id="dffff-216">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="dffff-217">視線ベースの操作</span><span class="sxs-lookup"><span data-stu-id="dffff-217">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="dffff-218">HoloLens 2 上の視線追跡</span><span class="sxs-lookup"><span data-stu-id="dffff-218">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="dffff-219">視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="dffff-219">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="dffff-220">視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="dffff-220">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="dffff-221">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="dffff-221">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="dffff-222">手 - ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="dffff-222">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="dffff-223">手 - ポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="dffff-223">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="dffff-224">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="dffff-224">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="dffff-225">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="dffff-225">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="dffff-226">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="dffff-226">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="dffff-227">立体音響の設計</span><span class="sxs-lookup"><span data-stu-id="dffff-227">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="dffff-228">音声入力</span><span class="sxs-lookup"><span data-stu-id="dffff-228">Voice input</span></span>](voice-input.md)


