---
title: ケーススタディ-HoloSketch の構築、空間レイアウト、および HoloLens 用の UX スケッチアプリ
description: HoloSketch は、holographic エクスペリエンスの構築に役立つ HoloLens 用のデバイス上の空間レイアウトおよび UX スケッチツールです。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, Windows Mixed Reality, スケッチ, アプリ
ms.openlocfilehash: 4cb5b6a0a0e057bafb7820d8893b2561b44a2d7e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686314"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>ケーススタディ-HoloSketch の構築、空間レイアウト、および HoloLens 用の UX スケッチアプリ

HoloSketch は、holographic エクスペリエンスの構築に役立つ HoloLens 用のデバイス上の空間レイアウトおよび UX スケッチツールです。 HoloSketch は、ペアになっている Bluetooth キーボードとマウス、およびジェスチャと音声コマンドで動作します。 HoloSketch の目的は、簡単な視覚エフェクトとイテレーションのための簡単な UX レイアウトツールを提供することです。

![HoloSketch: HoloLens 用の空間レイアウトと UX スケッチアプリ。](images/holosketch-image-01-640px.png)<br>
*HoloSketch: HoloLens 用の空間レイアウトと UX スケッチアプリ*

![シンプルな UX レイアウトツールで、視覚化とイテレーションを簡単に行うことができます。](images/holosketch-image-02.png)<br>
*シンプルな UX レイアウトツールで簡単に視覚化とイテレーションを行う*

## <a name="features"></a>特徴

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>クイックスタディとスケールのプロトタイプのプリミティブ

![プリミティブシェイプの使用](images/holosketch-primitives-giphy.gif)

プリミティブな図形を使用して、クイック massing スタディとスケールプロトタイプを構築します。

### <a name="import-objects-through-onedrive"></a>OneDrive を使用してオブジェクトをインポートする

![オブジェクトのインポート](images/holosketch-importobjects-giphy.gif)

PNG/JPG イメージまたは 3D FBX オブジェクト (Unity でパッケージ化する必要があります) を、OneDrive を通じて mixed reality スペースにインポートします。

### <a name="manipulate-objects"></a>オブジェクトの操作

![オブジェクトの操作](images/manipulate-objects-640px.jpg)

使い慣れた3D オブジェクトインターフェイスを使用して、オブジェクト (移動/回転/スケール) を操作します。

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>Bluetooth、マウス/キーボード、ジェスチャ、音声コマンド

![Bluetooth をサポートする](images/supports-bluetooth-640px.jpg)

HoloSketch では、Bluetooth マウス/キーボード、ジェスチャ、音声コマンドがサポートされています。

## <a name="background"></a>バックグラウンド

### <a name="importance-of-experiencing-your-design-in-the-device"></a>デバイスで設計が発生する重要性

HoloLens 向けに設計する場合は、デバイスで設計を行うことが重要です。 Mixed reality アプリ設計の最大の課題の1つは、特に従来の2D スケッチを通じて、スケール、位置、深さの意味を得るのが難しいことです。

### <a name="cost-of-2d-based-communication"></a>2D ベースの通信のコスト

UX フローとシナリオを効果的に他のユーザーに伝達するために、デザイナーでは、Illustrator、Photoshop、PowerPoint などの従来の2D ツールを使用して、アセットの作成に時間がかかることがあります。 これらの2D デザインでは、多くの場合、3D に変換するための追加の作業が必要になります。 2D から3D への変換では、いくつかのアイデアが失われています。

### <a name="complex-deployment-process"></a>複雑な展開プロセス

Mixed reality は新しいキャンバスであるため、さまざまな設計イテレーションと評価と、その性質によるエラーが含まれます。 Unity や Visual Studio などのツールに慣れていないデザイナーの場合、HoloLens で簡単にまとめることはできません。 通常は、次の手順に従って、デバイス内の 2D/3D アートワークを表示する必要があります。 これは、設計者がアイデアやシナリオを迅速に反復処理するための大きな障壁でした。

