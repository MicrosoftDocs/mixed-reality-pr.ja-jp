---
title: Windows Mixed Reality の PC ハードウェアの最小互換性ガイドライン
description: Windows Mixed Reality との互換性に関する PC システムの最小要件を概説したグラフ。
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、Ultra、互換性、互換性、システム要件、PC
appliesto:
- Windows 10
ms.openlocfilehash: e21d2d18edbf2c94d156f14fa8c2598822a8bc7a
ms.sourcegitcommit: 5eb27475f8616c9d4f95b4b386a5bd0d22f41125
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2020
ms.locfileid: "92174364"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>Windows Mixed Reality の PC ハードウェアの最小互換性ガイドライン

## <a name="features-and-experiences"></a>機能とエクスペリエンス

Windows 10 は、Windows Mixed Reality と Windows Mixed Reality の両方を支えています。 使用するバージョンは、PC ハードウェアによって異なります。

Windows Mixed Reality は、次のような追加の機能を備えています。

* 視覚エフェクトが鮮明になり、更新率が高くなります (1 秒あたり90フレーム)。
* 多くのグラフィックス処理を要するゲームを含む、より多くのアプリとエクスペリエンス。
* デスクトップ上の ' ' ミラー ' ' ウィンドウ。 mixed reality に表示される内容が表示されます。
* Mixed reality エクスペリエンスのビデオ (および写真) を記録し、共有します。

## <a name="minimum-pc-hardware-guidelines"></a>最小 PC ハードウェア ガイドライン

Windows Mixed Reality を最大限に活用するには、 [windows mixed reality 対応 pc または](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) windows mixed REALITY 互換 pc を使用します。 windows mixed reality のエクスペリエンスを提供できます。 Windows Mixed Reality Ultra は、より高いリフレッシュレートでビジュアル化されたビジュアルを提供します。最も多くのグラフィックスを消費するゲームを含むアプリとエクスペリエンスが増え、デスクトップ上で Windows Mixed Reality エクスペリエンスをミラーリングしたり、他のユーザーとのエクスペリエンスを記録および共有したりすることができます。 

PC が Windows Mixed Reality を実行できるかどうかを確認するには、以下のハードウェアガイドラインを確認し、 [Mixed Reality ポータルアプリ](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M)を実行します。

実際の設定によってパフォーマンスが異なることに注意してください。 また、使用している Windows Mixed Reality イマーシブヘッドセット用の [適切なポート](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) が PC にあることを確認する必要もあります。

>[!NOTE]
>開発用 Pc のガイドラインは、mixed reality アプリを実行しているコンシューマー Pc のガイドラインよりも高くなっています。 Mixed reality 開発者の方は、 [「推奨される開発用 PC 仕様」を参照してください](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development)。


## <a name="mixed-reality-portal-app"></a>Mixed Reality ポータルアプリ

混合 Reality ポータルは、PC が Windows Mixed Reality を実行する準備ができていることを確認するための最適な方法です。 

<a href="https://www.microsoft.com/store/productid/9ng1h8b3zc7m"><img alt="Download Mixed Reality Portal" src="images/WMR-PC-Check-app.png"/></a>

アプリを実行すると、次のいずれかのメッセージが表示されます。
* **これで問題ありません。** PC には、Windows Mixed Reality を実行するために必要なものがあります。
* **では、一部の機能がサポートされます。** この PC は Windows Mixed Reality を実行できますが、一部の機能が制限される場合があります。
* **Mixed reality を実行できません。** この PC は、Windows Mixed Reality を実行するために必要な最小要件を満たしていません。

次に、必要なハードウェア、ドライバー、およびオペレーティングシステムに対して PC の分析を行います。
![Windows Mixed Reality PC チェックのスクリーンショット](images/screenshot-mr-pc-check.jpg) 

<table>
<tr>
<th>アイコン</th><th>意味</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">必要な項目が PC から渡されます。</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">指定された要件に応じて、PC に問題がある可能性があります。 問題が発生した場合は、トラブルシューティングまたは PC のアップグレードが必要になることがあります。</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">指定された項目の要件を PC が満たしていません。</td>
</tr>
</table>

 [Mixed Reality ポータルの結果に関するヘルプを表示する](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)

