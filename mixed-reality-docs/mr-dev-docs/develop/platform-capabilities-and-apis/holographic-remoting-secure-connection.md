---
title: Holographic リモート処理の接続セキュリティを有効にする
description: このページでは、プレーヤーとリモートアプリの間で暗号化および認証された接続を使用するように Holographic リモート処理を構成する方法について説明します。
author: markkeinz
ms.author: makei
ms.date: 10/29/2020
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、セキュリティ、認証、サーバー対クライアント
ms.openlocfilehash: 4004c7534092c73fe478130b9d957461bb34bcfa
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679591"
---
# <a name="enabling-connection-security-for-holographic-remoting"></a><span data-ttu-id="6bbde-104">Holographic リモート処理の接続セキュリティを有効にする</span><span class="sxs-lookup"><span data-stu-id="6bbde-104">Enabling connection security for Holographic Remoting</span></span>

>[!IMPORTANT]
><span data-ttu-id="6bbde-105">このガイダンスは、HoloLens 2 の Holographic リモート処理に固有のものです。</span><span class="sxs-lookup"><span data-stu-id="6bbde-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="6bbde-106">このページでは、Holographic リモート処理のネットワークセキュリティの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-106">This page gives you an overview of network security for Holographic Remoting.</span></span> <span data-ttu-id="6bbde-107">次の情報が見つかります。</span><span class="sxs-lookup"><span data-stu-id="6bbde-107">You'll find information about</span></span>

* <span data-ttu-id="6bbde-108">Holographic リモート処理のコンテキストでのセキュリティと必要な理由</span><span class="sxs-lookup"><span data-stu-id="6bbde-108">security in the context of Holographic Remoting and why you might need it</span></span>
* <span data-ttu-id="6bbde-109">さまざまなユースケースに基づく推奨メジャー</span><span class="sxs-lookup"><span data-stu-id="6bbde-109">recommended measures based on different use cases</span></span>
* <span data-ttu-id="6bbde-110">Holographic リモート処理ソリューションへのセキュリティの実装</span><span class="sxs-lookup"><span data-stu-id="6bbde-110">implementing security in your Holographic Remoting solution</span></span>

## <a name="overview"></a><span data-ttu-id="6bbde-111">概要</span><span class="sxs-lookup"><span data-stu-id="6bbde-111">Overview</span></span>

<span data-ttu-id="6bbde-112">Holographic リモート処理では、ネットワーク経由で情報を交換します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-112">Holographic Remoting exchanges information over a network.</span></span> <span data-ttu-id="6bbde-113">セキュリティ対策が実施されていない場合、同じネットワーク上の敵対者は、通信またはアクセスの機密情報の整合性を損なう可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6bbde-113">If no security measures are in place, adversaries on the same network may compromise the integrity of the communication or access confidential information.</span></span>

<span data-ttu-id="6bbde-114">Windows ストアのサンプルアプリと Holographic リモート処理プレーヤーには、セキュリティが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="6bbde-114">The sample apps and the Holographic Remoting Player in the Windows Store come with security disabled.</span></span> <span data-ttu-id="6bbde-115">そうすることで、サンプルがわかりやすくなります。</span><span class="sxs-lookup"><span data-stu-id="6bbde-115">Doing so makes the samples easier to understand.</span></span> <span data-ttu-id="6bbde-116">また、開発をより迅速に開始するのにも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-116">It also helps you to get started more quickly with development.</span></span>

<span data-ttu-id="6bbde-117">ただし、フィールドテストまたは実稼働環境での使用については、Holographic リモート処理ソリューションでセキュリティを有効にすることを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6bbde-117">For field testing or production use however, we strongly recommend enabling security in your Holographic Remoting solution.</span></span>

<span data-ttu-id="6bbde-118">Holographic リモート処理のセキュリティは、ユースケースに対して正しく設定されると、次の保証を提供します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-118">Security in Holographic Remoting, when set up correctly for your use case, gives you the following guarantees:</span></span>

