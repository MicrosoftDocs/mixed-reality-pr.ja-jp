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
# <a name="enabling-connection-security-for-holographic-remoting"></a>Holographic リモート処理の接続セキュリティを有効にする

>[!IMPORTANT]
>このガイダンスは、HoloLens 2 の Holographic リモート処理に固有のものです。

このページでは、Holographic リモート処理のネットワークセキュリティの概要について説明します。 次の情報が見つかります。

* Holographic リモート処理のコンテキストでのセキュリティと必要な理由
* さまざまなユースケースに基づく推奨メジャー
* Holographic リモート処理ソリューションへのセキュリティの実装

## <a name="overview"></a>概要

Holographic リモート処理では、ネットワーク経由で情報を交換します。 セキュリティ対策が実施されていない場合、同じネットワーク上の敵対者は、通信またはアクセスの機密情報の整合性を損なう可能性があります。

Windows ストアのサンプルアプリと Holographic リモート処理プレーヤーには、セキュリティが無効になっています。 そうすることで、サンプルがわかりやすくなります。 また、開発をより迅速に開始するのにも役立ちます。

ただし、フィールドテストまたは実稼働環境での使用については、Holographic リモート処理ソリューションでセキュリティを有効にすることを強くお勧めします。

Holographic リモート処理のセキュリティは、ユースケースに対して正しく設定されると、次の保証を提供します。

* **信頼性:** プレーヤーとリモートの両方のアプリが、相手側として要求されていることを確認できます。
* **機密性:** サードパーティが、windows media player とリモートアプリの間で交換される情報を読み取ることはできません。
* **整合性:** プレーヤーとリモートは、通信に対する転送中の変更を検出できます。

>[!IMPORTANT]
>セキュリティ機能を使用できるようにするには、 [Windows Mixed Reality](holographic-remoting-create-remote-wmr.md) api または[OpenXR](holographic-remoting-create-remote-openxr.md) api を使用して、[カスタムプレーヤー](holographic-remoting-create-player.md)とカスタムリモートアプリの両方を実装する必要があります。

