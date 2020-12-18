---
title: Unity でサポートされている OpenXR プラグインの機能
description: Unity での mixed reality 開発に OpenXR がサポートする機能について説明します。
author: hferrone
ms.author: alexturn
ms.date: 12/15/2020
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 拡張現実, 仮想現実, mixed reality ヘッドセット, 学習, チュートリアル, 概要
ms.openlocfilehash: 1cbe9dd1ffb493bcc9da76e70dec9720f2d10340
ms.sourcegitcommit: 4bbf2f802117a9a3788b2b0e3b0a2f58e187f6ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2020
ms.locfileid: "97665364"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>Unity でサポートされている Mixed Reality OpenXR の機能

**Mixed Reality OpenXR プラグイン** パッケージは Unity の **OpenXR プラグイン** の拡張機能であり、HoloLens 2 および Windows Mixed Reality ヘッドセットの一連の機能をサポートしています。 続行する前に、 **unity 2020.2** 以降、 **OpenXR プラグインバージョン 0.1.1** 以降がインストールされていること、および unity プロジェクトが [OpenXR 用に構成](openxr-getting-started.md)されていることを確認してください。

## <a name="whats-supported"></a>サポートされる操作

現在、次の機能がサポートされています。

* Windows Mixed Reality ヘッドセット用の HoloLens 2 および Win32 VR アプリケーションの両方の UWP アプリケーションをサポートします。
* HoloLens 2 アプリケーションの UWP パッケージと CoreWindow の相互作用を最適化します。
* アンカーと無制限のスペースを使用したワールドスケールの追跡。
* [ストレージ API を固定](#anchors-and-anchor-persistence) して、HoloLens 2 ローカルストレージにアンカーを保持します。
* 新しい HP リバーブ G2 コントローラーを含む、[モーションコントローラーと手作業のやり取り](#motion-controller-and-hand-interactions)。
* 26個の関節と結合半径の入力を使用した、トレーラーを使用したハンドトラッキング。
* HoloLens 2 での視線の相互作用。
* HoloLens 2 で写真/ビデオ (PV) カメラを検索しています。
* PV カメラを使用した第3目のレンダリングを使用した Mixed Reality キャプチャ。
* [Holographic リモート処理アプリでの HoloLens 2 への "Play" を](#holographic-remoting-in-unity-editor-play-mode)サポートします。これにより、開発者は、デバイスにビルドしてデプロイすることなく、スクリプトをデバッグできます。
* Mrtk Unity 2.5.2 から MRTK OpenXR adapter パッケージに準拠しています。 <missing link>
* Unity [Arfoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 以降との互換性

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Unity エディター再生モードでの Holographic リモート処理

Visual Studio プロジェクトで UWP Unity プロジェクトをビルドしてから、パッケージ化して HoloLens 2 デバイスに配置すると、時間がかかることがあります。 1つの解決策は、Holographic エディターのリモート処理を有効にすることです。これにより、ネットワーク上の HoloLens 2 デバイスに対して "Play" モードで直接 C# スクリプトをデバッグできます。 このシナリオでは、UWP パッケージをビルドしてリモートデバイスに配置するオーバーヘッドを回避します。

1. まず、HoloLens 2 のストアから [Holographic Remoting Player アプリをインストール](https://www.microsoft.com/store/productId/9NBLGGH4SV40) する必要があります。  
2. HoloLens 2 で Holographic リモート処理プレーヤーアプリを実行すると、接続先のバージョン番号と IP アドレスが表示されます。
    * OpenXR プラグインを使用するには、v2.0 以降が必要です。

![HoloLens で実行されている Holographic リモート処理プレーヤーのスクリーンショット](images/openxr-features-img-01.png)

3. [ **編集-> プロジェクトの設定**] を開き、 **XR プラグイン管理** に移動して、[ **Windows Mixed Reality] 機能セット** ボックスをオンにします。

![XR プラグイン管理が強調表示されている Unity エディターで開いているプロジェクト設定パネルのスクリーンショット](images/openxr-features-img-02.png)

4. **OpenXR** の [**機能**] セクションを展開し、[**すべて表示**] を選択します。
5. [ **Holographic エディターリモート処理** ] チェックボックスをオンにして、Holographic リモート処理アプリから取得した IP アドレスを入力します。

![機能が強調表示されている Unity エディターでプロジェクト設定パネルが開いているスクリーンショット](images/openxr-features-img-03.png)

これで、[Play] \ (再生 \) ボタンをクリックして、HoloLens の Holographic リモート処理アプリで Unity アプリを再生できるようになりました。 また、 [Visual Studio を Unity にアタッチ](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) して、C# スクリプトを再生モードでデバッグすることもできます。

> [!NOTE]
> 0.1.0 のバージョンでは、Holographic リモート処理ではアンカー機能がサポートされておらず、ARAnchorManager 機能はリモート処理では機能しません。  この機能は今後のリリースで予定されています。

## <a name="anchors-and-anchor-persistence"></a>アンカーとアンカーの永続化

Mixed Reality OpenXR プラグインは、Unity の ARFoundation **ARAnchorManager** の実装を通じて基本的なアンカー機能を提供します。 Aranchor の **基本につい** ては、ARANCHOR の [AR アンカーマネージャーのマニュアル](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)を参照してください。 バージョン0.1.0 以降では、このプラグインは、プレーンにアタッチされたアンカーを作成する以外のすべての ARAnchorManager 機能をサポートしています。これは将来のリリースで予定されています。

### <a name="anchor-persistence-and-the-xranchorstore"></a>固定の永続性と XRAnchorStore

**XRAnchorStore** と呼ばれる追加の API を使用すると、セッション間でアンカーを永続化できます。 XRAnchorStore は、デバイスに保存されているアンカーの表現です。 アンカーは、Unity シーンの **Aranchors** から永続化したり、ストレージから新しい **aranchors** に読み込んだり、ストレージから削除したりできます。

> [!NOTE]
> これらのアンカーは保存され、同じデバイスに読み込まれます。 デバイス間のアンカーストレージは、今後のリリースで Azure 空間アンカーを通じてサポートされます。

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the 
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if 
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

XRAnchorStore を読み込むには、プラグインを使用して、XRAnchorSubsystem のサブシステムである ARAnchorManager の拡張メソッドを提供します。

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

この拡張メソッドを使用するには、次のように ARAnchorManager のサブシステムからアクセスします。
 
``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>(); 
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync(); 
```

アンカー > を永続化または非永続化する完全な例については、「 [Mixed Reality OpenXR Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples)」の「AnchorsSample.cs script and script」 (アンカーとアンカーの例) をご覧ください。

![[階層] パネルのスクリーンショット (アンカーのサンプルが強調表示された状態で、Unity エディターで開きます)](images/openxr-features-img-04.png)

![[インスペクター] サンプルスクリプトが強調表示された状態で、Unity エディターで開いているインスペクターパネルのスクリーンショット](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a>モーションコントローラーとハンド作用

Unity での mixed reality の相互作用の基本については、unity の unity の [XR 入力](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)に関するページを参照してください。 この Unity ドキュメントでは、コントローラー固有の入力から、より汎化された **Inputfeatureusage** へのマッピング、使用可能な XR 入力を識別および分類する方法、これらの入力からデータを読み取る方法などについて説明します。 
 
Mixed Reality OpenXR プラグインは、次に示すように、標準 **Inputfeatureusage** にマップされた追加の入力相互作用プロファイルを提供します。 
 
| InputFeatureUsage | HP リバーブ G2 コントローラー (OpenXR) | HoloLens (OpenXR) |
| ---- | ---- | ---- |
| primary2DAxis | ジョイ | |
| primary2DAxisClick | ジョイスティック-クリック | |
| トリガー (trigger) | トリガー  | |
| 把握 | 把握 | エアタップまたはつかみ |
| primaryButton | [X/A]-押します | エアタップ |
| secondaryButton | [Y/B]-押します | |
| gripButton | グリップ-押す | |
| triggerButton | トリガー-押す | |
| menuButton | メニュー | |

### <a name="aim-and-grip-poses"></a>目標とグリップ

OpenXR の入力相互作用を通じて、2組のポーズにアクセスできます。 
* 手の形でオブジェクトをレンダリングするためのグリップ
* 目標は、世界を指します。 

この設計の詳細と、2つの方法の違いについては、「 [OpenXR Specification-Input サブパス](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)」を参照してください。

InputFeatureUsages **Deviceposition**、 **Devicerotation**、 **devicevelocに** よって指定されたポーズ、およびすべてが OpenXR **グリップ** を表します。 グリップの設定に関連する InputFeatureUsages は、Unity の [commonusages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)で定義されています。

InputFeatureUsages **ポインター** によって提供されるポーズ、 **ポインターローテーション**、 **ポインター速度**、および **PointerAngularVelocity** all は、OpenXR **aim** を表します。 これらの InputFeatureUsages はインクルードされているすべての C# ファイルで定義されていないため、次のように独自の InputFeatureUsages を定義する必要があります。

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a>Haptics

Unity の XR 入力システムで haptics を使用する方法の詳細については、unity の unity [マニュアルの「UNITY XR](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)」を参照してください。 

## <a name="whats-coming-soon"></a>近日公開予定

次の問題および不足している機能は、Mixed Reality OpenXR プラグイン **バージョン 0.1.0** で知られています。 これらの機能については、今後のリリースで修正と新機能をリリースする予定です。

* **ARPlaneSubsystem** はまだサポートされていません。 HoloLens 2 では、 **Arplan emanager**、 **ARRaycastManager**、および ARANCHORMANAGER などの関連 API もサポートされていません **。**
* **アンカー** は Holographic リモート処理ではまだサポートされていませんが、近い将来に登場します。
* **手動メッシュ** 追跡、 **QR コード**、 **XRMeshSubsystem** はまだサポートされていません。
* **Azure 空間アンカー** のサポートは、今後のリリースで予定されています。
* **ARM64** は、HoloLens 2 アプリで唯一サポートされているプラットフォームです。 **ARM** プラットフォームは今後のリリースで予定されています。

## <a name="troubleshooting"></a>トラブルシューティング 

HoloLens 2 で Unity アプリを中断および再開すると、アプリは正しく再開できなくなります。これにより、HoloLens ビューでは、4つのスピン点が表示されます。 
* 回避策として、OpenXR プロジェクト設定で [ **深さの送信モード** ] を **[なし** ] に設定します。
