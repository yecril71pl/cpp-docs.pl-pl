---
title: 'Przeciąganie i upuszczanie: Implementowanie miejsca docelowego'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE drag and drop [MFC], implementing drop targets
- OLE drag and drop [MFC], drop target
- drag and drop [MFC], drop target
ms.assetid: 0689f1ec-5326-4008-b226-4b373c881358
ms.openlocfilehash: 46501193569d7f3098e23c67c68c76ce20a82ea3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405940"
---
# <a name="drag-and-drop-implementing-a-drop-target"></a>Przeciąganie i upuszczanie: Implementowanie miejsca docelowego

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

Zobacz MAINVIEW. CPP pliku część próbki MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) przykład jak te funkcje współdziałają ze sobą.

Aby uzyskać więcej informacji, zobacz:

- [Implementowanie miejsca źródłowego](../mfc/drag-and-drop-implementing-a-drop-source.md)

- [Tworzenie i niszczenie obiektów danych OLE i źródła danych](../mfc/data-objects-and-data-sources-creation-and-destruction.md)

- [Manipulowanie OLE obiekty danych i źródeł danych](../mfc/data-objects-and-data-sources-manipulation.md)

## <a name="see-also"></a>Zobacz także

[Przeciąganie i upuszczanie (OLE)](../mfc/drag-and-drop-ole.md)<br/>
[Klasa COleDropTarget](../mfc/reference/coledroptarget-class.md)