## <a name="compatibility-guidelines"></a>互換性のガイドライン
> [!IMPORTANT]
> Microsoft では、これらの Windows Mixed Reality PC 互換性ガイドラインを更新するために、を追加しています。 最新のガイドラインと要件については、定期的に確認してください。

**HP リバーブと互換性のある仕様**<br>
解像度が高いため、次の要件が HP リバーブの G1 & G2 製品ラインに適用され、最適な90Hz、完全な解決エクスペリエンスが実現されます。 

<ul>
<li> Intel Core i5、i7、Intel Xenon E3-1240 v5、同等またはそれ以上。 AMD Ryzen 5 と同等またはそれ以上。 </li>
<li> NVIDIA GeForce GTX 1080、AMD Radeon RX 5700、同等またはそれ以上 </li> 
<li> メモリ: 8 GB 以上の RAM </li> 
<li> ポート1.3 を表示する (1x) </li> 
<li> 電力供給付き USB 3.0 タイプ C (または付属の電源アダプター)</li>
<li> Windows 10 5 月2019更新以降 </li>
</ul>

**その他のすべての WMR 互換ヘッドセット** <br>
他のすべての HMD のについては、次の要件を参照してください。 

<table>
<tr>
    <th style="width:10%"></th><th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality ウルトラ Pc</th>
    <th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality Pc</th>
</tr><tr>
    <td style="vertical-align: middle">オペレーティング システム</td><td colspan="2" style="vertical-align: middle; text-align: center;">Windows 10 の作成者の更新プログラム (RS3)、またはそれ以降のホーム、Pro、ビジネス、教育。<br/>    (<b>注</b>: S モードでは、N バージョンまたは Windows 10 Pro ではサポートされていません)</td>
</tr><tr>
    <td style="vertical-align: middle">プロセッサ</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 4590 (第4世代)、クアッドコア (またはそれ以上) <br>AMD Ryzen 5 1400 3.4 Ghz (デスクトップ)、クアッドコア (またはそれ以上)</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 7200U (7 世代モバイル)、Intel Hyper-Threading テクノロジを使用したデュアルコア (またはそれ以上) <br>AMD Ryzen 5 1400 3.4 Ghz (デスクトップ)、クアッドコア (またはそれ以上)</td>
</tr><tr>
    <td style="vertical-align: middle">RAM</td>
    <td style="vertical-align: middle; text-align: center;">8 GB DDR3 (またはそれ以上)</td>
    <td style="vertical-align: middle; text-align: center;">8 GB DDR3 デュアルチャネル (またはそれ以上)</td>
</tr><tr>
    <td style="vertical-align: middle">ディスクの空き領域</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">10 GB 以上</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">10 GB 以上</td>
</tr><tr>
    <td style="vertical-align: middle">グラフィックスカード</td>
    <td style="vertical-align: middle; text-align: middle;">
            <ul> 
            <li>NVIDIA GTX 1060 (またはそれ以降) DX12 対応の離散 GPU</li>
            <li>AMD RX 470/570 (またはそれ以降) DX12 対応の個別 GPU </li>
            </ul>     
            <b>注:</b> GPU は、PCIe 3.0 x4 + リンクスロットでホストされている必要があります </td>
    <td style="vertical-align: middle; text-align: middle;">
            <li>Integrated Intel HD Graphics 620 (またはそれ以降) DX12 対応の統合 GPU <a href="https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units">(モデルが大きいかどうかを確認)</a></li>
        <li>NVIDIA MX150 (またはそれ以降) の個別 GPU</li>
        <li>Nvidia GeForce GTX 1050 離散 GPU</li>
        <li>Nvidia 965M 離散 GPU</li>
        <li>AMD Radeon RX 460/560</li>
        </ul>
        <b>注:</b> HD Graphics 4xx、5xx、2xxx、3xxx、4xxx、5xxx、6xxx などの古い Intel Gpu はサポートされていません。
    </td>
</tr><tr>
    <td style="vertical-align: middle">グラフィックスドライバー</td>
    <td colspan="3" td style="vertical-align: middle; text-align: center;">Windows Display Driver Model (WDDM) 2.2</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">グラフィックスの表示ポート</a></td>
    <td style="vertical-align: middle; text-align: center;">HDMI 2.0 または DisplayPort 1.2</td>
    <td style="vertical-align: middle; text-align: center;">HDMI 1.4 または DisplayPort 1.2</td>
