---
title: Unity のパフォーマンスに関する推奨事項
description: Mixed Reality アプリのパフォーマンスを向上させるための Unity 固有のヒント。
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2019
ms.topic: article
keywords: グラフィックス, cpu, gpu, レンダリング, ガベージ コレクション, hololens
ms.localizationpriority: high
ms.openlocfilehash: 6fd12bec31bb721def8801a8f2bacb8c3cb75745
ms.sourcegitcommit: d11275796a1f65c31dd56b44a8a1bbaae4d7ec76
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761774"
---
# <a name="performance-recommendations-for-unity"></a>Unity のパフォーマンスに関する推奨事項

この記事は、[Mixed Reality のパフォーマンスに関する推奨事項](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)についての記事の内容が基になっていますが、Unity エンジン環境に固有の学習に焦点を当てています。

## <a name="use-recommended-unity-project-settings"></a>推奨される Unity プロジェクト設定を使用する

Unity で Mixed Reality アプリのパフォーマンスを最適化する際に最も重要な初めのステップは、[推奨される Unity の環境設定](recommended-settings-for-unity.md)を使用しているかどうかを確認することです。 この記事には、パフォーマンスに優れた Mixed Reality アプリを構築するための最も重要なシーン構成に関するコンテンツが含まれています。 これらの推奨設定の一部は、以下でも強調して示されています。

## <a name="how-to-profile-with-unity"></a>Unity でプロファイルする方法

Unity に組み込まれている **[Unity プロファイラー](https://docs.unity3d.com/Manual/Profiler.html)** は、特定のアプリに関する貴重なパフォーマンスの分析情報を収集するための優れたリソースです。 エディターでプロファイラーを実行できますが、これらのメトリックは実際のランタイム環境を表していないため、その結果は慎重に使用する必要があります。 最も正確で実用的な分析情報を得るには、デバイスでアプリケーションを実行しながらリモートでプロファイルすることをお勧めします。 さらに、Unity の [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html) も、利用すると非常に強力な分析情報ツールです。

Unity では、次のことに関する優れたドキュメントが提供されています。
1) [Unity プロファイラーを UWP アプリケーションにリモート](https://docs.unity3d.com/Manual/windowsstore-profiler.html)で接続する方法
2) [Unity プロファイラーでパフォーマンスの問題を効果的に診断する](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)方法

>[!NOTE]
> Unity プロファイラーを接続し、GPU プロファイラーを追加した後 (右上隅の「*プロファイラーの追加*」を参照)、プロファイラーの中央で CPU と GPU それぞれで費やされている時間を確認できます。 これにより、開発者は簡単に、アプリケーションが CPU バウンドか GPU バウンドかをだいたい確認できます。
>
> ![Unity の CPU と GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>CPU のパフォーマンスに関する推奨事項

以下では、特に Unity と C# の開発でのパフォーマンスに関する慣例についてさらに詳しく説明します。

#### <a name="cache-references"></a>参照をキャッシュする

初期化時に、関連するすべてのコンポーネントと GameObject への参照をキャッシュするのがベスト プラクティスです。 これは、 *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* のような関数呼び出しを繰り返すと、ポインターを格納するためのコストの方がメモリ コストよりかなり大きくなるためです。 これはまた、非常によく使用される [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html) にも当てはまります。 *Camera.main* では実際には基になっている *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* が使用されるだけであり、そこで行われるシーン グラフでの *"MainCamera"* タグの付いたカメラ オブジェクトの検索にはコストがかかります。

```CS
using UnityEngine;
using System.Collections;

public class ExampleClass : MonoBehaviour
{
    private Camera cam;
    private CustomComponent comp;

    void Start() 
    {
        cam = Camera.main;
        comp = GetComponent<CustomComponent>();
    }

    void Update()
    {
        // Good
        this.transform.position = cam.transform.position + cam.transform.forward * 10.0f;

        // Bad
        this.transform.position = Camera.main.transform.position + Camera.main.transform.forward * 10.0f;

        // Good
        comp.DoSomethingAwesome();

        // Bad
        GetComponent<CustomComponent>().DoSomethingAwesome();
    }
}
```

>[!NOTE] 
> GetComponent(string) を使用しない <br/>
> *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* を使用と、いくつかの異なるオーバーロードが発生します。 常に、型ベースの実装を使用し、文字列ベースの検索オーバーロードは使用しないことが重要です。 シーンでの文字列による検索は、型での検索よりかなりコストがかかります。 <br/>
> (正しい) Component GetComponent(Type type) <br/>
> (正しい) T GetComponent\<T>() <br/>
> (正しくない) Component GetComponent(string)> <br/>

#### <a name="avoid-expensive-operations"></a>コストのかかる操作を避ける

1) **[LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq) を使わないようにする**

    LINQ は非常にすっきりしていて、読みことも書くことも簡単な場合がありますが、一般に、アルゴリズムを手作業で記述するより、計算と、特にメモリの割り当てが、はるかに多く必要になります。

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) **一般的な Unity API**

    特定の Unity API は便利ですが、実行コストが非常に大きくなることがあります。 それらの多くには、シーン グラフ全体での、一致する GameObject のリストの検索が含まれます。 これらの操作は、一般に、参照をキャッシュするか、問題のある GameObject に対するマネージャー コンポーネントを実装して実行時に参照を追跡することで回避できます。

    ```csharp
        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()
    ```

