---
title: 音声認識と文字起こしの統合と使用
description: このコースを完了すると、Mixed Reality アプリケーションで Azure の音声認識と文字起こしを追加して使用する方法がわかります。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality Toolkit, UWP, Azure 空間アンカー, 音声認識, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: f0c26c861cb3400c552d17d45f77cfe3a5cc284c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010122"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1.音声認識と文字起こしの統合と使用

このチュートリアル シリーズでは、HoloLens 2 での Azure Speech Services の使用を探索する Mixed Reality アプリケーションを作成します。 このチュートリアル シリーズを完了すると、デバイスのマイクを使用して、リアルタイムで音声を文字に起こしたり、音声を他の言語に翻訳したり、意図認識機能を利用して、人工知能を使って音声コマンドを理解したりできるようになります。

## <a name="objectives"></a>目標

* Azure Speech Services と HoloLens 2 アプリケーションを統合する方法を学習する
* 音声認識を使用して文字に起こす方法を学習する

## <a name="prerequisites"></a>前提条件

>[!TIP]
>[入門チュートリアル](mr-learning-base-01.md) シリーズをまだ完了していない場合は、まずこれらのチュートリアルを完了することをお勧めします。

* 正しい[ツールがインストールされている](../../install-the-tools.md)構成済みの Windows 10 PC
* Windows 10 SDK 10.0.18362.0 以降
* 基本的な C# プログラミング能力
* [開発用に構成された](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス
* Unity 2019 LTS がインストールされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>

> [!IMPORTANT]
> このチュートリアル シリーズで推奨されている Unity バージョンは、Unity 2019 LTS です。 これは、上のリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。

## <a name="creating-and-preparing-the-unity-project"></a>Unity プロジェクトの作成と準備

このセクションでは、新しい Unity プロジェクトを作成し、MRTK 開発用に準備します。

このためには、まず「[プロジェクトと最初のアプリケーションの初期化](mr-learning-base-02.md)」に従ってください (「[デバイスへのアプリケーションのビルド](mr-learning-base-02.md#building-and-deploying-to-your-hololens-2)」の手順は除く)。これには、次の手順が含まれます。

1. [Unity プロジェクトを作成](mr-learning-base-02.md#creating-the-unity-project)し、"*MRTK チュートリアル*" などの適切な名前を付ける
2. [ビルド プラットフォームを切り替える](mr-learning-base-02.md#switching-the-build-platform)
3. [TextMeshPro の重要なリソースをインポートする](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [Mixed Reality Toolkit をインポートする](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [Unity プロジェクトを構成する](mr-learning-base-02.md#selecting-mrtk-and-project-settings)
6. [シーンを作成して構成](mr-learning-base-02.md#creating-and-configuring-the-scene)し、シーンに *AzureSpeechServices* などの適切な名前を付ける

その後、「[空間認識表示オプションの変更](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)」の手順に従って、シーンの MRTK 構成プロファイルを **[DefaultHoloLens2ConfigurationProfile]** に変更し、空間認識メッシュの表示オプションを **[Occlusion]\(オクルージョン\)** に変更します。

## <a name="configuring-the-speech-commands-start-behavior"></a>音声コマンドの開始動作の構成

音声認識と文字起こしには Speech SDK を使用するため、Speech SDK の機能の妨げにならないように、MRTK の音声コマンドを構成する必要があります。 これを実現するには、音声コマンドの開始動作を [Auto Start]\(自動開始\) から [Manual Start]\(手動開始\) に変更することができます。

[Hierarchy]\(階層\) ウィンドウで **MixedRealityToolkit** オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで **[Input]\(入力\)** タブを選択し、**DefaultHoloLens2InputSystemProfile** と **DefaultMixedRealitySpeechCommandsProfile** を複製し、音声コマンドの **[Start Behavior]\(開始動作\)** を **[Manual Start]\(手動開始\)** に変更します。

![mrlearning-speech](images/mrlearning-speech/tutorial1-section2-step1-1.png)

> [!TIP]
> MRTK プロファイルを複製し、構成する方法については、[Mixed Reality ツールキット プロファイルの構成](mr-learning-base-03.md)に関するページにある手順を参照してください。

## <a name="configuring-the-capabilities"></a>機能の構成

Unity メニューで **[Edit]\(編集\)**  >  **[Project Settings]\(プロジェクトの設定\)** を選択して、[Player Settings]\(プレーヤーの設定\) ウィンドウを開きます。次に、 **[Player]\(プレーヤー\)**  >   **[Publishing Settings]\(発行の設定\)** セクションを見つけます。

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-1.png)

**[Publishing Settings]\(発行の設定\)** で、下にスクロールして **[Capabilities]\(機能\)** セクションまで移動し、チュートリアルの開始時にプロジェクトを作成したときに有効にした **InternetClient**、**Microphone**、および **SpatialPerception** の機能が有効になっていることを再確認します。 次に、**InternetClientServer** と **PrivateNetworkClientServer** の機能を有効にします。

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>チュートリアルのアセットのインポート

次の Unity カスタム パッケージを、**一覧に表示されている順序で** ダウンロードして **インポート** します。

* [Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (最新バージョン)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-speech-services-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage)

> [!TIP]
> Unity カスタム パッケージをインポートする方法については、「[Mixed Reality Toolkit をインポートする](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)」の手順を参照してください。

チュートリアルのアセットをインポートすると、プロジェクト ウィンドウは次のようになります。

![mrlearning-speech](images/mrlearning-speech/tutorial1-section4-step1-1.png)

## <a name="preparing-the-scene"></a>シーンの準備

このセクションでは、チュートリアルのプレハブを追加してシーンを準備し、シーンを制御するように Lunarcom Controller (Script) コンポーネントを構成します。

[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.AzureSpeechServices]**  >  **[Prefabs]** フォルダーに移動し、 **[Lunarcom]** プレハブを [Hierarchy]\(階層\) ウィンドウにドラッグしてシーンに追加します。

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-1.png)

[Hierarchy]\(階層\) ウィンドウで **Lunarcom** オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで **[Add Component]\(コンポーネントの追加\)** ボタンを使用して、**Lunarcom Controller (Script)** コンポーネントを Lunarcom オブジェクトに追加します。

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> Lunarcom Controller (Script) コンポーネントは MRTK の一部ではありません。 このチュートリアルのアセットと共に提供されました。

**[Lunarcom]** オブジェクトを選択した状態で、それを展開して子オブジェクトを表示し、次に **Terminal** オブジェクトを Lunarcom Controller (Script) コンポーネントの **[Terminal]\(ターミナル\)** フィールドにドラッグします。

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-3.png)

**Lunarcom** オブジェクトを選択した状態で、Terminal オブジェクトを展開して子オブジェクトを表示し、**ConnectionLight** オブジェクトを Lunarcom Controller (Script) コンポーネントの **[Connection Light]\(接続ライト\)** フィールドに、**OutputText** オブジェクトを **[Output Text]\(出力テキスト\)** フィールドにドラッグします。

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-4.png)

**Lunarcom** オブジェクトを選択した状態で、Buttons オブジェクトを展開して子オブジェクトを表示し、次に [Inspector]\(インスペクター\) ウィンドウで **[Buttons]\(ボタン\)** リストを展開し、その **[Size]\(サイズ\)** を 3 に設定し、**MicButton**、**SatelliteButton**、および **RocketButton** の各オブジェクトを **[Element]\(要素\)** 0、1、2 のフィールドにそれぞれドラッグします。

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a>Unity プロジェクトを Azure リソースに接続

Azure Speech Services を使用するには、Azure リソースを作成し、Speech Service 用の API キーを取得する必要があります。 「[Speech Service を無料で試す](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started)」の手順に従って、ご利用のサービス リージョン (ロケーションとも呼ばれる) と API キー (Key1 または Key2 とも呼ばれる) をメモします。

[Hierarchy]\(階層\) ウィンドウで **Lunarcom** オブジェクトを選択し、次に [Inspector]\(インスペクター\) ウィンドウで **Lunarcom Controller (Script)** コンポーネントの **[Speech SDK Credentials]\(Speech SDK 資格情報\)** セクションを見つけ、次のように構成します。

* **[Speech Service API Key]\(Speech Service の API キー\)** フィールドに、API キー (Key1 または Key2) を入力します
* **[Speech Service Region]\(Speech Service のリージョン\)** フィールドに、小文字を使用し、スペースを削除して、サービス リージョン (ロケーション) を入力します

![mrlearning-speech](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a>音声認識を使用して音声を文字に起こす

[Hierarchy]\(階層\) ウィンドウで **Lunarcom** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで **[Add Component]\(コンポーネントの追加\)** ボタンを使用して、**Lunarcom Speech Recognizer (Script)** コンポーネントを Lunarcom オブジェクトに追加します。

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> Lunarcom Speech Recognizer (Script) コンポーネントは MRTK の一部ではありません。 このチュートリアルのアセットと共に提供されました。

ゲーム モードに入ったら、まずマイクのボタンを押して音声認識をテストすることができます。

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-2.png)

次に、お使いのコンピューターにマイクがあると仮定して、何か話すと、音声がターミナルのパネル上に文字で表示されます。

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-3.png)


> [!CAUTION]
> アプリケーションは Azure に接続する必要があるため、お使いのコンピューター/デバイスがインターネットに接続されていることを確認してください。

## <a name="congratulations"></a>結論

Azure で提供される音声認識を実装しました。 デバイスでアプリケーションを実行して、機能が正常に動作していることを確認してください。

次のチュートリアルでは、Azure 音声認識を使用してコマンドを実行する方法を学習します。

> [!div class="nextstepaction"]
> [次のチュートリアル: 2.音声認識を使用したコマンドの実行](mrlearning-speechSDK-ch2.md)
