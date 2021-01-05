---
title: SteamVR に関する Faq
description: SteamVR Windows Mixed Reality のトラブルシューティングは、標準のコンシューマーサポートドキュメントを超えています。
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、トラブルシューティング、エラー、ヘルプ、サポート、SteamVR
ms.openlocfilehash: 275a334b2cbf402ea576948c4622f2098d8f3ec0
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725883"
---
# <a name="steamvr-faqs"></a>SteamVR に関する Faq

## <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-headset"></a>Windows Mixed Reality ヘッドセットで SteamVR ゲームを再生する方法

1. [SteamVR をダウンロードしてインストール](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe)します。 Steamvr チュートリアルは、SteamVR を開始すると自動的に開始されます。
2. ヘッドセットを PC に接続し、モーションコントローラーをオンにします。
3. Windows Mixed Reality ホームが読み込まれ、コントローラーが表示されたら、デスクトップでストリームアプリを開きます。
4. 蒸気 app を使用して、ストリームライブラリから SteamVR ゲームを起動します。 ヘッドセットをオフにせずに SteamVR ゲームを起動するには、Windows Mixed Reality の [ **スタート > すべてのアプリ**] でそれらを見つけて起動します。

## <a name="a-message-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>"Windows Mixed Reality で SteamVR を使用するには、最新の Windows Update をインストールする必要があります" または "Windows 開発者モードが必要" というメッセージが表示されます。

1. PC で最新バージョンの Windows 10 が実行されていることを確認します。 [ **設定 > システム >** にアクセスし、[Windows の仕様] の下にある [OS ビルド] が16299.64 以上であることを確認します。
2. ダウンロードまたはインストールを待機している更新プログラムがないことを確認します。 [設定] にアクセスして **& セキュリティ > を更新 > Windows Update** 、[更新プログラムの確認] を選択します。 他の更新プログラムが利用できなくなるまで複数回チェックし、PC を再起動することが必要になる場合があります。

## <a name="steamvr-is-crashing-after-updating-windows"></a>Windows の更新後に SteamVR がクラッシュする

SteamVR 用の Windows Mixed Reality の古いバージョンには、Windows との互換性がありません。 SteamVR の Windows Mixed Reality のバージョンが最新であることを確認するには、次のようにします。

1. 蒸気図書館で、「 **ソフトウェア > Windows Mixed Reality For SteamVR**」にアクセスします。
2. それを右クリックし、[プロパティ] にアクセスします。
3. [更新] タブを選択し、[このアプリケーションを常に最新の状態に保つ] を選択します。
4. [ローカルファイル] タブに移動し、[アプリケーションファイルの整合性を確認する] を選択して、更新を強制します。
5. ストリームと SteamVR を再起動します。

更新後に SteamVR がまだクラッシュしている場合は、コンピューター上に SteamVR 用の Windows Mixed Reality を2つインストールすることができます。 確認するには:

1. ```%localappdata%\openvr\openvrpaths.vrpath```それを探してメモ帳で開きます。
2. "外部ドライバー" セクションで、"MixedRealityVRDriver" に複数のエントリがあるかどうかを確認します。
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver",
      "E:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
3. 複数のエントリが表示されている場合は、2つのエントリのうち古い方を削除します。 エントリが1つしかない場合は、行の末尾にコンマが含まれなくなります。 例:
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
4. ファイルを保存して閉じます。
5. ストリームと SteamVR を再起動します。

## <a name="my-controllers-arent-working-as-expected-in-steamvr"></a>SteamVR でコントローラーが想定どおりに動作していない

1. SteamVR を閉じます。
2. Windows Mixed Reality ホームに戻り、コントローラーが動作していることを確認します。
3. もう一度 SteamVR エクスペリエンスを起動し、コントローラーを通常のモードに戻します。
4. 問題が解決しない場合は、[Mixed Reality] カテゴリの下にある [Windows フィードバックハブ](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) を使用してフィードバックファイルを、概要に SteamVR を含めます。

さまざまなゲームで、モーションコントローラーを別々に使用します。 使用を開始する際に役立つ基本事項をいくつか次に示します。
* 蒸気 dashboard を開くには、左のサムスティックを右上に押します。
* SteamVR ゲームを終了し、Windows Mixed Reality ホームに戻るには、[Windows] ボタンを押します。 次に、画面に表示される Mixed Reality ホームボタンを選択します。

## <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>私の左側と右側のコントローラーが SteamVR で元に戻される

コントローラーをオフにしてゲームを起動し、左側のコントローラーの電源を入れます。

## <a name="my-games-are-running-slowly"></a>ゲームの実行速度が低下しています

1. PC が Windows Mixed Reality とプレイ中のゲームで SteamVR の仕様を満たしていることを確認します。
2. デスクトップの Mixed Reality ポータルで、[一時停止] を選択してデスクトップのプレビューを停止します。
3. [ **設定 > システム >** にアクセスし、[Windows の仕様] の下にある [OS ビルド] が16299.64 以降であることを確認します。
4. お使いの PC に最新のグラフィックスドライバーがあることを確認してください (「Windows Update)」をご覧ください。
5. [タスクマネージャー] をオンにして、PC 上でリソースを消費している可能性がある他のプロセスを確認します。
6. ストリームがバックグラウンドでゲームをダウンロードしているかどうかを確認します。これにより、リソースが消費され、ゲームのパフォーマンスが低下します。
7. ウィンドウが表示されていない小さなクラスのアプリ (SteamVR ホームなど) には、既知のパフォーマンスの問題があります。 ほとんどのアプリはこのカテゴリに分類されず、今後の更新プログラムで修正プログラムを利用できるようになります。

予期しないパフォーマンスの問題が解決しない場合は、 [Windows フィードバックハブ](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)を使用してフィードバックをお送りください。 手順に従って、 [SteamVR パフォーマンストレースを含める](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr)ようにしてください。

## <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>SteamVR で、コンポジターエラーが表示されています ("共有 IPC コンポジター接続に失敗しました (400)" など)。

これは、ヘッドセットとプライマリモニターが2つの異なるビデオアダプターにある場合に発生する可能性があります。 ヘッドセットと同じアダプターにモニターを接続し、[設定] [ **アプリ > システム > 表示**] でプライマリモニターとして構成します。

## <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>SteamVR コンテンツは、床の上または上部にあるように間違った場所に表示される

位置をリセットします。

1. 左コントローラーのサムスティックを選択して、"SteamVR ダッシュボード" を表示します。
2. [設定] ボタンを選択します。
3. [固定位置のリセット] を選択します。

## <a name="my-steam-app-closed-unexpectedly"></a>ストリームアプリが予期せず終了しました

次の場合、蒸気 app は終了します。

* PC 画面をロックする
* ヘッドセットを削除する
* ユーザーの切り替え
* PC がスリープ状態になります。
