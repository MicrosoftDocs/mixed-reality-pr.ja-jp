---
title: MRTK を使用せずにプロジェクトを構成する
description: Mixed Reality Toolkit を使用せずに、Windows Mixed Reality 用の新しい Unity プロジェクトを構成する方法について説明します。
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity、mixed reality、開発、作業の開始、新しいプロジェクト、Windows Mixed Reality、UWP、XR、パフォーマンス
ms.openlocfilehash: bd25c56947007f90c0310ea9802bba91a81b0914
ms.sourcegitcommit: fd19bf57607c7ed94a849d4cf606bba2bb93e668
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102117626"
---
# <a name="configuring-your-project-without-mrtk"></a>MRTK を使用しないプロジェクトを構成する

Windows Mixed Reality (WMR) は、Windows 10 オペレーティングシステムの一部として導入された Microsoft プラットフォームです。 WMR プラットフォームを使用すると、holographic および VR 表示デバイスでデジタルコンテンツをレンダリングするアプリケーションを作成できます。

Microsoft とコミュニティは、wmr 環境を自動的に設定する [Mixed Reality Toolkit (mrtk)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) などのオープンソースツールを作成していますが、多くの開発者は、経験をゼロから構築することを望んでいます。  次のドキュメントでは、MRTK を使用しているかどうかにかかわらず、Mixed Reality 開発用のプロジェクトを適切に設定する方法を示します。  変更が必要な設定は、プロジェクトごとの設定とシーンごとの設定という2つのカテゴリに分類されます。

> [!NOTE]
> MRTK は、後でいつでもインポートできます。そのため、最初に手動による処理による影響はありません。

WMR 手動セットアップを選択した場合、変更する必要がある設定は、プロジェクトごととシーン単位の2つのカテゴリに分類されます。

## <a name="per-project-settings"></a>プロジェクトごとの設定

Desktop VR を対象としている場合は、新しい Unity プロジェクトで既定で選択されている PC スタンドアロンプラットフォームを使用することをお勧めします。

![[ビルドの設定] ウィンドウのスクリーンショット PC、Mac & スタンドアロンプラットフォームが強調表示されている unity エディターで開く](images/wmr-config-img-3.png)

HoloLens 2 を対象としている場合は、ユニバーサル Windows プラットフォームに切り替える必要があります。

