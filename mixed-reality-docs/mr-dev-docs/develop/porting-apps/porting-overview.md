---
title: 移植の概要
description: 既存のアプリケーションを混在させて使用するためのさまざまな移植オプションの概要について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 10/02/2020
ms.topic: article
keywords: 移植, unity, ミドルウェア, エンジン, UWP, Win32
ms.openlocfilehash: 074e0792a5ed43bb56b8f337613234efbd166eb7
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443544"
---
# <a name="porting-overview"></a>移植の概要

既存のプロジェクトを混在環境に移植またはアップグレードする場合は、アプリが Unity、Unreal Engine、HoloLens (第1世代)、HoloLens 2、または SteamVR のどちらでビルドされたかによって、いくつかのシナリオが適用されることがあります。 この概要ページには、各プラットフォームとデバイスの現在の推奨事項が含まれています。これらのプロセスが常に変化しているため、必ず確認してください。

まず、 [Unity](#unity) と [unreal](#unreal) の推奨事項のいずれかに基づいてプロジェクトターゲットをセットアップし、次に、1つ以上の移植シナリオに従います。

- [HoloLens (第1世代) から HoloLens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [Windows Mixed Reality ヘッドセット](#windows-mixed-reality-headsets)
- [SteamVR アプリ](#steamvr-applications)
- [2D UWP アプリ](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>推奨されるプロジェクトターゲット

アプリを別のターゲットデバイスに移植するかどうかにかかわらず、プロジェクトを最新の状態に保つことが重要です。 現在の推奨事項については、以下に示すエンジンベースのリソースを参照してください。

### <a name="unity"></a>Unity

Unity を Mixed Reality で開発するための現在の推奨事項は **、従来の XR パッケージを使用した unity 2019 LTS** です。 プロジェクトで Mixed Reality Toolkit を使用している場合は、最新バージョン (現在は **Mrtk-Unity 2.5**) であることを再度確認します。

> [!CAUTION]
> XR SDK はこのバージョンの Unity で使用できますが、現在、Azure 空間アンカーはこのセットアップと互換性がありません。 この推奨事項は、Unity 用 Azure 空間アンカーパッケージの今後のリリースで更新されます。 
> 
> * Azure 空間アンカーが不要な場合は、 [XR 用に Unity プロジェクトを構成](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) し、 [MRTK と XR SDK を使っ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html)てみることができます。
> 
> * 現在プロジェクトで XR SDK を使用していて、Azure 空間アンカーを使用する場合は、XR SDK をアンインストールし、レガシ XR パッケージを再インストールしてプロジェクト設定を元に戻します。


### <a name="unreal"></a>Unreal 

Mixed Reality での Unreal development の現在の推奨事項は、 **Unreal Engine 4.26** です。 プロジェクトで Mixed Reality Toolkit UX ツールが使用されている場合は、最新バージョン (現在は **Uxt 0.10**) を使用していることを確認してください。

## <a name="porting-scenarios"></a>移植のシナリオ

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>HoloLens (第1世代) Unity アプリから HoloLens 2

HoloLens 2 に移植する既存の HoloLens (第1世代) Unity アプリケーションがある場合は、 [hololens 移植](../unity/mrtk-porting-guide.md)に関する記事の手順に従ってください。

### <a name="windows-mixed-reality-headsets"></a>Windows Mixed Reality ヘッドセット

Oculus Rift や HP リバーブ G2 などの他のデバイス用にコンテンツを構築している場合は、ベンダー固有の VR Sdk および可能性のある入力マッピング Api を再ターゲットする必要があります。 Unity と Unreal の両方の移植のシナリオについては、 [イマーシブアプリの移植ガイド](porting-guides.md)に記載されています。

### <a name="steamvr-applications"></a>SteamVR アプリケーション

Windows Mixed Reality ヘッドセット用に更新する SteamVR エクスペリエンスについては、 [steamvr 更新ガイド](updating-your-steamvr-application-for-windows-mixed-reality.md)を参照してください。

### <a name="2d-universal-windows-applications"></a>2D ユニバーサル Windows アプリケーション

Windows Mixed Reality のイマーシブヘッドセットまたは HoloLens に移植する既存の 2D UWP アプリがある場合は、「 [Windows Mixed reality 用の 2D uwp アプリの移植](building-2d-apps.md) 」に記載されている手順に従ってください。

