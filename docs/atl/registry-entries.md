---
title: Wpisy rejestru (ATL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- registry, ATL services entries
- registry, application IDs
ms.assetid: 881989b7-61bb-459a-a13e-3bfcb33e184e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d74f458e28377dcc0bd7d6800cddc6e227c9f984
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751784"
---
# <a name="registry-entries"></a>Wpisy rejestru

DCOM wprowadzono pojęcie identyfikatorów aplikacji (identyfikatory AppID), które grupy opcji konfiguracji dla co najmniej jeden obiekt modelu DCOM w centralnej lokalizacji w rejestrze. Należy określić identyfikator AppID, wskazując jego wartości w AppID nazwanej wartości w obszarze CLSID obiektu.

Domyślnie usługi generowane ATL używa własny identyfikator CLSID jako identyfikatora GUID dla jego identyfikator aplikacji. W obszarze `HKEY_CLASSES_ROOT\AppID`, można określić wpisy dotyczące modelu DCOM. Początkowo istnieją dwa wpisy:

- `LocalService`, z wartością jest taka sama jak nazwa usługi. Jeśli ta wartość istnieje, jest ona używana zamiast `LocalServer32` klucza w obszarze identyfikator CLSID.

- `ServiceParameters`, o wartości równej `-Service`. Ta wartość określa parametry, które zostaną przekazane do usługi po jej ponownym uruchomieniu. Należy zauważyć, że te parametry są przekazywane do usługi `ServiceMain` funkcja nie `WinMain`.

Dowolną usługę DCOM również potrzebuje do utworzenia innego klucza w ramach `HKEY_CLASSES_ROOT\AppID`. Ten klucz jest taka sama jak nazwa pliku exe i działa jako odsyłaczy, ponieważ zawiera ona wartością AppID wskazuje wpisy Identyfikator aplikacji.

## <a name="see-also"></a>Zobacz też

[Usługi](../atl/atl-services.md)

