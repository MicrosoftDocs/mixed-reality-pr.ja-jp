---
title: ローカル音声テキスト変換用のオフライン モードの追加
description: このコースを完了すると、Mixed Reality アプリケーションでローカル音声テキスト変換用のオフライン モードを追加する方法がわかります。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality Toolkit, UWP, Azure 空間アンカー, 音声認識, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 2e7a48dc4bb64eb177e6fa290f4918345c3d642f
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590154"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="58c42-104">2.ローカル音声からテキストへの変換用のオフライン モードの追加</span><span class="sxs-lookup"><span data-stu-id="58c42-104">2. Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="58c42-105">このチュートリアルでは、Azure 音声認識を使用してコマンドを実行する機能を追加します。これを使用すると、定義した単語やフレーズに基づいて何かを実行させることができます。</span><span class="sxs-lookup"><span data-stu-id="58c42-105">In this tutorial, you will add the ability to execute commands using Azure speech recognition which will allow you to make something happen based on the word or phrase you define.</span></span>

## <a name="objectives"></a><span data-ttu-id="58c42-106">目標</span><span class="sxs-lookup"><span data-stu-id="58c42-106">Objectives</span></span>

* <span data-ttu-id="58c42-107">Azure 音声認識を使用してコマンドを実行する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="58c42-107">Learn how Azure speech recognition can be used to execute commands</span></span>

## <a name="instructions"></a><span data-ttu-id="58c42-108">手順</span><span class="sxs-lookup"><span data-stu-id="58c42-108">Instructions</span></span>

<span data-ttu-id="58c42-109">[Hierarchy]\(階層\) ウィンドウで **Lunarcom** オブジェクトを選択し、次に [Inspector]\(インスペクター\) ウィンドウで **[Add Component]\(コンポーネントの追加\)** ボタンを使用して、**Lunarcom Wake Word Recognizer (Script)** コンポーネントを Lunarcom オブジェクトに追加し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="58c42-109">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Wake Word Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="58c42-110">**[Wake Word]\(ウェイク ワード\)** フィールドに、適切なフレーズ (たとえば、「_Activate terminal_」など) を入力します。</span><span class="sxs-lookup"><span data-stu-id="58c42-110">In the **Wake Word** field, enter a suitable phrase, for example, _Activate terminal_.</span></span>
* <span data-ttu-id="58c42-111">**[Dismiss Word]\(終了ワード\)** フィールドに、適切なフレーズ (たとえば、「_Dismiss terminal_」など) を入力します。</span><span class="sxs-lookup"><span data-stu-id="58c42-111">In the **Dismiss Word** field, enter a suitable phrase, for example, _Dismiss terminal_.</span></span>

![Lunarcom Wake Word Recognizer スクリプト コンポーネントが強調表示されている Unity エディター](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="58c42-113">Lunarcom Wake Word Recognizer (Script) コンポーネントは MRTK の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="58c42-113">The Lunarcom Wake Word Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="58c42-114">このチュートリアルのアセットと共に提供されました。</span><span class="sxs-lookup"><span data-stu-id="58c42-114">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="58c42-115">前のチュートリアルと同様に、ゲーム モードに入ると、既定で [Terminal]\(ターミナル\) パネルが有効になりますが、今回は、終了ワードである **Dismiss terminal** と発話することにより無効にできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="58c42-115">If you now enter Game mode, as in the previous tutorial, the terminal panel is enabled by default, but you can now disable it by saying the Dismiss Word, **Dismiss terminal**:</span></span>

![音声認識エンジン機能が使用されているプレイ モードの Unity エディター](images/mrlearning-speech/tutorial2-section1-step1-2.png)

<span data-ttu-id="58c42-117">そして、ウェイク ワードである **Activate terminal** と発話することにより、再び有効にできます。</span><span class="sxs-lookup"><span data-stu-id="58c42-117">And enable it again by saying the Wake Word, **Activate terminal**:</span></span>

![アクティブなターミナルがあるプレイ モードの Unity エディター](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="58c42-119">アプリケーションは Azure に接続する必要があるため、お使いのコンピューター/デバイスがインターネットに接続されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="58c42-119">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

> [!TIP]
> <span data-ttu-id="58c42-120">頻繁に Azure に接続できないことが予測される場合は、「[音声コマンドの使用](mr-learning-base-09.md)」の手順に従うことで、MRTK を使用して音声コマンドを実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="58c42-120">If you anticipate frequently not being able to connect to Azure, you can also implement speech commands using MRTK by following the [Using speech commands](mr-learning-base-09.md) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="58c42-121">結論</span><span class="sxs-lookup"><span data-stu-id="58c42-121">Congratulations</span></span>

<span data-ttu-id="58c42-122">Azure で提供されている音声コマンドを実装しました。</span><span class="sxs-lookup"><span data-stu-id="58c42-122">You have implemented speech commands powered by Azure.</span></span> <span data-ttu-id="58c42-123">デバイスでアプリケーションを実行して、機能が正常に動作していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="58c42-123">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="58c42-124">次のチュートリアルでは、Azure Speech Translation を使用して音声を翻訳する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="58c42-124">In the next tutorial, you will learn how to translate speech using Azure speech translation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="58c42-125">次のチュートリアル:3.Azure Cognitive Services の Speech Translation コンポーネントの追加</span><span class="sxs-lookup"><span data-stu-id="58c42-125">Next Tutorial: 3. Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)