>[!NOTE]
> [2.4.0](holographic-remoting-version-history.md#v2.4.0)以降のバージョンでは、 [OpenXR API](../native/openxr.md)を使用したリモートアプリを作成できます。 OpenXR 環境でセキュリティで保護された接続を確立する方法の概要については、 [以下](#secure-connection-using-the-openxr-api)を参照してください。

## <a name="planning-the-security-implementation"></a>セキュリティ実装の計画

Holographic リモート処理でセキュリティを有効にすると、ネットワーク経由で交換されるすべてのデータについて、暗号化および整合性チェックが自動的に有効になります。

適切な認証を確保するには、追加の作業が必要です。 実際に必要なことは、ユースケースによって異なります。このセクションの残りの部分では、必要な手順を説明します。

>[!IMPORTANT]
> この記事では、一般的なガイダンスのみを提供します。 わからない場合は、セキュリティの専門家に相談して、ユースケースに固有のガイダンスを提供することを検討してください。

まず、ネットワーク接続を記述するときに、 _クライアント_ と _サーバー_ という用語が使用されます。 サーバーは既知のエンドポイントアドレスで着信接続をリッスンする側であり、クライアントはサーバーのエンドポイントに接続しています。

>[!NOTE]
> クライアントロールとサーバーロールは、アプリがプレーヤーとして動作しているか、リモートとして動作しているかに関連付けられていません。 サンプルにはサーバーロールのプレーヤーが用意されていますが、ユースケースに適していれば、ロールを逆にするのは簡単です。

### <a name="planning-the-server-to-client-authentication"></a>サーバー対クライアント認証の計画

サーバーは、デジタル証明書を使用して、クライアントに対して id を証明します。 クライアントは、接続ハンドシェイクフェーズ中にサーバーの証明書を検証します。 クライアントがサーバーを信頼していない場合は、この時点で接続を終了します。

クライアントがサーバー証明書を検証する方法と、使用できるサーバー証明書の種類は、ユースケースによって異なります。

**ユースケース 1:** サーバーのホスト名が固定されていないか、サーバーがホスト名でアドレス指定されていません。

このユースケースでは、サーバーのホスト名に対して証明書を発行することは実用的ではありません (または可能です)。 ここでは、代わりに証明書の拇印を検証することをお勧めします。 人間の指紋と同様に、拇印は証明書を一意に識別します。

拇印は、帯域外でクライアントに対して通信することが重要です。 つまり、リモート処理に使用されているのと同じネットワーク接続を経由して送信することはできません。 代わりに、クライアントの構成に手動で入力することも、クライアントが QR コードをスキャンするようにすることもできます。

**ユースケース 2:** サーバーには、安定したホスト名を使用してアクセスできます。

このユースケースでは、サーバーに特定のホスト名があり、この名前が変更される可能性はありません。 その後、サーバーのホスト名に対して発行された証明書を使用できます。 信頼は、ホスト名と証明書の信頼チェーンに基づいて確立されます。

このオプションを選択した場合、クライアントはサーバーのホスト名とルート証明書を事前に把握している必要があります。

### <a name="planning-the-client-to-server-authentication"></a>クライアントとサーバー間の認証の計画

クライアントは、自由形式トークンを使用してサーバーに対して認証を行います。 このトークンに含まれる内容は、ユースケースによって異なります。

**ユースケース 1:** クライアントアプリの id のみを確認する必要があります。

このユースケースでは、共有シークレットで十分です。 このシークレットは、推測できないほど複雑である必要があります。

適切な共有シークレットはランダムな GUID であり、サーバーとクライアントの両方の構成で手動で入力されます。 たとえば、PowerShell でコマンドを使用して作成でき `New-Guid` ます。

この共有シークレットが安全でないチャネルを介して伝達されることはないようにしてください。 リモート処理ライブラリにより、共有シークレットは常に暗号化され、信頼されたピアにのみ送信されます。

**ユースケース 2:** また、クライアントアプリのユーザーの id を確認する必要もあります。

共有シークレットは、このユースケースに対応するのに十分ではありません。 代わりに、id プロバイダーによって作成されたトークンを使用できます。 Id プロバイダーを使用する認証ワークフローは次のようになります。

* クライアントは id プロバイダーに対して承認を行い、トークンを要求します。
* Id プロバイダーは、トークンを生成し、それをクライアントに送信します。
* クライアントは、Holographic Remoting を使用してこのトークンをサーバーに送信します。
* サーバーは、クライアントのトークンを id プロバイダーに対して検証します。

Id プロバイダーの1つの例として、 [Microsoft id プラットフォーム](https://docs.microsoft.com/azure/active-directory/develop/)があります。

前のユースケースと同様に、これらのトークンが安全でないチャネル経由で送信されないようにするか、または公開するようにしてください。

## <a name="implementing-holographic-remoting-security"></a>Holographic リモート処理セキュリティの実装

接続のセキュリティを有効にする場合は、カスタムのリモートアプリとプレーヤーアプリを実装する必要があることに注意してください。 提供されているサンプルは、独自のアプリの開始点として使用できます。

セキュリティを有効にするには、ではなくを呼び出し、 `ListenSecure()` `Listen()` `ConnectSecure()` `Connect()` リモート処理接続を確立します。

これらの呼び出しでは、セキュリティ関連の情報を提供および検証するために、特定のインターフェイスの実装を提供する必要があります。

* サーバーは、証明書プロバイダーと認証検証ツールを実装する必要があります。
* クライアントは、認証プロバイダーと証明書検証を実装する必要があります。

すべてのインターフェイスには、アクションを実行するための関数があります。これは、コールバックオブジェクトをパラメーターとして受け取ります。 このオブジェクトを使用すると、要求の非同期処理を簡単に実装できます。 このオブジェクトへの参照を保持し、非同期アクションが完了したときに completion 関数を呼び出します。 完了関数は、任意のスレッドから呼び出すことができます。

>[!TIP]
>WinRT インターフェイスの実装は、C++/winrtを使用して簡単に行うことができます。 この詳細については、「 [C++/WinRT での api の作成」を](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) 参照してください。

>[!IMPORTANT]
>`build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl`NuGet パッケージ内には、セキュリティで保護された接続に関連する API の詳細なドキュメントが含まれています。

### <a name="implementing-a-certificate-provider"></a>証明書プロバイダーの実装

証明書プロバイダーは、使用する証明書をサーバーアプリケーションに提供します。 実装は、次の2つの部分で構成されます。

1) インターフェイスを実装する証明書オブジェクト `ICertificate` 。

    * `GetCertificatePfx()` は、証明書ストアのバイナリコンテンツを返す必要があり `PKCS#12` ます。 ファイルには `.pfx` データが含まれている `PKCS#12` ため、ここで直接その内容を使用することができます。
    * `GetSubjectName()` 使用する証明書を識別するフレンドリ名を返す必要があります。 証明書にフレンドリ名が割り当てられていない場合、この関数は証明書のサブジェクト名を返します。
    * `GetPfxPassword()` は、証明書ストアを開くために必要なパスワードを返す必要があります (パスワードが不要な場合は、空の文字列が返されます)。

2) インターフェイスを実装する証明書プロバイダー `ICertificateProvider` :
    * `GetCertificate()` は、 `CertificateReceived()` コールバックオブジェクトに対してを呼び出すことによって、証明書オブジェクトを構築し、それを返す必要があります。

### <a name="implementing-an-authentication-validator"></a>認証検証コントロールの実装

認証バリデーターは、クライアントから送信された認証トークンを受信し、検証結果を返します。

次のようにインターフェイスを実装し `IAuthenticationReceiver` ます。

* `GetRealm()` 認証領域の名前 (リモート処理接続のハンドシェイク中に使用される HTTP 領域) を返す必要があります。
* `ValidateToken()` では、クライアント認証トークンを検証し、 `ValidationCompleted()` 検証結果を使用してコールバックオブジェクトでを呼び出す必要があります。

