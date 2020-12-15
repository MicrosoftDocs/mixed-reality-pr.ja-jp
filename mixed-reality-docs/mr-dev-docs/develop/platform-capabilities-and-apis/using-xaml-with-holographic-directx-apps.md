---
title: XAML とホログラフィック DirectX アプリの使用
description: DirectX アプリでの 2D XAML ビューとイマーシブビューの切り替えの影響と、XAML ビューとイマーシブビューの両方を効率的に使用する方法について説明します。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: windows mixed reality, UWP, アプリビュー管理, xaml, キーボード, チュートリアル, DirectX
ms.openlocfilehash: b062efadca9ccfe2e2caeb054f662becc0807b50
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530275"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>XAML とホログラフィック DirectX アプリの使用

> [!NOTE]
> この記事は、従来の WinRT ネイティブ Api に関連しています。  新しいネイティブアプリプロジェクトの場合は、 **[OPENXR API](../native/openxr-getting-started.md)** を使用することをお勧めします。

このトピックでは、DirectX アプリでの [2D XAML ビューとイマーシブビュー](../../design/app-views.md) の切り替えの影響と、xaml ビューとイマーシブビューの両方を効率的に使用する方法について説明します。

## <a name="xaml-view-switching-overview"></a>XAML ビューの切り替えの概要

HoloLens では、後から 2D XAML ビューを表示できるイマーシブアプリでは、最初に XAML ビューを初期化し、そこからすぐにイマーシブビューに切り替える必要があります。 アプリが何かを実行する前に XAML が読み込まれるため、起動時間がわずかに増加します。 XAML は、バックグラウンドのままで、アプリのプロセスのメモリ領域を占有し続けます。 起動時の遅延とメモリの使用量は、ネイティブビューに切り替える前に、アプリが XAML で何を実行しているかによって異なります。 最初に XAML スタートアップコードで何もしない場合は、イマーシブビューを開始する以外に、影響は軽微である必要があります。 また、holographic レンダリングはイマーシブビューに直接行われるため、そのレンダリングには XAML 関連の制限はありません。

CPU と GPU の両方のメモリ使用量がカウントされます。 Direct3D 11 では仮想グラフィックスメモリを交換できますが、一部またはすべての XAML GPU リソースをスワップすることはできず、パフォーマンスが著しく低下する可能性があります。 どちらの方法でも、不要な XAML 機能を読み込まないと、アプリのためのスペースが増え、エクスペリエンスが向上します。

## <a name="xaml-view-switching-workflow"></a>XAML ビューの切り替えワークフロー

XAML からイマーシブモードに直接移動するアプリのワークフローは、次のようになります。
* アプリが 2D XAML ビューで開始されます。
* アプリの XAML スタートアップシーケンスは、現在のシステムが holographic のレンダリングをサポートしているかどうかを検出します。
* その場合は、アプリによってイマーシブビューが作成され、すぐに前面に移動します。 Xaml の読み込みは、XAML ビューでのレンダリングクラスや資産の読み込みなど、Windows Mixed Reality デバイスでは不要なものに対してスキップされます。 アプリでキーボード入力に XAML が使用されている場合でも、その入力ページは作成されます。
* それ以外の場合、XAML ビューは通常どおりビジネスで続行できます。

## <a name="tip-for-rendering-graphics-across-both-views"></a>両方のビューでグラフィックスをレンダリングするためのヒント

Windows Mixed Reality の XAML ビューに対して、DirectX で一定量のレンダリングを実装する必要がある場合、最良の方法は、両方のビューを使用できるレンダラーを1つ作成することです。 レンダラーは、両方のビューからアクセスできる1つのインスタンスである必要があり、2D と holographic のレンダリングを切り替える必要があります。 これにより、GPU 資産は1回だけ読み込みます。これにより、読み込み時間、メモリの影響、およびビューの切り替え時にスワップされたリソースの量が減少します。
