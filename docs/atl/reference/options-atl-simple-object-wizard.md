---
title: "Opcje, Kreator prostych obiektów ATL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.simple.options
dev_langs:
- C++
helpviewer_keywords:
- ATL Simple Object Wizard, options
ms.assetid: 125fe179-942d-4181-8b82-33e92e1fd779
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 37341dc23f95e1863aeae4a1b57c01d24d6ad365
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="options-atl-simple-object-wizard"></a>Opcje, Kreator prostych obiektów ATL
Ta strona kreatora prosty obiekt ATL do projektowania dla zwiększenia wydajności i obsługa błędów dla obiekt.  
  
 Aby uzyskać więcej informacji dotyczących projektów ATL i klasy ATL COM, zobacz [ATL COM — składniki pulpitu](../../atl/atl-com-desktop-components.md).  
  
 **Model wątkowości**  
 Wskazuje metodę zarządzania wątków. Domyślnie używa projektu **apartamentu** wątków.  
  
 Zobacz [określanie modelu wątkowości projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) Aby uzyskać więcej informacji.  
  
|Opcja|Opis|  
|------------|-----------------|  
|`Single`|Określa, czy obiekt jest zawsze uruchamiany w podstawowym wątku com. Zobacz [Apartamentach Single-Threaded](http://msdn.microsoft.com/library/windows/desktop/ms680112) i [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) Aby uzyskać więcej informacji.|  
|**Apartamentu**|Określa, że obiekt używa wątkowości typu apartment. Komórka odpowiednikiem pojedynczego wątku. Każdy obiekt składnika typu apartment przypisano apartamentu jego wątku przez cały okres istnienia obiektu. Jednak wiele wątków może służyć do wielu obiektów. Każdą jest związana z konkretnym wątkiem i ma przekazywanie komunikatów systemu Windows (ustawienie domyślne).<br /><br /> Zobacz [Apartamentach Single-Threaded](http://msdn.microsoft.com/library/windows/desktop/ms680112) Aby uzyskać więcej informacji.|  
|**Zarówno**|Określa, czy obiekt może używać typu apartment lub wolnych wątków w zależności od jakiego rodzaju wątku jest tworzony.|  
|**W warstwie bezpłatna**|Określa, że obiekt ma być używany wolnych wątków. Wolnych wątków jest równoważna z modelem typu apartment wielowątkowe. Zobacz [Apartamentach wielowątkowe](http://msdn.microsoft.com/library/windows/desktop/ms693421) Aby uzyskać więcej informacji.|  
|**Neutralna**|Określa, że obiekt następuje wytyczne dotyczące apartamentach wielowątkowe, ale można wykonywać na dowolny rodzaj wątku.|  
  
 **Agregacja**  
 Wskazuje, czy obiekt używa [agregacji](http://msdn.microsoft.com/library/windows/desktop/ms686558). Obiektu agregacji wybiera, które interfejsy dla klientów i interfejsy są widoczne tak, jakby obiektu agregacji zaimplementowana je. Klienci obiektu agregacji komunikować się tylko z obiektem agregacji.  
  
|Opcja|Opis|  
|------------|-----------------|  
|Tak|Określa, czy obiekt może agregować. Domyślnie.|  
|Nie|Określa, że obiekt nie jest agregowany.|  
|tylko program|Określa, czy obiekt musi być agregowana.|  
  
 **Interface**  
 Wskazuje typ interfejsu, który obsługuje obiektu. Domyślnie obiekt obsługuje dwa interfejsu.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Dual**|Określa, że obiekt obsługuje dwa interfejsu (jego vtable ma niestandardowy interfejs funkcje oraz późne wiązanie `IDispatch` metody). Umożliwia klientom zarówno COM i [kontrolerów automatyzacji](../../mfc/automation-clients.md) dostępu do tego obiektu. Domyślnie.|  
|**Niestandardowy**|Określa, że obiekt obsługuje niestandardowy interfejs (jego vtable ma funkcje niestandardowy interfejs). Niestandardowy interfejs może być szybsza niż dwa interfejsu, szczególnie w granicach procesu.<br /><br /> -   **Automatyzacja zgodne** kontrolerów umożliwia automatyzację dostępu do obiektu, który obsługuje niestandardowy interfejs.|  
  
 **Obsługa**  
 Określa dodatkowe wsparcie dla obiekt.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**ISupportErrorInfo**|Tworzy obsługę [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) interfejsu, obiekt można zwrócić informacje o błędzie do klienta.|  
|**Punkty połączenia**|Włącza punktów połączeń dla obiekt dokonując pochodzi od klasy do obiektu [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|  
|**Opcja**|Tworzy obiekt opcja do wskaźników interfejsu kierowanie wydajnie między wątkami w tym samym procesie. Dostępne dla obiekt określający **zarówno** jako modelu wątkowości.|  
|**IObjectWithSite (Obsługa obiektu programu Internet Explorer)**|Implementuje [IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md), która umożliwia w prosty sposób obsługi komunikacji między obiektem i jego lokacji w kontenerze.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator prostych obiektów ATL](../../atl/reference/atl-simple-object-wizard.md)   
 [Prosty obiekt ATL](../../atl/reference/adding-an-atl-simple-object.md)   
 [Problemy wielowątkowości Server wewnątrzprocesowe](http://msdn.microsoft.com/library/windows/desktop/ms687205)