</tr><tr>
    <td style="vertical-align: middle">ディスプレイ</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">接続された外部または統合 VGA (800x600) ディスプレイ (またはそれ以上)</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">USB 接続</a></td>
    <td colspan="2" style="vertical-align: middle; text-align: center;">USB 3.0 タイプ A </td>
</tr><tr>
    <td style="vertical-align: middle">Bluetooth 接続 ( <a href="controllers-in-wmr.md">モーションコントローラー</a>用)</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Bluetooth 4.0</td>
</tr><tr>
    <td style="vertical-align: middle">ヘッドセットのフレームレート</td>
    <td style="vertical-align: middle; text-align: center;">90 Hz</td>
    <td style="vertical-align: middle; text-align: center;">60 Hz</td>
</tr>
<tr>
    <td style="vertical-align: middle">Power</td>
    <td style="vertical-align: middle; text-align: center;">USB 3.0 (タイプ A) ポート</td>
    <td style="vertical-align: middle; text-align: center;">USB 3.0 (タイプ A) ポート</td>
</tr>
</table>



**追加情報: **
* 大規模なラップトップ (画面が15以上の場合) が最適です。
* 最適なエクスペリエンスを実現するために、Intel® Core™または7世代の Intel® Core™ i5 プロセッサを第8世代にすることをお勧めします。
* ハイブリッドグラフィックス構成は、Windows Mixed Reality Ultra とのみ互換性があります。 ハイブリッド構成の個別のグラフィックスアダプターは、「個別のグラフィックスアダプターの Windows Mixed Reality ガイドライン」に記載されているすべての要件を満たしている必要があります。
* Windows Mixed Reality を実行する必要がある独立したグラフィックスカードがあるが、既定では 60 Hz (60 フレーム/秒) のリフレッシュレートを使用している場合は、フルサイズの 2.0 DisplayPort を使用してヘッドセットに接続し、90 Hz のリフレッシュレートを有効にします。
* ヘッドセットごとに異なるハードウェアポートが必要になる場合があるため、ヘッドセットに接続するための適切なポートまたは [必要なアダプター](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) が PC にあることを確認してください。

>[!NOTE]
>最小確認の仕様を満たしていない、独立した統合されたグラフィックスハードウェアは、Windows Mixed Reality に対してテスト、確認、または最適化されていないため、正常に機能しない場合もあります。

## <a name="windows-mixed-reality-and-surface"></a>Windows Mixed Reality と Surface

Surface デバイスで最適な Windows Mixed Reality エクスペリエンスを実現するために、NVIDIA GeForce GTX 1060 および 16 GB の RAM で構成された、"" という2つのドライブを使用することをお勧めします。  この構成では、すべての Windows Mixed Reality 機能 @ 90Hz がサポートされています。また、Windows Mixed Reality バッジのテストが完了しています。  Surface Book 2 (13)、Surface Studio、Surface ノート Pc、Surface Pro (2017) では、Intel Core i5 CPU (またはそれ以上) と 8 GB 以上の RAM を使用して構成した場合に、一部の Windows Mixed Reality 機能がサポートされます。

**要件:**
* Surface 製品では、Windows Mixed Reality と互換性のあるドライバーの更新が必要です。 これらのドライバーは、[ **> 設定] [更新とセキュリティ > の更新プログラムの確認] の**順に移動して、画面にインストールできます。
* Surface 製品では、Windows Mixed Reality ヘッドセットの場合、ビデオポート (Surface PC によってはミニ DisplayPort または USB-C 2.0) からの [アダプター](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) が必要です。 HDMI AV アダプターに Mini-DisplayPort 表面の最新バージョンは、HDMI 2.0 と互換性があります (古いバージョンは)。 同様に、 <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">SURFACE USB-C から Hdmi アダプター</a> も hdmi 2.0 と互換性があります。

>[!WARNING]
>すべてのミニ DisplayPort アダプターまたは USB-C から HDMI アダプターが HDMI 2.0 に対応しているわけではありません。 すべてのアダプターで、明示的な "HDMI 2.0" 互換性または "4K" 互換性があるかどうかを確認することを検討してください。

Windows Mixed Reality とのサーフェイスの互換性の詳細については、次の表を参照してください。

