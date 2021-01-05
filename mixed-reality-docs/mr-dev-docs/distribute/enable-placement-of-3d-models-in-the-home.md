---
title: 家で 3D モデルの配置を有効にする
description: Windows Mixed Reality ホームに web サイトまたはアプリケーションの3D モデルを配置する方法
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D、モデル、ホーム、場所、世界、モデリング、mixed reality ホーム、web、アプリ、mixed reality ヘッドセット、windows mixed reality ヘッドセット、仮想現実ヘッドセット
ms.openlocfilehash: ad35e1d010e32c4729b0d0dd58943dabdee86e09
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757810"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a><span data-ttu-id="f4c22-104">Mixed Reality ホームで 3D モデルの配置を有効にする</span><span class="sxs-lookup"><span data-stu-id="f4c22-104">Enable placement of 3D models in the mixed reality home</span></span>

> [!NOTE]
> <span data-ttu-id="f4c22-105">この機能は、 [Windows 10 April 2018 更新プログラム](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)の一部として追加されました。</span><span class="sxs-lookup"><span data-stu-id="f4c22-105">This feature was added as part of the [Windows 10 April 2018 Update](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018).</span></span> <span data-ttu-id="f4c22-106">以前のバージョンの Windows は、この機能と互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="f4c22-106">Older versions of Windows are not compatible with this feature.</span></span>

