---
title: MR 入力 211 - ジェスチャ
description: Unity、Visual Studio、および HoloLens を使用したこのコーディングのチュートリアルに従って、ジェスチャの概念の詳細を確認してください。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit、academy、チュートリアル、ジェスチャ、HoloLens、Mixed Reality Academy、unity、mixed reality ヘッドセット、windows Mixed reality ヘッドセット、virtual Reality ヘッドセット、Windows 10
ms.openlocfilehash: dfb31901001f760abd60bda3022902267b7c05cf
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583706"
---
# <a name="mr-input-211-gesture"></a>MR 入力 211:ジェスチャ

>[!NOTE]
>Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。  そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。  これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。  これらは、サポートされているデバイス上で継続して動作するように、保守されます。 HoloLens 2 向けには、[新しいチュートリアル シリーズ](./mr-learning-base-01.md)が投稿されています。

[ジェスチャ](../../../design/gaze-and-commit.md#composite-gestures) によって、ユーザーの意図が動作するようになります。 ユーザーはジェスチャを使用して、ホログラムを操作できます。 このコースでは、ユーザーの手を追跡し、ユーザー入力に応答して、手動による状態と場所に基づいてユーザーにフィードバックを送る方法について説明します。

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

[MR 基本 101](../../../develop/unity/tutorials/holograms-101.md)では、単純なエアタップジェスチャを使用して、ホログラムを操作していました。 ここでは、エアタップのジェスチャを超えて、次のような新しい概念を見ていきます。

* ユーザーの手が追跡されていることを検出し、ユーザーにフィードバックを提供します。
* ナビゲーションジェスチャを使用して、ホログラムを回転させます。
* ユーザーの手が消えようとしているときにフィードバックを提供します。
* 操作イベントを使用して、ユーザーが自分でホログラムを移動できるようにします。

このコースでは、 [MR 入力 210](holograms-210.md)で構築した Unity プロジェクト **モデルエクスプローラー** について説明します。 Astronaut の友人は、これらの新しいジェスチャの概念をご紹介します。

>[!IMPORTANT]
>以下の各章に埋め込まれているビデオは、古いバージョンの Unity と Mixed Reality Toolkit を使用して記録されています。 ステップバイステップの手順は正確であり、最新のものですが、最新ではない対応するビデオにスクリプトとビジュアルが表示される場合があります。 ビデオはために含まれています。ここで説明する概念は引き続き適用されます。

## <a name="device-support"></a>デバイス サポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td>MR 入力 211:ジェスチャ</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始する前に

### <a name="prerequisites"></a>前提条件

* 適切な [ツールがインストール](../../../develop/install-the-tools.md)された WINDOWS 10 PC。
* 基本的な C# プログラミング機能。
* [MR の基本 101](../../../develop/unity/tutorials/holograms-101.md)を完了している必要があります。
* [MR 入力 210](holograms-210.md)を完了している必要があります。
* [開発用に構成され](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)た HoloLens デバイス。

### <a name="project-files"></a>プロジェクト ファイル

* プロジェクトに必要な [ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) をダウンロードします。 Unity 2017.2 以降が必要です。
* ファイルをデスクトップまたはその他の簡単な場所に保管します。

>[!NOTE]
>ダウンロードする前にソースコードを確認する場合は、GitHub から [入手でき](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture)ます。

### <a name="errata-and-notes"></a>エラッタとメモ

* コード内のブレークポイントにヒットするには、Visual Studio の [ツール]->オプション->デバッグ] の下にある [マイコードのみを有効にする] を無効 (*オフ*) にする必要があります。

## <a name="chapter-0---unity-setup"></a>章 0-Unity のセットアップ

### <a name="instructions"></a>Instructions

1. Unity を起動します。
2. **[Open]** を選択します。
3. 以前にアーカイブしていない **ジェスチャ** フォルダーに移動します。
4. [モデルエクスプローラーの **開始**] フォルダーを見つけて選択し / ます。
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

