---
title: 本能的な操作
description: Mixed Reality プラットフォーム全体に織り込まれている、シンプルで本能的な操作の理念について説明します。
author: shengkait
ms.author: shentan
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 視線入力, 視線入力ターゲット設定, 対話, 設計, HoloLens, MMR, マルチモーダル, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, HoloLens
ms.openlocfilehash: 37ac7475172977c8741c17817568cc9b5ad2a4e5
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847292"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="937bd-104">本能的な操作の概要</span><span class="sxs-lookup"><span data-stu-id="937bd-104">Introducing instinctual interactions</span></span>

![手で遠隔操作する](images/04_InteractionFundamentals.png)

<span data-ttu-id="937bd-106">シンプルで本能的な操作の理念は、Mixed Reality (MR) プラットフォーム全体に織り込まれています。</span><span class="sxs-lookup"><span data-stu-id="937bd-106">The philosophy of simple, instinctual interactions is interwoven throughout the mixed reality (MR) platform.</span></span> <span data-ttu-id="937bd-107">アプリケーションのデザイナーや開発者が顧客に簡単で直感的な操作を提供できるように、3 つの手順を使用しています。</span><span class="sxs-lookup"><span data-stu-id="937bd-107">We've taken three steps to ensure that application designers and developers can provide their customers with easy and intuitive interactions.</span></span> 

<span data-ttu-id="937bd-108">まず、センサーと入力テクノロジをまとめることで、マルチモーダル操作モデルを実現できるようにしました。</span><span class="sxs-lookup"><span data-stu-id="937bd-108">First, we've made sure our sensors and input technologies combine into multimodal interaction models.</span></span> <span data-ttu-id="937bd-109">これらの操作モデルには、自然言語による入力に加えて、手の追跡や視線の追跡が含まれます。</span><span class="sxs-lookup"><span data-stu-id="937bd-109">These interaction models include hand and eye tracking along with natural language input.</span></span> <span data-ttu-id="937bd-110">調査によれば、本能的なエクスペリエンスを作成する鍵となるのは、個々の入力をベースとせずに、マルチモーダル フレームワーク内で設計や開発を行うことです。</span><span class="sxs-lookup"><span data-stu-id="937bd-110">Based on our research, designing and developing within a multimodal framework (and not based on individual inputs) is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="937bd-111">2 つ目として、多くの開発者が複数の HoloLens デバイス (HoloLens 2 と HoloLens (第 1 世代) 、HoloLens と VR など) をターゲットにしていることを認識しています。</span><span class="sxs-lookup"><span data-stu-id="937bd-111">Second, we recognize that many developers target multiple HoloLens devices, such as HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span> <span data-ttu-id="937bd-112">このため、各デバイスで入力テクノロジが異なる場合でも、複数のデバイスで動作するように操作モデルを設計しています。</span><span class="sxs-lookup"><span data-stu-id="937bd-112">So we've designed our interaction models to work across devices, even if the input technology varies on each device.</span></span> <span data-ttu-id="937bd-113">たとえば、6DoF コントローラーを使用した Windows イマーシブ ヘッドセットや HoloLens 2 での遠隔インタラクションでは、どちらも同じアフォーダンスとパターンを使用しています。</span><span class="sxs-lookup"><span data-stu-id="937bd-113">For example, far interaction on a Windows Immersive headset with a 6DoF controller and HoloLens 2 both use identical affordances and patterns.</span></span> <span data-ttu-id="937bd-114">このため、クロスデバイスのアプリケーション開発が容易になり、ユーザー操作にも自然な感覚を実現できます。</span><span class="sxs-lookup"><span data-stu-id="937bd-114">This makes it easy for cross-device application development and provides a natural feel to user interactions.</span></span> 

