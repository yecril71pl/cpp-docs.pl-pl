---
title: 'Przeciąganie i upuszczanie: implementowanie miejsca docelowego'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE drag and drop [MFC], implementing drop targets
- OLE drag and drop [MFC], drop target
- drag and drop [MFC], drop target
ms.assetid: 0689f1ec-5326-4008-b226-4b373c881358
ms.openlocfilehash: 55c8bbe9484a71ee95d43609b29a055b4177914b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599878"
---
# <a name="drag-and-drop-implementing-a-drop-target"></a>Przeciąganie i upuszczanie: implementowanie miejsca docelowego

W tym artykule opisano sposób wprowadzania aplikacji miejsca docelowego. Implementowanie miejsca docelowego zajmuje nieco więcej pracy niż Implementowanie miejsca źródłowego, ale jest nadal stosunkowo proste. Metody te mają zastosowanie również do aplikacji innych niż OLE.

#### <a name="to-implement-a-drop-target"></a>Aby zaimplementować miejsca docelowego

1. Dodaj zmienną składową do każdego widoku w aplikacji, która ma być miejsca docelowego. Ta zmienna członka musi być typu `COleDropTarget` lub klasa pochodnej od niego.

1. Z funkcji klasy widoku, który obsługuje **WM_CREATE** wiadomości (zazwyczaj `OnCreate`), wywołaj nową zmienną elementu członkowskiego `Register` funkcja elementu członkowskiego. `Revoke` zostanie wywołana automatycznie dla Ciebie kiedy niszczony jest widok.

1. Zastąp następujące funkcje. Jeśli mają takie samo zachowanie w całej aplikacji, należy zastąpić tych funkcji w klasie widoku. Aby zmodyfikować zachowanie w przypadku izolowane, czy chcesz włączyć upuszczając go na inną niż`CView` systemu windows, zastąpić te funkcje w swojej `COleDropTarget`-klasy pochodnej.

    |Zastąpienie|Aby umożliwić|
    |--------------|--------------|
    |`OnDragEnter`|Usuwanie operacji w oknie. Wywołuje się, gdy kursor po raz pierwszy najedzie okna.|
    |`OnDragLeave`|Specjalne zachowanie podczas operacji przeciągania pozostawia określonego okna.|
    |`OnDragOver`|Usuwanie operacji w oknie. Wywołuje się, gdy kursor jest przeciągany w oknie.|
    |`OnDrop`|Obsługa danych Trwa porzucanie w określonym oknie.|
    |`OnScrollBy`|Specjalnego zachowania w przypadku gdy przewijania jest niezbędne w okno docelowe.|

Zobacz MAINVIEW. CPP pliku część próbki MFC OLE [OCLIENT](../visual-cpp-samples.md) przykład jak te funkcje współdziałają ze sobą.

Aby uzyskać więcej informacji, zobacz:

- [Implementowanie miejsca źródłowego](../mfc/drag-and-drop-implementing-a-drop-source.md)

- [Tworzenie i niszczenie obiektów danych OLE i źródła danych](../mfc/data-objects-and-data-sources-creation-and-destruction.md)

- [Manipulowanie OLE obiekty danych i źródeł danych](../mfc/data-objects-and-data-sources-manipulation.md)

## <a name="see-also"></a>Zobacz też

[Przeciąganie i upuszczanie (OLE)](../mfc/drag-and-drop-ole.md)<br/>
[Klasa COleDropTarget](../mfc/reference/coledroptarget-class.md)
