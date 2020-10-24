---
title: Windows Mixed Reality と新しい Microsoft Edge
description: Windows Mixed Reality の新しい Microsoft Edge の準備をします。 予想される変更、検索対象の更新、および既知の問題が含まれます。
author: mattzmsft
ms.author: mazeller
ms.date: 08/04/2020
ms.topic: article
keywords: edge、新規、イマーシブ web、microsoft edge、browser、vr
ms.openlocfilehash: 0f4ecdd26624e9b1e5b8e151e1ac074ece9c9769
ms.sourcegitcommit: 1aae69e26ae872b724be1bd1ae0b3158c49dc7e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92499587"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Windows Mixed Reality と新しい Microsoft Edge

[新しい Microsoft Edge をダウンロードできるようになりました](https://blogs.windows.com/windowsexperience/?p=173496)が、今後数か月の間に測定されたロールアウトアプローチに従って、 [Windows 10 の今後の更新プログラムにインストールされるのを待つ](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/)こともできます。 

この記事では、 **Windows Mixed reality のヘッドセットのお客様に、新しい Microsoft Edge から期待されることを知らせ、Windows Mixed reality での web 閲覧エクスペリエンスを向上させる保留中の更新**について通知します。

## <a name="introducing-the-new-microsoft-edge"></a>新しい Microsoft Edge の紹介

新しい Microsoft Edge は、 [Chromium のオープンソースプロジェクト](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) をデスクトップ上に採用しているため、より優れた web 互換性をユーザーに提供し、すべての web 開発者が web の断片化を減らすことができます。 また、WebVR の代わりに、VR ヘッドセット用のイマーシブ web エクスペリエンスを作成するための新しい標準である WebXR at launch もサポートします。

>[!IMPORTANT]
>Microsoft Edge を最新の Windows 10 デバイスにインストールすると、PC 上の以前の (レガシ) バージョンが置き換えられます。

## <a name="getting-ready-for-the-new-microsoft-edge"></a>新しい Microsoft Edge の準備

Mixed reality ホームで新しい Microsoft Edge を使用する windows Mixed Reality VR ヘッドセットのお客様は、mixed reality ホームで **Win32 アプリケーション (新しい Microsoft edge など) をネイティブでサポートするために、windows 10 バージョン1903以降にアップグレード** する必要があります。 Windows Update を確認 [するか、Windows 10 の最新バージョンを手動でインストールして](https://www.microsoft.com/en-us/software-download/windows10)ください。

混合現実のホームで Microsoft Edge エクスペリエンスを最大限に活用するために、windows **10 バージョン 1903 (またはそれ以降) の2020-01 累積的な更新プログラムが適用された新しい Microsoft edge の Windows Mixed reality 最適化の主要**な部分を待機することもお勧めします。これは、1月の最後まで Windows Update で利用可能になります。

>[!IMPORTANT]
>これらの更新を行う前に新しい Microsoft Edge をダウンロードすることを選択した場合は、Windows Mixed Reality でのその動作に関する既知の問題がいくつかあります (下記を参照してください)。

## <a name="known-issues"></a>既知の問題

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Windows 10 バージョン 1903 (またはそれ以降) の2020-01 累積更新プログラムによって解決された既知の問題

- 新しい Microsoft Edge を含む任意の Win32 アプリを起動すると、ヘッドセットの表示が短時間フリーズします。
- Microsoft Edge タイルは、Windows Mixed Reality の [スタート] メニューから消えます ("クラシックアプリ" フォルダーで見つけることができます)。
- 以前の Microsoft Edge からの Windows は、mixed reality ホームの周囲に配置されていますが、使用することはできません。 これらのウィンドウをアクティブ化しようとすると、デスクトップアプリ内で Edge が起動します。
- Mixed reality ホームでハイパーリンクを選択すると、mixed reality ホームではなく、デスクトップで web ブラウザーが起動します。
- Webvr ショーケースアプリは、WebVR がサポートされなくなっても、mixed reality ホームに存在します。
- キーボード起動とビジュアルの全般的な機能強化。

### <a name="monitor-and-input-handling-issues"></a>モニターと入力処理の問題

Windows 10 バージョン 1903 (またはそれ以降) の2020-01 の累積的な更新プログラムを実行した後、仮想モニターは、Windows Mixed Reality セッション中に **表示 > システム >** の [設定] に、汎用的な物理モニターとして表示されます。 一部のお客様 (特に複数の物理モニタを持つもの) は、デスクトップレイアウトと入力処理に関する問題を結果として通知することがあります。

**理由**

Windows [10 月2019更新プログラム](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-may-2019)では、Windows Mixed Reality の従来の Win32 アプリケーションのサポートが導入されました。 このサポートを有効にするには、Win32 アプリケーションをホストするために仮想モニターを作成する必要があります。 新しい Win32 アプリケーションを起動するたびに、別の仮想モニターを作成する必要があります。 残念ながら、仮想モニターの作成は集中的なタスクであり、ヘッドセットの表示が短時間フリーズすることがあります。 お客様は、これが不快で破壊的なエクスペリエンスであるというフィードバックを提供しました。 このフィードバックにより、Win32 アプリケーションの使用量が増えると同時に、Windows Mixed Reality の起動時に3つの仮想モニターを事前に割り当てて、この中断を防止し、ユーザーがヘッドセットの表示を停止せずに最大で3つの Win32 アプリケーションを起動できるようにしました。

**回避策**

私たちは、一部のお客様 (特に複数の物理モニタを持つもの) がこの仮想モニタの事前割り当てを無効にするというフィードバックを受け取りました。 お客様に制御と選択肢を提供するために、次の Windows 更新プログラムで使用できるレジストリキー値の変更を伴う回避策を有効にしました。
- 2020-07 Windows 10 バージョン2004の累積的な更新プログラムのプレビュー (KB4568831)
- 2020-10 Windows 10 バージョン1909の累積的な更新プログラムのプレビュー (KB4580386)
- 2020-10 Windows 10 バージョン1903の累積的な更新プログラムのプレビュー (KB4580386)

>[!NOTE]
>レジストリキー値の変更は、上級ユーザーを対象としています。

>[!WARNING]
>仮想モニタの事前割り当てを無効にすると、Windows Mixed Reality で Win32 アプリケーション (ストリーム、新しい Microsoft Edge、または Google Chrome など) を起動したときにヘッドセットが短時間で表示されることがあります。

仮想モニタの事前割り当てを無効にするには:
1. 上記の Windows 10 の累積的な更新プログラムのプレビューバージョンのいずれかを **Windows Update** 確認し、使用可能な場合は更新プログラムをインストールします ([Windows Update の設定] ページの [ **オプションの更新プログラム** または **詳細オプション** ] に更新プログラムが表示される場合があります)。
2. **レジストリエディター**の起動
3. [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic] に移動します。 \"
4. "PreallocateVirtualMonitors" REG_DWORD が存在しない場合は、[ **Edit > New > DWORD (32 ビット) 値** ] を選択し、名前として preallocatevirtualmonitors を入力して作成します。
5. "PreallocateVirtualMonitors" REG_DWORD が存在する (または作成した) 場合は、エントリをダブルクリックし、[値のデータ] を 1 (既定値) から 0 (ゼロ) に変更します。
    * TRUE-1
    * FALSE-0

事前割り当てではなく、Windows Mixed Reality で Win32 アプリケーションを起動しようとすると、仮想モニターが割り当てられるようになりました。 これをリセットし、仮想モニタの事前割り当てを再び有効にするには、DWORD の "値のデータ" を1に戻します。

### <a name="additional-known-issues"></a>その他の既知の問題

-   Windows Mixed reality で開かれている web サイトは、Mixed reality ポータルが閉じたときに失われます。ただし、Microsoft Edge ウィンドウは、mixed reality ホームに配置された場所に残ります。
- 360 Viewer 拡張機能などの WebXR エクスペリエンスは、ハイブリッド GPU セットアップを使用している Pc では正常に起動しない可能性があります。 グラフィックスカードソフトウェアの既定の GPU として専用 GPU を選択することで、この問題を回避できる場合があります。
-   Microsoft Edge ウィンドウからのオーディオは spatialized ません。
-   **360 Viewer 拡張機能のバージョン 2.3.8**: Windows Mixed Reality で YouTube から360ビデオを開くと、ヘッドセットでビデオがゆがんでしまう可能性があります。 Edge を再起動して、この問題を解決するには、360 Viewer 拡張機能を非表示にする必要があります。 `edge://system/`アドレスバーに「」と入力し、[拡張機能] の横にある**展開**ボタンを選択すると、拡張機能のバージョンを確認できます。
