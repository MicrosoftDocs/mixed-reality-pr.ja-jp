---
title: Unreal でのプロジェクトのアップグレード
description: Unreal プロジェクトでのバージョンのアップグレード手順と非推奨になった API の概要。
author: hferrone
ms.author: jacksonf
ms.date: 11/23/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, ドキュメント, ガイド, 機能, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, 移植, アップグレード
ms.openlocfilehash: 5460ab55c887c44029e956545cf6a549f55716f7
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010623"
---
# <a name="upgrading-projects-in-unreal"></a><span data-ttu-id="fe23c-104">Unreal でのプロジェクトのアップグレード</span><span class="sxs-lookup"><span data-stu-id="fe23c-104">Upgrading projects in Unreal</span></span>

<span data-ttu-id="fe23c-105">Unreal が新しいバージョンに更新されると、非推奨になった関数は、ブループリントをコンパイルするとき、またはプロジェクトをパッケージ化するときに、警告として表示されます。</span><span class="sxs-lookup"><span data-stu-id="fe23c-105">When updating to a new version of Unreal, deprecated functions show up as warnings when compiling blueprints or packaging the project.</span></span>  <span data-ttu-id="fe23c-106">関数は、代わりに使用する必要がある新しい関数が追加されると非推奨になります。</span><span class="sxs-lookup"><span data-stu-id="fe23c-106">Functions are deprecated when a new function has been added that should be used instead.</span></span> 

## <a name="426-upgrades"></a><span data-ttu-id="fe23c-107">4.26 のアップグレード</span><span class="sxs-lookup"><span data-stu-id="fe23c-107">4.26 upgrades</span></span>
 
<span data-ttu-id="fe23c-108">4\.26 では、AR と VR のすべてのプラットフォームがリファクタリングされ、共通のインターフェイスが追加されて、アプリケーションのコードはプラットフォームに依存しなくなったため、通常より多くの警告が表示される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fe23c-108">In 4.26, all AR and VR platforms have been refactored to add common interfaces and keep application code platform agnostic, so you may see more warnings than usual.</span></span>  <span data-ttu-id="fe23c-109">プロジェクトを他のプラットフォームにいっそう簡単に移植できるよう、新しい API に更新することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fe23c-109">Updating to the new APIs is recommended so the project can be more easily ported to other platforms.</span></span>

<span data-ttu-id="fe23c-110">非推奨になった関数と、代わりに使用する関数が、警告メッセージで示されます。</span><span class="sxs-lookup"><span data-stu-id="fe23c-110">Warning messages will show which function has been deprecated and indicate what function to use instead.</span></span>  <span data-ttu-id="fe23c-111">非推奨のすべての関数は、このリリースでは引き続き動作しますが、今後のリリースでは動作しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fe23c-111">All deprecated functions will continue to work for this release but may not work in future releases.</span></span>  <span data-ttu-id="fe23c-112">また、非推奨の関数は、ブループリントで関数を検索したときの一覧にも表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="fe23c-112">Deprecated functions will also no longer be listed when searching for functions in a blueprint.</span></span>

![名前付き ARPin 作成関数のブループリント](images/unreal-porting-img-01.png)

### <a name="425-deprecations"></a><span data-ttu-id="fe23c-114">4.25 で非推奨になったもの</span><span class="sxs-lookup"><span data-stu-id="fe23c-114">4.25 deprecations</span></span>

