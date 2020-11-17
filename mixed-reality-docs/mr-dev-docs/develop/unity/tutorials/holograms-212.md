---
title: MR 入力 212 - 音声
description: ここでは、Unity、Visual Studio、および HoloLens を使用したこのコーディングのチュートリアルに従って、音声の概念の詳細について説明します。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit、academy、チュートリアル、音声、HoloLens、Mixed Reality Academy、unity、mixed reality ヘッドセット、windows Mixed reality ヘッドセット、virtual Reality ヘッドセット、Windows 10
ms.openlocfilehash: b9d9002180da7a59c62b77b83872e77499da4c09
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677241"
---
# <a name="mr-input-212-voice"></a>MR 入力 212:音声

>[!NOTE]
>Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。  そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。  これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。  これらは、サポートされているデバイス上で継続して動作するように、保守されます。 HoloLens 2 向けには、[新しいチュートリアル シリーズ](../../../mr-learning-base-01.md)が投稿されています。

[音声入力](../../../design/voice-input.md) によって、ホログラムを操作するもう1つの方法が提供されます。 音声コマンドは、非常に自然で簡単な方法で動作します。 次のような音声コマンドを設計します。

* Natural
* 覚えやすい
* 適切なコンテキスト
* 同じコンテキスト内の他のオプションと十分に異なる

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

[MR 基本 101](../../../develop/unity/tutorials/holograms-101.md)では、KeywordRecognizer を使用して、2つの簡単な音声コマンドを作成していました。 MR 入力212では、次の方法について詳しく説明します。

* HoloLens speech エンジン用に最適化された音声コマンドを設計します。
* 使用できる音声コマンドをユーザーが認識できるようにします。
* ユーザーの声コマンドを聞いたことを確認します。
* ディクテーション認識エンジンを使用して、ユーザーが言っている内容を理解します。
* 構文認識エンジンを使用して、SRGS、または音声認識文法仕様 (ファイル) に基づいてコマンドをリッスンします。

このコースでは、 [Mr 入力 210](holograms-210.md) および [mr 入力 211](holograms-211.md)で構築したモデルエクスプローラーについて説明します。

>[!IMPORTANT]
>以下の各章に埋め込まれているビデオは、古いバージョンの Unity と Mixed Reality Toolkit を使用して記録されています。 ステップバイステップの手順は正確であり、最新のものですが、最新ではない対応するビデオにスクリプトとビジュアルが表示される場合があります。 ビデオはために含まれています。ここで説明する概念は引き続き適用されます。


## <a name="device-support"></a>デバイス サポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="../../../hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td>MR 入力 212:音声</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始する前に

### <a name="prerequisites"></a>必須コンポーネント

* 適切な [ツールがインストール](../../../develop/install-the-tools.md)された WINDOWS 10 PC。
* 基本的な C# プログラミング機能。
* [MR の基本 101](../../../develop/unity/tutorials/holograms-101.md)を完了している必要があります。
* [MR 入力 210](holograms-210.md)を完了している必要があります。
* [MR 入力 211](holograms-211.md)を完了している必要があります。
* [開発用に構成され](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)た HoloLens デバイス。

### <a name="project-files"></a>プロジェクト ファイル

* プロジェクトに必要な [ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) をダウンロードします。 Unity 2017.2 以降が必要です。
* ファイルをデスクトップまたはその他の簡単な場所に保管します。

>[!NOTE]
>ダウンロードする前にソースコードを確認する場合は、GitHub から [入手でき](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice)ます。

### <a name="errata-and-notes"></a>エラッタとメモ

* コード内のブレークポイントにヒットするには、Visual Studio の [ツール]->オプション->デバッグ] の下にある [マイコードのみを有効にする] を無効 (*オフ*) にする必要があります。

## <a name="unity-setup"></a>Unity のセットアップ

### <a name="instructions"></a>手順

1. Unity を起動します。
2. **[Open (開く)]** を選択します。
3. 以前にアーカイブしていた **HolographicAcademy-212-Voice** フォルダーに移動します。
4. [モデルエクスプローラーの **開始**] フォルダーを見つけて選択し / **Model Explorer** ます。
5. [ **フォルダーの選択** ] ボタンをクリックします。
6. [ **プロジェクト** ] パネルで、[ **シーン** ] フォルダーを展開します。
7. [ **Modelexplorer** シーン] をダブルクリックして Unity に読み込みます。

### <a name="building"></a>ビルド

