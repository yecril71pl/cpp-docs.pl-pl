---
title: Opcje, Kreator prostych obiektów ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.simple.options
dev_langs:
- C++
helpviewer_keywords:
- ATL Simple Object Wizard, options
ms.assetid: 125fe179-942d-4181-8b82-33e92e1fd779
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1cef503bf9862f1259e25aff76a013d60776077
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883729"
---
# <a name="options-atl-simple-object-wizard"></a>Opcje, Kreator prostych obiektów ATL
Użyj tej strony Kreator prostego obiektu ATL projektować pod kątem zwiększenia wydajności i obsługi błędów dla tego obiektu.  
  
 Aby uzyskać więcej informacji na temat projektów ATL i klasy ATL COM, zobacz [ATL COM pulpitu składniki](../../atl/atl-com-desktop-components.md).  
  
 **Model wątkowości**  
 Wskazuje metodę zarządzania wątków. Domyślnie używa projektu **apartamentu** wątków.  
  
 Zobacz [określanie modelu wątkowości projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) Aby uzyskać więcej informacji.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Single**|Określa, czy obiekt jest zawsze uruchamiany w podstawowym wątku com. Zobacz [Apartamentach Single-Threaded](http://msdn.microsoft.com/library/windows/desktop/ms680112) i [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) Aby uzyskać więcej informacji.|  
|**Apartamentu**|Określa, że obiekt używa wątkowości typu apartment. Komórka równoważne z jednego wątku. Każdy obiekt jako składnik typu apartment przypisano Lokal do wątku, przez cały okres istnienia obiektu. Jednak wiele wątków może służyć do wielu obiektów. Każda komórka jest powiązany z określonym wątku i ma pompy komunikatów Windows (ustawienie domyślne).<br /><br /> Zobacz [Apartamentach Single-Threaded](http://msdn.microsoft.com/library/windows/desktop/ms680112) Aby uzyskać więcej informacji.|  
|**Oba**|Określa, czy obiekt może używać apartamentu lub wolnych wątków w zależności od jakich wątek jest tworzony.|  
|**Bezpłatne**|Określa, że obiekt używa wolnych wątków. Wolnych wątków jest równoważna z modelem apartamentu wielowątkowych. Zobacz [wielowątkowy Apartamentach](http://msdn.microsoft.com/library/windows/desktop/ms693421) Aby uzyskać więcej informacji.|  
|**Niezależny od**|Określa, że obiekt następujące wytyczne dotyczące wielowątkowy apartamentach, ale można wykonywać na dowolny rodzaj wątku.|  
  
 **Agregacja**  
 Wskazuje, czy obiekt używa [agregacji](http://msdn.microsoft.com/library/windows/desktop/ms686558). Wybiera obiektu agregacji, które interfejsy do udostępnienia klientom i interfejsy są dostępne, tak jakby obiekt agregacji, zaimplementować je. Klienci z obiektu agregacji komunikują się tylko za pomocą obiektu agregacji.  
  
|Opcja|Opis|  
|------------|-----------------|  
|Tak|Określa, czy obiekt może być agregowany. Domyślnie.|  
|Nie|Określa, że obiekt nie jest agregowany.|  
|tylko program|Określa, czy obiekt musi być agregowana.|  
  
 **Interface**  
 Wskazuje typ interfejsu, który obsługuje obiektu. Domyślnie obiekt obsługuje podwójnego interfejsu.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Dual**|Określa, że obiekt obsługuje interfejs podwójny (jego vtable ma niestandardowy interfejs funkcji oraz późne powiązania `IDispatch` metody). Umożliwia obaj klienci COM i [kontrolery automatyzacji](../../mfc/automation-clients.md) dostępu do obiektu. Domyślnie.|  
|**Niestandardowy**|Określa, że obiekt obsługuje interfejs niestandardowy (jego vtable ma niestandardowy interfejs funkcji). Niestandardowy interfejs może być szybsza niż podwójnego interfejsu, szczególnie w granicach procesu.<br /><br /> -   **Automatyzacja zgodne** kontrolery automatyzacji umożliwia dostępu do obiektu, który obsługuje niestandardowy interfejs.|  
  
 **Obsługa**  
 Wskazuje dodatkową pomoc techniczną dla obiektu.  
  
|Opcja|Opis|  
|------------|-----------------|  
|`ISupportErrorInfo`|Tworzy obsługę [Interfejs ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) interfejsu, obiekt może zwrócić informacje o błędzie do klienta.|  
|**Punkty połączenia**|Włącza punkty połączenia dla obiektu, wprowadzając nazwę obiektu klasy pochodzi od [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|  
|**Bezwątkowego**|Tworzy obiekt bezwątkowego na przeprowadzanie marshalingu wskaźników interfejsu efektywnie między wątkami w tym samym procesie. Dostępne do określania obiektu **zarówno** jako modelu wątkowości.|  
|`IObjectWithSite` **(Obsługa obiektów programu Internet Explorer)**|Implementuje [IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md), który zapewnia prosty sposób obsługi komunikacji między obiektem i jego witryny w kontenerze.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator prostych obiektów ATL](../../atl/reference/atl-simple-object-wizard.md)   
 [Prosty obiekt ATL](../../atl/reference/adding-an-atl-simple-object.md)   
 [Problemy wielowątkowości dotyczące serwera przetwarzania](http://msdn.microsoft.com/library/windows/desktop/ms687205)

