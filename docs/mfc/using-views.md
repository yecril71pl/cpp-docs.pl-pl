---
title: Używanie widoków
ms.date: 11/04/2016
helpviewer_keywords:
- interacting with users and role of view class [MFC]
- drawing [MFC], data
- rendering data
- view classes [MFC], role in managing user interaction
- CView class [MFC], view architecture
- MFC, views
- views [MFC], using
- painting data
- user input [MFC], interpreting through view class [MFC]
- view classes [MFC], role in displaying application data
ms.assetid: dc3de6ad-5c64-4317-8f10-8bdcc38cdbd5
ms.openlocfilehash: 2038f2669d3aa8b5c4bf91b0ba0b38fbec9a1fc8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605702"
---
# <a name="using-views"></a>Używanie widoków

Obowiązki widoku są wyświetlane dane dokumentu graficznie użytkownikowi, a także zaakceptować i interpretowanie danych wprowadzonych przez użytkownika jako operacje na dokumencie. Zadania w pisaniu klasy widoku są:

- Zapis klasy widoku [OnDraw](../mfc/reference/cview-class.md#ondraw) funkcja elementu członkowskiego, która renderuje danych dokumentu.

- Połącz odpowiednie komunikaty Windows i obiekty interfejsu użytkownika, takie jak elementy menu do obsługi wiadomości składowych w klasie widoku.

- Implementuje te programy obsługi interpretowanie danych wprowadzonych przez użytkownika.

Ponadto konieczne może być zastąpienie innych `CView` funkcji składowych w klasie pochodnej widoku. W szczególności, możesz chcieć zastąpić [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) do wykonywania specjalnych inicjowania dla widoku i [OnUpdate](../mfc/reference/cview-class.md#onupdate) celu przetwarzana w specjalny potrzebne przed widoku odrysowuje sam. W przypadku dokumentów wielostronicowych, również należy zastąpić [onprepareprinting —](../mfc/reference/cview-class.md#onprepareprinting) zainicjować okno dialogowe drukowania z liczbą stron do wydrukowania i inne informacje. Aby uzyskać więcej informacji na temat zastępowania `CView` funkcji elementów członkowskich, można znaleźć klasy [CView](../mfc/reference/cview-class.md) w *odwołanie MFC*.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Pochodne klasy widoków dostępne w MFC](../mfc/derived-view-classes-available-in-mfc.md)

- [Rysowanie w widoku](../mfc/drawing-in-a-view.md)

- [Interpretowanie danych wejściowych użytkownika za pośrednictwem widoku](../mfc/interpreting-user-input-through-a-view.md)

- [Rola widoku w drukowaniu](../mfc/role-of-the-view-in-printing.md)

- [Przewijanie i skalowanie widoków](../mfc/scrolling-and-scaling-views.md)

- [Inicjowanie i oczyszczanie dokumentów i widoków](../mfc/initializing-and-cleaning-up-documents-and-views.md)

## <a name="see-also"></a>Zobacz też

[Architektura dokument/widok](../mfc/document-view-architecture.md)<br/>
[Klasa CFormView](../mfc/reference/cformview-class.md)<br/>
[Widoki rekordów (dostęp do danych MFC)](../data/record-views-mfc-data-access.md)<br/>
[Pomijanie mechanizmu serializacji](../mfc/bypassing-the-serialization-mechanism.md)

