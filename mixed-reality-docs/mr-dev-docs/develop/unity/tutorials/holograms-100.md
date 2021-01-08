---
title: MR の基本 100 - Unity の概要
description: HoloLens および Windows Mixed Reality デバイス向けに、初めての基本的な mixed reality "hello world" アプリケーションを作成する方法について説明します。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: mixed reality、Windows Mixed Reality、HoloLens、イマーシブ、vr、mr、はじめに、ホログラム、academy、チュートリアル、Mixed Reality Academy、unity、mixed reality ヘッドセット、Windows Mixed reality ヘッドセット、virtual reality ヘッドセット
ms.openlocfilehash: 7b316314d7aa693e8be9006b2c5578c1bae7e3ff
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006512"
---
# <a name="mr-basics-100-getting-started-with-unity"></a>MR の基本 100:Unity の概要

>[!IMPORTANT]
>Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。  そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。  これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。  これらは、サポートされているデバイス上で継続して動作するように、保守されます。 HoloLens 2 向けには、[新しいチュートリアル シリーズ](mrlearning-base.md)が投稿されています。

このチュートリアルでは、Unity でビルドされた基本的な mixed reality アプリを作成する手順について説明します。

## <a name="device-support"></a>デバイス サポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="../../../hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td>MR の基本 100:Unity の概要</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>前提条件

* 適切な [ツールがインストール](../../install-the-tools.md)された WINDOWS 10 PC。

## <a name="chapter-1---create-a-new-project"></a>章 1-新しいプロジェクトを作成する

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

Unity を使用してアプリをビルドするには、最初にプロジェクトを作成する必要があります。 このプロジェクトはいくつかのフォルダーに整理されています。最も重要なのは、アセットフォルダーです。 これは、Maya、Max 映画4D または Photoshop などのデジタルコンテンツ作成ツールからインポートしたすべてのアセット、Visual Studio で作成したすべてのコード、または任意のコードエディターを使用して作成したすべてのコンテンツを保持するフォルダーで、さらに、エディターでシーン、アニメーション、その他の Unity アセット型を作成するときに Unity によっ

UWP アプリをビルドして展開するために、Unity はプロジェクトを Visual Studio ソリューションとしてエクスポートできます。このソリューションには、必要なすべての資産とコードファイルが含まれます。

1. Unity を開始する
2. **[新規]** を選択します。
3. プロジェクト名を入力してください (例: "MixedRealityIntroduction")
4. プロジェクトを保存する場所を入力してください
5. **3d** の切り替えが選択されていることを確認する
6. [**プロジェクトの作成**] の選択

おめでとう、すべての設定が完了したら、今すぐに mixed reality カスタマイズを開始できます。

## <a name="chapter-2---setup-the-camera"></a>Chapter 2-カメラの設定

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

Unity のメインカメラは、ヘッドの追跡とステレオスコピックのレンダリングを処理します。 メインカメラには、mixed reality と共に使用するためのいくつかの変更が加えられています。

1. ファイル > 新しいシーンの選択

まず、ユーザーの開始位置を (**X**: 0, **Y**: 0, **Z**: 0) と考えると、アプリのレイアウトが簡単になります。 メインカメラはユーザーのヘッドの移動を追跡しているため、ユーザーの開始位置を設定することによって、メインカメラの開始位置を設定できます。

1. [**階層**] パネルの [**メインカメラ**] を選択します。
2. [ **インスペクター** ] パネルで **変換** コンポーネントを見つけ、 **位置** を (**x**: 0, **y**: 1, **z**:-10) から (**x**: 0, **y**: 0, **z**: 0) に変更します。

次に、カメラの既定の背景はいくつかの点を考慮する必要があります。

**HoloLens アプリケーションの** 場合、実際の世界は、スカイボックステクスチャではなく、カメラがレンダリングするすべての要素の背後に表示されます。

1. **メインカメラ** が [**階層**] パネルで選択された状態で、[**インスペクター** ] パネルの [**カメラ**] コンポーネントを見つけて、[**クリアフラグ**] ボックスを [**スカイ** ボックス] から [**純色**] に変更します。
2. **背景** 色ピッカーを選択し、 **RGBA** 値を (0, 0, 0, 0) に変更します。

