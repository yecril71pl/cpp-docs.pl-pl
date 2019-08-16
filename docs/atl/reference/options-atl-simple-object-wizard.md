---
title: Opcje, Kreator prostego obiektu ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.simple.options
helpviewer_keywords:
- ATL Simple Object Wizard, options
ms.assetid: 125fe179-942d-4181-8b82-33e92e1fd779
ms.openlocfilehash: e92f4909907645fc317590fbcc3601887346c642
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495157"
---
# <a name="options-atl-simple-object-wizard"></a>Opcje, Kreator prostego obiektu ATL

Użyj tej strony Kreatora prostych obiektów ATL, aby zaprojektować w celu zwiększenia wydajności i obsługi błędów dla obiektu.

Aby uzyskać więcej informacji na temat projektów ATL i klas COM ATL, zobacz [składniki komputerów stacjonarnych ATL com](../../atl/atl-com-desktop-components.md).

- **Model wątkowości**

   Wskazuje metodę zarządzania wątkami. Domyślnie projekt używa wątków apartamentu .

   Aby uzyskać więcej informacji [, zobacz Określanie modelu wątkowości projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) .

   |Opcja|Opis|
   |------------|-----------------|
   |**Single**|Określa, że obiekt jest zawsze uruchamiany w podstawowym wątku COM. Aby uzyskać więcej informacji, zobacz apartamentach i [InprocServer32](/windows/win32/com/inprocserver32) o [pojedynczym wątku](/windows/win32/com/single-threaded-apartments) .|
   |**Apartamentu**|Określa, że obiekt używa wątka Apartment. Równoważne z pojedynczym apartamentem wątku. Każdy obiekt składnika Apartment jest przypisany do wątku, dla którego jest przeznaczony dla tego obiektu; Jednak wiele wątków może być używanych dla wielu obiektów. Każda komórka jest powiązana z określonym wątkiem i ma pompę komunikatów systemu Windows (domyślnie).<br /><br /> Aby uzyskać więcej informacji, zobacz [apartamentach pojedyncze wątki](/windows/win32/com/single-threaded-apartments) .|
   |**Jedn**|Określa, że obiekt może używać Apartment lub Free Threading, w zależności od tego, jaki typ wątku jest tworzony.|
   |**Bezpłatna**|Określa, że obiekt używa wolnych wątków. Bezpłatna wątkowość jest równoważna z modelem apartamentu wielowątkowej. Aby uzyskać więcej informacji, zobacz [wielowątkowy apartamentach](/windows/win32/com/multithreaded-apartments) .|
   |**Zerowy**|Określa, że obiekt jest zgodny z wytycznymi dla wielowątkowych apartamentach, ale można go wykonać na dowolnym rodzaju wątku.|

- **Agregacja**

   Wskazuje, czy obiekt używa [agregacji](/windows/win32/com/aggregation). Obiekt zagregowany wybiera interfejsy, które należy uwidocznić klientom, a interfejsy są ujawniane tak, jakby obiekt agregacji zaimplementował je. Klienci obiektu zagregowanego komunikują się tylko z obiektem Aggregate.

   |Opcja|Opis|
   |------------|-----------------|
   |**Tak**|Określa, że obiekt może być zagregowany. Domyślnie.|
   |**Znaleziono**|Określa, że obiekt nie jest agregowany.|
   |**Only**|Określa, że obiekt musi być zagregowany.|

- **Interface**

   Wskazuje typ interfejsu obsługiwanego przez obiekt. Domyślnie obiekt obsługuje interfejs podwójny.

   |Opcja|Opis|
   |------------|-----------------|
   |**Dual**|Określa, że obiekt obsługuje podwójny interfejs (jego tablicę zawierającą niestandardowe funkcje interfejsu i metody późnego wiązania `IDispatch` ). Zezwala na dostęp do obiektu zarówno klientom COM, jak i [kontrolerom automatyzacji](../../mfc/automation-clients.md) . Domyślnie.|
   |**Custom**|Określa, że obiekt obsługuje interfejs niestandardowy (jego tablicę zawierającą niestandardowe funkcje interfejsu). Niestandardowy interfejs może być szybszy niż podwójny interfejs, szczególnie w granicach procesu.<br /><br /> - **Zgodne** z automatyzacją Umożliwia kontrolerom automatyzacji dostęp do obiektu, który ma obsługę interfejsu niestandardowego.|

- **Pomoc techniczna**

   Wskazuje dodatkową pomoc techniczną dla obiektu.

   |Opcja|Opis|
   |------------|-----------------|
   |**ISupportErrorInfo**|Tworzy obsługę interfejsu [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) , aby obiekt mógł zwrócić do klienta informacje o błędzie.|
   |**Punkty połączenia**|Włącza punkty połączenia dla obiektu przez uczynienie klasy obiektu pochodną od [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|
   |**Organizator wolnych wątków**|Tworzy obiekt organizatora wolnych wątków do wydajnego organizowania wskaźników interfejsów między wątkami w tym samym procesie. Dostępne dla obiektu określającego **zarówno** jako model wątkowości.|
   |**IObjectWithSite** (Obsługa obiektów IE)|Implementuje [IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md), która zapewnia prosty sposób obsługi komunikacji między obiektem a jego lokacją w kontenerze.|

## <a name="see-also"></a>Zobacz także

[Kreator prostych obiektów ATL](../../atl/reference/atl-simple-object-wizard.md)<br/>
[Prosty obiekt ATL](../../atl/reference/adding-an-atl-simple-object.md)<br/>
[Problemy wątkowości serwera w procesie](/windows/win32/com/in-process-server-threading-issues)