<span data-ttu-id="937bd-115">MR では効果的で魅力的な魔法のような何千もの操作が実現できますが、ユーザーが成功と優れたエクスペリエンスを実感できる最善の方法は、アプリケーションで意図的に単一の操作モデルを使用することであることがわかっています。</span><span class="sxs-lookup"><span data-stu-id="937bd-115">While we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we've found that intentionally employing a single interaction model in an application is the best way to ensure users are successful and have a great experience.</span></span> <span data-ttu-id="937bd-116">そのため、この操作ガイドに次の 3 つのことを含めました。</span><span class="sxs-lookup"><span data-stu-id="937bd-116">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="937bd-117">3 つの主要な操作モデルと、それぞれに必要なコンポーネントとパターンに関する具体的なガイダンス。</span><span class="sxs-lookup"><span data-stu-id="937bd-117">Specific guidance around the three primary interaction models and the components and patterns required for each.</span></span>
* <span data-ttu-id="937bd-118">このプラットフォームが提供するその他のメリットに関する補足的なガイダンス。</span><span class="sxs-lookup"><span data-stu-id="937bd-118">Supplemental guidance about other benefits that our platform provides.</span></span>
* <span data-ttu-id="937bd-119">開発シナリオに適した操作モデルの選択に役立つ全般的なガイダンス。</span><span class="sxs-lookup"><span data-stu-id="937bd-119">General guidance to help select the appropriate interaction model for your development scenario.</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="937bd-120">マルチモーダル操作モデル</span><span class="sxs-lookup"><span data-stu-id="937bd-120">Multimodal interaction models</span></span>

<span data-ttu-id="937bd-121">調査とお客様からのフィードバックに基づき、3 つの主要な操作モデルが大半の Mixed Reality エクスペリエンスに適していることがわかりました。</span><span class="sxs-lookup"><span data-stu-id="937bd-121">Based on our research and feedback from customers, we've discovered that three primary interaction models suit most mixed reality experiences.</span></span> <span data-ttu-id="937bd-122">多くの点で、操作モデルはワークフローの完了方法に関するユーザーのメンタル モデルです。</span><span class="sxs-lookup"><span data-stu-id="937bd-122">In many ways, the interaction model is the user's mental model for how to complete a workflow.</span></span> <span data-ttu-id="937bd-123">各操作モデルは一連の顧客ニーズに合わせて最適化されており、適切に使用すれば、どれもが強力かつ便利に使用できます。</span><span class="sxs-lookup"><span data-stu-id="937bd-123">Each of these interaction models is optimized for a set of customer needs and is convenient, powerful, and usable when used correctly.</span></span> 

