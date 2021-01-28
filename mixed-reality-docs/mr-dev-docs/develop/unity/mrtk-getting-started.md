---
title: Unity 用の MRTK の概要
description: クロスプラットフォームの Mixed Reality Toolkit で新しい Mixed Reality 開発者に提供されるすべてのものの概要を説明します。
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, テスト, Mixed Reality Toolkit, MRTK バージョン 2, MRTK, ツール, SDK, HoloLens, HoloLens 2, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, クロスプラットフォーム
ms.openlocfilehash: 4c013f1fa50518404f899b4181e7c07b9e4e0e56
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581705"
---
# <a name="introducing-mrtk-for-unity"></a>Unity 用の MRTK の概要

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Mixed Reality Toolkit (MRTK) とは

MRTK は、HoloLens が初めてリリースされてからずっとある、すばらしいオープンソースのツールキットです。 そのツールキットが今のような立ち位置にあるのは、勤勉な開発者コミュニティの貢献のおかげです。 過去 3 年間で、Microsoft では開発者コミュニティのフィードバックを受け、最も重要な懸念事項に対応するために MRTK v2 を構築しました。  

Unity 用の MRTK は、Mixed Reality アプリケーション向けのオープンソースのクロスプラットフォーム開発キットです。 そのツールキットには、空間でのインタラクションのための、クロスプラットフォームの入力システム、基本コンポーネント、共通の構成要素が備わっています。 MRTK バージョン 2 は、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォーム向けのアプリケーションの開発を高速化することを目的としています。 このプロジェクトは、参入障壁を減らすこと、Mixed Reality アプリケーションを作成すること、全体の成長に応じてコミュニティに貢献することを目的としています。

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

[GitHub の MRTK に関するドキュメント](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)を参照し、[インストール ガイド](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)の手順を開始してください。

## <a name="new-with-mrtk-v2"></a>MRTK v2 の新機能

これらのプラットフォーム ツールに込めた Microsoft の成果に注目して欲しいと考えています。  事実、Microsoft では MRTK バージョン 2 を使用して、アウトオブボックス設定エクスペリエンス (OOBE) などのすぐに使えるエクスペリエンスや Mixed Reality Tips アプリケーションを開発しました。 また、新しい HoloLens 2 機能は、まずは MRTK 経由で公開されることを期待していただいてかまいません。Microsoft では、お客様が当社のプラットフォーム上で開発を行ううえで、それが最適な方法であると確信しているからです。 

### <a name="modular"></a>モジュール式

モジュール式の手法でビルドされているため、ツールキットのすべての機能をプロジェクトに組み込む必要はありません。  実際に、これにはいくつかの利点があります。  プロジェクトを小規模に保ち、管理を容易にすることができます。  さらに、スクリプト作成が可能なオブジェクトによってビルドされており、インターフェイス駆動型であるため、組み込みのコンポーネントをお客様独自のものに置き換えて、他のサービス、システム、およびプラットフォームをサポートすることも可能です。

### <a name="cross-platform"></a>クロスプラットフォーム

他のプラットフォームに関しては、クロスプラットフォームのサポートを備えています。  また、このことによって、すべての単一プラットフォームがサポートされるわけではありませんが、ビルド ターゲットを他のプラットフォームに切り替えたときに、どのツールキットのコードも中断されないことを保証しています。  モジュール式の設計による堅牢性と拡張性により、ARCore、ARKit、および OpenVR などの複数のプラットフォームをサポートするようにアプリが設定されます。

### <a name="performant"></a>高いパフォーマンス

モバイル プラットフォームに対応し、パフォーマンスを考慮して構築されています。  このことは非常に重要であり、Microsoft ではツールがお客様の妨げにならないことを保証したいと考えました。

## <a name="see-also"></a>関連項目

* [ツールのインストール](../install-the-tools.md)
* [Unity 用 MRTK を使用した開発](unity-development-overview.md)
* [MRTK - インストール ガイド (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [MRTK - ドキュメント ホーム (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [HoloToolkit/MRTK から MRTK バージョン 2 への移植 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
