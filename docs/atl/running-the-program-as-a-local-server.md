---
title: Program działa jako serwer lokalny | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [ATL], running services as local server
- ATL services, running as local servers
ms.assetid: eb9701e6-e2a8-4666-897f-0c893aec8ac7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2b8a79978528493e02ac5a272dafe8da6fdc1d9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="running-the-program-as-a-local-server"></a>Program działa jako serwer lokalny
Jeśli program działa jako usługa jest niewygodne, można tymczasowo zmienić rejestru, aby program jest uruchamiany jako normalne serwera lokalnego. Po prostu zmienić `LocalService` wartości w ramach identyfikator aplikacji, który `_LocalService` i upewnij się, `LocalServer32` klucza w Twojej CLSID została poprawnie ustawiona. (Należy pamiętać, że za pomocą DCOMCNFG, aby określić, że aplikacja powinien być wykonywany na innym komputerze zmienia nazwę Twojej `LocalServer32` klucza `_LocalServer32`.) Uruchomić program zgodnie z lokalnego serwera zajmuje kilka sekund podczas uruchamiania, ponieważ wywołanie **StartServiceCtrlDispatcher** w `CAtlServiceModuleT::Start` zajmuje kilka sekund przed jej nie powiedzie się.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki dotyczące debugowania](../atl/debugging-tips.md)

