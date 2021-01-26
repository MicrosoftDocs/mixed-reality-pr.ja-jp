---
title: 音声コマンドの使用
description: このコースでは、Mixed Reality Toolkit (MRTK) を使用して Mixed Reality アプリで音声コマンドを設定、作成、使用する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality Toolkit, UWP, 音声コマンド, 音声入力
ms.localizationpriority: high
ms.openlocfilehash: c052c3501ab34811f33f1f6464c8394669eebe77
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/21/2021
ms.locfileid: "98635450"
---
# <a name="9-using-speech-commands"></a><span data-ttu-id="12491-104">9.音声コマンドの使用</span><span class="sxs-lookup"><span data-stu-id="12491-104">9. Using speech commands</span></span>

<span data-ttu-id="12491-105">このチュートリアルでは、音声コマンドを作成する方法と、それらをグローバルに制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="12491-105">In this tutorial, you will learn how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="12491-106">また、音声コマンドを制御するオブジェクトをユーザーが確認する必要があるローカルの音声コマンドを制御する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="12491-106">You will also learn how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

## <a name="objectives"></a><span data-ttu-id="12491-107">目標</span><span class="sxs-lookup"><span data-stu-id="12491-107">Objectives</span></span>

* <span data-ttu-id="12491-108">音声コマンドを作成する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="12491-108">Learn how to create speech commands</span></span>
* <span data-ttu-id="12491-109">音声コマンドをグローバルおよびローカルで制御する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="12491-109">Learn how to control speech commands globally and locally</span></span>

## <a name="ensuring-the-microphone-capability-is-enabled"></a><span data-ttu-id="12491-110">マイク機能が有効になっていることを確認する</span><span class="sxs-lookup"><span data-stu-id="12491-110">Ensuring the Microphone capability is enabled</span></span>

