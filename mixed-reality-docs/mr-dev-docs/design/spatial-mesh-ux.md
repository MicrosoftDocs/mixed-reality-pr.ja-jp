---
title: 空間メッシュの視覚化
description: MRTK での空間メッシュの視覚化を使用した設計ガイドラインと物理的な環境の理解について説明します。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Mixed Reality、HoloLens、UI コントロール、相互作用、UI、ux、UX デザイン、空間 UI、空間相互作用、3D UI、3D UX、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: 0f9cdc218c6fe54b8892c39a6a76f023e203d334
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009922"
---
# <a name="spatial-mesh"></a>空間メッシュ

![空間メッシュ](images/MRTK_PulseShader_SpatialMesh.gif)

ユーザーは、空間メッシュの視覚化によって、デバイスがどのように物理的な環境を認識し、理解しているかを学習します。 適切な空間メッシュの視覚化によって、空間コンテキストを提供しながら、すばらしいと魔法のエクスペリエンスを作成できます。  

## <a name="design-guideline"></a>設計ガイドライン

ユーザーがコンテンツにフォーカスを設定して操作できるようにすることが重要です。 バックグラウンドでの空間メッシュの継続的な視覚化は、邪魔になる可能性があります。 最初の起動時に1回だけ環境を表示しないようにすることをお勧めします。または、領域を対象にして環境メッシュを表示することをユーザーに明確に示すことをお勧めします。 この動作は、Mixed Reality ポータルで確認できます。
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity 用の MRTK (Mixed Reality Toolkit) での空間メッシュの視覚化

MRTK には、空間メッシュの視覚化に関するいくつかの素材が用意されています。

- **MRTK_Wireframe、MRTK_Wireframe ます**。既定の静的な空間メッシュマテリアルは、アニメーションを使用せずにメッシュの輪郭を表示します。 この資料は、空間メッシュジオメトリ全体を示すため、デバッグのために役立ちます。 ただし、運用環境では推奨されません。
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction**: この資料では、空間メッシュにアニメーション化されたパルス効果を提供します。 このマテリアルを使用して、特定の時点またはユーザーのエアタップ入力で環境を視覚化できます。 例については、「 **PulseShaderExamples** シーン」を参照してください。
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* 詳細については、「 [Mrtk-空間認識](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) 」と「 [Mrtk-Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html)」を参照してください。

<br>

---

## <a name="see-also"></a>関連項目

* [カーソル](cursors.md)
* [ハンド レイ](point-and-commit.md)
* [ボタン](button.md)
* [対話可能なオブジェクト](interactable-object.md)
* [境界ボックスとアプリ バー](app-bar-and-bounding-box.md)
* [操作](direct-manipulation.md)
* [ハンド メニュー](hand-menu.md)
* [メニューの近く](near-menu.md)
* [オブジェクト コレクション](object-collection.md)
* [音声コマンド](voice-input.md)
* [キーボード](keyboard.md)
* [ヒント](tooltip.md)
* [スレート](slate.md)
* [スライダー](slider.md)
* [シェーダー](shader.md)
* [Billboard と Tag-along](billboarding-and-tag-along.md)
* [進行状況を表示する](progress.md)
* [表面吸着](surface-magnetism.md)
