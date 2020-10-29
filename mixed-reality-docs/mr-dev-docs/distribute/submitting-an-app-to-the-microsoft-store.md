---
title: Microsoft Store へのアプリの送信
description: この記事では、アプリのパッケージ化とテストの方法や、証明書を渡してストア内のアプリを見つけやすくするためのヒントなど、Microsoft Store に対して mixed reality アプリを送信する方法についてのヒントを提供します。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: アプリ, uwp, 送信, 送信, フィルター, メタデータ, システム要件, キーワード, wack, 認定, パッケージ, appx, 販売
ms.openlocfilehash: d1b47366831ad46c889002f60dd13f98021a5690
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683050"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>Microsoft Store へのアプリの送信

[HoloLens](../hololens-hardware-details.md)と WINDOWS 10 PC の両方で、[イマーシブヘッドセット](../discover/immersive-headset-hardware-details.md)の電源を入れてユニバーサル Windows プラットフォームアプリを実行します。 HoloLens または PC (またはその両方) をサポートするアプリを送信するかどうかにかかわらず、 [パートナーセンター](https://partner.microsoft.com/dashboard)を通じて Microsoft Store にアプリを送信します。

パートナーセンターの開発者アカウントをまだお持ちでない場合は、 [今すぐサインアップ](https://developer.microsoft.com/store/register)できます。

## <a name="packaging-a-mixed-reality-app"></a>Mixed reality アプリのパッケージ化

### <a name="prepare-image-assets-included-in-the-appx"></a>Appx に含まれるイメージ資産を準備する

Appx 作成ツールでは、ストアに送信するためにアプリケーションを appx パッケージに組み込むために必要なイメージ資産がいくつかあります。 [タイルとアイコン資産のガイドラインの](https://msdn.microsoft.com/library/windows/apps/mt412102.aspx)詳細については、MSDN を参照してください。

| 必要な資産 | 推奨される小数点以下桁数 | イメージ形式 | これはどこに表示されますか。 | 
|----------|----------|----------|------------------|
| 71x71 正方形の正方形のロゴ | Any |  PNG | 該当なし | 
| 150x150 正方形の正方形のロゴ | 150x150 正方形 (100% scale) または 225x225 (150% scale) | PNG | 開始 pin とすべてのアプリ (310x310 のが提供されていない場合)、ストア検索候補、ストアリストページ、ストア参照、ストア検索 | 
|  310x150 ワイドのワイドロゴ |  Any  |  PNG  |  該当なし | 
|  ストア ロゴ |  75 x 75 (150% スケール)  |  PNG  |  パートナーセンター, レポートアプリ, レビューの作成, マイライブラリ | 
|  スプラッシュ スクリーン |  930x450 (150% scale)  |  PNG  |  2D アプリランチャー (スレート) | 

また、HoloLens で利用できる推奨資産もいくつかあります。

| 推奨資産 | 推奨される小数点以下桁数 | これはどこに表示されますか。 | 
|----------|----------|----------|
|  310x310 のの正方形のロゴ |  310x310 の (150% scale) |  開始 pin とすべてのアプリ | 

### <a name="live-tile-requirements"></a>ライブタイルの要件

HoloLens の [スタート] メニューには、付属の最大の正方形タイル画像が使用されます。

Microsoft によって発行された一部のアプリには、アプリケーション用の3D ランチャーがあることがわかります。 開発者は、 [これらの手順](implementing-3d-app-launchers.md)に従って、アプリの3d ランチャーを追加できます。

### <a name="specifying-target-and-minimum-version-of-windows"></a>Windows のターゲットと最小バージョンを指定する

Mixed reality アプリに特定のバージョンの Windows に固有の機能が含まれている場合は、ユニバーサル Windows アプリケーションでサポートされるターゲットと最小プラットフォームのバージョンを指定することが重要です。

**これは、windows 10 の秋の作成者の更新プログラム (10.0) 以上が必要な [Windows Mixed Reality のイマーシブヘッドセット](../discover/immersive-headset-hardware-details.md)を対象とするアプリに特に当てはまります。ビルド 16299) が正常に機能するようにします。**

Visual Studio で新しいユニバーサル Windows プロジェクトを作成するときに、Windows のターゲットと最小バージョンを設定するように求めるメッセージが表示されます。 また、[プロジェクト] メニューの既存のプロジェクトに対してこの設定を変更し、ドロップダウンメニューの下部にある [アプリ名の> プロパティを <する] を選択することもできます。

![Visual Studio 2019 で最小バージョンとターゲットプラットフォームのバージョンを設定する](images/visual-studio-min-version-500px.png)<br>
Visual Studio での最小バージョンとターゲットプラットフォームのバージョンの設定

### <a name="specifying-target-device-families"></a>ターゲットデバイスファミリの指定

Windows Mixed Reality アプリケーション ( [HoloLens](../hololens-hardware-details.md) と [イマーシブヘッドセット](../discover/immersive-headset-hardware-details.md)の両方) はユニバーサル Windows プラットフォームの一部であるため、 [ターゲットデバイスファミリ](https://msdn.microsoft.com/library/windows/apps/dn986903.aspx) が "Windows. Universal" のアプリパッケージは、イマーシブヘッドセットを使用する HoloLens または Windows 10 pc で実行できます。 ただし、アプリケーションマニフェストでターゲットデバイスファミリを指定しないと、意図しない Windows 10 デバイスにアプリが開かれることがあります。 次の手順に従って、目的の Windows 10 デバイスファミリを指定し、 [パートナーセンターでアプリパッケージをアップロードしてストアに送信するときに、正しいデバイスファミリが選択されていることを再確認します。](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

Visual Studio でこのフィールドを設定するには、package.appxmanifest を右クリックして [コードの表示] を選択し、TargetDeviceFamily Name フィールドを見つけます。 既定では、次のようになります。

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

アプリが **hololens** 用に作成されている場合は、"Holographic" のターゲットデバイスファミリを指定することで、hololens にのみインストールされるようにすることができます。 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

アプリが、視線追跡や手作業の追跡など、特定の **HoloLens 2** の機能を必要とする場合は、"Holographic" と MinVersion 10.0.18362.0 のターゲットデバイスファミリを指定することで、windows バージョン18362以降を対象とすることができます。 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.18362.0" MaxVersionTested="10.0.18362.0" />
</Dependencies>
```

アプリが **Windows Mixed reality のイマーシブヘッドセット** 用に作成されている場合は、"10.0.16299.0" というターゲットデバイスファミリを指定することにより、windows 10 のコンピューター (Windows mixed reality の場合に必要) の更新プログラムがインストールされている Windows 10 pc にのみインストールすることができます。

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

最後に、アプリが **HoloLens と Windows Mixed Reality** の両方で実行されるように設計されている場合、アプリがこれら2つのデバイスファミリでのみ利用可能であることを確認し、各ターゲットデバイスファミリにそれぞれの MinVersion を含める線を含めることによって、各が適切な最小 Windows バージョンを対象にするようにします。

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

デバイスファミリのターゲット設定の詳細については、 [TARGETDEVICEFAMILY UWP のドキュメント](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily)を参照してください。

### <a name="associate-app-with-the-store"></a>アプリをストアと関連付ける

Visual Studio ソリューションの [プロジェクト] メニューで、[ストア > アプリケーションをストアと関連付ける] を選択します。 これを行うと、アプリでの購入や通知のシナリオをテストできます。 アプリをストアに関連付けると、ローカルコンピューター上の現在のプロジェクトのアプリマニフェストファイルにこれらの値がダウンロードされます。
* パッケージ表示名
* パッケージ名
* パブリッシャー ID
* 発行者表示名
* Version

マニフェストのカスタム .xml ファイルを作成し、既定の package.appxmanifest ファイルをオーバーライドした場合は、ストアにアプリを関連付けることはできません。 カスタム マニフェスト ファイルをストアに関連付けようとすると、エラー メッセージが表示されます。

### <a name="creating-an-upload-package"></a>アップロードパッケージの作成

[Windows 10 用のユニバーサル windows アプリのパッケージ化](https://msdn.microsoft.com/library/hh454036.aspx#Anchor_2)に関するガイドラインに従ってください。

アップロードパッケージを作成する最後の手順は、 [Windows アプリ認定キット](#windows-app-certification-kit)を使用してパッケージを検証することです。

HoloLens 専用のパッケージを、他の Windows 10 デバイスファミリで使用可能な既存の製品に追加する場合は、 [特定の顧客に配布されるパッケージにバージョン番号がどのように影響](https://msdn.microsoft.com/library/windows/apps/mt188602.aspx)するか、および [パッケージを異なるオペレーティングシステムに配布する方法](https://msdn.microsoft.com/library/windows/apps/mt188601.aspx)についても説明します。

一般的なガイダンスとして、デバイスに適用可能な最も高いバージョン番号のパッケージがストアによって配布されます。

Windows のユニバーサルパッケージと Holographic パッケージがあり、Windows のユニバーサルパッケージのバージョン番号が高い場合、HoloLens ユーザーは Holographic パッケージではなく、より新しいバージョンの Windows. ユニバーサルパッケージをダウンロードします。 この問題には複数の解決方法があります。
1. Holographic などのプラットフォーム固有のパッケージが、Windows などのプラットフォームに依存しないパッケージよりも常に高いバージョン番号を持っていることを確認します。
2. アプリを Windows. Universal としてパッケージ化しないでください。プラットフォーム固有のパッケージがある場合は、代わりに、使用可能な特定のプラットフォーム用に Windows のユニバーサルパッケージをパッケージ化します。

>[!NOTE]
> HoloLens (第1世代) と HoloLen 2 の両方でアプリをサポートするには、2つのアプリパッケージをアップロードする必要があります。1つは、x86 for HoloLens (第1世代)、もう1つは ARM または ARM64 for HoloLens 2 を含んでいます。 
> 
> パッケージに ARM と ARM64 の両方を含めると、ARM64 のバージョンが HoloLens 2 で使用されます。 

>[!NOTE]
> 1つのパッケージを複数のターゲットデバイスファミリに適用するように宣言できます。

3. すべてのプラットフォームで動作する単一の Windows ユニバーサルパッケージを作成します。 これは今でもサポートされていないため、上記の解決策をお勧めします。

## <a name="testing-your-app"></a>アプリケーションのテスト

### <a name="windows-app-certification-kit"></a>Windows アプリ認定キット

Visual Studio を使用してパートナーセンターに送信するアプリパッケージを作成すると、アプリパッケージの作成ウィザードによって、作成されたパッケージに対して Windows アプリ認定キットを実行するように求められます。 ストアへのスムーズな送信プロセスを行うには、 [Windows アプリ認定キットのテスト](https://msdn.microsoft.com/library/windows/apps/jj657973.aspx) がローカルコンピューター上のアプリに対して成功することを確認してから、ストアに送信することをお勧めします。 リモート HoloLens で Windows アプリ認定キットを実行することは現在サポートされていません。

### <a name="run-on-all-targeted-device-families"></a>すべての対象デバイスファミリで実行する

Windows ユニバーサルプラットフォームを使用すると、すべての Windows 10 デバイスファミリで実行される1つのアプリケーションを作成できます。 ただし、ユニバーサル Windows アプリがすべてのデバイスファミリで動作することは保証されていません。 アプリを HoloLens または他の Windows 10 ターゲットデバイスファミリで使用できるようにする前に、これらの各デバイスファミリで [アプリをテスト](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md) して、適切なエクスペリエンスを確保することが重要です。

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>Mixed reality アプリをストアに送信する

Unity プロジェクトに基づく mixed reality アプリを送信する場合は、まずこの [ビデオ](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) を参照してください。

一般に、HoloLens やイマーシブヘッドセットで動作する Windows Mixed Reality アプリを送信するのは、Microsoft Store に UWP アプリを送信するのと同じです。 [名前を予約してアプリを作成](https://docs.microsoft.com/windows/uwp/publish/create-your-app-by-reserving-a-name)したら、 [UWP 送信チェックリスト](https://docs.microsoft.com/windows/uwp/publish/app-submissions)に従う必要があります。

最初の手順の1つとして、mixed reality エクスペリエンスの [カテゴリとサブカテゴリを選択し](https://docs.microsoft.com/windows/uwp/publish/category-and-subcategory-table) ます。 **アプリに最も正確なカテゴリを選択** して、適切なストアのカテゴリにアプリケーションを販売し、関連する検索クエリを使用して表示できるようにすることが重要です。 **VR タイトルをゲームとして一覧表示しても、アプリの露出が向上することはありません** 。これにより、より多くの調整が行われ、混雑が少なくなるカテゴリに表示されなくなる可能性があります。

ただし、発行プロセスには、次の4つの重要な領域があります。これにより、現実的に固有の選択を行うことができます。
1. [ [プロパティ](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)] の [ **[Product 宣言](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** ] セクションを参照してください。
2. [ [プロパティ](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)] の [ **[システム要件](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** ] セクションを参照してください。
3. [ [パッケージ](https://docs.microsoft.com/windows/uwp/publish/upload-app-packages)] の [ **[デバイスファミリの可用性](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** ] セクションを参照してください。
4. いくつかの **[ストアの一覧ページ](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** のフィールド。

### <a name="mixed-reality-product-declarations"></a>Mixed reality 製品宣言

アプリの送信プロセスの [ **[プロパティ](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** ] ページでは、[ **[製品宣言](https://docs.microsoft.com/windows/uwp/publish/app-declarations)** ] セクションで mixed reality に関連するいくつかのオプションを確認できます。

![Mixed reality 製品宣言](images/product-declarations-900px.png)<br>
Mixed reality 製品宣言

まず、アプリが mixed reality エクスペリエンスを提供するデバイスの種類を特定します。 これにより、アプリがストアの Windows Mixed Reality コレクションに含まれ、イマーシブヘッドセットを接続した後 (または HoloLens でストアを参照している場合)、ストアを閲覧しているユーザーに表示されるようになります。

"このエクスペリエンスは、次のような Windows Mixed Reality 向けに設計されています"
* ユーザーの PC にイマーシブヘッドセットが接続されている場合に、アプリが VR エクスペリエンスを提供する場合にのみ、[ **PC** ] ボックスをオンにします。 このボックスをオンにすると、アプリがイマーシブヘッドセット上でのみ実行されるように設計されているか、ヘッドセットが接続されているときに mixed reality モードやボーナスコンテンツを提供する標準 PC ゲーム/アプリであるかどうかを確認する必要があります。
* Hololens での実行時にアプリが holographic experience を提供する場合にのみ、 **hololens** ボックスをオンにします。
* 両方の種類のデバイスでアプリが mixed reality エクスペリエンスを提供する場合は、 **両方** のチェックボックスをオンにします。

上の [PC] を選択した場合は、"mixed reality セットアップ" (アクティビティレベル) を設定する必要があります。 これは、ユーザーがセットアップ中に境界を定義していないため、イマーシブヘッドセットに接続されている Pc で実行される mixed reality エクスペリエンスにのみ適用されます。
* アプリが、ユーザーが1つの場所にあるという意図を持つように設計されている場合は、[ **装着済み +** 継続] を選択します (たとえば、航空機のコックピットに座っているゲームなど)。
* アプリが、セットアップ時にユーザーが定義した境界内での意図に従って設計されている場合は、[ **すべてのエクスペリエンス** ] を選択します (例としては、サイドバイステップとアヒルによる攻撃の回避策があります)。

### <a name="mixed-reality-system-requirements"></a>Mixed reality システム要件

アプリの送信プロセスの [ **[プロパティ](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** ] ページでは、[ **[システム要件](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties#system-requirements)** ] セクションで mixed reality に関連するいくつかのオプションを確認できます。

![システム要件](images/system-reqs-800px.png)<br>
システム要件

このセクションでは、mixed reality アプリの最小 (必須) ハードウェアと推奨される (オプションの) ハードウェアを識別します。

**入力ハードウェア:**

アプリが **マイク** ( [音声入力](../design/voice-input.md)用)、 **[Xbox コントローラーまたはゲームパッド](../discover/hardware-accessories.md#bluetooth-gamepads)** 、または **[Windows Mixed Reality モーションコントローラー](../design/motion-controllers.md)** をサポートしている場合は、チェックボックスを使用して潜在顧客に通知します。 この情報は、ストアのアプリの製品詳細ページに表示され、アプリが適切なアプリ/ゲームコレクションに含まれるようにします (たとえば、モーションコントローラーをサポートするすべてのゲームにコレクションが存在する場合があります)。

入力の種類については、[ハードウェアの最小値] または [推奨されるハードウェア] のチェックボックスをオンにすることをお勧めします。 

次に例を示します。 
* ゲームにモーションコントローラーが必要で、マイクを使用して音声入力を受け入れる場合は、[Windows Mixed Reality motion controller] の横にある [最小ハードウェア] チェックボックスをオンにします。ただし、[マイク] の横にある [推奨されるハードウェア] チェックボックスをオンにします。 
* Xbox コントローラー/ゲームパッドまたはモーションコントローラーを使用してゲームをプレイできる場合は、"Xbox コントローラーまたはゲームパッド" の横にある [最小ハードウェア] チェックボックスをオンにし、[Windows Mixed Reality motion controller] の横にある [推奨されるハードウェア] チェックボックスをオンにします。

**Windows Mixed Reality イマーシブヘッドセット:**

アプリを使用するためにイマーシブヘッドセットが必要かどうか、またはオプションであるかどうかを示すことは、お客様の満足度と教育に不可欠です。

アプリをイマーシブヘッドセットで *のみ* 使用できる場合は、[Windows Mixed Reality イマーシブヘッドセット] の横にある [最小ハードウェア] チェックボックスをオンにします。 これは、アプリの製品詳細ページの [購入] ボタンの上に警告として表示されます。これにより、お客様は、従来のデスクトップアプリのように、PC で動作するアプリを購入しているとは考えられません。

アプリが従来の PC アプリのようなデスクトップで実行されていても、イマーシブヘッドセットが接続されているときに VR エクスペリエンスが提供されている場合 (アプリの完全なコンテンツを利用できるか、一部のみ)、"Windows Mixed Reality イマーシブヘッドセット" の横にある [推奨ハードウェア] チェックボックスをオンにします。 アプリがイマーシブヘッドセットが接続されていない従来のデスクトップアプリとして機能している場合、アプリの製品詳細ページの [購入] ボタンの上に警告は表示されません。

**PC 仕様:**

アプリが、可能な限り多くの Windows Mixed Reality イマーシブヘッドセットユーザーにリーチできるようにするには、統合され[たグラフィックスを使用して Windows Mixed Reality pc](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)の pc 仕様を[ターゲット](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)にする必要があります。

Mixed reality アプリが Windows Mixed Reality PC の最小要件を対象とするか、特定の PC 構成 ( [Windows Mixed Reality ウルトラ pc](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)の専用 GPU など) を必要とするかにかかわらず、関連する pc 仕様が "最小ハードウェア" 列にあることを示す必要があります。

Mixed reality アプリが、より優れたパフォーマンスを発揮するように設計されている場合や、高解像度のグラフィックスを提供している場合は、特定の PC 構成またはグラフィックスカードで、関連する PC 仕様を [推奨されるハードウェア] 列に指定する必要があります。

これは、混合 reality アプリが PC に接続されたイマーシブヘッドセットを使用している場合にのみ適用されます。 Mixed reality アプリが HoloLens でのみ実行される場合、HoloLens にはハードウェア構成が1つしかないという PC 仕様を示す必要はありません。

### <a name="device-family-availability"></a>デバイス ファミリの利用可否

Visual Studio で [アプリを正しくパッケージ化](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) した場合は、アプリの送信プロセスの [パッケージ] ページでアップロードすることで、アプリが使用可能になるデバイスファミリを識別するテーブルを作成する必要があります。

![デバイスファミリの可用性テーブル](images/device-family-table-900px.png)<br>
デバイスファミリの可用性テーブル

混合の現実アプリがイマーシブヘッドセットで動作する場合は、テーブルで少なくとも "Windows 10 Desktop" を選択する必要があります。 Mixed reality アプリが HoloLens で動作する場合は、少なくとも "Windows 10 Holographic" を選択する必要があります。 アプリが Windows Mixed Reality ヘッドセットの種類の両方で実行されている場合は、"Windows 10 Desktop" と "Windows 10 Holographic" の両方を選択する必要があります。

>[!TIP]
>多くの開発者は、パッケージマニフェストと、パートナーセンターでのアプリ/発行者アカウント情報の不一致に関連するアプリのパッケージをアップロードするときに、エラーが発生します。 多くの場合、これらのエラーは、Windows 開発者アカウントに関連付けられているアカウント (パートナーセンターへのサインインに使用するアカウント) を使用して Visual Studio にサインインすることで回避できます。 同じアカウントを使用すると、アプリをパッケージ化する前に、Microsoft Store の id に関連付けることができます。

![アプリを Microsoft Store に関連付ける](images/associate-your-app-700px.png)<br>
Visual Studio でアプリを Microsoft Store に関連付ける

### <a name="store-listing-page"></a>ストアの一覧ページ

アプリ送信プロセスの [ [ストアの一覧](https://docs.microsoft.com/windows/uwp/publish/create-app-store-listings) ] ページでは、いくつかの場所で、mixed reality アプリに関する有用な情報を追加できます。

>[!IMPORTANT]
>アプリがストアによって適切に分類され、Windows Mixed Reality のお客様が検出できるようにするには、アプリの "検索用語" の1つとして **"Windows Mixed reality"** を追加する必要があります ([共有フィールド] セクションを展開すると、検索語句を検索できます)。

![Windows Mixed Reality を検索語句に追加する](images/search-terms-800px.png)<br>
検索語句に "Windows Mixed Reality" を追加する

## <a name="offering-a-free-trial-for-your-game-or-app"></a>ゲームまたはアプリの無料試用版を提供する

Windows Mixed Reality のイマーシブヘッドセットを購入する前に、多くのコンシューマーが仮想現実についてはあまり経験がありません。 これらのユーザーは、大量のゲームで期待されることを認識していない可能性があります。また、イマーシブエクスペリエンスにおける自分の快適なしきい値についてはあまり詳しくありません。 多くのお客様は、windows [Mixed Reality pc](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)としてバッジされていない pc で、Windows mixed reality イマーシブヘッドセットを試すこともできます。 これらの考慮事項により、有料の混合現実アプリまたはゲームの [無料試用版](https://docs.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#free-trial) の提供を検討することを強くお勧めします。

## <a name="see-also"></a>関連項目
* [複合現実](../discover/mixed-reality.md)
* [開発の概要](../develop/development.md)
* [アプリ ビュー](../design/app-views.md)
* [Mixed Reality のパフォーマンスについて](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Unity のパフォーマンスに関する推奨事項](../develop/unity/performance-recommendations-for-unity.md)
* [HoloLens でアプリをテストする](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md)
* [Windows Mixed Reality の PC ハードウェアの最小互換性ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