>[!NOTE]
> *[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* と *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* は、絶対に除去する必要があります。 これらの関数は、関数を直接呼び出すより 1,000 倍も遅くなる可能性があります。

3) **ボックス化に注意する**

    [ボックス化](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing)は、C# 言語とランタイムの中核となる概念です。 これは、`char`、`int`、`bool` などの値型変数を参照型変数の中にラップするプロセスです。 値型変数が "ボックス化" されると、マネージド ヒープに格納される `System.Object` の内部にラップされます。 したがって、メモリが割り当てられ、最終的に破棄されるときは、ガベージ コレクターによって処理される必要があります。 これらの割り当てと割り当て解除は、パフォーマンス コストの原因になり、多くのシナリオでは、不要であるか、低コストの代替手段で簡単に置き換えることができます。

    ボックス化を回避するには、数値型と構造体 (`Nullable<T>` を含む) が格納される変数、フィールド、プロパティを、オブジェクトを使用するのではなく、`int`、`float?`、`MyStruct` などの特定の型として厳密に型指定します。  これらのオブジェクトをリストに配置する場合は、`List<object>` や `ArrayList` ではなく、`List<int>` などの厳密に型指定されたリストを使用します。

    **C# でのボックス化の例**

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

#### <a name="repeating-code-paths"></a>コード パスの繰り返し

繰り返し実行される Unity コールバック関数 ( Update など) で、1 秒間またはフレームごとの実行回数多いものは、非常に慎重に記述する必要があります。 ここでコストのかかる操作を行うと、パフォーマンスが常に大きな影響を受けるようになります。

1) **空のコールバック関数**

    次のようなコードはアプリケーション内に残しても害がないように見えますが、特にすべての Unity スクリプトがこのコード ブロックで自動的に初期化するため、これらの空のコールバックは実際には非常に高コストになる可能性があります。 Unity では、UnityEngine コードとアプリケーション コードの間で、アンマネージド コードとマネージド コードの境界を越えて行き来する動作が発生します。 実行するものがない場合であっても、このブリッジを越えるコンテキストの切り替えには大きなコストがかかります。 繰り返し呼び出される空の Unity コールバックを持つコンポーネントが含まれる GameObject がアプリに何百個もある場合、これは特に問題になります。

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> このようなパフォーマンスの問題の原因として最も一般的なものは Update() ですが、次のような他の反復的な Unity コールバックも、さらに悪くはないにしても、同程度に悪影響を及ぼす可能性があります: FixedUpdate()、LateUpdate()、OnPostRender()、OnPreRender()、OnRenderImage() など。 