<table>
    <tr>
        <th> Surface デバイス </th><th> Windows Mixed Reality 機能のサポート </th><th> 推奨構成 </th><th> Notes</th>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro (オリジナル)/Surface Pro 2 </td><td style="vertical-align: middle"> なし </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro 3 </td><td style="vertical-align: middle"> なし </td><td> </td><td></td>
    </tr>
(Windows 10 Pro がインストールされている場合) <tr>
        <td style="vertical-align: middle"> Surface Pro 4 </td><td style="vertical-align: middle"> なし </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface 3 </td><td style="vertical-align: middle"> なし </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Book </td><td style="vertical-align: middle"> なし </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> パフォーマンスベースのある Surface Book </td><td style="vertical-align: middle"> なし </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Go </td><td style="vertical-align: middle"> なし </td><td> </td><td></td>
    </tr>
<tr>
        <td style="vertical-align: middle"> Surface Book 2 (15 &quot; ) </td><td style="vertical-align: middle"> 完全 </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GTX 1060/16 GB RAM </td>
        <td>
            <ul>
                <li><b>推奨</b>: Surface デバイスで最適な Windows Mixed Reality エクスペリエンスを実現するために、NVIDIA GeForce GTX 1060 と 16 GB の RAM で構成された 2 15、"" を使用することをお勧めします。  この構成は、Windows Mixed Reality のバッジとしてテストされています。そのため、すべての Windows Mixed Reality 機能がサポートされ、互換性のあるさまざまなアプリやゲームを活用できます。</li>
                <li>NVIDIA GeForce GTX 1060 の離散 GPU では、Windows Mixed Reality の超 @ 90Hz エクスペリエンスが提供されます。</li><br/>                <li>最適なパフォーマンスを得るには、Surface Book 2 で特別にリリースされた Nvidia グラフィックスドライバーを使用してください。 新しいドライバーは Nvidia&#39;s web サイトで入手できますが、テストされていません。</li><br/>                <li><a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">SURFACE USB-C から HDMI アダプター</a>が必要です (他のアダプターは動作しますが、テストされていません)</li>
                <li><b>Surface dock での注意</b>: surface Book 2 での surface dock の使用は、Windows Mixed Reality では公式にサポートされていません。これは、surface dock の電源の制限によるものです。</li><br/>                <li><b>Windows 10 バージョン1803で</b>は、Windows 10 バージョン1803を&#39;再実行する場合は、最新のパフォーマンス修正プログラムがインストールされていることを確認するために、OS ビルド17134.137 以降 (KB4284848 によってインストールされます) に再&#39;する必要があります。 詳細については、 <a href="https://support.microsoft.com/en-us/help/4284848/windows-10-update-kb4284848">KB4284848</a>のリリースノートを参照してください。</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Book 2 (13.5 &quot; ) </td><td style="vertical-align: middle"> 一部サポート </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GTX 1050/16 GB RAM </td>
        <td>
            <ul>
                <li><b>注</b>: Surface Book 2 (13) は、Windows mixed reality ではバッジませんが、一部の Windows Mixed reality 機能をサポートするため、互換性のあるアプリとゲームの数に制限があります。  パフォーマンスは構成によって異なります。</li>
                <li>Intel Core i5/intel HD Graphics 620 統合 GPU を使用した構成では、Windows Mixed Reality @ 60Hz エクスペリエンスが提供されます。</li>
                <li>Intel Core i7/NVIDIA GeForce GTX 1050 の離散 GPU を使用した構成では、Windows Mixed Reality が使用されます。</li>                       <li>最適なパフォーマンスを得るには、Surface Book 2 で特別にリリースされた Nvidia グラフィックスドライバーを使用してください。 新しいドライバーは Nvidia&#39;s web サイトで入手できますが、テストされていません。</li>
                <li><a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">SURFACE USB-C から HDMI アダプター</a>が必要です (他のアダプターは動作しますが、テストされていません)</li>
                <li><b>Surface dock での注意</b>: surface Book 2 での surface dock の使用は、Windows Mixed Reality では公式にサポートされていません。これは、surface dock の電源の制限によるものです。</li>
                <li><b>Windows 10 バージョン1803で</b>は、Windows 10 バージョン1803を&#39;再実行する場合は、最新のパフォーマンス修正プログラムがインストールされていることを確認するために、OS ビルド17134.137 以降 (KB4284848 によってインストールされます) に再&#39;する必要があります。 詳細については、 <a href="https://support.microsoft.com/en-us/help/4284848/windows-10-update-kb4284848">KB4284848</a>のリリースノートを参照してください。</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Studio </td><td style="vertical-align: middle"> 一部サポート </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GeForce GTX 980m/16 GB の RAM </td>
        <td>
            <ul>
                <li><b>注</b>: Surface Studio は Windows mixed reality ではバッジませんが、一部の Windows Mixed reality 機能をサポートするため、互換性のあるアプリとゲームの数に制限があります。  パフォーマンスは構成によって異なります。</li>
                <li>NVIDIA GeForce GTX 965m を使用した構成では、Windows Mixed Reality @ 60Hz エクスペリエンスが提供されます。</li>
                <li>NVIDIA GeForce GTX 980m の構成では、Windows Mixed Reality @ 90Hz エクスペリエンスが提供されます。</li>
                <li>Surface ミニ DisplayPort から HDMI 2.0 アダプター (他のアダプターは動作しますが、テストされていない場合があります)</li>
                <li>Windows Mixed Reality ヘッドセットは、"+" 記号を使用して USB ポートに接続する必要があります</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro (2017) </td><td style="vertical-align: middle"> 一部サポート </td><td style="vertical-align: middle"> Intel Core i7/Intel®虹彩™プラスグラフィックス 640/16 GB の RAM </td>
        <td>
            <ul>
                <li><b>注</b>: Surface Pro (2017) は、Windows mixed reality のバッジではありませんが、一部の Windows Mixed reality 機能をサポートするため、互換性のあるアプリとゲームの数に制限があります。  パフォーマンスは構成によって異なります。</li>
                <li>Intel Core M3/Intel HD Graphics 615 統合 GPU を使用した構成はサポートされ<b>ていません</b>。</li>
                <li>Intel Core i5/intel HD Graphics 620 統合 GPU を使用した構成では、Windows Mixed Reality @ 60Hz エクスペリエンスが提供されます。</li>
                <li>Intel Core i7/Intel®虹彩™とグラフィックス640統合 GPU を使用した構成では、Windows Mixed Reality @ 60Hz エクスペリエンスが提供されます。</li><br/><li>2.0 アダプターの Surface ミニ DisplayPort が必要です (他のアダプターは動作しますが、テストされていません)</li>
                <li>使用中に <a href="https://support.microsoft.com/en-us/help/4023450/surface-surface-battery-and-power">パフォーマンススライダー</a> が "最適なパフォーマンス" に設定される必要があります。</li>
            </ul>
        </td>
    </tr><br/>    <tr>
        <td style="vertical-align: middle"> Surface Laptop </td><td style="vertical-align: middle"> 一部サポート </td><td style="vertical-align: middle"> Intel Core i7/Intel®虹彩™プラスグラフィックス 640/16 GB の RAM </td>
        <td>
            <ul>
                <li><b>注</b>: Surface ノート pc は、Windows mixed reality のバッジではありませんが、一部の Windows Mixed reality 機能をサポートするため、互換性のあるアプリとゲームの数に制限があります。  パフォーマンスは構成によって異なります。</li>
                <li>Intel Core M3/Intel HD Graphics 615 統合 GPU を使用した構成はサポートされ<b>ていません</b>。</li>
                <li>Intel Core i5/intel HD Graphics 620 統合 GPU を使用した構成では、Windows Mixed Reality @ 60Hz エクスペリエンスが提供されます。</li>
                <li>Intel Core i7/Intel®虹彩™とグラフィックス640統合 GPU を使用した構成では、Windows Mixed Reality @ 60Hz エクスペリエンスが提供されます。</li><br/><li>2.0 アダプターの Surface ミニ DisplayPort が必要です (他のアダプターは動作しますが、テストされていません)</li>
                <li>使用中に <a href="https://support.microsoft.com/en-us/help/4023450/surface-surface-battery-and-power">パフォーマンススライダー</a> が "最適なパフォーマンス" に設定される必要があります。</li>
            </ul>
        </td>
    </tr>
</table>

## <a name="see-also"></a>関連項目
* [コミュニティへの質問](https://answers.microsoft.com)
* [サポートについては、お問い合わせください](https://support.microsoft.com/contactus/)
* [Windows Mixed Reality 対応 Pc の推奨アダプター](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
