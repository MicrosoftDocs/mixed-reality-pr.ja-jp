---
title: Microsoft Store へのアプリの送信
description: Microsoft Store に対して、混在する現実のアプリをパッケージ化、テスト、および送信するプロセスについて説明します。
author: hferrone
ms.author: mazeller
ms.date: 11/13/2020
ms.topic: article
keywords: Microsoft Store, HoloLens, イマーシブヘッドセット, アプリ, uwp, 送信, 送信, フィルター, メタデータ, システム要件, キーワード, wack, 認定, パッケージ, appx, 販売促進
ms.openlocfilehash: f5dae379deee54056595c291363b5b1e3e83f25e
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678791"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>Microsoft Store へのアプリの送信

[HoloLens](../hololens-hardware-details.md)と WINDOWS 10 PC の両方で、[イマーシブヘッドセット](../discover/immersive-headset-hardware-details.md)の電源を入れてユニバーサル Windows プラットフォームアプリを実行します。 HoloLens、PC、またはその両方をサポートするアプリを送信する場合でも、アプリの送信は [パートナーセンター](https://partner.microsoft.com/dashboard)を経由します。

パートナーセンターの開発者アカウントをまだお持ちでない場合は、先に進む前に [サインアップ](https://developer.microsoft.com/store/register) してください。

## <a name="packaging-a-mixed-reality-app"></a>Mixed Reality アプリのパッケージ化

Mixed Reality アプリケーションをパッケージ化するには、次のようないくつかの手順があります。

* すべてのイメージアセットを正しく準備しています
* HoloLens の [スタート] メニューに表示されるタイルイメージの選択
* アプリのターゲットと最小の Windows バージョンを設定する
* アプリの依存関係でターゲットデバイスファミリを設定する
* アプリを Microsoft Store に関連付けるメタデータを追加する
* アップロードパッケージの作成

これらの各送信ステージについては、次のセクションで説明します。最初の送信の試行には参加しないことをお勧めします。

### <a name="prepare-image-assets-included-in-the-appx"></a>Appx に含まれるイメージ資産を準備する

Appx ビルドツールでアプリケーションを appx パッケージに組み込むには、次のイメージ資産が必要です。これは、Microsoft Store に送信するために必要です。 [タイルとアイコン資産のガイドラインの](https://msdn.microsoft.com/library/windows/apps/mt412102.aspx)詳細については、MSDN を参照してください。

| 必要な資産 | 推奨される小数点以下桁数 | イメージ形式 | 資産はどこに表示されますか。 | 
|----------|----------|----------|------------------|
| 71x71 正方形の正方形のロゴ | Any |  PNG | なし | 
| 150x150 正方形の正方形のロゴ | 150x150 正方形 (100% scale) または 225x225 (150% scale) | PNG | 開始 pin とすべてのアプリ (310x310 のが提供されていない場合)、ストア検索候補、ストアリストページ、ストア参照、ストア検索 | 
|  310x150 ワイドのワイドロゴ |  Any  |  PNG  |  なし | 
|  ストア ロゴ |  75 x 75 (150% スケール)  |  PNG  |  パートナーセンター, レポートアプリ, レビューの作成, マイライブラリ | 
|  スプラッシュ スクリーン |  930x450 (150% scale)  |  PNG  |  2D アプリランチャー (スレート) | 

HoloLens 向けに開発している場合は、次のような利点があります。

| 推奨資産 | 推奨される小数点以下桁数 | 資産はどこに表示されますか。 | 
|----------|----------|----------|
|  310x310 のの正方形のロゴ |  310x310 の (150% scale) |  開始 pin とすべてのアプリ | 

### <a name="live-tile-requirements"></a>ライブタイルの要件

HoloLens の [スタート] メニューでは、既定で、含まれる最大の四角形のタイルイメージが使用されます。 Microsoft によって発行されたアプリには、3d [アプリランチャーの実装](implementing-3d-app-launchers.md) 手順に従ってアプリに追加できる、オプションの3d ランチャーが用意されています。

### <a name="specifying-target-and-minimum-version-of-windows"></a>Windows のターゲットと最小バージョンを指定する

Mixed Reality アプリに Windows のバージョンに固有の機能が含まれている場合、サポートされているターゲットと最小プラットフォームのバージョンを指定することが重要です。

**[Windows Mixed Reality のイマーシブヘッドセット](../discover/immersive-headset-hardware-details.md)を対象とするアプリに特に注意を払ってください。少なくとも windows 10 の秋の作成者の更新プログラム (10.0;ビルド 16299) が正常に機能するようにします。**

Visual Studio で新しいユニバーサル Windows プロジェクトを作成するときに、Windows のターゲットと最小バージョンを設定するように求められます。 既存のプロジェクトの場合、この設定を変更するには、ドロップダウンメニューの下部にある [**アプリ名の> のプロパティ**] を選択して、[**プロジェクト**] メニューの [<ます。

![Visual Studio 2019 での最小バージョンとターゲットプラットフォームのバージョンの設定](images/visual-studio-min-version-500px.png)<br>
*Visual Studio での最小バージョンとターゲットプラットフォームのバージョンの設定*

### <a name="specifying-target-device-families"></a>ターゲットデバイスファミリの指定

Windows Mixed Reality アプリケーション ( [HoloLens](../hololens-hardware-details.md)と [イマーシブヘッドセット](../discover/immersive-headset-hardware-details.md)の両方) はユニバーサル Windows プラットフォームの一部であるため、 **windows ユニバーサル**[ターゲットデバイスファミリ](https://msdn.microsoft.com/library/windows/apps/dn986903.aspx)を使用するすべてのアプリパッケージは、イマーシブヘッドセットを使用する HoloLens または windows 10 pc で実行できます。 アプリマニフェストでターゲットデバイスファミリを指定しないと、意図しない Windows 10 デバイスまでアプリを開けないことがあります。 次の手順に従って、目的の Windows 10 デバイスファミリを指定し、 [パートナーセンターでアプリケーションパッケージをアップロードして Microsoft Store 送信するときに、正しいデバイスファミリが設定されていることを再確認します。](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

* Visual Studio でこのフィールドを設定するには、 **package.appxmanifest** を右クリックして [ **コードの表示**] をクリックし、[ **TargetDeviceFamily Name** ] フィールドを探します。 既定では、次のエントリのようになります。

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* **Hololens** アプリを作成している場合は、ターゲットデバイスファミリを **Holographic** に設定することによって、hololens にのみインストールされるようにすることができます。 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* アプリで、視線や手作業の追跡などの **HoloLens 2** 機能が必要な場合は、 **10.0.18362.0 の** Holographic を使用してターゲットデバイスファミリを **windows** に設定することで、windows バージョン18362以上を対象としていることを確認できます。

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.18362.0" MaxVersionTested="10.0.18362.0" />
</Dependencies>
```

* アプリが **Windows Mixed reality のイマーシブヘッドセット** 用に作成されている場合は、ターゲットデバイス **ファミリを 10.0.16299.0** の **MinVersion** で windows に設定することにより、windows 10 pc にインストールされていることを確認できます (windows mixed reality の場合に必要です)。

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

* 最後に、アプリが **HoloLens** と **Windows Mixed Reality** の両方で実行されるように設計されている場合、アプリがこれら2つのデバイスファミリでのみ利用可能であることを確認し、各ターゲットにそれぞれの MinVersion を持つ各ターゲットデバイスファミリの線を含めることにより、各ターゲットの Windows バージョンが正しいことを確認します。

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

デバイスファミリのターゲット設定の詳細については、 [TARGETDEVICEFAMILY UWP のドキュメント](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily)を参照してください。

### <a name="associate-app-with-the-store"></a>アプリをストアと関連付ける

アプリを Microsoft Store に関連付けると、次の値が現在のプロジェクトのローカルアプリマニフェストファイルにダウンロードされます。

* パッケージ表示名
* パッケージ名
* パブリッシャー ID
* 発行者表示名
* Version

独自のカスタム .xml ファイルを使用して既定の package.appxmanifest ファイルをオーバーライドしている場合は、アプリを Microsoft Store に関連付けることはできません。 カスタムマニフェストファイルをストアに関連付けると、エラーメッセージが表示されます。

また、Visual Studio ソリューションに移動し、[プロジェクト > ストア] を選択して **アプリをストア > 関連付ける** ことで、購入および通知のシナリオをテストすることもできます。

### <a name="creating-an-upload-package"></a>アップロードパッケージの作成

[Windows 10 用のユニバーサル windows アプリのパッケージ化](https://msdn.microsoft.com/library/hh454036.aspx#Anchor_2)に関するガイドラインに従ってください。

アップロードパッケージを作成する最後の手順は、 [Windows アプリ認定キット](#windows-app-certification-kit)を使用してパッケージを検証することです。

他の Windows 10 デバイスファミリで使用できる既存の製品に HoloLens 固有のパッケージを追加する場合は、次の点に注意してください。 

* [特定の顧客に配布されるパッケージに、バージョン番号がどのように影響するか](https://msdn.microsoft.com/library/windows/apps/mt188602.aspx)
* [パッケージがさまざまなオペレーティングシステムに配布されるしくみ](https://msdn.microsoft.com/library/windows/apps/mt188601.aspx)

一般的なガイダンスとして、デバイスのバージョン番号が最も大きいパッケージがストアによって配布されていることが挙げられます。

**Windows のユニバーサル** パッケージと **Holographic** パッケージがあり、windows のユニバーサルパッケージのバージョン番号が新しい場合、HoloLens ユーザーは Holographic パッケージではなく、より新しいバージョンの windows. ユニバーサルパッケージをダウンロードすることになります。 

上記のシナリオが探している結果ではない場合、いくつかの利用可能な解決策があります。

* Holographic などのプラットフォーム固有のパッケージが、Windows などのプラットフォームに依存しないパッケージよりも常に高いバージョン番号を持っていることを確認します。
* アプリを Windows. Universal としてパッケージ化しないでください。プラットフォーム固有のパッケージも含まれている場合は、代わりに、使用する特定のプラットフォーム用に Windows のユニバーサルパッケージをパッケージ化してください。
* すべてのプラットフォームで動作する単一の Windows ユニバーサルパッケージを作成します。 このオプションのサポートは現時点では適切ではないため、上記のソリューションをお勧めします。

>[!NOTE]
> HoloLens (第1世代) と HoloLen 2 の両方でアプリをサポートするには、2つのアプリパッケージをアップロードする必要があります。1つは、x86 for HoloLens (第1世代)、もう1つは ARM または ARM64 for HoloLens 2 を含んでいます。 
> 
> パッケージに ARM と ARM64 の両方を含めると、ARM64 のバージョンが HoloLens 2 で使用されます。 

>[!NOTE]
> 1つのパッケージを複数のターゲットデバイスファミリに適用するように宣言できます。

## <a name="testing-your-app"></a>アプリケーションのテスト

### <a name="windows-app-certification-kit"></a>Windows アプリ認定キット

Visual Studio を使用してパートナーセンターに送信するアプリパッケージを作成する場合、アプリパッケージの作成ウィザードでは、作成されたパッケージに対して Windows アプリ認定キットを実行するように求められます。 ストアへのスムーズな送信プロセスを行うには、アプリのローカルコピーが [Windows アプリ認定キットのテスト](https://msdn.microsoft.com/library/windows/apps/jj657973.aspx) に合格してからストアに送信することをお勧めします。 リモート HoloLens で Windows アプリ認定キットを実行することは現在サポートされていません。

### <a name="run-on-all-targeted-device-families"></a>すべての対象デバイスファミリで実行する

Windows ユニバーサルプラットフォームを使用すると、すべての Windows 10 デバイスファミリで実行される1つのアプリケーションを作成できます。 ただし、ユニバーサル Windows アプリがすべてのデバイスファミリで動作することは保証されていません。 選択した各デバイスファミリで [アプリをテスト](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md) して、適切なエクスペリエンスを確保することが重要です。

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>Mixed Reality アプリをストアに送信する

Unity プロジェクトに基づく Mixed Reality アプリを送信する場合は、まずこの [ビデオ](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) を参照してください。

一般に、HoloLens やイマーシブヘッドセットで動作する Windows Mixed Reality アプリを送信するのは、Microsoft Store に UWP アプリを送信するのと同じです。 [名前を予約してアプリを作成](https://docs.microsoft.com/windows/uwp/publish/create-your-app-by-reserving-a-name)したら、 [UWP 送信チェックリスト](https://docs.microsoft.com/windows/uwp/publish/app-submissions)に従います。

最初に行うことの1つは、Mixed Reality エクスペリエンスの [カテゴリとサブカテゴリを選択](https://docs.microsoft.com/windows/uwp/publish/category-and-subcategory-table) することです。 **アプリに最も正確なカテゴリを選択** することが重要です。 カテゴリを使用すると、アプリケーションを適切なストアカテゴリに分類し、関連する検索クエリを使用して表示されるようにすることができます。 **VR タイトルをゲームとして一覧表示すると、アプリの露出が向上しません** 。これにより、より多くの調整が行われ、混雑が少なくなるカテゴリには表示されなくなる可能性があります。

ただし、発行プロセスには、次の4つの重要な領域があります。これにより、現実的に固有の選択を行うことができます。
1. [[プロパティ](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)] の [ **[Product 宣言](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)**] セクションを参照してください。
2. [[プロパティ](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)] の [**[システム要件](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)**] セクションを参照してください。
3. [[パッケージ](https://docs.microsoft.com/windows/uwp/publish/upload-app-packages)] の [**[デバイスファミリの可用性](submitting-an-app-to-the-microsoft-store.md#device-family-availability)**] セクションを参照してください。
4. いくつかの **[ストアの一覧ページ](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** のフィールド。

### <a name="mixed-reality-product-declarations"></a>Mixed Reality 製品宣言

アプリの送信プロセスの [ **[プロパティ](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** ] ページでは、[ **[製品宣言](https://docs.microsoft.com/windows/uwp/publish/app-declarations)** ] セクションで Mixed Reality に関連するいくつかのオプションを確認できます。

![Mixed Reality 製品宣言](images/product-declarations-900px.png)<br>
Mixed Reality 製品宣言

まず、アプリが Mixed Reality エクスペリエンスを提供するデバイスの種類を識別する必要があります。 デバイスの種類を識別することで、アプリがストア内の Windows Mixed Reality コレクションに含まれるようになります。

"このエクスペリエンスは、次のような Windows Mixed Reality 向けに設計されています"
* アプリがユーザーの PC にイマーシブヘッドセットを接続したときに VR エクスペリエンスを提供する場合は、[ **PC** ] チェックボックスをオンにします。 このチェックボックスをオンにすることをお勧めします。アプリがイマーシブヘッドセットで排他的に実行するように設定されているか、または、ヘッドセットが接続されているときに、標準の PC ゲームまたは混合の現実モードやボーナスコンテンツを提供しているアプリか
* Hololens での実行時にアプリが holographic experience を提供する場合にのみ、 **hololens** ボックスをオンにします。
* 両方の種類のデバイスでアプリが Mixed Reality エクスペリエンスを提供する場合は、 **両方** のチェックボックスをオンにします。

上の [PC] を選択した場合は、"Mixed Reality セットアップ" (アクティビティレベル) を設定する必要があります。 これは、ユーザーがセットアップ中に境界を定義していないため、イマーシブヘッドセットに接続されている Pc で実行される Mixed Reality エクスペリエンスにのみ適用されます。
* ユーザーを1つの場所に配置するようにアプリを設計した場合は、[ **固定** ] を選択します。 たとえば、航空機コックピットを制御しているゲームがあるとします。
* セットアップ中に定義されたセットの境界内でユーザーが実行する意図に基づいてアプリが設計されている場合は、[ **すべてのエクスペリエンス** ] を選択します。 たとえば、は、サイドステップとアヒルが攻撃を避けるためのゲームである場合があります。

### <a name="mixed-reality-system-requirements"></a>Mixed Reality システム要件

アプリの送信プロセスの [ **[プロパティ](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** ] ページでは、[ **[システム要件](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties#system-requirements)** ] セクションで Mixed Reality に関連するいくつかのオプションを確認できます。

![システム要件](images/system-reqs-800px.png)<br>
システム要件

このセクションでは、Mixed Reality アプリの最小 (必須) ハードウェアと推奨される (オプションの) ハードウェアを識別します。

**入力ハードウェア:**

アプリケーションで [音声入力](../design/voice-input.md)用の **マイク** がサポートされている場合は、チェックボックスを使用して、潜在顧客に、 **[Xbox コントローラーまたはゲームパッド](../discover/hardware-accessories.md#bluetooth-gamepads)**、または **[Windows Mixed Reality モーションコントローラー](../design/motion-controllers.md)** を指定します。 この情報は、アプリの製品詳細ページにストアに表示され、アプリが適切なアプリ/ゲームコレクションに含まれるようになります。 たとえば、モーションコントローラーをサポートするすべてのゲームにコレクションが存在する場合があります。

入力の種類については、[ハードウェアの最小値] または [推奨されるハードウェア] のチェックボックスをオンにすることをお勧めします。 

次に例を示します。 
* ゲームにモーションコントローラーが必要で、マイクを使用して音声入力を受け入れる場合は、[Windows Mixed Reality motion controller] の横にある [最小ハードウェア] チェックボックスをオンにします。ただし、[マイク] の横にある [推奨されるハードウェア] チェックボックスをオンにします。 
* Xbox コントローラー、ゲームパッド、またはモーションコントローラーを使用してゲームをプレイできる場合は、"Xbox コントローラーまたはゲームパッド" の横にある [最小ハードウェア] チェックボックスをオンにし、[Windows Mixed Reality motion controller] の横にある [推奨されるハードウェア] チェックボックスをオンにします。

**Windows Mixed Reality イマーシブヘッドセット:**

アプリを使用するためにイマーシブヘッドセットが必要かどうか、またはオプションであるかどうかを示すことは、お客様の満足度と教育に不可欠です。

アプリをイマーシブヘッドセットで *のみ* 使用できる場合は、[Windows Mixed Reality イマーシブヘッドセット] の横にある [最小ハードウェア] チェックボックスをオンにします。 これは、アプリの製品詳細ページの [購入] ボタンの上に警告として表示されます。これにより、お客様は、従来のデスクトップアプリのように、PC で動作するアプリを購入しているとは考えられません。

アプリが従来の PC アプリのようなデスクトップで実行されていても、イマーシブヘッドセットが接続されているときに VR エクスペリエンスが提供されている場合 (アプリの完全なコンテンツを利用できるか、一部のみ)、"Windows Mixed Reality イマーシブヘッドセット" の横にある [推奨ハードウェア] チェックボックスをオンにします。 アプリがイマーシブヘッドセットが接続されていない従来のデスクトップアプリとして機能している場合、アプリの製品詳細ページの [購入] ボタンの上に警告は表示されません。

**PC 仕様:**

アプリが、可能な限り多くの Windows Mixed Reality イマーシブヘッドセットユーザーにリーチできるようにするには、統合され[たグラフィックスを使用する Windows Mixed Reality pc](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)の pc 仕様を[対象](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)とします。

Mixed Reality アプリが Windows Mixed Reality PC の最小要件を対象としているか、専用 GPU ([Windows Mixed Reality Ultra PC]) のような特定の PC 構成を必要とするか (の場合)、 https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines 関連する pc 仕様を "最小ハードウェア" 列に追加する必要があります。

混合の現実のアプリがパフォーマンスを向上させるように設計されている場合、または特定の PC 構成またはグラフィックスカードで高解像度のグラフィックスを提供している場合は、関連する PC 仕様を "推奨されるハードウェア" 列に含める必要があります。

これは、混合 Reality アプリが PC に接続されたイマーシブヘッドセットを使用している場合にのみ適用されます。 Mixed Reality アプリが HoloLens でのみ実行される場合、HoloLens にはハードウェア構成が1つしかないという PC 仕様を示す必要はありません。

### <a name="device-family-availability"></a>デバイス ファミリの利用可否

Visual Studio で [アプリを正しくパッケージ化](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) した場合は、[パッケージ] ページでアップロードすると、使用可能なデバイスファミリを含むテーブルが生成されます。

![デバイスファミリの可用性テーブル](images/device-family-table-900px.png)<br>
デバイスファミリの可用性テーブル

混合の現実アプリがイマーシブヘッドセットで動作する場合は、テーブルで少なくとも "Windows 10 Desktop" を選択する必要があります。 Mixed Reality アプリが HoloLens で動作する場合は、少なくとも "Windows 10 Holographic" を選択する必要があります。 アプリが Windows Mixed Reality ヘッドセットの種類の両方で実行されている場合は、"Windows 10 Desktop" と "Windows 10 Holographic" の両方を選択する必要があります。

>[!TIP]
>多くの開発者は、パッケージマニフェストと、パートナーセンターでのアプリ/発行者アカウント情報の不一致に関連するアプリのパッケージをアップロードするときに、エラーが発生します。 多くの場合、これらのエラーは、Windows 開発者アカウントに関連付けられているアカウント (パートナーセンターへのサインインに使用するアカウント) を使用して Visual Studio にサインインすることで回避できます。 同じアカウントを使用すると、アプリをパッケージ化する前に、Microsoft Store の id に関連付けることができます。

![アプリを Microsoft Store に関連付ける](images/associate-your-app-700px.png)<br>
Visual Studio でアプリを Microsoft Store に関連付ける

### <a name="store-listing-page"></a>ストアの一覧ページ

アプリ送信プロセスの [ [ストアの一覧](https://docs.microsoft.com/windows/uwp/publish/create-app-store-listings) ] ページでは、いくつかの場所で、Mixed Reality アプリに関する有用な情報を追加できます。

>[!IMPORTANT]
>アプリがストアによって適切に分類され、Windows Mixed Reality のお客様が検出できるようにするには、アプリの "検索用語" の1つとして **"Windows Mixed reality"** を追加する必要があります ([共有フィールド] セクションを展開すると、検索語句を検索できます)。

![Windows Mixed Reality を検索語句に追加する](images/search-terms-800px.png)<br>
検索語句に "Windows Mixed Reality" を追加する

## <a name="offering-a-free-trial-for-your-game-or-app"></a>ゲームまたはアプリの無料試用版を提供する

多くの場合、コンシューマーは、Windows Mixed Reality のイマーシブヘッドセットを購入する前に、仮想現実の経験がないことに制限されています。 このようなユーザーは、大量のゲームで期待されることを認識していない場合や、イマーシブエクスペリエンスで独自の快適なしきい値を把握していない場合があります。 多くのお客様は、windows [Mixed Reality pc](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)としてバッジされていない pc で、Windows mixed reality イマーシブヘッドセットを試すこともできます。 これらの考慮事項により、有料の混合現実アプリまたはゲームの [無料試用版](https://docs.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#free-trial) の提供を検討することを強くお勧めします。

## <a name="see-also"></a>関連項目
* [Mixed Reality とは](../discover/mixed-reality.md)
* [開発の概要](../develop/development.md)
* [アプリ ビュー](../design/app-views.md)
* [Mixed Reality のパフォーマンスについて](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Unity のパフォーマンスに関する推奨事項](../develop/unity/performance-recommendations-for-unity.md)
* [HoloLens でアプリをテストする](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md)
* [Windows Mixed Reality の PC ハードウェアの最小互換性ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
