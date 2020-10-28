---
ms.openlocfilehash: dcbeceb4cbe6b87cd6458afa789f9e09abaf7f3d
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638734"
---
# <a name="all-platforms"></a>[<span data-ttu-id="da993-101">すべてのプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="da993-101">All platforms</span></span>](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a><span data-ttu-id="da993-102">HP Motion Controller プラグインを有効にしています</span><span class="sxs-lookup"><span data-stu-id="da993-102">Enabling HP Motion Controller Plugin</span></span> 

<span data-ttu-id="da993-103">相互作用プロファイルとコントローラーマッピングは、HP Motion Controller プラグインに含まれています。このプラグインは、コントローラーマッピングを Unreal の入力システムに公開するために有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="da993-103">The interaction profile and controller mappings are in the HP Motion Controller plugin, which must be enabled to expose the controller mappings to Unreal’s input system.</span></span>

![OpenXRHPController プラグインを有効にする](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[<span data-ttu-id="da993-105">SteamVR</span><span class="sxs-lookup"><span data-stu-id="da993-105">SteamVR</span></span>](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a><span data-ttu-id="da993-106">スタートアップと HMDPluginPriority の構成</span><span class="sxs-lookup"><span data-stu-id="da993-106">Configuring Startup and HMDPluginPriority</span></span>

<span data-ttu-id="da993-107">SteamVR を使用しない場合の入力には、いくつかの違いがあります。</span><span class="sxs-lookup"><span data-stu-id="da993-107">Input in Unreal using SteamVR has a few differences.</span></span>  <span data-ttu-id="da993-108">プロジェクトを設定するときは、まず、vr を追加して、SteamVR の新しい入力システムを使用していることを確認し **ます。EnableVRInput = 1** が **Engine/Config/ConsoleVariables.ini** の **Startup** セクションにあります。</span><span class="sxs-lookup"><span data-stu-id="da993-108">When setting up the project, first ensure it is using SteamVR’s new input system by adding **vr.SteamVR.EnableVRInput=1** to the **Startup** section in **Engine/Config/ConsoleVariables.ini** .</span></span>  <span data-ttu-id="da993-109">この ini は、プロジェクトディレクトリではなく、エンジンインストールディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="da993-109">This ini is found in the engine install directory, not the project directory.</span></span>

![スタートアップ構成を更新しています](../images/reverb-g2-img-07.png)

<span data-ttu-id="da993-111">HP Motion Controller プラグインは、OpenXR を有効にします。</span><span class="sxs-lookup"><span data-stu-id="da993-111">The HP Motion Controller plugin will enable OpenXR.</span></span>  <span data-ttu-id="da993-112">OpenXR を使用していない場合は、ConsoleVariables.ini と同じディレクトリにある BaseEngine.ini で、SteamVR の HMDPluginPriority を編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da993-112">If you're not using OpenXR, you will need to edit the HMDPluginPriority of SteamVR in BaseEngine.ini in the same directory as ConsoleVariables.ini.</span></span>  <span data-ttu-id="da993-113">SteamVR 値を OpenXRHMD 値よりも大きい値に変更します。</span><span class="sxs-lookup"><span data-stu-id="da993-113">Change the SteamVR value to be greater than the OpenXRHMD value.</span></span>

![HMDPluginPriority 構成を更新しています](../images/reverb-g2-img-08.png)


