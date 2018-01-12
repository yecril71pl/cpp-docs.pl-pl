---
title: "Nagłówki i stopki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- printing [MFC], multipage documents
- page headers [MFC], printing
- headers [MFC], printing
- footers [MFC], printing
- page footers [MFC], printing
- page headers [MFC]
- printing [MFC], headers and footers
- page footers [MFC]
ms.assetid: b0be9c53-5773-4955-a777-3c15da745128
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7525cba7d05c4d04f0548bd2dc774503b284c220
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="headers-and-footers"></a>Nagłówki i stopki
W tym artykule opisano sposób dodawania nagłówków i stopek do wydrukować dokument.  
  
 Po wyświetleniu dokumentu na ekranie nazwę dokumentu i bieżącej lokalizacji w dokumencie często są wyświetlane w paska tytułu i paska stanu. Podczas przeglądania kopię dokumentu, warto mieć nazwę i numer strony wyświetlany w nagłówku lub stopce strony. Jest to często stosowana metoda, w których WYSIWYG nawet programy różnią się w sposób wykonywania drukowania i ekranu.  
  
 [OnPrint](../mfc/reference/cview-class.md#onprint) funkcja członkowska jest odpowiednie miejsce do drukowania nagłówków i stopek, ponieważ jest ona wywoływana dla każdej strony i jest ona wywoływana wyłącznie do drukowania, nie dla ekranu. Można zdefiniować oddzielne funkcji drukowania w nagłówku lub stopce strony i przekaż go kontekstu urządzenia drukarki z `OnPrint`. Może być konieczne dostosowanie pochodzenia okna lub zakresie przed wywołaniem [OnDraw](../mfc/reference/cview-class.md#ondraw) Aby uniknąć treści nakładanie strony w nagłówku lub stopce strony. Może być również konieczne zmodyfikować `OnDraw` ponieważ ilość dokument, który mieści się na stronie może zostać zmniejszona.  
  
 Jednym ze sposobów odpowiednio dla obszaru wykonywaną przez nagłówek lub stopka jest użycie **m_rectDraw** członkiem [cprintinfo —](../mfc/reference/cprintinfo-structure.md). Zawsze, gdy strona jest drukowany, ten element członkowski jest inicjowany z powierzchnia użytkowa strony. Podczas drukowania przed wydrukowaniem ciała strony nagłówku lub stopce strony, można zmniejszyć rozmiar prostokąta przechowywane w **m_rectDraw** dla obszaru podjęte w nagłówku lub stopce strony. Następnie `OnPrint` mogą odwoływać się do **m_rectDraw** Aby dowiedzieć się, ile obszaru pozostaje drukowanie ciała strony.  
  
 Nie można wydrukować nagłówka lub jakikolwiek inny, z [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc), ponieważ jest ona wywoływana przed `StartPage` funkcji członkowskiej klasy [CDC](../mfc/reference/cdc-class.md) została wywołana. W tym momencie kontekstu urządzenia drukarki uważa się na granicy strony. Można wykonywać drukowanie tylko z `OnPrint` funkcję elementu członkowskiego.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Drukowanie dokumentów wielostronicowych](../mfc/multipage-documents.md)  
  
-   [Alokowanie zasobów GDI do drukowania](../mfc/allocating-gdi-resources.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Drukowanie](../mfc/printing.md)

