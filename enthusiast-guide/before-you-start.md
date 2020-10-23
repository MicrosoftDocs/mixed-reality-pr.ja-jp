---
title: 開始する前に
description: PC が Windows Mixed Reality と互換性があり、準備ができていることを確認する方法。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、互換性、互換性、はじめに、セットアップ、PC、システム要件
appliesto:
- Windows 10
ms.openlocfilehash: 84001a46826ada06e315f1707ee9516c3da063bd
ms.sourcegitcommit: 55a6a0b481238e7a2e3278a51583b6bda0eb259a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434576"
---
# <a name="before-you-start"></a>開始する前に

## <a name="what-youll-need-to-run-windows-mixed-reality"></a>Windows Mixed Reality を実行するために必要なもの

* Windows [Mixed Reality ヘッドマウントされたディスプレイ (HMD)](https://www.microsoft.com/en-us/windows/windows-mixed-reality-devices)。
* Windows [Mixed reality](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 対応 pc、または Windows 10 バージョン1709以降を実行している Windows mixed REALITY 互換 pc。
* インターネット接続
* ディスプレイ、USB、および Bluetooth アダプター (ヘッドセットまたはコンピューターに組み込まれていない場合)
* モーションコントローラー、Xbox コントローラー、またはマウスとキーボードのいずれか
* マイク付きヘッドホン (HMD が組み込まれていない場合)
* 大きな空き領域

## <a name="make-sure-your-pc-is-compatible-with-windows-mixed-reality"></a>PC が Windows Mixed Reality と互換性があることを確認する

PC が Windows Mixed Reality と互換性があるかどうかを確認するには、 [Windows Mixed reality の最小 pc ハードウェア要件](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) を確認するか、Pc で [Windows mixed reality ポータル](install-windows-mixed-reality.md#launch-mixed-reality-portal) を実行します。

PC の互換性の問題の詳細については、 [こちら](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)を参照してください。

## <a name="make-sure-you-have-the-windows-10-version-1709-or-newer-installed"></a>Windows 10 バージョン1709以降がインストールされていることを確認します。

Windows Mixed Reality を使用するには、Windows 10 バージョン1903以降を実行している必要があります。 互換性のある Windows 10 のバージョンは次のとおりです。

* Windows 10 バージョン1903
* Windows 10 バージョン1909
* Windows 10 バージョン2004
* Windows 10 バージョン20H2

現在デバイスが実行されている Windows 10 のバージョンを確認するには、[ **スタート** ] ボタンを選択し、[ **設定] > [システム > について**] の順に選択します。

PC で Windows 10 が最新の状態になっていることを確認するには、[ **スタート** ] ボタンを選択し、[設定] を選択して **& セキュリティ > Windows Update > 更新**します。  **[更新プログラムの確認]** をクリックします。 更新プログラムが利用可能な場合は、インストールします。

PC を最新の状態に保つ方法の詳細について[は、こちら](https://support.microsoft.com/en-us/help/12373/windows-update-faq)を参照してください。

## <a name="make-sure-your-pc-is-connected-to-the-internet"></a>PC がインターネットに接続されていることを確認する

PC がインターネットに接続されていることを確認します。 Windows Mixed Reality を稼働させるには、ドライバーといくつかの追加のソフトウェアをダウンロードする必要があります。

## <a name="make-sure-you-have-a-compatible-graphics-driver"></a>互換性のあるグラフィックスドライバーがあることを確認します。

Windows Mixed Reality セットアップを完了するには、PC に WDDM 2.2 以降のグラフィックスドライバーが必要です。 互換性のあるグラフィックスドライバーがまだない場合は、次のソースを試してください。

* Windows Update を使用して、最新の重要なドライバーの更新プログラムを確認します (**> Windows 設定 > 更新プログラムとセキュリティ > 更新プログラムを確認**します)。
* オプションのドライバーの最新の更新プログラムを確認します。
    1. [ **スタート > デバイスマネージャー**を右クリックします。
    2. [ **ディスプレイアダプター**] を展開します。
    3. グラフィックスカードを右クリックし、[ドライバーの更新] を選択して、 **更新されたドライバーソフトウェアを自動的に検索 >** ます。
* PC の製造元 (OEM) の web サイトを確認します。
* Web サイトで、PC のグラフィックスカードの製造元 (AMD、Intel、NVIDIA など) を確認します。

## <a name="make-sure-that-you-have-any-required-adapters"></a>必要なアダプターがあることを確認する

Windows Mixed Reality 互換 PC には、イマーシブヘッドセットの接続に必要な完全な HDMI および USB 3.0 ポートが搭載されていない可能性があります。 または、Windows Mixed Reality ポータルの要件を満たすために Bluetooth アダプターが必要になる場合があります。  その場合は、ヘッドセットとモーションコントローラーを接続するアダプターが必要になります。 [必要になる可能性があるアダプターの種類の一覧と、特定のアダプターモデルに関する推奨事項](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)を確認してください。

## <a name="make-sure-that-you-have-input-devices"></a>入力デバイスがあることを確認する

Windows Mixed Reality は、Windows Mixed Reality のモーションコントローラーで最適に動作するように設計されています。これは、壁にハードウェアを取り付ける必要のない、自然で正確な対話を実現します。 ただし、Xbox コントローラーまたはマウスとキーボードを使用することもできます。

## <a name="make-sure-that-you-have-a-large-open-space"></a>大きな空き領域があることを確認します。

Windows Mixed Reality を使用しながら移動する場合は、大きな空き領域が必要になります。  セットアップ中に、"固定された" または "すべてのエクスペリエンス" のいずれかを選択するよう求められます。 [すべてのエクスペリエンス] を選択し、移動する場合は境界を設定します。 [イマーシブヘッドセットの正常性、安全性、および快適なガイドライン](wmr-health-safety-comfort.md)を確認して、領域の要件を理解します。

### <a name="seated-and-standing-no-boundary"></a>固定された状態 (境界なし)

[固定された状態] を選択した場合は、境界のないヘッドセットを使用します。 これは、ヘッドセットを使用するときに1つの場所を離れておく必要があることを意味します。これにより、物理的な障害を回避し、危険を防ぐことができます。 停止するか、または立ち上げてもかまいませんが、移動することはできません。 一部のアプリは、境界を使用して動作するように設計されている場合があります。境界を使用せずに使用した場合、それらを使用できなくなったり、同じエクスペリエンスを持たないことがあります。

### <a name="all-experiences-boundary"></a>すべてのエクスペリエンス (境界)

"すべてのエクスペリエンス" を選択した場合は、境界を設定します。境界を使用しているアプリやエクスペリエンスだけでなく、必要のないアプリケーションやエクスペリエンスを使用することもできます。 使用する領域 (ヘッドを含む) に障害、障害、または脆弱な項目がないことを確認するために、スペースを準備する必要があります。 階段の上部、または低天井ファンの下には設定しないでください。 領域から breakables 変更可能な障害を除去し、ヘッドセットを使用するすべてのユーザーが [安全ガイドライン](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort)を読み、理解していることを確認します。

## <a name="see-also"></a>関連項目

* [HMD にプラグインする](plug-in-your-headset.md)
* [最小 PC ハードウェア要件](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
* [推奨されるアダプター](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)