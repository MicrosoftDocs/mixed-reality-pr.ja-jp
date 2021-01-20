---
title: 空間オーディオのチュートリアル-1. プロジェクトへの空間オーディオの追加
description: Microsoft Spatializer プラグインを Unity プロジェクトに追加して、HoloLens 2 HRTF ハードウェアオフロードにアクセスします。
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality、unity、チュートリアル、hololens2、空間オーディオ、MRTK、mixed reality toolkit、UWP、Windows 10、HRTF、head 関連の転送機能、リバーブ、Microsoft Spatializer
ms.openlocfilehash: 7d4702a21fccbb18c7c4b07675953c37785ae6db
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580226"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a>1. Unity プロジェクトに空間オーディオを追加する

## <a name="overview"></a>概要

HoloLens2 上の Unity の空間オーディオチュートリアルへようこそ。 このチュートリアルシリーズでは、HoloLens 2 でヘッド関連の転送関数 (HRTF) オフロードを使用する方法と、HRTF オフロードを使用するときにリバーブを有効にする方法について説明します。

[Microsoft Spatializer GitHub リポジトリ](https://github.com/microsoft/spatialaudio-unity)には、このチュートリアルシーケンスの完成した Unity プロジェクトが用意されています。

HRTF ベースの spatialization テクノロジを使用してサウンドを spatialize することの意味と、役に立つ可能性がある場合の推奨事項については、「 [空間サウンドの設計](/windows/mixed-reality/spatial-sound-design)」を参照してください。

## <a name="what-is-hrtf-offload"></a>HRTF offload とは

HRTF ベースのアルゴリズムを使用してオーディオを処理するには、大量の特殊な計算が必要です。 HoloLens 2 には、アプリケーションプロセッサに負荷がかからないようにするために使用できる専用のハードウェアが含まれているため、HRTF ベースのアルゴリズムの処理を "オフロード" します。  Microsoft spatializer プラグインを使用すると、アプリケーションで専用の HRTF ハードウェアを利用して、空間オーディオ以外の操作でアプリケーションプロセッサをより多く使用できるようにすることができます。

## <a name="objectives"></a>目標

* Microsoft spatializer プラグインのインポートと有効化
* 開発者ワークステーションでの空間オーディオの有効化

## <a name="prerequisites"></a>前提条件

* 正しい[ツールがインストールされている](../../install-the-tools.md)構成済みの Windows 10 PC
* C# プログラミングの基本知識
* [開発用に構成された](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス
* Unity 2019 LTS がマウントされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>

作業を続行する前に、[概要](mr-learning-base-01.md)チュートリアルシリーズを完了するか、Unity と MRTK の基本的な経験があることを **強くお勧め** します。

> [!IMPORTANT]
>
> * このチュートリアル シリーズで推奨されている Unity バージョンは、Unity 2019 LTS です。 これは、上でリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。

## <a name="creating-and-preparing-the-unity-project"></a>Unity プロジェクトの作成と準備

このセクションでは、新しい Unity プロジェクトを作成し、MRTK 開発用に準備します。

このためには、まず「[プロジェクトと最初のアプリケーションの初期化](mr-learning-base-02.md)」に従ってください (「[デバイスへのアプリケーションのビルド](mr-learning-base-02.md#building-your-application-to-your-hololens-2)」の手順は除く)。これには、次の手順が含まれます。

1. [Unity プロジェクトを作成](mr-learning-base-02.md#creating-the-unity-project)し、"*MRTK チュートリアル*" などの適切な名前を付ける

1. [ビルド プラットフォームを切り替える](mr-learning-base-02.md#configuring-the-unity-project)

1. [TextMeshPro の重要なリソースをインポートする](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [Mixed Reality Toolkit をインポートする](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [Unity プロジェクトを構成する](mr-learning-base-02.md#configuring-the-unity-project)

1. [シーンを作成および設定](mr-learning-base-02.md#creating-and-configuring-the-scene)し、シーンに適切な名前を付けます (たとえば、 *SpatialAudio* )。

次に、「 [空間認識表示オプションの変更」](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) の手順に従って、シーンの MRTK 構成プロファイルが **DefaultXRSDKConfigurationProfile** になっていることを確認し、空間認識メッシュの表示オプションを **オクルージョン** に変更します。

## <a name="adding-microsoft-spatializer-to-the-project"></a>プロジェクトへの Microsoft Spatializer の追加

Microsoft Spatializer <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">SpatialAudio. Spatializer</a>をダウンロードしてインポートします。

>[!TIP]
> Unity カスタム パッケージをインポートする方法については、「[Mixed Reality Toolkit をインポートする](../../../mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)」の手順を参照してください。

## <a name="enable-the-microsoft-spatializer-plugin"></a>Microsoft Spatializer プラグインを有効にする

**Microsoft Spatializer** をインポートしたら、有効にする必要があります。 [ **編集-> プロジェクトの設定-> オーディオ**] を開き、 **Spatializer プラグイン** を "Microsoft Spatializer" に変更します。

![Spatializer プラグインを表示するプロジェクト設定](images/spatial-audio/spatial-audio-01-section3-step1-1.png)

## <a name="enable-spatial-audio-on-your-workstation"></a>ワークステーションで空間オーディオを有効にする

Windows のデスクトップバージョンでは、空間オーディオは既定で無効になっています。 これを有効にするには、タスクバーのボリュームアイコンを右クリックします。 HoloLens 2 で耳になる内容を最大限に活用するには、[ **空間サウンド > Windows Sonic For ヘッドホン**] を選択します。

![デスクトップ空間オーディオの設定](images/spatial-audio/spatial-audio-01-section4-step1-1.png)

> [!NOTE]
> この設定は、Unity エディターでプロジェクトをテストする場合にのみ必要です。

## <a name="congratulations"></a>結論

このチュートリアルでは、Microsoft Spatializer プラグインをインポートして有効にする方法と、ワークステーションで空間オーディオを有効にする方法について説明しました。
次のチュートリアルでは、unity プロジェクトに空間オーディオを追加する方法について説明します。

> [!div class="nextstepaction"]
> [次のチュートリアル: 2. Spatializing ボタンの相互作用サウンド](unity-spatial-audio-ch2.md)
