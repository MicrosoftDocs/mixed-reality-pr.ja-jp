---
title: Windows Mixed Reality で SteamVR を使用する
description: Windows Mixed Reality ヘッドセットと互換性のある Pc を使用するコントローラーで、SteamVR ゲームを設定して再生する方法について説明します。
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、ゲーム、SteamVR、蒸気、システム要件
ms.openlocfilehash: 01fac0f6ce88e473da8a8d9300a4169b37b74078
ms.sourcegitcommit: b13c517df19179ca281362a1f006914289c58ad4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98031968"
---
# <a name="using-steamvr-with-windows-mixed-reality"></a>Windows Mixed Reality で SteamVR を使用する

Windows mixed Reality for SteamVR では、ユーザーは Windows Mixed Reality のイマーシブヘッドセットで SteamVR エクスペリエンスを実行できます。 SteamVR 用の Windows Mixed Reality をインストールした後、ユーザーは自分のデスクトップまたは蒸気 library からお気に入りの SteamVR アプリケーションを起動し、Windows ヘッドセットで直接再生できます。

## <a name="get-your-pc-ready"></a>PC の準備

* 保留中の更新プログラムがないことを確認する: [開始 > 設定] を選択し、 **& セキュリティ > Windows Update を更新 >** ます。 更新プログラムが利用可能な場合は、[ **今すぐインストール**] を選択します。 利用可能な更新プログラムがない場合は、[ **更新プログラムの確認**] を選択して、新しいものをインストールします。
* PC の要件は、ストリームのアプリとコンテンツによって異なります。 タイトルごとの最小要件を参照してください。 GTX 1070 グラフィックスカード (またはそれと同等) と Intel® Core™ i7 プロセッサを搭載した PC では、さまざまなタイトルの優れたエクスペリエンスが提供されます。
* [Windows Mixed Reality](set-up-windows-mixed-reality.md)をまだセットアップしていない場合は設定します。 

## <a name="set-up-windows-mixed-reality-for-steamvr"></a>SteamVR 用に Windows Mixed Reality を設定する

1. [SteamVR をダウンロードしてインストールします。](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe)
2. 準備ができたら、SteamVR を開始します。 SteamVR チュートリアルは、自動的に開始されます。

