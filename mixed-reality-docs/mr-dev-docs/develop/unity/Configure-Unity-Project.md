---
title: Windows Mixed Reality 用の新しい Unity プロジェクトを構成する
description: Windows Mixed Reality の Unity プロジェクトを構成する手順
author: thetuvix
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity、mixed reality、開発、作業の開始、新しいプロジェクト、Windows Mixed Reality、UWP、XR、パフォーマンス
ms.openlocfilehash: cd7e6c5681c717c37368393a605998a2ab8e4175
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677671"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>Windows Mixed Reality 用の新しい Unity プロジェクトを構成する 

## <a name="overview"></a>概要

Windows Mixed Reality (WMR) は、Windows 10 オペレーティングシステムの一部として導入された Microsoft プラットフォームです。 WMR プラットフォームを使用すると、holographic および VR 表示デバイスでデジタルコンテンツをレンダリングするアプリケーションを作成できます。

WMR の設定時に実行できるパスは2つあります。 最初のオプションとして、 [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)をインストールします。これにより、wmr 環境が自動的に設定されます。 2つ目のオプションは、いくつかの Unity 設定を手動で変更して、WMR をロールします。 

> [!NOTE]
> MRTK は、後でいつでもインポートできます。そのため、最初に手動による処理による影響はありません。

WMR 手動セットアップを選択した場合、変更する必要がある設定は、プロジェクトごととシーン単位の2つのカテゴリに分類されます。

## <a name="per-project-settings"></a>プロジェクトごとの設定

WMR の最初の設定を変更する必要があるのは、プロジェクトプラットフォームです。 
1. **ファイル > ビルド設定** を選択してください...
2. [プラットフォーム] ボックスの一覧の [**ユニバーサル Windows プラットフォーム** を選択し、[**プラットフォームの切り替え**] をクリックします。
3. **SDK** を **Universal 10** に設定する
4. イマーシブヘッドセットまたは **HoloLens** への切り替えをサポートするために、**ターゲットデバイス** を **任意のデバイス** に設定する
5. **ビルドの種類** を **D3D** に設定
6. **UWP SDK** を **最新のインストール** に設定する

<img src="images/unity-uwp-settings.png" width="550px" alt="Unity XR Settings">
*Unity XR の設定*

プラットフォームが正しく構成されたら、アプリがエクスポート時に2D ビューではなく、 [イマーシブビュー](../../design/app-views.md) を作成する必要があることを Unity に知らせる必要があります。
1. [**ビルドの設定...** ] ウィンドウで、[プレーヤーの **設定**] を開きます。
2. ユニバーサル Windows プラットフォーム] タブ **の [設定** ] を選択し、[ **XR settings** ] グループを展開します。
3. [ **XR の設定** ] セクションで、[ **仮想現実のサポート** ] チェックボックスをオンにして、[ **仮想現実のデバイス** ] の一覧を追加します。
4. [ **XR 設定** ] グループで、 **"Windows Mixed Reality"** がサポートされているデバイスとして表示されていることを確認します。 (このオプションは、旧バージョンの Unity では **Windows Holographic** として表示される場合があります)

![Unity UWP の設定](images/xrsettings.png)<br>
*Unity XR の設定*

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

HoloLens には、モバイルクラスの GPU があります。 アプリが HoloLens を対象としている場合は、アプリの品質設定を最適なパフォーマンスのために調整して、完全なフレームレートを維持する必要があります。
1. [**プロジェクト設定の編集 > の > 品質**] を選択します。
2. **Windows ストア** のロゴの下にある **ドロップダウン** を選択し、[**非常に低い**] を選択します。 [Windows Store]\(Windows ストア\) 列のボックスと **[Very Low]\(非常に低い\)** 行が緑色の場合、設定が適切に適用されていることがわかります。

![Unity の品質設定](images/getting-started-unity-quality-settings.jpg)<br>
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

![Unity カメラの設定](images/Unitycamerasettings.png)<br>
*Unity カメラの設定*

> [!IMPORTANT]
> 新しいカメラを削除して作成する場合は、新しいカメラが **maincamera** としてタグ付けされていることを確認してください。

## <a name="see-also"></a>関連項目
* [MRTK - インストール ガイド (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [MRTK - ドキュメント ホーム (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [ツールのインストール](../install-the-tools.md)
* [Unity 開発の概要](unity-development-overview.md)
