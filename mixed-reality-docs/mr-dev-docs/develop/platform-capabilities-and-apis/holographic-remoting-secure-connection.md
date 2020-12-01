---
title: Holographic リモート処理の接続セキュリティを有効にする
description: このページでは、プレーヤーとリモートアプリの間で暗号化および認証された接続を使用するように Holographic リモート処理を構成する方法について説明します。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、セキュリティ、認証、サーバー対クライアント
ms.openlocfilehash: b2c054d19044b89b487331806b8256de1379fd53
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443461"
---
# <a name="enabling-connection-security-for-holographic-remoting"></a><span data-ttu-id="a13f6-104">Holographic リモート処理の接続セキュリティを有効にする</span><span class="sxs-lookup"><span data-stu-id="a13f6-104">Enabling connection security for Holographic Remoting</span></span>

>[!IMPORTANT]
><span data-ttu-id="a13f6-105">このガイダンスは、HoloLens 2 の Holographic リモート処理に固有のものです。</span><span class="sxs-lookup"><span data-stu-id="a13f6-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="a13f6-106">このページでは、Holographic リモート処理のネットワークセキュリティの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-106">This page gives you an overview of network security for Holographic Remoting.</span></span> <span data-ttu-id="a13f6-107">次の情報が見つかります。</span><span class="sxs-lookup"><span data-stu-id="a13f6-107">You'll find information about</span></span>

* <span data-ttu-id="a13f6-108">Holographic リモート処理のコンテキストでのセキュリティと必要な理由</span><span class="sxs-lookup"><span data-stu-id="a13f6-108">security in the context of Holographic Remoting and why you might need it</span></span>
* <span data-ttu-id="a13f6-109">さまざまなユースケースに基づく推奨メジャー</span><span class="sxs-lookup"><span data-stu-id="a13f6-109">recommended measures based on different use cases</span></span>
* <span data-ttu-id="a13f6-110">Holographic リモート処理ソリューションへのセキュリティの実装</span><span class="sxs-lookup"><span data-stu-id="a13f6-110">implementing security in your Holographic Remoting solution</span></span>

## <a name="overview"></a><span data-ttu-id="a13f6-111">概要</span><span class="sxs-lookup"><span data-stu-id="a13f6-111">Overview</span></span>

<span data-ttu-id="a13f6-112">Holographic リモート処理では、ネットワーク経由で情報を交換します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-112">Holographic Remoting exchanges information over a network.</span></span> <span data-ttu-id="a13f6-113">セキュリティ対策が実施されていない場合、同じネットワーク上の敵対者は、通信またはアクセスの機密情報の整合性を損なう可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a13f6-113">If no security measures are in place, adversaries on the same network may compromise the integrity of the communication or access confidential information.</span></span>

<span data-ttu-id="a13f6-114">Windows ストアのサンプルアプリと Holographic リモート処理プレーヤーには、セキュリティが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="a13f6-114">The sample apps and the Holographic Remoting Player in the Windows Store come with security disabled.</span></span> <span data-ttu-id="a13f6-115">そうすることで、サンプルがわかりやすくなります。</span><span class="sxs-lookup"><span data-stu-id="a13f6-115">Doing so makes the samples easier to understand.</span></span> <span data-ttu-id="a13f6-116">また、開発をより迅速に開始するのにも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-116">It also helps you to get started more quickly with development.</span></span>

<span data-ttu-id="a13f6-117">ただし、フィールドテストまたは実稼働環境での使用については、Holographic リモート処理ソリューションでセキュリティを有効にすることを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a13f6-117">For field testing or production use however, we strongly recommend enabling security in your Holographic Remoting solution.</span></span>

<span data-ttu-id="a13f6-118">Holographic リモート処理のセキュリティは、ユースケースに対して正しく設定されると、次の保証を提供します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-118">Security in Holographic Remoting, when set up correctly for your use case, gives you the following guarantees:</span></span>

* <span data-ttu-id="a13f6-119">**信頼性:** プレーヤーとリモートの両方のアプリが、相手側として要求されていることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-119">**Authenticity:** both player and remote app can be sure the other side is who they claim to be</span></span>
* <span data-ttu-id="a13f6-120">**機密性:** サードパーティが、windows media player とリモートアプリの間で交換される情報を読み取ることはできません。</span><span class="sxs-lookup"><span data-stu-id="a13f6-120">**Confidentiality:** no third party can read the information exchanged between player and remote app</span></span>
* <span data-ttu-id="a13f6-121">**整合性:** プレーヤーとリモートは、通信に対する転送中の変更を検出できます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-121">**Integrity:** player and remote can detect any in-transit changes to their communication</span></span>

