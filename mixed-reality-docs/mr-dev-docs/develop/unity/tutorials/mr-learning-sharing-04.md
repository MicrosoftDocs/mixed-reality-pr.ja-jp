---
title: マルチユーザー機能のチュートリアル - 4. 複数のユーザーとオブジェクトの移動を共有する
description: このコースを完了すると、HoloLens 2 アプリケーション内でオブジェクトの移動を複数のユーザーで共有する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 4a8d98bbabd3061e8fb9f4262e202dac680d584b
ms.sourcegitcommit: 63c228af55379810ab2ee4f09f20eded1bb76229
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2020
ms.locfileid: "93353420"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4.複数のユーザーとオブジェクトの移動を共有する

このチュートリアルでは、共有エクスペリエンスのすべての参加者が共同作業したり、相互の操作を表示したりできるように、オブジェクトの移動を共有する方法について説明します。

## <a name="objectives"></a>目標

* オブジェクトの移動を共有するようにプロジェクトを構成する
* 基本的なマルチユーザー コラボレーション アプリを構築する方法を学習する

## <a name="preparing-the-scene"></a>シーンの準備

このセクションでは、チュートリアルのプレハブを追加してシーンを準備します。

プロジェクト ウィンドウで **アセット** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs\(プレハブ\)** フォルダーの順に移動して、**TableAnchor** プレハブを 階層 ウィンドウの **SharedPlayground** オブジェクト上にドラッグし、SharedPlayground オブジェクトの子としてシーンに追加します。

![新しく追加された TableAnchor プレハブが選択されている Unity](images/mr-learning-sharing/sharing-04-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a>PUN を構成してオブジェクトのインスタンスを作成する

このセクションでは、「[入門チュートリアル](mr-learning-base-01.md)」で作成した Rover Explorer エクスペリエンスを使用するようにプロジェクトを構成し、そのプロジェクトがインスタンス化される場所を定義します。

[Project]\(プロジェクト\) ウィンドウで **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.MultiUserCapabilities]**  >  **[Resources]\(リソース\)** フォルダーに移動します。

[Hierarchy]\(ヒエラルキー\) ウィンドウで **NetworkLobby** オブジェクトを展開して **NetworkRoom** 子オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで **Photon Room (Script)** コンポーネントを探し、次のように構成します。

* **Rover Explorer の [Prefab]\(プレハブ\)** フィールドに、[リソース] フォルダーから **RoverExplorer_Complete_Variant** プレハブを割り当てます

![Photon Room コンポーネントが部分的に構成された Unity](images/mr-learning-sharing/sharing-04-section2-step1-1.png)

**NetworkRoom** 子オブジェクトを選択したまま [Hierarchy]\(ヒエラルキー\) ウィンドウで **TableAnchor** オブジェクトを展開し、[Inspector]\(インスペクター\) ウィンドウで **Photon Room (Script)** コンポーネントを探して次のように構成します。

* **Rover Explorer の [場所]** フィールドに、[階層] ウィンドウから TableAnchor > **Table** 子オブジェクトを割り当てます

![Photon Room コンポーネントが構成された Unity](images/mr-learning-sharing/sharing-04-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a>共有オブジェクト移動のエクスペリエンスを試す

Unity プロジェクトをビルドして HoloLens にデプロイしてから Unity に戻り、HoloLens でアプリが実行されている間に [再生] ボタンを押してゲーム モードに入ると、HoloLens でオブジェクトを動かした時に Unity でオブジェクトが移動するのを確認できます。

![ネットワーク接続されたオブジェクトが表示された Unity を表示するアニメーション](images/mr-learning-sharing/sharing-04-section3-step1-1.gif)

## <a name="congratulations"></a>結論

他のユーザーがオブジェクトを移動したときにそのオブジェクトの移動をユーザーが確認できるように、プロジェクトでオブジェクトの移動が同期するように構成できました。 次のチュートリアルでは、現実の世界に合わせてエクスペリエンスを調整するための機能を実装します。 これにより、ユーザーどうしが実際の物理的な位置関係にいるように表示したり、オブジェクトがどのユーザーからも同じ物理的な位置と角度で表示されるようにしたりできます。

> [!div class="nextstepaction"]
> [次のチュートリアル:5.Azure Spatial Anchors の共有エクスペリエンスへの統合](mr-learning-sharing-05.md)
