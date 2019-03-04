---
title: Uruchamianie programu jako serwera lokalnego
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [ATL], running services as local server
- ATL services, running as local servers
ms.assetid: eb9701e6-e2a8-4666-897f-0c893aec8ac7
ms.openlocfilehash: a412814fc5f3900a248f779501e2720b72287e57
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296829"
---
# <a name="running-the-program-as-a-local-server"></a>Uruchamianie programu jako serwera lokalnego

Jeśli program działa jako usługa jest wygodne, można tymczasowo zmienić rejestru, więc, że program jest uruchamiany jako normalna serwera lokalnego. Po prostu Zmień nazwę `LocalService` wartości w obszarze identyfikator aplikacji, który `_LocalService` i upewnij się, `LocalServer32` klucza w ramach Twojego identyfikatora CLSID jest poprawnie ustawiony. (Należy pamiętać, że za pomocą DCOMCNFG, aby określić, że Twoja aplikacja powinna zostać uruchomiona na innym komputerze zmienia nazwę Twojego `LocalServer32` klucza `_LocalServer32`.) Uruchamianie programu jako serwera lokalnego zajmuje kilka sekund podczas uruchamiania, ponieważ wywołanie `StartServiceCtrlDispatcher` w `CAtlServiceModuleT::Start` zajmuje kilka sekund, zanim zakończy się niepowodzeniem.

## <a name="see-also"></a>Zobacz także

[Wskazówki dotyczące debugowania](../atl/debugging-tips.md)
