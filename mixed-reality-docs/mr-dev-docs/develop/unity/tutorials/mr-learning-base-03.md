---
title: MRTK プロファイルの構成
description: このコースでは、Mixed Reality アプリ用に Mixed Reality Toolkit (MRTK) プロファイルを構成する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality Toolkit, UWP, 空間認識
ms.localizationpriority: high
ms.openlocfilehash: 58f9c5f756a12e99fd10b136b2a450c6227b2dad
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008012"
---
# <a name="3-configuring-the-mrtk-profiles"></a>3.MRTK プロファイルの構成

このチュートリアルでは、MRTK プロファイルをカスタマイズして構成する方法について学習します。

<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html" target="_blank">MRTK プロファイル</a>は入れ子になったプロファイルのツリーであり、MRTK システムと機能の初期化方法に関する構成情報を構成しています。 最上位レベルのプロファイルである構成プロファイルには、各プライマリ コア システムに対する入れ子になったプロファイルが含まれています。 入れ子になった各プロファイルは、対応するシステムの動作を構成するように設計されています。

この特定の例では、空間メッシュ オブザーバーの設定を変更して、空間認識メッシュを非表示にする方法を示します。 ただし、次の同じ原則に従って、MRTK プロファイルのすべての設定または値をカスタマイズできます。