2) **フレームごとに 1 回実行したくなる操作**

    次の Unity API は、多くのホログラフィック アプリで一般的な操作です。 常に可能であるとは限りませんが、これらの関数の結果は、1 回計算すれば、アプリケーション全体で特定のフレームに対して再利用できることが非常によくあります。

    a) 一般に、基本的に同じ Raycast 操作をコンポーネントごとに繰り返し行うのではなく、シーンに対する視線 Raycast を処理する専用のシングルトン クラスまたはサービスを用意し、他のすべてのシーン コンポーネントではこの結果を再利用することがよい方法です。 もちろん、アプリケーションによっては、異なるオリジンからの Raycast、または異なる [LayerMask](https://docs.unity3d.com/ScriptReference/LayerMask.html) に対する Raycast が必要になる場合があります。
    
    ```csharp
        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()
    ```

    b) Update() などの繰り返される Unity コールバックでの GetComponent() 操作は、Start() または Awake() で[参照をキャッシュする](#cache-references)ことによって回避します
    
    ```csharp
        UnityEngine.Object.GetComponent()
    ```

    c) 可能であれば、初期化時にすべてのオブジェクトをインスタンス化し、[オブジェクト プーリング](#object-pooling)を使用して、アプリケーションの実行時全体を通して GameObject を再利用するのがよい方法です

    ```csharp
        UnityEngine.Object.Instantiate()
    ```

3) **インターフェイスと仮想コンストラクトを避ける**

    直接オブジェクトではなくインターフェイスを介した関数の呼び出し、または仮想関数の呼び出しは、直接コンストラクトまたは直接関数呼び出しを利用するより、はるかにコストがかかることがよくあります。 仮想関数またはインターフェイスが不要な場合は、削除する必要があります。 ただし、開発の共同作業、コードの読みやすさ、コードの保守性を容易にするためにこれらの方法を利用する場合は、一般に、これらの方法によるパフォーマンスへの影響とトレードオフする価値があります。

    一般に、このメンバーを上書きする必要があると明確に予想される場合を除き、フィールドや関数を仮想としてマークしないことをお勧めします。 `UpdateUI()` メソッドなど、フレームごとに何回も呼び出される高頻度のコード パスは (フレームごとに 1 回であっても)、特に注意して使用する必要があります。

4) **構造体を値で渡さないようにする**

    クラスとは異なり、構造体は値型であり、関数に直接渡すと、その内容が新しく作成されるインスタンスにコピーされます。 このコピーにより、CPU コストが発生し、スタックにメモリが追加されます。 小さい構造体であれば、通常、影響は最小限であるため、許容されます。 しかし、すべてのフレームで繰り返し呼び出される関数や、大きな構造体を受け取る関数の場合は、可能であれば、関数定義を変更して参照渡しにします。 [詳細については、こちらを参照してください](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a>その他

1) **物理計算**

    a) 一般に、物理計算を改善する最も簡単な方法は、物理計算にかける時間または 1 秒あたりの反復回数を制限することです。 もちろん、これによりシミュレーションの精度は低下します。 Unity の [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) を参照してください

    b) Unity でのコライダーの種類には、さまざまなパフォーマンス特性があります。 次に示すのは、コライダーをパフォーマンスが最もよいもの (左端) から最も悪いもの (右端) まで順に並べたものです。 メッシュ コライダーを避けることが最も重要です。メッシュ コライダーは、プリミティブ コライダーよりはるかにコストが高くなります。

    スフィア < カプセル < ボックス <<< メッシュ (凸) < メッシュ (凸なし)

    詳細については、[Unity の物理計算のベスト プラクティス](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)に関するページを参照してください

2) **アニメーション**

    Animator コンポーネントを無効にして、アイドル状態のアニメーションを無効にします (ゲーム オブジェクトを無効にしても同じ効果は得られません)。 同じものに値を設定するループ内にアニメーターを配置する設計パターンは避けます。 この方法にはかなりのオーバーヘッドがありますが、アプリケーションへの効果はありません。 [詳細については、こちらを参照してください。](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **複雑なアルゴリズム**

    アプリケーションで、逆キネマティクスやパス ファインディングなどの複雑なアルゴリズムを使用している場合は、より簡単なアプローチを見つけたり、パフォーマンスに関連する設定を調整したりします

## <a name="cpu-to-gpu-performance-recommendations"></a>CPU と GPU のパフォーマンスに関する推奨事項

一般に、CPU と GPU のパフォーマンスは、グラフィックスカードに送信される **描画呼び出し** に行き着きます。 パフォーマンスを向上させるには、最適な結果が得られるように描画呼び出しを戦略的に **a) 減らす** か、または **b) 再構築する** 必要があります。 描画呼び出し自体がリソースを集中的に使用するため、呼び出しを減らすと必要な作業全体が減ります。 さらに、描画呼び出し間の状態変化には、グラフィックス ドライバーでコストのかかる検証と変換のステップが必要であるため、アプリケーションの描画呼び出しを再構築して状態の変化を制限すると (つまり、 異なる素材など) パフォーマンスが向上する可能性があります。

