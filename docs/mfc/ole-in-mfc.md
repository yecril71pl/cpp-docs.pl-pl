---
title: OLE w MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, OLE and
- OLE items
- OLE applications [MFC], about OLE
- OLE [MFC]
- OLE containers [MFC], about OLE
- applications [OLE], about OLE
- OLE component object model (COM)
ms.assetid: 5193479d-1239-4697-aea4-e82f92c707ab
ms.openlocfilehash: 2594531df63bcd62cdaec44fbc3668ea68990922
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366897"
---
# <a name="ole-in-mfc"></a>OLE w MFC

Artykuły te wyjaśniają podstawy programowania OLE przy użyciu MFC. MFC zapewnia najprostszy sposób pisania programów, które używają OLE:

- Aby użyć edycji wizualnej OLE (aktywacja w miejscu).

- Do pracy jako kontenery OLE lub serwery.

- Aby zaimplementować funkcję przeciągania i upuszczania.

- Do pracy z danymi daty i godziny.

- Aby zarządzać danymi stanu modułów MFC, w tym eksportowane punkty wejścia funkcji DLL, punkty wejścia interfejsu OLE/COM i punkty wejścia procedury okna.

Można również użyć [automatyzacji](../mfc/automation.md).

> [!NOTE]
> Termin OLE oznacza technologie skojarzone z łączeniem i osadzaniem, w tym kontenery OLE, serwery OLE, elementy OLE, aktywację w miejscu (lub edycję wizualną), trackery, przeciąganie i upuszczanie oraz scalanie menu. Termin Active ma zastosowanie do obiektów opartych na modelu com i com, takich jak formanty ActiveX. Automatyzacja OLE jest teraz nazywana automatyzacją.

## <a name="in-this-section"></a>W tej sekcji

[Podstawy OLE](../mfc/ole-background.md)<br/>
W tym artykule omówiono OLE i zawiera informacje koncepcyjne o tym, jak to działa.

[Aktywacja](../mfc/activation-cpp.md)<br/>
Opisuje rolę aktywacji w edycji elementów OLE.

[Containers](../mfc/containers.md)<br/>
Zawiera łącza do korzystania z kontenerów w ole.

[Obiekty danych i źródła danych](../mfc/data-objects-and-data-sources-ole.md)<br/>
Zawiera łącza do tematów omawiających użycie `COleDataObject` i `COleDataSource` klas.

[Przeciągnij i opuść](../mfc/drag-and-drop-ole.md)<br/>
W tym artykule omówiono przy użyciu kopiowania i wklejania z OLE.

[Menu OLE i zasoby](../mfc/menus-and-resources-ole.md)<br/>
Wyjaśniono użycie menu i zasobów w aplikacjach dokumentów MFC OLE.

[Rejestracja](../mfc/registration.md)<br/>
W tym artykule omówiono instalację i inicjowanie serwera.

[Serwery](../mfc/servers.md)<br/>
W tym artykule opisano sposób tworzenia elementów OLE (lub składników) do użytku przez aplikacje kontenera.

[Trackery](../mfc/trackers.md)<br/>
Zawiera informacje `CRectTracker` o klasie, która udostępnia interfejs graficzny, aby umożliwić użytkownikom interakcję z elementami klienta OLE.

## <a name="related-sections"></a>Sekcje pokrewne

[Punkty połączenia](../mfc/connection-points.md)<br/>
Wyjaśniono, jak zaimplementować punkty połączenia (wcześniej znane `CCmdTarget` `CConnectionPoint`jako punkty połączenia OLE) przy użyciu klas MFC i .

[Składniki COM kontenera/serwera](../mfc/containers-advanced-features.md)<br/>
W tym artykule opisano kroki niezbędne do włączenia opcjonalnych funkcji zaawansowanych do istniejących aplikacji kontenera.

[Model obiektu komponentu](/windows/win32/com/the-component-object-model)<br/>
Opisuje użycie ole bez MFC.

## <a name="see-also"></a>Zobacz też

[Pojęcia](../mfc/mfc-concepts.md)
