---
title: Visual Studio を使用した配置とデバッグ
description: Visual Studio を使用して、HoloLens および Windows Mixed Reality 用のアプリをビルド、デバッグ、配置する方法について説明します。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, Mixed Reality, デバッグ, 配置
ms.openlocfilehash: 20bda2cd247f18680d3f9fe95284e238a32e1140
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97529972"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Visual Studio を使用した配置とデバッグ

DirectX と Unity のどちらを使用して Mixed Reality アプリを開発する場合でも、デバッグと配置には Visual Studio が役立ちます。 このセクションでは、次の方法について説明します。
* Visual Studio を使用して、HoloLens または Windows Mixed Reality のイマーシブ ヘッドセットにアプリケーションを配置する。
* Visual Studio に組み込まれている HoloLens エミュレーターを使用する。
* Mixed Reality アプリをデバッグする。

## <a name="prerequisites"></a>前提条件
1. インストール手順については、「[ツールのインストール](../../develop/install-the-tools.md)」を参照してください。
2. Visual Studio で新しいユニバーサル Windows アプリ プロジェクトを作成します。  HoloLens (第 1 世代) の場合は、Visual Studio 2017 以降を使用します。  HoloLens 2 の場合は、Visual Studio 2019 16.2 以降を使用します。 C# と C++ がサポートされています  (または、[Unity でアプリを作成する](../../develop/unity/tutorials/holograms-100.md)ための手順に従ってください)。

## <a name="enabling-developer-mode"></a>開発者モードを有効にする

まず、デバイスで **開発者モード** を有効にして、Visual Studio から接続できるようにします。

### <a name="hololens"></a>HoloLens
1. HoloLens の電源を入れ、デバイスを装着します。
2. [スタート ジェスチャ](../../design/system-gesture.md)を使用して、メイン メニューを開きます。
3. **[Settings]\(設定\)** タイルを選択して、環境でアプリを起動します。
4. **[Update]** (更新) メニュー項目を選択します。
5. **[For developers]** (開発者向け) メニュー項目を選択します。
6. **[開発者モード]** を有効にして [Visual Studio から HoloLens にアプリを配置](using-visual-studio.md)できるようにします。
7. 省略可能: 下にスクロールして **[デバイス ポータル]** も有効にします。これにより、Web ブラウザーから HoloLens 上の [Windows デバイス ポータル](using-the-windows-device-portal.md)に接続できます。

### <a name="windows-pc"></a>Windows PC

PC に接続された Windows Mixed Reality ヘッドセットを使用している場合、PC 上で **[開発者モード]** を有効にする必要があります。
1. **[設定]** に移動します
2. **[更新とセキュリティ]** を選択します
3. **[開発者向け]** を選択します
4. **[開発者モード]** を有効にして、選択した設定の免責事項を読み、[はい] を選択して変更を確定します。

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>Wi-Fi 経由でのアプリの配置 - HoloLens (第 1 世代)
1. アプリに合わせて **[x86]** ビルド構成を選択します</br>
![Visual Studio の [x86] ビルド構成](images/x86setting.png)</br>
2. [配置ターゲット] ドロップダウン メニューで **[リモート マシン]** を選択します</br>
![Visual Studio でのリモート マシンの配置ターゲット](images/remotemachinesetting.png)</br>
3. C++ および JavaScript プロジェクトの場合は、 **[プロジェクト] > [プロパティ] > [構成プロパティ] > [デバッグ]** に移動します。 C# プロジェクトの場合、接続を構成するダイアログが自動的に表示されます。
  a。 **[アドレス]** または **[コンピューター名]** フィールドに、デバイスの IP アドレスを入力します。 IP アドレスは、HoloLens の **[Settings]\(設定\) > [Network & Internet]\(ネットワークとインターネット\) > [Advanced Options]\(詳細オプション\)** で確認します。または、Cortana に「自分の IP アドレスを教えて」と聞くことができます。
  b. 認証モードを **[ユニバーサル (暗号化されていないプロトコル)]** に設定します</br>
  ![Visual Studio の [リモート接続] ダイアログ](images/remotedeploy.png)</br>
4. **[デバッグ] > [デバッグの開始]** を選択して、アプリをデプロイし、デバッグを開始します</br>
![Visual Studio でのデバッグなしの開始](images/deploywithdebugging.png)</br>
5. PC から HoloLens にアプリを初めて配置するときは、PIN の入力を求められます。 後述する「**デバイスのペアリング**」の手順を実行します。

