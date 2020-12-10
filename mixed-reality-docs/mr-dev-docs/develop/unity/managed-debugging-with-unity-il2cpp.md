---
title: Unity IL2CPP を使用したマネージド デバッグ
description: この記事では、Unity IL2CPP UWP プロジェクトでマネージデバッガーを実行する方法について説明します。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity, visual studio, デバッグ, il2cpp, HoloLens, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想 reality ヘッドセット, UWP
ms.openlocfilehash: 4b21e4888e467e6bd5f1938024a1b8312d8ecbcb
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010243"
---
# <a name="managed-debugging-with-unity-il2cpp"></a>Unity IL2CPP を使用したマネージド デバッグ

次の手順に従って、マネージデバッガーを HoloLens と HoloLens 2 用の Unity IL2CPP UWP ビルドにアタッチします。

1. [マルチキャスト](https://en.wikipedia.org/wiki/Multicast)をサポートしているネットワーク上に配置する必要があります。
2. **UWP 発行設定機能** にアクセスし、 **Internetclientserver** と **PrivateNetworkClientServer** を確認します。

    ![UWP 発行設定機能](images/il2cpp-debugging-capabilities.png)

3. Unity UWP ビルド設定を構成します。
    - 開発のビルド
    - スクリプト デバッグ
    - マネージデバッガーを待機する (省略可能)

    ![UWP ビルドの設定](images/il2cpp-debugging-build.png)

4. Unity でビルドします。
5. Visual Studio ソリューションからデバイスにビルドしてデプロイします。 **デバッグ** 構成または **リリース** 構成を使用してビルドする必要があります。 **マスター** 構成によって Unity プロファイラーが無効になり、最適なデバッグができなくなる可能性があります。 必要に応じて、ソリューションの package.appxmanifest の [機能] ボックスの一覧で、 **インターネット (クライアント & サーバー)** と **プライベートネットワーク (クライアント & サーバー)** を確認します。
6. デバイスが PC と同じネットワークに接続されていることを確認し、デバイスでアプリを起動します。
7. デバイスが USB 経由で PC に接続されて **いない** ことを確認します。
8. Unity のスクリプトの1つをダブルクリックし、開いた Visual Studio ソリューションにアクセスして表示と編集を行います。
9. デバッグ-> Unity デバッガーをアタッチします。

    ![Unity デバッガーのアタッチ](images/il2cpp-debugging-attach.png)

10. 一覧からデバイスを選択し、[OK] をクリックして接続します。

    ![デバイス一覧](images/il2cpp-debugging-machines.png)
