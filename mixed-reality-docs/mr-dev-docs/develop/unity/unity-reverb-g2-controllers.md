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
# <a name="hp-reverb-g2-controllers-in-unity"></a><span data-ttu-id="a981e-104">Unity の HP リバーブ G2 コントローラー</span><span class="sxs-lookup"><span data-stu-id="a981e-104">HP Reverb G2 Controllers in Unity</span></span>

## <a name="getting-started"></a><span data-ttu-id="a981e-105">作業の開始</span><span class="sxs-lookup"><span data-stu-id="a981e-105">Getting started</span></span>

<span data-ttu-id="a981e-106">SteamVR 用に開発している場合、または Windows Mixed Reality 入力 API (XR を使用している場合は、HP リバーブ G2 コントローラーを使用するために追加のセットアップは必要ありません。付い.入力)。</span><span class="sxs-lookup"><span data-stu-id="a981e-106">There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input).</span></span> <span data-ttu-id="a981e-107">ただし、SteamVR を使用している場合を除き、[A]、[B]、[X]、[Y]、[Y]、および [つかみ] トリガーには、現在、入力マネージャーからアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="a981e-107">However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR.</span></span> <span data-ttu-id="a981e-108">追加のリバーブ G2 入力のサポートは近日中に利用できるようになる予定なので、ぜひご確認ください。</span><span class="sxs-lookup"><span data-stu-id="a981e-108">Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!</span></span>

## <a name="porting-existing-applications"></a><span data-ttu-id="a981e-109">既存のアプリケーションの移植</span><span class="sxs-lookup"><span data-stu-id="a981e-109">Porting existing applications</span></span>

<span data-ttu-id="a981e-110">Windows Mixed Reality のイマーシブヘッドセット用に開発している既存のアプリが既にある場合は、「 [移植ガイド」](../porting-apps/porting-guides.md) と「 [プロジェクトの設定](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) 」のセクションを参照して、一般的な提案を確認してください。</span><span class="sxs-lookup"><span data-stu-id="a981e-110">If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) sections for general suggestions.</span></span>

## <a name="mapping-input"></a><span data-ttu-id="a981e-111">マッピング (入力を)</span><span class="sxs-lookup"><span data-stu-id="a981e-111">Mapping input</span></span>

<span data-ttu-id="a981e-112">新しいコントローラーの入力マッピングを準備して実行する準備ができたら、「イマーシブ移植」ガイドの「 [入力マッピング](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) 」セクションから開始します。</span><span class="sxs-lookup"><span data-stu-id="a981e-112">When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) section of the immersive porting guide.</span></span> <span data-ttu-id="a981e-113">Unity で入力を構成する方法の詳細については、「 [ジェスチャとモーションコントローラー](gestures-and-motion-controllers-in-unity.md)」と「参照用の完全な [ボタンと軸のマッピングテーブル](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a981e-113">Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.</span></span>

## <a name="see-also"></a><span data-ttu-id="a981e-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="a981e-114">See also</span></span>
* [<span data-ttu-id="a981e-115">SteamVR の更新</span><span class="sxs-lookup"><span data-stu-id="a981e-115">Updating for SteamVR</span></span>](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)