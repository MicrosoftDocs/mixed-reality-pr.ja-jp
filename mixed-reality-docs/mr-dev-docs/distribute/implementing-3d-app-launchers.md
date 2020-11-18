---
title: 3D アプリ起動ツールの実装 (UWP アプリ)
description: HoloLens とイマーシブ (VR) ヘッドセットの両方で、Windows Mixed Reality UWP アプリとゲーム (Microsoft Store を通じて配布される) の3D アプリランチャーとロゴを作成する方法について説明します。
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D、ロゴ、アイコン、モデリング、ランチャー、3D ランチャー、タイル、live cube、ディープリンク、secondarytile、セカンダリタイル、UWP、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、XML、境界ボックス、unity
ms.openlocfilehash: 926d0b3bb337517b65986f85f6977b3dd1975735
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703198"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a>3D アプリ起動ツールの実装 (UWP アプリ)

> [!NOTE]
> この機能は、イマーシブヘッドセット用の2017フォール作成者更新プログラム (RS3) の一部として追加されました。 HoloLens では、Windows 10 April 2018 更新プログラムがサポートされています。 アプリケーションが10.0.16299 のバージョンをターゲットにしていることを確認してください。これは Windows SDK、HoloLens でのイマーシブヘッドセットと10.0.17125 の以上である必要があります。 最新の Windows SDK については、 [こちら](https://developer.microsoft.com/windows/downloads/windows-10-sdk)を参照してください。

[Windows Mixed Reality ホーム](../discover/navigating-the-windows-mixed-reality-home.md)は、アプリケーションを起動する前にユーザーが移動する開始点です。 Windows Mixed Reality の UWP アプリケーションを作成する場合、既定では、アプリはアプリのロゴを使用して2D スレートとして起動されます。 Windows Mixed Reality のエクスペリエンスを開発するときに、必要に応じて3D ランチャーを定義して、アプリケーションの既定の2D ランチャーをオーバーライドできます。 一般に、Windows Mixed Reality ホームからユーザーを取得するイマーシブアプリケーションを起動するには、3D ランチャーを使用することをお勧めします。一方、アプリが適切にアクティブ化されている場合は、既定の2D ランチャーが優先されます。 [3d ディープリンク (secondaryTile)](#3d-deep-links-secondarytiles)は、2d UWP アプリ内のコンテンツへの3d ランチャーとして作成することもできます。

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>3D アプリランチャー作成プロセス

3D アプリランチャーを作成するには、次の3つの手順を実行します。
1. [設計と concepting](3d-app-launcher-design-guidance.md)
2. [モデリングとエクスポート](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. アプリケーションへの統合 (この記事)

アプリケーションのランチャーとして使用する3D アセットは、互換性を確保するために、 [Windows Mixed Reality オーサリングガイドライン](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) を使用して作成する必要があります。 このオーサリング仕様に合わなかった資産は、Windows Mixed Reality ホームではレンダリングされません。

## <a name="configuring-the-3d-launcher"></a>3D ランチャーの構成

Visual Studio で新しいプロジェクトを作成すると、アプリの名前とロゴを表示する単純な既定のタイルが作成されます。 この2D 表現をカスタム3D モデルに置き換えるには、アプリケーションのアプリケーションマニフェストを編集して、既定のタイル定義の一部として "MixedRealityModel" 要素を追加します。 2D ランチャーに戻すには、マニフェストから MixedRealityModel 定義を削除するだけです。

### <a name="xml"></a>XML

最初に、現在のプロジェクトでアプリケーションパッケージマニフェストを見つけます。 既定では、マニフェストには package.appxmanifest という名前が付けられます。 Visual Studio を使用している場合は、ソリューションビューアーでマニフェストを右クリックし、[ **ソースの表示** ] を選択して編集用の xml を開きます。 

マニフェストの先頭に、uap5 スキーマを追加し、それを ignorable 名前空間として含めます。

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

次に、アプリケーションの既定のタイルで "MixedRealityModel" を指定します。

```xml
<Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="ExampleApp.App">
      <uap:VisualElements
        DisplayName="ExampleApp"
        Square150x150Logo="Assets\Logo.png"
        Square44x44Logo="Assets\SmallLogo.png"
        Description="ExampleApp"
        BackgroundColor="#464646">
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb" />
        </uap:DefaultTile>
        <uap:SplashScreen Image="Assets\SplashScreen.png" />
      </uap:VisualElements>
    </Application>
</Applications>
```

MixedRealityModel 要素は、アプリケーションパッケージに格納されている3D アセットを指すファイルパスを受け入れます。 現時点では、glb ファイル形式を使用して配信され、 [Windows Mixed Reality 3d アセットオーサリング手順](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) に対して作成された3d モデルのみがサポートされています。 アセットはアプリパッケージに保存する必要があり、アニメーションは現在サポートされていません。 "Path" パラメーターが空のままの場合、ウィンドウには3D ランチャーではなく2D スレートが表示されます。 **注:** glb 資産は、アプリをビルドして実行する前に、ビルド設定で "コンテンツ" としてマークする必要があります。


![ソリューションエクスプローラーで. glb を選択し、[プロパティ] セクションを使用して、ビルド設定で "コンテンツ" としてマークします。](images/buildsetting-content-300px.png)<br>
*ソリューションエクスプローラーで. glb を選択し、[プロパティ] セクションを使用して、ビルド設定で "コンテンツ" としてマークします。*

### <a name="bounding-box"></a>境界ボックス

境界ボックスを使用すると、必要に応じて、オブジェクトの周囲に追加のバッファー領域を追加できます。 境界ボックスは、中心点と範囲を使用して指定します。これは、境界ボックスの中心から各軸に沿った端までの距離を示します。 境界ボックスの単位は、1ユニット = 1 メーターにマップできます。 境界ボックスが指定されていない場合は、オブジェクトのメッシュに自動的に収まるようになります。 指定された境界ボックスがモデルより小さい場合、メッシュに合わせてサイズが変更されます。

境界ボックス属性のサポートには、MixedRealityModel 要素のプロパティとして Windows RS4 update が使用されます。 最初にアプリケーションマニフェストの最上部にある境界ボックスを定義するには、uap6 スキーマを追加し、それを無視できる名前空間として含めます。

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
次に、MixedRealityModel で、SpatialBoundingBox プロパティを設定して境界ボックスを定義します。 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>Unity の使用

Unity を使用する場合は、アプリケーションマニフェストを編集する前に、Visual Studio でプロジェクトをビルドして開く必要があります。 

>[!NOTE]
>新しい Visual Studio ソリューションをビルドして Unity からデプロイするときに、マニフェストで3D ランチャーを再定義する必要があります。

## <a name="3d-deep-links-secondarytiles"></a>3D ディープリンク (secondaryTiles)

> [!NOTE]
> この機能は、2017秋の RS3 (イマーシブ) のヘッドセット用に、年 4 2018 月の更新プログラム (RS4) の一部として追加されました。 アプリケーションで Windows SDK のバージョンが対象になっていることを確認します。これは、HoloLens の 10.0.16299 on イマーシブ (VR) ヘッドセットと10.0.17125 以上である必要があります。 最新の Windows SDK については、 [こちら](https://developer.microsoft.com/windows/downloads/windows-10-sdk)を参照してください。

>[!IMPORTANT]
>3D ディープリンク (secondaryTiles) は、2D UWP アプリでのみ機能します。 ただし、Windows Mixed Reality ホームから排他的なアプリを起動するための [3d アプリランチャー](implementing-3d-app-launchers.md) を作成できます。

Windows の [スタート] メニューの[2d セカンダリタイル](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles)と同じように、アプリから[windows mixed Reality ホーム](../discover/navigating-the-windows-mixed-reality-home.md)に3d モデルを配置する機能を、2d アプリ内のコンテンツへのディープリンクとして追加することで、windows Mixed reality 向けに2d アプリケーションを拡張できます。 たとえば、360°フォトビューアーアプリに直接リンクする360°の球体を作成したり、ユーザーが資産のコレクションから3D コンテンツを配置して、作成者に関する詳細ページを開いたりすることができます。 3D コンテンツを使用して2D アプリケーションの機能を拡張するには、次の2つの方法があります。

### <a name="creating-a-3d-secondarytile"></a>3D "secondaryTile" の作成

作成時に mixed reality モデルを定義することで、"secondaryTiles" を使用してアプリケーションの3D コンテンツを配置できます。 混合現実モデルは、アプリケーションパッケージ内の3D アセットを参照し、必要に応じて境界ボックスを定義することによって作成されます。 

> [!NOTE]
> 排他ビュー内から "secondaryTiles" を作成することは現在サポートされていません。

```cs
using Windows.UI.StartScreen;
using Windows.Foundation.Numerics;
using Windows.Perception.Spatial;

// Initialize the tile
SecondaryTile tile = new SecondaryTile("myTileId")
{
    DisplayName = "My Tile",
    Arguments = "myArgs"
};

tile.VisualElements.Square150x150Logo = new Uri("ms-appx:///Assets/MyTile/Square150x150Logo.png");

//Assign 3D model (only ms-appx and ms-appdata are allowed)
TileMixedRealityModel model = tile.VisualElements.MixedRealityModel;
model.Uri = new Uri("ms-appx:///Assets/MyTile/MixedRealityModel.glb");
model.ActivationBehavior = TileMixedRealityModelActivationBehavior.Default;
model.BoundingBox = new SpatialBoundingBox
{
    Center = new Vector3 { X = 1, Y = 0, Z = 0 },
    Extents = new Vector3 { X = 3, Y = 5, Z = 4 }
};

// And place it
await tile.RequestCreateAsync();
```

### <a name="bounding-box"></a>境界ボックス

境界ボックスを使用すると、オブジェクトの周囲に追加のバッファー領域を追加できます。 境界ボックスは、中心点と範囲を使用して指定します。これは、境界ボックスの中心から各軸に沿った端までの距離を示します。 境界ボックスの単位は、1ユニット = 1 メーターにマップできます。 境界ボックスが指定されていない場合は、オブジェクトのメッシュに自動的に収まるようになります。 指定された境界ボックスがモデルより小さい場合、メッシュに合わせてサイズが変更されます。

### <a name="activation-behavior"></a>アクティベーションの動作

> [!NOTE]
> この機能は、Windows RS4 update でサポートされる予定です。 この機能を使用する予定がある場合は Windows SDK、アプリケーションが10.0.17125 以上のバージョンを対象としていることを確認してください。

3D secondaryTile のアクティベーション動作を定義して、ユーザーがそれを選択したときの反応を制御できます。 これを使用すると、純粋な情報または装飾のある混合現実ホームに3D オブジェクトを配置できます。 次のアクティブ化動作の種類がサポートされています。
1. 既定: ユーザーが 3D secondaryTile を選択すると、アプリがアクティブ化されます
2. None: ユーザーが 3D secondaryTile を選択しても何も起こりません。アプリはアクティブ化されません。

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>既存の "secondaryTile" の取得と更新

開発者は、既存のセカンダリタイルの一覧を取得できます。これには、前に指定したプロパティが含まれます。 また、値を変更し、UpdateAsync () を呼び出すことによって、プロパティを更新することもできます。

```cs
// Grab the existing secondary tile
SecondaryTile tile = (await SecondaryTile.FindAllAsync()).First();

Uri updatedUri = new Uri("ms-appdata:///local/MixedRealityUpdated.glb");

// See if the model needs updating
if (!tile.VisualElements.MixedRealityModel.Uri.Equals(updatedUri))
{
    // Update it
    tile.VisualElements.MixedRealityModel.Uri = updatedUri;

    // And apply the changes
    await tile.UpdateAsync();
}
```

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a>ユーザーが Windows Mixed Reality であることを確認しています

3D ディープリンク (secondaryTiles) は、ビューが Windows Mixed Reality ヘッドセットに表示されている場合にのみ作成できます。 Windows Mixed Reality ヘッドセットにビューが表示されない場合は、エントリポイントを非表示にするか、エラーメッセージを表示することで、これを適切に処理することをお勧めします。 これを確認するには、 [IsCurrentViewPresentedOnHolographic ()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)に対してクエリを実行します。

## <a name="tile-notifications"></a>タイル通知

タイルの通知では、3D アセットを使用した更新の送信は現在サポートされていません。 これは、開発者が次のことを行うことができないことを意味します。
* プッシュ通知
* 定期的なポーリング
* スケジュールされた通知

その他のタイルの特徴と属性、およびそれらを2D タイルに使用する方法の詳細については、 [UWP アプリのドキュメントのタイル](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles)を参照してください。

## <a name="see-also"></a>関連項目

* 3D アプリランチャーを含む[Mixed reality モデルサンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)。
* [3D アプリ起動ツールの設計ガイダンス](3d-app-launcher-design-guidance.md)
* [Windows Mixed Reality ホームで使用するための3D モデルの作成](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [3D アプリランチャーの実装 (Win32 アプリ)](implementing-3d-app-launchers-win32.md)
* [Windows Mixed Reality ホームのナビゲーション](../discover/navigating-the-windows-mixed-reality-home.md)
