---
title: Microsoft Store への発行
description: Unreal Mixed Reality アプリケーションをパッケージ化して認定し、Microsoft Store に公開する方法について説明します。
author: hferrone
ms.author: jacksonf
ms.date: 12/3/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, ドキュメント, ガイド, 機能, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, 発行, 配布, Microsoft Store
ms.openlocfilehash: 41f081f11cdb9ac2fdf96a81bb761a1321d1776f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010022"
---
# <a name="publishing-to-the-microsoft-store"></a>Microsoft Store への発行

Unreal アプリを世界に提供する準備ができたら、Microsoft Store に送信する前に更新する必要があるプロジェクト設定がいくつかあります。 これらの設定にはすべて既定値がありますが、アプリケーションが最適に提供されるよう運用環境向けに変更する必要があります。

## <a name="project-settings-for-the-store-packaging"></a>ストア パッケージ用のプロジェクト設定

1. 最初に、 **[Project Settings]\(プロジェクトの設定\) > [Description]\(説明\)** 選択して、ゲームと発行元の情報を更新します。 
    * **[Game Name]\(ゲーム名\)** は、HoloLens のアプリ タイルに表示されます
    * **[Company Distinguished Name]\(会社の識別名\)** はプロジェクト証明書の生成時に使用され、次の形式にする必要があります。 
        * **CN=<一般名>, O=<組織名>, L=<市区町村等の名前>, S=<都道府県等の名前>, C=<国名>** :

![プロジェクトの設定で説明セクションが展開された Unreal エディターのスクリーンショット](images/unreal-publishing-img-01.png)

2. プロジェクトの設定の **[HoloLens]** セクションを展開し、パッケージ リソースを更新します。  これらのリソース名は、アプリケーションのストア ページに表示されます。

![プロジェクトの設定でパッケージ セクションが展開された Unreal エディターのスクリーンショット](images/unreal-publishing-img-02.png)

3. **[Images]\(画像\)** セクションを展開し、ストア アプリを表すテクスチャで既定のストア画像を更新します。  必要に応じて、 **[3D Logo]\(3D ロゴ\)** チェック ボックスをオンにし、アプリケーション起動時に 3D ライブ キューブとして使用する glb ファイルをアップロードします。

![プロジェクトの設定で画像セクションが展開された Unreal エディターのスクリーンショット](images/unreal-publishing-img-03.png)

4. 最後に、 **[Generate New]\(新規生成\)** を選択して、プロジェクト名と会社の識別名から署名証明書を生成します  
    * ストア画像の透明ピクセルの代わりに表示される **[Tile Background Color]\(タイルの背景色\)** を設定します。
    * リテールでロックされ、開発環境でロック解除されていないデバイスで実行するには、ドロップダウンを展開して **[Use Retail Windows Store Environment]\(リテール Windows ストア環境を使用する\)** を有効にします。

![プロジェクトの設定で証明書生成セクションが展開された Unreal エディターのスクリーンショット](images/unreal-publishing-img-04.png)

## <a name="optional-app-installer"></a>オプションのアプリ インストーラー

アプリ インストーラー ファイルは、 **[Project Settings]\(プロジェクトの設定\) > [HoloLens]** から作成できます。これを使用して、ストアの外部にアプリケーションを配布できます。  **[Should Create App Installer]\(アプリ インストーラーを作成する\)** チェック ボックスをオンにし、ゲームの appxbundle を格納する URL またはネットワーク パスを設定します。  

![プロジェクトの設定でアプリ インストーラー セクションが展開された Unreal エディターのスクリーンショット](images/unreal-publishing-img-05.png)

アプリをパッケージ化すると、appxbundle と appinstaller の両方が生成されます。  appxbundle をインストール URL にアップロードした後、appinstaller を起動してネットワーク上の場所からアプリをインストールします。

## <a name="windows-app-certification-kit"></a>Windows アプリ認定キット

Windows 10 SDK には、ストアへのパッケージのアップロードに影響する可能性がある一般的な問題を検証するための Windows アプリ認定キット (WACK) が付属しています。  WACK は、Windows キットのディレクトリ (通常は次のパスの下) にあります。 

```
C:\Program Files (x86)\Windows Kits\10\App Certification Kit.
```

1. 発行用に appx ファイルをパッケージ化した後、**appcertui.exe** を実行し、プロンプトに従って appx をスキャンします。

![Windows アプリ認定キットで検証対象として選択されているアプリのスクリーンショット](images/unreal-publishing-img-06.png)

2. **[ストア アプリの検証]** を選択します。

![Windows アプリ認定キットでの検証の選択のスクリーンショット](images/unreal-publishing-img-07.png)

3. 上部のセクションで appx を参照し、 **[次へ]** を選択します。

![Windows アプリ認定キットでのテストの選択のスクリーンショット](images/unreal-publishing-img-08.png)

4. **[次へ]** を選択し、テストを実行してレポートを作成します。
    * ホスト PC で実行できるすべての使用可能なテストが、既定で有効になります

![Windows アプリ認定キットでのアプリ検証の進行状況のスクリーンショット](images/unreal-publishing-img-09.png)

5. テストが終了するまで待ちます。 完了すると、最後のウィンドウに合格または不合格の結果が表示されます。これは、保存されたレポートで確認できます。

![Windows アプリ認定キットでの最終的なレポート結果のスクリーンショット](images/unreal-publishing-img-10.png)

## <a name="known-wack-failure-with-425"></a>4\.25 での既知の WACK エラー

HoloLens 向けのパッケージ化の間に一部の x64 バイナリが組み込まれるため、Unreal 4.25 の Windows Mixed Reality プラグインでは WACK が失敗します。 エラーは次のようになります。

![Windows アプリ認定キットでバイナリ アナライザーおよびサポートされている API のために失敗した結果のスクリーンショット](images/unreal-publishing-img-11.png)

問題を修正するには:
1. Unreal プロジェクトを開いて Unreal のインストールまたはソース ディレクトリのルートを参照し、タスク バーの Unreal アイコンを右クリックします。
2. UE4Editor を右クリックし、[properties]\(プロパティ\) を選択して、 **[Location]\(場所\)** エントリのパスを参照します。

```
Open Engine\Plugins\Runtime\WindowsMixedReality\Source\WindowsMixedRealityHMD\WindowsMixedRealityHMD.Build.cs.
```

3. **WindowsMixedRealityHMD.Build.cs** で、**32 行目** を変更します。

```cpp
if(Target.Platform != UnrealTargetPlatform.Win32)
```

を次のように変更します。

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64)

```

4. Unreal を閉じ、プロジェクトを再び開いて、HoloLens を再度パッケージ化します。  WACK を再実行すると、エラーが発生しなくなります。 

## <a name="see-also"></a>関連項目

* [Microsoft Store へのアプリの送信](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [Windows アプリ認定キット](https://developer.microsoft.com/windows/downloads/app-certification-kit)
* [アプリ インストーラー ファイルの手動作成](https://docs.microsoft.com/windows/msix/app-installer/how-to-create-appinstaller-file)