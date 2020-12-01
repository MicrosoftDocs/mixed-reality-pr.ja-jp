---
ms.openlocfilehash: c9ce068adc3b4b550ecaf1b1c106d9b12f363ac0
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443507"
---
# <a name="hololens"></a>[HoloLens](#tab/hololens)

HoloLens アプリケーションがある場合は、次の表から優先 [配布オプション](../distribute-overview.md#distribution-options) を選択してください。 Microsoft Store に発行する場合は、 [アプリ内購入](../in-app-purchases.md) を追加してコンテンツを収益化することができます。

# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

Windows Mixed Reality ヘッドセットを対象とするイマーシブアプリケーションを使用している場合は、3D アプリランチャーを作成し、次の表から優先 [配布オプション](../distribute-overview.md#distribution-options) を選択します。 Microsoft Store に発行する場合は、 [アプリ内購入](../in-app-purchases.md) を追加してコンテンツを収益化することができます。

### <a name="designing-3d-app-launchers-for-vr"></a>VR 用の3D アプリランチャーの設計 

3D アプリランチャーは、ユーザーがイマーシブヘッドセットに配置するたびに表示される Windows Mixed Reality ホーム環境にオブジェクトとして表示されます。 これらのオブジェクトは自由に作成およびカスタマイズできますが、 [設計ガイダンス](../3d-app-launcher-design-guidance.md) の記事から始めることをお勧めします。これには、スケーリング、種類、色の選択、テクスチャ、その他すべてを仮想環境で使用できるようにするための優れた設計方法があります。

### <a name="modeling-and-exporting-3d-app-launchers"></a>3D アプリランチャーのモデリングとエクスポート

3D アプリランチャーのアイデアを設定したら、資産ファイルの形式、三角形の数、テクスチャのサイズ、アニメーションの長さ、資産の最適化など、Microsoft Store の要件を満たしていることを確認する必要があります。 このプロセスは技術的には非常に優れているため、 [3d モデルの作成](../creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) に関する記事を使用してすべてのチェックボックスをオンにすることをお勧めします。 このオーサリング仕様を満たしていない資産は、Windows Mixed Reality ホームにはレンダリングされません。

### <a name="adding-3d-app-launchers-in-your-apps"></a>アプリに3D アプリランチャーを追加する

3D アプリランチャーが Windows Mixed Reality の作成ガイドラインを満たしていることを確認した後は、Windows Mixed Reality ホーム環境でアプリケーションの既定の2D ランチャーを上書きするために使用できます。 3D アプリランチャーをアプリケーションに統合するプロセスは、開発しているアプリケーションの種類によって異なります。

* [UWP アプリ](../implementing-3d-app-launchers.md)
* [Win32 アプリ](../implementing-3d-app-launchers-win32.md)

### <a name="optional-placing-3d-models-in-the-windows-mixed-reality-home"></a>OptionalWindows Mixed Reality ホームへの3D モデルの配置

おまけとして、一部の2D アプリケーションでは、3D モデルを装飾として Windows Mixed Reality ホームに直接配置したり、フル3D でさらに検査したりすることができます。 [モデルの追加] プロトコルを使用すると、3d モデルを web サイトまたはアプリケーションから Windows Mixed Reality ホームに送信できます。このホームは、3D アプリランチャー、2D アプリ、ホログラムと同様に保持されます。 [Windows Mixed Reality ホームに3d モデルを配置する方法](../enable-placement-of-3d-models-in-the-home.md)については、「」を参照してください。また、独自のアプリを装飾する方法の詳細と手順を確認できます。