* <span data-ttu-id="6bbde-119">**信頼性:** プレーヤーとリモートの両方のアプリが、相手側として要求されていることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-119">**Authenticity:** both player and remote app can be sure the other side is who they claim to be</span></span>
* <span data-ttu-id="6bbde-120">**機密性:** サードパーティが、windows media player とリモートアプリの間で交換される情報を読み取ることはできません。</span><span class="sxs-lookup"><span data-stu-id="6bbde-120">**Confidentiality:** no third party can read the information exchanged between player and remote app</span></span>
* <span data-ttu-id="6bbde-121">**整合性:** プレーヤーとリモートは、通信に対する転送中の変更を検出できます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-121">**Integrity:** player and remote can detect any in-transit changes to their communication</span></span>

>[!TIP]
><span data-ttu-id="6bbde-122">セキュリティ機能を使用できるようにするには、 [カスタムプレーヤー](holographic-remoting-create-player.md) と [カスタムリモートアプリ](holographic-remoting-create-host.md)の両方を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bbde-122">To be able to use security features, you will need to implement both a [custom player](holographic-remoting-create-player.md) and a [custom remote app](holographic-remoting-create-host.md).</span></span>

## <a name="planning-the-security-implementation"></a><span data-ttu-id="6bbde-123">セキュリティ実装の計画</span><span class="sxs-lookup"><span data-stu-id="6bbde-123">Planning the security implementation</span></span>

<span data-ttu-id="6bbde-124">Holographic リモート処理でセキュリティを有効にすると、ネットワーク経由で交換されるすべてのデータについて、暗号化および整合性チェックが自動的に有効になります。</span><span class="sxs-lookup"><span data-stu-id="6bbde-124">When you enable security in Holographic Remoting, the remoting library will automatically enable encryption and integrity checks for all data exchanged over the network.</span></span>

<span data-ttu-id="6bbde-125">適切な認証を確保するには、追加の作業が必要です。</span><span class="sxs-lookup"><span data-stu-id="6bbde-125">Ensuring proper authentication requires some extra work though.</span></span> <span data-ttu-id="6bbde-126">実際に必要なことは、ユースケースによって異なります。このセクションの残りの部分では、必要な手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-126">What exactly you need to do depends on your use case, and the rest of this section is about figuring out the necessary steps.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="6bbde-127">この記事では、一般的なガイダンスのみを提供します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-127">This article can only provide general guidance.</span></span> <span data-ttu-id="6bbde-128">わからない場合は、セキュリティの専門家に相談して、ユースケースに固有のガイダンスを提供することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="6bbde-128">If you feel unsure, consider consulting a security expert that can give you guidance specific to your use case.</span></span>

<span data-ttu-id="6bbde-129">まず、ネットワーク接続を記述するときに、 _クライアント_ と _サーバー_ という用語が使用されます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-129">First some terminology: when describing network connections, the terms _client_ and _server_ will be used.</span></span> <span data-ttu-id="6bbde-130">サーバーは既知のエンドポイントアドレスで着信接続をリッスンする側であり、クライアントはサーバーのエンドポイントに接続しています。</span><span class="sxs-lookup"><span data-stu-id="6bbde-130">The server is the side listening for incoming connections on a known endpoint address, and the client is the one connecting to the server's endpoint.</span></span>

>[!NOTE]
> <span data-ttu-id="6bbde-131">クライアントロールとサーバーロールは、アプリがプレーヤーとして動作しているか、リモートとして動作しているかに関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="6bbde-131">The client and and server roles are not tied to whether an app is acting as a player or as a remote.</span></span> <span data-ttu-id="6bbde-132">サンプルにはサーバーロールのプレーヤーが用意されていますが、ユースケースに適していれば、ロールを逆にするのは簡単です。</span><span class="sxs-lookup"><span data-stu-id="6bbde-132">While the samples have the player in the server role, it's easy to reverse the roles if it better fits your use case.</span></span>

### <a name="planning-the-server-to-client-authentication"></a><span data-ttu-id="6bbde-133">サーバー対クライアント認証の計画</span><span class="sxs-lookup"><span data-stu-id="6bbde-133">Planning the server-to-client authentication</span></span>

<span data-ttu-id="6bbde-134">サーバーは、デジタル証明書を使用して、クライアントに対して id を証明します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-134">The server uses digital certificates to prove its identity to the client.</span></span> <span data-ttu-id="6bbde-135">クライアントは、接続ハンドシェイクフェーズ中にサーバーの証明書を検証します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-135">The client validates the server's certificate during the connection handshake phase.</span></span> <span data-ttu-id="6bbde-136">クライアントがサーバーを信頼していない場合は、この時点で接続を終了します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-136">If the client doesn't trust the server, it will end the connection at this point.</span></span>