### <a name="implementing-an-authentication-provider"></a>認証プロバイダーの実装

認証プロバイダーは、サーバーに送信される認証トークンを生成または取得します。

次のようにインターフェイスを実装し `IAuthenticationProvider` ます。

* `GetToken()` 送信する認証トークンを生成または取得する必要があります。 トークンの準備ができたら、 `TokenReceived()` コールバックオブジェクトに対してメソッドを呼び出します。

### <a name="implementing-a-certificate-validator"></a>証明書検証を実装する

証明書検証ツールは、サーバーによって送信された証明書チェーンを受け取り、サーバーを信頼できるかどうかを判断します。

証明書を検証するには、基になるシステムの検証ロジックを使用できます。 このシステム検証では、独自の検証ロジックをサポートするか、完全に置き換えることができます。 セキュリティで保護された接続を要求するときに、独自の証明書検証ツールを渡さないと、システムの検証が自動的に使用されます。

Windows では、システム検証によって次のことが確認されます。

* 証明書チェーンの整合性: 証明書は、信頼されたルート証明書で終了する一貫性のあるチェーンを形成します。
* 証明書の有効性: サーバーの証明書は有効期間内であり、サーバー認証の目的で発行されます。
* 失効: 証明書が失効していません
* 名前の一致: サーバーのホスト名が、証明書が発行されたホスト名のいずれかと一致します。

次のようにインターフェイスを実装し `ICertificateValidator` ます。

 * `PerformSystemValidation()``true`前述のシステム検証を実行する必要がある場合は、を返します。 この場合、システム検証の結果は、入力としてメソッドに渡され `ValidateCertificate()` ます。
* `ValidateCertificate()` は、証明書チェーンを検証した後、 `CertificateValidated()` 最後の検証結果を使用して渡されたコールバックでを呼び出す必要があります。 このメソッドは、証明書チェーン、接続が確立されているサーバーの名前、および失効確認を強制する必要があるかどうかを受け入れます。 証明書チェーンに複数の証明書が含まれている場合、1つ目はサブジェクト証明書です。

>[!NOTE]
>ユースケースで異なる形式の検証が必要な場合は (上記の証明書のユースケース #1 を参照)、システムの検証を完全にバイパスします。 代わりに、DER でエンコードされた x.509 証明書を処理できる任意の API またはライブラリを使用して、証明書チェーンをデコードし、ユースケースに必要なチェックを実行します。

## <a name="secure-connection-using-the-openxr-api"></a>OpenXR API を使用して接続をセキュリティで保護する

[OPENXR api](../native/openxr.md)を使用する場合、セキュリティで保護された接続に関連するすべての api は OpenXR 拡張機能の一部として利用でき `XR_MSFT_holographic_remoting` ます。

>[!IMPORTANT]
>Holographic Remoting OpenXR extension API の詳細については、 [Holographic リモート処理のサンプル github リポジトリ](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)に記載されている[仕様](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html)を確認してください。

OpenXR 拡張機能を使用したセキュリティで保護された接続の主な要素 `XR_MSFT_holographic_remoting` は、次のコールバックです。
- `xrRemotingRequestAuthenticationTokenCallbackMSFT`は、送信される認証トークンを生成または取得します。
- `xrRemotingValidateServerCertificateCallbackMSFT`は、証明書チェーンを検証します。
- `xrRemotingValidateAuthenticationTokenCallbackMSFT`は、クライアント認証トークンを検証します。
- `xrRemotingRequestServerCertificateCallbackMSFT`では、使用する証明書をサーバーアプリケーションに提供します。

これらのコールバックは、およびを使用してリモート処理 OpenXR ランタイムに提供でき `xrRemotingSetSecureConnectionClientCallbacksMSFT` `xrRemotingSetSecureConnectionServerCallbacksMSFT` ます。 `XrRemotingConnectInfoMSFT` `XrRemotingListenInfoMSFT` また、またはを使用しているかどうかに応じて、構造体または構造体の secureconnection パラメーターを使用してセキュリティで保護された接続を有効にする必要があり `xrRemotingConnectMSFT` `xrRemotingListenMSFT` ます。

この API は、「 [holographic remoting security の実装](#implementing-holographic-remoting-security) 」で説明されている IDL ベースの api によく似ていますが、インターフェイスを実装するのではなく、コールバックの実装を提供します。 詳細な例については、OpenXR サンプルアプリの一部として、 [Holographic リモート処理サンプル github リポジトリ](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)を参照してください。

## <a name="see-also"></a>参照
* [Windows Mixed Realiy Api を使用した Holographic リモート処理リモートアプリの作成](holographic-remoting-create-remote-wmr.md)
* [OpenXR Api を使用した Holographic リモート処理リモートアプリの作成](holographic-remoting-create-remote-openxr.md)
* [カスタム Holographic リモート処理プレーヤーアプリの作成](holographic-remoting-create-player.md)
* [Holographic リモート処理のトラブルシューティングと制限事項](holographic-remoting-troubleshooting.md)
* [Holographic Remoting ソフトウェア ライセンス条項](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)
