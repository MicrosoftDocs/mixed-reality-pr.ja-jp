---
title: Maquette のインストール
description: VSCode で Maquette をインストールして構成する方法について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality、Maquette、プロトタイプ、Mixed Reality、Virtual Reality、VR、MR、フィードバック、フィードバックハブ、バグ
ms.openlocfilehash: ba0064326e83f04b056c0baa2f86f718e41bedfe
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935427"
---
# <a name="installing-maquette"></a><span data-ttu-id="8b02a-104">Maquette のインストール</span><span class="sxs-lookup"><span data-stu-id="8b02a-104">Installing Maquette</span></span>

<!-- TODO(Harrison): Need consolidated logo with text. -->
<span data-ttu-id="8b02a-105">![ロゴ ](../images/MaquetteIcon.png) MaquetteScript のインストール</span><span class="sxs-lookup"><span data-stu-id="8b02a-105">![Logo](../images/MaquetteIcon.png) MaquetteScript Installation</span></span>

<!-- TODO(Stefan): Need more explanation on the .mqjs route for running MaquetteScript. -->
<span data-ttu-id="8b02a-106">MaquetteScript の開発は、主に VSCode 内で行われます。</span><span class="sxs-lookup"><span data-stu-id="8b02a-106">MaquetteScript development is primarily done within VSCode.</span></span> <span data-ttu-id="8b02a-107">MaquetteScript は、ファイルに格納されているスクリプトから実行すること `.mqjs` も、特殊な VSCode 拡張機能インターフェイスを使用して実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="8b02a-107">MaquetteScript can run from script contained in `.mqjs` files and also via a special VSCode extension interface.</span></span> <span data-ttu-id="8b02a-108">MaquetteScript VSCode 拡張機能を使用して、VSCode と Maquette の間の統合によって拡張インターフェイスを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="8b02a-108">Integration between VSCode and Maquette to enable the extension interface is accomplished with a MaquetteScript VSCode extension.</span></span>

## <a name="installing-the-vscode-extension"></a><span data-ttu-id="8b02a-109">VSCode 拡張機能のインストール</span><span class="sxs-lookup"><span data-stu-id="8b02a-109">Installing the VSCode Extension</span></span>

* <span data-ttu-id="8b02a-110">[Vscode](https://code.visualstudio.com)をダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="8b02a-110">Download and install [VSCode](https://code.visualstudio.com).</span></span> 

<span data-ttu-id="8b02a-111">Maquette javascript 拡張機能は [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript)にあります。</span><span class="sxs-lookup"><span data-stu-id="8b02a-111">The Maquette javascript extension is in [the Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript).</span></span>

* <span data-ttu-id="8b02a-112">[拡張機能のインストール手順](vscode:extension/ms-maquette.vscode-maquette-javascript)を実行します。</span><span class="sxs-lookup"><span data-stu-id="8b02a-112">Run the [installation procedure for the extension](vscode:extension/ms-maquette.vscode-maquette-javascript).</span></span>

<!-- TODO(Stefan): Are there plans to have the extension update manually in the future? If so, when will this be available? -->
`NOTE: The VSCode extension does not automatically update currently and will need to be updated manually.`

## <a name="enabling-scripting"></a><span data-ttu-id="8b02a-113">スクリプトの有効化</span><span class="sxs-lookup"><span data-stu-id="8b02a-113">Enabling Scripting</span></span>

<!-- TODO(Stefan): Is scripting still a pre-release only option? If and when will it be available for current users? -->
`PRE-RELEASE NOTE: Javascript is already embedded within Maquette but requires additional steps and settings to access and enable. Scripting is currently only available for pre-release testing and is not a visible option for current users. Ensure at least version 2020.3.0.0.1315 but preferably use latest version.`

<span data-ttu-id="8b02a-114">プレリリース中にスクリプトにアクセスできるようにするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="8b02a-114">To make scripting accessible during pre-release:</span></span>

* <span data-ttu-id="8b02a-115">という名前のファイルを `scripting.enabled` Maquette の Users Documents ディレクトリに配置します `~/Documents/Maquette/Settings` 。</span><span class="sxs-lookup"><span data-stu-id="8b02a-115">Put a file with the name `scripting.enabled` in the Users Documents directory for Maquette in: `~/Documents/Maquette/Settings`.</span></span>

<span data-ttu-id="8b02a-116">インストール後は、セキュリティ上の理由により、スクリプトは既定で無効になります。</span><span class="sxs-lookup"><span data-stu-id="8b02a-116">After installation, scripting will be disabled by default for security reasons.</span></span>

<!-- TODO(Stefan): Missing a first step where the user has to select the {} tab in VSCode, shown in the screenshot, to access the scripting enabled setting.
                   - Also missing instructions and screenshot on how to turn on scripting in the JSON settings file.
 -->
* <span data-ttu-id="8b02a-117">スクリプトの実行を有効にするには、コンパニオンウィンドウの [メイン] タブまたは json 設定ファイルを有効にします。</span><span class="sxs-lookup"><span data-stu-id="8b02a-117">To enable execution of script, turn it ON in the main tab of the companion window or in the json settings file.</span></span>

![VS Code でのスクリプト作成の有効化](images/IntroductionEnableScripting.png)


