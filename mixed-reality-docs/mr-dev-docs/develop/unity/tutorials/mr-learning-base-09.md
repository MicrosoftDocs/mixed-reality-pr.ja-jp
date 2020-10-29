---
title: 入門チュートリアル - 9. 音声コマンドの使用
description: Mixed Reality ツールキット (MRTK) を使用して Mixed Reality アプリケーションを作成する方法について学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: d9ddf3d234b68dfe4ce3ab5c9272566479edd71d
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91700914"
---
# <a name="9-using-speech-commands"></a>9.音声コマンドの使用

## <a name="overview"></a>概要

このチュートリアルでは、音声コマンドを作成する方法と、それらをグローバルに制御する方法について説明します。 また、音声コマンドを制御するオブジェクトをユーザーが確認する必要があるローカルの音声コマンドを制御する方法についても説明します。

## <a name="objectives"></a>目標

* 音声コマンドを作成する方法について説明します
* 音声コマンドをグローバルおよびローカルで制御する方法について説明します

## <a name="ensuring-the-microphone-capability-is-enabled"></a>マイク機能が有効になっていることを確認する

[Unity] メニューで、[Mixed Reality Toolkit] > [Utilities]\(ユーティリティ\) > **[Configure Unity Project]\(Unity プロジェクトの構成\)** をクリックして **[MRTK Project Configurator]** ウィンドウを開き、 **[UWP Capabilities]\(UWP 機能\)** セクションで **[Enable Microphone Capability]\(マイク機能を有効にする\)** がグレーで表示されていることを確認します。

