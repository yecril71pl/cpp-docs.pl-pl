---
title: 'Kontenery: Stany elementu klienckiego | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE containers [MFC], client-item states
- states, OLE container client-item
- lifetime, lifetime states and OLE container client items
- client items and OLE containers
ms.assetid: e7021caa-bd07-4adb-976e-f5f3d025bc53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e482123207c287c33a36406ba961747545af7c73
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378064"
---
# <a name="containers-client-item-states"></a>Kontenery: stany elementu klienckiego

W tym artykule opisano różne stany, którego element Klient przechodzi w okresie swojego istnienia.

Element kliencki przechodzi przez kilka stanów, ponieważ jest tworzona, aktywowana, zmodyfikować i zapisać. Zawsze zmiany stanu elementu, struktura wywołuje [COleClientItem::OnChange](../mfc/reference/coleclientitem-class.md#onchange) z **OLE_CHANGED_STATE** powiadomień. Drugi parametr ma wartość z zakresu od `COleClientItem::ItemState` wyliczenia. Może to być jedna z następujących czynności:

- *COleClientItem::emptyState*

- *COleClientItem::loadedState*

- *COleClientItem::openState*

- *COleClientItem::activeState*

- *COleClientItem::activeUIState*

W stanu pustego elementu klienta nie jest jeszcze całkowicie elementu. Pamięć została przydzielona dla niego, ale go nie została jeszcze zainicjowana przy użyciu danych elementu OLE. Jest to stan elementu klienta jest w, gdy został on utworzony za pomocą wywołania **nowe** , ale nie zostało jeszcze poddane drugi etap tworzenia typowych dwuetapowej.

W drugim kroku, wykonywane za pomocą wywołania `COleClientItem::CreateFromFile` lub inne `CreateFrom` *xxxx* , element zostanie całkowicie utworzona funkcja. Skojarzonych danych OLE (z pliku lub innego źródła, na przykład zawartość Schowka) `COleClientItem`-pochodnych obiektu. Teraz element jest w stanie załadować.

Jeśli element ma został otwarty w oknie serwera zamiast otwierane bezpośrednio w kontenerze dokumentów, jest w stanie open (lub w pełni otwarty). W tym stanie kreskowania jest zazwyczaj rysowany ciągu reprezentujący element w oknie kontenera, aby wskazać, czy element jest aktywny gdzie indziej.

Gdy element został aktywowany w miejscu, przekazuje on, zwykle tylko krótko mówiąc, za pośrednictwem stanie aktywnym. Następnie wprowadza ona stan aktywny interfejsu użytkownika, w którym serwer został scalony jego menu, paski narzędzi i innych składników interfejsu użytkownika z tymi kontenera. Obecność tych składników interfejsu użytkownika odróżnia stan aktywny UI w stanie aktywnym. W przeciwnym razie w stanie aktywnym przypomina stan aktywny UI. Jeśli serwer obsługuje cofania, serwer jest wymagany do przechowania informacji poprzedni stan elementu OLE, dopóki nie osiągnie stan załadowany lub Otwórz.

## <a name="see-also"></a>Zobacz też

[Kontenery](../mfc/containers.md)<br/>
[Aktywacja](../mfc/activation-cpp.md)<br/>
[Kontenery: powiadomienia dotyczące elementów klienckich](../mfc/containers-client-item-notifications.md)<br/>
[Trackery](../mfc/trackers.md)<br/>
[Klasa CRectTracker](../mfc/reference/crecttracker-class.md)
