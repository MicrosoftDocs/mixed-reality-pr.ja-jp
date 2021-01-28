---
title: Unreal 用の MRTK の概要
description: Unreal 用の Mixed Reality Toolkit で新しい Mixed Reality 開発者に提供されるすべてのものの概要を説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, テスト, Mixed Reality Toolkit, MRTK バージョン 2, MRTK, ツール, SDK, HoloLens, HoloLens 2, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, クロスプラットフォーム
ms.openlocfilehash: 4aa21cbee75c4c362abfd609add922ad9c922682
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584831"
---
# <a name="introducing-mrtk-for-unreal"></a>Unreal 用の MRTK の概要

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Mixed Reality Toolkit (MRTK) とは

MRTK は、HoloLens が初めてリリースされてからずっとある、すばらしいオープンソースのツールキットです。 そのツールキットが今のような立ち位置にあるのは、勤勉な開発者コミュニティの貢献のおかげです。 

Unreal 用 Mixed Reality Toolkit (MRTK-Unreal) は、Unreal Engine を使用した Mixed Reality アプリケーションの開発に役立つように設計されたプラグイン、サンプル、ドキュメントの形式で構成される一連のコンポーネントです。 現在、ツールキットは次のもので構成されています。
* [Unreal 用 UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal)。Hololens 2 アプリケーション用の UX 機能を実装するためのコード、ブループリント、例が提供されます。
* [Unreal 用 Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal)。パフォーマンス バジェットに収めながら、Mixed Reality アプリケーションの視覚的な忠実性を向上させることができます。

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

[GitHub にある MRTK のドキュメント](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)を参照し、[UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) または [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) のインストール ガイドに従って作業を開始してください。

### <a name="modular"></a>モジュール式

MRTK Unreal はモジュール方式で構築されているため、ツールキットのすべての機能をプロジェクトに組み込む必要はありません。 必要なプラグインを見つけて選択し、必要に応じて追加または削除することができます。 この方法により、プロジェクトを小規模に保ち、管理を容易にすることができます。  

### <a name="performant"></a>高いパフォーマンス

モバイル プラットフォームで動作するので、MRTK Unreal はパフォーマンスを考慮して構築されています。 このことは非常に重要であり、Microsoft ではツールがお客様の妨げにならないことを保証したいと考えました。

## <a name="see-also"></a>関連項目

* [ツールのインストール](../install-the-tools.md)
* [Unreal 用 MRTK を使用した開発](unreal-development-overview.md)
* [UX Tools - インストール ガイド (GitHub)](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html)
* [UX Tools - ドキュメント ホーム (GitHub)](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)
* [Graphics Tools - インストール ガイド (GitHub)](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md)
* [Graphics Tools - ドキュメント ホーム (GitHub)](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/)