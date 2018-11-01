---
title: Uruchamianie programu jako serwera lokalnego
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [ATL], running services as local server
- ATL services, running as local servers
ms.assetid: eb9701e6-e2a8-4666-897f-0c893aec8ac7
ms.openlocfilehash: 9a55dba861457eae888f519fb3bbd6c7a66e623c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610863"
---
# <a name="running-the-program-as-a-local-server"></a>Uruchamianie programu jako serwera lokalnego

Jeśli program działa jako usługa jest wygodne, można tymczasowo zmienić rejestru, więc, że program jest uruchamiany jako normalna serwera lokalnego. Po prostu Zmień nazwę `LocalService` wartości w obszarze identyfikator aplikacji, który `_LocalService` i upewnij się, `LocalServer32` klucza w ramach Twojego identyfikatora CLSID jest poprawnie ustawiony. (Należy pamiętać, że za pomocą DCOMCNFG, aby określić, że Twoja aplikacja powinna zostać uruchomiona na innym komputerze zmienia nazwę Twojego `LocalServer32` klucza `_LocalServer32`.) Uruchamianie programu jako serwera lokalnego zajmuje kilka sekund podczas uruchamiania, ponieważ wywołanie `StartServiceCtrlDispatcher` w `CAtlServiceModuleT::Start` zajmuje kilka sekund, zanim zakończy się niepowodzeniem.

## <a name="see-also"></a>Zobacz też

[Wskazówki dotyczące debugowania](../atl/debugging-tips.md)