<span data-ttu-id="937bd-124">次の表は、簡単な概要です。</span><span class="sxs-lookup"><span data-stu-id="937bd-124">The chart below is a simplified overview.</span></span> <span data-ttu-id="937bd-125">各操作モデルを使用するための詳細情報は、イメージとコード サンプルを含むページにリンクしています。</span><span class="sxs-lookup"><span data-stu-id="937bd-125">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="937bd-126"><strong>Model</strong></span><span class="sxs-lookup"><span data-stu-id="937bd-126"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="937bd-127"><strong>シナリオ例</strong></span><span class="sxs-lookup"><span data-stu-id="937bd-127"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="937bd-128"><strong>適した使用方法</strong></span><span class="sxs-lookup"><span data-stu-id="937bd-128"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="937bd-129"><strong>ハードウェア</strong></span><span class="sxs-lookup"><span data-stu-id="937bd-129"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="937bd-130"><a href="hands-and-tools.md">手とモーション コントローラー</a></span><span class="sxs-lookup"><span data-stu-id="937bd-130"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="937bd-131">空間レイアウトやデザインなどの 3D 空間エクスペリエンス、コンテンツの操作、またはシミュレーション。</span><span class="sxs-lookup"><span data-stu-id="937bd-131">3D spatial experiences, such as spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="937bd-132">音声、視線追跡、頭の視線入力と組み合わせると、新しいユーザーに最適。</span><span class="sxs-lookup"><span data-stu-id="937bd-132">Great for new users coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="937bd-133">習得が容易。</span><span class="sxs-lookup"><span data-stu-id="937bd-133">Low learning curve.</span></span> <span data-ttu-id="937bd-134">手の追跡と 6 DoF コントローラーで一貫性のある UX。</span><span class="sxs-lookup"><span data-stu-id="937bd-134">Consistent UX across hand tracking and 6DoF controllers.</span></span></td>
        <td><span data-ttu-id="937bd-135">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="937bd-135">HoloLens 2</span></span><br><span data-ttu-id="937bd-136">イマーシブ ヘッドセット</span><span class="sxs-lookup"><span data-stu-id="937bd-136">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="937bd-137"><a href="hands-free.md">ハンズフリー</a></span><span class="sxs-lookup"><span data-stu-id="937bd-137"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="937bd-138">実地学習、メンテナンスなど、ユーザーの手がふさがっている場合のコンテキスト対応のエクスペリエンス。</span><span class="sxs-lookup"><span data-stu-id="937bd-138">Contextual experiences where a user's hands are occupied, such as on-the-job learning and maintenance.</span></span></td>
        <td><span data-ttu-id="937bd-139">いくらかの学習が必要。</span><span class="sxs-lookup"><span data-stu-id="937bd-139">Some learning required.</span></span> <span data-ttu-id="937bd-140">手が使用できない場合、デバイスにより音声と自然言語が組み合わされる。</span><span class="sxs-lookup"><span data-stu-id="937bd-140">If hands are unavailable, the device pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="937bd-141">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="937bd-141">HoloLens 2</span></span><br><span data-ttu-id="937bd-142">HoloLens (第 1 世代)</span><span class="sxs-lookup"><span data-stu-id="937bd-142">HoloLens (1st gen)</span></span><br><span data-ttu-id="937bd-143">イマーシブ ヘッドセット</span><span class="sxs-lookup"><span data-stu-id="937bd-143">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="937bd-144"><a href="gaze-and-commit.md">視線入力とコミット</a></span><span class="sxs-lookup"><span data-stu-id="937bd-144"><a href="gaze-and-commit.md">Gaze and commit</a></span></span></td>
        <td><span data-ttu-id="937bd-145">クリックスルー エクスペリエンス (3D プレゼンテーション、デモなど)。</span><span class="sxs-lookup"><span data-stu-id="937bd-145">Click-through experiences, for example, 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="937bd-146">移動を除く HMD のトレーニングが必要。</span><span class="sxs-lookup"><span data-stu-id="937bd-146">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="937bd-147">アクセシビリティ コントローラーに最適。</span><span class="sxs-lookup"><span data-stu-id="937bd-147">Best for accessible controllers.</span></span> <span data-ttu-id="937bd-148">HoloLens (第 1 世代) に最適。</span><span class="sxs-lookup"><span data-stu-id="937bd-148">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="937bd-149">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="937bd-149">HoloLens 2</span></span><br><span data-ttu-id="937bd-150">HoloLens (第 1 世代)</span><span class="sxs-lookup"><span data-stu-id="937bd-150">HoloLens (1st gen)</span></span><br><span data-ttu-id="937bd-151">イマーシブ ヘッドセット</span><span class="sxs-lookup"><span data-stu-id="937bd-151">Immersive headsets</span></span><br><span data-ttu-id="937bd-152">モバイル AR</span><span class="sxs-lookup"><span data-stu-id="937bd-152">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="937bd-153">ユーザー操作エクスペリエンスのギャップを避ける最善の方法は、1 つのモデルのガイダンスに最初から最後まで従うことです。</span><span class="sxs-lookup"><span data-stu-id="937bd-153">To avoid gaps in the user interaction experience, it's best to follow the guidance for a single model from beginning to end.</span></span>

