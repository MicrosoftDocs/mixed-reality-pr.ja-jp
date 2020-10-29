---
title: Azure Speech Services のチュートリアル - 3. Azure Cognitive Services の Speech Translation コンポーネントの追加
description: このコースでは、Mixed Reality アプリケーション内で Azure Speech SDK を実装する方法を学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 6a7aead068b5ab8ba25bcf84bbeae0a19723845b
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91702189"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="7d8fb-105">3.Azure Cognitive Services の Speech Translation コンポーネントの追加</span><span class="sxs-lookup"><span data-stu-id="7d8fb-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="7d8fb-106">このチュートリアルでは、Speech Translation をプロジェクトに追加します。これにより、音声を 3 つの異なる言語に翻訳して書き起こすことができます。</span><span class="sxs-lookup"><span data-stu-id="7d8fb-106">In this tutorial, you will add speech translation to your project which will allow you to translate and transcribed your speech into three different languages.</span></span>

## <a name="objectives"></a><span data-ttu-id="7d8fb-107">目標</span><span class="sxs-lookup"><span data-stu-id="7d8fb-107">Objectives</span></span>

* <span data-ttu-id="7d8fb-108">Azure Speech Translation を統合する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="7d8fb-108">Learn how to integrate Azure speech translation</span></span>

## <a name="instructions"></a><span data-ttu-id="7d8fb-109">手順</span><span class="sxs-lookup"><span data-stu-id="7d8fb-109">Instructions</span></span>

<span data-ttu-id="7d8fb-110">[Hierarchy]\(階層\) ウィンドウで **Lunarcom** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで **[Add Component]\(コンポーネントの追加\)** ボタンを使用して、 **Lunarcom Translation Recognizer (Script)** コンポーネントを Lunarcom オブジェクトに追加し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="7d8fb-110">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Translation Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="7d8fb-111">**[Target Language]\(対象言語\)** を選択した言語 (たとえば、[ _German_ ]\(ドイツ語\)) に変更します。</span><span class="sxs-lookup"><span data-stu-id="7d8fb-111">Change the **Target Language** to a language of your choosing, for example, _German_</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="7d8fb-113">Lunarcom Translation Recognizer (Script) コンポーネントは MRTK の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="7d8fb-113">The Lunarcom Translation Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="7d8fb-114">このチュートリアルのアセットと共に提供されました。</span><span class="sxs-lookup"><span data-stu-id="7d8fb-114">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="7d8fb-115">ゲーム モードに入ったら、まずサテライト ボタンを押して音声翻訳をテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="7d8fb-115">If you now enter Game mode, you can test the speech translation by first pressing the satellite button.</span></span> <span data-ttu-id="7d8fb-116">次に、お使いのコンピューターにマイクがあると仮定して、何かを話すと、選択した言語に音声が翻訳されて、ターミナルのパネル上に文字で表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d8fb-116">Then, assuming your computer has a microphone, when you say something, your speech will be translated into the chosen language and transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-2.png)

> [!CAUTION]
> <span data-ttu-id="7d8fb-118">アプリケーションは Azure に接続する必要があるため、お使いのコンピューター/デバイスがインターネットに接続されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7d8fb-118">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="7d8fb-119">結論</span><span class="sxs-lookup"><span data-stu-id="7d8fb-119">Congratulations</span></span>

<span data-ttu-id="7d8fb-120">プロジェクトでは、話した言葉を複数の異なる言語に正常に翻訳できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="7d8fb-120">Your project can now successfully translate the words you speak into several different languages.</span></span> <span data-ttu-id="7d8fb-121">デバイスでアプリケーションを実行して、機能が適切に動作していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7d8fb-121">Run the application on your device to ensure the feature is working properly.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7d8fb-122">次のチュートリアル: 4.インテントの設定と自然言語の理解</span><span class="sxs-lookup"><span data-stu-id="7d8fb-122">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
