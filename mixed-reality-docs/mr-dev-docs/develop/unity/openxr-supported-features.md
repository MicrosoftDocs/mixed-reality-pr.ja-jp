---
title: Unity でサポートされている OpenXR プラグインの機能
description: Unity での mixed reality 開発に OpenXR がサポートする機能について説明します。
author: hferrone
ms.author: alexturn
ms.date: 12/15/2020
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 拡張現実, 仮想現実, mixed reality ヘッドセット, 学習, チュートリアル, 概要
ms.openlocfilehash: dc908762d6e44e04f56b8ff82b90394106ca42e5
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2020
ms.locfileid: "97622946"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>Unity でサポートされている Mixed Reality OpenXR の機能

**Mixed Reality OpenXR プラグイン** パッケージは Unity の **OpenXR プラグイン** の拡張機能であり、HoloLens 2 および Windows Mixed Reality ヘッドセットの一連の機能をサポートしています。 続行する前に、 **unity 2020.2** 以降、 **OpenXR プラグインバージョン 0.1.1** 以降がインストールされていること、および unity プロジェクトが [OpenXR 用に構成](openxr-getting-started.md)されていることを確認してください。

## <a name="whats-supported"></a>サポートされる操作

現在、次の機能がサポートされています。

* Windows Mixed Reality ヘッドセット用の HoloLens 2 および Win32 VR アプリケーションの両方の UWP アプリケーションをサポートします。
* HoloLens 2 アプリケーションの UWP パッケージと CoreWindow の相互作用を最適化します。
* アンカーと無制限のスペースを使用したワールドスケールの追跡。
* ストレージ API を固定して、HoloLens 2 ローカルストレージにアンカーを保持します。
* 新しい HP リバーブ G2 コントローラーを含む、モーションコントローラーと手作業のやり取り。
* 26個の関節と結合半径の入力を使用した、トレーラーを使用したハンドトラッキング。
* HoloLens 2 での視線の相互作用。
* HoloLens 2 で写真/ビデオ (PV) カメラを検索しています。
* PV カメラを使用した第3目のレンダリングを使用した Mixed Reality キャプチャ。
* Holographic リモート処理アプリを使用して HoloLens 2 への "Play" をサポートします。これにより、開発者は、デバイスにビルドしてデプロイすることなく、スクリプトをデバッグできます。
* Mrtk Unity 2.5.2 から MRTK OpenXR adapter パッケージに準拠しています。 <missing link>
* Unity [Arfoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 以降との互換性

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Unity エディター再生モードでの Holographic リモート処理

Visual Studio プロジェクトで UWP Unity プロジェクトをビルドしてから、パッケージ化して HoloLens 2 デバイスに配置すると、時間がかかることがあります。 1つの解決策は、Holographic エディターのリモート処理を有効にすることです。これにより、ネットワーク上の HoloLens 2 デバイスに対して "Play" モードで直接 C# スクリプトをデバッグできます。 このシナリオでは、UWP パッケージをビルドしてリモートデバイスに配置するオーバーヘッドを回避します。

1. まず、HoloLens 2 のストアから [Holographic Remoting Player アプリをインストール](https://www.microsoft.com/store/productId/9NBLGGH4SV40) する必要があります。  
2. HoloLens 2 で Holographic リモート処理プレーヤーアプリを実行すると、接続先のバージョン番号と IP アドレスが表示されます。
    * OpenXR プラグインを使用するには、v2.0 以降が必要です。

![HoloLens で実行されている Holographic リモート処理プレーヤーのスクリーンショット](images/openxr-features-img-01.png)

3. [ **編集-> プロジェクトの設定**] を開き、 **XR プラグイン管理** に移動して、[ **Windows Mixed Reality] 機能セット** ボックスをオンにします。

![XR プラグイン管理が強調表示されている Unity エディターで開いているプロジェクト設定パネルのスクリーンショット](images/openxr-features-img-02.png)

4. **OpenXR** の [**機能**] セクションを展開し、[**すべて表示**] を選択します。
5. [ **Holographic エディターリモート処理** ] チェックボックスをオンにして、Holographic リモート処理アプリから取得した IP アドレスを入力します。

![機能が強調表示されている Unity エディターでプロジェクト設定パネルが開いているスクリーンショット](images/openxr-features-img-03.png)

これで、[Play] \ (再生 \) ボタンをクリックして、HoloLens の Holographic リモート処理アプリで Unity アプリを再生できるようになりました。 また、 [Visual Studio を Unity にアタッチ](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) して、C# スクリプトを再生モードでデバッグすることもできます。

> [!NOTE]
> 0.1.0 のバージョンでは、Holographic リモート処理ではアンカー機能がサポートされておらず、ARAnchorManager 機能はリモート処理では機能しません。  この機能は今後のリリースで予定されています。

## <a name="motion-controller-and-hand-interactions"></a>モーションコントローラーとハンド作用
Unity での mixed reality の相互作用の基本については、unity の unity の [XR 入力](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)に関するページを参照してください。 この Unity ドキュメントでは、コントローラー固有の入力からより多くの汎化に対するマッピング、 `InputFeatureUsage` 使用可能な XR 入力を識別および分類する方法、これらの入力からデータを読み取る方法などについて説明します。 
 
Mixed Reality OpenXR プラグインは、次に示すように、標準のにマップされている追加の入力インタラクションプロファイルを提供し `InputFeatureUsage` ます。 
 
| `InputFeatureUsage` | HP リバーブ G2 コントローラー (OpenXR) | HoloLens (OpenXR) |
| ---- | ---- | ---- |
| primary2DAxis | ジョイ | |
| primary2DAxisClick | ジョイスティック-クリック | |
| トリガー (trigger) | トリガー  | |
| 把握 | 把握 | エアタップまたはつかみ |
| primaryButton | [X/A]-押します | エアタップ |
| secondaryButton | [Y/B]-押します | |
| gripButton | グリップ-押す | |
| triggerButton | トリガー-押す | |
| menuButton | メニュー | |

#### <a name="haptics"></a>Haptics
Unity の XR 入力システムで haptics を使用する方法の詳細については、unity の unity [マニュアルの「UNITY XR](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)」を参照してください。 


## <a name="whats-coming-soon"></a>近日公開予定

次の問題および不足している機能は、Mixed Reality OpenXR プラグイン **バージョン 0.1.0** で知られています。 これらの機能については、今後のリリースで修正と新機能をリリースする予定です。

* **ARPlaneSubsystem** はまだサポートされていません。 HoloLens 2 では、 **Arplan emanager**、 **ARRaycastManager**、および ARANCHORMANAGER などの関連 API もサポートされていません **。**
* **アンカー** は Holographic リモート処理ではまだサポートされていませんが、近い将来に登場します。
* **手動メッシュ** 追跡、 **QR コード**、 **XRMeshSubsystem** はまだサポートされていません。
* **Azure 空間アンカー** のサポートは、今後のリリースで予定されています。
* **ARM64** は、HoloLens 2 アプリで唯一サポートされているプラットフォームです。 **ARM** プラットフォームは今後のリリースで予定されています。

## <a name="troubleshooting"></a>トラブルシューティング 

HoloLens 2 で Unity アプリを中断および再開すると、アプリは正しく再開できなくなります。これにより、HoloLens ビューでは、4つのスピン点が表示されます。 
* 回避策として、OpenXR プロジェクト設定で [ **深さの送信モード** ] を **[なし** ] に設定します。
