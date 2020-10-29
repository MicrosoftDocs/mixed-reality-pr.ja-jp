---
title: 空間メッシュの視覚化
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Mixed Reality、HoloLens、UI コントロール、相互作用、ui、ux、UX デザイン、空間 UI、空間相互作用、3D UI、3D UX
ms.openlocfilehash: 2c811edc14fbcc7c917fe9fa724f1cab23179a96
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686090"
---
# <a name="spatial-mesh"></a>空間メッシュ

![空間メッシュ](images/MRTK_PulseShader_SpatialMesh.gif)

ユーザーは、空間メッシュの視覚エフェクトを使用して、デバイスがどのように物理的な環境を認識し、理解しているかを知ることができます。 空間コンテキストを提供するだけでなく、適切な空間メッシュの視覚化によって、すばらしいと魔法のエクスペリエンスを実現できます。  

## <a name="design-guideline"></a>設計ガイドライン
ユーザーがコンテンツにフォーカスを設定して操作できるようにすることが重要であるため、バックグラウンドで空間メッシュを連続して繰り返し表示することは困難になる可能性があります。 最初の起動時に1回だけ環境を表示しないようにするか、またはユーザーがスペースをターゲットにして環境メッシュを表示する明確な意図を示すことをお勧めします。 HoloLens シェルでは、この動作を確認できます。
<br>


## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity 用の MRTK (Mixed Reality Toolkit) での空間メッシュの視覚化
MRTK には、空間メッシュの視覚化に関するいくつかの素材が用意されています。

- **MRTK_Wireframe、MRTK_Wireframe ます** 。既定の静的な空間メッシュマテリアルは、アニメーションを使用せずにメッシュのアウトラインを示します。 この資料は、空間メッシュジオメトリ全体を示すため、デバッグのために役立ちます。 ただし、運用環境では推奨されません。
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction** : この資料では、空間メッシュにアニメーション化されたパルス効果を提供します。 このマテリアルを使用して、特定の時点で、またはユーザーのエアタップ入力で環境を視覚化できます。 例については、「 **PulseShaderExamples** シーン」を参照してください。
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* 詳細については、「 [Mrtk-空間認識](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) 」と「 [Mrtk-Pulse シェーダー](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) 」を参照してください。

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