Unity には、それらのプラットフォームに対する描画呼び出しのバッチ処理に関する概要と詳細がわかる優れた記事があります。
- [Unity の描画呼び出しのバッチ処理](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a>単一パス インスタンス化レンダリング

Unity の単一パス インスタンス化レンダリングを使用すると、各視点に対する描画呼び出しを 1 つのインスタンス化描画呼び出しに減らすことができます。 2 つの描画呼び出し間のキャッシュの一貫性により、GPU のパフォーマンスもある程度向上します。

Unity プロジェクトでこの機能を有効にするには
1)  **[Player XR Settings]\(プレーヤー XR 設定\)** を開きます ( **[Edit]\(編集\)**  >  **[Project Settings]\(プロジェクト設定\)**  >  **[Player]\(プレーヤー\)**  >  **[XR Settings]\(XR 設定\)** )
2) **[Stereo Rendering Method]\(ステレオ レンダリング方法\)** ドロップダウン メニューから **[Single Pass Instanced]\(単一パス インスタンス化\)** を選択します ( **[Virtual Reality Supported]\(仮想現実のサポート\)** チェック ボックスをオンにする必要があります)

このレンダリング方法の詳細については、Unity の次の記事をお読みください。
- [高度なステレオ レンダリングを使用して AR と VR のパフォーマンスを最大化する方法](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [単一パス インスタンス化](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> 単一パス インスタンス化レンダリングに関する一般的な問題の 1 つは、開発者がインスタンス化対応に作成されていない既存のカスタム シェーダーを持っている場合に発生します。 この機能を有効にした後、開発者は、一部の GameObject が 1 つの視線でしかレンダリングしないことに気付く場合があります。 これは、関連付けられたカスタム シェーダーに、インスタンス化のための適切なプロパティがないためです。
>
> この問題への対処方法については、Unity から提供されている [HoloLens 用の単一パス ステレオ レンダリング](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)に関する記事を参照してください

#### <a name="static-batching"></a>静的バッチ処理

Unity では、多くの静的オブジェクトをバッチ処理して、GPU への描画呼び出しを減らすことができます。 静的バッチ処理は、**1) 同じ素材を共有し**、**2) *Static* とマークされている**、Unity のほとんどの [Renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) オブジェクトで動作します (Unity でオブジェクトを選択し、インスペクターの右上にあるチェック ボックスをオンにします)。 *Static* とマークされている GameObject は、アプリケーションの実行時を通して移動できません。 そのため、事実上すべてのオブジェクトの配置、移動、スケーリングなどを行う必要がある HoloLens では、静的バッチ処理を利用することが困難な場合があります。イマーシブ ヘッドセットの場合、静的バッチ処理によって描画呼び出しが大幅に減少し、パフォーマンスが向上する可能性があります。

詳細については、[Unity の描画呼び出しのバッチ処理](https://docs.unity3d.com/Manual/DrawCallBatching.html)に関する記事の「*静的バッチ処理*」を参照してください。

#### <a name="dynamic-batching"></a>動的バッチ処理

HoloLens の開発では *Static* としてオブジェクトをマークすることには問題であるため、動的バッチ処理が、この機能がないことを補う優れたツールになる可能性があります。 もちろん、イマーシブ ヘッドセットにも役立つことがあります。 ただし、GameObject が **a) 同じ素材を共有し**、**b) それ以外の条件の長い一覧を満たす** 必要があるため、Unity で動的バッチ処理を有効にすることは難しい場合があります。

