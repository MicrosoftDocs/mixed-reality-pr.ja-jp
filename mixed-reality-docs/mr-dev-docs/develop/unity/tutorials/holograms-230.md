---
title: MR 空間 230 - 空間マッピング
description: Unity、Visual Studio、および HoloLens を使用したこのコーディングのチュートリアルに従って、空間マッピングの概念の詳細を確認してください。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit、academy、チュートリアル、空間マッピング、surface 再構築、メッシュ、HoloLens、Mixed Reality Academy、unity、mixed reality ヘッドセット、windows Mixed reality ヘッドセット、virtual Reality ヘッドセット、Windows 10
ms.openlocfilehash: 6b218de239da04190fbf08ff8668fa16009df949
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582933"
---
# <a name="mr-spatial-230-spatial-mapping"></a>MR 空間 230:空間マッピング

>[!NOTE]
>Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。  そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。  これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。  これらは、サポートされているデバイス上で継続して動作するように、保守されます。 HoloLens 2 向けには、[新しいチュートリアル シリーズ](./mr-learning-base-01.md)が投稿されています。

[空間マッピング](../../../design/spatial-mapping.md) は、環境に関するホログラムを教えることによって、現実世界と仮想世界を組み合わせたものです。 MR 空間 230 (Project Planetarium) では、次の方法を学習します。

* 環境をスキャンし、HoloLens から開発用コンピューターにデータを転送します。
* シェーダーを調査し、それらを使用してスペースを視覚化する方法を学習します。
* メッシュ処理を使用して、ルームメッシュを単純な平面に分割します。
* [MR の基本 101](../../../develop/unity/tutorials/holograms-101.md)で学習した配置手法を超えて、その環境にホログラムを配置できる場所についてのフィードバックを提供します。
* 遮蔽効果を調べると、ホログラムが実際のオブジェクトの背後にある場合でも、x 光線による視覚エフェクトを見ることができます。

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a>デバイス サポート

<table>
<tr>
<th>コース</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></th>
</tr><tr>
<td>MR 空間 230:空間マッピング</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>開始する前に

### <a name="prerequisites"></a>前提条件

* 適切な [ツールがインストール](../../../develop/install-the-tools.md)された WINDOWS 10 PC。
* 基本的な C# プログラミング機能。
* [MR の基本 101](../../../develop/unity/tutorials/holograms-101.md)を完了している必要があります。
* [開発用に構成され](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)た HoloLens デバイス。

### <a name="project-files"></a>プロジェクト ファイル

* プロジェクトに必要な [ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) をダウンロードします。 Unity 2017.2 以降が必要です。
  * 引き続き Unity 5.6 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip)をご利用ください。
  * 引き続き Unity 5.5 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip)をご利用ください。
  * 引き続き Unity 5.4 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip)をご利用ください。
* ファイルをデスクトップまたはその他の簡単な場所に保管します。

>[!NOTE]
>ダウンロードする前にソースコードを確認する場合は、GitHub から [入手でき](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping)ます。

### <a name="notes"></a>Notes

* コード内のブレークポイントにヒットするには、Visual Studio の [マイコードのみの有効化] を無効 (*オフ*> >) にする必要があります。

## <a name="unity-setup"></a>Unity のセットアップ

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* **Unity** を起動します。
* [ **新規** ] を選択して、新しいプロジェクトを作成します。
* プロジェクトに **Planetarium** という名前を指定します。
* **3d** の設定が選択されていることを確認します。
* [ **プロジェクトの作成**] をクリックします。
* Unity が起動したら、[ **Edit > Project Settings > Player**] を開きます。
* [ **インスペクター** ] パネルで、緑色の **Windows ストア** アイコンを見つけて選択します。
* [ **その他の設定**] を展開します。
* [ **レンダリング** ] セクションで、[ **Virtual Reality サポート** ] オプションをオンにします。
* **Virtual Reality sdk** の一覧に [ **Windows Holographic** ] が表示されていることを確認します。 表示されていない場合は、 **+** 一覧の下部にあるボタンを選択し、[ **Windows Holographic**] を選択します。
* [ **発行の設定**] を展開します。
* [ **機能** ] セクションで、次の設定を確認します。
    * InternetClientServer
    * PrivateNetworkClientServer
    * Microphone
    * SpatialPerception
