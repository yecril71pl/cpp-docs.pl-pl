---
title: Wpisy rejestru (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- registry, ATL services entries
- registry, application IDs
ms.assetid: 881989b7-61bb-459a-a13e-3bfcb33e184e
ms.openlocfilehash: 7a89bc5d510d493f557b7ea74b8eabe5dfd87ac1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196758"
---
# <a name="registry-entries"></a>Wpisy rejestru

DCOM wprowadzono pojęcie identyfikatorów aplikacji (identyfikatory AppID), które grupy opcji konfiguracji dla co najmniej jeden obiekt modelu DCOM w centralnej lokalizacji w rejestrze. Należy określić identyfikator AppID, wskazując jego wartości w AppID nazwanej wartości w obszarze CLSID obiektu.

Domyślnie usługi generowane ATL używa własny identyfikator CLSID jako identyfikatora GUID dla jego identyfikator aplikacji. W obszarze `HKEY_CLASSES_ROOT\AppID`, można określić wpisy dotyczące modelu DCOM. Początkowo istnieją dwa wpisy:

- `LocalService`, z wartością jest taka sama jak nazwa usługi. Jeśli ta wartość istnieje, jest ona używana zamiast `LocalServer32` klucza w obszarze identyfikator CLSID.

- `ServiceParameters`, o wartości równej `-Service`. Ta wartość określa parametry, które zostaną przekazane do usługi po jej ponownym uruchomieniu. Należy zauważyć, że te parametry są przekazywane do usługi `ServiceMain` funkcja nie `WinMain`.

Dowolną usługę DCOM również potrzebuje do utworzenia innego klucza w ramach `HKEY_CLASSES_ROOT\AppID`. Ten klucz jest taka sama jak nazwa pliku exe i działa jako odsyłaczy, ponieważ zawiera ona wartością AppID wskazuje wpisy Identyfikator aplikacji.

## <a name="see-also"></a>Zobacz także

[Usługi](../atl/atl-services.md)
