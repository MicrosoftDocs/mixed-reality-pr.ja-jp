---
title: MRTK バージョン 2 の概要
description: MRTK の活用に関心がある開発初心者向け
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, テスト, Mixed Reality Toolkit, MRTK バージョン2, MRTK, ツール, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: 4513185573003510e5a7cae97ecce4cb5d2552e0
ms.sourcegitcommit: 83c9373fe5b2e07cdab921b6cab3fdd418307003
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2020
ms.locfileid: "94386208"
---
# <a name="getting-started-with-mrtk-for-unity"></a>Unity 用の MRTK の概要
![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Mixed Reality Toolkit (MRTK) とは
MRTK は、HoloLens が最初にリリースされて以来培われてきたすばらしいオープン ソースのツールキットであり、貢献してくれた開発者コミュニティの努力によって、現在の姿があります。 過去 3 年間で、Microsoft では開発者コミュニティのフィードバックを受け、最も重要な懸念事項に対応するために MRTK v2 を構築しました。  

Unity 用の MRTK は、Mixed Reality アプリケーション向けのオープンソースのクロスプラットフォーム開発キットです。 MRTK には、空間でのインタラクションのための、クロスプラットフォームの入力システム、基本コンポーネント、共通の構成要素が備わっています。 MRTK バージョン 2 は、Microsoft HoloLens、Windows Mixed Reality イマーシブ (VR) ヘッドセット、OpenVR プラットフォームをターゲットとしたアプリケーションの開発を加速させることを目的としています。 このプロジェクトは、参入障壁を減らすこと、Mixed Reality アプリケーションを作成すること、全体の成長に応じてコミュニティに貢献することを目的としています。

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Setting-up-your-HoloLens-2-development-environment/player?format=ny]

詳細については、[GitHub にある MRTK のドキュメント](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)を参照してください。 開始するには、「[インストール ガイド](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)」ページの手順に従います。


## <a name="new-with-mrtk-v2"></a>MRTK v2 の新機能
これらのプラットフォーム ツールに込めた Microsoft の成果に注目して欲しいと考えています。  事実、Microsoft では MRTK バージョン 2 を活かして、アウトオブボックス設定エクスペリエンス (OOBE) などのすぐに使えるエクスペリエンスや Mixed Reality Tips アプリケーションを開発しました。 また、新しい HoloLens 2 機能は、まずは MRTK 経由で公開されることを期待していただいてかまいません。Microsoft では、お客様が当社のプラットフォーム上で開発を行ううえで、それが最適な方法であると確信しているからです。 

### <a name="modular"></a>モジュール式
モジュール式の手法でビルドされているため、ツールキットのすべての機能をプロジェクトに組み込む必要はありません。  実際に、これにはいくつかの利点があります。  プロジェクトを小規模に保ち、管理を容易にすることができます。  さらに、スクリプト作成が可能なオブジェクトによってビルドされており、インターフェイス駆動型であるため、組み込みのコンポーネントをお客様独自のものに置き換えて、他のサービス、システム、およびプラットフォームをサポートすることも可能です。

### <a name="cross-platform"></a>クロスプラットフォーム
他のプラットフォームに関しては、クロスプラットフォームのサポートを備えています。  また、このことによって、何もしなくてもすべての単一プラットフォームがサポートされるわけではありませんが、ビルド ターゲットを他のプラットフォームに切り替えたときに、どのツールキットのコードも中断されないことを保証しています。  モジュール式の設計による堅牢性と拡張性を備えることから、適切な手法を利用して、ARCore、ARKit、および OpenVR などの複数のプラットフォームをサポートできます。

### <a name="performant"></a>高いパフォーマンス
モバイル プラットフォームに対応し、パフォーマンスを考慮して構築されています。  このことは非常に重要であり、Microsoft ではツールがお客様の妨げにならないことを保証したいと考えました。

## <a name="see-also"></a>関連項目
* [ツールのインストール](../install-the-tools.md)
* [MRTK - インストール ガイド (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [MRTK - ドキュメント ホーム (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [HoloToolkit/MRTK から MRTK バージョン 2 への移植 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