>[!IMPORTANT]
><span data-ttu-id="a13f6-122">セキュリティ機能を使用できるようにするには、 [Windows Mixed Reality](holographic-remoting-create-remote-wmr.md) api または[OpenXR](holographic-remoting-create-remote-openxr.md) api を使用して、[カスタムプレーヤー](holographic-remoting-create-player.md)とカスタムリモートアプリの両方を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a13f6-122">To be able to use security features, you will need to implement both a [custom player](holographic-remoting-create-player.md) and a custom remote app using either [Windows Mixed Reality](holographic-remoting-create-remote-wmr.md) or [OpenXR](holographic-remoting-create-remote-openxr.md) APIs.</span></span>

>[!NOTE]
> <span data-ttu-id="a13f6-123">[2.4.0](holographic-remoting-version-history.md#v2.4.0)以降のバージョンでは、 [OpenXR API](../native/openxr.md)を使用したリモートアプリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-123">Starting with version [2.4.0](holographic-remoting-version-history.md#v2.4.0) remote apps using the [OpenXR API](../native/openxr.md) can be created.</span></span> <span data-ttu-id="a13f6-124">OpenXR 環境でセキュリティで保護された接続を確立する方法の概要については、 [以下](#secure-connection-using-the-openxr-api)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a13f6-124">An overview on how to establish a secure connection in an OpenXR environment can be found [below](#secure-connection-using-the-openxr-api).</span></span>

## <a name="planning-the-security-implementation"></a><span data-ttu-id="a13f6-125">セキュリティ実装の計画</span><span class="sxs-lookup"><span data-stu-id="a13f6-125">Planning the security implementation</span></span>

<span data-ttu-id="a13f6-126">Holographic リモート処理でセキュリティを有効にすると、ネットワーク経由で交換されるすべてのデータについて、暗号化および整合性チェックが自動的に有効になります。</span><span class="sxs-lookup"><span data-stu-id="a13f6-126">When you enable security in Holographic Remoting, the remoting library will automatically enable encryption and integrity checks for all data exchanged over the network.</span></span>

<span data-ttu-id="a13f6-127">適切な認証を確保するには、追加の作業が必要です。</span><span class="sxs-lookup"><span data-stu-id="a13f6-127">Ensuring proper authentication requires some extra work though.</span></span> <span data-ttu-id="a13f6-128">実際に必要なことは、ユースケースによって異なります。このセクションの残りの部分では、必要な手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-128">What exactly you need to do depends on your use case, and the rest of this section is about figuring out the necessary steps.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="a13f6-129">この記事では、一般的なガイダンスのみを提供します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-129">This article can only provide general guidance.</span></span> <span data-ttu-id="a13f6-130">わからない場合は、セキュリティの専門家に相談して、ユースケースに固有のガイダンスを提供することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a13f6-130">If you feel unsure, consider consulting a security expert that can give you guidance specific to your use case.</span></span>

<span data-ttu-id="a13f6-131">まず、ネットワーク接続を記述するときに、 _クライアント_ と _サーバー_ という用語が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-131">First some terminology: when describing network connections, the terms _client_ and _server_ will be used.</span></span> <span data-ttu-id="a13f6-132">サーバーは既知のエンドポイントアドレスで着信接続をリッスンする側であり、クライアントはサーバーのエンドポイントに接続しています。</span><span class="sxs-lookup"><span data-stu-id="a13f6-132">The server is the side listening for incoming connections on a known endpoint address, and the client is the one connecting to the server's endpoint.</span></span>

>[!NOTE]
> <span data-ttu-id="a13f6-133">クライアントロールとサーバーロールは、アプリがプレーヤーとして動作しているか、リモートとして動作しているかに関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="a13f6-133">The client and and server roles are not tied to whether an app is acting as a player or as a remote.</span></span> <span data-ttu-id="a13f6-134">サンプルにはサーバーロールのプレーヤーが用意されていますが、ユースケースに適していれば、ロールを逆にするのは簡単です。</span><span class="sxs-lookup"><span data-stu-id="a13f6-134">While the samples have the player in the server role, it's easy to reverse the roles if it better fits your use case.</span></span>

### <a name="planning-the-server-to-client-authentication"></a><span data-ttu-id="a13f6-135">サーバー対クライアント認証の計画</span><span class="sxs-lookup"><span data-stu-id="a13f6-135">Planning the server-to-client authentication</span></span>

<span data-ttu-id="a13f6-136">サーバーは、デジタル証明書を使用して、クライアントに対して id を証明します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-136">The server uses digital certificates to prove its identity to the client.</span></span> <span data-ttu-id="a13f6-137">クライアントは、接続ハンドシェイクフェーズ中にサーバーの証明書を検証します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-137">The client validates the server's certificate during the connection handshake phase.</span></span> <span data-ttu-id="a13f6-138">クライアントがサーバーを信頼していない場合は、この時点で接続を終了します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-138">If the client doesn't trust the server, it will end the connection at this point.</span></span>

<span data-ttu-id="a13f6-139">クライアントがサーバー証明書を検証する方法と、使用できるサーバー証明書の種類は、ユースケースによって異なります。</span><span class="sxs-lookup"><span data-stu-id="a13f6-139">How the client validates the server certificate, and what kinds of server certificates can be used, depends on your use case.</span></span>

<span data-ttu-id="a13f6-140">**ユースケース 1:** サーバーのホスト名が固定されていないか、サーバーがホスト名でアドレス指定されていません。</span><span class="sxs-lookup"><span data-stu-id="a13f6-140">**Use case 1:** The server hostname isn't fixed, or the server isn't addressed by host name at all.</span></span>

<span data-ttu-id="a13f6-141">このユースケースでは、サーバーのホスト名に対して証明書を発行することは実用的ではありません (または可能です)。</span><span class="sxs-lookup"><span data-stu-id="a13f6-141">In this use case, it isn't practical (or even possible) to issue a certificate for the server's host name.</span></span> <span data-ttu-id="a13f6-142">ここでは、代わりに証明書の拇印を検証することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a13f6-142">The recommendation here is to validate the certificate's thumbprint instead.</span></span> <span data-ttu-id="a13f6-143">人間の指紋と同様に、拇印は証明書を一意に識別します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-143">Like a human fingerprint, the thumbprint uniquely identifies a certificate.</span></span>

<span data-ttu-id="a13f6-144">拇印は、帯域外でクライアントに対して通信することが重要です。</span><span class="sxs-lookup"><span data-stu-id="a13f6-144">It's important to communicate the thumbprint to the client out-of-band.</span></span> <span data-ttu-id="a13f6-145">つまり、リモート処理に使用されているのと同じネットワーク接続を経由して送信することはできません。</span><span class="sxs-lookup"><span data-stu-id="a13f6-145">That means, you can't send it over the same network connection that's used for remoting.</span></span> <span data-ttu-id="a13f6-146">代わりに、クライアントの構成に手動で入力することも、クライアントが QR コードをスキャンするようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-146">Instead, you could manually enter it into the client's configuration, or to have the client scan a QR code.</span></span>

<span data-ttu-id="a13f6-147">**ユースケース 2:** サーバーには、安定したホスト名を使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-147">**Use case 2:** The server can be reached over a stable host name.</span></span>

<span data-ttu-id="a13f6-148">このユースケースでは、サーバーに特定のホスト名があり、この名前が変更される可能性はありません。</span><span class="sxs-lookup"><span data-stu-id="a13f6-148">In this use case, the server has a specific host name, and you know this name isn't likely to change.</span></span> <span data-ttu-id="a13f6-149">その後、サーバーのホスト名に対して発行された証明書を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-149">You can then use a certificate issued to the server's host name.</span></span> <span data-ttu-id="a13f6-150">信頼は、ホスト名と証明書の信頼チェーンに基づいて確立されます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-150">Trust will be established based on the host name and the certificate's chain of trust.</span></span>

<span data-ttu-id="a13f6-151">このオプションを選択した場合、クライアントはサーバーのホスト名とルート証明書を事前に把握している必要があります。</span><span class="sxs-lookup"><span data-stu-id="a13f6-151">If you choose this option, the client needs to know the server's host name and the root certificate in advance.</span></span>

### <a name="planning-the-client-to-server-authentication"></a><span data-ttu-id="a13f6-152">クライアントとサーバー間の認証の計画</span><span class="sxs-lookup"><span data-stu-id="a13f6-152">Planning the client-to-server authentication</span></span>

<span data-ttu-id="a13f6-153">クライアントは、自由形式トークンを使用してサーバーに対して認証を行います。</span><span class="sxs-lookup"><span data-stu-id="a13f6-153">Clients authenticate against the server using a free-form token.</span></span> <span data-ttu-id="a13f6-154">このトークンに含まれる内容は、ユースケースによって異なります。</span><span class="sxs-lookup"><span data-stu-id="a13f6-154">What this token should contain will again depend on your use case:</span></span>

<span data-ttu-id="a13f6-155">**ユースケース 1:** クライアントアプリの id のみを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a13f6-155">**Use case 1:** You only need to verify the client app's identity.</span></span>

<span data-ttu-id="a13f6-156">このユースケースでは、共有シークレットで十分です。</span><span class="sxs-lookup"><span data-stu-id="a13f6-156">In this use case, a shared secret can be sufficient.</span></span> <span data-ttu-id="a13f6-157">このシークレットは、推測できないほど複雑である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a13f6-157">This secret must be complex enough that it can't be guessed.</span></span>

<span data-ttu-id="a13f6-158">適切な共有シークレットはランダムな GUID であり、サーバーとクライアントの両方の構成で手動で入力されます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-158">A good shared secret is a random GUID, which is manually entered in both the server's and client's configuration.</span></span> <span data-ttu-id="a13f6-159">たとえば、PowerShell でコマンドを使用して作成でき `New-Guid` ます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-159">To create one you can, for example, use the `New-Guid` command in PowerShell.</span></span>

<span data-ttu-id="a13f6-160">この共有シークレットが安全でないチャネルを介して伝達されることはないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="a13f6-160">Make sure this shared secret is never communicated over insecure channels.</span></span> <span data-ttu-id="a13f6-161">リモート処理ライブラリにより、共有シークレットは常に暗号化され、信頼されたピアにのみ送信されます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-161">The remoting library ensures that the shared secret is always sent encrypted, and only to trusted peers.</span></span>

<span data-ttu-id="a13f6-162">**ユースケース 2:** また、クライアントアプリのユーザーの id を確認する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="a13f6-162">**Use case 2:** You also need to verify the identity of the client app's user.</span></span>

<span data-ttu-id="a13f6-163">共有シークレットは、このユースケースに対応するのに十分ではありません。</span><span class="sxs-lookup"><span data-stu-id="a13f6-163">A shared secret won't be enough to cover this use case.</span></span> <span data-ttu-id="a13f6-164">代わりに、id プロバイダーによって作成されたトークンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-164">Instead, you can use tokens created by an identity provider.</span></span> <span data-ttu-id="a13f6-165">Id プロバイダーを使用する認証ワークフローは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a13f6-165">An authentication workflow using an identity provider would look like this:</span></span>

* <span data-ttu-id="a13f6-166">クライアントは id プロバイダーに対して承認を行い、トークンを要求します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-166">The client authorizes against the identity provider and requests a token</span></span>
* <span data-ttu-id="a13f6-167">Id プロバイダーは、トークンを生成し、それをクライアントに送信します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-167">The identity provider generates a token and sends it to the client</span></span>
* <span data-ttu-id="a13f6-168">クライアントは、Holographic Remoting を使用してこのトークンをサーバーに送信します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-168">The client sends this token to the server through Holographic Remoting</span></span>
* <span data-ttu-id="a13f6-169">サーバーは、クライアントのトークンを id プロバイダーに対して検証します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-169">The server validates the client's token against the identity provider</span></span>

<span data-ttu-id="a13f6-170">Id プロバイダーの1つの例として、 [Microsoft id プラットフォーム](https://docs.microsoft.com/azure/active-directory/develop/)があります。</span><span class="sxs-lookup"><span data-stu-id="a13f6-170">One example of an identity provider is the [Microsoft identity platform](https://docs.microsoft.com/azure/active-directory/develop/).</span></span>

<span data-ttu-id="a13f6-171">前のユースケースと同様に、これらのトークンが安全でないチャネル経由で送信されないようにするか、または公開するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="a13f6-171">Like in the previous use case, make sure these tokens aren't sent through insecure channels or otherwise exposed.</span></span>

## <a name="implementing-holographic-remoting-security"></a><span data-ttu-id="a13f6-172">Holographic リモート処理セキュリティの実装</span><span class="sxs-lookup"><span data-stu-id="a13f6-172">Implementing holographic remoting security</span></span>

<span data-ttu-id="a13f6-173">接続のセキュリティを有効にする場合は、カスタムのリモートアプリとプレーヤーアプリを実装する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a13f6-173">Remember that you need to implement custom remote and player apps if you want to enable connection security.</span></span> <span data-ttu-id="a13f6-174">提供されているサンプルは、独自のアプリの開始点として使用できます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-174">You can use the provided samples as starting points for your own apps.</span></span>

<span data-ttu-id="a13f6-175">セキュリティを有効にするには、ではなくを呼び出し、 `ListenSecure()` `Listen()` `ConnectSecure()` `Connect()` リモート処理接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-175">To enable security, call `ListenSecure()` instead of `Listen()`, and `ConnectSecure()` instead of `Connect()` to establish the remoting connection.</span></span>

<span data-ttu-id="a13f6-176">これらの呼び出しでは、セキュリティ関連の情報を提供および検証するために、特定のインターフェイスの実装を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a13f6-176">These calls require you to provide implementations of certain interfaces for providing and validating security-related information:</span></span>

* <span data-ttu-id="a13f6-177">サーバーは、証明書プロバイダーと認証検証ツールを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a13f6-177">The server needs to implement a certificate provider and an authentication validator</span></span>
* <span data-ttu-id="a13f6-178">クライアントは、認証プロバイダーと証明書検証を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a13f6-178">The client needs to implement an authentication provider and a certificate validator.</span></span>

<span data-ttu-id="a13f6-179">すべてのインターフェイスには、アクションを実行するための関数があります。これは、コールバックオブジェクトをパラメーターとして受け取ります。</span><span class="sxs-lookup"><span data-stu-id="a13f6-179">All interfaces have a function requesting you to take action, which receives a callback object as parameter.</span></span> <span data-ttu-id="a13f6-180">このオブジェクトを使用すると、要求の非同期処理を簡単に実装できます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-180">Using this object, you can easily implement asynchronous handling of the request.</span></span> <span data-ttu-id="a13f6-181">このオブジェクトへの参照を保持し、非同期アクションが完了したときに completion 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-181">Keep a reference to this object, and call the completion function when the asynchronous action is complete.</span></span> <span data-ttu-id="a13f6-182">完了関数は、任意のスレッドから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-182">The completion function may be called from any thread.</span></span>

>[!TIP]
><span data-ttu-id="a13f6-183">WinRT インターフェイスの実装は、C++/winrtを使用して簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-183">Implementing WinRT interfaces can easily be done using C++/WinRT.</span></span> <span data-ttu-id="a13f6-184">この詳細については、「 [C++/WinRT での api の作成」を](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) 参照してください。</span><span class="sxs-lookup"><span data-stu-id="a13f6-184">The [Author APIs with C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) chapter describes this in detail.</span></span>

>[!IMPORTANT]
><span data-ttu-id="a13f6-185">`build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl`NuGet パッケージ内には、セキュリティで保護された接続に関連する API の詳細なドキュメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a13f6-185">The `build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl` inside the NuGet package contains detailed documentation for the API related to secure connections.</span></span>

### <a name="implementing-a-certificate-provider"></a><span data-ttu-id="a13f6-186">証明書プロバイダーの実装</span><span class="sxs-lookup"><span data-stu-id="a13f6-186">Implementing a certificate provider</span></span>

<span data-ttu-id="a13f6-187">証明書プロバイダーは、使用する証明書をサーバーアプリケーションに提供します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-187">Certificate providers supply the server application with the certificate to use.</span></span> <span data-ttu-id="a13f6-188">実装は、次の2つの部分で構成されます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-188">The implementation consists of two parts:</span></span>

1) <span data-ttu-id="a13f6-189">インターフェイスを実装する証明書オブジェクト `ICertificate` 。</span><span class="sxs-lookup"><span data-stu-id="a13f6-189">A certificate object, which implements the `ICertificate` interface:</span></span>

    * <span data-ttu-id="a13f6-190">`GetCertificatePfx()` は、証明書ストアのバイナリコンテンツを返す必要があり `PKCS#12` ます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-190">`GetCertificatePfx()` should return the binary contents of a `PKCS#12` certificate store.</span></span> <span data-ttu-id="a13f6-191">ファイルには `.pfx` データが含まれている `PKCS#12` ため、ここで直接その内容を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-191">A `.pfx` file contains `PKCS#12` data, so its contents can be used directly here.</span></span>
    * <span data-ttu-id="a13f6-192">`GetSubjectName()` 使用する証明書を識別するフレンドリ名を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a13f6-192">`GetSubjectName()` should return the friendly name that identifies the certificate to use.</span></span> <span data-ttu-id="a13f6-193">証明書にフレンドリ名が割り当てられていない場合、この関数は証明書のサブジェクト名を返します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-193">If no friendly name is assigned to the certificate, this function should return the certificate's subject name.</span></span>
    * <span data-ttu-id="a13f6-194">`GetPfxPassword()` は、証明書ストアを開くために必要なパスワードを返す必要があります (パスワードが不要な場合は、空の文字列が返されます)。</span><span class="sxs-lookup"><span data-stu-id="a13f6-194">`GetPfxPassword()` should return the password required to open the certificate store (or an empty string if no password is required).</span></span>

2) <span data-ttu-id="a13f6-195">インターフェイスを実装する証明書プロバイダー `ICertificateProvider` :</span><span class="sxs-lookup"><span data-stu-id="a13f6-195">A certificate provider implementing the `ICertificateProvider` interface:</span></span>
    * <span data-ttu-id="a13f6-196">`GetCertificate()` は、 `CertificateReceived()` コールバックオブジェクトに対してを呼び出すことによって、証明書オブジェクトを構築し、それを返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a13f6-196">`GetCertificate()` should construct a certificate object and return it by calling `CertificateReceived()` on the callback object.</span></span>

