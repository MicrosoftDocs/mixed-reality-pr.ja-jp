---
title: Windows Mixed Reality を使用した場所ベースのエンターテインメント
description: 場所に基づくエンターテインメント (ハードウェア、backpack Pc、追跡、構成、サポート) のための Windows Mixed Reality について説明します。
author: jessemcculloch
ms.author: ishitak
ms.date: 08/03/2020
ms.topic: article
keywords: mixed reality、vr、lbe、場所
ms.openlocfilehash: 6ee013a576041a71d92307523dbfbaefa6c7d24a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91690330"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a>Windows Mixed Reality を使用した場所ベースのエンターテインメント

ここ数年で、場所ベースのエンターテインメントカテゴリにおいて非常に多くの成長とイノベーションを促進ました。 テーマの公園や theatres などの従来の会場は、既存のサービスやインストールに対する優れたエクスペリエンスとして、イマーシブ、マルチプレーヤーエクスペリエンスを提供するようになりました。 新しいオペレーターと会場は、一意のマルチ sensorial、マルチプレーヤーエクスペリエンスを、大量に魅力的な価格でもたらします。 これらのすべてのエクスペリエンスでは、mixed reality でできることについて、エンベロープをプッシュしています。

このドキュメントは、[場所ベースのエンターテインメント] カテゴリで Windows Mixed Reality の使用を開始するためのガイドです。 以下のガイダンスは、トレーニング、製品設計、またはその他のユースケースなど、エンターテインメント以外の場所ベースのエクスペリエンスにも適用される場合があります。

## <a name="engineering-faq"></a>エンジニアリングに関する FAQ

### <a name="hardware"></a>ハードウェア

**Q: Microsoft とそのパートナーがセットアップで使用できるハードウェアはどのようなものですか。**

A: Microsoft とその OEM パートナーは、ニーズに応じて選択する、説得力のあるデバイスのポートフォリオを提供します。  

お客様に提供しているエクスペリエンスで仮想現実のヘッドセットが必要な場合は、HP、Samsung、および Acer の次の市場にあるヘッドセットが非常に適しています。 各ヘッドセットには独自の区別された属性があります。 詳細については、以下を参照してください。

