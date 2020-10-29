---
title: Azure Speech Services のチュートリアル - 2. ローカル音声テキスト変換用のオフライン モードの追加
description: このコースでは、Mixed Reality アプリケーション内で Azure Speech SDK を実装する方法を学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: a7fa1bdaa72d341eaa49ac70dfa926d8f9bbad7a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91702206"
---
# <a name="2-using-speech-recognition-to-execute-commands"></a>2.音声認識を使用したコマンドの実行

このチュートリアルでは、Azure 音声認識を使用してコマンドを実行する機能を追加します。これを使用すると、定義した単語やフレーズに基づいて何かを実行させることができます。

## <a name="objectives"></a>目標

* Azure 音声認識を使用してコマンドを実行する方法を学習する

## <a name="instructions"></a>手順

[Hierarchy]\(階層\) ウィンドウで **Lunarcom** オブジェクトを選択し、次に [Inspector]\(インスペクター\) ウィンドウで **[Add Component]\(コンポーネントの追加\)** ボタンを使用して、 **Lunarcom Wake Word Recognizer (Script)** コンポーネントを Lunarcom オブジェクトに追加し、次のように構成します。

* **[Wake Word]\(ウェイク ワード\)** フィールドに、適切なフレーズ (たとえば、「 _Activate terminal_ 」など) を入力します。
* **[Dismiss Word]\(終了ワード\)** フィールドに、適切なフレーズ (たとえば、「 _Dismiss terminal_ 」など) を入力します。

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> Lunarcom Wake Word Recognizer (Script) コンポーネントは MRTK の一部ではありません。 このチュートリアルのアセットと共に提供されました。

前のチュートリアルと同様に、ゲーム モードに入ると、既定で [Terminal]\(ターミナル\) パネルが有効になりますが、今回は、終了ワードである **Dismiss terminal** と発話することにより無効にできるようになりました。

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-2.png)

そして、ウェイク ワードである **Activate terminal** と発話することにより、再び有効にできます。

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> アプリケーションは Azure に接続する必要があるため、お使いのコンピューター/デバイスがインターネットに接続されていることを確認してください。

> [!TIP]
> 頻繁に Azure に接続できないことが予測される場合は、「[音声コマンドの使用](mr-learning-base-09.md)」の手順に従うことで、MRTK を使用して音声コマンドを実装することもできます。

## <a name="congratulations"></a>結論

Azure で提供されている音声コマンドを実装しました。 デバイスでアプリケーションを実行して、機能が正常に動作していることを確認してください。

次のチュートリアルでは、Azure Speech Translation を使用して音声を翻訳する方法について説明します。

> [!div class="nextstepaction"]
> [次のチュートリアル:3.Azure Cognitive Services の Speech Translation コンポーネントの追加](mrlearning-speechSDK-ch3.md)