### <a name="implementing-an-authentication-validator"></a><span data-ttu-id="a13f6-197">認証検証コントロールの実装</span><span class="sxs-lookup"><span data-stu-id="a13f6-197">Implementing an authentication validator</span></span>

<span data-ttu-id="a13f6-198">認証バリデーターは、クライアントから送信された認証トークンを受信し、検証結果を返します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-198">Authentication validators receive the authentication token sent by the client, and answer back with the validation result.</span></span>

<span data-ttu-id="a13f6-199">次のようにインターフェイスを実装し `IAuthenticationReceiver` ます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-199">Implement the `IAuthenticationReceiver` interface as follows:</span></span>

* <span data-ttu-id="a13f6-200">`GetRealm()` 認証領域の名前 (リモート処理接続のハンドシェイク中に使用される HTTP 領域) を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a13f6-200">`GetRealm()` should return the name of the authentication realm (an HTTP realm  used during the remoting connection handshake).</span></span>
* <span data-ttu-id="a13f6-201">`ValidateToken()` では、クライアント認証トークンを検証し、 `ValidationCompleted()` 検証結果を使用してコールバックオブジェクトでを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a13f6-201">`ValidateToken()` should validate the client authentication token and call `ValidationCompleted()` on the callback object with the validation result.</span></span>

