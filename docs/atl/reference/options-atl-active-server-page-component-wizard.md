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
ms.openlocfilehash: f2198904905c4e130e320d8fe52638850696f127
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762850"
---
# <a name="options-atl-active-server-page-component-wizard"></a>Opcje, Kreator składników stron Active Server ATL

Użyj tej strony ATL Active Server strona kreatora składników się projektowania pod kątem zwiększenia wydajności i obsługi błędów dla tego obiektu.

Aby uzyskać więcej informacji na temat projektów ATL i klasy ATL COM, zobacz [ATL COM pulpitu składniki](../../atl/atl-com-desktop-components.md).

**Model wątkowości**  
Wskazuje metodę zarządzania wątków. Domyślnie używa projektu **apartamentu** wątków.

Zobacz [określanie modelu wątkowości projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) Aby uzyskać więcej informacji.

|Opcja|Opis|
|------------|-----------------|
|**Single**|Określa, że obiekt używa pojedynczego modelu wątkowości. W jednym modelu wątkowości obiekt zawsze działa w podstawowym wątku com. Zobacz [Apartamentach Single-Threaded](/windows/desktop/com/single-threaded-apartments) i [InprocServer32](/windows/desktop/com/inprocserver32) Aby uzyskać więcej informacji.|
|**Apartamentu**|Określa, że obiekt używa wątkowości typu apartment. Komórka równoważne z jednego wątku. Każdy obiekt jako składnik typu apartment przypisano Lokal do wątku, przez cały okres istnienia obiektu. Jednak wiele wątków może służyć do wielu obiektów. Każda komórka jest powiązany z określonym wątku i ma pompy komunikatów Windows (ustawienie domyślne).<br /><br /> Zobacz [Apartamentach Single-Threaded](/windows/desktop/com/single-threaded-apartments) Aby uzyskać więcej informacji.|
|**Oba**|Określa, czy obiekt może używać apartamentu lub wolnych wątków w zależności od jakich wątek jest tworzony.|
|**Bezpłatne**|Określa, że obiekt używa wolnych wątków. Wolnych wątków jest równoważna z modelem apartamentu wielowątkowych. Zobacz [wielowątkowy Apartamentach](/windows/desktop/com/multithreaded-apartments) Aby uzyskać więcej informacji.|
|**Niezależny od**|Określa, że obiekt następujące wytyczne dotyczące wielowątkowy apartamentach, ale można wykonywać na dowolny rodzaj wątku.|

**Agregacja**  
Wskazuje, czy obiekt używa [agregacji](/windows/desktop/com/aggregation). Wybiera obiektu agregacji, które interfejsy do udostępnienia klientom i interfejsy są dostępne, tak jakby obiekt agregacji, zaimplementować je. Klienci z obiektu agregacji komunikują się tylko za pomocą obiektu agregacji.

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