[前のチュートリアル](mr-learning-base-02.md#congratulations)の間にプロジェクトを HoloLens 2 に展開したときのように、<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">空間認識</a>メッシュは環境のジオメトリを表すメッシュのコレクションです。 これは最初に見ておくと役に立つ視覚情報ですが、見た目が繁雑になるのと、パフォーマンスに影響するのを避けるため、通常はオフになっています。

## <a name="objectives"></a>目標

* MRTK プロファイルをカスタマイズして構成する方法について学習する
* 空間認識メッシュを非表示にする

## <a name="changing-the-spatial-awareness-display-option"></a>空間認識表示オプションを変更する

空間認識メッシュを非表示にするための主な手順は次のとおりです。

1. 既定の構成プロファイルを複製する
2. 空間認識システムを有効にする
3. 既定の空間認識システムのプロファイルを複製する
4. 既定の空間認識メッシュ オブザーバーのプロファイルを複製する
5. 空間認識メッシュの可視性を変更する

> [!NOTE]
> 既定では、MRTK プロファイルは編集できません。 これらは、編集する前に複製する必要がある既定プロファイルのテンプレートです。 入れ子になったプロファイル レイヤーがいくつかあります。 そのため、1 つ以上の設定を構成するときは、複数のプロファイルを複製して編集するのが一般的です。

### <a name="1-clone-the-default-configuration-profile"></a>1.既定の構成プロファイルを複製する

> [!NOTE]
> 構成プロファイルは最上位のプロファイルです。 そのため、他のプロファイルを編集できるようにするには、まず構成プロファイルを複製する必要があります。

[Hierarchy]\(階層\) ウィンドウで **MixedRealityToolkit** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで、**MixedRealityToolkit** の構成プロファイルを **DefaultHoloLens2ConfigurationProfile** に変更します。

![DefaultHoloLens2ConfigurationProfile が選択された Unity MixedRealityToolkit コンポーネント](images/mr-learning-base/base-03-section1-step1-1.png)

**MixedRealityToolkit** オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで **[Copy & Customize]\(コピーしてカスタマイズ\)** ボタンをクリックして、[Clone Profile]\(プロファイルの複製\) ウィンドウを開きます。

![Unity MixedRealityToolkit コンポーネントの [Copy & Customize]\(コピーしてカスタマイズ\) ボタン](images/mr-learning-base/base-03-section1-step1-2.png)

[Clone Profile]\(プロファイルのクローン\) ウィンドウで、適切な **[Profile Name]\(プロファイル名\)** (例: _GettingStarted_HoloLens2ConfigurationProfile_) を入力し、 **[Clone]\(クローン\)** ボタンをクリックし、**DefaultHololens2ConfigurationProfile** の編集可能なコピーを作成します。

![Unity MixedRealityToolkit の構成プロファイルのクローン ポップアップ ウィンドウ](images/mr-learning-base/base-03-section1-step1-3.png)

新しく作成された構成プロファイルが、シーンの構成プロファイルとして割り当てられました。

![新しく作成したカスタム HoloLens2ConfigurationProfile が適用されている Unity MixedRealityToolkit コンポーネント](images/mr-learning-base/base-03-section1-step1-4.png)

Unity メニューで、 **[File]\(ファイル\)**  >  **[Save]\(保存\)** の順に選択してシーンを保存します。

> [!TIP]
> チュートリアルの実行中は、必ず作業を保存するようにしてください。

### <a name="2-enable-the-spatial-awareness-system"></a>2.空間認識システムを有効にする

[Hierarchy]\(階層\) ウィンドウで **MixedRealityToolkit** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで **[Spatial Awareness]\(空間認識\)** タブを選択し、次に **[Enable Spatial Awareness System]\(空間認識システムを有効にする\)** チェックボックスをオンにします。

![空間認識システムが有効になっている Unity MixedRealityToolkit コンポーネント](images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> 今後のプロジェクトのアプリで、環境に応答したり環境と対話したりする必要がない場合は、パフォーマンス コストを減らすため、空間認識をオフにしておくことをお勧めします。

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3.既定の空間認識システムのプロファイルを複製する

**[Spatial Awareness]\(空間認識\)** タブで、 **[Clone]\(複製\)** ボタンをクリックして [Clone Profile]\(プロファイルの複製\) ウィンドウを開きます。

![[Spatial Awareness]\(空間認識\) タブが選択された Unity MixedRealityToolkit コンポーネント](images/mr-learning-base/base-03-section1-step3-1.png)

[Clone Profile]\(プロファイルのクローン\) ウィンドウで、適切な **[Profile Name]\(プロファイル名\)** (例: _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_) を入力し、 **[Clone]\(クローン\)** ボタンをクリックし、**DefaultMixedRealitySpatialAwarenessSystemProfile** の編集可能なコピーを作成します。

![Unity MixedRealityToolkit 空間認識システム プロファイル クローン ポップアップ ウィンドウ](images/mr-learning-base/base-03-section1-step3-2.png)

これで、新しく作成された空間認識システム プロファイルが、構成プロファイルに自動的に割り当てられるようになりました。

![新しく作成したカスタム MixedRealitySpatialAwarenessSystemProfile が適用されている Unity MixedRealityToolkit コンポーネント](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4.既定の空間認識メッシュ オブザーバーのプロファイルを複製する

**[Spatial Awareness]\(空間認識\)** タブを引き続き選択した状態で、 **[Windows Mixed Reality Spatial Mesh Observer]\(Windows Mixed Reality 空間メッシュ オブザーバー\)** セクションを展開し、 **[Clone]\(複製\)** ボタンをクリックして、[Clone Profile]\(プロファイルの複製\) ウィンドウを開きます。

![Windows Mixed Reality 空間メッシュ オブザーバー セクションが展開された Unity MixedRealityToolkit コンポーネント](images/mr-learning-base/base-03-section1-step4-1.png)

[Clone Profile]\(プロファイルのクローン\) ウィンドウで、適切な **[Profile Name]\(プロファイル名\)** (例: _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_) を入力し、 **[Clone]\(クローン\)** ボタンをクリックし、**DefaultMixedRealitySpatialAwarenessMeshObserverProfile** の編集可能なコピーを作成します。

![Unity MixedRealityToolkit 空間メッシュ オブザーバー プロファイル クローン ポップアップ ウィンドウ](images/mr-learning-base/base-03-section1-step4-2.png)

これで、新しく作成された空間認識メッシュ オブザーバーが、空間認識システム プロファイルに自動的に割り当てられるようになりました。

![新しく作成したカスタム MixedRealitySpatialAwarenessMeshObserverProfile が適用されている Unity MixedRealityToolkit コンポーネント](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5.空間認識メッシュの可視性を変更する

**[Spatial Mesh Observer Settings]\(空間メッシュ オブザーバーの設定\)** で、 **[Display Option]\(表示オプション\)** を **[Occlusion]\(オクルージョン\)** に変更して、空間マッピング メッシュを、機能している状態のまま非表示にします。

![空間メッシュ オブザーバーの表示オプションがオクルージョンに設定される Unity MixedRealityToolkit コンポーネント](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> 空間マッピング メッシュは非表示になっていますが、引き続き存在して、機能しています。 たとえば、物理的な壁の後ろのホログラムなど、空間マッピング メッシュの背後にあるホログラムは表示されません。

ここまで、MRTK プロファイル内の設定を変更する方法を学習しました。 ご覧のように、MRTK の設定をカスタマイズするには、最初に既定のプロファイルのコピーを作成する必要があります。 既定のプロファイルは編集できないため、既定の設定に戻す場合の参照として常に保持します。 MRTK プロファイルとそのアーキテクチャの詳細については、[MRTK ドキュメント ポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)にある [MRTK プロファイルの構成ガイド](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)に関するページを参照してください。

## <a name="congratulations"></a>結論

このチュートリアルでは、MRTK プロファイルの設定をクローン、カスタマイズ、および構成する方法について学習しました。

> [!div class="nextstepaction"]
> [次のチュートリアル:4.シーンへのオブジェクトの配置](mr-learning-base-04.md)