### <a name="implementing-an-authentication-provider"></a><span data-ttu-id="a13f6-202">認証プロバイダーの実装</span><span class="sxs-lookup"><span data-stu-id="a13f6-202">Implementing an authentication provider</span></span>

<span data-ttu-id="a13f6-203">認証プロバイダーは、サーバーに送信される認証トークンを生成または取得します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-203">Authentication providers generate or retrieve the authentication token to be sent to the server.</span></span>

<span data-ttu-id="a13f6-204">次のようにインターフェイスを実装し `IAuthenticationProvider` ます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-204">Implement the `IAuthenticationProvider` interface as follows:</span></span>

* <span data-ttu-id="a13f6-205">`GetToken()` 送信する認証トークンを生成または取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a13f6-205">`GetToken()` should generate or retrieve the authentication token to be sent.</span></span> <span data-ttu-id="a13f6-206">トークンの準備ができたら、 `TokenReceived()` コールバックオブジェクトに対してメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-206">Once the token is ready, call the `TokenReceived()` method on the callback object.</span></span>

### <a name="implementing-a-certificate-validator"></a><span data-ttu-id="a13f6-207">証明書検証を実装する</span><span class="sxs-lookup"><span data-stu-id="a13f6-207">Implementing a certificate validator</span></span>