<span data-ttu-id="6bbde-137">クライアントがサーバー証明書を検証する方法と、使用できるサーバー証明書の種類は、ユースケースによって異なります。</span><span class="sxs-lookup"><span data-stu-id="6bbde-137">How the client validates the server certificate, and what kinds of server certificates can be used, depends on your use case.</span></span>

<span data-ttu-id="6bbde-138">**ユースケース 1:** サーバーのホスト名が固定されていないか、サーバーがホスト名でアドレス指定されていません。</span><span class="sxs-lookup"><span data-stu-id="6bbde-138">**Use case 1:** The server hostname isn't fixed, or the server isn't addressed by host name at all.</span></span>

<span data-ttu-id="6bbde-139">このユースケースでは、サーバーのホスト名に対して証明書を発行することは実用的ではありません (または可能です)。</span><span class="sxs-lookup"><span data-stu-id="6bbde-139">In this use case, it isn't practical (or even possible) to issue a certificate for the server's host name.</span></span> <span data-ttu-id="6bbde-140">ここでは、代わりに証明書の拇印を検証することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6bbde-140">The recommendation here is to validate the certificate's thumbprint instead.</span></span> <span data-ttu-id="6bbde-141">人間の指紋と同様に、拇印は証明書を一意に識別します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-141">Like a human fingerprint, the thumbprint uniquely identifies a certificate.</span></span>

<span data-ttu-id="6bbde-142">拇印は、帯域外でクライアントに対して通信することが重要です。</span><span class="sxs-lookup"><span data-stu-id="6bbde-142">It's important to communicate the thumbprint to the client out-of-band.</span></span> <span data-ttu-id="6bbde-143">つまり、リモート処理に使用されているのと同じネットワーク接続を経由して送信することはできません。</span><span class="sxs-lookup"><span data-stu-id="6bbde-143">That means, you can't send it over the same network connection that's used for remoting.</span></span> <span data-ttu-id="6bbde-144">代わりに、クライアントの構成に手動で入力することも、クライアントが QR コードをスキャンするようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-144">Instead, you could manually enter it into the client's configuration, or to have the client scan a QR code.</span></span>

<span data-ttu-id="6bbde-145">**ユースケース 2:** サーバーには、安定したホスト名を使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-145">**Use case 2:** The server can be reached over a stable host name.</span></span>

<span data-ttu-id="6bbde-146">このユースケースでは、サーバーに特定のホスト名があり、この名前が変更される可能性はありません。</span><span class="sxs-lookup"><span data-stu-id="6bbde-146">In this use case, the server has a specific host name, and you know this name isn't likely to change.</span></span> <span data-ttu-id="6bbde-147">その後、サーバーのホスト名に対して発行された証明書を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-147">You can then use a certificate issued to the server's host name.</span></span> <span data-ttu-id="6bbde-148">信頼は、ホスト名と証明書の信頼チェーンに基づいて確立されます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-148">Trust will be established based on the host name and the certificate's chain of trust.</span></span>

<span data-ttu-id="6bbde-149">このオプションを選択した場合、クライアントはサーバーのホスト名とルート証明書を事前に把握している必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bbde-149">If you choose this option, the client needs to know the server's host name and the root certificate in advance.</span></span>

### <a name="planning-the-client-to-server-authentication"></a><span data-ttu-id="6bbde-150">クライアントとサーバー間の認証の計画</span><span class="sxs-lookup"><span data-stu-id="6bbde-150">Planning the client-to-server authentication</span></span>

<span data-ttu-id="6bbde-151">クライアントは、自由形式トークンを使用してサーバーに対して認証を行います。</span><span class="sxs-lookup"><span data-stu-id="6bbde-151">Clients authenticate against the server using a free-form token.</span></span> <span data-ttu-id="6bbde-152">このトークンに含まれる内容は、ユースケースによって異なります。</span><span class="sxs-lookup"><span data-stu-id="6bbde-152">What this token should contain will again depend on your use case:</span></span>

<span data-ttu-id="6bbde-153">**ユースケース 1:** クライアントアプリの id のみを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bbde-153">**Use case 1:** You only need to verify the client app's identity.</span></span>