| <span data-ttu-id="fe23c-115">非推奨になった関数</span><span class="sxs-lookup"><span data-stu-id="fe23c-115">Deprecated function</span></span> | <span data-ttu-id="fe23c-116">新しい関数</span><span class="sxs-lookup"><span data-stu-id="fe23c-116">New function</span></span> |
| --- | --- |
| <span data-ttu-id="fe23c-117">CreateNamedARPin</span><span class="sxs-lookup"><span data-stu-id="fe23c-117">CreateNamedARPin</span></span> | ![ピン コンポーネント関数のブループリント](images/unreal-porting-img-02.png) |
| <span data-ttu-id="fe23c-119">LoadWMRAnchorStoreARPins</span><span class="sxs-lookup"><span data-stu-id="fe23c-119">LoadWMRAnchorStoreARPins</span></span> | ![ローカル ストアから ARPins を読み込む関数のブループリント](images/unreal-porting-img-03.png) |
| <span data-ttu-id="fe23c-121">LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins</span><span class="sxs-lookup"><span data-stu-id="fe23c-121">LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins</span></span> | ![ローカル ストアに ARPin を保存する関数のブループリント](images/unreal-porting-img-04.png) |
| <span data-ttu-id="fe23c-123">RemoveARPinFromWMRAnchorStore</span><span class="sxs-lookup"><span data-stu-id="fe23c-123">RemoveARPinFromWMRAnchorStore</span></span> | ![ローカル ストアから ARPin を削除する関数のブループリント](images/unreal-porting-img-05.png) |
| <span data-ttu-id="fe23c-125">SetEnabledMixedRealityCamera</span><span class="sxs-lookup"><span data-stu-id="fe23c-125">SetEnabledMixedRealityCamera</span></span> | ![有効な XRCamera を設定する関数のブループリント](images/unreal-porting-img-06.png) |
| <span data-ttu-id="fe23c-127">ResizeMixedRealityCamera</span><span class="sxs-lookup"><span data-stu-id="fe23c-127">ResizeMixedRealityCamera</span></span> | ![XRCamera のサイズを変更する関数のブループリント](images/unreal-porting-img-07.png) |
| <span data-ttu-id="fe23c-129">StartCameraCapture</span><span class="sxs-lookup"><span data-stu-id="fe23c-129">StartCameraCapture</span></span> | ![カメラ キャプチャ開始のために ARCapture を切り替える関数のブループリント](images/unreal-porting-img-08.png) |
| <span data-ttu-id="fe23c-131">StopCameraCapture</span><span class="sxs-lookup"><span data-stu-id="fe23c-131">StopCameraCapture</span></span> | ![カメラ キャプチャ停止のために ARCapture を切り替える関数のブループリント](images/unreal-porting-img-09.png) |
| <span data-ttu-id="fe23c-133">StartQRCodeCapture</span><span class="sxs-lookup"><span data-stu-id="fe23c-133">StartQRCodeCapture</span></span> | ![QRコード キャプチャ開始のために ARCapture を切り替える関数のブループリント](images/unreal-porting-img-10.png) |
| <span data-ttu-id="fe23c-135">StopQRCodeCapture</span><span class="sxs-lookup"><span data-stu-id="fe23c-135">StopQRCodeCapture</span></span> | ![QRコード キャプチャ停止のために ARCapture を切り替える関数のブループリント](images/unreal-porting-img-11.png) |
| <span data-ttu-id="fe23c-137">空間マッピングは、以前の 4.25 では自動的に開始されましたが、現在の 4.26 では切り替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe23c-137">Spatial mapping previously automatically started in 4.25, but now needs to be toggled in 4.26.</span></span> | ![空間マッピングを有効にするために ARCapture を切り替える関数のブループリント](images/unreal-porting-img-12.png) |
| <span data-ttu-id="fe23c-139">ShowKeyboard</span><span class="sxs-lookup"><span data-stu-id="fe23c-139">ShowKeyboard</span></span> | <span data-ttu-id="fe23c-140">キーボードはテキスト ウィジェットにフォーカスが設定されると自動的に表示されるため、4.26 では削除されました。</span><span class="sxs-lookup"><span data-stu-id="fe23c-140">Removed in 4.26 since the keyboard automatically shows when a text widget is focused on.</span></span> |
| <span data-ttu-id="fe23c-141">HideKeyboard</span><span class="sxs-lookup"><span data-stu-id="fe23c-141">HideKeyboard</span></span> | <span data-ttu-id="fe23c-142">キーボードはテキスト ウィジェットがフォーカスを失うと自動的に非表示になるため、4.26 では削除されました。</span><span class="sxs-lookup"><span data-stu-id="fe23c-142">Removed in 4.26 since the keyboard will automatically hide when a text widget is unfocused.</span></span> |
| <span data-ttu-id="fe23c-143">SupportsHandTracking</span><span class="sxs-lookup"><span data-stu-id="fe23c-143">SupportsHandTracking</span></span> | ![ハンド トラッキング サポート プロパティのブループリント](images/unreal-porting-img-13.png) |
| <span data-ttu-id="fe23c-145">IsDisplayOpaque</span><span class="sxs-lookup"><span data-stu-id="fe23c-145">IsDisplayOpaque</span></span> | ![IsDisplayOpaque プロパティのブループリント](images/unreal-porting-img-14.png) |
| <span data-ttu-id="fe23c-147">GetHandJointTransform、GetPointerPoseInfo、GetControllerTrackingStatus</span><span class="sxs-lookup"><span data-stu-id="fe23c-147">GetHandJointTransform, GetPointerPoseInfo, GetControllerTrackingStatus</span></span> | ![モーション コントローラーのデータを取得する関数のブループリント](images/unreal-porting-img-15.png) |
| <span data-ttu-id="fe23c-149">GetVersionString</span><span class="sxs-lookup"><span data-stu-id="fe23c-149">GetVersionString</span></span> | ![バージョン文字列を取得する関数のブループリント](images/unreal-porting-img-16.png) |
| <span data-ttu-id="fe23c-151">IsTrackingAvailable</span><span class="sxs-lookup"><span data-stu-id="fe23c-151">IsTrackingAvailable</span></span> | ![IsTrackingAvailable プロパティのブループリント](images/unreal-porting-img-17.png) |
| <span data-ttu-id="fe23c-153">IsButtonClicked、IsButtonDown、IsGrasped、IsSelectPressed</span><span class="sxs-lookup"><span data-stu-id="fe23c-153">IsButtonClicked, IsButtonDown, IsGrasped, IsSelectPressed</span></span> | <span data-ttu-id="fe23c-154">Unreal の入力アクション システムを使用します。</span><span class="sxs-lookup"><span data-stu-id="fe23c-154">Use Unreal’s input action system.</span></span> |
| <span data-ttu-id="fe23c-155">SetFocusPointForFrame</span><span class="sxs-lookup"><span data-stu-id="fe23c-155">SetFocusPointForFrame</span></span> | <span data-ttu-id="fe23c-156">4\.26 では削除されました。</span><span class="sxs-lookup"><span data-stu-id="fe23c-156">Removed in 4.26.</span></span>  <span data-ttu-id="fe23c-157">以前はリモート処理のときの再投影に使用されていましたが、現在は深度の再投影がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="fe23c-157">Previously used for reprojection when remoting, which now supports depth reprojection.</span></span> |

## <a name="426-changes"></a><span data-ttu-id="fe23c-158">4.26 の変更点</span><span class="sxs-lookup"><span data-stu-id="fe23c-158">4.26 changes</span></span>

<span data-ttu-id="fe23c-159">重要な変更点は、Windows Mixed Reality プラグインを起動する場合に、 **[Edit]\(編集\) > [Project Settings]\(プロジェクトの設定\) > [Project]\(プロジェクト\) > [Description]\(説明\) > [Settings]\(設定\)** の **[Start in VR]\(VR で開始\)** が必須であることです。</span><span class="sxs-lookup"><span data-stu-id="fe23c-159">The significant change is that **Start in VR** from **Edit > Project Settings > Project > Description > Settings** is mandatory for starting Windows Mixed Reality plugin.</span></span> <span data-ttu-id="fe23c-160">このパラメーターを指定しない場合、デバイスにホログラムは表示されません。</span><span class="sxs-lookup"><span data-stu-id="fe23c-160">Without that parameter, you will not see your holograms on the device.</span></span>
