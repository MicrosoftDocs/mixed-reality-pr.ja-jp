---
title: ケーススタディ-HoloLens の空間マッピング機能の拡張
description: Microsoft HoloLens 用の最初のアプリを作成する際には、デバイスでの空間マッピングの境界をどれだけまでにプッシュできるかについても説明しました。
author: jevertt
ms.author: jemccull
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、空間マッピング
ms.openlocfilehash: b6546c5c14c5a16f5218721d007bc83798bacfad
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91687479"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a>ケーススタディ-HoloLens の空間マッピング機能の拡張

Microsoft HoloLens 用の最初のアプリを作成する際には、デバイスでの空間マッピングの境界をどれだけまでにプッシュできるかについても説明しました。 Microsoft スタジオのソフトウェアエンジニアである Jeff Evertt は、新しいテクノロジがどのように開発され、ユーザーの実際の環境でのホログラムの配置方法をより細かく制御する必要がないかについて説明しています。

> [!NOTE]
> HoloLens 2 では、開発者向けの新しい [シーンランタイム](../design/scene-understanding.md)が実装されています。これは、環境を認識するアプリケーションの開発を直感的に行うように設計された、構造化された高レベルの環境表現を使用して、混合の現実開発 

## <a name="watch-the-video"></a>ビデオを見る

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a>空間マッピング以外

