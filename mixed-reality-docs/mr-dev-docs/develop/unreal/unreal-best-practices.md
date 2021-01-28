---
title: 全般的なベスト プラクティス
description: Unreal Engine で Mixed Reality アプリケーションを開発するための推奨されるすべてのベスト プラクティスの最新情報を提供します。
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, エディター拡張機能, Unreal エディター, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, ドキュメント, ガイド, 機能, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, 移植, アップグレード
ms.openlocfilehash: 478ae3137fc73d1ef516087618ab0247f2164c02
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584904"
---
# <a name="general-best-practices"></a>全般的なベスト プラクティス

Mixed Reality 用の Unreal Engine プロジェクトを作成するときに、すべての開発者に従うことをお勧めする一般的なベスト プラクティスを示します。

## <a name="constructors"></a>コンストラクター

ブループリントで "コンストラクター" に相当するものが必要な場合は、Unreals の[コンストラクション スクリプト](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)を使用します。 "BeginPlay" イベントを使用する場合と比較したときの最大の利点は、コンストラクター スクリプトは "エディター" でも実行されることです。 ほとんどの場合、起動時に、またはコンパイル時でさえ、値をキャッシュできます。

> [!NOTE]
> コンストラクション スクリプトのサポート情報の詳細については、[エディター拡張機能の概要](unreal-editor-extensions.md#construction-scripts)に関するページを参照してください。

## <a name="3d-buttons-and-textures"></a>3D ボタンとテクスチャ

Mixed Reality アプリケーションで 3D ボタを作成したり、その使用を計画したりするときは、パフォーマンスについて考えるのが自然です。 ただし、すべてのものをメッシュから 3D として認識されるようにする必要はありません。 テクスチャが慎重に作成されている Paper2D を使用して 3D の外観を取得するためのオプションがあります。 これは 3D "のように見える" ボタンの場合は非常にうまく機能しますが、クワッド上の加工された画像に過ぎません。 これらの装飾的なバージョンは、[スプライト](https://docs.unrealengine.com/AnimatingObjects/Paper2D/Sprites/index.html)と呼ばれます。

## <a name="variants"></a>バリアント

実行時に複数のオブジェクト構成を使用してシーンを作成するシナリオでは、[Unreal バリアント](https://docs.unrealengine.com/Basics/Levels/Variants/index.html)を使用します。 バリエーションには、変化する素材やメッシュを含めることができます。 

## <a name="animation"></a>アニメーション

多数の "対話型アニメーション" を作成する場合は、[Spline コンポーネント](https://docs.unrealengine.com/API/Runtime/Engine/Components/USplineComponent/index.html) (Spline "Mesh" コンポーネントではなく) と [Timeline ノード](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Timelines/index.html)を利用します。 

<!-- You can find a comprehensive [video tutorial here](https://www.youtube.com/watch?v=bWXI91FdMtk&ab_channel=DoubleCrossGames). -->

## <a name="communications"></a>通信

オブジェクトを動的に見つけることが困難な場合や、複数のアクターとブループリントの間の通信に使用される帯域幅が多すぎる場合は、[Level ブループリント](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Types/LevelBlueprint/index.html)を使用します。 Unreal Engine 4 は Unity とは異なり、すべてのものをコンポーネント内に置く必要がないことを思い出してください。 Level ブループリントは、複数のアクター間の通信を単純化するための、完全に有効で推奨される方法です。 オブジェクト参照さえ、Level ブループリントの OnBeginPlay で起動時に "キャッシュ" することができます。

## <a name="global-state"></a>グローバル状態

多くの場合、スコア、レベル データ、プレーヤー固有の情報、または特定のオブジェクトにまったく属していない他のものなど、レベル固有の状態を格納する必要があります。 [GameMode](https://docs.unrealengine.com/en-US/InteractiveExperiences/Framework/GameMode/index.html) を見落とさないようにしてください。 ほとんどの人はその存在を忘れていますが、GameMode はレベルごとに作成でき、各レベルに固有のデータが含まれています。

## <a name="optimizing-blueprints"></a>ブループリントの最適化

ブループリントの検索に時間がかかりすぎる場合は、C++ のコードを書き直す前に、Unreal でブループリントを "ネイティブ化" します。 独自のカスタム ソリューションを作成する前に、自動的な[ネイティブ化](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/TechnicalGuide/NativizingBlueprints/index.html)を使用してみてください。

![包含のブループリント ネイティブ化方法が強調表示されているブループリントの設定](images/unreal-general-practices-img-01.jpg)
