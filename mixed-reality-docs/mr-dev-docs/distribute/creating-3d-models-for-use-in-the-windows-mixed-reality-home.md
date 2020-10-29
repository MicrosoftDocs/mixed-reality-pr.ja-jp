---
title: 家で使用する 3D モデルの作成
description: HoloLens とイマーシブ (VR) ヘッドセットの両方で Windows Mixed Reality ホームで使用される3D モデルの資産要件と作成ガイダンス。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: 3D, モデリング, モデリングガイダンス, 資産要件, 作成ガイドライン, ランチャー, 3D ランチャー, テクスチャ, マテリアル, 複雑さ, 三角形, メッシュ, 多角形, polycount, 制限
ms.openlocfilehash: 606726b9c205ccdf3eacafca96b2bd9ccae43e82
ms.sourcegitcommit: 838bebf6bacac4047feff493c0847d4e6371976f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2020
ms.locfileid: "91781557"
---
# <a name="create-3d-models-for-use-in-the-home"></a>家で使用する 3D モデルの作成

[Windows Mixed Reality ホーム](../discover/navigating-the-windows-mixed-reality-home.md)は、アプリケーションを起動する前にユーザーが移動する開始点です。 Windows Mixed Reality ヘッドセット用のアプリケーションを設計して、 [アプリランチャーとして3d モデル](implementing-3d-app-launchers.md) を活用し、アプリ内から [3d ディープリンクを windows mixed reality ホームに配置](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles) できるようにすることができます。 この記事では、Windows Mixed Reality ホームと互換性のある3D モデルを作成するためのガイドラインの概要を示します。

