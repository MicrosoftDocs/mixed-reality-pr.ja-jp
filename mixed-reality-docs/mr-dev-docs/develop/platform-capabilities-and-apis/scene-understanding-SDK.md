---
title: シーンを理解する SDK
description: コンポーネント、メッシュ、オブジェクトなどのシーン認識 SDK をインストールして使用する方法については、「mixed reality アプリ」を参照してください。
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: シーンの理解、空間マッピング、Windows Mixed Reality、Unity
ms.openlocfilehash: 9520ad604125705c60624254b097de5fc93021ec
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009382"
---
# <a name="scene-understanding-sdk-overview"></a>シーンについて SDK の概要

シーンを理解することで、Mixed Reality デバイスによってキャプチャされた非構造化環境センサーデータが変換され、強力な抽象表現に変換されます。 SDK は、アプリケーションとシーンのランタイムを理解するための通信レイヤーとして機能します。 3D 表現の3D シーングラフや2D アプリケーション用の2D 四角形とパネルなど、既存の標準コンストラクトを模倣することを目的としています。 シーンについての理解を模倣することは、具象フレームワークにマップされますが、一般に SceneUnderstanding はフレームワークに依存しないため、相互にやり取りする多様なフレームワーク間で相互運用性を実現できます。 シーンを理解することは、SDK の役割を進化させることで、新しい表現と機能が統合されたフレームワーク内で引き続き公開されるようにしています。 このドキュメントでは、まず、開発環境や使用状況について理解を深め、特定のクラスと構成要素に関するより詳細なドキュメントを提供するための概要を紹介します。

## <a name="where-do-i-get-the-sdk"></a>SDK はどこで入手できますか?

SceneUnderstanding SDK は NuGet を使用してダウンロードできます。

