---
title: Unreal での空間オーディオ
description: HoloLens デバイス向け Unreal Mixed Reality アプリケーション用の空間オーディオ プラグインの概要について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 06/15/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, ストリーミング, リモート処理, Mixed Reality, 開発, 入門, 機能, 新しいプロジェクト, エミュレーター, ドキュメント, ガイド, 特徴, ホログラム, ゲームの開発, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, 空間オーディオ
ms.openlocfilehash: 98c10e370cd4ca5e437a4677be6fce3d3aee53a9
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009972"
---
# <a name="spatial-audio-in-unreal"></a>Unreal での空間オーディオ

視覚とは異なり、人間は 360 度のサラウンド サウンドを聞き取っています。 立体音響では、人間の聴覚のしくみをエミュレートし、ワールド空間でサウンドの位置を識別するのに必要なキューを提供しています。 Mixed Reality アプリケーションに立体音響を追加すると、ユーザーが経験する没入感のレベルを向上できます。  

高品質の立体音響処理は複雑であるため、HoloLens 2 には、それらのサウンド オブジェクトを処理するための専用ハードウェアが付属しています。  このハードウェア処理のサポートを利用するには、Unreal プロジェクトに **MicrosoftSpatialSound** プラグインをインストールする必要があります。 この記事では、そのプラグインのインストールと構成について説明し、さらに詳細なリソースを紹介します。

## <a name="installing-the-microsoft-spatial-sound-plugin"></a>Microsoft 立体音響プラグインのインストール

立体音響をプロジェクトに追加するには、最初に Microsoft 立体音響プラグインをインストールします。このプラグインは次の手順で見つけられます。

1. **[編集] > [プラグイン]** の順にクリックし、検索ボックスで「**MicrosoftSpatialSound**」を検索します。
2. **MicrosoftSpatialSound** プラグインの **[有効]** チェックボックスをオンにします。
3. [プラグイン] ページの **[今すぐ再起動]** を選択して、Unreal エディターを再起動します。

> [!NOTE]
> まだインストールしていない場合は、**Microsoft Windows Mixed Reality** プラグインと **HoloLens** プラグインをインストールする必要があります。インストールの手順については、Unreal チュートリアル シリーズの **[プロジェクトの初期化](tutorials/unreal-uxt-ch2.md)** に関するページを参照してください。

![Unreal の空間オーディオ プラグイン](images/unreal-spatial-audio-img-01.png)

エディターが再起動すると、プロジェクトの設定はすべて完了です。

## <a name="setting-the-spatialization-plugin-for-hololens-2-platform"></a>HoloLens 2 プラットフォーム用の空間化プラグインの設定

空間化プラグインの構成は、プラットフォームごとに行います。  HoloLens 2 用の Microsoft 立体音響プラグインは、次の手順で有効にできます。
1. **[Edit]\(編集\) > [Project Settings]\(プロジェクトの設定\)** を選択し、[Platforms]\(プラットフォーム\) までスクロールして、 **[HoloLens]** をクリックします。
2. **[オーディオ]** プロパティを展開し、 **[Spatialization Plugin]\(空間化プラグイン\)** フィールドを **[Microsoft 立体音響]** に設定します。

![HoloLens プラットフォーム用の空間化プラグイン](images/unreal-spatial-audio-img-02.png)

デスクトップ PC の Unreal エディターでアプリケーションをプレビューする場合は、**Windows** プラットフォームに対して上記の手順を繰り返す必要があります。

![Windows プラットフォーム用の空間プラグイン](images/unreal-spatial-audio-img-05.png)

## <a name="enabling-spatial-audio-on-your-workstation"></a>ワークステーションでの空間オーディオの有効化

空間オーディオは、デスクトップ バージョンの Windows では既定で無効になっています。 次の手順で空間オーディオを有効にできます。
* タスク バーの **[ボリューム]** アイコンを右クリックします。
    + **[立体音響] -> [Windows Sonic for Headphones]** の順に選択することで、HoloLens 2 で聞こえる内容を最適に再生できるようになります。

![空間化プラグイン](images/unreal-spatial-audio-img-04.png)

> [!NOTE]
>この設定は、プロジェクトを Unreal エディターでテストする場合にのみ必要です。

## <a name="creating-attenuation-objects"></a>減衰オブジェクトの作成