<span data-ttu-id="937bd-154">次のセクションでは、これらの操作モデルからいずれかを選択して実装する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="937bd-154">The sections below walk through the steps for selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-youll-understand-our-guidance-on"></a><span data-ttu-id="937bd-155">このページでは、以下についてのガイダンスを理解することができます。</span><span class="sxs-lookup"><span data-stu-id="937bd-155">By the end of this page, you'll understand our guidance on:</span></span>
 
* <span data-ttu-id="937bd-156">顧客の操作モデルの選択</span><span class="sxs-lookup"><span data-stu-id="937bd-156">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="937bd-157">操作モデルの実装</span><span class="sxs-lookup"><span data-stu-id="937bd-157">Implementing the interaction model</span></span>
* <span data-ttu-id="937bd-158">操作モデル間の遷移</span><span class="sxs-lookup"><span data-stu-id="937bd-158">Transitioning between interaction models</span></span>
* <span data-ttu-id="937bd-159">次の手順の設計</span><span class="sxs-lookup"><span data-stu-id="937bd-159">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="937bd-160">顧客の操作モデルを選択する</span><span class="sxs-lookup"><span data-stu-id="937bd-160">Choose an interaction model for your customer</span></span>

<span data-ttu-id="937bd-161">通常、開発者と作成者は、顧客が使用できる操作の種類を考慮しています。</span><span class="sxs-lookup"><span data-stu-id="937bd-161">Typically, developers and creators have thought through the types of interactions that their customers can have.</span></span> <span data-ttu-id="937bd-162">顧客中心の設計アプローチを促進するために、次のガイダンスに従って、顧客向けに最適化された操作モデルを選択することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="937bd-162">To encourage a customer-focused approach to design, we recommend the following guidance for selecting the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="937bd-163">ガイダンスに従う理由</span><span class="sxs-lookup"><span data-stu-id="937bd-163">Why follow this guidance?</span></span>

* <span data-ttu-id="937bd-164">Microsoft が提供する操作モデルは、物理効果、認識効果、直感性、学習性など、主観的および客観的な基準でテストされています。</span><span class="sxs-lookup"><span data-stu-id="937bd-164">We test our interaction models for objective and subjective criteria, including physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="937bd-165">操作が異なるため、操作モデル間でビジュアルやオーディオのアフォーダンスやオブジェクトの動作が異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="937bd-165">Because interactions differ, visual/audio affordances and object behavior might differ between interaction models.</span></span>  
* <span data-ttu-id="937bd-166">ハンド レイと頭の視線カーソルを同時に使用するなど、複数の操作モデルの一部を組み合わせると、アフォーダンスが競合するリスクが発生します。</span><span class="sxs-lookup"><span data-stu-id="937bd-166">Combining parts of multiple interaction models creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor.</span></span> <span data-ttu-id="937bd-167">その結果、ユーザーが困惑したり混乱したりする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="937bd-167">This can overwhelm and confuse users.</span></span>

