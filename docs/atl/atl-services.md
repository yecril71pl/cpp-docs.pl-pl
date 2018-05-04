---
title: Usługi ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CServiceModule
dev_langs:
- C++
helpviewer_keywords:
- CServiceModule class
- COM objects, ATL
- services, ATL
- ATL services
ms.assetid: 8c09d1a8-7548-4d2c-947c-9d795a81659b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db13b443e605168389f0a9bc767ba29a75d4234d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="atl-services"></a>Usługi ATL
Aby utworzyć obiekt ATL COM, dzięki czemu uruchamia się w usłudze, po prostu wybierz z listy opcji serwera w Kreatorze projektu ATL usługi (EXE). Kreator utworzy następnie klasę pochodzącą od `CAtlServiceModuleT` wdrażania usługi.  
  
 Po utworzeniu obiektu ATL COM jako usługa będzie można rejestrować tylko jako serwera lokalnego, a nie pojawi się na liście usługi w Panelu sterowania. Jest tak, ponieważ jest łatwiejsze do debugowania usługi, ponieważ serwer lokalny niż jako usługa. Aby zainstalować go jako usługa, uruchom następujące polecenie w wierszu polecenia:  
  
 `YourEXE``.exe /Service`  
  
 Aby go odinstalować, uruchom następujące polecenie:  
  
 `YourEXE``.exe /UnregServer`  
  
 Pierwsze cztery tematy w tej sekcji omówiono akcje, które zachodzą podczas wykonywania `CAtlServiceModuleT` funkcji elementów członkowskich. Te tematy są wyświetlane w takiej samej kolejności jak te funkcje są zwykle nazywane. Aby zwiększyć zrozumienie tych tematów, to warto użyć kodu źródłowego, generowane przez kreatora ATL projektu jako odwołania. Te tematy pierwsze cztery są:  
  

-   [Funkcja CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)  
  
-   [Funkcja CAtlServiceModuleT::ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)  
  
-   [Funkcja CAtlServiceModuleT::Run](../atl/reference/catlservicemodulet-class.md#run)  
  
-   [Funkcja CAtlServiceModuleT::Handler](../atl/reference/catlservicemodulet-class.md#handler)  
  
 Ostatnie trzy tematach opisano pojęcia dotyczące projektowania usługi:  
  
-   [Wpisy rejestru](../atl/registry-entries.md) dla usługi ATL  
  
-   [DCOMCNFG](../atl/dcomcnfg.md)  
  
-   [Debugowanie porady](../atl/debugging-tips.md) dla usługi ATL  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../atl/active-template-library-atl-concepts.md)