* **プロジェクト設定の編集 > > 品質** に進む
* [ **インスペクター** ] パネルの [Windows ストア] アイコンで、[既定] 行の下にある黒のドロップダウン矢印を選択し、既定の設定を [ **非常に低い**] に変更します。
* [アセット] [ **> カスタムパッケージ**] の [パッケージのインポート >] にアクセスします。
* **..\Holographicacademy-holograms-230-SpatialMapping\Starting** フォルダーに移動します。
* **Planetarium unitypackage** をクリックします。
* **[開く]** をクリックします。
* [ **Unity パッケージのインポート** ] ウィンドウが表示されたら、[ **インポート** ] ボタンをクリックします。
* Unity によって、このプロジェクトを完了するために必要なすべての資産がインポートされるのを待ちます。
* [ **階層** ] パネルで、 **メインカメラ** を削除します。
* [ **プロジェクト** ] パネルの [ **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** ] フォルダーで、 **メインカメラ** オブジェクトを見つけます。
* **メインカメラ** prefab を [**階層**] パネルにドラッグアンドドロップします。
* [ **階層** ] パネルで、 **指向性ライト** オブジェクトを削除します。
* [ **プロジェクト** ] パネルの [ **ホログラム** ] フォルダーで、 **Cursor** オブジェクトを探します。
* **カーソル** をドラッグして **階層** に & ドロップします。
* [ **階層** ] パネルで、 **カーソル** オブジェクトを選択します。
* [ **インスペクター** ] パネルで、[ **レイヤー** ] ドロップダウンをクリックし、[ **レイヤーの編集...**] を選択します。
* **ユーザーレイヤー 31** を "**SpatialMapping**" として指定します。
* 新しいシーンを保存する: **ファイル > [シーン名を付けて保存...**
* [ **新しいフォルダー** ] をクリックし、フォルダーに「 **シーン**」という名前を指定します。
* ファイルに "**Planetarium**" という名前を付けて、[ **シーン** ] フォルダーに保存します。

## <a name="chapter-1---scanning"></a>第1章-スキャン

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

**目標**

* SurfaceObserver とその設定がエクスペリエンスとパフォーマンスに与える影響について説明します。
* 部屋のメッシュを収集するためのルームスキャンエクスペリエンスを作成します。

**手順**

* [ **プロジェクト** ] パネルの **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** フォルダーで、 **SpatialMapping** prefab を見つけます。
* **SpatialMapping** prefab を [**階層**] パネルにドラッグ & ドロップします。

**ビルドと配置 (パート 1)**

* Unity で、[ **ファイル > ビルド設定**] を選択します。
* [ **開い** ているシーンの追加] をクリックして、 **Planetarium** シーンをビルドに追加します。
* [**プラットフォーム**] ボックスの一覧の [**ユニバーサル Windows プラットフォーム**] を選択し、[**プラットフォームの切り替え**] をクリックします。
* **SDK** を **Universal 10** に設定し、 **UWP ビルドの種類** を **D3D** に設定します。
* **Unity C# プロジェクト** を確認します。
* [**ビルド**] をクリックします。
* "App" という名前の **新しいフォルダー** を作成します。
* **アプリ** フォルダーをシングルクリックします。
* **[フォルダーの選択**] ボタンをクリックします。
* Unity のビルドが完了すると、エクスプローラーウィンドウが表示されます。
* **アプリ** フォルダーをダブルクリックして開きます。
* **Planetarium** をダブルクリックして、Visual Studio でプロジェクトを読み込みます。
* Visual Studio で、上部のツールバーを使用して、構成を [ **リリース**] に変更します。
* プラットフォームを **x86** に変更します。
* [ローカルコンピューター] の右側にあるドロップダウン矢印をクリックし、[ **リモートコンピューター**] を選択します。
* [アドレス] フィールドに [デバイスの IP アドレス](/hololens/hololens-network#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) を入力し、[認証モード] を [ **ユニバーサル (暗号化** されていないプロトコル)] に変更します。
* [ **デバッグ]、[デバッグなしで開始] の順にクリック >** 、Ctrl キーを押し **ながら F5** キーを押します。
* ビルドと配置の状態については、Visual Studio の [ **出力** ] パネルをご覧ください。
* アプリがデプロイされたら、ルームを案内します。 周囲のサーフェスが黒と白のワイヤーフレームメッシュで覆われていることがわかります。
* 周囲をスキャンします。 壁、雲、床を見てください。

**ビルドと配置 (パート 2)**

次に、空間マッピングがパフォーマンスに与える影響について説明します。

* Unity で、[ **ウィンドウ > プロファイラー**] を選択します。
* [ **プロファイラーの追加 > GPU**] をクリックします。
* [**アクティブなプロファイラー <Enter IP> の >**] をクリックします。
* HoloLens の **IP アドレス** を入力します。
* **[Connect]** をクリックします。
* GPU がフレームをレンダリングするためにかかる時間 (ミリ秒単位) を観察します。
* デバイスでアプリケーションの実行を停止します。
* Visual Studio に戻り、 **SpatialMappingObserver.cs** を開きます。 これは、Assembly-CSharp (ユニバーサル Windows) プロジェクトの HoloToolkit\SpatialMapping フォルダーにあります。
* 起動 **()** 関数を見つけ、次のコード行を追加します: **TrianglesPerCubicMeter = 1200;**
* プロジェクトをデバイスに再配置してから、 **プロファイラーを再接続** します。 フレームをレンダリングするミリ秒数の変化を確認します。
* デバイスでアプリケーションの実行を停止します。

**Unity での保存と読み込み**

最後に、部屋のメッシュを保存し、Unity に読み込んでみましょう。

* Visual Studio に戻り、前のセクションで **TrianglesPerCubicMeter** **()** 関数に追加した行を削除します。
* プロジェクトをデバイスに再デプロイします。 ここでは、3つ **500** の3つのトライアングルメーターで実行されるようになりました。
* ブラウザーを開き、HoloLens IPAddress に「」と入力して、 **Windows デバイスポータル** に移動します。
* 左側のパネルで [ **3D 表示** ] オプションを選択します。
* [ **Surface 再構築** ] で、[ **更新** ] ボタンを選択します。
* HoloLens でスキャンした領域が表示ウィンドウに表示されていることを確認します。
* 部屋のスキャンを保存するには、[ **保存** ] ボタンを押します。
* **ダウンロード** フォルダーを開いて、保存されているルームモデル **srmesh. .obj** を見つけます。
* Unity プロジェクトの **Assets** フォルダーに **srmesh. .obj** をコピーします。
* Unity で、[**階層**] パネルの [ **SpatialMapping** ] オブジェクトを選択します。
* **オブジェクトサーフェイスのオブザーバー (スクリプト)** コンポーネントを見つけます。
* [ **ルームモデル** ] プロパティの右側にある円をクリックします。
* **Srmesh** オブジェクトを探して選択し、ウィンドウを閉じます。
* [**インスペクター** ] パネルの [**ルームモデル**] プロパティが [ **srmesh**] に設定されていることを確認します。
* [ **再生** ] ボタンを押して Unity のプレビューモードに入ります。
* SpatialMapping コンポーネントは、保存された部屋モデルからメッシュを読み込み、Unity で使用できるようにします。
* [ **シーン** ] ビューに切り替えて、ワイヤーフレームシェーダーで表示されているすべての部屋モデルを表示します。
* プレビューモードを終了するには、もう一度 [ **再生** ] ボタンをクリックします。

**注:** Unity で次にプレビューモードに入ると、既定で保存されているルームメッシュが読み込まれます。

## <a name="chapter-2---visualization"></a>第2章-視覚化

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

**目標**

* シェーダーの基本について説明します。
* 周囲を視覚化します。

**手順**

* Unity の [ **階層** ] パネルで、 **SpatialMapping** オブジェクトを選択します。
* [ **インスペクター** ] パネルで、[ **空間マッピングマネージャー (スクリプト)** ] コンポーネントを見つけます。
* [ **Surface Material** ] プロパティの右側にある円をクリックします。
* **BlueLinesOnWalls** 素材を検索して選択し、ウィンドウを閉じます。
* [ **プロジェクト** パネル **シェーダー** ] フォルダーで、 **BlueLinesOnWalls** をダブルクリックして、Visual Studio でシェーダーを開きます。
* これは単純なピクセル (頂点からフラグメント) シェーダーで、次のタスクを実行します。
    1. 頂点の位置をワールド空間に変換します。
    2. ピクセルが垂直かどうかを判断するために、頂点の法線をチェックします。
    3. 表示するピクセルの色を設定します。

**ビルドと配置**

* Unity に戻り、[ **Play** ] を押してプレビューモードに入ります。
* 青色の線は、保存されているスキャンデータから自動的に読み込まれる、部屋メッシュのすべての垂直サーフェイスに表示されます。
* [ **シーン** ] タブに切り替えて、部屋の表示を調整し、Unity でのルームメッシュ全体の表示方法を確認します。
* [ **プロジェクト** ] パネルで、[ **素材** ] フォルダーを見つけて、 **BlueLinesOnWalls** の素材を選択します。
* 一部のプロパティを変更し、Unity エディターで変更がどのように表示されるかを確認します。
    * [ **インスペクター** ] パネルで、 **LineScale** の値を調整して、線が太くまたは細くなるようにします。
    * [ **インスペクター** ] パネルで、[行 **perメーター** ] の値を調整して、各壁面に表示される線の数を変更します。
* [ **再生** ] をもう一度クリックして、プレビューモードを終了します。
* HoloLens にビルドして展開し、シェーダーのレンダリングが実際のサーフェイスにどのように表示されるかを観察します。

Unity は、素材をプレビューするための優れたジョブを行いますが、常にデバイスでのレンダリングをチェックアウトすることをお勧めします。

## <a name="chapter-3---processing"></a>第3章: 処理

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

**目標**

* アプリケーションで使用するために空間マッピングデータを処理する方法について説明します。
* 空間マッピングデータを分析してプレーンを検索し、三角形を削除します。
* ホログラムの配置に平面を使用します。

**手順**

* Unity の [ **プロジェクト** ] パネルの [ **ホログラム** ] フォルダーで、 **SpatialProcessing** オブジェクトを見つけます。
* **SpatialProcessing** オブジェクトを [**階層**] パネルにドラッグ & ドロップします。

SpatialProcessing prefab には、空間マッピングデータを処理するためのコンポーネントが含まれています。 **SurfaceMeshesToPlanes.cs** は、空間マッピングのデータに基づいてプレーンを検索して生成します。 このアプリケーションでは、壁、床、および雲を表す平面を使用します。 この事前 fab には、空間マッピングメッシュから頂点を削除できる **RemoveSurfaceVertices.cs** も含まれています。 これを使用すると、メッシュに穴を作成したり、不要になった余分な三角形を削除したりできます (プレーンを代わりに使用できるため)。

* Unity の [ **プロジェクト** ] パネルの [ **ホログラム** ] フォルダーで **、[場所] オブジェクトを** 見つけます。
* [移動] オブジェクトを [**階層**] パネルにドラッグアンド **ドロップします**。
* [ **階層** ] パネルで、 **SpatialProcessing** オブジェクトを選択します。
* [ **インスペクター** ] パネルで、[ **Play Space Manager (スクリプト)** ] コンポーネントを見つけます。
* **PlaySpaceManager.cs** をダブルクリックして、Visual Studio で開きます。

PlaySpaceManager.cs には、アプリケーション固有のコードが含まれています。 このスクリプトに機能を追加して、次の動作を有効にします。

1. スキャンの制限時間 (10 秒) を超えた後に、空間マッピングデータの収集を停止します。
2. 空間マッピングデータを処理します。
    1. SurfaceMeshesToPlanes を使用して、ワールドの表現を平面 (壁面、床、雲など) として簡単に作成できます。
    2. 平面の境界内にある表面の三角形を削除するには、RemoveSurfaceVertices を使用します。
3. 世界中にホログラムのコレクションを生成し、ユーザーの近くにある壁と床面に配置します。

PlaySpaceManager.cs でマークされたコーディング演習を完了するか、次のスクリプトを完成したソリューションに置き換えます。

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

**ビルドと配置**

* HoloLens に展開する前に、Unity の [ **再生** ] ボタンを押して、再生モードにします。
* ファイルからルームメッシュが読み込まれたら、空間マッピングメッシュで処理が開始されるまで10秒間待機します。
* 処理が完了すると、平面は床、壁面、天井などを表すように見えます。
* すべての面が見つかったら、カメラの近くにあるフロアのテーブルに太陽のシステムが表示されます。
* 2つのポスターは、カメラの近くの壁にも表示されます。 **ゲーム** モードで表示できない場合は、[**シーン**] タブに切り替えます。
* 再生モードを終了するには、もう一度 [ **再生** ] ボタンをクリックします。
* 通常どおり HoloLens にビルドしてデプロイします。
* 空間マッピングデータのスキャンと処理が完了するまで待機します。
* プレーンが表示されたら、太陽のシステムとポスターを検索してみてください。

## <a name="chapter-4---placement"></a>章 4-配置

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

**目標**

* ホログラムがサーフェイスに適合するかどうかを判断します。
* ホログラムがサーフェイスに適合しない場合にユーザーにフィードバックを提供します。

**手順**

* Unity の [ **階層** ] パネルで、 **SpatialProcessing** オブジェクトを選択します。
* [ **インスペクター** ] パネルで、[ **平面 (スクリプト)] コンポーネントの表面メッシュを** 見つけます。
* [ **描画平面** ] プロパティを [ **なし** ] に変更して選択範囲をクリアします。
* " **描画平面** " プロパティを " **壁**" に変更して、壁面平面だけがレンダリングされるようにします。
* [ **プロジェクト** ] パネルの **Scripts** フォルダーで、 **Placeable.cs** をダブルクリックして Visual Studio で開きます。

配置可能 **なスクリプトは、平面** 検索が完了した後に作成されたポスターとプロジェクションボックスに既にアタッチされています。 いくつかのコードをコメント解除するだけで、次のことが実現されます。

1. Raycasting が境界キューブの中心と4つのコーナーから表面にホログラムを収めるかどうかを決定します。
2. 表面の法線を調べて、ホログラムをフラッシュするのに十分な滑らかさがあるかどうかを判断します。
3. ホログラムの周りに境界キューブをレンダリングして、配置中の実際のサイズを示します。
4. ホログラムの下または後ろに影をキャストして、床と壁のどこに配置されるかを示します。
5. ホログラムを表面に配置できない場合、または緑の場合は、影を赤で表示します。
6. 関係がある表面の種類 (垂直方向または水平方向) に合わせてホログラムを再配置します。
7. 選択したサーフェイスにホログラムをスムーズに配置して、ジャンプやスナップ動作を回避します。

以下のコーディング演習ですべてのコードのコメントを解除するか、 **Placeable.cs** でこの完成したソリューションを使用します。

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The alignToVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

**ビルドと配置**

* 前と同様に、プロジェクトをビルドし、HoloLens にデプロイします。
* 空間マッピングデータのスキャンと処理が完了するまで待機します。
* 太陽のシステムが表示されたら、下の投影ボックスを見つめ、選択ジェスチャを実行して移動します。 [プロジェクション] ボックスを選択すると、[プロジェクション] ボックスの周囲に境界キューブが表示されます。
* 部屋の別の場所に移動します。 プロジェクションボックスは、お使いの宝石に従う必要があります。 投影ボックスの下の影が赤に変わったら、その表面にホログラムを配置することはできません。 投影ボックスの下の影が緑色に変わったら、別の選択ジェスチャを実行してホログラムを配置できます。
* 壁の holographic ポスターの1つを探して選択し、新しい場所に移動します。 フロアまたはシーリングにポスターを配置することはできません。また、移動するたびに各壁面に合わせて正しい向きに保たれることに注意してください。

## <a name="chapter-5---occlusion"></a>第5章-オクルージョン

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

**目標**

* ホログラムが空間マッピングメッシュによって occluded されているかどうかを判断します。
* さまざまな遮蔽手法を適用して、楽しい効果を実現します。

**手順**

まず、空間マッピングメッシュで、occluding を使用せずに他のホログラムを occlude できるようにします。

* [ **階層** ] パネルで、 **SpatialProcessing** オブジェクトを選択します。
* [ **インスペクター** ] パネルで、[ **Play Space Manager (スクリプト)** ] コンポーネントを見つけます。
* [ **セカンダリマテリアル** ] プロパティの右側にある円をクリックします。
* **オクルージョン** を検索して選択し、ウィンドウを閉じます。

次に、地球に特別な動作を追加します。これにより、(太陽などの) 別のホログラムによって occluded されたとき、または空間マッピングメッシュによって、青の強調表示になります。

* [ **プロジェクト** ] パネルの [ **ホログラム** ] フォルダーで **、[] オブジェクトを** 展開します。
* [ **地球**] をクリックします。
* [ **インスペクター** ] パネルで、地球の素材 (下部コンポーネント) を見つけます。
* シェーダーの **ドロップダウン** で、シェーダーを **カスタム > OcclusionRim** に変更します。 これは、別のオブジェクトによって occluded されたときに、地球を中心とした青い強調表示になります。

最後に、太陽のシステムで惑星に対して x 線の視覚効果を有効にします。 次のことを実現するために、 **PlanetOcclusion.cs** (スクリプト \ システムフォルダーにあります) を編集する必要があります。

1. 地球が SpatialMapping レイヤーによって occluded されているかどうかを判断します (部屋メッシュと平面)。
2. SpatialMapping レイヤーによって occluded されるたびに、地球のワイヤーフレーム表現を表示します。
3. 地球のワイヤーフレーム表現が SpatialMapping レイヤーによってブロックされていない場合は非表示にします。

PlanetOcclusion.cs のコーディングの演習に従うか、次の解決策を使用します。

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

**ビルドと配置**

* 通常どおり、アプリケーションを HoloLens に構築してデプロイします。
* 空間マッピングデータのスキャンと処理が完了するまで待ちます (壁に青い線が表示されます)。
* [太陽システムの投影] ボックスを探して選択し、壁の横またはカウンターの背後にあるボックスを設定します。
* [ポスター] ボックスまたは [投影] ボックスで、ピアに対する表面の背後を非表示にすることで、基本的なオクルージョンを表示できます。
* 地球を探すには、別のホログラムや表面にいるときは常に青いハイライト効果があるはずです。
* 惑星が部屋の壁またはその他の表面の内側に移動するのを監視します。 X 線によるビジョンが可能になり、ワイヤーフレームスケルトンを見ることができるようになりました。

## <a name="the-end"></a>最後です

お疲れさまでした。 これで、 **MR 空間 230: 空間マッピング** が完了しました。

* 環境をスキャンして、Unity に空間マッピングデータを読み込む方法について説明します。
* シェーダーの基本と、マテリアルを使用して世界を再視覚化する方法について説明します。
* 平面を検索し、メッシュから三角形を削除するための新しい処理手法について学習しました。
* 意味のあるサーフェイスにホログラムを移動して配置することができました。
* さまざまな遮蔽手法を経験し、開花の力を活用しました。