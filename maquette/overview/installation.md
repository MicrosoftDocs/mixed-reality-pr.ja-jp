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
# <a name="installing-maquette"></a>Maquette のインストール

<!-- TODO(Harrison): Need consolidated logo with text. -->
![ロゴ ](../images/MaquetteIcon.png) MaquetteScript のインストール

<!-- TODO(Stefan): Need more explanation on the .mqjs route for running MaquetteScript. -->
MaquetteScript の開発は、主に VSCode 内で行われます。 MaquetteScript は、ファイルに格納されているスクリプトから実行すること `.mqjs` も、特殊な VSCode 拡張機能インターフェイスを使用して実行することもできます。 MaquetteScript VSCode 拡張機能を使用して、VSCode と Maquette の間の統合によって拡張インターフェイスを有効にすることができます。

## <a name="installing-the-vscode-extension"></a>VSCode 拡張機能のインストール

* [Vscode](https://code.visualstudio.com)をダウンロードしてインストールします。 

Maquette javascript 拡張機能は [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript)にあります。

* [拡張機能のインストール手順](vscode:extension/ms-maquette.vscode-maquette-javascript)を実行します。

<!-- TODO(Stefan): Are there plans to have the extension update manually in the future? If so, when will this be available? -->
`NOTE: The VSCode extension does not automatically update currently and will need to be updated manually.`

## <a name="enabling-scripting"></a>スクリプトの有効化

<!-- TODO(Stefan): Is scripting still a pre-release only option? If and when will it be available for current users? -->
`PRE-RELEASE NOTE: Javascript is already embedded within Maquette but requires additional steps and settings to access and enable. Scripting is currently only available for pre-release testing and is not a visible option for current users. Ensure at least version 2020.3.0.0.1315 but preferably use latest version.`

プレリリース中にスクリプトにアクセスできるようにするには、次のようにします。

* という名前のファイルを `scripting.enabled` Maquette の Users Documents ディレクトリに配置します `~/Documents/Maquette/Settings` 。

インストール後は、セキュリティ上の理由により、スクリプトは既定で無効になります。

<!-- TODO(Stefan): Missing a first step where the user has to select the {} tab in VSCode, shown in the screenshot, to access the scripting enabled setting.
                   - Also missing instructions and screenshot on how to turn on scripting in the JSON settings file.
 -->
* スクリプトの実行を有効にするには、コンパニオンウィンドウの [メイン] タブまたは json 設定ファイルを有効にします。

![VS Code でのスクリプト作成の有効化](images/IntroductionEnableScripting.png)


