---
ms.openlocfilehash: 212aa75ae91a7beebbfa609af6cc47106ba34b55
ms.sourcegitcommit: 0509cf6c57067cffd75a0189106e3369e9ecc5c8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "96855885"
---
# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

| オプション | 説明 |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | 接続先の HoloLens 2 デバイスの IP アドレス (およびオプションのポート) を取得します。 ポートが指定されていない場合、既定値は 8265 です。 |
| `-RemotingBitrate=<bitrate>` | (省略可能) 既定値は 8000 です。 最大ネットワーク転送速度 (kb/秒)。 |
| `-HoloLensRemotingListen` | (省略可能) リッスン サーバーを起動します |
| `-HoloLensRemotingListenPort=<port>` | (省略可能) リッスンするポートを取得します。 HoloLens デバイスから PC または VM に接続するために使用されます。 |
| `-HoloLens1Remoting=<IP address>` | (4.26 では非推奨) 接続先の HoloLens 1 デバイスの IP アドレスを取得します |

# <a name="openxr"></a>[OpenXR](#tab/openxr)

| オプション | 説明 |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | 接続先の HoloLens 2 デバイスの IP アドレス (およびオプションのポート、既定値は 8265)、またはアプリから接続のためにリッスンするポートを取得します。 |
| `-EnableAudio` | (省略可能) リモート処理時に PC からのオーディオを使用します  |
| `-Listen` | (省略可能) リッスン サーバーを起動します |
| `-RemotingBitrate=<bitrate>` | (省略可能) 既定値は 8000 です。 最大ネットワーク転送速度 (kb/秒)。 |
| `-RemotingCodec=<codec>` | (省略可能) 接続コーデック  |