詳細については、[Unity の描画呼び出しのバッチ処理](https://docs.unity3d.com/Manual/DrawCallBatching.html)に関する記事の「*動的バッチ処理*」を参照してください。 ほとんどの場合、関連付けられたメッシュ データは 300 個より多くの頂点を持つことができないため、GameObject は動的バッチ処理が無効になります。

#### <a name="other-techniques"></a>その他の手法

バッチ処理は、複数の GameObject が同じ素材を共有できる場合にのみ使用できます。 通常、これは、GameObject ではそれぞれの素材に対して固有のテクスチャを持つ必要があるため妨げられます。 複数のテクスチャを 1 つの大きなテクスチャに結合するのが一般的であり、これは[テクスチャ アトラシング](https://en.wikipedia.org/wiki/Texture_atlas)と呼ばれる手法です。

さらに、一般に、可能かつ妥当であれば、複数のメッシュを 1 つの GameObject に結合することをお勧めします。 Unity では、各レンダラーには関連する描画呼び出しがあり、結合されたメッシュは 1 つのレンダラーで送信されます。

>[!NOTE]
> 実行時に Renderer.material のプロパティを変更すると、素材のコピーが作成されるため、バッチ処理が損なわれる可能性があります。 GameObject 間で共有される素材のプロパティを変更するには、Renderer.sharedMaterial を使用します。

## <a name="gpu-performance-recommendations"></a>GPU のパフォーマンスに関する推奨事項

詳細については、[Unity でのグラフィックス レンダリングの最適化](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)に関する記事を参照してください

### <a name="optimize-depth-buffer-sharing"></a>深度バッファーの共有を最適化する

一般に、[ホログラム安定性](../platform-capabilities-and-apis/Hologram-stability.md)に対して最適化するには、 **[Player XR Settings]\(プレーヤー XR 設定\)** の **[Depth buffer sharing]\(深度バッファー共有\)** を有効にすることをお勧めします。 ただし、この設定を使用して深度ベースの遅延ステージ再投影を有効にする場合は、**24 ビット深度形式** ではなく、**16 ビット深度形式** を選択することをお勧めします。 16 ビット深度バッファーを使用すると、深度バッファー トラフィックに関連付けられた帯域幅 (したがって電力) が大幅に減少します。 これは、電力の削減とパフォーマンスの向上の両方に大きなメリットがあります。 ただし、"*16 ビット深度形式*" を使用すると、2 つの悪影響が発生する可能性があります。

**Z ファイティング**

深度範囲の忠実性を低くすると、24 ビットより 16 ビットの方が [Z ファイティング](https://en.wikipedia.org/wiki/Z-fighting)が発生しやすくなります。 これらのアーティファクトを回避するには、[Unity カメラ](https://docs.unity3d.com/Manual/class-Camera.html)のニア/ファー クリップ プレーンを変更して、低い精度に対応します。 HoloLens ベースのアプリケーションでは、Unity の既定の1000 m ではなく、50 m のファー クリップ プレーンにすることで、一般に Z ファイティングを除去できます。

**ステンシル バッファーの無効化**

Unity で [16 ビット深度のレンダリング テクスチャ](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html)が作成されるときは、ステンシル バッファーは作成されません。 Unity のドキュメントによると、24 ビット深度形式を選択した場合は、24 ビットの z バッファーと共に [8 ビットのステンシル バッファー](https://docs.unity3d.com/Manual/SL-Stencil.html) が作成されます (デバイスで 32 ビットが適用されている場合。HoloLens などではこれが一般的です)。

### <a name="avoid-full-screen-effects"></a>全画面効果を避ける

全画面に対して動作する手法は、すべてのフレームで数百万の操作が行われるため、非常にコストが高くなる可能性があります。 したがって、アンチエイリアシングやブルームなどの[後処理効果](https://docs.unity3d.com/Manual/PostProcessingOverview.html)を回避することをお勧めします。

### <a name="optimal-lighting-settings"></a>最適な照明設定

Unity で[リアルタイム全体照明](https://docs.unity3d.com/Manual/GIIntro.html)を使用すると、極めて優れたビジュアル結果を得ることができますが、非常に高コストの照明計算が含まれます。 **[Window]\(ウィンドウ\)**  >  **[Rendering]\(レンダリング\)**  >  **[Lighting Settings]\(証明設定\)** で **[Real-time Global Illumination]\(リアルタイム全体照明\)** をオフにすることで、すべての Unity シーン ファイルでリアルタイム全体照明を無効にすることをお勧めします。

また、シャドウ キャストも、Unity シーンに高コストの GPU パスが追加されるため、すべて無効にすることをお勧めします。 シャドウはライトごとに無効にできますが、品質設定を使用することでまとめて制御することもできます。

**[Edit]\(編集\)**  >  **[Project Settings]\(プロジェクト設定\)** で **[Quality]\(品質\)** カテゴリを選択し、UWP プラットフォームに対して **[Low Quality]\(低品質\)** を選択します。 また、 **[Shadows]\(シャドウ\)** プロパティを **[Disable Shadows]\(シャドウを無効にする\)** に設定するだけでもかまいません。

Unity のモデルでは、ベイク済みライティングを使用することをお勧めします。

### <a name="reduce-poly-count"></a>多角形の数を減らす

通常、多角形の数は次のようにすると減ります
1) シーンからのオブジェクトの削除
2) 特定のメッシュに対する多角形の数が減る資産の間引き
3) 遠く離れたオブジェクトが同じジオメトリのローポリ バージョンでレンダリングされる[詳細度 (LOD) システム](https://docs.unity3d.com/Manual/LevelOfDetail.html)のアプリケーションへの実装

### <a name="understanding-shaders-in-unity"></a>Unity でのシェーダーについて

パフォーマンスでのシェーダーの比較を近似する簡単な方法は、実行時に各操作が実行される平均操作数を特定することです。 Unity ではこれを簡単に行うことができます。

1) シェーダー資産をまたは素材を選択した後、インスペクター ウィンドウの右上隅にある歯車アイコンを選択して、 **[Select Shader]\(シェーダーの選択\)** を選択します

    ![Unity でシェーダーを選択する](images/Select-shader-unity.png)
2) シェーダー資産を選択した状態で、インスペクター ウィンドウの下の **[Compile and show code]\(コードのコンパイルと表示\)** ボタンをクリックします

    ![Unity でシェーダー コードをコンパイルする](images/compile-shader-code-unity.PNG)

3) コンパイル後、頂点シェーダーとピクセル シェーダーの両方について、異なる操作の数に関する結果の統計セクションを確認します (注: ピクセル シェーダーはフラグメント シェーダーとも呼ばれます)

    ![Unity での標準シェーダー操作](images/unity-standard-shader-compilation.png)

#### <a name="optimize-pixel-shaders"></a>ピクセル シェーダーを最適化する

上記の方法を使用してコンパイル済みの統計結果を調べると、平均して[フラグメント シェーダー](https://en.wikipedia.org/wiki/Shader#Pixel_shaders)では一般に[頂点シェーダー](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)より多くの操作が実行されます。 ピクセル シェーダーとも呼ばれるフラグメント シェーダーは、画面出力のピクセルごとに実行されます。一方、頂点シェーダーは、画面に描画されるすべてのメッシュの頂点ごとにだけ実行されます。 

したがって、すべての照明計算のために、フラグメント シェーダーには頂点シェーダーより多くの命令があるだけでなく、ほとんどの場合、フラグメント シェーダーは大きなデータセットに対して実行されます。 たとえば、画面出力が 2k x 2k の画像の場合、フラグメント シェーダーは 2,000 * 2,000 = 400 万回実行される可能性があります。 2 つの視線をレンダリングする場合、2 つの画面があるため、この数は 2 倍になります。 複合現実アプリケーションに複数のパス、全画面の後処理効果、または同じピクセルへの複数のメッシュのレンダリングがある場合は、この数が大幅に増加します。 

したがって、フラグメント シェーダー内の操作の数を減らすと、通常、頂点シェーダーでの最適化より、はるかに大幅にパフォーマンスが向上します。

#### <a name="unity-standard-shader-alternatives"></a>Unity 標準シェーダーの代替手段

物理ベースのレンダリング (PBR) や他の高品質シェーダーを使用する代わりに、より高パフォーマンスで低コストのシェーダーを利用することを検討します。 [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) では、複合現実プロジェクト用に最適化された [MRTK 標準シェーダー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)が提供されています。

Unity では、unlit、vertex lit、および Unity 標準シェーダーより大幅に高速の他の単純化されたシェーダー オプションも提供されています。 詳細については、「[組み込みシェーダーの使用とパフォーマンス](https://docs.unity3d.com/Manual/shader-Performance.html)」を参照してください。

#### <a name="shader-preloading"></a>シェーダーのプリロード

[シェーダーの読み込み時間](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html)を最適化するには、*シェーダーのプリロード* や他のテクニックを使用します。 特に、シェーダーのプリロードは、シェーダーの実行時コンパイルによる遅延が発生しないことを意味します。

### <a name="limit-overdraw"></a>オーバードローを制限する

Unity では、**シーン ビュー** の左上隅にある [**描画モード メニュー**](https://docs.unity3d.com/Manual/ViewModes.html)を切り替えて **[Overdraw]\(オーバードロー\)** を選択することにより、シーンのオーバードローを表示できます。

一般に、GPU に送られる前にオブジェクトを事前にカリングすることで、オーバードローを軽減できます。 Unity では、エンジンに[オクルージョン カリング](https://docs.unity3d.com/Manual/OcclusionCulling.html)を実装する詳しい方法が提供されています。

## <a name="memory-recommendations"></a>メモリに関する推奨事項

過剰なメモリ割り当て操作と割り当て解除操作により、ホログラフィック アプリケーションに悪影響があり、その結果、一定しないパフォーマンス、フレームの凍結、その他の有害な動作が発生する可能性があります。 メモリ管理はガベージ コレクターによって制御されるため、Unity で開発するときは、メモリに関する考慮事項を理解することが特に重要です。

#### <a name="garbage-collection"></a>ガベージ コレクション

ホログラフィック アプリでは、ガベージ コレクター (GC) がアクティブ化されて、実行中にスコープ外になったオブジェクトを分析し、そのメモリを解放して再利用できるようにする必要がある場合、GC のために処理計算時間が失われます。 通常、継続的に割り当てと割り当て解除を行うと、より頻繁にガベージ コレクターを実行する必要があるため、パフォーマンスとユーザー エクスペリエンスが低下します。

Unity では、ガベージ コレクターの詳細なしくみと、メモリ管理に関してより効率的なコードを記述するためのヒントが説明された、優れたページが提供されています。
- [Unity ゲームでのガベージ コレクションの最適化](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

ガベージ コレクションが過剰になる最も一般的な状況の 1 つは、Unity の開発においてコンポーネントとクラスへの参照をキャッシュしないことです。 Start() または Awake() の間にすべての参照をキャプチャし、後の Update() や LateUpdate() などの関数で再利用する必要があります。

その他のクイックヒント:
- C# の [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder) クラスを使用して、実行時に複雑な文字列を動的に構築します
- アプリのすべてのビルド バージョンで実行されるため、Debug.Log() の呼び出しは不要になったら削除します
- ホログラフィック アプリで一般に多くのメモリが必要な場合は、読み込み中や移行中の画面を表示するときなど、読み込みフェーズの間に、[_**System.GC.Collect()**_](https://docs.microsoft.com/dotnet/api/system.gc.collect) を呼び出すことを検討します

#### <a name="object-pooling"></a>オブジェクト プーリング

オブジェクト プーリングは、オブジェクトの継続的な割り当てと割り当て解除のコストを削減するための一般的な手法です。 これを行うには、同一のオブジェクトの大規模なプールを割り当て、時間の経過と共にオブジェクトを絶えず生成して破棄するのではなく、このプールの非アクティブで使用可能なインスタンスを再利用します。 オブジェクト プールは、アプリの間の有効期間が一定ではない再使用可能なコンポーネントに最適です。

- [Unity でのオブジェクト プーリングのチュートリアル](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>開始時のパフォーマンス

比較的小さなシーンでアプリを開始してから、 *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* を使用して残りのシーンを読み込むことを検討する必要があります。 これにより、可能な限り速くアプリを対話状態にすることができます。 新しいシーンをアクティブ化するときは大きな CPU スパイクが発生する可能性があること、およびレンダリングされるコンテンツが途切れたり停止したりする場合があることに注意してください。 これを回避する方法の 1 つは、読み込まれるシーンで AsyncOperation.allowSceneActivation プロパティを "false" に設定し、シーンが読み込まれるまで待った後、画面を黒にクリアしてから、"true" に戻してシーンのアクティブ化を完了することです。

開始シーンが読み込まれている間、ユーザーにはホログラフィック スプラッシュ画面が表示されることに注意してください。

## <a name="see-also"></a>関連項目
- [Unity ゲームでのグラフィックス レンダリングの最適化](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [Unity ゲームでのガベージ コレクションの最適化](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- [物理計算のベスト プラクティス [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)
- [スクリプトの最適化 [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)