1. Unity で、[ **ファイル > ビルド設定**] を選択します。
2. シーン **/ModelExplorer** が [ **ビルド] の [シーン**] に表示されていない場合は、[開いているシーンの **追加** ] をクリックしてシーンを追加します。
3. HoloLens 向けに特に開発している場合は、 **ターゲットデバイス** を **hololens** に設定します。 それ以外の場合は、 **任意のデバイス** に残しておきます。
4. **ビルドの種類** が [ **D3D** ] に設定され、[ **sdk** ] が [**最新のインストール済み**] に設定されていることを確認します (sdk 16299 以降である必要があります)。
5. [**ビルド**] をクリックします。
6. "App" という名前の **新しいフォルダー** を作成します。
7. **アプリ** フォルダーをシングルクリックします。
8. **[フォルダーの選択]** をクリックすると、Unity によって Visual Studio のプロジェクトのビルドが開始されます。

Unity が完了すると、エクスプローラーウィンドウが表示されます。

1. **アプリ** フォルダーを開きます。
2. **Modelexplorer Visual Studio ソリューション** を開きます。

HoloLens に展開する場合:

1. Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから **リリース** に変更し、ARM から **x86** に変更します。
2. [ローカルコンピューター] ボタンの横にあるドロップダウン矢印をクリックし、[ **リモートコンピューター**] を選択します。
3. **HoloLens デバイスの IP アドレス** を入力し、[認証モード] を [**ユニバーサル (暗号化** されていないプロトコル)] に設定します。 **[選択]** をクリックします。 デバイスの IP アドレスがわからない場合は、[ **設定] [Network & Internet > 詳細オプション >** 確認してください。
4. 上部のメニューバーで、[デバッグ]、[ **デバッグなしで開始** ] の順にクリック >、Ctrl キーを押し **ながら F5** キーを押します。 初めてデバイスをデプロイする場合は、 [Visual Studio とペアリング](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)する必要があります。
5. アプリが展開されたら、 **select ジェスチャ** を使用して、[ **fitbox** ] を閉じます。

イマーシブヘッドセットに展開する場合:

1. Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから **リリース** に、ARM から **x64** に変更します。
2. 配置ターゲットが **ローカルコンピューター** に設定されていることを確認します。
3. 上部のメニューバーで、[デバッグ]、[ **デバッグなしで開始** ] の順にクリック >、Ctrl キーを押し **ながら F5** キーを押します。
4. アプリがデプロイされたら、モーションコントローラーでトリガーをプルして、[ **Fitbox ボックス** を閉じます。

>[!NOTE]
>Visual Studio の [エラー] パネルに赤色のエラーが表示されることがあります。 無視しても安全です。 実際のビルドの進行状況を表示するには、[出力] パネルに切り替えます。 [出力] パネルでエラーが発生した場合は、修正を行う必要があります (多くの場合、スクリプトの間違いが原因です)。

## <a name="chapter-1---awareness"></a>Chapter 1-認識

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a>目標

* 音声コマンドの設計の **Dos とすべき** について説明します。
* **KeywordRecognizer** を使用して、宝石ベースの音声コマンドを追加します。
* ユーザーがカーソル **フィードバック** を使用して音声コマンドを認識できるようにします。

### <a name="voice-command-design"></a>音声コマンドのデザイン

この章では、音声コマンドの設計について学習します。 音声コマンドを作成する場合:

#### <a name="do"></a>DO

* 簡潔なコマンドを作成します。 *"現在選択さ* れているビデオを再生する" を使用しないでください。そのコマンドは簡潔ではなく、ユーザーが簡単に覚えられないからです。 代わりに、 *"Play Video"* を使用する必要があります。これは簡潔で、複数の音節があるためです。
* 単純なボキャブラリを使用します。 ユーザーが簡単に見つけて覚えておくことができる一般的な単語と語句を常に使用してください。 たとえば、アプリケーションで、表示または非表示にできるノートオブジェクトがある場合、"プラカード" はあまり使用されていないため、コマンド *"Show プラカード"* は使用しません。 代わりに、 *"Show note"* コマンドを使用して、アプリケーションでメモを表示します。
* 一貫性を保ちます。 音声コマンドは、アプリケーション全体で一貫した状態に保つ必要があります。 アプリケーションに2つのシーンがあり、両方のシーンにアプリケーションを閉じるためのボタンが含まれているとします。 最初のシーンで *"Exit"* コマンドを使用してボタンをトリガーしたが、2番目のシーンで *"アプリを閉じる"* コマンドを使用した場合、ユーザーは混乱を招きます。 同じ機能を複数のシーンで保持する場合は、同じ音声コマンドを使用してトリガーする必要があります。

#### <a name="dont"></a>できません

* 単一の syllable コマンドを使用します。 たとえば、音声コマンドを作成してビデオを再生する場合は、単純なコマンド *"play"* を使用しないようにする必要があります。これは単一の syllable であり、システムによって簡単に見逃しられる可能性があるためです。 代わりに、 *"Play Video"* を使用する必要があります。これは簡潔で、複数の音節があるためです。
* システムコマンドを使用します。 *"Select"* コマンドは、現在フォーカスがあるオブジェクトに対して Tap イベントをトリガーするためにシステムによって予約されています。 キーワードまたは語句では、予期したとおりに動作しない可能性があるため、 *"Select"* コマンドを再使用しないでください。 たとえば、アプリケーションでキューブを選択するための音声コマンドが *"Select cube"* であったのに、ユーザーがコマンドを発音したときに球を見ていた場合、代わりに球が選択されます。 同様に、アプリケーションバーのコマンドも音声に対応しています。 CoreWindow ビューでは、次の音声コマンドを使用しないでください。
    1. 戻る
    2. スクロールツール
    3. ズームツール
    4. ツールのドラッグ
    5. Adjust
    6. 削除
* 同様のサウンドを使用します。 Rhyme する音声コマンドを使用しないようにしてください。 *"Show Store"* と *"More show More"* がサポートされているショッピングアプリケーションがある場合は、もう一方のコマンドを使用している間に、いずれかのコマンドを無効にする必要があります。 たとえば、[ *Show store]* \ (ストアの表示 \) ボタンを使用してストアを開き、ストアが表示されたときにそのコマンドを無効にして、[ *さらに表示]* コマンドを使用して参照することができます。

### <a name="instructions"></a>手順

* Unity の [ **階層** ] パネルで、検索ツールを使用して **holoComm_screen_mesh** オブジェクトを検索します。
* **HoloComm_screen_mesh** オブジェクトをダブルクリックして、**シーン** で表示します。 これは、音声コマンドに応答する astronaut の watch です。
* [ **インスペクター** ] パネルで、[ **音声入力ソース (スクリプト)** ] コンポーネントを見つけます。
* [ **キーワード** ] セクションを展開して、サポートされている音声コマンドを確認します。 **Communicator を開き** ます。
* 右側にある [歯車] をクリックし、[ **スクリプトの編集**] を選択します。
* **SpeechInputSource.cs** を調べて、 **KeywordRecognizer** を使用して音声コマンドを追加する方法を理解します。

### <a name="build-and-deploy"></a>ビルドと配置

* Unity では、 **ファイル > ビルド設定** を使用して、アプリケーションをリビルドします。
* **アプリ** フォルダーを開きます。
* **Modelexplorer Visual Studio ソリューション** を開きます。

(セットアップ時に Visual Studio でこのプロジェクトを既にビルドまたは展開している場合は、VS のインスタンスを開いて、メッセージが表示されたら [すべて再読み込み] をクリックします)。

* Visual Studio で、[デバッグ]、[ **デバッグなしで開始** ] の順にクリック >、Ctrl キーを押し **ながら F5** キーを押します。
* アプリケーションが HoloLens にデプロイされたら、 [エアタップ](../../../design/gaze-and-commit.md#composite-gestures) ジェスチャを使用して [フィット] ボックスを閉じます。
* Astronaut の watch を見つめます。
* ウォッチにフォーカスがある場合は、カーソルがマイクに変わっていることを確認します。 これにより、アプリケーションが音声コマンドをリッスンしていることを示すフィードバックが提供されます。
* ウォッチにツールヒントが表示されていることを確認します。 これにより、ユーザーは *"Open Communicator"* コマンドを見つけることができます。
* 監視での再生中に、「communicator を *開く」* と言い、communicator パネルを開きます。

## <a name="chapter-2---acknowledgement"></a>Chapter 2-確認

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a>目標

* マイク入力を使用してメッセージを記録します。
* アプリケーションが音声をリッスンしていることをユーザーにフィードバックします。

>[!NOTE]
>マイクから録音するアプリの **マイク** 機能を宣言する必要があります。 これは、MR 入力212で既に行われていますが、独自のプロジェクトでは考慮しておいてください。
>
>1. Unity エディターで、[Edit > Project Settings > Player] の順に移動して、windows media player の設定に移動します。
>2. [ユニバーサル Windows プラットフォーム] タブをクリックします。
>3. [発行設定 > 機能] セクションで、 **マイク** の機能を確認します。

### <a name="instructions"></a>手順

* Unity の [ **階層** ] パネルで、 **holoComm_screen_mesh** オブジェクトが選択されていることを確認します。
* [ **インスペクター** ] パネルで、 **Astronaut Watch (スクリプト)** コンポーネントを見つけます。
* [ **Communicator Prefab** ] プロパティの値として設定されている小さい、blue のキューブをクリックします。
* [ **プロジェクト** ] パネルで、 **Communicator** prefab にフォーカスがあるはずです。
* [**プロジェクト**] パネルの [ **Communicator** prefab] をクリックして、**インスペクター** でそのコンポーネントを表示します。
* **マイクマネージャー (スクリプト)** コンポーネントを見ると、ユーザーの声を記録することができます。
* **Communicator** オブジェクトに、[**メッセージの送信**] コマンドに応答するための **音声入力ハンドラー (スクリプト)** コンポーネントがあることに注意してください。
* **Communicator (スクリプト)** コンポーネントを確認し、スクリプトをダブルクリックして Visual Studio で開きます。

Communicator.cs は、communicator デバイスで適切なボタンの状態を設定する役割を担います。 これにより、ユーザーはメッセージを記録して再生し、astronaut にメッセージを送信できるようになります。 また、アニメーション化された wave フォームを開始および停止して、音声が聞こえたことをユーザーに確認します。

* **Communicator.cs** で、 **Start** メソッドから次の行 (81 と 82) を削除します。 これにより、communicator の [レコード] ボタンが有効になります。

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a>ビルドと配置

* Visual Studio で、アプリケーションをリビルドし、デバイスにデプロイします。
* Astronaut の watch を見つめ、 *「Open communicator」* と言うと、communicator が表示されます。
* [ **録音** ] ボタン (マイク) を押して、astronaut の音声メッセージの録音を開始します。
* 読み上げを開始し、wave アニメーションが communicator で再生されることを確認します。これにより、音声が聞こえたことをユーザーにフィードバックできます。
* [ **停止** ] ボタン (左の四角形) をクリックし、wave アニメーションの実行が停止していることを確認します。
* **再生** ボタン (右三角形) を押して、記録されたメッセージを再生し、デバイスで再生します。
* 記録されたメッセージの再生を停止するには、[ **停止** ] ボタン (右の四角形) をクリックします。
* Communicator を終了し、astronaut から "メッセージを受信しました" という応答を受信するには、 *"メッセージの送信"* と言います。

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a>章 3-およびディクテーション認識エンジンについて

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a>目標

* ディクテーション認識エンジンを使用して、ユーザーの音声をテキストに変換します。
* Communicator でディクテーションエンジンの仮説と最終結果を表示します。

この章では、ディクテーション認識エンジンを使用して、astronaut のメッセージを作成します。 ディクテーション認識エンジンを使用する場合は、次の点に注意してください。

* ディクテーションエンジンが動作するには、WiFi に接続されている必要があります。
* タイムアウトは、一定の時間が経過すると発生します。 次の2つの点に注意する必要があります。
  * 認識エンジンが起動し、最初の5秒間オーディオが聞こえない場合は、タイムアウトします。
  * 認識エンジンが結果を指定した後、20秒間無音の状態になると、タイムアウトします。
* 一度に実行できるのは、1種類のレコグナイザー (キーワードまたはディクテーション) だけです。

>[!NOTE]
>マイクから録音するアプリの **マイク** 機能を宣言する必要があります。 これは、MR 入力212で既に行われていますが、独自のプロジェクトでは考慮しておいてください。
>
>1. Unity エディターで、[Edit > Project Settings > Player] の順に移動して、windows media player の設定に移動します。
>2. [ユニバーサル Windows プラットフォーム] タブをクリックします。
>3. [発行設定 > 機能] セクションで、 **マイク** の機能を確認します。

### <a name="instructions"></a>手順

ディクテーション認識エンジンを使用するように **MicrophoneManager.cs** を編集します。 次のように追加します。

1. [ **レコード] ボタン** が押されると、 **DictationRecognizer が開始** されます。
2. DictationRecognizer が理解したことの **仮説** を示します。
3. DictationRecognizer が理解した **結果** をロックします。
4. DictationRecognizer からのタイムアウトを確認します。
5. [ **停止] ボタン** が押されたとき、または mic セッションがタイムアウトになった場合は、 **DictationRecognizer を停止** します。
6. **KeywordRecognizer** を再起動します。これにより、[**メッセージの送信**] コマンドがリッスンされます。

始めましょう。 **MicrophoneManager.cs** の 3. a のコード演習をすべて完了するか、以下の完成したコードをコピーして貼り付けます。

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone.
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a>ビルドと配置

* Visual Studio でリビルドし、デバイスにデプロイします。
* エアタップジェスチャで [フィット] ボックスを閉じます。
* Astronaut の watch を見つめ、 *"Open Communicator"* と言います。
* [ **録音** ] ボタン (マイク) を選択して、メッセージを記録します。
* 読み上げを開始します。 **ディクテーションレコグナイザー** は、音声を解釈し、そのテキストを communicator で表示します。
* メッセージを記録しているときに、 *"メッセージの送信"* をお試しください。 **ディクテーションレコグナイザー** がまだアクティブであるため、**キーワードレコグナイザー** は応答しないことに注意してください。
* 数秒間読み上げを停止します。 ディクテーションレコグナイザーが仮説を完了し、最終的な結果が表示されることを確認します。
* 読み上げを開始し、20秒間一時停止します。 これにより、 **ディクテーションレコグナイザー** がタイムアウトします。
* 上記のタイムアウト後に、 **キーワード認識エンジン** が再度有効になっていることに注意してください。 これで、communicator は音声コマンドに応答します。
* Astronaut にメッセージを送信するには、 *"メッセージの送信"* と言います。

## <a name="chapter-4---grammar-recognizer"></a>Chapter 4-文法レコグナイザー

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a>目標

* SRGS、または音声認識の文法指定ファイルに従って、ユーザーの音声を認識するには、文法認識エンジンを使用します。

>[!NOTE]
>マイクから録音するアプリの **マイク** 機能を宣言する必要があります。 これは、MR 入力212で既に行われていますが、独自のプロジェクトでは考慮しておいてください。
>
>1. Unity エディターで、[Edit > Project Settings > Player] の順に移動して、windows media player の設定に移動します。
>2. [ユニバーサル Windows プラットフォーム] タブをクリックします。
>3. [発行設定 > 機能] セクションで、 **マイク** の機能を確認します。

### <a name="instructions"></a>手順

1. [ **階層** ] パネルで **Jetpack_Center** を検索して選択します。
2. [**インスペクター** ] パネルで **tagalong** スクリプトを探します。
3. オブジェクトの右側にある小さな円をクリックして、フィールド **にタグを付け** ます。
4. ポップアップ表示されたウィンドウで、[ **Srgstoolbox]** を検索し、一覧から選択します。
5. **Streamingassets** フォルダーの **SRGSColor.xml** ファイルを見てみましょう。
    1. SRGS の設計仕様は、W3C [の web サイトにあります](https://www.w3.org/TR/speech-grammar/)。

この SRGS ファイルには、次の3種類のルールがあります。

* 12色のリストから1色を指定できるルール。
* 色ルールと3つの図形の組み合わせをリッスンする3つのルール。
* ルートルールである colorChooser は、3つの "カラー + シェイプ" ルールの任意の組み合わせをリッスンします。 図形は任意の順序で、任意の量の任意の数を3つにすることができます。 これは、最初の文法タグのファイルの先頭にルートルールとして指定されているので、でリッスンされる唯一のルールです &lt; &gt; 。

### <a name="build-and-deploy"></a>ビルドと配置

* Unity でアプリケーションをリビルドし、Visual Studio からビルドしてデプロイし、HoloLens でアプリを体験します。
* エアタップジェスチャで [フィット] ボックスを閉じます。
* Astronaut の jetpack を見つめ、エアタップジェスチャを実行します。
* 読み上げを開始します。 **文法認識エンジン** は、音声を解釈し、認識に基づいて図形の色を変更します。 コマンドの例としては、"blue circle, 黄色い square" などがあります。
* 別のエアタップジェスチャを実行して、ツールボックスを閉じます。

## <a name="the-end"></a>最後です

おめでとうございます。 これで **MR 入力 212: Voice** が完了しました。

* 音声コマンドの Dos とすべきがわかっています。
* ユーザーが音声コマンドを認識できるように、ツールヒントがどのように使用されたかを見てきました。
* ユーザーの声が聞こえたことを認識するために使用されるフィードバックの種類がいくつかあります。
* キーワードレコグナイザーとディクテーション認識エンジンを切り替える方法と、これら2つの機能が音声を理解し、解釈する方法について説明します。
* アプリケーションで、SRGS ファイルと文法認識エンジンを使用して音声認識を行う方法を学習しました。