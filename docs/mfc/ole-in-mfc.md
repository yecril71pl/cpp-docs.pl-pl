---
title: OLE w MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, OLE and
- OLE items
- OLE applications [MFC], about OLE
- OLE [MFC]
- OLE containers [MFC], about OLE
- applications [OLE], about OLE
- OLE component object model (COM)
ms.assetid: 5193479d-1239-4697-aea4-e82f92c707ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e43484e5f30191c604f43a2280a8deab6eddd93c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434950"
---
# <a name="ole-in-mfc"></a>OLE w MFC

Artykuły te wyjaśniają zasady podstawy programowania OLE przy użyciu biblioteki MFC. Biblioteka MFC zawiera Najprostszym sposobem pisania programów, które używają OLE:

- Aby użyć OLE visual edycji (aktywacji w miejscu).

- Aby działać jako kontenery OLE lub serwerów.

- Do implementacji funkcji przeciągania i upuszczania.

- Aby pracować z danymi daty i godziny.

- Zarządzanie danymi stanu MFC moduły, w tym wyeksportowane punkty wejścia funkcji DLL, punkty wejścia interfejsu OLE/COM i punkty wejścia procedury okna.

Można również użyć [automatyzacji](../mfc/automation.md).

> [!NOTE]
>  Termin, który oznacza OLE, technologie związane z łączenia i osadzania, takie jak kontenery OLE, serwerów OLE, elementy OLE, aktywacji w miejscu (lub edycja wizualna), trackery, przeciągnij i upuść, a scalaniem menu. Termin aktywny odnosi się do Component Object Model (COM) i obiektów opartych na modelu COM, takich jak kontrolki ActiveX. Automatyzacji OLE jest teraz nazywana automatyzacji.

## <a name="in-this-section"></a>W tej sekcji

[Podstawy OLE](../mfc/ole-background.md)<br/>
Zawiera omówienie OLE, a także informacje o pojęciach dotyczących jej działania.

[Aktywacja](../mfc/activation-cpp.md)<br/>
W tym artykule opisano rolę aktywacji w edycji elementów OLE.

[Kontenery](../mfc/containers.md)<br/>
Zawiera łącza do korzystania z kontenerów w OLE.

[Obiekty danych i źródeł danych](../mfc/data-objects-and-data-sources-ole.md)<br/>
Zawiera łącza do tematów omawiających używanie `COleDataObject` i `COleDataSource` klasy.

[Przeciąganie i upuszczanie](../mfc/drag-and-drop-ole.md)<br/>
Omawia, przy użyciu kopiowanie i wklejanie z OLE.

[Menu i zasoby OLE](../mfc/menus-and-resources-ole.md)<br/>
W tym artykule wyjaśniono, użyj menu i zasoby w aplikacjach dokumentu MFC OLE.

[Rejestracja](../mfc/registration.md)<br/>
W tym artykule omówiono serwera instalacji i inicjacji.

[Serwery](../mfc/servers.md)<br/>
W tym artykule opisano, jak utworzyć elementy OLE (lub składniki) do użycia przez aplikacje kontenera.

[Trackery](../mfc/trackers.md)<br/>
Zawiera informacje na temat `CRectTracker` klasy, która udostępnia interfejs graficzny umożliwiający użytkownikom interakcję z elementami klienta OLE.

## <a name="related-sections"></a>Sekcje pokrewne

[Punkty połączenia](../mfc/connection-points.md)<br/>
Wyjaśnia, jak wdrożyć punktów połączenia (wcześniej znane jako punkty połączenia OLE) przy użyciu klas MFC `CCmdTarget` i `CConnectionPoint`.

[Składniki kontenera/serwera COM](../mfc/containers-advanced-features.md)<br/>
W tym artykule opisano kroki niezbędne do dołączyć opcjonalny zaawansowane funkcje do istniejących aplikacji kontenerowych.

[Model Component Object Model](/windows/desktop/com/the-component-object-model)<br/>
W tym artykule opisano, przy użyciu OLE bez MFC.

## <a name="see-also"></a>Zobacz też

[Pojęcia](../mfc/mfc-concepts.md)

