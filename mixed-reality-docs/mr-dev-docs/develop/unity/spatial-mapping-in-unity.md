---
title: Unity の空間マッピング
description: Unity で実際のジオメトリをレンダリングし、衝突します。
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、空間マッピング、レンダラー、collider、メッシュ、スキャン、コンポーネント、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: 60196a85689ce6c4c190acdfe305fc12982ace4c
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677401"
---
# <a name="spatial-mapping-in-unity"></a>Unity の空間マッピング

このトピックでは、Unity プロジェクトで [空間マッピング](../../design/spatial-mapping.md) を使用する方法について説明します。また、HoloLens デバイスを中心にしたワールドの表面を表す三角形のメッシュを取得して、配置、閉鎖、ルーム分析などを行う方法について説明します。

Unity には、次の方法で開発者に公開される空間マッピングの完全なサポートが含まれています。
1. MixedRealityToolkit で使用可能な空間マッピングコンポーネント。これは、空間マッピングを開始するための便利で迅速なパスを提供します。
2. フルコントロールを提供し、より高度なアプリケーション固有のカスタマイズを可能にする、下位レベルの空間マッピング Api

アプリで空間マッピングを使用するには、Package.appxmanifest で spatialPerception 機能を設定する必要があります。

## <a name="device-support"></a>デバイス サポート

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>機能</strong></td>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
    </tr>
     <tr>
        <td>空間マッピング</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="setting-the-spatialperception-capability"></a>SpatialPerception 機能の設定

アプリで空間マッピングデータを使用するためには、SpatialPerception 機能を有効にする必要があります。

SpatialPerception 機能を有効にする方法:
1. Unity エディターで、 **[プレーヤーの設定** ] ウィンドウを開きます (> プロジェクトの設定を編集し > player)
2. [ **Windows ストア** ] タブをクリックします。
3. [**発行の設定]** を展開し、 **[機能]** ボックスの一覧の **"SpatialPerception"** 機能を確認します。

既に Unity プロジェクトを Visual Studio ソリューションにエクスポートしている場合は、新しいフォルダーにエクスポートするか、 [Visual studio の package.appxmanifest でこの機能](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)を手動で設定する必要があることに注意してください。

空間マッピングでは、少なくとも10.0.10586.0 の MaxVersionTested が必要です。
1. Visual Studio でソリューションエクスプローラーで package.appxmanifest を右クリックし、[**コードの表示**] を選択し **ます。**
2. **TargetDeviceFamily** を指定する行を探し、 **maxversiontested = ""** を **maxversiontested 済み = "10.0.10586.0"** に変更します。
3. Package.appxmanifest を **保存** します。

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Unity の組み込みの空間マッピングコンポーネントの概要

Unity には、アプリに空間マッピングを簡単に追加するためのコンポーネントが2つ用意されています。空間マッピングの **レンダラー** と **空間マッピングの Collider** です。

### <a name="spatial-mapping-renderer"></a>空間マッピングレンダラー

空間マッピングレンダラーを使用すると、空間マッピングメッシュを視覚化できます。

