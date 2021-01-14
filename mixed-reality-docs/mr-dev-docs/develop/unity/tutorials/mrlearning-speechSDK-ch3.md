---
title: Azure Cognitive Services の Speech Translation コンポーネントの追加
description: このコースでは、Mixed Reality アプリケーションに Azure Cognitive Services の音声翻訳を追加する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality Toolkit, UWP, Azure 空間アンカー, 音声認識, Windows 10, 音声翻訳
ms.localizationpriority: high
ms.openlocfilehash: 3c647ca841e51b707aae4171b31b0b045c79fb03
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009882"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="598aa-104">3.Azure Cognitive Services の Speech Translation コンポーネントの追加</span><span class="sxs-lookup"><span data-stu-id="598aa-104">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="598aa-105">このチュートリアルでは、Speech Translation をプロジェクトに追加します。これにより、音声を 3 つの異なる言語に翻訳して書き起こすことができます。</span><span class="sxs-lookup"><span data-stu-id="598aa-105">In this tutorial, you will add speech translation to your project which will allow you to translate and transcribed your speech into three different languages.</span></span>

## <a name="objectives"></a><span data-ttu-id="598aa-106">目標</span><span class="sxs-lookup"><span data-stu-id="598aa-106">Objectives</span></span>

* <span data-ttu-id="598aa-107">Azure Speech Translation を統合する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="598aa-107">Learn how to integrate Azure speech translation</span></span>

## <a name="instructions"></a><span data-ttu-id="598aa-108">手順</span><span class="sxs-lookup"><span data-stu-id="598aa-108">Instructions</span></span>

<span data-ttu-id="598aa-109">[Hierarchy]\(階層\) ウィンドウで **Lunarcom** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで **[Add Component]\(コンポーネントの追加\)** ボタンを使用して、**Lunarcom Translation Recognizer (Script)** コンポーネントを Lunarcom オブジェクトに追加し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="598aa-109">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Translation Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="598aa-110">**[Target Language]\(対象言語\)** を選択した言語 (たとえば、[_German_]\(ドイツ語\)) に変更します。</span><span class="sxs-lookup"><span data-stu-id="598aa-110">Change the **Target Language** to a language of your choosing, for example, _German_</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="598aa-112">Lunarcom Translation Recognizer (Script) コンポーネントは MRTK の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="598aa-112">The Lunarcom Translation Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="598aa-113">このチュートリアルのアセットと共に提供されました。</span><span class="sxs-lookup"><span data-stu-id="598aa-113">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="598aa-114">ゲーム モードに入ったら、まずサテライト ボタンを押して音声翻訳をテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="598aa-114">If you now enter Game mode, you can test the speech translation by first pressing the satellite button.</span></span> <span data-ttu-id="598aa-115">次に、お使いのコンピューターにマイクがあると仮定して、何かを話すと、選択した言語に音声が翻訳されて、ターミナルのパネル上に文字で表示されます。</span><span class="sxs-lookup"><span data-stu-id="598aa-115">Then, assuming your computer has a microphone, when you say something, your speech will be translated into the chosen language and transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-2.png)

> [!CAUTION]
> <span data-ttu-id="598aa-117">アプリケーションは Azure に接続する必要があるため、お使いのコンピューター/デバイスがインターネットに接続されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="598aa-117">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="598aa-118">結論</span><span class="sxs-lookup"><span data-stu-id="598aa-118">Congratulations</span></span>

<span data-ttu-id="598aa-119">プロジェクトでは、話した言葉を複数の異なる言語に正常に翻訳できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="598aa-119">Your project can now successfully translate the words you speak into several different languages.</span></span> <span data-ttu-id="598aa-120">デバイスでアプリケーションを実行して、機能が適切に動作していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="598aa-120">Run the application on your device to ensure the feature is working properly.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="598aa-121">次のチュートリアル: 4.インテントの設定と自然言語の理解</span><span class="sxs-lookup"><span data-stu-id="598aa-121">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