<span data-ttu-id="a13f6-208">証明書検証ツールは、サーバーによって送信された証明書チェーンを受け取り、サーバーを信頼できるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-208">Certificate validators receive the certificate chain sent by the server and determine whether the server can be trusted.</span></span>

<span data-ttu-id="a13f6-209">証明書を検証するには、基になるシステムの検証ロジックを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-209">To validate certificates, you can use the validation logic of the underlying system.</span></span> <span data-ttu-id="a13f6-210">このシステム検証では、独自の検証ロジックをサポートするか、完全に置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-210">This system validation can either support your own validation logic, or replace it altogether.</span></span> <span data-ttu-id="a13f6-211">セキュリティで保護された接続を要求するときに、独自の証明書検証ツールを渡さないと、システムの検証が自動的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-211">If you don't pass your own certificate validator when requesting a secure connection, system validation will be used automatically.</span></span>

<span data-ttu-id="a13f6-212">Windows では、システム検証によって次のことが確認されます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-212">On Windows, the system validation will check for:</span></span>

* <span data-ttu-id="a13f6-213">証明書チェーンの整合性: 証明書は、信頼されたルート証明書で終了する一貫性のあるチェーンを形成します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-213">Integrity of the certificate chain: the certificates form a consistent chain that ends at a trusted root certificate</span></span>
* <span data-ttu-id="a13f6-214">証明書の有効性: サーバーの証明書は有効期間内であり、サーバー認証の目的で発行されます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-214">Certificate validity: the server's certificate is within its validity timespan, and is issued for the purpose of server authentication</span></span>
* <span data-ttu-id="a13f6-215">失効: 証明書が失効していません</span><span class="sxs-lookup"><span data-stu-id="a13f6-215">Revocation: The certificate hasn't been revoked</span></span>
* <span data-ttu-id="a13f6-216">名前の一致: サーバーのホスト名が、証明書が発行されたホスト名のいずれかと一致します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-216">Name match: The host name of the server matches one of the host names the certificate was issued for</span></span>