<span data-ttu-id="6bbde-154">このユースケースでは、共有シークレットで十分です。</span><span class="sxs-lookup"><span data-stu-id="6bbde-154">In this use case, a shared secret can be sufficient.</span></span> <span data-ttu-id="6bbde-155">このシークレットは、推測できないほど複雑である必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bbde-155">This secret must be complex enough that it can't be guessed.</span></span>

<span data-ttu-id="6bbde-156">適切な共有シークレットはランダムな GUID であり、サーバーとクライアントの両方の構成で手動で入力されます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-156">A good shared secret is a random GUID, which is manually entered in both the server's and client's configuration.</span></span> <span data-ttu-id="6bbde-157">たとえば、PowerShell でコマンドを使用して作成でき `New-Guid` ます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-157">To create one you can, for example, use the `New-Guid` command in PowerShell.</span></span>

<span data-ttu-id="6bbde-158">この共有シークレットが安全でないチャネルを介して伝達されることはないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="6bbde-158">Make sure this shared secret is never communicated over insecure channels.</span></span> <span data-ttu-id="6bbde-159">リモート処理ライブラリにより、共有シークレットは常に暗号化され、信頼されたピアにのみ送信されます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-159">The remoting library ensures that the shared secret is always sent encrypted, and only to trusted peers.</span></span>

<span data-ttu-id="6bbde-160">**ユースケース 2:** また、クライアントアプリのユーザーの id を確認する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="6bbde-160">**Use case 2:** You also need to verify the identity of the client app's user.</span></span>

<span data-ttu-id="6bbde-161">共有シークレットは、このユースケースに対応するのに十分ではありません。</span><span class="sxs-lookup"><span data-stu-id="6bbde-161">A shared secret won't be enough to cover this use case.</span></span> <span data-ttu-id="6bbde-162">代わりに、id プロバイダーによって作成されたトークンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-162">Instead, you can use tokens created by an identity provider.</span></span> <span data-ttu-id="6bbde-163">Id プロバイダーを使用する認証ワークフローは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6bbde-163">An authentication workflow using an identity provider would look like this:</span></span>

* <span data-ttu-id="6bbde-164">クライアントは id プロバイダーに対して承認を行い、トークンを要求します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-164">The client authorizes against the identity provider and requests a token</span></span>
* <span data-ttu-id="6bbde-165">Id プロバイダーは、トークンを生成し、それをクライアントに送信します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-165">The identity provider generates a token and sends it to the client</span></span>
* <span data-ttu-id="6bbde-166">クライアントは、Holographic Remoting を使用してこのトークンをサーバーに送信します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-166">The client sends this token to the server through Holographic Remoting</span></span>
* <span data-ttu-id="6bbde-167">サーバーは、クライアントのトークンを id プロバイダーに対して検証します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-167">The server validates the client's token against the identity provider</span></span>