<span data-ttu-id="937bd-168">アフォーダンスと動作を最適化する例を操作モデルごとに示します。</span><span class="sxs-lookup"><span data-stu-id="937bd-168">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span> <span data-ttu-id="937bd-169">新しいユーザーから、 _「システムが動作していることはどうすればわかりますか」_ 、 _「何ができるかはどうすればわかりますか」_ 、 _「自分がしたことをシステムが理解していることはどうすればわかりますか」_ などの、よく似た質問をしばしば受けます。</span><span class="sxs-lookup"><span data-stu-id="937bd-169">We often see new users have similar questions, such as _"how do I know the system is working"_, _"how do I know what I can do"_, and _"how do I know if it understood what I just did?"_</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="937bd-170"><strong>Model</strong></span><span class="sxs-lookup"><span data-stu-id="937bd-170"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="937bd-171"><strong>動作していることはどうすればわかりますか?</strong></span><span class="sxs-lookup"><span data-stu-id="937bd-171"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="937bd-172"><strong>何ができるかはどうすればわかりますか?</strong></span><span class="sxs-lookup"><span data-stu-id="937bd-172"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="937bd-173"><strong>自分が何をしたかはどうすればわかりますか?</strong></span><span class="sxs-lookup"><span data-stu-id="937bd-173"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="937bd-174"><a href="hands-and-tools.md">手とモーション コントローラー</a></span><span class="sxs-lookup"><span data-stu-id="937bd-174"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="937bd-175">ハンド メッシュが見える、指先アフォーダンスまたは手やコントローラーの光線が見える。</span><span class="sxs-lookup"><span data-stu-id="937bd-175">I see a hand mesh, a fingertip affordance, or hand/controller rays.</span></span></td>
        <td><span data-ttu-id="937bd-176">オブジェクトに手を近づけると、グラブ可能なハンドルや境界ボックスが表示される。</span><span class="sxs-lookup"><span data-stu-id="937bd-176">I see grabbable handles, or a bounding box appears when my hand is near an object.</span></span></td>
        <td><span data-ttu-id="937bd-177">音が聞こえ、グラブやリリースのアニメーションが見える。</span><span class="sxs-lookup"><span data-stu-id="937bd-177">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="937bd-178"><a href="gaze-and-commit.md">頭の視線入力とコミット</a></span><span class="sxs-lookup"><span data-stu-id="937bd-178"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="937bd-179">視野の中央にカーソルが見える。</span><span class="sxs-lookup"><span data-stu-id="937bd-179">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="937bd-180">カーソルを特定のオブジェクトに重ねると、カーソルの状態が変わる。</span><span class="sxs-lookup"><span data-stu-id="937bd-180">The cursor changes state when it's over certain objects.</span></span></td>
        <td><span data-ttu-id="937bd-181">行動すると、視覚または音声でわかる。</span><span class="sxs-lookup"><span data-stu-id="937bd-181">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="937bd-182"><a href="hands-free.md">ハンズフリー (頭の視線入力とドウェル)</a></span><span class="sxs-lookup"><span data-stu-id="937bd-182"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="937bd-183">視野の中央にカーソルが見える。</span><span class="sxs-lookup"><span data-stu-id="937bd-183">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="937bd-184">インタラクティブなオブジェクトにドウェルすると、進行状況のインジケーターが見える。</span><span class="sxs-lookup"><span data-stu-id="937bd-184">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="937bd-185">行動すると、視覚または音声でわかる。</span><span class="sxs-lookup"><span data-stu-id="937bd-185">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="937bd-186"><a href="hands-free.md">ハンズフリー (音声コマンド)</a></span><span class="sxs-lookup"><span data-stu-id="937bd-186"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="937bd-187">リスニング インジケーターとシステムが聞いた音を表示するキャプションが見える。</span><span class="sxs-lookup"><span data-stu-id="937bd-187">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="937bd-188">音声プロンプトとヒントが聞こえる。</span><span class="sxs-lookup"><span data-stu-id="937bd-188">I get voice prompts and hints.</span></span> <span data-ttu-id="937bd-189">次のように言います。音声操作の項目</span><span class="sxs-lookup"><span data-stu-id="937bd-189">When I say: "What can I say?"</span></span> <span data-ttu-id="937bd-190">フィードバックが得られる。</span><span class="sxs-lookup"><span data-stu-id="937bd-190">I see feedback.</span></span></td>
        <td><span data-ttu-id="937bd-191">コマンドを与えると、視覚または音声でわかる。必要な場合は不明瞭解消用の UX が提供される。</span><span class="sxs-lookup"><span data-stu-id="937bd-191">I see/hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="937bd-192">ヘルプ チームが操作モデルを選択する際に使用している質問を次に示します。</span><span class="sxs-lookup"><span data-stu-id="937bd-192">Below are questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="937bd-193">Q:ユーザーがホログラムにタッチして細かい操作を行うことはありますか?</span><span class="sxs-lookup"><span data-stu-id="937bd-193">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="937bd-194">A:その場合は、厳密なターゲット指定や操作を行うために、手とモーション コントローラーの操作モデルを確認します。</span><span class="sxs-lookup"><span data-stu-id="937bd-194">A:  If so, check out the Hands and motion controllers interaction model for precision targeting and manipulation.</span></span>
 
