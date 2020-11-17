---
title: Unreal の入力を見つめます
description: HoloLens および Unreal Engine 用の宝石入力の設定に関するチュートリアル
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality、ホログラム、HoloLens 2、視線追跡、宝石入力、ヘッドマウントディスプレイ、Unreal engine、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual Reality ヘッドセット
ms.openlocfilehash: 2ea55e3c53275f6150ca7f2def10d71634119e2e
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679051"
---
# <a name="gaze-input"></a>見つめ入力

## <a name="overview"></a>概要

[Windows Mixed Reality プラグイン](https://docs.unrealengine.com/Platforms/VR/WMR/index.html)には、入力を見つめするための組み込み関数が用意されていませんが、HoloLens 2 では視線追跡がサポートされています。 実際の追跡機能は、Unreal のマウントされた **ディスプレイ** と **視点の追跡** api によって提供され、次のものが含まれます。

- デバイス情報
- センサーの追跡
- 向きと位置
- クリップペイン
- データと追跡情報を見つめます

機能の完全な一覧については、Unreal の「マウントされた [ディスプレイ](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) と [視点の追跡](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) 」ドキュメントを参照してください。

Unreal Api に加えて、HoloLens 2 の [視線に基づく相互作用](../../design/eye-gaze-interaction.md) に関するドキュメントを参照し、 [hololens 2 の視線追跡](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) がどのように動作するかを確認してください。

> [!IMPORTANT]
> 視線追跡は、HoloLens 2 でのみサポートされています。

## <a name="enabling-eye-tracking"></a>目の追跡を有効にする
Unreal の Api を使用するには、HoloLens の入力を HoloLens プロジェクト設定で有効にする必要があります。 アプリケーションが起動すると、次のスクリーンショットに同意プロンプトが表示されます。

- [ **はい** ] を選択してアクセス許可を設定し、宝石入力のアクセス権を取得します。 この設定をいつでも変更する必要がある場合は、 **設定** アプリで見つけることができます。

![アイ入力のアクセス許可](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> ステレオスコピックの追跡に必要な2つの光線はサポートされていないため、Unreal の HoloLens の追跡では、両方の目に1つの宝石があります。

これで、HoloLens の入力を HoloLens 2 のアプリに Unreal に追加する必要があります。 より簡単な入力と、それが混合現実のユーザーに与える影響の詳細については、以下のリンクを参照してください。 対話型エクスペリエンスを構築するときは、これらのことを考慮してください。

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

私たちが用意した Unreal 開発チェックポイント体験に従っている場合、読者は MRTK コア構成要素を探索している段階にいます。 ここから、次の構成要素に進むことができます。 

> [!div class="nextstepaction"]
> [ハンド トラッキング](unreal-hand-tracking.md)

または、Mixed Reality プラットフォームの機能と API に移動します。

> [!div class="nextstepaction"]
> [HoloLens カメラ](unreal-hololens-camera.md)

いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#2-core-building-blocks)に戻ることができます。

## <a name="see-also"></a>関連項目
* [調整](../../calibration.md)
* [快適性](../../design/comfort.md)
* [視線入力とコミット](../../design/gaze-and-commit.md)
* [音声入力](../../out-of-scope/voice-design.md)