## <a name="chapter-1---hand-detected-feedback"></a>第1章でのフィードバックの検出

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>目標

* ハンドトラッキングイベントをサブスクライブします。
* カーソルのフィードバックを使用して、ユーザーを追跡しているときにユーザーを表示します。

>[!NOTE]
>HoloLens 2 では、両手が表示されると (指が指されているときだけではなく)、ハンド検出が発生します。

### <a name="instructions"></a>Instructions

* [ **階層** ] パネルで、[ **inputmanager** ] オブジェクトを展開します。
* **GesturesInput** オブジェクトを探して選択します。

**InteractionInputSource.cs** スクリプトは、次の手順を実行します。

1. Interactionsourcedetected イベントと Interactionsourcedetected イベントをサブスクライブします。
2. "ハンドラー検出" 状態を設定します。
3. Interactionsourcedetected イベントと Interactionsourcedetected イベントからアンサブスクライブします。

次に、ユーザーの操作に応じてフィードバックが表示されるように、 [MR 入力 210](holograms-210.md) からカーソルをアップグレードします。

1. [ **階層** ] パネルで、 **カーソル** オブジェクトを選択して削除します。
2. [ **プロジェクト** ] パネルで、[ **カーソルとフィードバック** ] を検索し、[ **階層** ] パネルにドラッグします。
3. [**階層**] パネルの [ **inputmanager** ] をクリックし、[カーソル] の下 **にある [** カーソル] フィールドを、**階層** から Inputmanager の **simplesingleポインターセレクター** の **カーソル** フィールドにドラッグし **ます。**
4. **階層** 内の **カーソル** をクリックします。
5. [**インスペクター** ] パネルで、**オブジェクトカーソル** スクリプトの [**カーソル状態データ**] を展開します。

**カーソル状態データ** は次のように動作します。

* **観察** 状態は、何も検出されず、ユーザーが単に見ていることを意味します。
* **対話** 状態とは、手動またはコントローラーが検出されたことを意味します。
* **ホバー** 状態は、ユーザーがホログラムを見ていることを意味します。

### <a name="build-and-deploy"></a>ビルドと配置

* Unity では、 **ファイル > ビルド設定** を使用して、アプリケーションをリビルドします。
* **アプリ** フォルダーを開きます。
* まだ開いていない場合は、 **Modelexplorer Visual Studio ソリューション** を開きます。
  * (セットアップ時に Visual Studio でこのプロジェクトを既にビルドまたは展開している場合は、VS のインスタンスを開いて、メッセージが表示されたら [すべて再読み込み] をクリックします)。