<span data-ttu-id="f4c22-107">[Windows Mixed Reality ホーム](../discover/navigating-the-windows-mixed-reality-home.md)は、アプリケーションを起動する前にユーザーが移動する開始点です。</span><span class="sxs-lookup"><span data-stu-id="f4c22-107">The [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="f4c22-108">シナリオによっては、(ホログラムアプリのような) 2D アプリでは、3D モデルを直接混合現実ホームに装飾として配置したり、フル3D でさらに検査したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="f4c22-108">In some scenarios, 2D apps (like the Holograms app) enable placement of 3D models directly into the mixed reality home as decorations or for further inspection in full 3D.</span></span> <span data-ttu-id="f4c22-109">[ *モデルの追加] プロトコル* を使用すると、web サイトまたはアプリケーションから Windows Mixed Reality ホームに3d モデルを直接送信できます。この場合、 [3d アプリランチャー](3d-app-launcher-design-guidance.md)、2d アプリ、ホログラムのように永続化されます。</span><span class="sxs-lookup"><span data-stu-id="f4c22-109">The *add model protocol* allows you to send a 3D model from your website or application directly into the Windows Mixed Reality home, where it will persist like [3D app launchers](3d-app-launcher-design-guidance.md), 2D apps, and holograms.</span></span> 

<span data-ttu-id="f4c22-110">たとえば、スペースを設計するための3D 家具のカタログを表示するアプリケーションを開発している場合は、[ *モデルの追加] プロトコル* を使用して、ユーザーがこれらの3d 家具モデルをカタログから配置できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f4c22-110">For example, if you're developing an application that surfaces a catalog of 3D furniture for designing a space, use the *add model protocol* to allow users to place those 3D furniture models from the catalog.</span></span> <span data-ttu-id="f4c22-111">ユーザーは、世界中に、自宅の他のホログラムと同じように、これらの3D モデルの移動、サイズ変更、および削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="f4c22-111">Once placed in the world, users can move, resize, and remove these 3D models just like other holograms in the home.</span></span> <span data-ttu-id="f4c22-112">この記事では、ユーザーがアプリまたは web から3D オブジェクトを使用して自分の世界を装飾できるようにするための、 *add model プロトコル* の実装の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="f4c22-112">This article provides an overview of implementing the *add model protocol* for enabling users to decorate their world with 3D objects from your app or the web.</span></span>

## <a name="device-support"></a><span data-ttu-id="f4c22-113">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="f4c22-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f4c22-114"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="f4c22-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="f4c22-115"><a href="../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="f4c22-115"><a href="../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="f4c22-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="f4c22-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f4c22-117">モデルプロトコルの追加</span><span class="sxs-lookup"><span data-stu-id="f4c22-117">Add model protocol</span></span></td>
        <td><span data-ttu-id="f4c22-118">✔️</span><span class="sxs-lookup"><span data-stu-id="f4c22-118">✔️</span></span></td>
        <td><span data-ttu-id="f4c22-119">✔️</span><span class="sxs-lookup"><span data-stu-id="f4c22-119">✔️</span></span></td>
    </tr>
</table>

## <a name="overview"></a><span data-ttu-id="f4c22-120">概要</span><span class="sxs-lookup"><span data-stu-id="f4c22-120">Overview</span></span>

<span data-ttu-id="f4c22-121">Windows Mixed Reality ホームで3D モデルの配置を有効にするには、次の2つの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="f4c22-121">There are two steps to enabling the placement of 3D models in the Windows Mixed Reality home:</span></span>
1. <span data-ttu-id="f4c22-122">[3d モデルが Windows Mixed Reality ホームと互換性があることを確認](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)します。</span><span class="sxs-lookup"><span data-stu-id="f4c22-122">[Ensure your 3D model is compatible with the Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span></span>
2. <span data-ttu-id="f4c22-123">アプリケーションまたは web ページで *モデルの追加プロトコル* を実装します (この記事)。</span><span class="sxs-lookup"><span data-stu-id="f4c22-123">Implement the *add model protocol* in your application or webpage (this article).</span></span>

## <a name="implementing-the-add-model-protocol"></a><span data-ttu-id="f4c22-124">モデルの *追加プロトコル* の実装</span><span class="sxs-lookup"><span data-stu-id="f4c22-124">Implementing the *add model protocol*</span></span>

<span data-ttu-id="f4c22-125">互換性のある [3d モデル](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)を作成したら、任意の web ページまたはアプリケーションから次の URI をアクティブにして、 *add model プロトコル* を実装できます。</span><span class="sxs-lookup"><span data-stu-id="f4c22-125">Once you have a [compatible 3D model](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), you can implement the *add model protocol* by activating the following URI from any webpage or application:</span></span>

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

<span data-ttu-id="f4c22-126">URI がリモートリソースを指している場合は、自動的にダウンロードされ、ホームに配置されます。</span><span class="sxs-lookup"><span data-stu-id="f4c22-126">If the URI points to a remote resource, then it will automatically be downloaded and placed in the home.</span></span> <span data-ttu-id="f4c22-127">ローカルリソースは、ホームに配置される前に、mixed reality ホームのアプリデータフォルダーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="f4c22-127">Local resources will be copied to the mixed reality home's app data folder before being placed in the home.</span></span> <span data-ttu-id="f4c22-128">ユーザーがこの機能をサポートしていない古いバージョンの Windows を実行している可能性がある場合は、ボタンを非表示にするか、可能な場合は無効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f4c22-128">We recommend designing your experience to account for scenarios where the user might be running an older version of Windows that doesn't support this feature by hiding the button or disabling it if possible.</span></span> 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a><span data-ttu-id="f4c22-129">ユニバーサル Windows プラットフォームアプリからの *モデルの追加プロトコル* の呼び出し:</span><span class="sxs-lookup"><span data-stu-id="f4c22-129">Invoking the *add model protocol* from a Universal Windows Platform app:</span></span>

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

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a><span data-ttu-id="f4c22-130">Web ページから *モデルの追加プロトコル* を呼び出す:</span><span class="sxs-lookup"><span data-stu-id="f4c22-130">Invoking the *add model protocol* from a webpage:</span></span>

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a><span data-ttu-id="f4c22-131">イマーシブ (VR) ヘッドセットに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="f4c22-131">Considerations for immersive (VR) headsets</span></span>

* <span data-ttu-id="f4c22-132">イマーシブ (VR) ヘッドセットの場合、[ *モデルの追加] プロトコル* を呼び出す前に Mixed Reality ポータルが実行されている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f4c22-132">For immersive (VR) headsets, the Mixed Reality Portal doesn't have to be running before invoking the *add model protocol*.</span></span> <span data-ttu-id="f4c22-133">この場合は、[ *モデルの追加] プロトコル* によって Mixed reality ポータルが起動され、このオブジェクトが、混合現実のホームに到着すると、ヘッドセットが見ている場所に直接配置されます。</span><span class="sxs-lookup"><span data-stu-id="f4c22-133">In this case, the *add model protocol* will launch the Mixed Reality Portal and place the object directly where the headset is looking once you arrive in the mixed reality home.</span></span> 
* <span data-ttu-id="f4c22-134">Mixed Reality ポータルが既に実行されているデスクトップから [ *モデルの追加] プロトコル* を呼び出すときに、ヘッドセットが "起動済み" になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f4c22-134">When invoking the *add model protocol* from the desktop with the Mixed Reality Portal already running, ensure that the headset is "awake".</span></span> <span data-ttu-id="f4c22-135">そうでない場合、配置は成功しません。</span><span class="sxs-lookup"><span data-stu-id="f4c22-135">If not, the placement won't succeed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="f4c22-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4c22-136">See also</span></span>

* [<span data-ttu-id="f4c22-137">Windows Mixed Reality ホームで使用するための3D モデルの作成</span><span class="sxs-lookup"><span data-stu-id="f4c22-137">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="f4c22-138">Windows Mixed Reality ホームのナビゲーション</span><span class="sxs-lookup"><span data-stu-id="f4c22-138">Navigating the Windows Mixed Reality home</span></span>](../discover/navigating-the-windows-mixed-reality-home.md)
