---
title: 混合現実向けに 2D UWP アプリを更新する
description: この記事では、既存の2D ユニバーサル Windows プラットフォームアプリを更新して、HoloLens および Windows Mixed Reality のイマーシブヘッドセットで実行する方法について説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 2D アプリ、UWP、フラットアプリ、HoloLens、イマーシブヘッドセット、アプリモデル、戻るボタン、アプリバー、dpi、解像度、スケール、移植、HoloLens 1 世代、HoloLens 2、mixed reality ヘッドセット、windows mixed reality ヘッドセット、移行、Windows 10
ms.openlocfilehash: 4103ee1e5a7169759dfd823b41b5e3fd18011956
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677801"
---
# <a name="updating-2d-uwp-apps-for-mixed-reality"></a>混合現実向けに 2D UWP アプリを更新する

Windows Mixed Reality を使用すると、ユーザーは、お客様の物理的またはデジタルの世界において、ホログラムを適切なものとして表示できます。 主に、HoloLens とデスクトップ Pc の両方を Windows 10 デバイスとして接続します。これは、ストア内のほぼすべてのユニバーサル Windows プラットフォーム (UWP) アプリを2D アプリとして実行できることを意味します。

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a>混合現実向けの 2D UWP アプリの作成

2D アプリを mixed reality ヘッドセットにするための最初の手順は、アプリを標準の2D アプリとしてデスクトップモニターで実行することです。

### <a name="building-a-new-2d-uwp-app"></a>新しい 2D UWP アプリを構築する

混合現実向けの新しい2D アプリを構築するには、標準の2D ユニバーサル Windows プラットフォーム (UWP) アプリを構築するだけです。 他のアプリの変更は、そのアプリが混合現実のスレートとして実行するために必要ありません。