1.  **ファイル > ビルド設定** を選択してください...
2.  [プラットフォーム] ボックスの一覧で [**ユニバーサル Windows プラットフォーム** を選択し、[**プラットフォームの切り替え**] を選択します。
3.  **アーキテクチャ** を **ARM 64** に設定する
4.  **ターゲットデバイス** を **HoloLens** に設定する
5.  **ビルドの種類** を **D3D** に設定
6.  **UWP SDK** を **最新のインストール** に設定する
7.  デバッグに関する既知のパフォーマンスの問題があるため、 **ビルド構成** を **リリース** に設定します

![ユニバーサル Windows プラットフォーム強調表示された [ビルド設定] ウィンドウのスクリーンショット (unity エディターで開く)](images/wmr-config-img-4.png)

プラットフォームを設定した後は、エクスポート時に2D ビューではなく、 [イマーシブビュー](../../design/app-views.md) を作成するよう Unity に知らせる必要があります。

### <a name="for-xrsdk"></a>XRSDK の場合 

1. Unity エディターで、[ **Edit > プロジェクトの設定**] に移動し、[ **XR Plugin Management** ] を選択します。

2. [ **INSTALL XR Plugin Management** ] を選択します。

![XR Plugin management が強調表示されている unity エディターで開き、[プロジェクトの設定] ウィンドウのスクリーンショット](images/wmr-config-img-5.png)

3. [スタートアップと **Windows Mixed Reality** **で XR を初期化** する] を選択します。

![XR Plugin management が強調表示されている unity エディターで開き、[プロジェクトの設定] ウィンドウのスクリーンショット](images/wmr-config-img-7.png)

4. **XR プラグイン管理** セクションを展開し、[**ユニバーサル Windows Platform Settings** ] タブを選択します。
5. Unity 2020 以降を使用している場合は、 **OpenXR (プレビュー)** または **Windows Mixed Reality** を確認するためのオプションが表示されます。
6. いずれかのランタイムを選択できます。  HoloLens 2 または HP リバーブ G2 用に特に開発していて、 **OpenXR (プレビュー)** を試す場合は、[OpenXR (プレビュー)] ボックスを選択して、このチュートリアルに戻る前に、 [Unity 用の Mixed Reality OpenXR プラグインを使用して](openxr-getting-started.md) 、これらのデバイスに適切に設定するためのガイドを参照してください。
7. **Windows Mixed Reality** プラグインを選択する場合は、すべてのチェックボックスをオンにし、**深さの送信モード** を **深さ16ビット** に設定します。

![Windows Mixed Reality セクションが強調表示されている unity エディターで開いているプロジェクト設定ウィンドウのスクリーンショット](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a>レガシ XR の場合 

> [!CAUTION]
> 従来の XR は Unity 2019 で非推奨とされ、Unity 2020 では削除されています。

1. ビルド設定から **プレーヤー設定** を開く... **ウィンドウ** を開き、 **XR 設定** グループを展開します。
2. [ **XR の設定** ] セクションで、[virtual Reality のサポート] を選択し **て** 、仮想現実のデバイスの一覧を追加します。
3. **深さの形式** を **16 ビット深度** に設定し、**深度バッファーの共有** を有効にします
4. **ステレオレンダリングモード** を **シングルパスインスタンス** に設定する
5. Holographic リモート処理を使用する場合は、[ **WSA Holographic リモート処理がサポートされてい** ます] を選択します。 

![[プレーヤーの設定] セクションが強調表示されている unity エディターで開いているプロジェクト設定ウィンドウのスクリーンショット](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a>マニフェストを更新しています

これで、アプリで holographic のレンダリングと空間入力を処理できるようになりました。 ただし、アプリでは、特定の機能を利用するために、マニフェストで適切な機能を宣言する必要があります。 プロジェクト機能を検索するには、 **ユニバーサル Windows プラットフォーム > 発行設定 > 機能の > 設定**] に移動します。 

エクスポートする今後のすべてのプロジェクトにマニフェスト宣言を含めることをお勧めします。 Mixed Reality で一般的に使用される Unity Api を有効にするための適用可能な機能は次のとおりです。

|  機能  |  機能を必要とする Api | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (HoloLens 上の [空間マッピング](../../design/spatial-mapping.md)メッシュへのアクセス) &mdash; *ヘッドセットの一般的な空間追跡に必要な機能はありません* | 
|  WebCam  |  PhotoCapture と VideoCapture | 
|  PicturesLibrary / VideosLibrary  |  PhotoCapture または VideoCapture (キャプチャされたコンテンツを格納する場合) | 
|  マイク  |  VideoCapture (オーディオをキャプチャする場合)、DictationRecognizer、GrammarRecognizer、および KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (および Unity Profiler の使用) | 

### <a name="quality-settings"></a>品質設定

HoloLens には、モバイルクラスの GPU があります。 アプリが HoloLens を対象としている場合は、アプリの品質設定から開始して、最大のパフォーマンスを実現し、完全なフレームレートを維持することをお勧めします。  を開発に追加した後は、品質設定への ping を実行して品質とパフォーマンスのバランスを適切に調べることを検討できます。 

1. [ **プロジェクト設定の編集 > の > 品質**] を選択します。 
2.  **Windows ストア** のロゴの下にある **ドロップダウン** を選択し、   [ **非常に低い**] を選択します。 Windows ストアの列のボックスと非常に少ない行が緑色になっていると、設定が正しく適用されていることがわかります。 
3. [ **影**   ] セクションで、[ **影を無効にする**] を選択します。 

![[品質設定] セクションが強調表示されている unity エディターで開いているプロジェクト設定ウィンドウのスクリーンショット](images/wmr-config-img-10.png)<br>
*Unity の品質設定*

## <a name="per-scene-settings"></a>シーンごとの設定

### <a name="unity-camera-settings"></a>Unity カメラの設定

[ **サポートされている仮想 Reality** ] チェックボックスをオンにすると、 [Unity カメラ](camera-in-unity.md) コンポーネントは [ヘッド追跡とステレオスコピックレンダリング](../platform-capabilities-and-apis/rendering.md)を処理します。 つまり、メインのカメラオブジェクトをカスタムカメラに置き換える必要はありません。

アプリが HoloLens を対象としている場合は、デバイスの透明ディスプレイを最適化するために、いくつかの設定を変更する必要があります。 これらの設定により、holographic コンテンツが物理的な世界に表示されるようになります。

1. **階層** で、**メインカメラ** を選択します。
2. [ **インスペクター** ] パネルで、[変換 **位置** ] を **0、0、0** に設定します。これにより、ユーザーのヘッドの位置が Unity の元の場所から開始されます。
3. **クリアフラグ** を **純色** に変更します。
4. **背景** 色を **RGBA 0、0、0、0** に変更します。 ブラックは HoloLens では透明としてレンダリングされます。
5. **クリッププレーン** を [HoloLens の推奨](camera-in-unity.md#clip-planes)0.85 (メーター) に近い場所に変更します。

![Unity エディターで開いている [インスペクター] タブのスクリーンショット](images/wmr-config-img-11.png)<br>
*Unity カメラの設定*

> [!IMPORTANT]
> 新しいカメラを削除して作成する場合は、新しいカメラが **maincamera** としてタグ付けされていることを確認してください。

## <a name="next-steps"></a>次のステップ

プロジェクトの準備ができたので、次のように Mixed Reality エクスペリエンスの開発を開始できます。

* [コア構成要素](unity-development-overview.md#2-core-building-blocks)の追加
* 使用可能な[プラットフォーム機能と api を](unity-development-overview.md#3-advanced-features)確認する
* [アプリをデプロイ](../platform-capabilities-and-apis/using-visual-studio.md#)する方法を学習する
* [Mixed Reality シミュレーター](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)を使用する

## <a name="see-also"></a>関連項目
* [ツールのインストール](../install-the-tools.md)