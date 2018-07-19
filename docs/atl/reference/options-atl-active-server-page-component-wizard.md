---
title: Opcje, Kreator składników stron Active Server ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.asp.options
dev_langs:
- C++
helpviewer_keywords:
- ATL Active Server Page Component Wizard, options
ms.assetid: 54f34e26-53c7-4456-9675-cb86e356bde0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cdd3e62915b81311450cf4d798b04f8df30492ff
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884603"
---
# <a name="options-atl-active-server-page-component-wizard"></a>Opcje, Kreator składników stron Active Server ATL
Użyj tej strony ATL Active Server strona kreatora składników się projektowania pod kątem zwiększenia wydajności i obsługi błędów dla tego obiektu.  
  
 Aby uzyskać więcej informacji na temat projektów ATL i klasy ATL COM, zobacz [ATL COM pulpitu składniki](../../atl/atl-com-desktop-components.md).  
  
 **Model wątkowości**  
 Wskazuje metodę zarządzania wątków. Domyślnie używa projektu **apartamentu** wątków.  
  
 Zobacz [określanie modelu wątkowości projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) Aby uzyskać więcej informacji.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Single**|Określa, że obiekt używa pojedynczego modelu wątkowości. W jednym modelu wątkowości obiekt zawsze działa w podstawowym wątku com. Zobacz [Apartamentach Single-Threaded](http://msdn.microsoft.com/library/windows/desktop/ms680112) i [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) Aby uzyskać więcej informacji.|  
|**Apartamentu**|Określa, że obiekt używa wątkowości typu apartment. Komórka równoważne z jednego wątku. Każdy obiekt jako składnik typu apartment przypisano Lokal do wątku, przez cały okres istnienia obiektu. Jednak wiele wątków może służyć do wielu obiektów. Każda komórka jest powiązany z określonym wątku i ma pompy komunikatów Windows (ustawienie domyślne).<br /><br /> Zobacz [Apartamentach Single-Threaded](http://msdn.microsoft.com/library/windows/desktop/ms680112) Aby uzyskać więcej informacji.|  
|**Oba**|Określa, czy obiekt może używać apartamentu lub wolnych wątków w zależności od jakich wątek jest tworzony.|  
|**Bezpłatne**|Określa, że obiekt używa wolnych wątków. Wolnych wątków jest równoważna z modelem apartamentu wielowątkowych. Zobacz [wielowątkowy Apartamentach](http://msdn.microsoft.com/library/windows/desktop/ms693421) Aby uzyskać więcej informacji.|  
|**Niezależny od**|Określa, że obiekt następujące wytyczne dotyczące wielowątkowy apartamentach, ale można wykonywać na dowolny rodzaj wątku.|  
  
 **Agregacja**  
 Wskazuje, czy obiekt używa [agregacji](http://msdn.microsoft.com/library/windows/desktop/ms686558). Wybiera obiektu agregacji, które interfejsy do udostępnienia klientom i interfejsy są dostępne, tak jakby obiekt agregacji, zaimplementować je. Klienci z obiektu agregacji komunikują się tylko za pomocą obiektu agregacji.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Tak**|Określa, czy obiekt może być agregowany. Domyślnie.|  
|**Brak**|Określa, że obiekt nie jest agregowany.|  
|**Only**|Określa, czy obiekt musi być agregowana.|  
  
 **Obsługa**  
 (Opis elementu do dodania)  
  
|Opcja|Opis|  
|------------|-----------------|  
|`ISupportErrorInfo`|Tworzy obsługę [Interfejs ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) interfejsu, obiekt może zwrócić informacje o błędzie do klienta.|  
|**Punkty połączenia**|Włącza punkty połączenia dla obiektu, wprowadzając nazwę obiektu klasy pochodzi od [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|  
|**Bezwątkowego**|Tworzy obiekt bezwątkowego na przeprowadzanie marshalingu wskaźników interfejsu efektywnie między wątkami w tym samym procesie. Dostępne do wybrania obiektu **zarówno** lub **bezpłatna** jako modelu wątkowości.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator składników stron Active Server ATL](../../atl/reference/atl-active-server-page-component-wizard.md)   
 [Składnika strony Active Server ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)

