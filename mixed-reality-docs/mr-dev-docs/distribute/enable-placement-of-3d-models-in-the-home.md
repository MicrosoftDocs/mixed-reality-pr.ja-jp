---
title: 家で 3D モデルの配置を有効にする
description: Windows Mixed Reality ホームで、web サイトまたはアプリケーションの3D モデルを配置する方法について説明します。
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D、モデル、ホーム、場所、世界、モデリング、mixed reality ホーム、web、アプリ、mixed reality ヘッドセット、windows mixed reality ヘッドセット、仮想現実ヘッドセット
ms.openlocfilehash: 58da61add35546331ff8199fa20885f9869a9f43
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583806"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>Mixed Reality ホームで 3D モデルの配置を有効にする

> [!NOTE]
> この機能は、 [Windows 10 April 2018 更新プログラム](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)の一部として追加されました。 以前のバージョンの Windows は、この機能と互換性がありません。

[Windows Mixed Reality ホーム](../discover/navigating-the-windows-mixed-reality-home.md)は、アプリケーションを起動する前にユーザーが移動する開始点です。 シナリオによっては、(ホログラムアプリのような) 2D アプリでは、3D モデルを直接混合現実ホームに装飾として配置したり、フル3D でさらに検査したりすることができます。 [ *モデルの追加] プロトコル* を使用すると、web サイトまたはアプリケーションから Windows Mixed Reality ホームに3d モデルを直接送信できます。この場合、 [3d アプリランチャー](3d-app-launcher-design-guidance.md)、2d アプリ、ホログラムのように永続化されます。 

たとえば、スペースを設計するための3D 家具のカタログを表示するアプリケーションを開発している場合は、[ *モデルの追加] プロトコル* を使用して、ユーザーがこれらの3d 家具モデルをカタログから配置できるようにします。 ユーザーは、世界中に、自宅の他のホログラムと同じように、これらの3D モデルの移動、サイズ変更、および削除を行うことができます。 この記事では、ユーザーがアプリまたは web から3D オブジェクトを使用して自分の世界を装飾できるようにするための、 *add model プロトコル* の実装の概要について説明します。

## <a name="device-support"></a>デバイス サポート

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>機能</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
    </tr>
     <tr>
        <td>モデルプロトコルの追加</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="the-basics"></a>基本

Windows Mixed Reality ホームで3D モデルの配置を有効にするには、次の2つの手順を実行します。
1. [3d モデルが Windows Mixed Reality ホームと互換性があることを確認](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)します。
2. アプリケーションまたは web ページで *モデルの追加プロトコル* を実装します (この記事)。

## <a name="implementing-the-add-model-protocol"></a>モデルの *追加プロトコル* の実装

互換性のある [3d モデル](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)を作成したら、任意の web ページまたはアプリケーションから次の URI をアクティブにして、 *add model プロトコル* を実装できます。

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

URI がリモートリソースを指している場合は、自動的にダウンロードされ、ホームに配置されます。 ローカルリソースは、ホームに配置される前に、mixed reality ホームのアプリデータフォルダーにコピーされます。 ユーザーがこの機能をサポートしていない古いバージョンの Windows を実行している可能性がある場合は、ボタンを非表示にするか、可能な場合は無効にすることをお勧めします。 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>ユニバーサル Windows プラットフォームアプリからの *モデルの追加プロトコル* の呼び出し:

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>Web ページから *モデルの追加プロトコル* を呼び出す:

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>イマーシブ (VR) ヘッドセットに関する考慮事項

* イマーシブ (VR) ヘッドセットの場合、[ *モデルの追加] プロトコル* を呼び出す前に Mixed Reality ポータルが実行されている必要はありません。 この場合は、[ *モデルの追加] プロトコル* によって Mixed reality ポータルが起動され、このオブジェクトが、混合現実のホームに到着すると、ヘッドセットが見ている場所に直接配置されます。 
* Mixed Reality ポータルが既に実行されているデスクトップから [ *モデルの追加] プロトコル* を呼び出すときに、ヘッドセットが "起動済み" になっていることを確認します。 そうでない場合、配置は成功しません。 

## <a name="see-also"></a>関連項目

* [Windows Mixed Reality ホームで使用するための3D モデルの作成](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Windows Mixed Reality ホームのナビゲーション](../discover/navigating-the-windows-mixed-reality-home.md)