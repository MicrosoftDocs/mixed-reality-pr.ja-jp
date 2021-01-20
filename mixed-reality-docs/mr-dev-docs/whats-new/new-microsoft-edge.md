---
title: Windows Mixed Reality と新しい Microsoft Edge
description: 新しい Microsoft Edge for Mixed Reality について説明します。これには、予想されること、検索する更新プログラム、既知の問題などが含まれます。
author: mattzmsft
ms.author: mazeller
ms.date: 08/04/2020
ms.topic: article
keywords: edge、new、イマーシブ web、microsoft edge、browser、vr、360、360 video、360 viewer、webxr、webvr
ms.openlocfilehash: 041c374e1e2120c3aac35bd09889b8594825a186
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582505"
---
# <a name="the-new-microsoft-edge-for-windows-mixed-reality"></a>新しい Microsoft Edge for Windows Mixed Reality

[新しい Microsoft Edge をダウンロードできるようになりました](https://blogs.windows.com/windowsexperience/?p=173496)が、今後数か月にわたって測定されたロールアウトアプローチに従っ[て、将来の更新によって Windows 10 でインストールされるまで待つ](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/)こともできます。 

このニュースでは、Windows mixed reality の **ヘッドセットのお客様に、新しい Microsoft Edge から期待されることを知らせ、保留中の更新プログラムを表示して、Windows 混在環境でのブラウズエクスペリエンスを向上させたいと考えまし** た。

## <a name="introducing-the-new-microsoft-edge"></a>新しい Microsoft Edge の紹介

新しい Microsoft Edge は、 [Chromium のオープンソースプロジェクト](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) をデスクトップ上に採用しているため、web 開発者にとって、顧客の互換性が向上し、web の断片化が少なくなります。 また、WebVR の代わりに、VR ヘッドセット用のイマーシブ web エクスペリエンスを作成するための新しい標準である WebXR at launch もサポートします。

>[!IMPORTANT]
>Microsoft Edge を最新の Windows 10 デバイスにインストールすると、PC 上の以前の (レガシ) バージョンが置き換えられます。

## <a name="getting-ready-for-the-new-microsoft-edge"></a>新しい Microsoft Edge の準備

Mixed reality ホームで新しい Microsoft Edge を使用する windows Mixed Reality VR ヘッドセットのお客様は、mixed reality ホームで **Win32 アプリケーション (新しい Microsoft edge など) をネイティブでサポートするために、windows 10 バージョン1903以降にアップグレード** する必要があります。 Windows Update を確認 [するか、Windows 10 の最新バージョンを手動でインストールして](https://www.microsoft.com/en-us/software-download/windows10)ください。

混合現実のホームで Microsoft Edge エクスペリエンスを最大限に活用するために、windows **10 バージョン 1903 (またはそれ以降) の2020-01 累積的な更新プログラムが適用された新しい Microsoft edge の Windows Mixed reality 最適化の主要** な部分を待機することもお勧めします。これは、1月の最後まで Windows Update で利用可能になります。

>[!IMPORTANT]
>これらの更新を行う前に新しい Microsoft Edge をダウンロードすることを選択した場合は、Windows Mixed Reality でのその動作に関する既知の問題がいくつかあります (下記を参照してください)。

## <a name="known-issues"></a>既知の問題

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Windows 10 バージョン 1903 (またはそれ以降) の2020-01 累積更新プログラムによって解決された既知の問題

- 新しい Microsoft Edge を含む任意の Win32 アプリを起動すると、ヘッドセットの表示が短時間フリーズします。
- Microsoft Edge タイルは、Windows Mixed Reality の [スタート] メニューから消えます ("クラシックアプリ" フォルダーで見つけることができます)。
- 以前の Microsoft Edge からの Windows は、mixed reality ホームの周囲に配置されていますが、使用することはできません。 これらのウィンドウをアクティブ化しようとすると、デスクトップアプリで Edge が起動します。
- Mixed reality ホームでハイパーリンクを選択すると、mixed reality ホームではなく、デスクトップで web ブラウザーが起動します。
- Webvr ショーケースアプリは、WebVR がサポートされなくなっても、mixed reality ホームに存在します。
- キーボード起動とビジュアルの全般的な機能強化。

### <a name="monitor-and-input-handling-issues"></a>モニターと入力処理の問題

Windows 10 バージョン 1903 (またはそれ以降) の2020-01 の累積的な更新プログラムを実行した後、仮想モニターは、Windows Mixed Reality セッション中に **表示 > システム >** の [設定] に、汎用的な物理モニターとして表示されます。 一部のお客様 (特に複数の物理モニタを使用している場合) は、デスクトップレイアウトと入力処理に関する問題を結果として通知することがあります。

**理由**

Windows [10 月2019更新プログラム](/windows/mixed-reality/enthusiast-guide/release-notes-may-2019)では、Windows Mixed Reality の従来の Win32 アプリケーションのサポートが導入されました。 このサポートを有効にするには、Win32 アプリケーションをホストするために仮想モニターを作成する必要があります。 新しい Win32 アプリケーションを起動するたびに、別の仮想モニターを作成する必要があります。 残念ながら、仮想モニターの作成は集中的なタスクであり、ヘッドセットの表示が短時間フリーズすることがあります。 お客様は、これが不快で破壊的なエクスペリエンスであるというフィードバックを提供しました。 フィードバックや Win32 アプリケーションの使用量の増加により、Windows Mixed Reality の起動時に3つの仮想モニターを事前に割り当てることを決定しました。 これにより、中断を防ぐことができます。また、ヘッドセットの表示がフリーズしていなくても、最大3つの同時 Win32 アプリケーションを起動できます。

**回避策**

私たちは、一部のお客様 (特に複数の物理モニタを持つもの) がこの仮想モニタの事前割り当てを無効にするというフィードバックを受け取りました。 お客様に制御を提供するために、次の Windows 更新プログラムで使用できるレジストリキー値の変更を伴う回避策を有効にしました。

- 2020-07 Windows 10 バージョン2004の累積的な更新プログラムのプレビュー (KB4568831)
- 2020-10 Windows 10 バージョン1909の累積的な更新プログラムのプレビュー (KB4580386)
- 2020-10 Windows 10 バージョン1903の累積的な更新プログラムのプレビュー (KB4580386)

>[!NOTE]
>レジストリキー値の変更は、上級ユーザーを対象としています。

>[!WARNING]
>仮想モニタの事前割り当てを無効にすると、Windows Mixed Reality で Win32 アプリケーション (ストリーム、新しい Microsoft Edge、または Google Chrome など) を起動したときにヘッドセットが短時間で表示されることがあります。

仮想モニタの事前割り当てを無効にするには:
1. 上記のいずれかの Windows 10 累積的な更新プログラムのプレビューバージョンの **Windows Update** を確認し、利用可能な場合は更新プログラムをインストールします。 更新プログラムは、[Windows Update の設定] ページの [ **オプションの更新プログラム** ] または [ **詳細** 設定] で確認できます。
2. **レジストリエディター** の起動
3. [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic] に移動します。 \"
4. "PreallocateVirtualMonitors" REG_DWORD が存在しない場合は、[ **Edit > New > DWORD (32 ビット)] 値** を選択し、名前として preallocatevirtualmonitors を入力して作成します。
5. "PreallocateVirtualMonitors" REG_DWORD が存在する (または作成した) 場合は、エントリをダブルクリックし、[値のデータ] を 1 (既定値) から 0 (ゼロ) に変更します。
    * TRUE-1
    * FALSE-0

事前割り当てではなく、Windows Mixed Reality で Win32 アプリケーションを起動しようとすると、仮想モニターが割り当てられるようになりました。 これをリセットし、仮想モニタの事前割り当てを再び有効にするには、DWORD の "値のデータ" を1に戻します。

### <a name="other-known-issues"></a>その他の既知の問題

-   Windows Mixed Reality で開いている web サイトは、Mixed Reality ポータルが閉じると失われます。 Microsoft Edge ウィンドウは、mixed reality ホームに配置された位置にとどまります。
- 360 Viewer 拡張機能などの WebXR エクスペリエンスは、ハイブリッド GPU セットアップを使用している Pc では正常に起動しない可能性があります。 この問題を回避するには、新しい Microsoft Edge でプレビュー機能を有効にします。 に移動し `edge://flags` 、"マルチ gpu" を検索して、 **WEBXR マルチ gpu サポート** と呼ばれるフラグを有効にします。
-   Microsoft Edge ウィンドウからのオーディオは spatialized ません。
-   **360 Viewer 拡張機能のバージョン 2.3.8**: Windows Mixed Reality で YouTube から360ビデオを開くと、ヘッドセットでビデオがゆがんでしまう可能性があります。 Edge を再起動して、この問題を解決するには、360 Viewer 拡張機能を非表示にする必要があります。 `edge://system/`アドレスバーに「」と入力し、[拡張機能] の横にある **展開** ボタンを選択すると、拡張機能のバージョンを確認できます。