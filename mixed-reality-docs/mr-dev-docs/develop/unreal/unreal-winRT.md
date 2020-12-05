---
title: Unreal での WinRT
description: Unreal Engine 用の空間オーディオ プラグインの概要。
author: hferrone
ms.author: jacksonf
ms.date: 07/08/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、streaming、リモート処理、mixed reality、開発、作業の開始、機能、新しいプロジェクト、エミュレーター、ドキュメント、ガイド、機能、ホログラム、ゲーム開発、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、WinRT、DLL
ms.openlocfilehash: f9001f3a9e36eb5d8553545f38cf10411bafd64b
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609410"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="4da5e-104">Unreal での WinRT</span><span class="sxs-lookup"><span data-stu-id="4da5e-104">WinRT in Unreal</span></span>

<span data-ttu-id="4da5e-105">HoloLens 開発の過程で、WinRT を使用して機能を作成することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4da5e-105">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="4da5e-106">たとえば、HoloLens アプリケーションでファイルのダイアログを開くには、FileSavePicker ヘッダーファイルに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4da5e-106">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span> <span data-ttu-id="4da5e-107">WinRT は、バージョン4.26 以降の Unreal のビルドシステムでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="4da5e-107">WinRT is supported in Unreal's build system from version 4.26 onwards.</span></span>

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="4da5e-108">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="4da5e-108">Next Development Checkpoint</span></span>

<span data-ttu-id="4da5e-109">実際の開発に取り組んでいない場合は、Mixed Reality プラットフォームの機能と Api を調査しています。</span><span class="sxs-lookup"><span data-stu-id="4da5e-109">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="4da5e-110">ここからは、任意の [トピック](unreal-development-overview.md#3-platform-capabilities-and-apis) に進み、デバイスまたはエミュレーターへのアプリのデプロイに直接ジャンプできます。</span><span class="sxs-lookup"><span data-stu-id="4da5e-110">From here, you can continue to any [topic](unreal-development-overview.md#3-platform-capabilities-and-apis) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4da5e-111">デバイスへの配置</span><span class="sxs-lookup"><span data-stu-id="4da5e-111">Deploying to device</span></span>](unreal-deploying.md)

## <a name="see-also"></a><span data-ttu-id="4da5e-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="4da5e-112">See also</span></span>
* [<span data-ttu-id="4da5e-113">C++/WinRT Api</span><span class="sxs-lookup"><span data-stu-id="4da5e-113">C++/WinRT APIs</span></span>](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="4da5e-114">FileSavePicker クラス</span><span class="sxs-lookup"><span data-stu-id="4da5e-114">FileSavePicker class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="4da5e-115">Unreal サードパーティ製ライブラリ</span><span class="sxs-lookup"><span data-stu-id="4da5e-115">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
