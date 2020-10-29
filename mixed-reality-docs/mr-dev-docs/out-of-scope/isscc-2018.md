---
title: 深度カメラのホワイトペーパー-ISSCC 2018
description: Project Kinect for Azure と次のバージョンの HoloLens で使用される深度カメラについて説明したテクニカルホワイトペーパー。
author: mattzmsft
ms.author: mazeller
ms.date: 7/5/2018
ms.topic: article
keywords: event, iscc, コンピュータービジョン, 研究, kinect, hololens, 深さ, tof
ms.openlocfilehash: b692f9deeb7768e57ab6161b2c356a6610f18ed9
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91691186"
---
# <a name="depth-camera-whitepaper---isscc-2018"></a><span data-ttu-id="b45c5-104">深度カメラのホワイトペーパー-ISSCC 2018</span><span class="sxs-lookup"><span data-stu-id="b45c5-104">Depth camera whitepaper - ISSCC 2018</span></span>

<span data-ttu-id="b45c5-105">**タイトル:** 1Mpixel 65NM Bsi 320MHz DEMODULATED TOF Image センサー3.5 Μm グローバルシャッターピクセルとアナログビン分割</span><span class="sxs-lookup"><span data-stu-id="b45c5-105">**Title:** 1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning</span></span>

<span data-ttu-id="b45c5-106">**共同** 作成者:Cyrus S Bamji、Swati Mehta、Thompson、作成者 Elkhatib、Stefan Wurster、Onur Akkaya、Andrew 給料 Ne、John Godbaz、Mike Fenton、Vijay Rajasekaran、Larry Prather、Satya Nagaraja、Vishali Mogallapu、Dane 雪、Rich McCauley、Mukadam、Iskender Agi、Shaun McCarthy、z Ping Xu、Travis Perry、ウィリアム Qian、Vei-漢字チャン、Prabhu Adepu、Ali Zi Muneeb、Ahmed Mukherjee、Tya Gampell、Sheethal Nayak、Dave Sunil、Kordus Acharya、Lou O'Connor、Pat</span><span class="sxs-lookup"><span data-stu-id="b45c5-106">**Contributors:** Cyrus S Bamji, Swati Mehta, Barry Thompson, Tamer Elkhatib, Stefan Wurster, Onur Akkaya, Andrew Payne, John Godbaz, Mike Fenton, Vijay Rajasekaran, Larry Prather, Satya Nagaraja, Vishali Mogallapu, Dane Snow, Rich McCauley, Mustansir Mukadam, Iskender Agi, Shaun McCarthy, Zhanping Xu, Travis Perry, William Qian, Vei-Han Chan, Prabhu Adepu, Gazi Ali, Muneeb Ahmed, Aditya Mukherjee, Sheethal Nayak, Dave Gampell, Sunil Acharya, Lou Kordus, Pat O'Connor</span></span>

<span data-ttu-id="b45c5-107">**ISSCC 2018 で公開され、Feb 2018 年2月に公開されています。**</span><span class="sxs-lookup"><span data-stu-id="b45c5-107">**Presented at ISSCC 2018 and published in ISSCC Deg. Tech. Papers, Feb 2018.**</span></span>

<span data-ttu-id="b45c5-108">C.</span><span class="sxs-lookup"><span data-stu-id="b45c5-108">C.</span></span> <span data-ttu-id="b45c5-109">Bamji et al.、"1Mpixel 65nm BSI 320MHz デ変調された TOF Image センサー3.5 μm グローバルシャッターピクセルおよびアナログビン分割" ISSCC Deg "</span><span class="sxs-lookup"><span data-stu-id="b45c5-109">Bamji et al., “1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning,” ISSCC Deg.</span></span> <span data-ttu-id="b45c5-110">責任.</span><span class="sxs-lookup"><span data-stu-id="b45c5-110">Tech.</span></span> <span data-ttu-id="b45c5-111">ペーパー、pp 94-95、Feb 2018。</span><span class="sxs-lookup"><span data-stu-id="b45c5-111">Papers, pp. 94-95, Feb 2018.</span></span> <span data-ttu-id="b45c5-112">IEEE 探索リンク: https://ieeexplore.ieee.org/document/8310200/</span><span class="sxs-lookup"><span data-stu-id="b45c5-112">IEEE Explore Link: https://ieeexplore.ieee.org/document/8310200/</span></span>

<span data-ttu-id="b45c5-113">© 2018 IEEE。</span><span class="sxs-lookup"><span data-stu-id="b45c5-113">© 2018 IEEE.</span></span> <span data-ttu-id="b45c5-114">このマテリアルの個人的な使用は許可されています。</span><span class="sxs-lookup"><span data-stu-id="b45c5-114">Personal use of this material is permitted.</span></span> <span data-ttu-id="b45c5-115">IEEE からのアクセス許可は、現在または将来のメディアにおいて、その他のすべての使用について取得する必要があります。これには、広告やプロモーションの目的でこの資料を再発行したり、新しい集団を作成したり、サーバーやリストに再配布したり、その他の作業の著作権を持つコンポーネントを再利用</span><span class="sxs-lookup"><span data-stu-id="b45c5-115">Permission from IEEE must be obtained for all other uses, in any current or future media, including reprinting/republishing this material for advertising or promotional purposes, creating new collective works, for resale or redistribution to servers or lists, or reuse of any copyrighted component of this work in other works.</span></span>

<span data-ttu-id="b45c5-116">**ホワイト**</span><span class="sxs-lookup"><span data-stu-id="b45c5-116">**Whitepaper:**</span></span><br>
<span data-ttu-id="b45c5-117">![ホワイトペーパーのプレビュー](images/depth-camera-isscc.PNG)</span><span class="sxs-lookup"><span data-stu-id="b45c5-117">![Preview of whitepaper](images/depth-camera-isscc.PNG)</span></span><br>
[<span data-ttu-id="b45c5-118">ダウンロード深度カメラのホワイトペーパー</span><span class="sxs-lookup"><span data-stu-id="b45c5-118">Download depth camera whitepaper</span></span>](images/Depth-Camera-ISSCC-2018.pdf)
