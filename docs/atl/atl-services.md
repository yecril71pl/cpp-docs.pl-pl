---
title: "Usługi ATL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CServiceModule
dev_langs: C++
helpviewer_keywords:
- CServiceModule class
- COM objects, ATL
- services, ATL
- ATL services
ms.assetid: 8c09d1a8-7548-4d2c-947c-9d795a81659b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5b0572f4d83cfc6b098f290cda53592dbe4aa54b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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