![Unity の空間マッピングレンダラー](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>空間マッピング Collider

空間マッピングの Collider を使用すると、領域マッピングメッシュを使用して、物理などの holographic コンテンツ (または文字) の操作を行うことができます。

![Unity の空間マッピング Collider](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>組み込みの空間マッピングコンポーネントの使用

物理サーフェスを視覚化して操作する場合は、両方のコンポーネントをアプリに追加することができます。

Unity アプリでこれらの2つのコンポーネントを使用するには、次の手順を実行します。
1. 空間サーフェスメッシュを検出する領域の中央にある [ユーザー] オブジェクトを選択します。
2. [インスペクター] ウィンドウで、**コンポーネント**  >  **XR**  >  **空間マッピング Collider** または **空間マッピングレンダラー** を追加します。

これらのコンポーネントの使用方法の詳細については、 <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity ドキュメントサイト</a>を参照してください。

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>組み込みの空間マッピングコンポーネント以外に

これらのコンポーネントを使用すると、空間マッピングを簡単に開始できるように、ドラッグアンドドロップ操作を簡単に行うことができます。  詳細に進むには、次の2つの主要なパスを参照してください。
* 独自の下位レベルのメッシュ処理を行うには、以下の「低レベルの空間マッピングスクリプト API について」セクションを参照してください。
* 上位レベルのメッシュ分析を行うには、 <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>の SpatialUnderstanding ライブラリに関する以下のセクションを参照してください。

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>低レベルの Unity 空間マッピング API の使用

空間マッピングレンダラーコンポーネントと空間マッピング Collider コンポーネントから取得するよりも制御が必要な場合は、低レベルの空間マッピングスクリプト Api を使用できます。

**名前空間:** *UNITYENGINE. XR*<br>
**型**: *SurfaceObserver*、 *SurfaceChange*、 *SurfaceData*、 *SurfaceId*

空間マッピング Api を使用するアプリケーションで推奨されるフローの概要を次に示します。

### <a name="set-up-the-surfaceobservers"></a>SurfaceObserver を設定する

空間マッピングデータが必要な、アプリケーションで定義された領域の領域ごとに1つの SurfaceObserver オブジェクトをインスタンス化します。

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

SetVolumeAsSphere、SetVolumeAsAxisAlignedBox、SetVolumeAsOrientedBox、または Setvolumeassphere を呼び出すことによって、各 SurfaceObserver オブジェクトがデータを提供する領域を指定します。 これらのメソッドのいずれかを再度呼び出すだけで、後で領域の領域を再定義することができます。

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

SurfaceObserver () を呼び出す場合は、空間マッピングシステムに新しい情報が格納されている SurfaceObserver の領域領域の各空間サーフェスに対して、ハンドラーを提供する必要があります。 このハンドラーは、1つの空間サーフェスに対してを受け取ります。

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a>サーフェイスの変更の処理

処理する主なケースがいくつかあります。 同じコードパスを使用して削除することができる更新 & が追加されました。
* この例で追加された & 更新されたケースでは、このメッシュを表す SurfaceData オブジェクトをディクショナリから追加または取得し、必要なコンポーネントを含む構造体を作成してから、RequestMeshDataAsync を呼び出して、シーン内のメッシュデータと位置を設定します。
* 削除された場合は、このメッシュを表すオブジェクトをディクショナリから削除し、破棄します。

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects = 
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

   private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
   {
       switch (changeType)
       {
           case SurfaceChange.Added:
           case SurfaceChange.Updated:
               if (!spatialMeshObjects.ContainsKey(surfaceId))
               {
                   spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                   spatialMeshObjects[surfaceId].transform.parent = this.transform;
                   spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
               }
               GameObject target = spatialMeshObjects[surfaceId];
               SurfaceData sd = new SurfaceData(
                   //the surface id returned from the system
                   surfaceId,
                   //the mesh filter that is populated with the spatial mapping data for this mesh
                   target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                   //the world anchor used to position the spatial mapping mesh in the world
                   target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                   //the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                   target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                   //triangles per cubic meter requested for this mesh
                   1000,
                   //bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                   true
                   );

               SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
               break;
           case SurfaceChange.Removed:
               var obj = spatialMeshObjects[surfaceId];
               spatialMeshObjects.Remove(surfaceId);
               if (obj != null)
               {
                   GameObject.Destroy(obj);
               }
               break;
           default:
               break;
       }
   }
```

### <a name="handling-data-ready"></a>データの準備完了

OnDataReady ハンドラーは、SurfaceData オブジェクトを受け取ります。 WorldAnchor、MeshFilter、および (必要に応じて) MeshCollider オブジェクトには、関連付けられている空間サーフェスの最新の状態が反映されます。 必要に応じて、MeshFilter オブジェクトのメッシュメンバーにアクセスして、メッシュデータの分析や [処理](../../design/spatial-mapping.md#mesh-processing) を実行します。 最新のメッシュを使用して空間サーフェスをレンダリングし、必要に応じて物理衝突と raycasts に使用します。 SurfaceData の内容が null でないことを確認することが重要です。

### <a name="start-processing-on-updates"></a>更新の処理を開始します

SurfaceObserver () は、すべてのフレームではなく、遅延時に呼び出す必要があります。

```cs
void Start () {
    ...
     StartCoroutine(UpdateLoop());
}

 IEnumerator UpdateLoop()
    {
        var wait = new WaitForSeconds(2.5f);
        while(true)
        {
            surfaceObserver.Update(OnSurfaceChanged);
            yield return wait;
        }
    }
```

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a>高レベルのメッシュ分析: SpatialUnderstanding

<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>は、Holographic Unity api に基づいて構築された holographic 開発用の便利なユーティリティコードを集めたものです。

### <a name="spatial-understanding"></a>空間の理解

物理的な世界にホログラムを配置するときは、多くの場合、空間マッピングのメッシュとサーフェス平面を超えることをお勧めします。 Procedurally の配置が完了したら、より高いレベルの環境を理解することをお勧めします。 これには通常、floor、天井、および壁面の決定を行う必要があります。 また、配置の制約のセットに対して最適化して、holographic オブジェクトにとって最も望ましい物理的な場所を決定することもできます。

若い Conker とフラグメントの開発中に、Asobo スタジオはこの問題に直面し、この目的のための部屋のソルバーを開発していました。 これらの各ゲームにはゲーム固有のニーズがありましたが、中心的な空間認識テクノロジを共有しています。 HoloToolkit ライブラリは、このテクノロジをカプセル化しています。これにより、壁上の空のスペースをすばやく検索したり、オブジェクトを天井に配置したり、文字の位置を識別したり、その他の多くの空間を理解したりすることができます。

すべてのソースコードが含まれているので、ニーズに合わせてカスタマイズし、その機能強化をコミュニティと共有することができます。 C++ ソルバーのコードは、UWP dll にラップされ、MixedRealityToolkit 内に含まれている drop in prefab を使用して Unity に公開されています。

### <a name="understanding-modules"></a>モジュールについて

モジュールによって公開される3つの主要なインターフェイスは、単純な surface と空間クエリのトポロジ、オブジェクト検出のための図形、およびオブジェクトセットの配置に基づくオブジェクト配置ソルバーです。 以下で、これらのそれぞれについて説明します。 3つの主要なモジュールインターフェイスに加えて、射線のキャストインターフェイスを使用してタグ付きサーフェス型を取得し、カスタムの watertight playspace メッシュをコピーすることができます。

### <a name="ray-casting"></a>射線のキャスト

部屋がスキャンされ、完了すると、床、天井、壁などの表面にラベルが内部的に生成されます。 "PlayRaycastResult Eraycast" 関数は、射線を受け取り、光線が既知の表面と競合している場合は、その表面に関する情報を "" の形式で返します。

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology, 
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and 
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface, 
                    //  but vertical surface that looks like a 
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown 
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

内部的には、raycast は、playspace の計算された8cm キューブ voxel 表現に対して計算されます。 各 voxel には、処理されたトポロジデータを含む surface 要素のセットが含まれています (「」)。 交差する voxel セルに含まれているが比較され、トポロジ情報の検索に使用される最適な一致が得られます。 このトポロジデータには、"SurfaceTypes" 列挙型の形式で返されるラベルと、交差するサーフェイスの表面領域が含まれます。

Unity のサンプルでは、カーソルは各フレームに射線をキャストします。 まず、Unity の colliders に対して行います。 2つ目は、モジュールのワールド表現を理解することです。 最後に、UI 要素を繰り返します。 このアプリケーションでは、UI の優先順位を取得し、結果を理解した後、Unity の colliders を取得します。 SurfaceType は、カーソルの横にテキストとして報告されます。

![Surface の種類がカーソルの横に表示される](images/su-raycastresults-300px.jpg)<br>
*Surface の種類がカーソルの横に表示される*

### <a name="topology-queries"></a>トポロジクエリ

DLL 内では、トポロジマネージャーは環境のラベル付けを処理します。 前述のように、データの大部分は、voxel ボリューム内に含まれる、1つのデータに格納されます。 さらに、"Playspace 情報" 構造体は、再生スペースに関する情報を格納するために使用されます。これには、ワールドアラインメント (下記の詳細情報)、floor、および天井高さが含まれます。 ヒューリスティックは、floor、シーリング、および壁面を決定するために使用されます。 たとえば、1 ~ 2 の範囲を超える水平方向サーフェイスは、床面と見なされます。 このプロセスでは、スキャン処理中のカメラパスも使用されることに注意してください。

トポロジマネージャーによって公開されるクエリのサブセットは、dll を通じて公開されます。 公開されているトポロジクエリは次のとおりです。

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

各クエリには、クエリの種類に固有のパラメーターのセットがあります。 次の例では、必要なボリュームの最小の高さ & 幅、床の上の最小配置高さ、およびボリュームの前面にある最小のクリアランスの量をユーザーが指定しています。 すべての測定値は、メーターで計算されます。

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

これらの各クエリは、"TopologyResult" 構造体の事前に割り当てられた配列を受け取ります。 "LocationCount" パラメーターは、渡された配列の長さを指定します。 戻り値は、返された場所の数を報告します。 この数は、渡された "locationCount" パラメーターよりも大きくありません。

"TopologyResult" には、返されたボリュームの中央の位置、フェーシングの方向 (通常は)、および検出された領域のサイズが含まれます。

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

Unity サンプルでは、これらの各クエリが仮想 UI パネルのボタンにリンクされていることに注意してください。 サンプルでは、これらの各クエリのパラメーターを妥当な値にハードコーディングしています。 その他の例については、サンプルコードの SpaceVisualizer.cs を参照してください。

### <a name="shape-queries"></a>クエリのシェイプ

Dll 内で、shape analyzer ("ShapeAnalyzer_W") は、トポロジアナライザーを使用して、ユーザーが定義したカスタム図形と照合します。 Unity のサンプルでは、図形のセットを定義し、[図形] タブ内の [アプリ内クエリ] メニューを使用して結果を表示します。その目的は、ユーザーが独自のオブジェクト図形のクエリを定義し、アプリケーションの必要に応じてそれらを利用できるようにすることです。

図形の分析は、水平方向のサーフェイスでのみ動作することに注意してください。 たとえば、ソファは、平らな座席の表面とソファの上面によって定義されています。 Shape クエリでは、特定のサイズ、高さ、および縦横範囲の2つのサーフェスが検索され、2つのサーフェスがアラインされ、接続されています。 Api の用語を使用して、ソファ座席と背面は形状コンポーネントであり、アラインメント要件はシェイプコンポーネントの制約です。

"Sittable" オブジェクトの Unity サンプル (ShapeDefinition.cs) で定義されているクエリの例を次に示します。

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

各図形クエリは、一連の図形コンポーネントによって定義されます。各図形コンポーネントには、一連のコンポーネント制約と、コンポーネント間の依存関係を示す一連の図形制約があります。 この例では、1つのコンポーネント定義に3つの制約が含まれており、コンポーネント間に図形の制約はありません (コンポーネントが1つだけであるため)。

これに対し、ソファ図形には、2つの図形コンポーネントと4つのシェイプ制約があります。 コンポーネントは、ユーザーのコンポーネントリスト内のインデックスによって識別されることに注意してください (この例では0と 1)。

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

カスタム図形の定義を簡単に作成するために、Unity モジュールにラッパー関数が用意されています。 コンポーネントとシェイプの制約の完全な一覧は、"ShapeComponentConstraint" 構造と "ShapeConstraint" 構造内の "SpatialUnderstandingDll.cs" にあります。

![四角形の形状がこの画面にあります](images/su-shapequery-300px.jpg)<br>
*四角形の形状がこの画面にあります*

### <a name="object-placement-solver"></a>オブジェクト配置のソルバー

オブジェクト配置のソルバーを使用して、オブジェクトを配置する物理的な部屋内の理想的な場所を識別できます。 ソルバーは、オブジェクトのルールと制約を指定して最適な場所を見つけます。 また、オブジェクトクエリは、オブジェクトが "Solver_RemoveObject" または "Solver_RemoveAllObjects" の呼び出しで削除されるまで保持され、制約された複数オブジェクトの配置が可能になります。 オブジェクト配置クエリは、3つの部分で構成されます。パラメーターを持つ配置の種類、規則の一覧、および制約の一覧です。 クエリを実行するには、次の API を使用します。

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

この関数は、オブジェクト名、配置定義、および規則と制約の一覧を受け取ります。 C# ラッパーは、規則と制約の構築を簡単にするための構築ヘルパー関数を提供します。 配置定義には、次のいずれかのクエリの種類が含まれます。

```cpp
public enum PlacementType
            {
                Place_OnFloor,
                Place_OnWall,
                Place_OnCeiling,
                Place_OnShape,
                Place_OnEdge,
                Place_OnFloorAndCeiling,
                Place_RandomInAir,
                Place_InMidAir,
                Place_UnderFurnitureEdge,
            };
```

各配置型には、型に固有のパラメーターのセットがあります。 "ObjectPlacementDefinition" 構造体には、これらの定義を作成するための静的ヘルパー関数のセットが含まれています。 たとえば、床にオブジェクトを配置する場所を見つけるには、次の関数を使用します。 public static Objectplacement Ementdefinition Create_OnFloor (Vector3 半 Dims) 配置の種類に加えて、一連のルールと制約を指定することができます。 規則に違反することはありません。 型とルールを満たす配置場所は、最適な配置場所を選択するために、一連の制約に対して最適化されます。 各ルールと制約は、指定された静的作成関数によって作成できます。 ルールと制約の構築関数の例を以下に示します。

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

次のオブジェクト配置クエリは、表面の端に半分のメーターキューブを配置する場所を探しています。これは、以前に配置された他のオブジェクトから、部屋の中心付近に向かっています。

```cs
List<ObjectPlacementRule> rules = 
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints = 
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f), 
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

成功した場合、配置位置、次元、および向きを含む "Objectplacement Ementresult" 構造体が返されます。 また、配置は、配置されたオブジェクトの dll の内部リストに追加されます。 後続の配置クエリでは、このオブジェクトが考慮されます。 Unity サンプルの "LevelSolver.cs" ファイルには、クエリの例が多数含まれています。

![オブジェクトの配置の結果](images/su-objectplacement-1000px.jpg)<br>
*図 3: 青色のボックスを使用して、カメラの位置ルールから離れた場所にあるフロアクエリの結果を確認する*

レベルまたはアプリケーションのシナリオで必要とされる複数のオブジェクトの配置場所を解決する場合、は、領域が見つかる確率を最大化するために、最初に不可欠なオブジェクトとラージオブジェクトを解決します。 配置順序は重要です。 オブジェクトの配置が見つからない場合は、制限の少ない構成を試してください。 一連のフォールバック構成を設定することは、多くの部屋構成で機能をサポートするために不可欠です。

### <a name="room-scanning-process"></a>ルームスキャンプロセス

HoloLens によって提供される空間マッピングソリューションは、問題のある領域全体のニーズに対応できるように設計されていますが、空間認識モジュールは、2つの特定のゲームのニーズをサポートするように構築されています。 このソリューションは、次に示すように、特定のプロセスと想定のセットに基づいて構築されています。

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

ユーザー駆動型の playspace "描画" –スキャンフェーズ中に、ユーザーは再生速度を移動して、必要な領域を効果的に描画します。 生成されたメッシュは、このフェーズでユーザーからのフィードバックを提供するために重要です。 屋内で home または office セットアップ–クエリ関数は、フラットなサーフェイスと壁面を中心に設計されています。 これは、ソフトな制限です。 ただし、スキャンフェーズでは、主要軸と補助軸に沿ってメッシュテセレーションを最適化するために、主軸分析が完了します。 含まれている SpatialUnderstanding.cs ファイルは、スキャンフェーズプロセスを管理します。 次の関数を呼び出します。

```
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan – 
    Called each frame to update the scanning process. The camera position and 
    orientation is passed in and is used for the playspace painting process, 
    described above.

GeneratePlayspace_RequestFinish – 
    Called to finalize the playspace. This will use the areas “painted” during 
    the scan phase to define and lock the playspace. The application can query 
    statistics during the scanning phase as well as query the custom mesh for 
    providing user feedback.

Import_UnderstandingMesh – 
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by 
    the module and placed on the understanding prefab will periodically query the 
    custom mesh generated by the process. In addition, this is done once more 
    after scanning has been finalized.
```

"SpatialUnderstanding" 動作によって実行されるスキャンフローは、InitScan を呼び出し、その後、各フレームに対してアップデートを実行します。 統計クエリによって適切なカバレッジが報告されると、ユーザーは、ユーザーが RequestFinish を呼び出して、スキャンフェーズの終了を示すことができます。 戻り値が dll の処理を完了したことを示すまで、アップデートを引き続き呼び出すことができます。

### <a name="understanding-mesh"></a>メッシュについて

Dll を理解すると、内部的に再生スペースが8cm サイズの voxel キューブのグリッドとして格納されます。 スキャンの初期部分では、主要なコンポーネント分析が完了して、部屋の軸が決定されます。 内部的には、これらの軸に合わせて voxel 領域を格納します。 メッシュは、voxel ボリュームから isosurface を抽出することによって、約1秒ごとに生成されます。 

![Voxel ボリュームから生成されたメッシュを生成しました](images/su-custommesh.jpg)<br>
*Voxel ボリュームから生成されたメッシュを生成しました*

## <a name="troubleshooting"></a>トラブルシューティング
* [SpatialPerception](#setting-the-spatialperception-capability)機能が設定されていることを確認します。
* 追跡が失われると、次の OnSurfaceChanged イベントによってすべてのメッシュが削除されます。

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>混合 Reality ツールキットでの空間マッピング
混合 Reality Toolkit v2 での空間マッピングの使用の詳細については、MRTK ドキュメントの「 <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">空間認識」セクション</a> を参照してください。

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

私たちが用意した Unity 開発チェックポイント体験に従っている場合、読者は MRTK コア構成要素を探索している段階にいます。 ここから、次の構成要素に進むことができます。 

> [!div class="nextstepaction"]
> [[テキスト]](text-in-unity.md)

または、Mixed Reality プラットフォームの機能と API に移動します。

> [!div class="nextstepaction"]
> [共有エクスペリエンス](shared-experiences-in-unity.md)

いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks)に戻ることができます。

## <a name="see-also"></a>関連項目
* [座標系](../../design/coordinate-systems.md)
* [Unity の座標系](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine. MeshFilter</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine. MeshCollider</a>
* <a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine。境界</a>
