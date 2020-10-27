---
ms.openlocfilehash: dcbeceb4cbe6b87cd6458afa789f9e09abaf7f3d
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638734"
---
# <a name="all-platforms"></a>[すべてのプラットフォーム](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a>HP Motion Controller プラグインを有効にしています 

相互作用プロファイルとコントローラーマッピングは、HP Motion Controller プラグインに含まれています。このプラグインは、コントローラーマッピングを Unreal の入力システムに公開するために有効にする必要があります。

![OpenXRHPController プラグインを有効にする](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a>スタートアップと HMDPluginPriority の構成

SteamVR を使用しない場合の入力には、いくつかの違いがあります。  プロジェクトを設定するときは、まず、vr を追加して、SteamVR の新しい入力システムを使用していることを確認し **ます。EnableVRInput = 1** が **Engine/Config/ConsoleVariables.ini** の **Startup** セクションにあります。  この ini は、プロジェクトディレクトリではなく、エンジンインストールディレクトリにあります。

![スタートアップ構成を更新しています](../images/reverb-g2-img-07.png)

HP Motion Controller プラグインは、OpenXR を有効にします。  OpenXR を使用していない場合は、ConsoleVariables.ini と同じディレクトリにある BaseEngine.ini で、SteamVR の HMDPluginPriority を編集する必要があります。  SteamVR 値を OpenXRHMD 値よりも大きい値に変更します。

![HMDPluginPriority 構成を更新しています](../images/reverb-g2-img-08.png)


