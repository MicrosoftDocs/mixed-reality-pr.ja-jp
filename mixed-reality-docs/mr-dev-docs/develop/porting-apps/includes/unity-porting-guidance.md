---
ms.openlocfilehash: bf6b98eca850d2b280e7a016799c4287955159a6
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443679"
---
# <a name="project-settings"></a>[プロジェクト設定](#tab/project)

### <a name="1-review-the-common-porting-steps-listed-above"></a>1. 上記の一般的な移植手順を確認してください

開発環境が正しく設定されていることを確認するために、上記の一般的な手順を確認してください。 Visual Studio を使用している場合は、手順 #3 で、[ **Unity を使用したゲーム開発** ] ワークロードを選択する必要があります。 次の手順で新しいバージョンの Unity をインストールするため、"Unity エディターオプション" コンポーネントの選択を解除できます。

### <a name="2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>2. Windows MR サポートを使用して Unity の最新のパブリックビルドにアップグレードする
1. Mixed reality サポートを使用して、 [Unity の最新の推奨パブリックビルド](../../install-the-tools.md) をダウンロードします。
2. 作業を開始する前にプロジェクトのコピーを保存する
3. 以前のバージョンの Unity でプロジェクトがビルドされている場合は、アップグレード時に Unity から入手できる [ドキュメント](https://docs.unity3d.com/Manual/UpgradeGuides.html) を確認してください。
4. Unity のサイトで自動 API アップデーターを使用する [手順](https://docs.unity3d.com/Manual/APIUpdater.html) に従います。
5. プロジェクトを実行するために必要な追加の変更があるかどうかを確認し、残りのエラーと警告を解決します。 

> [!Note] 
> 依存しているミドルウェアがある場合は、最新のリリースを使用していることを確認してください (以下の手順 3. の詳細)。

### <a name="3-upgrade-your-middleware-to-the-latest-versions"></a>3. ミドルウェアを最新バージョンにアップグレードする

Unity の更新プログラムでは、ゲームまたはアプリケーションが依存している1つ以上のミドルウェアパッケージを更新することが必要になる可能性があります。 さらに、最新のミドルウェアで最新の状態になると、移植プロセスの残りの部分全体で成功の可能性が高まります。

### <a name="4-target-your-application-to-run-on-win32"></a>4. Win32 で実行するようにアプリケーションをターゲットにする

Unity アプリケーション内から:

* ファイル > のビルド設定に移動します
* [PC、Mac、Linux スタンドアロン] を選択します。
* ターゲットプラットフォームを "Windows" に設定します
* アーキテクチャを "x86" に設定し、[プラットフォームの切り替え] を選択します。

> [!NOTE] 
> アプリケーションがデバイス固有のサービスに依存している場合 (ストリームからの照合など)、この手順で無効にする必要があります。 後で Windows が提供する同等のサービスにフックできます。

### <a name="5-setup-your-windows-mixed-reality-hardware"></a>5. Windows Mixed Reality ハードウェアをセットアップする
1. [イマーシブヘッドセットのセットアップ](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)の手順を確認する
2. [Windows Mixed reality シミュレーターを使用する](../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)方法と[windows mixed Reality ホームを移動](../../../discover/navigating-the-windows-mixed-reality-home.md)する方法について説明します。

### <a name="6-target-your-application-to-run-on-windows-mixed-reality"></a>6. Windows Mixed Reality で実行するようにアプリケーションをターゲットにする
1. まず、特定の VR SDK に固有の他のライブラリサポートを削除するか、条件に応じてコンパイルする必要があります。 これらの資産は、Windows Mixed Reality などの他の VR Sdk と互換性のない方法でプロジェクトの設定とプロパティを頻繁に変更します。
    * たとえば、プロジェクトが SteamVR SDK を参照している場合は、代わりに、Windows Mixed Reality と SteamVR の両方をサポートする Unity の一般的な VR Api を使用するようにプロジェクトを更新する必要があります。
    * 条件付きで他の VR Sdk を除外するための具体的な手順は近日対応予定です。
2. Unity プロジェクトで、 [Windows 10 SDK を対象とする](../../unity/tutorials/holograms-100.md#target-windows-10-sdk)
3. シーンごとに、[カメラを設定します](../../unity/tutorials/holograms-100.md#chapter-2---setup-the-camera)。

### <a name="7-use-the-stage-to-place-content-on-the-floor"></a>7. ステージを使用して、床にコンテンツを配置します。

さまざまな [エクスペリエンススケール](../../../design/coordinate-systems.md)にわたって、混合した現実のエクスペリエンスを構築できます。

取り付けられている **スケールエクスペリエンス** を移植する場合は、Unity が **固定** の追跡領域の種類に設定されていることを確認する必要があります。

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

上記のコードでは、Unity のワールド座標系を設定して、 [参照の静止フレーム](../../../design/coordinate-systems.md#spatial-coordinate-systems)を追跡します。 静止の追跡モードでは、アプリの起動時に、カメラの既定の場所 (フォワードが Z) の前にエディターに配置されたコンテンツがユーザーの前に表示されます。 ユーザーが recenter した元の位置を確認するには、Unity の XR を呼び出すことができ [ます。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) メソッド。

継続的な **スケールエクスペリエンス** または **ルームスケールエクスペリエンス** を移植している場合は、フロアを基準にコンテンツを配置します。 ユーザーが定義したフロアレベルのオリジンとオプションの部屋の境界を表す **[空間ステージ](../../../design/coordinate-systems.md#spatial-coordinate-systems)** を使用して、ユーザーのフロアについては、最初の実行時に設定します。 これらのエクスペリエンスについては、Unity が **RoomScale** の追跡領域の種類に設定されていることを確認する必要があります。 RoomScale が既定値であるのに対し、明示的に設定して、ユーザーが自分のコンピューターを調整した部屋から離れた状況を検出するために、true に戻すことをお勧めします。

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

アプリで RoomScale の追跡領域の種類が正常に設定されると、y = 0 平面に配置されたコンテンツがフロア上に表示されます。 (0, 0, 0) の原点は、部屋のセットアップ中にユーザーがそこしたフロア上の特定の場所になります。これは、セットアップ中に接続されていた前方方向を表す-Z です。

スクリプトコードでは、TrackedArea の境界の種類を指定して、境界ポリゴンを取得するために、XR 型の TryGetGeometry メソッドを呼び出すことができます。 ユーザーが境界を定義している場合 (頂点の一覧を取得した場合)、ユーザーに **ルームスケールエクスペリエンス** を提供し、ユーザーが作成したシーンを周囲にたどることができます。

ユーザーがこの境界に近づいたときに、境界が自動的に表示されます。 アプリでは、境界自体をレンダリングするためにこの多角形を使用する必要はありません。

詳細については、「 [Unity の座標系](../../unity/coordinate-systems-in-unity.md) 」ページを参照してください。

<!-- Some applications use a rectangle to constrain their interaction. Retrieving the largest inscribed rectangle is not directly supported in the UWP API or Unity. The example code linked to below shows how to find a rectangle within the traced bounds. It's heuristic-based so may not find the optimal solution, however, results are consistent with expectations. Parameters in the algorithm can be tuned to find more precise results at the cost of processing time. The algorithm is in a fork of the Mixed Reality Toolkit that uses the 5.6 preview MRTP version of Unity. This isn't publicly available. The code should be directly usable in 2017.2 and higher versions of Unity. The code will be ported to the current MRTK in the near future. -->

結果の例:

![結果の例](../../porting-apps/images/largestrectangle-400px.jpg)

アルゴリズムは、Daniel Smilkov: [polygon 内の最大の四角形](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)によるブログに基づいています

### <a name="8-work-through-your-input-model"></a>8. 入力モデルを処理する

既存の HMD を対象とする各ゲームまたはアプリケーションには、処理する入力のセット、エクスペリエンスに必要な入力の種類、およびそれらの入力を取得するために呼び出す特定の Api が含まれます。 Windows Mixed Reality で利用可能な入力を活用するために、可能な限りシンプルで単純なものにするために投資してきました。
1. Windows Mixed Reality が入力を公開する方法と、それが現在のアプリケーションの動作にどのように対応しているかの詳細については、隣接するタブの **Unity の入力移植ガイド** を参照してください。

### <a name="9-performance-testing-and-tuning"></a>9. パフォーマンステストとチューニング

Windows Mixed Reality は、ハイエンドゲーム Pc から広範な市場メインストリーム Pc まで、さまざまな種類のデバイスで利用できます。 対象となる市場によっては、アプリケーションに対して使用可能なコンピューティングとグラフィックの予算に大きな違いがあります。 この移植の演習では、premium PC を利用している可能性があります。また、アプリで使用できるコンピューティングとグラフィックの大きな予算があります。 アプリをより広範囲のユーザーが使用できるようにする場合は、 [対象とする代表的なハードウェア](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)でアプリをテストしてプロファイリングする必要があります。

[Unity](https://docs.unity3d.com/Manual/Profiler.html)と[Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index)のどちらにも、パフォーマンスプロファイラーと、パフォーマンスプロファイルと最適化に関する[Microsoft](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)と[Intel](https://software.intel.com/articles/vr-content-developer-guide)の両方の発行ガイドラインが含まれています。 [混合現実のパフォーマンスを理解](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)することで、パフォーマンスに関する広範な説明があります。 さらに、unity の [パフォーマンスに関する推奨事項](../../unity/performance-recommendations-for-unity.md)には、unity に関する具体的な詳細があります。

# <a name="input-mapping"></a>[入力マッピング](#tab/input)

2つの方法のいずれかを使用して、入力ロジックを Windows Mixed Reality に移植できます。 Unity の一般的な入力です。複数のプラットフォームにまたがっている GetButton/GetAxis Api、または Windows 固有の XR です。付い.モーションコントローラーと HoloLens ハンド専用の豊富なデータを提供する入力 Api。

> [!IMPORTANT]
> HP リバーブ G2 コントローラーを使用している場合は、追加の入力マッピング手順については、こちらの [記事](../../unity/unity-reverb-g2-controllers.md) を参照してください。

## <a name="unity-xr-input-apis"></a>Unity XR 入力 Api

新しいプロジェクトの場合は、最初から新しい XR 入力 Api を使用することをお勧めします。 

[XR api](https://docs.unity3d.com/Manual/xr_input.html)の詳細については、こちらを参照してください。

## <a name="inputgetbuttongetaxis-apis"></a>GetButton/GetAxis Api の入力

Unity では、現在、一般的な入力である GetButton/GetAxis Api を使用して [、OCULUS sdk](https://docs.unity3d.com/Manual/OculusControllers.html) と [openvr sdk](https://docs.unity3d.com/Manual/OpenVRControllers.html)の入力を公開しています。 アプリが既にこれらの Api を入力に使用している場合は、これが Windows Mixed Reality でのモーションコントローラーをサポートするための最も簡単なパスです。入力マネージャーでボタンと軸を再マップするだけで済みます。

詳細については、「 [unity のボタン/軸マッピングテーブル](../../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) 」と「 [共通 unity api の概要](../../unity/gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)」を参照してください。

## <a name="windows-specific-xrwsainput-apis"></a>Windows 固有の XR。付い.入力 Api

> [!CAUTION]
> プロジェクトが XR のいずれかを使用している場合。WSA Api は、今後の Unity リリースで XR SDK を優先するように段階的に廃止されています。 新しいプロジェクトの場合は、最初から XR SDK を使用することをお勧めします。 [XR 入力システムと api](https://docs.unity3d.com/Manual/xr_input.html)の詳細については、こちらを参照してください。

アプリが各プラットフォームのカスタム入力ロジックを既に作成している場合は、 **XR** 名前空間の下で Windows 固有の空間入力 api を使用することを選択できます。 これにより、位置の精度やソースの種類などの追加情報にアクセスして、HoloLens で両手とコントローラーを区別できるようになります。

> [!NOTE]
> HP リバーブ G2 コントローラーを使用している場合、すべての入力 Api は、 **supportsTouchpad** を除くすべての入力 api を引き続き動作します。これは、タッチパッドデータなしで false を返します。

詳細については、「 [UnityEngine. XR api の概要](../../unity/gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)」を参照してください。

## <a name="grip-pose-vs-pointing-pose"></a>グリップポーズとポインティングポーズ

Windows Mixed Reality では、さまざまなフォームファクターでモーションコントローラーがサポートされています。各コントローラーの設計は、ユーザーの手の位置と、アプリがコントローラーを表示するときに使用する自然な "進む" 方向との間の関係において異なります。

これらのコントローラーをより適切に表現するために、相互作用ソースごとに調査できる2種類の方法があります。

* **グリップ** は、HoloLens によって検出されたハンドの位置を表します。または、運動コントローラーを持つパームです。
    * イマーシブヘッドセットでは、この方法を使用して、 **ユーザーの手** や、剣や銃などの **ユーザーの手に保持** されているオブジェクトをレンダリングすることをお勧めします。
    * **グリップの位置**: コントローラーを自然に保持するときのパーム重心。グリップ内の位置を中央に配置するように左右に調整されます。
    * **グリップの向きの右軸**: 手を完全に開いて平らな5本の指を作成した場合 (左側のパームから前方、右側のパームから後方)、
    * **グリップの向きの前方軸**: ハンドを部分的に閉じた場合 (コントローラーを保持している場合と同様)、非表示の指で形成されたチューブを通過する光線。
    * **グリップの向きの上位軸**: 右および順方向の定義によって暗黙的に示される上位軸。
    * このグリップには、Unity のクロスベンダ入力 API (XR) を使用してアクセスでき **[ます。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/Rotation**) または Windows 固有の API (**TryGetPosition/rotation**) を使用して、グリップを要求します。
* **ポインター** は、前方を指し示すコントローラーの先端を表します。
    * この方法は、コントローラーモデル自体をレンダリングするときに **UI をポイント** するときに raycast するために使用することをお勧めします。
    * 現時点では、ポインターのポーズは、Windows 固有の API (**Sourcestate/Rotation**) を介してのみ使用でき、ポインターのポーズを要求します。

これらの発生座標はすべて Unity のワールド座標で表現されます。
