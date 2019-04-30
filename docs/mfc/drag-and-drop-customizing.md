---
title: 'Przeciąganie i upuszczanie: Dostosowywanie'
ms.date: 11/04/2016
helpviewer_keywords:
- drag and drop [MFC], implementing in non-OLE applications
- drag and drop [MFC], customizing behavior
- drag and  [MFC], COleDataSource object
- drag and drop [MFC], calling DoDragDrop
- OLE drag and drop [MFC], customizing behavior
ms.assetid: 03369d3e-46bf-4140-b58c-d0c9657cf38a
ms.openlocfilehash: b4749f8d45c962f8b9217e4c6367538d3e6a3608
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405953"
---
# <a name="drag-and-drop-customizing"></a>Przeciąganie i upuszczanie: Dostosowywanie

Domyślna implementacja funkcji przeciągania i upuszczania jest wystarczające dla większości aplikacji. Jednak niektóre aplikacje mogą wymagać, że to standardowy zachowanie można zmienić. W tym artykule opisano kroki niezbędne do zmienić te ustawienia domyślne. Ponadto można użyć tej techniki można ustanowić aplikacje, które nie obsługują dokumenty złożone jako źródła listy.

Jeśli dostosowujesz standardowe zachowanie przeciąganie i upuszczanie OLE lub aplikacji innych niż OLE, należy utworzyć `COleDataSource` będzie zawierał dane. Gdy użytkownik uruchamia operację przeciągania i upuszczania, kod powinien wywoływać `DoDragDrop` funkcji z tego obiektu, a nie z innych klas, które obsługują operacje przeciągania i upuszczania.

Opcjonalnie możesz utworzyć `COleDropSource` obiekt, aby kontrolować listy i zastąpić niektóre swoje funkcje, w zależności od typu zachowanie, które chcesz zmienić. Ten obiekt miejsca źródłowego jest następnie przekazywany do `COleDataSource::DoDragDrop` można zmienić domyślne zachowanie tych funkcji. Te różne opcje umożliwiają dużą elastyczność w sposób obsługi operacji przeciągania i upuszczania w aplikacji. Aby uzyskać więcej informacji na temat źródeł danych, zobacz artykuł [obiekty danych i źródeł danych (OLE)](../mfc/data-objects-and-data-sources-ole.md).

Można zastąpić następujące funkcje, aby dostosować operacji przeciągania i upuszczania:

|Zastąpienie|Aby dostosować|
|--------------|------------------|
|`OnBeginDrag`|Jak przeciągnięcie jest inicjowane po wywołaniu metody `DoDragDrop`.|
|`GiveFeedback`|Wizualne, takie jak wyglądem kursora w innej listy wyników.|
|`QueryContinueDrag`|Zakończenie operacji przeciągania i upuszczania. Ta funkcja umożliwia sprawdzenie modyfikator stany klucza podczas operacji przeciągania.|

## <a name="see-also"></a>Zobacz także

[Przeciąganie i upuszczanie (OLE)](../mfc/drag-and-drop-ole.md)<br/>
[Klasa COleDropSource](../mfc/reference/coledropsource-class.md)<br/>
[Klasa COleDataSource](../mfc/reference/coledatasource-class.md)
