---
title: HoloLens Research モード
description: HoloLens で Research モードを使用すると、アプリケーションは主要なデバイスセンサーストリーム (深さ、環境追跡、および赤外線反射) にアクセスできます。
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: Research モード, cv, rs4, コンピュータービジョン, 研究, HoloLens, HoloLens 2
ms.openlocfilehash: 6c40ac814a5dacfdbb942aec8200f46157bea161
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530090"
---
# <a name="hololens-research-mode"></a>HoloLens Research モード

検索モードは、キーセンサーへのアクセスを提供するために HoloLens (第1世代) デバイスで導入されました。特に、展開を意図していない研究アプリケーションに使用します。  HoloLens 2 の研究モードでは、HoloLens 1 の機能は維持されますが、次のストリームへのアクセス権が追加されます。

* **可視性の低い環境の追跡カメラ** -ヘッドの追跡とマップの作成にシステムが使用するグレースケールのカメラです。
* **深度カメラ** –2つのモードで動作します。  
    + セルフトラッキングに使用される AHAT、高頻度 (45 FPS) のほぼ深い検出。 最初のバージョンの短いスローモードとは別に、AHAT では、1メーターを超えるフェーズラップに擬似的な深さが与えられます。 
    + Long throw、低頻度 (1-5 FPS)、[空間マッピング](../../design/spatial-mapping.md)で使用される深い深さの検出

* **IR 反射率ストリームの2つのバージョン** 。 HoloLens が計算に使用します。 これらのイメージは赤外線によって照らされ、アンビエントに見える光の影響を受けません。

HoloLens 2 を使用している場合は、以下の追加入力にもアクセスできます。

* **加速度計** –システムによって使用され、X 軸、Y 軸、Z 軸、重力に沿った線形加速度を決定します。
* **ジャイロ** –回転を決定するためにシステムによって使用されます。
* **磁力計** –絶対方向を推定するためにシステムによって使用されます。

> [!IMPORTANT]
> リサーチモードは現在パブリックプレビュー段階です。 

![Research モードアプリのスクリーンショット](images/sensor-stream-viewer.jpg)<br>
*リサーチモードで使用可能な8個のセンサーストリームを表示するテストアプリケーションの mixed reality キャプチャ*

## <a name="usage"></a>使用

研究モードは、Computer Vision およびロボットのフィールドの新しいアイデアを調査する教育機関および産業用の研究者向けに設計されています。  これは、エンタープライズ環境に配置されているアプリケーションや、Microsoft Store またはその他の配布チャネルを通じて利用できるアプリケーションを対象としていません。

さらに、Microsoft は、今後のハードウェアまたは OS の更新で、リサーチモードまたは同等の機能がサポートされることを保証しません。 しかし、それを使用して新しいアイデアを開発し、テストすることをやめてください。

## <a name="security-and-performance"></a>セキュリティとパフォーマンス

リサーチモードを有効にすると、通常の条件下で HoloLens 2 を使用した場合よりも多くのバッテリ電源が使用されます。  このモードを有効にすると、アプリケーションがセンサーデータを誤用する可能性があるため、デバイスの全体的なセキュリティを低下させることもできます。  デバイスのセキュリティの詳細については、「 [HoloLens のセキュリティ](https://docs.microsoft.com/hololens/hololens-faq-security)に関する FAQ」を参照してください。  

## <a name="device-support"></a>デバイス サポート
<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    <tr>
        <td><strong>機能</strong></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 第 1 世代</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></td>
    </tr>
     <tr>
        <td>ヘッドトラッキングカメラ</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>IR カメラ & 深度</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>加速度計</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>ジャイロスコープ</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>磁力計</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-first-gen-and-hololens-2"></a>リサーチモードの有効化 (HoloLens first Gen および HoloLens 2)

リサーチモードは、開発者モードの拡張機能です。 開始する前に、デバイスの開発機能を有効にして、リサーチモードの設定にアクセスできるようにする必要があります。 

* [ **スタート] メニューを開き > 設定** を開き、[ **更新プログラム**] を選択します。
* **開発者向けに** 選択し、**開発者モード** を有効にします。
* 下へスクロールし、**デバイス ポータル** を有効にします。

開発者向け機能が有効になったら、 [デバイスポータルに接続](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) して、リサーチモードの機能を有効にします。

* **デバイスポータル** で、**システム > リサーチモード** に切り替えます。
* [ **センサーストリームへのアクセスを許可する**] を選択します。
* ページの上部にある **電源** メニュー項目からデバイスを再起動します。

デバイスを再起動すると、 **デバイスポータル** から読み込まれたアプリケーションは、リサーチモードのストリームにアクセスできるようになります。

![HoloLens デバイスポータルの [リサーチモード] タブ](images/ResearchModeDevPortal.png)<br>
*HoloLens デバイスポータルの [リサーチモード] ウィンドウ*

> [!IMPORTANT]
> HoloLens 2 の研究モードは、ビルド19041.1356 以降で使用できます。 以前のビルドでアクセスする必要がある場合は、 [Insider Preview](https://docs.microsoft.com/hololens/hololens-insider) プログラムにサインアップしてください。

### <a name="using-sensor-data-in-your-apps"></a>アプリでセンサーデータを使用する

アプリケーションは、写真やビデオのカメラストリームにアクセス [メディアファンデーション](https://msdn.microsoft.com/library/windows/desktop/ms694197) するのと同じ方法でセンサーストリームデータにアクセスできます。 

HoloLens 開発に使用できるすべての Api は、リサーチモードでも使用できます。 具体的には、アプリケーションは、各センサーフレームのキャプチャ時間で HoloLens が6つの領域にあることを正確に把握しています。

サンプルアプリケーションを使用して、リサーチモードのストリームアクセス、 [組み込みと extrを](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)使用した ics、およびストリームの記録を示しています。
* [HoloLens (最初の世代)](https://github.com/Microsoft/HoloLensForCV)
* [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a>サポート

HoloLens (最初の世代) の場合は、HoloLensForCV リポジトリの [issue tracker](https://github.com/Microsoft/HololensForCV/issues) を使用してフィードバックを投稿し、既知の問題を追跡します。

HoloLens 2 の場合は、HoloLens2ForCV リポジトリの [問題トラッカー](https://github.com/microsoft/HoloLens2ForCV/issues) を使用してフィードバックを投稿し、既知の問題を追跡します。

## <a name="see-also"></a>関連項目

* [Microsoft メディア ファンデーション](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [HoloLensForCV GitHub リポジトリ](https://github.com/Microsoft/HoloLensForCV)
* [HoloLens2ForCV GitHub リポジトリ](https://github.com/microsoft/HoloLens2ForCV)
* [Windows Device Portal を使用する](using-the-windows-device-portal.md)