2D UWP アプリの構築を開始するには、 [最初のアプリの作成](https://docs.microsoft.com/windows/uwp/get-started/your-first-app) に関する記事をご覧ください。

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a>既存の2D ストアアプリを UWP に導入する

ストアに既に 2D Windows アプリがある場合は、最初に Windows 10 ユニバーサル Windows プラットフォーム (UWP) を対象としていることを確認する必要があります。 現在、ストアアプリで使用できる可能性があるすべての開始点を次に示します。
<br>

|  開始ポイント  |  AppX マニフェストプラットフォームターゲット  |  ユニバーサルにする方法 | 
|----------|----------|----------|
|  Windows Phone (Silverlight)  |  Silverlight アプリケーションマニフェスト |  [WinRT への移行](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx) | 
|  Windows Phone 8.1 Universal  |  8.1 プラットフォームターゲットを含まない AppX マニフェスト  |  [アプリをユニバーサル Windows プラットフォームに移行する](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows ストア8  |  プラットフォームターゲットを含まない 8 AppX マニフェスト  |  [アプリをユニバーサル Windows プラットフォームに移行する](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows ストア 8.1 Universal  |  8.1 プラットフォームターゲットを含まない AppX マニフェスト  |  [アプリをユニバーサル Windows プラットフォームに移行する](https://msdn.microsoft.com/library/mt148501.aspx) | 

現在、Win32 アプリ ("PC, Mac & Linux スタンドアロン" ビルドターゲット) としてビルドされた 2D Unity アプリがある場合は、Unity を "ユニバーサル Windows プラットフォーム" ビルドターゲットに切り替えることによって、mixed reality をターゲットにすることができます。

ここでは、 [以下](#publish-and-maintain-your-universal-app)の Holographic デバイスファミリを使用して、アプリを HoloLens に限定する方法について説明します。

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a>Windows Mixed Reality のイマーシブヘッドセットで2D アプリを実行する

モニターで開発して試してみるデスクトップコンピューターに2D アプリをデプロイした場合は、既にイマーシブデスクトップヘッドセットで試してみることができます。

Mixed reality ヘッドセット内の [スタート] メニューにアクセスし、そこからアプリを起動します。 デスクトップシェルと holographic シェルの両方で同じ UWP アプリのセットが共有されるため、Visual Studio からデプロイした後は、アプリが既に存在している必要があります。

## <a name="targeting-both-immersive-headsets-and-hololens"></a>イマーシブヘッドセットと HoloLens の両方を対象とする

おめでとうございます。 これで、アプリは Windows 10 ユニバーサル Windows プラットフォーム (UWP) を使用しています。

これで、アプリは現在の windows デバイス (デスクトップ、モバイル、Xbox、Windows Mixed Reality イマーシブヘッドセット、HoloLens など) で実行できるようになり、今後の Windows デバイスでも実行できるようになりました。 ただし、これらのデバイスをすべてターゲットにするには、アプリが Windows のユニバーサルデバイスファミリを対象としていることを確認する必要があります。

### <a name="change-your-device-family-to-windowsuniversal"></a>デバイスファミリを Windows に変更します。 Universal

次に、AppX マニフェストに移動して、Windows 10 UWP アプリが HoloLens で実行できることを確認します。
* **Visual Studio** でアプリのソリューションファイルを開き、アプリのパッケージマニフェストに移動します。
* ソリューション内の package.appxmanifest ファイルを右クリックして、[**コードの表示**] にアクセスし **ます。**<br>
  ![ソリューションエクスプローラーの package.appxmanifest](images/openappxmanifest-500px.png)<br>
* [依存関係] セクションで、ターゲットプラットフォームが Windows. Universal であることを確認します。
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* 保存!

開発環境に Visual Studio を使用しない場合は、任意のテキストエディターで **AppXManifest.xml** を開いて、 **Windows. Universal** *TargetDeviceFamily* を対象としていることを確認できます。

### <a name="run-in-the-hololens-emulator"></a>HoloLens エミュレーターでの実行

UWP アプリが "Windows. Universal" を対象とするようになったので、アプリをビルドして [HoloLens エミュレーター](../platform-capabilities-and-apis/using-the-hololens-emulator.md)で実行しましょう。
* [HoloLens Emulator をインストール済み](../install-the-tools.md) であることを確認します。
* Visual Studio で、アプリの **x86** ビルド構成を選択します。

  ![Visual Studio の [x86] ビルド構成](../platform-capabilities-and-apis/images/x86setting.png)<br>
* [配置ターゲット] ドロップダウン メニューで **[HoloLens エミュレーター]** を選択します

  ![展開ターゲットリストの HoloLens エミュレーター](images/deployemulator-500px.png)<br>
* [デバッグ **> 開始** ] を選択して、アプリを配置し、デバッグを開始します。
* エミュレーターが起動し、アプリが実行されます。
* キーボード、マウス、または Xbox コントローラーで、アプリを世界中に配置して起動します。

  ![UWP サンプルで読み込まれた HoloLens エミュレーター](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a>次のステップ

この時点で、次の2つのいずれかが発生する可能性があります。
1. アプリのスプラッシュが表示され、エミュレーターに配置された後に実行が開始されます。 すごいですね。
2. または、2D ホログラムの読み込みアニメーションが表示されると、読み込みが停止し、スプラッシュスクリーンにアプリが表示されます。 これは、何らかの問題が発生したことを意味します。これは、アプリを Mixed Reality で利用する方法を理解するために、より多くの調査を受けます。

UWP アプリが HoloLens で開始されない原因の概要を把握するには、デバッグする必要があります。

### <a name="running-your-uwp-app-in-the-debugger"></a>デバッガーでの UWP アプリの実行

次の手順では、Visual Studio デバッガーを使用して UWP アプリをデバッグする方法について説明します。
* まだ行っていない場合は、Visual Studio でソリューションを開きます。 ターゲットを **HoloLens エミュレーター** に変更し、ビルド構成を **x86** に変更します。
* [デバッグ **> 開始** ] を選択して、アプリを配置し、デバッグを開始します。
* マウス、キーボード、または Xbox コントローラーを使用して、アプリを世界中に配置します。
* これで、Visual Studio はアプリコード内のどこかで中断するはずです。
  - ハンドルされないエラーが発生しても、アプリがすぐにクラッシュしたりデバッガーに侵入したりしない場合は、アプリのコア機能のテストパスを実行して、すべてが動作していて機能していることを確認してください。 次のようなエラーが表示されることがあります (処理中の内部例外)。 アプリのエクスペリエンスに影響を与える内部エラーが発生しないようにするには、自動テストと単体テストを実行して、すべてが期待どおりに動作することを確認します。

![システム例外を示す UWP サンプルが読み込まれた HoloLens エミュレーター](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a>UI を更新する

UWP アプリが2D ホログラムとしてイマーシブヘッドセットや HoloLens で実行されるようになったので、次は見栄えが良いことを確認します。 次の点を考慮することをお勧めします。
* Windows Mixed Reality は、853x480 有効ピクセルに相当する固定解像度および DPI ですべての2D アプリを実行します。 このスケールで設計を改良する必要があるかどうかを検討し、以下の設計ガイダンスを確認して、HoloLens とイマーシブヘッドセットのエクスペリエンスを向上させてください。
* Windows Mixed Reality では、2d ライブタイル [はサポートされていません](../../design/app-model.md) 。 コア機能がライブタイルに関する情報を表示している場合は、その情報をアプリに戻したり、 [3d アプリランチャー](../../distribute/3d-app-launcher-design-guidance.md)を調べたりすることを検討してください。

### <a name="2d-app-view-resolution-and-scale-factor"></a>2D アプリビューの解像度とスケールファクター

![応答性の高いデザインから](images/scale-500px.png)

Windows 10 は、すべてのビジュアルデザインを実際の画面ピクセルから **有効なピクセル** に移動します。 つまり、開発者は、Windows 10 のヒューマンインターフェイスガイドラインに従って、有効なピクセルに対して UI を設計します。また、Windows のスケーリングにより、デバイス、解像度、DPI などにおける使いやすさに適したサイズになります。詳細につい[ては、この](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx)[ビルドプレゼンテーション](https://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx)をご覧ください。

世界中にさまざまな距離でアプリを配置する独自の機能がある場合でも、テレビと同様の距離を使用することをお勧めします。 そのため、Mixed Reality ホームの仮想スレートには、フラットな UWP ビューが次のように表示されます。

**1280x720、150% DPI** (853x480 有効ピクセル)

この解決策にはいくつかの利点があります。
* この有効なピクセルレイアウトは、タブレットやスモールデスクトップと同じ情報密度を持ちます。
* これは、Xbox One で実行されている UWP アプリの固定 DPI と有効ピクセルに一致し、デバイス間でシームレスなエクスペリエンスを実現します。
* このサイズは、世界中のアプリのさまざまな運用距離にわたってスケーリングされた場合に適しています。

### <a name="2d-app-view-interface-design-best-practices"></a>2D アプリビューインターフェイスの設計のベストプラクティス

**ください**
* スタイル、フォントサイズ、およびボタンのサイズについては、 [Windows 10 ヒューマンインターフェイスガイドライン (HIG)](https://dev.windows.com/design) に従ってください。 HoloLens は、アプリが互換性のあるアプリパターン、読み取り可能なテキストサイズ、および適切なヒットターゲットのサイズを確実に持つように作業を行います。
* UI が [応答性](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx) の高い設計のベストプラクティスに従っていることを確認し、HoloLen の固有の解像度と DPI に最適であることを確認します。
* Windows の "明るい" 色のテーマに関する推奨事項を使用します。

**できません：**
* 混合現実の場合、UI が大幅に変更され、ユーザーがヘッドセットを使い慣れていることを確認できます。

### <a name="understand-the-app-model"></a>アプリモデルを理解する

混合現実の [アプリモデル](../../design/app-model.md) は、多くのアプリが一緒に存在する Mixed reality ホームを使用するように設計されています。 これは、多数の2D アプリを一度に実行するデスクトップに相当する mixed reality と考えることができます。 これは、アプリのライフサイクル、タイル、およびアプリのその他の主要な機能に影響します。

### <a name="app-bar-and-back-button"></a>アプリバーと [戻る] ボタン

2D ビューは、コンテンツの上にあるアプリバーで修飾されます。 アプリバーには、アプリ固有のパーソナル化の2つの点があります。

**タイトル:** アプリインスタンスに関連付けられているタイルの *displayname* を表示します

**戻るボタン:** 押されたときに、 *[バック要求さ](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* れたイベントを発生させます。 戻るボタンの可視性は、 *[Systemnavigationmanager. AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)* によって制御されます。

![2D アプリビューのアプリバー UI](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)<br>
*2D アプリビューのアプリバー UI*

### <a name="test-your-2d-apps-design"></a>2D アプリのデザインをテストする

アプリケーションをテストして、テキストが読み取り可能であること、ボタンが targetable であること、アプリ全体が正しいことを確認することが重要です。 解像度が 1280 x 20% に設定されているデスクトップヘッドセット、HoloLens、エミュレーター、またはタッチデバイスで [テスト](../platform-capabilities-and-apis/testing-your-app-on-hololens.md) することができ @150 ます。

## <a name="new-input-possibilities"></a>新しい入力可能性

HoloLens は高度な深度センサーを使用して世界を見て、ユーザーを表示します。 これにより、 [ブルーム](../../design/system-gesture.md#bloom) や [エアタップ](../../design/gaze-and-commit.md#composite-gestures)などの高度なハンドジェスチャが可能になります。 強力なマイクも [音声エクスペリエンス](../../design/voice-input.md)を実現します。

デスクトップヘッドセットを使用すると、ユーザーは、モーションコントローラーを使用してアプリをポイントし、アクションを実行できます。 また、ゲームパッドを使用することもできます。

Windows では、入力メカニズムを抽象化する[ポインターイベント](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events)に対して、[宝石](../../design/gaze-and-commit.md)、ジェスチャ、音声、およびモーションコントローラーの入力を変換することによって、UWP アプリのこのような複雑さをすべて処理します。 たとえば、ユーザーが手の形でエアタップを行った場合や、選択トリガーをモーションコントローラーで取得した場合、2D アプリケーションは、タッチスクリーンの場合と同様に、2D タッチの押下を認識しているだけではありません。

UWP アプリを HoloLens に持ち込むときの入力について理解しておく必要がある概要の概念とシナリオを次に示します。
* マウスをポイントすると、メニュー、flyouts、またはその他のユーザーインターフェイス要素が予期せずに起動し、アプリに関する情報が表示されるよう[になります](../../design/gaze-and-commit.md)。
* 宝石は、マウス入力ほど正確ではありません。 タッチ対応のモバイルアプリケーションと同様に、HoloLens に適したサイズのヒットターゲットを使用します。 アプリの端付近にある小さな要素は、特に操作が困難です。
* ユーザーは、スクロールから2つの指パンに移動するために入力モードを切り替える必要があります。 アプリがタッチ入力用に設計されている場合は、主要な機能が2本の指パンの背後でロックされていないことを確認してください。 その場合は、2つの指パンを開始できるボタンのような別の入力機構を使用することを検討してください。 たとえば、Maps アプリでは、2つの指パンでズームできますが、1回のクリックで同じズーム操作をシミュレートするには、プラス、マイナス、および回転ボタンがあります。

[音声入力](../../design/voice-input.md) は、mixed reality エクスペリエンスの重要な部分です。 ヘッドセットを使用すると、Cortana の電源をオンにしている Windows 10 のすべての speech Api が有効になりました。

## <a name="publish-and-maintain-your-universal-app"></a>ユニバーサルアプリの発行と管理

アプリが起動して実行されたら、アプリをパッケージ化して [Microsoft Store に送信](../../distribute/submitting-an-app-to-the-microsoft-store.md)します。

## <a name="see-also"></a>関連項目
* [アプリ モデル](../../design/app-model.md)
* [頭の視線入力とコミット](../../design/gaze-and-commit.md)
* [モーション コントローラー](../../design/motion-controllers.md)
* [音声入力](../../design/voice-input.md)
* [Microsoft Store へのアプリの送信](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [HoloLens エミュレーターを使用する](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
