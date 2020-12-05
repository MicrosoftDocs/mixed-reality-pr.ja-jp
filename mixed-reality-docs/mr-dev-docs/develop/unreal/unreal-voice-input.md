---
title: 音声入力
description: HoloLens 2 および Unreal engine での音声入力の設定と使用に関するチュートリアル
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality、Unreal、Unreal Engine 4、UE4、HoloLens 2、音声、音声入力、音声認識、mixed reality、開発、機能、ドキュメント、ガイド、ホログラム、ゲーム開発、mixed reality ヘッドセット、windows mixed Reality ヘッドセット、virtual reality ヘッドセット
ms.openlocfilehash: 504a2d978e3c9bc698e8edd11ea8a4d6be13795a
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609753"
---
# <a name="voice-input-in-unreal"></a>Unreal での音声入力

Unreal の音声入力を使用すると、ハンドジェスチャを使用しなくても、または HoloLens 2 のみがサポートされるようになります。 HoloLens 2 での音声入力は、他のすべてのユニバーサル Windows アプリで音声をサポートするのと同じエンジンによって機能しますが、より限定的なエンジンを使用して音声入力を処理します。 これにより、次のセクションで説明するように、Unreal の音声入力機能が定義済みの音声マッピングに限定されます。 

## <a name="enabling-speech-recognition"></a>音声認識を有効にする

HoloLens で音声認識を有効にするには:
1. [プロジェクトの設定] を選択して **> プラットフォーム > HoloLens > 機能** を選択し、 **マイク** を有効にします。 
2. [設定] で音声認識を有効にし、[**プライバシー] > [>** ] を選択します。 **English**

> [!NOTE]
> 音声認識は常に、 **設定** アプリで構成された Windows 表示言語で機能します。 また、サービス品質を最大限に高めるために、 **オンライン音声認識** を有効にすることをお勧めします。

![Windows 音声認識の設定](images/unreal/speech-recognition-settings.png)

3. アプリケーションが最初にマイクを有効にするかどうかを確認すると、ダイアログが表示されます。 **[はい]** を選択すると、アプリで音声入力が開始されます。

音声入力には、特別な Windows Mixed Reality Api は必要ありません。これは、既存の Unreal Engine 4 [入力](https://docs.unrealengine.com/Gameplay/Input/index.html) マッピング API を基に構築されています。 

## <a name="adding-speech-mappings"></a>音声マッピングの追加

音声入力を使用する場合は、音声をアクションに接続することが重要な手順です。 これらのマッピングは、ユーザーが話す可能性のある音声キーワードをアプリで監視し、リンクされたアクションを起動します。 音声マッピングは、次の方法で見つけることができます。
1. [ **プロジェクト設定の編集 >**] を選択し、[ **エンジン** ] セクションまでスクロールして [ **入力**] をクリックします。

ジャンプコマンドの新しい音声マッピングを追加するには、次のようにします。
1. [ **+** **配列要素** ] の横にあるアイコンを選択し、次の値を入力します。
    * **アクション名** の **jumpWord**
    * **Speech キーワード** の **ジャンプ**

> [!NOTE]
> すべての英語の単語または短い文をキーワードとして使用できます。 

![UE4 Engine の入力設定](images/unreal/engine-input.png)

音声マッピングは、アクションや軸のマッピングなどの入力コンポーネントとして、またはイベントグラフのブループリントノードとして使用できます。 たとえば、ジャンプコマンドをリンクして、単語が話されるタイミングに応じて2つの異なるログを出力することができます。

1. ブループリントをダブルクリックして、 **イベントグラフ** で開きます。
2. **右クリック** して音声マッピングの **アクション名** (この場合は **jumpWord**) を検索し、 **enter キー** を押して **入力アクション** ノードをグラフに追加します。
3. 次の図に示すように、 **押さ** れた pin をドラッグアンドドロップして文字列ノードを **印刷** します。 **解放** された pin は空のままにすることができ、音声マッピングの場合は何も実行されません。
 
![音声の単純なアクション](images/unreal/voice-input-img-03.png)

4. アプリを再生し、word の **ジャンプ** と言って、コンソールでログを出力します。

これで、HoloLens アプリへの音声入力の追加を開始する必要があります。 音声と対話機能の詳細については、以下のリンクを参照してください。ユーザー向けに作成しているエクスペリエンスについて考えてください。

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

デプロイされていない実際の開発については、次に、Mixed Reality プラットフォームの機能と Api について説明します。 

> [!div class="nextstepaction"]
> [HoloLens カメラ](unreal-hololens-camera.md)

いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#2-core-building-blocks)に戻ることができます。

## <a name="see-also"></a>関連項目
* [音声入力](../../design/voice-input.md)
* [視線入力とコミット](../../design/gaze-and-commit.md)
* [本能的な操作](../../design/interaction-fundamentals.md)

