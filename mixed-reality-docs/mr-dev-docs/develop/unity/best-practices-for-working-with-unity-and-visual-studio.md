---
title: Unity と Visual Studio のベストプラクティス
description: Unity と Visual Studio を使用した mixed reality アプリケーションの作成のワークフローを効率化するためのヒントとテクニックです。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: デプロイ、unity、visual studio、HoloLens、HoloLens 2、イマーシブヘッドセット、ベストプラクティス、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、UWP、Visual Studio Tools、Windows SDK
ms.openlocfilehash: 9464c86826b9a8ea2c64384dfa699fc6d98743dd
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009372"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Unity と Visual Studio を使用するためのベスト プラクティス

Unity を使用して mixed reality アプリケーションを作成する場合は、Unity と Visual Studio を切り替えて、アプリパッケージを HoloLens またはイマーシブヘッドセットに構築してデプロイする必要があります。 既定では、Visual Studio の2つのインスタンスが必要です。 Unity スクリプトを変更し、別のインスタンスをデバイスに配置してデバッグするために必要です。 次の手順では、1つの Visual Studio インスタンスを使用して開発し、Unity プロジェクトをエクスポートする頻度を下げ、デバッグエクスペリエンスを向上させます。

## <a name="improving-iteration-time"></a>イテレーション時間の向上

Unity での .NET スクリプティングバックエンドのサポートは、unity 2018 で非推奨とされ、Unity 2019 + で削除されました。 そのため、 [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)に切り替えることをお勧めします。 ただし、Unity から Visual Studio へのビルド時間が長くなることがあります。 より迅速な反復処理を向上させるために、最適なコンパイル結果を得るために環境を設定します。

1) インクリメンタルビルドを使用して、毎回同じディレクトリにプロジェクトをビルドし、ビルド済みのファイルを再利用します。
2) プロジェクト & ビルドフォルダーに対するマルウェア対策ソフトウェアスキャンを無効にする
   - Windows 10 設定アプリで **ウイルス & 脅威保護** を開く
   - [**ウイルス & 脅威保護の設定**] の下の [**設定の管理**] を選択します。
   - [**除外**] セクションで [**除外の追加または削除**] を選択します。
   - [ **除外の追加** ] を選択し、Unity プロジェクトコードとビルド出力を含むフォルダーを選択します。
3) SSD を使用してビルドする

詳細については、「 [IL2CPP のビルド時間の最適化](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) 」を参照してください。 また、 [IL2CPP Scripting バックエンドでのデバッグについて](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html)も確認してください。

[ *Unityscriptanalyzer* Visual Studio 拡張機能](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)をインストールすることを検討してください。 このツールは、より最適化された方法で記述できるコードの Unity C# スクリプトを分析します。

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity

ダウンロード [Visual Studio Tools for Unity](https://docs.microsoft.com/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)

**Visual Studio Tools for Unity の利点**
* ブレークポイントを配置し、変数や複雑な式を評価することで、Visual Studio から Unity のエディター内再生モードをデバッグします。
* Unity プロジェクトエクスプローラーを使用して、Unity に表示されるのとまったく同じ階層のスクリプトを検索します。
* Unity コンソールを Visual Studio 内で直接取得します。
* ウィザードを使用すると、スクリプトをすばやく作成したり、スクリプトに移動したりできます。

## <a name="expose-c-class-variables-for-easy-tuning"></a>簡単にチューニングできるように C# クラス変数を公開する

クラス変数を公開するには、2つの方法があります。 [SerializeField] 属性をプライベート変数に追加することをお勧めします。 シリアル化されたフィールドには、エディターからアクセスできますが、プログラムで公開することはできません。  もう1つの方法は、C# クラスの変数をパブリックにして、エディターの UI で公開することです。 

どちらの方法を使用しても、エディター内での変数の微調整が可能になります。これは、整備士のプロパティを調整する場合に特に便利です。

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Windows SDK または Unity アップグレード後に UWP Visual Studio ソリューションを再生成する

ソース管理にチェックインされた UWP Visual Studio ソリューションは、新しい Windows SDK または Unity エンジンにアップグレードした後に最新の状態になります。 Unity から新しい UWP ソリューションを構築して、チェックインされたソリューションに違いをマージすることで、最新ではないソリューションを解決できます。

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>テキスト形式のアセットを使用して、コンテンツの変更を簡単に比較する

アセットをテキスト形式で保存すると、Visual Studio でのコンテンツ変更の相違点を簡単に確認できるようになります。 アセットをテキスト形式で保存するには、[ **編集 > プロジェクトの設定** ] を選択し > エディター] を選択し、[ **資産のシリアル化** モード] を [ **テキストを強制** する] に変更します ただし、テキスト資産ファイルの変更をマージすると、エラーが発生しやすく、推奨されません。そのため、ソース管理で排他的なバイナリのチェックアウトを有効にすることを検討してください。

## <a name="see-also"></a>関連項目
- [Visual Studio Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [IL2CPP のビルド時間の最適化](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [*Unityscriptanalyzer* Visual Studio 拡張機能](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)
