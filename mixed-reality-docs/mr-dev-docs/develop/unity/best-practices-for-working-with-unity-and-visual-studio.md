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
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a><span data-ttu-id="e3623-104">Unity と Visual Studio を使用するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="e3623-104">Best practices for working with Unity and Visual Studio</span></span>

<span data-ttu-id="e3623-105">Unity を使用して mixed reality アプリケーションを作成する場合は、Unity と Visual Studio を切り替えて、アプリパッケージを HoloLens またはイマーシブヘッドセットに構築してデプロイする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e3623-105">When you're creating a mixed reality application with Unity, you need to switch between Unity and Visual Studio to build and deploy the app package to HoloLens or an immersive headset.</span></span> <span data-ttu-id="e3623-106">既定では、Visual Studio の2つのインスタンスが必要です。 Unity スクリプトを変更し、別のインスタンスをデバイスに配置してデバッグするために必要です。</span><span class="sxs-lookup"><span data-stu-id="e3623-106">By default, two instances of Visual Studio are required - one instance to modify Unity scripts and another to deploy to the device and debug.</span></span> <span data-ttu-id="e3623-107">次の手順では、1つの Visual Studio インスタンスを使用して開発し、Unity プロジェクトをエクスポートする頻度を下げ、デバッグエクスペリエンスを向上させます。</span><span class="sxs-lookup"><span data-stu-id="e3623-107">The following instructions let you develop using a single Visual Studio instance, reducing the frequency of exporting Unity projects and improves the debugging experience.</span></span>

## <a name="improving-iteration-time"></a><span data-ttu-id="e3623-108">イテレーション時間の向上</span><span class="sxs-lookup"><span data-stu-id="e3623-108">Improving iteration time</span></span>

<span data-ttu-id="e3623-109">Unity での .NET スクリプティングバックエンドのサポートは、unity 2018 で非推奨とされ、Unity 2019 + で削除されました。</span><span class="sxs-lookup"><span data-stu-id="e3623-109">Support for .NET scripting back-end in Unity is being deprecated in Unity 2018 and removed in Unity 2019+.</span></span> <span data-ttu-id="e3623-110">そのため、 [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)に切り替えることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e3623-110">so we recommend you switch to [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html).</span></span> <span data-ttu-id="e3623-111">ただし、Unity から Visual Studio へのビルド時間が長くなることがあります。</span><span class="sxs-lookup"><span data-stu-id="e3623-111">However, you may experience longer build times from Unity to Visual Studio.</span></span> <span data-ttu-id="e3623-112">より迅速な反復処理を向上させるために、最適なコンパイル結果を得るために環境を設定します。</span><span class="sxs-lookup"><span data-stu-id="e3623-112">To improve for faster iteration, set up your environment for best compilation results:</span></span>

