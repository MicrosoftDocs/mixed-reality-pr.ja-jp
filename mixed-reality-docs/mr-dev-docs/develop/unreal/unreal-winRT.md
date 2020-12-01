---
title: Unreal での WinRT
description: Unreal Engine 用の空間オーディオ プラグインの概要。
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 07/08/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、streaming、リモート処理、mixed reality、開発、作業の開始、機能、新しいプロジェクト、エミュレーター、ドキュメント、ガイド、機能、ホログラム、ゲーム開発、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、WinRT、DLL
ms.openlocfilehash: 722add1601013d206ffface84d3a53cf3a9d89f9
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354447"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="3fe1a-104">Unreal での WinRT</span><span class="sxs-lookup"><span data-stu-id="3fe1a-104">WinRT in Unreal</span></span>

<span data-ttu-id="3fe1a-105">HoloLens 開発の過程で、WinRT を使用して機能を作成することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3fe1a-105">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="3fe1a-106">たとえば、HoloLens アプリケーションでファイルのダイアログを開くには、FileSavePicker ヘッダーファイルに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3fe1a-106">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span> <span data-ttu-id="3fe1a-107">WinRT は、バージョン4.26 以降の Unreal のビルドシステムでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="3fe1a-107">WinRT is supported in Unreal's build system from version 4.26 onwards.</span></span>

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="3fe1a-108">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="3fe1a-108">Next Development Checkpoint</span></span>

<span data-ttu-id="3fe1a-109">私たちが用意した Unreal 開発チェックポイント体験に従っている場合、読者は Mixed Reality プラットフォームの機能と API を探索している段階にいます。</span><span class="sxs-lookup"><span data-stu-id="3fe1a-109">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="3fe1a-110">ここから、任意の [トピック](unreal-development-overview.md#3-platform-capabilities-and-apis) に進み、デバイスまたはエミュレーターへのアプリのデプロイに直接進むことができます。</span><span class="sxs-lookup"><span data-stu-id="3fe1a-110">From here, you can proceed to any [topic](unreal-development-overview.md#3-platform-capabilities-and-apis) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3fe1a-111">デバイスへの配置</span><span class="sxs-lookup"><span data-stu-id="3fe1a-111">Deploying to device</span></span>](unreal-deploying.md)

## <a name="see-also"></a><span data-ttu-id="3fe1a-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="3fe1a-112">See also</span></span>
* [<span data-ttu-id="3fe1a-113">C++/WinRT Api</span><span class="sxs-lookup"><span data-stu-id="3fe1a-113">C++/WinRT APIs</span></span>](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="3fe1a-114">FileSavePicker クラス</span><span class="sxs-lookup"><span data-stu-id="3fe1a-114">FileSavePicker class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="3fe1a-115">Unreal サードパーティ製ライブラリ</span><span class="sxs-lookup"><span data-stu-id="3fe1a-115">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
