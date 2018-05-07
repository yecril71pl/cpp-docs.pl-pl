---
title: 'Przeciąganie i upuszczanie: Implementowanie miejsca źródłowego | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE drag and drop [MFC], initiating drag operations
- drag and drop [MFC], calling DoDragDrop
- OLE drag and drop [MFC], drop source
- OLE drag and drop [MFC], calling DoDragDrop
- drag and drop [MFC], initiating drag operations
- drag and drop [MFC], drop source
ms.assetid: 0ed2fda0-63fa-4b1e-b398-f1f142f40035
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c057657605296b3ba65128f26b25aa526f45b211
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="drag-and-drop-implementing-a-drop-source"></a>Przeciąganie i upuszczanie: implementowanie miejsca źródłowego
W tym artykule wyjaśniono, jak pobrać aplikację do dostarczania danych do operacji przeciągania i upuszczania.  
  
 Podstawowa implementacja miejsca źródłowego jest stosunkowo proste. Pierwszym krokiem jest ustalenie, jakie zdarzenia rozpocząć operację przeciągania. Zalecane wskazówki dotyczące interfejsu użytkownika zdefiniować początku operacji przeciągania jako wybór danych i `WM_LBUTTONDOWN` zdarzeń występujących w punkcie wewnątrz wybranych danych. Przykłady MFC OLE [OCLIENT](../visual-cpp-samples.md) i [HIERSVR](../visual-cpp-samples.md) przestrzegać następujących wytycznych.  
  
 Jeśli aplikacja jest kontenerem i wybrane dane są połączone lub typu osadzonego obiektu `COleClientItem`, wywołaj jego `DoDragDrop` funkcję elementu członkowskiego. W przeciwnym razie utworzenia `COleDataSource` obiekt, Zainicjuj go z opcją i wywołać obiekt źródła danych `DoDragDrop` funkcję elementu członkowskiego. Jeśli aplikacja jest serwerem, użyj `COleServerItem::DoDragDrop`. Aby dowiedzieć się, jak dostosowywanie standardowych zachowania przeciągania i upuszczania, zobacz artykuł [przeciąganie i upuszczanie: dostosowywanie](../mfc/drag-and-drop-customizing.md).  
  
 Jeśli `DoDragDrop` zwraca `DROPEFFECT_MOVE`, natychmiast usunąć źródło danych z dokumentu źródłowego. Brak innych wartości zwracanej z `DoDragDrop` ma wpływ na miejsca źródłowego.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Implementowanie miejsca docelowego](../mfc/drag-and-drop-implementing-a-drop-target.md)  
  
-   [Dostosowywanie przeciąganie i upuszczanie](../mfc/drag-and-drop-customizing.md)  
  
-   [Tworzenie i niszczenie obiektów danych OLE i źródła danych](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [Manipulowanie OLE obiekty danych i źródła danych](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przeciąganie i upuszczanie (OLE)](../mfc/drag-and-drop-ole.md)   
 [COleDataSource::DoDragDrop](../mfc/reference/coledatasource-class.md#dodragdrop)   
 [COleClientItem::DoDragDrop](../mfc/reference/coleclientitem-class.md#dodragdrop)   
 [CView::OnDragLeave](../mfc/reference/cview-class.md#ondragleave)

