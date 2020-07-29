---
title: 'Kontenery: stany elementu klienckiego'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE containers [MFC], client-item states
- states, OLE container client-item
- lifetime, lifetime states and OLE container client items
- client items and OLE containers
ms.assetid: e7021caa-bd07-4adb-976e-f5f3d025bc53
ms.openlocfilehash: 660b544a0f061ae2e4435777cdd934367f2e7652
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228651"
---
# <a name="containers-client-item-states"></a>Kontenery: stany elementu klienckiego

W tym artykule wyjaśniono różne stany, w których element klienta przechodzi przez cały okres istnienia.

Element klienta przechodzi przez kilka stanów w miarę jego tworzenia, aktywacji, modyfikacji i zapisywania. Za każdym razem, gdy stan elementu ulegnie zmianie, struktura wywołuje [COleClientItem:: OnChanging](reference/coleclientitem-class.md#onchange) z powiadomieniem **OLE_CHANGED_STATE** . Drugi parametr jest wartością z `COleClientItem::ItemState` wyliczenia. Może być jedną z następujących czynności:

- *COleClientItem:: emptyState*

- *COleClientItem:: loadedState*

- *COleClientItem:: openState*

- *COleClientItem:: activeState*

- *COleClientItem:: activeUIState*

W pustym stanie element klienta nie jest jeszcze całkowicie elementem. Pamięć została przypisana do niej, ale nie została jeszcze zainicjowana z danymi elementu OLE. Jest to stan, w którym element klienta jest tworzony przez wywołanie do, **`new`** ale nie został jeszcze poddany drugi krok typowego tworzenia dwuetapowego.

W drugim kroku, wykonywane przez wywołanie `COleClientItem::CreateFromFile` lub inną `CreateFrom` funkcję *xxxx* , element jest całkowicie utworzony. Dane OLE (z pliku lub innego źródła, takie jak schowek) zostały skojarzone z `COleClientItem` obiektem pochodnym. Teraz element jest w stanie załadowania.

Gdy element zostanie otwarty w oknie serwera, a nie w miejscu w dokumencie kontenera, jest w stanie otwarty (lub w pełni otwarty). W tym stanie Kreskowanie krzyżowe jest zwykle rysowane nad reprezentacją elementu w oknie kontenera, aby wskazać, że element jest aktywny w innym miejscu.

Gdy element został aktywowany w miejscu, przekazuje, zazwyczaj tylko krótko, w stanie aktywnym. Następnie przechodzi do stanu aktywności interfejsu użytkownika, w którym serwer został scalony z menu, paskami narzędzi i innymi składnikami interfejsu użytkownika z tymi kontenerami. Obecność tych składników interfejsu użytkownika odróżnia stan aktywności interfejsu użytkownika ze stanu aktywnego. W przeciwnym razie stan aktywny jest podobny do stanu aktywnego interfejsu użytkownika. Jeśli serwer obsługuje cofanie, serwer jest wymagany do zachowania informacji o stanie cofnięcia elementu OLE do momentu osiągnięcia stanu załadowane lub otwarte.

## <a name="see-also"></a>Zobacz także

[Containers](containers.md)<br/>
[Uaktywnienie](activation-cpp.md)<br/>
[Kontenery: powiadomienia dotyczące elementów klienta](containers-client-item-notifications.md)<br/>
[Trackery](trackers.md)<br/>
[Klasa CRectTracker](reference/crecttracker-class.md)