1) <span data-ttu-id="e3623-113">インクリメンタルビルドを使用して、毎回同じディレクトリにプロジェクトをビルドし、ビルド済みのファイルを再利用します。</span><span class="sxs-lookup"><span data-stu-id="e3623-113">Use incremental building by building your project to the same directory every time, reusing the pre-built files there</span></span>
2) <span data-ttu-id="e3623-114">プロジェクト & ビルドフォルダーに対するマルウェア対策ソフトウェアスキャンを無効にする</span><span class="sxs-lookup"><span data-stu-id="e3623-114">Disable anti-malware software scans for your project & build folders</span></span>
   - <span data-ttu-id="e3623-115">Windows 10 設定アプリで **ウイルス & 脅威保護** を開く</span><span class="sxs-lookup"><span data-stu-id="e3623-115">Open **Virus & threat protection** under your Windows 10 settings app</span></span>
   - <span data-ttu-id="e3623-116">[**ウイルス & 脅威保護の設定**] の下の [**設定の管理**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e3623-116">Select **Manage Settings** under **Virus & threat protection settings**</span></span>
   - <span data-ttu-id="e3623-117">[**除外**] セクションで [**除外の追加または削除**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e3623-117">Select **Add or remove exclusions** under the **Exclusions** section</span></span>
   - <span data-ttu-id="e3623-118">[ **除外の追加** ] を選択し、Unity プロジェクトコードとビルド出力を含むフォルダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="e3623-118">Select **Add an exclusion** and select the folder containing your Unity project code and build outputs</span></span>
3) <span data-ttu-id="e3623-119">SSD を使用してビルドする</span><span class="sxs-lookup"><span data-stu-id="e3623-119">Use an SSD for building</span></span>

<span data-ttu-id="e3623-120">詳細については、「 [IL2CPP のビルド時間の最適化](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3623-120">Review [Optimizing Build Times for IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) for more info.</span></span> <span data-ttu-id="e3623-121">また、 [IL2CPP Scripting バックエンドでのデバッグについて](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html)も確認してください。</span><span class="sxs-lookup"><span data-stu-id="e3623-121">Also, review [Debugging on IL2CPP Scripting Back-end](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html).</span></span>

<span data-ttu-id="e3623-122">[ *Unityscriptanalyzer* Visual Studio 拡張機能](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)をインストールすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="e3623-122">Consider installing the [*UnityScriptAnalyzer* Visual Studio extension](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer).</span></span> <span data-ttu-id="e3623-123">このツールは、より最適化された方法で記述できるコードの Unity C# スクリプトを分析します。</span><span class="sxs-lookup"><span data-stu-id="e3623-123">This tool analyzes your Unity C# scripts for code that can be written in a more optimized manner.</span></span>

## <a name="visual-studio-tools-for-unity"></a><span data-ttu-id="e3623-124">Visual Studio Tools for Unity</span><span class="sxs-lookup"><span data-stu-id="e3623-124">Visual Studio Tools for Unity</span></span>

<span data-ttu-id="e3623-125">ダウンロード [Visual Studio Tools for Unity](https://docs.microsoft.com/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)</span><span class="sxs-lookup"><span data-stu-id="e3623-125">Download [Visual Studio Tools for Unity](https://docs.microsoft.com/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)</span></span>

<span data-ttu-id="e3623-126">**Visual Studio Tools for Unity の利点**</span><span class="sxs-lookup"><span data-stu-id="e3623-126">**Benefits of Visual Studio Tools for Unity**</span></span>
* <span data-ttu-id="e3623-127">ブレークポイントを配置し、変数や複雑な式を評価することで、Visual Studio から Unity のエディター内再生モードをデバッグします。</span><span class="sxs-lookup"><span data-stu-id="e3623-127">Debug Unity in-editor play mode from Visual Studio by putting breakpoints, evaluating variables and complex expressions.</span></span>
* <span data-ttu-id="e3623-128">Unity プロジェクトエクスプローラーを使用して、Unity に表示されるのとまったく同じ階層のスクリプトを検索します。</span><span class="sxs-lookup"><span data-stu-id="e3623-128">Use the Unity Project Explorer to find your script with the exact same hierarchy that Unity displays.</span></span>
* <span data-ttu-id="e3623-129">Unity コンソールを Visual Studio 内で直接取得します。</span><span class="sxs-lookup"><span data-stu-id="e3623-129">Get the Unity console directly inside Visual Studio.</span></span>
* <span data-ttu-id="e3623-130">ウィザードを使用すると、スクリプトをすばやく作成したり、スクリプトに移動したりできます。</span><span class="sxs-lookup"><span data-stu-id="e3623-130">Use wizards to quickly create or navigate to scripts.</span></span>

## <a name="expose-c-class-variables-for-easy-tuning"></a><span data-ttu-id="e3623-131">簡単にチューニングできるように C# クラス変数を公開する</span><span class="sxs-lookup"><span data-stu-id="e3623-131">Expose C# class variables for easy tuning</span></span>

<span data-ttu-id="e3623-132">クラス変数を公開するには、2つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="e3623-132">There are two ways to expose class variables.</span></span> <span data-ttu-id="e3623-133">[SerializeField] 属性をプライベート変数に追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e3623-133">The recommended way is to add the [SerializeField] attribute to your private variables.</span></span> <span data-ttu-id="e3623-134">シリアル化されたフィールドには、エディターからアクセスできますが、プログラムで公開することはできません。</span><span class="sxs-lookup"><span data-stu-id="e3623-134">Serialized fields can be accessed from the editor but not programmatically exposed.</span></span>  <span data-ttu-id="e3623-135">もう1つの方法は、C# クラスの変数をパブリックにして、エディターの UI で公開することです。</span><span class="sxs-lookup"><span data-stu-id="e3623-135">The other option is to make C# class variables public to expose them in the editor UI.</span></span> 

<span data-ttu-id="e3623-136">どちらの方法を使用しても、エディター内での変数の微調整が可能になります。これは、整備士のプロパティを調整する場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="e3623-136">Both approaches make it possible to easily tweak variables while playing in-editor, which is especially useful for tuning interaction mechanic properties.</span></span>

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a><span data-ttu-id="e3623-137">Windows SDK または Unity アップグレード後に UWP Visual Studio ソリューションを再生成する</span><span class="sxs-lookup"><span data-stu-id="e3623-137">Regenerate UWP Visual Studio solutions after Windows SDK or Unity upgrade</span></span>

<span data-ttu-id="e3623-138">ソース管理にチェックインされた UWP Visual Studio ソリューションは、新しい Windows SDK または Unity エンジンにアップグレードした後に最新の状態になります。</span><span class="sxs-lookup"><span data-stu-id="e3623-138">UWP Visual Studio solutions checked in to source control can get out-of-date after upgrading to a new Windows SDK or Unity engine.</span></span> <span data-ttu-id="e3623-139">Unity から新しい UWP ソリューションを構築して、チェックインされたソリューションに違いをマージすることで、最新ではないソリューションを解決できます。</span><span class="sxs-lookup"><span data-stu-id="e3623-139">You can resolve out-of-date solutions after by building a new UWP solution from Unity and merging differences into the checked-in solution.</span></span>

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a><span data-ttu-id="e3623-140">テキスト形式のアセットを使用して、コンテンツの変更を簡単に比較する</span><span class="sxs-lookup"><span data-stu-id="e3623-140">Use text-format assets for easy comparison of content changes</span></span>

<span data-ttu-id="e3623-141">アセットをテキスト形式で保存すると、Visual Studio でのコンテンツ変更の相違点を簡単に確認できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e3623-141">Storing assets in text format makes it easier to review content change diffs in Visual Studio.</span></span> <span data-ttu-id="e3623-142">アセットをテキスト形式で保存するには、[ **編集 > プロジェクトの設定** ] を選択し > エディター] を選択し、[ **資産のシリアル化** モード] を [ **テキストを強制** する] に変更します</span><span class="sxs-lookup"><span data-stu-id="e3623-142">You can store assets in text format by selecting **Edit > Project Settings > Editor** and change **Asset Serialization** mode to **Force Text**.</span></span> <span data-ttu-id="e3623-143">ただし、テキスト資産ファイルの変更をマージすると、エラーが発生しやすく、推奨されません。そのため、ソース管理で排他的なバイナリのチェックアウトを有効にすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="e3623-143">However, merging text asset file changes is error-prone and not recommended, so consider enabling exclusive binary checkouts in your source control.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3623-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="e3623-144">See also</span></span>
- [<span data-ttu-id="e3623-145">Visual Studio Tools for Unity</span><span class="sxs-lookup"><span data-stu-id="e3623-145">Visual Studio Tools for Unity</span></span>](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [<span data-ttu-id="e3623-146">IL2CPP のビルド時間の最適化</span><span class="sxs-lookup"><span data-stu-id="e3623-146">Optimizing Build Times for IL2CPP</span></span>](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [<span data-ttu-id="e3623-147">*Unityscriptanalyzer* Visual Studio 拡張機能</span><span class="sxs-lookup"><span data-stu-id="e3623-147">*UnityScriptAnalyzer* Visual Studio extension</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)
