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
ms.openlocfilehash: 529b6d0eaedaee200da547ef9ed980aab51ea233
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622172"
---
# <a name="ole-in-mfc"></a>OLE w MFC

W tych artykułach objaśniono podstawowe informacje dotyczące programowania obiektów OLE przy użyciu biblioteki MFC. MFC zapewnia najprostszy sposób pisania programów korzystających z interfejsu OLE:

- Aby użyć edycji wizualnej OLE (aktywacja w miejscu).

- Do pracy z kontenerami lub serwerami OLE.

- W celu zaimplementowania funkcji przeciągania i upuszczania.

- Do pracy z danymi daty i godziny.

- Zarządzanie danymi stanu modułów MFC, w tym wyeksportowane punkty wejścia funkcji DLL, punkty wejścia interfejsu OLE/COM i punkty wejścia procedury okna.

Można również użyć [automatyzacji](automation.md).

> [!NOTE]
> Termin OLE oznacza technologie związane z łączeniem i osadzaniem, w tym kontenery OLE, serwery OLE, elementy OLE, aktywacja w miejscu (lub edytowanie wizualne), śledzenie, przeciąganie i upuszczanie oraz scalanie menu. Termin aktywny dotyczy obiektów opartych na Component Object Model (COM) i COM, takich jak kontrolki ActiveX. Automatyzacja OLE jest teraz nazywana automatyzacją.

## <a name="in-this-section"></a>W tej sekcji

[Podstawy OLE](ole-background.md)<br/>
Omówienie technologii OLE i zawiera informacje o pojęciach związanych z tym, jak to działa.

[Uaktywnienie](activation-cpp.md)<br/>
Opisuje rolę aktywacji w edycji elementów OLE.

[Containers](containers.md)<br/>
Oferuje linki do korzystania z kontenerów w technologii OLE.

[Obiekty danych i źródła danych](data-objects-and-data-sources-ole.md)<br/>
Zawiera łącza do tematów omawiających korzystanie z `COleDataObject` `COleDataSource` klas i.

[Przeciągnij i opuść](drag-and-drop-ole.md)<br/>
Omawia używanie kopiowania i wklejania z OLE.

[Menu i zasoby OLE](menus-and-resources-ole.md)<br/>
Wyjaśnia korzystanie z menu i zasobów w aplikacjach MFC OLE.

[Rejestracja](registration.md)<br/>
Omawia instalację i inicjalizację serwera.

[Serwery](servers.md)<br/>
Opisuje sposób tworzenia elementów OLE (lub składników) do użycia przez aplikacje kontenerów.

[Trackery](trackers.md)<br/>
Zawiera informacje o `CRectTracker` klasie, która udostępnia interfejs graficzny umożliwiający użytkownikom posługiwanie się elementami klienta OLE.

## <a name="related-sections"></a>Sekcje pokrewne

[Punkty połączenia](connection-points.md)<br/>
Wyjaśnia, jak zaimplementować punkty połączenia (wcześniej znane jako punkty połączenia OLE) przy użyciu klas MFC `CCmdTarget` i `CConnectionPoint` .

[Składniki COM kontenera/serwera](containers-advanced-features.md)<br/>
Zawiera opis czynności, które należy wykonać, aby dołączyć opcjonalne funkcje zaawansowane do istniejących aplikacji kontenera.

[Component Object Model](/windows/win32/com/the-component-object-model)<br/>
Opisuje używanie technologii OLE bez MFC.

## <a name="see-also"></a>Zobacz też

[Pojęcia](mfc-concepts.md)