## <a name="asset-requirements-overview"></a>資産要件の概要
Windows Mixed Reality の3D モデルを作成する場合、すべての資産が満たす必要がある要件がいくつかあります。 
1. [エクスポート](#exporting-models) -アセットは、glb ファイル形式で配信する必要があります (バイナリ gltf)
2. [モデリング](#modeling-guidelines) -資産は10,000 三角形未満、64ノード以下、LOD あたり 32 submeshes が必要です。
3. [素材](#material-guidelines) -テクスチャを 4096 x 4096 より大きくすることはできません。また、どちらの次元でも最小の mip マップを4より大きくすることはできません
4. [アニメーション](#animation-guidelines) -アニメーションは 30 FPS (36000 キーフレーム) で20分より長くすることはできず、<= 8192 の変形ターゲット頂点を含める必要があります
5. [最適化](#optimizations) -アセットは [Windowsmrassetconverter](https://github.com/Microsoft/glTF-Toolkit/releases)を使用して最適化する必要があります。 これは、 **WINDOWS Os バージョン <= 1709** であり、windows os バージョン >= 1803 で推奨されています。

この記事の残りの部分では、これらの要件の詳細な概要と、モデルが Windows Mixed Reality ホームと適切に連携するようにするための追加のガイドラインを示します。 

## <a name="detailed-guidance"></a>詳細なガイダンス

### <a name="exporting-models"></a>モデルのエクスポート

Windows Mixed Reality ホームでは、埋め込み画像とバイナリデータを使用して、glb ファイル形式を使用して3D アセットを配信することを想定しています。 Glb は、Khronos グループによって管理される3D 資産配信用のロイヤリティフリーオープン標準である glTF 形式のバイナリバージョンです。 GlTF は相互運用可能な3D コンテンツの業界標準として進化しているため、Microsoft は Windows アプリとエクスペリエンス全体の形式をサポートしています。 Gltf 資産を作成していない場合は、glTF 作業グループの github ページで [サポートされているエクスポーターとコンバーターの一覧](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) を見つけることができません。  

### <a name="modeling-guidelines"></a>モデリングガイドライン

Windows では、Mixed Reality ホームエクスペリエンスとの互換性を確保するために、次のモデリングガイドラインを使用して資産を生成する必要があります。 選択したプログラムでモデリングする場合は、次の推奨事項と制限事項に留意してください。
1. 上の軸を "Y" に設定する必要があります。
2. 資産は正の Z 軸に "進む" ようになります。
3. すべての資産は、シーンの原点 (0, 0, 0) にある地上平面上に構築する必要があります。
4. 資産を世界規模で作成できるように、作業単位を [メーターと資産] に設定する必要があります。
5. すべてのメッシュを結合する必要はありませんが、リソースの制限付きデバイスを対象とする場合に推奨されます。
6. すべてのメッシュは1つの素材を共有する必要があり、1つのテクスチャセットのみが資産全体に使用されます。
7. UVs は、0-1 のスペースでの正方形の配置でレイアウトする必要があります。 テクスチャは許可されていますが、タイルのタイルは避けてください。
8. マルチ UVs はサポートされていません
9. 両面の素材はサポートされていません

### <a name="triangle-counts-and-levels-of-detail-lods"></a>三角形の数と詳細レベル (LODs)

Windows Mixed Reality ホームでは、1万を超える三角形のモデルはサポートされていません。 エクスポートする前にメッシュを三角形して、この数を超えないようにすることをお勧めします。 Windows MR では、パフォーマンスと高品質のエクスペリエンスを実現するために、オプションのジオメトリレベルの詳細 (LODs) もサポートしています。 [WindowsMRAssetConverter は、](https://github.com/Microsoft/glTF-Toolkit/releases) モデルの3つのバージョンを1つの glb モデルに結合するのに役立ちます。 Windows は、モデルが占める画面の大きさに基づいて、どの LOD を表示するかを決定します。 次の推奨される三角形の数では、3つの LOD レベルのみがサポートされます。
<br>

|  LOD レベル  |  推奨される三角形数  |  三角形の最大数 | 
|------|------|------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5,000  |  10,000 | 
|  LOD 2 |  2,500  |  10,000 | 

### <a name="node-counts-and-submesh-limits"></a>ノード数と submesh の制限
Windows Mixed Reality ホームは、64ノード以上のモデル、または LOD あたり 32 submeshes をサポートしていません。 ノードは、シーン内のオブジェクトを定義する [Gltf 仕様](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy) の概念です。 Submeshes は、オブジェクトのメッシュ上の [プリミティブ](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes) の配列で定義されます。 

|  機能 |  説明  |  サポートされる最大数 | ドキュメント |
|------|------|------|------|
|  Nodes |  GlTF シーン内のオブジェクト |  LOD あたり64 | [ここは](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  Submeshes |  すべてのメッシュのプリミティブの合計 |  LOD あたり32 | [ここは](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>マテリアルのガイドライン

テクスチャは、.PBR 金属の粗さワークフローを使用して準備する必要があります。 まず、Albedo、Normal、遮蔽、メタリック、粗さを含むテクスチャの完全なセットを作成します。 Windows Mixed Reality では、4096x4096 までの解像度のテクスチャがサポートされますが、512 x 512 で作成することをお勧めします。 さらに、テクスチャは4の倍数の解像度で作成する必要があります。これは、以下で説明するエクスポート手順のテクスチャに適用される圧縮形式の要件です。 最後に、mip マップまたはテクスチャを生成する場合、最も低い mipmap は最大4×4にする必要があります。
<br>

|  推奨されるテクスチャサイズ  |  テクスチャの最大サイズ | 最小 Mip
|----|----|----|
|  512x512  |  4096x4096 | 最大 4 x 4|

### <a name="albedo-base-color-map"></a>Albedo (基本色) マップ

照明情報のない未加工の色。 このマップには、金属 (メタリックマップの白) と insulator (メタリックマップでは黒) の反射と拡散に関する情報も含まれています。

### <a name="normal"></a>標準

接空間法線マップ

### <a name="roughness-map"></a>粗さマップ

オブジェクトのマイクロサーフェイスについて説明します。 ホワイト1.0 は、黒色の0.0 はスムーズです。 このマップは、傷、指紋、汚れ、汚れなどの表面に実際に説明されているように、資産に最も多くの文字を与えます。

### <a name="ambient-occlusion-map"></a>アンビエントオクルージョンマップ

反射をブロックする occluded light の領域を示す値スケールマップ

### <a name="metallic-map"></a>メタリックマップ

金属があるかどうかをシェーダーに指示します。 未加工メタル = 1.0 ホワイトメタル非金属 = 0.0 ブラック。 未加工の金属をカバーしているものを示すグレーの推移的な値がありますが、通常、このマップは黒と白のみである必要があります。

## <a name="optimizations"></a>最適化

Windows Mixed Reality ホームには、カスタム拡張機能を使用して定義された核となる glTF 仕様に加えて、一連の最適化が用意されています。 これらの最適化は、Windows バージョン <= 1709 であり、新しいバージョンの Windows で推奨されます。 GitHub で提供されている [Windows Mixed Reality アセットコンバーター](https://github.com/Microsoft/glTF-Toolkit/releases)を使用して、任意の gltf 2.0 モデルを簡単に最適化できます。 このツールでは、次に示すように、正しいテクスチャパッキングと最適化が実行されます。 一般的な使用方法として、WindowsMRAssetConverter を使用することをお勧めしますが、エクスペリエンスをより細かく制御する必要があり、独自の最適化パイプラインを作成する必要がある場合は、以下の詳細な仕様を参照できます。  

### <a name="materials"></a>素材

混合環境での資産の読み込み時間を向上させるために、Windows MR は、このセクションで定義されているテクスチャパッキングスキームに従ってパックされた、圧縮された DDS テクスチャのレンダリングをサポートします。 DDS テクスチャは、 [MSFT_texture_dds 拡張機能](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds)を使用して参照されます。 テクスチャを圧縮することを強くお勧めします。 

#### <a name="hololens"></a>HoloLens

HoloLens ベースの mixed reality エクスペリエンスでは、次のパッキング仕様を使用して2テクスチャ設定を使用してテクスチャがパックされることを想定しています。
<br>

|  glTF プロパティ  |  テクスチャ  |  パッキングスキーム | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  赤 (R)、緑 (G)、青 (B) | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalRoughnessMetallicTexture  |  通常 (RG)、粗さ (B)、メタリック (A) | 


DDS テクスチャを圧縮する場合、各マップで次の圧縮が想定されます。
<br>

|  テクスチャ  |  予想される圧縮 | 
|------|------|
|  baseColorTexture, normalRoughnessMetallicTexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>イマーシブ (VR) ヘッドセット

イマーシブ (VR) ヘッドセットのための PC ベースの Windows Mixed Reality エクスペリエンスでは、次のパッキング仕様を使用して3テクスチャ設定を使用してテクスチャがパックされることを想定しています。

##### <a name="windows-os--1803"></a>Windows OS >= 1803

<br>

|  glTF プロパティ  |  テクスチャ  |  パッキングスキーム | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  赤 (R)、緑 (G)、青 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  occlusionRoughnessMetallicTexture  |  遮蔽 (R)、粗さ (G)、メタリック (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  標準 (RG) | 

DDS テクスチャを圧縮する場合、各マップで次の圧縮が想定されます。
<br>

|  テクスチャ  |  予想される圧縮 | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, occlusionRoughnessMetallicTexture  |  BC7 | 

##### <a name="windows-os--1709"></a>Windows OS <= 1709
<br>

|  glTF プロパティ  |  テクスチャ  |  パッキングスキーム | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  赤 (R)、緑 (G)、青 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessMetallicOcclusionTexture  |  粗さ (R)、メタリック (G)、閉鎖 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  標準 (RG) | 

DDS テクスチャを圧縮する場合、各マップで次の圧縮が想定されます。
<br>

|  テクスチャ  |  予想される圧縮 | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, roughnessMetallicOcclusionTexture | BC7 |

### <a name="adding-mesh-lods"></a>メッシュ LODs の追加

Windows MR では、ジオメトリノード LODs を使用して、画面の範囲に応じてさまざまな詳細レベルで3D モデルを表示します。 この機能は技術的に必須ではありませんが、すべての資産には強くお勧めします。 現在、Windows では3つの詳細レベルがサポートされています。 既定の LOD は0で、これは最高の品質を表します。 その他の LODs には、1、2のように順番に番号が付けられ、品質が徐々に低下しています。 [Windows Mixed Reality 資産コンバーター](https://github.com/Microsoft/glTF-Toolkit/releases)は、複数の gltf モデルを受け入れ、それを有効な LOD レベルで1つの資産にマージすることによって、この LOD 仕様を満たす資産の生成をサポートします。 次の表は、想定される LOD 順序とトライアングルターゲットの概要を示しています。
<br>

|  LOD レベル  |  推奨される三角形数  |  三角形の最大数 | 
|-------|-------|-------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5,000  |  10,000 | 
|  LOD 2 |  2,500  |  10,000 | 

LODs を使用する場合は、常に3つの LOD レベルを指定します。 LODs が見つからないと、LOD システムが不足している LOD レベルに切り替えられるため、モデルが予期せず表示されなくなります。 glTF 2.0 では、現在、コア仕様の一部として LODs をサポートしていません。したがって、この場合は、 [MSFT_LOD 拡張機能](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)を使用して LODs を定義する必要があります。

### <a name="screen-coverage"></a>画面カバレッジ

LODs は、各 LOD に設定された画面カバレッジ値によって制御されるシステムに基づいて、Windows Mixed Reality に表示されます。 現在、画面領域の大きな部分を消費しているオブジェクトは、上位の LOD レベルで表示されます。 画面カバレッジは、核となる glTF 2.0 仕様の一部ではなく、 [MSFT_lod 拡張機能](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)の "エクストラ" セクションの MSFT_ScreenCoverage を使用して指定する必要があります。
<br>

|  LOD レベル  |  推奨される範囲  |  既定の範囲 | 
|-------|-------|-------|
|  LOD 0  |  100%-50% |  .5 | 
|  LOD 1 |  50%-20% 未満  |  0.2 | 
|  LOD 2 |  20%-1% 未満  |  0.01 | 
|  LOD 4  |  1% 未満  |  - | 

## <a name="animation-guidelines"></a>アニメーションのガイドライン

> [!NOTE]
> この機能は、 [Windows 10 April 2018 更新プログラム](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)の一部として追加されました。 以前のバージョンの Windows では、これらのアニメーションは再生されませんが、この記事のガイダンスに従って作成された場合でも読み込まれます。  

Mixed reality ホームでは、HoloLens およびイマーシブ (VR) ヘッドセットでのアニメーション化された glTF オブジェクトがサポートされています。 モデルでアニメーションをトリガーする場合は、glTF 形式でアニメーションマップ拡張機能を使用する必要があります。 この拡張機能を使用すると、世界中のユーザーに基づいて glTF モデルのアニメーションをトリガーできます。たとえば、ユーザーがオブジェクトに近づいたときや、アニメーションを見ているときにアニメーションをトリガーするなどです。 実際に Tf オブジェクトにアニメーションがあり、トリガーが定義されていない場合、アニメーションは再生されません。 以下のセクションでは、これらのトリガーをアニメーション化された glTF オブジェクトに追加するためのワークフローについて説明します。

### <a name="tools"></a>ツール
まず、次のツールをダウンロードします (まだインストールしていない場合)。 これらのツールを使用すると、glTF モデルを開いてプレビューし、変更を加えて、glTF または glb として保存することが簡単になります。
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [Visual Studio Code 用の glTF ツール](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>モデルを開いてプレビューする
まず、VSCode で gltf モデルを開いて、その glTF ファイルをエディターウィンドウにドラッグします。 GlTF ファイルではなく. glb を使用している場合は、ダウンロードした glTF Tools アドオンを使用して VSCode にインポートできます。 [ビュー-> コマンドパレット] にアクセスして、コマンドパレットで「glTF」と入力し、「glTF: Import from glb (glTF: Import from glb)」を選択します。これにより、を使用してをインポートするためのファイルピッカーがポップアップ表示されます。 

GlTF モデルを開いたら、エディターウィンドウに JSON が表示されます。 また、を使用してライブ3D ビューアーでモデルをプレビューすることもできます。そのためには、ファイル名を右クリックし、右クリックメニューから [glTF: Preview 3D Model] コマンドショートカットを選択します。 

### <a name="adding-the-triggers"></a>トリガーの追加
アニメーショントリガーは、アニメーションマップ拡張機能を使用して glTF model JSON に追加されます。 ここでは、アニメーションマップ拡張機能を [GitHub で](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) 公開しています (注: これはドラフト拡張機能です)。 モデルに拡張機能を追加するには、エディターで glTF ファイルの末尾までスクロールし、ファイルがまだ存在しない場合は "extensionsUsed" および "extensions" ブロックを追加します。 "ExtensionsUsed" セクションで、"extensions" ブロックに "EXT_animation_map" 拡張機能への参照を追加し、モデルのアニメーションにマッピングを追加します。

[仕様に](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md)示されているように、アニメーションでは、アニメーションのインデックスの配列である "アニメーション" のリストに "セマンティック" 文字列を使用して、何をトリガーするかを定義します。 次の例では、ユーザーがオブジェクトを使用しているときに再生するアニメーションを指定しています。

```json
  "extensionsUsed": [
    "EXT_animation_map"
  ],
  "extensions" : {
      "EXT_animation_map" : {
            "bindings": [
                {
                    "semantic": "GAZE",
                    "animations": [0]
                }
            ]
      }
  }
```
Windows Mixed Reality ホームでは、次のアニメーショントリガーセマンティクスがサポートされています。  
* "ALWAYS": アニメーションを常にループする
* "保持": オブジェクトが獲得されるまでの間にループします。
* "宝石": オブジェクトの検索中にループしています
* "近接": ビューアーがオブジェクトの近くにある間にループします。
* "ポインティング": ユーザーがオブジェクトをポイントしているときのループ

### <a name="saving-and-exporting"></a>保存とエクスポート
GlTF モデルに変更を加えた後は、glTF として直接保存できます。または、エディターでファイル名を右クリックして [glTF: Export to GLB (バイナリファイル)] を選択し、代わりに GLB をエクスポートすることもできます。 

### <a name="restrictions"></a>制限
アニメーションは20分より長くすることはできず、36000のキーフレーム (30 FPS で20分) を含めることはできません。 また、変形ターゲットベースのアニメーションを使用する場合は、8192の変形ターゲット頂点以下を超えることはありません。 これらの数を超えると、アニメーション化された資産が Windows Mixed Reality ホームでサポートされなくなります。 

|機能|最大値|
|-----|-----|
|Duration|20 分|
|キーフレーム|36,000| 
|変形ターゲット頂点|8192|

## <a name="gltf-implementation-notes"></a>glTF 実装に関する注意事項
Windows MR では、負のスケールを使用した geometry の反転はサポートされていません。 負の目盛りを持つジオメトリでは、ビジュアル成果物が生成される可能性があります。

GlTF 資産は、Windows MR によって表示されるシーン属性を使用して、既定のシーンをポイントする必要があります。 さらに、 [windows 10 の2018年4月の更新](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)より前の windows MR では、アクセサー **が必要です** 。
* 最小値と最大値が必要です。
* 型スカラーは、componentType UNSIGNED_SHORT (5123) または UNSIGNED_INT (5125) である必要があります。
* 型 VEC2 と VEC3 は、componentType FLOAT (5126) である必要があります。

次の素材プロパティは、核となる glTF 2.0 仕様で使用されていますが、必須ではありません。
* baseColorFactor, metallicFactor, roughnessFactor
* baseColorTexture: dds に格納されているテクスチャをポイントする必要があります。
* emissiveTexture: dds に格納されているテクスチャをポイントする必要があります。
* emissiveFactor
* alphaMode

コア仕様では、次の素材プロパティは無視されます。
* すべてのマルチ UVs
* metalRoughnessTexture: 代わりに、次に定義されている Microsoft 最適化されたテクスチャパッキングを使用する必要があります
* normalTexture: 代わりに、次に定義されている Microsoft 最適化テクスチャパッキングを使用する必要があります
* normalScale
* occlusionTexture: 代わりに、次に定義されている Microsoft 最適化されたテクスチャパッキングを使用する必要があります
* occlusionStrength

Windows MR は、プリミティブモードの線とポイントをサポートしていません。 

1つの UV 頂点属性のみがサポートされています。

## <a name="additional-resources"></a>その他の技術情報
* [glTF エクスポーターおよびコンバーター](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [glTF Toolkit](https://github.com/Microsoft/glTF-Toolkit)
* [glTF 2.0 仕様](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Microsoft glTF LOD Extension 仕様](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [PC 混合現実テクスチャパッキング拡張機能の仕様](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [HoloLens Mixed Reality テクスチャパッキング拡張機能の仕様](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Microsoft DDS テクスチャ glTF extensions 仕様](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>関連項目

* [3D アプリ起動ツールの実装 (UWP アプリ)](implementing-3d-app-launchers.md)
* [3D アプリ起動ツールの実装 (Win32 アプリ)](implementing-3d-app-launchers-win32.md)
* [Windows Mixed Reality ホームのナビゲーション](../discover/navigating-the-windows-mixed-reality-home.md)
