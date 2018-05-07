---
title: 'Przeciąganie i upuszczanie: Implementowanie miejsca docelowego | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE drag and drop [MFC], implementing drop targets
- OLE drag and drop [MFC], drop target
- drag and drop [MFC], drop target
ms.assetid: 0689f1ec-5326-4008-b226-4b373c881358
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 414437f044869fef7ae48883a88688ad50c9ac5f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="drag-and-drop-implementing-a-drop-target"></a>Przeciąganie i upuszczanie: implementowanie miejsca docelowego
W tym artykule opisano sposób wprowadzania aplikacji miejsca docelowego. Implementowanie miejsca docelowego przyjmuje nieco więcej pracy niż Implementowanie miejsca źródłowego, ale jest nadal stosunkowo proste. Metody te dotyczą także aplikacji innych niż OLE.  
  
#### <a name="to-implement-a-drop-target"></a>Aby zaimplementować miejsca docelowego  
  
1.  Dodaj zmienną członkowską do każdego widoku w aplikacji, które mają być miejsca docelowego. Ta zmienna elementu członkowskiego musi być typu `COleDropTarget` lub klasą pochodną go.  
  
2.  W klasie widoku funkcji, która obsługuje `WM_CREATE` komunikatu (zazwyczaj `OnCreate`), wywołaj nowej zmiennej członkowskiej `Register` funkcji członkowskiej. `Revoke` będzie ona wywoływana automatycznie dla możesz gdy widok zostanie zniszczony.  
  
3.  Zastąp następujące funkcje. Jeśli w całej aplikacji ma takie samo zachowanie, należy zastąpić te funkcje w klasie widoku. Aby zmodyfikować zachowanie w przypadku izolowanej lub chcesz włączyć porzucenie na inną niż`CView` z systemem windows, Zastąp te funkcje w Twojej `COleDropTarget`-klasy.  
  
    |Zastąpienie|Aby zezwolić|  
    |--------------|--------------|  
    |`OnDragEnter`|Usuwanie operacji w oknie. Wywoływane, gdy kursor po raz pierwszy najedzie okna.|  
    |`OnDragLeave`|Specjalnego zachowania podczas operacji przeciągania pozostawia określone okno.|  
    |`OnDragOver`|Usuwanie operacji w oknie. Wywoływane, gdy kursor jest przeciągany w oknie.|  
    |`OnDrop`|Obsługa danych usuwane w określonym oknem.|  
    |`OnScrollBy`|Specjalnego zachowania w przypadku gdy przewijanie jest niezbędne w oknie docelowej.|  
  
 Zobacz MAINVIEW. CPP pliku części próbki MFC OLE [OCLIENT](../visual-cpp-samples.md) przykład tych funkcji współdziałania.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Implementowanie miejsca źródłowego](../mfc/drag-and-drop-implementing-a-drop-source.md)  
  
-   [Tworzenie i niszczenie obiektów danych OLE i źródła danych](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [Manipulowanie OLE obiekty danych i źródła danych](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przeciąganie i upuszczanie (OLE)](../mfc/drag-and-drop-ole.md)   
 [Klasa COleDropTarget](../mfc/reference/coledroptarget-class.md)
