---
title: Windows Mixed Reality 用に SteamVR アプリを更新する
description: Windows Mixed Reality ヘッドセットとの互換性を最大化するために SteamVR アプリケーションを更新するためのベストプラクティス。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR、互換性、移植、HoloLens ファースト世代、mixed reality ヘッドセット、windows mixed reality ヘッドセット、移行、Windows 10、蒸気、motion controller、haptics
ms.openlocfilehash: 94b6aad63156d752858c6566174ff01e6127d75d
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2020
ms.locfileid: "97612906"
---
# <a name="updating-steamvr-apps-for-windows-mixed-reality"></a>Windows Mixed Reality 用に SteamVR アプリを更新する

Windows Mixed Reality ヘッドセットで実行するために、開発者は SteamVR エクスペリエンスをテストして最適化することをお勧めします。 このドキュメントでは、Windows Mixed Reality でのエクスペリエンスを向上させるために実行できる一般的な機能強化について説明します。

## <a name="initial-setup-instructions"></a>初期セットアップの手順

Windows Mixed Reality でゲームやアプリのテストを開始するには、まず、[ファーストステップガイド](https://aka.ms/WindowsMixedRealitySteamVR)に従ってください。

## <a name="controller-models"></a>コントローラーモデル

1. アプリがコントローラーモデルをレンダリングする場合:
    * [Windows Mixed Reality モーションコントローラーモデル](../../design/motion-controllers.md#rendering-the-motion-controller-model)を使用する
    * IVRRenderModel:: GetComponentState を使用して、コンポーネントパーツへのローカル変換を取得します (ポインターの例など)。
2. ききの概念を持つエクスペリエンスでは、コントローラーを区別するために入力 Api からヒントを取得する必要があります [(Unity の例)。](../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)

## <a name="controls"></a>コントロール

コントロールのレイアウトをデザインまたは調整する場合は、次の予約済みコマンドのセットに注意してください。
1. **左と右のアナログサムスティック** をクリックすると、**蒸気ダッシュボード** 用に予約されます。

> [!NOTE]
> HP リバーブ G2 コントローラーを使用している場合は、右のメニューボタンをクリックすると、 **蒸気ダッシュボード** 用に予約されています。

2. **Windows のボタンをクリック** すると、常にユーザーが Windows Mixed Reality ホームに戻ります。

可能であれば、既定ではサムスティックベースの [電話](../../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) を使用します。

## <a name="tooltips-and-ui"></a>ツールヒントと UI

多くの VR ゲームでは、モーションコントローラーのツールヒントとオーバーレイを利用して、ユーザーにアプリまたはゲームの最も重要なコマンドを学習させることができます。 Windows Mixed reality 用にアプリケーションをチューニングする場合、ツールヒントが Windows コントローラーモデルにマップされるように、エクスペリエンスのこの部分を確認することをお勧めします。

また、コントローラーのイメージを表示するポイントがある場合は、Windows Mixed Reality モーションコントローラーを使用して、更新されたイメージを提供するようにしてください。

## <a name="haptics"></a>Haptics

[Windows 10 April 2018 Update](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)以降では、Haptics が Windows Mixed Reality での SteamVR エクスペリエンスでサポートされるようになりました。 SteamVR アプリまたはゲームに既に haptics のサポートが含まれている場合は、 [Windows Mixed Reality モーションコントローラー](../../design/motion-controllers.md)を使用して (追加の作業を行わずに) 動作するようになります。

Windows Mixed Reality モーションコントローラーでは、他の SteamVR モーションコントローラーの線形アクチュエータではなく、標準の haptics モータが使用されます。 これにより、想定外のユーザーエクスペリエンスが多少異なります。 そのため、Windows Mixed Reality motion controller を使用して haptics の設計をテストおよびチューニングすることをお勧めします。 たとえば、Windows Mixed Reality モーションコントローラーでは、短い haptic パルス (5-10 ミリ秒) があまり目立たない場合があります。 より顕著なパルスを生成するには、もう一度電源をオフにするように指示する前に、より長い "クリック" (40-70 ミリ秒) を送信してみてください。

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>Windows Mixed Reality の [スタート] メニューから SteamVR アプリを起動する

ストリームによって配布される VR エクスペリエンスについては、最新の[windows リリース](https://insider.windows.com)と共に[steamvr の windows Mixed Reality を更新](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800)しました。 SteamVR のタイトルが、[すべてのアプリ] の一覧の Windows Mixed Reality の [スタート] メニューに自動的に表示されるようになりました。

## <a name="windows-mixed-reality-logo"></a>Windows Mixed Reality ロゴ

タイトルの Windows Mixed Reality サポートを表示するには、アプリのランディングページの [ストアの編集] ページに移動し、[基本情報] タブを選択して、[仮想現実] を下にスクロールします。 [Windows Mixed Reality を非表示にする] をオフにして、ストアに発行します。

## <a name="bugs-and-feedback"></a>バグとフィードバック

Windows Mixed Reality SteamVR エクスペリエンスを向上させるために、お客様のフィードバックは非常に重要です。 [Windows フィードバックハブ](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback)を通じてすべてのフィードバックとバグを送信します。 ここでは [、SteamVR フィードバックを可能な限り活用するためのヒント](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)を紹介します。

共有する質問やコメントがある場合は、 [ストリームフォーラム](https://steamcommunity.com/app/719950/discussions/)からもご連絡いただけます。

## <a name="faqs-and-troubleshooting"></a>FAQ とトラブルシューティング

一般的な問題が発生したときに、エクスペリエンスをセットアップまたは再生するには、 [最新のトラブルシューティング手順を確認](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)してください。

## <a name="see-also"></a>関連項目

* [ツールのインストール](../install-the-tools.md)
* [ヘッドセットとモーションコントローラーのドライバー履歴](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Windows Mixed Reality の PC ハードウェアの最小互換性ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
