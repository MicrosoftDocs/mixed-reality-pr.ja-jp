---
title: PC Holographic Remoting の概要
description: このコースを完了すると、Mixed Reality アプリケーションを PC から HoloLens 2 にリモート ストリーム配信する方法がわかります。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, PC Holographic Remoting, ヒント, 視線追跡
ms.localizationpriority: high
ms.openlocfilehash: 5a779ca03921701b2111e4ed5525b6f7bc250070
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590384"
---
# <a name="1-getting-started-with-pc-holographic-remoting"></a>1.PC Holographic Remoting の概要

HoloLens 2 のチュートリアルへようこそ。 2 部構成のこのチュートリアル シリーズでは、Mixed Reality エクスペリエンスのデモンストレーションを作成する方法と、Holographic Remoting 用の PC アプリを作成する方法について説明します。

このチュートリアルでは、Mixed Reality エクスペリエンスの作成方法について説明します。 このチュートリアルでは、UI 要素、3D モデルの操作、モデルのクリッピング、および視線追跡機能について説明します。

[Holographic Remoting アプリケーションの作成](mr-learning-pc-holographic-remoting-02.md)に関する 2 番目のチュートリアルでは、Holographic Remoting 用の PC アプリを作成する方法について説明します。 また、いつでも HoloLens 2 に接続して、Mixed Reality で 3D コンテンツを視覚化する方法についても説明します。

## <a name="objectives"></a>目標

* アセットをインポートし、シーンをセットアップする
* UI 要素とボタンを使用してホログラムを操作する
* クリッピング機能のために 3D オブジェクトを構成する
* 視線追跡を使用したヒントのアクティブ化について理解する

## <a name="prerequisites"></a>前提条件

