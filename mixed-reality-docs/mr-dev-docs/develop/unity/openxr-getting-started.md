---
title: Unity に Mixed Reality OpenXR プラグインを使用する
description: Unity プロジェクトで Mixed Reality OpenXR プラグインを有効にする方法について説明します。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 拡張現実, 仮想現実, mixed reality ヘッドセット, 学習, チュートリアル, 概要
ms.openlocfilehash: c5d312161b7d0f4f832e8d09dbacf5af700ffd8d
ms.sourcegitcommit: aa29b68603721e909f08f352feed24c65d2e505e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2021
ms.locfileid: "98108887"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a>Unity に Mixed Reality OpenXR プラグインを使用する

Unity バージョン2020.2 以降、Microsoft の Mixed Reality OpenXR プラグインパッケージは、Unity パッケージマネージャー (UPM) を使用して利用できます。

## <a name="prerequisites"></a>前提条件

* Unity 2020.2 以降
* Unity OpenXR plugin 0.1.2 以降
* Visual Studio 2019 以降
* HoloLens 2 アプリの **UWP** プラットフォームサポートを Unity でインストールする

> [!NOTE]
> Windows PC で VR アプリケーションを構築している場合、Mixed Reality OpenXR プラグインは必ずしも必要ではありません。 ただし、HP リバーブ G2 コントローラーのコントローラーマッピングをカスタマイズしている場合、または HoloLens 2 と VR ヘッドセットの両方で動作するアプリを作成する場合は、プラグインをインストールする必要があります。

## <a name="installing-the-mixed-reality-openxr-plugin"></a>Mixed Reality OpenXR プラグインのインストール

混合 Reality OpenXR プラグインを使用する前に、プロジェクトで **OpenXR plugin** と **XR plugin 管理** パッケージをインストールする必要があります。 既にインストールされている場合は、 それ以外の場合、Mixed Reality OpenXR プラグインをインストールすると、依存関係として自動的にインストールされます。

1. Unity エディターで、[ **> プロジェクトの設定の編集] > [パッケージマネージャー** ] の順に移動します。
2. [スコープされた **レジストリ** ] セクションを展開し、次の情報を入力して、[ **保存**] を選択します。
    * **名前** を **Microsoft Mixed Reality** に設定する
    * **URL** をに設定 **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**
    * **スコープ** を mixedreality に設定し **ます。**

3. [**詳細設定**] で、[**プレビューパッケージを有効にする**] を選択します。

![[プロジェクトの設定] で開いている Unity パッケージマネージャーウィンドウのスクリーンショット](images/openxr-img-01.png)

Unity パッケージマネージャーでは、 *manifest.js* という名前のマニフェストファイルを使用して、インストールするパッケージとインストール可能なレジストリを決定します。

> [!IMPORTANT]
> OpenXR は引き続き Unity で試験段階であり、開発者エクスペリエンスを最適化するために作業するため、このプロセスは時間の経過と共に変わる可能性があります。

### <a name="registering-the-mixed-reality-dependency"></a>Mixed Reality 依存関係を登録しています

Microsoft Mixed Reality スコープのレジストリがマニフェストに追加されたら、OpenXR パッケージを指定できます。

OpenXR パッケージを追加するには、次のようにします。

1. 次のようなテキストエディターで **[Projectroot]/パッケージ/manifest.jsを** 開き Visual Studio Code
    1. このページを表示するには、プロジェクトウィンドウの左側のパネルにある [ **パッケージ** ] を右クリックします。 次に、[ **エクスプローラーで表示**] をクリックします。
    ![[プロジェクト] ウィンドウのパッケージ一覧のスクリーンショット](images/packages.png)
1. 次のように、ファイルの *Packages/manifest.js* の dependencies セクションを変更します。

    > [!IMPORTANT]
    > マニフェストファイルには、ここに示されている以上の依存関係がある場合があります。 これらのいずれも削除しないでください。リストに OpenXR 依存関係を追加するだけです。

    ``` json
      "dependencies": {
        "com.microsoft.mixedreality.openxr": "0.1.2",
      }
    ```

1. ファイルを保存し、Unity エディターに戻り、 **パッケージマネージャー** を開いて、プラグインがインストールされていることを確認します。

    ![Mixed Reality OpenXR プラグインが強調表示されている unity エディターで開く Unity パッケージマネージャーのスクリーンショット](images/openxr-img-03.png)

    > [!Note]
    > Unity パッケージマネージャーを使用して OpenXR パッケージを削除した場合は、前に説明した手順を使用して、パッケージを再度追加する必要があります。

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

MRTK Unity では、2.5.3 リリース以降の Mixed Reality OpenXR プラグインがサポートされています。  [Mixed Reality OpenXR プラグインをインストール](#installing-the-mixed-reality-openxr-plugin)するときに設定したものと同じスコープを持つレジストリから、MRTK プラグインをインストールできます。 詳細については、 [Mrtk のドキュメント](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/usingupm.html#registering-the-mixed-reality-component-server)を参照してください。

1. ファイル **の [Projectroot]/パッケージ/manifest.js** に次のパッケージを追加します。

```json
"dependencies": {
    "com.microsoft.mixedreality.toolkit.foundation": "2.5.3",
    "com.microsoft.mixedreality.toolkit.tools": "2.5.3",
    "com.microsoft.mixedreality.toolkit.examples": "2.5.3",
    …
}
```

2. インスペクターの MixedReality Toolkit コンポーネントスクリプトに移動し、 **DefaultOpenXRConfigurationProfile** プロファイルに切り替えます。

![インスペクターの Mixed Reality Toolkit コンポーネントでの MRTK 構成の切り替えのスクリーンショット](images/openxr-img-11.png)

### <a name="known-issues"></a>既知の問題 

ハンドトラッキング機能を使用する場合は、 **Assets/MixedRealityToolkit/link.xml** ファイルに次の行を追加します。

```
<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
```

## <a name="next-steps"></a>次のステップ

プロジェクトが OpenXR 用に構成され、サンプルにアクセスできるようになったので、OpenXR プラグインで現在サポートされている [機能](openxr-supported-features.md) を確認してください。

## <a name="have-feedback"></a>フィードバックがありますか?

OpenXR は依然として試験的であるため、お客様からのフィードバックをお寄せください。 [](https://aka.ms/unityforums) **Microsoft**  +  **OpenXR** と **HoloLens 2** または **Windows Mixed Reality** でフォーラム投稿にタグを付けて、Unity フォーラムをご覧ください。

## <a name="see-also"></a>関連項目

* [MRTK を使用しないプロジェクトを構成する](configure-unity-project.md)
* [Unity で推奨される設定](recommended-settings-for-unity.md)
* [Unity のパフォーマンスに関する推奨事項](performance-recommendations-for-unity.md#how-to-profile-with-unity)