![マイク機能を有効にする](images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> このチュートリアル シリーズの冒頭で Unity プロジェクトを構成したときに、[MRTK Project Configurator 設定を適用する](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings)手順中にマイク機能を有効にしておく必要がありました。 しかし、有効にしていない場合は、ここで有効にしてください。

## <a name="creating-speech-commands"></a>音声コマンドを作成する

[階層] ウィンドウで **[MixedRealityToolkit]** オブジェクトを選択し、[インスペクター] ウィンドウで [MixedRealityToolkit] > **[入力]** タブを選択して、次の手順に従います。

* **[Speech]\(音声\)** セクションを展開します
* **DefaultMixedRealitySpeechCommandsProfile** を複製し、適切な名前 (たとえば、 _GettingStarted_MixedRealitySpeechCommandsProfile_ ) を指定します
* **[Start Behaviour]\(開始動作\)** が **[Auto Start]\(自動開始\)** に設定されていることを確認します

![音声コマンドを作成する](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> MRTK プロファイルを複製する方法については、[MRTK プロファイルの構成](mr-learning-base-03.md)に関するページにある手順を参照してください。

[Speech]\(音声\) > **[Speech Commands]\(音声コマンド\)** セクションで、 **[+Add a New Speech Command]\(新しい音声コマンドの追加\)** ボタンを 4 回クリックして、既存の音声コマンドの一覧に新しい音声コマンドを 4 つ追加します。次に、 **[Keyword]\(キーワード\)** フィールドに次の語句を入力します。

* Enable Indicator\(インジケーターの有効化\)
* Enable Tap to Place\(タップの有効化\)
* Enable Bounding Box\(境界ボックスの有効化\)
* Disable Bounding Box\(境界ボックスの無効化\)

![新しい音声コマンドを追加する](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> コンピューターにマイクが搭載されていない場合は、音声コマンドにキーコードを割り当てることができます。これにより、対応するキーが押されたときにそれらをトリガーできます。

## <a name="controlling-speech-commands"></a>音声コマンドを制御する

[プロジェクト] ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK]**  >  **[SDK]**  >  **[Features]\(機能\)**  >  **[UX]**  >  **[Prefabs]\(プレハブ\)**  >  **[ToolTip]\(ヒント\)** フォルダーの順に移動して、ヒント プレハブを見つけます。

![[ToolTip]\(ヒント\) フォルダーを開く](images/mr-learning-base/base-09-section3-step1-1.png)

[階層] ウィンドウで空の領域を右クリックし、 **[Create Empty]\(空を作成\)** を選択してシーンに空のオブジェクトを追加します。

プロジェクトに **SpeechInputHandler_Global** という名前を指定します。次に、[インスペクター] ウィンドウで、 **[コンポーネントの追加]** ボタンを使用して **[SpeechInputHandler]** コンポーネントを追加し、次のように構成します。

* **[Is Focus Required]\(フォーカスが必要\)** チェックボックスを **オフ** にして、ユーザーが SpeechInputHandler コンポーネントを使用してオブジェクトを確認しなくても音声コマンドをトリガーできるようにします
* [プロジェクト] ウィンドウで、 **[Speech Confirmation Tooltip Prefab]\(Speech Confirmation ヒント プレハブ\)** フィールドに **SpeechConfirmation Tooltip** プレハブを割り当てて、音声コマンドが認識されるとこのプレハブが表示されるようにします

![音声入力ハンドラー コンポーネントを構成する](images/mr-learning-base/base-09-section3-step1-2.png)

SpeechInputHandler コンポーネントで、小さい **+** アイコンを 3 回クリックして、3 つのキーワード要素を追加します。

![音声入力ハンドラーにキーワード要素を追加する](images/mr-learning-base/base-09-section3-step1-3.png)

**[Element 0]\(要素 0\)** を展開し、次のように構成します。

* **[Keyword]\(キーワード\)** フィールドに「 **Enable Indicator\(インジケーターの有効化\)** 」と入力して、前のセクションで作成した [Enable Indicator]\(インジケーターの有効化\) 音声コマンドを参照します
* 小さい **+** アイコンをクリックして、イベントを追加します
* [階層] ウィンドウで、 **[None (Object)]\(なし (オブジェクト)\)** フィールドに **Indicator** オブジェクトを割り当てます
* **[No Function]\(関数なし\)** ドロップダウンから、 **[GameObject]**  >  **[SetActive (bool)]** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します
* 引数チェックボックスが **オン** になっていることを確認します

![キーワード要素 0 を構成する](images/mr-learning-base/base-09-section3-step1-4.png)

**[Element 1]\(要素 1\)** を展開し、次のように構成します。

* **[Keyword]\(キーワード\)** フィールドに「 **Enable Bounding Box\(境界ボックスの有効化\)** 」と入力して、前のセクションで作成した [Enable Bounding Box]\(境界ボックスの有効化\) コマンドを参照します
* 小さい **+** アイコンをクリックして、イベントを追加します
* [階層] ウィンドウで、 **[None (Object)]\(なし (オブジェクト)\)** フィールドに **RoverExplorer** オブジェクトを割り当てます
* **[No Function]\(関数なし\)** ドロップダウンから、 **[BoundingBox]**  >  **[bool enabled]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします
* 引数チェックボックスが **オン** になっていることを確認します
* 小さい **[+]** アイコンをクリックして、別のイベントを追加します
* [階層] ウィンドウで、 **[None (Object)]\(なし (オブジェクト)\)** フィールドに **RoverExplorer** オブジェクトを割り当てます
* **[No Function]\(関数なし\)** ドロップダウンから、 **[ObjectManipulator]**  >  **[bool enabled]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします
* 引数チェックボックスが **オン** になっていることを確認します

![キーワード要素 1 を構成する](images/mr-learning-base/base-09-section3-step1-5.png)

**[Element 2]\(要素 2\)** を展開し、次のように構成します。

* **[Keyword]\(キーワード\)** フィールドに「 **Disable Bounding Box\(境界ボックスの無効化\)** 」と入力して、前のセクションで作成した [Disable Bounding Box]\(境界ボックスの無効化\) コマンドを参照します
* 小さい **+** アイコンをクリックして、イベントを追加します
* [階層] ウィンドウで、 **[None (Object)]\(なし (オブジェクト)\)** フィールドに **RoverExplorer** オブジェクトを割り当てます
* **[No Function]\(関数なし\)** ドロップダウンから、 **[BoundingBox]**  >  **[bool enabled]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします
* 引数チェックボックスが **オフ** になっていることを確認します
* 小さい **[+]** アイコンをクリックして、別のイベントを追加します
* [階層] ウィンドウで、 **[None (Object)]\(なし (オブジェクト)\)** フィールドに **RoverExplorer** オブジェクトを割り当てます
* **[No Function]\(関数なし\)** ドロップダウンから、 **[ObjectManipulator]**  >  **[bool enabled]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします
* 引数チェックボックスが **オフ** になっていることを確認します

![キーワード要素 2 を構成する](images/mr-learning-base/base-09-section3-step1-6.png)

[階層] ウィンドウで、[RoverExplorer] > **[RoverAssembly]** オブジェクトの順に選択します。次に、[インスペクター] ウィンドウで、 **[コンポーネントの追加]** ボタンを使用して **[SpeechInputHandler]** コンポーネントを追加し、次のように構成します。

* **[Is Focus Required]\(フォーカスが必要\)** チェックボックスが **オン** になっていることを確認します。これにより、ユーザーは音声コマンドをトリガーするために SpeechInputHandler コンポーネント (RoverAssembly) を使用してオブジェクトを確認する必要が生じます
* [プロジェクト] ウィンドウで、 **[Speech Confirmation Tooltip Prefab]\(Speech Confirmation ヒント プレハブ\)** フィールドに **SpeechConfirmation Tooltip** プレハブを割り当てて、音声コマンドが認識されるとこのプレハブが表示されるようにします

![探査車アセンブリに音声入力ハンドラーを追加する](images/mr-learning-base/base-09-section3-step1-7.png)

SpeechInputHandler コンポーネントで、小さい **+** アイコンをクリックしてキーワード要素を追加し、新しく作成された要素を展開して、次のように構成します。

* **[Keyword]\(キーワード\)** フィールドに「 **Enable Tap to Place\(タップの有効化\)** 」と入力して、前のセクションで作成した [Enable Tap to Place]\(タップの有効化\) コマンドを参照します
* 小さい **+** アイコンをクリックして、イベントを追加します
* [階層] ウィンドウで、 **[None (Object)]\(なし (オブジェクト)\)** フィールドにオブジェクト自体 (同じ **RoverAssembly** オブジェクト) を割り当てます
* **[No Function]\(関数なし\)** ドロップダウンから、 **TapToPlace** >  **[bool enabled]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします
* 引数チェックボックスが **オン** になっていることを確認します

![探査車アセンブリで音声入力ハンドラーを構成する](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a>結論

このチュートリアルでは、音声コマンドを作成する方法と、それらをグローバルに制御する方法について学習しました。 音声コマンドを制御するオブジェクトをユーザーが確認する必要があるローカルの音声コマンドを制御する方法についても学習しました。

また、[入門チュートリアル](mr-learning-base-01.md) シリーズも終了しました。 これらのチュートリアルでは、MRTK を使用して最初から完全な mixed reality エクスペリエンスを正常に構築できました。

次の [Azure Spatial Anchors のチュートリアル](mr-learning-asa-01.md)と[マルチユーザー機能のチュートリアル](mr-learning-sharing-01.md)の 2 つのチュートリアル シリーズでは、まず、Azure Spatial Anchors をプロジェクトに統合して、実際に作成した Rover Explorer のエクスペリエンスを固定する方法を学習します。 次に、ユーザーとオブジェクトの移動をリアルタイムで共有するために、マルチユーザー機能をプロジェクトに追加する方法を学習します。

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

私たちが用意した Unity 開発チェックポイント体験に従っている場合、次のタスクは Mixed Reality アプリのコア構成要素に慣れることです。

> [!div class="nextstepaction"]
> [基本的な対話式操作](../mrtk-101.md)

いつでも [Unity 開発チェックポイント](../unity-development-overview.md#1-getting-started)に戻ることができます。