必要なプラグインのインストールと構成を完了した後に、次の手順を実行します。
1. **[Place Actors]\(アクターの配置\)** ウィンドウで **[Ambient Sound]\(アンビエント サウンド\)** アクターを検索し、 **[シーン]** ウィンドウにドラッグします。

![アンビエント サウンド アクターの追加](images/unreal-spatial-audio-img-07.png)

2. **アンビエント サウンド** アクターを、シーン内のビジュアル要素の子に設定します。
    * アンビエント サウンド アクターには、既定ではビジュアル表現がありません。このため、シーン内の配置された場所から音声が聞こえるだけになります。 このアクターをビジュアル要素にアタッチすると、他の資産と同様にアクターを表示し、移動することができます。

3.  **コンテンツ ブラウザー** を右クリックし、 **[Create Advanced Asset]\(高度な資産の作成\) -> [サウンド] -> [Sound Attenuation]\(サウンドの減衰\)** の順に選択します。

![サウンドの減衰資産の作成](images/unreal-spatial-audio-img-06.png)

4. **コンテンツ ブラウザー** ウィンドウで **[Sound Attenuation]\(サウンドの減衰\)** 資産を右クリックし、 **[編集]** オプションを選択して、[プロパティ] ウィンドウを表示します。
    * **[Spatialization Method]\(空間化メソッド\)** を **[Binaural]\(バイノーラル\)** に切り替えます。

![空間化メソッドの設定](images/unreal-spatial-audio-img-03.png)

5. **アンビエント サウンド** アクターを選択し、 **[詳細]** パネルの **[減衰]** セクションまで下にスクロールします。
    * **[減衰設定]** プロパティを、作成した **[Sound Attenuation]\(サウンドの減衰\)** 資産に設定します。

![減衰設定の設定](images/unreal-spatial-audio-img-08.png)

6. アンビエント サウンド アクターにアタッチする **[Sound Asset]\(サウンド資産\)** を設定します。
    * アンビエント サウンド アクターの **[Sound]\(サウンド\)** プロパティを更新し、使用する SoundAsset ファイルを指定します。

![サウンド資産の設定](images/unreal-spatial-audio-img-09.png)

> [!NOTE]
> Microsoft 立体音響プラグインを使用して空間化するには、SoundAsset ファイルはモノラルである必要があります。 次のスクリーンショットに示すように、コンテンツ ブラウザー ウィンドウで資産にカーソルを合わせると、そのサウンド ファイルのプロパティが表示されます。

![新しいサウンドの減衰資産](images/unreal-spatial-audio-img-10.png)

サウンド資産を構成したら、HoloLens 2 の専用ハードウェア オフロードのサポートを使用して、アンビエント サウンドを空間化することができます。

## <a name="configuring-objects-for-spatialization"></a>空間化のためのオブジェクトの構成

空間オーディオを使用すると、仮想環境でのサウンドの動作を管理することが必要になります。 主に必要になるのは、ユーザーが接近すると音が大きくなり、ユーザーが離れると音が静かになるように感じられるサウンド オブジェクトを作成することです。 これはサウンドの減衰と呼ばれ、これにより、サウンドが決まった地点に配置されているように感じられるようになります。

すべての減衰オブジェクトには、変更可能な次の設定が用意されています。
* 距離
* 空間化
* 空気吸収
* リスナー フォーカス
* リバーブ センド
* オクルージョン

これらの各トピックに関する詳細と実装の仕様については、[Unreal のサウンドの減衰](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html)に関するページを参照してください。

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

用意されている Unreal 開発体験に従っている場合、MRTK コア構成要素を探索している段階にいます。 ここから、次の構成要素を続けることができます。

> [!div class="nextstepaction"]
> [音声入力](unreal-voice-input.md)

または、Mixed Reality プラットフォームの機能と API に移動します。

> [!div class="nextstepaction"]
> [HoloLens カメラ](unreal-hololens-camera.md)

いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#2-core-building-blocks)に戻ることができます。


## <a name="see-also"></a>関連項目
* [立体音響](https://docs.microsoft.com/windows/mixed-reality/spatial-sound)
* [立体音響の設計](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)
* [MR 空間 220:立体音響](https://docs.microsoft.com/windows/mixed-reality/holograms-220)
