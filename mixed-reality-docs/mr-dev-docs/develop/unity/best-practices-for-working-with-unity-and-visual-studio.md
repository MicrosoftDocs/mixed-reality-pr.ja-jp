---
title: Unity と Visual Studio を使用するためのベスト プラクティス
description: Unity と Visual Studio を使用した mixed reality アプリケーションの作成のワークフローを効率化するためのヒントとテクニックです。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: デプロイ、unity、visual studio、HoloLens、HoloLens 2、イマーシブヘッドセット、ベストプラクティス、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、UWP、Visual Studio Tools、Windows SDK
ms.openlocfilehash: 5e00b24c7a36ae83a281800e2c7d8b2fc377f178
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678847"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Unity と Visual Studio を使用するためのベスト プラクティス

Unity で mixed reality アプリケーションを作成する開発者は、Unity と Visual Studio を切り替えて、HoloLens やイマーシブヘッドセットにデプロイされたアプリケーションパッケージを作成する必要があります。 既定では、Visual Studio の2つのインスタンスが必要です (Unity スクリプトを変更し、1つをデバイスに配置してデバッグします)。 次の手順では、単一の Visual Studio インスタンスを使用して開発を行い、Unity プロジェクトをエクスポートする頻度を下げ、デバッグエクスペリエンスを向上させます。

## <a name="improving-iteration-time"></a>イテレーション時間の向上

Unity での .NET スクリプティングバックエンドのサポートは、unity 2018 で非推奨とされ、Unity 2019 + で削除されました。 そのため、 [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)に切り替えることをお勧めします。 ただし、Unity から Visual Studio へのビルド時間が長くなる可能性があります。 反復処理を高速化するために、最適なコンパイル結果を得るために環境を設定する必要があります。

1) 毎回同じディレクトリにプロジェクトをビルドして、インクリメンタルビルドを活用し、ビルド済みのファイルを再利用します。
2) プロジェクト & ビルドフォルダーに対するマルウェア対策ソフトウェアスキャンを無効にする
   - Windows 10 設定アプリで **ウイルス & 脅威保護** を開く
   - [**ウイルス & 脅威保護の設定**] の下の [**設定の管理**] を選択します。
   - [**除外**] セクションで [**除外の追加または削除**] を選択します。
   - [ **除外の追加** ] をクリックし、Unity プロジェクトコードとビルド出力を含むフォルダーを選択します。
3) SSD を使用してビルドする

詳細については、「 [IL2CPP のビルド時間の最適化](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) 」を参照してください。 また、 [IL2CPP Scripting バックエンドでのデバッグについて](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html)も確認してください。

さらに、 [ *Unityscriptanalyzer* Visual Studio 拡張機能](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)をインストールすることを検討してください。 このツールは、より最適化された方法で記述できる可能性のあるコードの Unity C# スクリプトを分析します。

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity

ダウンロード [Visual Studio Tools for Unity](https://docs.microsoft.com/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity?view=vs-2019)

**Visual Studio Tools for Unity の利点**
* ブレークポイントを配置し、変数や複雑な式を評価することで、Visual Studio から Unity のエディター内再生モードをデバッグします。
* Unity プロジェクトエクスプローラーを使用して、Unity に表示されるのとまったく同じ階層のスクリプトを検索します。
* Unity コンソールを Visual Studio 内で直接取得します。
* ウィザードを使用すると、スクリプトをすばやく作成したり、スクリプトに移動したりできます。

## <a name="expose-c-class-variables-for-easy-tuning"></a>簡単にチューニングできるように C# クラス変数を公開する

クラス変数を公開するには、2つの方法があります。 [SerializeField] 属性をプライベート変数に追加することをお勧めします。 これにより、エディターからアクセスできますが、プログラムで公開することはできません。  もう1つの方法は、C# クラスの変数をパブリックにして、エディターの UI で公開することです。 

どちらの方法でも、エディターでの再生中に変数を簡単に調整できるようになります。 これは特に、整備士プロパティを調整する場合に便利です。

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Windows SDK または Unity アップグレード後に UWP Visual Studio ソリューションを再生成する

ソース管理にチェックインされた UWP Visual Studio ソリューションは、新しい Windows SDK または Unity エンジンにアップグレードした後に最新の状態になります。 アップグレード後にこの問題を解決するには、Unity から新しい UWP ソリューションを構築し、すべての相違点をチェックインソリューションにマージします。

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>テキスト形式のアセットを使用して、コンテンツの変更を簡単に比較する

アセットをテキスト形式で保存すると、Visual Studio でのコンテンツ変更の相違点を簡単に確認できるようになります。 これは、 **資産のシリアル化** モードを [ **テキストを強制** する] に変更することで、[プロジェクト設定の編集 > > エディター] で有効にすることができます。 ただし、テキスト資産ファイルの変更をマージすると、エラーが発生しやすく、推奨されません。そのため、ソース管理システムで排他的なバイナリのチェックアウトを有効にすることを検討してください。

## <a name="see-also"></a>関連項目
- [Visual Studio Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [IL2CPP のビルド時間の最適化](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [*Unityscriptanalyzer* Visual Studio 拡張機能](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)