2.  <span data-ttu-id="937bd-195">Q:ユーザーは、現実世界で作業を行うために、手を空けておく必要がありますか?</span><span class="sxs-lookup"><span data-stu-id="937bd-195">Q:  Do my users need to keep their hands free for real-world tasks?</span></span><br><br>
<span data-ttu-id="937bd-196">A:その場合は、ハンズフリー操作モデルを確認します。このモデルは、視線入力または音声ベースの操作で優れたハンズフリー エクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="937bd-196">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="937bd-197">Q:ユーザーには MR アプリケーションの操作を学習する時間はありますか? それとも、最低限の学習で操作を行う必要がありますか?</span><span class="sxs-lookup"><span data-stu-id="937bd-197">Q:  Do my users have time to learn interactions for my MR application or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="937bd-198">A:最低限の学習で最も直感的に操作を行いたい場合、ユーザーが手を使って操作できるのであれば、手とモーション コントローラーのモデルをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="937bd-198">A:  For the lowest learning curve and most intuitive interactions, we recommend the Hands and motion controllers model, as long as users can use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="937bd-199">Q:ユーザーがポイントしたり操作したりする際、モーション コントローラーを使用しますか?</span><span class="sxs-lookup"><span data-stu-id="937bd-199">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="937bd-200">A:手とモーション コントローラーのモデルには、モーション コントローラーを使用してすばらしいエクスペリエンスを実現するためのガイダンスがすべて含まれています。</span><span class="sxs-lookup"><span data-stu-id="937bd-200">A:  The Hands and motion controllers model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="937bd-201">Q:ユーザーは、アクセシビリティ コントローラーやクリッカーなどの一般的な Bluetooth コントローラーを使用しますか?</span><span class="sxs-lookup"><span data-stu-id="937bd-201">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="937bd-202">A:すべての非追跡コントローラーには、頭の視線入力とコミットのモデルをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="937bd-202">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span> <span data-ttu-id="937bd-203">ユーザーが単純な「ターゲット指定とコミット」機構によるエクスペリエンス全体を利用できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="937bd-203">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanism.</span></span> 
 
