---
title: Holographic Remoting を使用したセキュリティで保護された接続の確立
description: このページでは、Holographic リモート処理の使用時にセキュリティで保護された暗号化接続を確立する方法について説明します。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理
ms.openlocfilehash: 4006a317ed2ecfd7a1e67336a80a4e536d45e554
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683647"
---
# <a name="establishing-a-secure-connection-with-holographic-remoting"></a>Holographic Remoting を使用したセキュリティで保護された接続の確立

>[!IMPORTANT]
>このガイダンスは、HoloLens 2 の Holographic リモート処理に固有のものです。

このページでは、Holographic リモート処理の使用時にセキュリティで保護された暗号化接続を確立する方法について説明します。

オープン WiFi やインターネットなど、セキュリティで保護されていないネットワーク経由で HoloLens 2 にコンテンツをストリーミングする場合は、暗号化された接続を使用することを強くお勧めします。

>[!IMPORTANT]
>信頼されたローカル WiFi を使用している場合でも、暗号化された接続を使用することを検討してください。

暗号化された接続を使用できるようにするには、 [カスタムプレーヤー](holographic-remoting-create-player.md) と [カスタムリモートアプリ](holographic-remoting-create-host.md)の両方を実装する必要があります。

暗号化は、基になるプラットフォームの TLS 実装を使用して実現されます。

## <a name="basics-of-an-encrypted-connection"></a>暗号化された接続の基礎

証明書の交換を可能にするには、次のオブジェクトを実装する必要があります。

>[!TIP]
>WinRT インターフェイスの実装は、C++/winrtを使用して簡単に行うことができます。 この詳細については、「 [C++/WinRT での api の作成」を](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) 参照してください。

>[!IMPORTANT]
>```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```NuGet パッケージ内には、セキュリティで保護された接続に関連する API の詳細なドキュメントが含まれています。

1) インターフェイスを実装する必要がある証明書オブジェクト ```ICertificate``` 。

    * メソッドを使用して、pfx 証明書のバイナリコンテンツを返し ```GetCertificatePfx``` ます。 .Pfx ファイルのバイナリコンテンツと同じです。
    * 証明書のサブジェクト名をから返し ```GetSubjectName``` ます。
    * を介して pfx パスワードを返し ```GetPfxPassword``` ます。 保護されていない pfx の空の文字列を返します。

2) ```ICertificateProvider```メソッドで要求されたときに証明書を提供するインターフェイスを実装する証明書プロバイダー ```GetCertificate``` 。

3) インターフェイスを実装する証明書検証コントロール ```ICertificateValidator``` 。 このタスクでは、受信証明書を確認します。
    * この ```PerformSystemValidation``` メソッドは、 ```true``` 基になるプラットフォームが受信証明書チェーンを検証する必要がある場合にを返し ```false``` ます。それ以外の場合はを返します。
    * ```ValidateCertificate``` は、証明書の検証を要求するためにクライアントコンテキストによって呼び出されます。 このメソッドは、証明書チェーン (最初の証明書がサブジェクト証明書である)、接続が確立されているサーバーの名前、および失効確認を強制的に行うかどうかを指定します。 基になるシステムによる検証が要求された場合、システム検証の結果が提供されます。 ```CertificateValidated```適切な結果を使用して処理を続行する場合、または ```Cancel``` 渡されたに対して検証をキャンセルする必要がある場合は ```ICertificateValidationCallback``` 。

さらに、セキュリティで保護されたトークンを交換できるようにするには、次のオブジェクトを実装する必要があります。

1) インターフェイスを実装する認証プロバイダー ```IAuthenticationProvider``` 。 クライアントの ```GetToken``` 認証のためのトークンを要求するために、そのメソッドがクライアントコンテキストによって呼び出されます。 ```TokenReceived```認証トークンを提供して接続プロセスを続行するかキャンセルするには、 ```Cancel``` 渡されたに対してプロセスを呼び出す必要があり ```IAuthenticationProviderCallback``` ます。
2) インターフェイスを実装する認証受信者 ```IAuthenticationReceiver``` 。 このタスクでは、受信トークンを検証します。
    * メソッドは、 ```GetRealm``` 認証領域の名前を返します。
    * ```ValidateToken```メソッドは、クライアント認証トークンの検証を要求するために、サーバーネットワークコンテキストによって呼び出されます。 を呼び出し ```ValidationCompleted``` て検証の完了を通知するか ```Cancel``` 、クライアント接続を拒否するには、を呼び出します。 クライアント接続は、に渡された検証結果に基づいて、受け付けまたは拒否され ```ValidationCompleted``` ます。 

これらのオブジェクトを実装した後は、 ```ListenSecure``` ```Listen``` ```ConnectSecure``` ```Connect``` リモートコンテキストおよびプレーヤーコンテキストではなく、との代わりにを呼び出す必要があります。 ```ListenSecure``` では、追加の証明書プロバイダーと認証レシーバーが必要です ```Listen``` 。 ```ConnectSecure``` では、追加の認証プロバイダーと証明書検証を行う必要があり ```Connect``` ます。

## <a name="see-also"></a>関連項目
* [Holographic Remoting リモート アプリの作成](holographic-remoting-create-host.md)
* [カスタム Holographic リモート処理プレーヤーアプリの作成](holographic-remoting-create-player.md)
* [Holographic リモート処理のトラブルシューティングと制限事項](holographic-remoting-troubleshooting.md)
* [Holographic Remoting ソフトウェア ライセンス条項](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)