<span data-ttu-id="a13f6-217">次のようにインターフェイスを実装し `ICertificateValidator` ます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-217">Implement the `ICertificateValidator` interface as follows:</span></span>

 * <span data-ttu-id="a13f6-218">`PerformSystemValidation()``true`前述のシステム検証を実行する必要がある場合は、を返します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-218">`PerformSystemValidation()` should return `true` if a system validation as described above should be performed.</span></span> <span data-ttu-id="a13f6-219">この場合、システム検証の結果は、入力としてメソッドに渡され `ValidateCertificate()` ます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-219">In this case, the system validation result is passed as an input to the `ValidateCertificate()` method.</span></span>
* <span data-ttu-id="a13f6-220">`ValidateCertificate()` は、証明書チェーンを検証した後、 `CertificateValidated()` 最後の検証結果を使用して渡されたコールバックでを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a13f6-220">`ValidateCertificate()` should validate the certificate chain and then call `CertificateValidated()` on the passed callback with the final validation result.</span></span> <span data-ttu-id="a13f6-221">このメソッドは、証明書チェーン、接続が確立されているサーバーの名前、および失効確認を強制する必要があるかどうかを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-221">This method accepts the certificate chain, the name of the server the connection is being established with, and whether a revocation check should be forced.</span></span> <span data-ttu-id="a13f6-222">証明書チェーンに複数の証明書が含まれている場合、1つ目はサブジェクト証明書です。</span><span class="sxs-lookup"><span data-stu-id="a13f6-222">If the certificate chain contains multiple certificates, the first one is the subject certificate.</span></span>