* 正しい[ツールがインストールされている](../../install-the-tools.md)構成済みの Windows 10 PC
* C# プログラミングの基本知識
* [開発用に構成された](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス
* Unity 2019 LTS がマウントされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>

続行する前に、[入門チュートリアル](mr-learning-base-01.md) シリーズを完了するか、Unity および MRTK の基本操作を経験しておくことを **強くお勧め** します。

> [!IMPORTANT]
> * このチュートリアル シリーズで推奨されている Unity バージョンは、Unity 2019 LTS です。 これは、上でリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。
> * MRTK プロジェクトでの Holographic Remoting は、レガシ XR でのみ機能します。 現時点では、XR SDK はサポートされていません。

## <a name="creating-and-preparing-the-unity-project"></a>Unity プロジェクトの作成と準備

このセクションでは、新しい Unity プロジェクトを作成し、MRTK 開発用に準備します。

このためには、まず「[プロジェクトと最初のアプリケーションの初期化](mr-learning-base-02.md)」に従ってください (「[デバイスへのアプリケーションのビルド](mr-learning-base-02.md#building-your-application-to-your-hololens-2)」の手順は除く)。これには、次の手順が含まれます。

1. [Unity プロジェクトを作成](mr-learning-base-02.md#creating-the-unity-project)し、"*MRTK チュートリアル*" などの適切な名前を付ける

2. [ビルド プラットフォームを切り替える](mr-learning-base-02.md#switching-the-build-platform)

3. [TextMeshPro の重要なリソースをインポートする](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

4. [Mixed Reality Toolkit をインポートする](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

5. [Unity プロジェクトを構成する](mr-learning-base-02.md#configuring-the-unity-project)

6. [シーンを作成して設定](mr-learning-base-02.md#creating-and-configuring-the-scene)し、シーンに **PC Holographic Remoting** などの適切な名前を付ける

次に、「[空間認識表示オプションの変更](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)」の手順に従って、シーンの MRTK 構成プロファイルを **DefaultHoloLens2ConfigurationProfile** に変更します。 空間認識メッシュの表示オプションを **[オクルージョン]** に変更します。

## <a name="importing-the-tutorial-assets"></a>チュートリアルのアセットのインポート

[MRTK.Tutorials.PCHolographicRemoting.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/pc-holographic-remoting-v2.4.0/MRTK.Tutorials.PCHolographicRemoting.unitypackage) をダウンロードして **インポート** します。

>[!TIP]
> Unity カスタム パッケージをインポートする方法については、「[チュートリアルのアセットのインポート](mr-learning-base-04.md#importing-the-tutorial-assets)」の手順を参照してください。

チュートリアル アセットをインポートすると、[プロジェクト] ウィンドウは次のようになります。

![チュートリアルのアセットがインポートされた後の Unity の [Hierarchy]\(階層\)、[Scene]\(シーン\)、[Project]\(プロジェクト\) ウィンドウ](images/mrlearning-pc-holographic-remoting/Tutorial1-Section2-Step1-1.png)

## <a name="configuring-and-preparing-the-scene"></a>シーンの構成と準備

このセクションでは、チュートリアルのプレハブをいくつか追加してシーンを準備します。

[プロジェクト] ウィンドウで、 **[アセット]**  >  **[MRTK.Tutorials.PCHolograhicRemoting]**  >  **[Prefabs]\(プレハブ\)** フォルダーの順に移動します。 CTRL ボタンを押したまま、次の 6 つのプレハブをクリックします。

* ButtonParent
* ClippingObjects
* HandSpatialMapButton
* 手順
* ModelParent
* プラットフォーム

![選択されたシーンに追加されるプレハブが表示されている Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-1.png)

これらのモデルを、[Prefabs]\(プレハブ\) フォルダーから **[階層] ウィンドウ** にドラッグ アンド ドロップします。

![新しく追加されたプレハブがまだ選択されている Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-2.png)

シーン内のオブジェクトに焦点を合わせるには、**ModelParent** オブジェクトをダブルクリックして、もう一度少しズームインします。

![ModelParent オブジェクトにフォーカスがある Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-3.png)

> [!TIP]
> シーンに大きいアイコンが表示されている場合 (大きいフレームの 'T' アイコンが邪魔になる場合など)、<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">ギズモをオフに切り替える</a>ことによってこれらを非表示にすることができます。

## <a name="configuring-the-buttons-to-operate-the-scene"></a>シーンを操作するためのボタンの構成

このセクションでは、シーンにスクリプトを追加して、モデルの切り替えとクリッピング機能の基礎をデモンストレーションするボタン イベントを作成します。

### <a name="1-configuring-the-interactable-script-component"></a>1.Interactable (Script) コンポーネントの構成

[階層] ウィンドウで、**ButtonParent** オブジェクトを展開し、**NextButton** を選択します。 [インスペクター] ウィンドウで、**Interactable (Script)** コンポーネントを見つけて、**OnClick ()** イベントの下にある **+** アイコンをクリックします。

![NextButton OnClick イベントが追加された Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-1.png)

[階層] ウィンドウで **NextButton** オブジェクトを選択したまま、**ButtonParent** オブジェクトを [階層] ウィンドウから、先ほど追加した空の **[None (Object)]\(なし(オブジェクト)\)** フィールドにドラッグして、このボタンをクリックすることによって発生するボタン クリック イベントを ButtonParent オブジェクトがリッスンするようにします。

![NextButton OnClick イベント リスナーが構成された Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-2.png)

同じイベントの **[No Function]\(関数なし\)** ドロップダウンをクリックします。 次に、**ViewButtonControl** > **NextModel ()** の順に選択して、このボタンを押すことでボタン イベントが発生するときにトリガーされるアクションとして、**NextModel ()** 関数を設定します。

![NextButton OnClick イベント アクション選択パスが表示されている Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-3.png)

### <a name="2-configuring-the-remaining-buttons"></a>2.残りのボタンの構成

残りの各ボタンについて、上記の手順を完了して、**OnClick ()** イベントに関数を割り当てます。

* PreviousButton オブジェクトについては、**ViewButtonControl** > **PreviousModel ()** 関数の順に割り当てます。

* ClippingButton については、**ToggleButton** > **ToggleClipping ()** 関数の順に選択します。

### <a name="3-configuring-the-view-button-control-script--and-toggle-button-script-components"></a>3.View Button Control (Script) および Toggle Button (Script) コンポーネントの構成

これで、モデルの切り替えとクリッピング機能をデモンストレーションできるようにボタンが構成されました。 次に、3D モデルとクリッピング オブジェクトをスクリプトに追加します。

デモンストレーション用に 6 つの異なる 3D モデルが用意されています。***ModelParentobject*** を展開して、これらの 3D モデルを表示します。

[階層] ウィンドウで ButtonParent オブジェクトを選択したまま、[インスペクター] ウィンドウで、**View Button Control (Script)** コンポーネントを見つけて、**Models** 変数を展開します。

**[サイズ]** フィールドに、シーンに含める 3D モデルの数を入力します。 この例では、6 を入力します。 これで、新しい 3D モデルを追加するためのフィールドが作成されます。

![ViewButtonControl スクリプト コンポーネントのフィールドが表示されている Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-1.png)

ModelParent オブジェクトの子オブジェクトを、これらのフィールドにそれぞれドラッグ アンド ドロップします。

![ViewButtonControl スクリプト コンポーネントのフィールドが構成されている Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-2.png)

**ClippingObjects** オブジェクトを、[階層] ウィンドウから **Toggle Button (Script)** コンポーネントの **[Clipping Object]\(クリッピング オブジェクト\)** フィールドにドラッグ アンド ドロップします。
>[!NOTE]
>ボタンの親オブジェクトから移動しないようにします。

![ToggleButton スクリプト コンポーネントのフィールドが構成されている Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-3.png)

[階層] ウィンドウで **ClippingObjects** プレハブを選択して、[インスペクター] ウィンドウでそれを有効にし、そのクリッピング オブジェクトをオンにします。

## <a name="configuring-the-clipping-objects-to-enable-clipping-feature"></a>クリッピング機能を有効にするためのクリッピング オブジェクトの構成

このセクションでは、MarsCuriosityRover オブジェクトの子オブジェクト レンダラーを各クリッピング オブジェクトに追加して、MarsCuriosityRover モデルのクリッピングをデモンストレーションします。

[階層] ウィンドウで、**ClippingObjects** オブジェクトを展開して、このプロジェクトで使用する 3 つの異なるクリッピング オブジェクトを表示します。

**ClippingSphere** オブジェクトを構成するため、このオブジェクトをクリックし、[インスペクター] ウィンドウで **Clipping Sphere (Script)** コンポーネントを見つけます。 [サイズ] フィールドに、3D モデルに追加する必要があるレンダラーの数を入力します。 この場合は、MarsCuriosityRover 子オブジェクト用に 10 個追加します。 これで、レンダラーを追加するためのフィールドが作成されます。MarsCuriosityRover オブジェクトの子モデル オブジェクトをこれらのフィールドにドラッグ アンド ドロップします。

![ClippingSphere スクリプト コンポーネントのフィールドが構成されている Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section5-Step1-1.png)

同じプロセスに従って、MarsCuriosityRover の子オブジェクト レンダラーを **ClippingBox** および **ClippingPlane** オブジェクトに追加します。

このチュートリアルでは、クリッピング機能のデモンストレーションに MarsCuriosityRover モデルのみを使用します。 クリッピング機能を他のモデルに追加し、レンダラーのサイズを大きくし、それぞれのメッシュ レンダラーを追加してきました。

## <a name="configuring-eye-tracking-to-highlight-tooltips"></a>ヒントを強調表示するための視線追跡の構成

このセクションでは、プロジェクトで視線追跡を有効にする方法を学習します。 たとえば、MarsCuriosityRover のパーツに関連付けられているヒントを、それらのパーツに視線を向けている時は強調表示し、視線を外すと非表示にする機能を実装できます。

### <a name="1-identify-target-objects-and-associated-tooltips"></a>1.ターゲット オブジェクトおよび関連するヒントを特定する

[階層] ウィンドウで、ModelParent オブジェクトを選択します。 * **[MarsCuriosity] -> [Rover]** _ を展開し、MarsCuriosityRover の 5 つの主要なパーツ _*POI-Camera**、**POI-Wheels**、**POI-Antenna**、**POI-Spectrometer**、**POI-RUHF Antenna** を見つけます。

* [階層] ウィンドウで、MarsCuriosityRover パーツに関連付けられている、対応する 5 つのヒント オブジェクトを確認します。
* これらの MarsCuriosityRover パーツに視線を向けたときにそのエクスペリエンスを強調表示するように、これらのオブジェクトを構成していきます。

![Rover オブジェクトが選択されて展開された Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step1-1.png)

### <a name="2-implement-while-looking-at-target-----on-look-away--events"></a>2.While Looking At Target () および On Look Away () イベントを実装する

[階層] ウィンドウで、***POI-Camera** _ オブジェクトを選択します。 [インスペクター] ウィンドウで、_ *Eye Tracking Target (Script)* * コンポーネントを見つけて、次のように **While Looking At Target ()**  & **On Look Away ()** イベントを構成します。

* **[None (Object)]\(なし (オブジェクト)\)** フィールドに、**POI-Camera ToolTip** オブジェクトを割り当てます。
* **While Looking At Target ()** イベントの **[No Function]\(関数なし\)** ドロップダウンから、**GameObject** > **SetActive (bool)** の順に選択します。 その下にある **チェックボックス** をオンにして、ターゲット オブジェクトに視線を向けたときにトリガーされるアクションとしてそのヒントが強調表示されるようにします。

![EyeTrackingTarget の WhileLookingAtTarget イベントの構成が進行中の Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-1.png)

* 同じプロセスに従い、**On Look Away ()** イベント リスナーの **[No Function]\(関数なし\)** ドロップダウンをクリックします。 次に、**GameObject** > **SetActive (bool)** の順に選択し、**チェックボックス** はオフのままにしておいて、ターゲット オブジェクトから視線を外したときにトリガーされるアクションとしてそのヒントが非表示になるようにします。

![EyeTrackingTarget の OnLookAway イベントが構成された Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-2.png)

同じプロセスに従い、同じ **MarsCuriosityRover** パーツの **While Looking At Target ()**  & **On Look Away ()** イベントに、それぞれのヒント オブジェクトを割り当てます。

視線追跡を有効にするには、こちらの[ガイドライン](/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations)に従ってください。

## <a name="congratulations"></a>結論

このチュートリアルでは、UI 要素、3D モデルの操作、モデルのクリッピング、および視線追跡機能をデモンストレーションする Mixed Reality エクスペリエンスを構築する方法を学習しました。 このチュートリアルで説明した NextButton および PreviousButton で、3D モデルのビューアー エクスペリエンスを実際に試しました。 ClippingObjectButton を使用して、クリッピング オブジェクトをオンにし、クリッピング機能を体験しました。 このチュートリアルでは、エクスペリエンスでのヒントの強調表示を可能にする視線追跡要素についても説明しました。

次のレッスンでは、いつでも HoloLens 2 に接続できる PC 用の Holographic Remoting アプリケーションを作成し、Mixed Reality で 3D コンテンツを視覚化する方法について説明します。

> [!div class="nextstepaction"]
> [次のレッスン:2.Holographic Remoting アプリケーションを作成する](mr-learning-pc-holographic-remoting-02.md)