![複雑な展開プロセス](images/holosketch-image-03-1000px.png)<br>
*デプロイ プロセス*

### <a name="simplified-process-with-holosketch"></a>HoloSketch を使用した簡素化されたプロセス

HoloSketch では、開発ツールとデバイスポータルのペアリングを使用しなくても、このプロセスを簡略化する必要がありました。 OneDrive を使用すると、ユーザーは簡単に 2D/3D アセットを HoloLens に入れることができます。

![HoloSketch を使用した簡素化されたプロセス](images/holosketch-image-04-1000px.png)<br>
*HoloSketch を使用した簡素化されたプロセス*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>3次元設計の考え方と解決策を奨励する

このツールを使用すると、デザイナーは、真の3次元空間でソリューションを調査できるようになり、2D では動かなくなります。 HoloLens の場合、バックグラウンドは実際の世界であるため、UI の背景を作成することを考える必要はありません。 HoloSketch を使用すると、デザイナーは HoloLens での3D デザインを簡単に調べることができます。

## <a name="get-started"></a>はじめに

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>HoloSketch に2D イメージ (JPG/PNG) をインポートする方法

* JPG/PNG イメージを OneDrive フォルダー ' Documents/HoloSketch ' にアップロードします。
* HoloSketch の OneDrive メニューから、環境内にイメージを選択して配置することができます。

![2D イメージのインポート](images/import-2d-images-1000px.jpg)<br>
*OneDrive を使用してイメージと3D オブジェクトをインポートする*

### <a name="how-to-import-3d-objects-into-holosketch"></a>HoloSketch に3D オブジェクトをインポートする方法

OneDrive フォルダーにアップロードする前に、次の手順に従って、3D オブジェクトを Unity 資産バンドルにパッケージ化してください。 このプロセスを使用して、Maya、映画4D、Microsoft Paint 3D などの3D ソフトウェアから FBX/OBJ ファイルをインポートできます。

>[!IMPORTANT]
>現時点では、資産バンドルの作成は、Unity バージョン 5.4.5 f1 でサポートされています。