## <a name="deploying-an-app-over-wi-fi---hololens-2"></a>Wi-Fi 経由でのアプリの配置 - HoloLens 2
1. アプリに合わせて **[ARM]** または **[ARM64]** ビルド構成を選択します</br>
![Visual Studio の [ARM64] ビルド構成](images/arm64setting.png)</br>
2. [配置ターゲット] ドロップダウン メニューで **[リモート マシン]** を選択します</br>
![Visual Studio でのリモート マシンの配置ターゲット](images/remotemachinesetting_arm64.png)</br>
3. C++ および JavaScript プロジェクトの場合は、 **[プロジェクト] > [プロパティ] > [構成プロパティ] > [デバッグ]** に移動します。 C# プロジェクトの場合、接続を構成するダイアログが自動的に表示されます。
  a。 **[アドレス]** または **[コンピューター名]** フィールドに、デバイスの IP アドレスを入力します。 IP アドレスは、HoloLens の **[Settings]\(設定\) > [Network & Internet]\(ネットワークとインターネット\) > [Advanced Options]\(詳細オプション\)** で確認します。または、Cortana に「自分の IP アドレスを教えて」と聞くことができます。
  b. 認証モードを **[ユニバーサル (暗号化されていないプロトコル)]** に設定します</br>
  ![Visual Studio の [リモート接続] ダイアログ](images/remotedeploy.png)</br>
4. **[デバッグ] > [デバッグの開始]** を選択して、アプリをデプロイし、デバッグを開始します</br>
![Visual Studio でのデバッグなしの開始](images/deploywithdebugging.png)</br>
5. PC から HoloLens にアプリを初めて配置するときは、PIN の入力を求められます。 後述する「**デバイスのペアリング**」の手順を実行します。

HoloLens IP アドレスが変わった場合は、 **[プロジェクト] > [プロパティ] > [構成プロパティ] > [デバッグ]** に移動して、ターゲット コンピューターの IP アドレスを変更できます。

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>USB 経由での アプリの配置 - HoloLens (第 1 世代)
1. アプリに合わせて **[x86]** ビルド構成を選択します</br>
![Visual Studio の [x86] ビルド構成](images/x86setting.png)</br>
2. [配置ターゲット] ドロップダウン メニューで **[デバイス]** を選択します</br>
![Visual Studio でのデバイスの配置](images/buildsettingsusbdeploy.png)</br>
3. **[デバッグ] > [デバッグの開始]** を選択して、アプリをデプロイし、デバッグを開始します</br>
![Visual Studio でのデバッグなしの開始](images/deploywithdebugging.png)</br>
4. PC から HoloLens にアプリを初めて配置するときは、PIN の入力を求められます。 後述する「**デバイスのペアリング**」の手順を実行します。

## <a name="deploying-an-app-over-usb---hololens-2"></a>USB 経由での アプリの配置 - HoloLens 2

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. アプリに合わせて **[ARM]** または **[ARM64]** ビルド構成を選択します</br>
![Visual Studio の [ARM64] ビルド構成](images/arm64setting.png)</br>
2. [配置ターゲット] ドロップダウン メニューで **[デバイス]** を選択します</br>
![Visual Studio でのデバイスの配置](images/buildsettingsusbdeploy_arm64.png)</br>
3. **[デバッグ] > [デバッグの開始]** を選択して、アプリをデプロイし、デバッグを開始します</br>
![Visual Studio でのデバッグなしの開始](images/deploywithdebugging.png)</br>
4. PC から HoloLens にアプリを初めて配置するときは、PIN の入力を求められます。 後述する「**デバイスのペアリング**」の手順を実行します。

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>アプリのローカル PC への配置 - イマーシブ ヘッドセット

PC または [Mixed Reality シミュレーター](using-the-windows-mixed-reality-simulator.md)に接続する Windows Mixed Reality イマーシブ ヘッドセットを使用するには:
1. アプリに合わせて **[x86]** または **[x64]** ビルド構成を選択します
2. [配置ターゲット] ドロップダウン メニューで **[ローカル コンピューター]** を選択します
3. **[デバッグ] > [デバッグの開始]** を選択して、アプリをデプロイし、デバッグを開始します

## <a name="pairing-your-device"></a>デバイスのペアリング

Visual Studio から HoloLens にアプリを初めて配置するときは、PIN の入力を求められます。 HoloLens 上で、[Settings]\(設定\) アプリを起動して PIN を生成し、 **[Update]\(更新\) > [For Developers]\(開発者向け\)** に移動し、 **[Pair]\(ペアリング\)** をタップします。 HoloLens に PIN が表示されたら、それを Visual Studio に入力します。 ペアリングが完了したら、HoloLens で **[Done]\(完了\)** をタップしてダイアログを閉じます。 この PC は HoloLens とペアリングされたので、アプリを自動的に配置できます。 HoloLens にアプリを配置するために使うすべての PC に対して、これらの手順を繰り返します。

すべてのペアリング済みコンピューターから HoloLens のペアリングを解除するには:
* **[Settings]\(設定\)** アプリを起動し、 **[Update]\(更新\) > [For Developers]\(開発者向け\)** にアクセスして、 **[Clear]\(クリア\)** をタップします。

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>HoloLens (第 1 世代) Emulator へのアプリの配置
1. **[HoloLens エミュレーターをインストール済み](../install-the-tools.md)** であることを確認します。
2. アプリに合わせて **[x86]** ビルド構成を選択します。</br>
![Visual Studio の [x86] ビルド構成](images/x86setting.png)</br>
3. [配置ターゲット] ドロップダウン メニューで **[HoloLens エミュレーター]** を選択します</br>
![Visual Studio のエミュレーター ターゲット](images/deployemulator.png)</br>
4. **[デバッグ] > [デバッグの開始]** を選択して、アプリをデプロイし、デバッグを開始します</br>
![Visual Studio でのデバッグなしの開始](images/deploywithdebugging.png)</br>

