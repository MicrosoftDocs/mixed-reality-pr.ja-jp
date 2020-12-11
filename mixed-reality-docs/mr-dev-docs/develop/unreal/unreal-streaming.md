---
title: Unreal でのストリーミング
description: Unreal での HoloLens 2 へのストリーミングに関するガイド
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, ストリーミング, PC, ホログラフィック アプリのリモート処理, Holographic Remoting Player, ドキュメント, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: 9cbde33ce7238d704d4b24b4afbed9d8306d4e4d
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609333"
---
# <a name="streaming-in-unreal"></a>Unreal でのストリーミング

PC から HoloLens にストリーミングを行うことには、次の 2 つの大きな利点があります。 
* Mixed Reality アプリで PC の演算性能を活用できる。 
* 開発のイテレーション時間を短縮できる。 

最初に、[Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) を HoloLens デバイスにダウンロードする必要があります。 Holographic Remoting Player を使用すると、アプリで次のソースから HoloLens 上のリモート処理プレーヤーに直接ストリーミングできるようになります。

* Unreal Engine エディター
* パッケージ化された Windows 実行可能ファイル 

ストリーミング時には、アプリケーションをデバイス上で実行する場合と同じ HoloLens の機能をほぼすべて利用できます。 これには、[ハンド ジョイント トラッキング](unreal-hand-tracking.md) (HoloLens 2 を使用している場合)、[空間マッピング](unreal-spatial-mapping.md)、[空間アンカー](unreal-spatial-anchors.md)などが含まれます。ただし、こちらの[一覧](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md)に記載されている機能は含まれません。 

> [!NOTE]
> * ストリーミング品質は、ユーザーの Wi-Fi ネットワークの強度に大きく依存します。
> * Holographic Remoting Player では、すべての機能が自動的に有効になります。 ユーザーのアクセス許可が必要な機能 (例: 視線追跡) がストリーミングでは機能しているものの、デバイスでの実行では機能していない場合、プロジェクト設定で適切な機能を有効にしていることをご確認ください。

## <a name="device-support"></a>デバイス サポート

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>ソース</strong></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 第 1 世代</strong></a></td>
        <td><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></td>
        <td><strong>イマーシブ ヘッドセット</strong></td>
    </tr>
     <tr>
        <td>Unreal エディター</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Windows パッケージ</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a>Unreal エディターからのストリーミング

開発者にとって、Unreal エディターから HoloLens デバイスへのストリーミングには、テスト時に大きなメリットがあります。更新プログラムをテストする前に、アプリのビルドとデプロイを待機する必要がなくなるからです。

[ エディターからのストリーミング](tutorials/unreal-uxt-ch6.md#device-only-streaming)の詳細な手順は、チュートリアル シリーズでわかります。

## <a name="streaming-from-a-packaged-windows-executable"></a>パッケージ化された Windows 実行可能ファイルからのストリーミング

Unreal 4.25.1 以降では、パッケージ化された Windows 実行可能ファイルから HoloLens 2 デバイスにアプリをストリーミングできます。 

1. エディター メニューで、 **[ファイル] > [パッケージ プロジェクト] > [Windows]** の順に移動します。 
    * パッケージを保存する場所を選択し、 **[Select Folder]\(フォルダーの選択\)** を選択します。

2. パッケージのビルドが完了したら、HoloLens 2 で **Holographic Remoting Player** を開き、IP アドレスをメモします。 
3. **Holographic Remoting Player** を開いたままにして、コマンド ライン プロンプトで次を実行します。 
    * cd を実行し、パッケージを保存したローカル ディレクトリに移動します。
    * 次のコマンドを入力します。```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```

> [!NOTE]
> プロジェクト設定に含まれるアプリケーション名が、Windows パッケージを作成するために自動的に使用されます。 何らかの理由でこれらが異なる場合は、コマンド プロンプトで Windows 実行可能ファイル名を使用します。

Enter キーを押すと、アプリケーションのストリーミングが開始します。

## <a name="see-also"></a>関連項目

* [Holographic リモート処理のバージョン履歴](../platform-capabilities-and-apis/holographic-remoting-version-history.md)
* [カスタム Holographic リモート処理プレーヤーアプリの作成](../platform-capabilities-and-apis/holographic-remoting-create-player.md)
* [Holographic Remoting を使用したセキュリティで保護された接続の確立](../platform-capabilities-and-apis/holographic-remoting-secure-connection.md)
