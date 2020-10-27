---
title: Unity の HP リバーブ G2 コントローラー
description: SteamVR および Windows Mixed Reality で HP リバーブ G2 コントローラーを使用する方法について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, リバーブ, リバーブ G2, HP リバーブ G2, mixed reality, 開発, モーションコントローラー, ユーザー入力, 機能, 新しいプロジェクト, エミュレーター, ドキュメント, ガイド, 機能, ホログラム, ゲーム開発
ms.openlocfilehash: 3add2ae52fbaba087da257212e1d8ddfdffe702a
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638389"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a>Unity の HP リバーブ G2 コントローラー

## <a name="getting-started"></a>作業の開始

SteamVR 用に開発している場合、または Windows Mixed Reality 入力 API (XR を使用している場合は、HP リバーブ G2 コントローラーを使用するために追加のセットアップは必要ありません。付い.入力)。 ただし、SteamVR を使用している場合を除き、[A]、[B]、[X]、[Y]、[Y]、および [つかみ] トリガーには、現在、入力マネージャーからアクセスできません。 追加のリバーブ G2 入力のサポートは近日中に利用できるようになる予定なので、ぜひご確認ください。

## <a name="porting-existing-applications"></a>既存のアプリケーションの移植

Windows Mixed Reality のイマーシブヘッドセット用に開発している既存のアプリが既にある場合は、「 [移植ガイド」](../porting-apps/porting-guides.md) と「 [プロジェクトの設定](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) 」のセクションを参照して、一般的な提案を確認してください。

## <a name="mapping-input"></a>マッピング (入力を)

新しいコントローラーの入力マッピングを準備して実行する準備ができたら、「イマーシブ移植」ガイドの「 [入力マッピング](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) 」セクションから開始します。 Unity で入力を構成する方法の詳細については、「 [ジェスチャとモーションコントローラー](gestures-and-motion-controllers-in-unity.md)」と「参照用の完全な [ボタンと軸のマッピングテーブル](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) 」を参照してください。

## <a name="see-also"></a>関連項目
* [SteamVR の更新](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)