<span data-ttu-id="6bbde-168">Id プロバイダーの1つの例として、 [Microsoft id プラットフォーム](https://docs.microsoft.com/azure/active-directory/develop/)があります。</span><span class="sxs-lookup"><span data-stu-id="6bbde-168">One example of an identity provider is the [Microsoft identity platform](https://docs.microsoft.com/azure/active-directory/develop/).</span></span>

<span data-ttu-id="6bbde-169">前のユースケースと同様に、これらのトークンが安全でないチャネル経由で送信されないようにするか、または公開するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="6bbde-169">Like in the previous use case, make sure these tokens aren't sent through insecure channels or otherwise exposed.</span></span>

## <a name="implementing-holographic-remoting-security"></a><span data-ttu-id="6bbde-170">Holographic リモート処理セキュリティの実装</span><span class="sxs-lookup"><span data-stu-id="6bbde-170">Implementing holographic remoting security</span></span>

<span data-ttu-id="6bbde-171">接続のセキュリティを有効にする場合は、カスタムのリモートアプリとプレーヤーアプリを実装する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6bbde-171">Remember that you need to implement custom remote and player apps if you want to enable connection security.</span></span> <span data-ttu-id="6bbde-172">提供されているサンプルは、独自のアプリの開始点として使用できます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-172">You can use the provided samples as starting points for your own apps.</span></span>

<span data-ttu-id="6bbde-173">セキュリティを有効にするには、ではなくを呼び出し、 `ListenSecure()` `Listen()` `ConnectSecure()` `Connect()` リモート処理接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-173">To enable security, call `ListenSecure()` instead of `Listen()`, and `ConnectSecure()` instead of `Connect()` to establish the remoting connection.</span></span>

<span data-ttu-id="6bbde-174">これらの呼び出しでは、セキュリティ関連の情報を提供および検証するために、特定のインターフェイスの実装を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bbde-174">These calls require you to provide implementations of certain interfaces for providing and validating security-related information:</span></span>

* <span data-ttu-id="6bbde-175">サーバーは、証明書プロバイダーと認証検証ツールを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bbde-175">The server needs to implement a certificate provider and an authentication validator</span></span>
* <span data-ttu-id="6bbde-176">クライアントは、認証プロバイダーと証明書検証を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bbde-176">The client needs to implement an authentication provider and a certificate validator.</span></span>

<span data-ttu-id="6bbde-177">すべてのインターフェイスには、アクションを実行するための関数があります。これは、コールバックオブジェクトをパラメーターとして受け取ります。</span><span class="sxs-lookup"><span data-stu-id="6bbde-177">All interfaces have a function requesting you to take action, which receives a callback object as parameter.</span></span> <span data-ttu-id="6bbde-178">このオブジェクトを使用すると、要求の非同期処理を簡単に実装できます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-178">Using this object, you can easily implement asynchronous handling of the request.</span></span> <span data-ttu-id="6bbde-179">このオブジェクトへの参照を保持し、非同期アクションが完了したときに completion 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-179">Keep a reference to this object, and call the completion function when the asynchronous action is complete.</span></span> <span data-ttu-id="6bbde-180">完了関数は、任意のスレッドから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-180">The completion function may be called from any thread.</span></span>

>[!TIP]
><span data-ttu-id="6bbde-181">WinRT インターフェイスの実装は、C++/winrtを使用して簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-181">Implementing WinRT interfaces can easily be done using C++/WinRT.</span></span> <span data-ttu-id="6bbde-182">この詳細については、「 [C++/WinRT での api の作成」を](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) 参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bbde-182">The [Author APIs with C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) chapter describes this in detail.</span></span>

>[!IMPORTANT]
><span data-ttu-id="6bbde-183">`build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl`NuGet パッケージ内には、セキュリティで保護された接続に関連する API の詳細なドキュメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6bbde-183">The `build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl` inside the NuGet package contains detailed documentation for the API related to secure connections.</span></span>

### <a name="implementing-a-certificate-provider"></a><span data-ttu-id="6bbde-184">証明書プロバイダーの実装</span><span class="sxs-lookup"><span data-stu-id="6bbde-184">Implementing a certificate provider</span></span>

<span data-ttu-id="6bbde-185">証明書プロバイダーは、使用する証明書をサーバーアプリケーションに提供します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-185">Certificate providers supply the server application with the certificate to use.</span></span> <span data-ttu-id="6bbde-186">実装は、次の2つの部分で構成されます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-186">The implementation consists of two parts:</span></span>

1) <span data-ttu-id="6bbde-187">インターフェイスを実装する証明書オブジェクト `ICertificate` 。</span><span class="sxs-lookup"><span data-stu-id="6bbde-187">A certificate object, which implements the `ICertificate` interface:</span></span>

    * <span data-ttu-id="6bbde-188">`GetCertificatePfx()` は、証明書ストアのバイナリコンテンツを返す必要があり `PKCS#12` ます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-188">`GetCertificatePfx()` should return the binary contents of a `PKCS#12` certificate store.</span></span> <span data-ttu-id="6bbde-189">ファイルには `.pfx` データが含まれている `PKCS#12` ため、ここで直接その内容を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-189">A `.pfx` file contains `PKCS#12` data, so its contents can be used directly here.</span></span>
    * <span data-ttu-id="6bbde-190">`GetSubjectName()` 使用する証明書を識別するフレンドリ名を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bbde-190">`GetSubjectName()` should return the friendly name that identifies the certificate to use.</span></span> <span data-ttu-id="6bbde-191">証明書にフレンドリ名が割り当てられていない場合、この関数は証明書のサブジェクト名を返します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-191">If no friendly name is assigned to the certificate, this function should return the certificate's subject name.</span></span>
    * <span data-ttu-id="6bbde-192">`GetPfxPassword()` は、証明書ストアを開くために必要なパスワードを返す必要があります (パスワードが不要な場合は、空の文字列が返されます)。</span><span class="sxs-lookup"><span data-stu-id="6bbde-192">`GetPfxPassword()` should return the password required to open the certificate store (or an empty string if no password is required).</span></span>

