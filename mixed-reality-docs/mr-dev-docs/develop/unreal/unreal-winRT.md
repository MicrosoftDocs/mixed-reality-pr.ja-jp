---
title: Unreal での WinRT
description: Unreal Engine 用の空間オーディオ プラグインの概要。
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、streaming、リモート処理、mixed reality、開発、作業の開始、機能、新しいプロジェクト、エミュレーター、ドキュメント、ガイド、機能、ホログラム、ゲーム開発、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、WinRT、DLL
ms.openlocfilehash: f86939ee53b51fad1e31d18f810d92c3d20611f8
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2020
ms.locfileid: "96926070"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="1b5aa-104">Unreal での WinRT</span><span class="sxs-lookup"><span data-stu-id="1b5aa-104">WinRT in Unreal</span></span>

<span data-ttu-id="1b5aa-105">HoloLens 開発の過程で、WinRT を使用して機能を作成することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="1b5aa-105">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="1b5aa-106">たとえば、HoloLens アプリケーションでファイルのダイアログを開くには、FileSavePicker ヘッダーファイルに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b5aa-106">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span> <span data-ttu-id="1b5aa-107">WinRT は、バージョン4.26 以降の Unreal のビルドシステムでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1b5aa-107">WinRT is supported in Unreal's build system from version 4.26 onwards.</span></span>

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="1b5aa-108">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="1b5aa-108">Next Development Checkpoint</span></span>

<span data-ttu-id="1b5aa-109">実際の開発に取り組んでいない場合は、Mixed Reality プラットフォームの機能と Api を調査しています。</span><span class="sxs-lookup"><span data-stu-id="1b5aa-109">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="1b5aa-110">ここからは、任意の [トピック](unreal-development-overview.md#3-platform-capabilities-and-apis) に進み、デバイスまたはエミュレーターへのアプリのデプロイに直接ジャンプできます。</span><span class="sxs-lookup"><span data-stu-id="1b5aa-110">From here, you can continue to any [topic](unreal-development-overview.md#3-platform-capabilities-and-apis) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1b5aa-111">デバイスへの配置</span><span class="sxs-lookup"><span data-stu-id="1b5aa-111">Deploying to device</span></span>](unreal-deploying.md)

## <a name="see-also"></a><span data-ttu-id="1b5aa-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b5aa-112">See also</span></span>
* [<span data-ttu-id="1b5aa-113">C++/WinRT Api</span><span class="sxs-lookup"><span data-stu-id="1b5aa-113">C++/WinRT APIs</span></span>](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="1b5aa-114">FileSavePicker クラス</span><span class="sxs-lookup"><span data-stu-id="1b5aa-114">FileSavePicker class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="1b5aa-115">Unreal サードパーティ製ライブラリ</span><span class="sxs-lookup"><span data-stu-id="1b5aa-115">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