1. Unity プロジェクト [' AssetBunlder_Unity '](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity)をダウンロードして開きます。 この Unity プロジェクトには、バンドル資産生成用のスクリプトが含まれています。
2. 新しいオブジェクトを作成します。
3. 内容に基づいて、このオブジェクトにという名前を指定します。
4. [インスペクター] パネルで、[コンポーネントの追加] をクリックし、[Box Collider] を追加します。 

   ![[インスペクター] パネルで、[コンポーネントの追加] をクリックし、[Box Collider] を追加します。](images/holosketch-10a-assetbundles-1000px.png)
   
   ![[インスペクター] パネルで、[コンポーネントの追加] をクリックし、[Box Collider] を追加し #2](images/holosketch-10b-assetbundles-1000px.png)

5. 3D FBX ファイルを [プロジェクト] パネルにドラッグして、インポートします。
6. **新しいユーザーオブジェクトの下** にある [階層] パネルにオブジェクトをドラッグします。

   ![新しいユーザーオブジェクトの下にある [階層] パネルにオブジェクトをドラッグします。](images/holosketch-12-assetbundles-1000px.png)

7. Collider ディメンションがオブジェクトと一致しない場合は、それを調整します。 オブジェクトを **Z 軸** に回転します。

   ![Collider ディメンションがオブジェクトと一致しない場合は調整します。](images/holosketch-13-assetbundles-1000px.png)

8. オブジェクトを [階層] パネルから [プロジェクト] パネルにドラッグし **て、prefab** にします。
9. [インスペクター] パネルの下部にあるドロップダウンリストをクリックし、新しい一意の名前を作成して割り当てます。 次の例では、AssetBundle 名に ' ' を追加して割り当てる方法を示します。 

   ![[インスペクター] パネルの下部にあるドロップダウンをクリックし、新しい一意の名前を割り当てます。](images/holosketch-14-assetbundles-1000px.png)

10. モデルオブジェクトのサムネイル画像を準備します。 
   ![イメージを [プロジェクト] パネルにドラッグし、オブジェクトに使用する名前を割り当てます。](images/holosketch-15-assetbundles-1000px.png)

11. Unity プロジェクトの ' Asset ' フォルダーの下に ' Assetbundles ' という名前のフォルダーを作成します。

12. [アセット] メニューの [Build AssetBundles] を選択して、ファイルを生成します。 
   ![[アセット] メニューの [Build AssetBundles] を選択して、ファイルを生成します。](images/holosketch-15a-assetbundles.png)


13. **生成されたファイルを OneDrive の/Files/Documents/HoloSketch フォルダーにアップロードします。** Asset_unique_name ファイルのみをアップロードします。 マニフェストファイルまたは AssetBundles ファイルをアップロードする必要はありません。 <br>
![ファイル/ドキュメント/HoloSketch/フォルダーにファイルを追加 ](images/holosketch-onedriveupload-1000px.png)
 ![ すると、HoloSketch の OneDrive メニューに追加された3d オブジェクトが表示されます](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>オブジェクトを操作する方法

HoloSketch は、3D ソフトウェアで広く使用されている従来のインターフェイスをサポートしています。 [移動]、[回転]、[ジェスチャとマウスを使用したオブジェクトの拡大/縮小] を使用できます。 音声またはキーボードを使用して、さまざまなモードをすばやく切り替えることができます。

### <a name="object-manipulation-modes"></a>オブジェクトの操作モード

![オブジェクトを操作する方法](images/holosketch-image-06-1000px.png)<br>
*オブジェクトを操作する方法*

### <a name="contextual-and-tool-belt-menus"></a>コンテキストとツールのベルトメニュー

**コンテキストメニューの使用**

ダブルエアタップを押して、コンテキストメニューを開きます。 

メニュー項目:
* **レイアウト画面:** これは 3D grid システムで、複数のオブジェクトをレイアウトし、グループとして管理できます。 レイアウト画面をダブルエアタップして、オブジェクトを追加します。
* **プリミティブ:** Massing の研究には、キューブ、球体、円柱、およびコーンを使用します。
* **OneDrive:** OneDrive メニューを開き、オブジェクトをインポートします。
* **ヘルプ:** ヘルプ画面を表示します。

![コンテキスト メニュー](images/holosketch-image-07.png)<br>
*コンテキスト メニュー*

**ツールベルトメニューの使用**

シーンの移動、回転、拡大/縮小、保存、読み込みは、ツールベルトメニューから行うことができます。 

## <a name="using-keyboard-gestures-and-voice-commands"></a>キーボード、ジェスチャ、音声コマンドの使用

![キーボード、ジェスチャ、音声コマンド](images/holosketch-image-08-1000px.png)<br>
*キーボード、ジェスチャ、音声コマンド*

## <a name="download-the-app"></a>アプリのダウンロード

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Microsoft Store から無料で HoloSketch アプリをダウンロードしてインストールする</a>
</td>
</tr>
</table>

## <a name="known-issues"></a>既知の問題
* 現在、資産バンドルの作成は、 **Unity バージョン 5.4.5 f1** でサポートされています。
* Onedrive のデータの量によっては、OneDrive コンテンツの読み込み中にアプリが停止したかのように表示されることがあります。
* 現在、保存および読み込み機能ではプリミティブオブジェクトのみがサポートされています
* テキスト、サウンド、ビデオ、および写真メニューは、コンテキストメニューで無効になっています
* ツールベルトメニューの [再生] ボタンをクリックすると、操作ギズモがクリアされます。

## <a name="sharing-your-sketches"></a>スケッチを共有する

HoloLens でビデオ記録機能を使用するには、「Cortana、Start/Stop レコーディング」と言ってください。 ボリュームの上下キーを押して、スケッチの画像を撮影します。

## <a name="about-the-authors"></a>著者について

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="../develop/unity/images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>駐車中</b><br>UX デザイナー @Microsoft</td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><b>パトリック Sebring</b><br>向け @Microsoft</td>
</tr>
</table> 