2) <span data-ttu-id="6bbde-193">インターフェイスを実装する証明書プロバイダー `ICertificateProvider` :</span><span class="sxs-lookup"><span data-stu-id="6bbde-193">A certificate provider implementing the `ICertificateProvider` interface:</span></span>
    * <span data-ttu-id="6bbde-194">`GetCertificate()` は、 `CertificateReceived()` コールバックオブジェクトに対してを呼び出すことによって、証明書オブジェクトを構築し、それを返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bbde-194">`GetCertificate()` should construct a certificate object and return it by calling `CertificateReceived()` on the callback object.</span></span>

### <a name="implementing-an-authentication-validator"></a><span data-ttu-id="6bbde-195">認証検証コントロールの実装</span><span class="sxs-lookup"><span data-stu-id="6bbde-195">Implementing an authentication validator</span></span>

<span data-ttu-id="6bbde-196">認証バリデーターは、クライアントから送信された認証トークンを受信し、検証結果を返します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-196">Authentication validators receive the authentication token sent by the client, and answer back with the validation result.</span></span>

<span data-ttu-id="6bbde-197">次のようにインターフェイスを実装し `IAuthenticationReceiver` ます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-197">Implement the `IAuthenticationReceiver` interface as follows:</span></span>

* <span data-ttu-id="6bbde-198">`GetRealm()` 認証領域の名前 (リモート処理接続のハンドシェイク中に使用される HTTP 領域) を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bbde-198">`GetRealm()` should return the name of the authentication realm (an HTTP realm  used during the remoting connection handshake).</span></span>
* <span data-ttu-id="6bbde-199">`ValidateToken()` では、クライアント認証トークンを検証し、 `ValidationCompleted()` 検証結果を使用してコールバックオブジェクトでを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bbde-199">`ValidateToken()` should validate the client authentication token and call `ValidationCompleted()` on the callback object with the validation result.</span></span>

### <a name="implementing-an-authentication-provider"></a><span data-ttu-id="6bbde-200">認証プロバイダーの実装</span><span class="sxs-lookup"><span data-stu-id="6bbde-200">Implementing an authentication provider</span></span>

<span data-ttu-id="6bbde-201">認証プロバイダーは、サーバーに送信される認証トークンを生成または取得します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-201">Authentication providers generate or retrieve the authentication token to be sent to the server.</span></span>

<span data-ttu-id="6bbde-202">次のようにインターフェイスを実装し `IAuthenticationProvider` ます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-202">Implement the `IAuthenticationProvider` interface as follows:</span></span>

* <span data-ttu-id="6bbde-203">`GetToken()` 送信する認証トークンを生成または取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bbde-203">`GetToken()` should generate or retrieve the authentication token to be sent.</span></span> <span data-ttu-id="6bbde-204">トークンの準備ができたら、 `TokenReceived()` コールバックオブジェクトに対してメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-204">Once the token is ready, call the `TokenReceived()` method on the callback object.</span></span>

### <a name="implementing-a-certificate-validator"></a><span data-ttu-id="6bbde-205">証明書検証を実装する</span><span class="sxs-lookup"><span data-stu-id="6bbde-205">Implementing a certificate validator</span></span>

<span data-ttu-id="6bbde-206">証明書検証ツールは、サーバーによって送信された証明書チェーンを受け取り、サーバーを信頼できるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-206">Certificate validators receive the certificate chain sent by the server and determine whether the server can be trusted.</span></span>

<span data-ttu-id="6bbde-207">証明書を検証するには、基になるシステムの検証ロジックを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-207">To validate certificates, you can use the validation logic of the underlying system.</span></span> <span data-ttu-id="6bbde-208">このシステム検証では、独自の検証ロジックをサポートするか、完全に置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-208">This system validation can either support your own validation logic, or replace it altogether.</span></span> <span data-ttu-id="6bbde-209">セキュリティで保護された接続を要求するときに、独自の証明書検証ツールを渡さないと、システムの検証が自動的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-209">If you don't pass your own certificate validator when requesting a secure connection, system validation will be used automatically.</span></span>

<span data-ttu-id="6bbde-210">Windows では、システム検証によって次のことが確認されます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-210">On Windows, the system validation will check for:</span></span>