> **注:** SteamVR セットアップの高度なトラブルシューティングを行うには、次のソフトウェアコンポーネントがインストールされていることを確認します。
> 1. [ストリーム](http://store.steampowered.com/about/)と **ログイン** をインストールするか **、新しいアカウントを作成します。**
> 2. [Steamvr](https://store.steampowered.com/app/250820/SteamVR/)をインストールします。 ヘッドセットを接続した状態で、ストリームを起動します。 SteamVR をインストールするように求めるダイアログが表示されます。 ダイアログの指示に従ってインストールします。
    * ポップアップが表示されない場合は、*ライブラリ* の [*ツール*] セクションに移動して、steamvr をインストールします。 リストで SteamVR を見つけて右クリックし、[ *Install Game*] \ (ゲームのインストール \) を選択します。
> 3. [SteamVR 用の Windows Mixed Reality を](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)インストールします。

## <a name="play-steamvr-games"></a>SteamVR ゲームをプレイする

1. ヘッドセットを PC に接続し、モーションコントローラーをオンにします。
2. Windows Mixed Reality ホームが読み込まれ、コントローラーが表示されたら、デスクトップでストリームアプリを開きます。
3. 蒸気 app を使用して、ストリームライブラリから SteamVR ゲームを起動します。

**ヒント**: ヘッドセットをオフにせずに SteamVR ゲームを起動するには、デスクトップアプリ (**開始 > デスクトップ**) を使用して、Windows MIXED Reality 内の PC デスクトップを表示し、操作します。

## <a name="using-motion-controllers-with-steamvr"></a>SteamVR でのモーションコントローラーの使用

さまざまなゲームで、モーションコントローラーを別々に使用します。 使用を開始する際に役立つ基本事項をいくつか次に示します。

* 蒸気 dashboard を開くには、左または右のサムスティックを右に押します。
* SteamVR ゲームを終了し、Windows Mixed Reality ホームに戻るには、[Windows] ボタンを押します。

## <a name="changing-the-resolution"></a>解像度の変更

より高い解像度でゲームをプレイする場合は、[SteamVR-> の設定-> アプリケーション] ウィンドウのアプリケーションの解像度スライダーをいつでも調整できます。 * * 高い解像度の乗数を使用すると、ゲームが PC により多くの負担をかけることが予想されます。 乗数を増やしてパフォーマンスが低下している場合は、スライダーを既定のレベルに再調整し、ゲームを再起動して変更が反映されるようにします。![アプリケーションの解像度の調整](images/SteamVR_Settings_Applications.png)

## <a name="using-multiple-headsets"></a>複数のヘッドセットの使用

VR の場合は、同じ PC で複数の VR ヘッドセットを定期的に使用することがあります。 Windows Mixed Reality ヘッドセットが電源に接続されている場合、常に Windows Mixed Reality ヘッドセットが起動されることに注意してください。 別のヘッドセットで SteamVR ゲームを起動する場合は、最初に Windows Mixed Reality ヘッドセットを抜いてから続行してください。

## <a name="preview-programs"></a>プログラムのプレビュー

Windows Mixed Reality のイマーシブヘッドセットで SteamVR を使用した場合のパフォーマンス、信頼性、および全体的なエクスペリエンスを向上させるために、定期的な更新プログラムをリリースします。 これらのプレビュープログラムはどれも必須ではありませんが、更新プログラムを迅速かつ頻繁に入手する場合 (およびそれらの更新プログラムについてのフィードバックをお寄せください) に参加することをお勧めします。

### <a name="windows-mixed-reality-for-steamvr-beta"></a>SteamVR Beta 用の Windows Mixed Reality

SteamVR の windows Mixed Reality は、蒸気 Amvr が Windows Mixed Reality ヘッドセットと連携できるようにする、ストリームストアからインストールするコンポーネントです。  この "ブリッジ" への更新プログラムは定期的に公開され、蒸気によって自動的にインストールされます。

更新プログラムをより頻繁に入手する場合は、パブリックベータ版に参加することをお勧めします。  更新プログラムは、最初にベータ版のユーザーに配信されます。フィードバックを使用して、すべてのユーザーに公開する前に、更新プログラムが高品質であることを確認します。  ベータプログラムに含まれていない場合は、最終的に同じ修正プログラムと機能をすべて取得できますが、ベータ版のユーザーによってテストされます。

参加するには:

  1. ストリームで、[ **ライブラリ** ] メニューの下にあるドロップダウンを使用して、 **ソフトウェア** にフィルターを適用します。
  2. 一覧で、[ **Windows Mixed Reality For SteamVR** ] を右クリックし、[ **プロパティ**] を選択します。
  3. [ **ベータ** ] タブを選択します。
  4. **"ベータ-パブリックベータ"** を選択し、[**閉じる**] を選択して確定します。 ベータ版のアクセスコードフィールドは空白のままにする必要があります。
  
### <a name="steamvr-beta"></a>SteamVR ベータ版

SteamVR はバルブによって構築およびリリースされ、すべての SteamVR ヘッドセットで共通です。  また、すべてのユーザーに公開する前に、ベータメンバーの更新をリリースする同様のモデルに従います。

参加するには:

  1. ストリームで、[ **ライブラリ** ] メニューのドロップダウンを使用して、 **ツール** にフィルターを適用します。
  2. 一覧で [ **Steamvr** ] を右クリックし、[ **プロパティ**] を選択します。
  3. [ **ベータ** ] タブを選択します。
  4. **"ベータ-パブリックベータ"** を選択し、[**閉じる**] を選択して確定します。  ベータ版のアクセスコードフィールドは空白のままにする必要があります。 ![SteamVR の [プロパティ] ダイアログで SteamVR beta に切り替えます。](images/steamvr-beta.png)

### <a name="windows-insider-program"></a>Windows Insider Program

Windows Mixed Reality は、Windows 10 の一部です。  SteamVR ユーザーに影響を与える多くの修正と機能は、Windows OS に付属しています。  最新の Windows 10 preview ビルドを試したい場合は、 [Windows Insider program](https://insider.windows.com)に参加することをお勧めします。

## <a name="enabling-motion-reprojection-for-steamvr-apps"></a>SteamVR アプリのモーション reprojection の有効化

SteamVR の Windows Mixed Reality には、90 FPS の再プロジェクションをよりスムーズに行うための実験的なモーション再プロジェクション機能があります。

モーション再投影が有効になっている場合、すべてのストリーム VR ゲームはとを1/2 フレームレート (90 FPS ではなく 45 fps) でレンダリングしますが、SteamVR の Windows Mixed Reality は、GPU によって生成されたモーションベクターを使用して次のフレームを推定します。 特定の PC で 60 FPS + を確実にヒットする SteamVR ゲームの場合、これにより、快適なエクスペリエンスを維持しながら、非常に頻繁なアーティファクトによる 90 FPS エクスペリエンスが実現されます。

使用可能なモーション再プロジェクションモードは次のとおりです。

* **アプリごとの Steamvr 設定**: STEAMVR 設定 UI を使用してモーションの再プロジェクションを制御できます。 次に、SteamVR 設定を開き、[ビデオ > Per-Application ビデオの設定] に移動して、[モーションスムージング] のオプションを選択します。
* **Auto**: ゲームが 90 FPS を維持するのに時間がかかりすぎる場合に、モーション再プロジェクションを自動的に有効にします。 ゲームが 90 FPS の維持を開始したり、45 FPS 未満でレンダリングを開始したりすると、モーション reprojection はオフになります。 非同期回転の再プロジェクションは常に有効になります。
* **Motion vector**: モーションベクターの再プロジェクションを使用して、アプリケーションが常に半フレームで実行されるようにします。
* **None**: モーションの再プロジェクションを無効にします。

**期待されるビジュアル成果物** 

1. 150% を超えるアプリケーションの解決を使用すると、ぼかしが発生する可能性があります。 モーション reprojection を使用する場合は、150% 未満の値を使用することをお勧めします。
2. 鋭いコントラストの端やテキスト (特に、ゲーム内の Ds またはメニュー) は、disocclusion ルージョンによって一時的にワープまたは変形する可能性があります。
3. PC 上で 50-60 FPS に確実にヒットしない他の多くのゲームは、このモードでは引き続き快適に動作します。
4. 一部のゲームは、50% の速度で実行されるか、待機時間 (lag) の増加によって報告されています。 以下の [Windows フィードバックハブ](filing-feedback.md) の指示に従って、これらのゲームについて報告してください。

最初に、最近の世代 NVidia Gpu の実験的なサポートがあります。 さらに多くの Gpu でのモーション再プロジェクションサポートの繰り返しと改善を続けており、お客様からのフィードバックをお待ちしています。

**サポートされている gpu:** Nvidia GeForce GTX1060、AMD RX470 以上、Windows Mixed Reality 互換グラフィックスドライバーがインストールされています。

モーション再投影を有効にするには

1. 前述の手順に従って、 **SteamVR Beta 用の Windows Mixed Reality** を選択していることを確認します。
2. SteamVR ダッシュボードを開きます。
3. Windows Mixed Reality のロゴが付いた左側のボタンを選択して、 **Windows Mixed reality For SteamVR** 設定を開きます。
4. ポップアップ表示された UI で、[グラフィックス] タブを選択します。
5. 自動モーション再プロジェクションを有効にするには、"既定の SteamVR アプリモーション reprojection モード" に対して [自動] を選択します。

![SettingsUX を使用して LSR & LSR インジケーターを有効にする](images/settingsux-enable-lsr.gif)

**モーションの再プロジェクションインジケーター**

モーション reprojection インジケーターは、試験的な自動モーション再プロジェクション機能の問題を診断するのに役立ちます。 True に設定すると、自動モーション再プロジェクション中にヘッドセットの左上にインジケーターが表示されます。 このインジケーターの色と位置は、現在のモーション再プロジェクションモードに対応しています。例については、次の図を参照してください。

![mvLSR インジケーター](images/mvLSRIndicator.png)

緑 = アプリケーションは完全なフレームレートでレンダリングできるため、モーション reprojection はオフになっています。

水色 = アプリケーションが cpu にバインドされているため、モーション reprojection がオンになっています。

Blue = アプリケーションが gpu にバインドされているため、モーション reprojection がオンになっています。

赤 = アプリケーションが半分のフレームレートで実行されているため、モーション reprojection がオフになっています。スーパーサンプリングを減らす場合は、有効にしてください。

緑 + 水色 + 青 = モーション再投影が半フレームモードであるか、アプリケーションがモーション再プロジェクションを要求しました。

## <a name="sharing-feedback-on-steamvr"></a>SteamVR でのフィードバックの共有

Windows Mixed Reality SteamVR エクスペリエンスを向上させるために、お客様のフィードバックは非常に重要です。 [Windows フィードバックハブ](filing-feedback.md)を通じてすべてのフィードバックとバグを送信します。 フィードバックを最大限に活用するには、次の推奨事項に従ってください。

1. フィードバックハブで、"フィードバックの種類" に関する新しい問題を報告していることを示しています。 セクションを参照してください。
2. [ **Mixed Reality** ] カテゴリと [ **アプリ** ] サブカテゴリを選択します。
3. 問題の概要に "SteamVR" という単語を配置します。 これにより、フィードバックを見つけることができます。
4. 問題が発生したときに使用していた SteamVR ゲームまたはアプリケーションについて説明します。
5. お客様のフィードバックに SteamVR システムレポートを添付することを検討してください。 これにより、問題の診断に役立つより多くのログが提供されます。
    1. SteamVR ウィンドウ (コントローラーの状態を表示する小さいウィンドウ) で、タイトルを選択してメニューを開きます。
    2. [システムレポートの作成] を選択します。
    3. ファイルに保存します。
    4. 生成されたファイルをフィードバックハブエントリに直接添付します。
6. SteamVR パフォーマンスに関するフィードバックがある場合は、Mixed Reality パフォーマンストレースを収集します。 
    1. [ **問題の再作成** ] ボタンを選択します。
    2. [データに関する情報を含める] の横にあるドロップダウンリストで、[ **Mixed Reality Performance**] を選択します。
    3. ゲームが実行されていることを確認し、[ **キャプチャの開始**] を選択します。
    4. ゲームをプレイしてトレースをキャプチャするのに数秒かかります。 10-15 秒以上トレースをキャプチャしないようにするか、または大きすぎて送信できません。
    5. [ **キャプチャの停止**] を選択します。
7. 残りのフィールドを完了したら、[ **送信** ] を選択します。

共有する質問やコメントがある場合は、 [ストリームフォーラム](http://steamcommunity.com/app/719950/discussions/)からもご連絡いただけます。

## <a name="see-also"></a>関連項目

* [Windows Mixed Reality を使用した SteamVR のトラブルシューティング](steamvr-questions.md)
* [Windows Mixed Reality でのゲームとアプリの使用](using-games-and-apps-in-windows-mixed-reality.md)
* [Unity での HP コントローラーの使用](https://docs.microsoft.com/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers)
* [Unreal での HP Controller の使用](https://docs.microsoft.com/windows/mixed-reality/develop/unreal/unreal-reverb-g2-controllers)
* [バグとフィードバックを提出する](filing-feedback.md)
