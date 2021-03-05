---
title: Unity に Mixed Reality OpenXR プラグインを使用する
description: Unity プロジェクトで Mixed Reality OpenXR プラグインを有効にする方法について説明します。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 拡張現実, 仮想現実, mixed reality ヘッドセット, 学習, チュートリアル, 概要
ms.openlocfilehash: a4606eeb1fa6c8dc0858653a196c1e536ae473d4
ms.sourcegitcommit: e2228b9585302eeff1d853ddb54be8421a21c954
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102189124"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a>Unity に Mixed Reality OpenXR プラグインを使用する

Unity バージョン2020.2 以降、Microsoft の Mixed Reality OpenXR プラグインパッケージは、Unity パッケージマネージャー (UPM) を使用して利用できます。

## <a name="prerequisites"></a>前提条件

* Unity 2020.2 以降
* Unity OpenXR plugin 0.1.3 以降
* Visual Studio 2019 以降
* HoloLens 2 アプリの **UWP** プラットフォームサポートを Unity でインストールする

> [!NOTE]
> Windows PC で VR アプリケーションを構築している場合、Mixed Reality OpenXR プラグインは必ずしも必要ではありません。 ただし、HP リバーブ G2 コントローラーのコントローラーマッピングをカスタマイズしている場合、または HoloLens 2 と VR ヘッドセットの両方で動作するアプリを作成する場合は、プラグインをインストールする必要があります。

## <a name="installing-openxr-with-the-mixed-reality-feature-tool"></a>Mixed Reality 機能ツールを使用した OpenXR のインストール

新しい Mixed Reality 機能ツールアプリケーションを使用して OpenXR プラグインをインストールします。 [インストールと使用に関する指示](welcome-to-mr-feature-tool.md)に従って、Mixed reality Toolkit カテゴリで **Mixed reality OpenXR プラグイン** パッケージを選択します。

![Open xr plugin が強調表示されている Mixed Reality 機能ツールパッケージウィンドウ](images/feature-tool-openxr.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a>OpenXR の XR Plugin Management の構成

Unity のランタイムとして OpenXR を設定するには、次のようにします。

1. Unity エディターで、[ **Edit > プロジェクトの設定**] に移動します。
2. 設定の一覧で、[ **XR Plugin Management** ] を選択します。
3. **[XR On Startup** and **OpenXR (プレビュー)** ] ボックスをオンにします。
4. HoloLens 2 を対象とする場合は、UWP プラットフォームを使用していることを確認し、[ **Microsoft HoloLens] 機能セット** を選択します。

![XR プラグイン管理が強調表示されている Unity エディターで開いているプロジェクト設定パネルのスクリーンショット](images/openxr-img-05.png)

> [!IMPORTANT]
> **OpenXR Plugin (Preview)** の横に赤い警告アイコンが表示された場合は、アイコンをクリックし、[**すべて修正**] を選択してから続行します。 変更を有効にするには、Unity エディター自体を再起動することが必要になる場合があります。

![OpenXR プロジェクト検証ウィンドウのスクリーンショット](images/openxr-img-06.png)

Unity で OpenXR を使用して開発を始める準備ができました。  OpenXR サンプルの使用方法については、次のセクションに進んでください。

## <a name="optimization"></a>Optimization

HoloLens 2 用に開発している場合は、 **Mixed Reality> > OpenXR に移動し、hololens 2 に推奨されるプロジェクト設定を適用して** 、アプリのパフォーマンスを向上させます。

![OpenXR が選択された状態で開いている mixed reality メニュー項目のスクリーンショット](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a>Unity のサンプルシーンを試す

1つ以上の例を使用するには、**パッケージマネージャー** から [arfoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation)をインストールします。

![Unity エディターで、AR Foundation が強調表示されている Unity パッケージマネージャーを開くスクリーンショット](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a>HoloLens 2 のサンプル

1. Unity エディターで、[ **] ウィンドウ > [パッケージマネージャー]** の順に移動します。
2. パッケージの一覧で [ **Mixed Reality OpenXR Plugin** ] を選択します。
3. **サンプル一覧で** サンプルを探し、[**インポート**] を選択します。

![Unity エディターで開く Unity パッケージマネージャーのスクリーンショット Mixed Reality OpenXR プラグインが選択され、サンプルのインポートボタンが強調表示されている](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> パッケージが更新されると、Unity にはインポートされたサンプルを更新するオプションが用意されています。  インポートしたサンプルを更新すると、サンプルおよび関連付けられている資産に加えられた変更が上書きされます。

## <a name="using-mrtk-with-openxr-support"></a>OpenXR サポートでの MRTK の使用

MRTK-Unity では、2.5.3 リリース以降の Mixed Reality OpenXR プラグインがサポートされています。

1. Mixed reality [ツール](welcome-to-mr-feature-tool.md) キットをまだインストールしていない場合は、それをもう一度開きます。 OpenXR のサポートは、 **Foundation** パッケージに含まれています。
2. インスペクターの MixedReality Toolkit コンポーネントスクリプトに移動し、 **DefaultOpenXRConfigurationProfile** プロファイルに切り替えます。

    ![インスペクターの Mixed Reality Toolkit コンポーネントでの MRTK 構成の切り替えのスクリーンショット](images/openxr-img-11.png)

    1. [OpenXR への移行の詳細につい](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)ては、MRTK のドキュメントを参照してください。

> [!NOTE]
> 以前のバージョンの MRTK からアップグレードする場合は、 **Assets/MixedRealityToolkit/link.xml** ファイルに次の行が含まれていることを確認してください。
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> MRTK 2.5.4 以降を使用して開始した場合、この行は既定で追加されます。

## <a name="next-steps"></a>次のステップ

プロジェクトが OpenXR 用に構成され、サンプルにアクセスできるようになったので、OpenXR プラグインで現在サポートされている [機能](openxr-supported-features.md) を確認してください。

## <a name="have-feedback"></a>フィードバックがありますか?

OpenXR は依然として試験的であるため、お客様からのフィードバックをお寄せください。 [](https://aka.ms/unityforums) **Microsoft**  +  **OpenXR** と **HoloLens 2** または **Windows Mixed Reality** でフォーラム投稿にタグを付けて、Unity フォーラムをご覧ください。

## <a name="see-also"></a>関連項目

* [MRTK を使用しないプロジェクトを構成する](configure-unity-project.md)
* [Unity で推奨される設定](recommended-settings-for-unity.md)
* [Unity のパフォーマンスに関する推奨事項](performance-recommendations-for-unity.md#how-to-profile-with-unity)