* <span data-ttu-id="6bbde-211">証明書チェーンの整合性: 証明書は、信頼されたルート証明書で終了する一貫性のあるチェーンを形成します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-211">Integrity of the certificate chain: the certificates form a consistent chain that ends at a trusted root certificate</span></span>
* <span data-ttu-id="6bbde-212">証明書の有効性: サーバーの証明書は有効期間内であり、サーバー認証の目的で発行されます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-212">Certificate validity: the server's certificate is within its validity timespan, and is issued for the purpose of server authentication</span></span>
* <span data-ttu-id="6bbde-213">失効: 証明書が失効していません</span><span class="sxs-lookup"><span data-stu-id="6bbde-213">Revocation: The certificate hasn't been revoked</span></span>
* <span data-ttu-id="6bbde-214">名前の一致: サーバーのホスト名が、証明書が発行されたホスト名のいずれかと一致します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-214">Name match: The host name of the server matches one of the host names the certificate was issued for</span></span>

<span data-ttu-id="6bbde-215">次のようにインターフェイスを実装し `ICertificateValidator` ます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-215">Implement the `ICertificateValidator` interface as follows:</span></span>

 * <span data-ttu-id="6bbde-216">`PerformSystemValidation()``true`前述のシステム検証を実行する必要がある場合は、を返します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-216">`PerformSystemValidation()` should return `true` if a system validation as described above should be performed.</span></span> <span data-ttu-id="6bbde-217">この場合、システム検証の結果は、入力としてメソッドに渡され `ValidateCertificate()` ます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-217">In this case, the system validation result is passed as an input to the `ValidateCertificate()` method.</span></span>
* <span data-ttu-id="6bbde-218">`ValidateCertificate()` は、証明書チェーンを検証した後、 `CertificateValidated()` 最後の検証結果を使用して渡されたコールバックでを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bbde-218">`ValidateCertificate()` should validate the certificate chain and then call `CertificateValidated()` on the passed callback with the final validation result.</span></span> <span data-ttu-id="6bbde-219">このメソッドは、証明書チェーン、接続が確立されているサーバーの名前、および失効確認を強制する必要があるかどうかを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="6bbde-219">This method accepts the certificate chain, the name of the server the connection is being established with, and whether a revocation check should be forced.</span></span> <span data-ttu-id="6bbde-220">証明書チェーンに複数の証明書が含まれている場合、1つ目はサブジェクト証明書です。</span><span class="sxs-lookup"><span data-stu-id="6bbde-220">If the certificate chain contains multiple certificates, the first one is the subject certificate.</span></span>

>[!NOTE]
><span data-ttu-id="6bbde-221">ユースケースで異なる形式の検証が必要な場合は (上記の証明書のユースケース #1 を参照)、システムの検証を完全にバイパスします。</span><span class="sxs-lookup"><span data-stu-id="6bbde-221">If your use case requires a different form of validation (see certificate use case #1 above), bypass system validation entirely.</span></span> <span data-ttu-id="6bbde-222">代わりに、DER でエンコードされた x.509 証明書を処理できる任意の API またはライブラリを使用して、証明書チェーンをデコードし、ユースケースに必要なチェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="6bbde-222">Instead, use any API or library that can handle DER-encoded X.509 certificates to decode the certificate chain and perform the checks needed for your use case.</span></span>

## <a name="see-also"></a><span data-ttu-id="6bbde-223">参照</span><span class="sxs-lookup"><span data-stu-id="6bbde-223">See Also</span></span>
* [<span data-ttu-id="6bbde-224">Holographic Remoting リモート アプリの作成</span><span class="sxs-lookup"><span data-stu-id="6bbde-224">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="6bbde-225">カスタム Holographic リモート処理プレーヤーアプリの作成</span><span class="sxs-lookup"><span data-stu-id="6bbde-225">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="6bbde-226">Holographic リモート処理のトラブルシューティングと制限事項</span><span class="sxs-lookup"><span data-stu-id="6bbde-226">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="6bbde-227">Holographic Remoting ソフトウェア ライセンス条項</span><span class="sxs-lookup"><span data-stu-id="6bbde-227">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="6bbde-228">Microsoft プライバシーに関する声明</span><span class="sxs-lookup"><span data-stu-id="6bbde-228">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
