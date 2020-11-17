---
title: Unity Visual Studio ソリューションのエクスポートとビルド
description: この記事では、Visual Studio でビルドおよびデプロイできるように、Unity からの mixed reality プロジェクトをエクスポートする方法について説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: unity, visual studio, エクスポート, ビルド, デプロイ, HoloLens, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実ヘッドセット, UWP, 展開
ms.openlocfilehash: 29415fa7d561cab1aec5f0c2c9344fa24b0e8293
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677561"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>Unity Visual Studio ソリューションのエクスポートとビルド

アプリケーションでシステムキーボードを使用しない場合は、アプリケーションで使用されるメモリが少し少なく、起動時間が少し短縮されるため、 *D3D* を使用することをお勧めします。 プロジェクトで TouchScreenKeyboard API を使用してシステムキーボードを使用している場合は、 *XAML* としてエクスポートする必要があります。

## <a name="how-to-export-from-unity"></a>Unity からエクスポートする方法

![Unity のビルド設定](images/unitybuildsettings-300px.png)<br>
*Unity のビルド設定*

1. Unity からプロジェクトをエクスポートする準備ができたら、[**ファイル**] メニューを開き、[**ビルドの設定**] を選択します。
2. [ **開い** ているシーンの追加] をクリックして、ビルドにシーンを追加します。
3. [ **ビルドの設定** ] ダイアログで、HoloLens をエクスポートする次のオプションを選択します。
   * **Platform:** *ユニバーサル Windows プラットフォーム* 、選択した内容を有効にするには、[ **プラットフォームの切り替え** ] を選択してください。
   * **SDK:** *Universal 10*。
   * **UWP ビルドの種類:** *D3D*。
4. **省略可能**: **Unity C# プロジェクト:** 確認済み。

>[!NOTE]
>このチェックボックスをオンにすると、次のことができます。
>* Visual Studio リモートデバッガーでアプリをデバッグします。
>* WinRT Api に IntelliSense を使用しながら、Unity C# プロジェクトのスクリプトを編集します。

5. [**ビルドの設定...** ] ウィンドウで、[プレーヤーの **設定**] を開きます。
6. [ユニバーサル Windows プラットフォーム] タブ **の設定** を選択します。
7. **[XR Settings]\(XR 設定\)** グループを展開します。
8. [ **XR の設定** ] セクションで、[ **サポートさ** れている仮想 reality] チェックボックスをオンにして、新しい **仮想デバイス** の一覧を追加し、 **"Windows Mixed reality"** がサポートされているデバイスとして表示されていることを確認します。
9. [ビルドの **設定** ] ダイアログに戻ります。
10. **[Build]\(ビルド\)** を選択します。
11. 表示された [エクスプローラー] ダイアログボックスで、Unity のビルド出力を保持する新しいフォルダーを作成します。 一般に、"App" というフォルダーに名前を指定します。
12. 新しく作成したフォルダーを選択し、[ **フォルダーの選択**] をクリックします。
13. Unity のビルドが完了すると、Windows エクスプローラーウィンドウが開き、プロジェクトのルートディレクトリが表示されます。 新しく作成したフォルダーに移動します。
14. このフォルダー内にある生成された Visual Studio ソリューションファイルを開きます。

## <a name="when-to-re-export-from-unity"></a>Unity から再エクスポートする場合

Unity からアプリをエクスポートするときに [C# プロジェクト] チェックボックスをオンにすると、すべての Unity スクリプトファイルを含む Visual Studio ソリューションが作成されます。 これにより、Unity から再エクスポートせずにスクリプトを反復処理することができます。 ただし、スクリプトの内容を変更するだけでなく、プロジェクトに変更を加える場合は、Unity から再エクスポートする必要があります。 Unity から再エクスポートする必要のある時間の例を次に示します。
* [プロジェクト] タブでアセットを追加または削除します。
* すべての値は、[インスペクター] タブで変更します。
* [階層] タブでオブジェクトを追加または削除します。
* Unity プロジェクトの設定を変更します

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>Unity Visual Studio ソリューションのビルドと配置

アプリのビルドと配置の残りの部分は、 [Visual Studio](../platform-capabilities-and-apis/using-visual-studio.md)で行われます。 Unity ビルド構成を指定する必要があります。 Unity の名前付け規則は、Visual Studio で通常使用されているものとは異なる場合があります。

|  構成  |  説明 | 
|----------|----------|
|  デバッグ  |  すべての最適化とプロファイラーが有効になります。 スクリプトのデバッグに使用します。 | 
|  Master  |  すべての最適化が有効になり、プロファイラーは無効になります。 ストアにアプリを送信するために使用されます。 | 
|  リリース  |  すべての最適化が有効になり、プロファイラーが有効になります。 アプリのパフォーマンスを評価するために使用されます。 | 

上記の一覧は、Visual Studio プロジェクトを生成する必要がある一般的なトリガーのサブセットです。 一般に、Visual Studio 内から .cs ファイルを編集する場合、Unity 内からプロジェクトを再生成する必要はありません。

## <a name="troubleshooting"></a>トラブルシューティング

Visual Studio プロジェクトで .cs ファイルの編集が認識されない場合は、Unity の [ビルド] メニューから VS プロジェクトを生成するときに、"Unity C# プロジェクト" がチェックされていることを確認してください。