[SceneUnderstanding SDK](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

**注:** 最新リリースはプレビューパッケージに依存しており、プレリリースパッケージを表示するには、そのパッケージを有効にする必要があります。

バージョン0.5.2022 以降では、シーンの理解によって C# および C++ の言語予測がサポートされるため、アプリケーションは Win32 または UWP プラットフォーム用のアプリケーションを開発できます。 このバージョンでは、SceneUnderstanding は unity でのエディターのサポートをサポートしていません。 SceneObserver は、HoloLens2 との通信にのみ使用されます。 

SceneUnderstanding には Windows SDK バージョン18362以降が必要です。 

Unity プロジェクトで SDK を使用している場合は、 [unity 用の NuGet](https://github.com/GlitchEnzo/NuGetForUnity) を使用して、パッケージをプロジェクトにインストールします。

## <a name="conceptual-overview"></a>概念

### <a name="the-scene"></a>シーン

混合の現実のデバイスは、環境内で認識されている内容に関する情報を常に統合しています。 シーンは、これらすべてのデータソースをじょうごし、1つのまとまりを持つ抽象化を生成します。 シーンについて理解すると、シーンが生成されます。これは、1つの物のインスタンスを表す [SceneObjects](scene-understanding-SDK.md#sceneobjects) の構成です (たとえば、壁面/シーリング/床)。シーンオブジェクト自体は、この SceneObject を構成する粒度の細かい部分を表す [SceneComponents] の合成です。 コンポーネントの例としては、四角形やメッシュなどがありますが、将来的には、境界ボックス、衝突メッシュ、メタデータなどを表すことができます。

生のセンサーデータをシーンに変換するプロセスは、負荷の高い操作である可能性があります。これは、大規模なスペース (~ 10x10m) に対しては数秒 (~ 50x50m) で、デバイスによって計算されているものではありません。 代わりに、必要に応じて、アプリケーションによってシーン生成がトリガーされます。 SceneObserver クラスには、シーンを計算または逆シリアル化できる静的メソッドがあります。このメソッドを使用して、列挙および操作を行うことができます。 "Compute" アクションは要求時に実行され、CPU ではなく、別のプロセス (Mixed Reality ドライバー) で実行されます。 ただし、別のプロセスで計算を行う場合、結果として得られるシーンデータは、アプリケーションのシーンオブジェクトに格納され、保持されます。 

このプロセスフローを示す図を以下に示します。また、2つのアプリケーションの例を示します。 

![プロセス図](images/SU-ProcessFlow.png)

左側には mixed reality ランタイムの図があります。これは常にオンになっており、独自のプロセスで実行されています。 このランタイムは、デバイスの追跡や空間マッピングなどの操作を実行します。また、シーンを理解することで、世界についての理解と理由を理解するために使用されます。 図の右側には、シーンの理解を活用する2つの理論的なアプリケーションが示されています。 最初のアプリケーションインターフェイスである MRTK では、シーンを理解する SDK を内部的に使用します。2つ目のアプリケーションは、2つの異なるシーンインスタンスを計算して使用します。 この図の3つのすべてのシーンでは、個別のインスタンスが生成されます。ドライバーは、アプリケーション間で共有されるグローバル状態を追跡しません。また、シーンオブジェクトが別のシーンで見つからないことを示します。 シーンを理解することは、時間の経過と共に追跡するメカニズムを提供しますが、これは SDK を使用して行われます。 追跡コードは、アプリのプロセスの SDK で既に実行されています。

各シーンでは、アプリケーションのメモリ領域にデータが格納されるため、シーンオブジェクトまたはその内部データのすべての関数がアプリケーションのプロセスで常に実行されると想定できます。

### <a name="layout"></a>レイアウト

シーンの理解を深めるには、ランタイムが論理的および物理的にコンポーネントを表す方法を理解し、理解しておくことが重要な場合があります。 シーンは、主要な改訂を必要とせずに将来の要件を満たすように pliable された、基になる構造を維持しながら、単純なレイアウトを持つデータを表します。 このシーンでは、すべてのコンポーネント (すべてのシーンオブジェクトの構成要素) をフラットリストに格納し、特定のコンポーネントが他のコンポーネントを参照する参照を使用して階層とコンポジションを定義します。

次に、フラットフォームと論理形式の両方で構造体の例を示します。

<table>
<tr><th>論理レイアウト</th><th>物理レイアウト</th></tr>
<tr>
<td>
<ul>
  Scene
  <ul>
  <li>SceneObject_1
    <ul>
      <li>SceneMesh_1</li>
      <li>SceneQuad_1</li>
      <li>SceneQuad_2</li>
    </ul>
  </li>
  <li>SceneObject_2
    <ul>
      <li>SceneQuad_1</li>
      <li>SceneQuad_3</li>
      </li></ul>
  </li>
  <li>SceneObject_3
    <ul>
      <li>SceneMesh_3</li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li>SceneObject_1</li>
  <li>SceneObject_2</li>
  <li>SceneObject_3</li>
  <li>SceneQuad_1</li>
  <li>SceneQuad_2</li>
  <li>SceneQuad_3</li>
  <li>SceneMesh_1</li>
  <li>SceneMesh_2</li>
</ul>
</td>
</tr>
</table>

この図は、シーンの物理的レイアウトと論理的レイアウトの違いを示しています。 左側には、シーンを列挙するときにアプリケーションに表示されるデータの階層型レイアウトが表示されます。 右側には、必要に応じて個別にアクセスできる12個の個別のコンポーネントで構成されているシーンがあることがわかります。 新しいシーンを処理する場合、アプリケーションはこの階層を論理的にウォークすることを想定していますが、シーンの更新間を追跡する場合、一部のアプリケーションは、2つのシーン間で共有される特定のコンポーネントを対象にするだけでよい場合があります。

## <a name="api-overview"></a>API の概要

次のセクションでは、シーンについて理解するための構造の概要について説明します。 このセクションを読むと、シーンの表現方法や、さまざまなコンポーネントがどのように使用されるかについて理解できます。 次のセクションでは、具体的なコード例と、この概要でここしている追加の詳細について説明します。

以下で説明するすべての型は、 `Microsoft.MixedReality.SceneUnderstanding` 名前空間に存在します。

### <a name="scenecomponents"></a>SceneComponents

これで、シーンの論理的なレイアウトを理解できたので、SceneComponents の概念と、階層の作成に使用する方法を提示できるようになりました。 SceneComponents は、メッシュ、クワッド、境界ボックスなど、1つのコアを表す SceneUnderstanding の最も詳細な decompositions です。 SceneComponents は、独立して更新でき、他の SceneComponents が参照できるものです。したがって、この種の追跡/参照メカニズムを可能にする一意の ID を持つ単一のグローバルプロパティを持つことになります。 Id は、シーン階層の論理構成およびオブジェクトの永続化 (あるシーンを別のシーンに更新する操作) に使用されます。 

新しく計算されたすべてのシーンを個別として処理し、その中のすべてのデータを列挙するだけで、Id は主に透過的になります。 ただし、複数の更新プログラムに対してコンポーネントを追跡する予定がある場合は、これらの Id を使用して、シーンオブジェクト間の SceneComponents のインデックス作成と検索を行います。

### <a name="sceneobjects"></a>SceneObjects

SceneObject は、"物" のインスタンスを表す SceneComponent です。たとえば、壁、床、天井、などです...Kind プロパティで表されます。 SceneObjects は幾何学的であるため、空間内の場所を表す関数とプロパティがありますが、ジオメトリックや論理構造は含まれていません。 代わりに、SceneObjects は他の SceneComponents、特に SceneQuads、SceneMeshes を参照しています。これは、システムでサポートされているさまざまな表現を提供します。 新しいシーンが計算されると、ほとんどの場合、アプリケーションは、目的の内容を処理するためにシーンの SceneObjects を列挙します。

SceneObjects は、次のいずれかを持つことができます。

<table>
<tr>
<th>SceneObjectKind</th> <th>説明</th>
</tr>
<tr><td>背景</td><td>SceneObject は、他の認識された種類のシーンオブジェクトの1つでは <b>ない</b> ことがわかっています。 このクラスは、背景が壁、床、天井などではないことがわかっている不明なものと混同しないようにしてください。不明な項目はまだ分類されていません。</b></td></tr>
<tr><td>Wall</td><td>物理的な壁面。 壁面は、移動可能な環境構造であると見なされます。</td></tr>
<tr><td>床</td><td>床は、どのような面でも使用できます。 注: 階段は床ではありません。 また、このフロアは、明らかにできることを前提としています。したがって、1つの床面を明確に想定することはできません。 複数レベルの構造、傾斜など...すべてが floor として分類される必要があります。</td></tr>
<tr><td>Ceiling</td><td>部屋の上面。</td></tr>
<tr><td>プラットフォーム</td><td>ホログラムを配置できる大きな平らなサーフェイス。 これらは、テーブル、countertops、およびその他の大きな水平サーフェスを表す傾向があります。</td></tr>
<tr><td>World</td><td>ラベル付けに依存しないジオメトリックデータ用に予約されたラベル。 EnableWorldMesh update フラグを設定することによって生成されるメッシュは、"世界" として分類されます。</td></tr>
<tr><td>Unknown</td><td>このシーンオブジェクトはまだ分類されていないため、種類が割り当てられています。 これは背景と混同しないようにしてください。このオブジェクトは何でもかまいませんが、システムはまだ十分な量の分類を持っているとは限りません。</td></tr>
</tr>
</table>

### <a name="scenemesh"></a>SceneMesh

SceneMesh は、トライアングルリストを使用して任意のジオメトリックオブジェクトのジオメトリを近似する SceneComponent です。 SceneMeshes は、いくつかの異なるコンテキストで使用されます。 watertight セル構造のコンポーネント、またはシーンに関連付けられた非バインド空間マッピングメッシュを表す WorldMesh として表すことができます。 各メッシュで提供されるインデックスと頂点データは、すべての最新のレンダリング Api で三角形メッシュをレンダリングするために使用される [頂点およびインデックスバッファー](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) と同じ使い慣れたレイアウトを使用します。 シーンの理解では、メッシュは32ビットのインデックスを使用し、特定のレンダリングエンジンのチャンクに分割する必要がある場合があります。

#### <a name="winding-order-and-coordinate-systems"></a>ワインディング順序と座標系

シーンの理解によって生成されるすべてのメッシュは、時計回りのワインディング順序を使用して Right-Handed 座標系でメッシュを返すことが想定されています。 

注: 191105 より前の OS ビルドでは既知のバグが発生する可能性があります。これは、"ワールド" メッシュが Counter-Clockwise ワインディング順序で戻り、その後修正されています。

### <a name="scenequad"></a>SceneQuad

SceneQuad は、3d ワールドを占める2d 表面を表す SceneComponent です。 SceneQuads は ARKit Arkit Eanchor または Arkit プレーンと同様に使用できますが、フラットなアプリや拡張された UX で使用される、より高度な機能を2d キャンバスとして提供します。 2D 固有の Api は、配置とレイアウトを簡単に使用できるようにするための四角形、および (レンダリングを除く) 四角形での開発には3d メッシュよりも2d キャンバスの方が似ています。

#### <a name="scenequad-shape"></a>SceneQuad 図形

SceneQuads は、境界のある四角形の表面を2d で定義します。 ただし、SceneQuads は、任意の複雑な可能性のある図形 (ドーナツの形のテーブルなど) を含むサーフェイスを表します。クワッドの表面の複雑な形状を表すために、GetSurfaceMask API を使用して、指定したイメージバッファーにサーフェイスの形状をレンダリングすることができます。 クワッドを持つ SceneObject にメッシュがある場合、メッシュの三角形は、このレンダリングされたイメージと同じである必要があり、両方とも2d 座標または3d 座標で表面の実際のジオメトリを表します。

## <a name="scene-understanding-sdk-details-and-reference"></a>シーンについて SDK の詳細とリファレンス

次のセクションでは、SceneUnderstanding の基本について説明します。 このセクションでは、サンプルアプリケーションを参照して、SceneUnderstanding がどのように総合的に使用されているかを確認するのに十分なコンテキストがある点について説明します。

### <a name="initialization"></a>初期化

SceneUnderstanding を操作するための最初の手順は、アプリケーションが Scene オブジェクトへの参照を取得することです。 これは、2つの方法のいずれかで実行できます。シーンはドライバーによって計算されるか、過去に計算された既存のシーンを逆シリアル化することができます。 後者は、開発時に SceneUnderstanding を使用する場合に役立ちます。この場合、アプリケーションとエクスペリエンスは、mixed reality デバイスなしで簡単にプロトタイプを作成できます。

シーンは SceneObserver を使用して計算されます。 シーンを作成する前に、アプリケーションがデバイスを照会して、SceneUnderstanding をサポートしていることを確認し、SceneUnderstanding が必要とする情報に対するユーザーアクセスを要求する必要があります。

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

RequestAccessAsync () が呼び出されていない場合、新しいシーンを計算することはできません。 次に、Mixed Reality ヘッドセットを囲む新しいシーンを計算し、10メートルの半径を持ちます。

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-also-known-as-the-pc-path"></a>データからの初期化 (とも呼ばれます。 PC パス)

直接消費するためのシーンは計算できますが、後で使用できるようにシリアル化された形式で計算することもできます。 これは、開発者がデバイスを使用しなくてもシーンの理解を深めることができるように、開発に役立つことが実証されています。 シーンをシリアル化する操作は、それを計算することとほぼ同じです。データは、SDK によってローカルで逆シリアル化されるのではなく、アプリケーションに返されます。 その後、自分で逆シリアル化したり、将来使用するために保存したりすることができます。

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneData for later
```

### <a name="sceneobject-enumeration"></a>SceneObject 列挙型

アプリケーションにシーンが作成されたので、アプリケーションは SceneObjects と対話します。 これを行うには、 **SceneObjects** プロパティにアクセスします。

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-refinding-components"></a>コンポーネントの更新と refinding のコンポーネント

シーン内のコンポーネントを取得する、**_Findcomponent_* _ という別の関数があります。 この関数は、追跡オブジェクトを更新し、後のシーンでそれらを検索する場合に便利です。 次のコードでは、前のシーンに対して相対的な新しいシーンを計算し、新しいシーンでフロアを検索します。

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a>シーンオブジェクトからのメッシュと四角形へのアクセス

SceneObjects が見つかると、ほとんどの場合、アプリケーションは、構成されている四角形やメッシュに含まれるデータにアクセスします。 このデータには、[ _*_四角形_*_ と _*_メッシュ_*_ ] プロパティを使用してアクセスします。 次のコードは、floor オブジェクトのすべての四角形とメッシュを列挙します。

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

これは、シーンオリジンに対して相対的な変換を含む SceneObject であることに注意してください。 これは、SceneObject は "物事" のインスタンスを表し、空間では、四角形とメッシュが親を基準に変換されるジオメトリを表しているためです。 個別の SceneObjects が同じ SceneMesh/SceneQuad SceneComponents を参照している可能性があります。また、SceneObject に複数の SceneMesh/SceneQuad がある可能性もあります。

### <a name="dealing-with-transforms"></a>変換の処理

シーンの理解により、変換を処理するときに、従来の3D シーン表現に合わせて意図的に配置しようとしました。 そのため、各シーンは、最も一般的な3D 環境表現と同じように、1つの座標系に限定されます。 SceneObjects は、その座標系を基準とした相対的な場所を提供します。 アプリケーションが、1つのオリジンが提供する機能の制限を拡大するシーンを処理している場合は、SceneObjects を SpatialAnchors に固定するか、複数のシーンを生成して結合することができますが、わかりやすくするために、watertight のシーンが独自のオリジンに存在することを想定しています。

次の Unity コードは、Windows 認識と Unity Api を使用して、座標系をまとめて配置する方法を示しています。 Unity の世界の出発点に対応する SpatialCoordinateSystem を取得する[方法の詳細につい](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced)ては、「 [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) and [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) 」を参照してください。

```cs
private System.Numerics.Matrix4x4? GetSceneToUnityTransformAsMatrix4x4(SceneUnderstanding.Scene scene)
{

      System.Numerics.Matrix4x4? sceneToUnityTransform = System.Numerics.Matrix4x4.Identity;

      Windows.Perception.Spatial.SpatialCoordinateSystem sceneCoordinateSystem = Microsoft.Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
      HolograhicFrameData holoFrameData =  Marshal.PtrToStructure<HolograhicFrameData>(UnityEngine.XR.XRDevice.GetNativePtr());
      Windows.Perception.Spatial.SpatialCoordinateSystem unityCoordinateSystem = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(holoFrameData.ISpatialCoordinateSystemPtr);

      sceneToUnityTransform = sceneCoordinateSystem.TryGetTransformTo(unityCoordinateSystem);

      if(sceneToUnityTransform != null)
      {
          sceneToUnityTransform = ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
      }
      else
      {
          return null;
      }

    return sceneToUnityTransform;
}
```

それぞれに `SceneObject` 変換があり、そのオブジェクトに適用されます。 Unity では、右きき座標に変換し、次のようにローカル変換を割り当てます。

```cs
private System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 matrix)
{
    matrix.M13 = -matrix.M13;
    matrix.M23 = -matrix.M23;
    matrix.M43 = -matrix.M43;

    matrix.M31 = -matrix.M31;
    matrix.M32 = -matrix.M32;
    matrix.M34 = -matrix.M34;

    return matrix;
}

 private void SetUnityTransformFromMatrix4x4(Transform targetTransform, System.Numerics.Matrix4x4 matrix, bool updateLocalTransformOnly = false)
 {
    if(targetTransform == null)
    {
        return;
    }

    Vector3 unityTranslation;
    Quaternion unityQuat;
    Vector3 unityScale;

    System.Numerics.Vector3 vector3;
    System.Numerics.Quaternion quaternion;
    System.Numerics.Vector3 scale;

    System.Numerics.Matrix4x4.Decompose(matrix, out scale, out quaternion, out vector3);

    unityTranslation = new Vector3(vector3.X, vector3.Y, vector3.Z);
    unityQuat        = new Quaternion(quaternion.X, quaternion.Y, quaternion.Z, quaternion.W);
    unityScale       = new Vector3(scale.X, scale.Y, scale.Z);

    if(updateLocalTransformOnly)
    {
        targetTransform.localPosition = unityTranslation;
        targetTransform.localRotation = unityQuat;
    }
    else
    {
        targetTransform.SetPositionAndRotation(unityTranslation, unityQuat);
    }
}

// Assume we have an SU object called suObject and a unity equivalent unityObject

System.Numerics.Matrix4x4 converted4x4LocationMatrix = ConvertRightHandedMatrix4x4ToLeftHanded(suObject.GetLocationAsMatrix());
SetUnityTransformFromMatrix4x4(unityObject.transform, converted4x4LocationMatrix, true);
        
```

### <a name="quad"></a>Quad

四角形は、2D の配置のシナリオを支援するように設計されており、2D キャンバス UX 要素の拡張機能と考える必要があります。 四角形は SceneObjects のコンポーネントであり、3D でレンダリングできますが、クワッド Api 自体は、四角形が2D 構造体であると想定しています。 エクステントや形などの情報を提供し、配置のための Api を提供します。

四角形は四角形のエクステントを持ちますが、任意の形の2D サーフェイスを表します。 3D 環境の四角形を操作するこれらの2D サーフェイス上の配置を有効にするには、この相互作用を可能にするユーティリティを提供します。 現在、シーンの理解には、_ *Findセンター* のほとんどの配置 * と **GetSurfaceMask** という2つの関数が用意されています。 Findセンターのほとんどの配置は、オブジェクトを配置できるクワッド上の位置を特定し、指定された境界ボックスが基になるサーフェイス上にあることを保証するオブジェクトの最適な場所を見つけることを試みる、高レベルの API です。

> [!NOTE]
> 出力の座標は、他の windows の Rect 型と同じように、左上隅が (x = 0, y = 0) である "クワッド空間" のクワッドに対して相対的です。 独自のオブジェクトのオリジンを操作するときは、必ずこのことを考慮してください。 

次の例では、中央の最も配置可能な場所を検索し、クワッドにホログラムを固定する方法を示します。

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

手順1-4 は、特定のフレームワーク/実装に大きく依存しますが、テーマは類似している必要があります。 クワッドは、空間でローカライズされた境界2D 平面を表すだけであることに注意することが重要です。 お使いのエンジンとフレームワークで、クワッドがどこにあるかを認識し、クワッドを基準としてオブジェクトをルート設定することにより、ホログラムは実際の世界に対して正しく配置されます。 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a>メッシュ型

メッシュは、オブジェクトまたは環境の幾何学的表現を表します。 [空間マッピング](../../design/spatial-mapping.md)と同様に、各空間サーフェスメッシュで提供されるメッシュインデックスと頂点データは、すべての最新のレンダリング api で三角形メッシュをレンダリングするために使用される頂点およびインデックスバッファーと同じ使い慣れたレイアウトを使用します。 頂点位置は、の座標系で指定され `Scene` ます。 このデータを参照するために使用される特定の Api は次のとおりです。

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

次のコードは、メッシュ構造から三角形リストを生成する例を示しています。

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

インデックス/頂点バッファーは >= インデックスまたは頂点の数である必要がありますが、それ以外の場合は、メモリを再利用できるように任意のサイズを設定できます。

### <a name="collidermesh"></a>ColliderMesh

シーンオブジェクトは、メッシュと ColliderMeshes プロパティを使用してメッシュと collider メッシュのデータへのアクセスを提供します。 これらのメッシュは常に一致します。つまり、メッシュプロパティの i'th インデックスは、ColliderMeshes プロパティの i'th インデックスと同じジオメトリを表します。 ランタイム/オブジェクトが collider メッシュをサポートしている場合は、最も低い多角形と最も高い順序の近似が得られることが保証されます。アプリケーションが colliders を使用する場所であれば、ColliderMeshes を使用することをお勧めします。 システムで colliders がサポートされていない場合、ColliderMeshes で返されるメッシュオブジェクトは、メッシュがメモリの制約を減らすことと同じオブジェクトになります。

## <a name="developing-with-scene-understanding"></a>シーンの理解による開発

この時点で、ランタイムと SDK について理解しているシーンのコア構成要素について理解しておく必要があります。 電力と複雑さの大半は、アクセスパターン、3D フレームワークとの対話、およびこれらの Api の上に記述できるツールによって、空間プランニング、ルーム分析、ナビゲーション、物理などのより高度なタスクを実行できます。 これらをサンプルでキャプチャして、シナリオを適切な方向に導くことができるようにすることをお勧めします。 説明していないサンプルまたはシナリオがある場合はお知らせください。必要なものをドキュメント化してプロトタイプを作成します。

### <a name="where-can-i-get-sample-code"></a>サンプルコードはどこで入手できますか。

Unity のサンプルコードについては、Unity の [サンプルページ](https://github.com/sceneunderstanding-microsoft/unitysample) ページを参照してください。 このアプリケーションを使用すると、デバイスと通信してさまざまなシーンオブジェクトをレンダリングすることができます。または、シリアル化されたシーンを PC に読み込んで、デバイスを使用せずにシーンの理解を体験することができます。

### <a name="where-can-i-get-sample-scenes"></a>サンプルシーンはどこで入手できますか。

HoloLens2 を持っている場合は、ComputeSerializedAsync の出力をファイルに保存し、独自の使いやすさで逆シリアル化することで、キャプチャしたすべてのシーンを保存できます。 

HoloLens2 デバイスを持っていないが、シーンを理解したい場合は、キャプチャ済みシーンをダウンロードする必要があります。 現在、シーンに関する理解のサンプルにはシリアル化されたシーンが付属しています。これをダウンロードして、独自の便利な方法で使用できます。 次の場所で見つけることができます。

[シーンについてのサンプルシーン](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples/tree/master/Assets/Resources/SerializedScenesForPCPath)

## <a name="see-also"></a>関連項目

* [空間マッピング](../../design/spatial-mapping.md)
* [シーンの理解](../../design/scene-understanding.md)
* [Unity のサンプル](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)