<span data-ttu-id="12491-111">[Unity] メニューで、[Mixed Reality Toolkit] > [Utilities]\(ユーティリティ\) > **[Configure Unity Project]\(Unity プロジェクトの構成\)** をクリックして **[MRTK Project Configurator]** ウィンドウを開き、 **[UWP Capabilities]\(UWP 機能\)** セクションで **[Enable Microphone Capability]\(マイク機能を有効にする\)** がグレーで表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="12491-111">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![マイク機能を有効にする](images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="12491-113">このチュートリアル シリーズの冒頭で Unity プロジェクトを構成したときに、[MRTK Project Configurator 設定を適用する](mr-learning-base-02.md#creating-and-configuring-the-scene)手順中にマイク機能を有効にしておく必要がありました。</span><span class="sxs-lookup"><span data-stu-id="12491-113">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#creating-and-configuring-the-scene) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="12491-114">しかし、有効にしていない場合は、ここで有効にしてください。</span><span class="sxs-lookup"><span data-stu-id="12491-114">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="creating-speech-commands"></a><span data-ttu-id="12491-115">音声コマンドを作成する</span><span class="sxs-lookup"><span data-stu-id="12491-115">Creating speech commands</span></span>

<span data-ttu-id="12491-116">[階層] ウィンドウで **[MixedRealityToolkit]** オブジェクトを選択し、[インスペクター] ウィンドウで [MixedRealityToolkit] > **[入力]** タブを選択して、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="12491-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="12491-117">**[Speech]\(音声\)** セクションを展開します</span><span class="sxs-lookup"><span data-stu-id="12491-117">Expand the **Speech** section</span></span>
* <span data-ttu-id="12491-118">**DefaultMixedRealitySpeechCommandsProfile** を複製し、適切な名前 (たとえば、_GettingStarted_MixedRealitySpeechCommandsProfile_) を指定します</span><span class="sxs-lookup"><span data-stu-id="12491-118">Clone the **DefaultMixedRealitySpeechCommandsProfile** and give it a suitable name, for example, _GettingStarted_MixedRealitySpeechCommandsProfile_</span></span>
* <span data-ttu-id="12491-119">**[Start Behaviour]\(開始動作\)** が **[Auto Start]\(自動開始\)** に設定されていることを確認します</span><span class="sxs-lookup"><span data-stu-id="12491-119">Verify that **Start Behaviour** is set to **Auto Start**</span></span>

![音声コマンドを作成する](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="12491-121">MRTK プロファイルを複製する方法については、[MRTK プロファイルの構成](mr-learning-base-03.md)に関するページにある手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="12491-121">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="12491-122">[Speech]\(音声\) > **[Speech Commands]\(音声コマンド\)** セクションで、 **[+Add a New Speech Command]\(新しい音声コマンドの追加\)** ボタンを 4 回クリックして、既存の音声コマンドの一覧に新しい音声コマンドを 4 つ追加します。次に、 **[Keyword]\(キーワード\)** フィールドに次の語句を入力します。</span><span class="sxs-lookup"><span data-stu-id="12491-122">In the Speech > **Speech Commands** section, click the **+ Add a New Speech Command** button four times to add four new speech commands to the list of the existing speech commands, then in the **Keyword** fields enter the following phrases:</span></span>

* <span data-ttu-id="12491-123">Enable Indicator\(インジケーターの有効化\)</span><span class="sxs-lookup"><span data-stu-id="12491-123">Enable Indicator</span></span>
* <span data-ttu-id="12491-124">Enable Tap to Place\(タップの有効化\)</span><span class="sxs-lookup"><span data-stu-id="12491-124">Enable Tap to Place</span></span>
* <span data-ttu-id="12491-125">Enable Bounding Box\(境界ボックスの有効化\)</span><span class="sxs-lookup"><span data-stu-id="12491-125">Enable Bounding Box</span></span>
* <span data-ttu-id="12491-126">Disable Bounding Box\(境界ボックスの無効化\)</span><span class="sxs-lookup"><span data-stu-id="12491-126">Disable Bounding Box</span></span>

![新しい音声コマンドを追加する](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="12491-128">コンピューターにマイクが搭載されていない場合は、音声コマンドにキーコードを割り当てることができます。これにより、対応するキーが押されたときにそれらをトリガーできます。</span><span class="sxs-lookup"><span data-stu-id="12491-128">If your computer does not have a microphone you can assign a KeyCode to the speech commands, which will let you trigger them when the corresponding key is pressed.</span></span>

## <a name="controlling-speech-commands"></a><span data-ttu-id="12491-129">音声コマンドを制御する</span><span class="sxs-lookup"><span data-stu-id="12491-129">Controlling speech commands</span></span>

<span data-ttu-id="12491-130">[プロジェクト] ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK]**  >  **[SDK]**  >  **[Features]\(機能\)**  >  **[UX]**  >  **[Prefabs]\(プレハブ\)**  >  **[ToolTip]\(ヒント\)** フォルダーの順に移動して、ヒント プレハブを見つけます。</span><span class="sxs-lookup"><span data-stu-id="12491-130">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![[ToolTip]\(ヒント\) フォルダーを開く](images/mr-learning-base/base-09-section3-step1-1.png)

<span data-ttu-id="12491-132">[階層] ウィンドウで空の領域を右クリックし、 **[Create Empty]\(空を作成\)** を選択してシーンに空のオブジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="12491-132">In the Hierarchy window, right-click on an empty spot and select **Create Empty** to add an empty object to your scene.</span></span>

<span data-ttu-id="12491-133">プロジェクトに **SpeechInputHandler_Global** という名前を指定します。次に、[インスペクター] ウィンドウで、 **[コンポーネントの追加]** ボタンを使用して **[SpeechInputHandler]** コンポーネントを追加し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="12491-133">Name the object **SpeechInputHandler_Global**, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="12491-134">**[Is Focus Required]\(フォーカスが必要\)** チェックボックスを **オフ** にして、ユーザーが SpeechInputHandler コンポーネントを使用してオブジェクトを確認しなくても音声コマンドをトリガーできるようにします</span><span class="sxs-lookup"><span data-stu-id="12491-134">**Uncheck** the **Is Focus Required** checkbox, so the user is not required to look at the object with the SpeechInputHandler component to trigger the speech command</span></span>
* <span data-ttu-id="12491-135">[プロジェクト] ウィンドウで、 **[Speech Confirmation Tooltip Prefab]\(Speech Confirmation ヒント プレハブ\)** フィールドに **SpeechConfirmation Tooltip** プレハブを割り当てて、音声コマンドが認識されるとこのプレハブが表示されるようにします</span><span class="sxs-lookup"><span data-stu-id="12491-135">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![音声入力ハンドラー コンポーネントを構成する](images/mr-learning-base/base-09-section3-step1-2.png)

<span data-ttu-id="12491-137">SpeechInputHandler コンポーネントで、小さい **+** アイコンを 3 回クリックして、3 つのキーワード要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="12491-137">On the SpeechInputHandler component, click the small **+** icon three times to add three keyword elements:</span></span>

![音声入力ハンドラーにキーワード要素を追加する](images/mr-learning-base/base-09-section3-step1-3.png)

<span data-ttu-id="12491-139">**[Element 0]\(要素 0\)** を展開し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="12491-139">Expand **Element 0** and configure it as follows:</span></span>

* <span data-ttu-id="12491-140">**[Keyword]\(キーワード\)** フィールドに「**Enable Indicator\(インジケーターの有効化\)** 」と入力して、前のセクションで作成した [Enable Indicator]\(インジケーターの有効化\) 音声コマンドを参照します</span><span class="sxs-lookup"><span data-stu-id="12491-140">In the **Keyword** field, enter **Enable Indicator**, to reference the Enable Indicator speech command you created in the previous section</span></span>
* <span data-ttu-id="12491-141">小さい **+** アイコンをクリックして、イベントを追加します</span><span class="sxs-lookup"><span data-stu-id="12491-141">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="12491-142">[階層] ウィンドウで、 **[None (Object)]\(なし (オブジェクト)\)** フィールドに **Indicator** オブジェクトを割り当てます</span><span class="sxs-lookup"><span data-stu-id="12491-142">From the Hierarchy window, assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="12491-143">**[No Function]\(関数なし\)** ドロップダウンから、 **[GameObject]**  >  **[SetActive (bool)]** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します</span><span class="sxs-lookup"><span data-stu-id="12491-143">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="12491-144">引数チェックボックスが **オン** になっていることを確認します</span><span class="sxs-lookup"><span data-stu-id="12491-144">Check the argument checkbox, so it is **checked**</span></span>

![キーワード要素 0 を構成する](images/mr-learning-base/base-09-section3-step1-4.png)

<span data-ttu-id="12491-146">**[Element 1]\(要素 1\)** を展開し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="12491-146">Expand **Element 1** and configure it as follows:</span></span>

* <span data-ttu-id="12491-147">**[Keyword]\(キーワード\)** フィールドに「**Enable Bounding Box\(境界ボックスの有効化\)** 」と入力して、前のセクションで作成した [Enable Bounding Box]\(境界ボックスの有効化\) コマンドを参照します</span><span class="sxs-lookup"><span data-stu-id="12491-147">In the **Keyword** field, enter **Enable Bounding Box**, to reference the Enable Bounding Box command you created in the previous section</span></span>
* <span data-ttu-id="12491-148">小さい **+** アイコンをクリックして、イベントを追加します</span><span class="sxs-lookup"><span data-stu-id="12491-148">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="12491-149">[階層] ウィンドウで、 **[None (Object)]\(なし (オブジェクト)\)** フィールドに **RoverExplorer** オブジェクトを割り当てます</span><span class="sxs-lookup"><span data-stu-id="12491-149">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="12491-150">**[No Function]\(関数なし\)** ドロップダウンから、 **[BoundingBox]**  >  **[bool enabled]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします</span><span class="sxs-lookup"><span data-stu-id="12491-150">From the **No Function** dropdown, select **BoundingBox** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="12491-151">引数チェックボックスが **オン** になっていることを確認します</span><span class="sxs-lookup"><span data-stu-id="12491-151">Check the argument checkbox, so it is **checked**</span></span>
* <span data-ttu-id="12491-152">小さい **[+]** アイコンをクリックして、別のイベントを追加します</span><span class="sxs-lookup"><span data-stu-id="12491-152">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="12491-153">[階層] ウィンドウで、 **[None (Object)]\(なし (オブジェクト)\)** フィールドに **RoverExplorer** オブジェクトを割り当てます</span><span class="sxs-lookup"><span data-stu-id="12491-153">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="12491-154">**[No Function]\(関数なし\)** ドロップダウンから、 **[ObjectManipulator]**  >  **[bool enabled]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします</span><span class="sxs-lookup"><span data-stu-id="12491-154">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="12491-155">引数チェックボックスが **オン** になっていることを確認します</span><span class="sxs-lookup"><span data-stu-id="12491-155">Check the argument checkbox, so it is **checked**</span></span>

![キーワード要素 1 を構成する](images/mr-learning-base/base-09-section3-step1-5.png)

<span data-ttu-id="12491-157">**[Element 2]\(要素 2\)** を展開し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="12491-157">Expand **Element 2** and configure it as follows:</span></span>

* <span data-ttu-id="12491-158">**[Keyword]\(キーワード\)** フィールドに「**Disable Bounding Box\(境界ボックスの無効化\)** 」と入力して、前のセクションで作成した [Disable Bounding Box]\(境界ボックスの無効化\) コマンドを参照します</span><span class="sxs-lookup"><span data-stu-id="12491-158">In the **Keyword** field, enter **Disable Bounding Box**, to reference the Disable Bounding Box command you created in the previous section</span></span>
* <span data-ttu-id="12491-159">小さい **+** アイコンをクリックして、イベントを追加します</span><span class="sxs-lookup"><span data-stu-id="12491-159">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="12491-160">[階層] ウィンドウで、 **[None (Object)]\(なし (オブジェクト)\)** フィールドに **RoverExplorer** オブジェクトを割り当てます</span><span class="sxs-lookup"><span data-stu-id="12491-160">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="12491-161">**[No Function]\(関数なし\)** ドロップダウンから、 **[BoundingBox]**  >  **[bool enabled]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします</span><span class="sxs-lookup"><span data-stu-id="12491-161">From the **No Function** dropdown, select **BoundingBox** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="12491-162">引数チェックボックスが **オフ** になっていることを確認します</span><span class="sxs-lookup"><span data-stu-id="12491-162">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="12491-163">小さい **[+]** アイコンをクリックして、別のイベントを追加します</span><span class="sxs-lookup"><span data-stu-id="12491-163">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="12491-164">[階層] ウィンドウで、 **[None (Object)]\(なし (オブジェクト)\)** フィールドに **RoverExplorer** オブジェクトを割り当てます</span><span class="sxs-lookup"><span data-stu-id="12491-164">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="12491-165">**[No Function]\(関数なし\)** ドロップダウンから、 **[ObjectManipulator]**  >  **[bool enabled]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします</span><span class="sxs-lookup"><span data-stu-id="12491-165">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="12491-166">引数チェックボックスが **オフ** になっていることを確認します</span><span class="sxs-lookup"><span data-stu-id="12491-166">Verify that the argument checkbox is **unchecked**</span></span>

![キーワード要素 2 を構成する](images/mr-learning-base/base-09-section3-step1-6.png)

<span data-ttu-id="12491-168">[階層] ウィンドウで、[RoverExplorer] > **[RoverAssembly]** オブジェクトの順に選択します。次に、[インスペクター] ウィンドウで、 **[コンポーネントの追加]** ボタンを使用して **[SpeechInputHandler]** コンポーネントを追加し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="12491-168">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="12491-169">**[Is Focus Required]\(フォーカスが必要\)** チェックボックスが **オン** になっていることを確認します。これにより、ユーザーは音声コマンドをトリガーするために SpeechInputHandler コンポーネント (RoverAssembly) を使用してオブジェクトを確認する必要が生じます</span><span class="sxs-lookup"><span data-stu-id="12491-169">Verify that the **Is Focus Required** checkbox is **check**, so the user is required to look at the object with the SpeechInputHandler component, i.e., the RoverAssembly, to trigger the speech command</span></span>
* <span data-ttu-id="12491-170">[プロジェクト] ウィンドウで、 **[Speech Confirmation Tooltip Prefab]\(Speech Confirmation ヒント プレハブ\)** フィールドに **SpeechConfirmation Tooltip** プレハブを割り当てて、音声コマンドが認識されるとこのプレハブが表示されるようにします</span><span class="sxs-lookup"><span data-stu-id="12491-170">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![探査車アセンブリに音声入力ハンドラーを追加する](images/mr-learning-base/base-09-section3-step1-7.png)

<span data-ttu-id="12491-172">SpeechInputHandler コンポーネントで、小さい **+** アイコンをクリックしてキーワード要素を追加し、新しく作成された要素を展開して、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="12491-172">On the SpeechInputHandler component, click the small **+** icon to add a keyword element, expand the newly created element, then configure it as follows:</span></span>

* <span data-ttu-id="12491-173">**[Keyword]\(キーワード\)** フィールドに「**Enable Tap to Place\(タップの有効化\)** 」と入力して、前のセクションで作成した [Enable Tap to Place]\(タップの有効化\) コマンドを参照します</span><span class="sxs-lookup"><span data-stu-id="12491-173">In the **Keyword** field, enter **Enable Tap to Place**, to reference the Enable Tap to Place command you created in the previous section</span></span>
* <span data-ttu-id="12491-174">小さい **+** アイコンをクリックして、イベントを追加します</span><span class="sxs-lookup"><span data-stu-id="12491-174">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="12491-175">[階層] ウィンドウで、 **[None (Object)]\(なし (オブジェクト)\)** フィールドにオブジェクト自体 (同じ **RoverAssembly** オブジェクト) を割り当てます</span><span class="sxs-lookup"><span data-stu-id="12491-175">From the Hierarchy window, assign the object itself, i.e., the same **RoverAssembly** object, to the **None (Object)** field</span></span>
* <span data-ttu-id="12491-176">**[No Function]\(関数なし\)** ドロップダウンから、**TapToPlace** >  **[bool enabled]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします</span><span class="sxs-lookup"><span data-stu-id="12491-176">From the **No Function** dropdown, select **TapToPlace** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="12491-177">引数チェックボックスが **オン** になっていることを確認します</span><span class="sxs-lookup"><span data-stu-id="12491-177">Check the argument checkbox, so it is **checked**</span></span>

![探査車アセンブリで音声入力ハンドラーを構成する](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="12491-179">結論</span><span class="sxs-lookup"><span data-stu-id="12491-179">Congratulations</span></span>

<span data-ttu-id="12491-180">このチュートリアルでは、音声コマンドを作成する方法と、それらをグローバルに制御する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="12491-180">In this tutorial, you learned how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="12491-181">音声コマンドを制御するオブジェクトをユーザーが確認する必要があるローカルの音声コマンドを制御する方法についても学習しました。</span><span class="sxs-lookup"><span data-stu-id="12491-181">You also learned how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

<span data-ttu-id="12491-182">また、[入門チュートリアル](mr-learning-base-01.md) シリーズも終了しました。</span><span class="sxs-lookup"><span data-stu-id="12491-182">This also concludes the [Getting started tutorials](mr-learning-base-01.md) series.</span></span> <span data-ttu-id="12491-183">これらのチュートリアルでは、MRTK を使用して最初から完全な mixed reality エクスペリエンスを正常に構築できました。</span><span class="sxs-lookup"><span data-stu-id="12491-183">Through these tutorials, you have successfully built a complete mixed reality experience from scratch using the MRTK.</span></span>

<span data-ttu-id="12491-184">次の [Azure Spatial Anchors のチュートリアル](mr-learning-asa-01.md)と[マルチユーザー機能のチュートリアル](mr-learning-sharing-01.md)の 2 つのチュートリアル シリーズでは、まず、Azure Spatial Anchors をプロジェクトに統合して、実際に作成した Rover Explorer のエクスペリエンスを固定する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="12491-184">In the next two tutorial series, [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) and [Multi-user capabilities tutorials](mr-learning-sharing-01.md), you will first learn how to integrate Azure Spatial Anchors into your project to anchor the Rover Explorer experience you created in the real world.</span></span> <span data-ttu-id="12491-185">次に、ユーザーとオブジェクトの移動をリアルタイムで共有するために、マルチユーザー機能をプロジェクトに追加する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="12491-185">Then, you will learn how to add multi-user capabilities to your project to share user and object movements in real-time.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="12491-186">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="12491-186">Next Development Checkpoint</span></span>

<span data-ttu-id="12491-187">私たちが用意した Unity 開発チェックポイント体験に従っている場合、次のタスクは Mixed Reality アプリのコア構成要素に慣れることです。</span><span class="sxs-lookup"><span data-stu-id="12491-187">If you're following the Unity development checkpoint journey we've laid out, your next task is to familiarize yourself with core building blocks of Mixed Reality apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="12491-188">基本的な対話式操作</span><span class="sxs-lookup"><span data-stu-id="12491-188">Basic interactions</span></span>](../mrtk-101.md)

<span data-ttu-id="12491-189">いつでも [Unity 開発チェックポイント](../unity-development-overview.md#1-getting-started)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="12491-189">You can always go back to the [Unity development checkpoints](../unity-development-overview.md#1-getting-started) at any time.</span></span>