**イマーシブヘッドセットを対象とする mixed reality アプリケーション** では、Unity が提供する既定のスカイボックステクスチャを使用できます。

1. **メインカメラ** を [**階層**] パネルで選択した状態で、[**インスペクター** ] パネルの [**カメラ**] コンポーネントを見つけて、[**フラグのクリア**] ドロップダウンを [**スカイ** ボックス] にします。

3番目の方法として、Unity の近くのクリッププレーンを考えて、ユーザーがオブジェクトまたはオブジェクトにアプローチしているときに、ユーザーに近いオブジェクトが表示されないようにします。

**Hololens アプリケーション** では、near クリッププレーンを [hololens 推奨](../camera-in-unity.md#clip-planes) 0.85 メーターに設定できます。

1. **メインカメラ** を [**階層**] パネルで選択した状態で、[**インスペクター** ] パネルの [**カメラ**] コンポーネントを見つけて、[**近距離クリップ平面**] フィールドを既定の **0.3** から HoloLens 推奨 **0.85** に変更します。

**イマーシブヘッドセットを対象とする mixed reality アプリケーション** では、Unity が提供する既定の設定を使用できます。

1. **メインカメラ** を [**階層**] パネルで選択した状態で、[**インスペクター** ] パネルの [**カメラ**] コンポーネントを見つけて、[**近くのクリッププレーン**] フィールドを既定の **0.3** にします。

最後に、ここまでの進行状況を保存しておきます。 シーンの変更を保存するには、> [名前を付け **てシーンを保存**] を選択し、シーンに「 **Main**」という名前を付けて、[ **保存**] を選択します。

## <a name="chapter-3---setup-the-project-settings"></a>Chapter 3-プロジェクト設定のセットアップ

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

この章では、開発用に Windows Holographic SDK を対象とするのに役立つ Unity プロジェクト設定をいくつか設定します。 また、アプリケーションの品質設定をいくつか設定します。 最後に、ビルドターゲットがユニバーサル Windows プラットフォームに設定されていることを確認します。

### <a name="unity-performance-and-quality-settings"></a>Unity のパフォーマンスと品質の設定

**HoloLens の Unity 品質設定**

![HoloLens の Unity 品質設定](images/qualitysettings.png)

HoloLens で高フレームレートを維持することは非常に重要であるため、品質設定をチューニングしてパフォーマンスを最速にすることをお勧めします。 詳細については、「 [Unity のパフォーマンスに関する推奨事項](../performance-recommendations-for-unity.md)」を参照してください。

1. [**プロジェクト設定の編集 > の > 品質**] を選択します。
2. **ユニバーサル Windows プラットフォーム** ロゴの下にある **ドロップダウン** を選択し、[**非常に低い**] を選択します。 ユニバーサル Windows プラットフォーム列のボックスと **非常に少ない** 行が緑色になっている場合は、設定が正しく適用されていることがわかります。

**Occluded を対象とする mixed reality アプリケーションで** は、品質設定を既定値のままにすることができます。

### <a name="target-windows-10-sdk"></a>ターゲット Windows 10 SDK

**ターゲット Windows Holographic SDK**

![ターゲット Windows Holographic SDK](../images/xrsettings.png)

エクスポートしようとしているアプリが2D ビューではなく [イマーシブビュー](../../../design/app-views.md) を作成する必要があることを Unity に知らせる必要があります。 これを行うには、Windows 10 SDK を対象とする Unity で仮想現実のサポートを有効にします。

1. [ **Edit > Project Settings > Player**] にアクセスします。
2. [プレーヤー設定] の [ **インスペクター] パネル** で、[ **ユニバーサル Windows プラットフォーム** ] アイコンを選択します。
3. **[XR Settings]\(XR 設定\)** グループを展開します。
4. **[Rendering]\(レンダリング\)** セクションで、 **[Virtual Reality Supported]\(バーチャル リアリティ サポート\)** チェック ボックスをオンにして、新しい **バーチャル リアリティ SDK** の一覧を追加します。
5. **[Windows Mixed Reality]** が一覧に表示されていることを確認します。 されていない場合は、一覧の下部にある **[+]** ボタンを選択し、 **[Windows Mixed Reality]** を選択します。

>[!NOTE]
>**ユニバーサル Windows プラットフォーム** アイコンが表示されない場合は、インストール時にユニバーサル Windows プラットフォームビルドサポートが選択されていることを確認してください。 していない場合は、適切な Windows インストールを使用して、Unity を再インストールする必要があります。

適用されたすべてのプロジェクト設定を取得するためのすばらしいジョブ。 次に、ホログラムを追加してみましょう。

## <a name="chapter-4---create-a-cube"></a>Chapter 4-キューブの作成

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

Unity プロジェクトでのキューブの作成は、Unity で他のオブジェクトを作成するのと同じです。 Unity の座標系は現実世界にマップされているため、ユーザーの前にキューブを配置するのは簡単です。 Unity の1つのメーターは実際の世界では約1メートルです。

1. **階層** パネルの左上隅にある [**作成**] ドロップダウンを選択し、[ **3d オブジェクト > キューブ**] を選択します。
2. [**階層**] パネルで、新しく作成した **キューブ** を選択します。
3. **インスペクター** で **変換** コンポーネントを検索し、**位置** を (**X**: 0、 **Y**: 0、 **Z**: 2) に変更します。 *これにより、ユーザーの開始位置の前にキューブ2のメーターが配置されます。*
4. **変換** コンポーネントで、**ローテーション** を (**x**:45、 **y**:45、 **z**:45) に変更し、**スケール** を (**x**: 0.25、 **y**: 0.25、 **z**: 0.25) に変更します。 *これにより、キューブが0.25 メートルにスケールされます。*
5. シーンの変更を保存するには、[ **ファイル > [シーンの保存**] を選択します。

## <a name="chapter-5---verify-on-device-from-unity-editor"></a>章 5-Unity エディターからデバイスを確認する

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

キューブを作成したので、デバイスのクイックチェックを実行します。 これは、Unity エディター内から直接行うことができます。

### <a name="initial-setup"></a>初期セットアップ

1. 開発用 PC の Unity で、[ **ファイル > ビルドの設定** ] ウィンドウを開きます。
2. **プラットフォーム** を **ユニバーサル Windows プラットフォーム** に変更し、[**プラットフォームの切り替え**] をクリックします。

### <a name="for-hololens-use-unity-remoting"></a>HoloLens で Unity リモート処理を使用する

1. HoloLens で、Windows ストアから入手できる [Holographic リモート処理プレーヤー](../../platform-capabilities-and-apis/holographic-remoting-player.md)をインストールして実行します。 デバイスでアプリケーションを起動すると、待機状態になり、デバイスの IP アドレスが表示されます。 IP を書き留めます。
2. **ウィンドウ > XR > Holographic エミュレーション]** を開きます。
3. [ **エミュレーションモード** ] を **[なし** ] から [リモート] から [ **デバイス**] に変更します。
4. [ **リモートコンピューター**] に、前にメモした HOLOLENS の IP アドレスを入力します。
5. **[Connect]** をクリックします。
6. 接続の **状態** が緑色に変わっ **ていること** を確認します。
7. これで、Unity エディターで [ **再生** ] をクリックできるようになりました。

これで、デバイスとエディターでキューブを表示できるようになります。 エディターでアプリを実行するのと同じように、一時停止、検査、およびデバッグを行うことができます。これは、アプリケーションをエディターで実行するのと同じです。ただし、これは基本的には、ホストコンピューターとデバイス間のネットワーク間で送受信されるビデオ、オーディオ、デバイスの入力を使用します。

### <a name="for-other-mixed-reality-supported-headsets"></a>その他の mixed reality がサポートするヘッドセットの場合

1. USB ケーブルと HDMI またはディスプレイポートケーブルを使用して、ヘッドセットを開発用 PC に接続します。
2. **Mixed Reality ポータル** を起動し、最初の実行エクスペリエンスを完了していることを確認します。
3. Unity から、再生ボタンを押すことができます。

これで、混合現実のヘッドセットとエディターでキューブのレンダリングを確認できるようになります。

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a>第6章-Visual Studio からデバイスへのビルドと配置

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

これで、プロジェクトを Visual Studio にコンパイルし、ターゲットデバイスにデプロイする準備ができました。

### <a name="export-to-the-visual-studio-solution"></a>Visual Studio ソリューションへのエクスポート

1. [ **ビルドの設定] ウィンドウ > ファイル** を開きます。
1. シーンを追加するには、[開いている **シーンの追加** ] をクリックします。
1. [ **プラットフォーム** ] を [ **ユニバーサル Windows プラットフォーム** に変更し、[ **プラットフォームの切り替え**] をクリックします。
1. **ユニバーサル Windows プラットフォーム** 設定で、 **SDK** が **Universal 10** であることを確認します。
1. ターゲットデバイスの場合は、occluded の **任意のデバイス** に表示するか、または **HoloLens** に切り替えます。
1. **UWP ビルドの種類** は **D3D** である必要があります。
1. **UWP SDK** は、 **インストールされている最新** の状態のままにすることができます。
1. [**ビルド**] をクリックします。
1. エクスプローラーで、[ **新しいフォルダー** ] をクリックし、フォルダーに **「App」** という名前を指定します。
1. **アプリ** フォルダーを選択した状態で、[**フォルダーの選択**] ボタンをクリックします。
1. Unity のビルドが完了すると、Windows エクスプローラーウィンドウが表示されます。
1. エクスプローラーで **アプリ** フォルダーを開きます。
1. 生成された Visual Studio ソリューションを開きます (この例では MixedRealityIntroduction)。

### <a name="compile-the-visual-studio-solution"></a>Visual Studio ソリューションをコンパイルする

最後に、エクスポートされた Visual Studio ソリューションをコンパイルしてデプロイし、デバイスで試します。

1. Visual Studio の上部のツールバーを使用して、ターゲットを **デバッグ** から **リリース** に変更し、 **ARM** から **X86** に変更します。

この手順は、デバイスとエミュレーターの間の配置で異なります。 セットアップに一致する指示に従います。

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a>Wi-Fi 経由で mixed reality デバイスにデプロイする

1. [ **ローカルコンピューター** ] ボタンの横にある矢印をクリックし、[配置ターゲット] を [ **リモートコンピューター**] に変更します。
2. Mixed reality デバイスの IP アドレスを入力し、HoloLens と **Windows** で他のデバイスの **認証モード** を Universal (暗号化されていないプロトコル) に変更します。
3. [ **デバッグ > デバッグなしで開始**] をクリックします。

**HoloLens の** 場合、初めてデバイスをデプロイする場合は、 [Visual Studio を使用して](../../platform-capabilities-and-apis/using-visual-studio.md)ペアリングする必要があります。

### <a name="deploy-to-mixed-reality-device-over-usb"></a>USB 経由で mixed reality デバイスに展開する

デバイスが USB ケーブル経由で接続されていることを確認します。

1. **HoloLens の** 場合は、[ **ローカルコンピューター** ] ボタンの横にある矢印をクリックし、展開ターゲットを [ **デバイス**] に変更します。
2. **PC に接続されている occluded デバイスを対象に** するには、設定をローカルコンピューターに保持します。 **Mixed Reality ポータル** が実行されていることを確認します。
3. [ **デバッグ > デバッグなしで開始**] をクリックします。

### <a name="deploy-to-emulator"></a>Emulator に配置

1. **デバイス** ボタンの横にある矢印をクリックし、ドロップダウンから [ **HoloLens Emulator**] を選択します。
2. [ **デバッグ > デバッグなしで開始**] をクリックします。

### <a name="try-out-your-app"></a>アプリを試してみる

アプリがデプロイされたので、キューブ全体を移動して、その前に世界中の状態が維持されることを確認します。

## <a name="see-also"></a>関連項目

* [Unity 開発の概要](../unity-development-overview.md)
* [Unity と Visual Studio を使用するためのベスト プラクティス](../best-practices-for-working-with-unity-and-visual-studio.md)
* [MR の基本 101](holograms-101.md)
* [MR の基本 101E](holograms-101e.md)