>[!NOTE]
><span data-ttu-id="a13f6-223">ユースケースで異なる形式の検証が必要な場合は (上記の証明書のユースケース #1 を参照)、システムの検証を完全にバイパスします。</span><span class="sxs-lookup"><span data-stu-id="a13f6-223">If your use case requires a different form of validation (see certificate use case #1 above), bypass system validation entirely.</span></span> <span data-ttu-id="a13f6-224">代わりに、DER でエンコードされた x.509 証明書を処理できる任意の API またはライブラリを使用して、証明書チェーンをデコードし、ユースケースに必要なチェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-224">Instead, use any API or library that can handle DER-encoded X.509 certificates to decode the certificate chain and perform the checks needed for your use case.</span></span>

## <a name="secure-connection-using-the-openxr-api"></a><span data-ttu-id="a13f6-225">OpenXR API を使用して接続をセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="a13f6-225">Secure connection using the OpenXR API</span></span>

<span data-ttu-id="a13f6-226">[OPENXR api](../native/openxr.md)を使用する場合、セキュリティで保護された接続に関連するすべての api は OpenXR 拡張機能の一部として利用でき `XR_MSFT_holographic_remoting` ます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-226">When using the the [OpenXR API](../native/openxr.md) all secure connection related API is available as part of the `XR_MSFT_holographic_remoting` OpenXR extension.</span></span>

>[!IMPORTANT]
><span data-ttu-id="a13f6-227">Holographic Remoting OpenXR extension API の詳細については、 [Holographic リモート処理のサンプル github リポジトリ](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)に記載されている[仕様](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="a13f6-227">To learn about the Holographic Remoting OpenXR extension API, check out the [specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) which can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="a13f6-228">OpenXR 拡張機能を使用したセキュリティで保護された接続の主な要素 `XR_MSFT_holographic_remoting` は、次のコールバックです。</span><span class="sxs-lookup"><span data-stu-id="a13f6-228">The key elements for secure connection using the `XR_MSFT_holographic_remoting` OpenXR extension are the following callbacks.</span></span>
- <span data-ttu-id="a13f6-229">`xrRemotingRequestAuthenticationTokenCallbackMSFT`は、送信される認証トークンを生成または取得します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-229">`xrRemotingRequestAuthenticationTokenCallbackMSFT`, generates or retrieves the authentication token to be sent.</span></span>
- <span data-ttu-id="a13f6-230">`xrRemotingValidateServerCertificateCallbackMSFT`は、証明書チェーンを検証します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-230">`xrRemotingValidateServerCertificateCallbackMSFT`, validates the certificate chain.</span></span>
- <span data-ttu-id="a13f6-231">`xrRemotingValidateAuthenticationTokenCallbackMSFT`は、クライアント認証トークンを検証します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-231">`xrRemotingValidateAuthenticationTokenCallbackMSFT`, validates the client authentication token.</span></span>
- <span data-ttu-id="a13f6-232">`xrRemotingRequestServerCertificateCallbackMSFT`では、使用する証明書をサーバーアプリケーションに提供します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-232">`xrRemotingRequestServerCertificateCallbackMSFT`, supply the server application with the certificate to use.</span></span>

<span data-ttu-id="a13f6-233">これらのコールバックは、およびを使用してリモート処理 OpenXR ランタイムに提供でき `xrRemotingSetSecureConnectionClientCallbacksMSFT` `xrRemotingSetSecureConnectionServerCallbacksMSFT` ます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-233">These callbacks can be provided to the remoting OpenXR runtime via `xrRemotingSetSecureConnectionClientCallbacksMSFT` and `xrRemotingSetSecureConnectionServerCallbacksMSFT`.</span></span> <span data-ttu-id="a13f6-234">`XrRemotingConnectInfoMSFT` `XrRemotingListenInfoMSFT` また、またはを使用しているかどうかに応じて、構造体または構造体の secureconnection パラメーターを使用してセキュリティで保護された接続を有効にする必要があり `xrRemotingConnectMSFT` `xrRemotingListenMSFT` ます。</span><span class="sxs-lookup"><span data-stu-id="a13f6-234">Additionally, the secure connection needs to be enabled via the secureConnection parameter on the `XrRemotingConnectInfoMSFT` structure or the `XrRemotingListenInfoMSFT` structure depending on whether you are using `xrRemotingConnectMSFT` or `xrRemotingListenMSFT`.</span></span>

<span data-ttu-id="a13f6-235">この API は、「 [holographic remoting security の実装](#implementing-holographic-remoting-security) 」で説明されている IDL ベースの api によく似ていますが、インターフェイスを実装するのではなく、コールバックの実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="a13f6-235">This API is quite similar to the IDL based API described in [Implementing holographic remoting security](#implementing-holographic-remoting-security) but instead of implementing interfaces your are supposed to provide callback implementations.</span></span> <span data-ttu-id="a13f6-236">詳細な例については、OpenXR サンプルアプリの一部として、 [Holographic リモート処理サンプル github リポジトリ](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a13f6-236">You can find an detailed example as part of the OpenXR sample app found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

## <a name="see-also"></a><span data-ttu-id="a13f6-237">参照</span><span class="sxs-lookup"><span data-stu-id="a13f6-237">See Also</span></span>
* [<span data-ttu-id="a13f6-238">Windows Mixed Realiy Api を使用した Holographic リモート処理リモートアプリの作成</span><span class="sxs-lookup"><span data-stu-id="a13f6-238">Writing a Holographic Remoting remote app using Windows Mixed Realiy APIs</span></span>](holographic-remoting-create-remote-wmr.md)
* [<span data-ttu-id="a13f6-239">OpenXR Api を使用した Holographic リモート処理リモートアプリの作成</span><span class="sxs-lookup"><span data-stu-id="a13f6-239">Writing a Holographic Remoting remote app using OpenXR APIs</span></span>](holographic-remoting-create-remote-openxr.md)
* [<span data-ttu-id="a13f6-240">カスタム Holographic リモート処理プレーヤーアプリの作成</span><span class="sxs-lookup"><span data-stu-id="a13f6-240">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="a13f6-241">Holographic リモート処理のトラブルシューティングと制限事項</span><span class="sxs-lookup"><span data-stu-id="a13f6-241">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="a13f6-242">Holographic Remoting ソフトウェア ライセンス条項</span><span class="sxs-lookup"><span data-stu-id="a13f6-242">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="a13f6-243">Microsoft プライバシーに関する声明</span><span class="sxs-lookup"><span data-stu-id="a13f6-243">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