* Visual Studio で、[デバッグ]、[ **デバッグなしで開始** ] の順にクリック >、Ctrl キーを押し **ながら F5** キーを押します。
* アプリケーションが HoloLens にデプロイされたら、エアタップジェスチャを使用して、[fitbox ボックスを閉じます。
* 手動での追跡を開始するには、自分をビューに移動して、インデックスの指を空にします。
* 左、右、下へ移動します。
* ハンドが検出され、ビューから失われたときに、カーソルがどのように変化するかを見てください。
* イマーシブヘッドセットを使用している場合は、コントローラーに接続して接続を切断する必要があります。 接続されたコントローラーは常に "利用可能" になるため、このフィードバックはイマーシブデバイスではあまり興味がありません。

## <a name="chapter-2---navigation"></a>第2章-ナビゲーション

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>目標

* Astronaut を回転させるには、ナビゲーションジェスチャイベントを使用します。

### <a name="instructions"></a>Instructions

アプリでナビゲーションジェスチャを使用するには、 **GestureAction.cs** を編集して、ナビゲーションジェスチャが発生したときにオブジェクトを回転させます。 また、ナビゲーションが利用可能になったときに表示されるように、カーソルにフィードバックを追加します。

1. [ **階層** ] パネルで、[ **カーソルとフィードバック**] を展開します。
2. **ホログラム** フォルダーで、 **scrollfeedback** 資産を見つけます。
3. **スクロールフィードバック** の Prefab を **階層** 内の **カーソル** にドラッグアンドドロップします。
4. [ **カーソル**] をクリックします。
5. [ **インスペクター** ] パネルで、[ **コンポーネントの追加** ] ボタンをクリックします。
6. メニューで、検索ボックスに「カーソルの **フィードバック**」と入力します。 検索結果を選択します。
7. **インスペクター** の [ **Cursor フィードバック**] コンポーネントの [**検出されたゲームオブジェクトをスクロール**] プロパティに、**階層** から **scrollfeedback** オブジェクトをドラッグアンドドロップします。
8. [ **階層** ] パネルで、 **AstroMan** オブジェクトを選択します。
9. [ **インスペクター** ] パネルで、[ **コンポーネントの追加** ] ボタンをクリックします。
10. メニューで、[検索ボックスのジェスチャ] **アクション** を入力します。 検索結果を選択します。

次に、Visual Studio で **GestureAction.cs** を開きます。 演習 2. c のコーディングで、スクリプトを編集して次の操作を実行します。

1. ナビゲーションジェスチャが実行されるたび **に、AstroMan オブジェクトを回転** します。
2. **RotationFactor** を計算して、オブジェクトに適用される回転の量を制御します。
3. ユーザーが手を左または右に移動したときに y 軸を中心に **オブジェクトを回転** します。

スクリプトで演習 2. c のコーディングを完了するか、以下の完成したソリューションでコードを置き換えます。

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

他のナビゲーションイベントには、何らかの情報が既に入力されていることがわかります。 ユーザーは、ローテーションが開始されたときに、ユーザーが Astronaut にフォーカスを保持する必要がないように、このオブジェクトを Toolkit の InputSystem's モーダルスタックにプッシュします。 同様に、ジェスチャが完了すると、そのオブジェクトはスタックからポップされます。

### <a name="build-and-deploy"></a>ビルドと配置

1. Unity でアプリケーションをリビルドし、Visual Studio からビルドしてデプロイし、HoloLens で実行します。
2. Astronaut を見つめて、カーソルの両側に2つの矢印が表示されます。 この新しいビジュアルは、astronaut を回転できることを示しています。
3. HoloLens がハンドの追跡を開始するように、自分を準備完了の位置 (インデックスは空の指) に置きます。
4. Astronaut を回転させるには、インデックスの指をピンチの位置に下げ、手を左または右に移動して NavigationX ジェスチャをトリガーします。

## <a name="chapter-3---hand-guidance"></a>第3章-ガイダンス

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>目標

* ハンド **ガイダンススコア** を使用して、ハンドトラッキングがいつ失われるかを予測できます。
* ユーザーがカメラのビューの端に近づいたときに表示されるように **、カーソルに関するフィードバック** を提供します。

### <a name="instructions"></a>Instructions

1. [ **階層** ] パネルで、[ **カーソルとフィードバック** ] オブジェクトを選択します。
2. [ **インスペクター** ] パネルで、[ **コンポーネントの追加** ] ボタンをクリックします。
3. メニューの [検索] ボックスに「」と **入力します。** 検索結果を選択します。
4. [ **プロジェクト** ] パネルの [ **ホログラム** ] フォルダーで、[ファイル] [ **guidguid] [フィードバック** ] 資産を見つけます。
5. [**インスペクター** ] パネルの [**ハンドガイダンスインジケーター** ] プロパティに、[ハンドラー] の [配布の **フィードバック**] 資産をドラッグアンドドロップします。

### <a name="build-and-deploy"></a>ビルドと配置

* Unity でアプリケーションをリビルドし、Visual Studio からビルドしてデプロイし、HoloLens でアプリを体験します。
* 手の形にして、インデックスの指を見て追跡します。
* ナビゲーションジェスチャを使用して astronaut の回転を開始します (インデックスの指とつまみを一緒にピンチします)。
* 左、右、上、下へ移動します。
* ジェスチャフレームの端に近づくと、カーソルの横に矢印が表示され、ハンドトラッキングが失われることを警告します。 矢印は、追跡が失われないようにするために、どの方向にハンドを移動するかを示します。

## <a name="chapter-4---manipulation"></a>章 4-操作

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>目標

* 操作イベントを使用して、astronaut を自分の手に移動します。
* カーソルに関するフィードバックを提供して、操作を使用できるタイミングをユーザーに知らせます。

### <a name="instructions"></a>Instructions

GestureManager.cs と AstronautManager.cs では、次のことを行うことができます。

1. Speech キーワード "**Move Astronaut**" を使用して **操作** ジェスチャを有効にし、"**Rotate Astronaut**" を使用して無効にします。
2. **操作ジェスチャレコグナイザー** に応答するように切り替えます。

では、始めましょう。

1. [ **階層** ] パネルで、新しい空の作成オブジェクトを作成します。 "**AstronautManager**" という名前を指定します。
2. [ **インスペクター** ] パネルで、[ **コンポーネントの追加** ] ボタンをクリックします。
3. メニューで、検索ボックスに「 **Astronaut Manager**」と入力します。 検索結果を選択します。
4. [ **インスペクター** ] パネルで、[ **コンポーネントの追加** ] ボタンをクリックします。
5. メニューで、[検索] ボックスに「 **音声入力ソース**」と入力します。 検索結果を選択します。

ここで、astronaut の相互作用の状態を制御するために必要な音声コマンドを追加します。

1. **インスペクター** の [**キーワード**] セクションを展開します。
2. 右側にあるをクリックして、 **+** 新しいキーワードを追加します。
3. 「 **Move Astronaut**」というキーワードを入力します。 必要に応じて、キーのショートカットを自由に追加できます。
4. 右側にあるをクリックして、 **+** 新しいキーワードを追加します。
5. 「 **Rotate Astronaut**」というキーワードを入力します。 必要に応じて、キーのショートカットを自由に追加できます。
6. 対応するハンドラーコードは、 **GestureAction.cs** の **ISpeechHandler** ハンドラーにあります。

![第4章の音声入力ソースを設定する方法](images/holograms211-speech.png)

次に、カーソルに対する操作に関するフィードバックを設定します。

1. [ **プロジェクト** パネル] の [ **ホログラム** ] フォルダーで、 **pathingfeedback** 資産を見つけます。
2. **Pathingfeedback** の Prefab を **階層** 内の **カーソル** にドラッグアンドドロップします。
3. [ **階層** ] パネルで、[ **カーソル**] をクリックします。
4. **Pathingfeedback** オブジェクトを **階層** から、**インスペクター** の [ **Cursor フィードバック**] コンポーネントの [**パス検出されたゲームオブジェクト**] プロパティにドラッグアンドドロップします。

次のように、 **GestureAction.cs** にコードを追加する必要があります。

1. **IManipulationHandler** 関数にコードを追加します。この関数は、**操作** ジェスチャが検出されたときに astronaut を移動します。
2. **移動ベクター** を計算して、astronaut が手の位置に基づいて移動される場所を決定します。
3. Astronaut を新しい位置に **移動** します。

**GestureAction.cs** のコードを完全にコーディングするか、以下の完成したソリューションを使用します。

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a>ビルドと配置

* Unity でリビルドし、Visual Studio からビルドしてデプロイし、HoloLens でアプリを実行します。
* HoloLens の前に手を置き、インデックスの指を上げて追跡できるようにします。
* Astronaut の上にカーソルを置きます。
* 操作ジェスチャを使用して Astronaut を移動するには、「Move Astronaut」と言います。
* カーソルの周囲に4つの矢印が表示され、プログラムが操作イベントに応答するようになったことを示します。
* インデックスを親指に下げて、pinched にしておきます。
* お客様の手を移動すると、astronaut も移動します (これは操作です)。
* Astronaut の操作を停止するには、インデックスの指を上げます。
* 注: 移動前に "Move Astronaut" と表示されない場合は、代わりにナビゲーションジェスチャが使用されます。
* "Rotate Astronaut" と言い、rotatable 状態に戻ります。

## <a name="chapter-5---model-expansion"></a>第5章-モデルの拡張

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>目標

* Astronaut モデルを、ユーザーが対話できる複数の小さなピースに拡張します。
* ナビゲーションと操作のジェスチャを使用して、各部分を個別に移動します。

### <a name="instructions"></a>Instructions

このセクションでは、次のタスクを実行します。

1. 新しいキーワード "**Expand model**" を追加して、astronaut モデルを展開します。
2. 新しいキーワード "**Reset model**" を追加して、モデルを元の形式に戻します。

これを行うには、前の章で説明した音声入力ソースに2つのキーワードを追加します。 また、認識イベントを処理する別の方法についても説明します。

1. **インスペクター** の [Back on **AstronautManager** ] をクリックし、**インスペクター** の [**キーワード**] セクションを展開します。
2. 右側にあるをクリックして、 **+** 新しいキーワードを追加します。
3. [ **モデルの展開**] としてキーワードを入力します。 必要に応じて、キーのショートカットを自由に追加できます。
4. 右側にあるをクリックして、 **+** 新しいキーワードを追加します。
5. 「 **Reset Model**」というキーワードを入力します。 必要に応じて、キーのショートカットを自由に追加できます。
6. [ **インスペクター** ] パネルで、[ **コンポーネントの追加** ] ボタンをクリックします。
7. メニューで、[検索] ボックスに「 **音声入力ハンドラー**」と入力します。 検索結果を選択します。
8. これらのコマンドは、注目しているすべてのオブジェクトに関係なく動作するようにするため、 **グローバルリスナーである** ことを確認してください。
9. ボタンをクリックし、[ **+** キーワード] ドロップダウンから [ **モデルの展開** ] を選択します。
10. [応答] の下をクリック **+** し、 **AstronautManager** を **階層** から [ **なし] (オブジェクト)** フィールドにドラッグします。
11. 次に、[ **関数なし** ] ドロップダウンをクリックし、[ **AstronautManager**]、[ **expandmodelcommand**] の順に選択します。
12. 音声入力ハンドラーの **+** ボタンをクリックし、[キーワード] ドロップダウンから [ **モデルのリセット** ] を選択します。
13. [応答] の下をクリック **+** し、 **AstronautManager** を **階層** から [ **なし] (オブジェクト)** フィールドにドラッグします。
14. 次に、[ **関数なし** ] ドロップダウンをクリックし、[ **AstronautManager**]、[ **resetmodelcommand**] の順に選択します。

![第5章の音声入力ソースとハンドラーを設定する方法](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>ビルドと配置

* 試してみる アプリをビルドして HoloLens にデプロイします。
* 拡張された astronaut モデルを表示するには、[ **モデルの展開** ] を言います。
* **ナビゲーション** を使用して、astronaut スーツの個々の要素を回転します。
* たとえば、 **Astronaut を移動** してから、 **操作** を使用して Astronaut スーツの各部分を移動します。
* **Astronaut を回転** させて、ピースを再び回転させます。
* Astronaut を元の形式に戻すには、 **Model をリセット** します。

## <a name="the-end"></a>最後です

お疲れさまでした。 これで **MR 入力 211: ジェスチャ** が完了しました。

* ハンドトラッキング、ナビゲーション、操作のイベントを検出して対応する方法がわかります。
* ナビゲーションジェスチャと操作ジェスチャの違いを理解します。
* カーソルを変更して、ハンドが検出されたとき、ハンドが失われるタイミング、およびオブジェクトが異なる相互作用 (ナビゲーションと操作) をサポートするタイミングについて視覚的にフィードバックを提供する方法を理解している。