6.  <span data-ttu-id="937bd-204">Q:ユーザーは、UI コントロールが詰まったレイアウトを操作するのではなく、「クリックスルー」によってのみエクスペリエンスを進行させることができますか (たとえば、3D スライド ショーのような環境)?</span><span class="sxs-lookup"><span data-stu-id="937bd-204">Q: Do my users only progress through an experience by "clicking through" (for example in a 3D slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="937bd-205">A:ユーザーが多くの UI を制御する必要がない場合は、頭の視線入力とコミットを使うと、ターゲットの指定について悩むことなく学習できるオプションを提供できます。</span><span class="sxs-lookup"><span data-stu-id="937bd-205">A:  If users don't need to control a lot of UI, Head-gaze and commit offers a learnable option where users don't have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="937bd-206">Q:ユーザーは HoloLens (第 1 世代) と HoloLens 2/Windows Mixed Reality イマーシブ ヘッドセット (VR) の両方を使用しますか?</span><span class="sxs-lookup"><span data-stu-id="937bd-206">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/Windows Mixed Reality immersive headsets (VR)?</span></span><br><br>
<span data-ttu-id="937bd-207">A:頭の視線入力とコミットは HoloLens (第 1 世代) の操作モデルであるため、HoloLens (第 1 世代) をサポートする作成者は、ユーザーが HoloLens (第 1 世代) ヘッドセットを使用する可能性があるすべての機能やモードで、頭の視線入力とコミットを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="937bd-207">A:  Since Head-gaze and commit are the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users will experience on a HoloLens (1st gen) headset.</span></span> <span data-ttu-id="937bd-208">複数の世代の HoloLens で優れたエクスペリエンスを作成する詳しい方法については、"*操作モデルの遷移*" について取り上げた次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="937bd-208">See the next section on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="937bd-209">Q:移動可能 (広い領域をカバーする、またはスペース間を移動する) なユーザーと、1 つのスペースで作業することが多いユーザーを比較するとどうなりますか?</span><span class="sxs-lookup"><span data-stu-id="937bd-209">Q: What about users who are mobile, covering a large space or moving between spaces, versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="937bd-210">A:どの操作モデルでも、これらのユーザーに対応できます。</span><span class="sxs-lookup"><span data-stu-id="937bd-210">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="937bd-211">アプリの設計に特化したガイダンスは、[近日中に公開](../out-of-scope/news.md)します。</span><span class="sxs-lookup"><span data-stu-id="937bd-211">More guidance specific to app design [coming soon](../out-of-scope/news.md).</span></span>


## <a name="transitioning-interaction-models"></a><span data-ttu-id="937bd-212">操作モデルの遷移</span><span class="sxs-lookup"><span data-stu-id="937bd-212">Transitioning interaction models</span></span>
<span data-ttu-id="937bd-213">複数の操作モデルを使用することが必要になるユース ケースもあります。</span><span class="sxs-lookup"><span data-stu-id="937bd-213">There are also use cases that might require using more than one interaction model.</span></span> <span data-ttu-id="937bd-214">たとえば、アプリケーションの作成フローで "_手とモーション コントローラー_" 操作モデルを利用しつつ、現場技術者向けにはハンズフリー モードを使用する場合などです。</span><span class="sxs-lookup"><span data-stu-id="937bd-214">For example, your application's creation flow uses the _"hands and motion controllers"_ interaction model, but you want to employ a hands-free mode for field technicians.</span></span> <span data-ttu-id="937bd-215">エクスペリエンスに複数の操作モデルが必要な場合、ある操作モデルから別の操作モデルに切り替えるのをユーザー (特に、Mixed Reality を初めて使用するユーザー) が難しく感じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="937bd-215">If your experience does require multiple interaction models, users might have difficulty transitioning from one model to another, especially when they're new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="937bd-216">開発者やデザイナーが使用できるガイダンスの作成に常に取り組んでおり、複数の MR 操作モデルを使用するための方法、タイミング、および理由についてお知らせしています。</span><span class="sxs-lookup"><span data-stu-id="937bd-216">We're constantly working on more guidance that will be available to developers and designers, informing them about the how, when, and why for using multiple MR interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="937bd-217">関連項目</span><span class="sxs-lookup"><span data-stu-id="937bd-217">See also</span></span>
* [<span data-ttu-id="937bd-218">快適性</span><span class="sxs-lookup"><span data-stu-id="937bd-218">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="937bd-219">視線ベースの操作</span><span class="sxs-lookup"><span data-stu-id="937bd-219">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="937bd-220">HoloLens 2 上の視線追跡</span><span class="sxs-lookup"><span data-stu-id="937bd-220">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="937bd-221">視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="937bd-221">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="937bd-222">視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="937bd-222">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="937bd-223">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="937bd-223">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="937bd-224">手 - ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="937bd-224">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="937bd-225">手 - ポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="937bd-225">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="937bd-226">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="937bd-226">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="937bd-227">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="937bd-227">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="937bd-228">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="937bd-228">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="937bd-229">立体音響の設計</span><span class="sxs-lookup"><span data-stu-id="937bd-229">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="937bd-230">音声入力</span><span class="sxs-lookup"><span data-stu-id="937bd-230">Voice input</span></span>](voice-input.md)