HP リバーブ: [詳細](https://hp.com/go/Reverbpro)

Samsung Odyssey +: [Details](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)

Acer: [詳細](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)

お客様の場所が、表示ヘッドセットの使用を必要とする、混合または拡張された現実のエクスペリエンスを専門としている場合は、Microsoft HoloLens 2 を調達することができます。  

HoloLens 2: [注文前の関心](https://www.microsoft.com//hololens/buy)

高度なコンピュータービジョン、音声、および本文の追跡を必要とするエクスペリエンスを試している場合、ニーズに合わせて Azure Kinect DK を見つけることができます。  

Azure Kinect: [詳細](https://azure.microsoft.com//services/kinect-dk/)

**Q: PC-テザリングさ VR エクスペリエンスを実行するために使用できる backpack Pc のポートフォリオは何ですか。**

PC-テザリングさ VR エクスペリエンスの場合、Oem は、ニーズに応じて正確に構築された backpack Pc を非常に優れた選択肢として提供しています。

HP は HP VR backpack G2 を起動しました。これは、無料ローミングエクスペリエンスのために最適化された、現在のところ、RTX 2080 GPU では30% 向上しています。 [詳細](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a>セットアップ

**Q: セットアップを簡単に構成し、LBE 用に Mixed Reality ポータルをカスタマイズするにはどうすればよいですか。**

>[!NOTE]
>この機能には、バージョン2000.19061.1011.0 以上が必要です。  

アプリをキオスクまたはカスタマイズされたエクスペリエンスにデプロイするためにアプリで通常利用できるものよりも、混合の現実ポータルのカスタマイズが必要になる場合があります。 最新の7月の Mixed Reality ポータルの更新では、構成ファイルを使用して次の操作を行うことができるいくつかの詳細設定がサポートされています。  

[失敗したシステムチェックを許可する] –セットアップを完了する前に、セットアッププロセスによって、PC が Windows Mixed Reality との互換性を確認します。 これを回避すると、互換性の問題がある場合に Windows Mixed Reality を実行しようとすると問題が発生する可能性があります。  

デバイスコンパニオンアプリのスキップ– DCA は製造元によって提供されるヘッドセット固有のセットアップ手順を提供し、ヘッドセットのファームウェアを更新できます。  

ルームのセットアップをスキップする–部屋の境界を作成するように求めるメッセージが表示されるのではなく、固定モードまたはスタンバイモードのヘッドセットに直接進むことができます。  

ストアからのアプリのインストールをスキップする-標準セットアップでは、3D ビューアーと Edge 360 ビューアーアドオンを含む、いくつかのストアアプリがインストールされます。 これにより、これらのアプリのインストールはスキップされますが、デバイスの機能が不足している可能性があります。  

全画面表示でプレビューを表示する: 混合 Reality ポータルでは、ヘッドセットが使用されている間、デスクトップ PC に全画面表示でヘッドセットのプレビューが表示されるようになります。  

サイドパネルの [新規] を非表示にします。これにより、Mixed Reality ポータルの起動時にパネルの新しいが拡張されるのを防ぐことができます。  

#### <a name="how-to-configure"></a>構成方法:  

これらの構成のいずれかを設定するには、次 _のディレクトリにUserConfig.js_ という名前のファイルを作成する必要があります: _$env: Localappdata\packages\ Microsoft.MixedReality.Portal_8wekyb3d8bbwe \ localstate \\_

ほとんどのユーザーにとって、これは _C:\Users \<username> \Appdata\local\packages\ Microsoft.mixedreality.portal_8wekyb3d8bbwe \ \\ localstate_ のようになります。

JSON ファイルの内容は、有効にする上記の設定のいずれかに対して "true" が設定されている必要があります。  

```
{

  "shouldAllowFailedSystemChecks": true,

  "shouldSkipDcaApp": true,

  "shouldSkipRoomSetup": true,

  "shouldSkipStoreAppInstall": true,

  "shouldShowPreviewFullScreen": true,

  "shouldHideEngagementPane": true

}
```
 
**Q: playspace の構成についてのガイダンスはありますか。**

A: playspace の構成は、コンシューマーのセットアップエクスペリエンスの場合と同じように行う必要があります。 ルームのセットアッププロセスでは、部屋の境界を定義することもできます。 ルーム境界の構成の詳細については、 [こちら](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)を参照してください。

上のドキュメントで説明したように、最大の適正な1座標の再生領域は5mx5m を中心にしています。 より大きな領域を作成する場合は、Windows Holographic API スタックで空間アンカー機能を使用できます。 この API を使用するには、生成するエクスペリエンスにカスタムエンジニアリングが必要です。  

さまざまな領域サイズに合わせてコンテンツを最適化する方法の詳細については、 [こちら](https://docs.microsoft.com//windows/mixed-reality/coordinate-systems)を参照してください。
 

**Q: 空間が大きすぎて、境界を使用して継続的なエクスペリエンスを設定しようとしたときにエラーが発生しています。大規模な無料のローミングエクスペリエンスを設定するにはどうすればよいですか。**

A: ~ 18xft を超える領域をセットアップする場合、システムによって提供される境界を使用することはできません。  境界システムは、1つの固定座標 "アンカー" を利用することに依存しています。これは、中央のステージアンカーから離れすぎていると不安定になる可能性があります。 

代わりに、"固定" モードを設定できます。このモードでは、境界が表示されず、ステージの境界や再生スペースも構成されません。  次に、物理的な境界領域を参照するように、アプリ内に複数の空間アンカーを構成する必要があります。 

アプリケーション開発者は、ユーザーが物理的な環境と競合しないように、必要なセーフガードを表示する責任があります。  これらは、エクスペリエンス内のデジタル壁面や、カスタマイズされたゲームの境界ビジュアルです。 

WMR を使用したルーム境界の設定に関するガイダンスについては、 [こちら](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)を参照してください。

**Q: playspace の起点はどこですか。**

A: playspace の原点は、セットアップ中にセンターボタンが押されたときに、ルームのセットアップエクスペリエンスによって決定されます。 

### <a name="multi-player-setup"></a>マルチプレーヤーセットアップ

**Q: 自分の会場で、マルチプレーヤーエクスペリエンスをデプロイしています。Windows Mixed Reality ではサポートされていますか。**

A: Windows 20H1 以降のビルド ( [Insider プログラム](https://docs.microsoft.com/windows-insider/at-home/get-started)を使用) を選択した場合は、マップ共有用の新しいインターフェイスにアクセスできます。 この新しい機能は、Windows デバイスポータルの [マップマネージャー](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) インターフェイスを使用して入手できます。 このツールを使用するには、次の手順に従います。
* 20H1 以降を選択していることを確認します (2019 年9月の時点では、Insider プログラムを使用しています)。
* 次の[手順](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-desktop)に従って、Windows デバイスポータル (WDP) を有効にします。
* 既存のマップをダウンロードするか、新しいマップをインポートする Windows Mixed Reality HMD をプラグインします。
* [設定] 画面で指定した URL を使用して、選択したブラウザーの WDP に移動します。
    * その後、"Mixed Reality" セクションに移動し、[マップマネージャー] を選択します。
    * [ダウンロード] ボタンを使用して、コンピューターから既存のマップをエクスポートできるようになりました。
    * [マップファイルのアップロード] ボタンを使用すると、以前のエクスポートからマップをインポートできます (おそらく、別のコンピューターにあります)。
    * "Import" を使用して、システムがこのコンピューター上のこの HMD に対してこのマップを使用できるようにすることができます。

> [!NOTE] 
> 以前は、空間データパッケージャーツールを使用することができましたが、そのツールは当初はサポートされていないものとしてリリースされており、公式に非推奨とされ、20H1 では機能しなくなりました。 代わりに、前に説明したように、受信トレイ [マップマネージャー](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) ツールを使用してください。 

  
### <a name="tracking"></a>追跡

Q: Windows Mixed Reality ヘッドセットの追跡テクノロジはどのように動作しますか。  

Mixed Reality は、HoloLens と同じ追跡テクノロジを共有します。 内部アウト追跡システムの詳細については、 [こちら](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/tracking-system)のドキュメントを参照してください。

上位レベルの空間マッピングシステムの動作の詳細については、 [こちらで](../design/spatial-mapping.md)説明を参照してください。

**Q: reliable tracking ボリュームを取得するためのベストプラクティスはありますか。**

成功を追跡するために環境を最適に構成するには、この [投稿](../environment-considerations-for-hololens.md)のベストプラクティスを読むことができます。

**Q: ウェアハウスでの追跡には特定の差異がありますか? スケールスペースや最適化を検討してください。**

A: 次のプラクティスは、より信頼性の高い追跡ボリュームを取得するのに役立ちます。  

複数の位置で重なり合ったさまざまな機能を部屋に用意することで、追跡システムの堅牢なロックを得ることができます。 単色の輪郭スタイルの線を使用するのではなく、ランダムな描画の splatters と陰影を考えてみましょう。 

可能な場合は、領域内の照明の動的範囲を最小化します。 混合現実 HMDs の追跡カメラは、HDR ではなく、AGC (自動利得) と AEC (自動露出) があるため、さまざまな照明を扱うことができます。 表面光、パターン、およびコントラストの分布によっては、AGC または AEC によって、ほぼすべての白または黒の部屋にいることがわかっている場合があります。これにより、反対の "色" の機能が薄く表示される可能性があります。 明るい日光を持つ外部ウィンドウの前に内部の画像を撮影しようとしているときに、露出を調整して詳細を見ることができるようにした場合、内部のすべてのものは underexposed と黒色になります。 または、内に設定されている場合、以外のすべてが overexposed、すべて白になります。  

トラックカメラの発生が、追跡カメラの AEC/AGC を混乱させる可能性がある場合に、表示される部屋 (オーバーヘッド) にスポットライト。 フラット/拡散照明が役立ちます。  

### <a name="mixed-reality-cloud-services-and-azure"></a>MIXED REALITY クラウドサービスと AZURE 

**Q: どのようにしてビジネススケールを Microsoft Azure できますか。**

A: Azure ベースのオンサイトおよびリモート管理を使用すると、ビジネスをデータ主導にすることができ、運用コストが削減され、既存の場所と新しい場所でのデプロイをスケーリングできます。 Azure Storage、Azure Functions、App Service、Azure ネットワーク、IOT Hub などの azure クラウドサービスは、次のユースケースに役立ちます。  

リモートデバイス展開 & 管理 

リアルタイムのオンサイト分析 

インテリジェントな適応性に優れたゲームプレイ 

LBE コンテンツのストリーミングとデプロイ 

LBE プレーヤーの基本設定ヒートマップ 

LBE 予約と予約システム 

**Q: 空間 MMOG を開発して、大規模なフットプリントをデプロイしています。コンテンツとオブジェクトの永続化を管理するのに役立つすべてのサービス**

A: Azure 空間アンカーは、HoloLens、iOS、および Android デバイスで、複数のユーザーに対応し、空間的に対応した mixed reality エクスペリエンスを可能にする新しい Mixed Reality サービスです。 Azure 空間アンカーの詳細については、 [こちら](https://azure.microsoft.com//services/spatial-anchors/)を参照してください。

**Q..この会場では、マルチプレーヤーエクスペリエンスを専門としており、開発時間をコンテンツやフロントエンド開発に専念させたいと考えています。バックエンド開発をブートストラップまたはオフロードするのに役立つサービスはありますか。**

A: Azure PlayFab は、ライブゲーム用の完全なバックエンドプラットフォームです。 詳細については、 [こちら](https://playfab.com/)を参照してください。

### <a name="misc"></a>その他

**Q: SteamVR を使用して自分のエクスペリエンスをデプロイします。Windows Mixed Reality は SteamVR と連携しますか。**

A: SteamVR の Windows Mixed Reality では、ユーザーは Windows Mixed Reality のイマーシブヘッドセットで SteamVR エクスペリエンスを実行できます。 SteamVR と WMR の詳細について [は、こちら](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)を参照してください。

### <a name="support-and-community"></a>サポートとコミュニティ  

以下は、チームの分野の専門家と連携し、トラブルシューティングのサポートを受け、より広範な mixed reality 開発コミュニティに貢献するうえで役立つリソースです。  

公開されているすべての機能で問題が発生した場合は、フィードバックハブを使用してバグを報告してください。ガイダンスについては、この [ページ](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/filing-feedback)を参照してください。

WMR のトラブルシューティングの詳細については、 [サポート要求](https://support.microsoft.com//supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782)を提出して、カスタマーサポートチームにご連絡ください。

HoloDevelopers の余裕期間チャネルに参加して、チームによる混合現実と分野の専門家に取り組んでいる開発者と提携してください。 [aka.ms/holodevelopers](https://aka.ms/holodevelopers)

Twitter: ニュース、イベント、および更新については、Mixed Reality 開発者関係チームにご協力ください @MxdRealityDev 

サンフランシスコにいる場合、Microsoft リアクターでは常に何かが行われています。 イベントのカレンダーを [ここ](https://developer.microsoft.com//reactor/Location/San%20Francisco)に表示できます。
