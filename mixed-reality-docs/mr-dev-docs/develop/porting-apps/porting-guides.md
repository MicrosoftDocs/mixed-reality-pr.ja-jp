---
title: Windows Mixed Reality に VR アプリを移植する
description: 既存のイマーシブアプリケーションを Windows Mixed Reality に移植する手順を説明したチュートリアルです。
author: JBrentJ
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: ポート、unity、unreal、ミドルウェア、エンジン、UWP、Win32、移植、HoloLens ファースト世代、mixed reality ヘッドセット、windows mixed reality ヘッドセット、移行、Windows 10、入力マッピング、
ms.openlocfilehash: 9f3e064c4462fc3d12a23bd94885476bcd2f9466
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2020
ms.locfileid: "96925945"
---
# <a name="porting-vr-apps-to-windows-mixed-reality"></a>Windows Mixed Reality に VR アプリを移植する

Windows 10 には、イマーシブおよび holographic ヘッドセットの直接サポートが含まれています。 Oculus Rift や HTC Naopak など、他のデバイス用にコンテンツを構築した場合は、オペレーティングシステムのプラットフォーム API の上に存在するライブラリに依存関係があります。 既存の Win32 Unity VR アプリを Windows Mixed Reality に導入するには、ベンダー固有の VR Sdk を Unity のクロスベンダ VR Api に再ターゲット使用する必要があります。

## <a name="porting-requirements"></a>移植の要件

大まかに言えば、既存のコンテンツの移植には次の手順が関係します。
1. **PC で Windows 10 の秋の作成者の更新プログラム (16299) が実行されていることを確認します。** 内部からのプレビュービルドを受信することはお勧めできなくなりました。これらのビルドは、mixed reality 開発では最も安定していないためです。
2. **グラフィックスまたはゲームエンジンの最新バージョンにアップグレードします。** ゲームエンジンは、Windows 10 SDK バージョン 10.0.15063.0 (2017 年4月にリリース) 以降をサポートする必要があります。
3. **任意のミドルウェア、プラグイン、またはコンポーネントをアップグレードします。** アプリにコンポーネントが含まれている場合は、最新バージョンにアップグレードすることをお勧めします。
4. **重複する sdk の依存関係を削除** します。 コンテンツがターゲットとしているデバイスによっては、その SDK を削除するか条件付きでコンパイルする必要があります (たとえば、SteamVR)。そのため、代わりに Windows Api を対象にすることができます。
5. **ビルドの問題を解決します。** この時点で、移植の演習は、アプリ、エンジン、およびコンポーネントの依存関係に固有です。

## <a name="common-porting-steps"></a>一般的な移植手順

### <a name="1-make-sure-you-have-the-right-development-hardware"></a>1. 適切な開発ハードウェアがあることを確認します。

[ [ツールのインストール](../install-the-tools.md#immersive-vr-headset-requirements) ] ページに、推奨される開発ハードウェアの一覧が表示されます。

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a>2. Windows 10 の最新のフライトにアップグレードする

Windows Mixed Reality プラットフォームは、まだアクティブな開発中です。 "Windows Insider Fast" のフライトにアクセスするには [、Windows Insider program に参加](https://insider.windows.com/) することをお勧めします。
1. Windows 10 の作成者の[更新プログラム](https://www.microsoft.com/software-download/windows10)をインストールする
2. Windows Insider プログラムに[参加](https://insider.windows.com/)します。
3. [開発者モード](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)を有効にする
4. [**設定 > 更新 & セキュリティ] セクション** で、 [Windows Insider Fast のフライト](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview)に切り替えます。

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a>3. Visual Studio の最新のビルドにアップグレードする
* Visual Studio を使用している場合は、最新のビルドにアップグレードします。
* 「Visual Studio 2019 で [のツールページのインストール」を](../install-the-tools.md#installation-checklist) 参照してください。

### <a name="4-choose-the-correct-adapter"></a>4. 正しいアダプターを選択します
* 2つの Gpu を持つ notebook などのシステムでは、 [正しいアダプターをターゲット](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications)にします。 これは、Unity とネイティブ DirectX アプリに適用されます。 ID3D11Device は、明示的に、または暗黙的に (メディアファンデーション) 機能に対して作成されます。

## <a name="unity-porting-guidance"></a>Unity の移植に関するガイダンス

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a>Unreal の移植に関するガイダンス

> [!IMPORTANT]
> HP リバーブ G2 コントローラーを使用している場合は、追加の入力マッピング手順については、こちらの [記事](../unreal/unreal-reverb-g2-controllers.md) を参照してください。

## <a name="see-also"></a>関連項目
* [Windows Mixed Reality の PC ハードウェアの最小互換性ガイドライン](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Mixed Reality のパフォーマンスについて](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Unity のパフォーマンスに関する推奨事項](../unity/performance-recommendations-for-unity.md)
* [モーション コントローラー](../../design/motion-controllers.md)
* [Unity でのジェスチャとモーション コントローラー](../unity/gestures-and-motion-controllers-in-unity.md)
* [UnityEngine. XR](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR 追跡](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [移植ガイド](porting-guides.md)