---
title: ScreenshotUtility
description: MRTK でスクリーンショット ツールを使用する方法に関するドキュメント
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 開発, MRTK,
ms.openlocfilehash: a1f5e6503244852d79abaf143f8e922ceb1b489c
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/03/2021
ms.locfileid: "101770741"
---
# <a name="screenshot-utility"></a><span data-ttu-id="8b847-104">スクリーンショット ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="8b847-104">Screenshot utility</span></span>

<span data-ttu-id="8b847-105">多くの場合、ドキュメントやプロモーション用の画像のために Unity でスクリーンショットを撮ることは煩雑であり、出力は望ましいものとは言えません。</span><span class="sxs-lookup"><span data-stu-id="8b847-105">Often taking screenshots in Unity for documentation and promotional imagery can be burdensome and the output often looks less than desirable.</span></span> <span data-ttu-id="8b847-106">ここで、`ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) クラスが機能します。</span><span class="sxs-lookup"><span data-stu-id="8b847-106">This is where the `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) class comes into play.</span></span>

<span data-ttu-id="8b847-107">ScreenshotUtility クラスは、Unity エディター内のメニュー項目とパブリック API を使用したスクリーンショットの撮影を支援します。</span><span class="sxs-lookup"><span data-stu-id="8b847-107">The ScreenshotUtility class aides in taking screenshots via menu items and public APIs within the Unity editor.</span></span> <span data-ttu-id="8b847-108">スクリーンショットをさまざまな解像度および無色透明でキャプチャして、画像の合成のポスト処理に簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="8b847-108">Screenshots can be captured at various resolutions and with transparent clear colors for use in easy post compositing of images.</span></span> <span data-ttu-id="8b847-109">スタンドアロン ビルドからスクリーンショットを撮ることは、このツールではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8b847-109">Taking screenshots from a standalone build is not supported by this tool.</span></span>

## <a name="taking-screenshots"></a><span data-ttu-id="8b847-110">スクリーンショットを撮る</span><span class="sxs-lookup"><span data-stu-id="8b847-110">Taking screenshots</span></span>

<span data-ttu-id="8b847-111">スクリーンショットを簡単にキャプチャするには、エディターで、 *[Mixed Reality Toolkit] -> [ユーティリティ] -> [スクリーンショットを撮る]* を選択し、目的のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="8b847-111">Screenshots can be easily capture while in the editor by selecting *Mixed Reality Toolkit->Utilities->Take Screenshot* and then selecting your desired option.</span></span> <span data-ttu-id="8b847-112">再生していないときにキャプチャする場合、ゲーム ウィンドウ タブが表示されていることを確認します。そうしないと、スクリーンショットが保存されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="8b847-112">Make sure to have the game window tab visible if capturing while not playing, or a screenshot may not be saved.</span></span>

<span data-ttu-id="8b847-113">既定では、すべてのスクリーンショットが[一時キャッシュ パス](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html)に保存され、スクリーンショットへのパスが Unity コンソールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8b847-113">By default, all screenshots are saved to your [temporary cache path](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html), the path to the screenshot will be displayed in the Unity console.</span></span>

![スクリーンショット ユーティリティのメニュー項目](../images/screenshot-utility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a><span data-ttu-id="8b847-115">スクリーンショットのキャプチャの例</span><span class="sxs-lookup"><span data-stu-id="8b847-115">Example screenshot capture</span></span>

<span data-ttu-id="8b847-116">下のスクリーンショットは、"*4 倍の解像度 (透明な背景)* " オプションを使用してキャプチャされました。</span><span class="sxs-lookup"><span data-stu-id="8b847-116">The below screenshot was captured with the *"4x Resolution (Transparent Background)"* option.</span></span> <span data-ttu-id="8b847-117">これにより、透明ピクセルとして保存されたクリア カラーで通常表されるピクセルにより高解像度の画像が出力されます。</span><span class="sxs-lookup"><span data-stu-id="8b847-117">This outputs a high-resolution image with whatever pixels normally represented by the clear color saved as transparent pixels.</span></span> <span data-ttu-id="8b847-118">この手法を使用すると、開発者はこの画像を他の画像の上に重ねて、ストアやその他のメディア発信源にアプリケーションを展示できます。</span><span class="sxs-lookup"><span data-stu-id="8b847-118">This technique helps developers showcase their application for the store, or other media outlets, by overlaying this image on top of other imagery.</span></span>

![スクリーンショット ユーティリティのキャプチャ例](../images/screenshot-utility/MRTK_ScreenshotUtility_Example_Capture.png)
