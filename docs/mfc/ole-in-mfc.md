---
title: OLE w MFC | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, OLE and
- OLE items
- OLE applications [MFC], about OLE
- OLE [MFC]
- OLE containers [MFC], about OLE
- applications [OLE], about OLE
- OLE component object model (COM)
ms.assetid: 5193479d-1239-4697-aea4-e82f92c707ab
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c2a7fcd7db19d9dcc6e12c351a3fd55f0e67b118
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ole-in-mfc"></a>OLE w MFC
Artykuły te wyjaśniają zasady podstawy programowania OLE za pomocą MFC. MFC zapewnia Najprostszym sposobem pisania programów, które używają OLE:  
  
-   Aby użyć OLE visual edycji (Aktywacja w miejscu).  
  
-   Aby działają jak kontenery OLE lub serwery.  
  
-   Aby zaimplementować funkcjonalność przeciągania i upuszczania.  
  
-   Aby pracować z danymi daty i godziny.  
  
-   Zarządzanie danymi stanu MFC moduły, w tym wyeksportowane punkty wejścia funkcji DLL, punkty wejścia interfejsu OLE/COM i punkty wejścia procedury okna.  
  
 Można również użyć [automatyzacji](../mfc/automation.md) lub [automatyzacji zdalnej](../mfc/remote-automation.md) do działania innego programu z programu.  
  
> [!NOTE]
>  Termin OLE oznacza technologii skojarzone z łączenie i osadzanie, takich jak kontenery OLE, serwerów OLE, elementy OLE, aktywacja w miejscu (lub edycja wizualna), trackerów, przeciągnij i upuść, a scalaniem menu. Termin aktywny dotyczy składnika modelu COM (Object) i obiekty oparte na modelu COM, takie jak kontrolki ActiveX. Automatyzacja OLE nosi teraz automatyzacji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Podstawy OLE](../mfc/ole-background.md)  
 W tym artykule omówiono OLE i znajdują się informacje koncepcyjne na temat jej działania.  
  
 [Aktywacji](../mfc/activation-cpp.md)  
 Zawiera opis roli aktywacji edytowania elementów OLE.  
  
 [Kontenery](../mfc/containers.md)  
 Zawiera łącza do używanie kontenerów w OLE.  
  
 [Obiekty danych i źródła danych](../mfc/data-objects-and-data-sources-ole.md)  
 Zawiera łącza do tematów korzystanie z omówieniem `COleDataObject` i `COleDataSource` klasy.  
  
 [Przeciągnij i upuść](../mfc/drag-and-drop-ole.md)  
 W tym artykule omówiono za pomocą kopiowania i wklejania z OLE.  
  
 [Menu i zasoby OLE](../mfc/menus-and-resources-ole.md)  
 Wyjaśnienia dotyczące korzystania z menu i zasoby w aplikacji MFC OLE dokumentu.  
  
 [Rejestracji](../mfc/registration.md)  
 W tym artykule omówiono instalacji serwera i inicjowania.  
  
 [Serwery](../mfc/servers.md)  
 Opisuje sposób tworzenia elementów OLE (lub składników) do użycia przez aplikacje kontenera.  
  
 [Trackery](../mfc/trackers.md)  
 Zawiera informacje na temat `CRectTracker` klasy, która udostępnia interfejsem graficznym, aby umożliwić użytkownikom na interakcję z elementami klienta OLE.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Punkty połączenia](../mfc/connection-points.md)  
 Opisuje sposób nadawania punkty połączenia (wcześniej znane jako punkty połączenia OLE) przy użyciu klas MFC `CCmdTarget` i `CConnectionPoint`.  
  
 [Składniki COM kontenera/serwera](../mfc/containers-advanced-features.md)  
 Opisuje czynności, włączenie zaawansowanych funkcji opcjonalnych do istniejących aplikacji kontenera.  
  
 [Model Component Object Model](http://msdn.microsoft.com/library/windows/desktop/ms694363)  
 Zawiera opis używania OLE bez MFC.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../mfc/mfc-concepts.md)

