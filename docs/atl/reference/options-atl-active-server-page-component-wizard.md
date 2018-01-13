---
title: "Opcje, Kreator składników stron ASP ATL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.asp.options
dev_langs: C++
helpviewer_keywords: ATL Active Server Page Component Wizard, options
ms.assetid: 54f34e26-53c7-4456-9675-cb86e356bde0
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6564b340458ae7e9a8e137d2338ba68b3e729a0f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="options-atl-active-server-page-component-wizard"></a>Opcje, Kreator składników stron ASP ATL
Ta strona ATL Active Server strona kreatora składników służy do projektowania dla zwiększenia wydajności i obsługa błędów dla obiekt.  
  
 Aby uzyskać więcej informacji dotyczących projektów ATL i klasy ATL COM, zobacz [ATL COM — składniki pulpitu](../../atl/atl-com-desktop-components.md).  
  
 **Model wątkowości**  
 Wskazuje metodę zarządzania wątków. Domyślnie używa projektu **apartamentu** wątków.  
  
 Zobacz [określanie modelu wątkowości projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) Aby uzyskać więcej informacji.  
  
|Opcja|Opis|  
|------------|-----------------|  
|`Single`|Określa, że obiekt używa pojedynczego modelu wątkowości. W jednym modelu wątkowości obiektu zawsze działa w podstawowym wątku com. Zobacz [Apartamentach Single-Threaded](http://msdn.microsoft.com/library/windows/desktop/ms680112) i [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) Aby uzyskać więcej informacji.|  
|**Apartamentu**|Określa, że obiekt używa wątkowości typu apartment. Komórka odpowiednikiem pojedynczego wątku. Każdy obiekt składnika typu apartment przypisano apartamentu jego wątku przez cały okres istnienia obiektu. Jednak wiele wątków może służyć do wielu obiektów. Każdą jest związana z konkretnym wątkiem i ma przekazywanie komunikatów systemu Windows (ustawienie domyślne).<br /><br /> Zobacz [Apartamentach Single-Threaded](http://msdn.microsoft.com/library/windows/desktop/ms680112) Aby uzyskać więcej informacji.|  
|**Zarówno**|Określa, czy obiekt może używać typu apartment lub wolnych wątków w zależności od jakiego rodzaju wątku jest tworzony.|  
|**W warstwie bezpłatna**|Określa, że obiekt ma być używany wolnych wątków. Wolnych wątków jest równoważna z modelem typu apartment wielowątkowe. Zobacz [Apartamentach wielowątkowe](http://msdn.microsoft.com/library/windows/desktop/ms693421) Aby uzyskać więcej informacji.|  
|**Neutralna** (tylko system Windows 2000)|Określa, że obiekt następuje wytyczne dotyczące apartamentach wielowątkowe, ale można wykonywać na dowolny rodzaj wątku.|  
  
 **Agregacja**  
 Wskazuje, czy obiekt używa [agregacji](http://msdn.microsoft.com/library/windows/desktop/ms686558). Obiektu agregacji wybiera, które interfejsy dla klientów i interfejsy są widoczne tak, jakby obiektu agregacji zaimplementowana je. Klienci obiektu agregacji komunikować się tylko z obiektem agregacji.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Tak**|Określa, czy obiekt może agregować. Domyślnie.|  
|**Brak**|Określa, że obiekt nie jest agregowany.|  
|**Tylko**|Określa, czy obiekt musi być agregowana.|  
  
 **Obsługa**  
 (Opis elementu do dodania)  
  
|Opcja|Opis|  
|------------|-----------------|  
|**ISupportErrorInfo**|Tworzy obsługę [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) interfejsu, obiekt można zwrócić informacje o błędzie do klienta.|  
|**Punkty połączenia**|Włącza punktów połączeń dla obiekt dokonując pochodzi od klasy do obiektu [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|  
|**Opcja**|Tworzy obiekt opcja do wskaźników interfejsu kierowanie wydajnie między wątkami w tym samym procesie. Dostępne do określania, albo obiekt **zarówno** lub **wolne** jako modelu wątkowości.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator składników stron ASP ATL](../../atl/reference/atl-active-server-page-component-wizard.md)   
 [Składnik strony Active Server ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)