## <a name="deploying-an-app-to-the-hololens-2-emulator"></a>HoloLens 2 Emulator へのアプリの配置
1. **[HoloLens エミュレーターをインストール済み](../install-the-tools.md)** であることを確認します。
2. アプリに合わせて **[x86]** または **[x64]** ビルド構成を選択します。</br>
![Visual Studio の [x86] ビルド構成](images/x86setting.png)</br>
3. [配置ターゲット] ドロップダウン メニューで **[HoloLens 2 エミュレーター]** を選択します</br>
![Visual Studio のエミュレーター ターゲット](images/deployemulator2.png)</br>
4. **[デバッグ] > [デバッグの開始]** を選択して、アプリをデプロイし、デバッグを開始します</br>
![Visual Studio でのデバッグなしの開始](images/deploywithdebugging.png)</br>

## <a name="graphics-debugger-for-hololens-1st-gen"></a>HoloLens (第 1 世代) 用グラフィックス デバッガー

Visual Studio グラフィックス診断ツールは、ホログラフィック アプリを作成して最適化するときに役立ちます。 詳細については、[MSDN の「Visual Studio グラフィックス診断」](https://msdn.microsoft.com/library/hh315751.aspx)を参照してください。

**グラフィックス デバッガーを起動するには**
1. 上記の手順に従って、デバイスまたはエミュレーターをターゲットにします
2. **[デバッグ] > [グラフィック] > [診断の開始]** に移動します
3. HoloLens で診断を初めて開始すると、"アクセス拒否" エラーが発生することがあります。 更新されたアクセス許可が反映されるように HoloLens を再起動してから、もう一度やり直してください。

## <a name="profiling"></a>プロファイリング

Visual Studio プロファイリング ツールを使用すると、アプリのパフォーマンスとリソースの使用量を分析できます。 これには、CPU、メモリ、グラフィックス、およびネットワークの使用を最適化するツールが含まれます。 詳細については、[MSDN のデバッグなしで診断ツールを実行する](https://msdn.microsoft.com/library/dn957936.aspx)方法に関する記事を参照してください。

**HoloLens でプロファイリング ツールを開始するには**
1. 上記の手順に従って、デバイスまたはエミュレーターをターゲットにします
2. **[デバッグ] > [デバッグなしで診断ツールを開始]** に移動します
3. 使用するツールを選択します
4. **[スタート]** を選択します
5. HoloLens で診断をデバッグなしで初めて開始すると、"アクセス拒否" エラーが発生することがあります。 更新されたアクセス許可が反映されるように HoloLens を再起動してから、もう一度やり直してください。

## <a name="debugging-an-installed-or-running-app"></a>インストール済みまたは実行中のアプリのデバッグ

Visual Studio を使用して、Visual Studio プロジェクトから配置せずにインストールされたユニバーサル Windows アプリをデバッグできます。 これは、インストール済みのアプリ パッケージをデバッグしたり、既に実行中のアプリをデバッグしたりする場合に便利です。
1. **[デバッグ] -> [その他のデバッグ ターゲット] -> [インストールされているアプリ パッケージのデバッグ]** に移動します
2. HoloLens の場合は **[リモート コンピューター]** ターゲットを選択し、イマーシブ ヘッドセットの場合は **[ローカル コンピューター]** を選択します。
3. デバイスの **[IP アドレス]** を入力します
4. **[ユニバーサル]** 認証モードを選択します
5. このウィンドウには、実行中のアプリと非アクティブなアプリの両方が表示されます。 デバッグするものを選択します。
6. デバッグするコードの種類を選択します ([マネージド]、[ネイティブ]、[混合])
7. **[アタッチ]** または **[開始]** を選択します

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

私たちが用意した Unity 開発チェックポイント体験に従っている場合、読者は配置段階にいます。 ここから、次のトピックを続けることができます。

> [!div class="nextstepaction"]
> [HoloLens エミュレーターへの配置](using-the-hololens-emulator.md)

または、高度なサービスの追加操作に直接移動します。

> [!div class="nextstepaction"]
> [高度なサービス](../../develop/unity/unity-development-overview.md#5-adding-services)

いつでも [Unity 開発チェックポイント](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator)に戻ることができます。

## <a name="see-also"></a>関連項目
* [ツールのインストール](../install-the-tools.md)
* [HoloLens エミュレーターを使用する](using-the-hololens-emulator.md)
* [ユニバーサル Windows プラットフォーム (UWP) アプリのデプロイとデバッグ](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [デバイスを開発用に有効にする](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
