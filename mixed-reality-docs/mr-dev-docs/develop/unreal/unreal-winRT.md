---
title: Unreal での WinRT
description: HoloLens デバイス向けの Unreal mixed reality アプリでカスタム WinRT 機能を作成および管理する方法について説明します。
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、streaming、リモート処理、mixed reality、開発、作業の開始、機能、新しいプロジェクト、エミュレーター、ドキュメント、ガイド、機能、ホログラム、ゲーム開発、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、WinRT、DLL
ms.openlocfilehash: f32b5b3ddbee2e24e61d08b0a1b887b7b06e6da4
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580403"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="ccdcf-104">Unreal での WinRT</span><span class="sxs-lookup"><span data-stu-id="ccdcf-104">WinRT in Unreal</span></span>

<span data-ttu-id="ccdcf-105">HoloLens 開発の過程で、WinRT を使用して機能を作成することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ccdcf-105">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="ccdcf-106">たとえば、HoloLens アプリケーションでファイルのダイアログを開くには、FileSavePicker ヘッダーファイルに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ccdcf-106">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span> <span data-ttu-id="ccdcf-107">WinRT は、バージョン4.26 以降の Unreal のビルドシステムでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ccdcf-107">WinRT is supported in Unreal's build system from version 4.26 onwards.</span></span>

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="ccdcf-108">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="ccdcf-108">Next Development Checkpoint</span></span>

<span data-ttu-id="ccdcf-109">用意されている Unreal 開発体験に従っている場合、Mixed Reality プラットフォームの機能と API を探索している段階にいます。</span><span class="sxs-lookup"><span data-stu-id="ccdcf-109">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="ccdcf-110">ここからは、任意の [トピック](unreal-development-overview.md#3-advanced-features) に進み、デバイスまたはエミュレーターへのアプリのデプロイに直接ジャンプできます。</span><span class="sxs-lookup"><span data-stu-id="ccdcf-110">From here, you can continue to any [topic](unreal-development-overview.md#3-advanced-features) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ccdcf-111">デバイスへの配置</span><span class="sxs-lookup"><span data-stu-id="ccdcf-111">Deploying to device</span></span>](unreal-deploying.md)

## <a name="see-also"></a><span data-ttu-id="ccdcf-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="ccdcf-112">See also</span></span>

* [<span data-ttu-id="ccdcf-113">C++/WinRT Api</span><span class="sxs-lookup"><span data-stu-id="ccdcf-113">C++/WinRT APIs</span></span>](/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="ccdcf-114">FileSavePicker クラス</span><span class="sxs-lookup"><span data-stu-id="ccdcf-114">FileSavePicker class</span></span>](/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="ccdcf-115">Unreal サードパーティ製ライブラリ</span><span class="sxs-lookup"><span data-stu-id="ccdcf-115">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html)