私たち[は、1](https://www.microsoft.com/p/young-conker/9nblggh5ggk1)つの HoloLens での最初の試合の2つであるの[に対して](https://www.microsoft.com/p/fragments/9nblggh5ggm8)、私たちは私たちの試合に取り組んできましたが、ここでは、ユーザーの環境についてより高いレベルの理解が必要でした。 各ゲームには独自の配置ニーズがありました。たとえば、フラグメントでは、フロアやテーブルなどのさまざまなサーフェスを区別して、関連する場所に手掛かりを配置する必要がありました。 また、ソファや椅子など、holographic 文字が見られる可能性のある表面を特定できるようにする必要がありました。 Young Conker では、プレーヤーの部屋の中で、生成された画面をプラットフォームとして使用できるようにしたいと考えていました。

これらのゲームの開発パートナーである[Asobo スタジオ](https://www.asobostudio.com/index.html)は、この問題に直面し、HoloLens の空間マッピング機能を拡張するテクノロジを作成しました。 これを使用すると、プレーヤーの部屋を分析し、壁、テーブル、椅子、床などの表面を特定できます。 また、holographic オブジェクトの最適な配置を決定するために、一連の制約に対して最適化する機能が用意されています。

## <a name="the-spatial-understanding-code"></a>空間を理解するコード

Asobo の元のコードを取って、このテクノロジをカプセル化するライブラリを作成しました。 Microsoft と Asobo は、このコードをオープンソースにし、独自のプロジェクトで使用できるように [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) で使用できるようにしました。 すべてのソースコードが含まれているので、ニーズに合わせてカスタマイズし、その機能強化をコミュニティと共有することができます。 C++ ソルバーのコードは、UWP DLL にラップされ、 [MixedRealityToolkit 内に含まれるドロップイン prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding)を使用して Unity に公開されています。

Unity サンプルには多くの便利なクエリが含まれています。これを使用すると、壁上の空のスペースを検索したり、オブジェクトを天井に配置したり、床上の大きなスペースに配置したり、文字の位置を識別したり、その他のさまざまな空間を理解するクエリを実行したりできます。

HoloLens によって提供される空間マッピングソリューションは、問題のある領域全体のニーズに対応できるように設計されていますが、空間を認識するモジュールは、2つの特定のゲームのニーズをサポートするように構築されています。 そのため、そのソリューションは、特定のプロセスと一連の前提を中心に構築されています。
* **固定サイズの playspace** : ユーザーは、init 呼び出しの最大 playspace サイズを指定します。
* **1 回限りのスキャンプロセス** : このプロセスには、ユーザーが再生領域を定義するための個別のスキャンフェーズが必要です。 クエリ関数は、スキャンが完了するまで機能しません。
* **ユーザー駆動型の playspace "描画"** : スキャンフェーズ中に、ユーザーが playspace を移動して表示し、含める必要がある領域を効果的に描画します。 生成されたメッシュは、このフェーズでユーザーからのフィードバックを提供するために重要です。
* **屋内で home または office セットアップ** : クエリ関数は、フラットなサーフェイスと壁面を中心に設計されています。 これは、ソフトな制限です。 ただし、スキャンフェーズでは、主要軸と補助軸に沿ってメッシュテセレーションを最適化するために、主軸分析が完了します。

### <a name="room-scanning-process"></a>ルームスキャンプロセス

空間を理解するためのモジュールを読み込むときは、最初にスペースをスキャンします。これにより、床、天井、壁など、使用可能なすべてのサーフェイスが識別され、ラベルが付けられます。 スキャン処理中は、部屋を見て、スキャンに含める必要がある領域を "ペイント" します。

このフェーズで見たメッシュは、どの部分がスキャンされているかをユーザーが知ることができる視覚的なフィードバックの重要な部分です。 空間認識モジュールの DLL は、内部的に、8cm サイズの voxel キューブのグリッドとして playspace を格納します。 スキャンの初期部分では、主要なコンポーネント分析が完了して、部屋の軸が決定されます。 内部的には、これらの軸に合わせて voxel 領域を格納します。 メッシュは、voxel ボリュームから isosurface を抽出することによって、約1秒ごとに生成されます。

![白の空間マッピングメッシュと、緑色の playspace メッシュについて理解する](images/spatial-mapping-500px.png)

白の空間マッピングメッシュと、緑色の playspace メッシュについて理解する



含まれている SpatialUnderstanding.cs ファイルは、スキャンフェーズプロセスを管理します。 次の関数を呼び出します。
* **SpatialUnderstanding_Init** : 開始時に1回呼び出されます。
* **GeneratePlayspace_InitScan** : スキャンフェーズを開始する必要があることを示します。
* **GeneratePlayspace_UpdateScan_DynamicScan** : 各フレームを呼び出して、スキャンプロセスを更新します。 カメラの位置と向きは、前に説明した playspace の描画プロセスに使用されます。
* **GeneratePlayspace_RequestFinish** : playspace を終了するために呼び出されます。 これは、スキャンフェーズ中に "描画された" 領域を使用して、playspace を定義およびロックします。 アプリケーションでは、スキャンフェーズ中に統計のクエリを実行したり、ユーザーフィードバックを提供するためにカスタムメッシュを照会したりすることができます。
* **Import_UnderstandingMesh** : スキャン中に、モジュールによって提供された **SpatialUnderstandingCustomMesh** の動作が、prefab を理解するために、プロセスによって生成されたカスタムメッシュを定期的に照会します。 さらに、この処理は、スキャンが完了した後に実行されます。

**SpatialUnderstanding** 動作によって実行されるスキャンフローは、 **initscan** を呼び出し、その後、各フレームに対して **アップデートを実行** します。 統計クエリによって適切なカバレッジが報告されると、ユーザーは、[ **Requestfinish** ] を呼び出して、スキャンフェーズの終了を示すことができます。 戻り値が DLL の処理を完了したことを示すまで、アップデートを引き続き呼び出す **ことができ** ます。

## <a name="the-queries"></a>クエリ

スキャンが完了すると、インターフェイスで次の3種類のクエリにアクセスできるようになります。
* **トポロジクエリ** : スキャンされたルームのトポロジに基づく高速クエリです。
* **Shape クエリ** : トポロジクエリの結果を使用して、定義したカスタム図形に適した水平方向のサーフェイスを検索します。
* **オブジェクト配置クエリ** : オブジェクトの一連のルールと制約に基づいて最適な場所を検索する、より複雑なクエリです。

3つの主要なクエリに加えて、raycasting インターフェイスを使用して、タグ付きサーフェスの種類を取得し、カスタムの watertight ルームメッシュをコピーすることができます。

### <a name="topology-queries"></a>トポロジクエリ

DLL 内では、トポロジマネージャーは環境のラベル付けを処理します。 前述のように、データの大部分は、voxel ボリューム内に含まれる、1つのデータに格納されています。 さらに、 **playspace** 情報構造体は、再生領域に関する情報を格納するために使用されます。これには、ワールドアラインメント (下記の詳細情報)、floor、および天井高さが含まれます。

ヒューリスティックは、floor、シーリング、および壁面を決定するために使用されます。 たとえば、1 ~ 2 の範囲を超える水平方向サーフェイスは、床面と見なされます。 このプロセスでは、スキャン処理中のカメラパスも使用されることに注意してください。

トポロジマネージャーによって公開されるクエリのサブセットは、DLL を通じて公開されます。 公開されているトポロジクエリは次のとおりです。
* QueryTopology_FindPositionsOnWalls
* QueryTopology_FindLargePositionsOnWalls
* QueryTopology_FindLargestWall
* QueryTopology_FindPositionsOnFloor
* QueryTopology_FindLargestPositionsOnFloor
* QueryTopology_FindPositionsSittable

各クエリには、クエリの種類に固有のパラメーターのセットがあります。 次の例では、必要なボリュームの最小の高さ & 幅、床の上の最小配置高さ、およびボリュームの前面にある最小のクリアランスの量をユーザーが指定しています。 すべての測定値は、メーターで計算されます。




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

これらの各クエリは、 **TopologyResult** 構造体の事前に割り当てられた配列を受け取ります。 **Locationcount** パラメーターは、渡された配列の長さを指定します。 戻り値は、返された場所の数を報告します。 この数は、渡された **Locationcount** パラメーターを超えてはなりません。

**TopologyResult** には、返されたボリュームの中央の位置、フェーシングの方向 (通常は)、および検出された領域の大きさが含まれます。




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

Unity サンプルでは、これらの各クエリが仮想 UI パネルのボタンにリンクされていることに注意してください。 サンプルでは、これらの各クエリのパラメーターを妥当な値にハードコーディングしています。 その他の例については、サンプルコードの *SpaceVisualizer.cs* を参照してください。

### <a name="shape-queries"></a>クエリのシェイプ

DLL 内で、shape analyzer ( **ShapeAnalyzer_W** ) は、トポロジアナライザーを使用して、ユーザーが定義したカスタム図形と照合します。 Unity サンプルには、定義済みの一連の図形があります。これは、[クエリ] メニューの [図形] タブに表示されます。

図形の分析は、水平方向のサーフェイスでのみ動作することに注意してください。 たとえば、ソファは、平らな座席の表面とソファの上面によって定義されています。 Shape クエリでは、特定のサイズ、高さ、および縦横範囲の2つのサーフェスが検索され、2つのサーフェスがアラインされ、接続されています。 この Api の用語を使用して、ソファ座席とソファの背面の上部には形状コンポーネントがあり、アラインメント要件はシェイプコンポーネントの制約です。

"Sittable" オブジェクトの Unity サンプル ( **ShapeDefinition.cs** ) で定義されているクエリの例を次に示します。




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

各図形クエリは、一連の図形コンポーネントによって定義されます。各図形コンポーネントには、一連のコンポーネント制約と、コンポーネント間の依存関係を示す一連の図形制約があります。 この例では、1つのコンポーネント定義に3つの制約が含まれており、コンポーネント間に図形の制約はありません (コンポーネントが1つだけであるため)。

これに対し、ソファ図形には、2つの図形コンポーネントと4つのシェイプ制約があります。 コンポーネントは、ユーザーのコンポーネントリスト内のインデックスによって識別されることに注意してください (この例では0と 1)。




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

カスタム図形の定義を簡単に作成するために、Unity モジュールにラッパー関数が用意されています。 コンポーネントとシェイプの制約の完全な一覧については、 **ShapeComponentConstraint** と **ShapeConstraint** の構造内の **SpatialUnderstandingDll.cs** を参照してください。

![青い四角形は、椅子の図形クエリの結果を強調表示します。](images/chair-shape-query-500px.png)

青い四角形は、椅子の図形クエリの結果を強調表示します。



### <a name="object-placement-solver"></a>オブジェクト配置のソルバー

オブジェクト配置クエリを使用すると、オブジェクトを配置する物理的な部屋の理想的な場所を識別できます。 ソルバーは、オブジェクトのルールと制約を指定して、最適な場所を見つけます。 また、オブジェクトクエリは、オブジェクトが **Solver_RemoveObject** または **Solver_RemoveAllObjects** 呼び出しで削除されるまで保持され、制約された複数オブジェクト配置が可能になります。

オブジェクト配置クエリは、3つの部分で構成されます。パラメーターを使用した配置の種類、規則の一覧、および制約の一覧です。 クエリを実行するには、次の API を使用します。




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
この関数は、オブジェクト名、配置定義、および規則と制約の一覧を受け取ります。 C# ラッパーは、規則と制約の構築を簡単にする構築ヘルパー関数を提供します。 配置定義には、次のいずれかのクエリの種類が含まれます。




```
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

各配置型には、型に固有のパラメーターのセットがあります。 **Objectplacementdefinition** 構造体には、これらの定義を作成するための静的ヘルパー関数のセットが含まれています。 たとえば、床にオブジェクトを配置する場所を見つけるには、次の関数を使用します。 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

配置の種類に加えて、一連のルールと制約を指定することができます。 規則に違反することはありません。 型とルールを満たす配置場所は、最適な配置場所を選択するために、一連の制約に対して最適化されます。 各ルールと制約は、指定された静的作成関数によって作成できます。 ルールと制約の構築関数の例を以下に示します。




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

次に示すオブジェクト配置クエリでは、画面の端に半分のメーターキューブを配置し、その他の場所にある他のオブジェクトから、ルームの中央付近に移動するための場所を探しています。




```
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

成功した場合、配置位置、次元、および向きを含む **Objectplacement Ementresult** 構造体が返されます。 また、配置は、配置されたオブジェクトの DLL の内部リストに追加されます。 後続の配置クエリでは、このオブジェクトが考慮されます。 Unity サンプルの **LevelSolver.cs** ファイルには、クエリの例が多数含まれています。

![青いボックスには、"カメラの位置から離れています" ルールを使用して、3か所のフロアクエリの結果が表示されます。](images/away-from-camera-position-500px.png)

青いボックスには、"カメラの位置から離れています" ルールを使用して、3か所のフロアクエリの結果が表示されます。


**ヒント:**
* レベルまたはアプリケーションのシナリオに必要な複数のオブジェクトの配置位置を解決する場合は、まず、必要以上に大きなオブジェクトを解決して、スペースが見つかる確率を最大化します。
* 配置順序は重要です。 オブジェクトの配置が見つからない場合は、制限の少ない構成を試してください。 一連のフォールバック構成を設定することは、多くの部屋構成で機能をサポートするために不可欠です。

### <a name="ray-casting"></a>射線のキャスト

3つの主要なクエリに加えて、射線のキャストインターフェイスを使用して、タグ付きサーフェス型を取得できます。また、ルームがスキャンされて完了した後に、カスタムの watertight playspace メッシュをコピーできます。フロア、天井、壁などの表面には、ラベルが内部的に生成されます。 **PlayRaycastResult Eraycast** 関数は、光線を受け取り、光線が既知のサーフェイスと競合している場合は、その表面に関する情報を **RaycastResult** の形式で返します。 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

内部的には、raycast は、playspace の計算された8cm キューブ voxel 表現に対して計算されます。 各 voxel には、処理されたトポロジデータ (とも呼ばれます) を持つ surface 要素のセットが含まれています。 交差する voxel セルに含まれているが比較され、トポロジ情報の検索に使用される最適な一致が得られます。 このトポロジデータには、 **SurfaceTypes** 列挙型の形式で返されるラベルと、交差するサーフェイスの表面領域が含まれます。

Unity のサンプルでは、カーソルは各フレームに射線をキャストします。 最初に、Unity の colliders に対して2番目は、モジュールの世界表現を理解するためのものです。最後に、UI 要素に対してを実行します。 このアプリケーションでは、UI は優先順位を取得し、結果を理解し、最後に Unity の colliders を取得します。 **SurfaceType** は、カーソルの横にテキストとして報告されます。

![Raycast 結果レポートを床と交差させることができます。](images/raycast-result-500px.jpg)

Raycast 結果レポートを床と交差させることができます。


## <a name="get-the-code"></a>コードを取得する

オープンソースコードは [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)で入手できます。 プロジェクトでコードを使用する場合は、 [HoloLens Developer フォーラム](https://forums.hololens.com/) でお知らせください。 何をしているかをお待ちください。

## <a name="about-the-author"></a>著者について

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <b>Jeff Evertt</b> は、育成から開発を体験できるようになったころから HoloLens で働いてきたソフトウェアエンジニアリングリードです。 HoloLens より前は、さまざまなプラットフォームやゲームで Xbox Kinect とゲーム業界で働いていました。 Jeff は、ロボットやグラフィックス、そしてビープ音が鳴り目立つ色ライトを使用したことに情熱を持っています。 新しいものを学習し、ソフトウェア、ハードウェア、特に2つの重なり合う領域で作業しています。</td>
</tr>
</table>



## <a name="see-also"></a>関連項目
* [空間マッピング](../design/spatial-mapping.md)
* [シーンの理解](../design/scene-understanding.md)
* [部屋のスキャンの可視化](../design/room-scan-visualization.md)
* [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Asobo Studio: HoloLens 開発の最前線からの教訓](https://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
