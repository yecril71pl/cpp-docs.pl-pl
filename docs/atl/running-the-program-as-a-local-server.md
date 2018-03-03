---
title: "Program działa jako serwer lokalny | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- debugging [ATL], running services as local server
- ATL services, running as local servers
ms.assetid: eb9701e6-e2a8-4666-897f-0c893aec8ac7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3e398bfed0174e4ec2a262ea03076ed17881f900
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="running-the-program-as-a-local-server"></a>Program działa jako serwer lokalny
Jeśli program działa jako usługa jest niewygodne, można tymczasowo zmienić rejestru, aby program jest uruchamiany jako normalne serwera lokalnego. Po prostu zmienić `LocalService` wartości w ramach identyfikator aplikacji, który `_LocalService` i upewnij się, `LocalServer32` klucza w Twojej CLSID została poprawnie ustawiona. (Należy pamiętać, że za pomocą DCOMCNFG, aby określić, że aplikacja powinien być wykonywany na innym komputerze zmienia nazwę Twojej `LocalServer32` klucza `_LocalServer32`.) Uruchomić program zgodnie z lokalnego serwera zajmuje kilka sekund podczas uruchamiania, ponieważ wywołanie **StartServiceCtrlDispatcher** w `CAtlServiceModuleT::Start` zajmuje kilka sekund przed jej nie powiedzie się.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki dotyczące debugowania](../atl/debugging-tips.md)

