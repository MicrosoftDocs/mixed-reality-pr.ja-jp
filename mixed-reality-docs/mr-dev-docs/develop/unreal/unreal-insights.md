---
title: Unreal Insights を使用したプロファイリング
description: HoloLens 2 で Unreal Insights を使用する方法について説明します。
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、development、プロファイリング、Unreal insights、documentation、ガイド、features、ホログラム、game development、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット
ms.openlocfilehash: 20e620f147f2cf5ee05073467c8ce7335340d59d
ms.sourcegitcommit: 53bde413a174712cb9d3794d02d96363a2d599cd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2020
ms.locfileid: "97486377"
---
# <a name="profiling-with-unreal-insights"></a>Unreal Insights を使用したプロファイリング 

[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) は、Unreal Engine のデータを収集、分析、視覚化するプロファイルシステムです。 プロファイリングシステムを使用すると、最適化のボトルネックや、アプリのパフォーマンスが向上する可能性のある領域を見つけることができます。 通常は、エディターから Unreal Insights を有効にしますが、HoloLens 2 の場合はコマンドラインを使用する必要があります。  

## <a name="setup"></a>セットアップ

Unreal では、HoloLens ランチャーで "カスタムプロファイル" を作成して構成し、コマンドラインパラメーターを使用して Unreal Insights を有効にすることができます。

1.  コマンドプロンプトで **ipconfig** コマンドを使用して、コンピューターの IP アドレスを検索します。 IP アドレスは、ipconfig によって示される IPv4 アドレスです。 後でコマンドラインパラメーターを設定するときは、この点に注意してください。

> [!IMPORTANT]
> VPN の背後にいる場合は、代わりに VPN 経由で提供される IP アドレスを指定する必要があります。

![Ipconfig コマンドのコマンドラインの結果のスクリーンショット](images/unreal-insights-img-01.png)

2.  Unreal Engine パネルの上部に戻り、[Launch] \ (**起動**\) ボタンの下に **デバイスマネージャー** を開きます。

![デバイスマネージャーが強調表示されている起動オプションのスクリーンショット](images/unreal-insights-img-02.png)

3.  [デバイスマネージャーで、[ **一覧** にないデバイスの追加] を選択します。

![Unreal engine で開かれるデバイスマネージャーのスクリーンショット](images/unreal-insights-img-03.png)

4. [ **プラットフォームの選択** ] をクリックし、[ **HoloLens**] を選択します。

![HoloLens が強調表示された [一覧にないデバイスの追加] ドロップダウンのスクリーンショット](images/unreal-insights-img-04.png)

5.  IPoverUSB を使用している場合は、デバイス Id として 127.0.0.1: 10080 を入力します。 HoloLens のユーザーとパスワードをそれぞれのフィールドに入力し、必要に応じて **表示名** を入力します。

> [!IMPORTANT]
> デバイス Id は HoloLens の IP アドレスであり、手順 1. で見つかった Unreal Insights を実行しているコンピューターではありません。

![デバイスマネージャーでの HoloLens デバイスの詳細のスクリーンショット](images/unreal-insights-img-05.png)

6.  [ **追加** ] を選択すると、デバイスマネージャーのデバイスの一覧に HoloLens が表示されます。

![デバイス一覧に追加された HoloLens のスクリーンショット](images/unreal-insights-img-06.png)

## <a name="launch"></a>Launch

1. [**起動**] ボタンの下にある [UE4] パネルから **プロジェクトランチャー** を開きます。

![プロジェクトランチャーが強調表示されている起動オプションのスクリーンショット](images/unreal-insights-img-07.png)

2. カスタム **+** **起動プロファイル** にカスタムプロファイルを作成するには、このボタンを選択します。 作成した後は、いつでもこのプロファイルを編集できます。

![カスタム起動プロファイルが強調表示されているプロジェクトランチャーのスクリーンショット](images/unreal-insights-img-08.png)

3. HoloLens カスタム起動プロファイルの [ **プロファイルの編集** ] ボタンを選択し、次のように構成します。
    * デバイスへのコピーを有効にするに **は、ブックで**[**クック**] を選択します。
    * [**アーカイブ**] セクションの [アーカイブします **か?** ] をオンにして、削除するのではなく、生成された .appxbundle を保持し、ディスク領域を節約することができます。 .Appxbundle の場所を指定し、必要に応じて開発ビルドに切り替えます。

![書籍と HoloLens が強調表示されているプロファイル構成のクックオプションのスクリーンショット](images/unreal-insights-img-09.png)

4. **ビルドを展開する方法** を設定しますか? [**デバイスにコピー** ] を選択して、UI の **起動** セクションをアクティブにします。

![デバイスへのコピーが強調表示されている配置オプションを使用したプロジェクトランチャーのスクリーンショット](images/unreal-insights-img-10.png)

5. [**起動**] セクションで、**追加のコマンドラインパラメーター** を設定します。 パラメーターは ue4commandline.txt ファイルに書き込まれ、バンドルにパッケージ化されて、起動時に使用されます。 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * 次のことを試してみてください。 **-tracehost = IP_OF_YOUR_PC-trace = Log、Bookmark、Frame、CPU、GPU、LoadTime、File、Net**
    * 使用可能な起動パラメーターの完全な一覧については、 [Unreal Insights のリファレンスドキュメントを参照](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html)してください。

> [!NOTE]
> "IP_OF_YOUR_PC" は、手順 1. で見つかった IP アドレスです。 これは、HoloLens の IP アドレスではなく、Unreal Insights を実行しているコンピューターの IP アドレスです。

> [!IMPORTANT]
> トレースが非常に高速になります。 トレースサイズを低く保つために必要なチャネルのみを有効にします。

![起動構成オプションのスクリーンショット](images/unreal-insights-img-11.png)

6. アプリを起動する前に、Unreal insights を起動します。そうしないと、アプリの前に実際の情報を適切に初期化できません。
    * Unreal Insights の実行可能ファイルは、通常は次のように、バイナリエンジンフォルダーに格納されます。 "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"

![実行中の unreal insights 実行可能ファイルのスクリーンショット](images/unreal-insights-img-12.png)

6.  [ **戻る** ] を選択して、 **プロジェクトランチャー** ダイアログのルートに戻ります。
7.  エディターに戻り、カスタム起動プロファイルで [ **起動** ] をクリックします。

![カスタム起動プロファイルのスクリーンショット](images/unreal-insights-img-13.png)

8.  プロジェクトがパッケージ化され、デバイスにインストールされ、起動します。

## <a name="profiling"></a>プロファイル

Unreal Insights に戻り、デバイスへの **ライブ** 接続を選択してプロファイリングを開始します

カスタムプロファイルは、プロジェクト間で共有されます。 ここからは、毎回作成したカスタムプロファイルを使用できます。これを毎回行う必要はありません。 [セットアップセクション](#setup)で手順 3. ~ 6. を実行するたびに、デバイスへの接続を再作成する必要があります。

## <a name="see-also"></a>関連項目
* [Unreal Insights のドキュメント](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

