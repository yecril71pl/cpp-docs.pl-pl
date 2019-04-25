---
title: 'Przeciąganie i upuszczanie: Implementowanie miejsca źródłowego'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE drag and drop [MFC], initiating drag operations
- drag and drop [MFC], calling DoDragDrop
- OLE drag and drop [MFC], drop source
- OLE drag and drop [MFC], calling DoDragDrop
- drag and drop [MFC], initiating drag operations
- drag and drop [MFC], drop source
ms.assetid: 0ed2fda0-63fa-4b1e-b398-f1f142f40035
ms.openlocfilehash: 2aa593fa953f7a9874036d48124ae7b92d88e0a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219759"
---
# <a name="drag-and-drop-implementing-a-drop-source"></a>Przeciąganie i upuszczanie: Implementowanie miejsca źródłowego

W tym artykule wyjaśniono, jak pobrać aplikację, aby dostarczać dane do operacji przeciągania i upuszczania.

Podstawową implementację miejsca źródłowego jest stosunkowo prosta. Pierwszym krokiem jest ustalenie, jakie zdarzenia rozpocząć operację przeciągania. Zalecane wskazówki dotyczące interfejsu użytkownika definiują początku operacji przeciągania jako wyboru danych i **WM_LBUTTONDOWN** zdarzeń występujących w punkcie wewnątrz wybranych danych. Przykłady MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) i [HIERSVR](../overview/visual-cpp-samples.md) przestrzegać następujących wytycznych.

Jeśli aplikacja jest kontenerem, a wybrane dane są połączone lub osadzonego obiektu typu `COleClientItem`, wywoływanie jej `DoDragDrop` funkcja elementu członkowskiego. W przeciwnym razie konstruowania `COleDataSource` obiektu, Zainicjuj go przy użyciu zaznaczenie i wywoływać obiektu źródła danych `DoDragDrop` funkcja elementu członkowskiego. Jeśli aplikacja jest serwerem, użyj `COleServerItem::DoDragDrop`. Aby uzyskać informacje o dostosowywaniu standardowe zachowanie przeciągnij i upuść, zobacz artykuł [przeciąganie i upuszczanie: Dostosowywanie](../mfc/drag-and-drop-customizing.md).

Jeśli `DoDragDrop` zwraca **DROPEFFECT_MOVE**, natychmiast usunąć źródło danych z dokumentu źródłowego. Nie zwraca wartości z `DoDragDrop` ma wpływ na miejsca źródłowego.

Aby uzyskać więcej informacji, zobacz:

- [Implementowanie miejsca docelowego](../mfc/drag-and-drop-implementing-a-drop-target.md)

- [Dostosowywanie przeciągania i upuszczania](../mfc/drag-and-drop-customizing.md)

- [Tworzenie i niszczenie obiektów danych OLE i źródła danych](../mfc/data-objects-and-data-sources-creation-and-destruction.md)

- [Manipulowanie OLE obiekty danych i źródeł danych](../mfc/data-objects-and-data-sources-manipulation.md)

## <a name="see-also"></a>Zobacz także

[Przeciąganie i upuszczanie (OLE)](../mfc/drag-and-drop-ole.md)<br/>
[COleDataSource::DoDragDrop](../mfc/reference/coledatasource-class.md#dodragdrop)<br/>
[COleClientItem::DoDragDrop](../mfc/reference/coleclientitem-class.md#dodragdrop)<br/>
[CView::OnDragLeave](../mfc/reference/cview-class.md#ondragleave)
